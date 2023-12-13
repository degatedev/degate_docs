# Grid Strategy

Grid strategy is a trading technique that allows users to set a price range for automatic order placement and make a profit by selling high and buying low. The DeGate protocol currently supports neutral arithmetic grid strategies which require users to prepare the two tokens of a trading pair. In this strategy, the grids’ price difference is distributed in an arithmetic sequence.

### Trading Mechanism

Similar to order-book trading, the funds used to create a DeGate grid strategy are also under the custody of users. Grid strategies are created following the steps below:

1. A user sets the parameters of a grid strategy. Upon the user’s confirmation, a grid strategy containing the user-set parameters is automatically generated with the user’s signature with their Asset Private Key. These parameters define how to place grid orders. A grid strategy contains at least two grid orders.
2. The DeGate node receives and verifies the user's signature. After verification, it places initial grid orders based on the content of the signature. It should be noted that in a neutral strategy, all initial grid orders must be Maker orders, otherwise the strategy will fail.
3. Whenever a grid order is matched, the circuit verifies that the match complies with the user's signed authorization.
4. When a grid order is completely filled, the DeGate node derives a new grid order based on the user's pre-authorized signature. For instance, when a buy order is filled, a sell order of the same quantity is placed at a higher price. When a sell order is entirely filled, a buy order of the same amount is placed at a lower price, thus achieving automatic trading.
5. The net capital difference between the repeated transactions and order placements in a grid strategy is a type of market-making income, which is credited directly into the available balance and is not locked.

### Grid Strategy Parameters

The following parameters are required for a grid strategy:

1. Price range: It comprises the lowest and the highest prices, representing the operational range of the grid strategy. No grid orders will exceed the range.
2. Initial allocation: This is the initial funds locked to run a strategy. Quote tokens are required for buy orders, while base tokens are required for sell orders.
3. Number of grids: This is the number of grid orders running simultaneously, irrespective of buying or selling. The minimum number of grids is 2, and the maximum is 255.
4. Quantity per grid: This is the quantity to be bought or sold per grid order, which is the same for all grid orders.
5. Grid Width: It is an important parameter that determines a grid strategy's profitability. Grid Width = (Sell Price - Buy Price) / Sell Price.
6. Expiration: The grid strategy automatically expires when the validity period elapses, and grid orders are automatically cancelled. The default validity period is 180 days, and the maximum is 365 days.

### Creation Method

DeGate offers two modes for creating a grid strategy: auto and manual. In the auto mode, parameters are automatically filled based on such information as recent transactions of the trading pair, available account balance and minimum order value requirements. Users can only adjust initial allocation. In the manual mode, users can modify all parameters. If parameters are the same, the strategies created under the two modes are identical with no difference.

### Previewing a Grid Strategy

Users can preview the distribution of all grid orders in the chart after they have configured the parameters but before a strategy is created.

### Grid Strategy Details

After a strategy is created, users can view details such as strategy parameters, open grid orders, and completed orders. Users can also adjust the strategy, such as canceling the strategy, copying the strategy, or having a graphical display of the strategy.

### Cancelling a Grid Strategy

Users can cancel a running grid strategy at any time, which will lead to the cancellations of all open grid orders and unfreeze the locked funds immediately. Users can also proceed to cancel the strategy on-chain after doing so off-chain. This operation incurs Gas fees which increase proportionally to the number of grid orders.

### Copying a Grid Strategy

Users can copy a closed strategy by replicating all its parameters to quickly create a new strategy.

### Graphical Display

Users can also get a visual representation of a running strategy, and view grid orders and recent fills in the chart.

### Liquidity Mining

After the DeGate liquidity mining program starts, users participate in mining with a grid strategy. For more information, please refer to:[ liquidity mining](grid-strategy.md#liquidity-mining)
