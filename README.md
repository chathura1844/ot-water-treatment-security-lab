# OT Water Treatment Security Lab

### Industrial Control Systems (ICS) | SCADA | PLC | Network Segmentation | Modbus TCP

## Project Overview

This project documents a hands-on Operational Technology (OT) cybersecurity lab built using the OTForge Water Treatment environment.

The project focuses on designing and assessing a simulated industrial water treatment network, applying defensive security principles, and examining cybersecurity risks affecting PLCs, SCADA systems, and industrial communications.

**Primary objectives:**
- Understand industrial control system architecture.
- Design and document segmented OT networks.
- Analyze Modbus TCP communications.
- Configure and review industrial firewall policies.
- Explore threat modeling and vulnerability assessment.
- Develop practical OT cybersecurity documentation.

## Lab Environment

**Platform:** OTForge Water Treatment Simulation

**Network architecture:** 22-device topology organized across the OT Process, Control Center, and Plant DMZ zones.

**Key components:**
- OpenPLC — simulated industrial controller
- SCADA server — supervisory monitoring and control
- Industrial firewall — traffic filtering and network segmentation
- Industrial network infrastructure
- Security monitoring and IDS components

## Network Architecture

| Zone | Purpose |
|---|---|
| OT Process | Industrial controllers and process equipment |
| Control Center | SCADA supervision and operational management |
| Plant DMZ | Controlled boundary for supporting services |

## Industrial Communication

**Protocol:** Modbus TCP

**Port:** TCP 502

**Example lab assets:**
- OpenPLC: `10.200.10.10`
- SCADA Server: `10.200.20.10`

The architecture includes a firewall rule permitting Modbus TCP traffic from the Control Center to the OT Process network.

## Security Controls

### Network Segmentation
Separate industrial process equipment from supervisory systems and supporting services.

### Firewall Policy
- Default-deny traffic policy
- Explicit allowance for required Modbus TCP communications
- Removal of unnecessarily broad access rules
- Review of protocol-specific exceptions

### Security Assessment
The project will document threat scenarios, potential attack paths, and defensive recommendations.

## Project Status

**In progress**

Completed:
- Created and saved the 22-device OT topology
- Organized OT Process, Control Center, and Plant DMZ zones
- Configured initial firewall segmentation rules

Planned:
- Validate communications and firewall behavior
- Review IDS deployment and monitoring
- Conduct authorized vulnerability assessments
- Develop a threat model and risk register
- Document findings and mitigation recommendations

## Relevant Skills

OT Security • ICS Security • SCADA • PLC • Modbus TCP • Network Security • Firewall Configuration • Network Segmentation • Threat Modeling • Security Documentation

## Disclaimer

This project is conducted in a simulated, authorized lab environment for educational and defensive security research. It does not represent a production industrial deployment.

## Author

**Chathura Chamantha**

[GitHub](https://github.com/chathura1844) | [LinkedIn](https://www.linkedin.com/in/chathura-comptia-security-59577218b) | [Cybersecurity Portfolio](https://chathura-cybersecurity.cchamara2.chatgpt.site)
