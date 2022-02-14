[↰ back](https://github.com/millecodex/BlockchainNZ_education#readme)
# Tokens
## 🛠️ Under Construction 🚧 👷

### Contents
1. [Introduction](tokens.md#introduction)
1. [Token Standards](tokens.md#token-standards)
1. [third](template.md#third)
1. [What did we miss?](template.md#what-did-we-miss)
1. [Further Reading - the very short list](template.md#further-reading---the-very-short-list)

# Introduction
Why would tokens need an introduction? 

Lets start with an example. Here in West Auckland we need to put tags on our rubbish and recycling bins before they will be collected and emptied by the waste disposal folks. Not just any tags though. The nice plastic stickers have to be the ones specifically appointed by the council. You can get them at the grocery store or library, but you will have to pay. Presently $3.80 for a standard 120 litre bin. ($4.25 if you're on the North Shore. Fancypants.)

> <p align="center"><img width="800" alt="auckland council rubbis tags" src="https://user-images.githubusercontent.com/39792005/153701164-dd32eef5-1f89-42e6-96a7-89f26adcf38a.PNG"></p>

The tag is a token. Each one is interchangeable with another one of the same colour. Each one has an underlying value determined by the issue price set by the council and enforced by the difficulty in conterfeiting. And each tag has utility, in this case a weekly empyting of your bin. In an extreme scenario you could even imagine a tag market emerging where those close to the tag-printer skim off the top and cut their neighbours in on a discount, benefiting both parties financially. Eventually the council will have to raise tag prices to cover the loss and thus affect the average every-tagger in their weekly budget. This embezzlement has now inflated the price of a tag and distorted the value (the rubbish trucks still only collect 1 bin per week). council rubbish tage are a hidden tax that disproportionately affect the lower socioeconomic class. Thankfully this is just a hypothetical scenario.

Back to the tag being a token. The **digital** representation has many of the same properties: it is fungible (interchangeable), secure (can't be stolen), scarce (can't be copied), valuable (someone would pay for it), and has utility (otherwise why do I need it?). Additionally we have just described many of the properties of money itself, and this may be why a distinction between cryptocurrencies, utility tokens, securities, and collectibles can be fuzzy and subjective. Without getting into the weeds, a $20 note is a physical token, but $20 in your bank account app is *not* a digital token─its just a promise stored in the bank's database.

### Are Coins Tokens?
If you have some bitcoin or ether, yes, these are digital tokens because they are fungible, secure, scarce, and have monetary value and utility. (Bitcoin's utility is widely considered to be a store-of-value.) Its confusing at first but there is a difference between value and utility. In Bitcoin's case the utility *is* value. For Ethereum there is broader application, e.g., using ether to purchase an NFT or invest in a new project or pay gas fees. 

### Non-Fungible
Currency tokens (and cash) are interchangeable, or fungible, because it doesn't matter what specific token you have, everyone agrees on the same value. If people were willing to pay a premium for specific tokens or characteristics, then the overall utility of the medium as money begins to fall apart. This is the problem with barter; there is far too much subjective difference in value between objects for people to easily exchange goods directly. 

Think of paintings in a gallery. All the paintings are similar in many respects - paint, colour, frame, 2-dimensional - however, each painting is obviously unique with value determined by many external factors. Non-fungible tokens, where each unit is unique, are designed for this purpose. In a digital manner they implement security and scarcity. Value and use are subjective like gallery paintings, but these now inherit properties the open, permissionless, censorship-resistant properties of the blockchain.

NFTs aren't just for collectibles, art, and profile pictures. Any document or data structure that can be digitised can be represented as an NFT. Music, investment rights,  certificates, degrees, licenses, passes, patents, title deeds, concert tickets, contracts et-cetera. 

## Token Standards
Over time standards have emerged that assist developers with creating new projects or building functionality. Some of the popular ones will be listed here.

### ERC-20
The first use case of Ethereum was generating new coins. These projects often launched with fundraising efforts called ICOs (initial coin offerings) that promised buyers a certain allocation of new tokens. All these tokens live inside (or on) the Ethereum blockchain but are separate from ether. Think of tokens as carriages that run on the rails of Ethereum and the whole train is powered by ether. The [Ethereum Request for Comments 20](https://eips.ethereum.org/EIPS/eip-20) is the standard that defines how to make a fungible token that is compatible with Ethereum itself. Because its an open network anyone is free to make their own token and launch it on Ethereum[^ownToken]. The contract will live forever on the blockchain and handle functions like transfers, account balances, token creation and destruction.
[^ownToken]: This is often a tutorial exercise when learning about blockchains. Launching a self-token contract on the mainnet is expensive due to gas fees, but you can easily launch one on a testnet.




### ERC-755 & ERC-1155
These are both NFT standards built on Ethereum.

* `ibTOKENS` interest bearing tokens
* `wTOKENS` wrapped tokens
* `ETH-USDC-lp` liquidity provider tokens
* bridging
* burning
* minting
* airdrops
* NFTs


* 
<p align="center"><img width="600" alt="tokens_abracadabra" src="https://user-images.githubusercontent.com/39792005/150704500-eab147f5-5191-4999-b44f-2bf044d7ac8b.png"></p>



# What kind of token is this?
You may have to lookup what blockchain the token runs on





# graphic example
Chart

<p align="center"><img width="800" alt="total-stablecoin-supply-daily" src="https://user-images.githubusercontent.com/39792005/147860382-00470018-aae5-46a7-8d7f-023a2b163a4f.png"></p>

# Table example
Table
|Stablecoin|Currency Peg|Backing|Blockchains          |
|:---------|:-----------|:------|:--------------------|
|USDT      |USD      |mix|Ethereum, Algorand, Tron, BSC, Solana, Fantom, etc.|
|USDC      |USD         |USD          |Ethereum, Algorand, BSC, Solana, Stellar, etc.|

# What did we miss?
* Point form list
  * second

# Further Reading - the very short list
* []()
* []()
* []()

# Next
* :point_right: [Addresses](addresses.md): bitcoin & segwit, multichain, formats, generation, vanity, security, math
* :point_right: [Wallets](wallets.md): cold storage, hot wallets, paper & brain, standards, security

# About the Author
Jeff is a Senior Lecturer in Blockchain & Cryptocurrencies at AUT and an Executive Council member of [BlockchainNZ](https://blockchain.org.nz/). He can be found tweeting about crypto at [@japple](https://twitter.com/Japple).\
[↰ back](https://github.com/millecodex/BlockchainNZ_education#readme)
