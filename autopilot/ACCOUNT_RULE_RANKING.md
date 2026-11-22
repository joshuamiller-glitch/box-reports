# DAYMASK_RANK - three screen rankings per session (W-DAYMASK, orders 1722Z + 1731Z), refreshed 2026-11-22 13:12Z

Screen level, 1 lot, $4.84 round trip in the points, last 26 weeks to the data end (L6M) and 13 weeks (L3M); EQUAL RISK (R = points / the cell stop in points; R/week); ranked by (red prior years, then min(L6M R/week, weakest prior-year R/week)); cells need L6M > 0 and >= 100 trades under THAT variant.
(a) BARE: no account rule. (b) OWN-STOP: stack-independent; no new entries for the rest of the 17:00-ET trading day once the cell itself is down 2 stops on the day (1.5 and 3 stops shown as neighbours). THIS ranking carries the shortlist. (c) CURRENT-STACK MASK: entries blocked while today's JL3 stack has >= 22 closes and day P&L <= -$4,200 live (JL3 history, code/th_grid/gday.py); valid for ADDING a book to today's stack only; not valid for a rebuilt stack; information, never the sole reason to shortlist or drop.
RE-RUN PROGRESS: 2026-11-18T21:52:27Z p1real done 5425 of 5425 pairs, 15820 s (plus every new grid job since 17:30Z carries (b)/(c) by itself).
COVERAGE CAUTION: (b) and (c) exist only for the (row, module) result files already re-run with GL_OWNSTOP / GL_ACCT (the bare top-4,000 cells per session + candidates + shortlist, started 17:28Z); the bare table covers every scored cell. Until the whole grid has been re-run the (b)/(c) tables are biased to cells that were already strong on bare. Cells scored per table are shown in each heading.

## Asia
Cells passing per session (a / b / c): Asia 4000 / 4000 / 4000; London 4000 / 4000 / 4000; NYAM 4000 / 4000 / 4000; NYPM 4000 / 4000 / 4000


### (a) BARE  (scored on exactly the same result files as (b) and (c); cells passing: 4000, capped at 4,000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | trb_400 | levels_vwap.break {"n": 3, "k": 0.5} | asym20u/10u | +758 | -385 | +0.49 | 271 | ok/ok/ok | strong on (b) too |
| 2 | vnorm_150 | levels_fibr_dev.false_break_native {"M": 2, "k": 0.5} | sym15u | +705 | -631 | +0.45 | 281 | ok/ok/ok | strong on (b) too |
| 3 | vnorm_150 | levels_fib5.break {"n": 1, "k": 0.0} | sym15u | +858 | -469 | +0.55 | 304 | AMBER/AMBER/ok | strong on (b) too |
| 4 | vnorm_150 | levels_fib5.break_native {"n": 1, "k": 0.0} | sym15u | +858 | -469 | +0.55 | 304 | AMBER/AMBER/ok | strong on (b) too |
| 5 | cusum_40 | momentum_rsi.mom_native {"len": 14, "lvl": 55} | plain60/60 | +624 | -45 | +0.40 | 608 | ok/ok/ok | bare only (not positive on own-stop) |
| 6 | vnorm_150 | levels_fib15.reject_native {"tol": 1.0, "conf": "body"} | sym15u | +834 | -701 | +0.53 | 302 | AMBER/AMBER/ok | bare only (not positive on own-stop) |
| 7 | dib_240 | momentum_mvote.v3of5_native {"scale": 1.0, "thr": 0.25} | plain60/60 | +616 | +1066 | +0.39 | 777 | ok/ok/ok | bare only (not positive on own-stop) |
| 8 | tm180 | levels_vwap.break_native {"n": 3, "k": 0.5} | plain60/60 | +605 | +1164 | +0.39 | 562 | ok/ok/ok | strong on (b) too |
| 9 | vib_3500 | momentum_stoch.zone_break_native {"len": 14, "lvl": 70} | sym15u | +561 | -724 | +0.36 | 313 | ok/ok/ok | strong on (b) too |
| 10 | trb_400 | levels_vwap.break {"n": 2, "k": 0.5} | asym15u/30u | +632 | +305 | +0.41 | 252 | ok/ok/ok | strong on (b) too |

