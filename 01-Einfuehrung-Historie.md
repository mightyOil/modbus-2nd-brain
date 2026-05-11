# MODBUS: Einführung & Historie

## Was ist MODBUS?
MODBUS ist ein **Application-Layer-Protokoll** für die Kommunikation zwischen Geräten in der industriellen Automatisierung. Es ermöglicht Master-Slave (heute Client-Server) Kommunikation über serielle Schnittstellen oder Netzwerke.

- **Einfach & robust**: Wenige Datenformate, polling-basiert
- **De-facto-Standard** in Industrie (PLCs, Sensoren, Aktoren, Energiezähler, SCADA)
- **Kostenlos & offen**: Keine Lizenzgebühren seit 2004 (Modbus Organization)

## Historie
- **1979**: Entwickelt von Modicon (heute Schneider Electric) für ihre PLCs
- **Zweck**: Einheitliche Sprache zwischen verschiedenen Herstellern
- **1997**: Modicon → Schneider Electric
- **2004**: Rechte an Modbus Organization übertragen (User & Supplier Trade Association)
- **Heute**: V1.1b3 (2012) + Erweiterungen (Security, etc.)

## Warum MODBUS immer noch relevant?
- Millionen von Nodes weltweit
- Günstig & einfach zu implementieren
- Wird in China sogar nationaler Standard (GB/T 19582)

## Moderne Sicht
Ursprünglich Master-Slave, heute oft **Client-Server**. Broadcast möglich (Address 0).

**Nächste Note:** [[02-Varianten-RTU-ASCII-TCP]] für die Übertragungsarten.