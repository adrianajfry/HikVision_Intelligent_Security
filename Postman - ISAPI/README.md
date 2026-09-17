# ISAPI Documentation — HikCentral Cameras

Documentation for direct camera-level API calls (ISAPI), as a companion to the existing HCP OpenAPI documentation. ISAPI is a **fundamentally different API layer** from everything documented so far — this file explains the differences before diving into individual device docs.

---

## How ISAPI differs from HCP OpenAPI

| | HCP OpenAPI (Artemis) | ISAPI |
|---|---|---|
| **Talks to** | HikCentral server (a proxy in front of all devices) | The camera/device directly |
| **Auth method** | AK/SK + HMAC-SHA256 signature (`X-Ca-Key`/`X-Ca-Signature` headers) | HTTP Digest Auth — device username + password |
| **Response format** | JSON | **XML** |
| **Addressing** | One shared host (`{{HOSTINFO}}`) for every call | Each device has its **own port** on the shared public IP — no single "host" covers everything |
| **Credentials** | AK/SK pairs shared for the whole HCP account | Per-device login (found so far: `admin` / `Hik24680!`) |

**Practical implication:** every ISAPI request needs its own port, and that port has to be confirmed to actually belong to the camera you think it does — port-to-camera mapping is **manually configured, not documented or guaranteed consistent** (confirmed by Aiman, the engineer managing the network side). Don't assume a port number based on naming or ordering; always verify via the response itself (see "How to identify a camera" below).

---

## How to identify which camera a port belongs to

Call `/ISAPI/System/deviceInfo` on the port in question, then match the returned `<serialNumber>` against the `encodeDevCode` field from HCP OpenAPI's **"Get encoding device list"** response (already documented in the main OpenAPI docs). The serial number is a unique fingerprint — an exact string match confirms the identity with certainty, no guessing required.

---

## Known ports and protocols so far

| Port | Protocol | Result | Notes |
|---|---|---|---|
| `1056` | (assumed HTTP) | ❌ Socket hang up | Turned out to be an **RTSP** port (video streaming), not HTTP/ISAPI — wrong protocol entirely, not a credentials issue |
| `1056` | HTTPS | ❌ TLS handshake failed | HTTPS is **not enabled** on this device/network per Aiman — don't retry HTTPS until confirmed otherwise |
| `8089` | HTTP | ✅ **Working** | Confirmed = **Fisheye camera** (see device file) |
| `1026` | HTTP | ❌ Request timed out (multiple attempts) | Unresolved — forwarded to Aiman. Timeout (not hang-up/refusal) suggests either a NAT/port-forwarding issue, or the device behind it is genuinely offline. Possible link: `cameraIndexCode: "55"` ("TM 80-Cam 3") showed `status: 2` in OpenAPI data, unlike every other camera's `status: 1` — plausible this is the same offline device, unconfirmed. |

---

## Files in this folder

- `device - Fisheye (port 8089).md` — first confirmed working device
- *(add one file per confirmed camera as ports are resolved)*

**Last updated:** 2026-09-15
