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
│   PRIMARY MARKET   ←→   LP vault (per market)           │
│                                                         │
│   SECONDARY MARKET                                      │
│   Orderbook                                             │
│   (peer-to-peer token trading)                          │
└─────────────────────────────────────────────────────────┘
```

## Onchain components (reference)

In the **app**, you pick markets, approve USDC when your wallet asks, and confirm trades. The table below is for **transparency**—contract names map to what runs on Somnia.

| Component | Role |
|---|---|
| Market | Parimutuel core: primary buys, settlement, redeem |
| Factory | Creates markets and wires vault + tokens |
| Orderbook | Secondary limit-order trading for BOUND/BREAK |
| LP vault | Per-market seed liquidity, fee streaming, LP exit |
| Router | Routes primary buys so you can approve USDC in one place |

Technical ABIs live under [Contracts](contracts/contract-overview.md) and [Builders](builders/builder-overview.md).

## Built on Somnia

Brimdex is deployed on the [Somnia](https://somnia.network) testnet. Somnia's high-throughput, low-latency EVM enables real-time price streaming, instant settlement, and onchain data publishing via Somnia Data Streams.