### (b) OWN-STOP (2 stops; 1.5 and 3 shown as neighbours)  (cells passing: 4000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | trb_400 | levels_vwap.break {"n": 3, "k": 0.5} | asym20u/10u | +930 | -376 | +0.60 | 254 | AMBER/AMBER/ok | L6M @1.5 stops +810 / @3 stops +866 |
| 2 | vib_700 | pullback_ema.count {"len": 50, "n": 4} | sym15u | +862 | +234 | +0.55 | 360 | AMBER/ok/AMBER | L6M @1.5 stops +624 / @3 stops <=0 or <100 tr |
| 3 | dol_350 | momentum_mvote.v3of5 {"scale": 1.0, "thr": 0.25} | plain60/60 | +629 | +930 | +0.40 | 416 | ok/ok/ok | L6M @1.5 stops +629 / @3 stops +616 |
| 4 | mrenko_20 | momentum_er.trend_z {"len": 10, "thr": 0.4} | plain60/60 | +870 | +360 | +0.56 | 432 | ok/ok/AMBER | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |
| 5 | trb_400 | levels_vwap.break {"n": 3, "k": 0.5} | asym15u/30u | +602 | -390 | +0.39 | 226 | ok/ok/ok | L6M @1.5 stops +602 / @3 stops +538 |
| 6 | tsf_5_100 | structure_breakout.brk {"n": 40, "buf": 0.0} | sym15u | +670 | -804 | +0.43 | 236 | ok/ok/ok | L6M @1.5 stops +706 / @3 stops +248 |
| 7 | vib_3500 | momentum_stoch.zone_break_native {"len": 14, "lvl": 70} | sym15u | +713 | -429 | +0.46 | 293 | AMBER/AMBER/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops +749 |
| 8 | tsf_5_100 | bands_donchian.break_native {"clk": 5, "buf": 0.0} | sym15u | +738 | -862 | +0.47 | 260 | AMBER/AMBER/ok | L6M @1.5 stops +620 / @3 stops +386 |
| 9 | time_m_7 | xmarket_rty.confirm {"w": 30} | plain60/60 | +634 | +74 | +0.41 | 386 | ok/ok/ok | L6M @1.5 stops +634 / @3 stops +598 |
| 10 | cusum_40 | momentum_rsi.mom_native {"len": 21, "lvl": 55} | plain60/60 | +562 | -75 | +0.36 | 470 | ok/ok/ok | L6M @1.5 stops +562 / @3 stops <=0 or <100 tr |

### (c) CURRENT-STACK MASK (valid for ADDING a book to today's stack only; not valid for a rebuilt stack)  (cells passing: 4000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | trb_400 | levels_vwap.break {"n": 3, "k": 0.5} | asym20u/10u | +755 | -385 | +0.48 | 270 | ok/ok/ok | also positive on (b) |
| 2 | vnorm_150 | levels_fib5.break {"n": 1, "k": 0.0} | sym15u | +858 | -469 | +0.55 | 304 | AMBER/AMBER/ok | also positive on (b) |
| 3 | vnorm_150 | levels_fib5.break_native {"n": 1, "k": 0.0} | sym15u | +858 | -469 | +0.55 | 304 | AMBER/AMBER/ok | also positive on (b) |
| 4 | vnorm_150 | levels_fibr_dev.false_break_native {"M": 2, "k": 0.5} | sym15u | +741 | -631 | +0.47 | 280 | AMBER/ok/AMBER | also positive on (b) |
| 5 | cusum_40 | momentum_rsi.mom_native {"len": 14, "lvl": 55} | plain60/60 | +723 | +62 | +0.46 | 604 | ok/AMBER/ok | depends on today's stack |
| 6 | tm180 | levels_vwap.break_native {"n": 3, "k": 0.5} | plain60/60 | +626 | +1202 | +0.40 | 556 | ok/ok/ok | also positive on (b) |
| 7 | trb_400 | levels_vwap.break {"n": 2, "k": 0.5} | asym15u/30u | +688 | +305 | +0.44 | 251 | AMBER/ok/ok | also positive on (b) |
| 8 | vib_3500 | momentum_stoch.zone_break_native {"len": 14, "lvl": 70} | sym15u | +551 | -724 | +0.35 | 312 | ok/ok/ok | also positive on (b) |
| 9 | cusum_20 | bands_bollinger.break_native {"clk": 5, "k": 2.0} | plain60/60 | +682 | -1182 | +0.44 | 748 | ok/AMBER/ok | depends on today's stack |
| 10 | vol_500 | levels_mmove.break {"n": 2, "k": 0.5} | plain60/60 | +675 | -92 | +0.43 | 598 | AMBER/AMBER/AMBER | also positive on (b) |

