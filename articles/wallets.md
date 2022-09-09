[↰ back](https://github.com/millecodex/BlockchainNZ_education#readme)

# Title
## 🛠️ Under Construction 🚧 👷
### Contents
1. [intro](template.md#intro)
1. [second](template.md#second)
1. [third](template.md#third)
1. [What did we miss?](template.md#what-did-we-miss)
1. [Further Reading - the very short list](template.md#further-reading---the-very-short-list)



# Intro?
In one word: trust. Or, ironically, you could also say trust*less*. 

## Hierarchical Deterministic (HD) Wallets
Each instance of MetaMask that has a recovery phrase is called a hierarchical deterministic wallet. Within this hierarchy you can generate multiple accounts, each having their own public/private key pair and each being able to be regenerated with the recovery phrase. This allows many addresses to be generated from the same seed entropy[^1], so you can always invoice with a fresh address. The new accounts generated under this regime are ordered, with one 'leading' to the next, and deterministic such that when recovering a wallet the child accounts generated will be the same and in the same order.

[^1]: Seed entropy refers to the orignal source of randomness used to generate the seed phrase. In the case of browser generation such as with MetaMask this comes from the OS random function and is the safest way to do so online. Good ways to generate your own entropy include [dice](https://vault12.com/securemycrypto/cryptocurrency-security-how-to/dice-crypto-recovery-seed/particle-29) and [lava-lamps](https://www.cloudflare.com/en-gb/learning/ssl/lava-lamp-encryption/).

> <p align="left"><img width="600" alt="HD key generation tree" src="https://user-images.githubusercontent.com/39792005/188350149-c50a1858-6a84-4f47-bd2d-740b47b8657b.png"></p>

## BIP39
The seed phrase is a mapping of common English (& some other) language words to numbers that when assembled in the correct order represent the master private key. **BIP39**[^2] is a standard that was developed for Bitcoin and now used in many cryptocurrency projects. The total list is [2048 words](https://github.com/bitcoin/bips/blob/master/bip-0039/bip-0039-wordlists.md) and contains words as short as `mom` and as long as `mosquito`. From the master key many branches and children can be derived as per the algorithm below. To generate a seed phrase, you first need some entropy, then run it through `SHA256`, append the bit difference to the entropy, and split the output into the required number of words (12, 18, 24, etc.). These individual pieces then map to one of the 2048 words.

[^2]: Bitcoin improvement proposal number [39](https://en.bitcoin.it/wiki/BIP_0039). See also [BIP32](https://en.bitcoin.it/wiki/BIP_0032) and [BIP44]()

> <p align="left"><img width="600" alt="extending parent public key" src="https://user-images.githubusercontent.com/39792005/188350155-7f26f889-fcc9-45bd-9691-74d2245031db.png"></p>
>
> Key diagram sources: Antonopolous, Mastering Bitcoin. 2nd ed. 2018. https://github.com/bitcoinbook/bitcoinbook. 

## Security
In order to guess someone's private key you need to guess a sequence of 12, or 24 words from the list. Since there are 2048 possibilities for each guess, you have a one-in-2048 chance of guessing the first word correctly. At this point it may seem feesible for a computer to run this search fairly easily. Keeping in mind there is no progress indicator like making it past the first tumbler in a lock, so the probability to find the first two words is now $p= {1 \over 2048}{1 \over 2048}={1 \over 4,194,304} $. Extending this to a twelve word seed phrase: $p={1 \over 2048^{12}}$ and inverting to represent the number of possibilities we get $5.44E10^{39}$. On average it might take half the time to correctly guess a seed, so this is $2.72E10^{39}$ attemps. This is [roughly](https://en.wikipedia.org/wiki/Orders_of_magnitude_(numbers)#1036) the same size as the theoretical maximum number of Internet addresses that can be allocated under the IPv6 addressing ( $10^{36}$ ); or the estimated number of atoms in Earth ( $10^{50}$ ).

*Exercise:* How much harder is it to guess a 24-word phrase? How long would it take your computer to guess every possible key?

<p align="center"><img width="800" alt="total-stablecoin-supply-daily" src="https://user-images.githubusercontent.com/39792005/147860382-00470018-aae5-46a7-8d7f-023a2b163a4f.png"></p>

# Third
Table
|Stablecoin|Currency Peg|Backing|Blockchains          |
|:---------|:-----------|:------|:--------------------|
|USDT      |USD      |[mix of assets](https://www.bloombergquint.com/business/tether-gives-more-details-on-assets-backing-crypto-stablecoin)|Ethereum, Algorand, Tron, BSC, Solana, Fantom, etc.|
|USDC      |USD         |USD          |Ethereum, Algorand, BSC, Solana, Stellar, etc.|
|AUDT      |AUD         |AUD          |Ethereum|
|NZDS      |NZD         |NZD          |Ethereum ([still in beta as of Jan. 2021](https://www.techemynt.com/))|
|XSGD      |SGD         |SGD          |Ethereum, Zilliqa|
|EURS      |EUR         |EUR          |Ethereum, Polygon, Algorand|
|DAI       |USD         |crypto collateral|Ethereum, Polygon, BSC, Fantom, Gnosis ||
|PAXG - Paxos Gold|1 oz of gold|physcial gold|Ethereum|

# What did we miss?
* Point form list
  * second

# Further Reading - the very short list
* []()
* []()
* []()

# Next
* :point_right: [DeFi](defi.md)

# About the Author
Jeff is a Senior Lecturer in Blockchain & Cryptocurrencies at AUT and an Executive Council member of [BlockchainNZ](https://blockchain.org.nz/). He can be found tweeting about crypto at [@japple](https://twitter.com/Japple).\
[↰ back](https://github.com/millecodex/BlockchainNZ_education#readme)
