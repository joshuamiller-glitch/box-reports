# NEW_BOOK_SHORTLIST - RULE-BASED (no top-N; W-SHORT, order 1845Z; replaces the 12-per-session list, kept as NEW_BOOK_SHORTLIST_12PER_SESSION_OLD.md)

refreshed 2026-11-22 05:20Z | screen level, bare ranking from server-2 results only (grid partitioned across servers until W-S3 merges; counts PROVISIONAL) | pick window = last 26 weeks (L6M) with last 13 (L3M) beside, equal risk (R = points / stop; risk-matched $/week = R/wk x $1,200)

RULE (a cell is shortlisted when it passes ALL): L6M > 0; >= 100 trades in L6M; L3M > 0; persistence > 0.60 (share of 2-week windows since 2023-10 positive); prior years 2023/24/25 R per week not more than 30% below the cell's own L6M R per week (RED = shown on disk, not delivered; AMBER 15-30% passes, flagged); then trust + look-ahead (phase 2, every passing cell, best first). Counts per session and the failing-reason split: autopilot/SURVIVOR_COUNTS.md. Every evaluated cell with its reason is on disk (server 2 /mnt/l2/l2vast/_grid/rule/bare_<session>.parquet) for the 2-week refit. OWN-STOP and current-stack MASK rankings beside bare: pending (full-grid arrays not built yet).

FAMILIES: cells are grouped into one family when they are the same module.variant on an adjacent bar size of the same bar type, an adjacent parameter of the same variant, or the identical parameter with another bracket / side (connected components of the grid neighbour graph). The engine runs the BEST member of a family first (highest min(L6M R/wk, weakest prior-year R/wk)); the other members are listed after it with their screen numbers; nothing is dropped. Full list (all passing cells with family id and rank in family): pass_bare_<session>.csv in the same folder. The tables below show the best member of the top 40 families per session only (for reading); the shortlist is every passing cell.

| session | cells evaluated | PASS (cells) | families | non-reversal | reversal (provisional: look-ahead gate) | level / S-D |
|---|---|---|---|---|---|---|
| Asia | 9,797,654 | **6,487** | 3,847 | 3964 | 2009 | 3183 |
| London | 10,744,790 | **3,158** | 2,237 | 1854 | 681 | 1445 |
| NYAM | 11,735,921 | **24,702** | 11,460 | 13407 | 7711 | 15343 |
| NYPM | 11,753,727 | **1,638** | 1,168 | 1059 | 214 | 562 |

## Today's engine leads (labels per PHASE2_TOOLING_TEST.md, 1932Z)

- **XA3** (NY AM tick_5000 | levels_vwap.retest_native {M 6, tol 0.5} | plain 60/60 | both): FRONT of the queue. Beats 25/30 same-bracket random draws, 30/30 date-shift engine controls (+$54,428 vs best control +$24,259); own-stop (screen) 1.5 stops L6M +1,313 pts, 3 stops +1,579 pts, prior years positive; trust pass.
- **WP10** (NY PM vol_350 | tape_libvol.cmf {len 10} | asym20u/10u | both): **lead for add-to-today's-stack at most; NOT a rebuilt-stack candidate**. Not distinguishable from random entries with its own wide bracket (beats 15/30), best date-shift control within $135 of it, own-stop weak (W-DAYMASK). No engine time ahead of R3 passers.

