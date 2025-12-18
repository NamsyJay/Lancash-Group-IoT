## Modbus Target
### Workflow
- Converting LoRa payloads into:
  - Modbus Registers
  - Input Registers
- Every sensor value is mapped to a fixed register address

### Testing
1) Connection
- IP Address: Gateway IP, Port 502, Unit ID:
- Port: Active

2) Start simple
- Variable Type: `Holding Registers 4xxx`
- Start Register: 001
- Display Length: 10
- Click `Read`

If you see non-zero values, Modbus is functioning.

### Troubleshooting
### 3) Common IoT Gateway challenges:
- Symptom           Cause                        Fix
- Always 0 ->   Wrong Register Block ->     Try Input Registers
- Wierd Big Numbers -> Float stored as int -> Change Display
- Values Swapped   ->   Endianness    ->     Swap Word Order(adjusting order from one device to another)
- Nothing Reads    -> Wrong Start Address    ->  Try 000 instead of 0001


- Scaling Issues: Gateways may store `25.6°C` as `256`; So check the scaling factor in the gateway docs.
- Multi-sensor mapping: `sensor 1 Temp -> 40001`, `sensor 2 Temp -> 40101`; ensure the reading has the correct register block.


### The End-To-End Application
- Gateways
  - Create and fill in the credentials.
  - Frequency plan:- Europe 863-870 MHz
  - Duty Cycle (Listen before Talk Optional) 
- Onboard by creating an application
  - Fill in the credentials
  - Click the button on the node to reset and show the uplink data message.
  - Fill in payload formatter (JavaScript Formatter)
- Integration depends on Application (MTTQ, Webhooks, AWS IoT)  
- Start the Node.js application in the terminal.
- View in the browser.
  - Press the button on the device to refresh data.
