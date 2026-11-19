IP Addressing Plan

1. Network Overview

- Project: Accounting Firm Network Design & Implementation
- Network IP: 192.168.10.0/24
- Addressing Method: VLSM
- Inter-VLAN Routing: Layer 3 Core Switch (CSW1)
- DHCP Server: Router R1
- DNS Server: Server-PT
- Default Gateways: SVI interfaces on CSW1

2. VLAN Subnet Allocation

VLAN ID| VLAN Name    | Network Address   |    CIDR    |  Subnet Mask     |   Default Gateway
71     | GUEST_WIFI   | 192.168.10.0      |    /26     |  255.255.255.192 |   192.168.10.1
70     | EMPLOYEE_WIFI| 192.168.10.64     |    /27     | 255.255.255.224  |   192.168.10.65
80     | VOICE        | 192.168.10.96     |    /28     |  255.255.255.240 |   192.168.10.97
20     | ACCOUNTING   | 192.168.10.112    |   /28      | 255.255.255.240  |   192.168.10.113
60     | PRINTERS     | 192.168.10.128    |    /28     | 255.255.255.240  |   192.168.10.129
99     | NET_MGMT     | 192.168.10.144    |   /28      | 255.255.255.240  |   192.168.10.145
30     | RECEPTION    | 192.168.10.160    |   /29      | 255.255.255.248  |   192.168.10.161
40     | IT_SUPPORT   | 192.168.10.168    |   /29      | 255.255.255.248  |   192.168.10.169
50     | SERVERS      | 192.168.10.176    |   /29      | 255.255.255.248  |   192.168.10.177
10     | MANAGEMENT   | 192.168.10.184    |   /29      | 255.255.255.248  |   192.168.10.185

3. Infrastructure Static IP Addresses

Network Management – VLAN 99

Device  | IP Address
CSW1    | 192.168.10.145
ASW1    | 192.168.10.146
ASW2    | 192.168.10.147
AP1     | N/A               AccessPoint-PT does not support configurable management IP addressing in Packet Tracer
AP2     | N/A               AccessPoint-PT does not support configurable management IP addressing in Packet Tracer

Reserved IP Addresses:

- 192.168.10.148
- 192.168.10.149
These addresses are reserved for future infrastructure devices or access points that support configurable management IP addressing.



Server – VLAN 50

Device    | IP Address          | Default Gateway
Server-PT | 192.168.10.178      | 192.168.10.177

Printers – VLAN 60

Device   |       IP Address    |   Default Gateway
Printer 1|    192.168.10.130   |   192.168.10.129
Printer 2|    192.168.10.131   |   192.168.10.129
Printer 3|    192.168.10.132   |   192.168.10.129
Printer 4|    192.168.10.133   |   192.168.10.129

4. Router-to-Core Transit Network

Device| Interface| IP Address
CSW1| GigabitEthernet0/1| 192.168.10.193/30
R1| GigabitEthernet0/0  | 192.168.10.194/30

- Network: 192.168.10.192/30
- Subnet Mask: 255.255.255.252
- Broadcast: 192.168.10.195


5. ISP Connection (WAN Network)

The company router (R1) connects to the simulated ISP router (ISP-R1) through a dedicated point-to-point network.

Device  | Interface            | IP Address
ISP-R1  | GigabitEthernet0/0   | 203.0.113.1/30
R1      | GigabitEthernet0/1         | 203.0.113.2/30

WAN Network Details:

- Network Address: "203.0.113.0/30"
- Subnet Mask: "255.255.255.252"
- ISP Gateway: "203.0.113.1"
- Broadcast Address: "203.0.113.3"

6. Simulated Internet Destination

A loopback interface is configured on ISP-R1 to represent an external Internet destination for connectivity and NAT/PAT testing.

Device| Interface   | IP Address
ISP-R1| Loopback0   | 198.51.100.1/32

This address is used as a simulated external destination in Cisco Packet Tracer. It does not represent a real public Internet connection.

7. Address Assignment Policy

- R1 is configured as a DHCP server for designated  client VLANs.
- Inter-VLAN routing will be performed by CSW1.
- DHCP relay will be configured on the relevant SVIs.
- Infrastructure devices will use static IP addresses.
- Guest Wi-Fi will be isolated from internal company networks through ACLs.
- Available address space is reserved for future network expansion.


8. DHCP Address Allocation

R1 provides dynamic IP address assignments to client devices in the following VLANs.

VLAN ID  |   VLAN Name     |       DHCP Address Range
  71     | GUEST_WIFI      |   192.168.10.2 – 192.168.10.62
  70     | EMPLOYEE_WIFI   |   192.168.10.66 – 192.168.10.94
  80     | VOICE           |   192.168.10.98 – 192.168.10.110
  20     | ACCOUNTING      |   192.168.10.114 – 192.168.10.126
  30     | RECEPTION       |   192.168.10.162 – 192.168.10.166
  40     | IT_SUPPORT      |   192.168.10.170 – 192.168.10.174
  10     | MANAGEMENT      |   192.168.10.186 – 192.168.10.190
 
The default gateway and other reserved addresses are excluded from the DHCP pools. Servers, printers, and network management interfaces use static IP assignments.

9. Routing and NAT Addressing

The following addresses are used for routing and network address translation:

- CSW1 uses "192.168.10.194" as its next hop for the default route.
- R1 uses "203.0.113.1" as its next hop for the default route.
- ISP-R1 has a static return route to "192.168.10.0/24" through "203.0.113.2".
- R1 performs NAT Overload (PAT) using its outside interface address "203.0.113.2".
- The internal network "192.168.10.0/24" is permitted for NAT translation.

10. DHCP and DNS Addressing

DHCP Server

- Device: R1
- DHCP relay is configured on the relevant SVIs of CSW1.
- DHCP relay destination: "192.168.10.194".

DNS Server

- Device: Server-PT
- IP Address: "192.168.10.178"
- VLAN: 50 (SERVERS)
- DNS service provides name resolution for internal network resources.

11. Network Addressing Summary

The network uses three main addressing segments:

Network Segment       |        Network Address        |           Purpose
Internal LAN          |        192.168.10.0/24        | Internal departments, servers, printers, and wireless clients
Router-to-Core Transit|       192.168.10.192/30       | Routed connection between R1 and CSW1
ISP/WAN Connection    |       203.0.113.0/30          | Connection between R1 and the simulated ISP

These networks provide separation between internal devices, routing infrastructure, and the simulated external network.

12.  Design Notes
This is a simulated small-business network built using Cisco Packet Tracer. 
The addressing plan is designed using VLSM to allocate address space efficiently and support future expansion.
- The internal network uses private IPv4 addressing.
- The WAN and simulated Internet addresses use documentation-only IPv4 ranges.
- The router-to-core transit network and ISP connection each use a "/30" subnet.
- The ISP loopback uses a "/32" address.
- NAT/PAT allows internal network devices to reach the simulated external destination.
- The ISP connection is used for lab testing and does not provide actual Internet access.



