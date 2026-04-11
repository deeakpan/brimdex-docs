# The Orderbook

The **orderbook** is the secondary market for trading BOUND and BREAK tokens before settlement. It works like a classic limit-order book: no new tokens are minted here—users trade with each other, and the app escrows USDC or tokens until a match.


## Why an orderbook?

Primary market buys are one-directional — you can buy but not sell back. If you want to exit early, you need a peer-to-peer mechanism. The orderbook lets you list your tokens at a price and have another user fill the order.


## How it works

**Placing a sell order:**  
You set a limit price and token amount. The app will ask you to **approve** the BOUND/BREAK tokens for the orderbook, then your tokens sit in **escrow** until the order fills or you cancel.

**Placing a buy order:**  
You set a limit price and token amount. The app will ask you to **approve USDC** for the orderbook; your **USDC plus the buyer fee** is held in escrow until a match or cancel.

**Matching:**
The contract matches on price. An incoming sell hits bids at or above the limit price; an incoming buy hits asks at or below the limit price. Matches execute at the **resting order's price** (maker pricing).


## Fees

| Side | Fee |
|---|---|
| Buyer | 0.5% of matched notional |
| Seller | 0.5% of matched notional |

The UI shows **buyer** totals (notional plus fee) and **seller** proceeds (notional minus fee). Fees go to the protocol treasury.


## Per-market isolation

Each market has its own order space within the orderbook. You cannot accidentally fill an order from a different market.


## Cancelling orders

Both buy and sell orders can be cancelled at any time before they are filled. Escrowed USDC or tokens are returned immediately.


## What the orderbook does NOT do

- It does not mint tokens
- It does not interact with pool prices — orderbook trades have no effect on the primary market price
- It does not guarantee a match — if no counterparty exists at your price, your order sits open until filled or cancelled
