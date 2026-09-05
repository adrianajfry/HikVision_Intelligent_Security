# Common API

Short one-line description of what this folder's endpoints are for.

**Environment used:** `HCP_OpenAPI` (or `HCP_OpenAPI_2` — note which AK/SK pair)
**Host:** `{{HOSTINFO}}`
**API version:** `{{API_VER}}`

---

## Endpoint: [Endpoint Name, e.g. "Get version of platform"]

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/common/{{API_VER}}/version` |
| AK used | `34489509` |
| Status | ✅ Passed / ❌ Failed / ⚠️ Blocked (no permission) |

**Request body:**
```json
{

}
```

**Signature check:**
- Computed (expected): `paste value here`
- Actual (from Postman Console): `paste value here`
- Match? `Yes / No`

**Response:**
```json
{
  "code": "0",
  "msg": "Success",
  "data": {

  }
}
```

**Notes / issues:**
- e.g. "Returned code 102 (no permission) when using AK #16436892 — flagged to senior on [date]."
- e.g. "Had to strip trailing slash from HOSTINFO or request timed out."

---

## Endpoint: [Next endpoint name]

*(repeat the block above for each endpoint tested in this folder)*

---

## Folder summary

- Total endpoints in this folder: `X`
- Tested: `X`
- Passed: `X`
- Blocked / failed: `X`
- Last updated: `YYYY-MM-DD`
