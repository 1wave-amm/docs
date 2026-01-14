# FAQ

## Perché Aqua / WaveSwap?

WaveSwap è un’AquaApp che esegue swap contro strategie gestite su **1inch Aqua**. Questo permette di:

- separare logica di swap (app) e gestione strategie/liquidità (maker adapter)
- aggiornare/publishare pair/strategie in modo controllato.

## Perché il subgraph è “source of truth” per la lista vault?

Nel frontend, la presenza di `AquaPair` indicizzate è il segnale che una vault è “attiva” (ha pairs pubblicate) e quindi va mostrata, anche se le metriche esterne non sono disponibili.

## Points token vs Merkl points

- `WavePointToken` è il token on-chain (non-transferable) usato come unità punti.
- Merkl calcola rewards/points off-chain tramite campagne e li espone via API.
- Il Points Service aggrega Merkl + subgraph + referral + boost.

## I referral persistono?

Attualmente no: sono in-memory nel processo del Points Service. Per produzione serve DB.

