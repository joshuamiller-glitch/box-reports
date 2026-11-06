# DS3_INSTR2_GC (S4a, T-INSTR-2 section 1, gold on its own grid; 2026-11-05 20:35Z; prereg autopilot/INSTR2_GC_PREREG.md sha256 6bfc49026ea3828474bc6907d5b2f49b4a5085ce0abf8f8fed02fbfc99dd5a2e). Research only, Shadow, no PASS claims, no purchases.
**Plain sentence: GC has no book on this evidence. Of 141,120 cells (448 signal sets x 5 liquid sessions x 63 brackets), 1,756 pass the tolerant gate, and they are one pattern: trend-following flips (Keltner 1,125, Supertrend 398, plus VWAP-reclaim, momentum, pullback, HMA-VWAP, Donchian, ORB) in NY-AM and the 08:30 pre session that pay in 2026; all 40 finalists fail the shared evaluator (placebo p_book .06-.99, family p 1.00 at F = 132,286), and every one is NEGATIVE in 2013-2023 (percent frame; 0-6 of 11 pre-2023 years positive; $-362k to $-2k over the 10 years), with the 1-min pipeline calibrated against the tick-built 1-s path at weekly correlation 0.93-1.00 (>= 0.90, so the verdict is formal). Label: REGIME (2026-only), not a diversifier book.**
## Setup
Feed: raw GC.v.0 1-min (cache_te2/GC.npz, 2013-01..2026-10-16, 69 contract changes) additive back-adjusted, label days from 18:00 ET, 138 roll label days dropped. Sessions (Z2 session_def_liquid, ET): asia 18:00-02:00, london 02:00-08:30, pre 08:30-09:30, nyam 09:30-12:00, nypm 12:00-15:00 (close 15:00-16:55 THIN, not tested); flat 16:55. Fills: 1-min live-style (next-bar open + 1 tick, resting stop 2 ticks worse, time exit 1 tick, fee $4.84 RT = te2_lib PROXY: FEES.md has no GC entry; no fee edge claimed); lots = min($1,200 / stop $, 6, session participation cap 4 / 7 / 16 / 18 / 7). Data end 2026-10-16, windows as book_harness gate_v3 (PRE carry-dropped weeks 2025 W06-09).
Look-ahead tests passed: (1) full-data truncation audit test_causal.py: 2,808 sampled signals across all 12 families, 0 mismatches; (2) intraday cut audit test_cuts.py (lead's alert; every 15 min across 17:00-18:30, 08:30-09:35, 15:55-16:05 ET on 12 days: Sunday opens, DST weeks, half-day, roll days, plain Tuesday): 13 families x 60 cuts = 780 checks, 1,792 signals compared, 0 mismatches. All levels are running or previous-label-day (PDH/PDL of the previous label day, OR / session extreme / VWAP cumulative, first-per-key chronological).
## Stage 1 (all 132,286 cells with >= 100 trades of 141,120 tried; n_tested T2_GC = 141,120)
Share of cells with window mean > 0: L3M 0.42, L6M 0.45, HOLD 0.34, PRE 0.14, X' 0.14: the recent windows pay, 2023-25 does not. Tolerant gate passers 2,100: by family {'KELT': 1323, 'SUPT': 482, 'VWR': 99, 'MOM': 66, 'DON': 46, 'HMAV': 39, 'PB': 32, 'ORB': 7, 'VWJ': 4, 'FBF': 1, 'PDF': 1}; by session {'nyam': 1012, 'pre': 833, 'asia': 159, 'london': 85, 'nypm': 11}.
## Stage 2 (40 finalists: best HOLD Calmar, <= 6 per family; BASE-4's shared evaluator, my 1-min kernel as simulator, 100 worlds each of forward shift5, random side and shuffled day; purged walk-forward over the 63 bracket variants; correlation and stack gain vs the Q1-A ts2 NQ stack V0 and V2)
Verdicts: {'FAILS': 40}. Strongest by placebo: HMAV nyam {"b": 5, "n": 34} stop usd1200 R2.0 T120: p_book 0.050; daily correlation to the NQ stack ~ 0 (V0 and V2), stack Calmar gain positive; but it fails the family test (Bonferroni over 132,286 cells) and its 2013-2023 record is -189337 USD (0 of 11 years positive): a 2026 trend-regime cell, uncorrelated to NQ only because it is a different market, not a persistent edge.
Canonical-bracket family null (4,480 cells = all 448 signal sets x 5 sessions x {stop ATR3, stop $1,200} x R1.5 x T60; worlds: random side and forward shift5, 100 each; the full 141,120-cell max-T is not run: 63 brackets would take about 14 hours per world set; finalists carry the Bonferroni family p of the evaluator instead): pending (canonical-bracket family run in progress).
## 13-year check (2013-01..2023-03, percent frame, roll days dropped) and tick calibration (2023-04..2026-10) for the 40 finalists
| fam   | sess   | stop    |   R |   T |   n13 |      usd13 |   pts13 |   yrs_pos |   yrs |   calib |
|:------|:-------|:--------|----:|----:|------:|-----------:|--------:|----------:|------:|--------:|
| KELT  | nyam   | usd600  | 1.5 | 120 |   837 |  -96859.2  |   -0.3  |         2 |    11 |    0.96 |
| KELT  | nyam   | usd600  | 1.5 |  30 |   840 |  -65901.9  |   -0.22 |         3 |    11 |    0.96 |
| KELT  | nyam   | usd600  | 1.5 |  60 |   839 |  -87914.7  |   -0.28 |         3 |    11 |    0.96 |
| KELT  | nyam   | atr2    | 1   | 120 |  2003 | -144171    |   -0.07 |         5 |    11 |    0.96 |
| KELT  | nyam   | atr2    | 1   | 120 |  2109 | -189592    |   -0.14 |         2 |    11 |    0.96 |
| KELT  | nyam   | atr2    | 2   |  60 |  2062 | -208628    |   -0.15 |         3 |    11 |    0.97 |
| VWR   | nyam   | atr6    | 2   |  60 |  1413 |  -47463.1  |   -0.33 |         0 |    11 |    0.98 |
| VWR   | pre    | atr4    | 2   | 120 |   861 |  -79999.8  |   -0.4  |         3 |    11 |    0.99 |
| VWR   | pre    | atr4    | 1.5 | 120 |   865 |  -82294.1  |   -0.45 |         3 |    11 |    0.98 |
| PB    | asia   | usd2400 | 1.5 | 120 |  7382 | -160130    |   -0.21 |         2 |    11 |    0.97 |
| DON   | asia   | atr6    | 1   | 120 |   612 |  -31584.2  |   -0.09 |         4 |    11 |    0.98 |
| SUPT  | nyam   | atr6    | 1   |  60 |  1559 |  -68929.4  |   -0.21 |         2 |    11 |    0.98 |
| SUPT  | nyam   | atr2    | 1.5 |  60 |  1024 |  -58878.6  |   -0.05 |         3 |    11 |    0.96 |
| VWR   | nyam   | usd2400 | 2   | 120 |   726 |  -14440.9  |   -0.23 |         2 |    11 |    0.98 |
| VWR   | pre    | atr4    | 1   | 120 |   871 |  -75921.8  |   -0.4  |         3 |    11 |    0.98 |
| VWR   | pre    | atr3    | 1   | 120 |   883 |  -88826    |   -0.36 |         2 |    11 |    0.96 |
| PB    | asia   | usd2400 | 2   | 120 |  7378 | -158801    |   -0.2  |         2 |    11 |    0.97 |
| SUPT  | nyam   | atr4    | 1.5 |  60 |  1494 |  -87766.6  |   -0.19 |         3 |    11 |    0.97 |
| SUPT  | nyam   | atr3    | 2   |  60 |  1656 | -131993    |   -0.17 |         3 |    11 |    0.96 |
| SUPT  | nyam   | atr3    | 1   |  60 |  1663 | -127368    |   -0.17 |         3 |    11 |    0.93 |
| SUPT  | nyam   | atr4    | 1.5 |  60 |  1588 | -106642    |   -0.21 |         3 |    11 |    0.98 |
| DON   | asia   | atr6    | 1.5 | 120 |   610 |  -24971    |   -0.05 |         6 |    11 |    1    |
| DON   | asia   | atr6    | 2   | 120 |   610 |  -29513.9  |   -0.09 |         4 |    11 |    0.99 |
| HMAV  | nyam   | usd1200 | 2   | 120 |  2588 | -189337    |   -0.38 |         0 |    11 |    0.97 |
| MOM   | pre    | atr4    | 2   |  30 |  2503 | -196761    |   -0.37 |         0 |    11 |    0.99 |
| MOM   | pre    | atr4    | 2   |  30 |  2544 | -198624    |   -0.37 |         0 |    11 |    0.99 |
| HMAV  | pre    | atr6    | 1   |  30 |  3421 | -129718    |   -0.18 |         1 |    11 |    1    |
| PB    | pre    | atr2    | 1.5 | 120 |  2122 | -341975    |   -0.34 |         2 |    11 |    0.96 |
| ORB   | nyam   | usd1200 | 1.5 |  30 |  3005 | -130310    |   -0.24 |         2 |    11 |    0.95 |
| DON   | asia   | usd2400 | 2   | 120 |   610 |   -2292.9  |   -0.02 |         4 |    11 |    1    |
| MOM   | pre    | atr6    | 1.5 |  30 |  2479 | -134674    |   -0.39 |         0 |    11 |    0.99 |
| HMAV  | pre    | atr6    | 1.5 |  30 |  3405 | -138325    |   -0.2  |         1 |    11 |    0.99 |
| MOM   | pre    | atr6    | 2   |  30 |  2479 | -135318    |   -0.4  |         0 |    11 |    0.99 |
| HMAV  | pre    | atr6    | 2   |  30 |  3402 | -137588    |   -0.2  |         1 |    11 |    1    |
| DON   | asia   | usd2400 | 1.5 | 120 |   610 |   -2084.42 |   -0.02 |         5 |    11 |    0.99 |
| MOM   | pre    | atr6    | 1.5 |  30 |  2521 | -133616    |   -0.39 |         0 |    11 |    0.99 |
| PB    | asia   | usd2400 | 1   | 120 |  7478 | -145828    |   -0.18 |         2 |    11 |    0.97 |
| PB    | pre    | atr2    | 1.5 | 120 |  2281 | -362236    |   -0.36 |         1 |    11 |    0.96 |
| PB    | pre    | usd1200 | 2   |  30 |  3699 | -222251    |   -0.31 |         0 |    11 |    0.97 |
| MOM   | pre    | atr6    | 2   |  30 |  2521 | -134176    |   -0.39 |         0 |    11 |    0.99 |
## Interim ranked table (16 columns; first 20 of 40 finalists by HOLD Calmar; $/wk at equal-risk lots $1,200, carry-dropped; all REGIME)
| book | session | anchor | trigger | shape | L1M | L3M | L6M | HOLD | MID | PRE | X' | regime-conditioned | placebo | stack gain | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| GC KELT | nyam | {"b": 3, "e": 21, "n": 20, "m": 2.5} | KELT | stop usd600 R1.5 T120m (n 306) | +1182 | +1290 | +775 | +973 | +1120 | +28 | +542 | pooled; pre-2023 years 0 | p_book 0.12 (shift5/side/days x HOLD,L6M,stack gain; 100 worlds); family 1.00 (F=132286) | k*=5.00: HOLD dCalmar +0.102 L6M dCalmar +0.065; corr V0 -0.02/-0.01 V2 -0.02/-0.01 (daily/weekly) | FAILS: placebo p_book 0.12 > .10 | family p 1.00 > .10 | FLAG: no saved trade frame (/mnt/l2/l2vast/instr2_trades/<instrument>/<cell_id>.parquet) | REGIME (13y negative: 2 of 11 pre-2023 years positive, $-96859 over 2013-2023, calibration 0.96) |
| GC KELT | nyam | {"b": 3, "e": 21, "n": 20, "m": 2.5} | KELT | stop usd600 R1.5 T30m (n 308) | +986 | +1094 | +855 | +1000 | +1210 | +31 | +197 | pooled; pre-2023 years 0 | p_book 0.06 (shift5/side/days x HOLD,L6M,stack gain; 100 worlds); family 1.00 (F=132286) | k*=5.00: HOLD dCalmar +0.133 L6M dCalmar +0.071; corr V0 -0.01/0.01 V2 0.00/0.02 (daily/weekly) | FAILS: family p 1.00 > .10 | FLAG: no saved trade frame (/mnt/l2/l2vast/instr2_trades/<instrument>/<cell_id>.parquet) | REGIME (13y negative: 3 of 11 pre-2023 years positive, $-65902 over 2013-2023, calibration 0.96) |
| GC KELT | nyam | {"b": 3, "e": 21, "n": 20, "m": 2.5} | KELT | stop usd600 R1.5 T60m (n 308) | +1182 | +1290 | +876 | +988 | +1120 | +12 | +500 | pooled; pre-2023 years 0 | p_book 0.08 (shift5/side/days x HOLD,L6M,stack gain; 100 worlds); family 1.00 (F=132286) | k*=5.00: HOLD dCalmar +0.103 L6M dCalmar +0.073; corr V0 -0.02/-0.02 V2 -0.01/-0.01 (daily/weekly) | FAILS: family p 1.00 > .10 | FLAG: no saved trade frame (/mnt/l2/l2vast/instr2_trades/<instrument>/<cell_id>.parquet) | REGIME (13y negative: 3 of 11 pre-2023 years positive, $-87915 over 2013-2023, calibration 0.96) |
| GC KELT | nyam | {"b": 10, "e": 13, "n": 7, "m": 0.5} | KELT | stop atr2 R1 T120m (n 742) | +927 | +1310 | +1164 | +1053 | +969 | -18 | -530 | pooled; pre-2023 years 0 | p_book 0.15 (shift5/side/days x HOLD,L6M,stack gain; 100 worlds); family 1.00 (F=132286) | k*=5.00: HOLD dCalmar +0.249 L6M dCalmar +0.097; corr V0 0.00/-0.02 V2 0.00/-0.01 (daily/weekly) | FAILS: placebo p_book 0.15 > .10 | family p 1.00 > .10 | FLAG: no saved trade frame (/mnt/l2/l2vast/instr2_trades/<instrument>/<cell_id>.parquet) | REGIME (13y negative: 5 of 11 pre-2023 years positive, $-144171 over 2013-2023, calibration 0.96) |
| GC KELT | nyam | {"b": 10, "e": 13, "n": 20, "m": 0.5} | KELT | stop atr2 R1 T120m (n 782) | +650 | +1033 | +830 | +753 | +188 | -196 | -417 | pooled; pre-2023 years 0 | p_book 0.44 (shift5/side/days x HOLD,L6M,stack gain; 100 worlds); family 1.00 (F=132286) | k*=5.00: HOLD dCalmar +0.060 L6M dCalmar +0.069; corr V0 0.03/0.02 V2 0.03/0.04 (daily/weekly) | FAILS: placebo p_book 0.44 > .10 | family p 1.00 > .10 | FLAG: no saved trade frame (/mnt/l2/l2vast/instr2_trades/<instrument>/<cell_id>.parquet) | REGIME (13y negative: 2 of 11 pre-2023 years positive, $-189592 over 2013-2023, calibration 0.96) |
| GC KELT | nyam | {"b": 10, "e": 13, "n": 7, "m": 0.5} | KELT | stop atr2 R2 T60m (n 759) | +944 | +1582 | +1184 | +1147 | +1069 | -239 | -500 | pooled; pre-2023 years 0 | p_book 0.30 (shift5/side/days x HOLD,L6M,stack gain; 100 worlds); family 1.00 (F=132286) | k*=5.00: HOLD dCalmar +0.079 L6M dCalmar +0.099; corr V0 0.03/0.04 V2 0.02/0.05 (daily/weekly) | FAILS: placebo p_book 0.30 > .10 | family p 1.00 > .10 | FLAG: no saved trade frame (/mnt/l2/l2vast/instr2_trades/<instrument>/<cell_id>.parquet) | REGIME (13y negative: 3 of 11 pre-2023 years positive, $-208628 over 2013-2023, calibration 0.97) |
| GC VWR | nyam | {"b": 1, "k": 1.5} | VWR | stop atr6 R2 T60m (n 559) | +397 | +1057 | +1884 | +1258 | +1513 | -66 | -146 | pooled; pre-2023 years 0 | p_book 0.43 (shift5/side/days x HOLD,L6M,stack gain; 100 worlds); family 1.00 (F=132286) | k*=3.14: HOLD dCalmar +0.048 L6M dCalmar +0.099; corr V0 -0.01/0.05 V2 -0.01/0.05 (daily/weekly) | FAILS: placebo p_book 0.43 > .10 | family p 1.00 > .10 | FLAG: no saved trade frame (/mnt/l2/l2vast/instr2_trades/<instrument>/<cell_id>.parquet) | REGIME (13y negative: 0 of 11 pre-2023 years positive, $-47463 over 2013-2023, calibration 0.98) |
| GC VWR | pre | {"b": 1, "k": 1.5} | VWR | stop atr4 R2 T120m (n 364) | -555 | +308 | +74 | +1018 | +2449 | +498 | -32 | pooled; pre-2023 years 0 | p_book 0.52 (shift5/side/days x HOLD,L6M,stack gain; 100 worlds); family 1.00 (F=132286) | k*=5.00: HOLD dCalmar +0.065 L6M dCalmar +0.006; corr V0 0.03/0.11 V2 0.04/0.12 (daily/weekly) | FAILS: placebo p_book 0.52 > .10 | family p 1.00 > .10 | FLAG: no saved trade frame (/mnt/l2/l2vast/instr2_trades/<instrument>/<cell_id>.parquet) | REGIME (13y negative: 3 of 11 pre-2023 years positive, $-80000 over 2013-2023, calibration 0.99) |
| GC VWR | pre | {"b": 1, "k": 1.5} | VWR | stop atr4 R1.5 T120m (n 366) | -555 | +177 | +117 | +904 | +2278 | +419 | -55 | pooled; pre-2023 years 0 | p_book 0.60 (shift5/side/days x HOLD,L6M,stack gain; 100 worlds); family 1.00 (F=132286) | k*=5.00: HOLD dCalmar +0.059 L6M dCalmar +0.010; corr V0 0.03/0.09 V2 0.04/0.11 (daily/weekly) | FAILS: placebo p_book 0.60 > .10 | family p 1.00 > .10 | FLAG: no saved trade frame (/mnt/l2/l2vast/instr2_trades/<instrument>/<cell_id>.parquet) | REGIME (13y negative: 3 of 11 pre-2023 years positive, $-82294 over 2013-2023, calibration 0.98) |
| GC PB | asia | {"b": 2, "e": 34, "m": 1.0} | PB | stop usd2400 R1.5 T120m (n 2668) | +305 | +393 | +1766 | +1877 | +377 | -70 | -4 | pooled; pre-2023 years 0 | p_book 0.21 (shift5/side/days x HOLD,L6M,stack gain; 100 worlds); family 1.00 (F=132286) | k*=5.00: HOLD dCalmar +0.162 L6M dCalmar +0.147; corr V0 0.04/0.08 V2 0.04/0.06 (daily/weekly) | FAILS: placebo p_book 0.21 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS 115/wk, p_rand 0.01, 12m: OOS -93/wk, p_rand 0.02) | FLAG: no saved trade frame (/mnt/l2/l2vast/instr2_trades/<instrument>/<cell_id>.parquet) | REGIME (13y negative: 2 of 11 pre-2023 years positive, $-160130 over 2013-2023, calibration 0.97) |
| GC DON | asia | {"b": 10, "n": 40} | DON | stop atr6 R1 T120m (n 248) | +106 | +568 | +358 | +759 | +1574 | +140 | +14 | pooled; pre-2023 years 0 | p_book 0.18 (shift5/side/days x HOLD,L6M,stack gain; 100 worlds); family 1.00 (F=132286) | k*=5.00: HOLD dCalmar +0.147 L6M dCalmar +0.030; corr V0 0.01/0.01 V2 0.00/-0.01 (daily/weekly) | FAILS: placebo p_book 0.18 > .10 | family p 1.00 > .10 | FLAG: no saved trade frame (/mnt/l2/l2vast/instr2_trades/<instrument>/<cell_id>.parquet) | REGIME (13y negative: 4 of 11 pre-2023 years positive, $-31584 over 2013-2023, calibration 0.98) |
| GC SUPT | nyam | {"b": 5, "n": 14, "m": 3.0} | SUPT | stop atr6 R1 T60m (n 611) | +578 | +949 | +775 | +1216 | +1171 | -343 | +353 | NOW-ONLY (REGIME) | p_book 0.17 (shift5/side/days x HOLD,L6M,stack gain; 100 worlds); family 1.00 (F=132286) | k*=5.00: HOLD dCalmar +0.262 L6M dCalmar +0.065; corr V0 0.03/-0.07 V2 0.03/-0.05 (daily/weekly) | FAILS: tolerant gate (PRE mean -343 < -0.5 MDE (-218)) | placebo p_book 0.17 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS 8/wk, p_rand 0.70, 12m: OOS -75/wk, p_rand 0.91) | FLAG: no saved trade frame (/mnt/l2/l2vast/instr2_trades/<instrument>/<cell_id>.parquet) | REGIME (13y negative: 2 of 11 pre-2023 years positive, $-68929 over 2013-2023, calibration 0.98) |
| GC SUPT | nyam | {"b": 5, "n": 7, "m": 4.0} | SUPT | stop atr2 R1.5 T60m (n 417) | +505 | +858 | +696 | +320 | +232 | +287 | +629 | pooled; pre-2023 years 0 | p_book 0.37 (shift5/side/days x HOLD,L6M,stack gain; 100 worlds); family 1.00 (F=132286) | k*=0.00: HOLD dCalmar +0.000 L6M dCalmar +0.000; corr V0 0.00/-0.02 V2 0.01/0.01 (daily/weekly) | FAILS: placebo p_book 0.37 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS -106/wk, p_rand 0.86, 12m: OOS -31/wk, p_rand 0.64) | stack Calmar not up at equal risk (HOLD/L6M, carry dropped) | FLAG: no saved trade frame (/mnt/l2/l2vast/instr2_trades/<instrument>/<cell_id>.parquet) | REGIME (13y negative: 3 of 11 pre-2023 years positive, $-58879 over 2013-2023, calibration 0.96) |
| GC VWR | nyam | {"b": 5, "k": 1.5} | VWR | stop usd2400 R2 T120m (n 305) | +633 | +1371 | +1363 | +1256 | +1204 | +123 | -49 | pooled; pre-2023 years 0 | p_book 0.08 (shift5/side/days x HOLD,L6M,stack gain; 100 worlds); family 1.00 (F=132286) | k*=5.00: HOLD dCalmar +0.265 L6M dCalmar +0.114; corr V0 0.05/0.04 V2 0.06/0.04 (daily/weekly) | FAILS: family p 1.00 > .10 | FLAG: no saved trade frame (/mnt/l2/l2vast/instr2_trades/<instrument>/<cell_id>.parquet) | REGIME (13y negative: 2 of 11 pre-2023 years positive, $-14441 over 2013-2023, calibration 0.98) |
| GC VWR | pre | {"b": 1, "k": 1.5} | VWR | stop atr4 R1 T120m (n 370) | -162 | +326 | +58 | +907 | +2045 | +327 | -182 | pooled; pre-2023 years 0 | p_book 0.44 (shift5/side/days x HOLD,L6M,stack gain; 100 worlds); family 1.00 (F=132286) | k*=5.00: HOLD dCalmar +0.059 L6M dCalmar +0.005; corr V0 0.03/0.09 V2 0.05/0.11 (daily/weekly) | FAILS: placebo p_book 0.44 > .10 | family p 1.00 > .10 | FLAG: no saved trade frame (/mnt/l2/l2vast/instr2_trades/<instrument>/<cell_id>.parquet) | REGIME (13y negative: 3 of 11 pre-2023 years positive, $-75922 over 2013-2023, calibration 0.98) |
| GC VWR | pre | {"b": 1, "k": 1.5} | VWR | stop atr3 R1 T120m (n 375) | -105 | +260 | +58 | +575 | +1515 | +138 | +61 | pooled; pre-2023 years 0 | p_book 0.50 (shift5/side/days x HOLD,L6M,stack gain; 100 worlds); family 1.00 (F=132286) | k*=5.00: HOLD dCalmar +0.124 L6M dCalmar +0.005; corr V0 0.04/0.06 V2 0.05/0.07 (daily/weekly) | FAILS: placebo p_book 0.50 > .10 | family p 1.00 > .10 | FLAG: no saved trade frame (/mnt/l2/l2vast/instr2_trades/<instrument>/<cell_id>.parquet) | REGIME (13y negative: 2 of 11 pre-2023 years positive, $-88826 over 2013-2023, calibration 0.96) |
| GC PB | asia | {"b": 2, "e": 34, "m": 1.0} | PB | stop usd2400 R2 T120m (n 2649) | +305 | +393 | +1354 | +2076 | +916 | -76 | -4 | pooled; pre-2023 years 0 | p_book 0.12 (shift5/side/days x HOLD,L6M,stack gain; 100 worlds); family 1.00 (F=132286) | k*=5.00: HOLD dCalmar +0.183 L6M dCalmar +0.113; corr V0 0.04/0.06 V2 0.04/0.05 (daily/weekly) | FAILS: placebo p_book 0.12 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS 115/wk, p_rand 0.01, 12m: OOS -93/wk, p_rand 0.02) | FLAG: no saved trade frame (/mnt/l2/l2vast/instr2_trades/<instrument>/<cell_id>.parquet) | REGIME (13y negative: 2 of 11 pre-2023 years positive, $-158801 over 2013-2023, calibration 0.97) |
| GC SUPT | nyam | {"b": 5, "n": 10, "m": 3.0} | SUPT | stop atr4 R1.5 T60m (n 596) | +807 | +1178 | +815 | +868 | +773 | -196 | +423 | pooled; pre-2023 years 0 | p_book 0.24 (shift5/side/days x HOLD,L6M,stack gain; 100 worlds); family 1.00 (F=132286) | k*=5.00: HOLD dCalmar +0.068 L6M dCalmar +0.068; corr V0 0.02/-0.08 V2 0.02/-0.08 (daily/weekly) | FAILS: placebo p_book 0.24 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS -27/wk, p_rand 0.78, 12m: OOS 45/wk, p_rand 0.56) | FLAG: no saved trade frame (/mnt/l2/l2vast/instr2_trades/<instrument>/<cell_id>.parquet) | REGIME (13y negative: 3 of 11 pre-2023 years positive, $-87767 over 2013-2023, calibration 0.97) |
| GC SUPT | nyam | {"b": 5, "n": 14, "m": 3.0} | SUPT | stop atr3 R2 T60m (n 651) | +245 | +616 | +605 | +1023 | +1362 | -222 | +698 | pooled; pre-2023 years 0 | p_book 0.16 (shift5/side/days x HOLD,L6M,stack gain; 100 worlds); family 1.00 (F=132286) | k*=5.00: HOLD dCalmar +0.132 L6M dCalmar +0.050; corr V0 0.03/-0.04 V2 0.03/-0.04 (daily/weekly) | FAILS: placebo p_book 0.16 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS 8/wk, p_rand 0.70, 12m: OOS -75/wk, p_rand 0.91) | FLAG: no saved trade frame (/mnt/l2/l2vast/instr2_trades/<instrument>/<cell_id>.parquet) | REGIME (13y negative: 3 of 11 pre-2023 years positive, $-131993 over 2013-2023, calibration 0.96) |
| GC SUPT | nyam | {"b": 5, "n": 14, "m": 3.0} | SUPT | stop atr3 R1 T60m (n 658) | +386 | +842 | +626 | +848 | +1598 | -112 | +281 | pooled; pre-2023 years 0 | p_book 0.18 (shift5/side/days x HOLD,L6M,stack gain; 100 worlds); family 1.00 (F=132286) | k*=5.00: HOLD dCalmar +0.082 L6M dCalmar +0.052; corr V0 0.02/0.00 V2 0.02/0.01 (daily/weekly) | FAILS: placebo p_book 0.18 > .10 | family p 1.00 > .10 | walk-forward not positive (6m: OOS 8/wk, p_rand 0.70, 12m: OOS -75/wk, p_rand 0.91) | FLAG: no saved trade frame (/mnt/l2/l2vast/instr2_trades/<instrument>/<cell_id>.parquet) | REGIME (13y negative: 3 of 11 pre-2023 years positive, $-127368 over 2013-2023, calibration 0.93) |
Files: /mnt/l2/l2vast/ds3_t2/GC_screen.parquet (132,286 cells), GC_stage2.pkl, GC_oos13.pkl, GC_family.pkl; trade frames /mnt/l2/l2vast/instr2_trades/GC/ (40 finalists); code l2vast/ds3/code/t2s4a/.

