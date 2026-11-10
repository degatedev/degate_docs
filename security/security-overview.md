# Security Overview

Create or import a recovery phrase wallet, connect a hardware wallet, continue with email, or connect an external wallet. Each method has different key handling and recovery requirements. Choose a backup method that matches the wallet you use.

## What DeGate can and cannot do

* Review the quote and transaction request before authorizing an action from your selected wallet. Supported trade flows include routing within the app.
* For recovery phrase wallets, keys stay on your device. When you connect a hardware wallet, its keys stay on that hardware device. Email and external-wallet accounts work differently, as explained below.
* When you deposit into a DeFi pool or vault, the assets enter its contracts. That protocol governs the position; the app provides the interface for managing it.

## Key storage by wallet type

Key storage and recovery work as follows:

* **Created or imported mnemonic wallets:** your recovery phrase is generated (or entered) locally and your keys stay on your device. You can restore it in DeGate, or in wallet software that supports the same recovery phrase, networks, derivation paths, and account settings. Verify that the restored addresses match before transferring assets.
* **Hardware wallets:** your private key never leaves the hardware device. DeGate connects to addresses derived by the device. Another wallet application can access assets at the same addresses if it supports the device, networks, and derivation paths. Verify the address in that application; a pool position may require an interface that supports its protocol.
* **Email wallets:** email wallets use an embedded wallet supplied by a wallet infrastructure partner. Use the original email address and DeGate password in the DeGate app to restore access; recovery outside the DeGate app is not currently supported.
* **External-wallet and web-sync accounts** (Connect External Wallet / Sync from DeGate Web): your original key stays in your external wallet. Connecting creates a separate DeGate operating wallet through a signature-based process. Assets held at the derived DeGate addresses are not balances at your original external-wallet address. To restore those DeGate addresses, reconnect the same external wallet in the DeGate app; restoring the external wallet alone does not display those derived balances.

These methods have different recovery dependencies. Recovery phrase and hardware wallets can work with compatible software outside the app. Email and external-wallet / web-sync recovery currently requires the app. Read [What this means for recovery](wallet-address-and-networks.md#what-this-means-for-recovery) before choosing a method.

## Report a vulnerability

If you find a security issue, report it to [bounty@degate.com](mailto:bounty@degate.com). See [Bug Bounty](bug-bounty.md) for reporting instructions.

## FAQ

**How do I make sure I'm using the real DeGate?**
Check every domain, app link, and community channel against [Official Links](../about-degate/official-links.md) before connecting a wallet or entering credentials. We will never ask you to send us your recovery phrase, private keys, or password. If someone asks for them, stop and verify the contact through the official channels.

**Can DeGate freeze my account?**
DeGate is a wallet, not an exchange account. You authorize transactions through the wallet method you selected, and access and recovery depend on that method. Token issuers can restrict certain tokens, and third-party protocols set their own rules for positions. Using DeGate does not remove those restrictions.
