# WavePointToken

## Scopo

**WavePointToken** è un token ERC20 **non-transferable** progettato per rappresentare punti del programma 1wave e integrarsi con **Merkl**.

## Proprietà (Base)

- Address: `0xC9c9C776C45768Ce84ECb3526AE05d02AEFf290F`
- Chain: Base (8453)
- Verified: Sourcify ✅

## Funzioni chiave (high level)

- `mint(account, amount)` (solo minter autorizzati)
- `burn(account, amount)` (solo minter autorizzati)
- `mintBatch(accounts[], amounts[])`
- `burnForClaim(amount)` (utente brucia propri punti se abilitato)

## Security model

- Non-transferable di default (può essere sbloccato/whitelistato da governance)
- Ruoli:
  - **Minter**: mint/burn
  - **Governor/Guardian**: toggle settings (transfer, whitelist, burn-for-claim)

## Relazione con Merkl / Points Service

- Merkl gestisce campaigns e rewards off-chain.
- Il Points Service aggrega dati e calcola `totalPoints`.
- Il token on-chain è l’unità “contabile” del programma punti.

