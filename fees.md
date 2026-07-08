# Fees

DeGate charges a swap fee that depends on the token you trade, not on which chains the route touches. As of July 2026: xStocks and Ondo RWA assets are 0%, most stablecoins are 0.01%, major native coins are 0.1%, and any token not listed below defaults to 0.25%. There are no subscription fees and no hidden charges.

{% hint style="info" %}
**xStocks tokens and Ondo Finance RWA assets incur zero DeGate swap fees.**
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

> ⚠️ [NEEDS VERIFICATION: fee-table rows for HyperEVM and MegaETH (testnet), which are supported networks but absent from this table.]

## Everything else

* **USDC bridging: free.** Moving USDC between supported chains is 1:1 with zero DeGate fees, across 10+ chains.
* **Simple Earn: free.** No DeGate fees; all vault yield goes to the user.
* **Turbo Range:** deposit and withdraw anytime; standard on-chain gas costs are handled automatically.

> ⚠️ [NEEDS VERIFICATION: whether Turbo Range carries any DeGate fee on earned LP fees, given the audited integrator fee-routing controls.]

* **Sends: free.** DeGate charges no fee on sends, whether same-chain or cross-chain; cross-chain sends are routed automatically. Standard network (gas) costs still apply, handled as below.
* **Gas:** handled automatically and deducted from your balance. You never need to hold native gas tokens.

## FAQ

**Are there hidden fees?**
No subscription fees, no hidden charges, and no monetization of user data. The swap fee tiers above plus network gas are the cost structure.

**Why are xStocks and Ondo assets free to swap?**
DeGate currently applies a zero swap fee to xStocks tokens and Ondo RWA assets, as of the July 2026 snapshot. Fee tiers can change; this page is updated when they do.

**Who pays gas?**
You do, but automatically: DeGate purchases the needed gas tokens and deducts the cost from your balance, so you do not need to pre-fund gas on each chain you use. Your balance does need enough to cover the network fees of a transaction.
