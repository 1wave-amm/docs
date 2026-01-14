# Goldsky deploy

The `backend/` package includes Yarn scripts to build and deploy on Goldsky.

## Build (base testing)

```bash
cd backend
yarn build:base:testing
```

## Deploy

```bash
yarn deploy:goldsky
```

Note: the script uses a hardcoded name/version (`onewave/backend-0.0.6`). When you bump the version, update:

- consumers (frontend / points-service) if they point to a specific endpoint
- any docs under **Deployments & endpoints**.

