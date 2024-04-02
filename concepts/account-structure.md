# 账户体系

用户通过以太坊钱包访问DeGate协议，首次使用前要开通DeGate账户，将账户权限与钱包地址绑定。

<figure><img src="../.gitbook/assets/Screen Shot 2022-11-28 at 12.03.23.png" alt=""><figcaption><p>完整树的账户节点</p></figcaption></figure>

以完整树的Account节点为例，每个Account节点表示了一个DeGate账户，其中存储了钱包地址(owner)，资产公钥(publicKeyX和publicKeyY)，交易公钥(appKeyX和appKeyY)，账户Nonce(nonce)，交易私钥权限(disableAppKeySpotTrade/Withdraw/TransferToOther)以及根数据(balanceRoot和storageRoot)。Account节点共$$4^{16}$$​个，因此DeGate协议支持约42亿个账户。每个DeGate账户按照顺序分配AccountID，从0开始以整数递增。0和1保留，用户账户从2开始。

为钱包地址分配AccountID，就可以用数字来表示很长的地址，这样能减少零知识证明的成本。**对用户来说，无需了解AccountID**，只要以相应的钱包访问DeGate就能使用了。无论提现还是转账，用户输入钱包地址完成操作。

### 账户Nonce和KeyNonce

默克尔树Account节点内也有Nonce，称为「账户Nonce」。目前为止，我们已经了解到两个Nonce概念：账户Nonce和[KeyNonce](signature-and-secret-key.md#sheng-cheng-he-geng-xin-zi-chan-si-yao)，两者比较如下

<table><thead><tr><th width="100">区别点</th><th>账户Nonce</th><th>KeyNonce</th></tr></thead><tbody><tr><td>存储位置</td><td>默克尔树的账户节点</td><td>DeGate节点链下存储</td></tr><tr><td>规则</td><td>从0开始，每执行1次AccountUpdate或AppKeyUpdate需要加1</td><td>从1开始，每次重置加1</td></tr><tr><td>校验方</td><td>电路</td><td>DeGate节点</td></tr><tr><td>作用</td><td>作为账户的EdDSA密钥权限更新操作的顺序，避免重放。类似以太坊交易的nonce。</td><td>用于生成不同的EdDSA私钥</td></tr></tbody></table>

{% hint style="info" %}
**如果DeGate节点弄丢了最新的KeyNonce，会有什么影响？**

用户每次解锁账户时，都需要从节点获取最新的KeyNonce，以便生成正确的资产私钥。如果没有KeyNonce，那就需要用户从1开始签名，与默克尔树账户节点内的Key进行比对，直到匹配后就能找出最新的KeyNonce。因此丢失KeyNonce不会导致资产丢失或无法访问。
{% endhint %}

### 账户资产

<figure><img src="../.gitbook/assets/Screen Shot 2022-11-28 at 12.14.02.png" alt=""><figcaption><p>账户节点下的资产节点</p></figcaption></figure>

账户里还需要有资产才能在DeGate进行交易。将代币从钱包充值到DeGate账户，或从其他DeGate账户转账过来都可以。充值进入协议的资产都存放在DeGate智能合约，每笔充值都需要通过零知识证明来确认，同时更新到默克尔树种相应的DeGate账户节点下面的资产节点。

换句话说，在DeGate内没办法直接用钱包资产，需要先充值再使用。用完后需要提现才能回到钱包。充值和提现虽带来一些门槛，但相应的好处就是下单和撤单可以做到瞬时和免费，对长期交易和专业交易用户非常友好。

另外，部分需要矿工费的操作，也要以账户资产支付。

DeGate协议层规定了只能通过钱包私钥和资产私钥的签名授权来操作账户资产，用户应自行做好安全防范。
