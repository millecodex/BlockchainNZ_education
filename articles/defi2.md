[↰ back](https://github.com/millecodex/BlockchainNZ_education#readme)

# DeFi Part II (& 2.0)

# Introduction
In Part 1.0 we covered some foundational parts of DeFi: stablecoins, decentralized exchanges, the automated market maker & pools, liquidity mining and yield farming. Here we're going to start by looking at happens when you can automate some of the behaviour witnessed in part 1.0. Eventually we'll get to [DeFi2.0](defi2.md#DeFi2.0) and discuss algorithmic coins, rebasing, and self-repaying loans.

### Contents
1. [Yield Aggregators & Vaults](defi2.md#yield-aggregators--vaults)
1. [Flash Loans](defi2.md#flash-loans)
1. [Algorithmic Stablecoins](defi2.md#algorithmic-stablecoins)
2. [DeFi 2.0](defi2.md#)
3. [What did we miss?](defi2.md#what-did-we-miss)
4. [Further Reading - the very short list](defi2.md#further-reading---the-very-short-list)

# Yield Aggregators & Vaults
The winter of Defi (2020; Summer in the northern hemisphere) looked at yields coming out of farms and saw the trend of capital hopping around to the projects with the highest interest rate. So a simple question arises: how can I, a simple investor, capture some of this yield by moving my coins (without gas fees eating into my profits)?

[Andre Cronje](https://andrecronje.medium.com/) was there with *yEarn* to automatically move investments between *dydx*, *Compound*, and *Aave*. The native governance token, YFI, was advertised as having no value and was distributed through a liquidity mining program to users and was so successful it now trades at tens of thousands of dollars.

> "we have released YFI, a completely valueless 0 supply token. We re-iterate, it has 0 financial value. There is no pre-mine, there is no sale, no you cannot buy it, no, it won’t be on uniswap, no, there won’t be an auction. We don’t have any of it."\
-*Andre Cronje on the [launch of YFI](https://medium.com/iearn/yfi-df84573db81) explicity stating that there are no tokens reserved for insiders, specifically VCs*

As with other successful DeFi Legos, this model was copied eagerly and now aggregators and vaults are common. The present version of [yearn.finance](yearn.finance) offers a vault for depositing tokens that then use strategies such as shifting capital, auto-compounding, and rebalancing to earn yield. These vaults offer self-custody and allow withdrawals at any time, both features which represent reduced risk to the user. 

Another feautre of many DeFi protocols is borowing and lending because of the simplicity of doing it in a trustless blockchain environment. In this scenario the lender earns interest directly from the borrower in an almost peer-to-peer transaction. The third party here holds the collateral and facilitates the *bank*. As an example Yearn offers loans of DAI at 1.35% APY (as of Jan. 2021) which is at the same level of capital lending that only institutions would have access to.

# Flash Loans
Flash loans are a uniquely blockchain and defi possibility. There is no real analog in traditional finance or the surrounding waters. A flash loan is a speedy instrument that involves borrowing funds, using them, and returning them all within a single transaction. To understand how this is possible we'll momentarily discuss a database concept called *atomicity*. Database systems need to update when there is new information, for example, when withdrawing $100 from an ATM the bank's database needs to update the customer account balance. 

The balance update can be further broken down into some substeps: **check this**
1. ATM sends the bank a request to debit $100
2. Bank checks $100 is available & puts a lock on the account so that another update can't come through until this transaction is finished
3. ATM receives the OK and asks bank to debit the funds
4. Bank updates the balance and unlocks the account
5. ATM dispenses cash

If something happens in the electronic communication between steps 2 and 4 the database will rollback the operations and the transaction will fail. The reader may be familiar with an error message similar to "the service is not available, please try again later" which usually means some update has failed somewhere between the user and the server. Atomic comes from the greek atoma which means indivisible; in this case either the update is successfull or its not. There is not grey area where you get $100 and your account does not register the transaction.

Okay, back to flash loans. Here a saavy blockchainer can use the latency in the chain to their advantage. The blocktime for Ethereum is around 12 seconds, allowing plenty of time for a smart contract to borrow money, send it elsewhere, do some stuff, await receipt, and return the money. Due to atomicity, if the money isn't returned or market volatility influences the outcome, the blockchain state will not be updated. A step-by-step view of a flash loan used for arbitrage, all of which is executed in a single block:

1. borrow $1m USDT (it can be a lot of money because collateral isn't necessary as there's no risk of absconding with the cash)
2. Send that $1m USDT to exchange X to buy a TOKEN
3. Send that $1m of TOKEN to exchange Y and sell into USDT for more than $1m (otherwise it wouldn't be profitable)
4. return original $1m USDT + interest & keep the change

If the user tries to settle their loan (step 4) and not return any funds then the entire series of steps if voided and the blockchain retains its state from before the flash loan. However you would lose your fees paid for borrowing the money. [Aave](https://docs.aave.com/faq/flash-loans) charges 0.09% on the principle. In addition to arbitrage, there are two more uses for a flash loan: a collateral swap--settle a loan and within the same transaction deposit different collateral, and self liquidation if you want to release some collateral from a loan.

# Algorithmic Stablecoins
We can categorize stablecoins in three ways: collateralized, algorithmic, or a hybrid. As discussed in [Part I](https://github.com/millecodex/BlockchainNZ_education/blob/main/articles/defi.md#stablecoins), collateralized has some equivallent backing reserved for anyone wanting to redeem their crypto for dollars. This comes with custodial risk for those managing the peg offchain, or with over-collaterization requirements for onchain versions. 

#### *(i) Collateralized* (e.g. USDC, USDT, DAI, RAI)
For a stablecoin to remain pegged to a fiat currency it must be actively managed. Tether issues (mints) new USDT when required and takes USD deposits as backing. As the volume of USDT grows, so does the value of the asset behind it. This creates centralised custodial and [regulatory issues](https://www.theverge.com/2021/10/15/22728253/tether-41-million-misleading-statements-fiat-currency-bitfinex-cftc). If a large number of people want to cash out of their USDS, for example, and back into dollars then this could create a problem for Circle, the company that issues USDC, as they need to be ready and have enough available. Upon redemption they should burn the tokens to provably reduce the circulating supply.

#### *(ii) Algorithmic* (e.g. AMPL, USDx)
As with many things in DeFi there is a push to automate the process and have code be the decentralised arbiter. This trustless algorithmic stablecoin should be scalable and require no maintenance, however, many attempts have been difficult to bootstrap or subject to volatility. Starting a new stable currency with no collateral is risky business for the users and this lack of trust has been apparent in the uptake of these coins.

> **How does it stay pegged at $1?**
> 
> Maintaining the peg in a decentralised manner is of crucial importance for stability. The value of a synthetic USD asset is set by an oracle that can be queried from a smart contract to check that say, 1 dollar is worth 1 USD. In the market these tokens may be exchanged for higher or lower than $1 depending on market factors. If the price rises to $1.01 per token then there is an opportunity for someone to mint new tokens, this costs them $1, and sell them on the market for $1.01, pocketing the difference. As the supply of tokens increases the market price will fall back in line. A similar mechanism occurs when the price drops below $1.00. Say it is $0.99, now you can purchase 100 tokens for $99 in the market, turn around and redeem them from the protocol for $100, profiting $1 for your trouble.

[*Dollar Protocol*](https://docs.dollarprotocol.com/) presents a case study in algorithmic tokenomics with their USD stablecoin USDx. The algorithm allows for rebasing when the price goes above $1.05 or below $0.95 and targets a Uniswap USDx-USDC pool price. The rebasing will expand the supply in times of demand and the newly minted USDx is distributed to protocol stakeholders (token and bond holders & LPs). When the price is low the negative rebase (debase) will cut the supply by proportionally shrinking the number of tokens in users wallets. To avoid this users are incentivised to bond or lock their USDx. Many of the parameters can be modified based on voting through a governance token SHARE that shares in seigniorage profits and fees.

> <img width="800" alt="usdx dollars price chart loses it peg to the USD" src="https://user-images.githubusercontent.com/39792005/150029689-995a1c67-2638-45e1-ad85-a0f1948a0ebb.PNG">
> 
> The chart from CoinGecko shows the market price of USDx had trouble holding its peg.

In the [post mortem](https://medium.com/dollar-protocol/xbond-deprecation-a-post-mortem-4c5c17e21712), it was detailed that the proportion of seigniorage rewards to the bond-holders was too large (50%) such that during positive rebases the newly minted tokens were market sold to recoup previous debt. Eventually demand dried up and too many bond holders were looking to exit back into USDC. The selling pressure broke the USDx peg severely was it was trading at $0.10 by early Febrary after only a few months since launch. As there was nothing backing USDx (its purely algorithmic remember) the bank run can continue all the way to zero. To remedy this Dollar Protocol attempted to pivot to a fractional strategy similar to FRAX (next), but this also has been shuttered due to bootstrapping issues.

Compare this to *Ampleforth* which describes itself as a "durable, fully-algorithmic unit of account [that] returns to a stable price by transferring the volatility of demand to supply, rather than attempting to eliminate volatility" AMPL is not described as a stablecoin because its protocol mediates the supply only and can take much more time to settle towards the target price $1. The supply is adjusted once per day through increasing or decreasing the token balances in user's wallets if the price falls outside a 5% margin.

> <img width="800" alt="ampleforth price and stock 2020 to 2021" src="https://user-images.githubusercontent.com/39792005/150047419-9138f874-c169-4928-97ee-d416913604fd.png">
> 
> Ampleforth's token price has remained around $1 while the stock is free to expand and contract ([source](https://faq.ampleforth.org/durability)).


#### *(iii) Hybrid of Collateral + Algorithmic* (e.g. FRAX, ESD, FEI, RAI)
A hybrid approach can use aspects of collateralization and trustless algorithmic adjustments to mitigate custodial and management risk while capturing efficiencies of automated controls. A successful example here is [FRAX](https://docs.frax.finance/) which is described as a hybrid (fractional) seigniorage shares model. This uses two tokens: FRAX which is soft-pegged to USD and Frax shares (FXS) to incentivise governance. A fraction of the FRAX is collateralized using mostly (but not all) stable cryptocurencies. The remaining fraction is unbacked. The ratio between backed/unbacked can be adjusted to keep its peg. Adjustment functions can be called by any holder and they are rewarded with seigniorage revenue through FXS. Additionally FXS is used for fees accrual and excess collateral value.

According to the Frax [docs](https://docs.frax.finance/conclusion):
> *The novel insight is to use market forces itself to see how much of a stablecoin can be algorithmically stabilized with its own seigniorage token so that it keeps a tight band around $1 like fiatcoins*

The value of FRAX (the peg) is set by an oracle that queries Chainlink for the true value of USD. Market forces allow for arbitrage when the price deviates from $1.00. Minting new tokens costs $1 via a combination of USDC + FXS at the ratio described above, and each token can always be redeemed for $1. If, for example, the price drops to $0.99, you can purchase 100 FRAX for $99 in the market, turn around and redeem them from the protocol for $100, profiting $1 for your trouble.

# DeFi 2.0 - Second Generation Protocols
The name DeFi 2.0 has emerged naturally as people were trying to fix the problems with liquidity mining. The boundary is fluid but the remaining topics I will classify under this 'newer' heading representing the second iteration, perhaps, of decentralised finance.

* pool1/pool2

## Liquidity Owned Protocols
* non-pegged - OHM - A free floating, or non-pegged coin is allowed to fluctuate up as much as demand will tolerate and down to floor based on its treasury. In order to build up the treasury to a sizable value (>~$1B? to back-stop the token) the protocol offers users incentives via a discount to mint new tokens. I.e. you can buy $100 worth of tokens for $95 if you particpate in the bonding program. At the end of a vesting period you are issued the new token that can only be exchanged at market value. 2021 saw immense popularity in Olympus DAO leading the way with about a $700M treasury built up in less than a year at a market value of over $3B.


# Topics unwritten
  * non-pegged stablecoins  & protocol owned liquidity
  * rebasing
  * oracles (~ necessary infrastructure)
  * pool 1 vs. pool 2 (motivation for 2.0 innovation)
  * options/derivatives/perps(dydx) etc 
  * Single-sided staking and IL insurance (Bancor v3)
  * Self-repaying loans(!) Abracadabra/MIM





<p align="center"><img width="800" alt="total-stablecoin-supply-daily" src="https://user-images.githubusercontent.com/39792005/147860382-00470018-aae5-46a7-8d7f-023a2b163a4f.png"></p>

# Third
Table
|Stablecoin|Currency Peg|Backing|Blockchains          |
|:---------|:-----------|:------|:--------------------|
|AUDT      |AUD         |AUD    |Ethereum|

# What did we miss?
* Point form list
  * second

# Further Reading - the very short list
* []()
* []()
* []()

# About the Author
Jeff is a Senior Lecturer in Blockchain & Cryptocurrencies at AUT and an Executive Council member of [BlockchainNZ](https://blockchain.org.nz/). He can be found tweeting about crypto at [@japple](https://twitter.com/Japple).\
[↰ back](https://github.com/millecodex/BlockchainNZ_education#readme)

