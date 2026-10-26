# NEARMISS_RESCORE (RESEARCH V2 section 6)

Produced 2026-10-24 by the NM agent with four forks (groups A-D) plus group E (own). Verdict function: lead s48score.verdict (READY_V2) for group E (checked identical at test ratios 0.25 and 0.5); groups A-D used the interim nm_lib.verdict which implements the same section-1 logic; the lead function should be re-run on rows/NM_*.json when convenient (differences expected only in the treatment of secondary conditions). All holdout looks here are RE-READS: every cell had its holdout seen in the original track (disclosed per group). Each group has its own prereg with sha256 in autopilot/DECISIONS.md written before scoring: NM_A, NM_B, NM_C, NM_D1/D2, NM_E1 (l2vast/struct48/prereg/).

## Headline
- PASS (12): the dip-buy sleeve family (NQ RSI2_t10, RSI2T, RSI2C_s20, RSI2CC_s20, ES RSI2, RTY RSI2, COMB_c3_R: ONE correlated exposure, WF weekly corr NQ-ES 0.73), BRK_960_1080, GSHORT_t90, ORB_ASIA_15_v1 s60/s75 (one system), and execution cell T4.2_Y4 (touch-join limit entries, +0.093 pt/trade). Independent PASS families: dip-buy, BRK, ORB Asia, GSHORT, T4.2_Y4.
- CANDIDATE (12): NQ_IBS_t20_n1, RTY_IBS_t20_n1 (placebo 0.94 / 0.92) and 10 Set B cells (B01 Set B = cap off, floor 12R, lots 14/10/10, and 9 PBDAY day-loss/profit-lock variants of it: ONE edge). Set B is CANDIDATE not PASS because the mean CI includes 0 on the block bootstrap and the test could not see less than 11.5k/wk (predicted +8.1k).
- DEAD: everything else, listed once below. Notable DEADs: overnight drift ON_none and ON_VT (2013-2023 placebo rank 0.32 / 0.29: the overnight edge is no better than a random clock), soft half-size switch STACK-FB (neighbours disagree: theta 0.4 and horizon +10 negative; isolated spike at +5 min), C5_m10 (net -0.40 pt/trade after commission, MDE 4.9 pt), all T4 skip-join and wait variants (T4.1a/b significantly negative; T4.4_W5 +0.049 pt only under the optimistic queue fill and neighbours disagree), all T1 cells, TH cooldown cells.
- Borderline DEADs that the lead may want to rule on (single failed condition): STACK-FB soft (neighbours only), T12_N1100_only (neighbour only; WF +4.2k/wk, maxDD -42k, placebo 0.98, holdout +), E5S (placebo 0.894 vs 0.90 floor), B03 Remove cap+week floor (placebo 0.73 only), T14_L_s50_t2.0_n10 and T14_C (no stored placebo; counted as failed).
- Registration records written to l2vast/struct48/paper_all/: NM_E_*.json (13), B01/B05/B06/B07 *.json (10, unprefixed), T4.2_Y4.json (1). TEST_dryrun.json in that directory is a stray dry-run file from a fork, not a registration (not deleted per rules; ignore it). The FWD agent should treat the 13 NM_E and 10 B records as 5 + 1 independent edges (dip-buy, IBS, BRK, ORB, GSHORT, Set B), not 24.
- Honest power note: weekly tests at a 0.25 sleeve ratio cannot see less than ~6.1k/wk; sizing/lock tests ~8-15k/wk; T1 modifiers ~$450-700/trade; T4 paired cells 0.03-0.05 pt/trade (waits/skips) to 0.18-0.5 (slicing). Every null below should be read as "could not have seen less than that".
- Caveats on PASSes: BRK earned only +30/wk with 4/11 positive years in 2013-2023 and halt slippage is 1 tick/side; GSHORT has ~31 trades and portfolio maxDD +28.9% (the sleeve rule does not look at either); ORB Asia was negative in IS and +12-15% worse portfolio maxDD; COMB L8W -5.1k/wk; dip-buy L8W positive for ES/RTY; T4.2_Y4 replay lacks 2024-02..2025-06 and its holdout is the same data as WF, depends on the trade-through fill model, ~0 in the last 8 weeks.

## PASS (12)

| group | cell | note |
|---|---|---|
| E sleeve | NQ_RSI2_t10 |  |
| E sleeve | NQ_RSI2T_t10 |  |
| E sleeve | NQ_RSI2C_s20 |  |
| E sleeve | NQ_RSI2CC_s20 |  |
| E sleeve | ES_RSI2_t10 |  |
| E sleeve | RTY_RSI2_t10 |  |
| E sleeve | COMB_c3_R |  |
| E sleeve | BRK_960_1080 |  |
| E sleeve | GSHORT_t90 |  |
| E sleeve | ORB_ASIA_15_v1_s60 |  |
| E sleeve | ORB_ASIA_15_v1_s75 |  |
| C execution | T4.2_Y4 |  |

## CANDIDATE (12)

| group | cell | note |
|---|---|---|
| E sleeve | NQ_IBS_t20_n1 |  |
| E sleeve | RTY_IBS_t20_n1 |  |
| B sizing/lock | B01_SetB |  |
| B sizing/lock | B05_SetB_pb3R_vsA |  |
| B sizing/lock | B05_SetB_pb4R_vsA |  |
| B sizing/lock | B05_SetB_pboff_vsA |  |
| B sizing/lock | B06_SetB_pb2R_noprofit_vsA |  |
| B sizing/lock | B06_SetB_pb3R_noprofit_vsA |  |
| B sizing/lock | B06_SetB_pb4R_noprofit_vsA |  |
| B sizing/lock | B06_SetB_pboff_noprofit_vsA |  |
| B sizing/lock | B07_SetB_Rscaled_pb2R_vsA |  |
| B sizing/lock | B07_SetB_Rscaled_pb4R_vsA |  |

## DEAD (77)

| group | cell | note |
|---|---|---|
| E sleeve | ES_IBS_t20_n1 | placebo>=0.90; placebo>=0.95; CI excludes 0 |
| E sleeve | ON_none | placebo>=0.90; placebo>=0.95; CI excludes 0 |
| E sleeve | ON_VT | placebo>=0.90; placebo>=0.95; year share<=60% |
| C execution | T4.1a |  |
| C execution | T4.1b |  |
| C execution | T4.2_L0 |  |
| C execution | T4.2_Lm2 |  |
| C execution | T4.2_LB0 |  |
| C execution | T4.3_G1 |  |
| C execution | T4.3_G4 |  |
| C execution | T4.3_S2x7 |  |
| C execution | T4.4_W2 |  |
| C execution | T4.4_W5 |  |
| C execution | T4.4_W2t |  |
| C execution | T4.4_W3t |  |
| C execution | T4.4_W5t |  |
| C signal | E5S |  |
| C trade-modifier | SO_f33_tr20 |  |
| B sizing/lock | B02_BEST5 |  |
| B sizing/lock | B03_RemCapWk |  |
| B sizing/lock | B04_CapOff_Wk12 |  |
| B sizing/lock | B07_SetB_Rscaled_pb3R_vsA |  |
| B sizing/lock | B08_Live_pb3R_vsA |  |
| B sizing/lock | B08_Live_pb4R_vsA |  |
| B sizing/lock | B08_Live_pboff_vsA |  |
| B sizing/lock | B09_Live_noprofit_vsA |  |
| B sizing/lock | B10_SetB_pb3R_vsSetB |  |
| B sizing/lock | B10_SetB_pb4R_vsSetB |  |
| B sizing/lock | B10_SetB_pboff_vsSetB |  |
| D trade-modifier / session rule | T12_A0000_L0730_N1100 |  |
| D trade-modifier / session rule | T12_A0000_L0800_N1100 |  |
| D trade-modifier / session rule | T12_A0130_L0730_N1100 |  |
| D trade-modifier / session rule | T12_A0130_L0800_N1030 |  |
| D trade-modifier / session rule | T12_A0130_L0800_N1100 |  |
| D trade-modifier / session rule | T12_A0130_L0830_N1100 |  |
| D trade-modifier / session rule | T12_A0130_L0900_N1100 |  |
| D trade-modifier / session rule | T12_N1100_only |  |
| D trade-modifier / session rule | T14_L_s50_t1.5_n10 |  |
| D trade-modifier / session rule | T14_L_s50_t2.0_n10 |  |
| D trade-modifier / session rule | T14_L_s60_t2.0_n10 |  |
| D trade-modifier / session rule | T14_L_s60_t2.0_n14 |  |
| D trade-modifier / session rule | T14_S_s50_t1.0_n14 |  |
| D trade-modifier / session rule | T14_S_s50_t1.5_n10 |  |
| D trade-modifier / session rule | T14_S_s50_t1.5_n14 |  |
| D trade-modifier / session rule | T14_S_s50_t2.0_n10 |  |
| D trade-modifier / session rule | T14_S_s50_t2.0_n14 |  |
| D trade-modifier / session rule | T14_C |  |
| D trade-modifier / session rule | T11_N2_book_lockon |  |
| D trade-modifier / session rule | T13_M2_R0 |  |
| D trade-modifier / session rule | T15_COMBO |  |
| D lock / session rule (weekly) | RL|PORT|off|3 |  |
| D lock / session rule (weekly) | RL|PORT|off|4 |  |
| D lock / session rule (weekly) | RL|B3tick|off|3 |  |
| D lock / session rule (weekly) | RL|B3tick|off|4 |  |
| D lock / session rule (weekly) | RL|B3sec|off|3 |  |
| D lock / session rule (weekly) | RL|B3sec|off|4 |  |
| D lock / session rule (weekly) | CV|PORT|loss |  |
| D lock / session rule (weekly) | CV|PORT|profit |  |
| D lock / session rule (weekly) | CV|PORT|both |  |
| D lock / session rule (weekly) | CV|B3tick|loss |  |
| D lock / session rule (weekly) | CV|B3tick|profit |  |
| D lock / session rule (weekly) | CV|B3tick|both |  |
| D lock / session rule (weekly) | CV|B3sec|loss |  |
| A | SOFT_FB_h5_t0.3 |  |
| A | SOFT_FB_h5_t0.4 |  |
| A | SOFT_FB_h10_t0.3 |  |
| A | SOFT_FB_h0_t0.3 |  |
| A | SOFT_FB_h15_t0.3 |  |
| A | SOFT_FB_h20_t0.3 |  |
| A | SOFT_FB_h30_t0.3 |  |
| A | SOFT_FB_h45_t0.3 |  |
| A | SOFT_FB_h60_t0.3 |  |
| A | SOFT_FB_h90_t0.3 |  |
| A | SOFT_FB_h120_t0.3 |  |
| A | C5_m5 |  |
| A | C5_m10 |  |
| A | C5_m15 |  |

Also DEAD from stored rows (not individually re-scored): 130 further T1 cells (87 with WF-PRE mean down, 43 with holdout down); 37 T2 cells (<=3/5 old conditions, T2 agent continues under V2).

## Cells NOT re-scored and why
- T3.1 (90 cells, best 4/10), T3.2 ORB other than ASIA_15_v1 s60/s75 (<=4/6 = 67% <70%), T3.3 ON_PD5/ST/BO/WK (<=4/6), T3.6/T3.7 other ideas (<=6/9), T3.8 YM RSI2/IBS and ES/YM IBS (5-6/9), XDIP/VTB/AFR: below the 70% bar; stored placebos/holdouts also below the CANDIDATE floor.
- T3.9 batch (running now), T4 months 2023-05 and 2024-02..2025-06 (replay in progress; rerun code/nm_c_score.py final), T2 cells beyond the two near-misses: pending.
- BEST5-exact on the 1-s engine with full R11 sequence test; trade-level pairing of sizing/lock cells (not defined); per-trade logs for T1 streams (day-paired used instead).
- Wall-clock: whole job ~1.5 h.

