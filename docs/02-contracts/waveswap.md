# WaveSwap

## Purpose

**WaveSwap** is an AquaApp implementing an AMM swap (constant product \(x \cdot y = k\)) with configurable fees (basis points), trading against strategies on **1inch Aqua**.

## Main API (high level)

- `quoteExactIn(strategy, zeroForOne, amountIn) -> amountOut`
- `quoteExactOut(strategy, zeroForOne, amountOut) -> amountIn`
- `swapExactIn(strategy, zeroForOne, amountIn, amountOutMin, to, data) -> amountOut`
- `swapExactOut(strategy, zeroForOne, amountOut, amountInMax, to, data) -> amountIn`

## Strategy

WaveSwap computes `strategyHash = keccak256(abi.encode(strategy))`.

Fields:

- `maker`: liquidity provider address (AquaAdapter)
- `token0`, `token1`
- `feeBps`
- `salt` (nonce/salt to make strategies unique)

## Swap mechanics (ExactIn)

1. Compute `amountOut` including fee.
2. `AQUA.pull(maker, strategyHash, tokenOut, amountOut, to)` (pull output).
3. `transferFrom` tokenIn from the user to the contract.
4. `approve` Aqua and `AQUA.push(...)` tokenIn into the strategy.
5. Verify the push and call `maker.publishPairs()` to keep strategies in sync.
6. Emit `SwapExactIn`.

## Events

- `SwapExactIn(vault, tokenIn, tokenOut, amountIn, amountOut)`
- `SwapExactOut(vault, tokenIn, tokenOut, amountIn, amountOut)`

The subgraph indexes these events into the `Swap` entity.

