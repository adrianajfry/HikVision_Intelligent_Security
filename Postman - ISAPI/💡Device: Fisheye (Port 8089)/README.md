# Device: Fisheye Camera — Port 8089

**Confirmed identity:** matched via `serialNumber` cross-reference against HCP OpenAPI's "Get encoding device list" response (`encodeDevCode: DS-2CD63C5G1-IVS20250709AAWRGB0034379`, `encodeDevIndexCode: "4"`).

| Field | Value |
|---|---|
| Public IP | `175.140.166.217` |
| Port | `8089` |
| Protocol | `http://` |
| Auth type | Digest Auth |
| Username | `admin` |
| Password | `Hik24680!` |
| Status | ✅ Reachable and confirmed |

---

## Endpoint: Get device info

| Field | Value |
|---|---|
| Method | `GET` |
| Path | `/ISAPI/System/deviceInfo` |
| Full URL | `http://175.140.166.217:8089/ISAPI/System/deviceInfo` |
| Status | ✅ Passed |

**Response:**
```xml
<?xml version="1.0" encoding="UTF-8"?>
<DeviceInfo version="2.0" xmlns="http://www.hikvision.com/ver20/XMLSchema">
    <deviceName>IP CAMERA</deviceName>
    <deviceID>8a620000-4af4-11b4-82c5-50e538bbaad1</deviceID>
    <deviceDescription>IPCamera</deviceDescription>
    <deviceLocation>hangzhou</deviceLocation>
    <systemContact>Hikvision.China</systemContact>
    <model>DS-2CD63C5G1-IVS</model>
    <serialNumber>DS-2CD63C5G1-IVS20250709AAWRGB0034379</serialNumber>
    <macAddress>50:e5:38:bb:aa:d1</macAddress>
    <firmwareVersion>V5.8.3</firmwareVersion>
    <firmwareReleasedDate>build 240821</firmwareReleasedDate>
    <encoderVersion>V7.3</encoderVersion>
    <encoderReleasedDate>build 240715</encoderReleasedDate>
    <bootVersion>V1.3.4</bootVersion>
    <bootReleasedDate>100316</bootReleasedDate>
    <hardwareVersion>0x0</hardwareVersion>
    <deviceType>IPCamera</deviceType>
    <telecontrolID>88</telecontrolID>
    <supportBeep>true</supportBeep>
    <supportVideoLoss>false</supportVideoLoss>
    <firmwareVersionInfo>B-R-G7-0</firmwareVersionInfo>
    <manufacturer>hikvision</manufacturer>
    <subSerialNumber>GB0034379</subSerialNumber>
    <OEMCode>1</OEMCode>
    <firmware>opdevsdk mediaDrv:v2.0.0</firmware>
    <platformName>G7</platformName>
</DeviceInfo>
```

**Notes / issues:**
- First working ISAPI call in this project — confirms the full chain: public IP + correct port + HTTP (not HTTPS/RTSP) + Digest Auth with real device credentials.
- Response format is **XML**, not JSON — different from every OpenAPI response documented so far. Parsing/handling logic downstream will need to account for this.
- `serialNumber` is the reliable way to identify which physical camera a port belongs to, since port-to-camera mapping is not otherwise documented (see main README).

---

## Remaining ISAPI endpoints for this device — not yet tested

*(add as tested — e.g., picture/snapshot capture, video streaming info, PTZ control, event/alarm status)*
