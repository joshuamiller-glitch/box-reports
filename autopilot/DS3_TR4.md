# DS3 TR4: T-TREND PRO R5 (regime and confirmation) and R7 (learned trend-continuation)

Generated 2026-10-26T23:09Z. Research only. Prereg R5 `l2vast/ds3/prereg/TR4_R5_prereg.md` sha256 `370a5c25c1c8b9d005912f72a0c10665ec7deca36096596c322b63190aee049f` (30 cells); prereg R7A `TR4_R7A_prereg.md` sha256 `ab6ea2504889a1c4e2d75d7fada4211b6a82718e0f470931043aabd235f4da14` (28 cells). Both frozen in DECISIONS.md before any cell/model was scored. Code `l2vast/ds3/code/tr4/`; rows `l2vast/ds3/rows/DS3_TR4.json`; raw `l2vast/ds3/out/TR4/`. Pre-holdout text `autopilot/DS3_TR4_PREHOLD.md`; ONE holdout look (track DS3_TR4) covering R5, R7A and the 2023-04..2024-01 second holdout.

## 0. Answer
**Trend (TR4): 0 PASS, 0 CANDIDATE, 58 DEAD of 58 cells (30 R5 + 28 R7A).** Best entry conditioning cell: none; the closest is R5_TD_ST (trend-day size x1.5 + hold to close): paired +0.59 pt/trade vs the unconditioned ST book, CI [-0.6, 2.4] (includes 0, MDE about 1.4), holdout +1.26, but book dWK -$651/wk and placebo 0.92. Best per-kept-trade lift: R5_IM5_ST +2.4 and R5_IM1_ST +2.7 pts/kept trade (placebo 0.99/0.97) but they keep only 23-28% of trades so the dollar paired effect is -0.8/-1.1 pt and dWK -$4.2k/-$5.9k, holdout negative: selectivity without income. R7: AUC 0.506 [0.495, 0.519] (full) / 0.508 [0.497, 0.520] (no-tape) on WF, 0.513/0.516 on the holdout, permuted-label AUC 0.498-0.50; the tape columns add nothing (full vs no-tape identical within noise); no learned selection beats the unconditioned stream (all 28 paired effects negative, CIs mostly exclude 0 on the wrong side). DS3 marginal Sharpe: not computed, no PASS/CANDIDATE to mix (mix-into-DS3 lines owed to none). Nothing is registered to paper_all; no 3x3 widening is owed.
Verdict line: "Trend: 0 PASS, 0 CANDIDATE. Best entry: n/a (R5_TD_ST paired +0.59 pt/trade [-0.6,2.4], 29 trades/wk). Best exit on ST's own entries: not in this track (R4 = D3XT). DS3 marginal Sharpe n/a."

## 1. Method (what was held fixed)
Bases: ST, HM (DS2 live signal streams, regenerated rows equal ROWS_bench3: 8,309 / 6,311), KB = TE7_kelt3m_n14_m1.0, SM = TE6_st10m_n7_m3.0, EM = TE7_emax5m_f30_s50. Bracket/execution fixed (60 pt / 1.0R, flat 16:55, 10 lots, per-book locks, $4.84); MAPPED path-sim pricing (te_core machinery) through the exact lock engine. Gates act on SIGNALS before the busy filter (the book = entry + condition). Paired universe = the signals the unconditioned book trades; dropped trades count as the gain/loss of not taking them (s48score.paired_score, session-block bootstrap); book-level weekly difference vs the unconditioned book and ST10 (true P9) also in the rows. Timing-destroyed placebo = same number kept at random within hour x side strata (1000 draws). Windows: PRE 2024-02..2025-06, holdout 2025-07+, second holdout 2023-04..2024-01 (R5: direct feature gates; R7: CPCV OOF, sign only; the forecaster does not exist before 2024-02 so QUIET cells are unconditioned on that span). Base streams reuse series that had earlier holdout looks (disclosed).
**Data availability.** ES, RTY, YM, ZN 1-min on disk (intermarket). Breadth proxy: constituent tape IS on disk as 1-min OHLCV for 10 mega-caps + QQQ (EQUS.MINI, 2023-03-28..2026-10-13), used (BR70; 10 names only, not a full-index breadth). VIX term slope = VIX3M - VIX from the forecast table (as-of session open). Compression forecaster = D3R pquiet_series (LightGBM P_quiet, theta 0.6, available from 2024-02). Not built: developing VAH/VAL levels (R2 level list uses prior-day, overnight, prior-week, NY opening-range levels only).

