# Economic Security

## Free Quota for Paid Deposits

Each deposit incurs certain fees as it requires zero-knowledge proof. Currently, the node operator subsidizes deposit fees, so users do not need to pay for deposits. To prevent attacks on the protocol, both standard and advanced deposits are limited by a maximum number of free deposits, which decreases with each successful deposit and increases linearly over time. Standard deposit parameters are configured in the node, and advanced deposit parameters are configured in the DeGate smart contract.&#x20;

After a standard deposit transaction is confirmed on-chain, the DeGate node will first check the remaining number of free deposits. If the limit has been reached, the node will suspend crediting the deposit amount to the user’s DeGate account until after the user has paid a deposit processing fee. Advanced deposit processes are slightly different in that users must pay not only the gas fees due for the transaction, but also an additional deposit processing fee when calling the smart contract. Otherwise the transaction may fail. All deposit processing fees can only be paid in ETH.&#x20;

## **Token Parameters Configuration**&#x20;

All centralized exchanges rely on people to manage tokens and the listing of trading pairs. Controlling the token listing process is a standard operating process in most centralised exchanges. In DeGate, these features are permissionless. Anyone can register and deposit any ERC20 tokens, add trading pairs and place orders. Assets are automatically added to the global token list upon registration.&#x20;

The permissionless token listing mechanism also leads to some potential problems, such as fake tokens, tokens with a transfer-to-burn mechanism, and non-standard ERC20 tokens with a supply rebase mechanism, affecting DeGate’s normal use. Attackers may also manipulate prices to attack the DeGate protocol. Therefore, the DeGate node operator has added additional parameter configurations to the global token list to avoid the above problems.&#x20;

## Default Token List

The node operator provides a default token list where the icons, symbols and contract addresses of the tokens have passed our consistency verification and are consistent with the data on coinmarketcap, tokenlists and other websites. Users can trade such assets with assurance that they are not fake. The node operator will regularly update the configuration of the default token list to incorporate mainstream and commonly seen tokens. The quote tokens of trading pairs are default, including ETH, USDC and USDT.&#x20;

The tokens listed on DeGate in a permissionless way will not be automatically added the to default list. Users will see risk warnings when trading these tokens.&#x20;

The differences between the two are listed in the table:&#x20;

| Function                                     | Default Token List | Other Tokens       |
| -------------------------------------------- | ------------------ | ------------------ |
| Token Icon                                   | Yes                | Question Mark Icon |
| Abbreviated Smart Contract Address           | No                 | Yes                |
| Trading Risk Warning                         | No                 | Yes                |
| Asset with 0 Balance Displayed in Asset List | Yes                | No                 |
| Verification Status                          | Verified           | Not Verified       |



{% hint style="warning" %}
How to distinguish between default and non-default tokens?
{% endhint %}

The distinction is mainly made through icons and contract addresses, as illustrated below. The token displayed Figure 1 is fake, and the one in Figure 2 is authentic.

<figure><img src="../.gitbook/assets/Screen Shot 2022-11-29 at 09.21.43 (2).png" alt=""><figcaption><p>Figure 1: Non-Default Token</p></figcaption></figure>

<figure><img src="../.gitbook/assets/Screen Shot 2022-11-29 at 09.21.30.png" alt=""><figcaption><p>Figure 2: Default Token</p></figcaption></figure>

## Actively and Inactively Traded Tokens

