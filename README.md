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

## Exercise 3
### Objectives
- Set up a DHCP server for IP assignment.
- Configure an HTTPS server and DNS server.

1. Add a Router, Switch, DHCP Server, Web Server, and PCs.
- Assigning IP Addresses:
```

Device IP Address Subnet Mask Gateway
Router (Interface) 192.168.1.1	255.255.255.0	-
DHCP Server	192.168.1.10	255.255.255.0	192.168.1.1
DNS Server	192.168.1.20	255.255.255.0	192.168.1.1
HTTPS Server	192.168.1.99	255.255.255.0	192.168.1.1
FTP Server	192.168.1.30	255.255.255.0	192.168.1.1
```
3. Configure DHCP Server:
- Services → DHCP → Enable DHCP.
-  Set:
```
Pool Name: enter Network1.
Default Gateway: 192.168.1.1
Subnet Mask: 255.255.255.0
DNS Server: 192.168.1.20
Starting IP Address: 192.168.1.100
Maximum Users: 50
```
Testing DHCP:
Go to each PC → Desktop → IP Configuration.
Set it to DHCP and check if it gets an IP

3. Configure DNS Server:
- Services → DNS → Add:
```
deep-in-net.local → 192.168.1.99
deep-in-net.com → 192.168.1.99
```
Testing DNS
```
nslookup deep-in-net.local
```
4. Configure HTTPS Server:
- Enable HTTPS service, disable HTTP.


- Test: HTTPS
Open a PC browser 
```
https://deep-in-net.com.
```

- Test FTP server:
```
C:\>ftp 192.168.1.30
username: cisco
ftp>dir
```
| Device  | Function                                      | Layer  | Uses                     |
|---------|----------------------------------------------|--------|--------------------------|
| Switch  | Connects devices in a LAN using MAC addresses | Layer 2 | Modern office networks   |
| Hub     | Broadcasts data to all connected devices    | Layer 1 | Rarely used today        |
| Router  | Connects different networks using IP addresses | Layer 3 | Home & business internet |


## Exercise 4
### Objectives
- Configure a Network in Cisco Packet Tracer

1. Add Network Devices
- Open Cisco Packet Tracer.
- From the End Devices category, drag and drop two PC-PT devices (PC0 and PC1).
- From the Network Devices → Routers category, drag and drop a Router-PT (1841).
- From the Connections category, select a Copper Straight-Through cable to connect each PC to the router.

2. Connect the Devices
- Connect PC0 to Router (FastEthernet0/0).
- Connect PC1 to Router (FastEthernet0/1).
- Use Copper Straight-Through cables since we are connecting different device types (PC to Router).