## 2. R5 results (30 cells; WF = 2024-02+; paired effect in net pts per unconditioned-book trade, 10 lots = $200/pt)
Reading: every gate that drops trades has a negative paired effect by construction whenever the base book earns a positive mean, because dropped trades lose their mean; the placebo rank and the per-kept lift measure selectivity. MDE (80% power, bootstrap) next to each estimate; the ex-ante MDE was 1.2-5.1 pts for gates and the predicted effects (+0.3 to +1.5) were below it for most cells, so a null is a null at that resolution only. Best-of-30 null: best standardised placebo z = 2.11 (R5_IM5_ST) vs ~2.0 expected as the maximum of 30 independent N(0,1): consistent with chance. Trade-frequency: every R5 cell is >= 3 trades/wk (SM/EM 5-12/wk); none is LOW-FREQUENCY. Long/short and quiet/wide columns are in the rows (cols, signal.long/short/quiet/wide).
| cell | verdict | WF paired pts [CI] | MDE | per-kept lift | HOLD pts | SPAN2 pts | plc rank | book dWK vs uncond $/wk | tr/wk WF | low-freq |
|--|--|--|--|--|--|--|--|--|--|--|
| R5_HTF3_ST | DEAD | -0.37 [-1.2,0.4] | 1.2 | 0.65 | 0.11 | 0.15 | 0.91 | 2,149 | 26.1 |  |
| R5_HTF3_HM | DEAD | -0.81 [-1.8,0.1] | 1.4 | 0.81 | -0.82 | 0.72 | 0.89 | 244 | 20.9 |  |
| R5_HTF3_KB | DEAD | -0.67 [-1.5,0.2] | 1.3 | 0.56 | 0.04 | 0.42 | 0.74 | -2,582 | 24.3 |  |
| R5_HTF3_SM | DEAD | -3.10 [-5.2,-1.0] | 3.0 | -1.44 | -2.55 | -1.53 | 0.23 | -8,356 | 5.1 |  |
| R5_HTF3_EM | DEAD | -2.01 [-4.1,0.2] | 3.0 | 1.58 | -1.81 | -0.79 | 0.85 | -4,375 | 5.7 |  |
| R5_DW_ST | DEAD | -0.98 [-2.0,0.1] | 1.5 | 0.76 | -1.05 | 0.21 | 0.92 | -6,862 | 17.7 |  |
| R5_DW_HM | DEAD | -1.27 [-2.5,-0.1] | 1.8 | 1.30 | -2.11 | 0.74 | 0.94 | -900 | 15.0 |  |
| R5_DW_KB | DEAD | -0.99 [-2.0,0.1] | 1.5 | 0.28 | -0.65 | 1.05 | 0.61 | -11,438 | 18.8 |  |
| R5_DW_SM | DEAD | -2.21 [-4.1,-0.1] | 2.8 | 0.45 | -1.22 | -0.49 | 0.48 | -6,750 | 5.9 |  |
| R5_DW_EM | DEAD | -2.86 [-4.8,-0.9] | 2.9 | -1.75 | -2.45 | -1.98 | 0.22 | -7,022 | 6.1 |  |
| R5_IM5_ST | DEAD | -0.84 [-2.0,0.4] | 1.6 | 2.44 | -0.87 | 0.03 | 0.99 | -4,209 | 19.9 |  |
| R5_IM5_HM | DEAD | -1.54 [-2.5,-0.6] | 1.3 | -0.65 | -1.25 | -0.22 | 0.18 | -5,424 | 22.2 |  |
| R5_IM5_KB | DEAD | -0.87 [-1.7,-0.0] | 1.2 | -0.27 | -0.35 | -0.97 | 0.35 | -10,735 | 26.6 |  |
| R5_IM5_SM | DEAD | -1.51 [-2.9,-0.1] | 2.1 | -0.38 | -2.03 | 0.28 | 0.34 | -3,458 | 8.9 |  |
| R5_IM5_EM | DEAD | -2.10 [-4.0,-0.3] | 2.7 | -0.44 | -2.28 | 0.68 | 0.34 | -3,619 | 7.1 |  |
| R5_QUIET_ST | DEAD | -0.64 [-1.3,0.0] | 0.9 | -0.25 | -0.55 | -0.93 | 0.27 | -4,976 | 23.3 |  |
| R5_QUIET_HM | DEAD | -0.52 [-1.3,0.3] | 1.1 | 0.24 | -0.81 | -0.23 | 0.78 | -1,267 | 20.7 |  |
| R5_QUIET_KB | DEAD | -0.23 [-0.8,0.4] | 0.8 | 0.22 | -0.05 | 0.35 | 0.81 | -2,553 | 23.4 |  |
| R5_QUIET_SM | DEAD | -1.06 [-2.4,0.2] | 1.9 | -0.03 | 0.11 | -0.82 | 0.48 | -2,665 | 9.4 |  |
| R5_QUIET_EM | DEAD | -0.45 [-1.6,0.8] | 1.8 | 0.74 | -0.13 | -0.10 | 0.83 | -746 | 9.0 |  |
| R5_TD_ST | DEAD | 0.59 [-0.6,2.4] | 2.2 | nan | 1.26 | 0.49 | 0.92 | -651 | 29.2 |  |
| R5_TD_HM | DEAD | 0.51 [-0.6,2.3] | 2.3 | nan | 1.37 | 0.85 | 0.92 | -622 | 26.3 |  |
| R5_TD_KB | DEAD | 0.56 [-0.5,2.3] | 2.1 | nan | 1.35 | -0.08 | 0.91 | -1,091 | 29.2 |  |
| R5_TD_SM | DEAD | 0.15 [-0.3,0.8] | 0.8 | nan | 0.06 | 0.00 | 0.83 | -78 | 12.5 |  |
| R5_TD_EM | DEAD | -0.31 [-0.9,0.3] | 0.8 | nan | -0.34 | -0.10 | 0.04 | -36 | 12.1 |  |
| R5_IM1_ST | DEAD | -1.05 [-2.3,0.1] | 1.7 | 2.67 | -0.90 | -0.02 | 0.97 | -5,899 | 17.2 |  |
| R5_IM1_KB | DEAD | -1.46 [-2.5,-0.5] | 1.5 | -0.92 | -0.91 | -0.90 | 0.13 | -7,937 | 23.1 |  |
| R5_ZNOK_ST | DEAD | -0.21 [-0.8,0.3] | 0.8 | 0.13 | 0.08 | -0.11 | 0.68 | 2,152 | 29.0 |  |
| R5_ZNOK_KB | DEAD | -0.27 [-0.8,0.3] | 0.7 | 0.01 | -0.03 | 0.88 | 0.41 | -735 | 28.6 |  |
| R5_BR70_ST | DEAD | -0.58 [-1.3,0.2] | 1.1 | 0.09 | -0.12 | 1.51 | 0.53 | -1,031 | 26.1 |  |

