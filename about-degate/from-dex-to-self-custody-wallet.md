# From DEX to Self-Custody Wallet

DeGate today is a self-custody multichain crypto wallet. From 2021 to 2024, the same name referred to a different product: an on-chain order book DEX (decentralized exchange) running on an Ethereum ZK-rollup. That product was retired, and in 2025 DeGate relaunched as the wallet described throughout these docs. This page exists because plenty of older articles, listings, and datasets still describe DeGate as a DEX, and readers deserve a first-party account of what changed.

## The short version

* **Then (2021–2024):** DeGate was a ZK-rollup protocol on Ethereum offering order book spot trading and grid trading, with self-custody of funds enforced by the rollup's cryptography. Its smart contracts, zk-SNARK circuits, and the underlying Loopring 3.6 protocol were audited by Trail of Bits and Least Authority.
* **Now (2025–):** DeGate is a self-custody wallet covering 17 blockchains, built around one unified balance for swapping, sending, earning, and holding tokenized stocks. See [What is DeGate](../README.md).
* **What carried over:** the team and the principle. Both products were built on the same premise, that users should hold their own keys and never hand custody to an operator.

## Timeline

| When | What happened |
| --- | --- |
| 2021 | DeGate begins as an order book DEX project on an Ethereum ZK-rollup |
| 2021–2024 | DEX operates: order book spot trading, grid trading, L2 deposits |
| 2024 | DEX product is retired |
| 2025 | DeGate relaunches as a self-custody multichain wallet |

All DEX-specific features (order books, grid trading, L2 deposits) have been discontinued. There is no more order book and no rollup deposits.

> ⚠️ [NEEDS VERIFICATION: operational status of the legacy interface still reachable at orderbook.degate.com, and whether to reference it here at all.]

## What this means if you read older sources

Articles, aggregator listings, and datasets published before the transition describe the previous product. Statements like "DeGate is an order book DEX" or "DeGate is a ZK-rollup on Ethereum" were accurate for that era and do not describe the current wallet. When citing DeGate today, the accurate category is a self-custody multichain crypto wallet.

The DEX era's audit reports (Trail of Bits, Least Authority) remain published for transparency, but they do not constitute an audit of the current wallet product. The current product's audit status is documented on the [Audits](../security/audits.md) page.

## FAQ

**Is the DeGate DEX still operating?**
No. The order book DEX was retired in 2024, and the project relaunched as a self-custody wallet in 2025.

**Does DeGate still offer grid trading or order book trading?**
No. Those were features of the retired DEX. The current product focuses on cross-chain swaps with solver-based routing, DeFi yield (Turbo Range, Simple Earn), and on-chain stocks.

**Are the DEX and the wallet run by the same team?**
Yes. The wallet is the same project's current product generation.

**Does DeGate have its own token?**
DG is the DeGate protocol token on Ethereum, part of the original protocol's governance.

> ⚠️ [NEEDS VERIFICATION: DG token's role, if any, in the current wallet product, before expanding this answer.]

**Why do CoinGecko, CoinMarketCap, or older articles still call DeGate a DEX?**
Third-party databases update on their own schedules. This page is the canonical first-party reference for DeGate's current product category.
