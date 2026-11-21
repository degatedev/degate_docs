# Power Pair

Power Pair lets you put two supported Ondo stock tokens into one concentrated-liquidity position and earn a share of pool trading fees when swaps use your liquidity. Choose the two tokens and the price range in which you want to provide liquidity.

Stock pools in [Turbo Range](turbo-range.md) pair a stock token with USDC. Power Pair pairs two stock tokens, so you set the range using their relative price, measured in units of one token per unit of the other. When the pair is shown as AAPLon/NVDAon, the range shows how many NVDAon one AAPLon is worth. Tap the switch icon next to the pair to view the same range as NVDAon/AAPLon. The lower and upper bounds become their reciprocals and trade places. The position stays the same. Its value also depends on the market prices of both tokens.

## Where it runs

Power Pair uses pools of Ondo stock tokens on Ethereum that run on the third-party Community V3 protocol. The assets you deposit enter Community V3’s pool contracts, which govern the position. Check the selected pair’s network before investing.

## Open a position

On the DeGate app’s **Home** screen, find **Power Pair** and tap **View More**. You can also open it from **Explore → Native Apps → Power Pair**. Power Pair supports Ondo stock tokens. xStocks are unavailable for Power Pair positions.

1. In **Power Pair**, tap **Invest Now**. Under **Create Power Pair**, select **Stock A** and **Stock B**, then tap **Next**.
2. Choose a **Fee tier** and a **Price range**. Before setting the range, check which token the price is quoted in. You can switch the display direction to view the same range in the inverse quote.
3. Under **Your investment**, choose an available investment mode and enter the amount. Depending on the pair and fee tier, you can deposit both stock tokens together, either stock token on its own, or USDC through **USDC Only**.

   When your deposit requires an automatic swap, the minimum swap amount is $1. The maximum depends on available liquidity and is shown in the app. When U.S. stock market liquidity is unavailable, for example outside market hours, you cannot submit a **USDC Only** or single-stock deposit that requires an automatic swap. Try again later. Review the expected deposit amounts before confirming.
4. Tap **Create Position**. On **Review Investment**, check the deposit assets, range, and maximum network fee before tapping **Confirm**. A one-time pool creation cost applies when opening the position creates a new pool. If the matching pool already exists on-chain, there is no pool creation cost.

Hardware-wallet users can open and manage Power Pair positions through [Action Wallet](../security-and-self-custody/action-wallet/README.md).

## Manage a position

Open **My Positions** in Power Pair to see the current price relative to your range, the capital in the position, and unclaimed yield. The position details also show the pool and network.

Use **Claim** to collect unclaimed yield while keeping the position open. This button appears when there is yield to claim. Use **Increase Investment** to add to the position or **Withdraw & Close** to exit. Check the assets and amounts shown before confirming an exit. The mix of the two stock tokens can change as the price ratio moves.

## Fees, earnings, and risks

Automatic swaps within Power Pair have no DeGate platform swap fee. Network costs and pool trading fees may still apply.

The pool's fee tier sets the trading fee paid on swaps that use the pool. Your position can earn a share of those fees when swaps use its liquidity. Estimated APR uses the pair's price volatility over the past 30 days and the range you select. It assumes the price ratio stays within your range and future volatility matches the past 30 days. The **Best APR** fee tier is based on a 30-day backtest that uses the period's low and high as the range. Actual fees depend on how much trading uses your liquidity and how long it stays in range. Review the network fee and any pool creation cost in the investment preview.

A position can lose value if either stock token falls in value. As the relative price changes, the position can hold more of one token and less of the other. Outside the range, it generally holds one of the two tokens and stops earning new fees at the current price. The position may be worth less than holding the two tokens separately, even after fees. Providing liquidity also exposes your assets to the pool's smart-contract risk.

## FAQ

**Can I copy a Power Pair position from the Leaderboard?**
Yes. The **Leaderboard** on the Power Pair home screen shows open positions ranked by APR. Open a listed position and tap **Copy** to use the same token pair, fee tier, and price range for your own position. Enter your own deposit amount and review the details before confirming.

**Do I need to hold both stock tokens before opening a position?**
You can start with USDC alone when **USDC Only** is available for the pair and fee tier. Opening this way requires an automatic swap. If U.S. stock market liquidity is unavailable, for example outside market hours, the app blocks submission. Try again later. Review the automatic swap amounts and estimated network fee before confirming.

**How do I collect earnings without closing my position?**
Open the position in **My Positions** and tap **Claim** when there is yield to collect. The position stays open.

**Can I open a Power Pair position with a hardware wallet?**
Yes. Select your connected hardware wallet in the app and use [Action Wallet](../security-and-self-custody/action-wallet/README.md) to open the position.

To provide liquidity with a stock token and USDC, see [Turbo Range](turbo-range.md).
