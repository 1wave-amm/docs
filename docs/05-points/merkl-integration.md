# Merkl integration

## Ruolo di Merkl

Merkl è usato come “calculation/indexing layer” per programmi a punti:

- campaign setup (es. deposit tracking)
- rewards aggregation
- API per estrarre rewards per token/campaign.

## API usate dal Points Service

- `/campaigns` (per elencare campaigns create dal creator)
- `/rewards` (rewards per campaign, paginata)
- `/rewards/token/` (rewards per token, paginata)

Nota importante:

- `chainId` nelle API Merkl è la chain dove è deployato il points token (qui: Base 8453), non necessariamente la chain dove avviene l’attività (dipende dal setup Merkl).

## Best practices

- Cache dei risultati Merkl (per evitare chiamate costose “all token rewards complete”).
- Usare paging/limit e job async per leaderboard.
- Validare schema risposta (Merkl può differire tra versioni/fields).

