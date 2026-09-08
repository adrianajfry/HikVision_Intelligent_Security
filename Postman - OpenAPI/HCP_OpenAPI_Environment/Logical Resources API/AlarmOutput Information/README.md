# Logical Resources API - AlarmOutput Information

_(POST endpoints in this folder — 4 total)_

**Environment used:** `HCP_OpenAPI`
**Host:** `{{HOSTINFO}}` (`175.140.166.217`)
**API version:** `{{API_VER}}`

---

## Endpoint: Get alarmOutputs information in page

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/alarmOutputs` *(corrected — original collection URL had the entire `/artemis/api/resource/` segment duplicated)* |
| AK used | `34489509` |
| Signature used | `kHjcfixwN5Q5DooVN6vGrKNK+h4EE9/3YTXTi21Hx+8=` |
| Status | ✅ Passed |

**Request body:**
```json
{
    "pageNo": 1,
    "pageSize": 10,
    "deviceType": "encodeDevice"
}
```

**Response:**
```json
{
    "code": "0",
    "msg": "Success",
    "data": {
        "total": 24,
        "pageNo": 1,
        "pageSize": 10,
        "list": [
            {"alarmOutputIndexCode": "9", "alarmOutputName": "A1", "regionIndexCode": "2", "devIndexCode": "4", "devResourceType": "encodeDevice", "status": 0},
            {"alarmOutputIndexCode": "32", "alarmOutputName": "A1", "regionIndexCode": "3", "devIndexCode": "5", "devResourceType": "encodeDevice", "status": 0},
            {"alarmOutputIndexCode": "80", "alarmOutputName": "A1", "regionIndexCode": "2", "devIndexCode": "9", "devResourceType": "encodeDevice", "status": 0}
        ]
    }
}
```
*(showing first 3 of 10 returned; 24 total exist)*

**Notes / issues:**
- **Confirmed URL bug**: original collection path was `{{HOSTINFO}}/artemis/api/resource/{{API_VER}}/artemis/api/resource/v1/alarmOutputs` — the `/artemis/api/resource/` segment appears twice. Corrected to `{{HOSTINFO}}/artemis/api/resource/{{API_VER}}/alarmOutputs`, which then returned real data instead of failing. This is the 3rd distinct URL-construction bug found in this collection (after the encode-device typo and record-server double-slash) — worth flagging to senior as a pattern, possibly worth a full URL audit across all 143 requests rather than fixing one-by-one as discovered.
- 24 real alarm outputs found across the same encode devices (`4`, `5`, `9`) seen in Camera and AlarmInput Information — same physical hardware, cross-referenced a 4th way.
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Flagged for senior; not something to fix on your end.

---

## Endpoint: Get a Alarmoutput information by alarmoutput ID

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/alarmoutputs/indexCode` |
| AK used | `34489509` |
| Signature used | `yaoUBiZNmP9K0AcXlmFg2vZubdSWGDzYgZ54ySlY8Kk=` |
| Status | ✅ Passed |

**Request body:**
```json
{
    "alarmOutputIndexCode": "9"
}
```

**Response:**
```json
{
    "code": "0",
    "msg": "Success",
    "data": {
        "alarmOutputIndexCode": "9",
        "alarmOutputName": "A1",
        "regionIndexCode": "2",
        "devIndexCode": "4",
        "devResourceType": "encodeDevice",
        "status": 0
    }
}
```

**Notes / issues:**
- Direct lookup matches the list entry exactly. Also used as the "before" and "after" state check for the Control AlarmOutput test below.
- **Known collection bug**: same as above.

---

## Endpoint: Search for alarmoutputs

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/alarmOutput/advance/alarmOutputList` |
| AK used | `34489509` |
| Signature used | `sUgPzdpXitzw8RmOzqkA0yv9waJrm9aH7gogmniQlZE=` |
| Status | ✅ Passed |

**Request body:**
```json
{
    "pageNo": 1,
    "pageSize": 10,
    "deviceType": "encodeDevice",
    "alarmOutputName": "A1",
    "devIndexCode": "4",
    "regionIndexCode": "2"
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
        "pageSize": 10,
        "list": [
            {
                "alarmOutputIndexCode": "9",
                "alarmOutputName": "A1",
                "regionIndexCode": "2",
                "devIndexCode": "4",
                "devResourceType": "encodeDevice",
                "status": 0
            }
        ]
    }
}
```

**Notes / issues:**
- Multi-field search correctly narrowed to exactly 1 real match, same pattern as AlarmInput Information's search.
- **Known collection bug**: same as above.

---

## Endpoint: Control AlarmOutput

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/alarmOutput/controlling` |
| AK used | `34489509` |
| Signature used | `QKb0B5MECs2cyoquddR/eeY82+vUBqaPo0gjomj9eh4=` |
| Status | ✅ Passed (reversible action — tested and reverted) |

**Request body (test sequence, not a single call):**
```json
// Step 1: baseline confirmed via "Get a Alarmoutput information" — status: 0
// Step 2: toggle on
{ "alarmOutputIndexCode": "9", "action": 1 }
// Step 3: toggle back off
{ "alarmOutputIndexCode": "9", "action": 0 }
```

**Response (both steps identical):**
```json
{
    "code": "0",
    "msg": "Success",
    "data": ""
}
```

**Notes / issues:**
- ⚠️ **This is an action/control endpoint, not a read** — it changes real (or virtual) hardware state rather than querying it. Tested carefully: confirmed `status: 0` before, called `action: 1`, called `action: 0`, then re-confirmed `status: 0` after — full reversible round-trip, documented and left in its original state.
- Both control calls returned `code: 0` with empty `data`, giving no direct confirmation of the intermediate state change (no `status: 1` was observed mid-sequence — only before and after states were checked). Final state matches starting state, which is the important outcome, but the toggle's actual effect couldn't be independently confirmed via this endpoint's own response.
- **Known collection bug**: same as above.

---

## Folder summary

- Total endpoints in this folder: `4`
- Tested: `4`
- Passed: `4`
- Blocked / failed: `0`
- 🔧 Contains a confirmed URL bug (duplicated path segment), fixed in Postman app only — not yet re-saved to the exported collection file.
- ⚠️ Contains one control/action endpoint — tested safely with before/after verification and reverted to original state.
- Last updated: `2026-09-07`
