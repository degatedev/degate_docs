# From DEX to Self-Custody Wallet

We previously operated DeGate as an order book DEX on an Ethereum Layer 2 ZK-rollup. We launched our wallet experience in December 2024, ran both products during the transition, and closed the DEX in June 2025. The current product is a self-custody multichain crypto wallet for on-chain stock trading and stock LP management. This page explains the change for readers who encounter older descriptions.

## The short version

* **Then:** we operated an Ethereum Layer 2 (ZK-rollup) protocol offering order book spot trading and grid trading, with self-custody of funds enforced by the rollup's cryptography. Its smart contracts, zk-SNARK circuits, and the underlying Loopring 3.6 protocol were audited by Trail of Bits and Least Authority.
* **Now:** DeGate is a self-custody multichain crypto wallet for trading on-chain stocks, managing stock LP positions, and using DeFi. DeGate supports 16+ mainnet blockchains. See [What is DeGate](../README.md).
* **Wallet access today:** recovery phrase, hardware, email, and external-wallet accounts have different key handling and recovery methods. See [Security Overview](../security/security-overview.md) before choosing how to add a wallet.

## Timeline

This table describes our products at each date, including the asset classes available when Turbo Range launched. For current pools and networks, check [Turbo Range](../features/turbo-range.md) in the DeGate mobile app.

| When | What happened |
| --- | --- |
| March 2022 | DEX testnet launches, with spot limit orders and grid trading |
| October 2023 | DEX mainnet beta launches on DeGate's Ethereum Layer 2 (ZK-rollup) |
| February 2024 | DeGate Layer 2 mainnet launch |
| December 2024 | The wallet-based swap experience launches (initially supporting Solana); DEX and wallet operate in parallel |
| June 2025 | The standalone DEX is sunset; DeGate commits fully to the self-custody wallet. Chain coverage expands and Simple Earn launches |
| July 2025 | On-chain stocks launch: tokenized equities, swappable 24/7 and settled in USDC |
| October 2025 | Turbo Range launches: one-click concentrated liquidity across crypto, stocks, index ETFs, and gold |
| March 2026 | Solana LP Handler passes third-party audit; Network coverage reaches 16 mainnets |
| September 2026 | Robinhood Chain support expands mainnet coverage to 17 blockchains |

We no longer offer the earlier DEX's order books, grid trading, or L2 deposits.

## What this means if you read older sources

Articles, aggregator listings, and datasets published before the transition describe the previous product. Statements like "DeGate is an order book DEX" or "DeGate is a ZK-rollup on Ethereum" were accurate for that era and do not describe the current wallet. The current wallet supports on-chain stock trading, stock LP positions through Turbo Range, and other DeFi services.

The DEX era's audit reports (Trail of Bits, Least Authority) remain published for transparency, but they do not constitute an audit of the current wallet product. The current product's audit status is documented on the [Audits](../security/audits.md) page.

Current network coverage is listed in [Supported networks](../README.md#supported-networks).

## FAQ

**Is the DeGate DEX still operating?**
No. We closed the L2 order book DEX in June 2025. Our current product is the self-custody multichain crypto wallet we launched in 2024.

**Does DeGate still offer grid trading or order book trading?**
No. We discontinued those features when we closed the DEX in June 2025. In our current wallet, you can use cross-chain swaps, on-chain stock trading, Turbo Range, and Simple Earn.

**Are the DEX and the wallet run by the same team?**
Yes. We developed the wallet as the next product from the same project.

**Does DeGate have its own token?**
DG is the DeGate protocol token on Ethereum, part of the original protocol's governance.
