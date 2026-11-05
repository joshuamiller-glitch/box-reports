# DS3_INSTR2_ES - T-INSTR-2 section 1 (Z1): ES on its own grid, STAGE-1 INTERIM (2026-11-05T20:20Z). Research only, no PASS claims, nothing live.
Scope ES sha256 8898fc1c0fb551fede8e45707676d2643209ed532a1b47fed9d5af2233dc643b (DECISIONS.md, before any cell was scored); grid T2Z1_grid.md sha256 736a94052b1089e0212d492ccadb34d49c8c3e96b6ff86a89a78b1d915aa947b; sig_lib v2 (two level look-aheads fixed; truncation test 0 of 384 level cuts and 0 of 8,064 event comparisons mismatch; the v1 ES run was never read and is SUPERSEDED, output in ds3_instr2_z1/ES_v1_SUPERSEDED_LEAK). Look-ahead cut test passed by the feature code: code/instr2_z1/test_trunc.py (cuts every 15 min across 17:00-18:30, 08:30-09:35 and 15:55-16:05 ET on 24 random label days; all level features and the events of 21 configs covering every family). Code l2vast/ds3/code/instr2_z1/ (sig_lib, i2eval, i2run, i2an, i2fin, i2page); results /mnt/l2/l2vast/ds3_instr2_z1/ES/ (cells_all.parquet = every cell, M.npy = null max).
Data: 1-min bars to 2026-10-16 (ES); sessions by entry ET minute (asia 18:00-02:00, london 02:00-08:30, pre 08:30-09:30, nyam 09:30-12:00, nypm 12:00-15:00, close 15:00-16:55; no live-window block, V0 clock); equal-$ risk $1,200, fractional lots, BASE costs (INSTR_SCALING.md, fee $4.84 proxy), 1-min approximation (stage 2 re-runs finalists on ticks/1-s where they exist).
## 0. Plain sentence
**STAGE-1 RESULT (ES): 0 LEAD CANDIDATES. Of 502,740 grid cells 486,864 were evaluated (456,498 eligible), 42,162 are positive in L3M, L6M and HOLD, 8,149 pass the tolerant gate, 28,986 are NOW-ONLY (REGIME); the best tolerant cell has family p 0.64 (the family null max z_j has median 3.57 and 95th percentile 4.01; the best real z_j is 4.26), and the 15 cells with family p <= .10 are all NOW-ONLY London/regime cells with PRE and X' deeply negative. Every tolerant cell sits inside what the random-side null produces over the grid (best-of-F), so none is a lead.**
Counts: cells evaluated 486,864 of 502,740 (the rest have too few events or invalid brackets); eligible (>= 10 L6M and >= 30 HOLD trades) 456,498; positive L3M+L6M+HOLD 42,162 (9.2% of eligible); TOLERANT 8,149 (1.79%); NOW-ONLY 28,986; leads 0; min family p over all cells 0.020. Null: 200 forward-only random-side worlds (hash-based common random numbers), z_j = min(z_L6M, z_HOLD), Westfall-Young max over all eligible cells.
## 1. Ranked table: TOLERANT cells (top 25 by z_j; each family x session x orientation x config shown once at its best bracket; corr to the NQ stack and stack gain come in stage 2)
| instrument | session | family | config orientation | bracket | L1M / L3M / L6M / HOLD / MID / PRE / X' ($/wk, equal-risk $1,200) | pre-2023 ($/wk) | HOLD maxDD ($) | HOLD Calmar | z_j | family p | label |
|--|--|--|--|--|--|--|--|--|--|--|--|
| ES | close | K | K|b5|ema8|atr14|m0.5 against | A4 1.5R T60 | +1050 / +309 / +665 / +408 / -151 / +31 / -262 | -478 | 7161 | 2.85 | 3.47 | 0.64 | tolerant, best-of-F (family p 0.64), not a lead |
| ES | close | K | K|b1|ema21|atr7|m1.0 against | A3 1.5R T60 | +418 / +656 / +994 / +580 / +391 / -96 / -378 | -996 | 6302 | 4.60 | 3.41 | 0.75 | tolerant, best-of-F (family p 0.75), not a lead |
| ES | close | K | K|b1|ema13|atr14|m1.5 against | A3 1.0R T120 | +2095 / +821 / +746 / +459 / -90 / -178 / -109 | -258 | 4449 | 5.16 | 3.28 | 0.92 | tolerant, best-of-F (family p 0.92), not a lead |
| ES | close | K | K|b1|ema34|atr20|m1.0 against | A3 2.0R T60 | -8 / +67 / +632 / +529 / +702 / +237 / -160 | -917 | 6311 | 4.19 | 3.26 | 0.93 | tolerant, best-of-F (family p 0.93), not a lead |
| ES | pre | S | S|b2|atr14|m1.5 with | D600 1.0R T60 | +1811 / +1317 / +1104 / +753 / +864 / -168 / -224 | -273 | 5819 | 6.47 | 3.12 | 1.00 | tolerant, best-of-F (family p 1.00), not a lead |
| ES | nyam | K | K|b1|ema21|atr14|m2.5 with | D600 2.0R T120 | +1937 / +1293 / +1400 / +910 / +86 / -462 / -342 | -95 | 11953 | 3.81 | 3.07 | 1.00 | tolerant, best-of-F (family p 1.00), not a lead |
| ES | close | K | K|b1|ema21|atr7|m1.5 against | D1200 1.5R T60 | -259 / +94 / +640 / +385 / +756 / -62 / -183 | -229 | 7410 | 2.59 | 3.04 | 1.00 | tolerant, best-of-F (family p 1.00), not a lead |
| ES | nypm | S | S|b15|atr10|m2.5 with | D2400 1.0R T30 | +1 / +123 / +235 / +148 / -20 / +20 / -54 | -29 | 1630 | 4.55 | 2.99 | 1.00 | tolerant, best-of-F (family p 1.00), not a lead |
| ES | pre | K | K|b2|ema13|atr10|m1.0 against | D600 1.5R T120 | +1268 / +1396 / +1323 / +703 / +412 / +17 / -312 | -10 | 6762 | 5.20 | 2.96 | 1.00 | tolerant, best-of-F (family p 1.00), not a lead |
| ES | pre | K | K|b2|ema13|atr20|m1.0 against | D600 1.0R T120 | +1541 / +1061 / +845 / +611 / +526 / +135 / -264 | -62 | 9881 | 3.09 | 2.91 | 1.00 | tolerant, best-of-F (family p 1.00), not a lead |
| ES | nyam | K | K|b1|ema21|atr10|m2.5 with | D1200 1.0R T120 | +2439 / +1207 / +1126 / +733 / +67 / -245 / -196 | -56 | 6995 | 5.24 | 2.91 | 1.00 | tolerant, best-of-F (family p 1.00), not a lead |
| ES | nypm | S | S|b10|atr5|m3.0 with | A3 1.0R T120 | +694 / +696 / +826 / +380 / -71 / -167 / -99 | -146 | 5703 | 3.33 | 2.90 | 1.00 | tolerant, best-of-F (family p 1.00), not a lead |
| ES | close | K | K|b1|ema8|atr20|m1.0 against | D1200 1.5R T60 | +209 / +574 / +424 / +322 / +391 / -43 / -104 | -217 | 6048 | 2.66 | 2.86 | 1.00 | tolerant, best-of-F (family p 1.00), not a lead |
| ES | close | K | K|b2|ema21|atr10|m1.0 against | D600 1.5R T60 | +1046 / +290 / +734 / +363 / -1367 / -192 / +35 | -347 | 18595 | 0.98 | 2.82 | 1.00 | tolerant, best-of-F (family p 1.00), not a lead |
| ES | close | K | K|b1|ema13|atr20|m1.5 against | A3 1.0R T120 | +1404 / +516 / +565 / +314 / -175 / -118 / +143 | -272 | 5945 | 2.64 | 2.81 | 1.00 | tolerant, best-of-F (family p 1.00), not a lead |
| ES | close | K | K|b2|ema8|atr7|m2.0 against | A3 1.0R T60 | +106 / +82 / +310 / +291 / +269 / -28 / +131 | -175 | 2536 | 5.73 | 2.81 | 1.00 | tolerant, best-of-F (family p 1.00), not a lead |
| ES | pre | K | K|b10|ema13|atr20|m0.5 with | D600 1.0R T60 | +179 / +629 / +932 / +521 / +438 / -205 / +35 | -213 | 7509 | 3.47 | 2.78 | 1.00 | tolerant, best-of-F (family p 1.00), not a lead |
| ES | nyam | K | K|b2|ema8|atr20|m1.0 with | A3 1.0R T60 | +2033 / +2004 / +1238 / +710 / +105 / -478 / +67 | -1184 | 7743 | 4.59 | 2.77 | 1.00 | tolerant, best-of-F (family p 1.00), not a lead |
| ES | pre | K | K|b10|ema13|atr14|m0.5 with | D2400 1.0R T60 | +320 / +382 / +369 / +270 / +88 / -30 / +17 | -39 | 1443 | 9.34 | 2.74 | 1.00 | tolerant, best-of-F (family p 1.00), not a lead |
| ES | close | K | K|b5|ema8|atr10|m0.5 against | A6 1.5R T60 | +370 / +179 / +319 / +189 / -149 / +85 / -139 | -306 | 4671 | 2.02 | 2.73 | 1.00 | tolerant, best-of-F (family p 1.00), not a lead |
| ES | pre | K | K|b10|ema13|atr10|m0.5 with | D1200 1.5R T60 | +909 / +816 / +563 / +400 / -87 / -67 / +12 | -87 | 4939 | 4.05 | 2.73 | 1.00 | tolerant, best-of-F (family p 1.00), not a lead |
| ES | close | K | K|b5|ema8|atr20|m0.5 against | A4 1.0R T60 | +1118 / +457 / +597 / +298 / -426 / +45 / -267 | -438 | 10045 | 1.48 | 2.73 | 1.00 | tolerant, best-of-F (family p 1.00), not a lead |
| ES | close | K | K|b1|ema34|atr14|m1.0 against | A2 1.5R T60 | -807 / +9 / +1069 / +616 / +69 / +48 / -253 | -1580 | 8227 | 3.74 | 2.73 | 1.00 | tolerant, best-of-F (family p 1.00), not a lead |
| ES | pre | PB | PB|b5|st10_3|ema10 against | A2 2.0R T60 | +3073 / +2094 / +870 / +481 / -483 / -296 / +46 | -755 | 8540 | 2.82 | 2.71 | 1.00 | tolerant, best-of-F (family p 1.00), not a lead |
| ES | pre | K | K|b2|ema13|atr7|m1.0 against | A2 2.0R T120 | +1065 / +2297 / +1656 / +622 / -159 / -201 / -437 | -692 | 18623 | 1.67 | 2.70 | 1.00 | tolerant, best-of-F (family p 1.00), not a lead |
## 2. Top 12 NOW-ONLY cells (REGIME, reported beside the pooled)
| instrument | session | family | config orientation | bracket | L1M / L3M / L6M / HOLD / MID / PRE / X' ($/wk, equal-risk $1,200) | pre-2023 ($/wk) | HOLD maxDD ($) | HOLD Calmar | z_j | family p | label |
|--|--|--|--|--|--|--|--|--|--|--|--|
| ES | london | K | K|b3|ema34|atr14|m1.0 against | A2 1.0R T120 | +1066 / +2002 / +1370 / +463 / -376 / -2983 / -3055 | -5259 | 18542 | 1.25 | 4.08 | 0.03 | NOW-ONLY REGIME (fails tolerant: PRE/X' or persistence) |
| ES | london | K | K|b3|ema34|atr7|m1.0 against | A2 1.0R T120 | +2479 / +1200 / +1636 / +449 / +140 / -3525 / -3252 | -5036 | 17425 | 1.29 | 3.85 | 0.15 | NOW-ONLY REGIME (fails tolerant: PRE/X' or persistence) |
| ES | london | S | S|b3|atr14|m4.0 against | A2 2.0R T60 | +3351 / +1694 / +973 / +176 / -975 / -1916 / -3128 | -4134 | 17188 | 0.51 | 3.64 | 0.40 | NOW-ONLY REGIME (fails tolerant: PRE/X' or persistence) |
| ES | london | K | K|b2|ema13|atr14|m0.5 against | A3 2.0R T60 | +5969 / +671 / +420 / +162 / -824 / -2542 / -3786 | -6862 | 21903 | 0.37 | 3.64 | 0.40 | NOW-ONLY REGIME (fails tolerant: PRE/X' or persistence) |
| ES | close | K | K|b1|ema21|atr7|m1.0 against | A2 1.5R T60 | +443 / +1375 / +1480 / +911 / +329 / -362 / -815 | -1629 | 6898 | 6.60 | 3.63 | 0.41 | NOW-ONLY REGIME (fails tolerant: PRE/X' or persistence) |
| ES | close | K | K|b5|ema8|atr14|m0.5 against | A4 2.0R T60 | +1050 / +297 / +623 / +399 / -93 / +39 / -290 | -464 | 7161 | 2.79 | 3.40 | 0.78 | NOW-ONLY REGIME (fails tolerant: PRE/X' or persistence) |
| ES | pre | S | S|b2|atr7|m1.5 with | D600 1.0R T60 | +1873 / +1242 / +1131 / +727 / +707 / -340 / -288 | -286 | 6015 | 6.05 | 3.27 | 0.93 | NOW-ONLY REGIME (fails tolerant: PRE/X' or persistence) |
| ES | london | K | K|b2|ema13|atr20|m0.5 against | A4 1.5R T60 | +4419 / +155 / +23 / +72 / +229 / -1722 / -2820 | -5167 | 21777 | 0.17 | 3.24 | 0.93 | NOW-ONLY REGIME (fails tolerant: PRE/X' or persistence) |
| ES | close | K | K|b1|ema21|atr10|m1.0 against | A3 1.0R T60 | -680 / +44 / +709 / +581 / +891 / -65 / -395 | -982 | 10005 | 2.90 | 3.24 | 0.93 | NOW-ONLY REGIME (fails tolerant: PRE/X' or persistence) |
| ES | london | K | K|b3|ema34|atr10|m1.0 against | A3 2.0R T60 | +3436 / +85 / +405 / +86 / -2128 / -1825 / -4357 | -5742 | 38154 | 0.11 | 3.15 | 0.98 | NOW-ONLY REGIME (fails tolerant: PRE/X' or persistence) |
| ES | london | S | S|b5|atr5|m2.5 against | A3 1.5R T60 | +2739 / +1667 / +529 / +72 / -538 / -1945 / -1389 | -2682 | 18781 | 0.19 | 3.14 | 0.99 | NOW-ONLY REGIME (fails tolerant: PRE/X' or persistence) |
| ES | nyam | K | K|b1|ema21|atr10|m2.5 with | D600 2.0R T120 | +4370 / +1761 / +1629 / +1117 / -342 / -426 / -526 | -76 | 10194 | 5.48 | 3.10 | 1.00 | NOW-ONLY REGIME (fails tolerant: PRE/X' or persistence) |
## 3. Cells with family p <= .10 (all, one per config x orientation x session)
| instrument | session | family | config orientation | bracket | L1M / L3M / L6M / HOLD / MID / PRE / X' ($/wk, equal-risk $1,200) | pre-2023 ($/wk) | HOLD maxDD ($) | HOLD Calmar | z_j | family p | label |
|--|--|--|--|--|--|--|--|--|--|--|--|
| ES | london | K | K|b3|ema34|atr14|m1.0 against | A3 1.5R T30 | +367 / -153 / +319 / -545 / -1993 / -4083 / -5610 | -8461 | 38178 | -0.71 | 4.17 | 0.02 | other family p 0.020 |
| ES | london | K | K|b3|ema34|atr7|m1.0 against | A3 1.5R T30 | +658 / -380 / +604 / -687 / -2485 / -3969 / -5798 | -8470 | 55777 | -0.62 | 4.05 | 0.04 | other family p 0.040 |
| ES | london | K | K|b3|ema34|atr10|m1.0 against | A3 2.0R T30 | -92 / -471 / +126 / -711 / -2472 / -4127 / -5489 | -8446 | 44516 | -0.80 | 3.99 | 0.06 | other family p 0.065 |
## 4. Family x session map (number of cells / tolerant / NOW-ONLY / best z_j)
| family | asia | london | pre | nyam | nypm | close |
|--|--|--|--|--|--|--|
| DC | 2520 / 4 / 24 / 2.33 | 2520 / 0 / 6 / 2.54 | 2520 / 76 / 324 / 2.52 | 2520 / 27 / 189 / 2.49 | 2520 / 12 / 85 / 1.98 | 2520 / 211 / 262 / 2.62 |
| FB | 1512 / 0 / 26 / 2.26 | 2268 / 24 / 55 / 2.03 | 3024 / 41 / 96 / 1.77 | 3780 / 36 / 396 / 2.25 | 3780 / 21 / 90 / 1.46 | 3402 / 0 / 0 / 1.89 |
| HV | 2268 / 0 / 19 / 2.12 | 2268 / 0 / 74 / 2.87 | 2268 / 9 / 258 / 2.22 | 2268 / 41 / 160 / 1.28 | 2268 / 49 / 272 / 2.19 | 2268 / 141 / 198 / 1.80 |
| K | 50400 / 6 / 482 / 2.25 | 50400 / 53 / 733 / 4.26 | 50400 / 1170 / 4852 / 3.04 | 50400 / 1017 / 3764 / 3.10 | 50400 / 854 / 2627 / 2.75 | 50400 / 2628 / 5352 / 3.63 |
| MV | 2268 / 7 / 51 / 2.27 | 2268 / 1 / 59 / 2.90 | 2268 / 39 / 271 / 2.59 | 2268 / 28 / 142 / 2.06 | 2268 / 7 / 91 / 1.81 | 2268 / 204 / 271 / 2.44 |
| OR | 378 / 0 / 5 / 1.54 | 378 / 0 / 6 / 2.06 | - | 378 / 9 / 41 / 1.48 | 378 / 0 / 0 / 2.02 | - |
| PB | 2016 / 0 / 5 / 2.73 | 2016 / 0 / 2 / 3.16 | 2016 / 50 / 174 / 2.71 | 2016 / 31 / 202 / 2.26 | 2016 / 32 / 63 / 1.94 | 2016 / 77 / 215 / 2.36 |
| PD | 504 / 0 / 18 / 1.98 | 504 / 0 / 46 / 1.35 | 504 / 0 / 0 / 1.10 | 504 / 1 / 36 / 1.67 | 504 / 0 / 0 / 1.58 | 504 / 0 / 0 / 1.22 |
| S | 15120 / 16 / 182 / 2.88 | 15120 / 10 / 641 / 3.64 | 15120 / 300 / 1828 / 3.27 | 15120 / 182 / 1232 / 2.49 | 15120 / 374 / 1524 / 2.99 | 15120 / 179 / 773 / 2.17 |
| SX | 504 / 0 / 1 / 1.32 | 1008 / 0 / 42 / 1.78 | 1260 / 10 / 53 / 1.86 | 1512 / 13 / 48 / 2.41 | 1260 / 0 / 0 / 1.87 | 882 / 0 / 0 / 1.11 |
| VW | 756 / 0 / 6 / 2.17 | 1512 / 0 / 12 / 1.88 | 1512 / 17 / 106 / 2.30 | 2268 / 45 / 180 / 2.16 | 2268 / 15 / 137 / 1.75 | 2268 / 82 / 179 / 2.33 |
Reading: the tolerant set is dominated by Keltner-breakout FADES (orientation against) in the 15:00-16:55 close session and by the pre/nyam/nypm sessions of the same family; those cells share the same events (hundreds of near-duplicate brackets), so the count of 8,000 cells is a handful of hypotheses; their family p (best 0.64) is far above .10. The only family-level cells (p <= .10) are London-session NOW-ONLY fades with PRE and X' of -$2.5k to -$3.8k/wk: a 2026-only pattern.
## 5. What stage 2 will do (prereg)
Top 30 distinct tolerant cells (and any lead): shared evaluator (BASE-4 instr2_eval: gate, forward-only shift5/side/days placebos, purged walk-forward on neighbouring parameter settings, V0/V2 stack correlation, stack Calmar/maxDD gain at equal risk with the carrying week dropped), 13-year percent-frame check, tick/1-s re-run (ES 2023-08+), NQ-ES joint tape; trade frames saved to /mnt/l2/l2vast/instr2_trades/ES/<cell_id>.parquet; ledger T2_ES (tolerant + NOW-ONLY + family p <= .5 cells and family-level summary rows; the full cell table stays in cells_all.parquet) and registry slice T2_ES = 502,740.
