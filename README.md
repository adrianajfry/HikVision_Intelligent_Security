# People Counting & Event Subscription — HCP OpenAPI Documentation

This is a **focused subset** of the full HCP OpenAPI collection, scoped only to the APIs actually needed for the People Counting / Alarm Subscription project (per the finalized tracking sheet). It replaces the broader 28-folder documentation effort for this purpose — only 6 endpoints are needed in total: 4 target APIs and 2 shared prerequisites.

**Environment used:** `HCP_OpenAPI` (AK `34489509`)
**Host:** `175.140.166.217`
**API version:** `v1`

---

## Dependency chain (verified, zero-guesswork roots)

```
Get Cameras Information In Page   (root — pageNo/pageSize + fixed "encodeDevice" constant only)
  → real cameraIndexCode values: 95, 6, 12, 55, 89, 13
    ├─→ Statistics Total Number By Time   (needs: cameraIndexCodes)
    └─→ Statistics Heat Map By Time        (needs: cameraIndexCode)

Get Resource Group List   (root — pageNo/pageSize only)
  → real resourceGroupIndexCode: "1" ("People Counting")
    └─→ Get Resource Group Real Time Count   (needs: resourceGroupIndexCodes)

Event Subscription By Event Types   (root — no API dependency)
  → eventTypes / alarm category codes come from a static reference table
    (Developer Guide Appendix A.3 "Event Types or Alarm Categories," p.797),
    not from any endpoint. token and eventDest are caller-defined values.
```

## Files in this set

| File | Role |
|---|---|
| `Get Cameras Information In Page.md` | Prerequisite for Statistics Total Number By Time & Statistics Heat Map By Time |
| `Get Resource Group List.md` | Prerequisite for Get Resource Group Real Time Count |
| `Get Resource Group Real Time Count.md` | Target API |
| `Statistics Total Number By Time.md` | Target API |
| `Statistics Heat Map By Time.md` | Target API |
| `Event Subscription By Event Types.md` | Target API (no prerequisite needed) |

## Cross-checked against official documentation

All 6 endpoints, their parameters, and the two bug fixes below have been verified against *HikCentral Professional OpenAPI V3.1.0 Developer Guide* (V3.1.0, 2026-01-30 build):

- `regionIndexCode` and `siteIndexCode` were removed from the "Get Cameras Information In Page" prerequisite call — neither is required; `siteIndexCode` defaults to the current site, and `regionIndexCode` isn't even a documented parameter for this endpoint.
- `deviceType` is a fixed enum (`mobileDevice` / `encodeDevice` / `acsDevice`) from the guide, not an API-derived value.

---

*Superseded scope note: the original 28-folder documentation project (Common API, Physical Resource API, Logical Resources API, etc.) remains valid and complete for its own purposes, but is not required for this People Counting / Event Subscription track. See the original `TESTING_LOG.md` for that broader effort.*
