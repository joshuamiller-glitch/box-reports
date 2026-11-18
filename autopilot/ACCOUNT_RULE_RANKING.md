# DAYMASK_RANK - three screen rankings per session (W-DAYMASK, orders 1722Z + 1731Z), refreshed 2026-11-18 20:57Z

Screen level, 1 lot, $4.84 round trip in the points, last 26 weeks to the data end (L6M) and 13 weeks (L3M); EQUAL RISK (R = points / the cell stop in points; R/week); ranked by (red prior years, then min(L6M R/week, weakest prior-year R/week)); cells need L6M > 0 and >= 100 trades under THAT variant.
(a) BARE: no account rule. (b) OWN-STOP: stack-independent; no new entries for the rest of the 17:00-ET trading day once the cell itself is down 2 stops on the day (1.5 and 3 stops shown as neighbours). THIS ranking carries the shortlist. (c) CURRENT-STACK MASK: entries blocked while today's JL3 stack has >= 22 closes and day P&L <= -$4,200 live (JL3 history, code/th_grid/gday.py); valid for ADDING a book to today's stack only; not valid for a rebuilt stack; information, never the sole reason to shortlist or drop.
RE-RUN PROGRESS: 2026-11-18T20:56:43Z p1real done 4616 of 5425 pairs, 12477 s (plus every new grid job since 17:30Z carries (b)/(c) by itself).
COVERAGE CAUTION: (b) and (c) exist only for the (row, module) result files already re-run with GL_OWNSTOP / GL_ACCT (the bare top-4,000 cells per session + candidates + shortlist, started 17:28Z); the bare table covers every scored cell. Until the whole grid has been re-run the (b)/(c) tables are biased to cells that were already strong on bare. Cells scored per table are shown in each heading.

## Asia
Cells passing per session (a / b / c): Asia 4000 / 4000 / 4000; London 4000 / 4000 / 4000; NYAM 4000 / 4000 / 4000; NYPM 4000 / 4000 / 4000


### (a) BARE  (scored on exactly the same result files as (b) and (c); cells passing: 4000, capped at 4,000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | dib_240 | momentum_mvote.v3of5_native {"scale": 1.0, "thr": 0.25} | plain60/60 | +616 | +1066 | +0.39 | 777 | ok/ok/ok | bare only (not positive on own-stop) |
| 2 | tm180 | levels_vwap.break_native {"n": 3, "k": 0.5} | plain60/60 | +605 | +1164 | +0.39 | 562 | ok/ok/ok | strong on (b) too |
| 3 | cusum_10 | momentum_cci.brk {"len": 30, "lvl": 200} | plain60/60 | +632 | +93 | +0.40 | 806 | ok/AMBER/ok | bare only (not positive on own-stop) |
| 4 | time_m_7 | xmarket_rty.confirm {"w": 30} | plain60/60 | +601 | +126 | +0.38 | 444 | ok/ok/ok | strong on (b) too |
| 5 | tick_300 | momentum_mvote.v3of5 {"scale": 1.0, "thr": 0.25} | plain60/60 | +502 | +600 | +0.32 | 483 | ok/ok/ok | strong on (b) too |
| 6 | vsess_30 | bands_envelope.break_ema_native {"clk": 10, "k": 1.5} | plain60/60 | +551 | +122 | +0.35 | 182 | ok/ok/ok | strong on (b) too |
| 7 | rng_20 | momentum_mvote.v3of5 {"scale": 1.0, "thr": 0.25} | plain60/60 | +476 | +913 | +0.30 | 653 | ok/ok/ok | strong on (b) too |
| 8 | dib_1200 | levels_vwap.break_native {"n": 2, "k": 0.25} | plain60/60 | +458 | +694 | +0.29 | 545 | ok/ok/ok | bare only (not positive on own-stop) |
| 9 | renko_10 | trend_libstack.ema_stack {"set": "13-34-89"} | plain60/60 | +455 | +913 | +0.29 | 505 | ok/ok/ok | bare only (not positive on own-stop) |
| 10 | time_m_10 | bands_vwap.break_native {"clk": 3, "k": 1.0} | plain60/60 | +481 | +1341 | +0.31 | 394 | ok/ok/ok | bare only (not positive on own-stop) |

