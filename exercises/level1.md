# Level 1

## Goals

Goal 1 : host my PC needs to communicate with host my little brother's computer - Status : KO - No forward way, try again ...
Goal 2 : host my Mac needs to communicate with host my little sister's computer - Status : KO - No forward way, try again ...

## Resolution

To be able to comunicate the devices have to be connected to the same network.

### Goal 1

1. We have a mask of `255.255.255.0` or `/24`, which means that the network portion of the IP address is going to be the first 3 octets. 

2. So the first 3 octets of the IP address have to be the same on both devices

3. The last octect can be any number between `1 and 254`, as long as they are **not equal to an IP address that already exists in the network**. Remember that 1 is reserved for the Network address and 255 is reserved for the Broadcast address.

### Goal 2

1. We have a mask of `255.255.0.0` or `/16`, which means that the network portion of the IP address is going to be the first 2 octets. 

2. So the first 2 octets of the IP address have to be the same on both devices

3. The last 2 octects can be any number between `1 and 254`, as long as they are **not equal to an IP address that already exists in the network**. Remember that 1 is reserved for the Network address and 255 is reserved for the Broadcast address.


## Solution

