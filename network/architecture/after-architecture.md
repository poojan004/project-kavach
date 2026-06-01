# Recommended Network Architecture (After Improvements)

## Proposed Secure Architecture

The following architecture is recommended to reduce the likelihood of malware infections and improve visibility into suspicious network activity.

### Architecture

Internet
↓
Web Application Firewall (WAF)
↓
Next Generation Firewall
↓
DMZ
↓
Application Services
↓
Database Services

Additional Security Controls

- DNS Filtering Service
- IDS/IPS Monitoring
- Endpoint Detection and Response (EDR)
- Security Information and Event Management (SIEM)
- Centralized Log Collection
- Multi-Factor Authentication (MFA)
- Network Segmentation

## Security Improvements

### DNS Protection

Blocks known malicious domains before connections are established.

### Network Segmentation

Limits lateral movement following a compromise.

### IDS/IPS

Detects and prevents suspicious traffic patterns.

### SIEM Monitoring

Provides centralized visibility and alerting.

### EDR Protection

Detects malware activity directly on endpoints.

### MFA

Reduces risk of unauthorized account access.

## Expected Outcome

The proposed architecture significantly improves the organization's ability to detect, prevent, and respond to malware infections while reducing attack surface and increasing monitoring visibility.
