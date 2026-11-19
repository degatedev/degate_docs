# How It Works

## Set up your Action Wallet <a href="#actionwallet-gitbook-setupyouractionwallet" id="actionwallet-gitbook-setupyouractionwallet"></a>

You will be asked to set it up the first time you use a feature that needs it, such as Turbo Range.

1. Connect and unlock your hardware wallet.
2. Sign a free, one-time message on your device. It does not move funds or approve anything.
3. Confirm with your password, Face ID or fingerprint.&#x20;

All accounts on the same hardware wallet share one Action Wallet. To see its addresses, go to **Wallet Details → Show Action Wallet**.

{% hint style="info" %}
_Only sign the Action Wallet setup message inside the official DeGate app. Never sign it on any other website or app._
{% endhint %}

## Open a Turbo Range position <a href="#actionwallet-gitbook-openaturborangeposition" id="actionwallet-gitbook-openaturborangeposition"></a>

&#x20;Here’s what happens when you open a Turbo Range position:

1. **Review the position in the DeGate app**\
   On your hardware wallet, check the amount and the destination (your Action Wallet), then confirm the transfer.
2. **Confirm the transfer on your hardware wallet**\
   Your device shows the amount and the destination, which is your Action Wallet. Check that it matches the address under **Wallet Details → Show Action Wallet**.
3. **The Action Wallet forwards your funds to the DeGate solver**\
   The solver calls the Handler contract to open your position in a single atomic transaction. If an operation fails, your funds always go back to your hardware wallet.
4. **Everything comes back to your hardware wallet**\
   Your LP position NFT and any leftover funds are sent directly to your hardware wallet address, not the Action Wallet.

Managing your position works the same way. Claiming rewards, adding funds, withdrawing, adjusting the range and closing all follow these steps. Your position NFT moves through the Action Wallet only for the duration of the operation, then returns to your hardware wallet.

### If operation failed  <a href="#actionwallet-gitbook-ifoperationfailed" id="actionwallet-gitbook-ifoperationfailed"></a>

Your funds always go back to your hardware wallet.&#x20;

**Most cases: the solver refunds you -** Your funds move to the solver almost immediately, so most failures happen there. The solver sends your principal or position NFT straight back to your hardware wallet.

**Rare cases: your Action Wallet returns them -** Sometimes funds reach your Action Wallet but don’t make it to the solver, for example due to a Solana timeout or network congestion. Your Action Wallet then sends them back:

* **Automatically while the app is open**, As long as the DeGate app stays open, it signs the return from your Action Wallet to your hardware wallet for you.
* **Manually**, if the app can’t do it automatically (for example, your Action Wallet is locked). Tap **Send back** in the app, or find the transaction marked **Pending** in **History**.
* **Gas is covered.** If your Action Wallet is short on gas, DeGate pays the network fee.

> Unused network fees from a failed operation are refunded to your Action Wallet.&#x20;

## Where your funds are at each step <a href="#actionwallet-gitbook-whereyourfundsareateachstep" id="actionwallet-gitbook-whereyourfundsareateachstep"></a>

The Action Wallet keeps your hardware wallet away from smart contracts. Here’s who controls your funds during an operation:

|                                    |                                                                          |                                                                                                                                                |
| ---------------------------------- | ------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| <ol><li>Before you start</li></ol> | Your hardware wallet                                                     | **You,** with your device                                                                                                                      |
| 2. You confirm the transfer        | Your Action Wallet                                                       | **You, through the DeGate app.** The keys are encrypted on your phone device and never sent to DeGate.                                         |
| 3. The operation runs              | DeGate’s solver                                                          | **DeGate solver.** The solver holds your funds briefly while it executes the trade, then sends the result or a refund to your hardware wallet. |
| 4. Operation completed             | <p>Your hardware wallet;<br>LP NFT position, rewards, leftover funds</p> | **You,** with your device                                                                                                                      |

{% hint style="info" %}
_**In short:** For a few seconds, at most a few minutes, you’re trusting DeGate’s solver to complete the trade or refund you._&#x20;
{% endhint %}

## How DeGate protects funds in transit <a href="#actionwallet-gitbook-howdegateprotectsfundsintransit" id="actionwallet-gitbook-howdegateprotectsfundsintransit"></a>

DeGate takes every measure to protect your funds at each step between your Action Wallet and your hardware wallet. Here’s how

* The solver only follows the route you confirmed, and sends outputs to your hardware wallet.
* If a trade fails, the solver refunds you only to your hardware wallet.
*

<br>