### (b) OWN-STOP (2 stops; 1.5 and 3 shown as neighbours)  (cells passing: 4000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | mrenko_20 | momentum_er.trend_z {"len": 10, "thr": 0.4} | plain60/60 | +870 | +360 | +0.56 | 432 | ok/ok/AMBER | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |
| 2 | time_m_7 | xmarket_rty.confirm {"w": 30} | plain60/60 | +634 | +74 | +0.41 | 386 | ok/ok/ok | L6M @1.5 stops +634 / @3 stops +598 |
| 3 | mrenko_20 | momentum_er.trend {"len": 10, "thr": 0.4} | plain60/60 | +603 | +34 | +0.39 | 428 | ok/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |
| 4 | tick_500 | levels_vwap.break {"n": 3, "k": 0.0} | plain60/60 | +674 | +1041 | +0.43 | 417 | AMBER/AMBER/AMBER | L6M @1.5 stops +674 / @3 stops +550 |
| 5 | tick_500 | levels_vwap.break_native {"n": 3, "k": 0.0} | plain60/60 | +674 | +1041 | +0.43 | 417 | ok/AMBER/AMBER | L6M @1.5 stops +674 / @3 stops +550 |
| 6 | tick_300 | trend_libstack.ema_stack {"set": "10-20-50"} | plain60/60 | +664 | +550 | +0.43 | 343 | AMBER/AMBER/AMBER | L6M @1.5 stops +664 / @3 stops <=0 or <100 tr |
| 7 | cusum_40 | levels_fib15.break_native {"n": 3, "k": 0.5} | plain60/60 | +673 | +70 | +0.43 | 555 | AMBER/ok/ok | L6M @1.5 stops +673 / @3 stops <=0 or <100 tr |
| 8 | tick_300 | momentum_mvote.v3of5 {"scale": 1.0, "thr": 0.25} | plain60/60 | +468 | +319 | +0.30 | 404 | ok/ok/ok | L6M @1.5 stops +468 / @3 stops <=0 or <100 tr |
| 9 | rng_20 | momentum_mvote.v3of5 {"scale": 1.0, "thr": 0.25} | plain60/60 | +535 | +899 | +0.34 | 500 | ok/ok/ok | L6M @1.5 stops +535 / @3 stops +266 |
| 10 | time_s_20 | bands_regchan.fade_linreg {"n": 10, "k": 1.5} | asym10u/20u | +325 | +690 | +0.29 | 372 | ok/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |

### (c) CURRENT-STACK MASK (valid for ADDING a book to today's stack only; not valid for a rebuilt stack)  (cells passing: 4000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | tm180 | levels_vwap.break_native {"n": 3, "k": 0.5} | plain60/60 | +626 | +1202 | +0.40 | 556 | ok/ok/ok | also positive on (b) |
| 2 | cusum_10 | momentum_cci.brk {"len": 30, "lvl": 200} | plain60/60 | +622 | +97 | +0.40 | 799 | ok/ok/ok | depends on today's stack |
| 3 | time_m_7 | xmarket_rty.confirm {"w": 30} | plain60/60 | +693 | +194 | +0.44 | 440 | ok/AMBER/AMBER | also positive on (b) |
| 4 | tick_300 | momentum_mvote.v3of5 {"scale": 1.0, "thr": 0.25} | plain60/60 | +525 | +600 | +0.34 | 482 | ok/ok/ok | also positive on (b) |
| 5 | vsess_30 | bands_envelope.break_ema_native {"clk": 10, "k": 1.5} | plain60/60 | +551 | +122 | +0.35 | 182 | ok/ok/ok | also positive on (b) |
| 6 | tick_500 | levels_vwap.break {"n": 3, "k": 0.0} | plain60/60 | +474 | +1566 | +0.30 | 533 | ok/ok/ok | also positive on (b) |
| 7 | tick_500 | levels_vwap.break_native {"n": 3, "k": 0.0} | plain60/60 | +474 | +1566 | +0.30 | 533 | ok/ok/ok | also positive on (b) |
| 8 | cusum_40 | levels_fib15.break_native {"n": 3, "k": 0.5} | plain60/60 | +467 | +418 | +0.30 | 706 | ok/ok/ok | also positive on (b) |
| 9 | renko_10 | trend_libstack.ema_stack {"set": "13-34-89"} | plain60/60 | +652 | +1013 | +0.42 | 500 | AMBER/AMBER/ok | depends on today's stack |
| 10 | time_m_10 | bands_vwap.break_native {"clk": 3, "k": 1.0} | plain60/60 | +481 | +1341 | +0.31 | 394 | ok/ok/ok | depends on today's stack |

