## 📚 Subnetting Lab

This lab demonstrates **Subnetting** in a multi-subnet topology using Cisco Packet Tracer.



### 🏗️ Topology Overview

![Subnetting Topology] ![Subnetting](https://github.com/user-attachments/assets/45853545-d8d9-49b6-8aa8-1a40c9bb7635)



### 🌐 IP Addressing Scheme

| Subnet   | Device        | Interface | IP Address      | Subnet Mask       |
|----------|---------------|-----------|-----------------|-------------------|
| Subnet 1 | Router (2911) | Gi0/0     | 192.168.10.1    | 255.255.255.0     |
| Subnet 1 | PCs           | Fa0       | 192.168.10.2-3  | 255.255.255.0     |
| Subnet 2 | Router (2911) | Gi0/1     | 192.168.10.132  | 255.255.255.0     |
| Subnet 2 | Switch (2960) | Fa0/4     | - (trunk)       | -                 |
| Subnet 2 | PCs           | Fa0       | 192.168.10.129-131 | 255.255.255.0  |



### 🔧 Configuration Code

Here’s the basic **Router configuration** for this topology:

#### Router (2911)

hostname Router

!
 
 interface GigabitEthernet0/0
 
 ip address 192.168.10.1 255.255.255.0
 
 no shutdown

!

interface GigabitEthernet0/1

 ip address 192.168.10.132 255.255.255.0
 
 no shutdown

!

ip route 192.168.10.0 255.255.255.0 GigabitEthernet0/0

ip route 192.168.10.128 255.255.255.0 GigabitEthernet0/1

Switch (2960)

hostname Switch1

!

interface range fa0/1 - 4

 switchport mode access
 
 switchport access vlan 10
!


vlan 10

 name Subnet2

PCs

PC Name	IP Address	Subnet Mask	Default Gateway

PC1	192.168.10.1	255.255.255.0	192.168.10.1

PC2	192.168.10.2	255.255.255.0	192.168.10.1

PC3	192.168.10.3	255.255.255.0	192.168.10.1

PC4	192.168.10.129	255.255.255.0	192.168.10.132

PC5	192.168.10.130	255.255.255.0	192.168.10.132

PC6	192.168.10.131	255.255.255.0	192.168.10.132


# 🚀 How to Use This Lab
 
 Clone this repository:

git clone [https://github.com/YOUR_USERNAME/CCNA-labs.git](https://lnkd.in/dYbuSBrT)

Open the Subnetting.pkt file in Cisco Packet Tracer.

Review the router and switch configurations.

Assign IP addresses to all PCs based on the table above.

Test connectivity by pinging PCs across the network.

Reference the topology image Screenshot 2025-05-28 145958.png for guidance.

# 📸 Topology Screenshot

![Subnetting](https://github.com/user-attachments/assets/9882c1f2-6e75-433b-afe2-a2a6d5a92851)


# 📚 Learning Outcomes

Practice Subnetting in a real-world network.

Configure routers and switches for inter-subnet communication.

Understand default gateways and IP addressing.

Build hands-on skills for CCNA Certification and troubleshooting.

# 📬 Contribute

Want to improve this lab or add new ones? Feel free to open a Pull Request or share feedback!

# 🌟 Stay Connected
This repository is a growing collection of labs—perfect for CCNA students and those looking to impress recruiters with practical networking skills!
