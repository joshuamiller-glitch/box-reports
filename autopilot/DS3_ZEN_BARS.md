# DS3_ZEN_BARS - the Zen entry on every bar type, lines and all (D3ZBR, T-ZEN family BARS, 2026-10-28)

**Verdict line: best bar type for the ZEN entry: 1-minute time bars, nothing beats them.** Across 34 bar types x 5 entry cells x 2 regime variants x 4 line options x 2 brackets x 2 flat rules (N = 5,440 + 160 control rows = 5,600 listed, 4,432 distinct rows with n >= 100 outside the control), no bar type beats 1-minute time bars on identical signals by more than the paired MDE80 (model bracket: median paired MDE80 1.68 pt/trade, mean paired difference +0.21; 17 of 2,212 distinct model-bracket rows exceed their paired MDE80 with a positive CI, none survives the white reality check: best row studentised t = 3.34, p(best of N) = 0.36, per-cell reality-check p >= 0.36 for every row). The 30 best PRE rows (all 60/60 comparator brackets, effect +5.8 to +10.8 pt/trade vs random-in-regime on the same bar type, MDE80 7-17) lost 74% of their effect in the one HOLD look (mean +1.9 pt/trade); G6 passed 2 of 30, G8 0 of 30, G5 0 of 30 (every PRE effect is below its own MDE80 or its CI includes 0); no row passes G1-G9, so none is a CANDIDATE (G10, the 1-s/L2 replay, was not run). Bar-weighted placebo pools flatter the fast types (range, Renko, Kagi: +0.2 to +0.5 pt/trade pooled over E1-E5 at the model bracket); with a minute-deduplicated pool the same types read -0.2 to -0.6. Time bars 1m: pooled E1-E5 effect -0.26 pt/trade (mean net -2.06 pts, 55.7% win vs 64.5% break-even): the ZEN entry has no edge on any bar type at the model's 15-pt stop.

**K5 NT8 identity-check statement.** No bar type passed, so no live bar type is recommended. For the record, a spec for any bar type from this table would carry: type, parameter (library name, e.g. tick_1000 = 1000 ticks, volume_1200, dollar_300M = $300M notional, range_40 = 40 ticks, renko_22 = 22 ticks, imbal_130 = tick-rule signed-volume imbalance of 130 contracts, kagi_32 = 32-tick reversal, line break = 3-line on 1-min closes, ha_1m = Heikin-Ashi on 1-minute time bars) and the identity check "library tick-built bar vs NT8 historical/Rithmic bar on the overlap window (bar count per day, open/high/low/close and bar close time of every bar of a 5-day window; max |difference| = 0 ticks and identical count required)". NT8's own historical build is NOT on this box and the identity check has NOT been run: it must be run by the user in NT8 before any non-time bar type could be used (Renko, range, tick, volume, Kagi and imbalance bars on a Rithmic feed can differ from the historical tick build; imbalance and Kagi bars have no NT8-native type: they would need custom NinjaScript). HA and line-break bars are derived from time bars and need no NT8 build beyond their base bars.

## 0. Counts at a glance
- Listed N 5,600 = 34 types x 160 cells + 160 time_1m control cells; scored 5,600 (0 skipped); 908 rows are duplicates by construction (E4 with a replaced line = E1 with the same line: 840 incl. the control; time_1m 5x = 5-min control: 80; minus 12 counted in both) and are reported but not selected twice; 5,408 rows have n >= 100.
- Unit tests bf_test.py 10/10 (events of time_1m, tick_1000, renko_22, ha_1m, linebreak3, time_3m unchanged when all later bars are deleted; time_1m regime == Z.regimes R1; time_1m pool == candidate rows; U lookup == Z.simulate). Reproduction: the time_1m E1 cell (n 1,551, effect -0.0783, MDE80 0.880) equals the LINES_C cell C|time_1m|EMA_200_close|tol5|R1 exactly.
- Holdout looks used: 1 (HOLD, 60 rows = 30 + 30 time_1m companions) + 1 (X), logged in out/zen/bars_fam/looks.jsonl and DECISIONS.md.


## 1. K4 counts (descriptive, no P&L)

Source: out/zen/bars/_k4_counts.csv (D3ZN0, full sample 2023-02..2026-02-06) re-stated, plus out/zen/bars_fam/k4_phantom.csv, k4_ha_lb.json, k4_delay.csv (this agent; code bars_fam/bf_k4.py, bf_delay.py).

| type | bars (full) | RTH bars/day | mean RTH dur s | bars/min first 30 min | bars/min 12-13 | ratio | bars/day inside 10:00-14:00 | phantom n=0 share | renko edge not traded |
|---|---|---|---|---|---|---|---|---|---|
| time_1m | 1067664 | 383.0 | 61.1 | 1.00 | 1.00 | 1.00 | 237.6 | 0.00% | - |
| time_15s | 4196160 | 1531.6 | 15.3 | 3.99 | 3.99 | 1.00 | 950.3 | 0.00% | - |
| time_30s | 2130188 | 765.9 | 30.6 | 2.00 | 2.00 | 1.00 | 475.3 | 0.00% | - |
| time_2m | 533962 | 191.5 | 122.2 | 0.50 | 0.50 | 1.00 | 118.8 | 0.00% | - |
| time_3m | 355979 | 127.7 | 183.3 | 0.33 | 0.33 | 1.00 | 79.2 | 0.00% | - |
| tick_250 | 1148361 | 1125.4 | 20.8 | 6.21 | 2.12 | 2.93 | 653.7 | 0.00% | - |
| tick_500 | 573986 | 562.7 | 41.6 | 3.10 | 1.06 | 2.93 | 326.9 | 0.00% | - |
| tick_1000 | 286810 | 281.3 | 83.2 | 1.55 | 0.53 | 2.93 | 163.4 | 0.00% | - |
| tick_2000 | 143216 | 140.7 | 166.3 | 0.78 | 0.27 | 2.92 | 81.7 | 0.00% | - |
| volume_500 | 881829 | 876.9 | 26.7 | 4.61 | 1.67 | 2.77 | 508.6 | 0.00% | - |
| volume_1200 | 367199 | 365.4 | 64.0 | 1.92 | 0.69 | 2.77 | 211.9 | 0.00% | - |
| volume_3600 | 122149 | 121.8 | 192.1 | 0.64 | 0.23 | 2.77 | 70.7 | 0.00% | - |
| dollar_150M | 1106335 | 1099.1 | 21.3 | 5.81 | 2.10 | 2.77 | 639.1 | 0.00% | - |
| dollar_300M | 553337 | 549.9 | 42.6 | 2.91 | 1.05 | 2.77 | 319.7 | 0.00% | - |
| dollar_900M | 184267 | 183.4 | 127.6 | 0.97 | 0.35 | 2.76 | 106.6 | 0.00% | - |
| range_5 | 21864304 | 19191.1 | 1.2 | 115.53 | 34.37 | 3.36 | 11186.1 | 0.00% | - |
| range_10 | 8005791 | 6823.4 | 3.4 | 40.68 | 12.12 | 3.36 | 3991.3 | 0.00% | - |
| range_20 | 2525007 | 2106.7 | 11.1 | 12.41 | 3.71 | 3.35 | 1238.0 | 0.00% | - |
| range_40 | 716233 | 590.4 | 39.6 | 3.45 | 1.03 | 3.35 | 347.9 | 0.00% | - |
| range_80 | 189288 | 154.9 | 151.1 | 0.90 | 0.27 | 3.30 | 91.4 | 0.00% | - |
| renko_4 | 17989536 | 14995.8 | 1.6 | 88.60 | 26.35 | 3.36 | 8806.2 | 7.47% | 32.6% |
| renko_8 | 4798153 | 3941.9 | 5.9 | 23.10 | 6.89 | 3.35 | 2322.3 | 3.06% | 29.9% |
| renko_16 | 1233546 | 1005.7 | 23.3 | 5.88 | 1.76 | 3.34 | 593.3 | 1.22% | 26.2% |
| renko_22 | 654787 | 532.9 | 43.9 | 3.11 | 0.94 | 3.32 | 314.6 | 0.81% | 25.4% |
| renko_38 | 219634 | 178.6 | 131.0 | 1.04 | 0.31 | 3.33 | 105.5 | 0.34% | 22.6% |
| imbal_130 | 339961 | 347.3 | 67.4 | 1.80 | 0.66 | 2.72 | 208.0 | 0.00% | - |
| imbal_260 | 114622 | 118.1 | 198.2 | 0.63 | 0.23 | 2.78 | 71.2 | 0.00% | - |
| kagi_8 | 7080915 | 6077.8 | 3.9 | 36.48 | 10.78 | 3.38 | 3545.7 | 0.00% | - |
| kagi_16 | 2118764 | 1768.6 | 13.2 | 10.44 | 3.11 | 3.36 | 1037.9 | 0.00% | - |
| kagi_32 | 584716 | 480.5 | 48.7 | 2.82 | 0.83 | 3.40 | 282.9 | 0.00% | - |
| kagi_60 | 172404 | 141.2 | 165.7 | 0.82 | 0.25 | 3.31 | 83.3 | 0.00% | - |
| linebreak3 | 291818 | 119.4 | 196.0 | - | - | - | 73.0 | 0 | - |
| ha_1m | 1067664 | = time_1m | | | | | = time_1m | 0 | HA close vs real close: mean abs gap 1.75 pt (p90 4.06), inside 10-14: mean abs 2.99 (p90 6.50); HA candle colour differs from the real candle in 36% of bars |
| ha_2m | 533962 | = time_2m | | | | | = time_2m | 0 | HA close vs real close: mean abs gap 2.50 pt (p90 5.81), inside 10-14: mean abs 4.26 (p90 9.25); HA candle colour differs from the real candle in 36% of bars |
| ha_3m | 355979 | = time_3m | | | | | = time_3m | 0 | HA close vs real close: mean abs gap 3.07 pt (p90 7.06), inside 10-14: mean abs 5.23 (p90 11.31); HA candle colour differs from the real candle in 35% of bars |

