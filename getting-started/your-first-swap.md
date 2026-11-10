# Your First Swap

Use Trade in the DeGate mobile app to buy a supported token with USDC or sell a token for USDC. Cross-chain routes include any required bridging in the swap flow. Review the source and destination networks, expected output, and costs before signing.

## Before you start

Buys on DeGate are paid in USDC, and selling a token settles back into USDC. So you need USDC first, and there are two ways to get it: deposit USDC from any supported chain, or sell a token you already hold (for example, selling TSLAx gives you USDC to buy with; note that a sell still needs network fees covered, so it may not go through if your wallet holds nothing besides that token). Non-hardware accounts can pay network costs for supported actions from eligible asset balances. Hardware accounts need the relevant native token at their own address. See [Quickstart](quickstart.md) if you have not set up yet.

## Steps

1. Open **Trade** in the DeGate mobile app.
2. Search for the token you want to receive. You can search across all supported chains at once.
3. Pay with USDC from your balance.
4. Review the quote. Check the expected output and price impact before confirming. The displayed amount reflects the DeGate platform swap fee for that token tier (see [Fees](../fees.md)).
5. Confirm. Same-chain swaps complete in seconds; cross-chain swaps typically take 30 seconds to 2 minutes, and the app shows an estimated completion time before you confirm. You can follow progress in the **Activity** tab.

A quote can change or become unavailable before execution. If a swap fails or stays pending, check its status and transaction record before trying again. Use Feedback in the app if you need us to investigate.

## What happens in the background

The quoted route includes any required bridging. For non-hardware accounts, eligible asset balances can fund the gas needed for supported actions. You pay that network cost; hardware accounts fund it from native tokens at their own address. You review and authorize the transaction from your selected wallet. The mechanics are described in [Cross-chain Swap](../features/cross-chain-swap.md).

## FAQ

**Why is my swap taking longer than expected?**
Cross-chain routes settle on more than one network and inherit those networks' confirmation times; congestion can add delay. Check the Activity tab, and see the [FAQ](../support/faq.md) if a swap seems stuck.

**Is there a limit on how much I can swap?**
There are no account-based limits. For very large swaps, price impact may be higher on assets with lower on-chain liquidity; the app displays price impact before confirmation.

**What fee did I pay?**
Ordinary swap fees have two tiers, set by the token traded against USDC: 0% for stablecoins, and 0.02% for all other tokens, as of August 2026. Details: [Fees](../fees.md).
