# REPORT PY3 - continuous linear VIX-block size tilt: SKEW-selected cell SKEW_P_b0.1 (D08 H5 x M8/M4, NQ pair)
**Verdict: NO. FOUND 0. Selected (clean-only, 12 cells) SKEW_P_b0.1: weekly-Sharpe uplift +0.05 clean / +0.92 H1 / +0.57 H2 (needed +0.10 each), all-in +0.26; flat-mean control -0.22/-0.15/+0.16; uplift minus flat +0.27/+1.07/+0.42; selection-corrected null p95 of best-of-12 clean uplift +0.31 (mean +0.09, chance of a >= +0.10 best cell 40%); bootstrap 90% CI all-in [-0.05, +0.60]; plateau 1/7; 2x slip -0.04/+0.89/+0.23; gates passed 2/10.**

## Pre-registration and disclosure
Registered in PREREG_AUTOPILOT.md block BATCH PY before any run. Data on disk (no purchase): CBOE VIX/VIX3M/VVIX/SKEW daily and VX futures daily (M2/M1 slope, 2018-11+). Related observables were already read: J8 (VIX/term/VVIX switch, carried cell +0.20/-0.11/-0.13), H8-C (VX slope weekly floor), RW2 (VIX block carries K4). Every NQ H1/H2/all-in number here is therefore non-virgin for the VIX family; the maximum status is FOUND-PENDING. H0 (2023-02-10..07-31) is untouched for these observables.
State: z = expanding walk-forward standardisation of the smoothed daily series (min 250 obs), clip +-3, value at the last date strictly before the trade label day (one-day lag). Multiplier clip(1 + s*b*z, 0.5, 1.5) divided by its clean-trade mean, re-clipped [0.5,1.5]. Grid: 2 features x s in {+,-} x b in {0.1,0.2,0.3} = 12 cells. Engine: B11 corrected NT8-faithful engine, clean process, live rules, baseline B.Cfg(wk_floor=8,wk_loss_pb=None) reproduced 1.46/2.83/2.30. Fill: 1 tick/side + $34.88/8-lot RT; 2x slippage = SLIP_PT 1.0 on baseline and candidate. Pair-change framing equals the constant-risk framing at mean multiplier 1 (flat control reported).

## All 12 cells (weekly-Sharpe uplift vs baseline; clean is the only selection-relevant column; H1/H2 of unselected cells shown after selection for transparency)
| cell | clean | H1 | H2 | all | mean mult all/clean | min-max | share touched |
|---|---|---|---|---|---|---|---|
| VVIX_P_b0.1 | -0.20 | -0.74 | +0.33 | -0.16 | 0.996/1.000 | 0.83-1.25 | 0.76 |
| VVIX_P_b0.2 | -0.33 | -0.66 | -0.24 | -0.35 | 0.995/1.000 | 0.68-1.39 | 0.88 |
| VVIX_P_b0.3 | -0.20 | -0.61 | -0.23 | -0.26 | 0.998/1.000 | 0.54-1.35 | 0.92 |
| VVIX_N_b0.1 | -0.11 | +0.04 | -0.23 | -0.10 | 1.004/1.000 | 0.73-1.18 | 0.78 |
| VVIX_N_b0.2 | -0.05 | -0.07 | +0.12 | +0.00 | 1.006/1.000 | 0.54-1.38 | 0.89 |
| VVIX_N_b0.3 | -0.10 | -0.24 | -0.17 | -0.11 | 1.003/1.000 | 0.56-1.50 | 0.93 |
| SKEW_P_b0.1 (SEL) | +0.05 | +0.92 | +0.57 | +0.26 | 0.982/1.000 | 0.79-1.11 | 0.79 |
| SKEW_P_b0.2 | -0.27 | +0.98 | +0.33 | +0.01 | 0.976/1.000 | 0.64-1.13 | 0.87 |
| SKEW_P_b0.3 | -0.03 | -0.19 | +0.05 | -0.02 | 0.992/1.000 | 0.55-1.07 | 0.86 |
| SKEW_N_b0.1 | -0.11 | -0.80 | -0.33 | -0.25 | 1.025/1.000 | 0.85-1.30 | 0.87 |
| SKEW_N_b0.2 | -0.04 | -1.13 | -0.52 | -0.30 | 1.044/1.000 | 0.74-1.50 | 0.94 |
| SKEW_N_b0.3 | -0.18 | +0.05 | -1.01 | -0.37 | 1.009/0.997 | 0.83-1.50 | 0.95 |

