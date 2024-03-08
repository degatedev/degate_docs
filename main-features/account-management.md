# Account Management

Managing an account means to manage its Asset Private Key, which is explained in greater detail in[secret-key-and-signatures.md](../concepts/secret-key-and-signatures.md "mention") .The Asset Private Key is initially generated during the account registration process and is tied to the Ethereum address from which it was derived.

### Unlocking and Locking An Account

The Asset Private Key is temporarily stored in the local SessionStorage of the browser used to accesses degate.com. Once the browser or all degate.com tabs are closed, all the data associated with the Asset Private Key is automatically deleted. Therefore, users must first unlock their account by completing the ECDSA signature with their Wallet Private Key whenever they reopen the browser to access the DeGate exchange, This signature shares the same content with the one used during account registration, and the same Asset Private Key is derived again.

{% code overflow="wrap" %}
```
Sign this message to access DeGate Exchange: 
0xdac304791B7f53593C701980aa52087Ed7EC6649 with key nonce: 1
```
{% endcode %}

Users can also choose to lock their account, which deletes all the information about the Asset Private Key from SessionStorage. However, they stay on the exchange’s website. Users can not access their DeGate account information, including information about assets, orders and historical records until the account is unlocked.

### Resetting the Asset Private Key

While generally safe, the Asset Private Key stored in SessionStorage is not completely immune to the risk of leakage. For example, if a user provides their signature to a phishing website to generate the Asset Private Key, they may unintentionally disclose it.  **Users are strongly advised to reset their Asset Private Key immediately if they suspect a leakage.** The reset process is similar to that of account registration. Users must complete two ECDSA signatures with their Wallet Private Key. They must first carry out the KeyNonce+1 signature to generate a new Asset Private Key, and then submit a request to update their Asset Private Key to the DeGate node.

When the DeGate protocol is in the midst of processing reset requests, some functions may be temporarily affected.&#x20;

1. All open orders will be cancelled.
2. Users will not be allowed to initiate any other operations, such as trading, withdrawals, transfers and so on.
3. Users can initiate another reset request, using the KeyNonce of the previous reset request incremented by 1.&#x20;

Once the zkBlock containing this reset request is submitted on-chain and the transaction is confirmed by the L1 network, the Asset Private Key is reset.

{% hint style="info" %}
Please withdraw all assets from DeGate immediately if you have disclosed your Wallet Private Key as attackers can control your DeGate account with a Wallet Private Key.
{% endhint %}

### Checking Asset Private Key

Checking the Asset Private Key is only applicable to users who need to use the DeGate SDK. Users can open their browser console to view their Asset Private Key. However, they can only access their DeGate account information, including assets, orders, and history after their account is unlocked.  The function of checking the Asset Private Key enables users to view it directly. Nonetheless, it is vital to take the necessary security precautions at all times.
