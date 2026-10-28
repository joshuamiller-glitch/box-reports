# DS3 T-STRUCT-BRACKET (D3SB) final
Generated 2026-10-28T03:49:50Z. Research only; no live/execution/chart change. Directive autopilot/DIRECTIVE_STRUCTBRACKET.md. Code l2vast/ds3/code/sb/ (sb_lib.py runner + levels, sb_cell.py cell/placebo evaluation, sb_cells.py grids, sb_prereg.py, sb_run.py, sb_report.py, sb_final.py); preregs l2vast/ds3/prereg/SB_SB1..SB10.md (sha256 prefixes: SB1 13ab39480dec, SB2 9db497788b17, SB3 22b8b69d145e, SB4 d68a191252e0, SB5 874158ec19d9, SB6 8bd4a4d87627, SB7 97b38e6b6169, SB8 fcfb6829189d, SB9 b487b7224d88, SB10 5a38d742b3c5; full hashes in DECISIONS.md); results out/SB/ (res_*.pkl, per-cell trades_*.parquet, final_full.pkl, identity_audit.json, equal_risk_SB.json); PREHOLD texts autopilot/DS3_SB_SB*_PREHOLD.md (10 logged looks + 10 second-holdout looks).

## 1. Verdict
**Structure brackets do not beat the fixed 60/60 on identical signals: 300 cells (10 preregs x 30; SB1-SB5 = ST, HM, KB, SM, EM with the same 30-cell grid; SB6 = 10 key cells on PB3B_R5_P1 / PB3B_R60_P2 / PRO2_ER4_EMA5; SB7-SB10 = remaining stop/buffer, target and combination cells on ST and KB), 0 PASS, 0 CANDIDATE, 300 DEAD.** Conservative basis (no stop-join credit), equal-risk lots (risk = 10 lots x 60 pts, cap 42), paired per trade vs the fixed bracket on the same valid signals.
- Mean paired effect over 299 scored cells -1.51 pts/trade (median -1.40); 2 cells have a paired CI above 0 and 115 below 0. Positive paired effect and positive HOLD: 38 cells; also positive 2023-04..2024-01: 16.
- STOPS: every structure stop (signal-bar extreme, 3/5/8-bar swing, higher-low, VWAP, prior-session extreme, any buffer 0/5/10 pts or 0.5/1.0 ATR) is paired-negative or neutral vs the fixed 60 stop: mean -1.45 pts/trade over 137 stop cells (9% positive). The fixed-lots comparison (the same stop at 10 lots) loses less per trade (-0.4) because it risks less on tight stops, not because the stop is better. Wider buffers lose less (5-bar swing +1 ATR -0.4 vs +5 pts -1.4): the stop converges to the fixed 60.
- TARGETS (stop 60): near-structure targets lose (nearest swing, opening range, VWAP sigma, value area, opposite range boundary: mean -2.0 to -4.0 over the five families), distant targets are neutral to positive (prior-session H/L +1.6 mean over five families, 5/5 positive; fib 1.618/2.618 +0.2..+0.3; two cells on KB have a paired CI above 0, see section 5) but none survives placebo, the second holdout and the best-of-N null.
- DYNAMIC EXITS: trail to each new swing and exit on the opposite structure break are the worst (-2.31 pts/trade): the break exit gives back the 60-pt winners early (-3.5 mean over families).
- Hurdle: observed win rate minus the required win rate (1/(1+R)) has median -0.008 over 299 cells (range -0.103 to +0.037); the structure stops tighten the stop and raise the lots without moving the observed win rate above the break-even line.
- Execution flag: share of stops < 8 pts (P9 stop-join band) is 0 in every cell by construction (minimum stop 15); stops < 20 pts are 8% of trades on average (execution-sensitive, mapped credit NOT given).

## 2. Top 10 by paired WF effect vs the fixed 60/60 (regardless of verdict; failed gates and MDE shown)
| cell | verdict | failed gates | tr/wk WF | paired WF pts vs fixed 60/60 [CI] (MDE, pairs) | $/trade | vs placebo (b) pts | placebo ranks PRE a/b/c ; WF beta-d | paired HOLD | paired 2023 | WF wk $ cell vs ctl (SD, maxDD) | x2-cost WF d$/wk | stop/tgt mean | lots | win obs vs req | DS3 stack WF d mean $ / d Sharpe / d maxDD |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| SB_KB_tg_pd | DEAD | placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,maxDD_not_worse(full sequence),SPAN2<=0,beats_(b)_CI_includes_0,best_of_N_all180 | +16.9 | +5.00 [+0.81,+9.08] (MDE 6.43, n 2412) | +1,001 | +2.90 | +0.62/+0.94/+0.12 ; +1.00 | +6.56 | -1.92 | 6,603 vs 6,420 (SD 53,280 vs 48,085; maxDD 363,018 vs 328,302) | +7,905 | 60/302 | 10.0 | 0.34 vs 0.31 @ R 2.18 | +7,337 / +0.03 / +103,251 |
| SB_ER4_tg_vp1 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,placebo<0.95,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | +2.3 | +4.21 [-1.03,+9.77] (MDE 7.60, n 260) | +841 | +2.00 | +1.00/+0.94/+1.00 ; +1.00 | +3.50 | +7.55 | 281 vs -1,340 (SD 11,245 vs 16,522; maxDD 88,637 vs 257,649) | +1,436 | 60/40 | 10.0 | 0.67 vs 0.66 @ R 0.52 | +235 / -0.00 / -210 |
| SB_ER4_dy_trail | DEAD | holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | +2.6 | +3.56 [-8.52,+16.29] (MDE 17.96, n 290) | +713 | -5.64 | +1.00/+0.25/+1.00 ; +0.56 | -4.10 | -14.41 | -2,070 vs -1,818 (SD 21,172 vs 17,148; maxDD 427,197 vs 349,009) | +294 | 33/nan | 23.6 | 0.29 vs 0.27 @ R 2.68 | -2,802 / -0.23 / +2,167 |
| SB_KB_tg_fib2618 | DEAD | neighbours_agree,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | +29.4 | +3.30 [+0.66,+5.92] (MDE 3.70, n 4201) | +660 | +1.81 | +1.00/+1.00/+1.00 ; +1.00 | +1.79 | +0.37 | 13,969 vs 10,297 (SD 53,019 vs 53,196; maxDD 357,080 vs 402,342) | +13,050 | 60/156 | 10.0 | 0.39 vs 0.36 @ R 1.74 | +14,574 / +0.23 / +167,005 |
| SB_ER4_dy_brk | DEAD | holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | +2.6 | +3.20 [-8.73,+15.57] (MDE 17.85, n 287) | +640 | -5.64 | +1.00/+0.31/+1.00 ; +0.69 | -5.12 | -19.43 | -1,925 vs -1,818 (SD 20,920 vs 17,148; maxDD 405,705 vs 349,009) | -3 | 33/nan | 23.5 | 0.28 vs 0.27 @ R 2.70 | -2,461 / -0.22 / +1,249 |
| SB_PBR5_P1_tg_pd | DEAD | placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | +16.6 | +2.16 [-1.63,+6.11] (MDE 5.69, n 2369) | +433 | +1.08 | +0.44/+0.69/+0.00 ; +0.94 | +2.78 | -1.98 | 2,477 vs 372 (SD 47,807 vs 46,261; maxDD 352,295 vs 497,615) | +8,562 | 60/264 | 10.0 | 0.36 vs 0.34 @ R 1.91 | +1,937 / -0.20 / +136,720 |
| SB_KB8_cb_sw5_pd | DEAD | placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | +16.0 | +2.03 [-2.71,+6.68] (MDE 6.40, n 2290) | +406 | +0.79 | +0.94/+0.56/+0.19 ; +1.00 | +3.39 | -4.35 | 3,927 vs 8,048 (SD 55,567 vs 48,070; maxDD 380,733 vs 306,685) | +1,247 | 52/272 | 15.4 | 0.31 vs 0.29 @ R 2.46 | +4,394 / -0.14 / +111,284 |
| SB_KB_tg_rh2 | DEAD | placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | +25.9 | +1.74 [-0.93,+4.39] (MDE 3.77, n 3704) | +348 | +0.11 | +0.81/+0.81/+0.06 ; +0.94 | +0.84 | -1.41 | 13,791 vs 11,010 (SD 54,624 vs 53,230; maxDD 324,625 vs 305,765) | +9,669 | 60/210 | 10.0 | 0.33 vs 0.32 @ R 2.15 | +14,482 / +0.29 / +133,535 |
| SB_EM_tg_on | DEAD | placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | +3.5 | +1.59 [-2.15,+5.58] (MDE 5.85, n 477) | +318 | +0.58 | n/a/+0.38/n/a ; n/a | +3.20 | +4.78 | 422 vs -279 (SD 23,432 vs 18,582; maxDD 259,958 vs 310,361) | +924 | 60/104 | 10.0 | 0.49 vs 0.48 @ R 1.08 | +457 / -0.07 / +28,361 |
| SB_KB8_cb_hl_pd | DEAD | placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | +17.2 | +1.49 [-3.64,+6.23] (MDE 6.97, n 2453) | +297 | +1.33 | +0.81/+0.88/+0.25 ; +0.88 | +0.71 | -10.83 | 6,407 vs 8,569 (SD 53,973 vs 47,497; maxDD 474,547 vs 347,365) | +4,173 | 43/284 | 18.2 | 0.27 vs 0.25 @ R 3.07 | +6,400 / +0.06 / +107,753 |

(WF = 2024-02..2026-10; PRE ranks are the selection-window placebo ranks (a) timing-destroyed, (b) random structure, (c) random-in-regime, WF beta-d rank = real standalone mean vs random-direction bracket; (a),(c),(d) were run only when the PRE paired effect was > 0.)

## 3. Cross-family consistency (paired WF pts/trade, SB1-SB5 grid; the same signal logic on five entry families)
| cell type (SB1-SB5 grid) | ST | HM | KB | SM | EM | mean | n positive |
|--|--|--|--|--|--|--|--|
| dy_brk | -2.60 | -2.54 | -2.88 | -4.48 | -4.91 | -3.48 | 0 |
| dy_trail | -0.85 | -0.76 | -2.08 | -2.77 | -3.82 | -2.06 | 0 |
| dy_trail_u1 | -3.31 | -2.91 | -2.96 | -5.73 | -4.96 | -3.97 | 0 |
| dy_u1 | -3.26 | -2.76 | -3.34 | -5.19 | -4.75 | -3.86 | 0 |
| dy_u2 | -2.57 | -0.28 | -2.35 | +0.19 | -1.17 | -1.24 | 1 |
| st_hl_5 | -1.80 | +0.31 | -2.04 | +0.63 | -0.80 | -0.74 | 2 |
| st_psl_10 | -1.55 | +0.64 | -0.69 | -1.74 | -1.26 | -0.92 | 1 |
| st_sig0 | -0.20 | -0.75 | -0.70 | -0.67 | -2.64 | -0.99 | 0 |
| st_sig5 | -2.64 | -1.33 | -2.19 | -0.15 | +0.13 | -1.24 | 1 |
| st_sw3_5 | -1.94 | -0.68 | -2.10 | -0.15 | -2.71 | -1.52 | 0 |
| st_sw5_10 | -1.09 | -0.01 | -1.26 | -0.70 | -1.08 | -0.83 | 0 |
| st_sw5_5 | -2.03 | -0.56 | -1.87 | +0.18 | -2.74 | -1.41 | 1 |
| st_sw5_5_fix | -1.08 | +0.07 | -0.57 | -0.14 | -0.33 | -0.41 | 1 |
| st_sw5_5_m20 | -2.04 | -0.52 | -1.95 | -0.27 | -1.68 | -1.29 | 0 |
| st_sw5_a05 | -1.63 | -0.65 | -1.67 | -0.19 | -1.05 | -1.04 | 0 |
| st_sw5_a10 | -1.16 | +0.06 | -1.15 | +0.14 | +0.19 | -0.38 | 3 |
| st_sw8_5 | -2.03 | -1.22 | -1.40 | +0.40 | -0.77 | -1.01 | 1 |
| st_vw_5 | -1.15 | -0.90 | -1.19 | -2.41 | -0.51 | -1.23 | 0 |
| tg_fib10 | +0.18 | -0.50 | +0.62 | -1.03 | +0.42 | -0.06 | 3 |
| tg_fib1618 | +0.49 | -0.43 | +0.42 | -0.18 | +1.25 | +0.31 | 3 |
| tg_fib2618 | +0.54 | -0.24 | +3.30 | -2.16 | -0.44 | +0.20 | 2 |
| tg_on | -0.61 | -3.96 | -0.57 | -2.97 | +1.59 | -1.30 | 1 |
| tg_or | -3.05 | -4.09 | -2.39 | -6.82 | -3.57 | -3.99 | 0 |
| tg_pd | +0.90 | +0.95 | +5.00 | +0.26 | +0.69 | +1.56 | 5 |
| tg_rh2 | -0.41 | -0.27 | +1.74 | -1.87 | +0.27 | -0.11 | 2 |
| tg_ropp | -1.98 | -3.20 | -2.65 | -2.60 | -3.24 | -2.74 | 0 |
| tg_sw1 | -1.53 | -1.76 | -1.40 | -2.62 | -2.60 | -1.98 | 0 |
| tg_va | -2.18 | -2.74 | -1.87 | -4.18 | -2.20 | -2.63 | 0 |
| tg_vp1 | -0.53 | -1.44 | -0.86 | -2.85 | -4.79 | -2.09 | 0 |
| tg_vp2 | -1.04 | -2.02 | -0.39 | -4.04 | -2.30 | -1.96 | 0 |

