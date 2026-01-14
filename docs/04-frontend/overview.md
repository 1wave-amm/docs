# Frontend — overview

The frontend (`app/`) is a React webapp that supports:

- wallet connection on **Base**
- swapping via WaveSwap
- browsing vaults and viewing vault details
- creating Pro vaults + configuring pairs/strategies
- integrating with the Points Service to display points (when wired in).

## Stack

- React 18 + TypeScript + Vite
- wagmi + viem + RainbowKit
- Tailwind CSS + Radix UI

## Dati e servizi
## Data sources & services

- **Subgraph**: source of truth for vault/pairs
- **Stats API** (optional): metrics/APY/strategies (via `VITE_STATS_API_BASE_URL`)
- **Points Service**: points, referrals, campaigns (when configured and routed in the product)

