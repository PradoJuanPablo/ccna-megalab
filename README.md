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
<img <img width="373" alt="image" src="https://github.com/user-attachments/assets/dc299ee8-d309-46a8-834e-ea1657e68390" />
  
</p>
<p>
In this first step I am adding a basic configuration to each router and switch. This includes creating a local user account and enabling encryption. I also set idle sessions to be logged out after 30 minutes. This ensures that only authorized users can access and make changes to the devices
</p>
<br />

<h2>Part 2 - VLANs, L2 EtherChannel </h2>

<p>
<img <img width="476" alt="image" src="https://github.com/user-attachments/assets/0f625279-93a6-4c20-af89-3e0f8f996e6b"/>
<img <img width="258" alt="image" src="https://github.com/user-attachments/assets/c07634ac-85a8-4ca3-97c1-85236fe61921"/>
<img <img width="299" alt="image" src="https://github.com/user-attachments/assets/2065611e-ef4a-4f4f-903a-1fa721c4e947"/>

</p>
<p>

Part 2, Step 1:
<p>
In the first section, it mentions to configure an EtherChannel using a Cisco-proprietary protocol. For this, we will use Port Aggregation Protocol (PAgP) between DSW-A1 and DSW-A2. PAgP is used to automatically combine multiple physical links into a single logical link, called EtherChannel. This helps increase bandwidth and provides redundancy. It operates in 2 modes: Desireable and Auto. Desireable mode tries to actively form an EtherChannel with the other device. Auto mode waits for the other device to initiate the EtherChannel but won't start it itself. For PAgP to work, one side has to be Desirable.

<img width="251" alt="image" src="https://github.com/user-attachments/assets/583b0828-ecd8-4561-b1f5-2545f371d3a7"/>
</p>

Part 2, Step 2:
<p>
  fsfsf
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
