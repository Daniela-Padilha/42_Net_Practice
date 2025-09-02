# 🖥️ Level 7

## 🎯 Goals

Goal 1 : host dev.non-real.net needs to communicate with host accounting.non-real.net

## 🔧 Resolution

To be able to comunicate the devices have to be connected to the same network, and have the same mask.

Remember that the ranges of the router interfaces must never overlap.

Remember that the left column of the routing table is the destination, and the right column is the next hop.

### Goal 1

1. The Interface A1 has to be in the same network as the router interface R11. So the mask and the IP address network portion has to be the same. And the host portion has to be inside the range, which is from `112.198.14.1` to `112.198.14.254`.

2. The interfaces of each router cannot overlap. So if interface R11 IP is `112.198.14.1` and the interface R12 IP is `112.198.14.254` we have to set the masks in a way that allows us to have **at least 3 different ranges** (one for each of the connections/networks), but we can have more this is up to you. We get a mask of `255.255.255.192` or `/26`.

- Interface A1 to Interface R11:

	From `112.198.14.1` to `112.198.14.62`

- Interface R12 to Interface R21: 

	From `112.198.14.193` to `112.198.14.254`

- Interface R22 to Interface C1:

	From `112.198.14.65` to `112.198.14.126` (it could also be the left over range `112.198.14.129 – 112.198.14.190`, it is indiferent in this case)

3. Now all we have left to do is fill the routing tables. Considering that host A destination must be host C and vice versa. The routers must have their next hops as each other to allow communication both ways.


## ✅ Solution

<img width="983" height="660" alt="Screenshot from 2025-09-01 19-33-21" src="https://github.com/user-attachments/assets/338a2ef1-0af3-4c8e-8c82-ec1ed7a1c110" />

