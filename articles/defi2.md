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
Twenty-twenty was the *Summer of Defi* (winter in the southern hemisphere) and folks looked at yields coming out of farms and saw the trend of capital hopping around to the projects with the highest interest rate. A simple question arises: how can I, a simple investor, capture some of this yield by moving my coins to the new farm with the highest yield (without gas fees eating into my profits)?

[Andre Cronje](https://andrecronje.medium.com/) was there with *yEarn* to automatically move investments between *dydx*, *Compound*, and *Aave*. Users would deposit their tokens into a yVault, receive a `yvToken` in return, and have their underlying tokens get deployed behind the scenes to a protocol such as Compound, earning `COMP`, which is then sold for the user's token increasing the amount in their vault. yEarn's native governance token, `YFI`, was advertised as having no value and was distributed through a liquidity mining program to users and was so successful it now trades at tens of thousands of dollars.

> "we have released YFI, a completely valueless 0 supply token. We re-iterate, it has 0 financial value. There is no pre-mine, there is no sale, no you cannot buy it, no, it won’t be on uniswap, no, there won’t be an auction. We don’t have any of it."\
-*Andre Cronje on the [launch of YFI](https://medium.com/iearn/yfi-df84573db81) explicity stating that there are no tokens reserved for insiders, specifically VCs*

As with other successful DeFi Legos, this model was copied eagerly and now aggregators and vaults are common. The present version of [yearn.finance](yearn.finance) offers a vault for depositing tokens that then use strategies such as shifting capital, auto-compounding, and rebalancing to earn yield. These vaults offer self-custody and allow withdrawals at any time, both features which represent reduced risk to the user. 

Another feautre of many DeFi protocols is borowing and lending because of the simplicity of doing it in a trustless blockchain environment. In this scenario the lender earns interest directly from the borrower in an almost peer-to-peer transaction. The third party here holds the collateral and facilitates the *bank*. As an example Yearn offers loans of `DAI` at 1.35% APR and [Aave](https://aave.com/) offers loans of `USDC` at 1.12% APR (as of Jan. 2021) which is at the same level of capital lending that only institutions would have access to.

# Flash Loans
Flash loans are a uniquely blockchain and defi possibility. There is no real analog in traditional finance or the surrounding waters. A flash loan is a speedy instrument that involves borrowing funds, using them, and returning them all within a single transaction. To understand how this is possible we'll momentarily discuss a database concept called *atomicity*. Database systems need to update when there is new information, for example, when withdrawing $100 from an ATM the bank's database needs to update the customer account balance. 

A single ATM transaction can be  broken down into substeps:
1. ATM sends the bank a request to debit $100
2. Bank checks $100 is available & puts a lock on the account so that another update can't come through until this transaction is finished
3. ATM receives the OK and asks bank to debit the funds
4. Bank updates the balance and unlocks the account
5. ATM dispenses cash

If something happens in the electronic communication between steps 2 and 4 the database will rollback the operations and the transaction will fail. The reader may be familiar with a type of online error message similar to *"the service is not available, please try again later"* which usually means some update has failed somewhere between the user and the server. In these cases the intermediate steps of the update are discarded and the database reverts back to before the update attempt. Atomic comes from the Greek *atomos* which means indivisible; in this case either the update is successfull or its not. There is no grey area where you get $100 and your account does not register the transaction.

Okay, back to flash loans. Here a savvy blockchainer can use the latency in the chain to their advantage. The blocktime for Ethereum is around 12 seconds, allowing plenty of time for a smart contract to borrow money, send it elsewhere, do some stuff, await receipt, and return the money. Due to atomicity, if the money isn't returned or market volatility influences the outcome and not enough is returned, the blockchain state will not be updated. This also means that there is no risk in that loan for the borrower and the lender. 

A step-by-step view of a flash loan used for arbitrage, all of which is executed in a single block:
1. Borrow $1m USDT (it can be a lot of money because collateral isn't necessary as there's no risk of absconding with the cash)
2. Send that $1m USDT to exchange X to buy a TOKEN
3. Send that $1m of TOKEN to exchange Y and sell into USDT for more than $1m (otherwise it wouldn't be profitable)
4. Return original $1m USDT + interest & fees & keep the change

If the user tries to settle their loan (step 4) and not return any funds then the entire series of steps if voided and the blockchain retains its state from before the flash loan. However, you would lose your fees paid for borrowing the money. [Aave](https://docs.aave.com/faq/flash-loans) charges a 0.09% fee on the principle meaning you could borrow $1,000,000 for $900!. In addition to arbitrage, there are two more uses for a flash loan: a collateral swap to settle a loan and within the same transaction deposit different collateral, and self liquidation if you want to release some collateral from a loan.

# Algorithmic Stablecoins
Stablecoins like `USDC` and `USDT` are backed by US dollar deposits in the ratio of 1:1. They remain stable because at any time when a user wants to redeem their tokens for dollars the equivallent amount is available to them. This does not mean that the underlying USD remains stable, but for general purposes the US dollar is the most consistently valued (and used) currency. This system requires someone to manage the pool of funds, handle the deposits and redemptions and any associated KYC and regulatory reporting requirements. At the same time this management is the primary risk because the custodian such as Circle or Tether could blacklist addresses, censor clients, obscure transparency and reporting, or perpetrate fraud.

A truly stable unit of account, method of exchange, and store of value in a decentralised manner is the goal of an algorithmic stablecoin. Removing the manager means putting their duties in code on the blockchain. The autonomous coin must:
* maintain a unit of account: for a USD-pegged stablecoin this would be 1 USD, ideally at 1:1, although some small deviation can be expected and is tolerated
* be useful as a method of exchange: the token should be present where it is needed and in enough quantity (liquidity) to function for trade
* represent a store of value such that you can momentarily hold value in the token; i.e. if you transfer $100 into a stablecoin you expect it to have the same purchasing power in the future. How long into the future is a matter of trusting the token to maintain that value.

### MakerDAO's DAI 
The longest-lived algorithmic stablecoin is `DAI` run by MakerDAO. DAI is pegged to the US-dollar and operates by loaning depositors DAI in exchange for 150% the value of `ETH`. The overcollateralization can absorb some of the volatility of ether, but Maker has mechanisms in place to avoid the value of the collateral dipping below the loaned DAI. In the event of liquidation a user's vault is opened, the ETH sold and the loan closed. This all happens in automatically in the smart contract. The peg of DAI is not set to 1; it must be bought and sold naturally in the market at an equillibrium of $1.00. If the price starts to rise above $1, then there is an opportunity to take out a loan of DAI and sell on the open market for >$1. This will naturally increase the supply and reduce the price. Similarly, if the price is trading at $0.99, borrowers can buy DAI and repay their loans at a discount.

> <p align="center"><img width="800" alt="DAIUSD_chart_trading_view_2022-01-27" src="https://user-images.githubusercontent.com/39792005/151286172-e2d51188-693a-41b7-be40-e53210986cca.png"></p>
> 
> The chart from [Trading View](https://www.tradingview.com/symbols/DAIUSD/) shows the DAI price against the Dollar. There are notable periods of volatility, especially during the March 2020 covid crash where it traded as high as $1.098, and the May 2021 crypto markets crash. 

DAI is a overcollateralized algorithmic stablecoin backed by a combination of cryptocurrency and USDC stablecoin collateral. Overcollateralization represents an inefficiency in capital allocation (extra ETH is unused in my vault) and the partially backed stablecoin situation introduces custodial risks we addressed above. On top of this there is the pricing volatility risk of ether. 

For these reasons there has been an innovative period of new algorithmic stablecoins being deployed, such as `FRAX` which is fractionally collateralized under a variable ratio depending on user confidence, and `RAI` which isn't pegged to any dollar, but has a floating peg. Another notable is Ampleforth's `AMPL` that changes the amount of supply (rebases) to maintain a peg of 1 USD in 2019 inflation adjusted terms. 

> Read more in the full primer on stablecoins [here](https://github.com/millecodex/BlockchainNZ_education/blob/main/articles/stablecoins.md).


# DeFi 2.0 - Second Generation Protocols!

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
  * Self-repaying loans(!) Alchemix/Abracadabra/MIM





<p align="center"><img width="800" alt="total-stablecoin-supply-daily" src="https://user-images.githubusercontent.com/39792005/147860382-00470018-aae5-46a7-8d7f-023a2b163a4f.png"></p>


# What did we miss?
* 

# Next
* :point_right: [My full primer on Stablecoins](https://github.com/millecodex/BlockchainNZ_education/blob/main/articles/stablecoins.md)

# Further Reading - the very short list
* [Beware the Coupon Clipper: The Insurmountable Flaws of so-called Algorithmic Stablecoins](http://thinking.farm/essays/2021-01-17-beware-the-coupon-clipper/)
* []()

# About the Author
Jeff is a Senior Lecturer in Blockchain & Cryptocurrencies at AUT and an Executive Council member of [BlockchainNZ](https://blockchain.org.nz/). He can be found tweeting about crypto at [@japple](https://twitter.com/Japple).\
[↰ back](https://github.com/millecodex/BlockchainNZ_education#readme)

