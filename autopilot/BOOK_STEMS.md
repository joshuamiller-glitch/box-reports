# BOOK_STEMS - map from session / MF number / L-hash to the LIVE STEM NAME (W-DYNA, 27 Nov 16:15 UTC; order 1612Z item 3)

Answer first: the MF numbers in every exact-engine table are the `tag` of the book in the live set JSON (/mnt/l2/l2vast/_th_sz/ijk/exact/sets/<set>.json, hooklist mf_multi streams): SPEC. The stem names asked for (NY-FIB, NY-NODE, AS-NR7, LO-CRUDE) match the trigger modules of the cells exactly (NY MF1 = fib-retracement false break, NY MF4 = volume-profile node false break, Asia MF1 = NR7 pattern, London MF1 = crude-oil (CL) cross-market): the other stems below are DERIVED by me from the trigger module and are READING until the relay confirms the NT8 names. Use `STEM (MFn)` in tables for Josh.

Sets: Asia TL3_SR_AS_STKd8da2eb47b_FSff6_PICKC; NY AM TL3_SR_NY_STKd8cd0279ff_FSff6_PICKC (9 books); NY PM TL3_SR_NP_STKd893133bd8_FSf46_PICKC (4 books); London TL3_SR_LO_STKd8w42lo_FSffb8_BARE (3 books) = 20 books. Bracket = stop/target points of the trades in the exact set (median); "set lots" = median lots per trade in the exact set that my tables use (the live FILE lots are the file-size rows of FILTERED_PICKS_FILE_SIZE.md, e.g. NY AM 6/6/6/6/3/6/1/1/3 at size 6/3/1: READING for the file); long/short = share of the trades that are long in the set; "cell mode" = what the cell is allowed to trade.

| session | MF | STEM | stem status | hash (cell id.bracket variant) | trigger (module variant params) | bracket stop/target pts | set lots | long share (cell mode) | trades in set |
|---|---|---|---|---|---|---|---|---|---|
| Asia | MF1 | AS-NR7 | SPEC (Josh/relay name) | Lb0e6dfa3_R0_F40_80 | structure_libpattern nr {"n": 7} | 40/80 | 3 | 52% long (cell mode long) | 1963 |
| Asia | MF2 | AS-RSI | READING (derived from the trigger module) | L385f4f2e_CX502 | momentum_rsi mom {"len": 14, "lvl": 60} | 60/60 | 3 | 55% long (cell mode both) | 638 |
| Asia | MF3 | AS-VWAPBRK | READING (derived from the trigger module) | L9c2622b0_R0_P45 | levels_vwap break {"n": 3, "k": 0.5} | 45/45 | 3 | 49% long (cell mode long) | 2602 |
| Asia | MF4 | AS-VWAPBAND | READING (derived from the trigger module) | L4aaacdb2_R0_P30 | bands_vwap break {"minbars": 20, "k": 1.0} | 30/30 | 3 | 47% long (cell mode both) | 908 |
| NY AM | MF1 | NY-FIB | SPEC (Josh/relay name) | L43f0cbfb.BRS8U | levels_fibr_on false_break {"M": 3, "k": 0.5} | 120/120 | 3 | 47% long (cell mode long) | 1652 |
| NY AM | MF2 | NY-VALUE | READING (derived from the trigger module) | B7bfd33b7 | levels_profile_va break_native {"n": 2, "k": 0.25} | 60/60 | 3 | 51% long (cell mode both) | 1988 |
| NY AM | MF3 | NY-SOPEN | READING (derived from the trigger module) | Bf428c4a1.BRS8U | structure_level sopen_cross {"buf": 0.0} | 120/120 | 3 | 50% long (cell mode both) | 986 |
| NY AM | MF4 | NY-NODE | SPEC (Josh/relay name) | Le4fede95.BRF90_30 | levels_profile_nodes false_break_native {"M": 2, "k": 0.5} | 90/30 | 3 | 49% long (cell mode both) | 3296 |
| NY AM | MF5 | NY-OFI | READING (derived from the trigger module) | Lf0346d55.BRP60 | book_ofi follow_sm {"L": 200, "z": 2.0, "sm": 3} | 60/60 | 2 | 64% long (cell mode both) | 2604 |
| NY AM | MF6 | NY-BLOCK | READING (derived from the trigger module) | L8cfda948.BRF90_30 | tape_block b10_follow_sm {"L": 50, "z": 1.0, "sm": 3} | 90/30 | 3 | 100% long (cell mode long) | 2933 |
| NY AM | MF7 | NY-BOLL | READING (derived from the trigger module) | L4407508c.BRF120_60 | bands_bollinger walk {"n": 30, "k": 1.5, "N": 2} | 120/60 | 1 | 100% long (cell mode long) | 885 |
| NY AM | MF8 | NY-EMA | READING (derived from the trigger module) | L39287638.BRF80_40 | trend_ma_ema cross {"len": 20, "width": 2, "hyst": 0.0} | 80/40 | 1 | 50% long (cell mode both) | 927 |
| NY AM | MF9 | NY-AVWAP | READING (derived from the trigger module) | L64390867.BRF80_40 | bands_avwap0830 break_0830_native {"clk": 3, "k": 1.0} | 80/40 | 2 | 100% long (cell mode long) | 681 |
| NY PM | MF1 | NP-ATRFADE | READING (derived from the trigger module) | L52359bf4_R0_P30 | bands_atrchan fade_ext {"n": 40, "atr": 14, "k": 4.0} | 30/30 | 3 | 48% long (cell mode both) | 3553 |
| NY PM | MF2 | NP-ZN | READING (derived from the trigger module) | L8e0bf58c_R0_S8U | xmarket_rates with_ZN {"w": 1, "thr": 1.0} | scaled bracket sym8u (stop/target = 8 x unit, no fixed points in the set trades) | 3 | 50% long (cell mode both) | 587 |
| NY PM | MF3 | NP-YM | READING (derived from the trigger module) | L4bdd521a_R0_F80_40 | xmarket_ym follow {"w": 5, "thr": 1.0} | 80/40 | 3 | 51% long (cell mode both) | 1138 |
| NY PM | MF4 | NP-DIVFADE | READING (derived from the trigger module) | L2c6916a5_R0_P60 | tape_div div_fade {"N": 20, "k": 0.5} | 60/60 | 3 | 56% long (cell mode both) | 1802 |
| London | MF1 | LO-CRUDE | SPEC (Josh/relay name) | L19201dfc.BRF90_30 | xmarket_commod against_CL {"w": 15, "thr": 2.0} | 90/30 | 8 | 53% long (cell mode both) | 1130 |
| London | MF2 | LO-IMB | READING (derived from the trigger module) | L12842dde.BRP45 | book_imb follow_native {"lv": 1, "thr": 0.35, "sm": 60} | 45/45 | 4 | 100% long (cell mode long) | 3097 |
| London | MF3 | LO-ZB | READING (derived from the trigger module) | L74274eca.BRF120_60 | xmarket_rates with_ZB {"w": 5, "thr": 1.0} | 120/60 | 2 | 50% long (cell mode both) | 1866 |

