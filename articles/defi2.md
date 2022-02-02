[↰ back](https://github.com/millecodex/BlockchainNZ_education#readme)

# DeFi Part II (& 2.0)

# Introduction
In [Part 1.0](defi.md) we covered some foundational parts of DeFi: stablecoins, decentralized exchanges, the automated market maker & pools, liquidity mining and yield farming. Here we're going to start by looking at happens when you can automate some of the behaviour witnessed in part 1.0. Eventually we'll get to [DeFi2.0](defi2.md#defi-20---second-generation-protocols) and discuss algorithmic coins, rebasing, and self-repaying loans.

### Contents
1. [Yield Aggregators & Vaults](defi2.md#yield-aggregators--vaults)
1. [Flash Loans](defi2.md#flash-loans)
1. [Algorithmic Stablecoins](defi2.md#algorithmic-stablecoins)
   - [MakerDAO's DAI](defi2.md#makerdaos-dai)
1. [Pool 1 vs Pool 2 & Vampire Attacks](defi2.md#pool-1-vs-pool-2--vampire-attacks)
1. [DeFi 2.0](defi2.md#defi-20---second-generation-protocols)
   - [Unpegged Stablecoins](defi2.md#olympus-dao--unpegged-stablecoins)
   - [Protocol Owned Liquidity](defi2.md#protocol-owned-liquidity)
   - [Self-repaying Loans](defi2.md#self-repaying-loans)
1. [What did we miss?](defi2.md#what-did-we-miss)
1. [Further Reading - the very short list](defi2.md#further-reading---the-very-short-list)

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

If the user tries to settle their loan (step 4) and not return any funds then the entire series of steps if voided and the blockchain retains its state from before the flash loan. However, you would lose your fees paid for borrowing the money. [Aave](https://docs.aave.com/faq/flash-loans) charges a 0.09% fee on the principle meaning you could borrow $1,000,000 for $900! In addition to arbitrage, there are two more applications for a flash loan: a collateral swap to settle a loan and within the same transaction deposit different collateral, and self-liquidation if you want to release some collateral from a loan.

# Pool 1 vs Pool 2 & Vampire Attacks
The pools used for liquidity provision and mining have evolved into two categories: Pool 1 and Pool 2. The first, Pool 1, represents tokens that are not part of the protocol or governance structure and can be easily moved around to pools with the highest interest rate. These tokens generally have deeper liquidity, are more common, and would still exist without the farm. Examples would be depositing `ETH-USDC` into Sushi. Neither of these tokens have their own governance token, and they can easily move to Yearn if the rates are more attractive. This type of fickle capital behaviour can be called *mercenary capital* as it moves to the highest bidder in a moments notice[^mercenary].
[^mercenary]: On Mercenary Capital: 42% of the yield farmers that enter a farm on the day it launches exit within 24 hours. Around 16% leave within 48 hours, and by the third day 70% of these users would have withdrawn from the contract. Source: Analysis of MasterChef from [Nansen.ai](https://www.nansen.ai/research/all-hail-masterchef-analysing-yield-farming-activity)

Having your liquidity drained from your platform is a problem as it affects onboarding new users and trading activity & fees. The next step is to incentive folks to keep their captial around by offering higher yields in a second pool, in the form of pairs with a native governance token, e.g. `SUSHI`. Now, tokens farming with a SUSHI pairing have higher rewards and aren't as easily moved to a competitor because the `SUSHI-ETH` or `SUSHI-USDC` pool doesn't exist there. 

This balance between Pool 1 and Pool 2 incentivises a new type of risk called a *vampire attack* and is how Sushi got started. When SushiSwap came on the scene in August 2020 it was just a fork of Uniswap and as such needed some bells or whistles to attract funds. It did this by offering very attractive rates for those that staked Uniswap's LP tokens on its platform and gave them the new SUSHI token for doing so. Popularity grew quickly and more people began depositing into SushiSwap pools (to earn SUSHI) and contribute to its AMM. Within a week it grew to over $1B in total value locked (TVL). Weeks later amidst some [drama](https://finematics.com/vampire-attack-sushiswap-explained/) involving its head developer - Chef Nomi - Sushi's TVL dropped down to hundreds of millions, but survived, and now is among the premier AMMs.

> <p align="center"><img width="800" alt="sushi TVL vampire attack" src="https://user-images.githubusercontent.com/39792005/151486262-012d7632-0408-45bf-9af9-bb30249c07df.png"></p>
> SushiSwap launched at the end of August, 2020 and quickly grew to over $1B in TVL

# Algorithmic Stablecoins
Stablecoins like `USDC` and `USDT` are backed by US dollar deposits in the ratio of 1:1. They remain stable because at any time when a user wants to redeem their tokens for dollars the equivallent amount is available to them. This does not mean that the underlying USD remains stable, but for general purposes the US dollar is the most consistently valued (and used) currency. This system requires someone to manage the pool of funds, handle the deposits and redemptions and any associated KYC and regulatory reporting requirements. At the same time this management is the primary risk because the custodian such as Circle or Tether could blacklist addresses, censor clients, obscure transparency and reporting, or perpetrate fraud.

A truly stable unit of account, method of exchange, and store of value in a decentralised manner is the goal of an algorithmic stablecoin. Removing the manager means putting their duties in code on the blockchain. The autonomous coin must:
* maintain a unit of account: for a USD-pegged stablecoin this would be 1 USD, ideally at 1:1, although some small deviation can be expected and is tolerated
* be useful as a method of exchange: the token should be present where it is needed and in enough quantity (liquidity) to function for trade
* represent a store of value such that you can momentarily hold value in the token; i.e. if you transfer $100 into a stablecoin you expect it to have the same purchasing power in the future. How long into the future is a matter of trusting the token to maintain that value.

### MakerDAO's DAI 
The longest-lived algorithmic stablecoin is `DAI` run by [MakerDAO](https://makerdao.com/en/). DAI is pegged to the US-dollar and operates by loaning depositors DAI in exchange for 150% the value of `ETH`. The overcollateralization can absorb some of the volatility of ether, but Maker has mechanisms in place to avoid the value of the collateral dipping below the loaned DAI. In the event of liquidation a user's vault is opened, the ETH sold and the loan closed. This all happens in automatically in the smart contract. The peg of DAI is not set to 1; it must be bought and sold naturally in the market at an equillibrium of $1.00. If the price starts to rise above $1, then there is an opportunity to take out a loan of DAI and sell on the open market for >$1. This will naturally increase the supply and reduce the price. Similarly, if the price is trading at $0.99, borrowers can buy DAI and repay their loans at a discount.

> <p align="center"><img width="800" alt="DAIUSD_chart_trading_view_2022-01-27" src="https://user-images.githubusercontent.com/39792005/151286172-e2d51188-693a-41b7-be40-e53210986cca.png"></p>
> 
> The chart from [Trading View](https://www.tradingview.com/symbols/DAIUSD/) shows the DAI price against the Dollar. There are notable periods of volatility, especially during the March 2020 covid crash where it traded as high as $1.098, and the May 2021 crypto markets crash. 

DAI is a overcollateralized algorithmic stablecoin backed by a combination of cryptocurrency and USDC stablecoin collateral. Overcollateralization represents an inefficiency in capital allocation (extra ETH is unused in my vault) and the partially backed stablecoin situation introduces custodial risks we addressed above. On top of this there is the pricing volatility risk of ether. 

For these reasons there has been an innovative period of new algorithmic stablecoins being deployed, such as `FRAX` which is fractionally collateralized under a variable ratio depending on user confidence, and `RAI` which isn't pegged to any dollar, but has a floating peg. Another notable is Ampleforth's `AMPL` that changes the amount of supply (rebases) to maintain a peg of 1 USD in 2019 inflation adjusted terms. 

> Read more in the full primer on stablecoins [here](https://github.com/millecodex/BlockchainNZ_education/blob/main/articles/stablecoins.md).


# DeFi 2.0 - Second Generation Protocols!
The name DeFi 2.0 has emerged naturally as people were trying to fix the problems with liquidity mining. The boundary is fluid but the remaining topics I will classify under this 'newer' heading representing the second iteration, perhaps, of decentralised finance. (Of course I ~~fear~~ anticipate that by the time I'm finished composing these topics a third gen will have emerged :money_with_wings:)

## Olympus DAO & Unpegged Stablecoins
Another type of ''stablecoin'' has no peg at all. In this sense its not stable as its allowed to float in price to the upside above a crypto-asset backed floor. Olympus DAO is the primary example here with their `OHM` token that is intending to be a "decentralized reserve currency protocol." OHM is a free-floating, or non-pegged coin is allowed to fluctuate up as much as demand (speculation) will tolerate and down to floor based on its treasury. In order to build up the treasury to a sizable value (>~$1B? to back-stop the token) the DAO governing the protocol offers users incentives via a discount to mint new tokens. For example, you can buy $100 worth of tokens for $95 if you particpate in the bonding program. At the end of a vesting period you are issued the new token that can only be exchanged at market value. As of November 2021 Olympus DAO led the way with about a $750M treasury built up in less than a year at a market cap of over $3B. It has since returned to more humble levels inspiring many to call it a Ponzi scheme.

The reason behind this is called *rebases*. Every eight hours new tokens are distributed to current holders increasing their balance. This is a highly inflationary supply and results mathematically in a high annual percentage compounding rate (APY). Sky high. Crazy high. :rocket: Tens-of-thousands of percent. Can that be right? Well yes and no. Its correct because if you held for a year you would have dramatically more tokens, but its incorrect because price is excluded from the marketing. The inflationary pressure will push the price down unless counteracted by demand. 

> <p align="center"><img width="800" alt="olympus dao OHM price chart" src="https://user-images.githubusercontent.com/39792005/152081921-bd20db38-44d2-45a6-b2fb-73f39eb3d427.PNG"></p>
> 
> The risk-free market value of backing per OHM shows the unpegged nature as it trades at multiples above the 1 `DAI` floor ([Dune Analytics](https://dune.xyz/shadow/Olympus-(OHM))).


These rebasing protocols are still in their infancy, and thus high risk. There is at least one for every main chain. [Invictus DAO](https://medium.com/@Sol-Invictus/the-great-event-9a3d81e0ce3b) even rebases continually so you can watch your token balance increase in realtime.

One of the innovations the rebasing era has brought to DeFi is *protocol owned* liquidity.

## Protocol Owned Liquidity
Lets pause for a moment and conside who *owns* the tokens that are criss crossing DeFi-land. Although it seems obvious─it should be the users, right?─it may not always be so. Standard yield farming pools use liquidity that is owned by the users. All participants receive a receipt of their share of the pool and that gives them the right to redeem it at any time. This has led to the mercenary capital situation described above. *This* then led to Pool 2 with governance tokens. So user-owned liquidity is good for users but bad for protocols which in turn can be bad for the user's bottom line, such as when the governance token apprecates in value and causes impermanent loss in the pool.

One way around this is to implement delays that lock up your tokens for a set amount of time thus guaranteeing a minimum amount of liquidity. This is the same as venture capitalists being restricted in when they can sell newly floated investments stock. Time delays as long as four years can be seen in Curve thereby boosting your rewards. Incredibly the average locktime on Curve is 3.63 years indicating high user confidence. Other lockups (although not specifically in liquidity pools): 
* C.R.E.A.M. staking periods of 1-4 years
* parachain auctions on Polkadot require 96 weeks
* Eth2 validators require 32 ether locked up for at least one year, and possibly longer depending on the rollout

Lockups can buy time but don't solve the problem, merely delaying the sell pressure.

A third option may be the best yet. Protocol owned liquidiy as pioneered in Olympus DAO is simple in the intention: rather than having users deposit any assets and shop their LP tokens to the highest APY the users purchase protocol tokens with them. The LP tokens are then *locked* in the treasury. The benefit is twofold: discounted tokens are available through the bonding process, and stakers are rewarded with the astronomical interest rates helped along by the autocompounding rebasing. The DAO will maintain the treasury, accepting stable LP tokens thus having control over the floor price. They also collect pool fees directly which acts as cash flow and can offset downward token volatility. By design the high interest rates in the short term incentivise growth, then will fall and in the long run this should stabilize the token price. 

One issue we've seen in the DeFi2.0 era is that people are excited about this rebasing concept and speculation has caused the tokens to rise well above the treasury-backed floor. This causes newcomers to have to purchase at a much higher price. It worth noting here that this is what floating currencies do. Unfortunately as of the time of writing (February 2022) many people bought at a price greater than the mark price; in short, it couldn't go up forever. This doesn't mean the floor 'peg' broke because every token is still backed by the same amount of underlying, just at multiples below market price (see the previous chart).

## Self-repaying Loans
Due to the trustless nature of DeFi lending requires overcollateralization. To borrow $500 you must deposit more than $500 of some accepted token. This removes the insolvency risk on the lender and helps absorb market volatility, especially for non-stablecoins. The lender now has many option of how to use collateral in their favour to make more money. This [rehypothecation](https://www.investopedia.com/terms/r/rehypothecation.asp) is what banks do with your house deposit. 

Now, if that $1000 loan collateral is in a stablecoin and deposited in a Yearn vault it can earn interest while waiting for the loan to mature. And if the interest is used to pay down the loan the maturity date can be removed altogether. This is the idea behind a self-repaying loan. [Alchemix](https://alchemix-finance.gitbook.io/alchemix-finance/) has requirements on acceptable collateral to ensure that it can generate income. The collateral goes straight to work in a vault and they loan out 50% in their own stablecoin. After depositing $1000 the borrower recieves $500 to do as they please knowing their loan will pay itself back.

## Single-Sided Staking and Impermanent Loss Insurance
[Bancor](https://bancor.network/) introduced both single-sided staking and [impermanent loss](defi.md#impermanent-loss) (IL) protection insurance with their version 2 protocol. Single-sided staking allows deposits into a pool with a single token rather than the multiple token approach required of other LPs. This opens up fees and rewards for those that want long exposure to a token without the risk of having a secondary token tied up in a pairing. Behind the scenes the protocol matches single-sided deposits with the Bancor token `BNT` to behave as a standard [AMM](defi.md#automated-market-makers-amms).

A benefit here is that Bancor can redistribute IL risk from the LP to the protocol. This smooths price diveregence across all pairs and they use income from co-investments to cover loss. A position becomes fully insured after 100 days by incrementing the protection 1% per day. If someone withdraws within 100 days and experience IL they are eligible for partial protection. Someone that waited 100 days or more and withdraws is fully insured. The upcoming Bancor V3 is promising instant IL protection for every LP.

# What did we miss?
Many folks have made fancy bricks to help build the DeFi citadel. Perhaps you, dear financier, are interested in:
* Futures? [dydx](https://dydx.exchange/) is a DEX that can facilitate perpetual futures contracts on layer 2 via Starkware.
* Covered-calls? [Ribbon Finance](https://www.ribbon.finance/) earns yield on its deposits by running a weekly automated options selling strategy.
* Miner-extractable Value? or MEV as its known presents a large profit opportunity and risk. [Read Charlie Noyes' take](https://research.paradigm.xyz/MEV).

# Next
* :point_right: [My full primer on Stablecoins](https://github.com/millecodex/BlockchainNZ_education/blob/main/articles/stablecoins.md)

# Further Reading - the very short list
* [Olympus DAO FAQ](https://docs.olympusdao.finance/main/basics/basics)
* [The Liquidity Loyalty Problem](https://posey.medium.com/the-liquidity-loyalty-problem-7e999f912080)
* [The Alchemix Whitepaper (and a short history of DeFi)](https://alchemix.fi/c76d1d663f6c8247b86a8fca83d5bd1b.pdf)

# About the Author
Jeff is a Senior Lecturer in Blockchain & Cryptocurrencies at AUT and an Executive Council member of [BlockchainNZ](https://blockchain.org.nz/). He can be found tweeting about crypto at [@japple](https://twitter.com/Japple).\
[↰ back](https://github.com/millecodex/BlockchainNZ_education#readme)

