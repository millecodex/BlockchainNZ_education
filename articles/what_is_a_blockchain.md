[↰ back](https://github.com/millecodex/BlockchainNZ_education#readme)

# What is a Blockchain?
A blockchain is a data structure with a unique set of properties suited to decentralized systems. The data in a blockchain is usually wrapped in a package called a block and when the network is updated with new information this block is linked to the previous update. In this manner the links form a chain that cannot be broken without invalidating the entire chain. The data is *immutable* meaning that once a block is written it cannot be deleted or changed. In a public blockchain this is managed by having many participants each storing a copy of the data and agreeing on any updates. These nodes keep the network *decentralized*—without a main server or single-point-of-failure, and *transparent*—open to anyone to participate and audit the activity. 

Sometimes referred to as decentralized-ledger technology, or DLT, a blockchain consists of many pieces: a network protocol to communcate with other participants, a consensus mechanism to agree on the state of the ledger, a method of data storage, a transaction queue to decide what to do next, and some business logic, i.e. What can this blockchain do? Can it keep track of account balances? Can it run snippits of code (smart contracts)? Can it calculate interest payments? Can it record weather data?

> <p align="center"><img width="800" alt="blockchain data structure resembles ledger books" src="https://user-images.githubusercontent.com/39792005/152084209-bbde7db2-ddef-4f1b-bc98-354c0bc2e2ed.PNG"></p>
> 
> Each individual ledger is analagous to a block. When one book is full a new one begins with the account balances being copied over, thus linking the 'blocks'. The ledger is an accounting system that starts all the way back in the 1400's when the Medici family in Florence popularized double-entry accounting. The blockchain can be thought of as triple-entry accounting, where the third entry is the distributed copies that maintain consensus. Here, the second block has a cryptographic hash of the first block, and the third block has a hash of the second block, which, by definition includes the hash of the first block. This is how the chain maintains its integrity.

Many blockchain projects are open-source so improvements are made by the community of developers, or copies can be made (called *forks*) where others can experiment and try out new features. A *public* and *permissionless* network is open to anyone to view the data and its source code; no one needs permission to access the data or run a node. An important feature of a public open network is that it is *censorship-resistant* and this is one of the reasons for Bitcoin's popularity and growth. There is no pay-to-play or gatekeeper. Ideally everyone has equal access to the network.

Today there are myriad cryptocurrencies and blockchains covering the whole spectrum of attributes described here, however, all can trace their roots back to [Bitcoin](bitcoin.md).

# What is a Cryptocurrency?
Bitcoin was the first blockchain and presented the first use-case: money. Creating cash in an entirely digital manner was a problem that remained unsolved until Satoshi Nakamoto (an alias) released [software](https://bitcointalk.org/index.php?topic=382374.0) in 2008 as an experiment to see if his version could prevent coins from being copied and incentivise people to join the network. Bitcoin is referred to as a cryptocurrency because user's coins are kept secure from theft using asymmetric encryption (the same technology that keeps credit card details safe when shopping online). 

Today the term cryptocurrency refers to digital tokens that are represented on a blockchain such as bitcoin (lower-case *b*, BTC), or ether (from ethereum, ETH). Generally these tokens have value and are interchangeable (fungible) with each other on their own network. Cryptocurrency is distinct from fiat (government-issued) currency whether its digital or cash, although the lines are becoming blurred with the approach of central bank digital currencies (CBDCs). Cryptocurrency is also distinct from utility tokens and security tokens. And all of these are separate from NFTs! (non-fungible tokens).

Economists, historians, central bankers, and Bitcoiners, will all debate their own version of what a currency is, how is it different from a cryptocurrency, and what is bitcoin compared with all those other coins? These are interesting and important questions worth thinking about. 

A good place to start is with the *OG*: Bitcoin.

# Learn More
* :point_right: [What is Bitcoin?](bitcoin.md)
* :point_right: [What is Ethereum?](ethereum.md)

# Featured Topic: DeFi
Bitcoin has decentralised money. What can be said of *finance*?
* :point_right: [Decentralised Finance 1.0](defi.md)
---
[See all featured topics](../featured.md)
