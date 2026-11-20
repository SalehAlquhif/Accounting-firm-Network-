Network Testing & Validation Results

1. Overview

This document summarizes the testing and validation performed on the Accounting Firm Network Design & Implementation project.

The objective was to verify network connectivity, VLAN segmentation, IP addressing, network services, security configurations, and Internet connectivity within the Cisco Packet Tracer environment.

2. Network Connectivity

Test                       | Result
VLAN configuration         | Passed
Inter-VLAN routing         | Implemented
DHCP address assignment    | Passed
Wired client connectivity  | Passed
Wireless connectivity      | Passed
R1–CSW1 routed connection  | Passed
ISP connectivity           | Passed

3. Network Services

Service        | Result
DHCP           | Passed
Internal DNS   | Passed
HTTP           | Passed
FTP            | Configured
NTP            | Passed
Syslog         | Passed

4. Wireless Network

Test                                   | Result
Guest Wi-Fi connectivity               | Passed
Employee Wi-Fi connectivity            | Passed
Wireless DHCP assignment               | Passed
Guest network isolation                | Passed
Employee access to internal resources  | Passed

5. Network Security

Security Feature                |   Status
VLAN segmentation               | Implemented
Extended ACLs                   | Configured
SSH remote management           | Configured
Port Security                   | Configured
DHCP Snooping                   | Configured
Dynamic ARP Inspection          | Configured
BPDU Guard                      | Configured
PortFast                        | Configured
Unused ports shutdown           | Implemented
Native VLAN 999                 | Implemented

6. Routing and Internet Connectivity

Feature               | Result
Inter-VLAN routing    | Implemented
Static routing        | Implemented
Default route         | Implemented
NAT/PAT               | Passed
Simulated Internet connectivity| Passed

Internet connectivity was tested using the simulated ISP router and the loopback address "198.51.100.1".

7. Infrastructure Services

- Network devices synchronized with the internal NTP server.
- Syslog messages were successfully sent to the internal server.
- SSH was configured for remote network device management.
- DNS records were configured for internal network services.

8. Security Testing

- Guest wireless clients were unable to access internal company resources.
- Employee wireless clients were able to access authorized internal resources.
- Access switch port security was configured to limit learned MAC addresses.
- DHCP Snooping and Dynamic ARP Inspection were enabled on access switches.
- Unused switch ports were administratively disabled.

9. Packet Tracer Limitations

Extended ACLs were configured and tested on CSW1. However, Packet Tracer did not consistently retain ACL interface bindings in the exported running configuration.

The ACL definitions and intended interface bindings are documented separately.

10. Conclusion

The Accounting Firm network was successfully implemented and tested in Cisco Packet Tracer.

The network provides VLAN-based segmentation, inter-VLAN routing, centralized DHCP and DNS services, wireless connectivity, security controls, remote device management, and simulated Internet connectivity.

The project demonstrates practical networking skills involving network design, configuration, troubleshooting, security, and documentation.

Environment: Cisco Packet Tracer

Project Status: Completed