Reading the table:
- **Phantom bars.** Only Renko prints bricks with n = 0 trades (a multi-brick gap fills the intermediate bricks without a trade): 7.5% of renko_4, 3.1% of renko_8, 1.2% of renko_16, 0.8% of renko_22, 0.3% of renko_38 (full sample; PRE counts in the delay table below). Another 23-33% of bricks complete on a trade that is not at the brick edge (the brick close is a price level, the last trade was beyond it): a Renko close is a level that was crossed, not always traded. Range, Kagi, imbalance, tick, volume, dollar, time, line-break and HA bars have no empty bars (n = 0 share 0). Every n = 0 bar is excluded from the events and from the placebo pool of the same type (counted: renko_4 1,020,796 bricks in PRE, renko_8 115,685, renko_16 11,378, renko_22 3,899, renko_38 542).
- **Compression.** Every activity-based type (tick, volume, dollar, range, Renko, Kagi, imbalance) prints 2.7-3.4x more bars per minute in the first 30 minutes than at 12:00-13:00, so a 10:00-14:00 window is a bar count that is front-loaded (e.g. tick_1000 163 bars/day inside the window, renko_22 315, imbal_130 208, vs 238 for 1-min time bars). Time bars: ratio 1.00. Line break: 119 lines per RTH day (mean 196 s).
- **Heikin-Ashi fill gap** (real close minus HA close at the signal bar): mean about 0 (0.02 pt) but mean absolute gap 1.75 pt (p90 4.06) on 1m, 2.50 (5.81) on 2m, 3.07 (7.06) on 3m; inside 10:00-14:00 the gap is larger (2.99 / 4.26 / 5.23 pt mean absolute; p90 6.5 / 9.3 / 11.3). The HA candle has the opposite colour to the real candle in 35-36% of bars. Entries are filled at the real next open; the HA open is never used.
- **Line break (3-line, 1-min closes):** 291,818 lines in the sample, 119 per RTH day, 73 inside 10:00-14:00, mean line 5.2 pt, 0.27 lines per 1-min bar.
- **Fill delay (the documented mapping).** The library fills on the 1-min path, so a signal on a bar that closes inside a minute is executed at the next 1-min open: median 30-34 s, p90 55-56 s for all sub-minute and activity-sized types; 0 s for 1m/2m/3m time bars, HA, line break. Several bars of the fast types map to the SAME entry minute (range_5 56.8 bars per entry minute, renko_4 43.2, kagi_8 18.4, range_10 20.8): one entry per minute and one open trade at a time, so these types are 1-minute-grid entries with a bar-type-specific signal, not a faster execution. Unmapped share (gap > 65 s, other label day) 0.06-0.25%.

| type | bars PRE (non-phantom) | phantom PRE | unmapped share | bars inside 10-14 | distinct entry minutes | bars per entry minute | delay median s | p90 s |
|---|---|---|---|---|---|---|---|---|
| time_1m | 498662 | 0 | 0.09% | 86385 | 86385 | 1.00 | 0.0 | 0.3 |
| time_15s | 1959015 | 0 | 0.25% | 345491 | 86385 | 4.00 | 30.0 | 45.1 |
| time_30s | 994873 | 0 | 0.14% | 172768 | 86385 | 2.00 | 30.0 | 30.2 |
| time_2m | 249392 | 0 | 0.16% | 43194 | 43194 | 1.00 | 0.0 | 0.3 |
| time_3m | 166264 | 0 | 0.23% | 28795 | 28795 | 1.00 | 0.0 | 0.3 |
| tick_250 | 550096 | 0 | 0.08% | 242375 | 83665 | 2.90 | 32.8 | 55.7 |
| tick_500 | 274963 | 0 | 0.09% | 121187 | 74882 | 1.62 | 32.7 | 55.6 |
| tick_1000 | 137404 | 0 | 0.09% | 60597 | 53228 | 1.14 | 32.5 | 55.6 |
| tick_2000 | 68609 | 0 | 0.09% | 30301 | 29830 | 1.02 | 32.4 | 55.5 |
| volume_500 | 408873 | 0 | 0.09% | 181950 | 81145 | 2.24 | 32.7 | 55.7 |
| volume_1200 | 170253 | 0 | 0.10% | 75817 | 60759 | 1.25 | 32.7 | 55.7 |
| volume_3600 | 56633 | 0 | 0.08% | 25286 | 25064 | 1.01 | 32.7 | 55.7 |
| dollar_150M | 536980 | 0 | 0.09% | 239074 | 83438 | 2.87 | 32.7 | 55.7 |
| dollar_300M | 268572 | 0 | 0.09% | 119611 | 74291 | 1.61 | 32.7 | 55.6 |
| dollar_900M | 89440 | 0 | 0.08% | 39882 | 38188 | 1.04 | 32.8 | 55.6 |
| range_5 | 12388367 | 0 | 0.11% | 4902258 | 86303 | 56.80 | 33.2 | 55.7 |
| range_10 | 4659496 | 0 | 0.11% | 1788651 | 85918 | 20.82 | 33.5 | 55.8 |
| range_20 | 1497482 | 0 | 0.11% | 565539 | 81935 | 6.90 | 33.9 | 55.9 |
| range_40 | 430695 | 0 | 0.11% | 161235 | 60408 | 2.67 | 34.1 | 55.9 |
| range_80 | 114650 | 0 | 0.08% | 42638 | 28590 | 1.49 | 34.3 | 56.0 |
| renko_4 | 9648774 | 1020796 | 0.11% | 3720947 | 86079 | 43.23 | 33.6 | 55.8 |
| renko_8 | 2765105 | 115685 | 0.11% | 1042063 | 83151 | 12.53 | 33.9 | 55.9 |
| renko_16 | 735474 | 11378 | 0.10% | 274212 | 65087 | 4.21 | 34.1 | 55.9 |
| renko_22 | 393041 | 3899 | 0.09% | 146323 | 51180 | 2.86 | 34.2 | 55.9 |
| renko_38 | 133064 | 542 | 0.08% | 49371 | 27972 | 1.77 | 34.3 | 56.0 |
| imbal_130 | 152798 | 0 | 0.06% | 72535 | 44015 | 1.65 | 33.5 | 55.8 |
| imbal_260 | 51094 | 0 | 0.06% | 24454 | 20564 | 1.19 | 33.9 | 55.9 |
| kagi_8 | 4104641 | 0 | 0.11% | 1579668 | 85787 | 18.41 | 33.1 | 55.8 |
| kagi_16 | 1252652 | 0 | 0.12% | 471953 | 79211 | 5.96 | 33.8 | 56.0 |
| kagi_32 | 350510 | 0 | 0.13% | 130717 | 53406 | 2.45 | 34.1 | 56.0 |
| kagi_60 | 104539 | 0 | 0.13% | 38915 | 25931 | 1.50 | 33.8 | 55.7 |
| linebreak3 | 136085 | 0 | 0.07% | 26622 | 26622 | 1.00 | 0.0 | 0.2 |
| ha_1m | 498662 | 0 | 0.09% | 86385 | 86385 | 1.00 | 0.0 | 0.3 |
| ha_2m | 249392 | 0 | 0.16% | 43194 | 43194 | 1.00 | 0.0 | 0.3 |
| ha_3m | 166264 | 0 | 0.23% | 28795 | 28795 | 1.00 | 0.0 | 0.3 |

Calibration drift note (plan section 2): the activity bars are calibrated on 2023-02/03; whole-sample mean durations are 25-30% shorter, so bars/day rise over the years and year ordering must be read with that.

## 2. Grid enumeration and screened N (copy of the prereg, prereg/ZEN_BARS_prereg.md sha256 8c0c7da6cc97a5c759e687238d0f7f6c2b6156120a6c17860e610a8bdafb7c47)
34 bar types x 5 entry cells (E1 R1+EMA200 tol5; E2 R1+EMA200 tol2; E3 R8+EMA200 tol5; E4 R1+session VWAP tol5; E5 R3+EMA50 tol5) x 2 regime variants (5-min time EMA200 control; EMA200 of the same type at ~5x) x 4 line options (own line; T3_233; TMA_377; SMMA_377 = top-3 LINES_C R1 lines) x 2 brackets (model: 15-pt stop from the entry + nearest 1-min confirmed swing target 5..60 pt; comparator 60/60 fixed) x 2 flat (14:00, 15:55) = 5,440; + 160 control rows (time_1m) = 5,600. Scored 5,600, skipped 0. Cells with n < 100 (192 of 5,600; flagged in pre_all.parquet) are counts, not verdicts. Cell table prereg/ZEN_BARS_cells.csv sha256 6cb0d393d14866c72eb7c917c4fa91555f66c449a33e8ee853f6a6aef100891f. Program N 291,130.
Screen-level facts (PRE 2024-02-01..2025-06-30, 75 weeks): distinct rows n >= 100 outside the control: 4,432; fraction with effect > 0 vs random-in-regime: 45%; mean effect -0.38 pt/trade (model bracket +0.09, 60/60 comparator -0.86); rows with week-block CI lower > 0: 107 of 2,212 model rows (55 expected by chance at 2.5% one-sided, rows are strongly correlated) and 13 of 2,220 comparator rows; rows with a per-cell white reality-check p <= 0.05: 0 (minimum 0.36).

