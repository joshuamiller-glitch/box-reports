# REPORT C1-F1 - five-minute trend family on other instruments (frozen NQ rules, no re-fit)

Pre-registration: `outputs/autopilot/PREREG_AUTOPILOT.md` (C1-F1). Baseline = live pair `B.Cfg(wk_floor=8,wk_loss_pb=None)` (weekly Sharpe 1.46 / 2.83 / 2.30), computed in a clean process (`t3_score` imports `b11_nt8` first). Robustness: the default-config pair (1.35 / 1.65 / 2.26) is a weaker baseline; since every uplift here is negative against the stronger one, nothing changes against the weaker. Spans: clean 2023-08..2025-07, H1 2025-08..2026-02-06, H2 2026-02-07..10-13, all-in 2023-08..2026-10-13. UNTOUCHED never read. No parameter was fitted.

## Method and fill model

- Signals: the `b10_gsig` generators used for the NQ books, on each instrument's purchased 1-minute bars (Databento GLBX.MDP3 ohlcv-1m continuous .v.0, 2013-2026; RTY from 2017-06; difference back-adjusted at roll ids; missing minutes forward-filled with zero volume). **8 of the 11 books run**: #1 EMA 9/21+ADX20, #2 EMA 9/21, #3 WMA 50/200 (1-min), #5 ZLEMA200, #6 Supertrend ATR14 x3, #7 MACD 12/26 zero, #9 MACD 5/35 zero + EMA200, #11 MACD 5/35 zero. The three delta-confirmed books (#4, #8, #10) need signed trade delta that ohlcv-1m does not carry and were not run.
- Engine: market entry at the next 1-min open after the tf-bar close, entries 18:05-16:40 ET, flat at the open of the 16:40 bar, one trade at a time per book, stop = target bracket (stop first on a spanning bar), per-book 5R/-2R daily rule (R = $12,000), no combined locks.
- Costs: slippage per side ES/ZN/6E/6J 0.5 tick, RTY/GC/CL/NQ 1 tick; commission $4.36 per contract round trip (T3 S2 convention, an assumption). 2x slippage = doubled ticks.
- **Two bracket conventions**, both fixed before any result: `adr` = stop = target = 0.193 x prior-20-day average range (T3 S2 convention, equal R, varies daily); `fx` = constant bracket in points = 60 x (instrument median ADR20 / NQ median ADR20 over 2023-08..2026-10), the analogue of NQ's fixed 60 pt. A cell counts as FOUND only if it passes under both.
- Sleeve sizing: the 8-book equal-weight ensemble is scaled so its clean weekly std = share x the pair's clean weekly std; additive C = P + sleeve, constant-risk C = (1-s) P + sleeve.
- Gating null (amended gate 4): per instrument and convention, 300 random-entry draws (same long/short signal counts per book, random eligible entry bars, same bracket, exit and daily rule), ensemble standalone all-in weekly Sharpe p95. The circular-shift null rank is reported and gates only for hedge claims (worst-decile correlation < 0).
- Engine validation on NQ: with the fixed 60-pt bracket the per-book entry minutes match the original V5 trade list on 2,717 of 3,523 trades (77%, exact 1-minute); the NQ ensemble is shown as a control.

## 1. Standalone ensemble (8 books, tf5, 1x slippage)

Pair window = 2023-08..2026-10 (weekly Sharpe, after costs). `pre` = 2013(2017 RTY)-2023-07, untouched by any choice here. Bracket: `adr` median ticks / `fx` points. Own-null = 300 random-entry draws (same signal counts, same bracket/exit/daily rule).

