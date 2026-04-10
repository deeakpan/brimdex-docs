# Contract Overview & Addresses

All Brimdex contracts are deployed on the **Somnia Testnet**.

## Addresses

Somnia Testnet deployment (from repo `deployments.json`, 2026-04-10).

| Contract / library | Address |
|---|---|
| `BrimdexFactory` | `0x14c005488847182d9fa5AEFCC4e6f8927e900804` |
| `BrimdexRouter` | `0x180a07de7BC493Ff11E66e129c8B520BbA204299` |
| `BrimdexOrderBook` | `0x3c45fa7c72dadc5692a3180f34eA32FB73BA5825` |
| `BrimdexFeeds` | `0xe24cB9468a690E33dDbC365BD29F8E1B53e48F93` |
| `USDC (collateral)` | `0x4b6E2382570b840d3B5E52B042E2F9d5dB23d3fE` |
| `Treasury` | `0x68ac96Ce64D62386b1A5E2DFf8f0F01fEEd46E09` |
| `OrderBookLinkedList` (library) | `0x75797fa067305999f7E4B9c639CCd583FB563841` |

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
