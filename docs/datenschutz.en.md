---
title: Privacy Policy
lang: en
---

# Privacy Policy

← [Back to overview](index.md) · [Deutsche Version](datenschutz.de.md) · [Legal Notice](impressum.en.md) · [Support](support.md)

## Controller

Joachim Christof Huben, c/o flexdienst – #11403, Kurt-Schumacher-Straße 76,
67663 Kaiserslautern, Germany.

- E-mail: [mail@jch-technologies.de](mailto:mail@jch-technologies.de)
- Phone: [+49 15679 698581](tel:+4915679698581)

## Types of Data Processed

- **Connection data** for the IEDs you configure (host / IP, TCP port, OSI
  AP-Title, AE-Qualifier, P/S/T selectors, optional display name) and for the
  GOOSE bridge (WebSocket URL).
- **Authentication passwords** (optional, for IEDs that require ACSE auth):
  stored in the **operating system keychain** (macOS Keychain, iOS Keychain)
  in encrypted form. They are NOT transmitted to vendor servers.
- **SCL files** (SCD/ICD/CID/IID) are processed strictly locally — never
  uploaded or shared. The file remains at its original location (via
  `LSSupportsOpeningDocumentsInPlace`).
- **MMS read/write values** (variable values, dataset contents, reports) are
  kept in application memory only and discarded on quit. There is no
  persistent storage.
- **GOOSE frames** (received/sent via the bridge) are kept in memory only,
  in the bridge app and the Studio app. The bridge is a separate, standalone
  helper application with its own privacy policy.

## Purposes of Processing

- Establishing and managing MMS connections to IEC 61850 IEDs.
- Receiving and sending GOOSE messages via the separate bridge app.
- Browsing / subscribing to / querying data points, displaying and testing
  values, RCB management.
- SCL editing and export (SCD/ICD/CID/IID).
- Server simulation (in-app IEC 61850 server for testing purposes).

## Principle

We do **not** process personal data on servers; all data remains locally on
your device. There is no disclosure, no sale and no sharing of data by the
vendor.

## Legal Basis (EU/UK GDPR)

Art. 6(1)(b) GDPR (contract) and Art. 6(1)(a) GDPR (consent) where you
voluntarily enter data (e.g., credentials).

## Recipients / Disclosure

- No disclosure to third parties by the vendor.
- Communication occurs solely between your device and the IEDs / bridge you
  choose. Content provided by the user (e.g., write commands, GOOSE
  publishes) is transmitted solely to those chosen endpoints; the application
  acts as a client only.

## Storage Duration

- Received MMS values and GOOSE frames are kept only temporarily in memory
  and discarded on quit.
- Configurations (saved IED connections, saved bridge URLs, generator
  profiles, loaded SCL models) persist in `SharedPreferences` or the app
  container until you delete them.
- Authentication passwords kept in the OS keychain remain there until you
  delete them in the app by removing the corresponding IED entry.

## Permissions

### macOS (App Store)

- **Network client:** outbound TCP connections to IEDs (port 102) and
  WebSocket connection to the bridge.
- **Network server:** inbound TCP connections for the embedded MMS server
  simulator (port 102 or user-defined).
- **File read/write (user-selected):** for opening SCL files and exporting
  SCD/ICD files via the native file picker.
- **Keychain:** for the encrypted storage of IED authentication passwords.
- **App Sandbox:** fully sandboxed (`com.apple.security.app-sandbox=true`).
- **NO access** to camera, microphone, location, contacts, calendar, photo
  library (apart from an indirect permission string due to a third-party
  library dependency) or other personal resources.

### iOS / iPadOS (App Store)

- **Local network** (`NSLocalNetworkUsageDescription`): for connections to
  IEDs and the bridge on the same subnet.
- **File picker** (Files app / Document Picker): for opening SCL files.
- **Document handling** (`LSSupportsOpeningDocumentsInPlace=YES`): SCL files
  can be opened directly from iCloud Drive / Files app without being copied
  into the app container.
- **NO access** to camera, microphone, location, contacts, calendar or
  similar personal resources.

## Transport and Data Security

- **MMS (IEC 61850-8-1):** ACSE auth (optional, configured per IED) supplies
  the password via the AARQ Authentication-Value field. Plain MMS is
  unencrypted by protocol; security must be provided by the network
  (VPN, VLAN, firewall) or by IEC 62351 extensions on the IED side.
- **GOOSE (IEC 61850-8-1 §15):** L2 multicast, unencrypted by protocol.
  Security is provided by network segmentation (VLAN). Optional VLAN tagging
  can be configured.
- **Bridge WebSocket:** local connection to the `jch_goose_bridge` app
  (typically `ws://localhost:8765` or LAN). Not recommended outside the LAN
  without TLS tunnelling.
- **Warning:** Writes to productive IEDs should only be performed in
  audited, sufficiently secured networks. This application provides no
  multi-user permission control — anyone with access to the device has full
  app access.

## Your Rights (EU/UK)

Access, rectification, erasure, restriction, objection, data portability
(Arts. 15–21 GDPR). Contact as above.

## UK Privacy (UK GDPR)

We comply with UK GDPR in addition to the EU GDPR. The above contact details
also apply to the United Kingdom.

## California Privacy (CPRA)

- We do not sell or share personal data.
- Data is processed only locally on your device. No data is transmitted to us.
- Privacy rights requests: [mail@jch-technologies.de](mailto:mail@jch-technologies.de).
- Not intended for children; we do not knowingly collect data from minors.

## US State Privacy (VA / CO / CT / UT)

- We do not sell or share personal data.
- Data is processed only locally on your device. No data is transmitted to us.
- Privacy rights requests (e.g., access / deletion):
  [mail@jch-technologies.de](mailto:mail@jch-technologies.de).
- Not intended for children; we do not knowingly collect data from minors.

## Changes

These notices may be updated as needed.

---

**As of:** 04.05.2026

→ [Legal Notice](impressum.en.md) · [Support](support.md)
