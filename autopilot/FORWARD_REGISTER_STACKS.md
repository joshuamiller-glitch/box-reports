# FORWARD REGISTER STACKS (W-TEST6, fixed 2026-11-26T20:51 UTC, nothing re-drawn)

Six stacks of 6 books drawn once, seed 20261127, from the list of books the Test 5 PRIMARY holds as of the last data date (week 182 of the walk, data to 2026-10-25), candidate set (3) (print-rule bar types and stale level cells removed). Asia A1-A3, NY AM N1-N3. At most one book per module family (trig_*) and one per near-twin group within a stack. Method: numpy default_rng(20261127), books sorted by id, per stack a fresh rng.permutation; first books that add a new module family and a new near-twin group; A1,A2,A3 then N1,N2,N3 from one generator; later stacks avoid books used by earlier ones unless 6 distinct families cannot be completed.

Use: score each stack every week from now on REAL forward data (equal weight, 1 lot per book, bare R0 own bracket, and with the session account layers), nothing re-drawn, no swaps. Book ids are the grid cell ids (W + md5 of session|row|module|params|bracket|mode); the exact set of each book is TL3_ALN_<AS|NY>_<id>_R0RT (events in /mnt/l2/l2vast/_rota/ev/<id>.parquet).

| stack | session | book ids (module, variant, bar type and size, bracket, side) | quick-screen $/lot/wk of the 6 books (equal weight, 2023-04..2026-10, no stack rules) | exact 42-month sets |
|---|---|---|---|---|
| A1 | Asia | Wabef8f99 (bands_donchian, break, time m_5, fixed40/80, long); W5d77f657 (trend_ma_sma, price, dchg 28, fixed90/30, long); Wa7df403e (levels_ob15, false_break_native, tsf 10_60, plain60/60, both); W450ab188 (momentum_mvote, v3of5, time m_3, fixed45/45, both); W57c26903 (pullback_ema, depth_native, tsf 25_40, plain60/60, both); W6d582cbb (confluence_xfam, bandflow, tsf 5_100, plain60/60, long) | 518 (L6M 1156, L3M 901) | TL3_SR_AS_T6A1_BARE / _LY |
| A2 | Asia | W109eb056 (bands_regchan, break_stderr_native, frenko 28, plain60/60, long); W852ce40a (levels_channel, break, frenko 28, fixed60/120, long); Wd116f43b (trend_ma_kama, price, renko 28, fixed40/80, long); W38c5305e (tape_sizemix, small_follow, swing atr_0.4, fixed45/45, both); W7c41e0e4 (structure_fvg, cont, tsf 5_100, plain60/60, long); Wbc4f3415 (barnative_avwap, cross, tsf 10_120, plain60/60, both) | 597 (L6M 1130, L3M 734) | TL3_SR_AS_T6A2_BARE / _LY |
| A3 | Asia | W5c3bfff6 (momentum_rsi, mom_native, tsf 25_20, plain60/60, long); W98254c75 (bands_keltner, walk, swing pct_5, fixed30/90, long); W142a885f (xmarket_es, confirm, renko 56, fixed90/30, long); W527709cc (manual_macd, zero, renko 28, fixed90/30, long); W0fe67991 (levels_vwap, break, lbrk 3_10, plain60/60, both); Wef2e1364 (trend_ma_kama, cross_native, pasl 10, fixed90/90, long) | 461 (L6M 859, L3M 519) | TL3_SR_AS_T6A3_BARE / _LY |
| N1 | NY AM | W43af5f5a (book_ofi, follow, pnf 14, fixed90/30, short); Wbcfa80fb (levels_prior_day, false_break, swing atr_0.25, fixed120/120, both); Wc0f0a762 (momentum_roc, break_native, swing atr_0.15, asym10u/20u, both); W3f23fbd1 (structure_level, sopen_cross, t3 bmsgq_B200, sym15u, long); W2b1bc7e6 (bands_keltner, walk_native, tm20 , fixed120/60, both); We52cf06e (pullback_ema, count, volor B030, fixed120/60, long) | 995 (L6M 1215, L3M 1077) | TL3_SR_NY_T6N1_BARE / _LY |
| N2 | NY AM | W6a8993ed (bands_atrchan, break_ema, bmsg B030, fixed60/120, both); Wbc90b09f (momentum_stoch, zone_break_native, swing atr_0.15, asym10u/20u, both); W01dfc899 (levels_ob5, break_native, pasl 14, fixed90/90, long); W2d6065cd (book_ofi, follow_sm, tsf 25_40, sym15u, both); W27c4dbd9 (structure_level, sopen_cross, kal volor_B200, asym10u/20u, long); W20980087 (live_seven, O7, renko 14, fixed30/90, both) | 974 (L6M 682, L3M 361) | TL3_SR_NY_T6N2_BARE / _LY |
| N3 | NY AM | Wf74d00e3 (levels_prior_day, false_break, dchg 20, fixed120/120, both); Wa3f069eb (book_ofi, follow_sm, swing atr_0.9, fixed120/60, both); We52cf06e (pullback_ema, count, volor B030, fixed120/60, long); W02b31e1f (bands_regchan, break_stderr_native, micro B030, fixed30/30, short); Waaa5a0bf (momentum_stoch, zone_break, swing atr_0.15, sym15u, both); W29a0680a (structure_level, sopen_cross, volor B080, sym15u, both) | 986 (L6M 1469, L3M 1060) | TL3_SR_NY_T6N3_BARE / _LY |

