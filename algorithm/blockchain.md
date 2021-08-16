# Blockchain

## Blockchain Basics

- It is originated from the paper called "[How to Time Stamp a Digital Document](https://www.anf.es/pdf/Haber_Stornetta.pdf)" written by Stuart Haber & W. Scott Stornetta in 1991.
- It is consisted of blocks which is linked by the hash value of its data.
  - Each Block chain can uses select a different hashing algorithm
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
- Consensus protocol is used to:
  - Protect the network from attacker by doing a list of check before adding new block
    - It uses either proof of work(POW) or proof of state(POS) protocol.
  - Solving the competing chains
    - Competing chains happens when two new block are mined at the same time
    - The block that has a new block added to it first will be accepted, the other one will be invalid and called orphaned block.
    - The group of nodes who finds a new block first proof it has more hashing(computing) power. Hence it get the reward.

## Cryptocurrency

- The name of the cryptocurrency is the name of the a protocol it applies.
  - Each one of them has a corresponding coin unit.
  - Block stores data about a series of current transactions that need to be stored. Transactions fees plus the new block's coin value will be paid to the miner.
- It has three layers: blockchain, protocol(coin), and token.
- It has its own monetary policy
  - It can be used to replace the banking system.
  - The Halving - the number of coins a new block contains will be halved after every certain amount of blocks are mines
    - After rounding, there will be a limited number of coins.
  - Block frequency is the average time it takes to mine a new block.
- Block frequency control
  - The difficulty will be adjusted after every certain amount blocks are found.
  - The initial difficulty is called the max target.
  - The difficulty can be calculated by dividing the current targets by the max target.
  - The difficulty will be adjusted automatically to fit the block frequency.
  - the current target is represented by the bit field. To calculate the target value from bit. convert it to hexadecimal number and convert the first to digit of the hexadecimal number into decimal. That number represents the length in bytes of the current target value in hexadecimal. Lastly, the rest digits(starting from the 3rd digit) of the hexadecimal number converted from bit will be used as the leading values of the current target value.
- Nonce is unsigned 32 bit number with 2^32 from 0 to around 4 billion
  - The largest nonce is called the max nonce
  - The nonce range is much smaller than than the hash range(10^77 combination)
  - An average mining machine can do 4 billion hashing in 40 second.
  - A timestamp is added to the block data for hashing to refresh the calculation every seconds
  - Only parts of the nonce will can be attempted in each second
- Mining Pool
  - Mining pool combined individual hashing power and assign a nonce range for guessing.
    - The reward will be assigned is proportional to its hashing power.
    - There is a fee for the mining pool service, everything will be managed automatically.
  - There is a transaction accelerator offered by mine pool provider. That helps the transaction get selected first.
  - For mine pools when it has really big hashing power. If all possible nonce is attempted within 1 second. The remaining time will be used for a block with different selection of transactions.
- Types of Mining Hardwares
  - CPU max 10 MH/s (Million Hashes per second)
  - GPU max 10 GH/s
  - ASIC over 1000 GH/s
    - special designed for a certain non memory based hashing algorithm, like Bitcoin.
- Mempool
  - Mempool stores all recent transactions distributed across the network
  - Block can stores transaction records picked from mempool
  - Transactions fee can be specified freely at the time of transactions
  - Transactions with low fee that have not been selected by miner to store in the block will be returned.
  - Miner picks transactions with highest fee first.
  - Only a certain amount of transactions can be selected. The size of a block is limited.
  - When a New transaction is made it will be added to the mempool.
  - When the transaction is selected by a block and the block is added to the chain the transaction is confirmed and removed from the mempool.
- The 51% attack
  - It happens when a large group of nodes maliciously join the mining and disconnect from the network then go back online when it has longer chain. It will make the chain people are using invalid. Fraud can happens when the new chain void some existing transaction using the old chain from outside.
  - Generally it takes 6 or more confirmation to make a transaction valid.
- (Unspent Transcation Outputs)UTXOs
  - UTXOs is the coins that send to the user which has not been sent to others.
  - The sum of all the UTXOs amount is the user's account balance.
  - The UTXOs amount from any transcation can be selected and sent to other users in a group.
    - The changes for the transcation can be obtained by sending it to the user itself.
    - If there is still amount remaining, it will be considered as transcation fee.
  - Each transcation is protected by Public/Private Key
    - Each user is uniquely identified by a private key.
    - Private key can be used to generate the public key.
    - Each transcation contains a signiture which is signed by the users private key.
    - The signiture is calculated using the private and the message content.
    - Transaction will be verified by the public key attached to the message.
    - The key info takes a large portion of the space in a block, it can be moved outside of the block with its own message services, this is called Segregated Witness (SegWit)
