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

- **Computer network**  
  A set of interconnected devices that share resources and exchange information using communication protocols.

- **Main devices**  
  - **Hosts**: End-user devices such as computers, servers, or smartphones that generate and consume data.  
  - **Routers**: Devices that forward packets between different networks and provide Internet connectivity.  
  - **Switches**: Devices that connect multiple hosts within the same local network and manage internal traffic.

- **Network topologies**  
  - **Star**: All devices connect to a central hub or switch.  
  - **Bus**: A single shared communication line connects all devices.  
  - **Ring**: Each device connects to the next, forming a closed loop.  
  - **Mesh**: Devices are interconnected with multiple paths, providing redundancy and reliability.

- **LAN vs WAN**  
  - **LAN (Local Area Network)**: A small-scale network limited to a specific location (home, office). High speed and low cost.  
  - **WAN (Wide Area Network)**: A large-scale network that connects multiple LANs across wide geographic areas (e.g., the Internet). Lower speed compared to LAN and more complex infrastructure.

---

### 2. IP Addressing
- **IPv4**: 32-bit addresses written in dotted decimal format (e.g., `192.168.1.1`).  

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
- Subnets: `(256 / Bock Size) -> 256 / 32 = 8`
- Example subnet: `192.168.143.192/27`  
  - Network address: `192.168.143.192`  
  - Broadcast address: `192.168.143.223`  
  - Usable host range: `192.168.143.193 – 192.168.143.222`

**Reference Table:**

| CIDR | Subnet Mask       | Hosts per Subnet | Block Size | Number of Subnets | Example Network  | First Usable IP     | Last Usable IP      | Broadcast Address   |
|------|-------------------|------------------|------------|-------------------|------------------|---------------------|---------------------|---------------------|
| /30  | 255.255.255.252   | 2                | 4          | 64                | 192.168.143.0    | 192.168.143.1       | 192.168.143.2       | 192.168.143.3       |
| /29  | 255.255.255.248   | 6                | 8          | 32                | 192.168.143.0    | 192.168.143.1       | 192.168.143.6       | 192.168.143.7       |
| /28  | 255.255.255.240   | 14               | 16         | 16                | 192.168.143.0    | 192.168.143.1       | 192.168.143.14      | 192.168.143.15      |
| /27  | 255.255.255.224   | 30               | 32         | 8                 | 192.168.143.0    | 192.168.143.1       | 192.168.143.30      | 192.168.143.31      |
| /26  | 255.255.255.192   | 62               | 64         | 4                 | 192.168.143.0    | 192.168.143.1       | 192.168.143.62      | 192.168.143.63      |
| /25  | 255.255.255.128   | 126              | 128        | 2                 | 192.168.143.0    | 192.168.143.1       | 192.168.143.126     | 192.168.143.127     |
| /24  | 255.255.255.0     | 254              | 256        | 1                 | 192.168.143.0    | 192.168.143.1       | 192.168.143.254     | 192.168.143.255     |

---

### 4. Gateways and Routing

- **Default gateway**  
  The device that serves as the exit point from a local network to other networks, typically a router.

- **Switch vs Router**  
  - **Switch**: Connects multiple devices within the same local network and forwards traffic based on MAC addresses.  
  - **Router**: Connects different networks together and forwards traffic based on IP addresses.

- **Routing tables and inter-subnet communication**  
  Routers maintain routing tables that define paths to different networks. These tables enable communication between subnets and ensure packets reach their correct destination.

---

### 5. Communication Protocols

- **TCP/IP model**  
  A four-layer model: Application, Transport, Network, and Link. It is the foundation of Internet communication.

	- **Application layer**: Provides services directly to the user (web, email, file transfer).  
  	- **Transport layer**: Ensures data delivery between applications.  
    	- **TCP (Transmission Control Protocol)**: Establishes a connection, divides data into numbered segments, waits for acknowledgments (ACK), and retransmits lost segments. This guarantees reliable and 	ordered delivery.  
    	- **UDP (User Datagram Protocol)**: Sends data without acknowledgments. It is faster but does not guarantee delivery or order.  
  	- **Network layer**: Handles logical addressing and routing using IP addresses, deciding how packets travel between networks.  
  	- **Link layer**: Deals with physical transmission over the local medium (Ethernet, Wi-Fi).  

