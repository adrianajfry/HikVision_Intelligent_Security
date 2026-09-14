# Event Subscription By Event Types

**Role:** Target API — Guide p.445 (printed page footer, this PDF build); Alarm Category reference table: Appendix A.3, p.797

**Prerequisite:** None — see note below

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/eventService/{{API_VER}}/eventSubscriptionByEventTypes` |
| AK used | `34489509` |
| Signature used | `DbFTEhfK1AKOKLjUipjrPoEawCX/RO3p9dwNh1D47Oo=` |
| Status | ✅ Passed |

**Request body:**
```json
{
    "eventTypes": [131331, 133122],
    "eventDest": "http://ip:port/eventRcv",
    "token": "qscasd"
}
```

**Response:**
```json
{
    "code": "0",
    "msg": "Success",
    "data": ""
}
```

**Notes / issues:**
- **No prerequisite API call is needed for this endpoint** — confirmed after investigation. Its three inputs each come from a different, non-API source:
  - `eventTypes` (e.g. `133122`, "People Queuing-up Alarm") — a fixed value from the **static reference table**, Developer Guide Appendix A.3 "Event Types or Alarm Categories," p.797. Not fetched from any endpoint.
  - `token` — arbitrary string the caller invents, used later to verify pushed event authenticity.
  - `eventDest` — the caller's own server callback URL, not provided by HikCentral.
- Tested both `131331` and `133122` together — both accepted, `code: 0`. This **confirms the guide's documentation is correct**; an earlier note suggesting `133122` "not found for this endpoint" was based on a stale/incorrect assumption and has been corrected here.
- Subscription success (`code: 0`) confirms the *request* was accepted — it does not by itself confirm event delivery, since `eventDest` above is a placeholder URL with no real listener behind it. Delivery was not independently verified.