## 3. Top-10 table (mandatory; the first 10 of the holdout 30 = top 10 of the family by PRE effect vs random-in-regime on the same bar type, regardless of verdict; row = type / cell / line / regime variant / bracket / flat)
| # | row | n PRE | trades/wk | PRE mean pts (net1/net2) | win vs BE | PRE effect [CI lo] | MDE80 | HOLD n / mean / effect [CI lo] | X n / effect | weeks for 80% power | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | kagi_32/E3/SMMA_377_close/x5/c60/955 | 191 | 2.5 | 9.01 / 6.41 | 0.592 vs 0.513 | 10.76 [1.76] | 11.65 | 51 / 7.86 / 5.04 [-9.48] | 43 / 8.77 | 400 | G5,G6,G8,G9 |
| 2 | renko_38/E2/TMA_377_close/ctl/c60/955 | 167 | 2.2 | 8.74 / 6.32 | 0.587 vs 0.512 | 10.63 [-0.41] | 17.29 | 57 / 2.17 / 0.53 [-13.11] | 22 / -3.51 | 79951 | G1,G5,G6,G7,G8,G9 |
| 3 | kagi_32/E3/SMMA_377_close/x5/c60/840 | 191 | 2.5 | 9.28 / 6.68 | 0.592 vs 0.504 | 10.47 [1.51] | 11.34 | 51 / 7.87 / 5.19 [-9.52] | 43 / 7.08 | 357 | G5,G6,G8,G9 |
| 4 | imbal_260/E2/SMMA_377_close/x5/c60/840 | 122 | 1.6 | 8.52 / 6.44 | 0.607 vs 0.522 | 8.53 [0.93] | 10.67 | 41 / 3.41 / 4.37 [-10.22] | 73 / 9.59 | 446 | G5,G6,G8 |
| 5 | kagi_60/E2/TMA_377_close/ctl/c60/840 | 122 | 1.6 | 6.59 / 4.05 | 0.574 vs 0.513 | 8.24 [-0.29] | 11.69 | 35 / 9.37 / 7.57 [-9.78] | 18 / -21.10 | 178 | G1,G5,G6,G7,G8 |
| 6 | renko_38/E3/TMA_377_close/ctl/c60/955 | 117 | 1.6 | 6.03 / 3.70 | 0.573 vs 0.521 | 8.14 [-2.56] | 16.46 | 44 / -12.46 / -13.95 [-27.34] | 29 / 1.91 | n/a (HOLD effect <= 0) | G1,G2,G5,G6,G8,G9 |
| 7 | kagi_32/E5/SMMA_377_close/x5/c60/840 | 244 | 3.3 | 6.46 / 3.91 | 0.574 vs 0.514 | 8.00 [0.86] | 9.41 | 66 / 4.02 / 2.09 [-9.37] | 58 / 1.98 | 1518 | G5,G6,G8,G9 |
| 8 | renko_38/E2/TMA_377_close/ctl/c60/840 | 167 | 2.2 | 6.04 / 3.66 | 0.569 vs 0.512 | 7.99 [-2.82] | 16.40 | 57 / -1.11 / -2.80 [-16.48] | 22 / 5.28 | n/a (HOLD effect <= 0) | G1,G5,G6,G8,G9 |
| 9 | linebreak3/E1/SMMA_377_close/ctl/c60/840 | 145 | 1.9 | 8.20 / 6.08 | 0.566 vs 0.477 | 7.74 [-0.74] | 11.50 | 53 / 5.82 / 4.73 [-9.20] | 83 / 1.50 | 443 | G1,G5,G6,G8 |
| 10 | imbal_260/E2/SMMA_377_close/x5/c60/955 | 122 | 1.6 | 6.61 / 4.48 | 0.557 vs 0.499 | 7.59 [-0.29] | 10.99 | 41 / 9.08 / 10.56 [-2.07] | 73 / 9.07 | 81 | G1,G2,G5,G6,G8 |

Reading: all 10 rows are the 60/60 comparator (high variance: MDE80 9-17 pt); none reaches its MDE with a positive HOLD CI. Weeks for 80% power use the HOLD effect and the PRE MDE80 (75 x (MDE80/effect)^2) and are in the hundreds-to-tens-of-thousands: there is no forward test worth running on any of them.

Top 10 among the MODEL bracket (the 15-pt stop; PRE only, not taken to the holdout by the prereg rule - listed because the 30 holdout rows are all 60/60):
| row | n PRE | trades/wk | net1 / net2 | win vs BE | pool | effect [CI lo] | MDE80 | paired vs 1m diff / MDE80 | white RC p |
|---|---|---|---|---|---|---|---|---|---|
| tick_2000/E2/TMA_377_close/x5/model/840 | 248 | 3.3 | 1.52 / -0.71 | 0.577 vs 0.524 | -1.63 | 3.15 [1.11] | 2.84 | 3.13 / 3.04 | 0.53 |
| imbal_260/E1/TMA_377_close/x5/model/955 | 178 | 2.4 | 1.54 / -0.46 | 0.556 vs 0.505 | -1.49 | 3.03 [0.52] | 3.75 | 3.00 / 3.98 | 0.99 |
| tick_2000/E2/TMA_377_close/x5/model/955 | 248 | 3.3 | 1.37 / -0.85 | 0.573 vs 0.526 | -1.63 | 3.00 [0.93] | 2.83 | 3.15 / 3.07 | 0.66 |
| imbal_260/E5/TMA_377_close/x5/model/840 | 140 | 1.9 | 1.35 / -0.66 | 0.564 vs 0.518 | -1.64 | 2.99 [0.63] | 3.64 | 3.49 / 3.88 | 0.98 |
| dollar_900M/E5/TMA_377_close/x5/model/955 | 268 | 3.6 | 1.13 / -0.83 | 0.511 vs 0.476 | -1.83 | 2.96 [0.96] | 2.95 | 3.71 / 3.19 | 0.80 |
| dollar_900M/E5/TMA_377_close/x5/model/840 | 268 | 3.6 | 1.13 / -0.83 | 0.507 vs 0.472 | -1.81 | 2.94 [0.95] | 2.91 | 3.44 / 3.16 | 0.79 |
| imbal_260/E5/TMA_377_close/x5/model/955 | 140 | 1.9 | 1.25 / -0.77 | 0.557 vs 0.515 | -1.65 | 2.90 [0.53] | 3.66 | 3.65 / 3.95 | 0.99 |
| imbal_260/E1/TMA_377_close/x5/model/840 | 178 | 2.4 | 1.39 / -0.60 | 0.562 vs 0.515 | -1.48 | 2.87 [0.48] | 3.64 | 2.67 / 3.82 | 0.99 |
| kagi_60/E2/base/x5/model/955 | 142 | 1.9 | 0.43 / -2.30 | 0.620 vs 0.603 | -2.43 | 2.86 [0.51] | 3.17 | 3.07 / 3.45 | 0.94 |
| renko_38/E5/TMA_377_close/x5/model/840 | 209 | 2.8 | 0.05 / -2.19 | 0.512 vs 0.510 | -2.75 | 2.80 [0.45] | 3.22 | 3.30 / 3.41 | 0.96 |

## 4. By window (PRE) for the top 10, long / short
| # | row | PRE 09:30-10 | 10-11 | 11-12 | 12-13 | 13-14 | 14:00-15:30 | PRIMARY | RTH 09:30-15:30 | long n / mean | short n / mean |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | kagi_32/E3/SMMA_377_close/x5/c60/955 | 1.24 (n 51) | 14.30 (n 87) | -5.52 (n 49) | 6.67 (n 42) | 11.32 (n 38) | 0.92 (n 50) | 10.76 (n 191) | 7.56 (n 271) | 95 / 6.67 | 96 / 11.32 |
| 2 | renko_38/E2/TMA_377_close/ctl/c60/955 | 4.05 (n 44) | 14.61 (n 66) | 4.86 (n 48) | 16.42 (n 32) | 5.65 (n 36) | 3.78 (n 45) | 10.63 (n 167) | 8.34 (n 249) | 56 / 6.74 | 111 / 9.75 |
| 3 | kagi_32/E3/SMMA_377_close/x5/c60/840 | 1.00 (n 51) | 15.05 (n 87) | -3.70 (n 49) | 9.21 (n 42) | 11.19 (n 38) | - (n 0) | 10.47 (n 191) | 8.12 (n 228) | 95 / 6.91 | 96 / 11.64 |
| 4 | imbal_260/E2/SMMA_377_close/x5/c60/840 | -0.89 (n 38) | -1.55 (n 59) | 14.61 (n 35) | 9.54 (n 24) | 6.61 (n 31) | - (n 0) | 8.53 (n 122) | 7.12 (n 147) | 82 / 11.49 | 40 / 2.44 |
| 5 | kagi_60/E2/TMA_377_close/ctl/c60/840 | 5.62 (n 18) | 7.55 (n 54) | -6.87 (n 23) | 31.53 (n 20) | 8.48 (n 30) | - (n 0) | 8.24 (n 122) | 7.95 (n 138) | 52 / 0.30 | 70 / 11.27 |
| 6 | renko_38/E3/TMA_377_close/ctl/c60/955 | -3.99 (n 30) | 3.13 (n 43) | -0.43 (n 29) | 26.23 (n 23) | 14.49 (n 30) | 5.61 (n 48) | 8.14 (n 117) | 4.72 (n 189) | 46 / 3.56 | 71 / 7.62 |
| 7 | kagi_32/E5/SMMA_377_close/x5/c60/840 | -3.00 (n 74) | 8.27 (n 109) | 3.37 (n 72) | 8.22 (n 53) | 8.22 (n 48) | - (n 0) | 8.00 (n 244) | 5.34 (n 302) | 133 / 3.26 | 111 / 10.29 |
| 8 | renko_38/E2/TMA_377_close/ctl/c60/840 | 2.53 (n 44) | 14.93 (n 66) | 1.63 (n 48) | 11.28 (n 32) | -0.38 (n 36) | - (n 0) | 7.99 (n 167) | 6.92 (n 208) | 56 / 4.77 | 111 / 6.69 |
| 9 | linebreak3/E1/SMMA_377_close/ctl/c60/840 | -3.90 (n 42) | 12.85 (n 54) | 1.23 (n 42) | 8.75 (n 40) | 3.84 (n 44) | - (n 0) | 7.74 (n 145) | 5.32 (n 179) | 65 / 4.65 | 80 / 11.09 |
| 10 | imbal_260/E2/SMMA_377_close/x5/c60/955 | -0.11 (n 38) | -2.47 (n 59) | 11.13 (n 35) | 21.87 (n 24) | 2.25 (n 31) | -10.89 (n 39) | 7.59 (n 122) | 3.17 (n 175) | 82 / 8.52 | 40 / 2.69 |

