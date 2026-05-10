---
title: JCH GOOSE Bridge
---

# JCH GOOSE Bridge

← [Übersicht / Overview](index.md)

Kostenloses macOS-Helferprogramm, das GOOSE- und Sampled-Values-Frames
via libpcap mit dem Stationsnetz austauscht. JCH IED Studio (iPad/Mac)
verbindet sich per WebSocket.

## Download

- [**Aktuelle Version (.dmg, 2.6 MB)**](JCH-GOOSE-Bridge-0.1.0.dmg)

> **Warum nicht über den Mac App Store?**
> Die Bridge braucht `libpcap`-Zugriff auf rohe Ethernet-Frames, und das
> verbietet die App-Store-Sandbox. Deshalb verteilen wir die Bridge direkt
> als signiertes `.dmg`.

## Systemvoraussetzungen

- macOS 13 (Ventura) oder neuer — Apple Silicon und Intel werden unterstützt (Universal Binary).
- Mac muss im selben Netzwerk wie das iPad / der zweite Mac sein, der die App ausführt.
- Administrator-Rechte für den ersten Start (BPF-Zugriff einrichten — siehe unten).

## Installation

### 1. DMG laden und Bridge in `/Applications` ziehen

Lade die aktuelle [`.dmg`](JCH-GOOSE-Bridge-0.1.0.dmg), öffne sie per
Doppelklick und ziehe **JCH 61850 GOOSE Bridge** in den `Programme`-Ordner.

### 2. Erststart: Gatekeeper bestätigen

Die Bridge ist ad-hoc-signiert (kein Apple-Developer-Zertifikat), deshalb
blockiert Gatekeeper den ersten Start. Lösung:

- **Rechtsklick** auf das App-Icon → *Öffnen*.
- Im aufpoppenden Dialog nochmal auf *Öffnen*.
- Beim zweiten Start startet die App ohne Rückfrage.

### 3. BPF-Zugriff freigeben (einmalig)

`libpcap` liest und schreibt rohe Ethernet-Frames über das `/dev/bpf*`-Device.
Standard-User können darauf nicht zugreifen, deshalb braucht es einmalig
erweiterte Rechte. Es gibt zwei Wege:

**Variante A — Permission-Helper (empfohlen):** Die Bridge bringt einen
kleinen Setup-Assistenten mit. Beim ersten Start erscheint ein Hinweis-Fenster
mit dem Button *BPF-Rechte einrichten*. Klick öffnet eine Admin-Abfrage und
passt `/dev/bpf*`-Permissions an. Danach läuft die Bridge ohne weitere Eingriffe.

**Variante B — Manuell per Terminal:**

```
sudo chmod 644 /dev/bpf*
```

Diese Einstellung hält bis zum nächsten Reboot. Wer es persistent will, legt
einen LaunchDaemon an — der Helper aus Variante A erledigt das automatisch.

### 4. Netzwerk-Interface wählen

Nach dem Start liegt die Bridge als Symbol in der Menüleiste. Klick →
*Interface wählen*. In der Liste das Ethernet-Interface auswählen, das mit
dem Stationsbus verbunden ist (z.&nbsp;B. `en0` oder ein USB-Ethernet-Adapter
wie `en7`).

> **VLAN-getaggte Pakete:** Wenn dein Stationsbus VLAN-Tags verwendet, fragt
> die Bridge beim ersten Senden nach Admin-Rechten und legt automatisch ein
> passendes `vlanXXX`-Interface an. Der Kernel setzt das 802.1Q-Tag —
> `pcap_sendpacket` allein kann das auf macOS nicht.

### 5. Verbindung mit JCH IED Studio

1. In der App: Tab *Bridge*.
2. WebSocket-URL eingeben: `ws://<Mac-IP>:8765` (Bridge-Default-Port).
3. *Verbinden* tippen — der Status-Punkt wird grün.
4. GOOSE/SV-Tabs zeigen jetzt Live-Frames vom gewählten Interface.

## Was die Bridge tut — und was nicht

| Funktion | Bridge |
|---|---|
| GOOSE empfangen (EtherType 0x88B8) | ✓ |
| GOOSE senden (mit Retransmission-Profil) | ✓ |
| Sampled Values empfangen (EtherType 0x88BA) | ✓ |
| Sampled Values senden (rohe APDU-Bytes) | ✓ |
| VLAN-Tagging via Kernel-`vlanX`-Interface | ✓ |
| MMS / Reports / Control-Services | nicht nötig — geht direkt aus der App über TCP |
| Bonjour-Advertising (App findet Bridges automatisch) | ✓ |

## Deinstallation

1. Bridge im Menüleisten-Symbol → *Beenden*.
2. `JCH 61850 GOOSE Bridge.app` aus `/Applications` in den Papierkorb ziehen.
3. Falls ein LaunchDaemon für persistente BPF-Rechte angelegt wurde:

```
sudo launchctl unload /Library/LaunchDaemons/com.jch.bpf.plist
sudo rm /Library/LaunchDaemons/com.jch.bpf.plist
```

## Fragen, Bugs, Wünsche

Siehe [Support](support.md).
