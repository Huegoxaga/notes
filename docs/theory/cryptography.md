# Cryptography

- Cryptography is about constructing and analyzing protocols that prevent third parties(called adversaries) or the public from reading private messages.

## Caesar Cipher

It is a type of substitution cipher in which each letter in the plaintext is shifted to a certain number of places down the alphabet.

## Vigenère cipher

It is a method to encrypt alphabetic text with a key. The key will determine the transition of each character in the text by matching the text repeatly.
Specials characters are not used is this type of cipher.

## Hashing Algorithm

- It generates value or values from a string of text using a hash function.
  Hash is a one way encryption algorithm, the original message cannot be calculated based on the hash value.
- It can be used to generate two hash values (checksum) for files or messages before and after they are transmitted. So the end users will know if the message is unchanged during the transmission.
- The hash code for the original message will be sent along with the message for the end user to compare.
- It can also be used to generate hashed password that to be stored on servers.

### Cryptographic Hash Functions

- MD5 - mainly used for verifying if a file has been unaltered.
- SHA-1

## Salted Hashing Algorithm

- Salt is a random string that is concatenated with the message before hashing it.
  Both the salt value and the result of the hash function are stored in the database on the host.
- It will make the dictionary attack difficult because all possible salts also need to be hashed with a single password.
- It protects people who have the same password on multiple machines because although passwords are the same, salts are different.
