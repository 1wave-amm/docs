# Points Service & API

Il **Points Service** è un backend che integra **Merkl** per calcolare e aggregare i punti dell'ecosistema 1wave.

## Architettura

1. **Merkl** traccia le attività on‑chain e calcola i punti base.
2. **Points Service** aggiunge logica custom:
   - punti basati su TVL e depositi
   - sistema di referral
   - boost per holder di token (1INCH, FCTR)
   - normalizzazione e combinazione dei dati.

## Setup

### Installazione

```bash
cd points-service
npm install
```

### Configurazione

```bash
cp .env.example .env
```

Variabili principali:

- `PORT`: porta HTTP (default `3001`)
- `SUBGRAPH_URL`: URL del subgraph 1wave
- `MERKL_API_URL`: base URL Merkl (default `https://api.merkl.xyz/v4`)
- `MERKL_API_KEY`: API key per Merkl (se richiesta)
- `MERKL_CREATOR_ADDRESS`: address che crea le Merkl campaigns
- `MERKL_DISTRIBUTOR_ADDRESS`: distributor (se richiesto da setup Merkl)
- `CHAIN_ID`: chain del points token (default `8453`)
- `RPC_URL`: usata per token boost checks (default `https://mainnet.base.org`)
- `POINTS_TOKEN_ADDRESS`: address del points token (WavePointToken / token punti Merkl)
- `TOKEN_1INCH_ADDRESS`, `TOKEN_FCTR_ADDRESS`: token per i boost
- Parametri di calcolo:
  - `POINTS_PER_USD_TVL`
  - `POINTS_PER_USD_DEPOSIT_PER_DAY`
  - `POINTS_PER_VAULT_OWNED`
  - `REFERRAL_BONUS_MULTIPLIER`
  - `TOKEN_BOOST_MULTIPLIER`

### Avvio

```bash
# Dev
npm run dev

# Prod
npm run build
npm start
```

## API Endpoints

### GET `/points/users/list`

Restituisce una lista di address che hanno interagito con vault (deposit/withdraw) usando il subgraph.

- Query: `?limit=5000` (max 20000)

### GET `/points/:address`

Restituisce i punti completi di un utente.

Risposta (schema semplificato):

```json
{
  "address": "0x...",
  "totalPoints": 1234.56,
  "breakdown": {
    "vaultOwnershipPoints": 500,
    "depositAmountPoints": 300,
    "timeBasedPoints": 200,
    "referralPoints": 50,
    "basePoints": 1000,
    "boostMultiplier": 1.2,
    "totalPoints": 1234.56
  },
  "vaultPositions": [],
  "referralCount": 5,
  "hasTokenBoost": true,
  "lastUpdated": 1234567890
}
```

### POST `/points/batch`

Calcola i punti per più address in un'unica chiamata.

Body:

```json
{
  "addresses": ["0x...", "0x..."]
}
```

### GET `/points/:address/merkl`

Restituisce solo i punti Merkl per un utente.

### GET `/points/:address/referral`

Restituisce le informazioni di referral per un utente.

### POST `/points/referral`

Registra un nuovo referral.

Body:

```json
{
  "referrer": "0x...",
  "referee": "0x..."
}
```

### GET `/points/merkl/campaigns`

Elenco delle Merkl campaigns configurate.

### GET `/points/merkl/campaigns/:campaignId/rewards`

Dettaglio rewards per una campagna Merkl specifica.

## Calcolo dei punti

La formula combina:

1. **Merkl Points**: punti base dalle campagne (es. 1 punto per $1000 depositati).
2. **Vault Ownership Points**: in base alla quota di TVL posseduta.
3. **Deposit Points**: importo depositato × tempo.
4. **Time Points**: bonus per holder di lungo periodo.
5. **Referral Points**: bonus referral.
6. **Token Boost**: moltiplicatore (es. 1.2x) se l'utente possiede token abilitati.

Note operative:

- Merkl aggiorna i dati circa ogni ~2 ore.
- I punti Merkl sono espressi in unità del points token.
- `chainId` nei Merkl API si riferisce alla chain del points token.

## Implementazione (high level)

Pipeline (per `GET /points/:address`):

1. Query subgraph → posizioni utente (deposit/withdraw aggregati, TVL stimata, giorni depositati).
2. Query Merkl → rewards per `POINTS_TOKEN_ADDRESS` (somma amount/pending a seconda della risposta API).
3. Referral count → in-memory.
4. Calcolo punti → somma componenti + referral bonus + token boost (RPC on-chain balance check).
