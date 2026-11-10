# Fees

Ordinary swaps trade a token against USDC: you pay USDC to buy and receive USDC when you sell. The DeGate platform fee follows that token in either direction, regardless of which chains the route uses. As of August 2026, the rate is 0% for stablecoins and 0.02% for other tokens.

Two examples:

* **USDC to USDT:** the other token is USDT, a stablecoin, so the fee is 0%.
* **Selling TSLAx for USDC:** the other token is TSLAx, so the fee is 0.02%. Receiving USDC does not make it a stablecoin swap; the fee follows TSLAx.

There is no subscription fee. Review the platform fee, network cost, and expected output on the confirmation screen before signing.

{% hint style="info" %}
**Ordinary swaps: 0% DeGate platform fee for stablecoins; 0.02% for other tokens, including stock tokens. Automatic swaps within Turbo Range: 0% DeGate platform swap fee. Network costs and pool trading fees may still apply.**
{% endhint %}

## Swap fees

These tiers apply to ordinary swaps in Trade. For automatic swaps within Turbo Range, see [Turbo Range swaps](#turbo-range-swaps).

| Tier | Fee | What it covers |
| --- | --- | --- |
| Stablecoins | 0% | Fiat-pegged tokens such as USDC, USDT, PYUSD, USDS, DAI, USDe, and EURC, across all supported chains |
| All other tokens | 0.02% | Every token that is not a stablecoin, from native coins to tokenized stocks, RWA assets, and long-tail tokens |

The exact fee for any token is shown in the swap quote before you confirm. If a token's quoted fee differs from the tier you expect, the quote is authoritative.

## Turbo Range swaps

As of 6 November 2026, automatic swaps within Turbo Range have **no DeGate platform swap fee**, including those that prepare the pool assets when you open or increase a position. The ordinary 0.02% rate does not apply to these swaps. Network costs and any pool trading fees are separate; review the expected output and network cost before signing.

If you buy a token in Trade before opening a position, or sell returned tokens in Trade after closing, that is an ordinary swap and follows the rates above.

## Everything else

* **USDC bridging:** there is no DeGate platform fee for supported same-asset USDC cross-chain transfers. These transfers are described as 1:1, as of July 2026. Network costs still apply. Check the USDC transfer screen for available routes.
* **Simple Earn:** there is no DeGate deposit, withdrawal, or performance fee. The selected vault determines its yield and withdrawal conditions.
* **Sends:** there is no DeGate platform fee for supported same-chain or cross-chain sends. Network costs still apply; review the route and fees before confirming.
* **Gas:** for non-hardware accounts, eligible asset balances can fund the native tokens needed for supported actions. Hardware accounts need native gas tokens at their own address. See the FAQ below.

## FAQ

**Which tokens count as stablecoins?**
The stablecoin fee tier includes these fiat-pegged tokens: USDC, USDT, PYUSD, USDS, DAI, USDe, EURC, and many more across supported chains. The app uses the current token classification; review the quoted fee before confirming. Fee tiers can change; the rates here reflect the August 2026 snapshot. If a stablecoin you trade is quoted at 0.02% and you think it belongs in the 0% tier, suggest it through the **Feedback** feature in the DeGate app (or the other channels on [Contact Support](support/contact-support.md)).

**If stablecoin swaps have zero fees, why is USDC to USDT not exactly 1:1?**
The fee and the exchange rate are two different things. A 0% platform fee means no DeGate swap fee is added; it does not set the rate. USDC and USDT are separate assets with their own market prices, so a swap between them executes at the current market rate on the route, which is typically close to, but not exactly, 1:1. The quote shows the exact amount you will receive before you confirm. Moving USDC between supported chains is a same-asset transfer, described as 1:1 with no DeGate platform fee. Network costs are separate.

**What do xStocks and Ondo assets cost to swap?**
For ordinary swaps, 0.02%, as of August 2026. Automatic swaps within Turbo Range have no DeGate platform swap fee, as of 6 November 2026. One boundary note: the tier follows the token classification, not the issuer. Ondo's USDY, a dollar-denominated yield token, sits in the stablecoin tier and swaps at 0%, while ordinary swaps of Ondo's onchain stocks and ETFs have a 0.02% platform fee.

**Who pays gas?**
You pay the network cost. For non-hardware accounts, eligible assets in the wallet can fund the gas needed for supported actions. Check the network cost before signing. Gas is funded from commonly held tokens in your balance, such as USDC, USDT, or major native coins (some native tokens, such as BTC, cannot fund gas on other chains; they still pay network fees on their own chain). Your balance does need enough to cover the network fees of a transaction.

**How does gas work on a hardware wallet account?**
Hardware wallet accounts pay network gas from their own address in the chain's native token, not from your DeGate balance. Keep enough native tokens at that address for the action you want to sign. For a current Ethereum stock LP in Turbo Range, that means ETH on Ethereum. A send on Base needs ETH on Base; these are separate network balances. Check an existing position's network before claiming fees or closing it.
