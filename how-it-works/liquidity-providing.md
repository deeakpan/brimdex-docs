# Liquidity Providing

Liquidity providers **seed** each market with USDC so the parimutuel pool can start near a **50/50** price. You do this through the **LP** section of the app: pick an **active** market, review the band and time to resolution, then **deposit** USDC into that market’s vault when funding is still open.

## No directional bet

LPs are **not** choosing BOUND vs BREAK. Seed USDC is split across both sides of the pool so the market can open fairly. When the market settles, **your seed principal is returned** through the vault flow regardless of which side won.

Your upside is the **streaming fee**: **0.2% of each primary buy** is directed to stabilizing / rewarding seed liquidity (see [Fees](fees.md) for how that fits next to the treasury share).

## In the app

1. Open **LPs** (or the LP entry point in the product).
2. **Filter** by asset or duration if you want, then **select an active market** from the picker.
3. Review **time to resolution**, **price bounds**, and **reference spot** so you know what you’re backing.
4. **Enter a USDC amount** and **deposit** while the vault is still accepting funding. Your wallet will ask you to **approve USDC** for the vault, then to **confirm the deposit**.
5. After settlement, use **Exit** (or the equivalent control) **once** to claim **accumulated fees** and **your principal share**—the app batches that for you.

You can **add more** USDC later while the market is active; the UI reflects your combined position.

## What you’re not doing

You’re not “picking the winner.” You’re helping **bootstrap and stabilize** the market; returns come from the **fee stream**, not from guessing the outcome.

## Deeper protocol math

Share pricing, NAV, and onchain fee indexing are implementation details. If you’re **building** on top of Brimdex or auditing contracts, see [Market liquidity vault](../contracts/market-liquidity-vault.md) and the [Builders overview](../builders/builder-overview.md).
