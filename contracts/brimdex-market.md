# BrimdexMarket

The core parimutuel market contract. One instance per market, deployed by `BrimdexFactory`.

**Source:** [`BrimdexMarket.sol`](https://github.com/deeakpan/Brimdex-contracts/blob/main/BrimdexMarket.sol)

## State

| Variable | Type | Description |
|---|---|---|
| `marketConfig` | `MarketConfig` | Name, bounds, expiry, start price, flags |
| `collateralToken` | `IERC20` | USDC |
| `boundToken` | `BrimdexParimutuelToken` | BOUND ERC-20 |
| `breakToken` | `BrimdexParimutuelToken` | BREAK ERC-20 |
| `boundPool` | `uint256` | USDC in the BOUND pool |
| `breakPool` | `uint256` | USDC in the BREAK pool |
| `seedPrincipal` | `uint256` | USDC seeded by LP vault |
| `liquidityVault` | `address` | Per-market LP vault |
| `redemptionRate` | `uint256` | Set at settlement (1e18 precision) |
| `boundWins` | `bool` | Outcome (set at settlement) |

## Constants

| Constant | Value | Description |
|---|---|---|
| `TRADE_FEE_BPS` | 200 | 2% total trade fee |
| `TRADE_FEE_TREASURY_BPS` | 180 | 1.8% to treasury |
| `TRADE_FEE_SEED_BPS` | 20 | 0.2% to LP vault |
| `MAX_ORACLE_STALENESS` | 300 | 5 minutes |
| `EMERGENCY_DELAY` | 43200 | 12 hours |
