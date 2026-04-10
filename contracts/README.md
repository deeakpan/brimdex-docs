# Contract Overview & Addresses

All Brimdex contracts are deployed on the **Somnia Testnet**.


## Addresses

| Contract | Address |
|---|---|
| `BrimdexFactory` | `— update after deploy —` |
| `BrimdexRouter` | `— update after deploy —` |
| `BrimdexOrderBook` | `— update after deploy —` |
| `BrimdexFeeds` | `— update after deploy —` |
| `USDC (collateral)` | `— update after deploy —` |
| `Treasury` | `— update after deploy —` |

> Markets and vaults are deployed per-market via `BrimdexFactory`. Use `factory.getAllMarkets()` to enumerate them.


## Network details

| Property | Value |
|---|---|
| Network | Somnia Testnet |
| Chain ID | `50312` |
| RPC | `https://dream-rpc.somnia.network` |
| Explorer | `https://shannon-explorer.somnia.network` |
| Currency | STT |


## Architecture diagram

```
User
 │
 ├── BrimdexRouter ──────────────────► BrimdexMarket
 │        │                              │        │
 │   (approval mgmt)              buyBound    buyBreak
 │                                     │        │
 │                               MarketLiquidityVault
 │                                (seed + fees + exit)
 │
 └── BrimdexOrderBook ──────────── BOUND / BREAK tokens
          (peer-to-peer)
```


## Contract pages

| Contract | Description |
|---|---|
| [BrimdexMarket](brimdex-market.md) | Core parimutuel market |
| [BrimdexFactory](brimdex-factory.md) | Market deployment |
| [BrimdexOrderBook](brimdex-orderbook.md) | Secondary token market |
| [MarketLiquidityVault](market-liquidity-vault.md) | LP seed vault |
| [BrimdexRouter](brimdex-router.md) | User entry point |

## Source repository

- [BrimdexFactory.sol](https://github.com/deeakpan/Brimdex-contracts/blob/main/BrimdexFactory.sol)
- [BrimdexMarket.sol](https://github.com/deeakpan/Brimdex-contracts/blob/main/BrimdexMarket.sol)
- [BrimdexOrderBook.sol](https://github.com/deeakpan/Brimdex-contracts/blob/main/BrimdexOrderBook.sol)
- [BrimdexRouter.sol](https://github.com/deeakpan/Brimdex-contracts/blob/main/BrimdexRouter.sol)
- [MarketLiquidityVault.sol](https://github.com/deeakpan/Brimdex-contracts/blob/main/MarketLiquidityVault.sol)
- [BrimdexFeeds.sol](https://github.com/deeakpan/Brimdex-contracts/blob/main/BrimdexFeeds.sol)
- [BrimdexParimutuelToken.sol](https://github.com/deeakpan/Brimdex-contracts/blob/main/BrimdexParimutuelToken.sol)
- [IDataStreams.sol](https://github.com/deeakpan/Brimdex-contracts/blob/main/IDataStreams.sol)
