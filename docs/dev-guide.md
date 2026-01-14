# Dev Guide

Questa guida raccoglie i comandi principali per lavorare su **contracts** e **points-service**.

## Prerequisiti

- `forge` / Foundry toolchain
- `node` + `npm` o `yarn`
- Accesso RPC alla rete (es. Base) per i deploy.

---

## Smart Contracts (Foundry)

Directory: `contracts/`

### Build

```bash
cd contracts
forge build
```

### Test

```bash
forge test
```

### Format

```bash
forge fmt
```

### Gas snapshot

```bash
forge snapshot
```

### Deploy WaveSwap

Simulazione:

```bash
forge script script/DeployWaveSwap.s.sol:DeployWaveSwap --rpc-url <RPC_URL>
```

Deploy su Base (Aqua default):

```bash
forge script script/DeployWaveSwap.s.sol:DeployWaveSwap \
  --rpc-url <RPC_URL> \
  --broadcast \
  --verify
```

### Deploy WavePointToken

Configura `.env` in `contracts/`:

- `PRIVATE_KEY`
- `MINTER_ADDRESS`
- `ACCESS_CONTROL_MANAGER_ADDRESS`

Deploy:

```bash
forge script script/DeployWavePointToken.s.sol:DeployWavePointToken \
  --rpc-url <RPC_URL> \
  --broadcast \
  --verify
```

Per la verifica su Basescan vedi anche `contracts/DEPLOYED.md`.

---

## Points Service

Directory: `points-service/`

### Installazione

```bash
cd points-service
npm install
```

### Configurazione

```bash
cp .env.example .env
```

Compila:

- `SUBGRAPH_URL`
- `MERKL_API_KEY`
- `MERKL_CREATOR_ADDRESS`
- `POINTS_TOKEN_ADDRESS`
- `TOKEN_1INCH_ADDRESS`
- `TOKEN_FCTR_ADDRESS`

### Avvio

Dev:

```bash
npm run dev
```

Produzione:

```bash
npm run build
npm start
```

Per i dettagli degli endpoint vedi **[Points Service & API](points-service.md)**.
