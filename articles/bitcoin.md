# What is bitcoin?
First, a brief history of the problem that Satoshi Nakamoto was looking to solve.

## Digital Cash
* The 80's & 90's saw many attempts to create a digital version of money that could have a token, both private and untraceable, treated as a bearer instrument and not subject to the fragilities of third party issuers and verifiers. To name a few there was David Chaum's work on *Untraceable Electronic Cash*, Wei Dai's [*b-money*](http://www.weidai.com/bmoney.txt), and Nick Szabo's [*Bit Gold*](https://unenumerated.blogspot.com/2005/12/bit-gold.html).
* Many technical challenges along the road to these approaches were overcome by advances in cryptography such as digital signatures and hash functions. One problem stood out: how to prevent someone from using a digital coin at one shop, copying it, and using it a second time at another shop? Known as the double-spend problem, this is easily sovled using a centralized authority to check someone's balance and update it accordingly; by the time you arrive at the second retailer your card will be declined for insufficient funds.
* The decentralized approach that removes the bank is *one* of the revolutionary ideas put forward by Satoshi.  

## The Whitepaper
<img width="800" alt="bitcoin_header" src="https://user-images.githubusercontent.com/39792005/145146212-c35aff55-97ab-478a-8e10-de2977bc7a7f.PNG">
* fixed supply is a decreasing geometric series
* addressess/ecdsa
* utxo

### Mining
* SHA256 & hashing
* difficulty adjustment
* the block reward
* security
* asics
* energy consumption

### Network
* consensus / longest chain / byzantine generals problem
* 10-100k nodes
* core software / dev community
* layer 1 blockchain; lightning network

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



