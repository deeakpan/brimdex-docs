# Contract Overview

Brimdex now runs on an **LMSR + conditional tokens + launch vault** stack, with settlement automation anchored on **Somnia**.

## Deployment addresses

### Somnia Mainnet

Mainnet addresses are not published in the docs yet.

| Contract | Address | Explorer |
|---|---|---|
| Stack Factory | TBA | TBA |
| LMSR Router | TBA | TBA |
| Fee Config | TBA | TBA |
| Asset Registry | TBA | TBA |
| Conditional Tokens | TBA | TBA |
| Brimdex Feeds | TBA | TBA |
| Launch Open Coordinator | TBA | TBA |
| Settlement Coordinator | TBA | TBA |
| BDX Token | TBA | TBA |
| BDX Staking | TBA | TBA |
| Voting Escrow | TBA | TBA |
| Governor | TBA | TBA |
| Timelock | TBA | TBA |

### Somnia Testnet

Explorer base: [shannon-explorer.somnia.network](https://shannon-explorer.somnia.network)

#### Core market stack

| Contract | Address | Explorer |
|---|---|---|
| Stack Factory | [`0xceb3C53e469690c0f9Cb9E2248AF22eA69a67692`](https://shannon-explorer.somnia.network/address/0xceb3C53e469690c0f9Cb9E2248AF22eA69a67692) | [View](https://shannon-explorer.somnia.network/address/0xceb3C53e469690c0f9Cb9E2248AF22eA69a67692) |
| LMSR Router | [`0xf304D3320bC97bB7a2F45De278739d5c6E15d3fe`](https://shannon-explorer.somnia.network/address/0xf304D3320bC97bB7a2F45De278739d5c6E15d3fe) | [View](https://shannon-explorer.somnia.network/address/0xf304D3320bC97bB7a2F45De278739d5c6E15d3fe) |
| CTF Orderbook (LMSR) | [`0x9F56d52D6eDb3D0803541B964970293Cd4d2eB12`](https://shannon-explorer.somnia.network/address/0x9F56d52D6eDb3D0803541B964970293Cd4d2eB12) | [View](https://shannon-explorer.somnia.network/address/0x9F56d52D6eDb3D0803541B964970293Cd4d2eB12) |
| Legacy Orderbook (ERC-20) | [`0x1FDFfe2650a092a804B53cDC6c9269957BA64726`](https://shannon-explorer.somnia.network/address/0x1FDFfe2650a092a804B53cDC6c9269957BA64726) | [View](https://shannon-explorer.somnia.network/address/0x1FDFfe2650a092a804B53cDC6c9269957BA64726) |
| Fee Config | [`0xE554443B66844F0A316EE0A54fbe19324Df77CF3`](https://shannon-explorer.somnia.network/address/0xE554443B66844F0A316EE0A54fbe19324Df77CF3) | [View](https://shannon-explorer.somnia.network/address/0xE554443B66844F0A316EE0A54fbe19324Df77CF3) |
| Asset Registry | [`0x3B1A28bbEABa6e5631f68EFBe3135C738Fd57902`](https://shannon-explorer.somnia.network/address/0x3B1A28bbEABa6e5631f68EFBe3135C738Fd57902) | [View](https://shannon-explorer.somnia.network/address/0x3B1A28bbEABa6e5631f68EFBe3135C738Fd57902) |
| Conditional Tokens | [`0x754db194CD4bD6d0c399F873CF993E8e597AcAb3`](https://shannon-explorer.somnia.network/address/0x754db194CD4bD6d0c399F873CF993E8e597AcAb3) | [View](https://shannon-explorer.somnia.network/address/0x754db194CD4bD6d0c399F873CF993E8e597AcAb3) |
| Brimdex Feeds | [`0x33e2e1521d3D26d90E41C548D94E61C0E0016A60`](https://shannon-explorer.somnia.network/address/0x33e2e1521d3D26d90E41C548D94E61C0E0016A60) | [View](https://shannon-explorer.somnia.network/address/0x33e2e1521d3D26d90E41C548D94E61C0E0016A60) |
| Launch Open Coordinator | [`0x6e69f1803b42F5BEE240E42B002342FA370f217A`](https://shannon-explorer.somnia.network/address/0x6e69f1803b42F5BEE240E42B002342FA370f217A) | [View](https://shannon-explorer.somnia.network/address/0x6e69f1803b42F5BEE240E42B002342FA370f217A) |
| Settlement Coordinator | [`0x08340bD6867c60ED60fC932Ae083DadecbDFE837`](https://shannon-explorer.somnia.network/address/0x08340bD6867c60ED60fC932Ae083DadecbDFE837) | [View](https://shannon-explorer.somnia.network/address/0x08340bD6867c60ED60fC932Ae083DadecbDFE837) |

#### Governance and token layer

| Contract | Address | Explorer |
|---|---|---|
| BDX Token | [`0xFCb06Ead3c9d3E46f3aB42E5811deF70EEc870E4`](https://shannon-explorer.somnia.network/address/0xFCb06Ead3c9d3E46f3aB42E5811deF70EEc870E4) | [View](https://shannon-explorer.somnia.network/address/0xFCb06Ead3c9d3E46f3aB42E5811deF70EEc870E4) |
| BDX Staking | [`0xCF57BeaCf1814233b3A18078232776629d1ba123`](https://shannon-explorer.somnia.network/address/0xCF57BeaCf1814233b3A18078232776629d1ba123) | [View](https://shannon-explorer.somnia.network/address/0xCF57BeaCf1814233b3A18078232776629d1ba123) |
| sBDX Token | [`0x11F9EF19161BD3D2c8f982D013768E3bE1f277E1`](https://shannon-explorer.somnia.network/address/0x11F9EF19161BD3D2c8f982D013768E3bE1f277E1) | [View](https://shannon-explorer.somnia.network/address/0x11F9EF19161BD3D2c8f982D013768E3bE1f277E1) |
| Voting Escrow (`xBDX`) | [`0x24E167fe04B5467912efD30aac8681dce1e64C70`](https://shannon-explorer.somnia.network/address/0x24E167fe04B5467912efD30aac8681dce1e64C70) | [View](https://shannon-explorer.somnia.network/address/0x24E167fe04B5467912efD30aac8681dce1e64C70) |
| Governor | [`0x7D98BA2c79aE15D017C1221aeA2eC8C26CD1777D`](https://shannon-explorer.somnia.network/address/0x7D98BA2c79aE15D017C1221aeA2eC8C26CD1777D) | [View](https://shannon-explorer.somnia.network/address/0x7D98BA2c79aE15D017C1221aeA2eC8C26CD1777D) |
| Timelock | [`0x88481A1B6bae027F65804B8AFf0149B4b6696faf`](https://shannon-explorer.somnia.network/address/0x88481A1B6bae027F65804B8AFf0149B4b6696faf) | [View](https://shannon-explorer.somnia.network/address/0x88481A1B6bae027F65804B8AFf0149B4b6696faf) |
| Emissions Vault | [`0x0beD6bcf7c06FA1BB2fF53C3aF668Af84c11E387`](https://shannon-explorer.somnia.network/address/0x0beD6bcf7c06FA1BB2fF53C3aF668Af84c11E387) | [View](https://shannon-explorer.somnia.network/address/0x0beD6bcf7c06FA1BB2fF53C3aF668Af84c11E387) |
| Emissions Distributor | [`0x32DBaDd330B9A348C11dA10DD7B9dacd56384DA6`](https://shannon-explorer.somnia.network/address/0x32DBaDd330B9A348C11dA10DD7B9dacd56384DA6) | [View](https://shannon-explorer.somnia.network/address/0x32DBaDd330B9A348C11dA10DD7B9dacd56384DA6) |

#### Utility and collateral

| Contract | Address | Explorer |
|---|---|---|
| USDC | [`0x4b6E2382570b840d3B5E52B042E2F9d5dB23d3fE`](https://shannon-explorer.somnia.network/address/0x4b6E2382570b840d3B5E52B042E2F9d5dB23d3fE) | [View](https://shannon-explorer.somnia.network/address/0x4b6E2382570b840d3B5E52B042E2F9d5dB23d3fE) |
| Fixed Math Library | [`0x09bbdB4f76910fA52bf84196d76AdF337E615686`](https://shannon-explorer.somnia.network/address/0x09bbdB4f76910fA52bf84196d76AdF337E615686) | [View](https://shannon-explorer.somnia.network/address/0x09bbdB4f76910fA52bf84196d76AdF337E615686) |

## Contract groups

| Group | Main contracts | Purpose |
|---|---|---|
| Raise | `BrimdexStackLaunchVault` | Collect commitments and open markets from a vault |
| LMSR | `BrimdexLMSRStackFactory`, `LMSRMarketMaker`, `BrimdexLMSRRouter`, `BrimdexFeeConfig` | Create, quote, trade, and fee-configure the primary market |
| Conditional tokens | `BrimdexConditionalTokens`, `BrimdexAssetRegistry` | Outcome accounting and settlement state |
| Oracle / automation | `BrimdexFeeds`, `BrimdexReactivityCoordinator`, `BrimdexLaunchOpenCoordinator`, `BrimdexFeedAgentPuller` | Feed storage and reactive launch / settlement |
| Secondary market | `BrimdexCTFOrderBook` | Peer-to-peer trading of outcome positions |

## Canonical flow

1. `BrimdexStackLaunchVault` collects commitments
2. `BrimdexLMSRStackFactory` opens the market when authorized
3. `LMSRMarketMaker` handles live primary trading
4. `BrimdexCTFOrderBook` handles secondary exits
5. `BrimdexFeeds` plus the coordinator stack drive launch and settlement on Somnia
6. traders and LPs redeem from the settled state

## Network assumptions

- settlement chain: **Somnia**
- collateral: **USDC-style 6 decimal asset**
- automation: **Somnia Reactivity + agents**

## Pages in this section

| Page | What it covers |
|---|---|
| [LMSR Stack Factory](brimdex-factory.md) | Stack deployment and vault-authorized market opening |
| [LMSR Market Maker](brimdex-market.md) | Live primary market execution and resolution |
| [Stack Launch Vault](market-liquidity-vault.md) | Commitment collection and LP redemption |
| [LMSR Router](brimdex-router.md) | User-facing trading entry point |
| [CTF Orderbook](brimdex-orderbook.md) | Secondary market for outcome positions |
| [Fee Config](brimdex-fee-config.md) | Centralized fee policy |
| [Feeds & Coordinators](feeds-and-coordinators.md) | Feed storage and reactive automation |
