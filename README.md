# Campus Network with Centralized Administration and Monitoring

A personal networking project designed and tested using Cisco Packet Tracer.

## Project Purpose

This project simulates a university campus network connecting IT, Administration, Academic, Voice and Wireless users.

The goal is to practise network configuration, secure administration, centralized services, monitoring and troubleshooting.

## Network Topology

The network includes:

- One simulated ISP router.
- One campus router, R1.
- Three multilayer switches: DSW1, DSW2 and DSW3.
- Three access switches: ASW1, ASW2 and ASW3.
- A central DHCP, DNS, Syslog, NTP and TFTP server.
- A RADIUS authentication server.
- One wireless LAN controller and three lightweight access points.
- Wired PCs, wireless clients and three IP phones.

DSW1 provides inter-VLAN routing. LACP EtherChannels connect the main switches and selected access switches. R1 exchanges routes with DSW1 using OSPF and provides NAT toward the simulated ISP.

## VLAN and IP Address Plan

| VLAN | Name | Network | Default Gateway |
|------|------|---------|-----------------|
| 10 | IT | 192.168.10.0/24 | 192.168.10.1 |
| 20 | ADMIN | 192.168.20.0/24 | 192.168.20.1 |
| 30 | ACADEMIC | 192.168.30.0/24 | 192.168.30.1 |
| 40 | VOICE | 192.168.40.0/24 | 192.168.40.1 |
| 50 | WLAN | 192.168.50.0/24 | 192.168.50.1 |

### Infrastructure Addresses

| Device or Interface | IP Address |
|---------------------|------------|
| DSW1 management / IT gateway | 192.168.10.1 |
| DSW2 management | 192.168.10.2 |
| DSW3 management | 192.168.10.3 |
| ASW1 management | 192.168.10.11 |
| ASW2 management | 192.168.10.12 |
| ASW3 management | 192.168.10.13 |
| RADIUS server | 192.168.10.10 |
| Wireless controller | 192.168.50.10 |
| Central services server | 192.168.50.20 |
| DSW1 connection to R1 | 10.0.0.1/30 |
| R1 connection to DSW1 | 10.0.0.2/30 |
| R1 connection to ISP | 12.12.12.2/30 |
| ISP connection to R1 | 12.12.12.1/30 |

DHCP client ranges are configured from .100 to .199 in each VLAN. The central server supplies addresses for data and wireless VLANs. R1 supplies voice DHCP with option 150 pointing to 10.0.0.2.

## Features Implemented

### Switching and Routing

- Department VLANs and IEEE 802.1Q trunks.
- Inter-VLAN routing using switch virtual interfaces on DSW1.
- LACP EtherChannel for bundled links.
- OSPF between DSW1 and R1.
- Default route advertisement from R1.
- NAT overload toward the simulated ISP.

### Centralized Administration and Services

- DHCP and DHCP relay.
- DNS records for infrastructure devices.
- SSH administration using local user accounts.
- VTY access restrictions allowing SSH from the IT VLAN.
- Centralized Syslog collection.
- NTP configuration for consistent device time.
- TFTP configuration backups and recovery testing.

### Wireless Networking

- Three lightweight APs registered with the wireless controller.
- CAMPUS-WIFI using WPA2-Personal and AES.
- CAMPUS-ENTERPRISE using WPA2-Enterprise and RADIUS.
- DHCP addressing for wireless clients.

### Voice Services

- Voice VLAN 40.
- R1 telephony service and voice DHCP.
- Three registered IP phones.
- Extensions 1001, 1002 and 1003.

## Tests and Results

| Test | Result |
|------|--------|
| Wired client DHCP addressing | Passed |
| Inter-VLAN connectivity | Passed |
| Switch management IP reachability | Passed |
| SSH access from the IT VLAN | Passed |
| SSH blocked from Administration and Academic VLANs | Passed |
| DNS name resolution | Passed |
| Central Syslog receipt from DSW1 and ASW1 | Passed |
| TFTP configuration backup | Passed |
| ASW1 configuration recovery | Passed |
| Connectivity during a single EtherChannel member-link failure | Passed |
| OSPF neighbor formation and campus route learning | Passed |
| NAT translation toward the simulated ISP | Passed |
| Registration of all three wireless APs | Passed |
| WPA2-Personal wireless connectivity | Passed |
| RADIUS login with valid credentials | Passed |
| RADIUS rejection of invalid credentials | Passed |
| Registration of all three IP phones | Passed |
| Call between IP phones | Passed |
| Connectivity of every wireless client | Pending final verification |
| NTP synchronization on all six switches | Pending final verification |
| Syslog delivery from all six switches | Pending final verification |

## How to Open the Project

1. Install Cisco Packet Tracer.
2. Download this repository using Code → Download ZIP.
3. Extract the ZIP file.
4. Open Cisco Packet Tracer.
5. Select File → Open.
6. Select the project .pkt file.
7. Use Realtime mode and allow devices time to start.
8. Test connectivity using ping, Simple PDU and phone calls.

Project filename: REPLACE_WITH_YOUR_FILENAME.pkt

Cisco Packet Tracer version: REPLACE_WITH_YOUR_VERSION

The version can be checked under Help → About in Packet Tracer.

## Project Evidence

Screenshots document:

- The complete network topology.
- VLANs, trunks and EtherChannels.
- OSPF neighbors and routing tables.
- Central Syslog messages.
- TFTP backup files.
- Wireless AP registration and client connectivity.
- Successful IP phone calls.

## Scope and Limitations

This is a simulated campus network for learning and demonstration.

- The ISP connection represents a simulated external network.
- SNMP monitoring is not implemented.
- Wireless users and central services share VLAN 50.
- DSW1 is the single inter-VLAN routing gateway.
- EtherChannel protects against individual member-link failure; it does not provide complete device redundancy.

## Credentials

Any credentials included in the public project are disposable lab credentials. Do not reuse them on real devices or accounts.

## Author

G. D. M. Kumaranayaka

BICT Undergraduate — Networking Specialization  
University of Sri Jayewardenepura
