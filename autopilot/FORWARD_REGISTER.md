# FORWARD_REGISTER (RESEARCH V2 sec 5; rewritten after every live-file arrival; generated 2026-10-27 01:19 ET)

Weeks start Sunday 18:00 ET. W43 (10-19..10-23) informational, never counted; official = W44+. Live file: `<repo>/data/live/StratTrades_DualStrat2_<acct>.csv` (80 grouped trades, last exit 2026-10-26 11:44 ET). Verdicts: PROMOTE >= 6 weeks, z >= -1, sign right; RETIRE >= 8 weeks, z < -2; BEHIND z < -1; z = (realised - expected*n)/(expected SD*sqrt(n)).

## Reference: Set A (live DualStrat2 HM+ST) realised vs its backtest expectation

Expectation $24,975/wk, SD $104,500/wk, ~35 trades/wk (REPORT_DS2_FIRM_V4 benchmark (corrected P9 14/14 $4.84, WF 25.0k/wk, SD 104.5k); FWD_AB_SETS hist_natural_vs_p9 WF_p9 24,975). WT rows in the same csv (sleeve, not Set A) are excluded here.

| week | role | status | trades | realised $ | expected $ | per trade realised | per trade expected | z (week) | cum z (official) |
|---|---|---|---|---|---|---|---|---|---|
| 2026-W43 | info | COMPLETE | 39 | -184,580 | 24,975 | -4,733 | 714 | -2.01 | - |
| 2026-W44 | official | IN PROGRESS | 22 | -47,620 | 24,975 | -2,165 | 714 | -0.69 | - |

Set A vs Set B forward column (FWD_AB_SETS; flat natural fills on forward weeks; PENDING until the 1-s tape is extended):

| week | role | status | A net | B net | B-A | live net (all csv rows) | live trades |
|---|---|---|---|---|---|---|---|
| 2026-W43 | info | DONE | -134,500 | -86,278 | - | -189,750 | 49 |
| 2026-W44 | official | PENDING | - | - | - | -63,815 | 33 |
| 2026-W45 | official | PENDING | - | - | - | - | 0 |
| 2026-W46 | official | PENDING | - | - | - | - | 0 |
| 2026-W47 | official | PENDING | - | - | - | - | 0 |

Tape ends 2026-10-23 20:59:00 UTC (label day 20261023); verdict field: none: 4 forward weeks cannot decide; numbers only

## Registered cells (PAPER-ALL, from l2vast/struct48/paper_all/)

