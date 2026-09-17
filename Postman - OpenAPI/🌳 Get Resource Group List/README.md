# Get Resource Group List

**Role:** Prerequisite (root — no dependency) for `Get Resource Group Real Time Count`

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/aiapplication/{{API_VER}}/people/advance/resourceGroupList` |
| AK used | `34489509` |
| Signature used | `MkLJfmWtaMdE8k3mh9qsvsvXvY2v+A7sg5rUXSdML1Q=` |
| Status | ✅ Passed |

**Request body:**
```json
{
    "pageNo": 1,
    "pageSize": 10
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
                "resourceGroupIndexCode": "1",
                "resourceGroupName": "People Counting",
                "siteIndexCode": "0",
                "peopleCountingParam": {
                    "relatedResourceInfoList": [
                        {
                            "resourceType": 1,
                            "resourceIndexCode": "95",
                            "resourceName": "Bullet Camera",
                            "entryExitConfig": 1
                        }
                    ]
                }
            }
        ]
    }
}
```

**Notes / issues:**
- Root call — no dependency, just paging.
- Real `resourceGroupIndexCode: "1"` ("People Counting" group) found, linked to camera `95` (Bullet Camera) — cross-references the same camera confirmed in "Get Cameras Information In Page."
- This endpoint is not part of the original 143-endpoint Postman collection; it belongs to the separate `aiapplication` API family, tested via the official guide's own tutorial/example directly in Postman.
