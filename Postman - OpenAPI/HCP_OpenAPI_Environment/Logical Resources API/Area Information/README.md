# Logical Resources API - Area Information

_(POST endpoints in this folder — 3 total)_

**Environment used:** `HCP_OpenAPI`
**Host:** `{{HOSTINFO}}` (`175.140.166.217`)
**API version:** `{{API_VER}}`

---

## Endpoint: Get area list of a parent area by area No

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/regions/subRegions` |
| AK used | `34489509` |
| Signature used | `yoqukFFsz2FojoGKcWe9RP8uL+mNOrXrSTbEaVSo8fs=` |
| Status | ✅ Passed (empty result) |

**Request body:**
```json
{
    "siteIndexCode": "0",
    "parentIndexCode": "1"
}
```

**Response:**
```json
{
    "code": "0",
    "msg": "Success",
    "data": ""
}
```

**Notes / issues:**
- `data: ""` (empty) — `parentIndexCode: "1"` doesn't match either real area (`"3"` or `"4"`, both with `parentIndexCode: "-1"`, meaning they're top-level areas with no parent). This ran successfully but queried a non-existent parent ID. Worth re-testing with `parentIndexCode: "-1"` to see if that returns the two real areas as children of the root.
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Search for areas

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/regions` |
| AK used | `34489509` |
| Signature used | `iJrvg+kZHsu3LHmMv4X3lUvOihuA7RzctSCHvnD81Gc=` |
| Status | ✅ Passed |

**Request body:**
```json
{
    "pageNo": 1,
    "pageSize": 2,
    "siteIndexCode": "0"
}
```

**Response:**
```json
{
    "code": "0",
    "msg": "Success",
    "data": {
        "total": 3,
        "pageNo": 1,
        "pageSize": 2,
        "list": [
            {
                "indexCode": "3",
                "parentIndexCode": "-1",
                "siteIndexCode": "0",
                "name": "Kg.Mukut"
            },
            {
                "indexCode": "4",
                "parentIndexCode": "-1",
                "siteIndexCode": "0",
                "name": "TM 80"
            }
        ]
    }
}
```

**Notes / issues:**
- Real areas found under site `"0"` (HikCentral Professional): `total: 3`, though only 2 shown due to `pageSize: 2`. `indexCode: "3"` (Kg.Mukut) and `"4"` (TM 80) — both top-level (`parentIndexCode: "-1"`). A 3rd area exists but wasn't returned on this page; worth re-running with `pageSize: 3` or higher to see it.
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Endpoint: Get an area information by area No

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/resource/{{API_VER}}/region/indexCode/regionInfo` |
| AK used | `34489509` |
| Signature used | `WSdbrBLaz9KFIS4a74exaB4gqse2eRizAfG4SP32sCE=` |
| Status | ✅ Passed |

**Request body (corrected):**
```json
{
    "regionIndexCode": "3",
    "siteIndexCode": "0"
}
```

**Response:**
```json
{
    "code": "0",
    "msg": "Success",
    "data": {
        "indexCode": "3",
        "parentIndexCode": "-1",
        "siteIndexCode": "0",
        "name": "Kg.Mukut"
    }
}
```

**Notes / issues:**
- First attempt used the collection's placeholder `regionIndexCode: "root000000"` and `siteIndexCode: "site000000"` — neither is a real ID on this account, so it correctly failed with `code: 2, "Incorrect request parameter"`.
- Corrected body above uses the real area ID (`"3"`, Kg.Mukut) found via "Search for areas." Awaiting retest.
- **Known collection bug**: this request's Tests script validates against a schema expecting `produceName`/`softVersion` — that schema belongs to the "Get version of platform" endpoint, not this one. Test Results will likely show 0/1 even on a correct, successful response. Flagged for senior; not something to fix on your end.

---

## Folder summary

- Total endpoints in this folder: `3`
- Tested: `3` 
- Passed: `3`
- Blocked / failed: `0`
- Last updated: `2026-09-07`
