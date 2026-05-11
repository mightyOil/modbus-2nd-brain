# MODBUS Varianten: RTU, ASCII, TCP & mehr

MODBUS ist **transport-unabhängig** – der Kern (PDU) bleibt gleich, nur die Kapselung (ADU) ändert sich.

## 1. Modbus RTU (Recommended Serial)
- **Häufigste serielle Variante** (RS485, RS232, RS422)
- **Binär**, kompakt
- **Fehlerprüfung**: CRC-16-MODBUS (2 Bytes)
- **Frame**: [Slave Addr 1B] + PDU + CRC
- **Timing**: Mind. 3.5 Char-Zeiten Pause zwischen Frames, max 1.5 zwischen Zeichen
- **Byte-Format**: 1 Start + 8 Data (LSB first) + Parity (even default) + 1 Stop = 11 Bit
- **Max. Slaves**: 247 (Addr 1-247)

## 2. Modbus ASCII (Legacy)
- **Textbasiert** (Hex-ASCII)
- **Fehlerprüfung**: LRC (Longitudinal Redundancy Check)
- **Frame**: `:` + Addr (2 Hex) + PDU (Hex) + LRC (2 Hex) + CR/LF
- **Erlaubt Pausen** bis 1s zwischen Zeichen
- **Weniger effizient**, aber menschlich lesbar

## 3. Modbus TCP/IP (Modern & empfohlen für neue Projekte)
- **Über Ethernet/TCP Port 502**
- **Kein CRC** nötig (TCP sichert schon)
- **Frame (MBAP Header)**: 
  - Transaction ID (2B)
  - Protocol ID (2B = 0)
  - Length (2B)
  - Unit ID (1B, meist 0xFF oder Slave-Adr)
  + PDU
- **Vorteile**: Keine 247-Limit, Gateways einfach, hohe Geschwindigkeit
- **Max PDU**: 253 Bytes

## Weitere Varianten
- **Modbus Plus**: Proprietär (Schneider), Token-Passing, 1 Mbit/s
- **Modbus over UDP**: Weniger Overhead
- **Modbus Security**: Neu (TLS + X.509 Zertifikate, Port 802) – siehe [[08-Sicherheit-Limitierungen]]

**Vergleichstabelle** (in Obsidian Tabelle ergänzen):
| Variante | Medium | Checksum | Max. Devices | Empfehlung |
|----------|--------|----------|--------------|------------|
| RTU     | Serial  | CRC     | 247         | Legacy    |
| TCP     | Ethernet| TCP     | Praktisch unbegrenzt | Neu & Zukunft |

**Nächste:** [[03-Datenmodell]] – die Daten, die übertragen werden.