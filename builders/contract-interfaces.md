# Contract Interfaces

Minimal ABIs for integrating with Brimdex. Copy what you need.


## BrimdexFactory

```json
[
  "function getAllMarkets() view returns (address[])",
  "function getMarkets(uint256 offset, uint256 limit) view returns (address[])",
  "function getMarketCount() view returns (uint256)",
  "function isMarket(address) view returns (bool)",
  "function isActiveMarket(string, uint256, uint256) view returns (bool)",
  "function marketToBoundToken(address) view returns (address)",
  "function marketToBreakToken(address) view returns (address)",
  "function marketToLiquidityVault(address) view returns (address)",
  "function seedPrincipal() view returns (uint256)"
]
```


## BrimdexMarket

```json
[
  "function marketConfig() view returns (string name, string feedName, uint256 lowerBound, uint256 upperBound, uint256 expiryTimestamp, uint256 creationTimestamp, uint256 startPrice, bool initialized, bool settled)",
  "function boundPool() view returns (uint256)",
  "function breakPool() view returns (uint256)",
  "function seedPrincipal() view returns (uint256)",
  "function getBoundPrice() view returns (uint256)",
  "function getBreakPrice() view returns (uint256)",
  "function getDisplayPool() view returns (uint256)",
  "function getEstimatedTokens(bool isBound, uint256 grossUsdc) view returns (uint256)",
  "function getEstimatedPayout(bool isBound, uint256 grossUsdc) view returns (uint256)",
  "function boundWins() view returns (bool)",
  "function redemptionRate() view returns (uint256)",
  "function resolvedPrice() view returns (uint256)",
  "function buyBound(uint256 amount, address recipient, uint256 minTokensOut) nonpayable",
  "function buyBreak(uint256 amount, address recipient, uint256 minTokensOut) nonpayable",
  "function settle() nonpayable",
  "function redeem(bool isBound, uint256 amount) nonpayable"
]
```


## BrimdexRouter

```json
[
  "function buyBound(address marketAddress, uint256 amount, uint256 minTokensOut) nonpayable",
  "function buyBreak(address marketAddress, uint256 amount, uint256 minTokensOut) nonpayable"
]
```


## MarketLiquidityVault

```json
[
  "function deposit(uint256 usdcAmount) nonpayable",
  "function exit() nonpayable",
  "function sharesOf(address) view returns (uint256)",
  "function totalShares() view returns (uint256)",
  "function pendingFees(address) view returns (uint256)",
  "function principalShareUsdc(address) view returns (uint256)",
  "function totalExitUsdc(address) view returns (uint256)",
  "function totalNAV() view returns (uint256)",
  "function seedFinalized() view returns (bool)",
  "function principalBalance() view returns (uint256)",
  "function targetSeed() view returns (uint256)"
]
```


## BrimdexOrderBook

```json
[
  "function placeSellOrder(address market, bool isBound, uint256 amount, uint256 limitPrice) nonpayable returns (uint256 orderId)",
  "function placeBuyOrder(address market, bool isBound, uint256 amount, uint256 limitPrice) nonpayable returns (uint256 orderId)",
  "function cancelSellOrder(uint256 orderId) nonpayable",
  "function cancelBuyOrder(uint256 orderId) nonpayable",
  "function feeRate() view returns (uint256)"
]
```


## ERC-20 (BOUND / BREAK tokens)

```json
[
  "function balanceOf(address) view returns (uint256)",
  "function totalSupply() view returns (uint256)",
  "function approve(address spender, uint256 amount) nonpayable returns (bool)",
  "function transfer(address to, uint256 amount) nonpayable returns (bool)",
  "function transferFrom(address from, address to, uint256 amount) nonpayable returns (bool)"
]
```
