# Overview

## Introduction <a href="#preface" id="preface"></a>

This document provides a detailed overview of the DeGate protocol, covering its design philosophy, key concepts, and main functions. DeGate is a decentralized order book exchange that leverages ZK-Rollup technology to offer self-custody of funds, fast transaction speeds, and low gas fees. The following principles have been followed during the protocol's design:

## Trustless

Funds in the DeGate protocol are non-custodial, with users having complete control over their assets. No other roles can access a user’s funds. Specifically:

* Users can unilaterally withdraw their deposits if a transaction is not confirmed before a preset deadline
* Users can initiate a forced withdrawal to enter the exodus mode and withdraw their assets.
* All operations involving asset changes in a user’s DeGate account require the user's signature, ensuring at the protocol layer that asset changes can only happen with users’ authorization.
* Trustless order cancellation is possible, with users able to add confirmation on the blockchain for 100% trust-free cancellation.
* The DeGate protocol requires a minimum timelock of 45 days to complete an upgrade, during which the code logic cannot be changed.

## Permissionless Listing of Tokens

DeGate can be accessed and used with a blockchain wallet without KYC, and anyone can list and trade standard ERC20 tokens on top of the protocol. The ability to list any qualified token in a permissionless manner is a key feature of DeGate.

## Economic Security

For an open protocol, functional and economical security are equally, if not more, important than direct access, listing and trading. DeGate is the only order book DEX that allows for direct listing of tokens, and it adopts several measures to guarantee economic security, including:

• Free gas fee quota for deposits

 • Token parameter configuration 

• Specific quote tokens

 • Minimum order size requirements

 • Risk price and order 

• Trading risk warnings 

• A blacklist that automatically blocks the listing of non-standard ERC 20 tokens  

For more details on these measures, please refer to [economic-security.md](concepts/economic-security.md "mention")

DeGate is designed to be the antithesis of centralization in areas such as barriers of entry, trading openness, and fund security, all while providing a similar trading experience as centralized exchanges.

## Core Concepts

Zero Knowledge Rollup technology (ZK-Rollup) is at the heart of the DeGate protocol, consisting of on-chain and off-chain operations that enable off-chain processing of all account and asset changes followed by a rollup to the on-chain smart contract.

**On-chain components:** the smart contract deployed on the EVM network, responsible for storing assets, verifying zero-knowledge proofs and providing deposit and withdrawal methods.

**Off-chain component:** the off-chain DeGate node, primarily comprised of

* A front-end website: a site accessible from a browser
* The trading system: processing users’ orders and matching orders based on the order book; processing events of asset or account changes
* Operator: processing off-chain account and asset transactions regularly, generating zkBlock, calling circuits, and submitting proofs
* Circuit: describing events that require zero-knowledge proofs, used to generate zk proofs
* Merkle tree: storing the data of accounts, assets and orders in the DeGate protocol in a tree structure
* Chain Sync: observing and confirming all transactions that occur on the DeGate smart contract
* Postman: Calling the DeGate smart contract method on the EVM network and submitting zkBlock data to the smart contract

<figure><img src=".gitbook/assets/Screen Shot 2022-12-09 at 17.02.14.png" alt=""><figcaption><p>The DeGate protocol framework</p></figcaption></figure>

## EVM Compatibility

The DeGate protocol supports the EVM network. A DeGate testnet has been deployed on Goerli and the first DeGate mainnet will be deployed to the Ethereum mainnet.

## User Requests and Off-Chain Transactions

In the DeGate protocol, any user-initiated operation requests must be authorized with the user's private key signature. Operations involving changes to assets or accounts are processed as off-chain transactions.

## ZK-Rollup

The ZK-Rollup process of the DeGate protocol can be summarized into three steps:

1. Users initiate a request with their signature.
2. The DeGate node verifies and processes users’ requests, packages off-chain transactions into a block, and calls the circuit to compute a zero-knowledge proof.
3. The node sends the proof to the on-chain smart contract for verification to complete ZK-Rollup, providing data availability for assets.

Fore more, please refer to [introduction-to-zk-rollup.md](concepts/introduction-to-zk-rollup.md "mention")

<figure><img src=".gitbook/assets/image (6) (1).png" alt=""><figcaption><p>ZK-Rollup Process</p></figcaption></figure>

## Signature

A signature is required when an off-chain request is initiated in DeGate, and two signature methods are supported: ECDSA and EdDSA. Users can use their "wallet private key” to complete the ECDSA signature and unlock their account, which will generate an EdDSA private key, called the "asset private key". The asset private key is used to sign users' off-chain requests as EdDSA is more zk-friendly while reducing the computational cost of proofs. Different off-chain requests require different signature methods. For example, an EdDSA signature is used for placing an order, without the need for users’ in-wallet confirmation. However, an ECDSA signature from the wallet is still required for withdrawal and transfer requests. This balances both security and convenience.

