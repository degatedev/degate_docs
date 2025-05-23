# Security

## **Security of Wallet Address Keys**

Your wallet addresses' keys offer the same level of security as asset keys.

1. The DeGate protocol and degate.com do not and cannot access users’ wallet private keys.
2. Wallet address keys are temporarily stored in the browser’s local SessionStorage and are automatically cleared when the browser tab is closed. SessionStorage does not support cross-domain or cross-session access, which makes it secure.
3. DeGate has implemented a front-end security isolation strategy by splitting the front-end into "wallet codes" and "trade codes". The wallet and trade codes are isolated: wallet code handles the signature mechanism within an iframe, while trade code executes in a sandboxed environment, ensuring the keys and signatures are secure and inaccessible from the trade side. In the future, the core front-end code will be deployed on decentralized platforms to make it immutable, further enhancing private key security. \
   \
   For more info on secret keys and signatures, do visit [https://docs.degate.com/product\_en/concepts/secret-key-and-signatures](https://docs.degate.com/product_en/concepts/secret-key-and-signatures)&#x20;
