# OT Water Treatment — Network Architecture

## 1. Architecture Overview

This project uses a simulated industrial water treatment environment in OTForge, organized into three network security zones.

The lab topology contains 22 devices, including industrial control, supervisory, and supporting network components.

## 2. Security Zones

### OT Process Zone
Hosts industrial controllers and process equipment responsible for simulated water treatment operations.

Example asset:
- OpenPLC — `10.200.10.10`

### Control Center Zone
Provides supervisory monitoring and communication with industrial controllers.

Example asset:
- SCADA Server — `10.200.20.10`

### Plant DMZ
Provides a separate security zone intended to isolate supporting services and mediate communications between network environments.

## 3. Industrial Communications

| Source | Destination | Protocol | Port |
|---|---|---|---|
| Control Center | OT Process | Modbus TCP | 502 |

Modbus TCP enables communication between supervisory systems and industrial controllers.

Because traditional Modbus TCP does not provide native authentication or encryption, network segmentation and restricted access are important security controls.

## 4. Firewall Security Design

The current lab configuration includes:

- Default-deny firewall policy.
- Explicit Control Center-to-OT Process permission for TCP port 502.
- Removal of a broad OT Process-to-Control Center allow rule.
- Removal of an unverified OPC UA TCP 4840 exception.

These settings represent the configured policy. Successful enforcement and end-to-end communication testing remain to be documented.

## 5. Security Considerations

### Unauthorized PLC Access
Restrict communication with industrial controllers to approved systems and services.

### Lateral Movement
Use network segmentation and least-privilege firewall rules to limit movement between security zones.

### Industrial Protocol Exposure
Monitor Modbus TCP traffic for unexpected sources, unauthorized function codes, and unusual communication patterns.

### Security Monitoring
Assess IDS visibility and logging to support detection of suspicious industrial network activity.

## 6. Planned Validation

- Verify authorized SCADA-to-PLC communications.
- Test firewall enforcement for unauthorized traffic.
- Capture and analyze Modbus TCP packets.
- Validate IDS operation and event logging.
- Record findings and supporting evidence.

## 7. Relevant Security Frameworks

Future assessments will reference:

- IEC 62443 — Industrial automation and control system security.
- NIST SP 800-82 — Operational Technology security guidance.
- NIST Cybersecurity Framework — Cybersecurity risk management.

These standards are reference frameworks for the project; formal compliance assessment has not been performed.

## Project Status

Architecture documented from the saved OTForge lab configuration. Communication testing, IDS validation, and security assessment remain in progress.
