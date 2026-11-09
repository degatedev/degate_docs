# Security Overview

DeGate is a self-custody wallet. Key handling and recovery depend on how you add a wallet: a recovery phrase wallet, a hardware wallet, an email wallet, or an external-wallet connection. Review the method for your wallet before relying on a backup.

## What DeGate can and cannot do

* DeGate **cannot** read your private keys or recovery phrase.
* DeGate **cannot** move funds from your addresses; only signatures produced by your key can do that.
* DeGate **can** construct transactions for you to sign, quote routes, and manage gas purchases, none of which requires custody of your assets.

## Key storage by wallet type

DeGate supports several ways of holding a wallet. Where the key material lives, and how independently you can recover it, differs by type:

* **Created or imported mnemonic wallets:** your recovery phrase is generated (or entered) locally and your keys stay on your device. You can restore it in DeGate, or in wallet software that supports the same recovery phrase, networks, derivation paths, and account settings. Verify that the restored addresses match before transferring assets.
* **Hardware wallets:** your private key never leaves the hardware device. DeGate reads your addresses over standard derivation paths, so another wallet application can access assets at those same hardware addresses if it supports the device, networks, and derivation paths. Verify the address in that application; a pool position may require an interface that supports its protocol.
* **Email wallets:** email wallets use an embedded wallet supplied by a wallet infrastructure partner. Use the original email address and DeGate password in the DeGate app to restore access; recovery outside the DeGate app is not currently supported.
* **External-wallet and web-sync accounts** (Connect External Wallet / Sync from DeGate Web): your original key stays in your external wallet. DeGate derives a separate operating wallet through a signature-based process. Assets held at the derived DeGate addresses are not balances at your original external-wallet address. To restore those DeGate addresses, reconnect the same external wallet in the DeGate app; restoring the external wallet alone does not display those derived balances.

None of these methods gives DeGate access to your raw private keys. However, they are **not equally independent of DeGate today**: see "What this means for recovery" in [Wallet Addresses & Networks](wallet-address-and-networks.md) for the practical difference between wallet types.

## Report a vulnerability

If you find a security issue, report it to [bounty@degate.com](mailto:bounty@degate.com). See [Bug Bounty](bug-bounty.md) for reporting instructions.

## FAQ

**How do I make sure I'm using the real DeGate?**
Check every domain, app link, and community channel against [Official Links](../about-degate/official-links.md) before connecting a wallet or entering credentials. DeGate will never ask for your recovery phrase, private keys, or password; anyone who does is not DeGate.

**Can DeGate freeze my account?**
There is no custodial account to freeze. Assets sit at addresses controlled by your key; only you can authorize transactions from them.
