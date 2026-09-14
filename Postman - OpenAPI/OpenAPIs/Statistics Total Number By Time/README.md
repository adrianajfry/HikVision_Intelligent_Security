# Statistics Total Number By Time

**Role:** Target API — Guide p.368 (printed page footer, this PDF build)

**Prerequisite:** `Get Cameras Information In Page` → real `cameraIndexCode` values

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/aiapplication/{{API_VER}}/people/statisticsTotalNumByTime` |
| AK used | `34489509` |
| Signature used | `LZ1eADpS4CTiaLOqwH014BofmOoqq8H4PciANsFLhH4=` |
| Status | ✅ Passed |

**Request body:**
```json
{
    "pageNo": 1,
    "pageSize": 2,
    "cameraIndexCodes": "95, 6, 12, 89, 55, 13",
    "statisticsType": 0,
    "startTime": "2026-09-08T00:00:00+08:00",
    "endTime": "2026-09-09T00:00:00+08:00"
}
```

**Response (excerpt — full response contains 30 records across cameras 12 and 95):**
```json
{
    "code": "0",
    "msg": "Success",
    "data": {
        "completeness": 1,
        "pageNo": 0,
        "pageSize": 0,
        "list": [
            { "time": "2026-09-08T05:00:00+08:00", "cameraIndexCode": "12", "exitNum": 2, "enterNum": 0 },
            { "time": "2026-09-08T06:00:00+08:00", "cameraIndexCode": "12", "exitNum": 4, "enterNum": 3 }
        ]
    }
}
```

**Notes / issues:**
- All 6 real cameras passed in `cameraIndexCodes` (comma-separated, per guide format).
- **Parameter breakdown** (confirmed against guide): `pageNo`/`pageSize` (caller-decided), `cameraIndexCodes` (the one real dependency), `statisticsType` (fixed enum: 0-hour/1-day/2-month/4-minute), `startTime`/`endTime` (caller-decided date range). This is a fully verified, complete one-link dependency chain.
- ⚠️ Response echoes `pageNo: 0, pageSize: 0` instead of the requested `1, 2` — same quirk pattern seen elsewhere in this project (e.g., Access Point Information's list endpoint); not something to fix, just a live inconsistency worth noting.
