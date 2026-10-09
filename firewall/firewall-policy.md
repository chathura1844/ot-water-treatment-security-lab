# OT Water Treatment — Firewall Security Policy

## Objective

Implement least-privilege network access between the Control Center, OT Process, and Plant DMZ security zones.

## Configured Firewall Policy

| Rule | Source | Destination | Protocol | Action |
|---|---|---|---|---|
| 1 | Control Center | OT Process | TCP 502 (Modbus) | ALLOW |
| 2 | Other unmatched traffic | Other destinations | Any | DENY (default) |

## Security Decisions

### 1. Default-Deny Policy

A default-deny policy restricts traffic unless an explicit rule permits it.

### 2. Modbus TCP Access

The Control Center is permitted to initiate Modbus TCP communications toward the OT Process zone on TCP port 502.

This exception supports the intended SCADA-to-PLC communication path.

### 3. Removal of Broad Access

A previously configured broad OT Process-to-Control Center allow rule was removed to reduce unnecessary network exposure.

### 4. OPC UA Rule Review

An unverified TCP 4840 exception was removed because the lab's documented communication requirement uses Modbus TCP.

## Security Risks Addressed

- Unnecessary access between industrial security zones
- Exposure of industrial control services
- Potential lateral movement between network segments
- Excessive firewall permissions

## Validation Status

**Configuration documented; enforcement testing pending.**

Planned tests:

1. Verify permitted SCADA-to-PLC Modbus TCP communication.
2. Attempt an unauthorized cross-zone connection in the isolated lab.
3. Inspect firewall logs for allowed and denied traffic.
4. Confirm that required operational communications remain functional.

## Framework References

- IEC 62443 — Zones, conduits, and industrial security controls
- NIST SP 800-82 — OT network security guidance
- NIST CSF — Protect and Detect functions

## Conclusion

The configured firewall policy applies least-privilege principles to the simulated water treatment environment. Its effectiveness will be assessed through subsequent connectivity and security testing.
