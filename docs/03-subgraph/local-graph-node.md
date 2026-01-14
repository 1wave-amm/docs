# Local Graph Node

This repo includes a `docker-compose.yml` to run:

- graph-node
- ipfs
- postgres

## Start

```bash
cd backend
export RPC_URL="base:https://mainnet.base.org"
yarn start-graph-node
```

## Build + create + deploy

```bash
yarn create-and-deploy:local
```

## Endpoint

- Query: `http://localhost:8000/subgraphs/name/1wave/backend`
- Admin: `http://localhost:8020/`
- Status: `http://localhost:8030/`

