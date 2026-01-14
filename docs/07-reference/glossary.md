# Glossary

- **Aqua**: 1inch protocol for “app-based” strategies/AMMs.
- **AquaApp**: an application smart contract that executes operations on Aqua (here: `WaveSwap`).
- **Maker**: address that provides liquidity/strategies to Aqua (here: `AquaAdapter`).
- **Pair**: token pair + fee (BPS) configured on the adapter.
- **Strategy**: configuration (maker, token0, token1, feeBps, salt) used by Aqua to manage balances.
- **StudioProFactory**: FactorDAO factory used to create Pro vaults.
- **StudioProVault**: Pro vault created by the factory; emits deposit/withdraw events and vault operations.
- **Subgraph**: GraphQL indexer for on-chain events.
- **Merkl**: infrastructure for point programs and off-chain reward calculation using a “point” token.
- **Points Service**: HTTP service that aggregates subgraph + Merkl + referrals + boost.

