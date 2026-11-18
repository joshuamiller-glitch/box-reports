# DAYMASK_RANK - three screen rankings per session (W-DAYMASK, orders 1722Z + 1731Z), refreshed 2026-11-18 19:26Z

Screen level, 1 lot, $4.84 round trip in the points, last 26 weeks to the data end (L6M) and 13 weeks (L3M); EQUAL RISK (R = points / the cell stop in points; R/week); ranked by (red prior years, then min(L6M R/week, weakest prior-year R/week)); cells need L6M > 0 and >= 100 trades under THAT variant.
(a) BARE: no account rule. (b) OWN-STOP: stack-independent; no new entries for the rest of the 17:00-ET trading day once the cell itself is down 2 stops on the day (1.5 and 3 stops shown as neighbours). THIS ranking carries the shortlist. (c) CURRENT-STACK MASK: entries blocked while today's JL3 stack has >= 22 closes and day P&L <= -$4,200 live (JL3 history, code/th_grid/gday.py); valid for ADDING a book to today's stack only; not valid for a rebuilt stack; information, never the sole reason to shortlist or drop.
RE-RUN PROGRESS: 2026-11-18T19:26:54Z p1real done 3051 of 5425 pairs, 7088 s (plus every new grid job since 17:30Z carries (b)/(c) by itself).
COVERAGE CAUTION: (b) and (c) exist only for the (row, module) result files already re-run with GL_OWNSTOP / GL_ACCT (the bare top-4,000 cells per session + candidates + shortlist, started 17:28Z); the bare table covers every scored cell. Until the whole grid has been re-run the (b)/(c) tables are biased to cells that were already strong on bare. Cells scored per table are shown in each heading.

## Asia
Cells passing per session (a / b / c): Asia 4000 / 4000 / 4000; London 4000 / 4000 / 4000; NYAM 4000 / 4000 / 4000; NYPM 4000 / 4000 / 4000


### (a) BARE  (scored on exactly the same result files as (b) and (c); cells passing: 4000, capped at 4,000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | dib_240 | momentum_mvote.v3of5_native {"scale": 1.0, "thr": 0.25} | plain60/60 | +616 | +1066 | +0.39 | 777 | ok/ok/ok | bare only (not positive on own-stop) |
| 2 | cusum_10 | momentum_cci.brk {"len": 30, "lvl": 200} | plain60/60 | +632 | +93 | +0.40 | 806 | ok/AMBER/ok | bare only (not positive on own-stop) |
| 3 | dib_1200 | levels_vwap.break_native {"n": 2, "k": 0.25} | plain60/60 | +458 | +694 | +0.29 | 545 | ok/ok/ok | bare only (not positive on own-stop) |
| 4 | frenko_40 | book_ofi.follow_sm {"L": 50, "z": 1.0, "sm": 3} | plain60/60 | +446 | +73 | +0.29 | 708 | ok/ok/ok | bare only (not positive on own-stop) |
| 5 | drb_400 | structure_orb.orb {"or_min": 5, "buf": 0.0} | plain60/60 | +543 | +513 | +0.35 | 175 | AMBER/ok/ok | strong on (b) too |
| 6 | mom_10 | levels_book_walls_loose.retest_native {"M": 6, "tol": 0.5} | plain60/60 | +523 | +446 | +0.34 | 159 | AMBER/ok/AMBER | bare only (not positive on own-stop) |
| 7 | mom_56 | trend_psar.flip {"af0": 0.02, "step": 0.03, "max": 0.2} | plain60/60 | +414 | +661 | +0.27 | 309 | ok/ok/ok | strong on (b) too |
| 8 | dlt_45 | momentum_willr.break_native {"len": 21, "lvl": 30} | plain60/60 | +508 | +537 | +0.33 | 576 | ok/AMBER/ok | strong on (b) too |
| 9 | cusum_80 | momentum_cci.zero_native {"len": 30, "lvl": 50} | plain60/60 | +435 | -495 | +0.28 | 441 | ok/ok/ok | bare only (not positive on own-stop) |
| 10 | dlt_45 | levels_fib15.break {"n": 3, "k": 0.5} | plain60/60 | +452 | -904 | +0.29 | 704 | ok/AMBER/ok | bare only (not positive on own-stop) |

