# 42_Net_Practice

_Discovering the basics of networking._

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

- The first three octets (`192.168.1`) are the **Network Portion**.
- The last octet (`204`) is the **Host Portion**.

---

## 🛡️ What is a subnet mask/netmask?

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

## 🧮 How many public IP addresses are there?

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
  There are roughly 340 undecillion IPv6 addresses—so we won't run out!

---

## 🛠 Useful Networking Commands
- `ifconfig` — Shows your IP addresses (Linux/macOS).
- `ipconfig` — Shows your IP addresses (Windows).
- `ping` — Checks if a device is reachable/alive.

---

## 🧩 Subnetting
- **Classful networking** uses the default netmask for a class.
- **Classless networking** uses a different subnet mask to break networks into smaller segments.
- 
---

## 📚 References & Further Reading

- [IP Addressing Basics (Youtube)](https://www.youtube.com/watch?v=5WfiTHiU4x8&list=PLIhvC56v63IKrRHh3gvZZBAGvsvOhwrRF)
- [What is DHCP?](https://en.wikipedia.org/wiki/Dynamic_Host_Configuration_Protocol)

---

Feel free to contribute or ask questions!
