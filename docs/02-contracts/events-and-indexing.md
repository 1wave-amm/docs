# Events & indexing

This page maps **on-chain events** → **subgraph entities** → **consumers (frontend/points)**.

## WaveSwap → Swap

Events:

- `SwapExactIn(...)`
- `SwapExactOut(...)`

Subgraph entity:

- `Swap` (fields: vault, tokenIn, tokenOut, amountIn, amountOut, swapType, block, timestamp, txid)

Consumers:

- frontend (analytics/UX)
- points-service (if you use swaps as a signal for Merkl campaigns)

## Vault (StudioProVault) → VaultDeposit / VaultWithdraw

Events:

- `Deposit(...)`
- `Withdraw(...)`

Entities:

- `VaultDeposit`
- `VaultWithdraw`

Consumers:

- points-service (user positions, daysDeposited, totalDepositedUSD)

## AquaAdapter (emesso dalla vault) → AquaPair / AquaStrategy

Events:

- `PairSet(token0, token1, feeBps, pairHash)`
- `StrategyShipped(pairHash, strategyHash)`

Entities:

- `AquaPair` (source of truth for the “active vaults” list)
- `AquaStrategy`

Consumers:

- frontend (vault list/pairs)

