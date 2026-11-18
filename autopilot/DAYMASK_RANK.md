# DAYMASK_RANK - three screen rankings per session (W-DAYMASK, orders 1722Z + 1731Z), refreshed 2026-11-18 17:34Z

Screen level, 1 lot, $4.84 round trip in the points, last 26 weeks to the data end (L6M) and 13 weeks (L3M); EQUAL RISK (R = points / the cell stop in points; R/week); ranked by (red prior years, then min(L6M R/week, weakest prior-year R/week)); cells need L6M > 0 and >= 100 trades under THAT variant.
(a) BARE: no account rule. (b) OWN-STOP: stack-independent; no new entries for the rest of the 17:00-ET trading day once the cell itself is down 2 stops on the day (1.5 and 3 stops shown as neighbours). THIS ranking carries the shortlist. (c) CURRENT-STACK MASK: entries blocked while today's JL3 stack has >= 22 closes and day P&L <= -$4,200 live (JL3 history, code/th_grid/gday.py); valid for ADDING a book to today's stack only; not valid for a rebuilt stack; information, never the sole reason to shortlist or drop.
RE-RUN PROGRESS: 2026-11-18T17:32:43Z p1real done 210 of 5425 pairs, 237 s (plus every new grid job since 17:30Z carries (b)/(c) by itself).
COVERAGE CAUTION: (b) and (c) exist only for the (row, module) result files already re-run with GL_OWNSTOP / GL_ACCT (the bare top-4,000 cells per session + candidates + shortlist, started 17:28Z); the bare table covers every scored cell. Until the whole grid has been re-run the (b)/(c) tables are biased to cells that were already strong on bare. Cells scored per table are shown in each heading.

## Asia
Cells passing per session (a / b / c): Asia 4000 / 4000 / 4000; London 4000 / 4000 / 4000; NYAM 4000 / 4000 / 4000; NYPM 4000 / 4000 / 4000


### (a) BARE  (scored on exactly the same result files as (b) and (c); cells passing: 4000, capped at 4,000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | cusum_80 | momentum_cci.zero_native {"len": 30, "lvl": 50} | plain60/60 | +435 | -495 | +0.28 | 441 | ok/ok/ok | bare only (not positive on own-stop) |
| 2 | dchg_28 | bands_regchan.break_linreg {"n": 20, "k": 2.0} | plain60/60 | +381 | -584 | +0.24 | 442 | ok/ok/ok | bare only (not positive on own-stop) |
| 3 | dchg_10 | bands_vwap.walk_native {"clk": 6, "k": 1.0, "N": 2} | plain60/60 | +355 | +530 | +0.23 | 538 | AMBER/ok/ok | strong on (b) too |
| 4 | dchg_10 | bands_atrchan.break_ext {"n": 40, "atr": 14, "k": 4.0} | plain60/60 | +325 | +43 | +0.21 | 464 | ok/ok/ok | bare only (not positive on own-stop) |
| 5 | cusum_56 | momentum_roc.break_native {"len": 5, "wd": 0.5} | sym15u | +523 | -246 | +0.17 | 315 | ok/ok/ok | strong on (b) too |
| 6 | dchg_10 | bands_vwap.walk {"minbars": 10, "k": 1.0, "N": 2} | plain60/60 | +266 | +189 | +0.17 | 537 | ok/ok/ok | strong on (b) too |
| 7 | dchg_56 | xmarket_mega.diverge {"w": 30} | plain60/60 | +315 | -256 | +0.20 | 132 | AMBER/ok/ok | strong on (b) too |
| 8 | cdr_400 | levels_vwap.break_native {"n": 2, "k": 0.25} | plain60/60 | +226 | -165 | +0.14 | 288 | ok/ok/ok | strong on (b) too |
| 9 | dchg_28 | bands_atrchan.break_ext_native {"clk": 5, "k": 1.0} | plain60/60 | +224 | +1 | +0.14 | 445 | ok/ok/ok | strong on (b) too |
| 10 | dchg_28 | bands_regchan.break_stderr {"n": 20, "k": 2.0} | plain60/60 | +267 | -435 | +0.17 | 283 | AMBER/ok/ok | strong on (b) too |

