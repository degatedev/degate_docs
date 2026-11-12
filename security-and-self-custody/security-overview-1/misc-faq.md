# Misc/FAQ

## Network fees  <a href="#actionwallet-gitbook-networkfees" id="actionwallet-gitbook-networkfees"></a>

Fees are paid in two parts:

|                                                  |                 |                                                                                                         |
| ------------------------------------------------ | --------------- | ------------------------------------------------------------------------------------------------------- |
| Moving funds to your Action Wallet               | Hardware wallet | That chain’s gas token (e.g. ETH on Base, SOL on Solana). Keep a small balance on your hardware wallet. |
| Everything else (the trade, Solana account rent) | Action Wallet   | Its gas balance, just like other DeGate accounts.                                                       |

### **Topping up**

If your Action Wallet runs low on gas, the app will ask you to Top Up Action Wallet from your hardware wallet. Top-ups are capped at $50 each, so only a small amount ever sits there.&#x20;

Before you confirm, the fee estimate shows both parts: From Hardware Wallet and From Action Wallet. Refundable Solana rent is shown as a separate line.

## Supported hardware wallets <a href="#actionwallet-gitbook-supportedhardwarewallets" id="actionwallet-gitbook-supportedhardwarewallets"></a>

We recommend a hardware wallet for long-term holdings and larger balances: your keys stay offline on a device you control.

| Device   | Connection | Status      |
| -------- | ---------- | ----------- |
| OneKey   | Bluetooth  | Supported   |
| Ledger   | Bluetooth  | Supported   |
| Keystone | Bluetooth  | Coming soon |
| Trezor   | Bluetooth  | Coming soon |

{% hint style="info" %}
_Hardware wallet accounts support most DeGate networks. Bitcoin is not yet supported. Keep your hardware wallet firmware up to date._&#x20;
{% endhint %}



## Frequently Asked Questions (FAQ) <a href="#actionwallet-gitbook-frequentlyaskedquestions-faq" id="actionwallet-gitbook-frequentlyaskedquestions-faq"></a>

#### **Do I need to back up my Action Wallet?**

No. Your hardware wallet is the backup. Sign the setup message again on the same device and you get the same Action Wallet back.

#### **Can DeGate move my funds?**

No. Your funds stay in your hardware wallet, and only your device can approve transfers out. Your Action Wallet’s keys are encrypted on your phone; DeGate's servers never receive them.

#### **Can I export my Action Wallet or use it in another wallet app?**

It is derived from your hardware wallet, so you can re-derive it with third-party tools and access it independently. Anything in your Action Wallet stays recoverable even without DeGate. Your hardware wallet address also stays fully usable in any compatible wallet software.

#### **Why do I need to top up my Action Wallet?**

It pays the network fees for each trade. If it runs low, the app will ask you to top it up from your hardware wallet (up to $50 at a time).

#### **I sent tokens to my Action Wallet by mistake. What now?**

Always use your hardware wallet address to receive funds. If something ended up in your Action Wallet, [contact support](https://docs.degate.com/about-degate/official-links).

#### **I removed my hardware wallet from the app. Is my money gone?**

No. Your funds live on your hardware wallet, not in the app. Just reconnect and set up your Action Wallet again.

{% hint style="info" %}
_You need to be online to remove a hardware wallet, so your other devices stay in sync._
{% endhint %}
