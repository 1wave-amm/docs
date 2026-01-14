# WaveSwap

## Scopo

**WaveSwap** è un’AquaApp che implementa uno swap AMM (formula x·y=k) con fee configurabile (basis points) e opera contro strategie su **1inch Aqua**.

## API principali (high level)

- `quoteExactIn(strategy, zeroForOne, amountIn) -> amountOut`
- `quoteExactOut(strategy, zeroForOne, amountOut) -> amountIn`
- `swapExactIn(strategy, zeroForOne, amountIn, amountOutMin, to, data) -> amountOut`
- `swapExactOut(strategy, zeroForOne, amountOut, amountInMax, to, data) -> amountIn`

## Strategy

WaveSwap calcola `strategyHash = keccak256(abi.encode(strategy))`.

Campi:

- `maker`: address che fornisce la liquidità (AquaAdapter)
- `token0`, `token1`
- `feeBps`
- `salt` (nonce/salt per distinguere strategie)

## Meccanica swap (ExactIn)

1. Calcola `amountOut` con fee.
2. `AQUA.pull(maker, strategyHash, tokenOut, amountOut, to)` (pull output).
3. `transferFrom` tokenIn dall’utente al contract.
4. `approve` ad Aqua e `AQUA.push(...)` tokenIn verso la strategia.
5. Verifica push e chiama `maker.publishPairs()` per riallineare strategie.
6. Emissione evento `SwapExactIn`.

## Eventi

- `SwapExactIn(vault, tokenIn, tokenOut, amountIn, amountOut)`
- `SwapExactOut(vault, tokenIn, tokenOut, amountIn, amountOut)`

Il subgraph indicizza questi eventi nella entity `Swap`.

