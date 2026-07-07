---
description: Creating your DeGate account
---

# Create a Wallet

There are two ways to create your DeGate wallet. The mobile app is the recommended path.

## 1️⃣ Create a wallet in the DeGate mobile app (recommended)

[![Download on the App Store](https://hub.degate.com/common/wallet-setup-img-en/Download_AppStore.png)](https://apps.apple.com/app/apple-store/id6742168343?pt=127643354\&ct=docs\&mt=8) [![Get it on Google Play](https://hub.degate.com/common/wallet-setup-img-en/Download_GooglePlay.png)](https://play.google.com/store/apps/details?id=com.app.degate\&referrer=utm_source%3Ddocs%26utm_medium%3Ddocs) [![Download APK](https://hub.degate.com/common/wallet-setup-img-en/Download_Android.png)](https://download.degate.com/apps/degate-android.apk)

Choose your preferred method to create or import a wallet. The easiest way is email:

**Enter your email** → **check your inbox** → **enter the confirmation code** → **done**

You will be prompted to set a password for accessing your wallet.

![add wallet](https://hub.degate.com/common/wallet-setup-img-en/add_wallet_resized.jpeg) ![insert email](https://hub.degate.com/common/wallet-setup-img-en/insert_email_cropped.png)

{% hint style="info" %}
For higher-value assets, we recommend the **Create Wallet** or **Import Wallet** methods rather than the email flow, so that you manage the recovery phrase yourself.
{% endhint %}

You do not need an email address: creating a wallet with a mnemonic phrase (seed phrase) works entirely locally. Generate the wallet, write down your recovery phrase offline, and you are set. You can also import an existing wallet, or use **Sign in with Wallet** to log in with an external wallet you already have (via WalletConnect; up to 10 external wallet accounts).

## 2️⃣ Create a wallet via the web app

Visit [app.degate.com](https://app.degate.com) and click **Connect Wallet**, then choose your preferred method.

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

## FAQ

**Do I need a separate wallet for each chain?**
No. One DeGate wallet gives you addresses on every supported chain, derived from a single key you control. See [Wallet Addresses & Networks](../security/wallet-address-and-networks.md).

**Who holds the keys of the wallet I just created?**
You do. DeGate cannot access your private keys regardless of which creation method you choose. See [Security Overview](../security/security-overview.md).

**Does creating a wallet require identity verification?**
No. DeGate is a key-management app, not an account service: there is no registration and no onboarding flow. Feature availability may vary by jurisdiction, and users are responsible for compliance with applicable local laws.

**Can I use a hardware wallet?**
Yes, partially. OneKey (via Bluetooth) is supported today; hardware-wallet accounts currently cover Receive, same-chain Send, and Turbo Range, and do not yet cover Bitcoin. The web app ([app.degate.com](https://app.degate.com)) also supports hardware wallet connections.
