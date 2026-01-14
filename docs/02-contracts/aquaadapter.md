# AquaAdapter

## Scopo

**AquaAdapter** è il maker adapter che:

- registra/configura pair (token0/token1, fee, Chainlink feeds)
- pubblica strategie su Aqua (`publishPairs`)
- mantiene nonce/salt e gestisce il lifecycle delle strategie.

## Concetti chiave

### Pair

Una pair è definita da:

- `token0`, `token1`
- `feeBps`
- feeds Chainlink per bilanciamento/valuation
- lista di DEX (AquaApp) abilitati per quella pair (es. WaveSwap)

### Strategy shipping

L’adapter “ship” una strategy ad Aqua per ogni DEX abilitato.

In sintesi:

- dock (se esiste una strategy precedente)
- crea nuova strategy con nonce/salt aggiornati
- ship ad Aqua e salva metadata in storage

## Funzioni principali (high level)

- `setPair(token0, token1, feeBps, chainlinkFeed0, chainlinkFeed1, dexes[])`
- `publishPairs()`

Il frontend usa FactorDAO StrategyBuilder per costruire transazioni `setPair(...)` e una `publishPairs()` finale, spesso in batch via `executeByManager` della vault.

## Eventi indicizzati

Nel subgraph (template `StudioProVault`):

- `PairSet(token0, token1, feeBps, pairHash)` → entity `AquaPair`
- `StrategyShipped(pairHash, strategyHash)` → entity `AquaStrategy`

