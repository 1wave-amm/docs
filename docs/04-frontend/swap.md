# Swap (frontend)

## Goal

Provide a UI for:

- token selection (pair)
- quoting (exact in / exact out)
- slippage control
- executing swaps on WaveSwap.

## Address WaveSwap

Default:

- `0xa9e35ef3cc6493c61cc782c373a5f076aaae2f98`

Override:

- `VITE_XYC_SWAP_ADDRESS`

## Dati

- Pairs/token lists: mostly from constants and/or the subgraph depending on the UI flow.
- Quotes: computed via view calls (quote functions) or client-side math (depending on the hook implementation).

