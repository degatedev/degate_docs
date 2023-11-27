# Exodus Mode

The Operator of the DeGate off-chain node is responsible for producing zkBlocks and submitting proofs. If the Operator stops working, all off-chain transactions that have not been submitted on-chain will become invalid. To ensure the trustlessness of funds, the DeGate protocol provides an **Exodus Mode** that allows users to withdraw their assets even when the node stops working.&#x20;

Once the Exodus Mode is activated, the DeGate smart contract will reject any new zkBlock data, and its state will stay in the last block before the Exodus Mode. This means that all off-chain transactions in DeGate will be suspended, including transactions, withdrawals and transfers. The Exodus Mode is irreversible, and the only action users are allowed to take under Exodus Mode is to withdraw their assets.

## Activating the Exodus Mode

The steps to activate the Exodus Mode are as follows:&#x20;

1. **Initiating a forced withdrawal**: Users can call the forceWithdraw method of the DeGate contract to initiate a forced withdrawal.
2. **Forced withdrawal unprocessed**: This refers to any forced withdrawal request not processed by the DeGate node within a pre-specified timeframe, which is configured in the DeGate smart contract.&#x20;
3. **Activating the Exodus Mode**: As long as a forced withdrawal request is not processed within the specified timeframe, any user can call the notifyForcedRequestTooOld method of the DeGate smart contract to throw the DeGate protocol into the Exodus Mode.&#x20;

If the DeGate node is honest, it will not want to enter the Exodus Mode. The node will therefore conscientiously identify and process all forced withdrawal requests within the specified timeframe. Forced withdrawals will be treated as ordinary withdrawals, with the following differences:

* Users must specify the token for a forced withdrawal. They don’t need to specify the withdrawal amount, as they will withdraw as much as possible. The DeGate node will cancel all open orders of the token, and then process the withdrawal request.
* When a user initiates a forced withdrawal, they must pay the fees from their wallet. However, for an ordinary withdrawal, gas fees are paid from users’ DeGate accounts.
* After the forced withdrawal request is successfully processed, the user should call the withdrawFromApprovedWithdrawal method of the DeGate smart contract again to retrieve their assets.&#x20;



## Forced Withdrawal Process Overview

<figure><img src="../.gitbook/assets/Screen Shot 2022-12-09 at 16.25.13.png" alt=""><figcaption><p>A Force Withdrawal Request Processed In-Time</p></figcaption></figure>

### Retrieving Assets In the Exodus Mode

After the Exodus Mode is activated, users can retrieve their assets. There are three possible scenarios:

1.  **DeGate account balance:** Users can call the `withdrawFromMerkleTree`&#x20;

    method on-chain to withdraw the entire balance of a token, which is the account balance status stored in the last block before the Exodus Mode.
2. **Unconfirmed advanced addition:** As the deposited assets are in the smart contract and have not been credited into the DeGate account balance, users can withdraw the assets using the withdrawFromDepositRequest method.&#x20;
3.  **Unconfirmed standard addition:** As the deposited assets are in the smart contract and have not been credited into the DeGate account balance, users must contact the node operator to apply for a refund.



{% hint style="info" %}
**How can ordinary users call the DeGate smart contract?**

Initiating a forced withdrawal and retrieving asset balance both require users to provide corresponding data, which can be obtained by parsing the Calldata of all submitBlock transactions in the DeGate smart contract. Users can refer to the design document for parsing methods. We expect to see third parties providing real-time DeGate calldata parsing services in the future, and users can engage these services to obtain information. Third parties may even provide products that allow users to initiate forced withdrawals, activate the Exodus Mode, and retrieve balances with one click. Users don't need to worry about the security of third-party services, because assets will only be retrieved to the account of the initiator. However, they should be careful not to lose their Wallet Private Key or Asset Private Key.
{% endhint %}
