# DAYMASK_RANK - three screen rankings per session (W-DAYMASK, orders 1722Z + 1731Z), refreshed 2026-11-19 02:07Z

Screen level, 1 lot, $4.84 round trip in the points, last 26 weeks to the data end (L6M) and 13 weeks (L3M); EQUAL RISK (R = points / the cell stop in points; R/week); ranked by (red prior years, then min(L6M R/week, weakest prior-year R/week)); cells need L6M > 0 and >= 100 trades under THAT variant.
(a) BARE: no account rule. (b) OWN-STOP: stack-independent; no new entries for the rest of the 17:00-ET trading day once the cell itself is down 2 stops on the day (1.5 and 3 stops shown as neighbours). THIS ranking carries the shortlist. (c) CURRENT-STACK MASK: entries blocked while today's JL3 stack has >= 22 closes and day P&L <= -$4,200 live (JL3 history, code/th_grid/gday.py); valid for ADDING a book to today's stack only; not valid for a rebuilt stack; information, never the sole reason to shortlist or drop.
RE-RUN PROGRESS: 2026-11-18T21:52:27Z p1real done 5425 of 5425 pairs, 15820 s (plus every new grid job since 17:30Z carries (b)/(c) by itself).
COVERAGE CAUTION: (b) and (c) exist only for the (row, module) result files already re-run with GL_OWNSTOP / GL_ACCT (the bare top-4,000 cells per session + candidates + shortlist, started 17:28Z); the bare table covers every scored cell. Until the whole grid has been re-run the (b)/(c) tables are biased to cells that were already strong on bare. Cells scored per table are shown in each heading.

## Asia
Cells passing per session (a / b / c): Asia 4000 / 4000 / 4000; London 4000 / 4000 / 4000; NYAM 4000 / 4000 / 4000; NYPM 4000 / 4000 / 4000


### (a) BARE  (scored on exactly the same result files as (b) and (c); cells passing: 4000, capped at 4,000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | cusum_40 | momentum_rsi.mom_native {"len": 14, "lvl": 55} | plain60/60 | +624 | -45 | +0.40 | 608 | ok/ok/ok | bare only (not positive on own-stop) |
| 2 | dib_240 | momentum_mvote.v3of5_native {"scale": 1.0, "thr": 0.25} | plain60/60 | +616 | +1066 | +0.39 | 777 | ok/ok/ok | bare only (not positive on own-stop) |
| 3 | tm180 | levels_vwap.break_native {"n": 3, "k": 0.5} | plain60/60 | +605 | +1164 | +0.39 | 562 | ok/ok/ok | strong on (b) too |
| 4 | vib_3500 | momentum_stoch.zone_break_native {"len": 14, "lvl": 70} | sym15u | +561 | -724 | +0.36 | 313 | ok/ok/ok | strong on (b) too |
| 5 | drb_2000 | levels_piv_cama.reject_native {"tol": 0.5, "conf": "body"} | plain60/60 | +764 | +351 | +0.49 | 573 | AMBER/ok/ok | bare only (not positive on own-stop) |
| 6 | tsf_10_60 | tape_delta.follow_native {"L": 900, "z": 1.0} | sym15u | +534 | +291 | +0.34 | 252 | ok/ok/ok | bare only (not positive on own-stop) |
| 7 | cusum_10 | momentum_cci.brk {"len": 30, "lvl": 200} | plain60/60 | +632 | +93 | +0.40 | 806 | ok/AMBER/ok | bare only (not positive on own-stop) |
| 8 | time_m_7 | xmarket_rty.confirm {"w": 30} | plain60/60 | +601 | +126 | +0.38 | 444 | ok/ok/ok | strong on (b) too |
| 9 | tick_300 | momentum_mvote.v3of5 {"scale": 1.0, "thr": 0.25} | plain60/60 | +502 | +600 | +0.32 | 483 | ok/ok/ok | strong on (b) too |
| 10 | tsf_5_50 | trend_libstack.ema_hold {"len": 13, "hold": 3} | sym15u | +610 | +507 | +0.39 | 297 | AMBER/ok/ok | bare only (not positive on own-stop) |

