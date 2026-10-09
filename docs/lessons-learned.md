# Lessons Learned — OT Water Treatment Cybersecurity Lab

## 1. Project Overview

This project explores industrial cybersecurity through a simulated water treatment environment using OTForge, Docker, Suricata IDS, SCADA, and PLC components.

The focus is on network segmentation, industrial protocol visibility, security troubleshooting, and evidence-based validation.

## 2. OT Network Architecture

A 22-device industrial topology was saved in OTForge, including the OT Process network, Control Center, and Plant DMZ.

**Lessons learned:**
- Industrial networks require carefully defined communication paths.
- PLCs and SCADA systems have different operational roles.
- Security zones help organize assets and restrict unnecessary access.
- A network diagram alone does not demonstrate that segmentation is enforced.

## 3. Firewall Security

A default-deny policy and an explicit Control Center-to-OT Process TCP 502 allow rule were configured in the lab.

**Lessons learned:**
- Default-deny is an important least-privilege design principle.
- Industrial communication requires explicit firewall exceptions.
- Broad access rules increase the potential for lateral movement.
- Firewall configuration must be validated through connectivity tests.

**Outstanding work:** Verify the effective firewall behavior and permitted communication paths.

## 4. Suricata IDS Monitoring

Suricata 8.0.7 was observed running in passive IDS mode.

The IDS generated an HTTP event showing Promtail forwarding logs to Loki over TCP port 3100.

**Lessons learned:**
- IDS health and traffic visibility should be verified separately.
- Capturing general network traffic does not prove visibility into industrial protocols.
- Suricata statistics events are not the same as Modbus transaction events.
- Security findings should be supported by actual logs and test results.

**Outstanding work:** Confirm Modbus traffic inspection and generate controlled IDS alerts.

## 5. SCADA and PLC Connectivity Troubleshooting

The SCADA and main PLC Docker containers were confirmed running.

The main PLC had two observed IP addresses:
- 10.200.10.10
- 10.200.70.10

A local TCP connection test to the PLC on port 502 succeeded, but a SCADA-to-PLC TCP 502 test failed.

**Lessons learned:**
- A running container does not guarantee application connectivity.
- Local service availability does not establish cross-network accessibility.
- Docker network interfaces, firewall rules, routing, and service binding require separate investigation.
- Troubleshooting should proceed from verified observations rather than assumptions.

**Outstanding work:** Determine why SCADA-to-PLC connectivity failed.

## 6. Risk Assessment

A preliminary risk register was developed covering unauthorized Modbus commands, inadequate segmentation, SCADA compromise, insufficient monitoring, PLC logic modification, denial-of-service, and Plant DMZ exposure.

**Lessons learned:**
- OT risk assessment must consider process availability and safety consequences.
- Threat scenarios must be distinguished from confirmed vulnerabilities.
- Risk ratings are preliminary until supported by further assessment.
- Mitigations should be linked to specific risks and validation activities.

## 7. Next Steps

1. Verify SCADA-to-PLC connectivity.
2. Validate firewall rule enforcement.
3. Generate authorized Modbus TCP requests.
4. Confirm Suricata Modbus event visibility.
5. Test industrial detection rules safely.
6. Capture supporting logs and screenshots.
7. Update the security validation report and risk register.

## 8. Conclusion

This lab provided practical experience in OT network architecture, industrial security controls, IDS monitoring, and structured troubleshooting.

The project demonstrates a documented security engineering process while clearly identifying controls and tests that remain unverified.
