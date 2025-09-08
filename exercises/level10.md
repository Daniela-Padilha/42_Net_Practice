# 🖥️ Level 10

## 🎯 Goals

Goal 1 : host Host one needs to communicate with host Host two

Goal 2 : host Host three needs to communicate with host Host four

Goal 3 : host Host one needs to communicate with host Internet

Goal 4 : host Host one needs to communicate with host Host four

Goal 5 : host Host two needs to communicate with host Host three

Goal 6 : host Host three needs to communicate with host Internet

Goal 7 : host Host four needs to communicate with host Internet

## 🔧 Resolution

To be able to comunicate the devices have to be connected to the same network, and have the same mask.

Remember that the ranges of the router interfaces must never overlap.

Remember that the left column of the routing table is the destination, and the right column is the next hop.\

Remember that `192.0.0.0` and `10.0.0.0` are private IP addresses.

### Goal 1

1. The Interface H11 has to be in the same network as the Interface H21 and router interface R11. So the mask and the IP address network portion has to be the same. And the host portion has to be inside the range, which is from `154.204.161.1` to `154.204.161.126`.

### Goal 2

1. The routing table of host H4 sets the next hop to `154.204.161.129`, so that will be Interface R23 IP.

2. The Interface H41 has to be in the same network as the router interface R23. So the mask and the IP address network portion has to be the same. Interface H41 has a pre-set mask of `/26` or `255.255.255.192`.

3. Make sure no private or reserved IP is being used. And that the Interface R22 and Interface H31 are in the same network.

### Goal 3

1. The Internet I routing table destination can be set to default to be able to communicate with more than one host.







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


## ✅ Solutio
<img width="870" height="793" alt="Screenshot from 2025-09-08 16-41-26" src="https://github.com/user-attachments/assets/a434776d-2b4e-409b-a721-61a752509c84" />
n
