# Stage 0 – Baseline Network Build

## Objective
The objective of Stage 0 is to design and deploy a fully functional baseline enterprise network for **ByBank**, a mid-sized regional financial institution. This stage establishes a realistic but intentionally insecure environment that will serve as the foundation for subsequent attack simulations and security hardening activities.

No security controls, monitoring, segmentation, or hardening mechanisms are applied at this stage. All systems are configured to prioritize functionality over security, accurately reflecting a common real-world starting point for many organizations.

---

## Environment Overview

The baseline environment was built using **GNS3** for network infrastructure simulation and **VMware Workstation** for hosting servers and endpoints. The network includes core infrastructure components, application servers, Active Directory services, and multiple department-based client workstations.

---

## Infrastructure Components

### Network Devices
- Router
- Switch
- DHCP-enabled network

### Servers
| Server | Purpose |
|------|--------|
| WEB Server | Hosts the public-facing ByBank website |
| Database Server | Stores backend application data |
| Windows Server | Active Directory Domain Services |

### Client Workstations
| Computer Name | Department | OS | Assigned User |
|--------------|------------|----|---------------|
| BYBKFIN01 | Finance | Windows 11 | Alice Smith (`asmith`) |
| BYBKIT01 | IT | Windows 11 | Ben Wayne (`bwayne`) |
| BYBKSAL01 | Sales | Windows 11 | Charlie Parker (`cparker`) |

---

## Active Directory Configuration

The environment includes a centralized Active Directory domain used for authentication and authorization across all Windows systems.

### Domain Users
| Department | Name | Username | Role |
|-----------|------|----------|------|
| IT | Ben Wayne | `bwayne` | Domain Administrator |
| Finance | Alice Smith | `asmith` | Standard User |
| Sales | Charlie Parker | `cparker` | Standard User |
| HR | Diana Prince | `dprince` | Standard User |
| Service | SQL Service | `svc_sql` | Service Account |

Passwords are intentionally weak and reused across accounts to simulate poor credential hygiene commonly observed in real-world enterprise environments.

---

## Virtual Machine Access (Lab Use Only)

| System | Username | Password |
|------|--------|----------|
| WEB Server | srv-web | Website@123 |
| Database Server | srv-db | Database@123 |
| Windows Server | Administrator | Customerdataissecure |
| BYBANKFIN01 | jpatel (Local Admin) | patel123 |
| BYBANKIT01 | jpatel (Local Admin) | patel123 |
| BYBANKSAL01 | jpatel (Local Admin) | patel123 |

> **Note:** All credentials are documented strictly for lab simulation purposes.

---

## Network Services
- DHCP enabled for client systems
- Domain-joined Windows workstations
- Publicly accessible web application
- Backend database connected to web server

---

## Known Insecure Configurations (Intentional)

The following weaknesses are deliberately present in the baseline environment:
- Weak and predictable user passwords
- Domain Administrator assigned to a standard IT user account
- Shared local administrator credentials across endpoints
- Service account with simple password
- Flat network with no segmentation between departments
- No firewall restrictions between internal systems
- No logging, monitoring, or SIEM deployment
- No endpoint protection or hardening policies

---

## Artifacts and Evidence

Screenshots and configuration artifacts captured during this stage include:
- Network topology design
- VMware environment overview
- Web server configuration
- Database server configuration
- Active Directory users and computers
- DHCP configuration
- Router IP configuration

These artifacts are stored in the `screenshots/` and `router-configs/` directories for reference.

---

## Stage 0 Outcome

At the completion of Stage 0, ByBank has a fully operational enterprise network with centralized identity management and business-critical services. However, the environment lacks fundamental security controls, creating multiple attack surfaces that will be explored in the next stages of this project.

The resulting baseline network provides a realistic platform for simulating adversary behavior, identifying weaknesses, and demonstrating measurable security improvements.
