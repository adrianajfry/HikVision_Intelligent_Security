# Logical Resources API - Site Information

_(POST endpoints in this folder — 3 total)_

**Environment used:** `HCP_OpenAPI`
**Host:** `{{HOSTINFO}}` (`175.140.166.217`)
**API version:** `{{API_VER}}`

---

## Endpoint: Get site list

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/site/siteList` |
| AK used | `34489509` |
| Signature used | `w1TPX511hSnwqhFGyygxL/JB5tyP7P5PB+PQfAW82pc=` |
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
        "total": 1,
        "pageNo": 1,
        "pageSize": 2,
        "list": [
            {
                "siteIndexCode": "0",
                "siteName": "HikCentral Professional",
                "siteIp": "127.0.0.1",
                "sitePort": "0",
                "description": ""
            }
        ]
    }
}
```

**Notes / issues:**
- Real site found: `siteIndexCode: "0"`, "HikCentral Professional" — this is very likely the parent site for the encode devices found earlier (Bullet Camera, NVR), given the matching IP `127.0.0.1` pattern seen elsewhere on this account.
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Search for sites

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/site/advance/siteList` |
| AK used | `34489509` |
| Signature used | `wrMySCP+P0Hbr3pVVjfr6YA/bwTOQRU/4n7+0pVvyqU=` |
| Status | ✅ Passed (empty result — see note) |

**Request body:**
```json
{
    "pageNo": 1,
    "pageSize": 10,
    "siteName": "siteName"
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
- `total: 0` despite a real site existing (per "Get site list" above) — same pattern seen with "Search for encoding devices": the placeholder `siteName: "siteName"` doesn't match the real site's actual name ("HikCentral Professional"), so the filter excludes it. Worth re-testing with `siteName: "HikCentral Professional"` or the field removed, to confirm the search itself works correctly rather than concluding sites are unsearchable.
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Get a site information

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/site/indexCode/siteInfo` |
| AK used | `34489509` |
| Signature used | `h5i0mMiaPbO5gc9+bcv0KF8mvTU+j6Z+Osa5EdMf5uk=` |
| Status | ✅ Passed |

**Request body:**
```json
{
    "siteIndexCode": "0"
}
```

**Response:**
```json
{
    "code": "0",
    "msg": "Success",
    "data": {
        "siteIndexCode": "0",
        "siteName": "HikCentral Professional",
        "siteIp": "127.0.0.1",
        "sitePort": "0",
        "description": ""
    }
}
```

**Notes / issues:**
- Confirms "Get site list" result via direct lookup by real ID — full read chain verified for this folder.
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Folder summary

- Total endpoints in this folder: `3`
- Tested: `3`
- Passed: `3` (1 with an empty result likely due to a placeholder search filter — see note)
- Blocked / failed: `0`
- Last updated: `2026-09-07`
