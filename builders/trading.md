# Trading via Contract

How to execute buys programmatically using `BrimdexRouter`.


## Setup

```js
const router = new ethers.Contract(ROUTER_ADDRESS, ROUTER_ABI, signer);
const usdc   = new ethers.Contract(USDC_ADDRESS, ERC20_ABI, signer);
```


## One-time approval

```js
await usdc.approve(ROUTER_ADDRESS, ethers.MaxUint256);
```

Or approve per-trade with the exact amount.


## Buy BOUND

```js
const amount       = 100_000_000n;  // $100 USDC (6 decimals)
const minTokensOut = 0n;            // set a real value for slippage protection

await router.buyBound(marketAddress, amount, minTokensOut);
```


## Buy BREAK

```js
await router.buyBreak(marketAddress, amount, minTokensOut);
```


## Calculating minTokensOut

Fetch the estimated tokens first, then apply your acceptable slippage:

```js
const estimated    = await market.getEstimatedTokens(true, amount);
const slippageBps  = 50n; // 0.5%
const minTokensOut = estimated * (10000n - slippageBps) / 10000n;

await router.buyBound(marketAddress, amount, minTokensOut);
```


## Redeeming after settlement

```js
const market = new ethers.Contract(marketAddress, MARKET_ABI, signer);

// isBound = true for BOUND tokens, false for BREAK tokens
await market.redeem(isBound, tokenAmount);
```


## Direct market interaction (no router)

If you want to call the market directly:

```js
// Approve the market directly (not the router)
await usdc.approve(marketAddress, amount);
await market.buyBound(amount, recipientAddress, minTokensOut);
```

The recipient can be any address — useful for buying on behalf of another wallet.
