# API Usage

The public Brimdex API is the fastest way to bootstrap builder integrations before adding direct onchain reads.

## Base path

Start from:

- `https://brimdex.markets/api/`

## What the API is useful for

The public API is useful for:

- market discovery
- market activity summaries
- supported asset lookups
- UI-friendly data hydration

## When to use the API first

Use the API first when you are building:

- dashboards
- market lists
- portfolio views
- lightweight bots
- internal tools that do not need full custom indexing

## When to add onchain reads

Add direct chain reads when you need:

- latest live odds
- latest redemption truth
- launch-vault phase checks
- event-driven automation

## Recommended builder pattern

The usual pattern is:

1. start with the Brimdex API
2. use contract reads for latency-sensitive state
3. use events or reactivity for live synchronization

See [Market Data](fetching-markets.md) and [Events & Reactivity](events-and-reactivity.md) for the next layer down.
