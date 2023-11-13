---
description: >-
  A fairly launched, Dao-centric, Zero Knowledge based trading protocol built on
  Ethereum. DeGate is Limit Orders, Decentralized
---

# A ZK Rollup DEX Protocol

DeGate is a Decentralized Exchange (DEX) protocol built on Zero Knowledge (ZK) technology. As a ZK Rollup, DeGate fills a key gap in the market by providing spot order book trading and grid trading within the Ethereum ecosystem, offering an experience similar to centralized exchanges (CEX). DeGate is a [DAO-centric](broken-reference/) protocol, with a DAO fully controlling its treasury. DeGate is a protocol of the community, by the community, and for the community.

The protocol enables several functions, including Spot Trading and Grid Trading, with more features to be added to enable a coherent trading experience.

**Spot Trading**

Gas fees are a major concern on the Ethereum mainnet. Conventional AMM DEXes incur high gas fees on Ethereum and provide only market orders, where traders have to accept the current market price for a trading pair. DeGate is a new type of protocol based on a ZK rollup that allows for spot trading through limit orders, similar in experience to a centralized exchange. The ZK technology powers a “match node” matching orders between traders, periodically recording the transactions on a mainnet. This ensures a faster, cheaper trading experience that is still secured by Ethereum. Crucially, the protocol is designed such that fees are low for taker orders, and free for maker orders.

Essentially, DeGate is limit orders, decentralized.

To further reduce gas fees for users, the protocol has pioneered gas-saving features including:

_Gas Saving Deposit_: Depositing into a DEX protocol often incurs a high one-time fee. DeGate has created a gas-saving deposit option. This option is based on a “simple transfer” rather than a “contract call”. This method can reduce the one-time gas deposit fee by up to 75%.

_Ultra-Efficient Gas Saving (UEGS) technology_: This innovation was built specifically for DeGate protocol this ensures significant gas savings while maintaining a decentralized protocol.

While DeGate derives its security from Ethereum and is designed to be trustless and permissionless, it provides functionality similar in form and function to centralized exchanges without the inherent security risks of such exchanges.

**Grid Trading**

The grid trading function is another innovation of the DeGate protocol. This replicates the grid trading on a CEX, which enables users to implement a trading strategy based on the ups and downs in a trading pair.

Combined with the advantages of DeGate's free maker orders, this feature can help users earn long-term and stable returns safely in the highly volatile cryptocurrency market without the assets being custodized by a centralized entity. Data availability for all grid strategies on DeGate is secured by Ethereum through zero-knowledge technology.

## Design Principles

The design of DeGate protocol is based on three principles:

**Fully decentralized**

In the long term, the goal of DeGate protocol is to implement a standalone open-source client functionality. This means that no one is running the service in a centralized fashion and the system is unstoppable. By downloading the open-source code on GitHub or a similar website, anyone can use the protocol. At long-term equilibrium, the protocol is designed to be based on an open network composed of thousands of nodes.

**Trustless**

DeGate was designed such that the user always has the highest authority, and no malicious or centralized authority has access to the user's assets. In this sense, malicious actors "can't do evil" through DeGate's non-custodial storing of assets. Additionally, smart contracts can be upgraded only after a substantial timelock of 45 days. See details [here](broken-reference/).

**Permissionless**

The whole system is an [open protocol](broken-reference/). Any token can be listed on DeGate by anyone. And anyone who has a blockchain wallet can directly use DeGate.

## Roadmap

DeGate is working towards a fully decentralized limit order trading protocol built on a DAO-centric model. All liquidity comes from the community, and all income belongs to the DAO. It is a grand and challenging project that will be implemented in multiple milestones, but even in the first version, the protocol still guarantees a [trustless](broken-reference/) system where all assets are owned by the user.

### Phase 1 - Testnet Launch

**Expected time to launch: 1st Quarter, 2022**

DeGate trading deployed on Ethereum testnet. All major features will be launched at this stage and delivered to all users for use on the testnet. This will demonstrate the product features to the community and allow for rapid feedback and iteration.

Features that will be included in this phase include:

1. Spot trading module based on zk-rollup
2. High-performance spot matching engine
3. Front end UI for easy access to DEX protocol
4. Ultra-Efficient Gas Saving aggregation technology
5. Grid trading features
6. Permissionless listing
7. Exodus withdraw mode

In this phase, concrete actions to be completed include:

1. Completion of security audits involving multiple third-party institutions for circuits and smart contracts
2. Fixing technical issues that need to be resolved before the official mainnet launch
3. Performance and throughput testing, tuning
4. Improvement and optimization of the gas fee billing system

### Phase 2 - Mainnet Beta

**Expected launch: 1st Quarter, 2023**

DeGate spot component deployed on Ethereum mainnet with a whitelist. Real Ethereum ERC20 assets will be supported for trading in this version. Early community contributors, partners, market makers, and developers will be given priority on the whitelist to test and use DeGate.

Features in this phase include :

1. Full trading API support with documentation
2. Asset Key support to enable more authorization for professional users

In this phase, concrete actions to be implemented include:

1. Preparation to open source the code base
2. Preparation for partial governance by DAO of token economy and parameter settings
3. Construction of developer community and market maker ecosystem

### Phase 3 - Mainnet Launch (DeGate 1.0)

**Expected launch: 3rd/4th Quarter 2023**

In this phase, the restrictions on whitelist registration will be removed. The protocol will be open to anyone to use.&#x20;

To attract an initial user base, liquidity mining incentives will be provided. In addition, the distributions of tokens awarded in our unique social media round, as well as other distributions will also commence at this time.

In this phase, DeGate will continue to develop the DAO-centric model of governance, giving increased voting power and incentives to token holders.

At this stage, it is important to note that the protocol will be served by a single match node, with full decentralization addressed in Phase 4.

### Phase 4 - Hyper Scalability (DeGate 2.0)

**Expected launch: 2024 and beyond**

[EIP-4844 ](https://eips.ethereum.org/EIPS/eip-4844)introduces a new kind of transaction type to Ethereum. EIP 4844 will enable "blobs" of data to persist in the beacon node for a short period of time. To be compatible with Ethereum's scaling roadmap and EIP-4844, DeGate will launch a new version to take advantage of the blobs data scheme that EIP-4844 brings about. This will significantly boost DeGate's throughput as well as decrease gas fees for DeGate users. At that time, user experience of DeGate will be greatly improved without compromising security.

## Other Resources

<table data-view="cards"><thead><tr><th></th><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td></td><td><strong>Product Feature Docs</strong></td><td></td><td><a href="https://docs.degate.com/v/product_en/">https://docs.degate.com/v/product_en/</a></td></tr><tr><td></td><td><strong>DeGate SDK Docs</strong></td><td></td><td><a href="https://api-docs.degate.com/spot/#introduction">https://api-docs.degate.com/spot/#introduction</a></td></tr></tbody></table>
