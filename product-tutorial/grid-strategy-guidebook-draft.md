# Grid Strategy Guidebook \[Draft]

Grid Strategy or grid trading is a powerful trading tool that automates buying and selling within a defined range. A grid strategy automatically places _buy_ orders when prices drop and _sell_ orders when they rise, allowing you to capitalize on market fluctuations and generate profits. &#x20;

### How to set up Grid Strategy on DeGate?&#x20;

Let's use the guided example below.

First, head to [DeGate DEX](https://app.degate.com/) -> select "[Grid Strategy](https://app.degate.com/grid/USDC/ETH)" -> enter your desired trading pair such as ETH/USDC.

<figure><img src="../.gitbook/assets/Screenshot 2024-02-02 at 4.06.19 PM.png" alt=""><figcaption></figcaption></figure>

#### **Select Grid Strategy mode**

There are 2 Grid Strategy modes to choose from.

**Auto:** Set up Grid Strategy using auto-generated parameters recommended by the system, based on technical analysis and historical data

**Manual:** Customize Grid Strategy parameters to match your preferences&#x20;

{% hint style="info" %}
For newcomers to Grid Strategy, it is recommended to start with \[Auto] mode.
{% endhint %}

<figure><img src="../.gitbook/assets/Screenshot 2024-02-02 at 4.29.57 PM.png" alt=""><figcaption></figcaption></figure>

#### **Set up Grid Strategy \[AUTO]**

1. Click on the \[Auto] tab
2. Enter the amount to allocate for Grid Strategy \[ETH/USDC].  For example, once you input the ETH amount, the system will auto-calculate the required USDC for the Grid Strategy, and vice versa.

{% hint style="info" %}
Do ensure you have sufficient ETH and USDC in your DeGate balance.&#x20;
{% endhint %}

<figure><img src="../.gitbook/assets/Screenshot 2024-02-02 at 4.40.02 PM (2).png" alt=""><figcaption></figcaption></figure>

3. Once you have en

<figure><img src="../.gitbook/assets/Screenshot 2024-02-02 at 4.40.32 PM (1).png" alt=""><figcaption></figcaption></figure>



You can customize the parameters of your grid strategy according to your preferences, including the Price Range, Initial Allocation, Number of Grids, Quantity per Grid, and Duration.

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/截屏2023-12-13 14.30.47.png" alt=""><figcaption></figcaption></figure>

Of course, you can also choose "Auto" to directly create a grid strategy using the price range and parameters provided by the system

Let's assume that the ETH price is 1303 USDC. Let's choose the ETH/USDC trading pair to create a grid.&#x20;

* Enter price range. In this example we will set a grid in the range of 1200 - 1400 USDC

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

* Enter Initial Allocation (the total amount you want to invest). In this example, we'll allocate 97 ETH, the system will calculate the corresponding USDC amount.

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

* Set grid density: let's set the number of grids to 200, the system will automatically calculate the quantity per grid.

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

After successfully creating the grid strategy, the DeGate system will set multiple buy and sell limit orders within the price range.

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

The grid robot will continuously buy low and sell high within the set price range to automatically generate profits, as illustrated in the diagram below:

<figure><img src="../.gitbook/assets/Grid-Trading-Short-35s-v27 (1).gif" alt=""><figcaption></figcaption></figure>

After completing one buy low and sell high cycle, you will profit 1 USDC.

**Note:**

For each grid strategy, in this case the ETH/USDC grid strategy example above, please ensure that the current market price is within the range you set (1200-1400), otherwise, the grid strategy will no longer generate profits.
