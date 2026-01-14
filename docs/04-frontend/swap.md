# Swap (frontend)

## Obiettivo

Fornire una UI per:

- selezione token (pair)
- quote (exact in / exact out)
- slippage
- esecuzione swap su WaveSwap.

## Address WaveSwap

Default:

- `0xa9e35ef3cc6493c61cc782c373a5f076aaae2f98`

Override:

- `VITE_XYC_SWAP_ADDRESS`

## Dati

- Pairs/token list: principalmente da costanti e/o subgraph a seconda del flusso UI.
- Quote: calcolate via chiamate view (quote) o calcoli client-side (dipende dall’implementazione hook).

