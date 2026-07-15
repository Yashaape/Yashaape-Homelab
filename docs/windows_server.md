# Windows Server / Active Directory

![Windows Server](Yashaape-Homelab/screenshots/windows_server.png)

## Overview

A dedicated Windows Server host was added to the lab to simulate the domain services layer found in a typical small business or enterprise IT environment. This host runs Active Directory Domain Services (AD DS) and acts as the identity and access management backbone for the lab, separate from the Linux self-hosted services host.

## Hardware Specifications

| Component | Spec |
|---|---|
| System | HP EliteDesk 800 G3 DM 35W (Mini Desktop) |
| CPU | Intel Core i7-6700T @ 2.80GHz (4 cores / 8 logical processors) |
| RAM | 8GB DDR4 |
| GPU | Intel HD Graphics 530 |
| OS | Microsoft Windows Server 2025 |

## Domain Configuration

- **Domain:** `ad.yashaape.com`
- **Role:** Active Directory Domain Services (AD DS)
- **DNS:** Integrated with AD DS on the same host

## Purpose

- Provide centralized identity, authentication, and access management for the lab
- Practice core Windows Server administration skills used in real IT/helpdesk and sysadmin roles
- Build hands-on experience with Active Directory concepts: domains, organizational units (OUs), user/group management, and Group Policy
- Give the overall lab a "mixed environment" feel (Linux + Windows) similar to what's found in most production IT shops

## Deployment

1. Installed Windows Server 2025 on the HP EliteDesk 800 G3 host
2. Configured static internal networking for the server
3. Installed the Active Directory Domain Services role
4. Promoted the server to a domain controller for `ad.yashaape.com`
5. Configured integrated DNS for the domain

## Integration with the Lab

- Runs as a separate physical host from the Ubuntu/CasaOS services box, keeping domain services isolated from self-hosted applications
- Positioned as the identity layer that the rest of the lab can eventually authenticate against as it grows (e.g., joining future Windows clients/VMs to the domain)
- Remote administration is kept internal to the lab network; no domain services are exposed to the public internet

## Planned Next Steps

- Create Organizational Units (OUs) and structure test user/group accounts
- Apply Group Policy Objects (GPOs) for security baselines
- Join a Windows client machine to the domain for end-to-end testing
- Document DNS and DHCP configuration in more detail

## Lessons Learned

- Windows Server installation and initial configuration
- Promoting a server to a domain controller
- Active Directory fundamentals (domains, forests, DNS integration)
- Planning a segmented network with distinct roles (services host vs. domain controller)
- Practical exposure to the kind of mixed Windows/Linux environments common in real IT departments

---

**Security note:** Internal IP addressing and port configuration are intentionally omitted from this documentation. Domain services are accessible only within the internal lab network and are not exposed to the public internet.
