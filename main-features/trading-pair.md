# 交易对

交易对由一个交易币种和一个计价币种组成，显示成**交易币种/计价币种**，例如ETH/USDC。DeGate节点维护了交易对信息，交易币种和计价币种组成了唯一的交易对，各对应一个订单簿。DeGate协议目前不支持切换交易对币种顺序，如ETH/USDC不能变成USDC/ETH。而且出于安全和实用性，对计价币种范围添加了限制。

### 添加交易对流程

用户可以通过degate.com或SDK来添加交易对，添加时需要指定一个交易币种，并从ETH、USDC、USDT中选择一个计价币种，来组成交易对。出于协议的经济安全考虑，用户添加交易对需要以DeGate账户支付少量矿工费，完成支付后，交易对立即添加成功，可以开始挂单交易。

### 计价币种限制

订单簿的交易对和AMM的交易池相似但不相同，主要区别在于

1. **顺序：**交易对有顺序，交易池没有顺序
2. **流动性：**交易对流动性不共享，交易池流动性只要币种相同，流动性会通过交易路由共享。

订单簿交易来自传统金融，法币担任计价币种。来到数字货币行业，常用计价币种除了美元稳定币，还有BTC和ETH。经过综合考量，节点运营方设置的计价币种**目前限于ETH，USDC和USDT**，能满足绝大部分的订单簿交易需求。

### 交易对类型

交易对有两种类型，影响订单簿和交易时的价格精度范围

1. **常规交易对：**绝大部分交易对属于此类。
2. **稳定类交易对：**稳定币交易对比如USDT/USDC、抵押物和原资产交易对比如stETH/ETH，这些价格波动较小，维持在区间范围内的交易对，称为稳定类交易对。

新添加交易对都默认为常规交易对，节点运营方将根据情况调整成稳定类型。

### 查找交易对

由于币种可以重名，查询交易对务必要检查币种合约地址。DeGate网站中默认币种的交易对会显示币种图标；非默认币种交易对的图标为<img src="../.gitbook/assets/Screen Shot 2022-09-05 at 09.41.22.png" alt="" data-size="line">，进入交易界面时会出现风险提示，在部分列表处还会显示缩略的合约地址。

### 自选交易对

degate.com支持交易对自选功能。自选信息存储在本地浏览器，没有同步机制，换设备后需要另行管理自选列表。