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
| Signature used | `vactaGgZM+osob4Nl73g6YQqh7aB3afh4dIx6iXJbQI=` |
| Status | ✅ Passed |

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
        "cpu": 3,
        "status": 0
    }
}
```

**Notes / issues:**
- Request succeeded fully (`code: 0`, Success) with real server data returned — confirms signature/auth is correct for this endpoint.
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results shows `0/1` even though the actual API call is correct and successful. Same collection-wide bug affecting 142/143 requests (see `TESTING_LOG.md`).
- Optional fix (not applied — flagging as an option for senior to decide): the Tests script could be rewritten to check for this endpoint's real fields (`ip`, `port`, `cpu`, `status`) instead of `produceName`/`softVersion`, which would make it show `1/1`. Left as-is for now since fixing all 142 affected requests is a separate scope of work from documentation/verification.

---

## Folder summary

- Total endpoints in this folder: `1`
- Tested: `1`
- Passed: `1`
- Blocked / failed: `0`
- ⚠️ Contains at least one endpoint with the known copy-pasted test-script bug (schema expects `produceName`/`softVersion`).
- Last updated: `2026-09-06`