3. Assign PC IP Addresses
- Click on PC0 → Open the Desktop Tab → Click on IP Configuration.
- Set the IP Address to 192.168.1.2 and 192.168.2.2
- Set the Subnet Mask to 255.255.255.0
- Set the Default Gateway to 192.168.1.1 (Router's interface).

4. Configure the Router
Click on the Router → Go to the CLI tab.
Enter configuration mode:
```
enable
configure terminal
```
Assign an IP to the first interface (FastEthernet0/0):
```
interface FastEthernet0/0
ip address 192.168.1.1 255.255.255.0
no shutdown
exit
```
Assign an IP to the second interface (FastEthernet0/1):
```
interface FastEthernet0/1
ip address 192.168.2.1 255.255.255.0
no shutdown
exit
```
Exit configuration mode and save the settings:
```
exit
write memory
```
5. Test
Run ping tests from PC0 to PC1 and vice versa

6. Explanations
7. Conceptual Explanations

### 1. What is a Router and What is Its Role?
A **router** is a network device that connects different networks and directs data packets based on IP addresses. Its main functions:
- Routes traffic between different subnets.
- Determines the best path for data to reach its destination.
- Acts as a **default gateway** for devices.

### 2. Switch vs. Router
| Feature  | Switch  | Router  |
|----------|--------|--------|
| Function | Connects devices within a LAN using MAC addresses | Connects different networks using IP addresses |
| OSI Layer | Layer 2 (Data Link) | Layer 3 (Network) |
| Uses | Used in LANs | Used to connect different networks (e.g., LAN to the Internet) |

### 3. OSI Model Layer Where a Router Operates
A **router** operates at **Layer 3 (Network Layer)**. It works with **IP addresses** to forward packets between networks.

### 4. What is a Default Gateway?
A **default gateway** is the router’s IP address within a subnet that a device uses to send data outside its network. In this setup:
- PC0’s default gateway is `192.168.1.1`.
- PC1’s default gateway is `192.168.2.1`.

## Exercise 5
### Objectives
- Creating the Network in Cisco Packet Tracer
- Create a network with two subnets that can communicate with each other.
- Ensure that all devices within the same switch can communicate.
- Ensure that inter-subnet communication is enabled via a router.

### Concept Descriptions

| Concept            | Description |
|--------------------|-------------|
| **Subnetting**    | Divides a network into smaller segments to improve efficiency. |
| **CIDR Notation** | Represents subnet size (e.g., /29 = 6 usable IPs). |
| **Default Gateway** | The router IP used by devices to communicate outside their subnet. |
| **Router Interfaces** | Connect different subnets and enable communication. |
| **Ping Command** | Used to test connectivity between devices. |
| **IP Configuration** | Each device must have an IP, subnet mask, and default gateway. |

### Subnet Details

| Subnet Name | Network Address | Subnet Mask     | CIDR | Usable IP Range         | Broadcast Address | Router Interface |
|-------------|----------------|-----------------|------|-------------------------|-------------------|-----------------|
| **Subnet 1** | 192.168.1.0    | 255.255.255.248 | /29  | 192.168.1.2 - 192.168.1.6 | 192.168.1.7       | 192.168.1.1     |
| **Subnet 2** | 192.168.1.8    | 255.255.255.248 | /29  | 192.168.1.10 - 192.168.1.14 | 192.168.1.15  | 192.168.1.9     |

### Subnet 1: 192.168.1.0/29

| Device        | IP Address     | Subnet Mask     | Default Gateway |
|--------------|---------------|----------------|----------------|
| **Router (G0/0)** | 192.168.1.1 | 255.255.255.248 | - |
| **PC1**       | 192.168.1.2   | 255.255.255.248 | 192.168.1.1 |
| **PC2**       | 192.168.1.3   | 255.255.255.248 | 192.168.1.1 |
| **PC3**       | 192.168.1.4   | 255.255.255.248 | 192.168.1.1 |
| **PC4**       | 192.168.1.5   | 255.255.255.248 | 192.168.1.1 |
| **PC5**       | 192.168.1.6   | 255.255.255.248 | 192.168.1.1 |

### Subnet 2: 192.168.1.8/29

| Device        | IP Address     | Subnet Mask     | Default Gateway |
|--------------|---------------|----------------|----------------|
| **Router (G0/1)** | 192.168.1.9 | 255.255.255.248 | - |
| **PC6**       | 192.168.1.10  | 255.255.255.248 | 192.168.1.9 |
| **PC7**       | 192.168.1.11  | 255.255.255.248 | 192.168.1.9 |
| **PC8**       | 192.168.1.12  | 255.255.255.248 | 192.168.1.9 |
| **PC9**       | 192.168.1.13  | 255.255.255.248 | 192.168.1.9 |
| **PC10**      | 192.168.1.14  | 255.255.255.248 | 192.168.1.9 |


#### Conceptual 
📌 Subnetting
- Subnetting divides a large network into smaller, more manageable sub-networks.
- The Subnet Mask (e.g., 255.255.255.248) defines the range of IPs in a subnet.
- The CIDR Notation (e.g., /29) represents how many bits are used for the network.
- Each subnet contains:
-- Network Address (first IP) – Identifies the subnet.
-- Usable IP Range – Assigned to hosts (PCs, servers, etc.).
-- Broadcast Address (last IP) – Used to send messages to all devices in the subnet.

📌 Router Configuration
- The router is responsible for inter-subnet communication.
- It has two interfaces:
-- GigabitEthernet0/0 (Subnet 1) → 192.168.1.1
-- GigabitEthernet0/1 (Subnet 2) → 192.168.1.9
- Each PC uses its respective router interface as the gateway.

📌 Default Gateway
- A default gateway is the router's IP address within a subnet.
- All devices use this IP to communicate outside their subnet.

📌 Ping Testing
To verify connectivity:
```
ping 192.168.1.3  # Test PC1 → PC2 (same subnet)
ping 192.168.1.10 # Test PC1 → PC6 (different subnet)
```

## Exercise 6
### Objectives
- Connecting Two Subnets Using Routers

🔍 Concepts Explained
- Subnetting - Divides a large network into smaller, manageable sub-networks to improve efficiency and security.
- Routing Table	- A table inside a router that contains information about available routes and helps determine the best path for data packets.
- Default Gateway	- The IP address of the router's interface that allows devices in a subnet to communicate outside their own subnet.
- Static Routing -	Manually configured routes that define a fixed path for network traffic between different subnets.
- Dynamic Routing -	Automatically discovers the best path for network traffic using protocols like RIP, OSPF, or EIGRP.
- Ping Command -	Used to test connectivity between devices and verify network configurations.

🗺️ Subnet Plan
- **Subnet 1:** `192.168.1.0/24` (PC1)
- **Subnet 2:** `192.168.2.0/24` (PC2)
- **Point-to-Point Network between Routers:** `10.10.0.0/30`

| Subnet | Network Address | Subnet Mask | Router Interface |
|--------|----------------|-------------|------------------|
| **Subnet 1** | `192.168.1.0` | `255.255.255.0` | `192.168.1.1` (Router1 G0/0) |
| **Subnet 2** | `192.168.2.0` | `255.255.255.0` | `192.168.2.1` (Router2 G0/0) |
| **Point-to-Point** | `10.10.0.0` | `255.255.255.252` | `10.10.0.1` (Router1 S0/0), `10.10.0.2` (Router2 S0/0) |

## 🛠️ Steps to Configure the Network

### 1️⃣ Add Devices in Cisco Packet Tracer
- **2 Routers** (Router1 & Router2)
- **2 PCs** (PC1 & PC2)
- **1 Serial Cable** (between routers)
- **2 Ethernet Cables** (PCs to routers)

### 2️⃣ Assign IP Addresses

#### **PC1 Configuration (Subnet 1)**
```text
IP Address: 192.168.1.2
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.1.1
```

#### **PC2 Configuration (Subnet 2)**
```text
IP Address: 192.168.2.2
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.2.1
```

### 3️⃣ Router Configuration

#### **Router1 Configuration**
```bash
enable
configure terminal
interface GigabitEthernet0/0
ip address 192.168.1.1 255.255.255.0
no shutdown
exit
interface Serial0/0/0
ip address 10.10.0.1 255.255.255.252
clock rate 64000
no shutdown
exit
ip route 192.168.2.0 255.255.255.0 10.10.0.2
```

#### **Router2 Configuration**
```bash
enable
configure terminal
interface GigabitEthernet0/0
ip address 192.168.2.1 255.255.255.0
no shutdown
exit
interface Serial0/0/0
ip address 10.10.0.2 255.255.255.252
no shutdown
exit
ip route 192.168.1.0 255.255.255.0 10.10.0.1
```

### 4️⃣ Verify Network Connectivity

#### **Ping from PC1 to PC2**
```bash
ping 192.168.2.2
```

#### **Check Routing Table on Router1**
```bash
show ip route
```
Expected output:
```text
C 192.168.1.0/24 is directly connected, GigabitEthernet0/0
S 192.168.2.0/24 [1/0] via 10.10.0.2
C 10.10.0.0/30 is directly connected, Serial0/0/0
```

#### **Check Routing Table on Router2**
```bash
show ip route
```
Expected output:
```text
C 192.168.2.0/24 is directly connected, GigabitEthernet0/0
S 192.168.1.0/24 [1/0] via 10.10.0.1
C 10.10.0.0/30 is directly connected, Serial0/0/0
```

## 🌟 Summary
- Configured **two subnets** connected via **two routers**.
- Assigned **IP addresses** to all devices.
- Set up **static routes** for subnet communication.
- Verified connectivity with **ping** and **show ip route**.
