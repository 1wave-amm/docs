# API reference (Points Service)

Base URL (dev): `http://localhost:3001`

## GET `/health`

Health check.

## GET `/points/users/list`

Lista utenti unici che hanno interagito con le vault (deposit/withdraw), estratti dal subgraph.

- Query: `?limit=5000` (max 20000)

Risposta:

```json
{ "count": 123, "users": ["0x...", "0x..."] }
```

## GET `/points/:address`

Restituisce i punti completi di un utente.

## POST `/points/batch`

Calcola punti per più address.

Body:

```json
{ "addresses": ["0x...", "0x..."] }
```

## GET `/points/:address/merkl`

Restituisce i soli punti Merkl (richiede `POINTS_TOKEN_ADDRESS`).

## GET `/points/:address/referral`

Restituisce il referrer (se presente) e referralCount.

## POST `/points/referral`

Registra un referral.

Body:

```json
{ "referrer": "0x...", "referee": "0x..." }
```

## GET `/points/merkl/campaigns`

Elenca le campaigns create dal `MERKL_CREATOR_ADDRESS`.

## GET `/points/merkl/campaigns/:campaignId/rewards`

Restituisce rewards per una specifica campaign.

