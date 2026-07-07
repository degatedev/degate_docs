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
3. DeGate implements a front-end isolation strategy that splits the front end into "wallet code" and "trade code". The wallet code handles the signature mechanism inside an iframe, while trade code executes in a sandboxed environment, keeping keys and signatures inaccessible from the trade side. In the future, the core front-end code will be deployed on decentralized platforms to make it immutable, further enhancing private key security.

## In the mobile app

> ⚠️ [NEEDS VERIFICATION: how keys are stored and protected in the mobile app (secure enclave/keystore usage, biometrics, email-wallet key architecture) before publishing this section.]

## Independent review

DeGate's Solana LP Handler has been independently audited; see [Audits](audits.md). Vulnerability reports are welcome at [bounty@degate.com](mailto:bounty@degate.com); see [Bug Bounty](bug-bounty.md).

## FAQ

**If DeGate's servers went down, could I still access my funds?**
Your addresses and keys are derived via open standards (BIP39/BIP44) on your device. See the [Self-Custody FAQ](self-custody-faq.md) for what recovery looks like.

**Can DeGate freeze my account?**
There is no custodial account to freeze. Assets sit at addresses controlled by your key.

> ⚠️ [NEEDS VERIFICATION: confirm there is no server-side gating of signing/routing that would nuance this answer, before publishing.]
