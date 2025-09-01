# 42_Net_Practice

_Discovering the basics of networking._

---

## 🌐 What is a Network?

A **network** is a group of devices (computers, phones, servers, IoT devices, etc.) connected together to share data and resources.  
Networking allows devices to:
- **Communicate:** Send and receive information.
- **Share resources:** Access printers, files, or internet connections.
- **Scale:** Easily add new devices.

### Key Components:
- **Hosts:** Devices connected to a network.
- **Switches/Routers:** Hardware that directs traffic.
- **Medium:** Wi-Fi or cables used to transmit data.
- **Protocols:** Rules that define communication, like TCP/IP.

---

## 🔗 TCP/IP

**TCP/IP (Transmission Control Protocol / Internet Protocol)** is the foundation of how devices communicate on networks and the internet.  
- **IP:** Handles addressing and routing. It ensures data packets get to the right device.  
- **TCP:** Ensures reliability. It breaks data into packets, tracks them, resends lost ones, and reassembles them in order.

📦 **Analogy:**  
Think of sending a package:  
- **IP** is the postal system that finds the route.  
- **TCP** ensures your package arrives safely and in the right order.

---

## 📍 What is an IP Address?

An **IP (Internet Protocol) address** is a unique combination of numbers that enables communication between devices and allows them to connect to the internet. Devices connected to a network are called **hosts**.

### How is it assigned?
IP addresses are usually assigned by the router using **DHCP (Dynamic Host Configuration Protocol)**, which automatically provides an IP address to any device that connects to a network.

---

### 🖼️ IP Address Structure Diagram

```
IP Address Example: 192.168.1.204
Mask:             255.255.255.0

┌───────────── Network Portion ────┐┌─ Host ─┐
192       .   168      .   1       .   204
│             │             │           │
│             │             │           └───── Host Identifier (unique per device)
│             │             └──────────────── Network Identifier
│             └────────────────────────────── Network Identifier
└──────────────────────────────────────────── Network Identifier
```

- Each number is an octet (beacuse it is composed of 8 bits).
- The first three octets (`192.168.1`) are the **Network Portion**.
- The last octet (`204`) is the **Host Portion**.

---

## 🛡️ What is a subnet mask/netmask?

- Defines how big the network is and how many IP addresses are there.
- If the octet in the mask is `255`, the corresponding octet from the IP address will always stay the same for all devices in the network.
- If the octet in the mask is `0`, the corresponding octet from the IP address can be any number between 0 and 255 (unique per host).

---

## 🟩 What is a Default Gateway?

The **default gateway** is typically the router. It allows hosts to communicate with devices outside of their local network.

---

##  🌎 IP Address Classes
Public IP addresses are organized by classes:
|Class | Range                       | Netmask        |
|------|-----------------------------|----------------|
|A     | 1.0.0.0 - 126.255.255.255   | 255.0.0.0      |
|B     | 128.0.0.0 - 191.255.0.0     | 255.255.0.0    |
|C     | 192.0.0.0 - 223.255.255.0   | 255.255.255.0  |
|D     | 224.0.0.0 - 239.255.255.255 | (Multicast)    |
|E     | 240.0.0.0 - 255.255.255.255 | (Experimental) |

- **Class A**: For large organizations, up to 16 million hosts per network (126 networks).
- **Class B**: Up to 65,534 hosts per network (16,382 networks).
- **Class C**: Up to 254 hosts per network (2 million networks).
- **Class D**: Reserved for multicast (not for hosts).
- **Class E**: Experimental, not usable for hosts.
- `127.0.0.0` is reserved for loopback addresses (network testing on your own device, 16 million hosts).

---

## 🧮 How many IP addresses are there in a network?

For a typical subnet:
- First address: **Network address** (e.g., `192.168.1.0`)
- Last address: **Broadcast address** (e.g., `192.168.1.255`)
- Router: usually `192.168.1.1`
- **Usable addresses per subnet:** 253

Globally, there are about **4.3 billion IPv4 addresses** (`2^32 = 4,294,967,296`).  
With billions of devices, we've run out of IPv4 addresses!

---

## 🦺 RFC1918: Private IP Address Ranges

**RFC1918** defines private IP address ranges for home/office devices to communicate locally, without using real internet addresses.

