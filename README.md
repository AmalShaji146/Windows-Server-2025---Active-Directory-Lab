# Windows-Server-2025---Active-Directory-Lab
Active directory and User management with Windows server 2025 inside virtual box for practical exposure to active directory

Windows Server 2025 – Active Directory Home Lab

Project Overview

A virtualised Windows and Linux infrastructure lab built using Oracle VirtualBox. The objective is to gain practical experience in Windows Server administration, Active Directory, DNS, Group Policy, network configuration and Linux integration.

This project follows a hands-on learning approach:

Understand → Configure → Test → Break → Troubleshoot → Document

The environment is designed to simulate a small organisation's IT infrastructure.

---

1. Lab Environment

Host Machine

Component| Specification
Host OS| Windows 11 Home
CPU| Intel Core i5-11400H
RAM| 16 GB
GPU| NVIDIA RTX 3050 4 GB
Hypervisor| Oracle VirtualBox 7.2.22

Virtual Machines

VM Name| Operating System| Purpose| Status
DC01| Windows Server 2025 Standard Evaluation (Desktop Experience)| Domain Controller, DNS, Active Directory| Installed
CLIENT01| Windows 11 Enterprise Evaluation| Domain client and Group Policy testing| Planned
RHEL01| Red Hat Enterprise Linux| Linux server and Active Directory integration| Planned

---

2. Network Architecture

The lab uses two network adapters on the Domain Controller.

Adapter 1 – NAT

Purpose: Internet connectivity for the Windows Server VM.

Current configuration:

Property| Value
Adapter| Ethernet
Network Mode| NAT
IPv4 Address| 10.0.2.15
Subnet Mask| 255.255.255.0
Default Gateway| 10.0.2.2
DHCP| Enabled

The IP address is automatically assigned by VirtualBox.

Adapter 2 – Internal Network

Purpose: Private communication between virtual machines.

Property| Value
Adapter| Ethernet 2
Network Mode| Internal Network
Internal Network Name| AD-LAB
Initial IPv4| 169.254.229.36
DHCP| Enabled
Default Gateway| None

The initial 169.254.x.x address is an APIPA address. It was assigned automatically because no DHCP server responded on the isolated internal network.

A static IP address will be configured.

Planned IP Addressing Scheme

Machine| Network Interface| Planned IPv4
DC01| NAT| DHCP
DC01| AD-LAB| 192.168.10.10
CLIENT01| AD-LAB| 192.168.10.20
RHEL01| AD-LAB| 192.168.10.30

Subnet mask: "255.255.255.0"

Network: "192.168.10.0/24"

The internal network will not have a default gateway initially. Internet access and internal domain communication are handled separately.

---

3. Current Progress

Completed

- [x] Installed Windows Server 2025 Standard Evaluation.
- [x] Selected Desktop Experience.
- [x] Renamed the server to DC01.
- [x] Configured VirtualBox Adapter 1 using NAT.
- [x] Enabled Adapter 2.
- [x] Configured Adapter 2 as an Internal Network.
- [x] Created the internal network named AD-LAB.
- [x] Verified both network adapters inside Windows Server.
- [x] Identified NAT and Internal Network interfaces using "ipconfig /all".

In Progress

- [ ] Assign static IPv4 address to Ethernet 2.
- [ ] Verify network configuration.
- [ ] Configure DNS.
- [ ] Install Active Directory Domain Services.
- [ ] Promote DC01 to a Domain Controller.
- [ ] Create the first Active Directory domain.

---

4. Planned Active Directory Configuration

Proposed domain name:

"corp.lab"

Domain Controller:

"DC01"

Planned services:

- Active Directory Domain Services (AD DS)
- Domain Name System (DNS)
- Centralised user authentication
- User and group management
- Computer account management
- Group Policy Management

---

5. Learning Objectives

Windows Server Administration

- Windows Server installation and configuration
- Server Manager
- Network adapter configuration
- Static and dynamic IP addressing
- Windows services
- PowerShell administration

Networking

- IPv4 addressing and subnet masks
- NAT and Internal Networks
- DHCP
- DNS and name resolution
- Default gateways
- Network connectivity troubleshooting
- Basic TCP/IP troubleshooting

Active Directory

- Domain creation
- Domain Controller configuration
- Organisational Units (OUs)
- User and security group management
- Computer domain joining
- Password policies
- Group Policy Objects (GPOs)
- Centralised authentication

Linux Integration

- Linux server configuration
- SSH administration
- DNS configuration
- Kerberos authentication
- realmd
- SSSD
- Joining a Linux machine to an Active Directory domain

---

6. Planned Practical Exercises

Exercise| Objective
Static IP configuration| Configure a permanent server IP
DNS configuration| Configure internal domain name resolution
AD DS installation| Create an Active Directory domain
User management| Create and manage domain users
Group management| Configure security groups
Domain joining| Connect a Windows client to the domain
Group Policy| Apply centralised configuration
DNS troubleshooting| Diagnose domain resolution failures
Authentication troubleshooting| Investigate failed domain logins
Linux integration| Authenticate RHEL users through Active Directory

---

7. Troubleshooting and Documentation

Every practical exercise will include:

1. Problem or requirement.
2. Initial system configuration.
3. Commands and configuration changes.
4. Expected results.
5. Actual results.
6. Troubleshooting process.
7. Final resolution.

The purpose is to develop practical troubleshooting ability rather than simply memorising commands.

---

8. Project Goals

By completing this project, the intended outcomes are:

- Build and manage a Windows Server environment.
- Understand Active Directory and domain administration.
- Configure DNS and basic network services.
- Manage Windows users, groups and policies.
- Integrate a Linux server with Windows Active Directory.
- Develop practical troubleshooting skills relevant to junior IT support and system administration roles.

Project status: In progress.

Environment: VirtualBox-based home lab.

Primary focus: Windows Server administration, Active Directory and Linux infrastructure integration.
