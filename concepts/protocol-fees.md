# Protocol Fees

When using the DeGate protocol, users may need to pay different fees based on different scenarios.

* **Trading fees:** When a limit order or market order is filled, the Taker of the order pays the Trading fees that vary by trading pairs. The trading fees are deducted from the tokens a user receives after trading. Take DG/USDC as an example. If a user buys 1,000 DG at the market price, assuming a trading fee rate of 0.1%, then the Taker pays 1,000\*0.1%=1 DG as trading fees, deducted from the 1,000 DG the user is supposed to receive. Thus, the user ultimately receives 999 DGs. All trading fees will accrue to the DeGate HomeDAO vault.
* **Gas Fees:** All operations completed through zero-knowledge proofs incur gas fees when submitted to the Ethereum mainnet. Based on our testing results, the DeGate protocol has defined the amount of gas each operation consumes. It also calculates the gas fees that a user is required to pay before an operation is initiated based on real-time gas price of the network and ETH price. Currently, gas fees can be paid with ETH, USDC and USDT.

### Trading Fee Rate

The node operator sets thetrading fee rate for each trading pair, which is currently fixed as:

<table data-card-size="large" data-view="cards" data-full-width="false"><thead><tr><th>Trading Pair Type</th><th>Taker Rate</th><th>Maker Rate</th><th>Example</th></tr></thead><tbody><tr><td>Stable pairs</td><td>0.01%</td><td><strong>Free</strong></td><td>USDT/USDC, DAI/USDC,<br>DAI/USDT, wstETH/ETH</td></tr><tr><td>Others</td><td>0.05%</td><td><strong>Free</strong></td><td>ETH/UDSC, DG/USDT</td></tr></tbody></table>

To prevent the node operator from arbitrarily modifying the fee rate, a parameter specifying the maximum fee rate is added to the DeGate smart contract. The actual fee rate can not exceed this parameter; otherwise the order will fail the smart contract verification when submitted on-chain. In addition, a 7-day grace period after the modification of the maximum fee rate gives users enough time to respond.

### Operation Requests and Fees

| Operation                                  | Gas Fee | Trading Fee | Description                                                                                                                                       |
| ------------------------------------------ | ------- | ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| Trade                                      | Yes     | Yes         | Fully incurred by taker, maker free                                                                                                               |
| Grid Strategy Trade                        | -       | -           | All orders under a grid strategy are maker orders                                                                                                 |
| Add                                        | -       | -           | Subsidised by the node operator of the protocol                                                                                                   |
| Send                                       | Yes     | -           |                                                                                                                                                   |
| Transfer                                   | Yes     | -           | Additional fee will be charged by the party that transfers asset to an unregistered DeGate account                                                |
| Account Registration                       | -       | -           | Subsidised by the node operator of the protocol                                                                                                   |
| Reset Asset Private Key                    | Yes     | -           |                                                                                                                                                   |
| On-Chain Order Cancellation                | Yes     | -           |                                                                                                                                                   |
| On-Chain Grid Cancellation                 | Yes     | -           | All orders in a grid strategy can only be canceled collectively. The total gas fees is the number of orders \* single on-chain order cancellation |
| Create Trading Pair (Add to glossary list) | Yes     | -           | Zero-knowledge proof is not required for creating new trading pairs. The gas fee is charged to hinder attack on the protocol                      |
| Claim Mining Rewards                       | Yes     | -           | Mining rewards are received through the transfer function                                                                                         |

### Calculating Gas fees

Gas usage is configured into every off-chain transaction based on an approximate value obtained after multiple simulations. When a user initiates a request, depending on the real-time gas price of the network and the ETH Price, the amount of ETH, USDC, and USDT to be paid is calculated respectively.

```
ETH = GasUsage * GasPrice
USDC = GasUsage * GasPrice / ETHPrice
USDT = GasUsage * GasPrice / ETHPrice
```

| Operation                               | Gas Usage Amount |
| --------------------------------------- | ---------------- |
| Trade                                   | 800              |
| Add                                     | -                |
| Send                                    | 58393            |
| Transfer                                | 2225             |
| Transfer to New Account                 | 22422            |
| Register Account                        | -                |
| Reset Asset Private Key                 | 20197            |
| On-Chain Order Cancellation             | 2393             |
| On-Chain Grid Cancellation :digit\_one: | N \* 2393        |
| Create Trading Pair                     | 100              |

Note :digit\_one:: N represents the number of orders under the same grid strategy. In other words, each grid order must be canceled independently on-chain.

###

### Paid Deposits

Each deposit incurs certain fees as it requires zero-knowledge proof. Currently, the node operator subsidizes deposit fees, so users do not need to pay for deposits. To prevent attackers from manipulating the subsidy policy to attack the DeGate protocol, an upper limit is added to the subsidies. If a user’s deposits incur more fees than the ceiling, they should pay a specified amount of ETH to complete the deposit.

* Standard deposit: Users can pay fees from their wallet or DeGate account, and the payment amount is calculated based on the real-time Gas price of the network.
* Advanced deposit: Fees are paid from users’ wallet. The payment amount parameters are configured in the DeGate smart contract, and the node operator has modification permissions. &#x20;

## **Forced Withdrawal**

Users interact directly with the DeGate smart contract from their wallet for a forced withdrawal. When calling the `ForceWithdraw` method, they must pay a specified amount of ETH, up to 0.25 ETH, configured in the DeGate smart contract. The node operator has modification permissions.

## DeGate HomeDAO Treasury

All gas fees and transaction trading fees will be transferred to the DeGate HomeDAO account. The node operator can claim funds from the account.\
