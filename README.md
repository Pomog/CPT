# CPT
 Getting Started with Cisco Packet Tracer. Packet Tracer is a tool that allows you to simulate real networks.

 ## install Cisco Packet Tracer
```
https://www.netacad.com/
Getting Started with Cisco Packet Tracer
https://www.netacad.com/resources/lab-downloads?courseLang=en-US
```
- Step 1. Download the version of Packet Tracer you require.
- Step 2. Launch the Packet Tracer install program.
- Step 3. Launch Cisco Packet Tracer by selecting the appropriate icon.
- Step 4. When prompted, click on Skills For All green button to authenticate.
- Step 5. Cisco Packet Tracer will launch and you are ready to explore its features.

## Launch Packet Tracer
```
packettracer
```
## Exercise 1
### Objectives
- Set up three pairs of PCs that can communicate with each other.
- Understand RJ-45 cables and their types.

1. Open Packet Tracer and create a new project.
2. Add 6 PCs.
3. Connect PCs with Copper Cables.
4. Assign IP Addresses:
```
IP Address: 192.168.1.(1-6)
Subnet Mask: 255.255.255.0
```
5. Test Connectivity:
Open Command Prompt on PC0 
```
ping 192.168.1.2
```
* RJ-45 Cable Types:
Straight-through (PC to Switch/Router)
Crossover (PC to PC)
T568A vs T568B are the two common wiring schemes, which are used to terminate the twisted-pair cable onto the connector interface. The two standards define how the RJ45 pinouts arrange the individual eight wires when linking the RJ45 connector to a cable. These wiring layouts have their own color convention to follow for electrical compatibility. The T-568B wiring scheme is considered to be the more commonly used one.

## Exercise 2
### Objectives
- Set up a network with a switch (level 2 - Data Link) and a hub (level 1 - Physical).
- Understand collision domains and how switches differ from hubs.

1. Open Packet Tracer and create a new project.
2. Drag 4 PCs, 1 Switch, and 1 Hub onto the workspace.
3. Connect PCs to Switch, using Straight-through cables.
4. Assign IPs: Switch 192.168.1.1, 192.168.1.2; Hub 192.168.1.3, 192.168.1.4.
5. Test Network:
- Switch Network: ping between two PCs.
- Hub Network: ping between two PCs.
* Switch (Layer 2): Intelligent device, forwards packets based on MAC address.
* Hub (Layer 1): Broadcasts data to all devices, creating collisions.
