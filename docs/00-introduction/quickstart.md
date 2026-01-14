# Quickstart (local dev)

Questa guida ti porta ad avviare rapidamente i componenti principali in locale.

## Prerequisiti

- Node.js 18+
- `pnpm` (frontend)
- Docker (per Graph Node locale)
- RPC Base (Alchmey consigliato per frontend)

---

## 1) Frontend

```bash
cd app
pnpm install
cp .env.example .env
pnpm dev
```

Minimo indispensabile in `app/.env`:

- `VITE_WALLETCONNECT_PROJECT_ID=...`
- `VITE_ALCHEMY_API_KEY=...`

---

## 2) Subgraph (Graph Node locale)

```bash
cd backend
export RPC_URL="base:https://mainnet.base.org"
yarn start-graph-node
```

Build + create + deploy locale:

```bash
yarn create-and-deploy:local
```

---

## 3) Points Service

```bash
cd points-service
npm install
cp .env.example .env
npm run dev
```

Test:

```bash
curl http://localhost:3001/health
curl http://localhost:3001/points/0xYourAddressHere
```

---

## 4) Contracts (Foundry)

```bash
cd contracts
forge build
forge test
```

