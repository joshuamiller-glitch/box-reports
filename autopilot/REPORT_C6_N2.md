# REPORT C6-N2 — RTY out-of-sample checks (autopilot cycle 6)

**Verdict: NO on both parts. 0 FOUND, no lead retained.** (a) The RTY bar-feature ML cell that looked best in C1-F7 loses money out of sample over 2017-2022. (b) The C3-H1 intraday-momentum RTY cells lose on 2017-2022 and in the pair window.

**Data limit:** RTY.v.0 1-minute bars exist only from 2017 (the 2013-2016 purchase requests were rejected: symbology_invalid_request). All "long history" statements here mean 2017-2022, not 2013-2022. The purchase therefore leaves 4 fewer untouched years for RTY than for NQ/ES.

## (a) RTY ML cell, frozen recipe, walk-forward 6/1 on 2017-2022
Recipe unchanged from C1-F7 / T3 S5 (22 bar-only features, 1-minute equivalents of the three 1-second features, LightGBM fixed hyper-parameters, 5-minute decision grid, ET 18:05-15:30 with 09:00-09:58 blocked, H=240 min time exit, tau 0.55, one position at a time, RTY $50/pt, 1 tick/side + $4.36 commission). Code `ap_c6_n2_*.py` is a string-substitution copy of the C1-F7 modules (bars 2017-01-03..2022-12-30, test months 2017-07..2022-12 = 66 months, train = previous 6 months). Surrogates: 30 timing-destroyed runs per cell (label sequences shifted by random whole days, same walk-forward), selection-corrected test not needed (two pre-named cells, no selection on this span).

| cell | trades | net/contract 2017-07..2022-12 | weekly Sharpe | surrogate p95 | surrogate median | rank | Sharpe 2017 | Sharpe 2018 | Sharpe 2019 | Sharpe 2020 | Sharpe 2021 | Sharpe 2022 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| H240 / 8 leaves / tau 0.55 | 7,527 | $-25,298 ($-4,600/yr) | -0.25 | -0.20 | -0.95 | 93% | -3.48 | -1.09 | -0.97 | 0.93 | -0.89 | 0.50 |
| H240 / 16 leaves / tau 0.55 | 7,987 | $-4,283 ($-779/yr) | -0.04 | 0.02 | -0.87 | 93% | -4.53 | -0.65 | -0.63 | 1.58 | -0.65 | 0.23 |

- The only question was Sharpe > 0 AND above the surrogate p95 out of sample. **Both fail:** Sharpe is -0.25 (8 leaves) and -0.04 (16 leaves). Net per contract over 5.5 years is -$25.3k and -$4.3k.
- They rank 93% of the surrogate runs only because the timing-destroyed model loses to cost (surrogate median Sharpe -0.95/-0.87); a negative Sharpe above a worse null is not an edge. Net rank is also 93%, with net below zero.
- Year pattern: positive in 2020 and 2022, negative or flat in 2017, 2018, 2019, 2021. The C1-F7 pair-window result (H2 Sharpe 1.75) is not reproduced in the earlier six years.
- Not scored as a sleeve: it fails the standalone gate, so the C1-F7 sleeve rows (0 of 72 pass) stand unchanged.

## (b) C3-H1 RTY cells (rerun, 2017-2026 bars)
`ap_c6_n2_h1.py` = `ap_c3_h1_run.py` restricted to RTY with the long-history window set to 2017-01..2022-12 (2013-2016 unavailable). Frozen 4 cells (r1 definition A/B, with and without r12 agreement); entry 15:30 ET, exit 16:55 ET open.

| cell | trades 2017-22 | Sharpe 2017-22 | own-null p95 | Sharpe pair window | null p95 | clean / H1 / H2 | 2x slip 2017-22 |
|---|---|---|---|---|---|---|---|
| RTY r1=A | 1257 | -1.18 | 0.13 | -0.60 | 0.18 | -0.39 / -1.92 / -0.32 | -1.57 |
| RTY r1=A +r12agree | 642 | -0.69 | 0.29 | -1.02 | 0.44 | -1.01 / -1.69 / -0.58 | -0.99 |
| RTY r1=B | 1274 | -1.01 | 0.09 | -0.13 | 0.21 | 0.16 / -2.59 / 0.86 | -1.47 |
| RTY r1=B +r12agree | 654 | -0.52 | 0.35 | -0.78 | 0.51 | -0.65 / -2.93 / 0.13 | -0.85 |

Per-year Sharpe (2017-2022):

| cell | 2017 | 2018 | 2019 | 2020 | 2021 | 2022 |
|---|---|---|---|---|---|---|
| RTY r1=A | -1.59 | -0.90 | -1.19 | -0.19 | -1.51 | -3.04 |
| RTY r1=A +r12agree | -2.19 | -0.13 | -1.41 | -0.56 | -0.73 | -0.76 |
| RTY r1=B | -1.10 | -2.41 | -0.61 | 0.69 | -1.64 | -1.94 |
| RTY r1=B +r12agree | -2.30 | -1.14 | -0.98 | -0.27 | -0.47 | -0.01 |

Additive sleeve rows (20% share etc. in `outputs/autopilot/c6/n2/h1/scored.csv`; 10% and 50% shown):

| cell | share | clean dSharpe | H1 dSharpe | H2 dSharpe | bootstrap 90% | verdict |
|---|---|---|---|---|---|---|
| RTY r1=A | 10% | -0.06 | -0.23 | -0.04 | [-0.16, +0.00] | NO |
| RTY r1=A | 50% | -0.36 | -1.23 | -0.36 | [-0.87, -0.12] | NO |
| RTY r1=A +r12agree | 10% | -0.10 | -0.24 | -0.07 | [-0.21, -0.02] | NO |
| RTY r1=A +r12agree | 50% | -0.59 | -1.25 | -0.52 | [-1.11, -0.23] | NO |
| RTY r1=B | 10% | -0.00 | -0.36 | +0.01 | [-0.15, +0.05] | NO |
| RTY r1=B | 50% | -0.13 | -1.85 | -0.14 | [-0.81, +0.07] | NO |
| RTY r1=B +r12agree | 10% | -0.07 | -0.29 | -0.03 | [-0.18, -0.00] | NO |
| RTY r1=B +r12agree | 50% | -0.43 | -1.47 | -0.30 | [-0.97, -0.13] | NO |

All 4 RTY cells have negative standalone Sharpe on 2017-2022 (-0.52 to -1.18) against own-null p95 of 0.09-0.35, negative in the pair window, positive in at most one of six years, and lower the pair's Sharpe on clean, H1 and H2. NO.

## Caveats
- RTY 1-minute bars only from 2017; no 2013-2016 history.
- Commission $4.36 per contract is an assumption; sizing and margin not assessed because nothing passes.
- 1-minute engine, stop-first conventions as in the earlier families; no netting against the pair.
- 30 surrogate runs per cell (>= 20 required).

Runtime: bars+features about 10 s; walk-forward 442 s on 5 workers (62 model sets); H1 rerun 36 s; evaluation about 1 min.

DONE C6_N2
