# Physical Resource API - Encode Device Information

_(POST endpoints in this folder — 3 total)_

**Environment used:** `HCP_OpenAPI`
**Host:** `{{HOSTINFO}}` (`175.140.166.217`)
**API version:** `{{API_VER}}`

---

## Endpoint: Get encoding device list

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/ncodeDevice/encodeDeviceList` |
| AK used | `34489509` |
| Signature used | `wa9y+I0vGYuCZksGPVE3whl8TI8Kpo+pIr88+W1g1ls=` |
| Status | ✅ Passed |

**Request body:**
```json
{
    "pageNo": 1,
    "pageSize": 2
}
```

**Response:**
```json
{
    "code": "0",
    "msg": "Success",
    "data": {
        "total": 5,
        "pageNo": 1,
        "pageSize": 2,
        "list": [
            {
                "encodeDevIndexCode": "11",
                "encodeDevName": "Bullet Camera",
                "encodeDevIp": "192.168.7.117",
                "encodeDevPort": "8000",
                "encodeDevCode": "iDS-2CD7A46G2-IZHSY20251211AAWRGM0538247",
                "treatyType": "hiksdk_net",
                "status": 1,
                "isSupportWakeUp": 0,
                "wakeUpStatus": -1,
                "pictureStorePosType": 0
            },
            {
                "encodeDevIndexCode": "9",
                "encodeDevName": "NVR",
                "encodeDevIp": "192.168.7.160",
                "encodeDevPort": "8000",
                "encodeDevCode": "DS-9664NI-I81620230526CCRRAB7049567WCVU",
                "treatyType": "hiksdk_net",
                "status": 1,
                "isSupportWakeUp": 0,
                "wakeUpStatus": -1,
                "pictureStorePosType": 0
            }
        ]
    }
}
```

**Notes / issues:**
- **Confirmed URL typo bug**: original collection path was `.../ncodeDevice/encodeDeviceList` (missing "e"). Corrected to `.../encodeDevice/encodeDeviceList` and the request now returns real data instead of `code: 8`. Confirms this was a collection authoring bug, not an account/product limitation.
- **Corrects earlier account-wide assumption**: this account is *not* fully empty — it has 5 registered encoding devices (a camera and an NVR). Only some resource types (mobile devices, stream servers, storage servers, access control devices) are genuinely empty; encode devices are not. Updated in `TESTING_LOG.md`.
- **New real IDs available for chaining**: `encodeDevIndexCode: "11"` (Bullet Camera) and `"9"` (NVR) — usable in "Get an encoding device information" below instead of the placeholder value.
- ⚠️ **Fix applied in the Postman app only, not saved back to the exported `.json` collection file** — if the collection is ever re-imported from the original file, the typo will return. Worth exporting/saving the corrected version, or noting this needs to be reapplied.
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response.

---

## Endpoint: Search for encoding devices

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/encodeDevice/advance/encodeDeviceList` |
| AK used | `34489509` |
| Signature used | `cGa4+Pn/6jwhA6Pja+lTdszKNqS6GAMq2a7qEDqOdgs=` |
| Status | ✅ Passed (empty result) |

**Request body:**
```json
{
    "pageNo": 1,
    "pageSize": 10,
    "encodeDevName": "devicename"
}
```

**Response:**
```json
{
    "code": "0",
    "msg": "Success",
    "data": {
        "total": 0,
        "pageNo": 1,
        "pageSize": 10
    }
}
```

**Notes / issues:**
- Request succeeded fully (`code: 0`, Success) via the correctly-spelled path — supports the URL-typo theory confirmed above.
- `"total": 0` here **despite 5 real encoding devices existing** (per "Get encoding device list" above) — almost certainly because the request body filters by `"encodeDevName": "devicename"`, a placeholder name that doesn't match either real device ("Bullet Camera" / "NVR"). Worth re-testing with `encodeDevName` removed, or set to `"Bullet Camera"`, to confirm the search itself works correctly.
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response.

---

## Endpoint: Get an encoding device information

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/encodeDevice/indexCode/encodeDeviceInfo` |
| AK used | `34489509` |
| Signature used | `zpM49sDHcMgURw/VDy59L74dYfrT2oh7OJmPhrns56E=` |
| Status | ✅ Passed |

**Request body:**
```json
{
    "encodeDevIndexCode": "11"
}
```

**Response:**
```json
{
    "code": "0",
    "msg": "Success",
    "data": {
        "encodeDevIndexCode": "11",
        "encodeDevName": "Bullet Camera",
        "encodeDevIp": "192.168.7.117",
        "encodeDevPort": "8000",
        "encodeDevCode": "iDS-2CD7A46G2-IZHSY20251211AAWRGM0538247",
        "treatyType": "hiksdk_net",
        "status": 1,
        "isSupportWakeUp": 0,
        "wakeUpStatus": -1,
        "pictureStorePosType": 0,
        "timeZone": {
            "enableDST": 0,
            "bias": -480
        }
    }
}
```

**Notes / issues:**
- **This is the first end-to-end "trace API backward" chain completed with real data in this documentation pass**: `Get encoding device list` (root, no ID needed) → returned real `encodeDevIndexCode: "11"` → fed into this endpoint → returned full device detail. This is a clean, concrete example of the API-sequencing question, using real verified data instead of a hypothetical.
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response.

---

## Folder summary

- Total endpoints in this folder: `3`
- Tested: `3`
- Passed: `3`
- Blocked / failed: `0`
- ⚠️ Contains at least one endpoint with the known copy-pasted test-script bug (schema expects `produceName`/`softVersion`).
- Last updated: `2026-09-07`
