# Stage 3: ByBank Network Redesign Proposal

## Executive Summary

The primary goal of Stage 3 is to design a **new network architecture** based on the recommendations from Stage 2. This new design addresses all issues identified during Stage 2 testing.

The architecture implements **Defense in Depth** and **Least Privilege** principles to protect critical financial assets and ensure compliance with industry security standards.

Key benefits of the new design:

- **Eliminate Lateral Movement:** Segmentation prevents a breach in one area from spreading to others.  
- **Reduce Attack Surface:** Strict firewall rules limit exposure of internal services.  
- **Centralized Visibility:** Full logging and monitoring via **Splunk** and **Wazuh**.  

---

## New Network Architecture

The network is divided into **three primary security zones**, managed by a **Next-Generation Firewall (NGFW)** for granular traffic inspection:

- **External Zone:** The untrusted buffer between the Internet and private infrastructure.  
- **DMZ (Demilitarized Zone):** Hosts public-facing services (Web Servers). Isolated from the internal network.  
- **Internal Zone:** Contains sensitive corporate data, divided into functional VLANs to enforce **Role-Based Access Control (RBAC)**.  

---

## Logical Segmentation (VLAN Schema)

| Zone       | VLAN       | Subnet          |
|------------|------------|----------------|
| External   | -          | 192.168.10.0/24|
| DMZ        | -          | 192.168.15.0/24|
| Internal   | -          | 192.168.20.0/24|
| Server     | VLAN 1001  | 192.168.35.0/24|
| Security   | VLAN 1010  | 192.168.30.0/24|
| IT         | VLAN 1015  | 192.168.50.0/24|
| Finance    | VLAN 1020  | 192.168.55.0/24|
| Sales      | VLAN 1030  | 192.168.60.0/24|

---

## Technical Stack

- **Perimeter Defense:** **pfSense Firewall (NGFW)** with stateful packet inspection and IDS/IPS (Snort)  
- **Routing & Switching:** Cisco IOS Routers/Switches for Inter-VLAN routing and hardware-level port security  
- **Endpoints:** Windows 11 Workstations, Ubuntu and Windows Server environments  
- **SIEM/XDR:** **Splunk** for centralized log analysis and **Wazuh** for endpoint detection and response (EDR)  

---

## Firewall Rules (Initial)

| Source       | Destination       | Protocol / Port | Business Justification |
|--------------|-----------------|----------------|----------------------|
| Internet     | DMZ             | HTTPS (443)    | Allow customers to access the banking portal |
| IT VLAN      | DMZ / Internal  | SSH (22) / RDP | Authorized administrative maintenance |
| All Zones    | Security VLAN   | Syslog (514) / Wazuh | Centralized security monitoring |
| DMZ          | Server VLAN     | DB Port (e.g., 3306) | Web server querying the database |

> Note: These rules are the initial configuration. Additional rules will be added as the implementation progresses.

---

## Device Hardening

- All devices will have **SSH and RDP** access restricted to authorized IT users.  
- Routers and switches will have strong passwords and security banners enabled.  
- Endpoint devices will run **Wazuh agents** for activity tracking.  
- Active Directory **GPOs** will manage Windows workstation policies.  
- Network devices will forward logs to **Splunk** for monitoring and threat detection.  

---

## Approval & Sign-off

By signing below, you authorize the implementation of Phase 3, including the procurement of virtual/physical hardware and reconfiguration of ByBank’s network interfaces.

**Approved By:** John Doe – ByBank IT Director  
**Date:** 29_Dec_2025


