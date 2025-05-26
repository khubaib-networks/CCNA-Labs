
# 📚 NAT Static Lab Configuration & Description

# 🌐 Network Topology Overview

# <img width="469" alt="NAT STATIC TOPLOGY" src="https://github.com/user-attachments/assets/874f7cec-a33f-4526-8deb-92ac5e55a3b5" />



topology consists of:

Two Routers (Router0 and Router1)

Two Switches (Switch0 and Switch1)

Two Hosts:

PC0 (Client PC in LAN 192.168.1.0/24)

Server0 (Web Server in LAN 192.168.3.0/24)

Public Network: 200.10.10.0/30

Network Breakdown

Device	Interface	IP Address	Role

Router0	Fa0/0	192.168.1.1	LAN Gateway (PC0)


Router0	Fa0/1	200.10.10.1	Public Network

Router1	Fa0/0	192.168.3.1	LAN Gateway (Server)

Router1	Fa0/1	200.10.10.2	Public Network

PC0	Fa0	192.168.1.2	Client PC

Server0	Fa0	192.168.3.2	Web Server

# 🎯 Lab Objectives

✅ Configure Static NAT on Router0 to translate PC0's private IP to a public IP (200.10.10.1).

✅ Allow communication between the internal LAN (192.168.1.0/24) and external network (Server LAN 192.168.3.0/24).

✅ Verify static NAT translation using show ip nat translations.

# 🔧 Router0 Configuration (NAT Configuration)

Step 1️⃣ Basic Interface Configuration

enable

configure terminal

Configure inside interface (LAN side)

interface FastEthernet0/0

 ip address 192.168.1.1 255.255.255.0
 
 ip nat inside
 
 no shutdown

exit

Configure outside interface (Public side)

interface FastEthernet0/1

 ip address 200.10.10.1 255.255.255.252
 
 ip nat outside
 
 no shutdown

exit

Step 2️⃣ Configure Static NAT on Router0

 Map inside local (PC0) to inside global (public)

ip nat inside source static 192.168.1.2 200.10.10.1

This means any packets from 192.168.1.2 will appear as 200.10.10.1 when going out.

# 🔧 Router1 Configuration (No NAT)

enable

configure terminal

 Configure inside interface (LAN side)

interface FastEthernet0/0

 ip address 192.168.3.1 255.255.255.0
 
 no shutdown

exit

Configure outside interface (Public side)

interface FastEthernet0/1

 ip address 200.10.10.2 255.255.255.252
 
 no shutdown

exit

# 🔧 PC & Server Configuration

Device	IP Address	Subnet Mask	Default Gateway

PC0	192.168.1.2	255.255.255.0	192.168.1.1

Server0	192.168.3.2	255.255.255.0	192.168.3.1

# 📊 NAT Verification Commands (Router0)

Run the following on Router0 to verify translations:

show ip nat translations

show ip nat statistics

Expected output after pings or traffic:


Pro Inside global   Inside local    Outside local  Outside global
--- 200.10.10.1     192.168.1.2     192.168.3.2    192.168.3.2

# 🧪 Testing Connectivity

✅ From PC0 (192.168.1.2):

Ping Server0 (192.168.3.2) → Successful ping via NAT.

✅ From Router0:

Use show ip nat translations to confirm NAT is working.

# 📌 Summary

Router0: Configured static NAT for PC0 (192.168.1.2) to be represented as 200.10.10.1.

Router1: Routes traffic between public and server LAN.

NAT Static enables one-to-one mapping of internal IP to public IP for external communication.

