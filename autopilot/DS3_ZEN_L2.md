# DS3_ZEN_L2 - T-ZEN family L2: the order book at the level, B1 triggers/filters, B3 day label, B4 walls, B2 execution economics (D3ZL2, 2026-10-28)

Research only (no live / execution-server / chart change, no replay launched). Screen on the mapped conservative basis (1-min OHLC fills, $4.84 RT, 10-lot unit = $200/pt; pts/trade next to dollars). PRE 2024-02-01..2025-06-30 for the screen; HOLD 2025-07-01..2026-02-06 and X 2023-04-01..2024-01-31 each read ONCE for 33 selected items. UNTOUCHED not read.

## 0. Verdict

**The book only filters.** At the model's 15-pt stop (E1-E5, market entry on the hold candle) a book-state trigger or filter adds +0.00 pts/trade over the same touches without the book (mean paired change of the 66 hold-candle filter items with n >= 100: +0.00, median +0.01; all 131 E items with n >= 100 incl. the no-hold 'alone' variants: +0.07), the best single one is +1.33 pts/trade (E2 + divergence, n = 174, paired CI lower -1.13, MDE80 3.7, white-reality-check adjusted p 1.00) and in the one HOLD look it is -2.26. Against random-in-regime WITH THE SAME BOOK STATE at the random minute: 4 of 131 E items have CI lower > 0 (3.3 expected by chance at 2.5%), none also beats random direction (G2), none has a positive mean net at 1x and 2x cost (G3), none reaches its MDE80 (G5, 0 of 144 B1 items with n >= 100), and the best-of-N reality check over N = 495 gives p = 0.096 for the best item (an inherited winner-curse base cell), 0 items <= 0.05. HOLD: 2 of 30 selected items have CI lower > 0 (E1 + ABSQ95 +4.45 [0.42], E3 + IMB5_15 +4.18 [0.24]); both have a PRE CI that includes 0 (-1.78 / -1.61), reality-check p 1.00, and one is negative in X. Labels: 0 CANDIDATE, 0 LEAD; G10 (direct replay) was not run and none is justified.
- The 15-pt cells lose money before and after the book: E1-E5 mapped mean net -1.22 to -1.76 pts/trade (PRE+HOLD, -$245 to -$351 per 10-lot trade), 41-44% win vs 46-48% break-even; realised stop 16.0 / 16.2 / 16.5 pt at 2 / 5 / 10 lots; edge after entry cost and measured stop slippage -2.1 to -2.7 pts at 2 lots and -2.3 to -2.9 at 10 lots: the lot level at which slippage alone exceeds the per-trade edge does not exist (the edge is negative before any slippage).
- B3 (opening-hour book as a 10:00 label): no E cell separates on thick vs thin book days (15 contrasts, |difference| <= 1.5 pts, every CI includes 0, MDE80 1.1-2.7); same verdict as Z6. B4 (walls 20-40 pt away) cannot be tested: mbp-10 shows 10 levels = 2.25 pt.
- Absorption X = 200 / 500 / 1000 contracts at the level practically never occurs in a minute (13 / 0 / 0 times in 86,252 PRE candidate minutes), so absorption is a count, not a verdict; the scale-adjusted variants (p95 / p99 of the PRE distribution, 51 / 81 contracts) are also null.

## 1. Counts block (descriptive, before any score)

Data on disk and used: Databento mbp-10 NQ derived tables, monthly: tape (per trade, with pre-trade best bid/ask and queue), 1 s book (10 levels, cancels, depletions), 1 min book. PRE months 2024-02..2025-06: 17 of 17 present; of 86,385 primary-window (10:00-14:00 ET) 1-min bars all 86,385 have tape and book (coverage 100%; the 13 PRE days with 180 instead of 240 bars are half days). HOLD 2025-07..2026-02-06 and X 2023-04..2024-01 present and complete. No order-level MBO: queue position is a FIFO model. Front contract only (the tape table carries one instrument per day). **mbp-10 depth covers 10 levels = median 9 ticks = 2.25 pt**, which is why B4 is not observable.

Features (l2_feat.py, per closed 1-min bar and side, window = the 60 s before t_sig, trades with ts < t_sig; unit test t_leak: 40 sampled bars, features unchanged when every tape/book record at or after t_sig is deleted, 0 mismatches). Trigger fire counts in PRE (CSV out/zen/l2/desc_trigger_counts_PRE.csv; 'hold' = hold candle touch set, 'alone' = touch of the line without the close condition):

| set | n | ABS200 | ABS500 | ABS1000 | ABSQ95 | ABSQ99 | REF2 | REF3 | IMB5_15 | IMB5_20 | IMB10_15 | IMB10_20 | IMB5_CH | IMB10_CH | DF5 | DF15 | DF30 | DIV | SWR | BIG50 | BIG100 | NOPULL | PULLINV |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| pool_R1 | 86252 | 13 | 0 | 0 | 3069 | 498 | 38059 | 22468 | 6758 | 1294 | 4975 | 709 | 13434 | 10940 | 55981 | 58588 | 59060 | 2443 | 135 | 13 | 1 | 77757 | 8495 |
| pool_R3 | 75075 | 12 | 0 | 0 | 2721 | 442 | 33423 | 19777 | 5759 | 1107 | 4278 | 607 | 11637 | 9527 | 48880 | 51115 | 51496 | 2181 | 125 | 11 | 1 | 67962 | 7113 |
| pool_R8 | 65408 | 8 | 0 | 0 | 2286 | 359 | 29146 | 17220 | 4902 | 932 | 3567 | 477 | 10063 | 8190 | 42258 | 44250 | 44613 | 1655 | 106 | 5 | 1 | 59349 | 6059 |
| E1_hold | 8019 | 1 | 0 | 0 | 302 | 55 | 3548 | 2114 | 568 | 95 | 380 | 41 | 1136 | 865 | 5222 | 5511 | 5631 | 281 | 16 | 2 | 0 | 7076 | 943 |
| E1_alone | 7880 | 2 | 0 | 0 | 344 | 65 | 3672 | 2221 | 606 | 102 | 455 | 54 | 1166 | 944 | 5299 | 5521 | 5600 | 370 | 13 | 2 | 0 | 7121 | 759 |
| E2_hold | 5446 | 1 | 0 | 0 | 197 | 31 | 2315 | 1337 | 383 | 60 | 227 | 26 | 769 | 567 | 3611 | 3837 | 3940 | 199 | 12 | 1 | 0 | 4776 | 670 |
| E2_alone | 5307 | 2 | 0 | 0 | 239 | 41 | 2439 | 1444 | 421 | 67 | 302 | 39 | 799 | 646 | 3688 | 3847 | 3909 | 288 | 9 | 1 | 0 | 4821 | 486 |
| E3_hold | 3522 | 0 | 0 | 0 | 127 | 22 | 1580 | 921 | 208 | 34 | 144 | 15 | 468 | 329 | 2323 | 2447 | 2491 | 156 | 7 | 1 | 0 | 3141 | 381 |
| E3_alone | 3403 | 0 | 0 | 0 | 143 | 27 | 1579 | 951 | 214 | 35 | 156 | 16 | 470 | 347 | 2293 | 2387 | 2416 | 181 | 6 | 1 | 0 | 3084 | 319 |
| E4_hold | 7354 | 1 | 0 | 0 | 273 | 44 | 3217 | 1911 | 531 | 96 | 351 | 46 | 1045 | 778 | 4889 | 5124 | 5247 | 243 | 4 | 1 | 0 | 6529 | 825 |
| E4_alone | 7221 | 3 | 0 | 0 | 311 | 54 | 3298 | 2014 | 575 | 103 | 412 | 65 | 1104 | 886 | 4945 | 5116 | 5186 | 327 | 5 | 3 | 0 | 6553 | 668 |
| E5_hold | 13793 | 2 | 0 | 0 | 444 | 56 | 6017 | 3472 | 889 | 153 | 609 | 76 | 1950 | 1479 | 8953 | 9486 | 9662 | 423 | 24 | 2 | 0 | 12184 | 1609 |
| E5_alone | 14051 | 2 | 0 | 0 | 524 | 71 | 6404 | 3805 | 979 | 191 | 778 | 103 | 2094 | 1679 | 9459 | 9880 | 9969 | 608 | 22 | 3 | 0 | 12737 | 1314 |

Reading: absorption X >= 200 fires 13 times in 86k minutes and X = 500 / 1000 never; REF2 / DF fire on 44% / 65-69% of minutes (weak filters by construction); IMB 2.0 on 1.5% / 0.8% (5 / 10 levels); large prints >= 50 contracts on 13 minutes, >= 100 once; sweep-and-reclaim 0.16%; pull (top decile of cancelled / (hit + 10)) 9.9%.

Control cells (no book), E1-E5 with the model bracket (stop 15 pt from the entry, nearest confirmed 1-min swing as target 5..60 pt else 20 pt fixed, flat 14:00), PRE, sequenced:

