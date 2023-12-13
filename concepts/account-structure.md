# Account Structure

Users access the DeGate protocol through their Ethereum wallet. Before using DeGate for the first time, users must register a DeGate account and link their account permissions to their wallet address.

<figure><img src="../.gitbook/assets/Screen Shot 2022-11-28 at 12.03.23.png" alt=""><figcaption><p>Account Nodes in the Entire Merkle Tree</p></figcaption></figure>

Each Account Node on the Entire Merkle Tree represents a DeGate account, which stores users’ wallet address (owner), Asset Public Key (publicKeyX and publicKeyY), Transaction Public Key (appKeyX and appKeyY), Account Nonce (nonce), Transaction Private Key permissions (disableAppKeySpotTrade/Withdraw/TransferToOther), and root data (balanceRoot and storageRoot). There are a total of 4^16 Account nodes, which means that the DeGate protocol supports up to 4.2 billion accounts. Each DeGate account is assigned an AccountID in order, starting from 0 and incrementing by integers. 0 and 1 are reserved, so users’ accounts start with 2.

Assigning AccountIDs to wallet addresses allows for using numbers to represent very long addresses, reducing the cost of zero-knowledge proofs. **Users don’t need to know their AccountID** as they access DeGate using an associated Ethereum wallet. Regardless of withdrawal or transfer, users can enter their wallet address to complete the operation.\\

## Account Nonce and KeyNonce

The Account node in the Merkle tree also contains a Nonce called "Account Nonce". So far, we have talked about two Nonce concepts: Account Nonce and KeyNonce. The comparison between the two is as follows:

<table><thead><tr><th width="148">Differences</th><th width="392">Account Nonce</th><th width="316">KeyNonce</th></tr></thead><tbody><tr><td>Storage Location</td><td>Account node in merkle tree</td><td>Off-chain storage in DeGate node</td></tr><tr><td>Rules</td><td>Begin from 0, increment by 1 each time AccountUpdate or AppKeyUpdate is executed</td><td>Begins from 1, and increase by 1 with each reset</td></tr><tr><td>Verifer</td><td>The circuit</td><td>DeGate node,</td></tr><tr><td>Function</td><td>Prevent replaying transaction updates to the account's EdDSA keys and permissions. This is similar to how the nonce of ethereum transactions works.</td><td>Used to generate different EdDSA keys</td></tr></tbody></table>

{% hint style="info" %}
**What happens if the DeGate node loses the latest KeyNonce?**

Every time a user unlocks their account, they need to obtain the latest KeyNonce from the node in order to generate a correct Asset Private Key. Without a KeyNonce, the user needs to sign starting from 1 and compare the new KeyNonce with the Key stored in the Account Node of the Merkle tree until there is a match. This helps them obtain the latest KeyNonce. So users’ assets will not become lost or inaccessible in the event of the DeGate node losing the latest KeyNonce.
{% endhint %}

## Account Assets

<figure><img src="../.gitbook/assets/Screen Shot 2022-11-28 at 12.14.02.png" alt=""><figcaption><p>Asset Node under an Account Node</p></figcaption></figure>

To start trading on DeGate, users must have assets in their DeGate account. Users can deposit tokens from their wallets to their DeGate accounts, or transfer assets from other DeGate accounts. All the assets deposited into the DeGate protocol are stored in the DeGate smart contract. Each deposit must be confirmed by zero-knowledge proofs, and simultaneously synchronized to the Asset Node under the corresponding Account Node in the Merkle tree.

In other words, users can not use their in-wallet assets directly in DeGate, and instead must deposit their assets first. On the other hand, if they need their assets back in their wallets, they must withdraw their assets. Despite the entry barriers arising from deposits and withdrawal, the resulting instantaneous and free order placements and cancellations are very friendly to long-term and professional traders.

In addition, some operations may require gas fees that must be paid with assets in a DeGate account.

At the protocol layer, DeGate stipulates that account assets can only be manipulated by signed authorizations using either the Wallet Private Key or the Asset Private Key. Users are expected to take security precautions themselves.
