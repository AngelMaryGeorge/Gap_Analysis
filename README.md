# Scenario

Your company has won a Request for Proposal (RFP) submission to provide a security gap assessment and recommend a secure network architecture for GridLink Utilities, a medium-sized utility responsible for the transmission and distribution of electricity. 

## System Overview

### Company and Network Background

 - GridLink Utilities has been in business for 75 years and currently operates a primary control centre and a backup control centre for their OT network that are approximately 30 minutes apart.
 - GridLink operates 10 transformer stations and 50 distribution stations that cover two medium sized cities and the surrounding areas.
 - GridLink services customers in two relatively large cities and the surrounding area.

 ### System and Network Architecture

 - GridLink operates an Operational Technology (OT) network that is used to manage the physical processes of the utility. 
 - The company also operates a corporate or IT network that is separated from the OT network by firewalls and an industrial DMZ which is used to securely move data between the corporate and OT networks.
 - A wide-area network connects GridLink’s control centres to their transformer and distribution stations.
 - Bill indicates that the OT Operations team manages approximately 250 Windows servers and 75 Linux servers at their primary and backup control centres.
 - Each station that GridLink operates has 1 or 2 workstations that are used to manage the OT devices located at each of the stations.

 ### Key Applications

 - Bill provides information about GridLink’s key applications used in their OT environment. 
 - They operate a distribution management system (DMS) that delivers power to their customers.
 - They also operate an energy management system (EMS) which helps to monitor, control and optimize the performance of the transmission system.
 - They also operate an outage management system (OMS) which provides outage notifications to their customers through automated phone calls, SMS messages and a mobile application.

 ## Existing Security Measures

 ### Network Security

 - GridLink’s corporate network is separated from their OT network by an industrial demilitarized zone (DMS). A part of next generation firewalls are used to restrict traffic between the OT network and the corporate network.
 - GridLink has deployed intrusion detection sensors (IDS) in key areas of their OT network to monitor traffic.
 - GridLink has deployed firewalls at all their stations and are currently halfway finished replacing legacy firewalls at the stations with next generation firewalls that will offer enhanced capabilities such as built in intrusion detection capabilities.
 - Internet access in the OT network is limited to systems or services that need to pull update files from specific vendors. External facing proxy servers are used to control which systems can communicate to specific websites. Internet access is not permitted from GridLink’s transformer and distribution stations.
 - GridLink uses access control lists (ACLs) on routers at their stations to control network traffic in and out of station networks.

 ### Remote Access

 - GridLink has pairs of Internet facing virtual private network (VPN) appliances that allow employees or vendor partners to connect remotely to the OT network.
 - GridLink also has a jump box/server infrastructure which allows users from their corporate network to manage systems that reside in the OT network.

 ### Vulnerability and Patch Management

 - Security patches are applied to servers and workstations located at the control centre and in stations on a monthly basis, using an automated patch deployment platform. Application related patches are applied to systems such as the distribution management system (DMS) and the energy management system (EMS) on a quarterly basis.
 - An agent based automated vulnerability scanning platform has been deployed to scan the end user workstations, the Linux and Windows servers in the control centre on a weekly basis. Network based scanners have been deployed at strategic points on GridLink’s OT network and scans of the routers and switches and other network based devices that support the OT network take place on a monthly basis.

 ### System Security

 - GridLink has deployed anti-virus software on their OT workstations in the control centres and the stations as well as the Windows and Linux servers located in the control centres.

 ## List of devices from GridLink’s OT Network

 - Breakers
 - Historian
 - Email Servers
 - Corporate Web Servers
 - Line Sensors
 - RTU/Gateways
 - Intelligent Electronic Devices (IEDs)
 - Engineering Workstations
 - Enterprise/Corporate Domain Controllers
 - SCADA/Application Servers
 - OT Domain Controllers
 - Operator Workstations


