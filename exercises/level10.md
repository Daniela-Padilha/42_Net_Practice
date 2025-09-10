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

### Goals
We have `4 networks`:

- Network 1: Between Interface H11, Interface H21 and Interface R11
- Network 2: Between Interface H41 and Interface R23
- Network 3: Between Interface R21 and Interface R13
- Network 4: Between Interface H31 and Interface R22


For the 1st Network we set interface H21 and interface H11 in a way that they are in the same network as interface R11 (which has the IP and Mask pre-set).

For the 2nd Network, we set interface R23 to be in the same network as interface H41 (which has the IP and Mask pre-set).

For the 3rd Network, we set the mask of interface R13 to the same as interface R21 (already pre-set). And in the router R1 router table, the destination of the first route can be set to default.

For the 4th Network, we have to be careful not to overlap the other router R2 interfaces, to ensure that we can use a mask that gives us a small range like `255.255.255.240`, which  will give us `14` usable hosts per range. And then we choose a range that does not overlap any of the ones already set.

Lastly, the destination of the internet can never be set to default, so we set the Network portion of the IP to the same that we used for every other interface, and the host portion of the IP can be set to 0. The CIDR can be set to `/24` so it includes all the ranges used in the interfaces.

So if every IP in the exercise starts with `154.204.161.` then the internet destiantion will be `154.204.161.0/24`.


## ✅ Solutio
<img width="870" height="793" alt="Screenshot from 2025-09-08 16-41-26" src="https://github.com/user-attachments/assets/a434776d-2b4e-409b-a721-61a752509c84" />
n
