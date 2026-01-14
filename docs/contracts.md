# Smart Contracts

Questa sezione descrive i principali contratti dell'ecosistema **1wave**.

## WaveSwap

- **File**: `src/WaveSwap.sol`
- **Ruolo**: AMM basato su **1inch Aqua** (AquaApp) che esegue gli swap.

**Caratteristiche principali**

- Swaps **exact in** ed **exact out**
- Funzioni di **quote** (stima importi senza eseguire transazioni)
- **Fee configurabili** in basis points
- Protezioni anti‑reentrancy ereditate da Aqua
- Aggiornamento automatico delle strategie tramite `publishPairs()`

**Modello di pricing (x · y = k)**

- Exact In: `amountOut = (amountInWithFee * balanceOut) / (balanceIn + amountInWithFee)`
- Exact Out: `amountIn = (balanceIn * amountOutWithFee).ceilDiv(balanceOut - amountOutWithFee)`

## AquaAdapter

- **File**: `adapter/AquaAdapter.sol`
- **Ruolo**: adapter che gestisce le strategie di liquidità su Aqua e integra il sistema di vault (FactorDAO).

**Caratteristiche principali**

- Gestione delle **pair** e delle fee
- Pubblicazione delle strategie su Aqua (`publishPairs`)
- Supporto **multi‑DEX** per pair
- Integrazione con **Chainlink** per il calcolo dei valori
- Storage tipo **Diamond Storage** per strategie, nonce, feed, pair list

## WavePointToken

- **File**: `src/WavePointToken.sol`
- **Ruolo**: token ERC20 **non‑transferable** usato come points token integrato con **Merkl**.

**Proprietà**

- **Network**: Base (Chain ID: 8453)
- **Address**: `0xC9c9C776C45768Ce84ECb3526AE05d02AEFf290F`
- **Name**: `1Wave Points`
- **Symbol**: `WAVE`

**Key features**

- Non‑transferable (salvo whitelist e toggle di governance)
- Gestione dei **minter** (solo minter autorizzati possono mint/burn)
- **Burn for claim** per tracciare future claim
- Batch minting per distribuzioni massive
- Integrazione con un `AccessControlManager` on‑chain

Per i dettagli di deployment, vedi anche la pagina **[Deployments](deployments.md)**.

