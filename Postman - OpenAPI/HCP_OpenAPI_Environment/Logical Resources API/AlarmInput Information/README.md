# Logical Resources API - AlarmInput Information

_(POST endpoints in this folder — 3 total)_

**Environment used:** `HCP_OpenAPI`
**Host:** `{{HOSTINFO}}` (`175.140.166.217`)
**API version:** `{{API_VER}}`

---

## Endpoint: Get alarminputs information in page

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/alarmInputs` |
| AK used | `34489509` |
| Signature used | `iOvHMPhR3Ecjekq0k0YdHQ2bdsPPyNfnBOSY1TFF2xs=` |
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
        "total": 36,
        "pageNo": 1,
        "pageSize": 10,
        "list": [
            {"alarmInputIndexCode": "7", "alarmInputName": "A1", "regionIndexCode": "2", "devIndexCode": "4", "devResourceType": "encodeDevice", "networkStatus": 1},
            {"alarmInputIndexCode": "14", "alarmInputName": "A1", "regionIndexCode": "3", "devIndexCode": "5", "devResourceType": "encodeDevice", "networkStatus": 2},
            {"alarmInputIndexCode": "64", "alarmInputName": "A1", "regionIndexCode": "2", "devIndexCode": "9", "devResourceType": "encodeDevice", "networkStatus": 1}
        ]
    }
}
```
*(showing first 3 of 10 returned; 36 total exist)*

**Notes / issues:**
- 36 real alarm inputs found, spread across encode devices `4` (Fisheye), `5` (Jetty CCTV/Uncle Sam CCTV), and `9` (NVR-Channel 1) — matches exactly the encode devices already confirmed in Encode Device Information and Camera Information, cross-referenced a third way.
- `networkStatus` differs by device: devices `4` and `9` show `1`, device `5` shows `2` — likely online/offline, meaning not documented in the collection but worth noting as a pattern.
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Flagged for senior; not something to fix on your end.

---

## Endpoint: Get a alarminput information by alarminput ID

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/alarmInputs/indexCode` |
| AK used | `34489509` |
| Signature used | `0tb71ioX3sf8GfO/QOAQmW4KtrnipsBCj1kFlz96Oq4=` |
| Status | ✅ Passed |

**Request body:**
```json
{
    "alarmInputIndexCode": "7"
}
```

**Response:**
```json
{
    "code": "0",
    "msg": "Success",
    "data": {
        "alarmInputIndexCode": "7",
        "alarmInputName": "A1",
        "regionIndexCode": "2",
        "devIndexCode": "4",
        "devResourceType": "encodeDevice",
        "networkStatus": 1
    }
}
```

**Notes / issues:**
- Direct lookup by real ID matches the list entry exactly — full read chain verified.
- **Known collection bug**: same as above.

---

## Endpoint: Search for alarminputs

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/alarmInput/advance/alarmInputList` |
| AK used | `34489509` |
| Signature used | `/I9kvRAQum+K9ZOHjL6uwwXnfw1ezz8o88Wly4mcMsU=` |
| Status | ✅ Passed |

**Request body:**
```json
{
    "pageNo": 1,
    "pageSize": 10,
    "deviceType": "encodeDevice",
    "alarmInputName": "A1",
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
                "alarmInputIndexCode": "7",
                "alarmInputName": "A1",
                "regionIndexCode": "2",
                "devIndexCode": "4",
                "devResourceType": "encodeDevice",
                "networkStatus": 1
            }
        ]
    }
}
```

**Notes / issues:**
- Multi-field search (name + device + region combined) correctly narrowed to exactly 1 real result — confirms combined filtering works correctly on this endpoint, another good contrast to the earlier failed placeholder-name searches.
- **Known collection bug**: same as above.

---

## Folder summary

- Total endpoints in this folder: `3`
- Tested: `3`
- Passed: `3`
- Blocked / failed: `0`
- Last updated: `2026-09-08`
