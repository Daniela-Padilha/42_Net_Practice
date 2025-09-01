# 🖥️ Level 5

## 🎯 Goals

Goal 1 : host Machine A needs to communicate with host The Mighty Router

Goal 2 : host Machine B needs to communicate with host The Mighty Router

Goal 3 : host Machine A needs to communicate with host Machine B

## 🔧 Resolution

To be able to comunicate the devices have to be connected to the same network, and have the same mask.

Remember that the left column of the routing table is the destination, and the right column is the next hop.

### Goal 1

1. The Interface A1 has to be in the same network as the router interface R1. So the mask and the IP address network portion has to be the same. And the host portion has to be inside the range, which is from `53.157.155.1` to `53.157.155.126`.

2. In the routing table of host A, the next hop will be the router IP of interface R1.

### Goal 2

1. The Interface B1 has to be in the same network as the router interface R2. So the mask and the IP address network portion has to be the same. And the host portion has to be inside the range, which is from `136.140.64.1` to `136.140.127.255`.

2. In the routing table of host B, the next hop will be the router IP of interface R2.

### Goal 3

1. For Machine A to be able to communicate with Machine B, the destination point of the routing table on Machine A needs to be the IP address for Machine B with the respective CIDR, or default to encompass every device in the network.


## ✅ Solution