Windows are the mapped entry-bar start; flat 14:00 rows have no 14:00-15:30 entries (n 0). Random-in-regime column = the pool of the same window and type (effect = mean net minus pool mean). Per-window n is 18-110; every cell is inside its MDE.

## 5. Holdout stage for the 30 (one HOLD look + X; paired vs the time_1m row with the same cell / line / variant / bracket / flat)
| # | row | PRE eff | HOLD eff [CI lo] | X eff | 2024 eff | 2025 eff | 2026 eff | paired vs 1m in HOLD: diff [CI lo] / MDE80 | G1 | G2 | G3 | G4 | G5 | G6 | G7 | G8 | G9 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | kagi_32/E3/SMMA_377_close/x5/c60/955 | 10.8 | 5.0 [-9.5] | 8.8 | 6.7 | 10.8 | 3.4 | 4.8 [-12.3] / 26.7 | Y | Y | Y | Y | n | n | Y | n | n |
| 2 | renko_38/E2/TMA_377_close/ctl/c60/955 | 10.6 | 0.5 [-13.1] | -3.5 | 19.8 | 1.6 | 10.0 | 0.4 [-15.8] / 24.0 | n | Y | Y | Y | n | n | n | n | n |
| 3 | kagi_32/E3/SMMA_377_close/x5/c60/840 | 10.5 | 5.2 [-9.5] | 7.1 | 4.7 | 11.7 | 2.6 | 8.1 [-9.4] / 27.1 | Y | Y | Y | Y | n | n | Y | n | n |
| 4 | imbal_260/E2/SMMA_377_close/x5/c60/840 | 8.5 | 4.4 [-10.2] | 9.6 | 9.5 | 7.7 | -11.5 | 8.7 [-8.1] / 24.5 | Y | Y | Y | Y | n | n | Y | n | Y |
| 5 | kagi_60/E2/TMA_377_close/ctl/c60/840 | 8.2 | 7.6 [-9.8] | -21.1 | 7.6 | 6.9 | 31.4 | 7.2 [-9.8] / 24.6 | n | Y | Y | Y | n | n | n | n | Y |
| 6 | renko_38/E3/TMA_377_close/ctl/c60/955 | 8.1 | -13.9 [-27.3] | 1.9 | 11.5 | -1.8 | -19.2 | -12.6 [-28.2] / 25.2 | n | n | Y | Y | n | n | Y | n | n |
| 7 | kagi_32/E5/SMMA_377_close/x5/c60/840 | 8.0 | 2.1 [-9.4] | 2.0 | 0.7 | 9.5 | 5.4 | 6.5 [-8.4] / 22.5 | Y | Y | Y | Y | n | n | Y | n | n |
| 8 | renko_38/E2/TMA_377_close/ctl/c60/840 | 8.0 | -2.8 [-16.5] | 5.3 | 14.9 | 0.2 | 3.7 | -3.2 [-19.2] / 23.5 | n | Y | Y | Y | n | n | Y | n | n |
| 9 | linebreak3/E1/SMMA_377_close/ctl/c60/840 | 7.7 | 4.7 [-9.2] | 1.5 | 4.0 | 11.0 | -14.3 | 7.7 [-9.5] / 23.1 | n | Y | Y | Y | n | n | Y | n | Y |
| 10 | imbal_260/E2/SMMA_377_close/x5/c60/955 | 7.6 | 10.6 [-2.1] | 9.1 | 6.6 | 11.8 | -3.3 | 15.1 [0.7] / 22.4 | n | n | Y | Y | n | n | Y | n | Y |
| 11 | kagi_32/E5/SMMA_377_close/x5/c60/955 | 7.5 | 2.5 [-8.8] | 2.3 | 0.3 | 9.0 | 6.4 | 6.1 [-9.4] / 23.0 | n | Y | Y | Y | n | n | Y | n | n |
| 12 | renko_38/E5/TMA_377_close/ctl/c60/955 | 7.5 | -7.5 [-19.5] | -2.6 | 8.4 | 1.3 | -5.6 | -6.0 [-20.6] / 22.8 | n | n | Y | Y | n | n | n | n | n |
| 13 | kagi_60/E2/TMA_377_close/x5/c60/955 | 7.3 | -4.6 [-25.8] | -4.4 | 1.8 | 6.6 | -19.7 | -4.7 [-26.9] / 29.8 | n | n | Y | Y | n | n | n | n | n |
| 14 | kagi_60/E2/TMA_377_close/ctl/c60/955 | 7.2 | 3.0 [-11.2] | -24.0 | 4.2 | 5.5 | 33.5 | 2.9 [-12.6] / 22.8 | n | n | Y | Y | n | n | n | n | Y |
| 15 | kagi_60/E1/T3_233_close/x5/c60/955 | 7.0 | 13.5 [2.0] | -13.6 | 5.8 | 10.6 | -0.4 | 12.6 [-0.3] / 17.9 | n | n | Y | Y | n | Y | n | n | n |
| 16 | kagi_60/E5/T3_233_close/x5/c60/955 | 7.0 | 14.0 [0.2] | -15.2 | 1.4 | 12.5 | 9.6 | 12.2 [-2.4] / 20.2 | n | n | Y | Y | n | Y | n | n | n |
| 17 | kagi_32/E3/SMMA_377_close/ctl/c60/955 | 7.0 | -2.0 [-11.4] | 0.3 | 7.6 | 2.3 | 8.8 | -2.3 [-13.6] / 17.2 | n | Y | Y | Y | n | n | Y | n | n |
| 18 | kagi_60/E1/T3_233_close/x5/c60/840 | 6.9 | 9.4 [-1.7] | -10.3 | 7.5 | 8.3 | -5.1 | 8.6 [-3.9] / 16.9 | n | n | Y | Y | n | n | n | n | n |
| 19 | kagi_60/E1/TMA_377_close/x5/c60/955 | 6.9 | -8.3 [-22.7] | 1.1 | 2.5 | 4.6 | -8.7 | -10.2 [-28.3] / 25.0 | n | Y | Y | Y | n | n | Y | n | n |
| 20 | kagi_60/E2/TMA_377_close/x5/c60/840 | 6.8 | 1.9 [-18.7] | -5.9 | 1.4 | 8.2 | -21.8 | 1.5 [-20.2] / 28.5 | n | n | Y | Y | n | n | n | n | n |
| 21 | kagi_60/E5/T3_233_close/x5/c60/840 | 6.6 | 9.4 [-3.6] | -13.9 | 3.1 | 9.7 | 3.7 | 7.8 [-6.2] / 19.7 | n | n | Y | Y | n | n | n | n | n |
| 22 | range_80/E2/base/ctl/c60/955 | 6.6 | -1.4 [-8.2] | -2.6 | 8.4 | 3.2 | -10.1 | -1.7 [-7.8] / 9.7 | Y | Y | Y | Y | n | n | n | n | n |
| 23 | linebreak3/E1/SMMA_377_close/ctl/c60/955 | 6.5 | 9.4 [-5.1] | -2.8 | 3.5 | 10.8 | 3.3 | 12.1 [-7.7] / 27.3 | n | Y | Y | Y | n | n | n | n | Y |
| 24 | renko_38/E1/TMA_377_close/x5/c60/955 | 6.4 | -3.9 [-15.4] | 5.1 | 5.2 | 4.1 | -14.2 | -5.8 [-20.1] / 20.8 | Y | n | Y | Y | n | n | Y | n | Y |
| 25 | kagi_60/E1/TMA_377_close/x5/c60/840 | 6.3 | -4.5 [-19.9] | 1.4 | 1.6 | 5.6 | -10.8 | -5.5 [-22.6] / 24.8 | n | Y | Y | Y | n | n | Y | n | n |
| 26 | renko_38/E1/TMA_377_close/x5/c60/840 | 6.3 | -3.2 [-13.7] | -0.1 | 5.9 | 3.7 | -11.3 | -4.1 [-16.3] / 18.3 | Y | Y | Y | Y | n | n | n | n | Y |
| 27 | renko_38/E5/TMA_377_close/x5/c60/955 | 6.3 | 1.3 [-11.2] | 13.4 | 8.5 | 3.9 | -12.5 | 2.8 [-13.2] / 25.3 | n | n | n | Y | n | n | Y | n | Y |
| 28 | kagi_32/E1/SMMA_377_close/x5/c60/955 | 6.1 | 1.9 [-7.4] | -0.5 | 3.9 | 4.8 | 12.7 | 4.7 [-6.5] / 17.2 | Y | Y | Y | Y | n | n | n | n | Y |
| 29 | kagi_32/E3/SMMA_377_close/ctl/c60/840 | 6.0 | -2.6 [-12.5] | 1.6 | 6.1 | 2.2 | 3.5 | 0.3 [-12.2] / 17.8 | n | Y | Y | Y | n | n | Y | n | n |
| 30 | dollar_900M/E5/TMA_377_close/x5/c60/840 | 5.8 | 5.7 [-6.8] | 0.8 | 4.8 | 6.1 | 12.2 | 5.9 [-7.6] / 18.0 | n | Y | Y | Y | n | n | Y | n | Y |

