# REPORT STRUCT48 T3 - second systems (sleeves): V2 verdicts (rewritten 2026-10-24 by T3.10a)

## Sleeve verdicts under the V2 criterion (DIRECTIVE_RESEARCH_V2 sections 1-3)
Sleeve criterion: standalone holdout (2025-07+) mean > 0, marginal portfolio Sharpe up at the tested risk ratio (0.5 unless stated), weekly corr to Set A <= 0.5. PASS = base conditions (WF mean up, holdout sign agrees, neighbours agree) + placebo >= 0.95 + criterion with no secondary failure; CANDIDATE = placebo >= 0.90 and at most one failure (registered in PAPER-ALL 2026-10-24, see l2vast/struct48/paper_all/); DEAD = anything else. The "maxDD down 10%" rule of the old T3 gate is withdrawn (a 1-14 lot sleeve cannot move a $330-400k Set A drawdown). Verdicts are the lead's (autopilot/LEADERBOARD.md). Benchmark Set A WF $24,975/wk, SD 104,523; weekly WF test cannot see less than $24,574/wk for a sleeve independent of Set A, so every sleeve null below is read against its own MDE.

**Independent exposures: 5.** The 23 leaderboard rows are 16 distinct sleeves (the ORB rows are 3 sleeves x 3 risk ratios; ON_none appears at two lot displays). By weekly WF correlation (corr > 0.5 = same exposure, chained) they collapse to 5 exposures, plus Set A itself which none of them overlaps (corr to Set A -0.10..+0.10): **G1** index-long dip-buy at the 15:55 ET close (NQ/ES/RTY/YM), hold one session; RSI2, IBS, RSI2T, RSI2C, RSI2CC, COMB variants; **G2** long NQ every night 15:55 ET close -> 09:30 ET open (ON_none); **G3** long NQ 16:00-18:00 ET (session-break drift); **G4** NQ Asian-session opening-range breakout with bracket (15/30-min OR, volume filter v1, stop 60/75); **G5** NQ short at 15:55 close when RSI2>90 and Set A trailing 4-week P&L<0 (regime-gated short). Cross-group weekly corr is |r| <= 0.29 (max pair G1_INDEX_DIP_BUY_CLOSE x G2_OVERNIGHT_INDEX_LONG); the 10 dip-buy sleeves are ONE bet (within-group corr up to 0.95; matrix out/T3_exposure_corr_matrix.csv, groups out/T3_exposure_groups.json). Under a stricter average-linkage cut the two RTY variants separate (7 clusters), but they are the same trade. Forward evidence therefore accrues per exposure, not per row.

Effect = portfolio weekly mean gain vs Set A, $/wk, WF 2024-02..2026-10 (142 wks), at the tested ratio, with week-block bootstrap 95% CI; MDE = 80%-power detectable weekly effect (2.80/(2x1.96) x CI width). Hold = standalone sleeve holdout mean at that ratio. msh = marginal Sharpe check from the exported series (Set A alone vs Set A + sleeve, WF weekly), corr = weekly WF corr to Set A.

