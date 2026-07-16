# Wallet Addresses & Networks

One DeGate wallet gives you addresses across supported chains. How those addresses come to exist depends on which type of wallet you use; this page explains each type and what it means for recovery.

## Your addresses across chains

When you receive assets, use your DeGate address for the network the sender is on: tap **Receive** in the app, pick the chain, and copy the address or share the QR code. Your DeGate address is the same across all EVM chains (Ethereum, Base, Arbitrum, Optimism, Polygon, BNB and so on): these chains share a single underlying key, rather than being independently generated per chain. Solana, Aptos, and Bitcoin use their own address formats. Incoming deposits are detected automatically, and everything you receive shows up in your unified balance.

Since only your private keys can authorize transactions from these addresses, DeGate cannot unilaterally move your funds.

## How your wallet is created

### Mnemonic wallets (created or imported)

**Create Wallet** generates a random 12-word BIP39 recovery phrase locally on your device; **Import Wallet** accepts an existing 12-word phrase. Per-chain private keys are derived from the phrase using BIP44, the standard framework for hierarchical deterministic wallets. This is a fully standard, open derivation: your 12 words alone can restore this wallet in DeGate, or in any other BIP39/BIP44-compatible wallet.

### Hardware wallets

Your private key never leaves the hardware device; DeGate reads your addresses over standard derivation paths. Hardware accounts currently cover Receive, same-chain Send, and Turbo Range. For other in-app operations, DeGate uses a secondary, app-managed operating wallet so you aren't prompted on your device for every action; your hardware key itself never leaves the device regardless.

### Email, external-wallet, and web-sync wallets

These wallet types don't start from a phrase you write down. Instead, DeGate derives an operating wallet from your existing login (your email-linked embedded wallet, or the external wallet you signed in with), through a signature-based process managed entirely by the DeGate app.

Day to day, this works like any other wallet: sign in the same way on a new device and the app restores the same addresses. **What's different is independence from DeGate**: today, recovering this wallet's funds using tools *outside* the DeGate app isn't supported yet for these wallet types. If you want a wallet you can recover independently of DeGate under any circumstance, use a mnemonic wallet or link a hardware wallet.

## Supported networks

The current list of supported networks appears in [What is DeGate](../README.md#supported-networks), with per-network fee tiers on the [Fees](../fees.md) page. Addresses for newly-supported chains are generated the first time you enable that chain, not automatically ahead of time. Hardware-wallet accounts cover a subset of networks; check the app for current coverage.

## What this means for recovery

* **Mnemonic wallet:** your 12-word phrase is the backup. It restores the wallet in DeGate, or in any BIP39/BIP44-compatible wallet, with no dependency on DeGate at all.
* **Hardware wallet:** your device is the backup. Your primary balance is recoverable with your device and any compatible wallet software, independent of DeGate.
* **Email wallet:** your email and password restore access in the app or web app, as long as DeGate is operating. Independent recovery outside the DeGate app isn't supported yet.
* **Sign in with Wallet / web-sync:** signing in again with the same external wallet restores access, as long as DeGate is operating. Independent recovery outside the DeGate app isn't supported yet.

## FAQ

**Can I send any token to my DeGate address?**
Send tokens on their matching network to your address for that network. Everything on supported networks lands in your unified balance.

**If DeGate disappeared, would I lose access to these addresses?**
Your funds are on-chain at addresses only your keys control, so the assets themselves are never on DeGate's servers. Whether *you* can restore access without DeGate's app depends on wallet type: mnemonic wallets and hardware wallets can be restored independently at any time. Email wallets and Sign in with Wallet / web-sync wallets currently rely on the DeGate app to restore access; independent recovery for these is planned but not yet available. See the [Self-Custody FAQ](self-custody-faq.md).
