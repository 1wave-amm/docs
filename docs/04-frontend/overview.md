# Frontend — overview

Il frontend (`app/`) è una webapp React che permette:

- collegamento wallet su **Base**
- swap via WaveSwap
- esplorazione vault e dettaglio vault
- creazione vault Pro + configurazione pairs/strategie
- integrazione con Points Service per mostrare punti (quando collegato).

## Stack

- React 18 + TypeScript + Vite
- wagmi + viem + RainbowKit
- Tailwind CSS + Radix UI

## Dati e servizi

- **Subgraph**: source of truth per vault/pairs
- **Stats API** (opzionale): metriche/apy/strategie (via `VITE_STATS_API_BASE_URL`)
- **Points Service**: punti, referral, campaigns (se configurato e routato nel prodotto)