## GC family null result (S4a, appended 2026-11-05 ~21:40Z; canonical-bracket family: 448 signal sets x 5 sessions x {stop ATR3, stop $1,200} x R1.5 x T60 = 4,200 cells with >= 100 trades; 100 worlds each of random side at the real times and forward shift5; same gate as the screen)
Real: max HOLD mean over the cells $1,407/wk, max L6M Calmar 0.654, **493 of 4,200 cells pass the tolerant gate**. Null (random side): max HOLD mean median $1,661, 95th pct $2,412 (p of the real max 0.86); max L6M Calmar p 0.71; gate passers median 250.5 (**p of the real count 0.0099: no world reaches 493**). Null (forward shift5): max HOLD median $1,477, p95 $1,973 (p 0.58); Calmar p 0.99; gate passers median 394 (**p 0.0099**).
Reading: no single GC cell is better than the best of a random-side family (the max statistic is inside both nulls); but the NUMBER of cells passing the tolerant gate (493) exceeds every null world, i.e. the 2026 gold trend regime that the Keltner / Supertrend flips (and the other trend families) exploit is real in the 2023-2026 data, and it is not a single parameter spike. It is also absent before 2023: all 40 finalists lose over 2013-2023 (percent frame, calibrated). Conclusion stays REGIME (2026-only), not a book; a persistent gold book would need the pre-2023 years to be at least non-negative.
Note: the full 141,120-cell max-T (63 brackets per signal set) was not run (about 14 h per world set); finalists carry the Bonferroni family p over 132,286 cells from the shared evaluator. Pending (parked for the blind-week order): Z2 walk-forward selector over the full grid (wf_grid.py), GC native books (Addendum A), T-FIND step 2.

