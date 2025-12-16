# 🏦 ByBank Security Architecture and Hardening Project

## Project Overview

This project simulates a comprehensive security audit, redesign, and hardening effort for a fictional mid-sized regional bank, **ByBank**. The primary objective was to transform a high-risk, flat network architecture into a robust, segmented, and secure environment compliant with industry best practices, effectively mitigating both external and internal threats.

---

## 💡 The Challenge: ByBank's Critical Flaw (The "Before")

ByBank's network was characterized by rapid growth without corresponding security investment, leading to a critical architecture flaw:

* **Flat Network Architecture:** All critical assets (Web Server, Database, Active Directory) and client machines were hosted on a single, non-segmented subnet.
* **High Risk:** This design meant that a single point of compromise—whether via a successful **SQL Injection** on the public-facing Netbanking server or a successful **Phishing** attack on an employee PC—granted an attacker immediate, unrestricted **lateral movement** to the entire network, including the high-value Customer Database and Active Directory Domain Controller.

### **Initial Network Components (Pre-Stage)**

The starting environment was built in Packet Tracer (and deployed in VMware/GNS3) and included:

* **Public-Facing Server:** `Server-PT WEB` (hosting the Netbanking application).
* **High-Value Assets:** `Server-PT Database` (Customer Data) and `Server-PT DNS + DHCP + AD` (Critical Infrastructure).
* **Internal Clients:** `PC-PT HR`, `PC-PT CEO`, `PC-PT Financial Analyst` (Representing phishing targets).

---

## 🗺️ Project Stages and Demonstrated Skills

The project was executed in a four-stage process, demonstrating expertise across the entire security lifecycle from audit to implementation.

### **Stage 1: Risk Assessment & Penetration Testing (The Audit)**

* **Objective:** Validate the network's vulnerabilities by executing a targeted penetration test.
* **Demonstrated Skills:** Vulnerability Assessment, Reconnaissance (`nmap`), Web Application Exploitation (SQL Injection), Credential Harvesting (`Responder`), Active Directory Attacking, Lateral Movement.
* **Key Finding:** Confirmed that the flat network allowed for a full Active Directory takeover from a low-privilege client machine, resulting in a **High Severity** risk rating.

### **Stage 2: Reporting & Secure Architecture Proposal**

* **Objective:** Document the technical findings and propose a professional, secure network architecture.
* **Demonstrated Skills:** Professional Reporting, Risk Analysis, Business Communication (translating technical findings to business impact), Security Architecture Design, Compliance Gap Analysis (e.g., lack of segmentation).
* **Proposal:** Design for a segmented network utilizing **VLANs** for separation of duties, including a dedicated **DMZ** and **Core Management** zone.

### **Stage 3: Secure Network Implementation (The "After")**

* **Objective:** Implement the proposed secure network design using virtualization and network emulation tools.
* **Demonstrated Skills:** Virtualization (VMware/VirtualBox), Network Emulation (GNS3/Packet Tracer), Firewall Configuration (e.g., pfSense/OpnSense), Layer 3 Routing, VLAN configuration, IP Schema design.
* **Key Design:** Implementation of strict Access Control Lists (ACLs) to enforce the **principle of least privilege** between all network segments.

### **Stage 4: Defense Hardening & Monitoring**

* **Objective:** Apply proactive security measures to prevent a repeat of Stage 1 attacks.
* **Demonstrated Skills:** Systems Hardening (Active Directory/GPO, Linux Server hardening), Centralized Logging (SIEM integration), Intrusion Detection System (IDS) Configuration, Endpoint Hardening.
* **Defense Implemented:** Installation and configuration of an IDS (e.g., Snort/Suricata) to actively monitor and alert on suspicious traffic, plus implementation of strong Group Policy Objects (GPOs) across the domain.

---

## 🛠️ Technologies Used

| Category | Technologies |
| :--- | :--- |
| **Virtualization** | VMware Workstation / VirtualBox |
| **Network Emulation** | Cisco Packet Tracer, GNS3 (for advanced routing/firewall) |
| **Servers / OS** | Windows Server (Active Directory Domain Services), Linux (Ubuntu/Debian) |
| **Security Tools** | Kali Linux, Nmap, Responder, Burp Suite, Hashcat, `sqlmap` |
| **Defensive Tools** | pfSense/OpnSense (Firewall), Snort/Suricata (IDS/IPS), Wazuh/Splunk Free (SIEM/Logging) |

---

## 🔗 Project Deliverables

* [Link to Stage 1 Penetration Testing Report]
* [Link to Stage 2 Secure Architecture Proposal and Network Diagrams (VLANs, Subnets)]
* [Link to Key Configuration Files (Firewall Rules, GPOs, Server Hardening Scripts)]
