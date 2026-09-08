# Logical Resources API - Camera Information

_(POST endpoints in this folder — 4 total)_

**Environment used:** `HCP_OpenAPI`
**Host:** `{{HOSTINFO}}` (`175.140.166.217`)
**API version:** `{{API_VER}}`

---

## Endpoint: Get camera list of an area by area No

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/regions/regionIndexCode/cameras` |
| AK used | `34489509` |
| Signature used | `W8fk9e+F+R8xO9H+eQJG2ycFPiM4FAv5rqPSQSWoiVc=` |
| Status | ✅ Passed |

**Request body:**
```json
{
    "pageNo": 1,
    "pageSize": 10,
    "regionIndexCode": "3",
    "siteIndexCode": "0",
    "deviceType": "encodeDevice"
}
```

**Response:**
```json
{
    "code": "0",
    "msg": "Success",
    "data": {
        "total": 2,
        "pageNo": 1,
        "pageSize": 10,
        "list": [
            {
                "cameraIndexCode": "12",
                "cameraName": "Jetty CCTV",
                "capabilitySet": "face_attributes",
                "devResourceType": "encodeDevice",
                "encodeDevIndexCode": "5",
                "regionIndexCode": "3",
                "siteIndexCode": "0",
                "status": 1
            },
            {
                "cameraIndexCode": "13",
                "cameraName": "Uncle Sam CCTV",
                "capabilitySet": "face_attributes",
                "devResourceType": "encodeDevice",
                "encodeDevIndexCode": "5",
                "regionIndexCode": "3",
                "siteIndexCode": "0",
                "status": 1
            }
        ]
    }
}
```

**Notes / issues:**
- Correctly filtered to only the 2 cameras genuinely belonging to `regionIndexCode: "3"` — both share the same `encodeDevIndexCode: "5"`, suggesting one physical NVR/encoder feeding two camera channels.
- **Refines the earlier region-filter finding**: unlike "Get cameras information in page" (which returned all 6 cameras regardless of the region filter), this endpoint correctly restricts by region. This is endpoint-specific behavior, not an account-wide bug — the URL path itself (`/regions/regionIndexCode/cameras`) is explicitly scoped to a region, while `/cameras` is a general listing that happens to accept (but seemingly ignores) the same filter fields.
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response.

---

## Endpoint: Get cameras information in page

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/cameras` |
| AK used | `34489509` |
| Signature used | `HafAib3Is/J042ARX0zjS9tStrAKn1iy1Bew850fzNg=` |
| Status | ✅ Passed |

**Request body:**
```json
{
    "pageNo": 1,
    "pageSize": 10,
    "regionIndexCode": "3",
    "siteIndexCode": "0",
    "deviceType": "encodeDevice"
}
```

**Response:**
```json
{
    "code": "0",
    "msg": "Success",
    "data": {
        "total": 6,
        "pageNo": 1,
        "pageSize": 10,
        "list": [
            {"cameraIndexCode": "95", "cameraName": "Bullet Camera", "capabilitySet": "event_pdc,face_attributes", "devResourceType": "encodeDevice", "encodeDevIndexCode": "11", "regionIndexCode": "2", "siteIndexCode": "0", "status": 1},
            {"cameraIndexCode": "6", "cameraName": "Fisheye", "devResourceType": "encodeDevice", "encodeDevIndexCode": "4", "regionIndexCode": "2", "siteIndexCode": "0", "status": 1},
            {"cameraIndexCode": "12", "cameraName": "Jetty CCTV", "capabilitySet": "face_attributes", "devResourceType": "encodeDevice", "encodeDevIndexCode": "5", "regionIndexCode": "3", "siteIndexCode": "0", "status": 1},
            {"cameraIndexCode": "89", "cameraName": "NVR-Channel 1", "capabilitySet": "event_pdc", "devResourceType": "encodeDevice", "encodeDevIndexCode": "9", "regionIndexCode": "2", "siteIndexCode": "0", "status": 1},
            {"cameraIndexCode": "55", "cameraName": "TM 80-Cam 3", "devResourceType": "encodeDevice", "encodeDevIndexCode": "8", "regionIndexCode": "4", "siteIndexCode": "0", "status": 2},
            {"cameraIndexCode": "13", "cameraName": "Uncle Sam CCTV", "capabilitySet": "face_attributes", "devResourceType": "encodeDevice", "encodeDevIndexCode": "5", "regionIndexCode": "3", "siteIndexCode": "0", "status": 1}
        ]
    }
}
```

