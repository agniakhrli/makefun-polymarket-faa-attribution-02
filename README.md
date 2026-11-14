# FAA Outage Attribution Forecaster

[![make.fun](https://make.fun/badge.svg)](https://make.fun)

A program that forecasts Polymarket Yes prices minute by minute, 4 hours ahead. For each market it estimates the market's own volatility (sigma) from the standard deviation of its recent 1-minute price moves (last 120 minutes, clamped to [0.0012, 0.009]) and forecasts five quantiles (0.05, 0.25, 0.5, 0.75, 0.95) as a random walk widening with the square root of the horizon. Written for the make.fun bounty "Forecast Polymarket's FAA outage attribution prices minute by minute, 4 hours ahead".

Run with Node 22: `node main.ts`. It reads every case file in `$MAKEFUN_INPUT_DIR` (or `/input`) and writes one forecast file per case to `$MAKEFUN_OUTPUT_DIR` (or `/output`), deterministically, with no network access. On the practice backtest (cases truncated 240 minutes before the checkpoint) it scores a mean pinball loss of 0.3906 against the house baseline's 0.4296.
