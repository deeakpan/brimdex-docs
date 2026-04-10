# Positions & Tokens

Every position on Brimdex is a **standard token balance** in your wallet. When you **buy** on the primary market, tokens are **minted** to you. When you **redeem** or **sell**, they’re **burned** or **transferred**.


## BOUND and BREAK tokens

Each market has two ERC-20 tokens:

| Token | Wins when | Symbol example |
|---|---|---|
| **BOUND** | Final price is inside the band | e.g. tied to BTC + duration |
| **BREAK** | Final price is outside the band | e.g. tied to BTC + duration |

Both sides use the same underlying collateral model (USDC in the pool). Token amounts use **6 decimals**, consistent with USDC.


## How you get tokens

When you **confirm a buy** in the app, the protocol mints tokens based on the **live pool price** and the **USDC you spend** (after the primary-market fee). You don’t mint manually—the **Buy** flow does it.


## How tokens go away

1. **Redeem after settlement** — if you hold **winning** tokens, the app’s **redeem** flow burns them and sends you USDC.  
2. **Sell on the orderbook** — tokens transfer to the buyer; nothing is burned.  
3. **Rare recovery paths** — if settlement is stuck for a long time, there may be a **recovery** option for traders (see [Settlement](../how-it-works/settlement.md)); the product UI reflects what’s available.


## Transferability

BOUND and BREAK are normal ERC-20s. You can hold them in your wallet, **sell** on the orderbook, or send them to another address if your wallet supports it.


## Seeing your position

In the app, your **position** is your **token balance** for that market’s BOUND or BREAK token—shown on the market page, portfolio, or similar views. You don’t need contract addresses for day-to-day use.


## After settlement

- **Winning** tokens can be **redeemed** for USDC at the published rate.  
- **Losing** tokens are worth zero for redemption.  
- Winning tokens **don’t expire** on a clock—you can redeem when you’re ready.


## For builders

Resolving token addresses and calling `balanceOf` onchain is covered in [Fetching markets](../builders/fetching-markets.md) and [Contract interfaces](../builders/contract-interfaces.md).