## London

### (a) BARE  (scored on exactly the same result files as (b) and (c); cells passing: 4000, capped at 4,000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | bmsg_B320 | barnative_speed.burst_go {"len": 10, "r": 0.25} | sym15u | +702 | +131 | +0.45 | 287 | ok/ok/ok | strong on (b) too |
| 2 | entropy_B200 | book_micro.fade_sm {"L": 100, "z": 1.5, "sm": 3} | sym15u | +852 | +899 | +0.55 | 255 | ok/AMBER/AMBER | strong on (b) too |
| 3 | dlt_70 | levels_zones.reject {"tol": 1.0, "conf": "body"} | plain60/60 | +964 | -521 | +0.62 | 225 | ok/AMBER/AMBER | bare only (not positive on own-stop) |
| 4 | bmsg_B320 | barnative_speed.burst_go {"len": 10, "r": 0.25} | sym15u | +666 | -175 | +0.43 | 140 | ok/ok/ok | strong on (b) too |
| 5 | ha_micro_B200 | trend_ma_hma.cross_native {"len": 34, "width": 1.0, "ratio": 3} | plain60/60 | +802 | +520 | +0.51 | 260 | ok/AMBER/ok | bare only (not positive on own-stop) |
| 6 | ha_qmid_B200 | trend_ma_hma.cross_native {"len": 34, "width": 1.0, "ratio": 3} | plain60/60 | +743 | +460 | +0.48 | 257 | ok/ok/ok | bare only (not positive on own-stop) |
| 7 | kal_bmsg_B200 | trend_ma_hma.cross {"len": 21, "width": 2, "hyst": 0.0} | sym15u | +914 | +1528 | +0.59 | 260 | AMBER/AMBER/AMBER | bare only (not positive on own-stop) |
| 8 | ha_qmid_B200 | trend_ma_hma.cross_native {"len": 34, "width": 1.0, "ratio": 3} | plain60/60 | +623 | +1129 | +0.40 | 502 | ok/ok/ok | bare only (not positive on own-stop) |
| 9 | cusum_14 | xmarket_fast.follow_ES {"w": 30, "thr": 1.0} | plain60/60 | +622 | +581 | +0.40 | 827 | ok/ok/ok | bare only (not positive on own-stop) |
| 10 | ha_micro_B200 | trend_ma_hma.cross_native {"len": 34, "width": 1.0, "ratio": 3} | plain60/60 | +621 | +1188 | +0.40 | 506 | ok/ok/ok | bare only (not positive on own-stop) |

### (b) OWN-STOP (2 stops; 1.5 and 3 shown as neighbours)  (cells passing: 4000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | bmsg_B320 | barnative_speed.burst_go {"len": 10, "r": 0.25} | sym15u | +687 | +276 | +0.44 | 269 | ok/ok/ok | L6M @1.5 stops +687 / @3 stops +877 |
| 2 | bmsg_B500 | book_pslope.fade_sm {"L": 100, "z": 1.5, "sm": 3} | sym15u | +898 | -1732 | +0.58 | 229 | AMBER/ok/AMBER | L6M @1.5 stops +898 / @3 stops <=0 or <100 tr |
| 3 | cusum_28 | trend_macd.hist_turn_native {"len": 26, "width": 0.03} | plain60/60 | +744 | +972 | +0.48 | 364 | ok/ok/ok | L6M @1.5 stops +370 / @3 stops +431 |
| 4 | entropy_B200 | book_micro.fade_sm {"L": 100, "z": 1.5, "sm": 3} | sym15u | +701 | +653 | +0.45 | 238 | ok/ok/ok | L6M @1.5 stops +701 / @3 stops <=0 or <100 tr |
| 5 | bmsgq_B080 | trend_psar.flip {"af0": 0.02, "step": 0.03, "max": 0.2} | sym15u | +627 | +78 | +0.40 | 245 | ok/ok/ok | L6M @1.5 stops +627 / @3 stops +825 |
| 6 | kal_bmsgq_B080 | trend_psar.flip {"af0": 0.02, "step": 0.03, "max": 0.2} | sym15u | +627 | +78 | +0.40 | 245 | ok/ok/ok | L6M @1.5 stops +627 / @3 stops +825 |
| 7 | bmsg_B320 | manual_macd.sigcross_native {"f": 20, "s": 45, "g": 15} | sym15u | +784 | +400 | +0.50 | 241 | AMBER/ok/ok | L6M @1.5 stops +784 / @3 stops <=0 or <100 tr |
| 8 | dib_2000 | book_micro.fade {"L": 50, "z": 1.0} | plain60/60 | +618 | +173 | +0.40 | 339 | ok/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |
| 9 | dltor_B320 | trend_ma_hma.price {"len": 9, "width": 0.0} | sym15u | +838 | +191 | +0.54 | 297 | ok/ok/AMBER | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |
| 10 | ha_rngor_B200 | trend_ma_hma.cross {"len": 34, "width": 4, "hyst": 0.0} | sym15u | +732 | -494 | +0.47 | 246 | ok/ok/AMBER | L6M @1.5 stops +732 / @3 stops <=0 or <100 tr |

