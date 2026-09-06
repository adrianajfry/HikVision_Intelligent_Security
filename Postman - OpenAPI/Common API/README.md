# Common API

Short one-line description of what this folder's endpoints are for.

**Environment used:** `HCP_OpenAPI`
**Host:** `{{HOSTINFO}}` (`175.140.166.217`)
**API version:** `{{API_VER}}`

---

## Endpoint: Get version of platform

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/common/{{API_VER}}/version` |
| AK used | `34489509` |
| Signature used | `8oBImGFnrmbUyylvRYox0RM/cJYUKGc1ku9raHcrAiM=` |
| Status | ✅ Passed |

**Request body:**
```json
(No request body required — this endpoint takes no request body)
```

**Response:**
```json
{
    "code": "0",
    "msg": "Success",
    "data": {
        "produceName": "HikCentral Professional",
        "softVersion": "V3.1.1.0"
    }
}
```

**Notes / issues:**
- _(none yet)_

---

## Endpoint: [Next endpoint name]

*(https://175.140.166.217/artemis/api/common/v1/v)*

---

## Folder summary

- Total endpoints in this folder: `1`
- Tested: `1`
- Passed: `1`
- Blocked / failed: `0`
- Last updated: `2026-09-06`