### (b) OWN-STOP (2 stops; 1.5 and 3 shown as neighbours)  (cells passing: 4000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | cusum_40 | levels_fib15.break_native {"n": 3, "k": 0.5} | plain60/60 | +673 | +70 | +0.43 | 555 | AMBER/ok/ok | L6M @1.5 stops +673 / @3 stops <=0 or <100 tr |
| 2 | dol_500 | momentum_roc.break {"len": 20, "wd": 1.0} | plain60/60 | +521 | -1178 | +0.33 | 478 | AMBER/AMBER/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |
| 3 | drb_400 | structure_orb.orb {"or_min": 5, "buf": 0.0} | plain60/60 | +543 | +513 | +0.35 | 175 | AMBER/ok/ok | L6M @1.5 stops +543 / @3 stops +543 |
| 4 | trb_240 | xmarket_ym.confirm {"w": 5} | sym15u | +571 | +621 | +0.37 | 346 | AMBER/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |
| 5 | trb_240 | trend_libstack.ema_hold {"len": 21, "hold": 5} | sym15u | +403 | -447 | +0.26 | 332 | ok/ok/ok | L6M @1.5 stops +410 / @3 stops <=0 or <100 tr |
| 6 | trb_240 | levels_fib15.break_native {"n": 3, "k": 0.5} | plain60/60 | +399 | +45 | +0.26 | 285 | ok/ok/ok | L6M @1.5 stops +399 / @3 stops <=0 or <100 tr |
| 7 | mom_14 | levels_fib15.break {"n": 3, "k": 0.5} | plain60/60 | +535 | -337 | +0.34 | 554 | AMBER/AMBER/ok | L6M @1.5 stops +535 / @3 stops <=0 or <100 tr |
| 8 | trend_20 | levels_profile_nodes.retest {"M": 6, "tol": 0.5} | sym15u | +458 | +59 | +0.29 | 213 | ok/ok/ok | L6M @1.5 stops +458 / @3 stops <=0 or <100 tr |
| 9 | pasl_10 | levels_fib5.reject_native {"tol": 1.0, "conf": "body"} | plain60/60 | +457 | +371 | +0.29 | 264 | ok/ok/ok | L6M @1.5 stops +457 / @3 stops <=0 or <100 tr |
| 10 | renko_14 | tape_vpin.follow {"N": 10, "thr": 0.08} | asym10u/20u | +561 | +44 | +0.25 | 344 | ok/ok/ok | L6M @1.5 stops +432 / @3 stops +348 |

### (c) CURRENT-STACK MASK (valid for ADDING a book to today's stack only; not valid for a rebuilt stack)  (cells passing: 4000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | cusum_10 | momentum_cci.brk {"len": 30, "lvl": 200} | plain60/60 | +622 | +97 | +0.40 | 799 | ok/ok/ok | depends on today's stack |
| 2 | cusum_40 | levels_fib15.break_native {"n": 3, "k": 0.5} | plain60/60 | +467 | +418 | +0.30 | 706 | ok/ok/ok | also positive on (b) |
| 3 | mom_10 | bands_bollinger.walk {"n": 20, "k": 2.0, "N": 2} | plain60/60 | +486 | -1221 | +0.31 | 815 | ok/ok/ok | depends on today's stack |
| 4 | mom_56 | trend_psar.flip {"af0": 0.02, "step": 0.03, "max": 0.2} | plain60/60 | +453 | +629 | +0.29 | 306 | ok/ok/ok | also positive on (b) |
| 5 | drb_400 | structure_orb.orb {"or_min": 5, "buf": 0.0} | plain60/60 | +543 | +513 | +0.35 | 175 | AMBER/ok/ok | also positive on (b) |
| 6 | mom_10 | levels_book_walls_loose.retest_native {"M": 6, "tol": 0.5} | plain60/60 | +523 | +446 | +0.34 | 159 | AMBER/ok/AMBER | depends on today's stack |
| 7 | trb_240 | levels_swsr5.break_native {"n": 3, "k": 0.5} | sym15u | +487 | -195 | +0.31 | 371 | ok/AMBER/ok | depends on today's stack |
| 8 | dlt_45 | momentum_willr.break_native {"len": 21, "lvl": 30} | plain60/60 | +555 | +495 | +0.36 | 570 | ok/AMBER/ok | also positive on (b) |
| 9 | swing_pct_5 | levels_fib15.break_native {"n": 3, "k": 0.5} | plain60/60 | +386 | +299 | +0.25 | 746 | ok/ok/ok | depends on today's stack |
| 10 | dlt_30 | levels_fib15.break {"n": 3, "k": 0.5} | plain60/60 | +482 | +1052 | +0.31 | 715 | ok/AMBER/ok | depends on today's stack |

