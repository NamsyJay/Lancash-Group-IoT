# SLA, SLO and SLI

## Service Level Agreement:- 
- A contractual agreement that outlines the level of service end users expect from CISOLNS. This is the promise.
- To ensure high-quality, reliable, and secure delivery of IoT, cloud, and analytics services, supporting business-critical operations in Lancash   Group.
### - PARTIES
- Service Provider: Cloud Infrastructure Solutions
- Client: Lancash Group

## Service Level Objectives:- 
- The  Objectives your team must hit to meet that agreement. This is the goal.
### - PERFORMANCE METRICS
- Service Availability:
  Definition: Uptime across all core services
  Target: `99.99`
  
- Data Ingestion Latency:
  Definition: Time to ingest data from devices to the cloud
  Target: `<2 Seconds`
  
- API Response Time:
  Definition: Processing time for API requests
  Target: `<2 Seconds`
  
- Incident Response Time:
  Definition: Time to respond to critical issues
  Target: `<2 Hours`
  
- Resolution Time:
  Definition: Time to restore services after an incident
  Target: `<4 Hours`
  
- Data Integrity:
  Definition: Successful transmission/storage of sensor/device data
  Target: `99.99%`
  
- Security Compliance:
  Definition: Compliance with relevant regulations.
  Target: `100 Conformant`
  
- Backup and Recovery:
  Definition: Data backup frequency and restoration
  Target: `<4 Daily Backups` 
  
## Service Level Indicators:- 
- The real numbers on your performance. This is how we did.

## Error Budgets:
- The acceptable levels of unreliability for a service before it falls out of compliance with an SLO. These are the differences between 100% reliability and the SLO target.

## Exclusions
- Any service not expressly defined in the SLA.
- External network failures outside provider control
- Third-party app failures unless integrated via approved interfaces.

## Penalties And Remedies
- Failure to meet the agreed SLOs results in credits or penalties to be negotiated in advance.