| cell | mode | n | mean net1 | random-in-regime | effect [CI lo] | MDE80 | win vs BE | G1 |
|---|---|---|---|---|---|---|---|---|
| E1 | ctrl_hold | 2466 | -1.66 | -1.58 | -0.08 [-0.67] | 0.9 | 0.414 vs 0.466 | False |
| E1 | ctrl_alone | 2401 | -1.59 | -1.58 | -0.01 [-0.64] | 0.8 | 0.397 vs 0.444 | False |
| E2 | ctrl_hold | 2107 | -1.44 | -1.58 | +0.14 [-0.53] | 1.0 | 0.420 vs 0.464 | False |
| E2 | ctrl_alone | 2021 | -1.24 | -1.58 | +0.34 [-0.36] | 1.0 | 0.403 vs 0.439 | False |
| E3 | ctrl_hold | 1115 | -1.18 | -1.53 | +0.35 [-0.51] | 1.2 | 0.427 vs 0.464 | False |
| E3 | ctrl_alone | 1060 | -0.84 | -1.53 | +0.69 [-0.16] | 1.2 | 0.432 vs 0.458 | False |
| E4 | ctrl_hold | 2353 | -1.54 | -1.58 | +0.04 [-0.65] | 1.0 | 0.413 vs 0.460 | False |
| E4 | ctrl_alone | 2406 | -1.70 | -1.58 | -0.12 [-0.79] | 1.0 | 0.389 vs 0.438 | False |
| E5 | ctrl_hold | 3986 | -1.41 | -1.53 | +0.12 [-0.32] | 0.7 | 0.434 vs 0.480 | False |
| E5 | ctrl_alone | 4104 | -1.42 | -1.53 | +0.11 [-0.30] | 0.6 | 0.410 vs 0.453 | False |
| F1|R8|d40|a30|L2e40_t5|T0at|955|R1_60 | ctrl_filter | 63 | +8.64 | +2.64 | +6.01 [-5.75] | 16.6 | 0.587 vs 0.504 | False |
| B:kagi_32|E3|SMMA_377_close|x5|c60|955 | ctrl_filter | 191 | +9.01 | -1.74 | +10.76 [+2.23] | 11.7 | 0.592 vs 0.513 | True |
| B:renko_38|E2|TMA_377_close|ctl|c60|955 | ctrl_filter | 167 | +8.74 | -1.89 | +10.63 [-0.13] | 16.9 | 0.587 vs 0.512 | False |
| S3:E2|cap60|prev_day_extreme+0t|swing_5m_k2_equal_highs | ctrl_filter | 31 | +0.35 | -5.82 | +6.17 [-0.90] | 10.9 | 0.677 vs 0.667 | False |
| S3:E2|cap15|swing_15m_k3_last+0t|pivot_R1 | ctrl_filter | 50 | +0.96 | +1.07 | -0.11 [-4.51] | 7.4 | 0.220 vs 0.194 | False |
| S3:E2|cap20|session_extreme+5t|pivot_R1 | ctrl_filter | 36 | +1.87 | +2.33 | -0.47 [-10.02] | 14.6 | 0.194 vs 0.166 | False |
| S3:E2|atr1.5|session_extreme+2t|session_extreme | ctrl_filter | 71 | +0.28 | -2.63 | +2.91 [-5.76] | 13.0 | 0.183 vs 0.180 | False |
| S3:E5|atr1.5|prev_hour_extreme+2t|swing_4h_nearest_high | ctrl_filter | 73 | +3.33 | -0.31 | +3.64 [-2.83] | 10.9 | 0.329 vs 0.249 | False |
| S3:E5|cap30|session_extreme+5t|swing_5m_k3_lower_high | ctrl_filter | 27 | -0.15 | -4.38 | +4.23 [-3.26] | 13.2 | 0.370 vs 0.377 | False |
| S3:E4|cap60|prev_day_extreme+0t|swing_4h_nearest_high | ctrl_filter | 151 | +0.95 | -3.02 | +3.96 [-1.78] | 9.5 | 0.325 vs 0.309 | False |

These reproduce the F3 / STRUCT result: the 15-pt model bracket on the EMA / VWAP touch is a random-in-regime entry (effect -0.08..+0.69, every CI includes 0) and loses -0.8 to -1.7 pts/trade.

## 2. Grid enumeration and screened N

Prereg ZEN_L2_B1 sha256 d08d5e70233882b770cd4a434f0cea44aa3e1db5317882eff16014205db56c52 (hashed and logged in DECISIONS.md before any cell was scored); table of every cell prereg/ZEN_L2_B1_cells.csv sha256 93d4e2f85492e3bd6f65e06892e2fe626719d72ed12e2c4838d699e88a8167d2. PREHOLD (33 items) sha256 9c9e0db26eef5a9fc0e50aa39b510da0aeba9daceaf8605fd7f57b87a59362e8, looks D3ZL2_HOLD and D3ZL2_X logged before the HOLD / X features were built.
- Base cells 15 = E1-E5 + the top 10 PRE cells pooled from the families (rule in the prereg: n >= 100 PRE in the family tables, ranked by effect vs random-in-regime, duplicates by buffer/flat/T0 removed): F1 R8|d40|a30|L2e40_t5|T0at|955|R1_60; BARS kagi_32 E3 SMMA_377 x5 c60 955; BARS renko_38 E2 TMA_377 ctl c60 955; S3 E2 cap60 prev_day_extreme / swing_5m equal highs; S3 E2 cap15 swing_15m_k3_last / pivot_R1; S3 E2 cap20 session_extreme+5t / pivot_R1; S3 E2 atr1.5 session_extreme+2t / session_extreme; S3 E5 atr1.5 prev_hour_extreme+2t / swing_4h_nearest_high; S3 E5 cap30 session_extreme+5t / swing_5m_k3_lower_high; S3 E4 cap60 prev_day_extreme / swing_4h_nearest_high.
- 22 triggers = plan 20 (ABS 200 / 500 / 1000, REF 2 / 3, IMB 5 / 10 levels x 1.5 / 2.0 + CHANGE x2, delta flip 5 / 15 / 30 s, divergence, sweep-reclaim, large print 50 / 100, pull as filter NOPULL and as inverse PULLINV) + 2 scale-adjusted absorption variants ABSQ95 / ABSQ99 (added in the prereg after the counts showed X >= 200 almost never fires; distribution-only thresholds).
- B1 alone 22 x 5 E = 110; B1 with hold candle (= filter on E) 22 x 5 = 110; filters on the top 10: 21 x 10 = 210 (PULLINV needs an inverse bracket the structural / bar / limit cells do not define: 10 skipped and counted); controls 20; B3 3 x 15 = 45; B4 2 x 15 = 30 NOT BUILT (depth). **Scored N = 495 (430 B1 + 20 controls + 45 B3); skipped and counted 40.** Program N 291,130 (plan). Of the 430 B1 rows: 280 have n >= 5 and a pool (150 do not: triggers that never fire), 144 have sequenced PRE n >= 100 (E 131, BARS 8, S3 5, F1 0), 64 have n 30-99 (a count, not a verdict), 72 n < 30.

## 3. Top 10 items by effect vs random-in-regime WITH THE SAME BOOK REQUIREMENT (PRE), regardless of verdict

Effect = real mean - exact expectation over all random regime minutes where the trigger is true (same bracket logic at that minute); 'draw rank' = rank among 100 explicit shared-seed draws; 'failed gates' G1 includes the draw rank >= 0.95; G10 never run. The first 8 rows are the base cell's own PRE winner-curse effect carried by a delta-flip / no-pull filter that fires on 65-90% of minutes (the paired change vs the unfiltered base cell is -4.5 to +3.5, CI lower < 0 in 9 of the 10 rows); rows 9-10 are a 4-hour-swing target cell whose HOLD CI is [-8, 9]:

| rank | cell | mode | trigger | PRE n | win vs BE | tr/wk | PRE effect [CI lo] | MDE80 | draw rank | HOLD n eff [CI lo] | X n eff | failed gates (by how much) | fwd wk 80% |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | B:renko_38|E2|TMA_377_close|ctl|c60|955 | filter | DF15 | 123 | 0.618 vs 0.515 | 1.64 | +14.32 [+4.43] | 16.0 | 0.98 | 45 +4.20 [-12.55] | 22 -2.70 | G5,G6,G7,G8,G9,G10 | 93 |
| 2 | B:renko_38|E2|TMA_377_close|ctl|c60|955 | filter | DF30 | 129 | 0.612 vs 0.515 | 1.72 | +14.04 [+4.11] | 15.3 | 0.98 | 45 +4.19 [-12.42] | 21 -3.08 | G5,G6,G7,G8,G9,G10 | 89 |
| 3 | B:renko_38|E2|TMA_377_close|ctl|c60|955 | filter | DF5 | 120 | 0.608 vs 0.516 | 1.60 | +12.91 [+2.25] | 16.4 | 0.97 | 43 +4.47 [-13.07] | 20 -4.04 | G5,G6,G7,G8,G9,G10 | 120 |
| 4 | B:renko_38|E2|TMA_377_close|ctl|c60|955 | filter | NOPULL | 147 | 0.605 vs 0.511 | 1.96 | +12.82 [+1.66] | 16.4 | 0.94 | 43 +1.84 [-13.39] | 22 -3.53 | G1,G5,G6,G7,G8,G9,G10 | 122 |
| 5 | B:kagi_32|E3|SMMA_377_close|x5|c60|955 | filter | DF15 | 164 | 0.610 vs 0.512 | 2.19 | +12.49 [+3.22] | 12.7 | 1.00 | 48 +3.29 [-12.80] | 35 +2.51 | G5,G6,G8,G9,G10 | 77 |
| 6 | B:kagi_32|E3|SMMA_377_close|x5|c60|955 | filter | DF5 | 154 | 0.604 vs 0.512 | 2.05 | +12.31 [+1.74] | 14.5 | 1.00 | 45 +5.50 [-11.94] | 34 +4.19 | G5,G6,G8,G10 | 104 |
| 7 | B:kagi_32|E3|SMMA_377_close|x5|c60|955 | filter | DF30 | 167 | 0.593 vs 0.513 | 2.23 | +10.98 [+0.88] | 13.6 | 1.00 | 48 +3.83 [-12.44] | 36 +4.04 | G5,G6,G8,G10 | 115 |
| 8 | B:kagi_32|E3|SMMA_377_close|x5|c60|955 | filter | NOPULL | 176 | 0.580 vs 0.513 | 2.35 | +9.21 [-0.07] | 12.8 | 0.95 | 34 +4.23 [-14.35] | 43 +8.42 | G1,G5,G6,G8,G9,G10 | 144 |
| 9 | S3:E4|cap60|prev_day_extreme+0t|swing_4h_nearest_high | filter | REF2 | 102 | 0.382 vs 0.326 | 1.36 | +5.98 [-1.81] | 12.5 | 1.00 | 19 +4.66 [-8.35] | 75 -1.10 | G1,G2,G5,G6,G7,G8,G10 | 330 |
| 10 | S3:E4|cap60|prev_day_extreme+0t|swing_4h_nearest_high | filter | NOPULL | 145 | 0.324 vs 0.301 | 1.93 | +5.07 [-0.91] | 9.9 | 0.97 | 27 +2.42 [-8.87] | 91 +0.88 | G1,G2,G3,G5,G6,G8,G9,G10 | 286 |


