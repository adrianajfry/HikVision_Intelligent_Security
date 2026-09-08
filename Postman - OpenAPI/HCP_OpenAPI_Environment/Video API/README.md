# Video API

Short one-line description of what this folder's endpoints are for.

**Environment used:** `HCP_OpenAPI` (or `HCP_OpenAPI_2` — note which AK/SK pair)
**Host:** `{{HOSTINFO}}`
**API version:** `{{API_VER}}`

---

## Endpoint: Get the streaming URL for live view
| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/video/{{API_VER}}/cameras/previewURLs` |
| AK used | `34489509` |
| SK used | `2+Ywueu+ITI9aJb12yJ2YGiN9Y7T2GyZYqQ0OujKKSI=` |
| Status | ✅ Passed |

**Request body:**
```json
{
    "cameraIndexCode": "89",
    "streamType": 0,
    "protocol": "rtsp",
    "transmode": 1,
    "requestWebsocketProtocol": 0
}
```

**Response:**
```json
{
    "code": "0",
    "msg": "Success",
    "data": {
        "url": "rtsp://192.168.7.156:554/sms/HCPEurl/commonvideobiz_ZiaOrqNISJQoc5Av9FhjOgrSabmOdXmdmooHxSdnGJLN699uc4%2ByHLNDrPCZXQXkAwnkr5km%2FVHFtn4cbyk62d5eBfUk9A2WCopdI5L5Nu5pNfnt2VeGj2FRMGcYQTRmHReBUZ0rVq6tER89gMzkRgbytnoRxpiwszOfovV99Xle%2FbcNEKAe7y63t3HmOvhaND5ZqlW9b20m8TJTN1DU04NF%2BbYJJ9Y%2Bx20FEEJVr0Hsj3L5EnJqLRqquWnHgVtASHE7nEGSJg%2FozOYlFhOUZg%3D%3D",
        "authentication": "Fsd8eugj2+RYG6EKEgN8/EHy6o5XPdkxD8t7Dy+EH6kXC9WO4slApzuN8UTfiwFY+AXwChjcZpGVvI05fqply39hARllxS3kcrltFx470Km6sECtGiYPP9y93m5H+WIlOrGqm4nnBpWsM3X5PLpi38uKocv+h1VNaopmziXxRvZXuQSsWVavIGt+EEekBViL/tzNcdvj4SyE0jg5yM0to9BrecrTDWIEteWIBJT6GzjVmo0dresQ6OxXUAb8rNbXlIsMB8Ot8Mp/Wa9ZvKxGCUFP7UwMEDUX7TF6ju1OUXo4Z47Jr0lOSIGkSGa3NncP3YLrObQ/WVrRFmlEoRUK4g=="
    }
}
```

**Notes / issues:**
- none for now.

---

## Endpoint: Statistics heat Map By Time
| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/video/{{API_VER}}/cameras/previewURLs` |
| AK used | `34489509` |
| SK used | `I/SEplnn+Y61XdiN/8EO62D2wy3DJJI1D2qCL43CuR0=` |
| Status | ✅ Passed |

**Request body:**
```json
  {
    "cameraIndexCode": "13",
    "statisticsType": 0,
    "beginTime": "2026-09-03T00:00:00+08:00",
    "endTime": "2026-09-04T00:00:00+08:00"
}
```

**Response:**
```json
{
    "code": "0",
    "msg": "Success",
    "data": {
        "maxValue": 0,
        "minValue": 0,
        "averageValue": 0,
        "arrayLine": 0,
        "arrayColum": 0,
        "buffer": ""
    }
}
```

**Notes / issues:**
- none for now.

---