For more, please refer to [secret-key-and-signatures.md](concepts/secret-key-and-signatures.md "mention")

## Account

The Merkle tree in the DeGate protocol records all the accounts’ permissions and asset information. New users are required to create a decentralized DeGate account in a permissionless way to write their wallet address and assets’ public key into the account node on the Merkle tree for binding. The on-chain assets that users deposit into the DeGate protocol will be credited to a corresponding account node on the Merkle tree for future operations such as trading and placing orders.

Fore more, please refer to [account-structure.md](concepts/account-structure.md "mention")

## Deposit

Before starting trading on DeGate, users must first deposit assets into their DeGate account. Following confirmation by the DeGate node of a user’s on-chain deposit transaction, the deposited amount will be credited to the user’s DeGate account balance, enabling an **immediate use for operations such as placing orders**. Simultaneously, the Operator will initiate an off-chain transaction for confirming the deposit, and ultimately roll it up to the on-chain smart contract to guarantee the consistency of on-chain and off-chain data.

Fore more, please refer to [deposit.md](main-features/deposit.md "mention")

## Withdrawal

Once a user initiates an off-chain request for withdrawal, the Operator will automatically and immediately process the request. It is important to note that **all withdrawals on DeGate are conducted without manual review**. Upon submission of the zkBlock containing the off-chain withdrawal transaction to the on-chain block, users will receive their withdrawn assets. In order to achieve 100% self-custody of assets, the DeGate protocol provides a forced withdrawal method, which allows users to retrieve their assets stored in the DeGate protocol **without any impediments**. Specifically, users can initiate a mandatory on-chain withdrawal request and force the Operator to process the request. If the Operator fails to process the request before a preset deadline, the entire DeGate protocol will cease operation, and enter the exodus mode.

Fore more, please refer to [withdrawal.md](main-features/withdrawal.md "mention")

## Exodus Mode

Once in the exodus mode, users can call the DeGate smart contract to retrieve their assets from the DeGate protocol. The DeGate smart contract will reject any new rollup of transactions, and all off-chain requests will not be processed. All DeGate accounts and assets will remain in the state of the most recent rollup prior to entering the exodus mode, and the DeGate smart contract will handle assets accordingly. To retrieve assets, users must parse all the Calldata data of the DeGate smart contract to create a Merkle tree, obtain the latest account and asset status, and retrieve assets from the DeGate smart contract with these data. Users may engage a third party to perform the parsing of the latest account and asset status.

Fore more, please refer to [exodus-mode.md](concepts/exodus-mode.md "mention")

## Protocol Fee

There are two types of DeGate protocol fees- **Gas Fees** and **Trading Fees**. The ZK-Rollup incurs costs, including Gas fees for rolling up the transactions on-chain and computational costs for generating ZK proofs. To ensure the economic security of the protocol, users are required to pay the gas fees for off-chain transactions. The protocol generates income from the trading fees that are charged when an order is filled. The order’s taker pays both the gas fees and transaction handling fees. All the fees collected are deposited into the DeGate HomeDAO vault.

Fore more, please refer to [protocol-fees.md](concepts/protocol-fees.md "mention")

## Trading System

The trading system is the core module of order book trading, which mainly comprises trading pairs, the order book, the matching logic and order records. All off-chain requests must be verified by the trading system first before being handed over to the Operator for processing. The matching logic used in the trading system is identical to that of a centralized exchange, which means orders are matched sequentially first by time priority and then price priority.

## Tokens and Trading Pairs

**Adding new assets and trading pairs does not require manual review**, and anyone can list standard ERC20 assets on the DeGate protocol. Specifically, the initiator first registers a token with the DeGate smart contract, and then adds trading pairs for the token in the DeGate node.

Currently, the protocol supports ETH, USDC, and USDT as quote token, which means each token can add up to 3 different trading pairs.

For some non-standard ERC20 assets, such as tokens with a transfer-to-burn mechanism or automatic supply updates, the DeGate node can support their listing and trading as well after additional processing on a case-by-case basis.

For more, please refer to [permissionless-listing.md](main-features/permissionless-listing.md "mention") and [trading-pairs.md](main-features/trading-pairs.md "mention")

## Security Auditing

