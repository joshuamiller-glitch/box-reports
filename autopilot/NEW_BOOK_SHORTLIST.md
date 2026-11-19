# NEW_BOOK_SHORTLIST - RULE-BASED (no top-N; W-SHORT, order 1845Z; replaces the 12-per-session list, kept as NEW_BOOK_SHORTLIST_12PER_SESSION_OLD.md)

refreshed 2026-11-19 00:20Z | screen level, bare ranking from server-2 results only (grid partitioned across servers until W-S3 merges; counts PROVISIONAL) | pick window = last 26 weeks (L6M) with last 13 (L3M) beside, equal risk (R = points / stop; risk-matched $/week = R/wk x $1,200)

RULE (a cell is shortlisted when it passes ALL): L6M > 0; >= 100 trades in L6M; L3M > 0; persistence > 0.60 (share of 2-week windows since 2023-10 positive); prior years 2023/24/25 R per week not more than 30% below the cell's own L6M R per week (RED = shown on disk, not delivered; AMBER 15-30% passes, flagged); then trust + look-ahead (phase 2, every passing cell, best first). Counts per session and the failing-reason split: autopilot/SURVIVOR_COUNTS.md. Every evaluated cell with its reason is on disk (server 2 /mnt/l2/l2vast/_grid/rule/bare_<session>.parquet) for the 2-week refit. OWN-STOP and current-stack MASK rankings beside bare: pending (full-grid arrays not built yet).

FAMILIES: cells are grouped into one family when they are the same module.variant on an adjacent bar size of the same bar type, an adjacent parameter of the same variant, or the identical parameter with another bracket / side (connected components of the grid neighbour graph). The engine runs the BEST member of a family first (highest min(L6M R/wk, weakest prior-year R/wk)); the other members are listed after it with their screen numbers; nothing is dropped. Full list (all passing cells with family id and rank in family): pass_bare_<session>.csv in the same folder. The tables below show the best member of the top 40 families per session only (for reading); the shortlist is every passing cell.

| session | cells evaluated | PASS (cells) | families | non-reversal | reversal (provisional: look-ahead gate) | level / S-D |
|---|---|---|---|---|---|---|
| Asia | 4,386,735 | **2,992** | 1,890 | 2099 | 835 | 1061 |
| London | 4,397,570 | **1,035** | 808 | 746 | 233 | 349 |
| NYAM | 4,828,997 | **9,504** | 4,556 | 6560 | 2430 | 5157 |
| NYPM | 4,842,376 | **531** | 396 | 401 | 86 | 112 |

## Today's engine leads (labels per PHASE2_TOOLING_TEST.md, 1932Z)

- **XA3** (NY AM tick_5000 | levels_vwap.retest_native {M 6, tol 0.5} | plain 60/60 | both): FRONT of the queue. Beats 25/30 same-bracket random draws, 30/30 date-shift engine controls (+$54,428 vs best control +$24,259); own-stop (screen) 1.5 stops L6M +1,313 pts, 3 stops +1,579 pts, prior years positive; trust pass.
- **WP10** (NY PM vol_350 | tape_libvol.cmf {len 10} | asym20u/10u | both): **lead for add-to-today's-stack at most; NOT a rebuilt-stack candidate**. Not distinguishable from random entries with its own wide bracket (beats 15/30), best date-shift control within $135 of it, own-stop weak (W-DAYMASK). No engine time ahead of R3 passers.

