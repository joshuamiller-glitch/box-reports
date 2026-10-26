# FORWARD_REGISTER (RESEARCH V2 sec 5; rewritten after every live-file arrival; generated 2026-10-26 18:16 ET)

Weeks start Sunday 18:00 ET. W43 (10-19..10-23) informational, never counted; official = W44+. Live file: `<repo>/data/live/StratTrades_DualStrat2_<acct>.csv` (80 grouped trades, last exit 2026-10-26 10:44 ET). Verdicts: PROMOTE >= 6 weeks, z >= -1, sign right; RETIRE >= 8 weeks, z < -2; BEHIND z < -1; z = (realised - expected*n)/(expected SD*sqrt(n)).

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
| B05_SetB_pb3R_vsA | CANDIDATE | sizing/lock rule (risk set) | 2026-W44 | 0 | - | - | 0 | - | 9,066 | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) [MERGED into B01_SetB: same exposure, not an independent test] | AWAITING EVALUATOR | - |
| B05_SetB_pb4R_vsA | CANDIDATE | sizing/lock rule (risk set) | 2026-W44 | 0 | - | - | 0 | - | 8,383 | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) [MERGED into B01_SetB: same exposure, not an independent test] | AWAITING EVALUATOR | - |
| B05_SetB_pboff_vsA | CANDIDATE | sizing/lock rule (risk set) | 2026-W44 | 0 | - | - | 0 | - | 10,507 | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) [MERGED into B01_SetB: same exposure, not an independent test] | AWAITING EVALUATOR | - |
| B06_SetB_pb2R_noprofit_vsA | CANDIDATE | sizing/lock rule (risk set) | 2026-W44 | 0 | - | - | 0 | - | 8,016 | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) [MERGED into B01_SetB: same exposure, not an independent test] | AWAITING EVALUATOR | - |
| B06_SetB_pb3R_noprofit_vsA | CANDIDATE | sizing/lock rule (risk set) | 2026-W44 | 0 | - | - | 0 | - | 9,125 | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) [MERGED into B01_SetB: same exposure, not an independent test] | AWAITING EVALUATOR | - |
| B06_SetB_pb4R_noprofit_vsA | CANDIDATE | sizing/lock rule (risk set) | 2026-W44 | 0 | - | - | 0 | - | 8,442 | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) [MERGED into B01_SetB: same exposure, not an independent test] | AWAITING EVALUATOR | - |
| B06_SetB_pboff_noprofit_vsA | CANDIDATE | sizing/lock rule (risk set) | 2026-W44 | 0 | - | - | 0 | - | 10,566 | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) [MERGED into B01_SetB: same exposure, not an independent test] | AWAITING EVALUATOR | - |
| B07_SetB_Rscaled_pb2R_vsA | CANDIDATE | sizing/lock rule (risk set) | 2026-W44 | 0 | - | - | 0 | - | 6,902 | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) [MERGED into B01_SetB: same exposure, not an independent test] | AWAITING EVALUATOR | - |
| B07_SetB_Rscaled_pb4R_vsA | CANDIDATE | sizing/lock rule (risk set) | 2026-W44 | 0 | - | - | 0 | - | 8,344 | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) [MERGED into B01_SetB: same exposure, not an independent test] | AWAITING EVALUATOR | - |
| BRK_960_1080 | DEAD (was PASS) | sleeve | 2026-W44 | 0 | 0 | 0 | 0 | - | 9,707 | - | 106.06485074626862 | - | ON TRACK (0 weeks live) [WATCH ONLY: DEAD per S48-LEAD] | LIVE (script) | 104,027 |
| COMB_c3_R | CANDIDATE (was PASS) | sleeve | 2026-W44 | 0 | 0 | 0 | 0 | - | 2,831 | - | 1262.066474820144 | - | ON TRACK (0 weeks live) | LIVE (script) | 22,335 |
| ES_RSI2_t10 | PASS | sleeve | 2026-W44 | 0 | 0 | 0 | 0 | - | 12,559 | - | 1544.535 | - | ON TRACK (0 weeks live) [MERGED into DIPBUY_RSI2_2lot: same exposure, not an independent test] | LIVE (script; no forward trades yet / bars not extended) | 0 |
| GSHORT_t90 | PASS | sleeve | 2026-W44 | 0 | - | - | 0 | - | 5,941 | - | 742.7406451612902 | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: GSHORT needs Set A daily P&L aligned to the extended calendar: not wired | - |
| IBS_t20_n1 | CANDIDATE | sleeve | 2026-W44 | 0 | 0 | 0 | 0 | - | 8,465 | - | 1357.5184905660378 | - | ON TRACK (0 weeks live) | LIVE (script) | 62,192 |
| NM_E_BRK_960_1080 | PASS | sleeve | 2026-W44 | 0 | 0 | 0 | 0 | - | 4,853 | - | 1285.7798054864124 | - | ON TRACK (0 weeks live) | LIVE (script) | 52,014 |
| NM_E_COMB_c3_R | PASS | sleeve | 2026-W44 | 0 | 0 | 0 | 0 | - | 5,118 | - | 5228.203652850883 | - | ON TRACK (0 weeks live) | LIVE (script) | 30,842 |
| NM_E_ES_RSI2_t10 | PASS | sleeve | 2026-W44 | 0 | 0 | 0 | 0 | - | 6,279 | - | 14861.047446187713 | - | ON TRACK (0 weeks live) [MERGED into DIPBUY_RSI2_2lot: same exposure, not an independent test] | LIVE (script; no forward trades yet / bars not extended) | 0 |
| NM_E_GSHORT_t90 | PASS | sleeve | 2026-W44 | 0 | - | - | 0 | - | 2,970 | - | 13606.497415702072 | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: GSHORT needs Set A daily P&L aligned to the extended calendar: not wired | - |
| NM_E_NQ_IBS_t20_n1 | CANDIDATE | sleeve | 2026-W44 | 0 | 0 | 0 | 0 | - | 4,232 | - | 5669.935565963551 | - | ON TRACK (0 weeks live) | LIVE (script) | 31,096 |
| NM_E_NQ_RSI2CC_s20 | PASS | sleeve | 2026-W44 | 0 | 0 | 0 | 0 | - | 5,284 | - | 10719.442546348757 | - | ON TRACK (0 weeks live) | LIVE (script) | 44,602 |
| NM_E_NQ_RSI2C_s20 | PASS | sleeve | 2026-W44 | 0 | 0 | 0 | 0 | - | 5,284 | - | 10719.442546348757 | - | ON TRACK (0 weeks live) [MERGED into DIPBUY_RSI2_2lot: same exposure, not an independent test] | LIVE (script) | 44,602 |
| NM_E_NQ_RSI2T_t10 | PASS | sleeve | 2026-W44 | 0 | 0 | 0 | 0 | - | 4,441 | - | 11261.571312508817 | - | ON TRACK (0 weeks live) | LIVE (script) | 53,615 |
| NM_E_NQ_RSI2_t10 | PASS | sleeve | 2026-W44 | 0 | 0 | 0 | 0 | - | 5,099 | - | 10342.737682700013 | - | ON TRACK (0 weeks live) | LIVE (script) | 37,757 |
| NM_E_ORB_ASIA_15_v1_s60 | PASS | sleeve | 2026-W44 | 0 | - | - | 0 | - | 4,462 | - | 5323.817786101251 | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: no evaluator wired for NM_E_ORB_ASIA_15_v1_s60 (ORB / overnight-drift / unknown variant) | - |
| NM_E_ORB_ASIA_15_v1_s75 | PASS | sleeve | 2026-W44 | 0 | - | - | 0 | - | 4,472 | - | 5336.896655614357 | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: no evaluator wired for NM_E_ORB_ASIA_15_v1_s75 (ORB / overnight-drift / unknown variant) | - |
| NM_E_RTY_IBS_t20_n1 | CANDIDATE | sleeve | 2026-W44 | 0 | 0 | 0 | 0 | - | 3,618 | - | 3982.8634438817066 | - | ON TRACK (0 weeks live) | LIVE (script) | 6,077 |
| NM_E_RTY_RSI2_t10 | PASS | sleeve | 2026-W44 | 0 | 0 | 0 | 0 | - | 8,005 | - | 17221.935768024072 | - | ON TRACK (0 weeks live) | LIVE (script; no forward trades yet / bars not extended) | 0 |
| ON_none_L2 | DEAD (was PASS) | sleeve | 2026-W44 | 0 | - | - | 0 | - | 7,476 | - | 505.0107993966814 | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) [WATCH ONLY: DEAD per S48-LEAD] | NOT EVALUABLE: no evaluator wired for ON_none_L2 (ORB / overnight-drift / unknown variant) | - |
| ON_none_L4 | DEAD (was PASS) | sleeve | 2026-W44 | 0 | - | - | 0 | - | 7,476 | - | 1010.0215987933628 | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) [WATCH ONLY: DEAD per S48-LEAD] | NOT EVALUABLE: no evaluator wired for ON_none_L4 (ORB / overnight-drift / unknown variant) | - |
| ORB_ASIA_15_v1__s60_0.25 | PASS (was CANDIDATE) | sleeve | 2026-W44 | 0 | - | - | 0 | - | 4,069 | - | 4018.7576470593326 | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: no evaluator wired for ORB_ASIA_15_v1__s60_0.25 (ORB / overnight-drift / unknown variant) | - |
| ORB_ASIA_15_v1__s60_0.5 | PASS (was CANDIDATE) | sleeve | 2026-W44 | 0 | - | - | 0 | - | 8,138 | - | 4018.7576470593326 | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: no evaluator wired for ORB_ASIA_15_v1__s60_0.5 (ORB / overnight-drift / unknown variant) | - |
| ORB_ASIA_15_v1__s60_1.0 | PASS (was CANDIDATE) | sleeve | 2026-W44 | 0 | - | - | 0 | - | 16,276 | - | 4018.7576470593326 | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: no evaluator wired for ORB_ASIA_15_v1__s60_1.0 (ORB / overnight-drift / unknown variant) | - |
| ORB_ASIA_15_v1__s75_0.25 | PASS (was CANDIDATE) | sleeve | 2026-W44 | 0 | - | - | 0 | - | 3,864 | - | 4723.534117647571 | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: no evaluator wired for ORB_ASIA_15_v1__s75_0.25 (ORB / overnight-drift / unknown variant) | - |
| ORB_ASIA_15_v1__s75_0.5 | PASS (was CANDIDATE) | sleeve | 2026-W44 | 0 | - | - | 0 | - | 7,727 | - | 4723.534117647571 | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: no evaluator wired for ORB_ASIA_15_v1__s75_0.5 (ORB / overnight-drift / unknown variant) | - |
| ORB_ASIA_15_v1__s75_1.0 | PASS (was CANDIDATE) | sleeve | 2026-W44 | 0 | - | - | 0 | - | 15,455 | - | 4723.534117647571 | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: no evaluator wired for ORB_ASIA_15_v1__s75_1.0 (ORB / overnight-drift / unknown variant) | - |
| ORB_ASIA_30_v1__s60_0.25 | CANDIDATE | sleeve | 2026-W44 | 0 | - | - | 0 | - | 4,001 | - | 4141.419130435292 | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: no evaluator wired for ORB_ASIA_30_v1__s60_0.25 (ORB / overnight-drift / unknown variant) | - |
| ORB_ASIA_30_v1__s60_0.5 | CANDIDATE | sleeve | 2026-W44 | 0 | - | - | 0 | - | 8,001 | - | 4141.419130435292 | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: no evaluator wired for ORB_ASIA_30_v1__s60_0.5 (ORB / overnight-drift / unknown variant) | - |
| ORB_ASIA_30_v1__s60_1.0 | CANDIDATE | sleeve | 2026-W44 | 0 | - | - | 0 | - | 16,003 | - | 4141.419130435292 | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: no evaluator wired for ORB_ASIA_30_v1__s60_1.0 (ORB / overnight-drift / unknown variant) | - |
| RSI2CC_s20 | CANDIDATE (was PASS) | sleeve | 2026-W44 | 0 | 0 | 0 | 0 | - | 2,646 | - | 1789.3398376761188 | - | ON TRACK (0 weeks live) | LIVE (script) | 22,335 |
| RSI2C_s20 | CANDIDATE (was PASS) | sleeve | 2026-W44 | 0 | 0 | 0 | 0 | - | 10,568 | - | 1789.3398376761188 | - | ON TRACK (0 weeks live) [MERGED into DIPBUY_RSI2_2lot: same exposure, not an independent test] | LIVE (script) | 89,204 |
| RSI2T_t10 | CANDIDATE (was PASS) | sleeve | 2026-W44 | 0 | 0 | 0 | 0 | - | 8,882 | - | 1563.820714285714 | - | ON TRACK (0 weeks live) | LIVE (script) | 107,230 |
| RSI2_t10 | PASS | sleeve | 2026-W44 | 0 | 0 | 0 | 0 | - | 10,197 | - | 2039.4457142857145 | - | ON TRACK (0 weeks live) | LIVE (script) | 75,514 |
| RTY_IBS_t20_n1 | DEAD (was CANDIDATE) | sleeve | 2026-W44 | 0 | 0 | 0 | 0 | - | 7,236 | - | 242.601860465117 | - | ON TRACK (0 weeks live) [WATCH ONLY: DEAD per S48-LEAD] | LIVE (script) | 12,154 |
| RTY_RSI2_t10 | DEAD (was PASS) | sleeve | 2026-W44 | 0 | 0 | 0 | 0 | - | 16,009 | - | 712.8872727272733 | - | ON TRACK (0 weeks live) [WATCH ONLY: DEAD per S48-LEAD] | LIVE (script; no forward trades yet / bars not extended) | 0 |
| YM_RSI2_t10 | CANDIDATE | sleeve | 2026-W44 | 0 | - | - | 0 | - | 8,274 | - | 521.8907692307694 | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: no extended 1-min source for YM | - |
| BK1_SETB_sizecredit | CANDIDATE | sizing/lock rule (risk set) | 2026-W44 | 0 | - | - | - | - | - | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) [MERGED into B01_SetB: same exposure, not an independent test] | AWAITING EVALUATOR | - |
| T14_S_s50_t1.5_n14 | CANDIDATE by user ruling 2026-10-25 | trade-modifier (shorts-only bracket) | 2026-W44 | 0 | 0 | 0 | 0 | - | 7,914 | - | 84 | - | ON TRACK (0 weeks live) | LIVE (script) | 47,950 |
| T4.2_Y4 | CANDIDATE | execution change | 2026-W44 | 0 | - | - | 0 | - | 179 | - | 0.0503076242657505 | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | AWAITING EVALUATOR | - |
| DIPBUY_RSI2_2lot | PASS | sleeve | 2026-W44 | 0 | 0 | 0 | 0 | - | 3,091 | - | - | - | ON TRACK (0 weeks live) | LIVE (script) | 14,890 |
| ds3_TB1_ST_k15_P60_N | CANDIDATE | sleeve (NQ intraday trend book, standalone) | 2026-W44 | 0 | - | - | 0 | - | 10,933 | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: no evaluator wired for ds3_TB1_ST_k15_P60_N (ORB / overnight-drift / unknown variant) | - |
| ds3_TB7_ORBNY_k3_P60_N | CANDIDATE | sleeve (NQ intraday trend book, standalone) | 2026-W44 | 0 | - | - | 0 | - | 6,866 | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: no evaluator wired for ds3_TB7_ORBNY_k3_P60_N (ORB / overnight-drift / unknown variant) | - |
| ds3_TB9_RENKO_c2_k1_P60_N | CANDIDATE | sleeve (NQ intraday trend book, standalone) | 2026-W44 | 0 | - | - | 0 | - | 9,418 | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: no evaluator wired for ds3_TB9_RENKO_c2_k1_P60_N (ORB / overnight-drift / unknown variant) | - |
| ds3_TB9_RENKO_c5_k1_A3_N | DEAD | sleeve (NQ intraday trend book, standalone) | 2026-W44 | 0 | - | - | 0 | - | 14,628 | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) [WATCH ONLY: DEAD per S48-LEAD] | NOT EVALUABLE: no evaluator wired for ds3_TB9_RENKO_c5_k1_A3_N (ORB / overnight-drift / unknown variant) | - |
| ds3_TE_TE1B_boll_3m | CANDIDATE | signal (entry into DS2 bracket, standalone book; T-ENTRY) | 2026-W44 | 0 | - | - | 0 | - | 10,405 | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: no bar evaluator wired for family boll | - |
| ds3_TE_TE1B_emax_5m | CANDIDATE | signal (entry into DS2 bracket, standalone book; T-ENTRY) | 2026-W44 | 0 | 0 | 0 | 0 | - | 6,817 | - | - | - | ON TRACK (0 weeks live) | LIVE (script) | 11,371 |
| ds3_TE_TE1_kelt_3m | CANDIDATE | signal (entry into DS2 bracket, standalone book; T-ENTRY) | 2026-W44 | 0 | 0 | 0 | 0 | - | 13,416 | - | - | - | ON TRACK (0 weeks live) | LIVE (script) | -14,081 |
| ds3_TE_TE1_st_10m | PASS | signal (entry into DS2 bracket, standalone book; T-ENTRY) | 2026-W44 | 0 | 0 | 0 | 0 | - | 8,799 | - | - | - | ON TRACK (0 weeks live) [MERGED into ds3_TE_TE6_st10m_n7_m3.0: same exposure, not an independent test] | LIVE (script) | -60,532 |
| ds3_TE_TE3_ice_follow_lb30_q0.95 | CANDIDATE | signal (entry into DS2 bracket, standalone book; T-ENTRY) | 2026-W44 | 0 | - | - | 0 | - | 4,815 | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: no bar evaluator wired for family ice | - |
| ds3_TE_TE3_ice_follow_lb30_q0.99 | CANDIDATE | signal (entry into DS2 bracket, standalone book; T-ENTRY) | 2026-W44 | 0 | - | - | 0 | - | 3,269 | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: no bar evaluator wired for family ice | - |
| ds3_TE_TE6_st10m_n10_m3.0 | PASS | signal (entry into DS2 bracket, standalone book; T-ENTRY) | 2026-W44 | 0 | 0 | 0 | 0 | - | 8,799 | - | - | - | ON TRACK (0 weeks live) [MERGED into ds3_TE_TE6_st10m_n7_m3.0: same exposure, not an independent test] | LIVE (script) | -60,532 |
| ds3_TE_TE6_st10m_n10_m3.5 | CANDIDATE | signal (entry into DS2 bracket, standalone book; T-ENTRY) | 2026-W44 | 0 | 0 | 0 | 0 | - | 5,304 | - | - | - | ON TRACK (0 weeks live) | LIVE (script) | -60,532 |
| ds3_TE_TE6_st10m_n14_m3.0 | PASS | signal (entry into DS2 bracket, standalone book; T-ENTRY) | 2026-W44 | 0 | 0 | 0 | 0 | - | 6,980 | - | - | - | ON TRACK (0 weeks live) [MERGED into ds3_TE_TE6_st10m_n7_m3.0: same exposure, not an independent test] | LIVE (script) | -60,532 |
| ds3_TE_TE6_st10m_n7_m3.0 | PASS | signal (entry into DS2 bracket, standalone book; T-ENTRY) | 2026-W44 | 0 | 0 | 0 | 0 | - | 8,749 | - | - | - | ON TRACK (0 weeks live) | LIVE (script) | -60,629 |
| ds3_TE_TE7_boll3m_n20_m1.5 | CANDIDATE | signal (entry into DS2 bracket, standalone book; T-ENTRY) | 2026-W44 | 0 | - | - | 0 | - | 10,602 | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: no bar evaluator wired for family boll | - |
| ds3_TE_TE7_boll3m_n20_m2.0 | CANDIDATE | signal (entry into DS2 bracket, standalone book; T-ENTRY) | 2026-W44 | 0 | - | - | 0 | - | 10,405 | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) [MERGED into ds3_TE_TE1B_boll_3m: same exposure, not an independent test] | NOT EVALUABLE: no bar evaluator wired for family boll | - |
| ds3_TE_TE7_boll3m_n30_m1.5 | CANDIDATE | signal (entry into DS2 bracket, standalone book; T-ENTRY) | 2026-W44 | 0 | - | - | 0 | - | 11,366 | - | - | - | ON TRACK (0 weeks live; AWAITING EVALUATOR) | NOT EVALUABLE: no bar evaluator wired for family boll | - |
| ds3_TE_TE7_emax5m_f20_s50 | CANDIDATE | signal (entry into DS2 bracket, standalone book; T-ENTRY) | 2026-W44 | 0 | 0 | 0 | 0 | - | 6,817 | - | - | - | ON TRACK (0 weeks live) [MERGED into ds3_TE_TE1B_emax_5m: same exposure, not an independent test] | LIVE (script) | 11,371 |
| ds3_TE_TE7_emax5m_f30_s50 | CANDIDATE (was PASS) | signal (entry into DS2 bracket, standalone book; T-ENTRY) | 2026-W44 | 0 | 0 | 0 | 0 | - | 7,142 | - | - | - | ON TRACK (0 weeks live) | LIVE (script) | -60,726 |
| ds3_TE_TE7_kelt3m_n14_m1.0 | PASS | signal (entry into DS2 bracket, standalone book; T-ENTRY) | 2026-W44 | 0 | 0 | 0 | 0 | - | 16,863 | - | - | - | ON TRACK (0 weeks live) | LIVE (script) | 34,016 |
| ds3_TE_TE7_kelt3m_n14_m1.5 | CANDIDATE | signal (entry into DS2 bracket, standalone book; T-ENTRY) | 2026-W44 | 0 | 0 | 0 | 0 | - | 8,453 | - | - | - | ON TRACK (0 weeks live) | LIVE (script) | -13,888 |
| ds3_TE_TE7_kelt3m_n20_m1.0 | CANDIDATE | signal (entry into DS2 bracket, standalone book; T-ENTRY) | 2026-W44 | 0 | 0 | 0 | 0 | - | 17,235 | - | - | - | ON TRACK (0 weeks live) | LIVE (script) | 33,725 |
| ds3_TE_TE7_kelt3m_n20_m1.5 | CANDIDATE | signal (entry into DS2 bracket, standalone book; T-ENTRY) | 2026-W44 | 0 | 0 | 0 | 0 | - | 13,416 | - | - | - | ON TRACK (0 weeks live) [MERGED into ds3_TE_TE1_kelt_3m: same exposure, not an independent test] | LIVE (script) | -14,081 |
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