| cell type (SB7/SB8 grids) | ST | KB |
|--|--|--|
| cb_hl_fib1618 | -2.44 | -2.03 |
| cb_hl_pd | -1.73 | +1.49 |
| cb_hl_u1 | -2.94 | -3.12 |
| cb_sig5_fib10 | -2.42 | -1.12 |
| cb_sig5_sw1 | -6.58 | -4.34 |
| cb_sig5_u1 | -5.34 | -4.71 |
| cb_sw5_fib10 | -1.85 | -1.73 |
| cb_sw5_fib1618 | -1.91 | -2.48 |
| cb_sw5_hvn | -1.09 | -2.96 |
| cb_sw5_on | +1.09 | -2.19 |
| cb_sw5_or | -2.73 | -4.69 |
| cb_sw5_pd | -0.24 | +2.03 |
| cb_sw5_rh2 | -1.24 | +0.32 |
| cb_sw5_ropp | -4.85 | -3.57 |
| cb_sw5_sw1 | -3.65 | -2.66 |
| cb_sw5_va | -3.05 | -2.11 |
| cb_sw5_vp1 | -1.38 | -1.01 |
| cb_sw5_vp2 | -4.33 | -2.73 |
| dy_brk_sig5 | -1.36 | -2.49 |
| dy_trail_hl5 | -0.73 | -1.60 |
| dy_trail_sig5 | -0.55 | -0.97 |
| dy_trail_sw8 | -1.17 | -1.88 |
| st_hl_0 | -1.48 | -1.26 |
| st_hl_05a | -1.61 | -0.96 |
| st_hl_10 | -0.87 | -1.31 |
| st_hl_5_r1 | -3.40 | -2.19 |
| st_psl_0 | -2.27 | -0.87 |
| st_psl_05a | -1.63 | +0.51 |
| st_psl_1a | -0.23 | +0.12 |
| st_psl_5 | -0.89 | +0.13 |
| st_sig_05a | -1.86 | -1.77 |
| st_sig_10 | -2.59 | -1.71 |
| st_sig_1a | -1.88 | -0.59 |
| st_sig_5_r1 | -4.92 | -4.04 |
| st_sw3_0 | -1.99 | -1.82 |
| st_sw3_05a | -1.82 | -1.53 |
| st_sw3_10 | -1.03 | -1.35 |
| st_sw3_5_fix | -0.92 | -0.76 |
| st_sw5_0 | -2.21 | -1.82 |
| st_sw5_5_m15x90 | -2.17 | -2.23 |
| st_sw5_5_m20x120 | -1.89 | -1.65 |
| st_sw5_5_r1 | -2.41 | -2.10 |
| st_sw5_5_r2 | -1.23 | -1.98 |
| st_sw8_0 | -1.16 | -1.39 |
| st_sw8_05a | -1.49 | -1.59 |
| st_sw8_10 | -1.23 | -0.90 |
| st_sw8_1a | -1.33 | -0.80 |
| st_sw8_5_r1 | -2.50 | -2.17 |
| st_sw8_5_r2 | -1.09 | -0.09 |
| st_vw_0 | -0.33 | -1.45 |
| st_vw_05a | -1.34 | -1.55 |
| st_vw_10 | -0.83 | -1.37 |
| tg_hvn | +0.62 | -0.01 |
| tg_lvn | +0.71 | +1.24 |
| tg_poc | +0.09 | -0.83 |
| tg_rh1 | -0.28 | +1.13 |
| tg_rmid | +0.28 |  |
| tg_sw2 | -1.16 | -2.07 |
| tg_u1 | -0.76 | -1.49 |
| tg_u2 | -0.52 | -0.42 |

| class | cells | mean paired pts/trade | median | share positive |
|--|--|--|--|--|
| DY | 78 | -2.31 | -2.48 | 0.09 |
| ST | 137 | -1.45 | -1.33 | 0.09 |
| TG | 84 | -0.85 | -0.55 | 0.32 |


## 4. Nulls (best-of-N on the WF effect vs placebo (b); primary = all cells, secondary = per group and per class), MDE beside each
| null group | cells with (b) draws | N_total scaling | best cell | best effect vs (b) pts/trade | null p95 | rank of best |
|--|--|--|--|--|--|--|
| ALL180 | 299 | 180 | SB_KB_tg_pd | +2.90 | +6.53 | 0.00 |
| ALL300 | 299 | 300 | SB_KB_tg_pd | +2.90 | +6.24 | 0.21 |
| SB1 | 30 | 180 | SB_ST_st_sig0 | +0.71 | +2.23 | 0.00 |
| SB10 | 29 | 180 | SB_KB8_cb_hl_pd | +1.33 | +3.68 | 0.19 |
| SB10_DY | 22 | 180 | SB_KB8_cb_hl_pd | +1.33 | +3.74 | 0.19 |
| SB10_TG | 7 | 180 | SB_KB8_tg_lvn | +0.92 | +2.03 | 0.56 |
| SB1_DY | 5 | 180 | SB_ST_dy_u1 | -0.58 | +1.55 | 0.00 |
| SB1_ST | 13 | 180 | SB_ST_st_sig0 | +0.71 | +1.85 | 0.25 |
| SB1_TG | 12 | 180 | SB_ST_tg_pd | +0.49 | +2.31 | 0.07 |
| SB2 | 30 | 180 | SB_HM_tg_pd | +1.42 | +3.20 | 0.54 |
| SB2_DY | 5 | 180 | SB_HM_dy_u2 | +0.75 | +3.83 | 0.69 |
| SB2_ST | 13 | 180 | SB_HM_st_sig0 | +1.37 | +1.73 | 0.88 |
| SB2_TG | 12 | 180 | SB_HM_tg_pd | +1.42 | +2.23 | 0.65 |
| SB3 | 30 | 180 | SB_KB_tg_pd | +2.90 | +2.55 | 1.00 |
| SB3_DY | 5 | 180 | SB_KB_dy_trail | -0.30 | +1.70 | 0.00 |
| SB3_ST | 13 | 180 | SB_KB_st_sig0 | +0.63 | +1.60 | 0.19 |
| SB3_TG | 12 | 180 | SB_KB_tg_pd | +2.90 | +2.57 | 1.00 |
| SB4 | 30 | 180 | SB_SM_tg_fib1618 | +1.39 | +5.97 | 0.06 |
| SB4_DY | 5 | 180 | SB_SM_dy_u2 | +0.58 | +3.89 | 0.06 |
| SB4_ST | 13 | 180 | SB_SM_st_sw8_5 | +0.97 | +2.68 | 0.07 |
| SB4_TG | 12 | 180 | SB_SM_tg_fib1618 | +1.39 | +6.16 | 0.25 |
| SB5 | 30 | 180 | SB_EM_tg_fib1618 | +1.35 | +3.15 | 0.00 |
| SB5_DY | 5 | 180 | SB_EM_dy_u2 | +0.85 | +3.08 | 0.04 |
| SB5_ST | 13 | 180 | SB_EM_st_sw8_5 | +1.23 | +3.24 | 0.06 |
| SB5_TG | 12 | 180 | SB_EM_tg_fib1618 | +1.35 | +2.60 | 0.19 |
| SB6 | 30 | 180 | SB_ER4_tg_vp1 | +2.00 | +6.31 | 0.02 |
| SB6_DY | 9 | 180 | SB_PBR60_P2_dy_trail | +0.03 | +6.07 | 0.00 |
| SB6_ST | 12 | 180 | SB_PBR60_P2_st_sw8_5 | +0.32 | +6.21 | 0.00 |
| SB6_TG | 9 | 180 | SB_ER4_tg_vp1 | +2.00 | +3.94 | 0.66 |
| SB7 | 30 | 180 | SB_ST7_st_psl_1a | +0.58 | +1.98 | 0.00 |
| SB7_ST | 30 | 180 | SB_ST7_st_psl_1a | +0.58 | +1.98 | 0.00 |
| SB8 | 30 | 180 | SB_ST8_cb_sw5_hvn | +0.61 | +4.99 | 0.00 |
| SB8_DY | 22 | 180 | SB_ST8_cb_sw5_hvn | +0.61 | +5.19 | 0.00 |
| SB8_TG | 8 | 180 | SB_ST8_tg_hvn | +0.43 | +2.86 | 0.06 |
| SB9 | 30 | 180 | SB_KB7_st_hl_5_r1 | +0.40 | +1.71 | 0.00 |
| SB9_ST | 30 | 180 | SB_KB7_st_hl_5_r1 | +0.40 | +1.71 | 0.00 |

Per-trade paired MDE is 1.3-18.2 pts (median 2.9; the largest are the 300-trade PRO2_ER4 trend cells); weekly MDE vs the control about $14k/wk. Observed effects of -4..+5 pts/trade are mostly inside one to two MDE; the negative stop/trail/break effects are well outside it (CIs below 0 in 115 cells).

## 5. Near misses (LEADS, not CANDIDATES)
- SB_KB_tg_fib2618 (KB entries, stop 60, target entry +2.618 x impulse): paired WF +3.30 [+0.66,+5.92] pts/trade (MDE 3.70, 4201 pairs), HOLD +1.79, 2023 +0.37, placebo ranks WF b 1.00, a 1.00, c 0.94, d 1.00; fails neighbours_agree,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180. Not replicated on ST/HM/SM/EM (-2.2..+0.5).
- SB_KB_tg_pd (KB, stop 60, prior-session H/L target): paired +5.00 [+0.81,+9.08] (MDE 6.43), HOLD +6.56, 2023 -1.92; ranks WF b 1.00, a 0.94, c 0.06, d 1.00; the random-in-regime placebo (c) rank is 0.06: the same target on random times of the same days earns as much, i.e. the effect is the day's trend, not the entry timing. Fails placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,maxDD_not_worse(full sequence),SPAN2<=0,beats_(b)_CI_includes_0,best_of_N_all180.
- Spec if anyone wants a forward test (LEAD, not a recommendation): KB 3-min Keltner entries as in TE7_kelt3m_n14_m1.0, fixed 60-pt stop, 10 lots, target at the prior-session high/low (or 2.618 x impulse from the latest confirmed 5-bar swing), flat 16:55; expect +3..+5 pts/trade vs 60/60 at most, 2023 sign negative/zero, best-of-N null p95 +6.5.

## 6. DS3 mix and equal-risk lines
Stack lines (cell added to the live stack, WF) are in the top-10 table (d mean $/wk, d Sharpe, d maxDD) and in out/SB/res_*.pkl for every cell. Equal-risk lines (equal_risk.py, no marginal-Sharpe call, so no holdout re-read) for the 123 cells with a positive WF weekly mean:
| cell (WF weekly mean > 0, top 10 by equal-risk $/wk) | equal-lots $/wk (10 lots) | equal-risk $/wk (lots) | capacity lots |
|--|--|--|--|
| SB_KB_tg_fib2618 | 14,574 | 15,852 (10.9) | 96 |
| SB_KB_tg_rh2 | 14,482 | 15,322 (10.6) | 109 |
| SB_ST_tg_fib2618 | 11,529 | 12,080 (10.5) | 71 |
| SB_KB8_cb_sw5_rh2 | 11,630 | 11,005 (9.5) | 100 |
| SB_SM_st_sw5_5_fix | 6,782 | 10,802 (16.6) | 128 |
| SB_SM_tg_fib1618 | 7,392 | 10,550 (14.4) | 122 |
| SB_SM_tg_pd | 9,172 | 10,485 (11.4) | 197 |
| SB_SM_tg_rh2 | 8,690 | 10,355 (11.9) | 151 |
| SB_HM_tg_rh2 | 9,743 | 10,256 (10.5) | 82 |
| SB_EM_st_hl_5 | 6,843 | 10,241 (15.2) | 166 |