### (b) OWN-STOP (2 stops; 1.5 and 3 shown as neighbours)  (cells passing: 4000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | cusum_56 | momentum_roc.break_native {"len": 20, "wd": 1.0} | plain60/60 | +405 | +757 | +0.26 | 407 | AMBER/ok/ok | L6M @1.5 stops +405 / @3 stops +739 |
| 2 | dchg_20 | bands_bollinger.break_native {"clk": 5, "k": 1.5} | plain60/60 | +270 | +774 | +0.17 | 362 | ok/ok/ok | L6M @1.5 stops +270 / @3 stops +263 |
| 3 | cusum_56 | momentum_mvote.v3of5 {"scale": 0.25, "thr": 0.25} | plain60/60 | +272 | +1289 | +0.17 | 333 | ok/ok/ok | L6M @1.5 stops +272 / @3 stops <=0 or <100 tr |
| 4 | cdr_100 | levels_fib15.break {"n": 3, "k": 0.5} | plain60/60 | +286 | +178 | +0.18 | 259 | AMBER/ok/AMBER | L6M @1.5 stops +286 / @3 stops +733 |
| 5 | dchg_14 | bands_atrchan.break_ext {"n": 40, "atr": 14, "k": 4.0} | sym15u | +491 | -325 | +0.16 | 152 | ok/ok/ok | L6M @1.5 stops +491 / @3 stops +212 |
| 6 | dchg_56 | xmarket_mega.diverge {"w": 5} | plain60/60 | +253 | +141 | +0.16 | 237 | ok/ok/ok | L6M @1.5 stops +253 / @3 stops +439 |
| 7 | dchg_28 | bands_atrchan.break_ema {"n": 10, "atr": 14, "k": 1.5} | sym15u | +534 | -659 | +0.17 | 240 | AMBER/ok/ok | L6M @1.5 stops +534 / @3 stops +866 |
| 8 | cusum_56 | bands_regchan.break_stderr_native {"clk": 10, "k": 2.0} | plain60/60 | +233 | +150 | +0.15 | 202 | ok/ok/ok | L6M @1.5 stops +233 / @3 stops +1032 |
| 9 | dlt_100 | barnative_delta.run {"n": 5, "thr": 0.0} | plain60/60 | +190 | +648 | +0.12 | 333 | ok/ok/ok | L6M @1.5 stops +190 / @3 stops +224 |
| 10 | cusum_14 | bands_vwap.break_native {"clk": 12, "k": 1.0} | sym15u | +498 | -597 | +0.16 | 268 | AMBER/ok/ok | L6M @1.5 stops +380 / @3 stops <=0 or <100 tr |

### (c) CURRENT-STACK MASK (valid for ADDING a book to today's stack only; not valid for a rebuilt stack)  (cells passing: 4000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | dchg_28 | bands_regchan.break_linreg {"n": 20, "k": 2.0} | plain60/60 | +377 | -579 | +0.24 | 440 | ok/ok/ok | depends on today's stack |
| 2 | cdr_100 | levels_vwap.break {"n": 3, "k": 0.0} | plain60/60 | +317 | +497 | +0.20 | 528 | ok/ok/ok | depends on today's stack |
| 3 | cdr_100 | levels_vwap.break_native {"n": 3, "k": 0.0} | plain60/60 | +317 | +497 | +0.20 | 528 | ok/ok/ok | depends on today's stack |
| 4 | cdr_100 | levels_vwap.break_native {"n": 2, "k": 0.5} | plain60/60 | +364 | +1033 | +0.23 | 554 | ok/ok/AMBER | depends on today's stack |
| 5 | dchg_10 | bands_vwap.walk_native {"clk": 6, "k": 1.0, "N": 2} | plain60/60 | +355 | +530 | +0.23 | 538 | AMBER/ok/ok | also positive on (b) |
| 6 | dlt_400 | structure_libpattern.nr {"n": 4} | plain60/60 | +328 | +14 | +0.21 | 121 | ok/ok/ok | depends on today's stack |
| 7 | cusum_28 | levels_vwap.retest {"M": 10, "tol": 0.5} | plain60/60 | +292 | +776 | +0.19 | 471 | ok/ok/ok | depends on today's stack |
| 8 | dlt_100 | momentum_stoch.zone_break_native {"len": 21, "lvl": 90} | plain60/60 | +380 | +113 | +0.24 | 477 | ok/ok/AMBER | depends on today's stack |
| 9 | dchg_10 | bands_atrchan.break_ext {"n": 40, "atr": 14, "k": 4.0} | plain60/60 | +374 | +92 | +0.24 | 460 | AMBER/ok/ok | depends on today's stack |
| 10 | cdr_250 | levels_opens.break_native {"n": 2, "k": 0.25} | plain60/60 | +394 | +607 | +0.25 | 300 | AMBER/AMBER/ok | also positive on (b) |