### PASS (11 rows, 10 distinct sleeves; go to a Sim leader for 2 weeks, then to the user)
| lead verdict | sleeve (cell) | effect $/wk [CI] | MDE $/wk | placebo | hold $/wk | corr | msh (dSharpe) | exposure |
|---|---|---|---|---|---|---|---|---|
| PASS | RTY_RSI2_t10 | 16,009 [8,362, 24,984] | 11,880 | 1.00 | 24,421 | +0.07 | up (+0.74) | G1 |
| PASS | ES_RSI2_t10 | 12,559 [3,559, 22,101] | 13,252 | 0.99 | 14,513 | +0.09 | up (+0.51) | G1 |
| PASS | RSI2C_s20 | 10,568 [2,294, 20,281] | 12,856 | 0.98 | 12,766 | -0.06 | up (+0.52) | G1 |
| PASS | RSI2_t10 | 10,197 [1,961, 20,243] | 13,066 | 0.98 | 10,991 | -0.05 | up (+0.49) | G1 |
| PASS | BRK_960_1080 | 9,707 [1,185, 18,109] | 12,096 | 0.99 | 10,629 | +0.00 | up (+0.42) | G3 |
| PASS | RSI2T_t10 | 8,882 [1,096, 19,045] | 12,828 | 0.96 | 10,606 | -0.09 | up (+0.45) | G1 |
| PASS | ON_none_L2 | 7,476 [-856, 15,926] | 11,994 | 0.97 | 3,132 | -0.00 | up (+0.28) | G2 |
| PASS | ON_none_L4 | 7,476 [-856, 15,926] | 11,994 | 0.97 | 6,264 | -0.00 | up (+0.28) | G2 |
| PASS | GSHORT_t90 | 5,941 [-2,995, 14,754] | 12,686 | 0.96 | 7,862 | +0.02 | up (+0.17) | G5 |
| PASS | COMB_c3_R | 2,831 [307, 5,812] | 3,934 | 0.96 | 3,490 | -0.10 | up (+0.19) | G1 |
| PASS | RSI2CC_s20 | 2,646 [574, 5,078] | 3,219 | 0.98 | 3,196 | -0.06 | up (+0.18) | G1 |
Notes: ON_none_L2/L4 are the same sleeve (1-lot unit x 2 / x 4 display; the effect shown is at ratio 0.5 and identical); its CI includes 0 ([-856, 15,926]) - the lead passes it on the sleeve criterion (holdout +, msh up, corr 0.00, placebo 0.97); overnight drift was NOT confirmed pre-2024 (T3.5: placebo 0.32, random 17.6 h holds earn about as much), so treat it as NQ long bias. GSHORT_t90 has 31 trades in WF (0.22/wk), CI [-2,995, 14,754]. RSI2CC_s20 and COMB_c3_R are lot-capped (3 lots), so their effect is the same at every ratio; their small size ($2.6-2.8k/wk) is what the cap leaves.

