# CH04 Block Ciphers and The Data Encryption Standard

[toc]

## Classification of Symmetric Encryption

### Stream Ciphers

- ymmetric encryption 
  - Two users share a symmetric encryption key. 
- Encrypts a digital data stream one bit or one byte at a time 
  - Example: Vernam • Ideal case: One-time pad 
- Practical solution: stream cipher 
  - Deterministic bit-stream generator so that the cryptographic bit stream can be produced by both users from a shorter generating key (seed value). 
  - It must be computationally impractical to predict future portions of the bit stream based on previous portions of the bit stream.

### Block Ciphers

- Symmetric encryption 
  - Two users share a symmetric encryption key. 
  - Generalization of multiple letter encryption 
  - A block of plaintext is treated as a whole and used to produce a ciphertext block of equal length. 
    - Typical block size: 64 bits or 128 bits

## Block Cipher

### Feistel Cipher

- Feistel proposed the use of a cipher that alternates substitutions and permutations

  - Substitutions

    Each plaintext element or group of elements is uniquely replaced by a corresponding ciphertext element or group of elements

  - Permutation

    No elements are added or deleted or replaced in the sequence, rather the order in which the elements appear in the sequence is changed

- Is a practical application of a proposal by Claude Shannon to develop a product cipher that alternates confusion and diffusion functions 
- Is the structure used by many significant symmetric block ciphers currently in use

## The Data Encryption Standard(DES)

- Issued in 1977 by the National Bureau of Standards (now NIST) as Federal Information Processing Standard 46
- Was the most widely used encryption scheme until the introduction of the Advanced Encryption Standard (AES) in 2001
- Algorithm itself is referred to as the Data Encryption Algorithm (DEA)
  - Data are encrypted in 64-bit blocks using a 56-bit key 
  - The algorithm transforms 64-bit input in a series of steps into a 64-bit output 
  - The same steps, with the same key, are used to reverse the encryption

### Encryption and Decryption

### Streangth of DES

Average Time Required for Exhaustive Key Search 

- DES
  - $56-bit\ keys: 2^{56} \approx\ 7.2 * 10^{16}$
  - With a machine with $10^9$ decryptions/s: 1.125 years
- Permutation cipher
  - $26! \approx 4 * 10^{26}$
  - With a machine with 10^9 decryptions/s: 6.3 billion years

- AES-128
  - $128-bit\ keys: 2 ^{128} ≈ 3.4 × 10^{38}$
  - With a machine with 10^9 decryptions/s: 5.3 × $10^{21}$ years