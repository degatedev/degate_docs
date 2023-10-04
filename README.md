# 概览

## 序言 <a href="#preface" id="preface"></a>

本文档详细阐述了DeGate协议的设计理念、核心概念和主要功能。DeGate是基于ZK-Rollup技术的去中心化订单簿交易所，特点是资金自托管、速度快、矿工费成本低。本协议设计时始终坚持了以下原则：

### 无需信任 <a href="#trustless" id="trustless"></a>

存在DeGate协议的资金都是非托管式的，最高权限由用户掌握，其他角色无法触及用户的资产，整个协议没有后门和管理员权限，主要体现在：

* DeGate协议无法升级。
* 交易未被确认超过规定时长后，用户可自主取回充值。
* 用户可发起强制提现，进入逃离模式后自主取回存放在协议内的资产。
* 所有涉及DeGate账户资产变化的操作，都需要用户签名才能完成，即在协议上确保资产的变化一定是经过用户授权才会发生。
* 无需信任的订单取消，用户可以在区块链上追加确认，实现100%的无需信任。

### 免审核上币 <a href="#permissionless-listing" id="permissionless-listing"></a>

只要有区块链钱包，无需身份审查，就能访问和使用DeGate。任何人都能在DeGate协议内上架任意符合标准ERC20规格的币种并进行交易。维持上币的开放性对DeGate来说意义重大。

### 经济安全 <a href="#economical-security" id="economical-security"></a>

开放协议中实现免审核使用、免审核上币和免审核交易要同时考虑功能和经济方面的安全。DeGate是目前市面上唯一的实现了无审核上币的订单簿去中心化交易协议。DeGate协议经济安全的措施包括如下：

* 充值入账的免费额度
* 币种分类属性
* 特定的计价币种
* 设置订单的最小价值要求
* 设置风险价格和风险订单
* 交易风险提示
* 自动排除不符合标准ERC20规格币种的币种黑名单系统

详细介绍见：[economic-security.md](concepts/economic-security.md "mention")



DeGate在准入门槛、交易开放性、资金安全等多个方面都站在中心化的对立面，同时又能提供和中心化交易所类似的下单交易体验。

## 核心概念 <a href="#core-concepts" id="core-concepts"></a>

DeGate协议的核心是ZK-Rollup技术，由链上和链下两部分构成，所有账户和资产变化通过链下处理后Rollup至链上智能合约。

* **链上部分：**部署于EVM网络的智能合约，存放资产、验证零知识证明、提供充值和提现方法
* **链下部分：**DeGate链下节点，主要包括
  * 前端网站：可通过浏览器访问的站点
  * 交易系统：处理用户的下单，根据订单簿完成撮合；处理账户和资产变化的事件
  * Operator：定期处理账户和资产的链下交易，生成zkBlock、调用电路、提交证明
  * 电路：描述需要进行零知识证明的事件，被用于生成零知识证明
  * 默克尔树：以树型结构存储了DeGate协议内的账户、资产和订单的数据
  * 区块同步：观察和确认DeGate智能合约上发生的所有交易
  * Postman：在EVM网络调用DeGate合约方法，提交zkBlock数据到合约

<figure><img src=".gitbook/assets/Screen Shot 2022-10-14 at 10.37.50.png" alt=""><figcaption><p>DeGate协议框架</p></figcaption></figure>

### EVM兼容 <a href="#evm-compatible" id="evm-compatible"></a>

DeGate协议支持EVM网络。测试网版本已经部署在Goerli，首个主网版本将会部署至以太坊主网。

### 用户请求和链下交易 <a href="#off-chain-request" id="off-chain-request"></a>

DeGate协议中用户发起任何操作请求，都需要经过用户的私钥签名授权。涉及资产和账户变化的操作会作为链下交易进行处理。

### ZK-Rollup

DeGate协议的ZK-Rollup过程可概括为下列三步：

1. 用户签名发起请求。
2. 节点验证和处理用户请求，将链下交易打包出块，调用电路计算零知识证明。
3. 节点将证明结果发到链上合约进行验证，完成ZK-Rollup，提供了资产的数据可用性。

了解更多：[introduction-to-zk-rollup.md](concepts/introduction-to-zk-rollup.md "mention")

<figure><img src=".gitbook/assets/Screen Shot 2022-10-13 at 11.36.49.png" alt=""><figcaption><p>Zk-Rollup过程</p></figcaption></figure>

### 签名 <a href="#sign-message" id="sign-message"></a>

在DeGate内发起链下请求时需要签名，支持两种签名方式：ECDSA和EdDSA。钱包私钥完成ECDSA签名来解锁账户，生成一把EdDSA私钥，该私钥称为「资产私钥」。DeGate协议采用资产私钥对用户的链下请求做签名，因为EdDSA对零知识证明更加友好，能降低证明的计算成本。不同链下请求所需签名方式不同，例如下单时用EdDSA签名，无须用户在钱包内确认，而提现和转账请求仍需通过钱包确认ECDSA签名，兼顾了安全和便利。

