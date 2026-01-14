# Subgraph — overview

The `backend/` folder implements a Graph Protocol subgraph that indexes events from:

- **StudioProFactory** (VaultCreated)
- **StudioProVault** (Deposit/Withdraw + adapter events)
- **WaveSwap** (SwapExactIn/Out)

## What it is used for

- Frontend: list of “active” vaults and pairs (`AquaPair`) + basic vault data.
- Points Service: deposit/withdraw history and user position estimates.

## Endpoint

Production (Goldsky):

- `https://api.goldsky.com/api/public/project_cmgzitcts001c5np28moc9lyy/subgraphs/onewave/backend-0.0.6/gn`

Local:

- `http://localhost:8000/subgraphs/name/1wave/backend`