Totals: G1 8/30, G2 18/30, G3 29/30, G4 30/30 (all because the 60/60 bracket has a break-even win rate near 51%), G5 0/30, G6 2/30, G7 16/30, G8 0/30, G9 11/30, all of G1-G9: 0/30. Mean PRE effect 7.40, mean HOLD effect 1.91 (74% shrinkage = selection), mean paired HOLD difference vs the time_1m counterpart +2.66 with paired MDE80 17-30: inside the MDE. 2024 / 2025 / 2026 columns are effects vs random-in-regime within WF (PRE + HOLD); 2026 = 5 weeks. HOLD rank (draws) and per-row detail: out/zen/bars_fam/top30_final.csv, hold_res.pkl.

## 6. Bar-type tables (PRE; E1-E5 pooled, base line, flat 14:00, n-weighted; 75 PRE weeks)
Model bracket (15-pt stop + nearest swing target), regime = 5-min time EMA200 (control). "effect (minute-deduped pool)" repeats the effect with each (minute, side) entering the placebo pool once instead of once per bar (sensitivity, see section 8).
| type | n (5 cells, PRE) | trades/wk | pts/trade net1 | net2 | win vs BE | effect vs random (bar-weighted pool, prereg) | effect vs random (minute-deduped pool) | diff vs 1m (prereg pool) | eff 2024-02..10 | eff 2024-11..2025-06 | 09:30-10 | 10-11 | 11-12 | 12-13 | 13-14 | 14:00-15:30 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| time_1m | 7415 | 99 | -2.06 | -4.19 | 0.557 vs 0.645 | -0.26 | -0.26 | 0.00 | -0.01 | -0.50 | 0.50 | -0.76 | -0.22 | -0.12 | 0.30 | nan |
| time_15s | 17084 | 228 | -2.05 | -4.24 | 0.568 vs 0.657 | -0.29 | -0.30 | -0.03 | -0.25 | -0.28 | -0.18 | -0.69 | -0.12 | -0.11 | 0.11 | nan |
| time_30s | 11506 | 153 | -1.97 | -4.13 | 0.566 vs 0.651 | -0.16 | -0.16 | 0.10 | -0.12 | -0.19 | 0.16 | -0.25 | -0.10 | -0.21 | -0.01 | nan |
| time_2m | 4510 | 60 | -2.21 | -4.25 | 0.534 vs 0.626 | -0.42 | -0.42 | -0.16 | -0.48 | -0.42 | -0.02 | -1.13 | 0.14 | 0.39 | -0.77 | nan |
| time_3m | 3655 | 49 | -1.74 | -3.81 | 0.551 vs 0.624 | 0.01 | 0.01 | 0.27 | -0.41 | 0.43 | 0.77 | 0.21 | -0.30 | 0.30 | -0.07 | nan |
| tick_250 | 15808 | 211 | -1.98 | -4.12 | 0.552 vs 0.635 | -0.13 | -0.17 | 0.13 | -0.10 | -0.12 | 0.17 | -0.25 | 0.18 | -0.06 | -0.18 | nan |
| tick_500 | 10729 | 143 | -1.75 | -3.90 | 0.559 vs 0.632 | 0.13 | 0.06 | 0.39 | -0.02 | 0.32 | 0.08 | -0.25 | 0.57 | 0.07 | 0.48 | nan |
| tick_1000 | 6599 | 88 | -2.10 | -4.15 | 0.527 vs 0.613 | -0.25 | -0.29 | 0.01 | -0.33 | -0.19 | 0.30 | -0.66 | -0.56 | 0.58 | 0.45 | nan |
| tick_2000 | 3458 | 46 | -1.61 | -3.71 | 0.536 vs 0.601 | 0.18 | 0.15 | 0.44 | -0.45 | 0.87 | 0.86 | -0.40 | 0.05 | -0.02 | 1.94 | nan |
| volume_500 | 13662 | 182 | -1.91 | -4.02 | 0.552 vs 0.632 | -0.13 | -0.13 | 0.13 | -0.08 | -0.16 | -0.04 | -0.25 | 0.02 | 0.03 | -0.07 | nan |
| volume_1200 | 7726 | 103 | -1.91 | -3.96 | 0.537 vs 0.615 | -0.13 | -0.15 | 0.13 | -0.23 | -0.03 | 0.19 | -0.85 | -0.06 | 1.12 | 0.15 | nan |
| volume_3600 | 2856 | 38 | -2.03 | -4.03 | 0.525 vs 0.607 | -0.23 | -0.24 | 0.03 | -0.45 | 0.00 | 0.35 | -0.58 | -0.27 | 0.22 | 0.10 | nan |
| dollar_150M | 15651 | 209 | -2.01 | -4.15 | 0.553 vs 0.639 | -0.22 | -0.24 | 0.04 | -0.12 | -0.30 | 0.40 | -0.30 | -0.12 | -0.26 | -0.05 | nan |
| dollar_300M | 10564 | 141 | -1.89 | -4.01 | 0.553 vs 0.632 | -0.04 | -0.05 | 0.22 | -0.11 | 0.04 | -0.42 | -0.26 | 0.14 | 0.15 | 0.06 | nan |
| dollar_900M | 4410 | 59 | -2.19 | -4.25 | 0.516 vs 0.604 | -0.36 | -0.39 | -0.11 | -0.64 | -0.07 | -0.10 | -0.32 | -0.47 | -0.17 | -0.52 | nan |
| range_5 | 50864 | 678 | -2.19 | -4.36 | 0.537 vs 0.628 | 0.06 | -0.39 | 0.32 | 0.00 | -0.02 | 0.46 | 0.19 | 0.00 | -0.27 | 0.23 | nan |
| range_10 | 38301 | 511 | -2.15 | -4.35 | 0.539 vs 0.628 | 0.25 | -0.35 | 0.51 | 0.02 | 0.27 | 0.48 | 0.32 | 0.28 | -0.10 | 0.53 | nan |
| range_20 | 23782 | 317 | -2.24 | -4.43 | 0.527 vs 0.619 | 0.22 | -0.43 | 0.48 | 0.03 | 0.23 | 0.38 | 0.15 | 0.41 | -0.12 | 0.63 | nan |
| range_40 | 11437 | 152 | -2.11 | -4.30 | 0.522 vs 0.606 | 0.44 | -0.21 | 0.70 | 0.41 | 0.33 | 0.57 | 0.19 | 0.87 | 0.72 | 0.30 | nan |
| range_80 | 3891 | 52 | -2.20 | -4.36 | 0.496 vs 0.581 | 0.40 | -0.23 | 0.65 | 0.04 | 0.51 | -0.45 | -0.31 | 0.76 | 0.82 | 1.11 | nan |
| renko_4 | 47138 | 629 | -2.21 | -4.39 | 0.537 vs 0.628 | 0.15 | -0.39 | 0.41 | 0.04 | 0.09 | 0.50 | 0.25 | 0.12 | -0.13 | 0.37 | nan |
| renko_8 | 30005 | 400 | -2.16 | -4.36 | 0.532 vs 0.621 | 0.34 | -0.39 | 0.60 | 0.09 | 0.38 | 0.35 | 0.37 | 0.37 | 0.01 | 0.73 | nan |
| renko_16 | 13836 | 184 | -2.38 | -4.58 | 0.514 vs 0.609 | 0.22 | -0.46 | 0.48 | -0.10 | 0.32 | 0.48 | 0.20 | 0.26 | 0.07 | 0.47 | nan |
| renko_22 | 8356 | 111 | -2.28 | -4.47 | 0.500 vs 0.589 | 0.32 | -0.34 | 0.57 | -0.27 | 0.62 | 0.63 | 0.00 | 0.63 | 0.66 | 0.40 | nan |
| renko_38 | 2500 | 33 | -2.65 | -4.75 | 0.458 vs 0.556 | 0.00 | -0.63 | 0.26 | -0.26 | 0.11 | 0.87 | -0.58 | 1.45 | 0.07 | -0.74 | nan |
| imbal_130 | 6607 | 88 | -1.81 | -3.79 | 0.539 vs 0.613 | -0.19 | -0.16 | 0.07 | -0.42 | 0.12 | 0.04 | -0.61 | -0.04 | 0.00 | 0.42 | nan |
| imbal_260 | 2151 | 29 | -1.89 | -3.83 | 0.524 vs 0.599 | -0.19 | -0.17 | 0.07 | -0.39 | 0.08 | 0.21 | -0.49 | -0.45 | 1.86 | -0.57 | nan |
| kagi_8 | 33648 | 449 | -2.13 | -4.33 | 0.540 vs 0.628 | 0.21 | -0.33 | 0.47 | 0.07 | 0.19 | 0.35 | 0.26 | 0.19 | -0.05 | 0.49 | nan |
| kagi_16 | 16962 | 226 | -2.29 | -4.48 | 0.527 vs 0.620 | 0.17 | -0.48 | 0.43 | -0.05 | 0.23 | 0.20 | 0.16 | 0.31 | -0.29 | 0.55 | nan |
| kagi_32 | 6060 | 81 | -2.44 | -4.61 | 0.513 vs 0.611 | 0.01 | -0.55 | 0.27 | -0.18 | 0.02 | 0.15 | -0.16 | -0.47 | 0.50 | 0.78 | nan |
| kagi_60 | 1760 | 23 | -1.93 | -4.26 | 0.531 vs 0.609 | 0.48 | 0.08 | 0.74 | -0.35 | 0.92 | 1.01 | -0.11 | 0.64 | 1.12 | 1.06 | nan |
| linebreak3 | 1198 | 16 | -1.94 | -3.90 | 0.525 vs 0.605 | -0.24 | -0.24 | 0.02 | -0.56 | -0.05 | 0.10 | -1.35 | -0.12 | 0.35 | 0.49 | nan |
| ha_1m | 9147 | 122 | -2.07 | -4.20 | 0.550 vs 0.638 | -0.26 | -0.26 | -0.00 | -0.10 | -0.37 | -0.24 | -1.02 | 0.20 | 0.04 | 0.13 | nan |
| ha_2m | 5963 | 80 | -2.19 | -4.23 | 0.528 vs 0.619 | -0.41 | -0.41 | -0.15 | -0.53 | -0.32 | 0.31 | -0.88 | 0.26 | 0.16 | -1.14 | nan |
| ha_3m | 4843 | 65 | -1.96 | -4.00 | 0.528 vs 0.608 | -0.15 | -0.15 | 0.11 | -0.69 | 0.40 | 0.62 | -0.53 | 0.31 | 0.56 | -0.56 | nan |

