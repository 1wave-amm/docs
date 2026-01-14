# Points — overview

Il sistema punti di 1wave è composto da:

- **WavePointToken** (on-chain, non-transferable)
- **Merkl** (campaigns + rewards/points off-chain via API)
- **Points Service** (API HTTP che aggrega tutto e calcola i punti finali)

## Cosa produce

Per un address utente, il servizio restituisce:

- `totalPoints`
- un `breakdown` per componenti (vault ownership, deposit, time bonus, referral, merkl, boost)
- `vaultPositions` (per spiegabilità)

## Dipendenze

- Subgraph (deposit/withdraw history e vault state)
- Merkl API (rewards)
- RPC Base (token boost checks)