## Asia - best member of the top 40 families (of 1,890)
| fam # | members | bar row | trigger.variant params | bracket / side | stop pts | R/wk L6M | weakest prior-yr R/wk | R/trade | L6M pts / $1 lot | L3M pts | trades L6M | persist | flags (amber yrs) | class | best neighbours (row, variant, params -> L6M pts) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2 | dib_240 | momentum_mvote.v3of5_native {"scale": 1.0, "thr": 0.25} | plain60/60 / both | 60 | +0.395 | +0.378 | +0.0132 | +616 / +12323 | +1066 | 777 | 0.63 | 0 | NR | dib_240 v3of5_native {"scale": 1.0, "thr": 0.25} -> +57 |
| 2 | 1 | mrenko_20 | momentum_er.trend_z {"len": 10, "thr": 0.4} | plain60/60 / both | 60 | +0.374 | +0.399 | +0.0188 | +584 / +11682 | +136 | 518 | 0.65 | 0 | REV | - |
| 3 | 1 | mrenko_20 | momentum_er.trend {"len": 10, "thr": 0.4} | plain60/60 / both | 60 | +0.390 | +0.369 | +0.0195 | +608 / +12161 | +101 | 521 | 0.65 | 0 | REV | - |
| 4 | 1 | cusum_10 | momentum_cci.brk {"len": 30, "lvl": 200} | plain60/60 / both | 60 | +0.405 | +0.342 | +0.0131 | +632 / +12633 | +93 | 806 | 0.62 | 1 | NR | - |
| 5 | 1 | time_m_7 | xmarket_rty.confirm {"w": 30} | plain60/60 / both | 60 | +0.385 | +0.342 | +0.0225 | +601 / +12010 | +126 | 444 | 0.60 | 0 | NR | - |
| 6 | 1 | tick_300 | momentum_mvote.v3of5 {"scale": 1.0, "thr": 0.25} | plain60/60 / both | 60 | +0.322 | +0.334 | +0.0173 | +502 / +10040 | +600 | 483 | 0.64 | 0 | NR | - |
| 7 | 2 | vsess_30 | bands_atrchan.break_ema_native {"clk": 5, "k": 1.5} | plain60/60 / both | 60 | +0.354 | +0.304 | +0.0505 | +551 / +11029 | +122 | 182 | 0.60 | 0 | NR | vsess_30 break_ema_native {"clk": 10, "k": 1.5} -> +551 |
| 8 | 1 | vsess_30 | bands_envelope.break_ema_native {"clk": 10, "k": 1.5} | plain60/60 / both | 60 | +0.354 | +0.304 | +0.0505 | +551 / +11029 | +122 | 182 | 0.60 | 0 | NR | - |
| 9 | 2 | vol_750 | trend_libstack.ema_stack {"set": "5-13-34"} | plain60/60 / both | 60 | +0.325 | +0.299 | +0.0207 | +506 / +10128 | +356 | 407 | 0.62 | 0 | NR | vol_750 ema_stack {"set": "5-13-34"} -> +35 |
| 10 | 2 | renko_10 | trend_libstack.ema_stack {"set": "13-34-89"} | plain60/60 / both | 60 | +0.291 | +0.297 | +0.0150 | +455 / +9090 | +913 | 505 | 0.62 | 0 | REV | renko_10 ema_stack {"set": "13-34-89"} -> +182 |
| 11 | 2 | wrenko_10 | trend_libstack.ema_stack {"set": "13-34-89"} | plain60/60 / both | 60 | +0.291 | +0.297 | +0.0150 | +455 / +9090 | +913 | 505 | 0.62 | 0 | REV | wrenko_10 ema_stack {"set": "13-34-89"} -> +182 |
| 12 | 16 | time_m_10 | bands_vwap.break_native {"clk": 3, "k": 1.0} | plain60/60 / both | 60 | +0.308 | +0.286 | +0.0203 | +481 / +9611 | +1341 | 394 | 0.62 | 0 | NR | time_m_10 break_native {"clk": 6, "k": 1.0} -> +481; time_m_10 break_native {"clk": 12, "k": 1.0} -> +481; time_m_10 break_native {"clk": 25, "k": 1.0} -> +481 |
| 13 | 1 | vol_500 | momentum_mvote.v3of5_native {"scale": 0.25, "thr": 0.25} | plain60/60 / both | 60 | +0.290 | +0.286 | +0.0131 | +452 / +9047 | +1146 | 575 | 0.60 | 0 | NR | - |
| 14 | 1 | frenko_40 | book_ofi.follow_sm {"L": 50, "z": 1.0, "sm": 3} | plain60/60 / both | 60 | +0.286 | +0.322 | +0.0105 | +446 / +8916 | +73 | 708 | 0.63 | 0 | REV | - |
| 15 | 1 | drb_400 | structure_orb.orb {"or_min": 5, "buf": 0.0} | plain60/60 / both | 60 | +0.348 | +0.268 | +0.0517 | +543 / +10852 | +513 | 175 | 0.63 | 1 | NR | - |
| 16 | 1 | mom_56 | trend_psar.flip {"af0": 0.02, "step": 0.03, "max": 0.2} | plain60/60 / both | 60 | +0.265 | +0.279 | +0.0223 | +414 / +8271 | +661 | 309 | 0.67 | 0 | OTHER | - |
| 17 | 1 | tm2700 | bands_donchian.break_native {"clk": 20, "buf": 0.0} | plain60/60 / both | 60 | +0.340 | +0.258 | +0.0373 | +530 / +10600 | +454 | 237 | 0.70 | 1 | NR | - |
| 18 | 1 | tm2700 | bands_donchian.break_native {"clk": 5, "buf": 0.0} | plain60/60 / both | 60 | +0.340 | +0.258 | +0.0373 | +530 / +10600 | +454 | 237 | 0.70 | 1 | NR | - |
| 19 | 33 | time_m_10 | bands_vwap.walk_native {"clk": 6, "k": 1.0, "N": 3} | plain60/60 / both | 60 | +0.302 | +0.255 | +0.0291 | +471 / +9419 | +569 | 270 | 0.69 | 1 | NR | time_m_10 walk_native {"clk": 12, "k": 1.0, "N": 3} -> +471; time_m_10 walk_native {"clk": 25, "k": 1.0, "N": 3} -> +471; time_m_10 walk_native {"clk": 6, "k": 1.0, "N": 2} -> +251 |
| 20 | 1 | tm1200 | momentum_er.trend_native {"len": 10, "thr": 0.5} | plain60/60 / both | 60 | +0.257 | +0.254 | +0.0361 | +401 / +8014 | +19 | 185 | 0.70 | 0 | NR | - |
| 21 | 1 | tm1200 | momentum_er.trend {"len": 10, "thr": 0.5} | plain60/60 / both | 60 | +0.257 | +0.254 | +0.0361 | +401 / +8014 | +19 | 185 | 0.70 | 0 | NR | - |
| 22 | 1 | time_m_60 | pullback_ema.depth_native {"len": 20, "w": 0.5} | plain60/60 / both | 60 | +0.335 | +0.253 | +0.0277 | +522 / +10449 | +29 | 314 | 0.68 | 1 | NR | - |
| 23 | 1 | dlt_45 | momentum_willr.break_native {"len": 21, "lvl": 30} | plain60/60 / both | 60 | +0.326 | +0.252 | +0.0147 | +508 / +10170 | +537 | 576 | 0.60 | 1 | NR | - |
| 24 | 4 | time_m_2 | bands_vwap.walk {"minbars": 20, "k": 1.0, "N": 2} | plain60/60 / both | 60 | +0.243 | +0.270 | +0.0145 | +379 / +7573 | +712 | 435 | 0.62 | 0 | NR | time_m_2 walk {"minbars": 20, "k": 1.0, "N": 3} -> +120; time_m_2 walk {"minbars": 20, "k": 1.0, "N": 2} -> +94; time_m_2 walk {"minbars": 20, "k": 1.0, "N": 3} -> +117 |
| 25 | 4 | swing_atr_0.15 | levels_vwap.break {"n": 2, "k": 0.0} | plain60/60 / both | 60 | +0.253 | +0.242 | +0.0110 | +395 / +7899 | +807 | 599 | 0.64 | 0 | REV, level | swing_atr_0.15 break {"n": 3, "k": 0.0} -> +95; swing_atr_0.15 break {"n": 3, "k": 0.0} -> +95; swing_atr_0.15 break {"n": 2, "k": 0.0} -> +61 |
| 26 | 4 | swing_atr_0.15 | levels_vwap.break_native {"n": 2, "k": 0.0} | plain60/60 / both | 60 | +0.253 | +0.242 | +0.0110 | +395 / +7899 | +807 | 599 | 0.64 | 0 | REV, level | swing_atr_0.15 break_native {"n": 3, "k": 0.0} -> +95; swing_atr_0.15 break_native {"n": 3, "k": 0.0} -> +95; swing_atr_0.15 break_native {"n": 2, "k": 0.0} -> +61 |
| 27 | 2 | time_m_30 | levels_fib5.break {"n": 3, "k": 0.5} | plain60/60 / both | 60 | +0.240 | +0.424 | +0.0127 | +374 / +7474 | +769 | 491 | 0.68 | 0 | NR, level | time_m_30 break {"n": 3, "k": 0.5} -> +442 |
| 28 | 2 | tm60 | levels_fib15.break_native {"n": 2, "k": 0.25} | plain60/60 / long | 60 | +0.260 | +0.235 | +0.0197 | +406 / +8119 | +903 | 343 | 0.60 | 0 | NR, level | tm60 break_native {"n": 2, "k": 0.25} -> +644 |
| 29 | 1 | time_m_7 | bands_vwap.break {"minbars": 5, "k": 1.0} | plain60/60 / both | 60 | +0.238 | +0.231 | +0.0150 | +371 / +7416 | +612 | 411 | 0.60 | 0 | NR | - |
| 30 | 1 | time_m_60 | pullback_ema.depth_native {"len": 5, "w": 0.5} | plain60/60 / both | 60 | +0.268 | +0.230 | +0.0230 | +419 / +8375 | +93 | 303 | 0.69 | 0 | NR | - |
| 31 | 1 | tm30 | bands_vwap.break {"minbars": 30, "k": 1.0} | plain60/60 / both | 60 | +0.226 | +0.271 | +0.0110 | +352 / +7046 | +2 | 535 | 0.65 | 0 | NR | - |
| 32 | 1 | mrenko_14 | levels_vwap.break {"n": 3, "k": 0.5} | plain60/60 / both | 60 | +0.274 | +0.217 | +0.0126 | +427 / +8544 | +345 | 566 | 0.67 | 1 | REV, level | - |
| 33 | 1 | vol_1100 | levels_vwap.break_native {"n": 2, "k": 0.0} | plain60/60 / both | 60 | +0.224 | +0.215 | +0.0118 | +349 / +6982 | +1450 | 495 | 0.62 | 0 | NR, level | - |
| 34 | 2 | vol_1100 | levels_vwap.break {"n": 2, "k": 0.0} | plain60/60 / both | 60 | +0.224 | +0.215 | +0.0118 | +349 / +6982 | +1450 | 495 | 0.62 | 0 | NR, level | vol_1100 break {"n": 2, "k": 0.25} -> +171 |
| 35 | 2 | vol_500 | bands_atrchan.break_ema {"n": 20, "atr": 14, "k": 2.0} | plain60/60 / both | 60 | +0.217 | +0.205 | +0.0105 | +338 / +6760 | +45 | 539 | 0.60 | 0 | NR | vol_500 break_ema {"n": 20, "atr": 14, "k": 2.0} -> +120 |
| 36 | 1 | tm60 | levels_fib15.break {"n": 2, "k": 0.25} | plain60/60 / long | 60 | +0.258 | +0.204 | +0.0194 | +403 / +8060 | +752 | 346 | 0.64 | 2 | NR, level | - |
| 37 | 3 | tm10 | bands_vwap.walk_native {"clk": 25, "k": 1.0, "N": 3} | plain60/60 / long | 60 | +0.213 | +0.204 | +0.0207 | +333 / +6651 | +46 | 268 | 0.68 | 0 | NR | tm10 walk_native {"clk": 25, "k": 1.0, "N": 3} -> +66; tm10 walk_native {"clk": 25, "k": 1.5, "N": 3} -> +48 |
| 38 | 1 | urenko_56 | trend_ma_ema.price_native {"len": 10, "width": 0.25} | plain60/60 / both | 60 | +0.285 | +0.203 | +0.0249 | +445 / +8897 | +26 | 298 | 0.64 | 1 | REV | - |
| 39 | 1 | rng_10 | structure_libpattern.threebar {"filt": 50} | plain60/60 / both | 60 | +0.268 | +0.201 | +0.0063 | +418 / +8367 | +477 | 1105 | 0.63 | 1 | NR | - |
| 40 | 1 | pasl_40 | trend_ma_sma.price {"len": 50, "width": 0.0} | plain60/60 / both | 60 | +0.279 | +0.200 | +0.0327 | +435 / +8702 | +255 | 222 | 0.62 | 2 | REV | - |

