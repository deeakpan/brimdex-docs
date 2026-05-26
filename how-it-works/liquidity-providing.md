# Liquidity & Vaults

Liquidity in Brimdex starts with a **launch vault**.

Instead of dropping a market live with no depth, Brimdex collects commitments first and then opens the market once the target is met.

## What LPs are doing

LPs are:

- committing USDC before market open
- bootstrapping the launch target
- underwriting the market maker once it goes live
- earning a share of fees according to the fee model

## What LPs are not doing

LPs are not choosing BOUND or BREAK directly.

They are backing the market infrastructure, not taking one explicit trader side.

That said, LP capital is still **at risk**. Brimdex LPs are not guaranteed full principal on every market.

## The launch vault flow

1. A launch vault is created for a specific market template.
2. Users commit USDC and receive commitment tokens.
3. If the vault reaches target, the market opens on Somnia.
4. If the target is missed, the vault can be unwound and commitments can be redeemed.
5. After settlement, LPs redeem based on their share of the resolved vault.

## Why seed size matters

Seed size controls two things at once:

- trader execution quality
- LP bankroll exposure

Small seed:

- gives thinner depth
- causes larger price jumps
- limits absolute capital at risk

Large seed:

- improves fills
- supports larger trades
- increases LP exposure if the market ends up imbalanced

## How LP return is formed

LP return comes from the final resolved state of the vault, which depends on:

- fee capture
- how much trading occurred
- whether order flow was balanced or one-sided
- the final settlement outcome

So LP returns are not fixed and should not be documented as guaranteed principal plus yield.

## Why commitment tokens matter

Commitment tokens are the LP-side accounting unit:

- they represent your share of the launch vault
- they let the protocol track proportional redemption after settlement
- they separate LP accounting from trader outcome tokens

See [Positions & Redemptions](../key-concepts/positions-and-tokens.md) for the difference between trader positions and LP claim tokens.
