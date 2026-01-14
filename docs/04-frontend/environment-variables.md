# Environment variables

File: `app/.env`

## Required

- `VITE_WALLETCONNECT_PROJECT_ID`: WalletConnect project ID (RainbowKit).
- `VITE_ALCHEMY_API_KEY`: required for Base RPC (without it, the RPC URL becomes `ALCHEMY_API_KEY_NOT_CONFIGURED.invalid`).

## Optional

- `VITE_STATS_API_BASE_URL`: base URL per Stats API (vault metrics, strategies, tokens).
- `VITE_XYC_SWAP_ADDRESS`: override address WaveSwap app (default: `0xa9e35ef3cc6493c61cc782c373a5f076aaae2f98`).
- `VITE_ENVIRONMENT`: `testing` | `production` (default `production`).

## Notes

- The app is configured to use **Base only** in `src/lib/web3/config.ts`.