## London

### (a) BARE  (scored on exactly the same result files as (b) and (c); cells passing: 4000, capped at 4,000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | bmsg_B320 | barnative_speed.burst_go {"len": 10, "r": 0.25} | sym15u | +702 | +131 | +0.45 | 287 | ok/ok/ok | strong on (b) too |
| 2 | dlt_70 | levels_zones.reject {"tol": 1.0, "conf": "body"} | plain60/60 | +964 | -521 | +0.62 | 225 | ok/AMBER/AMBER | strong on (b) too |
| 3 | bmsg_B320 | barnative_speed.burst_go {"len": 10, "r": 0.25} | sym15u | +666 | -175 | +0.43 | 140 | ok/ok/ok | strong on (b) too |
| 4 | cusum_14 | xmarket_fast.follow_ES {"w": 30, "thr": 1.0} | plain60/60 | +622 | +581 | +0.40 | 827 | ok/ok/ok | bare only (not positive on own-stop) |
| 5 | bmsgq_B080 | trend_psar.flip {"af0": 0.03, "step": 0.02, "max": 0.2} | sym15u | +669 | -258 | +0.43 | 249 | ok/ok/ok | strong on (b) too |
| 6 | bmsgq_B080 | trend_psar.flip {"af0": 0.02, "step": 0.03, "max": 0.2} | sym15u | +836 | +242 | +0.54 | 254 | ok/AMBER/ok | strong on (b) too |
| 7 | bmsg_B320 | bands_regchan.fade_linreg_native {"clk": 5, "k": 1.5} | sym15u | +588 | +723 | +0.38 | 197 | ok/ok/ok | strong on (b) too |
| 8 | bmsg_B320 | xmarket_rates.with_ZN {"w": 1, "thr": 1.0} | sym15u | +500 | +581 | +0.32 | 278 | ok/ok/ok | strong on (b) too |
| 9 | dlt_70 | levels_zones.reject {"tol": 0.5, "conf": "body"} | plain60/60 | +603 | -780 | +0.39 | 193 | AMBER/AMBER/ok | bare only (not positive on own-stop) |
| 10 | bmsgq_B130 | xmarket_commod.with_GC {"w": 1, "thr": 1.0} | plain60/60 | +644 | -330 | +0.41 | 375 | ok/AMBER/ok | strong on (b) too |

### (b) OWN-STOP (2 stops; 1.5 and 3 shown as neighbours)  (cells passing: 4000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | bmsg_B320 | barnative_speed.burst_go {"len": 10, "r": 0.25} | sym15u | +687 | +276 | +0.44 | 269 | ok/ok/ok | L6M @1.5 stops +687 / @3 stops +877 |
| 2 | bmsg_B500 | book_pslope.fade_sm {"L": 100, "z": 1.5, "sm": 3} | sym15u | +898 | -1732 | +0.58 | 229 | AMBER/ok/AMBER | L6M @1.5 stops +898 / @3 stops <=0 or <100 tr |
| 3 | cusum_28 | trend_macd.hist_turn_native {"len": 26, "width": 0.03} | plain60/60 | +744 | +972 | +0.48 | 364 | ok/ok/ok | L6M @1.5 stops +370 / @3 stops +431 |
| 4 | bmsgq_B080 | trend_psar.flip {"af0": 0.02, "step": 0.03, "max": 0.2} | sym15u | +627 | +78 | +0.40 | 245 | ok/ok/ok | L6M @1.5 stops +627 / @3 stops +825 |
| 5 | bmsg_B320 | manual_macd.sigcross_native {"f": 20, "s": 45, "g": 15} | sym15u | +784 | +400 | +0.50 | 241 | AMBER/ok/ok | L6M @1.5 stops +784 / @3 stops <=0 or <100 tr |
| 6 | dib_2000 | book_micro.fade {"L": 50, "z": 1.0} | plain60/60 | +618 | +173 | +0.40 | 339 | ok/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |
| 7 | bmsgq_B080 | trend_ma_hma.cross {"len": 8, "width": 2, "hyst": 0.0} | sym15u | +775 | +508 | +0.50 | 250 | AMBER/AMBER/ok | L6M @1.5 stops +775 / @3 stops <=0 or <100 tr |
| 8 | bmsg_B320 | bands_regchan.fade_linreg_native {"clk": 5, "k": 1.5} | sym15u | +530 | +555 | +0.34 | 188 | ok/ok/ok | L6M @1.5 stops +530 / @3 stops +588 |
| 9 | bmsgq_B080 | trend_psar.flip {"af0": 0.02, "step": 0.03, "max": 0.2} | sym15u | +680 | -145 | +0.44 | 133 | AMBER/ok/ok | L6M @1.5 stops +680 / @3 stops +631 |
| 10 | bmsgq_B080 | trend_psar.flip {"af0": 0.03, "step": 0.02, "max": 0.2} | sym15u | +495 | -521 | +0.32 | 241 | ok/ok/ok | L6M @1.5 stops +495 / @3 stops +657 |

