# REPORT STRUCT48 T3.7 (second-system ideas, continuation of T3.6: batches 3 and 4 + RSI2 combo family) - DONE
Ideas I11-I20 and the I21 replacement: rows/T3_7_proposed.json (copy of T3_6_proposed.json with updated status). Preregs: prereg/T3_6b3.md sha256 387bbca2363455ad187f0191de1062acb3b705e6701f963d54d1b46c51715b1a; prereg/T3_6b4.md 69f06628f8e40637208c5ac0037b3bdf1fb7df0b12702d6deffe0a80fcd9e39a; prereg/T3_7_rsi2c.md d9f65121e4f1e300dc37fec32fd8e575db4df1cbeab32286ac4088fdbbb303b8. Code code/t37lib.py, t37cells{3,4,4r}.py, t37run.py (copy of t36run.py), t37trunc.py. Rows rows/T3_7_b{3,4,4r}_{pre,final}.json, weekly unit series out/T3_7/, audits audit/T3_7b*_trunc.json.

## BATCH 3 PRE-HOLDOUT TEXT (ideas I11-I15; WF-PRE 2024-02..2025-06 scoring only; written before the batch-3 holdout stage)
Look-ahead audit: 360 cuts (NQ and RTY replaced by noise after the cut), 0 mismatches over 29 variants (SPR2, OPXA, OPXC, LON, WKND, TUEREV, GAPS). Caveat: rows spanning a contract roll are dropped, so since ~2020 the quarterly-OPEX weeks (roll falls inside) are excluded from I12 (22 OPXA trades in WF, 29 OPXC). Reading: no primary variant meets p1 (maxDD down >=10%) together with p2 (mean not down) at any ratio. NQ/RTY spread, OPEX-long, OPEX-fade, weekend-carry and Sunday-gap fade have negative or ~0 unit means (GAPS standalone placebo 0.00/0.01, i.e. the gap-fade direction is reliably WRONG: continuation, not fill); TUEREV +11/wk with 6.6x year share. Only the London-continuation cells have positive means: LONB_x565 unit +505/wk, port placebo 0.88, CI includes 0, maxDD +6.7% at 0.25; LONA_x565 +290/wk, maxDD -7.5% at 0.25 but placebo 0.73, CI includes 0. Per protocol the holdout is now scored once for all 10 batch-3 primaries.

