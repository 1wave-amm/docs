# Web3 configuration

## Chain

L’app abilita la sola chain:

- **Base** (8453)

## RPC

La RPC è costruita da `VITE_ALCHEMY_API_KEY`:

- `https://base-mainnet.g.alchemy.com/v2/<API_KEY>`

È una scelta intenzionale per evitare rate limits delle RPC pubbliche.

## Wallet connection

RainbowKit usa `VITE_WALLETCONNECT_PROJECT_ID` per WalletConnect.

## Contract addresses

L’address WaveSwap di default è hardcodata (o override via env):

- `0xa9e35ef3cc6493c61cc782c373a5f076aaae2f98`

Vedi anche **[Addresses](../07-reference/addresses.md)**.