- A fork is a software change made to the blockchain.
  - Any UTXOs store before the fork will be valid for all branches.
  - A hard fork happens when user starts to add block to blockchain using a lossened protocol. The original chain won't accept the block. It will form a new chain on its own.
  - A soft fork happens when majority user starts to add block to blockchain using a tightened protocol. The users with the old protocol can't compete with marjority hence their blocks that doesn't obey the new protocol will become orphaned block.
    - It is often initiated the provider.
- HD Wallet
  - Hierarchically Deterministic Wallets
  - A master private key can be used to generate multiple private keys
  - Good for enhanced security
  - Good for organization which can distribute to employee.
  - There is a master public key that need to be keep secret. It can access all other public key and be used by auditor.
- Mnemonic is a series of words used to generate a sequence of accounts and its public key and private key.
  - It is used for the users to easily remember all the accounts it can have with few words.
  - The mnemonic can be converted into account info by using this [tool](https://iancoleman.io/bip39/)

## Smart Contract

- It is a program that runs across the blockchian nodes.
- For a cryptocurrency supports smart contract, each node has:
  - history of all smart contracts
  - histrory of all transcations
  - the current state of all smart contracts
- Decentralized Application - The frontend of smart contract.
- Web 3.0 utilize distributed web servers.
- VMs are used to encapsulate the smart contract running environment to prevent the spread of virus or infinite loops.
- Gas is used to pay by the users for the execution of smart contract apps throughout the blockchain.
  - Each type of operation consume a specified amount of gas
    - It is often listed in a spreadsheet, the units of gas required for operations like addition, comparision are specified
    - storing data also requires gas
  - Use gas instead of coins because the coin value changes frequently
  - Gas price is the amount of coins required for each gas unit.
  - Gas limit is the maximum amount of gas unit the contract can consume.
    - The app will stop when it is about to consume gas beyond the limit
- Decentralized Autonomous Organization (DAO) - an organization that runs by itself based on rules set in smart contracts.
- A token is a currency that is usually purchased from a startup by coins. The token can be used to purchase services from the startup.
  - Tokens are release during (Initial Coin Offerring)ICO
  - The amount token release from ICO is limited.
  - After the token has been paid for services, the token can be sell by the company again.
  - [Click Here](https://coinmarketcap.com) to see a list of popular project, their business plan are written in the white paper.
- The deployed bytecode of the smart contract is public

## Common Cryptocurrency Platform

- Go to [Blockchain.com](https://www.blockchain.com) to see more info.

#### Bitcoin

- It uses SHA-256
- Works well with ASIC
- It can run programs written in Bitcoin Script
  - It is not Turing-Complete, it does not support loops
- 1MB block size
- Adopted SegWit on August 24th, 2017
- In August, 2017. Some user hard fork to BitCoinCash with 8 MB block size. While the official BitCoin still uses 1 MB.
- October 24th, 2017 Some user hard fork from BitCoin to prevent mining with ASIC.
- Transcation can be made to public key and BitCoin Address.
  - Bitcoin Address is the Hash code calculated from public key using SHA-256.

#### Ethereum

- Its algorithm requires access of memory, it uses GPU
- It can run programs written in Solidity
  - It is Turing-Complete, it supports all basic programming syntax
- It supports smart contract.
  - `Solidity` is the programming language for writing Ethereum smart contracts.
- A DAO is attacked due to error in the smart contract. In July 2017, it split into
  - Ethereum Classic - unchanged
  - Ethereum - Allows to go back and fix errors in smart contract
- The name of the cryptocurrency in Ethereum is called `ether`
  - `wei` is the smallest unit for `ether`
  - There are many others units. A conversion tool is available [here](https://www.etherchain.org/tools/unitConverter)
- It uses a 12 words mnemonic
- Beside the main ethereum network, there are test networks that works with fake coins and tokens.
  - Ropsten Test Network
  - Kovan Test Network
  - Rinkeby Test Network
    - [Click here](https://faucet.rinkeby.io) and complete one of the tasks listed to get fake Rinkeby ethers.
- [Etherscan](https://etherscan.io) can be used to view all transaction on the Ethereum network
  - add test network name in the subdomain can show tracsactions made on test networks
- The extension `metamask` for Google Chrome browser can be used to register and manage Ethereum account
  - Enter a new password at the first time will generate a new account
  - `metamsk` works with test networks, local network and custom RPC(remote network at custom address)
    - One account can be used across all networks
- `web3.js` is a `node.js` library that web servers use to interact with all `Ethereum` networks.
  - `web3` establish connection with blockchain networks using a `provider` proviced by various networks
- For any smart contract, modifying values inside the contract is a transaction and will consume ether from the user account.
  - This action takes time to excute(around 15 seconds)
