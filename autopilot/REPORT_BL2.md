# REPORT BL2 - side-count-matched (drift-matched) null for Q9 and the b2356 daily families; null ported as an option (analysis only)
**Verdict: 69 selected cells of the ap_y_run-covered b2356 families (ERA-retro, clean-only selection; Q2-Q10, N3-N7, W4/W6/W8, V1-V10, T6, S3/S5/S10, R1, Y1/Y2/Y5, Z2/Z3/Z10) were re-scored. The legacy null draws random dates with random +-1 sides; the new null draws random dates in each year with exactly the real number of long and short trades per symbol and year. 11 cells flip pass -> FAIL, 9 flip fail -> pass, 49 unchanged. Lead impact: Q10 commodity momentum (COM 20) loses the null (rank 1.00 -> 0.85); Q9 ALL26 low-vol reversal HOLDS (1.00 vs 1.00; real 1.38 vs new p95 1.14) but its MACRO12 sibling fails; Q5 k=4 holds (0.98) while its k=3 and (30,2) siblings fail and all three Q3 relatives fail, so the Q5ENS 12-cell ensemble LEAD must be re-checked (flag); N3 NQ holds (0.97) while N3 ES flips to fail; W4 EQ stays a pass (and a NO for wd corr). No FOUND or FOUND-PENDING item sits in this set, so nothing in LEDGER.md or the frozen predictions is touched; Q5ENS is flagged for the coordinator.**

## 1. Method and a caution about what the new null removes
- Legacy null (ap_y_run.job_null): per symbol, the real number of trades per calendar year, random dates (with replacement), sides random +-1; statistic = pair-window weekly Sharpe, 29 x 7 = 203 draws.
- Matched null (ap_null_dm.job_null_dm): same dates logic and counts, but per symbol and year EXACTLY the real n_long and n_short with sides permuted. Same hold, same ATR sizing, same costs, same 203 draws; the legacy null is re-run on identical seeds in the same script (ap_bl2_dm.py), so old and new ranks are like for like.
- Caution: for trend, momentum and cross-sectional rules the realised side counts per symbol-year ARE largely the edge (the rule is long what is trending up in that year). Matching them lets random dates inside the year earn the asset-year trend, so the new null median is +0.5 to +1.2 Sharpe for Q3/Q5/Q8/Q10 (it was -0.1). A FAIL there means 'not distinguishable from the exposure the rule carried', which is the question asked (drift/exposure-matched), but it is a harsher test than a timing null for these families and should be read together with replication, not alone. For fade/mean-reversion rules (S5, Y1, V9, Q4) the matched null is strongly NEGATIVE (-0.7 to -1.0): the rule fades the trend, so random dates with the same sides lose; these flip to pass.

