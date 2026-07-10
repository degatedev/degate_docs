# Self-Custody FAQ

Self-custody means your keys, and therefore your assets, are controlled by you rather than held in an account by a company. This page answers the questions people actually ask before trusting a self-custody wallet.

**Who controls my keys?**
You do. Keys are generated locally and remain under your sole control. The DeGate protocol and degate.com do not and cannot access users' wallet private keys. The derivation mechanism is documented in [Wallet Addresses & Networks](wallet-address-and-networks.md).

**Can DeGate move, freeze, or seize my funds?**
No. Your assets sit at blockchain addresses that only your key can sign for. There is no custodial account layer in between, so there is structurally nothing for DeGate to freeze or restrict.

**What happens to my assets if DeGate shuts down?**
Assets live on the blockchains themselves, not on DeGate's servers, at addresses only your keys control. What you can do next depends on wallet type. With a mnemonic wallet, your recovery phrase restores all funds through any BIP39/BIP44-compatible wallet (MetaMask, Rabby, Trust Wallet, and others), and LP positions on underlying protocols such as Raydium or Uniswap can be managed directly through those protocols. Email wallets are built on an embedded key that can be exported through a standalone export tool independent of the DeGate app; if the simplest possible independence matters to you, hold meaningful balances in a mnemonic wallet, whose recovery phrase works everywhere without extra steps. How each wallet type's keys derive is documented in [Wallet Addresses & Networks](wallet-address-and-networks.md).

**What do I need to back up?**
It depends on how you created the wallet:

* **Mnemonic (recovery phrase) wallet:** write down your recovery phrase and store it securely offline, never digitally. The phrase is the only way to recover this wallet type.
* **Email wallet:** your keys are tied to your email and password. You can re-access your wallet on any device, in the app or the web app, by signing in with the same email.

**What if I lose my phone?**
Download DeGate on a new device and restore with your recovery phrase or email login. Your funds are on-chain, not on the device; the device only holds keys, and keys can be restored from your recovery method.

**Can I use DeGate on multiple devices?**
Yes. Import your wallet on any additional device using your mnemonic phrase or email login. Balances are the same everywhere because all data is on-chain.

**How is this different from keeping assets on an exchange?**
With an exchange account, the exchange holds the assets and your balance is a claim on the operator; a hack, insolvency, or account restriction can affect your access. With a self-custody wallet, you hold the assets directly on-chain. The trade-off is responsibility: self-custody removes operator counterparty risk, and in exchange you carry the responsibility for your own backup.

**"Non-custodial", "self-custodial", "unhosted": what's the difference?**
They describe the same property: you control your own keys and funds. "Non-custodial" is the term EU regulations use, "self-custodial" is common in product descriptions, and "unhosted wallet" is the FATF / US FinCEN term. All three apply to DeGate.

**Is self-custody harder to use?**
It historically involved more manual work (gas tokens, bridging, one wallet per chain). Removing that overhead while keeping the keys with you is the specific problem DeGate is built around.