| cell | trades/wk | unit mean/wk (window) | corr SetA | stand placebo | nb agree | ratio | port dMean | dMaxDD % | CI | port placebo | x2 | yr max | pass of 9 | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| RTYS_w20_z15 | 1.15 | -257 | -0.11 | 0.39 | N | 0.25 | -942 | 5.8 | [-6530,4276] | 0.48 | -1238 | None | 1 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok,neighbours_agree |
| RTYS_w20_z15 | 1.15 | -257 | -0.11 | 0.39 | N | 0.5 | -1883 | 33.3 | [-13060,8552] | 0.48 | -2476 | None | 1 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok,neighbours_agree |
| RTYS_w20_z15 | 1.15 | -257 | -0.11 | 0.39 | N | 1.0 | -3767 | 95.8 | [-26120,17104] | 0.48 | -4951 | None | 1 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok,neighbours_agree |
| RTYS_w20_z20 | 0.39 | -60 | -0.12 | 0.51 | N | 0.25 | -492 | -1.5 | [-6146,4279] | 0.53 | -715 | None | 1 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok,neighbours_agree |
| RTYS_w20_z20 | 0.39 | -60 | -0.12 | 0.51 | N | 0.5 | -983 | 40.7 | [-12292,8558] | 0.53 | -1431 | None | 1 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok,neighbours_agree |
| RTYS_w20_z20 | 0.39 | -60 | -0.12 | 0.51 | N | 1.0 | -1966 | 172.9 | [-24583,17115] | 0.53 | -2862 | None | 1 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok,neighbours_agree |
| OPXA_thu | 0.15 | -210 | -0.05 | 0.17 | Y | 0.25 | -1185 | 22.2 | [-6438,4502] | 0.20 | -1197 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| OPXA_thu | 0.15 | -210 | -0.05 | 0.17 | Y | 0.5 | -2369 | 44.5 | [-12875,9003] | 0.20 | -2394 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| OPXA_thu | 0.15 | -210 | -0.05 | 0.17 | Y | 1.0 | -4739 | 88.9 | [-25750,18006] | 0.20 | -4788 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| OPXC_x959 | 0.20 | -176 | 0.13 | 0.36 | Y | 0.25 | -2730 | 10.1 | [-7959,2266] | 0.33 | -2776 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| OPXC_x959 | 0.20 | -176 | 0.13 | 0.36 | Y | 0.5 | -5459 | 30.1 | [-15918,4532] | 0.33 | -5551 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| OPXC_x959 | 0.20 | -176 | 0.13 | 0.36 | Y | 1.0 | -10919 | 111.3 | [-31836,9063] | 0.33 | -11103 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| LONA_x565 | 4.85 | 290 | 0.04 | 0.72 | Y | 0.25 | 1652 | -7.5 | [-3793,6740] | 0.73 | 1241 | 0.55 | 5 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95 |
| LONA_x565 | 4.85 | 290 | 0.04 | 0.72 | Y | 0.5 | 3303 | 5.4 | [-7587,13480] | 0.73 | 2483 | 0.55 | 5 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95 |
| LONA_x565 | 4.85 | 290 | 0.04 | 0.72 | Y | 1.0 | 6606 | 39.4 | [-15174,26961] | 0.73 | 4966 | 0.55 | 5 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95 |
| LONB_x565 | 4.84 | 505 | -0.02 | 0.83 | Y | 0.25 | 3291 | 6.7 | [-2309,8582] | 0.88 | 2824 | 0.68 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| LONB_x565 | 4.84 | 505 | -0.02 | 0.83 | Y | 0.5 | 6583 | 13.5 | [-4617,17165] | 0.88 | 5647 | 0.68 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| LONB_x565 | 4.84 | 505 | -0.02 | 0.83 | Y | 1.0 | 13166 | 58.3 | [-9235,34329] | 0.88 | 11294 | 0.68 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| WKND_E955 | 0.95 | -33 | 0.14 | 0.26 | N | 0.25 | -170 | 7.2 | [-6282,5111] | 0.26 | -242 | None | 1 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok,neighbours_agree |
| WKND_E955 | 0.95 | -33 | 0.14 | 0.26 | N | 0.5 | -340 | 32.1 | [-12564,10223] | 0.26 | -484 | None | 1 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok,neighbours_agree |
| WKND_E955 | 0.95 | -33 | 0.14 | 0.26 | N | 1.0 | -680 | 81.7 | [-25129,20445] | 0.26 | -968 | None | 1 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok,neighbours_agree |
| TUEREV_E570 | 0.88 | 11 | -0.11 | 0.52 | Y | 0.25 | 73 | 7.0 | [-4987,5634] | 0.52 | -11 | 6.61 | 3 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| TUEREV_E570 | 0.88 | 11 | -0.11 | 0.52 | Y | 0.5 | 146 | 14.0 | [-9974,11268] | 0.52 | -22 | 6.61 | 3 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| TUEREV_E570 | 0.88 | 11 | -0.11 | 0.52 | Y | 1.0 | 292 | 49.9 | [-19949,22536] | 0.52 | -44 | 6.61 | 3 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| GAPS_t2_x570 | 0.33 | -649 | 0.12 | 0.00 | Y | 0.25 | -5326 | 14.1 | [-11757,-581] | 0.04 | -5366 | None | 3 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p6_placebo_ge95,x2_ok,year_ok |
| GAPS_t2_x570 | 0.33 | -649 | 0.12 | 0.00 | Y | 0.5 | -10651 | 45.8 | [-23514,-1161] | 0.04 | -10732 | None | 3 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p6_placebo_ge95,x2_ok,year_ok |
| GAPS_t2_x570 | 0.33 | -649 | 0.12 | 0.00 | Y | 1.0 | -21302 | 144.9 | [-47028,-2323] | 0.04 | -21465 | None | 3 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p6_placebo_ge95,x2_ok,year_ok |
| GAPS_t4_x570 | 0.17 | -379 | 0.14 | 0.01 | Y | 0.25 | -3228 | 15.3 | [-9489,1433] | 0.08 | -3250 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| GAPS_t4_x570 | 0.17 | -379 | 0.14 | 0.01 | Y | 0.5 | -6456 | 48.2 | [-18977,2866] | 0.08 | -6499 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| GAPS_t4_x570 | 0.17 | -379 | 0.14 | 0.01 | Y | 1.0 | -12911 | 114.0 | [-37954,5732] | 0.08 | -12999 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |

## BATCH 4 PRE-HOLDOUT TEXT (I16 ZN->NQ, I18 COT, I19 CL EIA, I20 NR7, I21 IBS replacing unfit I17; prereg prereg/T3_6b4.md sha256 69f06628f8e40637208c5ac0037b3bdf1fb7df0b12702d6deffe0a80fcd9e39a; WF-PRE only; written before the batch-4 holdout stage)
I17 not scored: VX term file starts 2022-04 and is sparse, VX is not in the 1-min tape, so no executable series; the ranked list is exhausted after I20, so the replacement I21 (IBS reversal) is a new idea added post hoc (disclosed in prereg and rows/T3_7_proposed.json).
Look-ahead audit: 360 cuts (NQ, ZN and CL replaced by noise after the cut), 0 mismatches over 26 variants. Reading: no primary variant meets p1 (maxDD down >=10%) together with p2 (mean not down) at any ratio. Positive-mean cells: ZNP_h60 (+539/wk, placebo 0.85 but yr share 0.90 and maxDD +15%), IBS_t20_n1 (+728/wk, port placebo 0.71, maxDD +4.5%), IBS_t20_n2 (+355/wk, maxDD -6.8% @0.25, placebo 0.57), EIA_h60 (+58/wk, stand placebo 0.96, port placebo 0.94, maxDD -1.2% @0.25, neighbour EIA_h30 sibling pair disagree for h30 primary), COT_p10 (+282/wk, maxDD -7.3% @0.25, placebo 0.49), COT_p20, NR7_x955. ZNN (against the ZN move) is negative (the P/N pair are mirror images, so one is positive by construction); NR7_x720 negative.

