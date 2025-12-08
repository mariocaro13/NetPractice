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
- Address classes: A, B, C, D, E.  
- Private vs public addresses.  
- Special addresses: loopback (`127.0.0.1`), broadcast, network address.  

### 3. Subnetting
- Subnet mask: defines network vs host portion (e.g., `255.255.255.0`).  
- CIDR notation: `/8`, `/16`, `/24`.  
- Calculations: network address, broadcast address, valid host range, number of hosts.  

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
