# Fees

For ordinary swaps, DeGate charges a platform swap fee that depends on the token you trade, not on which chains the route touches. Ordinary swaps have USDC on one side: you pay in USDC when you buy, and you receive USDC when you sell. For these ordinary swaps, the fee tier follows the token traded against USDC, in either direction. As of August 2026 there are two tiers: 0% when that token is a stablecoin, and 0.02% when it is anything else.

Two examples:

* **USDC to USDT:** the other token is USDT, a stablecoin, so the fee is 0%.
* **Selling TSLAx for USDC:** the other token is TSLAx, so the fee is 0.02%. Receiving USDC does not make it a stablecoin swap; the fee follows TSLAx.

There are no subscription fees and no hidden charges.

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

As of 6 November 2026, automatic swaps within Turbo Range, including those that prepare the pool assets when opening or increasing a position, have a **0% DeGate platform swap fee**. The ordinary 0.02% rate does not apply to these swaps. Network costs and any pool trading fees are separate; review the expected output and network cost before signing.

If you buy a token in Trade before opening a position, or sell returned tokens in Trade after closing, that is an ordinary swap and follows the rates above.

## Everything else

* **USDC bridging: free.** Moving USDC between supported chains is 1:1 with zero DeGate fees, across 10+ chains.
* **Simple Earn: free.** No DeGate fees; all vault yield goes to the user. Deposit and withdraw anytime.
* **Sends: free.** DeGate charges no fee on sends, whether same-chain or cross-chain; cross-chain sends are routed automatically. Standard network (gas) costs still apply, handled as below.
* **Gas:** handled automatically for every account type except hardware wallets — deducted from your balance and funded from commonly held tokens such as USDC, so you do not need to hold native gas tokens. See the FAQ below for hardware wallet accounts.

## FAQ

**Which tokens count as stablecoins?**
Fiat-pegged tokens that DeGate classifies as stablecoins: USDC, USDT, PYUSD, USDS, DAI, USDe, EURC, and many more across supported chains. The list is maintained in the app, so the swap quote you see before confirming always reflects the fee that applies. Fee tiers can change; this page is updated when they do, as of the August 2026 snapshot. If a stablecoin you trade is quoted at 0.02% and you think it belongs in the 0% tier, suggest it through the **Feedback** feature in the DeGate app (or the other channels on [Contact Support](support/contact-support.md)).

**If stablecoin swaps have zero fees, why is USDC to USDT not exactly 1:1?**
The fee and the exchange rate are two different things. A 0% fee means DeGate adds no charge on top of the trade; it does not set the rate. USDC and USDT are separate assets with their own market prices, so a swap between them executes at the current market rate on the route, which is typically close to, but not exactly, 1:1. The quote shows the exact amount you will receive before you confirm. Moving the same asset between chains is a different operation: USDC bridging is 1:1 with zero DeGate fees.

**What do xStocks and Ondo assets cost to swap?**
For ordinary swaps, 0.02%, as of August 2026. Automatic swaps within Turbo Range have a 0% DeGate platform swap fee as of 6 November 2026. One boundary note: the tier follows DeGate's token classification, not the issuer. Ondo's USDY, a dollar-denominated yield token, sits in the stablecoin tier and swaps at 0%, while ordinary swaps of Ondo's onchain stocks and ETFs have a 0.02% platform fee.

**Who pays gas?**
You do, but automatically: for every account type except hardware wallets, DeGate purchases the needed gas tokens and deducts the cost from your balance, so you do not need to pre-fund gas on each chain you use. Gas is funded from commonly held tokens in your balance, such as USDC, USDT, or major native coins (a few native tokens, like BTC, can't be used to cover gas on other chains — on their own chain they pay gas as usual). Your balance does need enough to cover the network fees of a transaction.

**How does gas work on a hardware wallet account?**
Hardware wallet accounts pay network gas from their own address in the chain's native token, not from your DeGate balance. Keep a small balance there (for example, ETH on Base or SOL on Solana) for sends and Turbo Range operations, including withdrawing and closing a position.