## 2. Table (pair-window all-in weekly Sharpe vs the two nulls; rank = share of null draws below the real value; pass = real > p95)
| family | cell | pair-window long fraction | real Sharpe | legacy p95 / rank | matched p95 / rank | null median old -> new | change | status in CANDIDATES |
|---|---|---|---|---|---|---|---|---|
| Q4 | Q4_mom_20_XS_0_rev_W_h4_MACRO12 | 0.50 | +0.17 | +0.60 / 0.80 | +0.05 / 0.97 | -0.27 -> -0.99 | fail->pass |  |
| Q7 | Q7_hi52_252_XS_0_rev_W_h4_ALL26 | 0.50 | +0.35 | +0.47 / 0.92 | -0.84 / 1.00 | -0.43 -> -1.56 | fail->pass |  |
| S5 | S5_20_1.0_h5_ALL26 | 0.45 | +0.35 | +0.72 / 0.85 | -0.16 / 1.00 | -0.21 -> -0.90 | fail->pass |  |
| S5 | S5_60_1.0_h5_ALL26 | 0.40 | +0.40 | +0.70 / 0.88 | +0.06 / 1.00 | -0.18 -> -0.85 | fail->pass |  |
| S5 | S5_60_1.0_h5_SCR | 0.32 | +0.23 | +0.70 / 0.72 | +0.17 / 0.96 | -0.11 -> -0.67 | fail->pass |  |
| V9 | V9_1.5_0.33_h5_ALL26 | 0.54 | +0.40 | +0.58 / 0.92 | -0.07 / 0.98 | -0.40 -> -0.88 | fail->pass |  |
| V9 | V9_2.0_0.5_h5_ALL26 | 0.49 | +0.53 | +0.56 / 0.94 | +0.00 / 1.00 | -0.33 -> -0.79 | fail->pass |  |
| Y1 | Y1_3_fade_h3_SCR | 0.46 | +0.44 | +0.62 / 0.92 | +0.27 / 0.97 | -0.26 -> -0.67 | fail->pass |  |
| Y1 | Y1_4_fade_h3_ALL26 | 0.49 | +0.34 | +0.38 / 0.93 | -0.20 / 1.00 | -0.59 -> -1.05 | fail->pass |  |
| N3 | N3_flat_h1_ES | 1.00 | +1.07 | +0.82 / 0.98 | +1.16 / 0.91 | -0.08 -> +0.34 | pass->FAIL |  |
| Q10 | Q10_mom_20_XS_0_as_M_h19_COM | 0.50 | +1.25 | +0.69 / 1.00 | +1.54 / 0.85 | -0.16 -> +0.72 | pass->FAIL | LEAD (Q10) |
| Q3 | Q3_mom_252_XS_0_as_M_h19_ALL26 | 0.50 | +1.06 | +0.75 / 0.98 | +1.83 / 0.34 | -0.12 -> +1.20 | pass->FAIL |  |
| Q3 | Q3_mom_252_XS_0_as_M_h19_MACRO12 | 0.50 | +1.05 | +0.86 / 0.97 | +1.81 / 0.52 | -0.06 -> +1.00 | pass->FAIL |  |
| Q3 | Q3_mom_63_XS_0_as_M_h19_ALL26 | 0.50 | +0.80 | +0.73 / 0.96 | +1.76 / 0.29 | -0.11 -> +1.06 | pass->FAIL |  |
| Q5 | Q5_mom_25_XS_3_as_M_h19_MACRO12 | 0.50 | +1.29 | +0.75 / 1.00 | +1.40 / 0.92 | -0.10 -> +0.61 | pass->FAIL | Q5ENS member |
| Q5 | Q5_mom_30_XS_2_as_M_h19_MACRO12 | 0.50 | +1.02 | +0.79 / 0.98 | +1.28 / 0.83 | -0.09 -> +0.60 | pass->FAIL | Q5ENS member |
| Q8 | Q8_skew_120_XS_0_as_M_h19_MACRO12 | 0.50 | +1.08 | +0.71 / 0.99 | +1.48 / 0.84 | -0.07 -> +0.60 | pass->FAIL |  |
| Q9 | Q9_lowvol_20_XS_0_rev_M_h19_MACRO12 | 0.50 | +0.87 | +0.66 / 0.97 | +1.13 / 0.86 | -0.12 -> +0.58 | pass->FAIL |  |
| S10 | S10_follow_h1_RATES | 0.50 | -0.01 | -0.08 / 0.97 | +0.06 / 0.92 | -0.91 -> -0.84 | pass->FAIL |  |
| V10 | V10_('lo', 0.5)_h1_SCR | 0.50 | +0.90 | +0.77 / 0.97 | +0.91 / 0.95 | -0.01 -> -0.08 | pass->FAIL |  |
| N3 | N3_flat_h1_NQ | 1.00 | +1.20 | +0.82 / 1.00 | +1.11 / 0.97 | +0.02 -> +0.31 | unchanged | LEAD weak (N3, long NQ beta) |
| N3 | N3_flat_h1_RTY | 1.00 | +1.12 | +0.75 / 0.99 | +0.84 / 0.99 | -0.14 -> -0.12 | unchanged |  |
| N4 | N4_6A_5_-1_h5_EQ2 | 0.49 | +0.47 | +0.92 / 0.78 | +0.84 / 0.85 | +0.05 -> -0.02 | unchanged |  |
| N4 | N4_6J_10_1_h5_EQ2 | 0.34 | +0.31 | +0.88 / 0.73 | +0.54 / 0.90 | -0.02 -> -0.37 | unchanged |  |
| N4 | N4_HG_5_1_h5_EQ2 | 0.55 | +0.49 | +0.92 / 0.81 | +0.98 / 0.79 | +0.01 -> +0.08 | unchanged |  |
| Q10 | Q10_mom_10_XS_0_as_M_h19_RATES | 0.50 | +0.64 | +0.69 / 0.94 | +0.64 / 0.95 | -0.23 -> -0.18 | unchanged |  |
| Q10 | Q10_mom_40_XS_0_as_M_h19_COM | 0.50 | +0.59 | +0.76 / 0.91 | +1.68 / 0.26 | -0.20 -> +0.87 | unchanged |  |
| Q2 | Q2_20_as_h19_CLS6 | 0.49 | +0.63 | +0.69 / 0.93 | +1.31 / 0.55 | -0.07 -> +0.55 | unchanged |  |
| Q5 | Q5_mom_25_XS_4_as_M_h19_MACRO12 | 0.50 | +1.63 | +0.84 / 1.00 | +1.36 / 0.98 | -0.10 -> +0.59 | unchanged | LEAD (Q5; Q5ENS ensemble) |
| Q8 | Q8_skew_120_XS_0_as_M_h19_ALL26 | 0.50 | +1.34 | +0.81 / 1.00 | +1.13 / 0.97 | -0.15 -> +0.50 | unchanged |  |
| Q8 | Q8_skew_60_XS_0_as_M_h19_ALL26 | 0.50 | +0.52 | +0.81 / 0.86 | +1.00 / 0.69 | -0.10 -> +0.29 | unchanged |  |
| Q9 | Q9_lowvol_20_XS_0_rev_M_h19_ALL26 | 0.50 | +1.38 | +0.67 / 1.00 | +1.14 / 1.00 | -0.18 -> +0.68 | unchanged | LEAD (Q9) |
| R1 | R1_60_3_h3_ALL26 | 0.50 | +0.89 | +0.52 / 0.99 | +0.34 / 1.00 | -0.47 -> -0.53 | unchanged |  |
| R1 | R1_60_3_h3_SCR | 0.50 | +1.09 | +0.66 / 1.00 | +0.65 / 1.00 | -0.14 -> -0.34 | unchanged |  |
| R1 | R1_60_6_h3_SCR | 0.46 | +0.54 | +0.73 / 0.91 | +0.77 / 0.90 | -0.09 -> -0.12 | unchanged |  |
| S3 | S3_60_1.25_h5_ALL26 | 0.55 | +0.55 | +0.64 / 0.95 | +0.81 / 0.86 | -0.18 -> +0.06 | unchanged |  |
| T6 | T6__h1_EQ | 0.54 | +0.79 | +0.87 / 0.94 | +0.85 / 0.92 | -0.09 -> -0.05 | unchanged |  |
| T6 | T6__h1_FX | 0.57 | +1.26 | +0.61 / 1.00 | +0.65 / 1.00 | -0.24 -> -0.22 | unchanged |  |
| V1 | V1_NQ_1.5_h1_ES | 0.47 | +0.49 | +0.05 / 1.00 | +0.10 / 0.99 | -0.79 -> -0.78 | unchanged |  |
| V10 | V10_('hi', 0.67)_h1_SCR | 0.50 | +0.50 | +0.91 / 0.80 | +0.79 / 0.88 | -0.05 -> -0.00 | unchanged |  |
| V10 | V10_('lo', 0.5)_h1_ALL26 | 0.52 | +0.76 | +0.49 / 0.97 | +0.61 / 0.98 | -0.25 -> -0.34 | unchanged |  |
| V3 | V3_('hi', 0.5)_h3_SCR | 0.52 | +0.68 | +0.84 / 0.91 | +0.74 / 0.95 | -0.03 -> -0.19 | unchanged |  |
| V3 | V3_('hi', 0.67)_h1_ALL26 | 0.53 | +1.02 | +0.50 / 1.00 | +0.57 / 1.00 | -0.32 -> -0.33 | unchanged |  |
| V3 | V3_('hi', 0.67)_h1_SCR | 0.54 | +1.02 | +0.73 / 1.00 | +0.88 / 0.98 | -0.11 -> -0.07 | unchanged |  |
| V4 | V4_0.5_against_h1_SCR | 0.58 | +0.93 | +0.84 / 0.97 | +0.71 / 0.98 | -0.05 -> -0.14 | unchanged |  |
| V4 | V4_0.5_against_h3_SCR | 0.58 | +0.88 | +0.82 / 0.96 | +0.62 / 0.99 | -0.01 -> -0.22 | unchanged |  |
| V4 | V4_0.5_with_h1_SCR | 0.56 | +0.33 | +0.72 / 0.83 | +0.94 / 0.73 | -0.09 -> -0.07 | unchanged |  |
| V5 | V5_20_rev_h10_EQ | 0.48 | +0.26 | +0.80 / 0.71 | +0.69 / 0.80 | -0.04 -> -0.22 | unchanged |  |
| V5 | V5_20_rev_h5_EQ | 0.49 | +0.46 | +0.89 / 0.84 | +0.77 / 0.86 | -0.03 -> -0.13 | unchanged |  |
| V5 | V5_5_rev_h10_EQ | 0.51 | +0.83 | +0.80 / 0.96 | +0.81 / 0.96 | -0.07 -> -0.09 | unchanged |  |
| V8 | V8_fade_h1_6E | 0.61 | +0.12 | +0.82 / 0.67 | +0.77 / 0.66 | -0.17 -> -0.15 | unchanged |  |
| V8 | V8_fade_h3_GC | 0.46 | +0.40 | +0.84 / 0.77 | +0.74 / 0.79 | +0.04 -> -0.10 | unchanged |  |
| W4 | W4_0_EQ_h1_EQ | 1.00 | +1.59 | +0.93 / 1.00 | +0.98 / 1.00 | -0.17 -> +0.25 | unchanged | NO (fails wd corr) |
| W4 | W4_4_EN_h1_EN | 0.00 | +0.29 | +0.76 / 0.81 | +0.46 / 0.91 | -0.23 -> -0.43 | unchanged |  |
| W4 | W4_4_FX_h1_FX | 0.00 | -0.13 | +0.06 / 0.89 | +0.39 / 0.72 | -0.87 -> -0.40 | unchanged |  |
| W6 | W6_0.5_h1_SCR | 0.57 | +0.88 | +0.71 / 0.98 | +0.81 / 0.97 | -0.12 -> -0.13 | unchanged |  |
| W8 | W8_10_1_h5_NQ | 0.47 | +0.31 | +0.87 / 0.71 | +0.78 / 0.79 | +0.06 -> -0.14 | unchanged |  |
| W8 | W8_10_1_h5_RTY | 0.41 | +0.51 | +0.70 / 0.90 | +0.77 / 0.86 | -0.10 -> -0.11 | unchanged |  |
| W8 | W8_20_-1_h5_NQ | 0.54 | -0.19 | +0.91 / 0.35 | +0.92 / 0.32 | +0.01 -> +0.05 | unchanged |  |
| Y10 | Y10_3.0_follow_h4_M6 | 0.47 | -0.20 | -1.01 / 1.00 | -0.87 / 1.00 | -1.89 -> -1.85 | unchanged |  |
| Y10 | Y10_3.0_follow_h8_M6 | 0.47 | +0.35 | -0.33 / 1.00 | -0.47 / 1.00 | -1.25 -> -1.30 | unchanged |  |
| Y2 | Y2_0.6_60_h5_SCR | 0.59 | -0.05 | +0.78 / 0.51 | +1.14 / 0.34 | -0.10 -> +0.17 | unchanged |  |
| Y5 | Y5_1.5_fade_h1_SCR | 0.53 | +0.09 | +0.35 / 0.88 | +0.28 / 0.90 | -0.60 -> -0.69 | unchanged |  |
| Z10 | Z10_1.3_20_h5_SCR | 0.57 | +0.08 | +0.77 / 0.67 | +1.27 / 0.29 | -0.23 -> +0.40 | unchanged |  |
| Z10 | Z10_1.3_5_h3_SCR | 0.52 | +0.19 | +0.68 / 0.75 | +0.98 / 0.49 | -0.20 -> +0.22 | unchanged |  |
| Z2 | Z2_IDw_h3_ALL26 | 0.49 | +0.22 | +0.49 / 0.83 | +0.94 / 0.64 | -0.36 -> +0.01 | unchanged |  |
| Z2 | Z2_IDw_h5_ALL26 | 0.49 | +0.28 | +0.65 / 0.84 | +0.96 / 0.68 | -0.16 -> +0.07 | unchanged |  |
| Z3 | Z3_fade_h1_SCR | 0.46 | +0.82 | +0.82 / 0.95 | +0.79 / 0.96 | -0.15 -> -0.18 | unchanged |  |
| Z3 | Z3_fade_h3_SCR | 0.46 | +0.91 | +0.68 / 0.98 | +0.71 / 0.98 | -0.18 -> -0.13 | unchanged |  |