TD (trend-day) rule: 61 flagged days of 913 (6.7%); the sizing-lock verdict criterion needs mean up with CI or SD/maxDD down with CI: the weekly-mean CI includes 0 for all five bases, so DEAD (V2 sizing criterion, MAPPED basis; the no-target hold variant has no direct-replay arm in te_direct, so direct replay was not run).
Descriptive columns (realised-vol tercile, VIX-term tercile, day of week, session; 5 bases x PRE/HOLD, 140 level looks): 4 CIs exclude 0 (7 expected by chance at 5%), none replicate PRE to holdout. Nothing is gated on them (`out/TR4/r5_columns_final.json`).

## 3. R7A results (28 cells)
Pipelines: 2 featsets x (1 walk-forward + 1 CPCV + 20 label-permutation), 2,832 LightGBM fits, 33 monthly folds, 7-day embargo/purge; in-window feature selection kept ~16-17 features per fold and ZERO of the 20 noise columns in any fold (noise gain share 0); isotonic calibration in-window. AUC (week-block 95% CI): full PRE 0.501 [0.490,0.515], WF 0.506 [0.495,0.519], HOLD 0.513 [0.500,0.528], CPCV(all) 0.512, CPCV 2023-04..2024-01 0.525 [0.498,0.552]; no-tape PRE 0.498, WF 0.508, HOLD 0.516, CPCV 0.512. |WF-CPCV| <= 0.05 holds; the PRE AUC CI lower bound is < 0.5 in both featsets, so the model guard fails. The AUC MDE is about 0.02; the lift needed for calibrated P to reach 0.55 on many events is about 0.04, which is why only 0.1-5% of events reach theta (selected share, tr/wk below). PRED prior (AUC 0.50-0.54) reproduced; tape adds nothing.
| cell | verdict | selected events | WF paired pts [CI] | MDE | HOLD pts | perm rank (20) | book dWK vs uncond $/wk | tr/wk WF |
|--|--|--|--|--|--|--|--|--|
| R7_POOL_full_55 | DEAD | 9664 | -1.26 [-2.3,-0.2] | 1.5 | -0.78 | 0.25 | -17,801 | 9.17 |
| R7_POOL_full_60 | DEAD | 2018 | -1.11 [-2.1,-0.0] | 1.5 | -0.60 | 1.00 | -16,757 | 2.80 |
| R7_POOL_notape_55 | DEAD | 7034 | -1.24 [-2.2,-0.2] | 1.5 | -0.73 | 0.45 | -16,448 | 6.59 |
| R7_POOL_notape_60 | DEAD | 1180 | -1.23 [-2.2,-0.2] | 1.5 | -0.76 | 0.65 | -18,692 | 1.78 |
| R7_ST_full_55 | DEAD | 2735 | -1.95 [-3.2,-0.6] | 1.8 | -1.70 | 0.25 | -15,594 | 5.94 |
| R7_ST_full_60 | DEAD | 556 | -1.86 [-3.1,-0.5] | 1.9 | -1.50 | 0.85 | -12,018 | 1.59 |
| R7_ST_notape_55 | DEAD | 2009 | -1.90 [-3.2,-0.5] | 1.8 | -1.49 | 0.50 | -14,145 | 4.34 |
| R7_ST_notape_60 | DEAD | 293 | -2.05 [-3.3,-0.7] | 1.9 | -1.71 | 0.00 | -13,651 | 0.94 |
| R7_HM_full_55 | DEAD | 1699 | -2.34 [-3.8,-0.9] | 2.1 | -2.14 | 0.90 | -7,475 | 4.94 |
| R7_HM_full_60 | DEAD | 376 | -2.73 [-4.3,-1.3] | 2.1 | -2.98 | 0.90 | -10,136 | 1.38 |
| R7_HM_notape_55 | DEAD | 1267 | -2.75 [-4.3,-1.3] | 2.1 | -2.84 | 0.40 | -9,656 | 3.55 |
| R7_HM_notape_60 | DEAD | 243 | -2.85 [-4.4,-1.5] | 2.1 | -3.10 | 0.50 | -11,129 | 0.90 |
| R7_KB_full_55 | DEAD | 3381 | -1.50 [-2.7,-0.3] | 1.8 | -0.21 | 0.85 | -11,517 | 6.73 |
| R7_KB_full_60 | DEAD | 678 | -1.64 [-2.9,-0.4] | 1.9 | -0.52 | 0.90 | -13,415 | 1.85 |
| R7_KB_notape_55 | DEAD | 2432 | -1.37 [-2.6,-0.1] | 1.8 | -0.11 | 0.95 | -11,923 | 4.85 |
| R7_KB_notape_60 | DEAD | 418 | -1.60 [-2.9,-0.3] | 1.9 | -0.45 | 1.00 | -14,226 | 1.20 |
| R7_SM_full_55 | DEAD | 262 | -3.33 [-5.6,-1.0] | 3.3 | -2.64 | 0.85 | -8,418 | 1.47 |
| R7_SM_full_60 | DEAD | 57 | -3.62 [-6.1,-1.2] | 3.5 | -3.23 | 0.80 | -8,853 | 0.35 |
| R7_SM_notape_55 | DEAD | 168 | -3.83 [-6.3,-1.4] | 3.4 | -3.23 | 0.25 | -10,193 | 0.88 |
| R7_SM_notape_60 | DEAD | 23 | -3.86 [-6.3,-1.4] | 3.5 | -3.52 | 0.25 | nan | 0.00 |
| R7_EM_full_55 | DEAD | 266 | -3.39 [-5.6,-0.9] | 3.4 | -2.89 | 0.20 | -7,826 | 1.39 |
| R7_EM_full_60 | DEAD | 47 | -3.60 [-6.0,-1.1] | 3.5 | -3.31 | 0.05 | -7,899 | 0.25 |
| R7_EM_notape_55 | DEAD | 181 | -3.61 [-5.8,-1.2] | 3.4 | -3.47 | 0.00 | -8,349 | 0.92 |
| R7_EM_notape_60 | DEAD | 24 | -3.49 [-5.8,-1.0] | 3.6 | -3.42 | 0.45 | nan | 0.00 |
| R7_EXTRA_full_55 | DEAD | 3056 | -1.12 [-2.4,0.1] | 1.8 | -0.56 | 0.85 | -8,195 | 6.46 |
| R7_EXTRA_full_60 | DEAD | 668 | -1.29 [-2.6,0.1] | 1.9 | -0.97 | 0.90 | -11,964 | 1.78 |
| R7_EXTRA_notape_55 | DEAD | 2174 | -1.11 [-2.4,0.2] | 1.9 | -0.63 | 0.85 | -12,007 | 4.57 |
| R7_EXTRA_notape_60 | DEAD | 384 | -1.27 [-2.6,0.1] | 1.9 | -0.99 | 0.95 | -11,268 | 1.08 |
Best-of-28 null: no cell has a positive paired effect (max HOLD effect -0.11 pt), so the best-of-N statistic is below every permutation draw's maximum; permutation ranks in the table (20 draws, resolution 0.05) are scattered 0-1 with no pattern. LOW-FREQUENCY (<3 tr/wk) is marked in the rows: all theta 0.60 cells except none reach 3/wk (POOL full 2.8 is also below), and at theta 0.55 only POOL, ST, HM, KB, EXTRA cells reach >= 3/wk.

## 4. Executability, direct replay, deviations
Gates (HTF3, DW, IM, ZNOK, BR70, TD) are NT8-deliverable from bars (multi-series for ES/RTY/YM/ZN and constituents); QUIET needs the external forecaster table; R7 full = execution-server only (L2/tape/book + inference), R7 no-tape = precomputed P table. Direct L2 replay was owed for PASS/CANDIDATE and the "top 5 by PRE paired effect"; since there is no cell with a positive paired CI and every point estimate but five R5 cells is negative, direct replay was not run (pricing cannot turn a negative paired effect positive; stated deviation). Added at the final stage for reporting only: per-kept-trade lift and the descriptive columns. TR1/TR2 trigger streams (group R7B) were not available as final tables in time and are not scored; the R7A pool uses the T-ENTRY/T-B trigger families only.
Ledger: DS3_TR4_R5 30 + COLUMNS 75, DS3_TR4_R7A 28 + PIPELINES 44 (total counted this track 177).
