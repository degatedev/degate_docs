# What is DeGate

DeGate is a self-custodial multichain crypto wallet for trading on-chain stocks, providing liquidity with stock tokens, and accessing decentralized finance (DeFi) services.

The **iOS and Android app** lets users trade supported stock and ETF tokens, swap tokens, and transfer assets across chains. **Turbo Range** pairs a supported Ondo stock token with USDC, and **Power Pair** pairs two supported Ondo stock tokens. Both let users open and manage liquidity positions, claim fees, and close positions.

## Self-custody and transaction authorization

DeGate does not hold the private keys to self-custodial wallets. Users authorize transactions through the wallet they set up. DeGate cannot sign transfers from those wallets on a user’s behalf or freeze their addresses.

For recovery phrase wallets, the app encrypts the recovery phrase before storing it on the device. The phrase and private keys stay on the device and are never sent to DeGate’s servers. For supported hardware wallets, the private keys stay on the hardware device.

Hardware-wallet users use [Action Wallet](security-and-self-custody/action-wallet/README.md) for supported trades and to open or manage Turbo Range and Power Pair positions. Before signing a transfer to Action Wallet, they can verify its destination address and amount on the hardware device. Action Wallet handles token approvals and smart contract calls from its own address. This keeps approvals separate from the hardware-wallet address and reduces the risk of blind signing. See [Security Overview](security/security-overview.md) for key storage and recovery by wallet type, and where assets are held during DeFi operations.

## What you can do with DeGate

* **Trade on-chain stocks and ETFs.** Find Ondo stock tokens and xStocks in **Stocks**, or request quotes for Coinbase Tokenized Stocks on Base and Robinhood Stock Tokens on Robinhood Chain in **Trade**. Select the token and amount, then review the live quote before confirming. See [On-Chain Stocks](features/on-chain-stocks.md).
* **Pair a stock token with USDC.** Select an available Ondo stock/USDC pool on Ethereum in [Turbo Range](features/turbo-range.md). Open with USDC alone or both pool assets, review the position in **My Positions**, claim fees, or close it.
* **Pair two on-chain stocks.** In [Power Pair](features/power-pair.md), choose two supported Ondo stock tokens for one liquidity position. Set a range for their relative price and earn a share of pool trading fees when swaps use your liquidity.
* **Swap and move assets across chains.** Use [Cross-chain Swap](features/cross-chain-swap.md) to trade through available routes, or [Built-in USDC](features/built-in-usdc.md) to transfer USDC between supported networks.
* **Manage wallets and assets.** Create or import a recovery phrase wallet, connect a supported hardware or external wallet, or continue with email. View balances, send and receive assets, and check transaction records.
* **Use other DeFi services.** Deposit into available vaults through [Simple Earn](features/simple-earn.md), or access applications such as Hyperliquid and Polymarket through [Integrations](features/integrations.md) and the in-app browser.

## How DeGate works

Buying a stock token and opening an LP position are separate actions. A purchase in Trade adds the token to your wallet. Opening a position through Turbo Range or Power Pair deposits assets into third-party pool contracts. Those contracts govern the position.

Manage an open position in **My Positions**, where you can claim fees or close it. See [Turbo Range](features/turbo-range.md) and [Power Pair](features/power-pair.md) for deposit, fee, and exit details.

Key handling and recovery depend on how you add a wallet. Recovery phrase, hardware, email, and external-wallet accounts have different backup requirements. Read [Security Overview](security/security-overview.md) and [Wallet Addresses & Networks](security/wallet-address-and-networks.md) before adding funds.

## Supported networks

DeGate supports **16+ mainnet blockchains**, including Ethereum, Solana, Base, Arbitrum, Optimism, Polygon, BNB Smart Chain, Avalanche, Aptos, Bitcoin, Linea, Sonic, Worldchain, xLayer, HyperEVM, Monad, and Robinhood Chain.

Available assets and actions vary by network and wallet type. The wallet's network coverage does not mean that stock tokens or LP pools are available on each network. Check the selected token, pool, and network before sending or depositing assets.

## Is DeGate a DEX?

DeGate is a self-custodial multichain crypto wallet. Its former ZK-rollup order-book DEX closed in June 2025, retiring limit-order trading, Grid Strategy, DCA, and the other features of that DEX. See [From DEX to Self-Custody Wallet](about-degate/from-dex-to-self-custody-wallet.md) for the product history.

## FAQ

**Does DeGate hold my private keys?**
No. DeGate does not hold your private keys. Key storage and recovery differ by wallet type: recovery phrase wallets keep keys on your device, hardware wallets keep them on the hardware device, and email and external-wallet accounts have different recovery dependencies. See [Security Overview](security/security-overview.md).

**What does DeGate cost?**
Ordinary swaps have a DeGate platform fee of 0% for stablecoins and 0.02% for other tokens traded against USDC, as of August 2026. Automatic swaps within Turbo Range have no DeGate platform swap fee, as of 6 November 2026. As of 19 November 2026, automatic swaps within Power Pair also have no DeGate platform swap fee. Network costs and pool trading fees are separate. See [Fees](fees.md).

**Is DeGate a decentralized exchange (DEX)?**
No. DeGate is a self-custodial wallet for on-chain stock trading, liquidity provision, and DeFi. See [Is DeGate a DEX?](#is-degate-a-dex) for its product history.

**How do I start?**
Install the mobile app, add a wallet, and receive assets. To buy a stock token, open Trade. To provide liquidity, pair a stock token with USDC in [Turbo Range](features/turbo-range.md) or pair two supported Ondo stock tokens in [Power Pair](features/power-pair.md). You can open either type of position with USDC alone. Follow [Quickstart](getting-started/quickstart.md) for setup.