## Stakeholder Info

 - Maureen, the OT operations manager for GridLink. Maureen’s team manages the servers and applications that are located in GridLink’s primary and backup control centres.
 - Leo, is GridLink’s OT network manager. Leo’s team manages the local area networks at the control centres and the wide area network that connects GridLink’s control centres to their stations. Leo’s team is also responsible for maintaining GridLink’s network architecture and his team also manages the firewalls deployed in their OT environment.
 - Anca is responsible for managing GridLink’s Security Operations Centre. Her team provides security monitoring services of GridLink’s OT network and systems and they are also responsible for responding to incidents.
 - Rory is GridLink’s Threat and Vulnerability Management team lead. Rory and his team manage a commercial vulnerabilities

 ## The following are the findings to the meeting:

 ### Remote Access

 You ask about the remote access capabilities that are in place for the GridLink’s OT environment. Leo explains that there is a large terminal services farm in place in the OT environment that users located outside of GridLink’s control centres must use as a “jump server” to manage systems in the control centres or in the downstream transformer and distribution stations. You ask Leo how authentication is handled for these devices and he indicates that users need to login with an active directory account from an OT domain and they also need to enter a PIN combined one-time password from a hardware token to access the terminal server farm.

He also indicates that the other remote access platform that his team supports is a pair of virtual private network (VPN) appliances that were installed to provide remote access for operators so they can access their control centre workstations from home. These VPN appliances were installed during the pandemic to allow operators to continue to work during the lockdown without having to go to one of the control centres. You ask about authentication for these Internet facing VPN appliances and Leo indicates they are integrated with OT Active Directory but do not require a hardware token with a one-time password.

### Network Architecture

You ask Leo to provide an overview of the architecture of GridLink’s Operational Technology network. Leo indicates that the primary and backup control centres are connected by redundant 10 gigabit per second (gbps) dark fibre links. He also indicates that there are firewalls between GridLink’s OT and IT networks and industrial demilitarized (iDMZ) is used to securely allow user’s from GridLink’s corporate network to access OT data that is stored on their historian located in the iDMZ. 

GridLink has started to segment their OT network and currently have created a secure firewalled zone for their recently upgraded energy management system (EMS). Additionally they have separated their development environment from their production network through recently upgraded next generation firewalls. Leo indicates that the existing distribution management system (DMS) and the Outage Management System (OMS)  both reside in the production zone but have not been segmented from other OT applications. There are plans to segment the DMS system as part of an upgrade that will be completed next year. 

### Vulnerability and System Hardening

You ask Maureen, GridLink’s OT Operations manager, how her team hardens the servers they build. She indicates that she works closely with Rory and his team to ensure that server builds are aligned to the Center for Internet Security’s Benchmarks for all of their Windows and Linux server builds. Maureen indicates that there are Windows 10 computers that are used in GridLink’s transformer and distribution stations that are used for local control. She points out that these systems are not hardened as access to the stations is limited by firewalls at each station and Internet access is not available.

You ask whether any legacy operating systems are in use and Maureen indicates that a number of Windows 2012 servers are still in use as the Distribution Management System (DMS) is due for an update next year. Rory jumps in and indicates that these systems have a number of vulnerabilities but cannot be patched as they are no longer supported by Microsoft.

Rory indicates that his team runs scans of the servers and workstations in the control centre on a weekly basis and they provide reports to the OT Operations team. Maureen indicates that her team patches workstations and servers in the control centre on a monthly basis and after patches are applied, Rory’s team runs a scan to validate the success of the patches that have been deployed.

### Security Monitoring and Incident Response

You ask Anca to describe GridLink’s incident response and security monitoring capabilities. Anca indicates that her team receives logs from GridLink’s network equipment as well as their servers and workstations in the control centre. These logs get sent into their SIEM and Anca’s team maintains a number of use cases that are used to detect threats.

Anca also explains that her team maintains separate incident response plans, one for the IT environment and one for the OT environment. They also conduct annual table top exercises for both environments and maintain a series of playbooks that get used when an incident occurs in either environment. Anca indicates that her team does not receive logs back from OT equipment located in their stations but she said that there are plans over the next couple of years to start monitoring these logs as well.


I have completed the security gap assessment based on the information provided and shared the link to the report.

[Security Gap Assessment Report](./Gap%20Assessment%20Report.pdf)