## UPDATE (S4a, 2026-11-06): Z2 purged walk-forward selector on the whole generic GC grid (own parameter choice)
Z2 wf_selector.py (monthly decisions from the previous 26 or 52 weeks, purge 1 week, eligibility mean > 0 / older-half tolerance / >= 50% positive months, choice = best trailing Sharpe; top-1 and top-3 equal-weight), weekly matrix of every GC cell with >= 100 trades (23,101-26,775 eligible cells per session), OOS 2024-01..2026-10, 200 random-cell and 200 permutation placebos; /mnt/l2/l2vast/ds3_t2/GC_wfres.pkl.
| session | lookback (wk) | pick | eligible candidates | OOS mean $/wk 2024-26 | maxDD $ | L6M $/wk | HOLD $/wk | PRE $/wk | p vs random choice | p vs permuted | p boot (mean<=0) | stack Calmar gain HOLD k=1 |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| asia | 26 | top1 | 23393 | 251 | 29231 | -1775 | -32 | 121 | 0.01 | 0.01 | 0.10 | 0.001 |
| asia | 26 | top3 | 23393 | -14 | 21716 | -1281 | -188 | -47 | 0.01 | 0.12 | 0.50 | -0.005 |
| asia | 52 | top1 | 23393 | -276 | 46419 | -2058 | -183 | -131 | 0.45 | 0.75 | 0.82 | -0.000 |
| asia | 52 | top3 | 23393 | -71 | 25653 | -1797 | -78 | 31 | 0.07 | 0.37 | 0.58 | 0.002 |
| london | 26 | top1 | 26775 | -162 | 46983 | -581 | -255 | -152 | 0.04 | 0.26 | 0.83 | 0.005 |
| london | 26 | top3 | 26775 | -270 | 48510 | -81 | -339 | -276 | 0.01 | 0.46 | 0.97 | 0.002 |
| london | 52 | top1 | 26775 | -24 | 17063 | 102 | 22 | -60 | 0.01 | 0.18 | 0.54 | -0.010 |
| london | 52 | top3 | 26775 | -129 | 20632 | 110 | -118 | -160 | 0.01 | 0.31 | 0.78 | 0.002 |
| pre | 26 | top1 | 19035 | -216 | 43780 | 236 | -84 | -183 | 0.77 | 0.63 | 0.84 | -0.005 |
| pre | 26 | top3 | 19035 | -207 | 38473 | 370 | -92 | -298 | 0.90 | 0.70 | 0.94 | -0.004 |
| pre | 52 | top1 | 19035 | -37 | 22132 | -177 | -86 | -29 | 0.44 | 0.30 | 0.56 | -0.009 |
| pre | 52 | top3 | 19035 | -66 | 18328 | -51 | -34 | -150 | 0.57 | 0.34 | 0.65 | -0.008 |
| nyam | 26 | top1 | 23101 | -301 | 53182 | 176 | -232 | -468 | 0.77 | 0.84 | 0.98 | -0.027 |
| nyam | 26 | top3 | 23101 | -253 | 46463 | 74 | -25 | -493 | 0.85 | 0.82 | 0.99 | -0.014 |
| nyam | 52 | top1 | 23101 | -136 | 29594 | -61 | 33 | -415 | 0.53 | 0.64 | 0.80 | 0.001 |
| nyam | 52 | top3 | 23101 | -70 | 22305 | 443 | 205 | -263 | 0.26 | 0.42 | 0.77 | -0.004 |
| nypm | 26 | top1 | 20459 | -103 | 25150 | -782 | -29 | -214 | 0.14 | 0.14 | 0.70 | 0.012 |
| nypm | 26 | top3 | 20459 | -156 | 25703 | -618 | -154 | -230 | 0.04 | 0.24 | 0.92 | 0.003 |
| nypm | 52 | top1 | 20459 | -331 | 42378 | -661 | -427 | -234 | 0.64 | 0.86 | 0.99 | -0.013 |
| nypm | 52 | top3 | 20459 | -246 | 31429 | -416 | -235 | -159 | 0.29 | 0.60 | 0.98 | -0.003 |
**Plain sentence: the walk-forward choice of GC parameters does not work out of sample: 19 of the 20 session x lookback x top-k selectors have a NEGATIVE out-of-sample mean per week over 2024-2026 (the one positive, asia 26-week top-1 +$251 a week, has L6M -$1,775 and HOLD -$32 and a bootstrap p of 0.10); the small p-values against a random cell (London, asia) only say the selector picks less bad cells than a random one, not that it makes money, and none has a positive stack Calmar gain beyond +0.012 at k=1. Consistent with the REGIME label: GC trend cells paid only in 2026.**

