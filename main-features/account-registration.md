# Account Registration

We have learned from [account structure](../concepts/account-structure.md) that each DeGate account is a node on a Merkle tree, represented by a unique AccountID. The node stores the latest information about account permissions and assets. Account permissions associate a user’s wallet address with their Asset Public Key. Once permissions are set, users can use their wallet account to operate the corresponding DeGate account. Assets information records the balance of assets in the DeGate account, and is updated every time a transaction, fund addition, send, transfer, and other operations incurring gas fees is performed.

### Account Registration Procedure

Writing account permissions and assets information to the Merkle tree is not subject to any mandatory sequence requirements. Users can add assets first and then set permissions, or do it in reverse order. However, the node operator subsidizes the gas fees incurred during setting account permissions for _write_ operations. **To ensure economic security, the node must obtain assets first before setting permissions.** Users can submit an off-chain request for setting permissions first, and wait until their DeGate account has received assets, such as from a fund addition or a transfer. The DeGate node will only process the permissions setting request after that.&#x20;

The account registration procedure for a user involves:

1. Registering an account and submitting an off-chain request;
2. Completing a fund addition, or receiving a transfer;
3. Setting permissions at the same time as the fund addition (or transfer) is completed.&#x20;

### Account Registration Criteria

Account registration on DeGate requires no KYC, and DeGate supports External Owned Account(EOA) and contract account (CA). The only requirement is that the EVM account must have at least one transfer-in or transfer-out record. Therefore, a new address cannot register a DeGate account. The DeGate block synchronization service will regularly scan and updates the list of addresses that are eligible to create accounts.
