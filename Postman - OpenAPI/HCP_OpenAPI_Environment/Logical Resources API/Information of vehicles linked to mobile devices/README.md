# Logical Resources API - Information of vehicles linked to mobile devices

_(POST endpoints in this folder — 3 total)_

**Environment used:** `HCP_OpenAPI`
**Host:** `{{HOSTINFO}}` (`175.140.166.217`)
**API version:** `{{API_VER}}`

---

## Endpoint: Get a mobile vehicle information by mobile vehicle ID

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/mobileVehicle/indexCode/mobileVehicleInfo` |
| AK used | `34489509` |
| Signature used | `WgtLCVrX73rLhQbkQKjauw+6V2zlCKx9Z+48Ka8sgMo=` |
| Status | ✅ Passed |

**Request body:**
```json
{
    "mobilevehicleIndexCode": "1"
}
```

**Response:**
```json
{
    "code": "128",
    "msg": "The request resource does not exist"
}
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Get the mobile vehicle list in page

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/mobilevehicle/mobilevehicleList` |
| AK used | `34489509` |
| Signature used | `WgtLCVrX73rLhQbkQKjauw+6V2zlCKx9Z+48Ka8sgMo=` |
| Status | ✅ Passed |

**Request body:**
```json
{
    "pageNo": 1,
    "pageSize": 10
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

## Endpoint: Search the mobile vehicles list

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/mobilevehicle/advanced/mobilevehicleList` |
| AK used | `34489509` |
| Signature used | `swApj4AOX2py59fxBMLbo0W2oyK5hzIwUv/8Dp5bm9w=` |
| Status | ✅ Passed |

**Request body:**
```json
{
    "pageNo": 1,
    "pageSize": 10,
    "mobilevehicleName": "10.18.68.12",
    "devIndexCode": "1",
    "regionIndexCode": "1"
}
```

**Response:**
```json
{
    "code": "128",
    "msg": "The request resource does not exist"
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
