# Cross-chain Add/Send Feature

DeGate's cross-chain add and transfer function utilizes a cross-chain bridge managed by a Trusted Execution Environment (TEE), designed to provide users with a fast and secure way to add funds from and send funds to different blockchains. This mechanism enables users to transfer assets between blockchains more efficiently, reducing complexity and costs.

### Supported Assets and Chains for Cross-Chain Functionality <a href="#id-kua-lian-hua-ru-fa-song-gong-neng-dui-wai-wen-dang-biao-shu-supportedassetsandchainsforcrosschain" id="id-kua-lian-hua-ru-fa-song-gong-neng-dui-wai-wen-dang-biao-shu-supportedassetsandchainsforcrosschain"></a>

| Asset         | Supported Chains (Add Funds) | Supported Chains (Send) |
| ------------- | ---------------------------- | ----------------------- |
| ETH           | Arbitrum One, Optimism       | Arbitrum One            |
| USDC (Native) | Arbitrum One, Optimism       | Arbitrum One            |
| USDT          | Arbitrum One, Optimism       | Arbitrum One            |



**Q: Are there limits on add funds and transfers?**\
**A:** Yes, limits are based on the current capacity of the cross-chain bridge. The maximum limit is shown during the transaction.

**Q: Are funds in my DeGate balance still trustless?**\
**A:** Yes, funds in DeGate remain trustless, secured by zero-knowledge rollups on Ethereum mainnet. During cross-chain transactions, typically in seconds funds are temporarily custodied by the bridge service.

**Q: Why hasn't my added funds arrived and why does it show a "failed" status?**\
**A:** You can create a support ticket on Discord, and our team will assist you.

\