## Asia - best member of the top 40 families (of 3,847)
| fam # | members | bar row | trigger.variant params | bracket / side | stop pts | R/wk L6M | weakest prior-yr R/wk | R/trade | L6M pts / $1 lot | L3M pts | trades L6M | persist | flags (amber yrs) | class | best neighbours (row, variant, params -> L6M pts) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2 | dib_240 | momentum_mvote.v3of5_native {"scale": 1.0, "thr": 0.25} | plain60/60 / both | 60 | +0.395 | +0.378 | +0.0132 | +616 / +12323 | +1066 | 777 | 0.63 | 0 | NR | dib_240 v3of5_native {"scale": 1.0, "thr": 0.25} -> +57 |
| 2 | 1 | mrenko_20 | momentum_er.trend_z {"len": 10, "thr": 0.4} | plain60/60 / both | 60 | +0.374 | +0.399 | +0.0188 | +584 / +11682 | +136 | 518 | 0.65 | 0 | REV | - |
| 3 | 1 | mrenko_20 | momentum_er.trend {"len": 10, "thr": 0.4} | plain60/60 / both | 60 | +0.390 | +0.369 | +0.0195 | +608 / +12161 | +101 | 521 | 0.65 | 0 | REV | - |
| 4 | 3 | trb_400 | levels_vwap.break {"n": 2, "k": 0.5} | asym15u/30u / both | 60 | +0.405 | +0.356 | +0.0418 | +632 / +12641 | +305 | 252 | 0.64 | 0 | NR, level | trb_400 break {"n": 2, "k": 0.5} -> +157; trb_400 break {"n": 2, "k": 0.5} -> +31 |
| 5 | 1 | drb_2000 | levels_piv_cama.reject_native {"tol": 0.5, "conf": "body"} | plain60/60 / both | 60 | +0.490 | +0.345 | +0.0222 | +764 / +15275 | +351 | 573 | 0.63 | 1 | NR, level | - |
| 6 | 3 | tsf_10_60 | tape_delta.follow_native {"L": 900, "z": 1.0} | sym15u / both | 60 | +0.342 | +0.351 | +0.0353 | +534 / +10679 | +291 | 252 | 0.62 | 0 | OTHER | tsf_10_60 follow_native {"L": 900, "z": 1.0} -> +262; tsf_10_60 follow_native {"L": 900, "z": 1.0} -> +165 |
| 7 | 1 | cusum_10 | momentum_cci.brk {"len": 30, "lvl": 200} | plain60/60 / both | 60 | +0.405 | +0.342 | +0.0131 | +632 / +12633 | +93 | 806 | 0.62 | 1 | NR | - |
| 8 | 1 | time_m_7 | xmarket_rty.confirm {"w": 30} | plain60/60 / both | 60 | +0.385 | +0.342 | +0.0225 | +601 / +12010 | +126 | 444 | 0.60 | 0 | NR | - |
| 9 | 2 | tick_300 | momentum_mvote.v3of5 {"scale": 1.0, "thr": 0.25} | plain60/60 / both | 60 | +0.322 | +0.334 | +0.0173 | +502 / +10040 | +600 | 483 | 0.64 | 0 | NR | tick_300 v3of5 {"scale": 0.5, "thr": 0.25} -> +77 |
| 10 | 1 | tsf_5_50 | trend_libstack.ema_hold {"len": 13, "hold": 3} | sym15u / both | 60 | +0.391 | +0.309 | +0.0342 | +610 / +12206 | +507 | 297 | 0.63 | 1 | OTHER | - |
| 11 | 2 | vsess_30 | bands_atrchan.break_ema_native {"clk": 5, "k": 1.5} | plain60/60 / both | 60 | +0.354 | +0.304 | +0.0505 | +551 / +11029 | +122 | 182 | 0.60 | 0 | NR | vsess_30 break_ema_native {"clk": 10, "k": 1.5} -> +551 |
| 12 | 2 | vsess_30 | bands_envelope.break_ema_native {"clk": 5, "k": 1.5} | plain60/60 / both | 60 | +0.354 | +0.304 | +0.0505 | +551 / +11029 | +122 | 182 | 0.60 | 0 | NR | vsess_30 break_ema_native {"clk": 10, "k": 1.5} -> +551 |
| 13 | 2 | vol_750 | trend_libstack.ema_stack {"set": "5-13-34"} | plain60/60 / both | 60 | +0.325 | +0.299 | +0.0207 | +506 / +10128 | +356 | 407 | 0.62 | 0 | NR | vol_750 ema_stack {"set": "5-13-34"} -> +35 |
| 14 | 1 | tsf_10_60 | momentum_cci.brk_native {"len": 20, "lvl": 100} | plain60/60 / both | 60 | +0.350 | +0.298 | +0.0427 | +546 / +10916 | +410 | 213 | 0.70 | 0 | OTHER | - |
| 15 | 1 | vib_2000 | momentum_stoch.zone_break_native {"len": 14, "lvl": 70} | plain60/60 / long | 60 | +0.311 | +0.298 | +0.0218 | +485 / +9701 | +188 | 370 | 0.64 | 0 | NR | - |
| 16 | 2 | renko_10 | trend_libstack.ema_stack {"set": "13-34-89"} | plain60/60 / both | 60 | +0.291 | +0.297 | +0.0150 | +455 / +9090 | +913 | 505 | 0.62 | 0 | REV | renko_10 ema_stack {"set": "13-34-89"} -> +182 |
| 17 | 2 | wrenko_10 | trend_libstack.ema_stack {"set": "13-34-89"} | plain60/60 / both | 60 | +0.291 | +0.297 | +0.0150 | +455 / +9090 | +913 | 505 | 0.62 | 0 | REV | wrenko_10 ema_stack {"set": "13-34-89"} -> +182 |
| 18 | 16 | time_m_10 | bands_vwap.break_native {"clk": 3, "k": 1.0} | plain60/60 / both | 60 | +0.308 | +0.286 | +0.0203 | +481 / +9611 | +1341 | 394 | 0.62 | 0 | NR | time_m_10 break_native {"clk": 6, "k": 1.0} -> +481; time_m_10 break_native {"clk": 12, "k": 1.0} -> +481; time_m_10 break_native {"clk": 25, "k": 1.0} -> +481 |
| 19 | 1 | vol_500 | momentum_mvote.v3of5_native {"scale": 0.25, "thr": 0.25} | plain60/60 / both | 60 | +0.290 | +0.286 | +0.0131 | +452 / +9047 | +1146 | 575 | 0.60 | 0 | NR | - |
| 20 | 1 | dib_400 | barnative_delta.imb {"smooth": 3, "thr": 0.1} | plain60/60 / both | 60 | +0.286 | +0.346 | +0.0069 | +446 / +8923 | +268 | 1085 | 0.62 | 0 | NR | - |
| 21 | 1 | frenko_40 | book_ofi.follow_sm {"L": 50, "z": 1.0, "sm": 3} | plain60/60 / both | 60 | +0.286 | +0.322 | +0.0105 | +446 / +8916 | +73 | 708 | 0.63 | 0 | REV | - |
| 22 | 1 | tsf_5_100 | momentum_mvote.v3of5_native {"scale": 0.25, "thr": 0.25} | plain60/60 / both | 60 | +0.347 | +0.280 | +0.0349 | +542 / +10834 | +253 | 259 | 0.63 | 1 | OTHER | - |
| 23 | 3 | drb_400 | structure_orb.orb {"or_min": 15, "buf": 0.0} | plain60/60 / both | 60 | +0.376 | +0.276 | +0.0579 | +587 / +11737 | +259 | 169 | 0.70 | 1 | NR | drb_400 orb {"or_min": 5, "buf": 0.0} -> +543; drb_400 orb {"or_min": 10, "buf": 0.0} -> +22 |
| 24 | 1 | tm1800 | levels_swsr5.break {"n": 3, "k": 0.5} | plain60/60 / both | 60 | +0.356 | +0.271 | +0.0240 | +555 / +11105 | +984 | 386 | 0.60 | 1 | NR, level | - |
| 25 | 2 | tsf_5_100 | trend_heikin.run_native {"len": 5, "width": 0.25} | plain60/60 / both | 60 | +0.350 | +0.271 | +0.0281 | +545 / +10909 | +256 | 324 | 0.60 | 1 | OTHER | tsf_5_100 run_native {"len": 5, "width": 0.25} -> +87 |
| 26 | 2 | dol_750 | levels_fib5.break {"n": 2, "k": 0.5} | sym30u / both | 60 | +0.308 | +0.267 | +0.0256 | +480 / +9609 | +625 | 313 | 0.64 | 0 | NR, level | dol_750 break {"n": 2, "k": 0.5} -> +86 |
| 27 | 1 | vnorm_700 | book_ofi.follow_sm {"L": 100, "z": 1.5, "sm": 3} | sym15u / long | 60 | +0.339 | +0.266 | +0.0588 | +529 / +10578 | +593 | 150 | 0.67 | 1 | NR | - |
| 28 | 1 | mom_56 | trend_psar.flip {"af0": 0.02, "step": 0.03, "max": 0.2} | plain60/60 / both | 60 | +0.265 | +0.279 | +0.0223 | +414 / +8271 | +661 | 309 | 0.67 | 0 | OTHER | - |
| 29 | 1 | vib_3500 | levels_fvg5.reject_native {"tol": 0.5, "conf": "body"} | sym15u / both | 60 | +0.342 | +0.262 | +0.0325 | +533 / +10663 | +1896 | 273 | 0.60 | 2 | NR, level | - |
| 30 | 1 | tm2700 | bands_donchian.break_native {"clk": 20, "buf": 0.0} | plain60/60 / both | 60 | +0.340 | +0.258 | +0.0373 | +530 / +10600 | +454 | 237 | 0.70 | 1 | NR | - |
| 31 | 1 | tm2700 | bands_donchian.break_native {"clk": 5, "buf": 0.0} | plain60/60 / both | 60 | +0.340 | +0.258 | +0.0373 | +530 / +10600 | +454 | 237 | 0.70 | 1 | NR | - |
| 32 | 6 | wrenko_28 | levels_swsr5.break_native {"n": 2, "k": 0.5} | sym8u / both | 60 | +0.258 | +0.277 | +0.0201 | +403 / +8051 | +613 | 334 | 0.62 | 0 | REV, level | wrenko_28 break_native {"n": 2, "k": 0.5} -> +403; wrenko_28 break_native {"n": 2, "k": 0.5} -> +403; wrenko_28 break_native {"n": 2, "k": 0.5} -> +403 |
| 33 | 1 | urenko_14 | levels_trendline.break_native {"n": 2, "k": 0.5} | asym10u/20u / both | 88 | +0.313 | +0.256 | +0.0258 | +712 / +14241 | +58 | 315 | 0.69 | 1 | REV, level | - |
| 34 | 33 | time_m_10 | bands_vwap.walk_native {"clk": 6, "k": 1.0, "N": 3} | plain60/60 / both | 60 | +0.302 | +0.255 | +0.0291 | +471 / +9419 | +569 | 270 | 0.69 | 1 | NR | time_m_10 walk_native {"clk": 12, "k": 1.0, "N": 3} -> +471; time_m_10 walk_native {"clk": 25, "k": 1.0, "N": 3} -> +471; time_m_10 walk_native {"clk": 6, "k": 1.0, "N": 2} -> +251 |
| 35 | 1 | tm1200 | momentum_er.trend_native {"len": 10, "thr": 0.5} | plain60/60 / both | 60 | +0.257 | +0.254 | +0.0361 | +401 / +8014 | +19 | 185 | 0.70 | 0 | NR | - |
| 36 | 1 | tm1200 | momentum_er.trend {"len": 10, "thr": 0.5} | plain60/60 / both | 60 | +0.257 | +0.254 | +0.0361 | +401 / +8014 | +19 | 185 | 0.70 | 0 | NR | - |
| 37 | 1 | frenko_56 | levels_vwap.break {"n": 2, "k": 0.25} | sym15u / both | 60 | +0.285 | +0.253 | +0.0334 | +445 / +8907 | +383 | 222 | 0.67 | 0 | REV, level | - |
| 38 | 1 | time_m_60 | pullback_ema.depth_native {"len": 20, "w": 0.5} | plain60/60 / both | 60 | +0.335 | +0.253 | +0.0277 | +522 / +10449 | +29 | 314 | 0.68 | 1 | NR | - |
| 39 | 1 | dlt_45 | momentum_willr.break_native {"len": 21, "lvl": 30} | plain60/60 / both | 60 | +0.326 | +0.252 | +0.0147 | +508 / +10170 | +537 | 576 | 0.60 | 1 | NR | - |
| 40 | 4 | time_m_2 | bands_vwap.walk {"minbars": 20, "k": 1.0, "N": 2} | plain60/60 / both | 60 | +0.243 | +0.270 | +0.0145 | +379 / +7573 | +712 | 435 | 0.62 | 0 | NR | time_m_2 walk {"minbars": 20, "k": 1.0, "N": 3} -> +120; time_m_2 walk {"minbars": 20, "k": 1.0, "N": 2} -> +94; time_m_2 walk {"minbars": 20, "k": 1.0, "N": 3} -> +117 |

