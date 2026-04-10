# MarketLiquidityVault

Per-market LP vault. Accepts USDC deposits, seeds the market, accumulates streaming fees, and returns principal at settlement.

**Source:** [`MarketLiquidityVault.sol`](https://github.com/deeakpan/Brimdex-contracts/blob/main/MarketLiquidityVault.sol)


## Key functions

### `deposit(usdcAmount)`
Deposit USDC into the vault. Mints shares at current NAV. Open before and during the active epoch.

### `exit()`
After market settlement only. Burns all your shares and sends:
- Accumulated fee earnings
- Pro-rata share of returned seed principal


## Share pricing

```
mintShares = usdcAmount × totalShares / totalNAV
totalNAV   = vaultBalance + totalDeployed
```

`totalDeployed` tracks USDC currently in the market (not yet returned), so NAV is accurate at all times.


## Fee distribution

```solidity
// Called by market on each trade
accRewardPerShare += (feeAmount × PRECISION) / totalShares;
```

Your pending fees:
```
live    = (shares × accRewardPerShare / PRECISION) − rewardDebt
total   = live + pendingFeeCredit
```

`pendingFeeCredit` accumulates harvested fees from re-deposits — guarantees no fees are lost when adding to your position.


## Key state

| Variable | Description |
|---|---|
| `targetSeed` | USDC required to seed the market (immutable) |
| `seedFinalized` | True after seed has been pulled to market |
| `totalShares` | Sum of all LP shares |
| `sharesOf` | LP address → share balance |
| `accRewardPerShare` | Global fee reward index |
| `rewardDebt` | LP address → fee debt checkpoint |
| `pendingFeeCredit` | LP address → harvested unclaimed fees |
| `principalBalance` | Returned seed USDC awaiting LP exit |
| `totalDeployed` | USDC in market not yet returned |


## View functions

| Function | Returns |
|---|---|
| `pendingFees(user)` | Unclaimed fee USDC |
| `principalShareUsdc(user)` | Pro-rata principal share |
| `totalExitUsdc(user)` | Total USDC on exit |
| `totalNAV()` | Current vault NAV |
