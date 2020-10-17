# Classical Encryption

[toc]

## Symmetric Cipher Model

### Terminology

- Plaintext

  - An original message

- Ciphertext

  - The coded message

- Enciphering/Encryption

  - The process of converting from plaintext to ciphertet

- Deciphering/Decryption

  - Restoring the plaintext from the ciphertext

- Cryptography

  - The are of study of the many schemes used for encryption

- Cryptographic System/Cipher

  - A scheme

- Cryptanalysis

  - Techniques used for deciphering a message without any knowledge of the enciphering details

- Cryptology

  - The areas of crytography and cryptanalysis

    

### Simplified Model of Symmetric Encryption

<img src="Resources/43.jpg" style="zoom:70%;" />



- There are two requirements for secure use of conventional encryption:

  - A strong encryption algorithm

  - Sender and receiver must have obtained copies of the secret key in a secure fashion and must keep the key secure

    

- Model of Symmetric Cryptosystem

<img src="Resources/44.jpg" style="zoom:70%;" />

- Classification of Cryptanalysis Methods

<img src="Resources/45.jpg" style="zoom:70%;" />

## Substitution Technique

- Is one in which the letters of plaintext are replaced by other letters or by numbers or symbols
- If the plaintext is viewed as a sequence of bits, then substitution involves replacing plaintext bit patterns with ciphertext bit patterns

### Monoalphabetic Ciphers

#### Caesar Cipher

- Simplest and earliest known use of a substitution cipher 
- Used by Julius Caesar 
- Involves replacing each letter of the alphabet with the letter standing three places further down the alphabet 
- Alphabet is wrapped around so that the letter following Z is A

- Example:

  plain : 	meet		me	after		the		toga		party

  cipher:	PHHW	 PH	DIWHU	WKH	WRJD	SDUWB

- Define Transformation as:

<img src="Resources/46.jpg" style="zoom:70%;" />

- Mathematically give each letter a number

  <img src="Resources/47.jpg" style="zoom:70%;" />

- Algorithm can be expressed as :
  $$
  c = E(3,p)=(p+3)\mod (26)
  $$

- A shift may be of any amount,so that the general caesar algorithms is:
  $$
  \begin{align}
  & C = E(k,p)=(p+k)\mod 26 \\ 
  & where\quad t\quad takes\quad on\quad a\quad value\quad in\quad the\quad range\quad 1\quad to\quad 25
  \end{align}
  $$
  
- The decryption algorithm is simply:
  $$
  P = D(k,C)=(C-k)\mod 26
  $$

#### Permutation Cipher

- Permutation

  Of a finite set of elements S is an ordered sequence of all
  the elements of S , with each element appearing exactly
  once.

<img src="Resources/48.jpg" style="zoom:70%;" />

- If the “cipher” line can be any permutation of the 26 alphabetic characters, then there are 26! or greater than $4 * 10^{26}$ possible keys
  - This is 10 orders of magnitude greater than the key space for DES 
  - Approach is referred to as a monoalphabetic substitution cipher because a single cipher alphabet is used per message
- Easy to break because they reflect the frequency data of the original alphabet
- Digram 
  - Two-letter combination 
  - Most common is th

- Trigram 
  - Three-letter combination 
  - Most frequent is the 

-  Countermeasures
  1. encrypt multiple letters of plaintext (chunk) at once.
  2. provide multiple substitutes (homophones) for a single letter 

#### First countermeasure: Playfair Cipher

- Best-known multiple-letter encryption cipher 
- Treats digrams in the plaintext as single units and translates these units into ciphertext digrams 
- Based on the use of a 5 x 5 matrix of letters constructed using a keyword 
- Invented by British scientist Sir Charles Wheatstone in 1854 
- Used as the standard field system by the British Army in World War I and the U.S. Army and other Allied forces during World War II

- Fill in letters of keyword (minus duplicates) from left to right and from top to bottom, then fill in the remainder of the matrix with the remaining letters in alphabetic order

<img src="Resources/49.jpg" style="zoom:70%;" />



## Second countermeasure: Polyalphabetic Ciphers

Improves on the simple monoalphabetic technique by using different monoalphabetic substitutions as one proceeds through the plaintext message

<img src="Resources/50.jpg" style="zoom:70%;" />

### Vigenère Cipher

