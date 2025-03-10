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

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
