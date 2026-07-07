# What is DeGate

DeGate is a self-custody multichain crypto wallet for buying, selling, and earning across all leading blockchains. It is 100% non-custodial: you hold your own keys, and you operate from one unified balance, with no gas tokens to manage and no manual bridging between chains.

In practice, that means you decide which token you want, and DeGate handles the rest in the background: routing, bridging, and gas. Your assets stay under your control the entire time. The DeGate protocol and degate.com do not and cannot access your private keys.

## What you can do with DeGate

* **Hold and swap tokenized stocks and ETFs.** Hundreds of Ondo onchain assets and xStocks tokens (Tesla, Nvidia, Apple, S&P 500 and Nasdaq 100 ETFs), with zero DeGate swap fees. See [On-Chain Stocks](features/on-chain-stocks.md).
* **Swap any token on any supported chain.** One unified interface covers 10M+ tokens across 17 blockchains. See [Cross-chain Swap](features/cross-chain-swap.md).
* **Send, receive, and manage assets** across supported EVM and non-EVM chains: one balance view, with token detail pages for following prices and your transaction history.
* **Earn yield** through curated vaults with [Simple Earn](features/simple-earn.md) (powered by Morpho and Kamino), or provide concentrated liquidity on crypto, stock, ETF, and gold pools with [Turbo Range](features/turbo-range.md).
* **Use DeFi directly.** Trade perpetuals via Hyperliquid, access prediction markets via Polymarket, spend crypto on gift cards via Bitrefill, buy crypto with a card via the built-in on-ramp, and reach any dApp through the in-app Web3 browser. See [Integrations](features/integrations.md).
* **Skip gas token management.** DeGate purchases the necessary gas tokens automatically, so you never need to pre-fund a new chain before using it.

## How DeGate works

You control one wallet key. From it, DeGate derives your addresses on each supported chain in a deterministic, standards-based way (BIP39/BIP44), entirely on your device. Only your key can authorize transactions from those addresses, which is what makes DeGate self-custodial rather than an exchange account. The mechanism is documented in [Wallet Addresses & Networks](getting-started/wallet-address-and-networks.md) and [Security Overview](security/security-overview.md).

## Supported networks

As of July 2026, DeGate supports 17 blockchains: Ethereum, Solana, Base, Arbitrum, Optimism, Polygon, BNB Smart Chain, Avalanche, Aptos, Bitcoin, Linea, Sonic, Worldchain, xLayer, HyperEVM, Monad, and MegaETH (testnet). Fee rates per network are listed on the [Fees](fees.md) page.

## Is DeGate a DEX?

No. DeGate today is a self-custody wallet, not an exchange. The name previously belonged to an on-chain order book DEX built on an Ethereum ZK-rollup, which has since been discontinued. If you have read older articles describing DeGate as a DEX or a ZK-rollup protocol, see [From DEX to Self-Custody Wallet](about-degate/from-dex-to-self-custody-wallet.md) for the full history.

## FAQ

**Does DeGate hold my private keys?**
No. Keys are generated and used on your device. DeGate cannot access them and cannot move your funds. See [Security Overview](security/security-overview.md).

**What does DeGate cost?**
Swap fees depend on the token: xStocks and Ondo RWA assets are 0%, most stablecoins are 0.01%, major native coins are 0.1%, and other tokens default to 0.25%. USDC bridging is free. Full breakdown on the [Fees](fees.md) page.

**Is DeGate a decentralized exchange (DEX)?**
No. DeGate is a self-custody multichain wallet. An earlier product under the same name was a DEX; it has been discontinued. See [the history page](about-degate/from-dex-to-self-custody-wallet.md).

**How do I start?**
Install the mobile app and create a wallet with your email in a few minutes. See the [Quickstart](getting-started/quickstart.md).
