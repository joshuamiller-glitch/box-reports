# DS3_TI - T-I cross-sectional momentum across 27 markets (D3CT, 2026-10-26)

**Verdict: 0 PASS, 0 CANDIDATE, 24 DEAD (all report-only). Pool contribution 0 (want 4, min 1 not met). No PASS, so no 3x3 grid.**

Prereg `l2vast/ds3/prereg/T-I_prereg.md` sha256 `7b00b380fffc4799dcf122ab7de0ff7e4e2be4a190765e04f6a00104660b3bfe` (24 cells), frozen before scoring. Pre-holdout text `l2vast/ds3/out/TI/PREHOLD.md` logged with `log_holdout_look('TI')`, SPAN23 look with it. Rows `l2vast/ds3/rows/DS3_TI.json`; daily series `l2vast/ds3/out/TI/`; code `l2vast/ds3/code/th_cells.py`.

## Mechanism and prior
Market-neutral ranking by vol-scaled L-day return (L 63/126/252), long the top, short the bottom, weekly or monthly rebalance, market-wide or within asset class; risk-parity lots. Nearest scored: TC_X_D1 (WF -$265/wk DEAD), STRUCT48 T3.1 negative. Predicted +$0.2-0.5k/wk; below the MDE (about $1.5-3.8k/wk, measured), so report-only.

Disclosure on cells: within-class 'third' and '3' are identical by the prereg's own rule (1 per side for class size 3-4, else 2), so the 12 within-class cells are 6 distinct exposures (identical rows in the table); total distinct exposures 18.

