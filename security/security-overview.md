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

Email-based wallets (available in both the app and the web app) use an embedded key tied to your email and password; mnemonic wallets are generated locally on your device; hardware-wallet keys never leave the device. None of these methods gives DeGate access to your keys.

> ⚠️ [NEEDS VERIFICATION: (1) device-level key protection details in the mobile app (secure enclave/keystore usage, biometrics); (2) how to disclose the email wallet's embedded-key infrastructure (it is provided via Privy) — naming the provider and phrasing the custody nuance needs a marketing/legal decision, since "keys only you control" reads differently when an embedded-wallet provider is involved.]

## Audit status, stated plainly

The **Solana LP Handler** (the contract powering Turbo Range on Solana) was audited by Adevar Labs in March 2026; the report is public and the code is open-source. That audit's scope is limited to the LP Handler. Other components of the current wallet (email-wallet key storage, the cross-chain routing, Simple Earn integrations, the mobile and web front ends) have not yet undergone external third-party audit; they rely on open-source review and the active bug bounty at [bounty@degate.com](mailto:bounty@degate.com).

Audit reports from the retired ZK-rollup DEX era (Trail of Bits, Least Authority) remain published for transparency but do not cover the current wallet product. Details: [Audits](audits.md), [From DEX to Self-Custody Wallet](../about-degate/from-dex-to-self-custody-wallet.md).

## FAQ

**If DeGate's servers went down, could I still access my funds?**
Yes. Your assets are on-chain at addresses derived from your key via open standards (BIP39/BIP44). With your recovery phrase you could access them through any compatible wallet. See the [Self-Custody FAQ](self-custody-faq.md).

**Can DeGate freeze my account?**
There is no custodial account to freeze. Assets sit at addresses controlled by your key, and only you can authorize transactions.
