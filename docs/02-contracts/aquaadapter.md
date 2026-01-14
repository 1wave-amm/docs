# AquaAdapter

## Purpose

**AquaAdapter** is the maker adapter that:

- registers/configures pairs (token0/token1, fee, Chainlink feeds)
- publishes strategies to Aqua (`publishPairs`)
- maintains nonce/salt and manages strategy lifecycle.

## Key concepts

### Pair

A pair is defined by:

- `token0`, `token1`
- `feeBps`
- Chainlink feeds for balancing/valuation
- the list of enabled DEXes (AquaApps) for that pair (e.g. WaveSwap)

### Strategy shipping

The adapter “ships” a strategy to Aqua for each enabled DEX.

In practice:

- dock (if a previous strategy exists)
- create a new strategy with updated nonce/salt
- ship to Aqua and persist metadata in storage

## Main functions (high level)

- `setPair(token0, token1, feeBps, chainlinkFeed0, chainlinkFeed1, dexes[])`
- `publishPairs()`

The frontend uses the FactorDAO StrategyBuilder to build `setPair(...)` transactions and a final `publishPairs()` call, often batched via the vault’s `executeByManager`.

## Indexed events

In the subgraph (via the `StudioProVault` template):

- `PairSet(token0, token1, feeBps, pairHash)` → entity `AquaPair`
- `StrategyShipped(pairHash, strategyHash)` → entity `AquaStrategy`

