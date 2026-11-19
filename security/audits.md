# Audits

## Security Audit Report: Solana LP Handler

### Overview

In March 2026, **Adevar Labs** audited DeGate’s Solana LP Handler, the component that powered Turbo Range’s earlier Solana pools on Raydium CLMM.

The report covers the Solana LP Handler’s `programs/*` codebase. New stock LP positions in [Turbo Range](../features/turbo-range.md) currently use Ondo stock/USDC pools on Ethereum. Those pools and the Ethereum pools used by [Power Pair](../features/power-pair.md) run on the third-party Community V3 protocol. Community V3’s Ethereum pool contracts are outside the scope of this Solana audit.

### What was audited

The audited Solana LP Handler covered these flows:

* Position creation and liquidity management (increase/decrease)
* Token swaps into the required deposit ratio (zap flows)
* Reward and fee collection
* Protocol-specific security controls for integrator fee routing and operational safety

All High and Medium severity findings were resolved before the first production deployment.

#### Auditor’s assessment

> _“The Degate team has demonstrated a strong understanding of Raydium CLMM primitives and the preliminary audit adopted a security-first mindset. The Degate team promptly resolved all High and Medium severity issues and demonstrated a strong understanding of the security implications.”_
>
> — Adevar Labs, March 2026

### Ongoing security review

The Adevar Labs report above covers the Solana LP Handler. The other components of the current wallet (email-wallet key storage, cross-chain routing, Simple Earn integrations, the mobile and web front ends) are reviewed on an ongoing basis by DeGate’s dedicated security team as part of our regular release process, and are covered by the active [bug bounty](bug-bounty.md), which focuses on the live web and mobile apps.

### Full report

The complete audit report including all findings, proof-of-concept exploits, code snippets, and developer responses is publicly available:

{% file src="../.gitbook/assets/DeGate_audit_report_full.pdf" %}

_Audited by Adevar Labs · March 2026_

{% hint style="info" %}
To report a vulnerability, contact [bounty@degate.com](mailto:bounty@degate.com). See [Bug Bounty](bug-bounty.md).
{% endhint %}
