# Video API

Short one-line description of what this folder's endpoints are for.

**Environment used:** `HCP_OpenAPI` (or `HCP_OpenAPI_2` — note which AK/SK pair)
**Host:** `{{HOSTINFO}}`
**API version:** `{{API_VER}}`

---

## Endpoint: Resource Group Real Time Count

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/aiapplication/{{API_VER}}/people/resourceGroupRealTimeCount` |
| AK used | `34489509` |
| SK used | `odnUarSlGk0WsFXac578WnSbuMzhmvT5k9VdoxAvCj4=` |
| Status | ✅ Passed / ❌ Failed / ⚠️ Blocked (no permission) |

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
- none for now.

---

## Endpoint: [Next endpoint name]

*(repeat the block above for each endpoint tested in this folder)*

---

## Folder summary

- Total endpoints in this folder: `X`
- Tested: `X`
- Passed: `X`
- Blocked / failed: `X`
- Last updated: `YYYY-MM-DD`
