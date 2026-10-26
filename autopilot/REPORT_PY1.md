# REPORT PY1 - continuous linear VIX-block size tilt: CHG-selected cell CHG_N_b0.3 (D08 H5 x M8/M4, NQ pair)
**Verdict: NO. FOUND 0. Selected (clean-only, 12 cells) CHG_N_b0.3: weekly-Sharpe uplift -0.06 clean / -0.47 H1 / -0.98 H2 (needed +0.10 each), all-in -0.32; flat-mean control -0.17/+0.07/+0.08; uplift minus flat +0.12/-0.53/-1.06; selection-corrected null p95 of best-of-12 clean uplift +0.24 (mean +0.09, chance of a >= +0.10 best cell 40%); bootstrap 90% CI all-in [-0.92, +0.30]; plateau 0/7; 2x slip +0.07/-0.44/-1.28; gates passed 1/10.**

## Pre-registration and disclosure
Registered in PREREG_AUTOPILOT.md block BATCH PY before any run. Data on disk (no purchase): CBOE VIX/VIX3M/VVIX/SKEW daily and VX futures daily (M2/M1 slope, 2018-11+). Related observables were already read: J8 (VIX/term/VVIX switch, carried cell +0.20/-0.11/-0.13), H8-C (VX slope weekly floor), RW2 (VIX block carries K4). Every NQ H1/H2/all-in number here is therefore non-virgin for the VIX family; the maximum status is FOUND-PENDING. H0 (2023-02-10..07-31) is untouched for these observables.
State: z = expanding walk-forward standardisation of the smoothed daily series (min 250 obs), clip +-3, value at the last date strictly before the trade label day (one-day lag). Multiplier clip(1 + s*b*z, 0.5, 1.5) divided by its clean-trade mean, re-clipped [0.5,1.5]. Grid: 2 features x s in {+,-} x b in {0.1,0.2,0.3} = 12 cells. Engine: B11 corrected NT8-faithful engine, clean process, live rules, baseline B.Cfg(wk_floor=8,wk_loss_pb=None) reproduced 1.46/2.83/2.30. Fill: 1 tick/side + $34.88/8-lot RT; 2x slippage = SLIP_PT 1.0 on baseline and candidate. Pair-change framing equals the constant-risk framing at mean multiplier 1 (flat control reported).

## All 12 cells (weekly-Sharpe uplift vs baseline; clean is the only selection-relevant column; H1/H2 of unselected cells shown after selection for transparency)
| cell | clean | H1 | H2 | all | mean mult all/clean | min-max | share touched |
|---|---|---|---|---|---|---|---|
| LVL_P_b0.1 | -0.27 | -0.09 | +0.11 | -0.17 | 1.000/1.000 | 0.89-1.27 | 0.69 |
| LVL_P_b0.2 | -0.20 | -0.58 | +0.23 | -0.16 | 1.000/1.000 | 0.79-1.50 | 0.85 |
| LVL_P_b0.3 | -0.33 | -0.46 | -0.12 | -0.30 | 1.004/1.000 | 0.68-1.50 | 0.89 |
| LVL_N_b0.1 | -0.16 | -0.16 | -0.08 | -0.12 | 1.000/1.000 | 0.73-1.11 | 0.69 |
| LVL_N_b0.2 | -0.14 | -0.13 | -0.43 | -0.18 | 1.000/1.000 | 0.50-1.21 | 0.85 |
| LVL_N_b0.3 | -0.10 | -0.06 | -0.09 | -0.06 | 0.996/1.000 | 0.50-1.31 | 0.89 |
| CHG_P_b0.1 | -0.16 | -0.65 | +0.07 | -0.18 | 0.996/1.000 | 0.69-1.27 | 0.81 |
| CHG_P_b0.2 | -0.19 | -0.86 | -0.02 | -0.24 | 0.993/1.000 | 0.50-1.44 | 0.90 |
| CHG_P_b0.3 | -0.11 | -0.62 | -0.23 | -0.19 | 0.993/1.001 | 0.50-1.43 | 0.93 |
| CHG_N_b0.1 | -0.11 | -0.22 | -0.03 | -0.10 | 1.005/1.000 | 0.71-1.33 | 0.82 |
| CHG_N_b0.2 | -0.10 | -0.56 | -0.26 | -0.18 | 1.007/0.998 | 0.52-1.50 | 0.91 |
| CHG_N_b0.3 (SEL) | -0.06 | -0.47 | -0.98 | -0.32 | 1.006/0.995 | 0.53-1.50 | 0.94 |

## Selected cell vs baseline pair (weekly Sharpe)
| span | pair | cell | uplift | flat-mean control | uplift minus flat | vs B.Cfg() | 2x slip uplift |
|---|---|---|---|---|---|---|---|
| clean | 1.46 | 1.40 | -0.06 | -0.17 | +0.12 | +0.13 | +0.07 |
| H1 | 2.83 | 2.36 | -0.47 | +0.07 | -0.53 | +1.05 | -0.44 |
| H2 | 2.30 | 1.31 | -0.98 | +0.08 | -1.06 | -1.38 | -1.28 |
| all | 1.86 | 1.53 | -0.32 | -0.09 | -0.23 | -0.10 | -0.31 |

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
- nulls (rank/p95 of uplift): shuffled-state clean 0.81/+0.19, H1 0.33/+1.09, H2 0.23/+0.63, all 0.41/+0.11; random-month-sign clean 0.69/+0.21, H1 0.61/+0.42, H2 0.14/+0.23, all 0.41/-0.00
- selection-corrected null (60 shuffled-state replicates, full 12-cell grid, clean-only selection): best clean uplift mean +0.09, p95 +0.24; real clean -0.06 rank 0.05
- plateau neighbours (all-in uplift; need >= -0.24): {'b x0.75': -0.31, 'b x1.25': -0.27, 'roll756': -0.21, 'lag+1': -0.24, 'clip .6-1.4': -0.35, 'p 4': -0.61, 'p 6': -0.23}
- bootstrap CI clean [-0.77, +0.67]; weekly corr with pair 0.80; worst-week delta all-in +726; multiplier min/max/mean 0.53/1.50/1.006

