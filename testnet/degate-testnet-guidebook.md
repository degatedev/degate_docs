# DeGate Testnet Guidebook

The DeGate Testnet has been released for a couple of weeks now and the team is immensely thankful to have received a lot of feedback from many enthusiastic users. Many users provided constructive suggestions for DeGate, and the team is actively working hard on them with the aim of implementing them in future releases. Having said that, certain users also raised questions with regards to some of the product features.&#x20;

This document will serve as a guide to answer common questions, and also to provide users with a seamless Testnet experience on DeGate. This guidebook in a work in progress and will be continuously updated as more questions are raised by the community.&#x20;

Questions：

* [Why do I need to deposit into DeGate account before trading?](degate-testnet-guidebook.md#degatetestnet-xin-shou-zhi-nan-whydoineedtodepositintodegateaccountbeforetrading)
* [How can I be sure that my deposit funds are safe with DeGate？](degate-testnet-guidebook.md#degatetestnet-xin-shou-zhi-nan-howcanibesurethatmydepositfundsaresafewithdegate)
* [How to use the Permissionless Listing feature to set up a new trading pair？](degate-testnet-guidebook.md#degatetestnet-xin-shou-zhi-nan-howtousethepermissionlesslistingfeaturetosetupanewtradingpair)

## Why do I need to deposit into DeGate account before trading? <a href="#degatetestnet-xin-shou-zhi-nan-whydoineedtodepositintodegateaccountbeforetrading" id="degatetestnet-xin-shou-zhi-nan-whydoineedtodepositintodegateaccountbeforetrading"></a>

In order to provide users with a trading experience similar to that of a traditional centralized exchange, DeGate orderbook product was built based on ZK Rollup technology. It is for this reason that users are required to deposit their assets from Ethereum main network to DeGate decentralized account before conducting any transactions. We firmly believe this feature will pay out in the long term as it can bring about significant user experience improvements such as:&#x20;

* Real-time order placement, order cancellation, and matching of orders
* Order placement and cancellation is completely free
* The transaction gas fee will be much lower than on Ethereum mainnet

Simply put, trading on DeGate will be much faster and cheaper.

## How can I be sure that my deposit funds are safe with DeGate？ <a href="#degatetestnet-xin-shou-zhi-nan-howcanibesurethatmydepositfundsaresafewithdegate" id="degatetestnet-xin-shou-zhi-nan-howcanibesurethatmydepositfundsaresafewithdegate"></a>

In ZK-Rollup technology system, users' assets are hosted in smart contracts, leveraging on cryptography and immutable protocols to ensure that no one can manipulate these assets. In addition, in order to ensure that DeGate is a completely decentralized, trustless, permissionless order book DEX, the DeGate protocol has added security guarantees via the following 3 unique features:

### **Data visibility guaranteed by ZK-Rollup**

All transaction data is recorded in the Merkle tree through smart contracts, and secured by Ethereum mainnet;

### **No AdminKey**

To ensure complete decentralization, DeGate protocol was created without an AdminKey. Once the DeGate protocol is deployed, its code execution logic will never change;

### **Exodus Mode**

Exodus Mode is designed into the DeGate protocol to deal with the most extreme situations such as an operator going offline. Anyone can activate Exodus Mode once any mandatory withdrawal has not been executed for more than 15 days. At this point, users will be able to withdraw their assets by providing proof of data (recoverable from the Ethereum mainnet) to the smart contract.

## How to use the Permissionless Listing feature to set up a new trading pair？ <a href="#degatetestnet-xin-shou-zhi-nan-howtousethepermissionlesslistingfeaturetosetupanewtradingpair" id="degatetestnet-xin-shou-zhi-nan-howtousethepermissionlesslistingfeaturetosetupanewtradingpair"></a>

A unique feature of DeGate protocol is titled Permissionless Listing - This feature fully allows users to create new trading pairs without permission, which is first-of-its-kind amongst all the current order book DEXes in the market. Next, let's take a look at the step-by-step guide in adding a new trading pair.

Step 1: Before creating your trading pair, you must ensure that the relevant token has been added. Select on the trading pair in the upper left corner, and search for a token you want to add. If token is not found, you are able to 'Register Token'.

![Search for token](../.gitbook/assets/image.png)

Step 2: Fill in the contract address of the token and select 'Register Token'. Once prompted, select 'Confirm Registration' in the pop-up, and subsequently confirm the transaction in the wallet to complete the addition of the token.\
\
_Note: Do ensure the contract address of the token are from official sources._ &#x20;

![Enter token contract address](<../.gitbook/assets/image (5).png>)

Step 3: After token registration has been completed (requires 12 blocks confirmations), you can now search for the token which you have just added, after which you can select "Add New Pair'.

!['Add New Pair' is now available](<../.gitbook/assets/image (3).png>)

Step 4: On the 'Add Trading Pair' window, select the desired 'Quote Token' , and select 'Preview'.

![Select Quote Token to complete token pair registration](<../.gitbook/assets/image (2).png>)

Step 5: Select 'Register Token Pair', and confirm transaction in wallet.

![Complete token pair registration ](<../.gitbook/assets/image (6).png>)

You are now done! And have successfully created a new trading pair! Of course, no one is trading it yet, so the Order Book is currently empty. Share your pair you have just created with the community or create more grid market orders to increase usage and popularity!

![You can now make a trade on the new token pair](<../.gitbook/assets/image (1).png>)