### CANDIDATE (12 rows, 6 distinct sleeves; registered in PAPER-ALL 2026-10-24, forward-scored weekly)
| lead verdict | sleeve (cell) | effect $/wk [CI] | MDE $/wk | placebo | hold $/wk | corr | msh (dSharpe) | exposure |
|---|---|---|---|---|---|---|---|---|
| CANDIDATE | IBS_t20_n1 | 8,465 [420, 18,131] | 12,658 | 0.94 | 10,973 | -0.07 | up (+0.40) | G1 |
| CANDIDATE | YM_RSI2_t10 | 8,274 [-87, 17,321] | 12,442 | 0.94 | 11,303 | +0.10 | up (+0.25) | G1 |
| CANDIDATE | RTY_IBS_t20_n1 | 7,236 [-396, 16,183] | 11,849 | 0.92 | 10,003 | -0.01 | up (+0.27) | G1 |
| CANDIDATE | ORB_ASIA_15_v1__s60@1.0 | 16,276 [1,553, 32,788] | 22,324 | 0.96 | 24,491 | +0.08 | up (+0.30) | G4 |
| CANDIDATE | ORB_ASIA_15_v1__s60@0.5 | 8,138 [776, 16,394] | 11,162 | 0.96 | 12,245 | +0.08 | up (+0.29) | G4 |
| CANDIDATE | ORB_ASIA_15_v1__s60@0.25 | 4,069 [388, 8,197] | 5,581 | 0.96 | 6,123 | +0.08 | up (+0.20) | G4 |
| CANDIDATE | ORB_ASIA_30_v1__s60@1.0 | 16,003 [-464, 32,465] | 23,535 | 0.98 | 26,620 | +0.08 | up (+0.25) | G4 |
| CANDIDATE | ORB_ASIA_30_v1__s60@0.5 | 8,001 [-232, 16,232] | 11,767 | 0.98 | 13,310 | +0.08 | up (+0.27) | G4 |
| CANDIDATE | ORB_ASIA_30_v1__s60@0.25 | 4,001 [-116, 8,116] | 5,884 | 0.98 | 6,655 | +0.08 | up (+0.19) | G4 |
| CANDIDATE | ORB_ASIA_15_v1__s75@1.0 | 15,455 [926, 30,113] | 20,860 | 0.96 | 29,359 | +0.06 | up (+0.32) | G4 |
| CANDIDATE | ORB_ASIA_15_v1__s75@0.5 | 7,727 [463, 15,057] | 10,430 | 0.96 | 14,680 | +0.06 | up (+0.30) | G4 |
| CANDIDATE | ORB_ASIA_15_v1__s75@0.25 | 3,864 [232, 7,528] | 5,215 | 0.96 | 7,340 | +0.06 | up (+0.20) | G4 |
Notes: YM_RSI2_t10 fails year share (> 60% of the gain from one year) and its placebo is 0.94 (< 0.95); the leaderboard file (15:07Z) lists it CANDIDATE but the live scorer (s48score.py modified 15:16Z) now evaluates it DEAD (year share + placebo < 0.95 = two failures), so expect the next leaderboard rewrite to demote it - its PAPER-ALL record is kept as written; IBS_t20_n1 placebo 0.94, RTY_IBS CI includes 0 and placebo 0.92. **ORB_ASIA verdicts are provisional (likely understated):** the leaderboard lists "-sleeve_marginal_sharpe_up / -sleeve_secondary" for all nine ORB rows, but lb2.norm does not read the T3.2 row keys (port_WF_mean etc.), so marginal Sharpe is treated as missing evidence. Recomputed from the exported series, Set A + ORB sleeve Sharpe is higher at all three ratios (dSharpe +0.19..+0.32), holdout > 0 and corr 0.06-0.08, i.e. the V2 sleeve criterion is met; ORB_ASIA_15_v1 s60/s75 (placebo 0.96, CI excludes 0 at ratios 0.25/0.5/1.0) would then be PASS, ORB_ASIA_30_v1 s60 (CI includes 0 at 1.0/0.5/0.25) remains a CANDIDATE. Flagged to the lead; no verdict changed here. ORB caveats: 160 trades in 3.7 y (0.84/wk), ratio 1.0 implies 68 lots (50-contract limit not enforced inside the sum), maxDD rises +9..+100% with ratio. The nine ORB rows and ON_none are Asia/overnight NQ-long-bias or breakout exposures - see exposure groups.

