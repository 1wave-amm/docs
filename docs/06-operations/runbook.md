# Runbook

## Frontend: wallet/RPC issues

- `VITE_WALLETCONNECT_PROJECT_ID` is set and valid
- `VITE_ALCHEMY_API_KEY` is set (required)
- wallet is on **Base**

## Vault list is empty

- Subgraph is reachable
- `AquaPair` entities exist in the subgraph (pairs configured + `publishPairs` executed)
- If Stats API is not configured: OK, but metrics will be incomplete

## Subgraph is not syncing

Local:

- container up (graph-node/postgres/ipfs)
- `RPC_URL` is in `network:rpc` format (e.g. `base:https://...`)

Prod (Goldsky):

- status deploy/sync
- correct address and startBlock

## Points Service returns 0

- correct `SUBGRAPH_URL`
- Merkl:
  - `POINTS_TOKEN_ADDRESS` set
  - `MERKL_CREATOR_ADDRESS` / API key OK
- Boost:
  - `RPC_URL` reachable
  - correct token addresses

## Referrals do not persist

Expected (in-memory). Production requires a database.

