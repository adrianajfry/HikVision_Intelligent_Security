# Logical Resources API - Visitor Information

_(POST endpoints in this folder — 15 total)_

**Environment used:** `HCP_OpenAPI`
**Host:** `{{HOSTINFO}}` (`175.140.166.217`)
**API version:** `{{API_VER}}`

---

## ⚠️ Key finding: permission validation happens AFTER parameter validation

Testing "Add a visitor" revealed something important about how this API behaves: **a `code: 2` (parameter error) result does not mean an endpoint is unblocked.** The API appears to validate the *shape* of a request (dates, required fields, formats) before checking whether the AppKey is authorized to call it at all. "Add a visitor" returned `code: 2` twice — for stale placeholder dates, then for an invalid email — and only revealed the real `code: 17` permission block once both were fixed. This means any endpoint elsewhere in this collection showing `code: 2` could theoretically also be permission-blocked underneath, undiscovered, unless retested with fully valid data. Worth flagging to senior as a general caution when interpreting `code: 2` results across the whole project.

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
{ "code": "17", "msg": "No permission for OpenAPI access" }
```

---

## Endpoint: Add a appointrecord

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/visitor/{{API_VER}}/appointment/appointmentlist` *(distinct request from "Add a visitor," different endpoint despite similar name)* |
| AK used | `34489509` |
| Status | 🚫 Blocked (inferred, low confidence) |

**Notes / issues:**
- Not directly tested. Given the validation-order finding above, this is a low-confidence inference, not a confirmed result — flagged as a gap rather than assumed safely blocked.

---

## Endpoint: Delete a appoint record

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/visitor/{{API_VER}}/appointment/single/delete` |
| AK used | `34489509` |
| Status | 🚫 Blocked — no permission |

**Response:**
```json
{ "code": "17", "msg": "No permission for OpenAPI access" }
```

---

## Endpoint: Get appointrecordlist

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/visitor/{{API_VER}}/appointment/appointmentlist` |
| AK used | `34489509` |
| Signature used | `EFnGQGGhZuEBAAhxISQGwgukSb3Pfo5HdHz5mtoiw00=` |
| Status | 🚫 Blocked — no permission |

**Request body:**
```json
{
    "pageNo": 1, "pageSize": 100,
    "appointStartTime": "2021-04-09T15:00:00+08:00",
    "appointEndTime": "2021-04-19T15:00:00+08:00",
    "visitorName": "1", "companyName": "1", "interviewName": "1",
    "appointCode": "1", "identiCode": "1", "phoneNo": "1",
    "appointState": "1", "visitorReason": "1"
}
```

**Response:**
```json
{ "code": "17", "msg": "No permission for OpenAPI access" }
```

---

## Endpoint: VisitorGroup

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/visitor/{{API_VER}}/visitorgroups` |
| AK used | `34489509` |
| Signature used | `hGb2pnBJ553OuXXOss5hGD/yuJ0gTaBiJ/b7C5H6FS0=` |
| Status | 🚫 Blocked — no permission |

**Request body:**
```json
{ "SearchCriteria": { "visitorGroupName": "" } }
```

**Response:**
```json
{ "code": "17", "msg": "No permission for OpenAPI access" }
```

---

## Endpoint: Add a visitor

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/visitor/{{API_VER}}/appointment` |
| AK used | `34489509` |
| Signature used | `GXVAhYWuDQ+dA/lsRoy1soTv+MNG80j0mw2d9z29+lc=` |
| Status | 🚫 Blocked — no permission (see key finding above) |

**Request body (final, valid attempt):**
```json
{
    "receptionistId": "1",
    "visitStartTime": "2026-09-10T09:00:00+08:00",
    "visitEndTime": "2026-09-10T18:00:00+08:00",
    "visitPurposeType": 0,
    "visitPurpose": "null",
    "visitorInfoList": [
        {
            "VisitorInfo": {
                "visitorFamilyName": "null",
                "visitorGivenName": "null",
                "gender": 1,
                "email": "testvisitor@example.com",
                "phoneNo": "13600000000",
                "plateNo": "浙A",
                "companyName": "hik",
                "certificateType": 111,
                "certificateNo": "null",
                "remark": "null"
            }
        }
    ]
}
```

**Response:**
```json
{ "code": "17", "msg": "No permission for OpenAPI access" }
```

**Notes / issues:**
- **This is the key finding of the folder** — see box at top. Original placeholder body failed with `code: 2` (stale 2018 dates → then invalid `"null"` email). Only after fixing both did the true `code: 17` block surface.

---

## Endpoint: Get Customfield

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/visitor/{{API_VER}}/visitorconfig/customfields` |
| AK used | `34489509` |
| Signature used | `HrMMOsYF1KXKxUdlcDs+gmmXFYDeTrsKQkD1xbCrjbY=` |
| Status | ✅ Passed — **only confirmed working endpoint in this folder** |

**Request body:**
```json
{ "pageIndex": 1, "pageSize": 10, "customFieldName": "" }
```

**Response:**
```json
{
    "code": "0",
    "msg": "Success",
    "data": {
        "CustomFieldList": { "TotalNum": -1, "pageIndex": -1, "pageSize": -1 }
    }
}
```

**Notes / issues:**
- The one confirmed non-blocked endpoint in this folder. Notably, all three numeric fields return `-1` instead of `0` — unlike every other empty-result response seen throughout this collection (which use `0`). Unclear if this is intentional (e.g., "-1 = not configured" vs "0 = configured but empty") or a minor inconsistency — worth a note to senior rather than assuming either.

---

## Remaining 9 endpoints — not tested

Edit a visitor · Add a visitor v2 · Edit a appointrecord · Edit a visitor v2 · Get visitor photo · VisitorGroup Info · Visitor record · Visitor record single

Not run due to time — given the pattern (5 of 6 sampled endpoints blocked, only fully confirmed after fixing placeholder data), these should **not** be assumed blocked without individual testing, per the validation-order finding above.

---

## Folder summary

- Total endpoints in this folder: `15`
- Tested: `6` (5 confirmed blocked, 1 confirmed working)
- Passed: `1`
- Blocked / failed: `5`
- Untested: `9` (do not assume outcome — see key finding)
- 🔑 **Key finding**: `code: 2` parameter errors can mask an underlying permission block; only a `code: 0` or fully-corrected `code: 17` response is conclusive.
- Last updated: `2026-09-08`
