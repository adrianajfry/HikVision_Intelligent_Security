# Statistics Heat Map By Time

**Role:** Target API — Guide p.375 (printed page footer, this PDF build)

**Prerequisite:** `Get Cameras Information In Page` → real `cameraIndexCode` value

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/aiapplication/{{API_VER}}/people/statisticsHeatMapByTime` |
| AK used | `34489509` |
| Signature used | `I/SEplnn+Y61XdiN/8EO62D2wy3DJJI1D2qCL43CuR0=` |
| Status | ✅ Passed |

**Request body:**
```json
{
    "cameraIndexCode": "6",
    "statisticsType": 1,
    "beginTime": "2026-09-08T00:00:00+08:00",
    "endTime": "2026-09-09T00:00:00+08:00"
}
```

**Response:**
```json
{
    "code": "0",
    "msg": "Success",
    "data": {
        "maxValue": 494,
        "minValue": 0,
        "averageValue": 0,
        "arrayLine": 176,
        "arrayColum": 176,
        "buffer": "AAAAAAA..."
    }
}
```

**Notes / issues:**
- `statisticsType: 1` = "people count" heat map mode (per guide).
- `buffer` is a real data payload (binary heat map matrix), truncated above for readability — full value present in the actual test.
- Shares the exact same prerequisite as "Statistics Total Number By Time" — only needs one real `cameraIndexCode`, no other dependency.