## Results
| cell | WF mean | WF SD | MDE | CI WF mean | HOLD | L8W | IS | 2023-04..24-01 | trades/wk | 1.5x WF | 2x WF | pre-2023 t | placebo time | placebo lib | corr DS2 | max corr pool | verdict | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TI_L63_W_kthird_AL | -471 | 16206 | 3810 | [-3206, 2043] | 816 | 2745 | -1609 | -610 | 3.55 | -613 | -754 | 0.52 | 0.20 | 0.37 | -0.08 | 0.72 | DEAD | c2,c4,c5,c6 |
| TI_L63_W_kthird_CN | -310 | 6895 | 1621 | [-1415, 751] | 224 | -215 | -1617 | -1652 | 3.20 | -414 | -519 | -1.29 | 0.37 | 0.35 | -0.03 | 0.51 | DEAD | c2,c4,c5,c6 |
| TI_L63_W_k3_AL | -283 | 8774 | 2063 | [-1808, 1160] | 403 | -487 | -1018 | -815 | 2.06 | -354 | -424 | -0.18 | 0.28 | 0.37 | -0.06 | 0.63 | DEAD | c2,c3,c4,c5,c6 |
| TI_L63_W_k3_CN | -310 | 6895 | 1621 | [-1415, 751] | 224 | -215 | -1617 | -1652 | 3.20 | -414 | -519 | -1.29 | 0.37 | 0.35 | -0.03 | 0.51 | DEAD | c2,c4,c5,c6 |
| TI_L63_M_kthird_AL | 958 | 15662 | 3682 | [-1587, 3467] | 1903 | 3619 | -1648 | -1773 | 1.55 | 862 | 766 | 0.89 | 0.53 | 0.43 | -0.05 | 0.72 | DEAD | c3,c4,c5 |
| TI_L63_M_kthird_CN | 190 | 6693 | 1574 | [-910, 1225] | 226 | 132 | -1494 | -1680 | 1.25 | 129 | 67 | -0.49 | 0.50 | 0.37 | -0.02 | 0.49 | DEAD | c2,c3,c4,c5 |
| TI_L63_M_k3_AL | -192 | 7861 | 1848 | [-1551, 1103] | -30 | -1808 | -29 | -118 | 0.80 | -228 | -265 | 0.50 | 0.22 | 0.38 | -0.12 | 0.60 | DEAD | c1,c2,c3,c4,c5,c6 |
| TI_L63_M_k3_CN | 190 | 6693 | 1574 | [-910, 1225] | 226 | 132 | -1494 | -1680 | 1.25 | 129 | 67 | -0.49 | 0.50 | 0.37 | -0.02 | 0.49 | DEAD | c2,c3,c4,c5 |
| TI_L126_W_kthird_AL | -1557 | 15917 | 3742 | [-4241, 972] | 1317 | 5774 | -1547 | -1543 | 2.75 | -1681 | -1805 | 1.24 | 0.06 | 0.33 | -0.06 | 0.70 | DEAD | c2,c3,c4,c5,c6 |
| TI_L126_W_kthird_CN | 160 | 6236 | 1466 | [-845, 1068] | 356 | 1823 | -726 | -882 | 2.13 | 74 | -12 | -0.67 | 0.46 | 0.37 | -0.08 | -0.55 | DEAD | c2,c3,c4,c5 |
| TI_L126_W_k3_AL | -353 | 7243 | 1703 | [-1446, 781] | 705 | 846 | -692 | -555 | 1.54 | -408 | -464 | 0.41 | 0.16 | 0.37 | -0.12 | 0.58 | DEAD | c2,c3,c4,c5,c6 |
| TI_L126_W_k3_CN | 160 | 6236 | 1466 | [-845, 1068] | 356 | 1823 | -726 | -882 | 2.13 | 74 | -12 | -0.67 | 0.46 | 0.37 | -0.08 | -0.55 | DEAD | c2,c3,c4,c5 |
| TI_L126_M_kthird_AL | -901 | 14379 | 3380 | [-3334, 1570] | 1049 | 6348 | -1462 | -2236 | 1.23 | -987 | -1072 | 1.75 | 0.13 | 0.36 | -0.02 | 0.59 | DEAD | c2,c3,c4,c5,c6 |
| TI_L126_M_kthird_CN | 476 | 6608 | 1553 | [-635, 1527] | 476 | 1686 | -640 | -615 | 0.96 | 419 | 362 | -0.58 | 0.51 | 0.38 | -0.08 | -0.51 | DEAD | c3,c4,c5 |
| TI_L126_M_k3_AL | 213 | 7363 | 1731 | [-944, 1439] | 944 | 2458 | -254 | -179 | 0.62 | 179 | 144 | 1.53 | 0.36 | 0.41 | -0.16 | 0.67 | DEAD | c3,c4,c5 |
| TI_L126_M_k3_CN | 476 | 6608 | 1553 | [-635, 1527] | 476 | 1686 | -640 | -615 | 0.96 | 419 | 362 | -0.58 | 0.51 | 0.38 | -0.08 | -0.51 | DEAD | c3,c4,c5 |
| TI_L252_W_kthird_AL | 674 | 14438 | 3394 | [-1731, 2976] | 2349 | 4980 | -123 | 1099 | 2.10 | 567 | 460 | 1.56 | 0.43 | 0.41 | -0.17 | 0.68 | DEAD | c3,c4 |
| TI_L252_W_kthird_CN | 311 | 6694 | 1574 | [-789, 1363] | 687 | 971 | 121 | 243 | 1.59 | 240 | 169 | -0.32 | 0.50 | 0.38 | -0.06 | -0.57 | DEAD | c3,c4 |
| TI_L252_W_k3_AL | 466 | 7123 | 1675 | [-635, 1650] | 1142 | 795 | -505 | -162 | 1.27 | 420 | 373 | 1.48 | 0.51 | 0.42 | -0.18 | -0.58 | DEAD | c3,c4,c5 |
| TI_L252_W_k3_CN | 311 | 6694 | 1574 | [-789, 1363] | 687 | 971 | 121 | 243 | 1.59 | 240 | 169 | -0.32 | 0.50 | 0.38 | -0.06 | -0.57 | DEAD | c3,c4 |
| TI_L252_M_kthird_AL | 1310 | 13513 | 3177 | [-825, 3485] | 1912 | 3279 | -266 | 225 | 0.94 | 1231 | 1151 | 1.24 | 0.57 | 0.44 | -0.20 | 0.68 | DEAD | c3,c4 |
| TI_L252_M_kthird_CN | 592 | 6372 | 1498 | [-458, 1575] | 924 | 148 | -132 | 232 | 0.70 | 541 | 490 | -0.52 | 0.58 | 0.39 | -0.02 | -0.53 | DEAD | c3,c4 |
| TI_L252_M_k3_AL | 1248 | 6639 | 1561 | [158, 2395] | 1365 | -495 | 281 | 572 | 0.41 | 1220 | 1192 | 1.25 | 0.84 | 0.51 | -0.14 | -0.55 | DEAD | c3,c4 |
| TI_L252_M_k3_CN | 592 | 6372 | 1498 | [-458, 1575] | 924 | 148 | -132 | 232 | 0.70 | 541 | 490 | -0.52 | 0.58 | 0.39 | -0.02 | -0.53 | DEAD | c3,c4 |

