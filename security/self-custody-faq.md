# Self-Custody FAQ

Before adding funds, check how your wallet stores keys, what you need to back up, and how to restore access. Recovery requirements differ between recovery phrase, hardware, email, and external-wallet accounts.

**Who controls my keys?**
Key handling and recovery differ by wallet type. A recovery phrase wallet keeps its keys on your device, and a hardware wallet keeps them on the hardware device. Email wallets use an email-linked embedded wallet; connecting an external wallet creates a separate DeGate operating wallet. See the recovery requirements in [Security Overview](security-overview.md) and [Wallet Addresses & Networks](wallet-address-and-networks.md).

**Can DeGate move, freeze, or seize my funds?**
No. DeGate does not hold the private keys to self-custodial wallets. DeGate cannot sign a transfer from your address or freeze the wallet address. This does not make assets unrestricted: token issuers may limit transfers, and third-party pool or vault contracts govern deposited assets. See [Security Overview](security-overview.md).

**What do I need to back up?**
It depends on how you created the wallet:

* **Mnemonic (recovery phrase) wallet:** write down your recovery phrase and store it securely offline, never digitally. Keep a separate backup for each recovery phrase wallet; we cannot replace a lost recovery phrase for you.
* **Email sign-in:** keep access to the linked email address. When you sign in to the DeGate app, enter the six-digit verification code sent to that address. The app asks you to set up a password or biometric unlock on the new device to protect its local data. If you permanently lose access to the linked email, you may be unable to recover the wallet. We do not recommend keeping large balances in an email wallet.
* **External-wallet / web-sync:** back up the original external wallet according to its recovery method. On your new device, select the original account and reconnect it in the DeGate app to restore the derived DeGate addresses and view their balances. These addresses are separate from the external wallet’s own address.
* **Hardware wallet:** your device (and the recovery sheet you set up with its manufacturer) is the backup.

**What if I lose my phone?**
Install the official DeGate app on a new phone and follow the recovery method above for your wallet type. For email sign-in, use the original email address and the six-digit verification code sent to it, then set up the unlock method for the new device. Check that the restored addresses match the ones you used before. Your assets remain recorded on-chain when you lose your phone.

**Can I use DeGate on multiple devices?**
In the DeGate app on the additional device, use the recovery method above for the wallet you want to access. Check that the addresses match. The same address on the same network refers to the same on-chain assets; an application's display also depends on which tokens and positions it supports.

**How is this different from keeping assets on an exchange?**
With an exchange account, the exchange holds the assets and your balance is a claim on the operator; a hack, insolvency, or account restriction can affect your access. With a self-custody wallet, you hold the assets directly on-chain. You are responsible for your backup and the transactions you authorize. Recovery dependencies vary by wallet type; email and external-wallet / web-sync recovery currently requires DeGate, as explained above.

**"Non-custodial", "self-custodial", "unhosted": what's the difference?**
DeGate is described as a self-custody wallet. You may see the other terms in descriptions of wallets, but a label does not explain how a particular wallet stores keys or restores access. Check the recovery requirements for the method you use, as described above.

**Is self-custody harder to use?**
Supported flows include routing, bridging, and network fees in the app, so you do not need to arrange them separately before each action. You still need to keep the appropriate wallet backup and review what you sign. Hardware accounts need native gas tokens at their own address.
