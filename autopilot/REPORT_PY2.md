# REPORT PY2 - continuous linear VIX-block size tilt: VXS-selected cell VXS_P_b0.2 (D08 H5 x M8/M4, NQ pair)
**Verdict: NO. FOUND 0. Selected (clean-only, 12 cells) VXS_P_b0.2: weekly-Sharpe uplift -0.03 clean / -1.04 H1 / -0.46 H2 (needed +0.10 each), all-in -0.26; flat-mean control -0.03/-0.53/-0.32; uplift minus flat +0.00/-0.51/-0.15; selection-corrected null p95 of best-of-12 clean uplift +0.38 (mean +0.12, chance of a >= +0.10 best cell 50%); bootstrap 90% CI all-in [-0.79, +0.26]; plateau 0/7; 2x slip +0.09/-0.99/-0.79; gates passed 1/10.**

## Pre-registration and disclosure
Registered in PREREG_AUTOPILOT.md block BATCH PY before any run. Data on disk (no purchase): CBOE VIX/VIX3M/VVIX/SKEW daily and VX futures daily (M2/M1 slope, 2018-11+). Related observables were already read: J8 (VIX/term/VVIX switch, carried cell +0.20/-0.11/-0.13), H8-C (VX slope weekly floor), RW2 (VIX block carries K4). Every NQ H1/H2/all-in number here is therefore non-virgin for the VIX family; the maximum status is FOUND-PENDING. H0 (2023-02-10..07-31) is untouched for these observables.
State: z = expanding walk-forward standardisation of the smoothed daily series (min 250 obs), clip +-3, value at the last date strictly before the trade label day (one-day lag). Multiplier clip(1 + s*b*z, 0.5, 1.5) divided by its clean-trade mean, re-clipped [0.5,1.5]. Grid: 2 features x s in {+,-} x b in {0.1,0.2,0.3} = 12 cells. Engine: B11 corrected NT8-faithful engine, clean process, live rules, baseline B.Cfg(wk_floor=8,wk_loss_pb=None) reproduced 1.46/2.83/2.30. Fill: 1 tick/side + $34.88/8-lot RT; 2x slippage = SLIP_PT 1.0 on baseline and candidate. Pair-change framing equals the constant-risk framing at mean multiplier 1 (flat control reported).

## All 12 cells (weekly-Sharpe uplift vs baseline; clean is the only selection-relevant column; H1/H2 of unselected cells shown after selection for transparency)
| cell | clean | H1 | H2 | all | mean mult all/clean | min-max | share touched |
|---|---|---|---|---|---|---|---|
| IDX_P_b0.1 | -0.07 | -0.06 | -0.01 | -0.02 | 1.035/1.000 | 0.73-1.24 | 0.89 |
| IDX_P_b0.2 | -0.18 | -0.30 | -1.08 | -0.39 | 1.070/1.000 | 0.54-1.50 | 0.94 |
| IDX_P_b0.3 | -0.19 | -1.13 | -1.07 | -0.53 | 1.094/1.000 | 0.56-1.50 | 0.96 |
| IDX_N_b0.1 | -0.37 | +1.14 | +0.07 | -0.09 | 0.968/1.000 | 0.78-1.25 | 0.88 |
| IDX_N_b0.2 | -0.42 | +0.59 | -0.73 | -0.39 | 0.941/1.000 | 0.57-1.39 | 0.93 |
| IDX_N_b0.3 | -0.46 | +0.31 | -0.52 | -0.40 | 0.921/1.000 | 0.50-1.36 | 0.95 |
| VXS_P_b0.1 | -0.21 | -0.76 | +0.04 | -0.19 | 1.029/1.000 | 0.73-1.25 | 0.83 |
| VXS_P_b0.2 (SEL) | -0.03 | -1.04 | -0.46 | -0.26 | 1.059/1.000 | 0.54-1.50 | 0.92 |
| VXS_P_b0.3 | -0.06 | -0.56 | -0.71 | -0.26 | 1.078/0.997 | 0.55-1.50 | 0.94 |
| VXS_N_b0.1 | -0.32 | +0.74 | -0.08 | -0.16 | 0.973/1.000 | 0.77-1.25 | 0.82 |
| VXS_N_b0.2 | -0.55 | +1.00 | +0.07 | -0.25 | 0.948/1.000 | 0.56-1.40 | 0.90 |
| VXS_N_b0.3 | -0.35 | +0.56 | -1.04 | -0.42 | 0.932/1.000 | 0.50-1.38 | 0.92 |

