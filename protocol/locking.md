# Locking

Locking is the long-term commitment layer of the Brimdex protocol.

It is designed for users who want stronger governance influence and deeper alignment with the future direction of Brimdex.

## What locking is for

Locking is for users who want:

- stronger voting power
- longer-term protocol alignment
- a bigger role in governance

## Simple mental model

The protocol path looks like this:

1. hold **BDX**
2. stake it
3. lock it for longer-term governance weight

The current design locks **sBDX**, not raw BDX, and mints **xBDX** as the locked governance position.

## What xBDX is

In the current contracts, `xBDX` is a **vote-escrow NFT**:

- it is created when `sBDX` is locked
- its voting power decays over time
- longer locks create stronger governance weight

The lock can run for up to **4 years**.

## What lockers can do

Once a lock exists, the current escrow contract lets users:

- create a new lock
- add more `sBDX` to an existing lock
- extend the unlock time
- withdraw once the lock expires

## Why locking matters in practice

Locking is not just symbolic. In the current design it is tied to two real benefits:

- **governance power** through `xBDX`
- the **discounted trading fee path** once a user holds at least **200,000 xBDX**

The fee config documents that discount as:

- standard fee: **0.9%**
- discounted fee: **0.675%**

## Why locking matters

Brimdex is designed so that long-term commitment carries more weight than passive short-term holding.

That helps push governance toward participants who are more aligned with the protocol over time.

## Who locking is for

Locking is for users who want to help shape:

- protocol direction
- governance decisions
- long-term ecosystem incentives

If you only want to trade markets, you do not need locking.