## London

### (a) BARE  (scored on exactly the same result files as (b) and (c); cells passing: 4000, capped at 4,000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | ha_bmsgq_B080 | tape_libvol.vwmacd {"f": 8, "s": 17} | sym15u | +908 | -79 | +0.58 | 239 | ok/ok/ok | bare only (not positive on own-stop) |
| 2 | typ_bmsgq_B080 | bands_atrchan.fade_ema_native {"clk": 5, "k": 1.0} | sym15u | +865 | -1 | +0.55 | 231 | ok/ok/ok | strong on (b) too |
| 3 | typ_bmsgq_B080 | bands_envelope.fade_ema_native {"clk": 5, "k": 1.0} | sym15u | +865 | -1 | +0.55 | 231 | ok/ok/ok | strong on (b) too |
| 4 | typ_bmsgq_B080 | bands_keltner.fade_native {"clk": 5, "k": 1.0} | sym15u | +865 | -1 | +0.55 | 231 | ok/ok/ok | strong on (b) too |
| 5 | vnorm_700 | xmarket_rates.with_ZN {"w": 1, "thr": 1.0} | sym15u | +946 | +1390 | +0.61 | 264 | ok/ok/ok | bare only (not positive on own-stop) |
| 6 | med_bmsgq_B080 | tape_libvol.vwmacd {"f": 8, "s": 17} | sym15u | +783 | -106 | +0.50 | 240 | ok/ok/ok | strong on (b) too |
| 7 | vol_2600 | levels_fib5.retest_native {"M": 10, "tol": 0.5} | plain60/60 | +791 | +384 | +0.51 | 611 | ok/ok/ok | bare only (not positive on own-stop) |
| 8 | dol_750 | levels_fib5.break_native {"n": 3, "k": 0.5} | asym20u/10u | +822 | -260 | +0.53 | 251 | ok/ok/ok | bare only (not positive on own-stop) |
| 9 | med_rngor_B200 | trend_ma_hma.cross {"len": 34, "width": 4, "hyst": 0.0} | sym15u | +736 | -344 | +0.47 | 260 | ok/ok/ok | strong on (b) too |
| 10 | bmsg_B320 | barnative_speed.burst_go {"len": 10, "r": 0.25} | sym15u | +702 | +131 | +0.45 | 287 | ok/ok/ok | strong on (b) too |

### (b) OWN-STOP (2 stops; 1.5 and 3 shown as neighbours)  (cells passing: 4000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | typ_bmsgq_B080 | bands_atrchan.fade_ema_native {"clk": 5, "k": 1.0} | sym15u | +958 | +60 | +0.61 | 224 | ok/ok/ok | L6M @1.5 stops +958 / @3 stops +871 |
| 2 | typ_bmsgq_B080 | bands_envelope.fade_ema_native {"clk": 5, "k": 1.0} | sym15u | +958 | +60 | +0.61 | 224 | ok/ok/ok | L6M @1.5 stops +958 / @3 stops +871 |
| 3 | typ_bmsgq_B080 | bands_keltner.fade_native {"clk": 5, "k": 1.0} | sym15u | +958 | +60 | +0.61 | 224 | ok/ok/ok | L6M @1.5 stops +958 / @3 stops +871 |
| 4 | vol_500 | levels_trendline.break {"n": 2, "k": 0.25} | plain60/60 | +977 | -156 | +0.63 | 293 | AMBER/ok/ok | L6M @1.5 stops +908 / @3 stops <=0 or <100 tr |
| 5 | t3_entropy_B080 | tape_libvol.vwmacd {"f": 8, "s": 17} | sym15u | +1034 | +62 | +0.66 | 225 | AMBER/AMBER/ok | L6M @1.5 stops +1034 / @3 stops <=0 or <100 tr |
| 6 | trend_10 | xmarket_rates.with_ZB {"w": 5, "thr": 1.0} | sym15u | +951 | +1213 | +0.61 | 212 | AMBER/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |
| 7 | med_bmsgq_B080 | tape_libvol.vwmacd {"f": 8, "s": 17} | sym15u | +861 | -83 | +0.55 | 230 | ok/ok/AMBER | L6M @1.5 stops +861 / @3 stops +783 |
| 8 | trb_700 | tape_delta.follow_native {"L": 3600, "z": 2.0} | sym15u | +705 | +865 | +0.45 | 156 | ok/ok/ok | L6M @1.5 stops +201 / @3 stops +477 |
| 9 | bmsg_B320 | barnative_speed.burst_go {"len": 10, "r": 0.25} | sym15u | +687 | +276 | +0.44 | 269 | ok/ok/ok | L6M @1.5 stops +687 / @3 stops +877 |
| 10 | bmsg_B500 | book_pslope.fade_sm {"L": 100, "z": 1.5, "sm": 3} | sym15u | +898 | -1732 | +0.58 | 229 | AMBER/ok/AMBER | L6M @1.5 stops +898 / @3 stops <=0 or <100 tr |