### (c) CURRENT-STACK MASK (valid for ADDING a book to today's stack only; not valid for a rebuilt stack)  (cells passing: 4000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | bmsg_B320 | barnative_speed.burst_go {"len": 10, "r": 0.25} | sym15u | +1175 | +593 | +0.75 | 236 | ok/AMBER/AMBER | also positive on (b) |
| 2 | dlt_70 | levels_zones.reject {"tol": 1.0, "conf": "body"} | plain60/60 | +674 | -435 | +0.43 | 182 | ok/ok/ok | also positive on (b) |
| 3 | dib_2000 | book_micro.fade {"L": 50, "z": 1.0} | plain60/60 | +647 | +578 | +0.41 | 563 | ok/ok/ok | also positive on (b) |
| 4 | entropy_B500 | book_ice.follow {"thr": 1} | sym15u | +686 | +153 | +0.44 | 210 | ok/AMBER/ok | depends on today's stack |
| 5 | entropy_B500 | book_sweep.span_fade {"thr": 4} | sym15u | +617 | -795 | +0.40 | 243 | ok/ok/ok | depends on today's stack |
| 6 | dltor_B320 | book_ice.follow {"thr": 2} | sym15u | +592 | -516 | +0.38 | 124 | ok/AMBER/ok | also positive on (b) |
| 7 | bmsg_B320 | bands_regchan.fade_linreg_native {"clk": 5, "k": 1.5} | sym15u | +534 | +704 | +0.34 | 164 | ok/ok/ok | also positive on (b) |
| 8 | dlt_70 | levels_zones.reject {"tol": 0.5, "conf": "body"} | plain60/60 | +569 | -575 | +0.36 | 156 | ok/ok/ok | depends on today's stack |
| 9 | trb_240 | tape_libvol.adline {"len": 20} | plain60/60 | +618 | +762 | +0.40 | 541 | AMBER/AMBER/AMBER | depends on today's stack |
| 10 | bmsgq_B080 | momentum_libosc.demarker {"len": 7, "lvl": 0.2} | sym15u | +472 | -120 | +0.30 | 204 | ok/ok/ok | also positive on (b) |

## NYAM

### (a) BARE  (scored on exactly the same result files as (b) and (c); cells passing: 4000, capped at 4,000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | frenko_40 | book_ofi.follow_sm {"L": 200, "z": 2.0, "sm": 3} | plain60/60 | +1751 | +147 | +1.12 | 582 | AMBER/AMBER/ok | strong on (b) too |
| 2 | bmsg_B200 | bands_bollinger.walk {"n": 30, "k": 2.0, "N": 3} | sym15u | +1380 | +1784 | +0.88 | 303 | ok/ok/ok | strong on (b) too |
| 3 | swing_atr_0.15 | momentum_willr.break_native {"len": 14, "lvl": 10} | plain60/60 | +1413 | +21 | +0.91 | 1828 | ok/ok/ok | bare only (not positive on own-stop) |
| 4 | bmsg_B130 | bands_bollinger.break {"n": 30, "k": 2.5} | sym15u | +1125 | +814 | +0.72 | 266 | ok/ok/ok | strong on (b) too |
| 5 | dchg_28 | book_ofi.follow_sm {"L": 50, "z": 1.0, "sm": 3} | plain60/60 | +1370 | -2321 | +0.88 | 1270 | AMBER/ok/ok | bare only (not positive on own-stop) |
| 6 | bmsg_B030 | book_cancel.net_follow {"L": 200, "z": 2.0} | sym15u | +1115 | +780 | +0.72 | 256 | ok/ok/ok | strong on (b) too |
| 7 | bmsg_B080 | bands_keltner.break {"ema": 30, "atr": 10, "mult": 2.5} | sym15u | +1056 | +391 | +0.68 | 238 | ok/ok/ok | bare only (not positive on own-stop) |
| 8 | renko_20 | trend_libstack.ema_hold {"len": 13, "hold": 3} | plain60/60 | +1046 | -1325 | +0.67 | 1160 | ok/ok/ok | bare only (not positive on own-stop) |
| 9 | bmsg_B200 | book_pslope.fade_native {"L": 900, "z": 1.0} | sym15u | +1376 | +1868 | +0.88 | 430 | ok/AMBER/ok | strong on (b) too |
| 10 | bmsgq_B080 | bands_keltner.break {"ema": 30, "atr": 10, "mult": 2.5} | sym15u | +1025 | +1034 | +0.66 | 230 | ok/ok/ok | bare only (not positive on own-stop) |

