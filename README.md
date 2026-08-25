# Ex. No: 9 - Packet Tracer: Subnet an IPv4 Network
# Date: 25/08/2026
________________________________________ <br>
# Objective
Design, configure, and verify an IPv4 subnetting scheme in Cisco Packet Tracer.<br>
•	Subnet the 192.168.0.0/24 network into multiple subnets.<br>
•	Assign addresses to LAN-A, LAN-B, and future networks.<br>
•	Configure IP addressing on routers, switches, and PCs.<br>
•	Verify connectivity using ping and router show commands.<br>
________________________________________
# Apparatus / Tools Required
•	Cisco Packet Tracer<br>
•	CustomerRouter (2911 or equivalent)<br>
•	ISP Router<br>
•	2 Customer Switches (LAN-A Switch, LAN-B Switch)<br>
•	ISP Switch<br>
•	2 PCs (PC-A, PC-B)<br>
•	ISP Workstation and ISP Server<br>
•	Copper straight-through cables for LAN links<br>
•	Serial DCE/DTE cable for WAN link<br>
________________________________________<br>
# Network Topology Diagram
(Insert your Packet Tracer screenshot showing CustomerRouter → LAN-A Switch → PC-A, CustomerRouter → LAN-B Switch → PC-B, and ISP side with Router, Switch, Workstation, Server, and Serial link.)<br>
________________________________________<br>
# Addressing Table
Device	Interface	IP Address	Subnet Mask	Default Gateway<br>
CustomerRouter	G0/0	(1st host of LAN-A subnet)	(Subnet mask)	N/A<br>
CustomerRouter	G0/1	(1st host of LAN-B subnet)	(Subnet mask)	N/A<br>
CustomerRouter	S0/1/0	209.165.201.2	255.255.255.252	N/A<br>
LAN-A Switch	VLAN1	(2nd host of LAN-A subnet)	(Subnet mask)	CustomerRouter G0/0<br>
LAN-B Switch	VLAN1	(2nd host of LAN-B subnet)	(Subnet mask)	CustomerRouter G0/1<br>
PC-A	NIC	(Last host of LAN-A subnet)	(Subnet mask)	CustomerRouter G0/0<br>
PC-B	NIC	(Last host of LAN-B subnet)	(Subnet mask)	CustomerRouter G0/1<br>
ISP Router	G0/0	209.165.200.225	255.255.255.224	N/A<br>
ISP Router	S0/1/0	209.165.201.1	255.255.255.252	N/A<br>
ISP Switch	VLAN1	209.165.200.226	255.255.255.224	209.165.200.225<br>
ISP Workstation	NIC	209.165.200.235	255.255.255.224	209.165.200.225<br>
ISP Server	NIC	209.165.200.240	255.255.255.224	209.165.200.225<br>
(LAN-A and LAN-B IPs to be filled in after subnetting calculation.)<br>
________________________________________<br>
# Procedure
# Part 1: Subnet the Assigned Network
1.	Start with 192.168.0.0/24.<br>
2.	Requirements:<br>
o	LAN-A: ≥50 hosts<br>
o	LAN-B: ≥40 hosts<br>
o	At least 2 unused subnets for future expansion.<br>
3.	Choose a subnet mask that supports both host requirements.<br>
o	Example: /26 (255.255.255.192) → 62 hosts per subnet, 4 subnets.
4.	Allocate:<br>
o	Subnet 1 → LAN-A<br>
o	Subnet 2 → LAN-B<br>
o	Subnets 3 & 4 → Reserved<br>
________________________________________<br>
# Part 2: Configure the Devices
CustomerRouter<br>
•	Set hostname: hostname CustomerRouter<br>
•	Passwords:<br>
o	enable secret Class123<br>
o	line console 0 → password Cisco123 → login<br>
•	Configure interfaces:<br>
•	interface g0/0  <br>
•	 ip address <LAN-A first host> <mask>  
•	 no shutdown  
•	interface g0/1  
•	 ip address <LAN-B first host> <mask>  <br>
•	 no shutdown  <br>
•	interface s0/1/0  <br>
•	 ip address 209.165.201.2 255.255.255.252  <br>
•	 clock rate 64000   ← DCE end  <br>
•	 no shutdown  <br>
•	Save: copy running-config startup-configv
Switches (LAN-A, LAN-B)<br>
•	VLAN1 IP: 2nd host of subnet<br>
•	Default gateway: Router G0/0 or G0/1<br>
PCs (PC-A, PC-B)<br>
•	Last host of subnet<br>
•	Subnet mask and gateway configured<br>
________________________________________<br>
# Part 3: Verification & Testing
1.	On routers:<br>
o	show ip interface brief (check status up/up)<br>
o	show ip route (verify connected subnets)<br>
2.	On PCs:<br>
o	Ping default gateway<br>
o	Ping across subnets (PC-A ↔ PC-B)<br>
o	Ping ISP Server<br>
________________________________________<br>
# Commands Used (Summary)
•	Mode/navigation: enable, configure terminal, end<br>
•	Interface config: interface g0/0, ip address, no shutdown<br>
•	Show/verify: show ip interface brief, show ip route<br>
•	Save: copy running-config startup-config<br>
________________________________________<br>
# Output (Attach Screenshots)

<img width="1916" height="1015" alt="Screenshot 2026-08-25 135614" src="https://github.com/user-attachments/assets/c92c6302-7f46-47dd-b750-4e8f7861c195" />

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/5dca9147-8d00-47ea-b697-e8176a4064a6" />

<img width="1917" height="1015" alt="Screenshot 2026-08-25 140346" src="https://github.com/user-attachments/assets/8fa371ed-b51c-41fc-9fa8-f873f3329614" />

<img width="1916" height="1003" alt="Screenshot 2026-08-25 140400" src="https://github.com/user-attachments/assets/f99c1518-562c-40b9-8ae3-c9cd93c786b8" />

<img width="1915" height="1016" alt="Screenshot 2026-08-25 135442" src="https://github.com/user-attachments/assets/70ec8a35-d76b-4bea-9454-cc1435996483" />

<img width="1917" height="1017" alt="Screenshot 2026-08-25 140419" src="https://github.com/user-attachments/assets/c0e040b3-a13b-461f-ac36-f17b73733143" />

<img width="1917" height="1017" alt="Screenshot 2026-08-25 140437" src="https://github.com/user-attachments/assets/94ae00e0-c301-487b-be39-b58848c3956e" />

<img width="1917" height="1020" alt="Screenshot 2026-08-25 140515" src="https://github.com/user-attachments/assets/895c8c00-c43a-41ff-842b-ad66a362b3b9" />

<img width="1917" height="1020" alt="Screenshot 2026-08-25 140612" src="https://github.com/user-attachments/assets/d1a02d42-b3d5-4ee1-8cfa-1d819c6d5c89" />

________________________________________<br>
# Result
The IPv4 subnetting scheme was successfully designed and implemented. Router, switches, and PCs were configured with correct addressing. Connectivity within LANs, across subnets, and to ISP devices was verified using ping and show commands.<br>

