# OT Water Treatment — Cybersecurity Risk Assessment

## 1. Objective

Identify and evaluate cybersecurity risks affecting a simulated industrial water treatment control system, including SCADA servers, PLCs, industrial network communications, and supporting infrastructure.

This assessment applies defense-in-depth, least-privilege, and IEC 62443 zone-and-conduit security concepts.

## 2. Scope

The simulated OTForge environment includes:

- OT Process network
- Control Center network
- Plant DMZ
- SCADA server
- Main PLC and safety controllers
- Industrial network communication using Modbus TCP
- Firewall segmentation
- Suricata network intrusion detection

## 3. Risk Assessment Methodology

Risks are assessed using qualitative likelihood and impact ratings.

| Rating | Likelihood | Impact |
|---|---|---|
| Low | Unlikely under current assumptions | Limited operational disruption |
| Medium | Plausible under realistic conditions | Significant but recoverable disruption |
| High | Credible under adverse conditions | Potential major process, safety, or availability consequences |

The ratings below are preliminary scenario-based assessments, not measured probabilities or verified vulnerabilities.

## 4. OT Cybersecurity Risk Register

| ID | Threat Scenario | Likelihood | Impact | Priority |
|---|---|---|---|---|
| OT-R01 | Unauthorized Modbus commands issued to PLC | Medium | High | High |
| OT-R02 | Excessive access between OT security zones | Medium | High | High |
| OT-R03 | Compromised SCADA workstation or server | Medium | High | High |
| OT-R04 | Industrial network traffic not adequately monitored | Medium | Medium | Medium |
| OT-R05 | Unauthorized modification of PLC logic | Medium | High | High |
| OT-R06 | Denial-of-service affecting industrial communications | Medium | High | High |
| OT-R07 | Compromise of services in the Plant DMZ | Medium | Medium | Medium |

## 5. Risk Analysis and Mitigations

### OT-R01 — Unauthorized Modbus Commands

**Threat:** An unauthorized system sends Modbus requests to a PLC, potentially modifying process values or control outputs.

**Potential impact:** Process disruption, equipment damage, or unsafe operating conditions depending on the controlled process.

**Recommended controls:**
- Restrict Modbus TCP access to authorized clients.
- Apply network segmentation and least-privilege firewall rules.
- Monitor Modbus operations using industrial-aware IDS signatures.
- Investigate unexpected write operations.

**Validation status:** Pending.

### OT-R02 — Inadequate Network Segmentation

**Threat:** Overly permissive network access allows lateral movement between industrial security zones.

**Potential impact:** Increased exposure of PLCs, SCADA servers, and other critical assets.

**Recommended controls:**
- Default-deny firewall policy.
- Explicit allow rules for required industrial communications.
- Separate OT Process, Control Center, and Plant DMZ networks.
- Test permitted and denied network paths.

**Lab status:** Segmentation policy configured; enforcement not yet verified.

### OT-R03 — Compromised SCADA System

**Threat:** An attacker compromises the SCADA server through stolen credentials, vulnerable software, or an exposed management interface.

**Potential impact:** Loss of supervisory visibility, unauthorized control requests, or disruption of industrial operations.

**Recommended controls:**
- Role-based access control.
- Secure remote administration.
- Patch and vulnerability management with OT operational safeguards.
- Network monitoring and incident response procedures.

**Validation status:** Pending.

### OT-R04 — Limited OT Network Visibility

**Threat:** Suspicious industrial communication goes undetected because of incomplete monitoring coverage or missing detection rules.

**Potential impact:** Delayed incident identification and response.

**Recommended controls:**
- Deploy Suricata IDS on relevant network segments.
- Enable and validate industrial protocol logging.
- Monitor unexpected PLC communication.
- Review IDS alerts and investigate anomalies.

**Lab status:** General network visibility confirmed; Modbus detection not yet verified.

### OT-R05 — Unauthorized PLC Logic Changes

**Threat:** Unauthorized modification of control logic affects industrial process behavior.

**Potential impact:** Operational disruption, process integrity loss, and potential safety consequences.

**Recommended controls:**
- Restrict engineering access.
- Protect controller programming interfaces.
- Maintain version-controlled PLC logic backups.
- Review and approve logic changes.

**Validation status:** Pending.

### OT-R06 — Industrial Network Denial-of-Service

**Threat:** Excessive traffic or malicious requests degrade communication between SCADA and PLC devices.

**Potential impact:** Loss of monitoring, delayed control responses, or process interruption.

**Recommended controls:**
- Network segmentation.
- Traffic baselining.
- Industrial network monitoring.
- Resilience and recovery procedures.

**Validation status:** Pending. No disruptive testing is planned against production equipment.

### OT-R07 — Plant DMZ Compromise

**Threat:** An exposed or vulnerable DMZ service provides an attacker with an opportunity to move toward OT systems.

**Potential impact:** Unauthorized access to industrial assets or supporting infrastructure.

**Recommended controls:**
- Limit DMZ-to-OT communication.
- Harden exposed services.
- Apply access control and monitoring.
- Review permitted data flows.

**Validation status:** Pending.

## 6. Observed Findings Versus Hypothetical Risks

The scenarios in this assessment represent potential OT security risks. They are not confirmed security incidents or exploited vulnerabilities.

Observed lab findings include:

- SCADA and PLC containers were operational.
- A TCP service was accessible locally on PLC port 502.
- SCADA-to-PLC TCP connectivity testing failed.
- Suricata recorded HTTP logging traffic.
- Modbus event visibility and firewall enforcement remain unverified.

The SCADA-to-PLC connectivity failure is an unresolved operational finding and is not, by itself, evidence of a cybersecurity attack.

## 7. Planned Security Validation

- Verify authorized SCADA-to-PLC communication.
- Confirm firewall enforcement between security zones.
- Generate controlled Modbus requests in the lab.
- Validate industrial IDS signatures and alerts.
- Test selected unauthorized access scenarios safely.
- Record evidence and update the risk register.

## 8. Framework Alignment

This assessment draws on concepts associated with:

- IEC 62443 — Industrial automation and control system security
- NIST SP 800-82 — Operational technology security
- Defense in depth
- Least privilege
- Network segmentation and security monitoring

Framework alignment is conceptual and does not constitute certification or a formal compliance assessment.

## 9. Conclusion

The simulated water treatment environment provides a practical foundation for studying industrial cybersecurity threats, network segmentation, and intrusion detection.

The risk register identifies priority scenarios for future validation, while distinguishing proposed security controls from those demonstrated through testing.
