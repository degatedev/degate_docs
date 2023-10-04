# Placing Orders

An order refers to a user's request to trade a certain amount of a certain token at a particular price. An order book is a collection of orders sorted by price and placing time. Whenever two orders are matched at the same price, a "transaction" is generated. Each order can be matched with multiple orders, and each order can have multiple transactions. During each transaction, the counterparties’ roles are determined  based on their respective order-placing time. The party who placed the order first is known as the Maker, while the other party is referred to as the Taker.&#x20;

The implementation of ZK-Rollup technology enables DeGate to provide users with an order-placing experience as smooth as that of a centralized exchange. Users place an order by signing it with their Asset Private Key, creating an off-chain request. Therefore, **placing an order is free, with immediate execution**. After receiving the signature associated with an order, the DeGate node will match or place the order based on the order book. Information related to each matched transaction is then rolled up on-chain through zero-knowledge proof.

### Limit Order

Limit orders enable users to place an order by specifying both the price and quantity. Post-Only orders are also supported. When Post-Only is enabled, users can only place limit orders as Makers. If an order is filled with the user acting as a Taker, the entire order will fail. To prevent users from entering wrong prices, the DeGate website offers a risk management function named "price deviation warning". Whenever the input price deviates from the best price in the order book by 5% or more, a warning will be displayed to the user. However, the user can still choose to proceed with placing orders.

### Market Order

Market orders require users to specify only the quantity. Once a market order is placed, the transaction will be completed based on the best available price in the order book. To minimize the likelihood of Frontrun attacks by the DeGate node, DeGate provides an additional risk management function called "slippage protection”. This function limits the difference between the transaction price and the optimal price in the order book to 10% and any portion of the order exceeding the cap will be cancelled. Therefore, users’ maximum loss is limited to 10% in the event of a Frontrun attack. Users who are indifferent to the price but want the fastest order completion can choose to place a market order.

### Minimum Order Size