### (c) CURRENT-STACK MASK (valid for ADDING a book to today's stack only; not valid for a rebuilt stack)  (cells passing: 4000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | bmsg_B320 | barnative_speed.burst_go {"len": 10, "r": 0.25} | sym15u | +1175 | +593 | +0.75 | 236 | ok/AMBER/AMBER | also positive on (b) |
| 2 | vol_500 | levels_trendline.break {"n": 2, "k": 0.25} | plain60/60 | +984 | +224 | +0.63 | 347 | AMBER/ok/ok | also positive on (b) |
| 3 | ha_sessrng_B080 | xmarket_rates.with_ZB {"w": 5, "thr": 1.0} | sym15u | +954 | +1179 | +0.61 | 186 | AMBER/ok/ok | depends on today's stack |
| 4 | kal_sessrng_B080 | xmarket_rates.with_ZB {"w": 5, "thr": 1.0} | sym15u | +954 | +1179 | +0.61 | 186 | AMBER/ok/ok | depends on today's stack |
| 5 | med_sessrng_B080 | xmarket_rates.with_ZB {"w": 5, "thr": 1.0} | sym15u | +954 | +1179 | +0.61 | 186 | AMBER/ok/ok | depends on today's stack |
| 6 | t3_sessrng_B080 | xmarket_rates.with_ZB {"w": 5, "thr": 1.0} | sym15u | +954 | +1179 | +0.61 | 186 | AMBER/ok/ok | depends on today's stack |
| 7 | typ_sessrng_B080 | xmarket_rates.with_ZB {"w": 5, "thr": 1.0} | sym15u | +954 | +1179 | +0.61 | 186 | AMBER/ok/ok | depends on today's stack |
| 8 | vnorm_700 | book_ice.follow {"thr": 1} | plain60/60 | +870 | -88 | +0.56 | 472 | ok/ok/AMBER | also positive on (b) |
| 9 | vnorm_700 | book_ice.follow_native {"thr": 1, "sm": 60} | plain60/60 | +870 | -88 | +0.56 | 472 | ok/ok/AMBER | also positive on (b) |
| 10 | volor_B130 | levels_fib5.retest {"M": 6, "tol": 0.5} | sym15u | +924 | +236 | +0.59 | 218 | AMBER/ok/ok | also positive on (b) |

## NYAM

