# Market Lifecycle

Every Brimdex market moves through a fixed sequence of states.


## States

```
DEPLOYED → ACTIVE → EXPIRED → SETTLED
```


## 1. Deployed

The factory has deployed the market and its vault. The market is not yet open for trading.

This state is invisible to most users — it is an internal factory step that completes in the same transaction as market creation.


## 2. Active

The market is open for trading. This begins the moment `BrimdexFactory.createMarket()` completes.

During the active state:
- `buyBound()` and `buyBreak()` are available
- Orderbook orders can be placed and matched
- LP deposits into the `MarketLiquidityVault` are accepted
- Pool prices update with every trade

The active state ends at `expiryTimestamp`.


## 3. Expired

`block.timestamp >= expiryTimestamp`.

- No new primary market buys accepted
- Orderbook trading stops
- Settlement is now callable

The protocol keeper calls `settle()`. The contract reads the oracle price and resolves the outcome. Oracle price must be fresh (within 5 minutes).


## 4. Settled

`settle()` has been called and succeeded.

- Winners can call `redeem()` to collect USDC
- LPs can call `vault.exit()` to collect fees + principal
- `emergencyWithdraw()` is available as a fallback for edge cases (12h after expiry if settlement has not occurred)


## Timing summary

| Action | Available when |
|---|---|
| `buyBound / buyBreak` | Active (before expiry) |
| Orderbook orders | Active |
| `settle()` | Expired |
| `redeem()` | Settled |
| `vault.exit()` | Settled |
| `emergencyWithdraw()` | 12h past expiry, not yet settled |
| `vault.deposit()` | Before settlement (active + expired) |


## Market slot

Each market occupies a **slot** — a unique combination of `name + timeframeDuration + bandPercent`. Only one active market can occupy a slot at a time. Once a market in that slot settles or expires, a new one can be created for the same slot.
