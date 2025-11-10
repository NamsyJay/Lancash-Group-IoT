## Lancash-Group-IoT
This Project is a POC for Lancash Group; The Company is implementing an IoT System to monitor devices in their Healthcare and Farm.

This Project structure allows for secure, scalable data collection from edge devices, real-time processing, centralised analytics, and integration with both user-facing apps and enterprise systems (SAP). It demonstrates layered, modern architecture principles, separating edge, process, data lake, and experience, while ensuring third-party observability and privacy solutions. 

##   Project Architecture & Components
###  This IoT Project is composed of multiple layers running in AWS and enterprise systems.

  - Experience Layer:
    - Mobile, PC - ``It provides user access via clients and mobile clients``
  - Process Layer:
    - IoT API, Machine Gateway, Translation, IAM Permissions - ``Manages IoT API interactions, machine gateway functionality, data translation, and permission logic``
  - Data Lake Layer:
    - Amazon DynamoDB - ``NoSQL database for device or event storage.``
    - AWS Data Pipeline - ``Orchestration and workflow automation.``
    - AWS Kinesis - ``Real-time data streaming for IoT telemetry and logs.``
    - AWS Lake Formation - ``Data Lake management and security.``
    - DataLake - ``Aggregated repository for analysis.``
  - Edge Layer:
    - IoT Greengrass, ``Enables Local Compute, messaging and data management on edge devices``
    - IoT Device Defender, ``Security and Compliance for IoT devices``
    - Device Advisor, IoT Device jobs, Fleet Hub, Device Location ``Device Management Modules``
  - Equipment:
    - (Agriculture) - Drones and Satellites, Animal activity and location trackers, Soil Monitors. 
    - (HealthCare) - Cardiac Monitoring Sensors, Blood Pressure Sensors and Remote Heart rate Monitors.
   
## Workflow
  - Modems exist on clients and machines.
  - Data is captured using AWS IoT GreenGrass.
  - The Captured Data is being filtered through AWS Kinesis, flowing through AWS Data Pipeline and stored in Amazon DynamoDB.
  - Data exists on external cloud platforms like SAP Cloud.
  - Data is being processed through different applications and filtered into various devices (Mobile, PC).
  - This flow is built using a CI/CD Pipeline.
    - In addition to the pipeline, there are several tools in the workflow.
    - Datadog
    - Hotjar
    - CloudFlare
    - Google Analytics
  - A Centralised CIDM (Customer Identity Management) where customer information is managed
