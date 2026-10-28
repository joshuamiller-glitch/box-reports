# DS3_ASIM_FINAL - T-ASIM (Waqar Asim 1-min model) on NQ and 6E (D3CZ, 2026-10-28)

**Verdict: NQ 0 PASS / 0 CANDIDATE / 30 DEAD; 6E 0 PASS / 0 CANDIDATE / 30 DEAD. No spec. The model as written produces almost no trades once its HTF filters are applied, and the 1-minute setup alone has no net edge on NQ and a large negative one on 6E because its zones are 2-3 pips wide and cost is 0.57-0.71 R.**

Prereg: NQ sha256 9080983693a996074d7cbd8842b6123681f93ac49df56c61d7bd3e4e9c8e565a, 6E sha256 0a09800806571730a828c8851e1f4f47c4b359d3f4551eceae3955fbf53a81b1 (both in autopilot/DECISIONS.md before any P&L; 30 cells each, N_total 30). Pre-holdout texts l2vast/ds3/prereg/ASIM_{NQ,6E}_PREHOLD.md logged (tracks DS3_ASIM_NQ/6E and _SPAN2); HOLD (2025-07..2026-10-16) and X (2023-04..2024-01, second holdout) read once, after the log. UNTOUCHED never read. Code l2vast/ds3/code/asim/ (as_core numba engines, as_ctx HTF context, as_run, as_eval, as_gates, as_report, as_audit identity test, as_trunc as-of test); stored results out/asim/eval_{NQ,6E}.pkl.

## What was tested (one paragraph)
1H order-block zones (impulse >= 1.5/2 x ATR14(1H)), 15m trend = last BOS after a sweep, 15m premium/discount (12/24 bars), 1m BOS/MSB (L 3/5) + inducement sweep (1/2 ticks) + 1m OB or FVG retest, limit at the proximal edge or 50%, cancel 10/20 min or if > 50% of the way to the leg high is travelled, stop distal +0/+1 tick capped at 10/15/20 NQ pts (6/10/14 ticks = 3/5/7 pips on 6E), exits 50% 3R + 50% 10R / all 3R / all 5R with and without BE, windows 03-04 + 09-10 ET / London / NY / all hours, SMT (NQ-ES, 6E-6B), RSI divergence, first 15/30 min of the window. All fills are on 1-min bars, conservative (limit needs a 1-tick trade-through, stop first in a bar, targets need a print 1 tick through, stop/time exits slip 1 tick). Cost: NQ 4.84/lot RT (0.242 pt) + 1 tick on stop/time exits; 6E 5.30 RT (FEES.md addendum, exchange fee WEAK third-party) + 1 tick on every fill.

## Fees, 6B availability, NEEDS
6E: 5.30 USD RT = commission 0.59 + exchange/NFA 1.62 + clearing 0.19 + routing 0.25 per side; the 1.62 exchange+NFA is third-party (Topstep schedule), not confirmed by NT pages (WEAK). 6B: 1-min bars ARE on disk (/mnt/l2/rootmoves/data_autopilot/ohlcv1m/6B_2013..2026.dbn.zst, through 2026-10-16; daily outrights in data/t4) and were used here ONLY as the SMT partner series; FEES.md has NO 6B fee line (INSTRUMENT_COSTS.md uses the 4.84 PROXY-STD, not an NT/CME number), so 6B is not scored as a traded instrument. **NEEDS: one NinjaTrader statement round-trip line for 6B and for 6E (confirms the 1.62 exchange+NFA); nothing bought or downloaded.**