## 7. All cells

### SB1 (ST), prereg sha256 13ab39480dec4c19...
| cell | verdict | failed | valid/trades | tr/wk | stop/tgt mean | win obs/req @R (WF) | paired WF pts [CI] (MDE) | HOLD/2023 paired | WF wk $ d vs ctl |
|--|--|--|--|--|--|--|--|--|--|
| ST_st_sig5 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5155/5125 | +32.7 | 30/60 | 0.33/0.34@1.9 | -2.64 [-4.7,-0.6] (2.9) | -3.61/-5.15 | -3,380 |
| ST_st_sw3_5 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 7036/6812 | +41.3 | 43/60 | 0.41/0.42@1.4 | -1.94 [-3.4,-0.5] (2.1) | -1.80/-3.99 | -8,263 |
| ST_st_sw5_5 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6480/6172 | +36.9 | 48/60 | 0.43/0.44@1.3 | -2.03 [-3.5,-0.5] (2.2) | -1.61/-2.64 | -7,696 |
| ST_st_sw8_5 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6030/5584 | +32.9 | 54/60 | 0.45/0.47@1.1 | -2.03 [-3.4,-0.6] (2.0) | -1.82/-2.67 | -5,006 |
| ST_st_sw5_10 | DEAD | mean_up,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6780/6415 | +37.7 | 50/60 | 0.45/0.45@1.2 | -1.09 [-2.4,+0.2] (2.0) | +0.30/-3.75 | -14,636 |
| ST_st_sw5_a05 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6101/5766 | +34.9 | 49/60 | 0.44/0.45@1.2 | -1.63 [-3.3,-0.1] (2.2) | -0.93/-3.84 | -8,203 |
| ST_st_sw5_a10 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6195/5828 | +35.0 | 52/60 | 0.46/0.46@1.2 | -1.16 [-2.6,+0.3] (2.1) | -0.35/-2.79 | -6,604 |
| ST_st_hl_5 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5297/5164 | +31.7 | 41/60 | 0.40/0.41@1.5 | -1.80 [-3.3,+0.0] (2.3) | -1.28/-6.50 | -6,403 |
| ST_st_vw_5 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 4931/4593 | +26.6 | 60/60 | 0.49/0.49@1.1 | -1.15 [-2.3,+0.1] (1.7) | -0.55/-1.44 | +416 |
| ST_st_psl_10 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1227/1126 | +6.0 | 76/60 | 0.54/0.54@0.9 | -1.55 [-4.3,+1.1] (3.7) | -1.18/-1.77 | -3,296 |
| ST_st_sig0 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 3582/3563 | +23.6 | 31/60 | 0.34/0.35@1.9 | -0.20 [-2.8,+2.6] (3.9) | -0.26/-7.55 | +3,155 |
| ST_st_sw5_5_fix | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6480/6172 | +36.9 | 48/60 | 0.43/0.44@1.3 | -1.08 [-2.1,-0.0] (1.5) | -0.37/-0.47 | -7,702 |
| ST_st_sw5_5_m20 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5228/5123 | +31.2 | 45/60 | 0.42/0.43@1.3 | -2.04 [-3.3,-0.7] (2.0) | -1.35/-3.20 | -10,382 |
| ST_tg_sw1 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 4939/4877 | +30.6 | 60/37 | 0.64/0.67@0.5 | -1.53 [-2.5,-0.4] (1.6) | -0.48/+0.69 | -10,806 |
| ST_tg_pd | DEAD | placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5562/3009 | +17.3 | 60/243 | 0.37/0.36@1.7 | +0.90 [-2.6,+4.4] (5.0) | +3.00/-1.35 | -1,594 |
| ST_tg_on | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1936/1562 | +9.3 | 60/120 | 0.45/0.47@1.1 | -0.61 [-3.5,+2.4] (4.4) | -1.07/-1.77 | +928 |
| ST_tg_or | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1057/971 | +6.0 | 60/81 | 0.50/0.53@0.9 | -3.05 [-6.6,+0.6] (5.2) | -2.45/-1.11 | -1,857 |
| ST_tg_vp1 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 2111/1953 | +12.6 | 60/63 | 0.57/0.59@0.7 | -0.53 [-2.4,+1.6] (2.8) | -0.27/-1.88 | +1,002 |
| ST_tg_vp2 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5567/4711 | +28.9 | 60/85 | 0.51/0.52@0.9 | -1.04 [-2.4,+0.4] (2.0) | -0.50/-1.88 | -4,402 |
| ST_tg_va | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 2669/2455 | +15.7 | 60/64 | 0.55/0.59@0.7 | -2.18 [-3.9,-0.5] (2.4) | -2.08/+4.44 | -1,920 |
| ST_tg_fib10 | DEAD | placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6607/6014 | +37.0 | 60/58 | 0.57/0.58@0.7 | +0.18 [-1.0,+1.3] (1.7) | +0.76/-1.99 | -1,431 |
| ST_tg_fib1618 | DEAD | placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 7279/5961 | +35.7 | 60/85 | 0.50/0.50@1.0 | +0.49 [-0.9,+1.8] (2.0) | +1.46/-1.39 | -496 |
| ST_tg_fib2618 | DEAD | placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 7420/5190 | +30.5 | 60/136 | 0.42/0.41@1.4 | +0.54 [-1.3,+2.4] (2.7) | +1.03/-0.20 | +2,924 |
| ST_tg_ropp | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 4999/4793 | +30.4 | 60/51 | 0.58/0.61@0.6 | -1.98 [-3.2,-0.6] (1.9) | -0.74/+0.63 | -8,010 |
| ST_tg_rh2 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 8308/4569 | +26.1 | 60/235 | 0.31/0.31@2.2 | -0.41 [-3.1,+2.2] (3.9) | -1.30/-1.67 | -5,117 |
| ST_dy_u1 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5978/5448 | +32.9 | 48/47 | 0.56/0.58@0.7 | -3.26 [-5.1,-1.4] (2.6) | -2.87/-3.98 | -19,143 |
| ST_dy_u2 | DEAD | mean_up,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 4484/3782 | +23.4 | 48/91 | 0.42/0.44@1.3 | -2.57 [-5.1,+0.3] (3.9) | +0.10/-7.96 | -7,888 |
| ST_dy_trail | DEAD | mean_up,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6480/5632 | +33.5 | 46/- | 0.34/0.34@2.0 | -0.85 [-2.9,+1.2] (3.0) | +0.26/-4.30 | -6,287 |
| ST_dy_brk | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6480/5614 | +33.3 | 45/- | 0.33/0.34@1.9 | -2.60 [-4.8,-0.5] (3.1) | -1.46/-5.06 | -14,005 |
| ST_dy_trail_u1 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5978/5855 | +35.5 | 48/47 | 0.50/0.54@0.9 | -3.31 [-4.8,-1.7] (2.2) | -2.59/-5.66 | -21,933 |

### SB2 (HM), prereg sha256 9db497788b176bbc...
| cell | verdict | failed | valid/trades | tr/wk | stop/tgt mean | win obs/req @R (WF) | paired WF pts [CI] (MDE) | HOLD/2023 paired | WF wk $ d vs ctl |
|--|--|--|--|--|--|--|--|--|--|
| HM_st_sig5 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1968/1967 | +12.6 | 26/60 | 0.32/0.32@2.2 | -1.33 [-5.5,+2.2] (5.7) | -2.09/-10.74 | +1,168 |
| HM_st_sw3_5 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5562/5413 | +32.2 | 46/60 | 0.44/0.43@1.3 | -0.68 [-2.1,+0.8] (2.1) | -0.28/+0.85 | -5,444 |
| HM_st_sw5_5 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5544/5365 | +31.6 | 48/60 | 0.45/0.44@1.3 | -0.56 [-2.0,+0.9] (2.0) | -0.53/-1.52 | -3,107 |
| HM_st_sw8_5 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5270/5001 | +29.2 | 52/60 | 0.47/0.46@1.2 | -1.22 [-2.5,+0.1] (1.9) | -1.92/-1.25 | -740 |
| HM_st_sw5_10 | DEAD | mean_up,placebo>=0.90,pairedCI&maxDD,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5777/5567 | +32.3 | 50/60 | 0.47/0.46@1.2 | -0.01 [-1.3,+1.2] (1.8) | +0.07/+0.90 | -1,131 |
| HM_st_sw5_a05 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5226/5026 | +29.9 | 49/60 | 0.46/0.45@1.2 | -0.65 [-2.0,+0.7] (2.0) | -0.59/-2.20 | -3,941 |
| HM_st_sw5_a10 | DEAD | holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5212/4983 | +29.4 | 52/60 | 0.48/0.46@1.2 | +0.06 [-1.2,+1.4] (1.9) | -0.05/-0.25 | -1,028 |
| HM_st_hl_5 | DEAD | placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5327/5238 | +31.4 | 42/60 | 0.43/0.42@1.4 | +0.31 [-1.3,+2.0] (2.4) | +0.73/-0.75 | +67 |
| HM_st_vw_5 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 3567/3411 | +19.6 | 59/60 | 0.49/0.48@1.1 | -0.90 [-2.5,+0.6] (2.2) | -1.34/+1.56 | +1,178 |
| HM_st_psl_10 | DEAD | placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1020/953 | +5.0 | 74/60 | 0.52/0.54@0.9 | +0.64 [-2.4,+3.8] (4.4) | +2.54/-5.16 | +1,434 |
| HM_st_sig0 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1187/1186 | +7.8 | 27/60 | 0.32/0.32@2.1 | -0.75 [-5.1,+3.9] (6.5) | -1.94/-2.06 | -5,671 |
| HM_st_sw5_5_fix | DEAD | holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5544/5365 | +31.6 | 48/60 | 0.45/0.44@1.3 | +0.07 [-1.0,+1.3] (1.5) | -0.15/-1.19 | +2,218 |
| HM_st_sw5_5_m20 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 4630/4553 | +27.1 | 46/60 | 0.45/0.44@1.3 | -0.52 [-1.9,+0.9] (1.9) | -0.99/-0.27 | -922 |
| HM_tg_sw1 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 2772/2749 | +16.7 | 60/35 | 0.67/0.68@0.5 | -1.76 [-3.1,-0.4] (2.0) | -1.72/-2.11 | -4,456 |
| HM_tg_pd | DEAD | placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 4336/2593 | +14.7 | 60/256 | 0.35/0.34@1.9 | +0.95 [-2.5,+4.7] (5.1) | +3.35/-1.98 | +7,538 |
| HM_tg_on | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1343/1113 | +6.5 | 60/136 | 0.44/0.46@1.2 | -3.96 [-8.1,+0.5] (6.2) | -3.32/-0.49 | -3,511 |
| HM_tg_or | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 764/696 | +4.1 | 60/95 | 0.50/0.52@0.9 | -4.09 [-7.6,-0.6] (5.3) | -3.95/-3.87 | -2,220 |
| HM_tg_vp1 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1577/1426 | +8.9 | 60/75 | 0.54/0.55@0.8 | -1.44 [-4.0,+1.0] (3.6) | -0.87/-3.46 | +1,036 |
| HM_tg_vp2 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 3613/3083 | +18.7 | 60/91 | 0.51/0.52@0.9 | -2.02 [-3.9,-0.2] (2.6) | -1.79/+0.17 | -3,547 |
| HM_tg_va | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1835/1684 | +10.4 | 60/72 | 0.56/0.57@0.8 | -2.74 [-4.8,-0.5] (3.1) | -3.17/-2.70 | +8 |
| HM_tg_fib10 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5455/5208 | +31.4 | 60/53 | 0.59/0.59@0.7 | -0.50 [-1.6,+0.7] (1.7) | -0.13/+0.86 | +3,321 |
| HM_tg_fib1618 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5937/5147 | +30.4 | 60/79 | 0.51/0.50@1.0 | -0.43 [-1.9,+1.1] (2.1) | -0.22/+0.50 | +3,805 |
| HM_tg_fib2618 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6030/4527 | +26.3 | 60/125 | 0.42/0.41@1.4 | -0.24 [-2.2,+1.6] (2.7) | -0.73/-1.30 | +3,642 |
| HM_tg_ropp | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1726/1717 | +11.2 | 60/34 | 0.68/0.69@0.4 | -3.20 [-5.1,-1.4] (2.7) | -3.72/-4.52 | -6,558 |
| HM_tg_rh2 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6308/4022 | +22.7 | 60/203 | 0.34/0.33@2.0 | -0.27 [-2.7,+2.2] (3.6) | -0.12/-1.03 | +5,232 |
| HM_dy_u1 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 4951/4560 | +27.2 | 48/50 | 0.56/0.57@0.7 | -2.76 [-4.6,-1.1] (2.5) | -1.89/+0.80 | -5,607 |
| HM_dy_u2 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 3729/3099 | +18.8 | 48/104 | 0.42/0.41@1.4 | -0.28 [-3.6,+3.0] (4.7) | -0.02/-6.27 | -840 |
| HM_dy_trail | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5544/4897 | +28.7 | 47/- | 0.37/0.36@1.8 | -0.76 [-2.8,+1.2] (3.0) | -0.68/-3.16 | +802 |
| HM_dy_brk | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5544/4896 | +28.6 | 46/- | 0.37/0.37@1.7 | -2.54 [-4.7,-0.5] (3.0) | -1.47/-4.65 | -5,407 |
| HM_dy_trail_u1 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 4951/4854 | +29.0 | 48/50 | 0.51/0.53@0.9 | -2.91 [-4.6,-1.3] (2.4) | -3.04/-2.78 | -10,086 |

