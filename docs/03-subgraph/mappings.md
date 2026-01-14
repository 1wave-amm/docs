# Mappings (handlers)

Entry point: `backend/src/mappings.ts` exports the handlers:

- `handlers/factory.ts`
- `handlers/vault.ts`
- `handlers/aquaAdapter.ts`
- `handlers/waveSwap.ts`

## Factory: VaultCreated

- Filters vaults: it only indexes those that include **AquaAdapter** in `initialManagerAdapters`.
- Creates the vault template dataSource (`StudioProVault.create(...)`).
- Initializes the `Vault` entity.

## Vault: Deposit / Withdraw

- Stores `VaultDeposit` and `VaultWithdraw`.
- Updates `Vault` fields (name/symbol/totalSupply/pricePerShare/netVaultValue) by calling view functions on the vault contract.

## AquaAdapter events (emitted from the vault)

- `PairSet` → `AquaPair`
- `StrategyShipped` → `AquaStrategy`

## WaveSwap events

- `SwapExactIn/Out` → `Swap`