### (b) OWN-STOP (2 stops; 1.5 and 3 shown as neighbours)  (cells passing: 4000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | mrenko_20 | momentum_er.trend_z {"len": 10, "thr": 0.4} | plain60/60 | +870 | +360 | +0.56 | 432 | ok/ok/AMBER | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |
| 2 | tsf_5_100 | structure_breakout.brk {"n": 40, "buf": 0.0} | sym15u | +670 | -804 | +0.43 | 236 | ok/ok/ok | L6M @1.5 stops +706 / @3 stops +248 |
| 3 | vib_3500 | momentum_stoch.zone_break_native {"len": 14, "lvl": 70} | sym15u | +713 | -429 | +0.46 | 293 | AMBER/AMBER/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops +749 |
| 4 | tsf_5_100 | bands_donchian.break_native {"clk": 5, "buf": 0.0} | sym15u | +738 | -862 | +0.47 | 260 | AMBER/AMBER/ok | L6M @1.5 stops +620 / @3 stops +386 |
| 5 | time_m_7 | xmarket_rty.confirm {"w": 30} | plain60/60 | +634 | +74 | +0.41 | 386 | ok/ok/ok | L6M @1.5 stops +634 / @3 stops +598 |
| 6 | cusum_40 | momentum_rsi.mom_native {"len": 21, "lvl": 55} | plain60/60 | +562 | -75 | +0.36 | 470 | ok/ok/ok | L6M @1.5 stops +562 / @3 stops <=0 or <100 tr |
| 7 | tsf_5_100 | levels_fib5.break {"n": 3, "k": 0.5} | sym15u | +548 | -417 | +0.35 | 295 | ok/ok/ok | L6M @1.5 stops +502 / @3 stops +435 |
| 8 | mrenko_20 | momentum_er.trend {"len": 10, "thr": 0.4} | plain60/60 | +603 | +34 | +0.39 | 428 | ok/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |
| 9 | tsf_5_100 | bands_donchian.break {"n": 40, "buf": 0.0} | sym15u | +670 | -804 | +0.43 | 236 | ok/AMBER/AMBER | L6M @1.5 stops +706 / @3 stops +248 |
| 10 | tsf_10_30 | pullback_brick.brick {"k": 2, "m": 1} | sym15u | +511 | -327 | +0.33 | 222 | ok/ok/ok | L6M @1.5 stops +259 / @3 stops +400 |

### (c) CURRENT-STACK MASK (valid for ADDING a book to today's stack only; not valid for a rebuilt stack)  (cells passing: 4000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | cusum_40 | momentum_rsi.mom_native {"len": 14, "lvl": 55} | plain60/60 | +723 | +62 | +0.46 | 604 | ok/AMBER/ok | depends on today's stack |
| 2 | tm180 | levels_vwap.break_native {"n": 3, "k": 0.5} | plain60/60 | +626 | +1202 | +0.40 | 556 | ok/ok/ok | also positive on (b) |
| 3 | vib_3500 | momentum_stoch.zone_break_native {"len": 14, "lvl": 70} | sym15u | +551 | -724 | +0.35 | 312 | ok/ok/ok | also positive on (b) |
| 4 | dib_2000 | momentum_rsi.mom {"len": 21, "lvl": 55} | plain60/60 | +537 | -340 | +0.34 | 727 | ok/ok/ok | also positive on (b) |
| 5 | tsf_10_60 | tape_delta.follow_native {"L": 900, "z": 1.0} | sym15u | +535 | +291 | +0.34 | 251 | ok/ok/ok | depends on today's stack |
| 6 | cusum_10 | momentum_cci.brk {"len": 30, "lvl": 200} | plain60/60 | +622 | +97 | +0.40 | 799 | ok/ok/ok | depends on today's stack |
| 7 | time_m_7 | xmarket_rty.confirm {"w": 30} | plain60/60 | +693 | +194 | +0.44 | 440 | ok/AMBER/AMBER | also positive on (b) |
| 8 | tick_300 | momentum_mvote.v3of5 {"scale": 1.0, "thr": 0.25} | plain60/60 | +525 | +600 | +0.34 | 482 | ok/ok/ok | also positive on (b) |
| 9 | tsf_5_50 | trend_libstack.ema_hold {"len": 13, "hold": 3} | sym15u | +610 | +507 | +0.39 | 297 | AMBER/ok/ok | depends on today's stack |
| 10 | vsess_30 | bands_atrchan.break_ema_native {"clk": 5, "k": 1.5} | plain60/60 | +551 | +122 | +0.35 | 182 | ok/ok/ok | also positive on (b) |

