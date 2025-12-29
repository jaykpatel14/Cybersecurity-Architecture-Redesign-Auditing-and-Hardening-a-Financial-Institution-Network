# ByBank – Stage 2 Penetration Testing Report

## Document Information

- **Organization:** ByBank  
- **Assessment Stage:** Stage 2 – Penetration Testing  
- **Assessment Type:** Internal Network Penetration Test  
- **Performed By:** Byseciot  
- **Testing Platform:** Kali Linux  
- **Environment:** VMware & GNS3 Lab  
- **Testing Window:** Bank Holiday (Saturday)

---

## 1. Executive Summary

ByBank authorized a full internal penetration testing engagement to validate the security risks identified during **Stage 1 – Risk Assessment**. The objective of this assessment was to determine whether identified weaknesses could be exploited by a real-world attacker and to evaluate the potential business impact.

The assessment demonstrated that multiple high-risk vulnerabilities could be chained together, allowing an attacker to progress from initial network access to sensitive data exposure and internal system compromise. The findings confirm that the current network architecture presents a **high-risk security posture** and requires immediate remediation.

---

## 2. Objectives

The objectives of this penetration test were to:

- Identify exploitable vulnerabilities within the ByBank network
- Validate risks identified during Stage 1
- Demonstrate realistic attack paths and impact
- Assess the effectiveness of existing security controls

No destructive actions were performed during this engagement.

---

## 3. Scope of Testing

### In-Scope Assets
- Network devices (routers and switches)
- Web server
- Database server
- Active Directory Domain Controller
- Windows servers and workstations
- Internal network services

### Out of Scope
- Physical security controls
- Third-party systems
- Denial-of-Service testing

---

## 4. Methodology

The assessment simulated a real-world attacker operating from within the internal network. The following phases were conducted:

- Network discovery and reconnaissance
- Service enumeration
- Initial access
- Web application exploitation
- Credential exposure analysis
- Lateral movement validation
- Privilege escalation validation
- Impact demonstration

All findings were documented with screenshots and supporting evidence.

---

## 5. Vulnerability Summary

| Vulnerability | Description | Impact | Risk |
|--------------|------------|--------|------|
| Default Credentials | Network device accessible using default credentials | Unauthorized access | High |
| Exposed Services | Unnecessary open ports discovered | Network mapping | Medium |
| SQL Injection | Authentication bypass and data exposure | Sensitive data leakage | Critical |
| Command Injection | Remote command execution via web app | Server compromise | High |
| Weak Password Practices | User accounts vulnerable to compromise | Unauthorized access | High |
| Excessive Privileges | Users with elevated local/admin rights | Privilege escalation | Critical |

---

## 6. Detailed Findings & Attack Narrative

### 6.1 Network Discovery

Network discovery techniques were used to identify active hosts and network devices. Multiple internal IP addresses were identified, including infrastructure devices and servers.

One device was observed with an unknown MAC vendor, indicating a potential network infrastructure component.

---

### 6.2 Network Device Access

Further enumeration confirmed the device to be a router exposing a management service. The router was found to be using default credentials, allowing unauthorized administrative access.

**Impact:**  
Access to internal IP addressing and network topology.

**Risk Validated:**  
Use of default credentials on critical infrastructure (High).

---

### 6.3 Internal Network Enumeration

Using information obtained from the router, internal network scanning was performed. This revealed:

- A web server hosting internal banking applications
- A database server
- A domain controller
- Windows workstations with remote access enabled

The flat network architecture allowed unrestricted visibility across all internal assets.

---

### 6.4 Web Application Exploitation – SQL Injection

The internal banking web application was assessed and found vulnerable to SQL Injection. This vulnerability allowed authentication bypass and access to sensitive banking information.

**Impact:**  
Exposure of confidential customer and account data.

**Risk Validated:**  
SQL Injection leading to sensitive data leakage (Critical).

---

### 6.5 Web Application Exploitation – Command Injection

A network diagnostic feature of the web application was found vulnerable to command injection. This allowed controlled execution of system commands on the underlying server, resulting in limited shell access.

**Impact:**  
Demonstrated the ability to execute arbitrary commands and access application files.

**Risk Validated:**  
Remote command execution via web application (Critical).

---

### 6.6 Credential Exposure

Application configuration files contained hardcoded database credentials. While direct database access was restricted, this demonstrated insecure credential storage practices.

**Impact:**  
Credentials could be leveraged for lateral movement or reused across systems.

---

### 6.7 Lateral Movement Validation

Files accessible on the compromised server revealed references to internal user accounts. Authentication testing confirmed that weak password practices allowed access to an internal workstation.

This validated the risk of credential reuse and weak identity controls.

---

### 6.8 Privilege Escalation & Impact

The compromised workstation account was found to possess elevated privileges. This demonstrated the risk of excessive privilege assignment and the potential for full system compromise.

No persistence mechanisms, malware deployment, or security control tampering were performed.

---

## 7. Overall Impact

The penetration test demonstrated that a single initial weakness could be chained into:

- Unauthorized infrastructure access
- Sensitive data exposure
- Internal system compromise
- Privilege escalation

These findings directly validate the risks identified during **Stage 1 – Risk Assessment**.

---

## 8. Recommendations

1. Enforce role-based access control and least privilege principles  
2. Remove default credentials from all infrastructure devices  
3. Implement network segmentation and security zones  
4. Deploy firewalls, IDS/IPS, and web application firewalls  
5. Enforce strong password policies and credential hygiene  
6. Implement centralized logging and continuous monitoring  

---

## 9. Conclusion

The Stage 2 penetration testing engagement confirms that ByBank’s current network architecture is highly vulnerable to chained attacks. Immediate remediation and network redesign are strongly recommended.

Findings from this assessment will be used as input for **Stage 3 – Secure Network Redesign & Hardening**.

---

## Disclaimer

This project represents a simulated penetration test conducted in a controlled lab environment for educational and portfolio purposes only.