The same table restricted to the E1-E5 cells (the 15-pt stop question; row numbers are positions in the top-30 list):

| rank | cell | mode | trigger | PRE n | win vs BE | tr/wk | PRE effect [CI lo] | MDE80 | draw rank | HOLD n eff [CI lo] | X n eff | failed gates (by how much) | fwd wk 80% |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 14 | E2 | alone | DIV | 251 | 0.402 vs 0.398 | 3.35 | +2.10 [-0.02] | 3.0 | 0.99 | 100 -1.67 [-4.34] | 142 +0.84 | G1,G2,G3,G5,G6,G8,G9,G10 | 154 |
| 15 | E4 | alone | DIV | 294 | 0.412 vs 0.410 | 3.92 | +1.99 [+0.07] | 2.9 | 0.99 | 105 +0.82 [-2.98] | 134 +1.39 | G2,G3,G5,G6,G8,G9,G10 | 154 |
| 16 | E2 | hold | DIV | 174 | 0.397 vs 0.404 | 2.32 | +1.68 [-0.83] | 3.7 | 0.97 | 80 -2.26 [-5.16] | 96 +0.77 | G1,G2,G3,G4,G5,G6,G8,G9,G10 | 369 |
| 17 | E3 | hold | DIV | 128 | 0.398 vs 0.417 | 1.71 | +1.59 [-1.65] | 4.8 | 0.89 | 55 -1.94 [-4.88] | 94 -0.43 | G1,G2,G3,G4,G5,G6,G7,G8,G9,G10 | 679 |
| 18 | E5 | alone | IMB5_20 | 180 | 0.494 vs 0.490 | 2.40 | +1.50 [-0.66] | 3.1 | 0.90 | 60 +3.18 [-0.65] | 125 -0.34 | G1,G2,G3,G5,G6,G7,G8,G9,G10 | 321 |
| 19 | E1 | alone | DIV | 315 | 0.387 vs 0.408 | 4.20 | +1.19 [-0.76] | 2.9 | 0.95 | 122 -1.31 [-3.59] | 198 +0.96 | G1,G2,G3,G4,G5,G6,G8,G9,G10 | 441 |
| 20 | E3 | alone | DF5 | 876 | 0.441 vs 0.458 | 11.68 | +0.99 [+0.10] | 1.3 | 1.00 | 309 +0.87 [-0.56] | 512 +0.82 | G2,G3,G4,G5,G6,G8,G9,G10 | 133 |
| 21 | E3 | alone | DIV | 149 | 0.383 vs 0.418 | 1.99 | +0.98 [-1.93] | 4.2 | 0.78 | 59 -2.79 [-5.30] | 101 -0.13 | G1,G2,G3,G4,G5,G6,G7,G8,G9,G10 | 1362 |
| 22 | E1 | hold | DIV | 240 | 0.388 vs 0.419 | 3.20 | +0.84 [-1.36] | 3.3 | 0.88 | 104 -1.44 [-3.86] | 152 +1.00 | G1,G2,G3,G4,G5,G6,G8,G9,G10 | 1125 |
| 23 | E3 | hold | DF5 | 916 | 0.442 vs 0.465 | 12.21 | +0.84 [+0.00] | 1.2 | 0.99 | 318 +0.70 [-0.91] | 520 +0.86 | G2,G3,G4,G5,G6,G8,G9,G10 | 166 |

HOLD (one look): the 30 selected: sign agrees 23 of 30, G6 (effect > 0 and CI lower > 0) 2 of 30 (expected 0.75 by chance), the 8 BARS rows keep +1.8 to +5.5 with CI [-12, +27] (74% shrinkage as in the BARS report); X >= 0 in 17 of 30; reality check p <= 0.05 for none (adjusted p 0.33-1.00); G9 not satisfied by any item that passes G6. 0 items pass G1-G9.

By window, year and side for the 10 items of the first table (PRE + HOLD pooled, descriptive; entries exist only 10:00-14:00; random-in-regime column = same trigger at random minutes; no HOLD-only selection):

