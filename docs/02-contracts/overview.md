# Smart contracts — overview

Il package `contracts/` contiene i contratti core del prodotto.

## Componenti

- **WaveSwap** (`src/WaveSwap.sol`): AquaApp che esegue gli swap.
- **AquaAdapter** (`adapter/AquaAdapter.sol`): maker adapter che configura pair e pubblica strategie su Aqua.
- **WavePointToken** (`src/WavePointToken.sol`): token punti non-transferable, compatibile con Merkl.

## Perché questa separazione?

- WaveSwap si occupa **solo** di swap e quote.
- AquaAdapter gestisce **strategie/pairs** e il lifecycle (publishPairs, nonce, dock/ship).
- Il subgraph indicizza i principali eventi per costruire il modello dati usato da frontend e points.

## Deployments

Vedi **[Addresses](../07-reference/addresses.md)** per i valori on-chain e endpoints.