Per-cell frozen expectation (WF / L8W / IS) and parameters: `autopilot/forward/series/PAPERALL_CELLS.json`.

Removed from the register (kept in the json): TEST_dryrun

## DS3 reference lines (D3L; expectation only, selection-inflated: best of a 191-cell search, weight the 2x-cost figure)

| line | WF mean/wk | WF SD | note |
|---|---|---|---|
| ds3 TE7_kelt3m_n14_m1.0 | 16,838 | 59,572 | 26.8 tr/wk, win 52%, avg win 11,302 / loss -10,858, 2x-cost mean 12,395 |
| ds3 TE6_st10m_n7_m3.0 | 9,130 | 35,530 | 12.2 tr/wk, win 53%, 2x-cost 6,716 |
| ds3 TE7_emax5m_f30_s50 | 7,142 | 34,206 | 11.8 tr/wk, win 53%, 2x-cost 4,257 |
| DS3 3-book portfolio (kelt + st10m_n7 + TB7_ORBNY_k3_P60_N, monthly risk parity, 27 contracts) | 28,820 | 72,379 | forward realised needs the exact TB7 series: not evaluable yet |
| DS2 10/10/7 alone | 25,840 | 106,637 | comparison line |

Evaluation basis for the three bar-based books: x_te replay on the extended NQ tape with natural fills and a closed-trade lock approximation (the expectation is the direct-L2 series with S10x1 + XJ and exact 1-s locks), so a small execution gap is expected before any verdict is read. TE7_boll / TE3 ice / TB books / TF1 are execution-layer or not wired and show NOT EVALUABLE.


