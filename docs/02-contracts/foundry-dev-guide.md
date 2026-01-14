# Foundry dev guide

Directory: `contracts/`

## Build / test / format

```bash
cd contracts
forge build
forge test
forge fmt
```

## Deploy (WaveSwap)

Simulazione:

```bash
forge script script/DeployWaveSwap.s.sol:DeployWaveSwap --rpc-url <RPC_URL>
```

Broadcast + verify:

```bash
forge script script/DeployWaveSwap.s.sol:DeployWaveSwap \
  --rpc-url <RPC_URL> \
  --broadcast \
  --verify
```

## Deploy (WavePointToken)

Prerequisiti `.env`:

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

## Verify (Basescan)

Vedi `contracts/DEPLOYED.md` e script `verify-basescan.sh`.

