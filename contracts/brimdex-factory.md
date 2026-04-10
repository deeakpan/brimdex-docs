# BrimdexFactory

Deploys and starts markets in a single transaction. Maintains the registry of all active markets.

**Source:** [`BrimdexFactory.sol`](https://github.com/deeakpan/Brimdex-contracts/blob/main/BrimdexFactory.sol)


## Market creation flow

```
Owner approves factory for seedPrincipal USDC
       ↓
factory.createMarket(...)
       ├── Deploy BrimdexParimutuelToken (BOUND)
       ├── Deploy BrimdexParimutuelToken (BREAK)
       ├── Deploy BrimdexMarket
       ├── Deploy MarketLiquidityVault
       ├── Pull seedPrincipal USDC from owner → factory
       ├── depositFor(owner, seedPrincipal) → vault (owner gets LP shares)
       ├── vault.pullSeedToMarket() → market
       └── market.initialize() → reads oracle, sets bounds, opens trading
```

All in one transaction.


## Key functions

### `createMarket(...)`

```solidity
function createMarket(
    string memory name,           // 1–8 characters
    uint256 expiryTimestamp,
    uint256 timeframeDuration,
    string memory feedName,       // e.g. "BTC/USD"
    uint256 bandPercent,          // e.g. 200 = 2%
    string memory boundTokenName,
    string memory boundTokenSymbol,
    string memory breakTokenName,
    string memory breakTokenSymbol
) external onlyOwner returns (address market, address boundToken, address breakToken, address liquidityVault)
```

Caller must pre-approve this contract for `seedPrincipal` USDC.

### `setSeedPrincipal(uint256)`
Owner only. Sets the USDC amount required to seed new markets.

### `getAllMarkets()`
Returns all market addresses ever created.

### `getMarkets(offset, limit)`
Paginated market list.

### `isActiveMarket(name, timeframeDuration, bandPercent)`
Returns true if a non-expired, non-settled market exists for this slot.


## Registry mappings

| Mapping | Key → Value |
|---|---|
| `isMarket` | address → bool |
| `marketToBoundToken` | market → BOUND token |
| `marketToBreakToken` | market → BREAK token |
| `marketToLiquidityVault` | market → vault |
| `activeMarkets` | slotKey → market |


## Market slot key

```solidity
keccak256(abi.encodePacked(name, timeframeDuration, bandPercent))
```

One active market per unique slot at any time.
