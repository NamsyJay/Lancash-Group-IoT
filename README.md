## Lancash-Group-IoT
This Project is a POC for Lancash Group; The Company is implementing an IoT System to monitor devices in their Healthcare and Farm.

This Project structure allows for secure, scalable data collection from edge devices, real-time processing, centralised analytics, and integration with both user-facing apps and enterprise systems (SAP). It demonstrates layered, modern architecture principles-separating edge, process, data lake and experience while ensuring third-party observability and privacy solutions. 

Project Architecture & Components
This IoT Project is composed of multiple layers running in AWS and enterprise systems.

  - Experience Layer:
    - Mobile, PC - ``It provides user access via clients and mobile clients``.
  - Process Layer:
    - IoT API, Machine Gateway, Translation, IAM Permissions
  - Data Lake:
    - Amazon DynamoDB, AWS Data Pipeline, Kinesis Lake Formation, DataLake.
  - Edge:
    - IoT Greengrass, IoT Device Defender, Device Advisor, IoT Device jobs, Fleet Hub, Device Location
  - Equipment:
    - (Agriculture) - Drones and Satellites, Animal activity and location trackers, Soil Monitors. 
    - (HealthCare) - Cardiac Monitoring Sensors, Blood Pressure Sensors and Remote Heart rate Monitors.
