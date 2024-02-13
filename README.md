# blockchain-tech-slack

> Curated list of resources for the development and applications of block chain.

The blockchain is an incorruptible digital ledger of economic transactions that can be programmed to record not just financial transactions but virtually everything of value (by [Don Tapscott](https://www.linkedin.com/pulse/whats-next-generation-internet-surprise-its-all-don-tapscott)).

<font color=#0099ff size=3>**This is not a simple collection of Internet resources, but verified and organized data ensuring it's really suitable for your learning process and useful for your development and application.**</font>

## Contents
<details><summary>Click to expand</summary>

- [blockchain-tech-slack](#blockchain-tech-slack)
  - [Contents](#contents)
  - [Frequently Asked Questions (F.A.Q.s) & Answers](#frequently-asked-questions-faqs--answers)
  - [Basic Introduction](#basic-introduction)
  - [Development Tutorial](#development-tutorial)
  - [Releated Tools](#releated-tools)
    - [Solidity](#solidity)
    - [truffle](#truffle)
    - [web3.js](#web3js)
  - [Further Extension](#further-extension)
    - [Papers](#papers)
    - [Books](#books)
  - [Contribute](#contribute)

</details>

## Frequently Asked Questions (F.A.Q.s) & Answers

**Q: What's a Blockchain?**

A: A blockchain is a distributed database with a list (that is, chain) of records (that is, blocks) linked and secured by
digital fingerprints (that is, crypto hashes).
Example from [`genesis_block.json`](https://github.com/yjjnls/awesome-blockchain/tree/master/src/js/genesis_block.json):

```js
{
    "version": 0,
    "height": 1,
    "previous_hash": null,
    "timestamp": 1550049140488,
    "merkle_hash": null,
    "generator_publickey": "18941c80a77f2150107cdde99486ba672b5279ddd469eeefed308540fbd46983",
    "hash": "d611edb9fd86ee234cdc08d9bf382330d6ccc721cd5e59cf2a01b0a2a8decfff",
    "block_signature": "603b61b14348fb7eb087fe3267e28abacadf3932f0e33958fb016ab60f825e3124bfe6c7198d38f8c91b0a3b1f928919190680e44fbe7289a4202039ffbb2109",
    "consensus_data": {},
    "transactions": []
}
```

![](Basic/img/blockchain-jesus.png)

**Q: What's a Hash? What's a (One-Way) Crypto(graphic) Hash Digest Checksum**?

A: A hash e.g. `d611edb9fd86ee234cdc08d9bf382330d6ccc721cd5e59cf2a01b0a2a8decfff`
is a small digest checksum calculated
with a one-way crypto(graphic) hash digest checksum function
e.g. SHA256 (Secure Hash Algorithm 256 Bits)
from the data. Example from [`crypto.js`](https://github.com/yjjnls/awesome-blockchain/blob/master/src/js/crypto.js):

```js
function calc_hash(data) {
    return crypto.createHash('sha256').update(data).digest('hex');
}
```

A blockchain uses

-   the block header (e.g. `Version`, `TimeStamp`, `Previous Hash...` )and
-   the block data (e.g. `Transaction Data...`)

to calculate the new hash digest checksum.

**Q: What's a Merkle Tree?**

A: A Merkle tree is a hash tree named after Ralph Merkle who patented the concept in 1979
(the patent expired in 2002). A hash tree is a generalization of hash lists or hash chains where every leaf node (in the tree) is labelled with a data block and every non-leaf node (in the tree)
is labelled with the crypto(graphic) hash of the labels of its child nodes. For more see the [Merkle tree](https://en.wikipedia.org/wiki/Merkle_tree) Wikipedia Article.

Note: By adding crypto(graphic) hash functions you can "merkelize" any data structure.

**Q: What's a Merkelized DAG (Directed Acyclic Graph)?**

A: It's a blockchain secured by crypto(graphic) hashes that uses a directed acyclic graph data structure (instead of linear "classic" linked list).

Note: Git uses merkelized dag (directed acyclic graph)s for its blockchains.

**Q: Is the Git Repo a Blockchain?**

A: Yes, every branch in the git repo is a blockchain.
The "classic" Satoshi-blockchain is like a git repo with a single master branch (only).

**More Q&A**
- [Blockchain Interview Questions](https://mindmajix.com/blockchain-interview-questions)
- [10 Essential Blockchain Interview Questions](https://www.toptal.com/blockchain/interview-questions)
- [Top 36 Blockchain Job Interview Questions & Answers](https://blockchainsfactory.com/blockchain-interview-questions/)

---
## Basic Introduction

<!--    
### Encryption knowledge
   -->

-   **Encryption knowledge**  
    * [Basic concepts](https://www.jianshu.com/p/a044b303f7d5) - Asymmetric encryption, Digital signature, Certificate  
    * [Digital signature extension](https://www.jianshu.com/p/410e77ec23fa)  - Multi-signature, Blind signature, Group signature, Ring signature
    * [Merkle tree](https://www.jianshu.com/p/a044b303f7d5)  
    <!-- * [Merkle tree in blockchain](./Basic/merkle_tree_in_blockchain.md)   -->
    * [Merkle DAG](http://www.sohu.com/a/247540268_100222281)   
    * [**CryptoNote v2.0**](https://cryptonote.org/whitepaper.pdf) - Untraceable Transactions and Egalitarian Proof-of-work
<!--   
### Consensus
    -->
-   **Consensus**  
    * [Proof of Work](https://www.jianshu.com/p/3462f2ed74d7)
    * [Proof of Stake](https://www.jianshu.com/p/2fd3bce523b0)
    * [Proof of Stake FAQs](https://github.com/ethereum/wiki/wiki/Proof-of-Stake-FAQs) / [Chinese version](https://ethfans.org/posts/Proof-of-Stake-FAQ-new-2018-3-15)
    * [Delegated Proof of Stake](https://www.jianshu.com/p/ccc3fff7a60d)
    * [Practical Byzantine Fault Tolerance](https://www.jianshu.com/p/e991c1385f9f)

<!--    
### Account and transaction model
    -->
-   **Account and transaction model**  
    * [UTXO model](https://www.jianshu.com/p/2f4e75dbc2e4)
<!--
### Exchange
    -->
-   **Exchange**  
<!--
### Applications
    -->
-   **Applications**  
    * [Do You Need a Blockchain?](https://spectrum.ieee.org/computing/networks/do-you-need-a-blockchain)  
    * [What can't blockchain do?](https://www.jianshu.com/p/70f6a29a6296)  
<!--     
### Governance
    -->
-   **Governance**
    * [Blockchains should not be democracies](https://haseebq.com/blockchains-should-not-be-democracies/)                                       
<!-- * [](https://github.com/yfeng125/blockchain-tutorial/blob/master/doc/%E2%80%8B25.%E6%AF%94%E7%89%B9%E5%B8%81%EF%BC%9A%E6%89%A9%E5%AE%B9%E4%B9%8B%E4%BA%89%E3%80%81IFO%E4%B8%8E%E9%93%BE%E4%B8%8A%E6%B2%BB%E7%90%86.md)   -->


<!--     
### Digital currency ranking
    -->
-   **[Digital currency ranking](https://coinmarketcap.com/)**   

---
## Development Tutorial


## Releated Tools

### Solidity
-   [doc](https://solidity.readthedocs.io/en/develop/index.html) 

### truffle
-   [BlockChain KickStarter From Scratch](https://prasannabrabourame.medium.com/blockchain-kickstarter-from-scratch-9a3906596cd0)

### web3.js
-   [doc](https://web3js.readthedocs.io/en/1.0/) 

---
## Further Extension
### [Papers](https://github.com/decrypto-org/blockchain-papers)

### Books

-   [**Blockchain guide**](https://yeasy.gitbooks.io/blockchain_guide/content/) by Baohua Yang, 2017 --
    Introduce blockchain related technologies, from theory to practice with bitcoin, ethereum and hyperledger.
    <!-- -   [区块链原理、设计与应用](https://github.com/yjjnls/books/blob/master/block%20chain/%E5%8C%BA%E5%9D%97%E9%93%BE%E5%8E%9F%E7%90%86%E3%80%81%E8%AE%BE%E8%AE%A1%E4%B8%8E%E5%BA%94%E7%94%A8.pdf) -->
-   [**Blockchain: from Digital Currency to Credit Society**](https://github.com/yjjnls/books/blob/master/block%20chain/%E5%8C%BA%E5%9D%97%E9%93%BE%20%E4%BB%8E%E6%95%B0%E5%AD%97%E8%B4%A7%E5%B8%81%E5%88%B0%E4%BF%A1%E7%94%A8%E7%A4%BE%E4%BC%9A.pdf)
-   [**Attack of the 50 Foot Blockchain: Bitcoin, Blockchain, Ethereum & Smart Contracts**](https://davidgerard.co.uk/blockchain/table-of-contents/) by David Gerard, London, 2017 --
    _What is a bitcoin? ++
    The Bitcoin ideology ++
    The incredible promises of Bitcoin! ++
    Early Bitcoin: the rise to the first bubble ++
    How Bitcoin mining centralised ++
    Who is Satoshi Nakamoto? ++
    Spending bitcoins in 2017 ++
    Trading bitcoins in 2017: the second crypto bubble ++
    Altcoins ++
    Smart contracts, stupid humans ++
    Business bafflegab, but on the Blockchain ++
    Case study: Why you can’t put the music industry on a blockchain_

-   [**Mastering Bitcoin - Programming the Open Blockchain**](https://github.com/bitcoinbook/bitcoinbook/blob/develop/ch09.asciidoc) 2nd Edition,
    by Andreas M. Antonopoulos, 2017 - FREE (Online Source Version) --
    _What Is Bitcoin? ++
    How Bitcoin Works ++
    Bitcoin Core: The Reference Implementation ++
    Keys, Addresses ++
    Wallets ++
    Transactions ++
    Advanced Transactions and Scripting ++
    The Bitcoin Network ++
    The Blockchain ++
    Mining and Consensus ++
    Bitcoin Security ++
    Blockchain Applications_

-   [**Programming Blockchains in Ruby from Scratch Step-by-Step Starting w/ Crypto Hashes... ( Beta / Rough Draft )**](https://github.com/yukimotopress/programming-blockchains-step-by-step)
    by Gerald Bauer et al, 2018 - FREE (Online Version) --
    _(Crypto) Hash ++
    (Crypto) Block ++
    (Crypto) Block with Proof-of-Work ++
    Blockchain! Blockchain! Blockchain! ++
    Blockchain Broken? ++
    Timestamping ++
    Mining, Mining, Mining - What's Your Hash Rate? ++
    Bitcoin, Bitcoin, Bitcoin ++
    (Crypto) Block with Transactions (Tx)_


-   [**Programming Cryptocurrencies and Blockchains in Ruby ( Beta / Rough Draft )**](http://yukimotopress.github.io/blockchains)
    by Gerald Bauer et al, 2018 - FREE (Online Version) @ Yuki & Moto Press Bookshelf --
    _Digital $$$ Alchemy - What's a Blockchain? -
    How-To Turn Digital Bits Into $$$ or €€€? •
    Decentralize Payments. Decentralize Transactions. Decentralize Blockchains. •
    The Proof of the Pudding is ... The Bitcoin (BTC) Blockchain(s)
    \++
    Building Blockchains from Scratch -
    A Blockchain in Ruby in 20 Lines! A Blockchain is a Data Structure  •
    What about Proof-of-Work? What about Consensus?   •
    Find the Lucky Number - Nonce == Number Used Once
    \++
    Adding Transactions -
    The World's Worst Database - Bitcoin Blockchain Mining  •
    Tulips on the Blockchain! Adding Transactions
    \++
    Blockchain Lite -
    Basic Blocks  •
    Proof-of-Work Blocks  •
    Transactions
    \++
    Merkle Tree -
    Build Your Own Crypto Hash Trees; Grow Your Own Money on Trees  •
    What's a Merkle Tree?   •
    Transactions
    \++
    Central Bank -
    Run Your Own Federated Central Bank Nodes on the Blockchain Peer-to-Peer over HTTP  •
    Inside Mining - Printing Cryptos, Cryptos, Cryptos on the Blockchain
    \++
    Awesome Crypto
    \++
    Case Studies - Dutch Gulden  • Shilling  • CryptoKitties (and CryptoCopycats)_
---

## Contribute

Contributions welcome!

1.  Fork it (<https://github.com/nathass-the-legend/blockchain-tech-slack/fork>)
2.  Clone it (`git clone https://github.com/nathass-the-legend/blockchain-tech-slack`)
3.  Create your feature branch (`git checkout -b your_branch_name`)
4.  Commit your changes (`git commit -m 'Description of a commit'`)
5.  Push to the branch (`git push origin your_branch_name`)
6.  Create a new Pull Request

If you found this resource helpful, give it a 🌟 otherwise contribute to it and give it a ⭐️.