### (b) OWN-STOP (2 stops; 1.5 and 3 shown as neighbours)  (cells passing: 4000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | trend_20 | levels_vwap.break_native {"n": 2, "k": 0.25} | sym15u | +2161 | +1183 | +1.39 | 258 | AMBER/ok/ok | L6M @1.5 stops +2298 / @3 stops <=0 or <100 tr |
| 2 | cusum_20 | book_ofi.follow {"L": 200, "z": 2.0} | plain60/60 | +2026 | +333 | +1.30 | 496 | AMBER/AMBER/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops +579 |
| 3 | trend_20 | levels_vwap.reject {"tol": 1.0, "conf": "body"} | sym15u | +1375 | -248 | +0.88 | 260 | ok/ok/ok | L6M @1.5 stops +763 / @3 stops +1879 |
| 4 | bmsg_B200 | book_pslope.fade_native {"L": 900, "z": 1.0} | sym15u | +1591 | +1735 | +1.02 | 370 | AMBER/AMBER/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops +1254 |
| 5 | trend_20 | momentum_cci.brk_native {"len": 20, "lvl": 100} | sym15u | +1129 | +1387 | +0.72 | 279 | ok/ok/ok | L6M @1.5 stops +973 / @3 stops <=0 or <100 tr |
| 6 | bmsgq_B200 | bands_regchan.break_linreg_native {"clk": 5, "k": 1.5} | sym15u | +1509 | +1348 | +0.97 | 245 | ok/AMBER/ok | L6M @1.5 stops +1166 / @3 stops +1358 |
| 7 | bmsgq_B130 | levels_round.break {"n": 2, "k": 0.25} | sym15u | +1342 | +10 | +0.86 | 367 | AMBER/ok/ok | L6M @1.5 stops +465 / @3 stops <=0 or <100 tr |
| 8 | bmsg_B050 | bands_envelope.break_sma {"n": 20, "pct": 0.1} | sym15u | +1115 | +706 | +0.71 | 256 | ok/ok/ok | L6M @1.5 stops +1209 / @3 stops +318 |
| 9 | bmsg_B130 | bands_bollinger.break {"n": 30, "k": 2.5} | sym15u | +1203 | +697 | +0.77 | 232 | ok/ok/ok | L6M @1.5 stops +460 / @3 stops +1352 |
| 10 | kagi_14 | bands_atrchan.break_ext_native {"clk": 10, "k": 2.0} | plain60/60 | +1283 | +766 | +0.82 | 541 | ok/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |

