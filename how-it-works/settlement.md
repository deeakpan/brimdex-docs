# Settlement

When the **expiry time** passes, the market **stops taking new primary buys** and the protocol **finalizes the outcome** using the live oracle price. You don’t run a separate “settle” action in the app as a trader—the network keeps this automated so winners can redeem.

## Who wins?

- **BOUND** wins if the final oracle price is **on or inside** the market’s lower and upper bounds.
- **BREAK** wins if the final price is **below the lower bound** or **above the upper bound**.

## What happens to payouts

The **trader pool** (the USDC from traders, after the usual fees on buys) is shared among **holders of the winning token**. Seed liquidity is handled separately so LPs get their principal back through the LP flow, not as a directional bet.

If you hold **winning** tokens after settlement, the app lets you **redeem**: you sign a transaction and USDC returns to your wallet. Partial redemptions are fine—you choose how many tokens to cash in.

## Oracle freshness

Finalization needs a **recent** oracle reading. If data is temporarily stale, settlement may wait until a fresh price is available; the app will still show the market as pending resolution until that completes.

## Liquidity providers

After settlement, LPs use the **LP / vault** flow in the app to **exit once** and receive accumulated fees plus their share of returned principal. See [Liquidity providing](liquidity-providing.md).

## If something goes wrong

If settlement were **unable to complete** for an extended time after expiry, the protocol includes a **last-resort path** for traders to recover a **pro-rata share** of trader funds (not a “winning” payout). This is rare; the UI or docs will reflect the current product behavior if that path is exposed.

## Integrators & builders

Automation, onchain settlement and redeem methods, emergency paths, and exact accounting are documented in [Brimdex Market](../contracts/brimdex-market.md) and the [Builders](../builders/builder-overview.md) section.
