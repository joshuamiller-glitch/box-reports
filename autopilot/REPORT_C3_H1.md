# REPORT C3-H1 — intraday momentum (first 30 min -> last 30 min), NQ and ES

**Verdict: NO. FOUND 0, no lead.** 8 frozen cells (NQ, ES x r1 definition x r12 agreement), 64 scored rows (8 cells x 4 shares x 2 framings): all NO. RTY **not run**: its 1-minute files for 2013-2016 are still being purchased (10 of 14 yearly files on disk when this ran); RTY would add 4 cells and needs only `python code/census/night_ins/ap_c3_h1_run.py` once the 14 files exist (the script auto-includes it).

## Rule (frozen in PREREG_AUTOPILOT.md, no fitting)
r1 definition A = return from the previous 15:59 ET bar close to the 09:59 bar close; B = 09:30 open to the 09:59 bar close. Trade in the sign of r1; enter at the open of the 15:30 ET bar, exit at the open of the 16:55 ET bar (15:55 CT, per the prereg; note this holds through the 16:00 cash close and the 16:00-16:55 thin session). Variant: take the trade only if sign(r12) (15:00 -> 15:30 open) agrees. 1 contract; costs: NQ 1 tick/side, ES 0.5 tick/side, $4.36 round-trip commission. Bars: purchased Databento 1-minute .v.0, ET DST clock; days where the instrument_id changes between the first and last bar used (rolls) are dropped. Sleeve scaled to the pair's clean weekly volatility for the pair scoring (contracts-equivalent 19-58). Pair = B.Cfg(wk_floor=8, wk_loss_pb=None) computed in a clean process (this script imports b11_nt8 only); robustness vs B.Cfg() stored in scored.csv (`dsh_defcfg`).

## 1. Standalone on the untouched 2013-2022 history (primary test) and the pair window
Null = random days, same count and hold, random direction (1,000 draws), weekly-Sharpe p95.

| cell | n 2013-22 | Sharpe 2013-22 | own-null p95 | 2x slip | Sharpe clean | H1 | H2 | pair-window Sharpe | own-null p95 | wd corr |
|---|---|---|---|---|---|---|---|---|---|---|
| NQ r1=A | 2323 | -0.46 | 0.24 | -0.64 | -0.09 | -0.96 | 1.33 | 0.21 | 0.78 | -0.42 |
| NQ r1=A +r12agree | 1171 | 0.05 | 0.32 | -0.09 | -0.95 | 0.09 | 1.22 | -0.11 | 0.83 | -0.00 |
| NQ r1=B | 2354 | -0.23 | 0.25 | -0.44 | -0.33 | -1.70 | -0.90 | -0.66 | 0.81 | -0.11 |
| NQ r1=B +r12agree | 1186 | 0.20 | 0.31 | 0.05 | -1.02 | -0.29 | -0.55 | -0.76 | 0.77 | 0.21 |
| ES r1=A | 2354 | -0.67 | -0.01 | -1.02 | -0.08 | -1.74 | 0.42 | -0.18 | 0.59 | -0.27 |
| ES r1=A +r12agree | 1153 | -0.11 | 0.21 | -0.36 | -0.69 | -0.11 | 0.30 | -0.38 | 0.73 | 0.03 |
| ES r1=B | 2385 | -0.63 | 0.05 | -0.95 | -1.06 | -2.04 | -0.12 | -1.05 | 0.58 | 0.11 |
| ES r1=B +r12agree | 1154 | -0.20 | 0.17 | -0.45 | -1.29 | -0.64 | -0.17 | -0.95 | 0.74 | 0.35 |

Reading: on the 10-year untouched history **6 of 8 cells have a negative Sharpe, and none beats its own null p95** (best: NQ r1=B +r12 agree, 0.20 against p95 0.31). In the pair window (2023-08..2026-10) every cell is below or inside its null p95 (0.58-0.83); the positive pair-window figures for NQ r1=A are inside the null. Per-year Sharpe 2013-2022 (below) shows no calendar-year consistency; NQ r1=B +agree is positive in 5 of 10 years.

| cell | 2013 | 2014 | 2015 | 2016 | 2017 | 2018 | 2019 | 2020 | 2021 | 2022 |
|---|---|---|---|---|---|---|---|---|---|---|
| NQ r1=A | -1.93 | -0.13 | -0.58 | -1.49 | -0.39 | 0.34 | -0.87 | 0.61 | -0.89 | -1.81 |
| NQ r1=A +r12agree | -2.43 | -0.62 | 0.73 | -1.44 | 0.47 | 1.22 | -1.76 | 0.72 | -0.24 | -0.14 |
| NQ r1=B | -1.30 | -1.73 | -1.18 | -1.26 | -0.96 | -1.06 | -0.18 | 0.55 | -1.21 | 0.14 |
| NQ r1=B +r12agree | -1.20 | -1.61 | 0.13 | -1.25 | -0.11 | 0.22 | -1.32 | 0.60 | -0.06 | 1.20 |
| ES r1=A | 0.24 | -0.90 | -1.24 | -2.49 | -2.85 | -1.26 | 0.05 | 0.24 | -1.01 | -1.49 |
| ES r1=A +r12agree | -0.34 | -1.41 | 0.23 | -2.55 | -1.67 | -0.05 | -0.47 | 0.51 | -0.42 | 0.36 |
| ES r1=B | -0.12 | -3.83 | -1.98 | -1.25 | -0.88 | -1.26 | 0.53 | -0.00 | -0.96 | -1.31 |
| ES r1=B +r12agree | -0.47 | -2.96 | -0.39 | -1.71 | -0.32 | -0.19 | -0.20 | 0.15 | -0.17 | 0.22 |

