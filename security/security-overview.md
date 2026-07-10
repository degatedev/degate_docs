# Security Overview

DeGate is self-custodial: your private keys are generated and used on your device, and the DeGate protocol and degate.com do not and cannot access them. This page explains what that means concretely, and how the front end is engineered to keep keys isolated.

## What DeGate can and cannot do

* DeGate **cannot** read your private keys or recovery phrase.
* DeGate **cannot** move funds from your addresses; only signatures produced by your key can.
* DeGate **can** construct transactions for you to sign, quote routes, and manage gas purchases, none of which requires custody of your assets.

## Security of wallet address keys

Your per-chain wallet address keys offer the same level of security as your root asset keys:

1. The DeGate protocol and degate.com do not and cannot access users' wallet private keys.
2. In the web app, wallet address keys are held temporarily in the browser's SessionStorage and automatically cleared when the tab closes. SessionStorage does not support cross-domain or cross-session access.
3. DeGate implements a front-end isolation strategy that splits the front end into "wallet code" and "trade code". The wallet code handles the signature mechanism inside an iframe, while trade code executes in a sandboxed environment, keeping keys and signatures inaccessible from the trade side.

> ⚠️ [NEEDS VERIFICATION: points 2 and 3 are carried over from the current live docs and describe the web architecture. Confirm with engineering that they still describe today's product accurately (and how they map to the mobile app) before publishing. The old copy's forward-looking sentence about deploying the front end to decentralized platforms has been dropped; restore only if it is still the plan and worth stating publicly.]

## Key storage by wallet type

DeGate supports several ways of holding a wallet, and the key material lives in a different place for each:

* **Created or imported mnemonic wallets:** the recovery phrase is generated (or entered) locally and keys stay on your device.
* **Email wallets** (app and web app): an embedded key tied to your email and password.
* **Sign in with Wallet / web-sync accounts:** the root key stays in your own external wallet; DeGate derives its operating keys from a signature you make, as described in [Wallet Addresses & Networks](wallet-address-and-networks.md).
* **Hardware wallets:** the private key never leaves the device.

None of these methods gives DeGate access to your keys.

> ⚠️ [NEEDS VERIFICATION: (1) device-level key protection details in the mobile app (secure enclave/keystore usage, biometrics) — engineering to supply, to be reviewed together with the web/mobile architecture description below; (2) how to disclose the email wallet's embedded-key infrastructure (it is provided via Privy) — naming the provider and phrasing the custody nuance needs a marketing/legal decision.]

## Independent review

DeGate's components are put through independent security review as they ship; the most recent published audit covers the Solana LP Handler, the contract powering Turbo Range (Adevar Labs, March 2026). Reports, scope, and what is and is not covered are documented on the [Audits](audits.md) page. Vulnerability reports are welcome at [bounty@degate.com](mailto:bounty@degate.com); see [Bug Bounty](bug-bounty.md).

## FAQ

**If DeGate's servers went down, could I still access my funds?**
It depends on your wallet type. Mnemonic wallets: yes, your recovery phrase restores funds in any BIP39/BIP44-compatible wallet. Hardware wallets: yes, your keys are on your device. Email wallets: your root key can be exported through a standalone export tool built on Privy that works independently of the DeGate app; for the simplest independence story, use a mnemonic wallet. See the [Self-Custody FAQ](self-custody-faq.md).

> ⚠️ [NEEDS VERIFICATION before publishing the email-wallet answer: (1) engineering to confirm the end-to-end path from the exported root key to funds at DA addresses (the export yields the L0 key; deriving the DA mnemonic from it additionally needs the derivation recipe, which is not yet published); (2) whether to officially bless and link the export tool (degatedev.github.io/privy_wallet_export) in docs and Official Links — it asks users for email login, so it must be formally owned, maintained, and referenced only from official surfaces.]

**Can DeGate freeze my account?**
There is no custodial account to freeze. Assets sit at addresses controlled by your key, and only you can authorize transactions.