## Selected cell vs baseline pair (weekly Sharpe)
| span | pair | cell | uplift | flat-mean control | uplift minus flat | vs B.Cfg() | 2x slip uplift |
|---|---|---|---|---|---|---|---|
| clean | 1.46 | 1.51 | +0.05 | -0.22 | +0.27 | -0.13 | -0.04 |
| H1 | 2.83 | 3.75 | +0.92 | -0.15 | +1.07 | +0.59 | +0.89 |
| H2 | 2.30 | 2.87 | +0.57 | +0.16 | +0.42 | +0.53 | +0.23 |
| all | 1.86 | 2.12 | +0.26 | -0.13 | +0.39 | +0.12 | +0.12 |

## Gate checklist
- [FAIL] g1 uplift >= +0.10 clean/H1/H2
- [PASS] g2 uplift minus flat-mean-multiplier control >= +0.10 clean/H1/H2
- [FAIL] g3 worst week not worse (all-in)
- [FAIL] g4a shuffled-state null p95 (clean and all-in)
- [PASS] g4b random-month-sign null rank >= 0.95 (clean and all-in)
- [FAIL] g4c selection-corrected null: clean uplift >= p95 of best-of-12 replicates
- [FAIL] g5 bootstrap 90% CI of all-in uplift > 0
- [FAIL] g6 plateau >= 75% of 7 neighbours keep >= 75% (>=6 of 7)
- [FAIL] g7 2x slippage uplift >= +0.10 each span
- [FAIL] g8 replication >= 2 of 4 legs (newest weeks n/a; H0; ES/RTY; alt-month) -> 0 of 3 testable
- nulls (rank/p95 of uplift): shuffled-state clean 0.88/+0.10, H1 0.99/+0.67, H2 0.94/+0.58, all 0.99/+0.11; random-month-sign clean 0.96/-0.01, H1 0.93/+1.01, H2 0.97/+0.49, all 1.00/-0.03
- selection-corrected null (60 shuffled-state replicates, full 12-cell grid, clean-only selection): best clean uplift mean +0.09, p95 +0.31; real clean +0.05 rank 0.38
- plateau neighbours (all-in uplift; need >= 0.20): {'b x0.75': 0.11, 'b x1.25': 0.12, 'roll756': -0.04, 'lag+1': 0.09, 'clip .6-1.4': 0.26, 'p 2': 0.18, 'p 4': 0.17}
- bootstrap CI clean [-0.33, +0.40]; weekly corr with pair 0.95; worst-week delta all-in -3385; multiplier min/max/mean 0.79/1.11/0.982

## Replication legs (Amendment 2; need >= 2 of 4, newest live weeks n/a)
- H0 2023-02-10..07-31 (pair rows): base 0.67, cell 0.54, uplift -0.13 -> FAIL
- ES/RTY standalone ST+HM books, same cell and state, all-in uplift ES -0.09, RTY -0.01 (NQ +0.26) -> FAIL (same calendar window as the pair: correlated evidence)
- alternating months odd->even: selected SKEW_N_b0.1 (selection-half -0.04) read -0.44; carried SKEW_P_b0.1: selection-half -0.20, held-out +0.64
- alternating months even->odd: selected SKEW_P_b0.1 (selection-half +0.64) read -0.20; carried SKEW_P_b0.1: selection-half +0.64, held-out -0.20
- alt-month leg: FAIL; legs passed 0 of 3 testable