| instr | conv | bracket | net/yr $ (at R=$12k/book) | all-in | clean | H1 | H2 | pre-2023 | yrs pre | null p95 | null median | beats null p95? | corr pair all / worst-decile |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES | adr | 32 ticks | -484k | -1.89 | -1.87 | -1.26 | -2.32 | -3.44 | 10.6 | -1.77 | -2.62 | no | -0.23 / 0.18 |
| ES | fx | 12 pts | -175k | -0.64 | -0.88 | 0.27 | -0.72 | -1.37 | 10.6 | -1.84 | -2.78 | yes | -0.22 / 0.03 |
| RTY | adr | 75 ticks | -452k | -1.80 | -2.62 | -1.80 | 0.12 | -1.98 | 6.1 | -2.63 | -3.41 | yes | -0.10 / -0.20 |
| RTY | fx | 7.2 pts | -382k | -1.44 | -2.03 | -0.90 | -0.35 | -1.39 | 6.1 | -3.08 | -4.03 | yes | -0.10 / -0.24 |
| GC | adr | 44 ticks | -536k | -2.16 | -2.60 | -1.73 | -1.00 | -3.27 | 10.6 | -2.16 | -3.05 | no | 0.07 / -0.59 |
| GC | fx | 7.8 pts | -567k | -2.31 | -3.19 | -3.58 | 0.48 | -1.57 | 10.6 | -2.44 | -3.32 | yes | -0.04 / -0.39 |
| CL | adr | 36 ticks | -842k | -3.18 | -3.95 | -4.49 | -0.16 | -3.70 | 10.6 | -4.44 | -5.53 | yes | -0.07 / -0.46 |
| CL | fx | 0.37 pts | -806k | -2.88 | -3.99 | -3.08 | -0.26 | -3.27 | 10.6 | -5.57 | -6.73 | yes | 0.08 / -0.45 |
| ZN | adr | 7 ticks | -2,169k | -8.27 | -7.91 | -9.55 | -7.98 | -8.12 | 10.6 | -14.54 | -16.01 | yes | 0.04 / 0.15 |
| ZN | fx | 0.09375 pts | -2,670k | -10.35 | -11.77 | -8.55 | -8.15 | -9.79 | 10.6 | -19.77 | -21.90 | yes | 0.02 / 0.00 |
| 6E | adr | 30 ticks | -635k | -2.52 | -2.02 | -4.37 | -2.77 | -2.31 | 10.6 | -5.58 | -6.73 | yes | 0.08 / 0.24 |
| 6E | fx | 0.0012 pts | -698k | -2.74 | -2.32 | -4.50 | -2.97 | -3.65 | 10.6 | -6.49 | -7.52 | yes | -0.03 / 0.30 |
| 6J | adr | 24 ticks | -963k | -3.56 | -3.22 | -5.48 | -2.92 | -3.18 | 10.6 | -7.08 | -8.08 | yes | -0.10 / 0.48 |
| 6J | fx | 9.5e-06 pts | -1,152k | -4.11 | -4.68 | -5.79 | -1.44 | -4.49 | 10.6 | -8.05 | -9.20 | yes | -0.05 / -0.07 |
| NQ (control) | adr | 130 ticks | -103k | -0.42 | -0.47 | 1.15 | -1.55 | -1.90 | 10.6 | -0.23 | -1.06 | no | -0.23 / 0.42 |
| NQ (control) | fx | 60 pts | 100k | 0.37 | 0.12 | 0.81 | 0.64 | -0.11 | 10.6 | -0.31 | -1.15 | yes | -0.31 / 0.10 |

Every instrument loses money standalone in the pair window under both conventions (all-in Sharpe -0.64 to -10.4); the NQ control with the fixed 60-pt bracket is +0.37 (clean +0.12, H1 +0.81, H2 +0.64; pre-2023 -0.11). The signals beat the random-entry null on most instruments, so there is some timing information, but the cost of a tick or half tick against a small bracket (median `adr` bracket in ticks: NQ 130, ES 32, RTY 75, GC 44, CL 36, 6E 30, 6J 24, ZN 7) exceeds it. Pre-2023 history is also negative everywhere (ES -1.4 to -3.4, 13 years), so this is not a recent-regime artefact.

## 2. Additive uplift in weekly Sharpe vs the live pair (ensemble tf5; sleeve scaled to share of the pair's clean weekly vol)

Gate 3 needs >= +0.10 on clean, H1 and H2 separately and worst week not worse by more than the share.

