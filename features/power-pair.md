# Power Pair

Power Pair lets you put two supported Ondo stock tokens into one concentrated-liquidity position and earn a share of pool trading fees when swaps use your liquidity. Choose the two tokens and the price range in which you want to provide liquidity.

Stock pools in [Turbo Range](turbo-range.md) pair a stock token with USDC. Power Pair pairs two stock tokens, so the range tracks the price of one token in units of the other. For example, in an AAPLon/NVDAon pair, the range is measured in NVDAon per AAPLon. The position's value also depends on the market prices of both tokens.

## Open a position

On the DeGate app’s **Home** screen, find **Power Pair** and tap **View More**. You can also open it from **Explore → Native Apps → Power Pair**. Power Pair supports Ondo stock tokens. xStocks are unavailable for Power Pair positions. Check the selected pair for its network.

1. In **Power Pair**, tap **Invest Now**. Under **Create Power Pair**, select **Stock A** and **Stock B**, then tap **Next**.
2. Choose a **Fee tier** and a **Price range**. Check the order of the pair before setting the range. The screen shows which token the price is quoted in.
3. Under **Your investment**, choose an investment mode and enter the amount. The AAPLon/NVDAon flow, for example, offers both stock tokens together, either stock token alone, or **USDC Only**. When the flow uses an automatic swap, review the expected deposit amounts. The app may show a minimum or maximum swap amount.
4. Tap **Create Position**. On **Review Investment**, check the deposit assets, range, and maximum network fee before tapping **Confirm**. If the selected pool doesn’t exist yet, the fee breakdown can include a one-time pool creation cost.

Hardware-wallet users can open and manage Power Pair positions through [Action Wallet](../security-and-self-custody/action-wallet/README.md).

## Manage a position

Open **My Positions** in Power Pair to see the current price relative to your range, the capital in the position, and unclaimed yield. The position details show the pool and network. For example, AAPLon and NVDAon are Ondo stock tokens paired in an Ethereum pool on the third-party Community V3 protocol. Deposited assets enter the pool contracts.

Use **Claim** to collect unclaimed yield while keeping the position open. This button appears when there is yield to claim. Use **Increase Investment** to add to the position or **Withdraw & Close** to exit. Check the assets and amounts shown before confirming an exit. The mix of the two stock tokens can change as the price ratio moves.

## Fees, earnings, and risks

Automatic swaps within Power Pair have no DeGate platform swap fee. Network costs and pool trading fees may still apply.

The pool's fee tier sets the trading fee paid on swaps that use the pool. Your position can earn a share of those fees when swaps use its liquidity. Estimated APR uses the pair's price volatility over the past 30 days and the range you select. It assumes the price ratio stays within your range and future volatility matches the past 30 days. The **Best APR** fee tier is based on a 30-day backtest that uses the period's low and high as the range. Actual fees depend on how much trading uses your liquidity and how long it stays in range. Check the network fee and any pool creation cost separately in the investment preview.

A position can lose value if either stock token falls in value. As the relative price changes, the position can hold more of one token and less of the other. Outside the range, it generally holds one of the two tokens and stops earning new fees at the current price. The position may be worth less than holding the two tokens separately, even after fees. Providing liquidity also exposes your assets to the pool's smart-contract risk.
