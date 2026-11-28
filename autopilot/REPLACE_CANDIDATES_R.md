> **CORRECTED TABLE (28 Nov, W-PLAN-AS). Key = bar row | module | variant | params; 392 W-NEGBOOK rows + 4 nbtop files, 8,910 row-specific cells, 510,660 (cell, session, bracket) combinations; one position at a time, both sides, bare bracket, 1-s NQ. NET OF CHANCE (stage-2 qualifiers, non-live families; real vs mean of 5 same-day shuffled replicates with the identical filters): ASIA 137 vs 3.2 -> 134; NY AM 38 vs 4.2 -> 34; NY PM 23 vs 7.8 -> 15 (weak: 34% chance share); LONDON 5 vs 4.8 -> 0 (nothing above chance). Same-day null (>= 90% beaten on each side): Asia 88 of 137, London 2 of 5, NY AM 38 of 38, NY PM 13 of 23. The earlier REPLACE_CANDIDATES.md and REPL_EXACT_SCORES.md are for MERGED STREAMS (wrong key). All numbers here are bare-bracket quick-screen = UNTESTED IDEAS until the exact rows land (TL3_DX_*_REPL2_*, 588 rows queued 28 Nov).**

# SLOT REPLACEMENTS for the nine MOSTLY DRIFT books (W-PLAN-AS, order 1622Z item 2; first look Fri 27 Nov 17:30Z). Candidate set = every signal event of the NEGBOOK library extracted so far on server C (158 event files = 110 of 392 bar rows, 1,505 trigger cells x 4 sessions x both sides) + the live books' own cells; 15 brackets (10/60 ... 120/120, 60/30, 80/40, 90/30, 40/80, 120/60); bare bracket on the 1-s NQ path, ONE position at a time (both sides share the slot), fee 0.24 pt + 0.25 pt stop slip, exit at the bell.

SELECTION (written before the second stage): stage 1 on L6M only (May-Oct 2026): n >= 40 trades each side, both sides mean > 0, both sides beat the matched random-timing control (random entry every 3 min of every session day, same bracket, both sides; z >= 2 strict / 1.3 relaxed), L3M mean > 0. Stage 2 on the FULL history (selection used only L6M, so 2023-2025 are out-of-sample for the choice): n >= 80 each side, z >= 2 vs the control on each side over all months, each side mean > 0, each prior year mean > -1 pt, L6M and L3M > 0 and both sides > 0 in L6M, trigger family is not one of the 20 live books'. Luck charge: 87,585 (cell, session, bracket) combinations looked at in stage 1; 101 strict + 408 relaxed went to stage 2; 70 qualify (family duplicates inside that). The control draws are the analytic equivalent of the 200-draw check (control mean over ~100k random entries per cell of session x side x bracket x year; z on the real mean).

Columns: bracket | n long / short | mean pts per trade long / short (net of costs) | z vs random timing long / short | mean pts by year 2023 / 2024 / 2025 / 2026 | L6M, L3M mean pts | $ per trade at 1 lot | trades per week | max DD of the candidate alone at 1 lot (weekly) | worst week at 1 lot | win rate

## ASIA: emptied slot(s): MF4 AS-VWAPBAND (30/30, 3 lots)
qualified candidates (distinct trigger families, best bracket each): 72
| rank | trigger family (cell) | bracket | n L/S | mean pts L/S | z L/S | yearly mean pts 2023/24/25/26 | L6M | L3M | $/trade @1 lot | trades/wk | DD @1 lot | worst wk | win rate |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | trb_240 trig_levels_profile_nodes `break_native|{"k": 0.25, "n": 2}` | 120/120 | 492 / 442 | +8.1 / +7.2 | 2.4 / 2.4 | +1.1 / +0.1 / +5.1 / +17.9 | +22.2 | +14.3 | +154 | 5.1 | -21555 | -6769 | 54% |
| 2 | tick_800 trig_trend_heikin `run_native|{"len": 3, "width": 0.25}` | 90/90 | 711 / 657 | +7.5 / +5.2 | 3.0 / 2.7 | +2.1 / +6.1 / +0.8 / +12.3 | +16.9 | +5.6 | +128 | 7.4 | -20065 | -9347 | 54% |
| 3 | cusum_28 trig_trend_supertrend `native|{"len": 30, "width": 4.5}` | 120/60 | 661 / 588 | +7.9 / +4.6 | 2.8 / 2.1 | +1.9 / +0.0 / +8.0 / +9.9 | +16.7 | +11.5 | +127 | 6.8 | -24328 | -8086 | 46% |
| 4 | vrb_700 trig_trend_supertrend `native|{"len": 14, "width": 4.5}` | 90/90 | 574 / 513 | +8.6 / +5.1 | 3.2 / 2.4 | -0.0 / +1.3 / +11.4 / +10.2 | +16.2 | +6.6 | +139 | 5.9 | -29465 | -8654 | 54% |
| 5 | vol_500 trig_trend_supertrend `native|{"len": 20, "width": 4.5}` | 90/90 | 618 / 570 | +5.5 / +3.9 | 2.0 / 2.0 | +0.9 / +1.9 / +2.6 / +9.8 | +15.9 | +2.3 | +94 | 6.4 | -21623 | -6528 | 53% |
| 6 | tsf_5_400 trig_levels_mmove `retest|{"M": 3, "tol": 0.0}` | 60/60 | 477 / 478 | +7.2 / +6.2 | 3.7 / 3.8 | +1.8 / +3.6 / +5.0 / +12.6 | +15.3 | +15.8 | +134 | 5.2 | -6405 | -3113 | 57% |
| 7 | tick_800 trig_trend_supertrend `native|{"len": 30, "width": 3.0}` | 60/60 | 664 / 612 | +5.7 / +4.2 | 2.9 / 2.9 | +0.4 / +2.6 / +2.0 / +9.9 | +14.3 | +14.2 | +100 | 6.9 | -13873 | -5952 | 54% |
| 8 | vol_1100 trig_trend_ma_kama `price|{"len": 20, "width": 0.5}` | 60/60 | 573 / 526 | +8.2 / +5.8 | 4.0 / 3.5 | -0.5 / +6.9 / +4.3 / +11.9 | +13.8 | +14.8 | +142 | 6.0 | -9623 | -5359 | 56% |

