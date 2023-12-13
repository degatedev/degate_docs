# Withdrawal

Users can initiate off-chain withdrawal requests at any time to retrieve assets from the DeGate smart contract. As depicted in the figure, the user signs a withdrawal request, which is verified by the node. Once the signature is verified, the node first locks the specified amount from the available balance of the asset, and then hands over to the Operator for the rollup operation. When the rollup transaction containing the withdrawal request is included in a block, the user will receive their withdrawn assets. In case the node rejects the withdrawal request, users can retrieve their assets through[ forced withdrawal and the exodus mode](../concepts/exodus-mode.md).

<figure><img src="../.gitbook/assets/Screen Shot 2022-12-09 at 16.30.40.png" alt=""><figcaption><p>Withdrawal Process</p></figcaption></figure>

### Withdrawal Fees

When initiating a withdrawal request, users are required to pay gas fees, which currently can be paid with ETH, USDC, and USDT, but not the withdrawn token.

### Withdrawal Failure

When a rollup transaction containing zkBlock zero-knowledge proofs is packed into a block, the DeGate smart contract verifies the validity of the data, and the rollup will be completed after verification. If the rollup transaction includes a withdrawal request, an Inline transaction will also be initiated simultaneously. For an ERC20 token, such a withdrawal means calling the transfer method of its contract address. However, in special situations, such as when the token’s smart contract has restricted the transfer function, the withdrawal transaction will fail. The assets will remain in the DeGate smart contract and users can retry the transfer by calling the DeGate smart contract method. Nevertheless, neither the recipient address nor the amount to be transferred can be modified.
