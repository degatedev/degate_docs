# Turbo Range

Turbo Range lets you deposit xStocks pairs into AMM liquidity pools with a single click, aiming for capital efficiency through a simplified interface.

* **Raydium pool integration.** DeGate serves as a streamlined front-end terminal for Raydium's pools. You access that liquidity directly inside the DeGate interface, without navigating to external platforms.
* **Multi-chain USDC deposits.** Leveraging DeGate's multichain system, you can deposit USDC from any supported chain instantly. The system manages balances across networks, so there is no manual bridging.

_Example: you can use USDC from any chain and open a Turbo Range position in a few clicks._

![](<../.gitbook/assets/unknown (2).jpeg>)![](<../.gitbook/assets/unknown (3).jpeg>)

## Security

The Solana program that powers Turbo Range's liquidity management (the Solana LP Handler, a wrapper around Raydium CLMM flows) has been independently audited. See [Audits](../security/audits.md).

## FAQ

**What am I actually depositing into?**
Raydium concentrated-liquidity (CLMM) pools on Solana, accessed through DeGate's interface. Positions carry the usual risks of providing AMM liquidity, including impermanent loss when the pair's prices diverge.

**Do I need funds on Solana first?**
No. You can fund a position with USDC from any supported chain; DeGate handles the routing.
