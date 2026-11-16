# Cybersecurity Virtual Home Lab


## At a Glance

This project was completed to develop practical, hands-on experience administering enterprise Windows infrastructure and Linux servers within isolated virtual environments. 

### Project Summary

This repository documents two independent virtual lab environments built
in Oracle VirtualBox.

| Environment | Purpose | Core Technologies |
|------------|---------|-------------------|
| Enterprise Windows Lab | Windows enterprise administration | Windows Server 2022, Windows 11, Active Directory, DNS, DHCP |
| Linux Administration Lab | Linux administration & security testing | Ubuntu Server, Apache2, SSH, Kali Linux |

### Key Accomplishments

- Built two independent virtual lab environments using Oracle VirtualBox.
- Configured Windows Server 2022 as an Active Directory Domain Controller.
- Implemented DNS and DHCP services.
- Created Organizational Units, domain user accounts, and security groups.
- Installed and configured Apache2 on Ubuntu Server.
- Enabled secure remote administration using SSH.
- Performed network validation and basic enumeration from Kali Linux.
- Documented implementation steps and troubleshooting methodologies.


# Overview

This project covers the creation of two independent virtual lab environments built using Oracle VirtualBox to strengthen practical skills in enterprise Windows administration and Linux system administration.

The initial environment focuses on core Microsoft enterprise technologies, including a Windows Server 2022 Domain Controller and a Windows 11 domain client. Through this environment, I gained practical experience deploying Active Directory Domain Services (AD DS), configuring DNS and DHCP, creating and managing domain user accounts, creating Organizational Units (OUs), and implementing security groups. 

The second environment focuses on Linux administration and cybersecurity techniques. An Ubuntu Server was configured to host an Apache2 web server, allow remote administration using SSH, and handle network validation from a Kali Linux workstation. This environment gave hands-on experience in Linux service management, troubleshooting connectivity issues, and performing basic network reconnaissance. 

Although the two environments were created independently, together they strengthened my understanding of administering both Linux and Windows systems while reinforcing structured procedures, enterprise networking principles, and technical documentation.


# Lab Architecture

## Enterprise Windows Lab

### Purpose:

Develop practical experience administering a Windows enterprise environment through AD-DS, DHCP, DNS, user management, and Windows networking. 


Virtual Machines:
- Windows Server 2022 (Domain Controller)
- Windows 11 (Domain Client)


![Enterprise Windows Lab](images/architecture/windows-lab.png)

*Enterprise Windows lab consisting of a Windows Server 2022 Domain Controller and a Windows 11 domain client.*

## Linux Administration Lab

### Purpose:

Develop Linux administration skills through server deployment, web server configuration, remote administration, and network validation. 

Virtual Machines:

- Ubuntu Server 
- Kali Linux 

![Linux Administration Lab](images/architecture/linux-lab.png)


# Objectives

## Enterprise Windows Lab

-   Deployed and configured Active Directory Domain Services (AD DS).
-   Configured DNS for internal name resolution.
-   Configured DHCP to automatically assign IP addresses to client systems.
-   Created Organizational Units (OUs) to organize domain resources.
-   Created and managed domain user accounts.
-   Configured security groups for role-based administration.

## Linux Administration Lab

-   Deployed and configured an Ubuntu Server.
-   Installed and configured the Apache2 web server.
-   Configured OpenSSH for secure remote administration.
-   Verified network connectivity between Ubuntu Server and Kali Linux.
-   Performed basic network reconnaissance using Kali Linux. 


# Technologies

## Virtualization

-   Oracle VirtualBox

## Windows

-   Windows Server 2022
-   Windows 11
-   Active Directory Domain Services (AD DS)
-   DNS
-   DHCP

## Linux

-   Ubuntu Server
-   Apache2
-   OpenSSH
-   UFW

## Security

-   Kali Linux
-   Nmap

<details open>
<summary><strong>Enterprise Windows Lab</strong></summary>

## Environment Overview

> **Initial Goal:** Build and administer a Windows enterprise environment using Microsoft's core infrastructure services.


The Enterprise Windows Lab was designed to simulate a small business environment using Windows Server 2022 and Windows 11. The primary objective of this virtual environment was to gain practical experience administering a Windows domain and becoming familiar with core Microsoft enterprise technologies.

Through this lab, I configured Active Directory Domain Services (AD DS), DHCP, DNS, Organizational Units (OUs), domain user accounts, and security groups before verifying communication between the Domain Controller and the Windows 11 client. 

This environment provided hands-on experience with centralized authentication, user administration, and network services that are commonly found in enterprise Windows environments. 
## Domain Controller

The first step in building the Windows environment was installing AD DS and promoting the server.

