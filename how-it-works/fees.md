# Fees

Brimdex has two separate fee structures — one for the primary parimutuel market, one for the secondary orderbook.


## Primary market fees (parimutuel)

Every buy on the primary market incurs a **2% fee on gross USDC**.

| Recipient | Rate | Basis points |
|---|---|---|
| Treasury | 1.8% | 180 bps |
| LP Vault (streaming) | 0.2% | 20 bps |
| **Total** | **2.0%** | **200 bps** |

**Net USDC entering the pool:**

```
netToPool = grossUsdc × (1 − 0.018 − 0.002) = grossUsdc × 0.98
```

The LP vault fee is streamed per trade and distributed to all vault depositors proportionally via the reward index.


## Orderbook fees

The `BrimdexOrderBook` charges a flat fee on each side of a matched trade:

| Side | Rate |
|---|---|
| Buyer | 1.5% of matched notional |
| Seller | 1.5% of matched notional |

**Buyer deposits:** `notional + 1.5%` upfront into escrow
**Seller receives:** `notional − 1.5%` on fill

Both fee portions go to the protocol treasury.


## Settlement fees

None. The entire trader pool (total USDC minus seed) goes to winners with no protocol skim in the normal settlement path.

**Exception:** If one side has zero tokens and the other side loses, the orphaned trader pool is sent to the treasury. This is an extreme edge case.


## Fee summary table

| Action | Fee | Goes to |
|---|---|---|
| `buyBound` / `buyBreak` | 2% of trade | 1.8% treasury + 0.2% LP vault |
| Orderbook buy fill | 1.5% of notional | Treasury |
| Orderbook sell fill | 1.5% of notional | Treasury |
| `settle()` / `redeem()` | 0% | — |
| `vault.exit()` | 0% | — |