### (c) CURRENT-STACK MASK (valid for ADDING a book to today's stack only; not valid for a rebuilt stack)  (cells passing: 4000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | cusum_20 | book_ofi.follow {"L": 200, "z": 2.0} | plain60/60 | +1493 | +667 | +0.96 | 633 | ok/ok/ok | also positive on (b) |
| 2 | dchg_40 | manual_macd.sigcross_native {"f": 5, "s": 13, "g": 4} | plain60/60 | +1357 | -639 | +0.87 | 604 | ok/ok/ok | depends on today's stack |
| 3 | trend_20 | levels_fibr_dev.retest {"M": 3, "tol": 0.0} | sym15u | +1354 | +338 | +0.87 | 234 | ok/ok/ok | depends on today's stack |
| 4 | trend_20 | levels_fibr_dev.retest_native {"M": 3, "tol": 0.0} | sym15u | +1354 | +338 | +0.87 | 234 | ok/ok/ok | depends on today's stack |
| 5 | bmsgq_B050 | bands_atrchan.break_ema {"n": 10, "atr": 14, "k": 1.5} | sym15u | +1211 | -27 | +0.78 | 190 | ok/ok/ok | depends on today's stack |
| 6 | kagi_20 | book_ofi.follow_native {"L": 900, "z": 2.0} | plain60/60 | +1199 | -192 | +0.77 | 660 | ok/ok/ok | depends on today's stack |
| 7 | anch_L0200_B50 | levels_piv_floor.break {"n": 2, "k": 0.25} | sym15u | +1526 | +203 | +0.98 | 180 | AMBER/ok/AMBER | also positive on (b) |
| 8 | bmsgq_B050 | bands_atrchan.break_ema {"n": 20, "atr": 14, "k": 2.0} | sym15u | +1440 | -13 | +0.92 | 165 | ok/AMBER/ok | depends on today's stack |
| 9 | dchg_14 | tape_block.b10_follow_sm {"L": 100, "z": 1.5, "sm": 3} | plain60/60 | +1288 | -231 | +0.83 | 817 | AMBER/ok/ok | depends on today's stack |
| 10 | entropy_B080 | book_cancel.net_follow_native {"L": 900, "z": 1.0} | sym15u | +1348 | +647 | +0.86 | 266 | ok/AMBER/ok | depends on today's stack |

## NYPM

### (a) BARE  (scored on exactly the same result files as (b) and (c); cells passing: 4000, capped at 4,000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | dib_400 | tape_libvol.cmf {"len": 10} | plain60/60 | +1160 | +1543 | +0.74 | 1086 | ok/ok/ok | bare only (not positive on own-stop) |
| 2 | lbrk_3_10 | momentum_rsi.mom_native {"len": 7, "lvl": 55} | plain60/60 | +1323 | +1957 | +0.85 | 778 | AMBER/ok/AMBER | bare only (not positive on own-stop) |
| 3 | swing_pct_8 | momentum_willr.break_native {"len": 7, "lvl": 10} | plain60/60 | +1060 | -783 | +0.68 | 827 | ok/ok/AMBER | strong on (b) too |
| 4 | bmsg_B500 | book_wall.near_fade {"m": 3, "d": 2} | plain60/60 | +1026 | -140 | +0.66 | 561 | ok/ok/AMBER | bare only (not positive on own-stop) |
| 5 | anch_R0830_B50 | xmarket_nkd.diverge {"w": 5} | sym15u | +1137 | +1081 | +0.73 | 225 | AMBER/ok/AMBER | strong on (b) too |
| 6 | dlt_30 | tape_libvol.force {"len": 26} | plain60/60 | +1115 | +960 | +0.71 | 941 | ok/AMBER/ok | bare only (not positive on own-stop) |
| 7 | bmsg_B500 | book_ice.follow {"thr": 2} | sym15u | +954 | +1181 | +0.61 | 247 | AMBER/AMBER/ok | bare only (not positive on own-stop) |
| 8 | dib_400 | trend_supertrend.native {"len": 14, "width": 3.0} | plain60/60 | +803 | +727 | +0.51 | 1033 | ok/ok/ok | bare only (not positive on own-stop) |
| 9 | dib_400 | trend_supertrend.plain {"len": 14, "width": 3.0} | plain60/60 | +757 | +1253 | +0.49 | 1013 | ok/ok/ok | strong on (b) too |
| 10 | dchg_20 | trend_heikin.flip_after_run_native {"len": 8, "width": 0.25} | plain60/60 | +882 | +731 | +0.57 | 640 | ok/AMBER/ok | strong on (b) too |

