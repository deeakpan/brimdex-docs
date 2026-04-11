# BrimdexOrderBook

Onchain CLOB (Central Limit Order Book) for trading BOUND and BREAK tokens between users. No minting — only token transfers.

**Somnia testnet (current):** `0x1FDFfe2650a092a804B53cDC6c9269957BA64726` — same as `orderBook` in repo `deployments.json`.

**Source:** [`BrimdexOrderBook.sol`](https://github.com/deeakpan/Brimdex-contracts/blob/main/BrimdexOrderBook.sol)

## Key functions

### `placeSellOrder(market, isBound, amount, limitPrice)`
List BOUND or BREAK tokens for sale at a limit price. Tokens are moved to escrow. If buy orders exist at or above `limitPrice`, the order matches immediately.

### `placeBuyOrder(market, isBound, amount, limitPrice)`
Bid for BOUND or BREAK tokens at a limit price. USDC (`amount × limitPrice / 1e18 + fee`) is moved to escrow. Matches against resting sell orders at or below `limitPrice`.

### `cancelSellOrder(orderId)`
Return escrowed tokens to the seller.

### `cancelBuyOrder(orderId)`
Return escrowed USDC to the buyer.

## Matching

- Incoming sell hits bids at **≥ limit price** (best bid first)
- Incoming buy hits asks at **≤ limit price** (best ask first)
- Matches execute at the **resting order's price** (maker pricing)
- Partial fills are supported — remaining amount stays open

## Fees

1.5% per side on matched notional. Collected from escrow at fill time, sent to treasury.

## Per-market isolation

Every order is associated with a specific market address. The contract rejects orders for unregistered markets.

## State

| Variable | Description |
|---|---|
| `feeRate` | 150 bps per side |
| `marketFactory` | Reference to BrimdexFactory for market validation |
| `orders` | Mapping of orderId → Order |
| Price level linked lists | Sorted bid/ask queues per market per side |