## London - best member of the top 40 families (of 808)
| fam # | members | bar row | trigger.variant params | bracket / side | stop pts | R/wk L6M | weakest prior-yr R/wk | R/trade | L6M pts / $1 lot | L3M pts | trades L6M | persist | flags (amber yrs) | class | best neighbours (row, variant, params -> L6M pts) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 1 | tick_300 | book_micro.follow_sm {"L": 100, "z": 1.5, "sm": 3} | plain60/60 / both | 60 | +0.665 | +0.477 | +0.0286 | +1037 / +20740 | +1955 | 604 | 0.60 | 1 | NR | - |
| 2 | 1 | dltor_B320 | trend_macd.hist_turn {"len": 6, "width": 0.0} | sym15u / both | 60 | +0.475 | +0.381 | +0.0394 | +741 / +14814 | +867 | 313 | 0.72 | 1 | NR | - |
| 3 | 1 | tm420 | momentum_stoch.zone_break {"len": 5, "lvl": 70} | plain60/60 / both | 60 | +0.381 | +0.490 | +0.0176 | +594 / +11878 | +571 | 562 | 0.62 | 0 | NR | - |
| 4 | 1 | tm420 | momentum_stoch.zone_break_native {"len": 5, "lvl": 70} | plain60/60 / both | 60 | +0.381 | +0.490 | +0.0176 | +594 / +11878 | +571 | 562 | 0.62 | 0 | NR | - |
| 5 | 8 | tm20 | xmarket_rates.with_ZN {"w": 1, "thr": 1.0} | plain60/60 / long | 60 | +0.366 | +0.337 | +0.0256 | +571 / +11425 | +158 | 372 | 0.62 | 0 | NR | tm30 with_ZN {"w": 1, "thr": 1.0} -> +571; tm10 with_ZN {"w": 1, "thr": 1.0} -> +571; tm15 with_ZN {"w": 1, "thr": 1.0} -> +571 |
| 6 | 2 | tm60 | xmarket_rates.with_ZN {"w": 1, "thr": 1.0} | plain60/60 / long | 60 | +0.366 | +0.337 | +0.0256 | +571 / +11425 | +158 | 372 | 0.62 | 0 | NR | tm60 with_ZN {"w": 1, "thr": 1.0} -> +359 |
| 7 | 1 | bmsg_B320 | xmarket_rates.with_ZN {"w": 1, "thr": 1.0} | sym15u / both | 60 | +0.320 | +0.349 | +0.0300 | +500 / +9995 | +581 | 278 | 0.60 | 0 | OTHER | - |
| 8 | 2 | bmsg_B050 | bands_regchan.break_linreg {"n": 10, "k": 1.5} | plain60/60 / long | 60 | +0.328 | +0.302 | +0.0304 | +512 / +10237 | +525 | 281 | 0.64 | 0 | OTHER | bmsg_B050 break_linreg {"n": 10, "k": 1.5} -> +22 |
| 9 | 1 | tm1800 | levels_fib5.break {"n": 1, "k": 0.0} | plain60/60 / long | 60 | +0.408 | +0.290 | +0.0406 | +636 / +12718 | +262 | 261 | 0.68 | 3 | NR, level | - |
| 10 | 1 | tm1800 | levels_fib5.break_native {"n": 1, "k": 0.0} | plain60/60 / long | 60 | +0.408 | +0.290 | +0.0406 | +636 / +12718 | +262 | 261 | 0.68 | 3 | NR, level | - |
| 11 | 1 | tib_400 | barnative_delta.run {"n": 3, "thr": 0.0} | plain60/60 / long | 60 | +0.324 | +0.283 | +0.0200 | +506 / +10123 | +136 | 422 | 0.67 | 0 | NR | - |
| 12 | 1 | tm20 | momentum_squeeze.fire_native {"len": 20, "wd": 2.0} | asym15u/30u / long | 68 | +0.337 | +0.270 | +0.0434 | +592 / +11841 | +154 | 202 | 0.63 | 2 | NR | - |
| 13 | 1 | tm20 | momentum_squeeze.fire {"len": 20, "wd": 2.0} | asym15u/30u / long | 68 | +0.337 | +0.270 | +0.0434 | +592 / +11841 | +154 | 202 | 0.63 | 2 | NR | - |
| 14 | 1 | dltor_B320 | levels_swcluster.false_break {"M": 1, "k": 0.0} | plain60/60 / both | 60 | +0.291 | +0.266 | +0.0614 | +453 / +9069 | +360 | 123 | 0.63 | 0 | NR, level | - |
| 15 | 1 | dltor_B320 | levels_swcluster.false_break_native {"M": 1, "k": 0.0} | plain60/60 / both | 60 | +0.291 | +0.266 | +0.0614 | +453 / +9069 | +360 | 123 | 0.63 | 0 | NR, level | - |
| 16 | 1 | time_s_45 | xmarket_rates.with_ZN {"w": 1, "thr": 1.0} | plain60/60 / long | 60 | +0.266 | +0.267 | +0.0190 | +415 / +8299 | +196 | 364 | 0.64 | 0 | NR | - |
| 17 | 1 | bmsgq_B200 | pullback_ema.depth_native {"len": 5, "w": 0.5} | plain60/60 / long | 60 | +0.264 | +0.274 | +0.0164 | +412 / +8235 | +702 | 418 | 0.63 | 0 | OTHER | - |
| 18 | 2 | bmsgq_B200 | levels_round.false_break {"M": 3, "k": 0.5} | sym15u / long | 60 | +0.292 | +0.253 | +0.0532 | +456 / +9124 | +248 | 143 | 0.62 | 0 | OTHER, level | bmsgq_B200 false_break {"M": 2, "k": 0.5} -> +360 |
| 19 | 2 | tick_500 | xmarket_rates.with_ZB {"w": 5, "thr": 1.0} | plain60/60 / long | 60 | +0.351 | +0.249 | +0.0340 | +547 / +10941 | +98 | 268 | 0.65 | 2 | NR | tick_300 with_ZB {"w": 5, "thr": 1.0} -> +1 |
| 20 | 1 | cusum_14 | trend_macd.signal {"len": 26, "width": 0.15} | plain60/60 / long | 60 | +0.247 | +0.245 | +0.0211 | +386 / +7715 | +485 | 305 | 0.60 | 0 | NR | - |
| 21 | 1 | dib_700 | trend_heikin.flip_after_run {"len": 8, "width": 0.25} | plain60/60 / long | 60 | +0.327 | +0.234 | +0.0240 | +510 / +10199 | +407 | 354 | 0.62 | 2 | NR | - |
| 22 | 1 | urenko_10 | bands_regchan.break_linreg_native {"clk": 20, "k": 2.5} | plain60/60 / both | 60 | +0.233 | +0.255 | +0.0125 | +363 / +7269 | +458 | 485 | 0.62 | 0 | REV | - |
| 23 | 2 | vol_1700 | levels_vwap_bands.reject {"tol": 1.0, "conf": "body"} | plain60/60 / long | 60 | +0.257 | +0.227 | +0.0229 | +401 / +8010 | +355 | 292 | 0.60 | 0 | NR, level | vol_1700 reject {"tol": 0.5, "conf": "body"} -> +228 |
| 24 | 1 | bmsg_B320 | book_ofi.follow_sm {"L": 50, "z": 1.0, "sm": 3} | sym15u / both | 60 | +0.289 | +0.224 | +0.0294 | +451 / +9022 | +608 | 256 | 0.65 | 1 | OTHER | - |
| 25 | 1 | vrb_700 | book_imb.delta_fade {"lv": 5, "thr": 0.2} | plain60/60 / long | 60 | +0.222 | +0.299 | +0.0153 | +346 / +6922 | +122 | 378 | 0.67 | 0 | NR | - |
| 26 | 1 | tib_240 | tape_delta.cvd_fade {"N": 10, "L": 100, "z": 1.5} | sym15u / long | 68 | +0.288 | +0.222 | +0.0265 | +506 / +10111 | +225 | 283 | 0.67 | 1 | NR | - |
| 27 | 1 | entropy_B200 | book_pslope.follow_sm {"L": 100, "z": 1.5, "sm": 3} | sym15u / long | 60 | +0.249 | +0.221 | +0.0583 | +389 / +7771 | +564 | 111 | 0.60 | 0 | OTHER | - |
| 28 | 1 | kagi_10 | levels_fibr_dev.reject_native {"tol": 0.5, "conf": "body"} | plain60/60 / long | 60 | +0.220 | +0.224 | +0.0159 | +344 / +6878 | +85 | 360 | 0.64 | 0 | REV, level | - |
| 29 | 2 | mrenko_10 | levels_fib5.pullback {"tol": 1.0, "conf": "close"} | asym15u/30u / long | 86 | +0.249 | +0.218 | +0.0497 | +558 / +11150 | +80 | 130 | 0.67 | 0 | REV, level | mrenko_10 pullback {"tol": 1.0, "conf": "close"} -> +269 |
| 30 | 1 | dltor_B320 | levels_ob5.false_break {"M": 2, "k": 0.5} | plain60/60 / both | 60 | +0.262 | +0.218 | +0.0328 | +409 / +8185 | +1030 | 208 | 0.63 | 1 | NR, level | - |
| 31 | 1 | tm20 | xmarket_fx.with_6J {"w": 3, "thr": 1.0} | asym10u/20u / long | 45 | +0.215 | +0.254 | +0.0183 | +252 / +5032 | +222 | 305 | 0.60 | 0 | NR | - |
| 32 | 1 | dlt_100 | levels_vwap_bands.false_break_native {"M": 1, "k": 0.0} | plain60/60 / long | 60 | +0.253 | +0.215 | +0.0209 | +395 / +7901 | +156 | 315 | 0.60 | 1 | NR, level | - |
| 33 | 1 | dlt_100 | levels_vwap_bands.false_break {"M": 1, "k": 0.0} | plain60/60 / long | 60 | +0.253 | +0.215 | +0.0209 | +395 / +7901 | +156 | 315 | 0.60 | 1 | NR, level | - |
| 34 | 1 | renko_20 | xmarket_commod.against_CL {"w": 15, "thr": 2.0} | plain60/60 / both | 60 | +0.290 | +0.214 | +0.0368 | +453 / +9061 | +455 | 205 | 0.64 | 2 | REV | - |
| 35 | 1 | trend_20 | xmarket_commod.against_CL {"w": 15, "thr": 2.0} | plain60/60 / both | 60 | +0.290 | +0.214 | +0.0368 | +453 / +9061 | +455 | 205 | 0.64 | 2 | OTHER | - |
| 36 | 1 | dib_400 | trend_linreg.thresh {"len": 10, "width": 1.0} | plain60/60 / long | 60 | +0.264 | +0.214 | +0.0163 | +412 / +8231 | +560 | 422 | 0.63 | 1 | NR | - |
| 37 | 1 | renko_10 | levels_vwap_bands.break_native {"n": 2, "k": 0.25} | plain60/60 / long | 60 | +0.276 | +0.206 | +0.0198 | +430 / +8596 | +84 | 362 | 0.60 | 1 | REV, level | - |
| 38 | 1 | dol_500 | trend_linreg.thresh {"len": 10, "width": 1.0} | plain60/60 / long | 60 | +0.282 | +0.204 | +0.0241 | +440 / +8801 | +262 | 304 | 0.63 | 1 | NR | - |
| 39 | 1 | vrb_700 | levels_trendline.break_native {"n": 2, "k": 0.25} | plain60/60 / long | 60 | +0.253 | +0.203 | +0.0271 | +395 / +7891 | +325 | 243 | 0.62 | 1 | NR, level | - |
| 40 | 1 | tick_300 | book_micro.follow_native {"L": 1800, "z": 1.5} | plain60/60 / long | 60 | +0.257 | +0.203 | +0.0205 | +401 / +8023 | +80 | 326 | 0.65 | 1 | NR | - |

