# Security Overview

How you set up your DeGate wallet determines where your keys are stored and what you’ll need to recover access.

## At a glance

* **Recovery phrase and hardware wallets keep keys on the device.** The app encrypts your recovery phrase on your phone. Your recovery phrase and private keys stay on your phone and are never sent to DeGate's servers. If you use a hardware wallet, the keys stay on the hardware device.
* **You authorize transfers.** DeGate cannot sign from your self-custodial wallet or freeze its address. Token issuers and DeFi protocols can set their own restrictions.
* **Check what you’re signing.** Review the network, amount, recipient or contract, and any other details shown. If you’re swapping tokens, check the quote as well.
* **Action Wallet keeps DeFi approvals separate.** When you use [Action Wallet](../security-and-self-custody/action-wallet/README.md), it handles token approvals and contract calls from its own address. You check the transfer on your hardware device, which reduces the risk of blind signing.
* **Know how you’ll recover your wallet.** If you use a recovery phrase or hardware wallet, you can recover access with compatible wallet software. Check the network, derivation path, and account settings, then verify that the address matches. See [recovery requirements by wallet type](wallet-address-and-networks.md#what-this-means-for-recovery).

## Where are my assets when I trade or provide liquidity?

* **In your wallet.** You can check the on-chain balance at your wallet address.
* **During an operation that uses DeGate’s solver.** The solver briefly holds the funds for that operation while it carries out the route you confirmed. For an example, see [how Action Wallet works](../security-and-self-custody/action-wallet/how-it-works.md).
* **In a stock LP or vault.** When you open a position in [Turbo Range](../features/turbo-range.md) or [Power Pair](../features/power-pair.md), your deposit goes into third-party pool contracts. A [Simple Earn](../features/simple-earn.md) deposit goes into the third-party contracts of the vault you select. Those contracts govern what happens to your deposit.

## Key storage by wallet type

Key storage and recovery work as follows:

* **Created or imported mnemonic wallets:** your recovery phrase is generated (or entered) locally and your keys stay on your device. You can restore it in DeGate, or in wallet software that supports the same recovery phrase, networks, derivation paths, and account settings. Verify that the restored addresses match before transferring assets. The app encrypts the recovery phrase before storing it in the device's Keychain on iOS, where it is restricted to that device, or in encrypted storage on Android. During setup, you choose an unlock method. If you set an app password, the app uses it to encrypt the recovery phrase. If you choose Face ID or fingerprint unlock, the app generates a random password to encrypt the phrase and protects that password with biometrics. The app displays a warning if it detects a screenshot during recovery phrase backup.
* **Hardware wallets:** your private key never leaves the hardware device. DeGate connects to addresses derived by the device. Another wallet application can access assets at the same addresses if it supports the device, networks, and derivation paths. Verify the address in that application; a pool position may require an interface that supports its protocol. When you connect a supported hardware wallet, the app checks its firmware against the minimum supported version.
* **Email sign-in:** email wallets use an embedded wallet supplied by a wallet infrastructure partner. On a new device, open the DeGate app and sign in with the same email address and the six-digit verification code sent to it. Then set up a password or biometric unlock to protect data stored on that device.
* **External wallet connected in the app:** your private key stays in the external wallet. DeGate uses a signature from that wallet to derive a separate set of addresses. The app asks your external wallet to sign the same message twice. It continues only if the signatures match, so it can check that the wallet signs consistently. The signatures are off-chain, cost no gas, and give no permission to spend tokens. To see your DeGate balances again, reconnect the same account using **Connect external wallet**. If you restored your external wallet from a backup, select the original account before reconnecting.
* **DeGate Web sync:** connect the original wallet account on DeGate Web, then sign to generate a QR code. Scan it within 60 seconds using **Sync from DeGate Web** in the app. Keep the code private. [See the web sync steps](../getting-started/create-a-wallet.md#sync-an-existing-degate-web-account).

These methods have different recovery dependencies. Recovery phrase and hardware wallets can work with compatible software outside the app. Email sign-in and external-wallet reconnection take place in the DeGate app. Web sync starts on DeGate Web and finishes in the app. Read [What this means for recovery](wallet-address-and-networks.md#what-this-means-for-recovery) before choosing a method.

## Audits and vulnerability reporting

In March 2026, Adevar Labs audited the Solana LP Handler that DeGate used for its earlier Solana pools. You can read the report and check what it covered on the [Audits](audits.md) page. The Ethereum pool contracts used by Turbo Range and Power Pair are outside that report’s scope.

Report security vulnerabilities privately to [bounty@degate.com](mailto:bounty@degate.com). See [Bug Bounty](bug-bounty.md) for reporting instructions.

## FAQ

**How do I make sure I'm using the real DeGate?**
Check every domain, app link, and community channel against [Official Links](../about-degate/official-links.md) before connecting a wallet or entering credentials. We will never ask you to send us your recovery phrase, private keys, or password. If someone asks for them, stop and verify the contact through the official channels.

* Sign the Action Wallet setup message only in the official DeGate app.
* Before generating a DeGate Web sync QR code, stop screen sharing or recording and make sure no one else can see or capture your screen. Keep the code to yourself.
* In a dApp, check whether you’re connecting your wallet, signing a message, or approving token spending. Connecting shares your public address. A token approval gives the contract permission to spend the token up to the amount you approve.

**Can DeGate freeze my account?**
No. DeGate does not hold the private keys to self-custodial wallets. DeGate cannot sign a transfer from your address or freeze the wallet address. Token issuers can restrict certain tokens, and third-party protocols set their own rules for positions. Using DeGate does not remove those restrictions.
