# Logical Resources API - Visitor Information

_(POST endpoints in this folder — 15 total)_

**Environment used:** `HCP_OpenAPI`
**Host:** `{{HOSTINFO}}` (`175.140.166.217`)
**API version:** `{{API_VER}}`

---

## Endpoint: Add a visitor

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/visitor/{{API_VER}}/appointment` |
| AK used | `34489509` |
| Signature used | `GXVAhYWuDQ+dA/lsRoy1soTv+MNG80j0mw2d9z29+lc=` |
| Status | ⬜ Not yet tested |

**Request body:**
```json
{
    "receptionistId": "1",
    "visitStartTime": "2018-07-26T15:00:00+08:00",
    "visitEndTime": "2018-07-26T15:00:00+08:00",
    "visitPurposeType": 0,
    "visitPurpose": "null",
    "visitorInfoList": [
        {
            "VisitorInfo": {
                "visitorFamilyName": "null",
                "visitorGivenName": "null",
                "gender": 1,
                "email": "null",
                "phoneNo": "13600000000",
                "plateNo": "\u6d59A",
                "companyName": "hik",
                "certificateType": 111,
                "certificateNo": "null",
                "remark": "null",
                "faces": [
                    {
                        "faceData": "/9j/4AAQSkZRgABAQEAAAAAAAD/4QBCRXhpZgAATU.."
                    }
                ],
                "fingerPrint": [
                    {
                        "fingerPrintIndexCode": "c7d1e474f-8ef9-69009691ad3c",
                        "fingerPrintName": "fringe_pringt_01",
                        "fingerPrintData": "46504D228697F1AD0146C8D00",
                        "relatedCardNo": "1123"
                    }
                ],
                "cards": [
                    {
                        "cardNo": "123456"
                    }
                ]
            }
        }
    ]
}
```

**Response:**
```json
{
    "code": "2",
    "msg": "Incorrect request parameter. [visitStartTime and visitEndTime parameter error]"
}
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Edit a visitor

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/visitor/{{API_VER}}/appointment/update` |
| AK used | `34489509` |
| Signature used | `HqwalmQ8q126MVS2mEmP4/k+AfQ0lNYcZ7Ljr77WYHw=` |
| Status | ⬜ Not yet tested |

**Request body:**
```json
{
    "appointRecordId": "1",
    "receptionistId": "1",
    "visitStartTime": "2018-07-26T15:00:00+08:00",
    "visitEndTime": "2018-07-26T15:00:00+08:00",
    "visitPurposeType": 0,
    "visitPurpose": "null",
    "visitorInfoList": [
        {
            "VisitorInfo": {
                "visitorFamilyName": "null",
                "visitorGivenName": "null",
                "gender": 1,
                "email": "null",
                "phoneNo": "13600000000",
                "plateNo": "\u6d59A",
                "companyName": "hik",
                "certificateType": 111,
                "certificateNo": "null",
                "remark": "null",
                "faces": [
                    {
                        "faceData": "/9j/4AAQSkZJRgABAQEAAAAAAAD/4QBCRXhpZgAATU.."
                    }
                ],
                "fingerPrint": [
                    {
                        "fingerPrintIndexCode": "c7d1e474f-8ef9-69009691ad3c",
                        "fingerPrintName": "fringe_pringt_01",
                        "fingerPrintData": "46504D228697F1AD0146C8D00",
                        "relatedCardNo": "1123"
                    }
                ],
                "cards": [
                    {
                        "cardNo": "123456"
                    }
                ]
            }
        }
    ]
}
```

**Response:**
```json
{
    "code": "2",
    "msg": "Incorrect request parameter. [visitStartTime and visitEndTime parameter error]"
}
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Visitor out

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/visitor/{{API_VER}}/visitor/out` |
| AK used | `34489509` |
| Signature used | `Bv83PwxIMWi3FiopCvuRfvQHC7ZzGWFQT8bhdiVTYHE=` |
| Status | ⬜ Not yet tested |

**Request body:**
```json
{
    "appointRecordId": "1"
}
```

**Response:**
```json
{
    "code": "17",
    "msg": "No permission for OpenAPI access"
}
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Add a appointrecord

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/visitor/{{API_VER}}/appointment` |
| AK used | `34489509` |
| Signature used | `GXVAhYWuDQ+dA/lsRoy1soTv+MNG80j0mw2d9z29+lc=` |
| Status | ⬜ Not yet tested |

**Request body:**
```json
{
    "receptionistId": "1",
    "appointStartTime": "2021-04-09T15:00:00+08:00",
    "appointEndTime": "2021-04-14T15:00:00+08:00",
    "visitReasonType": 0,
    "visitReasonDetail": "null",
    "visitorInfoList": [
        {
            "VisitorInfo": {
                "visitorFamilyName": "null",
                "visitorGivenName": "null",
                "gender": 1,
                "email": "1@qq.com",
                "phoneNo": "13600000000",
                "plateNo": "\u6d59A",
                "companyName": "hik",
                "certificateType": 111,
                "certificateNo": "null",
                "remark": "null",
                "faces": [
                    {
                        "faceData": "/9j/4AAQSkZRgABAQEAAAAAAAD/4QBCRXhpZgAATU.."
                    }
                ],
                "identiPhoto": [
                    {
                        "identiPhotoData": "/9j/4AAQSkZRgABAQEAAAAAAAD/4QBCRXhpZgAATU.."
                    }
                ],
                "customField": [
                    {
                        "customID": "1",
                        "customFieldName": "1",
                        "customFieldType": 1,
                        "customFieldValue": "1"
                    }
                ]
            }
        }
    ]
}
```

**Response:**
```json
{
    "code": "2",
    "msg": "Incorrect request parameter. [visitStartTime parameter error]"
}
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Add a visitor v2

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/visitor/{{API_VER}}/registerment` |
| AK used | `34489509` |
| Signature used | `8az8xQzqxYHSWnEkR3rHail/jFyztSSzTlkM3lOflig=` |
| Status | ⬜ Not yet tested |

**Request body:**
```json
{
    "receptionistId": "1",
    "visitStartTime": "2018-07-26T15:00:00+08:00",
    "visitEndTime": "2018-07-26T15:00:00+08:00",
    "visitPurposeType": 0,
    "visitPurpose": "null",
    "visitorInfoList": [
        {
            "VisitorInfo": {
                "visitorFamilyName": "null",
                "visitorGivenName": "null",
                "gender": 1,
                "email": "null",
                "phoneNo": "13600000000",
                "plateNo": "\u6d59A",
                "companyName": "hik",
                "certificateType": 111,
                "certificateNo": "null",
                "remark": "null",
                "faces": [
                    {
                        "faceData": "/9j/4AAQSkZRgABAQEAAAAAAAD/4QBCRXhpZgAATU.."
                    }
                ],
                "fingerPrint": [
                    {
                        "fingerPrintIndexCode": "c7d1e474f-8ef9-69009691ad3c",
                        "fingerPrintName": "fringe_pringt_01",
                        "fingerPrintData": "46504D228697F1AD0146C8D00",
                        "relatedCardNo": "1123"
                    }
                ],
                "cards": [
                    {
                        "cardNo": "123456"
                    }
                ],
                "customField": [
                    {
                        "customID": "1",
                        "customFieldName": "1",
                        "customFieldType": 1,
                        "customFieldValue": "1"
                    }
                ]
            }
        }
    ],
    "appointId": "1",
    "visitorId": "1"
}
```

**Response:**
```json
{
    "code": "2",
    "msg": "Incorrect request parameter. [visitStartTime and visitEndTime parameter error]"
}
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Delete a appoint record

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/visitor/{{API_VER}}/appointment/single/delete` |
| AK used | `34489509` |
| Signature used | `5l7AY2AYp29hLJ0RMvUhYrakyBlp5k4NWqU9aL1vk+E=` |
| Status | ⬜ Not yet tested |

**Request body:**
```json
{
    "appointRecordId": "1"
}
```

**Response:**
```json
{
    "code": "17",
    "msg": "No permission for OpenAPI access"
}
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Edit a appointrecord

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/visitor/{{API_VER}}/appointment/update` |
| AK used | `34489509` |
| Signature used | `HqwalmQ8q126MVS2mEmP4/k+AfQ0lNYcZ7Ljr77WYHw=` |
| Status | ⬜ Not yet tested |

**Request body:**
```json
{
    "appointRecordId": "1",
    "receptionistId": "1",
    "appointStartTime": "2021-04-09T15:00:00+08:00",
    "appointEndTime": "2021-04-14T15:00:00+08:00",
    "visitReasonType": 0,
    "visitReasonDetail": "null",
    "visitorInfoList": [
        {
            "VisitorInfo": {
                "visitorFamilyName": "null",
                "visitorGivenName": "null",
                "gender": 1,
                "email": "1@qq.com",
                "phoneNo": "13600000000",
                "plateNo": "\u6d59A",
                "companyName": "hik",
                "certificateType": 111,
                "certificateNo": "null",
                "remark": "null",
                "faces": [
                    {
                        "faceData": "/9j/4AAQSkZRgABAQEAAAAAAAD/4QBCRXhpZgAATU.."
                    }
                ],
                "identiPhoto": [
                    {
                        "identiPhotoData": "/9j/4AAQSkZRgABAQEAAAAAAAD/4QBCRXhpZgAATU.."
                    }
                ],
                "customField": [
                    {
                        "customID": "1",
                        "customFieldName": "1",
                        "customFieldType": 1,
                        "customFieldValue": "1"
                    }
                ]
            }
        }
    ]
}
```

**Response:**
```json
{
    "code": "2",
    "msg": "Incorrect request parameter. [visitStartTime parameter error]"
}
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Edit a visitor v2

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/visitor/{{API_VER}}/registerment/update` |
| AK used | `34489509` |
| Signature used | `RRNOHhS6IDsB20c3H5+ZTg/yYNCF9a7NKVHaplg60/4=` |
| Status | ⬜ Not yet tested |

**Request body:**
```json
{
    "appointRecordId": "1",
    "receptionistId": "1",
    "visitStartTime": "2018-07-26T15:00:00+08:00",
    "visitEndTime": "2018-07-26T15:00:00+08:00",
    "visitPurposeType": 0,
    "visitPurpose": "null",
    "visitorInfoList": [
        {
            "VisitorInfo": {
                "visitorFamilyName": "null",
                "visitorGivenName": "null",
                "gender": 1,
                "email": "null",
                "phoneNo": "13600000000",
                "plateNo": "\u6d59A",
                "companyName": "hik",
                "certificateType": 111,
                "certificateNo": "null",
                "remark": "null",
                "faces": [
                    {
                        "faceData": "/9j/4AAQSkZJRgABAQEAAAAAAAD/4QBCRXhpZgAATU.."
                    }
                ],
                "fingerPrint": [
                    {
                        "fingerPrintIndexCode": "c7d1e474f-8ef9-69009691ad3c",
                        "fingerPrintName": "fringe_pringt_01",
                        "fingerPrintData": "46504D228697F1AD0146C8D00",
                        "relatedCardNo": "1123"
                    }
                ],
                "cards": [
                    {
                        "cardNo": "123456"
                    }
                ],
                "customField": [
                    {
                        "customID": "1",
                        "customFieldName": "1",
                        "customFieldType": 1,
                        "customFieldValue": "1"
                    }
                ]
            }
        }
    ]
}
```

**Response:**
```json
{
    "code": "2",
    "msg": "Incorrect request parameter. [visitStartTime and visitEndTime parameter error]"
}
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Get Customfield

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/visitor/{{API_VER}}/visitorconfig/customfields` |
| AK used | `34489509` |
| Signature used | `34489509` |
| Status | ⬜ Not yet tested |

**Request body:**
```json
{
    "pageIndex": 1,
    "pageSize": 10,
    "customFieldName": ""
}
```

**Response:**
```json
(not yet tested — run this request and paste the response here)
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Get appointrecordlist

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/visitor/{{API_VER}}/appointment/appointmentlist` |
| AK used | `34489509` |
| Signature used | `34489509` |
| Status | ⬜ Not yet tested |

**Request body:**
```json
{
    "pageNo": 1,
    "pageSize": 100,
    "appointStartTime": "2021-04-09T15:00:00+08:00",
    "appointEndTime": "2021-04-19T15:00:00+08:00",
    "visitorName": "1",
    "companyName": "1",
    "interviewName": "1",
    "appointCode": "1",
    "identiCode": "1",
    "phoneNo": "1",
    "appointState": "1",
    "visitorReason": "1"
}
```

**Response:**
```json
(not yet tested — run this request and paste the response here)
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Get visitor photo

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/visitor/{{API_VER}}/appointment/downloadpicture` |
| AK used | `34489509` |
| Signature used | `34489509` |
| Status | ⬜ Not yet tested |

**Request body:**
```json
{
    "visitorId": "1",
    "picType": "0",
    "picUrl": "2222"
}
```

**Response:**
```json
(not yet tested — run this request and paste the response here)
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: VisitorGroup Info

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/visitor/{{API_VER}}/visitorgroups/groupinfo` |
| AK used | `34489509` |
| Signature used | `34489509` |
| Status | ⬜ Not yet tested |

**Request body:**
```json
{
    "VisitorListRequest": {
        "indexCode": "1",
        "pageIndex": 1,
        "pageSize": 10,
        "searchCriteria": {
            "identifiyCode": "",
            "personName": "",
            "phoneNum": "",
            "companyName": "",
            "temperatureStatus": 1,
            "blackLisitStatus": 0
        }
    }
}
```

**Response:**
```json
(not yet tested — run this request and paste the response here)
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Visitor record

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/visitor/{{API_VER}}/visitor/visitorinfo` |
| AK used | `34489509` |
| Signature used | `34489509` |
| Status | ⬜ Not yet tested |

**Request body:**
```json
{
    "pageNo": "1",
    "pageSize": "20",
    "searchCriteria": {
        "visitorGroupID": "",
        "identifiyCode": "",
        "personName": "",
        "companyName": ""
    }
}
```

**Response:**
```json
(not yet tested — run this request and paste the response here)
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Visitor record single

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/visitor/{{API_VER}}/visitor/single/visitorinfo` |
| AK used | `34489509` |
| Signature used | `34489509` |
| Status | ⬜ Not yet tested |

**Request body:**
```json
{
    "visitorId": "125"
}
```

**Response:**
```json
(not yet tested — run this request and paste the response here)
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: VisitorGroup

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/visitor/{{API_VER}}/visitorgroups` |
| AK used | `34489509` |
| Signature used | `34489509` |
| Status | ⬜ Not yet tested |

**Request body:**
```json
{
    "SearchCriteria": {
        "visitorGroupName": ""
    }
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

- Total endpoints in this folder: `15`
- Tested: `0`
- Passed: `0`
- Blocked / failed: `0`
- ⚠️ Contains at least one endpoint with the known copy-pasted test-script bug (schema expects `produceName`/`softVersion`).
- Last updated: `2026-09-06`
