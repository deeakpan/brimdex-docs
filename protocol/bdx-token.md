# BDX Token

**BDX** is the core protocol token of Brimdex.

It is designed to support:

- governance
- staking
- long-term ecosystem alignment
- incentive distribution over time

## What BDX does

BDX is the base asset users hold when they want a deeper role in the protocol beyond trading markets.

That includes:

- staking to earn protocol-linked rewards
- locking for stronger long-term voting power
- participating in the broader protocol economy

## What BDX is, exactly

In the current contracts, `BDX` is:

- an ERC-20 token
- capped at **750,000,000 BDX**
- mintable only by its owner, up to that cap
- built with vote-tracking support at the token level

But the current Brimdex governance design does **not** use plain liquid BDX as the main voting asset. The active governance path is:

- hold `BDX`
- stake into `sBDX`
- lock into `xBDX`

So BDX is the starting point, while `xBDX` is the governance weight used by the governor.

## Supply

The current token design documents:

- a **750,000,000 BDX** hard cap
- **210,000,000 BDX** allocated to the emissions vault at deployment

The documented emissions schedule currently includes:

- Year 1: **75M BDX**
- Year 2: **55M BDX**
- Year 3: **45M BDX**
- Year 4: **35M BDX**

The current emissions vault is documented as a **mechanical distribution vault** for that 210M allocation rather than a governance-controlled pool.

## Why BDX matters to users

BDX is the asset that unlocks the rest of the participation stack:

- stake it to receive **sBDX**
- lock `sBDX` to receive **xBDX**
- use `xBDX` for governance power
- qualify for the current fee discount path through `xBDX`

## Why BDX matters

Brimdex is built so that the product and the protocol can grow together.

BDX is the part of that design meant to align:

- users
- governors
- stakers
- long-term supporters of the network

## Related pages

- [Governance](governance.md)
- [Staking](staking.md)
- [Locking](locking.md)