| rank | item | W10 / W11 / W12 / W13 (n, mean, random-in-regime mean) | 2024 / 2025 / 2026 | long / short |
|---|---|---|---|---|
| 1 | B:renko_38|E2|TMA_377_close|ctl|c60|955 | <bound method Series.mode of cell           B:renko_38|E2|TMA_377_close|ctl|c60|955
kind                                                 BARS
mode                                               filter
trigger                                              DF15
win                                              0.617886
n_touch                                               235
n_trig                                                160
n                                                     123
pool_n                                              34196
bracket                                               c60
ok                                                   True
mean1                                           11.982017
mean2                                            9.451839
be                                               0.515378
pool_mean                                       -2.341917
effect                                          14.323934
se                                               5.697642
ci_lo                                            4.427231
ci_hi                                           26.237156
mde80                                           15.953397
t                                                2.514011
trades_wk                                            1.64
usd_trade                                     2396.403385
dir_effect                                      13.739871
dir_lo                                           2.851815
dir_n                                               123.0
G1                                                   True
G2                                                   True
G3                                                   True
G4                                                   True
G5                                                  False
rc_p                                                0.487
paired                                             3.5022
paired_lo                                       -0.732284
paired_hi                                        7.553742
paired_mde                                       5.830427
prior_mde                                       12.953576
rank_draw                                            0.98
draw_mean                                       -1.316613
effect_draw                                      13.29863
Name: 0, dtype: object> | DF15 (rows 1-10 of the top-30 list) | W10 74, +9.2, -1.0 ; W11 39, +0.3, -1.8 ; W12 29, +18.1, +0.5 ; W13 26, +20.1, -2.2 | 2024 54, +20.6, -0.2 ; 2025 108, +3.8, -1.6 ; 2026 6, +36.2, -1.2 | long 54, +7.2, -2.7 ; short 114, +11.9, +0.0 |
| 2 | B:renko_38|E2|TMA_377_close|ctl|c60|955 | <bound method Series.mode of cell           B:renko_38|E2|TMA_377_close|ctl|c60|955
kind                                                 BARS
mode                                               filter
trigger                                              DF30
win                                              0.612403
n_touch                                               235
n_trig                                                164
n                                                     129
pool_n                                              34467
bracket                                               c60
ok                                                   True
mean1                                           11.336292
mean2                                            8.812119
be                                               0.515413
pool_mean                                       -2.704753
effect                                          14.041045
se                                               5.475689
ci_lo                                            4.106261
ci_hi                                            25.19118
mde80                                            15.33193
t                                                2.564252
trades_wk                                            1.72
usd_trade                                     2267.258447
dir_effect                                      13.111198
dir_lo                                           2.370797
dir_n                                               129.0
G1                                                   True
G2                                                   True
G3                                                   True
G4                                                   True
G5                                                  False
rc_p                                                0.447
paired                                           3.875951
paired_lo                                        0.673957
paired_hi                                        7.100017
paired_mde                                       4.737077
prior_mde                                       12.648743
rank_draw                                            0.98
draw_mean                                       -1.782529
effect_draw                                     13.118821
Name: 1, dtype: object> | DF30 (rows 1-10 of the top-30 list) | W10 76, +8.9, -1.2 ; W11 43, -2.6, -1.9 ; W12 29, +18.1, +0.0 ; W13 26, +24.7, -2.8 | 2024 55, +21.3, -0.3 ; 2025 113, +3.0, -2.0 ; 2026 6, +36.2, -0.8 | long 57, +7.7, -3.1 ; short 117, +11.0, -0.2 |
| 3 | B:renko_38|E2|TMA_377_close|ctl|c60|955 | <bound method Series.mode of cell           B:renko_38|E2|TMA_377_close|ctl|c60|955
kind                                                 BARS
mode                                               filter
trigger                                               DF5
win                                              0.608333
n_touch                                               235
n_trig                                                151
n                                                     120
pool_n                                              32730
bracket                                               c60
ok                                                   True
mean1                                           10.803547
mean2                                            8.244594
be                                               0.515827
pool_mean                                       -2.102875
effect                                          12.906422
se                                               5.842604
ci_lo                                            2.249899
ci_hi                                           25.146175
mde80                                           16.359291
t                                                2.209019
trades_wk                                             1.6
usd_trade                                     2160.709369
dir_effect                                      12.602503
dir_lo                                           1.307351
dir_n                                               120.0
G1                                                   True
G2                                                   True
G3                                                   True
G4                                                   True
G5                                                  False
rc_p                                                0.723
paired                                           0.934681
paired_lo                                        -3.79692
paired_hi                                        4.985251
paired_mde                                        6.22353
prior_mde                                       13.114496
rank_draw                                            0.97
draw_mean                                       -1.587402
effect_draw                                     12.390949
Name: 2, dtype: object> | DF5 (rows 1-10 of the top-30 list) | W10 72, +9.4, -0.5 ; W11 40, +1.7, -1.5 ; W12 26, +13.6, +0.5 ; W13 25, +18.7, -2.7 | 2024 49, +19.2, -0.4 ; 2025 108, +3.8, -1.2 ; 2026 6, +36.2, -1.4 | long 54, +7.2, -2.7 ; short 109, +10.8, +0.3 |
| 4 | B:renko_38|E2|TMA_377_close|ctl|c60|955 | <bound method Series.mode of cell           B:renko_38|E2|TMA_377_close|ctl|c60|955
kind                                                 BARS
mode                                               filter
trigger                                            NOPULL
win                                              0.605442
n_touch                                               235
n_trig                                                198
n                                                     147
pool_n                                              44114
bracket                                               c60
ok                                                   True
mean1                                           10.999726
mean2                                            8.567479
be                                               0.510656
pool_mean                                       -1.823535
effect                                          12.823261
se                                               5.843302
ci_lo                                            1.658376
ci_hi                                           23.915146
mde80                                           16.361244
t                                                2.194523
trades_wk                                            1.96
usd_trade                                     2199.945161
dir_effect                                      12.724964
dir_lo                                           0.511231
dir_n                                               147.0
G1                                                   True
G2                                                   True
G3                                                   True
G4                                                   True
G5                                                  False
rc_p                                                0.732
paired                                           2.268328
paired_lo                                       -0.694071
paired_hi                                        4.966901
paired_mde                                       4.157371
prior_mde                                       11.849051
rank_draw                                            0.94
draw_mean                                       -0.127933
effect_draw                                     11.127659
Name: 3, dtype: object> | NOPULL (rows 1-10 of the top-30 list) | W10 76, +12.0, -0.3 ; W11 48, -1.2, -1.5 ; W12 32, +14.6, -0.8 ; W13 34, +13.2, -2.2 | 2024 68, +22.2, +0.0 ; 2025 117, +0.8, -1.4 ; 2026 5, +32.3, -3.3 | long 62, +6.1, -2.4 ; short 128, +10.9, +0.2 |
| 5 | B:kagi_32|E3|SMMA_377_close|x5|c60|955 | <bound method Series.mode of cell           B:kagi_32|E3|SMMA_377_close|x5|c60|955
kind                                                BARS
mode                                              filter
trigger                                             DF15
win                                             0.609756
n_touch                                              499
n_trig                                               350
n                                                    164
pool_n                                             49657
bracket                                              c60
ok                                                  True
mean1                                          11.166511
mean2                                           8.531192
be                                              0.512477
pool_mean                                       -1.32074
effect                                          12.48725
se                                              4.525753
ci_lo                                           3.223055
ci_hi                                          20.801313
mde80                                          12.672109
t                                               2.759154
trades_wk                                       2.186667
usd_trade                                    2233.302143
dir_effect                                     13.660018
dir_lo                                          4.135169
dir_n                                              164.0
G1                                                  True
G2                                                  True
G3                                                  True
G4                                                  True
G5                                                 False
rc_p                                               0.327
paired                                         -1.329198
paired_lo                                      -4.508627
paired_hi                                       1.967195
paired_mde                                      4.628511
prior_mde                                      11.218126
rank_draw                                            1.0
draw_mean                                      -1.288929
effect_draw                                    12.455439
Name: 4, dtype: object> | DF15 (rows 1-10 of the top-30 list) | W10 92, +14.2, +0.0 ; W11 49, -5.9, +3.2 ; W12 38, +17.4, +0.9 ; W13 33, +14.1, -5.4 | 2024 69, +10.5, +0.7 ; 2025 133, +10.0, -0.4 ; 2026 10, +9.2, -0.4 | long 108, +11.1, -1.8 ; short 104, +9.1, +1.8 |
| 6 | B:kagi_32|E3|SMMA_377_close|x5|c60|955 | <bound method Series.mode of cell           B:kagi_32|E3|SMMA_377_close|x5|c60|955
kind                                                BARS
mode                                              filter
trigger                                              DF5
win                                             0.603896
n_touch                                              499
n_trig                                               329
n                                                    154
pool_n                                             48129
bracket                                              c60
ok                                                  True
mean1                                          10.526612
mean2                                           7.924978
be                                              0.512072
pool_mean                                       -1.78279
effect                                         12.309402
se                                              5.165817
ci_lo                                           1.744943
ci_hi                                          21.676378
mde80                                          14.464287
t                                               2.382857
trades_wk                                       2.053333
usd_trade                                    2105.322468
dir_effect                                     13.064392
dir_lo                                          2.445465
dir_n                                              154.0
G1                                                  True
G2                                                  True
G3                                                  True
G4                                                  True
G5                                                 False
rc_p                                               0.595
paired                                         -2.352496
paired_lo                                      -6.081855
paired_hi                                       1.494478
paired_mde                                      5.390487
prior_mde                                      11.576622
rank_draw                                            1.0
draw_mean                                      -1.249964
effect_draw                                    11.776576
Name: 5, dtype: object> | DF5 (rows 1-10 of the top-30 list) | W10 86, +15.3, -0.3 ; W11 46, -4.8, +2.8 ; W12 37, +13.1, +1.2 ; W13 30, +13.7, -6.5 | 2024 65, +11.2, +0.9 ; 2025 124, +9.5, -0.9 ; 2026 10, +9.2, -2.5 | long 101, +10.3, -2.4 ; short 98, +9.8, +1.7 |
| 7 | B:kagi_32|E3|SMMA_377_close|x5|c60|955 | <bound method Series.mode of cell           B:kagi_32|E3|SMMA_377_close|x5|c60|955
kind                                                BARS
mode                                              filter
trigger                                             DF30
win                                             0.592814
n_touch                                              499
n_trig                                               360
n                                                    167
pool_n                                             50176
bracket                                              c60
ok                                                  True
mean1                                           9.183979
mean2                                           6.623946
be                                              0.512925
pool_mean                                      -1.795009
effect                                         10.978988
se                                              4.861012
ci_lo                                            0.88171
ci_hi                                          19.705632
mde80                                          13.610835
t                                               2.258581
trades_wk                                       2.226667
usd_trade                                    1836.795787
dir_effect                                     11.658816
dir_lo                                          1.440412
dir_n                                              167.0
G1                                                  True
G2                                                  True
G3                                                  True
G4                                                  True
G5                                                 False
rc_p                                               0.691
paired                                         -1.865759
paired_lo                                      -4.997498
paired_hi                                       0.967371
paired_mde                                      4.127494
prior_mde                                      11.116907
rank_draw                                            1.0
draw_mean                                      -1.605844
effect_draw                                    10.789823
Name: 6, dtype: object> | DF30 (rows 1-10 of the top-30 list) | W10 93, +14.6, -0.4 ; W11 50, -9.3, +2.9 ; W12 40, +13.5, +0.4 ; W13 32, +12.8, -6.3 | 2024 71, +10.1, +0.6 ; 2025 134, +7.7, -1.1 ; 2026 10, +9.2, -0.2 | long 110, +9.8, -2.4 ; short 105, +7.3, +1.5 |
| 8 | B:kagi_32|E3|SMMA_377_close|x5|c60|955 | <bound method Series.mode of cell           B:kagi_32|E3|SMMA_377_close|x5|c60|955
kind                                                BARS
mode                                              filter
trigger                                           NOPULL
win                                             0.579545
n_touch                                              499
n_trig                                               429
n                                                    176
pool_n                                             64718
bracket                                              c60
ok                                                  True
mean1                                           7.677295
mean2                                           5.184136
be                                              0.512827
pool_mean                                      -1.531533
effect                                          9.208828
se                                              4.559391
ci_lo                                          -0.074721
ci_hi                                           17.33365
mde80                                          12.766296
t                                                2.01975
trades_wk                                       2.346667
usd_trade                                    1535.459085
dir_effect                                     10.092327
dir_lo                                          1.251516
dir_n                                              176.0
G1                                                 False
G2                                                  True
G3                                                  True
G4                                                  True
G5                                                 False
rc_p                                                0.84
paired                                         -0.139351
paired_lo                                      -2.368678
paired_hi                                       2.329515
paired_mde                                       3.36289
prior_mde                                      10.828939
rank_draw                                           0.95
draw_mean                                      -0.748973
effect_draw                                     8.426268
Name: 7, dtype: object> | NOPULL (rows 1-10 of the top-30 list) | W10 99, +12.2, +0.2 ; W11 43, -7.3, +1.8 ; W12 38, +17.4, +0.6 ; W13 30, +2.2, -5.3 | 2024 78, +8.4, +1.1 ; 2025 126, +8.7, -1.1 ; 2026 6, -21.7, -2.9 | long 110, +9.1, -1.7 ; short 100, +6.1, +1.1 |
| 9 | S3:E4|cap60|prev_day_extreme+0t|swing_4h_nearest_high | <bound method Series.mode of cell           S3:E4|cap60|prev_day_extreme+0t|swing_4h_neare...
kind                                                          S3
mode                                                      filter
trigger                                                     REF2
win                                                     0.382353
n_touch                                                      643
n_trig                                                       301
n                                                            102
pool_n                                                      2859
bracket          cap60|prev_day_extreme+0t|swing_4h_nearest_high
ok                                                          True
mean1                                                   3.326364
mean2                                                   1.772826
be                                                      0.325911
pool_mean                                              -2.650224
effect                                                  5.976588
se                                                      4.475599
ci_lo                                                  -1.810633
ci_hi                                                  15.850514
mde80                                                  12.531676
t                                                       1.335372
trades_wk                                                   1.36
usd_trade                                             665.272812
dir_effect                                                   NaN
dir_lo                                                       NaN
dir_n                                                        NaN
G1                                                         False
G2                                                         False
G3                                                          True
G4                                                          True
G5                                                         False
rc_p                                                       0.997
paired                                                  2.825287
paired_lo                                              -1.795785
paired_hi                                              10.386481
paired_mde                                              8.718864
prior_mde                                              14.224668
rank_draw                                                    1.0
draw_mean                                              -2.299295
effect_draw                                             5.625659
Name: 8, dtype: object> | REF2 (rows 1-10 of the top-30 list) | W10 49, +12.2, +6.6 ; W11 36, -6.3, -2.7 ; W12 19, +10.9, -4.3 ; W13 17, -4.6, -3.2 | 2024 70, +3.8, -4.4 ; 2025 51, +4.6, +4.0 ; 2026 0 | long 31, -0.4, -6.8 ; short 90, +5.7, +0.7 |
| 10 | S3:E4|cap60|prev_day_extreme+0t|swing_4h_nearest_high | <bound method Series.mode of cell           S3:E4|cap60|prev_day_extreme+0t|swing_4h_neare...
kind                                                          S3
mode                                                      filter
trigger                                                   NOPULL
win                                                     0.324138
n_touch                                                      643
n_trig                                                       581
n                                                            145
pool_n                                                      5150
bracket          cap60|prev_day_extreme+0t|swing_4h_nearest_high
ok                                                          True
mean1                                                   1.376186
mean2                                                  -0.140732
be                                                      0.300625
pool_mean                                              -3.692606
effect                                                  5.068792
se                                                      3.532428
ci_lo                                                  -0.905449
ci_hi                                                   12.89301
mde80                                                   9.890799
t                                                       1.434931
trades_wk                                               1.933333
usd_trade                                              275.23719
dir_effect                                              1.772092
dir_lo                                                -51.988439
dir_n                                                        6.0
G1                                                         False
G2                                                         False
G3                                                         False
G4                                                          True
G5                                                         False
rc_p                                                        0.99
paired                                                  0.489029
paired_lo                                              -1.061948
paired_hi                                               2.264659
paired_mde                                              2.405871
prior_mde                                              11.930488
rank_draw                                                   0.97
draw_mean                                               -2.02818
effect_draw                                             3.404366
Name: 9, dtype: object> | NOPULL (rows 1-10 of the top-30 list) | W10 65, +9.1, +6.1 ; W11 53, -6.9, -4.8 ; W12 23, +9.2, -4.6 ; W13 31, -2.3, -2.8 | 2024 90, +0.5, -5.4 ; 2025 82, +3.9, +2.9 ; 2026 0 | long 41, -1.9, -6.5 ; short 131, +3.4, -0.3 |


