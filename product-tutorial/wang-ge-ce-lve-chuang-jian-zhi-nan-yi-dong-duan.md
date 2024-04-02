# 网格策略创建指南（移动端）

* 输入初始投入（我想投入的总资金）：输入97 ETH，系统将自动计算出USDC的数量

<figure><img src="broken-reference" alt=""><figcaption></figcaption></figure>

* 设置网格密度：网格数设置为200，系统将自动计算出每格数量

<figure><img src="broken-reference" alt=""><figcaption></figcaption></figure>

创建网格策略创建成功之后，DeGate系统将在价格区间内设置多个买卖限价订单

<figure><img src="broken-reference" alt=""><figcaption></figcaption></figure>

网格机器人将会在设置的价格区间内不断地进行低买高卖自动产生收益。原理如下图：

<figure><img src="../.gitbook/assets/Normal-Grid-CN-m (2) (1).gif" alt=""><figcaption></figcaption></figure>

当完成一次低买高卖后，您将获利1 USDC



**注意：**

以文中的ETH/USDC网格策略为例，请确保当前市场价处于您设置的价格区间内（1200-1400），否则网格策略将不再产生收益。
