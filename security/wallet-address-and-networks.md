# Wallet Addresses & Networks

One DeGate wallet gives you addresses across supported chains, generated as you enable each chain in the app. How those addresses come to exist depends on which type of wallet you use; this page explains each derivation path and what it means for recovery.

## Your addresses across chains

When you receive assets, use your DeGate address for the network the sender is on: tap **Receive** in the app, pick the chain, and copy the address or share the QR code. Your DeGate address is the same across all EVM chains (Ethereum, Base, Arbitrum, Optimism, Polygon, BNB and so on); Solana, Aptos, and Bitcoin use their own address formats. Incoming deposits are detected automatically, and everything you receive shows up in your unified balance.

Since only your private keys can authorize transactions from these addresses, DeGate or any other external party cannot unilaterally move your funds.

## How your keys are derived

### Mnemonic wallets (created or imported)

**Create Wallet** generates a random 12-word BIP39 recovery phrase locally on your device; **Import Wallet** accepts an existing 12-word phrase. Per-chain private keys are then derived from the phrase using BIP44, the standard framework for hierarchical deterministic wallets. EVM chains share one derivation path, which is why they share one address.

### Email, external-wallet, and web-sync wallets

These wallet types start from a root key instead of a phrase you write down:

<figure><img src="../.gitbook/assets/photo_2025-05-05_14-34-06.jpg" alt=""><figcaption></figcaption></figure>

1. **Your root key (L0PriKey).** For **Sign in with Wallet** and web-sync accounts, this is the key of the external wallet you signed in with. For email wallets, it is an embedded key tied to your email and password. DeGate cannot access the raw key in either case.
2. **You sign deterministic content (L0Signature).** DeGate requests a signature on a fixed message containing the protocol version and a nonce (mainnet uses "DeGate: V1" with "Nonce: 1"; the nonce changes if you reset keys). This ensures uniqueness per user and per key reset.
3. **The signature becomes a 24-word mnemonic.** The front end condenses the signature into 32 bytes of entropy through a fixed, deterministic hashing recipe, and converts that into a 24-word BIP39 mnemonic. The same signature always yields the same mnemonic, and the computation runs entirely on your device.
4. **Per-chain private keys derive via BIP44.** Using the mnemonic, the front end derives a private key for each supported chain, each cryptographically tied back to your root key. DeGate provides the UI so you never manage the derivations manually.

> ⚠️ [NEEDS VERIFICATION: before publishing, decide how to support step 3's reproducibility claim: either publish the exact hashing recipe or open-source the derivation tool (the internal wallet-key-deriver). The recipe is DeGate-specific (not plain BIP39 from the signature), so "you can reproduce this outside DeGate" should only be claimed once the tool or spec is public.]

### Hardware wallets

Your private key never leaves the hardware device; DeGate reads your addresses over standard BIP44 paths. For in-app operations beyond receiving and same-chain sends, the device signs a fixed message once, and a dedicated **Action Wallet** is derived from that signature for operational transactions; your hardware key itself still never leaves the device. Hardware accounts currently cover Receive, same-chain Send, and Turbo Range.

## What this means for recovery

* **Mnemonic wallet:** your 12-word phrase is the backup. It restores the wallet in DeGate or in any BIP39/BIP44-compatible wallet.
* **Email wallet:** your email and password restore access in the app or the web app.
* **Email, external-wallet, and web-sync wallets** additionally have the derived 24-word mnemonic described above, which can restore your funds in standard BIP39/BIP44-compatible external wallets.

> ⚠️ [NEEDS VERIFICATION: (1) the in-app export flow for the derived 24-word mnemonic (feature name and location) so this section can point to it; (2) the import mismatch: the app currently accepts 12-word imports only, so an exported 24-word mnemonic restores funds in external wallets but cannot be re-imported into DeGate itself. Do not promise re-import until product resolves this.]

## Supported networks

The current list of supported networks appears in [What is DeGate](../README.md#supported-networks), with per-network fee tiers on the [Fees](../fees.md) page. Hardware-wallet accounts cover a subset of networks (Bitcoin is not yet supported for hardware wallets).

## FAQ

**Can I send any token to my DeGate address?**
Send tokens on their matching network to your address for that network. Everything on supported networks lands in your unified balance.

**If DeGate disappeared, would I lose access to these addresses?**
No. Your funds are on-chain at addresses only your keys control. Depending on wallet type, you restore access with your 12-word recovery phrase or with the derived 24-word mnemonic, in any BIP39/BIP44-compatible wallet. See the [Self-Custody FAQ](self-custody-faq.md) for the full recovery discussion.