| cell | trades/wk | unit mean/wk (window) | corr SetA | stand placebo | nb agree | ratio | port dMean | dMaxDD % | CI | port placebo | x2 | yr max | pass of 9 | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ZNP_h60 | 4.57 | 539 | 0.08 | 0.85 | Y | 0.25 | 2942 | 15.1 | [-2885,8665] | 0.86 | 2572 | 0.9 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ZNP_h60 | 4.57 | 539 | 0.08 | 0.85 | Y | 0.5 | 5884 | 30.2 | [-5770,17329] | 0.86 | 5144 | 0.9 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ZNP_h60 | 4.57 | 539 | 0.08 | 0.85 | Y | 1.0 | 11769 | 76.1 | [-11541,34658] | 0.86 | 10287 | 0.9 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ZNN_h60 | 4.57 | -675 | -0.08 | 0.13 | Y | 0.25 | -3680 | -10.0 | [-9407,2139] | 0.11 | -4050 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| ZNN_h60 | 4.57 | -675 | -0.08 | 0.13 | Y | 0.5 | -7361 | -0.3 | [-18815,4277] | 0.11 | -8101 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| ZNN_h60 | 4.57 | -675 | -0.08 | 0.13 | Y | 1.0 | -14721 | 82.7 | [-37630,8554] | 0.11 | -16202 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| COT_p10 | 0.32 | 282 | 0.10 | 0.46 | Y | 0.25 | 1045 | -7.3 | [-4298,6473] | 0.49 | 1027 | 1.68 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| COT_p10 | 0.32 | 282 | 0.10 | 0.46 | Y | 0.5 | 2090 | 27.4 | [-8596,12946] | 0.49 | 2055 | 1.68 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| COT_p10 | 0.32 | 282 | 0.10 | 0.46 | Y | 1.0 | 4180 | 96.8 | [-17192,25891] | 0.49 | 4109 | 1.68 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| COT_p20 | 0.56 | 153 | 0.08 | 0.38 | Y | 0.25 | 467 | 8.0 | [-5197,5527] | 0.39 | 442 | 1.33 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| COT_p20 | 0.56 | 153 | 0.08 | 0.38 | Y | 0.5 | 934 | 16.0 | [-10394,11053] | 0.39 | 883 | 1.33 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| COT_p20 | 0.56 | 153 | 0.08 | 0.38 | Y | 1.0 | 1868 | 72.7 | [-20788,22107] | 0.39 | 1767 | 1.33 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| EIA_h30 | 0.95 | -44 | -0.12 | 0.26 | N | 0.25 | -2698 | 5.5 | [-7969,2999] | 0.38 | -4130 | None | 1 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok,neighbours_agree |
| EIA_h30 | 0.95 | -44 | -0.12 | 0.26 | N | 0.5 | -5397 | 20.7 | [-15938,5997] | 0.38 | -8261 | None | 1 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok,neighbours_agree |
| EIA_h30 | 0.95 | -44 | -0.12 | 0.26 | N | 1.0 | -10794 | 55.7 | [-31876,11995] | 0.38 | -16522 | None | 1 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok,neighbours_agree |
| EIA_h60 | 0.95 | 58 | -0.15 | 0.96 | Y | 0.25 | 2896 | -1.2 | [-2391,8588] | 0.94 | 1718 | 1.1 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| EIA_h60 | 0.95 | 58 | -0.15 | 0.96 | Y | 0.5 | 5791 | 7.3 | [-4781,17175] | 0.94 | 3436 | 1.1 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| EIA_h60 | 0.95 | 58 | -0.15 | 0.96 | Y | 1.0 | 11583 | 60.4 | [-9562,34351] | 0.94 | 6872 | 1.1 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| NR7_x955 | 0.67 | 173 | -0.05 | 0.69 | N | 0.25 | 1515 | -5.3 | [-3778,6861] | 0.71 | 1428 | 2.62 | 3 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok,neighbours_agree |
| NR7_x955 | 0.67 | 173 | -0.05 | 0.69 | N | 0.5 | 3029 | 48.7 | [-7557,13723] | 0.71 | 2856 | 2.62 | 3 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok,neighbours_agree |
| NR7_x955 | 0.67 | 173 | -0.05 | 0.69 | N | 1.0 | 6058 | 159.4 | [-15114,27445] | 0.71 | 5713 | 2.62 | 3 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok,neighbours_agree |
| NR7_x720 | 0.72 | -93 | 0.04 | 0.39 | N | 0.25 | -1173 | 8.2 | [-6935,4690] | 0.37 | -1308 | None | 1 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok,neighbours_agree |
| NR7_x720 | 0.72 | -93 | 0.04 | 0.39 | N | 0.5 | -2347 | 35.8 | [-13870,9381] | 0.37 | -2615 | None | 1 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok,neighbours_agree |
| NR7_x720 | 0.72 | -93 | 0.04 | 0.39 | N | 1.0 | -4693 | 133.4 | [-27740,18761] | 0.37 | -5230 | None | 1 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok,neighbours_agree |
| IBS_t20_n1 | 0.80 | 728 | -0.04 | 0.82 | Y | 0.25 | 2596 | 4.5 | [-2461,8369] | 0.71 | 2554 | 0.82 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| IBS_t20_n1 | 0.80 | 728 | -0.04 | 0.82 | Y | 0.5 | 5192 | 9.1 | [-4922,16737] | 0.71 | 5107 | 0.82 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| IBS_t20_n1 | 0.80 | 728 | -0.04 | 0.82 | Y | 1.0 | 10384 | 18.1 | [-9844,33474] | 0.71 | 10215 | 0.82 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| IBS_t20_n2 | 0.80 | 355 | -0.09 | 0.55 | Y | 0.25 | 1536 | -6.8 | [-3963,6737] | 0.57 | 1485 | 0.59 | 5 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95 |
| IBS_t20_n2 | 0.80 | 355 | -0.09 | 0.55 | Y | 0.5 | 3072 | 11.6 | [-7927,13473] | 0.57 | 2969 | 0.59 | 5 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95 |
| IBS_t20_n2 | 0.80 | 355 | -0.09 | 0.55 | Y | 1.0 | 6143 | 98.8 | [-15853,26946] | 0.57 | 5938 | 0.59 | 5 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95 |

