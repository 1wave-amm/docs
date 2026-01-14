# Vaults data model (frontend)

## Source of truth: subgraph pairs

Il frontend determina quali vault mostrare partendo da `AquaPair` nel subgraph:

- se una vault ha almeno una `AquaPair`, è considerata “attiva” e viene mostrata.

## Enrichment: Stats API (opzionale)

Se `VITE_STATS_API_BASE_URL` è impostata, il frontend arricchisce la UI con:

- TVL/pricePerShare/apy/performance windows
- lista token / logo
- strategie salvate via `/strategies/save`.

## Aggregazione (high level)

La logica fa:

1. Fetch `AquaPair` (subgraph) → elenco vault
2. Fetch vault metadata (subgraph) per gli address trovati
3. Fetch pro-vaults / available-tokens / strategies (Stats API) e merge per address
4. Fallback: se una vault è nel subgraph ma non nella Stats API, viene comunque inclusa (con dati minimi).

