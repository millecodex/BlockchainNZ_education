[↰ back](https://github.com/millecodex/BlockchainNZ_education#readme)

# What is Ethereum?
First, a brief history of the problems that Vitalik Buterin was looking to solve. 

Bitcoin provided a solution to the double-spend problem of creating digital cash by using proof-of-work mining to both maintain the state of the ledger and allow open participation in the network based on computing power. By assigning value to these digitally scarce coins the ledger can be used as a monetary system. This works great for money but comes up short when using Bitcoin's scripting language to make simple extensions such as a decentralized exchange -- how to determine the NZD/BTC rate? or how to do some arbitrary calculation, e.g. what is the probability that your game character encounters a villan?

While writing for *Bitcoin Weekly* and co-founding [*Bitcoin Magazine*](https://bitcoinmagazine.com/), Vitalik saw the limitations in Bitcoin as an opportunity to create a new blockchain from scratch that can allow developers to build general applications. The first feature to include in this new blockchain was *Turing completness*. In computer programming this means it is possible to have loops in the code which would be necessary, for example, for calculating a probability or the value of pi. Bicoin's *script* language is not considered Turing complete because it is stack-based and therefore anything that is needed by the program must be loaded onto the stack. (Also, by definition stacks cannot loop.) 

The second feature was to use an account-based system. The benefit of this style is that each account (address) has a balance *and* the option of some code and storage. (This is in contrast to Bitcoin that uses a UTXO model I won't detail here but basically can only keep track of coins and not any additional data or code.)

### Summarized in the whitepaper, Ethereum is:
> a blockchain with a built-in Turing-complete programming language, allowing anyone to write smart contracts and decentralized applications where they can create their own arbitrary rules for ownership, transaction formats and state transition functions.

The whitepaper for *Ethereum* was published online in 2013 and a year later a formal specification was written by Gavin Wood and the project raised funds through their initial coin offering. This was followed by the network launch in 2015.

# Initial Coin Offering
In order to fund their new proposed blockchain network, the founders embarked on a unique fundraising scheme that laid down the template for future crowdfunding sales. An initial coin offering (ICO) seeks to bootstrap user adoption and funding by combining the style of an initial public offering (IPO) with a crowd fund model. A marked difference from the IPO model is that the token sale was open to anyone without geographic or regulatory restriction. All users had to do to participate was deposit bitcoin and receive *ether* tokens that represent their stake in the new network. The token sale was successful resulting in more than 50 million ether (the native currency of ethereum) being sold. Investors were aware of the token distribution from the beginning which included 9.9% of the tokens reserved for the founders (to fund development, salaries, bug bounties, etc.) and another 9.9% for a [foundation](https://ethereum.foundation/) that was set up to guide the long term mission of the network. These tokens didn't have to be purchased in a traditional sense; a practice now known as *pre-mining*.

### ICO Boom Times
The success of Ethereum's ICO and its smart contract capability combined with its open source code made it an ideal model for other founders to fund their projects. A new project could easily copy and modify smart contract code and host their own ICO and issue their own new ERC-20 tokens. (ERC-20 refers to the token standard that most coins that run on Ethereum use.) 2017--2018 was a boom period for ICOs with many projects and tokens launching. Unfortunately many of them had questionable products and practices or were outright scams and because there was no regulation in crypto (as there is for an IPO), there was no recourse for those that invested and lost their money (this author included 🙃). 

# Smart Contracts
The term *smart contract* refers to some executable code that lives on the blockchain. This code may be a snippet, small or large, it may be straightforward or complex, it may contain bugs, not compile, it may never even be executed. Ethereum allows for code to be stored on the blockchain in *contracts* which have a callable address that looks just like a user's address. All of these bits of code are generically called smart contracts. Pedants will like to tell you that they are not smart nor are they contractual and they might be right in a traditional sense, however, the term has come to be redefined in a blockchain context.

Earlier we mentioned that Ethereum is turing-complete, and here is where that comes in. A developer can write a program, say to issue crop insurance based on weather data, and store this program in a smart contract on the blockchain. As the blockchain is immutable this code will live there forever, it is also visible and thus can be easily verified or audited. The only limits to the applications that can be deployed on Ethereum come from the creativity & skill of the developer, and the amount of computation that program needs to do.

### Gas
Computation occurs in the EVM (Ethereum virtual machine) and well we will be light on details, because its a blockchain, all the nodes need to have a copy of the data and verify any updates. This includes running *all* smart contracts and doing *any* calculation. A scenario could arise, either accidentally or maliciously, to halt the network by deploying a contract with an infinite loop:
```
int i=1
while i>0
  i=i+1
 ```
The simple code above continually updates the counter because the stop condition of i being less than or equal to 0 is never met. To avoid this scenario all computation in the EVM needs gas. As a contract is executed gas is consumed and if the contract runs out of the gas then the update fails. All gas is paid in ether (ETH) and goes to the nodes (miners) that perform the calculations. A follow up question is what if I am wealthy and have enough gas to spam the network in this manner? To prevent this there is a gas limit on all transactions that is calculated based on how busy the network is.
> The recent *London* upgrade to Ethereum changed the way that gas is distributed. Previously the miner would be compensated by receiving the entire gas fee in the transaction. Now, part of this fee is *burned*, and the miner gets the remainder. Burning some ETH reduces the overall issuance. More in the section on Proof-of-Work.

# dapps
Decentralised applications, or *dapps* just refer to smart contracts that are executed on a blockchain. In the case of Ethereum it is generally accepted that these applications are indeed decentralised meaning that they can't be censored and everyone has a fair chance to use them (subject to being able to pay gas fees).

The [most used dapps](https://dappradar.com/rankings/protocol/ethereum) on Ethereum in 2021:

| App         | Category | Users (k) |
|--------------|:-----:|-----------:|
| Uniswap      |  Decentralised Exchange |    520 |
| OpenSea |  NFT Marketplace |   304 |
| MetaMask Swap  |  Decentralised Exchange |    166 |
| Polygon Bridge      |  Decentralised Exchange |    114 |
| Sushi      | Decentralised Exchange  |    98 |

* stable coins
* defi
* dapps
* nfts / cryptokitties / punks
* 
# I thought Ethereum was Proof-of-Stake?
* from the ICO 26% of tokens were reserved to be distributed to the miners
* Proof-of-Stake? difficulty bomb / ETH 2.0
* unlimited supply

# What did we miss?
* scaling & ETH 2.0
** sharding
** rollups
* DAO hack
* Layer 1's versus Layer 2's, for example Bitcoin and Ethereum are considered base layer or layer 1 blockchains. Layer 2 blockchains look to extend the base layer and improve performance. Presently Polygon and Arbitrum are extending and improving the performance and reducing fees for Ethereum. 

# Further Reading - the very short list
* [The Whitepaper by Vitalik Buterin](https://ethereum.org/en/whitepaper/)
* [The Yellowpaper by Gavin Wood](https://github.com/ethereum/yellowpaper), & [pdf](https://ethereum.github.io/yellowpaper/paper.pdf)

# About the Author
Jeff is a Senior Lecturer in Blockchain & Cryptocurrencies at AUT and an Executive Council member of BlockchainNZ\
[↰ back](https://github.com/millecodex/BlockchainNZ_education#readme)