## London - best member of the top 40 families (of 2,237)
| fam # | members | bar row | trigger.variant params | bracket / side | stop pts | R/wk L6M | weakest prior-yr R/wk | R/trade | L6M pts / $1 lot | L3M pts | trades L6M | persist | flags (amber yrs) | class | best neighbours (row, variant, params -> L6M pts) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 1 | vnorm_700 | xmarket_rates.with_ZN {"w": 1, "thr": 1.0} | sym15u / both | 60 | +0.606 | +0.536 | +0.0597 | +946 / +18912 | +1390 | 264 | 0.60 | 0 | NR | - |
| 2 | 1 | tick_300 | book_micro.follow_sm {"L": 100, "z": 1.5, "sm": 3} | plain60/60 / both | 60 | +0.665 | +0.477 | +0.0286 | +1037 / +20740 | +1955 | 604 | 0.60 | 1 | NR | - |
| 3 | 1 | trb_400 | levels_piv_floor.reject_native {"tol": 1.0, "conf": "body"} | sym15u / both | 60 | +0.522 | +0.439 | +0.0637 | +815 / +16293 | +8 | 213 | 0.60 | 1 | NR, level | - |
| 4 | 1 | dol_750 | manual_macd.sigcross_native {"f": 5, "s": 13, "g": 4} | sym15u / both | 60 | +0.584 | +0.416 | +0.0556 | +911 / +18217 | +53 | 273 | 0.64 | 1 | NR | - |
| 5 | 2 | ha_micro_B200 | trend_ma_hma.cross_native {"len": 34, "width": 1.0, "ratio": 3} | plain60/60 / long | 60 | +0.514 | +0.414 | +0.0514 | +802 / +16037 | +520 | 260 | 0.69 | 1 | OTHER | ha_micro_B200 cross_native {"len": 34, "width": 1.0, "ratio": 3} -> +621 |
| 6 | 2 | ha_qmid_B200 | trend_ma_hma.cross_native {"len": 34, "width": 1.0, "ratio": 3} | plain60/60 / long | 60 | +0.477 | +0.412 | +0.0482 | +743 / +14867 | +460 | 257 | 0.69 | 0 | OTHER | ha_qmid_B200 cross_native {"len": 34, "width": 1.0, "ratio": 3} -> +623 |
| 7 | 1 | vib_1200 | xmarket_rates.with_ZB {"w": 5, "thr": 1.0} | sym15u / both | 60 | +0.531 | +0.399 | +0.0506 | +829 / +16572 | +334 | 273 | 0.62 | 1 | NR | - |
| 8 | 1 | tib_400 | xmarket_rates.with_ZN {"w": 1, "thr": 1.0} | plain60/60 / both | 60 | +0.509 | +0.389 | +0.0178 | +794 / +15876 | +182 | 743 | 0.62 | 1 | NR | - |
| 9 | 1 | dltor_B320 | trend_macd.hist_turn {"len": 6, "width": 0.0} | sym15u / both | 60 | +0.475 | +0.381 | +0.0394 | +741 / +14814 | +867 | 313 | 0.72 | 1 | NR | - |
| 10 | 1 | tm420 | momentum_stoch.zone_break {"len": 5, "lvl": 70} | plain60/60 / both | 60 | +0.381 | +0.490 | +0.0176 | +594 / +11878 | +571 | 562 | 0.62 | 0 | NR | - |
| 11 | 1 | tm420 | momentum_stoch.zone_break_native {"len": 5, "lvl": 70} | plain60/60 / both | 60 | +0.381 | +0.490 | +0.0176 | +594 / +11878 | +571 | 562 | 0.62 | 0 | NR | - |
| 12 | 1 | vnorm_700 | book_micro.follow_sm {"L": 100, "z": 1.5, "sm": 3} | sym15u / both | 60 | +0.411 | +0.375 | +0.0431 | +641 / +12830 | +370 | 248 | 0.63 | 0 | NR | - |
| 13 | 2 | med_bmsg_B080 | trend_linreg.thresh_native {"len": 10, "width": 1.0} | sym15u / long | 60 | +0.481 | +0.356 | +0.0863 | +751 / +15014 | +225 | 145 | 0.64 | 1 | OTHER | med_bmsg_B080 thresh_native {"len": 10, "width": 1.0} -> +505 |
| 14 | 1 | ha_qmid_B080 | bands_atrchan.break_ext_native {"clk": 5, "k": 1.0} | sym15u / long | 60 | +0.488 | +0.348 | +0.0913 | +762 / +15230 | +24 | 139 | 0.65 | 3 | OTHER | - |
| 15 | 8 | tm20 | xmarket_rates.with_ZN {"w": 1, "thr": 1.0} | plain60/60 / long | 60 | +0.366 | +0.337 | +0.0256 | +571 / +11425 | +158 | 372 | 0.62 | 0 | NR | tm30 with_ZN {"w": 1, "thr": 1.0} -> +571; tm10 with_ZN {"w": 1, "thr": 1.0} -> +571; tm15 with_ZN {"w": 1, "thr": 1.0} -> +571 |
| 16 | 2 | tm60 | xmarket_rates.with_ZN {"w": 1, "thr": 1.0} | plain60/60 / long | 60 | +0.366 | +0.337 | +0.0256 | +571 / +11425 | +158 | 372 | 0.62 | 0 | NR | tm60 with_ZN {"w": 1, "thr": 1.0} -> +359 |
| 17 | 1 | vol_4000 | levels_piv_floor.retest {"M": 6, "tol": 0.0} | plain60/60 / both | 60 | +0.406 | +0.325 | +0.0533 | +633 / +12654 | +1040 | 198 | 0.60 | 1 | NR, level | - |
| 18 | 1 | vol_4000 | levels_piv_floor.retest_native {"M": 6, "tol": 0.0} | plain60/60 / both | 60 | +0.406 | +0.325 | +0.0533 | +633 / +12654 | +1040 | 198 | 0.60 | 1 | NR, level | - |
| 19 | 1 | micro_B320 | book_ice.follow {"thr": 1} | sym15u / long | 60 | +0.321 | +0.339 | +0.0760 | +501 / +10028 | +310 | 110 | 0.60 | 0 | OTHER | - |
| 20 | 1 | qmid_B320 | book_ice.follow {"thr": 1} | sym15u / long | 60 | +0.321 | +0.339 | +0.0760 | +501 / +10028 | +310 | 110 | 0.60 | 0 | OTHER | - |
| 21 | 1 | bmsg_B320 | xmarket_rates.with_ZN {"w": 1, "thr": 1.0} | sym15u / both | 60 | +0.320 | +0.349 | +0.0300 | +500 / +9995 | +581 | 278 | 0.60 | 0 | OTHER | - |
| 22 | 1 | tsf_5_700 | xmarket_fx.with_6J {"w": 5, "thr": 1.0} | sym15u / both | 60 | +0.319 | +0.338 | +0.0774 | +497 / +9938 | +843 | 107 | 0.62 | 0 | OTHER | - |
| 23 | 1 | rngor_B320 | book_queue.follow_sm {"thr": 0.3, "min": 3, "sm": 3} | sym15u / both | 60 | +0.316 | +0.473 | +0.0575 | +493 / +9860 | +93 | 143 | 0.62 | 0 | NR | - |
| 24 | 1 | dol_2600 | structure_inside.outside {"cf": 0.75, "filt": 0} | plain60/60 / both | 60 | +0.355 | +0.307 | +0.0521 | +553 / +11063 | +281 | 177 | 0.62 | 0 | NR | - |
| 25 | 1 | med_qmid_B200 | trend_ma_hma.cross_native {"len": 34, "width": 1.0, "ratio": 3} | plain60/60 / long | 60 | +0.306 | +0.384 | +0.0306 | +478 / +9556 | +279 | 260 | 0.68 | 0 | OTHER | - |
| 26 | 2 | tsf_2_400 | xmarket_commod.against_CL {"w": 1, "thr": 1.0} | sym15u / both | 60 | +0.306 | +0.460 | +0.0313 | +477 / +9538 | +424 | 254 | 0.60 | 0 | OTHER | tsf_2_400 against_CL {"w": 1, "thr": 1.0} -> +246 |
| 27 | 1 | rngor_B320 | trend_ma_hma.cross_native {"len": 34, "width": 1.0, "ratio": 3} | sym15u / long | 60 | +0.303 | +0.464 | +0.0580 | +473 / +9458 | +154 | 136 | 0.63 | 0 | NR | - |
| 28 | 1 | tsf_10_30 | xmarket_commod.against_CL {"w": 15, "thr": 2.0} | sym15u / both | 60 | +0.303 | +0.305 | +0.0679 | +473 / +9451 | +10 | 116 | 0.64 | 0 | OTHER | - |
| 29 | 2 | bmsg_B050 | bands_regchan.break_linreg {"n": 10, "k": 1.5} | plain60/60 / long | 60 | +0.328 | +0.302 | +0.0304 | +512 / +10237 | +525 | 281 | 0.64 | 0 | OTHER | bmsg_B050 break_linreg {"n": 10, "k": 1.5} -> +22 |
| 30 | 2 | typ_qmid_B200 | trend_ma_hma.cross_native {"len": 34, "width": 1.0, "ratio": 3} | plain60/60 / long | 60 | +0.291 | +0.416 | +0.0296 | +454 / +9081 | +379 | 256 | 0.69 | 0 | OTHER | typ_qmid_B200 cross_native {"len": 34, "width": 1.0, "ratio": 3} -> +433 |
| 31 | 1 | tm1800 | levels_fib5.break {"n": 1, "k": 0.0} | plain60/60 / long | 60 | +0.408 | +0.290 | +0.0406 | +636 / +12718 | +262 | 261 | 0.68 | 3 | NR, level | - |
| 32 | 1 | tm1800 | levels_fib5.break_native {"n": 1, "k": 0.0} | plain60/60 / long | 60 | +0.408 | +0.290 | +0.0406 | +636 / +12718 | +262 | 261 | 0.68 | 3 | NR, level | - |
| 33 | 1 | entropy_B500 | levels_fib5.reject_native {"tol": 0.5, "conf": "body"} | sym15u / both | 60 | +0.288 | +0.349 | +0.0254 | +449 / +8975 | +281 | 295 | 0.60 | 0 | OTHER, level | - |
| 34 | 1 | vfp_rng16 | levels_swcluster.false_break_native {"M": 3, "k": 0.5} | sym15u / both | 60 | +0.287 | +0.320 | +0.0627 | +447 / +8950 | +415 | 119 | 0.62 | 0 | OTHER, level | - |
| 35 | 1 | vfp_rng16 | levels_swcluster.false_break {"M": 3, "k": 0.5} | sym15u / both | 60 | +0.287 | +0.301 | +0.0627 | +447 / +8950 | +415 | 119 | 0.62 | 0 | OTHER, level | - |
| 36 | 1 | vfp_rng16 | levels_swcluster.false_break {"M": 1, "k": 0.0} | sym15u / both | 60 | +0.287 | +0.327 | +0.0627 | +447 / +8950 | +415 | 119 | 0.60 | 0 | OTHER, level | - |
| 37 | 1 | vfp_rng16 | levels_swcluster.false_break_native {"M": 1, "k": 0.0} | sym15u / both | 60 | +0.287 | +0.327 | +0.0627 | +447 / +8950 | +415 | 119 | 0.60 | 0 | OTHER, level | - |
| 38 | 1 | volor_B080 | levels_swcluster.false_break {"M": 1, "k": 0.0} | plain60/60 / both | 60 | +0.289 | +0.283 | +0.0641 | +450 / +9006 | +193 | 117 | 0.64 | 0 | NR, level | - |
| 39 | 1 | volor_B080 | levels_swcluster.false_break_native {"M": 1, "k": 0.0} | plain60/60 / both | 60 | +0.289 | +0.283 | +0.0641 | +450 / +9006 | +193 | 117 | 0.64 | 0 | NR, level | - |
| 40 | 1 | tib_400 | barnative_delta.run {"n": 3, "thr": 0.0} | plain60/60 / long | 60 | +0.324 | +0.283 | +0.0200 | +506 / +10123 | +136 | 422 | 0.67 | 0 | NR | - |

