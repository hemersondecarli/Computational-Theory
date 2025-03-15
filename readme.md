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
