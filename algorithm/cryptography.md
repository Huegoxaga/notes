# Cryptography

- Cryptography is about constructing and analyzing protocols that prevent third parties(called adversaries) or the public from reading private messages
- Greek: kryptos (hidden) + grafo (write)
- Cryptography is aim to hide the meaning of messages, while steganography is aim to hide the existence of messages

## Random Number

- Random number is important in cryptography, example use cases:
  - Keys for public-key algorithms
  - The stream key for a symmetric stream cipher
  - A symmetric key for use as a temporary session key or in creating a digital envelope
- Requirements:
  - Randomness
    - Uniform distribution: frequency of occurrence of each number should be approximately the same
    - Independence: no one value in the sequence can be inferred from others
  - Unpredictability
    - Each number is statistically independent of others in the sequence
    - Future elements of sequence unpredictable based on the basis of earlier elements
- Source of random number
  - Pseudo-random number generator (PRNG)
    - Produces sequences that satisfy randomness tests
    - Not truly random – deterministic based on a seed value
      - Algorithms are deterministic and therefore produce sequences of numbers that are not statistically random
    - Fast operation
  - True random number generator (TRNG)
    - Uses a non-deterministic source to produce randomness
    - Most operate by measuring unpredictable natural processes, e.g. radiation, gas discharge tubes, leaky capacitors, thermal noise
    - Increasingly provided on modern processors

## Caesar Cipher

- It is a type of substitution cipher in which each letter in the plaintext is shifted to a certain number of places down the alphabet.

## Vigenère Cipher

- It is a method to encrypt alphabetic text with a key. The key will determine the transition of each character in the text by matching the text repeatly.
- Specials characters can not used in this type of cipher.

## Hashing Algorithm

- A hash function generally turns an arbitrary-length piece of data and returns a fixed-length "fingerprint" of the data
- Message is usually padded out to a multiple of some fixed length (e.g. 1024 bits) and padding includes the length of the message (increasing the difficulty to generate a collision)
  - Fingerprints are also called: digests, hash sums, hash values, hash codes, or hashes
- It is NOT "encryption", as the original cannot be recovered; it is a one-way operation
- A secret key is not used as an input to the hash (unlike with MACs)
- Use cases
  - It can be used to generate two hash values (checksum) for files or messages before and after they are transmitted. So the end users will know if the message is unchanged during the transmission
  - The hash code for the original message will be sent along with the message for the end user to compare
  - It can also be used to generate hashed password that to be stored on servers
- Secure Hash Function Requirements
  - Produces a fixed-length output
  - Speed: hash function H(x) should be relatively easy to compute for any given input x
  - One-way/First pre-image resistant (given h, a hash value)
    - It should be infeasible to find an input x such that H(x) = h
    - hard to recover original data
  - Second pre-image resistant (given input x)
    - It should be infeasible to find y ≠ x such that H(y) = H(x)
    - hard to find another raw data with the same output
  - Collision resistant
    - It should be difficult to find any pair (x,y) such that H(y) = H(x)
    - For two different files, collision happens when they have the same hash output
- Salted Hashing Algorithm
  - Salt is a random string that is concatenated with the message before hashing it.
    Both the salt value and the result of the hash function are stored in the database on the host.
  - It will make the dictionary attack difficult because all possible salts also need to be hashed with a single password.
  - It protects people who have the same password on multiple machines because although passwords are the same, salts are different

### Message Digest algorithms

- `MD2`, `MD4` were likely to be insecure.
- Mainly used for verifying if a file has been unaltered.
- MD5
  - It was designed by Ronald Rivest in 1991 to replace an earlier hash function MD4, and was specified in 1992 as RFC 1321.
  - Collisions against MD5 can be calculated within seconds which makes the algorithm unsuitable for most use cases where a cryptographic hash is required.
  - MD5 produces a digest of 128 bits (16 bytes). with 512 bit block size.

### Secure Hash Algorithms

