# Turbo Range

Turbo Range is DeGate's liquidity provision (LP) feature. It puts your funds into a concentrated-liquidity pool within a price range you set; when the market trades inside that range, you earn fees. It compresses a normally multi-step LP workflow into a one-click experience, and it is not limited to one asset class: pools cover crypto, tokenized stocks and ETFs, and gold.

## What you can provide liquidity for

As of July 2026, Turbo Range offers 15 products, including Gold, Bitcoin, Ethereum, Tesla, Nvidia, Google, Amazon, Apple, Meta, MicroStrategy, Circle, SpaceX, a Silver ETF, the S&P 500, and the Nasdaq 100. New pools are added regularly; check the current pool list in **Turbo Range in the mobile app**. The web app does not support transactions.

## Where it runs

* **Solana**, via Raydium CLMM integration
* **Base and Ethereum**, via Uniswap V3

DeGate acts as a streamlined front-end terminal for these pools: you access their liquidity inside the DeGate interface, and manage positions on all three chains from one place.

## How you enter a position

* **Single-token entry.** Deposit just USDC and DeGate handles conversion into the pool's required ratio. Dual-asset deposits also work.
* **Cross-chain deposits.** Fund a position with USDC from any supported chain; DeGate routes it, with no manual bridging.
* **No lock-up.** You can close a position at any time; your tokens return to your wallet and earned fees are collected.

## Swap fees

As of 6 November 2026, automatic swaps within Turbo Range have a **0% DeGate platform swap fee**, including swaps that prepare the pool assets when opening or increasing a position. The ordinary 0.02% swap fee does not apply to these swaps. Network costs and pool trading fees may still apply. Review the swap result and network cost before signing.

Buying tokens separately in Trade before opening, or selling returned tokens in Trade after closing, follows the [ordinary swap fees](../fees.md).

## Earnings and risks

APYs vary with asset volatility and market conditions and can reach 100%+ on volatile pairs. Higher APYs generally mean higher volatility, which also means higher impermanent loss risk. Past performance does not guarantee future returns.

Like all concentrated liquidity provision, Turbo Range positions are subject to impermanent loss. If the price moves outside your selected range, the position stops earning fees and shifts entirely into one token. Your funds remain yours: you can wait for the price to return, adjust the range, or close the position.

## FAQ

**Why use Turbo Range instead of LPing directly on Raydium or Uniswap?**
Four conveniences: cross-chain deposits without bridging, single-token entry, automatic gas handling, and one interface for positions across Solana, Base, and Ethereum. The underlying pools are the same.

**Can I withdraw at any time?**
Yes. There is no lock-up period.

**What happens when the price leaves my range?**
The position stops earning fees and converts into one token. You can rebalance, wait, or exit; nothing is locked or lost beyond normal market movement.
