# Cybersecurity Home Lab

## Overview
This project helps demostrate the design and implementation of a virtual cybersecurity home lab that is used to develop hands-on experience using Windows Server administration, Active Directory, Linux server management, network services,
 and vulnerability assesment. This enviornment was built using VirtualBox and consists of multiple virtual machines that were configured to simulate a small enterprise network

 ## Objectives
-  Build a functional Windowsa Active Directory domain
-  Configure core network services
-  Deploy a Linux web server
-  Practice troubleshooting and system administration
-  Perform Vulnerability assessments
-  Develop practical cybersecurity skills that are applicable to enterpirse enviornments

## Tools/Technologies Used
- Oracle VirtualBox
- Ubunut Server
- Kali Linux
- Windows 11
- Windows Server 2022
- Active Directory Domain Services
- Apache2
- DNS
- SSH

## Implementation

### Active Directory

<details>
 <summary>Active Directory Configuration</summary>
Used Windows Server 2022 to configure a domain controller and promoted the server to manage authentication and centralizaed administration.

Tasks:
- Installing Active Directory
- Creating Organizational Units
- Creating user accounts
- Configuring security groups
- Joining Windows clients to the domain
</details> 
 
### DNS
<details>
 <summary>DNS Configuration</summary>
Configured DNS to provide internal name resoltuion for all virtual machines. 

Tasks:
- Forward lookup zones
- Reverse lookup zones
- DNS verification
- Client testing
</details>


### DHCP
<details>
 <summary>DHCP Configuration</summary>
Configured DHCP to automatically assign IP addresses to clients.

Tasks:
- DHCP scope creation
- Reservations
- Lease Verification
- Client testing
</details>

### Ubuntu Web Server
<details>
 <summary>Ubuntu Web Server Configuration</summary>
Installed Ubuntu Server and configured Apache to host a web page.

Tasks:
- Apache installation
- Service management
- Firewall configuration
- SSH configuration
- Remote administration
</details>

### Kali Linux
<details>
 <summary>Kali Linux Configuration</summary>
Used Kali Linux as the security workstation that remote connects to the Ubuntu Server 

Tasks:
- Network discovery
- Service enumeration
- Connectivity testing
- Vulnerability assessment 
</details>

## Challenges Encountered

### Apache Connectivity
<details>
<summary>Apache Connectivity</summary>

Issue: Apache server was unreachable from Kali Linux.

Troubleshooting prcoess:
- Verified Apache service status
- Tested ICMP connectivity
- Reviewed firewall configuration
- Opened TCP port 80 using UFW
- Confirmed successful HTTP communciation

Final Soltuion: Updated the Ubunutu firewall configuration and verified network connectivity
</details>

### SSH Access
<details>
 <summary>SSH Access</summary>
Issue: Remote SSh sessions initially were unsuccessful

Resolution: Confirmed the SSH service was running, validated firewall rules, and tested the connectivity until successful remote administration was established. 
</details>

## Skills Demonstrated From Project

- Windows Server Administration
- Active Directory
- DNS
- DHCP
- Linux Administration
- Apache Web Server
- SSH
- Virtualization
- Network Troubleshooting
- Vulnerability Management
- Security Assessment
- Documentation

## Future Implementations 

## Lessons Learned From Project 
