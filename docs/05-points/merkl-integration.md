# Merkl integration

## Role of Merkl

Merkl is used as a “calculation/indexing layer” for point programs:

- campaign setup (e.g. deposit tracking)
- rewards aggregation
- APIs to fetch rewards by token/campaign.

## APIs used by the Points Service

- `/campaigns` (list campaigns created by the creator)
- `/rewards` (campaign rewards, paginated)
- `/rewards/token/` (token rewards, paginated)

Important note:

- `chainId` in Merkl APIs refers to the chain where the points token is deployed (here: Base 8453), not necessarily the chain where the activity happens (depends on Merkl setup).

## Best practices

- Cache Merkl results (to avoid expensive “all token rewards complete” calls).
- Use paging/limits and async jobs for leaderboards.
- Validate response schema (Merkl can differ across versions/fields).

