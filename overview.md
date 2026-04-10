# Overview

Brimdex is an onchain parimutuel prediction market for crypto price ranges, built on Somnia.

You pick a direction — does the price **stay inside the band** (BOUND) or **break out** (BREAK) by expiry? Buy your position, hold to settlement, or exit early through the orderbook.

## What makes Brimdex different

| Feature | Brimdex |
|---|---|
| Execution | Instant — always accepts buys |
| Pricing | Fully dynamic, pool-ratio driven |
| Counterparty | The pool — not another user |
| Early exit | Onchain orderbook for BOUND/BREAK tokens |
| Liquidity | Seeded by LPs who earn streaming fees |
| Settlement | Oracle-driven, onchain |
| Collateral | USDC only |

## Protocol at a glance

```
┌─────────────────────────────────────────────────────────┐
│                      BRIMDEX                            │
│                                                         │
│   TRADERS                      LIQUIDITY PROVIDERS      │
│   buy BOUND / BREAK             deposit USDC to vault   │
│   via primary market            earn 0.2% per trade     │
│   or orderbook                  principal returned      │
│                                 at settlement           │
│                                                         │
│   PRIMARY MARKET   ←→   MarketLiquidityVault            │
│   BrimdexMarket             (per-market)                │
│                                                         │
│   SECONDARY MARKET                                      │
│   BrimdexOrderBook                                      │
│   (peer-to-peer token trading)                          │
└─────────────────────────────────────────────────────────┘
```

## Core contracts

| Contract | Role |
|---|---|
| `BrimdexMarket` | Main parimutuel market: buy, settle, redeem |
| `BrimdexFactory` | Deploys and starts markets in one transaction |
| `BrimdexOrderBook` | Secondary market — BOUND/BREAK token trading |
| `MarketLiquidityVault` | Per-market LP vault — seed, fees, principal |
| `BrimdexRouter` | User-facing entry point — approve once, trade everywhere |

## Built on Somnia

Brimdex is deployed on the [Somnia](https://somnia.network) testnet. Somnia's high-throughput, low-latency EVM enables real-time price streaming, instant settlement, and onchain data publishing via Somnia Data Streams.
