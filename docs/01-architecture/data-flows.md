# Data flows

## Swap flow

1. Frontend costruisce la `Strategy` (maker, token0, token1, feeBps, salt).
2. L’utente firma e invia una tx a `WaveSwap.swapExactIn` o `swapExactOut`.
3. WaveSwap:
   - calcola quote con formula x·y=k (fee inclusive)
   - `pull` tokenOut dalla strategia Aqua verso il recipient
   - riceve tokenIn dall’utente e fa `push` a Aqua
   - chiama `publishPairs()` sul maker (AquaAdapter)
   - emette `SwapExactIn/Out`.
4. Il subgraph indicizza l’evento e salva una entity `Swap`.

## Vault flow (create + pairs)

1. Frontend usa FactorDAO SDK Studio:
   - deploy vault via `StudioProFactory`
   - configura pairs su adapter (setPair)
   - chiama `publishPairs()` (batch)
   - imposta public strategy / deposit strategy.
2. Subgraph:
   - su `VaultCreated` crea un template dataSource per la vault
   - indicizza `Deposit`/`Withdraw`, `PairSet`, `StrategyShipped`.

## Points flow

1. Points Service riceve request `GET /points/:address`.
2. Query subgraph:
   - deposits/withdrawals dell’utente
   - stato vault (pricePerShare, totalSupply, netVaultValue)
3. (opzionale) Query Merkl:
   - rewards per `POINTS_TOKEN_ADDRESS` su `CHAIN_ID`
4. Referral:
   - referralCount in-memory
5. Token boost:
   - check balance on-chain (RPC Base)
6. Calcolo finale:
   - breakdown + totalPoints.