### SB3 (KB), prereg sha256 22b8b69d145e518f...
| cell | verdict | failed | valid/trades | tr/wk | stop/tgt mean | win obs/req @R (WF) | paired WF pts [CI] (MDE) | HOLD/2023 paired | WF wk $ d vs ctl |
|--|--|--|--|--|--|--|--|--|--|
| KB_st_sig5 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 7020/6929 | +42.8 | 37/60 | 0.37/0.39@1.6 | -2.19 [-3.7,-0.6] (2.3) | -2.45/+1.75 | -4,057 |
| KB_st_sw3_5 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 7536/7075 | +42.3 | 50/60 | 0.44/0.45@1.2 | -2.10 [-3.3,-0.9] (1.8) | -1.66/-2.26 | -13,337 |
| KB_st_sw5_5 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 7326/6702 | +39.5 | 55/60 | 0.47/0.47@1.1 | -1.87 [-3.0,-0.8] (1.5) | -1.22/-1.87 | -11,145 |
| KB_st_sw8_5 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6905/6105 | +35.4 | 60/60 | 0.50/0.50@1.0 | -1.40 [-2.5,-0.3] (1.7) | -1.25/-1.13 | -13,724 |
| KB_st_sw5_10 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 7355/6652 | +38.7 | 58/60 | 0.49/0.49@1.0 | -1.26 [-2.3,-0.3] (1.5) | -0.64/-1.10 | -10,009 |
| KB_st_sw5_a05 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6854/6179 | +36.4 | 58/60 | 0.48/0.48@1.1 | -1.67 [-2.8,-0.7] (1.6) | -1.42/-1.51 | -14,196 |
| KB_st_sw5_a10 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6457/5725 | +33.1 | 61/60 | 0.50/0.50@1.0 | -1.15 [-2.3,+0.1] (1.8) | -0.24/-2.18 | -10,441 |
| KB_st_hl_5 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 7414/7109 | +42.9 | 46/60 | 0.42/0.44@1.3 | -2.04 [-3.3,-0.8] (1.8) | -1.49/-2.74 | -15,252 |
| KB_st_vw_5 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 4370/4143 | +24.0 | 59/60 | 0.47/0.48@1.1 | -1.19 [-2.8,+0.3] (2.1) | -0.58/-0.94 | +337 |
| KB_st_psl_10 | DEAD | mean_up,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1536/1429 | +7.6 | 72/60 | 0.51/0.54@0.9 | -0.69 [-3.2,+1.8] (3.5) | +2.43/-1.20 | -2,162 |
| KB_st_sig0 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5783/5718 | +35.9 | 36/60 | 0.37/0.38@1.6 | -0.70 [-2.5,+0.9] (2.4) | -0.25/+0.46 | -5,656 |
| KB_st_sw5_5_fix | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 7326/6702 | +39.5 | 55/60 | 0.47/0.47@1.1 | -0.57 [-1.5,+0.3] (1.3) | -0.34/+0.56 | -5,359 |
| KB_st_sw5_5_m20 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5803/5547 | +32.7 | 50/60 | 0.45/0.46@1.2 | -1.95 [-3.0,-0.8] (1.5) | -1.39/-1.89 | -12,696 |
| KB_tg_sw1 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 4682/4550 | +28.0 | 60/39 | 0.63/0.66@0.5 | -1.40 [-2.8,-0.2] (1.9) | -0.67/-0.18 | -8,729 |
| KB_tg_pd | DEAD | placebo>=0.90,neighbours_agree,pairedCI&maxDD,maxDD_not_worse(full sequence),SPAN2<=0,beats_(b)_CI_includes_0,best_of_N_all180 | 6167/2939 | +16.9 | 60/302 | 0.34/0.31@2.2 | +5.00 [+0.8,+9.1] (6.4) | +6.56/-1.92 | +183 |
| KB_tg_on | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 2334/1646 | +9.5 | 60/176 | 0.40/0.41@1.5 | -0.57 [-3.9,+2.8] (4.9) | -1.25/-1.73 | -924 |
| KB_tg_or | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1441/1184 | +7.0 | 60/129 | 0.46/0.48@1.1 | -2.39 [-6.1,+1.2] (5.1) | -1.77/-2.46 | -1,291 |
| KB_tg_vp1 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 2805/2205 | +13.5 | 60/110 | 0.47/0.47@1.1 | -0.86 [-3.2,+1.5] (3.4) | -0.31/-1.70 | +575 |
| KB_tg_vp2 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5474/4002 | +24.3 | 60/115 | 0.49/0.49@1.1 | -0.39 [-2.1,+1.4] (2.6) | -0.12/-2.09 | -3,280 |
| KB_tg_va | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 3044/2468 | +15.2 | 60/106 | 0.49/0.50@1.0 | -1.87 [-3.9,+0.2] (3.0) | -1.76/-1.26 | -4,176 |
| KB_tg_fib10 | DEAD | placebo>=0.90,neighbours_agree,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 7870/6896 | +41.8 | 60/65 | 0.54/0.53@0.9 | +0.62 [-0.4,+1.6] (1.4) | +0.44/+1.37 | -1,917 |
| KB_tg_fib1618 | DEAD | holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 8316/6171 | +36.5 | 60/99 | 0.45/0.45@1.2 | +0.42 [-0.8,+1.6] (1.8) | -0.16/+0.48 | -1,631 |
| KB_tg_fib2618 | DEAD | neighbours_agree,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 8387/5081 | +29.4 | 60/156 | 0.39/0.36@1.7 | +3.30 [+0.7,+5.9] (3.7) | +1.79/+0.37 | +3,672 |
| KB_tg_ropp | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 2850/2829 | +18.1 | 60/33 | 0.66/0.70@0.4 | -2.65 [-4.2,-1.2] (2.2) | -1.83/-1.37 | -7,116 |
| KB_tg_rh2 | DEAD | placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 8593/4578 | +25.9 | 60/210 | 0.33/0.32@2.2 | +1.74 [-0.9,+4.4] (3.8) | +0.84/-1.41 | +2,782 |
| KB_dy_u1 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6716/5850 | +34.8 | 57/49 | 0.58/0.61@0.6 | -3.34 [-5.0,-1.7] (2.3) | -2.28/-2.56 | -13,868 |
| KB_dy_u2 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5205/3798 | +22.7 | 57/108 | 0.42/0.44@1.3 | -2.35 [-4.9,-0.1] (3.4) | -1.18/-3.79 | -6,592 |
| KB_dy_trail | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 7326/6282 | +36.9 | 56/- | 0.36/0.37@1.7 | -2.08 [-3.8,-0.5] (2.3) | -1.32/-2.64 | -18,414 |
| KB_dy_brk | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 7326/6239 | +36.5 | 55/- | 0.35/0.37@1.7 | -2.88 [-4.4,-1.4] (2.2) | -1.98/-3.70 | -21,981 |
| KB_dy_trail_u1 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6716/6537 | +39.2 | 57/49 | 0.50/0.54@0.8 | -2.96 [-4.5,-1.6] (2.1) | -1.74/-2.99 | -23,720 |

