[↰ back](https://github.com/millecodex/BlockchainNZ_education#readme)

# Stablecoins: A Primer
Introducing stablecoins beginning with the question: What makes a coin stable? and looking at some of the unique features that algorithmic stablecoins have innovated. The second portion will investigate risks associated with this new asset and detail some case studies from the wild.

# Contents
1. Introduction
1. What is stability?
1. How many breeds in the stable?
   - (Weak) Taxonomy
     - Collateral and ownership
1. Algorithmic Stablecoins
   - Coupon Clipping & Bonding
   - Supply Management Strategies
1. Risks
1. Case Studies
   1. De-Peg
      - Dai
      - sUSD
   2. Collapse
      - Dollar Protocol
      - Empty Set Collar
      - Basis
1. Conclusion
1. [What did we miss?](stablecoins.md#what-did-we-miss)
1. [Further Reading - the very short list](stablecoins.md#further-reading---the-very-short-list)

# Introduction
We [first](https://github.com/millecodex/BlockchainNZ_education/blob/main/articles/defi.md#stablecoins) introduced stablecoins as a key element of DeFi to map value from your traditional banking world to the crypto-digital world without being exposed to volatility. Thus far they have proven essential for liquidity pools, trading and settlement, as well as operations like borrowing & lending. Although they generally adopt all the benefits of having a cryto-native platform such as low fees, fast settlements, auditability, programmability, and censorship resistance, not all stablecoins are created equal.

#### Up and to the Right
It is hard to ignore the growth and popularity of stablecoins when looking at the total value. This chart from [TheBlock](https://www.theblockcrypto.com/data/decentralized-finance/stablecoins) is showing growth in stablecoins over the past four years. In 2021 the total value of stablecoins rose from ~$28B to $150B USD. DeFi has been largely responsible for this increased demand for a variety of stablecoins as they are useful for liquidity provision, farming, lending/borrowing, or short term settlement.

<p align="center"><img width="800" alt="total-stablecoin-supply-daily" src="https://user-images.githubusercontent.com/39792005/147860382-00470018-aae5-46a7-8d7f-023a2b163a4f.png"></p>

The top five by supply are Tether (USDT), USD-Coin by Circle (USDC), Binance USD (BUSD), and Dai (DAI). Tether, USDC, and Binance's USD are issued privately, whereas DAI maintains a US dollar peg by holding crypto assets in its treasury managed by a *Decentralized Autonomous Organization* (DAO). Here is a partial listing of stablecoins, the currency they are pegged to, the collateral backing the peg, and the blockchains where they can be found.
|Stablecoin|Currency Peg|Collateral   |Blockchains          |
|:---------|:-----------|:------------|:--------------------|
|USDT      |USD         |Mix of assets|Ethereum, Algorand, Tron, BSC, Solana, Fantom, etc.|
|USDC      |USD         |USD          |Bitcoin (Liquid), Ethereum, Algorand, BSC, Solana, Stellar, etc.|
|AUDT      |AUD         |AUD          |Ethereum|
|NZDS      |NZD         |NZD          |Ethereum ([still in beta as of Jan. 2021](https://www.techemynt.com/))|
|XSGD      |SGD         |SGD          |Ethereum, Zilliqa|
|EURS      |EUR         |EUR          |Ethereum, Polygon, Algorand|
|DAI       |USD         |cryptocurrency|Ethereum, Polygon, BSC, Fantom, Gnosis ||
|PAXG      |1 oz of gold|physical gold|Ethereum|

# What is stability?
Lets begin by looking at the question: What is stability?
> peg
> how does it remain stable?
> 
> **How does it stay pegged at $1?**
Maintaining the peg in a decentralised manner is of crucial importance for stability. The value of a synthetic USD asset is set by an oracle that can be queried from a smart contract to check that say, 1 dollar is worth 1 USD. In the market these tokens may be exchanged for higher or lower than $1 depending on market factors. If the price rises to $1.01 per token then there is an opportunity for someone to mint new tokens, this costs them $1, and sell them on the market for $1.01, pocketing the difference. As the supply of tokens increases the market price will fall back in line. A similar mechanism occurs when the price drops below $1.00. Say it is $0.99, now you can purchase 100 tokens for $99 in the market, turn around and redeem them from the protocol for $100, profiting $1 for your trouble.

# How many breeds in the stable?
In an effort to categorize or taxonomize the myriad coins in the stable, there are a few obvious approaches: collateral type and fraction, and ownership.

## (Weak) Taxonomy
 * Collateral and ownership

### Collateral
Now, categorizing what assets, if any, are backing the stablecoins to ensure consumer confidence should they need to be redeemed. Ordered from material to virtual collateralization we have: Gold, Fiat, Crypto, and Nothing. 

#### Percentage
At the same time there is a sliding scale of the percentage of the asset used in collateralization. 
#### Ownership
We must also consider who owns the collateral.  

# Algorithmic Stablecoins

1. Algorithmic Stablecoins
   - Coupon Clipping & Bonding
   - Supply Management Strategies

We can categorize stablecoins in three ways: collateralized, algorithmic, or a hybrid. As discussed in [Part I](https://github.com/millecodex/BlockchainNZ_education/blob/main/articles/defi.md#stablecoins), collateralized has some equivallent backing reserved for anyone wanting to redeem their crypto for dollars. This comes with custodial risk for those managing the peg offchain, or with over-collaterization requirements for onchain versions. 

#### *Collateralized* (e.g. USDC, USDT, DAI, RAI)
For a stablecoin to remain pegged to a fiat currency it must be actively managed. Tether issues (mints) new USDT when required and takes USD deposits as backing. As the volume of USDT grows, so does the value of the asset behind it. This creates centralised custodial and [regulatory issues](https://www.theverge.com/2021/10/15/22728253/tether-41-million-misleading-statements-fiat-currency-bitfinex-cftc). If a large number of people want to cash out of their USDS, for example, and back into dollars then this could create a problem for Circle, the company that issues USDC, as they need to be ready and have enough available. Upon redemption they should burn the tokens to provably reduce the circulating supply.

#### *Algorithmic* (e.g. AMPL, USDx)
As with many things in DeFi there is a push to automate the process and have code be the decentralised arbiter. This trustless algorithmic stablecoin should be scalable and require no maintenance, however, many attempts have been difficult to bootstrap or subject to volatility. Starting a new stable currency with no collateral is risky business for the users and this lack of trust has been apparent in the uptake of these coins.





Compare this to *Ampleforth* which describes itself as a "durable, fully-algorithmic unit of account [that] returns to a stable price by transferring the volatility of demand to supply, rather than attempting to eliminate volatility" `AMPL` is not described as a stablecoin because its protocol mediates the supply only and can take time to settle towards the target price $1. The supply is adjusted once per day through increasing or decreasing the token balances in user's wallets if the price falls outside a 5% margin.

> <img width="800" alt="ampleforth price and stock 2020 to 2021" src="https://user-images.githubusercontent.com/39792005/150047419-9138f874-c169-4928-97ee-d416913604fd.png">
> 
> Ampleforth's token price has remained around $1 while the stock is free to expand and contract ([source](https://faq.ampleforth.org/durability)).




#### *Hybrid of Collateral + Algorithmic* (e.g. FRAX, ESD, FEI, RAI)
A hybrid approach can use aspects of collateralization and trustless algorithmic adjustments to mitigate custodial and management risk while capturing efficiencies of automated controls. A successful example here is [FRAX](https://docs.frax.finance/) which is described as a hybrid (fractional) seigniorage shares model. This uses two tokens: FRAX which is soft-pegged to USD and Frax shares (FXS) to incentivise governance. A fraction of the FRAX is collateralized using mostly (but not all) stable cryptocurencies. The remaining fraction is unbacked. The ratio between backed/unbacked can be adjusted to keep its peg. Adjustment functions can be called by any holder and they are rewarded with seigniorage revenue through FXS. Additionally FXS is used for fees accrual and excess collateral value.

According to the Frax [docs](https://docs.frax.finance/conclusion):
> *The novel insight is to use market forces itself to see how much of a stablecoin can be algorithmically stabilized with its own seigniorage token so that it keeps a tight band around $1 like fiatcoins*

The value of FRAX (the peg) is set by an oracle that queries Chainlink for the true value of USD. Market forces allow for arbitrage when the price deviates from $1.00. Minting new tokens costs $1 via a combination of USDC + FXS at the ratio described above, and each token can always be redeemed for $1. If, for example, the price drops to $0.99, you can purchase 100 FRAX for $99 in the market, turn around and redeem them from the protocol for $100, profiting $1 for your trouble.


---
# Risks
* custodial risk of white/blacklisting
* collateral risk of underlying crashing, DAO-ETH vault liquidations
* L2 risks of illiquidiy
* Death Spiral of no demand / no buyer of last resort


# Case Studies
A look at some of the recent experiments and how they've performed in the wild west of global crypto markets. Included are Dai, Synthetix's sUSD, Dollar Protocol's USDx &f, Empty Set's trio, and ___ ?

## Where's my peg?
A number of times a stablecoin has lost its peg, in fact at a high enough resolution a stablecoin can *never* be at the peg and is always error-correcting, but at some point a loss of peg is synonymous with investors loss of confidence. Some examples are from Dai, Tether, and sUSD.
* Dai
* sUSD

## It was always just an experiment
A few attempts have resulted in major collapse, or as the authors often remind us, experiments that didn't go as planned.

### Dollar Protocol
[*Dollar Protocol*](https://docs.dollarprotocol.com/) presents a case study in algorithmic tokenomics with their USD stablecoin `USDx`. The algorithm allows for rebasing when the price goes above $1.05 or below $0.95 and targets a Uniswap USDx-USDC pool price. The rebasing will expand the supply in times of demand and the newly minted USDx is distributed to protocol stakeholders (token and bond holders & LPs). When the price is low the negative rebase (debase) will cut the supply by proportionally shrinking the number of tokens in users wallets. To avoid this debasing users are incentivised to bond or lock their USDx. Many of the parameters can be modified based on voting through a governance token `SHARE` that shares in seigniorage profits and fees.

> <img width="800" alt="usdx dollars price chart loses it peg to the USD" src="https://user-images.githubusercontent.com/39792005/150029689-995a1c67-2638-45e1-ad85-a0f1948a0ebb.PNG">
> 
> The chart from CoinGecko shows the market price of USDx had trouble holding its peg.

In the [post mortem](https://medium.com/dollar-protocol/xbond-deprecation-a-post-mortem-4c5c17e21712), it was detailed that the proportion of seigniorage rewards to the bond-holders was too large (50%) such that during positive rebases the newly minted tokens were market sold to recoup previous debt. Eventually demand dried up and too many bond holders were looking to exit back into USDC. The selling pressure created a death spiral, broke the USDx peg severely, and it was trading at $0.10 by early Febrary after only a few months since launch. As there was nothing backing USDx (its purely algorithmic remember) the bank run can continue all the way to zero, save for a final few holders hoping that the developers can fix the algorithm and save their money. To remedy this, Dollar Protocol attempted to pivot to a fractional strategy (USDf) similar to FRAX (a hybrid approach, next), but this also has been shuttered due to bootstrapping issues.

### Empty Set Dollar (ESD)
<img width="600" alt="empty set dollar price chart ESD" src="https://user-images.githubusercontent.com/39792005/150709622-1c1d088b-3695-4d4d-bfbd-33a40da1e6af.PNG">

### Digital Standard Unit (DSU)
<img width="600" alt="DSU digital standard unit total circulating value" src="https://user-images.githubusercontent.com/39792005/150884497-58daf7b2-723c-42c1-b44f-4596995e0f9d.PNG"> Chart from [DeFi Pulse](https://www.defipulse.com/usd/DSU)

### Basis

# Conclusions
stuff here

# What did we miss?
* I'm not sure yet

# Further Reading - the very short list
* [A Note on Cryptocurrency Stabilisation: Seigniorage Shares by Robert Sams (pdf)](https://github.com/rmsams/stablecoins/blob/master/paper.pdf)
* [Beware the Coupon Clipper: The Insurmountable Flaws of so-called Algorithmic Stablecoins](http://thinking.farm/essays/2021-01-17-beware-the-coupon-clipper/)
* [Motivation, design, and performance of the Ampleforth protocol under live market conditions](https://faq.ampleforth.org/durability)

# Next
* :point_right: [DeFi](defi.md)

# About the Author
Jeff is a Senior Lecturer in Blockchain & Cryptocurrencies at AUT and an Executive Council member of [BlockchainNZ](https://blockchain.org.nz/). He can be found tweeting about crypto at [@japple](https://twitter.com/Japple).\
[↰ back](https://github.com/millecodex/BlockchainNZ_education#readme)
