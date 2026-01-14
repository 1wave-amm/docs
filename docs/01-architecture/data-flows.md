# Data flows

## Swap flow

1. The frontend builds a `Strategy` (maker, token0, token1, feeBps, salt).
2. The user signs and submits a transaction to `WaveSwap.swapExactIn` or `swapExactOut`.
3. WaveSwap:
   - computes the quote using the \(x \cdot y = k\) formula (fee included)
   - `pull`s tokenOut from the Aqua strategy to the recipient
   - receives tokenIn from the user and `push`es it into Aqua
   - calls `publishPairs()` on the maker (AquaAdapter)
   - emits `SwapExactIn/Out`.
4. The subgraph indexes the event and stores a `Swap` entity.

## Vault flow (create + pairs)

1. The frontend uses the FactorDAO Studio SDK:
   - deploys a vault via `StudioProFactory`
   - configures pairs on the adapter (`setPair`)
   - calls `publishPairs()` (batched)
   - sets public strategy / deposit strategy.
2. The subgraph:
   - on `VaultCreated` creates a template dataSource for the vault
   - indexes `Deposit`/`Withdraw`, `PairSet`, `StrategyShipped`.

## Points flow

1. The Points Service receives `GET /points/:address`.
2. Subgraph query:
   - the user’s deposits/withdrawals
   - vault state (pricePerShare, totalSupply, netVaultValue)
3. (optional) Merkl query:
   - rewards for `POINTS_TOKEN_ADDRESS` on `CHAIN_ID`
4. Referrals:
   - in-memory referralCount
5. Token boost:
   - on-chain balance check (Base RPC)
6. Final computation:
   - breakdown + totalPoints.