### (c) CURRENT-STACK MASK (valid for ADDING a book to today's stack only; not valid for a rebuilt stack)  (cells passing: 4000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | bmsg_B320 | barnative_speed.burst_go {"len": 10, "r": 0.25} | sym15u | +1175 | +593 | +0.75 | 236 | ok/AMBER/AMBER | also positive on (b) |
| 2 | ha_sessrng_B080 | xmarket_rates.with_ZB {"w": 5, "thr": 1.0} | sym15u | +954 | +1179 | +0.61 | 186 | AMBER/ok/ok | depends on today's stack |
| 3 | kal_sessrng_B080 | xmarket_rates.with_ZB {"w": 5, "thr": 1.0} | sym15u | +954 | +1179 | +0.61 | 186 | AMBER/ok/ok | depends on today's stack |
| 4 | med_sessrng_B080 | xmarket_rates.with_ZB {"w": 5, "thr": 1.0} | sym15u | +954 | +1179 | +0.61 | 186 | AMBER/ok/ok | depends on today's stack |
| 5 | med_bmsgq_B080 | tape_libvol.vwmacd {"f": 8, "s": 17} | sym15u | +677 | -374 | +0.43 | 189 | ok/ok/ok | depends on today's stack |
| 6 | dlt_70 | levels_zones.reject {"tol": 1.0, "conf": "body"} | plain60/60 | +674 | -435 | +0.43 | 182 | ok/ok/ok | depends on today's stack |
| 7 | kal_entropy_B080 | tape_libvol.vwmacd {"f": 8, "s": 17} | sym15u | +670 | -420 | +0.43 | 193 | ok/ok/ok | depends on today's stack |
| 8 | dib_2000 | book_micro.fade {"L": 50, "z": 1.0} | plain60/60 | +647 | +578 | +0.41 | 563 | ok/ok/ok | also positive on (b) |
| 9 | tib_400 | barnative_delta.run {"n": 3, "thr": 0.0} | plain60/60 | +602 | +380 | +0.39 | 630 | ok/ok/ok | depends on today's stack |
| 10 | entropy_B500 | book_ice.follow {"thr": 1} | sym15u | +686 | +153 | +0.44 | 210 | ok/AMBER/ok | depends on today's stack |

## NYAM

### (a) BARE  (scored on exactly the same result files as (b) and (c); cells passing: 4000, capped at 4,000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | kal_micro_B200 | pullback_ema.count {"len": 10, "n": 2} | sym15u | +1967 | +206 | +1.26 | 379 | AMBER/ok/ok | strong on (b) too |
| 2 | kal_qmid_B080 | bands_regchan.break_stderr_native {"clk": 20, "k": 2.5} | sym15u | +1956 | +1097 | +1.25 | 316 | AMBER/AMBER/ok | strong on (b) too |
| 3 | trend_20 | levels_vwap.reject {"tol": 1.0, "conf": "body"} | sym15u | +1707 | -264 | +1.09 | 340 | ok/AMBER/ok | strong on (b) too |
| 4 | ha_micro_B080 | book_ofi.follow_native {"L": 3600, "z": 2.0} | sym15u | +1685 | +1174 | +1.08 | 358 | ok/AMBER/ok | strong on (b) too |
| 5 | kal_qmid_B080 | book_ofi.follow_native {"L": 3600, "z": 2.0} | sym15u | +1685 | +1174 | +1.08 | 358 | ok/AMBER/ok | strong on (b) too |
| 6 | bmsgq_B050 | book_cancel.canc_follow {"L": 50, "z": 1.0} | sym15u | +1657 | +307 | +1.06 | 387 | ok/AMBER/ok | bare only (not positive on own-stop) |
| 7 | frenko_40 | book_ofi.follow_sm {"L": 200, "z": 2.0, "sm": 3} | plain60/60 | +1751 | +147 | +1.12 | 582 | AMBER/AMBER/ok | strong on (b) too |
| 8 | kal_qmid_B200 | pullback_ema.count {"len": 10, "n": 2} | sym15u | +1641 | +212 | +1.05 | 379 | AMBER/ok/ok | strong on (b) too |
| 9 | renko_10 | momentum_mvote.v3of5_native {"scale": 0.25, "thr": 0.25} | plain60/60 | +1302 | +386 | +0.83 | 1427 | ok/ok/ok | bare only (not positive on own-stop) |
| 10 | bmsg_B200 | bands_bollinger.walk {"n": 30, "k": 2.0, "N": 3} | sym15u | +1380 | +1784 | +0.88 | 303 | ok/ok/ok | strong on (b) too |