### SB4 (SM), prereg sha256 d68a191252e03677...
| cell | verdict | failed | valid/trades | tr/wk | stop/tgt mean | win obs/req @R (WF) | paired WF pts [CI] (MDE) | HOLD/2023 paired | WF wk $ d vs ctl |
|--|--|--|--|--|--|--|--|--|--|
| SM_st_sig5 | DEAD | mean_up,placebo>=0.90,pairedCI&maxDD,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1976/1969 | +11.1 | 44/60 | 0.44/0.42@1.4 | -0.15 [-2.7,+2.2] (3.6) | +0.01/+1.35 | +330 |
| SM_st_sw3_5 | DEAD | mean_up,placebo>=0.90,neighbours_agree,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1946/1931 | +10.6 | 49/60 | 0.46/0.45@1.2 | -0.15 [-2.4,+2.0] (3.1) | +0.25/+0.72 | -946 |
| SM_st_sw5_5 | DEAD | placebo>=0.90,neighbours_agree,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1948/1923 | +10.3 | 54/60 | 0.49/0.47@1.1 | +0.18 [-2.0,+2.3] (3.1) | +0.36/+0.11 | -2,695 |
| SM_st_sw8_5 | DEAD | placebo>=0.90,neighbours_agree,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1883/1844 | +9.7 | 58/60 | 0.51/0.48@1.1 | +0.40 [-1.4,+2.4] (2.7) | +0.32/+2.30 | -1,332 |
| SM_st_sw5_10 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 2016/1982 | +10.5 | 56/60 | 0.51/0.48@1.1 | -0.70 [-2.8,+1.4] (3.0) | -1.86/+1.42 | -3,564 |
| SM_st_sw5_a05 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1853/1817 | +9.7 | 58/60 | 0.52/0.48@1.1 | -0.19 [-2.4,+2.0] (3.2) | -0.36/-1.43 | -1,363 |
| SM_st_sw5_a10 | DEAD | holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1750/1695 | +9.0 | 63/60 | 0.54/0.50@1.0 | +0.14 [-2.0,+2.3] (3.2) | -1.27/+0.60 | -1,379 |
| SM_st_hl_5 | DEAD | placebo>=0.90,neighbours_agree,pairedCI&maxDD,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1962/1952 | +10.8 | 47/60 | 0.46/0.44@1.2 | +0.63 [-1.6,+2.8] (3.2) | +1.36/+1.88 | +1,215 |
| SM_st_vw_5 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1645/1640 | +8.9 | 47/60 | 0.46/0.44@1.3 | -2.41 [-5.2,-0.1] (3.5) | -2.63/+2.04 | -2,519 |
| SM_st_psl_10 | DEAD | mean_up,placebo>=0.90,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 773/754 | +3.7 | 68/60 | 0.52/0.53@0.9 | -1.74 [-4.8,+1.3] (4.4) | +1.62/+0.21 | -1,756 |
| SM_st_sig0 | DEAD | mean_up,placebo>=0.90,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1739/1734 | +10.0 | 44/60 | 0.43/0.42@1.4 | -0.67 [-3.4,+2.2] (3.9) | +0.23/+0.49 | -1,280 |
| SM_st_sw5_5_fix | DEAD | mean_up,placebo>=0.90,pairedCI&maxDD,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1948/1923 | +10.3 | 54/60 | 0.49/0.47@1.1 | -0.14 [-1.8,+1.4] (2.4) | +0.98/+1.27 | -100 |
| SM_st_sw5_5_m20 | DEAD | mean_up,placebo>=0.90,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1554/1547 | +8.4 | 49/60 | 0.47/0.46@1.2 | -0.27 [-2.5,+2.0] (3.2) | +0.27/+2.49 | -2,190 |
| SM_tg_sw1 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 637/636 | +4.0 | 60/39 | 0.63/0.66@0.5 | -2.62 [-5.8,+0.5] (4.6) | -2.74/-5.57 | -1,702 |
| SM_tg_pd | DEAD | placebo>=0.90,neighbours_agree,pairedCI&maxDD,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 2061/1707 | +9.3 | 60/272 | 0.32/0.31@2.2 | +0.26 [-4.6,+5.2] (7.0) | +2.75/+0.20 | +3,391 |
| SM_tg_on | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 595/593 | +3.2 | 60/125 | 0.44/0.46@1.2 | -2.97 [-8.4,+1.8] (7.3) | -2.57/+2.50 | -1,185 |
| SM_tg_or | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 186/186 | +1.5 | 60/91 | 0.46/0.56@0.8 | -6.82 [-14.6,+0.9] (10.8) | -10.95/+6.39 | -979 |
| SM_tg_vp1 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 756/754 | +4.4 | 60/65 | 0.54/0.57@0.8 | -2.85 [-6.8,+0.8] (5.4) | -2.23/-0.18 | -1,835 |
| SM_tg_vp2 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1435/1397 | +7.9 | 60/89 | 0.49/0.51@0.9 | -4.04 [-7.2,-1.0] (4.4) | -5.16/+1.01 | -5,862 |
| SM_tg_va | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 714/708 | +4.3 | 60/68 | 0.54/0.58@0.7 | -4.18 [-8.2,-0.2] (5.5) | -6.29/+3.98 | -1,749 |
| SM_tg_fib10 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 2104/2067 | +11.6 | 60/67 | 0.54/0.53@0.9 | -1.03 [-3.4,+1.3] (3.2) | -0.64/-1.00 | -3,098 |
| SM_tg_fib1618 | DEAD | mean_up,placebo>=0.90,pairedCI&maxDD,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 2255/2155 | +11.9 | 60/103 | 0.46/0.45@1.2 | -0.18 [-2.8,+2.8] (4.1) | +0.25/+0.83 | +563 |
| SM_tg_fib2618 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 2298/2065 | +11.2 | 60/162 | 0.38/0.38@1.7 | -2.16 [-6.1,+2.0] (5.8) | -0.08/+1.48 | -1,445 |
| SM_tg_ropp | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 480/480 | +3.3 | 60/30 | 0.71/0.71@0.4 | -2.60 [-6.7,+1.5] (6.0) | -2.33/+0.70 | -1,712 |
| SM_tg_rh2 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 2397/2099 | +11.3 | 60/204 | 0.34/0.34@2.0 | -1.87 [-5.7,+2.1] (5.6) | -0.75/+1.43 | +2,441 |
| SM_dy_u1 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1854/1769 | +9.5 | 53/60 | 0.55/0.57@0.7 | -5.19 [-8.3,-1.9] (4.4) | -4.76/+3.89 | -11,750 |
| SM_dy_u2 | DEAD | placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1496/1373 | +7.5 | 53/121 | 0.44/0.41@1.4 | +0.19 [-4.7,+5.3] (7.5) | +1.65/-1.88 | -3,384 |
| SM_dy_trail | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1948/1945 | +10.4 | 54/- | 0.37/0.37@1.7 | -2.77 [-5.9,+0.3] (4.4) | -0.49/-0.04 | -6,166 |
| SM_dy_brk | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1948/1945 | +10.4 | 54/- | 0.37/0.38@1.6 | -4.48 [-7.5,-1.3] (4.5) | -2.44/-2.25 | -9,829 |
| SM_dy_trail_u1 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1854/1854 | +10.0 | 53/59 | 0.48/0.50@1.0 | -5.73 [-8.5,-3.1] (3.7) | -4.37/-1.70 | -12,198 |

### SB5 (EM), prereg sha256 874158ec19d992d3...
| cell | verdict | failed | valid/trades | tr/wk | stop/tgt mean | win obs/req @R (WF) | paired WF pts [CI] (MDE) | HOLD/2023 paired | WF wk $ d vs ctl |
|--|--|--|--|--|--|--|--|--|--|
| EM_st_sig5 | DEAD | placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1193/1193 | +7.2 | 34/60 | 0.38/0.36@1.8 | +0.13 [-4.1,+4.3] (5.9) | +1.00/-3.73 | +233 |
| EM_st_sw3_5 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1530/1513 | +8.7 | 44/60 | 0.42/0.42@1.4 | -2.71 [-5.9,+0.4] (4.5) | -1.70/-1.47 | -2,869 |
| EM_st_sw5_5 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1656/1632 | +9.1 | 49/60 | 0.45/0.43@1.3 | -2.74 [-5.4,-0.3] (3.7) | -2.16/-0.79 | -3,211 |
| EM_st_sw8_5 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1723/1674 | +9.1 | 53/60 | 0.48/0.46@1.2 | -0.77 [-3.6,+2.0] (3.9) | -0.23/-1.83 | -995 |
| EM_st_sw5_10 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1865/1834 | +9.9 | 49/60 | 0.46/0.44@1.3 | -1.08 [-3.7,+1.5] (3.7) | -0.89/-2.38 | -2,702 |
| EM_st_sw5_a05 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1636/1604 | +9.0 | 52/60 | 0.48/0.44@1.2 | -1.05 [-3.5,+1.6] (3.7) | -1.57/-2.12 | -1,162 |
| EM_st_sw5_a10 | DEAD | placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1694/1651 | +9.1 | 55/60 | 0.50/0.47@1.1 | +0.19 [-2.1,+2.6] (3.4) | +0.95/-0.51 | -1,412 |
| EM_st_hl_5 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1447/1437 | +8.2 | 43/60 | 0.43/0.41@1.4 | -0.80 [-4.6,+2.7] (5.0) | -0.14/+0.76 | +1,866 |
| EM_st_vw_5 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,standalone<=beta(d),best_of_N_group,best_of_N_all180 | 1639/1638 | +9.1 | 46/60 | 0.45/0.43@1.3 | -0.51 [-3.4,+2.3] (4.1) | -2.58/+0.86 | -1,923 |
| EM_st_psl_10 | DEAD | mean_up,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 807/779 | +3.9 | 69/60 | 0.53/0.54@0.9 | -1.26 [-4.7,+2.2] (4.9) | +1.11/-1.24 | +116 |
| EM_st_sig0 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 895/895 | +5.6 | 35/60 | 0.37/0.36@1.7 | -2.64 [-6.9,+2.1] (6.7) | -5.69/-10.96 | -1,899 |
| EM_st_sw5_5_fix | DEAD | mean_up,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1656/1632 | +9.1 | 49/60 | 0.45/0.43@1.3 | -0.33 [-2.3,+1.6] (2.7) | +0.22/-2.09 | -1,427 |
| EM_st_sw5_5_m20 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1274/1268 | +7.2 | 47/60 | 0.47/0.43@1.3 | -1.68 [-4.1,+0.9] (3.6) | -1.08/+1.61 | -1,395 |
| EM_tg_sw1 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 770/769 | +5.0 | 60/33 | 0.67/0.68@0.5 | -2.60 [-5.3,+0.1] (4.0) | -2.93/-0.04 | -2,093 |
| EM_tg_pd | DEAD | placebo>=0.90,neighbours_agree,pairedCI&maxDD,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 2056/1720 | +9.3 | 60/266 | 0.32/0.31@2.3 | +0.69 [-4.4,+6.1] (7.6) | +3.16/+1.17 | +3,198 |
| EM_tg_on | DEAD | placebo>=0.90,neighbours_agree,pairedCI&maxDD,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 629/628 | +3.5 | 60/104 | 0.49/0.48@1.1 | +1.59 [-2.2,+5.6] (5.8) | +3.20/+4.78 | +702 |
| EM_tg_or | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 286/286 | +2.0 | 60/61 | 0.53/0.57@0.8 | -3.57 [-8.8,+1.6] (7.2) | -2.23/+1.86 | -1,042 |
| EM_tg_vp1 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 648/648 | +4.2 | 60/52 | 0.58/0.62@0.6 | -4.79 [-7.8,-1.9] (4.3) | -3.98/-5.86 | -3,767 |
| EM_tg_vp2 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1473/1459 | +8.5 | 60/73 | 0.55/0.55@0.8 | -2.30 [-4.9,+0.3] (3.7) | -3.35/-0.79 | -2,682 |
| EM_tg_va | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 640/638 | +4.2 | 60/50 | 0.61/0.63@0.6 | -2.20 [-5.2,+1.5] (4.7) | -3.28/+1.69 | -604 |
| EM_tg_fib10 | DEAD | placebo>=0.90,neighbours_agree,pairedCI&maxDD,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1665/1658 | +9.6 | 60/62 | 0.58/0.55@0.8 | +0.42 [-1.7,+2.6] (3.1) | +0.92/+0.09 | +463 |
| EM_tg_fib1618 | DEAD | placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1895/1865 | +10.6 | 60/91 | 0.50/0.48@1.1 | +1.25 [-1.8,+4.0] (4.1) | +1.78/-2.34 | +3,912 |
| EM_tg_fib2618 | DEAD | mean_up,placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1954/1870 | +10.6 | 60/144 | 0.41/0.40@1.5 | -0.44 [-4.3,+3.4] (5.5) | +0.53/-0.45 | +4,399 |
| EM_tg_ropp | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 830/829 | +5.3 | 60/34 | 0.68/0.69@0.4 | -3.24 [-6.1,-0.5] (4.0) | -2.42/-4.49 | -3,106 |
| EM_tg_rh2 | DEAD | placebo>=0.90,neighbours_agree,pairedCI&maxDD,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 2333/2138 | +11.6 | 60/200 | 0.35/0.34@1.9 | +0.27 [-3.7,+4.2] (5.7) | +3.07/+1.78 | +4,321 |
| EM_dy_u1 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1612/1558 | +8.7 | 48/52 | 0.55/0.55@0.8 | -4.75 [-8.1,-1.2] (4.9) | -5.44/+2.80 | -7,180 |
| EM_dy_u2 | DEAD | mean_up,placebo>=0.90,pairedCI&maxDD,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1323/1246 | +7.2 | 48/116 | 0.40/0.39@1.5 | -1.17 [-5.8,+3.7] (6.9) | +1.10/+5.43 | +1,809 |
| EM_dy_trail | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1656/1653 | +9.2 | 49/- | 0.33/0.34@2.0 | -3.82 [-7.6,-0.5] (5.1) | -4.36/-6.61 | -5,073 |
| EM_dy_brk | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1656/1652 | +9.2 | 49/- | 0.33/0.35@1.8 | -4.91 [-8.5,-1.5] (5.1) | -5.64/-9.60 | -6,175 |
| EM_dy_trail_u1 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1612/1610 | +9.0 | 48/52 | 0.46/0.48@1.1 | -4.96 [-8.1,-2.0] (4.5) | -6.11/-6.10 | -8,317 |

