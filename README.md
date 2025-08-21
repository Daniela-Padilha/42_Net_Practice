# 42_Net_Practice

## 📍 IP Address

### What is it?
**IP (Internet Protocol) addresses** enable communication between devices and allow them to connect to the internet.
The devices connected to a network are called **hosts**.

### How is it assigned?
IP addresses are typically assigned by the router using **DHCP (Dynamic Host Configuration Protocol)**, which automatically provides an IP address to any device that connects to a network.

### What does it mean?
Example: 
IP Address: ''' 192.168.1.204 '''

Mask: ''' 255.255.255.0 '''

Each of the numbers between the dots are called **octets**, and can be between 0 and 255.
The first 3 octets are the **Network Portion** of the IP address.
The last octet is the **Host Portion** of the IP address.

### What is a subnet mask/netmask
If the octet is 255 we know that the corresponding octet from the IP address will always stay the same in a network. So all the devices in that network will have those same octets.
If the octet is 0, the corresponding octet from the IP address can be any number between 0 and 255.

## Default Gateway
It is the router, it allows for hosts to communicate with other devices outside of their network.

## How many IP addresses are there?
Originally it would be 256, but some are reserved.

- The first one is the **network address**: ''' 192.168.1.0 '''
- The last one is the **broadcast address**: ''' 192.168.1.255 ''' (it communicates wwhat you tell him to everyone)
- The router: ''' 192.168.1.1 '''

Result: 253 usable IP addresses