## DS3 live (Sim leader; DS3 file) - realised vs paper_all expectation, per book and total

DS3 file(s): 1; 4 grouped trades; last exit 2026-10-26 16:12 ET. Expectations are the paper_all values at the registered 10 lots (KB 16,863/wk SD 59,362; SM 8,749/wk SD 35,698), scaled by live median qty/10 = **x1.00** (median qty 10). Total SD assumes independent books (sqrt of summed variances; actual correlation >0 makes the true SD larger). Expectations are selection-inflated (best of 191 cells); the 2x-cost mean is 12,395 (KB) / 6,716 (SM).

Start week 2026-W44 (first entry 10-26 14:03 ET); weeks count once complete (Friday 17:00 ET). Verdict: PROMOTE >=6 wks z>=-1 right sign; RETIRE >=8 wks z<-2; BEHIND z<-1.

| book | week | complete | trades | exp trades | realised $ | expected $ | per trade real | z (week) | cum weeks | cum z | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|
| KB | 2026-W44 | no | 4 | 26.8 | 240 | 16,863 | 60 | -0.28 | 0 | - | in progress |
| SM | 2026-W44 | no | 0 | 12.2 | 0 | 8,749 | - | - | 0 | - | in progress |
| TOTAL | 2026-W44 | no | 4 | 39.0 | 240 | 25,612 | 60 | -0.37 | 0 | - | in progress |


