# 私钥和签名

DeGate协议需要用到两种签名方式

* ECDSA（椭圆曲线数字签名算法）是DSA（数字签名算法）的椭圆曲线实现。椭圆曲线密码术能够以较小的密钥提供与RSA相对相同的安全级别。[了解更多>](https://en.wikipedia.org/wiki/Elliptic\_Curve\_Digital\_Signature\_Algorithm)
* EdDSA（爱德华兹曲线数字签名算法）是一种使用基于扭曲爱德华兹曲线的Schnorr签名变体的数字签名方案。签名创建在EdDSA中是确定性的，其安全性是基于某些离散对数问题的难处理性，因此它比DSA和ECDSA更安全，后者要求每个签名都具有高质量的随机性。[了解更多>](https://en.wikipedia.org/wiki/EdDSA)

## 资产私钥

资产私钥是用户通过以太坊钱包私钥签名生成的EdDSA私钥，用于发起DeGate内各种操作请求。用户登录DeGate账户时需要先解锁账户，即派生出资产私钥，临时存放在本地浏览器的session中。

<figure><img src="../.gitbook/assets/Screen Shot 2022-10-21 at 14.43.51.png" alt=""><figcaption><p>ECDSA和EdDSA签名关系</p></figcaption></figure>

ECDSA签名需要用户在钱包确认，例如下图MetaMask网页插件。

![](<../.gitbook/assets/Screen Shot 2022-08-18 at 12.51.47 PM.png>)

## ECDSA签名类型

DeGate协议支持3种ECDSA的签名和验签方式

1. 开放式签名(ETH\_Sign)
2. 结构化签名(EIP-712)：[https://eips.ethereum.org/EIPS/eip-712](https://eips.ethereum.org/EIPS/eip-712)
3. 智能合约支持(EIP-1271)：[https://eips.ethereum.org/EIPS/eip-1271](https://eips.ethereum.org/EIPS/eip-1271)

### 用户请求与签名

节点同时验证ECDSA签名和EdDSA签名，电路仅验证EdDSA签名，合约仅验证ECDSA签名

| 操作请求             | 用户发起的签名类型   | 验签方            |
| ---------------- | ----------- | -------------- |
| 开通账户             | ECDSA       | 节点 -> 合约       |
| 重置资产私钥           | ECDSA       | 节点 -> 合约       |
| 解锁账户             | ECDSA       | 节点             |
| 提现               | ECDSA+EdDSA | 节点 -> 电路 -> 合约 |
| 转账               | ECDSA+EdDSA | 节点 -> 电路       |
| 创建订单             | EdDSA       | 节点             |
| 创建网格策略           | EdDSA       | 节点             |
| 订单成交             | 下单时的EdDSA签名 | 电路             |
| 注册交易对            | ECDSA+EdDSA | 节点 -> 电路       |
| 付费入账:digit\_one: | ECDSA+EdDSA | 节点 -> 电路       |
| 取消订单             | EdDSA       | 节点             |
| 链上取消订单           | ECDSA+EdDSA | 节点 -> 电路       |
| 链上取消网格策略         | ECDSA+EdDSA | 节点 -> 电路       |
| 领取挖矿奖励           | ECDSA+EdDSA | 节点 -> 电路       |

注:digit\_one:：付费入账支持通过钱包支付与DeGate账户支付，此处表示后者情况

### 签名有效期

提交请求的ECDSA和EdDSA签名中都加入了**有效期(ValidUntil)**字段，验签时，首先判断签名是否在有效期内，才会继续执行。

## 生成和更新资产私钥

开通账户时要完成两次ECDSA签名，第一次签名后生成资产私钥，签名内容包含了DeGate智能合约地址与KeyNonce。KeyNonce初始为1，之后每次重置账户都会加1，由DeGate节点链下存储。

{% code overflow="wrap" %}
```markup
Sign this message to access DeGate Exchange: 0xdac304791B7f53593C701980aa52087Ed7EC6649 with key nonce: 1
```
{% endcode %}

第二次签名会提交`AccountUpdate`请求，用来关联钱包地址、AccountID、资产私钥对应的公钥，这些数据会通过零知识证明，同时更新到默克尔树，最后提交到智能合约进行验证。

{% code overflow="wrap" %}
```
owner: 0x8465f0641187132873Dc204366C125CcCB1f591F
accountID: 13
feeTokenID: 9
maxFee: 224000000000000000
publicKey: 19751969071188309383411147255314514902438722385019108049538486649726264961725
validUntil: 4294967295
nonce: 1
```
{% endcode %}

重置资产私钥的过程与开通账户一样，区别在于每次KeyNonce+1。

## 私钥安全

1. DeGate协议和degate.com不会访问也无法访问用户的以太坊钱包私钥。
2. 资产私钥临时保存在本地浏览器SessionStorage，关闭浏览器标签时会自动清除。SessionStorage不支持跨域名和跨Session访问，所以是安全的。
3. DeGate实施了前端安全隔离方案，将前端网站拆分成「前端普通代码」和「前端核心代码」。前端核心代码用于和以太坊钱包互动，调用资产私钥进行签名，并与前端普通代码通信。而前端普通代码只负责站点功能，无法直接访问私钥。未来计划将前端核心代码部署到去中心化的平台服务之上，使其不可更改，进一步提升私钥安全性。

{% hint style="warning" %}
**请保护好你的私钥**

如果用户的资产私钥遭到泄露，虽然攻击者无法直接提现和转账，但可以在DeGate交易所上用非常低的价格出售用户的资产，并作为交易对手方来获利。

如果你认为资产私钥已经泄露，请立即使用「重置资产私钥」功能，这样已泄露的私钥就会失效。
{% endhint %}