## Headline numbers
* Trade rate is the first result: the full HTF stack (1H OB overlap x 15m trend x premium/discount) leaves 82 filled NQ trades in 3.7 years (0.43/wk all hours, 0.01-0.05/wk in the model's own windows) and 30 on 6E. B0 (cell H01) has 1 NQ / 2 6E trades in WFPRE. The model's own windows cannot be evaluated; the cells that can be (>=30 trades) are the all-hours stack cells and the 1m-only cells.
* NQ 1m-only all hours (M04, 14.5 trades/wk, n=1,942 over WF): WFPRE mean R -0.006 (MDE 0.144), HOLD +0.112, X -0.054, cost2x -0.261. It beats the plain sweep-and-reclaim comparator (+0.274 R [0.170,0.367]) and the random-zone / timing / random-direction placebos (the placebos are biased negative, see below), but net mean R is not positive in WFPRE and not after 2x cost: DEAD on mean_up, beats_b (undefined for an all-hours window), cost2x, year_share, stack_add_pre, hold, span2.
* The median NQ stop is only ~4.5-5 pts (17-20 ticks), not the 15-pt cap: cost is 0.12 R, required win rate at 3R-all 27.9%; observed 26% (his window, 3R-all, n=202) vs required 27.9%; blended exit needs P(3R) = 26.4% and observes 25.9% (M01). So at 3R the model is at breakeven within noise (MDE 0.6 R at n~200); the question "is the observed rate above required" is: no, and not distinguishable from it. Not a single NQ cell has a 95% interval above zero.
* 6E: median stop 4 ticks (2 pips); cost 0.57-0.71 R; required win rate at 3R 39-43%; observed 8-9% (M04: 9.2%, mean R -0.82 WF). The 1-tick/side rule alone consumes about half of a 4-tick risk. Every 6E cell has negative WFPRE mean R (best -0.58 R); as a DS3 sleeve it adds negative Sharpe (M04 d_Sharpe -0.30 WFPRE, -0.20 HOLD, -0.46 X).
* Windows: no cell's real window beats the shifted-window draws with a CI above zero (placebo b effects 0.0-0.48 R with CIs spanning zero on NQ; the one 6E CI above zero is H02 with n=0 draws undefined): the 03-04 / 09-10 ET windows show no edge over other hours.
* Confluence columns (SMT, RSI divergence, first-15/30 min) reduce n below 30 or leave mean R unchanged; none is positive with a CI above zero.

## Reading the placebos
(a) random zones of the same width have a strongly negative mean R (-0.5 to -0.7 R NQ) because a randomly placed limit has a tight stop with no structural reason and a stop-first conservative fill bar; therefore 'beats_a' is passed by almost any cell and best_of_N (effect vs (a), prereg) is mostly non-binding; the gate that decides is mean_up/cost2x (absolute net). The absolute sign-flip best-of-N p95 of the best mean R over the 30 cells is 1.151 R (NQ) / 1.431 R (6E) against a best observed WFPRE mean of 0.384 R (H10, n=17) / -0.583 (6E). (b) is undefined for all-hours cells (draw = real, effect 0.000, counted as a failed gate, not softened). (c) timing-destroyed draws are about -0.1 to -0.4 R; (d) random direction is about -0.3 to -0.8 R on NQ: the structure carries information relative to random entries but not enough to cover cost.

## NQ

Tiers: {'DEAD': 30}. Best-of-N (effect vs placebo (a), N_total=30): null p95 0.546, best effect 0.956 (cell see table). Absolute sign-flip null p95 of the best WFPRE mean R over the cells: 1.151.

Per cell, sorted by WFPRE mean R (the first 10 rows are the top 10 regardless of verdict; MDE = 2.8 sd/sqrt(n) in R):

| cell | tier | WFPRE n | /wk | WR | mean R | MDE | HOLD n | HOLD mean R | X n | X mean R | cost2x mean R (pre) | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| H10_stack_all_ind1H | DEAD | 17 | 0.227 | 0.471 | 0.384 | 1.268 | 15 | 0.806 | 10 | -0.274 | 0.216 | min_n,beats_b,beats_c,vs_plain,year_share,stack_add_pre,hold,span2 |
| M19_1m_his_time15 | DEAD | 27 | 0.360 | 0.296 | 0.298 | 1.480 | 30 | -0.657 | 14 | -0.464 | 0.057 | min_n,beats_a,beats_b,beats_c,vs_plain,year_share,stack_add_pre,hold,span2 |
| H03_stack_ny | DEAD | 2 | 0.027 | 0.500 | 0.188 | 3.546 | 2 | -1.062 | 3 | -0.718 | 0.082 | min_n,beats_a,beats_b,beats_c,beats_beta,vs_plain,year_share,stack_add_pre,hold,span2 |
| H07_stack_all_noPD | DEAD | 45 | 0.600 | 0.356 | 0.141 | 0.836 | 34 | 0.453 | 41 | -0.201 | -0.035 | beats_b,beats_c,vs_plain,cost2x_pre,year_share,stack_add_pre,hold,span2 |
| M20_1m_his_time30 | DEAD | 58 | 0.773 | 0.259 | 0.081 | 0.916 | 51 | -0.283 | 29 | -0.526 | -0.144 | beats_b,beats_c,vs_plain,cost2x_pre,year_share,stack_add_pre,hold,span2 |
| M06_1m_his_all5R | DEAD | 109 | 1.453 | 0.193 | 0.079 | 0.640 | 92 | -0.065 | 68 | -0.153 | -0.139 | beats_b,beats_c,vs_plain,cost2x_pre,year_share,stack_add_pre,hold,span2 |
| M03_1m_ny | DEAD | 58 | 0.773 | 0.328 | 0.043 | 0.736 | 37 | 0.090 | 49 | -0.117 | -0.088 | beats_b,beats_c,vs_plain,cost2x_pre,year_share,stack_add_pre,hold,span2 |
| M13_1m_his_stop+1 | DEAD | 107 | 1.427 | 0.252 | 0.026 | 0.627 | 92 | -0.020 | 68 | -0.155 | -0.170 | beats_b,beats_c,vs_plain,cost2x_pre,stack_add_pre,hold,span2 |
| H04_stack_all | DEAD | 32 | 0.427 | 0.375 | 0.021 | 0.805 | 23 | 0.503 | 25 | 0.097 | -0.174 | beats_b,beats_c,vs_plain,cost2x_pre,year_share,stack_add_pre,hold,span2 |
| M04_1m_all | DEAD | 1088 | 14.507 | 0.365 | -0.006 | 0.144 | 854 | 0.112 | 659 | -0.054 | -0.261 | mean_up,beats_b,cost2x_pre,year_share,stack_add_pre,hold,span2 |
| M01_1m_his | DEAD | 109 | 1.453 | 0.257 | -0.007 | 0.618 | 92 | -0.043 | 68 | -0.183 | -0.225 | mean_up,beats_b,beats_c,vs_plain,cost2x_pre,year_share,stack_add_pre,hold,span2 |
| M14_1m_his_cap10 | DEAD | 101 | 1.347 | 0.267 | -0.009 | 0.639 | 78 | -0.050 | 65 | -0.144 | -0.239 | mean_up,beats_b,beats_c,vs_plain,cost2x_pre,stack_add_pre,hold,span2 |
| M12_1m_his_cancel10 | DEAD | 103 | 1.373 | 0.262 | -0.018 | 0.626 | 87 | -0.124 | 66 | -0.152 | -0.237 | mean_up,beats_b,beats_c,vs_plain,cost2x_pre,year_share,stack_add_pre,hold,span2 |
| M07_1m_his_noBE | DEAD | 109 | 1.453 | 0.275 | -0.025 | 0.619 | 92 | -0.081 | 68 | -0.220 | -0.243 | mean_up,beats_b,beats_c,vs_plain,cost2x_pre,year_share,stack_add_pre,hold,span2 |
| H06_stack_all_pd12 | DEAD | 30 | 0.400 | 0.367 | -0.028 | 0.847 | 30 | 0.227 | 28 | -0.086 | -0.214 | mean_up,beats_b,beats_c,beats_beta,vs_plain,cost2x_pre,year_share,stack_add_pre,hold,span2 |
| M15_1m_his_cap20 | DEAD | 113 | 1.507 | 0.248 | -0.034 | 0.598 | 97 | -0.011 | 68 | -0.183 | -0.246 | mean_up,beats_b,beats_c,vs_plain,cost2x_pre,year_share,stack_add_pre,hold,span2 |
| H09_stack_all_no1Hzone | DEAD | 287 | 3.827 | 0.376 | -0.044 | 0.271 | 217 | 0.276 | 170 | 0.040 | -0.315 | mean_up,beats_b,beats_c,cost2x_pre,year_share,stack_add_pre,hold |
| H08_stack_all_no15mtrend | DEAD | 63 | 0.840 | 0.349 | -0.054 | 0.558 | 42 | 0.653 | 48 | -0.249 | -0.282 | mean_up,beats_b,beats_c,vs_plain,cost2x_pre,stack_add_pre,best_of_N,hold,span2 |
| M05_1m_his_all3R | DEAD | 109 | 1.453 | 0.257 | -0.054 | 0.475 | 93 | 0.006 | 68 | -0.249 | -0.272 | mean_up,beats_b,beats_c,vs_plain,cost2x_pre,year_share,stack_add_pre,hold,span2 |
| M09_1m_his_ind2 | DEAD | 108 | 1.440 | 0.241 | -0.083 | 0.601 | 92 | -0.046 | 72 | -0.170 | -0.300 | mean_up,beats_b,beats_c,vs_plain,cost2x_pre,year_share,stack_add_pre,hold,span2 |
| M10_1m_his_entry50 | DEAD | 88 | 1.173 | 0.261 | -0.129 | 0.699 | 85 | -0.126 | 61 | 0.022 | -0.485 | mean_up,beats_b,beats_c,vs_plain,cost2x_pre,year_share,stack_add_pre,hold,span2 |
| M08_1m_his_L3 | DEAD | 134 | 1.787 | 0.231 | -0.186 | 0.458 | 149 | 0.144 | 117 | -0.096 | -0.372 | mean_up,beats_b,beats_c,vs_plain,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |
| M02_1m_london | DEAD | 166 | 2.213 | 0.205 | -0.238 | 0.426 | 137 | 0.032 | 87 | -0.339 | -0.512 | mean_up,beats_b,beats_c,vs_plain,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |
| H05_stack_all_imp2 | DEAD | 22 | 0.293 | 0.318 | -0.318 | 0.624 | 9 | -0.274 | 18 | 0.010 | -0.489 | min_n,mean_up,beats_a,beats_b,beats_c,vs_plain,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |
| M18_1m_his_rsi | DEAD | 3 | 0.040 | 0.333 | -0.423 | 1.889 | 5 | 0.802 | 2 | 2.621 | -0.570 | min_n,mean_up,beats_a,beats_b,beats_c,beats_beta,vs_plain,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |
| H02_stack_london | DEAD | 4 | 0.053 | 0.250 | -0.585 | 1.604 | 3 | 2.292 | 3 | -0.689 | -0.948 | min_n,mean_up,beats_a,beats_b,beats_c,beats_beta,vs_plain,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |
| M11_1m_his_fvg | DEAD | 67 | 0.893 | 0.179 | -0.617 | 0.600 | 63 | -0.089 | 47 | -0.676 | -1.081 | mean_up,beats_a,beats_b,beats_c,vs_plain,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |
| M17_1m_his_smt15 | DEAD | 16 | 0.213 | 0.188 | -0.632 | 0.607 | 17 | -0.285 | 17 | -0.430 | -0.934 | min_n,mean_up,beats_a,beats_b,beats_c,vs_plain,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |
| M16_1m_his_smt5 | DEAD | 23 | 0.307 | 0.130 | -0.891 | 0.451 | 19 | 0.330 | 20 | -0.407 | -1.238 | min_n,mean_up,beats_a,beats_b,beats_c,vs_plain,cost2x_pre,year_share,stack_add_pre,best_of_N,span2 |
| H01_stack_his | DEAD | 1 | 0.013 | 0.000 | -1.151 | n/a | 3 | 1.453 | 3 | -0.287 | -1.380 | min_n,mean_up,beats_a,beats_b,beats_c,beats_beta,vs_plain,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |

Placebo / comparator columns (WFPRE) for the top 10:

| cell | eff (a) random zones [CI] rank | eff (b) shuffled windows [CI] rank | eff (c) timing [CI] rank | eff (d) random dir [CI] rank | vs plain sweep-reclaim [CI] | draw means a/b/c/d |
|---|---|---|---|---|---|---|
| H10_stack_all_ind1H | 0.956 [0.198,2.038] 1.000 | 0.000 [-0.000,0.000] 0.000 | 0.647 [-0.192,1.764] 0.938 | 0.713 [0.337,1.185] 1.000 | 0.665 [-0.114,1.805] | -0.571/0.384/-0.262/-0.328 |
| M19_1m_his_time15 | 0.867 [-0.013,1.986] 1.000 | 0.478 [-0.458,1.633] 0.812 | 0.727 [-0.192,1.965] 1.000 | 1.085 [0.472,1.818] 1.000 | 0.537 [-0.385,1.722] | -0.569/-0.180/-0.429/-0.787 |
| H03_stack_ny | 0.685 [0.225,0.869] 0.938 | 0.167 [-0.413,0.787] 0.438 | 0.543 [-0.064,0.814] 0.812 | 0.300 [0.000,0.300] 0.438 | 0.424 [0.163,0.503] | -0.497/0.021/-0.356/-0.113 |
| H07_stack_all_noPD | 0.698 [0.193,1.262] 1.000 | 0.000 [-0.000,0.000] 0.000 | 0.296 [-0.298,0.914] 0.875 | 0.527 [0.180,0.889] 1.000 | 0.421 [-0.110,1.027] | -0.557/0.141/-0.156/-0.386 |
| M20_1m_his_time30 | 0.711 [0.162,1.343] 1.000 | 0.205 [-0.353,0.858] 0.812 | 0.186 [-0.397,0.894] 0.688 | 0.799 [0.296,1.300] 1.000 | 0.252 [-0.337,0.918] | -0.630/-0.124/-0.106/-0.718 |
| M06_1m_his_all5R | 0.751 [0.331,1.207] 1.000 | 0.134 [-0.280,0.658] 0.688 | 0.345 [-0.105,0.836] 1.000 | 0.901 [0.547,1.246] 1.000 | 0.268 [-0.180,0.745] | -0.672/-0.055/-0.266/-0.822 |
| M03_1m_ny | 0.722 [0.234,1.243] 1.000 | 0.039 [-0.434,0.618] 0.500 | 0.263 [-0.237,0.812] 0.875 | 0.804 [0.436,1.140] 1.000 | 0.279 [-0.220,0.814] | -0.679/0.004/-0.220/-0.761 |
| M13_1m_his_stop+1 | 0.657 [0.277,1.085] 1.000 | 0.036 [-0.320,0.541] 0.500 | 0.199 [-0.222,0.652] 0.875 | 0.745 [0.382,1.104] 1.000 | 0.181 [-0.229,0.649] | -0.630/-0.009/-0.172/-0.719 |
| H04_stack_all | 0.607 [0.109,1.266] 1.000 | 0.000 [-0.000,0.000] 0.000 | 0.233 [-0.336,0.918] 0.688 | 0.565 [0.257,0.955] 1.000 | 0.301 [-0.207,0.989] | -0.586/0.021/-0.212/-0.544 |
| M04_1m_all | 0.610 [0.515,0.695] 1.000 | 0.000 [-0.000,0.000] 0.000 | 0.169 [0.067,0.263] 1.000 | 0.423 [0.343,0.496] 1.000 | 0.274 [0.170,0.367] | -0.616/-0.006/-0.176/-0.429 |

Required-vs-observed win rate (the cost question; required WR at 3R-all = (1+c)/4, blended: P(3R) solving E[R]=0 given the empirical payoff when 3R is / is not reached; observed from the cell trades 2024-02..2026-10):

| cell | window | n (all windows WF) | median stop | cost in R (median) | required WR @3R-all | observed WR | observed share reaching 3R | observed share reaching 10R | required P(3R) blended exit | mean R WF |
|---|---|---|---|---|---|---|---|---|---|---|
| M04_1m_all | all | 1942 | 19.000 ticks | 0.116 | 0.279 | 0.377 | 0.157 | 0.042 | 0.146 | 0.046 |
| M01_1m_his | his | 201 | 20.000 ticks | 0.116 | 0.279 | 0.259 | 0.259 | 0.095 | 0.264 | -0.023 |
| M05_1m_his_all3R | his | 202 | 20.000 ticks | 0.116 | 0.279 | 0.262 | 0.262 | 0.000 | 0.273 | -0.026 |
| M06_1m_his_all5R | his | 201 | 20.000 ticks | 0.116 | 0.279 | 0.179 | 0.179 | 0.000 | 0.180 | 0.013 |
| H04_stack_all | all | 55 | 24.000 ticks | 0.086 | 0.271 | 0.436 | 0.218 | 0.055 | 0.122 | 0.223 |
| H09_stack_all_no1Hzone | all | 504 | 18.000 ticks | 0.123 | 0.281 | 0.395 | 0.173 | 0.046 | 0.146 | 0.094 |

Equal-risk (lots = clip(12000/(risk $),1,42)) added to the LIVE stack, additive, no lock engine (NQ); only cells with >=30 trades:

| cell | window | d_Sharpe | d_mean $/wk | CI d_mean | d_maxDD |
|---|---|---|---|---|---|
| H10_stack_all_ind1H | WFPRE | 0.009 | 374 | [-423,1450] | -10963 |
| H10_stack_all_ind1H | HOLD | 0.083 | 1500 | [-611,4941] | -16993 |
| H10_stack_all_ind1H | X | -0.023 | -368 | [-816,8] | -1897 |
| M19_1m_his_time15 | WFPRE | 0.038 | 728 | [-799,2365] | 9220 |
| M19_1m_his_time15 | HOLD | -0.088 | -1728 | [-2886,-435] | 1673 |
| M19_1m_his_time15 | X | -0.038 | -530 | [-1368,312] | 10263 |
| H07_stack_all_noPD | WFPRE | -0.013 | 473 | [-1235,2427] | -10963 |
| H07_stack_all_noPD | HOLD | 0.093 | 1448 | [-913,4961] | -18595 |
| H07_stack_all_noPD | X | -0.137 | -1898 | [-3350,-431] | -1897 |
| M20_1m_his_time30 | WFPRE | 0.022 | 450 | [-1479,2472] | 12041 |
| M20_1m_his_time30 | HOLD | -0.061 | -1014 | [-2755,860] | 1673 |
| M20_1m_his_time30 | X | -0.089 | -1184 | [-2105,-220] | 19896 |
| M06_1m_his_all5R | WFPRE | 0.037 | 458 | [-2417,3555] | 2033 |
| M06_1m_his_all5R | HOLD | 0.016 | 356 | [-3139,3915] | 9430 |
| M06_1m_his_all5R | X | -0.077 | -923 | [-3385,1789] | -10594 |
| M03_1m_ny | WFPRE | -0.006 | 42 | [-2270,3019] | 5519 |
| M03_1m_ny | HOLD | 0.022 | 260 | [-1856,2530] | -7265 |
| M03_1m_ny | X | -0.025 | -164 | [-3413,4052] | -33142 |
| M13_1m_his_stop+1 | WFPRE | 0.083 | 1491 | [-1808,5040] | -5425 |
| M13_1m_his_stop+1 | HOLD | 0.060 | 1060 | [-2331,4845] | 10060 |
| M13_1m_his_stop+1 | X | -0.068 | -866 | [-3497,2538] | 1376 |
| H04_stack_all | WFPRE | -0.027 | -249 | [-1306,971] | -10963 |
| H04_stack_all | HOLD | 0.085 | 1458 | [-828,5093] | -16993 |
| H04_stack_all | X | -0.078 | -1018 | [-2247,99] | -1897 |
| M04_1m_all | WFPRE | 0.001 | 2229 | [-5673,9770] | 95791 |
| M04_1m_all | HOLD | 0.347 | 4960 | [-2973,13044] | -74724 |
| M04_1m_all | X | -0.267 | -2447 | [-11469,7324] | -2380 |

### NQ appendix: all 30 cells, long/short and comparator (WFPRE | WF)

| cell | n WF | long n / mean R | short n / mean R | comparator n (WFPRE) / mean R | cell - comparator [CI] WFPRE | cell - comparator [CI] HOLD | cell - comparator [CI] X |
|---|---|---|---|---|---|---|---|
| H01_stack_his | 4 | 1 / -1.151 | 3 / 1.453 | 1872 / -0.178 | -0.973 [-1.036,0.227] | 1.644 [-0.916,6.716] | -0.003 [-1.039,1.034] |
| H02_stack_london | 7 | 4 / -0.508 | 3 / 2.190 | 2954 / -0.198 | -0.386 [-1.007,0.947] | 2.488 [-0.857,6.709] | -0.408 [-1.232,1.009] |
| H03_stack_ny | 4 | 0 / n/a | 4 / -0.437 | 1411 / -0.236 | 0.424 [0.163,0.503] | -0.791 [-0.902,0.320] | -0.621 [-1.065,0.156] |
| H04_stack_all | 55 | 16 / -0.325 | 39 / 0.448 | 21156 / -0.280 | 0.301 [-0.207,0.989] | 0.733 [-0.240,1.922] | 0.428 [-0.310,1.342] |
| H05_stack_all_imp2 | 31 | 8 / -0.655 | 23 / -0.183 | 21156 / -0.280 | -0.038 [-0.506,0.523] | -0.044 [-0.834,0.851] | 0.340 [-0.412,1.154] |
| H06_stack_all_pd12 | 60 | 21 / -0.347 | 39 / 0.340 | 21156 / -0.280 | 0.252 [-0.308,0.966] | 0.457 [-0.278,1.492] | 0.245 [-0.440,1.046] |
| H07_stack_all_noPD | 79 | 29 / 0.046 | 50 / 0.408 | 21156 / -0.280 | 0.421 [-0.110,1.027] | 0.683 [-0.034,1.567] | 0.130 [-0.336,0.665] |
| H08_stack_all_no15mtrend | 105 | 38 / 0.157 | 67 / 0.270 | 21156 / -0.280 | 0.227 [-0.125,0.626] | 0.883 [0.141,1.701] | 0.081 [-0.363,0.647] |
| H09_stack_all_no1Hzone | 504 | 200 / 0.138 | 304 / 0.065 | 21156 / -0.280 | 0.236 [0.037,0.449] | 0.506 [0.190,0.858] | 0.370 [0.105,0.655] |
| H10_stack_all_ind1H | 32 | 6 / -0.158 | 26 / 0.753 | 21156 / -0.280 | 0.665 [-0.114,1.805] | 1.036 [-0.371,2.636] | 0.057 [-0.698,1.149] |
| M01_1m_his | 201 | 113 / 0.001 | 88 / -0.054 | 1872 / -0.178 | 0.171 [-0.238,0.630] | 0.148 [-0.255,0.574] | 0.101 [-0.434,0.683] |
| M02_1m_london | 303 | 151 / -0.235 | 152 / 0.003 | 2954 / -0.198 | -0.039 [-0.311,0.260] | 0.228 [-0.110,0.594] | -0.058 [-0.537,0.539] |
| M03_1m_ny | 95 | 49 / 0.210 | 46 / -0.097 | 1411 / -0.236 | 0.279 [-0.220,0.814] | 0.361 [-0.210,1.048] | -0.020 [-0.565,0.516] |
| M04_1m_all | 1942 | 940 / 0.015 | 1002 / 0.074 | 21156 / -0.280 | 0.274 [0.170,0.367] | 0.342 [0.213,0.488] | 0.277 [0.153,0.405] |
| M05_1m_his_all3R | 202 | 113 / 0.053 | 89 / -0.128 | 1872 / -0.231 | 0.177 [-0.172,0.521] | 0.217 [-0.131,0.584] | 0.037 [-0.359,0.439] |
| M06_1m_his_all5R | 201 | 113 / 0.009 | 88 / 0.018 | 1872 / -0.189 | 0.268 [-0.180,0.745] | 0.109 [-0.272,0.503] | 0.100 [-0.416,0.627] |
| M07_1m_his_noBE | 201 | 113 / -0.035 | 88 / -0.070 | 1872 / -0.152 | 0.127 [-0.278,0.586] | 0.084 [-0.300,0.509] | 0.021 [-0.519,0.585] |
| M08_1m_his_L3 | 283 | 137 / 0.028 | 146 / -0.049 | 1872 / -0.178 | -0.008 [-0.303,0.324] | 0.335 [-0.052,0.752] | 0.188 [-0.188,0.607] |
| M09_1m_his_ind2 | 200 | 112 / -0.071 | 88 / -0.060 | 1795 / -0.164 | 0.081 [-0.319,0.510] | 0.134 [-0.270,0.575] | 0.088 [-0.407,0.632] |
| M10_1m_his_entry50 | 173 | 93 / -0.169 | 80 / -0.079 | 1872 / -0.178 | 0.049 [-0.443,0.605] | 0.065 [-0.424,0.561] | 0.306 [-0.314,0.923] |
| M11_1m_his_fvg | 130 | 68 / -0.375 | 62 / -0.346 | 1872 / -0.178 | -0.439 [-0.803,0.006] | 0.102 [-0.422,0.711] | -0.392 [-0.940,0.213] |
| M12_1m_his_cancel10 | 190 | 107 / -0.070 | 83 / -0.063 | 1872 / -0.178 | 0.160 [-0.264,0.636] | 0.067 [-0.314,0.496] | 0.132 [-0.411,0.709] |
| M13_1m_his_stop+1 | 199 | 111 / -0.036 | 88 / 0.057 | 1867 / -0.155 | 0.181 [-0.229,0.649] | 0.178 [-0.195,0.590] | 0.107 [-0.418,0.686] |
| M14_1m_his_cap10 | 179 | 104 / -0.035 | 75 / -0.016 | 1615 / -0.208 | 0.199 [-0.233,0.663] | 0.184 [-0.242,0.651] | 0.178 [-0.369,0.776] |
| M15_1m_his_cap20 | 210 | 118 / 0.008 | 92 / -0.064 | 2028 / -0.160 | 0.126 [-0.285,0.566] | 0.161 [-0.230,0.588] | 0.069 [-0.454,0.633] |
| M16_1m_his_smt5 | 42 | 26 / -0.820 | 16 / 0.444 | 1872 / -0.178 | -0.713 [-1.000,-0.355] | 0.521 [-0.758,1.950] | -0.124 [-0.813,0.880] |
| M17_1m_his_smt15 | 33 | 17 / -0.498 | 16 / -0.405 | 1872 / -0.178 | -0.454 [-0.875,0.040] | -0.094 [-0.925,1.107] | -0.147 [-0.863,0.939] |
| M18_1m_his_rsi | 8 | 5 / -0.327 | 3 / 1.459 | 1872 / -0.178 | -0.245 [-0.965,1.129] | 0.993 [-0.925,4.491] | 2.904 [-0.939,6.734] |
| M19_1m_his_time15 | 57 | 35 / 0.068 | 22 / -0.638 | 569 / -0.239 | 0.537 [-0.385,1.722] | -0.398 [-0.902,0.268] | -0.068 [-0.868,1.282] |
| M20_1m_his_time30 | 109 | 61 / 0.002 | 48 / -0.206 | 1069 / -0.171 | 0.252 [-0.337,0.918] | -0.054 [-0.528,0.478] | -0.138 [-0.627,0.533] |

## 6E

Tiers: {'DEAD': 30}. Best-of-N (effect vs placebo (a), N_total=30): null p95 0.474, best effect 0.653 (cell see table). Absolute sign-flip null p95 of the best WFPRE mean R over the cells: 1.431.

Per cell, sorted by WFPRE mean R (the first 10 rows are the top 10 regardless of verdict; MDE = 2.8 sd/sqrt(n) in R):

| cell | tier | WFPRE n | /wk | WR | mean R | MDE | HOLD n | HOLD mean R | X n | X mean R | cost2x mean R (pre) | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| M16_1m_his_smt5 | DEAD | 12 | 0.160 | 0.083 | -0.583 | 1.765 | 10 | -1.331 | 12 | -0.929 | -1.279 | min_n,mean_up,beats_a,beats_b,beats_c,beats_beta,vs_plain,cost2x_pre,year_share,stack_add_pre,hold,span2 |
| M19_1m_his_time15 | DEAD | 10 | 0.133 | 0.100 | -0.608 | 2.151 | 11 | -1.223 | 13 | -1.054 | -1.314 | min_n,mean_up,beats_a,beats_b,beats_c,beats_beta,vs_plain,cost2x_pre,year_share,stack_add_pre,hold,span2 |
| H09_stack_all_no1Hzone | DEAD | 93 | 1.240 | 0.097 | -0.708 | 0.492 | 92 | -0.698 | 63 | -0.934 | -1.334 | mean_up,beats_b,beats_c,beats_beta,vs_plain,cost2x_pre,year_share,stack_add_pre,hold,span2 |
| M07_1m_his_noBE | DEAD | 54 | 0.720 | 0.111 | -0.845 | 0.715 | 45 | -0.980 | 39 | -1.242 | -1.506 | mean_up,beats_a,beats_b,beats_c,beats_beta,vs_plain,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |
| M13_1m_his_stop+1 | DEAD | 77 | 1.027 | 0.065 | -0.865 | 0.494 | 76 | -0.863 | 48 | -0.773 | -1.498 | mean_up,beats_a,beats_b,beats_c,beats_beta,vs_plain,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |
| M04_1m_all | DEAD | 404 | 5.387 | 0.082 | -0.871 | 0.187 | 323 | -0.748 | 255 | -0.937 | -1.519 | mean_up,beats_b,beats_c,beats_beta,vs_plain,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |
| M08_1m_his_L3 | DEAD | 86 | 1.147 | 0.081 | -0.876 | 0.389 | 87 | -1.061 | 66 | -0.729 | -1.477 | mean_up,beats_b,beats_c,beats_beta,vs_plain,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |
| M15_1m_his_cap20 | DEAD | 57 | 0.760 | 0.053 | -0.881 | 0.549 | 46 | -0.856 | 39 | -1.151 | -1.519 | mean_up,beats_b,beats_c,beats_beta,vs_plain,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |
| M17_1m_his_smt15 | DEAD | 7 | 0.093 | 0.000 | -0.883 | 0.532 | 14 | -0.748 | 10 | -1.228 | -1.454 | min_n,mean_up,beats_a,beats_b,beats_c,beats_beta,vs_plain,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |
| M01_1m_his | DEAD | 54 | 0.720 | 0.056 | -0.883 | 0.578 | 45 | -0.867 | 39 | -1.151 | -1.544 | mean_up,beats_b,beats_c,beats_beta,vs_plain,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |
| M20_1m_his_time30 | DEAD | 22 | 0.293 | 0.045 | -0.894 | 0.984 | 19 | -1.271 | 19 | -0.919 | -1.586 | min_n,mean_up,beats_a,beats_b,beats_c,beats_beta,vs_plain,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |
| M09_1m_his_ind2 | DEAD | 56 | 0.747 | 0.071 | -0.897 | 0.566 | 46 | -0.890 | 42 | -1.170 | -1.583 | mean_up,beats_a,beats_b,beats_c,beats_beta,vs_plain,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |
| M11_1m_his_fvg | DEAD | 26 | 0.347 | 0.077 | -0.931 | 0.864 | 29 | -0.893 | 12 | -1.181 | -1.590 | min_n,mean_up,beats_a,beats_b,beats_c,beats_beta,vs_plain,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |
| M06_1m_his_all5R | DEAD | 54 | 0.720 | 0.037 | -0.966 | 0.466 | 45 | -1.034 | 39 | -1.100 | -1.627 | mean_up,beats_b,beats_c,beats_beta,vs_plain,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |
| M05_1m_his_all3R | DEAD | 54 | 0.720 | 0.056 | -0.985 | 0.388 | 45 | -0.811 | 39 | -1.074 | -1.645 | mean_up,beats_b,beats_c,beats_beta,vs_plain,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |
| M12_1m_his_cancel10 | DEAD | 44 | 0.587 | 0.045 | -0.991 | 0.530 | 42 | -0.930 | 33 | -1.190 | -1.658 | mean_up,beats_a,beats_b,beats_c,beats_beta,vs_plain,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |
| M03_1m_ny | DEAD | 64 | 0.853 | 0.062 | -0.998 | 0.390 | 73 | -0.811 | 43 | -0.961 | -1.551 | mean_up,beats_a,beats_b,beats_c,beats_beta,vs_plain,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |
| M02_1m_london | DEAD | 62 | 0.827 | 0.081 | -1.000 | 0.406 | 46 | -0.341 | 48 | -1.097 | -1.704 | mean_up,beats_b,beats_c,beats_beta,vs_plain,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |
| H05_stack_all_imp2 | DEAD | 4 | 0.053 | 0.000 | -1.065 | 0.539 | 6 | -0.938 | 2 | -1.693 | -1.729 | min_n,mean_up,beats_a,beats_b,beats_c,beats_beta,vs_plain,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |
| H08_stack_all_no15mtrend | DEAD | 24 | 0.320 | 0.042 | -1.099 | 0.368 | 20 | -0.666 | 9 | -1.037 | -1.767 | min_n,mean_up,beats_a,beats_b,beats_c,beats_beta,vs_plain,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |
| M10_1m_his_entry50 | DEAD | 14 | 0.187 | 0.071 | -1.100 | 0.556 | 7 | -0.879 | 13 | -0.518 | -1.725 | min_n,mean_up,beats_a,beats_b,beats_c,beats_beta,vs_plain,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |
| M14_1m_his_cap10 | DEAD | 46 | 0.613 | 0.022 | -1.102 | 0.486 | 43 | -0.968 | 34 | -1.188 | -1.822 | mean_up,beats_a,beats_b,beats_c,beats_beta,vs_plain,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |
| H06_stack_all_pd12 | DEAD | 12 | 0.160 | 0.000 | -1.218 | 0.289 | 13 | -0.579 | 7 | -0.828 | -1.871 | min_n,mean_up,beats_a,beats_b,beats_c,beats_beta,vs_plain,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |
| H04_stack_all | DEAD | 9 | 0.120 | 0.000 | -1.265 | 0.285 | 13 | -0.579 | 7 | -0.916 | -1.924 | min_n,mean_up,beats_a,beats_b,beats_c,beats_beta,vs_plain,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |
| H07_stack_all_noPD | DEAD | 18 | 0.240 | 0.000 | -1.278 | 0.228 | 18 | -0.827 | 12 | -0.301 | -1.969 | min_n,mean_up,beats_a,beats_b,beats_c,beats_beta,vs_plain,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |
| H10_stack_all_ind1H | DEAD | 4 | 0.053 | 0.000 | -1.311 | 0.343 | 2 | -0.786 | 3 | -1.252 | -2.046 | min_n,mean_up,beats_a,beats_b,beats_c,beats_beta,vs_plain,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |
| H01_stack_his | DEAD | 2 | 0.027 | 0.000 | -1.370 | 0.000 | 4 | 0.413 | 2 | 0.011 | -1.939 | min_n,mean_up,beats_a,beats_b,beats_c,beats_beta,vs_plain,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |
| H03_stack_ny | DEAD | 2 | 0.027 | 0.000 | -1.370 | 0.000 | 3 | -1.131 | 1 | -1.308 | -1.939 | min_n,mean_up,beats_a,beats_b,beats_c,beats_beta,vs_plain,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |
| M18_1m_his_rsi | DEAD | 3 | 0.040 | 0.000 | -1.431 | 0.086 | 2 | -1.370 | 5 | -1.385 | -2.096 | min_n,mean_up,beats_a,beats_b,beats_c,beats_beta,vs_plain,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |
| H02_stack_london | DEAD | 0 | n/a | n/a | n/a | n/a | 5 | 0.056 | 2 | -1.547 | n/a | min_n,mean_up,beats_a,beats_b,beats_c,beats_beta,vs_plain,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |

Placebo / comparator columns (WFPRE) for the top 10:

| cell | eff (a) random zones [CI] rank | eff (b) shuffled windows [CI] rank | eff (c) timing [CI] rank | eff (d) random dir [CI] rank | vs plain sweep-reclaim [CI] | draw means a/b/c/d |
|---|---|---|---|---|---|---|
| M16_1m_his_smt5 | 0.630 [-0.186,2.052] 1.000 | 0.316 [-0.538,1.745] 0.750 | -0.039 [-0.944,1.384] 0.688 | -0.593 [-1.706,0.543] 0.188 | 0.168 [-0.665,1.638] | -1.213/-0.899/-0.544/0.010 |
| M19_1m_his_time15 | 0.653 [-0.281,2.381] 1.000 | 0.401 [-0.517,2.024] 0.875 | 0.047 [-1.051,1.835] 0.625 | -0.073 [-1.578,1.159] 0.438 | 0.184 [-0.761,1.913] | -1.261/-1.009/-0.655/-0.535 |
| H09_stack_all_no1Hzone | 0.480 [0.166,0.851] 1.000 | 0.000 [-0.000,0.000] 0.000 | -0.006 [-0.352,0.397] 0.438 | -0.235 [-0.558,0.108] 0.125 | 0.068 [-0.255,0.458] | -1.188/-0.708/-0.702/-0.472 |
| M07_1m_his_noBE | 0.393 [-0.028,0.960] 1.000 | 0.023 [-0.362,0.551] 0.562 | -0.120 [-0.584,0.472] 0.375 | -0.671 [-1.234,-0.200] 0.000 | -0.122 [-0.574,0.496] | -1.239/-0.868/-0.725/-0.175 |
| M13_1m_his_stop+1 | 0.278 [-0.024,0.609] 1.000 | -0.057 [-0.386,0.274] 0.312 | -0.304 [-0.629,0.045] 0.000 | -0.287 [-0.586,-0.005] 0.000 | -0.273 [-0.616,0.084] | -1.143/-0.808/-0.561/-0.578 |
| M04_1m_all | 0.313 [0.190,0.440] 1.000 | 0.000 [-0.000,0.000] 0.000 | -0.165 [-0.307,-0.020] 0.000 | -0.374 [-0.503,-0.239] 0.000 | -0.096 [-0.221,0.040] | -1.184/-0.871/-0.705/-0.497 |
| M08_1m_his_L3 | 0.281 [0.006,0.579] 1.000 | -0.091 [-0.341,0.220] 0.438 | -0.254 [-0.541,0.073] 0.062 | -0.332 [-0.622,-0.054] 0.000 | -0.124 [-0.427,0.205] | -1.157/-0.785/-0.622/-0.544 |
| M15_1m_his_cap20 | 0.355 [0.045,0.815] 1.000 | -0.022 [-0.311,0.448] 0.438 | -0.205 [-0.573,0.282] 0.250 | -0.634 [-1.108,-0.227] 0.000 | -0.170 [-0.516,0.311] | -1.236/-0.859/-0.677/-0.247 |
| M17_1m_his_smt15 | 0.328 [-0.094,0.718] 0.938 | -0.182 [-0.772,0.329] 0.562 | -0.310 [-0.719,0.104] 0.375 | -0.973 [-2.400,0.150] 0.062 | -0.131 [-0.533,0.240] | -1.210/-0.700/-0.573/0.090 |
| M01_1m_his | 0.367 [0.034,0.841] 1.000 | -0.026 [-0.334,0.464] 0.438 | -0.174 [-0.538,0.347] 0.062 | -0.734 [-1.257,-0.294] 0.000 | -0.132 [-0.493,0.380] | -1.250/-0.857/-0.709/-0.149 |

Required-vs-observed win rate (the cost question; required WR at 3R-all = (1+c)/4, blended: P(3R) solving E[R]=0 given the empirical payoff when 3R is / is not reached; observed from the cell trades 2024-02..2026-10):

| cell | window | n (all windows WF) | median stop | cost in R (median) | required WR @3R-all | observed WR | observed share reaching 3R | observed share reaching 10R | required P(3R) blended exit | mean R WF |
|---|---|---|---|---|---|---|---|---|---|---|
| M04_1m_all | all | 727 | 4.000 ticks | 0.712 | 0.428 | 0.092 | 0.074 | 0.026 | 0.280 | -0.816 |
| M01_1m_his | his | 99 | 4.000 ticks | 0.570 | 0.392 | 0.081 | 0.081 | 0.030 | 0.314 | -0.876 |
| M05_1m_his_all3R | his | 99 | 4.000 ticks | 0.570 | 0.392 | 0.081 | 0.081 | 0.000 | 0.314 | -0.906 |
| M06_1m_his_all5R | his | 99 | 4.000 ticks | 0.570 | 0.392 | 0.030 | 0.030 | 0.000 | 0.202 | -0.997 |
| H04_stack_all | all | 22 | 4.500 ticks | 0.570 | 0.392 | 0.045 | 0.045 | 0.045 | 0.249 | -0.859 |
| H09_stack_all_no1Hzone | all | 185 | 4.000 ticks | 0.712 | 0.428 | 0.086 | 0.076 | 0.043 | 0.228 | -0.703 |

Equal-risk (lots = clip(12000/(risk $),1,42)) added to the LIVE stack, additive, no lock engine (6E as a potential DS3 sleeve); only cells with >=30 trades:

| cell | window | d_Sharpe | d_mean $/wk | CI d_mean | d_maxDD |
|---|---|---|---|---|---|
| M16_1m_his_smt5 | WFPRE | -0.005 | -74 | [-300,227] | 2545 |
| M16_1m_his_smt5 | HOLD | -0.012 | -222 | [-379,-94] | 0 |
| M16_1m_his_smt5 | X | -0.027 | -383 | [-618,-159] | 0 |
| M19_1m_his_time15 | WFPRE | -0.003 | -40 | [-267,272] | 2545 |
| M19_1m_his_time15 | HOLD | -0.009 | -217 | [-348,-94] | 0 |
| M19_1m_his_time15 | X | -0.029 | -400 | [-717,-131] | 3333 |
| H09_stack_all_no1Hzone | WFPRE | -0.051 | -808 | [-1581,130] | 5336 |
| H09_stack_all_no1Hzone | HOLD | -0.056 | -994 | [-1515,-387] | 2505 |
| H09_stack_all_no1Hzone | X | -0.111 | -1509 | [-2228,-753] | 6323 |
| M07_1m_his_noBE | WFPRE | -0.032 | -598 | [-1165,134] | 7476 |
| M07_1m_his_noBE | HOLD | -0.036 | -618 | [-1110,-80] | 0 |
| M07_1m_his_noBE | X | -0.101 | -1396 | [-1957,-900] | 3515 |
| M13_1m_his_stop+1 | WFPRE | -0.053 | -887 | [-1422,-155] | 9194 |
| M13_1m_his_stop+1 | HOLD | -0.058 | -1030 | [-1620,-432] | 1718 |
| M13_1m_his_stop+1 | X | -0.094 | -1269 | [-2051,-396] | 6928 |
| M04_1m_all | WFPRE | -0.304 | -5383 | [-6636,-4107] | 45352 |
| M04_1m_all | HOLD | -0.204 | -3912 | [-4888,-2881] | 10586 |
| M04_1m_all | X | -0.460 | -6460 | [-7717,-5102] | 45300 |
| M08_1m_his_L3 | WFPRE | -0.071 | -1319 | [-1764,-881] | 7596 |
| M08_1m_his_L3 | HOLD | -0.087 | -1597 | [-2117,-978] | 6101 |
| M08_1m_his_L3 | X | -0.102 | -1214 | [-2220,-70] | 17149 |
| M15_1m_his_cap20 | WFPRE | -0.040 | -699 | [-1203,-28] | 12201 |
| M15_1m_his_cap20 | HOLD | -0.034 | -566 | [-1025,-83] | 0 |
| M15_1m_his_cap20 | X | -0.097 | -1319 | [-1850,-820] | 6140 |
| M17_1m_his_smt15 | WFPRE | -0.006 | -108 | [-200,-33] | 485 |
| M17_1m_his_smt15 | HOLD | -0.011 | -127 | [-401,228] | 0 |
| M17_1m_his_smt15 | X | -0.031 | -409 | [-654,-186] | 1798 |
| M01_1m_his | WFPRE | -0.034 | -596 | [-1095,66] | 12201 |
| M01_1m_his | HOLD | -0.033 | -547 | [-1010,-45] | 0 |
| M01_1m_his | X | -0.097 | -1319 | [-1850,-820] | 6140 |

### 6E appendix: all 30 cells, long/short and comparator (WFPRE | WF)

| cell | n WF | long n / mean R | short n / mean R | comparator n (WFPRE) / mean R | cell - comparator [CI] WFPRE | cell - comparator [CI] HOLD | cell - comparator [CI] X |
|---|---|---|---|---|---|---|---|
| H01_stack_his | 6 | 3 / 1.120 | 3 / -1.483 | 1120 / -0.751 | -0.618 [-0.709,0.795] | 1.106 [-0.918,6.862] | 0.666 [-0.584,1.918] |
| H02_stack_london | 5 | 3 / 1.120 | 2 / -1.539 | 1530 / -0.703 | n/a [0.629,0.773] | 0.838 [-0.815,6.938] | -0.835 [-1.263,0.763] |
| H03_stack_ny | 5 | 3 / -1.151 | 2 / -1.339 | 1105 / -0.712 | -0.658 [-0.737,0.738] | -0.461 [-0.834,0.667] | -0.715 [-0.814,0.667] |
| H04_stack_all | 22 | 14 / -0.756 | 8 / -1.041 | 8378 / -0.775 | -0.489 [-0.661,-0.264] | 0.195 [-0.621,1.318] | -0.154 [-0.841,0.442] |
| H05_stack_all_imp2 | 10 | 5 / -1.220 | 5 / -0.757 | 8378 / -0.775 | -0.289 [-0.607,0.216] | -0.165 [-0.626,0.521] | -0.931 [-1.184,0.789] |
| H06_stack_all_pd12 | 25 | 15 / -0.736 | 10 / -1.110 | 8378 / -0.775 | -0.443 [-0.634,-0.210] | 0.195 [-0.621,1.318] | -0.066 [-0.612,0.468] |
| H07_stack_all_noPD | 36 | 21 / -0.966 | 15 / -1.175 | 8378 / -0.775 | -0.503 [-0.652,-0.324] | -0.054 [-0.654,0.817] | 0.461 [-0.555,2.150] |
| H08_stack_all_no15mtrend | 44 | 24 / -0.758 | 20 / -1.076 | 8378 / -0.775 | -0.324 [-0.557,-0.054] | 0.107 [-0.504,0.906] | -0.275 [-0.790,0.248] |
| H09_stack_all_no1Hzone | 185 | 106 / -0.638 | 79 / -0.790 | 8378 / -0.775 | 0.068 [-0.255,0.458] | 0.075 [-0.197,0.401] | -0.172 [-0.437,0.174] |
| H10_stack_all_ind1H | 6 | 6 / -1.136 | 0 / n/a | 8378 / -0.775 | -0.535 [-0.702,-0.166] | -0.013 [-0.201,0.790] | -0.490 [-1.172,0.765] |
| M01_1m_his | 99 | 48 / -0.855 | 51 / -0.895 | 1120 / -0.751 | -0.132 [-0.493,0.380] | -0.174 [-0.506,0.331] | -0.496 [-0.714,-0.245] |
| M02_1m_london | 108 | 52 / -0.661 | 56 / -0.773 | 1530 / -0.703 | -0.297 [-0.547,0.015] | 0.441 [-0.082,1.073] | -0.386 [-0.603,-0.136] |
| M03_1m_ny | 137 | 72 / -0.921 | 65 / -0.874 | 1105 / -0.712 | -0.286 [-0.523,-0.019] | -0.142 [-0.419,0.178] | -0.369 [-0.660,0.003] |
| M04_1m_all | 727 | 366 / -0.795 | 361 / -0.837 | 8378 / -0.775 | -0.096 [-0.221,0.040] | 0.026 [-0.120,0.187] | -0.174 [-0.288,-0.047] |
| M05_1m_his_all3R | 99 | 48 / -0.938 | 51 / -0.875 | 1120 / -0.747 | -0.238 [-0.496,0.091] | -0.127 [-0.477,0.372] | -0.382 [-0.649,-0.035] |
| M06_1m_his_all5R | 99 | 48 / -0.980 | 51 / -1.013 | 1120 / -0.720 | -0.246 [-0.547,0.168] | -0.379 [-0.614,0.013] | -0.429 [-0.700,-0.035] |
| M07_1m_his_noBE | 99 | 48 / -0.699 | 51 / -1.102 | 1120 / -0.723 | -0.122 [-0.574,0.496] | -0.294 [-0.639,0.243] | -0.508 [-0.709,-0.276] |
| M08_1m_his_L3 | 173 | 86 / -0.934 | 87 / -1.003 | 1120 / -0.751 | -0.124 [-0.427,0.205] | -0.368 [-0.563,-0.103] | -0.075 [-0.461,0.365] |
| M09_1m_his_ind2 | 102 | 51 / -0.916 | 51 / -0.872 | 805 / -0.659 | -0.238 [-0.592,0.270] | -0.283 [-0.612,0.214] | -0.614 [-0.842,-0.367] |
| M10_1m_his_entry50 | 21 | 7 / -1.331 | 14 / -0.874 | 1120 / -0.751 | -0.349 [-0.676,0.082] | -0.186 [-0.797,0.590] | 0.137 [-0.805,1.681] |
| M11_1m_his_fvg | 55 | 21 / -0.430 | 34 / -1.208 | 1120 / -0.751 | -0.180 [-0.646,0.489] | -0.199 [-0.627,0.316] | -0.526 [-0.863,-0.104] |
| M12_1m_his_cancel10 | 86 | 42 / -0.848 | 44 / -1.069 | 1120 / -0.751 | -0.239 [-0.557,0.236] | -0.237 [-0.574,0.296] | -0.535 [-0.740,-0.284] |
| M13_1m_his_stop+1 | 153 | 80 / -0.921 | 73 / -0.802 | 1066 / -0.592 | -0.273 [-0.616,0.084] | -0.341 [-0.613,0.058] | -0.231 [-0.598,0.253] |
| M14_1m_his_cap10 | 89 | 46 / -0.895 | 43 / -1.189 | 672 / -0.889 | -0.213 [-0.507,0.234] | -0.130 [-0.462,0.390] | -0.376 [-0.640,-0.081] |
| M15_1m_his_cap20 | 103 | 49 / -0.861 | 54 / -0.878 | 1208 / -0.711 | -0.170 [-0.516,0.311] | -0.177 [-0.507,0.318] | -0.548 [-0.772,-0.295] |
| M16_1m_his_smt5 | 22 | 10 / -0.663 | 12 / -1.141 | 1120 / -0.751 | 0.168 [-0.665,1.638] | -0.638 [-0.832,-0.324] | -0.274 [-0.652,0.174] |
| M17_1m_his_smt15 | 21 | 10 / -0.587 | 11 / -0.980 | 1120 / -0.751 | -0.131 [-0.533,0.240] | -0.055 [-0.773,1.428] | -0.573 [-0.773,-0.376] |
| M18_1m_his_rsi | 5 | 1 / -1.370 | 4 / -1.416 | 1120 / -0.751 | -0.680 [-0.777,0.777] | -0.676 [-0.760,0.745] | -0.730 [-0.874,-0.557] |
| M19_1m_his_time15 | 21 | 11 / -0.604 | 10 / -1.289 | 287 / -0.792 | 0.184 [-0.761,1.913] | -0.490 [-0.744,-0.243] | -0.480 [-0.953,0.132] |
| M20_1m_his_time30 | 41 | 21 / -0.895 | 20 / -1.251 | 554 / -0.736 | -0.157 [-0.679,0.677] | -0.624 [-0.811,-0.403] | -0.320 [-0.719,0.175] |

## Deviations and caveats
* Own 1-min bar simulator (not corepool; no tape for 6E; NQ also on bars for like-for-like). Limit semantics: fill = min(limit, bar open) + entry slip. A first run filled at the limit even when the bar opened below it; this created a placebo-(a) artifact and was fixed for all cells and placebos before any gate was finalised (DECISIONS.md amendment; the first run's pre numbers had been seen, no cell/gate/threshold changed). Engine identity vs an independent python re-implementation: 19,600 setups, 0 mismatches; as-of truncation audit: 96 comparisons, 0 mismatches.
* My readings: the 50%-of-range invalidation = cancel a pending order once price has travelled > 50% of the way from the edge to the leg high without filling; 1H zone overlap uses [min(leg low, 1m zone low), 1m zone high]; 48-h zone life; SMT = exactly one of the pair makes a new 5/15-min extreme vs the previous 30 min; BE = stop to entry after a confirmed fractal(3) swing high above the entry.
* The comparator is not sequenced and unpaired (difference of means with week-block bootstrap), and placebos (c)(d) are not sequenced.
* Stack lines are additive daily equal-risk $ without the lock engine; only cells with >= 30 trades have one.
* Small samples: all stacked cells are underpowered by construction (MDE columns).
