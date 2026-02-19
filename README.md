# active-directory-lab
Enterprise Active Directory homelab with domain controller, domain-joined endpoints, and structured OU design.

## Overview
This project documents the build of an enterprise-style Active Directory
environment hosted on a self-managed home server.

The lab includes a Windows domain controller, structured organizational units,
security groups, and a domain-joined Windows workstation. It serves as a
realistic foundation and will be updated in phases. 

## Environment
- Custom Home Server
  - AMD Ryzen 7 9700X 8-Core Processor
  - 34GB DDR5 RAM
  - NVMe 1TB SSD Storage
  - Proxmox Virtual Environment

- Operating Systems (Virtual Machines)
  - Windows Server 2022
  - Windows 11 Pro

## Architecture
- Domain: `lab.local`
  - Domain Controller: DC01 (Windows Server 2022)
  - Workstation: WS01 (Windows 11 Pro)

- Organizational Unit (OU) Design
  - CORP
    - Admin
      - Admin_Workstations
    - Endpoints
      - Laptops
      - Workstations
    - Identity
      - Privileged_Users
      - Service_Accounts
      - Standard_Users
    - Quarantine
    - Servers
      - Application_Servers
      - File_Servers

*The structure mirrors common enterprise design patterns and supports
role-based access control and future Group Policy application.*

## Phase 1: Active Directory
Phase 1 establishes the core enterprise identity infrastructure:

- Setup & Configuration
- Deployment of a Windows Server domain controller
- DNS-backed domain authentication
- Structured OU and security group design
- Creation of standard user accounts
- Domain join of a Windows 11 Pro workstation
- Placement of endpoints into appropriate OUs

Screenshots for this phase are in: [AD-Phase-1](AD-Phase-1)
