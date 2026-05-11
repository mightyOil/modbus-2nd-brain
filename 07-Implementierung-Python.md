# Implementierung mit Python (pymodbus)

## Warum pymodbus?
- Vollständige Implementierung (Client + Server + Simulator)
- Sync & Async (asyncio)
- Unterstützt RTU, TCP, Serial, etc.
- Aktiv maintained (2026)

## Installation
```bash
pip install pymodbus
```

## Einfacher TCP Client (Sync)
```python
from pymodbus.client import ModbusTcpClient

client = ModbusTcpClient('192.168.1.100', port=502)
client.connect()

# Read 2 Holding Registers ab Adresse 0
result = client.read_holding_registers(0, 2, slave=1)
print(result.registers)  # z.B. [1234, 5678]

client.close()
```

## Write Beispiel
```python
client.write_register(0, 42, slave=1)           # Einzelnes Register
client.write_registers(0, [100, 200, 300], slave=1)  # Mehrere
client.write_coil(0, True, slave=1)               # Spule einschalten
```

## Server (Simulator) Beispiel
```python
from pymodbus.server import StartTcpServer
from pymodbus.device import ModbusDevice

# Einfacher Server mit Daten
StartTcpServer(
    context=ModbusDevice(
        slaves={0: {  # Slave 0
            'coils': [False]*100,
            'holding_registers': [0]*100
        }}
    ),
    identity=ModbusDeviceIdentity(...),
    address=("0.0.0.0", 502)
)
```

## Nächste Schritte im Projekt
- [ ] Eigenen Simulator starten & mit Client testen
- [ ] Mit realem Gerät (z.B. via USB-RS485 Adapter) verbinden
- [ ] Async Client für bessere Performance
- [ ] Logging + Error-Handling erweitern

**Tipp:** In Obsidian kannst du Code-Blocks mit `python` highlighten und sogar mit Plugins ausführen.

**Nächste Note:** [[09-Ressourcen]]