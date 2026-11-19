# Security Overview

Create or import a recovery phrase wallet, connect a hardware wallet, continue with email, or connect an external wallet. If you used DeGate Web, you can sync your existing account to the app. Each method has different key handling and recovery requirements. Choose a backup method that matches the wallet you use.

## What DeGate can and cannot do

* Review the quote and transaction request before authorizing an action from your selected wallet. Supported trade flows include routing within the app.
* For recovery phrase wallets, keys stay on your device. When you connect a hardware wallet, its keys stay on that hardware device. Email and external-wallet accounts work differently, as explained below.
* When you deposit into a DeFi pool or vault, the assets enter its contracts. That protocol governs the position; the app provides the interface for managing it.

## Key storage by wallet type

Key storage and recovery work as follows:

* **Created or imported mnemonic wallets:** your recovery phrase is generated (or entered) locally and your keys stay on your device. You can restore it in DeGate, or in wallet software that supports the same recovery phrase, networks, derivation paths, and account settings. Verify that the restored addresses match before transferring assets. The app encrypts the recovery phrase before storing it in the device's Keychain on iOS, where it is restricted to that device, or in encrypted storage on Android. During setup, you choose an unlock method. If you set an app password, the app uses it to encrypt the recovery phrase. If you choose Face ID or fingerprint unlock, the app generates a random password to encrypt the phrase and protects that password with biometrics. The app displays a warning if it detects a screenshot during recovery phrase backup.
* **Hardware wallets:** your private key never leaves the hardware device. DeGate connects to addresses derived by the device. Another wallet application can access assets at the same addresses if it supports the device, networks, and derivation paths. Verify the address in that application; a pool position may require an interface that supports its protocol. When you connect a supported hardware wallet, the app checks its firmware against the minimum supported version.
* **Email sign-in:** email wallets use an embedded wallet supplied by a wallet infrastructure partner. On a new device, open the DeGate app and sign in with the same email address and the six-digit verification code sent to it. Then set up a password or biometric unlock to protect data stored on that device.
* **External wallet connected in the app:** your original key stays in your external wallet. Connecting creates a separate set of DeGate addresses through a signature-based process. To restore those addresses and view their balances, reconnect the same account through **Connect external wallet** in the DeGate app. If you restored the external wallet from a backup, select the original account before reconnecting.
* **DeGate Web sync:** connect the original wallet account on DeGate Web, then sign to generate a QR code. Scan it within 60 seconds using **Sync from DeGate Web** in the app. Keep the code private. [See the web sync steps](../getting-started/create-a-wallet.md#sync-an-existing-degate-web-account).

These methods have different recovery dependencies. Recovery phrase and hardware wallets can work with compatible software outside the app. Email sign-in and external-wallet reconnection take place in the DeGate app. Web sync starts on DeGate Web and finishes in the app. Read [What this means for recovery](wallet-address-and-networks.md#what-this-means-for-recovery) before choosing a method.

## Independent review

Audit reports and their scope are documented on the [Audits](audits.md) page; vulnerability reports are welcome at [bounty@degate.com](mailto:bounty@degate.com) ([Bug Bounty](bug-bounty.md)).

## Report a vulnerability

If you find a security issue, report it to [bounty@degate.com](mailto:bounty@degate.com). See [Bug Bounty](bug-bounty.md) for reporting instructions.

## FAQ

**How do I make sure I'm using the real DeGate?**
Check every domain, app link, and community channel against [Official Links](../about-degate/official-links.md) before connecting a wallet or entering credentials. We will never ask you to send us your recovery phrase, private keys, or password. If someone asks for them, stop and verify the contact through the official channels.

**Can DeGate freeze my account?**
No. DeGate does not hold the private keys to self-custodial wallets. DeGate cannot sign a transfer from your address or freeze the wallet address. Token issuers can restrict certain tokens, and third-party protocols set their own rules for positions. Using DeGate does not remove those restrictions.
