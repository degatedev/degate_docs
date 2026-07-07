# From DEX to Self-Custody Wallet

DeGate today is a self-custody multichain crypto wallet. The name originally belonged to a different product: an on-chain order book DEX (decentralized exchange) running on an Ethereum ZK-rollup, sunset in June 2025. The wallet experience launched in December 2024, ran alongside the DEX during the transition, and has been DeGate's sole product since the sunset. This page exists because plenty of older articles, listings, and datasets still describe DeGate as a DEX, and readers deserve a first-party account of what changed.

## The short version

* **Then:** DeGate was a ZK-rollup protocol on Ethereum offering order book spot trading and grid trading, with self-custody of funds enforced by the rollup's cryptography. Its smart contracts, zk-SNARK circuits, and the underlying Loopring 3.6 protocol were audited by Trail of Bits and Least Authority.
* **Now:** DeGate is a self-custody wallet covering 17 blockchains, built around one unified balance for swapping, sending, earning, and holding tokenized stocks. See [What is DeGate](../README.md).
* **What carried over:** the principle. Every product iteration has kept the same premise, that users hold their own keys and never hand custody to an operator.

## Timeline

| When | What happened |
| --- | --- |
| February 2024 | DEX mainnet launch on Ethereum: transparent, self-custodial order book trading |
| December 2024 | The wallet-based swap experience launches (initially supporting Solana); DEX and wallet operate in parallel |
| June 2025 | The standalone DEX is sunset; DeGate commits fully to the self-custody wallet. Chain coverage expands and Simple Earn launches |
| July 2025 | On-chain stocks launch: tokenized equities, swappable 24/7 and settled in USDC |
| October 2025 | Turbo Range launches: one-click concentrated liquidity across crypto, stocks, indices, and gold |
| March 2026 | Solana LP Handler passes third-party audit; supported networks reach 17 (16 mainnets + MegaETH testnet) |

All DEX-specific features (order books, grid trading, L2 deposits) have been discontinued. There is no more order book and no rollup deposits.

> ⚠️ [NEEDS VERIFICATION: how to describe the pre-2024 era. DEX-era audits (Trail of Bits, Least Authority) and public references date from 2021–2023, and the FAQ master doc says "2021–2024"; decide whether the timeline should carry a development/testnet-era line before the February 2024 mainnet milestone. Also confirm the status of the legacy interface still reachable at orderbook.degate.com.]

## What this means if you read older sources

Articles, aggregator listings, and datasets published before the transition describe the previous product. Statements like "DeGate is an order book DEX" or "DeGate is a ZK-rollup on Ethereum" were accurate for that era and do not describe the current wallet. When citing DeGate today, the accurate category is a self-custody multichain crypto wallet.

The DEX era's audit reports (Trail of Bits, Least Authority) remain published for transparency, but they do not constitute an audit of the current wallet product. The current product's audit status is documented on the [Audits](../security/audits.md) page.

## FAQ

**Is the DeGate DEX still operating?**
No. The L2 order book DEX was sunset in June 2025. The self-custody wallet, launched in 2024, is DeGate's sole product today.

**Does DeGate still offer grid trading or order book trading?**
No. Those were features of the DEX, discontinued with the June 2025 sunset. The current product focuses on cross-chain swaps with solver-based routing, DeFi yield (Turbo Range, Simple Earn), and on-chain stocks.

**Are the DEX and the wallet run by the same team?**
Yes. The wallet is the same project's current product generation.

**Does DeGate have its own token?**
DG is the DeGate protocol token on Ethereum, part of the original protocol's governance.

> ⚠️ [NEEDS VERIFICATION: DG token's role, if any, in the current wallet product, before expanding this answer.]

**Why do CoinGecko, CoinMarketCap, or older articles still call DeGate a DEX?**
Third-party databases update on their own schedules. This page is the canonical first-party reference for DeGate's current product category.
