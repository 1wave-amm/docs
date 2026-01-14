# Create vault flow

This page describes the end-to-end pipeline used by the frontend to create a **Studio Pro Vault** and make it usable in 1wave.

## Step 1 — Deploy Vault

- Uses the FactorDAO Studio SDK (`StudioProFactory`).
- Configures:
  - whitelisted assets
  - fees (deposit/withdraw/management/performance)
  - adapter: includes AquaAdapter in `initialManagerAdapters` and `initialWithdrawAdapters`
  - denominator token and accounting adapter (Chainlink).

## Step 2 — Setup pairs + publishPairs (batch)

For each selected pair:

- builds a `setPair(token0, token1, feeBps, feed0, feed1, dexes=[WaveSwap])` transaction

Then adds:

- `publishPairs()`

And sends everything in a batch with:

- `executeByManager([...])` on the vault.

## Step 3 — Public strategy

Sets the public strategy (0, blocks) so the vault is usable.

## Step 4 — Deposit strategy

Sets a deposit strategy that (typically) runs `publishPairs()` on deposits to keep strategies up to date.

## Step 5 — Save metadata (Stats API)

If `VITE_STATS_API_BASE_URL` is configured, it saves metadata/strategy via:

- `POST /strategies/save`

using a user signature.

