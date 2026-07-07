# Your First Swap

A swap on DeGate works the same whether the token lives on the chain your funds are on or a different one: you choose the token, DeGate handles routing, bridging, and gas behind the scenes, and the result lands in your unified balance.

## Before you start

You need a funded wallet. Any supported token on any supported chain works as the starting point; there is no need to hold the destination chain's gas token. See [Quickstart](quickstart.md) if you have not set up yet.

## Steps

> ⚠️ [NEEDS VERIFICATION: exact tab and button labels below against the current app build before publishing.]

1. Open the swap view in the app.
2. Choose the token you want to receive. You can search across all supported chains at once.
3. Choose what to pay with, or let DeGate use your unified balance.
4. Review the quote. The displayed amount reflects the DeGate swap fee for that token tier (see [Fees](../fees.md)).
5. Confirm. Cross-chain swaps involve on-chain settlement on more than one network, so allow a little more time than a same-chain swap.

## What happens in the background

DeGate finds the route, executes any bridging, and pays gas on the chains involved by purchasing the necessary gas tokens automatically. You sign with your own key; at no point does DeGate take custody of your assets. The mechanics are described in [Cross-chain Swap](../features/cross-chain-swap.md).

## FAQ

**Why is my swap taking longer than expected?**
Cross-chain routes settle on more than one network and inherit those networks' confirmation times. See [Troubleshooting](../support/troubleshooting.md) if a swap seems stuck.

**What fee did I pay?**
Swap fees depend on the token tier: 0.01% for most stablecoins, 0.1% for major native coins, 0% for xStocks on Solana, and 0.25% by default for other tokens, as of July 2026. Details: [Fees](../fees.md).