## London

### (a) BARE  (scored on exactly the same result files as (b) and (c); cells passing: 4000, capped at 4,000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | dlt_150 | bands_regchan.fade_linreg_native {"clk": 10, "k": 2.0} | plain60/60 | +471 | -91 | +0.30 | 150 | ok/ok/ok | bare only (not positive on own-stop) |
| 2 | cdr_250 | levels_vwap_bands.reject {"tol": 0.0, "conf": "close"} | plain60/60 | +352 | +384 | +0.23 | 446 | ok/ok/ok | strong on (b) too |
| 3 | cdr_250 | levels_vwap_bands.reject_native {"tol": 0.0, "conf": "close"} | plain60/60 | +352 | +384 | +0.23 | 446 | ok/ok/ok | strong on (b) too |
| 4 | dchg_20 | barnative_profile.va_fade {"va": 0.5, "buf": 0.0} | plain60/60 | +304 | +505 | +0.20 | 189 | ok/ok/ok | bare only (not positive on own-stop) |
| 5 | dib_2000 | bands_atrchan.break_ext {"n": 20, "atr": 14, "k": 3.0} | plain60/60 | +299 | +838 | +0.19 | 597 | ok/ok/ok | bare only (not positive on own-stop) |
| 6 | cusum_80 | levels_zones.reject_native {"tol": 1.0, "conf": "body"} | sym15u | +598 | +1328 | +0.19 | 173 | ok/ok/ok | strong on (b) too |
| 7 | cusum_28 | bands_regchan.break_linreg {"n": 40, "k": 2.5} | plain60/60 | +270 | -301 | +0.17 | 129 | ok/ok/ok | bare only (not positive on own-stop) |
| 8 | cusum_56 | levels_zones.reject_native {"tol": 0.5, "conf": "body"} | plain60/60 | +313 | +147 | +0.20 | 280 | ok/AMBER/ok | strong on (b) too |
| 9 | cusum_20 | book_wall.near_fade {"m": 4, "d": 4} | plain60/60 | +273 | +1571 | +0.17 | 609 | ok/ok/ok | strong on (b) too |
| 10 | cdr_250 | xmarket_commod.against_CL {"w": 15, "thr": 2.0} | plain60/60 | +315 | +507 | +0.20 | 122 | AMBER/ok/ok | strong on (b) too |

### (b) OWN-STOP (2 stops; 1.5 and 3 shown as neighbours)  (cells passing: 4000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | dlt_150 | levels_opens.retest_native {"M": 3, "tol": 0.0} | plain60/60 | +295 | +714 | +0.19 | 169 | ok/ok/ok | L6M @1.5 stops +297 / @3 stops +419 |
| 2 | dlt_150 | levels_opens.retest {"M": 3, "tol": 0.0} | plain60/60 | +295 | +714 | +0.19 | 169 | ok/ok/ok | L6M @1.5 stops +297 / @3 stops +419 |
| 3 | cusum_20 | bands_regchan.break_linreg_native {"clk": 20, "k": 2.0} | plain60/60 | +328 | -142 | +0.21 | 179 | AMBER/ok/ok | L6M @1.5 stops +228 / @3 stops +38 |
| 4 | cdr_250 | xmarket_commod.against_CL {"w": 15, "thr": 2.0} | plain60/60 | +286 | +544 | +0.18 | 118 | AMBER/ok/ok | L6M @1.5 stops +286 / @3 stops +315 |
| 5 | cusum_14 | bands_bollinger.break_native {"clk": 40, "k": 2.5} | plain60/60 | +222 | +124 | +0.14 | 244 | ok/ok/ok | L6M @1.5 stops +267 / @3 stops +68 |
| 6 | cdr_250 | levels_vwap_bands.reject {"tol": 0.0, "conf": "close"} | plain60/60 | +218 | -111 | +0.14 | 294 | ok/ok/ok | L6M @1.5 stops +146 / @3 stops +521 |
| 7 | cdr_250 | levels_vwap_bands.reject_native {"tol": 0.0, "conf": "close"} | plain60/60 | +218 | -111 | +0.14 | 294 | ok/ok/ok | L6M @1.5 stops +146 / @3 stops +521 |
| 8 | cdr_160 | levels_fib5.reject_native {"tol": 1.0, "conf": "body"} | sym15u | +550 | -482 | +0.18 | 197 | AMBER/AMBER/ok | L6M @1.5 stops +223 / @3 stops +443 |
| 9 | cdr_160 | levels_fib5.reject_native {"tol": 1.0, "conf": "body"} | sym15u | +440 | -357 | +0.14 | 101 | ok/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops +633 |
| 10 | cusum_112 | tape_stack.r5_fade {"k": 4} | plain60/60 | +256 | -67 | +0.16 | 152 | ok/ok/AMBER | L6M @1.5 stops +136 / @3 stops +201 |

