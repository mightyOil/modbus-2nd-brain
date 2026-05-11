# MODBUS Datenmodell: Die 4 Tabellen

MODBUS definiert ein einfaches, aber mächtiges **abstraktes Datenmodell** mit 4 logischen Tabellen. Jede Tabelle hat bis zu 65.536 Adressen (0–65535).

## Die 4 Datentypen

| Tabelle              | Typ          | Zugriff     | Beschreibung                          | Typische Verwendung          |
|----------------------|--------------|-------------|---------------------------------------|------------------------------|
| **Coils**           | 1-Bit (bool) | Read/Write | Diskrete Ausgänge / interne Bits     | Relais, Ventile, Flags      |
| **Discrete Inputs** | 1-Bit (bool) | Read-only  | Physikalische Eingänge / Status     | Taster, Sensoren, Limits    |
| **Holding Registers**| 16-Bit Word | Read/Write | Konfigurations- & Steuerwerte        | Sollwerte, Parameter, Zähler |
| **Input Registers** | 16-Bit Word | Read-only  | Messwerte & Status von der Hardware   | Temperatur, Spannung, Zähler |

## Wichtige Regeln
- **Big-Endian**: 16-Bit-Werte immer MSB zuerst (z.B. 0x1234 = Byte 0x12 dann 0x34)
- **Mehrere Register lesen/schreiben**: Immer aufeinanderfolgende Adressen
- **Maximale Anzahl pro Request**:
  - Read Coils/Discrete: bis 2000
  - Read Registers: bis 125
  - Write Multiple: bis 123 (Registers) / 1968 (Coils)

## Adressierung
- **0-basiert** in der Protokoll-Spezifikation
- Viele Geräte/Software verwenden **1-basiert** (z.B. 40001 für erstes Holding Register)
- **Beispiel**: Holding Register 0 = Adresse 0x0000

## Praktischer Tipp
In der Praxis mappst du oft:
- Coils → digitale Ausgänge
- Discrete Inputs → digitale Eingänge
- Holding Registers → Konfiguration + Steuerung
- Input Registers → Sensor-Daten

**Nächste Note:** [[04-Nachrichtenstruktur]] – wie die Daten verpackt werden.