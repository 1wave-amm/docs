# Product overview

**1wave** è un prodotto “liquidity as a service” su **Base** che combina:

- un DEX/AMM (WaveSwap) basato su **1inch Aqua**
- vault Pro (FactorDAO Studio) che usano un adapter Aqua (AquaAdapter) per gestire strategie/pairs
- un sistema di **points** (WavePointToken + Merkl + Points Service) per incentivare attività e retention.

## Cosa fa l’utente

### Swap

L’utente effettua swap su Base tramite WaveSwap, che opera contro strategie Aqua pubblicate dal maker (AquaAdapter).

### Vaults

L’utente può:

- depositare/ritirare in vault esistenti
- (se abilitato) creare una nuova vault Pro, configurare pair (setPair) e pubblicarle (publishPairs).

### Points

L’utente accumula punti in base a:

- TVL/ownership nelle vault
- depositi e durata
- referral
- boost se possiede determinati token (es. 1INCH/FCTR)
- campagne Merkl configurate.

## Componenti (high level)

- **Frontend (`app/`)**: UI Vite/React + wagmi/RainbowKit, integra swap/vault/points.
- **Subgraph (`backend/`)**: indicizza eventi (vault, pairs, swap) e fornisce dati via GraphQL.
- **Smart contracts (`contracts/`)**: WaveSwap, AquaAdapter, WavePointToken.
- **Points Service (`points-service/`)**: backend Express che aggrega subgraph + Merkl + referral + boost.

## Ambienti e scope

- Chain principale: **Base (8453)**
- Dati “source of truth” per elenco vault/pairs: **subgraph**
- Dati “enrichment” (se presenti): Stats API esterna (usata dal frontend)

