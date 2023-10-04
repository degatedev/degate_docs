# Trading Pairs

Trading pairs consist of a base token and a quote token, denoted as **base token/quote token**, such as ETH/USDC. A base token and a quote token form a unique trading pair, each corresponding to a separate order book. The DeGate node maintains trading pairs’ information. The DeGate protocol currently does not support switching the order of trading pairs, for example ETH/USDC cannot be reshuffled to USDC/ETH. Moreover, for safety and practical reasons, the range of quote tokens is restricted.

### The Process of Adding Trading Pairs

Users can add trading pairs on degate.com or using SDK. When adding a new trading pair, users are required to specify the base token and choose a quote token from ETH, USDC, and USDT. To maintain the economic security of the protocol, users must pay a small amount of gas fees from their DeGate account to add a trading pair. Once the payment is completed, the trading pair is added instantly, and users can start placing orders and trading.

### Quote Token Constraints

Order books’ trading pairs are similar to AMM’s trading pool, with some differences. For example:&#x20;

1. **Sequence:** trading pairs have a sequence, but trading pools do not.&#x20;
2. **Liquidity:** trading pairs do not share liquidity. However, the same tokens across trading pools do share liquidity via transaction routing.

Order book transactions originate from traditional finance where fiat is used as the quote currency. However, in the crypto world, in addition to USD-pegged stable coins, BTC and ETH are also commonly used as quote tokens. After comprehensive considerations, the node operator has decided to **limit the quote tokens currently to ETH, USDC and USDT**, which can satisfy the majority of order book transaction needs.

### Trading Pairs Types

There are two types of trading pairs, affecting the price precision level of both the order book and orders.&#x20;

1. **Regular trading pairs:** The vast majority of trading pairs fall into this category.
2. **Stable trading pairs:** stable coin-based trading pairs such as USDT/USDC and trading pairs formed by collaterals and their underlying assets such as stETH/ETH are called stable trading pairs. They have relatively small price fluctuations within a certain range

Newly added trading pairs are regular trading pairs by default, and the node operator may recategorize them as stable pairs when conditions are appropriate.&#x20;

### Querying Trading Pairs

As multiple tokens can have the same name, it is important to check the tokens’ contract address when querying a transaction pair. Trading pairs containing a default token will be accompanied by its icon on the DeGate website. The icon of a trading pair containing non-default tokens is represented by ? and a risk warning will appear on the trading page. Additionally, an abbreviated contract address will be displayed under _token info._

### Favorite Trading Pairs

Degate.com allows users to maintain a list of favorite trading pairs, whose information is stored locally in the browser without any synchronization mechanism. In other words, users must create and maintain their favorite list again if they switch to a different device.&#x20;
