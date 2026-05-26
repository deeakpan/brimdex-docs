# Brimdex 101

Brimdex lets you express one view in a very simple way:

- **BOUND** if you think the asset will stay inside the quoted range
- **BREAK** if you think the asset will finish outside the quoted range

The protocol then handles pricing, token issuance, orderbook exits, and settlement on Somnia.

## The basic shape of a market

Every market has:

- an asset, such as `ETH / USD`, `NVDA / USD`, or `XAU / USD`
- a band, such as `±0.5%`, `±1.5%`, or `±3%`
- a duration, such as `10m`, `30m`, `2h`, or `1d`
- one settlement timestamp

At expiry there are only two outcomes:

- final price is **inside** the range -> **BOUND**
- final price is **outside** the range -> **BREAK**

## Simple examples

### Crypto example

`ETH / USD · 10m · ±0.5%`

- If ETH settles inside the band, **BOUND** wins
- If ETH settles below the lower bound or above the upper bound, **BREAK** wins

### Stock example

`NVDA / USD · 30m · ±1.5%`

- If NVDA stays inside the quoted range, **BOUND** wins
- If NVDA breaks out of the range, **BREAK** wins

### RWA / commodity example

`XAU / USD · 2h · ±1.0%`

- If gold stays inside the band, **BOUND** wins
- If gold settles outside the band, **BREAK** wins

## How trading works

Brimdex uses an automated pricing engine for continuous quotes:

- you can buy immediately without waiting for another user
- larger orders move price more than smaller orders
- lower seed means sharper price moves and worse fills
- larger seed means better depth, but more LP exposure

If you want out before expiry, Brimdex also supports an **orderbook** for secondary trading.

## How settlement works

Brimdex chooses to settle on **Somnia**:

- the market itself lives on Somnia
- price updates land on Somnia
- Somnia Reactivity and **onchain agents** coordinate the launch and settlement flow
- once the final trigger is available, Brimdex is designed for **sub-2s reactive settlement**

## What LPs do

LPs seed the launch vault that opens the market.

They are not guaranteed to get the full seed back:

- they earn a share of fees
- they also absorb market-making risk
- after settlement, LPs redeem their share of the resolved vault proceeds

See [Liquidity & Vaults](how-it-works/liquidity-providing.md) for the full LP flow.

## Summary

1. A launch vault collects USDC commitments
2. Reactivity and agents open the market on Somnia
3. Traders buy BOUND or BREAK
4. Users can hold to expiry or exit through the orderbook
5. Somnia settlement resolves the market and winners redeem
6. LPs redeem the resolved vault proceeds
