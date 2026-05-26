# Market Lifecycle

Brimdex markets follow a launch-vault-to-settlement lifecycle on Somnia.

## Lifecycle at a glance

**Launch vault -> Pending launch -> Live market -> Expiry -> Settlement -> Redemptions**

## 1. Launch vault created

A launch vault is created for a specific:

- asset
- band
- horizon
- fee config
- launch target

At this stage, the market maker is not live yet. Users are committing capital to the vault that will open it.

## 2. Commitments collected

The launch vault accepts USDC commitments until:

- the target notional is reached, or
- the commitment window expires

If the target is not met in time, the vault can abort and commitments can be redeemed.

## 3. Pending launch

Once the vault reaches target:

- Somnia Reactivity schedules the launch flow
- a Somnia agent fetches the relevant price
- the market receives the fresh price it needs
- the launch flow completes and the market opens

This is the bridge between capital formation and the live market.

## 4. Live market

When the market opens:

- BOUND and BREAK trading starts
- the orderbook can be used for secondary trading
- odds update with every trade
- LP seed is now actively backing the market

This is the phase most traders interact with.

## 5. Expiry

At expiry:

- no more live trading should be accepted
- the market transitions into settlement preparation
- Somnia Reactivity schedules the settlement path

## 6. Settlement on Somnia

Brimdex chooses to settle on Somnia.

The settlement flow is:

1. market expires
2. the settlement coordinator / puller is triggered
3. the final price is fetched and written through the Somnia-native path
4. the market resolves on Somnia
5. the resolved state becomes redeemable

The protocol is designed for **sub-2s reactive settlement** once the final trigger and final price are available.

## 7. Redemption phase

After settlement:

- traders redeem winning BOUND or BREAK positions
- LPs redeem their commitment-token share of the resolved LP pool
- the market is economically complete

## What users can do when

| Action | Phase |
|---|---|
| Commit to launch vault | Before launch target is met |
| Trade BOUND / BREAK | While live |
| Use the orderbook | While live |
| Redeem winning positions | After settlement |
| Redeem LP share | After settlement |

## Why this lifecycle matters

Brimdex is not just a single market contract. The product is a coordinated flow across:

- launch vaults
- Somnia agents
- reactive automation
- live markets
- orderbook exits
- settlement and redemption

See [Agents & Reactivity](../architecture/agents-and-reactivity.md) and [Settlement on Somnia](../how-it-works/settlement.md) for the automation path.
