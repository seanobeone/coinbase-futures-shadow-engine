# Coinbase Futures Shadow Engine

A Python-based research and simulation engine for evaluating directional cryptocurrency futures strategies without granting the software live order authority.

## Purpose

The project demonstrates how a trading idea can be tested in a controlled SHADOW environment before any consideration of production execution. It processes public Coinbase market data, evaluates long and short conditions, simulates position entries and exits, applies configurable risk controls, and records hypothetical results for later analysis.

**This public portfolio edition does not place live orders and does not contain Coinbase credentials, account information, private production configuration, or live execution authority.**

## Core Capabilities

- Public Coinbase five-minute candle retrieval
- EMA-based trend analysis
- RSI momentum analysis
- Short-term return and relative-volume filters
- LONG, SHORT, and FLAT signal qualification
- Configurable simulated capital and per-trade risk
- Maximum concurrent-position controls
- Simulated stop-loss and take-profit exits
- Signal-flip exits
- Hypothetical realized and unrealized P/L tracking
- Atomic local state persistence
- JSONL event logging for research and review
- Explicit `SHADOW` mode with `live_authority: false`

## Architecture

```text
Coinbase Public Market Data
          |
          v
   Candle Processing
          |
          v
 EMA / RSI / Return / Volume
          |
          v
 Long / Short Qualification
          |
          v
  SHADOW Risk Controls
          |
          v
 Simulated Position Engine
          |
          v
 State + Research Event Logs
```

## Safety Design

The public engine is deliberately separated from production order execution. It uses public market-data requests and maintains hypothetical positions locally. Runtime state, trade logs, credentials, private configuration, and account-specific information are excluded from source control.

## Configuration

Copy `config/futures_shadow.example.json` and adjust the SHADOW research parameters. Keep `mode` set to `SHADOW` and `live_authority` set to `false`.

Example controls include simulated capital, risk per trade, maximum open positions, contract limits, stop-loss percentage, and take-profit percentage.

## Run

```bash
python src/futures_shadow_engine.py
```

The engine performs a market-analysis cycle approximately once per minute and writes local SHADOW state/results. Runtime output files are ignored by Git.

## Portfolio Focus

This repository demonstrates Python automation, API integration, quantitative signal processing, risk-control design, state management, fault handling, and safety separation between research and production execution.

## Disclaimer

This project is for software engineering, research, and portfolio demonstration purposes. Simulated results do not represent guaranteed future performance and this repository does not provide financial advice.