## RSI2 COMBO FAMILY PRE-HOLDOUT TEXT (prereg prereg/T3_7_rsi2c.md sha256 d9f65121e4f1e300dc37fec32fd8e575db4df1cbeab32286ac4088fdbbb303b8; separate family, own holdout look; WF-PRE only)
Look-ahead audit: 360 cuts (signal, eligibility and the ATR stop distance), 0 mismatches over 6 variants. In WF-PRE the stop cell RSI2C_s20 (stop 2.0 x ATR14, ~13 of 312 signals in 2013-26 stop out) has unit mean +704/wk (plain RSI2_t10 +921; stops 1.5 / 2.5 give +836 / +921) and portfolio maxDD +3.2% / +57.6% / +195.6% at ratios 0.25 / 0.5 / 1.0 (worse than plain RSI2_t10 at 0.25 +2.3%): the stop does not cut the drawdown. With the 3-lot cap the multiplier is min(k,3) at every ratio (k_ratio = 6.2 / 12.3 / 24.7 lots, cap binds everywhere, realised SD ratio 0.12): portfolio maxDD +1.6%, dMean +2,112/wk, CI [-365, 4,726] includes 0, placebo 0.92. p1 (maxDD down >=10%) fails in both cells at every ratio.

| cell | trades/wk | unit mean/wk (window) | corr SetA | stand placebo | nb agree | ratio | port dMean | dMaxDD % | CI | port placebo | x2 | yr max | pass of 9 | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| RSI2C_s20 | 0.47 | 704 | 0.04 | 0.91 | Y | 0.25 | 4341 | 3.2 | [-751,9714] | 0.91 | 4299 | 0.52 | 5 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95 |
| RSI2C_s20 | 0.47 | 704 | 0.04 | 0.91 | Y | 0.5 | 8683 | 57.6 | [-1503,19428] | 0.91 | 8597 | 0.52 | 5 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95 |
| RSI2C_s20 | 0.47 | 704 | 0.04 | 0.91 | Y | 1.0 | 17366 | 195.6 | [-3005,38856] | 0.91 | 17195 | 0.52 | 5 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95 |
| RSI2CC_s20 | 0.47 | 704 | 0.04 | 0.92 | Y | 0.25 | 2112 | 1.6 | [-365,4726] | 0.92 | 2091 | 0.52 | 5 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95 |
| RSI2CC_s20 | 0.47 | 704 | 0.04 | 0.92 | Y | 0.5 | 2112 | 1.6 | [-365,4726] | 0.92 | 2091 | 0.52 | 5 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95 |
| RSI2CC_s20 | 0.47 | 704 | 0.04 | 0.92 | Y | 1.0 | 2112 | 1.6 | [-365,4726] | 0.92 | 2091 | 0.52 | 5 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95 |

## BATCH 3 FINAL (WF 2024-02+, holdout 2025-07+ scored once, ledger track T3.7b3)
0/10 primary cells PASS (rows/T3_7_b3_final.json; 29 variants counted). No cell passes p1 (portfolio maxDD down >=10%), p5 (CI excludes 0) or p6 (placebo >=0.95) simultaneously with p2; all 10 fail p1, p5 and p6. Holdout unit means (1 lot, per week): RTYS -481/-480, OPXA -273, OPXC -63, LONA -662, LONB -668 (the pre-holdout London-continuation lead reversed), WKND_E955 +989 (WF +456, port placebo 0.66, CI [-1697, 7170], maxDD +10.5%, 5/9), TUEREV +58, GAPS_t2 +412 / GAPS_t4 +47 (WF negative). Best by pass count: WKND_E955 and TUEREV_E570 5/9; GAPS 3/9; the rest 1-2/9. Truncation audit: 0 mismatches / 360 cuts.

