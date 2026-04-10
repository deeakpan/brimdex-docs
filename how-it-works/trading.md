# Trading

Buying BOUND or BREAK on Brimdex happens in the app: you choose a market, pick a side, enter how much USDC you want to spend, and confirm. The interface walks you through each step.

## In the app

1. **Connect your wallet** on Somnia testnet and make sure you have USDC.

2. **Open an active market** from the markets list (or the market page). You’ll see the price band, time to expiry, and current odds.

3. **Choose BOUND or BREAK**  
   - **BOUND** wins if the oracle price is **inside** the band at expiry.  
   - **BREAK** wins if the price ends **outside** the band.

4. **Enter the USDC amount** you want to spend. The UI shows an estimate of how many tokens you’ll receive based on the live pool.

5. **Set slippage (if shown)** so the trade won’t execute if the pool moves too much and you’d get fewer tokens than your minimum.

6. **Approve USDC** when your wallet prompts you. You’re allowing the app’s **router** to move USDC for this trade. Approvals can be set once for a comfortable limit so you aren’t asked every time; you can also approve per trade if you prefer.

7. **Confirm the buy.** After the transaction confirms, BOUND or BREAK tokens appear in your wallet. The app handles routing behind the scenes.

## What you’re paying

The **2% fee** on primary buys is taken from the USDC you send: most goes to the protocol treasury, and **0.2%** is streamed to seed liquidity providers. The rest becomes pool liquidity that backs your tokens. See [Fees](fees.md).

## Limit orders (orderbook)

For limit buys and sells, the app will ask you to **approve USDC** (for buys) or **approve the BOUND/BREAK tokens** (for sells) to the **orderbook** when needed—again, your wallet explains what you’re signing.

## After you buy

- Your **position** is simply your **token balance** for that market’s BOUND or BREAK token. The portfolio or market view reflects this.
- **Hold to settlement** and redeem if your side wins, or **sell early** on the orderbook if you want out before expiry.

## Integrators & builders

Function names, router flow, and `minTokensOut` semantics are documented for developers in [Builders: Trading](../builders/trading.md) and [Brimdex Router](../contracts/brimdex-router.md).
