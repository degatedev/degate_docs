# Audits

## Security Audit Report: Solana LP Handler

### Overview

DeGate's Solana LP Handler has been independently audited by **Adevar Labs**, a boutique blockchain security firm with over 100 audits completed and a track record securing protocols across Solana, Ethereum, and beyond.

The audit covered the full `programs/*` codebase of the Solana LP Handler, a wrapper around Raydium CLMM liquidity management flows that powers DeGate's [Turbo Range](../features/turbo-range.md) product on Solana.

### What was audited

The Solana LP Handler supports:

* Position creation and liquidity management (increase/decrease)
* Token swaps into the required deposit ratio (zap flows)
* Reward and fee collection
* Protocol-specific security controls for integrator fee routing and operational safety

**Auditor:** Adevar Labs
**Report date:** March 20, 2026
**Repository:** [github.com/degatedev/solana\_lp\_handler](https://github.com/degatedev/solana_lp_handler)
**After-fix commit:** `c09ed65b8b1ed572c0d743d69a15064134cc8fc1`

### Auditor's assessment

> _"The Degate team has demonstrated a strong understanding of Raydium CLMM primitives and the preliminary audit adopted a security-first mindset. The Degate team promptly resolved all High and Medium severity issues and demonstrated a strong understanding of the security implications."_
>
> — Adevar Labs, March 2026

### Scope, stated plainly

This audit covers the Solana LP Handler only. Other components of the current wallet (email-wallet key storage, cross-chain routing, Simple Earn integrations, the mobile and web front ends) have not yet undergone external third-party audit; they rely on open-source review and the active [bug bounty](bug-bounty.md).

Audit reports from the retired ZK-rollup DEX era (Trail of Bits, Least Authority) remain published for transparency; they cover the previous product, not the current wallet. See [From DEX to Self-Custody Wallet](../about-degate/from-dex-to-self-custody-wallet.md).

### Full report

The complete audit report including all findings, proof-of-concept exploits, code snippets, and developer responses is publicly available:

{% file src="../.gitbook/assets/DeGate_audit_report_full.pdf" %}

_Audited by Adevar Labs · March 2026_

{% hint style="info" %}
To report a vulnerability, contact [bounty@degate.com](mailto:bounty@degate.com). See [Bug Bounty](bug-bounty.md).
{% endhint %}
