[↰ back](https://github.com/millecodex/BlockchainNZ_education#readme)

# DeFi (Decentralized Finance)

### Contents
1. [Motivation: Why decentralize finance?](https://github.com/millecodex/BlockchainNZ_education/blob/main/articles/defi.md#motivation)
1. [Stablecoins](https://github.com/millecodex/BlockchainNZ_education/blob/main/articles/defi.md#stablecoins)
3. [Decentralised Exchanges (DeXs)]()
6. [Farming]()
7. [What did we miss?](https://github.com/millecodex/BlockchainNZ_education/blob/main/articles/defi.md#what-did-we-miss)
8. [Further Reading - the very short list](https://github.com/millecodex/BlockchainNZ_education/blob/main/articles/defi.md#further-reading---the-very-short-list)

# Why decentralize finance?
In one word: trust. Or, ironically, you could also say trust*less*. Allow me to explain. For the same reason that Bitcoin is successful without a centralizing third-party─namely that you can transact with a perfect stranger in a foreign country by trusting the protocol and you *don't* need to trust the stranger─the cascade of financial products that can be built upon digital money is an ideal fit for blockchains.

Anything you can do at a bank, or an investment bank, or a hedge fund, or a stock exchange can be built in code and run on a blockchain. There are number of more practical reasons why someone would be interested in decentralised finace such as higher yields than found in more standard financial products, lower fees, transparency, easier access to foreign markets, more fine grained control (you can program it), etcetera. 

I could go on, but lets detail some of these innovations happening in defi-land.

# Stablecoins
The primary advantage to having a fiat currency on a blockchain is to map value from your bank-and-mortar world to the crypto-digital world without being exposed to the price volatility of tokens. I can exchange $1 dollar for 1 crypto-token, say, USD-Coin (USDC) and be assured that 1:1 mapping will hold. For business operations, valuations, projections, and so on this is crucial. The secondary advantages come from all the benifits of having a cryto-native platform such as low fees, fast settlements, auditability, programmability, and censorship resistance.

It is hard to ignore the growth and popularity of stablecoins when looking at the total value. This chart from [TheBlock](https://www.theblockcrypto.com/data/decentralized-finance/stablecoins) is showing growth in stablecoins over the past four years. In 2021 the total value of stablecoins rose from ~$28B to $150B USD.

<p align="center"><img width="800" alt="total-stablecoin-supply-daily" src="https://user-images.githubusercontent.com/39792005/147860382-00470018-aae5-46a7-8d7f-023a2b163a4f.png"></p>

The top five by supply are Tether ($USDT), USD-Coin by Circle ($USDC), Binance USD ($BUSD), and Dai ($DAI). Tether, USDC, and Binance's USD are issued privately, whereas DAI maintains a US dollar peg by holding crypto assets in its treasury managed by a *Decentralized Autonomous Organization* (DAO). Here is a partial listing of stablecoins, the currency they are pegged to, the collateral backing the peg, and the blockchains where they can be found.
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

# Decentralised Exchanges (DEXs)
Most crypto (and all stock) exchanges are centralized and use an order book to match trades. Called the central limit order book (CLOB) model, this works very well for a corporate structure such as the NZX (New Zealand Stock Exchange) that can have complete control over their servers and centrally manage events. The order book is a list of all the open buy/bid and sell/ask orders for a stock. Its the job of the software matching engine to fill as many orders as possible at the market price. This type of model does not scale to a blockchain because of amount of activity that would need to be written to the chain; all bids & asks for example, and the latency when updating the actual transactions.

### Automated Market Makers (AMMs)
The AMM solution to this is to add trading pairs to a pool of assets. The pairs are binded together so that in a pool of dollars to widgets there are always 10 widgets per dollar, depending on the depth of liquidity in the pool. A downside is slippage which is how the price moves for orders of a large fraction of the total pool liquidity, but this has improved in recent times. This AMM model bring many benefits that fall in line with a decentralised ethos:
* users can create their own trading pair; very useful for smaller or new assets or pairings
* users self-custody their assets & visa versa - the protocol isn't directly responsible for user's capital
* accessibility; the crypto markets are global and thus run 24/7, and this means a user only need access to the protocol (via the internet) to trade in any market

Uniswap is the leader in terms of activity for decentralized exchanges. The chart from [TheBlock](https://www.theblockcrypto.com/data/decentralized-finance/dex-non-custodial) shows that they have maintained over 50% of the market for the past few years. 

<p align="center"><img width="800" alt="total-decentralized-exchange-volume" src="https://user-images.githubusercontent.com/39792005/148142845-94dc4032-645f-4854-ae65-3e361481a49d.png"></p>

> There are two version of Uniswap: v2 and v3. This is a quirk of decentralized blockchain developement. Once the app code, in this case the Uniswap contract, is deployed on a blockchain, its effectively set and cannot be edited, updated, or have bugs fixed. This immutability is a key feature of blockchains and dapps, however, it means that for a project to have a new release often means they have to deploy another contract which introduces migratory challenges (and significant cost). Also, Uniswap v3 has many new features such as concentrated liquidity, and limit-like orders, that increase efficiency and will be discussed more in the [Defi 2.0](https://github.com/millecodex/BlockchainNZ_education/blob/main/articles/defi2.md) dive.

# Farming (fruit & veg emojis)
Farming took off in July/August of 2020 as Sushiswap and Uniswap started offering more products(?). In order to swap one asset to another a few prerequisites must be in place. There needs to be enough of the asset you want available to buy. And, 2, there needs to be a seller for the asset you want to sell. Lastly, a fair price is agreed upon by both buyer and seller.

### Yield farms & liquidity mining

### Impermanent loss

* unwritten
  * LPs & liquidity mining / yield farms / vaults  
  * IL
* yield aggregators 
* flash loans
* Tokenize everything
  * oracles
  * wrapped tokens


# What did we miss?
* [Defi 2.0](https://github.com/millecodex/BlockchainNZ_education/blob/main/articles/defi2.md) is the dive into more complex and obscure financial stuff happening on the blockchain. Here you will find a primer on:   
  * algorithmic stablecoins - USDN, FEI, FRAX, UST: see Messario 2021 report p.120.
  * non-pegged stablecoins & protocol owned liquidity
  * rebasing
  * pool 1 vs. pool 2
  * options/derivatives/perps(dydx) etc 

# Further Reading - the very short list
* []()
* []()
* []()

# About the Author
Jeff is a Senior Lecturer in Blockchain & Cryptocurrencies at AUT and an Executive Council member of [BlockchainNZ](https://blockchain.org.nz/). He can be found tweeting about crypto at [@japple](https://twitter.com/Japple).\
[↰ back](https://github.com/millecodex/BlockchainNZ_education#readme)
