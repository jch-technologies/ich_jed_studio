---
title: JCH IED Studio
---

[English version](index.en.md) · [Bridge](bridge.md) · [Support](support.md)

**Engineering- und Test-Werkzeug für IEC 61850.**
Native macOS- und iPadOS-App. Lädt SCD/ICD/CID-Dateien, verbindet sich mit
IEDs per MMS, empfängt und sendet GOOSE und Sampled Values über die separate
[JCH GOOSE Bridge](bridge.md), simuliert eine eigene IED auf dem Mac.

---

## Funktionen

- **MMS-Client (IEC 61850-8-1)** — verbindet sich mit IEDs über TCP/102.
  Discovery (GetNameList / GetVAA), Read, Write, Reports (URCB/BRCB),
  Setting Groups, Control-Services (SBO/Direct).
- **MMS-Server-Simulator** — eingebauter IEC-61850 Edition&nbsp;2.1 Server
  (Class A/B). SCD laden, IED auswählen, Variablen-Werte editieren,
  Signal-Generatoren (Sinus, Dreieck, Sägezahn, Rechteck, Rampe, Zufall)
  auf jedem MX-Wert. Quality + Timestamp werden automatisch gepflegt.
- **GOOSE & Sampled Values über Bridge** — die separate
  [JCH GOOSE Bridge](bridge.md) (eigenständig, kostenlos) macht die
  Layer-2-Frame-Arbeit (libpcap). Studio verbindet sich per WebSocket —
  Subscribe + Publish für GOOSE (EtherType 0x88B8) und SV (0x88BA).
- **SCL-Editor** — Substations, Voltage Levels, Bays, ConductingEquipment,
  IEDs, LDevices, LNs, DataSets, RCBs, GoCBs, Inputs. Export als
  SCD/ICD/IID/CID/SED. Drei eingebaute Demo-Projekte für Schulung +
  Konformitätstest.
- **Spec-konformer SCL-Export** — `xsi:schemaLocation`, `RptEnabled`,
  korrektes P-Element-Ordering, transitive DataTypeTemplates-Closure.
---

## Plattformen

| Plattform | Status |
|---|---|
| **macOS 13+** | Mac App Store, sandboxed |
| **iPadOS 13+** | App Store, sandboxed |

---

## Bridge

- [JCH GOOSE Bridge — Download und Installation](bridge.md)

## Rechtliches & Support

- [Impressum (Deutsch)](impressum.de.md) · [Legal Notice (English)](impressum.en.md)
- [Datenschutzerklärung (Deutsch)](datenschutz.de.md) · [Privacy Policy (English)](datenschutz.en.md)
- [Support](support.md)

## Sicherheit

- Sicherheitskontakt: [security@jch-technologies.de](mailto:security@jch-technologies.de)
- Cybersecurity Support Period: 5 Jahre ab Erstveröffentlichung jeder Version
  (CRA Annex II §8)

---

© 2026 Joachim Christof Huben · [mail@jch-technologies.de](mailto:mail@jch-technologies.de)
