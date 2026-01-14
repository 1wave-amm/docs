# Subgraph — overview

Il folder `backend/` implementa un subgraph (Graph Protocol) che indicizza eventi di:

- **StudioProFactory** (VaultCreated)
- **StudioProVault** (Deposit/Withdraw + eventi adapter)
- **WaveSwap** (SwapExactIn/Out)

## Per cosa viene usato

- Frontend: elenco vault “attive” e pairs (`AquaPair`) + dati base vault.
- Points Service: history deposit/withdraw e stime posizione utente.

## Endpoint

Produzione (Goldsky):

- `https://api.goldsky.com/api/public/project_cmgzitcts001c5np28moc9lyy/subgraphs/onewave/backend-0.0.6/gn`

Locale:

- `http://localhost:8000/subgraphs/name/1wave/backend`