## Replication legs (Amendment 2; need >= 2 of 4, newest live weeks n/a)
- H0 2023-02-10..07-31 (pair rows): base 0.67, cell 1.01, uplift +0.34 -> FAIL
- ES/RTY standalone ST+HM books, same cell and state, all-in uplift ES +0.10, RTY +0.03 (NQ -0.32) -> FAIL (same calendar window as the pair: correlated evidence)
- alternating months odd->even: selected LVL_N_b0.3 (selection-half -0.01) read -0.20; carried CHG_N_b0.3: selection-half -0.12, held-out -0.47
- alternating months even->odd: selected CHG_P_b0.2 (selection-half +0.17) read -0.67; carried CHG_N_b0.3: selection-half -0.47, held-out -0.12
- alt-month leg: FAIL; legs passed 0 of 3 testable

## ES/RTY leg, all 12 cells (weekly-Sharpe uplift clean/H1/H2/all)
| book | cell | clean | H1 | H2 | all |
|---|---|---|---|---|---|
| ES | LVL_P_b0.1 | +0.04 | +0.08 | +0.01 | +0.04 |
| ES | LVL_P_b0.2 | +0.04 | -0.08 | +0.09 | +0.03 |
| ES | LVL_P_b0.3 | +0.09 | -0.06 | +0.11 | +0.06 |
| ES | LVL_N_b0.1 | +0.01 | -0.29 | -0.09 | -0.04 |
| ES | LVL_N_b0.2 | +0.05 | -0.17 | -0.12 | -0.01 |
| ES | LVL_N_b0.3 | +0.07 | -0.23 | -0.15 | +0.00 |
| ES | CHG_P_b0.1 | -0.00 | -0.25 | -0.19 | -0.07 |
| ES | CHG_P_b0.2 | +0.05 | -0.35 | -0.42 | -0.09 |
| ES | CHG_P_b0.3 | -0.07 | -0.42 | -0.51 | -0.20 |
| ES | CHG_N_b0.1 | -0.04 | -0.16 | +0.12 | -0.02 |
| ES | CHG_N_b0.2 | +0.00 | -0.13 | +0.39 | +0.07 |
| ES | CHG_N_b0.3 | -0.02 | -0.19 | +0.64 | +0.10 |
| RTY | LVL_P_b0.1 | +0.05 | -0.04 | -0.02 | +0.02 |
| RTY | LVL_P_b0.2 | +0.06 | +0.05 | -0.12 | +0.02 |
| RTY | LVL_P_b0.3 | +0.08 | +0.09 | -0.05 | +0.05 |
| RTY | LVL_N_b0.1 | -0.13 | +0.10 | +0.03 | -0.05 |
| RTY | LVL_N_b0.2 | -0.14 | +0.08 | -0.00 | -0.06 |
| RTY | LVL_N_b0.3 | -0.13 | -0.04 | +0.09 | -0.06 |
| RTY | CHG_P_b0.1 | +0.05 | +0.07 | -0.23 | +0.01 |
| RTY | CHG_P_b0.2 | +0.07 | +0.02 | -0.34 | -0.01 |
| RTY | CHG_P_b0.3 | +0.14 | +0.08 | -0.49 | +0.02 |
| RTY | CHG_N_b0.1 | +0.00 | +0.03 | +0.09 | +0.02 |
| RTY | CHG_N_b0.2 | -0.10 | +0.25 | +0.32 | +0.05 |
| RTY | CHG_N_b0.3 | -0.17 | +0.26 | +0.47 | +0.03 |

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| clean cand | 1.40 | 2.59 | 3.64 | -78.8k | -78.2k | 362k | -80.4k | 44.8 |
| H1 cand | 2.36 | 4.16 | 3.81 | -80.3k | -79.6k | 145k | -81.8k | 25.0 |
| H2 cand | 1.31 | 2.60 | 2.03 | -80.3k | -79.4k | 242k | -81.6k | 55.6 |
| all cand | 1.53 | 2.85 | 6.53 | -79.7k | -78.9k | 362k | -81.8k | 44.0 |

Insurance flags (INS?, cost%, CVaR5 impr%, worst-week impr%, maxDD impr%): clean (False, -0.8, -0.1, 1.8, -29.3); H1 (False, -7.0, -3.4, -4.5, 4.3); H2 (False, -35.2, 1.0, 1.1, -11.5); all (False, -11.9, -0.6, 0.9, -29.3)

ERA FLAG: not testable pre-2023 for the pair (rows start 2023-02); no cost decomposition possible.

## Executability
NT8 at NinjaTrader Brokerage via Rithmic: entry-quantity multiplier from a daily file (expanding mean/std constants of the series and the previous close of VIX/VIX3M/VVIX/SKEW or VX M2/M1 refreshed after 16:15 ET, free CBOE data); sizes round to whole contracts; margin unchanged at multipliers <= 1, peak +50% at 1.5. No data purchase.

Files: code/census/night_ins/ap_py1_{feat,core,run,rep,xi,doc}.py; outputs/autopilot/py1/.

DONE PY1
