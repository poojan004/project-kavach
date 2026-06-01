# Network Traffic Analysis Report

## Project

Project KAVACH

## Team

Offline

### Team Members

- Poojan Patel
- Shilpa Soni

---

# Executive Summary

A network traffic capture associated with an XLoader malware infection was analyzed using Wireshark.

The objective of this investigation was to identify suspicious communications, understand network behavior, and determine indicators associated with the infection.

Analysis identified multiple suspicious DNS lookups, outbound communications to external infrastructure, HTTP activity, and traffic patterns consistent with malware execution.

The overall assessment indicates a compromised host communicating with external systems after malware execution.

Risk Level: High

---

# Scope

The following packet capture was analyzed:

2025-01-30-XLoader-infection-traffic.pcap

Analysis included:

- Protocol review
- DNS investigation
- IP analysis
- HTTP traffic review
- IOC identification
- Threat assessment

---

# Tools Used

| Tool | Purpose |
|--------|---------|
| Wireshark | Packet analysis |
| DNS Filters | Domain investigation |
| Endpoint Review | Traffic interpretation |

---

# Protocol Analysis

Wireshark protocol hierarchy review identified the following traffic:

| Protocol | Observation |
|----------|-------------|
| TCP | Primary communication protocol |
| HTTP | Web communication observed |
| TLS | Encrypted sessions present |
| DNS | Domain resolution activity |
| ARP | Local network communication |
| SMB | Limited internal communication |

Total packets analyzed:

18224 packets

---

# DNS Activity Analysis

DNS traffic revealed multiple domain lookups.

Examples observed:

- physicsbrain.xyz
- bydotoparca.net
- autonomousrich.xyz
- corellia.pro
- trustai.chat
- spreadsyndicate.net
- bitcoinescort.xyz
- sigmaque.today
- hotethereum.xyz

Several domains exhibited characteristics commonly associated with suspicious infrastructure:

- Random naming conventions
- Newly observed domains
- Uncommon top-level domains
- High volume of lookups

DNS activity suggests malware attempting to locate remote infrastructure.

---

# HTTP Activity Analysis

HTTP traffic was observed between the infected workstation and external servers.

Observed methods:

- GET
- POST

Example URI observed:

/s3u9/

POST requests indicate data transmission from the infected endpoint to external systems.

This behavior is frequently observed during:

- Malware beaconing
- Data submission
- Command retrieval
- Status reporting

---

# External Communications

The infected host communicated with several external IP addresses.

Examples include:

| IP Address |
|------------|
| 76.223.54.146 |
| 13.248.169.48 |
| 85.159.66.93 |
| 31.31.196.17 |
| 217.160.0.90 |

These communications occurred following DNS resolution activity.

---

# Indicators of Compromise (IOCs)

## Domains

- physicsbrain.xyz
- bydotoparca.net
- autonomousrich.xyz
- spreadsyndicate.net
- sigmaque.today
- hotethereum.xyz

## IP Addresses

- 76.223.54.146
- 13.248.169.48
- 85.159.66.93
- 31.31.196.17
- 217.160.0.90

---

# Findings

## Finding N-01

Title:
Suspicious DNS Activity

Severity:
High

Description:

Numerous DNS queries were generated toward suspicious domains exhibiting characteristics commonly associated with malware infrastructure.

Impact:

Potential communication with attacker-controlled systems.

---

## Finding N-02

Title:
External Host Communications

Severity:
High

Description:

The infected workstation established outbound communications with multiple external IP addresses after domain resolution.

Impact:

Potential malware command-and-control communication.

---

## Finding N-03

Title:
HTTP POST Requests Observed

Severity:
Medium

Description:

HTTP POST requests were observed from the endpoint to external infrastructure.

Impact:

Potential transmission of malware telemetry or stolen information.

---

# Attack Flow Assessment

The following infection sequence is the most likely scenario:

1. User receives malicious email
2. Malicious attachment executed
3. XLoader installed
4. Malware performs DNS lookups
5. Infrastructure resolved
6. Outbound communication established
7. Malware exchanges information with remote systems

---

# Risk Assessment

| Category | Rating |
|-----------|---------|
| Infection Confidence | High |
| Suspicious DNS Activity | High |
| External Communication | High |
| Data Exposure Risk | Medium |
| Overall Risk | High |

---

# Recommendations

Immediate actions recommended:

1. Isolate affected endpoint
2. Block identified domains
3. Block identified IP addresses
4. Collect endpoint forensic evidence
5. Perform malware scanning
6. Review email gateway logs
7. Monitor network for recurring indicators
8. Reset affected user credentials

---

# Conclusion

Analysis of the provided packet capture identified multiple indicators consistent with malware-related activity.

The infected workstation performed suspicious DNS lookups, established outbound communications, and generated HTTP requests toward external systems.

The observed behavior aligns with known malware communication patterns and indicates compromise of the analyzed endpoint.

The overall risk associated with this activity is assessed as High.

---

Report Prepared By

Team Offline

Members:

- Poojan Patel
- Shilpa Soni
