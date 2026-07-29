# active-directory-cybersecurity-home-lab
Active Directory Cybersecurity Home Lab
# 🛡️ Active Directory Cybersecurity Home Lab

![Windows Server](https://img.shields.io/badge/Windows%20Server-2022-0078D6?style=for-the-badge&logo=windows)
![Active Directory](https://img.shields.io/badge/Active%20Directory-AD%20DS-0078D6?style=for-the-badge)
![Kali Linux](https://img.shields.io/badge/Kali-2026.2-557C94?style=for-the-badge&logo=kalilinux)
![Parallels](https://img.shields.io/badge/Virtualization-Parallels%20Desktop-black?style=for-the-badge)
![LDAP](https://img.shields.io/badge/LDAP-Directory%20Services-0A66C2?style=for-the-badge)
![SMB](https://img.shields.io/badge/SMB-File%20Sharing-green?style=for-the-badge)
![Nmap](https://img.shields.io/badge/Nmap-Network%20Enumeration-orange?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-success?style=for-the-badge)

---

# 📖 Overview

This project demonstrates the design, deployment, and security assessment of a small enterprise Active Directory environment built entirely within a virtualized lab. The objective was to gain practical experience administering Windows Server infrastructure while performing reconnaissance and directory enumeration from a Kali Linux workstation using industry-standard cybersecurity tools.

The lab simulates the foundational components commonly found within enterprise environments, including a Windows Server 2022 Domain Controller, Active Directory Domain Services (AD DS), DNS, Organizational Units, security groups, and domain user accounts. After establishing communication between virtual machines, multiple enumeration techniques were performed to analyze exposed network services, shared resources, and directory information.

Rather than simply following installation steps, this project emphasizes understanding how enterprise authentication, directory services, and network protocols interact within a Windows domain. Throughout the build process, networking issues, authentication challenges, and service configuration problems were identified and resolved, providing valuable hands-on experience with real-world troubleshooting.

---

# 🖥️ Lab Environment

| Component | Technology |
|------------|------------|
| Hypervisor | Parallels Desktop |
| Host Operating System | macOS (Intel) |
| Domain Controller | Windows Server 2022 |
| Domain Name | lab.local |
| Workstation | Kali Linux 2026.2 |
| Directory Services | Active Directory Domain Services |
| DNS | Microsoft DNS |
| Networking | Shared (NAT) + Host-Only |
| Enumeration Tools | Nmap, smbclient, smbmap, ldapsearch |
| Authentication | Kerberos / LDAP |
| File Sharing | SMB |

---

# 🌐 Network Topology

```
                   Internet
                       │
                Shared Network
                       │
      ┌────────────────┴────────────────┐
      │                                 │
┌───────────────┐              ┌─────────────────────┐
│ Kali Linux    │─────────────▶│ Windows Server 2022 │
│ Security VM   │ Host-Only    │ Domain Controller   │
│               │              │ DC01                │
└───────────────┘              └─────────────────────┘
                     lab.local
```

---

# ⚙️ Environment Configuration

## 1️⃣ Windows Server Deployment

### Actions Performed

1. Installed Windows Server 2022 Evaluation.
2. Configured a static IP address.
3. Renamed the server to **DC01**.
4. Installed Active Directory Domain Services.
5. Installed DNS Server.
6. Promoted the server to a Domain Controller.
7. Created the Active Directory domain:

```
lab.local
```

---

## 👥 Active Directory Administration

### Actions Performed

1. Created Organizational Units (OUs).
2. Created multiple domain users.
3. Created security groups.
4. Assigned users to appropriate groups.
5. Verified authentication within the domain.

---

## 🌐 Network Configuration

### Actions Performed

1. Configured Shared (NAT) networking for Internet access.
2. Configured Host-Only networking for internal communication.
3. Verified IP connectivity.
4. Verified DNS functionality.
5. Successfully established communication between Kali Linux and the Domain Controller.

---

# 🔍 Network Reconnaissance

## Actions Performed

1. Performed host discovery.
2. Verified ICMP communication.
3. Conducted TCP service enumeration using Nmap.
4. Identified Active Directory services.

### Services Identified

- DNS (53)
- Kerberos (88)
- RPC
- LDAP (389)
- SMB (445)
- Global Catalog
- RPC Endpoint Mapper

---

# 📂 SMB Enumeration

## Actions Performed

1. Enumerated SMB shares anonymously.
2. Authenticated using domain credentials.
3. Enumerated administrative shares.
4. Identified permissions using SMBMap.

### Shares Enumerated

- ADMIN$
- C$
- IPC$
- NETLOGON
- SYSVOL

---

# 📚 LDAP Enumeration

## Actions Performed

1. Performed RootDSE enumeration.
2. Retrieved domain naming contexts.
3. Identified forest and domain functionality levels.
4. Authenticated against LDAP.
5. Enumerated Active Directory users.
6. Identified group memberships.
7. Retrieved directory object attributes.

---

# 🛠️ Troubleshooting

## Issues Resolved

- Dual-NIC configuration within Parallels
- DHCP addressing issues
- Repository configuration errors
- Linux networking problems
- SMB authentication failures
- LDAP authentication issues
- Nmap scan behavior against Windows Server

---

# 💻 Technologies Used

- Windows Server 2022
- Active Directory
- DNS
- LDAP
- Kerberos
- SMB
- Kali Linux
- Parallels Desktop
- Nmap
- smbclient
- smbmap
- ldapsearch

---

# 📈 Skills Demonstrated

| Category | Skills |
|----------|--------|
| Windows Administration | Windows Server Deployment, AD DS Installation, DNS Configuration |
| Identity Management | Active Directory Administration, User Management, Security Groups |
| Networking | Static IP Configuration, NAT, Host-Only Networking, DNS |
| Linux | Package Management, Network Configuration, Troubleshooting |
| Enumeration | Nmap, LDAP, SMB, Active Directory Discovery |
| Security | Authentication Analysis, Directory Enumeration, Share Enumeration |
| Troubleshooting | Connectivity, Authentication, Service Configuration |
| Documentation | Technical Documentation, Lab Design, Portfolio Development |

---

# 🎯 Lessons Learned

## Understanding Enterprise Identity Infrastructure

Building the environment from the ground up provided practical insight into how enterprise identity systems operate beyond theory. Installing Active Directory Domain Services, promoting a Domain Controller, configuring DNS, and creating users and groups demonstrated how authentication and authorization depend on multiple interconnected services. This reinforced the importance of understanding the underlying infrastructure before attempting to secure or assess it.

---

## Enumeration Is Information Gathering, Not Exploitation

A major takeaway from this project was that effective security assessments begin with understanding an environment rather than attacking it. Using tools such as Nmap, SMBMap, smbclient, and ldapsearch illustrated how much information is available to authenticated users through standard protocols. Enumerating network services, directory objects, and shared resources provided valuable visibility into the environment while highlighting why organizations should continuously review permissions, configurations, and exposed services.

---

## Troubleshooting Is a Core Cybersecurity Skill

The most valuable learning moments occurred while resolving issues rather than executing successful commands. Network adapter configuration, DNS resolution, package management, authentication failures, and service communication required systematic troubleshooting and validation. These experiences emphasized that cybersecurity professionals must be capable of diagnosing infrastructure problems, validating assumptions, and understanding how systems interact before meaningful security analysis can occur.

---

# 📸 Project Screenshots

- Windows Server Installation
- Active Directory Users and Computers
- Organizational Units
- Domain Users
- Successful VM Connectivity
- Nmap Service Enumeration
- SMB Share Enumeration
- SMB Permission Enumeration
- LDAP RootDSE Enumeration
- LDAP User Enumeration

---

# 🚀 Future Enhancements

- BloodHound Active Directory Visualization
- Microsoft Sentinel SIEM Integration
- Windows Event Log Collection
- Sysmon Deployment
- Splunk Log Analysis
- Nessus Vulnerability Assessment
- Group Policy Hardening
- Windows Client Domain Join
- PowerShell Automation

---

# 📚 References

- Microsoft Learn – Windows Server Documentation
- Microsoft Learn – Active Directory Domain Services
- Kali Linux Documentation
- Nmap Official Documentation
- Samba Documentation
- OpenLDAP Documentation
- MyDFIR Active Directory Home Lab Series
- MITRE ATT&CK Framework

---

# 👨‍💻 Author

**Virch Reid**

Cybersecurity | IT Support | Windows Administration | Active Directory | Networking | Security+

---

> **Disclaimer:** This project was performed entirely within an isolated virtual laboratory environment for educational and defensive cybersecurity purposes. No production systems or unauthorized networks were accessed during this project.
