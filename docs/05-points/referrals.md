# Referrals

## Stato attuale

Il referral system nel Points Service è **in-memory**:

- `referee -> referrer`
- `referrer -> referralCount`

Implica:

- i referral **non persistono** a restart
- non c’è dedup cross-deploy / multi-instance.

## API

- `POST /points/referral` registra un referral (no self-referral, no overwrite)
- `GET /points/:address/referral` restituisce referrer e count

## Production hardening

- Persistenza su DB (Postgres/Mongo)
- Rate limit e anti-abuse
- Idempotency keys / signatures se necessario

