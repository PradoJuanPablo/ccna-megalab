<p align="center">
<img width="500" alt="image" src="https://conceptodefinicion.de/wp-content/uploads/2014/06/ccna.jpg">
</p>

<h1>Complete Network Configuration </h1>
This "CCNA Mega Lab" tutorial by Jeremy’s IT Lab is a hands-on walk thorugh that teaches how to configure a complete network using VLANs, OSPF, STP, DHCP, security, and wireless.<br />


<h2>Video Demonstration</h2>

- ### YouTube: CCNA Mega Lab:[([https://www.youtube.com/watch?v=2p7-MluKAgE])](https://www.youtube.com/watch?v=2p7-MluKAgE)

<h2>Environments and Materials Used</h2>

- Cisco Packet Tracer
- CCNA Mega Lab file:
https://jitl.jp/mega-lab
- My Configuration Notes: [file:///E:/Packet%20Tracer/Mega%20Lab%20Configurations.pdf](https://drive.google.com/file/d/1eSZKhLcuARCgp5TSkYzJEfVhpWAOUlXD/view?usp=sharing)
  


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
<img width="804" alt="image" src="https://github.com/user-attachments/assets/6ad88d33-5d7b-4e59-9ac5-5e19e98454af" />
<img width="945" alt="image" src="https://github.com/user-attachments/assets/7aecf860-77bd-4869-b7e5-8ec61084a840" />
</p>
Step 1:
</p>
</p>
In this step, I first excluded the first 10 usable IP addresses in each pool to prevent them from being assigned to clients. I then created DHCP pools for different network segments (Management, PCs, Phones, Wi-Fi). Next, I assigned network parameters to each pool, meaning the default gateway, domain name, DNS server, and WLC when needed.
</p>
<img width="323" alt="image" src="https://github.com/user-attachments/assets/d792cd79-9c9d-45c1-830b-2fa18ad6cd0e" />
</p>
Step 2:
</p>
</p>
In the second step, I configure the Distribution switches to forward DHCP requests to R1. I use the DHCP Relay agent (ip helper-address) to allow DHCP clients to get an IP from the DHCP server. To test, I enter into the COmmand Prompt on PC1 and type "ipconfig /renew" to send a DHCP Discover packet and retrieve an IP address. I also get some successful ping replies from R1's loopback and Internet interfaces.

</p>
<img width="256" alt="image" src="https://github.com/user-attachments/assets/b0ccbec0-8dd4-4d53-95a7-0b94aa78ad29" />
<img width="578" alt="Part 6, Step 2" src="https://github.com/user-attachments/assets/7adaf10c-d373-4bb3-8092-226d57752346" />
</p>
Step 3:
</p>
</p>
In this step, I enabled DNS on SRV1 and added entries for Google.com, Youtube.com and Jeremysitlab.com. I also set a CNAME record to map an alias, www.jeremysitlab.com to the domain jeremysitlab.com
</p>
<img width="487" alt="image" src="https://github.com/user-attachments/assets/43d2d86b-964f-4f01-94a4-1991e99a28a1" />

<img width="456" alt="Part 6, Step 3" src="https://github.com/user-attachments/assets/6693fca0-dc96-4c3e-b1c6-f496384d9984" />
</p>
Step 4:
</p>
</p>
In step 4, I configure all devices to use the domain name jeremysitlab.com and set SRV1 as the DNS Server. 

</p>
<img width="234" alt="image" src="https://github.com/user-attachments/assets/73369ef9-a1c5-4156-b39d-3a0c6ce31561" />
</p>
Step 5:
</p>
</p>
In this step, I set R1 as an NTP (Network Time Protocol) server. NTP is used to synchronize time across devices. I then sync R1 to an external NTP server using the IP 216.239.35.0.
</p>
<img width="226" alt="image" src="https://github.com/user-attachments/assets/cd96558b-3f4d-4a76-acb5-b84c4b477450" />
</p>
Step 6:
</p>
</p>
In this step, I configure NTP authentication on all switches. I first set authentication key 1 (ccna) on R1. On the switches, I set R1 as the NTP server. Using these commands ensures that the devices trust R1 as the time source. 
</p>
<img width="319" alt="image" src="https://github.com/user-attachments/assets/f071691b-ff3a-46ba-b496-50ef635daa77" />
</p>
Step 7-8:
</p>
</p>
In steps 7 and 8, I configure Simple Network Management Protocol (SNMP) and Syslog. SNMP is a protocol used to monitor and manage network devices like router, switches, and servers. It allows network admins to collect performance data, alerts, and configure devices remotely. Syslog is a log collection system used to store and manage event messages from network devices. Admins can use this information to troubleshoot issues or detect security threats. 
</p>
I configure SNMP with read-only (RO) access. Syslog messages get sent to SRV1. I use the command "logging trap debugging" to ensure that messages of all severity level are sent. I then enable logging to the buffer, which is stored in local memory on the device. 
</p>
</p>
To ensure the configures are complete and accurate I enter the command "do show logging" and confirm the commands are enabled.

</p>
</p>
<img width="288" alt="image" src="https://github.com/user-attachments/assets/0b83465a-8f17-48d9-889a-a89f6776e4a9" />

![Part 6, Steps 7-8](https://github.com/user-attachments/assets/dc6d73f6-6700-41a0-b9ef-db761e031168)
</p>
Step 9:
</p>
</p>
In this step, I use FTP on R1 to upgrade its IOS version. I first set FTP credentials, Transferred the new IOS via FTP from SRV1, and then configured R1 to boot from the new IOS file.
</p>
</p>
I confirmed a successful upgrade using the command "do show version". Lastly, I delete the previous IOS version. 
</p>
<img width="524" alt="image" src="https://github.com/user-attachments/assets/f3b7ad9c-7677-42ed-a33c-a00f886297a6" />

![Part 6, Step 9](https://github.com/user-attachments/assets/c5bf42d4-e89a-4060-9a2c-2225fe99bd11)
</p>
Step 10:
</p>
</p>
In this step, I configure SSH for secure remote access to all routers and switches. I first generate 4096-bit RSA keys. I then enable SSHv2 only. Next, I used an Access Control List (ACL) to restrict SSH to Office A's PCs. I also disable the use of Telnet since it is unsecure. Additionally, I configure a local account which will be required for users to log in with when connecting via SSH. I set these commands on all devices. 
</p>
Lastly, I confirm a successful ssh login from PC1, located in Office A
</p>
<img width="325" alt="image" src="https://github.com/user-attachments/assets/43389541-1fc5-4ddb-8649-aa3297d57bef" />
<img width="697" alt="Part 6, Step 10" src="https://github.com/user-attachments/assets/3d44df45-07ec-4902-b47b-39bdc10099ff" />
</p>
Steps 11-12:
</p>
In these steps, I configure NAT (Network Address Translation). NAT allows internal devices to communicate with external networks. 
</p>
I first set Static NAT on R1 to enable hosts to access SRV1 via IP 203.0.113.113. I then configure the interfaces G0/0/0 and G0/1/0 as outside interfaces as they are connected to the internet. I set G0/0 and G0/1 as inside interfaces as they are connected to CSW1 and CSW2. 
</p>
Next I configure dynamic PAT (Port Address Translation) to allow hosts in Office's A and B to access the internet. I first permit Office A's PCs subnet using the command "access-list 2 permit 10.1.0.0 0.0.0.255". I do this same command for the other subnets. The wildcard 0.0.0.255 means that only the last octet varies. I then define the NAT Pool (POOL1) assigning 8 public IPs between 203.0.113.200 - 203.0.113.207. The subnet mask /29 supports 6 usable addresses, as two are reserved for network and broadcast. After, I map ACL 2 to POOL1 and enable PAT. The overload keyword allows multiple internal devices to share a single public IP by using different port numbers. Now, hosts in the specified subnets can access the internet using addresses from POOL1. I confirm hosts can access the internet by pining jeremysitlab.com from PC1.
</p>
I then verify Internet Link Failover works by removing and re-configuring the OSPF default-information originate command. I confirm this by entering the command "do show ip route" and we can see that R1's default route has an AD of 2, which is the floating route I configured earlier in the lab. I then try to ping jeremysitlab.com from PC1 and it is still successful. Lastly, I re-enable G0/0/0 and remove and re-configure default-information originate. 
</p>
<img width="573" alt="image" src="https://github.com/user-attachments/assets/ab661b55-77cf-4827-861c-7945dccd10ab" />
<img width="354" alt="Part 6, step 12" src="https://github.com/user-attachments/assets/70cea337-6dac-4a60-a097-ce77090e8c92" />

![Part 6, Step 12-D](https://github.com/user-attachments/assets/93c749ab-1f3d-4bb3-92ca-88617c4e4df1)
</p>
Step 13:
</p>
Lastly, I disable CDP (Cisco Discovery Protocol) and enable LLDP (Link Layer Discovery Protocol) on all switches. Both these protocols are used for network discovery that help devices identify and share information about directly connected neighbors.

</p>
<img width="331" alt="image" src="https://github.com/user-attachments/assets/9048a4ec-b8c2-4fe0-abf1-dee7c9f28235" />
</p>
<h2>Part Part 7 – Security: ACLs and Layer-2 Security Features </h2>
<p>
<img width="635" alt="image" src="https://github.com/user-attachments/assets/ce2f8d4b-3797-4faf-a61a-5289aa27bf89" />

</p>

</p>
Step 1:
</p>
</p>
Part 7 is focused on security. In this first step, I created an extended Access Control List (ACL) called OfficeA_to_OfficeB on both DSW-A1 and DSW-A2 to control traffice between the two offices. I allow ICMP traffic, which is used by ping and tracert commands and is used to troubleshoot networks. I then block all other traffic from Office A to Office B. Next, I allow all other traffic that's not explicitly denied, this is to prevent accidently blocking unintended traffic. After, I applied an ACL on VLAN 10, ensuring filtering happens as close to the source as possible.
</p>
<img width="400" alt="image" src="https://github.com/user-attachments/assets/be72bc2e-e6db-40a1-99ed-a617b98e9865" />
</p>
Step 2:
</p>
In this step, I enable port security on F0/1 for all access swicthes to restrict MAC addresses and prevent unauthorized devices from connecting. On switches ASW-A2, ASW-A3, and ASW-B2 I allow for two MAC addresses as each phone and PC will need one as well. The command "switchport port-security mac-address sticky" automatically learn the first connected MAC address and saves them. The command "switchport port-security violation restrict" blocks unauthorized MAC addresses without shutting down the port. 
</p>
<img width="321" alt="image" src="https://github.com/user-attachments/assets/f7d50947-b263-4cf0-9184-9bcc5154bea9" />
</p>
Step 3:
</p>
In this step, I configure DHCP Snooping to prevent rogue DHCP servers and DHCP-based attacks. I first enable DHCP Snooping globally and then enable it on specific VLANs. I then disable Option 82 insertion to avoid DHCP relay issues. I also set uplink ports on interface G0/1-2 as trusted so they forwars DHCP replies. Next, I limit DHCP requests to 15 per second to prevent DHCP Starvation attacks. On ASW-A1, I increase the rate for the Wireless LAN Controller (WLC1) since Wi-Fi clients generate a lot of DHCP requests.  
</p>
<img width="311" alt="image" src="https://github.com/user-attachments/assets/076f11a6-e98d-41a2-985c-7c2706abd7dc" />

</p>
Step 4:
</p>
In this last step, I enable Dynamic ARP Inspection (DAI) to prevent ARP spoofing attacks. First, I enable ARP Inspection on the specific VLANs. Then I enable validation checks for source and destination MAC addresses as well as IP. Lastly, I set uplink ports on interfaces G0/1-2 as trusted so they can forward valid ARP messages. This configuration ensures that devices cannot falsely claim another's IP. 
</p>
<img width="323" alt="image" src="https://github.com/user-attachments/assets/923f2dbd-3ff0-496d-a80d-cde0556be268" />

</p>
<h2>Part 8 – IPv6 </h2>
<img width="638" alt="image" src="https://github.com/user-attachments/assets/af42c18e-0866-4174-bbc4-7c266857edd1" />

<p>
</p>
Step 1:
</p>
This part is all on IPv6. I first enable IPv6 unicast routing on R1, CSW1 and CSW2 so that the devices can forward IPv6 traffic. 
</p>
On R1, I assign an IPv6 addresses to interfaces G0/0/0, G0/1/0, G0/0, and G0/1. For the G0/0 and G0/1 interfaces, I used EUI-64 to generate the interface ID dynamically. The interface ID is automatically derived from the MAC address. 
</p>
On CSW1 and CSW2, the commands are the same except for assigning different IPv6 addresses. For Port-Channel 1, I configure IPv6 without assigning a specific address. This allows IPv6 communication without explicitly configuring an address. 
</p>
Lastly, I verify a correct configuration using the command "do show ipv6 interface brief. For R1, I can see the four interfaces that I configured, each with a link local address and the global unicast address. On the screenshot for CSW2, we see that for Port-Channel 1, enabling IPv6 with the "ipv6 enable" command automatically generates a link local address. 
</p>
<img width="322" alt="image" src="https://github.com/user-attachments/assets/474710e3-5645-482e-a3b1-232757784e66" />
<img width="775" alt="Part 8, step 1" src="https://github.com/user-attachments/assets/e656baae-d596-4c81-91f9-2fbe317819fb" />
<img width="740" alt="Part 8, step 1-E" src="https://github.com/user-attachments/assets/b6d3cda5-0c2c-498e-a92a-d6e748475729" />
</p>
Step 2:
</p>
In this step, I configure two default static routes on R1. The first step is to set up a recursive route, meaning it should only specify the next hop IP address. The next route has to be fully specified, meaning it should specify the exit interface of G0/1/0 and the next hop IP address of 2001:db8:b::1. I set the Administratice distance to 2, which is higher than the default of 1, making it a floating route which will be used if the primary fails. 
</p>
<img width="350" alt="image" src="https://github.com/user-attachments/assets/93553a0b-fe81-43d6-bca1-3ac3fb6f9542" />

</p>
<h2>Part 9 – Wireless  </h2>
<img width="635" alt="image" src="https://github.com/user-attachments/assets/26314533-616d-408c-9a24-09a6f4086167" />

<p>
</p>
Step 1:
</p>
In this last section, I will conifigure a wireless LAN using the GUI of WLC1. I first checked connectivity by using the ping command to ensure that PC1 can reach WLC1 with the IP of 10.0.0.7. Once I confirmed connectivity I went to the Web Broswer and entered the URL: https://10.0.0.7. I log in using the credentials provided (Username: admin, Password: adminPW12). 
</p>

![image](https://github.com/user-attachments/assets/f9ec1e55-8e1b-4d52-b325-fa51dce97aa0)


</p>
Step 2:
</p>
In the next step, I create a dynamic interface for Wi-Fi WLAN. A dynamic interface is used for wireless VLANS, allowing traffic segmentation. First, I navigate to the Controller tab and then to Interfaces. I then select New to create a new interface. I then enter in the following details: Interface Name: Wi-Fi, VLAN ID: 40. After I hit Apply. Next, I set the physical and logical information. I set the Port NUmber to 1, the IP address to 10.6.0.2, the Netmask of 255.255.255.0 and the Gateway to 10.6.0.1. Lastly, I enter in the Primary DHCP Server of 10.0.0.76 and hit Apply
</p>

![image](https://github.com/user-attachments/assets/05e3d70a-5895-4288-b048-5e08f5089376)

<img width="600" alt="Part 9, step 2" src="https://github.com/user-attachments/assets/d3bc3f9d-1eae-4f39-8795-2fc52c5b5b96" />

</p>
Step 3:
</p>
After I create the dynamic interface, I create the Wi-Fi network (SSID). I navigate to the WLAN tab and select Go. From there I create a WI-Fi profile with the SSID of Wi-Fi and the ID of 1. I then checked the "Enabled" box for Status and assigned Wi-Fi as the interface. Next, I navigate to the Security tab and then to Layer 2 Security and enter in WPA+WPA2. After, I check the box for "WPA2 Policy". Under Authentication Key Management, I check the box for "PSK" and enter in the password of "cisco123" for PSK Format. Lastly, I hit apply and hit "Save configuration"
</p>

![image](https://github.com/user-attachments/assets/79f6339a-6f7d-4811-bb83-332a60eb20a4)
<img width="691" alt="Part 9, Step 3" src="https://github.com/user-attachments/assets/296cb9a5-931d-4c62-9e6f-8f49f7f6d253" />

</p>
Step 4:
</p>
In this last part, I check that both Lightweight Access Points (LWAP) connect to WLC1. Due to Packet Tracer's limitations, clients won't be able to get DHCP leases, but the APs should still register. I access Laptop 1 and from there navigate to the Config tab and then to Wireless0. There, I set the SSID of Wi-Fi, set the authentication to WPA2-PSK and enter in the passphrase of cisco123. I then ensure that the encryption type is set to AES. 
</p>

![image](https://github.com/user-attachments/assets/412a4feb-923b-4667-a99c-ece6720c5e8f)
![Part 9, Step 4](https://github.com/user-attachments/assets/c553b2a9-ae9c-4d68-b887-14059faaee39)

</p>
This is the end of the lab! Thank you for taking the time to go through this lab with me! 
</p>
<br />
