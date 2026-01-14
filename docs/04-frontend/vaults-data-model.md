# Vaults data model (frontend)

## Source of truth: subgraph pairs

The frontend determines which vaults to show by starting from `AquaPair` entities in the subgraph:

- if a vault has at least one `AquaPair`, it is considered “active” and will be displayed.

## Enrichment: Stats API (optional)

If `VITE_STATS_API_BASE_URL` is set, the frontend enriches the UI with:

- TVL/pricePerShare/apy/performance windows
- token lists / logos
- strategies saved via `/strategies/save`.

## Aggregation (high level)

The flow is:

1. Fetch `AquaPair` (subgraph) → vault list
2. Fetch vault metadata (subgraph) for the discovered addresses
3. Fetch pro-vaults / available-tokens / strategies (Stats API) and merge by address
4. Fallback: if a vault exists in the subgraph but not in the Stats API, it is still included (with minimal data).

