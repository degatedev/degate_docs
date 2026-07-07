# On-Chain Stocks

DeGate supports holding and swapping tokenized stocks and RWA tokens directly from your self-custody wallet, with zero DeGate swap fees. As of July 2026, coverage spans **Ondo Global Markets onchain stocks** and **100+ xStocks tokens**, covering individual equities (Tesla, Nvidia, Apple, Microsoft and more), index ETFs (S&P 500, Nasdaq 100), and commodities such as gold. All are settled in USDC, fractional, and swappable 24/7.

Browse the full list at [app.degate.com/stocks](https://app.degate.com/stocks).

## Ondo onchain stocks

Ondo Global Markets issues tokens that track listed US equities. The underlying shares are held through regulated intermediaries (Alpaca Securities for the shares, BitGo Bank & Trust for cash and stablecoins) in a bankruptcy-remote issuer structure. Dividends are reflected through total-return pricing: value accrues into the token's price via a multiplier rather than being paid out as cash.

> ⚠️ [NEEDS VERIFICATION: the exact Ondo asset list and chains available on DeGate, before publishing.]

## xStocks (Backed Finance)

xStocks are tokenized equities backed 1:1 by the underlying stock through the Backed Finance framework; the "x" suffix (as in TSLAx) denotes xStocks issuance. Legally, each xStock is a tracker certificate rather than an equity share. Dividends on the underlying equity are reinvested (net of applicable taxes) through a rebasing mechanism: on EVM chains balances adjust automatically, and on Solana adjusted balances are shown via Scaled UI.

## What you can do

* **Swap in and out with zero DeGate fees.** Both Ondo assets and xStocks trade like any other token, from your unified balance, starting on any supported chain. See [Fees](../fees.md).
* **Hold them in self-custody.** Tokens sit at addresses only your key controls.
* **Earn yield on stock tokens.** Provide liquidity to stock pairs (for example TSLAx/USDC or MSTRx/USDC) through [Turbo Range](turbo-range.md).

**To buy:** open the DeGate app, go to **Swap**, search for the token (for example TSLAx for Tesla), enter the amount, and confirm. DeGate handles routing, bridging, and gas automatically.

## What tokenized stocks are, and are not

Tokenized stocks give you economic exposure to the underlying equity; they are not shares held in a securities account in your name, and they do not confer shareholder voting rights. The precise legal form depends on the issuer (a Backed tracker certificate and an Ondo issuer claim are different instruments), so for meaningful size it is worth reading the issuer's own terms. For a plain-language comparison of issuance models, see [What is the tokenized stock in your wallet?](https://degate.com/playbook/tokenized-stock-issuance-models/) in the DeGate reference library.

## Trading hours and pricing

Tokens can be swapped 24/7, since transfers settle on-chain at any hour. The underlying equities trade on exchanges with fixed hours: during US market hours, token prices generally stay close to the underlying through market making and arbitrage; outside those hours, prices form from secondary-market supply and demand, so spreads can be wider and deviations can occur. Full mechanics: [Why 24/7 tokenized stocks do not mean 24/7 price discovery](https://degate.com/playbook/tokenized-stocks-24-7-price-discovery/).

## FAQ

**What does it cost to trade tokenized stocks on DeGate?**
Zero DeGate swap fees on xStocks and Ondo RWA assets, as of July 2026.

**Do I receive dividends?**
Economically yes, through each issuer's mechanism: xStocks rebase balances, while Ondo reflects dividends in the token price. Neither pays cash to your wallet. Details: [How tokenized stock dividends work](https://degate.com/playbook/tokenized-stock-dividends-mechanisms/).

**Can I buy tokenized stocks from the EU?**
Yes. DeGate is available in EU and EEA countries. Users are responsible for tax and reporting requirements in their jurisdiction.

**Are tokenized stocks available everywhere?**
No. xStocks follow the issuer's restrictions: users in regions on Backed's [restricted countries list](https://assets.backed.fi/legal-documentation/restricted-countries) (including the United States) cannot trade xStocks tokens on DeGate. This restriction applies to the Backed-issued tokens, not to your other assets.

**Can I trade when the stock market is closed?**
You can swap the tokens at any hour. Price behavior outside underlying market hours has its own dynamics; see the pricing section above.
