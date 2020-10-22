# Chapter6 Advanced Encryption Standard

[toc]

## Finite Field Arithmetic

### Why Finite Field for Block Cipher

-  Underlying operations
  - Substitution 
  - Transposition (permutation) 
  - Multiple rounds 
  - Simple bit operations (such as XOR) 
- Bit randomizion effect 
  -  Field multiplication 
  -  Field inversion

### Rationale for Binary Field

- For convenience and for implementation efficiency we would like to work with integers that fit exactly into a given number of bits with no wasted bit patterns. 
  - Integers in the range 0 through $2^ n – 1$, which fit into an n-bit word 
- The set of such integers, using modular arithmetic, is not a field. 
- A finite field containing $2^n$ elements is referred to as GF($2^n$ ) 
  - Every polynomial in GF($2^n$ ) can be represented by an n-bit number.

### Finite Field Arithmetic for AES

- For Advanced Encryption Standard (AES), we use GF($2^8$ ).
  - All operations are performed on 8-bit bytes
- The arithmetic operations of addition, subtraction, multiplication, and division are performed over the finite field GF($2^8$ )
  - Irreducible polynomial: $(x^ 8 + x^ 4 + x^ 3 + x + 1)$
  - Division is defined as: $a /b = a (b^{-1} )$

## AES 

- Advanced Encryption Standard 
  - Standardized by NIST in 2001. 
  - FIPS Publication 197

### General Structure

- State 
  - 4 by 4 square matrix of bytes 
  - Represents platin-text/cipher-text/intermediate data
- Parameters corresponding to the key size 
  - Key: 128, 192 and 256 bits 
  - Rounds: 10, 12 and 14
- SPN (Substitution-permutation network) 
  - Round: four transformation functions 
  - Permutation: ShiftRows 
  - Substitution: SubBytes / MixColumns / AddRoundKey

### Detailed Structure

- Processes the entire data block as a single matrix during each round using substitutions and permutation 
- The key that is provided as input is expanded into an array of forty-four 32-bit words, w[i]
- The cipher begins and ends with an AddRoundKey stage 
- Can view the cipher as alternating operations of XOR encryption (AddRoundKey) of a block, followed by scrambling of the block (the other three stages), followed by XOR encryption, and so on 
- `Each stage is easily reversible`
- The decryption algorithm makes use of the expanded key in reverse order, however the `decryption algorithm is not identical to the encryption algorithm`
- State is the same for both encryption and decryption 
- Final round of both encryption and decryption consists of only three stages

#### Four Different Stages are Used

- Substitute bytes – uses an S-box to perform a byte-by-byte substitution of the block 
- ShiftRows – a simple permutation
- MixColumns – a substitution that makes use of arithmetic over GF($2^8$ )
- AddRoundKey – a simple bitwise XOR of the current block with a portion of the expanded key

### S-Box Rationale

- The S-box is designed to be resistant to known cryptanalytic attacks 
- The Rijndael developers sought a design that has a low correlation between input bits and output bits and the property that the output is not a linear mathematical function of the input 
- The nonlinearity is due to the use of the multiplicative inverse

### Substitute Bytes

### Shift Rows

- More substantial than it may first appear 
- The State, as well as the cipher input and output, is treated as an array of four 4-byte columns 
- On encryption, the first 4 bytes of the plaintext are copied to the first column of State, and so on 
- The round key is applied to State column by column 
  - Thus, a row shift moves an individual byte from one column to another, which is a linear distance of a multiple of 4 bytes 
- Transformation ensures that the 4 bytes of one column are spread out to four different columns

### Mix Columns

- Coefficients of a matrix based on a linear code with maximal distance between code words ensures a good mixing among the bytes of each column 
- The mix column transformation combined with the shift row transformation ensures that after a few rounds all output bits depend on all input bits

### Add RoundKey

- The 128 bits of State are bitwise XORed with the 128 bits of the round key 
- Operation is viewed as a columnwise operation between the 4 bytes of a State column and one word of the round key
  - Can also be viewed as a byte-level operation 
- Rationale 
  -  As simple as possible 
  - The complexity of the round key expansion plus the complexity of the other stages of AES ensure security

## AES Key Expansion

- Takes as input a four-word (16 byte) key and produces a linear array of 44 words (176 bytes) 
  - This is sufficient to provide a four-word round key for the initial AddRoundKey stage and each of the 10 rounds of the cipher 
-  Key is copied into the first four words of the expanded key 
  - The remainder of the expanded key is filled in four words at a time 
- Each added word w[i] depends on the immediately preceding word, w[i – 1], and the word four positions back, w[i – 4]
  - In three out of four cases a simple XOR is used 
  - For a word whose position in the w array is a multiple of 4, a more complex function is used

### Key Expansion Algorithm

- The Rijndael developers designed the expansion key algorithm to be resistant to known cryptanalytic attacks 
- Inclusion of a rounddependent round constant eliminates the symmetry between the ways in which round keys are generated in different rounds

#### The specific criteria that were used are

- Knowledge of a part of the cipher key or round key does not enable calculation of many other round-key bits 
- An invertible transformation 
- Speed on a wide range of processors 
- Usage of round constants to eliminate symmetries 
- Diffusion of cipher key differences into the round keys 
- **`Enough nonlinearity`** to prohibit the full determination of round key differences from cipher key differences only 
- Simplicity of description

### Implementation Aspects

- AES can be implemented very efficiently on an 8- bit processor 
- AddRoundKey is a bytewise XOR operation 
- ShiftRows is a simple byte-shifting operation 
- SubBytes operates at the byte level and only requires a table of 256 bytes 
- MixColumns requires matrix multiplication in the field GF($2^8$ ), which means that all operations are carried out on bytes

### Implementation Aspects

- Can efficiently implement on a 32-bit processor 
  - Redefine steps to use 32-bit words 
  - Can precompute 4 tables of 256-words 
  - Then each column in each round can be computed using 4 table lookups + 4 XORs 
  - At a cost of 4Kb to store tables 
  - Designers believe this very efficient implementation was a key factor in its selection as the AES cipher