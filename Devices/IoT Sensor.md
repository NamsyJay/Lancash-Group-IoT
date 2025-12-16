## IoT Sensor (LoRaWan End Device)
- This cannot be tested directly with ModBusView.
- Confirm the sensor uplinks are updated - Look out for payload, RSSI, and frame counter increasing.
- Verify The Payload Decoding
  ````
    Raw payload: 0A 01 00 FA
    Decoded:
    Temperature = 25.0°C
  ````
- Confirm Modbus Mapping
  ```
  Sensor sends 25.0°C
          ↓
  Gateway writes 250 to 40001
          ↓
  ModbusView reads 40001 = 250
  ```
  
  Modbus is validating - Gateway Logic, Sensor Data arrival.
