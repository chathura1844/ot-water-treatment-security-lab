# Suricata IDS Monitoring — OT Water Treatment Lab

## Project Objective

Evaluate network visibility and intrusion detection capabilities within a simulated industrial water treatment environment using Suricata IDS.

The lab focuses on industrial network traffic monitoring, Modbus TCP visibility, and security event investigation.

## Lab Environment

| Component | Details |
|---|---|
| Simulation platform | OTForge |
| IDS | Suricata 8.0.7 |
| Deployment | Docker containers |
| SCADA Server | 10.200.20.10 |
| Main PLC | 10.200.10.10 |
| Industrial protocol | Modbus TCP, port 502 |
| Network architecture | Segmented OT Process, Control Center, and Plant DMZ |

## IDS Configuration

Suricata was observed running in AF_PACKET capture mode across Docker bridge interfaces.

The IDS was configured with industrial security detection rules, including SCADA and Modbus-related rulesets.

The deployment was operating in passive IDS mode rather than inline prevention mode.

## Network Monitoring Evidence

During troubleshooting, Suricata generated an HTTP event with the following details:

| Field | Observed value |
|---|---|
| Timestamp (UTC) | 2026-10-09 04:07:55 |
| Source IP | 10.200.20.244 |
| Destination IP | 10.200.20.241 |
| Destination port | 3100 |
| Protocol | TCP/HTTP |
| HTTP endpoint | /loki/api/v1/push |
| User agent | promtail/3.6.8 |

This event demonstrated visibility into Promtail-to-Loki logging traffic on a monitored network interface.

It does not establish that Modbus traffic was successfully monitored.

## Modbus TCP Investigation

The following checks were performed:

1. Confirmed that the SCADA Docker container was running.
2. Confirmed that the main PLC Docker container was running.
3. Identified the PLC's OT Process IP address as 10.200.10.10.
4. Verified that a TCP service accepted local connections on PLC port 502.
5. Attempted SCADA-to-PLC TCP connectivity testing.
6. Observed that the SCADA-to-PLC connection test returned a nonzero exit code.
7. Searched Suricata logs for Modbus events, without confirming an actual Modbus transaction.

## Investigation Status

**Verified:**
- Suricata was running.
- Suricata recorded network traffic.
- SCADA and main PLC containers were running.
- A service was reachable locally on PLC TCP port 502.

**Pending:**
- Identify why SCADA-to-PLC TCP connectivity failed.
- Verify Modbus TCP traffic generation.
- Confirm Suricata Modbus event logging.
- Test industrial intrusion detection rules.
- Capture and document real IDS alerts.

## Security Relevance

This exercise supports practical learning in:

- OT network monitoring
- Industrial protocol analysis
- IDS deployment and troubleshooting
- Network segmentation validation
- Security event investigation
- Evidence-based security documentation

## Limitations

The current evidence demonstrates network visibility but does not yet prove successful Modbus inspection, detection of malicious industrial traffic, or firewall enforcement.

Further validation is planned within the authorized lab environment.