### SB6 (PB3B_R5_P1, PB3B_R60_P2, PRO2_ER4_EMA5), prereg sha256 8bd4a4d87627a0f0...
| cell | verdict | failed | valid/trades | tr/wk | stop/tgt mean | win obs/req @R (WF) | paired WF pts [CI] (MDE) | HOLD/2023 paired | WF wk $ d vs ctl |
|--|--|--|--|--|--|--|--|--|--|
| PBR5_P1_st_sig5 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 3515/3502 | +22.5 | 28/60 | 0.30/0.33@2.0 | -2.39 [-4.5,-0.2] (3.1) | -2.36/-11.28 | -3,131 |
| PBR5_P1_st_sw5_5 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6763/6372 | +38.4 | 51/60 | 0.44/0.46@1.2 | -1.39 [-2.6,-0.1] (1.8) | -1.43/-1.83 | -2,898 |
| PBR5_P1_st_sw8_5 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6460/5890 | +34.8 | 59/60 | 0.48/0.49@1.0 | -0.71 [-1.8,+0.3] (1.5) | -0.81/-1.46 | +1,957 |
| PBR5_P1_st_hl_5 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5753/5629 | +34.8 | 41/60 | 0.39/0.41@1.4 | -1.53 [-3.0,-0.2] (2.0) | -1.61/-1.20 | -1,633 |
| PBR5_P1_tg_pd | DEAD | placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5717/2903 | +16.6 | 60/264 | 0.36/0.34@1.9 | +2.16 [-1.6,+6.1] (5.7) | +2.78/-1.98 | +2,105 |
| PBR5_P1_tg_vp1 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 2138/1827 | +11.4 | 60/82 | 0.52/0.55@0.8 | -0.38 [-2.6,+2.1] (3.4) | -0.13/-0.35 | +416 |
| PBR5_P1_tg_fib1618 | DEAD | placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 7490/5886 | +35.4 | 60/88 | 0.48/0.49@1.1 | +0.40 [-0.9,+1.7] (1.8) | +0.70/-2.14 | +1,631 |
| PBR5_P1_dy_u1 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6238/5691 | +34.7 | 52/45 | 0.56/0.61@0.6 | -3.53 [-5.2,-1.9] (2.5) | -2.91/-1.65 | -7,250 |
| PBR5_P1_dy_trail | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6763/5653 | +33.8 | 50/- | 0.32/0.34@2.0 | -1.85 [-3.8,+0.2] (2.8) | -2.13/-3.21 | -10,906 |
| PBR5_P1_dy_brk | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6763/5615 | +33.5 | 49/- | 0.32/0.34@1.9 | -3.29 [-5.2,-1.2] (2.9) | -3.21/-3.77 | -17,423 |
| PBR60_P2_st_sig5 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 3212/3194 | +20.2 | 30/60 | 0.33/0.34@1.9 | -4.06 [-6.8,-1.3] (3.9) | -3.87/+1.66 | -7,222 |
| PBR60_P2_st_sw5_5 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5333/5161 | +31.0 | 46/60 | 0.42/0.44@1.3 | -2.01 [-3.7,-0.4] (2.3) | -1.68/-2.36 | -13,052 |
| PBR60_P2_st_sw8_5 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5427/5205 | +30.9 | 51/60 | 0.45/0.46@1.2 | -1.13 [-2.5,+0.2] (1.9) | -0.58/-0.18 | -4,141 |
| PBR60_P2_st_hl_5 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 4149/4059 | +25.0 | 38/60 | 0.37/0.39@1.6 | -2.24 [-3.9,-0.6] (2.4) | -2.00/-1.71 | -12,412 |
| PBR60_P2_tg_pd | DEAD | placebo>=0.90,neighbours_agree,pairedCI&maxDD,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 3958/2614 | +14.9 | 60/148 | 0.40/0.40@1.5 | +1.13 [-1.6,+4.0] (4.1) | +2.77/+2.31 | -1,870 |
| PBR60_P2_tg_vp1 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 2726/2360 | +14.2 | 60/77 | 0.50/0.53@0.9 | -1.25 [-3.1,+0.6] (2.6) | -1.38/-1.18 | -4,582 |
| PBR60_P2_tg_fib1618 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5719/5000 | +29.9 | 60/75 | 0.51/0.52@0.9 | -0.87 [-2.3,+0.5] (2.1) | -0.17/-0.39 | -7,407 |
| PBR60_P2_dy_u1 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5021/4841 | +29.3 | 47/34 | 0.57/0.61@0.6 | -3.43 [-5.0,-1.7] (2.4) | -3.19/-4.62 | -19,818 |
| PBR60_P2_dy_trail | DEAD | mean_up,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5333/4772 | +28.5 | 45/- | 0.33/0.34@1.9 | -1.70 [-3.9,+0.4] (3.1) | +0.17/-4.95 | -14,961 |
| PBR60_P2_dy_brk | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5333/4747 | +28.3 | 45/- | 0.32/0.35@1.9 | -3.25 [-5.6,-1.1] (3.2) | -1.25/-5.17 | -21,910 |
| ER4_st_sig5 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 408/406 | +3.1 | 25/60 | 0.29/0.31@2.2 | -4.92 [-12.1,+2.8] (10.6) | -9.98/-4.85 | -3,688 |
| ER4_st_sw5_5 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,standalone<=beta(d),best_of_N_group,best_of_N_all180 | 349/347 | +2.6 | 33/60 | 0.32/0.36@1.8 | -4.18 [-12.4,+2.6] (10.6) | -7.91/-3.82 | -1,152 |
| ER4_st_sw8_5 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 514/510 | +3.2 | 34/60 | 0.35/0.36@1.7 | -4.65 [-11.2,+2.0] (9.5) | -5.15/-5.16 | -1,930 |
| ER4_st_hl_5 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 125/125 | +1.6 | 28/60 | 0.23/0.33@2.0 | -13.53 [-27.0,-1.8] (18.2) | -19.40/-8.39 | -1,758 |
| ER4_tg_pd | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 906/818 | +4.3 | 60/170 | 0.39/0.38@1.6 | -0.31 [-5.9,+5.8] (8.4) | -2.49/-0.35 | -609 |
| ER4_tg_vp1 | DEAD | neighbours_agree,pairedCI&maxDD,placebo<0.95,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 308/302 | +2.3 | 60/40 | 0.67/0.66@0.5 | +4.21 [-1.0,+9.8] (7.6) | +3.50/+7.55 | +1,621 |
| ER4_tg_fib1618 | DEAD | placebo>=0.90,pairedCI&maxDD,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 370/365 | +2.7 | 60/44 | 0.59/0.63@0.6 | +1.12 [-4.0,+6.4] (7.5) | +1.76/+2.37 | +277 |
| ER4_dy_u1 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 341/339 | +2.6 | 33/32 | 0.50/0.55@0.8 | -1.95 [-10.2,+6.0] (11.7) | -6.20/-9.43 | -1,011 |
| ER4_dy_trail | DEAD | holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 349/344 | +2.6 | 33/- | 0.29/0.27@2.7 | +3.56 [-8.5,+16.3] (18.0) | -4.10/-14.41 | -252 |
| ER4_dy_brk | DEAD | holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 349/341 | +2.6 | 33/- | 0.28/0.27@2.7 | +3.20 [-8.7,+15.6] (17.8) | -5.12/-19.43 | -107 |

### SB7 (ST), prereg sha256 97b38e6b6169ffd2...
| cell | verdict | failed | valid/trades | tr/wk | stop/tgt mean | win obs/req @R (WF) | paired WF pts [CI] (MDE) | HOLD/2023 paired | WF wk $ d vs ctl |
|--|--|--|--|--|--|--|--|--|--|
| ST7_st_sig_10 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 7094/7056 | +43.5 | 30/60 | 0.33/0.35@1.9 | -2.59 [-4.2,-0.8] (2.4) | -1.89/-4.14 | -11,999 |
| ST7_st_sig_05a | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5214/5160 | +33.0 | 34/60 | 0.35/0.37@1.7 | -1.86 [-3.7,+0.0] (2.6) | -1.91/-4.76 | +3,411 |
| ST7_st_sig_1a | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6276/6171 | +38.8 | 38/60 | 0.38/0.39@1.5 | -1.88 [-3.3,-0.4] (2.2) | -0.73/-5.68 | -7,999 |
| ST7_st_sw3_0 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6351/6174 | +38.4 | 41/60 | 0.40/0.41@1.4 | -1.99 [-3.5,-0.5] (2.2) | -1.49/-6.20 | -12,633 |
| ST7_st_sw3_10 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 7420/7149 | +42.5 | 46/60 | 0.43/0.44@1.3 | -1.03 [-2.2,+0.2] (1.8) | -0.47/-2.27 | -9,079 |
| ST7_st_sw3_05a | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6623/6372 | +39.2 | 45/60 | 0.42/0.43@1.3 | -1.82 [-3.3,-0.3] (2.2) | -1.65/-4.77 | -9,268 |
| ST7_st_sw5_0 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5913/5640 | +34.4 | 47/60 | 0.42/0.43@1.3 | -2.21 [-3.6,-0.8] (2.1) | -1.25/-5.39 | -8,178 |
| ST7_st_sw8_0 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5648/5236 | +31.3 | 53/60 | 0.45/0.46@1.2 | -1.16 [-2.5,+0.1] (2.0) | -1.72/-3.57 | -8,622 |
| ST7_st_sw8_10 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6242/5732 | +33.3 | 56/60 | 0.47/0.48@1.1 | -1.23 [-2.5,+0.0] (1.9) | -0.49/-2.68 | -6,149 |
| ST7_st_sw8_05a | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5728/5285 | +31.4 | 55/60 | 0.46/0.47@1.1 | -1.49 [-3.0,-0.1] (2.1) | -1.39/-2.99 | -9,456 |
| ST7_st_sw8_1a | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5745/5275 | +31.2 | 57/60 | 0.48/0.48@1.1 | -1.33 [-2.7,+0.1] (2.0) | -1.20/-0.56 | -5,023 |
| ST7_st_hl_0 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 4533/4428 | +27.7 | 41/60 | 0.39/0.40@1.5 | -1.48 [-3.3,+0.4] (2.6) | -0.56/-5.64 | -4,947 |
| ST7_st_hl_10 | DEAD | mean_up,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5983/5818 | +34.7 | 42/60 | 0.41/0.42@1.4 | -0.87 [-2.4,+0.7] (2.3) | +0.66/-2.75 | -5,355 |
| ST7_st_hl_05a | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5084/4926 | +30.5 | 43/60 | 0.41/0.42@1.4 | -1.61 [-3.3,+0.2] (2.4) | -1.23/-6.99 | -6,182 |
| ST7_st_vw_0 | DEAD | mean_up,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 4740/4417 | +25.6 | 59/60 | 0.49/0.48@1.1 | -0.33 [-1.6,+1.0] (1.8) | +0.80/-1.82 | -2,458 |
| ST7_st_vw_10 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5221/4824 | +27.7 | 60/60 | 0.49/0.49@1.1 | -0.83 [-2.0,+0.4] (1.7) | -0.90/-1.38 | +2,711 |
| ST7_st_vw_05a | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 4852/4507 | +26.1 | 60/60 | 0.49/0.49@1.1 | -1.34 [-2.5,-0.2] (1.7) | -0.54/-1.64 | -4,556 |
| ST7_st_psl_0 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1330/1218 | +6.4 | 75/60 | 0.54/0.53@0.9 | -2.27 [-4.7,+0.2] (3.4) | -0.93/-2.84 | -3,940 |
| ST7_st_psl_5 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1262/1156 | +6.1 | 75/60 | 0.54/0.54@0.9 | -0.89 [-3.3,+1.8] (3.6) | -1.08/-2.66 | -2,978 |
| ST7_st_psl_05a | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1266/1158 | +6.0 | 75/60 | 0.54/0.54@0.9 | -1.63 [-4.2,+1.1] (3.7) | -1.80/-3.15 | -3,791 |
| ST7_st_psl_1a | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1206/1113 | +5.9 | 75/60 | 0.55/0.54@0.9 | -0.23 [-2.6,+2.1] (3.5) | -0.47/-2.07 | -1,452 |
| ST7_st_sw5_5_m15x90 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5852/5737 | +34.2 | 42/60 | 0.41/0.42@1.4 | -2.17 [-3.8,-0.6] (2.3) | -1.81/-2.42 | -8,995 |
| ST7_st_sw5_5_m20x120 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5856/5563 | +34.0 | 51/60 | 0.45/0.46@1.2 | -1.89 [-3.2,-0.6] (1.9) | -1.17/-3.43 | -9,292 |
| ST7_st_sig_5_r1 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5155/5091 | +32.5 | 30/30 | 0.51/0.55@0.8 | -4.92 [-6.9,-3.0] (2.7) | -6.78/-7.08 | -15,091 |
| ST7_st_sw5_5_r1 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6480/5783 | +34.6 | 47/47 | 0.51/0.53@0.9 | -2.41 [-3.8,-1.0] (2.0) | -1.60/-1.13 | -19,160 |
| ST7_st_sw8_5_r1 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6030/5087 | +29.9 | 53/53 | 0.51/0.52@0.9 | -2.50 [-4.0,-1.0] (2.1) | -2.18/-3.55 | -14,071 |
| ST7_st_hl_5_r1 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5297/5006 | +30.7 | 41/41 | 0.51/0.53@0.9 | -3.40 [-4.8,-1.8] (2.2) | -3.09/-4.03 | -19,475 |
| ST7_st_sw5_5_r2 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6480/4846 | +28.7 | 47/94 | 0.36/0.36@1.8 | -1.23 [-2.9,+0.5] (2.5) | -0.72/-0.30 | -8,498 |
| ST7_st_sw8_5_r2 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6030/4214 | +24.6 | 53/105 | 0.36/0.36@1.8 | -1.09 [-3.3,+1.0] (3.2) | -1.20/-3.90 | -7,004 |
| ST7_st_sw3_5_fix | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 7036/6812 | +41.3 | 43/60 | 0.41/0.42@1.4 | -0.92 [-1.9,+0.1] (1.4) | -0.73/-0.98 | -3,380 |

