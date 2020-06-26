# Cryptography

- Cryptography is about constructing and analyzing protocols that prevent third parties(called adversaries) or the public from reading private messages.

## Caesar Cipher

- It is a type of substitution cipher in which each letter in the plaintext is shifted to a certain number of places down the alphabet.

## Vigenère Cipher

- It is a method to encrypt alphabetic text with a key. The key will determine the transition of each character in the text by matching the text repeatly.
- Specials characters can not used in this type of cipher.

## Hashing Algorithm

- It generates value or values from a string of text using a hash function.
  Hash is a one way encryption algorithm, the original message cannot be calculated based on the hash value.
- It can be used to generate two hash values (checksum) for files or messages before and after they are transmitted. So the end users will know if the message is unchanged during the transmission.
- The hash code for the original message will be sent along with the message for the end user to compare.
- It can also be used to generate hashed password that to be stored on servers.

### Common Usage

##### Message Digest algorithms

- `MD2`, `MD4` were likely to be insecure.
- Mainly used for verifying if a file has been unaltered.
- MD5
  - It was designed by Ronald Rivest in 1991 to replace an earlier hash function MD4, and was specified in 1992 as RFC 1321.
  - Collisions against MD5 can be calculated within seconds which makes the algorithm unsuitable for most use cases where a cryptographic hash is required.
  - MD5 produces a digest of 128 bits (16 bytes). with 512 bit block size.

##### Secure Hash Algorithms

- The Secure Hash Algorithms are a family of cryptographic hash functions selected and published by the National Institute of Standards and Technology (NIST) as a U.S. Federal Information Processing Standard (FIPS), including:
  - `SHA-0`: A retronym applied to the original version of the 160-bit hash function published in 1993 under the name "SHA". It was withdrawn shortly after publication due to an undisclosed "significant flaw" and replaced by the slightly revised version SHA-1.
  - `SHA-1`: A 160-bit hash function which resembles the earlier MD5 algorithm. This was designed by the National Security Agency (NSA) to be part of the Digital Signature Algorithm. Cryptographic weaknesses were discovered in SHA-1, and the standard was no longer approved for most cryptographic uses after 2010.
  - `SHA-2`: A family of two similar hash functions, with different block sizes, known as SHA-256 and SHA-512. They differ in the word size; SHA-256 uses 32-byte words where SHA-512 uses 64-byte words. There are also truncated versions of each standard, known as SHA-224, SHA-384, SHA-512/224 and SHA-512/256. These were also designed by the NSA.
  - `SHA-3`: A hash function formerly called Keccak, chosen in 2012 after a public competition among non-NSA designers. It supports the same hash lengths as SHA-2, and its internal structure differs significantly from the rest of the SHA family.

## Salted Hashing Algorithm

- Salt is a random string that is concatenated with the message before hashing it.
  Both the salt value and the result of the hash function are stored in the database on the host.
- It will make the dictionary attack difficult because all possible salts also need to be hashed with a single password.
- It protects people who have the same password on multiple machines because although passwords are the same, salts are different.

## Symmetric encryption

- It utilizes symmetric-key algorithms that encrypt plaintext and decrypt ciphertext with the same cryptographic keys.
- Secret key is required by both parties when using symmetric encryption.
- Caesar Cipher is the earilest and simpleset.
- It is faster than asymmetric encryption.
- Many cryptographic systems use symmetric-key algorithms internally.

### Common Usage

##### Advanced Encryption Standard(AES)

- A symmetric block cipher chosen by the U.S. government.
- NIST(The National Institute of Standards and Technology) set the standard and select algorithm for AES.
  - The cipher are required to handle data in blacks of 128 bits.
- The encryption process is based on rounds
  - one round includes procedures like subsititution, transposition, mixing of the input plain text, and transforming it into the final output of cipher text.
- AES has three standards.
  - `AES-128` - using 128 bits key size, has 10 rounds.
  - `AES-192` - using 192 bits key size, has 12 rounds.
  - `AES-256` - using 256 bits key size, has 14 rounds.

## Asymmetric encryption

- It utilizes public-key algorithms and uses a public & private key pairs.
  - Public keys are public, everyone can have it.
  - Private keys are private, only the owner can have it.
- This design can achieve two tasks:
  - Encryption - Private key can decrypt content that encrypted with public key.
  - Authentication - Only the holder of the paired private key can be verified by the public key.
- it is more secure than symmetric encryption since the private key is kept secret.

### Common Usage

##### Diffie-Hellman key exchange protocol(DH)

- The first public-key algorithm, invented in 1976.

##### DSS (Digital Signature Standard)

- It utilize the Authentication ability of the asymmetric encryption.
- A tag with user info is encrypted with a private key which can only be decrypted by the public key. The public key and the tag will be sent to others to check the senders' authenticity.
- This can also be achieved by hashing algorithm.
  - It will provide additional feature like checking the completeness of the tag.
- `X.509` is a standard defining the format of public key certificates.
  - The certificates are special tags containing hostname info, or organization info, or individual owner info.
  - When a certificate is signed by a trusted certificate authority, or validated by other means, certificate owner can rely on the public key it contains to establish secure communications with others.
  - `X.509` is defined by the International Telecommunications Union's Standardization sector (ITU-T), and is based on ASN.1, another ITU-T standard.

##### Various password-authenticated key agreement techniques

##### RSA encryption algorithm(Rivest-Shamir-Adleman)

- RSA keys has the following standard sizes:
  - 512 bits - Low-strength key
  - 1024 bits - Medium-strength key
  - 2048 bits - High-strength key
  - 4096 bits - Very high-strength key
