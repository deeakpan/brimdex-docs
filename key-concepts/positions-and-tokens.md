# Positions & Tokens

Every position on Brimdex is represented by an ERC-20 token. When you buy, tokens are minted to your wallet. When you redeem or sell, they are burned or transferred.


## BOUND and BREAK tokens

Each market deploys two separate ERC-20 tokens:

| Token | Wins when | Symbol example |
|---|---|---|
| **BOUND** | Final price is inside the band | `BOUND-BTC-1H` |
| **BREAK** | Final price is outside the band | `BREAK-BTC-1H` |

Both tokens share the same collateral (USDC) and market contract. They use **6 decimals**, matching USDC precision.


## Minting

Tokens are minted by the `BrimdexMarket` contract when you call `buyBound()` or `buyBreak()`. The quantity is determined by the pool price at the time of your transaction:

```
tokens = netUSDC / price
```

You cannot mint tokens directly — all minting goes through the market's buy functions.


## Burning

Tokens are burned in two scenarios:

1. **Redeem after settlement** — winning tokens are burned and USDC is sent to you
2. **Emergency withdrawal** — unsettled tokens can be burned to recover pro-rata trader USDC after settlement delay passes (12h past expiry)


## Transferability

BOUND and BREAK tokens are standard ERC-20s — fully transferable. You can:

- Send them to another wallet
- List them on the `BrimdexOrderBook`
- Hold them in any ERC-20-compatible wallet


## Viewing your position

Your position is simply your token balance:

```solidity
boundToken.balanceOf(yourAddress)   // BOUND position
breakToken.balanceOf(yourAddress)   // BREAK position
```

Token addresses per market are registered in `BrimdexFactory`:

```solidity
factory.marketToBoundToken(marketAddress)
factory.marketToBreakToken(marketAddress)
```


## After settlement

Once the market settles:
- **Winning tokens** can be redeemed for USDC at the `redemptionRate`
- **Losing tokens** have zero value and cannot be redeemed
- Unredeemed winning tokens remain redeemable indefinitely — there is no expiry on redemption