- Best known and one of the simplest polyalphabetic substitution ciphers 
- In this scheme the set of related monoalphabetic substitution rules consists of the 26 Caesar ciphers with shifts of 0 through 25 
- Each cipher is denoted by a key letter which is the ciphertext letter that substitutes for the plaintext letter a

#### Example

- To encrypt a message, a key is needed that is as long as the message 

- Usually, the key is a repeating keyword 

- For example, if the keyword is deceptive, the message “we are discovered save yourself” is encrypted as

  ​						key: deceptive deceptive deceptive 

  ​						plaintext: wearedisc overedsav eyourself 

  ​						ciphertext: ZICVTWQNG RZGVTWAVZ HCQYGLMGJ

  (Sending message divide by the length of key to get he plaintext. Then plaintext change to the ciphertext by Caesar Cipher.)

### Vigenère Autokey System

- A keyword is concatenated with the plaintext itself to provide a running key

- Example: 

  key: deceptivewearediscoveredsav 

  plaintext: wearediscoveredsaveyourself 

  ciphertext: ZICVTWQNGKZEIIGASXSTSLVVWLA

- Even this scheme is vulnerable to cryptanalysis 
  - Because the key and the plaintext share the same frequency distribution of letters, a statistical technique can be applied

### Vernam Cipher

<img src="Resources/51.jpg" style="zoom:70%;" />

### One-Time Pad

- Improvement to Vernam cipher proposed by an Army Signal Corp officer, Joseph Mauborgne 
- Use a random key that is as long as the message so that the key need not be repeated 
- Key is used to encrypt and decrypt a single message and then is discarded

- Each new message requires a new key of the same length as the new message 
- Scheme is unbreakable 
- Produces random output that bears no statistical relationship to the plaintext 
- Because the ciphertext contains no information whatsoever about the plaintext, there is simply no way to break the code

#### Difficulties

- The one-time pad offers complete security but, in practice, has two fundamental difficulties:
  - There is the practical problem of making large quantities of random keys 
    - Any heavily used system might require millions of random characters on a regular basis

- Mammoth key distribution problem 
  - For every message to be sent, a key of equal length is needed by both sender and receiver

- Because of these difficulties, the one-time pad is of limited utility 
  - Useful primarily for low-bandwidth channels requiring very high security 
  - The one-time pad is the only cryptosystem that exhibits perfect secrecy (see Appendix F)

## Transposition Cipher

### Rail Fence Cipher

- Simplest transposition cipher 

- Plaintext is written down as a sequence of diagonals and then read off as a sequence of rows 

- To encipher the message “meet me after the toga party” with a rail fence of depth 2, we would write: 

  ​			m e m a t r h t g p r y 

  ​				e t e f e t e o a a t 

  

  Encrypted message is: 

  ​	MEMATRHTGPRYETEFETEOAAT

### Row Transposition Cipher

- Is a more complex transposition 

- Write the message in a rectangle, row by row, and read the message off, column by column, but permute the order of the columns

  - The order of the columns then becomes the key to the algorithm

    

    ​		Key :					4	3	1	2	5	6   7

    ​		Plaintext:             a	t	  t	a	c	k	p

    ​									o	s	t	p	 o	n	e

    ​									d	u	n	t	 i	 l	 t

    ​									w	o	a	m  x	y	z                               

    ​		Cliphertext:          TTNAAPTMTSUOAODWCOIXKNLYPETZ

## Steganography Techniques

- Character marking 
  - Selected letters of printed or typewritten text are over-written in pencil 
  - The marks are ordinarily not visible unless the paper is held at an angle to bright light 
- Invisible ink 
  - A number of substances can be used for writing but leave no visible trace until heat or some chemical is applied to the paper 
- Pin punctures 
  - Small pin punctures on selected letters are ordinarily not visible unless the paper is held up in front of a light 
- Typewriter correction ribbon 
  - Used between lines typed with a black ribbon, the results of typing with the correction tape are visible only under a strong light 

### Steganography vs. Encryption

- Steganography has a number of drawbacks when compared to encryption
  - It requires a lot of overhead to hide a relatively few bits of information 
  - Once the system is discovered, it becomes virtually worthless

- The advantage of steganography
  - It can be employed by parties who have something to lose should the fact of their secret communication (not necessarily the content) be discovered
  - Encryption flags traffic as important or secret or may identify the sender or receiver as someone with something to hide