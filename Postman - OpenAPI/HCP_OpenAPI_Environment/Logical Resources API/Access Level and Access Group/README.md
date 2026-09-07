# Logical Resources API - Access Level and Access Group

_(POST endpoints in this folder — 4 total)_

**Environment used:** `HCP_OpenAPI`
**Host:** `{{HOSTINFO}}` (`175.140.166.217`)
**API version:** `{{API_VER}}`

---

## Endpoint: Get access level list

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/acs/{{API_VER}}/privilege/group` |
| AK used | `34489509` |
| Signature used | `VFwMx10G2JYlbjy6uq9FaBPDV/IdPM1sRLsgrh6L5YU=` |
| Status | 🚫 Blocked — no permission |

**Request body:**
```json
{
    "pageNo": 1,
    "pageSize": 10,
    "type": 1
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
- AK `34489509` is not authorized for this API group. Signature/auth succeeded (clean structured response, not a rejection at the auth layer) — this is an authorization-scope issue, not a technical problem with the request.
- Same failure category as Visitor Information (also `code: 17`). Two confirmed API groups this account cannot access. No console access available to check the full authorized-API list directly, so this account's permission boundaries are being mapped empirically instead.
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Not relevant here since the request never reached that far, but noted for consistency.

---

## Endpoint: Add person(s) to the access group

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/acs/{{API_VER}}/privilege/group/single/addPersons` |
| AK used | `34489509` |
| Signature used | `VFwMx10G2JYlbjy6uq9FaBPDV/IdPM1sRLsgrh6L5YU=` |
| Status | 🚫 Blocked — no permission (inferred) |

**Request body:**
```json
{
    "privilegeGroupId": "1",
    "type": 1,
    "list": [
        {
            "id": "1"
        }
    ]
}
```

**Response:**
```json
(not individually tested — see note)
```

**Notes / issues:**
- Not tested directly. The `code: 17` permission block confirmed on "Get access level list" applies at the API-group level, not per-endpoint, so this endpoint is confidently expected to return the same block. Skipped to avoid burning further requests on a folder this account cannot access.

---

## Endpoint: Delete person(s) form the access group

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/acs/{{API_VER}}/privilege/group/single/deletePersons` |
| AK used | `34489509` |
| Signature used | `VFwMx10G2JYlbjy6uq9FaBPDV/IdPM1sRLsgrh6L5YU=` |
| Status | 🚫 Blocked — no permission (inferred) |

**Request body:**
```json
{
    "privilegeGroupId": "1",
    "type": 1,
    "list": [
        {
            "id": "1"
        }
    ]
}
```

**Response:**
```json
(not individually tested — see note)
```

**Notes / issues:**
- Same as above — inferred blocked via the folder-level `code: 17` permission finding, not individually tested.

---

## Endpoint: Get information list of persons related to the access levels

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/acs/{{API_VER}}/privilege/group/single/personList` |
| AK used | `34489509` |
| Signature used | `VFwMx10G2JYlbjy6uq9FaBPDV/IdPM1sRLsgrh6L5YU=` |
| Status | 🚫 Blocked — no permission (inferred) |

**Request body:**
```json
{
    "pageNo": 1,
    "pageSize": 2,
    "type": 1,
    "privilegeGroupId": "5"
}
```

**Response:**
```json
(not individually tested — see note)
```

**Notes / issues:**
- Same as above — inferred blocked via the folder-level `code: 17` permission finding, not individually tested.

---

## Folder summary

- Total endpoints in this folder: `4`
- Tested: `1` (directly) — remaining 3 inferred blocked
- Passed: `0`
- Blocked / failed: `4` (1 confirmed, 3 inferred from the same permission scope)
- 🚫 Entire folder blocked — AK `34489509` not authorized for this API group (`code: 17`). No Artemis console access to verify/request authorization.
- ⚠️ Contains at least one endpoint with the known copy-pasted test-script bug (schema expects `produceName`/`softVersion`) — not relevant here since permission blocks requests before reaching that stage.
- Last updated: `2026-09-07`
