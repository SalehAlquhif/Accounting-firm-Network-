# Accounting-firm-Network-
Small Business Network Design and Implementation using Cisco Packet Tracer
Project Overview

This project demonstrates the design and implementation of a small accounting firm's network using Cisco Packet Tracer.

The network is designed for a two-floor office environment. It uses VLAN segmentation, inter-VLAN routing, centralized DHCP services, wireless access, network security controls, and simulated Internet connectivity.

Network Topology

"Network Topology" (screenshots/Network-Topology.png)

Network Architecture

The network follows a hierarchical design with dedicated edge, core, and access functions.

- R1 – Edge Router: Provides DHCP, NAT/PAT, and WAN connectivity.
- CSW1 – Layer 3 Core Switch: Handles inter-VLAN routing, ACLs, and connectivity to the access switches.
- ASW1 and ASW2 – Access Switches: Connect end devices, IP phones, printers, and wireless access points.
- ISP-R1: Simulates the Internet service provider.
- Server: Provides internal DNS, HTTP, FTP, NTP, and Syslog services.

VLAN Segmentation

The network is divided into separate VLANs to organize departments and services:

VLAN| Name
10| Management
20| Accounting
30| Reception
40| IT Support
50| Servers
60| Printers
70| Employee Wi-Fi
71| Guest Wi-Fi
80| Voice
99| Network Management

Key Features

- VLAN segmentation and 802.1Q trunking
- Inter-VLAN routing using a Layer 3 switch
- DHCP services and DHCP relay
- Internal DNS and web services
- Wireless networks for employees and guests
- Access Control Lists (ACLs) for traffic control
- SSH remote device management
- NAT/PAT for simulated Internet access
- Rapid-PVST+ spanning tree
- Port security
- DHCP snooping and Dynamic ARP Inspection
- NTP time synchronization and Syslog monitoring

Testing

The implementation included connectivity and service checks, including:

- DHCP address assignment
- Inter-VLAN connectivity and access restrictions
- DNS resolution and internal web access
- Wireless client connectivity
- SSH device access
- NAT/PAT and simulated external connectivity
- Network time synchronization and Syslog messages

- note Packet Tracer ACL Limitation

Extended ACLs were configured and tested on the Layer 3 switch (CSW1). Traffic filtering behaved as expected during testing. However, Packet Tracer did not consistently retain the ACL interface bindings in the exported running configuration.
The ACL definitions are included in "configs/CSW1-running-config.cfg", and the intended interface bindings are documented separately in "configs/CSW1-ACL-Applications.cfg".

This limitation is specific to the Packet Tracer simulation environment.

Tools and Technologies

- Cisco Packet Tracer
- Cisco IOS CLI
- VLANs and 802.1Q
- IPv4 subnetting
- Static routing
- DHCP, DNS, HTTP, FTP, NTP, and Syslog
- ACLs, SSH, NAT/PAT
- Layer 2 security features

Repository Structure

- "Packet-Tracer/" – Packet Tracer project file
- "configs/" – Network device configurations
- "docs/" – Network documentation and IP addressing plan
- "screenshots/" – Network topology screenshot
- "tests/" – Testing notes and results

Project Status

Completed – Network designed, implemented, and tested in Cisco Packet Tracer.

This is a simulated lab environment created for learning and portfolio demonstration. The ISP and external connectivity are simulated within Packet Tracer.
