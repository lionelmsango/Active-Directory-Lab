# Active Directory On-Premises Lab

**Lionel Sango** 
*Active Directory administration & user support capabilities*

---

## 🎯 Project Objectives

This project demonstrates hands-on Active Directory administration in an isolated lab environment:

1. **Design & implement** production-ready OU structure with German corporate naming
2. **Configure** Group Policy Objects for security and standardization
3. **Document** common support scenarios with troubleshooting procedures
4. **Demonstrate** user lifecycle management (onboarding/offboarding)

---

## 🏗️ Architecture

![Network Topology](https://github.com/lionelmsango/Active-Directory-Lab/blob/e7fa3ec70a31d48c53851f21e481e0514d013c65/network-topography.drawio.png)

**Environment Specifications:**
- **Hypervisor:** Hyper-V on Windows Desktop
- **Domain Controller:** Windows Server 2022 (DC-GW-01)
- **Client Workstation:** Windows 11 Enterprise (CLIENT-WIN11)
- **Network:** Isolated internal vSwitch (192.168.10.0/24)
- **Domain:** yosco.local

---

## 📋 Implementation Tasks Completed

### Task 1: Domain Services Installation
**Objective:** Deploy functional Active Directory Domain Controller

**Actions Taken:**
- Installed Windows Server 2022 on Hyper-V virtual machine
- Configured static IP addressing (192.168.10.10/24)
- Installed Active Directory Domain Services role
- Promoted server to Domain Controller for new forest
- Configured DNS and DHCP services

**Skills Demonstrated:** Windows Server administration, AD DS deployment, DNS configuration, network planning

**Result:** Fully operational domain controller serving yosco.local domain

![Domain Controller](screenshots/02-domain-controller/05-dns-manager.png)

---

### Task 2: Organizational Unit Structure Design
**Objective:** Create professional OU hierarchy with German corporate naming

**Actions Taken:**
- Designed hierarchical OU structure separating users, computers, groups, and locations
- Created organizational units using German naming conventions:
  - **YOSCO-BETRIEB** (main operations container)
  - **Benutzer** with 6 departments: Geschäftsführung, Klima-Team, Advocacy, Kommunikation, Finanzen, IT-Abteilung
  - **Computer** with 3 types: Arbeitsplätze, Laptops, Servers
  - **Gruppen** with Sicherheitsgruppen and Verteilergruppen
  - **Standorte** for Bonn and Berlin offices
- Protected all OUs from accidental deletion

**Skills Demonstrated:** AD architecture, organizational design, German corporate culture awareness

**Result:** Scalable OU structure supporting up to 200 users

![OU Structure](screenshots/03-ou-structure/02-complete-hierarchy.png)

---

### Task 3: User Account Management
**Objective:** Provision 15 user accounts with realistic attributes

**Actions Taken:**
- Created 13 user accounts across 6 departments
- Implemented standardized naming convention (firstname.lastname)
- Configured UPNs for email-style authentication
- Set complex passwords with forced change at first login
- Populated attributes: department, job title, office location, company

**Skills Demonstrated:** User provisioning, identity management, attribute population

**Result:** 13 production-ready user accounts with complete profiles

![Users](screenshots/04-users-and-groups/02-all-users.png)

---

### Task 4: Client Domain Integration
**Objective:** Join Windows 11 workstation and verify policy application

**Actions Taken:**
- Configured Windows 11 VM with static IP
- Joined CLIENT-WIN11 to yosco.local
- Verified GPO application with gpresult
- Tested user authentication

**Skills Demonstrated:** Client deployment, domain integration, GPO verification

![Client](screenshots/06-client-domain-join/04-login-screen.png)

---

### Task 7: Support Scenario Documentation
**Objective:** Document common AD support tasks

**8 Scenarios Documented:**
1. Account lockout resolution
2. Password reset procedures
3. User onboarding workflow
4. Account offboarding


**Skills Demonstrated:** Technical documentation, troubleshooting methodology

---


## 🔧 Technologies Used

- Windows Server 2022, Windows 11 Enterprise
- Active Directory DS, DNS, DHCP
- Group Policy Management
- Hyper-V


---

## 💡 Key Learnings

### Technical Insights

**OU Planning is Critical**
- Pre-planning prevented restructuring
- Department/location separation simplified GPO application

**GPO Testing Requires Patience**
- gpupdate /force and gpresult became essential
- Staged deployment simplified troubleshooting

**DNS is Everything**
- Client DNS must point to DC
- Incorrect DNS = authentication failures

---

## 🚀 Real-World Applications

**Daily Operations:**
- Password resets 
- User provisioning


---

## 📞 Contact

**Lionel Sango**  
📧 lionel.m.sango@gmail.com  
💼 [LinkedIn](https://linkedin.com/in/lionel-sango)  
🐙 [GitHub](https://github.com/lionelmsango)

---

*This project demonstrates AD administration skills for IT Support and System Administrator roles in 40-200 employee organizations.*
