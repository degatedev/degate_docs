# Liquidity Mining

DeGate’s liquidity mining program is designed to incentivize users who contribute effective liquidity to the order book. Effective liquidity refers to grid strategy orders placed in the vicinity of the highest buying price or the lowest selling price in the order book.

### Mining Pool

Liquidity mining on DeGate is conducted based on trading pairs. A mining pool refers to a trading pair where mining is ongoing or about to begin. The node operator is responsible for setting up a mining pool. Users can query information about mining pools on the mining page. The life cycle of a mining pool may consist of multiple stages, and the duration of each stage and corresponding rewards may differ.

### How To Start Mining

To begin mining on DeGate, all of the following requirements must be met:

1. **Order type**: Only grid strategy orders are eligible for mining, and ordinary orders do not qualify.&#x20;
2. **Order value**: Whether a grid order meets the order value conditions for mining is determined at the time of grid strategy creation. Users can preview whether each grid order meets this criterion.
3. **Order price**: To incentivize users to contribute effective liquidity, the DeGate protocol makes a judgment every 15 seconds and allocates mining rewards to orders within the required price range and meeting the aforementioned conditions.&#x20;

{% hint style="info" %}
_Note: The minimum mining order amount per grid is $25_
{% endhint %}

While the first two conditions are static and determined when a grid strategy is created, the third condition is dynamic, excluding some grid orders from receiving mining rewards. Grid strategies with the same initial allocation may receive different mining rewards if they have different price ranges and numbers of grids.

**In addition, if a grid strategy is created earlier than a mining pool starts, such strategy can automatically be involved in mining once it starts. Users do not need to cancel an existing grid strategy and create a new one.**

### Rewardable Price Range

The rewardable price range changes in real-time based on the status of the order book. Depending on the type of trading pair, the rules are as follows:

1. Regular trading pairs: the highest buying price in the order book \* 0.99 \~ the lowest selling price in the order book \* 1.01
2. Stable trading pairs: the highest buying price in the order book \~ the lowest selling price in the order book

Stable trading pairs, such as USDT/USDC, have less price fluctuations, and are thus subject to more demanding rewardable price range requirements.&#x20;

### Rewards Calculation and Allocation

Rewards are calculated every 15 seconds. All the qualified orders in the same mining pool share the rewards proportional to their value to be filled. Users need to claim their rewards after allocation.

**Examples of Rewards Calculation**

> 1. Your ETH/USDC grid strategy has met the order value requirements at the time of creation;&#x20;
> 2. Assuming that the highest buying price in the order book is 1495, and the lowest selling price is 1502 at a certain moment, the rewardable price range is 1480.05 to 1517.02. You have a grid order to sell 1 ETH at $1510, which falls within the rewardable price range.
> 3. Based on the ETH[ risk price,](../concepts/economic-security.md#risk-price) your order value is 1\*1495=$1495;
> 4. The total value of all the qualified ETH/USDC grid orders at that moment amounts to $42391;
> 5. The total rewards at that moment are 10 DG
> 6. Therefore, the yields you will receive are 1495 / 42391 \* 10 = 0.35266919 DG

### Grid Strategy Duration

To prevent users from frequently creating and canceling grid strategies solely for mining yields, a requirement for grid strategies’ duration has been added. All the allocated rewards are initially "temporarily unclaimable" and only become "claimable"  after the duration expires. If a user cancels a strategy before the duration expires, they will lose their temporarily unclaimable rewards, which will return to the mining pool.

To participate in ongoing mining programs, users must create a grid strategy earlier than a specific time point before mining closes, which is typically related to the strategy duration requirement.

> For instance, if a mining program closes at 2200hrs on October 30, 2022, and the strategy duration requirement is 12hrs, users must create a grid strategy no later than 1000hrs on October 30, 2022 to participating in mining.



### Claiming Mining Rewards

Users can retrieve the "claimable" mining rewards at any point in time. Each time they claim, they must pay the gas fees. After a claim is successfully processed, the rewards will be immediately transferred to the user's DeGate account.

### Mining Statistics

Users can also view their own mining statistics, including the latest value of their invested funds, latest earnings, and which grid strategies are currently being used for mining. They can click on a specific grid strategy for more detailed data, such as mining yields and sources of rewards, etc.

{% hint style="info" %}
Mining Yields and Mining Pool’s Yields

* Mining yields calculate the total mining income of individual users. Each grid strategy is calculated independently based on a combination of the total mining yields, initial investment value and mining duration. Generally speaking, mining yields are relatively high at the beginning, and gradually decrease as the mining duration increases.
* How to calculate mining duration: mining duration is defined as the overlapping portion between the duration of a user's grid strategy and that of the corresponding mining pool. This parameter is not displayed in the mining statistics and users need to do calculations themselves.&#x20;
* A mining pool’s yields are calculated based on the value of daily rewards and the total funds invested by all the users into the mining pool. The mining pool’s yield represent an estimate of future earnings and is provided for reference only.
* The mining pool funds only count in the grid strategy orders that meet the “order value requirements", without considering whether the orders meet the "price requirements", so mining pool's yields are generally lower than individual's mining return.&#x20;
{% endhint %}

### Project Collaboration

The DeGate liquidity mining program supports the distribution of rewards in multiple tokens. We invite other projects to collaborate with us to customize mining pools.
