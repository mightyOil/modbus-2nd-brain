# MODBUS Nachrichtenstruktur: PDU & ADU

## Grundprinzip
Jede MODBUS-Nachricht besteht aus:

- **PDU (Protocol Data Unit)**: Der eigentliche Inhalt (Funktionscode + Daten) – **transport-unabhängig**
- **ADU (Application Data Unit)**: PDU + zusätzliche Header/Footer je nach Variante (Adresse, Checksum, MBAP-Header)

## PDU Aufbau (max. 253 Bytes)
```
[ Function Code (1 Byte) ] + [ Data (0–252 Bytes) ]
```
- Function Code: 1–127 (public), 128–255 = Exception
- Data: Adressen, Anzahlen, Werte (Big-Endian)

## ADU je Variante

### RTU ADU
```
[ Slave Address (1B) ] + PDU + [ CRC-16 (2B) ]
```
- CRC berechnet über Address + PDU

### ASCII ADU
```
: [ Addr (2 Hex) ] + PDU (Hex) + [ LRC (2 Hex) ] + CR/LF
```

### TCP ADU (MBAP Header)
```
[ Trans. ID (2B) ] [ Prot. ID (2B=0) ] [ Length (2B) ] [ Unit ID (1B) ] + PDU
```
- Kein CRC, da TCP die Integrität sichert
- Transaction ID: Vom Client frei wählbar (für Matching)

## Request → Response Flow
1. Client sendet Request-PDU
2. Server verarbeitet
3. Server antwortet mit Response-PDU (gleicher FC) oder Exception-PDU (FC + 0x80 + Exception Code)

**Beispiel Request (Read Holding Registers FC=03)**:
- PDU: `03 00 00 00 02` (Start=0, Qty=2)
- TCP ADU: `00 01 00 00 00 06 FF` + PDU

**Nächste:** [[05-Funktionscodes]] mit konkreten Beispielen.