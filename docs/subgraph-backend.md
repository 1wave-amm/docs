# Subgraph (backend)

Il folder `backend/` contiene un **subgraph** (Graph Protocol) che indicizza:

- Factory + Vault events (FactorDAO StudioPro)
- Eventi dell’adapter Aqua (`PairSet`, `StrategyShipped`)
- Eventi di swap di **WaveSwap** (`SwapExactIn`, `SwapExactOut`)

Questo subgraph è usato da:

- frontend (lista vault/pairs, dati base)
- points-service (posizioni utente, deposit/withdraw history)

## Entità (schema)

Definite in `backend/schema.graphql`:

- `Vault`
- `VaultDeposit`
- `VaultWithdraw`
- `AquaPair`
- `AquaStrategy`
- `Swap`

## Data sources & template

File template: `backend/subgraph.yaml.mustache`

- **StudioProFactory**: ascolta `VaultCreated(...)`
  - filtra: indicizza solo vault che includono l’`AquaAdapter` tra gli `initialManagerAdapters`
  - crea un template dataSource per ogni vault (`StudioProVault.create(...)`)
- **WaveSwap**: ascolta `SwapExactIn` / `SwapExactOut`
- **StudioProVault (template)**: ascolta `Deposit`, `Withdraw`, `PairSet`, `StrategyShipped`

## Config per network

Il file `subgraph.yaml` viene generato via Mustache:

- `yarn prepare:local` usa `backend/config/local.json`
- `yarn prepare:base:testing` usa `backend/config/base.testing.json`

## Esecuzione locale (Graph Node + IPFS + Postgres)

Avvio stack docker:

```bash
cd backend
export RPC_URL="base:https://mainnet.base.org" # formato richiesto da graph-node
yarn start-graph-node
```

Build + create + deploy locale:

```bash
yarn create-and-deploy:local
```

Endpoint locali tipici:

- GraphQL query: `http://localhost:8000/subgraphs/name/1wave/backend`
- Admin: `http://localhost:8020/`
- Index status: `http://localhost:8030/`

## Deploy (Goldsky)

Script repo:

- `yarn build:base:testing`
- `yarn deploy:goldsky`

L’endpoint pubblico attualmente usato dal frontend e points-service è:

- `https://api.goldsky.com/api/public/project_cmgzitcts001c5np28moc9lyy/subgraphs/onewave/backend-0.0.6/gn`

Nota: il comando `deploy:goldsky` usa un nome/versione hardcodata (`onewave/backend-0.0.6`). Quando bumpi la versione, aggiorna anche i consumer (frontend/points-service) se serve.

