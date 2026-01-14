# API reference (Points Service)

Base URL (dev): `http://localhost:3001`

## GET `/health`

Health check.

## GET `/points/users/list`

List of unique users who interacted with vaults (deposit/withdraw), fetched from the subgraph.

- Query: `?limit=5000` (max 20000)

Response:

```json
{ "count": 123, "users": ["0x...", "0x..."] }
```

## GET `/points/:address`

Returns the full points payload for a user.

## POST `/points/batch`

Computes points for multiple addresses.

Body:

```json
{ "addresses": ["0x...", "0x..."] }
```

## GET `/points/:address/merkl`

Returns Merkl-only points (requires `POINTS_TOKEN_ADDRESS`).

## GET `/points/:address/referral`

Returns the referrer (if any) and the referralCount.

## POST `/points/referral`

Registers a referral.

Body:

```json
{ "referrer": "0x...", "referee": "0x..." }
```

## GET `/points/merkl/campaigns`

Lists campaigns created by `MERKL_CREATOR_ADDRESS`.

## GET `/points/merkl/campaigns/:campaignId/rewards`

Returns rewards for a specific campaign.

