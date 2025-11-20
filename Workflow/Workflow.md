## This follows the workflow of the Architecture.

- Experience Layer (Devices): 
  How it behaves:
    - These devices will talk to your backend over HTTPS protocol.
    - THey do notcommunicate directly with field equipment.

- Process Layer (IoT API, Machine Gateway, Translation, Permissions):
  How It Behaves:
    - IoT API (Magneta Service):
      This is the front door for all app and system calls.
    - Machine Gateway (Lambda):
      The first Lambda hop after the API for device-relatd operations.
        - Maps user or app requests.
        - Handles retirs/basic error handling around talking to the IoT backend.
    - Translation (Lambda Chain):
      Lambda job to normalise and enrich data.
      Different fucntions for device types and message types.
    - Permissions (Magenta Services):
      This handles authentication and permissons policies.

## WORK SKETCH
    1) IoT API receives the call
    2) IoT API asks permission.
    3) If allowed, IoT API hands off to Machine Gateway and then Translation.
    4) Response is sent back to the Experience Layer.

- Edge Layer (Device + Control Plane)
  How The Service Behaves:
  - Devices emit telemetry & events
  - IoT Greengrass & local edge
    Runs on hospital gateways / on-prem servers / in ambulances.
  - IoT Core / Gateway.
    Greengrass or devices connect to IoT Core endpoints.
    Rules engine routes messages:
    - To Kinesis for real-time streams.
    - To Lambdas (Machine Gateway/Translation) for application processing.
    - To DynamoDB for current state / digital twin records.
  - Defender + Advisor
    Device Advisor: used earlier in the lifecycle to certify that
    each device model behaves correctly  with IoT Core (good test harness).
  - Device Defender: Monitors metrics, audits IoT policies and certs
  - Data Lake: The findings flow into this layer and can be accessed in the experience layer.
  - Fleet Management:
    IoT Device Jobs - schedules firmware updates, config pushes and maintainace actions.
    Fleet Hub - gives operational teams operational teams in a single pane of glass.
    (Anomalies, fleet health and job success).
    Device Location - tracks where assets (static & mobile).

- Data Lake Layer (Data & Analytics plane)
  Kinesis 
  - From IoT Core rules and edge gateways, raw telemetry lands on Kinesis
    - Near-real-time stream of device readings, alarms, status changes.
    - Consumers of this stream
      - Lambda functions feeding DynamoDB with “latest state” per device
      - Kinesis Firehose / custom consumers dropping data into S3 (raw zone) of the Data Lake.
      - Real-time analytics / alerting components.
  DynamoDB
  - Holds current and recent state, optimised for low-latency reads/writes.
    - Device shadow / digital twin (online/offline, firmware version, config, last-seen).
    - Active alarms, workflow status, etc.\
  - The Process Layer (IoT API, Machine Gateway, Translation).
    - UI screens showing “current status”.
    - Real-time checks in business logic.
  Raw & curated history – Data Lake (S3)
  - All historical streams land here, typically in partitioned objects (by date, device, tenant, etc.).
  - Contains:
    - Raw payloads from devices (for forensic/debug).
    - Normalised, translated events from the Translation Lambdas.
    - Aggregated metrics for analytics and ML.
  ETL/Batch Movemment
    - Move data between DynamoDB, S3, and other stores (e.g. Redshift, OpenSearch).
    - Run scheduled batch jobs: daily compaction, backfill, reprocessing when schemas change.
  Governance & access control – Lake Formation.
    - Sits over the S3 Data Lake.
    - Fine-grained permissions per role/tenant (which teams can see which patients, which hospital’s data.
    - When analytics tools query data, they respect the same privacy and tenancy rules
      you enforce in the Process/Experience layers.
