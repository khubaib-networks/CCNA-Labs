
# Port Security on Cisco Switches - Lab Setup

Welcome to this simple lab designed to help students and networking enthusiasts understand **Port Security** on Cisco switches using Cisco Packet Tracer or a similar network simulator.

## 📷 Network Topology

<img width="479" alt="toplogy pic" src="https://github.com/user-attachments/assets/0566cf91-a4e7-4ab8-a127-3c524181f4b0" />


This topology consists of:

- 1 Switch (S1)

- 4 PCs (PC0, PC1, PC2, PC3)

- All PCs are connected to FastEthernet ports Fa0/1 to Fa0/4 of the switch.

## 🛠️ Objective

To implement **Port Security** on the switch so that:

- Each port only allows **one MAC address** (the one that is first connected).

- Sticky MAC addresses are used (the switch dynamically learns and saves the MAC addresses).

- If a violation occurs (another device is plugged in), the port will **restrict** access and **log** the violation without shutting down the port.

## 🧾 Switch Configuration Commands

Below are the exact configuration steps used on the switch:

Switch> enable

Switch# configure terminal

Switch(config)# hostname S1

S1(config)# interface range fa0/1 - 4

S1(config-if-range)# switchport mode access

S1(config-if-range)# switchport port-security

S1(config-if-range)# switchport port-security mac-address sticky

S1(config-if-range)# switchport port-security maximum 1

S1(config-if-range)# switchport port-security violation restrict

S1(config-if-range)# no shutdown

S1(config-if-range)# end

S1# write


## 🔒 How Port Security Works Here

- **Sticky MAC**: Learns the first MAC address seen on the port and saves it.

- **Maximum 1**: Limits each port to one MAC address only.

- **Violation mode "restrict"**: If an unauthorized device connects, the switch will:

  - Drop packets from that device

  - Send a log message (syslog if enabled)

  - Keep the port up (unlike shutdown mode)

## 🧑‍🎓 Who This Lab Is For

This lab is perfect for:

- CCNA students

- Beginners practicing Cisco CLI

- Anyone learning about switch-level security features


## 📂 Files Included

- `toplogy pic.png` – Topology diagram

- Configuration steps (see above or replicate in Packet Tracer)

- Packet Tracer `.pkt` file (add it to your repo if available)

## ✅ How to Use

1. Open the topology in Cisco Packet Tracer.

2. Apply the switch configuration manually or use the `.pkt` file if provided.

3. Test by changing the connected PC or its MAC address and observe how the switch restricts the port.


**Author**: Khubaib Jahangir  

**License**: MIT

> If you found this helpful, don't forget to ⭐ the repo and share it with your fellow learners!