The amount and value of a limit order must meet the [minimum order value](../concepts/economic-security.md#minimum-order-size) requirements. However, as the gas fee for a market order is born by the user placing the order, market orders are subject no minimum order value requirements. As long as an account has enough balance to cover the pre-auth gas fee, and the specified amount meets the decimal requirements, market orders can be placed.

### Pre-auth Gas Fee

In DeGate, filled orders are entirely free for the Maker, while the Taker is required to pay both the gas fees and transaction handling fees. Depending on the order type, users are always Takers for market orders. When it comes to limit orders, users can be both Takers and Makers depending on their specified price and the overall order book situation.

As it is impossible to determine whether a user is a Maker or a Taker at the time an order is placed, users are required to **pre-authorize the maximum amount of Gas fees they are willing to pay,** regardless of the order type. Such an authorization process is completed automatically without the need for users’ manual configuration. The DeGate node calculates the required pre-auth gas fees in real-time, based on the gas price of the Ethereum mainnet, ETH’s price, and the gas consumption of each transaction. The **Pre-auth Gas Fee may not necessarily equal the actual costs**, which can vary depending on whether the order is immediately filled with the user as the Taker. Takers must pay the gas fees, which will not exceed the pre-authorized amount. Makers, on the other hand, are not required to pay any gas fees.

Currently, **the Pre-auth Gas Fee is configured to cover up to 6 transactions**. This means that there can be no more than 6 transactions for the same order with the user as the Taker. However, if an order remains partially filled after 6 transactions, the completed transactions will remain unchanged, while the unfilled portion of the order will be automatically cancelled. Let’s consider the following scenarios:

> 1. A user placed a market order which was completely filled after 4 transactions.
> 2. A user placed a market order which remained partially filled after 6 transactions. The unfilled portion of the order was automatically cancelled.
> 3. A user placed a limit order which was not filled with the user as a Taker. Instead, the order was added to the order book and awaited matching with the user as a Maker.
> 4. A user placed a limit order which was partially filled after 3 transactions with the user as a Taker. The unfilled portion of the order was added to the order book and awaited matching with the user as a Maker.
> 5. A user placed a limit order which was partially filled after 6 transactions with the user as a Taker. Since the user was expected to remain a Taker in the next transaction, the unfilled portion of the order was automatically cancelled.
> 6. A user placed a limit order which was partially filled after 6 transactions with the user as a Taker. Since no transaction ensued with the user as a Taker, the unfilled portion of the order was added to the order book with the user as a Maker.

Gas fees must be paid with the quote token of a trading pair. To lower the threshold for users, the DeGate protocol allows users to pay gas fees using the quote token they receive after a sale order is completed.

> Take DG/USDC as an example, when a user only has DG but no USDC, they can sell DG and pay the actual Gas fees using the USDC they receive.

Finally, users can click the "Advanced" icon located below the order placing section to check the latest Pre-auth Gas Fee parameters.

### Transaction Handling Fees

Transaction handling fees represent the main source of income for the DeGate protocol. A certain proportion will be charged from the assets a Taker is expected to receive after a transaction as the transaction handling fees. [Click here to check the fee rate](../concepts/protocol-fees.md#transaction-handling-fee-rate).

### Order Validity Period

The DeGate protocol requires that orders be placed with a pre-specified validity period. The circuit checks the order’s validity status when verifying a transaction. If an order has expired, the transaction will fail verification. As users’ signatures are always valid before the order is completely filled and can be used for transactions, the order validity period helps reduce the risk of an attacker decoding the order’s signature.

Both limit orders and market orders have a default expiration date. Users can modify the expiration date of a limit order in the “Advanced” section. The default validity period for a market order is very short, as the order is expected to be filled immediately, so users don’t need to modify this parameter.

### Order Cancellations

Users can cancel orders at any time. **Order cancellations are free and executed immediately**. Once the DeGate node verifies a user’s order cancellation request, the trading system will withdraw the corresponding order from the order book and discard the order’s signature. All this is based on the assumption that the user trusts that the DeGate node will faithfully perform their cancellation operations and will not use the order signature to perform matching again. To achieve permissionless cancellation, the DeGate protocol provides the functions of "cancellation of orders on-chain” and "cancellation of grid strategy on-chain”.

Users can initiate a cancellation request on-chain for canceled orders. The request processing result by the DeGate node will then be rolled up on-chain, and the order will be marked as closed and are no longer available for matching. Users can determine whether the node has truthfully processed the cancellation request on-chain according to calldata. When canceling an order on-chain, users must pay gas fees. If an order has expired and the signature can no longer be used for matching, there is no need to cancel the order on-chain.

### Risk Warning for Non-default Tokens

Distinguishing between default and non-default tokens helps users quickly identify authentic tokens. [Click here](../concepts/economic-security.md#actively-and-inactively-traded-tokens) to learn more about the differences between the two. When users enter either the trading page or the grid strategy page, they will see a "risk warning” if the trading token is non-default. Please make sure the token contract address is correct before placing orders to avoid buying counterfeits.&#x20;

{% hint style="info" %}
How to determine whether a token is authentic?

The most reliable way is to check its contract address.&#x20;

1. Users can check the token’s information on popular websites to verify the consistency of its contract address, icon, symbol, name and other information. &#x20;

&#x20;      [https://coinmarketcap.com/](https://coinmarketcap.com/)

&#x20;      [https://www.coingecko.com/](https://www.coingecko.com/)

2. Additionally, users can check the official platforms of the corresponding project, such as its website and Discord, to confirm the contract address.
{% endhint %}

### Balance Reconciliation and Correction

According to the system design, the DeGate trading system first deducts the transaction handling fees and gas fees when matching orders. The Operator then packages the transaction request for circuit verification when the Merkle tree’s asset node is also updated. However, as the decimal precision of the trading system is higher than that of the circuit, the asset balance following the circuit update may be lower than the number shown in the trading system. Nevertheless, users should refer to the Merkle tree for their true balance, which will be regularly rolled up to the DeGate smart contract. To ensure accuracy, users' DeGate balance is updated according to the actual value after the rollup transaction is confirmed. This process is called "Balance Reconciliation and Correction”, which result in minimal corrections that do not affect normal use.