| instr | conv | share | clean | H1 | H2 | all-in | worst-week change % | boot 90% CI (all-in uplift) | shift-null rank | worst-decile corr | g3 | g4 | g5 plateau (frac) | g5 2x slip | g6 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES | adr | 10% | -0.17 | -0.24 | -0.14 | -0.17 | +8 | [-0.27, -0.07] | 0.99 | 0.18 | n | n | n (0.00) | n | Y |
| ES | adr | 20% | -0.35 | -0.48 | -0.31 | -0.36 | +23 | [-0.56, -0.16] | 0.99 | 0.18 | n | n | n (0.00) | n | Y |
| ES | adr | 50% | -0.95 | -1.19 | -1.14 | -1.02 | +68 | [-1.49, -0.54] | 0.99 | 0.18 | n | n | n (0.00) | n | Y |
| ES | fx | 10% | -0.08 | 0.10 | 0.02 | -0.04 | +5 | [-0.14, 0.06] | 0.99 | 0.03 | n | n | n (0.00) | n | Y |
| ES | fx | 20% | -0.17 | 0.14 | 0.00 | -0.10 | +16 | [-0.30, 0.11] | 0.99 | 0.03 | n | n | n (0.00) | n | Y |
| ES | fx | 50% | -0.50 | -0.02 | -0.24 | -0.39 | +56 | [-0.87, 0.10] | 0.99 | 0.03 | n | n | n (0.00) | n | Y |
| RTY | adr | 10% | -0.26 | -0.34 | 0.11 | -0.19 | +10 | [-0.29, -0.09] | 0.89 | -0.20 | n | n | n (0.00) | n | Y |
| RTY | adr | 20% | -0.53 | -0.69 | 0.20 | -0.40 | +25 | [-0.60, -0.20] | 0.89 | -0.20 | n | n | n (0.00) | n | Y |
| RTY | adr | 50% | -1.32 | -1.62 | 0.26 | -1.06 | +71 | [-1.54, -0.59] | 0.89 | -0.20 | n | n | n (0.00) | n | Y |
| RTY | fx | 10% | -0.21 | -0.18 | 0.07 | -0.14 | +6 | [-0.25, -0.05] | 0.89 | -0.24 | n | n | n (0.00) | n | Y |
| RTY | fx | 20% | -0.42 | -0.37 | 0.11 | -0.31 | +15 | [-0.51, -0.12] | 0.89 | -0.24 | n | n | n (0.00) | n | Y |
| RTY | fx | 50% | -1.06 | -0.95 | 0.02 | -0.85 | +47 | [-1.33, -0.40] | 0.89 | -0.24 | n | n | n (0.00) | n | Y |
| GC | adr | 10% | -0.27 | -0.31 | -0.05 | -0.22 | +10 | [-0.32, -0.14] | 0.13 | -0.59 | n | n | n (0.00) | n | Y |
| GC | adr | 20% | -0.55 | -0.61 | -0.11 | -0.46 | +26 | [-0.65, -0.29] | 0.13 | -0.59 | n | n | n (0.00) | n | Y |
| GC | adr | 50% | -1.32 | -1.37 | -0.37 | -1.13 | +75 | [-1.56, -0.75] | 0.13 | -0.59 | n | n | n (0.00) | n | Y |
| GC | fx | 10% | -0.32 | -0.58 | 0.12 | -0.25 | +13 | [-0.36, -0.15] | 0.72 | -0.39 | n | n | n (0.00) | n | Y |
| GC | fx | 20% | -0.64 | -1.11 | 0.21 | -0.52 | +33 | [-0.73, -0.32] | 0.72 | -0.39 | n | n | n (0.00) | n | Y |
| GC | fx | 50% | -1.58 | -2.37 | 0.27 | -1.32 | +92 | [-1.78, -0.87] | 0.72 | -0.39 | n | n | n (0.00) | n | Y |
| CL | adr | 10% | -0.39 | -0.66 | 0.02 | -0.34 | +17 | [-0.46, -0.23] | 0.79 | -0.46 | n | n | n (0.00) | n | Y |
| CL | adr | 20% | -0.80 | -1.33 | 0.01 | -0.70 | +40 | [-0.93, -0.49] | 0.79 | -0.46 | n | n | n (0.00) | n | Y |
| CL | adr | 50% | -1.93 | -3.14 | -0.14 | -1.74 | +111 | [-2.23, -1.26] | 0.79 | -0.46 | n | n | n (0.00) | n | Y |
| CL | fx | 10% | -0.41 | -0.41 | -0.11 | -0.34 | +15 | [-0.45, -0.24] | 0.13 | -0.45 | n | n | n (0.00) | n | Y |
| CL | fx | 20% | -0.81 | -0.85 | -0.23 | -0.68 | +36 | [-0.89, -0.48] | 0.13 | -0.45 | n | n | n (0.00) | n | Y |
| CL | fx | 50% | -1.93 | -2.12 | -0.62 | -1.62 | +99 | [-2.09, -1.17] | 0.13 | -0.45 | n | n | n (0.00) | n | Y |
| ZN | adr | 10% | -0.79 | -1.24 | -0.80 | -0.86 | +23 | [-0.99, -0.74] | 0.32 | 0.15 | n | n | n (0.00) | n | Y |
| ZN | adr | 20% | -1.58 | -2.43 | -1.58 | -1.71 | +46 | [-1.96, -1.48] | 0.32 | 0.15 | n | n | n (0.00) | n | Y |
| ZN | adr | 50% | -3.69 | -5.40 | -3.66 | -3.96 | +117 | [-4.54, -3.45] | 0.68 | 0.15 | n | n | n (0.00) | n | Y |
| ZN | fx | 10% | -1.18 | -0.98 | -0.81 | -1.07 | +23 | [-1.22, -0.94] | 0.41 | 0.00 | n | n | n (0.00) | n | Y |
| ZN | fx | 20% | -2.34 | -1.94 | -1.61 | -2.12 | +47 | [-2.41, -1.88] | 0.59 | 0.00 | n | n | n (0.00) | n | Y |
| ZN | fx | 50% | -5.46 | -4.48 | -3.77 | -4.90 | +128 | [-5.53, -4.38] | 0.59 | 0.00 | n | n | n (0.00) | n | Y |
| 6E | adr | 10% | -0.21 | -0.43 | -0.36 | -0.28 | +14 | [-0.38, -0.19] | 0.18 | 0.24 | n | n | n (0.00) | n | Y |
| 6E | adr | 20% | -0.43 | -0.86 | -0.71 | -0.56 | +28 | [-0.75, -0.39] | 0.18 | 0.24 | n | n | n (0.00) | n | Y |
| 6E | adr | 50% | -1.06 | -2.12 | -1.66 | -1.36 | +74 | [-1.80, -0.97] | 0.18 | 0.24 | n | n | n (0.00) | n | Y |
| 6E | fx | 10% | -0.23 | -0.39 | -0.35 | -0.28 | +12 | [-0.38, -0.19] | 0.62 | 0.30 | n | n | n (0.00) | n | n |
| 6E | fx | 20% | -0.47 | -0.79 | -0.72 | -0.57 | +24 | [-0.77, -0.40] | 0.62 | 0.30 | n | n | n (0.00) | n | n |
| 6E | fx | 50% | -1.19 | -1.98 | -1.74 | -1.43 | +61 | [-1.87, -1.03] | 0.62 | 0.30 | n | n | n (0.00) | n | n |
| 6J | adr | 10% | -0.31 | -0.85 | -0.26 | -0.37 | +14 | [-0.49, -0.26] | 0.89 | 0.48 | n | n | n (0.00) | n | n |
| 6J | adr | 20% | -0.64 | -1.65 | -0.54 | -0.76 | +29 | [-0.99, -0.55] | 0.89 | 0.48 | n | n | n (0.00) | n | n |
| 6J | adr | 50% | -1.60 | -3.55 | -1.49 | -1.90 | +72 | [-2.42, -1.41] | 0.11 | 0.48 | n | n | n (0.00) | n | n |
| 6J | fx | 10% | -0.47 | -0.88 | -0.10 | -0.44 | +13 | [-0.56, -0.33] | 0.71 | -0.07 | n | n | n (0.00) | n | Y |
| 6J | fx | 20% | -0.94 | -1.71 | -0.23 | -0.90 | +29 | [-1.13, -0.68] | 0.71 | -0.07 | n | n | n (0.00) | n | Y |
| 6J | fx | 50% | -2.27 | -3.71 | -0.74 | -2.18 | +77 | [-2.70, -1.69] | 0.29 | -0.07 | n | n | n (0.00) | n | Y |
| NQ | adr | 10% | -0.04 | 0.18 | -0.04 | -0.01 | +8 | [-0.12, 0.09] | 1.00 | 0.42 | n | n | n (0.00) | n | n |
| NQ | adr | 20% | -0.09 | 0.30 | -0.12 | -0.04 | +17 | [-0.25, 0.17] | 1.00 | 0.42 | n | n | n (0.00) | n | n |
| NQ | adr | 50% | -0.30 | 0.30 | -0.58 | -0.27 | +43 | [-0.76, 0.25] | 1.00 | 0.42 | n | n | n (0.00) | n | n |
| NQ | fx | 10% | 0.05 | 0.20 | 0.17 | 0.10 | +0 | [-0.01, 0.20] | 1.00 | 0.10 | n | n | n (0.33) | n | Y |
| NQ | fx | 20% | 0.09 | 0.36 | 0.32 | 0.17 | +8 | [-0.04, 0.39] | 1.00 | 0.10 | n | n | n (0.17) | n | Y |
| NQ | fx | 50% | 0.09 | 0.45 | 0.52 | 0.25 | +61 | [-0.29, 0.79] | 1.00 | 0.10 | n | n | n (0.17) | n | Y |