## London

### (a) BARE  (scored on exactly the same result files as (b) and (c); cells passing: 4000, capped at 4,000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | med_bmsgq_B080 | tape_libvol.vwmacd {"f": 8, "s": 17} | sym15u | +783 | -106 | +0.50 | 240 | ok/ok/ok | strong on (b) too |
| 2 | vol_2600 | levels_fib5.retest_native {"M": 10, "tol": 0.5} | plain60/60 | +791 | +384 | +0.51 | 611 | ok/ok/ok | bare only (not positive on own-stop) |
| 3 | med_rngor_B200 | trend_ma_hma.cross {"len": 34, "width": 4, "hyst": 0.0} | sym15u | +736 | -344 | +0.47 | 260 | ok/ok/ok | strong on (b) too |
| 4 | bmsg_B320 | barnative_speed.burst_go {"len": 10, "r": 0.25} | sym15u | +702 | +131 | +0.45 | 287 | ok/ok/ok | strong on (b) too |
| 5 | entropy_B200 | book_micro.fade_sm {"L": 100, "z": 1.5, "sm": 3} | sym15u | +852 | +899 | +0.55 | 255 | ok/AMBER/AMBER | strong on (b) too |
| 6 | dlt_70 | levels_zones.reject {"tol": 1.0, "conf": "body"} | plain60/60 | +964 | -521 | +0.62 | 225 | ok/AMBER/AMBER | bare only (not positive on own-stop) |
| 7 | bmsg_B320 | barnative_speed.burst_go {"len": 10, "r": 0.25} | sym15u | +666 | -175 | +0.43 | 140 | ok/ok/ok | strong on (b) too |
| 8 | ha_micro_B200 | trend_ma_hma.cross_native {"len": 34, "width": 1.0, "ratio": 3} | plain60/60 | +802 | +520 | +0.51 | 260 | ok/AMBER/ok | bare only (not positive on own-stop) |
| 9 | ha_qmid_B200 | trend_ma_hma.cross_native {"len": 34, "width": 1.0, "ratio": 3} | plain60/60 | +743 | +460 | +0.48 | 257 | ok/ok/ok | bare only (not positive on own-stop) |
| 10 | kal_bmsg_B200 | trend_ma_hma.cross {"len": 21, "width": 2, "hyst": 0.0} | sym15u | +914 | +1528 | +0.59 | 260 | AMBER/AMBER/AMBER | bare only (not positive on own-stop) |

### (b) OWN-STOP (2 stops; 1.5 and 3 shown as neighbours)  (cells passing: 4000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | t3_entropy_B080 | tape_libvol.vwmacd {"f": 8, "s": 17} | sym15u | +1034 | +62 | +0.66 | 225 | AMBER/AMBER/ok | L6M @1.5 stops +1034 / @3 stops <=0 or <100 tr |
| 2 | med_bmsgq_B080 | tape_libvol.vwmacd {"f": 8, "s": 17} | sym15u | +861 | -83 | +0.55 | 230 | ok/ok/AMBER | L6M @1.5 stops +861 / @3 stops +783 |
| 3 | bmsg_B320 | barnative_speed.burst_go {"len": 10, "r": 0.25} | sym15u | +687 | +276 | +0.44 | 269 | ok/ok/ok | L6M @1.5 stops +687 / @3 stops +877 |
| 4 | bmsg_B500 | book_pslope.fade_sm {"L": 100, "z": 1.5, "sm": 3} | sym15u | +898 | -1732 | +0.58 | 229 | AMBER/ok/AMBER | L6M @1.5 stops +898 / @3 stops <=0 or <100 tr |
| 5 | tsf_10_120 | xmarket_commod.against_CL {"w": 1, "thr": 1.0} | sym15u | +677 | +1721 | +0.43 | 175 | ok/ok/ok | L6M @1.5 stops +799 / @3 stops <=0 or <100 tr |
| 6 | t3_bmsg_B200 | trend_macd.signal_native {"len": 12, "width": 0.05} | sym15u | +825 | +379 | +0.53 | 242 | ok/AMBER/ok | L6M @1.5 stops +825 / @3 stops <=0 or <100 tr |
| 7 | cusum_28 | trend_macd.hist_turn_native {"len": 26, "width": 0.03} | plain60/60 | +744 | +972 | +0.48 | 364 | ok/ok/ok | L6M @1.5 stops +370 / @3 stops +431 |
| 8 | t3_volor_B200 | trend_hma_turn.turn {"len": 60, "width": 0.08} | sym15u | +666 | -36 | +0.43 | 232 | ok/ok/ok | L6M @1.5 stops +666 / @3 stops +702 |
| 9 | entropy_B200 | book_micro.fade_sm {"L": 100, "z": 1.5, "sm": 3} | sym15u | +701 | +653 | +0.45 | 238 | ok/ok/ok | L6M @1.5 stops +701 / @3 stops <=0 or <100 tr |
| 10 | bmsgq_B080 | trend_psar.flip {"af0": 0.02, "step": 0.03, "max": 0.2} | sym15u | +627 | +78 | +0.40 | 245 | ok/ok/ok | L6M @1.5 stops +627 / @3 stops +825 |

