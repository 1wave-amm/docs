# Frontend (app)

Frontend React per **Wave – Liquidity as a Service**.

## Stack

- React 18 + TypeScript
- Vite
- wagmi + viem + RainbowKit (wallet connect & web3)
- Tailwind CSS + Radix UI

## Setup

```bash
cd app
pnpm install
cp .env.example .env
pnpm dev
```

## Env vars

Minime:

- `VITE_WALLETCONNECT_PROJECT_ID`: WalletConnect Project ID
- `VITE_ALCHEMY_API_KEY`: usata per RPC Base (obbligatoria: senza API key l’RPC diventa `ALCHEMY_API_KEY_NOT_CONFIGURED.invalid`)

Opzionali:

- `VITE_STATS_API_BASE_URL`: base URL della Stats API (vault metrics / strategie). Se vuota alcune viste restano parziali.
- `VITE_XYC_SWAP_ADDRESS`: address della WaveSwap app (default: `0xa9e35ef3cc6493c61cc782c373a5f076aaae2f98`)
- `VITE_ENVIRONMENT`: `testing` | `production` (default `production`)

## Web3 config

File: `src/lib/web3/config.ts`

- Chain abilitata: **Base**
- Transport: HTTP via Alchemy, con retry/timeout configurati.

## Funzionalità principali

- **Landing**: presentazione del progetto e sezioni tecniche
- **Swap**: UI swap che usa WaveSwap su Base
- **Vaults / Vault detail**: lista vault e dettagli, aggregando dati da:
  - **Subgraph** (source of truth per vault/pairs)
  - **Stats API** (metriche/APY/strategie, se configurata)
- **Create Vault Wizard**: deploy di vault Pro via FactorDAO SDK e setup pairs:
  - deploy vault (StudioProFactory)
  - `setPair(...)` e `publishPairs()` sull’adapter
  - set public strategy / deposit strategy
  - salvataggio metadata verso Stats API (`/strategies/save`)

## Dati e dipendenze esterne

- **Subgraph**: `https://api.goldsky.com/api/public/project_cmgzitcts001c5np28moc9lyy/subgraphs/onewave/backend-0.0.6/gn`
- **Stats API**: configurabile via `VITE_STATS_API_BASE_URL`

