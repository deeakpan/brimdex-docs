# Settlement on Somnia

Brimdex chooses **Somnia** as the canonical settlement chain.

That means:

- the market expires on Somnia
- the settlement trigger runs on Somnia
- the final oracle write is processed on Somnia
- redemptions read the settled state from Somnia

## What triggers settlement

Brimdex uses:

- **Somnia Reactivity** for scheduling and triggering
- **onchain agents** for pulling the required price data

Once the final settlement trigger is available, Brimdex is designed for **sub-2s reactive settlement**.

## Who wins

- **BOUND** wins if the final price is inside or on the quoted range
- **BREAK** wins if the final price is outside the range

## Settlement flow

1. Market reaches expiry
2. Reactivity schedules the settlement path
3. Onchain agents fetch the needed final price
4. The market resolves on Somnia
5. Traders can redeem winning positions
6. LPs can redeem the resolved vault pool

## Why Brimdex keeps settlement on Somnia

Brimdex may serve multichain users, but keeping settlement on one chain provides:

- one canonical market state
- deterministic automation
- faster reactive finalization
- simpler redemption logic

See [Multichain with Stargate](../architecture/multichain-and-stargate.md) for the access model.

## Redemption

After the market resolves:

- winning traders redeem their BOUND or BREAK positions
- losing positions do not redeem
- LPs redeem their share of the vault's resolved LP pool

## Safety checks

Settlement still depends on:

- a valid final price
- acceptable oracle freshness
- the onchain automation path being ready

If the final price path is not ready yet, the market can remain pending for a short time instead of settling against stale data.