## ES/RTY leg, all 12 cells (weekly-Sharpe uplift clean/H1/H2/all)
| book | cell | clean | H1 | H2 | all |
|---|---|---|---|---|---|
| ES | VVIX_P_b0.1 | +0.05 | +0.06 | +0.01 | +0.04 |
| ES | VVIX_P_b0.2 | +0.10 | -0.16 | +0.12 | +0.06 |
| ES | VVIX_P_b0.3 | +0.02 | -0.13 | +0.10 | +0.01 |
| ES | VVIX_N_b0.1 | +0.10 | -0.24 | -0.09 | +0.02 |
| ES | VVIX_N_b0.2 | +0.15 | -0.28 | -0.11 | +0.05 |
| ES | VVIX_N_b0.3 | +0.24 | -0.39 | -0.13 | +0.10 |
| ES | SKEW_P_b0.1 | -0.08 | -0.21 | -0.07 | -0.09 |
| ES | SKEW_P_b0.2 | -0.14 | -0.26 | -0.06 | -0.13 |
| ES | SKEW_P_b0.3 | -0.13 | -0.10 | +0.01 | -0.09 |
| ES | SKEW_N_b0.1 | +0.25 | -0.07 | -0.03 | +0.14 |
| ES | SKEW_N_b0.2 | +0.28 | +0.36 | +0.01 | +0.21 |
| ES | SKEW_N_b0.3 | +0.42 | +0.01 | -0.01 | +0.26 |
| RTY | VVIX_P_b0.1 | +0.05 | +0.04 | -0.12 | +0.02 |
| RTY | VVIX_P_b0.2 | +0.07 | +0.09 | -0.12 | +0.04 |
| RTY | VVIX_P_b0.3 | +0.09 | +0.15 | -0.18 | +0.06 |
| RTY | VVIX_N_b0.1 | -0.12 | +0.07 | -0.02 | -0.06 |
| RTY | VVIX_N_b0.2 | -0.12 | -0.12 | +0.14 | -0.07 |
| RTY | VVIX_N_b0.3 | -0.11 | -0.05 | +0.24 | -0.03 |
| RTY | SKEW_P_b0.1 | -0.03 | +0.04 | -0.01 | -0.01 |
| RTY | SKEW_P_b0.2 | -0.06 | +0.06 | +0.03 | -0.01 |
| RTY | SKEW_P_b0.3 | -0.05 | +0.14 | -0.12 | -0.01 |
| RTY | SKEW_N_b0.1 | -0.00 | +0.05 | -0.09 | -0.01 |
| RTY | SKEW_N_b0.2 | +0.09 | +0.20 | -0.24 | +0.03 |
| RTY | SKEW_N_b0.3 | +0.08 | -0.07 | -0.24 | -0.03 |

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| clean cand | 1.51 | 2.87 | 5.11 | -80.3k | -79.0k | 272k | -85.9k | 41.9 |
| H1 cand | 3.75 | 8.39 | 5.50 | -78.2k | -66.1k | 138k | -78.7k | 28.6 |
| H2 cand | 2.87 | 6.12 | 4.08 | -78.2k | -73.4k | 221k | -78.5k | 36.1 |
| all cand | 2.12 | 4.21 | 11.22 | -79.6k | -78.6k | 272k | -85.9k | 38.7 |

Insurance flags (INS?, cost%, CVaR5 impr%, worst-week impr%, maxDD impr%): clean (False, 4.4, -2.0, -4.9, 3.0); H1 (False, 27.5, -0.7, -0.6, 9.3); H2 (False, 18.4, 3.6, 4.9, -1.6); all (False, 13.5, -0.5, -4.1, 3.0)

ERA FLAG: not testable pre-2023 for the pair (rows start 2023-02); no cost decomposition possible.

## Executability
NT8 at NinjaTrader Brokerage via Rithmic: entry-quantity multiplier from a daily file (expanding mean/std constants of the series and the previous close of VIX/VIX3M/VVIX/SKEW or VX M2/M1 refreshed after 16:15 ET, free CBOE data); sizes round to whole contracts; margin unchanged at multipliers <= 1, peak +50% at 1.5. No data purchase.

Files: code/census/night_ins/ap_py1_{feat,core,run,rep,xi,doc}.py; outputs/autopilot/py3/.

DONE PY3