了解更多：[signature-and-secret-key.md](concepts/signature-and-secret-key.md "mention")

### 账户 <a href="#account" id="account"></a>

DeGate协议的默克尔树记录了所有账户的权限和资产信息。用户首次使用时需以免审核的方式开通一个去DeGate去中心化账户，即在默克尔树上的账户节点写入钱包地址、资产公钥等绑定关系。用户存入DeGate协议的链上资产，将被记账到相应的账户节点，用于交易挂单等操作。

了解更多：[account-structure.md](concepts/account-structure.md "mention")

### 充值 <a href="#deposit" id="deposit"></a>

在DeGate开始交易前，需要先往DeGate账户充值资产。DeGate节点确认完用户的链上充值交易后，所转账数量就会计入DeGate账户的可用余额，该余额**立即可用于挂单等操作**；同时，Operator会发起一个确认充值的链下交易，并最终rollup到链上合约，以保证链上和链下数据的一致性。

了解更多：[deposit.md](main-features/deposit.md "mention")

### 提现 <a href="#withdraw" id="withdraw"></a>

用户发起提现的链下请求后，Operator会自动立即处理。这里需要强调，**DeGate中的提现不存在人工审核**。当包含了提现链下交易的zkBlock提交到链上区块后，用户就会收到所提现的资产。为了实现100%资产自托管的属性，DeGate协议提供了强制提现方法，强制提现实现了用户以**不受任何阻拦**的方式自主取回其存放在DeGate协议中资产的功能。用户可在链上发起强制提现，强迫Operator处理；如果Operator没有在预先规定的时间内处理，则整个DeGate协议的运行关停，DeGate协议进入逃离模式**。**

了解更多：[withdrawal.md](main-features/withdrawal.md "mention")

### 逃离模式

一旦进入逃离模式，用户可调用DeGate的智能合约，直接取回DeGate协议内的资产**。**DeGate智能合约会拒绝任何新的Rollup，所有链下请求将无法得到处理，所有DeGate账户和资产状态会停留在进入逃离模式前最后一次Rollup的状态**，**DeGate智能合约将以这个最后的状态来处置资产。为了取回资产，用户需解析DeGate合约所有Calldata数据来构建默克尔树，得到最新账户和资产状态，通过这些数据直接向DeGate智能合约取回资产。当然，解析最新账户和资产的状态，这件事可以委托第三方完成。

了解更多：[exodus-mode.md](concepts/exodus-mode.md "mention")

### 协议费用 <a href="#protocol-fees" id="protocol-fees"></a>

DeGate协议费用有**矿工费**和**手续费**两类。ZK-Rollup会产生成本，包括交易上链的矿工费和零知识证明计算成本。为了协议经济安全，用户需要承担链下交易的矿工费。协议收入来自订单成交时的手续费，订单Taker承担矿工费和交易手续费。所有产生费用都进入DeGate HomeDAO金库。

了解更多：[protocol-fees.md](concepts/protocol-fees.md "mention")

### 交易系统 <a href="#trading-system" id="trading-system"></a>

交易系统是订单簿交易的核心模块，主要包含了交易对、订单簿、撮合逻辑、订单记录等。全部链下请求先通过交易系统的校验，再交给Operator处理。订单撮合逻辑和中心化交易所一样，按照时间优先，然后价格优先顺序依次匹配。

### 币种和交易对 <a href="#token-and-pair" id="token-and-pair"></a>

**添加新资产和交易对无需人工审核**，任何人都可以在DeGate协议上架符合标准ERC20规范的资产。具体来说，发起者先向DeGate合约注册币种，然后在DeGate节点添加该币种的交易对，就能开启新的交易对。

目前协议开放的交易对计价币种包括ETH、USDC、USDT，即每个币种都可以添加3个不同交易对。

对于部分非标准的ERC20资产，比如转账燃烧和自动更新数量的币种，DeGate节点做相应的额外处理后也能支持上币和开通交易，但需要根据情况逐一评估和调整。

了解更多：[permissionless-listing.md](main-features/permissionless-listing.md "mention") [trading-pair.md](main-features/trading-pair.md "mention")

### 安全审计 <a href="#security-audit" id="security-audit"></a>