- The Secure Hash Algorithms are a family of cryptographic hash functions selected and published by the National Institute of Standards and Technology (NIST) as a U.S. Federal Information Processing Standard (FIPS), including:
  - `SHA-0`: A retronym applied to the original version of the 160-bit hash function published in 1993 under the name "SHA". It was withdrawn shortly after publication due to an undisclosed "significant flaw" and replaced by the slightly revised version SHA-1.
  - `SHA-1`: A 160-bit hash function which resembles the earlier MD5 algorithm. This was designed by the National Security Agency (NSA) to be part of the Digital Signature Algorithm. Cryptographic weaknesses were discovered in SHA-1, and the standard was no longer approved for most cryptographic uses after 2010.
  - `SHA-2`: A family of two similar hash functions, with different block sizes, known as SHA-256 and SHA-512. They differ in the word size; SHA-256 uses 32-byte words where SHA-512 uses 64-byte words. There are also truncated versions of each standard, known as SHA-224, SHA-384, SHA-512/224 and SHA-512/256. These were also designed by the NSA.
    - `SHA-256`
      - It takes 256-bit memory and has 64 Hexdecimal digits.
      - This algorithm generates a unique hash for all files.
  - `SHA-3`: A hash function formerly called Keccak, chosen in 2012 after a public competition among non-NSA designers. It supports the same hash lengths as SHA-2, and its internal structure differs significantly from the rest of the SHA family.
