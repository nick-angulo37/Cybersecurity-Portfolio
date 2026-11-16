# AWS Honeypot Lab

## At a Glance

I built this project to gain hands-on experience deploying a cloud-based honeypot, troubleshooting Linux and container services, and working with network security telemetry.

### Project Summary

| Environment | Purpose | Core Technologies |
|---|---|---|
| AWS Honeypot Lab | Deploy decoy services and practice reviewing security events from an internet-facing host | AWS EC2, Ubuntu Server, T-Pot Mini, Docker, Cowrie, Suricata |

### Key Accomplishments

- Deployed T-Pot Mini on an Ubuntu Server instance in AWS EC2.
- Used EC2 security groups and SSH during deployment and remote administration.
- Checked container and service status while investigating T-Pot dashboard connectivity.
- Recovered dashboard access after troubleshooting service availability and credentials.
- Explored Nmap for port validation and SpiderFoot with Shodan for IP enrichment.

# Overview

A honeypot exposes decoy services that can record interactions such as connection attempts and login activity. I used T-Pot Mini to bring multiple security tools into a single AWS environment. The project gave me practice administering an Ubuntu host remotely and tracing access problems across AWS networking, the Linux host, and Docker.

# Lab Architecture

| Component | Role in the Lab |
|---|---|
| AWS EC2 and Ubuntu Server | Cloud host for the honeypot deployment |
| EC2 security group | Controls inbound traffic to the instance |
| T-Pot Mini and Docker | Run the honeypot and supporting services in containers |
| Cowrie | Records interactions with a simulated remote login service |
| Mailoney | Provides an SMTP decoy |
| Suricata | Generates network security events and alerts |
| T-Pot web interface | Provides a way to review collected events |
| SSH and Nmap | Support remote administration and port validation |
| SpiderFoot and Shodan | Provide external context for IP addresses during investigation |

# Objectives

- Deploy and administer an Ubuntu-based honeypot in AWS.
- Verify that honeypot services are running and that the management interface is reachable.
- Understand what decoy service logs and network alerts can show during an investigation.

<details open>
<summary><strong>Deployment & Configuration</strong></summary>

## 1. Provisioning the AWS EC2 Instance

I started by creating an Amazon EC2 instance to host the honeypot. Available memory was a factor when choosing the instance and the T-Pot instance and the T-Pot installation profile. I used T-Pot Mini in order to run a smaller set of honeypot services on the resources that were available for the lab.

## 2. Configuring Network Access

I used an EC2 security group to control which connections could reach the instance. This step involved three types of access: SSH for administering the host, browser access to the T-Pot dashboard, and inbound traffic to the decoy services. Being able to keep track of which port served each purpose helped me troubleshoot connectivity issues during and after the installation process. 

I then connected from my Kali Linux virtual machine using SSH and the EC2 key pair. This gave me a remote shell on the instance to install T-Pot and check the host configuration. 

## 3. Installing T-Pot Mini

Once connected to the EC2 instance, I installed T-Pot Mini, T-Pot uses Docker to run the honeypots and supporting tools as containers. Cowrie helped provide a simulate remote login service, Mailoney provided an SMTP decoy, and Suricata generated alerts based on network traffic. 

## Validating the Deployment 

I tested SSH and the T-Pot web interface separately. When the dashboard returned a connection-refused error, I reviewed the EC2 inbound rules, checked whether the T-Pot service was active, and inspected the containers. I also used verbose SSH output and port checks to help narrow down connectivity issues. 

After restoring access to the dashboard, I could use the web interface to review the honeypot activity. Since the honeypot ran on EC2, it could continue collecting events while my local machine was asleep, as long as the cloud instance and its services were running. 

</details>

<details>
<summary><strong>Troubleshooting & Validation</strong></summary>

## Dashboard Connection Refused

### Initial Issue

The T-Pot web interface returned a connection-refused error. During troubleshooting, I also found that the T-Pot service was inactive.

### Investigation

I used SSH to check the service and container status on Ubuntu. I reviewed the relevant inbound rules in the EC2 security group and used port checks to see what was reachable from outside the instance. Checking from both locations helped narrow down whether the service was listening and whether traffic could reach it.

### Outcome

I restored access to the web interface and recovered the dashboard credentials. I also confirmed that the honeypot could only collect new events while the EC2 instance and its services were running.

</details>

<details>
<summary><strong>Security Monitoring</strong></summary>

## Reviewing Events

Cowrie can provide details about a connection or login attempt, while Suricata can flag traffic that matches a detection rule. When reviewing these records, I can use the timestamp, source IP address, and destination port to compare events across tools. SpiderFoot and Shodan can add context about an IP address, such as previously indexed services.

</details>

# Skills Developed

- **Cloud administration** · EC2 provisioning, inbound security group rules, and SSH access.
- **Linux troubleshooting** · Service status checks, port validation, and remote administration.
- **Container operations** · Inspecting Docker containers and checking service availability.
- **Security monitoring** · Interpreting honeypot events and network alerts and enriching IP addresses with external data.

# References

- [T-Pot documentation](https://github.com/telekom-security/tpotce)