## LONDON: emptied slot(s): MF2 LO-IMB (45/45, 4 lots, long-only)
qualified candidates (distinct trigger families, best bracket each): 2
| rank | trigger family (cell) | bracket | n L/S | mean pts L/S | z L/S | yearly mean pts 2023/24/25/26 | L6M | L3M | $/trade @1 lot | trades/wk | DD @1 lot | worst wk | win rate |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | vrb_700 trig_pullback_st `st|{"arm": 10, "ema": 30, "st_mult": 3.0}` | 45/45 | 961 / 969 | +4.2 / +1.7 | 3.0 / 2.7 | +2.6 / +2.4 / +0.5 / +5.6 | +7.4 | +11.8 | +59 | 10.5 | -11342 | -7658 | 53% |
| 2 | dol_2600 trig_structure_inside `outside|{"cf": 0.75, "filt": 20}` | 10/60 | 472 / 375 | +2.0 / +1.9 | 2.1 / 2.6 | +3.2 / +0.9 / +1.6 / +2.4 | +4.2 | +3.1 | +39 | 4.6 | -5866 | -3234 | 84% |

## NY AM: emptied slot(s): MF3 NY-SOPEN (120/120, 3); MF6 NY-BLOCK (90/30, 3, long-only); MF7 NY-BOLL (120/60, 1, long-only); MF8 NY-EMA (80/40, 1); MF9 NY-AVWAP (80/40, 2, long-only)
qualified candidates (distinct trigger families, best bracket each): 21
| rank | trigger family (cell) | bracket | n L/S | mean pts L/S | z L/S | yearly mean pts 2023/24/25/26 | L6M | L3M | $/trade @1 lot | trades/wk | DD @1 lot | worst wk | win rate |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | swing_atr_0.25 trig_levels_prior_day `false_break_native|{"M": 1, "k": 0.0}` | 120/120 | 499 / 516 | +13.7 / +14.8 | 3.1 / 4.2 | +8.5 / +4.8 / +21.0 / +18.0 | +25.8 | +14.9 | +286 | 5.5 | -38831 | -9644 | 58% |
| 2 | pnf_5 trig_levels_prior_day `false_break_native|{"M": 1, "k": 0.5}` | 120/120 | 486 / 512 | +12.3 / +11.3 | 2.7 / 3.3 | +6.4 / +0.8 / +19.5 / +15.7 | +24.4 | +13.5 | +236 | 5.4 | -40531 | -10904 | 57% |
| 3 | dchg_14 trig_levels_prior_day `false_break_native|{"M": 3, "k": 0.5}` | 120/120 | 498 / 509 | +11.5 / +12.8 | 2.6 / 3.6 | +8.0 / +3.8 / +19.6 / +13.6 | +23.5 | +15.4 | +243 | 5.5 | -42591 | -9989 | 57% |
| 4 | kagi_14 trig_levels_prior_day `false_break_native|{"M": 3, "k": 0.5}` | 120/120 | 498 / 509 | +11.5 / +12.8 | 2.6 / 3.6 | +8.0 / +3.8 / +19.6 / +13.6 | +23.5 | +15.4 | +243 | 5.5 | -42591 | -9989 | 57% |
| 5 | dchg_20 trig_levels_prior_day `false_break_native|{"M": 1, "k": 0.0}` | 120/120 | 501 / 512 | +12.4 / +13.7 | 2.8 / 3.9 | +9.0 / +3.6 / +19.5 / +16.3 | +23.4 | +6.8 | +262 | 5.5 | -39856 | -9569 | 57% |
| 6 | kagi_20 trig_levels_prior_day `false_break_native|{"M": 1, "k": 0.0}` | 120/120 | 501 / 512 | +12.4 / +13.7 | 2.8 / 3.9 | +9.0 / +3.6 / +19.5 / +16.3 | +23.4 | +6.8 | +262 | 5.5 | -39856 | -9569 | 57% |
| 7 | kagi_28 trig_levels_prior_day `false_break|{"M": 3, "k": 0.5}` | 120/120 | 495 / 521 | +12.1 / +11.4 | 2.6 / 3.4 | +8.9 / +4.9 / +16.6 / +13.8 | +18.1 | +4.3 | +235 | 5.5 | -26796 | -9279 | 56% |
| 8 | ha_micro_B080 trig_bands_atrchan `break_ema|{"atr": 14, "k": 1.5, "n": 10}` | 120/120 | 514 / 559 | +13.2 / +8.8 | 3.0 / 2.7 | +12.5 / +1.3 / +16.4 / +14.3 | +17.3 | +17.0 | +218 | 5.8 | -33396 | -11204 | 56% |