## NYAM - best member of the top 40 families (of 4,556)
| fam # | members | bar row | trigger.variant params | bracket / side | stop pts | R/wk L6M | weakest prior-yr R/wk | R/trade | L6M pts / $1 lot | L3M pts | trades L6M | persist | flags (amber yrs) | class | best neighbours (row, variant, params -> L6M pts) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 1 | frenko_40 | book_ofi.follow_sm {"L": 200, "z": 2.0, "sm": 3} | plain60/60 / both | 60 | +1.122 | +0.853 | +0.0501 | +1751 / +35011 | +147 | 582 | 0.63 | 2 | REV | - |
| 2 | 2 | bmsg_B200 | bands_bollinger.walk {"n": 30, "k": 2.0, "N": 3} | sym15u / both | 60 | +0.884 | +0.817 | +0.0759 | +1380 / +27593 | +1784 | 303 | 0.63 | 0 | OTHER | bmsg_B200 walk {"n": 30, "k": 2.0, "N": 3} -> +914 |
| 3 | 1 | swing_atr_0.15 | momentum_willr.break_native {"len": 14, "lvl": 10} | plain60/60 / both | 60 | +0.906 | +0.794 | +0.0129 | +1413 / +28259 | +21 | 1828 | 0.63 | 0 | REV | - |
| 4 | 1 | bmsg_B130 | bands_bollinger.break {"n": 30, "k": 2.5} | sym15u / both | 60 | +0.721 | +0.733 | +0.0705 | +1125 / +22492 | +814 | 266 | 0.65 | 0 | OTHER | - |
| 5 | 1 | trend_20 | levels_vwap.break_native {"n": 2, "k": 0.25} | sym15u / long | 60 | +0.851 | +0.713 | +0.1437 | +1328 / +26555 | +1326 | 154 | 0.63 | 1 | OTHER, level | - |
| 6 | 1 | trend_20 | momentum_mvote.v3of5 {"scale": 0.25, "thr": 0.25} | sym15u / both | 60 | +0.800 | +0.700 | +0.0535 | +1249 / +24974 | +515 | 389 | 0.62 | 0 | OTHER | - |
| 7 | 1 | bmsg_B030 | book_cancel.net_follow {"L": 200, "z": 2.0} | sym15u / both | 60 | +0.715 | +0.686 | +0.0726 | +1115 / +22310 | +780 | 256 | 0.62 | 0 | OTHER | - |
| 8 | 1 | bmsg_B200 | book_pslope.fade_native {"L": 900, "z": 1.0} | sym15u / both | 60 | +0.882 | +0.661 | +0.0533 | +1376 / +27512 | +1868 | 430 | 0.62 | 1 | OTHER | - |
| 9 | 1 | bmsgq_B080 | bands_keltner.break {"ema": 30, "atr": 10, "mult": 2.5} | sym15u / both | 60 | +0.657 | +0.664 | +0.0743 | +1025 / +20499 | +1034 | 230 | 0.63 | 0 | OTHER | - |
| 10 | 1 | dol_6000 | levels_vwap.reject_native {"tol": 1.0, "conf": "body"} | plain60/60 / both | 60 | +0.703 | +0.652 | +0.0198 | +1096 / +21925 | +393 | 923 | 0.62 | 0 | NR, level | - |
| 11 | 1 | tib_6000 | bands_bollinger.walk_native {"clk": 5, "k": 1.5, "N": 2} | plain60/60 / both | 60 | +0.651 | +0.716 | +0.0148 | +1016 / +20311 | +2054 | 1147 | 0.64 | 0 | NR | - |
| 12 | 1 | anch_L0200_B50 | levels_piv_floor.break {"n": 2, "k": 0.25} | sym15u / both | 60 | +0.648 | +0.776 | +0.0591 | +1011 / +20220 | +477 | 285 | 0.63 | 0 | OTHER, level | - |
| 13 | 1 | tm120 | book_ofi.follow {"L": 200, "z": 2.0} | plain60/60 / both | 60 | +0.646 | +0.627 | +0.0183 | +1008 / +20156 | +330 | 918 | 0.62 | 0 | NR | - |
| 14 | 1 | swing_atr_0.6 | book_ofi.follow_sm {"L": 200, "z": 2.0, "sm": 3} | plain60/60 / both | 60 | +0.641 | +0.621 | +0.0669 | +1000 / +20003 | +495 | 249 | 0.68 | 0 | REV | - |
| 15 | 1 | bmsg_B080 | structure_level.round_break {"grid": 50, "buf": 0.0} | sym15u / both | 60 | +0.611 | +0.655 | +0.0314 | +953 / +19069 | +248 | 506 | 0.67 | 0 | OTHER, level | - |
| 16 | 1 | anch_N0930_B50 | levels_vwap.retest_native {"M": 10, "tol": 0.5} | sym15u / both | 60 | +0.733 | +0.600 | +0.0693 | +1143 / +22866 | +633 | 275 | 0.67 | 1 | OTHER, level | - |
| 17 | 2 | dib_15000 | structure_fvg.cont {"w": 0.75} | plain60/60 / both | 60 | +0.693 | +0.598 | +0.0364 | +1081 / +21629 | +455 | 495 | 0.62 | 0 | NR | dib_15000 cont {"w": 0.75} -> +486 |
| 18 | 1 | dlt_100 | bands_bollinger.walk_native {"clk": 10, "k": 2.0, "N": 2} | plain60/60 / both | 60 | +0.805 | +0.582 | +0.0417 | +1255 / +25104 | +1563 | 502 | 0.63 | 2 | NR | - |
| 19 | 1 | trend_20 | structure_breakout.brk_native {"minutes": 5, "buf": 0.0} | sym15u / long | 60 | +0.651 | +0.582 | +0.0838 | +1016 / +20313 | +860 | 202 | 0.63 | 0 | OTHER | - |
| 20 | 1 | vol_1700 | book_ofi.follow_native {"L": 1800, "z": 1.5} | plain60/60 / both | 60 | +0.716 | +0.555 | +0.0171 | +1117 / +22333 | +1229 | 1089 | 0.63 | 1 | NR | - |
| 21 | 1 | trend_20 | momentum_willr.break_native {"len": 7, "lvl": 10} | sym15u / both | 60 | +0.710 | +0.546 | +0.0381 | +1107 / +22148 | +1294 | 484 | 0.63 | 1 | OTHER | - |
| 22 | 3 | tick_300 | structure_breakout.brk_native {"minutes": 5, "buf": 0.0} | sym15u / both | 120 | +0.691 | +0.537 | +0.0357 | +2157 / +43139 | +1334 | 503 | 0.68 | 2 | NR | tick_300 brk_native {"minutes": 5, "buf": 0.0} -> +2160; tick_300 brk_native {"minutes": 5, "buf": 0.0} -> +245 |
| 23 | 1 | pnf_7 | levels_vwap.break {"n": 2, "k": 0.25} | sym15u / both | 120 | +0.556 | +0.536 | +0.0434 | +1736 / +34724 | +812 | 333 | 0.69 | 0 | REV, level | - |
| 24 | 1 | bmsg_B050 | manual_cci.go {"len": 34, "lvl": 100} | sym15u / both | 60 | +0.532 | +0.576 | +0.0512 | +830 / +16592 | +367 | 270 | 0.63 | 0 | OTHER | - |
| 25 | 1 | pnf_7 | levels_sdx3.retest {"d": "E", "M": 6, "tol": 0.5} | plain60/60 / both | 60 | +0.586 | +0.528 | +0.0460 | +914 / +18290 | +550 | 331 | 0.68 | 0 | REV, level | - |
| 26 | 1 | bmsg_B130 | trend_libstack.ema_hold {"len": 34, "hold": 5} | sym15u / both | 60 | +0.603 | +0.527 | +0.0478 | +940 / +18799 | +901 | 328 | 0.60 | 0 | OTHER | - |
| 27 | 1 | dchg_14 | momentum_mvote.v4of5 {"scale": 0.25, "thr": 0.25} | sym15u / both | 120 | +0.612 | +0.519 | +0.0324 | +1910 / +38200 | +1158 | 491 | 0.65 | 1 | REV | - |
| 28 | 1 | lbrk_3_10 | tape_block.b10_follow_sm {"L": 200, "z": 1.5, "sm": 3} | asym15u/30u / both | 94 | +0.579 | +0.517 | +0.0282 | +1412 / +28234 | +174 | 534 | 0.64 | 0 | REV | - |
| 29 | 1 | tib_10000 | book_cancel.net_follow_native {"L": 1800, "z": 1.5} | sym15u / both | 120 | +0.522 | +0.517 | +0.0303 | +1628 / +32557 | +1551 | 448 | 0.69 | 0 | NR | - |
| 30 | 1 | bmsgq_B130 | structure_breakout.brk_native {"minutes": 5, "buf": 0.0} | sym15u / long | 60 | +0.553 | +0.512 | +0.0688 | +863 / +17266 | +695 | 209 | 0.69 | 0 | OTHER | - |
| 31 | 1 | dlt_70 | structure_breakout.brk_native {"minutes": 5, "buf": 0.0} | sym15u / both | 120 | +0.579 | +0.506 | +0.0296 | +1807 / +36130 | +67 | 508 | 0.64 | 0 | NR | - |
| 32 | 1 | tick_8000 | levels_open_range.break_native {"n": 3, "k": 0.25} | plain60/60 / both | 60 | +0.677 | +0.506 | +0.0394 | +1056 / +21110 | +1306 | 447 | 0.62 | 1 | NR, level | - |
| 33 | 24 | renko_40 | structure_libpattern.nr {"n": 4} | asym10u/20u / both | 120 | +0.512 | +0.503 | +0.0272 | +1598 / +31966 | +1169 | 490 | 0.60 | 0 | REV | renko_40 nr {"n": 10} -> +1864; renko_40 nr {"n": 7} -> +1598; renko_40 nr {"n": 4} -> +1598 |
| 34 | 1 | drb_2000 | book_ofi.follow_sm {"L": 100, "z": 1.5, "sm": 3} | sym15u / both | 120 | +0.502 | +0.602 | +0.0452 | +1566 / +31329 | +1230 | 289 | 0.62 | 0 | NR | - |
| 35 | 2 | urenko_20 | bands_regchan.break_stderr {"n": 20, "k": 2.0} | plain60/60 / both | 60 | +0.597 | +0.491 | +0.0123 | +932 / +18630 | +1221 | 1264 | 0.64 | 1 | REV | urenko_20 break_stderr {"n": 20, "k": 2.0} -> +25 |
| 36 | 1 | tm10 | momentum_squeeze.fire_native {"len": 14, "wd": 2.0} | asym10u/20u / both | 88 | +0.621 | +0.487 | +0.0272 | +1412 / +28239 | +614 | 593 | 0.62 | 3 | NR | - |
| 37 | 1 | tm10 | momentum_squeeze.fire {"len": 14, "wd": 2.0} | asym10u/20u / both | 88 | +0.621 | +0.487 | +0.0272 | +1412 / +28239 | +614 | 593 | 0.62 | 3 | NR | - |
| 38 | 1 | swing_atr_0.15 | manual_cci.go {"len": 50, "lvl": 150} | sym15u / both | 120 | +0.607 | +0.486 | +0.0331 | +1894 / +37874 | +1776 | 477 | 0.64 | 2 | REV | - |
| 39 | 2 | entropy_B080 | book_cancel.net_follow_native {"L": 900, "z": 1.0} | sym15u / both | 60 | +0.484 | +0.745 | +0.0304 | +755 / +15093 | +535 | 414 | 0.68 | 0 | OTHER | entropy_B080 net_follow_native {"L": 900, "z": 1.0} -> +523 |
| 40 | 1 | mom_40 | book_cancel.canc_follow {"L": 50, "z": 1.0} | plain60/60 / both | 60 | +0.476 | +0.611 | +0.0137 | +742 / +14849 | +303 | 903 | 0.62 | 0 | OTHER | - |