As DeGate allows for permissionless token listing and trading. Without a minimum order value requirement, the transaction costs will increase and it will be more vulnerable to attacks. So in DeGate, orders must meet a minimum value threshold, which is higher than that of centralized exchanges. To lower the minimum value requirement,  we have added actively traded tokens with a lower value threshold for trading. The[ order values ](economic-security.md#minimum-order-size)of actively and inactively traded tokens are calculated differently.

## Supported Tokens for Standard Deposits

DeGate offers a standard deposit method that saves gas fees. Given the potential trustlessness issue this method may lead to, not all assets can be deposited this way. Generally speaking, all the default tokens support standard deposits.

## Quote Tokens of Trading Pairs

A trading pair consists of a base token and a quote token. For example, in the ETH/USDC pair, ETH is the base token and USDC is the quote token. The DeGate protocol allows users to register any tokens. Nevertheless, except for ETH, USDC, and USDT, others can only as base tokens. In the future, the DeGate HomeDAO may add new quote tokens. \


The gas fee involved in transactions must be paid in the quote token.&#x20;

> For example: ETH/USDC&#x20;
>
> * Buying ETH: users must have USDC to proceed with the trading and pay the gas fee with the USDC in their account.&#x20;
> * Selling ETH: users are not required to have USDC prior to the transaction and can use the USDC in their account balance plus whatever USDC they obtain from the transaction to pay the Gas fee.&#x20;

{% hint style="danger" %}
**Assuming any two tokens can form a trading pair:**

An attacker deploys new tokens XXX and YYY to form a trading pair. They pay worthless XXX and YYY to complete transactions. However, the DeGate protocol still has to pay the Gas fees for rollup in ETH and thereby suffer losses.
{% endhint %}

{% hint style="danger" %}
**If a base token can be used to pay the Gas fee:**

An attacker deploys a new token XXX and creates a trading pair XXX/USDC. They can transacts with themselves as the Maker in sell orders and Taker in buy orders. They only pay Gas fees and transaction handling fees in XXX. The DeGate protocol receives worthless XXX, yet pays for the rollup transaction in ETH, thereby suffering losses.
{% endhint %}

## Risk Price

Currently, one base token can form trading pairs with 3 quote tokens, namely XXX/ETH, XXX/USDC, and XXX/USDT. The DeGate protocol has designed 3 price types:

* Risk price: A token has only one risk price, calculated based on the transaction data of all the trading pairs of the token.
* Real-time price: A token has only one real-time price, calculated based on the transaction data of all the trading pairs of the token.
* Latest price: Each trading pair has a latest price, which is the price from the latest transaction.&#x20;

Risk price is the most important as it is used to calculate the value of an order to determine whether the order can be successfully placed. Real-time prices are used for statistics. The latest price is displayed on the trading page.

**Price Calculation:**

1. For any token XXX. Based on the historical data of all its trading pairs, we do hourly calculation to select a trading pair P with the largest average transaction value over a certain period of time;
2. The average price of P becomes XXX’ risk price;
3. The latest price of P becomes the real-time price of XXX.&#x20;

<figure><img src="../.gitbook/assets/Screen Shot 2022-12-09 at 16.29.25.png" alt=""><figcaption><p>Calculation of the Risk and Real-Time Prices</p></figcaption></figure>

## Minimum Order Size

The minimum order value is used to determine whether an order can be successfully placed. It is set by the node operator and currently stands at $100. It will be adjusted based on the Ethereum network costs and the statistical data of DeGate's order transaction value in the future.

Depending on whether a base token is active or not, there are different calculation methods.&#x20;

* **Tokens with active transactions:** Base token value >= minimum order value **OR** quote token value >= minimum order value
* **Tokens that are not actively traded:** the value of the quote token >= the minimum order value

Where token value = quantity \* risk price

> **Take the ETH/USDC trading pair as an example**&#x20;
>
> * The Minimum order value is $100
> * ETH is an active token
> * Assuming the ETH risk price is $2000
>
>
>
> Example A:
>
> * An order buying 0.05 ETH at a price of 1500 can be placed because
> * ETH value = $2000\*0.05 = $100 >= minimum order value
> * USDC value = $1500\*0.05 = $75 < minimum order value
> * Even if the value of the quote token (USDC) is lower than the minimum order value , the order can still be placed, because the base token (ETH) is an active currency, and its value has met the minimum order value threshold. To place an order, it suffices for either the quote token or the base token meets the threshold.&#x20;
>
>
>
> Example B:
>
> * An order that says selling 0.04 ETH at a price of 2100 can not be placed because
> * ETH value = $2000\*0.04 = $80 < minimum order value
> * USDC value = $2100\*0.04 = $84 < minimum order value
> * The order cannot be placed because neither the trading token (ETH) nor the pricing token (USDC) meets the minimum order value conditions.
>
>
>
> Take the XYZ/USDC trading pair as an example
>
> * The minimum order value is $100
> * XYZ is an inactively traded token
> * Assuming XYZ risk price is $2
>
>
>
> Example C:
>
> * An order buying 40 XYZ at a price of 1.5 can not be placed because
> * USDC value = $1.5\*40 = $60 < minimum order value
> * The order cannot be placed because the quote token (USDC) does not meet the minimum order value condition.
>
>
>
> Example D:
>
> * An order selling 20 XYZ at a price of 10 can be placed because
> * USDC value = $10\*20 = $200 >= minimum order value
> * The order can be placed because the quote token (USDC) meets the minimum order value condition.

Grid strategies also conform to the above rules. All orders under a grid strategy must meet the minimum order value requirement.

{% hint style="warning" %}
**If the minimum order value is very low, such as $10**&#x20;

Where the minimum order value on a centralized exchange is set generally at $5\~10, why has DeGate imposed a much higher threshold? The answer lies in its fee structure. Firstly, every transaction in DeGate incurs rollup fees from L2 to L1. Secondly, as Takers bear all the transaction costs, attackers can place a large number of small orders at no cost as Makers. More small orders lead to more transactions, therefore, Takers must pay more Gas fees.\

{% endhint %}

## Risk Order

A DeGate account can support only a finite number of open orders, restricted by two parameters: risk orders and circuit constraints. The node operator is responsible for parameters configuration, but does not modify circuit constraints.

#### Risk Orders

Risk orders are designed to deter malicious orders, and therefore have a relatively high threshold, unlikely to be triggered by ordinary users. Ordinary and grid orders are bound by the same constraint. After an order meets the minimum value requirement (a token’s value = the token’s risk price \* quantity), it is also necessary to determine whether it is a risk order based on the attributes of the base token. The rules are as follows:

1\. The base token is ETH, USDC or USDT

<table><thead><tr><th width="82">Side</th><th width="388">Conditions</th><th width="277">Result</th></tr></thead><tbody><tr><td>Sell</td><td>Base Token Value >= Minimum Order Size <strong>and</strong><br>Quote Token Value >= Minimum Order Size</td><td>Non-Risk Order</td></tr><tr><td>Sell</td><td>Base Token Value &#x3C; Minimum Order Size <strong>and</strong><br>Quote Token Value >= Minimum Order Size</td><td>Risk Order</td></tr><tr><td>Buy</td><td>Quote Token Value >= Minimum Order Size</td><td>Non-Risk Order</td></tr><tr><td>Buy</td><td>Base Token Value >= Minimum Order Size <strong>and</strong><br>Quote Token Value &#x3C; Minimum Order Size</td><td>Risk Order</td></tr></tbody></table>

2\. The base token is not ETH, USDC or USDT, nor is it an active token

<table><thead><tr><th width="84">Side</th><th width="385">Conditions</th><th>Result</th></tr></thead><tbody><tr><td>Sell</td><td>All sell orders</td><td>Risk Order</td></tr><tr><td>Buy</td><td>All buy orders because the order can only be placed when Quote Token Value >= Minimum Order Size</td><td>Non-Risk Order</td></tr></tbody></table>

3\. The base token is an active token, but not ETH, USDC or USDT

<table><thead><tr><th width="84.5">Side</th><th width="386">Conditions</th><th>Result</th></tr></thead><tbody><tr><td>Sell</td><td>All sell orders</td><td>Risk Order</td></tr><tr><td>Buy</td><td>Quote Token Value >= Minimum Order Size</td><td>Non-Risk Order</td></tr><tr><td>Buy</td><td>Base Token Value >= Minimum Order Size <strong>and</strong><br>Quote Token Value &#x3C; Minimum Order Size</td><td>Risk Order</td></tr></tbody></table>

#### Circuit Constraints

There are 16384 StorageIDs under each account in the circuit, which means that there can be up to 16384 unfilled orders. Ordinary and grid orders are bound by the same constraint.

### Other Constraints

To improve performance, the DeGate protocol is also bound by the following constraints set by the node operator.

* The maximum number of ordinary orders an account can create in a minute
* The maximum number of grid strategies an account can create in a minute

## Blacklist

The DeGate protocol allows for the registration of any tokens, including some non-standard ERC20 tokens that allow for supply modification or freezing of transfers. To protect users and prevent attacks, a blacklist has been implemented in the DeGate front-end and back-end services. The list is maintained by the node operator.

Operations below are not available for tokens in the blacklist:

* Deposit: Blacklisted tokens will not be credited into users’ DeGate account whether deposited via degate.com or by calling the smart contract. This applies to both standard or advanced deposits. Users must contact our Discord admin for assistance to retrieve their assets if they have deposited blacklisted tokens.&#x20;
* Transfers: Transfer of blacklisted tokens to other accounts is forbidden.
* Adding trading pairs: Adding new trading pairs for blacklisted tokens are not allowed.
* Placing an order: Creating orders or grid strategies for blacklisted tokens is not permitted.&#x20;
* Listing: Token registration on degate.com is unavailable. However, users can still call the DeGate smart contract to register blacklisted tokens.

Functions available to blacklisted tokens include:

* Viewing token balance
* Viewing historical data
* Withdrawal
* Order cancellation
* Canceling a grid strategy

## Adding Tokens to The Blacklist

In addition to the node operator maintaining the blacklist, some tokens are automatically added to the blacklist following the rules below:

1. During deposit, if the deposited amount recorded by the DeGate smart contract does not match the actual amount received, the corresponding tokens will be automatically added to the blacklist.
2. During Rollup, if the off-chain balance is greater than the assets on-chain, the corresponding tokens will be automatically added to the blacklist.&#x20;

### Removal of Tokens in the Token Blacklist

The node operator can remove tokens from the blacklist.
