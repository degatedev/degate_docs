# Self-Custody FAQ

Self-custody means your keys, and therefore your assets, are controlled by you rather than held in an account by a company. This page answers the questions people actually ask before trusting a self-custody wallet.

**Who controls my keys?**
Key handling and recovery differ by wallet type. A recovery phrase wallet keeps its keys on your device, and a hardware wallet keeps them on the hardware device. Email wallets use an email-linked embedded wallet; external-wallet connections create a separate operating wallet through DeGate. The recovery dependencies are described in [Security Overview](security-overview.md) and [Wallet Addresses & Networks](wallet-address-and-networks.md).

**Can DeGate move, freeze, or seize my funds?**
No. Your assets sit at blockchain addresses that only your key can sign for. There is no custodial account layer in between, so there is structurally nothing for DeGate to freeze or restrict.

**What do I need to back up?**
It depends on how you created the wallet:

* **Mnemonic (recovery phrase) wallet:** write down your recovery phrase and store it securely offline, never digitally. The phrase is the only way to recover this wallet type.
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
They describe the same property: you control your own keys and funds. "Non-custodial" is the term EU regulations use, "self-custodial" is common in product descriptions, and "unhosted wallet" is the FATF / US FinCEN term. All three apply to DeGate.

**Is self-custody harder to use?**
It historically involved more manual work (gas tokens, bridging, one wallet per chain). Removing that overhead while keeping the keys with you is the specific problem DeGate is built around.
