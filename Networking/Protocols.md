## MQTT Protocol
- The MQTT protocol TCP/IP port 1883 is reserved with IANA; port 8883 is registered.
- The MQTT Protocol is preferred over the SSL Protocol because of low bandwidth. A firewall is placed
  over the clients (Area1 and Area2), allowing flow from clients to the broker.
- All clients can publish and subscribe to the MQTT protocol.
- MQTT is lightweight and scalable; it identifies unreliable networks and has security features enabled.
- It uses a publish/subscribe architecture; it is not designed for time-critical solutions.

## Modbus TCP/IP Protocol
- It is used to link different vendors to communicate with devices.
- Server/Client Architecture; each device will have a unique IP address; the Ethernet protocol is used with
  Fibre optic for communication. 
- It communicates on port 502
- Waveshare Device (RS232/485/TTL), Remote IO device, Finder device with (A=, B- ports).
- Belden 3105A cables are used; D-shell 9-pin connector (male/female view)
- Device Data bus (Modbus TCP) sends to Cloud Provider(Azure);
  then links to CLOUD WEB analysis or Direct WEB Analysis when connected via an internal LAN.
- It is used by legacy systems and does not have security.

IoT Devices  
## IoT Sensor (LoRaWan End Device)
- This cannot be tested directly with ModBusView.
- Confirm the sensor uplinks are updated - Look out for payload, RSSI, and frame counter increasing.
- Verify The Payload Decoding
  `Raw payload: 0A 01 00 FA
    Decoded:
    Temperature = 25.0°C
  `
- Confirm Modbus Mapping
  `Sensor sends 25.0°C
          ↓
  Gateway writes 250 to 40001
          ↓
  ModbusView reads 40001 = 250
  `
  Modbus is validating - Gateway Logic, Sensor Data arrival.
- 
