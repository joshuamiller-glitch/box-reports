# REPORT C1-F6 - VOL-REGIME SIZE SWITCH (cycle 1)
Pre-registered in PREREG_AUTOPILOT.md (cycle 1, 21:58Z) before any run. Baseline = live pair, combined week floor -8R, per-book week rule off (clean 1.46 / H1 2.83 / H2 2.30 weekly Sharpe), computed in a process that never imported b10_core. Fill model: NT8-faithful engine, 1 tick/side + $34.88 commission. Thresholds fitted on CLEAN only; H1/H2 read untouched. UNTOUCHED not read.

**Result: NO. 0 of 28 cells passes; the pair does not need a vol-regime size switch.** Verdict key (rep_common): 28 NO, 0 INSURANCE, 0 SURVIVES. 0 cells reach +0.10 weekly Sharpe on clean, H1 and H2 together (2 reach it on clean, 5 on H1, 3 on H2; none on the same cell).

## Data and look-ahead
- VX1/VX2 from data/databento/B10/vx_1d.dbn.zst (CFE daily bars 2018-11-04..2026-10-12: covers 2023-02..2026-10), contango = VX2/VX1-1 with the Track L roll (5 trading days pre-expiry). VIX = FRED VIXCLS to 2026-10-13. NQ 20-day realised vol from the box 1-min closes at 16:00 ET (daily log returns clipped +-5%).
- Decision-time rule: each entry uses the last value strictly before it: VX bar with UTC date <= entry UTC date - 1; VIX/RV observation date < entry ET date. Features are the previous close or older.
- Regimes: backwardation (VX contango < 0); VIX or NQ-RV above the clean-period 70/80/90th percentile. Multipliers x0.5/0.75/1.25/1.5 on entry size when flagged: 7 regimes x 4 = 28 cells. Flagged share of entries: 9-33%. Average size stays within 2% of live (0.98-1.00).

## Selection on clean only
Best clean Sharpe uplift: **VIX > clean 90th pct, size x1.5** (flagged 9% of entries). Read once on the other spans:

| span | Sharpe uplift (1 tick) | at 2x slippage | vs B.Cfg() pair | share of 200 label-shuffles >= real | shuffle p95 | bootstrap 90% CI of uplift |
|---|---|---|---|---|---|---|
| clean | +0.118 | +0.154 | +0.147 | 0.12 | +0.189 | [+0.01, +0.25] |
| H1 | +0.024 | +0.029 | +0.025 | 0.27 | +0.339 | [+0.00, +0.07] |
| H2 | -0.117 | -0.117 | -0.110 | 0.47 | +0.242 | [-0.28, +0.00] |
| all | +0.050 | +0.070 | +0.069 | 0.13 | +0.112 | [-0.03, +0.14] |

Top cells by clean uplift (all 28 are in cells.csv):
| regime | thr | mult | flagged share | clean dSh | H1 dSh | H2 dSh | all dSh | avg size ratio |
|---|---|---|---|---|---|---|---|---|
| vix | 90 | x1.5 | 9% | +0.118 | +0.024 | -0.117 | +0.050 | 0.994 |
| vix | 80 | x1.5 | 17% | +0.108 | -0.372 | -0.519 | -0.104 | 0.996 |
| rv | 90 | x1.5 | 8% | +0.098 | +0.000 | -0.416 | -0.035 | 1.000 |
| vix | 70 | x0.5 | 28% | +0.057 | -0.200 | -0.549 | -0.115 | 0.982 |
| rv | 80 | x1.5 | 24% | +0.039 | +0.000 | -0.266 | -0.038 | 0.994 |
| vix | 70 | x1.5 | 28% | +0.024 | -0.380 | -0.916 | -0.275 | 1.002 |
| vix | 70 | x0.75 | 28% | +0.009 | +0.078 | +0.147 | +0.049 | 0.997 |
| vix | 90 | x1.25 | 9% | -0.024 | -0.010 | -0.098 | -0.041 | 0.993 |

## Gates, translated for a sizing change
(There is no new book: additive framing becomes an entry-size multiplier, own timing-destroyed null becomes the shuffled-regime-label null, gate 6 is the effect on the pair's worst weeks.)
1. Pre-registered: yes.
2. Clean-only selection, H1/H2 read once: yes.
3. Sharpe +0.10 on each span: **FAIL** (clean +0.118, H1 +0.024, H2 -0.117). Worst week: unchanged (-$82.5k both); the flag rarely coincides with the worst week, so the switch does not touch tail weeks (mean change in the baseline's worst-decile weeks: +0).
4. Shuffled-label null: **FAIL**. The real clean uplift sits at the 88th percentile of 200 shuffles (p95 = +0.189); the selection of the best of 28 clean cells explains it. Bootstrap CIs include zero in every span, and the H2 interval is [-0.28, +0.00].
5. Plateau: **FAIL**, 25% of neighbours keep >=75% of the all-in uplift (neighbours below); 26-week rolling Sharpe >= baseline in 62% of windows. 2x slippage does not change the picture.
| neighbour | mult | all-in dSh |
|---|---|---|
| vix70 | x1.500 | -0.275 |
| vix80 | x1.500 | -0.104 |
| vix90 | x1.375 | +0.012 |
| vix90 | x1.625 | +0.062 |
6. Worst-decile: not applicable beyond the line above (no new book).
7. Executable: a DualStrat size multiplier would need a daily VIX/VX feed into the strategy at 17:55 ET; not worth specifying since it fails.

## Reading
- Across the 28 cells, mean uplift by regime family: backwardation clean -0.15/H1 +0.07/H2 -0.32; VIX -0.05/-0.13/-0.40; RV -0.12/+0.07/-0.26 (clean/H1/H2). The sign flips by span. Cutting size when VIX is above its 70th percentile (x0.75) does help H1 and H2 (+0.08, +0.15) but is flat on clean (+0.01) and is a single cell.
- No regime in VX term structure, VIX level or NQ realised vol separates the pair's good and bad periods in a way that holds out of sample. Consistent with D2 E1 (vol targeting) and D3 S1/S6.
- Limits: sizes change inside the per-book rules and the day lock, so a higher multiplier also moves those thresholds in dollars; no new look-ahead found but VX daily bars are UTC-day closes, so intraday regime changes are ignored.

Runtime: features 20 s; 28 cells 127 s on 3 workers; verdict table + 200-draw shuffle null + plateau + slippage 17 min on 3 workers.
Code: code/census/night_ins/ap_c1_f6_feat.py, ap_c1_f6_run.py, ap_c1_f6_stage2.py. Outputs: outputs/autopilot/c1/f6/ (cells.csv, verdicts.csv, REPORT_make.md, stage1.pkl, stage2.pkl).

DONE C1_F6
