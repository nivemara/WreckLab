# **Phase 0 - The Machine**

This phase is about defining the purpose, identity and direction of this PC so it becomes a structured homelab/training environment.

What will this machine be?
	- Essentially a virtualisation host + Windows domain lab.

## **1. Machine Naming Process**

The name I have decided to give this machine is **WreckLab**.

***Why?***
-  "Wreck" represents breaking things intentionally - corrupting setups, misconfiguring services and simulating failures
-  "Lab" represents the controlled environment for experimentation and learning.
-  WreckLab reflects the core philosophy:
		- *A safe space to break systems, understand failure, and rebuild them properly.*

I felt like this also gives the machine a strong identity that matches its purpose; a sandbox for controlled chaos and learning.
## **2. Machine Purpose, Reasoning and Planning**

This machine will allow me to:
	- Recreate real troubleshooting scenarios (Windows Issues, user access problems, networks faults)
	- Learn and practise Active Directory management
	- Experiment with Windows Server features (users, groups, policies, domains)
	- Build confidence with system administration tasks in a safe environment
	- Break and fix systems intentionally to understand root causes.

***Why did I take this route instead of taking paid IT courses or structure training programs?***

Well, mainly because paid courses can be quite expensive. Most courses are designed around teaching concepts in isolation and preparing you for exams and structured assessments in a controlled environment. However, Service Desk / IT Support work is often messy, scenario-driven, and root-cause focused. It’s less about memorising concepts and more about understanding _what broke, why it broke, and how to fix it under pressure_.

Paid courses typically provide guided labs, predefined outcomes, and clean environments where everything works as expected. What WreckLab gives me instead is broken states that I create myself, unknown problems, real debugging cycles, and decision-making under uncertainty. This mirrors actual IT support work far more closely than most structured courses, because in real environments, nothing is neatly packaged.

Another key point is that I am leveraging existing assets instead of spending money on pre-built learning environments. Why pay for pre-made labs when I can build, configure, break, and rebuild them myself? This not only saves money but also gives me hands-on experience in both software and hardware troubleshooting, including system configuration, OS-level issues, and physical hardware diagnosis.

Courses typically provide a certificate. WreckLab, on the other hand, provides a documented environment, troubleshooting logs, real scenarios I have created and resolved, and a portfolio of systems I have built, broken, and repaired. In interviews, being able to say _“I built and maintained a Windows Server lab with Active Directory, DNS, DHCP, and client troubleshooting scenarios”_ stands out significantly more than _“I completed a course on Windows Server basics.”_

I am not avoiding courses entirely, as I do recognise they are valuable for building foundational knowledge in areas such as networking fundamentals, Windows Server administration, cybersecurity basics, and cloud concepts (e.g., Azure or AWS). I will likely still take some courses in the future where they add value or structure is needed. However, I chose to create WreckLab because I am aiming to become someone who can confidently handle broken systems, not just someone who has studied them.

## **3. Scope Definition**

WreckLab will be virtualised IT Support training environment built on Proxmox VE. The system will be designed to simulate real-world IT infrastructure by hosting multiple isolated virtual machines that replicate enterprise environments.

**Core Infrastructure Layer**
-  Proxmox VE
	-  Installed on hardware directly
	-  BIOS Configuration for virtualisation support (Intel VT-x, boot order, power settings)
	-  Storage configuration (HDD-based (for the time being), ZFS file system)
	-  Network bridge setup for VM communication
- Virtualisation Management
	-  VM creation, deletion and lifecycle control
	-  Resource allocation (CPU, RAM, storage limits)
	-  Snapshotting and rollback for safe experimentation
	-  Isolation of environments for controlled failure testing

**Core Training Environments (Primary Lab Workload)**

These run as VMs inside Proxmox:
-  Windows Server Environment
	-  Active Directory Domain Services (AD AS)
	-  DNS and DHCP roles
	-  Group Policy Objects (GPOs)
	-  Domain controller setup and management

-  Windows Client Environment (Windows 10/11)
	-  Domain-joined workstation simulation
	-  User login and profile troubleshooting
	-  Update, driver and performance issue simulation
	-  Permission and access control issues

**Networking Layer (Simulated Enterprise Network)**
-  Virtual network bridging inside Proxmox
-  IP addressing and subnet configuration within the lab
-  DNS resolution and misconfiguration troubleshooting
-  Simulated network failures and connectivity issues
-  Basic segmentation between server and client environments

**Identity and Access Management**
-  User account creation and lifecycle management
-  Group-based permissions and role assignment
-  Active Directory authentication flow
-  Group Policy enforcement and troubleshooting
-  Access control and privilege escalation simulation (within lab scope)

**System Administration and Recovery**
-  Software installation and deployment scenarios
-  System misconfiguration and recovery workflows
- Snapshot-based rollback after failures
- Service failure diagnosis and repair (Windows services, domain issues, etc.)

## **4. Post WreckLab Stability**

Once WreckLab is running and stable, I want to expand into (if additional hardware is introduced):
-  Linux Server Environment
	-  Ubuntu/Debian servers
	-  SSH management, services, permissions, scripting basics
-  Advanced Virtual Infrastructure
	-  Proxmox clustering
	-  VLANs and more advanced network segmentation
	-  Backup systems and replication strategies

If feasible, I want to integrate my current homelab with WreckLab. 
*Yes, I have already setup a homelab running various services and is still pending on a name*

**Why?**

I would integrate my home lab with Wrecklab to make the environment more realistic and closer to how real IT systems operate. In real workplaces, systems are rarely isolated, and internal infrastructure often interacts with external services, cloud-hosted tools, and separate networks. By connecting the two, I can treat Wrecklab as an internal enterprise environment while using my home lab as external or production-like services.

This would also allow me to simulate hybrid infrastructure setups, which are very common in modern IT environments. I could practice scenarios involving DNS across networks, reverse proxy routing, firewall rules, and service accessibility between internal and external systems. These are the types of issues I would realistically encounter in IT support or infrastructure roles.

It would also help me improve my networking and troubleshooting skills by introducing more complexity. When systems are connected, problems become multi-layered and require deeper investigation across different services and layers, which better reflects real-world diagnostics.

However, I also recognise that integration is not always necessary and can add unnecessary complexity early on. If done too soon, it could make debugging harder and risk affecting stable services in my home lab. Because of this, I would treat integration as an advanced step after the core Wrecklab environment is fully stable.