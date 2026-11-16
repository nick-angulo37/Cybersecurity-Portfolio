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

## AWS and Ubuntu Server

I provisioned an EC2 instance running Ubuntu Server and used SSH to administer it. The EC2 security group controlled inbound traffic. During validation, I checked management access separately from the ports used by the honeypot services.

## T-Pot Mini

I installed T-Pot Mini on Ubuntu and inspected the Docker containers that supported the deployment. Cowrie and Mailoney provided decoy services, while Suricata supplied network alerts. The T-Pot web interface provided a place to review the events produced by those components.

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