(Shares 30% in `F1_gates.csv`. g4 = standalone Sharpe above the own-null p95 AND bootstrap lower bound > 0 (and shift-null rank >= 0.95 if the worst-decile correlation is < 0). Plateau neighbours: tf 3,4,6,10 and all rule lengths -25% / +25%; the base uplift is negative for every instrument, so no neighbour can retain 75% of it.)

## 3. Per-book standalone (tf5, 1x slippage) - all-in weekly Sharpe

| instr | conv | b1 ema9_21_adx20 | b2 ema9_21 | b3 wma50_200_1m | b5 zlema200 | b6 st14_3 | b7 macd12_26_zero | b9 macd5_35_zero_e200 | b11 macd5_35_zero | clean-selected top-3 (read H1/H2 untouched): H1 / H2 additive uplift at 20% |
|---|---|---|---|---|---|---|---|---|---|---|
| ES | adr | -1.27 | -1.72 | -1.75 | -0.96 | -1.98 | -1.03 | -1.41 | -1.56 | b5, b7, b9: -0.28 / -0.25 |
| ES | fx | -0.73 | -0.59 | -0.73 | -0.18 | -0.42 | -0.08 | -0.54 | -0.65 | b5, b7, b2: 0.25 / -0.10 |
| RTY | adr | -1.65 | -2.18 | -1.35 | -0.40 | -0.84 | -1.29 | -1.65 | -1.87 | b5, b1, b3: -0.63 / -0.12 |
| RTY | fx | -0.91 | -1.30 | -1.27 | -1.36 | -1.11 | -1.00 | -0.84 | -1.01 | b3, b1, b5: -0.49 / -0.24 |
| GC | adr | -1.39 | -1.52 | -0.90 | -1.83 | -1.58 | -1.83 | -2.32 | -2.20 | b3, b2, b6: -0.46 / -0.16 |
| GC | fx | -0.80 | -0.85 | -1.85 | -2.10 | -2.26 | -1.72 | -1.93 | -1.67 | b3, b2, b1: -0.84 / 0.08 |
| CL | adr | -1.86 | -2.24 | -2.82 | -2.58 | -1.93 | -3.04 | -2.88 | -2.75 | b1, b6, b2: -1.28 / -0.01 |
| CL | fx | -1.57 | -1.90 | -2.87 | -2.69 | -2.06 | -1.91 | -2.46 | -2.39 | b1, b7, b6: -0.86 / -0.19 |
| ZN | adr | -6.80 | -6.52 | -6.96 | -7.19 | -6.95 | -6.21 | -6.27 | -6.30 | b3, b7, b9: -2.09 / -1.48 |
| ZN | fx | -8.10 | -7.86 | -7.90 | -9.21 | -8.20 | -7.56 | -7.25 | -7.46 | b3, b9, b11: -1.50 / -1.33 |
| 6E | adr | -1.38 | -1.31 | -1.83 | -2.35 | -2.72 | -2.67 | -1.66 | -1.77 | b2, b3, b1: -0.43 / -0.56 |
| 6E | fx | -2.51 | -2.09 | -1.51 | -1.83 | -2.76 | -2.52 | -1.74 | -1.66 | b5, b3, b11: -0.60 / -0.64 |
| 6J | adr | -2.47 | -2.78 | -2.43 | -4.06 | -2.98 | -2.91 | -2.70 | -2.89 | b1, b2, b3: -1.46 / -0.28 |
| 6J | fx | -3.27 | -3.23 | -2.98 | -3.83 | -3.15 | -3.04 | -3.26 | -3.17 | b6, b7, b3: -1.56 / -0.20 |
| NQ | adr | 0.30 | -0.38 | -0.99 | -0.16 | 0.10 | -0.58 | -0.36 | -0.45 | b1, b7, b6: 0.14 / -0.15 |
| NQ | fx | 0.12 | -0.03 | 0.15 | 0.46 | 1.06 | 0.54 | -0.07 | 0.16 | b6, b7, b11: 0.29 / 0.30 |

