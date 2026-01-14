# Monitoring & logging

## Frontend

- Error tracking (Sentry o simili)
- RPC health (rate limits, timeout)
- User journey metrics (swap, vault create, deposit/withdraw)

## Subgraph

- Sync lag / indexing errors
- Reorg threshold settings (se applicabile)
- Alert su “no new blocks processed”

## Points Service

- Latency endpoint `/points/:address`
- Cache hit ratio (quando aggiunta)
- Error rate per Merkl/Subgraph fetch
- Rate limiting e abuse detection

## Logging

Standardizzare:

- requestId per request
- error stack + upstream response (Merkl/Subgraph) in modo safe (no secrets)

