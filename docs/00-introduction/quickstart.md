# Quickstart (local dev)

This guide helps you quickly run the main components locally.

## Prerequisites

- Node.js 18+
- `pnpm` (frontend)
- Docker (for a local Graph Node)
- Base RPC (Alchemy recommended for the frontend)

---

## 1) Frontend

```bash
cd app
pnpm install
cp .env.example .env
pnpm dev
```

Minimum required in `app/.env`:

- `VITE_WALLETCONNECT_PROJECT_ID=...`
- `VITE_ALCHEMY_API_KEY=...`

---

## 2) Subgraph (Graph Node locale)
## 2) Subgraph (local Graph Node)

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

