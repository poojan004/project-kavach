# Security Assessment Methodology

## Overview

This document describes the methodology followed during Project KAVACH to assess the security posture of web applications and analyze network traffic associated with suspected malware activity.

The assessment was conducted using a structured approach that included web application security testing, static analysis review, network traffic analysis, threat modeling, and defensive architecture evaluation.

---

## Assessment Objectives

The primary objectives of this assessment were:

- Identify security vulnerabilities in target web applications.
- Validate common OWASP Top 10 attack scenarios.
- Evaluate application security controls before and after remediation.
- Analyze network traffic for indicators of malicious activity.
- Identify Indicators of Compromise (IOCs).
- Develop threat models based on observed attack patterns.
- Recommend defense-in-depth security improvements.

---

## Web Application Security Assessment Methodology

### Target Applications

The following intentionally vulnerable applications were used during testing:

- DVWA
- OWASP Juice Shop

These applications provided controlled environments for evaluating common web security weaknesses.

### Testing Approach

A manual security testing methodology was followed to validate vulnerabilities and document exploitation evidence.

The assessment focused on:

- SQL Injection
- Cross-Site Scripting
- Insecure Direct Object References
- Authentication weaknesses
- Security misconfiguration

### Evidence Collected

Evidence was collected through:

- Screenshots
- Payload records
- cURL requests
- API responses
- Finding-level notes
- Remediation examples

---

## Static Application Security Testing Methodology

Static analysis findings were reviewed before and after remediation activities.

The objective was to:

- Identify insecure coding practices.
- Verify remediation effectiveness.
- Compare security findings before and after fixes.

Assessment artifacts included:

- `before-report.md`
- `after-report.md`
- `sast-diff.md`
- secure patch examples under `webapp/fixes/`

---

## Network Traffic Analysis Methodology

### Evidence Source

A public packet capture associated with an XLoader malware infection scenario was analyzed using Wireshark.

### Analysis Activities

The following investigation activities were performed:

- Protocol hierarchy review
- Endpoint analysis
- DNS traffic analysis
- HTTP request review
- External communication review
- IOC extraction
- Attack hypothesis validation

### DNS Analysis

DNS activity was reviewed to identify suspicious domain resolutions.

The analysis focused on:

- Unusual domain names
- Randomized naming patterns
- Suspicious top-level domains
- Repeated domain lookups

### Host Communication Analysis

Internal and external communications were reviewed to identify potentially malicious traffic.

The analysis focused on:

- Source and destination IP addresses
- HTTP methods
- HTTP POST activity
- External infrastructure communication
- Potential command-and-control behavior

---

## Indicator of Compromise Extraction

Potential indicators were extracted from network traffic.

Indicators included:

- Suspicious domains
- External IP addresses
- URI patterns
- HTTP methods
- Internal host information

A machine-readable IOC file was maintained as:

- `network/iocs/iocs.csv`

---

## Threat Modeling Methodology

Threat modeling was conducted using evidence collected during both web application and network investigations.

The process included:

1. Identifying key assets.
2. Identifying likely threat actors.
3. Mapping attack paths.
4. Assessing likelihood and impact.
5. Recommending mitigations.

Threat relationships were also documented using Mermaid-based visual diagrams.

---

## Defense-in-Depth Methodology

A layered security approach was developed to reduce organizational risk.

Security controls were mapped across multiple defensive layers:

- Email Security
- User Awareness
- Endpoint Protection
- DNS Security
- Network Monitoring
- Threat Intelligence
- Incident Response

The goal was to ensure that failure of a single security control would not result in complete compromise.

---

## Documentation and Evidence Collection

Throughout the assessment, findings were documented with supporting evidence to ensure traceability and reproducibility.

Artifacts included:

- Screenshots
- Payload examples
- PCAP evidence
- IOC inventories
- Architecture notes
- Threat model diagrams
- Executive reports

---

## Conclusion

The methodology followed during Project KAVACH combined offensive testing, defensive analysis, network investigation, and strategic security planning.

This approach provided a practical assessment of both application-layer and network-layer security risks while producing actionable recommendations for improving the overall security posture.