Same, regime EMA200 on the same bar type at ~5x size (5x column of the grid):
| type | n (5 cells, PRE) | trades/wk | pts/trade net1 | net2 | win vs BE | effect vs random (bar-weighted pool, prereg) | effect vs random (minute-deduped pool) | diff vs 1m (prereg pool) | eff 2024-02..10 | eff 2024-11..2025-06 | 09:30-10 | 10-11 | 11-12 | 12-13 | 13-14 | 14:00-15:30 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| time_1m | 7415 | 99 | -2.06 | -4.19 | 0.557 vs 0.645 | -0.26 | n/a | 0.00 | -0.01 | -0.50 | 0.50 | -0.76 | -0.22 | -0.12 | 0.30 | nan |
| time_15s | 18745 | 250 | -2.05 | -4.24 | 0.568 vs 0.658 | -0.39 | n/a | -0.13 | -0.34 | -0.39 | -0.42 | -0.86 | -0.04 | -0.25 | -0.05 | nan |
| time_30s | 12031 | 160 | -2.04 | -4.19 | 0.562 vs 0.650 | -0.28 | n/a | -0.03 | -0.25 | -0.32 | 0.12 | -0.39 | -0.14 | -0.46 | -0.07 | nan |
| time_2m | 4083 | 54 | -2.20 | -4.25 | 0.534 vs 0.627 | -0.59 | n/a | -0.33 | -0.48 | -0.78 | -0.22 | -0.95 | -0.28 | -0.01 | -0.94 | nan |
| time_3m | 2987 | 40 | -1.84 | -3.93 | 0.550 vs 0.627 | -0.15 | n/a | 0.11 | -0.45 | 0.14 | 0.81 | -0.09 | -0.39 | 0.55 | -0.56 | nan |
| tick_250 | 16658 | 222 | -2.10 | -4.22 | 0.546 vs 0.634 | -0.21 | n/a | 0.05 | -0.14 | -0.26 | 0.27 | -0.26 | 0.01 | -0.20 | -0.30 | nan |
| tick_500 | 10074 | 134 | -1.78 | -3.91 | 0.556 vs 0.630 | 0.10 | n/a | 0.36 | -0.00 | 0.24 | 0.39 | -0.34 | 0.47 | 0.21 | 0.37 | nan |
| tick_1000 | 5621 | 75 | -1.89 | -3.96 | 0.536 vs 0.613 | -0.15 | n/a | 0.11 | 0.05 | -0.40 | 0.63 | -0.33 | -0.63 | 0.94 | 0.08 | nan |
| tick_2000 | 2982 | 40 | -1.35 | -3.46 | 0.542 vs 0.597 | 0.28 | n/a | 0.53 | -0.21 | 0.82 | 0.86 | 0.20 | 0.04 | 0.25 | 1.16 | nan |
| volume_500 | 13715 | 183 | -1.91 | -4.02 | 0.550 vs 0.630 | -0.09 | n/a | 0.16 | -0.02 | -0.14 | -0.13 | -0.14 | -0.02 | 0.02 | -0.13 | nan |
| volume_1200 | 6742 | 90 | -1.84 | -3.90 | 0.540 vs 0.615 | -0.13 | n/a | 0.12 | -0.11 | -0.17 | 0.08 | -0.58 | -0.52 | 1.60 | -0.37 | nan |
| volume_3600 | 2542 | 34 | -2.19 | -4.18 | 0.519 vs 0.607 | -0.50 | n/a | -0.24 | -0.49 | -0.57 | 0.41 | -1.26 | 0.16 | -0.08 | 0.22 | nan |
| dollar_150M | 16541 | 221 | -2.06 | -4.19 | 0.551 vs 0.638 | -0.21 | n/a | 0.05 | -0.13 | -0.27 | 0.33 | -0.22 | -0.21 | -0.25 | -0.14 | nan |
| dollar_300M | 9901 | 132 | -1.90 | -4.02 | 0.551 vs 0.630 | -0.07 | n/a | 0.19 | -0.17 | 0.06 | 0.00 | -0.21 | -0.13 | 0.25 | -0.02 | nan |
| dollar_900M | 3771 | 50 | -2.01 | -4.05 | 0.521 vs 0.602 | -0.24 | n/a | 0.02 | -0.30 | -0.21 | 0.46 | -0.65 | 0.18 | 0.33 | -0.76 | nan |
| range_5 | 54748 | 730 | -2.15 | -4.39 | 0.554 vs 0.646 | 0.10 | n/a | 0.36 | -0.08 | 0.10 | 0.47 | 0.09 | 0.29 | -0.39 | 0.29 | nan |
| range_10 | 40922 | 546 | -2.15 | -4.38 | 0.547 vs 0.637 | 0.28 | n/a | 0.54 | -0.05 | 0.35 | 0.45 | 0.29 | 0.48 | -0.12 | 0.41 | nan |
| range_20 | 23938 | 319 | -2.26 | -4.48 | 0.528 vs 0.620 | 0.28 | n/a | 0.54 | -0.10 | 0.40 | 0.40 | 0.24 | 0.56 | -0.09 | 0.54 | nan |
| range_40 | 10068 | 134 | -2.30 | -4.51 | 0.512 vs 0.604 | 0.43 | n/a | 0.69 | 0.37 | 0.34 | 0.52 | 0.25 | 0.70 | 0.76 | 0.27 | nan |
| range_80 | 3118 | 42 | -2.22 | -4.44 | 0.495 vs 0.580 | 0.35 | n/a | 0.61 | -0.24 | 0.62 | -0.22 | -0.38 | 0.64 | 1.10 | 1.00 | nan |
| renko_4 | 50295 | 671 | -2.16 | -4.40 | 0.551 vs 0.643 | 0.30 | n/a | 0.56 | -0.00 | 0.33 | 0.45 | 0.20 | 0.53 | -0.06 | 0.58 | nan |
| renko_8 | 30825 | 411 | -2.10 | -4.35 | 0.537 vs 0.624 | 0.40 | n/a | 0.66 | 0.05 | 0.48 | 0.30 | 0.50 | 0.61 | -0.14 | 0.49 | nan |
| renko_16 | 12961 | 173 | -2.56 | -4.79 | 0.509 vs 0.612 | 0.23 | n/a | 0.49 | -0.19 | 0.38 | 0.49 | 0.25 | 0.34 | -0.07 | 0.43 | nan |
| renko_22 | 7472 | 100 | -2.28 | -4.51 | 0.501 vs 0.590 | 0.51 | n/a | 0.76 | -0.22 | 0.85 | 0.47 | 0.40 | 0.54 | 0.42 | 0.85 | nan |
| renko_38 | 2130 | 28 | -2.30 | -4.45 | 0.474 vs 0.559 | 0.38 | n/a | 0.63 | 0.32 | 0.33 | 1.29 | 0.19 | 1.28 | -0.24 | 0.04 | nan |
| imbal_130 | 5325 | 71 | -1.59 | -3.61 | 0.551 vs 0.616 | -0.07 | n/a | 0.19 | -0.22 | 0.13 | 0.12 | -0.60 | 0.39 | 0.32 | 0.03 | nan |
| imbal_260 | 1812 | 24 | -1.16 | -3.15 | 0.538 vs 0.584 | 0.38 | n/a | 0.63 | 0.16 | 0.68 | 0.25 | 0.32 | -0.45 | 2.72 | -0.52 | nan |
| kagi_8 | 36228 | 483 | -2.09 | -4.33 | 0.547 vs 0.634 | 0.28 | n/a | 0.53 | 0.00 | 0.35 | 0.44 | 0.39 | 0.37 | -0.11 | 0.30 | nan |
| kagi_16 | 16720 | 223 | -2.28 | -4.51 | 0.526 vs 0.619 | 0.28 | n/a | 0.54 | -0.09 | 0.42 | 0.10 | 0.34 | 0.37 | -0.19 | 0.62 | nan |
| kagi_32 | 5214 | 70 | -2.43 | -4.66 | 0.515 vs 0.613 | 0.15 | n/a | 0.40 | 0.20 | 0.03 | 0.11 | 0.21 | -0.46 | 0.62 | 0.60 | nan |
| kagi_60 | 1391 | 19 | -1.39 | -3.90 | 0.559 vs 0.617 | 1.14 | n/a | 1.40 | -0.41 | 1.91 | 0.57 | 1.27 | 0.74 | 1.80 | 0.80 | nan |
| linebreak3 | 1010 | 13 | -2.25 | -4.22 | 0.525 vs 0.617 | -0.82 | n/a | -0.56 | -0.94 | -0.88 | -0.48 | -1.26 | -0.40 | -0.35 | -1.08 | nan |
| ha_1m | 9139 | 122 | -2.08 | -4.21 | 0.550 vs 0.638 | -0.27 | n/a | -0.01 | -0.12 | -0.37 | -0.24 | -1.02 | 0.19 | 0.04 | 0.12 | nan |
| ha_2m | 5357 | 71 | -2.05 | -4.12 | 0.535 vs 0.620 | -0.46 | n/a | -0.20 | -0.48 | -0.45 | 0.65 | -0.60 | -0.11 | -0.04 | -1.12 | nan |
| ha_3m | 4005 | 53 | -1.71 | -3.79 | 0.543 vs 0.612 | -0.04 | n/a | 0.22 | -0.58 | 0.53 | 0.70 | -0.01 | 0.21 | 0.65 | -0.91 | nan |

