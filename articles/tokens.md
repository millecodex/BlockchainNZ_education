[↰ back](https://github.com/millecodex/BlockchainNZ_education#readme)
# Tokens
## 🛠️ Under Construction 🚧 👷

### Contents
1. [Introduction](tokens.md#introduction)
1. [Token Standards (Ethereum)](tokens.md#token-standards)
2. [Non-Ethereum Standards](tokens.md#)
3. [Token Lifecycle](tokens.md#)
4. [What did we miss?](tokens.md#what-did-we-miss)
5. [Further Reading - the very short list](tokens.md#further-reading---the-very-short-list)

# Introduction
Why would tokens need an introduction? 

Lets start with an example. Here in West Auckland we need to put tags on our rubbish and recycling bins before they will be collected and emptied by the waste disposal folks. Not just any tags though. The nice plastic stickers have to be the ones specifically appointed by the council. You can get them at the grocery store or library, but you will have to pay. Presently $3.80 for a standard 120 litre bin. ($4.25 if you're on the North Shore. Fancypants.)

> <p align="center"><img width="800" alt="auckland council rubbis tags" src="https://user-images.githubusercontent.com/39792005/154602801-882fb89d-3015-4891-8de3-227f4f0e9345.png"></p>

The tag is a token. Each one is interchangeable with another one of the same colour. Each one has an underlying value determined by the issue price set by the council and enforced by the difficulty in conterfeiting. The tag can be transferred to someone else whereby possession indicated ownership. And each tag has utility, in this case a weekly empyting of your bin. In an extreme scenario you could even imagine a tag market emerging where those close to the tag-printer skim off the top and cut their neighbours in on a discount, benefiting both parties financially. Eventually the council will have to raise tag prices to cover the loss and thus hit the average every-tagger in their weekly budget. This embezzlement has now inflated the price of a tag and distorted the value (the rubbish trucks still only collect 1 bin per week). The Council rubbish tag racket is a hidden tax that disproportionately affects the lower socioeconomic class. Thankfully this is just a hypothetical scenario.

Back to the tag being a token. The **digital** representation has many of the same properties: it is fungible (interchangeable), secure (can't be stolen), scarce (can't be copied), valuable (someone would pay for it), transferrable (not tied to someone's identity), and has utility (otherwise why do I need it?). Additionally we have just described many of the properties of money itself, and this may be why a distinction between cryptocurrencies, utility tokens, securities, and collectibles can be fuzzy and subjective. Without getting into the weeds, a $20 note is a physical token, but $20 in your bank account app is *not* a digital token─its just a promise stored in the bank's database.

### Are Coins Tokens?
If you have some bitcoin or ether, yes, these are digital tokens because they are fungible, secure, scarce, transferrable, and have monetary value and utility. (Bitcoin's utility is widely considered to be a store-of-value.) Its confusing at first but there is a difference between value and utility. In Bitcoin's case the utility *is* value. For Ethereum there is broader application, e.g., using ether to purchase an NFT or invest in a new project or pay gas fees. 

### Non-Fungible
Currency tokens (and cash) are interchangeable, or fungible, because it doesn't matter what specific token you have, everyone agrees on the same value. If people were willing to pay a premium for specific tokens or characteristics, then the overall utility of the medium as money begins to fall apart. This is the problem with barter; there is far too much subjective difference in value between objects for people to easily exchange goods directly. 

Think of paintings in a gallery. All the paintings are similar in many respects - paint, colour, frame, 2-dimensional - however, each painting is obviously unique with value determined by many external factors. Non-fungible tokens, where each unit is unique, are designed for this purpose. In a digital manner they implement security and scarcity. Value and use are subjective like gallery paintings, but these now inherit properties the open, permissionless, censorship-resistant properties of the blockchain.

NFTs aren't just for collectibles, art, and profile pictures. Any document or data structure that can be digitised can be represented as an NFT: music, certificates, degrees, licenses, passes, patents, title deeds, concert tickets, contracts, investment rights, et-cetera.

# Token Standards (Ethereum)
Over time standards have emerged that assist developers with creating new projects, building functionality, and interacting with other tokens, contracts, and chains. Some of the main ones that have been developed for [Ethereum](https://ethereum.org/en/developers/docs/standards/tokens/) are:

### ERC-20
The first use case of Ethereum was generating new coins. These projects often launched with fundraising efforts called ICOs (initial coin offerings) that promised buyers a certain allocation of new tokens. All these tokens live inside (or on) the Ethereum blockchain but are separate from ether. Think of tokens as carriages that run on the rails of Ethereum and the whole train is powered by ether. The [Ethereum Request for Comments #20](https://eips.ethereum.org/EIPS/eip-20) is the standard that defines how to make a fungible token that is compatible with Ethereum itself. Because its an open network anyone is free to make their own token and launch it on Ethereum[^ownToken]. The contract will live forever on the blockchain and handle functions like transfers, account balances, token creation and destruction. These tokens can be divided into as small as eight decimal places (`0.000 000 001`) to allow for very small and fractional payments.
[^ownToken]: This is often a tutorial exercise when learning about blockchains. Launching a self-token contract on the mainnet is expensive due to gas fees, but you can easily launch one on a testnet.

Examples of the ERC-20 standard include the following tokens (among *many*):
* `DAI` the decentralized algorithmic [stablecoin](https://makerdao.com/en/)
* `LINK` the decentralized [oracle network](https://chain.link/)
* `wBTC` [wrapped bitcoin](internal link)

### ERC-721
ERC-721 is a standard that includes an *integer* variable called `tokenID` that must be unique. From the EIP: "In general, all houses are distinct and no two kittens are alike. NFTs are distinguishable and you must track the ownership of each one separately." Any tokens deployed with this standard cannot be subdivided, and ownership is wholly transferred. 

Examples of the ERC-721 standard include:
* [CryptoKitties](https://www.cryptokitties.co/) collectibles and game,
* [Ethereum Name Service](https://ens.domains/) domain registrar, and
* [the Bored Ape Yacht Club](https://boredapeyachtclub.com/#/) collectibles and club membership.

### ERC-1155
Further to the previous two standards, the 1155 standard merges both fungible and non-fungible into a new standard that extends functionality. Called a Multi-token standard it can batch transfer groups of items, for example, if your character kills another in a game it can transfer the items to the winner in a single transaction. It also improves efficiency with a focus on game design where a large number of transfers could be required and it would be cumbersome for the user to stop gameplay to interact with a smart contract and pay associated gas fees.

Examples of the ERC-1155 standard include:
* [OpenSea](https://opensea.io/) the NFT marketplace,
* [Skyweaver](https://www.skyweaver.net/) the game, and
* [The Sandbox](https://www.sandbox.game/en/) metaverse platform.

# Non-Ethereum Token Standards
Ethereum may be the original smart contract platform, but there are plenty of younger ones vying for your tokens. Here I've listed some of the main smart contract platforms and their associated token standards. EVM compatibiliy refers to the Ethereum virtual machine which handles the processing of smart contracts. If compatible, the chain can understand contracts made for Ethereum which can help with bootstrapping users and projects that already exist there.

|Blockchain|native token|EVM compatible?|comments|
|:---------|:-----------|:--------------|:-------|
|Ethereum |`ETH`|:heavy_check_mark:|`ETH` is the native currency; ERC-20 tokens run on top and are processed by the EVM.|
|Avalanche|`AVAX`|:heavy_check_mark:|Avalanche has a 'X-chain' for native assets but also a 'C-chain' designed to be compatible with Ethereum **C**ontracts.|
|Fantom   |`FTM` |:heavy_check_mark:|The `FTM` token [exists](https://etherscan.io/address/0x4E15361FD6b4BB609Fa63C81A2be19d873717870) on Ethereum, but is the native asset of the Fantom ecosystem and can be bridged between the two.|
|Polkadot |`DOT` |:heavy_check_mark:|Although compatible with the EVM, this is not the main functionality. DOT is a new standard of the Polkadot ecosystem.|
|Solana   |`SOL` |:negative_squared_cross_mark:|Solana has [built-in support](https://spl.solana.com/token) for creating new tokens; EVM compatibility is in progress.|
|Tezos    |`XTZ` |:negative_squared_cross_mark:|Tezos has its own standards; [FA2](https://gitlab.com/tezos/tzip/-/blob/master/proposals/tzip-12/tzip-12.md) is a unified token contract interface.|
|Cosmos   |`ATOM`|:negative_squared_cross_mark:|The `ATOM` token can be found on Ethereum and Binance Smart Chain, but is the native asset of the Cosmos ecosystem. EVM compatibility is in progress.|

# Token Lifecycle


### Minting
* & airdrops

### Wrapping

### Bridging

### Burning


There are many smart contract platforms, or "Layer 1s", that can run dApps and transfer tokens. Some of them even appear to have the same token running on multiple blockchains. While this may true in name, the prudent reader always does their own research (DYOR) to avoid the embarassment of sending tokens to a contract that cannot accept them. 

> You may have to lookup exactly what type of token you are dealing with. Your first hint comes from the label itself. Here some common ones. Note these are **not** standardized and thus new projects may introduce their own token identifiers.

Summary Table

|Token label|description|example|
|:----------|:----------|:------|
|`ibTKN`| interest bearing tokens||
|`wTKN` |wrapped tokens|`wETH.e` is wrapped ETH on avalanche|
|`ETH-USDC-lp`| liquidity provider tokens||

<p align="center"><img width="600" alt="tokens_abracadabra" src="https://user-images.githubusercontent.com/39792005/150704500-eab147f5-5191-4999-b44f-2bf044d7ac8b.png"></p>

# graphic example
Chart

<p align="center"><img width="800" alt="total-stablecoin-supply-daily" src="https://user-images.githubusercontent.com/39792005/147860382-00470018-aae5-46a7-8d7f-023a2b163a4f.png"></p>

# What did we miss?
* Point form list
  * second

# Further Reading - the very short list
* [An Ethereum token list standard](https://tokenlists.org/)
* []()
* []()

# Next
* :point_right: [Addresses](addresses.md): bitcoin & segwit, multichain, formats, generation, vanity, security, math
* :point_right: [Wallets](wallets.md): cold storage, hot wallets, paper & brain, standards, security

# About the Author
Jeff is a Senior Lecturer in Blockchain & Cryptocurrencies at AUT and an Executive Council member of [BlockchainNZ](https://blockchain.org.nz/). He can be found tweeting about crypto at [@japple](https://twitter.com/Japple).\
[↰ back](https://github.com/millecodex/BlockchainNZ_education#readme)
