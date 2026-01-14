# WavePointToken

## Purpose

**WavePointToken** is a **non-transferable** ERC20 designed to represent points for the 1wave program and integrate with **Merkl**.

## Properties (Base)

- Address: `0xC9c9C776C45768Ce84ECb3526AE05d02AEFf290F`
- Chain: Base (8453)
- Verified: Sourcify ✅

## Key functions (high level)

- `mint(account, amount)` (authorized minters only)
- `burn(account, amount)` (authorized minters only)
- `mintBatch(accounts[], amounts[])`
- `burnForClaim(amount)` (user burns their own points when enabled)

## Security model

- Non-transferable by default (can be enabled/whitelisted via governance)
- Roles:
  - **Minter**: mint/burn
  - **Governor/Guardian**: toggle settings (transfer, whitelist, burn-for-claim)

## Relationship with Merkl / Points Service

- Merkl manages campaigns and rewards off-chain.
- The Points Service aggregates data and computes `totalPoints`.
- The on-chain token is the accounting unit of the points program.

