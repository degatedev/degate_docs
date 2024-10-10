# 跨链划入发送功能

DeGate 的跨链划入发送功能利用由一个可信执行环境 (TEE) 管理的跨链桥，旨在为用户提供一种快速、安全的方式，从不同区块链充值和提取资金。通过这种机制，用户可以更高效地在不同区块链之间转移资产，降低了复杂性和成本。

当前跨链功能支持的资产和链

<table><thead><tr><th width="188">资产</th><th width="256">已支持划入的链</th><th>已支持发送的链</th></tr></thead><tbody><tr><td>ETH</td><td>Arbitrum One， Optimism</td><td>Arbitrum One</td></tr><tr><td>USDC(Native)</td><td>Arbitrum One， Optimism</td><td>Arbitrum One</td></tr><tr><td>USDT</td><td>Arbitrum One， Optimism</td><td>Arbitrum One</td></tr></tbody></table>



### FAQ

Q: 可以划入和发送的资金有限额么？

A: 是的，会根据当前跨链桥能够支持服务的能力决定，用户可以在使用功能是看到最大限额。\


Q: 用户在DeGate余额中的资金仍然是去信任的么？

A: 用户在DeGate的资金仍然是去信任的，仍由以太坊主网作为DA的zkrollup进行保护，仅当跨链订单进行中的极短时间内，用户的跨链资金由跨链桥服务进行操作。\


Q: 为什么我的划入没有到账，显示状态失败？

A: 可以创建 discrod 工单进行，由客服协助处理

