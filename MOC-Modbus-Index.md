# MOC: MODBUS - Gesamtübersicht & Einstieg

> **Map of Content** für das MODBUS-Tiefenverständnis-Projekt. Dein zentraler Einstiegspunkt.

## Kern-Themen (Pfad für tiefes Verständnis)

1. [[01-Einfuehrung-Historie]] - Was ist MODBUS? Warum existiert es? Historie seit 1979
2. [[02-Varianten-RTU-ASCII-TCP]] - Die verschiedenen Übertragungsarten im Detail
3. [[03-Datenmodell]] - Die 4 Tabellen: Coils, Discrete Inputs, Holding & Input Registers
4. [[04-Nachrichtenstruktur]] - PDU vs. ADU, Aufbau von Requests & Responses
5. [[05-Funktionscodes]] - Die wichtigsten FCs mit Hex-Beispielen & Anwendung
6. [[06-Fehlerbehandlung]] - Exceptions, Timeouts, CRC/LRC
7. [[07-Implementierung-Python]] - pymodbus Beispiele (Client & Server)
8. [[08-Sicherheit-Limitierungen]] - Warum MODBUS unsicher ist & moderne Alternativen
9. [[09-Ressourcen]] - Offizielle Specs, Tools, Bücher, Community

## Praktische Projekte (nächste Ebene)
- Modbus TCP Client/Server simulieren
- Mit realem Gerät (z.B. PLC, Energiezähler) verbinden
- Eigenen Simulator bauen
- Integration in Home Assistant / Node-RED / SCADA

## Tags & Verknüpfungen
#modbus #protokoll #industrial-automation #plc #scada #iot #embedded

## Schnell-Links
- Offizielle Modbus Organization: https://www.modbus.org/
- Protokoll-Spec V1.1b3: https://www.modbus.org/file/secure/modbusprotocolspecification.pdf
- Serial Line Guide: Modbus Serial Line Protocol V1.02

---
**Tipp:** Lies die Notes in der Reihenfolge 1→2→... und notiere Fragen in [[Inbox/Modbus-Fragen.md]]. Wir klären sie gemeinsam!