**Notes / issues:**
- 6 real cameras found, spanning all 3 known areas. Two are attached to the encode devices found earlier: "Bullet Camera" → `encodeDevIndexCode: 11`, "NVR-Channel 1" → `encodeDevIndexCode: 9` — confirms these devices and cameras are the same underlying hardware, cross-referenced two different ways.
- - **Filter finding**: filtered by `regionIndexCode: "3"` (Kg.Mukut), but the returned cameras span `regionIndexCode` 2, 3, and 4 — the region filter does not appear to restrict results on this endpoint, unlike "Get camera list of an area by area No" (below), which correctly filters to just the 2 cameras in region 3. Worth flagging to senior as endpoint-specific, inconsistent filter behavior — not a bug in the requests.
- `cameraIndexCode: "55"` ("TM 80-Cam 3") shows `status: 2`, differing from all others (`status: 1`) — likely offline or a different device state; meaning not documented in the collection.
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. 

---

## Endpoint: Search for cameras

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/camera/advance/cameraList` |
| AK used | `34489509` |
| Signature used | `9kg3Vm95PDc2yeRRhgCmYzSzK+tv26tlYfRPzRayhko=` |
| Status | ✅ Passed |

**Request body:**
```json
{
    "pageNo": 1,
    "pageSize": 100,
    "cameraName": "Bullet Camera",
    "siteIndexCode": "0",
    "deviceType": "encodeDevice"
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
        "pageSize": 100,
        "list": [
            {
                "cameraIndexCode": "95",
                "cameraName": "Bullet Camera",
                "capabilitySet": "event_pdc,face_attributes",
                "devResourceType": "encodeDevice",
                "encodeDevIndexCode": "11",
                "regionIndexCode": "2",
                "siteIndexCode": "0",
                "status": 1
            }
        ]
    }
}
```

**Notes / issues:**
- Search by real camera name (`"Bullet Camera"`) returned exactly 1 correct match — confirms name-based search works correctly here, in contrast to earlier "Search for..." endpoints (mobile devices, encoding devices, sites) that returned empty results due to unmatched placeholder names.
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response.

---

## Endpoint: Get a camera information by camera ID

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/cameras/indexCode` |
| AK used | `34489509` |
| Signature used | `eNCrB7s9DXjV4LiYSutyM9UUoAK9mShUnuA613nAmeU=` |
| Status | ✅ Passed |

**Request body:**
```json
{
    "cameraIndexCode": "95"
}
```

**Response:**
```json
{
    "code": "0",
    "msg": "Success",
    "data": {
        "cameraIndexCode": "95",
        "cameraName": "Bullet Camera",
        "capabilitySet": "event_pdc,face_attributes",
        "devResourceType": "encodeDevice",
        "cameraGuid": "7A00DC1E4A7540B7B6F95C4740A2A30F",
        "encodeDevIndexCode": "11",
        "regionIndexCode": "2",
        "siteIndexCode": "0",
        "status": 1
    }
}
```

**Notes / issues:**
- Direct lookup by real ID matches the list entry exactly, plus reveals one bonus field (`cameraGuid`) not shown in the list views — full read chain verified: list → real ID → direct lookup confirms same record with additional detail.
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. 

---

## Folder summary

- Total endpoints in this folder: `4`
- Tested: `4` 
- Passed: `4`
- Blocked / failed: `0`
- Last updated: `2026-09-08`
