# Schema (entities)

File: `backend/schema.graphql`

## Entities

- `Vault`: metadata e configurazioni di una vault (assets, fee, totalSupply, pricePerShare, netVaultValue…)
- `VaultDeposit`: deposit events (owner, shares, timestamp…)
- `VaultWithdraw`: withdraw events (receiver, shares, timestamp…)
- `AquaPair`: pair configurate su adapter (token0/token1/feeBps/pairHash)
- `AquaStrategy`: strategie pubblicate (pairHash/strategyHash)
- `Swap`: swap events da WaveSwap (ExactIn/ExactOut)

## Principi

- Gli id sono costruiti per evitare collisioni (txHash + logIndex + extra keys).
- La lista vault mostrata dal frontend è derivata dalle `AquaPair` (se una vault ha pair indicizzate, è “attiva”).

