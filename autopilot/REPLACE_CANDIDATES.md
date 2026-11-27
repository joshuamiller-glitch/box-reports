# SLOT REPLACEMENTS for the nine MOSTLY DRIFT books (W-PLAN-AS, order 1622Z item 2; first look Fri 27 Nov 17:30Z). Candidate set = every signal event of the NEGBOOK library extracted so far on server C (158 event files = 110 of 392 bar rows, 1,505 trigger cells x 4 sessions x both sides) + the live books' own cells; 15 brackets (10/60 ... 120/120, 60/30, 80/40, 90/30, 40/80, 120/60); bare bracket on the 1-s NQ path, ONE position at a time (both sides share the slot), fee 0.24 pt + 0.25 pt stop slip, exit at the bell.

SELECTION (written before the second stage): stage 1 on L6M only (May-Oct 2026): n >= 40 trades each side, both sides mean > 0, both sides beat the matched random-timing control (random entry every 3 min of every session day, same bracket, both sides; z >= 2 strict / 1.3 relaxed), L3M mean > 0. Stage 2 on the FULL history (selection used only L6M, so 2023-2025 are out-of-sample for the choice): n >= 80 each side, z >= 2 vs the control on each side over all months, each side mean > 0, each prior year mean > -1 pt, L6M and L3M > 0 and both sides > 0 in L6M, trigger family is not one of the 20 live books'. Luck charge: 87,585 (cell, session, bracket) combinations looked at in stage 1; 101 strict + 408 relaxed went to stage 2; 70 qualify (family duplicates inside that). The control draws are the analytic equivalent of the 200-draw check (control mean over ~100k random entries per cell of session x side x bracket x year; z on the real mean).

Columns: bracket | n long / short | mean pts per trade long / short (net of costs) | z vs random timing long / short | mean pts by year 2023 / 2024 / 2025 / 2026 | L6M, L3M mean pts | $ per trade at 1 lot | trades per week | max DD of the candidate alone at 1 lot (weekly) | worst week at 1 lot | win rate

## ASIA: emptied slot(s): MF4 AS-VWAPBAND (30/30, 3 lots)
qualified candidates (distinct trigger families, best bracket each): 15
| rank | trigger family (cell) | bracket | n L/S | mean pts L/S | z L/S | yearly mean pts 2023/24/25/26 | L6M | L3M | $/trade @1 lot | trades/wk | DD @1 lot | worst wk | win rate |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | levels_mmove retest `{"M": 3, "tol": 0.0}` | 60/60 | 477 / 478 | +7.2 / +6.2 | 3.7 / 3.8 | +1.8 / +3.6 / +5.0 / +12.6 | +15.3 | +15.8 | +134 | 5.2 | -6405 | -3113 | 57% |
| 2 | trend_ma_kama price `{"len": 20, "width": 0.5}` | 60/60 | 573 / 526 | +8.2 / +5.8 | 4.0 / 3.5 | -0.5 / +6.9 / +4.3 / +11.9 | +13.8 | +14.8 | +142 | 6.0 | -9623 | -5359 | 56% |
| 3 | levels_fibr_dev false_break `{"M": 3, "k": 0.5}` | 60/60 | 873 / 827 | +5.6 / +2.5 | 3.3 / 2.3 | -0.4 / +2.9 / +5.0 / +5.6 | +9.0 | +10.1 | +83 | 9.2 | -27172 | -7844 | 54% |
| 4 | levels_opens retest `{"M": 6, "tol": 0.0}` | 15/90 | 354 / 346 | +2.5 / +2.2 | 2.1 / 2.4 | +0.2 / -0.8 / +1.3 / +5.4 | +7.0 | +9.8 | +47 | 3.8 | -10428 | -2955 | 78% |
| 5 | momentum_stoch zone_break `{"len": 21, "lvl": 90}` | 40/80 | 984 / 830 | +3.9 / +2.4 | 3.1 / 2.5 | +1.4 / +2.7 / +0.8 / +5.8 | +6.0 | +6.3 | +64 | 9.8 | -13534 | -6643 | 61% |
| 6 | momentum_mvote v3of5 `{"scale": 1.0, "thr": 1.0}` | 45/45 | 1804 / 1843 | +3.8 / +3.2 | 4.3 / 4.8 | -0.1 / +2.4 / +2.6 / +5.7 | +5.6 | +4.8 | +70 | 19.8 | -20047 | -6853 | 54% |
| 7 | bands_envelope break_sma `{"clk": 20, "k": 1.5}` | 10/90 | 543 / 465 | +1.9 / +1.2 | 2.8 / 2.2 | +1.9 / +0.5 / +0.4 / +3.6 | +5.5 | +5.2 | +31 | 5.5 | -7111 | -5094 | 81% |
| 8 | trend_ma_ema price `{"len": 100, "width": 0.5}` | 60/60 | 12286 / 11453 | +4.4 / +1.3 | 9.3 / 5.9 | +1.6 / +2.5 / +2.4 / +3.9 | +5.3 | +6.2 | +58 | 128.6 | -226343 | -94378 | 52% |