### (b) OWN-STOP (2 stops; 1.5 and 3 shown as neighbours)  (cells passing: 4000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | trend_20 | levels_vwap.break_native {"n": 2, "k": 0.25} | sym15u | +2161 | +1183 | +1.39 | 258 | AMBER/ok/ok | L6M @1.5 stops +2298 / @3 stops <=0 or <100 tr |
| 2 | cusum_20 | book_ofi.follow {"L": 200, "z": 2.0} | plain60/60 | +2026 | +333 | +1.30 | 496 | AMBER/AMBER/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops +579 |
| 3 | kal_micro_B200 | pullback_ema.count {"len": 10, "n": 2} | sym15u | +1389 | +271 | +0.89 | 318 | ok/ok/ok | L6M @1.5 stops +1501 / @3 stops <=0 or <100 tr |
| 4 | trend_20 | levels_vwap.reject {"tol": 1.0, "conf": "body"} | sym15u | +1375 | -248 | +0.88 | 260 | ok/ok/ok | L6M @1.5 stops +763 / @3 stops +1879 |
| 5 | kal_qmid_B200 | pullback_ema.count {"len": 10, "n": 2} | sym15u | +1348 | +276 | +0.86 | 317 | ok/ok/ok | L6M @1.5 stops +1582 / @3 stops <=0 or <100 tr |
| 6 | dltor_B080 | book_cancel.canc_follow {"L": 200, "z": 2.0} | sym15u | +1528 | +2013 | +0.98 | 322 | AMBER/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |
| 7 | dltor_B130 | bands_atrchan.break_ema {"n": 10, "atr": 14, "k": 1.5} | sym15u | +1533 | +257 | +0.98 | 388 | ok/AMBER/ok | L6M @1.5 stops +625 / @3 stops +1501 |
| 8 | ha_micro_B200 | barnative_run.cont {"n": 4} | sym15u | +1226 | +241 | +0.79 | 343 | ok/ok/ok | L6M @1.5 stops +1202 / @3 stops +418 |
| 9 | entropy_B200 | levels_swsr5.break {"n": 3, "k": 0.5} | sym15u | +1217 | -1804 | +0.78 | 346 | ok/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops +1325 |
| 10 | ha_entropy_B200 | levels_round.retest {"M": 10, "tol": 0.5} | sym15u | +1329 | +706 | +0.85 | 364 | ok/ok/ok | L6M @1.5 stops +359 / @3 stops <=0 or <100 tr |

