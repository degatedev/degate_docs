# Cross-chain Swap

Use a cross-chain swap to trade supported assets on different networks without arranging a separate bridge transfer first. Buy tokens with USDC or sell supported tokens for USDC, then review the route and expected output before signing.

* **One swap flow.** Choose the token and amount in Trade. Review the route, expected output, price impact, and costs before confirming.
* **Solver-based routing.** Available routes use integrated cross-chain protocols.
* **Wallet authorization.** You review and authorize the transaction from your selected wallet. Key handling and recovery depend on your [wallet type](../security/security-overview.md).
* **Network fees.** Non-hardware accounts can pay network costs for supported actions from eligible asset balances. Hardware accounts need native gas tokens at their hardware address. See [Fees](../fees.md).

## What it replaces

You do not need to arrange a separate bridge transfer before a supported cross-chain swap in the app. Routing and bridging are included in the swap flow. Available routes and completion times depend on the networks and protocols involved.

## Fees

Ordinary swaps have a DeGate platform fee of 0% for stablecoins and 0.02% for other tokens traded against USDC, as of August 2026. Network fees and the execution price also affect the amount you receive. See [Fees](../fees.md).

## FAQ

**Do I need to bridge before swapping?**
No separate bridge step is needed for a supported cross-chain swap. Choose the destination token, then review the quoted route before signing.

**Does DeGate take custody of my funds during the swap?**
You authorize the transaction from your selected wallet after reviewing the route and quote. Execution uses the protocols shown in the route. Key handling and recovery differ by wallet type; see [Security Overview](../security/security-overview.md) before choosing how to add a wallet.
