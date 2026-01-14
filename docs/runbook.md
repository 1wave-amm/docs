# Runbook

Checklist e troubleshooting per i componenti di **1wave**.

## Frontend non si connette (wallet / RPC)

- Verifica `VITE_WALLETCONNECT_PROJECT_ID`
- Verifica `VITE_ALCHEMY_API_KEY` (RPC Base è obbligatoria)
- Controlla che stai usando **Base** come chain in wallet

## Vaults vuoti / lista incompleta

Il frontend considera il subgraph come “source of truth” per vault/pairs.

- Verifica che il subgraph endpoint sia raggiungibile
- Verifica che esistano `AquaPair` nel subgraph (pair configurate e pubblicate)
- Se `VITE_STATS_API_BASE_URL` è vuoto, alcune metriche possono mancare (ma la lista dovrebbe comunque apparire se il subgraph ha pairs)

## Subgraph non aggiorna

Locale:

- `docker ps` e log di graph-node/postgres/ipfs
- `RPC_URL` nel formato `network:rpc` (es. `base:https://...`)

Goldsky:

- verifica lo stato di deploy/sync nel pannello Goldsky
- controlla `startBlock` e gli address dei dataSource (Factory/WaveSwap)

## Points Service restituisce 0 punti

- Verifica `SUBGRAPH_URL` (deve puntare al subgraph corretto)
- Se Merkl è parte del calcolo:
  - verifica `MERKL_API_KEY` e `MERKL_CREATOR_ADDRESS`
  - verifica `POINTS_TOKEN_ADDRESS` e `CHAIN_ID`
- Se token boost è attivo:
  - verifica `RPC_URL`
  - verifica `TOKEN_1INCH_ADDRESS` / `TOKEN_FCTR_ADDRESS`

## Referral non persiste

Attualmente i referral sono in-memory nel processo Node (non persistono a restart).

Soluzione production:

- usare DB (Postgres/Mongo) + migrazioni
- aggiungere rate-limit e anti-abuse

