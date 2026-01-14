# 1wave Docs

Documentazione ufficiale del progetto **1wave**.

## Quick start

- **[Architecture](architecture.md)**: componenti e flow principali.
- **[Frontend (app)](frontend-app.md)**: UI Vite/React, Web3 config, env vars.
- **[Subgraph (backend)](subgraph-backend.md)**: Graph Node locale + deploy Goldsky.
- **[Smart Contracts](contracts.md)**: WaveSwap, AquaAdapter, WavePointToken.
- **[Points Service](points-service.md)**: API HTTP e calcolo punti.
- **[Deployments](deployments.md)**: indirizzi su Base e link utili.
- **[Runbook](runbook.md)**: troubleshooting e checklist di debug.

## Repository layout (monorepo)

- `app/`: frontend (Vite + React + wagmi/RainbowKit)
- `backend/`: subgraph (Graph Protocol / Goldsky)
- `contracts/`: smart contracts (Foundry)
- `points-service/`: backend Node/Express per points

