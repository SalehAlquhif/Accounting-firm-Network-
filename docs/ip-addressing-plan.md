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

Device| IP Address
CSW1| 192.168.10.145
ASW1| 192.168.10.146
ASW2| 192.168.10.147
AP1| 192.168.10.148
AP2| 192.168.10.149

Server – VLAN 50

Device   | IP Address
Server-PT| 192.168.10.178

Printers – VLAN 60

Device| IP Address
Printer 1| 192.168.10.130
Printer 2| 192.168.10.131
Printer 3| 192.168.10.132
Printer 4| 192.168.10.133

4. Router-to-Core Transit Network

Device| Interface| IP Address
CSW1| GigabitEthernet0/1| 192.168.10.193/30
R1| GigabitEthernet0/1| 192.168.10.194/30

- Network: 192.168.10.192/30
- Subnet Mask: 255.255.255.252
- Broadcast: 192.168.10.195

5. Address Assignment Policy

- DHCP will be configured on R1.
- Inter-VLAN routing will be performed by CSW1.
- DHCP relay will be configured on the relevant SVIs.
- Infrastructure devices will use static IP addresses.
- Guest Wi-Fi will be isolated from internal company networks through ACLs.
- The addressing plan reserves capacity for approximately 50% growth in the planned endpoint counts.

6. Design Notes

This is a simulated small-business network built using Cisco Packet Tracer. 
The addressing plan is designed using VLSM to allocate address space efficiently and support future expansion.
