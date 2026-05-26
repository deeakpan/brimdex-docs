# Protocol Overview

Brimdex is more than a trading interface. It also has a token and governance layer designed around long-term participation.

## What sits under the product

The user-facing Brimdex experience is built around:

- range markets with **BOUND** and **BREAK**
- launch liquidity for new markets
- fast settlement on **Somnia**
- **onchain agents** that help open and resolve markets
- a protocol layer centered around **BDX**

## The protocol layer

The Brimdex protocol layer covers:

- **BDX** as the base token
- **sBDX** as the staking receipt token
- **xBDX** as the locked governance position
- onchain governance through a governor and timelock
- emissions and treasury decisions over time

## The participation path

The current protocol path is:

1. hold **BDX**
2. stake BDX to receive **sBDX**
3. lock `sBDX` to receive **xBDX**

Each step does something different:

- **BDX** is the base asset
- **sBDX** keeps your staked position liquid and reward-bearing
- **xBDX** is the long-term governance position

## Why this matters to users

The protocol layer is what turns Brimdex from a single product into a governed network.

It gives the ecosystem a way to:

- align long-term participants
- reward users who stay involved
- vote on protocol changes
- build governance around fees, incentives, and treasury decisions

## What users get from it

In the current contract design:

- `sBDX` holders earn **USDC trade-fee rewards**
- `xBDX` holders hold the governance power used by the current governor
- users with at least **200,000 xBDX** qualify for the discounted trading fee path

## Main pages in this section

| Page | What it covers |
|---|---|
| [BDX Token](bdx-token.md) | What BDX is for and how it fits into Brimdex |
| [Governance](governance.md) | How protocol decisions are made |
| [Staking](staking.md) | How users move from holding BDX into protocol participation |
| [Locking](locking.md) | How long-term participants gain stronger governance weight |
| [Audits](audits.md) | Security review status and future audit disclosures |
