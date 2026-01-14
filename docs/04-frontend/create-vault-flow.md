# Create vault flow

Questa pagina descrive la pipeline end-to-end usata dal frontend per creare una **Studio Pro Vault** e abilitarla su 1wave.

## Step 1 — Deploy Vault

- Usa FactorDAO SDK Studio (`StudioProFactory`).
- Configura:
  - assets whitelisted
  - fee (deposit/withdraw/management/performance)
  - adapter: include AquaAdapter negli `initialManagerAdapters` e `initialWithdrawAdapters`
  - denominator token e accounting adapter (Chainlink).

## Step 2 — Setup pairs + publishPairs (batch)

Per ogni pair selezionata:

- costruisce una tx `setPair(token0, token1, feeBps, feed0, feed1, dexes=[WaveSwap])`

Poi aggiunge:

- `publishPairs()`

E invia tutto in batch con:

- `executeByManager([...])` sulla vault.

## Step 3 — Public strategy

Imposta la public strategy (0, blocks) in modo che la vault sia utilizzabile.

## Step 4 — Deposit strategy

Imposta una deposit strategy che esegue (tipicamente) `publishPairs()` su deposit per mantenere strategie aggiornate.

## Step 5 — Save metadata (Stats API)

Se `VITE_STATS_API_BASE_URL` è configurata, salva metadata/strategia via:

- `POST /strategies/save`

con signature dell’utente.

