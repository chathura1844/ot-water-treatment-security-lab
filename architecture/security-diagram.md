# OT Water Treatment — Logical Security Architecture

```mermaid
flowchart TB
    subgraph DMZ["Plant DMZ"]
        S["Supporting Services"]
    end
    subgraph CC["Control Center"]
        SCADA["SCADA Server - 10.200.20.10"]
    end
    FW{"Firewall - Default Deny"}
    subgraph OT["OT Process"]
        PLC["OpenPLC - 10.200.10.10"]
        DEV["Process Devices"]
    end
    SCADA -->|"Modbus TCP 502 allowed"| FW
    FW --> PLC
    PLC --- DEV
    S -.-|"Access subject to policy"| FW
```

**Scope:** Conceptual security-zone diagram, not a complete representation of all 22 devices.

**Validation status:** Firewall rule configured; end-to-end communications and IDS behavior have not yet been verified.