A Domain Controller provides centralized authentication and authorization services for devices and users within a Windows domain. By configuring the server as the Domain Controller, it became responsible for managing user authentication, domain resources, and administrative policies through the environment.

### Tasks Completed 

- Installed Active Directory Domain Services (AD DS)
- Promoted Windows Server to a Domain Controller 
- Created a new Active Directory domain
- Verified successful domain deployment 

![Administrator Login](images/active-directory/administrator-login.png)

*Successfully authenticated to the Domain Controller using the built-in domain administrator account.*

## Organizational Units

To simulate a small enterprise environment, Organizational Units (OUs) were created to logically organize users by department. 

Organizational Units simplify administration by allowing users, computers, and other directory objects to be grouped according to their role within an organization. This structure also provides the foundation for applying Group Policy Objects (GPOs) and delegating administrative responsibilities as the environment grows, something that is planned for future improvements on this project.

### Organizational Units Created:

- Information Technology (IT)
- Finance 
- Human Resources 
- Executive

![Organizational Units](images/active-directory/organizational-units.png)

*Organizational Units created to separate users by department.*

 ## Domain User Accounts 

 After creating the Organizational Units (OUs), user accounts were created for each department to simulate employees within a small enterprise environment. Creating multiple departmental accounts provided practical experience with user management, account organization, and Active Directory administration. **Note:** names of users are randomly generated.

### Information Technology

![IT Users](images/active-directory/it-users.png)

*Example user accounts created for the Information Technology department.*

### Finance

![Finance Users](images/active-directory/finance-users.png)

*Finance department user accounts.*

### Human Resources

![HR Users](images/active-directory/hr-users.png)

*Human Resources department user accounts.*

### Executive

![Executive Users](images/active-directory/executive-users.png)

*Executive department user accounts.*

## Security Groups

Security Groups were created within Active Directory to demonstrate centralized user management and establish a foundation for role-based access control. Rather than managing users individually, Security Groups allow administrators to organize accounts according to their responsibilities and assign permissions to groups when configuring access to resources. Throughout this lab, I created role-based security groups, assigned users to the appropriate groups, and verified their memberships. This approach helped me understand how organizations can simplify user administration while supporting more scalable access management.

### Tasks Completed:

- Created role-based security groups 
- Added users to the appropriate groups 
- Verified group memberships

![Security Groups](images/active-directory/security-groups.png)

*Example Active Directory security group demonstrating centralized user management.*

## DNS

Active Directory relies on DNS to locate Domain Controllers and other domain services within a Windows environment. Proper DNS configuration allows domain clients to discover the services that are required for authentication and communications with the Domain Controller. As part of this lab, DNS was configured to provide internal name resolution and support communication between the Windows Server and Windows 11 workstation. 

### Tasks Completed:

- Verified Forward Lookup Zones
- Verified Reverse Lookup Zones
- Validated DNS name resolution

**Note**: Future updates to this project will include the screenshots of DNS configuration. 

## DHCP

DHCP was configured to automatically assign IP addresses and network configuration information to client systems within the virtual environment. Automating IP address assignment simplifies network administration while ensuring devices receive consistent network settings.   

### Tasks Completed:

- Created a DHCP scope 
- Configured the address pool 
- Verified client leases 
- Validated DHCP functionality

![DHCP Scope](images/networking/dhcp-scope.png)

*Configured DHCP Scope.*

## Windows Client Verification

After configuring Active Directory, DNS, and DHCP, I performed network validation tests on the Windows 11 workstation to verify communication with the Domain Controller. This included reviewing the client's IP configuration, confirming its configured DNS server, and testing network connectivity using the `ping` command. The successful connectivity test demonstrated that the Windows 11 workstation was able to communicate with the Domain Controller over the virtual network. These tests provide a foundation for further verification of the domain services configured throughout the lab.  

### Verifications Performed:

- Verified IP configuration 
- Confirmed DNS server assignment 
- Tested network connectivity
- Verified communication with the Domain Controller

![IP Configuration](images/networking/ip-configuration.png)

*Windows client network configuration.*

![Ping Test](images/networking/ping-test.png)

*Successful communication between the Windows client and the Domain Controller.*
</details>

<details>
<summary><strong>Linux Administration Lab</strong></summary>

## Environment Overview

The Linux Administration Lab was developed independently from the Windows environment to strengthen practical Linux administration skills and gain hands-on experience managing common server services. This environment consisted of an Ubuntu Server that served as a primary web server and a Kali Linux workstation used for administration, connectivity testing, and basic network reconnaissance. 