### (c) CURRENT-STACK MASK (valid for ADDING a book to today's stack only; not valid for a rebuilt stack)  (cells passing: 4000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | bmsg_B320 | barnative_speed.burst_go {"len": 10, "r": 0.25} | sym15u | +1175 | +593 | +0.75 | 236 | ok/AMBER/AMBER | also positive on (b) |
| 2 | ha_sessrng_B080 | xmarket_rates.with_ZB {"w": 5, "thr": 1.0} | sym15u | +954 | +1179 | +0.61 | 186 | AMBER/ok/ok | depends on today's stack |
| 3 | kal_sessrng_B080 | xmarket_rates.with_ZB {"w": 5, "thr": 1.0} | sym15u | +954 | +1179 | +0.61 | 186 | AMBER/ok/ok | depends on today's stack |
| 4 | med_sessrng_B080 | xmarket_rates.with_ZB {"w": 5, "thr": 1.0} | sym15u | +954 | +1179 | +0.61 | 186 | AMBER/ok/ok | depends on today's stack |
| 5 | t3_sessrng_B080 | xmarket_rates.with_ZB {"w": 5, "thr": 1.0} | sym15u | +954 | +1179 | +0.61 | 186 | AMBER/ok/ok | depends on today's stack |
| 6 | typ_sessrng_B080 | xmarket_rates.with_ZB {"w": 5, "thr": 1.0} | sym15u | +954 | +1179 | +0.61 | 186 | AMBER/ok/ok | depends on today's stack |
| 7 | rngor_B320 | book_queue.follow_sm {"thr": 0.3, "min": 3, "sm": 3} | sym15u | +704 | +434 | +0.45 | 122 | ok/ok/ok | also positive on (b) |
| 8 | t3_bmsg_B200 | trend_supertrend.native {"len": 14, "width": 3.0} | sym15u | +970 | +1287 | +0.62 | 228 | AMBER/AMBER/ok | also positive on (b) |
| 9 | med_bmsgq_B080 | tape_libvol.vwmacd {"f": 8, "s": 17} | sym15u | +677 | -374 | +0.43 | 189 | ok/ok/ok | also positive on (b) |
| 10 | dlt_70 | levels_zones.reject {"tol": 1.0, "conf": "body"} | plain60/60 | +674 | -435 | +0.43 | 182 | ok/ok/ok | depends on today's stack |

## NYAM

