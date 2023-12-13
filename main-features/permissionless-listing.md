# Permissionless Listing

To trade new assets in the DeGate protocol, users must register the token first and then add trading pairs for it, all in a permissionless manner. The registration information is recorded in the DeGate smart contract and cannot be modified.

### Listing Process

Anyone can call the `registerToken` method of the DeGate smart contract to register a new asset. The DeGate node regularly observes on-chain asset registration transactions. After a transaction is confirmed, the new asset will be automatically added to the token list that the node maintains. Alternatively, if a user calls the smart contract’s deposit method, they can directly deposit unregistered assets, and the deposited tokens will be automatically registered.

Users can also list tokens on the degate.com website, via the following methods:

1. Searching for Assets in the Account Assets page;
2. Searching for Assets in the Trading Pair tab of the Trading /Grid Strategy page;
3. Entering the contract address of the new token on the Assets tab of the Deposit page.

### Listing Fees

DeGate does not charge any manual review fees that are common in centralized exchanges. Only Gas fees are required for a listing transaction.

### Token List

The DeGate node maintains a list of registered tokens for DeGate.

### Limitations

1. The DeGate protocol supports tokens up to: about 4.2 billion.
2. The DeGate node also supports the listing and trading of non-standard ERC20 assets, such as those with a transfer-to-burn mechanism and tokens whose supply automatically updates. However, evaluation is done one a case-by-case basis.
3. Newly registered assets are non-default tokens that can become default tokens if they meet the [requirements](../concepts/economic-security.md#default-token-list) during regular updates of the node operator.
