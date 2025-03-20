# Tasks Overview

## Task 1: Binary Representations

**Objective:** Implement bitwise operations commonly used in computational theory.

### Steps:

1. **Bitwise Rotation Functions:**
   - Implement `rotl(x, n)`: Rotates bits of a 32-bit unsigned integer `x` to the left by `n` places.
   - Implement `rotr(x, n)`: Rotates bits of a 32-bit unsigned integer `x` to the right by `n` places.

2. **Logical Bitwise Functions:**
   - Implement `ch(x, y, z)`: Chooses bits from `y` where `x` has bits set to 1 and from `z` where `x` has bits set to 0.
   - Implement `maj(x, y, z)`: Computes the majority function, setting a bit if at least two of `x, y, z` have it set.

3. **Testing and Demonstration:**
   - Provide example inputs for each function.
   - Print outputs in binary format to verify correctness.

---

## Task 2: Hash Functions

**Objective:** Convert the hash function from *The C Programming Language* by Kernighan & Ritchie into Python, test it, and analyze why 31 and 101 are used.

### Steps:

1. **Implement Hash Function:**
   - Convert the original C hash function into Python.
   - Use `31` as the multiplier and `101` as the modulus.

2. **Alternative Implementation:**
   - Implement the hash function using a class-based approach.
   - Allow customization of multiplier and modulus values.

3. **Testing and Demonstration:**
   - Provide example inputs to compute hash values.
   - Print results to verify correctness.

4. **Analysis of Constants:**
   - Explain why `31` is used as a multiplier /ANS = (prime number, efficient distribution, fast computation).
   - Explain why `101` is used as a modulus /ANS = (prime number, even distribution, avoids common factors).

---

# Task 3: SHA-256 Padding

**Objective:** Implement a Python function that calculates SHA-256 padding for a given file.  
The function reads a file, computes the required padding, and prints the final padded message in hex format.  

## **Steps:**

### **1. Read File Content:**
   - Read the file as binary data.
   - Convert the data to hexadecimal representation for debugging.

### **2. Compute Original Message Length:**
   - Calculate the message length in bits (bytes × 8).
   - This value will be stored in the last 8 bytes of the final padded message.

### **3. Append '1' Bit (`0x80` in hex):**
   - SHA-256 padding requires a `1` bit to mark the end of the message.
   - This is represented as `0x80` in hexadecimal.

### **4. Compute Zero Padding:**
   - Add enough zero bits so that the total message length is 448 mod 512.
   - Ensures that the final message (after adding the length) is a multiple of 512 bits (64 bytes).

### **5. Append Original Message Length (64-bit Big-Endian Integer):**
   - Store the original message length** as a 64-bit (8-byte) big-endian integer**.
   - This ensures the receiver can correctly determine the pre-padding length.

   ---

# Task 4: Prime Numbers

## **Objective**
Calculate the first 100 prime numbers using two well-established algorithms:  
1. **Trial Division Algorithm** (Checking divisibility up to the square root).  
2. **Sieve of Eratosthenes** (Efficient prime number generation).  

---

## **Steps:**

### **1. Implement Prime Number Check**
   - **Trial Division:**  
     - Check divisibility for numbers **up to the square root** of `n` to determine primality.  
     - This method is **slower** but simple.  

   - **Sieve of Eratosthenes:**  
     - Mark multiples of each prime starting from `2` as **non-prime**.  
     - Faster for computing **multiple prime numbers at once**.

### **2. Generate the First 100 Prime Numbers**
   - **Trial Division:** Iterate through numbers, checking for primality.  
   - **Sieve of Eratosthenes:** Generate primes up to a **precomputed limit**.  

---

# Task 5: Roots

## **Objective**
- Compute the **first 32 bits of the fractional part** of the square roots of the **first 100 prime numbers**.

## **Approach**

1. **Find the first 100 prime numbers** using Trial Division.
2. **Compute the square root of each prime**.
3. **Extract the fractional part** from the square root.
4. **Convert the fractional part into a 32-bit binary representation**.

---

## **Steps Implemented So Far**

### **1. Compute the First 100 Prime Numbers**
- We use the **Trial Division Algorithm** to generate prime numbers.
- The function iterates through numbers, checking if they are **divisible only by 1 and themselves**.
- Only numbers **up to the square root** are checked for divisibility to improve efficiency.

---

### **2. Compute Square Root and Extract the Fractional Part**
- We compute `sqrt(n)`, then subtract the integer part to get **only the fractional value**.
- This fractional part is **what we convert into a 32-bit binary number**.