|Class | Range                               | Netmask        |
|------|-------------------------------------|----------------|
|A     | 10.0.0.0 - 10.255.255.255           | 255.0.0.0      |
|B     | 172.16.0.0 - 172.31.255.255         | 255.255.0.0    |
|C     | 192.168.0.0 - 192.168.255.255       | 255.255.255.0  |

Private IPs are **not unique** and don't connect you directly to the internet. To solve this, we use **NAT**.

---

## 🌐 NAT (Network Address Translation)
Your ISP lends your router a public IP address. The router uses NAT to translate local private IPs into that public IP, allowing internet access for all local devices.

Phones use public IPs from cellular providers when not on Wi-Fi.

---

## 🚦 IPv4 vs IPv6

- **IPv4**: the old system, 32 bits, 4 numbers separated by dots (e.g., `192.168.1.204`)
- **IPv6**: the upgrade, 128 bits, 8 groups of hexadecimal numbers (e.g., `2001:0db8:85a3::8a2e:0370:7334`).  
  There are roughly 340 undecillion (36 zeros) IPv6 addresses—so we won't run out!

---

## 🛠 Useful Networking Commands
- `ifconfig` — Shows your IP addresses (Linux/macOS).
- `ipconfig` — Shows your IP addresses (Windows).
- `ping` — Checks if a device is reachable/alive.

---

## 🧩 Subnetting
- **Subnetting is dividing a large network into smaller, easier-to-manage networks by “borrowing” some of the host space and making it part of the network.**
- Subnetting allows you to **manipulate the number of hosts in a network** in a network by creating more networks, and to do that you have to borrow bits from the host portion and adding them to the network portion.
- The **Host Identifier** tells us how many hosts we can have in that network.  
  - Convert the subnet mask to **binary**: the number of `0`s indicates the host portion.
  - Formula: `2 ^ (number of 0's) - 2`.  
    - Example: `2^8 - 2 = 256 - 2 = 254` usable hosts.
- CIDR is writing the mask like this: `/24` which means **the first 24 bits are for the network, and the last 8 bits are for devices**.
- **Classful networking** uses the default netmask for a class.
- **Classless networking** uses a custom subnet mask to break networks into smaller segments.

### 🔍 Visual Example
| Subnet | Binary Netmask                               | Network Bits | Host Bits | Total Hosts | Usable Hosts |
|--------|---------------------------------------------|-------------|-----------|-------------|--------------|
| `/24`  | 11111111.11111111.11111111.00000000          | 24          | 8         | 256         | 254          |
| `/25`  | 11111111.11111111.11111111.10000000          | 25          | 7         | 128         | 126          |
| `/26`  | 11111111.11111111.11111111.11000000          | 26          | 6         | 64          | 62           |

💡 Splitting a `/24` network into `/25`s creates **two subnets** with 126 usable IPs each, instead of one big network of 254 hosts.

### Practical Examples of Subnetting: 

- [Subnetting based on network requirements](examples/4_networks.md)
- [Subnetting based on host requirements](examples/40_hosts.md)

---

## 🖲 Switch

Destributes packages between devices in the same network. It cannot connect to a network outside of its own.

---

## 🔌 Router

Connects multiple networks together. It has an interface for every network it connects to. The range on one of its interfaces must never overlap the range of its other interfaces. An overlap would imply the interfaces belong to the same network.

---

## 🗄 Routing Table

Is a data table stored in a router or networkhost that lists all the routes to a particular network destination.

### 📫 Destination

- It is the left column of the table.
- It contains the IP addresses that you want to send a package to, combined with the mask/CIDR of that network.
- It can be set to `default` or `0.0.0.0/0` if you don't want to specify a destination. This way any device inside the network can be the destination.


### 📨 Next Hop

- It is the right column of the table.
- It contains the IP address of the next router that you need to send the packages to in order to reach the destination network.

---

## 📚 References & Further Reading

- [IP Addressing Basics (Youtube)](https://www.youtube.com/watch?v=5WfiTHiU4x8&list=PLIhvC56v63IKrRHh3gvZZBAGvsvOhwrRF)
- [What is DHCP?](https://en.wikipedia.org/wiki/Dynamic_Host_Configuration_Protocol)

---

Feel free to contribute or ask questions!
