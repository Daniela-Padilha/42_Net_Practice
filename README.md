# 42_Net_Practice

_Discovering the basics of networking._

---

## 📍 IP Address

### What is it?
An **IP (Internet Protocol) address** is a unique combination of numbers that enables communication between devices and allows them to connect to the internet. Devices connected to a network are called **hosts**.

### How is it assigned?
IP addresses are usually assigned by the router using **DHCP (Dynamic Host Configuration Protocol)**, which automatically provides an IP address to any device that connects to a network.

---

### IP Address Structure Diagram

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

### What is a subnet mask/netmask?

- If the octet in the mask is `255`, the corresponding octet from the IP address will always stay the same for all devices in the network.
- If the octet in the mask is `0`, the corresponding octet from the IP address can be any number between 0 and 255 (unique per host).

---

## 🟩 What is a Default Gateway?

The **default gateway** is typically the router. It allows hosts to communicate with devices outside of their local network.

---

### IP Address Organization
Public IP addresses are organized by classes (a, b, c, d and e).
|Class | Range                       | Netmask        |
|------|-----------------------------|----------------|
|A     | 1.0.0.0 - 126.255.255.255   | 255.0.0.0      |
|B     | 128.0.0.0 - 191.255.0.0     | 255.255.0.0    |
|C     | 192.0.0.0 - 223.255.255.0   | 255.255.255.0  |
|D     | 224.0.0.0 - 239.255.255.255 |                |
|E     | 240.0.0.0 - 255.255.255.255 |                |

- Class A was designed for companies and government entities, it is a type of network that gives access to 16 million different IP adresses per network. In the world there is only 126 class A networks.
- Class B gives access to 65,534 hosts per network. In the world there are 16,382 class B networks.
- Class C gives access to 254 hosts per network. In the world there are 2 million class C networks.
- Class D addresses are reserved for multicast (very important for networking and we cannot use them).
- Class E are experimental, not usable either.
- 127.0.0.0 are loop back addresses (virtual IP addresses inside our device), they are missing from the range and are used for network testing. There are 16 million of them.

---

## 🧮 How many public IP addresses are there?

For a typical subnet:

- The first address is the **network address** (e.g., `192.168.1.0`)
- The last address is the **broadcast address** (e.g., `192.168.1.255`, used to communicate with all devices)
- The router typically uses the first usable address (e.g., `192.168.1.1`)

**Result:** 253 usable IP addresses per subnet.

In the world: about 4.3 billion IP addresses (2^32 = 4,294,967,296).
Sounds like a lot, but… with billions of people, phones, computers, smart TVs, fridges, cars, etc. we ran out of IP addresses.

---

**To solve the issue we came up with a temporary solution**

## RFC1918
RFC1918 is a document that defines private IP address ranges your devices use at home or in an office, so they can communicate locally without using up real internet addresses.

|Class | Range                               | Netmask        |
|------|-------------------------------------|----------------|
|A     | 10.0.0.0 - 10.255.255.255           | 255.0.0.0      |
|B     | 172.16.0.0 - 172.31.255.255         | 255.255.0.0    |
|C     | 192.168.0.0 - 192.168.255.255       | 255.255.255.0  |

Private IP addresses are **not** unique, and as such do not connect you to the internet. To solve that we use NAT.

---

## NAT (Network Address Translation)
Your ISP (Internet service provider, example: meo, vodafone, etc...) will let you borrow one public IP address that will be assigned to your router that will do the NAT. Nat will automatically translate a private IP address into a public one when connecting to the internet.

Our phones, also have a public IP address for when we are not connected to our home network (Wi-fi), and we are connected to our cellular provider.

---
**Even with private IP addresses and NAT we ran out of IP addresses.**

## IPv4 vs IPv6
- IPv4: is the old system, it uses 32 bits to represent an address, written as 4 numbers separated by dots.
- IPv6: is the upgrade, designed to fix the shortage. It uses 128 bits, written as 8 groups of hexadecimal numbers (example: `2001:0db8:85a3::8a2e:0370:7334`). There are roughly 340 undecillion (that’s a 3.4 with 38 zeros) IPv6 addresses in the world.

---

## Useful commands
- `ifconfig`: tells you your ip address.
- `ping`: Is a command used to see if something is "alive and awake".

---

## Subnetting
Taking a class A network and make it smaller with a diferent submask other than its default, its called a classless network.
If we use the deafult submask, its a classful.

---

## 📚 References & Further Reading

- [IP Addressing Basics](https://www.youtube.com/watch?v=5WfiTHiU4x8&list=PLIhvC56v63IKrRHh3gvZZBAGvsvOhwrRF)
- [What is DHCP?](https://en.wikipedia.org/wiki/Dynamic_Host_Configuration_Protocol)

---

Feel free to contribute or ask questions!