### (c) CURRENT-STACK MASK (valid for ADDING a book to today's stack only; not valid for a rebuilt stack)  (cells passing: 4000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | dlt_150 | bands_regchan.fade_linreg_native {"clk": 10, "k": 2.0} | plain60/60 | +373 | -316 | +0.24 | 130 | ok/ok/ok | depends on today's stack |
| 2 | cusum_80 | levels_zones.reject_native {"tol": 1.0, "conf": "body"} | sym15u | +679 | +1249 | +0.22 | 137 | ok/ok/ok | also positive on (b) |
| 3 | cdr_100 | structure_libpattern.pin {"k": 3.0, "filt": 50} | plain60/60 | +242 | +348 | +0.16 | 204 | ok/ok/ok | depends on today's stack |
| 4 | dib_700 | bands_bollinger.break_native {"clk": 20, "k": 2.0} | asym20u/10u | +497 | -6 | +0.16 | 284 | ok/ok/ok | depends on today's stack |
| 5 | dlt_45 | bands_bollinger.walk_native {"clk": 5, "k": 1.5, "N": 2} | plain60/60 | +234 | -26 | +0.15 | 229 | ok/ok/ok | depends on today's stack |
| 6 | dchg_20 | bands_regchan.break_linreg {"n": 20, "k": 2.0} | plain60/60 | +208 | -118 | +0.13 | 181 | ok/ok/ok | also positive on (b) |
| 7 | cdr_100 | structure_swing.choch {"k": 5, "buf": 0.0} | plain60/60 | +205 | +54 | +0.13 | 194 | ok/ok/ok | depends on today's stack |
| 8 | cusum_20 | book_sweep.cnt_follow {"thr": 2} | plain60/60 | +198 | -52 | +0.13 | 321 | ok/ok/ok | depends on today's stack |
| 9 | dib_240 | bands_vwap.walk {"minbars": 20, "k": 1.5, "N": 2} | plain60/60 | +190 | +496 | +0.12 | 204 | ok/ok/ok | depends on today's stack |
| 10 | dib_700 | bands_bollinger.walk {"n": 30, "k": 1.5, "N": 3} | plain60/60 | +183 | -104 | +0.12 | 265 | ok/ok/ok | depends on today's stack |

## NYAM

### (a) BARE  (scored on exactly the same result files as (b) and (c); cells passing: 4000, capped at 4,000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | cusum_20 | book_ofi.follow_native {"L": 3600, "z": 2.0} | plain60/60 | +1408 | +528 | +0.90 | 1026 | AMBER/ok/ok | bare only (not positive on own-stop) |
| 2 | dib_15000 | structure_fvg.cont {"w": 0.75} | plain60/60 | +1081 | +455 | +0.69 | 495 | ok/ok/ok | bare only (not positive on own-stop) |
| 3 | dlt_100 | bands_bollinger.walk_native {"clk": 10, "k": 2.0, "N": 2} | plain60/60 | +1255 | +1563 | +0.80 | 502 | AMBER/ok/AMBER | strong on (b) too |
| 4 | dib_10000 | levels_session_hl.break_native {"n": 3, "k": 0.5} | plain60/60 | +721 | +842 | +0.46 | 866 | ok/ok/ok | bare only (not positive on own-stop) |
| 5 | dib_10000 | levels_session_hl.break_native {"n": 3, "k": 0.5} | plain60/60 | +737 | +574 | +0.47 | 434 | ok/ok/ok | bare only (not positive on own-stop) |
| 6 | dchg_28 | bands_bollinger.break_native {"clk": 20, "k": 1.5} | sym15u | +1596 | -4 | +0.51 | 497 | ok/ok/ok | strong on (b) too |
| 7 | dchg_40 | manual_cci.go {"len": 14, "lvl": 100} | sym15u | +1356 | +1098 | +0.43 | 411 | ok/ok/ok | strong on (b) too |
| 8 | cusum_20 | book_ofi.follow {"L": 200, "z": 2.0} | plain60/60 | +642 | -121 | +0.41 | 1022 | ok/ok/ok | strong on (b) too |
| 9 | dib_6000 | levels_profile_nodes.break {"n": 2, "k": 0.25} | plain60/60 | +639 | +19 | +0.41 | 631 | ok/ok/ok | bare only (not positive on own-stop) |
| 10 | dlt_100 | bands_avwap0930.walk_0930_native {"clk": 6, "k": 1.0, "N": 2} | plain60/60 | +621 | +353 | +0.40 | 322 | ok/ok/ok | strong on (b) too |