## Selected cell vs baseline pair (weekly Sharpe)
| span | pair | cell | uplift | flat-mean control | uplift minus flat | vs B.Cfg() | 2x slip uplift |
|---|---|---|---|---|---|---|---|
| clean | 1.46 | 1.43 | -0.03 | -0.03 | +0.00 | -0.01 | +0.09 |
| H1 | 2.83 | 1.79 | -1.04 | -0.53 | -0.51 | +0.03 | -0.99 |
| H2 | 2.30 | 1.83 | -0.46 | -0.32 | -0.15 | +0.14 | -0.79 |
| all | 1.86 | 1.60 | -0.26 | -0.15 | -0.11 | +0.05 | -0.25 |

## Gate checklist
- [FAIL] g1 uplift >= +0.10 clean/H1/H2
- [FAIL] g2 uplift minus flat-mean-multiplier control >= +0.10 clean/H1/H2
- [PASS] g3 worst week not worse (all-in)
- [FAIL] g4a shuffled-state null p95 (clean and all-in)
- [FAIL] g4b random-month-sign null rank >= 0.95 (clean and all-in)
- [FAIL] g4c selection-corrected null: clean uplift >= p95 of best-of-12 replicates
- [FAIL] g5 bootstrap 90% CI of all-in uplift > 0
- [FAIL] g6 plateau >= 75% of 7 neighbours keep >= 75% (>=6 of 7)
- [FAIL] g7 2x slippage uplift >= +0.10 each span
- [FAIL] g8 replication >= 2 of 4 legs (newest weeks n/a; H0; ES/RTY; alt-month) -> 0 of 3 testable
- nulls (rank/p95 of uplift): shuffled-state clean 0.84/+0.12, H1 0.09/+0.86, H2 0.42/+0.43, all 0.55/+0.06; random-month-sign clean 0.74/+0.17, H1 0.23/+0.89, H2 0.30/+0.45, all 0.34/+0.13
- selection-corrected null (60 shuffled-state replicates, full 12-cell grid, clean-only selection): best clean uplift mean +0.12, p95 +0.38; real clean -0.03 rank 0.18
- plateau neighbours (all-in uplift; need >= -0.19): {'b x0.75': -0.11, 'b x1.25': -0.29, 'roll756': -0.4, 'lag+1': -0.29, 'clip .6-1.4': -0.24, 'p 2': -0.31, 'p 4': -0.35}
- bootstrap CI clean [-0.52, +0.46]; weekly corr with pair 0.84; worst-week delta all-in +894; multiplier min/max/mean 0.54/1.50/1.059

## Replication legs (Amendment 2; need >= 2 of 4, newest live weeks n/a)
- H0 2023-02-10..07-31 (pair rows): base 0.67, cell 1.58, uplift +0.91 -> FAIL
- ES/RTY standalone ST+HM books, same cell and state, all-in uplift ES -0.05, RTY -0.03 (NQ -0.26) -> FAIL (same calendar window as the pair: correlated evidence)
- alternating months odd->even: selected IDX_P_b0.1 (selection-half -0.16) read +0.05; carried VXS_P_b0.2: selection-half -0.55, held-out -0.03
- alternating months even->odd: selected IDX_N_b0.1 (selection-half +0.09) read -0.32; carried VXS_P_b0.2: selection-half -0.03, held-out -0.55
- alt-month leg: FAIL; legs passed 0 of 3 testable

