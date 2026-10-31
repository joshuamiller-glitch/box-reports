# DS3_CAPPED_RERUN - capped re-score (<= 2026-02-06) of the DS-1 priority programs and the leaderboard rows (RR-A, 2026-10-31)

Stored-series re-reads only: no new strategy search, UNTOUCHED never read, shared libraries (`s48score.py`, `vs_lib.py`) NOT edited. Copy-based capped library `l2vast/ds3/code/cappedrerun/cap_lib.py` (HOLD 20250701..20260206 = 32 wk, WF 20240201..20260206 = 106 wk, L6M 20250801..20260206, PRE 20240201..20250630 = 75 wk, X' 20230401..20240131 = 44 wk, L8W = last 8 weeks to 2026-02-06). Outputs: `l2vast/ds3/out/cappedrerun/` (per-program CSVs, TIER_CHANGES_ALL.csv, SUMMARY_counts.csv); code `l2vast/ds3/code/cappedrerun/`.

## PAGE 1 - tier changes under the cap

**103 rows change tier: 41 UP, 62 DOWN.** The cap cuts both ways. DOWN is dominated by CANDIDATE rows that failed only the placebo or SPAN2 and now also fail WF CI>0 (no slack left); UP is dominated by rows that failed only WF CI/HOLD because the 36 post-cut weeks were weak (TA1 regime-gated cells, TPULLBACK/TR2 thin-CI rows). Almost no sign reversals: the moves are thin-CI (t 1.2 to 2.7), not collapses. Net PASS+CANDIDATE count: roughly flat in the pullback/trend files, falls in PRO1/PRO2 and in the struct48 LEADERBOARD PASS tier (18 PASS -> 5 PASS), rises in TA1.

| program (report / leaderboard) | rows tiered | PASS orig -> capped | CANDIDATE orig -> capped | UP | DOWN | not tiered (no series) |
|---|---|---|---|---|---|---|
| PRO1 | 108 | 3 -> 2 | 19 -> 10 | 3 | 14 | 9 |
| PRO2 | 104 | 3 -> 2 | 13 -> 7 | 1 | 9 | 0 |
| TA1 | 76 | 2 -> 7 | 6 -> 10 | 11 | 2 | 44 |
| PRO3 | 42 | 2 -> 2 | 2 -> 6 | 4 | 1 | 3 |
| TPULLBACK | 157 | 16 -> 17 | 24 -> 21 | 7 | 8 | 0 |
| TPULLBACK2 | 52 | 0 -> 0 | 2 -> 3 | 1 | 0 | 0 |
| TPULLBACK4 | 177 | 13 -> 11 | 15 -> 16 | 2 | 5 | 0 |
| TR1 | 133 | 2 -> 2 | 6 -> 3 | 0 | 3 | 1 |
| TR2 | 74 | 12 -> 12 | 14 -> 17 | 5 | 2 | 0 |
| LEADERBOARD.md (struct48: T3/NM/T1/T4) | 46 | 18 -> 5 | 28 -> 37 | 7 | 18 | 0 |
| TCHOP block 0 (13) / CHOP_FINAL (274 cells, 26 CANDIDATE) | 13 / 274 | 0 -> 0 | 0 / 26 -> 26 | 0 | 0 | G4/G5/G6 carried (needs stack engine) |
| XT exits (DS3_TC1C2/TC3C4/TC4R4/TC5, 246 v2 cells) | 246 | 0 -> 0 | 0 -> 0 | 0 | 0 | weekly proxy only (paired-pts gates carried) |
| STACK_D (9 cells) | 9 | - | - | 0 | 0 | all DEAD, stay DEAD |
| DIV_VOLGATE (21 cells) | 21 | - | - | 0 | 0 | all DEAD, stay DEAD |
| CONFIRM_B / CONFIRM_FINAL | 24 + 3 | - | - | 0 | 0 | same 4 T-basis cells pass; 0 of 24 pass both bases |
| DIV2_A_AUDIT | descriptive | - | - | - | - | no tiers; statistics recomputed |
| BRACKET_LEADERBOARD | 0 PASS / 0 CANDIDATE | - | - | 0 | 0 | 9 PENDING_DIRECT + DEAD: nothing to change |
| PULLBACK_LEADERBOARD extra (TPULLBACK3 141, TPBX ~500) | - | - | 17 CAND (TPULLBACK3) | 0 | 0 | trade-paired s48 gates: capped absolute stats only, tier carried |

Counts in the table are on the rows each CSV could tier, not the leaderboard headline totals (the leaderboards merge duplicates, mapped/direct). The LEADERBOARD.md row also gets +6 UP from a scan of 213 DEAD sleeve/NM rows (T3.2 ORB_NY_15_v0, holdout turns positive when capped; they fail only year_share).

### Five things to know before reading further
1. **DS-1's XT claim ("replay variants median WF +4.4k -> -0.1k") rests on INVALID v1 series.** `SERIES/XT_*.parquet` (written 2026-10-27 12:30Z) are the v1 pricing-bug run: their X' window mean is +285k/wk where the valid v2 rows say +2.1k. The valid v2 daily series (`ds3/out/tcx/score_*_final_v.pkl`, `_daily_r/_daily_b`) were re-scored here: all 246 cells stay DEAD, capped delta-vs-bracket WF>0 in 85 of 246 (91 uncapped), HOLD>0 in 86 (100), capped WF t>=2 in 3 cells, HOLD t>=2 in 1. The DS-1 XT sentence should be struck.
2. **The struct48 PASS -> CANDIDATE moves are mostly the year-share gate, a mechanical effect of truncation.** Cutting 36 weeks of 2026 raises the 2025 share of the gain (ORB Asia 15 s60 0.52 -> 0.65; s75 ~0.48 -> 0.73) while capped d_mean and holdout d are mostly higher than uncapped. See section 3.
3. **Gates recomputed vs carried.** Recomputed from stored series on the capped windows: WF CI>0 (week-block bootstrap, same seed/draws as `S48.boot_ci`), HOLD>0, x2_WF>0 (APPROXIMATION everywhere: capped WF mean minus the stored per-week 2x-cost drag of the original run; stored 2x series were not used), standalone/sleeve stats, year share, marginal-Sharpe sign, MDE (106 wk). Carried as stored (flagged): placebo ranks, tpw, PRE and SPAN2 (bounded windows; verified: recomputed PRE and X' equal the stored values on every tiered row), DSR, trade-level paired CIs, `dST_wf>0` (PRO1, 6 rows), neighbours.
4. **Reproduction check.** Stored daily series are full length; uncapped WF/HOLD were NOT reloaded to reproduce stored numbers (that would be reading post-cut data). Instead the bounded PRE and X' windows reproduce the stored numbers to the dollar for every tiered row (PRO1 108/108, PRO2 104/104, TA1 76/76, XT 246/246, CHOP 274/274, STACK_D, VOLGATE, CONFIRM_A/B, struct48 sleeve k to 10 digits). Live-book uncapped figures are the pool's stored ones, reproduced earlier by DS-1.
5. **Disclosure.** Stored per-cell daily files contain post-cut rows, so they are read and sliced at load (`cap_lib.sl`); nothing after 2026-02-06 was inspected or kept. One early listing pass of fork B imported the real `s48score` (loads Set A to 2026-10-16 into memory); no value past 2026-02-06 was looked at.

## 1. Every row whose tier changes (capped vs original)

Columns: program, cell, tier original -> capped, failed gates original -> capped, capped WF $/wk (t), capped HOLD $/wk (t). Capped tier uses the same gate rules as the original program (T-ENTRY/D3 rule: PASS = no failed gate, CANDIDATE = one, DEAD = two or more; struct48 6-condition rule for LEADERBOARD rows; for the LB- rows the dollars are the sleeve's own capped sizing d). TA1 up-moves have no WF CI>0 / HOLD>0 failure left but keep carried placebo/x2 as stored.

| program | cell | tier | failed gates | WF (t) | HOLD (t) |
|---|---|---|---|---|---|
| LB-NM_B | B01_SetB | CANDIDATE -> PASS | mean_not_down&(SD|maxDD down with CI) OR mean_up&maxDD_not_worse -> - | 9,943 | 9,518 |
| LB-T3.2 (DEAD scan) | ORB_NY_15_v0__s60@0.25 | DEAD -> CANDIDATE | (DEAD, uncapped) -> year_share>60% | 6,335 | 1,396 |
| LB-T3.2 (DEAD scan) | ORB_NY_15_v0__s60@0.5 | DEAD -> CANDIDATE | (DEAD, uncapped) -> year_share>60% | 12,670 | 2,791 |
| LB-T3.2 (DEAD scan) | ORB_NY_15_v0__s60@1.0 | DEAD -> CANDIDATE | (DEAD, uncapped) -> year_share>60% | 25,340 | 5,583 |
| LB-T3.2 (DEAD scan) | ORB_NY_15_v0__s75@0.25 | DEAD -> CANDIDATE | (DEAD, uncapped) -> year_share>60% | 4,922 | 427 |
| LB-T3.2 (DEAD scan) | ORB_NY_15_v0__s75@0.5 | DEAD -> CANDIDATE | (DEAD, uncapped) -> year_share>60% | 9,844 | 855 |
| LB-T3.2 (DEAD scan) | ORB_NY_15_v0__s75@1.0 | DEAD -> CANDIDATE | (DEAD, uncapped) -> year_share>60% | 19,687 | 1,710 |
| PRO1 | PRO1_AGG_RL5_ST10_VWAP | DEAD -> CANDIDATE | WF_CI>0,HOLD>0,x2_WF>0 -> WF_CI>0 | 6,251 (1.7) | 4,045 (0.6) |
| PRO1 | PRO1_IMB_K3_ST10_SWZ | DEAD -> CANDIDATE | WF_CI>0,plc>=.95 -> plc>=.95 | 11,367 (2.3) | 21,565 (2.0) |
| PRO1 | PRO1_LPC_C100_EMA200_SWZ | DEAD -> CANDIDATE | WF_CI>0,SPAN2>0 -> SPAN2>0 | 6,834 (1.9) | 12,123 (2.6) |
| PRO2 | PRO_ST10_dPOC_T1_2nd | DEAD -> CANDIDATE | WF_CI>0,plc>=.95 -> plc>=.95 | 9,710 (2.2) | 18,010 (2.2) |
| PRO3 | PRO3A_A1 | DEAD -> CANDIDATE | WF_CI>0,HOLD>0 -> WF_CI>0 | 7,062 (1.8) | 6,924 (1.1) |
| PRO3 | PRO3A_A1P3 | DEAD -> PASS | WF_CI>0,HOLD>0 -> - | 7,621 (2.5) | 2,443 (0.6) |
| PRO3 | PRO3A_A1X25 | DEAD -> CANDIDATE | WF_CI>0,HOLD>0 -> WF_CI>0 | 5,152 (1.5) | 4,579 (0.8) |
| PRO3 | PRO3A_X20 | DEAD -> CANDIDATE | WF_CI>0,HOLD>0 -> WF_CI>0 | 8,200 (1.6) | 6,560 (0.7) |
| TA1 | TE1_st_10m|quiet | DEAD -> PASS | WF_CI>0,HOLD>0 -> - | 4,554 (2.0) | 2,438 (1.0) |
| TA1 | TE2_big_w5_q0.98|wide | DEAD -> PASS | WF_CI>0,HOLD>0 -> - | 6,614 (2.5) | 5,964 (1.4) |
| TA1 | TE3_ice_follow_lb30_q0.95|wide | DEAD -> CANDIDATE | WF_CI>0,SPAN2>0 -> SPAN2>0 | 7,904 (2.3) | 12,934 (2.2) |
| TA1 | TE3_ofi_w1_q0.99|wide | DEAD -> PASS | WF_CI>0,HOLD>0 -> - | 9,828 (2.4) | 5,545 (0.6) |
| TA1 | TE3_ofi_w3_q0.99|wide | DEAD -> PASS | WF_CI>0,HOLD>0 -> - | 12,845 (4.0) | 1,759 (0.3) |
| TA1 | TE3_ofi_w5_q0.97|wide | DEAD -> PASS | WF_CI>0,HOLD>0 -> - | 10,383 (2.7) | 1,223 (0.2) |
| TA1 | TE3_vpin_n20_q0.95|quiet | DEAD -> CANDIDATE | WF_CI>0,HOLD>0,SPAN2>0 -> SPAN2>0 | 6,068 (2.9) | 4,838 (1.3) |
| TA1 | TE4_vwb_k1.5_ny|wide | DEAD -> CANDIDATE | WF_CI>0,HOLD>0,SPAN2>0 -> SPAN2>0 | 7,026 (2.3) | 6,226 (0.9) |
| TA1 | TE6_st10m_n14_m3.0|quiet | DEAD -> CANDIDATE | WF_CI>0,HOLD>0 -> WF_CI>0 | 3,236 (1.5) | 1,030 (0.4) |
| TA1 | TE7_emax5m_f15_s40|quiet | DEAD -> CANDIDATE | WF_CI>0,HOLD>0,SPAN2>0 -> SPAN2>0 | 4,812 (2.4) | 252 (0.1) |
| TA1 | TE7_emax5m_f20_s50|wide | DEAD -> CANDIDATE | WF_CI>0,SPAN2>0 -> SPAN2>0 | 7,850 (2.5) | 16,024 (2.7) |
| TPULLBACK | PB6_ST3m_EMA20_2m_T1 | DEAD -> CANDIDATE | WF_CI>0,SPAN2>0 -> SPAN2>0 | 12,201 (2.3) | 18,337 (2.1) |
| TPULLBACK | PB6_ST60m_EMA20_2m_T1 | CANDIDATE -> PASS | WF_CI>0 -> - | 11,281 (2.0) | 19,779 (1.8) |
| TPULLBACK | PB6_ST60m_EMA20_5m_T1 | DEAD -> CANDIDATE | WF_CI>0,HOLD>0 -> WF_CI>0 | 7,185 (1.5) | 5,457 (0.6) |
| TPULLBACK | PB7_PB6_ST60m_EMA20_3m_T1_W15_s+0 | DEAD -> CANDIDATE | WF_CI>0,plc>=.95 -> plc>=.95 | 9,889 (2.0) | 19,341 (2.3) |
| TPULLBACK | PB7_PB6_ST60m_EMA20_3m_T1_W60_s+0 | CANDIDATE -> PASS | WF_CI>0 -> - | 11,578 (2.3) | 20,105 (2.2) |
| TPULLBACK | PB7_PB_ST10_SWZ_T1_W30_s+3 | DEAD -> CANDIDATE | WF_CI>0,plc>=.95 -> plc>=.95 | 12,602 (2.5) | 31,265 (2.9) |
| TPULLBACK | PB_HMA55_SWZ_T1 | CANDIDATE -> PASS | WF_CI>0 -> - | 13,999 (2.7) | 17,858 (2.1) |
| TPULLBACK2 | PB2B_B2_SC2_T30_i62 | DEAD -> CANDIDATE | WF_CI>0,HOLD>0 -> WF_CI>0 | 3,599 (1.3) | 3,831 (0.8) |
| TPULLBACK4 | TB4B_tick_21_tick_1000_ST5_E20_1_T2 | DEAD -> CANDIDATE | WF_CI>0,HOLD>0,x2_WF>0 -> WF_CI>0 | 6,808 (1.4) | 5,087 (0.7) |
| TPULLBACK4 | TB4C_range_19_range_60_ST3_SW62_T1 | DEAD -> CANDIDATE | WF_CI>0,SPAN2>0 -> SPAN2>0 | 11,432 (2.4) | 13,002 (1.5) |
| TR2 | TR3_DON15_FH | DEAD -> CANDIDATE | WF_CI>0,HOLD>0 -> HOLD>0 | 4,958 (2.0) | -4,062 (-1.0) |
| TR2 | TR3_KB_C2 | DEAD -> CANDIDATE | WF_CI>0,SPAN2>0 -> SPAN2>0 | 10,555 (2.0) | 1,109 (0.1) |
| TR2 | TR3_KB_RTH15 | DEAD -> CANDIDATE | WF_CI>0,plc>=.95 -> plc>=.95 | 9,923 (2.1) | 7,866 (0.9) |
| TR2 | TR3_KB_RTH5 | CANDIDATE -> PASS | WF_CI>0 -> - | 10,092 (1.9) | 2,340 (0.3) |
| TR2 | TRW_kelt3m_n30_m2.0_RT15 | DEAD -> CANDIDATE | WF_CI>0,HOLD>0,SPAN2>0 -> SPAN2>0 | 12,985 (2.4) | 4,635 (0.4) |
| LB-NM_D | T14_S_s50_t1.5_n14 | CANDIDATE -> DEAD | neighbours_agree;paired_CI_excludes0&maxDD_not_worse;placebo<0.95;year_share>60% -> holdout_sign_agrees;neighbours_agree;paired_CI_excludes0&maxDD_not_worse;placebo<0.95;year_share>60% | 2,807 | -10,615 |
| LB-NM_E | E:ES_RSI2_t10 | PASS -> CANDIDATE | - -> year_share>60% | 5,502 | 7,262 |
| LB-NM_E | E:GSHORT_t90 | PASS -> CANDIDATE | - -> year_share>60% | 3,182 | 6,488 |
| LB-NM_E | E:NQ_IBS_t20_n1 | CANDIDATE -> DEAD | placebo<0.95 -> placebo<0.95;year_share>60% | 3,720 | 5,314 |
| LB-NM_E | E:NQ_RSI2_t10 | PASS -> CANDIDATE | - -> year_share>60% | 4,778 | 4,834 |
| LB-NM_E | E:ORB_ASIA_15_v1_s60 | PASS -> CANDIDATE | - -> year_share>60% | 4,401 | 9,477 |
| LB-NM_E | E:ORB_ASIA_15_v1_s75 | PASS -> CANDIDATE | - -> year_share>60% | 3,777 | 10,863 |
| LB-T1 | T14_S_s50_t1.5_n14 | CANDIDATE -> DEAD | neighbours_agree;paired_CI_excludes0&maxDD_not_worse;placebo<0.95;year_share>60% -> holdout_sign_agrees;neighbours_agree;paired_CI_excludes0&maxDD_not_worse;placebo<0.95;year_share>60% | 2,759 | -10,615 |
| LB-T3.2 | ORB_ASIA_15_v1__s60@0.25 | PASS -> CANDIDATE | - -> year_share>60% | 4,401 | 9,477 |
| LB-T3.2 | ORB_ASIA_15_v1__s60@0.5 | PASS -> CANDIDATE | - -> year_share>60% | 8,802 | 18,954 |
| LB-T3.2 | ORB_ASIA_15_v1__s60@1.0 | PASS -> CANDIDATE | - -> year_share>60% | 17,605 | 37,907 |
| LB-T3.2 | ORB_ASIA_15_v1__s75@0.25 | PASS -> CANDIDATE | - -> year_share>60% | 3,777 | 10,863 |
| LB-T3.2 | ORB_ASIA_15_v1__s75@0.5 | PASS -> CANDIDATE | - -> year_share>60% | 7,553 | 21,726 |
| LB-T3.2 | ORB_ASIA_15_v1__s75@1.0 | PASS -> CANDIDATE | - -> year_share>60% | 15,106 | 43,451 |
| LB-T3.6b1 | RSI2_t10 | PASS -> CANDIDATE | - -> year_share>60% | 9,555 | 9,667 |
| LB-T3.7b4 | IBS_t20_n1 | CANDIDATE -> DEAD | placebo<0.95 -> placebo<0.95;year_share>60% | 7,440 | 10,628 |
| LB-T3.8A | ES_RSI2_t10 | PASS -> CANDIDATE | - -> year_share>60% | 11,004 | 14,523 |
| LB-T3.8B | GSHORT_t90 | PASS -> CANDIDATE | - -> year_share>60% | 6,363 | 12,976 |
| PRO1 | PRO1_ABS_R10_EMA200_EMA5 | CANDIDATE -> DEAD | WF_CI>0 -> WF_CI>0,HOLD>0 | 5,433 (1.4) | -3,877 (-0.5) |
| PRO1 | PRO1_ABS_R12_EMA200_EMA5 | PASS -> CANDIDATE | - -> WF_CI>0 | 4,815 (1.5) | 2,023 (0.3) |
| PRO1 | PRO1_ABS_R12_EMA200_SWZ | CANDIDATE -> DEAD | plc>=.95 -> plc>=.95,WF_CI>0 | 4,850 (1.5) | 2,399 (0.4) |
| PRO1 | PRO1_ABS_V25_EMA200_SWZ | CANDIDATE -> DEAD | plc>=.95 -> plc>=.95,WF_CI>0 | 4,235 (1.0) | 2,794 (0.4) |
| PRO1 | PRO1_AGG_CD2_EMA200_SWZ | CANDIDATE -> DEAD | plc>=.95 -> plc>=.95,WF_CI>0 | 10,186 (1.9) | 27,180 (2.9) |
| PRO1 | PRO1_AGG_CD3_EMA200_SWZ | CANDIDATE -> DEAD | plc>=.95 -> plc>=.95,WF_CI>0 | 8,070 (1.6) | 26,635 (2.9) |
| PRO1 | PRO1_AGG_RL3_EMA200_SWZ | CANDIDATE -> DEAD | plc>=.95 -> plc>=.95,WF_CI>0 | 7,360 (1.6) | 10,177 (1.4) |
| PRO1 | PRO1_AGG_RL3_ST10_SWZ | CANDIDATE -> DEAD | plc>=.95 -> plc>=.95,WF_CI>0 | 9,746 (1.8) | 22,027 (2.2) |
| PRO1 | PRO1_IMB_K3_EMA200_SWZ | CANDIDATE -> DEAD | plc>=.95 -> plc>=.95,WF_CI>0 | 8,905 (1.7) | 24,960 (2.9) |
| PRO1 | PRO1_IMB_K5_EMA200_SWZ | CANDIDATE -> DEAD | plc>=.95 -> plc>=.95,WF_CI>0 | 7,391 (1.6) | 12,129 (1.8) |
| PRO1 | PRO1_LPC_Z13_EMA200_EMA5 | CANDIDATE -> DEAD | plc>=.95 -> plc>=.95,WF_CI>0 | 6,105 (1.5) | 12,153 (1.3) |
| PRO1 | PRO1_LPC_Z16_ST10_SWZ | CANDIDATE -> DEAD | plc>=.95 -> plc>=.95,WF_CI>0 | 6,123 (1.9) | 14,989 (2.2) |
| PRO1 | PRO1_QD_R4_EMA200_EMA5 | CANDIDATE -> DEAD | plc>=.95 -> plc>=.95,WF_CI>0,x2_WF>0 | 1,851 (0.5) | 5,993 (0.9) |
| PRO1 | PRO1_QD_R6_EMA200_SWZ | CANDIDATE -> DEAD | plc>=.95 -> plc>=.95,WF_CI>0 | 6,194 (1.3) | 9,121 (1.0) |
| PRO2 | PRO_KAL_k0.0 | PASS -> CANDIDATE | - -> WF_CI>0 | 6,944 (1.3) | 11,283 (1.1) |
| PRO2 | PRO_KAL_s0.5_k0.0 | CANDIDATE -> DEAD | plc>=.95 -> plc>=.95,WF_CI>0 | 6,720 (1.1) | 20,485 (1.7) |
| PRO2 | PRO_KAL_s0.5_k0.25 | CANDIDATE -> DEAD | SPAN2>0 -> SPAN2>0,WF_CI>0 | 10,427 (1.8) | 16,135 (1.5) |
| PRO2 | PRO_RIB1m_q25_M10 | CANDIDATE -> DEAD | plc>=.95 -> plc>=.95,WF_CI>0 | 9,123 (1.6) | 21,495 (2.3) |
| PRO2 | PRO_RIB1m_q25_M5 | CANDIDATE -> DEAD | plc>=.95 -> plc>=.95,WF_CI>0 | 7,875 (1.4) | 20,301 (2.1) |
| PRO2 | PRO_RIB1m_q30_M20 | CANDIDATE -> DEAD | plc>=.95 -> plc>=.95,WF_CI>0 | 9,101 (1.6) | 16,849 (1.8) |
| PRO2 | PRO_RIB1m_q30_M5 | CANDIDATE -> DEAD | plc>=.95 -> plc>=.95,WF_CI>0 | 8,680 (1.5) | 19,549 (1.9) |
| PRO2 | PRO_RIB1m_q35_M20 | CANDIDATE -> DEAD | plc>=.95 -> plc>=.95,WF_CI>0 | 10,256 (1.8) | 22,721 (2.3) |
| PRO2 | PRO_RIB1m_q35_M5 | CANDIDATE -> DEAD | plc>=.95 -> plc>=.95,WF_CI>0 | 8,522 (1.5) | 23,265 (2.2) |
| PRO3 | PRO3A_REL | PASS -> CANDIDATE | - -> WF_CI>0 | 5,343 (1.2) | 4,308 (0.5) |
| TA1 | TE7_boll3m_n20_m1.5|wide | CANDIDATE -> DEAD | SPAN2>0 -> SPAN2>0,WF_CI>0 | 5,981 (1.5) | 9,029 (1.1) |
| TA1 | TE7_boll3m_n30_m1.5|wide | CANDIDATE -> DEAD | SPAN2>0 -> SPAN2>0,WF_CI>0 | 8,606 (2.1) | 3,285 (0.4) |
| TPULLBACK | PB7_PB5_depth_atr0.5_W15_s+0 | PASS -> CANDIDATE | - -> WF_CI>0 | 9,595 (1.9) | 4,731 (0.6) |
| TPULLBACK | PB7_PB6_ST60m_EMA20_3m_T1_W30_s+3 | CANDIDATE -> DEAD | plc>=.95 -> plc>=.95,WF_CI>0 | 8,978 (1.8) | 20,445 (2.3) |
| TPULLBACK | PB7_PB6_ST60m_EMA20_3m_T1_W60_s+3 | CANDIDATE -> DEAD | plc>=.95 -> plc>=.95,WF_CI>0 | 8,714 (1.9) | 19,018 (2.1) |
| TPULLBACK | PB7_PB_HMA55_EMA1_T1_W15_s-3 | CANDIDATE -> DEAD | plc>=.95 -> plc>=.95,WF_CI>0 | 8,035 (1.4) | 8,822 (0.7) |
| TPULLBACK | PB7_PB_HMA55_EMA1_T1_W60_s-3 | CANDIDATE -> DEAD | plc>=.95 -> plc>=.95,WF_CI>0 | 9,088 (1.6) | 11,488 (0.9) |
| TPULLBACK | PB7_PB_HMA55_EMA1_T2_W60_s+0 | PASS -> CANDIDATE | - -> WF_CI>0 | 9,222 (1.6) | 3,667 (0.3) |
| TPULLBACK | PB_EMA200_EMA5_T1 | CANDIDATE -> DEAD | plc>=.95 -> plc>=.95,WF_CI>0 | 5,941 (1.2) | 17,968 (1.9) |
| TPULLBACK | PB_EMA200_KELT_T1 | CANDIDATE -> DEAD | plc>=.95 -> plc>=.95,WF_CI>0 | 7,094 (1.5) | 23,015 (2.3) |
| TPULLBACK4 | TB4A_time_00_time_15s_EMA20010_E20_1_T1 | CANDIDATE -> DEAD | plc>=.95 -> plc>=.95,WF_CI>0 | 9,585 (1.6) | 16,986 (1.7) |
| TPULLBACK4 | TB4A_time_11_time_15s_ST5_SW50_T3 | CANDIDATE -> DEAD | SPAN2>0 -> SPAN2>0,WF_CI>0 | 9,529 (1.9) | 13,655 (1.4) |
| TPULLBACK4 | TB4E_renko_28_renko_20_ST15_E20_1_T3 | PASS -> CANDIDATE | - -> WF_CI>0 | 10,904 (1.8) | 9,722 (1.0) |
| TPULLBACK4 | TB4W_07_tick_250_ST5_SW62_T2_ntick26 | CANDIDATE -> DEAD | plc>=.95 -> plc>=.95,WF_CI>0 | 8,778 (1.7) | 11,993 (1.6) |
| TPULLBACK4 | TB4W_19_volume_1000_ST3_E20_1_T2_nvolume21 | PASS -> CANDIDATE | - -> WF_CI>0 | 8,979 (1.6) | 11,807 (1.2) |
| TR1 | TR1B_reg1m_n60_t2_r0.5 | CANDIDATE -> DEAD | SPAN2>0 -> SPAN2>0,HOLD>0 | 10,650 (2.1) | -5,551 (-0.5) |
| TR1 | TR1B_reg1m_n60_t3_r0.5 | CANDIDATE -> DEAD | SPAN2>0 -> SPAN2>0,HOLD>0 | 10,650 (2.1) | -5,551 (-0.5) |
| TR1 | TR1F_vote_TSM_k3 | CANDIDATE -> DEAD | plc>=.95 -> plc>=.95,WF_CI>0 | 6,451 (1.3) | 8,251 (0.8) |
| TR2 | TR2_DON15_LV2 | PASS -> CANDIDATE | - -> WF_CI>0 | 3,385 (1.6) | 1,132 (0.3) |
| TR2 | TRW_kelt3m_n14_m2.0_RT15 | CANDIDATE -> DEAD | plc>=.95 -> plc>=.95,WF_CI>0 | 7,894 (1.7) | 12,001 (1.5) |

## 2. Per-window re-read of the DS-1 priority programs (original PASS/CANDIDATE rows; $/wk (t))

Windows: X' 2023-04..2024-01 and PRE are bounded (unchanged by the cap); WF and HOLD columns are capped. `WF unc` / `HOLD unc` are the originally reported uncapped means.

### PRO1 (22 original PASS/CANDIDATE rows with series: capped WF t>=2 2, capped HOLD t>=2 7, capped WF CI lower bound >0 3, capped HOLD>0 21)

| cell | basis | tier orig -> capped | X' (t) | PRE (t) | WF unc | WF cap (t) [CI lo] | HOLD unc | HOLD cap (t) | L6M (t) | failed orig -> capped |
|---|---|---|---|---|---|---|---|---|---|---|
| PRO1_IMB_K5_ST10_SWZ | mapped | PASS -> PASS | 5,756 (0.9) | 6,722 (1.0) | 12,915 | 11,685 (2.2) [1,170] | 19,459 | 22,951 (2.7) | 27,122 (3.0) | nan -> - |
| PRO1_AGG_CD3_ST10_SWZ | mapped | CANDIDATE -> CANDIDATE | 4,785 (0.8) | 5,683 (0.9) | 9,387 | 11,082 (2.1) [1,213] | 13,277 | 23,391 (2.5) | 26,009 (2.7) | plc>=.95 -> plc>=.95 |
| PRO1_ABS_V15_EMA200_SWZ | mapped | CANDIDATE -> CANDIDATE | 3,077 (0.5) | 6,865 (1.0) | 8,421 | 10,188 (1.8) [-847] | 9,990 | 17,658 (2.0) | 21,631 (2.3) | WF_CI>0 -> WF_CI>0 |
| PRO1_AGG_CD2_EMA200_SWZ | mapped | **CANDIDATE -> DEAD** | 2,399 (0.4) | 2,800 (0.4) | 14,950 | 10,186 (1.9) [-85] | 27,941 | 27,180 (2.9) | 29,470 (3.0) | plc>=.95 -> plc>=.95,WF_CI>0 |
| PRO1_AGG_RL3_ST10_SWZ | mapped | **CANDIDATE -> DEAD** | 1,204 (0.2) | 4,376 (0.7) | 10,244 | 9,746 (1.8) [-613] | 16,474 | 22,027 (2.2) | 24,531 (2.4) | plc>=.95 -> plc>=.95,WF_CI>0 |
| PRO1_IMB_K3_EMA200_SWZ | mapped | **CANDIDATE -> DEAD** | 12,048 (2.1) | 1,937 (0.3) | 13,299 | 8,905 (1.7) [-1,095] | 25,457 | 24,960 (2.9) | 28,975 (3.5) | plc>=.95 -> plc>=.95,WF_CI>0 |
| PRO1_AGG_CD3_EMA200_SWZ | mapped | **CANDIDATE -> DEAD** | 3,224 (0.5) | 41 (0.0) | 13,481 | 8,070 (1.6) [-1,548] | 27,894 | 26,635 (2.9) | 27,757 (2.9) | plc>=.95 -> plc>=.95,WF_CI>0 |
| PRO1_ABS_R10_EMA200_SWZ | mapped | PASS -> PASS | 6,731 (1.3) | 6,492 (1.4) | 9,546 | 8,004 (1.8) [340] | 12,727 | 11,300 (1.3) | 14,953 (1.5) | nan -> - |
| PRO1_IMB_K5_EMA200_SWZ | mapped | **CANDIDATE -> DEAD** | 7,568 (1.1) | 5,271 (0.9) | 14,084 | 7,391 (1.6) [-1,512] | 23,460 | 12,129 (1.8) | 12,725 (1.8) | plc>=.95 -> plc>=.95,WF_CI>0 |
| PRO1_AGG_RL3_EMA200_SWZ | mapped | **CANDIDATE -> DEAD** | 1,343 (0.2) | 6,060 (1.0) | 9,720 | 7,360 (1.6) [-1,934] | 13,558 | 10,177 (1.4) | 11,381 (1.6) | plc>=.95 -> plc>=.95,WF_CI>0 |
| PRO1_QD_R6_ST10_SWZ | mapped | CANDIDATE -> CANDIDATE | 732 (0.1) | 3,562 (0.6) | 6,177 | 6,644 (1.4) [-2,426] | 8,931 | 13,661 (1.6) | 20,792 (2.5) | WF_CI>0 -> WF_CI>0 |
| PRO1_QD_R6_EMA200_SWZ | mapped | **CANDIDATE -> DEAD** | 1,045 (0.2) | 4,862 (0.8) | 11,368 | 6,194 (1.3) [-2,944] | 18,276 | 9,121 (1.0) | 15,105 (1.7) | plc>=.95 -> plc>=.95,WF_CI>0 |
| PRO1_LPC_Z16_ST10_SWZ | mapped | **CANDIDATE -> DEAD** | 12,200 (3.6) | 2,258 (0.7) | 5,810 | 6,123 (1.9) [-153] | 9,586 | 14,989 (2.2) | 16,442 (2.6) | plc>=.95 -> plc>=.95,WF_CI>0 |
| PRO1_LPC_Z13_EMA200_EMA5 | mapped | **CANDIDATE -> DEAD** | 214 (0.0) | 3,443 (0.8) | 8,001 | 6,105 (1.5) [-2,063] | 12,839 | 12,153 (1.3) | 17,441 (1.9) | plc>=.95 -> plc>=.95,WF_CI>0 |
| PRO1_AGG_RL5_EMA200_EMA5 | mapped | CANDIDATE -> CANDIDATE | 1,485 (0.3) | 7,742 (1.7) | 4,481 | 5,945 (1.4) [-1,995] | 872 | 1,549 (0.2) | 4,727 (0.5) | WF_CI>0 -> WF_CI>0 |
| PRO1_AGG_RL3_EMA200_EMA5 | mapped | CANDIDATE -> CANDIDATE | 184 (0.0) | 6,199 (0.9) | 7,714 | 5,770 (1.1) [-4,141] | 9,250 | 4,586 (0.5) | 6,613 (0.7) | WF_CI>0 -> WF_CI>0 |
| PRO1_ABS_R10_ST10_EMA5 | mapped | CANDIDATE -> CANDIDATE | 3,148 (0.7) | 6,458 (1.1) | 5,410 | 5,674 (1.2) [-3,634] | 4,192 | 3,661 (0.4) | 4,965 (0.6) | WF_CI>0 -> WF_CI>0 |
| PRO1_ABS_R10_EMA200_EMA5 | mapped | **CANDIDATE -> DEAD** | 6,632 (1.3) | 9,333 (2.2) | 7,001 | 5,433 (1.4) [-2,096] | 4,365 | -3,877 (-0.5) | -576 (-0.1) | WF_CI>0 -> WF_CI>0,HOLD>0 |
| PRO1_ABS_R12_EMA200_SWZ | mapped | **CANDIDATE -> DEAD** | 7,103 (1.6) | 5,831 (1.5) | 7,254 | 4,850 (1.5) [-1,817] | 8,695 | 2,399 (0.4) | 7,084 (1.1) | plc>=.95 -> plc>=.95,WF_CI>0 |
| PRO1_ABS_R12_EMA200_EMA5 | mapped | **PASS -> CANDIDATE** | 2,445 (0.6) | 5,942 (1.6) | 5,788 | 4,815 (1.5) [-1,434] | 5,537 | 2,023 (0.3) | 4,531 (0.7) | nan -> WF_CI>0 |
| PRO1_ABS_V25_EMA200_SWZ | mapped | **CANDIDATE -> DEAD** | 1,986 (0.5) | 4,793 (0.9) | 7,543 | 4,235 (1.0) [-3,971] | 10,422 | 2,794 (0.4) | 7,819 (1.0) | plc>=.95 -> plc>=.95,WF_CI>0 |
| PRO1_QD_R4_EMA200_EMA5 | mapped | **CANDIDATE -> DEAD** | 6,686 (1.5) | 59 (0.0) | 7,045 | 1,851 (0.5) [-5,278] | 14,535 | 5,993 (0.9) | 6,954 (0.9) | plc>=.95 -> plc>=.95,WF_CI>0,x2_WF>0 |

### PRO2 (16 original PASS/CANDIDATE rows with series: capped WF t>=2 5, capped HOLD t>=2 7, capped WF CI lower bound >0 5, capped HOLD>0 16)

| cell | basis | tier orig -> capped | X' (t) | PRE (t) | WF unc | WF cap (t) [CI lo] | HOLD unc | HOLD cap (t) | L6M (t) | failed orig -> capped |
|---|---|---|---|---|---|---|---|---|---|---|
| PRO_Z20_t1.0 | direct | CANDIDATE -> CANDIDATE | -3,367 (-0.6) | 10,105 (1.7) | 14,005 | 13,173 (2.5) [2,480] | 18,041 | 19,949 (1.7) | 25,339 (2.3) | SPAN2>0 -> SPAN2>0 |
| PRO_Z60_t1.0 | direct | CANDIDATE -> CANDIDATE | 7,660 (1.2) | 7,951 (1.1) | 9,277 | 10,509 (1.8) [-985] | 10,583 | 16,174 (1.8) | 21,419 (2.5) | WF_CI>0 -> WF_CI>0 |
| PRO_KAL_s0.5_k0.25 | mapped | **CANDIDATE -> DEAD** | -5,203 (-0.8) | 7,853 (1.2) | 16,713 | 10,427 (1.8) [-569] | 26,102 | 16,135 (1.5) | 23,602 (2.1) | SPAN2>0 -> SPAN2>0,WF_CI>0 |
| PRO_RIB1m_q35_M20 | mapped | **CANDIDATE -> DEAD** | 5,488 (0.9) | 4,801 (0.7) | 10,753 | 10,256 (1.8) [-290] | 17,068 | 22,721 (2.3) | 29,134 (3.0) | plc>=.95 -> plc>=.95,WF_CI>0 |
| PRO_RIB1m_q30 | direct | CANDIDATE -> CANDIDATE | 6,605 (1.2) | 4,683 (0.7) | 8,535 | 9,287 (1.7) [-1,376] | 12,598 | 19,789 (2.1) | 26,170 (3.0) | WF_CI>0 -> WF_CI>0 |
| PRO_RIB1m_q25_M10 | mapped | **CANDIDATE -> DEAD** | 1,954 (0.3) | 3,723 (0.6) | 10,128 | 9,123 (1.6) [-1,681] | 16,944 | 21,495 (2.3) | 27,891 (3.1) | plc>=.95 -> plc>=.95,WF_CI>0 |
| PRO_RIB1m_q30_M20 | mapped | **CANDIDATE -> DEAD** | 6,036 (1.1) | 5,674 (0.8) | 11,024 | 9,101 (1.6) [-1,652] | 16,679 | 16,849 (1.8) | 22,026 (2.5) | plc>=.95 -> plc>=.95,WF_CI>0 |
| PRO_RIB1m_q30_M5 | mapped | **CANDIDATE -> DEAD** | 4,200 (0.8) | 3,926 (0.6) | 11,662 | 8,680 (1.5) [-2,912] | 19,902 | 19,549 (1.9) | 25,087 (2.5) | plc>=.95 -> plc>=.95,WF_CI>0 |
| PRO_RIB1m_q35_M5 | mapped | **CANDIDATE -> DEAD** | 3,288 (0.6) | 2,118 (0.3) | 10,103 | 8,522 (1.5) [-2,147] | 18,635 | 23,265 (2.2) | 29,734 (2.9) | plc>=.95 -> plc>=.95,WF_CI>0 |
| PRO_RIB1m_q25_M5 | mapped | **CANDIDATE -> DEAD** | 1,820 (0.3) | 2,467 (0.4) | 9,823 | 7,875 (1.4) [-3,167] | 17,675 | 20,301 (2.1) | 25,727 (2.8) | plc>=.95 -> plc>=.95,WF_CI>0 |
| PRO_KAL_k0.0 | direct | **PASS -> CANDIDATE** | 2,447 (0.4) | 5,000 (0.8) | 10,077 | 6,944 (1.3) [-3,403] | 15,449 | 11,283 (1.1) | 23,204 (2.5) | nan -> WF_CI>0 |
| PRO_KAL_s0.5_k0.0 | mapped | **CANDIDATE -> DEAD** | 3,036 (0.5) | 757 (0.1) | 11,036 | 6,720 (1.1) [-4,681] | 22,050 | 20,485 (1.7) | 30,080 (2.5) | plc>=.95 -> plc>=.95,WF_CI>0 |
| PRO_ER4_EMA5 | direct | PASS -> PASS | 33 (0.0) | 5,025 (1.3) | 5,220 | 6,644 (2.1) [1,119] | 5,355 | 10,232 (2.1) | 12,366 (2.5) | nan -> - |
| PRO_ER5_EMA5 | direct | PASS -> PASS | 2,862 (1.0) | 4,011 (1.7) | 4,866 | 5,824 (2.8) [1,781] | 5,724 | 9,891 (2.4) | 10,823 (2.4) | nan -> - |
| PRO_ER4_n40_EMA5 | mapped | CANDIDATE -> CANDIDATE | 1,604 (0.6) | 5,704 (2.8) | 4,476 | 4,994 (2.9) [1,527] | 3,077 | 3,174 (1.0) | 5,281 (1.5) | tpw>=3 -> tpw>=3 |
| PRO_ER6_n20_EMA5 | mapped | CANDIDATE -> CANDIDATE | 839 (0.5) | 2,236 (2.0) | 1,979 | 2,582 (2.5) [480] | 1,670 | 3,313 (1.5) | 2,200 (0.9) | tpw>=3 -> tpw>=3 |

### TA1 (8 original PASS/CANDIDATE rows with series: capped WF t>=2 7, capped HOLD t>=2 1, capped WF CI lower bound >0 6, capped HOLD>0 8)

| cell | basis | tier orig -> capped | X' (t) | PRE (t) | WF unc | WF cap (t) [CI lo] | HOLD unc | HOLD cap (t) | L6M (t) | failed orig -> capped |
|---|---|---|---|---|---|---|---|---|---|---|
| TE7_kelt3m_n20_m1.0|wide | direct | CANDIDATE -> CANDIDATE | -5,417 (-1.1) | 16,249 (2.9) | 16,516 | 15,007 (3.1) [5,422] | 16,568 | 11,630 (1.3) | 15,498 (1.7) | SPAN2>0 -> SPAN2>0 |
| TE7_kelt3m_n14_m1.0|wide | direct | PASS -> PASS | 2,638 (0.5) | 12,730 (2.8) | 12,585 | 13,957 (3.2) [5,502] | 12,245 | 16,399 (1.6) | 19,055 (1.9) | nan -> - |
| TE1_kelt_3m|wide | direct | CANDIDATE -> CANDIDATE | -1,593 (-0.3) | 12,626 (2.4) | 7,804 | 12,113 (2.7) [2,834] | 2,450 | 10,532 (1.2) | 13,583 (1.5) | SPAN2>0 -> SPAN2>0 |
| TE7_boll3m_n30_m1.5|wide | direct | **CANDIDATE -> DEAD** | -4,702 (-0.8) | 10,762 (2.2) | 10,285 | 8,606 (2.1) [-166] | 9,618 | 3,285 (0.4) | 1,326 (0.2) | SPAN2>0 -> SPAN2>0,WF_CI>0 |
| TE1_st_10m|wide | direct | PASS -> PASS | 2,789 (0.6) | 4,652 (1.3) | 7,115 | 6,917 (2.2) [706] | 9,689 | 12,012 (2.0) | 11,881 (1.7) | nan -> - |
| TE6_st10m_n14_m3.0|wide | direct | CANDIDATE -> CANDIDATE | 3,119 (0.6) | 4,097 (1.0) | 6,242 | 6,763 (2.0) [238] | 8,482 | 12,799 (2.3) | 11,901 (1.9) | plc>=.95 -> plc>=.95 |
| TE7_boll3m_n20_m1.5|wide | direct | **CANDIDATE -> DEAD** | -2,174 (-0.3) | 4,600 (1.0) | 8,325 | 5,981 (1.5) [-1,839] | 12,253 | 9,029 (1.1) | 8,374 (1.0) | SPAN2>0 -> SPAN2>0,WF_CI>0 |
| TE5_mbo1|quiet | mapped | CANDIDATE -> CANDIDATE | 2,140 (0.9) | 5,103 (2.6) | 2,703 | 3,647 (2.5) [913] | 56 | 120 (0.1) | -406 (-0.6) | tpw>=3 -> tpw>=3 |

PRO1: not tiered: 9 P7 learned-detector rows (no series: AUC/permutation gates, DEAD). PRO2: the 14 DIRECT-replay cells use `PRO2/direct_daily.parquet` with the `direct_final.pkl` gates. TA1: 76 of 120 rows have a stored series (44 are DEAD for tpw<3/too few trades or have no series; they cannot be tiered here). TA1 up-moves are regime-gated 'wide' forecaster cells whose uncapped HOLD was negative because the post-cut weeks were poor; capped WF/HOLD are positive, but placebo and x2 are carried/approximate, so treat the 5 DEAD -> PASS as LEAD at most (they are post-hoc selected from 120 cells, best-of-N unchanged).

### TCHOP (DS3_TCHOP block 0, 13 cells) and CHOP_FINAL (169 cells + block 0, 274 scored rows incl. direct)

Block 0: all 13 DEAD originally and cannot move: 10 fail G6 (placebo) AND M (trades/wk < 3, window independent), the rest fail 5-6 gates. Capped stats (equal-risk series): WF/HOLD $/wk (t):

| cell | orig failed | WF unc | WF cap (t) | HOLD unc | HOLD cap (t) |
|---|---|---|---|---|---|
| RSI2C_s20 | G6,M | 11,547 | 10,178 (2.1) | 13,766 | 11,729 (1.5) |
| ES_RSI2_t10 | G6,M | 13,862 | 13,784 (2.3) | 16,027 | 18,202 (2.3) |
| RSI2T_t10 | G6,M | 9,625 | 10,010 (2.3) | 11,478 | 14,838 (1.6) |
| IBS_t20_n1 | G6,M | 9,196 | 8,204 (1.5) | 11,953 | 11,768 (1.8) |
| RTY_IBS_t20_n1 | G6,G7,M | 7,648 | 6,551 (1.1) | 10,694 | 10,486 (0.9) |
| ORB_ASIA_15_v1_s60 | G4,G5,G6,G7,G8,M | 9,027 | 9,674 (1.7) | 14,037 | 21,814 (2.0) |
| ORB_ASIA_15_v1_s75 | G5,G6,G7,G8,M | 9,280 | 8,456 (1.4) | 18,160 | 25,419 (2.7) |
| COMB_c3_R | G6,M | 9,781 | 9,479 (1.9) | 12,085 | 13,676 (1.8) |
| YM_RSI2_t10 | G6,M | 9,076 | 4,719 (0.8) | 12,399 | 1,704 (0.2) |
| DIPBUY_RSI2_2lot | G6,M | 13,737 | 12,777 (2.3) | 16,145 | 15,674 (1.8) |
| T14_S_s50_t1.5_n14 | G4,G6,G7,G8,M,T1 verdict DEAD inherited (paired CI [-5.9k,20.8k], year share 68%, placebo 0.91) | 7,914 | 2,759 (0.4) | 7,325 | -10,416 (-0.9) |
| FOURTH_R4_k2.0_H60_8lots | G2,G4,G5,G6,G7,G8 | -23,000 | -24,324 (-5.1) | -28,006 | -38,022 (-4.3) |
| FOURTH_R2_k1.0_H120_8lots | G2,G4,G5,G6,G7,G8 | -26,281 | -27,600 (-5.7) | -24,400 | -26,653 (-3.1) |

CHOP_FINAL: the 26 CANDIDATE rows (X09 and B2_X09_DG1/2 fail M only; the B3/B4/B10 rows fail G4 only). G1/G2 (standalone WF/HOLD mean>0) recomputed capped: all 26 keep WF>0 and HOLD>0, so no tier change. Capped WF t of the B3/B4 family 1.5 to 2.3 (uncapped WF means 11-15k -> 8-13k/wk), capped HOLD t 1.4 to 2.6. G4 (marginal Sharpe + dMaxDD sign), G5 (L25) and G6 (shift placebo) need the stack/risk-parity add-one engine and are CARRIED (not recomputed); G4 is the gate that was failing for all 22 B3/B4 candidates, so a capped G4 re-run is the open item (the dMaxDD WF sign comes from 2024-04..2024-08, inside the capped window, so it should not move; marginal Sharpe could). 'DEAD [REGIME BETA]' labels treated as DEAD.

### XT exits (DS3_TC1C2 / TC3C4 / TC4R4 / TC5; valid v2 daily series)

246 v2 cells (paired against the stream's own DS2 bracket): all DEAD, all stay DEAD. The trade-modifier gates mean_up / holdout_sign_agrees are paired-points gates (trade level); here they are replaced by the weekly proxy d(WF)>0 / d(HOLD)>0, the other gates carried. Capped d(replay - bracket) WF>0 in 85 cells (91 uncapped), HOLD>0 in 86 (100); capped WF t>=2 in 3, HOLD t>=2 in 1. Best capped cells: XT_R4_ONH_HM dWF 12,009 (t 2.4), dHOLD 10,715 (t 1.4); XT_R4_ONH_PB3 dWF 11,831 (t 2.1), dHOLD -4,374 (t -0.6); XT_C1_90_PB3 dWF 9,667 (t 2.0), dHOLD 5,602 (t 0.7); XT_C1_120_ST10n10 dWF 9,396 (t 1.8), dHOLD 11,606 (t 1.0). Each still fails neighbours/placebo/paired-CI&maxDD/SPAN2/year-share. **The 14 `SERIES/XT_*` files used by DS-1 are the v1 INVALID run; ignore the DS-1 XT figure.** Full table: XT_rescore.csv.


## 3. Live books: capped baseline (item 2)

Series: `ds3/out/series/D00x.parquet` pnl_live (report-scale USD, corrected P9 live cost $4.84, per-book locks), sliced at 2026-02-06. 'unc' = the pool's stored uncapped WF (142 wk) / HOLD (68 wk) mean and t; 'cap' = WF 106 wk / HOLD 32 wk (week-block t of the weekly mean). D6 tags per the 2026-10-29 user ruling: ST = S6 (in D6, disabled), WT not in D6 (W6 placeholder), HM carried by DS6 / H6; MA6 and CR (C6) have no DS2 pool series (not in this table; their research series are in the DS3 reports, not DS2 books). Implied post-cut mean = (142 x WF unc - 106 x WF cap) / 36.

| id | book | D6 tag | WF unc (t) | WF cap (t) | HOLD unc (t) | HOLD cap (t) | L6M cap (t) | PRE (t) | X' (t) | implied 36 post-cut wk |
|---|---|---|---|---|---|---|---|---|---|---|
| D000 | DS2_ST10_pb | ST10 (S6 in D6, disabled) | 14,250 (3.0) | 15,086 (2.8) | 16,225 (2.2) | 21,280 (2.0) | 27,568 (2.6) | 12,242 (2.0) | 6,055 (0.9) | 11,786 |
| D001 | DS2_HM10_pb | HM10 (DS6 / H6 carrier) | 9,982 (2.2) | 9,329 (1.9) | 10,445 (1.5) | 8,818 (0.9) | 13,524 (1.5) | 9,422 (1.6) | 3,808 (0.7) | 11,903 |
| D002 | DS2_WT7_pb | WT7 (W6 placeholder, not in D6) | 1,428 (0.6) | 2,380 (0.9) | 775 (0.2) | 3,173 (0.6) | 4,883 (1.0) | 2,010 (0.6) | 1,293 (0.3) | -1,375 |
| D003 | DS2_ST8_pb | ST8 | 11,400 (3.0) | 12,069 (2.8) | 12,980 (2.2) | 17,024 (2.0) | 22,054 (2.6) | 9,794 (2.0) | 4,844 (0.9) | 9,429 |
| D004 | DS2_HM8_pb | HM8 | 7,985 (2.2) | 7,463 (1.9) | 8,356 (1.5) | 7,055 (0.9) | 10,819 (1.5) | 7,538 (1.6) | 3,046 (0.7) | 9,523 |
| D005 | DS2_ST12_pb | ST12 | 17,100 (3.0) | 18,104 (2.8) | 19,470 (2.2) | 25,536 (2.0) | 33,082 (2.6) | 14,691 (2.0) | 7,265 (0.9) | 14,143 |
| D006 | DS2_HM12_pb | HM12 | 11,978 (2.2) | 11,195 (1.9) | 12,534 (1.5) | 10,582 (0.9) | 16,229 (1.5) | 11,307 (1.6) | 4,569 (0.7) | 14,284 |
| D007 | DS2_ST14_pb_s14 | ST14 (s14) | 16,841 (3.0) | 17,906 (2.7) | 19,573 (2.4) | 26,261 (2.2) | 32,609 (2.9) | 14,103 (1.8) | 3,196 (0.4) | 13,705 |
| D008 | DS2_HM10_pb_s14 | HM10 (s14) | 13,491 (2.5) | 12,535 (2.1) | 16,047 (1.9) | 15,836 (1.3) | 22,931 (1.9) | 10,960 (1.6) | 5,763 (0.8) | 16,305 |
| D009 | DS2_WT7_pb_s14 | WT7 (s14) | 1,428 (0.6) | 2,380 (0.9) | 775 (0.2) | 3,173 (0.6) | 4,883 (1.0) | 2,010 (0.6) | 1,293 (0.3) | -1,375 |

Reading: ST10 gets better when capped (HOLD 16.2k -> 21.3k/wk, t 2.2 -> 2.0, L6M 27.6k t 2.6; the post-cut 36 weeks were weaker, about 11.8k/wk). HM10 gets worse on the HOLD CI (10.4k -> 8.8k/wk, t 1.5 -> 0.9; L6M 13.5k, t 1.5): its post-cut weeks (about 11.9k/wk) were better than its in-window HOLD, so the uncapped HOLD flattered it. WT7 stays statistically nothing (WF t 0.6 -> 0.9, HOLD t 0.2 -> 0.6). The D009 / D002 rows are the same series (identical). Stack (from the reports, not recomputed here): capped WF 46,785/wk over 106 wk (STACK_B) vs uncapped 45,947 over 142; capped HOLD base 52,448/wk, SD 151,891, 32 wk (STACK_D re-run) vs uncapped 47,279 over 68 wk; implied post-cut mean about 43.5k/wk.

## 4. STACK_D, DIV_VOLGATE, CONFIRM_B, DIV2_A_AUDIT (capped; fork C, scripts fc_*.py, CSVs fc_*.csv)

No verdict or tier changes: every STACK_D / VOLGATE cell was DEAD and stays DEAD; CONFIRM_B/FINAL claims unchanged. Reproduction: STACK_D, VOLGATE and CONFIRM_A match their stored PRE and X' numbers to the dollar; CONFIRM_B matches X' for all 24 cells; the DIV2_A capped WF base (47,055/wk) matches. Gates G4 (placebo draws), G8 (2x cost series) and trade-level paired CIs are not stored: carried and flagged '(carried)'. Windows capped; t = week-block t.

**STACK_D (9 cells), WF raw d_mean and HOLD lot-matched (LM) d_mean $/wk, uncapped -> capped (t capped):**

| cell | WF raw d | HOLD LM d | tier |
|---|---|---|---|
| D_L20s | -16,176 -> -15,597 (-1.7) | +2,598 -> +14,052 (0.8) | DEAD -> DEAD |
| D_L30s | -7,470 -> -10,238 (-1.8) | +6,094 -> +4,541 (0.4) | DEAD -> DEAD |
| D_L40s | +1,788 -> +1,699 (1.0) | +2,270 -> +1,371 (0.6) | DEAD -> DEAD (fails G2, G3, G5, G6; PRE LM +3,385, t 1.5) |
| D_B2s | -20,053 -> -21,151 (-2.1) | -153 -> +5,008 (0.2) | DEAD -> DEAD |
| D_B3s | -9,953 -> -11,945 (-1.8) | +2,488 -> +303 (0.0) | DEAD -> DEAD |
| D_B4s | -3,624 -> -3,411 (-0.9) | +478 -> +2,215 (0.4) | DEAD -> DEAD |
| D_B3h | -5,771 -> -8,042 (-1.5) | -584 -> -7,347 (-0.9) | DEAD -> DEAD |
| D_B3e | -10,057 -> -12,399 (-2.0) | +2,538 -> +622 (0.1) | DEAD -> DEAD |
| D_L30t | -5,119 -> -6,069 (-1.4) | +743 -> +341 (0.0) | DEAD -> DEAD |

**DIV_VOLGATE (21 cells; 17 scored non-reference + VS_ref), WF raw d_mean and HOLD LM d_mean:** all 20 scored cells stay DEAD. Selected rows: A_skipB WF -25,067 -> -26,765 (t -3.4), HOLD LM -28,658 -> -44,586 (-2.1); A_half -10,438 -> -10,651 (-2.8), HOLD -9,399 -> -12,402 (-1.4); A_up WF +3,504 -> -792 (-0.2), HOLD +7,047 -> -3,160 (-0.6) (the only cell positive on both uncapped windows; now negative on both and also fails G1); V_skipB -19,412 -> -19,704 (-2.7); A_skipT WF -8,399 -> -9,715 (-1.1), HOLD LM +34,473 -> +48,808 (t 2.4, CI [7.8k, 86.6k], still a leverage artefact: fails G3, G6, G7; capped L6M +60.4k, t 3.3; nothing reaches LEAD); F_hu_vs WF -5,077 -> -6,512 (-2.4), HOLD +8,432 -> +10,837 (1.8), fails G1, G3, G5, G6, G7. All 21 rows in fc_volgate.csv.

**CONFIRM_B (24 cells, queue-position replay; re-scored with `cfb_score` on signals dated <= 20260206):** the same 4 cells pass (T basis, 0 s delay, 5 and 10 lots, back and prop queues); 0 of 24 pass on both M and T bases (unchanged). Headline cell (back, 1 s, 10 lots): M basis WF d +909 -> +1,086 (CI still includes 0, MDE 2,119 -> 2,356), HOLD +396 -> +404 (t 0.3); T basis WF +1,768 -> +1,950 (CI lo +293, MDE 2,279 -> 2,502), HOLD +1,422 -> +1,636 (t 1.1). Every HOLD CI still includes 0. 3 s delay on M: HOLD flips from positive to negative (-117 at 5 lots, -235 at 10 lots). 0 s on M: WF CI now excludes 0 (lo +65 / +131) but WF < MDE still fails. Verdict "does not exist at live latency" stands.

**CONFIRM_FINAL (CONFIRM_A cross-instrument rows):** replication stays 0 of 3 for both rules. DR5m: ES WF +55..+185 [-112, +487], HOLD t 1.2; RTY HOLD +140..+536 (t 1.8) but WF -145; YM WF -124; POOL WF -85 [-735, +576]. RVW1: ES WF +98 [-225, +387]; YM -101; RTY -228 (HOLD -1,036, t -4.5); POOL -231. NQ reference rows strengthen (DR5m +443..+623, t 3.6; RVW1 +402..+473, t 3.0) but are in-sample. Both rules stay NQ-only.

**DIV2_A_AUDIT (descriptive, no tiers):** audit re-run on trades with label day <= 20260206: 149 weeks, 19,069 trades, $5.89M ($39,564/wk) (file headers in `fc_dv2a_audit_capped.txt` still print 185/142 wk and 2026-10-16; the numbers are capped). Losing days 354 of 737 (48%; was 438/917, 48%); range-day share of losing-day dollars 65% (64%); WF mean 47,055/wk (45,947); negative WF weeks 38 of 106 (54 of 142); 20 worst weeks -$3.53M (-$3.74M; equals DS3_DIV2_FINAL's capped figure). Net-negative entry slots 11 (12): 07:00, 12:00, 13:00, 22:00 drop out; 01:00, 01:30, 08:30 enter; 8 persist (03:30, 05:00, 05:30, 08:00, 11:30, 14:30, 16:30, 23:30). Only 16:30 reaches |t_week| >= 1.8 (-2.10); 03:30 falls from -1.81 to -1.08. Same 6 idle slots.

## 5. STRUCT48-era PASS/CANDIDATE rows whose status changes under the cap (item 3; data for the open question)

Source: `struct48_leaderboard_capped.csv` (57 rows: 47 PASS/CANDIDATE + 10 PENDING), `struct48_tier_changes.csv`, `struct48_dead_upflip_scan.csv` (fork B; code `fb_*.py`). Rule: `s48score.verdict` six conditions with WF = 106 wk, HOLD = 32 wk, MDE from 106 wk; sleeve rows re-sized to the capped WF SD; standalone/marginal/2x/year-share recomputed from the stored unit series. Carried: placebo ranks (incl. the 5,000-draw placebo of record), DSR, T3.10b worst-of-stress, NM_E OOS 2013-2023. Not re-scored: T4.2_Y4 (no series, carried CANDIDATE; its uncapped holdout was already -2.7k/wk); STRUCT48_LEADERBOARD.md (PASS 0, superseded). 10 PENDING rows unchanged (no WF dependence).

**Totals (47 PASS/CANDIDATE rows): 18 PASS -> 4 PASS + 14 CANDIDATE; 29 CANDIDATE -> 23 CANDIDATE, 4 DEAD, 1 PASS, 1 carried. After the cap: 5 PASS, 37 CANDIDATE (+1 carried), 4 DEAD. Plus 6 DEAD -> CANDIDATE from a scan of 213 DEAD sleeve/NM_E/NM_B rows (20 had no series).** The 47 rows are about 12 independent exposures (T3 and NM_E rows share series and each series is scored at three sizing ratios).

| exposure (rows) | original -> capped | gate that flips | capped WF d $/wk (CI lo), HOLD d | year share (limit 0.60) |
|---|---|---|---|---|
| ORB Asia 15 s60 (T3.2 x3, NM_E x1) | PASS -> CANDIDATE | year_share | 4.4k/8.8k/17.6k per ratio (CI lo -0.4k/-0.8k/-1.7k), HOLD 9.5k/19.0k/37.9k | 0.52 -> 0.65 |
| ORB Asia 15 s75 (T3.2 x3, NM_E x1) | PASS -> CANDIDATE | year_share | 3.8k/7.6k/15.1k (lo -1.3k/-2.5k/-5.0k), HOLD 10.9k/21.7k/43.5k | 0.48 -> 0.73 |
| NQ RSI2_t10 (T3.6b1, NM_E) | PASS -> CANDIDATE | year_share (borderline) | 9.6k / 4.8k (lo +0.6k / +0.3k), HOLD 9.7k / 4.8k | 0.606 |
| ES RSI2_t10 (T3.8A, NM_E) | PASS -> CANDIDATE | year_share (borderline) | 11.0k / 5.5k (lo +1.9k / +1.0k), HOLD 14.5k / 7.3k | 0.611 |
| GSHORT_t90 (T3.8B, NM_E) | PASS -> CANDIDATE | year_share (razor thin) | 6.4k / 3.2k (lo -2.8k / -1.4k), HOLD 13.0k / 6.5k | 0.6002 |
| NQ IBS_t20_n1 (T3.7b4, NM_E) | CANDIDATE -> DEAD | year_share added to placebo 0.932 | 7.4k / 3.7k (lo -1.5k / -0.7k), HOLD 10.6k / 5.3k | 0.69 |
| T14_S_s50_t1.5_n14 (T1, NM_D) | CANDIDATE -> DEAD (scorer reading) | holdout sign, neighbours, CI | 2.8k (lo -11.5k), HOLD -10.6k (was +7.4k) | n/a |
| NM_B B01_SetB | CANDIDATE -> PASS | sizing criterion (CI now excludes 0) | 9.9k (block-bootstrap lo +0.4k, 2,000 draws), HOLD 9.5k | n/a |
| ORB NY 15 v0 s60, s75 (T3.2, 6 rows, previously DEAD) | DEAD -> CANDIDATE | holdout sign, neighbours, marginal Sharpe now pass; year_share still fails | 4.9k..25.3k, HOLD +0.4k..+5.6k (was -5.3k..-8.3k) | >0.6 |
| RSI2C_s20 / RSI2CC_s20 (T3.7rsi2c, NM_E) | PASS -> PASS | none | 10.2k / 5.1k (lo +0.9k / +0.4k), HOLD 12.1k / 6.0k | 0.52 |
| ORB Asia 30 (9 rows), NQ RSI2T_t10, YM_RSI2, COMB_c3_R, 9 NM_B rows | CANDIDATE -> CANDIDATE | (already failing year_share/placebo/object criterion) | see CSV | 0.56 to 1.05 |

How to read it (data only):
* **The year-share gate drives most flips and it is partly mechanical.** The gate asks that no calendar year hold more than 60% of the WF gain; truncating 2026 (about 36 of the ~41 weeks of 2026 removed) shrinks the 2026 slice, so 2024/2025 shares rise. Capped d_mean and HOLD d are mostly HIGHER than uncapped for the T3/NM_E sleeves (the post-cut weeks were weak for ORB Asia and the RSI2 family), i.e. the edge does not erode; the year-share evidence does. If the user keeps the cap as the standard, year_share should arguably be defined on completed calendar years (2024, 2025) plus the 2026 stub, not on the stub-truncated three-year split.
* **Real losses are two exposures:** NQ IBS_t20 (placebo 0.932 plus year share 0.69) and T14 (holdout turns -10.6k/wk; it was CANDIDATE only through the 2026-10-25 user ruling in `lb2.USER_RULINGS`, carried as-is).
* **Gains:** ORB NY 15 v0 (holdout positive when capped, fails year_share only) and NM_B B01 (CI lo +0.4k, thin).
* **Not recomputed and could move:** placebo ranks at 0.95-0.96 (ES_RSI2, GSHORT, YM_RSI2, COMB) and the YM_RSI2 neighbours.
* **Net:** 14 PASS -> CANDIDATE, 4 CANDIDATE -> DEAD, 1 CANDIDATE -> PASS, 6 DEAD -> CANDIDATE. The LEADERBOARD PASS tier falls from 18 rows to 5, but 4 of those 5 rows are the RSI2C / RSI2CC series appearing in T3 and NM_E, so independent PASS exposures go from 6 (ORB Asia s60, s75, NQ RSI2_t10, ES RSI2_t10, GSHORT, RSI2C) to 2 (RSI2C, NM_B B01). Nothing in this table changes the 2026-10-19 ruling that the pair-era programs knowingly read H2 2026; it is a comparability question. Tag options for the leaderboard (user decision, MORNING): (a) keep original tier and add a `capped` tier column, (b) replace by the capped tier, (c) mark year_share-only flips as `PASS(uncapped)`.

## 6. Caveats and what was not done
* Rows without a stored full per-cell daily series were not re-tiered: PRO1 9 P7 rows, PRO3 3, TA1 44 (low-trade/regime cells), TR1 1 (REPORT-ONLY), TR4 (58, all DEAD), TPBX* (about 500; the 2 CANDIDATE fail SPAN2 and a trade-level gate, bounded or trade-level, so the cap should not change them), TBRACKET*/TPYRAMID* (0 PASS/CANDIDATE), TPULLBACK3 (141; trade-paired s48 gates, capped absolute stats only: 6 of 17 CANDIDATE have a capped WF CI lo > 0, all 17 have capped HOLD > 0 with t 0.2 to 2.3; PB3B_R5_P1 is the strongest at WF 14.1k/wk t 2.9, HOLD 19.1k t 2.3).
* x2_WF is approximated everywhere (constant per-week cost drag from the original run); stored 2x series (SERIES pnl_2x, TA1 direct d2) were not used, so this gate could be refined. Placebo ranks were not re-drawn; they are WF-independent only for PRE-keyed placebos (T-ENTRY family), WF-keyed ones (struct48 placebo of record) may move.
* CHOP_FINAL G4/G5/G6 and the XT paired-pts gates need engines/trade pairs that were not re-run (listed above as carried).
* DS-1 section C figures (T1 1,022 -> 591, 633 survivors below zero, 154 series counts) were not repeated; the program-level counts here (PRO1 WF t>=2 16 -> 2 only among PASS/CANDIDATE, HOLD t>=2 13 -> 7) agree with DS-1's capped figures for PRO1 (2 and 7); XT is corrected (invalid series).
* Capped re-scores are a second view of data already seen (tag `RESCORE_CAPPED`, not a new holdout look). Selection (best-of-N) is untouched: nothing here lifts a tier above LEAD unless the original rules did.
