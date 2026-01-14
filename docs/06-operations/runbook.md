# Runbook

## Frontend: wallet/RPC issues

- `VITE_WALLETCONNECT_PROJECT_ID` presente e valido
- `VITE_ALCHEMY_API_KEY` presente (obbligatoria)
- wallet su chain **Base**

## Vault list vuota

- Subgraph raggiungibile
- Esistono `AquaPair` nel subgraph (pairs configurate + publishPairs eseguita)
- Se Stats API non configurata: ok, ma metriche incomplete

## Subgraph non synca

Locale:

- container up (graph-node/postgres/ipfs)
- `RPC_URL` nel formato `network:rpc` (es. `base:https://...`)

Prod (Goldsky):

- status deploy/sync
- address e startBlock corretti

## Points Service ritorna 0

- `SUBGRAPH_URL` corretto
- Merkl:
  - `POINTS_TOKEN_ADDRESS` impostato
  - `MERKL_CREATOR_ADDRESS` / API key ok
- Boost:
  - `RPC_URL` raggiungibile
  - token addresses corretti

## Referral non persiste

Atteso (in-memory). Per produzione: DB.

