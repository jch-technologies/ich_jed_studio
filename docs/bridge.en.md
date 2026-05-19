---
title: JCH GOOSE Bridge
---

# JCH GOOSE Bridge

← [Back to overview](index.md) · [Deutsche Version](bridge.md) · [Support](support.md)

Free macOS helper that exchanges GOOSE and Sampled-Values frames with the
station bus via libpcap. JCH IED Studio (iPad/Mac) connects to it over
WebSocket.

## Download

- [**Latest version (.dmg, 2.6 MB)**]({{ '/JCH-GOOSE-Bridge-0.1.0.dmg' | relative_url }})

> **Why not via the Mac App Store?**
> The Bridge needs `libpcap` access to raw Ethernet frames, which the
> App Store sandbox forbids. That's why we ship the Bridge as a signed
> `.dmg` directly.

## System requirements

- macOS 13 (Ventura) or newer — Apple Silicon and Intel both supported (Universal Binary).
- Mac must be on the same network as the iPad / second Mac running the app.
- Administrator rights for the first launch (BPF access setup — see below).

## Installation

### 1. Open the DMG and drag the Bridge into `/Applications`

Download the latest [`.dmg`]({{ '/JCH-GOOSE-Bridge-0.1.0.dmg' | relative_url }}), open it
by double-clicking, and drag **JCH 61850 GOOSE Bridge** into the `Applications` folder.

### 2. First launch: confirm Gatekeeper

The Bridge is ad-hoc signed (no Apple Developer certificate), so Gatekeeper
blocks the first launch. Solution:

- **Right-click** on the app icon → *Open*.
- In the popup dialog, click *Open* again.
- On the second launch, the app starts without prompting.

### 3. Grant BPF access (one-time)

`libpcap` reads and writes raw Ethernet frames via the `/dev/bpf*` device.
Standard users cannot access these, so elevated rights are required once.
Two options:

**Option A — Permission helper (recommended):** The Bridge ships with a
small setup assistant. On first launch, a notice window appears with a
*Set up BPF permissions* button. Clicking it opens an admin prompt and
adjusts `/dev/bpf*` permissions. Afterwards the Bridge runs without
further intervention.

**Option B — Manually via terminal:**

```
sudo chmod 644 /dev/bpf*
```

This setting persists until the next reboot. To make it permanent, install
a LaunchDaemon — the helper from Option A does this automatically.

### 4. Select the network interface

After launch, the Bridge sits in the menu bar. Click → *Select interface*.
From the list, pick the Ethernet interface connected to the station bus
(e.g. `en0` or a USB-Ethernet adapter such as `en7`).

> **VLAN-tagged packets:** If your station bus uses VLAN tags, the Bridge
> asks for admin rights on first send and automatically creates a matching
> `vlanXXX` interface. The kernel sets the 802.1Q tag — `pcap_sendpacket`
> alone cannot do this on macOS.

### 5. Connect from JCH IED Studio

1. In the app: tab *Bridge*.
2. Enter the WebSocket URL: `ws://<Mac-IP>:8765` (Bridge default port).
3. Tap *Connect* — the status dot turns green.
4. GOOSE/SV tabs now display live frames from the selected interface.

## What the Bridge does — and what it doesn't

| Function | Bridge |
|---|---|
| GOOSE receive (EtherType 0x88B8) | ✓ |
| GOOSE send (with retransmission profile) | ✓ |
| Sampled Values receive (EtherType 0x88BA) | ✓ |
| Sampled Values send (raw APDU bytes) | ✓ |
| VLAN tagging via kernel `vlanX` interface | ✓ |
| MMS / Reports / Control services | not needed — handled directly by the app over TCP |
| Bonjour advertising (app discovers Bridges automatically) | ✓ |

## Uninstall

1. Bridge menu-bar icon → *Quit*.
2. Drag `JCH 61850 GOOSE Bridge.app` from `/Applications` to the Trash.
3. If a LaunchDaemon was installed for persistent BPF rights:

```
sudo launchctl unload /Library/LaunchDaemons/com.jch.bpf.plist
sudo rm /Library/LaunchDaemons/com.jch.bpf.plist
```

## Questions, bugs, requests

See [Support](support.md).
