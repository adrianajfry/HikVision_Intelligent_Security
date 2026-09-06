# Physical Resource API - Vídeo Management Server info

_(POST endpoints in this folder — 1 total)_

**Environment used:** `HCP_OpenAPI`
**Host:** `{{HOSTINFO}}` (`175.140.166.217`)
**API version:** `{{API_VER}}`

---

## Endpoint: Get video manager server

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/videoManagementServer` |
| AK used | `34489509` |
| Signature used | `2+Ywueu+ITI9aJb12yJ2YGiN9Y7T2GyZYqQ0OujKKSI=` |
| Status | ⬜ Not yet tested |

**Request body:**
```json
{}
```

**Response:**
```json
{
    "code": "0",
    "msg": "Success",
    "data": {
        "ip": "127.0.0.1",
        "port": 443,
        "cpu": 6,
        "status": 0
    }
}
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Folder summary

- Total endpoints in this folder: `1`
- Tested: `0`
- Passed: `0`
- Blocked / failed: `0`
- ⚠️ Contains at least one endpoint with the known copy-pasted test-script bug (schema expects `produceName`/`softVersion`).
- Last updated: `2026-09-06`