## GC-DISSECT (ZL-1, 2026-11-06; prereg l2vast/ds3/prereg/GC_DISSECT_prereg.md; code l2vast/ds3/code/gcdis/; data /mnt/l2/l2vast/gcdis/) - what drives S4a's tolerant-gate count excess (493, p .0099)

**GC: the thing it does in 2023-26 is that Keltner (excess +171 passers) and Supertrend (+57) trend flips in NY-AM (+130) and the 08:30 pre session (+114) pass the tolerant gate far more often than the random-side null (493 real vs null median 251, maximum 288 over 24 worlds), but the dominant cluster's cleanest strong representative (KELT b5 e34 n14 m0.5, NY-AM, stop ATR3 R1.5 T60) pays ONLY in 2026 (+19781 $ at screen lots; 2023 -24044, 2024 +107, 2025 -10536; 2013-2022 -137670; 2 of 10 pre-2023 years positive), and its 2026 profit is the short side (+24372 vs long -4591) of a net-down year (gold -3.4% on the continuous contract) with the highest volatility since 2013 (28.6% annualised, 5-min abs move 6.7 bp): a pure forced-short book at the same entry times earned +26924 in 2026 and a forced-long -26722, while trend persistence did not change (VR12 0.996 in 2026, 1.024 in 2023); gold's own trailing variance ratio, volatility rank, trend-day share and drift/vol ratio do not predict when it pays (walk-forward family p >= 0.82); the book is REGIME (2026 short-drift + vol), not a trend book, and it does not clear: placebo p_book 0.82, family p 1.00 (F=132,286), walk-forward not positive, stack Calmar not up at any weight (k* = 0).**

