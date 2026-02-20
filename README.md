# active-directory-lab
Enterprise Active Directory homelab with domain controller, domain-joined endpoints, and structured OU design.

## Overview
This project documents the build of an enterprise-style Active Directory
environment hosted on a self-managed home server.

The lab includes a Windows domain controller, structured organizational units,
security groups, and a domain-joined Windows workstation. It serves as a
realistic foundation and will be updated in phases later introducing SIEM deployment and incident simulations with responses.

## Environment
- Custom Home Server
  - AMD Ryzen 7 9700X 8-Core Processor
  - 32GB DDR5 RAM
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

## Phase 2: Security Information Event Management Deployment (Splunk)
Phase 2 extends the Active Directory lab by introducing logging and basic SIEM capabilities using Splunk Enterprise

## SIEM
- Splunk Enterprise (On Ubuntu Server - splunk01)
  -Splunk Universal Forwarder on:
    -DC01 (Domain Controller)
    -WS01 (Domain-joined workstation)

## Data Sources
- Windows Security Event Logs
- Windows System Logs
- Windows Application Logs

## Ingestion Architecture
- Indexer (Ubuntu Server - splunk01)
- Receiving Port - TCP 9997
- Splunk Web Interface - TCP 8000

## Validation
- Verified forwarder connectivity
- Confirmed log ingestion from DC01 and WS01 with sucessful search queries

Screenshots for this phase are in: [AD-Phase-2](AD-Phase-2)