## NY PM: emptied slot(s): MF1 NP-ATRFADE (30/30, 3); MF4 NP-DIVFADE (60/60, 3)
qualified candidates (distinct trigger families, best bracket each): 18
| rank | trigger family (cell) | bracket | n L/S | mean pts L/S | z L/S | yearly mean pts 2023/24/25/26 | L6M | L3M | $/trade @1 lot | trades/wk | DD @1 lot | worst wk | win rate |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | time_m_1 trig_levels_trendline `reject_native|{"conf": "body", "tol": 1.0}` | 120/120 | 648 / 703 | +7.5 / +9.5 | 2.6 / 3.0 | +8.5 / +2.4 / +11.7 / +11.2 | +17.7 | +5.3 | +171 | 7.3 | -33386 | -7268 | 54% |
| 2 | renko_14 trig_levels_trendline `reject|{"conf": "close", "tol": 0.5}` | 120/120 | 571 / 620 | +6.4 / +6.7 | 2.2 / 2.1 | +13.2 / +2.9 / +4.4 / +8.4 | +17.6 | +15.5 | +132 | 6.5 | -27390 | -10474 | 54% |
| 3 | tm60 trig_levels_trendline `reject_native|{"conf": "body", "tol": 1.0}` | 120/120 | 648 / 707 | +8.5 / +9.7 | 2.9 / 3.0 | +8.1 / +2.0 / +15.7 / +9.3 | +15.4 | +5.1 | +182 | 7.3 | -26486 | -10133 | 54% |
| 4 | vol_1100 trig_book_cancel `canc_follow|{"L": 100, "z": 2.0}` | 90/90 | 1083 / 639 | +4.6 / +9.3 | 2.4 / 3.3 | +0.7 / +7.2 / +8.8 / +6.2 | +13.3 | +6.5 | +126 | 9.3 | -40361 | -8913 | 55% |
| 5 | dol_750 trig_levels_trendline `reject_native|{"conf": "body", "tol": 0.5}` | 90/90 | 805 / 826 | +4.8 / +6.8 | 2.2 / 2.9 | +7.0 / +9.4 / +2.2 / +5.8 | +11.1 | +7.9 | +116 | 8.8 | -27238 | -11261 | 53% |
| 6 | vfp_vol1000 trig_levels_trendline `reject|{"conf": "body", "tol": 1.0}` | 60/60 | 1073 / 1105 | +3.8 / +3.6 | 2.8 / 2.5 | +7.2 / +4.4 / +1.1 / +3.6 | +8.6 | +3.4 | +73 | 11.8 | -30392 | -10022 | 53% |
| 7 | vsess_30 trig_trend_heikin `flip_after_run_native|{"len": 8, "width": 0.0}` | 10/90 | 389 / 478 | +2.1 / +2.1 | 2.0 / 2.5 | -0.1 / +0.4 / +2.8 / +5.6 | +7.0 | +6.5 | +42 | 4.7 | -11448 | -3059 | 86% |
| 8 | nbtop_NYPM kal_rngor_B080 `trig_momentum_stoch|revert_native|{"len": 14, "lvl": 15}` | 30/30 | 468 / 379 | +3.4 / +3.5 | 3.0 / 2.7 | +5.5 / +3.1 / +3.0 / +3.1 | +6.0 | +3.5 | +69 | 4.7 | -5352 | -3242 | 56% |