## LONDON: emptied slot(s): MF2 LO-IMB (45/45, 4 lots, long-only)
qualified candidates (distinct trigger families, best bracket each): 1
| rank | trigger family (cell) | bracket | n L/S | mean pts L/S | z L/S | yearly mean pts 2023/24/25/26 | L6M | L3M | $/trade @1 lot | trades/wk | DD @1 lot | worst wk | win rate |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | structure_inside outside `{"cf": 0.75, "filt": 20}` | 10/60 | 472 / 375 | +2.0 / +1.9 | 2.1 / 2.6 | +3.2 / +0.9 / +1.6 / +2.4 | +4.2 | +3.1 | +39 | 4.6 | -5866 | -3234 | 84% |

## NY AM: emptied slot(s): MF3 NY-SOPEN (120/120, 3); MF6 NY-BLOCK (90/30, 3, long-only); MF7 NY-BOLL (120/60, 1, long-only); MF8 NY-EMA (80/40, 1); MF9 NY-AVWAP (80/40, 2, long-only)
qualified candidates (distinct trigger families, best bracket each): 4
| rank | trigger family (cell) | bracket | n L/S | mean pts L/S | z L/S | yearly mean pts 2023/24/25/26 | L6M | L3M | $/trade @1 lot | trades/wk | DD @1 lot | worst wk | win rate |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | levels_prior_day false_break `{"M": 1, "k": 0.0}` | 120/120 | 1501 / 1540 | +12.9 / +14.1 | 5.0 / 7.0 | +8.8 / +4.0 / +20.0 / +16.9 | +24.2 | +9.5 | +270 | 16.5 | -118544 | -28782 | 57% |
| 2 | levels_fib60 retest `{"M": 6, "tol": 0.0}` | 120/120 | 514 / 579 | +10.7 / +6.3 | 2.3 / 2.2 | +16.1 / +12.4 / +5.2 / +4.2 | +16.5 | +25.8 | +168 | 5.9 | -64864 | -14498 | 55% |
| 3 | levels_piv_wf retest `{"M": 3, "tol": 0.5}` | 120/120 | 855 / 931 | +8.5 / +7.6 | 2.4 / 3.5 | +8.2 / +7.2 / +10.1 / +6.8 | +12.3 | +2.8 | +161 | 9.7 | -28367 | -20278 | 55% |
| 4 | tape_vpin fade `{"N": 600, "thr": 0.12}` | 60/60 | 347 / 383 | +9.2 / +2.9 | 3.6 / 2.1 | +9.5 / +1.2 / +0.4 / +12.2 | +12.0 | +8.6 | +118 | 4.0 | -12818 | -3889 | 56% |

## NY PM: emptied slot(s): MF1 NP-ATRFADE (30/30, 3); MF4 NP-DIVFADE (60/60, 3)
qualified candidates (distinct trigger families, best bracket each): 6
| rank | trigger family (cell) | bracket | n L/S | mean pts L/S | z L/S | yearly mean pts 2023/24/25/26 | L6M | L3M | $/trade @1 lot | trades/wk | DD @1 lot | worst wk | win rate |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | book_cancel canc_follow `{"L": 100, "z": 2.0}` | 90/90 | 1083 / 639 | +4.6 / +9.3 | 2.4 / 3.3 | +0.7 / +7.2 / +8.8 / +6.2 | +13.3 | +6.5 | +126 | 9.3 | -40361 | -8913 | 55% |
| 2 | levels_trendline reject `{"conf": "body", "tol": 1.0}` | 90/90 | 2493 / 2620 | +3.8 / +4.4 | 3.0 / 3.5 | +7.6 / +1.2 / +3.1 / +5.7 | +8.4 | +9.0 | +81 | 27.7 | -67137 | -21574 | 52% |
| 3 | levels_trendline break `{"k": 0.5, "n": 2}` | 60/60 | 6899 / 6851 | +1.6 / +1.6 | 3.6 / 3.2 | +1.2 / +3.9 / +0.7 / +0.6 | +2.8 | +4.4 | +32 | 74.5 | -175536 | -54857 | 52% |
| 4 | trend_psar flip `{"af0": 0.02, "max": 0.2, "step": 0.03}` | 60/60 | 43266 / 43155 | +0.3 / +0.4 | 3.6 / 3.3 | +1.6 / -0.9 / +0.4 / +0.7 | +1.5 | +1.7 | +7 | 468.2 | -692119 | -170919 | 50% |
| 5 | levels_channel break `{"k": 0.0, "n": 1}` | 60/30 | 15289 / 15026 | +0.5 / +0.2 | 4.7 / 2.9 | -0.2 / +1.1 / +0.6 / -0.2 | +1.3 | +2.4 | +7 | 164.2 | -186503 | -55505 | 37% |
| 6 | bands_envelope break_ema `{"n": 20, "pct": 0.05}` | 15/60 | 12324 / 11697 | +0.3 / +0.3 | 2.8 / 2.4 | +0.8 / +0.3 / +0.2 / +0.2 | +0.8 | +1.0 | +6 | 130.1 | -55603 | -24884 | 78% |
