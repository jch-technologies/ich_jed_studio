---
title: Datenschutzerklärung
lang: de
---

# Datenschutzerklärung

← [Zurück zur Übersicht](index.md) · [English version](datenschutz.en.md) · [Impressum](impressum.de.md) · [Support](support.md)

## Verantwortlicher

Joachim Christof Huben, c/o flexdienst – #11403, Kurt-Schumacher-Straße 76,
67663 Kaiserslautern, Deutschland.

- E-Mail: [mail@jch-technologies.de](mailto:mail@jch-technologies.de)
- Telefon: [+49 15679 698581](tel:+4915679698581)

## Arten der verarbeiteten Daten

- **Verbindungsdaten** zu den von Ihnen konfigurierten IEDs (Hostname / IP,
  TCP-Port, OSI-AP-Title, AE-Qualifier, P/S/T-Selektoren, optionaler
  Anzeigename) sowie zur GOOSE-Bridge (WebSocket-URL).
- **Authentifizierungs-Passwörter** (optional, für IEDs die ACSE-Auth
  verlangen): werden im **Betriebssystem-Schlüsselbund** (macOS Keychain,
  iOS Keychain) verschlüsselt abgelegt. Sie werden NICHT an Server des
  Herstellers übertragen.
- **SCL-Dateien** (SCD/ICD/CID/IID): werden ausschließlich lokal verarbeitet,
  weder hochgeladen noch geteilt. Die Datei verbleibt am Original-Speicherort
  (über `LSSupportsOpeningDocumentsInPlace`).
- **MMS-Lese-/Schreibwerte** (Variablenwerte, DataSet-Inhalte, Reports): werden
  nur im Arbeitsspeicher der Anwendung gehalten und beim Beenden verworfen.
  Eine persistente Speicherung erfolgt nicht.
- **GOOSE-Frames** (empfangen/gesendet via Bridge): nur im Arbeitsspeicher der
  Bridge-App und der Studio-App. Die Bridge ist eine separate, eigenständige
  Helper-Anwendung mit eigener Datenschutzerklärung.

## Zwecke der Verarbeitung

- Aufbau und Verwaltung von MMS-Verbindungen zu IEC-61850-IEDs.
- Empfang und Versand von GOOSE-Nachrichten über die separate Bridge-App.
- Browsing / Abonnement / Abfrage von Datenpunkten, Anzeige und Test von
  Werten, RCB-Verwaltung.
- SCL-Editing und -Export (SCD/ICD/CID/IID).
- Server-Simulation (eigener IEC-61850-Server für Testzwecke).

## Grundsatz

Wir verarbeiten **keine personenbezogenen Daten serverseitig**; alle Daten
verbleiben lokal auf Ihrem Gerät. Es erfolgt keine Weitergabe, kein Verkauf
und kein Teilen von Daten durch den Hersteller.

## Rechtsgrundlage

Art. 6 Abs. 1 lit. b DSGVO (Erfüllung eines Nutzungsvertrags) und lit. a
(Einwilligung), soweit Sie freiwillig Daten (z. B. Zugangsdaten) eingeben.

## Empfänger / Weitergabe

- Keine Weitergabe an Dritte durch den Hersteller.
- Kommunikation findet ausschließlich zwischen Ihrem Gerät und den von Ihnen
  gewählten IEDs / der Bridge statt. Vom Nutzer eingegebene Inhalte
  (z. B. Write-Befehle, GOOSE-Publishes) werden ausschließlich an diese
  gewählten Endpunkte übermittelt; die Anwendung fungiert nur als Client.

## Speicherdauer

- Empfangene MMS-Werte und GOOSE-Frames werden nur temporär im
  Arbeitsspeicher gehalten und beim Beenden gelöscht.
- Konfigurationen (gespeicherte IED-Verbindungen, gespeicherte Bridge-URLs,
  Generator-Profile, geladene SCL-Modelle) bleiben in den `SharedPreferences`
  bzw. im App-Container bis zur Löschung durch Sie erhalten.
- Im OS-Schlüsselbund gespeicherte Auth-Passwörter bleiben dort, bis Sie sie
  in der App durch Löschen des entsprechenden IED-Eintrags entfernen.