| cell | trades/wk | unit mean/wk (window) | corr SetA | stand placebo | nb agree | ratio | port dMean | dMaxDD % | CI | port placebo | x2 | yr max | pass of 9 | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| RTYS_w20_z15 | 1.27 | -366 | -0.17 | 0.27 | N | 0.25 | -1521 | 9.5 | [-5595,3134] | 0.35 | -1903 | None | 1 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok,neighbours_agree |
| RTYS_w20_z15 | 1.27 | -366 | -0.17 | 0.27 | N | 0.5 | -3042 | 40.7 | [-11191,6269] | 0.35 | -3807 | None | 1 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok,neighbours_agree |
| RTYS_w20_z15 | 1.27 | -366 | -0.17 | 0.27 | N | 1.0 | -6084 | 122.6 | [-22381,12538] | 0.35 | -7614 | None | 1 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok,neighbours_agree |
| RTYS_w20_z20 | 0.48 | -262 | -0.22 | 0.21 | Y | 0.25 | -2052 | -2.0 | [-6743,1760] | 0.25 | -2324 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| RTYS_w20_z20 | 0.48 | -262 | -0.22 | 0.21 | Y | 0.5 | -4104 | 35.8 | [-13486,3520] | 0.25 | -4648 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| RTYS_w20_z20 | 0.48 | -262 | -0.22 | 0.21 | Y | 1.0 | -8207 | 160.3 | [-26973,7040] | 0.25 | -9297 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| OPXA_thu | 0.15 | -242 | -0.03 | 0.09 | Y | 0.25 | -1326 | 21.6 | [-5475,2886] | 0.11 | -1338 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| OPXA_thu | 0.15 | -242 | -0.03 | 0.09 | Y | 0.5 | -2651 | 43.3 | [-10950,5772] | 0.11 | -2676 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| OPXA_thu | 0.15 | -242 | -0.03 | 0.09 | Y | 1.0 | -5302 | 86.6 | [-21900,11545] | 0.11 | -5353 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| OPXC_x959 | 0.20 | -123 | -0.05 | 0.63 | Y | 0.25 | -1701 | 8.0 | [-6161,2613] | 0.64 | -1743 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| OPXC_x959 | 0.20 | -123 | -0.05 | 0.63 | Y | 0.5 | -3401 | 27.5 | [-12321,5226] | 0.64 | -3485 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| OPXC_x959 | 0.20 | -123 | -0.05 | 0.63 | Y | 1.0 | -6802 | 218.4 | [-24642,10451] | 0.64 | -6970 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| LONA_x565 | 4.92 | -164 | -0.02 | 0.42 | Y | 0.25 | -831 | -7.1 | [-4911,3522] | 0.42 | -1201 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| LONA_x565 | 4.92 | -164 | -0.02 | 0.42 | Y | 0.5 | -1661 | 18.9 | [-9821,7043] | 0.42 | -2401 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| LONA_x565 | 4.92 | -164 | -0.02 | 0.42 | Y | 1.0 | -3322 | 169.8 | [-19643,14087] | 0.42 | -4802 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| LONB_x565 | 4.92 | -53 | -0.04 | 0.55 | Y | 0.25 | -281 | 5.5 | [-4721,3844] | 0.55 | -669 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| LONB_x565 | 4.92 | -53 | -0.04 | 0.55 | Y | 0.5 | -562 | 17.0 | [-9442,7689] | 0.55 | -1338 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| LONB_x565 | 4.92 | -53 | -0.04 | 0.55 | Y | 1.0 | -1124 | 159.3 | [-18884,15378] | 0.55 | -2677 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| WKND_E955 | 0.94 | 456 | 0.07 | 0.77 | Y | 0.25 | 2646 | 10.5 | [-1697,7170] | 0.66 | 2565 | 0.64 | 5 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| WKND_E955 | 0.94 | 456 | 0.07 | 0.77 | Y | 0.5 | 5291 | 38.6 | [-3395,14339] | 0.66 | 5130 | 0.64 | 5 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| WKND_E955 | 0.94 | 456 | 0.07 | 0.77 | Y | 1.0 | 10583 | 94.8 | [-6789,28678] | 0.66 | 10260 | 0.64 | 5 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| TUEREV_E570 | 0.91 | 34 | -0.03 | 0.55 | Y | 0.25 | 222 | 7.1 | [-4144,4623] | 0.55 | 133 | 4.86 | 5 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| TUEREV_E570 | 0.91 | 34 | -0.03 | 0.55 | Y | 0.5 | 444 | 14.2 | [-8288,9246] | 0.55 | 267 | 4.86 | 5 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| TUEREV_E570 | 0.91 | 34 | -0.03 | 0.55 | Y | 1.0 | 887 | 62.0 | [-16576,18491] | 0.55 | 533 | 4.86 | 5 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| GAPS_t2_x570 | 0.36 | -145 | 0.09 | 0.21 | Y | 0.25 | -1331 | 17.8 | [-5808,2704] | 0.26 | -1380 | None | 3 | p1_maxdd_down_10pct,p2_mean_not_down,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| GAPS_t2_x570 | 0.36 | -145 | 0.09 | 0.21 | Y | 0.5 | -2662 | 53.1 | [-11617,5409] | 0.26 | -2759 | None | 3 | p1_maxdd_down_10pct,p2_mean_not_down,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| GAPS_t2_x570 | 0.36 | -145 | 0.09 | 0.21 | Y | 1.0 | -5324 | 181.5 | [-23234,10817] | 0.26 | -5519 | None | 3 | p1_maxdd_down_10pct,p2_mean_not_down,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| GAPS_t4_x570 | 0.23 | -178 | 0.10 | 0.08 | Y | 0.25 | -1785 | 21.2 | [-6241,2303] | 0.20 | -1818 | None | 3 | p1_maxdd_down_10pct,p2_mean_not_down,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| GAPS_t4_x570 | 0.23 | -178 | 0.10 | 0.08 | Y | 0.5 | -3569 | 60.0 | [-12481,4607] | 0.20 | -3636 | None | 3 | p1_maxdd_down_10pct,p2_mean_not_down,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| GAPS_t4_x570 | 0.23 | -178 | 0.10 | 0.08 | Y | 1.0 | -7138 | 137.9 | [-24963,9213] | 0.20 | -7273 | None | 3 | p1_maxdd_down_10pct,p2_mean_not_down,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |

