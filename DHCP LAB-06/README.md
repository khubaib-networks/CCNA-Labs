# 🖥️ DHCP LAB CONFIGURATION AND DESCRIPTION


# 🌐 Network Topology

 ![Screenshot 2025-05-25 145944](https://github.com/user-attachments/assets/2f3dfad5-1420-419b-8ee1-5b5b95a46174)




Your network consists of:

Two Routers (Router0 and Router1)

Two Switches (Switch0 and Switch1)

6 PCs (PC0 - PC5)

Network Segments:

Network 192.168.1.0/24 (Left side)

Router0 (192.168.1.1)

PCs: PC0, PC1, PC2 (Get IPs via DHCP from Router0)

Network 192.168.2.0/24 (Right side)

Router1 (192.168.2.1)

PCs: PC3, PC4, PC5 (Get IPs via DHCP from Router1)

# 📋 Goals:

✅ Configure DHCP on both routers so PCs get IPs dynamically.

✅ PCs in each network should get IPs in their respective subnets.

✅ Test connectivity (ping between PCs and router interfaces).

# 🔧 Router Configuration:


Let's configure Router0 and Router1.

# 🔹 Router0 Configuration (192.168.1.1)
    
enable

configure terminal

Configure interface Fa0/0 (connected to Switch0)

interface FastEthernet0/0

 ip address 192.168.1.1 255.255.255.0
 
 no shutdown

exit

Configure DHCP for network 192.168.1.0/24

ip dhcp pool LAN1

 network 192.168.1.0 255.255.255.0
 
 default-router 192.168.1.1
 
 dns-server 8.8.8.8

 Exclude router's IP from DHCP pool

ip dhcp excluded-address 192.168.1.1

exit

# 🔹 Router1 Configuration (192.168.2.1)

enable

configure terminal


 Configure interface Fa0/1 (connected to Switch1)

interface FastEthernet0/1

 ip address 192.168.2.1 255.255.255.0
 
 no shutdown

exit

Configure DHCP for network 192.168.2.0/24

ip dhcp pool LAN2

 network 192.168.2.0 255.255.255.0
 
 default-router 192.168.2.1
 
 dns-server 8.8.8.8


 Exclude router's IP from DHCP pool

ip dhcp excluded-address 192.168.2.1

exit

# 📡 Switch Configuration (Switch0 and Switch1)

The switches are simple Layer 2 devices—no configuration required for DHCP. Just ensure all PCs are connected to their respective switches.

# 🖥️ PC Configuration

For each PC:

Go to Desktop tab.

Open IP Configuration.

Select DHCP.

They should receive IPs like:

PC0, PC1, PC2 → from 192.168.1.0/24 (Router0)

PC3, PC4, PC5 → from 192.168.2.0/24 (Router1)

# ✅ Testing and Verification

On each PC, open Command Prompt and test:

ping 192.168.1.1   (for PCs 0-2)

ping 192.168.2.1   (for PCs 3-5)

Check that they get DHCP addresses by running ipconfig on the PCs.

# 📌 Summary

Router0 → Provides DHCP for 192.168.1.0/24

Router1 → Provides DHCP for 192.168.2.0/24

Switches → Connect PCs to the network.

PCs → Set to DHCP to get automatic IPs.
