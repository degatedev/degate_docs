# Action Wallet

The Action Wallet is an operating wallet derived from **your hardware wallet.** A one-time signature from your device creates it, so it is tied to your hardware wallet: the same device always recreates the same Action Wallet, and no new seed phrase is needed. It sits between your hardware wallet and DeFi smart contracts, so your hardware wallet never has to blind-sign smart contract calls or token approvals.

The Action Wallet keeps a small balance for network fees and handles the tokens or position NFT needed for the operation.

{% hint style="info" %}
_Your hardware wallet never signs DeFi contract calls or token approvals._
{% endhint %}

<figure><img src="../../.gitbook/assets/action-wallet-setup-details-preview (1).png" alt=""><figcaption></figcaption></figure>

### Why use an Action Wallet?&#x20;

Hardware wallets are the safest place to keep crypto, but using them directly with DeFi carries two risks:

* **Unlimited token approvals -** DeFi apps often ask permission to spend all of a token. If that app is ever hacked, those funds can be drained, even from a hardware wallet.
* **Blind signing -** Your hardware wallet can't display complex transactions, so you end up approving something you can't read.

### How the Action Wallet fixes this <a href="#actionwallet-gitbook-howtheactionwalletfixesthis" id="actionwallet-gitbook-howtheactionwalletfixesthis"></a>

* **Only simple transfers** - Your hardware wallet only signs simple transfers to your own Action Wallet. These are clear on screen and easy to check.
* **No approvals from your hardware wallet -** All DeFi approvals and contract calls happen in the Action Wallet, never in your hardware wallet.
* **Minimal exposure -** The Action Wallet holds only what is needed for the current operation, and your assets return to your hardware wallet when completed.<br>

**Result:**

* Your main funds never touch DeFi risk.
* Every signature on your device is easy to read: a simple transfer or message you can check before confirming.

### Key Benefits

* **No blind signing -**&#x59;our hardware wallet never approves or calls a smart contract.
* **You keep proof of ownership -** Every proof of ownership returns to your hardware wallet, including your LP position NFTs. Claimed rewards and leftover funds go directly to your hardware wallet too.
* **Fewer confirmations -** Approvals, contract calls and gas are handled by the Action Wallet via DeGate solver. You only confirm the transfer out of your hardware wallet.
* **Nothing to back up -** Because it is derived from your hardware wallet, your device can always recreate the same Action Wallet.<br>