## 4. Trigger-level summary on the 15-pt-stop cells (PRE, items with n >= 30)

Per trigger over the 5 E cells: median n, mean effect vs random-in-regime-with-the-same-book, items with effect > 0, mean and max paired change vs the unfiltered touches (identical touches):

| trigger | hold: med n | mean effect | positive | mean paired | max paired | alone: med n | mean effect | positive | mean paired | max paired |
|---|---|---|---|---|---|---|---|---|---|---|
| ABSQ95 | 176 | +0.33 | 4/5 | +0.66 | +1.10 | 203 | +0.02 | 3/5 | +0.56 | +1.02 |
| ABSQ99 | 49 | +0.02 | 1/3 | -0.02 | +0.56 | 53 | -1.11 | 1/4 | -0.72 | +0.84 |
| DF15 | 2023 | +0.29 | 5/5 | -0.14 | +0.03 | 2080 | +0.32 | 5/5 | -0.09 | +0.03 |
| DF30 | 2058 | +0.21 | 5/5 | -0.09 | +0.08 | 2093 | +0.23 | 5/5 | -0.04 | +0.06 |
| DF5 | 1967 | +0.44 | 5/5 | +0.00 | +0.12 | 2039 | +0.47 | 5/5 | +0.07 | +0.14 |
| DIV | 219 | +0.74 | 4/5 | +0.33 | +1.33 | 294 | +1.21 | 4/5 | +0.87 | +1.76 |
| IMB10_15 | 295 | -0.64 | 2/5 | -0.39 | +0.58 | 330 | +0.13 | 3/5 | +0.31 | +0.90 |
| IMB10_20 | 40 | -2.02 | 0/3 | -0.84 | +0.43 | 54 | +1.78 | 3/4 | +2.69 | +4.57 |
| IMB10_CH | 621 | -0.65 | 1/5 | -0.32 | +0.55 | 656 | -0.84 | 0/5 | -0.38 | +0.68 |
| IMB5_15 | 446 | +0.14 | 4/5 | +0.45 | +1.00 | 473 | -0.04 | 2/5 | +0.28 | +0.70 |
| IMB5_20 | 86 | -2.82 | 0/5 | -2.34 | +0.02 | 92 | -1.69 | 1/5 | -1.33 | +1.82 |
| IMB5_CH | 790 | -0.43 | 1/5 | -0.17 | +0.21 | 815 | -0.55 | 1/5 | -0.17 | +0.32 |
| NOPULL | 2148 | +0.03 | 3/5 | -0.01 | +0.04 | 2251 | +0.13 | 4/5 | +0.01 | +0.05 |
| PULLINV | 515 | -0.71 | 0/5 | +nan | +nan | 422 | -0.18 | 2/5 | +nan | +nan |
| REF2 | 1280 | +0.34 | 4/5 | +0.18 | +0.44 | 1349 | +0.18 | 4/5 | +0.07 | +0.46 |
| REF3 | 920 | -0.10 | 1/5 | -0.26 | +0.24 | 960 | +0.00 | 3/5 | -0.17 | +0.39 |

Does the book state predict the 15-pt-stop outcome at RANDOM regime minutes (pool lift, week-block CI), selected rows:

| pool | trigger | share of minutes | mean net1 with trigger | all | lift [CI] |
|---|---|---|---|---|---|
| E1 | ABSQ95 | 3.6% | -1.29 | -1.58 | +0.29 [-0.41, +0.97] |
| E1 | REF2 | 44.1% | -1.39 | -1.58 | +0.19 [+0.04, +0.34] |
| E1 | REF3 | 26.0% | -1.43 | -1.58 | +0.15 [-0.07, +0.38] |
| E1 | IMB5_15 | 7.8% | -1.40 | -1.58 | +0.19 [-0.17, +0.59] |
| E1 | IMB10_20 | 0.8% | -0.56 | -1.58 | +1.02 [-0.30, +2.30] |
| E1 | IMB5_CH | 15.6% | -1.52 | -1.58 | +0.06 [-0.18, +0.30] |
| E1 | DF15 | 67.9% | -1.65 | -1.58 | -0.07 [-0.16, +0.01] |
| E1 | DIV | 2.8% | -1.95 | -1.58 | -0.36 [-1.09, +0.36] |
| E1 | SWR | 0.2% | -2.45 | -1.58 | -0.87 [-3.81, +1.88] |
| E1 | NOPULL | 90.2% | -1.56 | -1.58 | +0.02 [-0.02, +0.06] |
| E1 | PULLINV | 9.8% | -1.77 | -1.58 | -0.19 [-0.55, +0.18] |
| E5 | ABSQ95 | 3.6% | -1.27 | -1.53 | +0.26 [-0.56, +1.11] |
| E5 | REF2 | 44.5% | -1.33 | -1.53 | +0.21 [+0.05, +0.38] |
| E5 | REF3 | 26.3% | -1.31 | -1.53 | +0.22 [-0.03, +0.47] |
| E5 | IMB5_15 | 7.7% | -1.36 | -1.53 | +0.17 [-0.23, +0.61] |
| E5 | IMB10_20 | 0.8% | -0.48 | -1.53 | +1.05 [-0.34, +2.41] |
| E5 | IMB5_CH | 15.5% | -1.55 | -1.53 | -0.02 [-0.27, +0.24] |
| E5 | DF15 | 68.1% | -1.60 | -1.53 | -0.07 [-0.15, +0.01] |
| E5 | DIV | 2.9% | -1.83 | -1.53 | -0.30 [-1.09, +0.52] |
| E5 | SWR | 0.2% | -2.44 | -1.53 | -0.91 [-3.88, +1.90] |
| E5 | NOPULL | 90.5% | -1.50 | -1.53 | +0.03 [-0.01, +0.07] |
| E5 | PULLINV | 9.5% | -1.80 | -1.53 | -0.27 [-0.67, +0.13] |

