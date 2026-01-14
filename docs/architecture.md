# Overview & Architecture

Questa pagina descrive la visione d'insieme di **1wave**: DEX, adapter, vault e sistema punti.

## Componenti principali

- **WaveSwap**: AMM (AquaApp) per eseguire gli swap.
- **AquaAdapter**: adapter che gestisce le strategie di liquidità su Aqua.
- **Vault (FactorDAO)**: gestisce i fondi e utilizza AquaAdapter.
- **WavePointToken + Points Service**: sistema di punti non‑transferable integrato con Merkl.

## Diagramma alto livello

```text
┌─────────────┐
│   Vault     │
│ (FactorDAO) │
└──────┬──────┘
       │ uses
       ▼
┌─────────────┐      ┌──────────────┐      ┌─────────────┐
│AquaAdapter  │──────▶│   Aqua       │◀─────│  WaveSwap   │
│  (Maker)    │ ship  │  Protocol    │ pull │  (App)      │
└─────────────┘       └──────────────┘ push └─────────────┘
       │                      │
       │                      │
       └──────────────────────┘
              manages
              strategies
```

## Flow di swap

1. AquaAdapter crea e pubblica le strategie su Aqua (`publishPairs`).
2. L'utente chiama WaveSwap (`swapExactIn` / `swapExactOut`).
3. WaveSwap:
   - calcola amountOut / amountIn con formula x·y=k
   - trasferisce i token verso la strategia su Aqua
   - riceve i token di output
4. Dopo lo swap, WaveSwap chiama `publishPairs()` per aggiornare le strategie.

## Sistema di punti

1. Attività (depositi, ownership, swap, referral) vengono tracciate.
2. **Merkl** calcola i punti base per le campagne configurate.
3. Il **Points Service** aggrega:
   - dati da Merkl
   - dati da subgraph e vault
   - informazioni di referral
   - token boost.
4. I risultati vengono esposti via API HTTP e riflessi nel `WavePointToken` su Base.

Per i dettagli sui contratti specifici vedi **[Smart Contracts](contracts.md)**, per l'API vedi **[Points Service & API](points-service.md)**.