### (a) BARE  (scored on exactly the same result files as (b) and (c); cells passing: 4000, capped at 4,000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | med_dltor_B200 | structure_level.round_break {"grid": 100, "buf": 0.25} | sym15u | +2402 | +954 | +1.54 | 416 | AMBER/AMBER/ok | bare only (not positive on own-stop) |
| 2 | sessrng_B030 | book_ofi.follow_sm {"L": 100, "z": 1.5, "sm": 3} | sym15u | +1985 | +624 | +1.27 | 296 | ok/ok/ok | strong on (b) too |
| 3 | kal_micro_B200 | pullback_ema.count {"len": 10, "n": 2} | sym15u | +1967 | +206 | +1.26 | 379 | AMBER/ok/ok | strong on (b) too |
| 4 | lbrk_5_40 | xmarket_fast.revert_ES {"w": 60, "thr": 2.0} | sym15u | +2111 | +831 | +1.35 | 145 | AMBER/ok/AMBER | bare only (not positive on own-stop) |
| 5 | vnorm_1500 | momentum_willr.break {"len": 7, "lvl": 10} | sym15u | +1969 | +534 | +1.26 | 522 | AMBER/ok/ok | bare only (not positive on own-stop) |
| 6 | med_micro_B080 | levels_round.break {"n": 2, "k": 0.25} | sym15u | +1526 | +1131 | +0.98 | 485 | ok/ok/ok | bare only (not positive on own-stop) |
| 7 | t3_dltor_B080 | levels_round.break {"n": 2, "k": 0.25} | sym15u | +1711 | +719 | +1.10 | 508 | ok/ok/ok | strong on (b) too |
| 8 | lbrk_4_20 | levels_fibr_dev.break {"n": 1, "k": 0.0} | sym15u | +1691 | -962 | +1.08 | 411 | ok/ok/ok | bare only (not positive on own-stop) |
| 9 | lbrk_4_20 | levels_fibr_dev.break_native {"n": 1, "k": 0.0} | sym15u | +1691 | -962 | +1.08 | 411 | ok/ok/ok | bare only (not positive on own-stop) |
| 10 | med_bmsgq_B200 | tape_stoprun.fade {"N": 10, "k": 0.0} | sym15u | +1723 | +1816 | +1.10 | 497 | ok/ok/ok | bare only (not positive on own-stop) |

### (b) OWN-STOP (2 stops; 1.5 and 3 shown as neighbours)  (cells passing: 4000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | med_entropy_B080 | levels_round.retest_native {"M": 6, "tol": 0.5} | sym15u | +2501 | +1601 | +1.60 | 348 | AMBER/ok/AMBER | L6M @1.5 stops +1806 / @3 stops +2299 |
| 2 | trend_20 | levels_vwap.break_native {"n": 2, "k": 0.25} | sym15u | +2161 | +1183 | +1.39 | 258 | AMBER/ok/ok | L6M @1.5 stops +2298 / @3 stops <=0 or <100 tr |
| 3 | trb_2000 | levels_vwap.break {"n": 3, "k": 0.5} | sym15u | +1967 | -1066 | +1.26 | 242 | ok/ok/ok | L6M @1.5 stops +1725 / @3 stops +1714 |
| 4 | sessrng_B030 | book_ofi.follow_sm {"L": 100, "z": 1.5, "sm": 3} | sym15u | +2383 | +969 | +1.53 | 244 | AMBER/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops +2096 |
| 5 | t3_qmid_B200 | bands_envelope.break_ema {"n": 10, "pct": 0.05} | sym15u | +1627 | +1246 | +1.04 | 347 | ok/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops +991 |
| 6 | med_volor_B200 | structure_level.round_break {"grid": 100, "buf": 0.25} | sym15u | +1842 | +959 | +1.18 | 289 | ok/ok/ok | L6M @1.5 stops +900 / @3 stops <=0 or <100 tr |
| 7 | t3_dltor_B080 | levels_round.break {"n": 2, "k": 0.25} | sym15u | +2133 | +679 | +1.37 | 380 | AMBER/AMBER/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |
| 8 | t3_micro_B200 | bands_envelope.break_ema {"n": 10, "pct": 0.05} | sym15u | +1552 | +1171 | +1.00 | 345 | ok/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops +985 |
| 9 | tsf_2_400 | levels_swsr5.retest_native {"M": 6, "tol": 0.5} | sym15u | +1610 | +1155 | +1.03 | 278 | ok/ok/ok | L6M @1.5 stops +1243 / @3 stops +1523 |
| 10 | volor_B030 | book_ofi.follow_sm {"L": 100, "z": 1.5, "sm": 3} | sym15u | +1537 | +330 | +0.99 | 282 | ok/ok/ok | L6M @1.5 stops +1725 / @3 stops +1263 |