Clean-only re-selection (the 3 books with the best clean Sharpe per instrument/convention) does not rescue any instrument: the additive H1/H2 uplifts of the clean-selected top-3 are shown in the last column (clean uplift is in `F1_gates.csv` rows `level=top3`).

## 4. Constant-risk framing (total risk fixed; pair shrinks to fund the sleeve)

| instr | conv | share | verdict | all-in net change % | worst-week improvement % | CVaR5 improvement % |
|---|---|---|---|---|---|---|
| ES | adr | 10% | NO | -21 | +1 | +4 |
| ES | adr | 30% | NO | -63 | -10 | +10 |
| ES | fx | 10% | NO | -14 | +5 | +7 |
| ES | fx | 30% | NO | -41 | -1 | +12 |
| RTY | adr | 10% | NO | -21 | -1 | +4 |
| RTY | adr | 30% | NO | -62 | -12 | +5 |
| RTY | fx | 10% | NO | -18 | +4 | +5 |
| RTY | fx | 30% | NO | -55 | +2 | +8 |
| GC | adr | 10% | NO | -21 | -1 | +2 |
| GC | adr | 30% | NO | -63 | -15 | +1 |
| GC | fx | 10% | NO | -24 | -4 | +1 |
| GC | fx | 30% | NO | -71 | -24 | -0 |
| CL | adr | 10% | NO | -29 | -8 | -1 |
| CL | adr | 30% | NO | -86 | -36 | -12 |
| CL | fx | 10% | NO | -27 | -5 | -2 |
| CL | fx | 30% | NO | -81 | -29 | -14 |
| ZN | adr | 10% | NO | -56 | -13 | -7 |
| ZN | adr | 30% | NO | -168 | -40 | -26 |
| ZN | fx | 10% | NO | -67 | -13 | -9 |
| ZN | fx | 30% | NO | -202 | -46 | -32 |
| 6E | adr | 10% | NO | -24 | -4 | -1 |
| 6E | adr | 30% | NO | -71 | -14 | -5 |
| 6E | fx | 10% | NO | -25 | -2 | -0 |
| 6E | fx | 30% | NO | -75 | -7 | -4 |
| 6J | adr | 10% | NO | -31 | -4 | +2 |
| 6J | adr | 30% | NO | -92 | -13 | +4 |
| 6J | fx | 10% | NO | -34 | -3 | -0 |
| 6J | fx | 30% | NO | -102 | -16 | -5 |
| NQ | adr | 10% | NO | -12 | +2 | +8 |
| NQ | adr | 30% | NO | -37 | +4 | +19 |
| NQ | fx | 10% | NO | -8 | +9 | +9 |
| NQ | fx | 30% | NO | -23 | -4 | +19 |