### (b) OWN-STOP (2 stops; 1.5 and 3 shown as neighbours)  (cells passing: 4000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | cusum_20 | book_ofi.follow {"L": 200, "z": 2.0} | plain60/60 | +2026 | +333 | +1.30 | 496 | AMBER/AMBER/ok | L6M @1.5 stops +2439 / @3 stops +579 |
| 2 | cusum_20 | book_ofi.follow {"L": 200, "z": 2.0} | plain60/60 | +1028 | +506 | +0.66 | 250 | ok/ok/AMBER | L6M @1.5 stops +1199 / @3 stops +201 |
| 3 | cdr_400 | levels_opens.break_native {"n": 3, "k": 0.5} | plain60/60 | +765 | -19 | +0.49 | 338 | ok/ok/ok | L6M @1.5 stops +342 / @3 stops +119 |
| 4 | dchg_40 | manual_cci.go {"len": 14, "lvl": 100} | sym15u | +1811 | +863 | +0.58 | 297 | ok/AMBER/ok | L6M @1.5 stops +1902 / @3 stops +1089 |
| 5 | dib_1200 | bands_bollinger.break_native {"clk": 5, "k": 2.0} | asym15u/30u | +1364 | -371 | +0.53 | 413 | AMBER/ok/AMBER | L6M @1.5 stops <=0 or <100 tr / @3 stops +385 |
| 6 | cdr_600 | levels_vwap.false_break_native {"M": 2, "k": 0.5} | sym15u | +1373 | +488 | +0.44 | 230 | AMBER/ok/ok | L6M @1.5 stops +1360 / @3 stops +531 |
| 7 | cusum_20 | book_ofi.follow {"L": 200, "z": 2.0} | sym15u | +1276 | +1006 | +0.41 | 281 | ok/ok/ok | L6M @1.5 stops +879 / @3 stops +1848 |
| 8 | dib_25000 | structure_level.sopen_reject {"buf": 0.0} | plain60/60 | +576 | +53 | +0.37 | 179 | ok/ok/ok | L6M @1.5 stops +640 / @3 stops +674 |
| 9 | cusum_112 | levels_fib5.break {"n": 3, "k": 0.5} | plain60/60 | +688 | +245 | +0.44 | 321 | AMBER/AMBER/ok | L6M @1.5 stops +509 / @3 stops +112 |
| 10 | cusum_20 | bands_atrchan.break_ema {"n": 20, "atr": 14, "k": 2.0} | sym15u | +1147 | +94 | +0.37 | 140 | ok/AMBER/ok | L6M @1.5 stops +1456 / @3 stops +1274 |

