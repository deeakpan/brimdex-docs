# Architecture Overview

Brimdex is designed so the product feels simple even though a lot is happening underneath.

## The big picture

From a user point of view, the Brimdex architecture has five simple parts:

1. **asset coverage**  
   markets can be created for crypto, stocks, and RWAs
2. **launch liquidity**  
   new markets can be funded before they open
3. **live trading**  
   users can buy BOUND or BREAK while a market is active
4. **secondary exit**  
   users can use the orderbook if they want to exit before expiry
5. **automated resolution**  
   onchain agents help resolve markets on Somnia after expiry

## Why Brimdex keeps settlement on Somnia

Brimdex is multichain in access, but single-chain in settlement truth.

That means Somnia is the place where:

- markets open
- markets resolve
- redemptions become final

This gives Brimdex:

- one canonical source of truth
- faster settlement
- cleaner user flows
- less fragmentation across chains

## Why users care

This design is meant to deliver a product that feels:

- fast
- consistent
- easy to understand
- easier to scale across many asset types

If you want the technical contract-by-contract breakdown, go to [Contract Overview](../contracts/contract-overview.md). If you want the product explanation of how markets are opened and resolved, go to [Agents & Reactivity](agents-and-reactivity.md).
