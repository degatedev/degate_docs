# Audit Report

## Security Audit Report — Solana LP Handler

### Overview

DeGate's Solana LP Handler has been independently audited by **Adevar Labs**, a boutique blockchain security firm with over 100 audits completed and a track record securing protocols across Solana, Ethereum, and beyond.

The audit covered the full `programs/*` codebase of the Solana LP Handler — a wrapper around Raydium CLMM liquidity management flows that powers DeGate's Turbo Range product on Solana.

***

### What Was Audited

The Solana LP Handler supports:

* Position creation and liquidity management (increase/decrease)
* Token swaps into the required deposit ratio (zap flows)
* Reward and fee collection
* Protocol-specific security controls for integrator fee routing and operational safety

**Auditor:** Adevar Labs **Report Date:** March 20, 2026 **Repository:** [github.com/degatedev/solana\_lp\_handler](https://github.com/degatedev/solana_lp_handler) **After-Fix Commit:** `c09ed65b8b1ed572c0d743d69a15064134cc8fc1`

***

### Auditor's Assessment

> _"The Degate team has demonstrated a strong understanding of Raydium CLMM primitives and the preliminary audit adopted a security-first mindset. The Degate team promptly resolved all High and Medium severity issues and demonstrated a strong understanding of the security implications."_
>
> — Adevar Labs, March 2026

***

### Full Report

The complete audit report including all findings, proof-of-concept exploits, code snippets, and developer responses is publicly available:

📄 [**Download Full Audit Report (PDF)**](https://link-to-your-report.pdf)

***

_Audited by Adevar Labs · March 2026_

{% hint style="info" %}
For submission of bug bounty reports, please contact us at [bounty@degate.com](mailto:bounty@degate.com)&#x20;
{% endhint %}