### (c) CURRENT-STACK MASK (valid for ADDING a book to today's stack only; not valid for a rebuilt stack)  (cells passing: 4000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | cusum_20 | book_ofi.follow {"L": 200, "z": 2.0} | plain60/60 | +1493 | +667 | +0.96 | 633 | ok/ok/ok | also positive on (b) |
| 2 | dchg_40 | manual_macd.sigcross_native {"f": 5, "s": 13, "g": 4} | plain60/60 | +1357 | -639 | +0.87 | 604 | ok/ok/ok | depends on today's stack |
| 3 | dchg_28 | levels_vwap.break {"n": 3, "k": 0.5} | plain60/60 | +892 | -280 | +0.57 | 538 | ok/ok/ok | depends on today's stack |
| 4 | dlt_100 | bands_bollinger.walk {"n": 20, "k": 2.0, "N": 2} | plain60/60 | +789 | +831 | +0.51 | 336 | ok/ok/ok | also positive on (b) |
| 5 | dlt_150 | momentum_roc.break_native {"len": 20, "wd": 1.0} | plain60/60 | +755 | +597 | +0.48 | 422 | ok/ok/ok | depends on today's stack |
| 6 | dib_240 | bands_avwap0930.walk_0930 {"minbars": 20, "k": 1.5, "N": 2} | plain60/60 | +738 | -713 | +0.47 | 548 | ok/ok/ok | depends on today's stack |
| 7 | dol_350 | bands_atrchan.break_ema {"n": 40, "atr": 14, "k": 1.5} | plain60/60 | +681 | -347 | +0.44 | 841 | ok/ok/ok | depends on today's stack |
| 8 | dib_10000 | levels_profile_nodes.false_break {"M": 1, "k": 0.0} | plain60/60 | +666 | -51 | +0.43 | 373 | ok/ok/ok | depends on today's stack |
| 9 | dib_10000 | levels_profile_nodes.false_break_native {"M": 1, "k": 0.0} | plain60/60 | +666 | -51 | +0.43 | 373 | ok/ok/ok | depends on today's stack |
| 10 | cdr_100 | levels_vwap.break_native {"n": 1, "k": 0.5} | asym10u/20u | +1368 | +85 | +0.44 | 219 | ok/ok/ok | depends on today's stack |

## NYPM

### (a) BARE  (scored on exactly the same result files as (b) and (c); cells passing: 4000, capped at 4,000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | dib_3500 | barnative_speed.burst_fade {"len": 10, "r": 0.4} | plain60/60 | +811 | +1354 | +0.52 | 967 | ok/ok/AMBER | strong on (b) too |
| 2 | dchg_40 | structure_swing.bos {"k": 2, "buf": 0.0} | plain60/60 | +471 | +421 | +0.30 | 274 | ok/ok/ok | strong on (b) too |
| 3 | cusum_20 | bands_atrchan.break_ext {"n": 10, "atr": 14, "k": 2.0} | plain60/60 | +376 | +1246 | +0.24 | 487 | ok/ok/ok | strong on (b) too |
| 4 | cdr_100 | bands_regchan.break_linreg {"n": 20, "k": 2.0} | plain60/60 | +435 | +110 | +0.28 | 395 | ok/ok/ok | bare only (not positive on own-stop) |
| 5 | dib_25000 | momentum_stoch.zone_break_native {"len": 14, "lvl": 70} | plain60/60 | +372 | -106 | +0.24 | 271 | ok/ok/ok | bare only (not positive on own-stop) |
| 6 | dib_40000 | tape_libvol.force {"len": 7} | plain60/60 | +371 | -425 | +0.24 | 205 | ok/ok/ok | bare only (not positive on own-stop) |
| 7 | dib_70000 | trend_ma_t3.price_native {"len": 5, "width": 0.25} | plain60/60 | +360 | -369 | +0.23 | 215 | ok/ok/ok | strong on (b) too |
| 8 | dib_15000 | xmarket_fx.with_6J {"w": 1, "thr": 1.0} | sym15u | +712 | +977 | +0.23 | 277 | ok/ok/ok | bare only (not positive on own-stop) |
| 9 | cusum_56 | manual_squeeze.momturn {"len": 20} | plain60/60 | +356 | +309 | +0.23 | 131 | ok/ok/ok | bare only (not positive on own-stop) |
| 10 | cdr_600 | structure_libpattern.nr {"n": 10} | plain60/60 | +335 | -232 | +0.21 | 179 | ok/ok/ok | strong on (b) too |