### (c) CURRENT-STACK MASK (valid for ADDING a book to today's stack only; not valid for a rebuilt stack)  (cells passing: 4000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | dol_1700 | book_ofi.follow_sm {"L": 200, "z": 2.0, "sm": 3} | asym20u/10u | +2400 | +1447 | +1.54 | 133 | AMBER/ok/AMBER | depends on today's stack |
| 2 | sessrng_B030 | book_ofi.follow_sm {"L": 100, "z": 1.5, "sm": 3} | sym15u | +1995 | +566 | +1.28 | 181 | ok/ok/ok | also positive on (b) |
| 3 | trb_700 | levels_vwap.break {"n": 2, "k": 0.5} | asym15u/30u | +1601 | -790 | +1.03 | 216 | ok/ok/ok | also positive on (b) |
| 4 | dol_1100 | bands_keltner.walk_native {"clk": 5, "k": 1.0, "N": 2} | sym15u | +1556 | -107 | +1.00 | 204 | ok/ok/ok | also positive on (b) |
| 5 | dol_1100 | book_dwm.drift_follow_native {"L": 1800, "z": 1.5} | sym15u | +2142 | +502 | +1.37 | 299 | AMBER/ok/AMBER | depends on today's stack |
| 6 | trb_700 | levels_vwap.break {"n": 2, "k": 0.25} | asym10u/20u | +1574 | -598 | +1.01 | 216 | ok/ok/ok | depends on today's stack |
| 7 | trb_700 | levels_vwap.break {"n": 2, "k": 0.5} | sym30u | +1496 | -875 | +0.96 | 214 | ok/ok/ok | also positive on (b) |
| 8 | cusum_20 | book_ofi.follow {"L": 200, "z": 2.0} | plain60/60 | +1493 | +667 | +0.96 | 633 | ok/ok/ok | also positive on (b) |
| 9 | ha_bmsgq_B200 | levels_round.retest {"M": 6, "tol": 0.5} | sym15u | +1885 | -312 | +1.21 | 318 | ok/AMBER/ok | depends on today's stack |
| 10 | med_volor_B080 | structure_breakout.brk_native {"minutes": 5, "buf": 0.0} | sym15u | +1448 | -307 | +0.93 | 257 | ok/ok/ok | depends on today's stack |

## NYPM

### (a) BARE  (scored on exactly the same result files as (b) and (c); cells passing: 4000, capped at 4,000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | trb_700 | xmarket_fast.follow_RTY {"w": 5, "thr": 1.0} | sym15u | +1452 | +1367 | +0.93 | 354 | ok/AMBER/ok | bare only (not positive on own-stop) |
| 2 | dol_750 | levels_trendline.reject_native {"tol": 0.5, "conf": "body"} | sym15u | +1656 | -504 | +1.06 | 238 | AMBER/ok/ok | strong on (b) too |
| 3 | vib_15000 | levels_trendline.reject_native {"tol": 0.5, "conf": "body"} | sym15u | +1580 | +308 | +1.01 | 224 | AMBER/AMBER/ok | bare only (not positive on own-stop) |
| 4 | tsf_2_100 | levels_trendline.break {"n": 3, "k": 0.5} | sym15u | +1489 | +512 | +0.95 | 264 | AMBER/AMBER/ok | strong on (b) too |
| 5 | dib_400 | tape_libvol.cmf {"len": 10} | plain60/60 | +1160 | +1543 | +0.74 | 1086 | ok/ok/ok | bare only (not positive on own-stop) |
| 6 | vib_70000 | tape_speed.fade_native {"f": 2.0, "L": 1800} | sym15u | +1081 | -253 | +0.69 | 195 | ok/ok/ok | strong on (b) too |
| 7 | vnorm_1000 | structure_level.round_reject {"grid": 50, "buf": 0.0} | sym15u | +1250 | +1252 | +0.80 | 322 | ok/ok/ok | bare only (not positive on own-stop) |
| 8 | dol_1700 | levels_trendline.reject_native {"tol": 0.5, "conf": "body"} | sym15u | +1099 | -1207 | +0.70 | 234 | ok/ok/ok | strong on (b) too |
| 9 | t3_sessrng_B200 | tape_libvol.obv {"len": 10} | plain60/60 | +1193 | +1124 | +0.76 | 794 | ok/ok/ok | bare only (not positive on own-stop) |
| 10 | vnorm_1500 | levels_trendline.reject_native {"tol": 0.5, "conf": "body"} | sym15u | +1134 | -1187 | +0.73 | 243 | ok/ok/ok | bare only (not positive on own-stop) |

