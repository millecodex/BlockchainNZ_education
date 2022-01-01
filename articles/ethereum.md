[↰ back](https://github.com/millecodex/BlockchainNZ_education#readme)

# What is Ethereum?
First, a brief history of the problems that Vitalik Buterin was looking to solve. 

Bitcoin provided a solution to the double-spend problem of creating digital cash by using proof-of-work mining to both maintain the state of the ledger and allow open participation in the network based on computing power. By assigning value to these digitally scarce coins the ledger can be used as a monetary system. This works great for money but comes up short when using Bitcoin's scripting language to make simple extensions such as a decentralized exchange -- how to determine the NZD/BTC rate? or how to do some arbitrary calculation, e.g. what is the probability that your game character encounters a villan?

While writing for *Bitcoin Weekly* and co-founding [*Bitcoin Magazine*](https://bitcoinmagazine.com/), Vitalik saw the limitations in Bitcoin as an opportunity to create a new blockchain from scratch that can allow developers to build general applications. The first feature to include in this new blockchain was *Turing completness*. In computer programming this means it is possible to have loops in the code which would be necessary, for example, for calculating a probability or the value of pi. Bicoin's *script* language is not considered Turing complete because it is stack-based and therefore anything that is needed by the program must be loaded onto the stack. (Also, by definition stacks cannot loop.) 

The second feature was to use an account-based system. The benefit of this style is that each account (address) has a balance *and* the option of some code and storage. (This is in contrast to Bitcoin that uses a UTXO model I won't detail here but basically can only keep track of coins and not any additional data or code.)

### Summarized in the whitepaper, Ethereum is:
> a blockchain with a built-in Turing-complete programming language, allowing anyone to write smart contracts and decentralized applications where they can create their own arbitrary rules for ownership, transaction formats and state transition functions.

The whitepaper for *Ethereum* was published online in 2013 which was followed by a formal specification by Gavin Wood in 2014 and culminated in the ICO in 2015.

# Initial Coin Offering (ICO)
* founders / premine / foundation
* pow
* unlimited supply
* DAO hack

# Arbitrary Computation
* Smart Contracts
* dapps
* Ethereum Virtual Machine (EVM)
* Proof-of-Stake? difficulty bomb

# Applications
* stable coins
* defi
* dapps
* nfts / cryptokitties / punks

# Scaling
* ETH2
* alternate L1's
* arbitrum

# What did we miss?
* sharding
* rollups
* 

# Further Reading - the very short list
* [The Whitepaper by Vitalik Buterin](https://ethereum.org/en/whitepaper/)
* [The Yellowpaper by Gavin Wood](https://github.com/ethereum/yellowpaper), & [pdf](https://ethereum.github.io/yellowpaper/paper.pdf)

# About the Author
Jeff is a Senior Lecturer in Blockchain & Cryptocurrencies at AUT and an Executive Council member of BlockchainNZ\
[↰ back](https://github.com/millecodex/BlockchainNZ_education#readme)
