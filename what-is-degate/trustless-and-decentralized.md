# Trustless and Decentralized

To ensure that DeGate is a trustless, decentralized and permissionless limit order exchange, the trust mechanism of the entire DeGate protocol is guaranteed by two factors: ZK-Rollup data availability and "Exodus Mode".

### ZK-Rollup Data Availability

ZK-Rollup technology is one of the most promising solutions being developed to scale the Ethereum Blockchain. Crucially, it increases scalability by processing a large number of transactions and "rolling" them into a transaction on a base layer, greatly reducing cost.

The DeGate ZK-Rollup is secured by two key factors: **proof** **generation** and **proof** **verification**.

In DeGate protocol, the proof generation is undertaken by the relayer through an off-chain **circuit program.** The relayer collects a large number of transactions to generate a SNARK proof. The SNARK proof is a hash-like piece of content that represents the changeset to the state of DeGate protocol. For verification, to achieve and prove trustlessness in the blockchain system, we use immutable open-source **smart contracts** to verify the proof and update the state atomically. The exchange data is recorded in Merkel trees through the smart contract, and the Ethereum mainnet guarantees its security.

### Exodus Mode

In the ZK-Rollup technical architecture, the protocol must host users' assets in smart contracts. No one can manipulate a user's assets, which are proved by cryptography.

However, there is still an availability risk in that an operator running a DEX based on DeGate protocol could go offline and be unable or unwilling to provide services. If the operator is shut down, the logic for regular deposits and withdrawals will not be available. In this worst case scenario, the DeGate "exodus mode" enables users to retrieve their assets.

To illustrate, suppose any force withdrawal has not been processed for more than 15 days. Anyone can trigger a transaction to enable the **exodus mode** of DeGate protocol. This process is irreversible, which means that this deployment instance of the DeGate protocol is no longer useable. The only thing that can be done is for users to withdraw assets by directly providing data proof as a parameter to the smart contract. Users can restore their data from historical call data stored on Ethereum.

### Further work

In addition to the guarantees of the above three mechanisms, DeGate is also working on decentralizing operators to reduce the limited risk of denial of service, dropped orders, and changing transaction orders from one single operator node. DeGate will build towards an ultimate trustless protocol by establishing a consensus network with a punishment mechanism similar to public chains.

In the redeployment of the DeGate protocol in November 2023, upgradeability with a time lock was introduced, to provide greater flexibility in subsequent iterations, but maintaining trustlessness. The initial delay time for the time lock is set to 45 days. As the protocol becomes increasingly stable, DeGate plans to gradually extend the upgrade delay, and may eventually eliminate his upgrade capability altogether.
