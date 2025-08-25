# 🖥️ Level 2

## 🎯 Goals

Goal 1 : host Computer B needs to communicate with host Computer A 

Goal 2 : host Computer D needs to communicate with host Computer C 

## 🔧 Resolution

To be able to comunicate the devices have to be connected to the same network, and have the same mask.

Remember that `127.0.0.0` is a reserved IP for network testing on your own device.

### Goal 1

1. We have a mask of `255.255.255.224` or `/27`, which means that the network portion of the IP address is going to be the first 3 octets. And our increment is going to be `32`, with `30` usable addresses.

2. So the first 3 octets of the IP address have to be the same on both devices.

3. We know that the incremet is `32`, that means the subnets on `192.168.91.x` start at multiples of 32:
`.0, .32, .64, .96, .128, .160, .192, .224`

4. Since the IP address of Client B is set to `192.168.36.222`, then we can infer that the network range is between `192.168.36.192` and `192.168.36.223`.

5. So the last octet can be any number between `193 and 222`, as long as they are **not equal to an IP address that already exists in the network**. Remember that the first octet is reserved for the Network address and the last is reserved for the Broadcast address.

### Goal 2

1. We have a mask of `/30` or `255.255.255.252`, which means that the network portion of the IP address is going to be the first 3 octets. And our increment is going to be `4`, with `2` usable addresses.

2. So the first 3 octets of the IP address have to be the same on both devices.

3. The last octect can only be `1 or 2`. Remember that 0 is reserved for the Network address and 255 is reserved for the Broadcast address.

4. And the first octet can not be `127` as it is a reserved IP.


## ✅ Solution