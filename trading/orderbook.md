# Orderbook

Brimdex also includes an **orderbook** for secondary trading.

The orderbook exists mainly for one reason: **early exit**.

## What the orderbook is for

Use the orderbook when you want to:

- reduce a position
- exit before expiry
- choose your own price
- wait for someone else to match your order

## How it differs from the AMM

The **AMM** gives you instant execution.

The **orderbook** gives you:

- limit prices
- peer-to-peer trading
- more control over execution

## How it works

### Sell order

You choose:

- the market
- the side you want to sell
- the amount
- the price you want

Your order sits there until it is matched or cancelled.

### Buy order

You choose:

- the market
- the side you want to buy
- the amount
- the price you are willing to pay

Your order sits there until it is matched or cancelled.

## Why it matters

The orderbook is useful when:

- you want more control than instant trading gives you
- you want to exit without taking the current live quote
- you think someone else will meet your price

## Important limitation

The orderbook does not resolve markets and it does not decide who wins.

It is a trading venue, not the settlement engine.