60/60 comparator bracket, 5-min control (high variance, MDE of a pooled type about 3-6 pt):
| type | n (5 cells, PRE) | trades/wk | pts/trade net1 | net2 | win vs BE | effect vs random (bar-weighted pool, prereg) | effect vs random (minute-deduped pool) | diff vs 1m (prereg pool) | eff 2024-02..10 | eff 2024-11..2025-06 | 09:30-10 | 10-11 | 11-12 | 12-13 | 13-14 | 14:00-15:30 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| time_1m | 3345 | 45 | -2.38 | -4.39 | 0.491 vs 0.516 | -2.23 | -2.23 | 0.00 | -2.93 | -1.42 | -1.28 | -3.98 | -3.66 | 0.57 | -0.47 | nan |
| time_15s | 5469 | 73 | -1.34 | -3.40 | 0.502 vs 0.515 | -1.30 | -1.28 | 0.93 | -1.80 | -0.74 | -1.17 | -2.91 | -2.00 | 1.08 | 0.31 | nan |
| time_30s | 4346 | 58 | -2.09 | -4.13 | 0.490 vs 0.511 | -2.03 | -2.01 | 0.20 | -2.56 | -1.42 | 1.21 | -3.95 | -2.27 | 0.72 | -1.63 | nan |
| time_2m | 2561 | 34 | -2.67 | -4.64 | 0.485 vs 0.512 | -2.43 | -2.43 | -0.20 | -3.14 | -1.60 | -0.24 | -3.13 | -3.24 | 1.46 | -2.53 | nan |
| time_3m | 2308 | 31 | -0.13 | -2.17 | 0.510 vs 0.512 | 0.11 | 0.11 | 2.33 | -2.48 | 2.90 | 0.46 | 0.37 | -1.82 | 2.41 | -1.14 | nan |
| tick_250 | 5521 | 74 | -0.70 | -2.80 | 0.506 vs 0.512 | -1.20 | -0.63 | 1.03 | -2.16 | -0.08 | -1.69 | -1.78 | -2.67 | 1.83 | -1.45 | nan |
| tick_500 | 4270 | 57 | -1.37 | -3.43 | 0.500 vs 0.514 | -1.80 | -1.51 | 0.43 | -2.54 | -0.86 | -4.02 | -3.25 | -0.25 | 1.34 | -0.23 | nan |
| tick_1000 | 3238 | 43 | -1.50 | -3.54 | 0.495 vs 0.510 | -1.71 | -1.70 | 0.52 | -1.40 | -1.78 | -2.41 | -3.21 | -1.48 | 2.41 | 0.79 | nan |
| tick_2000 | 2257 | 30 | -2.57 | -4.61 | 0.493 vs 0.518 | -2.66 | -2.66 | -0.43 | -5.30 | 0.10 | -0.66 | -5.12 | -1.59 | -0.90 | 2.46 | nan |
| volume_500 | 4919 | 66 | -1.08 | -3.14 | 0.501 vs 0.512 | -1.73 | -1.11 | 0.50 | -2.34 | -0.89 | -3.82 | -2.75 | -1.30 | 0.35 | -2.38 | nan |
| volume_1200 | 3546 | 47 | -0.75 | -2.79 | 0.500 vs 0.507 | -1.20 | -1.03 | 1.03 | -1.31 | -0.80 | -1.07 | -2.85 | -1.62 | 3.32 | -0.48 | nan |
| volume_3600 | 1930 | 26 | -1.28 | -3.31 | 0.497 vs 0.510 | -1.63 | -1.62 | 0.59 | -2.61 | -0.41 | 0.87 | -1.30 | -5.48 | 0.20 | -0.77 | nan |
| dollar_150M | 5446 | 73 | -0.49 | -2.58 | 0.508 vs 0.512 | -1.17 | -0.47 | 1.06 | -2.39 | 0.16 | -1.87 | -1.54 | -1.80 | 1.47 | -1.12 | nan |
| dollar_300M | 4186 | 56 | -1.15 | -3.20 | 0.501 vs 0.513 | -1.70 | -1.26 | 0.53 | -2.44 | -0.78 | -4.40 | -2.62 | -1.78 | 0.88 | -1.36 | nan |
| dollar_900M | 2561 | 34 | -0.41 | -2.47 | 0.503 vs 0.507 | -0.69 | -0.73 | 1.54 | -2.25 | 1.02 | -2.31 | 0.38 | -2.88 | 1.12 | 1.23 | nan |
| range_5 | 10441 | 139 | -1.01 | -3.23 | 0.505 vs 0.515 | -0.56 | -0.80 | 1.67 | -0.58 | -0.42 | 0.92 | -0.26 | -0.66 | 0.18 | -0.11 | nan |
| range_10 | 9590 | 128 | -1.19 | -3.40 | 0.502 vs 0.514 | -0.43 | -1.01 | 1.80 | -1.04 | -0.01 | 0.47 | -0.35 | -1.44 | 0.34 | 0.04 | nan |
| range_20 | 7628 | 102 | -1.19 | -3.40 | 0.504 vs 0.516 | -0.03 | -1.00 | 2.20 | -0.64 | 0.30 | -0.71 | 0.38 | -0.28 | 1.02 | -0.08 | nan |
| range_40 | 4947 | 66 | -1.53 | -3.73 | 0.495 vs 0.510 | -0.27 | -1.46 | 1.95 | -2.34 | 0.95 | -1.85 | -1.15 | 0.38 | 1.56 | -0.31 | nan |
| range_80 | 2662 | 35 | -0.13 | -2.36 | 0.512 vs 0.514 | 1.74 | 0.54 | 3.96 | -0.33 | 2.86 | -0.82 | -0.32 | 0.65 | 4.81 | 1.31 | nan |
| renko_4 | 10264 | 137 | -1.31 | -3.52 | 0.503 vs 0.516 | -0.59 | -1.05 | 1.63 | -1.21 | -0.16 | 1.20 | -0.03 | -0.88 | -0.26 | -0.29 | nan |
| renko_8 | 8777 | 117 | -1.25 | -3.48 | 0.505 vs 0.517 | -0.15 | -1.11 | 2.08 | -1.32 | 0.54 | -0.61 | -0.00 | -1.08 | 0.71 | 0.29 | nan |
| renko_16 | 5818 | 78 | -2.72 | -4.92 | 0.491 vs 0.517 | -1.37 | -2.59 | 0.85 | -4.00 | 0.18 | -2.27 | -1.36 | -1.40 | 2.12 | -2.81 | nan |
| renko_22 | 4342 | 58 | -1.71 | -3.91 | 0.491 vs 0.507 | -0.41 | -1.70 | 1.81 | -2.38 | 0.73 | -1.89 | -0.56 | -2.20 | 1.50 | 0.54 | nan |
| renko_38 | 1997 | 27 | -4.99 | -7.13 | 0.465 vs 0.513 | -2.93 | -4.10 | -0.70 | -4.74 | -1.94 | 0.47 | -4.36 | -3.46 | 2.97 | -2.58 | nan |
| imbal_130 | 3380 | 45 | -0.43 | -2.46 | 0.507 vs 0.512 | -1.08 | -0.88 | 1.15 | -1.87 | 0.01 | -0.80 | -0.34 | -4.72 | 2.18 | -0.67 | nan |
| imbal_260 | 1794 | 24 | -2.00 | -3.94 | 0.489 vs 0.509 | -2.32 | -2.10 | -0.09 | -1.94 | -2.54 | 2.93 | -0.62 | -5.33 | -1.22 | -2.36 | nan |
| kagi_8 | 9376 | 125 | -0.97 | -3.18 | 0.506 vs 0.516 | -0.30 | -0.75 | 1.93 | -0.32 | -0.24 | 0.35 | 0.04 | -1.25 | 0.76 | -0.08 | nan |
| kagi_16 | 6883 | 92 | -1.05 | -3.26 | 0.504 vs 0.514 | 0.06 | -0.83 | 2.29 | -0.49 | 0.37 | -0.17 | 0.53 | -1.52 | 0.48 | 0.61 | nan |
| kagi_32 | 3784 | 50 | -0.98 | -3.17 | 0.496 vs 0.506 | -0.05 | -0.95 | 2.18 | -2.79 | 1.65 | -0.62 | -0.79 | -0.24 | 2.56 | 0.32 | nan |
| kagi_60 | 1662 | 22 | -0.92 | -3.14 | 0.509 vs 0.518 | 0.84 | -0.39 | 3.07 | -1.28 | 1.96 | -4.19 | 1.06 | -0.61 | 0.89 | 3.46 | nan |
| linebreak3 | 1211 | 16 | -0.85 | -2.76 | 0.498 vs 0.507 | -1.25 | -1.25 | 0.97 | -2.68 | 0.33 | -0.89 | -6.18 | 4.07 | -0.25 | -0.12 | nan |
| ha_1m | 3599 | 48 | -3.11 | -5.14 | 0.483 vs 0.515 | -2.96 | -2.96 | -0.73 | -4.23 | -1.65 | 0.07 | -5.09 | -4.85 | 0.20 | -0.76 | nan |
| ha_2m | 2842 | 38 | -1.99 | -4.01 | 0.492 vs 0.512 | -1.76 | -1.76 | 0.47 | -3.20 | -0.25 | -3.96 | -2.19 | -3.10 | 1.53 | -2.42 | nan |
| ha_3m | 2589 | 35 | -1.30 | -3.34 | 0.501 vs 0.514 | -1.02 | -1.02 | 1.21 | -2.47 | 0.48 | -3.87 | -2.53 | -2.27 | 2.64 | -0.90 | nan |