## BATCH 4 FINAL (ideas I16, I18, I19, I20, I21; holdout scored once, ledger track T3.7b4)
0/10 primary cells PASS (rows/T3_7_b4_final.json; 26 variants counted). Best: IBS_t20_n1 (long NQ when IBS<0.2 at 15:55, hold 1 day): 7/9 at every ratio, fails ONLY p1 (maxDD +5.3% / +10.6% / +31% vs Set A) and p6 (port placebo 0.94, standalone placebo 0.97); unit WF +1,013/wk, holdout +1,314/wk, corr -0.07, CI of portfolio-minus-Set-A at ratio 0.25 [210, 9,065], 2013-2023 +$88k over 427 trades (9 of 11 years positive), DSR 0.04. CAVEAT: weekly correlation of IBS_t20_n1 with RSI2_t10 is 0.66, so it is the same dip-buy edge, not an independent second lead. IBS_t20_n2 6/9 (maxDD -6.1% at 0.25 only; CI includes 0), ZNP_h60 6/9 (ZN-direction continuation, +453/wk WF, +352 holdout, fails p1 +13.9%, p5, p6 0.89), COT_p20 5/9, EIA_h60 5/9 (WF +48/wk, neighbours disagree), COT_p10 / NR7 / EIA_h30 / ZNN negative or <=3/9. Truncation audit 0 mismatches / 360 cuts (NQ, ZN, CL noised). I17 not scored (unfit; see above).

