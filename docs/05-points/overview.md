# Points — overview

The 1wave points system is made of:

- **WavePointToken** (on-chain, non-transferable)
- **Merkl** (campaigns + off-chain rewards/points via API)
- **Points Service** (HTTP API that aggregates everything and computes final points)

## Output

For a given user address, the service returns:

- `totalPoints`
- a `breakdown` by component (vault ownership, deposit, time bonus, referral, Merkl, boost)
- `vaultPositions` (for explainability)

## Dependencies

- Subgraph (deposit/withdraw history and vault state)
- Merkl API (rewards)
- RPC Base (token boost checks)