## ES/RTY leg, all 12 cells (weekly-Sharpe uplift clean/H1/H2/all)
| book | cell | clean | H1 | H2 | all |
|---|---|---|---|---|---|
| ES | IDX_P_b0.1 | +0.00 | -0.08 | -0.14 | -0.04 |
| ES | IDX_P_b0.2 | +0.04 | -0.16 | -0.15 | -0.03 |
| ES | IDX_P_b0.3 | +0.07 | -0.12 | -0.66 | -0.11 |
| ES | IDX_N_b0.1 | +0.01 | +0.01 | +0.02 | +0.01 |
| ES | IDX_N_b0.2 | +0.09 | -0.25 | +0.14 | +0.06 |
| ES | IDX_N_b0.3 | +0.07 | -0.21 | +0.22 | +0.07 |
| ES | VXS_P_b0.1 | +0.00 | -0.14 | -0.12 | -0.04 |
| ES | VXS_P_b0.2 | +0.01 | -0.20 | -0.13 | -0.05 |
| ES | VXS_P_b0.3 | +0.02 | -0.09 | -0.67 | -0.13 |
| ES | VXS_N_b0.1 | -0.05 | +0.06 | +0.00 | -0.03 |
| ES | VXS_N_b0.2 | +0.04 | +0.12 | +0.05 | +0.04 |
| ES | VXS_N_b0.3 | +0.01 | +0.31 | +0.01 | +0.04 |
| RTY | IDX_P_b0.1 | -0.11 | +0.30 | -0.10 | -0.04 |
| RTY | IDX_P_b0.2 | -0.12 | +0.00 | -0.04 | -0.09 |
| RTY | IDX_P_b0.3 | -0.22 | -0.03 | +0.07 | -0.13 |
| RTY | IDX_N_b0.1 | +0.09 | -0.04 | -0.08 | +0.04 |
| RTY | IDX_N_b0.2 | +0.14 | +0.10 | -0.19 | +0.08 |
| RTY | IDX_N_b0.3 | +0.12 | +0.43 | -0.25 | +0.11 |
| RTY | VXS_P_b0.1 | -0.10 | +0.11 | -0.04 | -0.05 |
| RTY | VXS_P_b0.2 | -0.09 | +0.17 | -0.03 | -0.03 |
| RTY | VXS_P_b0.3 | -0.05 | +0.29 | +0.06 | +0.04 |
| RTY | VXS_N_b0.1 | +0.04 | -0.11 | -0.04 | -0.00 |
| RTY | VXS_N_b0.2 | +0.01 | -0.18 | -0.20 | -0.06 |
| RTY | VXS_N_b0.3 | -0.01 | -0.27 | -0.24 | -0.09 |

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| clean cand | 1.43 | 2.70 | 4.41 | -79.3k | -78.5k | 289k | -81.6k | 41.0 |
| H1 cand | 1.79 | 3.22 | 3.03 | -78.8k | -78.4k | 143k | -79.8k | 32.1 |
| H2 cand | 1.83 | 4.23 | 2.88 | -78.4k | -77.9k | 253k | -78.8k | 47.2 |
| all cand | 1.60 | 3.14 | 8.44 | -79.2k | -78.4k | 289k | -81.6k | 41.1 |

Insurance flags (INS?, cost%, CVaR5 impr%, worst-week impr%, maxDD impr%): clean (False, -4.2, -0.7, 0.3, -3.1); H1 (False, -26.9, -1.5, -1.9, 5.6); H2 (False, -4.3, 3.3, 4.5, -16.4); all (False, -9.2, 0.1, 1.1, -3.1)

ERA FLAG: not testable pre-2023 for the pair (rows start 2023-02); no cost decomposition possible.

## Executability
NT8 at NinjaTrader Brokerage via Rithmic: entry-quantity multiplier from a daily file (expanding mean/std constants of the series and the previous close of VIX/VIX3M/VVIX/SKEW or VX M2/M1 refreshed after 16:15 ET, free CBOE data); sizes round to whole contracts; margin unchanged at multipliers <= 1, peak +50% at 1.5. No data purchase.

Files: code/census/night_ins/ap_py1_{feat,core,run,rep,xi,doc}.py; outputs/autopilot/py2/.

DONE PY2
