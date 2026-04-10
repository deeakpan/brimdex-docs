# Liquidity Providing

Liquidity Providers (LPs) seed each market with USDC through the `MarketLiquidityVault`. This bootstrap liquidity creates the initial 50/50 pool, enabling the market to open with a fair starting price.


## No directional risk

LPs do **not** take a bet on BOUND or BREAK. The seed USDC is split equally between both pools — it is neutral. At settlement, the seed principal is returned in full regardless of which side wins.

The LP's incentive is entirely from **streaming fees**, not from the market outcome.


## How it works

### 1. Deposit USDC

```solidity
vault.deposit(usdcAmount);
```

You can deposit before or during the active epoch. Deposits are open until the market settles. Share pricing is NAV-based — you pay the current value of the vault per share, so latecomers don't get a free ride.

### 2. Earn streaming fees

Every primary market trade sends **0.2% of the gross trade amount** to the vault. This is distributed proportionally to all LP shares via a reward index (`accRewardPerShare`). You earn from the moment your deposit lands, on all future trades.

### 3. Exit after settlement

```solidity
vault.exit();
```

One transaction pays out:
- All accumulated fee earnings (from your deposit timestamp onwards)
- Your pro-rata share of the returned seed principal


## Share pricing

Shares are priced at vault NAV:

```
mintShares = depositAmount × totalShares / totalNAV
totalNAV   = vaultUSDC + deployedPrincipal
```

`deployedPrincipal` is the seed USDC currently sitting in the market (not yet returned). This means your share price correctly reflects the full value of the vault even while the seed is deployed.


## Fee accounting

Fees are tracked with a global reward index that only increases:

```
accRewardPerShare += feeAmount × PRECISION / totalShares
```

Your pending fees at any point:

```
pending = (shares × accRewardPerShare / PRECISION) − rewardDebt + pendingFeeCredit
```

When you deposit additional USDC (top-up), your pending fees are harvested into `pendingFeeCredit` before your share count updates — so re-deposits never lose earned fees.


## Capital safety summary

| Risk | Status |
|---|---|
| Directional price risk | None — seed is split 50/50, returned at settlement |
| Smart contract risk | Standard ERC-20 vault, no admin keys post-deploy |
| LP principal loss | Not possible by design — principal is separated from trader funds |
| Fee slippage | None — fees accrue continuously per trade |
| Exit liquidity | Vault holds USDC + fees; exit is always available after settlement |


## Multiple deposits

You can deposit more USDC into a market vault at any time while it is active. Each deposit:
- Snapshots and preserves any pending fees earned so far
- Mints new shares at the current NAV price
- Starts earning fees on the combined share balance from that point forward
