# On-Chain Stocks

Use **Stocks** in the DeGate mobile app to find supported stock and ETF tokens from **Ondo onchain assets** (tickers ending in "on", like TSLAon) and **xStocks** (tickers ending in "x", like TSLAx), together covering individual US equities (Tesla, Nvidia, Apple, Microsoft and more) and index ETFs (S&P 500, Nasdaq 100). **Trade** also provides quotes for **Coinbase Tokenized Stocks on Base** and **Robinhood Stock Tokens on Robinhood Chain**. Select the exact token and amount to request a quote. Execution depends on an available route and quote. Ordinary stock-token swaps have a 0.02% DeGate platform fee, as of August 2026.

Browse the [stock token list](https://degate.com/en/stocks).

## Ondo onchain assets

Ondo Global Markets issues tokens that track listed US stocks and ETFs; in the app these carry the "on" ticker suffix (TSLAon for Tesla). The underlying shares are held through regulated intermediaries (Alpaca Securities for the shares, BitGo Bank & Trust for cash and stablecoins) in a bankruptcy-remote issuer structure. Dividends are reflected through total-return pricing: value accrues into the token's price via a multiplier rather than being paid out as cash.

For an eligible Ondo order, a solver partner integrated with DeGate can send a Request for Quote (RFQ) through **Ondo's official API** when that route is available. The quote refers to the price and available liquidity of the corresponding stock in the traditional US market, so the order does not have to rely solely on one on-chain pool. Quote availability and executable amounts depend on the asset, market session, and order size. See [How to check a tokenized-stock quote](https://degate.com/guides/stocks/how-to-check-a-tokenized-stock-quote-before-you-buy/) for the distinction between a display price and a trade quote.

## xStocks (Backed Finance)

xStocks are tokenized equities backed 1:1 by the underlying stock through the Backed Finance framework; the "x" suffix (as in TSLAx) denotes xStocks issuance. Legally, each xStock is a tracker certificate rather than an equity share. Dividends on the underlying equity are reinvested (net of applicable taxes) through a rebasing mechanism: on EVM chains balances adjust automatically, and on Solana adjusted balances are shown via Scaled UI.

## What you can do

* **Trade against USDC.** Ordinary stock-token swaps have a 0.02% DeGate platform fee, as of August 2026. See [Fees](../fees.md).
* **Hold tokens in your wallet.** Check the selected wallet, token contract, and network before receiving or trading.
* **Provide stock liquidity.** In [Turbo Range](turbo-range.md), you can open new positions in available Ondo stock/USDC pools on Ethereum. Earlier xStocks positions remain in **My Positions**; new xStocks LP positions are not currently available in Turbo Range.
* **Pair two stock tokens.** In [Power Pair](power-pair.md), choose two supported Ondo stock tokens and provide liquidity within a range based on their relative price. You can earn a share of trading fees when swaps use your liquidity.

**To buy:** find a supported token in **Stocks**, or search for the exact token in **Trade**. Enter the amount to request a quote in **Trade**. Review the quote, network, and fees before confirming. Routing is included in the trade flow. Supported hardware-wallet trades in the DeGate app use Action Wallet. For each transfer your hardware wallet sends to Action Wallet, including gas top-ups, your hardware-wallet address pays gas in that network’s native token. Action Wallet covers the remaining network fees from its own gas balance. See [Fees](../fees.md).

## What tokenized stocks are, and are not

Tokenized stocks give you economic exposure to the underlying equity; they are not shares held in a securities account in your name, and they do not confer shareholder voting rights. The precise legal form depends on the issuer (a Backed tracker certificate and an Ondo issuer claim are different instruments), so before trading, read the issuer's own terms. For a plain-language comparison of issuance models, see [What is the tokenized stock in your wallet?](https://degate.com/playbook/tokenized-stock-issuance-models/) in the DeGate reference library.

## Trading hours and pricing

On-chain transfers do not follow stock-exchange opening hours, but a transfer being possible does not guarantee an executable trade quote. Check the live quote in Trade. The underlying equities trade on exchanges with fixed hours: during US market hours, token prices generally stay close to the underlying through market making and arbitrage; outside those hours, pricing and liquidity vary by token. Some tokens still have request-for-quote (RFQ) pricing. Some on-chain pools may continue trading outside those hours. Automatic swaps for Turbo Range and Power Pair deposits require their own RFQ quotes. Spreads and slippage can be higher, so review the live quote and expected output before confirming. Full mechanics: [Why 24/7 tokenized stocks do not mean 24/7 price discovery](https://degate.com/playbook/tokenized-stocks-24-7-price-discovery/).

## FAQ

**What does it cost to trade tokenized stocks on DeGate?**
Ordinary swaps of Ondo stock tokens and xStocks have a 0.02% DeGate platform fee, as of August 2026. As of 19 November 2026, automatic swaps in Turbo Range and Power Pair have a 0% DeGate platform swap fee. Network costs and pool trading fees may still apply. See [Fees](../fees.md).

**Do I receive dividends?**
Economically yes, through each issuer's mechanism: xStocks rebase balances, while Ondo reflects dividends in the token price. Neither pays cash to your wallet. Details: [How tokenized stock dividends work](https://degate.com/playbook/tokenized-stock-dividends-mechanisms/).

**Can I buy tokenized stocks from the EU?**
The app is available in EU and EEA countries. Token eligibility and third-party terms can vary by issuer and region. Check those terms and your local tax and reporting obligations before trading.

**Can I trade when the stock market is closed?**
Check Trade for an executable quote. On-chain transfers can occur outside stock-market hours, but issuer routes and liquidity may be limited. See the pricing section above.