## 5. Executability and margin

All seven instruments are CME Group futures (CME/CBOT/COMEX/NYMEX/CME FX) and are tradable through NinjaTrader Brokerage via Rithmic (general knowledge, not checked against the brokerage's product list). The strategy would be a new NT8 multi-series strategy per instrument: eight 5-minute (one 1-minute) books with the NQ rules, market entries, stop/target bracket, 18:05-16:40 ET window; DualStrat would not run it as a parameter set. Margins below are ASSUMED typical exchange initial margins (unverified for today; GC uses the 9%-of-notional reading from V5 P4), upper bound = all 8 books open at once at 20% share:

| instr | assumed margin $/contract | contracts per book at 20% share (adr / fx) | upper-bound margin at 20% share (fx) |
|---|---|---|---|
| ES | 24,000 | 54.79 / 34.68 | $6,658,118 |
| RTY | 9,000 | 61.45 / 58.27 | $4,195,328 |
| GC | 37,000 | 46.06 / 30.02 | $8,885,240 |
| CL | 7,000 | 60.16 / 56.00 | $3,135,886 |
| ZN | 3,500 | 189.23 / 223.85 | $6,267,848 |
| 6E | 3,500 | 113.34 / 139.99 | $3,919,711 |
| 6J | 3,500 | 139.21 / 171.24 | $4,794,789 |

## 6. Verdict (FOUND / LEAD per cell family)

**FOUND: none.** Every cell family fails gate 3 (the additive Sharpe uplift is negative on clean for every instrument and convention, and negative on H1/H2 for most) and gate 4's bootstrap condition (lower bound below zero). No cell family is even a LEAD:

| cell family | verdict | failed gates |
|---|---|---|
| ES, RTY, GC, CL, ZN, 6E, 6J ensemble, `adr` bracket, tf3-10, 20% share | NO | 3, 4 (bootstrap), 5 (base uplift negative), standalone loses money |
| same, `fx` constant bracket | NO | same; ES `fx` is the closest (H1 +0.14 at 20% share, clean -0.17, H2 0.00) |
| clean-selected top-3 per instrument | NO | 3 |
| NQ control (fx 60 pt) | reference only (not a new instrument): additive +0.09 / +0.36 / +0.32 at 20% share, worst week +8%, correlation with the pair -0.31 all weeks / +0.10 worst-decile; standalone +0.37; this is the V5 P1 family, already a LEAD there (fails 2x slippage, plateau, pre-2023-08 holdout) | |

Reading: the negative correlation to the pair that made the NQ five-minute family interesting does not transfer. Weekly correlation with the pair is -0.23 to +0.08 on the other instruments, but the books lose money after costs on all of them, so adding them lowers the Sharpe. The mechanism is cost against a small bracket: one side of slippage as a share of the median `adr` bracket is NQ 0.8%, RTY 1.3%, ES 1.6%, 6E 1.7%, 6J 2.1%, GC 2.3%, CL 2.8%, ZN 7.1%. The 13 pre-2023 years (ES 2013-2023) confirm the loss is not regime-specific.

## 7. Limits and runtime

- Delta-confirmed books (#4, #8, #10) not run (no signed delta in ohlcv-1m); the 8 books run are the only ones that can be tested on purchased data.
- 1-minute fills with stop-first on a spanning bar and no queue model; roll handling by difference back-adjustment at instrument-id changes (RTY continuous data starts 2017-06).
- Slippage 0.5 / 1 tick per side by instrument as directed; commission $4.36 per contract round trip is an assumption; margins unverified.
- Engine check on NQ: 77% of entries match the original V5 trade list minute-for-minute (2,717 of 3,523); remaining differences come from bar grouping and one-trade-at-a-time sequencing.
- Runtime: variants 2 min per instrument (6 workers), nulls 4-13 min per instrument (300 draws x 2 conventions, 8 workers under load ~20), scoring ~3 min per instrument; total ~2 h wall including the wait for the 6E/6J purchase. Code `ap_c1_f1_*.py` in `code/census/night_ins/`, data `outputs/autopilot/c1/f1/`.

DONE C1_F1
