Network Topology Documentation

Accounting Firm Network Design & Implementation

1. Overview

This document describes the network topology designed and implemented for a small accounting firm using Cisco Packet Tracer.

The network is organized into two floors, with separate departments and network services connected through a centralized switching infrastructure.

The design uses a hierarchical structure consisting of an edge router, a Layer 3 core switch, and two Layer 2 access switches.

2. Network Architecture

The network follows a three-layer functional design:

- Edge Layer    :     R1 provides connectivity to the simulated ISP and handles NAT/PAT.
- Core Layer    :     CSW1 provides inter-VLAN routing and connects the internal network to R1.
- Access Layer  :     ASW1 and ASW2 connect end devices, IP phones, printers, and wireless access points.

The overall connection follows this path:

"ISP-R1 → R1 → CSW1 → ASW1 / ASW2 → End Devices"

3. Network Devices and Their Roles

Device    | Model           | Main Responsibility
ISP-R1    | Cisco 2911      | Simulates the Internet Service Provider
R1        | Cisco 2911      | DHCP server, NAT/PAT, and WAN connectivity
CSW1      | Cisco 3560-24PS | Core switching and inter-VLAN routing
ASW1      | Cisco 2960-24TT | First-floor access connectivity
ASW2      | Cisco 2960-24TT | Second-floor access connectivity
Server-PT | Server-PT       | Internal DNS, HTTP, FTP, NTP, and Syslog services
AP1       | AccessPoint-PT  | Guest wireless connectivity
AP2       | AccessPoint-PT  | Employee wireless connectivity

4. Physical Network Layout

The office is divided into two floors.

First Floor – ASW1

The first floor contains:

- Guest Wi-Fi – VLAN 71
- Reception – VLAN 30
- Accounting – VLAN 20

End devices, IP phones, and printers are connected through ASW1 according to their assigned network segments.

Second Floor – ASW2

The second floor contains:

- Employee Wi-Fi – VLAN 70
- Management – VLAN 10
- IT Support – VLAN 40
- Server Network – VLAN 50

ASW2 provides connectivity for the second-floor departments and the internal server.

5. VLAN Organization

Each department and network service is assigned to a separate VLAN.

VLAN ID  | VLAN Name     | Purpose
  10     | MANAGEMENT    | Management department
  20     | ACCOUNTING    | Accounting department
  30     | RECEPTION     | Reception department
  40     | IT_SUPPORT    | IT support department
  50     | SERVERS       | Internal server services
  60     | PRINTERS      | Network printers
  70     | EMPLOYEE_WIFI | Employee wireless network
  71     | GUEST_WIFI    | Guest wireless network
  80     | VOICE         | IP phone traffic
  99     | NET_MGMT      | Network device management

VLAN separation helps organize network traffic and provides a foundation for applying access control policies between departments.

6. Network Connections

The main network connections are:

- ISP-R1 connects to R1 through a dedicated WAN link.
- R1 connects to CSW1 through a routed Layer 3 connection.
- CSW1 connects to ASW1 and ASW2 through trunk links.
- ASW1 and ASW2 connect the end devices on their respective floors.
- AP1 provides guest wireless access, while AP2 provides employee wireless access.

The router-to-core connection uses a routed "/30" network. The access-switch uplinks carry the required VLANs using 802.1Q trunking.

7. Wireless Network Organization

Two separate wireless networks are configured:

Access Point| SSID               | VLAN     | Purpose
AP1         | Accounting_Guest   |      71  | Guest wireless access
AP2         | Accounting_Employee|      70  | Employee wireless access

Both wireless networks use WPA2-PSK security.

Guest wireless traffic is restricted from accessing internal company resources through ACLs.

8. Design Summary

The topology provides a structured network for the accounting firm's two-floor office.

Using a central Layer 3 switch, separate access switches, and dedicated VLANs allows the departments and network services to operate in organized network segments.

The design also provides centralized routing, wireless connectivity, and a connection to a simulated external network.

The topology was implemented and tested in Cisco Packet Tracer.
