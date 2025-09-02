# 🖥️ Level 8

## 🎯 Goals

Goal 1 : host office.non-real.com needs to communicate with host home.non-real.com

Goal 2 : host office.non-real.com needs to communicate with interface Somewhere on the Net

Goal 3 : host home.non-real.com needs to communicate with interface Somewhere on the Net

## 🔧 Resolution

To be able to comunicate the devices have to be connected to the same network, and have the same mask.

Remember that the ranges of the router interfaces must never overlap.

Remember that the left column of the routing table is the destination, and the right column is the next hop.

### Goal 1, 2 & 3

1. The internet has a routing table with a destination route of `133.219.14.0/26`. This means that it can send packets to IPs from `133.219.14.1` to `133.219.14.63` (because if our mask is `/26` then our increment is `64`). This means that all networks in between the internet and the destination must be within this range (without overlaping).

2. We have 4 networks:

- 1: Interface C1 to Interface R22
- 2: Interface D1 to Interface R23
- 3: Interface R21 to Interface R13
- 4 (already set): Interface R12 to Internet I

So we have to set the masks in a way that allows us to have **at least 3 different ranges** (one for each of the connections/networks), but we can have more this is up to you. We can have a mask of `255.255.255.192` (`/26`) or above. Since the exercise already has a mask of `255.255.255.240` (`/28`) for some interfaces we can keep that.

3. Considering that the next hop for the router R2's routing table is already set to `133.219.14.62`, this should be the IP Address for the Interface R13.

4. Taking into account these limitations, you can assign the IPs as you want (avoid overlaping). Remember, with a `/28` mask you have `16` networks avaliable, each with an increment of `16`, and `14` usable hosts per network. For networks 1 and 2 you can choose any range, but for network 3 you have to choose the range that includes `133.219.14.62` (the IP address that is already set in the R2 routing table).

Example:

- 1: From `133.219.14.1` to `133.219.14.14`
- 2: From `133.219.14.17` to `133.219.14.30`
- 3: From `133.219.14.49` to `133.219.14.62`

5. Now all we have left to do is fill the routing tables. Considering that Routers R1 and R2's next hops must be each others, Routers R1 destination must be the same destination as Internet, and the destination of clients C and D must be default.

## ✅ Solution