### 1. Where the excess comes from (reproduction: 4200 cells, 493 passers = S4a's 493; 24 random-side worlds seeds 5000..5023: passers median 251, min 230, max 288)
| family | real passers | null mean | excess |
|--|--|--|--|
| KELT | 314 | 143.0 | +171.0 |
| SUPT | 122 | 64.6 | +57.4 |
| VWR | 11 | 3.8 | +7.2 |
| MOM | 13 | 6.4 | +6.6 |
| HMAV | 7 | 3.8 | +3.2 |
| PDF | 2 | 0.1 | +1.9 |

| session | real passers | null mean | excess |
|--|--|--|--|
| nyam | 197 | 67.5 | +129.5 |
| pre | 230 | 115.6 | +114.4 |
| asia | 30 | 17.1 | +12.9 |
| london | 9 | 16.6 | -7.6 |
| nypm | 27 | 36.0 | -9.0 |

Bracket: stop ATR3 240 real vs 109 null; stop $1,200 253 vs 144. Largest (family, session) excesses: KELT|pre 157 vs 64.6 (x2.4); KELT|nyam 113 vs 37.2 (x3.0); SUPT|nyam 67 vs 19.2 (x3.5); SUPT|pre 42 vs 29.9 (x1.4); MOM|pre 13 vs 3.2 (x4.1). 96% of the excess is Keltner + Supertrend flips, 100% is NY-AM + 08:30 pre.

