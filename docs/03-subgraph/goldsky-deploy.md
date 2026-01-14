# Goldsky deploy

Nel repo `backend/` sono presenti script Yarn per build e deploy su Goldsky.

## Build (base testing)

```bash
cd backend
yarn build:base:testing
```

## Deploy

```bash
yarn deploy:goldsky
```

Nota: lo script usa un nome/versione hardcodata (`onewave/backend-0.0.6`). Quando bumpi la versione, aggiorna:

- consumer (frontend / points-service) se puntano a un endpoint specifico
- eventuali documenti in **Deployments & endpoints**.