### (b) OWN-STOP (2 stops; 1.5 and 3 shown as neighbours)  (cells passing: 4000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | cdr_250 | xmarket_fx.with_6J {"w": 1, "thr": 1.0} | sym15u | +1837 | +1382 | +0.59 | 170 | ok/ok/AMBER | L6M @1.5 stops +2040 / @3 stops +1926 |
| 2 | cdr_100 | bands_atrchan.break_ext {"n": 10, "atr": 14, "k": 2.0} | plain60/60 | +506 | -942 | +0.32 | 271 | ok/ok/ok | L6M @1.5 stops +460 / @3 stops +420 |
| 3 | dib_3500 | barnative_speed.burst_fade {"len": 20, "r": 0.6} | plain60/60 | +503 | +127 | +0.32 | 154 | ok/ok/ok | L6M @1.5 stops +494 / @3 stops +502 |
| 4 | cusum_40 | bands_envelope.fade_sma {"n": 40, "pct": 0.2} | plain60/60 | +442 | -17 | +0.28 | 240 | ok/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops +376 |
| 5 | cusum_20 | book_pslope.follow_sm {"L": 200, "z": 2.0, "sm": 3} | sym15u | +1040 | +1262 | +0.33 | 190 | AMBER/ok/ok | L6M @1.5 stops +1216 / @3 stops +841 |
| 6 | dchg_56 | trend_macd.zero_native {"len": 6, "width": 0.0} | plain60/60 | +438 | +3 | +0.28 | 105 | ok/AMBER/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |
| 7 | dchg_14 | bands_regchan.break_linreg {"n": 20, "k": 2.0} | sym15u | +698 | +402 | +0.22 | 159 | ok/ok/ok | L6M @1.5 stops +993 / @3 stops +533 |
| 8 | dib_70000 | trend_ma_t3.price_native {"len": 5, "width": 0.25} | plain60/60 | +408 | +14 | +0.26 | 215 | ok/ok/ok | L6M @1.5 stops +267 / @3 stops <=0 or <100 tr |
| 9 | cdr_600 | xmarket_fx.with_6J {"w": 1, "thr": 1.0} | plain60/60 | +400 | +628 | +0.26 | 139 | AMBER/ok/AMBER | L6M @1.5 stops +318 / @3 stops +113 |
| 10 | cusum_20 | bands_regchan.break_stderr {"n": 10, "k": 1.5} | plain60/60 | +296 | +127 | +0.19 | 265 | ok/ok/ok | L6M @1.5 stops +313 / @3 stops <=0 or <100 tr |

### (c) CURRENT-STACK MASK (valid for ADDING a book to today's stack only; not valid for a rebuilt stack)  (cells passing: 4000)
| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | cdr_100 | bands_regchan.break_linreg {"n": 10, "k": 1.5} | plain60/60 | +743 | -49 | +0.48 | 565 | ok/ok/ok | also positive on (b) |
| 2 | cusum_56 | tape_vpin.fade {"N": 10, "thr": 0.05} | plain60/60 | +709 | -11 | +0.45 | 218 | ok/AMBER/ok | also positive on (b) |
| 3 | dlt_100 | bands_regchan.break_stderr_native {"clk": 10, "k": 2.0} | plain60/60 | +568 | +415 | +0.36 | 464 | ok/ok/ok | depends on today's stack |
| 4 | dlt_70 | bands_regchan.break_linreg {"n": 10, "k": 1.5} | plain60/60 | +503 | -725 | +0.32 | 577 | ok/ok/ok | depends on today's stack |
| 5 | cdr_100 | bands_regchan.break_linreg {"n": 20, "k": 2.0} | plain60/60 | +585 | +99 | +0.37 | 233 | ok/AMBER/AMBER | depends on today's stack |
| 6 | dlt_70 | bands_regchan.break_linreg {"n": 10, "k": 1.5} | plain60/60 | +556 | -576 | +0.36 | 294 | ok/AMBER/AMBER | depends on today's stack |
| 7 | cdr_100 | structure_libpattern.rangeexp {"k": 1.5} | plain60/60 | +425 | +744 | +0.27 | 525 | ok/ok/ok | depends on today's stack |
| 8 | dib_3500 | levels_profile_va.break {"n": 2, "k": 0.25} | plain60/60 | +447 | -327 | +0.29 | 137 | ok/ok/ok | depends on today's stack |
| 9 | cusum_56 | momentum_libosc.aroon {"len": 25} | plain60/60 | +504 | +76 | +0.32 | 121 | AMBER/ok/ok | depends on today's stack |
| 10 | dlt_70 | bands_regchan.break_linreg {"n": 20, "k": 2.0} | plain60/60 | +389 | -92 | +0.25 | 477 | ok/ok/ok | depends on today's stack |

