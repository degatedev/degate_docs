---
description: Creating your DeGate account
---

# Create a Wallet

The mobile app is the recommended path. Install it, then pick the way in that fits you.

[![Download on the App Store](https://hub.degate.com/common/wallet-setup-img-en/Download_AppStore.png)](https://apps.apple.com/app/apple-store/id6742168343?pt=127643354\&ct=docs\&mt=8) [![Get it on Google Play](https://hub.degate.com/common/wallet-setup-img-en/Download_GooglePlay.png)](https://play.google.com/store/apps/details?id=com.app.degate\&referrer=utm_source%3Ddocs%26utm_medium%3Ddocs) [![Download APK](https://hub.degate.com/common/wallet-setup-img-en/Download_Android.png)](https://download.degate.com/apps/degate-android.apk)

## Ways to add a wallet

The **Add Wallet** screen offers six options:

<img src="../.gitbook/assets/add-wallet.jpg" alt="Add Wallet options" width="360">

* **Connect External Wallet:** sign in with a wallet you already have, via WalletConnect (up to 10 external wallet accounts).
* **Connect Hardware Wallet:** Bluetooth-capable OneKey and Ledger models are supported in the mobile app. Check the connection screen for supported models and networks. See the FAQ below.
* **Create Wallet:** generate a new wallet with a 12-word recovery phrase, created locally on your device. Write the phrase down and store it offline.
* **Import Wallet:** bring an existing 12-word recovery phrase.
* **Continue with Email:** the fastest start if you are new to crypto. Enter your email, confirm the code from your inbox, and set a DeGate password (separate from the password you use to sign in to your email provider).
* **Sync from DeGate Web:** bring an account you use on the DeGate web app into the app.

{% hint style="info" %}
We do not recommend keeping large balances in an email wallet. If you permanently lose access to its linked email, you may be unable to recover it. For higher-value assets, we recommend **Create Wallet** or **Import Wallet** (or connecting a hardware wallet), so that you hold the recovery phrase yourself.
{% endhint %}

## Web accounts and mobile transactions

The web app does not support transactions. Use the iOS or Android mobile app for swaps, transfers, and Turbo Range position actions. If you already use a DeGate web account, choose **Sync from DeGate Web** in the mobile app to bring it into the app.

## FAQ

**Do I need a separate wallet for each chain?**
No. One DeGate wallet gives you addresses across supported chains, generated as you enable each chain and controlled by your keys. See [Wallet Addresses & Networks](../security/wallet-address-and-networks.md).

**Who holds the keys of the wallet I just created?**
It depends on the wallet type. Recovery phrase wallets keep keys on your device; hardware wallets keep them on the hardware device. Email wallets and external-wallet connections have different key handling and recovery dependencies. Read [Security Overview](../security/security-overview.md) and [Wallet Addresses & Networks](../security/wallet-address-and-networks.md) for your chosen method.

**Does creating a wallet require identity verification?**
You can create a recovery phrase wallet without uploading identity documents or completing exchange-style identity verification. **Continue with Email** has a separate sign-in setup, including email verification and a DeGate password. A third-party service you use may have its own identity and regional requirements; check those requirements before using it.

**Can I use a hardware wallet?**
Yes. The mobile app connects over Bluetooth to **Bluetooth-capable OneKey and Ledger models**. Check DeGate's connection screen for supported models and networks. Hardware-wallet accounts support receiving, sending, trading, cross-chain transfers, and Turbo Range. Confirm signatures on the hardware device; do not enter its recovery phrase into your phone.

Hardware-wallet accounts pay network gas from their own address in the chain's native token. Keep enough native tokens there (for example, ETH on Base) for the action you intend to sign. Review network costs on the confirmation screen.