## Live stop-join rate and slip (Set A stop exits; file `StratTrades_DualStrat2_<acct>.csv`)

| item | live | replay | note |
|---|---|---|---|
| join rate (stop-join fills / attempts) | 8/20 = 0.40 exact 95% CI [0.19, 0.64] | 0.78 | attempts = joined + fell back to market; broker-rejected join attempts (1) counted separately; incl. rejects 8/21 |
| replay inside live CI? | NO | | |
| stop-exit slip vs nominal, all stop exits | 2.45 pts worse (n=21; 95% CI 1.01..3.89) | 0.52 pts worse | nominal = entry avg -/+ 60 pts; live earlier read 2.01 on n=18 |
| stop-exit slip, join-filled | -0.52 pts worse (n=8; 95% CI -1.23..0.19) | - | |
| stop-exit slip, market fallback | 4.46 pts worse (n=12; 95% CI 2.80..6.13) | 1.74 pts worse | |
| replay on the same 17 live triggers (10-20..23 tape, exec_engine_l2, true trigger) | 11/17 = 0.65 exact 95% CI [0.38, 0.86] (trade-through rule 9/17) | 0.78 all-history | per-attempt outcome agreement 14/17 (traced 11/11); see JOIN_RECON.md section 5 |
| entry slip vs mid (tape) | 1.83 ticks per lot (0.46 pts; n=29 ST/HM 14-lot trades; t95 [0.98, 2.69]) vs the tape mid at each slice's order time (exchange clock = log stamp - 27 ms); vs the single mid at the trigger minute -0.41 pts [-2.45, 1.63] (includes the 26 s stagger drift) | replay on the same slices 2.12 ticks per lot; replay expectation ST 1.90 / HM 1.77 ticks (S14x1) | computed 2026-10-25 by join_recon2 (tape mids now on disk); LIVE_RECON per-trade column uses the 1-min bar open |

