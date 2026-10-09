# OT Water Treatment Cybersecurity Lab

### Industrial Control System Security | SCADA | PLC | Suricata IDS | Docker

## Project Overview

![OT Water Treatment Cybersecurity Lab Architecture](OT%20Water%20Treatment%20Cybersecurity%20Lab.png)

A hands-on industrial cybersecurity project using OTForge to design, document, and investigate security controls within a simulated water treatment industrial control system (ICS).

The project focuses on network segmentation, Modbus TCP communication, intrusion detection, cybersecurity risk assessment, and security validation.

## Technologies & Tools

- **ICS/OT:** SCADA, PLC, Modbus TCP
- **Security Monitoring:** Suricata IDS
- **Infrastructure:** Docker, OTForge
- **Network Security:** Firewall segmentation, default-deny policies, least-privilege access
- **Security Frameworks:** IEC 62443 concepts, NIST SP 800-82
- **Documentation:** Network architecture, risk assessment, test results, and security findings

## Lab Architecture

Designed and saved a 22-device industrial topology consisting of:

- OT Process network
- Control Center network
- Plant DMZ
- SCADA server and industrial controllers
- Firewall and intrusion detection components

The architecture uses security zones and defined communication paths to support defense in depth.

## Security Engineering Activities

### 1. OT Network Segmentation
- Configured a default-deny firewall policy.
- Defined an explicit Control Center-to-OT Process Modbus TCP 502 permit rule.
- Removed overly broad access rules.
- Documented intended communication flows.

### 2. Industrial Intrusion Detection
- Investigated Suricata 8.0.7 running in passive IDS mode.
- Confirmed network traffic capture through Suricata EVE JSON logs.
- Analyzed observed Promtail-to-Loki HTTP traffic.
- Identified outstanding requirements for Modbus protocol monitoring.

### 3. Security Validation
- Verified SCADA and PLC container availability.
- Confirmed local TCP port 502 connectivity on the PLC.
- Investigated unsuccessful SCADA-to-PLC connectivity.
- Recorded completed tests and outstanding validation activities.

### 4. Cybersecurity Risk Assessment
- Developed a preliminary OT security risk register.
- Evaluated unauthorized Modbus commands, network segmentation weaknesses, SCADA compromise, and monitoring gaps.
- Proposed mitigations aligned with industrial security principles.

## Project Documentation

| Document | Description |
|---|---|
| [Network Topology](architecture/network-topology.md) | OT architecture and industrial assets |
| [Security Diagram](architecture/security-diagram.md) | Network segmentation visualization |
| [Firewall Policy](firewall/firewall-policy.md) | Intended traffic control rules |
| [Suricata Monitoring](ids/suricata-monitoring.md) | IDS configuration and observed evidence |
| [Security Validation](testing/security-validation.md) | Connectivity tests and findings |
| [Risk Assessment](security/risk-assessment.md) | OT threats, impacts, and mitigations |
| [Lessons Learned](docs/lessons-learned.md) | Investigation outcomes and next steps |

## Current Project Status

**Completed:** Architecture documentation, firewall policy configuration, initial IDS monitoring, connectivity investigation, and preliminary risk assessment.

**In progress:** SCADA-to-PLC connectivity troubleshooting, firewall enforcement validation, Modbus protocol monitoring, and industrial IDS alert testing.

## Security Focus

This project demonstrates practical learning in industrial network architecture, OT security monitoring, risk-based analysis, and evidence-driven troubleshooting.

It is a simulated training project and does not represent a production deployment or formal IEC 62443 compliance assessment.
