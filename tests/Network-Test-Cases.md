Network Test Cases

Project

Accounting Firm Network Design & Implementation

Purpose

This document defines the test cases used to validate the functionality, connectivity, security, and reliability of the network infrastructure implemented in Cisco Packet Tracer.

Test Cases

Test ID| Test Description| Expected Result
TC-01| Verify VLAN assignments| Devices are assigned to their correct VLANs
TC-02| Verify DHCP functionality| Clients receive valid IP addresses, gateways, and DNS settings
TC-03| Verify wired connectivity| Wired clients successfully connect to the network
TC-04| Verify wireless connectivity| Wireless clients connect and receive IP addresses
TC-05| Verify inter-VLAN routing| Authorized devices communicate between VLANs
TC-06| Verify DNS functionality| Internal hostnames resolve to the correct IP addresses
TC-07| Verify internal web server| The internal HTTP service is reachable
TC-08| Verify guest network isolation| Guest clients cannot access restricted internal resources
TC-09| Verify employee wireless access| Employee wireless clients access authorized internal resources
TC-10| Verify SSH management| Network devices can be accessed using SSH
TC-11| Verify NAT/PAT| Internal clients access the simulated external network
TC-12| Verify NTP synchronization| Network devices synchronize with the internal NTP server
TC-13| Verify Syslog| Network devices send log messages to the Syslog server
TC-14| Verify Port Security| Switch access ports enforce configured MAC address limits
TC-15| Verify DHCP Snooping| DHCP Snooping is enabled on access switches
TC-16| Verify Dynamic ARP Inspection| DAI is enabled on the designated VLANs
TC-17| Verify STP| Rapid-PVST operates and CSW1 is the root bridge
TC-18| Verify unused ports| Unused switch ports are administratively disabled

Testing Environment

- Cisco Packet Tracer
- Cisco 2911 Routers
- Cisco 3560 Layer 3 Switch
- Cisco 2960 Layer 2 Switches
- PCs, laptops, IP phones, printers, wireless access points, and server

Notes

Testing was performed in a simulated environment.
