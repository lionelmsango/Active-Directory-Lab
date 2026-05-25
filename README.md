# Active Directory On-Premises Lab

---

## Project Objectives

This project demonstrates hands-on Active Directory administration in an isolated lab environment:

1. **Design & implement** production-ready OU structure with German corporate naming
2. **Configure** Group Policy Objects for security and standardization
3. **Document** common support scenarios with troubleshooting procedures
4. **Demonstrate** user lifecycle management (onboarding/offboarding)

---

## Architecture

![Network Topology](https://github.com/lionelmsango/Active-Directory-Lab/blob/e7fa3ec70a31d48c53851f21e481e0514d013c65/network-topography.drawio.png)



**Environment Specifications:**
- **Hypervisor:** Hyper-V on Windows Desktop
- **Domain Controller:** Windows Server 2022 (DC-GW-01)
- **Client Workstation:** Windows 11 Enterprise (CLIENT-WIN11)
- **Network:** Isolated internal vSwitch (192.168.10.0/24)
- **Domain:** yosco.local

---

## Implementation Tasks Completed

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

![Domain Controller](https://github.com/lionelmsango/Active-Directory-Lab/blob/838653160bd0daa9e9200d6d0c40712df94bc76d/Screenshots/screenshot_2_win_server_static_ip.jpg)
![Domain Controller](https://github.com/lionelmsango/Active-Directory-Lab/blob/838653160bd0daa9e9200d6d0c40712df94bc76d/Screenshots/screenshot_2a_ad_ds.jpg)



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

![D](https://github.com/lionelmsango/Active-Directory-Lab/blob/f006b6c905c5cde80fa26d07611b6c7d413d26a2/Screenshots/Screenshot_3a_domain_created_.jpg)
![OU Structure](https://github.com/lionelmsango/Active-Directory-Lab/blob/5a235c82cb5896fe3a0997e7d2406b3721932328/Screenshots/screenshot_4_OU_created.jpg)



---

### Task 3: User Account Management
**Objective:** Provision 13 user accounts with realistic attributes

**Actions Taken:**
- Created 13 user accounts across 6 departments
- Implemented standardized naming convention (firstname.lastname)
- Configured UPNs for email-style authentication
- Set complex passwords with forced change at first login
- Populated attributes: department, job title, office location, company

**Skills Demonstrated:** User provisioning, identity management, attribute population

**Result:** 13 production-ready user accounts with complete profiles

![Users](https://github.com/lionelmsango/Active-Directory-Lab/blob/e08ab56c79f12cac2736751215e9292b20d0d1c6/Screenshots/ascreenshot5a_users.jpg)
![Users](https://github.com/lionelmsango/Active-Directory-Lab/blob/e08ab56c79f12cac2736751215e9292b20d0d1c6/Screenshots/bscreenshot5b_users.jpg)
![Users](https://github.com/lionelmsango/Active-Directory-Lab/blob/bf59ee42e224004db2277ba1c26454873f2e60e7/Screenshots/scre5ccccc.jpg)
![Users](https://github.com/lionelmsango/Active-Directory-Lab/blob/e08ab56c79f12cac2736751215e9292b20d0d1c6/Screenshots/dscreenshot5d_users.jpg)
![Users](https://github.com/lionelmsango/Active-Directory-Lab/blob/e08ab56c79f12cac2736751215e9292b20d0d1c6/Screenshots/escreenshot5e_users.jpg)
![Users](https://github.com/lionelmsango/Active-Directory-Lab/blob/e08ab56c79f12cac2736751215e9292b20d0d1c6/Screenshots/fscreenshot5f_users.jpg)


---

### Task 4: Client Domain Integration
**Objective:** Join Windows 11 workstation and verify policy application

**Actions Taken:**
- Configured Windows 11 VM with static IP
- Joined CLIENT-WIN11 to yosco.local
- Verified GPO application with gpresult 
- Tested user authentication

**Skills Demonstrated:** Client deployment, domain integration, GPO verification

![Client](https://github.com/lionelmsango/Active-Directory-Lab/blob/d9775ddacaff9170bade06fec8f1cda5f6eab03d/Screenshots/Screen6a.jpg)
![Client](https://github.com/lionelmsango/Active-Directory-Lab/blob/d9775ddacaff9170bade06fec8f1cda5f6eab03d/Screenshots/screen6b.jpg)
![Client](https://github.com/lionelmsango/Active-Directory-Lab/blob/d9775ddacaff9170bade06fec8f1cda5f6eab03d/Screenshots/screen6c.jpg)
![Client](https://github.com/lionelmsango/Active-Directory-Lab/blob/d9775ddacaff9170bade06fec8f1cda5f6eab03d/Screenshots/screen6d.jpg)
![Client](https://github.com/lionelmsango/Active-Directory-Lab/blob/d9775ddacaff9170bade06fec8f1cda5f6eab03d/Screenshots/screen6e.jpg)
![Client](https://github.com/lionelmsango/Active-Directory-Lab/blob/3152e3ceb540962e7caa3862416c6c9133af116f/Screenshots/screen6f.jpg)




---

### Task 7: Support Scenario Documentation
**Objective:** Document common AD support tasks

**8 Scenarios Documented:**
1. Account lockout resolution
   - Problem: User Lisa Mueller reports she cannot log in. Error: "Your account has been locked out."
   - Diagnosis: I Opened Active Directory Users and Computers amd navigate to user: Lisa Mueller. I right-click Properties. Account tab shows: "Account is locked out" checkbox is grayed and checked
   - Root Cause: 5 failed login attempts (per Password Policy GPO) - User was typing old password after recent password change
   - Resolution: In user Properties → Account tab Check: ■ "Unlock account. This account is currently locked out" → Click Apply, then OK → Called user: "Your account is unlocked. Please try logging in now" → Received confirmation from user
   - Prevention: - Educate user about Password Manager usage - Consider increasing lockout threshold from 5 to 7 attempts


![Client](https://github.com/lionelmsango/Active-Directory-Lab/blob/c3c13de00812c48655d1d241b4eac8da93421bab/Screenshots/screen7a.jpg)
![Client](https://github.com/lionelmsango/Active-Directory-Lab/blob/c3c13de00812c48655d1d241b4eac8da93421bab/Screenshots/screen7b.jpg)
![Client](https://github.com/lionelmsango/Active-Directory-Lab/blob/c3c13de00812c48655d1d241b4eac8da93421bab/Screenshots/screen7c.jpg)



   
2. User onboarding workflow
   -  Scenario: A new member, Eva Krug, joined the organization's Communications department. Her account has been provisioned and assigned to the appropriate Organizational Unit (OU).

![Client](https://github.com/lionelmsango/Active-Directory-Lab/blob/2b9a68025744481e42deff987599d0fdfc016bf3/Screenshots/sc8.jpg)





4. Account offboarding
   - Scenario: Laura Becker is leaving the organization. Her account has been disabled, a password reset has been performed, and she has been removed from the user group
     
![Client](https://github.com/lionelmsango/Active-Directory-Lab/blob/2b9a68025744481e42deff987599d0fdfc016bf3/Screenshots/sc9a.jpg)
![Client](https://github.com/lionelmsango/Active-Directory-Lab/blob/2b9a68025744481e42deff987599d0fdfc016bf3/Screenshots/sc9b.jpg)
![Client](https://github.com/lionelmsango/Active-Directory-Lab/blob/2b9a68025744481e42deff987599d0fdfc016bf3/Screenshots/sc9c.jpg)
     



**Skills Demonstrated:** Technical documentation, troubleshooting methodology

---


## Technologies Used

- Windows Server 2022, Windows 11 Enterprise
- Active Directory DS, DNS, DHCP
- Group Policy Management
- Hyper-V


---

## Key Learnings

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

## Real-World Applications

**Daily Operations:**
- Password resets 
- User provisioning/deprovisioning


---


---


