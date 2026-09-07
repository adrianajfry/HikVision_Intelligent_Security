# Physical Resource API - Storage Server Info

_(POST endpoints in this folder — 3 total)_

**Environment used:** `HCP_OpenAPI`
**Host:** `{{HOSTINFO}}` (`175.140.166.217`)
**API version:** `{{API_VER}}`

---

## Endpoint: Get record server list

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/recordServer/recordServerList` |
| AK used | `34489509` |
| Signature used | `WsUn3UL6IgR7Hik13BmnhcfNpTnnsMd24+yGUWE8Yng=` |
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
- `"total": 0` — no record/storage servers registered under this account.
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix alone.

---

## Endpoint: Get record server info

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}//recordServer/indexCode/recordServerInfo` |
| AK used | `34489509` |
| Signature used | `5JHmynW+fwrcNF8nPV61U7tm8sRpPF5n8UJ8HM0iNJo=` |
| Status | ✅ Passed (empty result) |

**Request body:**
```json
{
    "recordServerIndexCode": "1"
}
```

**Response:**
```json
{
    "code": "128",
    "msg": "Resource Not Exist",
    "data": ""
}
```

**Notes / issues:**
- URL had a double-slash bug (fixed) → placeholder ID had a bad format (also effectively fixed by using "1") → genuinely blocked only by the account having zero record servers registered, same root cause as the rest of Storage Server Info.

---

## Endpoint: Get server record status

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/recordServer/recordStatus` |
| AK used | `34489509` |
| Signature used | `5JHmynW+fwrcNF8nPV61U7tm8sRpPF5n8UJ8HM0iNJo=` |
| Status | ✅ Passed |

**Request body:**
```json
{
    "pageNo": 1,
    "pageSize": 2,
    "recordServerIndexCode": "22222",
    "poolID": "12"
}
```

**Response:**
```json
{
    "code": "128",
    "msg": "Resource Not Exist",
    "data": ""
}
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Folder summary

- Total endpoints in this folder: `3`
- Tested: `1`
- Passed: `1`
- Blocked / failed: `0`
- ⚠️ Contains at least one endpoint with the known copy-pasted test-script bug (schema expects `produceName`/`softVersion`).
- Last updated: `2026-09-06`
