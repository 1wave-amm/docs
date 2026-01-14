# System architecture

## Componenti e responsabilità

- **WaveSwap (on-chain)**: swap exact in/out contro strategie Aqua, emette eventi di swap.
- **AquaAdapter (on-chain)**: crea/configura pair e pubblica strategie su Aqua.
- **StudioProFactory/Vault (on-chain)**: factory e vault Pro (FactorDAO) che emettono deposit/withdraw e chiamano adapter.
- **Subgraph (off-chain indexing)**: indicizza eventi e produce un modello dati GraphQL per frontend/points.
- **Points Service (off-chain API)**: calcola punti aggregando subgraph + Merkl + referral + boost.
- **Frontend (client)**: UI che usa subgraph + stats API + points API e firma transazioni.

## Diagramma alto livello (Mermaid)

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

## “Source of truth”

- **Vault list / active pairs**: subgraph (`AquaPair`)
- **Metrics/APY/strategies**: Stats API esterna (se configurata nel frontend)
- **Points**: aggregazione Points Service (Merkl + subgraph + referral + boost)

