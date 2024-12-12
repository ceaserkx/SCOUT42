# SECURITY PROJECT | SCOUT42

Welcome to SCOUT42. 

This is a work-in-progess, self initiated, self managed Cybersecurity practical learning and research project centered on understanding the ***Security***, ***Configuration***, ***Optimization*** and ***Unified*** ***Testing*** of a custom crafted network. The project aims to foster learning in primarily two cybersecurity professions. 
1. **Security Operations Center (SOC) Analyst**
2. **Cybersecurity Engineering**

Other professions are also covered throughout the project:

1. **Cybersecurity Architecture**
2. **Penetration Testing**
3. **Governance, Risk, and Compliance**

I will update this repository as I progress through the project. There will be a much more detailed outline on the components of the network and how they interact with each other. Feel free to [message me](https://www.linkedin.com/in/kareem--ceaser/) on LinkedIn with suggestions and feedback. There are some additional things I may add to the project, most of these ideas are listed under the [Idea Bucket](#idea-bucket) section.

## Contents
- [Scope](#scope)
- [Architecture](#architecture)
- [Components](#components)
- [Procedure](#procedure)
- [Idea Bucket](#idea-bucket)

     
## SCOPE

Understanding how to configure various server types and how they interact with the network as a whole will sharpen knowledge as a prospective SOC Analyst or Cybersecurity Engineer. This project will be challenging and complex for a single indvidual (myself) to build, but I will try to make it as rewarding and repeatable as possible with proper documentation along the way to share with others. I will execute the project in phases as described in the project's [Procedure](#procedure) section. 

This Scope section serves a general overview of the project. The network will include multiple server types such as FTP, DNS, and DHCP, and others. Each and every asset and component of the network will be outlined in the project's [Components](#components) section. I will be using Terraform as an IaaC tool to build out many parts of the project, i.e. pfSense. The network will include security tools to monitor and protect all network assets, such as Firewall, IDS/IPS, SIEM. Azure will house all network assets and security tools. There will be 3 subnets, 1 for the DMZ which will host web server, WAF, mail server, ftp server, and dns server. 1 private subnet will host backend servers such as database server and the SIEM console. 1 subnet for general users to house windows and linux workstations. I will consider hosting a bastion host or jump server.  3 user workstations will be configured securely, 4 will be intentionally insecure to simulate vulnerablities in the network.

Once all network assets are built and security tools are deployed, I will use Kali to generate attack telemetry against servers and endpoints, performing actions such as ssh brute forcing, reverse shelling for C2, etc. I plan to use Python to automate log collection. I would also like to apply common information security compliance standards across the network, perhaps while building the network or at the end of the network building phase for assessment/audting purposes. I may restructure the network to comply with these standards to practice applying frameworks and compliance regulations to live networks. 

## ARCHITECTURE
<a href="https://imgur.com/5yWdcC3"><img src="https://i.imgur.com/5yWdcC3.png" title="source: imgur.com" /></a>

## COMPONENTS
### Infrastructure
- Azure
- DMZ, Private, and Workstation subnets
- IaaC tool - Terraform
- Web Server - nginx
- Database Server - MySQL
- File Server - Nextcloud
- Client Systems (Endpoints) - Windows and Ubuntu
- Active Directory - Windows Server 2025
- DNS - Bind9 (May not use Bind9 due to GCP's built in DNS capabilities)
- Mail Server - iRedMail
- FTP Server - Filezilla
- Routers - pfSense
- Switches - Open Vswitch

### Security Tools

- Firewall - pfSense
- Web Access Firewall - ModSecurity
- SIEM - Wazuh
- IDS/IPS - Suricata
- Pentesting - Kali
- [Test My NIDS](https://github.com/3CORESec/testmynids.org)
- Sliver
- Web server exploitation - SQL Injection, XXS
- Credential attacks - Hydra, Medusa
- Reverse Shells - Metasploit
- Network Scanning - Nmap
- Phishing Simulation - GoPhish

### Automation with Python
- Log parsing with wazuh/suricata
- Alerting - integration with APIs like Slack or email for automated alerts

### Apply Compliance Standards and Frameworks
- NIST 800-53
- NIST RMF
- NIST CSF
- ISO 270001/270000

## PROCEDURE

This section is heavily under maintenance. 

Once all project plans are finalized, this section will provide a step-by-step view on how the project is secured, configured, optimized, and tested. Below is rough draft of the project's procedure. 

1. Planning
    - [ ]  Create and Optimize Network Architecture Diagram
2. Configuration and Optimization
    1. Install Network Components
    - [ ]  2.1 Utilize Terraform to build the network *(DO NOT ALLOW ANY NETWORK 
    COMPONENT TO ACCESS THE OPEN INTERNET UNTIL NETWORK IS 
    TESTED FOR FUNCTIONALITY)*
        - [ ]  2.2 pfSense
            - [ ]  2.2.1 Create DMZ, Private subnet
            - [ ]  2.2.2 Create External and Internall FW function
            - [ ]  2.2.3 Create routing from DMZ to Internal network
            - [ ]  2.2.4 Create routing for switches (need to create switches)
        - [ ]  2.3 nginx
            - [ ]  2.3.1ModSecurity
                - [ ]  2.3.1.1 create static webpage
        - [ ]  2.4 iRedMail
        - [ ]  2.5 FileZilla
        - [ ]  2.6 MySQL
        - [ ]  2.7 AD
        - [ ]  2.8 Nextcloud
        - [ ]  2.9 Open vSwitch
            - [ ]  2.9.1 Switch for DMZ
            - [ ]  2.9.2 Switch for Private Sub
            - [ ]  2.9.3 Switch for User Group
        - [ ]  2.10 User Group
            - [ ]  2.10.1 Deploy and Configure WIN1
            - [ ]  2.10.2 Deploy and Configure WIN2
            - [ ]  2.10.3 Deploy and Configure UBU1
            - [ ]  2.10.4 Deploy and Configure WIN3
            - [ ]  2.10.5 Deploy and Configure WIN4
            - [ ]  2.10.6 Deploy and Configure WIN5
            - [ ]  2.10.7 Deploy and Configure UBU2
        - [ ]  2.11 Wazuh
            - [ ]  2.11.1 Must install agent on all network servers and endpoints
            - [ ]  2.11.2 Setup slack or email alerts for detected alerts
        - [ ]  2.12 Suricata (integrate with pfSense)
            - [ ]  2.12.1 for the DMZ
            - [ ]  2.12.2 for Private Sub
            - [ ]  2.12.3 for User Group
        - [ ]  2.13 TPOT
3. Testing
    - [ ]  3.1 Access nginx website
    - [ ]  3.2 Send an email with iRedMail
    - [ ]  3.3 Access a resource on nextcloud?
    - [ ]  3.4 Try to access MySQL database, make table changes to test functions
    - [ ]  3.5 Login to AD environment and make changes on endpoints, 
    check endpoints to see if changes were made.
    - [ ]  3.6 Ensure able to ping external firewall interface from all network components
    (servers, switches, and endpoints)
    - [ ]  3.7 Ensure getting telemetry into Wazuh from ALL network components
4. Apply Compliance
    - [ ]  4.1 Ensure network complies with standards
        - [ ]  4.1.1 NIST 800-53
        - [ ]  4.1.2 NIST CSF
        - [ ]  4.1.3 ISO 27000/270001
        - [ ]  4.1.4 NIST RMF
5. Network Deployment (to the internet)
6. Execute various attack methods (BREAK THE NETWORK)

## IDEA BUCKET
- Should label each switch and router interface on diagram (as a seperate, confidential diagram document?
- Send Wazuh alerts to iRedMail?
- Probably should consider configuring backups for the network, especially when attack simulations begin.
