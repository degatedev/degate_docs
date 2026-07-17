# Security Overview

DeGate is self-custodial: your private keys are generated and used on your device (or, for hardware wallets, on your hardware device), and DeGate's servers do not hold them.

## What DeGate can and cannot do

* DeGate **cannot** read your private keys or recovery phrase.
* DeGate **cannot** move funds from your addresses; only signatures produced by your key can do that.
* DeGate **can** construct transactions for you to sign, quote routes, and manage gas purchases, none of which requires custody of your assets.

## Key storage by wallet type

DeGate supports several ways of holding a wallet. Where the key material lives, and how independently you can recover it, differs by type:

* **Created or imported mnemonic wallets:** your recovery phrase is generated (or entered) locally and your keys stay on your device. This is the most independent option: your phrase alone restores your wallet in DeGate, or in any BIP39/BIP44-compatible wallet, with no dependency on DeGate at all.
* **Hardware wallets:** your private key never leaves the hardware device. DeGate reads your addresses over standard derivation paths, so your primary balance is recoverable with your device and any compatible wallet software, independent of DeGate.
* **Email wallets:** your signing key is an embedded wallet provided by our wallet infrastructure partner, tied to your email login, not generated or held by DeGate directly.
* **External-wallet and web-sync accounts** (Connect External Wallet / Sync from DeGate Web): your root key stays in your own external wallet; DeGate derives an operating wallet from a signature you provide with that wallet.

None of these methods gives DeGate access to your raw private keys. However, they are **not equally independent of DeGate today**: see "What this means for recovery" in [Wallet Addresses & Networks](wallet-address-and-networks.md) for the practical difference between wallet types.

## Independent review

Audit reports and their scope are documented on the [Audits](audits.md) page; vulnerability reports are welcome at [bounty@degate.com](mailto:bounty@degate.com) ([Bug Bounty](bug-bounty.md)).

## FAQ

**How do I make sure I'm using the real DeGate?**
Check every domain, app link, and community channel against [Official Links & Verified Contracts](../about-degate/official-links.md) before connecting a wallet or entering credentials. DeGate will never ask for your recovery phrase, private keys, or password; anyone who does is not DeGate.

**Can DeGate freeze my account?**
There is no custodial account to freeze. Assets sit at addresses controlled by your key; only you can authorize transactions from them.