| cell | trades/wk | unit mean/wk (window) | corr SetA | stand placebo | nb agree | ratio | port dMean | dMaxDD % | CI | port placebo | x2 | yr max | pass of 9 | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ZNP_h60 | 4.65 | 453 | 0.06 | 0.88 | Y | 0.25 | 2269 | 13.9 | [-1982,6823] | 0.89 | 1924 | 0.52 | 6 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95 |
| ZNP_h60 | 4.65 | 453 | 0.06 | 0.88 | Y | 0.5 | 4537 | 35.6 | [-3963,13647] | 0.89 | 3847 | 0.52 | 6 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95 |
| ZNP_h60 | 4.65 | 453 | 0.06 | 0.88 | Y | 1.0 | 9075 | 139.2 | [-7927,27294] | 0.89 | 7694 | 0.52 | 6 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95 |
| ZNN_h60 | 4.65 | -591 | -0.06 | 0.12 | Y | 0.25 | -2959 | -9.8 | [-7519,1291] | 0.11 | -3304 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| ZNN_h60 | 4.65 | -591 | -0.06 | 0.12 | Y | 0.5 | -5917 | -2.4 | [-15038,2581] | 0.11 | -6607 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| ZNN_h60 | 4.65 | -591 | -0.06 | 0.12 | Y | 1.0 | -11834 | 97.5 | [-30075,5162] | 0.11 | -13215 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| COT_p10 | 0.30 | 113 | 0.09 | 0.53 | N | 0.25 | 464 | -3.7 | [-3829,4956] | 0.54 | 446 | 2.21 | 3 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok,neighbours_agree |
| COT_p10 | 0.30 | 113 | 0.09 | 0.53 | N | 0.5 | 928 | 34.7 | [-7659,9911] | 0.54 | 892 | 2.21 | 3 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok,neighbours_agree |
| COT_p10 | 0.30 | 113 | 0.09 | 0.53 | N | 1.0 | 1857 | 111.5 | [-15318,19822] | 0.54 | 1785 | 2.21 | 3 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok,neighbours_agree |
| COT_p20 | 0.58 | 192 | 0.12 | 0.52 | Y | 0.25 | 641 | 8.8 | [-3728,4883] | 0.53 | 613 | 1.6 | 5 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| COT_p20 | 0.58 | 192 | 0.12 | 0.52 | Y | 0.5 | 1283 | 20.8 | [-7457,9765] | 0.53 | 1226 | 1.6 | 5 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| COT_p20 | 0.58 | 192 | 0.12 | 0.52 | Y | 1.0 | 2566 | 114.1 | [-14913,19530] | 0.53 | 2451 | 1.6 | 5 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| EIA_h30 | 0.96 | -18 | -0.11 | 0.57 | Y | 0.25 | -1220 | 6.9 | [-5563,3162] | 0.56 | -2806 | None | 3 | p1_maxdd_down_10pct,p2_mean_not_down,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| EIA_h30 | 0.96 | -18 | -0.11 | 0.57 | Y | 0.5 | -2440 | 23.5 | [-11125,6325] | 0.56 | -5612 | None | 3 | p1_maxdd_down_10pct,p2_mean_not_down,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| EIA_h30 | 0.96 | -18 | -0.11 | 0.57 | Y | 1.0 | -4880 | 73.0 | [-22251,12649] | 0.56 | -11225 | None | 3 | p1_maxdd_down_10pct,p2_mean_not_down,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| EIA_h60 | 0.96 | 48 | -0.16 | 0.95 | N | 0.25 | 2579 | -0.6 | [-1462,6649] | 0.96 | 1306 | 0.7 | 5 | p1_maxdd_down_10pct,p5_ci_excludes0,year_ok,neighbours_agree |
| EIA_h60 | 0.96 | 48 | -0.16 | 0.95 | N | 0.5 | 5158 | 10.0 | [-2924,13298] | 0.96 | 2611 | 0.7 | 5 | p1_maxdd_down_10pct,p5_ci_excludes0,year_ok,neighbours_agree |
| EIA_h60 | 0.96 | 48 | -0.16 | 0.95 | N | 1.0 | 10316 | 70.5 | [-5849,26595] | 0.96 | 5222 | 0.7 | 5 | p1_maxdd_down_10pct,p5_ci_excludes0,year_ok,neighbours_agree |
| NR7_x955 | 0.70 | 81 | -0.05 | 0.63 | N | 0.25 | 767 | 7.3 | [-3516,5357] | 0.65 | 669 | 2.96 | 3 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok,neighbours_agree |
| NR7_x955 | 0.70 | 81 | -0.05 | 0.63 | N | 0.5 | 1535 | 84.0 | [-7032,10713] | 0.65 | 1339 | 2.96 | 3 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok,neighbours_agree |
| NR7_x955 | 0.70 | 81 | -0.05 | 0.63 | N | 1.0 | 3070 | 237.5 | [-14065,21426] | 0.65 | 2678 | 2.96 | 3 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok,neighbours_agree |
| NR7_x720 | 0.73 | -46 | 0.04 | 0.44 | N | 0.25 | -581 | 8.3 | [-4614,3734] | 0.43 | -717 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok,neighbours_agree |
| NR7_x720 | 0.73 | -46 | 0.04 | 0.44 | N | 0.5 | -1162 | 36.8 | [-9228,7469] | 0.43 | -1435 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok,neighbours_agree |
| NR7_x720 | 0.73 | -46 | 0.04 | 0.44 | N | 1.0 | -2323 | 135.5 | [-18456,14937] | 0.43 | -2870 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok,neighbours_agree |
| IBS_t20_n1 | 0.75 | 1013 | -0.07 | 0.97 | Y | 0.25 | 4232 | 5.3 | [210,9065] | 0.94 | 4186 | 0.47 | 7 | p1_maxdd_down_10pct,p6_placebo_ge95 |
| IBS_t20_n1 | 0.75 | 1013 | -0.07 | 0.97 | Y | 0.5 | 8465 | 10.6 | [420,18131] | 0.94 | 8372 | 0.47 | 7 | p1_maxdd_down_10pct,p6_placebo_ge95 |
| IBS_t20_n1 | 0.75 | 1013 | -0.07 | 0.97 | Y | 1.0 | 16930 | 31.0 | [840,36262] | 0.94 | 16745 | 0.47 | 7 | p1_maxdd_down_10pct,p6_placebo_ge95 |
| IBS_t20_n2 | 0.74 | 792 | -0.08 | 0.76 | Y | 0.25 | 3549 | -6.1 | [-380,7832] | 0.83 | 3500 | 0.56 | 6 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95 |
| IBS_t20_n2 | 0.74 | 792 | -0.08 | 0.76 | Y | 0.5 | 7098 | 12.9 | [-760,15663] | 0.83 | 7000 | 0.56 | 6 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95 |
| IBS_t20_n2 | 0.74 | 792 | -0.08 | 0.76 | Y | 1.0 | 14197 | 105.4 | [-1520,31326] | 0.83 | 14000 | 0.56 | 6 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95 |

