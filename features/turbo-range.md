# Turbo Range

Turbo Range is DeGate's liquidity provision (LP) feature. You choose a pool and price range, then authorize a deposit from your wallet into the pool's contracts. Your position can earn a share of pool trading fees when trades use its liquidity within that range.

## What you can provide liquidity for

Check **Turbo Range in the mobile app** for the current pools, assets, and networks. A token available in Trade may have no Turbo Range pool. New stock LP positions currently use Ondo stock/USDC pools on Ethereum; earlier xStocks positions remain visible in **My Positions**. The web app does not support transactions.

## Where it runs

Current Ethereum stock pools use [Community Uniswap V3](https://communityv3.org/), a third-party protocol based on a Uniswap V3 fork. DeGate provides the wallet interface for selecting a pool, reviewing a quote, and authorizing position actions. Deposited assets enter the pool protocol's contracts. Community Uniswap V3 pools are distinct from Uniswap V3 pools.

For an existing position, check its network and pool before managing or closing it.

## How you enter a position

* **Single-token entry.** Deposit just USDC and DeGate handles conversion into the pool's required ratio. Dual-asset deposits also work.
* **Cross-chain deposits.** Fund a position with USDC from any supported chain; DeGate routes it, with no manual bridging.
* **No lock-up.** You can close a position at any time; your tokens return to your wallet and earned fees are collected.

## Closing a position

Closing returns the assets held by the position at that time, which may include both pool tokens. Review the expected assets and unclaimed fees before confirming. Closing does not currently convert everything to USDC in one step.

If you want only USDC, close the position first, then request a separate sell quote in **Trade** for any returned non-USDC tokens. That sale requires an executable quote and follows the ordinary swap fees and network costs. You can also keep the returned tokens in your wallet.

## Swap fees

As of 6 November 2026, automatic swaps within Turbo Range have a **0% DeGate platform swap fee**, including swaps that prepare the pool assets when opening or increasing a position. The ordinary 0.02% swap fee does not apply to these swaps. Network costs and pool trading fees may still apply. Review the swap result and network cost before signing.

Buying tokens separately in Trade before opening, or selling returned tokens in Trade after closing, follows the [ordinary swap fees](../fees.md).

## Earnings and risks

The APR shown in the app is an annualized estimate based on historical pool activity, not a guaranteed return. Fees actually earned depend on trading volume, how trades use your liquidity, other liquidity in the pool, and whether the price remains within your range. Evaluate fees received together with the current value of both position assets.

Concentrated-liquidity positions are subject to impermanent loss and smart-contract risk. Pool activity and price movement change the amounts of both tokens in your position. If the price moves outside the selected range, the position generally holds one side of the pair and stops earning new trading fees at the current price. See the FAQ below before changing your strategy or closing.

## FAQ

**What does DeGate handle when I open an LP position?**
Turbo Range brings pool selection, single- or dual-asset deposits, and position management into the mobile wallet. Review the pool protocol, network, deposit assets, and costs before signing. Hardware-wallet accounts need the chain's native token at their hardware address to pay network fees; see [Fees](../fees.md).

**Can I withdraw at any time?**
Yes. There is no lock-up period.

**What happens when the price leaves my range?**
An out-of-range position generally stops earning new trading fees at the current price and holds one side of the pair. You can keep it open or close it. The current stock LP flow does not let you edit the range in place; changing it requires closing and opening a new position, with a new quote and network costs. Your position can lose value even after earning fees.