| cell | tier | object | start wk | weeks live | n trades | realised $ | expected $ | real/wk | exp/wk | per trade real | per trade exp | z | verdict | evaluator | W43 info $ |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| B01_SetB | CANDIDATE | sizing/lock rule (risk set) | 2026-W44 | 0 | 0 | 0 | 0 | - | 8,131 | - | - | - | ON TRACK (0 weeks live) | LIVE (FWD_AB_SETS B-A; natural fills) | 48,223 |
| B05_SetB_pb3R_vsA | CANDIDATE | sizing/lock rule (risk set) | 2026-W44 | 0 | - | - | 0 | - | 9,066 | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| B05_SetB_pb4R_vsA | CANDIDATE | sizing/lock rule (risk set) | 2026-W44 | 0 | - | - | 0 | - | 8,383 | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| B05_SetB_pboff_vsA | CANDIDATE | sizing/lock rule (risk set) | 2026-W44 | 0 | - | - | 0 | - | 10,507 | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| B06_SetB_pb2R_noprofit_vsA | CANDIDATE | sizing/lock rule (risk set) | 2026-W44 | 0 | - | - | 0 | - | 8,016 | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| B06_SetB_pb3R_noprofit_vsA | CANDIDATE | sizing/lock rule (risk set) | 2026-W44 | 0 | - | - | 0 | - | 9,125 | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| B06_SetB_pb4R_noprofit_vsA | CANDIDATE | sizing/lock rule (risk set) | 2026-W44 | 0 | - | - | 0 | - | 8,442 | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| B06_SetB_pboff_noprofit_vsA | CANDIDATE | sizing/lock rule (risk set) | 2026-W44 | 0 | - | - | 0 | - | 10,566 | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| B07_SetB_Rscaled_pb2R_vsA | CANDIDATE | sizing/lock rule (risk set) | 2026-W44 | 0 | - | - | 0 | - | 6,902 | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| B07_SetB_Rscaled_pb4R_vsA | CANDIDATE | sizing/lock rule (risk set) | 2026-W44 | 0 | - | - | 0 | - | 8,344 | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| BRK_960_1080 | PASS | sleeve | 2026-W44 | 0 | 0 | 0 | 0 | - | 9,707 | - | 106.06485074626862 | - | ON TRACK (0 weeks live) | LIVE (script) | 104,027 |
| COMB_c3_R | PASS | sleeve | 2026-W44 | 0 | 0 | 0 | 0 | - | 2,831 | - | 1262.066474820144 | - | ON TRACK (0 weeks live) | LIVE (script) | 22,335 |
| ES_RSI2_t10 | PASS | sleeve | 2026-W44 | 0 | 0 | 0 | 0 | - | 12,559 | - | 1544.535 | - | ON TRACK (0 weeks live) | LIVE (script; no forward trades yet / bars not extended) | 0 |
| GSHORT_t90 | PASS | sleeve | 2026-W44 | 0 | - | - | 0 | - | 5,941 | - | 742.7406451612902 | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: GSHORT needs Set A daily P&L aligned to the extended calendar: not wired | - |
| IBS_t20_n1 | CANDIDATE | sleeve | 2026-W44 | 0 | 0 | 0 | 0 | - | 8,465 | - | 1357.5184905660378 | - | ON TRACK (0 weeks live) | LIVE (script) | 62,192 |
| NM_E_BRK_960_1080 | PASS | sleeve | 2026-W44 | 0 | 0 | 0 | 0 | - | 4,853 | - | 1285.7798054864124 | - | ON TRACK (0 weeks live) | LIVE (script) | 52,014 |
| NM_E_COMB_c3_R | PASS | sleeve | 2026-W44 | 0 | 0 | 0 | 0 | - | 5,118 | - | 5228.203652850883 | - | ON TRACK (0 weeks live) | LIVE (script) | 30,842 |
| NM_E_ES_RSI2_t10 | PASS | sleeve | 2026-W44 | 0 | 0 | 0 | 0 | - | 6,279 | - | 14861.047446187713 | - | ON TRACK (0 weeks live) | LIVE (script; no forward trades yet / bars not extended) | 0 |
| NM_E_GSHORT_t90 | PASS | sleeve | 2026-W44 | 0 | - | - | 0 | - | 2,970 | - | 13606.497415702072 | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: GSHORT needs Set A daily P&L aligned to the extended calendar: not wired | - |
| NM_E_NQ_IBS_t20_n1 | CANDIDATE | sleeve | 2026-W44 | 0 | 0 | 0 | 0 | - | 4,232 | - | 5669.935565963551 | - | ON TRACK (0 weeks live) | LIVE (script) | 31,096 |
| NM_E_NQ_RSI2CC_s20 | PASS | sleeve | 2026-W44 | 0 | 0 | 0 | 0 | - | 5,284 | - | 10719.442546348757 | - | ON TRACK (0 weeks live) | LIVE (script) | 44,602 |
| NM_E_NQ_RSI2C_s20 | PASS | sleeve | 2026-W44 | 0 | 0 | 0 | 0 | - | 5,284 | - | 10719.442546348757 | - | ON TRACK (0 weeks live) | LIVE (script) | 44,602 |
| NM_E_NQ_RSI2T_t10 | PASS | sleeve | 2026-W44 | 0 | 0 | 0 | 0 | - | 4,441 | - | 11261.571312508817 | - | ON TRACK (0 weeks live) | LIVE (script) | 53,615 |
| NM_E_NQ_RSI2_t10 | PASS | sleeve | 2026-W44 | 0 | 0 | 0 | 0 | - | 5,099 | - | 10342.737682700013 | - | ON TRACK (0 weeks live) | LIVE (script) | 37,757 |
| NM_E_ORB_ASIA_15_v1_s60 | PASS | sleeve | 2026-W44 | 0 | - | - | 0 | - | 4,462 | - | 5323.817786101251 | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: no evaluator wired for NM_E_ORB_ASIA_15_v1_s60 (ORB / overnight-drift / unknown variant) | - |
| NM_E_ORB_ASIA_15_v1_s75 | PASS | sleeve | 2026-W44 | 0 | - | - | 0 | - | 4,472 | - | 5336.896655614357 | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: no evaluator wired for NM_E_ORB_ASIA_15_v1_s75 (ORB / overnight-drift / unknown variant) | - |
| NM_E_RTY_IBS_t20_n1 | CANDIDATE | sleeve | 2026-W44 | 0 | 0 | 0 | 0 | - | 3,618 | - | 3982.8634438817066 | - | ON TRACK (0 weeks live) | LIVE (script) | 6,077 |
| NM_E_RTY_RSI2_t10 | PASS | sleeve | 2026-W44 | 0 | 0 | 0 | 0 | - | 8,005 | - | 17221.935768024072 | - | ON TRACK (0 weeks live) | LIVE (script; no forward trades yet / bars not extended) | 0 |
| ON_none_L2 | PASS | sleeve | 2026-W44 | 0 | - | - | 0 | - | 7,476 | - | 505.0107993966814 | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: no evaluator wired for ON_none_L2 (ORB / overnight-drift / unknown variant) | - |
| ON_none_L4 | PASS | sleeve | 2026-W44 | 0 | - | - | 0 | - | 7,476 | - | 1010.0215987933628 | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: no evaluator wired for ON_none_L4 (ORB / overnight-drift / unknown variant) | - |
| ORB_ASIA_15_v1__s60_0.25 | CANDIDATE | sleeve | 2026-W44 | 0 | - | - | 0 | - | 4,069 | - | 4018.7576470593326 | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: no evaluator wired for ORB_ASIA_15_v1__s60_0.25 (ORB / overnight-drift / unknown variant) | - |
| ORB_ASIA_15_v1__s60_0.5 | CANDIDATE | sleeve | 2026-W44 | 0 | - | - | 0 | - | 8,138 | - | 4018.7576470593326 | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: no evaluator wired for ORB_ASIA_15_v1__s60_0.5 (ORB / overnight-drift / unknown variant) | - |
| ORB_ASIA_15_v1__s60_1.0 | CANDIDATE | sleeve | 2026-W44 | 0 | - | - | 0 | - | 16,276 | - | 4018.7576470593326 | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: no evaluator wired for ORB_ASIA_15_v1__s60_1.0 (ORB / overnight-drift / unknown variant) | - |
| ORB_ASIA_15_v1__s75_0.25 | CANDIDATE | sleeve | 2026-W44 | 0 | - | - | 0 | - | 3,864 | - | 4723.534117647571 | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: no evaluator wired for ORB_ASIA_15_v1__s75_0.25 (ORB / overnight-drift / unknown variant) | - |
| ORB_ASIA_15_v1__s75_0.5 | CANDIDATE | sleeve | 2026-W44 | 0 | - | - | 0 | - | 7,727 | - | 4723.534117647571 | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: no evaluator wired for ORB_ASIA_15_v1__s75_0.5 (ORB / overnight-drift / unknown variant) | - |
| ORB_ASIA_15_v1__s75_1.0 | CANDIDATE | sleeve | 2026-W44 | 0 | - | - | 0 | - | 15,455 | - | 4723.534117647571 | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: no evaluator wired for ORB_ASIA_15_v1__s75_1.0 (ORB / overnight-drift / unknown variant) | - |
| ORB_ASIA_30_v1__s60_0.25 | CANDIDATE | sleeve | 2026-W44 | 0 | - | - | 0 | - | 4,001 | - | 4141.419130435292 | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: no evaluator wired for ORB_ASIA_30_v1__s60_0.25 (ORB / overnight-drift / unknown variant) | - |
| ORB_ASIA_30_v1__s60_0.5 | CANDIDATE | sleeve | 2026-W44 | 0 | - | - | 0 | - | 8,001 | - | 4141.419130435292 | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: no evaluator wired for ORB_ASIA_30_v1__s60_0.5 (ORB / overnight-drift / unknown variant) | - |
| ORB_ASIA_30_v1__s60_1.0 | CANDIDATE | sleeve | 2026-W44 | 0 | - | - | 0 | - | 16,003 | - | 4141.419130435292 | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: no evaluator wired for ORB_ASIA_30_v1__s60_1.0 (ORB / overnight-drift / unknown variant) | - |
| RSI2CC_s20 | PASS | sleeve | 2026-W44 | 0 | 0 | 0 | 0 | - | 2,646 | - | 1789.3398376761188 | - | ON TRACK (0 weeks live) | LIVE (script) | 22,335 |
| RSI2C_s20 | PASS | sleeve | 2026-W44 | 0 | 0 | 0 | 0 | - | 10,568 | - | 1789.3398376761188 | - | ON TRACK (0 weeks live) | LIVE (script) | 89,204 |
| RSI2T_t10 | PASS | sleeve | 2026-W44 | 0 | 0 | 0 | 0 | - | 8,882 | - | 1563.820714285714 | - | ON TRACK (0 weeks live) | LIVE (script) | 107,230 |
| RSI2_t10 | PASS | sleeve | 2026-W44 | 0 | 0 | 0 | 0 | - | 10,197 | - | 2039.4457142857145 | - | ON TRACK (0 weeks live) | LIVE (script) | 75,514 |
| RTY_IBS_t20_n1 | CANDIDATE | sleeve | 2026-W44 | 0 | 0 | 0 | 0 | - | 7,236 | - | 242.601860465117 | - | ON TRACK (0 weeks live) | LIVE (script) | 12,154 |
| RTY_RSI2_t10 | PASS | sleeve | 2026-W44 | 0 | 0 | 0 | 0 | - | 16,009 | - | 712.8872727272733 | - | ON TRACK (0 weeks live) | LIVE (script; no forward trades yet / bars not extended) | 0 |
| YM_RSI2_t10 | CANDIDATE | sleeve | 2026-W44 | 0 | - | - | 0 | - | 8,274 | - | 521.8907692307694 | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: no extended 1-min source for YM | - |
| BK1_SETB_sizecredit | CANDIDATE | sizing/lock rule (risk set) | 2026-W44 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| T14_S_s50_t1.5_n14 | CANDIDATE | trade-modifier (shorts-only bracket) | 2026-W44 | 0 | 0 | 0 | 0 | - | 7,914 | - | 84 | - | ON TRACK (0 weeks live) | LIVE (script) | 47,950 |
| T4.2_Y4 | CANDIDATE | execution change | 2026-W44 | 0 | - | - | 0 | - | 179 | - | 0.0503076242657505 | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| DIPBUY_RSI2_2lot | PASS | sleeve | 2026-W44 | 0 | 0 | 0 | 0 | - | 3,091 | - | - | - | ON TRACK (0 weeks live) | LIVE (script) | 14,890 |
| ds3_TB1_ST_k15_P60_N | CANDIDATE | sleeve (NQ intraday trend book, standalone) | 2026-W44 | 0 | - | - | 0 | - | 10,933 | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: no evaluator wired for ds3_TB1_ST_k15_P60_N (ORB / overnight-drift / unknown variant) | - |
| ds3_TB7_ORBNY_k3_P60_N | CANDIDATE | sleeve (NQ intraday trend book, standalone) | 2026-W44 | 0 | - | - | 0 | - | 6,866 | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: no evaluator wired for ds3_TB7_ORBNY_k3_P60_N (ORB / overnight-drift / unknown variant) | - |
| ds3_TB9_RENKO_c2_k1_P60_N | CANDIDATE | sleeve (NQ intraday trend book, standalone) | 2026-W44 | 0 | - | - | 0 | - | 9,418 | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: no evaluator wired for ds3_TB9_RENKO_c2_k1_P60_N (ORB / overnight-drift / unknown variant) | - |
| ds3_TB9_RENKO_c5_k1_A3_N | DEAD | sleeve (NQ intraday trend book, standalone) | 2026-W44 | 0 | - | - | 0 | - | 14,628 | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: no evaluator wired for ds3_TB9_RENKO_c5_k1_A3_N (ORB / overnight-drift / unknown variant) | - |
| ds3_TE_TE1B_boll_3m | CANDIDATE | signal (entry into DS2 bracket, standalone book; T-ENTRY) | 2026-W44 | 0 | - | - | 0 | - | 10,405 | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: no bar evaluator wired for family boll | - |
| ds3_TE_TE1B_emax_5m | CANDIDATE | signal (entry into DS2 bracket, standalone book; T-ENTRY) | 2026-W44 | 0 | 0 | 0 | 0 | - | 6,817 | - | - | - | ON TRACK (0 weeks live) | LIVE (script) | 11,371 |
| ds3_TE_TE1_kelt_3m | CANDIDATE | signal (entry into DS2 bracket, standalone book; T-ENTRY) | 2026-W44 | 0 | 0 | 0 | 0 | - | 13,416 | - | - | - | ON TRACK (0 weeks live) | LIVE (script) | -14,081 |
| ds3_TE_TE1_st_10m | PASS | signal (entry into DS2 bracket, standalone book; T-ENTRY) | 2026-W44 | 0 | 0 | 0 | 0 | - | 8,799 | - | - | - | ON TRACK (0 weeks live) | LIVE (script) | -60,532 |
| ds3_TE_TE3_ice_follow_lb30_q0.95 | CANDIDATE | signal (entry into DS2 bracket, standalone book; T-ENTRY) | 2026-W44 | 0 | - | - | 0 | - | 4,815 | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: no bar evaluator wired for family ice | - |
| ds3_TE_TE3_ice_follow_lb30_q0.99 | CANDIDATE | signal (entry into DS2 bracket, standalone book; T-ENTRY) | 2026-W44 | 0 | - | - | 0 | - | 3,269 | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: no bar evaluator wired for family ice | - |
| ds3_TE_TE6_st10m_n10_m3.0 | PASS | signal (entry into DS2 bracket, standalone book; T-ENTRY) | 2026-W44 | 0 | 0 | 0 | 0 | - | 8,799 | - | - | - | ON TRACK (0 weeks live) | LIVE (script) | -60,532 |
| ds3_TE_TE6_st10m_n10_m3.5 | CANDIDATE | signal (entry into DS2 bracket, standalone book; T-ENTRY) | 2026-W44 | 0 | 0 | 0 | 0 | - | 5,304 | - | - | - | ON TRACK (0 weeks live) | LIVE (script) | -60,532 |
| ds3_TE_TE6_st10m_n14_m3.0 | PASS | signal (entry into DS2 bracket, standalone book; T-ENTRY) | 2026-W44 | 0 | 0 | 0 | 0 | - | 6,980 | - | - | - | ON TRACK (0 weeks live) | LIVE (script) | -60,532 |
| ds3_TE_TE6_st10m_n7_m3.0 | PASS | signal (entry into DS2 bracket, standalone book; T-ENTRY) | 2026-W44 | 0 | 0 | 0 | 0 | - | 8,749 | - | - | - | ON TRACK (0 weeks live) | LIVE (script) | -60,629 |
| ds3_TE_TE7_boll3m_n20_m1.5 | CANDIDATE | signal (entry into DS2 bracket, standalone book; T-ENTRY) | 2026-W44 | 0 | - | - | 0 | - | 10,602 | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: no bar evaluator wired for family boll | - |
| ds3_TE_TE7_boll3m_n20_m2.0 | CANDIDATE | signal (entry into DS2 bracket, standalone book; T-ENTRY) | 2026-W44 | 0 | - | - | 0 | - | 10,405 | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: no bar evaluator wired for family boll | - |
| ds3_TE_TE7_boll3m_n30_m1.5 | CANDIDATE | signal (entry into DS2 bracket, standalone book; T-ENTRY) | 2026-W44 | 0 | - | - | 0 | - | 11,366 | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: no bar evaluator wired for family boll | - |
| ds3_TE_TE7_emax5m_f20_s50 | CANDIDATE | signal (entry into DS2 bracket, standalone book; T-ENTRY) | 2026-W44 | 0 | 0 | 0 | 0 | - | 6,817 | - | - | - | ON TRACK (0 weeks live) | LIVE (script) | 11,371 |
| ds3_TE_TE7_emax5m_f30_s50 | PASS | signal (entry into DS2 bracket, standalone book; T-ENTRY) | 2026-W44 | 0 | 0 | 0 | 0 | - | 7,142 | - | - | - | ON TRACK (0 weeks live) | LIVE (script) | -60,726 |
| ds3_TE_TE7_kelt3m_n14_m1.0 | PASS | signal (entry into DS2 bracket, standalone book; T-ENTRY) | 2026-W44 | 0 | 0 | 0 | 0 | - | 16,863 | - | - | - | ON TRACK (0 weeks live) | LIVE (script) | 34,016 |
| ds3_TE_TE7_kelt3m_n14_m1.5 | CANDIDATE | signal (entry into DS2 bracket, standalone book; T-ENTRY) | 2026-W44 | 0 | 0 | 0 | 0 | - | 8,453 | - | - | - | ON TRACK (0 weeks live) | LIVE (script) | -13,888 |
| ds3_TE_TE7_kelt3m_n20_m1.0 | CANDIDATE | signal (entry into DS2 bracket, standalone book; T-ENTRY) | 2026-W44 | 0 | 0 | 0 | 0 | - | 17,235 | - | - | - | ON TRACK (0 weeks live) | LIVE (script) | 33,725 |
| ds3_TE_TE7_kelt3m_n20_m1.5 | CANDIDATE | signal (entry into DS2 bracket, standalone book; T-ENTRY) | 2026-W44 | 0 | 0 | 0 | 0 | - | 13,416 | - | - | - | ON TRACK (0 weeks live) | LIVE (script) | -14,081 |
| ds3_TE_TE7_kelt3m_n30_m1.0 | CANDIDATE | signal (entry into DS2 bracket, standalone book; T-ENTRY) | 2026-W44 | 0 | 0 | 0 | 0 | - | 13,603 | - | - | - | ON TRACK (0 weeks live) | LIVE (script) | 10,500 |
| ds3_TF1_FOMC_NY_block | CANDIDATE | trade-modifier (entry filter on NQ NY-window trend entries) | 2026-W44 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_TE2_GC_KEL_k15 | CANDIDATE | sleeve (GC 15-min intraday trend book, standalone) | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: no evaluator wired for ds3_TE2_GC_KEL_k15 (ORB / overnight-drift / unknown variant) | - |
| ds3_TE2_GC_VWAP_k15 | CANDIDATE | sleeve (GC 15-min intraday trend book, standalone) | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: no evaluator wired for ds3_TE2_GC_VWAP_k15 (ORB / overnight-drift / unknown variant) | - |
| ds3_TA1__TE1_kelt_3m__wide | CANDIDATE | signal (entry + regime gate; gate execution-server-only) | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_TA1__TE1_st_10m__wide | CANDIDATE | signal (entry + regime gate; gate execution-server-only) | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_TA1__TE6_st10m_n14_m3.0__wide | CANDIDATE | signal (entry + regime gate; gate execution-server-only) | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_TA1__TE7_boll3m_n20_m1.5__wide | CANDIDATE | signal (entry + regime gate; gate execution-server-only) | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_TA1__TE7_boll3m_n30_m1.5__wide | CANDIDATE | signal (entry + regime gate; gate execution-server-only) | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_TA1__TE7_kelt3m_n14_m1.0__wide | CANDIDATE | signal (entry + regime gate; gate execution-server-only) | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_TA1__TE7_kelt3m_n20_m1.0__wide | CANDIDATE | signal (entry + regime gate; gate execution-server-only) | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_PRO3A_P3 | CANDIDATE | signal (T-PULLBACK base cell filtered by an as-of trend-quality condition) | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_PRO3A_REL | CANDIDATE | signal (T-PULLBACK base cell filtered by an as-of trend-quality condition) | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_PRO3A_VOL | CANDIDATE | signal (T-PULLBACK base cell filtered by an as-of trend-quality condition) | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_PRO3A_X30 | CANDIDATE | signal (T-PULLBACK base cell filtered by an as-of trend-quality condition) | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_TR1A_ens_s0.5_k4 | CANDIDATE | signal (T-TREND PRO R1/R6 trend entry into the DS2 bracket) | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_TR1A_ens_s1.0_k3 | CANDIDATE | signal (T-TREND PRO R1/R6 trend entry into the DS2 bracket) | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_TR1B_reg1m_n60_t2_r0.5 | CANDIDATE | signal (T-TREND PRO R1/R6 trend entry into the DS2 bracket) | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_TR1B_reg1m_n60_t3_r0.5 | CANDIDATE | signal (T-TREND PRO R1/R6 trend entry into the DS2 bracket) | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_TR1C_MAMA_10m_flip | CANDIDATE | signal (T-TREND PRO R1/R6 trend entry into the DS2 bracket) | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_TR1D_HP_10m_slope | CANDIDATE | signal (T-TREND PRO R1/R6 trend entry into the DS2 bracket) | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_TR1E_retest_15m_c3 | CANDIDATE | signal (T-TREND PRO R1/R6 trend entry into the DS2 bracket) | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_TR1F_vote_TSM_k3 | CANDIDATE | signal (T-TREND PRO R1/R6 trend entry into the DS2 bracket) | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_TR3_DON15_S | CANDIDATE | signal (entry type; stop/limit order at the break level) | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_TR3_KB20_S | CANDIDATE | signal (entry type; stop/limit order at the break level) | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_TR3_KB_RT15 | CANDIDATE | signal (entry type; stop/limit order at the break level) | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_TR3_KB_RT5 | CANDIDATE | signal (entry type; stop/limit order at the break level) | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_TR3_KB_S | CANDIDATE | signal (entry type; stop/limit order at the break level) | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_PRO_ER4_EMA5 | CANDIDATE | signal | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_PRO_ER4_n40_EMA5 | CANDIDATE | signal | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_PRO_ER5_EMA5 | CANDIDATE | signal | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_PRO_ER6_n20_EMA5 | CANDIDATE | signal | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_PRO_KAL_k0.0 | CANDIDATE | signal | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_PRO_KAL_s0.5_k0.0 | CANDIDATE | signal | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_PRO_KAL_s0.5_k0.25 | CANDIDATE | signal | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_PRO_RIB1m_q25_M10 | CANDIDATE | signal | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_PRO_RIB1m_q25_M5 | CANDIDATE | signal | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_PRO_RIB1m_q30 | CANDIDATE | signal | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_PRO_RIB1m_q30_M20 | CANDIDATE | signal | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_PRO_RIB1m_q30_M5 | CANDIDATE | signal | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_PRO_RIB1m_q35_M20 | CANDIDATE | signal | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_PRO_RIB1m_q35_M5 | CANDIDATE | signal | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_PRO_Z20_t1.0 | CANDIDATE | signal | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_PRO_Z60_t1.0 | CANDIDATE | signal | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_tpullback3_PB3B_R10_P3 | CANDIDATE | signal (multi-timeframe pullback entry with DS2 or pullback bracket; bars only) | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_tpullback3_PB3B_R5_P1 | CANDIDATE | signal (multi-timeframe pullback entry with DS2 or pullback bracket; bars only) | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_tpullback3_PB3B_R5_P3 | CANDIDATE | signal (multi-timeframe pullback entry with DS2 or pullback bracket; bars only) | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_tpullback3_PB3B_R60_P2 | CANDIDATE | signal (multi-timeframe pullback entry with DS2 or pullback bracket; bars only) | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_tpullback3_PB3B_R60_P3 | CANDIDATE | signal (multi-timeframe pullback entry with DS2 or pullback bracket; bars only) | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_tpullback3_PB3D_R3_P2 | CANDIDATE | signal (multi-timeframe pullback entry, bars only) | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_tpullback3_PB3E_D_R3_P2_40_1.5R | CANDIDATE | signal (multi-timeframe pullback entry with DS2 or pullback bracket; bars only) | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| ds3_tpullback3_PB3F_D_R3_P2_60_2R_bracket | CANDIDATE | signal (multi-timeframe pullback entry with DS2 or pullback bracket; bars only) | 2026-W45 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |

Per-cell frozen expectation (WF / L8W / IS) and parameters: `autopilot/forward/series/PAPERALL_CELLS.json`.

Removed from the register (kept in the json): TEST_dryrun

## Live stop-join rate and slip (Set A stop exits; file `StratTrades_DualStrat2_<acct>.csv`)

| item | live | replay | note |
|---|---|---|---|
| join rate (stop-join fills / attempts) | 8/20 = 0.40 exact 95% CI [0.19, 0.64] | 0.78 | attempts = joined + fell back to market; broker-rejected join attempts (1) counted separately; incl. rejects 8/21 |
| replay inside live CI? | NO | | |
| stop-exit slip vs nominal, all stop exits | 2.45 pts worse (n=21; 95% CI 1.01..3.89) | 0.52 pts worse | nominal = entry avg -/+ 60 pts; live earlier read 2.01 on n=18 |
| stop-exit slip, join-filled | -0.52 pts worse (n=8; 95% CI -1.23..0.19) | - | |
| stop-exit slip, market fallback | 4.46 pts worse (n=12; 95% CI 2.80..6.13) | 1.74 pts worse | |
| entry slip vs mid at signal | PENDING: no tape mids (data/live/REF.csv absent; NQ 1-min series ends 2026-10-23 20:59:00 UTC) | ST 1.90 / HM 1.77 ticks (S14x1) | filled by LIVE_RECON once bars/REF arrive |

Weekly (official/info) join and slip:

| week | stop exits | joined | fell back | rejected | join rate | slip pts worse |
|---|---|---|---|---|---|---|
| 2026-W43 | 18 | 8 | 9 | 1 | 0.47 | 2.01 |
| 2026-W44 | 3 | 0 | 3 | 0 | 0.00 | 5.10 |

Other forward shadows (DS15, S130, P30/P36, ...) remain in LEAGUE.md / ap_m2_paperall.py. Weekly L2 extension check: tape 2026-10-23 20:59:00 UTC (a Saturday 06:00Z run extends it; nothing is bought here).
