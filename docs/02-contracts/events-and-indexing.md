# Events & indexing

Questa pagina collega **eventi on-chain** → **entity del subgraph** → **consumer (frontend/points)**.

## WaveSwap → Swap

Eventi:

- `SwapExactIn(...)`
- `SwapExactOut(...)`

Subgraph entity:

- `Swap` (campi: vault, tokenIn, tokenOut, amountIn, amountOut, swapType, block, timestamp, txid)

Consumer:

- frontend (analytics/UX)
- points-service (se usi swap come segnale per campagne Merkl)

## Vault (StudioProVault) → VaultDeposit / VaultWithdraw

Eventi:

- `Deposit(...)`
- `Withdraw(...)`

Entity:

- `VaultDeposit`
- `VaultWithdraw`

Consumer:

- points-service (posizioni utente, daysDeposited, totalDepositedUSD)

## AquaAdapter (emesso dalla vault) → AquaPair / AquaStrategy

Eventi:

- `PairSet(token0, token1, feeBps, pairHash)`
- `StrategyShipped(pairHash, strategyHash)`

Entity:

- `AquaPair` (source of truth per lista vault “attive”)
- `AquaStrategy`

Consumer:

- frontend (vault list/pairs)

