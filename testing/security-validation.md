# OT Water Treatment — Security Validation & Test Results

## Objective

Validate the operational status, network connectivity, industrial protocol exposure, and monitoring capabilities of a simulated water treatment industrial control system.

## Test Environment

- Platform: OTForge
- Deployment: Docker
- IDS: Suricata 8.0.7
- SCADA Server: 10.200.20.10
- Main PLC: 10.200.10.10
- Industrial protocol: Modbus TCP (502)

## Test Results

| Test ID | Security Test | Result |
|---|---|---|
| OT-001 | Verify SCADA container is running | PASS |
| OT-002 | Verify main PLC container is running | PASS |
| OT-003 | Confirm PLC OT network IP | PASS |
| OT-004 | Check local PLC TCP port 502 | PASS |
| OT-005 | Test SCADA-to-PLC TCP 502 connection | FAIL |
| OT-006 | Verify Suricata is running | PASS |
| OT-007 | Verify Suricata records network traffic | PASS |
| OT-008 | Confirm Modbus traffic detection | NOT VERIFIED |
| OT-009 | Validate firewall default-deny enforcement | PENDING |
| OT-010 | Test unauthorized cross-zone access | PENDING |
| OT-011 | Generate and investigate IDS security alerts | PENDING |

## Test Evidence

### OT-004: PLC TCP Port 502

A Python socket connectivity test executed inside the main PLC container returned exit code 0 when connecting to 127.0.0.1:502.

**Result:** A local TCP service was accepting connections on port 502.

### OT-005: SCADA-to-PLC Connectivity

A TCP connection test from the SCADA container to 10.200.10.10:502 returned exit code 1.

**Result:** Connection unsuccessful.

**Potential causes requiring investigation:**
- Firewall filtering
- Network routing or segmentation
- Service interface binding

The root cause has not yet been established.

### OT-007: Suricata Network Visibility

Suricata logged HTTP communication from 10.200.20.244 to 10.200.20.241 on TCP port 3100.

The traffic was associated with Promtail forwarding logs to Loki.

**Result:** Network traffic capture confirmed on a monitored interface.

### OT-008: Modbus Monitoring

Searches of Suricata event logs did not establish that Modbus application traffic had been captured.

**Result:** Not verified.

## Findings

### Finding 1 — SCADA-to-PLC Connectivity Failure

**Status:** Open

The SCADA server was unable to establish a TCP connection to the PLC at 10.200.10.10:502 during the test.

**Next action:** Investigate routing, firewall behavior, and PLC interface binding.

### Finding 2 — Modbus IDS Visibility Not Established

**Status:** Open

Suricata captured HTTP traffic, but successful Modbus protocol monitoring has not yet been demonstrated.

**Next action:** Generate authorized Modbus traffic and inspect IDS events.

## Planned Validation

1. Confirm SCADA and PLC network interfaces.
2. Verify routing and firewall enforcement.
3. Establish permitted SCADA-to-PLC Modbus communication.
4. Generate controlled Modbus requests.
5. Inspect Suricata event logs.
6. Test unauthorized traffic against the intended firewall policy.
7. Capture evidence and update findings.

## Conclusion

Initial testing confirmed that the main industrial components and Suricata IDS were operational.

However, SCADA-to-PLC connectivity and Modbus IDS monitoring require additional troubleshooting.

This report records observed results without treating unverified controls as successful.
