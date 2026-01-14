# Security

## On-chain

### WaveSwap

- Uses Aqua primitives (`nonReentrantStrategy` / safe balances) and input/output checks (slippage).
- Calls `publishPairs()` on the maker after swaps: ensure the maker implements the interface correctly, otherwise swaps can revert.

### WavePointToken

- Non-transferable di default
- Ruoli e governance toggles (minter, governor/guardian)

## Off-chain

### Points Service

- Rate limiting (required for batch/list endpoints)
- Caching for Merkl and subgraph calls
- A database for referrals and leaderboard
- Input validation (address format) is already enforced on key endpoints

### Subgraph

- Correct address/startBlock to avoid indexing unrelated data
- Monitor for reorgs and handler failures.

