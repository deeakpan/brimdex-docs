# Market Lifecycle

Every Brimdex market goes through clear phases from creation to payout.


## Phases

**Created → Live → Expired → Resolved**


## 1. Created

Right after creation, the market and its LP vault exist onchain, but **trading isn’t open** yet until initialization completes. In practice this is a short, automatic step users rarely think about.


## 2. Live

The market is **open for trading**:

- Primary **BOUND/BREAK** buys are available  
- **Orderbook** limit orders can be placed and matched  
- **LP deposits** are accepted while funding is open  
- Pool **prices update** with each primary buy  

This phase lasts until the **expiry time** shown in the UI.


## 3. Expired

After expiry:

- **No new** primary buys  
- **Orderbook** activity for that market stops  
- The system **prepares to resolve** the outcome using the oracle  

Automation finalizes resolution; you don’t press a “settle” button as a normal trader.


## 4. Resolved

Once finalization succeeds:

- **Winners** can **redeem** in the app for USDC  
- **LPs** can use the **vault exit** flow for fees + principal  
- Exceptional **recovery** paths may exist if resolution is delayed (see [Settlement](../how-it-works/settlement.md))


## What you can do when

| You want to… | Typical timing |
|---|---|
| Buy BOUND/BREAK on primary | While market is **live** (before expiry) |
| Trade on orderbook | While market is **live** |
| Add LP USDC | While vault accepts deposits (through settlement rules) |
| Redeem winning tokens | After market is **resolved** |
| Exit LP position | After **resolution**, via LP exit |

## Slot / uniqueness

Each live market occupies a **slot** (asset name + duration + band settings). Only one **active** market uses a given slot at a time; after it ends, a new one can be created for that slot.

Contract function names and timestamps live in [Builders](../builders/builder-overview.md) / [Factory](../contracts/brimdex-factory.md) docs.
