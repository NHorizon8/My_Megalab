# CCNA Mega Lab — Objective Plan

## 1. Device Initial Configuration

- [x] Configure hostnames on all routers and switches
- [x] Configure enable secret
- [x] Configure local user account
- [ ] Configure console authentication
- [ ] Configure console inactivity timeout
- [ ] Enable synchronous logging


## 2. Layer-2 Foundation

### 2.1 EtherChannel

- [x] Configure DSW-A1 ↔ DSW-A2 PAgP Layer-2 EtherChannel
- [x] Configure DSW-B1 ↔ DSW-B2 LACP Layer-2 EtherChannel
- [x] Configure CSW1 ↔ CSW2 Layer-3 EtherChannel using the planned interfaces

### 2.2 Trunks

- [x] Configure Distribution-to-Access links as 802.1Q trunks
- [x] Configure Distribution EtherChannel links as trunks where required
- [x] Configure the WLC-facing link for the required VLANs
- [x] Disable DTP on the required trunk links
- [x] Allow only the VLANs used by the actual lab on each trunk

### 2.3 VLANs and VTP

- [x] Configure one Distribution switch as the VTP server
- [x] Configure the required Access switches as VTP clients
- [x] Configure the VTP domain
- [x] Create VLAN 10 for PCs
- [x] Create VLAN 20 for Phones
- [x] Create VLAN 30 for Servers where required
- [x] Create VLAN 40 for Wi-Fi where required
- [x] Create VLAN 99 for Management
- [x] Do not configure unused reference VLANs that are not part of the actual lab

### 2.4 Access Ports

- [x] Configure PC ports for VLAN 10
- [x] Configure Phone ports for VLAN 20
- [x] Configure Server port for the required Server VLAN
- [x] Configure AP/WLC-related ports according to the actual topology
- [x] Configure required ports as access or trunk based on their actual role
- [x] Disable DTP where required
- [x] Shut down unused switch ports

## 3. Layer-3 Foundation

### 3.1 IPv4 Routing

- [x] Enable IPv4 routing on all Core and Distribution switches

### 3.2 Routed Links and Loopbacks

- [x] Configure routed links between R1, CSW1, CSW2, and Distribution switches according to the Address Allocation Plan
- [x] Configure the CSW1 ↔ CSW2 Layer-3 EtherChannel
- [x] Configure Loopback0 on R1
- [x] Configure Loopback0 on CSW1 and CSW2
- [x] Configure Loopback0 on the required Distribution switches

### 3.3 SVIs and HSRP

- [x] Configure Management SVIs
- [x] Configure PC VLAN SVIs
- [x] Configure Phone VLAN SVIs
- [x] Configure Wi-Fi SVI where required
- [x] Configure Server SVI where required
- [x] Configure HSRP virtual IP addresses
- [x] Configure HSRP active/standby roles
- [x] Configure HSRP priorities and preemption

## 4. Spanning Tree

- [x] Enable Rapid PVST+
- [x] Configure STP root placement according to the actual HSRP gateway design
- [x] Configure appropriate STP priority on the secondary side
- [x] Configure PortFast on end-device ports
- [x] Configure BPDU Guard on end-device ports

## 5. OSPF

- [x] Configure OSPF process 1
- [x] Configure Area 0
- [x] Configure router IDs using Loopback0
- [x] Enable OSPF on the required Layer-3 interfaces
- [x] Advertise the required routed networks
- [x] Advertise the required loopback networks
- [x] Configure appropriate passive interfaces
- [x] Configure point-to-point OSPF network type on the required physical routed links

## 6. Internet Connectivity

- [x] Configure the available ISP connection on R1
- [x] Configure the available Internet default route
- [x] Configure OSPF default-route advertisement toward the internal network
- [x] Configure Internet connectivity for the internal network
- [ ] Configure the planned second ISP connection
- [ ] Configure Internet failover between the two ISP connections

