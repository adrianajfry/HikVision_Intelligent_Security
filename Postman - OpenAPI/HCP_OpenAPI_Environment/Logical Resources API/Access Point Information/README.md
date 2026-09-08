# Logical Resources API - Access Point Information

_(POST endpoints in this folder — 5 total)_

**Environment used:** `HCP_OpenAPI`
**Host:** `{{HOSTINFO}}` (`175.140.166.217`)
**API version:** `{{API_VER}}`

---

## Endpoint: Get access control points information in page

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/acsDoor/acsDoorList` |
| AK used | `34489509` |
| Signature used | `wbrpPM4/kVnqFAWAcvr0wZa67SIh+MZoDlxgmaFu9ss=` |
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
        "pageNo": 0,
        "pageSize": 0
    }
}
```

**Notes / issues:**
- `total: 0` — consistent with Access Control Device Information being empty; access points (doors) are physically tied to access control devices, so this follows the same root cause, not a new issue.
- Minor inconsistency worth noting: `pageNo`/`pageSize` in the response both show `0` instead of echoing the requested `1`/`2`, unlike every other empty-list response seen elsewhere in this collection (which echo the request values). Not investigated further as it doesn't affect functionality.
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Get an access control point information

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/acsDoor/indexCode/acsDoorInfo` |
| AK used | `34489509` |
| Signature used | `47yNhGtbbZfKTmex4RLi2LA5Cvbzk0bK2UtwdwPQmpY=` |
| Status | 🚫 Blocked (empty account — expected format error) |

**Request body:**
```json
{
    "doorIndexCode": "9290949c81434d2a84a06a6d127cefd6"
}
```

**Response:**
```json
{
    "code": "2",
    "msg": "Incorrect request parameter. [doorIndexCode parameter error]",
    "data": ""
}
```

**Notes / issues:**
- Signature/auth confirmed working (clean structured error, not a rejection). `code: 2` (format-rejected) matches the expected pattern for a placeholder ID with no real backing data — same category seen with the mobile device and record server placeholder IDs earlier, not a structural bug like the URL typos found elsewhere.

---

## Endpoint: Get access control point list of an area by area No

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/acsDoor/region/acsDoorList` |
| AK used | `34489509` |
| Signature used | `X6l30B/NXUvHHNJiYP0ri8DBHctk2bFQThJq+Uad2AY=` |
| Status | ✅ Passed (empty result) |

**Request body:**
```json
{
    "pageNo": 1,
    "pageSize": 2,
    "regionIndexCode": "3"
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
- `total: 0` — confirms the inferred empty-account conclusion directly for a real area (Kg.Mukut), rather than assuming from the account-wide list. `pageNo`/`pageSize` echo correctly here, unlike the earlier root list request — supports that the earlier `0`/`0` echo was a minor quirk of that specific endpoint, not account-wide.
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Flagged for senior; not something to fix on your end.

---

## Endpoint: Search for access control points

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/acsDoor/advance/acsDoorList` |
| AK used | `34489509` |
| Signature used | `fN+7Amhtxa9nLF15HF9NPRZliUZbi+P0ncXXgwMD2nc=` |
| Status | 🚫 Blocked (format-rejected placeholder ID) |

**Request body:**
```json
{
    "pageNo": 1,
    "pageSize": 2,
    "doorName": "test",
    "acsDevIndexCode": "79f11b9427794cb298ffafb8428042cf",
    "regionIndexCode": "3"
}
```

**Response:**
```json
{
    "code": "2",
    "msg": "Incorrect request parameter. [acsDevIndexCode parameter error]",
    "data": ""
}
```

**Notes / issues:**
- Signature/auth confirmed working. `acsDevIndexCode` is the collection's original placeholder value — same category as other format-rejected placeholder IDs seen throughout (mobile device, record server). Consistent with empty-account pattern.
- **Known collection bug**: same as above.

---

## Endpoint: Get card reader information

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/reader/search` |
| AK used | `34489509` |
| Signature used | `3VxzbZUUyWeIHR4bW6leB6H9Kh72DhaAWndV3oT9BgI=` |
| Status | 🚫 Blocked (resource not found) |

**Request body:**
```json
{
    "doorIndexCode": "1",
    "readerIndexCode": "2"
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
- Different failure stage than the other two: `code: 128` means these IDs are validly *formatted*, they simply don't exist — no card readers registered, consistent with no doors existing to attach them to.
- **Known collection bug**: same as above.
  
---

## Folder summary

- Total endpoints in this folder: `5`
- Tested: `5`
- Passed: `2` (both empty results)
- Blocked / failed: `3` (2 format-rejected placeholders, 1 not-found)
- 🔗 Root cause confirmed: no access control devices, doors, or card readers registered on this account.
- Last updated: `2026-09-08`
