# Turbo Range

Use Turbo Range to open and manage stock liquidity provision (LP) positions. Select a pool, fee tier, price range, and deposit amount, then review the assets and network cost before signing. Your position can earn a share of pool trading fees when trades use its liquidity within that range.

## What you can provide liquidity for

Check **Turbo Range in the mobile app** for the current pools, assets, and networks. A token available in Trade may have no Turbo Range pool. New stock LP positions currently use Ondo stock/USDC pools on Ethereum. You can find earlier xStocks positions in **My Positions**. The web app does not support transactions.

## Where it runs

Current Ethereum stock pools use [Community V3](https://communityv3.org/), a third-party protocol based on a Uniswap V3 fork. Select a pool and authorize position actions through Turbo Range. The assets you deposit enter Community V3's pool contracts, which govern the position. Community V3 is a separate protocol; its pools are distinct from Uniswap V3 pools.

For an existing position, open **My Positions** and check its network and pool before managing or closing it. Check the pool list for currently available deposits. Wallet-wide network support does not mean an LP pool is available on each network.

## How you enter a position

* **Single-token entry.** Deposit USDC alone. The opening flow prepares the two pool assets in the ratio required for your selected range. Dual-asset deposits also work.
* **Cross-chain deposits.** For supported routes, fund a position with USDC from another chain. The deposit is routed to the pool's network; check the destination before signing.
* **No lock-up.** You can close a position at any time; your tokens return to your wallet and earned fees are collected.

## Closing a position

Closing returns the assets held by the position at that time, which may include both pool tokens. Review the expected assets and unclaimed fees before confirming. Closing does not currently convert everything to USDC in one step.

If you want only USDC, close the position first, then request a separate sell quote in **Trade** for any returned non-USDC tokens. That sale requires an executable quote and follows the ordinary swap fees and network costs. You can also keep the returned tokens in your wallet.

## Swap fees

As of 6 November 2026, automatic swaps within Turbo Range have **no DeGate platform swap fee**, including swaps that prepare the pool assets when you open or increase a position. The ordinary 0.02% swap fee does not apply to these swaps. Network costs and pool trading fees may still apply. Review the swap result and network cost before signing.

Buying tokens separately in Trade before opening, or selling returned tokens in Trade after closing, follows the [ordinary swap fees](../fees.md).

## Earnings and risks

The displayed APR is an annualized estimate based on historical pool activity. It does not guarantee future returns. Fees actually earned depend on trading volume, how trades use your liquidity, other liquidity in the pool, and whether the price remains within your range. Evaluate fees received together with the current value of both position assets.

Concentrated-liquidity positions are subject to impermanent loss and smart-contract risk. Pool activity and price movement change the amounts of both tokens in your position. If the price moves outside the selected range, the position generally holds one side of the pair and stops earning new trading fees at the current price. See the FAQ below before changing your strategy or closing.

## FAQ

**What does DeGate handle when I open an LP position?**
Select a pool, deposit one or both assets, and manage the position in the DeGate mobile app. Review the pool protocol, network, deposit assets, and costs before signing. Hardware-wallet accounts need the chain's native token at their hardware address to pay network fees; see [Fees](../fees.md).

**Can I withdraw at any time?**
Yes. There is no lock-up period.

**What happens when the price leaves my range?**
An out-of-range position generally stops earning new trading fees at the current price and holds one side of the pair. You can keep it open or close it. The current stock LP flow does not let you edit the range in place; changing it requires closing and opening a new position, with a new quote and network costs. Your position can lose value even after earning fees.
