# Schema (entities)

File: `backend/schema.graphql`

## Entities

- `Vault`: vault metadata and configuration (assets, fees, totalSupply, pricePerShare, netVaultValue…)
- `VaultDeposit`: deposit events (owner, shares, timestamp…)
- `VaultWithdraw`: withdraw events (receiver, shares, timestamp…)
- `AquaPair`: adapter pairs (token0/token1/feeBps/pairHash)
- `AquaStrategy`: published strategies (pairHash/strategyHash)
- `Swap`: swap events from WaveSwap (ExactIn/ExactOut)

## Principles

- IDs are built to avoid collisions (txHash + logIndex + extra keys).
- The vault list shown by the frontend is derived from `AquaPair` (if a vault has indexed pairs, it is considered “active”).