---
# Detail by group (full tables, conditions met/failed, MDE statements)

# NM-E re-score (RESEARCH V2): stored-series sleeves (RSI2 family, IBS, COMB, BRK, GSHORT, overnight drift, ORB Asia)

Prereg l2vast/struct48/prereg/NM_E1.md sha256 a52624a0f6ae5397111566cbd72f46ba505711fbcdc3ba8cba33d64465c74610 (in DECISIONS.md before scoring); pre-holdout text prereg/NM_E_PREHOLD.md; holdout look logged as track NM-E. Code code/nm_e.py, nm_e_lead.py, nm_e_register.py; rows rows/NM_E.json. No new engine run: the stored unit series of the original tracks were re-scored (sleeve rule at risk ratio 0.25, also 0.5/1.0 in the rows). Verdicts below agree with the lead s48score.verdict at test ratios 0.25 and 0.5 (out/NM_E_leadverdict.json).
Holdout disclosure: every holdout here was already looked at (T3.2, T3.3, T3.5, T3.6b1, T3.7b4/b4r, T3.8A, T3.8B); this is a re-read, not a blind look.

Sleeve criterion (section 3): standalone holdout mean > 0, marginal portfolio Sharpe up at the tested ratio (WF 142 wks, Set A Sharpe 0.239/wk), weekly corr <= 0.5. The weekly MDE of every cell is about 6.1k/wk (paired SD of the difference at ratio 0.25): all predicted and seen effects (1k-8k) are of that order, so the CI-based claim could not have seen less than ~6.1k/wk; the sleeve criterion does not need the CI, so the verdicts rest on holdout sign, Sharpe, correlation, placebo and neighbours.

| cell | old verdict | d mean @0.25 $/wk (paired CI) | MDE | WFPRE / HOLD / L8W d mean | Sharpe A -> port | corr | d maxDD % | placebo used (WF; independent 2013-23) | x2 | year max | nb d mean | NEW |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| NQ_RSI2_t10 | T3.6b1 8/9 fail p1 maxDD; T3.8A NQ 2013-2023 OOS passes o1-o6 | 5099 [980, 10121] | 6140 | 4670 / 5496 / -6589 | 0.239 -> 0.282 | -0.05 | +2.7 | 0.978 ; 0.986 | 5061 | 0.42 | [3025, 6456] | **PASS** |
| NQ_RSI2T_t10 | T3.6b1 8/9 fail p1 | 4441 [548, 9523] | 6140 | 3601 / 5303 / -9357 | 0.239 -> 0.279 | -0.09 | +3.8 | 0.956 ; n/a | 4399 | 0.43 | [1761, 6265] | **PASS** |
| NQ_RSI2C_s20 | T3.7 RSI2-combo 8/9 fail p1 (stop worsens maxDD) | 5284 [1147, 10141] | 6140 | 4218 / 6383 / -7784 | 0.239 -> 0.285 | -0.06 | +3.2 | 0.978 ; n/a | 5240 | 0.44 | [5943, 5099] | **PASS** |
| NQ_RSI2CC_s20 | T3.7 RSI2-combo+3-lot cap 8/9 fail p1 | 5284 [1147, 10141] | 6140 | 4218 / 6383 / -7784 | 0.239 -> 0.285 | -0.06 | +3.2 | 0.984 ; n/a | 2624 | 0.44 | [5943, 5099] | **PASS** |
| ES_RSI2_t10 | T3.8A 8/9 fail p1 | 6279 [1779, 11051] | 6140 | 5310 / 7257 / 7860 | 0.239 -> 0.284 | 0.09 | +1.7 | 0.99 ; 0.966 | 6158 | 0.45 | [6126, 7580] | **PASS** |
| RTY_RSI2_t10 | T3.8A 8/9 fail p1 | 8005 [4181, 12492] | 6140 | 4085 / 12210 / 10044 | 0.239 -> 0.301 | 0.07 | +1.7 | 1.0 ; 0.86 | 7838 | 0.53 | [4733, 6171] | **PASS** |
| NQ_IBS_t20_n1 | T3.7b4 7/9 fail p1+placebo 0.94; OOS fails CI/placebo/year share | 4232 [210, 9065] | 6140 | 3039 / 5486 / -1070 | 0.239 -> 0.276 | -0.07 | +5.3 | 0.94 ; 0.946 | 4186 | 0.47 | [3189, 4846] | **CANDIDATE** |
| ES_IBS_t20_n1 | T3.8A 6/9 | 3160 [-793, 7774] | 6140 | 1923 / 4478 / -3417 | 0.239 -> 0.265 | -0.05 | +0.0 | 0.828 ; 0.922 | 2969 | 0.45 | [2740, 4338] | **DEAD** |
| RTY_IBS_t20_n1 | T3.8A 6/9 | 3618 [-198, 8091] | 6140 | 2316 / 5002 / -3988 | 0.239 -> 0.266 | -0.01 | +3.4 | 0.922 ; 0.918 | 3397 | 0.53 | [4816, 3669] | **CANDIDATE** |
| COMB_c3_R | T3.8A 8/9 fail p1 (+9.3% maxDD) | 5118 [1131, 9760] | 6140 | 5321 / 4818 / -6224 | 0.239 -> 0.286 | -0.10 | +7.8 | 0.964 ; 0.978 | 2767 | 0.6 | [5118, 5118] | **PASS** |
| BRK_960_1080 | T3.8B 8/9 fail p1; DSR 0.08; 2013-2023 +30/wk 4/11 yrs | 4853 [592, 9054] | 6140 | 4370 / 5315 / 6190 | 0.239 -> 0.277 | 0.00 | -2.1 | 0.994 ; n/a | 4174 | 0.46 | [3834, 2289] | **PASS** |
| GSHORT_t90 | T3.8B 7/9 fail p1,p5 | 2970 [-1498, 7377] | 6140 | 2060 / 3931 / 2485 | 0.239 -> 0.258 | 0.02 | +28.9 | 0.962 ; n/a | 2911 | 0.57 | [2555, 1996] | **PASS** |
| ON_none | T3.3 5/6 fails CI; T3.5 12/16 (OOS 2013-2023 placebo 0.32) | 3738 [-428, 7963] | 6140 | 2576 / 4965 / -6844 | 0.239 -> 0.267 | -0.00 | -14.5 | 0.884 ; 0.324 | 3518 | 0.5 | [3865, 3907] | **DEAD** |
| ON_VT | T3.3 5/6 fails placebo 0.75; T3.5 12/16 | 4220 [137, 8729] | 6140 | 4554 / 3789 / -12755 | 0.239 -> 0.273 | -0.03 | -7.4 | 0.768 ; 0.292 | 4006 | 0.68 | [3358, 3412] | **DEAD** |
| ORB_ASIA_15_v1_s60 | T3.2 5/6 fails c2 maxDD (all ratios) | 4462 [426, 8988] | 6140 | 2360 / 6713 / 10690 | 0.239 -> 0.268 | 0.08 | +15.0 | 0.958 ; n/a | 3435 | 0.52 | [1491, 4472] | **PASS** |
| ORB_ASIA_15_v1_s75 | T3.2 5/6 fails c2 maxDD (all ratios) | 4472 [268, 8714] | 6140 | 765 / 8496 / 11490 | 0.239 -> 0.269 | 0.06 | +12.9 | 0.962 ; n/a | 3346 | 0.5 | [4462, 1491] | **PASS** |

## Conditions met / failed per cell
- NQ_RSI2_t10 -> PASS: met ['WF mean up', 'holdout sign agrees', 'neighbours agree', 'placebo>=0.90', 'object criterion (sleeve)', 'CI excludes 0', '2x-cost sign', 'year share<=60%', 'maxDD not worse']; failed []
- NQ_RSI2T_t10 -> PASS: met ['WF mean up', 'holdout sign agrees', 'neighbours agree', 'placebo>=0.90', 'object criterion (sleeve)', 'CI excludes 0', '2x-cost sign', 'year share<=60%', 'maxDD not worse']; failed []
- NQ_RSI2C_s20 -> PASS: met ['WF mean up', 'holdout sign agrees', 'neighbours agree', 'placebo>=0.90', 'object criterion (sleeve)', 'CI excludes 0', '2x-cost sign', 'year share<=60%', 'maxDD not worse']; failed []
- NQ_RSI2CC_s20 -> PASS: met ['WF mean up', 'holdout sign agrees', 'neighbours agree', 'placebo>=0.90', 'object criterion (sleeve)', 'CI excludes 0', '2x-cost sign', 'year share<=60%', 'maxDD not worse']; failed []
- ES_RSI2_t10 -> PASS: met ['WF mean up', 'holdout sign agrees', 'neighbours agree', 'placebo>=0.90', 'object criterion (sleeve)', 'CI excludes 0', '2x-cost sign', 'year share<=60%', 'maxDD not worse']; failed []
- RTY_RSI2_t10 -> PASS: met ['WF mean up', 'holdout sign agrees', 'neighbours agree', 'placebo>=0.90', 'object criterion (sleeve)', 'CI excludes 0', '2x-cost sign', 'year share<=60%', 'maxDD not worse']; failed []
- NQ_IBS_t20_n1 -> CANDIDATE: met ['WF mean up', 'holdout sign agrees', 'neighbours agree', 'placebo>=0.90', 'object criterion (sleeve)', 'CI excludes 0', '2x-cost sign', 'year share<=60%', 'maxDD not worse']; failed ['placebo>=0.95']
- ES_IBS_t20_n1 -> DEAD: met ['WF mean up', 'holdout sign agrees', 'neighbours agree', 'object criterion (sleeve)', '2x-cost sign', 'year share<=60%', 'maxDD not worse']; failed ['placebo>=0.90', 'placebo>=0.95', 'CI excludes 0']
- RTY_IBS_t20_n1 -> CANDIDATE: met ['WF mean up', 'holdout sign agrees', 'neighbours agree', 'placebo>=0.90', 'object criterion (sleeve)', '2x-cost sign', 'year share<=60%', 'maxDD not worse']; failed ['placebo>=0.95', 'CI excludes 0']
- COMB_c3_R -> PASS: met ['WF mean up', 'holdout sign agrees', 'neighbours agree', 'placebo>=0.90', 'object criterion (sleeve)', 'CI excludes 0', '2x-cost sign', 'year share<=60%', 'maxDD not worse']; failed []
- BRK_960_1080 -> PASS: met ['WF mean up', 'holdout sign agrees', 'neighbours agree', 'placebo>=0.90', 'object criterion (sleeve)', 'CI excludes 0', '2x-cost sign', 'year share<=60%', 'maxDD not worse']; failed []
- GSHORT_t90 -> PASS: met ['WF mean up', 'holdout sign agrees', 'neighbours agree', 'placebo>=0.90', 'object criterion (sleeve)', '2x-cost sign', 'year share<=60%', 'maxDD not worse']; failed ['CI excludes 0']
- ON_none -> DEAD: met ['WF mean up', 'holdout sign agrees', 'neighbours agree', 'object criterion (sleeve)', '2x-cost sign', 'year share<=60%', 'maxDD not worse']; failed ['placebo>=0.90', 'placebo>=0.95', 'CI excludes 0']
- ON_VT -> DEAD: met ['WF mean up', 'holdout sign agrees', 'neighbours agree', 'object criterion (sleeve)', 'CI excludes 0', '2x-cost sign', 'maxDD not worse']; failed ['placebo>=0.90', 'placebo>=0.95', 'year share<=60%']
- ORB_ASIA_15_v1_s60 -> PASS: met ['WF mean up', 'holdout sign agrees', 'neighbours agree', 'placebo>=0.90', 'object criterion (sleeve)', 'CI excludes 0', '2x-cost sign', 'year share<=60%', 'maxDD not worse']; failed []
- ORB_ASIA_15_v1_s75 -> PASS: met ['WF mean up', 'holdout sign agrees', 'neighbours agree', 'placebo>=0.90', 'object criterion (sleeve)', 'CI excludes 0', '2x-cost sign', 'year share<=60%', 'maxDD not worse']; failed []

