# Frequently -Asked -Questions (FAQ)

### Are the assets stored in DeGate safe?

All operations concerning funds require authorizations from a user’s account and no one else can embezzle their assets. Additionally, the DeGate smart contract does not have an admin key, thus making it impossible for the node operator to steal users’ funds.

### Why do I need to add funds?

As DeGate is a decentralized exchange that uses ZK-Rollup technology. Performing a fund addition and send is equivalent to utilizing an L2 bridge.

### What types of costs there are when trading on DeGate?

1. First, users need to pay gas costs from a L1 wallet when adding funds into DeGate.&#x20;
2. Users are also required to pre-authorize gas fees when placing an order. However, they only need to pay the gas fees and transactions handling fees as the Taker of a filled order.
3. Gas fees are also required for operations such as assets withdrawals and transfers, resetting Asset Private Key, permissionless token listing, and adding trading pairs.

### Why does DeGate charge Gas fees?

As an L2 transaction protocol, DeGate needs to regularly submit off-chain transactions data to the smart contract. Initiating such transactions consumes gas on L1, which is why DeGate charges gas fees for users’ operations. This is similar to initiating transactions on other L2s and paying gas fees accordingly.

### How has DeGate managed to make transactions fast and cheap?

Because DeGate enables orders and transactions to be completed off-chain, and only sends packaged information on-chain for zero-knowledge proof, which is different from traditional DEXs where every order and transaction is initiated and completed on-chain. This saves a lot of sas fees, and does not depend on the confirmation time of the L1 blockchain network.

### What assets can I trade on DeGate?

DeGate supports all ERC20 assets issued on the network where it is deployed, such as assets on Ethereum.

### In addition to ETH, USDC, USDT, will other quote tokens be added?

In the future, we will adjust the quote tokens based on market needs.

### What are the use cases of DG tokens?

Users can access all the functions on DeGate without holding DG. DG is a governance token that allows its holders to participate in proposal voting.
