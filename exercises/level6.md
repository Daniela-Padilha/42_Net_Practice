# 🖥️ Level 6

## 🎯 Goals

Goal 1 : host webserv.non-real.com needs to communicate with interface Somewhere on the Net

## 🔧 Resolution

To be able to comunicate the devices have to be connected to the same network, and have the same mask.

Remember that the left column of the routing table is the destination, and the right column is the next hop.

### Goal 1

1. The Interface A1 has to be in the same network as the router interface R1. So the mask and the IP address network portion has to be the same. And the host portion has to be inside the range, which is from `87.88.254.129` to `87.88.254.254`.

2. In the routing table of host A, the next hop will be the router IP of interface R1. And the destination will be the interface Somewhere on the Net, and as we are not given that IP we set the destination to default.

3. In the routing table of router R, we can see that the next hop is an IP address that is not on the exercise, so to reach that IP address the destination haas to be default.

4. In the routing table of internet I, the destination will be Interface A1 IP address `87.88.254.227/25`.


## ✅ Solution

<img width="893" height="660" alt="Screenshot from 2025-09-01 18-57-18" src="https://github.com/user-attachments/assets/fc1a19f9-85f7-475b-978a-edd7085bead9" />
