# Common API -Get version of platform

Short one-line description of what this folder's endpoints are for.

**Environment used:** `HCP_OpenAPI`
**Host:** `{{HOSTINFO}}`
**API version:** `{{API_VER}}`

---

## Endpoint: [Endpoint Name, e.g. "Get version of platform"]

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/common/{{API_VER}}/version` |
| AK used | `34489509` |
| Signature used | `8oBImGFnrmbUyylvRYox0RM/cJYUKGc1ku9raHcrAiM=` |
| Status | ✅ Passed |

**Request body:**
```json
{

}
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
- e.g. "Returned code 102 (no permission) when using AK #16436892 — flagged to senior on [date]."
- e.g. "Had to strip trailing slash from HOSTINFO or request timed out."

---

## Endpoint: [Next endpoint name]

*(https://175.140.166.217/artemis/api/common/v1/v)*

---

## Folder summary

- Total endpoints in this folder: `X`
- Tested: `X`
- Passed: `X`
- Blocked / failed: `X`
- Last updated: `2026-09-06`
