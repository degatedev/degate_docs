# Self-Custody FAQ

Self-custody means your keys, and therefore your assets, are controlled by you rather than held in an account by a company. This page answers the questions people actually ask before trusting a self-custody wallet.

**Who controls my keys?**
You do. DeGate's servers do not hold your private keys and cannot access them. Where the key material lives differs by wallet type (on your device for mnemonic wallets, on your hardware device, in your own external wallet, or in an email-linked embedded wallet); the breakdown is in [Security Overview](security-overview.md) and [Wallet Addresses & Networks](wallet-address-and-networks.md).

**Can DeGate move, freeze, or seize my funds?**
No. Your assets sit at blockchain addresses that only your key can sign for. There is no custodial account layer in between, so there is structurally nothing for DeGate to freeze or restrict.

**What do I need to back up?**
It depends on how you created the wallet:

* **Mnemonic (recovery phrase) wallet:** write down your recovery phrase and store it securely offline, never digitally. The phrase is the only way to recover this wallet type.
* **Email wallet:** your keys are tied to your email and password. You can re-access your wallet on any device, in the app or the web app, by signing in with the same email.
* **Sign in with Wallet / web-sync:** your external wallet is the key; back it up according to that wallet's own recovery method, and signing in with it again restores your DeGate account.
* **Hardware wallet:** your device (and the recovery sheet you set up with its manufacturer) is the backup.

**What if I lose my phone?**
Download DeGate on a new device and restore with your recovery method: your mnemonic phrase, your email login, or signing in again with your external wallet. Your funds are on-chain, not on the device.

**Can I use DeGate on multiple devices?**
Yes. Restore your wallet on any additional device using the same recovery method (mnemonic phrase, email login, or external-wallet sign-in). Balances are the same everywhere because all data is on-chain.

**How is this different from keeping assets on an exchange?**
With an exchange account, the exchange holds the assets and your balance is a claim on the operator; a hack, insolvency, or account restriction can affect your access. With a self-custody wallet, you hold the assets directly on-chain. The trade-off is responsibility: self-custody removes operator counterparty risk, and in exchange you carry the responsibility for your own backup.

**"Non-custodial", "self-custodial", "unhosted": what's the difference?**
They describe the same property: you control your own keys and funds. "Non-custodial" is the term EU regulations use, "self-custodial" is common in product descriptions, and "unhosted wallet" is the FATF / US FinCEN term. All three apply to DeGate.

**Is self-custody harder to use?**
It historically involved more manual work (gas tokens, bridging, one wallet per chain). Removing that overhead while keeping the keys with you is the specific problem DeGate is built around.
