# Hardware Testbed for Cybersecurity Education

A sandbox definition designed for cybersecurity training and education as part of the **Hardware Testbed for Cybersecurity Education** thesis. This topology simulates a realistic industrial control system (ICS) environment with segmented networks, representative of modern critical infrastructure scenarios commonly used in cybersecurity education platforms like CyberRangeCZ.


## 🏗️ Architecture

The topology consists of two isolated network segments connected through routers:

```
┌─────────────────────────────────────────────────────────────┐
│                      WAN/Management Network                 │
└────────────┬──────────────────────────────────┬─────────────┘
             │                                  │
        ┌────▼─────┐                      ┌────▼─────┐
        │USR Router│                      │OT Router │
        │10.0.10.1 │                      │10.0.20.1 │
        └────┬─────┘                      └────┬─────┘
             │                                 │
    ┌────────▼────────┐              ┌─────────▼──────────┐
    │ USR Network     │              │ OT Network         │
    │ 10.0.10.0/24    │              │ 10.0.20.0/24       │
    └────────┬────────┘              └─────────┬──────────┘
             │                                 │
    ┌────────▼──────────┐            ┌─────────▼──────────┐
    │ usr-workstation   │            │ ot-hmi             │
    │ 10.0.10.10        │            │ 10.0.20.21         │
    │ (Debian 12)       │            │ (Ubuntu Noble)     │
    └───────────────────┘            └────────────────────┘
```

## 🌐 Network Topology

### Networks

| Network Name | CIDR          | Purpose                    | User Accessible |
|--------------|---------------|----------------------------|-----------------|
| **usr**      | 10.0.10.0/24  | User/Corporate Network     | Yes             |
| **ot**       | 10.0.20.0/24  | Operational Technology     | Yes             |

### Hosts

| Hostname          | IP Address  | Operating System    | Flavor   | Purpose                        |
|-------------------|-------------|---------------------|----------|--------------------------------|
| **usr-workstation** | 10.0.10.10  | Debian 12 (x86_64) | a4-4-35  | User workstation (attacker)    |
| **ot-hmi**        | 10.0.20.21  | Ubuntu Noble        | a2-2-35  | HMI (Human-Machine Interface)  |
| **usr-router**    | 10.0.10.1   | Debian 12 (x86_64) | a1-2-20  | User network router            |
| **ot-router**     | 10.0.20.1   | Debian 12 (x86_64) | a1-2-20  | OT network router              |

## 🔧 Components

### 1. **OT-HMI (Human-Machine Interface)**
- **Role**: Simulates an industrial HMI system in an operational technology environment
- **OS**: Ubuntu Noble (latest LTS)
- **Network**: OT Network (10.0.20.0/24)
- **Configuration**: Provisioned via `hmi-role` from [thesis-role-hmi](https://github.com/prer00DEV/thesis-role-hmi.git)

### 2. **USR-Workstation**
- **Role**: Represents a user workstation, potentially used as an attack vector or penetration testing platform
- **OS**: Debian 12
- **Network**: User Network (10.0.10.0/24)
- **Configuration**: Provisioned via `workstation-role` from [thesis-role-workstation](https://github.com/prer00DEV/thesis-role-workstation.git)
- **Special Features**: Configured with reverse shell capabilities for red team exercises


**Project**: Hardware Testbed for Cybersecurity Education  
**Platform**: CyberRangeCZ  
**Repository**: [windplant-thesis-topology](https://github.com/prer00DEV/windplant-thesis-topology)  
**Author**: Thesis Project - Cybersecurity Education

For more information about the individual components, refer to:
- [HMI Role Repository](https://github.com/prer00DEV/thesis-role-hmi.git)
- [Workstation Role Repository](https://github.com/prer00DEV/thesis-role-workstation.git)

This README was generated with the help of Claude Sonnet 4.5.
