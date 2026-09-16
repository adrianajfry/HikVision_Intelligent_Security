# Retail KPI Analytics — HikCentral Professional (HCP) OpenAPI & ISAPI Integration

## 1. Project Overview

This project builds retail analytics (footfall, occupancy, dwell time, queueing, crowd density, and related KPIs) on top of Hikvision's video analytics ecosystem — cameras and NVRs running people-counting and other VCA (video content analysis) features, managed centrally through **HikCentral Professional (HCP)**.

The original requirements for this project were defined by **Mr. Izzat**, scoped entirely around **HCP OpenAPI**. As the team worked through implementation, a related device-level API — **ISAPI (Intelligent Security API)** — came up as a way to potentially close gaps that HCP OpenAPI doesn't cover.

This document exists so anyone joining the project can understand both APIs, how they relate, what's actually usable today, and what's still blocked or out of scope.

## 2. Two APIs, Two Layers

| | **ISAPI** | **HCP OpenAPI (Artemis)** |
|---|---|---|
| Layer | Device-level — runs on each camera/NVR's firmware | Platform-level — runs on the HikCentral Professional server |
| Scope | One device at a time | Aggregates data across all registered devices |
| Auth | HTTP Digest Auth (camera's own admin login) | AK/SK, HMAC-SHA256 signed requests |
| Reachability | Private LAN only (e.g. `192.168.x.x`), unless VPN'd or port-forwarded | Reachable wherever the HCP server is exposed (public IP in this project) |
| Typical use | Direct config (enable counting, set thresholds) + raw single-device data | Cross-device reporting, statistics, and event/alarm subscriptions |
| Status in this project | **Not in original scope** — being evaluated for specific gaps | **Confirmed working** — credentials tested, live calls succeeding |

**Key takeaway:** these are not chained together (ISAPI does not "feed into" OpenAPI). They're two independent, parallel ways to reach the same underlying devices. In this project, HCP OpenAPI is the primary integration path; ISAPI is only relevant for the small number of KPIs HCP doesn't expose.

## 3. Current API Availability Status

The team mapped ~48 retail KPIs against what's actually retrievable. Summary:

| Status | Count | Meaning |
|---|---|---|
| **Yes** | 17 | Confirmed, documented, callable via HCP OpenAPI today |
| **Yes (Flagged)** | 12 | Documented and callable, but needs Hikvision to validate real-world reliability (e.g. Heatmap/Dwell Time can return an empty payload) |
| **Partial** | 11 | No continuous query exists on HCP OpenAPI — only available (if at all) via device-direct ISAPI, or depends on site configuration |
| **No** | 8 | No known API path at any layer (mainly Re-ID / cross-camera visitor journey features) |

**KPIs that specifically require ISAPI** (not available via HCP OpenAPI at all):
- Queue Length (continuous count)
- Average Wait Time (continuous)
- Crowd Density (continuous index/score)
- Passersby (config-dependent — may just need the outdoor line registered as its own camera resource)

Everything else in the "Yes" and "Yes (Flagged)" categories is fully served by HCP OpenAPI and needs no ISAPI work.

## 4. Project Scope Note

ISAPI was **not part of the original requirements**. Mr. Izzat's scope and the KPI mapping were built entirely around HCP OpenAPI, and HCP OpenAPI is confirmed to cover everything originally requested. The four KPIs above are an open question for the team lead: whether to formally expand scope to include ISAPI, or leave them out of this project's deliverables.

## 5. ISAPI Status: Blocked (Not Yet Tested)

The team has **not been able to test any ISAPI endpoint** — this is a single, well-understood blocker, not a series of individual API failures:

1. **Network access** — camera/NVR IPs (e.g. `192.168.7.117`) sit on a private LAN, unreachable from outside without being physically on-site or connected via VPN.
2. **Credentials** — camera-level admin username/password (Digest Auth) has not been provided. This is separate from the HCP OpenAPI AK/SK credentials already in use.

Both are access requests for whoever manages the physical devices/network — not a coding or documentation problem.

## 6. What's Confirmed Working

- HCP OpenAPI credentials (AK/SK) are live and tested via Postman.
- Successfully called `encodeDeviceList` and retrieved the real registered device list (e.g. Bullet Camera, TMDA-NVR, TM 80-Cam 3, Kg.Mukut NVR, Fisheye) with their IPs, ports, and protocol types.
- Successfully tested `cameras`, and people-counting statistics endpoints (`statisticsTotalNumByTime`, `resourceGroupRealTimeCount`, etc.) referenced in the KPI mapping.

## 7. Key People

- **Mr. Izzat** — defined original project requirements/scope
- **Puan Hana** — team lead, reviewing progress and testing status
- **Edwin & Shirlin (Hikvision)** — technical contacts consulted on API gaps (e.g. Heatmap/Dwell Time reliability, UI-vs-OpenAPI discrepancies)

## 8. Open Questions / Next Steps

- [ ] Confirm with Puan Hana / Mr. Izzat: is ISAPI in scope for the 4 flagged KPIs, or are they accepted as unavailable?
- [ ] If in scope: request VPN or on-site network access to the camera LAN
- [ ] If in scope: request camera/NVR admin credentials for ISAPI Digest Auth
- [ ] Confirm whether Queue Management and Crowd Density are separate ISAPI feature modules (with their own developer guides) distinct from the People Counting guide already reviewed
- [ ] Ask Hikvision to validate the "Yes (Flagged)" endpoints live (Heatmap/Dwell Time empty-buffer issue)
- [ ] Confirm entrance/zone-to-camera-resource mapping on site (affects Passersby, Visitors by Zone, Capture Rate)

## 9. Reference Documents

- *Intelligent Security API (People Counting) Developer Guide* — ISAPI conventions, capability-first config pattern, arming/listening event modes
- *HikCentral Professional OpenAPI V3.1.0 Developer Guide* (851 pages) — full HCP OpenAPI endpoint reference
- Internal KPI-to-API availability mapping spreadsheet (48 KPIs, Yes/Flagged/Partial/No classification)