## 3. The port (item 2) - how to use, past results unchanged
- ap_null_dm.py (new file, docstring has the recipe): side_counts(cnt,G) and job_null_dm(args) for the b2356 harness; usage end to end in ap_bl2_dm.py: x,nt,cnt = run_cell(c); sc = side_counts(cnt, G); draws = job_null_dm((c, sc, seed, 29, 1.0, G, BC, to_axis, FD)); compare ax.wsh(x,'pairwin') with the draws exactly as ap_b2356_pipe.null_summary. Nothing in ap_y_run / ap_b2356_pipe was modified, so all stored b2356 results are untouched.
- I-series (ap_i_fams.py; backup ap_i_fams.py.bak_pre_bl2): new module variable DM = None. Set ap_i_fams.DM = {name: (n_long, n_short)} (real sides in the pair window are captured automatically in fam._real_sides when fam.run is called without rng) and the random-entry draws of fam.run(..., rng=..., counts=...) take the real long/short mix instead of the candidate side. Default None reproduces the old behaviour exactly. ap_bl2_idm.py is the validation script: I4 (balanced): legacy rank 0.947 -> matched 0.927, p95 0.13 -> 0.18. I9, J4, K4 and the other long-only families (own run() methods: long entries only) were already side-matched by construction and need no change.
- ap_b_base pipelines (B, Q, SW, BI, BJ): ap_bj_pipe.py (matched null built in) for new runs; ap_bl_rescore.py for existing cells (BL1).

## 4. Flags for the coordinator (no LEDGER edit made)
1. Q5ENS (12-cell Q5 grid ensemble, LEAD 'hedge shift null 0.96 pass'): under the matched null Q5 k=4 holds (rank 0.98, real 1.63 vs p95 1.36), Q5 k=3 (0.92) and (30,2) (0.83) fail; the ensemble's null should be re-run as an ensemble with matched sides before its LEAD wording is kept. Q3 (252, 63) cells fail outright.
2. Q10 commodity momentum lead (COM 20-day): fails the matched null (real 1.25 vs p95 1.54).
3. Q9 ALL26 low-vol reversal lead: holds.
4. N3 (VX curve, long): NQ cell holds against the matched null, ES fails; the 'long NQ beta' reading on record stands.
5. No FOUND-PENDING status is affected (none in this set).

Files: code/census/night_ins/ap_null_dm.py, ap_bl2_dm.py, ap_bl2_idm.py, ap_i_fams.py (DM option); outputs/autopilot/b2356c/bl2_all.csv and <ID>_dm.csv.

DONE BL2
