# REPORT STRUCT48 T3.8 (second-system leads: confirmation of the NQ dip-buy sleeves + 20 new ideas)
Preregs: prereg/T3_8A.md sha256 65f8de6958dac1f66b1858ddd91a978fc3df221d762caabe97f554e9e09830b0 (task A, 32 variants, track T3.8A); prereg/T3_8B.md sha256 7fe3e93267fb149261c44f9bbddd3bbd3a220adf912971935da9cd671785c86a (task B, 27 variants, track T3.8B). Ideas I22-I41: rows/T3_8_proposed.json. Code code/t38lib.py, t38cellsA.py, t38cellsB.py, t38run.py, t38trunc.py. Rows rows/T3_8_Aoos.json, T3_8_A_{pre,final}.json, T3_8_B_{pre,final}.json; weekly unit series out/T3_8/*.npz; audits audit/T3_8{A,B}_trunc.json.
Process disclosure: (1) the first run of `t38run.py Aoos` left post-2023 trades in the n/hit/per-year fields (weekly stats were correct); the NQ and COMB per-year totals for 2024-2026 were printed to the log (NQ 2024+ P&L of these two rules was already known from T3.6/T3.7; ES/RTY/YM 2024+ per-year numbers were never printed or inspected). Fixed by restricting trades to the OOS window (t38run.py sha256 changed; superseded file kept as rows/T3_8_Aoos_bug1_superseded.json); the T3.8A holdout is unaffected because the pre-stage / OOS numbers below are from the fixed run. (2) audit script first crashed on a read-only array and was fixed before any audit result existed. No parameter or cell changed.

## PRE-HOLDOUT TEXT (written before the T3.8A and T3.8B holdout stage; WF-PRE 2024-02..2025-06 scoring only; the pre-2024 OOS section does not touch the holdout)
### A(i) NQ pre-2024 out-of-sample (2013-02..2023-12, 1 lot, $14.84 RT, 500 placebos; no Set A)
| cell | trades (/wk) | hit | $/trade | wk mean | wk SD | wk maxDD | CI of mean | 2x wk mean | placebo | max year share | years pos | gates failed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| NQ_RSI2_t10 | 237 (0.42) | 0.586 | 392 | 163 | 1607 | 23772 | [36, 301] | 157 | 0.986 | 0.40 | 8/11 | PASS (o1-o6) |
| NQ_IBS_t20_n1 | 471 (0.83) | 0.561 | 248 | 205 | 2628 | 76944 | [-24, 426] | 193 | 0.946 | 0.64 | 9/11 | o2_ci_excl0,o3_placebo_ge95,o5_year_le60 |
| ES_RSI2_t10 | 237 (0.42) | 0.553 | 212 | 88 | 1410 | 23665 | [-33, 204] | 76 | 0.966 | 0.37 | 9/11 | o2_ci_excl0 |
| ES_IBS_t20_n1 | 443 (0.78) | 0.546 | 131 | 102 | 1659 | 32189 | [-42, 233] | 78 | 0.922 | 0.66 | 8/11 | o2_ci_excl0,o3_placebo_ge95,o5_year_le60 |
| RTY_RSI2_t10 | 172 (0.51) | 0.558 | 118 | 60 | 985 | 10963 | [-46, 157] | 53 | 0.860 | 0.45 | 5/7 | o2_ci_excl0,o3_placebo_ge95 |
| RTY_IBS_t20_n1 | 315 (0.94) | 0.533 | 103 | 97 | 1278 | 10756 | [-44, 227] | 83 | 0.918 | 0.60 | 4/7 | o2_ci_excl0,o3_placebo_ge95,o5_year_le60 |
| YM_RSI2_t10 | 256 (0.45) | 0.543 | 97 | 43 | 1141 | 17628 | [-52, 139] | 37 | 0.782 | 0.34 | 10/11 | o2_ci_excl0,o3_placebo_ge95 |
| YM_IBS_t20_n1 | 433 (0.76) | 0.543 | 104 | 79 | 1215 | 15106 | [-26, 179] | 68 | 0.886 | 0.66 | 8/11 | o2_ci_excl0,o3_placebo_ge95,o5_year_le60 |
| COMB_c3_R | 596 (1.05) | 0.560 | 262 | 695 | 6677 | 199687 | [112, 1235] | 652 | 0.978 | 0.68 | 9/11 | o5_year_le60 |
| COMB_c1_N | 596 (1.05) | 0.560 | 262 | 274 | 2766 | 68747 | [40, 501] | 258 | 0.982 | 0.58 | 9/11 | PASS (o1-o6) |

Per-calendar-year totals (1 lot, $):

| year | NQ_RSI2_t10 | NQ_IBS_t20_n1 | COMB_c3_R |
|---|---|---|---|
| 2013 | 3622 | 5971 | 21846 |
| 2014 | 3013 | 3970 | 12517 |
| 2015 | -4031 | -4688 | -19257 |
| 2016 | -4141 | 6292 | 5928 |
| 2017 | 8623 | 7028 | 30224 |
| 2018 | 9954 | 18432 | 57955 |
| 2019 | -217 | 8456 | 19005 |
| 2020 | 37197 | 75093 | 270760 |
| 2021 | 16458 | 12223 | 36286 |
| 2022 | 2411 | -51630 | -144004 |
| 2023 | 20028 | 35593 | 104628 |

Reading (A(i)): NQ_RSI2_t10 PASSES all six OOS gates on 2013-2023 (weekly mean +$163, CI [36, 301], placebo 0.986, 2x +$157, largest year share 0.40, neighbours t5/t15 +$122/+$264; 8 of 11 years positive; 237 trades, hit 58.6%) - a confirmation on data whose total had been printed before (T3.6/T3.7 extra evidence). NQ_IBS_t20_n1 FAILS o2 (CI [-24, 426]), o3 (placebo 0.946) and o5 (2020 is 64% of the total; 2022 is -$51.6k): +$205/wk, 9 of 11 years positive, neighbours positive. The other markets (information rows, not PASS-bearing for A(i)): ES, RTY, YM all have positive mean, positive 2x and 2x-neighbours for both rules but none has a CI excluding 0 or a placebo >=0.95 (ES RSI2 0.966, CI lower -33); the IBS version fails the 60% year-share on ES/RTY/YM as on NQ (2020). The combined sleeve COMB_c3_R (3 lots, halving rule) earns +$695/wk with CI [112, 1235], placebo 0.978, but 2020 is 68% of the total and 2022 loses $144k (maxDD $200k); the 1-lot unrule COMB_c1_N passes o1-o5 (no neighbours defined).

### A(ii)/(iii) Set A portfolio, WF-PRE (ES/RTY/YM x RSI2_t10/IBS_t20_n1; COMB_c3_R). Pre stage: p4 (holdout) unscored, so max 'pass count' shown excludes it.

| cell | ratio | unit WF-PRE $/wk | d mean | d maxDD % | CI of d | placebo | corr | 2x d | max yr share | L8W d mean | nb agree | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES_RSI2_t10 | 0.25 | 552 | 4116 | 1.4 | [-1228, 9406] | 0.88 | 0.08 | 4024 | 0.66 | 6093 | True | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ES_RSI2_t10 | 0.5 | 552 | 8231 | 2.7 | [-2455, 18812] | 0.88 | 0.08 | 8047 | 0.66 | 12185 | True | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ES_RSI2_t10 | 1.0 | 552 | 16462 | 74.9 | [-4911, 37623] | 0.88 | 0.08 | 16094 | 0.66 | 24371 | True | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ES_IBS_t20_n1 | 0.25 | 234 | 1474 | 0.0 | [-3741, 7149] | 0.57 | -0.05 | 1321 | 0.60 | -2618 | True | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ES_IBS_t20_n1 | 0.5 | 234 | 2947 | 0.1 | [-7483, 14297] | 0.57 | -0.05 | 2642 | 0.60 | -5237 | True | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ES_IBS_t20_n1 | 1.0 | 234 | 5895 | 25.6 | [-14965, 28595] | 0.57 | -0.05 | 5284 | 0.60 | -10474 | True | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| RTY_RSI2_t10 | 0.25 | 169 | 4805 | 2.0 | [-596, 10144] | 0.95 | 0.02 | 4603 | 1.10 | 11817 | True | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| RTY_RSI2_t10 | 0.5 | 169 | 9611 | 30.3 | [-1193, 20289] | 0.95 | 0.02 | 9206 | 1.10 | 23633 | True | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| RTY_RSI2_t10 | 1.0 | 169 | 19221 | 91.8 | [-2385, 40578] | 0.95 | 0.02 | 18412 | 1.10 | 47266 | True | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| RTY_IBS_t20_n1 | 0.25 | 141 | 2090 | 3.1 | [-2980, 7373] | 0.76 | -0.06 | 1920 | 0.95 | -3598 | True | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| RTY_IBS_t20_n1 | 0.5 | 141 | 4179 | 8.6 | [-5961, 14745] | 0.76 | -0.06 | 3839 | 0.95 | -7196 | True | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| RTY_IBS_t20_n1 | 1.0 | 141 | 8358 | 40.4 | [-11921, 29490] | 0.76 | -0.06 | 7678 | 0.95 | -14393 | True | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| YM_RSI2_t10 | 0.25 | 188 | 2170 | 3.5 | [-3393, 7647] | 0.71 | 0.15 | 2063 | 1.38 | 9294 | True | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| YM_RSI2_t10 | 0.5 | 188 | 4340 | 14.2 | [-6787, 15294] | 0.71 | 0.15 | 4125 | 1.38 | 18588 | True | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| YM_RSI2_t10 | 1.0 | 188 | 8681 | 88.1 | [-13574, 30589] | 0.71 | 0.15 | 8250 | 1.38 | 37175 | True | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| YM_IBS_t20_n1 | 0.25 | -65 | -907 | -0.4 | [-6908, 3876] | 0.30 | -0.01 | -1070 | n/a (neg) | -4177 | False | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok,neighbours_agree |
| YM_IBS_t20_n1 | 0.5 | -65 | -1815 | 22.1 | [-13816, 7751] | 0.30 | -0.01 | -2140 | n/a (neg) | -8355 | False | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok,neighbours_agree |
| YM_IBS_t20_n1 | 1.0 | -65 | -3630 | 141.1 | [-27633, 15502] | 0.30 | -0.01 | -4280 | n/a (neg) | -16710 | False | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok,neighbours_agree |
| COMB_c3_R | 0.25 | sized | 2196 | 9.3 | [-1434, 5801] | 0.88 | 0.03 | 2108 | 1.00 | -5120 | True | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| COMB_c3_R | 0.5 | sized | 2196 | 9.3 | [-1434, 5801] | 0.88 | 0.03 | 2108 | 1.00 | -5120 | True | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |

Reading (A pre): no ES/RTY/YM cell, and not the combined sleeve, meets p1 (maxDD down >= 10%): the maxDD change is +0..3% at ratio 0.25 for the RSI2 cells (rising to +30..90% at 0.5-1.0) and +9.3% for COMB_c3_R. Positive-mean cells (ES/RTY/YM RSI2, ES/RTY IBS, COMB) add $1.5k-4.8k/wk to the portfolio at ratio 0.25 but every CI includes 0; RTY_RSI2_t10 placebo 0.95 (borderline), ES_RSI2_t10 0.88. YM_IBS_t20_n1 is negative on WF-PRE (neighbours disagree). COMB's L8W delta is -$5.1k/wk (negative in the last 8 weeks), the RSI2 cells' L8W is positive (+$6-12k at 0.25) and the IBS cells' negative.

### B: new ideas I22/I27/I30/I33/I34, WF-PRE (look-ahead audit 360 cuts, 0 mismatches over 27 variants incl. Set A-gate, VIX and 5 symbols noised; audit/T3_8B_trunc.json. A: 0 mismatches over 32 variants.)
| cell | trades/wk | unit $/wk | nb unit | stand placebo | ratio 0.25: d mean | d maxDD % | CI | port placebo | pass count (of 9; p4 unscored) | 2013-2023 extra: $/wk, years pos |
|---|---|---|---|---|---|---|---|---|---|---|
| XDIP_ZN_t10 | 0.57 | -7 | -17/13 | 0.71 | -648 | 25.4 | [-6305, 4527] | 0.70 | 1 | -54, 3/11 |
| XDIP_6E_t10 | 0.65 | 28 | 89/54 | 0.67 | 1739 | 19.7 | [-4039, 7677] | 0.74 | 4 | -103, 1/11 |
| XDIP_6J_t10 | 0.80 | -8 | -14/47 | 0.56 | -399 | 39.3 | [-6305, 4727] | 0.55 | 1 | -214, 4/11 |
| XDIP_GC_t10 | 0.31 | 91 | 158/137 | 0.57 | 1768 | 0.0 | [-3931, 7303] | 0.61 | 4 | -39, 4/11 |
| XDIP_CL_t10 | 0.52 | 22 | 70/1 | 0.64 | 733 | 7.8 | [-4999, 6176] | 0.66 | 4 | -50, 7/11 |
| GSHORT_t90 | 0.29 | 112 | 106/-41 | 0.70 | 1464 | 19.5 | [-4345, 6452] | 0.74 | 3 | n/a (needs Set A) |
| VTB_1.0 | 0.67 | -266 | -276/27 | 0.19 | -972 | 3.8 | [-7144, 4051] | 0.24 | 1 | 276, 8/11 |
| BRK_960_1080 | 3.67 | 361 | 153/240 | 0.97 | 4966 | 1.0 | [-767, 10771] | 0.98 | 6 | 30, 4/11 |
| AFR_720 | 4.67 | -1085 | -1061/-298 | 0.09 | -3063 | 10.9 | [-9482, 1717] | 0.15 | 2 | -348, 2/11 |

Reading (B pre): none meets p1 together with p2. BRK (16:00-18:00 session-break drift, long NQ) is the only positive-looking idea: unit +$361/wk at 3.7 trades/wk, standalone placebo 0.97, portfolio placebo 0.98, neighbours positive (+153/+240), corr 0.09, 2x delta positive, maxDD +1.0% at 0.25, CI [-767, 10,771] includes 0; its 2013-2023 history is only +$30/wk with 4 of 11 years positive. XDIP: 6E and GC and CL have small positive unit means (+28/+91/+22) but ZN and 6J are negative (neighbours disagree), CIs include 0 and placebos are 0.56-0.74; CL's gain is >100% attributable to one year. GSHORT (Set A-regime short): +$112/wk unit, 0.29 trades/wk (n tiny), maxDD +19.5% at 0.25, neighbours disagree (thr 95 negative). VTB (VIX backwardation long): unit -$266/wk (placebo 0.19) although +$276/wk with 8/11 years positive on 2013-2023 - the sign flips between the periods. AFR (afternoon reversal) is reliably wrong-way: -$1,085/wk, placebo 0.09 (the morning move CONTINUES; the reverse rule was not preregistered and is not scored). Per protocol the holdout is now scored once for the batches T3.8A and T3.8B.

## FINAL (holdout 2025-07+ scored once per track: T3.8A and T3.8B; WF = 2024-02+, 142 weeks; rows/T3_8_A_final.json, rows/T3_8_B_final.json)
**Verdict: 0 of 8 task-A cells and 0 of 9 task-B cells PASS; every task-A and task-B near miss fails ONLY or mainly p1 (portfolio maxDD down >= 10%).** Ledger: 59 variants appended (cumulative corrected total 28,458).

### Task A
| cell (ratio 0.25 unless noted) | unit WF $/wk (HOLD) | d mean | d maxDD % | CI of d | port placebo | L8W d mean | pass | failed |
|---|---|---|---|---|---|---|---|---|
| ES_RSI2_t10 | 653 (754) | +6,279 | +1.7 | [1,779, 11,051] | 0.99 | +7,860 | 8/9 | p1 |
| ES_IBS_t20_n1 | 385 (546) | +3,160 | 0.0 | [-793, 7,774] | 0.83 | -3,417 | 6/9 | p1, p5, p6 |
| RTY_RSI2_t10 | 331 (505) | +8,005 | +1.7 | [4,181, 12,492] | 1.00 | +10,044 | 8/9 | p1 |
| RTY_IBS_t20_n1 | 220 (305) | +3,618 | +3.4 | [-198, 8,091] | 0.92 | -3,988 | 6/9 | p1, p5, p6 |
| YM_RSI2_t10 | 287 (392) | +4,137 | +4.4 | [-44, 8,661] | 0.94 | +11,600 | 5/9 | p1, p5, p6, year share 0.70 |
| YM_IBS_t20_n1 | 175 (437) | +2,733 | -0.4 | [-1,307, 6,794] | 0.83 | -4,690 | 5/9 | p1, p5, p6, year share 0.86 |
| COMB_c3_R (ratios 0.25 and 0.5 identical: cap binds, realised SD ratio 0.16) | 1,235 (1,163) | +2,831 | +9.3 | [307, 5,812] | 0.96 | -5,120 | 8/9 | p1 |
Detail:
- (i) NQ 2013-2023: NQ_RSI2_t10 PASSES all six OOS gates (see pre-holdout section; wk mean +$163, CI [36, 301], placebo 0.986, 8/11 years positive, no year > 40%); NQ_IBS_t20_n1 fails o2/o3/o5 (CI [-24, 426], placebo 0.946, 2020 = 64% of total, 2022 = -$51.6k). Caveat: the NQ totals for these rules over 2013-2023 had been printed in T3.7, so this is a confirmation, not a blind test. The strong years are 2020 (RSI2 +$37k, IBS +$75k) and 2023; 2015-16 and 2019 are flat or negative for RSI2, 2015 and 2022 negative for IBS.
- (ii) ES/RTY/YM (genuine OOS markets, never scored before): RSI2_t10 is positive on all three on 2013-2023, WF-PRE and HOLD standalone; on the Set A harness ES_RSI2_t10 and RTY_RSI2_t10 are 8/9: CI excludes 0 (ES [1,779, 11,051], RTY [4,181, 12,492]), placebo 0.99 / 1.00, 2x positive, neighbours agree, corr 0.09 / 0.07, largest year share 0.45 / 0.53, holdout standalone positive; they add $6.3k / $8.0k per week at ratio 0.25 (Set A $24,975) and L8W +$7.9k / +$10.0k. They fail only p1: portfolio maxDD +1.7% at 0.25, +18.5% / +21.1% at 0.5 and +122% / +73% at 1.0. YM RSI2 has a CI touching 0 ([-44, 8,661]), placebo 0.94 and 2025 70% of the gain. All three IBS cells are 5-6/9 (CI includes 0, placebos 0.83-0.92). So the RSI2 dip-buy generalises across ES and RTY and the IBS version does not independently confirm.
- (iii) Combined sleeve COMB_c3_R: standalone 1 lot +$1,235/wk WF (HOLD +$1,163), 0.98 trades/wk; portfolio at 0.25/0.5 (3 lots, realised SD ratio 0.16): WF mean $27,807 vs $24,975 (+$2,831, CI [307, 5,812], placebo 0.96, 2x +$2,767, neighbours c2/c1 same sign: +1,888/+944), maxDD $438,639 vs $401,293 (+9.3%; the sizing rule did not help: without the rule COMB_c3_N is +$3,706 and +5.7%), worst week -$169,976 vs -$137,081, SD 104,566 vs 104,523. Portfolio L8W: mean $29,071 vs Set A $34,191 (delta -$5,120/wk; the sleeve lost money in the last 8 weeks: 1-lot L8W -$1,502/wk), L8W maxDD +$112. Variants: c2_R +1,888 / +6.2%, c1_R +944 / +3.1%, c3_N +3,706 / +5.7%, s5_c3_R +1,723 / +0.2%, s15_c3_R +4,405 / +3.9%. The trailing-8w halving rule reduces the mean more than it reduces the maxDD (maxDD change +9.3% with the rule vs +5.7% without at cap 3 -> the rule is WORSE on maxDD here, because the sleeve's own losses arrive when its trailing 8 weeks are still positive). Limitation: with cap 3 the ratio rows coincide, so a genuine 0.25x/0.5x overlay of the full uncapped sleeve is the (ii) RSI2 rows.

### Task B (top 5 of I22-I41)
| cell | unit WF $/wk (HOLD) | d mean @0.25 | d maxDD % | CI | port placebo | pass | failed |
|---|---|---|---|---|---|---|---|
| BRK_960_1080 (I33) | 400 (438) | +4,853 | -2.1 | [592, 9,054] | 0.99 | 8/9 | p1 only |
| GSHORT_t90 (I27) | 162 (215) | +2,970 | +28.9 | [-1,498, 7,377] | 0.96 | 7/9 | p1, p5 |
| XDIP_CL_t10 (I22) | 36 (51) | +1,137 | +7.5 | [-3,030, 5,328] | 0.65 | 5/9 | p1, p5, p6, year (117%) |
| VTB_1.0 (I30) | 114 (532) | +528 | +4.8 | [-3,792, 5,003] | 0.46 | 5/9 | p1, p5, p6, year (171%) |
| XDIP_6J_t10 | 9 (28) | +596 | +47.3 | [-3,942, 5,013] | 0.89 | 4/9 | p1, p5, p6, x2, year |
| XDIP_ZN_t10 | 2 (12) | +246 | +31.6 | [-3,910, 4,528] | 0.94 | 3/9 | p1, p5, p6, x2, year, neighbours |
| XDIP_GC_t10 | -276 (-676) | -2,257 | +36.0 | [-7,089, 1,516] | 0.07 | 2/9 | p1, p2, p4, p5, p6, x2, year |
| AFR_720 (I34) | -818 (-511) | -2,807 | +13.2 | [-7,281, 1,221] | 0.14 | 2/9 | p1, p2, p4, p5, p6, x2, year |
| XDIP_6E_t10 | -13 (-57) | -806 | +20.2 | [-4,862, 3,423] | 0.53 | 1/9 | p1, p2, p4, p5, p6, x2, year, neighbours |
- BRK (long NQ 16:00 -> 18:00 ET, spanning the 17:00-18:00 halt) is the most interesting new lead of the whole T3 programme: WF +$400/wk unit (3.8 trades/wk, $14.84 RT), WF-PRE +$361 and HOLD +$438 (consistent), neighbours +$399 / +$151, corr 0.00, standalone placebo 0.99, portfolio CI excludes 0 at all ratios, 2x positive (+$4,174), no year > 46%, maxDD -2.1% at 0.25 (+21% at 0.5), L8W d mean +$6,190 with L8W maxDD delta -$25.8k at 0.25, holdout d mean positive. It fails p1 (maxDD not down >= 10%), DSR 0.08. Warning signs: on 2013-2023 (pre-window, not scored) it earned only +$30/wk with 4 of 11 years positive (2019 -$9.3k, 2020 +$15.7k, 2021 +$12.6k), so the recent edge is not long-lived; post-halt gap/thin-book fills are modelled at 1 tick/side only. Treat as a LEAD to be re-tested on a longer or independent window and with realistic halt-period slippage.
- GSHORT (short RSI2>90 only when Set A's trailing 4 weeks are negative): +$162/wk on 0.22 trades/wk (31 trades in the 142 WF weeks); placebo 0.96 but maxDD +28.9% at 0.25 - it does not hedge Set A drawdowns (L8W delta +$2.5k) and the CI includes 0.
- XDIP cross-asset dip-buy: only CL has a positive mean (+$36/wk, one year dominates); ZN/6J ~0, GC and 6E negative on the holdout. The equity-index RSI2 edge does NOT transfer to rates, FX or metals. VTB: holdout +$532 vs WF-PRE -$266 (sign flip); AFR: reliably wrong-way (continuation, not reversal).
Truncation audits: A 0 mismatches / 360 cuts over 32 variants; B 0 mismatches / 360 cuts over 27 variants (5 symbols, VIX, Set A gate noised).

## SUMMARY (T3.8)
- Task A: RSI2_t10 is independently supported: NQ 2013-2023 OOS passes all six gates, and on never-scored ES and RTY it is 8/9 on the Set A harness (CI excludes 0, placebo >= 0.99, holdout positive, corr < 0.1) failing ONLY p1 (maxDD +1.7% at 0.25). IBS_t20_n1 fails OOS (CI, placebo 0.946, year share) and on ES/RTY/YM. The combined 3-lot sleeve with the trailing-8w halving rule is 8/9 (p1 +9.3%) and does not cut the drawdown; the portfolio L8W is -$5,120/wk vs Set A. No cell is a CONFIRMED second system because p1 (maxDD down >= 10%) fails for every sleeve at every ratio.
- Task B: 0/9 PASS; best BRK (session-break drift) 8/9 failing only p1 with a short, unstable history (4/11 years positive pre-2023); the cross-asset dip-buy ideas do not transfer.
- Most frequently failed: p1 (all 17 cells), p5/p6 for the IBS and cross-asset cells, year share for YM and cross-asset, p2/p4 for GC, 6E, AFR.
- Leads (all fail p1): RTY_RSI2_t10 and ES_RSI2_t10 (8/9; same RSI2 dip-buy edge, mean-adders; combined with NQ RSI2 they are one correlated dip-buy exposure), BRK_960_1080 (8/9; independent of dip-buy by construction, corr 0.00 to Set A), COMB_c3_R (8/9).
- Caveats: 1-min conservative fills; proxy costs; ZN tick cost heavy ($36.09 RT); BRK halt-period slippage; Aoos first run bug (disclosed above); the COMB rule uses 1-lot trailing P&L (exits before the entry date).
- Files: rows/T3_8_Aoos.json, T3_8_A_{pre,final}.json, T3_8_B_{pre,final}.json, T3_8_proposed.json; out/T3_8/*.npz; audit/T3_8{A,B}_trunc.json; prereg/T3_8A.md, T3_8B.md; code/t38*.py.
