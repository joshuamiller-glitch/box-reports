# REPORT STRUCT48 T3.10b - robustness backlog of the T3 PASS / CANDIDATE sleeves (RESEARCH V2 section 7), 2026-10-24
Prereg l2vast/struct48/prereg/T3_10b.md, sha256 27c260bce8a07e30651532fe9337cbe488d3f8813c49e4348ae65a49ef0979c3 (in autopilot/DECISIONS.md at 15:13Z, before any number; one clarification line added, no check changed). **No new strategy cell, no new rule, 0 new trials (nothing appended to ledger/trials.jsonl), no holdout look added, nothing registered.** Research only; no downloads, deletions or live change. Verdicts by `s48score.verdict(cell,'sleeve')` (file sha256 54459dd5f19e22d2..., mtime 15:17Z, the scorer in force at the run; criteria untouched) with the `lb2.norm` field conventions.
Code: l2vast/struct48/code/t310b_{lib,gen,score,orb,1s,drift,bigplc,build,check}.py. Outputs: out/T3_10b/{score_*.json, score1s_*.json, score_ORB.json, drift_placebo.json, bigplc.json, tables.md}; rows/T3_10b_robustness.json (key `rows`, not `cells`, so lb2 does not ingest these re-scores as new leaderboard cells).

## 0. What was scored and how it was validated
15 unique series behind the 11 PASS + 12 CANDIDATE sleeve rows of the 15:07Z leaderboard: NQ RSI2_t10, RSI2T_t10, RSI2C_s20, RSI2CC_s20 (3-lot cap), COMB_c3_R, BRK_960_1080, GSHORT_t90, ON_none (L2/L4 are one series), IBS_t20_n1; ES/RTY/YM RSI2_t10, RTY IBS_t20_n1; NQ ORB_ASIA_15_v1 s60 / s75, ORB_ASIA_30_v1 s60. Each at risk ratio 0.25 / 0.5 / 1.0 (COMB: 0.25 and 0.5 as originally; 1.0 added and flagged, the 3-lot cap binds so it equals 0.5).
Validation: the 1x recomputation reproduces the stored rows exactly (scale k, portfolio mean-delta, placebo ranks with the original seeds, corr, year-share flag, neighbours) for all 13 1-min series, and the unit series are identical (max abs diff 0.0, 1x and 2x) to the T3.10a exports checked (RSI2_t10, COMB, BRK, ON_none, ES, RSI2C); k equals the T3.10a manifest scale factors. ORB 1x/2x series reproduce out/T3_2/*.npz to the cent (placebo draw 0 identical).
Sample size is the first thing to know: the dip-buy family has only 56-139 trades in the 142-week WF window (35-62 in the holdout): RSI2 70, RSI2T 56, RSI2C(C) 70, IBS 106, COMB 139, GSHORT 31 (9 in holdout), ES 60, RTY 66, YM 78; BRK (536) and ON_none (663) trade daily. Net edge per 1-lot trade is $0.7-2.0k for the dip-buys (cost is 1-2% of it) and only $106 (BRK) / $253 (ON_none) for the daily clock trades, which is why cost matters only for those two.
Detectable effect (directive section 2): the weekly WF test cannot see less than $24.6k/wk for an independent candidate (about 2.5x any sleeve gain here, so every weekly CI containing zero is expected); sleeves are judged by holdout sign + marginal Sharpe + corr, not by the CI. The bootstrap CIs below are therefore reported next to every result as a size-of-evidence statement, not as a gate.

## 1. Verdict changes (item 5) - the short list
Against the 15:07Z leaderboard snapshot (labels at ratio 0.5; identical at 0.25 / 1.0 unless stated):
| series | snapshot | after | trigger | failing condition |
|---|---|---|---|---|
| COMB_c3_R | PASS | **CANDIDATE** | 1.5x and 2x sleeve cost (1-min); also 1-s tape at 1x (live fill) | year_share>60%: the 2025 share of the WF gain is 0.5996 at 1x (limit 0.60), 0.6009 at 1.5x, 0.6079 at 2x; 2024 contributes ~0. A boundary flip (0.0013), not a collapse: mean/holdout/marginal Sharpe/corr/placebo (0.964, 0.962 fresh seed) all hold. |
| BRK_960_1080 | PASS | **DEAD** at 1-s tape with 1.5x / 2x cost; PASS at 1-s 1x (live model) and PASS at 1-min 2x | 1-s fills: 0.995 pt market slippage per side (about 4 ticks, +$30/trade) cuts net $/trade from 82 to 52 (1x), 29 (1.5x), 7 (2x) | neighbours_agree (BRK_975_1080 unit mean -$47/wk at 1.5x, -$131 at 2x); at 2x also year_share>60% and (ratio 0.5/1.0) marginal Sharpe not up. Fresh pre-2024: 2x-cost sign negative, 5/11 years positive, and the drift-matched diagnostic rank is 0.92 (WF) / 0.90 (pre) - BRK is the least robust PASS. |
| RTY_IBS_t20_n1 | CANDIDATE | DEAD only at the conservative 2x (8 ticks/side) | extreme stress on 1-min-only data | year_share>60%; placebo<0.95 (and marginal Sharpe at ratio 1.0). Stays CANDIDATE at conservative 1x and 1.5x. |
| YM_RSI2_t10 | CANDIDATE | DEAD at every cost level except the conservative 2x (CANDIDATE, rank noise) | NOT a robustness effect: the scorer (15:17Z) now counts placebo<0.95 as a failure and the 500-draw rank is 0.938; the 5,000-draw rank is 0.951, so with a tighter rank the only failure is year_share>60% (CANDIDATE) | year_share>60% + placebo<0.95 |
| ORB_ASIA_15_v1 s60 and s75 (all ratios) | CANDIDATE | **PASS** at 1x, 1.5x, 2x | label-source artefact, NOT robustness: the published CANDIDATE comes from `lb2.norm` not finding `port_WF_mean/port_WF_sd/A_*` in the T3.2 flat rows, so `marginal_sharpe_up` is None and the sleeve criterion fails. Recomputed from the stored series the marginal Sharpe is up (annualised 1.72 -> 2.02 at ratio 0.5), corr 0.08, holdout > 0, placebo 0.958 / 0.962: PASS under the unchanged function. | caveat that the verdict does not see: portfolio maxDD worsens +9% to +102% (ratio 0.25 to 1.0; WF window) and the implied size is 14-68 NQ lots on top of Set A's 28 (50-contract limit). **LEAD: fix lb2 key mapping for T3.2 rows or confirm these should read PASS.** |
| ORB_ASIA_30_v1 s60 | CANDIDATE | PASS at 1x/1.5x; CANDIDATE at 2x | 2x cost | year_share>60% |
| ON_none | PASS (T3.3 basis) | PASS at every cost level and on the 1-s tape (breakeven cost multiple 18x WF / 24x HOLD) - **but the placebo behind that PASS is the sign-randomised-night draw, which any long-biased series beats**. Drift-matched diagnostic (random long windows of the same 17.6 h): rank 0.22 (WF), 0.10 (pre-2024); T3.5 had 0.32. This agrees with the current leaderboard, which already shows ON_none_L2/L4 as superseded DEAD via NM_E. | | placebo (drift-matched) |
No other label changes: RSI2_t10, RSI2T_t10, RSI2C_s20, RSI2CC_s20, GSHORT_t90, ES_RSI2_t10, RTY_RSI2_t10 stay PASS and IBS_t20_n1 stays CANDIDATE at 1.5x, 2x, 1-s fills (also 1.5x/2x of the 1-s model) and, for ES/RTY, the conservative 4-tick model at 1x, 1.5x and 2x.

Fresh-seed replication (item 4) does not change a label under the unchanged criteria but moves the placebo bar: pre-2024 fresh-seed ranks are RSI2_t10 0.988, COMB 0.968, ON_none 0.986 (sign-random basis), BRK 0.988 (sign-random basis) but **RSI2T 0.926, RSI2C 0.932, RSI2CC 0.934, ES 0.944, RTY 0.904** (5,000 draws: 0.911, 0.917, 0.920, 0.962, 0.870). If the NM-E convention (placebo = min(WF rank, independent pre-2024 rank)) were applied to these series they would read CANDIDATE (RTY_RSI2 DEAD on the 5,000-draw rank; ES_RSI2 0.944 is CANDIDATE with 500 draws but 0.962 with 5,000, i.e. stays PASS). The sign agrees everywhere; the pre-2024 weekly means are small and mostly CI-includes-zero (all but RSI2_t10 [36,301], RSI2T [6,188] and COMB [112,1235]).

## 2. Findings by backlog item
**Item 1 - bootstrap (10,000 week-block draws, WF index matrix seed 3101001, HOLD seed 3101002; Table 2).** At ratio 0.5: portfolio-minus-Set A mean CI excludes zero for 8 of 10 PASS series (not GSHORT [-2.5k, 14.8k], not ON_none [-1.0k, 15.8k]); P(mean>0) 0.92-1.00. The marginal-Sharpe-up statement (b) is the weakest leg: its CI excludes zero at ratio 0.5 only for RSI2CC, COMB and RTY_RSI2 (P(b>0) 0.74-1.00; the lower limit is -0.010 for RSI2_t10); at ratio 0.25 it excludes zero for 8 of 10 PASS series (not GSHORT, ON_none). Standalone holdout mean (c, 68 weeks): CI excludes zero for RSI2_t10, RSI2C, RSI2CC, GSHORT, ES, RTY; includes zero for RSI2T (P>0 0.92), COMB (0.96), BRK (0.94), ON_none (0.93). Direction is right everywhere (P>0 >= 0.92) - the evidence is "sign-consistent, small sample", not "significant".
**Item 2 - 1.5x / 2x sleeve cost (Table 3).** 1-min dip-buys are immune (cost is 1-2% of $0.7-2.0k per trade; breakeven cost multiple > 30x). Costly ones: BRK breakeven 8.1x (WF) / 8.7x (HOLD) at 1-min costs, ON_none 18x / 24x, RTY_IBS 17x / 21x, ORB_ASIA_15 s60 7.4x WF. Only COMB (year-share boundary) and ORB_ASIA_30 s60 at 2x (year-share) change label. The placebo rank does not move with cost for the 1-min sleeves (placebos have the same trade count and are re-priced together); ORB placebos were re-simulated at each multiple (0.958 -> 0.960).
**Item 3 - 1-s tape (Table 4).** NQ sleeves re-filled on the fp2lib 1-s arrays with the t32lib model (market = 1-min open of the order minute +/- 0.995 pt; stop join 1.01 pt on 1-s lows; $4.84 RT; all 2023-02+ trades covered and filled, 0 dropped; 15 trades with a data-set roll mismatch >5 pt kept at 1-min gross, BRK 10, ON 5). The live fill costs +$27.7-30.3 per trade over the 1-min model (+$72-75 at 2x). Dip-buys lose 2-6% of net per trade (GSHORT 6%) (e.g. RSI2 1,633 -> 1,604; RSI2C 3 of 93 trades stopped) and keep their labels at 1x, 1.5x, 2x; BRK falls from 82 to 52 $/trade (see section 1); ON_none 216 -> 186 and still PASS (sign-random placebo basis). ORB sleeves are already 1-s fills (native). **Coverage limit:** the 1-s tape exists for NQ only and only from 2023-02-10, so ES, RTY, YM (and GC/CL/ZN/6E/6J) have 1-min data only: they were re-scored with the conservative model (4 ticks per side adverse + $4.84 RT: ES $104.84 vs $29.84, RTY/YM $44.84 vs $14.84) and 1.5x / 2x of it; ES_RSI2 and RTY_RSI2 stay PASS at all three, RTY_IBS drops to DEAD only at 2x, YM_RSI2 is DEAD on the scorer's own 1x rule (see section 1). No short-term fill-timing detail (queue, partial fills) is modelled for these markets.
**Item 4 - fresh seeds, other windows (Table 5, Table 7).** WF-window fresh-seed ranks reproduce the original ranks within noise (RSI2 0.974 vs 0.978; RSI2T 0.964 vs 0.956; RSI2C 0.980 vs 0.978; RSI2CC 0.986 vs 0.984; COMB 0.962 vs 0.964; BRK 0.988 vs 0.994; GSHORT 0.956 vs 0.962; ON 0.966 vs 0.966; ES 0.986 vs 0.990; RTY 1.000). Halves (71 weeks each, sleeve re-scaled inside the half): standalone mean, portfolio delta and marginal Sharpe have the right sign in **all 20 half-windows (10 series x 2)**, corr stays within -0.17..0.19; the fresh-seed within-half placebo rank is below 0.90 in 5 of 20 (RSI2 H1 0.872, RSI2T H2 0.848, COMB H1 0.830, GSHORT H2 0.774, ON H1 0.846; ES H1 0.900 and BRK H2 0.930 are marginal) - expected at half the power, but GSHORT H2 and COMB H1 are the thin ones. Pre-2024 (NQ 2013-02..2023-12, ES 2013-02, RTY 2017-08; no Set A): sign agrees for all 9 series with history (GSHORT has no pre-2023 history: it needs the Set A gate), 2x-cost sign agrees for all except BRK (-$15/wk), positive calendar years 8/11 (RSI2 family), 9/11 (COMB, ON, ES), 5/11 (BRK), 5/7 (RTY).
Rank noise (Table 7): with 500 draws the SE of a rank near 0.95 is 0.010 - the same size as the spread between seeds (ES pre-2024 0.944 vs 0.962; YM WF 0.938 vs 0.951; RSI2T WF 0.956 / 0.964 / 0.953). A PASS/CANDIDATE call that rests on 0.95 vs 0.94 should be read with that error bar.

## 3. Flags for the LEAD / coordinator
1. lb2 does not read T3.2 flat rows' `port_WF_mean/port_WF_sd/WF_A_mean/WF_A_sd` -> ORB_ASIA cells are labelled CANDIDATE for a missing field; with the field they are PASS (ratio 0.5: annualised Sharpe of Set A 1.72 -> 2.02 with the ORB_ASIA_15 s60 sleeve). Note the maxDD/size caveat above.
2. ON_none's PASS rests on the sign-randomised placebo; the drift-matched rank is 0.22 / 0.10 (consistent with T3.5 0.32 and the NM_E supersession). BRK_960_1080's placebo is the same sign-random type (the sleeve trades every eligible day): drift-matched ranks 0.92 / 0.90.
3. s48score.verdict changed at 15:17Z (placebo<0.95 now a secondary failure): re-running this job after later scorer edits needs `python3 code/t310b_score.py && python3 code/t310b_orb.py && python3 code/t310b_1s.py && python3 code/t310b_build.py` (about 6 minutes on 3-6 cores).
4. Forward-register implication: the series with the least cushion are COMB (year-share boundary, 2024 contributes nothing), GSHORT (31 WF trades, 9 in holdout; CI of the mean-delta includes zero, P(b>0) 0.74), BRK (cost-fragile) and ON_none (no overnight specificity). RSI2_t10 (NQ), ES_RSI2_t10, RTY_RSI2_t10 and RSI2CC/RSI2C carry the evidence; RSI2 NQ/ES/RTY/YM/IBS/COMB are one correlated dip-buy exposure (all trade the same 15:55 clock).
5. Cores: the whole job needs minutes (placebos are cheap); peak WANT 6 via corepool; no idle backlog remains inside this scope. Remaining open backlog items in directive section 7 (combined system, live-vs-replay) belong to other agents.

## 4. Tables (full, generated by code/t310b_build.py from out/T3_10b/*.json)
### Table 1 - verdict ladder (sleeve costs only; Set A unchanged). Labels from s48score.verdict(cell,"sleeve"); 1x = recomputation of the leaderboard basis (no 2x sign); stress columns apply the 2x-cost-sign secondary at that level

| series | status (task list) | ratio | 1x | 1.5x | 2x | 1-s / cons 1x | 1-s / cons 1.5x | 1-s / cons 2x | worst | failing condition at worst |
|---|---|---|---|---|---|---|---|---|---|---|
| RSI2_t10 | PASS | 0.25 | PASS | PASS | PASS | PASS | PASS | PASS | **PASS** |  |
| RSI2_t10 | PASS | 0.5 | PASS | PASS | PASS | PASS | PASS | PASS | **PASS** |  |
| RSI2_t10 | PASS | 1.0 | PASS | PASS | PASS | PASS | PASS | PASS | **PASS** |  |
| RSI2T_t10 | PASS | 0.25 | PASS | PASS | PASS | PASS | PASS | PASS | **PASS** |  |
| RSI2T_t10 | PASS | 0.5 | PASS | PASS | PASS | PASS | PASS | PASS | **PASS** |  |
| RSI2T_t10 | PASS | 1.0 | PASS | PASS | PASS | PASS | PASS | PASS | **PASS** |  |
| RSI2C_s20 | PASS | 0.25 | PASS | PASS | PASS | PASS | PASS | PASS | **PASS** |  |
| RSI2C_s20 | PASS | 0.5 | PASS | PASS | PASS | PASS | PASS | PASS | **PASS** |  |
| RSI2C_s20 | PASS | 1.0 | PASS | PASS | PASS | PASS | PASS | PASS | **PASS** |  |
| RSI2CC_s20 | PASS | 0.25 | PASS | PASS | PASS | PASS | PASS | PASS | **PASS** |  |
| RSI2CC_s20 | PASS | 0.5 | PASS | PASS | PASS | PASS | PASS | PASS | **PASS** |  |
| RSI2CC_s20 | PASS | 1.0 | PASS | PASS | PASS | PASS | PASS | PASS | **PASS** |  |
| COMB_c3_R | PASS | 0.25 | PASS | CANDIDATE | CANDIDATE | CANDIDATE | CANDIDATE | CANDIDATE | **CANDIDATE** | year_share>60% |
| COMB_c3_R | PASS | 0.5 | PASS | CANDIDATE | CANDIDATE | CANDIDATE | CANDIDATE | CANDIDATE | **CANDIDATE** | year_share>60% |
| COMB_c3_R | PASS | 1.0 | PASS | CANDIDATE | CANDIDATE | - | - | - | **CANDIDATE** | year_share>60% |
| BRK_960_1080 | PASS | 0.25 | PASS | PASS | PASS | PASS | DEAD | DEAD | **DEAD** | neighbours_agree |
| BRK_960_1080 | PASS | 0.5 | PASS | PASS | PASS | PASS | DEAD | DEAD | **DEAD** | neighbours_agree |
| BRK_960_1080 | PASS | 1.0 | PASS | PASS | PASS | PASS | DEAD | DEAD | **DEAD** | neighbours_agree; sleeve_marginal_sharpe_up; standalone_hold>0&marginal_Sharpe_up&corr<=0.5; sleeve_secondary |
| GSHORT_t90 | PASS | 0.25 | PASS | PASS | PASS | PASS | PASS | PASS | **PASS** |  |
| GSHORT_t90 | PASS | 0.5 | PASS | PASS | PASS | PASS | PASS | PASS | **PASS** |  |
| GSHORT_t90 | PASS | 1.0 | PASS | PASS | PASS | PASS | PASS | PASS | **PASS** |  |
| ON_none | PASS | 0.25 | PASS | PASS | PASS | PASS | PASS | PASS | **PASS** |  |
| ON_none | PASS | 0.5 | PASS | PASS | PASS | PASS | PASS | PASS | **PASS** |  |
| ON_none | PASS | 1.0 | PASS | PASS | PASS | PASS | PASS | PASS | **PASS** |  |
| ES_RSI2_t10 | PASS | 0.25 | PASS | PASS | PASS | PASS | PASS | PASS | **PASS** |  |
| ES_RSI2_t10 | PASS | 0.5 | PASS | PASS | PASS | PASS | PASS | PASS | **PASS** |  |
| ES_RSI2_t10 | PASS | 1.0 | PASS | PASS | PASS | PASS | PASS | PASS | **PASS** |  |
| RTY_RSI2_t10 | PASS | 0.25 | PASS | PASS | PASS | PASS | PASS | PASS | **PASS** |  |
| RTY_RSI2_t10 | PASS | 0.5 | PASS | PASS | PASS | PASS | PASS | PASS | **PASS** |  |
| RTY_RSI2_t10 | PASS | 1.0 | PASS | PASS | PASS | PASS | PASS | PASS | **PASS** |  |
| IBS_t20_n1 | CANDIDATE | 0.25 | CANDIDATE | CANDIDATE | CANDIDATE | CANDIDATE | CANDIDATE | CANDIDATE | **CANDIDATE** |  |
| IBS_t20_n1 | CANDIDATE | 0.5 | CANDIDATE | CANDIDATE | CANDIDATE | CANDIDATE | CANDIDATE | CANDIDATE | **CANDIDATE** |  |
| IBS_t20_n1 | CANDIDATE | 1.0 | CANDIDATE | CANDIDATE | CANDIDATE | CANDIDATE | CANDIDATE | CANDIDATE | **CANDIDATE** |  |
| YM_RSI2_t10 | CANDIDATE | 0.25 | DEAD | DEAD | DEAD | DEAD | DEAD | CANDIDATE | **DEAD** |  |
| YM_RSI2_t10 | CANDIDATE | 0.5 | DEAD | DEAD | DEAD | DEAD | DEAD | CANDIDATE | **DEAD** |  |
| YM_RSI2_t10 | CANDIDATE | 1.0 | DEAD | DEAD | DEAD | DEAD | DEAD | CANDIDATE | **DEAD** |  |
| RTY_IBS_t20_n1 | CANDIDATE | 0.25 | CANDIDATE | CANDIDATE | CANDIDATE | CANDIDATE | CANDIDATE | DEAD | **DEAD** | year_share>60%; placebo<0.95 |
| RTY_IBS_t20_n1 | CANDIDATE | 0.5 | CANDIDATE | CANDIDATE | CANDIDATE | CANDIDATE | CANDIDATE | DEAD | **DEAD** | year_share>60%; placebo<0.95 |
| RTY_IBS_t20_n1 | CANDIDATE | 1.0 | CANDIDATE | CANDIDATE | CANDIDATE | CANDIDATE | CANDIDATE | DEAD | **DEAD** | sleeve_marginal_sharpe_up; standalone_hold>0&marginal_Sharpe_up&corr<=0.5; sleeve_secondary; year_share>60%; placebo<0.95 |
| ORB_ASIA_15_v1__s60 | CANDIDATE | 0.25 | PASS | PASS | PASS | n/a (1-s native) | - | - | **PASS** |  |
| ORB_ASIA_15_v1__s60 | CANDIDATE | 0.5 | PASS | PASS | PASS | n/a (1-s native) | - | - | **PASS** |  |
| ORB_ASIA_15_v1__s60 | CANDIDATE | 1.0 | PASS | PASS | PASS | n/a (1-s native) | - | - | **PASS** |  |
| ORB_ASIA_30_v1__s60 | CANDIDATE | 0.25 | PASS | PASS | CANDIDATE | n/a (1-s native) | - | - | **CANDIDATE** | year_share>60% |
| ORB_ASIA_30_v1__s60 | CANDIDATE | 0.5 | PASS | PASS | CANDIDATE | n/a (1-s native) | - | - | **CANDIDATE** | year_share>60% |
| ORB_ASIA_30_v1__s60 | CANDIDATE | 1.0 | PASS | PASS | CANDIDATE | n/a (1-s native) | - | - | **CANDIDATE** | year_share>60% |
| ORB_ASIA_15_v1__s75 | CANDIDATE | 0.25 | PASS | PASS | PASS | n/a (1-s native) | - | - | **PASS** |  |
| ORB_ASIA_15_v1__s75 | CANDIDATE | 0.5 | PASS | PASS | PASS | n/a (1-s native) | - | - | **PASS** |  |
| ORB_ASIA_15_v1__s75 | CANDIDATE | 1.0 | PASS | PASS | PASS | n/a (1-s native) | - | - | **PASS** |  |

### Table 2 - item 1: 10,000-draw week-block bootstrap (WF idx seed 3101001, HOLD idx seed 3101002); (a) portfolio-minus-Set A weekly mean $/wk; (b) marginal annualised Sharpe (Set A+k*sleeve minus Set A); (c) standalone holdout weekly mean $/wk (68 weeks)

| series | ratio | (a) point [2.5,97.5] P>0 | (b) point [2.5,97.5] P>0 | (c) point [2.5,97.5] P>0 |
|---|---|---|---|---|
| RSI2_t10 | 0.25 | 5,099 [985, 9,631] 0.993 | 0.313 [0.047, 0.609] 0.990 | 5,496 [164, 11,484] 0.979 |
| RSI2_t10 | 0.5 | 10,197 [1,971, 19,262] 0.993 | 0.491 [-0.010, 1.001] 0.971 | 10,991 [327, 22,969] 0.979 |
| RSI2_t10 | 1.0 | 20,394 [3,941, 38,525] 0.993 | 0.546 [-0.317, 1.343] 0.904 | 21,983 [654, 45,938] 0.979 |
| RSI2T_t10 | 0.25 | 4,441 [322, 8,898] 0.984 | 0.291 [0.023, 0.599] 0.985 | 5,303 [-1,868, 13,416] 0.922 |
| RSI2T_t10 | 0.5 | 8,882 [644, 17,797] 0.984 | 0.450 [-0.049, 0.979] 0.962 | 10,606 [-3,736, 26,833] 0.922 |
| RSI2T_t10 | 1.0 | 17,765 [1,288, 35,594] 0.984 | 0.468 [-0.386, 1.284] 0.867 | 21,212 [-7,472, 53,665] 0.922 |
| RSI2C_s20 | 0.25 | 5,284 [1,062, 9,748] 0.994 | 0.331 [0.051, 0.644] 0.989 | 6,383 [25, 13,460] 0.976 |
| RSI2C_s20 | 0.5 | 10,568 [2,123, 19,496] 0.994 | 0.524 [-0.016, 1.074] 0.971 | 12,766 [50, 26,919] 0.976 |
| RSI2C_s20 | 1.0 | 21,137 [4,246, 38,992] 0.994 | 0.595 [-0.341, 1.468] 0.902 | 25,531 [100, 53,838] 0.976 |
| RSI2CC_s20 | 0.25 | 2,646 [532, 4,882] 0.994 | 0.182 [0.041, 0.345] 0.994 | 3,196 [12, 6,740] 0.976 |
| RSI2CC_s20 | 0.5 | 2,646 [532, 4,882] 0.994 | 0.182 [0.041, 0.345] 0.994 | 3,196 [12, 6,740] 0.976 |
| RSI2CC_s20 | 1.0 | 2,646 [532, 4,882] 0.994 | 0.182 [0.041, 0.345] 0.994 | 3,196 [12, 6,740] 0.976 |
| COMB_c3_R | 0.25 | 2,831 [230, 5,597] 0.984 | 0.195 [0.012, 0.400] 0.982 | 3,490 [-357, 7,713] 0.961 |
| COMB_c3_R | 0.5 | 2,831 [230, 5,597] 0.984 | 0.195 [0.012, 0.400] 0.982 | 3,490 [-357, 7,713] 0.961 |
| COMB_c3_R | 1.0 | 2,831 [230, 5,597] 0.984 | 0.195 [0.012, 0.400] 0.982 | 3,490 [-357, 7,713] 0.961 |
| BRK_960_1080 | 0.25 | 4,853 [805, 9,271] 0.991 | 0.273 [0.020, 0.543] 0.983 | 5,315 [-1,352, 13,039] 0.938 |
| BRK_960_1080 | 0.5 | 9,707 [1,609, 18,543] 0.991 | 0.417 [-0.049, 0.902] 0.962 | 10,629 [-2,704, 26,077] 0.938 |
| BRK_960_1080 | 1.0 | 19,413 [3,218, 37,086] 0.991 | 0.442 [-0.325, 1.241] 0.873 | 21,259 [-5,407, 52,155] 0.938 |
| GSHORT_t90 | 0.25 | 2,970 [-1,266, 7,376] 0.917 | 0.140 [-0.159, 0.428] 0.832 | 3,931 [609, 8,504] 0.993 |
| GSHORT_t90 | 0.5 | 5,941 [-2,532, 14,753] 0.917 | 0.172 [-0.403, 0.704] 0.742 | 7,862 [1,218, 17,008] 0.993 |
| GSHORT_t90 | 1.0 | 11,882 [-5,063, 29,505] 0.917 | 0.060 [-0.885, 0.941] 0.579 | 15,724 [2,436, 34,017] 0.993 |
| ON_none | 0.25 | 3,738 [-497, 7,914] 0.958 | 0.199 [-0.087, 0.481] 0.920 | 4,965 [-1,766, 11,609] 0.930 |
| ON_none | 0.5 | 7,476 [-993, 15,828] 0.958 | 0.280 [-0.284, 0.822] 0.848 | 9,929 [-3,532, 23,218] 0.930 |
| ON_none | 1.0 | 14,951 [-1,986, 31,656] 0.958 | 0.225 [-0.752, 1.166] 0.693 | 19,859 [-7,065, 46,436] 0.930 |
| ES_RSI2_t10 | 0.25 | 6,279 [2,089, 10,700] 0.997 | 0.324 [0.050, 0.583] 0.989 | 7,257 [3,117, 11,713] 1.000 |
| ES_RSI2_t10 | 0.5 | 12,559 [4,178, 21,401] 0.997 | 0.510 [-0.019, 0.966] 0.971 | 14,513 [6,234, 23,425] 1.000 |
| ES_RSI2_t10 | 1.0 | 25,117 [8,355, 42,802] 0.997 | 0.613 [-0.301, 1.381] 0.918 | 29,026 [12,469, 46,851] 1.000 |
| RTY_RSI2_t10 | 0.25 | 8,005 [3,900, 12,485] 1.000 | 0.449 [0.198, 0.714] 1.000 | 12,210 [5,437, 19,698] 1.000 |
| RTY_RSI2_t10 | 0.5 | 16,009 [7,799, 24,970] 1.000 | 0.738 [0.276, 1.213] 0.999 | 24,421 [10,875, 39,397] 1.000 |
| RTY_RSI2_t10 | 1.0 | 32,018 [15,598, 49,940] 1.000 | 0.965 [0.205, 1.741] 0.993 | 48,842 [21,749, 78,793] 1.000 |
| IBS_t20_n1 | 0.25 | 4,232 [133, 8,691] 0.980 | 0.264 [-0.009, 0.564] 0.971 | 5,486 [323, 11,176] 0.983 |
| IBS_t20_n1 | 0.5 | 8,465 [266, 17,381] 0.980 | 0.399 [-0.111, 0.921] 0.935 | 10,973 [645, 22,352] 0.983 |
| IBS_t20_n1 | 1.0 | 16,930 [532, 34,763] 0.980 | 0.395 [-0.470, 1.239] 0.826 | 21,945 [1,291, 44,705] 0.983 |
| YM_RSI2_t10 | 0.25 | 4,137 [6, 8,519] 0.975 | 0.182 [-0.095, 0.465] 0.904 | 5,651 [889, 10,368] 0.991 |
| YM_RSI2_t10 | 0.5 | 8,274 [12, 17,038] 0.975 | 0.252 [-0.281, 0.756] 0.837 | 11,303 [1,778, 20,736] 0.991 |
| YM_RSI2_t10 | 1.0 | 16,548 [24, 34,076] 0.975 | 0.209 [-0.679, 1.043] 0.704 | 22,605 [3,556, 41,471] 0.991 |
| RTY_IBS_t20_n1 | 0.25 | 3,618 [-618, 7,976] 0.953 | 0.196 [-0.096, 0.503] 0.906 | 5,002 [-711, 10,934] 0.957 |
| RTY_IBS_t20_n1 | 0.5 | 7,236 [-1,236, 15,952] 0.953 | 0.275 [-0.268, 0.847] 0.836 | 10,003 [-1,422, 21,867] 0.957 |
| RTY_IBS_t20_n1 | 1.0 | 14,473 [-2,472, 31,903] 0.953 | 0.213 [-0.685, 1.143] 0.677 | 20,006 [-2,845, 43,735] 0.957 |
| ORB_ASIA_15_v1__s60 | 0.25 | 4,069 [247, 7,896] 0.983 | 0.197 [-0.055, 0.460] 0.933 | 6,123 [866, 11,648] 0.990 |
| ORB_ASIA_15_v1__s60 | 0.5 | 8,138 [495, 15,792] 0.983 | 0.294 [-0.173, 0.773] 0.887 | 12,245 [1,733, 23,296] 0.990 |
| ORB_ASIA_15_v1__s60 | 1.0 | 16,276 [989, 31,585] 0.983 | 0.299 [-0.481, 1.098] 0.765 | 24,491 [3,465, 46,592] 0.990 |
| ORB_ASIA_30_v1__s60 | 0.25 | 4,001 [113, 8,041] 0.978 | 0.189 [-0.074, 0.470] 0.914 | 6,655 [980, 12,585] 0.990 |
| ORB_ASIA_30_v1__s60 | 0.5 | 8,001 [226, 16,083] 0.978 | 0.273 [-0.209, 0.788] 0.860 | 13,310 [1,960, 25,171] 0.990 |
| ORB_ASIA_30_v1__s60 | 1.0 | 16,003 [451, 32,166] 0.978 | 0.254 [-0.535, 1.082] 0.729 | 26,620 [3,920, 50,341] 0.990 |
| ORB_ASIA_15_v1__s75 | 0.25 | 3,864 [253, 7,462] 0.981 | 0.197 [-0.044, 0.438] 0.945 | 7,340 [2,754, 12,025] 0.999 |
| ORB_ASIA_15_v1__s75 | 0.5 | 7,727 [506, 14,923] 0.981 | 0.302 [-0.157, 0.763] 0.904 | 14,680 [5,508, 24,051] 0.999 |
| ORB_ASIA_15_v1__s75 | 1.0 | 15,455 [1,012, 29,846] 0.981 | 0.324 [-0.455, 1.111] 0.795 | 29,359 [11,016, 48,101] 0.999 |

### Table 3 - item 2: cost re-score (1-min sleeves: commission+1 tick/side x mult; ORB: engine mult path, own locks). stand = standalone WF mean at the ratio ($/wk), hold = standalone holdout mean, plc = placebo rank (placebos re-priced), msh = marginal Sharpe up, nb = neighbours agree, yr = year share ok

| series | ratio | cost | stand WF | hold | corr | plc | msh | nb | yr | verdict | failed | breakeven cost x (WF / HOLD) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| RSI2_t10 | 0.25 | 1.0x | 5,099 | 5,496 | -0.049 | 0.978 | Y | Y | Y | PASS |  | 30.0 / 30.0 |
| RSI2_t10 | 0.25 | 1.5x | 5,080 | 5,476 | -0.049 | 0.978 | Y | Y | Y | PASS |  |  |
| RSI2_t10 | 0.25 | 2.0x | 5,061 | 5,457 | -0.049 | 0.978 | Y | Y | Y | PASS |  |  |
| RSI2_t10 | 0.5 | 1.0x | 10,197 | 10,991 | -0.049 | 0.978 | Y | Y | Y | PASS |  | 30.0 / 30.0 |
| RSI2_t10 | 0.5 | 1.5x | 10,160 | 10,953 | -0.049 | 0.978 | Y | Y | Y | PASS |  |  |
| RSI2_t10 | 0.5 | 2.0x | 10,123 | 10,914 | -0.049 | 0.978 | Y | Y | Y | PASS |  |  |
| RSI2_t10 | 1.0 | 1.0x | 20,394 | 21,983 | -0.049 | 0.978 | Y | Y | Y | PASS |  | 30.0 / 30.0 |
| RSI2_t10 | 1.0 | 1.5x | 20,320 | 21,906 | -0.049 | 0.978 | Y | Y | Y | PASS |  |  |
| RSI2_t10 | 1.0 | 2.0x | 20,246 | 21,828 | -0.049 | 0.978 | Y | Y | Y | PASS |  |  |
| RSI2T_t10 | 0.25 | 1.0x | 4,441 | 5,303 | -0.094 | 0.956 | Y | Y | Y | PASS |  | 30.0 / 30.0 |
| RSI2T_t10 | 0.25 | 1.5x | 4,420 | 5,279 | -0.094 | 0.956 | Y | Y | Y | PASS |  |  |
| RSI2T_t10 | 0.25 | 2.0x | 4,399 | 5,254 | -0.095 | 0.956 | Y | Y | Y | PASS |  |  |
| RSI2T_t10 | 0.5 | 1.0x | 8,882 | 10,606 | -0.094 | 0.956 | Y | Y | Y | PASS |  | 30.0 / 30.0 |
| RSI2T_t10 | 0.5 | 1.5x | 8,840 | 10,557 | -0.094 | 0.956 | Y | Y | Y | PASS |  |  |
| RSI2T_t10 | 0.5 | 2.0x | 8,798 | 10,509 | -0.095 | 0.956 | Y | Y | Y | PASS |  |  |
| RSI2T_t10 | 1.0 | 1.0x | 17,765 | 21,212 | -0.094 | 0.956 | Y | Y | Y | PASS |  | 30.0 / 30.0 |
| RSI2T_t10 | 1.0 | 1.5x | 17,680 | 21,115 | -0.094 | 0.956 | Y | Y | Y | PASS |  |  |
| RSI2T_t10 | 1.0 | 2.0x | 17,596 | 21,017 | -0.095 | 0.956 | Y | Y | Y | PASS |  |  |
| RSI2C_s20 | 0.25 | 1.0x | 5,284 | 6,383 | -0.059 | 0.978 | Y | Y | Y | PASS |  | 30.0 / 30.0 |
| RSI2C_s20 | 0.25 | 1.5x | 5,262 | 6,360 | -0.059 | 0.978 | Y | Y | Y | PASS |  |  |
| RSI2C_s20 | 0.25 | 2.0x | 5,240 | 6,337 | -0.059 | 0.978 | Y | Y | Y | PASS |  |  |
| RSI2C_s20 | 0.5 | 1.0x | 10,568 | 12,766 | -0.059 | 0.978 | Y | Y | Y | PASS |  | 30.0 / 30.0 |
| RSI2C_s20 | 0.5 | 1.5x | 10,525 | 12,720 | -0.059 | 0.978 | Y | Y | Y | PASS |  |  |
| RSI2C_s20 | 0.5 | 2.0x | 10,481 | 12,674 | -0.059 | 0.978 | Y | Y | Y | PASS |  |  |
| RSI2C_s20 | 1.0 | 1.0x | 21,137 | 25,531 | -0.059 | 0.978 | Y | Y | Y | PASS |  | 30.0 / 30.0 |
| RSI2C_s20 | 1.0 | 1.5x | 21,049 | 25,440 | -0.059 | 0.978 | Y | Y | Y | PASS |  |  |
| RSI2C_s20 | 1.0 | 2.0x | 20,962 | 25,348 | -0.059 | 0.978 | Y | Y | Y | PASS |  |  |
| RSI2CC_s20 | 0.25 | 1.0x | 2,646 | 3,196 | -0.059 | 0.984 | Y | Y | Y | PASS |  | 30.0 / 30.0 |
| RSI2CC_s20 | 0.25 | 1.5x | 2,635 | 3,185 | -0.059 | 0.984 | Y | Y | Y | PASS |  |  |
| RSI2CC_s20 | 0.25 | 2.0x | 2,624 | 3,173 | -0.059 | 0.984 | Y | Y | Y | PASS |  |  |
| RSI2CC_s20 | 0.5 | 1.0x | 2,646 | 3,196 | -0.059 | 0.984 | Y | Y | Y | PASS |  | 30.0 / 30.0 |
| RSI2CC_s20 | 0.5 | 1.5x | 2,635 | 3,185 | -0.059 | 0.984 | Y | Y | Y | PASS |  |  |
| RSI2CC_s20 | 0.5 | 2.0x | 2,624 | 3,173 | -0.059 | 0.984 | Y | Y | Y | PASS |  |  |
| RSI2CC_s20 | 1.0 | 1.0x | 2,646 | 3,196 | -0.059 | 0.984 | Y | Y | Y | PASS |  | 30.0 / 30.0 |
| RSI2CC_s20 | 1.0 | 1.5x | 2,635 | 3,185 | -0.059 | 0.984 | Y | Y | Y | PASS |  |  |
| RSI2CC_s20 | 1.0 | 2.0x | 2,624 | 3,173 | -0.059 | 0.984 | Y | Y | Y | PASS |  |  |
| COMB_c3_R | 0.25 | 1.0x | 2,831 | 3,490 | -0.076 | 0.964 | Y | Y | Y | PASS |  | 30.0 / 30.0 |
| COMB_c3_R | 0.25 | 1.5x | 2,812 | 3,472 | -0.076 | 0.964 | Y | Y | N | CANDIDATE | year_share>60% |  |
| COMB_c3_R | 0.25 | 2.0x | 2,767 | 3,453 | -0.079 | 0.958 | Y | Y | N | CANDIDATE | year_share>60% |  |
| COMB_c3_R | 0.5 | 1.0x | 2,831 | 3,490 | -0.076 | 0.964 | Y | Y | Y | PASS |  | 30.0 / 30.0 |
| COMB_c3_R | 0.5 | 1.5x | 2,812 | 3,472 | -0.076 | 0.964 | Y | Y | N | CANDIDATE | year_share>60% |  |
| COMB_c3_R | 0.5 | 2.0x | 2,767 | 3,453 | -0.079 | 0.958 | Y | Y | N | CANDIDATE | year_share>60% |  |
| COMB_c3_R | 1.0 | 1.0x | 2,831 | 3,490 | -0.076 | 0.964 | Y | Y | Y | PASS |  | 30.0 / 30.0 |
| COMB_c3_R | 1.0 | 1.5x | 2,812 | 3,472 | -0.076 | 0.964 | Y | Y | N | CANDIDATE | year_share>60% |  |
| COMB_c3_R | 1.0 | 2.0x | 2,767 | 3,453 | -0.079 | 0.958 | Y | Y | N | CANDIDATE | year_share>60% |  |
| BRK_960_1080 | 0.25 | 1.0x | 4,853 | 5,315 | 0.000 | 0.994 | Y | Y | Y | PASS |  | 8.1 / 8.7 |
| BRK_960_1080 | 0.25 | 1.5x | 4,514 | 4,969 | 0.000 | 0.994 | Y | Y | Y | PASS |  |  |
| BRK_960_1080 | 0.25 | 2.0x | 4,174 | 4,624 | 0.000 | 0.994 | Y | Y | Y | PASS |  |  |
| BRK_960_1080 | 0.5 | 1.0x | 9,707 | 10,629 | 0.000 | 0.994 | Y | Y | Y | PASS |  | 8.1 / 8.7 |
| BRK_960_1080 | 0.5 | 1.5x | 9,028 | 9,939 | 0.000 | 0.994 | Y | Y | Y | PASS |  |  |
| BRK_960_1080 | 0.5 | 2.0x | 8,349 | 9,248 | 0.000 | 0.994 | Y | Y | Y | PASS |  |  |
| BRK_960_1080 | 1.0 | 1.0x | 19,413 | 21,259 | 0.000 | 0.994 | Y | Y | Y | PASS |  | 8.1 / 8.7 |
| BRK_960_1080 | 1.0 | 1.5x | 18,055 | 19,878 | 0.000 | 0.994 | Y | Y | Y | PASS |  |  |
| BRK_960_1080 | 1.0 | 2.0x | 16,697 | 18,497 | 0.000 | 0.994 | Y | Y | Y | PASS |  |  |
| GSHORT_t90 | 0.25 | 1.0x | 2,970 | 3,931 | 0.017 | 0.962 | Y | Y | Y | PASS |  | 30.0 / 30.0 |
| GSHORT_t90 | 0.25 | 1.5x | 2,941 | 3,913 | 0.017 | 0.962 | Y | Y | Y | PASS |  |  |
| GSHORT_t90 | 0.25 | 2.0x | 2,911 | 3,895 | 0.017 | 0.960 | Y | Y | Y | PASS |  |  |
| GSHORT_t90 | 0.5 | 1.0x | 5,941 | 7,862 | 0.017 | 0.962 | Y | Y | Y | PASS |  | 30.0 / 30.0 |
| GSHORT_t90 | 0.5 | 1.5x | 5,882 | 7,826 | 0.017 | 0.962 | Y | Y | Y | PASS |  |  |
| GSHORT_t90 | 0.5 | 2.0x | 5,822 | 7,790 | 0.017 | 0.960 | Y | Y | Y | PASS |  |  |
| GSHORT_t90 | 1.0 | 1.0x | 11,882 | 15,724 | 0.017 | 0.962 | Y | Y | Y | PASS |  | 30.0 / 30.0 |
| GSHORT_t90 | 1.0 | 1.5x | 11,763 | 15,652 | 0.017 | 0.962 | Y | Y | Y | PASS |  |  |
| GSHORT_t90 | 1.0 | 2.0x | 11,644 | 15,580 | 0.017 | 0.960 | Y | Y | Y | PASS |  |  |
| ON_none | 0.25 | 1.0x | 3,738 | 4,965 | -0.000 | 0.966 | Y | Y | Y | PASS |  | 18.0 / 23.5 |
| ON_none | 0.25 | 1.5x | 3,628 | 4,854 | -0.000 | 0.966 | Y | Y | Y | PASS |  |  |
| ON_none | 0.25 | 2.0x | 3,518 | 4,744 | -0.000 | 0.966 | Y | Y | Y | PASS |  |  |
| ON_none | 0.5 | 1.0x | 7,476 | 9,929 | -0.000 | 0.966 | Y | Y | Y | PASS |  | 18.0 / 23.5 |
| ON_none | 0.5 | 1.5x | 7,256 | 9,709 | -0.000 | 0.966 | Y | Y | Y | PASS |  |  |
| ON_none | 0.5 | 2.0x | 7,036 | 9,488 | -0.000 | 0.966 | Y | Y | Y | PASS |  |  |
| ON_none | 1.0 | 1.0x | 14,951 | 19,859 | -0.000 | 0.966 | Y | Y | Y | PASS |  | 18.0 / 23.5 |
| ON_none | 1.0 | 1.5x | 14,512 | 19,417 | -0.000 | 0.966 | Y | Y | Y | PASS |  |  |
| ON_none | 1.0 | 2.0x | 14,073 | 18,976 | -0.000 | 0.966 | Y | Y | Y | PASS |  |  |
| ES_RSI2_t10 | 0.25 | 1.0x | 6,279 | 7,257 | 0.094 | 0.990 | Y | Y | Y | PASS |  | 30.0 / 30.0 |
| ES_RSI2_t10 | 0.25 | 1.5x | 6,219 | 7,195 | 0.094 | 0.990 | Y | Y | Y | PASS |  |  |
| ES_RSI2_t10 | 0.25 | 2.0x | 6,158 | 7,134 | 0.093 | 0.990 | Y | Y | Y | PASS |  |  |
| ES_RSI2_t10 | 0.5 | 1.0x | 12,559 | 14,513 | 0.094 | 0.990 | Y | Y | Y | PASS |  | 30.0 / 30.0 |
| ES_RSI2_t10 | 0.5 | 1.5x | 12,437 | 14,391 | 0.094 | 0.990 | Y | Y | Y | PASS |  |  |
| ES_RSI2_t10 | 0.5 | 2.0x | 12,316 | 14,268 | 0.093 | 0.990 | Y | Y | Y | PASS |  |  |
| ES_RSI2_t10 | 1.0 | 1.0x | 25,117 | 29,026 | 0.094 | 0.990 | Y | Y | Y | PASS |  | 30.0 / 30.0 |
| ES_RSI2_t10 | 1.0 | 1.5x | 24,875 | 28,781 | 0.094 | 0.990 | Y | Y | Y | PASS |  |  |
| ES_RSI2_t10 | 1.0 | 2.0x | 24,632 | 28,536 | 0.093 | 0.990 | Y | Y | Y | PASS |  |  |
| RTY_RSI2_t10 | 0.25 | 1.0x | 8,005 | 12,210 | 0.070 | 1.000 | Y | Y | Y | PASS |  | 30.0 / 30.0 |
| RTY_RSI2_t10 | 0.25 | 1.5x | 7,921 | 12,131 | 0.069 | 1.000 | Y | Y | Y | PASS |  |  |
| RTY_RSI2_t10 | 0.25 | 2.0x | 7,838 | 12,052 | 0.069 | 1.000 | Y | Y | Y | PASS |  |  |
| RTY_RSI2_t10 | 0.5 | 1.0x | 16,009 | 24,421 | 0.070 | 1.000 | Y | Y | Y | PASS |  | 30.0 / 30.0 |
| RTY_RSI2_t10 | 0.5 | 1.5x | 15,842 | 24,263 | 0.069 | 1.000 | Y | Y | Y | PASS |  |  |
| RTY_RSI2_t10 | 0.5 | 2.0x | 15,676 | 24,104 | 0.069 | 1.000 | Y | Y | Y | PASS |  |  |
| RTY_RSI2_t10 | 1.0 | 1.0x | 32,018 | 48,842 | 0.070 | 1.000 | Y | Y | Y | PASS |  | 30.0 / 30.0 |
| RTY_RSI2_t10 | 1.0 | 1.5x | 31,685 | 48,525 | 0.069 | 1.000 | Y | Y | Y | PASS |  |  |
| RTY_RSI2_t10 | 1.0 | 2.0x | 31,352 | 48,209 | 0.069 | 1.000 | Y | Y | Y | PASS |  |  |
| IBS_t20_n1 | 0.25 | 1.0x | 4,232 | 5,486 | -0.068 | 0.940 | Y | Y | Y | CANDIDATE | placebo<0.95 | 30.0 / 30.0 |
| IBS_t20_n1 | 0.25 | 1.5x | 4,209 | 5,465 | -0.069 | 0.940 | Y | Y | Y | CANDIDATE | placebo<0.95 |  |
| IBS_t20_n1 | 0.25 | 2.0x | 4,186 | 5,444 | -0.069 | 0.940 | Y | Y | Y | CANDIDATE | placebo<0.95 |  |
| IBS_t20_n1 | 0.5 | 1.0x | 8,465 | 10,973 | -0.068 | 0.940 | Y | Y | Y | CANDIDATE | placebo<0.95 | 30.0 / 30.0 |
| IBS_t20_n1 | 0.5 | 1.5x | 8,419 | 10,931 | -0.069 | 0.940 | Y | Y | Y | CANDIDATE | placebo<0.95 |  |
| IBS_t20_n1 | 0.5 | 2.0x | 8,372 | 10,889 | -0.069 | 0.940 | Y | Y | Y | CANDIDATE | placebo<0.95 |  |
| IBS_t20_n1 | 1.0 | 1.0x | 16,930 | 21,945 | -0.068 | 0.940 | Y | Y | Y | CANDIDATE | placebo<0.95 | 30.0 / 30.0 |
| IBS_t20_n1 | 1.0 | 1.5x | 16,837 | 21,862 | -0.069 | 0.940 | Y | Y | Y | CANDIDATE | placebo<0.95 |  |
| IBS_t20_n1 | 1.0 | 2.0x | 16,745 | 21,778 | -0.069 | 0.940 | Y | Y | Y | CANDIDATE | placebo<0.95 |  |
| YM_RSI2_t10 | 0.25 | 1.0x | 4,137 | 5,651 | 0.099 | 0.938 | Y | Y | N | DEAD | year_share>60%; placebo<0.95 | 30.0 / 30.0 |
| YM_RSI2_t10 | 0.25 | 1.5x | 4,078 | 5,602 | 0.098 | 0.940 | Y | Y | N | DEAD | year_share>60%; placebo<0.95 |  |
| YM_RSI2_t10 | 0.25 | 2.0x | 4,019 | 5,554 | 0.098 | 0.940 | Y | Y | N | DEAD | year_share>60%; placebo<0.95 |  |
| YM_RSI2_t10 | 0.5 | 1.0x | 8,274 | 11,303 | 0.099 | 0.938 | Y | Y | N | DEAD | year_share>60%; placebo<0.95 | 30.0 / 30.0 |
| YM_RSI2_t10 | 0.5 | 1.5x | 8,156 | 11,205 | 0.098 | 0.940 | Y | Y | N | DEAD | year_share>60%; placebo<0.95 |  |
| YM_RSI2_t10 | 0.5 | 2.0x | 8,038 | 11,107 | 0.098 | 0.940 | Y | Y | N | DEAD | year_share>60%; placebo<0.95 |  |
| YM_RSI2_t10 | 1.0 | 1.0x | 16,548 | 22,605 | 0.099 | 0.938 | Y | Y | N | DEAD | year_share>60%; placebo<0.95 | 30.0 / 30.0 |
| YM_RSI2_t10 | 1.0 | 1.5x | 16,312 | 22,410 | 0.098 | 0.940 | Y | Y | N | DEAD | year_share>60%; placebo<0.95 |  |
| YM_RSI2_t10 | 1.0 | 2.0x | 16,077 | 22,215 | 0.098 | 0.940 | Y | Y | N | DEAD | year_share>60%; placebo<0.95 |  |
| RTY_IBS_t20_n1 | 0.25 | 1.0x | 3,618 | 5,002 | -0.012 | 0.922 | Y | Y | Y | CANDIDATE | placebo<0.95 | 17.3 / 20.7 |
| RTY_IBS_t20_n1 | 0.25 | 1.5x | 3,508 | 4,874 | -0.013 | 0.922 | Y | Y | Y | CANDIDATE | placebo<0.95 |  |
| RTY_IBS_t20_n1 | 0.25 | 2.0x | 3,397 | 4,747 | -0.013 | 0.922 | Y | Y | Y | CANDIDATE | placebo<0.95 |  |
| RTY_IBS_t20_n1 | 0.5 | 1.0x | 7,236 | 10,003 | -0.012 | 0.922 | Y | Y | Y | CANDIDATE | placebo<0.95 | 17.3 / 20.7 |
| RTY_IBS_t20_n1 | 0.5 | 1.5x | 7,015 | 9,749 | -0.013 | 0.922 | Y | Y | Y | CANDIDATE | placebo<0.95 |  |
| RTY_IBS_t20_n1 | 0.5 | 2.0x | 6,794 | 9,494 | -0.013 | 0.922 | Y | Y | Y | CANDIDATE | placebo<0.95 |  |
| RTY_IBS_t20_n1 | 1.0 | 1.0x | 14,473 | 20,006 | -0.012 | 0.922 | Y | Y | Y | CANDIDATE | placebo<0.95 | 17.3 / 20.7 |
| RTY_IBS_t20_n1 | 1.0 | 1.5x | 14,030 | 19,497 | -0.013 | 0.922 | Y | Y | Y | CANDIDATE | placebo<0.95 |  |
| RTY_IBS_t20_n1 | 1.0 | 2.0x | 13,588 | 18,989 | -0.013 | 0.922 | Y | Y | Y | CANDIDATE | placebo<0.95 |  |
| ORB_ASIA_15_v1__s60 | 0.25 | 1.0x | 4,069 | 6,123 | 0.081 | 0.958 | Y | Y | Y | PASS |  | 7.4 / >8 |
| ORB_ASIA_15_v1__s60 | 0.25 | 1.5x | 3,752 | 5,836 | 0.081 | 0.960 | Y | Y | Y | PASS |  |  |
| ORB_ASIA_15_v1__s60 | 0.25 | 2.0x | 3,435 | 5,549 | 0.080 | 0.960 | Y | Y | Y | PASS |  |  |
| ORB_ASIA_15_v1__s60 | 0.5 | 1.0x | 8,138 | 12,245 | 0.081 | 0.958 | Y | Y | Y | PASS |  | 7.4 / >8 |
| ORB_ASIA_15_v1__s60 | 0.5 | 1.5x | 7,504 | 11,672 | 0.081 | 0.960 | Y | Y | Y | PASS |  |  |
| ORB_ASIA_15_v1__s60 | 0.5 | 2.0x | 6,869 | 11,098 | 0.080 | 0.960 | Y | Y | Y | PASS |  |  |
| ORB_ASIA_15_v1__s60 | 1.0 | 1.0x | 16,276 | 24,491 | 0.081 | 0.958 | Y | Y | Y | PASS |  | 7.4 / >8 |
| ORB_ASIA_15_v1__s60 | 1.0 | 1.5x | 15,007 | 23,344 | 0.081 | 0.960 | Y | Y | Y | PASS |  |  |
| ORB_ASIA_15_v1__s60 | 1.0 | 2.0x | 13,739 | 22,197 | 0.080 | 0.960 | Y | Y | Y | PASS |  |  |
| ORB_ASIA_30_v1__s60 | 0.25 | 1.0x | 4,001 | 6,655 | 0.079 | 0.976 | Y | Y | Y | PASS |  | 7.6 / >8 |
| ORB_ASIA_30_v1__s60 | 0.25 | 1.5x | 3,698 | 6,385 | 0.078 | 0.980 | Y | Y | Y | PASS |  |  |
| ORB_ASIA_30_v1__s60 | 0.25 | 2.0x | 3,395 | 6,116 | 0.077 | 0.980 | Y | Y | N | CANDIDATE | year_share>60% |  |
| ORB_ASIA_30_v1__s60 | 0.5 | 1.0x | 8,001 | 13,310 | 0.079 | 0.976 | Y | Y | Y | PASS |  | 7.6 / >8 |
| ORB_ASIA_30_v1__s60 | 0.5 | 1.5x | 7,396 | 12,771 | 0.078 | 0.980 | Y | Y | Y | PASS |  |  |
| ORB_ASIA_30_v1__s60 | 0.5 | 2.0x | 6,791 | 12,231 | 0.077 | 0.980 | Y | Y | N | CANDIDATE | year_share>60% |  |
| ORB_ASIA_30_v1__s60 | 1.0 | 1.0x | 16,003 | 26,620 | 0.079 | 0.976 | Y | Y | Y | PASS |  | 7.6 / >8 |
| ORB_ASIA_30_v1__s60 | 1.0 | 1.5x | 14,792 | 25,541 | 0.078 | 0.980 | Y | Y | Y | PASS |  |  |
| ORB_ASIA_30_v1__s60 | 1.0 | 2.0x | 13,582 | 24,463 | 0.077 | 0.980 | Y | Y | N | CANDIDATE | year_share>60% |  |
| ORB_ASIA_15_v1__s75 | 0.25 | 1.0x | 3,864 | 7,340 | 0.064 | 0.962 | Y | Y | Y | PASS |  | >8 / >8 |
| ORB_ASIA_15_v1__s75 | 0.25 | 1.5x | 3,605 | 7,110 | 0.063 | 0.964 | Y | Y | Y | PASS |  |  |
| ORB_ASIA_15_v1__s75 | 0.25 | 2.0x | 3,346 | 6,881 | 0.063 | 0.964 | Y | Y | Y | PASS |  |  |
| ORB_ASIA_15_v1__s75 | 0.5 | 1.0x | 7,727 | 14,680 | 0.064 | 0.962 | Y | Y | Y | PASS |  | >8 / >8 |
| ORB_ASIA_15_v1__s75 | 0.5 | 1.5x | 7,209 | 14,220 | 0.063 | 0.964 | Y | Y | Y | PASS |  |  |
| ORB_ASIA_15_v1__s75 | 0.5 | 2.0x | 6,691 | 13,761 | 0.063 | 0.964 | Y | Y | Y | PASS |  |  |
| ORB_ASIA_15_v1__s75 | 1.0 | 1.0x | 15,455 | 29,359 | 0.064 | 0.962 | Y | Y | Y | PASS |  | >8 / >8 |
| ORB_ASIA_15_v1__s75 | 1.0 | 1.5x | 14,418 | 28,441 | 0.063 | 0.964 | Y | Y | Y | PASS |  |  |
| ORB_ASIA_15_v1__s75 | 1.0 | 2.0x | 13,382 | 27,522 | 0.063 | 0.964 | Y | Y | Y | PASS |  |  |

### Table 4 - item 3: NQ 1-s tape re-fill (fills: market = 1-min open of the order minute +/- 0.995*m pt, stop join 1.01*m pt, $4.84*m RT) and conservative 1-min model for ES/RTY/YM (4 ticks/side + $4.84 RT)

| series | model | trades in 1-s coverage / filled | stopped | gross-fallback | extra cost vs 1-min $/trade | net $/trade 1-s (1-min same trades) | hit 1-s (1-min) |
|---|---|---|---|---|---|---|---|
| RSI2_t10 | 1-s mult 1.0 | 93 / 93 | 0 | 0 | 29.3 | 1604 (1633) | 0.59 (0.59) |
| RSI2_t10 | 1-s mult 2.0 | 93 / 93 | 0 | 0 | 73.9 | 1559 (1633) | 0.59 (0.59) |
| RSI2T_t10 | 1-s mult 1.0 | 76 / 76 | 0 | 0 | 28.0 | 1172 (1200) | 0.58 (0.58) |
| RSI2T_t10 | 1-s mult 2.0 | 76 / 76 | 0 | 0 | 72.7 | 1127 (1200) | 0.58 (0.58) |
| RSI2C_s20 | 1-s mult 1.0 | 93 / 93 | 3 | 0 | 27.7 | 1417 (1445) | 0.59 (0.59) |
| RSI2C_s20 | 1-s mult 2.0 | 93 / 93 | 3 | 0 | 72.4 | 1373 (1445) | 0.59 (0.59) |
| RSI2CC_s20 | 1-s mult 1.0 | 93 / 93 | 3 | 0 | 27.7 | 1417 (1445) | 0.59 (0.59) |
| RSI2CC_s20 | 1-s mult 2.0 | 93 / 93 | 3 | 0 | 72.4 | 1373 (1445) | 0.59 (0.59) |
| COMB_c3_R | 1-s mult 1.0 | 198 / 198 | 0 | 0 | 29.6 | 1042 (1072) | 0.57 (0.57) |
| COMB_c3_R | 1-s mult 2.0 | 198 / 198 | 0 | 0 | 74.2 | 998 (1072) | 0.57 (0.57) |
| BRK_960_1080 | 1-s mult 1.0 | 729 / 729 | 0 | 10 | 30.2 | 52 (82) | 0.47 (0.50) |
| BRK_960_1080 | 1-s mult 2.0 | 729 / 729 | 0 | 10 | 74.9 | 7 (82) | 0.43 (0.50) |
| GSHORT_t90 | 1-s mult 1.0 | 44 / 44 | 0 | 0 | 29.5 | 457 (486) | 0.50 (0.50) |
| GSHORT_t90 | 1-s mult 2.0 | 44 / 44 | 0 | 0 | 74.1 | 412 (486) | 0.50 (0.50) |
| ON_none | 1-s mult 1.0 | 901 / 901 | 0 | 5 | 29.6 | 186 (216) | 0.54 (0.54) |
| ON_none | 1-s mult 2.0 | 901 / 901 | 0 | 5 | 74.2 | 142 (216) | 0.53 (0.54) |
| ES_RSI2_t10 | conservative (cu 104.84 vs 1-min 29.84) | - | - | - | 75.0 | - | - |
| RTY_RSI2_t10 | conservative (cu 44.84 vs 1-min 14.84) | - | - | - | 30.0 | - | - |
| IBS_t20_n1 | 1-s mult 1.0 | 158 / 158 | 0 | 0 | 30.3 | 1080 (1110) | 0.56 (0.57) |
| IBS_t20_n1 | 1-s mult 2.0 | 158 / 158 | 0 | 0 | 74.9 | 1035 (1110) | 0.56 (0.57) |
| YM_RSI2_t10 | conservative (cu 44.84 vs 1-min 14.84) | - | - | - | 30.0 | - | - |
| RTY_IBS_t20_n1 | conservative (cu 44.84 vs 1-min 14.84) | - | - | - | 30.0 | - | - |

| series | ratio | model | cost | stand WF | hold | plc | msh | nb | yr | verdict | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|
| RSI2_t10 | 0.25 | 1-s | 1.0x | 5,027 | 5,421 | 0.978 | Y | Y | Y | PASS |  |
| RSI2_t10 | 0.25 | 1-s | 1.5x | 4,971 | 5,363 | 0.978 | Y | Y | Y | PASS |  |
| RSI2_t10 | 0.25 | 1-s | 2.0x | 4,915 | 5,304 | 0.978 | Y | Y | Y | PASS |  |
| RSI2_t10 | 0.5 | 1-s | 1.0x | 10,054 | 10,842 | 0.978 | Y | Y | Y | PASS |  |
| RSI2_t10 | 0.5 | 1-s | 1.5x | 9,942 | 10,725 | 0.978 | Y | Y | Y | PASS |  |
| RSI2_t10 | 0.5 | 1-s | 2.0x | 9,831 | 10,609 | 0.978 | Y | Y | Y | PASS |  |
| RSI2_t10 | 1.0 | 1-s | 1.0x | 20,108 | 21,684 | 0.978 | Y | Y | Y | PASS |  |
| RSI2_t10 | 1.0 | 1-s | 1.5x | 19,884 | 21,451 | 0.978 | Y | Y | Y | PASS |  |
| RSI2_t10 | 1.0 | 1-s | 2.0x | 19,661 | 21,218 | 0.978 | Y | Y | Y | PASS |  |
| RSI2T_t10 | 0.25 | 1-s | 1.0x | 4,363 | 5,212 | 0.956 | Y | Y | Y | PASS |  |
| RSI2T_t10 | 0.25 | 1-s | 1.5x | 4,300 | 5,138 | 0.956 | Y | Y | Y | PASS |  |
| RSI2T_t10 | 0.25 | 1-s | 2.0x | 4,237 | 5,065 | 0.956 | Y | Y | Y | PASS |  |
| RSI2T_t10 | 0.5 | 1-s | 1.0x | 8,727 | 10,423 | 0.956 | Y | Y | Y | PASS |  |
| RSI2T_t10 | 0.5 | 1-s | 1.5x | 8,600 | 10,277 | 0.956 | Y | Y | Y | PASS |  |
| RSI2T_t10 | 0.5 | 1-s | 2.0x | 8,473 | 10,130 | 0.956 | Y | Y | Y | PASS |  |
| RSI2T_t10 | 1.0 | 1-s | 1.0x | 17,454 | 20,846 | 0.956 | Y | Y | Y | PASS |  |
| RSI2T_t10 | 1.0 | 1-s | 1.5x | 17,200 | 20,553 | 0.956 | Y | Y | Y | PASS |  |
| RSI2T_t10 | 1.0 | 1-s | 2.0x | 16,946 | 20,260 | 0.956 | Y | Y | Y | PASS |  |
| RSI2C_s20 | 0.25 | 1-s | 1.0x | 5,206 | 6,297 | 0.978 | Y | Y | Y | PASS |  |
| RSI2C_s20 | 0.25 | 1-s | 1.5x | 5,140 | 6,228 | 0.978 | Y | Y | Y | PASS |  |
| RSI2C_s20 | 0.25 | 1-s | 2.0x | 5,074 | 6,159 | 0.978 | Y | Y | Y | PASS |  |
| RSI2C_s20 | 0.5 | 1-s | 1.0x | 10,411 | 12,594 | 0.978 | Y | Y | Y | PASS |  |
| RSI2C_s20 | 0.5 | 1-s | 1.5x | 10,280 | 12,456 | 0.978 | Y | Y | Y | PASS |  |
| RSI2C_s20 | 0.5 | 1-s | 2.0x | 10,148 | 12,319 | 0.978 | Y | Y | Y | PASS |  |
| RSI2C_s20 | 1.0 | 1-s | 1.0x | 20,823 | 25,188 | 0.978 | Y | Y | Y | PASS |  |
| RSI2C_s20 | 1.0 | 1-s | 1.5x | 20,559 | 24,913 | 0.978 | Y | Y | Y | PASS |  |
| RSI2C_s20 | 1.0 | 1-s | 2.0x | 20,295 | 24,637 | 0.978 | Y | Y | Y | PASS |  |
| RSI2CC_s20 | 0.25 | 1-s | 1.0x | 2,607 | 3,153 | 0.984 | Y | Y | Y | PASS |  |
| RSI2CC_s20 | 0.25 | 1-s | 1.5x | 2,574 | 3,119 | 0.984 | Y | Y | Y | PASS |  |
| RSI2CC_s20 | 0.25 | 1-s | 2.0x | 2,541 | 3,084 | 0.984 | Y | Y | Y | PASS |  |
| RSI2CC_s20 | 0.5 | 1-s | 1.0x | 2,607 | 3,153 | 0.984 | Y | Y | Y | PASS |  |
| RSI2CC_s20 | 0.5 | 1-s | 1.5x | 2,574 | 3,119 | 0.984 | Y | Y | Y | PASS |  |
| RSI2CC_s20 | 0.5 | 1-s | 2.0x | 2,541 | 3,084 | 0.984 | Y | Y | Y | PASS |  |
| RSI2CC_s20 | 1.0 | 1-s | 1.0x | 2,607 | 3,153 | 0.984 | Y | Y | Y | PASS |  |
| RSI2CC_s20 | 1.0 | 1-s | 1.5x | 2,574 | 3,119 | 0.984 | Y | Y | Y | PASS |  |
| RSI2CC_s20 | 1.0 | 1-s | 2.0x | 2,541 | 3,084 | 0.984 | Y | Y | Y | PASS |  |
| COMB_c3_R | 0.25 | 1-s | 1.0x | 2,683 | 3,416 | 0.954 | Y | Y | N | CANDIDATE | year_share>60% |
| COMB_c3_R | 0.25 | 1-s | 1.5x | 2,627 | 3,359 | 0.958 | Y | Y | N | CANDIDATE | year_share>60% |
| COMB_c3_R | 0.25 | 1-s | 2.0x | 2,561 | 3,302 | 0.958 | Y | Y | N | CANDIDATE | year_share>60% |
| COMB_c3_R | 0.5 | 1-s | 1.0x | 2,683 | 3,416 | 0.954 | Y | Y | N | CANDIDATE | year_share>60% |
| COMB_c3_R | 0.5 | 1-s | 1.5x | 2,627 | 3,359 | 0.958 | Y | Y | N | CANDIDATE | year_share>60% |
| COMB_c3_R | 0.5 | 1-s | 2.0x | 2,561 | 3,302 | 0.958 | Y | Y | N | CANDIDATE | year_share>60% |
| BRK_960_1080 | 0.25 | 1-s | 1.0x | 3,480 | 3,940 | 0.994 | Y | Y | Y | PASS |  |
| BRK_960_1080 | 0.25 | 1-s | 1.5x | 2,459 | 2,901 | 0.994 | Y | N | Y | DEAD | neighbours_agree |
| BRK_960_1080 | 0.25 | 1-s | 2.0x | 1,437 | 1,863 | 0.992 | Y | N | N | DEAD | neighbours_agree; year_share>60% |
| BRK_960_1080 | 0.5 | 1-s | 1.0x | 6,960 | 7,879 | 0.994 | Y | Y | Y | PASS |  |
| BRK_960_1080 | 0.5 | 1-s | 1.5x | 4,917 | 5,802 | 0.994 | Y | N | Y | DEAD | neighbours_agree |
| BRK_960_1080 | 0.5 | 1-s | 2.0x | 2,875 | 3,725 | 0.992 | N | N | N | DEAD | neighbours_agree; sleeve_marginal_sharpe_up; standalone_hold>0&marginal_Sharpe_up&corr<=0.5; sleeve_secondary; year_share>60% |
| BRK_960_1080 | 1.0 | 1-s | 1.0x | 13,920 | 15,759 | 0.994 | Y | Y | Y | PASS |  |
| BRK_960_1080 | 1.0 | 1-s | 1.5x | 9,834 | 11,604 | 0.994 | N | N | Y | DEAD | neighbours_agree; sleeve_marginal_sharpe_up; standalone_hold>0&marginal_Sharpe_up&corr<=0.5; sleeve_secondary |
| BRK_960_1080 | 1.0 | 1-s | 2.0x | 5,749 | 7,450 | 0.992 | N | N | N | DEAD | neighbours_agree; sleeve_marginal_sharpe_up; standalone_hold>0&marginal_Sharpe_up&corr<=0.5; sleeve_secondary; year_share>60% |
| GSHORT_t90 | 0.25 | 1-s | 1.0x | 2,852 | 3,859 | 0.958 | Y | Y | Y | PASS |  |
| GSHORT_t90 | 0.25 | 1-s | 1.5x | 2,763 | 3,805 | 0.958 | Y | Y | Y | PASS |  |
| GSHORT_t90 | 0.25 | 1-s | 2.0x | 2,673 | 3,750 | 0.954 | Y | Y | Y | PASS |  |
| GSHORT_t90 | 0.5 | 1-s | 1.0x | 5,704 | 7,717 | 0.958 | Y | Y | Y | PASS |  |
| GSHORT_t90 | 0.5 | 1-s | 1.5x | 5,525 | 7,609 | 0.958 | Y | Y | Y | PASS |  |
| GSHORT_t90 | 0.5 | 1-s | 2.0x | 5,347 | 7,501 | 0.954 | Y | Y | Y | PASS |  |
| GSHORT_t90 | 1.0 | 1-s | 1.0x | 11,408 | 15,435 | 0.958 | Y | Y | Y | PASS |  |
| GSHORT_t90 | 1.0 | 1-s | 1.5x | 11,051 | 15,218 | 0.958 | Y | Y | Y | PASS |  |
| GSHORT_t90 | 1.0 | 1-s | 2.0x | 10,693 | 15,002 | 0.954 | Y | Y | Y | PASS |  |
| ON_none | 0.25 | 1-s | 1.0x | 3,301 | 4,534 | 0.968 | Y | Y | Y | PASS |  |
| ON_none | 0.25 | 1-s | 1.5x | 2,971 | 4,202 | 0.968 | Y | Y | Y | PASS |  |
| ON_none | 0.25 | 1-s | 2.0x | 2,640 | 3,870 | 0.968 | Y | Y | Y | PASS |  |
| ON_none | 0.5 | 1-s | 1.0x | 6,602 | 9,068 | 0.968 | Y | Y | Y | PASS |  |
| ON_none | 0.5 | 1-s | 1.5x | 5,942 | 8,405 | 0.968 | Y | Y | Y | PASS |  |
| ON_none | 0.5 | 1-s | 2.0x | 5,281 | 7,741 | 0.968 | Y | Y | Y | PASS |  |
| ON_none | 1.0 | 1-s | 1.0x | 13,205 | 18,137 | 0.968 | Y | Y | Y | PASS |  |
| ON_none | 1.0 | 1-s | 1.5x | 11,883 | 16,809 | 0.968 | Y | Y | Y | PASS |  |
| ON_none | 1.0 | 1-s | 2.0x | 10,561 | 15,481 | 0.968 | Y | Y | Y | PASS |  |
| ES_RSI2_t10 | 0.25 | cons | 1.0x | 5,974 | 6,949 | 0.990 | Y | Y | Y | PASS |  |
| ES_RSI2_t10 | 0.25 | cons | 1.5x | 5,761 | 6,734 | 0.994 | Y | Y | Y | PASS |  |
| ES_RSI2_t10 | 0.25 | cons | 2.0x | 5,548 | 6,519 | 0.996 | Y | Y | Y | PASS |  |
| ES_RSI2_t10 | 0.5 | cons | 1.0x | 11,949 | 13,898 | 0.990 | Y | Y | Y | PASS |  |
| ES_RSI2_t10 | 0.5 | cons | 1.5x | 11,523 | 13,467 | 0.994 | Y | Y | Y | PASS |  |
| ES_RSI2_t10 | 0.5 | cons | 2.0x | 11,096 | 13,037 | 0.996 | Y | Y | Y | PASS |  |
| ES_RSI2_t10 | 1.0 | cons | 1.0x | 23,898 | 27,795 | 0.990 | Y | Y | Y | PASS |  |
| ES_RSI2_t10 | 1.0 | cons | 1.5x | 23,045 | 26,935 | 0.994 | Y | Y | Y | PASS |  |
| ES_RSI2_t10 | 1.0 | cons | 2.0x | 22,193 | 26,074 | 0.996 | Y | Y | Y | PASS |  |
| RTY_RSI2_t10 | 0.25 | cons | 1.0x | 7,668 | 11,891 | 1.000 | Y | Y | Y | PASS |  |
| RTY_RSI2_t10 | 0.25 | cons | 1.5x | 7,416 | 11,652 | 1.000 | Y | Y | Y | PASS |  |
| RTY_RSI2_t10 | 0.25 | cons | 2.0x | 7,164 | 11,413 | 1.000 | Y | Y | Y | PASS |  |
| RTY_RSI2_t10 | 0.5 | cons | 1.0x | 15,335 | 23,781 | 1.000 | Y | Y | Y | PASS |  |
| RTY_RSI2_t10 | 0.5 | cons | 1.5x | 14,832 | 23,303 | 1.000 | Y | Y | Y | PASS |  |
| RTY_RSI2_t10 | 0.5 | cons | 2.0x | 14,328 | 22,825 | 1.000 | Y | Y | Y | PASS |  |
| RTY_RSI2_t10 | 1.0 | cons | 1.0x | 30,671 | 47,563 | 1.000 | Y | Y | Y | PASS |  |
| RTY_RSI2_t10 | 1.0 | cons | 1.5x | 29,664 | 46,607 | 1.000 | Y | Y | Y | PASS |  |
| RTY_RSI2_t10 | 1.0 | cons | 2.0x | 28,657 | 45,651 | 1.000 | Y | Y | Y | PASS |  |
| IBS_t20_n1 | 0.25 | 1-s | 1.0x | 4,138 | 5,404 | 0.940 | Y | Y | Y | CANDIDATE | placebo<0.95 |
| IBS_t20_n1 | 0.25 | 1-s | 1.5x | 4,069 | 5,341 | 0.940 | Y | Y | Y | CANDIDATE | placebo<0.95 |
| IBS_t20_n1 | 0.25 | 1-s | 2.0x | 3,999 | 5,278 | 0.940 | Y | Y | Y | CANDIDATE | placebo<0.95 |
| IBS_t20_n1 | 0.5 | 1-s | 1.0x | 8,276 | 10,807 | 0.940 | Y | Y | Y | CANDIDATE | placebo<0.95 |
| IBS_t20_n1 | 0.5 | 1-s | 1.5x | 8,137 | 10,681 | 0.940 | Y | Y | Y | CANDIDATE | placebo<0.95 |
| IBS_t20_n1 | 0.5 | 1-s | 2.0x | 7,998 | 10,555 | 0.940 | Y | Y | Y | CANDIDATE | placebo<0.95 |
| IBS_t20_n1 | 1.0 | 1-s | 1.0x | 16,552 | 21,615 | 0.940 | Y | Y | Y | CANDIDATE | placebo<0.95 |
| IBS_t20_n1 | 1.0 | 1-s | 1.5x | 16,274 | 21,363 | 0.940 | Y | Y | Y | CANDIDATE | placebo<0.95 |
| IBS_t20_n1 | 1.0 | 1-s | 2.0x | 15,996 | 21,110 | 0.940 | Y | Y | Y | CANDIDATE | placebo<0.95 |
| YM_RSI2_t10 | 0.25 | cons | 1.0x | 3,899 | 5,454 | 0.942 | Y | Y | N | DEAD | year_share>60%; placebo<0.95 |
| YM_RSI2_t10 | 0.25 | cons | 1.5x | 3,721 | 5,306 | 0.944 | Y | Y | N | DEAD | year_share>60%; placebo<0.95 |
| YM_RSI2_t10 | 0.25 | cons | 2.0x | 3,544 | 5,159 | 0.956 | Y | Y | N | CANDIDATE | year_share>60% |
| YM_RSI2_t10 | 0.5 | cons | 1.0x | 7,798 | 10,908 | 0.942 | Y | Y | N | DEAD | year_share>60%; placebo<0.95 |
| YM_RSI2_t10 | 0.5 | cons | 1.5x | 7,443 | 10,613 | 0.944 | Y | Y | N | DEAD | year_share>60%; placebo<0.95 |
| YM_RSI2_t10 | 0.5 | cons | 2.0x | 7,087 | 10,318 | 0.956 | Y | Y | N | CANDIDATE | year_share>60% |
| YM_RSI2_t10 | 1.0 | cons | 1.0x | 15,596 | 21,816 | 0.942 | Y | Y | N | DEAD | year_share>60%; placebo<0.95 |
| YM_RSI2_t10 | 1.0 | cons | 1.5x | 14,885 | 21,226 | 0.944 | Y | Y | N | DEAD | year_share>60%; placebo<0.95 |
| YM_RSI2_t10 | 1.0 | cons | 2.0x | 14,175 | 20,636 | 0.956 | Y | Y | N | CANDIDATE | year_share>60% |
| RTY_IBS_t20_n1 | 0.25 | cons | 1.0x | 3,171 | 4,487 | 0.922 | Y | Y | Y | CANDIDATE | placebo<0.95 |
| RTY_IBS_t20_n1 | 0.25 | cons | 1.5x | 2,836 | 4,103 | 0.922 | Y | Y | Y | CANDIDATE | placebo<0.95 |
| RTY_IBS_t20_n1 | 0.25 | cons | 2.0x | 2,502 | 3,719 | 0.922 | Y | Y | N | DEAD | year_share>60%; placebo<0.95 |
| RTY_IBS_t20_n1 | 0.5 | cons | 1.0x | 6,342 | 8,975 | 0.922 | Y | Y | Y | CANDIDATE | placebo<0.95 |
| RTY_IBS_t20_n1 | 0.5 | cons | 1.5x | 5,673 | 8,206 | 0.922 | Y | Y | Y | CANDIDATE | placebo<0.95 |
| RTY_IBS_t20_n1 | 0.5 | cons | 2.0x | 5,004 | 7,437 | 0.922 | Y | Y | N | DEAD | year_share>60%; placebo<0.95 |
| RTY_IBS_t20_n1 | 1.0 | cons | 1.0x | 12,683 | 17,949 | 0.922 | Y | Y | Y | CANDIDATE | placebo<0.95 |
| RTY_IBS_t20_n1 | 1.0 | cons | 1.5x | 11,346 | 16,412 | 0.922 | Y | Y | Y | CANDIDATE | placebo<0.95 |
| RTY_IBS_t20_n1 | 1.0 | cons | 2.0x | 10,008 | 14,875 | 0.922 | N | Y | N | DEAD | sleeve_marginal_sharpe_up; standalone_hold>0&marginal_Sharpe_up&corr<=0.5; sleeve_secondary; year_share>60%; placebo<0.95 |

### Table 5 - item 4: fresh-seed replication of the PASS series (500 draws, seeds 3104000+100*window+series index; ratio 0.5 shown for halves, rank is scale-free except COMB/RSI2CC caps). Halves: 71 WF weeks each, sleeve re-scaled to the ratio inside the half.

| series | WF full fresh rank (orig rank) | H1 mean / ms / corr / rank | H2 mean / ms / corr / rank | pre-2024 wk mean [CI] | 2x sign | +yrs | pre-2024 fresh rank | min(orig, fresh pre) | verdict if that min replaces the placebo (NM-E convention, info only) |
|---|---|---|---|---|---|---|---|---|---|
| RSI2_t10 | 0.974 (0.978) | 8,454 / Y / 0.03 / 0.872 | 12,416 / Y / -0.14 / 0.966 | 163 [36, 301] | Y | 8/11 | 0.988 | 0.978 | PASS [] |
| RSI2T_t10 | 0.964 (0.956) | 9,540 / Y / 0.03 / 0.942 | 8,937 / Y / -0.17 / 0.848 | 98 [6, 188] | Y | 8/11 | 0.926 | 0.926 | CANDIDATE ['placebo<0.95'] |
| RSI2C_s20 | 0.980 (0.978) | 9,008 / Y / 0.04 / 0.940 | 12,104 / Y / -0.14 / 0.954 | 119 [-21, 253] | Y | 8/11 | 0.932 | 0.932 | CANDIDATE ['placebo<0.95'] |
| RSI2CC_s20 | 0.986 (0.984) | 2,231 / Y / 0.04 / 0.940 | 3,061 / Y / -0.14 / 0.964 | 119 [-21, 253] | Y | 8/11 | 0.934 | 0.934 | CANDIDATE ['placebo<0.95'] |
| COMB_c3_R | 0.962 (0.964) | 1,852 / Y / 0.03 / 0.830 | 3,811 / Y / -0.17 / 0.952 | 695 [112, 1,235] | Y | 9/11 | 0.968 | 0.964 | PASS [] |
| BRK_960_1080 | 0.988 (0.994) | 10,889 / Y / 0.07 / 0.982 | 8,987 / Y / -0.04 / 0.930 | 41 [-34, 120] | N | 5/11 | 0.988 | 0.988 | PASS [] |
| GSHORT_t90 | 0.956 (0.962) | 7,593 / Y / 0.12 / 0.938 | 3,174 / Y / -0.11 / 0.774 | n/a (needs Set A trailing gate: no pre-2023 history) | - | - | - | - | - |
| ON_none | 0.966 (0.966) | 4,892 / Y / 0.19 / 0.846 | 10,110 / Y / -0.16 / 0.924 | 210 [-20, 446] | Y | 9/11 | 0.986 | 0.966 | PASS [] |
| ES_RSI2_t10 | 0.986 (0.990) | 8,539 / Y / 0.08 / 0.900 | 21,178 / Y / 0.13 / 1.000 | 88 [-33, 204] | Y | 9/11 | 0.944 | 0.944 | CANDIDATE ['placebo<0.95'] |
| RTY_RSI2_t10 | 1.000 (1.000) | 9,092 / Y / 0.03 / 0.948 | 22,394 / Y / 0.08 / 0.998 | 60 [-46, 157] | Y | 5/7 | 0.904 | 0.904 | CANDIDATE ['placebo<0.95'] |

### Table 6 - diagnostic (not part of any verdict): drift-matched placebo for the always-long clock sleeves (500 draws, same duration, random start, long only)

| sleeve | window | sleeve wk mean (1 lot) | placebo median | placebo p95 | rank |
|---|---|---|---|---|---|
| BRK_960_1080 | WF | 400 | 26 | 468 | 0.922 |
| BRK_960_1080 | PRE | 41 | -28 | 74 | 0.896 |
| ON_none | WF | 1,179 | 1,626 | 2,675 | 0.220 |
| ON_none | PRE | 210 | 370 | 597 | 0.098 |

### Table 7 - diagnostic (not part of any verdict): placebo rank noise. 5,000 fresh draws (seed 3106000+100*window+idx) vs the 500-draw ranks (orig = leaderboard seeds, fresh = Table 5 seeds). SE of a rank near 0.95: 500 draws 0.010, 5,000 draws 0.003.

| series | status | WF rank orig 500 (r=0.5) | WF rank fresh 500 | WF rank 5,000 | pre-2024 rank fresh 500 | pre-2024 rank 5,000 |
|---|---|---|---|---|---|---|
| RSI2_t10 | PASS | 0.978 | 0.974 | 0.978 | 0.988 | 0.976 |
| RSI2T_t10 | PASS | 0.956 | 0.964 | 0.953 | 0.926 | 0.911 |
| RSI2C_s20 | PASS | 0.978 | 0.980 | 0.980 | 0.932 | 0.917 |
| RSI2CC_s20 | PASS | 0.984 | 0.986 | 0.987 | 0.934 | 0.920 |
| COMB_c3_R | PASS | 0.964 | 0.962 | 0.966 | 0.968 | 0.981 |
| BRK_960_1080 | PASS | 0.994 | 0.988 | 0.994 | 0.988 | 0.988 |
| GSHORT_t90 | PASS | 0.962 | 0.956 | 0.957 | - | - |
| ON_none | PASS | 0.966 | 0.966 | 0.962 | 0.986 | 0.984 |
| ES_RSI2_t10 | PASS | 0.990 | 0.986 | 0.994 | 0.944 | 0.962 |
| RTY_RSI2_t10 | PASS | 1.000 | 1.000 | 1.000 | 0.904 | 0.870 |
| IBS_t20_n1 | CANDIDATE | 0.940 | - | 0.932 | - | - |
| YM_RSI2_t10 | CANDIDATE | 0.938 | - | 0.951 | - | - |
| RTY_IBS_t20_n1 | CANDIDATE | 0.922 | - | 0.931 | - | - |
