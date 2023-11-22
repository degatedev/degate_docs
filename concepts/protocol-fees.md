# 协议费用

使用DeGate协议时，根据不同场景的操作，用户可能需要支付不同的费用

* **手续费：**限价单和市价单成交时，作为Taker一方的用户需要支付交易手续费。手续费率取决于不同的交易对。手续费会从用户成交后得到币种中扣除。例如DG/USDC交易对，市价单买入1000个DG，假设手续费率为0.1%，则用户作为Taker得到的1000个DG中，有1000\*0.1%=1个DG作为手续费，最终收到999个DG。所有交易手续费都进入DeGate HomeDAO金库。
* **矿工费：**所有通过零知识证明完成的操作，最终提交到以太坊主网时，会有一笔矿工费开销。经过测试，DeGate协议定义了每种操作的Gas使用量，并在用户发起相关操作前，根据当时网络的Gas价格和以太坊价格，计算出用户需要支付的矿工费。目前支持用ETH、USDC和USDT来支付矿工费。

### 手续费率 <a href="#trading-fee-rate" id="trading-fee-rate"></a>

每个交易对的手续费率由节点运营方设置，目前设置为：

<table data-card-size="large" data-view="cards" data-full-width="false"><thead><tr><th>交易对类型</th><th>Taker费率</th><th>Maker费率</th><th>举例</th></tr></thead><tbody><tr><td>稳定类</td><td>0.01%</td><td><strong>免费</strong></td><td>USDT/USDC, DAI/USDC,<br>DAI/USDT，wstETH/ETH</td></tr><tr><td>其他</td><td>0.05%</td><td><strong>免费</strong></td><td>ETH/USDC, DG/USDT</td></tr></tbody></table>

为了防止节点运营方任意修改手续费率，在DeGate智能合约中加入了手续费率最大值的参数，实际收取的费率不得超过此参数，否则订单成交提交到合约无法通过验证。并且手续费率最大值修改后有7天的延迟生效期，留出足够时间供用户应对。

### 操作请求与费用

<table><thead><tr><th width="133">操作请求</th><th width="100">矿工费</th><th width="100">手续费</th><th>说明</th></tr></thead><tbody><tr><td>普通订单成交</td><td>有</td><td>有</td><td>全部由Taker支付, Maker免费</td></tr><tr><td>网格策略成交</td><td>/</td><td>/</td><td>网格策略下均为Maker单</td></tr><tr><td>划入</td><td>/</td><td>/</td><td>DeGate节点运营方协议补贴矿工费</td></tr><tr><td>发送</td><td>有</td><td>/</td><td></td></tr><tr><td>转账</td><td>有</td><td>/</td><td>若转账给未开通的DeGate账户，发起转账的用户需额外支付开通账户的费用</td></tr><tr><td>开通账户</td><td>/</td><td>/</td><td>DeGate节点运营方协议补贴矿工费</td></tr><tr><td>重置资产私钥</td><td>有</td><td>/</td><td></td></tr><tr><td>链上取消订单</td><td>有</td><td>/</td><td></td></tr><tr><td>链上取消网格订单</td><td>有</td><td>/</td><td>网格策略下所有订单都需要一起链上取消，总费用为订单数*单次链上取消订单</td></tr><tr><td>注册交易对</td><td>有</td><td>/</td><td>交易对注册无需零知识证明，收取矿工费用来预防攻击</td></tr><tr><td>领取挖矿奖励</td><td>有</td><td>/</td><td>挖矿奖励通过转账方式完成领取</td></tr></tbody></table>

### 计算矿工费

每种链下交易都配置了Gas使用量(GasUsage)，是基于多次实验统计后得到的数值。用户发起请求时，根据此时网络的Gas价格(GasPrice)和ETH价格(ETHPrice)，可计算出分别所需的ETH、USDC、USDT数量

```
ETH = GasUsage * GasPrice
USDC = GasUsage * GasPrice / ETHPrice
USDT = GasUsage * GasPrice / ETHPrice
```

| 操作请求                  | Gas使用量    |
| --------------------- | --------- |
| 成交                    | 800       |
| 划入                    | /         |
| 充值                    | 58393     |
| 转账                    | 2225      |
| 转账给新账户                | 22422     |
| 开通账户                  | /         |
| 重置资产私钥                | 20197     |
| 链上取消订单                | 2393      |
| 链上取消网格策略 :digit\_one: | N \* 2393 |
| 注册交易对                 | 100       |

注:digit\_one:：N为网格策略下的订单数，每个网格订单都要单独一次链上取消

###

### 付费划入

每笔划入都因需要零知识证明而产生费用，目前节点运营方会补贴这类费用，用户无需为划入资产付费。但同时为避免补贴策略被利用在对DeGate协议的攻击，增加了免费补贴的上限保护。用户划入时如果触发了补贴上限，则需要支付指定数量的ETH才能完成该笔划入。

* 标准划入：可以用钱包或DeGate账户来付费，支付数量根据当时网络的Gas价格计算
* 高级划入：通过钱包支付，支付数量参数配置在DeGate智能合约内，节点运营方有修改权限

### 强制提现

直接用钱包与DeGate智能合约交互，调用`ForceWithdraw`方法时，需要支付指定数量的ETH，该参数配置在DeGate智能合约内，最多为0.25 ETH，节点运营方有修改权限。

### DeGate HomeDAO金库

所有产生的矿工费和交易费会转入DeGate HomeDAO金库账户。节点运营方可以领取这部分资金。