Weekly (official/info) join and slip:

| week | stop exits | joined | fell back | rejected | join rate | slip pts worse |
|---|---|---|---|---|---|---|
| 2026-W43 | 18 | 8 | 9 | 1 | 0.47 | 2.01 |
| 2026-W44 | 3 | 0 | 3 | 0 | 0.00 | 5.10 |

Other forward shadows (DS15, S130, P30/P36, ...) remain in LEAGUE.md / ap_m2_paperall.py. Weekly L2 extension check: tape 2026-10-23 20:59:00 UTC (a Saturday 06:00Z run extends it; nothing is bought here).

## Forward TH-cut counterfactual (user job 3, 2026-10-25; code forward/ap_forward_th.py; full method and caveats REPORT_FORWARD_TH.md)

Object: every live ST trade closed by the TH LOSS-side cut (exit name ends LossExit), replayed WITHOUT the cut on the real mbp-10 tape (exec_engine_l2, live entry as anchor, 60/60 bracket, 16:55 ET flatten, stop exits through the live stop-join model XJ3). Paired difference d = cut P&L - no-cut P&L per cut trade (+ = TH helped). Weeks start Sunday 18:00 ET; W42 is partial (trading days 10-13..10-16), W43 informational. Only complete rows from 10-13 on; days without mbp-10 on disk are PENDING_L2 (never imputed).