### (c) CURRENT-STACK MASK (valid for ADDING a book to today's stack only; not valid for a rebuilt stack)  (cells passing: 4000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | cusum_20 | book_ofi.follow {"L": 200, "z": 2.0} | plain60/60 | +1493 | +667 | +0.96 | 633 | ok/ok/ok | also positive on (b) |
| 2 | ha_bmsgq_B200 | levels_round.retest {"M": 6, "tol": 0.5} | sym15u | +1885 | -312 | +1.21 | 318 | ok/AMBER/ok | depends on today's stack |
| 3 | med_volor_B080 | structure_breakout.brk_native {"minutes": 5, "buf": 0.0} | sym15u | +1448 | -307 | +0.93 | 257 | ok/ok/ok | depends on today's stack |
| 4 | ha_sessrng_B200 | bands_keltner.walk {"ema": 30, "atr": 10, "mult": 1.5, "N": 3} | sym15u | +1356 | +918 | +0.87 | 235 | ok/ok/ok | depends on today's stack |
| 5 | med_bmsgq_B200 | tape_stoprun.fade {"N": 10, "k": 0.0} | sym15u | +1835 | +1003 | +1.18 | 323 | AMBER/AMBER/ok | depends on today's stack |
| 6 | dchg_40 | manual_macd.sigcross_native {"f": 5, "s": 13, "g": 4} | plain60/60 | +1357 | -639 | +0.87 | 604 | ok/ok/ok | depends on today's stack |
| 7 | trend_20 | levels_fibr_dev.retest {"M": 3, "tol": 0.0} | sym15u | +1354 | +338 | +0.87 | 234 | ok/ok/ok | depends on today's stack |
| 8 | trend_20 | levels_fibr_dev.retest_native {"M": 3, "tol": 0.0} | sym15u | +1354 | +338 | +0.87 | 234 | ok/ok/ok | depends on today's stack |
| 9 | med_volor_B080 | bands_bollinger.break_native {"clk": 40, "k": 2.5} | sym15u | +1703 | +412 | +1.09 | 152 | AMBER/AMBER/ok | depends on today's stack |
| 10 | ha_sessrng_B080 | bands_keltner.break {"ema": 10, "atr": 10, "mult": 1.5} | sym15u | +1396 | +1013 | +0.89 | 138 | ok/ok/ok | depends on today's stack |

## NYPM

### (a) BARE  (scored on exactly the same result files as (b) and (c); cells passing: 4000, capped at 4,000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | dib_400 | tape_libvol.cmf {"len": 10} | plain60/60 | +1160 | +1543 | +0.74 | 1086 | ok/ok/ok | bare only (not positive on own-stop) |
| 2 | lbrk_3_10 | momentum_rsi.mom_native {"len": 7, "lvl": 55} | plain60/60 | +1323 | +1957 | +0.85 | 778 | AMBER/ok/AMBER | bare only (not positive on own-stop) |
| 3 | entropy_B500 | trend_macd.hist_turn_native {"len": 12, "width": 0.01} | plain60/60 | +1133 | +880 | +0.73 | 973 | ok/ok/ok | bare only (not positive on own-stop) |
| 4 | tm1800 | xmarket_ym.follow {"w": 5, "thr": 1.0} | plain60/60 | +981 | +520 | +0.63 | 151 | ok/ok/ok | strong on (b) too |
| 5 | tm900 | xmarket_es.follow {"w": 5, "thr": 1.0} | plain60/60 | +1194 | +1168 | +0.77 | 280 | ok/ok/AMBER | bare only (not positive on own-stop) |
| 6 | entropy_B080 | levels_trendline.reject_native {"tol": 1.0, "conf": "body"} | sym15u | +957 | -186 | +0.61 | 253 | ok/ok/ok | strong on (b) too |
| 7 | time_s_20 | bands_atrchan.break_ext {"n": 10, "atr": 14, "k": 2.0} | plain60/60 | +1084 | -624 | +0.69 | 893 | ok/ok/ok | strong on (b) too |
| 8 | ha_sessrng_B080 | xmarket_ym.follow {"w": 1, "thr": 1.0} | sym15u | +878 | +353 | +0.56 | 297 | ok/ok/ok | strong on (b) too |
| 9 | ha_volor_B080 | manual_macd.histturn {"f": 5, "s": 13, "g": 5} | plain60/60 | +913 | +1136 | +0.59 | 983 | ok/ok/ok | bare only (not positive on own-stop) |
| 10 | swing_pct_8 | momentum_willr.break_native {"len": 7, "lvl": 10} | plain60/60 | +1060 | -783 | +0.68 | 827 | ok/ok/AMBER | strong on (b) too |

