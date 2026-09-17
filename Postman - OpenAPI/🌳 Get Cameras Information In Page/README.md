# Get Cameras Information In Page

**Role:** Prerequisite (root — no dependency) for `Statistics Total Number By Time` and `Statistics Heat Map By Time`

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/cameras` |
| AK used | `34489509` |
| Signature used | `HafAib3Is/J042ARX0zjS9tStrAKn1iy1Bew850fzNg=` |
| Status | ✅ Passed |

**Request body (final, zero-dependency version):**
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
        "total": 6,
        "pageNo": 1,
        "pageSize": 10,
        "list": [
            { "cameraIndexCode": "95", "cameraName": "Bullet Camera", "encodeDevIndexCode": "11", "status": 1 },
            { "cameraIndexCode": "6", "cameraName": "Fisheye", "encodeDevIndexCode": "4", "status": 1 },
            { "cameraIndexCode": "12", "cameraName": "Jetty CCTV", "encodeDevIndexCode": "5", "status": 1 },
            { "cameraIndexCode": "55", "cameraName": "TM 80-Cam 3", "encodeDevIndexCode": "8", "status": 2 },
            { "cameraIndexCode": "89", "cameraName": "TMDA NVR-Channel 1", "encodeDevIndexCode": "9", "status": 1 },
            { "cameraIndexCode": "13", "cameraName": "Uncle Sam CCTV", "encodeDevIndexCode": "5", "status": 1 }
        ]
    }
}
```
*(full field set — capabilitySet, recordType, recordLocation, regionIndexCode, siteIndexCode, isSupportWakeUp, wakeUpStatus — omitted above for brevity; all present in the actual tested response)*

**Notes / issues:**
- **This is a true zero-dependency root call.** Earlier versions of this request included `siteIndexCode` and `regionIndexCode`, which looked like real prerequisite IDs but weren't actually required: `siteIndexCode` defaults to "the current site" per the official guide if omitted, and `regionIndexCode` isn't a documented parameter for this endpoint at all (silently ignored, not a real filter). Confirmed by retesting with both removed — identical 6-camera result.
- `deviceType` is a fixed enum value (`mobileDevice` / `encodeDevice` / `acsDevice`) from the official guide, not something fetched via API.
- Camera `89`'s name changed between test runs (`"NVR-Channel 1"` → `"TMDA NVR-Channel 1"`) — same underlying device (`encodeDevIndexCode: 9`), likely just a display-name edit on the account side, not a bug.