Identification: exitName ends 'LossExit' (loss-side TH cut; ProfitExit = profit-side cut) in data/live/StratTrades_*.csv, trading day >= 20261013 (entries from 2026-10-12 18:00 ET). Cuts by file/book: DualStrat2 file HM CUT_LOSS n=3; DualStrat2 file HM CUT_PROFIT n=1; DualStrat2 file ST CUT_LOSS n=16; DualStrat2 file ST CUT_PROFIT n=6; DualStrat2 file WT CUT_LOSS n=9; Sim file HM CUT_LOSS n=11; Sim file ST CUT_LOSS n=12; Sim file WT CUT_LOSS n=17; pair file (DualStrat) ST CUT_LOSS n=46. Trace logs (nt8log_trace.*, nt8log_latest): 5 files, 219 LossExit lines (trace window ends before the 10-23 TH-on period; the CSV is the identification of record).

| week | ST loss-cuts | replayed | pending L2 | mean d pts/trade | mean d $/trade | 95% CI $/trade (session-block bootstrap, 10,000) | d $ in week | MDE80 $ for this week alone | P(d>0) | DualStrat2 file n / d $ | pair file n / d $ |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 2026-W42 (partial, from 10-13; informational) | 46 | 46 | 0 | +3.03 | +485 | [-2,247, +3,307] | +22,314 | 152,801 | 0.64 | - | 46 / +22,314 |
| 2026-W43 (informational) | 4 | 4 | 0 | +34.88 | +5,581 | [+4,942, +6,411] | +22,325 | 45,058 | 1.00 | 4 / +22,325 | - |
| 2026-W44 | 24 | 0 | 24 | - | - | - | - | 22,529 | - | - | - |
| **cumulative (10-13 on)** | 50 | 50 | 57 | +5.58 | +893 | [-1,897, +3,611] | +44,639 | 107,646/wk | 0.74 | | |