- [Click](https://www.staff.science.uu.nl/~tel00101/liter/Books/CrypCont.pdf) to see the details about SHA algorithm in Chapter 1.
- Requirement for a good Hash Algorithms
  - One-way - the original data can not be retrieved from the hash code.
  - Deterministic - the data will generate the same hash code.
  - Fast Computation
  - The Avalanche Effect - One small change in the data will completely change the hash code.
  - Must withstand collisions - Two different input data rarely generate the same hash code.

## Message Authentication

- Verifies authenticity of the message
  - Contents are not altered
  - From an authentic source
  - Timely (not replayed) and in the correct sequence
- For this use case the content doesn't have to be protected

### Message Authentication Code (MAC)

- Use a secret key to generate a small block of data appended to the message, called the MAC
- Sender will share the algorithm and the secret key to the receiver, if the receiver find the MAC appended to the message match what it calculate by using the secret key, the message is authenticated, as a result
  - The recipient can be sure the message is unaltered
  - The recipient can be sure of the sender’s identity
  - The recipient can be sure of the proper block sequence if sequence numbers are used (e.g. TCP)
- Can be generated using DES-CBC (using the last 16 or 32 bits of ciphertext as the MAC)

## Symmetric Encryption

- It utilizes symmetric-key algorithms that encrypt plaintext and decrypt ciphertext with the same cryptographic keys
- Secret key is required by both parties when using symmetric encryption
  - Both party should store this key securely
- Caesar Cipher is the earilest and simpleset
- It is faster than asymmetric encryption
- Many cryptographic systems use symmetric-key algorithms internally
- To brutal force symmetric encryption half of all possible keys must be attempted
  - One must know what result to expect, so it might not be feasiable for compressed, encoded data
- Cryptanalysis Attack
  - Study of circumventing encryption; codebreaking
  - Relies on the nature of the algorithm
  - Some knowledge of plaintext's characteristics
  - Some sample plaintext-ciphertext pairs
  - Attempts to deduce specific plaintext or key used
  - If successful, all future and past messages encrypted with that key are compromised
- Block Ciphers
  - Processes plaintext input in fixed-size blocks, and produces a block of ciphertext of equal size for each plaintext block
  - Longer plaintexts are broken up into these fixed-size blocks
  - A constant transformation is applied to each plaintext block to produce the ciphertext blocks
  - All of the below algorithms use block cipher except `RC5`
  - Weakness
    - Electronic Code Book (ECB) can be used as a dictionary
    - can only applied to units of data larger than block size
- Stream Ciphers
  - Processes input continuously (rather than a block at a time)
  - XORs plaintext bits with keystream, encrypts plaintext (often) 1 byte at a time
  - Keystream is a pseudorandom sequence generated from the key
  - Key reuse is not recommended
  - Typically faster than a block cipher
  - Uses less code than a block cipher
  - Commonly in use: ChaCha20, RC4 (deprecated)

### DES

- 64 bits block size for plaintext/ciphertext
- DES key size is 56 bits
- DES has a 56-bit key plus an 8-bit parity
- NIST FIPS PUB 46, 1977
- Data Encryption Algorithm, DEA
- Public algorithm submitted by IBM Labs
- 56-bit keys are too small for present-day use
  - It is now considered vulnerable

### Triple-DES (3DES)

- It is an enhanced version of `DES`
- 64 bits block size for plaintext/ciphertext
- It has double or triple sized keys than `DES`
  - Repeats basic DES algorithm 3 times using either 2 or 3 unique keys (112 or 168 bits)
- NIST FIPS PUB 46-3, 1999
- Convenient since the DES algorithm was widely used
- Slow due to 3x DES operations
- A meet-in-the-middle attack can cause 3DES to be brute-forced with fewer operations than expected
  - Effective key strength of 3DES is only 112 bits as a result

### RC5

- Stream cipher
- Plaintext/ciphertext block size can be either 32, 64, 128 bits
- Key size is `0 - 2040` bits

### Blowfish

- Plaintext/ciphertext block size can be either 64 bits
- Key size is `32 - 448` bits

### Advanced Encryption Standard(AES)

- Mostly used symmetric encryption
- A symmetric block cipher chosen by the U.S. government
- NIST(The National Institute of Standards and Technology) set the standard and select algorithm for AES
- There was an open competition for a new standard
  - Winner is Belgian algorithm named Rijndael
  - Published by NIST FIPS PUB 197, 2001
- Plaintext/ciphertext block size is 128-bit
- The encryption process is based on rounds
  - one round includes procedures like subsititution, transposition, mixing of the input plain text, and transforming it into the final output of cipher text.
- AES has three standards.
  - `AES-128` - using 128 bits key size, has 10 rounds.
  - `AES-192` - using 192 bits key size, has 12 rounds.
  - `AES-256` - using 256 bits key size, has 14 rounds.

## Asymmetric Encryption

- It utilizes public-key algorithms and uses a public & private key pairs
  - Public keys are public, everyone can have it
  - Private keys are private, only the owner can have it
- Keys are mathematically-related, but the private key cannot be derived from the public key
- This design can achieve the following tasks:
  - Encryption - Messages encrypted with a user’s public key can only be decrypted with the user’s corresponding private key
  - Authentication - a user encrypting a message with their private key can only be decrypted using the user's corresponding public key (e.g. digital signatures)
    - The hashed message is used, instead of the entire plaintext
  - Secure Communication with two pairs of key - Sender use random generated secret key to encrypt message, the use recipient's public key to encrypt the random secret key, combine and send it to recipient. Then, recipient use its secret key to get the sender's random secret key to decrypt the message (known as digital envelope)
- It is more secure than symmetric encryption since the private key is kept secret
- Basic Public-Key Cryptosystem Requirements
  - Easy for Bob to create a public + private key pair
  - Easy for Alice to compute ciphertext by encrypting plaintext message with Bob’s public key
  - Easy for Bob to decrypt ciphertext using his private key
  - Hard for adversary to derive the private key from someone's public key
  - Hard to recover the plaintext message from having only the ciphertext and the public key
  - Either the public or the private key can be used for encryption or decryption (optional)

### Diffie-Hellman key exchange protocol(DH)

- The first public-key algorithm, invented in 1976.

### DSS (Digital Signature Standard)

- It utilize the Authentication ability of the asymmetric encryption.
- A tag with user info is encrypted with a private key which can only be decrypted by the public key. The public key and the tag will be sent to others to check the senders' authenticity.
- This can also be achieved by hashing algorithm.
  - It will provide additional feature like checking the completeness of the tag.
- `X.509` is a standard defining the format of public key certificates.
  - The certificates are special tags containing hostname info, or organization info, or individual owner info.
  - When a certificate is signed by a trusted certificate authority, or validated by other means, certificate owner can rely on the public key it contains to establish secure communications with others.
  - `X.509` is defined by the International Telecommunications Union's Standardization sector (ITU-T), and is based on ASN.1, another ITU-T standard.

### Various password-authenticated key agreement techniques

### RSA encryption algorithm(Rivest-Shamir-Adleman)

- RSA keys has the following standard sizes:
  - 512 bits - Low-strength key
  - 1024 bits - Medium-strength key
  - 2048 bits - High-strength key
  - 4096 bits - Very high-strength key
