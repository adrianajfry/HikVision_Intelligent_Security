# Physical Resource API - Stream Server Info

_(POST endpoints in this folder — 1 total)_

**Environment used:** `HCP_OpenAPI`
**Host:** `{{HOSTINFO}}` (`175.140.166.217`)
**API version:** `{{API_VER}}`

---

## Endpoint: Get stream server list

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/streamServer/streamServerList` |
| AK used | `34489509` |
| Signature used | `QnWDuz5iGUyweFKLBJ3FNvd27Or8bNSDfBmiD70Rycg=` |
| Status | ✅ Passed (empty result) |

**Request body:**
```json
{
    "pageNo": 1,
    "pageSize": 2
}
```

**Response:**
```json
{
    "code": "0",
    "msg": "Success",
    "data": {
        "total": 0,
        "pageNo": 1,
        "pageSize": 2
    }
}
```

**Notes / issues:**
- Request succeeded fully (`code: 0`, Success) — signature/auth confirmed correct.
- `"total": 0` — no stream servers registered under this account. Same pattern as mobile devices, video management, etc. — see `TESTING_LOG.md` "Account has no registered resources" finding.
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Folder summary

- Total endpoints in this folder: `1`
- Tested: `1`
- Passed: `1`
- Blocked / failed: `0`
- ⚠️ Contains at least one endpoint with the known copy-pasted test-script bug (schema expects `produceName`/`softVersion`).
- Last updated: `2026-09-06`
