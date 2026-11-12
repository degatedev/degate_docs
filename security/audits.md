# Audits

## Security Audit Report: Solana LP Handler

### Overview

Adevar Labs independently audited DeGate's Solana LP Handler, a wrapper around Raydium CLMM liquidity management flows used for Turbo Range on Solana. The report is dated **20 March 2026** and is labeled **after fix review**.

### What was audited

The report covers the Solana LP Handler's `programs/*` code, including:

* Position creation and liquidity increases and decreases
* Token swaps into the required deposit ratio
* Reward and fee collection
* Security controls for integrator fee routing and operational safety

The report identifies the reviewed code versions. Its findings apply to that scope, not to every component or later version of DeGate.

### Findings after fix review

The report's executive summary records these findings and remediation statuses:

| Severity | Findings | Fixed | Acknowledged |
| --- | --- | --- | --- |
| Critical | 0 | 0 | 0 |
| High | 1 | 1 | 0 |
| Medium | 5 | 5 | 0 |
| Low | 4 | 1 | 3 |

See the full report for the individual findings, developer responses, assumptions, and recommendations. An audit does not guarantee that a program is free of vulnerabilities.

### Scope boundaries

This audit covers the **Solana LP Handler only**. It is not an audit of the entire DeGate wallet, email-wallet infrastructure, cross-chain routing, Simple Earn integrations, or mobile and web interfaces. It does not cover Community V3 or the Ethereum stock pools described in [Turbo Range](../features/turbo-range.md).

### Full report

{% file src="../.gitbook/assets/DeGate_audit_report_full.pdf" %}

_Adevar Labs, 20 March 2026. Version: after fix review._

{% hint style="info" %}
To report a vulnerability, contact [bounty@degate.com](mailto:bounty@degate.com). See [Bug Bounty](bug-bounty.md) for reporting instructions.
{% endhint %}
