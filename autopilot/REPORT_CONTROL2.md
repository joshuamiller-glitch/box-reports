# REPORT CONTROL2 - the ST, HM, WT-10 and pair grids as METHOD-2 families (directive METHOD-2 item 6; item 7 for the intraday-other families)

**Configuration (POWER2 accepted):** fit 12 / read 3 / step 3 months, ensemble rule `tilt` (weights proportional to positive fit-window Sharpe, each cell scaled to unit SD on the fit window), 142 OOS weeks from 2024-02, halves 2024-02..2025-04 and 2025-05..2026-10, family null = sign-flip (one random sign per ISO week applied to all cells; ST, HM, WT and the pair are two-sided long/short books; the net-exposure check, correlation of the OOS daily series with NQ daily changes, is +0.00 / +0.01 / -0.01 / +0.04, so the drift-matched custom null is not needed), 200 replicates, gates a-d (Sharpe and net > 0; null rank >= 0.95; 4-week block bootstrap 90% CI of the OOS weekly mean > 0; both halves positive). Matrices: outputs/methods2/fam/CTRL_{ST,HM,WT10,PAIR}.npz (229 / 229 / 270 / 247 cells from the CONTROL run: NT8-faithful harness with lot netting for the pair). Code: ap_m2_ctrl2.py, ap_m2_ctrl2_bof.py.

## 1. Family verdicts (OOS ensemble)

| family | cells | OOS Sh | net (unit) | null rank | null p95 | boot lo (weekly mean) | half 1 / half 2 (Sharpe) | corr with pair | gates a/b/c/d | best-of-F rank (F=567 / F=4) | power class (adjacent-cell Sharpe ratio vs the live cell) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| CTRL_ST | 229 | 1.65 | 56.0 | 1.000 | 1.00 | +0.165 | 1.52 / 1.75 | +0.71 | 1111 | 0.22 / 0.995 | peaked (~80% decay), ratio 0.71; 100% of cells have positive full-window Sharpe |
| CTRL_HM | 229 | 2.18 | 71.4 | 1.000 | 0.96 | +0.285 | 1.61 / 2.72 | +0.61 | 1111 | 0.90 / 1.000 | flat (~97% decay), ratio 1.20; 100% of cells have positive full-window Sharpe |
| CTRL_WT10 | 270 | 0.59 | 12.9 | 0.805 | 1.06 | -0.055 | 0.18 / 0.94 | +0.10 | 1001 | 0.00 / 0.430 | peaked (~80% decay), ratio 0.65; 73% of cells have positive full-window Sharpe |
| CTRL_PAIR | 247 | 1.83 | 66.0 | 1.000 | 0.95 | +0.226 | 1.68 / 1.95 | +0.84 | 1111 | 0.59 / 1.000 | peaked (~80% decay), ratio 0.77; 100% of cells have positive full-window Sharpe |

Reading: the ST, HM and PAIR ensembles pass gates a-d (OOS Sharpe 1.65 / 2.18 / 1.83, null rank 1.00, bootstrap lower bound above zero, both halves positive); the WT-10 ensemble fails (0.59, null rank 0.81, bootstrap lower bound -0.06, first half 0.18): the WT family (ATR 10-20, multiplier 2-4, 5/10/15-minute bars, EMA on/off, three brackets) is dominated by weak cells although the live WT-10 cell itself is strong in-sample. METHOD-2 therefore labels the pair family PASS on gates a-d, which is the answer to "would the method find a book of the pair quality": yes, at OOS Sharpe 1.8 with a peaked neighbourhood. The best-of-F rank against 567 independent families is below 0.95 for all three (ST 0.22, pair 0.59, HM 0.90); the independent-draw approximation is conservative because the 563 comparison families are heavily correlated (many are rule variants of one mechanism), so the global F that the harness owner computes is the figure to use; no independent pre-registered replication exists for these families.

## 2. Does the ensemble beat its live cell? (OOS days, ensemble scaled to the live cell OOS daily SD, native 8-NQ dollars)

| family | live-cell OOS Sh | clean-selected cell OOS Sh | ensemble OOS Sh | max DD live / ensemble | worst week live / ensemble | beats live: Sharpe / DD / worst week |
|---|---|---|---|---|---|---|
| CTRL_ST | 2.01 | 2.06 | 1.65 | $268k / $317k | $-78k / $-96k | no / no / no |
| CTRL_HM | 1.22 | 2.47 | 2.18 | $276k / $265k | $-78k / $-95k | yes / yes / no |
| CTRL_WT10 | 1.82 | 1.29 | 0.59 | $213k / $250k | $-59k / $-70k | no / no / no |
| CTRL_PAIR | 2.10 | 2.05 | 1.83 | $280k / $367k | $-83k / $-104k | no / no / no |

