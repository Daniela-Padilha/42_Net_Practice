# 🖥️ Level 3

## 🎯 Goals

Goal 1 : host Host A needs to communicate with host Host B

Goal 2 : host Host A needs to communicate with host Host C 

Goal 3 : host Host B needs to communicate with host Host C

## 🔧 Resolution

To be able to comunicate the devices have to be connected to the same network, and have the same mask.

Remember that `127.0.0.0` is a reserved IP for network testing on your own device.

### Goal 1

1. We have a mask of `255.255.255.128` or `/25`, which means that the network portion of the IP address is going to be the first 3 octets. And our increment is going to be `128`, with `126` usable addresses.

2. So the first 3 octets of the IP address have to be the same on the 3 devices.

3. We know that the incremet is `128`, that means the subnets on `104.198.167.x` start at multiples of 128:
`.0, .128`

4. Since the IP address of Interface A is set to `104.198.167.125`, then we can infer that the network range is between `104.198.167.0` and `104.198.167.127`.

5. So the last octet can be any number between `1 and 126`, as long as they are **not equal to an IP address that already exists in the network**. Remember that the first octet is reserved for the Network address and the last is reserved for the Broadcast address.

### Goal 2 & 3

1. The IP of interface C has to be in the same range as the other interfaces.


## ✅ Solution