# FAQ

## Why Aqua / WaveSwap?

WaveSwap is an AquaApp that swaps against strategies managed on **1inch Aqua**. This allows you to:

- separate swap logic (app) from liquidity/strategy management (maker adapter)
- publish and update pairs/strategies in a controlled way.

## Why is the subgraph the source of truth for the vault list?

In the frontend, the existence of indexed `AquaPair` entities is the signal that a vault is “active” (it has published pairs) and should be displayed, even if external metrics are not available.

## Points token vs Merkl points

- `WavePointToken` is the on-chain (non-transferable) token used as the points unit.
- Merkl computes rewards/points off-chain via campaigns and exposes them via API.
- The Points Service aggregates Merkl + subgraph + referrals + boost.

## Do referrals persist?

Not currently: referrals are stored in-memory inside the Points Service process. Production requires a database.