Cumulative ST loss-cut: n=50 cuts in 9 replayed trading days; mean d +5.58 pts/trade (95% CI [-11.80, +22.29]) = +893 $/trade (CI [-1,897, +3,611]); +24,799 $/5-day week (total +44,639); cut better in 76% of trades; SD of d 50.3 pts. **Detectable effect (80% power, 5% two-sided, = 2.8 x bootstrap SE): 24.4 pts/trade = $3,942/trade = $107,646/wk.** A null here means 'could not have seen less than that'; with a handful of cuts per week the weekly MDE is far larger still.

| class (informational except ST loss) | n | mean d pts | mean d $ | 95% CI $/trade | $/5-day wk | MDE80 $/trade |
|---|---|---|---|---|---|---|
| ST LOSS ALL | 50 | +5.58 | +893 | [-1,897, +3,611] | +24,799 | 3,942 |
| ST LOSS DualStrat2 file | 4 | +34.88 | +5,581 | [+4,942, +6,411] | +22,325 | 1,119 |
| ST LOSS pair file | 46 | +3.03 | +485 | [-2,247, +3,307] | +27,892 | 4,042 |
| ST LOSS second file | 0 | - | - | - | - | - |
| HM LOSS | 3 | -9.66 | -1,545 | [-11,435, +8,240] | -4,635 | 13,122 |
| WT LOSS | 7 | -10.32 | -1,445 | [-4,680, +3,155] | -10,115 | 5,837 |
| ST PROFIT CUT | 4 | +19.03 | +3,045 | [-6,048, +12,138] | +12,180 | 12,749 |
| HM PROFIT CUT | 0 | - | - | - | - | - |