### 2. Clusters of the 493 passers (weekly P&L 2023-04..2026-10, average linkage on 1-corr, cut at corr 0.6)
| cluster | size | mean within-corr | families | sessions | stop bracket | median HOLD $/wk |
|--|--|--|--|--|--|--|
| 44 | 35 | 0.67 | {'SUPT': 20, 'KELT': 15} | {'nyam': 35} | {"('atr', 3.0)": 35} | 354 |
| 11 | 33 | 0.68 | {'KELT': 33} | {'pre': 33} | {"('atr', 3.0)": 24, "('usd', 1200.0)": 9} | 228 |
| 46 | 32 | 0.67 | {'KELT': 28, 'SUPT': 4} | {'nyam': 32} | {"('atr', 3.0)": 32} | 264 |
| 21 | 25 | 0.66 | {'KELT': 21, 'SUPT': 4} | {'pre': 25} | {"('usd', 1200.0)": 24, "('atr', 3.0)": 1} | 270 |
| 17 | 24 | 0.69 | {'KELT': 18, 'SUPT': 6} | {'pre': 24} | {"('usd', 1200.0)": 24} | 356 |
| 10 | 20 | 0.73 | {'KELT': 13, 'SUPT': 7} | {'pre': 20} | {"('usd', 1200.0)": 19, "('atr', 3.0)": 1} | 187 |

