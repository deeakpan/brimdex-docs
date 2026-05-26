# Governance

Brimdex is designed for **onchain governance**.

That means the protocol is intended to evolve through token-holder voting rather than only through a centralized admin path.

## What governance is for

Governance can be used to shape decisions around:

- protocol parameters
- fee policy
- treasury direction
- emissions and incentives
- future ecosystem upgrades

## Voting power

The current governance contracts use **xBDX** for voting power.

That means governance weight comes from the locked vote-escrow position, not from simply holding liquid BDX.

## Current governance settings

The live governor contract documents these parameters:

- **voting delay:** 1 day
- **voting period:** 5 days
- **proposal threshold:** 100,000 xBDX
- **quorum:** 4% of total xBDX supply
- **timelock delay:** 2 days

## Proposal flow

At a high level, governance follows a standard onchain flow:

1. eligible participants propose changes
2. the community votes
3. successful proposals pass through a timelocked execution path
4. the approved changes are executed onchain

## What governance can actually do today

Based on the current contracts, governance can control timelock-owned protocol surfaces such as:

- changing the **LP / staker / protocol fee split**
- updating the **staking rewards** contract address
- updating the **voting escrow** contract address
- updating the **stack factory** operator
- updating the **settlement** and **launch-open** coordinators
- pointing new markets at a new **fee config** contract
- moving treasury-held assets if the treasury is timelock-owned
- executing arbitrary treasury actions through the treasury contract

## Important nuance on fees

In the current fee config, governance controls the **split** of trading fees, not the headline total fee itself.

So governance can rebalance who receives the fee, but not arbitrarily change the total trading fee from the governor alone.

## Important nuance

Not every operational control is intentionally governed.

For example, the current fee config keeps the **protocol wallet rotation** under a separate protocol-admin path so it can be rotated quickly in an emergency, rather than waiting on a full governance cycle.

## Why this matters

Governance gives Brimdex a path to become community-shaped over time instead of remaining a fixed product with no voice for long-term users.

## Related pages

- [BDX Token](bdx-token.md)
- [Staking](staking.md)
- [Locking](locking.md)
