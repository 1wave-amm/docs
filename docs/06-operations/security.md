# Security

## On-chain

### WaveSwap

- Usa primitive Aqua (nonReentrantStrategy / balances safe) e controlli su output/input (slippage).
- Chiama `publishPairs()` sul maker dopo swap: attenzione a possibili failure se maker non implementa correttamente l’interfaccia.

### WavePointToken

- Non-transferable di default
- Ruoli e governance toggles (minter, governor/guardian)

## Off-chain

### Points Service

- Rate limiting (necessario su batch/list endpoints)
- Cache per Merkl e subgraph
- DB per referrals e leaderboard
- Sanitizzazione input (address format) già presente sui principali endpoint

### Subgraph

- Address/startBlock corretti per evitare indexing “sporco”
- Monitor su reorg e revert.