## Extra NY PM books named in the plans (not in the 4-book live set JSON; READING from code/th_plan_np/data.py and the cell registry)

| stem | MF / name | hash | trigger | bracket |
|---|---|---|---|---|
| NP-MACD | NPMACD | L6d238076_R0_F90_30 | manual_macd sigcross {"f":12,"s":26,"g":9} | 90/30 |
| NP-CONF | NPCONF | L8dff280f_R0_P90 | confluence_user u3a {"k":2,"w":1} (2-of-3 squeeze/MACD/CCI) | 90/90 |

## How the map was made
- MF tag -> events file -> cell id: the set JSON `hooklist[mf_multi].par.streams[*].tag/events` (SPEC). Cell id -> trigger module, variant, params, mode: `dx_build.cell2(id)` reading /mnt/l2/l2vast/_nye/ladder_cells_both.json and _lon/ladder_cells.json (SPEC). Stem names = Josh/relay names for four books (checked against the modules) + my derivation from the module for the rest (READING): FIB = fibr_on, NODE = profile_nodes, VALUE = profile value-area break, SOPEN = session-open cross, OFI = order-flow imbalance, BLOCK = tape block, BOLL = Bollinger walk, EMA = EMA cross, AVWAP = anchored VWAP from 08:30, ATRFADE = ATR-channel fade, DIVFADE = tape divergence fade, ZN/ZB/YM = rates / equity-index cross-market, IMB = book imbalance, RSI = RSI momentum, VWAPBRK / VWAPBAND = VWAP break / VWAP band break, NR7 = narrow-range-7 pattern, CRUDE = CL.
- Only the MF numbers inside one set are unique: NY AM MF5 and NY PM MF1 are different books. Tables should print `STEM (SESSION MFn)`.
- Names are not used by the engine; if the relay confirms different NT8 names, only the STEM column changes.
