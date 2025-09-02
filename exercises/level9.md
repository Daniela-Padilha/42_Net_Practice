# 🖥️ Level 9

## 🎯 Goals

Goal 1 : host meson needs to communicate with host ion

Goal 2 : host cation needs to communicate with host gluon

Goal 3 : host meson needs to communicate with host Internet

Goal 4 : host meson needs to communicate with host gluon

Goal 5 : host ion needs to communicate with host cation

Goal 6 : host cation needs to communicate with host Internet

## 🔧 Resolution

To be able to comunicate the devices have to be connected to the same network, and have the same mask.

Remember that the ranges of the router interfaces must never overlap.

Remember that the left column of the routing table is the destination, and the right column is the next hop.\

Remember that `192.0.0.0` and `10.0.0.0` are private IP addresses.

### Goal 1

1. The Interface A1 has to be in the same network as the Interface B1 and router interface R11. So the mask and the IP address network portion has to be the same. And the host portion has to be inside the range, which is from `(network portion).1` to `(network portion).126`.

### Goal 2

1. The routing table of host D sets the next hop to `109.203.117.112`, so that will be Interface R23 IP.

2. The Interface D1 has to be in the same network as the router interface R23. So the mask and the IP address network portion has to be the same. Interface R23 has a pre-set mask of `/18` or `255.255.192.0`. So the host portion has to be from `109.203.65.1` to `109.203.126.254`.

3. The Interface R22 cannot overlap Interface R23.

4. The Interface C1 has to be in the same network as the router interface R22. So the mask and the IP address network portion has to be the same.

### Goal 3

1. The routing table of host A needs to have the next hop as the IP of the Interface R11. The destination can be set to default.

2. The routing table of router R1 has to have a route that connects to the internet (pre-set).

3. The routing table of the Internet I has to have one route where the destination is the Interface A1 IP so that reverse way is possible.

### Goal 4

1. Host A is already connected to router R1, and host D is already connected to router R2, so all that is left to do is connect router R2 to router R1.

2. Interface R13 and Interface R21 have to be in the same network. So the mask and the IP address network portion has to be the same. Interface R21 has a pre-set mask of `/30` or `255.255.255.252`, with an increment of `4` and `2` usable hosts per network.

3. The routing table of router R2 has to have the next hop set to the IP of Interface R13.

4. The routing table of router R1 has to have a route to reach host D, where the next hop is the IP of Interface R21, and the destination can be default.

### Goal 5

1. The routing table of Host B needs to have the next hop set to the IP of Interface R11. And the destination can be default.

2. Interface C1 and Interface R22 have to be in the same network. So the mask and the IP address network portion has to be the same. But the Interfaces on the router cannot overlap.

3. The routing table of Host C needs to have the next hop set to the IP of Interface R22.


### Goal 6

1. Make sure no pirvate or reserved IP is being used. Connect the routing table of Internet I to the host C by setting up a route with the IP of host C as the destination.


## ✅ Solution