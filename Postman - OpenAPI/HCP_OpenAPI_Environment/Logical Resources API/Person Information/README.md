# Logical Resources API - Person Information

_(POST endpoints in this folder — 15 total)_

**Environment used:** `HCP_OpenAPI`
**Host:** `{{HOSTINFO}}` (`175.140.166.217`)
**API version:** `{{API_VER}}`

---

## Endpoint: Get person information

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/person/personList` |
| AK used | `{{AK}}` *(not yet tested)* |
| Signature used | *(pending — not yet tested)* |
| Status | ⬜ Not yet tested |

**Request body:**
```json
{
    "pageNo": 1,
    "pageSize": 100
}
```

**Response:**
```json
(not yet tested — run this request and paste the response here)
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Get a person information by person ID

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/person/personId/personInfo` |
| AK used | `34489509` |
| Signature used | `Tm94mdOOIMccHpWqEfEN7JECkdtqmbhlka5z3BEokmk=` |
| Status | ✅ Passed |

**Request body:**
```json
{
    "personId": "1"
}
```

**Response:**
```json
{
    "code": "0",
    "msg": "Success",
    "data": {
        "personId": "1",
        "personCode": "person001",
        "personName": "Test Tan",
        "gender": 1,
        "orgIndexCode": "1",
        "personPhoto": {
            "picUri": "",
            "picBigUri": ""
        },
        "phoneNo": "13000110011",
        "email": "testperson@example.com",
        "remark": "Test person created for API documentation",
        "beginTime": "2020-05-26T15:00:00+08:00",
        "endTime": "2030-05-26T15:00:00+08:00",
        "personFamilyName": "Tan",
        "personGivenName": "Test"
    }
}
```

**Notes / issues:**
- This is a good sanity check that the creation actually stuck, and completes another real end-to-end chain: Add a person → real personId → Get a person information by person ID.

---

## Endpoint: Search for person

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/person/advance/personList` |
| AK used | `{{AK}}` *(not yet tested)* |
| Signature used | *(pending — not yet tested)* |
| Status | ⬜ Not yet tested |

**Request body:**
```json
{
    "pageNo": 1,
    "pageSize": 10,
    "personName": "x"
}
```

**Response:**
```json
(not yet tested — run this request and paste the response here)
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Get person picture

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/person/picture_data` |
| AK used | `{{AK}}` *(not yet tested)* |
| Signature used | *(pending — not yet tested)* |
| Status | ⬜ Not yet tested |

**Request body:**
```json
{
    "personId": "3",
    "picUri": "/pic?8dd685i46-e*9b649962225a--0a15b67eb3a78i7b5*=ids1*=idp2*=0d8t0pe*m5i11=4-3634fc91z20ds=4i32="
}
```

**Response:**
```json
(not yet tested — run this request and paste the response here)
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Verify the face picture

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/acs/{{API_VER}}/faceCheck` |
| AK used | `{{AK}}` *(not yet tested)* |
| Signature used | *(pending — not yet tested)* |
| Status | ⬜ Not yet tested |

**Request body:**
```json
{
    "faceData": "null",
    "acsDevIndexCode": "1"
}
```

**Response:**
```json
(not yet tested — run this request and paste the response here)
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Add a person

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/person/single/add` |
| AK used | `34489509` |
| Signature used | `dUDvXIHtA56UNoVHxuW5NQ0bnvzwWbAr96UbDAP2VW0=` |
| Status | ✅ Passed |

**Request body:**
```json
{
    "personCode": "person001",
    "personFamilyName": "Tan",
    "personGivenName": "Test",
    "gender": 1,
    "orgIndexCode": "1",
    "remark": "Test person created for API documentation",
    "phoneNo": "13000110011",
    "email": "testperson@example.com",
    "beginTime": "2020-05-26T15:00:00+08:00",
    "endTime": "2030-05-26T15:00:00+08:00"
}
```

**Response:**
```json
{
    "code": "0",
    "msg": "Success",
    "data": "1"
}
```

**Notes / issues:**
- personCode just needs to be a unique identifier — changed it from the collection's placeholder in case that exact code was already tried/reserved somewhere.
- gender: 1 — this API typically uses 1/2 (check the Docs tab on this request to confirm which is which; not critical for a test record).
- beginTime/endTime define the person's access validity window — the collection's default (2020–2030) works fine as a wide-open test range.

---

