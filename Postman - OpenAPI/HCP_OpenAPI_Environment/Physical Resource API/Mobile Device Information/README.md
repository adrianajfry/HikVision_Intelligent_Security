# Physical Resource API - Mobile Device Information

_(POST endpoints in this folder — 3 total)_

**Environment used:** `HCP_OpenAPI`
**Host:** `{{HOSTINFO}}` (`175.140.166.217`)
**API version:** `{{API_VER}}`

---

## Endpoint: Get the information of a mobile device by device ID

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/mobileDevice/indexCode/mobileDeviceInfo` |
| AK used | `34489509` |
| Signature used | `I/L8wRvmgMOKeijCwgjemYb6EGu+d1KNCXAaMOqf9Ho=` |
| Status | ⚠️ Blocked (no matching device) |

**Request body:**
```json
{
    "mobileDevIndexCode": "1"
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
- Tried `"mobileDevIndexCode": "1"` (placeholder from collection) → `code: 128`, "resource does not exist". Signature/auth confirmed working (clean JSON error, not an auth failure).
- Also tried `"mobileDevIndexCode": "0"` → `code: 2`, "Incorrect request parameter" — server rejects the ID format itself before even searching, so this is a different failure stage than the `"1"` attempt.
- Root cause (confirmed via "Get the mobile device list in page" and "Search the mobile device list" below): this account has **0 mobile devices registered** — there is currently no valid device ID to test a genuine Success case with.
- **Known collection bug**: the "Tests" script attached to this request validates the response against a schema expecting `produceName`/`softVersion` fields — that schema belongs to the "Get version of platform" endpoint, not this one. This test cannot pass even with a correct response. Flagged for senior.

---

## Endpoint: Get the mobile device list in page

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/mobileDevice/mobileDeviceList` |
| AK used | `34489509` |
| Signature used | `dyIIOEebHxx2rV6yt2t/Aj83Y1hjdcrvM6LUaP3QC0E=` |
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
- Request succeeded fully (`code: 0`, Success) — confirms signature/auth is correct for this endpoint.
- `"total": 0` — no mobile devices are registered under this account. This is the source of the blocked test above, not a bug in this request.

---

## Endpoint: Search the mobile device list

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/mobileDevice/advance/mobileDeviceList` |
| AK used | `34489509` |
| Signature used | `lDmmF+GLBoodwQjxmyqtwwp+FuQqTRXGhNcEjvt95qI=` |
| Status | ✅ Passed (empty result), ❌ Test script fails |

**Request body:**
```json
{
    "pageNo": 1,
    "pageSize": 2,
    "mobileDevName": "10.18.64.39"
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
- Request body filters by `"mobileDevName": "10.18.64.39"` — this looks like a leftover sample value (an IP address used as a device name) from whoever originally built the collection, not something meaningful for this account. Worth re-testing with this field removed/blank to rule out an over-narrow filter.
- Confirms (2nd independent check) that this account has 0 mobile devices registered.
- **Same known collection bug** as "Get the information of a mobile device by device ID" — the Tests script here is also checking for `produceName`/`softVersion`, copy-pasted from the version endpoint. Test Results shows 0/1 even though the actual API call is genuinely correct and successful.

---

## Folder summary

- Total endpoints in this folder: `3`
- Tested: `3`
- Passed: `1`
- Blocked / failed: `2`
- ⚠️ Contains at least one endpoint with the known copy-pasted test-script bug (schema expects `produceName`/`softVersion`).
- Last updated: `2026-09-06`