## Book details

### A1 (Asia), families trig_bands, trig_trend, trig_levels, trig_momentum, trig_pullback, trig_confluence

- Wabef8f99: module trig_bands_donchian, variant break, params {"n": 20, "buf": 0.5, "variant": "break"}, bar time m_5 (row time_m_5), bracket fixed40/80, side long; quick $/lot/wk 544, L6M 1220, L3M 615; t 4.6 over 687 trades; mark: new
- W5d77f657: module trig_trend_ma_sma, variant price, params {"len": 50, "width": 0.5, "variant": "price"}, bar dchg 28 (row dchg_28), bracket fixed90/30, side long; quick $/lot/wk 386, L6M 587, L3M 294; t 4.0 over 557 trades; mark: new
- Wa7df403e: module trig_levels_ob15, variant false_break_native, params {"M": 1, "k": 0.0, "variant": "false_break_native"}, bar tsf 10_60 (row tsf_10_60), bracket plain60/60, side both; quick $/lot/wk 311, L6M 1090, L3M 1322; t 4.7 over 210 trades; mark: new
- W450ab188: module trig_momentum_mvote, variant v3of5, params {"scale": 1.0, "thr": 1.0, "variant": "v3of5"}, bar time m_3 (row time_m_3), bracket fixed45/45, side both; quick $/lot/wk 635, L6M 1985, L3M 1972; t 4.5 over 1303 trades; mark: new
- W57c26903: module trig_pullback_ema, variant depth_native, params {"len": 5, "w": 0.5, "variant": "depth_native"}, bar tsf 25_40 (row tsf_25_40), bracket plain60/60, side both; quick $/lot/wk 787, L6M 1360, L3M 1024; t 4.2 over 1233 trades; mark: new
- W6d582cbb: module trig_confluence_xfam, variant bandflow, params {"k": 2, "w": 1, "variant": "bandflow"}, bar tsf 5_100 (row tsf_5_100), bracket plain60/60, side long; quick $/lot/wk 444, L6M 692, L3M 181; t 4.2 over 552 trades; mark: new

### A2 (Asia), families trig_bands, trig_levels, trig_trend, trig_tape, trig_structure, trig_barnative

- W109eb056: module trig_bands_regchan, variant break_stderr_native, params {"clk": 20, "k": 2.5, "variant": "break_stderr_native"}, bar frenko 28 (row frenko_28), bracket plain60/60, side long; quick $/lot/wk 607, L6M 654, L3M 679; t 4.3 over 594 trades; mark: new
- W852ce40a: module trig_levels_channel, variant break, params {"n": 1, "k": 0.25, "variant": "break"}, bar frenko 28 (row frenko_28), bracket fixed60/120, side long; quick $/lot/wk 810, L6M 1291, L3M 936; t 4.4 over 880 trades; mark: new
- Wd116f43b: module trig_trend_ma_kama, variant price, params {"len": 10, "width": 0.25, "variant": "price"}, bar renko 28 (row renko_28), bracket fixed40/80, side long; quick $/lot/wk 493, L6M 578, L3M -468; t 3.7 over 737 trades; mark: new
- W38c5305e: module trig_tape_sizemix, variant small_follow, params {"L": 200, "z": 1.0, "variant": "small_follow"}, bar swing atr_0.4 (row swing_atr_0.4), bracket fixed45/45, side both; quick $/lot/wk 831, L6M 2104, L3M 1716; t 4.2 over 2676 trades; mark: new
- W7c41e0e4: module trig_structure_fvg, variant cont, params {"w": 0.75, "variant": "cont"}, bar tsf 5_100 (row tsf_5_100), bracket plain60/60, side long; quick $/lot/wk 421, L6M 814, L3M 232; t 3.7 over 604 trades; mark: new
- Wbc4f3415: module trig_barnative_avwap, variant cross, params {"anchor": "ny", "k": 0.0, "variant": "cross"}, bar tsf 10_120 (row tsf_10_120), bracket plain60/60, side both; quick $/lot/wk 420, L6M 1342, L3M 1308; t 4.2 over 373 trades; mark: new

