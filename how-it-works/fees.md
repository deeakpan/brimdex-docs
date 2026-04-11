# Fees

Brimdex has two fee contexts: the **primary market** (parimutuel buys) and the **orderbook** (peer-to-peer limit trades).


## Primary market fees (parimutuel)

Every **buy** on the primary market pays **2% of the USDC you spend**:

| Recipient | Rate |
|---|---|
| Protocol treasury | 1.8% |
| Seed LP vault (streaming) | 0.2% |
| **Total** | **2.0%** |

So about **98%** of what you spend becomes **net liquidity** in the pool after that fee. The **0.2%** portion **stabilizes and rewards** seed LPs over time; see [Liquidity providing](liquidity-providing.md).


## Orderbook fees

On the **orderbook**, each **matched** trade pays **0.5% of the matched notional** on the **buy side** and **0.5%** on the **sell side**. The app shows what you’re depositing or receiving so you can see fees before you confirm.


## Settlement

**No extra protocol skim** on the trader pool in the normal settlement path—the winning side redeems against that pool.

**Rare edge case:** if essentially all activity is on one token side and that side **loses**, there may be no natural winners; in that situation protocol rules can route stranded trader funds to the treasury. This is exceptional.


## Fee summary

| Action | Fee | Goes to |
|---|---|---|
| Primary buy (BOUND or BREAK) | 2% of spend | Treasury + LP vault stream |
| Orderbook buy fill | 0.5% of matched notional | Protocol |
| Orderbook sell fill | 0.5% of matched notional | Protocol |
| Settlement / redeem / LP exit | **0%** protocol fee on those steps | — |

For contract-level detail, see [Builders overview](../builders/builder-overview.md) and the [orderbook](../contracts/brimdex-orderbook.md) / [market](../contracts/brimdex-market.md) references.