Only REF2 (>= 2 replenishments) has a CI above 0 in both pools (+0.19 / +0.21 pt per minute, 44% of minutes): about the size of one tick of the half-spread and inside the multiplicity of 22 triggers x 2 pools; delta flip is null to slightly negative, divergence and sweep-reclaim negative.

## 5. B3 - opening-hour book metrics as a 10:00 label

Metrics per label day over 09:30-10:00 ET from the 1-min book table: depth (mean of bid + ask size over 5 levels), imbalance persistence (share of minutes with the dominant imb5 sign), trade-through rate (levels cleared per trade); label = above / below the PRE median (depth 41.4, persistence 0.533, through 0.598). Effect = mean net on high-label days minus low-label days (trades sequenced), and the same net of the random-in-regime difference on those days. The 15 cells x 3 metrics:

| cell | metric | n high / low | mean net high / low | high - low [CI] | pool-adjusted [CI] | MDE80 | HOLD diff [CI] | X diff [CI] |
|---|---|---|---|---|---|---|---|---|
| E1 | depth | 1049/1417 | -1.3 / -1.9 | +0.61 [-0.54, +1.72] | +0.02 [-1.22, +1.15] | 1.7 |  |  |
| E1 | imbpersist | 1161/1305 | -2.1 / -1.3 | -0.80 [-2.11, +0.53] | -0.80 [-2.11, +0.49] | 1.9 |  |  |
| E1 | through | 1438/1028 | -1.9 / -1.3 | -0.54 [-1.73, +0.61] | -0.25 [-1.38, +0.85] | 1.6 |  |  |
| E2 | depth | 875/1232 | -1.2 / -1.6 | +0.41 [-0.96, +1.69] | -0.18 [-1.61, +1.17] | 1.9 |  |  |
| E2 | imbpersist | 981/1126 | -1.6 / -1.3 | -0.35 [-1.82, +1.20] | -0.35 [-1.76, +1.14] | 2.1 |  |  |
| E2 | through | 1243/864 | -1.6 / -1.2 | -0.45 [-1.74, +0.76] | -0.16 [-1.38, +1.02] | 1.7 |  |  |
| E3 | depth | 510/605 | -1.1 / -1.2 | +0.09 [-1.60, +1.71] | -0.50 [-2.19, +0.97] | 2.3 |  |  |
| E3 | imbpersist | 511/604 | -2.0 / -0.5 | -1.47 [-3.47, +0.62] | -1.52 [-3.46, +0.43] | 2.7 |  |  |
| E3 | through | 610/505 | -1.1 / -1.3 | +0.23 [-1.38, +1.97] | +0.32 [-1.23, +1.91] | 2.4 |  |  |
| E4 | depth | 1011/1342 | -1.2 / -1.8 | +0.53 [-0.87, +1.87] | -0.06 [-1.47, +1.34] | 1.9 |  |  |
| E4 | imbpersist | 1048/1305 | -1.6 / -1.5 | -0.18 [-1.55, +1.21] | -0.18 [-1.41, +1.19] | 1.9 |  |  |
| E4 | through | 1338/1015 | -1.8 / -1.2 | -0.67 [-1.82, +0.55] | -0.38 [-1.50, +0.90] | 1.7 |  |  |
| E5 | depth | 1752/2234 | -1.3 / -1.5 | +0.25 [-0.69, +1.26] | -0.48 [-1.22, +0.32] | 1.1 |  |  |
| E5 | imbpersist | 1743/2243 | -1.3 / -1.5 | +0.24 [-0.87, +1.23] | +0.24 [-0.64, +1.07] | 1.2 |  |  |
| E5 | through | 2213/1773 | -1.4 / -1.4 | -0.03 [-1.05, +0.92] | +0.31 [-0.50, +1.14] | 1.2 |  |  |
| F1|R8|d40|a30|L2e40_t5|T0at|955|R1_60 | depth | 35/28 | +16.1 / -0.7 | +16.89 [-6.14, +42.19] | +2.22 [-20.10, +26.60] | 32.9 |  |  |
| F1|R8|d40|a30|L2e40_t5|T0at|955|R1_60 | imbpersist | 28/35 | +17.6 / +1.5 | +16.08 [-6.51, +38.53] | +23.51 [+3.28, +43.50] | 27.6 |  |  |
| F1|R8|d40|a30|L2e40_t5|T0at|955|R1_60 | through | 29/34 | +3.0 / +13.5 | -10.54 [-36.56, +13.30] | +1.10 [-21.94, +24.03] | 33.1 |  |  |
| B:kagi_32|E3|SMMA_377_close|x5|c60|955 | depth | 32/159 | -2.3 / +11.3 | -13.62 [-39.16, +13.29] | -17.41 [-40.30, +8.83] | 34.3 |  |  |
| B:kagi_32|E3|SMMA_377_close|x5|c60|955 | imbpersist | 90/101 | +6.5 / +11.2 | -4.69 [-25.13, +16.49] | -4.56 [-22.52, +14.30] | 26.1 |  |  |
| B:kagi_32|E3|SMMA_377_close|x5|c60|955 | through | 158/33 | +10.3 / +3.0 | +7.24 [-16.94, +28.99] | +14.91 [-10.42, +36.76] | 34.3 |  |  |
| B:renko_38|E2|TMA_377_close|ctl|c60|955 | depth | 42/125 | +19.4 / +5.2 | +14.25 [-10.26, +35.45] | +9.33 [-14.04, +29.68] | 31.2 |  |  |
| B:renko_38|E2|TMA_377_close|ctl|c60|955 | imbpersist | 71/96 | +3.2 / +12.8 | -9.62 [-24.04, +11.28] | -6.94 [-21.99, +12.86] | 25.1 |  |  |
| B:renko_38|E2|TMA_377_close|ctl|c60|955 | through | 131/36 | +4.8 / +23.0 | -18.22 [-38.88, +7.47] | -10.38 [-31.32, +13.13] | 32.6 |  |  |
| S3:E2|cap60|prev_day_extreme+0t|swing_5m_k2_ | depth | 22/9 | -0.5 / +2.3 | -2.77 [-10.91, +14.59] | +1.34 [-15.91, +24.06] | 27.9 |  |  |
| S3:E2|cap60|prev_day_extreme+0t|swing_5m_k2_ | imbpersist | 20/11 | +1.4 / -1.5 | +2.91 [-15.06, +19.03] | -5.35 [-23.00, +16.42] | 28.8 |  |  |
| S3:E2|cap60|prev_day_extreme+0t|swing_5m_k2_ | through | 10/21 | +4.9 / -1.8 | +6.70 [-10.40, +30.87] | +1.23 [-18.22, +30.99] | 32.6 |  |  |
| S3:E2|cap15|swing_15m_k3_last+0t|pivot_R1 | depth | 33/17 | +0.7 / +1.4 | -0.73 [-18.25, +12.36] | -0.32 [-18.70, +12.75] | 22.2 |  |  |
| S3:E2|cap15|swing_15m_k3_last+0t|pivot_R1 | imbpersist | 31/19 | -1.6 / +5.2 | -6.86 [-23.68, +4.19] | -12.50 [-28.41, -2.60] | 18.3 |  |  |
| S3:E2|cap15|swing_15m_k3_last+0t|pivot_R1 | through | 16/34 | +1.8 / +0.6 | +1.23 [-12.31, +21.31] | +5.69 [-7.08, +25.18] | 23.0 |  |  |
| S3:E2|cap20|session_extreme+5t|pivot_R1 | depth | 22/14 | +9.4 / -10.0 | +19.48 [+4.61, +30.67] | +17.32 [-0.02, +34.65] | 24.6 | +7.1 [-10.5, +19.2] (n 4/3) | -3.2 [-10.2, +2.5] (n 38/0) |
| S3:E2|cap20|session_extreme+5t|pivot_R1 | imbpersist | 21/15 | +7.3 / -5.7 | +13.03 [-6.34, +35.47] | +13.66 [-6.71, +34.95] | 28.6 |  |  |
| S3:E2|cap20|session_extreme+5t|pivot_R1 | through | 16/20 | -10.6 / +11.9 | -22.46 [-32.99, -6.73] | -22.12 [-37.31, -5.01] | 23.2 | -0.7 [-11.5, +13.7] (n 2/5) | +39.5 [-0.6, +46.2] (n 1/37) |
| S3:E2|atr1.5|session_extreme+2t|session_extr | depth | 33/38 | -2.9 / +3.1 | -6.01 [-24.87, +12.28] | -6.03 [-23.54, +10.87] | 24.2 |  |  |
| S3:E2|atr1.5|session_extreme+2t|session_extr | imbpersist | 39/32 | -8.3 / +10.8 | -19.13 [-37.39, +1.53] | -11.69 [-30.39, +8.00] | 26.7 |  |  |
| S3:E2|atr1.5|session_extreme+2t|session_extr | through | 40/31 | -1.0 / +2.0 | -3.03 [-21.37, +17.03] | -2.73 [-18.93, +15.76] | 25.3 |  |  |
| S3:E5|atr1.5|prev_hour_extreme+2t|swing_4h_n | depth | 42/31 | +4.7 / +1.5 | +3.26 [-15.06, +19.14] | +4.12 [-14.10, +20.56] | 23.7 |  |  |
| S3:E5|atr1.5|prev_hour_extreme+2t|swing_4h_n | imbpersist | 40/33 | -1.3 / +9.0 | -10.25 [-25.30, +2.84] | -11.12 [-24.82, +0.87] | 19.2 |  |  |
| S3:E5|atr1.5|prev_hour_extreme+2t|swing_4h_n | through | 30/43 | +5.2 / +2.0 | +3.18 [-10.88, +23.30] | +2.66 [-11.09, +23.03] | 25.2 |  |  |
| S3:E5|cap30|session_extreme+5t|swing_5m_k3_l | depth | 26/1 | -1.7 / +40.0 | -41.67 [-48.30, +4.60] | -48.63 [-56.60, -0.89] | 54.5 |  |  |
| S3:E5|cap30|session_extreme+5t|swing_5m_k3_l | imbpersist | 17/10 | -0.1 / -0.3 | +0.26 [-18.85, +24.54] | +8.48 [-10.58, +31.21] | 29.0 |  |  |
| S3:E5|cap30|session_extreme+5t|swing_5m_k3_l | through | 2/25 | +6.4 / -0.7 | +7.04 [-30.33, +42.99] | +11.52 [-29.07, +51.31] | 64.6 |  |  |
| S3:E4|cap60|prev_day_extreme+0t|swing_4h_nea | depth | 86/65 | +3.5 / -2.5 | +5.99 [-6.29, +21.29] | +8.39 [-4.02, +24.31] | 20.0 |  |  |
| S3:E4|cap60|prev_day_extreme+0t|swing_4h_nea | imbpersist | 68/83 | -7.1 / +7.5 | -14.65 [-31.91, -3.78] | -6.25 [-21.04, +4.08] | 18.3 | +19.8 [-11.4, +53.9] (n 20/18) | -4.0 [-21.1, +11.7] (n 38/53) |
| S3:E4|cap60|prev_day_extreme+0t|swing_4h_nea | through | 55/96 | -2.0 / +2.6 | -4.65 [-19.88, +8.92] | -12.32 [-29.08, +1.94] | 22.1 |  |  |

