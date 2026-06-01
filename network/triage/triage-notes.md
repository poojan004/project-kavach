# Network Traffic Triage Notes

## Dataset Information

Dataset: 2025-01-30 XLoader Infection Traffic

Analyst: Poojan Patel and Shilpa soni

Review Date: June 2026

---

## Initial Review

The packet capture was loaded into Wireshark and reviewed using protocol hierarchy statistics and packet-level inspection.

The capture contains 18,224 packets and represents a Windows host communicating with multiple external systems.

---

## Protocol Distribution

| Protocol | Observation |
|-----------|------------|
| IPv4 | Primary protocol observed |
| TCP | Dominant transport protocol (98.0%) |
| DNS | Used for domain resolution |
| HTTP | Used for outbound communications |
| TLS | Encrypted sessions observed |
| ARP | Local network communications |

---

## Host Under Investigation

Internal Host:

10.1.30.242

This host generated DNS lookups and established outbound HTTP/TCP connections to external systems.

Based on current observations, this system is considered the likely infected endpoint.

---

## Domains Observed

- www.physicsbrain.xyz
- bydotoparca.net

---

## External IP Addresses Observed

- 76.223.54.146
- 85.159.66.93

---

## Suspicious Behaviour

Multiple outbound HTTP POST requests were observed during analysis.

One observed URI:

/s3u9/

The traffic pattern is consistent with malware initiating communications after domain resolution.

The capture also contains URL-encoded HTTP content, which may indicate command-and-control communication or transfer of host information.

---

## Preliminary Assessment

Current evidence suggests that host 10.1.30.242 initiated outbound communications to external infrastructure following DNS resolution.

The communication pattern is consistent with malware infection activity and warrants deeper investigation.

Status: Under Investigation
