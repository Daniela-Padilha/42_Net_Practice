# Subnetting Based on Network Requirements (5 Networks)

## Exercise
**Goal:** Divide this network into **at least 5 equal-sized subnets**. Calculate the increment and list 5 subnet ranges.

**Given:**  
- IP: `192.168.1.0`  
- Mask: `255.255.255.0` or `/24`

> ℹ️ You cannot have exactly 5 equal subnets. Borrow enough bits so that `2^n ≥ 5` → `n = 3` (gives 8 subnets). Each subnet will be `/27`.

---

## Step 1: Convert the Mask to Binary

   `255.255.255.0 → 11111111.11111111.11111111.00000000`

---
   
## Step 2: Determine Bits to Borrow

   Multiply the binary chart by 2:
   
   `128 64 32 16 8 4 2 1 (*2) → 256 128 64 32 16 8 4 2`

   We want at least **5 networks**.

   `256 128 64 32 16 8 4 2`
                     | | |

   Borrow **3 bits** from the host portion.

---
   
## Step 3: Create the New Subnet Mask
   
   Binary: `11111111.11111111.11111111.11100000`

   Decimal: `255.255.255.224` or `/27`

---
   
## Step 4: Find the Increment

   The increment is the value of the **last network bit** in the mask.

   Binary last octet: `11100000` → Increment = **32**.

---

## Step 5: Calculate Subnet Ranges

| Subnet            | Usable Hosts Range             | Broadcast Address |
|-------------------|--------------------------------|-------------------|
| 192.168.1.0/27    | 192.168.1.1 – 192.168.1.30     | 192.168.1.31      |
| 192.168.1.32/27   | 192.168.1.33 – 192.168.1.62    | 192.168.1.63      |
| 192.168.1.64/27   | 192.168.1.65 – 192.168.1.94    | 192.168.1.95      |
| 192.168.1.96/27   | 192.168.1.97 – 192.168.1.126   | 192.168.1.127     |
| 192.168.1.128/27  | 192.168.1.129 – 192.168.1.158  | 192.168.1.159     |

(Three more available if needed: `192.168.1.160/27`, `192.168.1.192/27`, `192.168.1.224/27`.)

---

## Step 6: Calculate Number of Usable Hosts

   We have `5` host bits (5 zeros in the subnet mask).      

   **Number of usable hosts** = `2^5 - 2 = 30` hosts per subnet

---

## Final Answer

- **New mask:** `255.255.255.224 (/27)`  
- **Increment:** `32`  
- **Usable hosts per subnet:** `30`  
- **Five subnet ranges:**  
  - `192.168.1.0 – 192.168.1.31`  
  - `192.168.1.32 – 192.168.1.63`  
  - `192.168.1.64 – 192.168.1.95`  
  - `192.168.1.96 – 192.168.1.127`  
  - `192.168.1.128 – 192.168.1.159` 

---