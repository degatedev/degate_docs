# Copy Trade

> ⚠️ DRAFT, publish-gated. [NEEDS VERIFICATION: two things before this page goes live. (1) Custody model of the Copy Trade account: who holds its key, and how that squares with the wallet's non-custodial claims; the answer shapes the wording of this entire page. (2) What Copy Trade costs the user (any DeGate fee on bot trades). Also confirm with marketing whether Copy Trade should appear in docs at all.]

Copy Trade automates meme-token trading on Solana. Instead of watching charts, you create a bot that either copies the trades of top-performing wallets in real time or follows curated trade signals, using a fixed SOL amount per trade.

## Two ways to copy

* **Smart Wallets:** copy the trades of top meme wallets, ranked by 7-day APY.
* **Smart Signals:** follow curated signal feeds designed to catch meme trends early.

## How a bot works

1. Fund your Copy Trade account with SOL, either by internal transfer from your DeGate balance or by direct deposit from an exchange or another wallet.
2. Create a bot: pick a wallet or signal to copy, set the fixed SOL amount per trade, and choose a sell strategy. A stop-loss of -60% is set by default; buy and sell parameters can be adjusted in advanced settings.
3. The bot buys and sells automatically. You can track running bots, activity, and holdings, and close a bot at any time; your tokens remain in your Copy Trade account, and you can transfer funds back out whenever you like.

## Risk, stated plainly

Memecoins are among the most volatile assets in crypto, and an automated bot will execute trades without asking you first. Default settings are tuned for win rate, not for capital preservation. Only allocate an amount you can afford to lose entirely.

## FAQ

**Which chains does Copy Trade support?**
Solana. The Copy Trade account is funded and settled in SOL.

**Can I stop a bot at any time?**
Yes. Closing a bot cancels its pending orders; your tokens stay in your Copy Trade account until you transfer them out.
