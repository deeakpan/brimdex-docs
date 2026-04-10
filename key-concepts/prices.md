# Prices

Brimdex uses a **parimutuel pricing model** — prices are derived entirely from pool ratios and update automatically with every trade. There is no order book for the primary market, no spread, and no liquidity requirement from a counterparty.


## The formula

```
BOUND price = boundPool / (boundPool + breakPool)
BREAK price = breakPool / (boundPool + breakPool)
```

These always sum to exactly **1.0**. Think of them as implied probabilities — if BOUND is priced at 0.65, the market implies a 65% chance the price stays in the band.


## Starting price

Both pools are seeded equally at market creation:

```
boundPool = seedPrincipal / 2
breakPool = seedPrincipal / 2
```

This gives a 50/50 starting price — no directional bias at open.


## How a buy moves the price

When a trader buys BOUND with $X USDC (after the 2% fee):

```
netToPool = X × 0.98
tokens    = netToPool / price_before
boundPool += netToPool
```

The new BOUND price is now higher (more USDC in the bound pool), and BREAK price falls correspondingly. Each buy shifts the ratio.


## Example

| State | boundPool | breakPool | BOUND price | BREAK price |
|---|---|---|---|---|
| After seed | $10 | $10 | 0.50 | 0.50 |
| After $20 BOUND buy | $29.60 | $10 | 0.748 | 0.252 |
| After $10 BREAK buy | $29.60 | $19.80 | 0.599 | 0.401 |

> Pool values above are net of fees for illustration.


## Token quantity

The number of tokens you receive for a given USDC amount:

```
tokens = netToPool / price
```

At a BOUND price of 0.50 with $100 net USDC, you get 200 BOUND tokens.
At 0.75, the same $100 net buys you ~133 BOUND tokens.


## Slippage

Every buy changes the pool ratio. Large trades move the price more. The router exposes a `minTokensOut` parameter on every buy — if the pool moves before your transaction lands and you'd receive fewer tokens, the transaction reverts.


## Redemption price

At settlement, the winner's redemption rate is:

```
redemptionRate = traderPool / winningTokenSupply
```

Where `traderPool = totalPool − seedPrincipal`. This means LPs' seed never participates in the winner/loser split — only the net trader USDC flows to winners.
