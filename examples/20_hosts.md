# Subnetting Based on Host Requirements (20 hosts)

## Exercise
**Goal:** Divide this network into 5 subnets with 20 hosts each. Calculate the increment and the IP ranges.  

**Given:**  
- Network: `142.2.0.0 /16`  

---

## Step 1: Convert the Mask to Binary

   `/16` means that the mask has 24 bits reserved for the network portion, which leaves 8 bits for the host portion, so the mask is `11111111.11111111.00000000.00000000`

   `11111111.11111111.00000000.00000000  → 255.255.0.0`

---

## Step 2: Determine Bits to Borrow

   Multiply the binary chart by 2:
   
   `128 64 32 16 8 4 2 1 (*2) → 256 128 64 32 16 8 4 2`

   We want **40 hosts**.

   `256 128 64 32 16 8 4 2`
                |  | | | |

   Reserve **5 bits** from the host portion.
   So we have **11 bits** that are not reserved and that we can borrow.

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

| Subnet         | Usable Hosts Range       | Broadcast Address |
|----------------|--------------------------|-------------------|
| 142.2.0.0/26   | 142.2.0.1 – 142.2.0.30   | 142.2.0.31        |
| 142.2.0.32/26  | 142.2.0.33 – 142.2.0.62  | 142.2.0.63        |
| 142.2.0.64 /26 | 142.2.0.65 – 142.2.0.94  | 142.2.0.95        |
| 142.2.0.96 /26 | 142.2.0.97 – 142.2.0.126 | 142.2.0.127       |
| 142.2.0.128 /26| 142.2.0.129 – 142.2.0.158| 142.2.0.159       |

(One more available if needed: `142.2.0.160/27`, `142.2.0.192/27`, `142.2.0.224/27`)

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
  - `142.2.0.0 - 142.2.0.31`  
  - `142.2.0.32 - 142.2.0.63`  
  - `142.2.0.64 - 142.2.0.95`
  - `142.2.0.96 - 142.2.0.127`
  - `142.2.0.128 - 142.2.0.159`
  
---