### DEAD (315 sleeve rows; listed once with reason, not re-run with the same features)
| track | dead rows | best effect $/wk [CI] | MDE $/wk (median) | dominant reason | what the null means |
|---|---|---|---|---|---|
| T3.2 | 153 | ORB_ASIA_30_v1__s75@1.0 14,390 [-2,059, 30,776] | 11,700 | sleeve_marginal_sharpe_up; standalone_hold>0&marginal_Sharpe_up&corr<=0.5 | NQ triggers other than ORB-ASIA (ORB NY/LON, Donchian 20/55, VWAP-trend, sweep): ORB_ASIA_30_v1 s75/s50 @1.0 and the NY rows have CI including 0 and/or holdout < 0; Donchian/VWAP/sweep are placebo-indistinguishable |
| T3.3 | 18 | ON_VT_L2 8,439 [275, 17,457] | 12,343 | placebo>=0.90; sleeve_marginal_sharpe_up | swing (supertrend), 20d breakout, weekly-open: ~0 or negative; ON_VT fails placebo 0.85 and year share (one year carries it) |
| T3.5 | 8 | ON_none_L1_R0.25 - [-, -] | - | placebo>=0.90; neighbours_agree | overnight confirmation on pre-2024 NQ (out-of-sample): ON_none +$210/wk CI [-20,446], placebo 0.32 (rows are info/OOS, scored DEAD by the leaderboard mapping) |
| T3.6b1 | 8 | FOMC_P1_x1400 3,746 [-4,101, 12,388] | 12,284 | placebo>=0.90; sleeve_marginal_sharpe_up | see sub-report |
| T3.6b2 | 10 | VIXS_t15_n2 4,447 [-3,745, 13,952] | 12,142 | placebo>=0.90; sleeve_marginal_sharpe_up | see sub-report |
| T3.7b3 | 10 | WKND_E955 5,291 [-3,395, 14,339] | 12,228 | placebo>=0.90; sleeve_marginal_sharpe_up | see sub-report |
| T3.7b4 | 9 | IBS_t20_n2 7,098 [-760, 15,663] | 12,472 | placebo>=0.90; sleeve_marginal_sharpe_up | see sub-report |
| T3.8A | 2 | ES_IBS_t20_n1 6,320 [-1,586, 15,548] | 11,913 | placebo>=0.90; year_share>60% | see sub-report |
| T3.8B | 7 | XDIP_CL_t10 2,273 [-6,061, 10,657] | 12,153 | sleeve_marginal_sharpe_up; standalone_hold>0&marginal_Sharpe_up&corr<=0.5 | see sub-report |
| T3_1 | 90 | 6J|s1.25@1.0 3,463 [-12,087, 20,333] | 12,247 | holdout_sign_agrees; standalone_hold>0&marginal_Sharpe_up&corr<=0.5 | D2 transplanted to ES, RTY, YM, CL, GC, ZN, 6E, 6J and baskets (1-min, conservative fills): every market negative standalone (WF unit: ES -11.3k ... ZN -84.3k /wk); no edge, so corr<=0.5 is vacuous |
Reading the DEAD tier: a weekly sleeve test at these sizes could not see an effect smaller than the MDE column (about $10-25k/wk portfolio gain at ratios 0.25-1.0, $3-5k/wk only for the capped/small sleeves), so a DEAD with CI [-X, +Y] means "no effect larger than the MDE", not "zero". Nearest misses by effect (all DEAD): ORB_ASIA_30_v1 s75@1.0 +14,390 [-2,059, 30,776] (MDE 23,468, placebo 0.96, holdout +28,509; fails the lead's marginal-Sharpe/secondary mapping, same ORB artefact as above - worth re-scoring), ON_VT_L2 +8,439 [275, 17,457] (placebo 0.85, year share), ES_IBS_t20_n1 +6,320 [-1,586, 15,548] (placebo 0.83).

### Evidence rows, not verdicts (PENDING on the leaderboard)
The 10 T3_8 rows (NQ/ES/RTY/YM RSI2_t10 and IBS_t20_n1, COMB_c3_R, COMB_c1_N) are the pre-2024 standalone OOS evidence (2013-2023, no Set A): NQ_RSI2_t10 CI [36, 301] $/wk (1 lot) placebo 0.99 (MDE 189), NQ_IBS_t20_n1 [-24, 426] (MDE 321), ES_RSI2 [-33, 204] (MDE 169), RTY_RSI2 [-46, 157] placebo 0.86 (MDE 145), YM_RSI2 [-52, 139] placebo 0.78 (MDE 136), COMB_c3_R [112, 1,235]. They support the dip-buy exposure on NQ and COMB but the ES/RTY/YM nulls could not see less than $136-197/wk per lot.

### T3.4 overlays are POST-HOC
The T3.4 "portfolio assembly" (V1 0.25x, V2 0.5x, V3 risk parity; out/T3_4_assembly.json) is NOT a preregistered cell and carries no verdict. Its components (ON_VT_L2, ORB_ASIA_15_v1 stop 60, ES s1.0) were chosen after seeing T3.1-T3.3 results, and the overlays are 0.96-0.99 correlated with Set A (Set A plus a small overlay). Its +$2.7k/+$5.4k/wk and maxDD -13..-16% are selection-biased and must not be quoted as evidence. The combined-system test of the registered PASS/CANDIDATE sleeves stacked on Set A (directive section 7) is the proper replacement and has not been run.

### Exports and registrations (T3.10a)
Series for every PASS/CANDIDATE row: l2vast/struct48/out/<sleeve>_{daily,weekly,trades}.parquet (16 sleeves; daily sums assert-verified against the saved npz series, scaled series verified against the rows file portfolio d_mean), manifest out/T3_export_manifest.json (23 leaderboard cells -> files, engine 1min/1s, scale factors), code code/t310a_export_1min.py, t310a_export_orb.py, t310a_groups.py, t310a_records.py. PAPER-ALL records: l2vast/struct48/paper_all/<cell_id>.json (23 new, none overwritten); 17 of the 23 sleeves/ratios were also registered by the near-miss re-score as NM_E_* (same sleeve at ratio 0.25) - the forward register should count each sleeve-ratio once.

## Superseded (pre-V2 criterion)
Everything below is the original T3 report text, written under the withdrawn rule (second system must cut Set A maxDD by >= 10%); its "no second system passes" verdict is superseded by the section above.

### REPORT STRUCT48 T3 - second system scored as a portfolio with Set A (2026-10-24) (original title)
Verdict: **no second system passes.** T3.1 0/30 primary cells (90 scored), T3.2 0/54 cells (162 rows), T3.3 0/20 cells (60 rows). Details: REPORT_STRUCT48_T3_1.md, _T3_2.md, _T3_3.md; rows/T3_{1,2,3}_final.json.

## Sub-track summary
- T3.1 D2 on ES,RTY,YM,CL,GC,ZN,6E,6J (1-min, conservative fills, $4.84 RT proxy, 1 tick/side): every market and both baskets negative standalone (WF, unit risk): ES -11.3k, RTY -6.8k, YM -20.5k, CL -17.9k, GC -21.2k, ZN -84.3k, 6E -48.9k, 6J -18.0k, basket8 -30.4k, +NQ -23.5k per wk. NQ 1-min engine vs true Set A: corr 0.75 (mean 31.3k vs 25.0k). Corr to Set A <= 0.5 everywhere only because no edge. 2013-2023 also negative (incl. NQ 1-min). Weekly correlation matrix: out/T3_1/corr_final.csv.
- T3.2 NQ triggers (ORB, Donchian, VWAP-trend, sweep; 1-s tape, live cost): one row meets maxDD -10% with mean not down (ORB_NY_30_v0 stop75 @0.25x) but holdout standalone -7.4k/wk. Closest: ORB_ASIA_15_v1 (8/10; fails maxDD and DSR; ~0.9 trades/wk). Portfolio maxDD rose in 153/162 rows. Corr <= 0.47 all.
- T3.3 NQ horizons: overnight drift is the only real sleeve. ON_VT (VIX9D/VIX<1): +2.2k/wk at 2 lots, holdout +2.0k, corr -0.03, @0.25 portfolio d mean +4.2k, CI [137,8729], maxDD only -7.4%, placebo 0.85, year-share fail. ON_none: +2.4k/wk, maxDD -14.5% @0.25, placebo 0.97, fails CI only. Swing/20d-breakout/weekly-open: ~0 or negative. DSR <= 0.51.

## T3.4 portfolio assembly (NOT PASSED - labelled)
Not a prereg'd scored grid: a single exploratory assembly (code/t34_assemble.py, out/T3_4_assembly.json), selection = best pass-count sleeve of each sub-track (none passed): ON_VT_L2 (T3.3), ORB_ASIA_15_v1 stop60 (T3.2), ES s1.0 (T3.1; negative sleeve, included only as the T3.1 best-by-count). Inverse-vol weights from trailing 26 weeks, re-estimated monthly, prior data only. Week alignment drops 1 partial week (141 wks; Set A WF mean 25,725, SD 104,512, maxDD 330,314 on weekly sums).
| portfolio | WF mean | SD | maxDD | worst wk | L8W mean | L8W maxDD | d-mean CI |
|---|---|---|---|---|---|---|---|
| Set A | 25,725 | 104,512 | 330,314 | -137,081 | 34,191 | 134,131 | |
| V1 overlay 0.25 | 28,429 | 109,670 | 278,934 (-15.6%) | -154,620 | 30,825 | 171,798 | [31, 5,449] |
| V2 overlay 0.5 | 31,133 | 117,161 | 285,368 (-13.6%) | -172,202 | 27,459 | 210,662 | [62, 10,898] |
| V3 full risk parity (sleeves incl. ES) | 29,088 | 125,901 | 570,174 | -301,485 | -3,102 | 299,655 | [-13k, 21k] |
Sleeve WF corr to Set A: ON_VT -0.03, ORB_ASIA -0.07 (0.074), ES 0.37. Caveats: mix of 3 weak sleeves chosen post-hoc after seeing T3.1-T3.3 results (selection bias, DSR of components <= 0.5, ON_VT placebo 0.85, V1/V2 maxDD gain mostly from ON_VT/ORB timing); worst week and L8W worse than Set A; correlation of portfolio with Set A 0.99/0.96 (it is Set A plus small overlay). Not a PASS: components fail placebo/DSR/holdout conditions; treat as a LEAD only for T3.3 overnight drift (ON_VT/ON_none) needing its own prereg'd confirmation (e.g. 2-lot to Set-A-ratio 0.25 sizing, different VIX-term variants, 2013-2023 positive in 8-9 of 11 years).

## Coverage limits
1-min data for non-NQ markets (conservative fills), fee proxy $4.84 for non-ES/NQ, fractional lots (ZN~90, 6E~67, 6J~75 contracts; margin not modelled), VX term file unused, overnight trades spanning contract rolls skipped.

## Note (coordinator request)
T3.4's 0.25x/0.5x overlays are post-hoc (components chosen after seeing T3.1-T3.3 results) and are 0.96-0.99 correlated with Set A (they are Set A plus a small overlay). The 2024+ holdout has already been looked at for ON_VT/ON_none in T3.3 (counted); T3.5 (overnight confirmation, pre-2024 out-of-sample, prereg T3_5) and T3.6 (20 further ideas, top 5 prereg'd) are running as extensions.

