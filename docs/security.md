# Security

Questa sezione raccoglie note di sicurezza operative e design choices rilevanti.

## WavePointToken (points)

- **Non-transferable by default**: riduce il rischio di mercato secondario dei punti.
- **Minter management**: mint/burn solo da minter autorizzati.
- **Governance toggles**: abilitazione trasferimenti/whitelist/burn-for-claim via ruoli di governance (governor/guardian).

## Swap & strategies

- WaveSwap eredita meccanismi anti‑reentrancy del framework Aqua.
- Dopo ogni swap viene chiamato `publishPairs()` sul maker (AquaAdapter) per riallineare le strategie.

## Backend services

### Points Service

- Aggiungere **rate limiting** (es. per `/points/batch` e `/points/users/list`)
- Aggiungere **caching** per chiamate ripetute a subgraph/Merkl
- Referral: persistenza su DB e protezioni anti‑abuse (anti-sybil, one‑time constraints, etc.)

### Subgraph

- Verificare `startBlock` e address dei contratti per evitare indexing di eventi non correlati.

