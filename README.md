# People Counting Integration Research — ISAPI & HCP OpenAPI

Research notes on Hikvision's People Counting capabilities across two separate API layers, done in support of a retail KPI reporting project. This documents how the two APIs relate, what was tested, and what's confirmed vs. still open.

## 1. The Two Layers

Hikvision exposes people-counting data through two independent APIs. They are **not chained** — an app doesn't call one to reach the other. They're two separate doors into the same underlying camera data, each with its own auth, base URL, and use case.

| | ISAPI | HCP OpenAPI (Artemis) |
|---|---|---|
| Level | Device (camera/NVR) | Platform (HikCentral Professional server) |
| Talks to | Camera's own IP directly | HCP server's public-facing address |
| Auth | HTTP Digest (device admin/password) | AppKey/AppSecret, HMAC-SHA256 signed |
| Payload | XML | JSON |
| Used for | Configuring a camera (enable counting, set thresholds) | Reading aggregated stats across all registered cameras |

```
Camera (runs ISAPI internally)
        │
        ▼  (HikCentral onboarding — not something the app codes)
HikCentral Professional platform
        │
        ▼
Your app ──── HCP OpenAPI ────▶ read aggregated stats
        │
        └──── ISAPI (direct to camera IP) ────▶ configure counting settings
```

## 2. ISAPI — Core Pattern

Every ISAPI feature follows the same request sequence (from the *Intelligent Security API (People Counting) Developer Guide*):

1. `GET .../capabilities` — check the feature is supported
2. `GET` current config — read existing settings (optional)
3. `PUT` config — enable the feature / set parameters
4. Data flows out via **events**, in one of two modes:
   - **Arming mode** — app holds open a long-lived GET request; device streams events down it (pull)
   - **Listening mode** — app runs a small HTTP server; device pushes events to it like a webhook (push)

Appendices in the guide (URIs, XML schemas, error codes) are reference material — consult as needed, not something to read end-to-end.

## 3. HCP OpenAPI — What's Actually Used

Confirmed via the *HikCentral Professional OpenAPI V3.1.0 Developer Guide*, Section 4.11 (Intelligent Analysis):

```
1. POST /artemis/api/aiapplication/v1/people/advance/resourceGroupList
2. POST /artemis/api/aiapplication/v1/people/statisticsTotalNumByTime
3. POST /artemis/api/aiapplication/v1/people/resourceGroupRealTimeCount
4. POST /artemis/api/aiapplication/v1/people/statisticsHeatMapByTime
5. POST /artemis/api/eventService/v1/eventSubscriptionByEventTypes  (alarm/event push)
6. POST /artemis/api/resource/v1/cameras
7. POST /artemis/api/resource/v1/encodeDevice/encodeDeviceList
```

This section is purely **read/report** — no endpoint here configures or enables counting on a device. Confirmed by full-text search of the guide: no ISAPI passthrough, transparent-transmission, or forwarding mechanism exists in HCP OpenAPI. Device configuration is only possible via ISAPI, direct to the device.

## 4. ID Mapping (the one real bridge between the two APIs)

ISAPI identifies a camera by **IP + channel ID**. HCP identifies it by its own internal **`cameraIndexCode`**. Neither API surfaces the other's identifier directly for a given camera, so a manual join is needed:

- `POST /artemis/api/resource/v1/cameras` → returns `cameraIndexCode`, `encodeDevIndexCode`
- `POST /artemis/api/resource/v1/encodeDevice/encodeDeviceList` → returns `encodeDevIndexCode`, `encodeDevIp`, `encodeDevPort`

Join on `encodeDevIndexCode` to get a `cameraIndexCode ↔ deviceIp` lookup table. Note: for cameras behind an NVR, `encodeDevIp` is the **NVR's** IP, and the camera is a channel number on that NVR, not a separate IP.

## 5. Network Notes

- HCP OpenAPI's `HOSTINFO` is typically a **public IP** — the organization port-forwards specifically for OpenAPI access.
- Camera IPs (`encodeDevIp`) are typically **private LAN addresses** (e.g. `192.168.x.x`) and are *not* reachable from outside that network. Reaching them for direct ISAPI calls requires one of: on-site network access, VPN into the site, a jump host inside the LAN, or (short-term only) explicit port forwarding to the camera.
- ISAPI runs on the device's standard HTTP/HTTPS port (80/443) — not the SDK port (commonly 8000) that `encodeDeviceList` reports, which is used for HikCentral's private protocol, not ISAPI.

## 6. Postman Setup Notes

- **HCP OpenAPI** requests require a pre-request script that computes an `X-Ca-Signature` header via HMAC-SHA256 using the environment's `SK` value. Requests built without this script fail with `code: 68, "Signature authentication Failed"`.
- **ISAPI** requests use Digest Auth (camera admin credentials) instead, need SSL certificate verification disabled (self-signed device certs), and use `Content-Type: application/xml` instead of JSON.
- The vendor-exported HCP OpenAPI Postman collection has a known typo in one bundled request (`ncodeDevice` instead of `encodeDevice` in the URL path) — fix manually if reused.

## 7. KPI → API Availability (Retail Project Mapping)

From the project's KPI availability review (48 KPIs assessed):

| Status | Count | Meaning |
|---|---|---|
| Yes | 17 | Confirmed, callable today (HCP OpenAPI and/or ISAPI) |
| Yes (Flagged) | 12 | Documented but needs a live validation demo from Hikvision (e.g. Heatmap/Dwell Time return an explicitly empty buffer in some cases) |
| Partial | 11 | Only available via camera/NVR-direct ISAPI (not exposed by HCP OpenAPI), or config-dependent |
| No | 8 | No known endpoint at any layer (Visitor Re-ID, Journey, Repeat Visitors — all downstream of a missing Re-ID capability) |

**KPIs that would require ISAPI work specifically** (HCP OpenAPI has no continuous-value endpoint for these — only threshold alarms):
- Queue Length (continuous count)
- Average Wait Time (continuous)
- Crowd Density (continuous index)
- Passersby (config-dependent — needs confirmation on camera/resource setup)

## 8. Project Scope Note

Per the project's original requirements (set by Mr. Izzat), the intended integration is **HCP OpenAPI only** — ISAPI was never part of the defined scope. The four KPIs above are technically achievable via ISAPI, but pursuing them would extend scope beyond the original plan. This is a decision point for the project owner, not an engineering gap to silently fill.

## 9. Open Items

- [ ] Confirm with Hikvision: dedicated ISAPI developer guides for Queue Management and Crowd Density/Regional People Counting modules (separate from the People Counting guide already reviewed)
- [ ] Get a live validation demo from Hikvision for the "Yes (Flagged)" Heatmap/Dwell Time endpoints
- [ ] Scope decision from Mr. Izzat on the 4 ISAPI-only KPIs
- [ ] Confirm zone-to-resource-group mapping for `resourceGroupRealTimeCount` (unlocks several "Partial" zone-based KPIs without touching ISAPI)

## References

- *Intelligent Security API (People Counting) Developer Guide* — Hikvision
- *HikCentral Professional OpenAPI V3.1.0 Developer Guide* (20260130) — Hikvision
- Retail KPI API Availability Map (internal project spreadsheet)
