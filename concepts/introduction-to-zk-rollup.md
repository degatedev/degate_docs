# Introduction to ZK-Rollup

The DeGate protocol is a trading protocol designed to achieve high throughput while minimizing gas costs. The protocol uses zkSNARKs technology to generate zero-knowledge proofs after processing requests off-chain, and submits the proofs on-chain for verification and data availability.

<figure><img src="../.gitbook/assets/Screen Shot 2022-12-09 at 16.19.15.png" alt=""><figcaption><p>ZK-Rollup Overview</p></figcaption></figure>

## Operator

A crucial component of the protocol, the Operator is mainly responsible for：

1. Producing zkBlocks: The Operator processes each batch of ZK-Rollup events based on predetermined rules and generates zkBlocks.
2. Generating zero-knowledge proofs: The Operator calls the circuit to generate proofs for zkBlocks.
3. Submitting zkBlock data: The Operator calls Postman to submit zkBlocks data to the on-chain smart contract to confirm state changes.

## Off-Chain Transactions&#x20;

Off-chain transactions that require zero-knowledge proof and verification in the DeGate protocol include the following:

<table><thead><tr><th width="214">Event</th><th>Description</th></tr></thead><tbody><tr><td>No-op</td><td>Null transactions used to fill zkBlocks that are not fully filled with off-chain transactions</td></tr><tr><td>AccountUpdate</td><td>This allows users to create or update their account asset private key</td></tr><tr><td>AppKeyUpdate</td><td>This allows users to create, update, and configure the trading private key's permissions</td></tr><tr><td>SpotTrade <span data-gb-custom-inline data-tag="emoji" data-code="0031">1️</span></td><td>The off-chain matching of two orders</td></tr><tr><td>BatchSpotTrade</td><td>The aggregation of SpotTrade is performed by the operator to increase transaction throughput and lower the on-chain cost for users</td></tr><tr><td>OrderCancel <span data-gb-custom-inline data-tag="emoji" data-code="0032">2️</span></td><td>This allows users to perform an on-chain order cancellation operation which guarantees that the order can never be used by the operator for order matching</td></tr><tr><td>Add</td><td>This confirms the user's L1 fund addition which will credit the user's balance in L2</td></tr><tr><td>Send</td><td>Move the user's asset from L2 to L1</td></tr><tr><td>Transfer</td><td>Assets are moved between two L2 accounts</td></tr></tbody></table>

:digit\_one:: Orders are not directly submitted on-chain. This only happens when an order is filled.

:digit\_two:: Cancelling an order or a grid strategy involves only informing the trading system of the cancellation with a user’s signature without any proofs submitted on-chain. Therefore, it is not a ZK-Rollup event. To prevent the DeGate node from “doing evil” with the signature a user provides when placing the order, DeGate provides a OrderCancel method, which allows the user to request the submission of a proof that the order has been cancelled.

## zkBlock

zkBlocks can be regarded conceptually as DeGate’s “L2 block”. Depending on the number of events, one or more sequential zkBlocks are generated for each batch of events that the Operator processes. These zkBlocks are then passed to the circuit for zk-proof computation.

## Circuit

This is not a physical circuit, but a zkSNARK circuit. The Circuit is responsible for describing events that require zero-knowledge proofs, such as order completions and deposits, and thus an important part of zero-knowledge proofs. The Circuit receives inputs, and the input signal generates an output through the path of the electric gate to produce zk-proofs for the corresponding zkBlocks.

## Merkle Tree

To improve computing and storage efficiencies, DeGate has implemented data selection and compression. As Merkle tree balances complexity, computing time, and user-friendliness, the protocol has created two Merkle trees: Entire Merkle Tree and Asset Merkle Tree.

* The Entire Merkle Tree ensures the data security of DeGate protocol as it records all the information regarding accounts, assets, and transactions on DeGate.
* The Asset Merkle Tree guarantees users’ self-custody of their assets. Even when the DeGate node operator cannot provide any services, users can still withdraw their assets safely. The Asset Merkle Tree records all DeGate accounts and assets information.

## Submitting zkBlocks

Once the zk proof of a zkBlock is generated, the Operator calls the submitBlocks method of the DeGate smart contract through Postman to submit zkBlock-related data on-chain for confirmation of status change (multiple zkBlocks can be submitted simultaneously in strict accordance with the sequence of block generation ). These data mainly include:

* The root hash of the Entire Merkle Tree
* The root hash of the Asset Merkle Tree
* Zero-knowledge proofs
* Change of account permissions and asset balance
* Additional data for deposit, withdrawal, and account update transactions

As the Node operator has to pay ETH as Gas to submit zkBlocks on-chain, users will be charged gas fees.

## Smart Contract

The on-chain DeGate smart contract is responsible for storing user funds, verifying the zero-knowledge proofs submitted by the off-chain node and storing the latest Merkle tree roots. It consists of multiple contracts, the main contracts of which are:

1. **Exchange:** interactions where the Operator submits zkBlock or users’ deposits or mandatory withdrawals.&#x20;
2. **Deposit:** stewarding the assets deposited by users, and providing the providing the functions of deposit, withdrawal and transfer.
3. **Loopring:** the Exchange contract parameters configuration.
4. **BlockVerify:** registering verifying key and verifying zero-knowledge proofs.

## Postman

The Operator calls the DeGate smart contract through Postman, and submits zkBlocks' data on chain in strict accordance with the sequence of zkBlocks generation.

## Chain Sync

Observing all on-chain transactions of the DeGate smart contract, such as fund additions, mandatory withdrawals, and Rollup transactions, and notifying the node after a transaction is confirmed.

The above is a brief description of the ZK-Rollup part of the DeGate protocol. For more information, please refer to the protocol design document.
