# Referrals

## Current behavior

The referral system in the Points Service is **in-memory**:

- `referee -> referrer`
- `referrer -> referralCount`

This means:

- referrals **do not persist** across restarts
- there is no cross-deploy / multi-instance deduplication.

## API

- `POST /points/referral` registers a referral (no self-referral, no overwrite)
- `GET /points/:address/referral` returns referrer and count

## Production hardening

- Persistence in a DB (Postgres/Mongo)
- Rate limiting and anti-abuse protections
- Idempotency keys / signatures if required