Is the ordering stable? Spearman correlation of the 34 type effects between the two PRE halves (2024-02..10 vs 2024-11..2025-06): control/model 0.21 (p 0.23), control/comparator 0.19 (p 0.27), 5x/model 0.27 (p 0.12), 5x/comparator 0.15 (p 0.41): the ordering of bar types is not stable (not distinguishable from random). By calendar year beyond PRE only the 30 holdout rows were read (section 5): no type ordering holds in 2024 / 2025 / 2026. Equal-resolution reading: ~1-min class (time_1m, tick_800 not in the 34, volume_1200, dollar_300M, range_40, renko_22, imbal_130, kagi_32, ha_1m) pooled effects -0.26, -0.13, -0.04, +0.44 (deduped -0.21), +0.32 (deduped -0.34), -0.19, +0.01 (deduped -0.55), -0.26; ~3-min class (time_3m, tick_2000, volume_3600, dollar_900M, range_80, renko_38, imbal_260, kagi_60, ha_3m, line break): +0.02, +0.18, -0.23, -0.36, +0.40, 0.00, -0.19, +0.48, -0.15, -0.24: all within the per-row paired MDE80 (median 1.68 pt/trade) of 1-min time bars and sign-unstable.

Plain line: does any bar type beat 1-minute time bars on identical signals by more than the MDE, and is the ordering stable across years? No, and no. The largest pooled gaps vs 1-min time bars at the model bracket (+0.70 range_40, +0.74 kagi_60, +0.60 renko_8, bar-weighted pool) become +0.05, +0.34 and -0.14 with the minute-deduplicated pool, all below the per-row paired MDE80 (median 1.68); they come from the pool counting a minute once per bar (a minute with 30 Renko bricks counts 30 times in the placebo), not from a better signal.

## 7. Realised-stop / bracket facts
The model bracket (15-pt stop from the entry price) has median target distance about 9 pt (LINES_C med_tdist; 5-60 pt window), so the realised R:R is about 0.6; net 1x pooled mean is -2.0 pts/trade on every type, break-even win rate 0.60-0.66 vs realised 0.50-0.57. The 60/60 comparator has break-even win rate ~0.51 and a pooled mean of -0.1 to -3.1 pts/trade with MDE ~3-6 pt per type.

## 8. Deviations and disclosures
- **Fill path.** The signal is computed on the bar type, the fill and the bracket are on the 1-min path: market order at the first 1-min open >= the bar's close time. Sub-minute and activity-sized bars wait a median 30-34 s (p90 55 s) for the fill; several bars of fast types (range_5 56.8, renko_4 43.2, kagi_8 18.4 bars per entry minute inside 10:00-14:00) map to one entry minute, so those types are 1-minute-grid entries with a different trigger; they do not trade faster. The swing target of the model bracket is the 1-min confirmed swing (not a swing of the bar type).
- **Bar-weighted pool (prereg) vs minute-deduplicated pool (sensitivity).** The prereg pool is every non-phantom bar of the type with a regime side (random bar of the same type). For fast types that weights busy minutes by their bar count and makes the effect look +0.2 to +0.5 pt/trade; the minute-deduplicated pool gives -0.2 to -0.6 for range/Renko/Kagi (out/zen/bars_fam/sens_pool.csv). The screen and the gates follow the prereg; the sensitivity says the positive pooled effects of the fast types are a pool-weighting artifact. G1 for the top 30 used the bar-weighted pool.
- **Line options.** The top-3 LINES_C lines (T3_233, TMA_377, SMMA_377 on close) were chosen with regime R1 on PRE (LINES_C PRE table) and their period is in bars of the type (233 bars is 233 minutes on 1-min bars, 700 minutes on 3-min bars, hours-to-days on activity bars). The 4,432 distinct rows include 908 where row i duplicates row j by construction.
- **5x types.** 15 s / 30 s: 5 consecutive bars inside a label day (75 s / 150 s, not clock aligned); 2m / 3m: 10m / 15m; tick / volume / dollar / range / Renko / imbalance / Kagi: separately built library files (tick_1250 ... kagi_300, builds in out/zen/bars_fam/build5x_*.log; existing files renko_20/40/80/110, range_200, volume_2500/6000, dollar_1500M, tick 5x, imbal_650, kagi_160 reused); line break 5x = 3-line break on 5-min closes; HA 5x = HA on 5/10/15-min bars. For time_1m the 5x variant equals the 5-min control.
- **Phantom bars.** Renko n = 0 bricks excluded from events and the pool (counts in section 1). Another 23-33% of Renko bricks close at a price level that was crossed but not the last trade (edge-not-traded column); those events are kept (they have a real trade n > 0).
- **Calibration drift.** Activity bars were calibrated on 2023-02/03; bars/day rise 25-30% over the sample; a type's per-year behaviour cannot be separated from that.
- **Holdout bookkeeping.** HOLD/X were read once for 60 rows (30 selected + the 30 time_1m companions, disclosed as extra reads) after the PREHOLD hash (autopilot/DS3_ZEN_BARS_PREHOLD.md sha256 313b73825b4eccf4f04e26734085dfad49f40188770e3fab18d3aabe075cb0a7). The by-window table is PRE only. G8 uses the per-cell studentised white reality-check p over the 5,408 valid rows (family N 5,600 listed; program N 291,130 would only raise the p). G10 not run.
- **Selection effect.** The prereg rule (top 30 by PRE effect) picks the highest-variance rows: all 30 are 60/60; the top-30 PRE effect (mean 7.4) is a mixture of luck and the large bracket variance, and it shrank to 1.9 in HOLD.
- **Not covered / not built.** UniRenko / with-wick Renko, session-anchored time bars as entry types (identical to epoch-aligned bars for N dividing 30), second pass on a changed top-3 entry cell, NT8 identity check (K5, user), G10 replay, Jurik. The lib bug reported by D3ZF1 (zen_struct._grid with fill_mode=1) does not touch this family: all entries are market orders and every cell is a lookup into Z.simulate (identity to Z.simulate checked on 200 random entries, test 10 in bf_test.py).
- **Screen basis.** Mapped conservative 1-min fills (0.05-0.13 pt/trade more conservative than the 1-s path on tight stops).

## 9. Files
Code: l2vast/ds3/code/zen/bars_fam/{bf_eng,bf_run,bf_merge,bf_top,bf_hold,bf_final,bf_tables,bf_sens,bf_md,bf_report,bf_test,bf_k4,bf_k4md,bf_delay}.py. Output: l2vast/ds3/out/zen/bars_fam/ (pre_all.parquet = every cell, pre_rc.json, top30_keys.json, top30_pre_extras.pkl, hold_res.pkl, top30_final.csv, ref_cells.parquet, type_table.parquet, sens_pool.csv, k4_*.csv/json/md, looks.jsonl, bf_test.log). Prereg l2vast/ds3/prereg/ZEN_BARS_prereg.md(+cells csv), PREHOLD autopilot/DS3_ZEN_BARS_PREHOLD.md.

DONE BARS
