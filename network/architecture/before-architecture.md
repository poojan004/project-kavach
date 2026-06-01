# Current Network Architecture (Before Improvements)

## Existing Environment

The analyzed environment appears to follow a traditional network design where internal hosts communicate directly with external internet resources through a perimeter firewall.

### Architecture

Internet
↓
Perimeter Firewall
↓
Internal Network
↓
User Workstations
↓
Application Services
↓
Database Services

## Observed Weaknesses

- Limited DNS monitoring capability
- No dedicated DNS filtering controls
- No visible IDS/IPS deployment
- Limited network segmentation
- Insufficient outbound traffic inspection
- Lack of centralized security monitoring
- Malware communications can reach external hosts with limited visibility

## Risk Assessment

This architecture provides basic connectivity and perimeter protection but offers limited visibility into malware activity, command-and-control communications, and suspicious outbound connections.
