# Positions & Redemptions

Brimdex positions are tokenized claims on a specific market outcome.

For every market, the trader-facing outcomes are:

- **BOUND**
- **BREAK**

## What you actually hold

When you buy through the main Brimdex trading flow, you receive outcome exposure that the UI presents as your BOUND or BREAK position for that market.

Under the hood, Brimdex uses an automated primary market plus an orderbook for secondary trading and exit.

So the important user mental model is simple:

- your position balance is your claim on BOUND or BREAK
- if your side wins, you can redeem
- if your side loses, it does not redeem

## How positions are created

Positions are created when you trade:

1. choose a market
2. choose **BOUND** or **BREAK**
3. enter a USDC amount
4. sign the trade
5. receive the corresponding position balance

## How positions change

Positions can change in three ways:

### 1. You buy more

Your balance increases.

### 2. You sell on the orderbook

Your balance decreases as another user takes the other side.

### 3. You redeem after settlement

Winning balance is redeemed for USDC and your redeemable token balance drops accordingly.

## What the app should show

For a useful position view, Brimdex surfaces:

- current BOUND / BREAK balance
- entry / cost basis
- current status
- whether the market is settled
- whether the position is redeemable

## After settlement

After the market resolves:

- **winning** positions can be redeemed for USDC
- **losing** positions remain non-redeemable
- the protocol publishes the final payout state on Somnia

Brimdex settlement is designed so the outcome is written on Somnia and the redeem flow reads the same canonical settlement result.

## LP commitment tokens

Launch vault participants are a different class of holder from traders.

When you commit to a launch vault, you receive:

- **commitment tokens** representing your share of the launch vault

After the market resolves, those commitment tokens are burned to redeem your share of the LP pool.

See [Liquidity & Vaults](../how-it-works/liquidity-providing.md) for that flow.
