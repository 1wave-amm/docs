# Product overview

**1wave** is a “liquidity as a service” product on **Base** that combines:

- a DEX/AMM (WaveSwap) built on **1inch Aqua**
- Pro vaults (FactorDAO Studio) that use an Aqua adapter (AquaAdapter) to manage pairs/strategies
- a **points system** (WavePointToken + Merkl + Points Service) to incentivize activity and retention.

## What users do

### Swap

Users swap on Base through WaveSwap, which trades against Aqua strategies published by the maker (AquaAdapter).

### Vaults

Users can:

- deposit/withdraw into existing vaults
- (if enabled) create a new Pro vault, configure pairs (`setPair`) and publish them (`publishPairs`).

### Points

Users earn points based on:

- vault TVL/ownership
- deposits and holding duration
- referrals
- a boost if they hold specific tokens (e.g. 1INCH/FCTR)
- configured Merkl campaigns.

## Components (high level)

- **Frontend (`app/`)**: Vite/React UI + wagmi/RainbowKit; integrates swap/vaults/points.
- **Subgraph (`backend/`)**: indexes events (vaults, pairs, swaps) and exposes a GraphQL data model.
- **Smart contracts (`contracts/`)**: WaveSwap, AquaAdapter, WavePointToken.
- **Points Service (`points-service/`)**: Express backend that aggregates subgraph + Merkl + referrals + boost.

## Environments & scope

- Main chain: **Base (8453)**
- Source of truth for vault/pair discovery: **the subgraph**
- Optional enrichment: an external Stats API (used by the frontend when configured)