Throughout this lab, I successfully installed and configured Apache2, enabled SSH for remote administration, validated network connectivity, and used Kali Linux to access and interact with the Ubuntu Server. This environment provided practical experience administering Linux systems while reinforcing networking fundamentals, service management, and troubleshooting methodologies commonly used by system administrators and cybersecurity professionals. 

## Ubuntu Server

Ubuntu Server served as the primary Linux server for this lab environment. The server was configured to host an Apache2 web server while also supporting secure remote administration through SSH. Throughout the project, Ubuntu was used to practice Linux system administration, service management, firewall configuration, and network troubleshooting.

### Tasks Completed:

- Installed Ubuntu Server
- Updated system packages
- Installed Apache2
- Configured the UFW firewall
- Enabled SSH
- Verified running services 

![Ubuntu Server](images/linux/ubuntu-server.png)

*Ubuntu Server configured for web hosting and remote administration.*

## Apache2 Web Server

Configuring the Apache2 web server presented several challenges, particularly when troubleshooting connectivity between the Ubuntu Server and Kali Linux workstation. These issues and the troubleshooting steps taken to resolve them are discussed in greater detail in the Troubleshooting & Validation section.

### Tasks Completed:
- Installed Apache2
- Started the Apache service 
- Verified the service status
- Confirmed the default webpage loaded successfully 

![Apache Webpage](images/linux/apache-webpage.png)

*Default Apache webpage successfully served from the Ubuntu Server.*

## Secure Shell (SSH) 

SSH was configured to allow secure remote administration of the Ubuntu Server from the Kali Linux workstation. Using SSH made it possible to administer the server remotely without requiring direct console access, closely mirroring how Linux servers are commonly managed in enterprise environments. 

### Tasks Completed:
- Enabled the SSH service
- Verified remote connectivity
- Successfully authenticated from Kali Linux 
- Performed remote administrative tasks 

![SSH Connection](images/linux/ssh-login.png)

*Successful SSH connection established between Kali Linux and the Ubuntu Server.*

## Network Connectivity Verification

After configuring the Ubuntu Server, connectivity testing was performed in order to verify successful communication between the server and the Kali Linux workstation. The successful communication confirmed that the virtual machines were correctly configured and able to exchange network traffic.

### Validation Performed:

- Verified IP configuration 
- Tested connectivity using `ping`
- Confirmed access to the Apache web server 
- Verified SSH connectivity

![Connectivity Test](images/linux/connectivity-test.png)

*Successful communication between Ubuntu Server and Kali Linux.*


## Kali Linux

Kali Linux served as the administrative and testing workstation throughout this environment. After the Ubuntu Server had been fully configured, Kali Linux was used to validate network connectivity, remotely administer the server using SSH, and perform basic network reconnaissance. Using Kali Linux in this lab reinforced fundamental networking concepts while providing practical experience interacting with Linux systems from a security-focused operating system. Kali Linux will also serve as the primary workstation that will be used for future cybersecurity projects.

### Tasks Completed:

- Connected to Ubuntu Server using SSH 
- Validated network connectivity
- Performed network scanning 
- Verified running services 
</details>

<details>
<summary><strong>Troubleshooting & Validation</strong></summary>

Throughout both lab environments, I encountered several configuration challenges while performing validation tests to confirm that services were functioning properly. Rather than relying on trial and error, I followed a structured troubleshooting process by verifying system configurations, testing network connectivity, validating running services, and isolating potential causes before implementing solutions. The following case studies summarize examples of the troubleshooting and validation processes used throughout the project.

## Case Study 1 - Apache Web Server Connectivity 

### Initial Issue

After installing Apache2 on the Ubuntu Server, I attempted to access the default webpage from the Kali Linux workstation. Although Apache2 had been installed successfully, the webpage could not be reached. 

### Investigation 

To  identify the root cause of this connectivity issue, I performed the following validation steps:

1. Confirmed Apache2 was correctly installed.
2. Verified that the Apache service was running using `systemctl status apache2` command.
3. Confirmed basic network connectivity between Ubuntu Server and Kali Linux using `ping` command.
4. Reviewed the Ubuntu firewall (UFW) configuration.
5. Identified that HTTP traffic on TCP port 80 was not permitted by the current UFW firewall configuration.
6. Updated the UFW firewall configuration to allow HTTP traffic on TCP port 80.
7. Retested access from the Kali Linux workstation.

### Resolution 

After allowing the HTTP traffic through the Ubuntu firewall and confirming that the Apache service was active by using the command in step 2, the default Apache webpage became accessible from the Kali Linux workstation.

## Key Takeaway

This issue reinforced the importance of validating service status, firewall configuration, and network connectivity before assuming an application has been configured incorrectly. 