目前为止DeGate协议的电路逻辑和智能合约正在进行或已完成了至少两家专业安全团队的审计。查看[审计报告](https://github.com/degatedev/protocols/tree/degate\_mainnet\_beta/packages/loopring\_v3/security\_audit)。

### 可信配置(Trusted Setup) <a href="#trusted-setup" id="trusted-setup"></a>

DeGate协议部署到以太坊主网的时候，需要对电路与合约进行初始化设置，此过程因为会引入随机熵而被称作Trusted Setup。DeGate协议的Trusted Setup分为两个阶段

1. 引用[powers-of-tau](https://github.com/weijiekoh/perpetualpowersoftau/)的配置作为初始值。
2. 基于初始值，引入一个未来的比特币区块哈希，然后找5名社区成员各自输入随机熵，接着再引入另一个未来的比特币区块哈希，最终计算出Proving Key和Verifying Key，分别放入电路与合约。

参考资料：[Vitalik - How do trusted setups work?](https://vitalik.ca/general/2022/03/14/trustedsetup.html)

### DeGate节点 <a href="#degate-node" id="degate-node"></a>

目前DeGate协议的链下部分为单节点运行模式，由节点运营方负责。单节点可能出现故障或作恶的情况和应对方式如下：

1. **节点不处理链下请求。**为应对这种情况，用户可以发起强制提现取回资产，如果DeGate对于强制提现的链上请求都不处理，那么在预先规定的时间后，任何人都可以让DeGate协议进入逃离模式，之后用户可直接向DeGate智能合约提取属于自己的资产。
2. **订单簿成交抢跑(Frontrun)。**市价单保护价功能可将用户可能受到的抢跑损失限定较小的范围。
3. **代码安全风险：**开源与钱包和资产交互的代码并独立部署，供前端网站调用，确保资产操作过程不被恶意代码伪造。
4. **接口通信安全：**前端和后端之间调用接口时，通过约定的私钥签名验签来确保所通信数据没有被篡改。

### 更多特点 <a href="#more-features" id="more-features"></a>

为了使DeGate协议更加Trustless，降低用户成本和方便专业用户使用，还加入了以下功能：

* 链上追加取消订单
* 去中心化网格策略
* 聚合交易
* 转账方式充值（标准充值）
* 高级账户与交易私钥
* SDK工具和文档
* Shutdown模式

## 主要功能 <a href="#features" id="features"></a>

### 1. 兼容性 <a href="#compatible" id="compatible"></a>

DeGate网站可通过Web浏览器和移动浏览器访问，Web端支持Metamask插件钱包、WalletConnect协议和Ledger硬件钱包，Mobile端支持主流手机钱包和WalletConnect协议。

### 2. 账户管理 <a href="#manage-account" id="manage-account"></a>

管理DeGate账户就是管理资产私钥，包括新账户开通，每次登录时的解锁账户，重置和查看资产私钥。

### 3. 资产管理 <a href="#manage-asset" id="manage-asset"></a>

除了充值和提现，还可以进行DeGate账户间的内部转账。内部转账是一种链下请求，需要Rollup上链，但只要发起签名，就能立即完成向目标账户的转账，并且所需矿工费相比链上转账低得多。

### 4. 订单簿交易 <a href="#orderbook-trade" id="orderbook-trade"></a>

提供限价单和市价单两种下单模式。限价单适用于按指定价格成交的场景， 还具备Post-Only功能，可以只下Maker订单。市价单适合希望以订单簿目前最优价格快速成交的用户，DeGate具有价格滑点保护功能，避免订单簿深度不佳时的市价单扩大损失。

### 5. 免审核上币 <a href="#permissionless-listing-token" id="permissionless-listing-token"></a>

输入币种合约地址，发起链上合约调用，便可添加新资产。

### 6. 免审核添加交易对 <a href="#permissionless-add-pair" id="permissionless-add-pair"></a>

选择一个交易币种（Base Token）和一个计价币种（Quote Token），即可组成交易对，立即完成交易对添加并开始交易。

### 7. 网格策略 <a href="#grid-strategy" id="grid-strategy"></a>

DeGate协议以资产自托管的方式提供了网格策略的交易能力。与订单簿下单类似，用户会用资产私钥签名一个网格策略，DeGate节点验证后，订单簿会挂上初始网格订单。某一个网格订单被撮合成交后，电路验证该笔撮合符合用户的签名授权；当一个网格订单被完全成交后，DeGate节点会依照用户事先授权的签名来派生出一个新的网格订单，以此往复循环，实现完整的网格策略交易。网格策略的订单和普通交易使用同一个订单簿。

此外DeGate还提供了网格下单预览、图形化展示订单和近期成交、网格数据统计和历史明细等功能，便于用户了解自己的网格策略。

### 8. 流动性挖矿 <a href="#yield-farming" id="yield-farming"></a>

流动性挖矿是DeGate完成冷启动的重要途径，以保证交易对有足够的流动性来满足交易需求。以交易对为单位，用户创建同时符合资金条件和价格条件的网格策略，便能参与挖矿。挖矿奖励每隔15秒进行一次计算和分配。值得注意的是，该挖矿奖励独立于网格策略的做市收益，为用户额外得到的收益。

### 9. 历史记录 <a href="#history" id="history"></a>

DeGate协议还提供了账户的详细历史记录，包括充值、提现、转账历史，订单和成交历史，网格策略记录，账户活动等。
