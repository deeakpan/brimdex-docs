# Agents & Reactivity

Brimdex uses **Somnia Reactivity** and **onchain agents** to automate both market launch and market settlement.

## Why Brimdex uses this model

The product needs two things:

- reliable event-driven scheduling onchain
- a way to fetch fresh price data when a market needs to open or settle

Reactivity handles the timing. Agents handle the price-triggered action.

## What users should know

Users do not need to manually settle markets.

Instead, Brimdex is designed so that:

- markets can open automatically once launch conditions are met
- markets can be resolved automatically after expiry
- **onchain agents** help move that process forward on Somnia

## Launch flow

1. A launch vault reaches its required notional.
2. Reactivity schedules the open flow.
3. An onchain agent fetches the required asset update.
4. The market opens on Somnia.

## Settlement flow

1. A market expires.
2. Reactivity schedules the settlement path.
3. An onchain agent fetches the final price update.
4. The market resolves on Somnia.
5. Traders and LPs can redeem from the resolved state.

## Performance target

Brimdex is designed for **sub-2s reactive settlement** once the final trigger and required price update are available.

That target is part of the reason Brimdex keeps the full settlement path on Somnia instead of splitting settlement logic across multiple execution chains.

## Why this matters for the product

This architecture is what makes Brimdex feel live:

- launch vaults can open automatically
- market cards can refresh around real onchain events
- settlement can happen quickly after expiry
- redemption reads one canonical resolved state

See [Settlement on Somnia](../how-it-works/settlement.md) for the product view and [Feeds & Coordinators](../contracts/feeds-and-coordinators.md) for the builder / contract view.
