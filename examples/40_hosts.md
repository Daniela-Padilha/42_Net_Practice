# Subnetting Based on Host Requirements (40 hosts)

## Exercise
**Goal:** Divide this network into 3 subnets with 40 hosts each. Calculate the increment and the IP ranges.  

**Given:**  
- IP: `10.1.1.0`  
- Mask: `255.255.255.0` or `/24`  

---

## Step 1: Convert the Mask to Binary

   `/24` means that the mask has 24 bits reserved for the network portion, which leaves 8 bits for the host portion, so the mask is `255.255.255.0`

   `255.255.255.0 → 11111111.11111111.11111111.00000000`

---

## Step 2: Determine Bits to Borrow

   Multiply the binary chart by 2:
   
   `128 64 32 16 8 4 2 1 (*2) → 256 128 64 32 16 8 4 2`

   We want **40 hosts**.

   `256 128 64 32 16 8 4 2`
             |  |  | | | |

   Reserve **6 bits** from the host portion.
   So we have **2 bits** that are not reserved and that we can borrow.

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

| Subnet        | Usable Hosts Range     | Broadcast Address |
|---------------|------------------------|-------------------|
| 10.1.1.0/26   | 10.1.1.1 – 10.1.1.62   | 10.1.1.63         |
| 10.1.1.64/26  | 10.1.1.65 – 10.1.1.126 | 10.1.1.127        |
| 10.1.1.128/26 | 10.1.1.129 – 10.1.1.190| 10.1.1.191        |

(One more available if needed: `10.1.1.254/26`)

---

## Step 6: Calculate Number of Usable Hosts

   We have `6` host bits (6 zeros in the subnet mask).      

   **Number of usable hosts** = `2^6 - 2 = 62` hosts per subnet

---

## Final Answer

- **New mask:** `255.255.255.192 (/26)`  
- **Increment:** `64`  
- **Usable hosts per subnet:** `62`  
- **Five subnet ranges:**  
  - `10.1.1.0 – 10.1.1.63`  
  - `10.1.1.64 – 10.1.1.127`  
  - `10.1.1.128 – 10.1.1.191`

---