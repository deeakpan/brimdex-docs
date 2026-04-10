# Settlement

When a market expires, the protocol keeper calls `settle()`. The contract reads the oracle price, determines the winner, and sets the redemption rate. Winners call `redeem()` to collect their USDC.

## Triggering settlement

```solidity
market.settle();
```

Requirements:
- `block.timestamp >= expiryTimestamp`
- Oracle price is fresh (within 5 minutes of `block.timestamp`)

## Oracle price check

The `BrimdexFeeds` contract provides the final price. The market normalises it to 6 decimal USDC precision:

```solidity
if (priceData.decimals >= 6)
    finalPrice = priceData.price / 10^(decimals - 6)
else
    finalPrice = priceData.price × 10^(6 - decimals)
```

If the oracle data is stale (older than 5 minutes), `settle()` reverts and must be called again when fresh data is available.

## Outcome determination

```
BOUND wins if: lowerBound ≤ finalPrice ≤ upperBound
BREAK wins if: finalPrice < lowerBound OR finalPrice > upperBound
```

## Redemption rate calculation

```
traderPool     = totalPool − seedPrincipal
redemptionRate = traderPool / winningTokenSupply
```

The seed is excluded — LPs get their principal back separately. Only the net USDC deposited by traders flows to winners.

**Edge case:** If all tokens are on one side and that side loses, the trader pool goes to the treasury (no winners to pay).

## Redeeming winnings

```solidity
market.redeem(isBound, tokenAmount);
```

```
payout = tokenAmount × redemptionRate / 1e18
```

Winning tokens are burned. USDC is sent to your wallet. Partial redemptions are supported.

## LP settlement

After settlement, seed principal is automatically transferred to the `MarketLiquidityVault` before `settle()` returns. LPs call `vault.exit()` to collect fees and principal.

## Emergency withdrawal

If the oracle is persistently unavailable and `settle()` cannot succeed, traders can recover their USDC 12 hours after expiry:

```solidity
market.emergencyWithdraw(isBound, tokenAmount);
```

This returns the trader's pro-rata share of trader-only funds (seed excluded). It is a last resort and does not pay winning odds.