Conventions: weekly $ at $1,000/day/market risk parity (fractional lots, monthly resize), 142 WF weeks (2024-02..2026-10), HOLD 2025-07+, cost proxy 1 tick/side + $4.84 RT ($1.78 MBT/MET), roll back-adjusted with one RT charged per roll in position. Fail codes: c1 HOLD mean>0, c2 marginal portfolio Sharpe vs DS2 10/10/7 up, c3 trades/wk>=3, c4 both placebos>=0.95, c5 SPAN23 sign = WF sign and WF>0, c6 WF mean>0. Max corr pool = largest |weekly WF corr| to any of the 31,098 pool books (informational, not gating; the pool contains many near-duplicate families so a maximum over 31k books is inflated). All cells are report-only per the prereg because the predicted effect is below the cell MDE.
Engine bug fixed before any holdout look: a market-closed day (e.g. 2018-12-06 in the rates futures) produced a false gap P&L in the first draft; fixed to take the gap from the last valid close on the next valid day and rerun before the pre-holdout text was logged.

## Reading
- No PASS or CANDIDATE. The only positive group is the 252-day lookback with monthly rebalance: all four of those cells have positive WF, holdout and SPAN23 means. The most striking is TI_L252_M_k3_AL (3 longs / 3 shorts of the 27, monthly): WF +$1,248/wk, CI [+158, +2,395] (excludes 0), holdout +$1,365, SPAN23 +$572, 2x cost +$1,192, 2014-22 t +1.25, marginal portfolio Sharpe vs DS2 up (1.75 to 2.30), weekly corr to DS2 -0.14. It fails on trade rate (0.41 trades/wk, structural for a monthly rebalance book: unmeasurable in a forward test at 3/wk) and placebo (timing-destroyed 0.84, library 0.51: below 0.95). Two failures, so DEAD by the bar, but it is the one LEAD from T-H/T-I worth a forward shadow, with the caveat that it is the best of 24 cells (DSR 0.13), the CI is the iid-week bootstrap, and the 2014-22 t of +1.25 does not reach significance. MDE for this cell: about $1.56k/wk, so the WF mean is below one MDE.
- Short lookbacks (63, 126 d) and weekly rebalances lose or are flat (e.g. L63 weekly -$471 to -$283/wk), consistent with cost drag at 3 to 4 trades/wk and no short-horizon cross-sectional momentum; the long-lookback gain is the usual 12-month momentum shape.
- Within-class (neutral) versions are weaker (+$592/wk at L252 monthly) than the market-wide ranking, so the signal is partly an asset-class tilt rather than within-class relative strength.
- Executability: needs a 27-market daily ranking: in NT8 a multi-instrument NinjaScript strategy (Add series per market, daily bars) or an external rank feeding orders; not a single-chart strategy. exec_status PENDING.
- Prior held: no result clears the placebo. MDE next to every null: see the MDE column.
