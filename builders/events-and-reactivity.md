# Events & Reactivity

Brimdex integrations that need live updates should combine normal reads with an event-driven layer.

## When this matters

You need event-driven sync when you are building:

- live market cards
- trading terminals
- alerting systems
- reactive bots
- settlement-sensitive tooling

## Two useful sources of truth

### 1. Onchain events

Use onchain events when you want canonical low-level state transitions such as:

- market opens
- trades land
- funding changes
- markets pause or resume
- markets resolve

### 2. Somnia Reactivity

Use Somnia Reactivity when you want to understand the automation path around:

- market opening
- settlement triggers
- fast post-expiry resolution flows

## Recommended builder pattern

For most builder apps:

1. load initial state from the API or standard reads
2. subscribe to the relevant events
3. refresh only the affected market or position when an update lands

## What to keep live

The most useful state to keep live is:

- market odds
- market stage
- user positions
- redeemability state
- launch-vault phase

## Related pages

- [Market Data](fetching-markets.md)
- [Trading Integration](trading.md)
- [Positions & Redemptions](reading-positions.md)
