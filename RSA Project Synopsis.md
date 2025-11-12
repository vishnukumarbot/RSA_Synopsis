# Project Synopsis – Public Key Cryptosystem Implementation

**Author:** Vishnu Gelle  
**Course Project:** WSU – Public Key Cryptosystem Implementation  
**Language:** C  

---

## 🧩 Overview
This project implements a complete public-key encryption system based on the **RSA algorithm**, designed to encrypt and decrypt ASCII text files using modular exponentiation over large primes.  

The program supports key generation, encryption, and decryption through command-line options, following the required interface:

```bash
./wsu-pub-crypt -genkey
./wsu-pub-crypt -e -k pubkey.txt -in plaintext.txt -out ciphertext.txt
./wsu-pub-crypt -d -k prikey.txt -in ciphertext.txt -out decrypted.txt

This implementation uses multiplicative modular arithmetic with a randomly chosen secret exponent and a safe prime modulus to provide semantic security. Each plaintext block is encrypted using a fresh random value, producing a unique ciphertext even if the same message block is repeated.
Key Generation
•	A 32-bit safe prime p is generated as p = 2q + 1, where q is a (k–1)-bit prime satisfying q mod 12 = 5.
•	Generator g = 2 is used, which is a primitive root modulo p.
•	A random private key d is chosen with 0 < d < p, and the corresponding public key is e = g^d mod p.
•	Keys are saved in plain text:
o	pubkey.txt: e g p
o	prikey.txt: d g p

Encryption and Decryption
•	Plaintext is read as bytes and grouped into 24-bit blocks (m < p).
•	For each block, a random integer k is chosen and ciphertext pairs are computed as:
•	C1 = g^k mod p
•	C2 = (e^k * m) mod p
•	Decryption uses either:
•	m = (C1^(p-1-d) * C2) mod p
(based on Fermat’s Little Theorem, avoiding modular inversion).

Implementation Details
•	Language: C
•	No third-party crypto libraries: All math is written from scratch:
o	Miller-Rabin probabilistic primality test for key generation
o	Fast modular exponentiation (square-and-multiply)
o	Safe prime construction
•	Data Types: uint64_t with 128-bit intermediate arithmetic (__int128) to handle 32-bit modulus securely.
Why I Found This Project Interesting
 I found this project particularly engaging because it bridges theoretical cryptography with real systems programming. Implementing modular arithmetic, primality testing, and key generation from scratch helped me understand how abstract math translates into secure, working code. Writing my own Miller–Rabin test and modular exponentiation made me appreciate the elegance of these algorithms and how much detail lies behind a simple encryption command. It was rewarding to see the entire pipeline — from generating a safe prime to successfully decrypting text — come together as a functioning cryptosystem.
Summary
This project demonstrates a working example of asymmetric encryption. It adheres closely to academic cryptography principles by implementing its own number theory algorithms, while still being lightweight and testable on any Linux system.
The system highlights the fundamental operations behind modern public-key schemes—key generation, modular exponentiation, and the importance of randomness in encryption.