E1-E5 (15 contrasts): high-depth days do +0.1 to +0.6 pts/trade better (E1 +0.61 [-0.54, +1.72], MDE80 1.7), persistence and through-rate point the other way (-0.03 to -1.5); no CI excludes 0, no |difference| reaches its MDE80 (1.1-2.7): **thin book = range day is not a usable 10:00 label for the ZEN cells** (inside MDE). Z6 (F5, 10:15 rule): on TREND days the model bracket is also not separable (ZM1 -0.74 vs random, CI lower -1.97). On the top 10 only 3 of 30 contrasts have a PRE CI that excludes 0 (1.5 expected by chance); in HOLD they have 4/3, 2/5 and 20/18 high/low days with CI including 0 and in X one has 0 low days: not testable, not confirmed.

## 6. B4 - book walls as targets: NOT BUILT

mbp-10 displays 10 levels, a median 9 ticks (2.25 pt) deep; a resting wall 20-40 pt above is not in the data. 30 cells (2 x 15) skipped and counted. What would be needed: a deeper book (mbp-N / full MBO price ladder) or the order-level feed. The first-scale-target idea inside the visible 2.25 pt is below the 5 pt minimum target of the model and was not tested.

## 7. B2 - execution reality, ANALYTIC (not a replay)

No cell survives PRE + HOLD, so by instruction no replay was launched (the governor needs a PRIO_ALLOW entry and a restart by main; none is requested). Everything below is built from measured pieces, not from a 1-s/L2 replay of the cell: (a) entry cost of a market order at 0 / 1 / 3 s after the closed signal bar, measured on the real entries from the 1 s book and the tape (ask - first trade price for longs, mirror for shorts); (b) passive-only entry from a FIFO queue model on the tape (join the best passive level at the signal bar; queue ahead = displayed size; filled when the cumulative opposing aggressor volume at that price reaches the queue or price trades through; cancels ignored = conservative); (c) stop-market slippage from DS3_DN_STOPFILL (measured 1 / 5 / 8 / 10 / 13 / 14 lots = 0.85 / 1.18 / 1.34 / 1.44 / 1.57 / 1.61 pt; 2 lots interpolated in ln(lots) = 0.99; year multipliers 2024 0.78, 2025 1.21, 2026 1.19; the 11:00-14:59 class is 1.45 and 09:45-10:59 1.39, i.e. no penalty for the 10:00-14:00 window) times each cell's realised stop share; the library stop correction is clipped to 0 (zen_lib), so this slippage is not already in the mapped net. Caveat: the DN slippage was measured at DN's Donchian stop triggers (trend-continuation stops), a pullback model's stops may sit in different book states; re-measure with a replay if any cell ever survives. Not measured: the 3-s stop-order delay (DN: 1 s latency +0.38 pt on the stop fill), limit target 'filled only on trade-through' (the library target fill is at the limit; no queue model on targets was run).

Edge after costs = mapped mean net1 - 1-s market entry cost (measured, 0.30-0.58 pt) - P(stop) x slippage(lots, year). PRE + HOLD, sequenced entries:

| cell | n | mapped mean net1 | win bar-fill | win after entry cost + slippage (2/5/10 lots) | P(stop) | stop pts + slip = realised stop (2/5/10 lots) | entry cost 0 s / 1 s / 3 s | edge after costs (2 / 5 / 10 / 14 lots) | lot level where stop slippage alone exceeds the edge |
|---|---|---|---|---|---|---|---|---|---|
| E1 | 3363 | -1.76 | 0.414 | 0.412/0.412/0.412 | 0.564 | 15 + 1.01/1.21/1.47 = 16.0/16.2/16.5 | 0.24 / 0.33 / 0.31 | -2.66 / -2.76 / -2.91 / -3.01 | edge <= 0 before any stop slippage |
| E2 | 2885 | -1.63 | 0.417 | 0.415/0.415/0.415 | 0.560 | 15 + 1.02/1.21/1.48 = 16.0/16.2/16.5 | 0.23 / 0.34 / 0.31 | -2.54 / -2.65 / -2.80 / -2.89 | edge <= 0 before any stop slippage |
| E3 | 1507 | -1.22 | 0.429 | 0.426/0.426/0.426 | 0.536 | 15 + 1.00/1.19/1.45 = 16.0/16.2/16.4 | 0.23 / 0.30 / 0.22 | -2.06 / -2.16 / -2.30 / -2.39 | edge <= 0 before any stop slippage |
| E4 | 3235 | -1.40 | 0.420 | 0.418/0.418/0.418 | 0.565 | 15 + 1.02/1.21/1.48 = 16.0/16.2/16.5 | 0.17 / 0.32 / 0.38 | -2.30 / -2.41 / -2.56 / -2.66 | edge <= 0 before any stop slippage |
| E5 | 5608 | -1.34 | 0.441 | 0.439/0.439/0.439 | 0.538 | 15 + 1.02/1.21/1.48 = 16.0/16.2/16.5 | 0.14 / 0.30 / 0.32 | -2.19 / -2.29 / -2.44 / -2.53 | edge <= 0 before any stop slippage |
| F1|R8|d40|a30|L2e40_t5|T0at|955|R1_60 | 97 | +8.13 | 0.598 | 0.598/0.598/0.598 | 0.320 | 60 + 1.01/1.20/1.46 = 61.0/61.2/61.5 | n/a (limit fill) | +7.55 / +7.49 / +7.41 / +7.35 | >399 |
| B:kagi_32|E3|SMMA_377_close|x5|c60|955 | 242 | +8.77 | 0.591 | 0.591/0.591/0.591 | 0.401 | n/a (60-pt bar-type bracket) | 0.48 / 0.58 / 0.71 | +7.76 / +7.68 / +7.57 / +7.50 | >399 |
| B:renko_38|E2|TMA_377_close|ctl|c60|955 | 224 | +7.07 | 0.576 | 0.576/0.576/0.576 | 0.415 | n/a (60-pt bar-type bracket) | 0.16 / 0.42 / 0.16 | +6.20 / +6.11 / +5.99 / +5.92 | >399 |
| S3:E2|cap60|prev_day_extreme+0t|swing_5m_k2_equa | 57 | +1.30 | 0.561 | 0.561/0.561/0.561 | 0.228 | 37 + 0.97/1.16/1.41 = 37.9/38.1/38.4 | 0.53 / 0.37 / 0.13 | +0.71 / +0.67 / +0.61 / +0.57 | >399 |
| S3:E2|cap15|swing_15m_k3_last+0t|pivot_R1 | 65 | +1.69 | 0.215 | 0.215/0.215/0.215 | 0.692 | 9 + 0.94/1.11/1.36 = 9.5/9.7/9.9 | 0.22 / 0.22 / 0.29 | +0.82 / +0.70 / +0.53 / +0.42 | 64 |
| S3:E2|cap20|session_extreme+5t|pivot_R1 | 43 | +0.64 | 0.186 | 0.186/0.186/0.186 | 0.721 | 13 + 0.91/1.09/1.33 = 13.7/13.9/14.1 | 0.22 / 0.20 / 0.76 | -0.22 / -0.34 / -0.52 / -0.63 | 1 |
| S3:E2|atr1.5|session_extreme+2t|session_extreme | 91 | +3.04 | 0.198 | 0.198/0.198/0.198 | 0.802 | 20 + 0.97/1.16/1.41 = 21.4/21.5/21.8 | 0.29 / 0.32 / 0.27 | +1.94 / +1.79 / +1.58 / +1.45 | >399 |
| S3:E5|atr1.5|prev_hour_extreme+2t|swing_4h_neare | 97 | +1.29 | 0.278 | 0.278/0.278/0.278 | 0.691 | 12 + 0.98/1.16/1.42 = 13.0/13.2/13.4 | 0.24 / 0.35 / -0.22 | +0.27 / +0.14 / -0.04 / -0.15 | 9 |
| S3:E5|cap30|session_extreme+5t|swing_5m_k3_lower | 42 | -1.93 | 0.357 | 0.333/0.333/0.333 | 0.190 | 25 + 0.99/1.18/1.43 = 25.6/25.8/26.1 | 0.24 / 0.29 / 0.15 | -2.40 / -2.44 / -2.48 / -2.52 | edge <= 0 before any stop slippage |
| S3:E4|cap60|prev_day_extreme+0t|swing_4h_nearest | 189 | +1.19 | 0.354 | 0.354/0.354/0.354 | 0.582 | 27 + 1.02/1.21/1.48 = 28.2/28.4/28.7 | 0.22 / 0.30 / 0.70 | +0.30 / +0.19 / +0.03 / -0.07 | 12 |

