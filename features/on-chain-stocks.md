# On-Chain Stocks

DeGate supports holding and swapping tokenized stocks directly from your self-custody wallet. As of July 2026 this covers 100+ xStocks tokens, spanning individual equities (TSLAx, NVDAx, AAPLx, MSFTx, METAx, GOOGLx, AMZNx, NFLXx, MSTRx, COINx and more), index ETFs (SPYx for the S&P 500, QQQx for the Nasdaq 100), and commodities (GLDx for gold), plus Ondo Finance RWA assets. Swapping xStocks and Ondo assets on DeGate carries zero DeGate swap fees.

Browse the full list at [app.degate.com/stocks](https://app.degate.com/stocks).

## What xStocks are

xStocks are tokenized versions of real-world equities, backed 1:1 by the underlying stock through the Backed Finance framework. The "x" suffix (as in TSLAx) denotes xStocks issuance by Backed Finance. They are freely transferable, DeFi-composable, fractional, and settled in USDC. They are issued by Backed Finance, a third-party issuer, not by DeGate.

## How to buy a tokenized stock

Open the DeGate app, go to **Swap**, search for the token you want (for example TSLAx for Tesla), enter the amount, and confirm. DeGate handles cross-chain routing, bridging, and gas automatically; the tokens appear in your wallet within seconds, at addresses only your key controls.

## Earning yield on stock tokens

Through [Turbo Range](turbo-range.md) you can provide liquidity to xStocks pairs (for example TSLAx/USDC or MSTRx/USDC) and earn LP fees from price movement within your chosen range. APYs are variable and depend on market conditions.

## Dividends, voting, and what the token is legally

* **Dividends:** reflected economically rather than paid in cash. Dividends on the underlying equity are reinvested (net of applicable taxes) through xStocks' rebasing mechanism. On EVM chains balances adjust automatically; on Solana, adjusted balances are shown via Scaled UI.
* **Voting rights:** none. xStocks provide economic exposure, not shareholder voting rights or direct ownership of the underlying shares.
* **Legal form:** each xStock is a bearer debt instrument (tracker certificate) rather than an equity share. Full legal terms are in the Backed Finance prospectus for each token.

## Trading hours and pricing

xStocks tokens can be swapped 24/7, since token transfers settle on-chain at any hour. The underlying equities, however, trade on exchanges with fixed hours. During US market hours, token prices generally stay close to the underlying through market making and arbitrage; outside those hours, prices form from secondary-market supply and demand, so spreads can be wider and deviations can occur. For the full mechanics, see [Why 24/7 tokenized stocks do not mean 24/7 price discovery](https://degate.com/playbook/tokenized-stocks-24-7-price-discovery/) in the DeGate reference library.

## FAQ

**What does it cost to trade tokenized stocks on DeGate?**
Zero DeGate swap fees on xStocks and Ondo RWA assets, as of July 2026. See [Fees](../fees.md).

**Can I buy tokenized stocks from the EU?**
Yes. DeGate is available in EU and EEA countries. Users are responsible for tax and reporting requirements in their jurisdiction.

**Do I receive dividends?**
Economically yes, via the rebasing mechanism described above; there is no cash payout to claim.

**Can I trade when the stock market is closed?**
You can swap the tokens at any hour. Price behavior outside underlying market hours has its own dynamics; see the pricing section above.
