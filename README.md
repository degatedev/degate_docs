# What is DeGate

DeGate is a self-custody multichain crypto wallet for trading on-chain stocks and managing stock liquidity positions.

Use the **iOS or Android app** to buy and sell supported stock and ETF tokens, open stock liquidity provision (LP) positions through **Turbo Range**, claim fees, and close positions. The app also supports token swaps, cross-chain transfers, and other DeFi services.

## What you can do with DeGate

* **Trade on-chain stocks and ETFs.** Find Coinbase Tokenized Stocks on Base and Robinhood Stock Tokens on Robinhood Chain in **Trade**. Select the token and amount, then review the live quote before confirming. See [On-Chain Stocks](features/on-chain-stocks.md).
* **Open and manage stock LP positions.** Select an available Ondo stock/USDC pool on Ethereum in [Turbo Range](features/turbo-range.md). Open with USDC alone or both pool assets, review the position in **My Positions**, claim fees, or close it.
* **Swap and move assets across chains.** Use [Cross-chain Swap](features/cross-chain-swap.md) to trade through available routes, or [Built-in USDC](features/built-in-usdc.md) to transfer USDC between supported networks.
* **Manage wallets and assets.** Create or import a recovery phrase wallet, connect a supported hardware or external wallet, or continue with email. View balances, send and receive assets, and check transaction records.
* **Use other DeFi services.** Deposit into available vaults through [Simple Earn](features/simple-earn.md), or access applications such as Hyperliquid and Polymarket through [Integrations](features/integrations.md) and the in-app browser.

## How DeGate works

Buying a stock token and opening an LP position are separate actions. A purchase in Trade adds the token to your wallet. Opening a position in Turbo Range deposits assets into third-party pool contracts. The pool's contracts govern the position; Turbo Range provides the interface for opening and managing it.

Manage an open position in **My Positions**, where you can claim fees or close it. See [Turbo Range](features/turbo-range.md) for deposit, fee, and exit details.

Key handling and recovery depend on how you add a wallet. Recovery phrase, hardware, email, and external-wallet accounts have different backup requirements. Read [Security Overview](security/security-overview.md) and [Wallet Addresses & Networks](security/wallet-address-and-networks.md) before adding funds.

## Supported networks

DeGate supports **16+ mainnet blockchains**, including Ethereum, Solana, Base, Arbitrum, Optimism, Polygon, BNB Smart Chain, Avalanche, Aptos, Bitcoin, Linea, Sonic, Worldchain, xLayer, HyperEVM, Monad, and Robinhood Chain.

Available assets and actions vary by network and wallet type. The wallet's network coverage does not mean that stock tokens or LP pools are available on each network. Check the selected token, pool, and network before sending or depositing assets.

## Is DeGate a DEX?

DeGate's current product is a self-custody multichain crypto wallet. The earlier order book DEX on an Ethereum ZK-rollup closed in June 2025. See [From DEX to Self-Custody Wallet](about-degate/from-dex-to-self-custody-wallet.md) for the product history.

## FAQ

**Does DeGate hold my private keys?**
No. DeGate does not hold your private keys. Key storage and recovery differ by wallet type: recovery phrase wallets keep keys on your device, hardware wallets keep them on the hardware device, and email and external-wallet accounts have different recovery dependencies. See [Security Overview](security/security-overview.md).

**What does DeGate cost?**
Ordinary swaps have a DeGate platform fee of 0% for stablecoins and 0.02% for other tokens traded against USDC, as of August 2026. Automatic swaps within Turbo Range have no DeGate platform swap fee, as of 6 November 2026. Network costs and pool trading fees are separate. See [Fees](fees.md).

**Is DeGate a decentralized exchange (DEX)?**
No. The earlier DEX closed in June 2025. The current mobile app combines a self-custody wallet, on-chain stock trading, and stock LP management. See [the history page](about-degate/from-dex-to-self-custody-wallet.md).

**How do I start?**
Install the mobile app, add a wallet, and receive assets. To buy a stock token, open Trade. To open a stock LP, select a pool in Turbo Range; buying a token first is not required for a USDC-only deposit. Follow [Quickstart](getting-started/quickstart.md) for setup and [Turbo Range](features/turbo-range.md) for LP actions.
