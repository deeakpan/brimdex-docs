# AMM Trading

Brimdex uses an **AMM** for instant market access.

That means you do not need to wait for another user to take the other side before entering a position.

## What AMM trading is for

AMM trading is the fastest way to:

- buy **BOUND**
- buy **BREAK**
- enter a live market immediately

Under the hood, Brimdex uses an LMSR-style pricing model, but for users the simpler mental model is:

- the market is live
- you choose a side
- you get an instant quote
- you confirm the trade

## Primary trading flow

1. Connect your wallet on Somnia.
2. Open a live market.
3. Choose **BOUND** or **BREAK**.
4. Enter the amount you want to trade.
5. Review the estimate.
6. Approve if needed.
7. Confirm the trade.

## What happens after you trade

After an AMM trade:

- your BOUND or BREAK position updates
- the market odds update
- the market can move for the next trader

## When to use AMM trading

Use the AMM when you want:

- instant execution
- quick entry
- a simple trading flow

## When not to use it

If you want:

- a very specific price
- an early exit with limit control
- to wait for a better fill

then the [Orderbook](orderbook.md) may be the better choice.