95 clusters in total; the passers are NOT one pattern but several correlated families of the same trade (flip entries on 5-15 min bars in the same sessions); the dominant cluster (35 cells: Supertrend and Keltner, NY-AM, stop ATR3) has mean within-cluster correlation 0.67. Plateau score (share of one-step parameter neighbours that also pass) over all 448 passers' sets: median 0.50, 123 cells >= 0.70.

### 3. Representatives
Frozen rule (highest plateau, ties highest HOLD): **SUPT b2 n10 m4.0 NY-AM stop ATR3** (plateau 1.00 on only 4 neighbours, HOLD $38/wk at screen lots) - degenerate: the rule picks a borderline cell whose neighbours also barely pass. DISCLOSED secondary (max HOLD among dominant-cluster members with plateau >= .70 and >= 5 neighbours): **KELT b5 e34 n14 m0.5 NY-AM stop ATR3 R1.5 T60** (plateau 0.83 over 6 neighbours, HOLD $456/wk, L6M $689/wk at screen lots). Both are evaluated; the analysis below follows the secondary.

### 4. Yearly table 2013-2026 of the secondary representative (percent frame before 2023-04, roll days dropped; screen lots = min($1,200 / stop, 6); drift books = same entry times, side forced)
| year | trades | net $ | mean ticks | long $ | short $ | weeks positive | forced-long $ | forced-short $ |
|--|--|--|--|--|--|--|--|--|
| 2013 | 191 | -706 | +3.3 | +2111 | -2817 | 0.45 | -9499 | -16761 |
| 2014 | 187 | -7030 | -0.3 | -13336 | +6306 | 0.41 | -26869 | +8823 |
| 2015 | 188 | -7632 | -1.3 | -7256 | -376 | 0.38 | -20232 | -7471 |
| 2016 | 221 | -8816 | -2.2 | -10036 | +1220 | 0.46 | -30520 | -7909 |
| 2017 | 236 | -42309 | -4.6 | -18537 | -23772 | 0.29 | -19021 | -38205 |
| 2018 | 187 | -39048 | -5.7 | -21559 | -17490 | 0.27 | -30345 | -14039 |
| 2019 | 219 | -38458 | -5.1 | -14273 | -24185 | 0.25 | -10849 | -26882 |
| 2020 | 229 | +2962 | +5.3 | +1314 | +1649 | 0.43 | -13580 | -11158 |
| 2021 | 204 | +5115 | +1.7 | +5980 | -864 | 0.50 | -4195 | -13788 |
| 2022 | 225 | -1748 | -1.2 | -1839 | +91 | 0.56 | -9660 | -1938 |
| 2023 | 227 | -24044 | -6.2 | -13717 | -10327 | 0.37 | -20819 | -2893 |
| 2024 | 223 | +107 | -0.5 | -3185 | +3292 | 0.50 | -21033 | +2277 |
| 2025 | 209 | -10536 | -5.2 | +90 | -10626 | 0.53 | +7986 | -21212 |
| 2026 | 182 | +19781 | +14.8 | -4591 | +24372 | 0.60 | -26722 | +26924 |
Dominant-cluster top-10 by plateau: 2013-2022 total $-137k to $-216k each, 1-3 of 10 pre-2023 years positive, 2023-2026 total $-31k to +$2k each. Calibration of the 1-min kernel against the tick-built 1-s path was measured by S4a for its 40 finalists (weekly correlation 0.93-1.00); this representative was not among them, so its pre-2023 table is INFORMAL (same pipeline, not separately calibrated).

