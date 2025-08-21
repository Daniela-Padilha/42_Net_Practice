# 42_Net_Practice

_Discovering the basics of networking._

---

## 📍 IP Address

### What is it?
An **IP (Internet Protocol) address** enables communication between devices and allows them to connect to the internet. Devices connected to a network are called **hosts**.

### How is it assigned?
IP addresses are usually assigned by the router using **DHCP (Dynamic Host Configuration Protocol)**, which automatically provides an IP address to any device that connects to a network.

---

### IP Address Structure Diagram

```
IP Address Example: 192.168.1.204
Mask:             255.255.255.0

┌───────────── Network Portion ────┐┌─ Host ─┐
192       .   168      .   1       .   204
│             │             │         │
│             │             │         └───── Host Identifier (unique per device)
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

## 🟩 Default Gateway

The **default gateway** is typically the router. It allows hosts to communicate with devices outside of their local network.

---

## 🧮 How many IP addresses are there?

For a typical subnet:

- The first address is the **network address** (e.g., `192.168.1.0`)
- The last address is the **broadcast address** (e.g., `192.168.1.255`, used to communicate with all devices)
- The router typically uses the first usable address (e.g., `192.168.1.1`)

**Result:** 253 usable IP addresses per subnet.

---

## 📚 References & Further Reading

- [IP Addressing Basics](https://www.youtube.com/watch?v=5WfiTHiU4x8&list=PLIhvC56v63IKrRHh3gvZZBAGvsvOhwrRF)
- [What is DHCP?](https://en.wikipedia.org/wiki/Dynamic_Host_Configuration_Protocol)

---

Feel free to contribute or ask questions!