CAVEAT: the live cells were chosen on 2023-26 data, so they are in-sample inside the OOS window (their OOS Sharpe of 2.0 / 1.2 / 1.8 / 2.1 is not out-of-sample); the only out-of-sample element is the ensemble rule. Result: the ensemble does not beat the in-sample live cell for ST, WT and the pair (Sharpe 1.65 vs 2.01, 0.59 vs 1.82, 1.83 vs 2.10; max DD and worst week are 18-31% larger at the same volatility), but it gets within 0.3 Sharpe of the pair without choosing any parameter, and it beats the live HM cell (2.18 vs 1.22, smaller max DD, worse worst week) because the live HM cell is a weak cell of its family (rank 94 of 138 on clean Sharpe). The pair ensemble sized to the pair 6/6 DD match ($210k) earns $1.37M net over the OOS window with worst week $-60k (harness sizing).

## 3. Power class (so the pass is read at the right power)

POWER2 power at true Sharpe 1.5 is 38% for a peaked neighbourhood (decay ~80%) and 90% for a flat one (~97%). The adjacent-cell Sharpe ratio (one grid step, one parameter at a time, full-window weekly Sharpe relative to the live cell) is 0.71 for ST, 0.77 for the pair and 0.65 for WT (peaked), and 1.20 for HM (flat, because the live HM cell is below its neighbours). The pair and ST passes are therefore passes of peaked families: they clear the null at Sharpe ~1.7-1.8, where peaked-family power is about 40-60%, and a pair-grade book with these neighbourhoods would be found about half of the time.

## 4. Item 7: the intraday-other families (563 families: Q, BJ, BM, BI, B1/B4/B7/B10 grids, E, J incl. v3-x)

Scored with the same configuration (sign-flip family null, 200 replicates, gates a-d, beta check against NQ). Results: outputs/methods2/FAMILY_RESULTS.csv (also FAMILY_RESULTS_intraday_other.csv). 0 families pass gates a-d on their own null (BM13_NQ, BM11_NQ, BM8_RTY, BM12_NQ, Q37_RTY, BI8_YM; none has a net-exposure correlation above 0.15); 138 of 563 have a positive OOS Sharpe; median OOS Sharpe -0.49. Against the best-of-F null within the 563 + 4 families no family reaches 0.95 (best: BM13_NQ rank 0.48 at OOS Sharpe 1.77 with only 6 cells; BM11_NQ 0.03); POWER2 measured a 1.7% false-positive rate for zero-edge families, so about 10 single-family passes are expected by chance among 563 families; 6 is below that count (the families are correlated, so the count is noisy). No resting-order family (E, J) passes gates a-d: the best is M2-E-L0-ooat (OOS Sharpe 1.01, null rank 0.96, bootstrap lower bound -0.05).

Top 10 by OOS Sharpe:

| family | cells | OOS Sh | null rank | boot lo | best-of-F | gates | verdict |
|---|---|---|---|---|---|---|---|
| BM13_NQ | 6 | 1.77 | 1.00 | +0.31 | 0.482 | 1111 | FAIL (best-of-F 0.48 < 0.95) |
| BM11_NQ | 8 | 1.46 | 0.99 | +0.13 | 0.025 | 1111 | FAIL (best-of-F 0.03 < 0.95) |
| BM8_RTY | 12 | 1.32 | 0.99 | +0.11 | 0.001 | 1111 | FAIL (best-of-F 0.00 < 0.95) |
| BM12_NQ | 12 | 1.28 | 0.98 | +0.08 | 0.000 | 1111 | FAIL (best-of-F 0.00 < 0.95) |
| Q37_RTY | 8 | 1.24 | 0.97 | +0.01 | 0.000 | 1111 | FAIL (best-of-F 0.00 < 0.95) |
| BI8_YM | 12 | 1.10 | 1.00 | +0.01 | 0.000 | 1111 | FAIL (best-of-F 0.00 < 0.95) |
| BM2_BTC | 12 | 1.08 | 0.96 | -0.09 | 0.000 | 1100 | FAIL |
| M2-E-L0-ooat | 8 | 1.01 | 0.95 | -0.05 | 0.000 | 1100 | FAIL |
| M2-E-CH-ooat | 16 | 1.01 | 0.93 | -0.00 | 0.000 | 1001 | FAIL |
| BM8_BTC | 12 | 0.97 | 0.98 | -0.02 | 0.000 | 1101 | FAIL |

BK/BQ (pair-overlay families) and Q22 (spread series files missing) are not scored: the overlays modify the pair and need a different construct. The plateau breadth in FAMILY_RESULTS for the market-entry families is the share of cells with positive full-window Sharpe, and the adjacent ratio is a grid-order proxy (median Sharpe ratio of consecutive cells); for the CONTROL families the adjacency is exact (one parameter, one grid step).

## 5. LIVEPACK status

For the intraday-other families nothing meets the pack condition (gates a-d + best-of-F >= 0.95 or an independent pre-registered replication): the CONTROL ST, HM and pair ensembles pass gates a-d but their best-of-F ranks are 0.22 / 0.90 / 0.59 with F=567, and no replication was pre-registered. Nothing is emitted unless the global best-of-F computed by the harness owner puts one of them at or above 0.95.

DONE CONTROL2
