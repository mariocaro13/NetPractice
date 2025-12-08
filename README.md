This project has been created as part of the 42 curriculum by mcaro-ro

# NetPractice

## 📖 Description
NetPractice is a project designed to introduce the fundamentals of **computer networking**.  
The goal is to learn how to configure IP addresses, subnet masks, and gateways so that a network functions correctly.  
Through an interactive web interface, you will face 10 levels with non-functioning network diagrams that must be fixed.

---

## ⚙️ Instructions
1. Download the project archive from the intra-net project's page.  
2. Extract the files into a folder.  
3. Open the `index.html` file in your web browser.  
4. Log in with your 42 login or use the *evaluation* tab for random configurations.  
5. Adjust the network settings (IP, subnet mask, gateway) until the network works properly.  
6. Use the **Check again** button to verify your solution.  
7. Export your configuration with **Get my config** once you complete each level.  
8. Place the 10 exported configuration files (one per level) at the root of your Git repository.  

---

## 📚 Resources
Networking concepts studied in this project:  

### 1. Basic Networking Concepts
- Definition of a computer network.  
- Main devices: hosts, routers, switches.  
- Network topologies: star, bus, ring, mesh.  
- Difference between LAN (local area network) and WAN (wide area network).  

### 2. IP Addressing
- IPv4: 32-bit addresses written in dotted decimal format (e.g., `192.168.1.1`).  

#### IPv4 Address Classes

| Class | Leading Bits | Range of First Octet | Default Subnet Mask | Networks Available | Hosts per Network | Typical Use                                     |
|-------|--------------|----------------------|---------------------|--------------------|-------------------|-------------------------------------------------|
| A     | 0xxxxxxx     | 0 – 127              | 255.0.0.0 (/8)      | 128                | ~16 million       | Very large networks (ISPs, big organizations)   |
| B     | 10xxxxxx     | 128 – 191            | 255.255.0.0 (/16)   | 16,384             | ~65,000           | Medium-sized networks (universities, companies) |
| C     | 110xxxxx     | 192 – 223            | 255.255.255.0 (/24) | 2,097,152          | 254               | Small networks (home, office LANs)              |
| D     | 1110xxxx     | 224 – 239            | N/A                 | N/A                | N/A               | Multicast groups (specialized communication)    |
| E     | 1111xxxx     | 240 – 255            | N/A                 | N/A                | N/A               | Experimental / reserved (not used in practice)  |

#### IPv4 Private and Public Address Ranges

| Type    | Range                          | CIDR Notation | Typical Use                                         |
|---------|--------------------------------|---------------|-----------------------------------------------------|
| Private | 10.0.0.0 – 10.255.255.255      | 10.0.0.0/8    | Large private networks (corporate, ISP labs)        |
| Private | 172.16.0.0 – 172.31.255.255    | 172.16.0.0/12 | Medium private networks (universities, enterprises) |
| Private | 192.168.0.0 – 192.168.255.255  | 192.168.0.0/16| Small private networks (home, office LANs)          |
| Public  | All other ranges               | N/A           | Routable on the Internet                            |

#### IPv4 Special Address Ranges

| Address / Range                    | CIDR Notation  | Purpose / Description                                  |
|------------------------------------|----------------|--------------------------------------------------------|
| 127.0.0.0 – 127.255.255.255        | 127.0.0.0/8    | Loopback (localhost, internal testing)                 |
| 0.0.0.0                            | N/A            | Default route / “any address”                          |
| 255.255.255.255                    | N/A            | Limited broadcast (to all hosts in local network)      |
| x.x.x.0                            | N/A            | Network address (identifies the subnet itself)         |
| x.x.x.255 (last address in subnet) | N/A            | Broadcast address (to all hosts in that subnet)        |
| 169.254.0.0 – 169.254.255.255      | 169.254.0.0/16 | Link-local (APIPA, automatic assignment if DHCP fails) |

---

### 3. Subnetting
- Subnet mask: defines network vs host portion (e.g., `255.255.255.0`).  
- CIDR notation: `/8`, `/16`, `/24`.  
- Calculations: network address, broadcast address, valid host range, number of hosts. 

#### Subnetting Reference Table

**Example Calculation:**

- Mask: `255.255.255.224`  
- Binary form: `11111111.11111111.11111111.11100000`  
- Count the bits set to 1 → `8 + 8 + 8 + 3 = 27` → CIDR `/27`  
- Block size: `256 - 224 = 32` → each subnet has 32 addresses  
- Valid hosts: `32 - 2 = 30` (subtract network and broadcast)  
- Example subnet: `192.168.143.192/27`  
  - Network address: `192.168.143.192`  
  - Broadcast address: `192.168.143.223`  
  - Usable host range: `192.168.143.193 – 192.168.143.222`

**Reference Table:**

| CIDR | Subnet Mask       | Hosts per Subnet | Block Size | Example Network       | First Usable IP     | Last Usable IP      | Broadcast Address   |
|------|-------------------|------------------|------------|-----------------------|---------------------|---------------------|---------------------|
| /30  | 255.255.255.252   | 2                | 4          | 192.168.143.0         | 192.168.143.1       | 192.168.143.2       | 192.168.143.3       |
| /29  | 255.255.255.248   | 6                | 8          | 192.168.143.0         | 192.168.143.1       | 192.168.143.6       | 192.168.143.7       |
| /28  | 255.255.255.240   | 14               | 16         | 192.168.143.0         | 192.168.143.1       | 192.168.143.14      | 192.168.143.15      |
| /27  | 255.255.255.224   | 30               | 32         | 192.168.143.0         | 192.168.143.1       | 192.168.143.30      | 192.168.143.31      |
| /26  | 255.255.255.192   | 62               | 64         | 192.168.143.0         | 192.168.143.1       | 192.168.143.62      | 192.168.143.63      |
| /25  | 255.255.255.128   | 126              | 128        | 192.168.143.0         | 192.168.143.1       | 192.168.143.126     | 192.168.143.127     |
| /24  | 255.255.255.0     | 254              | 256        | 192.168.143.0         | 192.168.143.1       | 192.168.143.254     | 192.168.143.255     |


### 4. Gateways and Routing
- Default gateway: exit point from local network to other networks.  
- Switch vs router:  
  - Switch → connects devices within the same network.  
  - Router → connects different networks.  
- Routing tables and inter-subnet communication.  

### 5. Communication Protocols
- TCP/IP model: Application, Transport, Network, Link.  
- OSI model: 7 layers and correspondence with TCP/IP.  
- ARP: resolves IP ↔ MAC addresses.  
- ICMP: diagnostic protocol (ping, traceroute).  

### 6. Network Configuration
- Static vs dynamic IP assignment (DHCP).  
- Configuring IP, subnet mask, and gateway.  
- Common errors: invalid IP, wrong mask, missing gateway.  
- Logs for troubleshooting.  

Recommended documentation:  
- [RFC 791 – Internet Protocol](https://www.rfc-editor.org/rfc/rfc791)  
- [RFC 1180 – TCP/IP tutorial](https://www.rfc-editor.org/rfc/rfc1180)  

---

## 🤖 Use of AI
AI tools were used during this project to:  
- Generate theoretical explanations of networking concepts.  

All AI-generated content was reviewed and fully understood before being included in the project.  

---

## 📂 Submission
- Deliver **10 configuration files** (one per level) at the root of the repository.  
- Include the `README.md` file at the root.  
- During the defense, you will solve 3 random levels within a limited time.  
- External tools are not allowed (only a simple calculator such as `bc` is tolerated).  

---
