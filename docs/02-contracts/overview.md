# Smart contracts — overview

The `contracts/` package contains the core on-chain components of the product.

## Components

- **WaveSwap** (`src/WaveSwap.sol`): AquaApp that executes swaps.
- **AquaAdapter** (`adapter/AquaAdapter.sol`): maker adapter that configures pairs and publishes strategies to Aqua.
- **WavePointToken** (`src/WavePointToken.sol`): non-transferable points token designed to work with Merkl.

## Why this separation?

- WaveSwap focuses on **swap execution and quoting**.
- AquaAdapter manages **pairs/strategies** and their lifecycle (`publishPairs`, nonces, dock/ship).
- The subgraph indexes key events to produce the data model consumed by the frontend and points system.

## Deployments

See **[Addresses](../07-reference/addresses.md)** for on-chain values and endpoints.