## Notes that qualify the verdicts
- RSI2 NQ/RSI2T/RSI2C/RSI2CC, ES RSI2, RTY RSI2 and COMB are one correlated dip-buy exposure (WF weekly correlations: NQ-ES RSI2 0.73, NQ RSI2-COMB 0.81, NQ RSI2-NQ IBS 0.68, NQ-RTY 0.32; BRK, ORB and GSHORT are ~0 to all of them), not six independent systems; count it as ONE PASS family. IBS (NQ, RTY) is the same exposure again, CANDIDATE only because its placebo is 0.94 / 0.92. ES_IBS is DEAD (WF placebo 0.83).
- NQ RSI2_t10 independent window 2013-2023: passes all six OOS gates (placebo 0.986, CI [36, 301]); ES RSI2 OOS placebo 0.966 with CI including 0; RTY RSI2 OOS (7 years, 172 trades) placebo 0.86, informational per prereg. RSI2 uses the same signal in the 1-lot sleeve and the sleeve is long-only: its weakness is regime (2015-16, 2019 flat/negative, 2022 for IBS).
- RSI2C_s20 and RSI2CC_s20 have identical WF-PRE and WF numbers because the 3-lot cap does not bind in the scored window at ratio 0.25; they are one rule for registration.
- COMB_c3_R: PASS on the sleeve rule but 2020 is 68% of its 2013-2023 total and 2022 lost 144k at 3 lots; the trailing-8w halving rule raises the maxDD (+9.3%) versus the un-ruled sleeve; L8W d mean is -5,120 (negative). Worth forward paper, not capital.
- BRK_960_1080: PASS formally (placebo 0.994, CI [592, 9054], holdout +438/wk, corr 0.00), but 2013-2023 earned only +30/wk with 4/11 positive years and halt-period slippage is modelled at 1 tick/side; DSR 0.08. Treat the PASS as fragile; it is the most window-dependent PASS.
- GSHORT_t90: PASS formally on the sleeve rule but only ~31 trades in 142 weeks, CI [-1498, 7377] includes 0, portfolio maxDD +28.9%: the sleeve rule cannot see that; it has least evidence of all PASSes. Per directive, the weekly test of this cell could not have seen less than 6.1k/wk; its effect is 3.0k.
- ORB_ASIA_15_v1 s60/s75: PASS on the sleeve rule (they failed ONLY maxDD in the old test, which V2 withdraws as a sleeve condition); portfolio maxDD is +12 to +15% worse at 0.25 and the unit size implies >50 lots at higher ratios (T3.2 lots_over_50_note). IS (2023-02..2024-01) standalone was negative (-3.4k/wk at scale): the edge is a 2024+ result. Same strategy at two stop widths = one system.
- ON_none: DEAD. The 2013-2023 placebo rank is 0.324 (the overnight edge is no better than a random clock; WF placebo 0.966 on days, 0.884 on the T3.5 clock placebo). ON_VT: DEAD for the same reason (0.292) plus the year share. Old T3.3 verdict (5/6, fails CI only) was a CI-only fail; the CI is not why it is dead now.
- The three PASS families that matter for forward paper: dip-buy (RSI2 NQ/ES/RTY), BRK, ORB Asia; GSHORT and COMB are registered as PASS under the interim rules but should be read with the caveats above.

## Registrations written (l2vast/struct48/paper_all/NM_E_<cell>.json)
- NM_E_BRK_960_1080.json
- NM_E_COMB_c3_R.json
- NM_E_ES_RSI2_t10.json
- NM_E_GSHORT_t90.json
- NM_E_NQ_IBS_t20_n1.json
- NM_E_NQ_RSI2CC_s20.json
- NM_E_NQ_RSI2C_s20.json
- NM_E_NQ_RSI2T_t10.json
- NM_E_NQ_RSI2_t10.json
- NM_E_ORB_ASIA_15_v1_s60.json
- NM_E_ORB_ASIA_15_v1_s75.json
- NM_E_RTY_IBS_t20_n1.json
- NM_E_RTY_RSI2_t10.json

## Not rescored in group E
Cells with < 70% of old conditions (T3.1 all 90 cells, best 4/10; T3.2 ORB_ASIA_30_v1 s50/s60/s75 4/6, ORB_NY_15_v0/v1 4/6 and below, ORB_LON, DON; T3.3 ON_PD5 4/6, ST10, BO, WK; T3.6 batch 1/2 other ideas best 6/9 GAP_t5_x690; T3.7 b3/b4 ZNP_h60 6/9 (67%), IBS_t20_n2 6/9; T3.8 YM RSI2/IBS 5/9, ES/YM IBS) and the XDIP/AFR/VTB cells of T3.8B were not re-scored: they cleared < 70% of their old conditions and their holdout means or placebos are below the CANDIDATE bar in the stored rows (e.g. XDIP_CL placebo 0.65, VTB 0.46, YM_RSI2 placebo 0.94 but year share 0.70 and CI includes 0 -> if the lead wants them, they would be DEAD or at best CANDIDATE on the stored numbers). T3.4 risk-parity assembly and T3.9 (batch running now) are not in scope.


---

# NM-B near-miss re-score: Set B / BEST5 / PBDAY cells (RESEARCH V2 sections 1-3)
Prereg prereg/NM_B.md (sha256 c5b95bdf176125b7c8b6258c0e44b899cdeaa6f281d22d28c7f1bbd4c93b0019, logged in DECISIONS.md before scoring); pre-holdout text prereg/NM_B_PREHOLD.md, holdout look logged as track NM-B. Code l2vast/struct48/code/nmb_{build,cells,score,mde,prereg}.py; results rows/NM_B.json, out/NM_B/. Registrations: l2vast/struct48/paper_all/B*.json.
**Object type: sizing / lock rule. Test: weekly paired difference vs benchmark (live Set A, corrected P9, same engine), 8-week block bootstrap + iid-week bootstrap, 142 WF weeks. Criterion (section 3): mean not down and SD or maxDD down with CI excluding 0, or mean up with CI excluding 0 and maxDD not worse (daily path).**
Earlier holdout looks (disclosure): WF totals (including 2025-07+) for all these cells were printed in REPORT_PBDAY / DS2_FIRM V4-V6 / FWD_AB_SETS; PBDAY printed a frozen holdout for its three WF-chosen Set B -2R variants; V5 printed a frozen holdout for its top-5 H1 picks. The holdout is not blind for these cells.

## Headline
- **Set B (cap off, floor 12R, 14/10/10) = CANDIDATE, not PASS.** WF +8,131/wk vs Set A (24,978 -> 33,109), maxDD 401,641 -> 320,103 (-81.5k, -20%), SD +2.2k, worst week -189k vs -137k. Block-bootstrap CI of the mean difference [-80, +16,029] (iid-week CI [584, 15,552]); CI of the maxDD difference [-282k, +97k] and of the SD difference [-4.7k, +8.7k] include 0. **Could not have seen a mean effect smaller than 11.5k/wk, a maxDD effect smaller than 268k, or an SD effect smaller than 9.6k on 142 weeks: the predicted +8.1k is below the detectable effect, so this test cannot confirm Set B and cannot reject it.** Holdout (2025-07+) d mean +5,959, d maxDD -10.8k, L8W +22.8k, IS -3.4k (IS is where it loses: 13.7k -> 10.3k, IS maxDD -31k). Neighbours (floor 8R +3.4k; floor 16R identical to 12R, floor not binding above 12; lots 14/12/12 +10.4k; lots 14/8/8 +3.7k) all positive. 2x cost sign positive (+8.0k, approximate). Largest year share 48%.
- Why CANDIDATE and not PASS: criterion fails on the CI (CI of the mean difference includes 0 on the block bootstrap; maxDD and SD differences not detectable). Placebo is inherited, not run for Set B: V5 BEST5 lock-timing placebo has maxDD rank 1.00 but mean rank 0.42 (income not better than random locks), size-subset placebo 0.98/1.00. If the mean claim were the criterion, the 0.42 would make it DEAD; the maxDD claim carries it. Selection multiplicity: Set B came from a 23,040-cell screen (DSR 0.975 at n=3,601 in PBDAY; BEST5 0.66). This is the live-selected alternative that the forward Set A vs Set B column already tracks (FWD_AB_SETS).
- **BEST5 (keep 67% after 2 trades) = DEAD:** mean +558 (CI [-8.2k, +8.6k]), maxDD -114k, SD -11.4k (the SD difference CI excludes 0), but neighbours disagree (keep 80%: negative), holdout d maxDD +20k, 2024-26 year share 316%. Could not have seen a mean effect below 12.2k/wk.
- Remove cap + week floor (14/14), B03: mean +9,770/wk, CI [4,230, 15,910] excludes 0, maxDD -76.7k, SD +6.8k, holdout +5.1k, neighbours agree, but placebo 0.73 (W1 capwk worlds) < 0.90 and holdout maxDD +36.6k worse: DEAD (nearest miss; fails placebo only, plus SD/maxDD CI undetectable).

