# Points calculation

This page documents the points calculation logic implemented in the Points Service.

## Main inputs

- User vault positions (from subgraph):
  - `valueUSD` (estimated)
  - `tvlUSD` (estimated)
  - `totalDepositedUSD` (estimated)
  - `daysDeposited`
- `merklPoints` (sum of Merkl rewards)
- `referralCount`
- `hasTokenBoost` (balance check on enabled tokens)

## Components

### Vault ownership points

Goal: reward the user’s share of vault TVL.

### Deposit amount points

Goal: reward deposited amount × time.

### Time based points

Bonus for holders > 30 days (grows up to ~2x at 1 year, with reduced weight).

### Vault count points

Bonus for the number of distinct vaults.

### Referral points

Bonus proportional to `basePoints` and the number of referrals.

### Token boost

Multiplier applied if the user holds at least one of `TOKEN_1INCH_ADDRESS` or `TOKEN_FCTR_ADDRESS`.

## Output

- full `breakdown`
- `totalPoints = (basePoints + referralPoints) * boostMultiplier`