## RSI2 COMBO FINAL (hard-cap variants of RSI2_t10; separate family, ledger track T3.7rsi2c, holdout scored once)
0/2 primary cells PASS (rows/T3_7_b4r_final.json; 6 variants counted). Both cells are 8/9 and fail ONLY p1:
- RSI2C_s20 (stop 2.0 x ATR14, ratio-scaled lots): unit WF +882/wk (holdout +1,065), stand placebo 0.98, port placebo 0.978, CI excludes 0 ([1,147, 10,141] at 0.25), corr -0.06, neighbours agree (stop 1.5 / 2.5: +978 / +1,005). Portfolio maxDD +3.2% / +53.7% / +187.6% vs Set A at ratios 0.25 / 0.5 / 1.0 (plain RSI2_t10 had +2.7% / +5.3% / +64%): the stop makes the drawdown WORSE, not better.
- RSI2CC_s20 (stop + 3-lot cap): cap binds at every ratio (k_ratio 6-25 lots), so the three ratio rows coincide at an effective SD ratio of about 0.12: dMean +2,646/wk (CI [574, 5,078]), placebo 0.984, maxDD +1.6% vs Set A. Hard caps shrink the drawdown penalty to +1.6% but cannot turn it into a >=10% reduction. L8W delta mean is negative (-3,898/wk at the cap; -7,784 at ratio 0.25 uncapped): the sleeve lost money in the last 8 weeks.
Verdict: the RSI2 sleeve stays a mean-adder LEAD (post-selected follow-up of a known near-miss), not a second-system PASS: p1 fails with or without hard caps.

| cell | trades/wk | unit mean/wk (window) | corr SetA | stand placebo | nb agree | ratio | port dMean | dMaxDD % | CI | port placebo | x2 | yr max | pass of 9 | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| RSI2C_s20 | 0.49 | 882 | -0.06 | 0.98 | Y | 0.25 | 5284 | 3.2 | [1147,10141] | 0.98 | 5240 | 0.44 | 8 | p1_maxdd_down_10pct |
| RSI2C_s20 | 0.49 | 882 | -0.06 | 0.98 | Y | 0.5 | 10568 | 53.7 | [2294,20281] | 0.98 | 10481 | 0.44 | 8 | p1_maxdd_down_10pct |
| RSI2C_s20 | 0.49 | 882 | -0.06 | 0.98 | Y | 1.0 | 21137 | 187.6 | [4588,40563] | 0.98 | 20962 | 0.44 | 8 | p1_maxdd_down_10pct |
| RSI2CC_s20 | 0.49 | 882 | -0.06 | 0.98 | Y | 0.25 | 2646 | 1.6 | [574,5078] | 0.98 | 2624 | 0.44 | 8 | p1_maxdd_down_10pct |
| RSI2CC_s20 | 0.49 | 882 | -0.06 | 0.98 | Y | 0.5 | 2646 | 1.6 | [574,5078] | 0.98 | 2624 | 0.44 | 8 | p1_maxdd_down_10pct |
| RSI2CC_s20 | 0.49 | 882 | -0.06 | 0.98 | Y | 1.0 | 2646 | 1.6 | [574,5078] | 0.98 | 2624 | 0.44 | 8 | p1_maxdd_down_10pct |

## SUMMARY (T3.7)
- Batch 3 (I11-I15): 0/10 PASS. Batch 4 (I16, I18-I20 + I21 replacing unfit I17): 0/10 PASS. RSI2-combo family: 0/2 PASS (8/9, fails only p1). Total 22 primary cells, 61 variants logged as trials (29 + 26 + 6; ledger T3.7b3, T3.7b4, T3.7rsi2c; cumulative ledger total after these: 28,337).
- Most frequently failed: p1 (maxDD down >=10%, all 22 cells), p6 placebo, p5 CI, neighbours_agree for small-n cells, year share for TUEREV/COT/NR.
- Leads (all fail p1): RSI2C_s20 / RSI2CC_s20 (8/9), IBS_t20_n1 (7/9; fails p1 + port placebo 0.94; 0.66 weekly corr with RSI2 so not independent).
- Pattern across T3.6-T3.7 (40 primary cells): the only edges that survive are long-only NQ dip-buys at the 15:55 close (RSI2, IBS); they add mean uncorrelated to D2 weekly P&L but never reduce Set A's maxDD by 10%.
- Caveats: 1-min conservative fills; roll-spanning rows dropped (I12 excludes quarterly OPEX weeks since ~2020); CL/ZN/RTY costs are proxies ($4.84 + 1 tick/side); COT release lag modelled as Friday (CFTC-only holiday delays not modelled); I21 added post hoc.
- Files: rows/T3_7_b3_{pre,final}.json, rows/T3_7_b4_{pre,final}.json, rows/T3_7_b4r_{pre,final}.json, rows/T3_7_proposed.json, out/T3_7/*.npz, audit/T3_7b{3,4,4r}_trunc.json, code/t37*.py, prereg/T3_6b3.md, T3_6b4.md, T3_7_rsi2c.md.