## Case Study 2 - SSH Remote Administration 

### Initial Issue

SSH connections from the Kali Linux workstation to the Ubuntu Server initially failed, preventing remote administration.

### Investigation

In order to isolate the issue, I performed the following steps:

1. Confirmed the OpenSSH service was installed. 
2. Verified that the SSH service was running.
3. Confirmed the Ubuntu Server IP address. 
4. Tested network connectivity using `ping` command.
5. Reviewed the UFW firewall configuration
6. Retested the SSH connection after confirming the required service and firewall settings.

### Resolution

Once the SSH service and firewall configuration were verified, remote administration was successfully established between the Ubuntu Server and Kali Linux workstation.

### Key Takeaway 

This issue demonstrates the importance of validating services and connectivity before unnecessarily modifying server configurations. 

## Case Study 3 - Windows Infrastructure Validation 

### Objective 

This case study does not revolve around an issue that was encountered throughout the project but rather a step for verification. After successfully configuring Active Directory Domain Services, DNS, and DHCP, I needed to verify that the Windows 11 client could communicate successfully with the Domain Controller. 

### Validation Process

I performed the following steps for validation:

1. Reviewed the Windows 11 client's IP configuration.
2. Confirmed the configured DNS server address. 
3. Verified that the client was using the expected network settings.
4. Tested network connectivity with the Domain Controller using the `ping` command.
5. Confirmed that the Windows 11 workstation could successfully communicate with the server over the virtual network. 

### Outcome

The Windows 11 workstation successfully communicated with the Domain Controller during network connectivity testing. This confirmed that both virtual machines were able to communicate over the configured network. The validation process also reinforced the importance of reviewing IP addressing and DNS configuration when troubleshooting connectivity issues in a Windows domain environment.

### Key Takeaway

This validation process highlighted how closely Active Directory can depend on proper DNS configuration and reinforced the importance of testing enterprise infrastructure after deployment. 
</details>

<details>
<summary><strong>Skills Demonstrated</strong></summary>

## Enterprise Administration

- Active Directory Domain Services (AD DS)
- Domain Controller Administration 
- Organizational Units (OUs)
- Domain User Administration 
- Security Groups
- DNS
- DHCP

## Linux Administration

- Ubuntu Server Administration 
- Apache2 Web Server 
- OpenSSH
- UFW Firewall
- Service Management 

## Networking

- TCP/IP
- IP Addressing 
- DNS Resolution 
- Network Connectivity Validation 
- Network Troubleshooting 

## Cybersecurity

- Kali Linux
- Network Reconnaissance
- SSH Remote Administration 
- Security Documentation 
</details>

<details>
<summary><strong>Future Improvements</strong></summary>

## Windows

- Deploy additional Windows clients to simulate a larger enterprise environment. 
- Implement Group Policy Objects (GPOs) to enforce centralized security policies.
- Explore Active Directory delegation and advanced administrative roles.
- Configure Windows Server Update Services (WSUS) for centralized update management.

## Linux

- Deploy the Wazuh SIEM platform for centralized log monitoring.
- Perform vulnerability assessments using OpenVAS.
- Configure centralized logging for Linux services.
- Harden Apache2 using security best practices. 
</details>

<details>
<summary><strong>Lessons Learned</strong></summary>

## Technical Lessons

Throughout the Windows Lab, I was able to strengthen my understanding of how Active Directory, DNS, and DHCP work together to provide centralized identity management and network services. The Linux Lab strengthened my understanding of Linux Server administration, Apache2, OpenSSH, and enterprise service management. 

## Professional Lessons

This project reinforced the importance of following a structured troubleshooting methodology rather than relying on the trial and error method to make configuration changes. Throughout both environments, I learned the importance of verifying services, confirming network connectivity, validating system configuration, and isolating any potential causes before taking action. Developing clear documentation throughout this project has also demonstrated the importance of being able to communicate technical work in a professional and structured manner. 
</details>

<details>
<summary><strong>References</strong></summary>

-   **Microsoft Learn: Active Directory**
 https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/get-started/virtual-dc/active-directory-domain-services-overview
-   **Microsoft Learn: DNS** 
https://learn.microsoft.com/en-us/windows-server/networking/dns/dns-overview
-   **Microsoft Learn: DHCP**
https://learn.microsoft.com/en-us/windows-server/networking/technologies/dhcp/dhcp-top
-   **Ubuntu Documentation** 
https://ubuntu.com/server/docs/
-   **Apache HTTP Server Documentation**
https://httpd.apache.org/docs/
-   **Oracle VirtualBox Documentation**
https://www.virtualbox.org/wiki/Documentation
</details>
