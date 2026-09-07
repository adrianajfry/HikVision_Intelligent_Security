# Logical Resources API - Organization Information

_(POST endpoints in this folder — 8 total)_

**Environment used:** `HCP_OpenAPI`
**Host:** `{{HOSTINFO}}` (`175.140.166.217`)
**API version:** `{{API_VER}}`

---

## Endpoint: Get the root organization information

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/org/rootOrg` |
| AK used | `34489509` |
| Signature used | `pf819FFsTDUe/G0B+apoMkY13c207xxfFIc+Y9/JNYY=` |
| Status | ✅ Passed |

**Request body:**
```json
{}
```

**Response:**
```json
{
    "code": "0",
    "msg": "Success",
    "data": {
        "orgIndexCode": "1",
        "orgName": "All Departments",
        "parentOrgIndexCode": "0"
    }
}
```

**Notes / issues:**
- orgIndexCode: "1" ("All Departments") is a real root organization.

---

## Endpoint: Get information list of lower level organizations by parent organization

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/org/parentOrgIndexCode/subOrgList` |
| AK used | `{{AK}}` *(not yet tested)* |
| Signature used | *(pending — not yet tested)* |
| Status | ⬜ Not yet tested |

**Request body:**
```json
{
    "parentOrgIndexCode": "4db7c89d-0ce6-4826-9146-6b71f037d81e",
    "pageNo": 1,
    "pageSize": 1000
}
```

**Response:**
```json
(not yet tested — run this request and paste the response here)
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Get the information list of all organizations by page

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/org/orgList` |
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

## Endpoint: Search the specified organization

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/org/advance/orgList` |
| AK used | `{{AK}}` *(not yet tested)* |
| Signature used | *(pending — not yet tested)* |
| Status | ⬜ Not yet tested |

**Request body:**
```json
{
    "orgName": "x",
    "pageNo": 1,
    "pageSize": 1000
}
```

**Response:**
```json
(not yet tested — run this request and paste the response here)
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Get organization information by organization ID

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/org/orgIndexCode/orgInfo` |
| AK used | `{{AK}}` *(not yet tested)* |
| Signature used | *(pending — not yet tested)* |
| Status | ⬜ Not yet tested |

**Request body:**
```json
{
    "orgIndexCode": "b8d059a7-608a-4800-9b84-4eb8332978d2"
}
```

**Response:**
```json
(not yet tested — run this request and paste the response here)
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Add an organization

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/org/single/add` |
| AK used | `{{AK}}` *(not yet tested)* |
| Signature used | *(pending — not yet tested)* |
| Status | ⬜ Not yet tested |

**Request body:**
```json
{
    "orgName": "name",
    "parentIndexCode": "1"
}
```

**Response:**
```json
(not yet tested — run this request and paste the response here)
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Edit the information of an organization

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/org/single/update` |
| AK used | `{{AK}}` *(not yet tested)* |
| Signature used | *(pending — not yet tested)* |
| Status | ⬜ Not yet tested |

**Request body:**
```json
{
    "orgName": "name",
    "orgIndexCode": "root0000001",
    "parentIndexCode": "root000000"
}
```

**Response:**
```json
(not yet tested — run this request and paste the response here)
```

**Notes / issues:**
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Delete an organization

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/org/single/delete` |
| AK used | `{{AK}}` *(not yet tested)* |
| Signature used | *(pending — not yet tested)* |
| Status | ⬜ Not yet tested |

**Request body:**
```json
{
    "orgIndexCode": "root000000"
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

- Total endpoints in this folder: `8`
- Tested: `0`
- Passed: `0`
- Blocked / failed: `0`
- ⚠️ Contains at least one endpoint with the known copy-pasted test-script bug (schema expects `produceName`/`softVersion`).
- Last updated: `2026-09-06`