### (b) OWN-STOP (2 stops; 1.5 and 3 shown as neighbours)  (cells passing: 4000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | micro_B130 | book_sweep.resil_fade {"r": 1.0} | sym15u | +1112 | +1430 | +0.71 | 166 | ok/ok/ok | L6M @1.5 stops +597 / @3 stops +1385 |
| 2 | qmid_B130 | book_sweep.resil_fade {"r": 1.0} | sym15u | +1112 | +1430 | +0.71 | 166 | ok/ok/ok | L6M @1.5 stops +597 / @3 stops +1385 |
| 3 | trb_700 | tape_libvol.vwmacd {"f": 8, "s": 17} | sym15u | +1153 | -184 | +0.74 | 217 | ok/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops +560 |
| 4 | tsf_10_60 | manual_macd.sigcross {"f": 5, "s": 13, "g": 5} | sym15u | +1208 | -331 | +0.77 | 204 | AMBER/AMBER/ok | L6M @1.5 stops +408 / @3 stops <=0 or <100 tr |
| 5 | tsf_10_60 | trend_macd.signal {"len": 6, "width": 0.0} | sym15u | +1176 | -355 | +0.75 | 204 | ok/AMBER/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |
| 6 | time_s_5 | bands_bollinger.walk {"n": 20, "k": 2.0, "N": 2} | plain60/60 | +995 | +365 | +0.64 | 353 | ok/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops +390 |
| 7 | vib_70000 | tape_speed.fade_native {"f": 2.0, "L": 1800} | sym15u | +1013 | -88 | +0.65 | 143 | ok/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops +347 |
| 8 | trb_700 | manual_macd.sigcross {"f": 12, "s": 26, "g": 9} | sym15u | +937 | +397 | +0.60 | 197 | ok/ok/ok | L6M @1.5 stops +1174 / @3 stops <=0 or <100 tr |
| 9 | ha_micro_B080 | book_ice.follow_sm {"thr": 2, "sm": 3} | sym15u | +954 | +514 | +0.61 | 131 | ok/ok/ok | L6M @1.5 stops +1097 / @3 stops +776 |
| 10 | ha_qmid_B080 | book_ice.follow_sm {"thr": 2, "sm": 3} | sym15u | +954 | +514 | +0.61 | 131 | ok/ok/ok | L6M @1.5 stops +1097 / @3 stops +776 |

### (c) CURRENT-STACK MASK (valid for ADDING a book to today's stack only; not valid for a rebuilt stack)  (cells passing: 4000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | vib_15000 | book_pslope.follow {"L": 100, "z": 1.5} | sym15u | +1137 | +614 | +0.73 | 173 | ok/ok/ok | also positive on (b) |
| 2 | mrenko_14 | levels_fibr_dev.break {"n": 2, "k": 0.0} | plain60/60 | +1063 | +122 | +0.68 | 499 | ok/ok/ok | also positive on (b) |
| 3 | mrenko_14 | levels_fibr_dev.break_native {"n": 2, "k": 0.0} | plain60/60 | +1063 | +122 | +0.68 | 499 | ok/ok/ok | also positive on (b) |
| 4 | kal_rngor_B080 | levels_round.retest {"M": 6, "tol": 0.5} | sym15u | +1024 | +671 | +0.66 | 210 | ok/ok/ok | depends on today's stack |
| 5 | micro_B030 | xmarket_fast.follow_RTY {"w": 5, "thr": 1.0} | sym15u | +1283 | +430 | +0.82 | 130 | ok/AMBER/ok | depends on today's stack |
| 6 | qmid_B030 | xmarket_fast.follow_RTY {"w": 5, "thr": 1.0} | sym15u | +1283 | +430 | +0.82 | 130 | ok/AMBER/ok | depends on today's stack |
| 7 | vol_350 | levels_fibr_dev.break {"n": 3, "k": 0.25} | plain60/60 | +1033 | +694 | +0.66 | 528 | ok/ok/ok | depends on today's stack |
| 8 | volor_B130 | levels_trendline.reject_native {"tol": 1.0, "conf": "body"} | sym15u | +984 | -925 | +0.63 | 152 | ok/ok/ok | depends on today's stack |
| 9 | kal_sessrng_B200 | levels_round.retest {"M": 6, "tol": 0.5} | plain60/60 | +1186 | +925 | +0.76 | 646 | ok/AMBER/ok | depends on today's stack |
| 10 | vib_10000 | levels_trendline.reject_native {"tol": 1.0, "conf": "body"} | sym15u | +1003 | -479 | +0.64 | 144 | ok/ok/ok | depends on today's stack |


Note: ACCOUNT_RULE_RANKING.md carries the same three rankings side by side as DAYMASK_RANK.md (one builder).