The circuit logic and smart contract of the DeGate protocol are undergoing or have completed audits by at least two professional security teams. View [audit reports](https://github.com/degatedev/protocols/tree/degate\_mainnet/packages/loopring\_v3/security\_audit).

## Trusted Setup

When the DeGate protocol is deployed to the Ethereum mainnet, it is necessary to initialize both the circuit and the smart contract. This process, known as the Trusted Setup, entails the introduction of random entropies. The Trusted Setup for the DeGate protocol comprises two phases:

1. Referencing the configuration of [powers-of-tau](https://github.com/weijiekoh/perpetualpowersoftau/) as the initial value.
2. Based on the initial value, introducing a future Bitcoin block hash. 5 community members are then asked to input a random entropy respectively, followed by the introduction of another future Bitcoin block hash. Finally, the Proving Key and Verifying Key are calculated, which are subsequently put in the circuit and smart contract respectively.

For more, please refer to [Vitalik - How do trusted setups work?](https://vitalik.ca/general/2022/03/14/trustedsetup.html)

## DeGate Node

Currently, the off-chain components of the DeGate protocol operates on a single node, with a node operator in charge. The situations where the node may fail or do evil and corresponding countermeasures are listed as follows:

1. **The nodes fails to process off-chain requests.** To deal with this situation, users can initiate a mandatory withdrawal to retrieve their assets. If DeGate fails to process this on-chain request for mandatory withdrawal before a preset deadline, then anyone can force the DeGate protocol into the exodus mode. Users then can retrieve their assets directly from the DeGate smart contract.
2. **Order book Frontrun:** The market order slippage protection feature limits the possible scope of front-running losses that a user may suffer.
3. **Code security risk:** the code that interacts with wallets and assets is open-sourced and deployed separately for calls by front-end websites to ensure that the asset operation process is not forged by malicious code.
4. **End point security:** When APIs are called between the front end and the back end, a pre-agreed private key signature will be verified to ensure that the communicated data has not been tampered with.

## More Features

To make the DeGate protocol more trustless and reduce costs for users while facilitating professional users’ experience, the following functions have been added:

* The ability to cancel orders on-chain
* Decentralized grid trading strategy
* Aggregate transactions
* Deposit by transfer (standard deposits)
* Advanced accounts and trading private key
* SDK tooling and documentation
* Shutdown mode

## Main Functions

### 1. Compatibility

The DeGate website can be accessed through web and mobile browsers, including the web-based Metamask plug-in wallet, WalletConnect protocol and Ledger hardware wallet, as well as mainstream mobile wallets and mobile-based WalletConnect protocol.

### 2. Account Management

To manage a DeGate account is to manage its asset private key. Account management involves creating a new account, unlocking the account during login, resetting and viewing the asset private key.

### 3. Asset Management

In addition to deposits and withdrawals, internal transfers between DeGate accounts are also supported. Internal transfer is an off-chain request that will be rolled up on-chain. However, as long as a signature is initiated, the transfer to the target account can be completed immediately, and the gas fee is much lower than that of on-chain transfers.

### 4. Order Book Trading

DeGate offers two order types: limit and market orders. Limit order applies to the scenario where users set a desired execution price. It also has a Post-Only function, enabling users to place Maker orders only. Market orders are suitable for users who want to get a quick execution at the current best price in the order book. DeGate has a price slippage protection function to avoid magnified losses for orders when the depth is poor.

### 5. Permissionless Token Listing

Users can directly add new assets by entering the token's contract address and initiating a on-chain smart contract call.

### 6. Permissionless Addition of Trading Pairs

Users can select a Base Token and a Quote Token to form a trading pair and immediately add the trading pair to start trading.

### 7. Grid Strategy

The DeGate protocol allows users to trade with a grid strategy while maintaining self custody of their assets. Similar to placing an order in the order book, users can sign a grid strategy with their asset private key. After verification by the DeGate node, the initial grid orders will be added to the order book. After a grid order is matched and completed, the circuit verifies that the match aligns with the user's signed authorization. When a grid order is completely filled, the DeGate node will derive a new grid order according to the user's pre-authorized signature. This process keeps cycling for complete grid strategy trading. Grid strategy orders and ordinary orders share the same order book.

In addition, DeGate provides other functions, including grid order preview, graphical display of orders and recently closed orders, grid data statistics and historical details, etc., so that users understand their grid strategies.

### 8. Liquidity Mining

Liquidity mining is an element for DeGate’s cold start as it helps ensure sufficient liquidity for trading pairs. Users can participate in liquidity mining by creating a grid strategy that meets both the value and price conditions for a specific trading pair. Mining rewards are calculated and distributed every 15 seconds, providing an additional source of income for users that is independent of the market-making income from their grid strategy.

### 9. Historical Records

The DeGate protocol also provides detailed historical records of an account, including deposits, withdrawals, transfer history, order and transactions history, grid strategy records, account activities, and etc.