### SB8 (ST), prereg sha256 fcfb6829189ddbd5...
| cell | verdict | failed | valid/trades | tr/wk | stop/tgt mean | win obs/req @R (WF) | paired WF pts [CI] (MDE) | HOLD/2023 paired | WF wk $ d vs ctl |
|--|--|--|--|--|--|--|--|--|--|
| ST8_tg_poc | DEAD | holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,standalone<=beta(d),best_of_N_group,best_of_N_all180 | 508/489 | +4.1 | 60/62 | 0.58/0.64@0.6 | +0.09 [-3.9,+4.4] (6.0) | -0.49/-6.77 | +938 |
| ST8_tg_hvn | DEAD | placebo>=0.90,pairedCI&maxDD,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 3980/3194 | +19.3 | 60/86 | 0.51/0.53@0.9 | +0.62 [-1.2,+2.6] (2.8) | +0.84/+1.29 | -967 |
| ST8_tg_lvn | DEAD | placebo>=0.90,pairedCI&maxDD,SPAN2<=0,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 3959/3116 | +18.8 | 60/94 | 0.49/0.50@1.0 | +0.71 [-1.2,+2.8] (2.8) | +1.93/-2.77 | -738 |
| ST8_tg_rmid | DEAD | holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 639/639 | +4.7 | 60/29 | 0.69/0.72@0.4 | +0.28 [-2.6,+3.4] (4.4) | -0.35/+9.25 | +349 |
| ST8_tg_rh1 | DEAD | mean_up,placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 8202/5891 | +34.7 | 60/119 | 0.41/0.41@1.4 | -0.28 [-2.1,+1.4] (2.4) | +0.55/-0.39 | -3,832 |
| ST8_tg_sw2 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 3054/2976 | +18.9 | 60/52 | 0.54/0.58@0.7 | -1.16 [-2.4,+0.3] (1.9) | -0.47/-4.72 | +476 |
| ST8_tg_u1 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 7661/7024 | +42.4 | 60/46 | 0.64/0.65@0.5 | -0.76 [-1.8,+0.3] (1.5) | -0.25/-0.17 | -8,295 |
| ST8_tg_u2 | DEAD | mean_up,placebo>=0.90,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5763/4727 | +29.3 | 60/90 | 0.50/0.51@1.0 | -0.52 [-2.2,+1.1] (2.3) | +0.66/+1.04 | -3,413 |
| ST8_cb_sw5_pd | DEAD | mean_up,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 4385/2761 | +16.2 | 45/237 | 0.29/0.29@2.4 | -0.24 [-5.0,+5.2] (7.2) | +0.54/-2.05 | -987 |
| ST8_cb_sw5_fib1618 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6480/5330 | +31.8 | 47/68 | 0.43/0.44@1.3 | -1.91 [-3.5,-0.4] (2.2) | -1.00/-2.25 | -17,026 |
| ST8_cb_sw5_vp1 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1661/1518 | +9.8 | 49/61 | 0.50/0.53@0.9 | -1.38 [-4.5,+1.5] (4.2) | -0.55/-5.51 | -2,996 |
| ST8_cb_sw5_ropp | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 3756/3544 | +22.4 | 50/48 | 0.51/0.56@0.8 | -4.85 [-6.6,-2.9] (2.7) | -3.42/-4.39 | -15,352 |
| ST8_cb_sw5_fib10 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5856/5249 | +32.0 | 51/46 | 0.55/0.56@0.8 | -1.85 [-3.2,-0.4] (2.0) | -1.16/-4.50 | -17,226 |
| ST8_cb_sw5_va | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 2109/1935 | +12.4 | 48/60 | 0.48/0.53@0.9 | -3.05 [-5.7,-0.4] (3.9) | -1.99/+1.24 | -6,962 |
| ST8_cb_sw5_on | DEAD | placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1430/1160 | +6.8 | 56/117 | 0.43/0.46@1.2 | +1.09 [-3.3,+5.9] (6.5) | +0.78/-10.27 | -8 |
| ST8_cb_sw5_or | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 814/734 | +4.5 | 53/78 | 0.46/0.51@1.0 | -2.73 [-7.2,+2.2] (6.8) | -0.60/-9.78 | -2,932 |
| ST8_cb_sw5_hvn | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 3142/2635 | +16.1 | 46/87 | 0.44/0.45@1.2 | -1.09 [-4.0,+1.8] (4.2) | -1.15/-5.39 | -5,231 |
| ST8_cb_sw5_rh2 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6480/3949 | +22.9 | 46/211 | 0.25/0.25@3.0 | -1.24 [-4.5,+2.0] (4.7) | -2.47/-2.91 | -577 |
| ST8_cb_sw5_sw1 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 3785/3639 | +22.9 | 48/36 | 0.56/0.60@0.7 | -3.65 [-5.2,-2.0] (2.4) | -2.29/-7.89 | -17,522 |
| ST8_cb_sw5_vp2 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 4357/3712 | +22.7 | 48/81 | 0.43/0.45@1.2 | -4.33 [-6.6,-2.0] (3.2) | -2.05/-6.27 | -14,258 |
| ST8_cb_hl_u1 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 4835/4547 | +28.3 | 41/50 | 0.52/0.54@0.9 | -2.94 [-4.8,-1.0] (2.7) | -2.59/-8.21 | -15,515 |
| ST8_cb_hl_fib1618 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5257/4403 | +26.8 | 40/87 | 0.36/0.37@1.7 | -2.44 [-4.5,-0.3] (3.0) | -1.50/-3.45 | -9,896 |
| ST8_cb_hl_pd | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 3548/2461 | +14.9 | 38/261 | 0.25/0.25@3.0 | -1.73 [-6.8,+3.9] (7.7) | -0.85/-9.46 | -1,304 |
| ST8_cb_sig5_sw1 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 3389/3354 | +22.2 | 30/39 | 0.43/0.49@1.0 | -6.58 [-9.0,-4.5] (3.1) | -7.54/-2.42 | -15,476 |
| ST8_cb_sig5_u1 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 4843/4717 | +30.3 | 30/46 | 0.44/0.48@1.1 | -5.34 [-7.3,-3.3] (2.8) | -6.06/+0.64 | -15,300 |
| ST8_cb_sig5_fib10 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 4497/4191 | +26.7 | 30/69 | 0.35/0.36@1.8 | -2.42 [-5.0,+0.4] (3.7) | -3.60/-4.12 | -7,253 |
| ST8_dy_trail_sig5 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5155/4392 | +27.9 | 29/- | 0.27/0.27@2.7 | -0.55 [-4.0,+2.9] (5.1) | -0.43/-6.92 | +3,552 |
| ST8_dy_trail_hl5 | DEAD | mean_up,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5297/4503 | +27.4 | 39/- | 0.33/0.33@2.0 | -0.73 [-3.3,+2.1] (3.8) | +0.15/-7.14 | -1,755 |
| ST8_dy_brk_sig5 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5155/4361 | +27.7 | 29/- | 0.27/0.28@2.6 | -1.36 [-4.6,+1.9] (4.6) | -1.91/-6.10 | +242 |
| ST8_dy_trail_sw8 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6030/5396 | +31.7 | 52/- | 0.33/0.33@2.0 | -1.17 [-3.1,+1.1] (3.0) | -0.37/-4.71 | -9,936 |

### SB9 (KB), prereg sha256 b487b7224d88dee0...
| cell | verdict | failed | valid/trades | tr/wk | stop/tgt mean | win obs/req @R (WF) | paired WF pts [CI] (MDE) | HOLD/2023 paired | WF wk $ d vs ctl |
|--|--|--|--|--|--|--|--|--|--|
| KB7_st_sig_10 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 8051/7930 | +47.8 | 38/60 | 0.38/0.40@1.5 | -1.71 [-3.2,-0.4] (1.9) | -1.72/+1.76 | -8,969 |
| KB7_st_sig_05a | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 7138/6977 | +43.1 | 42/60 | 0.40/0.42@1.4 | -1.77 [-3.2,-0.5] (1.9) | -1.51/+1.07 | -4,796 |
| KB7_st_sig_1a | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 7532/7165 | +43.3 | 49/60 | 0.45/0.45@1.2 | -0.59 [-1.7,+0.4] (1.5) | -0.60/-2.04 | -3,420 |
| KB7_st_sw3_0 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 7023/6621 | +40.3 | 48/60 | 0.43/0.44@1.3 | -1.82 [-3.2,-0.6] (1.9) | -1.49/+0.02 | -7,114 |
| KB7_st_sw3_10 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 7776/7241 | +42.6 | 52/60 | 0.46/0.47@1.1 | -1.35 [-2.5,-0.3] (1.6) | -1.05/-0.27 | -15,480 |
| KB7_st_sw3_05a | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 7158/6618 | +39.6 | 53/60 | 0.46/0.47@1.1 | -1.53 [-2.7,-0.5] (1.5) | -1.27/-2.53 | -10,907 |
| KB7_st_sw5_0 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6999/6447 | +38.6 | 54/60 | 0.46/0.47@1.1 | -1.82 [-3.0,-0.8] (1.5) | -0.99/-1.27 | -9,078 |
| KB7_st_sw8_0 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6805/6057 | +35.7 | 59/60 | 0.49/0.49@1.0 | -1.39 [-2.5,-0.3] (1.6) | -1.49/-1.30 | -12,615 |
| KB7_st_sw8_10 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6841/5973 | +34.3 | 63/60 | 0.52/0.51@0.9 | -0.90 [-1.9,+0.1] (1.4) | -0.93/+0.08 | -10,676 |
| KB7_st_sw8_05a | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6454/5653 | +32.8 | 62/60 | 0.51/0.50@1.0 | -1.59 [-2.8,-0.6] (1.6) | -2.09/-0.37 | -11,472 |
| KB7_st_sw8_1a | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5966/5160 | +29.4 | 66/60 | 0.52/0.52@0.9 | -0.80 [-1.9,+0.2] (1.5) | -0.68/-0.25 | -8,272 |
| KB7_st_hl_0 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6735/6491 | +39.9 | 45/60 | 0.42/0.43@1.3 | -1.26 [-2.6,+0.1] (1.9) | -1.09/+0.21 | -8,289 |
| KB7_st_hl_10 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 7865/7482 | +44.4 | 48/60 | 0.44/0.45@1.2 | -1.31 [-2.6,-0.2] (1.7) | -0.70/-0.03 | -12,702 |
| KB7_st_hl_05a | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 7216/6781 | +40.9 | 50/60 | 0.45/0.45@1.2 | -0.96 [-2.2,+0.1] (1.7) | -0.58/-3.33 | -12,075 |
| KB7_st_vw_0 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 4217/4039 | +23.5 | 58/60 | 0.47/0.47@1.1 | -1.45 [-2.9,-0.0] (2.1) | -0.65/+1.36 | -531 |
| KB7_st_vw_10 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 4653/4334 | +25.0 | 60/60 | 0.47/0.48@1.1 | -1.37 [-2.8,+0.0] (2.0) | -1.06/+0.87 | -4,523 |
| KB7_st_vw_05a | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 4401/4094 | +23.8 | 61/60 | 0.48/0.49@1.0 | -1.55 [-3.0,-0.2] (2.0) | -0.83/-0.09 | -2,243 |
| KB7_st_psl_0 | DEAD | mean_up,placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1646/1513 | +8.0 | 70/60 | 0.50/0.53@0.9 | -0.87 [-3.3,+1.6] (3.5) | +0.03/-4.53 | -850 |
| KB7_st_psl_5 | DEAD | placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1592/1468 | +7.7 | 70/60 | 0.51/0.53@0.9 | +0.13 [-2.3,+2.5] (3.5) | +1.42/-1.20 | -1,865 |
| KB7_st_psl_05a | DEAD | placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1554/1437 | +7.5 | 71/60 | 0.51/0.53@0.9 | +0.51 [-2.0,+3.1] (3.7) | +2.63/-2.73 | -1,104 |
| KB7_st_psl_1a | DEAD | placebo>=0.90,neighbours_agree,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1448/1349 | +7.0 | 71/60 | 0.51/0.54@0.9 | +0.12 [-2.2,+2.4] (3.3) | +0.14/+0.20 | -2,123 |
| KB7_st_sw5_5_m15x90 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6229/5970 | +34.6 | 48/60 | 0.44/0.45@1.2 | -2.23 [-3.5,-1.1] (1.7) | -1.70/-1.62 | -13,079 |
| KB7_st_sw5_5_m20x120 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6900/6281 | +37.6 | 58/60 | 0.48/0.49@1.1 | -1.65 [-2.6,-0.7] (1.4) | -1.02/-2.17 | -12,155 |
| KB7_st_sig_5_r1 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 7020/6778 | +41.8 | 36/36 | 0.50/0.54@0.9 | -4.04 [-5.5,-2.6] (2.0) | -3.69/-1.43 | -24,559 |
| KB7_st_sw5_5_r1 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 7326/6040 | +35.3 | 55/55 | 0.51/0.51@1.0 | -2.10 [-3.4,-0.8] (1.9) | -2.14/-0.83 | -15,576 |
| KB7_st_sw8_5_r1 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6905/5402 | +31.1 | 60/60 | 0.51/0.51@1.0 | -2.17 [-3.6,-0.8] (2.0) | -1.75/-0.46 | -17,170 |
| KB7_st_hl_5_r1 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 7414/6704 | +40.4 | 45/45 | 0.51/0.52@0.9 | -2.19 [-3.7,-0.9] (2.0) | -2.13/-1.21 | -17,650 |
| KB7_st_sw5_5_r2 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 7326/4731 | +27.2 | 54/107 | 0.35/0.35@1.8 | -1.98 [-4.1,+0.0] (2.9) | -2.86/-3.30 | -7,039 |
| KB7_st_sw8_5_r2 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6905/4212 | +23.7 | 58/116 | 0.37/0.36@1.8 | -0.09 [-2.2,+1.9] (3.0) | -0.30/-2.71 | -3,677 |
| KB7_st_sw3_5_fix | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 7536/7075 | +42.3 | 50/60 | 0.44/0.45@1.2 | -0.76 [-1.8,+0.2] (1.4) | -0.45/+0.35 | -7,654 |