## All cells
| cell | what | WF d mean (benchmark) | CI mean (block) [iid] | d SD / d maxDD (daily) | MDE mean / SD / maxDD | placebo used | HOLD d mean / d maxDD | L8W / IS d mean | neighbours | old verdict | NEW |
|---|---|---|---|---|---|---|---|---|---|---|---|
| B01_SetB | pb|A|SETB|2R vs pb|A|LIVE|2R | 8,131 (24,978) | [-80, 16,029] [584, 15,552] | 2,163 / -81,538 | 11,517 / 9,618 / 267,867 | 1.0 | 5,959 / -10,783 | 22,803 / -3,398 | True | PBDAY/FWD_AB_SETS: Set B reproduces +8.1k/wk vs live, CI [1.8k,15.1k], DSR 0.975; DS2-FIRM | **CANDIDATE** |
| B02_BEST5 | v6|BEST5 vs pb|A|LIVE|2R | 558 (24,978) | [-8,178, 8,634] [-7,703, 8,572] | -11,397 / -114,344 | 12,124 / 9,233 / 251,064 | 1.0 | 373 / 20,164 | 21,932 / -471 | False | DS2-FIRM V5: strict objective (mean>=bench AND maxDD<=0.7x) met by 0/23,040 cells (closest | **DEAD** |
| B03_RemCapWk | W1|pb+gb vs pb|A|LIVE|2R | 9,770 (24,978) | [4,230, 15,910] [3,968, 16,663] | 6,754 / -76,689 | 8,410 / 10,004 / 232,961 | 0.73 | 5,142 / 36,560 | 7,412 / 5,343 | True | DS2-FIRM W1: removing cap+week floor +9.8k/wk, maxDD -76k, CI90 [5.3k,15.1k], 10/11 folds  | **DEAD** |
| B04_CapOff_Wk12 | v5|capoff_wk12_1414 vs pb|A|LIVE|2R | 3,776 (24,978) | [-287, 8,548] [-498, 9,362] | -1,724 / -76,689 | 6,325 / 7,067 / 217,884 | 0.83 | 467 / 36,560 | 0 / 5,093 | True | DS2-FIRM V5 B6: cap off, week floor 12R at 14/14 lots (part of the Set B grid) | **DEAD** |
| B05_SetB_pb3R_vsA | pb|A|SETB|3R vs pb|A|LIVE|2R | 9,066 (24,978) | [-1,773, 18,525] [-747, 18,441] | 14,777 / -77,740 | 14,504 / 11,862 / 323,775 | 1.0 | 12,967 / 45,571 | 18,848 / -6,035 | True | PBDAY: Set B with per-book day loss relaxed to 3R; NOT SUPPORTED as a day-limit lever, Set | **CANDIDATE** |
| B05_SetB_pb4R_vsA | pb|A|SETB|4R vs pb|A|LIVE|2R | 8,383 (24,978) | [-2,578, 18,411] [-2,379, 18,479] | 17,737 / -69,563 | 15,153 / 14,333 / 343,591 | 1.0 | 9,550 / 35,938 | 18,809 / -6,307 | True | PBDAY: Set B with per-book day loss relaxed to 4R; NOT SUPPORTED as a day-limit lever, Set | **CANDIDATE** |
| B05_SetB_pboff_vsA | pb|A|SETB|off vs pb|A|LIVE|2R | 10,507 (24,978) | [-273, 20,378] [-683, 21,232] | 17,517 / -52,489 | 14,917 / 14,475 / 347,961 | 1.0 | 12,226 / 46,075 | 19,740 / -5,856 | True | PBDAY: Set B with per-book day loss relaxed to off; NOT SUPPORTED as a day-limit lever, Se | **CANDIDATE** |
| B06_SetB_pb2R_noprofit_vsA | pb|B|SETB|2R|nopft vs pb|A|LIVE|2R | 8,016 (24,978) | [-522, 16,241] [313, 15,913] | 3,113 / -81,538 | 12,031 / 10,924 / 267,746 | 1.0 | 6,479 / -10,783 | 30,273 / -3,398 | True | PBDAY T1b: profit rule (+5R) off in Set B, day loss 2R | **CANDIDATE** |
| B06_SetB_pb3R_noprofit_vsA | pb|B|SETB|3R|nopft vs pb|A|LIVE|2R | 9,125 (24,978) | [-1,522, 18,982] [-764, 18,844] | 16,063 / -77,740 | 14,811 / 13,330 / 324,158 | 1.0 | 13,851 / 45,571 | 26,318 / -6,035 | True | PBDAY T1b: profit rule (+5R) off in Set B, day loss 3R | **CANDIDATE** |
| B06_SetB_pb4R_noprofit_vsA | pb|B|SETB|4R|nopft vs pb|A|LIVE|2R | 8,442 (24,978) | [-2,458, 18,693] [-2,166, 18,860] | 19,009 / -69,563 | 15,356 / 15,676 / 344,620 | 1.0 | 10,434 / 35,938 | 26,279 / -6,307 | True | PBDAY T1b: profit rule (+5R) off in Set B, day loss 4R | **CANDIDATE** |
| B06_SetB_pboff_noprofit_vsA | pb|B|SETB|off|nopft vs pb|A|LIVE|2R | 10,566 (24,978) | [-327, 20,628] [-595, 21,423] | 18,463 / -52,489 | 15,151 / 15,429 / 348,600 | 1.0 | 13,110 / 46,075 | 27,210 / -5,856 | True | PBDAY T1b: profit rule (+5R) off in Set B, day loss off | **CANDIDATE** |
| B07_SetB_Rscaled_pb2R_vsA | pb|C|SETB|2R|Rscaled vs pb|A|LIVE|2R | 6,902 (24,978) | [-1,070, 14,596] [-1,256, 15,424] | 3,088 / -17,342 | 11,126 / 12,023 / 243,429 | 1.0 | 1,611 / 60,976 | 3,871 / -3,881 | True | PBDAY C: R-scaled reading (limit shrinks to 10/14 in London/NY), day loss 2R; lowest maxDD | **CANDIDATE** |
| B07_SetB_Rscaled_pb3R_vsA | pb|C|SETB|3R|Rscaled vs pb|A|LIVE|2R | 10,200 (24,978) | [1,009, 18,141] [1,258, 18,579] | 9,253 / -83,849 | 12,491 / 11,375 / 272,651 | 0.42 | 12,129 / 40,793 | 15,935 / -2,823 | True | PBDAY C: R-scaled reading (limit shrinks to 10/14 in London/NY), day loss 3R; lowest maxDD | **DEAD** |
| B07_SetB_Rscaled_pb4R_vsA | pb|C|SETB|4R|Rscaled vs pb|A|LIVE|2R | 8,344 (24,978) | [-1,554, 17,422] [-1,544, 17,856] | 14,455 / -65,034 | 13,514 / 13,239 / 317,791 | 1.0 | 11,151 / 69,474 | 18,338 / -6,175 | True | PBDAY C: R-scaled reading (limit shrinks to 10/14 in London/NY), day loss 4R; lowest maxDD | **CANDIDATE** |
| B08_Live_pb3R_vsA | pb|A|LIVE|3R vs pb|A|LIVE|2R | -2,863 (24,978) | [-9,103, 3,365] [-9,651, 4,426] | 10,445 / 29,423 | 9,019 / 8,824 / 239,878 | 0.78 | -771 / 33,817 | 4,014 / -3,372 | True | PBDAY live layer: day loss 3R: NOT SUPPORTED (mean -2.9k, maxDD worse) | **DEAD** |
| B08_Live_pb4R_vsA | pb|A|LIVE|4R vs pb|A|LIVE|2R | -252 (24,978) | [-7,017, 6,239] [-8,115, 8,216] | 10,856 / 37,834 | 9,756 / 11,310 / 292,349 | 0.83 | 3,158 / 10,051 | 4,523 / -10,697 | True | PBDAY live layer: day loss 4R: NOT SUPPORTED (mean -0.3k, maxDD worse) | **DEAD** |
| B08_Live_pboff_vsA | pb|A|LIVE|off vs pb|A|LIVE|2R | -1,376 (24,978) | [-10,042, 6,606] [-10,180, 8,188] | 14,992 / 104,228 | 12,335 / 9,262 / 372,370 | None | 2,096 / 66,065 | 2,801 / -10,597 | True | PBDAY live layer: day loss off: NOT SUPPORTED (mean -1.4k, maxDD worse) | **DEAD** |
| B09_Live_noprofit_vsA | pb|B|LIVE|2R|nopft vs pb|A|LIVE|2R | 261 (24,978) | [-617, 1,272] [-661, 1,296] | -623 / 0 | 1,319 / 1,675 / 20,313 | 0.86 | 93 / 0 | -1,371 / 0 | True | PBDAY T1b: live with +5R profit lock off: +0.26k, CI [-0.45k,+1.13k] | **DEAD** |
| B10_SetB_pb3R_vsSetB | pb|A|SETB|3R vs pb|A|SETB|2R | 935 (33,109) | [-4,696, 6,911] [-4,936, 6,704] | 12,613 / 3,799 | 8,241 / 8,398 / 154,045 | 0.2 | 7,008 / 56,354 | -3,955 / -2,637 | True | PBDAY: Set B day loss 3R vs Set B -2R: +0.9k/wk, CI spans 0; maxDD +1..9% worse; worst day | **DEAD** |
| B10_SetB_pb4R_vsSetB | pb|A|SETB|4R vs pb|A|SETB|2R | 252 (33,109) | [-5,249, 6,054] [-6,487, 6,818] | 15,573 / 11,975 | 8,094 / 10,813 / 188,865 | 0.0 | 3,591 / 46,721 | -3,994 / -2,909 | True | PBDAY: Set B day loss 4R vs Set B -2R: +0.3k/wk, CI spans 0; maxDD +1..9% worse; worst day | **DEAD** |
| B10_SetB_pboff_vsSetB | pb|A|SETB|off vs pb|A|SETB|2R | 2,376 (33,109) | [-2,595, 7,544] [-4,737, 9,274] | 15,354 / 29,049 | 7,471 / 10,988 / 183,454 | None | 6,267 / 56,858 | -3,063 / -2,458 | True | PBDAY: Set B day loss off vs Set B -2R: +2.4k/wk, CI spans 0; maxDD +1..9% worse; worst da | **DEAD** |

## Conditions per cell (met / failed)
- B01_SetB CANDIDATE: failed ['object criterion (sizing/lock rule)', 'CI excludes 0']; met ['WF mean up', 'holdout sign agrees', 'neighbours agree', 'placebo>=0.90', 'placebo>=0.95', '2x-cost sign', 'year share<=60%', 'maxDD not worse']
- B02_BEST5 DEAD: failed ['neighbours agree', 'CI excludes 0', 'year share<=60%']; met ['WF mean up', 'holdout sign agrees', 'placebo>=0.90', 'placebo>=0.95', 'object criterion (sizing/lock rule)', '2x-cost sign', 'maxDD not worse']
- B03_RemCapWk DEAD: failed ['placebo>=0.90', 'placebo>=0.95']; met ['WF mean up', 'holdout sign agrees', 'neighbours agree', 'object criterion (sizing/lock rule)', 'CI excludes 0', '2x-cost sign', 'year share<=60%', 'maxDD not worse']
- B04_CapOff_Wk12 DEAD: failed ['placebo>=0.90', 'placebo>=0.95', 'object criterion (sizing/lock rule)', 'CI excludes 0', 'year share<=60%']; met ['WF mean up', 'holdout sign agrees', 'neighbours agree', '2x-cost sign', 'maxDD not worse']
- B05_SetB_pb3R_vsA CANDIDATE: failed ['object criterion (sizing/lock rule)', 'CI excludes 0']; met ['WF mean up', 'holdout sign agrees', 'neighbours agree', 'placebo>=0.90', 'placebo>=0.95', '2x-cost sign', 'year share<=60%', 'maxDD not worse']
- B05_SetB_pb4R_vsA CANDIDATE: failed ['object criterion (sizing/lock rule)', 'CI excludes 0']; met ['WF mean up', 'holdout sign agrees', 'neighbours agree', 'placebo>=0.90', 'placebo>=0.95', '2x-cost sign', 'year share<=60%', 'maxDD not worse']
- B05_SetB_pboff_vsA CANDIDATE: failed ['object criterion (sizing/lock rule)', 'CI excludes 0']; met ['WF mean up', 'holdout sign agrees', 'neighbours agree', 'placebo>=0.90', 'placebo>=0.95', '2x-cost sign', 'year share<=60%', 'maxDD not worse']
- B06_SetB_pb2R_noprofit_vsA CANDIDATE: failed ['object criterion (sizing/lock rule)', 'CI excludes 0']; met ['WF mean up', 'holdout sign agrees', 'neighbours agree', 'placebo>=0.90', 'placebo>=0.95', '2x-cost sign', 'year share<=60%', 'maxDD not worse']
- B06_SetB_pb3R_noprofit_vsA CANDIDATE: failed ['object criterion (sizing/lock rule)', 'CI excludes 0']; met ['WF mean up', 'holdout sign agrees', 'neighbours agree', 'placebo>=0.90', 'placebo>=0.95', '2x-cost sign', 'year share<=60%', 'maxDD not worse']
- B06_SetB_pb4R_noprofit_vsA CANDIDATE: failed ['object criterion (sizing/lock rule)', 'CI excludes 0']; met ['WF mean up', 'holdout sign agrees', 'neighbours agree', 'placebo>=0.90', 'placebo>=0.95', '2x-cost sign', 'year share<=60%', 'maxDD not worse']
- B06_SetB_pboff_noprofit_vsA CANDIDATE: failed ['object criterion (sizing/lock rule)', 'CI excludes 0']; met ['WF mean up', 'holdout sign agrees', 'neighbours agree', 'placebo>=0.90', 'placebo>=0.95', '2x-cost sign', 'year share<=60%', 'maxDD not worse']
- B07_SetB_Rscaled_pb2R_vsA CANDIDATE: failed ['object criterion (sizing/lock rule)', 'CI excludes 0']; met ['WF mean up', 'holdout sign agrees', 'neighbours agree', 'placebo>=0.90', 'placebo>=0.95', '2x-cost sign', 'year share<=60%', 'maxDD not worse']
- B07_SetB_Rscaled_pb3R_vsA DEAD: failed ['placebo>=0.90', 'placebo>=0.95']; met ['WF mean up', 'holdout sign agrees', 'neighbours agree', 'object criterion (sizing/lock rule)', 'CI excludes 0', '2x-cost sign', 'year share<=60%', 'maxDD not worse']
- B07_SetB_Rscaled_pb4R_vsA CANDIDATE: failed ['object criterion (sizing/lock rule)', 'CI excludes 0']; met ['WF mean up', 'holdout sign agrees', 'neighbours agree', 'placebo>=0.90', 'placebo>=0.95', '2x-cost sign', 'year share<=60%', 'maxDD not worse']
- B08_Live_pb3R_vsA DEAD: failed ['WF mean up', 'holdout sign agrees', 'placebo>=0.90', 'placebo>=0.95', 'object criterion (sizing/lock rule)', 'CI excludes 0', 'year share<=60%', 'maxDD not worse']; met ['neighbours agree', '2x-cost sign']
- B08_Live_pb4R_vsA DEAD: failed ['WF mean up', 'holdout sign agrees', 'placebo>=0.90', 'placebo>=0.95', 'object criterion (sizing/lock rule)', 'CI excludes 0', 'year share<=60%', 'maxDD not worse']; met ['neighbours agree', '2x-cost sign']
- B08_Live_pboff_vsA DEAD: failed ['WF mean up', 'holdout sign agrees', 'placebo>=0.90', 'placebo>=0.95', 'object criterion (sizing/lock rule)', 'CI excludes 0', 'year share<=60%', 'maxDD not worse']; met ['neighbours agree', '2x-cost sign']
- B09_Live_noprofit_vsA DEAD: failed ['placebo>=0.90', 'placebo>=0.95', 'object criterion (sizing/lock rule)', 'CI excludes 0', 'year share<=60%']; met ['WF mean up', 'holdout sign agrees', 'neighbours agree', '2x-cost sign', 'maxDD not worse']
- B10_SetB_pb3R_vsSetB DEAD: failed ['placebo>=0.90', 'placebo>=0.95', 'object criterion (sizing/lock rule)', 'CI excludes 0', 'year share<=60%', 'maxDD not worse']; met ['WF mean up', 'holdout sign agrees', 'neighbours agree', '2x-cost sign']
- B10_SetB_pb4R_vsSetB DEAD: failed ['placebo>=0.90', 'placebo>=0.95', 'object criterion (sizing/lock rule)', 'CI excludes 0', '2x-cost sign', 'year share<=60%', 'maxDD not worse']; met ['WF mean up', 'holdout sign agrees', 'neighbours agree']
- B10_SetB_pboff_vsSetB DEAD: failed ['placebo>=0.90', 'placebo>=0.95', 'object criterion (sizing/lock rule)', 'CI excludes 0', 'year share<=60%', 'maxDD not worse']; met ['WF mean up', 'holdout sign agrees', 'neighbours agree', '2x-cost sign']

## Notes and honest limits
- The nine PBDAY relaxations that are CANDIDATE vs Set A (B05, B06, B07 2R/4R) are the Set B lever plus a day-loss/profit-lock change; the increment over Set B (B10) is DEAD in all three (mean +0.3k..+2.4k, CI spans 0, SD +12.6k..15.6k worse, maxDD +3.8k..+29k worse, placebo 0.00-0.94). They are registered because the rule says every CANDIDATE is, but they are one edge, not nine: the forward register should treat B01 as the representative. B07 Rscaled 3R scored DEAD on its own placebo (0.42 mean rank / PBDAY 0.86 hazard, 0.60 shuffled).
- Placebos for Set B-family vs Set A are inherited from V5 (BEST5) and not re-run; no Set B-specific placebo exists. Neighbours for Set B were re-run on the same engine (nmb_build.py; Set B reproduces PBDAY exactly, max|diff| 0).
- 2x-cost sign is approximate (trades/wk x calibrated extra cost; lot factor 0.82 for 14/10/10): positive everywhere; margin >> cost.
- Live-layer relaxations B08 (3R, 4R, off) and the profit-lock-off B09: mean down or +0.26k with CI spanning 0, maxDD +29k..+104k worse (B08): DEAD. Could not have seen less than 8.8k/9.6k/12.2k (B08) and 1.3k (B09) per week.
- maxDD cannot be tested with one 142-week path (MDE 220-380k vs the 50-115k observed differences). The directive's 'maxDD not worse in the full sequence' is satisfied at the point estimate by Set B but not testable for significance.
- Not rescored: BEST5-exact on the 1-s engine with the full R11 sequence test (needs the L2/firm engine run; V5 reported it). No trade-level pairing: sizing/lock change alters the set of trades taken.


---

# NM-C: T4 execution cells and two T2 near-misses, re-scored under RESEARCH V2
prereg prereg/NM_C.md sha256 1d29dd6b7101b6d959e3e1641b519a4a940a66fbfce2316461c01b94751e55dd; pre-holdout text prereg/NM_C_PREHOLD.md; holdout look logged (track NM-C).
Coverage: 2023-02..2026-10 (19 months). The T4 L2 replay does NOT cover 2024-02..2025-06 (WF-PRE) so 'WF' = holdout window for every T4 cell and 'holdout sign' is the same data as 'WF mean up' (not independent); the independent check is the 2023 months (reported). Paired population = Set A's executed trades (locks engine f>0); sensitivity on all replayed rows in autopilot/nm/NM_C_T4_final.json (same verdicts).
Placebo = session sign-flip permutation null of the paired mean (rank = share of null means below the observed mean). x2-cost: fill-timing change, same commission/ticks, sign follows 1x. DSR not applicable to paired execution tests.

## T4 cells (object = execution; test = paired pts/trade, session-block bootstrap 10,000 draws; no weekly test)
| cell | n pairs (sessions) | effect pts/trade [CI] | $/wk at 14 lots | MDE (80%) pts | 2023 pts | holdout pts | placebo | neighbours | old | NEW | met / failed |
|---|---|---|---|---|---|---|---|---|---|---|---|
| T4.1a | 2955 (376) | -0.045 [-0.075, -0.019] | -466 | 0.040 | -0.076 | -0.041 | 0.000 | Y (T4.1b -0.087, T4.4_W2 -0.029) | interim L8W -449 $/wk (no full score) | **DEAD** | met: neighbours_agree; failed: mean_up, holdout_sign_agrees, placebo>=0.90, paired_CI_excludes0, 2x_cost_sign, year_share>60% |
| T4.1b | 2955 (376) | -0.087 [-0.124, -0.055] | -909 | 0.049 | -0.132 | -0.081 | 0.000 | Y (T4.1a -0.045, T4.4_W3t -0.047) | interim L8W -872 $/wk | **DEAD** | met: neighbours_agree; failed: mean_up, holdout_sign_agrees, placebo>=0.90, paired_CI_excludes0, 2x_cost_sign, year_share>60% |
| T4.2_L0 | 2955 (376) | +0.034 [-0.087, +0.158] | +352 | 0.176 | +0.340 | -0.003 | 0.697 | Y (T4.2_Lm2 +0.019, T4.2_Y4 +0.093) | interim L8W -1,996 | **DEAD** | met: mean_up, neighbours_agree; failed: holdout_sign_agrees, placebo>=0.90, paired_CI_excludes0, year_share>60% |
| T4.2_Lm2 | 2955 (376) | +0.019 [-0.108, +0.147] | +200 | 0.182 | +0.297 | -0.014 | 0.597 | Y (T4.2_L0 +0.034, T4.2_Y4 +0.093) | interim L8W +879 | **DEAD** | met: mean_up, neighbours_agree; failed: holdout_sign_agrees, placebo>=0.90, paired_CI_excludes0, year_share>60% |
| T4.2_Y4 | 2955 (376) | +0.093 [+0.038, +0.150] | +971 | 0.080 | +0.170 | +0.084 | 1.000 | Y (T4.2_L0 +0.034, T4.2_Lm2 +0.019) | interim L8W -2,313 | **PASS** | met: mean_up, holdout_sign_agrees, placebo>=0.90, neighbours_agree, paired_CI_excludes0; failed: - |
| T4.2_LB0 | 2955 (376) | -0.643 [-0.998, -0.286] | -6733 | 0.510 | -0.148 | -0.702 | 0.000 | N (T4.2_L0 +0.034, T4.2_Lm2 +0.019) | interim L8W -13,236 | **DEAD** | met: ; failed: mean_up, holdout_sign_agrees, placebo>=0.90, neighbours_agree, paired_CI_excludes0, 2x_cost_sign, year_share>60% |
| T4.3_G1 | 2955 (376) | -0.085 [-0.266, +0.102] | -891 | 0.260 | +0.070 | -0.103 | 0.185 | N (T4.3_S2x7 -0.230, T4.3_G4 +0.048) | interim L8W +135 | **DEAD** | met: ; failed: mean_up, holdout_sign_agrees, placebo>=0.90, neighbours_agree, paired_CI_excludes0, 2x_cost_sign, year_share>60% |
| T4.3_G4 | 2955 (376) | +0.048 [-0.174, +0.271] | +506 | 0.320 | +0.405 | +0.006 | 0.661 | N (T4.3_G1 -0.085, T4.3_S2x7 -0.230) | interim L8W +5,822 | **DEAD** | met: mean_up, holdout_sign_agrees; failed: placebo>=0.90, neighbours_agree, paired_CI_excludes0, year_share>60% |
| T4.3_S2x7 | 2955 (376) | -0.230 [-0.419, -0.037] | -2405 | 0.273 | -0.106 | -0.244 | 0.010 | N (T4.3_G1 -0.085, T4.3_G4 +0.048) | interim L8W -617 | **DEAD** | met: ; failed: mean_up, holdout_sign_agrees, placebo>=0.90, neighbours_agree, paired_CI_excludes0, 2x_cost_sign, year_share>60% |
| T4.4_W2 | 2955 (376) | -0.029 [-0.052, -0.006] | -299 | 0.033 | -0.016 | -0.030 | 0.006 | N (T4.4_W5 +0.049, T4.4_W2t -0.080) | interim L8W -3,610 | **DEAD** | met: ; failed: mean_up, holdout_sign_agrees, placebo>=0.90, neighbours_agree, paired_CI_excludes0, 2x_cost_sign, year_share>60% |
| T4.4_W5 | 2955 (376) | +0.049 [+0.022, +0.076] | +512 | 0.039 | +0.016 | +0.053 | 1.000 | N (T4.4_W2 -0.029, T4.4_W5t +0.002) | interim L8W +1,339 | **DEAD** | met: mean_up, holdout_sign_agrees, placebo>=0.90, paired_CI_excludes0; failed: neighbours_agree, year_share>60% |
| T4.4_W2t | 2955 (376) | -0.080 [-0.115, -0.048] | -837 | 0.048 | -0.085 | -0.079 | 0.000 | Y (T4.4_W3t -0.047, T4.4_W2 -0.029) | interim L8W -4,041 | **DEAD** | met: neighbours_agree; failed: mean_up, holdout_sign_agrees, placebo>=0.90, paired_CI_excludes0, 2x_cost_sign, year_share>60% |
| T4.4_W3t | 2955 (376) | -0.047 [-0.068, -0.029] | -489 | 0.028 | -0.068 | -0.044 | 0.000 | N (T4.4_W2t -0.080, T4.4_W5t +0.002) | interim L8W (n/a) | **DEAD** | met: ; failed: mean_up, holdout_sign_agrees, placebo>=0.90, neighbours_agree, paired_CI_excludes0, 2x_cost_sign, year_share>60% |
| T4.4_W5t | 2955 (376) | +0.002 [-0.034, +0.035] | +19 | 0.049 | -0.052 | +0.008 | 0.550 | N (T4.4_W3t -0.047, T4.4_W5 +0.049) | interim L8W (n/a) | **DEAD** | met: mean_up, holdout_sign_agrees; failed: placebo>=0.90, neighbours_agree, paired_CI_excludes0, year_share>60% |

Detectable effect, plain: the wait/skip cells (T4.1a/b, T4.4_*) could not have seen less than ~0.03-0.05 pts/trade (~$10-20/trade at 14 lots); the entry-slicing and limit cells (T4.2_L0/Lm2, T4.3_*) could not have seen less than ~0.18-0.32 pts/trade; LB0 less than ~0.51. Their nulls (L0, Lm2, G1, G4, S2x7 CIs include 0) say 'no effect larger than that', not 'no effect'.

Reading:
- T4.2_Y4 (14 x 1-lot touch-join limit entries, 2 s life, market fallback): PASS. +0.093 pts/trade (CI +0.038..+0.150), placebo 1.00, holdout +0.084, 2023 months +0.17, both neighbours (L0, Lm2) positive. Caveats: not replayed 2024-02..2025-06; the effect is ~0 in the last 8 weeks (L8W about $5/wk); it relies on the trade-through fill model (live stop-join fill was 8/17 against a replay of 0.78, so passive-fill optimism is the main risk); +$26/trade at 14 lots, ~$970/wk. Registered paper_all/T4.2_Y4.json.
- T4.1a/T4.1b skip-join: DEAD as a replay result: -0.04/-0.09 pts/trade (CI excludes 0 on the negative side, holdout negative) = the measured cost of skipping the join on the ~1.5-5% of exits that overlap. The replay cannot value the avoided live rejection (56>50 lots) so this is the price of the patch, not a verdict on whether to ship it; the patch stays a structural/risk question. Could not have seen a gain smaller than ~0.04-0.05 pts/trade.
- T4.4 waits: W5 (queue model) is +0.049 [+0.022, +0.076], placebo 1.00, holdout +, but DEAD on neighbours: W2 and W5t are negative and W5t (same wait, trade-through fill) is ~0 (+0.002), so the apparent gain exists only under the optimistic queue fill rule. W2, W2t, W3t are significantly negative; W5t null (MDE 0.049). The existing 3 s wait is not beaten.
- T4.2_LB0 (single 14-lot limit) -0.64 pts/trade; T4.3_S2x7 -0.23 (CI excludes 0); G1/G4/L0/Lm2 null within MDE.

## T2 cells (pre-holdout 4 of 5 conditions; holdout looked now for the first time, track NM-C)
| cell | object | test | effect [CI] | MDE | placebo | holdout | maxDD | neighbours | old | NEW | met / failed |
|---|---|---|---|---|---|---|---|---|---|---|---|
| E5S | signal | weekly | +7,065 $/wk [-204, +15,009] | 11,279 $/wk | 0.894 | +7,635 | -17,710 | Y | T2 pre 4/5 (CI, holdout open) | **DEAD** | met: mean_up, holdout_sign_agrees, neighbours_agree; failed: placebo>=0.90, weekly_CI_excludes0&maxDD_not_worse |
| SO_f33_tr20 | trade-modifier | day-paired (D2 trade rows not stored; allocated evenly over each day) | +12,181 $/wk [+3,136, +21,922]; +1.28 pts/trade [+0.36, +2.24] | 13,350 $/wk; 1.34 pts/trade | 0.268 | +12,133 | -19,329 | Y | T2 pre 4/5 (CI, holdout open); placebo 0.416 | **DEAD** | met: mean_up, holdout_sign_agrees, neighbours_agree, paired_CI_excludes0&maxDD_not_worse; failed: placebo>=0.90 |

- E5S (5-variant ensemble): WF +7,065/wk (CI -204..+15,009), maxDD -17.7k, holdout +7,635, neighbours agree, year share ok, 2x sign +; placebo rank on WF 0.894 (0.974 on WF-PRE) is just below the 0.90 floor -> DEAD by one placebo point; could not have seen less than ~11,300 $/wk, so the CI-includes-0 is a power limit. Borderline: closest thing to a CANDIDATE in this group; flagged for the lead, not registered.
- SO_f33_tr20 (scale out 1/3 at +1R, trail 20): +12,181/wk (CI +3,136..+21,922), +1.28 pts/trade [+0.36, +2.24] day-paired (MDE 1.34), holdout +, maxDD -19.3k, neighbours agree; DEAD only on the placebo (0.268: random trails U(10,45) with the same fraction do as well). The gain is generic to 'scale out + trail' (all 4 SO cells positive in T2 pre) and not specific to 20 pts. Also rows are MAPPED costs (T2 prereg: mapped screening overstates +4-7k/wk) and need a direct-L2 re-run. Flag: a null of 'random scale-out parameters' is the wrong null for the generic claim; a 'no scale-out' vs 'any scale-out' test would need a different prereg (not run here).

## Not rescored
- Other T2 cells (37): below 70% of old conditions on WF-PRE (<=3 of 5 passed) or negative; T2 agent a4f51422d4e4ac22e continues them under V2 rules.
- T4 months still being replayed (2023-05, 2024-*, 2025-01..06): re-run `python3 code/nm_c_score.py final` (and nm_c_report.py) to refresh when coverage grows.


---

# NM-D: near-miss re-score of STRUCT48 Track 1 cells and the TH-audit cooldown cells (RESEARCH V2 s1-3)
Preregs: l2vast/struct48/prereg/NM_D1.md sha256 807acd631648ef5e0e4957e6a5ed96d785434e43f3f847dd0deb5bb6e0d203dd (21 T1 cells), NM_D2.md sha256 cd57b301e0d45665a9ff5ed296a30277c857140d26a2fc520317acdea9349db0 (13 TH cells), both logged in DECISIONS.md before scoring. Pre-holdout text prereg/NM_D_PREHOLD.md (logged, holdout look "NM-D" in ledger/holdout_looks.jsonl). Code code/nm_lib.py, nmd_lib.py, nmd_th.py, nmd_final.py; cells out/NM_D_cells.json, rows/NM_D.json.

## Result: PASS 0, CANDIDATE 0, DEAD 34 (21 T1 + 13 TH), plus 130 further T1 cells DEAD from stored rows. No registration records written (nothing to register).

## Verdict function used (interim, code/nm_lib.py verdict(); the lead v2 function governs once READY_V2 appears)
core = WF mean up, holdout sign agrees, neighbours agree (all available same sign of WF paired mean), placebo rank >= 0.90. PASS = core + placebo >= 0.95 + object criterion (trade-modifier: paired mean > 0, paired CI excludes 0, maxDD not worse over the full WF path; lock rule: mean not down and SD or maxDD down with CI, or mean up with maxDD not worse). CANDIDATE = core met, not PASS, at most one further failure among {placebo<0.95, 2x-cost sign, year share>60%, maxDD not worse}; CI including 0 is the allowed failure. DEAD otherwise.

## Honest power statement
T1 cells are trade modifiers scored PAIRED on the same signal stream. Per-trade logs of the regenerated T1 streams are not stored (only daily P&L and trade counts per cell), so the paired unit is the session (day); per-trade effect = paired total / Set A trades in the window (about 5,100 in WF). On WF the 80%-power minimum detectable effect is about $12-23k/wk (about $450-700 per Set A trade) for the window/entry/stop cells, $9k/wk for the T1.1 halt: every T1 prediction ($0.1-8k/wk, $4-390/trade) is far below it. Every T1 null therefore reads "could not have seen less than ~$12-23k/wk (~$0.5k per trade) on 142 weeks". TH cells: MDE $6-10k/wk on 101-142 weeks vs predicted $0.5-2.7k/wk; nulls read "could not have seen less than $6-10k/wk".

## D1: T1 cells (paired per-day, WF 2024-02+; $ at report scale 14/14 x1.75; effects are cell minus Set A)
| cell | object | test | WF effect $/wk [paired 95% CI] | $/Set-A-trade | MDE80 $/wk (could not have seen less than) | holdout sign (eff $/wk) | placebo (stored, WF-PRE) | neighbours agree | WF dMaxDD $ | old verdict | new verdict | conditions failed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| T12_A0000_L0730_N1100 | trade-modifier/session rule | paired day-block | 2,441 [-9,727, 14,504] | 67 | 17,559 | - (-7,789) | 0.958 | False | -46,812 | FAIL 4/6 (failed: CI excl 0, holdout sign) | **DEAD** | holdout sign agrees; neighbours agree; object criterion (trade-modifier/session rule (paired)); CI excludes 0; year share<=60% |
| T12_A0000_L0800_N1100 | trade-modifier/session rule | paired day-block | 2,151 [-10,094, 14,490] | 59 | 17,786 | - (-9,469) | 0.97 | False | -46,918 | FAIL 4/6 (failed: CI excl 0, holdout sign) | **DEAD** | holdout sign agrees; neighbours agree; object criterion (trade-modifier/session rule (paired)); CI excludes 0; 2x-cost sign; year share<=60% |
| T12_A0130_L0730_N1100 | trade-modifier/session rule | paired day-block | 5,844 [-5,158, 16,691] | 161 | 15,745 | + (2,686) | n/a (not run) | False | 24,521 | FAIL 3/6 (failed: maxDD not worse, CI excl 0, placebo>=0.95) | **DEAD** | neighbours agree; placebo>=0.90; placebo>=0.95; object criterion (trade-modifier/session rule (paired)); CI excludes 0; year share<=60%; maxDD not worse |
| T12_A0130_L0800_N1030 | trade-modifier/session rule | paired day-block | 691 [-9,153, 10,360] | 19 | 13,800 | + (1,297) | n/a (not run) | False | 68,605 | FAIL 2/6 (failed: maxDD not worse, CI excl 0, placebo>=0.95, neighbours) | **DEAD** | neighbours agree; placebo>=0.90; placebo>=0.95; object criterion (trade-modifier/session rule (paired)); CI excludes 0; 2x-cost sign; year share<=60%; maxDD not worse |
| T12_A0130_L0800_N1100 | trade-modifier/session rule | paired day-block | 5,206 [-5,607, 16,083] | 144 | 15,540 | + (1,445) | 0.892 | True | -65,792 | FAIL 4/6 (failed: CI excl 0, placebo>=0.95) | **DEAD** | placebo>=0.90; placebo>=0.95; object criterion (trade-modifier/session rule (paired)); CI excludes 0; year share<=60% |
| T12_A0130_L0830_N1100 | trade-modifier/session rule | paired day-block | 3,832 [-6,653, 14,067] | 106 | 14,923 | + (5,107) | 0.582 | False | -15,823 | FAIL 4/6 (failed: CI excl 0, placebo>=0.95) | **DEAD** | neighbours agree; placebo>=0.90; placebo>=0.95; object criterion (trade-modifier/session rule (paired)); CI excludes 0; year share<=60% |
| T12_A0130_L0900_N1100 | trade-modifier/session rule | paired day-block | 3,482 [-6,284, 12,993] | 96 | 13,556 | + (2,348) | 0.802 | False | -17,003 | FAIL 4/6 (failed: CI excl 0, placebo>=0.95) | **DEAD** | neighbours agree; placebo>=0.90; placebo>=0.95; object criterion (trade-modifier/session rule (paired)); CI excludes 0; year share<=60% |
| T12_N1100_only | trade-modifier/session rule | paired day-block | 4,184 [-4,393, 12,924] | 116 | 12,192 | + (2,547) | 0.984 | False | -42,018 | FAIL 4/6 (failed: CI excl 0, neighbours) | **DEAD** | neighbours agree; object criterion (trade-modifier/session rule (paired)); CI excludes 0 |
| T14_L_s50_t1.5_n10 | trade-modifier/session rule | paired day-block | 4,801 [-7,685, 17,334] | 133 | 17,919 | + (6,786) | 0.448 | False | 15,818 | FAIL 3/6 (failed: CI excl 0, placebo>=0.95, neighbours) | **DEAD** | neighbours agree; placebo>=0.90; placebo>=0.95; object criterion (trade-modifier/session rule (paired)); CI excludes 0; year share<=60%; maxDD not worse |
| T14_L_s50_t2.0_n10 | trade-modifier/session rule | paired day-block | 5,632 [-6,925, 18,446] | 156 | 18,463 | + (10,358) | n/a (not run) | True | 231,703 | FAIL 3/6 (failed: maxDD not worse, CI excl 0, placebo>=0.95) | **DEAD** | placebo>=0.90; placebo>=0.95; object criterion (trade-modifier/session rule (paired)); CI excludes 0; year share<=60%; maxDD not worse |
| T14_L_s60_t2.0_n10 | trade-modifier/session rule | paired day-block | 5,900 [-6,358, 18,218] | 163 | 17,644 | + (8,530) | n/a (not run) | False | 40,179 | FAIL 2/6 (failed: maxDD not worse, CI excl 0, placebo>=0.95, neighbours) | **DEAD** | neighbours agree; placebo>=0.90; placebo>=0.95; object criterion (trade-modifier/session rule (paired)); CI excludes 0; maxDD not worse |
| T14_L_s60_t2.0_n14 | trade-modifier/session rule | paired day-block | 5,891 [-6,455, 18,374] | 163 | 17,859 | + (6,350) | n/a (not run) | False | 10,999 | FAIL 2/6 (failed: maxDD not worse, CI excl 0, placebo>=0.95, neighbours) | **DEAD** | neighbours agree; placebo>=0.90; placebo>=0.95; object criterion (trade-modifier/session rule (paired)); CI excludes 0; maxDD not worse |
| T14_S_s50_t1.0_n14 | trade-modifier/session rule | paired day-block | 3,771 [-7,626, 15,663] | 104 | 16,790 | + (912) | 0.782 | False | -6,553 | FAIL 4/6 (failed: CI excl 0, placebo>=0.95) | **DEAD** | neighbours agree; placebo>=0.90; placebo>=0.95; object criterion (trade-modifier/session rule (paired)); CI excludes 0; year share<=60% |
| T14_S_s50_t1.5_n10 | trade-modifier/session rule | paired day-block | 3,871 [-9,064, 16,952] | 107 | 18,766 | + (2,641) | 0.626 | False | -10,075 | FAIL 4/6 (failed: CI excl 0, placebo>=0.95) | **DEAD** | neighbours agree; placebo>=0.90; placebo>=0.95; object criterion (trade-modifier/session rule (paired)); CI excludes 0; year share<=60% |
| T14_S_s50_t1.5_n14 | trade-modifier/session rule | paired day-block | 8,016 [-4,440, 20,357] | 221 | 17,591 | + (7,390) | 0.912 | False | 5,748 | FAIL 4/6 (failed: CI excl 0, placebo>=0.95) | **DEAD** | neighbours agree; placebo>=0.95; object criterion (trade-modifier/session rule (paired)); CI excludes 0; year share<=60%; maxDD not worse |
| T14_S_s50_t2.0_n10 | trade-modifier/session rule | paired day-block | 6,218 [-6,709, 19,483] | 172 | 18,667 | + (7,081) | 0.696 | False | 30,428 | FAIL 4/6 (failed: CI excl 0, placebo>=0.95) | **DEAD** | neighbours agree; placebo>=0.90; placebo>=0.95; object criterion (trade-modifier/session rule (paired)); CI excludes 0; maxDD not worse |
| T14_S_s50_t2.0_n14 | trade-modifier/session rule | paired day-block | 3,312 [-8,903, 15,968] | 91 | 18,012 | + (4,252) | 0.674 | True | -56,705 | FAIL 4/6 (failed: CI excl 0, placebo>=0.95) | **DEAD** | placebo>=0.90; placebo>=0.95; object criterion (trade-modifier/session rule (paired)); CI excludes 0; year share<=60% |
| T14_C | trade-modifier/session rule | paired day-block | 7,952 [-7,814, 24,028] | 220 | 22,910 | + (12,856) | n/a (not run) | True | 86,238 | FAIL 3/6 (failed: maxDD not worse, CI excl 0, placebo>=0.95) | **DEAD** | placebo>=0.90; placebo>=0.95; object criterion (trade-modifier/session rule (paired)); CI excludes 0; year share<=60%; maxDD not worse |
| T11_N2_book_lockon | trade-modifier/session rule | paired day-block | -876 [-7,487, 5,458] | -24 | 9,270 | - (-8,271) | 0.804 | True | -2,087 | FAIL 2/6 (failed: CI excl 0, placebo>=0.95, holdout sign, neighbours) | **DEAD** | WF mean up; holdout sign agrees; placebo>=0.90; placebo>=0.95; object criterion (trade-modifier/session rule (paired)); CI excludes 0; year share<=60% |
| T13_M2_R0 | trade-modifier/session rule | paired day-block | -3,911 [-15,360, 8,007] | -108 | 16,524 | - (-19,440) | n/a (not run) | True | 155,284 | FAIL 2/6 (failed: maxDD not worse, CI excl 0, placebo>=0.95, holdout sign) | **DEAD** | WF mean up; holdout sign agrees; placebo>=0.90; placebo>=0.95; object criterion (trade-modifier/session rule (paired)); CI excludes 0; 2x-cost sign; year share<=60%; maxDD not worse |
| T15_COMBO | trade-modifier/session rule | paired day-block | -2,710 [-16,850, 11,889] | -75 | 20,371 | - (-15,757) | 0.91 | False | -13,289 | FAIL 3/6 (failed: CI excl 0, placebo>=0.95, holdout sign) | **DEAD** | WF mean up; holdout sign agrees; neighbours agree; placebo>=0.95; object criterion (trade-modifier/session rule (paired)); CI excludes 0; year share<=60% |

Notes on the closest cells:
- T14_S_s50_t1.5_n14 (short stop 50, target 1.5R, 14 lots): WF +$8.0k/wk (paired CI includes 0, weekly CI [-4.4k,20.4k]), holdout +, placebo 0.91, three of four neighbours positive but the fourth (T14_S_s60_t1.5_n14, i.e. stop 60) is negative, WF maxDD +$5.7k worse, largest year 68% (2026), 2x cost positive. Fails neighbours (strict all-agree), placebo < 0.95, maxDD, CI, year share -> DEAD. Under a lenient 3-of-4 neighbour rule it would still be DEAD (maxDD and year share are two further failures).
- T12_N1100_only (no NY first entry before 11:00): WF +$4.2k/wk, holdout +, placebo 0.98, maxDD -$42k better, year share 0.56, 2x +; fails ONLY neighbours (its single neighbour T12_N1030_only is WF-negative) and the CI. It is the one T1 cell that is a CANDIDATE except for the neighbour condition; it is listed DEAD under the letter of section 1, flagged here as the nearest miss for the lead to decide whether a single edge neighbour should veto.
- T12_A0000_L0730_N1100, T12_A0000_L0800_N1100: placebo 0.96-0.97 but holdout negative (-$7.7k/-$9.4k per week) -> DEAD.
- T15_COMBO, T13_M2_R0, T11_N2_book_lockon: best-by-WF-PRE selections; WF mean DOWN and holdout down -> DEAD (selection noise).

## D2: TH-audit cooldown cells (lock rule, weekly paired, ST+HM audit book, live layer, 2023-08..2026-02 WF test months; holdout = subset >= 2025-07-01 already seen in the audit)
| cell | object | test | WF effect $/wk [CI] | d SD [CI] | d maxDD $ [CI] | MDE80 $/wk | holdout eff $/wk | sign-flip placebo | neighbours agree | old verdict | new verdict | conditions failed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| RL|PORT|off|3 | lock rule | weekly paired | 236 [-4,077, 4,505] | 3,068 [-1,307, 6,816] | -82,370 [-234,736, 107,144] | 6,145 | 4,989 | 0.54 | False | not real / untested lead | **DEAD** | neighbours agree; placebo>=0.90; placebo>=0.95; CI excludes 0; year share<=60% |
| RL|PORT|off|4 | lock rule | weekly paired | 2,786 [-2,693, 7,926] | 5,520 [1,234, 9,496] | -157,524 [-254,566, 124,174] | 7,633 | 10,682 | 0.84 | True | not real / untested lead | **DEAD** | placebo>=0.90; placebo>=0.95; CI excludes 0; year share<=60% |
| RL|B3tick|off|3 | lock rule | weekly paired | -713 [-6,514, 4,880] | 4,899 [-620, 9,055] | 35,114 [-214,317, 361,753] | 7,910 | 6,705 | 0.41 | False | not real / untested lead | **DEAD** | WF mean up; neighbours agree; placebo>=0.90; placebo>=0.95; object criterion (lock rule (weekly)); CI excludes 0; year share<=60%; maxDD not worse |
| RL|B3tick|off|4 | lock rule | weekly paired | 1,645 [-4,148, 7,560] | 3,592 [-1,925, 8,540] | -145,474 [-263,405, 192,360] | 8,476 | 11,124 | 0.66 | False | not real / untested lead | **DEAD** | neighbours agree; placebo>=0.90; placebo>=0.95; CI excludes 0; year share<=60% |
| RL|B3sec|off|3 | lock rule | weekly paired | -1,547 [-6,873, 3,921] | 3,423 [-1,545, 8,052] | 101,155 [-119,471, 342,639] | 7,597 | 9,081 | 0.28 | False | not real / untested lead | **DEAD** | WF mean up; neighbours agree; placebo>=0.90; placebo>=0.95; object criterion (lock rule (weekly)); CI excludes 0; year share<=60%; maxDD not worse |
| RL|B3sec|off|4 | lock rule | weekly paired | 537 [-5,514, 6,452] | 4,243 [-1,276, 9,180] | -51,968 [-191,914, 172,213] | 8,530 | 14,408 | 0.58 | False | not real / untested lead | **DEAD** | neighbours agree; placebo>=0.90; placebo>=0.95; CI excludes 0; year share<=60% |
| CV|PORT|loss | lock rule | weekly paired | -5,572 [-10,929, -74] | 4,792 [-229, 11,805] | 333,563 [-67,647, 938,868] | 7,636 | -9,495 | 0.02 | True | not real / untested lead | **DEAD** | WF mean up; holdout sign agrees; placebo>=0.90; placebo>=0.95; object criterion (lock rule (weekly)); CI excludes 0; year share<=60%; maxDD not worse |
| CV|PORT|profit | lock rule | weekly paired | -4,300 [-9,779, 1,061] | 4,716 [325, 10,244] | 386,046 [-42,298, 792,750] | 7,909 | -8,717 | 0.08 | True | not real / untested lead | **DEAD** | WF mean up; holdout sign agrees; placebo>=0.90; placebo>=0.95; object criterion (lock rule (weekly)); CI excludes 0; year share<=60%; maxDD not worse |
| CV|PORT|both | lock rule | weekly paired | -3,129 [-8,448, 2,565] | 4,376 [608, 7,801] | 316,297 [-297,493, 824,697] | 7,715 | -10,969 | 0.15 | True | not real / untested lead | **DEAD** | WF mean up; holdout sign agrees; placebo>=0.90; placebo>=0.95; object criterion (lock rule (weekly)); CI excludes 0; year share<=60%; maxDD not worse |
| CV|B3tick|loss | lock rule | weekly paired | -1,206 [-7,809, 5,621] | 3,588 [-3,031, 11,778] | -98,472 [-520,306, 463,302] | 9,423 | -3,546 | 0.40 | True | not real / untested lead | **DEAD** | WF mean up; holdout sign agrees; placebo>=0.90; placebo>=0.95; object criterion (lock rule (weekly)); CI excludes 0; year share<=60% |
| CV|B3tick|profit | lock rule | weekly paired | -2,803 [-8,631, 3,303] | 955 [-3,742, 6,671] | 254,147 [-378,403, 729,172] | 8,682 | -7,454 | 0.16 | True | not real / untested lead | **DEAD** | WF mean up; holdout sign agrees; placebo>=0.90; placebo>=0.95; object criterion (lock rule (weekly)); CI excludes 0; year share<=60%; maxDD not worse |
| CV|B3tick|both | lock rule | weekly paired | -374 [-6,842, 6,352] | 2,579 [-1,780, 7,791] | 2,626 [-836,431, 662,651] | 9,323 | -6,475 | 0.47 | True | not real / untested lead | **DEAD** | WF mean up; holdout sign agrees; placebo>=0.90; placebo>=0.95; object criterion (lock rule (weekly)); CI excludes 0; year share<=60%; maxDD not worse |
| CV|B3sec|loss | lock rule | weekly paired | -875 [-7,685, 5,470] | 2,103 [-3,300, 9,950] | -156,188 [-614,928, 474,812] | 8,969 | -5,645 | 0.37 | True | not real / untested lead | **DEAD** | WF mean up; holdout sign agrees; placebo>=0.90; placebo>=0.95; object criterion (lock rule (weekly)); CI excludes 0; year share<=60% |

Cell codes: RL|engine|off|L = TH-off books with per-book day-loss limit -L R versus the live -2R (lock-rule relaxation); CV|engine|arm = TH conversion = (arm net at -4R minus arm net at -2R) minus (TH-off net at -4R minus -2R), cand=4R vs base=2R; engines PORT (tick port), B3tick, B3sec.
Reading: RL|PORT|off|4 is the best (+$2.8k/wk, CI includes 0, holdout +, maxDD better, but sign-flip placebo 0.84 < 0.90; its MDE is $7.6k/wk, so the audit could not have seen less than $7.6k/wk). Every conversion cell has WF mean DOWN (the PORT loss-side conversion is significantly negative, CI [-10.9k, -0.07k]); the two IS-positive conversions (B3tick both, B3sec loss) are negative on the WF test months and on the holdout subset -> DEAD. Caveats: no Set A baseline exists for TH, the series are a different book (ST+HM), the "holdout" subset is inside the audit window, x2-cost is not available, placebo is a sign-flip test (equivalent to a one-sided sign test), no per-limit random-control exists.

## Remaining 130 T1 cells (not scored in depth; DEAD from stored rows; selection rule: not (old pass count >= 4 or WF-PRE d mean > 0 and holdout d mean > 0))
| group | WF-PRE mean down (n) | WF-PRE mean up but holdout down (n) | total | reason |
|---|---|---|---|---|
| T1.1 | 9 | 3 | 12 | DEAD: fails WF mean up (WF-PRE) or holdout sign (holdout d mean <= 0); a cell must have both to reach core |
| T1.2 | 41 | 27 | 68 | DEAD: fails WF mean up (WF-PRE) or holdout sign (holdout d mean <= 0); a cell must have both to reach core |
| T1.3 | 8 | 6 | 14 | DEAD: fails WF mean up (WF-PRE) or holdout sign (holdout d mean <= 0); a cell must have both to reach core |
| T1.4 | 26 | 1 | 27 | DEAD: fails WF mean up (WF-PRE) or holdout sign (holdout d mean <= 0); a cell must have both to reach core |
| T1.5 | 1 | 8 | 9 | DEAD: fails WF mean up (WF-PRE) or holdout sign (holdout d mean <= 0); a cell must have both to reach core |

Cell ids: out/NM_D1_rest.json. Each of these has a WF-PRE paired effect smaller than the 80%-power MDE (about $15-25k/wk), so the DEAD label means "failed core sign conditions", not "proven zero": could not have seen an effect below about $17k/wk (about $0.55k/trade).

## Not done / limitations
- Per-trade paired logs for the T1 stream (needs a re-run of t1lib.run per cell to emit tradelog): not done; day-block pairing used instead (power on trade count is the same order since cells remove or alter 100-500 of ~5,100 trades).
- Placebo ranks for T1 cells whose old run did not compute them (mean not up or maxDD worse on WF-PRE: 7 of the 21) were not regenerated (500 signal-stream regenerations per cell exceed the cap); they count as failing placebo >= 0.90. This can only turn a would-be CANDIDATE into DEAD; for the 14 cells with a stored placebo the verdicts are as shown. Cells with no stored placebo all also fail a second core condition (holdout, neighbours) except T14_L_s50_t2.0_n10 and T14_C, which fail the placebo and maxDD only and might be CANDIDATE if their placebo were >= 0.90: flagged, not rescored (T14_C selected by best-of WF-PRE; T14_L_s50_t2.0_n10 maxDD +$232k worse).
- Year-share and 2x-cost are the old STRUCT48 reporting conditions kept as secondary tests in the interim verdict function; V2 section 1 lists neither.

Registration: none (0 PASS, 0 CANDIDATE); paper_all untouched by NM-D.


---

# NM-A re-score (RESEARCH V2): soft half-size switch and C5_m10
Prereg l2vast/struct48/prereg/NM_A.md sha256 20a57b8b3858b30f862d01ebaf6d2fc2b9a5d2fbccd5f9e22e6d3576b974b628 (in DECISIONS.md before scoring). Pre-holdout text prereg/NM_A_PREHOLD.md, holdout look logged as track NM-A. Rows: l2vast/struct48/rows/NM_A.json; code code/nm_a.py (+ nm_lib.py). No new engine run: stored FAILPRED weekly series and STEP2 trades re-read.
Holdout disclosure: the holdout of every cell here was already seen in FAILPRED (soft arm, all 1,080 cells) and FAILPRED STEP2 (C5, hold2.py); this is a re-read, not a blind test. Prereg correction: the C5 MDE written in the prereg (~0.45 pt/trade) was a wrong guess of the trade SD; the realised session-block SE gives the MDE below (~4.9 pt/trade).

## Item 3: STACK-FB soft +5 min theta 0.3 (object = sizing rule, weekly test)
| quantity | value |
|---|---|
| WF delta vs Set A | +8,613 $/wk (WF mean 33,588 vs 24,975), 103 of 142 weeks differ |
| paired weekly CI (10,000 draws) | [+2,219, +15,514] excludes 0 |
| MDE (80% power, WF) | 9,508 $/wk: the predicted effect (5.6k) was below it, effect seen 8.6k also below; a null here could not have seen less than 9.5k/wk |
| weekly SD / maxDD | SD 100,079 vs 104,523 (-4,444); maxDD 381,470 vs 401,293 (-19,824) |
| WF-PRE / HOLD / L8W / IS delta | +10,009 / +6,946 / +11,795 / 0 (no IS flags) |
| placebo rank (500 random half-size switches, same count) | 0.998 on mean; 0.60 on maxDD (the drawdown gain is not distinguishable from random half-size) |
| largest year share | 0.50 (ok) ; 2x cost: not run (soft arm credits no cost refund; not computed) |
| neighbours (fixed in prereg) | theta 0.4 same horizon: -118 ; horizon +10 same theta: -610 -> DISAGREE (also +0: -775) |
| isolation across horizons at theta 0.3 (WF delta, $/wk) | 0:-775 5:+8,613 10:-610 15:+637 20:-3,421 30:+969 45:+2,278 60:-3,289 90:-6,664 120:-4,349; WF mean up in 4 of 10, holdout up in 5 of 10 |
| object criterion (section 3) | met (mean up, SD and maxDD down, CI excludes 0) |
| old verdict | FAILPRED: PASS on its 5 conditions, reported not endorsed (isolated) |
| NEW VERDICT | **DEAD** (strict function). Met: WF mean up, holdout sign, placebo mean 0.998, object criterion, CI excludes 0, year share, maxDD. Failed: neighbours agree (both fixed neighbours negative; a +5 min flag with 286 sessions is a one-horizon spike). It is the single-failure cell: borderline CANDIDATE if the lead reads 'fails one condition' to include the neighbour condition; the register file is NOT written. Decision for the NM lead. |
Other soft cells (h0, h5 t0.4, h10, h15-h120 at 0.3): all DEAD (WF mean down for h0, h10, h20, h60, h90, h120 and theta 0.4; h15, h30, h45 are mean-up but CI includes 0, placebo not run, maxDD worse for h15/h30). The only cell with CI excluding zero other than the primary is h90 and its CI is negative.

## Item 8: C5_m10 opening-range fade inside CHOSEN +60 chop sessions (object = sleeve/strategy)
| cell | trades (pre/WF) | net pts/trade incl $4.84 RT | session-block CI | MDE | WF $/wk | HOLD $/wk | L8W | sleeve Sharpe up | corr | verdict |
|---|---|---|---|---|---|---|---|---|---|---|
| C5_m5 | 146 / 266 | -0.91 | [-4.13, +2.82] | 4.9 pt | -479 | -114 | -2,319 | no | 0.08 | DEAD |
| C5_m10 | 151 / 287 | -0.40 (pts column -0.16; WF-PRE -0.18 before commission, -0.42 after) | [-3.80, +3.07] | 4.9 pt | -225 | -210 | -1,137 | no (Sharpe 0.2341 vs 0.2389) | 0.05 | DEAD |
| C5_m15 | 156 / 296 | -0.56 | [-3.98, +2.92] | 5.0 pt | -324 | -197 | -1,137 | no | 0.04 | DEAD |
C5_m10: old verdict fails mean<=C0, CI, placebo A (0.50), GENERAL, holdout. New: WF mean down, standalone holdout mean negative (-210/wk), sleeve marginal Sharpe down, placebo 0.50 -> DEAD. Met: neighbours agree (all negative), corr <= 0.5 (0.05). Failed: WF mean up, holdout > 0, placebo >= 0.90, marginal Sharpe up. Could not have seen an effect smaller than about 4.9 pt/trade (287 trades, 240 sessions), and the weekly sleeve test could not see less than 2.7k/wk; the point estimate is negative, the CI includes zero in both directions (it is a weak null, not evidence of a large loss). Gross edge is +0.57 pt but cost is about 0.75 pt.

## Registrations
None (no PASS or CANDIDATE in group A). Files: l2vast/struct48/rows/NM_A.json.


---

---
Update 2026-10-24 (after handback): Track 1 V2 re-score by the T1 agent is in l2vast/struct48/rows/T1_v2.json (151 cells, all DEAD, paired arrays in out/T1_paired/). It agrees with NM-D: no T1 PASS or CANDIDATE. Use it as the authoritative T1 verdict source.