## NYAM - best member of the top 40 families (of 11,460)
| fam # | members | bar row | trigger.variant params | bracket / side | stop pts | R/wk L6M | weakest prior-yr R/wk | R/trade | L6M pts / $1 lot | L3M pts | trades L6M | persist | flags (amber yrs) | class | best neighbours (row, variant, params -> L6M pts) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 1 | med_dltor_B200 | structure_level.round_break {"grid": 100, "buf": 0.25} | sym15u / both | 60 | +1.540 | +1.186 | +0.0962 | +2402 / +48034 | +954 | 416 | 0.69 | 2 | OTHER, level | - |
| 2 | 2 | sessrng_B030 | book_ofi.follow_sm {"L": 100, "z": 1.5, "sm": 3} | sym15u / both | 60 | +1.273 | +1.102 | +0.1118 | +1985 / +39706 | +624 | 296 | 0.65 | 0 | OTHER | sessrng_B030 follow_sm {"L": 100, "z": 1.5, "sm": 3} -> +476 |
| 3 | 1 | kal_micro_B200 | pullback_ema.count {"len": 10, "n": 2} | sym15u / both | 60 | +1.261 | +1.062 | +0.0865 | +1967 / +39347 | +206 | 379 | 0.62 | 1 | OTHER | - |
| 4 | 1 | lbrk_5_40 | xmarket_fast.revert_ES {"w": 60, "thr": 2.0} | sym15u / both | 60 | +1.354 | +1.055 | +0.2427 | +2111 / +42229 | +831 | 145 | 0.67 | 2 | REV | - |
| 5 | 2 | vnorm_1500 | momentum_willr.break {"len": 7, "lvl": 10} | sym15u / both | 60 | +1.262 | +0.994 | +0.0629 | +1969 / +39388 | +534 | 522 | 0.65 | 1 | NR | vnorm_1500 break {"len": 7, "lvl": 10} -> +1365 |
| 6 | 1 | t3_dltor_B080 | levels_round.break {"n": 2, "k": 0.25} | sym15u / both | 60 | +1.097 | +0.971 | +0.0561 | +1711 / +34225 | +719 | 508 | 0.64 | 0 | OTHER, level | - |
| 7 | 1 | med_qmid_B080 | book_ofi.follow_native {"L": 3600, "z": 2.0} | sym15u / both | 60 | +1.080 | +0.909 | +0.0784 | +1685 / +33695 | +1174 | 358 | 0.62 | 1 | OTHER | - |
| 8 | 1 | t3_micro_B080 | book_ofi.follow_native {"L": 3600, "z": 2.0} | sym15u / both | 60 | +1.080 | +0.909 | +0.0784 | +1685 / +33695 | +1174 | 358 | 0.62 | 1 | OTHER | - |
| 9 | 1 | med_micro_B080 | book_ofi.follow_native {"L": 3600, "z": 2.0} | sym15u / both | 60 | +1.080 | +0.909 | +0.0784 | +1685 / +33695 | +1174 | 358 | 0.62 | 1 | OTHER | - |
| 10 | 1 | typ_micro_B080 | book_ofi.follow_native {"L": 3600, "z": 2.0} | sym15u / both | 60 | +1.080 | +0.909 | +0.0784 | +1685 / +33695 | +1174 | 358 | 0.62 | 1 | OTHER | - |
| 11 | 1 | ha_qmid_B080 | book_ofi.follow_native {"L": 3600, "z": 2.0} | sym15u / both | 60 | +1.080 | +0.909 | +0.0784 | +1685 / +33695 | +1174 | 358 | 0.62 | 1 | OTHER | - |
| 12 | 1 | kal_micro_B080 | book_ofi.follow_native {"L": 3600, "z": 2.0} | sym15u / both | 60 | +1.080 | +0.909 | +0.0784 | +1685 / +33695 | +1174 | 358 | 0.62 | 1 | OTHER | - |
| 13 | 1 | ha_micro_B080 | book_ofi.follow_native {"L": 3600, "z": 2.0} | sym15u / both | 60 | +1.080 | +0.909 | +0.0784 | +1685 / +33695 | +1174 | 358 | 0.62 | 1 | OTHER | - |
| 14 | 1 | typ_qmid_B080 | book_ofi.follow_native {"L": 3600, "z": 2.0} | sym15u / both | 60 | +1.080 | +0.909 | +0.0784 | +1685 / +33695 | +1174 | 358 | 0.62 | 1 | OTHER | - |
| 15 | 1 | t3_qmid_B080 | book_ofi.follow_native {"L": 3600, "z": 2.0} | sym15u / both | 60 | +1.080 | +0.909 | +0.0784 | +1685 / +33695 | +1174 | 358 | 0.62 | 1 | OTHER | - |
| 16 | 1 | kal_qmid_B080 | book_ofi.follow_native {"L": 3600, "z": 2.0} | sym15u / both | 60 | +1.080 | +0.909 | +0.0784 | +1685 / +33695 | +1174 | 358 | 0.62 | 1 | OTHER | - |
| 17 | 1 | micro_B080 | bands_atrchan.break_ema {"n": 40, "atr": 14, "k": 3.0} | sym15u / both | 60 | +1.136 | +0.896 | +0.1354 | +1772 / +35432 | +1200 | 218 | 0.67 | 2 | OTHER | - |
| 18 | 1 | bmsgq_B050 | book_cancel.canc_follow {"L": 50, "z": 1.0} | sym15u / both | 60 | +1.062 | +0.895 | +0.0713 | +1657 / +33134 | +307 | 387 | 0.60 | 1 | OTHER | - |
| 19 | 1 | micro_B320 | momentum_mvote.v3of5 {"scale": 2.0, "thr": 1.0} | sym15u / both | 60 | +0.894 | +0.902 | +0.0713 | +1395 / +27901 | +1422 | 326 | 0.70 | 0 | OTHER | - |
| 20 | 2 | qmid_B080 | bands_atrchan.break_ema {"n": 40, "atr": 14, "k": 3.0} | sym15u / both | 60 | +0.964 | +0.882 | +0.1139 | +1503 / +30066 | +1131 | 220 | 0.68 | 0 | OTHER | qmid_B130 break_ema {"n": 40, "atr": 14, "k": 3.0} -> +901 |
| 21 | 1 | med_dltor_B200 | trend_libstack.wave_agree {"set": "fast"} | sym15u / both | 60 | +1.029 | +0.879 | +0.0552 | +1605 / +32107 | +126 | 485 | 0.67 | 0 | OTHER | - |
| 22 | 1 | lbrk_4_40 | xmarket_fast.revert_ES {"w": 60, "thr": 2.0} | sym15u / both | 60 | +1.191 | +0.874 | +0.2038 | +1859 / +37173 | +253 | 152 | 0.60 | 2 | REV | - |
| 23 | 1 | kal_volor_B080 | tape_stoprun.fade {"N": 20, "k": 0.25} | sym15u / both | 60 | +1.173 | +0.867 | +0.0684 | +1830 / +36593 | +779 | 446 | 0.64 | 1 | OTHER | - |
| 24 | 1 | frenko_40 | book_ofi.follow_sm {"L": 200, "z": 2.0, "sm": 3} | plain60/60 / both | 60 | +1.122 | +0.853 | +0.0501 | +1751 / +35011 | +147 | 582 | 0.63 | 2 | REV | - |
| 25 | 1 | kal_qmid_B200 | pullback_ema.count {"len": 10, "n": 2} | sym15u / both | 60 | +1.052 | +0.842 | +0.0722 | +1641 / +32825 | +212 | 379 | 0.60 | 1 | OTHER | - |
| 26 | 1 | med_bmsgq_B200 | bands_keltner.break {"ema": 30, "atr": 10, "mult": 2.5} | sym15u / both | 60 | +0.834 | +0.932 | +0.0730 | +1301 / +26026 | +1270 | 297 | 0.65 | 0 | OTHER | - |
| 27 | 3 | typ_sessrng_B200 | structure_level.round_break {"grid": 50, "buf": 0.0} | sym15u / both | 60 | +0.824 | +0.831 | +0.0406 | +1286 / +25717 | +116 | 528 | 0.63 | 0 | OTHER, level | typ_sessrng_B200 round_break {"grid": 50, "buf": 0.0} -> +1235; typ_sessrng_B080 round_break {"grid": 50, "buf": 0.0} -> +371 |
| 28 | 1 | trend_14 | tape_run.runv_follow {"thr": 15} | sym15u / both | 60 | +0.848 | +0.824 | +0.0412 | +1324 / +26472 | +728 | 535 | 0.60 | 0 | OTHER | - |
| 29 | 2 | bmsg_B200 | bands_bollinger.walk {"n": 30, "k": 2.0, "N": 3} | sym15u / both | 60 | +0.884 | +0.817 | +0.0759 | +1380 / +27593 | +1784 | 303 | 0.63 | 0 | OTHER | bmsg_B200 walk {"n": 30, "k": 2.0, "N": 3} -> +914 |
| 30 | 1 | vrb_3500 | tape_sizemix.diff_follow {"L": 200, "thr": 1.0} | sym15u / both | 60 | +0.808 | +0.805 | +0.0463 | +1260 / +25199 | +532 | 454 | 0.63 | 0 | NR | - |
| 31 | 1 | vib_6000 | book_cancel.net_follow_native {"L": 900, "z": 1.0} | sym30u / both | 60 | +0.806 | +0.802 | +0.0406 | +1257 / +25142 | +1496 | 516 | 0.60 | 0 | NR | - |
| 32 | 1 | swing_atr_0.15 | momentum_willr.break_native {"len": 14, "lvl": 10} | plain60/60 / both | 60 | +0.906 | +0.794 | +0.0129 | +1413 / +28259 | +21 | 1828 | 0.63 | 0 | REV | - |
| 33 | 6 | dol_1700 | book_ofi.follow_sm {"L": 100, "z": 2.0, "sm": 3} | sym8u / both | 60 | +0.766 | +0.770 | +0.0844 | +1195 / +23902 | +1014 | 236 | 0.65 | 0 | NR | dol_1700 follow_sm {"L": 100, "z": 2.0, "sm": 3} -> +1171; dol_1700 follow_sm {"L": 100, "z": 2.0, "sm": 3} -> +1171; dol_1700 follow_sm {"L": 100, "z": 2.0, "sm": 3} -> +1171 |
| 34 | 1 | dol_1700 | levels_vwap.break_native {"n": 2, "k": 0.25} | sym15u / both | 60 | +0.765 | +0.771 | +0.0592 | +1193 / +23858 | +152 | 336 | 0.73 | 0 | NR, level | - |
| 35 | 2 | med_bmsgq_B200 | structure_level.round_break {"grid": 50, "buf": 0.0} | sym15u / both | 60 | +0.763 | +0.763 | +0.0386 | +1190 / +23797 | +282 | 514 | 0.60 | 0 | OTHER, level | med_bmsgq_B080 round_break {"grid": 50, "buf": 0.0} -> +129 |
| 36 | 1 | trb_1200 | levels_fibr_dev.reject {"tol": 1.0, "conf": "body"} | sym15u / both | 60 | +0.748 | +0.786 | +0.0455 | +1167 / +23337 | +1170 | 427 | 0.62 | 0 | NR, level | - |
| 37 | 1 | med_qmid_B200 | pullback_st.st {"st_mult": 3.0, "ema": 14, "arm": 10} | sym15u / both | 60 | +0.745 | +0.753 | +0.0507 | +1162 / +23249 | +371 | 382 | 0.64 | 0 | OTHER | - |
| 38 | 1 | dol_1100 | levels_vwap.break_native {"n": 3, "k": 0.5} | sym15u / both | 60 | +1.045 | +0.743 | +0.0797 | +1630 / +32593 | +248 | 341 | 0.64 | 3 | NR, level | - |
| 39 | 1 | vrb_2000 | levels_profile_va.false_break_native {"M": 3, "k": 0.5} | sym15u / both | 60 | +0.997 | +0.729 | +0.1379 | +1555 / +31104 | +847 | 188 | 0.60 | 2 | NR, level | - |
| 40 | 1 | bmsg_B130 | bands_bollinger.break {"n": 30, "k": 2.5} | sym15u / both | 60 | +0.721 | +0.733 | +0.0705 | +1125 / +22492 | +814 | 266 | 0.65 | 0 | OTHER | - |