Entry cost of a market entry: 0.14-0.24 pt at 0 s (about one tick, the directive's +1 tick adverse), 0.30-0.34 pt at 1 s, 0.22-0.38 pt at 3 s for E1-E5 (the 3-s figure is noisy, +0.2 to +0.4). Realised win rate vs bar-fill win rate: 0.412 vs 0.414 (E1) ... 0.439 vs 0.441 (E5): slippage moves a few percent of target trades below zero, not the win rate; the loss is in the stop side (realised stop 16.0-16.5 pt vs 15).

Passive-only (resting limit joined at the best passive level at the signal, FIFO queue model, E1-E5 and the market-entry top cells):

| cell | n entries | mean displayed best-passive size (lots) | fill within 60 s | within 300 s | mean net of FILLED (mapped) | mean net of UNFILLED (missed) |
|---|---|---|---|---|---|---|
| E1 | 3363 | 2.6 | 0.938 | 0.971 | -2.41 | +8.18 |
| E2 | 2885 | 2.6 | 0.936 | 0.971 | -2.27 | +7.78 |
| E3 | 1507 | 2.7 | 0.920 | 0.964 | -1.85 | +6.04 |
| E4 | 3235 | 2.6 | 0.926 | 0.969 | -2.21 | +8.69 |
| E5 | 5608 | 2.7 | 0.913 | 0.958 | -2.22 | +7.93 |
| B:kagi_32|E3|SMMA_377_close|x5|c60|955 | 242 | 2.1 | 0.934 | 0.975 | +7.47 | +27.10 |
| B:renko_38|E2|TMA_377_close|ctl|c60|955 | 224 | 2.2 | 0.951 | 0.969 | +6.18 | +24.20 |
| S3:E2|cap60|prev_day_extreme+0t|swing_5m_k2_equa | 57 | 2.9 | 0.895 | 0.912 | -0.31 | +14.97 |
| S3:E2|cap15|swing_15m_k3_last+0t|pivot_R1 | 65 | 2.9 | 0.938 | 0.985 | +2.00 | -3.15 |
| S3:E2|cap20|session_extreme+5t|pivot_R1 | 43 | 2.9 | 0.884 | 0.953 | -2.56 | +25.02 |
| S3:E2|atr1.5|session_extreme+2t|session_extreme | 91 | 2.4 | 0.923 | 0.978 | +4.73 | -17.24 |
| S3:E5|atr1.5|prev_hour_extreme+2t|swing_4h_neare | 97 | 2.6 | 0.959 | 0.979 | +1.66 | -7.24 |
| S3:E5|cap30|session_extreme+5t|swing_5m_k3_lower | 42 | 3.1 | 0.881 | 0.952 | -2.13 | -0.41 |
| S3:E4|cap60|prev_day_extreme+0t|swing_4h_nearest | 189 | 2.8 | 0.926 | 0.979 | +0.14 | +14.31 |

Passive-only fills 91-95% within 60 s and 96-98% within 300 s (queue ahead is 2-3 lots on average, so the queue is short and price trading through fills most orders), but **the missed 5-9% are the winners**: unfilled entries average +6 to +9 pts (E cells) against -1.9 to -2.4 for the filled; per executed trade the passive entry is about 0.4 pt worse than the market entry even after the ~0.24 pt price improvement. Adverse selection, as in F3 / T-PBX block (iii), not a fill-rate problem.

The lot level at which slippage alone exceeds the per-trade edge: **E1-E5: none (edge <= 0 at zero slippage; -2.3 to -2.9 pts at 10 lots)**. Top cells with a positive mapped mean (all n = 43-242, inside MDE, winner-curse selections): F1 / kagi / renko cells carry 60-pt stops so slippage is 0.3-0.7 pt of a +6 to +8 mean (no lot level below 399); S3 cells 1 lot (cap20, edge -0.2 already), 9 lots (E5 atr1.5), 12 lots (E4 cap60), 64 lots (cap15), > 399 (others) on 43-189 trades. Extrapolation above 14 lots uses the 5-14 lot slope and is flagged.

## 8. Deviations and disclosures

- **Resolution:** book metrics are measured on the closed 60 s signal bar and the entry is the open of the next bar (the bar-based entry of every family). Sub-minute trigger timing (entering the second a trigger fires) was not built; the 'alone' variants therefore trigger on the closed bar, not at the touch second. Seconds-level queue replay of the entries and of the resting limit with 'real queue position' was NOT run (analytic queue model only).
- **Definitions not in the addendum** (fixed in the prereg from distributions or by me, never from P&L): level = extreme of the 60 s window +-2 ticks (the touch line itself is only within a 2-5 pt tolerance of the extreme); absorption 'holds' = last trade >= 4 ticks off the extreme; refresh = re-trade at the passive price within 10 s after the displayed quantity was cleared; imbalance CHANGE = ratio >= 1.5 x its value 60 s earlier; divergence = new extreme beyond the previous 10 same-day bars with higher favourable cumulative delta; sweep = 1-3 ticks through the previous-5-bar extreme with reclaim within 15 s and passive size x1.5; pull = top decile of cancelled / (hit + 10) at the best level (PRE, 11.59); ABSQ95 / ABSQ99 = 51 / 81 contracts (PRE p95 / p99).
- **Base cells:** the top 10 were chosen from the families' own PRE tables by unsequenced family n >= 100; after the one-open-trade rule several have only 31-191 trades (S3 cells 27-73, F1 63), so the book test on them is a count / inconclusive by construction (MDE80 10-30 pts). They are winner-curse selections that every family found dead in HOLD. G2 (random direction) is evaluated as a week-block CI lower bound > 0 of half the mean difference to the opposite side at the same minute, not as a 100-draw rank (the 100-draw machinery was run on the 30 selected items). The screen uses the exact pool expectation for the random-in-regime-with-book placebo.
- **Not run:** B4 (depth); PULLINV on the top 10 (10 cells); flat 15:55; any replay (G10); queue-model market entry with the sweep surcharge; the 3-s stop delay; second pass on a newly found top-3 (not needed).
- **Looks used:** 1 HOLD + 1 X (33 items each), logged. B3 items went to HOLD only when their PRE CI excluded 0 (3 items). All thresholds (pull p90, ABSQ p95 / p99, B3 medians) are PRE values reused in HOLD / X.
- **Selection effects:** top 30 chosen on PRE effect with n >= 100; the 'top 10' table is mandatory and is dominated by the BARS / S3 base cells' own effect; the reality check treats all 495 as the family (best-of-N p 0.096).
- **Lib:** no zen_lib bug found; zen_struct._grid fill_mode=1 not used (Z.simulate and the families' own pool simulators only); reproduction checks: E-cell pool mean -1.58 = F3 / STRUCT, S3 cells reproduce the stored n_seq and mean exactly, BARS cells reproduce the family effect (kagi +10.755, renko +10.629), F1 reproduces the sequenced mean (8.64) and pool (2.64).
- **Memory / compute:** < 6 GB peak, CPU only, nice 19, no worker beyond 5 threads; features for 34 months take 1 s per month.

## 9. Files / code

Code: l2vast/ds3/code/zen/l2/ (l2_feat.py features + leak test, l2_trig.py triggers, l2_cells.py base-cell builders, l2_score.py scoring / reality check / draws, l2_run.py PRE screen, l2_top.py, l2_hold.py, l2_b2.py, l2_b3.py, l2_tables*.py, l2_enum.py). Outputs: l2vast/ds3/out/zen/l2/ (items_PRE/HOLD/X.csv, top30_PRE.csv, top30_gates.csv, b3_*.csv, b2_analytic.csv, pool_lift_PRE.csv, trigger_summary_E_PRE.csv, desc_trigger_counts_PRE.csv, feat_PRE/HOLD/X.npz, looks.jsonl). Prereg: l2vast/ds3/prereg/ZEN_L2_B1_prereg.md (+ .sha256, ZEN_L2_B1_cells.csv); PREHOLD autopilot/DS3_ZEN_L2_PREHOLD.md.

Plain line: **the book only filters** (it adds +0.00 pts/trade at the 15-pt stop over the same touches without it; best single trigger +1.33 inside an MDE of 3.7, adjusted p 1.00).

DONE L2
