# Fees

DeGate charges a swap fee that depends on the token you trade, not on which chains the route touches. As of July 2026: most stablecoins are 0.01%, major native coins are 0.1%, xStocks tokens on Solana are 0%, and any token not listed below defaults to 0.25%.

{% hint style="info" %}
**All xStocks tokens on the Solana chain incur zero DeGate swap fees.**
{% endhint %}

## Swap fees by network

| Network | 0.01% | 0.1% |
| --- | --- | --- |
| Bitcoin | USDC, USDT and most stablecoins | BTC |
| Ethereum | USDC, USDT and most stablecoins | ETH |
| Solana _(all xStocks tokens: 0%)_ | USDC, USDT and most stablecoins | SOL |
| BSC | USDC, USDT and most stablecoins | BNB |
| Base | USDC, USDT and most stablecoins | ETH |
| Arbitrum | USDC, USDT and most stablecoins | ETH |
| Optimism | USDC, USDT and most stablecoins | ETH |
| Avalanche | USDC, USDT and most stablecoins | AVAX |
| Aptos | USDC, USDT and most stablecoins | APT |
| Polygon | USDC, USDT and most stablecoins | POL |
| Sonic | USDC, USDT and most stablecoins | S |
| xLayer | USDC, USDT and most stablecoins | OKB |
| Monad | USDC, USDT and most stablecoins | MON |
| Linea | USDC, USDT and most stablecoins | ETH |
| Worldchain | USDC | WLD, ETH |

Tokens not listed default to **0.25%**.

## What else affects your total cost

* **Network (gas) costs.** DeGate purchases gas tokens automatically so you never manage them, but on-chain execution has real network costs.

> ⚠️ [NEEDS VERIFICATION: how gas/network costs are presented and charged to the user (included in quote, itemized, or absorbed), so this section states it precisely.]

* **Route pricing.** Cross-chain routes execute against underlying liquidity venues; the quote you confirm reflects the full route.

> ⚠️ [NEEDS VERIFICATION: whether deposits, sends, and withdrawals carry any DeGate fee beyond network costs.]

## FAQ

**Are there hidden fees?**
The DeGate swap fee for each token tier is listed above. Your confirmed quote is what you pay from your balance.

> ⚠️ [NEEDS VERIFICATION: confirm this statement matches how quotes are constructed before publishing.]

**Why are xStocks free to swap?**
DeGate currently applies a zero swap fee to xStocks tokens on Solana, as of the July 2026 snapshot. Fee tiers can change; this page is updated when they do.
