# Subnetting Based on Host Requirements

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
                       | |

   Borrow **6 bits** from the host portion.

---
  
2. Define how many hosts bits we need, so that each network can have 40 hosts.
   
    `128 64 32 16 8 4 2 1 (*2) = 256 128 64 32 16 8 4 2`
   
     We need 6 bits `64, 32, 16, 8, 4 and 2`
   
4. Create the new mask with 6 more bits (reversed for host requirements)

     `11111111.11111111.11111111.00111111`

5. Transform it into decimal

   `255.255.255.63`

