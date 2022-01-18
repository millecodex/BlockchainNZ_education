[↰ back](https://github.com/millecodex/BlockchainNZ_education#readme)

# DeFi Part II (& 2.0)

# Introduction
In Part 1.0 we covered some foundational parts of DeFi: stablecoins, decentralized exchanges, the automated market maker & pools, liquidity mining and yield farming. Here we're going to start by looking at happens when you can automate some of the behaviour witnessed in part 1.0. Eventually we'll get to [DeFi2.0](defi2.md#DeFi2.0) and discuss algorithmic coins, rebasing, and self-repaying loans.

### Contents
1. [Yield Aggregators & Vaults](defi2.md#intro)
1. [Flash Loans](defi2.md#second)
1. [](defi2.md#third)
1. [What did we miss?](defi2.md#what-did-we-miss)
1. [Further Reading - the very short list](defi2.md#further-reading---the-very-short-list)

# Yield Aggregators & Vaults
The winter of Defi (2020; Summer in the northern hemisphere) looked at yields coming out of farms and saw the trend of capital hopping around to the projects with the highest interest rate. So a simple question arises: how can I, a simple investor, capture some of this yield by moving my coins (without gas fees eating into my profits)?

[Andre Cronje](https://andrecronje.medium.com/) was there with *yEarn* to automatically move investments between *dydx*, *Compound*, and *Aave*. The native governance token, YFI, was advertised as having no value and was distributed through a liquidity mining program to users and was so successful it now trades at tens of thousands of dollars.

> "we have released YFI, a completely valueless 0 supply token. We re-iterate, it has 0 financial value. There is no pre-mine, there is no sale, no you cannot buy it, no, it won’t be on uniswap, no, there won’t be an auction. We don’t have any of it."\
-*Andre Cronje on the [launch of YFI](https://medium.com/iearn/yfi-df84573db81) explicity stating that there are no tokens reserved for insiders, specifically VCs*

As with other successful DeFi Legos, this model was copied eagerly and now aggregators and vaults are common. The present version of [yearn.finance](yearn.finance) offers a vault for depositing tokens that then use strategies such as shifting capital, auto-compounding, and rebalancing to earn yield. These vaults offer self-custody and allow withdrawals at any time, both features which represent reduced risk to the user. 

Another feautre of many DeFi protocols is borowing and lending because of the simplicity of doing it in a trustless blockchain environment. In this scenario the lender earns interest directly from the borrower in an almost peer-to-peer transaction. The third party here holds the collateral and facilitates the *bank*. As an example Yearn offers loans of DAI at 1.35% APY (as of Jan. 2021) which is at the same level of capital lending that only institutions would have access to.

# Flash Loans
Flash loans are a uniquely blockchain and defi possibility. There is no real analog in traditional finance or the surrounding waters. A flash loan is a speedy instrument that involves borrowing funds, using them, and returning them all within a single transaction. To understand how this is possible we'll momentarily discuss a database concept called *atomicity*. Database systems need to update when there is new information, for example, when withdrawing $100 from an ATM the bank's database needs to update the customer account balance. 

The balance update can be further broken down into some substeps:
1. ATM sends the bank a request to debit $100
2. Bank checks $100 is available & puts a lock on the account so that another update can't come through until this transaction is finished
3. ATM receives the OK and asks bank to debit the funds
4. Bank updates the balance and unlocks the account
5. ATM dispenses cash

If something happens in the electronic communication between steps 2 and 4 the database will rollback the operations and the transaction will fail. The reader may be familiar with an error message similar to "the service is not available, please try again later" which usually means some update has failed somewhere between the user and the server. Atomic comes from the greek atoma which means indivisible; in this case either the update is successfull or its not. There is not grey area where you get $100 and your account does not register the transaction.

Okay, back to flash loans. Here a saavy blockchainer can use the latency in the chain to their advantage. The blocktime for Ethereum is around 12 seconds, allowing plenty of time for a smart contract to borrow money, send it elsewhere, do some stuff, await receipt, and return the money. Due to atomicity, if the money isn't returned or market volatility influences the outcome, the blockchain state will not be updated. A step-by-step view of a flash loan used for arbitrage, all of which is executed in a single block:

1. borrow $1 m USDT (it can be a lot of money because collateral isn't necessary as there's no risk of absconding with the cash)
2. Send that $1 m USDT to exchange X to buy a TOKEN
3. Send that $1 m of TOKEN to exchange Y and sell into USDT for more than $1 m (otherwise it wouldn't be profitable)
4. return original $1 m USDT + interest & keep the change

If the user tries to settle their loan (step 4) and not return any funds then the entire series of steps if voided and the blockchain retains its state from before the flash loan. However you would lose your fees paid for borrowing the money. [Aave](https://docs.aave.com/faq/flash-loans) charges 0.09% on the principle. In addition to arbitrage, there are two more uses for a flash loan: a collateral swap to settle a loan and within the same transaction deposit different collateral, and self liquidation if you want to release some collateral from a loan.

# Topics unwritten

  * algorithmic stablecoins - USDN, FEI, FRAX, UST: see Messario 2021 report p.120.
  * non-pegged stablecoins & protocol owned liquidity
  * rebasing
  * oracles (~ necessary infrastructure)
  * pool 1 vs. pool 2 (motivation for 2.0 innovation)
  * options/derivatives/perps(dydx) etc 
  * Single-sided staking and IL insurance (Bancor v3)
  * Self-repaying loans(!) Abracadabra/MIM

# Algorithmic Stables 
* USDN, FEI, FRAX, UST: see Messario 2021 report p.120.

# Liquidity Owned Protocols
* pool1/pool2
* non-pegged - OHM - A free floating, or non-pegged coin is allowed to fluctuate up as much as demand will tolerate and down to floor based on its treasury. In order to build up the treasury to a sizable value (>~$1B? to back-stop the token) the protocol offers users incentives via a discount to mint new tokens. I.e. you can buy $100 worth of tokens for $95 if you particpate in the bonding program. At the end of a vesting period you are issued the new token that can only be exchanged at market value. 2021 say immense popularity in Olympus DAO leading the way with about a $700M treasury built up in less than a year at a market value of over $3B.
* rebasing
* options/derivatives/perps(dydx) etc 

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

