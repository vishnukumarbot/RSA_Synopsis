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

