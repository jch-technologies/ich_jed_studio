---
title: JCH IED Studio
---

[Deutsche Version](index.md) · [Bridge](bridge.en.md) · [Support](support.md)

**Engineering and testing tool for IEC 61850.**
Native macOS and iPadOS app. Loads SCD/ICD/CID files, connects to IEDs
over MMS, receives and sends GOOSE and Sampled Values via the separate
[JCH GOOSE Bridge](bridge.en.md), simulates its own IED on the Mac.

---

## Features

- **MMS client (IEC 61850-8-1)** — connects to IEDs over TCP/102.
  Discovery (GetNameList / GetVAA), Read, Write, Reports (URCB/BRCB),
  Setting Groups, Control services (SBO/Direct), all Phoenix quirks covered.
- **MMS server simulator** — built-in IEC 61850 Edition&nbsp;2.1 server
  (Class A/B). Load SCD, pick an IED, edit variable values, attach
  signal generators (sine, triangle, sawtooth, square, ramp, random)
  to any MX value. Quality + timestamp are maintained automatically.
- **GOOSE & Sampled Values via Bridge** — the separate
  [JCH GOOSE Bridge](bridge.en.md) (standalone, free) handles the
  Layer-2 frame work (libpcap). Studio connects over WebSocket —
  Subscribe + Publish for GOOSE (EtherType 0x88B8) and SV (0x88BA).
- **SCL editor** — Substations, Voltage Levels, Bays, ConductingEquipment,
  IEDs, LDevices, LNs, DataSets, RCBs, GoCBs, Inputs. Export as
  SCD/ICD/IID/CID/SED. Three built-in demo projects for training +
  conformance testing.
- **Spec-compliant SCL export** — `xsi:schemaLocation`, `RptEnabled`,
  correct P-element ordering, transitive DataTypeTemplates closure.
  
---

## Platforms

| Platform | Status |
|---|---|
| **macOS 13+** | Mac App Store, sandboxed |
| **iPadOS 13+** | App Store, sandboxed |

---

## Bridge

- [JCH GOOSE Bridge — download and installation](bridge.en.md)

## Legal & Support

- [Impressum (Deutsch)](impressum.de.md) · [Legal Notice (English)](impressum.en.md)
- [Datenschutzerklärung (Deutsch)](datenschutz.de.md) · [Privacy Policy (English)](datenschutz.en.md)
- [Support](support.md)

## Security

- Security contact: [security@jch-technologies.de](mailto:security@jch-technologies.de)
- Cybersecurity Support Period: 5 years from the initial release of each version
  (CRA Annex II §8)

---

© 2026 Joachim Christof Huben · [mail@jch-technologies.de](mailto:mail@jch-technologies.de)
