# Multichain with Stargate

Brimdex is **multichain in access** and **single-chain in settlement**.

That means users and liquidity can arrive from other ecosystems, but the actual market execution and resolution still happen on **Somnia**.

## Why Brimdex uses this model

Bringing liquidity in from multiple chains is useful.

Splitting market truth across multiple settlement chains is not.

Brimdex therefore uses a simple product rule:

- **distribution and routing can be multichain**
- **market truth lives on Somnia**

## Where Stargate fits

Stargate is the routing layer for:

- moving liquidity toward Somnia
- onboarding users who hold capital on other chains
- reducing the need for Brimdex to recreate the full market stack on every chain

## What still stays on Somnia

Even with multichain access, these parts remain on Somnia:

- market launch
- live trading
- orderbook activity
- market resolution
- settlement
- redemption

## Why this is good for users

- one canonical source of market truth
- simpler wallet and redemption logic
- lower coordination risk
- faster reactive settlement

## Mental model

Think of Brimdex as:

- **multichain at the edge**
- **Somnia-native at the core**

That lets the protocol expand distribution without fragmenting the actual market state.
