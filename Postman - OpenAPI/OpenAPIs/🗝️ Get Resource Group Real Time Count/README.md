# Get Resource Group Real Time Count

**Role:** Target API — Guide p.370 (printed page footer, this PDF build)

**Prerequisite:** `Get Resource Group List` → real `resourceGroupIndexCode: "1"`

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/aiapplication/{{API_VER}}/people/resourceGroupRealTimeCount` |
| AK used | `34489509` |
| Signature used | `odnUarSlGk0WsFXac578WnSbuMzhmvT5k9VdoxAvCj4=` |
| Status | ✅ Passed |

**Request body:**
```json
{
    "resourceGroupIndexCodes": "1"
}
```

**Response:**
```json
{
    "code": "0",
    "msg": "Success",
    "data": {
        "list": [
            {
                "timebeginTime": "2026-09-08T00:00:00+08:00",
                "resourceGroupIndexCode": "1",
                "resourceGroupName": "People Counting",
                "exitNum": 10,
                "enterNum": 10,
                "limitNum": 0
            }
        ]
    }
}
```

**Notes / issues:**
- ⚠️ **Field name discrepancy**: the response returns `timebeginTime`, but the official guide documents this field simply as `time`. Confirmed as a real API response quirk, not a documentation-reading error or copy-paste artifact — worth flagging to senior as a live behavior that doesn't match the guide.
- Values (`exitNum`/`enterNum`) differ from the guide's example response, as expected — this is live, real-time count data, not a static reference.
