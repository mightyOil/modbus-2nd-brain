# Fehlerbehandlung, Exceptions & Integrität

## Mögliche Fehler-Szenarien
1. **Kommunikationsfehler** (Parity, CRC, Framing) → Keine Antwort (Timeout auf Client-Seite)
2. **Logischer Fehler** (ungültige Adresse, Wert) → **Exception Response**
3. **Gerätefehler** (Busy, Failure) → Exception

## Exception Codes (wichtigste)
| Code | Bedeutung                          | Typische Ursache                     |
|------|------------------------------------|--------------------------------------|
| 01   | Illegal Function                   | FC nicht unterstützt               |
| 02   | Illegal Data Address               | Adresse existiert nicht / falsch     |
| 03   | Illegal Data Value                 | Wert außerhalb erlaubtem Bereich   |
| 04   | Server Device Failure              | Interner schwerer Fehler             |
| 05   | Acknowledge                        | Lange Verarbeitung – später poll en |
| 06   | Server Device Busy                 | Gerät beschäftigt – später retry |
| 0A   | Gateway Path Unavailable           | Gateway kann Ziel nicht erreichen   |
| 0B   | Gateway Target Device Failed       | Ziel-Gerät antwortet nicht         |

## CRC & LRC Berechnung
- **RTU**: CRC-16-MODBUS (polynomial 0xA001)
- **ASCII**: LRC = Zweierkomplement der Summe aller Bytes
- Viele Libraries (pymodbus) erledigen das automatisch

## Best Practices
- Immer Timeouts setzen (z.B. 1-5s)
- Retries bei Busy/Exception 05/06
- Logging von Requests + Responses + Exceptions
- Bei TCP: Transaction ID zum Matching nutzen

**Nächste:** [[07-Implementierung-Python]] – endlich Code!