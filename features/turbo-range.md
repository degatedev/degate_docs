# Turbo Range

Turbo Range is DeGate's liquidity provision (LP) feature. It puts your funds into a concentrated-liquidity pool within a price range you set; when the market trades inside that range, you earn fees. It compresses a normally multi-step LP workflow into a one-click experience, and it is not limited to one asset class: pools cover crypto, tokenized stocks, and commodities.

## What you can provide liquidity for

As of July 2026, Turbo Range offers 14 products, including Gold, Bitcoin, Ethereum, Tesla, Nvidia, Google, Amazon, Apple, Meta, MicroStrategy, Circle, a Silver ETF, the S&P 500, and the Nasdaq 100. New pools are added regularly; the live list is in the app at [app.degate.com/turbo-range](https://app.degate.com/turbo-range).

## Where it runs

* **Solana**, via Raydium CLMM integration
* **Base and Ethereum**, via Uniswap V3

DeGate acts as a streamlined front-end terminal for these pools: you access their liquidity inside the DeGate interface, and manage positions on all three chains from one place.

## How you enter a position

* **Single-token entry.** Deposit just USDC and DeGate handles conversion into the pool's required ratio. Dual-asset deposits also work.
* **Cross-chain deposits.** Fund a position with USDC from any supported chain; DeGate routes it, with no manual bridging.
* **No lock-up.** You can close a position at any time; your tokens return to your wallet and earned fees are collected.

## Earnings and risks

APYs vary with asset volatility and market conditions and can reach 100%+ on volatile pairs. Higher APYs generally mean higher volatility, which also means higher impermanent loss risk. Past performance does not guarantee future returns.

Like all concentrated liquidity provision, Turbo Range positions are subject to impermanent loss. If the price moves outside your selected range, the position stops earning fees and shifts entirely into one token. Your funds remain yours: you can wait for the price to return, adjust the range, or close the position.

## Security

The Solana program powering Turbo Range's liquidity management (the Solana LP Handler, a wrapper around Raydium CLMM flows) was independently audited by Adevar Labs in March 2026. See [Audits](../security/audits.md).

## FAQ

**Why use Turbo Range instead of LPing directly on Raydium or Uniswap?**
Four conveniences: cross-chain deposits without bridging, single-token entry, automatic gas handling, and one interface for positions across Solana, Base, and Ethereum. The underlying pools are the same.

**Can I withdraw at any time?**
Yes. There is no lock-up period.

**What happens when the price leaves my range?**
The position stops earning fees and converts into one token. You can rebalance, wait, or exit; nothing is locked or lost beyond normal market movement.
