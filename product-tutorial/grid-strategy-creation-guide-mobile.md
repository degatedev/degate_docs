# Grid Strategy Creation Guide （Mobile）

Grid strategy is a powerful tool that can capitalize on market fluctuations within a predetermined price range. A grid strategy sets multiple buy and sell orders to automatically buy low and sell high for profit.

### How to create a Grid Strategy on DeGate？

Let's work through a guided example below.

First, open [DeGate DEX](https://app.degate.com/) with an Ethereum wallet, click on "**Grid**" at the bottom of the page, then choose to "**Create Grid Strategy**".

<figure><img src="../.gitbook/assets/WechatIMG722.jpeg" alt="" width="375"><figcaption></figcaption></figure>

**Create a Grid  Strategy**

You can search and select the trading pair you want to trade at the top of the page, such as ETH/USDC.&#x20;

Then, customize the parameters of your grid strategy according to your preferences, including the Price Range, Initial Allocation, Number of Grids, Quantity per Grid, and Duration."

<figure><img src="../.gitbook/assets/截屏2023-12-18 20.03.43.png" alt=""><figcaption></figcaption></figure>

Let's assume that the ETH price is 1303 USDC. Let's choose the ETH/USDC trading pair to create a grid.&#x20;

* Enter price range. In this example we will set a grid in the range of 1200 - 1400 USDC

<figure><img src="../.gitbook/assets/截屏2023-12-13 14.50.11.png" alt=""><figcaption></figcaption></figure>

* Enter Initial Allocation (the total amount you want to invest). In this example, we'll allocate 97 ETH, the system will automatically calculate the equivalent amount in USDC

<figure><img src="../.gitbook/assets/截屏2023-12-13 14.52.01.png" alt=""><figcaption></figcaption></figure>

* Set grid density: let's set the number of grids to 200, the system will automatically calculate the quantity per grid.

<figure><img src="../.gitbook/assets/截屏2023-12-13 14.52.18.png" alt=""><figcaption></figcaption></figure>

After successfully creating the grid strategy, the DeGate system will set multiple buy and sell limit orders within the price range.

<figure><img src="../.gitbook/assets/WechatIMG743.jpeg" alt=""><figcaption></figcaption></figure>

The grid robot will continuously buy low and sell high within the set price range to automatically generate profits, as illustrated in the diagram below:

<figure><img src="../.gitbook/assets/Normal-Grid-EN-v2m (1).gif" alt=""><figcaption></figcaption></figure>

After completing one buy low and sell high cycle, you will profit 1 USDC.



Note:

For each grid strategy, in this case the ETH/USDC grid strategy example above, please ensure that the current market price is within the range you set (1200-1400), otherwise, the grid strategy will no longer generate profits.