## NYPM - best member of the top 40 families (of 1,168)
| fam # | members | bar row | trigger.variant params | bracket / side | stop pts | R/wk L6M | weakest prior-yr R/wk | R/trade | L6M pts / $1 lot | L3M pts | trades L6M | persist | flags (amber yrs) | class | best neighbours (row, variant, params -> L6M pts) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 1 | vrb_240 | bands_atrchan.break_ext {"n": 10, "atr": 14, "k": 2.0} | plain60/60 / both | 60 | +0.955 | +0.776 | +0.0228 | +1489 / +29788 | +622 | 1088 | 0.67 | 1 | NR | - |
| 2 | 1 | trb_700 | xmarket_fast.follow_RTY {"w": 5, "thr": 1.0} | sym15u / both | 60 | +0.930 | +0.764 | +0.0683 | +1452 / +29031 | +1367 | 354 | 0.65 | 1 | NR | - |
| 3 | 1 | tsf_2_100 | levels_trendline.break {"n": 3, "k": 0.5} | sym15u / both | 60 | +0.954 | +0.724 | +0.0940 | +1489 / +29776 | +512 | 264 | 0.67 | 2 | OTHER, level | - |
| 4 | 1 | vnorm_1000 | structure_level.round_reject {"grid": 50, "buf": 0.0} | sym15u / both | 60 | +0.801 | +0.688 | +0.0647 | +1250 / +24992 | +1252 | 322 | 0.65 | 0 | NR, level | - |
| 5 | 1 | t3_sessrng_B200 | tape_libvol.obv {"len": 10} | plain60/60 / both | 60 | +0.765 | +0.670 | +0.0250 | +1193 / +23865 | +1124 | 794 | 0.63 | 0 | OTHER | - |
| 6 | 7 | tm1800 | xmarket_ym.follow {"w": 5, "thr": 1.0} | plain60/60 / both | 60 | +0.629 | +0.716 | +0.1083 | +981 / +19630 | +520 | 151 | 0.67 | 0 | NR | tm1800 follow {"w": 5, "thr": 1.0} -> +240; tm1800 follow {"w": 5, "thr": 1.0} -> +240; tm1800 follow {"w": 5, "thr": 1.0} -> +240 |
| 7 | 2 | tsf_5_700 | levels_trendline.reject_native {"tol": 0.5, "conf": "body"} | sym15u / both | 60 | +0.882 | +0.623 | +0.1097 | +1376 / +27518 | +357 | 209 | 0.63 | 2 | OTHER, level | tsf_5_700 reject_native {"tol": 1.0, "conf": "body"} -> +455 |
| 8 | 1 | vib_15000 | book_pslope.follow {"L": 100, "z": 1.5} | sym15u / both | 60 | +0.552 | +0.550 | +0.0491 | +861 / +17218 | +994 | 292 | 0.62 | 0 | NR | - |
| 9 | 1 | vib_10000 | tape_run.runv_fade {"thr": 100} | plain60/60 / both | 60 | +0.571 | +0.524 | +0.0316 | +891 / +17815 | +1035 | 470 | 0.63 | 0 | NR | - |
| 10 | 1 | typ_dltor_B080 | book_pslope.follow {"L": 200, "z": 2.0} | sym15u / both | 60 | +0.516 | +0.514 | +0.0561 | +805 / +16103 | +668 | 239 | 0.64 | 0 | OTHER | - |
| 11 | 1 | t3_dltor_B080 | book_pslope.follow {"L": 200, "z": 2.0} | sym15u / both | 60 | +0.516 | +0.514 | +0.0561 | +805 / +16103 | +668 | 239 | 0.64 | 0 | OTHER | - |
| 12 | 1 | dltor_B080 | book_pslope.follow {"L": 200, "z": 2.0} | sym15u / both | 60 | +0.516 | +0.514 | +0.0561 | +805 / +16103 | +668 | 239 | 0.63 | 0 | NR | - |
| 13 | 1 | ha_dltor_B080 | book_pslope.follow {"L": 200, "z": 2.0} | sym15u / both | 60 | +0.516 | +0.514 | +0.0561 | +805 / +16103 | +668 | 239 | 0.64 | 0 | OTHER | - |
| 14 | 1 | med_dltor_B080 | book_pslope.follow {"L": 200, "z": 2.0} | sym15u / both | 60 | +0.516 | +0.514 | +0.0561 | +805 / +16103 | +668 | 239 | 0.64 | 0 | OTHER | - |
| 15 | 1 | kal_dltor_B080 | book_pslope.follow {"L": 200, "z": 2.0} | sym15u / both | 60 | +0.516 | +0.514 | +0.0561 | +805 / +16103 | +668 | 239 | 0.64 | 0 | OTHER | - |
| 16 | 1 | kal_dltor_B200 | levels_round.reject {"tol": 1.0, "conf": "body"} | sym15u / both | 60 | +0.509 | +0.534 | +0.0377 | +795 / +15893 | +583 | 351 | 0.60 | 0 | OTHER, level | - |
| 17 | 1 | kal_bmsg_B200 | trend_ma_hma.price_native {"len": 50, "width": 1.0} | sym15u / both | 60 | +0.506 | +0.554 | +0.0458 | +789 / +15788 | +746 | 287 | 0.63 | 0 | OTHER | - |
| 18 | 2 | rng_10 | levels_fibr_dev.break {"n": 3, "k": 0.0} | plain60/60 / both | 60 | +0.578 | +0.504 | +0.0169 | +902 / +18030 | +774 | 888 | 0.62 | 0 | NR, level | rng_10 break {"n": 3, "k": 0.25} -> +646 |
| 19 | 1 | rng_10 | levels_fibr_dev.break_native {"n": 3, "k": 0.0} | plain60/60 / both | 60 | +0.578 | +0.504 | +0.0169 | +902 / +18030 | +774 | 888 | 0.62 | 0 | NR, level | - |
| 20 | 1 | dib_2000 | manual_squeeze.fire {"len": 20, "kc": 2.0} | plain60/60 / both | 60 | +0.491 | +0.803 | +0.0182 | +765 / +15306 | +710 | 702 | 0.65 | 0 | NR | - |
| 21 | 1 | dltor_B200 | levels_trendline.reject {"tol": 1.0, "conf": "body"} | plain60/60 / both | 60 | +0.621 | +0.484 | +0.0347 | +969 / +19385 | +1410 | 465 | 0.64 | 1 | NR, level | - |
| 22 | 1 | vnorm_250 | xmarket_rates.with_ZN {"w": 1, "thr": 1.0} | sym15u / both | 60 | +0.470 | +0.510 | +0.0390 | +733 / +14665 | +478 | 313 | 0.60 | 0 | NR | - |
| 23 | 1 | tick_5000 | levels_fib15.retest {"M": 3, "tol": 0.0} | plain60/60 / both | 60 | +0.482 | +0.463 | +0.0437 | +752 / +15033 | +671 | 287 | 0.62 | 0 | NR, level | - |
| 24 | 1 | tick_5000 | levels_fib15.retest_native {"M": 3, "tol": 0.0} | plain60/60 / both | 60 | +0.482 | +0.463 | +0.0437 | +752 / +15033 | +671 | 287 | 0.62 | 0 | NR, level | - |
| 25 | 1 | typ_bmsgq_B200 | bands_regchan.break_linreg_native {"clk": 10, "k": 2.0} | plain60/60 / both | 60 | +0.437 | +0.519 | +0.0209 | +682 / +13635 | +300 | 543 | 0.60 | 0 | OTHER | - |
| 26 | 1 | tib_240 | tape_vpin.follow {"N": 10, "thr": 0.08} | plain60/60 / both | 60 | +0.465 | +0.434 | +0.0110 | +726 / +14512 | +1947 | 1102 | 0.63 | 0 | NR | - |
| 27 | 1 | trb_1200 | structure_libpattern.threebar {"filt": 0} | plain60/60 / both | 60 | +0.509 | +0.432 | +0.0160 | +794 / +15878 | +85 | 825 | 0.60 | 1 | NR | - |
| 28 | 1 | vrb_700 | book_ice.follow {"thr": 1} | plain60/60 / both | 60 | +0.428 | +0.556 | +0.0118 | +668 / +13355 | +493 | 943 | 0.63 | 0 | NR | - |
| 29 | 1 | tpo_30m | xmarket_es.follow {"w": 5, "thr": 1.0} | plain60/60 / both | 60 | +0.584 | +0.423 | +0.0867 | +910 / +18209 | +1098 | 175 | 0.63 | 1 | OTHER | - |
| 30 | 1 | entropy_B050 | trend_macd.zero_native {"len": 12, "width": 0.1} | sym15u / both | 60 | +0.550 | +0.422 | +0.0714 | +857 / +17145 | +621 | 200 | 0.64 | 2 | OTHER | - |
| 31 | 1 | drb_1200 | tape_run.runv_fade {"thr": 60} | plain60/60 / both | 60 | +0.422 | +0.497 | +0.0344 | +658 / +13153 | +438 | 319 | 0.69 | 0 | NR | - |
| 32 | 1 | vib_2000 | levels_trendline.break_native {"n": 3, "k": 0.5} | sym15u / both | 60 | +0.452 | +0.416 | +0.0437 | +705 / +14105 | +29 | 269 | 0.60 | 0 | NR, level | - |
| 33 | 1 | trb_400 | confluence_xfam.fadeset {"k": 3, "w": 6} | plain60/60 / both | 60 | +0.581 | +0.414 | +0.0243 | +907 / +18133 | +2349 | 622 | 0.62 | 1 | NR | - |
| 34 | 1 | tm20 | momentum_rsi.mom_native {"len": 10, "lvl": 55} | sym15u / both | 98 | +0.518 | +0.405 | +0.0382 | +1314 / +26280 | +85 | 353 | 0.62 | 2 | NR | - |
| 35 | 1 | tm20 | momentum_rsi.mom {"len": 10, "lvl": 55} | sym15u / both | 98 | +0.518 | +0.405 | +0.0382 | +1314 / +26280 | +85 | 353 | 0.62 | 2 | NR | - |
| 36 | 1 | renko_40 | levels_channel.false_break_native {"M": 1, "k": 0.5} | plain60/60 / both | 60 | +0.399 | +0.727 | +0.0262 | +622 / +12437 | +698 | 396 | 0.64 | 0 | REV, level | - |
| 37 | 1 | qmid_B320 | momentum_roc.zero {"len": 20, "wd": 3} | sym15u / both | 60 | +0.455 | +0.390 | +0.0409 | +710 / +14200 | +708 | 289 | 0.62 | 0 | OTHER | - |
| 38 | 1 | volor_B080 | trend_macd.zero_native {"len": 6, "width": 0.0} | sym15u / both | 60 | +0.430 | +0.389 | +0.0367 | +671 / +13424 | +737 | 305 | 0.60 | 0 | NR | - |
| 39 | 1 | frenko_80 | levels_fvg5.false_break_native {"M": 1, "k": 0.0} | sym15u / both | 60 | +0.387 | +0.424 | +0.0846 | +604 / +12080 | +733 | 119 | 0.65 | 0 | REV, level | - |
| 40 | 1 | frenko_80 | levels_fvg5.false_break {"M": 1, "k": 0.0} | sym15u / both | 60 | +0.387 | +0.424 | +0.0846 | +604 / +12080 | +733 | 119 | 0.65 | 0 | REV, level | - |

Not in this table: trust + look-ahead results (phase 2), 30 same-bracket controls, the selection-corrected null, exits, layers, engine; the 12-row hand-picked list with its stage-3 numbers is kept in NEW_BOOK_SHORTLIST_12PER_SESSION_OLD.md.