> ==Dual-ISP implementation was not completed because of Packet Tracer interface/module limitations. The final lab uses the available Internet connection.==

## 7. DHCP

- [x] Configure DHCP pools on R1 for the required internal networks
- [x] Configure DHCP addressing for Management networks
- [x] Configure DHCP addressing for PC networks
- [x] Configure DHCP addressing for Phone networks
- [x] Configure DHCP addressing for the Server network where required
- [x] Configure DHCP addressing for the Wi-Fi network where required
- [x] Exclude infrastructure addresses from DHCP pools
- [x] Configure DHCP default gateways
- [x] Configure DHCP DNS information
- [x] Configure DHCP relay on the required Distribution SVIs toward R1

## 8. Network Services

- [x] Configure DNS service on the server
- [x] Configure the required DNS records
- [x] Configure the required domain name on network devices
- [x] Configure R1 as the NTP server
- [x] Configure network devices to use R1 as their NTP server
- [x] Configure NTP authentication where required
- [x] Configure SNMP
- [x] Configure Syslog
- [x] Configure local logging buffer
- [x] Configure FTP service where required

## 9. Secure Remote Management

- [x] Configure domain name for SSH
- [x] Configure local user authentication
- [x] Generate RSA keys
- [x] Enable SSH version 2
- [x] Restrict VTY lines to SSH access
- [x] Configure local authentication on VTY lines
- [x] Apply the required management ACL to VTY access
- [x] Configure synchronous logging on VTY lines

## 10. NAT / PAT

- [x] Configure the required Static NAT mapping
- [x] Configure PAT for the required internal networks
- [x] Configure NAT inside interfaces
- [x] Configure NAT outside interface
- [x] Configure the required PAT ACL
- [x] Configure the required PAT address pool

## 11. Layer-2 Security

- [x] Configure Port Security on the required Access switch ports
- [x] Configure the required maximum secure MAC addresses
- [x] Configure sticky MAC addresses
- [x] Configure the required Port Security violation mode
- [x] Configure DHCP Snooping on the active VLANs
- [x] Configure DHCP Snooping trusted interfaces
- [x] Configure DHCP Snooping rate limits where required
- [x] Configure DHCP Option 82 behavior according to the actual lab design
- [x] Configure Dynamic ARP Inspection on the active VLANs
- [x] Configure DAI trusted interfaces
- [x] Configure the required DAI validation checks

## 12. Layer-3 ACL

- [x] Configure the Office A to Office B traffic-control ACL
- [x] Permit the required ICMP traffic
- [x] Restrict the specified traffic between the required Office A and Office B networks
- [x] Permit other required traffic according to the lab design
- [x] Apply the ACL at the appropriate Layer-3 interface

## 13. CDP / LLDP

- [x] Disable CDP where required
- [x] Enable LLDP
- [x] Configure the required LLDP behavior on Access switch ports

## 14. IPv6

- [x] Enable IPv6 routing on the required devices
- [x] Configure IPv6 addressing on R1
- [x] Configure IPv6 addressing on CSW1 and CSW2
- [x] Configure EUI-64 where required
- [x] Enable IPv6 on the Layer-3 EtherChannel where required
- [x] Configure IPv6 default routes
- [x] Configure the required floating IPv6 route

## 15. Wireless / WLC

- [ ] Configure WLC management connectivity
- [ ] Configure the WLC dynamic interface for the Wi-Fi VLAN
- [ ] Configure the WLAN and SSID
- [ ] Configure WPA2/AES wireless security
- [ ] Establish the LWAP/AP connections with the WLC
- [ ] Complete the WLC-based wireless implementation

> ==WLC/Wireless was not fully completed because of Packet Tracer limitations encountered during implementation and troubleshooting.==

- [ ] Wireless clients obtain DHCP addresses from the Wi-Fi DHCP pool

> ==Wireless DHCP client behavior is limited in Packet Tracer, so this part was not completed as a working end-to-end feature.==