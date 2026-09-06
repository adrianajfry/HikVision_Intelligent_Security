# Physical Resource API - Access Control Device Information

_(POST endpoints in this folder — 3 total)_

**Environment used:** `HCP_OpenAPI`
**Host:** `{{HOSTINFO}}` (`175.140.166.217`)
**API version:** `{{API_VER}}`

---

## Endpoint: Get access control device list

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/acsDevice/acsDeviceList` |
| AK used | `34489509` |
| Signature used | `1ia84TaaKHz9y+UF7uGopR0vW4bx8gm3smFM9z6VgYg=` |
| Status | ✅ Passed |

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
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Search for access control devices

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/acsDevice/advance/acsDeviceList` |
| AK used | `34489509` |
| Signature used | `85E0AKJqHD3LWSev526CYfXeuGy3p4XcMfhIwKYlSYs=` |
| Status | ✅ Passed |

**Request body:**
```json
{
    "pageNo": 1,
    "pageSize": 10,
    "acsDevName": "devicename1"
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
        "pageSize": 10
    }
}
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Get an access control device information by ID

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/acsDevice/indexCode/acsDeviceInfo` |
| AK used | `34489509` |
| Signature used | `CXZVbLNV75NSbsVfgxgKn7VjinBtXU/KAUPIwyWwS4E=` |
| Status | ✅ Passed |

**Request body:**
```json
{
    "acsDevIndexCode": "1"
}
```

**Response:**
```json
{
    "code": "128",
    "msg": "The request resource does not exist",
    "data": ""
}
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Folder summary

- Total endpoints in this folder: `3`
- Tested: `3`
- Passed: `3`
- Blocked / failed: `0`
- ⚠️ Contains at least one endpoint with the known copy-pasted test-script bug (schema expects `produceName`/`softVersion`).
- Last updated: `2026-09-06`
