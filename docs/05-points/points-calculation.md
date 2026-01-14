# Points calculation

Questa pagina documenta la logica di calcolo implementata nel Points Service.

## Input principali

- Posizioni utente per vault (da subgraph):
  - `valueUSD` (stima)
  - `tvlUSD` (stima)
  - `totalDepositedUSD` (stima)
  - `daysDeposited`
- `merklPoints` (somma rewards Merkl)
- `referralCount`
- `hasTokenBoost` (balance check su token abilitati)

## Componenti

### Vault ownership points

Idea: premiare la quota di TVL posseduta.

### Deposit amount points

Idea: premiare quantità depositata × tempo.

### Time based points

Bonus per holder > 30 giorni (crescita fino a ~2x su 1 anno, con peso ridotto).

### Vault count points

Bonus per numero di vault distinte.

### Referral points

Bonus proporzionale a `basePoints` e al numero referral.

### Token boost

Moltiplicatore applicato se l’utente possiede almeno uno tra `TOKEN_1INCH_ADDRESS` o `TOKEN_FCTR_ADDRESS`.

## Output

- `breakdown` completo
- `totalPoints = (basePoints + referralPoints) * boostMultiplier`

