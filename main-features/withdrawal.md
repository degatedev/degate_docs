# 提现

用户可随时发出提现链下请求，从DeGate合约中取回资产。如图所示，用户签名发起提现请求，节点验证签名通过后，先从该资产的可用余额中锁定需要提现的部分数量，然后交给Operator进行rollup操作。当包含了提现请求的rollup交易入块后，用户会收到提现的资产。假如节点拒接处理提现申请，用户可通过[强制提现和逃离模式](../concepts/exodus-mode.md)来取回资产。

<figure><img src="../.gitbook/assets/Screen Shot 2022-10-07 at 13.10.08.png" alt=""><figcaption><p>提现过程</p></figcaption></figure>

### 提现费用

发起提现时，需支付矿工费。目前支持ETH、USDC、USDT，不支持以提现币种支付矿工费。

### 提现失败

包含了zkBlock零知识证明的rollup交易入块时，DeGate合约会验证数据有效性，通过验证后便完成了rollup。如果rollup交易包含了提现请求，同时还会发起转账(Inline transaction)。对ERC20币种提现而言，会调用其合约地址的transfer方法。特殊情况下，例如该币种的合约限制了转账功能，这笔提现就会失败。资产会停留在DeGate合约，并未丢失，用户可以调用DeGate合约方法重试转账，转账目标地址和资产数量无法更改。