### A3 (Asia), families trig_momentum, trig_bands, trig_xmarket, trig_manual, trig_levels, trig_trend

- W5c3bfff6: module trig_momentum_rsi, variant mom_native, params {"len": 14, "lvl": 50, "variant": "mom_native"}, bar tsf 25_20 (row tsf_25_20), bracket plain60/60, side long; quick $/lot/wk 310, L6M 351, L3M 342; t 3.5 over 422 trades; mark: new
- W98254c75: module trig_bands_keltner, variant walk, params {"ema": 10, "atr": 10, "mult": 1.0, "N": 2, "variant": "walk"}, bar swing pct_5 (row swing_pct_5), bracket fixed30/90, side long; quick $/lot/wk 409, L6M 891, L3M 516; t 3.9 over 419 trades; mark: new
- W142a885f: module trig_xmarket_es, variant confirm, params {"w": 15, "variant": "confirm"}, bar renko 56 (row renko_56), bracket fixed90/30, side long; quick $/lot/wk 409, L6M 801, L3M 366; t 3.9 over 764 trades; mark: new
- W527709cc: module trig_manual_macd, variant zero, params {"f": 5, "s": 13, "g": 5, "variant": "zero"}, bar renko 28 (row renko_28), bracket fixed90/30, side long; quick $/lot/wk 318, L6M 80, L3M -311; t 3.6 over 598 trades; mark: new
- W0fe67991: module trig_levels_vwap, variant break, params {"n": 3, "k": 0.5, "variant": "break"}, bar lbrk 3_10 (row lbrk_3_10), bracket plain60/60, side both; quick $/lot/wk 960, L6M 1593, L3M 579; t 4.2 over 1836 trades; mark: new
- Wef2e1364: module trig_trend_ma_kama, variant cross_native, params {"len": 5, "width": 0.5, "ratio": 3, "variant": "cross_native"}, bar pasl 10 (row pasl_10), bracket fixed90/90, side long; quick $/lot/wk 357, L6M 1440, L3M 1626; t 4.3 over 188 trades; mark: new

### N1 (NY AM), families trig_book, trig_levels, trig_momentum, trig_structure, trig_bands, trig_pullback

- W43af5f5a: module trig_book_ofi, variant follow, params {"L": 50, "z": 2.0, "variant": "follow"}, bar pnf 14 (row pnf_14), bracket fixed90/30, side short; quick $/lot/wk 608, L6M -128, L3M -189; t 4.0 over 894 trades; mark: new
- Wbcfa80fb: module trig_levels_prior_day, variant false_break, params {"M": 1, "k": 0.0, "variant": "false_break"}, bar swing atr_0.25 (row swing_atr_0.25), bracket fixed120/120, side both; quick $/lot/wk 1527, L6M 3554, L3M 3470; t 4.9 over 1045 trades; mark: new
- Wc0f0a762: module trig_momentum_roc, variant break_native, params {"len": 5, "wd": 0.5, "variant": "break_native"}, bar swing atr_0.15 (row swing_atr_0.15), bracket asym10u/20u, side both; quick $/lot/wk 2315, L6M 1359, L3M 1397; t 4.8 over 2778 trades; mark: new
- W3f23fbd1: module trig_structure_level, variant sopen_cross, params {"buf": 0.0, "variant": "sopen_cross"}, bar t3 bmsgq_B200 (row t3_bmsgq_B200), bracket sym15u, side long; quick $/lot/wk 833, L6M 1040, L3M 795; t 4.0 over 486 trades; mark: new
- W2b1bc7e6: module trig_bands_keltner, variant walk_native, params {"clk": 5, "k": 1.5, "N": 3, "variant": "walk_native"}, bar tm20  (row tm20), bracket fixed120/60, side both; quick $/lot/wk 328, L6M 627, L3M 317; t 4.4 over 185 trades; mark: new
- We52cf06e: module trig_pullback_ema, variant count, params {"len": 34, "n": 3, "variant": "count"}, bar volor B030 (row volor_B030), bracket fixed120/60, side long; quick $/lot/wk 361, L6M 839, L3M 669; t 4.3 over 183 trades; mark: new

