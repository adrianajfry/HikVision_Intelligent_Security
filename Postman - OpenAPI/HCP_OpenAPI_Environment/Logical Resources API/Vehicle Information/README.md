# Logical Resources API - Vehicle Information

_(POST endpoints in this folder — 10 total)_

**Environment used:** `HCP_OpenAPI`
**Host:** `{{HOSTINFO}}` (`175.140.166.217`)
**API version:** `{{API_VER}}`

---

## Endpoint: Get vehicle group list

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/vehicleGroup/single/add` |
| AK used | `{{AK}}` *(not yet tested)* |
| Signature used | *(pending — not yet tested)* |
| Status | ⬜ Not yet tested |

**Request body:**
```json
{
    "vehicleGroupName": "test",
    "description": "test"
}
```

**Response:**
```json
(not yet tested — run this request and paste the response here)
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Add single vehicle group

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/vehicleGroup/single/add` |
| AK used | `34489509` |
| Signature used | `Raw7tIV+1TTVZDvp5GhOflY/nURPXHceF2/XQ96XQw0=` |
| Status | ✅ Passed |

**Request body:**
```json
{
    "vehicleGroupName": "test",
    "description": "test"
}
```

**Response:**
```json
{
    "code": "0",
    "msg": "Success",
    "data": {
        "vehicleGroupIndexCode": "1",
        "vehicleGroupName": "test",
        "description": "test"
    }
}
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Update single vehicle group

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/vehicleGroup/single/update` |
| AK used | `{{AK}}` *(not yet tested)* |
| Signature used | *(pending — not yet tested)* |
| Status | ⬜ Not yet tested |

**Request body:**
```json
{
    "vehicleGroupIndexCode": "test",
    "vehicleGroupName": "test",
    "description": "test"
}
```

**Response:**
```json
(not yet tested — run this request and paste the response here)
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Delete single vehicle group

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/vehicleGroup/single/delete` |
| AK used | `{{AK}}` *(not yet tested)* |
| Signature used | *(pending — not yet tested)* |
| Status | ⬜ Not yet tested |

**Request body:**
```json
{
    "vehicleGroupIndexCode": "15"
}
```

**Response:**
```json
(not yet tested — run this request and paste the response here)
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Get vehicle list

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/vehicle/vehicleList` |
| AK used | `{{AK}}` *(not yet tested)* |
| Signature used | *(pending — not yet tested)* |
| Status | ⬜ Not yet tested |

**Request body:**
```json
{
    "pageNo": 1,
    "pageSize": 10,
    "vehicleGroupIndexCode": "1"
}
```

**Response:**
```json
(not yet tested — run this request and paste the response here)
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Search for vehicles

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/vehicle/advance/vehicleList` |
| AK used | `{{AK}}` *(not yet tested)* |
| Signature used | *(pending — not yet tested)* |
| Status | ⬜ Not yet tested |

**Request body:**
```json
{
    "pageNo": 1,
    "pageSize": 10,
    "personName": "name",
    "plateNo": "111",
    "phoneNo": "12345678",
    "vehicleGroupIndexCode": "7345-543"
}
```

**Response:**
```json
(not yet tested — run this request and paste the response here)
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Get a vehicle information by vehicle ID

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/vehicle/indexCode/vehicleInfo` |
| AK used | `{{AK}}` *(not yet tested)* |
| Signature used | *(pending — not yet tested)* |
| Status | ⬜ Not yet tested |

**Request body:**
```json
{
    "vehicleIndexCode": "111d9ade-8057-4d01-bb38-2af26d43083e "
}
```

**Response:**
```json
(not yet tested — run this request and paste the response here)
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Add single vehicle

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/vehicle/single/add` |
| AK used | `34489509` |
| Signature used | `Raw7tIV+1TTVZDvp5GhOflY/nURPXHceF2/XQ96XQw0=` |
| Status | Blocked |

**Request body:**
```json
{
    "plateNo": "ABC1234",
    "personId": "1",
    "phoneNo": "13000110011",
    "vehicleColor": 3,
    "vehicleGroupIndexCode": "1",
    "personGivenName": "Test",
    "personFamilyName": "Tan",
    "effectiveDate": "2020-05-26",
    "expiryDate": "2030-05-26"
}
```

**Response:**
```json
{
    "code": "2",
    "msg": "Incorrect request parameter. [effectiveDate parameter error]",
    "data": ""
}
```

**Notes / issues:**
- "Add single vehicle" requires an effectiveDate parameter not present in the collection's original template. Tried 4 formats (ISO datetime with timezone, epoch milliseconds, date-only string, and omitted entirely) — all rejected with the same generic error, which doesn't specify the expected format. Blocked pending either official Hikvision Artemis API documentation for this endpoint, or confirmation from senior on the correct format.
- personId: "12" → "1" (real person)
- vehicleGroupIndexCode: "11" → "1" (the real group just created)
- personGivenName/personFamilyName: matched to Test Tan's actual name, so the record is internally consistent
- plateNo: changed to something more plate-like ("ABC1234") — the original "7465154" was purely numeric, which is unusual for a plate number and might trigger a format validation error the same way the person edit did earlier
- phoneNo: matched to Test Tan's real phone number for consistency

---

## Endpoint: Delete single vehicle

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/vehicle/single/delete` |
| AK used | `{{AK}}` *(not yet tested)* |
| Signature used | *(pending — not yet tested)* |
| Status | ⬜ Not yet tested |

**Request body:**
```json
{
    "vehicleId": "12"
}
```

**Response:**
```json
(not yet tested — run this request and paste the response here)
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Update single vehicle

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/vehicle/single/update` |
| AK used | `{{AK}}` *(not yet tested)* |
| Signature used | *(pending — not yet tested)* |
| Status | ⬜ Not yet tested |

**Request body:**
```json
{
    "vehicleId": "64",
    "plateNo": "7465154",
    "personId": "111",
    "phoneNo": "111111111111",
    "vehicleColor": 3,
    "vehicleGroupIndexCode": "11",
    "personFamilyName": "dong",
    "personGivenName": "zhaod"
}
```

**Response:**
```json
(not yet tested — run this request and paste the response here)
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Folder summary

- Total endpoints in this folder: `10`
- Tested: `0`
- Passed: `0`
- Blocked / failed: `0`
- ⚠️ Contains at least one endpoint with the known copy-pasted test-script bug (schema expects `produceName`/`softVersion`).
- Last updated: `2026-09-06`