### (a) BARE  (scored on exactly the same result files as (b) and (c); cells passing: 4000, capped at 4,000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | med_dltor_B200 | structure_level.round_break {"grid": 100, "buf": 0.25} | sym15u | +2402 | +954 | +1.54 | 416 | AMBER/AMBER/ok | bare only (not positive on own-stop) |
| 2 | kal_micro_B200 | pullback_ema.count {"len": 10, "n": 2} | sym15u | +1967 | +206 | +1.26 | 379 | AMBER/ok/ok | strong on (b) too |
| 3 | med_micro_B080 | levels_round.break {"n": 2, "k": 0.25} | sym15u | +1526 | +1131 | +0.98 | 485 | ok/ok/ok | bare only (not positive on own-stop) |
| 4 | t3_dltor_B080 | levels_round.break {"n": 2, "k": 0.25} | sym15u | +1711 | +719 | +1.10 | 508 | ok/ok/ok | strong on (b) too |
| 5 | med_bmsgq_B200 | tape_stoprun.fade {"N": 10, "k": 0.0} | sym15u | +1723 | +1816 | +1.10 | 497 | ok/ok/ok | bare only (not positive on own-stop) |
| 6 | kal_qmid_B080 | bands_regchan.break_stderr_native {"clk": 20, "k": 2.5} | sym15u | +1956 | +1097 | +1.25 | 316 | AMBER/AMBER/ok | strong on (b) too |
| 7 | trend_20 | levels_vwap.reject {"tol": 1.0, "conf": "body"} | sym15u | +1707 | -264 | +1.09 | 340 | ok/AMBER/ok | strong on (b) too |
| 8 | ha_micro_B080 | book_ofi.follow_native {"L": 3600, "z": 2.0} | sym15u | +1685 | +1174 | +1.08 | 358 | ok/AMBER/ok | strong on (b) too |
| 9 | kal_micro_B080 | book_ofi.follow_native {"L": 3600, "z": 2.0} | sym15u | +1685 | +1174 | +1.08 | 358 | ok/AMBER/ok | strong on (b) too |
| 10 | kal_qmid_B080 | book_ofi.follow_native {"L": 3600, "z": 2.0} | sym15u | +1685 | +1174 | +1.08 | 358 | ok/AMBER/ok | strong on (b) too |

### (b) OWN-STOP (2 stops; 1.5 and 3 shown as neighbours)  (cells passing: 4000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | trend_20 | levels_vwap.break_native {"n": 2, "k": 0.25} | sym15u | +2161 | +1183 | +1.39 | 258 | AMBER/ok/ok | L6M @1.5 stops +2298 / @3 stops <=0 or <100 tr |
| 2 | trb_2000 | levels_vwap.break {"n": 3, "k": 0.5} | sym15u | +1967 | -1066 | +1.26 | 242 | ok/ok/ok | L6M @1.5 stops +1725 / @3 stops +1714 |
| 3 | t3_qmid_B200 | bands_envelope.break_ema {"n": 10, "pct": 0.05} | sym15u | +1627 | +1246 | +1.04 | 347 | ok/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops +991 |
| 4 | med_volor_B200 | structure_level.round_break {"grid": 100, "buf": 0.25} | sym15u | +1842 | +959 | +1.18 | 289 | ok/ok/ok | L6M @1.5 stops +900 / @3 stops <=0 or <100 tr |
| 5 | t3_dltor_B080 | levels_round.break {"n": 2, "k": 0.25} | sym15u | +2133 | +679 | +1.37 | 380 | AMBER/AMBER/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |
| 6 | t3_micro_B200 | bands_envelope.break_ema {"n": 10, "pct": 0.05} | sym15u | +1552 | +1171 | +1.00 | 345 | ok/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops +985 |
| 7 | cusum_20 | book_ofi.follow {"L": 200, "z": 2.0} | plain60/60 | +2026 | +333 | +1.30 | 496 | AMBER/AMBER/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops +579 |
| 8 | vrb_1200 | xmarket_fast.revert_ES {"w": 60, "thr": 2.0} | sym15u | +1549 | +422 | +0.99 | 305 | ok/ok/ok | L6M @1.5 stops +1530 / @3 stops +1671 |
| 9 | trend_14 | levels_vwap.retest {"M": 10, "tol": 0.5} | sym15u | +1566 | +354 | +1.00 | 248 | ok/ok/ok | L6M @1.5 stops +1562 / @3 stops +1096 |
| 10 | kal_micro_B200 | pullback_ema.count {"len": 10, "n": 2} | sym15u | +1389 | +271 | +0.89 | 318 | ok/ok/ok | L6M @1.5 stops +1501 / @3 stops <=0 or <100 tr |

