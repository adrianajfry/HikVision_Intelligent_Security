# Logical Resources API - Face Comparision Group

_(POST endpoints in this folder — 6 total)_

**Environment used:** `HCP_OpenAPI`
**Host:** `{{HOSTINFO}}` (`175.140.166.217`)
**API version:** `{{API_VER}}`

---

## Endpoint: Get face comparison group list

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/frs/{{API_VER}}/face/groupList` |
| AK used | `34489509` |
| Signature used | `wDkQDmScRcfEJWdfJgz3agaH37bYz4Mr6I1uSalTIVo=` |
| Status | ✅ Passed |

**Request body:**
```json
{
    "pageNo": 1,
    "pageSize": 6
}
```

**Response:**
```json
{
    "code": "0",
    "msg": "Success",
    "data": {
        "total": 1,
        "pageNo": 1,
        "pageSize": 6,
        "list": [
            {
                "indexCode": "2",
                "name": "name",
                "description": "test"
            }
        ]
    }
}
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Search the specified face comparison groups

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/frs/{{API_VER}}/face/group` |
| AK used | `34489509` |
| Signature used | `k9X1K5cG07sVG7uP1FOzugWBDJqrzo/smqTBRtX8eIM=` |
| Status | ✅ Passed |

**Request body:**
```json
{
    "indexCodes": [
        "2"
    ]
}
```

**Response:**
```json
{
    "code": "0",
    "msg": "Success",
    "data": {
        "list": [
            {
                "indexCode": "2",
                "name": "name",
                "description": "test"
            }
        ]
    }
}
```

**Notes / issues:**
- swap indexCodes: ["2"], name: "name" to match what created.
- name: "name" is removed as the endpoint wants to search by either name or indexCodes, not both together.
---

## Endpoint: Add a face comparison group

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/frs/{{API_VER}}/face/group/single/addition` |
| AK used | `34489509` |
| Signature used | `CRulojijDwOq0AxBVUHAOIfKcX1Y/bifJDzqhwg0BAI=` |
| Status | ✅ Passed |

**Request body:**
```json
{
    "name": "name",
    "description": "test"
}
```

**Response:**
```json
{
    "code": "0",
    "msg": "Success",
    "data": {
        "indexCode": "2",
        "name": "name",
        "description": "test"
    }
}
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Edit information of a face comparison group

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/frs/{{API_VER}}/face/group/single/update` |
| AK used | `34489509` |
| Signature used | `JijTG6oO8QPxrhDHyCcOS9/sxs5rVAsOVO9PUH4fnkI=` |
| Status | ✅ Passed |

**Request body:**
```json
{
    "indexCode": "2",
    "name": "name updated",
    "description": "test"
}
```

**Response:**
```json
{
    "code": "0",
    "msg": "Success",
    "data": ""
}
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Delete a face comparison group by group ID

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/frs/{{API_VER}}/face/group/batch/deletion` |
| AK used | `{{AK}}` *(not yet tested)* |
| Signature used | *(pending — not yet tested)* |
| Status | ⬜ Not yet tested |

**Request body:**
```json
{
    "indexCodes": [
        "5dc82633-a4cb-4107-b55e-f21bbdf952f9"
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

## Endpoint: Apply all face information to device

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/frs/{{API_VER}}/plan/recognition/black/restart` |
| AK used | `34489509` |
| Signature used | `ZLZBro0jSLo0ZXE2+xiztcoxRifWRqI4mMAJY9/Lyk8=` |
| Status | ✅ Passed (empty result) |

**Request body:**
```json
{
    "indexCode": "2"
}
```

**Response:**
```json
{
    "code": "0",
    "msg": "Success",
    "data": ""
}
```

**Notes / issues:**
- "Apply all face information to device" returned success even with data: "" (empty) — makes sense, since this group has zero actual face entries linked to it yet (haven't touched the Face Information folder). Worth noting it succeeded but pushed nothing, since the group is empty.
- This account has zero access control devices registered. So even though the face group now genuinely has content, there's nothing physically connected to push it to. The API dutifully reports success (the operation itself is valid and accepted), but there's no receiving device on the other end, so the result stays empty regardless of what's in the group.

---

## Folder summary

- Total endpoints in this folder: `6`
- Tested: `5`
- Passed: `5`
- Blocked / failed: `0`
- ⚠️ Contains at least one endpoint with the known copy-pasted test-script bug (schema expects `produceName`/`softVersion`).
- Last updated: `2026-09-06`
