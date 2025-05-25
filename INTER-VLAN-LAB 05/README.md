# 🖥️ Inter-VLAN Routing Lab Configuration and Description

# 🌐 Network Topology Overview

![Screenshot 2025-05-25 151145](https://github.com/user-attachments/assets/709e27b0-e816-45da-8454-4e6b8c85f7da)


Your lab consists of:

One Router (Router0)

One Switch (Switch0)

4 PCs in two VLANs:

VLAN 10: MANAGER

PC1 (192.168.1.10)

PC2 (192.168.1.11)

VLAN 20: ACCOUNTANT

PC3 (192.168.2.10)

PC4 (192.168.2.11)

# VLAN Details:

VLAN ID	Name	Subnet	Default Gateway
10	MANAGER	192.168.1.0/24	192.168.1.1
20	ACCOUNTANT	192.168.2.0/24	192.168.2.1

# 📋 Goals:

✅ Configure VLANs on the switch.

✅ Configure sub-interfaces (Router-on-a-Stick) on the router.

✅ Enable communication between VLANs.

✅ Verify connectivity via ping.

# 🔧 Router Configuration (Router0)

Step 1️⃣ Configure Sub-interfaces for VLANs:

enable

configure terminal

Configure the trunk interface (connecting to Switch0)

interface GigabitEthernet0/0

no shutdown

Sub-interface for VLAN 10 (MANAGER)

interface GigabitEthernet0/0.10

encapsulation dot1Q 10

ip address 192.168.1.1 255.255.255.0

exit

Sub-interface for VLAN 20 (ACCOUNTANT)

interface GigabitEthernet0/0.20

 encapsulation dot1Q 20
 
 ip address 192.168.2.1 255.255.255.0

exit

exit

# 🔧 Switch Configuration (Switch0)

Step 2️⃣ Create VLANs and Assign Ports:

enable

configure terminal

Create VLAN 10

vlan 10

 name MANAGER

exit

Create VLAN 20

vlan 20

 name ACCOUNTANT

exit

 Assign ports to VLANs

interface FastEthernet0/1

 switchport mode access
 
 switchport access vlan 10

exit

interface FastEthernet0/2

 switchport mode access
 
 switchport access vlan 10

exit

interface FastEthernet0/3

 switchport mode access
 
 switchport access vlan 20

exit


interface FastEthernet0/4

 switchport mode access
 
 switchport access vlan 20

exit


 Configure the trunk port (Router connection)

interface FastEthernet0/5

 switchport mode trunk

exit

exit

# 🖥️ PC Configuration

Manually assign IP addresses to each PC as follows:

PC	VLAN	IP Address	Subnet Mask	Default Gateway

PC1	VLAN 10	192.168.1.10	255.255.255.0	192.168.1.1

PC2	VLAN 10	192.168.1.11	255.255.255.0	192.168.1.1

PC3	VLAN 20	192.168.2.10	255.255.255.0	192.168.2.1

PC4	VLAN 20	192.168.2.11	255.255.255.0	192.168.2.1


# ✅ Testing and Verification

1️⃣ From PC1 (192.168.1.10), ping PC3 (192.168.2.10).

2️⃣ From PC2 (192.168.1.11), ping PC4 (192.168.2.11).

3️⃣ Ping the router's sub-interfaces (192.168.1.1 and 192.168.2.1) from any PC.


# 📌 Summary

Router0 → Configured with sub-interfaces for Inter-VLAN Routing (Router-on-a-Stick).

Switch0 → VLANs and trunk configured.

PCs → Static IPs assigned based on VLANs.

Result → VLANs can communicate via the router.
