# Reading Positions

How to read a user's open positions, pending payouts, and LP state.


## Token balances (trading positions)

```js
const boundToken = new ethers.Contract(
  await factory.marketToBoundToken(marketAddress),
  ['function balanceOf(address) view returns (uint256)'],
  provider
);

const breakToken = new ethers.Contract(
  await factory.marketToBreakToken(marketAddress),
  ['function balanceOf(address) view returns (uint256)'],
  provider
);

const boundBalance = await boundToken.balanceOf(userAddress);
const breakBalance = await breakToken.balanceOf(userAddress);
```


## Estimated payout at settlement

```js
const redemptionRate = await market.redemptionRate(); // set after settlement

// If market settled and user holds winning tokens:
const payout = (balance * redemptionRate) / BigInt(1e18);
```

Before settlement, estimate with current pool state:

```js
const estimated = await market.getEstimatedPayout(isBound, grossUsdc);
```


## LP positions (vault)

```js
const vault = new ethers.Contract(vaultAddress, VAULT_ABI, provider);

const shares          = await vault.sharesOf(userAddress);
const pendingFees     = await vault.pendingFees(userAddress);
const principalShare  = await vault.principalShareUsdc(userAddress);
const totalOnExit     = await vault.totalExitUsdc(userAddress);
```


## Reading across all markets

To build a portfolio view:

```js
const allMarkets = await factory.getAllMarkets();

for (const marketAddr of allMarkets) {
  const boundToken = await factory.marketToBoundToken(marketAddr);
  const breakToken = await factory.marketToBreakToken(marketAddr);
  const vault      = await factory.marketToLiquidityVault(marketAddr);

  const [bound, brk, lpShares] = await Promise.all([
    erc20(boundToken).balanceOf(user),
    erc20(breakToken).balanceOf(user),
    vault ? erc20Vault(vault).sharesOf(user) : 0n,
  ]);

  if (bound > 0n || brk > 0n || lpShares > 0n) {
    // user has a position in this market
  }
}
```