### SB10 (KB), prereg sha256 5a38d742b3c577ca...
| cell | verdict | failed | valid/trades | tr/wk | stop/tgt mean | win obs/req @R (WF) | paired WF pts [CI] (MDE) | HOLD/2023 paired | WF wk $ d vs ctl |
|--|--|--|--|--|--|--|--|--|--|
| KB8_tg_poc | DEAD | mean_up,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1064/964 | +6.2 | 60/99 | 0.48/0.50@1.0 | -0.83 [-4.5,+3.1] (5.6) | +0.66/-5.05 | +647 |
| KB8_tg_hvn | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 4902/3826 | +22.9 | 60/96 | 0.49/0.50@1.0 | -0.01 [-2.0,+2.2] (3.1) | -0.53/+2.16 | -3,624 |
| KB8_tg_lvn | DEAD | placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 4762/3601 | +21.6 | 60/107 | 0.48/0.47@1.1 | +1.24 [-1.0,+3.5] (3.1) | +1.92/-0.76 | -1,184 |
| SB_KB8_tg_rmid | DEAD | too few valid events |  |  |  |  |  |  |  |
| KB8_tg_rh1 | DEAD | placebo>=0.90,neighbours_agree,pairedCI&maxDD,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 8505/6061 | +35.5 | 60/108 | 0.42/0.42@1.4 | +1.13 [-0.3,+2.6] (2.0) | +1.46/+0.18 | -2,840 |
| KB8_tg_sw2 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 3327/3103 | +18.7 | 60/59 | 0.53/0.56@0.8 | -2.07 [-3.5,-0.7] (2.0) | -1.84/-1.60 | -3,527 |
| KB8_tg_u1 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 7883/7160 | +43.1 | 60/49 | 0.62/0.64@0.6 | -1.49 [-2.7,-0.4] (1.6) | -0.41/+0.73 | -7,815 |
| KB8_tg_u2 | DEAD | mean_up,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6139/4581 | +27.9 | 60/109 | 0.46/0.47@1.1 | -0.42 [-2.1,+1.2] (2.4) | +0.65/-1.00 | -3,290 |
| KB8_cb_sw5_pd | DEAD | placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5273/2820 | +16.0 | 52/272 | 0.31/0.29@2.5 | +2.03 [-2.7,+6.7] (6.4) | +3.39/-4.35 | -4,122 |
| KB8_cb_sw5_fib1618 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 7326/5280 | +30.7 | 54/79 | 0.42/0.43@1.3 | -2.48 [-4.3,-0.9] (2.4) | -3.40/-1.61 | -14,231 |
| KB8_cb_sw5_vp1 | DEAD | mean_up,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 2376/1857 | +11.1 | 62/100 | 0.47/0.48@1.1 | -1.01 [-3.7,+1.9] (3.9) | +0.53/-5.53 | -690 |
| KB8_cb_sw5_ropp | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 2242/2165 | +13.6 | 66/30 | 0.68/0.71@0.4 | -3.57 [-5.6,-1.6] (2.8) | -2.97/-3.48 | -10,039 |
| KB8_cb_sw5_fib10 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6900/5748 | +34.2 | 57/52 | 0.54/0.54@0.9 | -1.73 [-3.1,-0.5] (1.9) | -1.53/-0.75 | -12,909 |
| KB8_cb_sw5_va | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 2579/2038 | +12.3 | 62/97 | 0.50/0.51@1.0 | -2.11 [-5.0,+0.5] (3.9) | -1.58/-1.93 | -4,315 |
| KB8_cb_sw5_on | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1828/1271 | +7.1 | 71/159 | 0.45/0.46@1.2 | -2.19 [-5.9,+1.5] (5.4) | -1.01/-7.20 | -2,834 |
| KB8_cb_sw5_or | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 1193/953 | +5.4 | 69/119 | 0.48/0.50@1.0 | -4.69 [-8.6,-0.8] (5.6) | -2.07/-5.66 | -2,584 |
| KB8_cb_sw5_hvn | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 4177/3261 | +19.4 | 55/92 | 0.45/0.47@1.1 | -2.96 [-5.5,-0.5] (3.5) | -1.50/-0.69 | -10,277 |
| KB8_cb_sw5_rh2 | DEAD | holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 7326/4010 | +22.6 | 53/185 | 0.29/0.28@2.5 | +0.32 [-3.0,+3.6] (4.7) | -0.12/-5.25 | +1,512 |
| KB8_cb_sw5_sw1 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 3957/3650 | +22.1 | 60/37 | 0.61/0.64@0.6 | -2.66 [-4.3,-1.0] (2.4) | -2.17/-4.19 | -12,911 |
| KB8_cb_sw5_vp2 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 4649/3313 | +19.9 | 60/105 | 0.48/0.48@1.1 | -2.73 [-5.2,-0.5] (3.4) | -1.12/-5.25 | -6,376 |
| KB8_cb_hl_u1 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6859/6253 | +38.1 | 47/49 | 0.53/0.57@0.8 | -3.12 [-5.0,-1.3] (2.6) | -2.21/-5.90 | -18,953 |
| KB8_cb_hl_fib1618 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 7389/5448 | +32.4 | 44/93 | 0.36/0.37@1.7 | -2.03 [-4.0,-0.0] (2.9) | -2.94/-2.13 | -12,310 |
| KB8_cb_hl_pd | DEAD | placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 5321/2949 | +17.2 | 43/284 | 0.27/0.25@3.1 | +1.49 [-3.6,+6.2] (7.0) | +0.71/-10.83 | -2,162 |
| KB8_cb_sig5_sw1 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 3997/3894 | +24.8 | 37/40 | 0.48/0.53@0.9 | -4.34 [-6.3,-2.5] (2.8) | -3.50/-1.99 | -11,005 |
| KB8_cb_sig5_u1 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6525/6167 | +38.5 | 37/49 | 0.47/0.52@0.9 | -4.71 [-6.9,-2.9] (2.7) | -4.02/-2.16 | -13,753 |
| KB8_cb_sig5_fib10 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6843/6034 | +37.1 | 36/68 | 0.37/0.39@1.6 | -1.12 [-2.9,+0.9] (2.7) | -1.20/+0.52 | -2,610 |
| KB8_dy_trail_sig5 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 7020/5956 | +36.5 | 36/- | 0.32/0.32@2.1 | -0.97 [-3.3,+1.3] (3.3) | -1.20/-4.14 | -9,975 |
| KB8_dy_trail_hl5 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 7414/6297 | +37.7 | 46/- | 0.34/0.36@1.8 | -1.60 [-3.6,+0.1] (2.7) | -0.72/-5.52 | -15,992 |
| KB8_dy_brk_sig5 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 7020/5900 | +36.1 | 36/- | 0.31/0.33@2.0 | -2.49 [-4.7,-0.4] (3.1) | -2.29/-4.88 | -9,470 |
| KB8_dy_trail_sw8 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,pairedCI&maxDD,SPAN2<=0,2x_cost<=0,year_share>60%,beats_(b)_CI_includes_0,best_of_N_group,best_of_N_all180 | 6905/6106 | +35.5 | 61/- | 0.36/0.37@1.7 | -1.88 [-3.5,-0.4] (2.2) | -0.94/-1.35 | -12,890 |


## 8. Method and disclosures
- Identity: the runner reproduces the library 60/60 rows of all 8 entry bases (ST 8,309; HM 6,311; KB 8,593; SM 2,397; EM 2,335; PB3B_R5_P1 8,339; PB3B_R60_P2 6,580; PRO2_ER4_EMA5 1,522) with identical points in every trade (out/SB/identity_audit.json). As-of: every level uses bars <= ei-1 (fractal swings confirmed at j+L, PRO2 level series as-of the completed bar, prior-session/OR/range arrays); no formal truncation test was run (levels re-use audited sf_lib/PRO2/FM code), disclosed.
- Conservative basis: raw + 0.5 + min(P9 correction, 0) - $4.84/lot - s113 sweep surcharge above 14 lots; no stop-join credit; mapped numbers never cited. Equal-risk lots clip(round(12000/(stop x 20)),1,42); the 50-lot concurrency replay and the direct L2 replay were NOT run (no finalist; the cells are 1-s-path structural brackets).
- The signal list of each family is the list taken under its own 60/60 sequence; signals skipped while a 60/60 trade was open are not available, so a cell that exits earlier cannot re-enter on them (cells re-sequence with their own exits; pairing on common events; the attrition is in the valid/trades column).
- Placebo (b) permutes the cell's stop/target distances across valid events (real levels replaced by the same distance distribution); (a) timing destroyed, (c) random time of day on the same label days, (d) random direction (beta); (a),(c),(d) were skipped when the PRE paired effect <= 0 (rank counted as failed). Best-of-N: inverse-transform null from the (b) draws, N_total 180 (as stated in the SB1-SB6 preregs) and 300; per-group and per-class nulls reported.
- Directive options NOT scored: the pullback-origin and sweep-extreme stops for non-pullback/non-sweep families (n/a), the HVN/LVN/POC stops, prior-session targets other than pd (overnight, OR, POC, HVN, LVN appear as targets in SB8/SB10 for ST/KB only), the measured move as a separate cell (it equals fib 1.0), second-level targets for every level type (only the union u2 and sw2), L=3/8 trail variants, STRUCT-FIB and SBS resting-limit entries (mapped-only limits), min 20/max 90 on every cell (reported as a subset sensitivity r['pair_min20max90'] and two explicit cells), families TE1*/TE3*/TE6*/TE7* other than KB/SM/EM, PB3D/PB3E/PB3F. Fixed-lots version only for two stop cells per family.
- Holdout discipline: one logged look per prereg group (10 groups + 10 second-holdout looks), logged before any HOLD/2023 value was printed; before the preregs one ST smoke test printed all-window results of three configurations (see DECISIONS.md); the SB1-SB6 runs were repeated once (identical code except an added 2x-cost control field) before the looks; chain.done of the first run renamed chain.done.killed_firstrun. Verdict extras (SPAN2, 2x-cost vs control, year share, beats (b), standalone > beta, group best-of-N) are counted as failures like in T-H item 3.
- Ledger: +300 cells (67,933 -> 68,203 after the SB preregs).
