# Wallet Addresses & Networks

Use the address for the network where you want to receive assets. How the addresses are created and restored depends on your wallet type. Check the method below before adding funds or replacing a device.

## Your addresses across chains

When you receive assets, use your DeGate address for the network the sender is on: tap **Receive** in the app, pick the chain, and copy the address or share the QR code. Your DeGate address is the same across all EVM chains (Ethereum, Base, Arbitrum, Optimism, Polygon, BNB and so on): these chains share a single underlying key, rather than being independently generated per chain. Solana, Aptos, and Bitcoin use their own address formats. Supported assets appear in your balance after the deposit is detected. Check the address, network, and token if an asset does not appear.

You authorize transactions from the wallet you selected. The key handling and recovery requirements for each wallet type are described below.

## How your wallet is created

### Mnemonic wallets (created or imported)

**Create wallet** generates a random 12-word BIP39 recovery phrase locally on your device; **Import wallet** accepts an existing 12-word phrase. Per-chain private keys are derived from the phrase using BIP44, the standard framework for hierarchical deterministic wallets. To restore the same addresses in another wallet application, it must support the recovery phrase, network, derivation path, and account settings used for that address. BIP39/BIP44 support alone does not guarantee that an application will display the same account. Check the restored address before receiving or sending assets.

### Hardware wallets

Your private key stays on the hardware device; DeGate connects to addresses derived by the device. Connect a Bluetooth-capable OneKey or Ledger model in the DeGate mobile app to receive, send, trade, transfer across chains, or manage Turbo Range positions. Check the connection screen for supported models and networks, and confirm signatures on the hardware device.

Hardware wallet accounts pay network gas from their own address in the chain's native token, not from your DeGate balance. Keep enough native tokens for the action you want to sign. A current Ethereum stock LP in Turbo Range needs ETH on Ethereum; a send on Base needs ETH on Base. Check an existing position's network before claiming fees or closing it.

### Email, external-wallet, and web-sync wallets

These wallet types don't start from a phrase you write down. Instead, DeGate derives an operating wallet from your existing login (your email-linked embedded wallet, or the external wallet you signed in with), through a signature-based process in the app.

For an external-wallet or web-sync account, the derived DeGate addresses are separate from your original external-wallet address. Restoring that external wallet in another application does not by itself restore the derived DeGate balances. Reconnect the same external wallet in the DeGate app to restore the derived addresses. For an email wallet, use the original email address and DeGate password in the DeGate app.

## Supported networks

The current list of supported networks appears in [What is DeGate](../README.md#supported-networks), with per-network fee tiers on the [Fees](../fees.md) page. An address for a newly supported chain is generated when you first enable it. Hardware-wallet accounts cover a subset of networks; check the app for current coverage.

## What this means for recovery

* **Mnemonic wallet:** back up its 12-word recovery phrase. Restore in DeGate, or in wallet software with the same network, derivation path, and account settings, then verify the address. If you created several wallets, back up each phrase separately.
* **Hardware wallet:** keep the device and the recovery backup created during its setup. Reconnect it to DeGate, or use wallet software that supports the same device, network, and derivation path. Check that the address matches. A pool position may require an interface that supports the underlying protocol.
* **Email wallet:** use the original email address and DeGate password in the DeGate app. This recovery method depends on the email-linked wallet infrastructure and DeGate's sign-in flow.
* **External-wallet / web-sync:** preserve access to the original external wallet, then reconnect it in the DeGate app. Assets at derived DeGate addresses will not appear merely because you restore the original external-wallet address elsewhere.

Restoring email and external-wallet / web-sync wallets outside the DeGate app is not currently supported. These methods have different recovery dependencies from a recovery phrase or hardware wallet.

### If you lose access to your email

An email wallet depends on access to its linked email address. If you permanently lose access to that email, you may be unable to recover the wallet. Your DeGate password is separate from your email provider's password. We do not recommend keeping large balances in an email wallet; for funds you need to recover independently of email sign-in, consider a recovery phrase wallet or a supported hardware wallet and keep its backup securely.

## FAQ

**Can I send any token to my DeGate address?**
Send tokens on their matching network to your address for that network. Supported assets appear after the deposit is detected. Check that both the token and its network are supported before sending.

**Why is my address the same on Ethereum and Base?**
All EVM chains share a single underlying key in your DeGate wallet, so they share one address. That makes receiving simpler: any EVM network's deposit goes to the same address, and you pick the network when sharing it. Solana, Aptos, and Bitcoin use their own address formats.
