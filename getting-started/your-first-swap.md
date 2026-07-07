# Your First Swap

A swap on DeGate works the same whether the token lives on the chain your funds are on or a different one: you choose the token, DeGate handles routing, bridging, and gas behind the scenes, and the result lands in your unified balance.

## Before you start

You need a funded wallet. Any supported token on any supported chain works as the starting point; there is no need to hold the destination chain's gas token. See [Quickstart](quickstart.md) if you have not set up yet.

## Steps

1. Open **Swap** in the app.
2. Search for the token you want to receive. You can search across all supported chains at once.
3. Choose what to pay with, or let DeGate use your unified balance.
4. Review the quote. The app shows the expected output amount and price impact before you confirm, and the displayed amount reflects the DeGate swap fee for that token tier (see [Fees](../fees.md)).
5. Confirm. Same-chain swaps complete in seconds; cross-chain swaps typically take 30 seconds to 2 minutes, and the app shows an estimated completion time before you confirm. You can follow progress in the **Activity** tab.

If market conditions change significantly during execution, the transaction reverts and your original tokens are returned automatically.

## What happens in the background

DeGate finds the route, executes any bridging, and pays gas on the chains involved by purchasing the necessary gas tokens automatically. You sign with your own key; at no point does DeGate take custody of your assets. The mechanics are described in [Cross-chain Swap](../features/cross-chain-swap.md).

## FAQ

**Why is my swap taking longer than expected?**
Cross-chain routes settle on more than one network and inherit those networks' confirmation times; congestion can add delay. Check the Activity tab, and see [Troubleshooting](../support/troubleshooting.md) if a swap seems stuck.

**Is there a limit on how much I can swap?**
There are no account-based limits. For very large swaps, price impact may be higher on assets with lower on-chain liquidity; the app displays price impact before confirmation.

**What fee did I pay?**
Swap fees depend on the token tier: 0.01% for most stablecoins, 0.1% for major native coins, 0% for xStocks on Solana, and 0.25% by default for other tokens, as of July 2026. Details: [Fees](../fees.md).
