<p align="center">
<img width="500" alt="image" src="https://conceptodefinicion.de/wp-content/uploads/2014/06/ccna.jpg">
</p>

<h1>Complete Network Configuration </h1>
This "CCNA Mega Lab" tutorial by Jeremy’s IT Lab is a hands-on walk thorugh that teaches how to configure a complete network using VLANs, OSPF, STP, DHCP, security, and wireless.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: CCNA Mega Lab]([https://www.youtube.com/watch?v=2p7-MluKAgE])](https://www.youtube.com/watch?v=2p7-MluKAgE)

<h2>Environments and Technologies Used</h2>

- Cisco Packet Tracer
<h2>Operating Systems Used </h2>

- Windows 11

<h2>High-Level Deployment and Configuration Steps</h2>

- Part 1 - Initial Setup 
- Part 2 - VLANs, L2 EtherChannel 
- Part 3 - IP Addresses, L3 EtherChannel, HSRP
- Part 4 - Rapid Spanning Tree Protocol
- Part 5 - Static and Dynamic Routing
- Part 6 - Network Services: DHCP, DNS, NTP, SNMP, Syslog, FTP, SSH, NAT
- Part 7 - ACLs and Layer-2 Security Features
- Part 8 - IPv6
- Part 9 - Wireless

<h2>Topology</h2>

<p>
<img <img width="712" alt="image" src="https://github.com/user-attachments/assets/57bb6f5e-9754-4e1a-8165-2d158ba15e5d" />
/>
</p>
<p>

</p>
<br />

<h2>Part 1 - Initial Setup </h2>

<p>
<img <img width="632" alt="image" src="https://github.com/user-attachments/assets/202b5188-6e7f-4eab-b4a7-49cff65f8791" />

  
</p>
<p>
In this first step I am adding a basic configuration to each router and switch. This includes creating a local user account and enabling encryption. I also set idle sessions to be logged out after 30 minutes. This ensures that only authorized users can access and make changes to the devices
</p>
<img <img width="373" alt="image" src="https://github.com/user-attachments/assets/dc299ee8-d309-46a8-834e-ea1657e68390" />
<br />

<h2>Part 2 - VLANs, L2 EtherChannel </h2>

<p>
<img <img width="476" alt="image" src="https://github.com/user-attachments/assets/0f625279-93a6-4c20-af89-3e0f8f996e6b"/>

</p>
<p>

Step 1:
<p>
In the first section, it mentions to configure an EtherChannel using a Cisco-proprietary protocol. For this, we will use Port Aggregation Protocol (PAgP) between DSW-A1 and DSW-A2. PAgP is used to automatically combine multiple physical links into a single logical link, called EtherChannel. This helps increase bandwidth and provides redundancy. It operates in 2 modes: Desireable and Auto. Desireable mode tries to actively form an EtherChannel with the other device. Auto mode waits for the other device to initiate the EtherChannel but won't start it itself. For PAgP to work, one side has to be Desirable.
<p></p>

<img width="239" alt="image" src="https://github.com/user-attachments/assets/39d52c3c-e2dd-46c7-8302-1ff43b28f337" />

</p>

Step 2:
<p>
  The second section asks to use an open standard protocol. In this case, we will use Link Aggregation Control Protocol. It works like PAgP, however; it has 2 modes: Active mode and Passive mode. Active mode actively tries to form an EtherChannel. Passive mode waits for the other device to start the EtherChannel. For this protocol to work, one side must be Active, or both sides can be active.
<p></p>
<img width="245" alt="image" src="https://github.com/user-attachments/assets/fc6c0b36-623f-41ad-ab62-505c8fc9197d" />

  
</p>

Step 3:
<p>
Step 3 wants us to configure trunk links between the Distribution and Access switches. This will ensure that VLAN traffic is able to pass through. To complete this step, I disabled Dynamic Trunking Protocol (DTP) to prevent automatic trunk negotiation. I also changed the native VLAN to VLAN 1000 to prevent VLAN hopping attacks. I then allow only specific VLANs on each trunk, VLANs 10, 20, 40, 99 in Office A and VLANs 10, 20, 30, 99 in Office B. By doing this, I ensure that only the required VLANs are carried over the trunks, improving security and efficiency. 


<br />

<p>
<img width="395" alt="image" src="https://github.com/user-attachments/assets/be3895d6-5f81-44bd-be13-bdad433e3fda" />

</p>
Step 4:

<p>

In this step, I configured one Distribution switch in each office as a VTPv2 server and set the VTP domain name to "JeremysITLab". The VTP protocol automates VLAN configuration management across multiple switches. A VTP server is able to create, modify, and delete VLANs, and automatically sync those changes to the VTP clients. This helps reduce manual configuration errors. I configured all Access switches as VTP clients so they can receive VLAN updates from the server. This setup ensures consistency across the network.

<img width="272" alt="image" src="https://github.com/user-attachments/assets/65740fdb-17c8-4df1-b8e6-affc5b480a86" />


</p>
Step 5-6:
<p></p>
<p>
I created several VLANs on one of the Distribution switches and verified the Access switches received the update from the VTP server.
<p>
</p>
<img width="325" alt="image" src="https://github.com/user-attachments/assets/42aa38b9-65bf-4916-b179-32a992d5770d" />

</p>

Step 7-8:
<p>
In this step, I configured each Access switch's interfaces connecting to end hosts. Lightweight Access Points (LWAPs) are set up without using FlexConnect, meaning they will rely on the wireless controller for all traffic processing. I manually set the ports to access mode and disabled DTP, this prevents any unwanted VLAN negotiation. I also configured ASW-A1's connection to WCL1 to support the Wi-Fi and Management VLANs, providing proper communication between the access points and the controller. The Management VLAN is left untagged, meaning it will be treated as the native VLAN. The purpose of this setup is to ensure proper VLAN segmentation, secure access, and stable connectivity for both wired and wireless devices.
</p>
<img width="335" alt="image" src="https://github.com/user-attachments/assets/a8da114d-70e2-4c93-b261-bf41be88edbb" />

</p>
Step 9:
<p>
The final step is to shut down all unused ports on all Distribution and Access switches to improve security and stability. I used the command "show interface status" to verify the correct ports were shut down.
</p>
<img width="326" alt="image" src="https://github.com/user-attachments/assets/58117b2b-586e-43f0-ba2d-ec7a14108fe3" />
<img width="500" alt="image" src="https://github.com/user-attachments/assets/962552d6-af9e-4393-b612-e76c87c2e745" />


</p>
<h2>Part 3 – IP Addresses, Layer-3 EtherChannel, HSRP </h2>

<img width="700" alt="image" src="https://github.com/user-attachments/assets/664c65b0-a123-4052-a4bf-d3c5e10e9af2" />

<img width="700" alt="image" src="https://github.com/user-attachments/assets/0734e811-f673-4461-a04f-06d8327475fc" />


</p>
Step 1:
</p>
<p>
In this step, I consoled into R1. I set interfaces G0/0/0 and G0/1/0 to act as DHCP clients. Meaning they will automatically be assigned an IP address from a DHCP server. For interfaces G0/0, G0/1, and Loopback0, I manually assigned them an IP address. At the end, I ran the command "do show ip interface brief" to ensure a correct configuration.
</p>

<img width="242" alt="image" src="https://github.com/user-attachments/assets/48147d4f-0597-4550-8181-533e1dd1bc39" />
<img width="527" alt="Part 3, Step 1" src="https://github.com/user-attachments/assets/090a1179-2447-42ca-9fd1-e95f02b0e2d6" />

</p>
Step 2:
</p>
<p>
In this step, I turned on IPv4 routing on all Core and Distribution switches by entering the command "ip routing". This will allow them to forward data between different networks.
</p>
<img width="300" alt="image" src="https://github.com/user-attachments/assets/9fab0138-8636-491f-9c1e-221166367819" />

</p>
Step 3:
</p>
<p>
In this step, I created a layer-3 EtherChannel between CSW1 and CSW2 using a Cisco proprietary protocol (PAgP). Since, both switches are set to desirable, they will actively try to form the EtherChannel. To complete this step, I assigned IP addresses to the PortChanel interface to ensure routing between the two Core Switches. A PortChannel is a virtual interface created by bundling multiple physical links into a single logical one. At the end, I ran the command "do show etherchannel summary" to ensure a correct configuration. 
</p>
<img width="257" alt="image" src="https://github.com/user-attachments/assets/f2439ecf-c243-4c77-9a29-3e5d0b88d959" />
<img width="449" alt="Part 3, Step 3" src="https://github.com/user-attachments/assets/0b6dfa86-beac-4f7c-b907-4f1f33005525" />

</p>
Step 4-5:
</p>
<p>
In steps 4-5, I manually set IP addresses on multiple interfaces od CSW1 and CSW2 to allow communication between them. I then disabled unused ports to improve security and prevent unauthorized connections. 
</p>
<img width="380" alt="image" src="https://github.com/user-attachments/assets/a2176e70-f1ef-4d34-8880-80431fb6f3fc" />

</p>
Step 6-9:
</p>
<p>
In steps 6-9, I configure IP addresses on all Distribution switches. I assign IPs on the neccessary interfaces to make sure they can route traffic porperly. I also set up loopback interfaces, which helps with network management and routing protocols by remaining active and accessible. 
</p>
<img width="422" alt="image" src="https://github.com/user-attachments/assets/3ed23e6c-292b-43f7-bbcb-5cb3e2f67605" />

</p>
Step 10:
</p>
<p>
In this step, I configure SRV1's IP settings via the GUI. I assign it a default gateway, an IP address and a subnet mask. 
</p>
<img width="208" alt="image" src="https://github.com/user-attachments/assets/f5d980d9-3e98-4634-ba1a-b89ea7677fa8" />
<img width="533" alt="image" src="https://github.com/user-attachments/assets/a004f5ea-38d2-41ea-81e5-33fd4b2a8190" />

</p>
Step 11:
</p>
<p>
In this step, I configure IPs on VLAN 99 as it is used for management. I set their default gateway to the first usable IP in their subnet to allow proper routing
</p>
<img width="329" alt="image" src="https://github.com/user-attachments/assets/ae421143-5239-4f71-8f43-646dd9062bba" />

</p>
Step 12-15:
</p>
<p>
In these steps, I configure Hot Standby Router Protocol (HSRPv2) on VLANS 99, 10, 20, 40 in Office A. HSRP is used to provide redundancy, ensuring that another router takes over in case one fails. I then set up Virtual IP addresses (VIPs) for each VLAN in Offices A and B, with one router acting as the primary and the other as backup. One router, or layer 3 switch, is elected as the "Active" router, which responds to traffic sent to the VIP. As the name suggests, the "Standby" router is on standby in case the active router fails. Hosts use the VIP as their default gateway, so they don't need to change their settings if a failure occurs. I also adjust the router priorty and enabled preemption, so the preferred router takes over automatically if it recovers from failure. Preemption allows a router with a higher priority to take over as the Active router when it comes online, even if another router is already active. 
</p>
<img width="295" alt="image" src="https://github.com/user-attachments/assets/19e6002c-66e0-46f5-8e16-5127b53834c4" />

</p>
Step 16-19:
</p>
<p>
In these steps, I configure similar settings for VLANs 99, 10, 20, 30 for Office B. 
</p>
<img width="245" alt="image" src="https://github.com/user-attachments/assets/e474ea1c-4136-4048-ae34-1a87628c154f" />

</p>
<h2>Part 4 – Rapid Spanning Tree Protocol </h2>

<p>
<img width="639" alt="image" src="https://github.com/user-attachments/assets/8d382166-d67c-4294-ab34-757382d826d9" />

</p>
Step 1:
</p>
<p>
In this step, I configure Rapid Per-VLAN Spanning Tree Plus(PVST+) on all Access and Distribution switches. Rapid PVST+ is a spanning tree protocol that creates a separate loop-free path for each VLAN, helping the network adjust quickly and manage traffic better. In Office A, I configure DSW-A1 as the Root Bridge for VLANs 99 and 10. On DSW-A2, I set it as the Root Bridge for VLANs 20 and 40. The same applies in Office B with VLAN 30 replacing VLAN 40. The task asks to configure the lowest possible STP priority, so I set it to priority 0. 
</p>
I then set the HSRP STandby Router to have an STP priority one increment higher than the Root Bridge, which will be 4096. If the active router or Root Bridge fails, this standby switch will take over, keeping the netwrok stable without major disruptions.
</p>
<img width="367" alt="image" src="https://github.com/user-attachments/assets/6fd439db-dde2-4663-b04a-fc2ffaac21e8" />

![Part 4, Step 1](https://github.com/user-attachments/assets/270798cd-5a9c-4b44-a1a4-101e45f9a106)



</p>
Step 2:
</p>
</p>
On all ports connected to end hosts, Access switches and WLC1, I enable PortFast and BPDU Guard. PortFast allows the ports to skip the STP listening and learning states and immediately transition to the forwarding state. This helps devices connect quickly without delays, which is especially useful for PCs, printers, and acess points. BPDU Guard prevents accidental network loops by disabling any port that recives a BPDU. If a switch is mistakenly plugged into an access port, BPDU Guard will shut down that port to protect the network. 
</p>
This configuration improves network efficiency, reduces downtime, and prevents spanning tree loops.
</p>
</p>
Notice in the screenshot below that I ran into an issue enabling PortFast on interface F0/2. Interface F0/2 is a trunk port because it is connected to WLC1. To solve this problem, we enter the command "Spanning-tree portfast trunk". This command will enable PortFast on the interface even in trunk mode.
</p>


<img width="330" alt="image" src="https://github.com/user-attachments/assets/b0414806-a2c0-4866-b14d-6723af65172a" />

![Part 4, Step 2](https://github.com/user-attachments/assets/9c7cdb96-59c4-4036-8e82-f9572119a915)


<br />
</p>
<h2>Part 5 – Static and Dynamic Routing </h2>
</p>
</p>
<img width="638" alt="image" src="https://github.com/user-attachments/assets/0f9d02d1-3b8e-474b-92a7-26f02bdf757d" />

</p>
Step 1:
</p>
<p>
In this first part, I configured Open Shortest Path First(OSPF) on R1's LAN-facing interfaces and on all Layer-3 switches (Core and Distribution switches). OSPF is a link-state routing protocol that dynamically exchanges routing information and calculates the best path to a destination. I ensured all devices were in Area 0, the backbone area. On R1, I set OSPF with Process ID 1 and assigned it a Router ID of 10.0.0.76, which is the loopback interface IP. Next, I set the loopback interface as passive to prevent OSPF Hello packets from being sent out. I then enabled OSPF on the loopback and physical interfaces. Setting the network type to point-to-point prevents uncecessary Designated Router (DR0 and Backup Designated Router (BDR) elections on direct links. 
</p>
For CSW1 and CSW2, I configured OSPF with Process ID 1 and assigned a Router ID for each switch. I then set the loopback interfaces as passive since they don't need to form OSPF adjacencies. Next, I sed the "network" command to specify excatly which interfaces should participate in OSPF. Thw wildcard 0.0.0.0 ensures OSPF runs only on the specified interface. On both switches, I configured OSPF for the physical interfaces and set the network type to point-to-point. 
</p>
</p>
For the Distribution switches, we configure OSPF with Process ID 1 and assign a Router ID. I set loopback interfaces and VLAN SVIs (except VLAN 99) as passive, preventing OSPF Hello messages on these interfaces. I then configured OSPF for the necessary interfaces using the "network" command. I also ensured the physical interfaces connecting to OSPF neighbors were set to point-to-point. This prevents the unnecessary election of DR/BDRs in OSPF.
</p>
<img width="340" alt="image" src="https://github.com/user-attachments/assets/03db3797-3972-49d8-a7df-4275c7143277" />
<img width="300" alt="image" src="https://github.com/user-attachments/assets/a74798d5-7e01-45c8-aa08-ae69e5a0c6e6" />

</p>
Step 2:
</p>
</p>
In this part, I configure static routes on R1's Internet connections, pointing to different next-hop IPs. I set one of the next-hop IPs to 203.0.113.1, which is the ISP's address. I configure the second next-hop IP of 203.0.113.5 with an Administrative Distance of 2, making it a floating static route. This is a backup incase the primary fails. I used the command "Do show ip route" to verify that only 1 is active in the routing table. 
</p>
</p>
Next, I set R1 as an OSPF ASBR (Autonomous System Boundary Router) to advertise its default route to other routers in the OSPF domain. This is to ensure that all OSPF routers recive the default route and can foward internet-bounfd traffic to R1. I confirm this has been set by sending a ping command to R1's internet IP at 203.0.113.2. If I try to ping the IPs IP, as shown in the screenshot, I get five "U"s, meaning unreachable. To solve this, we need to configure NAT (Network Address Translation). 
</p>
<img width="302" alt="image" src="https://github.com/user-attachments/assets/ad580949-43b9-4c14-9e5a-39405a5949d9" />
<img width="516" alt="Part 5, Step 2B" src="https://github.com/user-attachments/assets/32afa90a-d00f-4eb7-b7b0-080f579acbf5" />
</p>
<h2>Part 6 - Network Services: DHCP, DNS, NTP, SNMP, Syslog, FTP, SSH, NAT </h2>
</p>
<p>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
