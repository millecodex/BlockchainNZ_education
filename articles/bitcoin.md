# What is bitcoin?
First, a brief history of the problem that Satoshi Nakamoto was looking to solve.

## Digital Cash (without the bank)
* The 80's & 90's saw many attempts to create a digital version of money that could have a token, both private and untraceable, treated as a bearer instrument and not subject to the fragilities of third party issuers and verifiers. To name a few there was David Chaum's work on *Untraceable Electronic Cash*, Wei Dai's [*b-money*](http://www.weidai.com/bmoney.txt), and Nick Szabo's [*Bit Gold*](https://unenumerated.blogspot.com/2005/12/bit-gold.html).
* Many technical challenges along the road to these approaches were overcome by advances in cryptography such as digital signatures and hash functions. One problem stood out: how to prevent someone from using a digital coin at one shop, copying it, and using it a second time at another shop? Known as the double-spend problem, this is easily sovled using a centralized authority to check someone's balance and update it accordingly; by the time you arrive at the second retailer your card will be declined for insufficient funds.
* The decentralized approach that removes the bank is *one* of the revolutionary ideas put forward by Satoshi in his whitepaper.  

## The Whitepaper
<img width="800" alt="header to the bitcoin whitepaper" src="https://user-images.githubusercontent.com/39792005/145146212-c35aff55-97ab-478a-8e10-de2977bc7a7f.PNG">
* There are many components to this system that will be introduced. Individually it can be difficult to see the connection between them and how they contribute to a peer-to-peer monetary system. This is intended to be an overview and if you are just learning about Bitcoin don't be disuaded if the pieces don't fall into place quickly *(Learning is hard!)*

### p2p Network
* consensus / longest chain / byzantine generals problem
* The key to the double-spend is to distribute the record of transactions to every participant in the network. In this manner every seller can verify independently that any buyer has the required unspent amount. Every new transaction is shared through the network with everyone else in a peer-to-peer (p2p) manner, rather than sending to a central server and having them update the accounts, this is handled at the individual level. The distributed ledger removes both the need for centralized accounting, and for trust between usesr. There is no reason for Alice to trust Bob because the network consensus says that Bob has the authority to spend his coins.

* Practicaly speaking, each peer in the network listens for new blocks of transactions, verifies them, and adds them to their own, local database. Should two nodes have conflicting information because they received new blocks at slightly different times, or with different transactions in them, then the state is said to fork, and for the time being *both* forks are valid. Resolving forks happens often, is expected, and is the job of the consensus mechanism. The way that Bitcoin does this is by a longest chain rule, meaning that whatever node has the longest chain of blocks is the most likely to receive a new block and therefore continue the chain. If a node falls behind, then it abandons its chain and contributes to the longest. This method of distributed system consensus is now known as *Nakamoto* conseneus.
 
* Because the chain is public you can do an inventory of nodes online at any given time. This also removes gatekeepers as anyone is free to join or leave at any time. At the end of 2021 the number of [bitcoin nodes](https://bitnodes.io/) globally was just under 15,000. (Compare this with centralized systems like Facebook that keep your data on anywhere from 3-5 nodes.)

### Mining & Security
* The next major advance demonstrated in Bitcoin was using computational power through proof-of-work to act as a secure time-stamping service. This accomplished two things: keeps the network secure because it is very hard to alter the ledger (needs heaps of power) and incentivses actors to behave honestly (in their economic best interest) 
* A hash is a cryptographic function that scrambles input data and outputs a fixed-length string that appears random. Any data of any size can be fed into a hash, such as a transaction, an image, or an entire block, and the result is a string of letters and numbers that can only be recreated using the original data. This makes hashing one-way, it cannot be reverse engineered, and if you have the original data the hash can be verified very quickly.
* Bitcoin uses secure hash algorithm of length 256 bits (SHA256) to store pointers to the data in the blockchain. This has the advantage of being easy and fast to verify data, yet difficult (mathematically near impossible) to forge. The hashes in each new block include references to the previous block so if someone wanted to change or delete old data then hash pointers would all have to updated. 
* Its a good place to pause and ask: why would someone agree to using their hardware for all this hashing and maintaining the ledger? And an answer: what if the protocol had some form of built-in money to reward people for donating their finite computing power?
* Proof-of-work (PoW) uses the same SHA256 algorithm to incentivise participants in the network by rewarding lucky ones with coins. Here is where the killer-app comes in. Bitcoin is a system to maintain a distributed ledger *and* the ledger's purpose is to keep track of its own coins! Every block includes some coins that are up for grabs to the miner that finds a lucky hash value. There is no way to game the system because the hashes are not reversible which means everyone is guessing and hoping their hash is a winner. One misconception this author notes is the hashes are sometimes referred to as *complex math problems* or hash *puzzles*, both of which are incorrect. SHA256 is just a recipe to scramble bits of data and using the terms *math* and *puzzle* imply that there can be some optization or correct solution.

* So, PoW is called mining because of the non-redeemable effort that goes into finding new new coins. Every ten minumtes on average a new block is  mined and with it the miner can redeem the block reward - new bitcoins. 

## Economics

* the block reward

* difficulty adjustment 10 minute intervals
* asics
* energy consumption
* 
* core software / dev community
* layer 1 blockchain; lightning network

* fixed supply is a decreasing geometric series
* addressess/ecdsa
* utxo

### Socio-economic Factors
* born from the ashes of the GFC
* genesis block

## Today
* most robust network humans have created
* bootstrapped an entire financial system; global settlement in minutes; fees orders of magnitude lower than before
* 2% of global population has used it
* 14th largest currency next to the Russian Ruble and Swiss Franc [(source)](https://coinmarketcap.com/fiat-currencies/)
* 7 tps 
* SoV
* features transparent, etc.; block explorers

## Further Reading
* The whitepaper: [*Bitcoin: A Peer-to-Peer Electronic Cash System* ](https://bitcoin.org/bitcoin.pdf)
* History of the tech: [*Bitcoin's Academic Pedigree*, Communications of the ACM](https://cacm.acm.org/magazines/2017/12/223058-bitcoins-academic-pedigree/fulltext)