## Endpoint: Statics total number by time
| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/aiapplication/{{API_VER}}/people/advance/resourceGroupList` |
| AK used | `34489509` |
| SK used | `LZ1eADpS4CTiaLOqwH014BofmOoqq8H4PciANsFLhH4=` |
| Status | ✅ Passed |

**Request body:**
```json
{
    "pageNo": 1,
    "pageSize": 2,
    "cameraIndexCodes": "95, 6, 12, 89, 55, 13",
    "statisticsType": 0,
    "startTime": "2026-09-08T00:00:00+08:00",
    "endTime": "2026-09-09T00:00:00+08:00"
}
```

**Response:**
```json
{
    "code": "0",
    "msg": "Success",
    "data": {
        "completeness": 1,
        "pageNo": 0,
        "pageSize": 0,
        "list": [
            {
                "time": "2026-09-08T05:00:00+08:00",
                "cameraIndexCode": "12",
                "exitNum": 2,
                "enterNum": 0
            },
            {
                "time": "2026-09-08T06:00:00+08:00",
                "cameraIndexCode": "12",
                "exitNum": 4,
                "enterNum": 3
            },
            {
                "time": "2026-09-08T07:00:00+08:00",
                "cameraIndexCode": "12",
                "exitNum": 5,
                "enterNum": 5
            },
            {
                "time": "2026-09-08T08:00:00+08:00",
                "cameraIndexCode": "12",
                "exitNum": 6,
                "enterNum": 9
            },
            {
                "time": "2026-09-08T09:00:00+08:00",
                "cameraIndexCode": "12",
                "exitNum": 17,
                "enterNum": 16
            },
            {
                "time": "2026-09-08T10:00:00+08:00",
                "cameraIndexCode": "12",
                "exitNum": 27,
                "enterNum": 29
            },
            {
                "time": "2026-09-08T11:00:00+08:00",
                "cameraIndexCode": "12",
                "exitNum": 34,
                "enterNum": 59
            },
            {
                "time": "2026-09-08T12:00:00+08:00",
                "cameraIndexCode": "12",
                "exitNum": 38,
                "enterNum": 68
            },
            {
                "time": "2026-09-08T13:00:00+08:00",
                "cameraIndexCode": "12",
                "exitNum": 42,
                "enterNum": 73
            },
            {
                "time": "2026-09-08T14:00:00+08:00",
                "cameraIndexCode": "12",
                "exitNum": 49,
                "enterNum": 99
            },
            {
                "time": "2026-09-08T15:00:00+08:00",
                "cameraIndexCode": "12",
                "exitNum": 53,
                "enterNum": 108
            },
            {
                "time": "2026-09-08T08:00:00+08:00",
                "cameraIndexCode": "95",
                "exitNum": 1,
                "enterNum": 1
            },
            {
                "time": "2026-09-08T10:00:00+08:00",
                "cameraIndexCode": "95",
                "exitNum": 1,
                "enterNum": 2
            },
            {
                "time": "2026-09-08T11:00:00+08:00",
                "cameraIndexCode": "95",
                "exitNum": 3,
                "enterNum": 1
            },
            {
                "time": "2026-09-08T12:00:00+08:00",
                "cameraIndexCode": "95",
                "exitNum": 2,
                "enterNum": 2
            },
            {
                "time": "2026-09-08T13:00:00+08:00",
                "cameraIndexCode": "95",
                "exitNum": 2,
                "enterNum": 1
            },
            {
                "time": "2026-09-08T14:00:00+08:00",
                "cameraIndexCode": "95",
                "exitNum": 1,
                "enterNum": 1
            },
            {
                "time": "2026-09-08T15:00:00+08:00",
                "cameraIndexCode": "95",
                "exitNum": 3,
                "enterNum": 0
            },
            {
                "time": "2026-09-08T16:00:00+08:00",
                "cameraIndexCode": "95",
                "exitNum": 1,
                "enterNum": 1
            }
        ]
    }
}
```

**Notes / issues:**
- none for now.

---

## Endpoint: Get Resource Group List
| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/aiapplication/{{API_VER}}/people/advance/resourceGroupList` |
| AK used | `34489509` |
| SK used | `MkLJfmWtaMdE8k3mh9qsvsvXvY2v+A7sg5rUXSdML1Q==` |
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
- none for now.

---

## Endpoint: Resource Group Real Time Count

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/aiapplication/{{API_VER}}/people/resourceGroupRealTimeCount` |
| AK used | `34489509` |
| SK used | `odnUarSlGk0WsFXac578WnSbuMzhmvT5k9VdoxAvCj4=` |
| Status | ✅ Passed |

**Request body:**
```json
{
    "resourceGroupIndexCodes": "1"
}
```

**Response:**
```json
{
    "code": "0",
    "msg": "Success",
    "data": {
        "list": [
            {
                "timebeginTime": "2026-09-08T00:00:00+08:00",
                "resourceGroupIndexCode": "1",
                "resourceGroupName": "People Counting",
                "exitNum": 10,
                "enterNum": 10,
                "limitNum": 0
            }
        ]
    }
}
```

**Notes / issues:**
- none for now.

---

## Endpoint: Search for presets

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/video/{{API_VER}}/presets/searches` |
| AK used | `34489509` |
| SK used | `OIDlNprGz5R+bnoRtZQF0U4d+KwEd4QgIy2nFwWFtqA=` |
| Status | ✅ Passed |

**Request body:**
```json
{
    "cameraIndexCode": "89"
}
```

**Response:**
```json
{
    "code": "0",
    "msg": "Success",
    "data": {
        "total": 0
    }
}
```

**Notes / issues:**
- none for now.

---

## Endpoint: [Example]

| Field | Value |
|---|---|
| Method | `POST` |
| Path | `/artemis/api/aiapplication/{{API_VER}}/people/resourceGroupRealTimeCount` |
| AK used | `34489509` |
| SK used | `odnUarSlGk0WsFXac578WnSbuMzhmvT5k9VdoxAvCj4=` |
| Status | ✅ Passed / ❌ Failed / ⚠️ Blocked (no permission) |

**Request body:**
```json
{
    "resourceGroupIndexCodes": "1"
}
```

**Response:**
```json
{
    "code": "0",
    "msg": "Success",
    "data": {
        "list": [
            {
                "timebeginTime": "2026-09-08T00:00:00+08:00",
                "resourceGroupIndexCode": "1",
                "resourceGroupName": "People Counting",
                "exitNum": 10,
                "enterNum": 10,
                "limitNum": 0
            }
        ]
    }
}
```

**Notes / issues:**
- none for now.

---

## Endpoint: [Next endpoint name]

*(repeat the block above for each endpoint tested in this folder)*

---

## Folder summary

- Total endpoints in this folder: `X`
- Tested: `X`
- Passed: `X`
- Blocked / failed: `X`
- Last updated: `YYYY-MM-DD`
