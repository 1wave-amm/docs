# Mappings (handlers)

Entry point: `backend/src/mappings.ts` esporta i handler:

- `handlers/factory.ts`
- `handlers/vault.ts`
- `handlers/aquaAdapter.ts`
- `handlers/waveSwap.ts`

## Factory: VaultCreated

- Filtra le vault: indicizza solo quelle che includono l’**AquaAdapter** tra gli `initialManagerAdapters`.
- Crea la dataSource template per la vault (`StudioProVault.create(...)`).
- Inizializza la entity `Vault`.

## Vault: Deposit / Withdraw

- Salva `VaultDeposit` e `VaultWithdraw`.
- Aggiorna campi della `Vault` (name/symbol/totalSupply/pricePerShare/netVaultValue) chiamando funzioni view del vault contract.

## AquaAdapter events (emessi sulla vault)

- `PairSet` → `AquaPair`
- `StrategyShipped` → `AquaStrategy`

## WaveSwap events

- `SwapExactIn/Out` → `Swap`