---

### **3. Convert Fractional Part to 32-bit Binary**
- We repeatedly **multiply the fraction by 2**, extracting `1` for values `≥1`, and `0` otherwise.
- This continues for **32 iterations** to obtain a 32-bit binary string.

---

# Task 6: Proof of Work

## **Objective**
- Identify the **English word** with the **greatest number of leading 0 bits**.
- Provide proof that the word(s) exist in at least one **English dictionary**.

---

## **Approach**
1. **Load a list of English words** from a dictionary file.
2. **Compute the SHA-256 hash** for each word.
3. **Convert the hash into a binary representation**.
4. **Count the number of leading 0 bits** in each hash.
5. **Find the word(s) with the most leading 0 bits**.
6. **Verify that the word exists in a dictionary**.

---

### **1. Load an English Dictionary**
- A wordlist file (`words.txt`) was used to obtain a list of **valid English words**.
- The dataset includes **common English words** from **various dictionaries**.

---

### **2. Compute the SHA-256 Hash of Each Word**
- Each word was converted to a **SHA-256 hash**.
- The hash was then represented in **binary format**.

---

### **3. Count Leading 0 Bits in the Hash**
- Each hash was analyzed to determine the **number of leading zeros**.
- The word(s) with the **highest count** of leading 0 bits were identified.

---

### **4. Verify Word in an Online Dictionary**
- To confirm the word exists, an **automated search** was performed in **Merriam-Webster**.
- The dictionary lookup ensures that the word is **genuinely English**

---

# Task 7: Turing Machines

## **Objective**
- Design a **Turing Machine** that adds **1** to a binary number.
- The machine starts at the **left-most non-blank symbol**.
- The **right-most bit** is the **least significant bit (LSB)**.

---

## **Approach**
1. **Define Turing Machine rules** for binary addition.
2. **Simulate the Turing Machine in Python**.
3. **Process binary numbers by flipping bits and propagating carries**.

---
### **Explanation**
1. **Start at the right-most bit**.
2. **If the bit is `1`**, turn it into `0` and move left (carry propagation).
3. **If the bit is `0`**, turn it into `1` and halt (no carry needed).
4. **If there's no more bits (blank space), write `1` to extend the number**.
---
## **Example**
| **Input** | **Output** |
|----------|----------|
| `100111` | `101000` |
| `111` | `1000` |
| `0` | `1` |
| `1` | `10` |
| `1111` | `10000` |

---

## **Methodology**
### **How the Turing Machine Adds 1**
1. **Start at the right-most bit**.
2. **If we see a `1`**, change it to `0` (carry the 1).
3. **If we see a `0`**, change it to `1` and stop.
4. **If all bits are flipped (`111...` turns into `000...`), add a `1` at the beginning**.

---

# Task 8: Computational Complexity

## **Objective**
- Implement **Bubble Sort** in Python.
- Modify the algorithm to **count the number of comparisons** made during sorting.
- **Sort all permutations** of the list `L = [1, 2, 3, 4, 5]`.
- Print each permutation **along with the number of comparisons**.

---

## **Approach**
1. **Implement Bubble Sort** with a counter to track comparisons.
2. **Generate all permutations** of `[1, 2, 3, 4, 5]`.
3. **Sort each permutation** using Bubble Sort.
4. **Record and print the number of comparisons** for each permutation.

---

## **Bubble Sort Algorithm with Comparison Counter**
- Bubble Sort is a **simple sorting algorithm** that repeatedly swaps adjacent elements if they are in the wrong order.
- We count the **number of comparisons** made during sorting.

### **Time Complexity of Bubble Sort**
| **Case** | **Time Complexity** |
|---------|----------------|
| **Best Case (Already Sorted)** | `O(n)` |
| **Worst Case (Reverse Sorted)** | `O(n²)` |
| **Average Case** | `O(n²)` |

---

## **Example Output**
| **Permutation** | **Comparisons Required** |
|---------------|--------------------|
| `[1, 2, 3, 4, 5]` | `10` |
| `[5, 4, 3, 2, 1]` | `10` |
| `[3, 1, 4, 5, 2]` | `9` |
| `[4, 5, 3, 1, 2]` | `10` |

---

## **Methodology**
### **Steps Taken**
1. **Generate all permutations** of `[1, 2, 3, 4, 5]`.
2. **Apply Bubble Sort** to each permutation.
3. **Count the number of comparisons** made.

---