### (c) CURRENT-STACK MASK (valid for ADDING a book to today's stack only; not valid for a rebuilt stack)  (cells passing: 4000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | dol_1100 | bands_keltner.walk_native {"clk": 5, "k": 1.0, "N": 2} | sym15u | +1556 | -107 | +1.00 | 204 | ok/ok/ok | also positive on (b) |
| 2 | dol_1100 | book_dwm.drift_follow_native {"L": 1800, "z": 1.5} | sym15u | +2142 | +502 | +1.37 | 299 | AMBER/ok/AMBER | depends on today's stack |
| 3 | cusum_20 | book_ofi.follow {"L": 200, "z": 2.0} | plain60/60 | +1493 | +667 | +0.96 | 633 | ok/ok/ok | also positive on (b) |
| 4 | ha_bmsgq_B200 | levels_round.retest {"M": 6, "tol": 0.5} | sym15u | +1885 | -312 | +1.21 | 318 | ok/AMBER/ok | depends on today's stack |
| 5 | med_volor_B080 | structure_breakout.brk_native {"minutes": 5, "buf": 0.0} | sym15u | +1448 | -307 | +0.93 | 257 | ok/ok/ok | depends on today's stack |
| 6 | t3_dltor_B080 | bands_bollinger.walk_native {"clk": 20, "k": 2.0, "N": 3} | sym15u | +1441 | +781 | +0.92 | 216 | ok/ok/ok | also positive on (b) |
| 7 | t3_sessrng_B080 | levels_round.break_native {"n": 3, "k": 0.5} | sym15u | +1372 | +500 | +0.88 | 121 | ok/ok/ok | also positive on (b) |
| 8 | ha_sessrng_B200 | bands_keltner.walk {"ema": 30, "atr": 10, "mult": 1.5, "N": 3} | sym15u | +1356 | +918 | +0.87 | 235 | ok/ok/ok | depends on today's stack |
| 9 | vib_15000 | book_ofi.follow_native {"L": 3600, "z": 2.0} | sym15u | +1346 | -533 | +0.86 | 244 | ok/ok/ok | depends on today's stack |
| 10 | med_bmsgq_B200 | tape_stoprun.fade {"N": 10, "k": 0.0} | sym15u | +1835 | +1003 | +1.18 | 323 | AMBER/AMBER/ok | depends on today's stack |

## NYPM

### (a) BARE  (scored on exactly the same result files as (b) and (c); cells passing: 4000, capped at 4,000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | vib_15000 | levels_trendline.reject_native {"tol": 0.5, "conf": "body"} | sym15u | +1580 | +308 | +1.01 | 224 | AMBER/AMBER/ok | bare only (not positive on own-stop) |
| 2 | tsf_2_100 | levels_trendline.break {"n": 3, "k": 0.5} | sym15u | +1489 | +512 | +0.95 | 264 | AMBER/AMBER/ok | strong on (b) too |
| 3 | dib_400 | tape_libvol.cmf {"len": 10} | plain60/60 | +1160 | +1543 | +0.74 | 1086 | ok/ok/ok | bare only (not positive on own-stop) |
| 4 | dol_1700 | levels_trendline.reject_native {"tol": 0.5, "conf": "body"} | sym15u | +1099 | -1207 | +0.70 | 234 | ok/ok/ok | strong on (b) too |
| 5 | t3_sessrng_B200 | tape_libvol.obv {"len": 10} | plain60/60 | +1193 | +1124 | +0.76 | 794 | ok/ok/ok | bare only (not positive on own-stop) |
| 6 | lbrk_3_10 | momentum_rsi.mom_native {"len": 7, "lvl": 55} | plain60/60 | +1323 | +1957 | +0.85 | 778 | AMBER/ok/AMBER | bare only (not positive on own-stop) |
| 7 | entropy_B500 | trend_macd.hist_turn_native {"len": 12, "width": 0.01} | plain60/60 | +1133 | +880 | +0.73 | 973 | ok/ok/ok | bare only (not positive on own-stop) |
| 8 | tm1800 | xmarket_ym.follow {"w": 5, "thr": 1.0} | plain60/60 | +981 | +520 | +0.63 | 151 | ok/ok/ok | strong on (b) too |
| 9 | tsf_5_700 | levels_trendline.reject_native {"tol": 0.5, "conf": "body"} | sym15u | +1376 | +357 | +0.88 | 209 | AMBER/AMBER/ok | bare only (not positive on own-stop) |
| 10 | tm900 | xmarket_es.follow {"w": 5, "thr": 1.0} | plain60/60 | +1194 | +1168 | +0.77 | 280 | ok/ok/AMBER | bare only (not positive on own-stop) |

