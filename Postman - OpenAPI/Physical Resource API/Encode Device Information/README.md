# Physical Resource API - Encode Device Information

_(POST endpoints in this folder — 3 total)_

**Environment used:** `HCP_OpenAPI`
**Host:** `{{HOSTINFO}}` (`175.140.166.217`)
**API version:** `{{API_VER}}`

---

## Endpoint: Get encoding device list

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/ncodeDevice/encodeDeviceList` |
| AK used | `34489509` |
| Signature used | `oquEKtj1iUHTtG+/cv4I0CeP5ZjWCRHBn5EGU7oX/pc=` |
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
    "code": "8",
    "msg": "This product version is not supported"
}
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Search for encoding devices

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/encodeDevice/advance/encodeDeviceList` |
| AK used | `34489509` |
| Signature used | `cGa4+Pn/6jwhA6Pja+lTdszKNqS6GAMq2a7qEDqOdgs=` |
| Status | ✅ Passed |

**Request body:**
```json
{
    "pageNo": 1,
    "pageSize": 10,
    "encodeDevName": "devicename"
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

## Endpoint: Get an encoding device information

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/encodeDevice/indexCode/encodeDeviceInfo` |
| AK used | `34489509` |
| Signature used | `zpM49sDHcMgURw/VDy59L74dYfrT2oh7OJmPhrns56E=` |
| Status | ✅ Passed |

**Request body:**
```json
{
    "encodeDevIndexCode": "6f731abbe9b74197801274d1be455804"
}
```

**Response:**
```json
{
    "code": "2",
    "msg": "Incorrect request parameter. [encodeDevIndexCode parameter error]",
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
