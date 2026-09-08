# Logical Resources API - Visitor Information

_(POST endpoints in this folder — 15 total)_

**Environment used:** `HCP_OpenAPI`
**Host:** `{{HOSTINFO}}` (`175.140.166.217`)
**API version:** `{{API_VER}}`

---

## Endpoint: Visitor out

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/visitor/{{API_VER}}/visitor/out` |
| AK used | `34489509` |
| Signature used | `Bv83PwxIMWi3FiopCvuRfvQHC7ZzGWFQT8bhdiVTYHE=` |
| Status | 🚫 Blocked — no permission |

**Response:**
```json
{
    "code": "17",
    "msg": "No permission for OpenAPI access"
}
```

**Notes / issues:**
- AK `34489509` is not authorized for this endpoint (`code: 17`). Signature/auth succeeded (clean structured response, not a rejection), confirming this is an authorization-scope issue.
- ⚠️ **Do not assume this applies to the rest of the folder** — a permission block on one endpoint does not necessarily mean every endpoint in the same folder is blocked (this was a mistaken assumption made earlier in this project on this exact folder, later corrected). Each endpoint needs to be tested individually to know for sure.

---

## Remaining 14 endpoints — not yet tested

Add a visitor · Edit a visitor · Add a appointrecord · Add a visitor v2 · Delete a appoint record · Edit a appointrecord · Edit a visitor v2 · Get Customfield · Get appointrecordlist · Get visitor photo · VisitorGroup Info · Visitor record · Visitor record single · VisitorGroup

None of these have been run yet. Test each individually and record its real result — don't assume outcome from the one confirmed block above.

---

## Folder summary

- Total endpoints in this folder: `15`
- Tested: `1`
- Passed: `0`
- Blocked / failed: `1`
- Last updated: `2026-09-08`
