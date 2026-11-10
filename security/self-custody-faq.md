# Self-Custody FAQ

Before adding funds, check how your wallet stores keys, what you need to back up, and how to restore access. Recovery requirements differ between recovery phrase, hardware, email, and external-wallet accounts.

**Who controls my keys?**
Key handling and recovery differ by wallet type. A recovery phrase wallet keeps its keys on your device, and a hardware wallet keeps them on the hardware device. Email wallets use an email-linked embedded wallet; connecting an external wallet creates a separate DeGate operating wallet. See the recovery requirements in [Security Overview](security-overview.md) and [Wallet Addresses & Networks](wallet-address-and-networks.md).

**Can DeGate move, freeze, or seize my funds?**
DeGate is a wallet, not an exchange account. You authorize actions through your selected wallet, and key handling and recovery depend on that method. This does not make assets unrestricted: token issuers may limit transfers, and third-party pool or vault contracts govern deposited assets. See [Security Overview](security-overview.md).

**What do I need to back up?**
It depends on how you created the wallet:

* **Mnemonic (recovery phrase) wallet:** write down your recovery phrase and store it securely offline, never digitally. Keep a separate backup for each recovery phrase wallet; we cannot replace a lost recovery phrase for you.
* **Email wallet:** use the original email address and DeGate password in the DeGate app. Keep access to that email and preserve your password securely; recovery outside the DeGate app is not currently supported. If you permanently lose access to the linked email, you may be unable to recover the wallet. We do not recommend keeping large balances in an email wallet.
* **External-wallet / web-sync:** back up the original external wallet according to its recovery method, then reconnect it in the DeGate app. Assets at the derived DeGate addresses are separate from balances at your original external-wallet address. Restoring the external wallet alone in another application does not display those DeGate balances.
* **Hardware wallet:** your device (and the recovery sheet you set up with its manufacturer) is the backup.

**What if I lose my phone?**
Install the official DeGate app on a new phone. Import the original recovery phrase, reconnect your hardware wallet, sign in with the original email address and DeGate password, or reconnect the original external wallet, depending on the wallet type. Verify the restored addresses. Losing a phone does not erase assets recorded on-chain, but you still need the appropriate recovery method to access them.

**Can I use DeGate on multiple devices?**
Use the same recovery phrase, hardware-wallet connection, email address and DeGate password, or external-wallet connection in the DeGate app on the additional device. Check that the addresses match. The same address on the same network refers to the same on-chain assets; an application's display also depends on which tokens and positions it supports.

**How is this different from keeping assets on an exchange?**
With an exchange account, the exchange holds the assets and your balance is a claim on the operator; a hack, insolvency, or account restriction can affect your access. With a self-custody wallet, you hold the assets directly on-chain. You are responsible for your backup and the transactions you authorize. Recovery dependencies vary by wallet type; email and external-wallet / web-sync recovery currently requires DeGate, as explained above.

**"Non-custodial", "self-custodial", "unhosted": what's the difference?**
DeGate is described as a self-custody wallet. You may see the other terms in descriptions of wallets, but a label does not explain how a particular wallet stores keys or restores access. Check the recovery requirements for the method you use, as described above.

**Is self-custody harder to use?**
Supported flows include routing, bridging, and network fees in the app, so you do not need to arrange them separately before each action. You still need to keep the appropriate wallet backup and review what you sign. Hardware accounts need native gas tokens at their own address.
