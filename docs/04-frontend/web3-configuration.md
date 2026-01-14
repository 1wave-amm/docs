# Web3 configuration

## Chain

The app enables a single chain:

- **Base** (8453)

## RPC

The RPC URL is built from `VITE_ALCHEMY_API_KEY`:

- `https://base-mainnet.g.alchemy.com/v2/<API_KEY>`

This is an intentional choice to avoid public RPC rate limits.

## Wallet connection

RainbowKit uses `VITE_WALLETCONNECT_PROJECT_ID` for WalletConnect.

## Contract addresses

The default WaveSwap address is hardcoded (or can be overridden via env):

- `0xa9e35ef3cc6493c61cc782c373a5f076aaae2f98`

See also **[Addresses](../07-reference/addresses.md)**.