### (b) OWN-STOP (2 stops; 1.5 and 3 shown as neighbours)  (cells passing: 4000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | dlt_70 | bands_regchan.break_linreg {"n": 10, "k": 1.5} | sym15u | +2155 | +808 | +0.69 | 177 | AMBER/AMBER/AMBER | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |
| 2 | drb_1200 | bands_regchan.break_linreg {"n": 20, "k": 2.0} | plain60/60 | +972 | +77 | +0.62 | 288 | ok/ok/AMBER | L6M @1.5 stops +1000 / @3 stops <=0 or <100 tr |
| 3 | trb_240 | momentum_libosc.ao {"f": 3, "s": 21} | plain60/60 | +794 | +549 | +0.51 | 267 | ok/ok/ok | L6M @1.5 stops +332 / @3 stops +464 |
| 4 | entropy_B200 | levels_fibr_ib.reject {"tol": 0.5, "conf": "body"} | plain60/60 | +810 | +682 | +0.52 | 318 | ok/ok/ok | L6M @1.5 stops +844 / @3 stops <=0 or <100 tr |
| 5 | drb_400 | trend_macd.signal {"len": 12, "width": 0.05} | plain60/60 | +777 | +688 | +0.50 | 323 | ok/ok/ok | L6M @1.5 stops +973 / @3 stops <=0 or <100 tr |
| 6 | mom_10 | trend_ma_hma.cross {"len": 8, "width": 2, "hyst": 0.0} | plain60/60 | +687 | +122 | +0.44 | 207 | ok/ok/ok | L6M @1.5 stops +352 / @3 stops <=0 or <100 tr |
| 7 | cdr_250 | xmarket_fx.with_6J {"w": 1, "thr": 1.0} | sym15u | +1837 | +1382 | +0.59 | 170 | ok/ok/AMBER | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |
| 8 | dib_1200 | tape_libvol.force {"len": 7} | plain60/60 | +647 | +70 | +0.41 | 265 | ok/ok/ok | L6M @1.5 stops +756 / @3 stops <=0 or <100 tr |
| 9 | dib_240 | levels_vwap.break {"n": 2, "k": 0.25} | plain60/60 | +898 | +118 | +0.58 | 171 | ok/AMBER/ok | L6M @1.5 stops +928 / @3 stops +446 |
| 10 | swing_atr_0.4 | bands_envelope.break_sma {"n": 10, "pct": 0.05} | plain60/60 | +706 | +898 | +0.45 | 263 | ok/ok/ok | L6M @1.5 stops +507 / @3 stops <=0 or <100 tr |

### (c) CURRENT-STACK MASK (valid for ADDING a book to today's stack only; not valid for a rebuilt stack)  (cells passing: 4000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | mom_14 | bands_atrchan.break_ext_native {"clk": 5, "k": 1.5} | plain60/60 | +1008 | +1874 | +0.65 | 605 | ok/ok/ok | also positive on (b) |
| 2 | bmsg_B130 | levels_round.reject {"tol": 0.0, "conf": "close"} | sym15u | +1172 | +549 | +0.75 | 196 | ok/AMBER/ok | depends on today's stack |
| 3 | bmsg_B130 | levels_round.reject_native {"tol": 0.0, "conf": "close"} | sym15u | +1172 | +549 | +0.75 | 196 | ok/AMBER/ok | depends on today's stack |
| 4 | dltor_B320 | levels_trendline.break_native {"n": 3, "k": 0.5} | sym15u | +842 | -539 | +0.54 | 142 | ok/ok/ok | also positive on (b) |
| 5 | rng_28 | xmarket_commod.with_GC {"w": 1, "thr": 1.0} | plain60/60 | +1101 | +1215 | +0.71 | 445 | AMBER/AMBER/ok | depends on today's stack |
| 6 | dlt_250 | xmarket_commod.with_GC {"w": 1, "thr": 1.0} | plain60/60 | +1074 | +467 | +0.69 | 301 | AMBER/AMBER/ok | depends on today's stack |
| 7 | bmsg_B080 | xmarket_fast.follow_ES {"w": 5, "thr": 1.0} | plain60/60 | +798 | +602 | +0.51 | 392 | ok/ok/ok | depends on today's stack |
| 8 | ha_bmsg_B080 | xmarket_fast.follow_ES {"w": 5, "thr": 1.0} | plain60/60 | +798 | +602 | +0.51 | 392 | ok/ok/ok | depends on today's stack |
| 9 | entropy_B500 | trend_macd.hist_turn_native {"len": 12, "width": 0.01} | plain60/60 | +998 | +606 | +0.64 | 594 | AMBER/ok/ok | depends on today's stack |
| 10 | bmsg_B200 | book_sweep.resil_fade {"r": 1.25} | sym15u | +762 | +79 | +0.49 | 116 | ok/ok/ok | depends on today's stack |

