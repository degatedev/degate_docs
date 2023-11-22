# ZK-Rollup介绍

DeGate协议技术目标为实现高吞吐量，低Gas成本的交易协议。基于zkSNARKs技术，DeGate链下处理请求后生成零知识证明，一并提交上链，最终通过链上验证的同时达到数据可用性之目的。

<figure><img src="../.gitbook/assets/Screen Shot 2022-12-09 at 16.18.34.png" alt=""><figcaption><p>ZK-Rollup概览</p></figcaption></figure>

### Operator

Operator是协议的重要一环，主要负责

1. **创建zkBlock：**按规则处理每个批次(Batch)的ZK-Rollup事件，生成zkBlock
2. **生成零知识证明：**调用电路生成zkBlock的证明
3. **提交zkBlock数据：**调用Postman提交zkBlock数据到链上合约，确认状态变更

### 链下交易

DeGate协议内需要经过零知识证明和验证的链下交易，包括以下：

<table><thead><tr><th width="191">事件</th><th>说明</th></tr></thead><tbody><tr><td>No-op</td><td>空交易，用于填充未全部塞满链下交易的zkBlock</td></tr><tr><td>AccountUpdate</td><td>允许用户添加、更新资产私钥</td></tr><tr><td>AppKeyUpdate</td><td>允许用户添加、更新交易私钥，配置交易私钥权限</td></tr><tr><td>SpotTrade<span data-gb-custom-inline data-tag="emoji" data-code="0031">1</span></td><td>两个订单的链下撮合</td></tr><tr><td>BatchSpotTrade</td><td>Operator对SpotTrade进行聚合，提高交易吞吐量，并降低用户上链开销</td></tr><tr><td>OrderCancel <span data-gb-custom-inline data-tag="emoji" data-code="0032">2</span> </td><td>允许用户上链取消订单，此操作后的订单无法再被operator用于撮合</td></tr><tr><td>Add</td><td>确认用户在L1的资产划入行为，然后记账到L2账户</td></tr><tr><td>Send</td><td>用户将资产从L2发送到L1</td></tr><tr><td>Transfer</td><td>两个L2账户之间的资产转移</td></tr></tbody></table>

注:digit\_one:：订单不会直接上链，只有订单成交后才会上链。

注:digit\_two:：取消订单和网格策略，也仅通过签名通知交易系统撤单，不会上链证明，就不属于ZK-Rollup事件。为了防止DeGate节点利用下单签名作恶，特提供OrderCancel方法，要求追加上链证明此订单已取消。

### zkBlock

zkBlock可视为DeGate L2的区块。Operator处理的每个批次，根据事件数量多少，会生成一到多个有顺序的zkBlock。然后zkBlock会传给电路来计算零知识证明。

### 电路

这不是物理上存在的电路，而是指zkSNARK电路。电路负责描述需要进行零知识证明的事件，例如订单成交和充值，是零知识证明的重要组成部分。电路接受输入，输入信号通过电气门的路径产生输出，得到zkBlock相应的零知识证明。

### 默克尔树

为提高计算和存储效率，DeGate对数据进行了筛选压缩，默克尔树能在复杂性、计算时间和用户友好性之间取得平衡。协议构建了两颗树：完整树(Entire Merkle Tree)和资产树(Asset Merkle Tree)。

* 完整树确保DeGate协议的数据安全性，记录了所有DeGate账户、资产、交易信息。
* 资产树确保用户资产的去托管化，即使DeGate运营方无法提供任何服务，用户仍旧可以安全地提取自己的资产。资产树记录了所有DeGate账户和资产信息。

### 提交zkBlock

生成zkBlock的零知识证明后，Operator会通过Postman调用DeGate智能合约的`submitBlocks`方法，以提交zkBlock相关数据到链上进行状态变更的确认（可以同时提交多个zkBlock，但必须严格按照出块顺序来提交），这些数据主要包含：

* 完整树的默克尔树根哈希
* 资产树的默克尔树根哈希
* 零知识证明
* 账户权限和资产余额的变更数据
* 划入、发送、账户更新这三种交易类型的额外数据

节点运营方提交zkBlock的链上交易需要支付ETH作为gas，所以会向用户收取一定的矿工费。

### 智能合约

DeGate协议部署在链上的智能合约，负责存储用户资金，验证链下节点提交的零知识证明并存储最新的默克尔树根。其由多个合约构成，其中主要合约为：

1. **Exchange：**Operator提交zkBlock、用户充值和强制提现的交互
2. **Deposit：**托管用户存入的资产，提供划入、发送、转账的功能
3. **Loopring：**Exchange合约参数配置
4. **BlockVerify：**注册Verifying Key和验证零知识证明

### Postman

Operator通过Postman来调用DeGate合约，严格按照zkBlock的出块顺序，依次提交上链。

### 区块同步

观察DeGate智能合约的所有链上交易，例如划入资产、强制提现、Rollup交易，确认交易后通知节点。

以上对DeGate协议的ZK-Rollup部分做了简单说明，想要了解更多，请查看协议设计文档