### (b) OWN-STOP (2 stops; 1.5 and 3 shown as neighbours)  (cells passing: 4000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | micro_B130 | book_sweep.resil_fade {"r": 1.0} | sym15u | +1112 | +1430 | +0.71 | 166 | ok/ok/ok | L6M @1.5 stops +597 / @3 stops +1385 |
| 2 | qmid_B130 | book_sweep.resil_fade {"r": 1.0} | sym15u | +1112 | +1430 | +0.71 | 166 | ok/ok/ok | L6M @1.5 stops +597 / @3 stops +1385 |
| 3 | trb_700 | tape_libvol.vwmacd {"f": 8, "s": 17} | sym15u | +1153 | -184 | +0.74 | 217 | ok/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops +560 |
| 4 | tsf_10_60 | manual_macd.sigcross {"f": 5, "s": 13, "g": 5} | sym15u | +1208 | -331 | +0.77 | 204 | AMBER/AMBER/ok | L6M @1.5 stops +408 / @3 stops <=0 or <100 tr |
| 5 | tsf_10_60 | trend_macd.signal {"len": 6, "width": 0.0} | sym15u | +1176 | -355 | +0.75 | 204 | ok/AMBER/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |
| 6 | trb_700 | manual_macd.sigcross {"f": 12, "s": 26, "g": 9} | sym15u | +937 | +397 | +0.60 | 197 | ok/ok/ok | L6M @1.5 stops +1174 / @3 stops <=0 or <100 tr |
| 7 | ha_micro_B080 | book_ice.follow_sm {"thr": 2, "sm": 3} | sym15u | +954 | +514 | +0.61 | 131 | ok/ok/ok | L6M @1.5 stops +1097 / @3 stops +776 |
| 8 | kal_micro_B080 | book_ice.follow_sm {"thr": 2, "sm": 3} | sym15u | +954 | +514 | +0.61 | 131 | ok/ok/ok | L6M @1.5 stops +1097 / @3 stops +776 |
| 9 | kal_qmid_B080 | book_ice.follow_sm {"thr": 2, "sm": 3} | sym15u | +954 | +514 | +0.61 | 131 | ok/ok/ok | L6M @1.5 stops +1097 / @3 stops +776 |
| 10 | med_micro_B080 | book_ice.follow_sm {"thr": 2, "sm": 3} | sym15u | +954 | +514 | +0.61 | 131 | ok/ok/ok | L6M @1.5 stops +1097 / @3 stops +776 |

### (c) CURRENT-STACK MASK (valid for ADDING a book to today's stack only; not valid for a rebuilt stack)  (cells passing: 4000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | vib_15000 | book_pslope.follow {"L": 100, "z": 1.5} | sym15u | +1137 | +614 | +0.73 | 173 | ok/ok/ok | also positive on (b) |
| 2 | kal_rngor_B080 | levels_round.retest {"M": 6, "tol": 0.5} | sym15u | +1024 | +671 | +0.66 | 210 | ok/ok/ok | depends on today's stack |
| 3 | micro_B030 | xmarket_fast.follow_RTY {"w": 5, "thr": 1.0} | sym15u | +1283 | +430 | +0.82 | 130 | ok/AMBER/ok | depends on today's stack |
| 4 | kal_sessrng_B200 | levels_round.retest {"M": 6, "tol": 0.5} | plain60/60 | +1186 | +925 | +0.76 | 646 | ok/AMBER/ok | depends on today's stack |
| 5 | kal_volor_B200 | book_imb.delta_fade {"lv": 5, "thr": 0.2} | sym15u | +1074 | -249 | +0.69 | 208 | ok/ok/ok | depends on today's stack |
| 6 | med_volor_B200 | book_imb.delta_fade {"lv": 5, "thr": 0.2} | sym15u | +1074 | -249 | +0.69 | 208 | ok/ok/ok | depends on today's stack |
| 7 | t3_volor_B200 | book_imb.delta_fade {"lv": 5, "thr": 0.2} | sym15u | +1074 | -249 | +0.69 | 208 | ok/ok/ok | depends on today's stack |
| 8 | vib_15000 | levels_trendline.reject_native {"tol": 1.0, "conf": "body"} | sym15u | +951 | -159 | +0.61 | 140 | ok/ok/ok | depends on today's stack |
| 9 | rng_10 | levels_fibr_dev.break_native {"n": 3, "k": 0.5} | plain60/60 | +1334 | +361 | +0.86 | 530 | ok/AMBER/AMBER | depends on today's stack |
| 10 | mom_14 | bands_atrchan.break_ext_native {"clk": 5, "k": 1.5} | plain60/60 | +1008 | +1874 | +0.65 | 605 | ok/ok/ok | also positive on (b) |

