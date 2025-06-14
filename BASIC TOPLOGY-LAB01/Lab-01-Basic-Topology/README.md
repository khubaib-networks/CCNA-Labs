# Lab 01 - Basic Network Topology

This lab is designed to help beginners understand the fundamental structure of a simple LAN.

## 🧱 Topology Components
- 2 x End Devices (PC0, PC1)
- 1 x Switch (2960)
- 1 x Roter (2911)
- 2 x Copper Straight-through Cables

## 🧠 Learning Objectives
- Connect devices using correct cables
- Assign IP addresses to PCs
- Test connectivity using ping

## 📂 File Included
- `01-basic-topology.pkt`: Packet Tracer file for the lab setup

## 📝 Instructions
1. Assign the following IPs:
   - PC0: `192.168.1.1/24`
   - PC1: `192.168.1.2/24`
2. Connect both PCs to the switch using straight-through cables.
3. Open Command Prompt on PC0 and ping PC1 to test.

## 📷 Screenshot

![lab01](https://github.com/user-attachments/assets/6120c077-bbee-46d7-9482-67f48cf49971)

## Configuration
-Router

enbale
conf t
interface gigabitEthernet 0/0
ip address 192.168.1.1 255.255.255.0
no shutdown
exit

-PC0 & PC1 
simple assign ip through IP CONFIG

for testing:
open any PC command prompt and write command
-ping (ip of other pc)


