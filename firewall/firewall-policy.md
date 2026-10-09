# OT Water Treatment — Firewall Security Policy

## Objective

Design a segmented industrial control system (ICS) network that restricts communication between operational technology (OT) devices, the Control Center, and the Plant DMZ.

## Network Security Zones

| Zone | Purpose |
|---|---|
| OT Process | Industrial controllers and process equipment |
| Control Center | SCADA supervision and monitoring |
| Plant DMZ | Segregated services and controlled communication between security zones |

## Firewall Policy Design

The lab uses a default-deny firewall policy as its intended security baseline.

| Source | Destination | Protocol | Port | Intended action |
|---|---|---|---|---|
| Control Center | OT Process | Modbus TCP | 502 | ALLOW |
| OT Process | Control Center | Unapproved new connections | Any | DENY |
| Unapproved zones | OT Process | Unapproved traffic | Any | DENY |
| Any zone | Any zone | Traffic without an explicit permit rule | Any | DENY |

## Security Controls

- Apply least-privilege access between OT network zones.
- Restrict Modbus TCP communication to approved paths.
- Avoid broad access from industrial controllers to the Control Center.
- Use Suricata IDS for network traffic monitoring.
- Review firewall rules and network activity for unexpected communication.
- Document and validate permitted and denied traffic.

## Implementation Progress

**Configured in the OTForge lab:**
- A 22-device industrial network topology was saved.
- A default-deny firewall policy was configured.
- A Control Center-to-OT Process TCP 502 permit rule was configured.
- Broad OT Process-to-Control Center access was removed.

**Validation pending:**
- Confirm firewall enforcement.
- Verify authorized SCADA-to-PLC Modbus communication.
- Test unauthorized cross-zone communication.
- Collect firewall and IDS evidence.

## Security Principles

This project applies concepts from industrial network segmentation, least privilege, defense in depth, and IEC 62443 zone-and-conduit architecture.

The lab is a simulated training environment. Firewall enforcement and security effectiveness must be verified through testing before being reported as validated controls.