> [!NOTE]
> <details>
>	<summary>TCP (Transmission Control Protocol)</summary>
>	TCP is a transport-layer protocol designed to ensure reliable communication between two devices.
>	Its operation is based on the following mechanisms:
>
>	1. **Connection establishment (Three-way handshake)**  
>	   - The client sends a `SYN` message to request a connection.  
>	   - The server replies with `SYN-ACK` to acknowledge and accept.  
>	   - The client responds with `ACK`, and the connection is established.  
>	   This process guarantees that both sides are ready before data transmission begins.  
>
>	2. **Data segmentation and numbering**  
>	   - Large data is divided into smaller segments.  
>	   - Each segment is assigned a sequence number.  
>	   - This allows the receiver to reassemble the data in the correct order.  
>
>	3. **Acknowledgments (ACKs)**  
>	   - For every segment received, the receiver sends back an acknowledgment.  
>	   - If the sender does not receive an ACK, it retransmits the segment.  
>	   This ensures that no data is lost.  
>
>	4. **Flow control**  
>	   - TCP uses a "window size" to control how much data can be sent before requiring an acknowledgment.  
>	   - This prevents overwhelming the receiver.  
>
>	5. **Error detection**  
>	   - Each segment includes a checksum.  
>	   - If the checksum does not match, the segment is discarded and retransmitted.  
>	   This guarantees data integrity.  
>
>	6. **Connection termination**  
>	   - When communication ends, both sides exchange `FIN` and `ACK` messages to close the connection gracefully.  
>	   - This ensures that all data has been delivered before the connection is released.
>
>	**Summary:**  
>	TCP works by establishing a connection, sending data in numbered segments, waiting for acknowledgments, retransmitting lost data, and closing the connection cleanly. It guarantees that information  
>	arrives 	complete, correct, and in order.
>
>	</details>

- **OSI model**  
  A seven-layer conceptual model (Physical, Data Link, Network, Transport, Session, Presentation, Application) that maps closely to the TCP/IP model.

  - **Physical**: Transmits raw bits over cables or wireless signals.  
  - **Data Link**: Packages bits into frames and manages access to the physical medium using MAC addresses.  
  - **Network**: Provides logical addressing and routing (IP).  
  - **Transport**: Ensures reliable or fast delivery of data between applications (TCP/UDP).  
  - **Session**: Establishes, manages, and terminates communication sessions.  
  - **Presentation**: Translates, encrypts, or compresses data for the Application layer.  
  - **Application**: Interfaces directly with user applications and services.

- **ARP (Address Resolution Protocol)**  
  ARP is used within local networks to map an IP address to a physical MAC address. It ensures that devices can locate each other on the same subnet and allows data to be delivered to the correct hardware interface.

- **ICMP (Internet Control Message Protocol)**  
  Used for diagnostics and error reporting. Common tools like `ping` and `traceroute` rely on ICMP.

---

### 6. Network Configuration

- **Static vs dynamic IP assignment**  
  - **Static**: IP addresses are manually configured and remain fixed.  
  - **Dynamic (DHCP)**: IP addresses are automatically assigned by a DHCP server.

- **Configuring IP, subnet mask, and gateway**  
  Proper configuration ensures devices can communicate within the subnet and reach external networks.

- **Common errors**  
  - Invalid IP address (outside the subnet range).  
  - Incorrect subnet mask (causing devices to appear in different networks).  
  - Missing or wrong gateway (preventing external communication).

- **Logs for troubleshooting**  
  System and network logs help identify misconfigurations, connectivity issues, and routing errors.

---

Recommended documentation:  
- [RFC 791 – Internet Protocol](https://www.rfc-editor.org/rfc/rfc791)  
- [RFC 1180 – TCP/IP tutorial](https://www.rfc-editor.org/rfc/rfc1180)
- [Youtube Tutorial from Thuggonaut](https://youtu.be/HQUw0CfQWAM?si=QI7vKhg9tzCQ8j9u)
- [Youtube Tutorial from PowerCert Animated Videos](https://youtu.be/s_Ntt6eTn94?si=Ybqnw3N6bw0XEXlw)
  
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
