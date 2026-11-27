# CASE-STUDIES-AND-PROJECTES
This repositoy is to verify and show off my skill pallet,-.!!!



Overview

This is the CCNA-3v7 (ENSA) Case Study, Rev C, built in Cisco Packet Tracer. In the scenario, a company is deploying a new network to support its users in two locations, Phoenix and Dallas. Your job is to configure all of the routers and switches to match the design. Phoenix is an IPv4 network, Dallas is an IPv6 network, and both reach the Internet through an ISP.

Addressing and VLAN Plan
Network	Address	Purpose
PHX-LAN-A, B, C	172.16.200.0, .201.0, .202.0 /24	User LANs on VLANs 200, 201, 202, with a workstation at .10 on each
PHX-WIFI-LINK	172.16.203.0/24 (VLAN 203)	Link to the wireless router, with a separate wireless LAN (10.10.10.0/24, SSID "PHOENIX") behind it
PHX-MGMT	172.16.204.0/24 (VLAN 204)	Device management
PHOENIX.COM	172.16.205.0/24	Phoenix web server
PHX-LOOPBACK	172.16.206.0/24	Loopback on PHX-RTR-1
PHX-SUPPORT	172.16.207.0/24	Support server running NTP, Syslog, and TFTP
PHX-LAN-D	172.16.208.0/24	Stub network that gets addresses by DHCP from PHX-BRDR
Links A through E	192.168.16.0 to 192.168.20.0 /24	Router and switch interconnects: A is PHX-SW-3 to PHX-RTR-1, B is RTR-1 to RTR-2, C is RTR-1 to BRDR, D is RTR-2 to BRDR, E is RTR-3 to BRDR
Native VLAN	VLAN 500	Native VLAN on trunks
Blackhole VLAN	VLAN 999	Parking VLAN for unused ports
Dallas IPv6	2001:ACAD:1234::/64 networks	ISP link (:1::), router-to-router link (:C::), and LANs on VLAN 300 and VLAN 301

All IPv4 networks are /24 except the ISP link, which is a /29 (209.165.200.225). Default gateways are the first usable address in each range. Hosts use static addresses except where DHCP is specified: PHX-LAN-D by DHCP on PHX-BRDR and DAL-LAN-301 by a DHCP server on DAL-RTR-2. The ISP, DNS servers, and a cisco.com server complete the Internet side.

Topology

Phoenix has three switches (PHX-SW-1, SW-2, and SW-3), one for each user LAN, interconnected with each other. PHX-SW-3 is a Layer 3 switch that connects to PHX-RTR-1 over Link A. A wireless router hangs off PHX-SW-1. Behind the switches sit three routers: PHX-RTR-1 (with the web server and loopback), PHX-RTR-2 (with the support server), and PHX-RTR-3 (with the stub LAN). All three connect to the border router, PHX-BRDR, which faces the Internet. The links use a mix of Ethernet and serial connections.

Dallas has two routers and one switch. DAL-RTR-1 connects to the ISP and DAL-RTR-2, and DAL-SW-1 connects over a trunk to the second router (this looks like router-on-a-stick for VLANs 300 and 301, though that part is my inference). It is an IPv6-only network.

Technologies the Design Calls For
VLANs and trunking with native VLAN 500, and VLAN 999 as a blackhole for unused ports.
Inter-VLAN routing on PHX-SW-3 for VLANs 200 through 204.
EtherChannel using channel group 5 with LACP in active mode, which appears to bundle the links between PHX-SW-1 and PHX-SW-3.
OSPF, with the topology noting process ID 5, to connect all the Phoenix routers and networks.
DHCP for PHX-LAN-D (IPv4) and for DAL-LAN-301 (IPv6).
Wireless configuration on the Wi-Fi router.
Infrastructure services on the support server (NTP, Syslog, TFTP).
IPv6 addressing across Dallas and the ISP link.





<img width="1568" height="680" alt="image" src="https://github.com/user-attachments/assets/771e81a4-8d05-44a8-8907-4d8c4a82213d" />

