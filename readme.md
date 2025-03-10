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