### (b) OWN-STOP (2 stops; 1.5 and 3 shown as neighbours)  (cells passing: 4000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | ha_micro_B080 | book_ice.follow_sm {"thr": 2, "sm": 3} | sym15u | +954 | +514 | +0.61 | 131 | ok/ok/ok | L6M @1.5 stops +1097 / @3 stops +776 |
| 2 | kal_micro_B080 | book_ice.follow_sm {"thr": 2, "sm": 3} | sym15u | +954 | +514 | +0.61 | 131 | ok/ok/ok | L6M @1.5 stops +1097 / @3 stops +776 |
| 3 | kal_qmid_B080 | book_ice.follow_sm {"thr": 2, "sm": 3} | sym15u | +954 | +514 | +0.61 | 131 | ok/ok/ok | L6M @1.5 stops +1097 / @3 stops +776 |
| 4 | tm1800 | xmarket_ym.follow {"w": 5, "thr": 1.0} | plain60/60 | +1219 | +433 | +0.78 | 115 | ok/AMBER/ok | L6M @1.5 stops +925 / @3 stops +1181 |
| 5 | time_s_20 | bands_atrchan.break_ext {"n": 10, "atr": 14, "k": 2.0} | plain60/60 | +885 | +115 | +0.57 | 255 | ok/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops +1152 |
| 6 | tick_2000 | levels_session_hl.reject {"tol": 1.0, "conf": "body"} | plain60/60 | +910 | +444 | +0.58 | 161 | ok/ok/ok | L6M @1.5 stops +886 / @3 stops +293 |
| 7 | ha_sessrng_B080 | xmarket_ym.follow {"w": 1, "thr": 1.0} | sym15u | +824 | +300 | +0.53 | 200 | ok/ok/ok | L6M @1.5 stops +730 / @3 stops +274 |
| 8 | kal_sessrng_B080 | xmarket_ym.follow {"w": 1, "thr": 1.0} | sym15u | +824 | +300 | +0.53 | 200 | ok/ok/ok | L6M @1.5 stops +730 / @3 stops +274 |
| 9 | dlt_70 | bands_regchan.break_linreg {"n": 10, "k": 1.5} | sym15u | +2155 | +808 | +0.69 | 177 | AMBER/AMBER/AMBER | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |
| 10 | drb_1200 | bands_regchan.break_linreg {"n": 20, "k": 2.0} | plain60/60 | +972 | +77 | +0.62 | 288 | ok/ok/AMBER | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |

### (c) CURRENT-STACK MASK (valid for ADDING a book to today's stack only; not valid for a rebuilt stack)  (cells passing: 4000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | kal_rngor_B080 | levels_round.retest {"M": 6, "tol": 0.5} | sym15u | +1024 | +671 | +0.66 | 210 | ok/ok/ok | depends on today's stack |
| 2 | kal_volor_B200 | book_imb.delta_fade {"lv": 5, "thr": 0.2} | sym15u | +1074 | -249 | +0.69 | 208 | ok/ok/ok | depends on today's stack |
| 3 | med_volor_B200 | book_imb.delta_fade {"lv": 5, "thr": 0.2} | sym15u | +1074 | -249 | +0.69 | 208 | ok/ok/ok | depends on today's stack |
| 4 | mom_14 | bands_atrchan.break_ext_native {"clk": 5, "k": 1.5} | plain60/60 | +1008 | +1874 | +0.65 | 605 | ok/ok/ok | also positive on (b) |
| 5 | bmsg_B130 | levels_round.reject {"tol": 0.0, "conf": "close"} | sym15u | +1172 | +549 | +0.75 | 196 | ok/AMBER/ok | depends on today's stack |
| 6 | bmsg_B130 | levels_round.reject_native {"tol": 0.0, "conf": "close"} | sym15u | +1172 | +549 | +0.75 | 196 | ok/AMBER/ok | depends on today's stack |
| 7 | renko_10 | tape_delta.cvd_fade {"N": 5, "L": 100, "z": 1.0} | plain60/60 | +1219 | +206 | +0.78 | 527 | AMBER/AMBER/ok | depends on today's stack |
| 8 | dltor_B320 | levels_trendline.break_native {"n": 3, "k": 0.5} | sym15u | +842 | -539 | +0.54 | 142 | ok/ok/ok | depends on today's stack |
| 9 | rng_28 | xmarket_commod.with_GC {"w": 1, "thr": 1.0} | plain60/60 | +1101 | +1215 | +0.71 | 445 | AMBER/AMBER/ok | depends on today's stack |
| 10 | dlt_250 | xmarket_commod.with_GC {"w": 1, "thr": 1.0} | plain60/60 | +1074 | +467 | +0.69 | 301 | AMBER/AMBER/ok | depends on today's stack |


Note: ACCOUNT_RULE_RANKING.md carries the same three rankings side by side as DAYMASK_RANK.md (one builder).
