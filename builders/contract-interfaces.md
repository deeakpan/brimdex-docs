# Contracts & ABIs

Use the generated ABIs from the repository artifacts instead of copying old handwritten interface snippets.

## Recommended ABI sources

### LMSR stack

- `artifacts-lmsr/` or `artifacts-lmsr-brimdex/`
- `smart-contract/lmsr/BrimdexLMSRStackFactory.sol`
- `smart-contract/lmsr/LMSRMarketMaker.sol`
- `smart-contract/lmsr/BrimdexLMSRRouter.sol`
- `smart-contract/lmsr/BrimdexFeeConfig.sol`

### Raise / LP vault

- `smart-contract/raise/BrimdexStackLaunchVault.sol`

### Orderbook

- `smart-contract/orderbook/BrimdexCTFOrderBook.sol`

### Oracle / automation

- `smart-contract/oracle/BrimdexFeeds/BrimdexFeeds.sol`
- `smart-contract/oracle/BrimdexFeeds/BrimdexReactivityCoordinator.sol`
- `smart-contract/oracle/BrimdexFeeds/BrimdexLaunchOpenCoordinator.sol`
- `smart-contract/oracle/BrimdexFeeds/BrimdexFeedAgentPuller.sol`

## High-signal functions

If you only need to orient yourself before loading the full ABI, these are the main current entry points:

### `BrimdexLMSRStackFactory`

- `createLaunchVault(...)`
- `authorizeVault(address)`
- `openMarket(...)`

### `BrimdexLMSRRouter`

- `tradeLmsr(LMSRMarketMaker market, int256[] outcomeTokenAmounts, int256 collateralLimit)`

### `LMSRMarketMaker`

- `calcNetCost(...)`
- `calcMarginalPrice(uint8 outcomeTokenIndex)`
- `trade(...)`
- `resolve()`

### `BrimdexStackLaunchVault`

- `phase()`
- `commit(uint256)`
- `openCommittedMarket()`
- `finishOpen()`
- `redeemLP()`
- `redeemCommitment()`

### `BrimdexCTFOrderBook`

- `placeSellOrder(...)`
- `placeBuyOrder(...)`
- `cancelSellOrder(...)`
- `cancelBuyOrder(...)`
- `getBestBid(...)`
- `getBestAsk(...)`
- `getOrderBookSnapshot(...)`

## Best practice

Do not hand-maintain inline ABI docs unless you are pinning them to a specific deployment version. For the current repo, the generated artifacts are the safest source of truth.