## 2. As a sleeve against the live pair (additive, 20% share; other shares in scored.csv)
| cell | clean dSharpe | H1 | H2 | all-in | shift-null p95 | boot lo | worst-week chg % | verdict |
|---|---|---|---|---|---|---|---|---|
| NQ r1=A | -0.08 | -0.18 | 0.14 | -0.05 | 0.05 | -0.22 | 15 | NO |
| NQ r1=A +r12agree | -0.23 | -0.13 | 0.12 | -0.12 | -0.03 | -0.32 | 28 | NO |
| NQ r1=B | -0.08 | -0.36 | -0.52 | -0.22 | -0.16 | -0.44 | 24 | NO |
| NQ r1=B +r12agree | -0.21 | -0.20 | -0.32 | -0.22 | -0.17 | -0.43 | 23 | NO |
| ES r1=A | -0.06 | -0.32 | -0.01 | -0.09 | -0.03 | -0.26 | 16 | NO |
| ES r1=A +r12agree | -0.14 | -0.14 | -0.02 | -0.10 | -0.07 | -0.29 | 27 | NO |
| ES r1=B | -0.22 | -0.69 | -0.20 | -0.27 | -0.21 | -0.44 | 23 | NO |
| ES r1=B +r12agree | -0.24 | -0.31 | -0.17 | -0.22 | -0.18 | -0.39 | 30 | NO |

Every cell **lowers** the pair's Sharpe on clean and H1; gate 3 (+0.10 on each of clean/H1/H2) fails for all 64 rows; every bootstrap lower bound is negative; the shift-null p95 is reported (the amended gate uses the standalone own-null above, which also fails). Worst-decile correlation with the pair: -0.42 to +0.35 on 17 weeks (not informative). All-in weekly correlation with the pair: -0.01 to +0.14.

## 3. Sensitivities (non-gating, listed so nothing is hidden)
Exit at 16:00 ET instead of 16:55, and the |r1| > 0.25 / 0.5 x ADR20 thresholds (my reading of the prereg's "0.5*ADR-pct": 20-day mean RTH range, points), 2013-2022 / pair window weekly Sharpe:
NQ A+agree exit 16:00: 0.23 / -0.42; NQ B+agree exit 16:00: 0.23 / -0.81; thresholds give 2013-22 Sharpe from -0.65 to +0.18 (ES r1=B +agree thr 0.25: 0.18 / 0.02; thr 0.5 small-sample or NaN). No variant is positive in both the 2013-2022 history and the pair window. 2x slippage lowers 2013-22 Sharpe by 0.1-0.4 in every cell. Plateau gate: not met (no cell passes any other gate, so the plateau count is moot; neighbours in sens.csv).

## 4. Implementation / margin / caveats
Executable at NinjaTrader Brokerage via Rithmic as a separate NQ/ES strategy (arm 15:30 ET, exit 16:55 ET); margin not computed (nothing passes): at the pair-volatility scale it would need 19-58 contracts, an assumed $22k/NQ and $15k/ES margin each, i.e. far larger than the account budget. Small-sample flag: none (n 1,150-2,400 trades in 2013-2022; 450-600 in the pair window). Look-ahead: signals use closes up to 09:59 and opens at 15:00/15:30, entry at the 15:30 open (no lookahead). Weakness: bars for 2013-2016 NQ carry the 2014-06 degraded-quality days Databento flags; roll days dropped. The effect in the literature is for the last 30 minutes to 16:00; holding to 16:55 adds an hour of unrelated noise, hence the exit-16:00 sensitivity (also negative in the pair window).
Runtime: 88 s of compute (1 worker; ~3 min including loading). Files: outputs/autopilot/c3/h1/{cells,scored,sens}.csv, h1.pkl; code code/census/night_ins/ap_c3_h1_core.py, ap_c3_h1_run.py.

## RTY cells (added in cycle 6, C6-N2; 2017-2026 bars only, 2013-2016 unavailable)
| cell | trades 2017-22 | Sharpe 2017-22 | own-null p95 | Sharpe pair window | null p95 | clean / H1 / H2 | 2x slip 2017-22 |
|---|---|---|---|---|---|---|---|
| RTY r1=A | 1257 | -1.18 | 0.13 | -0.60 | 0.18 | -0.39 / -1.92 / -0.32 | -1.57 |
| RTY r1=A +r12agree | 642 | -0.69 | 0.29 | -1.02 | 0.44 | -1.01 / -1.69 / -0.58 | -0.99 |
| RTY r1=B | 1274 | -1.01 | 0.09 | -0.13 | 0.21 | 0.16 / -2.59 / 0.86 | -1.47 |
| RTY r1=B +r12agree | 654 | -0.52 | 0.35 | -0.78 | 0.51 | -0.65 / -2.93 / 0.13 | -0.85 |

Per-year Sharpe 2017-2022:

| cell | 2017 | 2018 | 2019 | 2020 | 2021 | 2022 |
|---|---|---|---|---|---|---|
| RTY r1=A | -1.59 | -0.90 | -1.19 | -0.19 | -1.51 | -3.04 |
| RTY r1=A +r12agree | -2.19 | -0.13 | -1.41 | -0.56 | -0.73 | -0.76 |
| RTY r1=B | -1.10 | -2.41 | -0.61 | 0.69 | -1.64 | -1.94 |
| RTY r1=B +r12agree | -2.30 | -1.14 | -0.98 | -0.27 | -0.47 | -0.01 |

Verdict: NO. All 4 RTY cells have negative standalone Sharpe on 2017-2022 and in the pair window, none beats its own random-day null p95, and every additive row lowers the pair's Sharpe on clean, H1 and H2 (details: `REPORT_C6_N2.md`, `c6/n2/h1/`).

DONE C3_H1
