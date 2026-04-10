# The Orderbook

The `BrimdexOrderBook` is a secondary market for trading BOUND and BREAK tokens before settlement. It is a classic CLOB (Central Limit Order Book) — no AMM, no minting, just token transfers between users.


## Why an orderbook?

Primary market buys are one-directional — you can buy but not sell back. If you want to exit early, you need a peer-to-peer mechanism. The orderbook lets you list your tokens at a price and have another user fill the order.


## How it works

**Placing a sell order:**
You set a limit price and token amount. Your tokens are held in escrow by the contract.

**Placing a buy order:**
You set a limit price and token amount. Your USDC (notional + buyer fee) is held in escrow.

**Matching:**
The contract matches on price. An incoming sell hits bids at or above the limit price; an incoming buy hits asks at or below the limit price. Matches execute at the **resting order's price** (maker pricing).


## Fees

| Side | Fee |
|---|---|
| Buyer | 1.5% of matched notional |
| Seller | 1.5% of matched notional |

Buyer deposits `notional + 1.5%` upfront. Seller receives `notional − 1.5%`. Fee goes to the protocol treasury.


## Per-market isolation

Each market has its own order space within the orderbook. You cannot accidentally fill an order from a different market.


## Cancelling orders

Both buy and sell orders can be cancelled at any time before they are filled. Escrowed USDC or tokens are returned immediately.


## What the orderbook does NOT do

- It does not mint tokens
- It does not interact with pool prices — orderbook trades have no effect on the primary market price
- It does not guarantee a match — if no counterparty exists at your price, your order sits open until filled or cancelled