## Berechtigungen

### macOS (App Store)

- **Netzwerk-Client:** ausgehende TCP-Verbindungen zu IEDs (Port 102) und
  WebSocket-Verbindung zur Bridge.
- **Netzwerk-Server:** eingehende TCP-Verbindungen für den eingebauten
  MMS-Server-Simulator (Port 102 oder benutzerdefiniert).
- **Datei-Lese/-Schreib (User-Selected):** für das Öffnen von SCL-Dateien und
  Export von SCD/ICD-Dateien über den nativen File-Picker.
- **Schlüsselbund:** für die verschlüsselte Speicherung von IED-Auth-Passwörtern.
- **App Sandbox:** vollständig sandboxed (`com.apple.security.app-sandbox=true`).
- **KEIN Zugriff** auf Kamera, Mikrofon, Standort, Kontakte, Kalender,
  Fotomediathek (außer indirekter Anzeige im Permission-String wegen einer
  indirekten Bibliotheks-Abhängigkeit) oder ähnliche persönliche Ressourcen.

### iOS / iPadOS (App Store)

- **Lokales Netzwerk** (`NSLocalNetworkUsageDescription`): für Verbindungen
  zu IEDs und der Bridge im selben Subnetz.
- **Datei-Auswahl** (Files-App / Document Picker): für das Öffnen von
  SCL-Dateien.
- **Document-Owning** (`LSSupportsOpeningDocumentsInPlace=YES`): SCL-Dateien
  können direkt aus iCloud Drive / Files-App geöffnet werden, ohne in den
  App-Container kopiert zu werden.
- **KEIN Zugriff** auf Kamera, Mikrofon, Standort, Kontakte, Kalender oder
  ähnliche persönliche Ressourcen.

## Transport- und Datensicherheit

- **MMS (IEC 61850-8-1):** ACSE-Auth optional pro IED konfigurierbar (Password
  über AARQ Authentication-Value-Field). Plain-MMS ist protokollbedingt
  unverschlüsselt; Absicherung muss über das Netzwerk erfolgen
  (VPN, VLAN, Firewall) oder über IEC-62351-Erweiterungen am IED.
- **GOOSE (IEC 61850-8-1 §15):** L2-Multicast, protokollbedingt unverschlüsselt.
  Absicherung erfolgt durch Netzwerk-Segmentierung (VLAN). Optional kann der
  Standardweg auf VLAN-Tagging eingeschränkt werden.
- **Bridge-WebSocket:** lokale Verbindung zur `jch_goose_bridge`-App (in der
  Regel `ws://localhost:8765` oder im LAN). Außerhalb des LAN nicht zu
  empfehlen ohne TLS-Tunneling.
- **Warnung:** Schreibvorgänge auf produktive IEDs sollten nur in geprüften,
  ausreichend abgesicherten Netzwerken durchgeführt werden. Diese Anwendung
  bietet keine Multi-User-Berechtigungssteuerung — wer Zugriff auf das Gerät
  hat, hat den vollen Zugriff der App.

## Ihre Rechte

Auskunft, Berichtigung, Löschung, Einschränkung, Widerspruch,
Datenübertragbarkeit (Art. 15–21 DSGVO). Kontakt siehe oben.

## UK Datenschutz (UK GDPR)

Zusätzlich zur DSGVO beachten wir das UK GDPR. Die oben genannten Kontaktdaten
gelten auch für das Vereinigte Königreich.

## California Privacy (CPRA)

- We do not sell or share personal data.
- Data is processed only locally on your device. No data is transmitted to us.
- Privacy rights requests: [mail@jch-technologies.de](mailto:mail@jch-technologies.de).
- This application is not intended for children; we do not knowingly collect
  data from minors.

## US State Privacy (VA / CO / CT / UT)

- We do not sell or share personal data.
- Data is processed only locally on your device. No data is transmitted to us.
- Privacy rights requests (e.g., access / deletion):
  [mail@jch-technologies.de](mailto:mail@jch-technologies.de).
- This application is not intended for children.

## Änderungen

Diese Hinweise können bei Bedarf aktualisiert werden.

---

**Stand:** 04.05.2026

→ [Impressum](impressum.de.md) · [Support](support.md)