### Forward ST loss-cut counterfactual split by session and cut size (added 2026-10-26, USER ORDER; next to the G1 replay of the same live ST rule on the ST entry list, 2023-02..2026-10, DS3_TH_G1_LIVEJOIN.json)

session = entry session of the cut trade (Asia 18-02, London 02-09:30, NY 09:30-18 ET, from the session-block label); cut-size bucket = points lost at the cut vs the live entry price (<15, 15-25, >25 pts); ST loss cuts only, replayed rows only; d = cut - no-cut (+ = TH helped)

| group | live n cuts | live mean d pts [95% CI] | live mean d $/cut [CI] | live MDE80 pts | would hit target / stop | G1 replay n cuts | G1 replay EV/cut pts (0.78-style fixed 1.01 stop cost) | G1 replay EV/cut pts (live-join profile) | G1 replay would hit target |
|---|---|---|---|---|---|---|---|---|---|
| Asia | 22 | +9.17 [-11.9, +26.8] | +1,467 [-1,847, +4,233] | 27.6 | 18% / 82% | 1392 | -1.04 | -1.03 | 0.29 |
| London | 17 | +7.14 [-17.9, +28.6] | +1,142 [-2,940, +4,567] | 33.3 | 24% / 76% | 1264 | -1.13 | -1.44 | 0.31 |
| NY | 11 | -4.00 [-37.7, +28.2] | -640 [-5,986, +4,479] | 47.6 | 36% / 64% | 2377 | -1.25 | -1.74 | 0.27 |
| <15 pts lost | 4 | -13.11 [-71.7, +45.5] | -2,098 [-11,475, +7,280] | 81.3 | 50% / 50% | 1030 | -0.51 | -0.80 | 0.36 |
| 15-25 pts lost | 24 | +10.71 [-13.6, +34.6] | +1,713 [-2,185, +5,538] | 34.6 | 25% / 75% | 2184 | -2.99 | -3.28 | 0.34 |
| >25 pts lost | 22 | +3.38 [-14.3, +19.1] | +541 [-2,247, +3,055] | 23.6 | 18% / 82% | 1819 | +0.67 | +0.32 | 0.19 |

Live groups with a handful of cuts have MDEs of tens of points: they cannot be compared with the replay at better than "consistent / not inconsistent". Replay by-cut-size rows for the other entries: DS3_TH_G1.md addendum.


Knock-on caveat (informational, not the paired test): 30 of the 50 replayed ST cuts are followed by a LIVE same-book entry before the no-cut trade would have ended, i.e. without the cut the book would have been busy and that later trade would not exist. Sequence view per file (A = live, B = no TH, later entries inside a no-cut holding dropped): DualStrat2 file: 4 kept cuts d +22,325 + 1 dropped live trades +3,419 = A-B +25,744 $; Sim file: 0 kept cuts d +0 + 0 dropped live trades +0 = A-B +0 $; pair file (DualStrat): 26 kept cuts d +5,474 + 27 dropped live trades -11,382 = A-B -5,909 $.

Second account: no StratTrades file for a second account exists in data/live (the Sim files hold no ST loss-cut in the window), so there is no second-file row; it appears automatically when such a file arrives. Bootstrap basis: trading-day x session (Asia 18-02, London 02-09:30, NY 09:30-18 ET) blocks, 10,000 draws; rows with fewer than 5 blocks use trade-level resampling (flagged in FORWARD_TH.json).

Machinery check on the live trades that were NOT cut (same replay, n=120): outcome class agrees in 119/120 (live targets reproduced as targets 65/66, live stops as stops 54/54); stop-exit pts live -61.31 vs replay XJ3 -61.36.
