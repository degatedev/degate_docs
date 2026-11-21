# Self-Custody FAQ

Before adding funds, check how your wallet stores keys, what you need to back up, and how to restore access. Recovery requirements differ by wallet type and by how you first accessed DeGate.

## Who controls my keys?

Key handling and recovery differ by wallet type. A recovery phrase wallet keeps its keys on your device, and a hardware wallet keeps them on the hardware device. Email wallets use an email-linked embedded wallet; connecting an external wallet creates a separate DeGate operating wallet. See the recovery requirements in [Security Overview](security-overview.md) and [Wallet Addresses & Networks](wallet-address-and-networks.md).

## Can DeGate move, freeze, or seize my funds?

No. DeGate does not hold the private keys to self-custodial wallets. DeGate cannot sign a transfer from your address or freeze the wallet address. This does not make assets unrestricted: token issuers may limit transfers, and third-party pool or vault contracts govern deposited assets. See [Security Overview](security-overview.md).

## What do I need to back up?

It depends on how you created the wallet:

* **Mnemonic (recovery phrase) wallet:** Select the wallet itself in the wallet management screen, open **Wallet Details**, and select **Recovery phrase**. If the row shows **Back up now**, follow the prompts. Write down the phrase and store it securely offline. Never store it digitally. Keep a separate backup for each recovery phrase wallet; we cannot replace a lost recovery phrase for you.
* **Email sign-in:** keep access to the linked email address. When you sign in to the DeGate app, enter the six-digit verification code sent to that address. The app asks you to set up a password or biometric unlock on the new device to protect its local data. If you permanently lose access to the linked email, you may be unable to recover the wallet. If you want a wallet you can recover independently of email, choose a recovery phrase wallet or a supported hardware wallet and keep your own backup.
* **External wallet connected in the app:** back up the external wallet according to its recovery method. On the new device, reconnect the original account through **Connect external wallet** to restore its DeGate-derived addresses and view their balances. These addresses are separate from the external wallet’s own address.
* **DeGate Web sync:** keep access to the wallet account you used on DeGate Web. Connect it on DeGate Web and sign to generate a QR code. On the new phone, select **Sync from DeGate Web** and scan it within 60 seconds. Keep the code private. [See the web sync steps](../getting-started/create-a-wallet.md#sync-an-existing-degate-web-account).
* **Hardware wallet:** your device (and the recovery sheet you set up with its manufacturer) is the backup.

Email sign-in, external-wallet, and DeGate Web sync accounts require the DeGate app to restore access. See [Wallet Addresses & Networks](wallet-address-and-networks.md#what-this-means-for-recovery) for recovery requirements by wallet type.

## What if I lose my phone?

Install the official DeGate app on a new phone and follow the recovery method above for your wallet type. For email sign-in, use the original email address and the six-digit verification code sent to it, then set up the unlock method for the new device. Check that the restored addresses match the ones you used before. Your assets remain recorded on-chain when you lose your phone.

## Can I use DeGate on multiple devices?

In the DeGate app on the additional device, use the recovery method above for the wallet you want to access. Check that the addresses match. The same address on the same network refers to the same on-chain assets; an application's display also depends on which tokens and positions it supports.

## How is this different from keeping assets on an exchange?

With an exchange account, the exchange holds the assets and your balance is a claim on the operator; a hack, insolvency, or account restriction can affect your access. With a self-custodial wallet, you hold the assets directly on-chain. You are responsible for your backup and the transactions you authorize. Follow the recovery steps above for the wallet or account you use.

## "Non-custodial", "self-custodial", "unhosted": what's the difference?

DeGate is a self-custodial wallet. You may see the other terms in descriptions of wallets, but a label does not explain how a particular wallet stores keys or restores access. Check the recovery requirements for the method you use, as described above.

## Is self-custody harder to use?

Supported flows include routing, bridging, and network fees in the app, so you do not need to arrange them separately before each action. You still need to keep the appropriate wallet backup and review what you sign.
