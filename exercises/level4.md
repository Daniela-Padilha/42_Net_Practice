# 🖥️ Level 3

## 🎯 Goals

Goal 1 : host A nice host needs to communicate with host Another host

Goal 2 : host A nice host needs to communicate with host My_Gate

Goal 3 : host Another host needs to communicate with host My_Gate

## 🔧 Resolution

To be able to comunicate the devices have to be connected to the same network, and have the same mask.

Remember that the ranges of the router interfaces must never overlap.

### Goal 2 & 3

1. The Interface R2 of the router has a range of IPs from `61.43.116.1` to `61.43.116.127`, and the Interface R3 has a range from `61.43.116.192` to `61.43.116.255`. So we must choose a mask that ensures no overlaping of IPs.

2. To ensure that, we have to choose a mask that encompasses the IP addresses in the interval of `61.43.116.128` and `61.43.116.191`, which gives us `63` possible addresses.

3. We need a mask that gives us `63` usable hosts. If we know that `2 ^ (number of 0's) - 2` is equal to the number of usable hosts, `2^6-2` will give us exactly `63` hosts. We need a mask with at least 6 zeros which is `/26` or `255.255.255.192`. But that mask already exists in our router, so we have to remove one zero, becoming `/27` or `255.255.255.224`, which gives us `30` usable addresses.

4. We choose a mask of `255.255.255.224` or above. And an IP address between `61.43.116.129` and `61.43.116.158`. And cannot be the same as interfaces B1 and A1

### Goal 1

1. The IP and mask of interfaces B1 and A1 have to be in the same range as the interface R1.


## ✅ Solution

<img width="753" height="697" alt="Screenshot from 2025-09-01 17-42-24" src="https://github.com/user-attachments/assets/91cbf1b6-dd6c-402b-aa33-0a678e9090ef" />