### 5. What changed (GC 1-min closes, label days, percent frame)
| year | days | vol ann % | 5-min abs bp | VR(6) z | VR(12) z | VR(36) z | lag-1 corr 30-min | trend-day share | gold return % |
|--|--|--|--|--|--|--|--|--|--|
| 2013 | 242 | 22.1 | 4.48 | 0.970 (-1.2) | 0.973 (-0.8) | 1.052 (1.0) | -0.014 | 0.48 | -28.5 |
| 2014 | 241 | 14.6 | 3.30 | 0.928 (-3.5) | 0.937 (-2.2) | 0.970 (-0.7) | +0.000 | 0.39 | -0.4 |
| 2015 | 248 | 13.9 | 3.41 | 0.986 (-0.6) | 0.997 (-0.1) | 1.075 (1.6) | +0.016 | 0.40 | -11.6 |
| 2016 | 248 | 15.9 | 3.79 | 0.997 (-0.1) | 1.020 (0.6) | 1.111 (2.0) | +0.019 | 0.40 | +8.6 |
| 2017 | 247 | 10.4 | 2.59 | 0.951 (-3.0) | 0.952 (-2.0) | 0.977 (-0.6) | -0.012 | 0.49 | +13.3 |
| 2018 | 248 | 10.0 | 2.59 | 0.954 (-2.9) | 0.974 (-1.1) | 1.026 (0.7) | +0.005 | 0.41 | -1.6 |
| 2019 | 248 | 12.5 | 2.80 | 0.960 (-1.9) | 0.980 (-0.7) | 1.027 (0.6) | +0.008 | 0.41 | +18.3 |
| 2020 | 249 | 21.3 | 5.01 | 0.951 (-1.9) | 0.960 (-1.1) | 1.035 (0.6) | +0.021 | 0.42 | +25.1 |
| 2021 | 248 | 13.9 | 3.55 | 1.020 (0.9) | 1.022 (0.7) | 1.039 (0.8) | +0.028 | 0.38 | -3.7 |
| 2022 | 248 | 15.3 | 3.84 | 0.991 (-0.5) | 1.021 (0.8) | 1.066 (1.5) | +0.011 | 0.44 | -0.0 |
| 2023 | 247 | 13.1 | 3.11 | 1.020 (1.0) | 1.024 (0.8) | 1.126 (2.7) | -0.009 | 0.40 | +13.2 |
| 2024 | 249 | 16.3 | 3.52 | 1.013 (0.7) | 1.037 (1.4) | 1.102 (2.4) | -0.000 | 0.47 | +27.4 |
| 2025 | 248 | 20.6 | 4.67 | 1.001 (0.1) | 1.014 (0.6) | 1.019 (0.4) | +0.009 | 0.46 | +64.1 |
| 2026 | 197 | 28.6 | 6.65 | 0.999 (-0.0) | 0.996 (-0.1) | 0.968 (-0.5) | +0.016 | 0.48 | -3.4 |
Rank correlation across the 14 years between each indicator and the representative's yearly P&L: vol_ann_pct +0.75, abs5_bp +0.75, VR6 +0.30, VR12 +0.20, VR36 +0.02, ac30 +0.45, trend_day_share +0.01, gold_ret_pct -0.28 (n = 14, rank only). Volatility and the 5-min move size line up with the P&L (+0.75); variance ratios, lag-1 autocorrelation and trend-day share do not, and VR is within noise of 1 in every year from 2021 on: nothing about persistence changed in 2023; what changed is volatility, rising from 13% (2023) to 29% (2026). The central-bank-bid hypothesis cannot be tested with owned data (no reserves series); it is named, not tested.

### 6. Regime awareness (one-sided gates on gold's own trailing indicators, expanding walk-forward 2017-2026, 2-week purge, 2,000 within-year permutations, family max over the 4)
| indicator | share of weeks on | uplift $/wk vs always-on | 2017-21 | 2022-26 | gated mean / maxDD | always-on mean / maxDD | p cell | p family |
|--|--|--|--|--|--|--|--|--|
| VR12_20d | 0.45 | +123 | +283 | -45 | -128 / 83356 | -251 / 155206 | 0.702 | 1.000 |
| volpct_60d | 0.44 | +217 | +425 | -0 | -34 / 47901 | -251 / 155206 | 0.793 | 0.818 |
| trendshare_20d | 0.46 | +159 | +325 | -14 | -92 / 59207 | -251 / 155206 | 0.617 | 1.000 |
| absret_over_vol_60d | 0.33 | +178 | +305 | +45 | -73 / 45787 | -251 / 155206 | 0.348 | 0.994 |

Verdict: not regime-aware (no indicator has family p <= .10 with a positive uplift in both OOS halves); the gates cut the loss mainly by being off in 2017-2019, not by anticipating 2026.

### 7. Evaluator and stack (instr2_eval.evaluate, 100 placebo worlds, family F = 132,286, integer equal-risk lots - the screen used fractional lots, so $ differ)
| book | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | HOLD maxDD | corr V0/V2 daily | stack k* | placebo p_book | walk-forward 6m / 12m OOS $/wk | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| SUPT b2 n10 m4.0 NY-AM (frozen) | -92 | +34 | +34 | -366 | -247 | +27 | -190 | +148 | 31798 | 0.02 / 0.01 | 0.00 | 0.96 | -520 / -413 | FAILS: tolerant gate (NOW-ONLY fails (L3M/L6M mean not both > 0)) ; persistence 50% <= 60% ; placebo p_book 0.96 > .10 ; family p 1.00 > .10 ; walk-forward not positive (6m: OOS -520/wk, p_rand 1.00,  |
| KELT b5 e34 n14 m0.5 NY-AM (secondary) | +249 | +269 | +269 | +1004 | +557 | +37 | -270 | -204 | 25176 | 0.03 / 0.02 | 0.00 | 0.82 | +169 / -17 | FAILS: placebo p_book 0.82 > .10 ; family p 1.00 > .10 ; walk-forward not positive (6m: OOS 169/wk, p_rand 0.13, 12m: OOS -17/wk, p_rand 0.52) ; stack Calmar not up at equal risk (HOLD/L6M, carry drop |

Sizing of the secondary at the real contract (2023-26 trades, n 783): equal-risk lots median 1.0 (IQR 1.0-2.0), risk per GC lot (stop distance) median $1040; rounding to integer GC lots changes the realised risk by more than 25% in 45% of trades (GC integer-lot risk p10-p90 $936-$2490); with MGC (10 oz, tick $1) contracts = round(10 x lots), median 10 contracts, risk p10-p90 $936-$2490; participation cap binds in 0% of trades. MGC fee is unmeasured (the $4.84 GC fee per contract is NOT assumed for MGC).

Label: **REGIME** (2026 short-drift + volatility; 10-year pre-2023 negative; placebo, family, walk-forward and stack tests fail); WATCH spec: autopilot/WATCH_GC_TREND_SPEC.md.
