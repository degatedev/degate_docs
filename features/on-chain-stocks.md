# On-Chain Stocks

DeGate supports holding and swapping tokenized stocks: crypto tokens that track the price of listed equities. As of July 2026, this covers xStocks tokens on Solana, which trade on DeGate with zero DeGate swap fees.

## What you can do

* **Swap into and out of xStocks** the same way as any other token, from your unified balance, starting on any supported chain. DeGate's swap fee for xStocks on Solana is 0% (see [Fees](../fees.md)).
* **Hold them in self-custody.** xStocks in your DeGate wallet sit at addresses only your key controls, like any other token.
* **Provide liquidity on xStocks pairs** through [Turbo Range](turbo-range.md).

## What tokenized stocks are, and are not

xStocks are tokens issued by a third-party issuer, not by DeGate; each token is designed to track the price of a specific listed equity.

> ⚠️ [NEEDS VERIFICATION: current issuer naming and one-line description of the xStocks issuance structure, consistent with the on-chain-stocks research already done for the playbook.]

Two distinctions worth understanding before you buy:

* Holding a stock token is not the same as holding the share in a securities account. The token tracks the price; shareholder mechanics such as voting differ by issuer structure.
* Tokens transfer on-chain around the clock, but the underlying stock markets have opening hours. Price behavior outside market hours has its own dynamics; see the explainer [Why 24/7 tokenized stocks do not mean 24/7 price discovery](https://degate.com/playbook/tokenized-stocks-24-7-price-discovery/) in the DeGate reference library.

## FAQ

**Can I trade tokenized stocks 24/7 on DeGate?**
You can swap the tokens whenever you like, since token transfers settle on-chain at any hour. Keep in mind the underlying equities trade on exchanges with fixed hours, which affects how token prices form outside those hours.

**Does DeGate charge fees on xStocks swaps?**
No DeGate swap fee on xStocks tokens on Solana, as of July 2026. Standard network costs still apply. See [Fees](../fees.md).

**Which stocks are available?**

> ⚠️ [NEEDS VERIFICATION: whether to link a live in-app list or maintain a snapshot list here.]
