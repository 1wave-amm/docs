# Monitoring & logging

## Frontend

- Error tracking (Sentry or similar)
- RPC health (rate limits, timeout)
- User journey metrics (swap, vault create, deposit/withdraw)

## Subgraph

- Sync lag / indexing errors
- Reorg threshold settings (if applicable)
- Alerts for “no new blocks processed”

## Points Service

- Latency endpoint `/points/:address`
- Cache hit ratio (when caching is introduced)
- Error rate for Merkl/Subgraph fetches
- Rate limiting and abuse detection

## Logging

Standardize:

- requestId per request
- error stack + upstream responses (Merkl/Subgraph), safely (no secrets)

