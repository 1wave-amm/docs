# System architecture

## Components & responsibilities

- **WaveSwap (on-chain)**: exact-in/out swaps against Aqua strategies; emits swap events.
- **AquaAdapter (on-chain)**: configures pairs and publishes strategies to Aqua.
- **StudioProFactory/Vault (on-chain)**: factory and Pro vaults (FactorDAO) that emit deposit/withdraw events and invoke the adapter.
- **Subgraph (off-chain indexing)**: indexes events and exposes a GraphQL model for frontend/points.
- **Points Service (off-chain API)**: computes points by aggregating subgraph + Merkl + referrals + boost.
- **Frontend (client)**: UI that consumes subgraph + optional Stats API + Points API and signs transactions.

## High-level diagram (Mermaid)

```mermaid
flowchart LR
  user([User]) -->|wallet| fe[Frontend (app)]

  fe -->|tx: swap| ws[WaveSwap (AquaApp)]
  fe -->|tx: create vault / setPair / publishPairs| v[Vault / Factory]
  v --> aa[AquaAdapter (maker)]
  ws --> aa

  aa --> aqua[(1inch Aqua)]
  ws --> aqua

  subg[Subgraph (GraphQL)] --> fe
  ws -->|events| subg
  v -->|events| subg
  aa -->|events| subg

  merkl[Merkl API] --> ps[Points Service]
  subg --> ps
  ps --> fe
```

## Source of truth

- **Vault list / active pairs**: subgraph (`AquaPair`)
- **Metrics/APY/strategies**: external Stats API (when configured in the frontend)
- **Points**: Points Service aggregation (Merkl + subgraph + referrals + boost)

