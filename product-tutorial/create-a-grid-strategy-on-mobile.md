# Create a Grid Strategy on Mobile

The Grid Strategy is a powerful tool that allows users automatically buy and sell between a token pair within a set price range, taking advantage of price fluctuations. If done right, grid strategy is one of the most powerful ways to earn profit by repeatedly buying low and selling high. Follow the step-by-step guide below to start grid trading on DeGate.

## How to create a Grid Strategy on DeGate

### 1. Click **\[**Grid]- \[Create Grid Strategy]

<figure><img src="../.gitbook/assets/image (7) (1).png" alt=""><figcaption></figcaption></figure>

### 2. At the top of the screen, search and select which trading pair you want  to set up a grid for, e.g. ETH/USDC

<figure><img src="../.gitbook/assets/image (29).png" alt=""><figcaption></figcaption></figure>

### 3. Select **\[Auto]** or **\[Manual]** to set up Grid Strategy parameters.

#### Auto Mode

The Auto mode will automatically populate the grid parameter fields. You will only need to input the **`Initial Allocation`** field.

You also have the option to use the Auto Mode to obtain initial recommended parameters. You can then click on **\[Copy parameters to Manual]** to pre-fill those parameters in Manual Mode and adjust them according to your needs.



<figure><img src="../.gitbook/assets/mobile_parameters.gif" alt=""><figcaption></figcaption></figure>

#### Manual Mode

In manual mode, you can customize the grid strategy parameters according to your preferences, including **`Price Range`**, **`Initial Allocation`**,**`Number of Grids`** , **`Quantity per Grid`** and **`Expire in`**.

#### How to setup Grid Strategy parameters?

1. **Price range**: This refers to the lowest and the highest prices you want to trade within. No grid orders will exceed the range. Picking a sensible price range that is not too wide, that you believe the market price will fluctuate within for as long as possible will lead to stable returns.&#x20;
2. **Initial allocation**: This is the initial funds locked to run a strategy.&#x20;
3. **Number of grids**: This is the number of grid orders running simultaneously within your grid strategy. The minimum number of grid orders is 2, and the maximum is 255.
4. **Quantity per grid**: This is the quantity to be bought or sold per grid order, which is the same for all grid orders. In the mobile version, this parameter cannot be directly configured; it is automatically calculated through other parameters.
5. **Grid Width**: This is an important parameter that determines a grid strategy's profitability. Grid Width = (Sell Price - Buy Price) / Sell Price. The increase in grid width can enhance the profit from each "low buy" and "high sell", but it can also decrease the number of orders executed during price fluctuations.
6. **Expire in**: The grid strategy automatically expires when the validity period elapses, and grid orders are automatically cancelled. The default validity period is 180 days, and the maximum is 365 days. Click "Advanced" to proceed with the configuration.

For convenience, the system will automatically populate the upper and lower limits based on the current latest price. You can modify it according to your needs.

<figure><img src="../.gitbook/assets/image (30).png" alt=""><figcaption></figcaption></figure>

Once all the parameters are set, if you modify any value, the other values will automatically adjust accordingly. By checking the **\[Preview Orders]** checkbox, you can preview the each grid orders. If the parameters do not meet the conditions for creating a grid, a red warning popup notice will appear when clicking 'Create Grid Strategy.' Please note that the quantity per grid needs be greater than the equivalent of $100.



### 4. Create Grid Strategy

Once you confirm the parameters, click the **\[Create Grid Strategy]** button. In the popup that appears, review the parameters again and click **\[Confirm]** to successfully create the grid strategy.&#x20;

After successful creation, the grid details will be displayed directly, including the status of the grid strategy and providing information on profit, orders, and trade history.  Click on **\[Summary]** to access more info.

You can reopen the details popup by accessing the corresponding strategy's action in the **\[Grid]** at the bottom of the interface.

<figure><img src="../.gitbook/assets/mobile_create_en.gif" alt=""><figcaption></figcaption></figure>

## Cancel a Grid Strategy&#x20;

You can access and view the running grid strategies by entering the **\[Grid]** at the bottom of the interface. click to enter the strategy you want to close. Click on the cancel icon button, confirm, and the selected grid strategy will be closed.

Once closed, you can review it again in **\[Grid]** - **\[History]** - **\[Completed]** at the bottom or in the **\[History]**  at the top right corner of screen. You can view the details of the closed grid strategy here and copy the parameters of the closed grid for easy creation of a new grid.

![](<../.gitbook/assets/image (31).png>)![](<../.gitbook/assets/image (32).png>)

## Understanding the principles behind Grid Strategy

Please see the links for a concise overview of the grid strategy's principles and technical implementation.

[https://docs.degate.com/v/product\_en/main-features/grid-strategy](https://docs.degate.com/v/product\_en/main-features/grid-strategy)\
[https://docs.degate.com/advanced/decentralized-grid-strategy](https://docs.degate.com/advanced/decentralized-grid-strategy)
