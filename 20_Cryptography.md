## Terms

- Clear text / plaintext : the unencrypted data
- Cipher text : the encrypted data
- Key : specifies the transformation of data for encryption / decryption ("key" is not synonymous with "password", although a password can
 in fact be used as a key)

#### Symmetric cryptography

- Use the same key for the encryption and the decryption
- Symmetric-key either use stream cipher and block cipher
- Popular algorithms: AES, DES


#### Asymmetric / Public Key cryptography

- Two key used: public and private
- Public key is publically known to everyone, issued by Public Key Infrastructure (PKI) and use to encrypt the data
- Private key is a secret for the public,only known by the owner and it is used to decrypt the data
- Asymmetric crytography delivers confidentiality, integrity, authenticity and non-repudation
- Popular algorithms : RSA, DSA and Diffie-Hellman

### Cipher

- Cipher is an algorithm for performing encryption and decryption

Methods:

#### Substitution Cipher

- Every character is substituded with another one
- More on [Wikipedia](https://en.wikipedia.org/wiki/Substitution_cipher)
- Example cipher : [Caesar cipher](https://en.wikipedia.org/wiki/Caesar_cipher)
- Example:

```
Plaintext :  THE QUICK BROWN FOX JUMPS OVER THE LAZY DOG
Ciphertext : QEB NRFZH YOLTK CLU GRJMP LSBO QEB IXWV ALD

Key : right shift of 3 
```

#### Transposition Cipher

- The positions held by units of plaintext are shifted according to a regular system
- Example cipher [Rail Fence cipher](https://en.wikipedia.org/wiki/Rail_fence)
- Example:

```
Clear text: WE ARE DISCOVERED. FLEE AT ONCE

W . . . E . . . C . . . R . . . L . . . T . . . E
. E . R . D . S . O . E . E . F . E . A . O . C .
. . A . . . I . . . V . . . D . . . E . . . N . .

Ciphertext: WECRLTEERDSOEEFEAOCAIVDEN
```

#### Polyalphabetic Cipher

- Based on substitution
- Using multiple substitution alphabets
- Example cipher : [Vigenère cipher](https://en.wikipedia.org/wiki/Vigen%C3%A8re_cipher)

#### Stream Cipher

- Text digits are combined with a pseudorandom cipher digit stream (keystream)
- Each plaintext digit is encrypted one at a time with the corresponding digit of the stream
- 2 type:
- **Synchronous Stream Ciphers** : stream of pseudo-random digits is generated independently of the plaintext and ciphertext 
messages, and then combined with the plaintext (to encrypt) or the ciphertext (to decrypt)
- **Self-Synchronizing Stream Cipher** : uses several of the previous N ciphertext to compute the keystream
- Example cipher: RC4

#### Block Cipher

- Operating on fixed-length groups of bits, called a block, with an unvarying transformation that is specified by a symmetric key
- Example cipher: AES, DES

# Stream Cipher

## RC4

- Designed in 1987, leaked in 1994
- Used in SSL, WEP
- Simple amd fast algorithm
- RC4 generates a pseudorandom stream of bits (a keystream) and combining it with the plaintext using bit-wise exclusive-or for 
encryption
- The permutation is initialized with a variable length key, typically between 40 and 2048 bits
- Marked as insecure


# Symmetric Algorithms

## Data Encryption Standard (DES)

- Introduced in 1975
- Standardized in 1977
- Problem with DES: short key length (56 bits)
- Now considered as insecure
- Improved version: Triple DES (involves DES three times)
- Problem with Triple DES: slow, compute heavy

#### Parameters

|   Parameter       |   Value  |
|+-----------------+|+--------+|
|   Block size      | 64 bits  |
|   Key size        | 56 bits  |
|   No. of rounds   |    16    |


## Advanced Encryption Standard (AES)

- First published in 1998
- Became a federal government standard in 2002
- First approved (and only) publicly accessible cipher approved by the NSA for top secret information

#### Parameters

|      Parameter    |    AES-128 value   |    AES-192 value  |    AES-256 value   |
|+-----------------+|+------------------+|+-----------------+|+------------------+|
|    Block size     |      128 bits      |      128 bits     |      128 bits      |
|    Key size       |      128 bits      |      192 bits     |      256 bits      |
|   No. of rounds   |         10         |       12          |         14         |

