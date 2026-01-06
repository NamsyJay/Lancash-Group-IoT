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


Sensors Stack
- Arduino/SX1276 Sensor.

ABP vs OTAA Activation.
OTAA - Over The Air Approach.
- The device will join over the air "JoinRequest/JoinAccept".
- The network generates session keys each time; this is a secure and standard practice.
- In TTN, we configure the DevEUI, JoinEUI/AppEUI, AppKey.

LoRaWAN Stack - MCCI LMIC 
Communication
Hardware Connection  
- The sensor connects via SPI;

Software Connection
- The region and radio chip need to be updated in the MCCI LMIC library before compilation.

The Radio Wiring 
- The LMIC
  Types of pins(
  SPI,MISO,SCK).
  RST pin
  DIO pins (usually DIO0, DIO1; sometimes DIO2)

- Match TTN Frequency Plan
  This is because our client is in the UK (EU868); "US902" - if we get a US client.
TTN - The Things Network OTA Setup
- Add device, activate
- Setup DevEUI, JoinEUI, AppKey

