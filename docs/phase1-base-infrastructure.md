# **Phase 1 - Base Infrastructure**

## **Goal**

Transform existing hardware into the stable foundation of WreckLab by deploying a dedicated virtualisation environment capable of hosting enterprise-style IT infrastructure, troubleshooting scenarios, and repeatable break/fix simulations.

## **Primary Objectives**

- Dedicated lab server running Proxmox VE
- Stable networking with remote access
- Reliable VM deployment capability
- Proper storage organisation
- Snapshot and recovery functionality
- A clean foundation for future Active Directory environments

## **Hardware Preparation**

### Initial Hardware Checks

#### PC Spec Breakdown

- CPU: Intel Xeon Processor 4C/4T
- RAM: 8GB@1333Mhz, ECC memory
- Storage: 500GB HDD

#### Hardware Stability

- Check RAM health
- Verify HDD condition
- Clean dust from system
- Replace failing fans in necessary

#### BIOS Configuration

- Inside BIOS:
  - Enable Intel VT-x (allows for virtualisation)
  - Enable VT-d (allows for virtualisation to directly access physical hardware)
- Configure:
  - Boot Order
  - AHCI mode for storage

## **Proxmox Installation**

### Install Proxmox VE

#### Installation Tasks

- Storage Configuration:
  - Filesystem
  - Hard Disk
- Basic Configuration Options:
  - Location
  - Time Zone
  - Keyboard Layout
- Superuser Configuration:
  - Secure Password
  - Email Address
- Network Configuration:
  - Hostname (FQDN)
  - Static IP Address
  - Gateway
  - DNS Server

#### Post Installation

-  Verify Connectivity
   -  Ping Router
   -  Ping Internet

## **Remote Management**

### Configure Remote Access

- Enable SSH access to Proxmox
- Secure Web Management

## **Organising Environment**

### Creating Structure Standards

- Naming conventions
  - Using naming conventions for VMs and Storage creates a consistent framework that allows information to be instantly readable, searchable and organised. Allows for scalability and easier troubleshooting
  - Examples:
    - Ubuntu VM: UBUNTU01
    - Windows 10: WIN10-CLIENT01
    - Backup: backup-storage

## **Resource Planning**

#### Resource Rules

- Reserve RAM for Proxmox VE
- Avoid overcommitting CPU cores
- Keep VM allocations conservative

#### VM Plan

| VM             | Storage | Purpose              |
| -------------- | ------- | -------------------- |
| DC01           | 60GB    | Domain Controller    |
| WIN10-CLIENT01 | 50GB    | Employee Workstation |

## **Preparing for Future Phases**

### ISOs for VMs

#### Reason for Windows Server 2022 
I chose Windows Server 2022 as my Domain Controller as it provides a highly stable, enterprise-grade foundation for centralising identity, credentials and security policies via Active Directory. Whilst I could choose to go with the Core Installation of 2022 due to resource limitations, I have decided to install Server 2022 with Desktop Experience since it offers the ideal hands-on learning environment, providing a visual map of Active Directory, Group Policies, and network roles that a command-line interface cannot replicate for a beginner.

*Why not Windows Server 2025?*

As someone still learning, I need a solid environment where I could focus on mastering Active Directory without fighting the bugs of a newer OS. From my research when choosing, I found that since Windows Server 2025 is built on the heavier Windows 11 codebase, its graphical interface demands more CPU and RAM resources- an overhead my current specifications simply cannot meet to run efficiently. Sticking to the Windows 10 based architecture allows for a snappier GUI that respects my strict hardware limits, alongside the massive advantage of online tutorials and documentation that exists to further my learning.

#### Reason for Windows 10 IoT Enterprise LTSC over Windows 10 Enterprise LTSC
I chose Windows 10 IoT Enterprise LTSC over the standard Enterprise LTSC because it gives me the absolute leanest Windows footprint possible for my resource-limited environment. While both versions strip out consumer bloatware like Cortana and the Microsoft Store, the IoT version is optimised specifically for fixed purpose hardware, resulting in fewer active background services and a lower idle RAM overhead.

