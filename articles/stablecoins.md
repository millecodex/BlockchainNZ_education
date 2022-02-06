[↰ back](https://github.com/millecodex/BlockchainNZ_education#readme)

# Stablecoins: A Primer
Introducing stablecoins beginning with the question: What makes a coin stable? and looking at some of the unique features that algorithmic stablecoins have innovated. The second portion will investigate risks associated with this new asset and detail some case studies from the wild.

# Contents
1. [Introduction](stablecoins.md#introduction)
2. [What is stability?](stablecoins.md#what-is-stability)
   - Volatility
   - How does it stay pegged? 
3. [How many breeds in the stable?](stablecoins.md#how-many-breeds-in-the-stable)
   - (Weak) Taxonomy
     - Collateral and ownership
4. Algorithmic Stablecoins
   - Coupon Clipping & Bonding
   - Supply Management Strategies
5. Risks
6. Case Studies
   1. Un-Peg
      - Dai
      - sUSD
   2. Collapse
      - Dollar Protocol
      - Empty Set Collar
      - Basis
7. Conclusion
8. [What did we miss?](stablecoins.md#what-did-we-miss)
9. [Further Reading - the very short list](stablecoins.md#further-reading---the-very-short-list)

# Introduction
We [first](https://github.com/millecodex/BlockchainNZ_education/blob/main/articles/defi.md#stablecoins) introduced stablecoins as a key element of DeFi to map value from your traditional banking world to the crypto-digital world without being exposed to volatility. Thus far they have proven essential for liquidity pools, trading and settlement, as well as operations like borrowing & lending. Although they generally adopt all the benefits of having a cryto-native platform such as low fees, fast settlements, auditability, programmability, and censorship resistance, not all stablecoins are created equal.

#### Up and to the Right
It is hard to ignore the growth and popularity of stablecoins when looking at the total value. This chart from [TheBlock](https://www.theblockcrypto.com/data/decentralized-finance/stablecoins) is showing growth in stablecoins over the past four years. In 2021 the total value of stablecoins rose from ~$28B to $150B USD. DeFi has been largely responsible for this increased demand with people rushing to create a stablecoin for every chain and every new finance protocol.

> <p align="center"><img width="800" alt="total-stablecoin-supply-daily" src="https://user-images.githubusercontent.com/39792005/147860382-00470018-aae5-46a7-8d7f-023a2b163a4f.png"></p>

The top five by supply are Tether (USDT), USD-Coin by Circle (USDC), Binance USD (BUSD), and Dai (DAI). Tether, USDC, and Binance's USD are issued privately, whereas DAI maintains a US dollar peg by holding crypto assets in its treasury managed by a DAO. Here is a partial listing of stablecoins, the currency they are pegged to, the collateral backing the peg, and the blockchains where they can be found. (As of January 2022, [CoinGecko](https://www.coingecko.com/en/categories/stablecoins) lists 71 stablecoins, 52 of which have active trading.)

|Stablecoin|Peg         |Collateral   |Blockchains          |
|:---------|:-----------|:------------|:--------------------|
|USDT      |USD         |Mix of assets|Ethereum, Algorand, Tron, BSC, Solana, Fantom, etc.|
|USDC      |USD         |USD          |Bitcoin (Liquid), Ethereum, Algorand, BSC, Solana, Stellar, etc.|
|NZDS      |NZD         |NZD          |Ethereum ([still in beta as of Jan. 2021](https://www.techemynt.com/))|
|XSGD      |SGD         |SGD          |Ethereum, Zilliqa|
|EURS      |EUR         |EUR          |Ethereum, Polygon, Algorand|
|DAI       |USD         |crypto       |Ethereum, Polygon, BSC, Fantom, Gnosis |
|PAXG      |1 oz of gold|physical gold|Ethereum|
|FRAX      |USD         |crypto, fractional|Ethereum, Avalanche, BSC, Fantom, Kusama   |
|AMPL      |2019 USD    |none         |Ethereum, Avalanche, BSC, Near|
|RAI       |none        |crypto       |Ethereum|

# What is stability?
Lets begin by looking at the question: What is stability? Just like liquidity means not affecting the price, *stability means not worrying about the price*. In a liquid market no individual's buy/bid or sell/ask activity should be able to change the price. In a stable market the same individual isn't concerned about price movement; they can look away and come back at some time in the future expecting the price to be the same. This is not equivalent to being able to predict the price in the future─there is still some uncertainty─however we will not spend a lot time worry about price flucuation.

The vast majority of stablecoins are pegged to the US dollar which means they target the price of $1.00. Any deviance from this numerical value will invoke some mechanism to bring the price back to 1. Its tempting to call 1 an equilibrium but there is a subtle difference. An equilibrium condition is arrived at naturally such as a mass hanging from a spring -> the force of gravity *down* will be in equillibrium with the force of the spring *up*. In the case of the US dollar the numerical value is set and its spending power (the natural equilibrium) varies with inflation and monetary policy etc. 

The previous example of equilibrium versus target peg brings up a problem with stablecoins, that is, they are only stable compared to their reference peg. The utility of such tokens is in fact variable, just as the wages of your parents generation cannot be compared to yours today. An interesting example is Ampleforth that is pegged to the 2019 inflation-adjusted US dollar. More on `AMPL` later. 

### Volatility
If we set the target to be 1 and allow some variation in either direction, this is the volatility that can be expected. In fact, the stablecoin can only be considered stable within a certain subjective tolerance. The more resolution required, the more difficult it will be to maintain the peg. If you are comfortable with ±0.5% volatility then you'll be happy trading between $0.995 and $1.005 for an asset valued at $1.000. The farther from the target that the price strays the harder it is for people to maintain confidence. In other words, they will begin to worry about the peg and our token is no longer considered stable. 

**volatility analysis & calculation**
Volatility is a measure of how much the price fluctuates around its mean.

* see V-lab https://vlab.stern.nyu.edu/docs/volatility
* Does the Design of Stablecoins Impact Their Volatility? Klaudia Jarno and Hanna Kołodziejczyk. Authors conclude that design matters. They use coinmarketcap data and have a volatility methodolody
* On the stability of stablecoins by Grobys et al compare Bitcoin volatility to stablecoins

### How does it stay pegged?
So what can you do when your dollar is trading for 99½ cents? Maintaining the peg in a decentralised manner is of crucial importance for stability. The value of a synthetic USD asset is set by an oracle (external to the blockchain) that can be queried from a smart contract to check that say, 1 blockchain-dollar is worth 1 USD. In the market these tokens may be exchanged for higher or lower than $1 depending on market factors. If the price rises to $1.01 per token then there is an opportunity for someone to mint new tokens, which, by definition cost them $1.00, and sell them on the open market for $1.01, pocketing the difference. These newly minted tokens cause the supply to increases reducing the market demand. The price should reflect this supply expansion and decrease towards the peg. A similar mechanism occurs when the price drops below $1.00. Say your token is $0.99, now you can purchase 100 tokens for $99 in the market, turn around and redeem 100 from the protocol for $100, profiting $1 for your trouble. This type of regular arbitrage is open to anyone undertake and often executed by bots that watch the various exchanges for price and execute a trade when profitable.

Fiat stablecoins like USDC have their peg set and do not need to be maintained by market mechanisms as long they can scale.

### Does the peg need to be 1? 
No, its just handy because its the standard unit for much of the globe, even if not the dollar. There are not many examples, however, AMPL presently trades around $1.079 which is the 2019 inflation-adjusted peg.

### Do we need a peg? 
Not at all. This is called floating and is what many currencices do in the foreign exchange markets such as the US Dollar and Japanese Yen since 1971, and the New Zealand Dollar  since 1985. Reflexer's `RAI` token was originally set to 3.14 (π) because they needed a place to start. Now it is free to float according to the market. A new category called unpegged stablecoins has emerged and will be discussed later.

# How many breeds in the stable?
In an effort to categorize or taxonomize the myriad coins in the stable, a few approaches arise including: collateral ownership, collateral type, and maintenance dynamics. I will consider all angles in an attempt to develop a (weak) taxonomy.

### Collateral Type
Now, categorizing what assets, if any, are backing the stablecoins to ensure consumer confidence should they need to be redeemed. Ordered from material to virtual collateralization we have: Gold, Fiat, Crypto, and Nothing. 

### Collateral Ownership

### Peg Maintenance Dynamics


collateralized has some equivallent backing reserved for anyone wanting to redeem their crypto for dollars. This comes with custodial risk for those managing the peg offchain, or with over-collaterization requirements for onchain versions.

This is by no means straight-forward, and you will find different perspectives out there. [X] does it this way; [Y] does it that way. While tempting to say that all stables are either algorithmic or not, this is inconsistent because it doesn't capture the variability withing the algorithmic sphere. For this reason, a better way to group these is by........




# Algorithmic Stablecoins
As with many things in DeFi there is a push to automate the process and have code be the decentralised arbiter. This trustless algorithmic stablecoin should be scalable and require no maintenance, however, many attempts have been difficult to bootstrap or subject to volatility. Starting a new stable currency with no collateral is risky business for the users and this lack of trust has been apparent in the uptake of these coins.


## Coupon Clipping & Bonding
### Seigniorage Shares
## Supply Management Strategies

 

#### *Collateralized* (e.g. USDC, USDT, DAI, RAI)
For a stablecoin to remain pegged to a fiat currency it must be actively managed. Tether issues (mints) new USDT when required and takes USD deposits as backing. As the volume of USDT grows, so does the value of the asset behind it. This creates centralised custodial and [regulatory issues](https://www.theverge.com/2021/10/15/22728253/tether-41-million-misleading-statements-fiat-currency-bitfinex-cftc). If a large number of people want to cash out of their USDS, for example, and back into dollars then this could create a problem for Circle, the company that issues USDC, as they need to be ready and have enough available. Upon redemption they should burn the tokens to provably reduce the circulating supply.

#### AMPL
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
* https://www.liquity.org/blog/how-synthetix-uses-lusd

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
* Branded Dollars allow a project to use their own token to bootstrap their own stablecoin. [ICHI](https://www.ichi.org/) is calling it stablecoin-as-a-service.

# Further Reading - the very short list
* [A Note on Cryptocurrency Stabilisation: Seigniorage Shares by Robert Sams (pdf)](https://github.com/rmsams/stablecoins/blob/master/paper.pdf)
* [Beware the Coupon Clipper: The Insurmountable Flaws of so-called Algorithmic Stablecoins](http://thinking.farm/essays/2021-01-17-beware-the-coupon-clipper/)
* [Motivation, design, and performance of the Ampleforth protocol under live market conditions](https://faq.ampleforth.org/durability)

# Next
* :point_right: [DeFi](defi.md)

# About the Author
Jeff is a Senior Lecturer in Blockchain & Cryptocurrencies at AUT and an Executive Council member of [BlockchainNZ](https://blockchain.org.nz/). He can be found tweeting about crypto at [@japple](https://twitter.com/Japple).\
[↰ back](https://github.com/millecodex/BlockchainNZ_education#readme)
