# Subnetting Based on Network Requirements (4 Networks)

## Exercise
**Goal:** Divide this network into 4 subnets. Calculate the increment and the IP ranges.  

**Given:**  
- IP: `192.168.1.0`  
- Mask: `255.255.255.0` or `/24`  

---

## Step 1: Convert the Mask to Binary

   `255.255.255.0 → 11111111.11111111.11111111.00000000`

---
   
## Step 2: Determine Bits to Borrow

   Multiply the binary chart by 2:
   
   `128 64 32 16 8 4 2 1 (*2) → 256 128 64 32 16 8 4 2`

   We want **4 networks**.

   `256 128 64 32 16 8 4 2`
                       | |

   Borrow **2 bits** from the host portion.

---
   
## Step 3: Create the New Subnet Mask
   
   Binary: `11111111.11111111.11111111.11000000`

   Decimal: `255.255.255.192` or `/26`

---
   
## Step 4: Find the Increment

   The increment is the value of the **last network bit** in the mask.

   Binary last octet: `11000000` → Increment = **64**.

---

## Step 5: Calculate Subnet Ranges

| Subnet           | Usable Hosts Range           | Broadcast Address |
|------------------|------------------------------|-------------------|
| 192.168.1.0/26   | 192.168.1.1 – 192.168.1.62   | 192.168.1.63      |
| 192.168.1.64/26  | 192.168.1.65 – 192.168.1.126 | 192.168.1.127     |
| 192.168.1.128/26 | 192.168.1.129 – 192.168.1.190| 192.168.1.191     |
| 192.168.1.192/26 | 192.168.1.193 – 192.168.1.254| 192.168.1.255     |

---

## Step 6: Calculate Number of Usable Hosts

   We have `6` host bits (6 zeros in the subnet mask).      

   **Number of usable hosts** = `2^6 - 2 = 62` hosts per subnet

---

## Final Answer

- **Increment:** 64  
- **Subnet ranges:**  
  - `192.168.1.0 – 192.168.1.63`  
  - `192.168.1.64 – 192.168.1.127`  
  - `192.168.1.128 – 192.168.1.191`  
  - `192.168.1.192 – 192.168.1.255`  

---