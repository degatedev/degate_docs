# 在DeGate DEX自主上架代币

创建DeGate支持无需许可代币上架，就是允许任何人在无需事先获得交易所上批准的情况下自行上架代币。通过这一功能，个人或项目可以独立地将他们的代币添加到DeGate DEX上，为用户提供更广泛的交易选择，而无需依赖中心化的上币审核。

本教程将以本教程将以Rocket Pool 代币 (RPL)为例，教你如何一步步在DeGate DEX上列出新代币：

第一阶段 - 在DeGate DEX上添加你的代币并创建交易对

第二阶段 - 为你的代币交易对提供流动性

## 第一阶段 - 在DeGate DEX上添加你的代币并创建交易对

1.1 在搜索栏中粘贴上你的代币合约地址，选择“免审核上币”

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption><p>复制代币合约地址到搜索栏</p></figcaption></figure>

{% hint style="info" %}
注意：DeGate DEX不支持弹性供应代币。

更多详细信息，请参考：[https://docs.degate.com/v/product\_en/concepts/economic-security。](https://docs.degate.com/v/product\_en/concepts/economic-security%E3%80%82)
{% endhint %}

1.2 确认你要添加的代币信息，并点击“立即上币”

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption><p>在DeGate上添加你的代币</p></figcaption></figure>

1.3  耐心等待12个块的确认，你也可以随时查看上币进程

<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption><p>批准钱包签名以完成整个添加流程</p></figcaption></figure>

1.4 当代币完成添加后可以进行创建交易对

<figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption><p>Rocket Pool 代币 (RPL) 已成功被添加</p></figcaption></figure>

1.5 选择交易对的Quote代币，需支付一定的gas费来完成交易对的创建

<figure><img src="../.gitbook/assets/image (11).png" alt=""><figcaption><p>选择一个代币与 $RPL 配对</p></figcaption></figure>

{% hint style="info" %}
注意：只支持USDC/USDT/ETH作为Quote代币。

更多详细信息，请参考：[https://docs.degate.com/v/product\_en/main-features/trading-pairs。](https://docs.degate.com/v/product\_en/main-features/trading-pairs%E3%80%82)
{% endhint %}

<figure><img src="../.gitbook/assets/image (12).png" alt=""><figcaption><p>继续添加交易对</p></figcaption></figure>

<figure><img src="../.gitbook/assets/image (13).png" alt=""><figcaption><p>批准钱包签名以完成交易对流程</p></figcaption></figure>

1.6 其他请求（例如添加交易对图标或代币的激活[标准划入](https://docs.degate.com/v/product\_zh/main-features/deposit)）

请在 [https://discord.gg/delegate](https://discord.gg/delegate) 为你的需求开工单。团队将在24小时内响应。

{% hint style="info" %}
对于添加图标需求，请确保您的图标文件是以透明背景的PNG格式。
{% endhint %}

## 第二阶段 - 为你的代币交易对提供流动性

2.1 当交易对创建完毕后，你需要将相应的代币充值到DeGate DEX中

<figure><img src="../.gitbook/assets/image (14).png" alt=""><figcaption><p>将交易对中的(RPL/USDC) 充值到DeGate DEX中</p></figcaption></figure>

2.2  在正式为你的交易对注入流动性之前，你需要通过在该交易对中设置1笔卖出限价单和1笔买入限价单，来激活网格交易功能

<figure><img src="../.gitbook/assets/image (15).png" alt=""><figcaption><p>网格交易功能需要激活</p></figcaption></figure>

<figure><img src="../.gitbook/assets/image (16).png" alt=""><figcaption><p>设置一个$RPL买入限价单</p></figcaption></figure>

<figure><img src="../.gitbook/assets/image (18).png" alt=""><figcaption><p>设置一个$RPL卖出限价单</p></figcaption></figure>

{% hint style="info" %}
提示：&#x20;

1）最佳实践 - 初始的买入订单和卖出订单应该相邻，价差较小。

&#x20;2）确保买入/卖出订单的规模大于100 USDC。

更多详细信息，请参考[https://docs.degate.com/v/product\_en/main-features/placing-orders](https://docs.degate.com/v/product\_en/main-features/placing-orders%E3%80%82)
{% endhint %}

2.3 顶部选择“网格交易”并选择你创建的交易对

<figure><img src="../.gitbook/assets/image (19).png" alt=""><figcaption><p>网格交易已激活，启动后就如同设置了许多买入卖出的限价单</p></figcaption></figure>

2.4  输入合适的网格交易策略参数

<figure><img src="../.gitbook/assets/image (20).png" alt=""><figcaption><p>输入流动性参数</p></figcaption></figure>

2.5 你可以左侧行情图上预览该策略

{% hint style="info" %}
提示：&#x20;

价格区间 - 鼓励选择较宽的价格范围。&#x20;

初始投入 - 较高的分配量可以为您的代币交易对提供更深的流动性。&#x20;

网格数 - 更多的网格可以为您的代币创建更高效的订单薄。
{% endhint %}

2.5 确认填写网格参数，准备在设定的价格区间中为你的交易对提供流动性

<figure><img src="../.gitbook/assets/image (21).png" alt=""><figcaption><p>再次确认参数</p></figcaption></figure>

2.6 网格设置完成你可以随时查看运行状态和代成交的买卖单

<figure><img src="../.gitbook/assets/image (22).png" alt=""><figcaption><p>代币的网格交易已上线！用户现在可以交易你的代币了</p></figcaption></figure>

{% hint style="info" %}
注意：关于网格交易的更多策略内容，请参考：[https://docs.degate.com/v/product\_en/product-tutorial/decentralized-grid-strategy。](https://docs.degate.com/v/product\_en/product-tutorial/decentralized-grid-strategy%E3%80%82)
{% endhint %}

在DeGateDEX中设置网格策略，就等于变相的在为该交易对（在你设置的特定价格区间中）提供流动性

当你完成以上所有步骤，其他用户就可以在DeGate DEX 交易你的代币了
