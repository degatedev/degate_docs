# Send

Users can initiate off-chain send requests at any time to retrieve assets from the DeGate smart contract. As depicted in the figure, the user signs a send request, which is verified by the node. Once the signature is verified, the node first locks the specified amount from the available balance of the asset, and then hands over to the Operator for the rollup operation. When the rollup transaction containing the send request is included in a block, the user will receive their withdrew assets. In case the node rejects the send request, users can retrieve their assets through[ forced withdrawal and the exodus mode](../concepts/exodus-mode.md).

<figure><img src="../.gitbook/assets/Screen Shot 2022-12-09 at 16.30.40.png" alt=""><figcaption><p>Withdrawal Process</p></figcaption></figure>

### Send Fees

When initiating a send request, users are required to pay gas fees, which currently can be paid with ETH, USDC, and USDT, but not the sent token.

### **Send Fund Options**

DeGate now offers two modes for sending funds: **Economy** and **Fast**.

• **Fast Mode**: This option has a slightly higher gas fee but guarantees arrival within 10 minutes.

• **Economy Mode**: Perfect for those users who have time and want to save on gas fees.

The great thing is, whenever someone initiates a Fast Send, Economy Send requests get processed immediately. It’s like taking a free ride.

### **Send Fund Options** <a href="#send-fund-options" id="send-fund-options"></a>

DeGate now offers two modes for sending funds: **Economy** and **Fast**.

• **Fast Mode**: This option has a slightly higher gas fee but guarantees arrival within 10 minutes.

• **Economy Mode**: Perfect for those users who have time and want to save on gas fees.

{% hint style="info" %}
The great thing is, whenever someone initiates a Fast Send, Economy Send requests get processed immediately. It’s like taking a free ride.
{% endhint %}

### Send Failure

When a rollup transaction containing zkBlock zero-knowledge proofs is packed into a block, the DeGate smart contract verifies the validity of the data, and the rollup will be completed after verification. If the rollup transaction includes a withdrawal request, an Inline transaction will also be initiated simultaneously. For an ERC20 token, such a send  means calling the transfer method of its contract address. However, in special situations, such as when the token’s smart contract has restricted the transfer function, the send transaction will fail. The assets will remain in the DeGate smart contract and users can retry the transfer by calling the DeGate smart contract method. Nevertheless, neither the recipient address nor the amount to be transferred can be modified.
