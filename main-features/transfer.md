# Transfer

To quickly move assets between DeGate accounts, users can initiate a transfer by specifying the recipient address and the amount to be transferred. After users’ signature, the node verifies the transfer request. The recipient address receives the assets immediately after verification, whereas simultaneously the corresponding amount is deducted from the sender’s address. At the same time, the Operator will continue to process the transfer request, and roll it up on-chain after a series of operations from block inclusion, block production, proof generation, to updating the asset balance on Merkle tree.

<figure><img src="../.gitbook/assets/Screen Shot 2022-12-09 at 17.01.01.png" alt=""><figcaption><p>Transfer Process</p></figcaption></figure>

### Transfer Fees

When initiating a transfer request, users are required to pay gas fees, which can currently be paid with ETH, USDC, and USDT, but not the token being transferred.

### Transfer to New Account

Assets can be transferred to any DeGate account or any recipient address without a DeGate account. However, transferring to a new account incurs higher gas fees. Users will see a warning prompt when the recipient address they have entered does not have a DeGate account.

### Transfer Constraints

1. . Users cannot transfer assets to their own address.
2. The effective number of digits of the transferred amount cannot exceed 7 to ensure the accuracy of circuit calculation.

> For example, if an account has 123456.78 DG, the user can only input 123456.7 instead of 123456.78, with a remnant of 0.08.
>
> However, for tokens with a large order of magnitude, such as SHIB, a transfer amount of 12,345,670,000 is supported.

### How Transfer Differs From Withdrawal

1. A transfer moves assets between DeGate accounts, but the assets remain in the DeGate smart contract. In contrast, a withdrawal retrieves assets from the DeGate smart contract to a specified Ethereum mainnet address.
2. Transfers are completed immediately, whereas withdrawals require waiting for the rollup to complete.
3. The gas fee for transfers is much lower than that for withdrawals.
