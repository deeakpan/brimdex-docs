# Staking

Staking is the first step for users who want to participate in the Brimdex protocol beyond just trading markets.

## What staking is for

Staking is designed for users who want:

- deeper protocol participation
- protocol-linked rewards
- a path toward longer-term alignment

## Simple flow

In simple terms:

1. hold **BDX**
2. stake **BDX**
3. receive a staking receipt position

The current design uses **sBDX** as that receipt token.

## Why the receipt token matters

The receipt token is not just accounting in the background. In the current contracts, `sBDX` is a real wallet token:

- minted **1:1** when you stake BDX
- burned **1:1** when you withdraw BDX
- transferable
- lockable into `xBDX`

That gives stakers a more flexible participation path than a non-transferable staking balance.

## What stakers get

In the current staking contract, `sBDX` holders earn **USDC rewards** funded by the staker share of Brimdex trading fees.

That means stakers can:

- accumulate USDC rewards over time
- claim those rewards when they want
- use `exit()` to withdraw BDX and claim accrued USDC in one go

## Important benefit

Because `sBDX` lives in your wallet, it is also the asset you lock to move into the governance layer.

## Who staking is for

Staking is for users who want more than market exposure.

It is the step between:

- simply holding BDX
- becoming a longer-term governor through locking

## Next step

If you want stronger governance influence, staking can lead into [Locking](locking.md).
