# Block Chain

- It is originated from the paper called "[How to Time Stamp a Digital Document](https://www.anf.es/pdf/Haber_Stornetta.pdf)" written by Stuart Haber & W. Scott Stornetta in 1991.
- It is consisted of blocks which is linked by the hash value of its data.
  - Block chain uses SHA-256 as its hashing algorithm
  - Each block stores a block number, some data, a hash value and a previous hash value which points to the prevous block.
  - The hash value of a block is calculated from the block number, data and previous hash.
- The first block among all linked blocks is called the genesis block, it has the previous hash value of all zeros.
- Immutable Ledger - is an application of block chain, it is used to prevent and changes made to the ledgers.
  - Each record in the ledger is stored as a block in a block chain.
- Distributed P2P network will share and sync local block chain to devices across the network constantly, when any block chain is altered and become invalid. The valid block chain that majority has will be used to overwrite the invalid block chain.
- Mining
  - Nonce (Number only used once), Each block has an additional field called Nonce, it is also used to calculate the has for the block
  - Mining the process to guess the nonce number by brutal-forcing in order to let the generated hash lay within a target range
    - The range is generally a threshold value which the generated hash has to be smaller than it.
    - The range is effect throughout the block chain.
    - The nonce value that makes the hash value hit the target is called the golden knot.
  - Then the block with the valid nonce value will be accepted by the block chain.
  - Byzantine Fault Tolerance - is the property of a distributed system that is able to resist the class of failures derived from the Byzantine Generals’ Problem. This means that a BFT system is able to continue operating even if some of the nodes fail or act maliciously.
    - Byzantine Generals’ Problem - An amry is consisted of many generals, each general can make a decision, the decision made by the most general will be accepted. The question is how many traitors can they have among the generals that won't affect the final decision.