## NYPM - best member of the top 40 families (of 396)
| fam # | members | bar row | trigger.variant params | bracket / side | stop pts | R/wk L6M | weakest prior-yr R/wk | R/trade | L6M pts / $1 lot | L3M pts | trades L6M | persist | flags (amber yrs) | class | best neighbours (row, variant, params -> L6M pts) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 1 | vrb_240 | bands_atrchan.break_ext {"n": 10, "atr": 14, "k": 2.0} | plain60/60 / both | 60 | +0.955 | +0.776 | +0.0228 | +1489 / +29788 | +622 | 1088 | 0.67 | 1 | NR | - |
| 2 | 2 | tm1800 | xmarket_ym.follow {"w": 5, "thr": 1.0} | plain60/60 / both | 60 | +0.629 | +0.716 | +0.1083 | +981 / +19630 | +520 | 151 | 0.67 | 0 | NR | tm1800 follow {"w": 5, "thr": 1.0} -> +240 |
| 3 | 1 | tick_5000 | levels_fib15.retest_native {"M": 3, "tol": 0.0} | plain60/60 / both | 60 | +0.482 | +0.463 | +0.0437 | +752 / +15033 | +671 | 287 | 0.62 | 0 | NR, level | - |
| 4 | 1 | tick_5000 | levels_fib15.retest {"M": 3, "tol": 0.0} | plain60/60 / both | 60 | +0.482 | +0.463 | +0.0437 | +752 / +15033 | +671 | 287 | 0.62 | 0 | NR, level | - |
| 5 | 1 | tib_240 | tape_vpin.follow {"N": 10, "thr": 0.08} | plain60/60 / both | 60 | +0.465 | +0.434 | +0.0110 | +726 / +14512 | +1947 | 1102 | 0.63 | 0 | NR | - |
| 6 | 1 | vrb_700 | book_ice.follow {"thr": 1} | plain60/60 / both | 60 | +0.428 | +0.556 | +0.0118 | +668 / +13355 | +493 | 943 | 0.63 | 0 | NR | - |
| 7 | 1 | drb_1200 | tape_run.runv_fade {"thr": 60} | plain60/60 / both | 60 | +0.422 | +0.497 | +0.0344 | +658 / +13153 | +438 | 319 | 0.69 | 0 | NR | - |
| 8 | 1 | tm20 | momentum_rsi.mom {"len": 10, "lvl": 55} | sym15u / both | 98 | +0.518 | +0.405 | +0.0382 | +1314 / +26280 | +85 | 353 | 0.62 | 2 | NR | - |
| 9 | 1 | tm20 | momentum_rsi.mom_native {"len": 10, "lvl": 55} | sym15u / both | 98 | +0.518 | +0.405 | +0.0382 | +1314 / +26280 | +85 | 353 | 0.62 | 2 | NR | - |
| 10 | 1 | urenko_14 | levels_sdx3.rej {"d": "A", "F": 0, "tol": 0.5} | plain60/60 / both | 60 | +0.550 | +0.392 | +0.0611 | +858 / +17166 | +504 | 234 | 0.62 | 1 | REV, level | - |
| 11 | 1 | tick_2000 | tape_delta.cvd_fade {"N": 5, "L": 100, "z": 1.0} | plain60/60 / both | 60 | +0.524 | +0.384 | +0.0327 | +817 / +16342 | +667 | 416 | 0.60 | 2 | NR | - |
| 12 | 2 | drb_1200 | book_cancel.net_follow_native {"L": 3600, "z": 2.0} | plain60/60 / both | 60 | +0.447 | +0.362 | +0.0230 | +697 / +13934 | +239 | 504 | 0.64 | 1 | NR | drb_1200 net_follow_native {"L": 3600, "z": 2.0} -> +875 |
| 13 | 1 | vol_750 | momentum_stoch.revert_native {"len": 14, "lvl": 30} | plain60/60 / both | 60 | +0.403 | +0.358 | +0.0133 | +629 / +12583 | +768 | 790 | 0.60 | 0 | NR | - |
| 14 | 1 | swing_pct_12 | bands_envelope.fade_ema {"n": 20, "pct": 0.1} | plain60/60 / short | 60 | +0.453 | +0.323 | +0.0523 | +706 / +14121 | +137 | 225 | 0.62 | 3 | REV | - |
| 15 | 2 | tick_500 | tape_exhaust.follow {"k": 1.5, "L": 100} | asym20u/10u / both | 120 | +0.357 | +0.311 | +0.0373 | +1113 / +22266 | +408 | 249 | 0.63 | 0 | NR | tick_500 follow {"k": 1.5, "L": 100} -> +711 |
| 16 | 1 | urenko_56 | levels_fvg5.break_native {"n": 3, "k": 0.5} | plain60/60 / long | 60 | +0.305 | +0.303 | +0.0756 | +476 / +9530 | +193 | 105 | 0.60 | 0 | REV, level | - |
| 17 | 1 | time_s_5 | trend_supertrend.native {"len": 14, "width": 3.0} | plain60/60 / long | 60 | +0.362 | +0.303 | +0.0213 | +565 / +11295 | +282 | 442 | 0.62 | 1 | NR | - |
| 18 | 1 | time_s_5 | trend_supertrend.plain {"len": 14, "width": 3.0} | plain60/60 / long | 60 | +0.362 | +0.303 | +0.0213 | +565 / +11295 | +282 | 442 | 0.62 | 1 | NR | - |
| 19 | 1 | drb_240 | trend_supertrend.plain {"len": 7, "width": 2.0} | plain60/60 / both | 60 | +0.314 | +0.301 | +0.0081 | +489 / +9785 | +881 | 1008 | 0.62 | 0 | NR | - |
| 20 | 1 | tick_300 | tape_speed.follow {"f": 1.5, "L": 50} | asym10u/20u / both | 111 | +0.293 | +0.314 | +0.0213 | +847 / +16931 | +1352 | 358 | 0.60 | 0 | NR | - |
| 21 | 1 | dol_500 | levels_vwap.break_native {"n": 1, "k": 0.5} | plain60/60 / both | 60 | +0.288 | +0.563 | +0.0186 | +450 / +9001 | +276 | 404 | 0.60 | 0 | NR, level | - |
| 22 | 1 | time_s_5 | bands_atrchan.break_ext {"n": 40, "atr": 14, "k": 4.0} | plain60/60 / both | 60 | +0.279 | +0.343 | +0.0076 | +436 / +8717 | +1165 | 960 | 0.65 | 0 | NR | - |
| 23 | 1 | vol_350 | trend_psar.flip {"af0": 0.02, "step": 0.02, "max": 0.2} | plain60/60 / long | 60 | +0.310 | +0.275 | +0.0161 | +484 / +9686 | +52 | 500 | 0.60 | 0 | NR | - |
| 24 | 1 | cusum_10 | levels_vwap.break_native {"n": 2, "k": 0.5} | plain60/60 / short | 60 | +0.358 | +0.266 | +0.0478 | +559 / +11184 | +162 | 195 | 0.62 | 1 | NR, level | - |
| 25 | 1 | cusum_10 | trend_ma_t3.cross {"len": 4, "width": 2, "hyst": 0.0} | plain60/60 / long | 60 | +0.263 | +0.313 | +0.0126 | +410 / +8210 | +89 | 543 | 0.63 | 0 | NR | - |
| 26 | 1 | bmsg_B500 | book_ice.follow_sm {"thr": 1, "sm": 3} | sym15u / both | 60 | +0.347 | +0.263 | +0.0387 | +541 / +10829 | +1430 | 233 | 0.60 | 2 | OTHER | - |
| 27 | 1 | rng_10 | momentum_libosc.mfi {"len": 7, "lvl": 25} | plain60/60 / long | 60 | +0.263 | +0.258 | +0.0123 | +410 / +8199 | +413 | 556 | 0.62 | 0 | NR | - |
| 28 | 1 | tick_3200 | trend_ma_t3.price {"len": 13, "width": 0.0} | sym15u / both | 120 | +0.260 | +0.257 | +0.0332 | +812 / +16239 | +40 | 204 | 0.65 | 0 | NR | - |
| 29 | 1 | urenko_28 | levels_sdx5.lim_prox {"d": "A", "F": 0, "tgt": "opp"} | plain60/60 / short | 60 | +0.251 | +0.241 | +0.0328 | +392 / +7838 | +304 | 199 | 0.62 | 0 | REV, level | - |
| 30 | 1 | cdr_100 | bands_regchan.break_linreg {"n": 20, "k": 2.0} | plain60/60 / long | 60 | +0.279 | +0.239 | +0.0184 | +435 / +8698 | +110 | 395 | 0.63 | 0 | NR | - |
| 31 | 1 | dol_500 | levels_stack.break_native {"k": 4, "cw": 2.0} | plain60/60 / short | 60 | +0.248 | +0.235 | +0.0441 | +387 / +7733 | +132 | 146 | 0.60 | 0 | NR, level | - |
| 32 | 1 | tib_6000 | levels_trendline.break_native {"n": 3, "k": 0.5} | sym15u / long | 60 | +0.301 | +0.234 | +0.0718 | +469 / +9385 | +93 | 109 | 0.62 | 1 | NR, level | - |
| 33 | 1 | tib_6000 | book_ice.follow {"thr": 1} | plain60/60 / both | 60 | +0.234 | +0.283 | +0.0068 | +365 / +7299 | +190 | 895 | 0.60 | 0 | NR | - |
| 34 | 1 | tib_6000 | book_ice.follow_native {"thr": 1, "sm": 60} | plain60/60 / both | 60 | +0.234 | +0.283 | +0.0068 | +365 / +7299 | +190 | 895 | 0.60 | 0 | NR | - |
| 35 | 2 | vol_350 | levels_stack.break_native {"k": 2, "cw": 1.0} | sym15u / both | 120 | +0.270 | +0.234 | +0.0481 | +843 / +16866 | +5 | 146 | 0.67 | 0 | NR, level | vol_350 break_native {"k": 2, "cw": 0.5} -> +299 |
| 36 | 1 | lbrk_3_20 | book_ice.follow_sm {"thr": 1, "sm": 3} | sym15u / both | 120 | +0.232 | +0.275 | +0.0231 | +724 / +14471 | +852 | 261 | 0.69 | 0 | REV | - |
| 37 | 1 | tib_25000 | xmarket_ym.diverge {"w": 5} | sym15u / both | 120 | +0.243 | +0.232 | +0.0277 | +759 / +15179 | +701 | 228 | 0.64 | 0 | NR | - |
| 38 | 1 | tick_300 | tape_delta.fade_native {"L": 900, "z": 1.5} | sym15u / both | 120 | +0.229 | +0.254 | +0.0174 | +714 / +14288 | +18 | 343 | 0.60 | 0 | NR | - |
| 39 | 1 | cusum_56 | manual_squeeze.momturn {"len": 20} | plain60/60 / short | 60 | +0.228 | +0.305 | +0.0452 | +356 / +7111 | +309 | 131 | 0.65 | 0 | NR | - |
| 40 | 1 | tick_500 | xmarket_ym.diverge {"w": 5} | sym15u / both | 120 | +0.224 | +0.249 | +0.0184 | +700 / +14003 | +899 | 317 | 0.62 | 0 | NR | - |

Not in this table: trust + look-ahead results (phase 2), 30 same-bracket controls, the selection-corrected null, exits, layers, engine; the 12-row hand-picked list with its stage-3 numbers is kept in NEW_BOOK_SHORTLIST_12PER_SESSION_OLD.md.