### N2 (NY AM), families trig_bands, trig_momentum, trig_levels, trig_book, trig_structure, trig_live

- W6a8993ed: module trig_bands_atrchan, variant break_ema, params {"n": 10, "atr": 14, "k": 3.0, "variant": "break_ema"}, bar bmsg B030 (row bmsg_B030), bracket fixed60/120, side both; quick $/lot/wk 558, L6M 263, L3M 169; t 4.1 over 246 trades; mark: new
- Wbc90b09f: module trig_momentum_stoch, variant zone_break_native, params {"len": 5, "lvl": 90, "variant": "zone_break_native"}, bar swing atr_0.15 (row swing_atr_0.15), bracket asym10u/20u, side both; quick $/lot/wk 2019, L6M 2129, L3M 1817; t 4.2 over 2794 trades; mark: new
- W01dfc899: module trig_levels_ob5, variant break_native, params {"n": 2, "k": 0.25, "variant": "break_native"}, bar pasl 14 (row pasl_14), bracket fixed90/90, side long; quick $/lot/wk 613, L6M -116, L3M -449; t 4.1 over 398 trades; mark: new
- W2d6065cd: module trig_book_ofi, variant follow_sm, params {"L": 50, "z": 1.0, "sm": 3, "variant": "follow_sm"}, bar tsf 25_40 (row tsf_25_40), bracket sym15u, side both; quick $/lot/wk 1365, L6M 688, L3M 491; t 4.0 over 1445 trades; mark: twin of live book Lf0346d55.BRP60 (same module+variant+side)
- W27c4dbd9: module trig_structure_level, variant sopen_cross, params {"buf": 0.25, "variant": "sopen_cross"}, bar kal volor_B200 (row kal_volor_B200), bracket asym10u/20u, side long; quick $/lot/wk 798, L6M 621, L3M -625; t 3.9 over 488 trades; mark: new
- W20980087: module trig_live_seven, variant O7, params {"live": 1, "variant": "O7"}, bar renko 14 (row renko_14), bracket fixed30/90, side both; quick $/lot/wk 491, L6M 505, L3M 763; t 4.1 over 529 trades; mark: new

### N3 (NY AM), families trig_levels, trig_book, trig_pullback, trig_bands, trig_momentum, trig_structure; reused from an earlier stack: We52cf06e

- Wf74d00e3: module trig_levels_prior_day, variant false_break, params {"M": 3, "k": 0.5, "variant": "false_break"}, bar dchg 20 (row dchg_20), bracket fixed120/120, side both; quick $/lot/wk 1385, L6M 2809, L3M 2640; t 4.5 over 1043 trades; mark: new
- Wa3f069eb: module trig_book_ofi, variant follow_sm, params {"L": 100, "z": 1.5, "sm": 3, "variant": "follow_sm"}, bar swing atr_0.9 (row swing_atr_0.9), bracket fixed120/60, side both; quick $/lot/wk 1041, L6M 874, L3M 402; t 4.3 over 1444 trades; mark: twin of live book Lf0346d55.BRP60 (same module+variant+side)
- We52cf06e: module trig_pullback_ema, variant count, params {"len": 34, "n": 3, "variant": "count"}, bar volor B030 (row volor_B030), bracket fixed120/60, side long; quick $/lot/wk 361, L6M 839, L3M 669; t 4.3 over 183 trades; mark: new
- W02b31e1f: module trig_bands_regchan, variant break_stderr_native, params {"clk": 5, "k": 2.5, "variant": "break_stderr_native"}, bar micro B030 (row micro_B030), bracket fixed30/30, side short; quick $/lot/wk 152, L6M 63, L3M -56; t 4.1 over 158 trades; mark: new
- Waaa5a0bf: module trig_momentum_stoch, variant zone_break, params {"len": 5, "lvl": 90, "variant": "zone_break"}, bar swing atr_0.15 (row swing_atr_0.15), bracket sym15u, side both; quick $/lot/wk 1819, L6M 2143, L3M 1976; t 4.2 over 2532 trades; mark: new
- W29a0680a: module trig_structure_level, variant sopen_cross, params {"buf": 0.0, "variant": "sopen_cross"}, bar volor B080 (row volor_B080), bracket sym15u, side both; quick $/lot/wk 1158, L6M 2087, L3M 728; t 4.0 over 1143 trades; mark: new
