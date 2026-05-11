# Die wichtigsten MODBUS Funktionscodes (FC)

## Übersicht der Public Function Codes (1–127)

| FC (Hex) | Name                              | Beschreibung                              | Typ     | Max. Items |
|----------|-----------------------------------|-------------------------------------------|---------|------------|
| 01 (01) | Read Coils                       | Lese Spulen (bool)                       | Read    | 2000      |
| 02 (02) | Read Discrete Inputs             | Lese diskrete Eingänge                 | Read    | 2000      |
| 03 (03) | Read Holding Registers           | Lese Halteregister (16-Bit)              | Read    | 125       |
| 04 (04) | Read Input Registers             | Lese Eingangsregister                    | Read    | 125       |
| 05 (05) | Write Single Coil                | Schreibe einzelne Spule                  | Write   | 1         |
| 06 (06) | Write Single Holding Register    | Schreibe einzelnes Register              | Write   | 1         |
| 0F (15) | Write Multiple Coils             | Schreibe mehrere Spulen                  | Write   | 1968      |
| 10 (16) | Write Multiple Holding Registers | Schreibe mehrere Register                | Write   | 123       |
| 17 (23) | Read/Write Multiple Registers    | Kombi Read + Write in einem Request     | Both    | -         |
| 2B (43) | Read Device Identification       | Geräte-Info (Vendor, Product, etc.)    | Read    | -         |

## Detailliertes Beispiel: Read Holding Registers (03)
**Request PDU**:
- `03` + Start Address (2B) + Quantity (2B)

**Response PDU**:
- `03` + Byte Count (1B) + Data (n*2B)

**Beispiel** (Start 0, Qty 2):
- Request: `03 00 00 00 02`
- Response: `03 04 12 34 56 78` (Werte 0x1234, 0x5678)

## Write Single Coil (05)
- `05` + Address (2B) + Value (2B: 0xFF00=ON, 0x0000=OFF)

## Exception Response
- FC wird um 0x80 erhöht (z.B. 03 → 83)
- Dann 1 Byte Exception Code (1=Illegal Function, 2=Illegal Data Address, 3=Illegal Data Value...)

**Vollständige Liste & Details**: Offizielle Spec V1.1b3 (siehe Resources)

**Nächste Note:** [[06-Fehlerbehandlung]]