## Extensions after the coordinator request (T3.5-T3.8; detail in REPORT_STRUCT48_T3_5.md ... _T3_8.md)
- T3.5 overnight drift: NOT confirmed. Pre-2024 NQ: ON_none +$210/wk CI [-20,446] placebo 0.32; ON_VT +$173/wk CI [7,351] placebo 0.29; random 17.6 h holds earn about as much (drift is NQ's long bias, not overnight-specific or VT-filter-specific). 9/11 years positive; 12/14 calendar years positive; ON_VT portfolio gain 68% in 2025. 0/8 cells pass. 2024+ looked at twice (T3.3, T3.5), counted.
- T3.6/T3.7 (41 ideas total; 20 fixed-cell primaries scored in b1-b2, 22 in b3-b4+RSI2 combo): 0 pass. Only survivors are long-only NQ dip-buys at 15:55 (RSI2_t10, IBS_t20_n1): add mean ($1.0k/wk unit, corr ~0), fail only portfolio maxDD (+2.7% at 0.25x); hard caps / stops do not fix it.
- T3.8: RSI2_t10 independent support: NQ 2013-2023 OOS passes 6/6 gates (CI [36,301], placebo 0.986); on never-scored ES and RTY it is 8/9 (ES +$6.3k/wk CI [1.8k,11.1k]; RTY +$8.0k/wk CI [4.2k,12.5k], placebo >=0.99, corr <0.1) failing only p1 (maxDD +1.7%). IBS fails OOS. BRK_960_1080 (long NQ 16:00-18:00 ET): 8/9, fails p1 only, but only 4/11 positive years pre-2023. Combined dip-buy sleeve COMB_c3_R 8/9, p1 +9.3%, L8W -$5.1k/wk vs Set A. 0/17 pass.
- Overall T3 verdict: no passing second system (every near miss fails the maxDD-down->=10% condition); best mean-adding leads: RSI2 dip-buy on NQ/ES/RTY (one correlated exposure), BRK, overnight drift (unconfirmed).

