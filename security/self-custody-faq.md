# Self-Custody FAQ

Self-custody means your keys, and therefore your assets, are controlled by you rather than held in an account by a company. This page answers the questions people actually ask before trusting a self-custody wallet.

**Who controls my keys?**
You do. Keys are generated and used on your device. The DeGate protocol and degate.com do not and cannot access users' wallet private keys. The derivation mechanism is documented in [Wallet Addresses & Networks](../getting-started/wallet-address-and-networks.md).

**Can DeGate move, freeze, or seize my funds?**
No. Your assets sit at blockchain addresses that only your key can sign for. There is no custodial account layer in between.

**What happens to my assets if DeGate shuts down?**
Your assets live on the blockchains themselves, at addresses derived from your key via open standards (BIP39/BIP44), not on DeGate's servers.

> ⚠️ [NEEDS VERIFICATION: the exact user-facing recovery path per wallet type (email wallet vs. created vs. imported), e.g. recovery-phrase export, so this answer can state concretely how a user would restore access with third-party tools.]

**What do I need to back up?**
It depends on how you created the wallet. If you created or imported a wallet with a recovery phrase, back up that phrase offline. For email wallets:

> ⚠️ [NEEDS VERIFICATION: email-wallet backup and recovery model.]

**How is this different from keeping assets on an exchange?**
With an exchange account, the exchange holds the assets and your balance is a claim on the operator. With a self-custody wallet, you hold the assets directly on-chain. The practical trade-off: self-custody removes counterparty risk from the operator, and in exchange you carry the responsibility for your own backup.

**Is self-custody harder to use?**
It historically involved more manual work (gas tokens, bridging, one wallet per chain). Removing that overhead while keeping the keys with you is the specific problem DeGate is built around.

**If I lose my device, are my assets gone?**
Not if you have your backup (see above). Your assets are on-chain; the device only holds keys, and keys can be restored from backup on a new device.