## Endpoint: Edit person

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/person/single/update` |
| AK used | `{{AK}}` *(not yet tested)* |
| Signature used | *(pending — not yet tested)* |
| Status | ⬜ Not yet tested |

**Request body:**
```json
{
    "personId": "12",
    "personCode": "123245214",
    "personFamilyName": "Li",
    "personGivenName": "person0",
    "orgIndexCode": "1231",
    "gender": 1,
    "phoneNo": "13000110011",
    "remark": "description",
    "email": "person1@qq.com",
    "cards": [
        {
            "cardNo": "123456"
        }
    ],
    "beginTime": "2020-05-26T15:00:00+08:00",
    "endTime": "2030-05-26T15:00:00+08:00"
}
```

**Response:**
```json
(not yet tested — run this request and paste the response here)
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Delete a person

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/person/single/delete` |
| AK used | `{{AK}}` *(not yet tested)* |
| Signature used | *(pending — not yet tested)* |
| Status | ⬜ Not yet tested |

**Request body:**
```json
{
    "personId": "111"
}
```

**Response:**
```json
(not yet tested — run this request and paste the response here)
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Edit person face

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/person/face/update` |
| AK used | `{{AK}}` *(not yet tested)* |
| Signature used | *(pending — not yet tested)* |
| Status | ⬜ Not yet tested |

**Request body:**
```json
{
    "personId": "f5110a5f05ec4a66afa0754dca482522",
    "faceData": "person0"
}
```

**Response:**
```json
(not yet tested — run this request and paste the response here)
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Edit person fingerprints

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/person/fingerPrints/update` |
| AK used | `{{AK}}` *(not yet tested)* |
| Signature used | *(pending — not yet tested)* |
| Status | ⬜ Not yet tested |

**Request body:**
```json
{
    "personId": "f5110a5f05ec4a66afa0754dca482522",
    "fingerPrint": [
        {
            "fingerPrintIndexCode": "c7d1e474f-8ef9-69009691ad3c",
            "fingerPrintName": "fringe_pringt_01",
            "fingerPrintData": "228697F1AD0146C8D00",
            "relatedCardNo": "1123"
        }
    ]
}
```

**Response:**
```json
(not yet tested — run this request and paste the response here)
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Apply the access level to the person again

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/visitor/{{API_VER}}/auth/reapplication` |
| AK used | `{{AK}}` *(not yet tested)* |
| Signature used | *(pending — not yet tested)* |
| Status | ⬜ Not yet tested |

**Request body:**
```json
{}
```

**Response:**
```json
(not yet tested — run this request and paste the response here)
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Get permission to issue details

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/acs/{{API_VER}}/auth/applicationResult` |
| AK used | `{{AK}}` *(not yet tested)* |
| Signature used | *(pending — not yet tested)* |
| Status | ⬜ Not yet tested |

**Request body:**
```json
{
    "applicationResultType": 1,
    "pageNo": 1,
    "pageSize": 2,
    "type": 1
}
```

**Response:**
```json
(not yet tested — run this request and paste the response here)
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Edit the person custominformation

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/person/personId/customFieldsUpdate` |
| AK used | `{{AK}}` *(not yet tested)* |
| Signature used | *(pending — not yet tested)* |
| Status | ⬜ Not yet tested |

**Request body:**
```json
{
    "personId": "41",
    "list": [
        {
            "id": "1",
            "customFiledName": "ssss",
            "customFieldType": 1,
            "customFieldValue": "2354"
        }
    ]
}
```

**Response:**
```json
(not yet tested — run this request and paste the response here)
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Get person information according to PersonCode

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/person/personCode/personInfo` |
| AK used | `34489509` |
| Signature used | `9gGxU5vTxNxewvl6vES7ao02r/oAxJxSjw3fHigD7ZE=` |
| Status | ✅ Passed |

**Request body:**
```json
{
    "personCode": "person001"
}
```

**Response:**
```json
{
    "code": "0",
    "msg": "Success",
    "data": {
        "personId": "1",
        "personCode": "person001",
        "personName": "Test Tan",
        "personFamilyName": "Tan",
        "personGivenName": "Test",
        "gender": 1,
        "orgIndexCode": "1",
        "personPhoto": {
            "picUri": "",
            "picBigUri": ""
        },
        "phoneNo": "13000110011",
        "email": "testperson@example.com",
        "remark": "Test person created for API documentation",
        "beginTime": "2020-05-26T15:00:00+08:00",
        "endTime": "2030-05-26T15:00:00+08:00"
    }
}
```

**Notes / issues:**
- no issues for now.

---

## Endpoint: Get the person custom information list

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/person/customFields` |
| AK used | `34489509` |
| Signature used | `yPLLPvP/K6twPdgNJC4LChJRJIP/TRy7Ab6y8WCYF+A=` |
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
- **total: 0** means no custom fields are configured on this account at all

---

## Folder summary

- Total endpoints in this folder: `15`
- Tested: `0`
- Passed: `0`
- Blocked / failed: `0`
- ⚠️ Contains at least one endpoint with the known copy-pasted test-script bug (schema expects `produceName`/`softVersion`).
- Last updated: `2026-09-06`
