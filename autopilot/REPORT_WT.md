# REPORT WT - PRIORITY 0: WilderTrail (WT) RE-SCORE ON THE CORRECTED NT8-FAITHFUL ENGINE

**Verdict: LEAD (strong), 0 FOUND.** The most important number: WT as a *separate-account sleeve* (cell ATR 14 / mult 3 / no EMA filter / 10-minute signal bars / 60-60 bracket, `ATR14_m3_ema0_tf10_X1`) adds weekly Sharpe **+0.37 / +0.42 / +0.31 (clean / H1 / H2) at a 20% share** of the 8/8 pair (bootstrap 90% CI of the all-in uplift +0.19..+0.58, 2x slippage +0.34/+0.41/+0.25, worst-decile-week correlation with the pair -0.20, all-weeks correlation 0.00), but it **fails the plateau gate (4 of 8 neighbours keep 75% of the uplift)**, has **no long-history support** (2013-2022 Sharpe +0.06 at a fixed 60-pt bracket, -1.38 at the faithful scaled bracket 60 x price/20000), and **the uplift does not survive being run as a third book in the same NT8 account** (position netting with ST/HM: trio ATR14/m3/tf10 at 8/8/4 = weekly Sharpe 1.65 all-in vs pair 1.86; the same sleeve in its own account = 2.28). Cells: 432 grid + 2 fixed specs (12 fully scored). Runtime about 1.3 h wall clock on a 7-worker pool (engine build and verification about 25 min; grid 26 s; scoring with 200-draw nulls and plateau 4 min; family null 25 min; tick-level TH 8 min; 1-minute history 15 min). Status: `outputs/autopilot/status/WT.txt`. The B3-era rejection ('TH collapses WT') is **confirmed for WT's own live TH setting** (ml 10 / req 2 / 30 s: all-in Sharpe 1.54 -> -0.90) while WT-LIVE alone, TH off, is a Sharpe 1.98 book on the corrected engine (see (a)).

## 0. What WT is (confirmed from code) and how it was scored
- **Spec (code: `night/b3_dispatch.py` family F2, `night/b3_refs.py` WT_MODAL, `night_b10/b10_build.py` spec_B, `night_b10/b10_trackB.py` LIVE):** Wilder ATR ratchet trail flip. atr = RMA(TR, n) (Wilder) on the signal-timeframe bars; trend long while close stays above the stop; `stop = max(stop, close - m*atr)` (ratchets up only, never down); flip short when close < stop, then `stop = close + m*atr` and ratchet down only (mirror). Anchor = close, reset on flip, confirm = 1 close. Entry at the flip bar close -> next 1-minute open; EMA(e) filter on the signal-timeframe close (buy needs close > EMA, sell close < EMA); 60-pt stop / 60-pt target bracket (60/60), one open trade per book; same session windows as ST/HM (signal-bar start 18:00-15:00 ET except 09:00-09:58, flat at the open of the 16:55 bar). The B10 'live' reference is `B_WT_20_2.0_100` (ATR 20, mult 2.0, EMA 100, 1-min), the book named in the brief is `B_WT_20_1.75_50` (mult 1.75, EMA 50); the older WT_MODAL used a 45/0.75R bracket (not used here: the brief and B10 use 60/60). My implementation (`ap_wt_core.py`) reproduces the harness `dispatch('F2')` flips **bit-for-bit** (checked for ATR20/m2 and ATR10/m3: all 34,531 / 18,490 buy flips and sell flips equal). WT is **not** live and is not in the NT8 trade list, so its NT8 fills are unverified (the 1-second path is validated for ST/HM only).
- **Engine (fidelity):** the live pair engine uses the **1-second path** (nt8sim order-level account model: one account position, FIFO netting of an entry against the oldest opposite lot, orphan protective orders, stop/target resolved on second bars, stop gaps fill at the previous second close). I extended it to three books (`ap_wt_core.acct3`, tie priority ST > HM > WT) and the b11 account to any number of books (`ap_wt_acct.py`: per-book 5R/-2R day rule, combined day lock cap 8R / arm 2R / keep 33% from 00:00, combined week floor -8R, per-book week rule off; thresholds in dollars, R = $9,600). **Verification before use:** `acct3` with ST+HM reproduces `ROWS_corrected_engine.parquet` field-by-field (13,089 rows, all equal); `ap_wt_acct` on those rows reproduces the daily P&L of `B.Cfg(wk_floor=8, wk_loss_pb=None)` with **max abs difference $0.00** over 950 days (net $2,811,678.40). Baseline pair computed in a clean process (never imported b10_core before b11_nt8): weekly Sharpe clean/H1/H2 **1.46/2.83/2.30** (B.Cfg() default: 1.35/1.65/2.26). 2013-2022 history uses the 1-minute engine (P1 machinery, 1-min bar fills, stop-first, entries at next open): there is no 1-second data before 2023-02-09, so the history is a lower-fidelity read (stated wherever it appears).
- **Fill model / costs:** entry at the next 1-min bar open, 1 tick/side slippage (0.5 pt per round trip per contract) + NT8 commission $34.88 per 8-lot trade; 2x-slippage test = 2 ticks/side on both baseline and variant. Executability: WT is a trend-flip book on NQ, same instrument, sessions and order types as ST/HM: executable at NinjaTrader Brokerage via Rithmic. Margin: not verified (no margin source on the box); WT at 8 NQ adds up to 8 contracts to the pair's 16 in the same direction (50% more gross exposure), and WT holds across the Globex night (flat only 16:55-18:00), so overnight margin applies.
- **Pre-registration:** `PREREG_AUTOPILOT.md`, section 'PRIORITY 0 - WT RE-SCORE (C-WT)', written before the grid or any WT scoring (only a signal-equality check, the pair reproduction and a smoke run of the live spec preceded it).

## (a) WT standalone at 8 NQ
### a1. Corrected NT8-faithful 1-second path, clean / H1 / H2 / all-in (one book of 8 NQ, 60/60 bracket)
No rules = raw book; live rules = per-book 5R/-2R day rule + combined day lock + week floor. Pair row for comparison.

| cell | span | net | sharpe | sortino | mar | maxdd | worst_week | cvar5 | cvar10 | neg_wk |
|---|---|---|---|---|---|---|---|---|---|---|
| WT-LIVE no rules (8 NQ, 1 book) | clean | 790,283 | 1.02 | 1.61 | 1.83 | 431,755 | -168,599 | -107,774 | -83,889 | 41.90 |
| WT-LIVE no rules (8 NQ, 1 book) | H1 | 748,738 | 4.03 | 8.26 | 3.54 | 211,788 | -94,551 | -70,726 | -61,968 | 25.00 |
| WT-LIVE no rules (8 NQ, 1 book) | H2 | 63,948 | 0.20 | 0.27 | 0.15 | 413,845 | -173,424 | -134,459 | -106,874 | 44.44 |
| WT-LIVE no rules (8 NQ, 1 book) | all | 1,602,969 | 1.23 | 1.93 | 3.71 | 431,755 | -173,424 | -113,591 | -91,202 | 39.88 |
| WT-LIVE live rules (8 NQ, 1 book) | clean | 926,142 | 1.40 | 2.49 | 3.33 | 277,829 | -77,099 | -72,602 | -63,391 | 41.90 |
| WT-LIVE live rules (8 NQ, 1 book) | H1 | 573,509 | 3.20 | 6.74 | 2.97 | 192,798 | -65,727 | -56,132 | -52,718 | 32.14 |
| WT-LIVE live rules (8 NQ, 1 book) | H2 | 515,736 | 2.92 | 5.48 | 3.09 | 166,650 | -70,878 | -57,100 | -46,854 | 30.56 |
| WT-LIVE live rules (8 NQ, 1 book) | all | 2,015,388 | 1.98 | 3.64 | 7.25 | 277,829 | -77,099 | -70,082 | -59,698 | 38.10 |
| WT-B10 no rules (8 NQ, 1 book) | clean | 832,829 | 1.11 | 1.72 | 2.16 | 386,259 | -169,059 | -106,919 | -82,939 | 44.76 |
| WT-B10 no rules (8 NQ, 1 book) | H1 | 732,798 | 3.21 | 7.44 | 4.40 | 166,523 | -84,681 | -76,195 | -65,202 | 39.29 |
| WT-B10 no rules (8 NQ, 1 book) | H2 | 104,458 | 0.29 | 0.41 | 0.28 | 378,870 | -194,922 | -181,009 | -132,918 | 50.00 |
| WT-B10 no rules (8 NQ, 1 book) | all | 1,670,085 | 1.24 | 1.94 | 4.23 | 394,558 | -194,922 | -124,166 | -96,305 | 45.24 |
| WT-B10 live rules (8 NQ, 1 book) | clean | 1,025,017 | 1.53 | 2.81 | 4.03 | 254,416 | -77,429 | -69,294 | -60,808 | 45.71 |
| WT-B10 live rules (8 NQ, 1 book) | H1 | 374,179 | 2.10 | 4.36 | 2.85 | 131,402 | -74,383 | -59,867 | -53,471 | 42.86 |
| WT-B10 live rules (8 NQ, 1 book) | H2 | 626,460 | 2.92 | 5.95 | 4.96 | 126,385 | -77,828 | -70,664 | -56,468 | 33.33 |
| WT-B10 live rules (8 NQ, 1 book) | all | 2,025,656 | 1.93 | 3.65 | 7.96 | 254,416 | -77,828 | -70,164 | -60,118 | 42.26 |
| PAIR ST+HM 8/8 (B.Cfg(wk_floor=8,wk_loss_pb=None)) | clean | 1,329,959 | 1.46 | 2.78 | 4.75 | 280,110 | -81,874 | -78,736 | -78,009 | 42.86 |
| PAIR ST+HM 8/8 (B.Cfg(wk_floor=8,wk_loss_pb=None)) | H1 | 593,797 | 2.83 | 6.09 | 3.91 | 151,713 | -78,287 | -77,610 | -66,030 | 39.29 |
| PAIR ST+HM 8/8 (B.Cfg(wk_floor=8,wk_loss_pb=None)) | H2 | 761,254 | 2.30 | 4.69 | 3.50 | 217,425 | -82,524 | -81,089 | -79,185 | 44.44 |
| PAIR ST+HM 8/8 (B.Cfg(wk_floor=8,wk_loss_pb=None)) | all | 2,685,011 | 1.86 | 3.63 | 9.59 | 280,110 | -82,524 | -79,220 | -78,243 | 42.86 |

Reading: WT-LIVE alone has an all-in weekly Sharpe of **1.98 (live rules)**, equal to the whole 8/8 pair's 1.86 with half its contracts; but it is regime-shaped like the pair (raw Sharpe 1.02 / 4.03 / 0.20 on clean / H1 / H2; the rules lift H2 to 2.92 by cutting the bad days). WT-B10 (mult 1.75, EMA 50) gives 1.93. Trade counts: 6,322 trades in the pair window (7.6/day); mean 2.30 pt/trade = 0.038 bracket units (60 pt) before costs of about 0.72 pt/trade.

### a2. Scaled-bracket history 2013-2026 (1-minute engine; P1 scalings a / b / c)
Scalings exactly as the P1 pair runs (`ap_p1_scaled.py`): a = 60 x raw price/20000 (faithful), b = clean-median ratio to ADR20 (k = 0.2109), c = clean-median ratio to ATR(120, 1-min) (m = 10.57), plus the fixed 60-pt bracket; costs real (1 tick/side + $4.36/contract), cost-scaled (costs x bracket/60) and gross (zero). Each cell is net R (R = $9,600 per trade at full size; x $9,600 = $ at 8 NQ-equivalent) / weekly Sharpe, live account rules (single book). Pair reference (P1): a_gross 2013-22 +0.06, a_real -1.38, a_scaled -0.38, fixed_real -0.78; 2023-26 1.62 / 1.25 / 1.28 / 1.78.

**WT-LIVE (ATR20 / 2.0 / EMA100 / 1-min / 60-60):**

| span | fixed_real | fixed_gross | a_real | a_scaled | a_gross | b_real | b_scaled | b_gross | c_real | c_scaled | c_gross |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 2013 | +3 / +0.43 | +6 / +0.96 | -115 / -3.97 | -56 / -1.91 | -44 / -1.49 | -158 / -5.71 | -77 / -2.63 | -63 / -2.06 | -146 / -5.61 | -76 / -2.95 | -68 / -2.60 |
| 2014 | -12 / -1.26 | -8 / -0.90 | -56 / -1.77 | -9 / -0.26 | -2 / -0.05 | -88 / -2.91 | -8 / -0.28 | -2 / -0.05 | -92 / -3.42 | -36 / -1.32 | -25 / -0.92 |
| 2015 | +7 / +0.59 | +11 / +0.94 | -36 / -0.95 | +12 / +0.30 | +12 / +0.31 | -46 / -1.21 | +7 / +0.19 | +30 / +0.82 | -8 / -0.24 | +30 / +0.94 | +40 / +1.24 |
| 2016 | +7 / +0.63 | +11 / +1.01 | -60 / -2.38 | -23 / -0.89 | -10 / -0.40 | -80 / -2.91 | -32 / -1.12 | -12 / -0.45 | -57 / -2.27 | -10 / -0.38 | -1 / -0.06 |
| 2017 | +4 / +0.36 | +7 / +0.72 | -2 / -0.11 | +21 / +0.90 | +30 / +1.31 | -80 / -3.15 | -16 / -0.57 | -9 / -0.33 | -72 / -2.51 | -16 / -0.52 | +0 / +0.00 |
| 2018 | -3 / -0.16 | +4 / +0.20 | -49 / -1.54 | -14 / -0.44 | -9 / -0.29 | -26 / -0.80 | -3 / -0.08 | +17 / +0.53 | -22 / -0.82 | -6 / -0.22 | +9 / +0.31 |
| 2019 | +13 / +0.75 | +18 / +1.07 | -34 / -1.30 | -15 / -0.54 | -14 / -0.51 | -34 / -1.27 | -8 / -0.31 | +4 / +0.15 | -23 / -0.95 | -6 / -0.26 | +5 / +0.20 |
| 2020 | -13 / -0.53 | +9 / +0.37 | -62 / -1.71 | -52 / -1.42 | -37 / -1.06 | -11 / -0.40 | -8 / -0.27 | +6 / +0.20 | +10 / +0.34 | +12 / +0.39 | +25 / +0.80 |
| 2021 | +14 / +0.60 | +21 / +0.93 | +11 / +0.40 | +16 / +0.58 | +27 / +1.03 | +35 / +1.16 | +38 / +1.26 | +54 / +1.81 | +42 / +1.55 | +45 / +1.65 | +55 / +2.00 |
| 2022 | +27 / +0.73 | +44 / +1.20 | -75 / -2.16 | -66 / -1.89 | -53 / -1.56 | +43 / +1.31 | +42 / +1.26 | +50 / +1.56 | +32 / +1.27 | +29 / +1.17 | +37 / +1.56 |
| 2023 | +3 / +0.13 | +11 / +0.44 | -20 / -0.61 | -15 / -0.46 | +3 / +0.10 | +23 / +0.64 | +27 / +0.73 | +39 / +1.07 | -6 / -0.26 | -5 / -0.20 | +8 / +0.35 |
| 2024 | +65 / +1.65 | +75 / +1.92 | +71 / +1.82 | +72 / +1.84 | +79 / +2.07 | +29 / +0.80 | +29 / +0.81 | +39 / +1.05 | -3 / -0.09 | -3 / -0.10 | +5 / +0.17 |
| 2025 | +52 / +1.57 | +70 / +2.20 | +54 / +1.68 | +52 / +1.65 | +69 / +2.19 | +62 / +1.77 | +58 / +1.62 | +71 / +2.06 | +80 / +2.70 | +77 / +2.62 | +92 / +3.04 |
| 2026 | +58 / +2.27 | +67 / +2.89 | -2 / -0.10 | -6 / -0.23 | +12 / +0.47 | +35 / +1.51 | +31 / +1.35 | +56 / +2.29 | +58 / +2.60 | +54 / +2.42 | +67 / +2.93 |
| 2013-22 | +45 / +0.24 | +121 / +0.66 | -479 / -1.57 | -186 / -0.60 | -100 / -0.33 | -446 / -1.45 | -65 / -0.21 | +75 / +0.25 | -336 / -1.20 | -34 / -0.12 | +76 / +0.27 |
| 2023-26 | +173 / +1.41 | +217 / +1.85 | +119 / +0.95 | +120 / +0.95 | +177 / +1.42 | +139 / +1.11 | +135 / +1.07 | +193 / +1.52 | +134 / +1.27 | +129 / +1.22 | +177 / +1.65 |
| clean | +102 / +1.49 | +124 / +1.87 | +118 / +1.73 | +120 / +1.76 | +145 / +2.19 | +78 / +1.13 | +79 / +1.13 | +102 / +1.46 | +56 / +0.94 | +54 / +0.91 | +77 / +1.30 |
| H1 | +46 / +2.34 | +55 / +2.87 | +31 / +1.58 | +30 / +1.52 | +37 / +1.91 | +50 / +2.65 | +47 / +2.44 | +55 / +2.97 | +50 / +3.61 | +49 / +3.53 | +57 / +4.02 |
| H2 | +45 / +2.18 | +55 / +2.92 | -4 / -0.21 | -8 / -0.37 | +9 / +0.42 | +30 / +1.54 | +26 / +1.36 | +49 / +2.36 | +53 / +2.76 | +49 / +2.58 | +60 / +3.02 |

**WT-B10 (ATR20 / 1.75 / EMA50 / 1-min):**

| span | fixed_real | fixed_gross | a_real | a_scaled | a_gross | b_real | b_scaled | b_gross | c_real | c_scaled | c_gross |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 2013 | -5 / -0.83 | -2 / -0.35 | -92 / -3.47 | -31 / -1.12 | -23 / -0.80 | -116 / -4.20 | -39 / -1.34 | -28 / -0.99 | -158 / -6.12 | -92 / -3.48 | -82 / -3.12 |
| 2014 | -3 / -0.44 | -0 / -0.00 | -109 / -4.58 | -63 / -2.64 | -56 / -2.30 | -96 / -3.27 | -20 / -0.68 | -11 / -0.36 | -110 / -4.79 | -58 / -2.56 | -54 / -2.39 |
| 2015 | +10 / +0.80 | +14 / +1.13 | -38 / -0.97 | +6 / +0.14 | +20 / +0.50 | -61 / -1.88 | -15 / -0.45 | +15 / +0.40 | -42 / -1.33 | -4 / -0.14 | +10 / +0.32 |
| 2016 | +8 / +0.78 | +12 / +1.17 | -91 / -3.27 | -42 / -1.53 | -34 / -1.34 | -121 / -4.09 | -64 / -2.06 | -51 / -1.73 | -69 / -2.56 | -26 / -0.94 | -16 / -0.57 |
| 2017 | +4 / +0.44 | +8 / +0.80 | -12 / -0.53 | +9 / +0.39 | +20 / +0.88 | -80 / -2.94 | -11 / -0.44 | -1 / -0.04 | -44 / -1.58 | +12 / +0.42 | +18 / +0.63 |
| 2018 | -13 / -0.65 | -5 / -0.27 | -95 / -2.93 | -66 / -1.93 | -31 / -0.92 | -76 / -2.68 | -56 / -1.94 | -27 / -0.91 | -26 / -1.02 | -5 / -0.19 | +9 / +0.35 |
| 2019 | -15 / -0.95 | -9 / -0.59 | -31 / -1.04 | -13 / -0.44 | -7 / -0.24 | -68 / -2.62 | -50 / -1.91 | -37 / -1.39 | -64 / -2.39 | -46 / -1.68 | -38 / -1.40 |
| 2020 | -8 / -0.32 | -7 / -0.30 | -68 / -2.05 | -49 / -1.44 | -39 / -1.22 | -27 / -1.05 | -20 / -0.77 | -11 / -0.39 | +29 / +0.95 | +28 / +0.89 | +38 / +1.21 |
| 2021 | +2 / +0.07 | +7 / +0.29 | -36 / -1.55 | -36 / -1.61 | -18 / -0.79 | +51 / +1.68 | +54 / +1.81 | +64 / +2.20 | +30 / +1.17 | +31 / +1.20 | +44 / +1.64 |
| 2022 | -12 / -0.33 | +1 / +0.02 | -92 / -2.52 | -82 / -2.21 | -59 / -1.68 | +35 / +0.98 | +33 / +0.91 | +50 / +1.45 | +6 / +0.23 | +4 / +0.14 | +8 / +0.29 |
| 2023 | +10 / +0.31 | +15 / +0.49 | +13 / +0.37 | +18 / +0.51 | +14 / +0.43 | -1 / -0.03 | +2 / +0.07 | +18 / +0.48 | +7 / +0.29 | +8 / +0.33 | +19 / +0.73 |
| 2024 | +60 / +1.67 | +69 / +1.99 | +65 / +1.68 | +65 / +1.68 | +75 / +1.99 | +23 / +0.67 | +24 / +0.68 | +34 / +0.99 | +21 / +0.72 | +21 / +0.70 | +33 / +1.09 |
| 2025 | +20 / +0.58 | +54 / +1.61 | +3 / +0.09 | +2 / +0.06 | +20 / +0.59 | +12 / +0.35 | +9 / +0.28 | +18 / +0.53 | +43 / +1.34 | +41 / +1.27 | +51 / +1.59 |
| 2026 | +95 / +3.64 | +120 / +4.84 | +33 / +1.27 | +30 / +1.15 | +38 / +1.42 | +41 / +1.63 | +37 / +1.48 | +48 / +1.94 | +57 / +2.15 | +53 / +2.01 | +66 / +2.56 |
| 2013-22 | -33 / -0.17 | +18 / +0.09 | -665 / -2.22 | -368 / -1.21 | -228 / -0.76 | -559 / -1.85 | -189 / -0.63 | -37 / -0.12 | -446 / -1.60 | -157 / -0.57 | -64 / -0.23 |
| 2023-26 | +191 / +1.58 | +265 / +2.25 | +115 / +0.88 | +115 / +0.88 | +149 / +1.17 | +76 / +0.63 | +74 / +0.61 | +117 / +0.96 | +144 / +1.31 | +139 / +1.26 | +184 / +1.67 |
| clean | +99 / +1.43 | +136 / +2.03 | +101 / +1.38 | +102 / +1.39 | +124 / +1.75 | +34 / +0.49 | +34 / +0.49 | +60 / +0.86 | +57 / +0.95 | +56 / +0.93 | +78 / +1.29 |
| H1 | +38 / +2.08 | +49 / +2.67 | +34 / +1.75 | +33 / +1.69 | +34 / +1.79 | +31 / +1.86 | +31 / +1.82 | +33 / +2.07 | +36 / +2.60 | +35 / +2.53 | +43 / +3.03 |
| H2 | +61 / +2.76 | +85 / +4.24 | +7 / +0.31 | +4 / +0.17 | +11 / +0.48 | +18 / +0.95 | +15 / +0.77 | +24 / +1.25 | +50 / +2.12 | +46 / +1.97 | +57 / +2.48 |

Span detail for the faithful scaling and the fixed bracket (maxDD in R, trades per day, mean points per trade in bracket units):

| run | span | netR | net_usd88 | sharpe | maxddR | trades_day | pts_bracket | n |
|---|---|---|---|---|---|---|---|---|
| LIVE_a_real | 2013-22 | -478.58 | -4,594,387 | -1.57 | 482.81 | 4.24 | -0.00 | 10810 |
| LIVE_a_real | 2023-26 | 119.24 | 1,144,752 | 0.95 | 56.17 | 4.63 | 0.04 | 4370 |
| LIVE_a_real | clean | 117.64 | 1,129,382 | 1.73 | 23.83 | 4.57 | 0.07 | 2350 |
| LIVE_a_real | H1 | 30.86 | 296,282 | 1.58 | 19.95 | 4.20 | 0.07 | 558 |
| LIVE_a_real | H2 | -4.50 | -43,170 | -0.21 | 46.55 | 5.18 | 0.00 | 916 |
| LIVE_a_scaled | 2013-22 | -186.47 | -1,790,074 | -0.60 | 193.10 | 4.25 | -0.00 | 10835 |
| LIVE_a_scaled | 2023-26 | 119.65 | 1,148,683 | 0.95 | 58.82 | 4.63 | 0.04 | 4369 |
| LIVE_a_scaled | clean | 119.59 | 1,148,065 | 1.76 | 23.85 | 4.58 | 0.07 | 2352 |
| LIVE_a_scaled | H1 | 29.63 | 284,453 | 1.52 | 20.27 | 4.20 | 0.07 | 558 |
| LIVE_a_scaled | H2 | -7.63 | -73,268 | -0.37 | 48.43 | 5.15 | 0.00 | 912 |
| LIVE_a_gross | 2013-22 | -100.19 | -961,854 | -0.33 | 112.03 | 4.12 | -0.01 | 10522 |
| LIVE_a_gross | 2023-26 | 177.07 | 1,699,830 | 1.42 | 41.47 | 4.52 | 0.04 | 4268 |
| LIVE_a_gross | clean | 144.97 | 1,391,690 | 2.19 | 23.01 | 4.46 | 0.07 | 2290 |
| LIVE_a_gross | H1 | 37.46 | 359,597 | 1.91 | 18.73 | 4.11 | 0.07 | 546 |
| LIVE_a_gross | H2 | 8.95 | 85,896 | 0.42 | 35.17 | 5.06 | 0.01 | 896 |
| LIVE_fixed_real | 2013-22 | 45.08 | 432,809 | 0.24 | 39.11 | 2.25 | 0.02 | 5658 |
| LIVE_fixed_real | 2023-26 | 172.92 | 1,660,078 | 1.41 | 32.09 | 4.72 | 0.05 | 4445 |
| LIVE_fixed_real | clean | 101.97 | 978,868 | 1.49 | 26.36 | 4.42 | 0.06 | 2271 |
| LIVE_fixed_real | H1 | 46.42 | 445,664 | 2.34 | 22.16 | 4.62 | 0.09 | 614 |
| LIVE_fixed_real | H2 | 45.05 | 432,484 | 2.18 | 22.96 | 6.54 | 0.04 | 1157 |
| B10_a_real | 2013-22 | -664.57 | -6,379,828 | -2.22 | 671.78 | 4.29 | -0.02 | 10955 |
| B10_a_real | 2023-26 | 114.87 | 1,102,733 | 0.88 | 39.75 | 4.83 | 0.04 | 4568 |
| B10_a_real | clean | 101.21 | 971,643 | 1.38 | 34.05 | 4.84 | 0.06 | 2488 |
| B10_a_real | H1 | 33.83 | 324,804 | 1.75 | 18.32 | 4.18 | 0.08 | 556 |
| B10_a_real | H2 | 6.57 | 63,072 | 0.31 | 22.20 | 5.30 | 0.01 | 938 |
| B10_a_gross | 2013-22 | -228.04 | -2,189,201 | -0.76 | 239.69 | 4.17 | -0.02 | 10627 |
| B10_a_gross | 2023-26 | 148.72 | 1,427,740 | 1.17 | 35.20 | 4.64 | 0.03 | 4383 |
| B10_a_gross | clean | 123.64 | 1,186,956 | 1.75 | 31.25 | 4.62 | 0.05 | 2375 |
| B10_a_gross | H1 | 34.16 | 327,933 | 1.79 | 17.09 | 4.11 | 0.07 | 547 |
| B10_a_gross | H2 | 10.58 | 101,535 | 0.48 | 22.76 | 5.12 | 0.00 | 906 |
| B10_fixed_real | 2013-22 | -32.63 | -313,266 | -0.17 | 66.88 | 2.26 | 0.01 | 5698 |
| B10_fixed_real | 2023-26 | 191.36 | 1,837,057 | 1.58 | 28.06 | 5.07 | 0.05 | 4769 |
| B10_fixed_real | clean | 99.15 | 951,869 | 1.43 | 28.06 | 4.70 | 0.06 | 2412 |
| B10_fixed_real | H1 | 38.12 | 365,960 | 2.08 | 13.67 | 4.99 | 0.07 | 664 |
| B10_fixed_real | H2 | 60.93 | 584,966 | 2.76 | 16.51 | 7.11 | 0.05 | 1259 |

Full per-year tables with all columns (net R, $ at 8, Sharpe, maxDD R, trades/day, pts/bracket, expectancy R, n, median bracket) for all 22 runs: `outputs/autopilot/wt/HIST_tables.txt`, `HIST_all.csv`.

**Reading:** the same pattern as the pair. With the faithful scaled bracket WT is negative in 2013-2022 even gross (-0.33; real -1.57), positive only from 2024 (1.8 in 2024, 1.7 in 2025, -0.1 in 2026 because a bracket of 87 pt at 29k is wider than the 60 pt the 2026 result needs); at a fixed 60-pt bracket the 2013-2022 Sharpe is +0.24 (real) / +0.66 (gross) but that bracket was 2% of price in 2013-2016 (1 trade/day vs 4.5). The 2023-2026 result is the live-window regime, not a 13-year property. Scalings do not rescue it, exactly as for the pair. Because the bracket width matters this much, the plateau gate below has bite.

## (b) Trio ST + HM + WT in one NT8 account (netting, orphan orders) vs the pair
Sizes are ST/HM/WT contracts. Additive = the literal sizes with ST/HM unchanged where 8/8; constant-risk = every size x 16/(sum of contracts) so the total is 16 contract-equivalents. Rules in dollars (R = $9,600, as live), combined day lock and week floor apply to all three books. WT columns: LIVE = ATR20/2.0/EMA100/1-min; B10 = ATR20/1.75/EMA50/1-min; TOP1 = ATR10/3/no EMA/10-min (best clean uplift); T3 = ATR14/3/no EMA/10-min (best gate profile). All WT cells here use the 60/60 bracket (the trail-only cells need a different exit and the account model's order logic is bracket-only).

| cell | framing | Sh clean | Sh H1 | Sh H2 | Sh all | net $ all | maxDD $ all | worst wk $ | CVaR5 $ | CVaR10 $ | Sortino | MAR | %neg wk | corr w/ pair all wks | corr worst-decile | increment corr w/ pair | increment corr worst-dec |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PAIR 8/8 | - | 1.46 | 2.83 | 2.30 | 1.86 | 2,685,011 | 280,110 | -82,524 | -79,220 | -78,243 | 3.63 | 9.59 | 42.86 | 1.00 | 1.00 | nan | nan |
| TRIO LIVE 8/8/4 | add | 1.51 | 4.22 | 1.66 | 1.94 | 3,349,014 | 349,280 | -84,203 | -80,584 | -79,521 | 3.86 | 9.59 | 40.48 | 0.67 | -0.25 | -0.22 | -0.27 |
| TRIO LIVE 8/8/8 | add | 1.32 | 2.13 | 1.33 | 1.46 | 2,707,456 | 449,780 | -85,030 | -80,828 | -79,786 | 2.74 | 6.02 | 44.05 | 0.58 | -0.35 | -0.24 | -0.37 |
| TRIO LIVE 6/6/4 | add | 1.03 | 3.91 | 2.48 | 1.80 | 2,753,649 | 357,331 | -85,985 | -80,052 | -78,866 | 3.44 | 7.71 | 40.48 | 0.74 | -0.23 | -0.30 | -0.26 |
| TRIO LIVE 6/6/6 | add | 1.50 | 3.93 | 2.68 | 2.15 | 3,575,922 | 326,480 | -83,924 | -79,944 | -78,998 | 4.31 | 10.95 | 36.31 | 0.69 | -0.16 | -0.24 | -0.19 |
| TRIO LIVE 8/8/4 | const | 1.09 | 4.60 | 2.71 | 1.96 | 2,992,634 | 343,137 | -79,798 | -79,153 | -78,455 | 3.82 | 8.72 | 38.10 | 0.74 | -0.25 | -0.30 | -0.29 |
| TRIO LIVE 8/8/8 | const | 1.43 | 4.09 | 2.18 | 2.01 | 3,126,454 | 324,622 | -81,915 | -79,824 | -78,833 | 3.88 | 9.63 | 36.90 | 0.69 | -0.18 | -0.32 | -0.21 |
| TRIO LIVE 6/6/4 | const | 1.03 | 3.91 | 2.48 | 1.80 | 2,753,649 | 357,331 | -85,985 | -80,052 | -78,866 | 3.44 | 7.71 | 40.48 | 0.74 | -0.23 | -0.30 | -0.26 |
| TRIO LIVE 6/6/6 | const | 1.43 | 4.09 | 2.18 | 2.01 | 3,126,454 | 324,622 | -81,915 | -79,824 | -78,833 | 3.88 | 9.63 | 36.90 | 0.69 | -0.18 | -0.32 | -0.21 |
| TRIO B10 8/8/4 | add | 1.46 | 2.66 | 2.59 | 1.93 | 3,459,563 | 410,573 | -82,830 | -79,803 | -78,940 | 3.88 | 8.43 | 42.86 | 0.65 | -0.48 | -0.20 | -0.50 |
| TRIO B10 8/8/8 | add | 1.31 | 2.19 | 0.85 | 1.33 | 2,530,134 | 417,098 | -87,182 | -81,999 | -80,536 | 2.47 | 6.07 | 47.02 | 0.66 | 0.24 | -0.13 | 0.11 |
| TRIO B10 6/6/4 | add | 1.12 | 3.39 | 2.10 | 1.70 | 2,901,436 | 442,686 | -81,405 | -79,271 | -78,611 | 3.33 | 6.55 | 42.86 | 0.69 | -0.46 | -0.22 | -0.48 |
| TRIO B10 6/6/6 | add | 1.36 | 3.61 | 2.28 | 1.94 | 3,385,769 | 381,617 | -81,142 | -79,224 | -78,519 | 3.84 | 8.87 | 39.88 | 0.67 | -0.41 | -0.20 | -0.43 |
| TRIO B10 8/8/4 | const | 1.06 | 3.43 | 1.76 | 1.59 | 2,712,169 | 436,008 | -80,395 | -79,155 | -78,635 | 3.09 | 6.22 | 43.45 | 0.68 | -0.45 | -0.22 | -0.48 |
| TRIO B10 8/8/8 | const | 1.40 | 3.26 | 2.11 | 1.85 | 3,056,748 | 353,985 | -81,915 | -78,952 | -78,295 | 3.59 | 8.64 | 40.48 | 0.69 | -0.35 | -0.25 | -0.38 |
| TRIO B10 6/6/4 | const | 1.12 | 3.39 | 2.10 | 1.70 | 2,901,436 | 442,686 | -81,405 | -79,271 | -78,611 | 3.33 | 6.55 | 42.86 | 0.69 | -0.46 | -0.22 | -0.48 |
| TRIO B10 6/6/6 | const | 1.40 | 3.26 | 2.11 | 1.85 | 3,056,748 | 353,985 | -81,915 | -78,952 | -78,295 | 3.59 | 8.64 | 40.48 | 0.69 | -0.35 | -0.25 | -0.38 |
| TRIO TOP1 8/8/4 | add | 1.12 | 2.91 | 0.95 | 1.36 | 2,160,364 | 450,444 | -82,359 | -79,707 | -78,668 | 2.59 | 4.80 | 46.43 | 0.78 | -0.36 | -0.21 | -0.41 |
| TRIO TOP1 8/8/8 | add | 1.30 | 2.92 | 1.09 | 1.48 | 2,369,471 | 274,096 | -84,412 | -79,191 | -78,413 | 2.85 | 8.64 | 47.02 | 0.72 | -0.47 | -0.26 | -0.50 |
| TRIO TOP1 6/6/4 | add | 1.42 | 3.23 | 1.55 | 1.73 | 2,377,477 | 351,686 | -79,399 | -78,478 | -78,041 | 3.22 | 6.76 | 41.67 | 0.74 | -0.37 | -0.42 | -0.42 |
| TRIO TOP1 6/6/6 | add | 1.68 | 3.45 | 1.48 | 1.88 | 2,689,687 | 334,756 | -79,768 | -78,690 | -78,120 | 3.63 | 8.03 | 41.07 | 0.73 | -0.34 | -0.38 | -0.39 |
| TRIO TOP1 8/8/4 | const | 1.22 | 3.95 | 1.37 | 1.64 | 2,329,593 | 367,725 | -79,149 | -77,963 | -77,586 | 3.13 | 6.34 | 42.86 | 0.77 | -0.25 | -0.37 | -0.32 |
| TRIO TOP1 8/8/8 | const | 1.76 | 3.26 | 1.59 | 1.96 | 2,527,408 | 310,340 | -78,863 | -77,850 | -77,470 | 3.70 | 8.14 | 39.29 | 0.73 | -0.29 | -0.50 | -0.35 |
| TRIO TOP1 6/6/4 | const | 1.42 | 3.23 | 1.55 | 1.73 | 2,377,477 | 351,686 | -79,399 | -78,478 | -78,041 | 3.22 | 6.76 | 41.67 | 0.74 | -0.37 | -0.42 | -0.42 |
| TRIO TOP1 6/6/6 | const | 1.76 | 3.26 | 1.59 | 1.96 | 2,527,408 | 310,340 | -78,863 | -77,850 | -77,470 | 3.70 | 8.14 | 39.29 | 0.73 | -0.29 | -0.50 | -0.35 |
| TRIO T3 8/8/4 | add | 1.43 | 2.64 | 1.50 | 1.65 | 2,609,945 | 263,991 | -81,659 | -79,346 | -78,451 | 3.25 | 9.89 | 44.05 | 0.83 | -0.34 | -0.14 | -0.39 |
| TRIO T3 8/8/8 | add | 1.10 | 2.31 | 1.08 | 1.29 | 2,087,710 | 277,407 | -84,591 | -80,710 | -79,481 | 2.34 | 7.53 | 46.43 | 0.73 | -0.46 | -0.23 | -0.49 |
| TRIO T3 6/6/4 | add | 1.64 | 3.04 | 1.07 | 1.72 | 2,380,747 | 297,466 | -82,355 | -79,358 | -78,526 | 3.19 | 8.00 | 41.67 | 0.76 | -0.36 | -0.40 | -0.41 |
| TRIO T3 6/6/6 | add | 1.67 | 3.40 | 1.20 | 1.80 | 2,582,363 | 307,733 | -84,736 | -79,721 | -78,658 | 3.40 | 8.39 | 41.07 | 0.74 | -0.34 | -0.37 | -0.39 |
| TRIO T3 8/8/4 | const | 1.28 | 4.12 | 1.86 | 1.84 | 2,640,281 | 369,661 | -80,340 | -78,428 | -77,875 | 3.60 | 7.14 | 42.86 | 0.83 | -0.27 | -0.31 | -0.34 |
| TRIO T3 8/8/8 | const | 1.88 | 2.96 | 1.02 | 1.84 | 2,420,076 | 298,663 | -78,904 | -77,942 | -77,626 | 3.45 | 8.10 | 40.48 | 0.74 | -0.26 | -0.47 | -0.32 |
| TRIO T3 6/6/4 | const | 1.64 | 3.04 | 1.07 | 1.72 | 2,380,747 | 297,466 | -82,355 | -79,358 | -78,526 | 3.19 | 8.00 | 41.67 | 0.76 | -0.36 | -0.40 | -0.41 |
| TRIO T3 6/6/6 | const | 1.88 | 2.96 | 1.02 | 1.84 | 2,420,076 | 298,663 | -78,904 | -77,942 | -77,626 | 3.45 | 8.10 | 40.48 | 0.74 | -0.26 | -0.47 | -0.32 |

Detail by span (clean / H1 / H2), net / Sharpe / maxDD / worst week / CVaR5:

| cell | framing | span | net | sharpe | maxdd | worst_week | cvar5 |
|---|---|---|---|---|---|---|---|
| PAIR 8/8 | - | clean | 1,329,959 | 1.46 | 280,110 | -81,874 | -78,736 |
| PAIR 8/8 | - | H1 | 593,797 | 2.83 | 151,713 | -78,287 | -77,610 |
| PAIR 8/8 | - | H2 | 761,254 | 2.30 | 217,425 | -82,524 | -81,089 |
| TRIO LIVE 8/8/4 | add | clean | 1,624,556 | 1.51 | 349,280 | -84,203 | -80,052 |
| TRIO LIVE 8/8/4 | add | H1 | 1,073,487 | 4.22 | 144,155 | -79,014 | -78,297 |
| TRIO LIVE 8/8/4 | add | H2 | 650,972 | 1.66 | 215,185 | -83,093 | -82,609 |
| TRIO LIVE 8/8/8 | add | clean | 1,497,398 | 1.32 | 449,780 | -82,913 | -80,583 |
| TRIO LIVE 8/8/8 | add | H1 | 642,078 | 2.13 | 233,546 | -79,616 | -79,024 |
| TRIO LIVE 8/8/8 | add | H2 | 567,980 | 1.33 | 355,872 | -85,030 | -82,005 |
| TRIO LIVE 6/6/4 | add | clean | 994,016 | 1.03 | 357,331 | -85,985 | -80,773 |
| TRIO LIVE 6/6/4 | add | H1 | 973,093 | 3.91 | 189,891 | -78,596 | -78,551 |
| TRIO LIVE 6/6/4 | add | H2 | 786,541 | 2.48 | 174,481 | -78,725 | -78,245 |
| TRIO LIVE 6/6/6 | add | clean | 1,526,594 | 1.50 | 326,480 | -83,924 | -79,918 |
| TRIO LIVE 6/6/6 | add | H1 | 1,033,718 | 3.93 | 212,940 | -79,043 | -78,518 |
| TRIO LIVE 6/6/6 | add | H2 | 1,015,610 | 2.68 | 177,508 | -80,492 | -80,217 |
| TRIO LIVE 8/8/4 | const | clean | 1,044,943 | 1.09 | 343,137 | -79,798 | -79,299 |
| TRIO LIVE 8/8/4 | const | H1 | 1,091,016 | 4.60 | 178,216 | -77,740 | -77,448 |
| TRIO LIVE 8/8/4 | const | H2 | 856,674 | 2.71 | 167,509 | -79,778 | -78,765 |
| TRIO LIVE 8/8/8 | const | clean | 1,379,773 | 1.43 | 324,622 | -81,451 | -79,184 |
| TRIO LIVE 8/8/8 | const | H1 | 993,890 | 4.09 | 184,229 | -77,877 | -77,484 |
| TRIO LIVE 8/8/8 | const | H2 | 752,791 | 2.18 | 214,381 | -81,915 | -81,429 |
| TRIO LIVE 6/6/4 | const | clean | 994,016 | 1.03 | 357,331 | -85,985 | -80,773 |
| TRIO LIVE 6/6/4 | const | H1 | 973,093 | 3.91 | 189,891 | -78,596 | -78,551 |
| TRIO LIVE 6/6/4 | const | H2 | 786,541 | 2.48 | 174,481 | -78,725 | -78,245 |
| TRIO LIVE 6/6/6 | const | clean | 1,379,773 | 1.43 | 324,622 | -81,451 | -79,184 |
| TRIO LIVE 6/6/6 | const | H1 | 993,890 | 4.09 | 184,229 | -77,877 | -77,484 |
| TRIO LIVE 6/6/6 | const | H2 | 752,791 | 2.18 | 214,381 | -81,915 | -81,429 |
| TRIO B10 8/8/4 | add | clean | 1,575,910 | 1.46 | 410,573 | -82,830 | -79,576 |
| TRIO B10 8/8/4 | add | H1 | 744,058 | 2.66 | 189,427 | -78,644 | -78,082 |
| TRIO B10 8/8/4 | add | H2 | 1,139,595 | 2.59 | 266,324 | -81,444 | -81,063 |
| TRIO B10 8/8/8 | add | clean | 1,518,615 | 1.31 | 417,098 | -87,182 | -82,125 |
| TRIO B10 8/8/8 | add | H1 | 608,332 | 2.19 | 205,276 | -78,447 | -78,069 |
| TRIO B10 8/8/8 | add | H2 | 403,186 | 0.85 | 321,747 | -86,180 | -82,881 |
| TRIO B10 6/6/4 | add | clean | 1,138,853 | 1.12 | 442,686 | -80,048 | -78,760 |
| TRIO B10 6/6/4 | add | H1 | 881,854 | 3.39 | 166,968 | -79,162 | -78,598 |
| TRIO B10 6/6/4 | add | H2 | 880,729 | 2.10 | 258,336 | -81,405 | -80,733 |
| TRIO B10 6/6/6 | add | clean | 1,405,094 | 1.36 | 381,617 | -80,791 | -79,173 |
| TRIO B10 6/6/6 | add | H1 | 1,045,244 | 3.61 | 170,590 | -78,607 | -78,419 |
| TRIO B10 6/6/6 | add | H2 | 935,430 | 2.28 | 276,901 | -81,142 | -79,469 |
| TRIO B10 8/8/4 | const | clean | 1,080,340 | 1.06 | 436,008 | -80,395 | -79,198 |
| TRIO B10 8/8/4 | const | H1 | 875,113 | 3.43 | 172,068 | -78,813 | -78,469 |
| TRIO B10 8/8/4 | const | H2 | 756,717 | 1.76 | 250,820 | -79,618 | -79,198 |
| TRIO B10 8/8/8 | const | clean | 1,401,344 | 1.40 | 353,985 | -79,622 | -78,357 |
| TRIO B10 8/8/8 | const | H1 | 865,562 | 3.26 | 171,857 | -79,380 | -78,547 |
| TRIO B10 8/8/8 | const | H2 | 789,841 | 2.11 | 226,960 | -81,915 | -80,525 |
| TRIO B10 6/6/4 | const | clean | 1,138,853 | 1.12 | 442,686 | -80,048 | -78,760 |
| TRIO B10 6/6/4 | const | H1 | 881,854 | 3.39 | 166,968 | -79,162 | -78,598 |
| TRIO B10 6/6/4 | const | H2 | 880,729 | 2.10 | 258,336 | -81,405 | -80,733 |
| TRIO B10 6/6/6 | const | clean | 1,401,344 | 1.40 | 353,985 | -79,622 | -78,357 |
| TRIO B10 6/6/6 | const | H1 | 865,562 | 3.26 | 171,857 | -79,380 | -78,547 |
| TRIO B10 6/6/6 | const | H2 | 789,841 | 2.11 | 226,960 | -81,915 | -80,525 |
| TRIO TOP1 8/8/4 | add | clean | 1,054,787 | 1.12 | 450,444 | -82,143 | -78,961 |
| TRIO TOP1 8/8/4 | add | H1 | 734,657 | 2.91 | 161,001 | -80,792 | -78,897 |
| TRIO TOP1 8/8/4 | add | H2 | 370,920 | 0.95 | 267,699 | -82,359 | -81,055 |
| TRIO TOP1 8/8/8 | add | clean | 1,203,613 | 1.30 | 274,096 | -84,412 | -79,502 |
| TRIO TOP1 8/8/8 | add | H1 | 699,416 | 2.92 | 179,625 | -77,497 | -73,495 |
| TRIO TOP1 8/8/8 | add | H2 | 466,442 | 1.09 | 252,564 | -79,448 | -78,864 |
| TRIO TOP1 6/6/4 | add | clean | 1,171,073 | 1.42 | 351,686 | -78,822 | -78,269 |
| TRIO TOP1 6/6/4 | add | H1 | 681,094 | 3.23 | 210,436 | -79,399 | -79,152 |
| TRIO TOP1 6/6/4 | add | H2 | 525,310 | 1.55 | 267,483 | -78,194 | -78,098 |
| TRIO TOP1 6/6/6 | add | clean | 1,429,165 | 1.68 | 334,756 | -79,768 | -78,727 |
| TRIO TOP1 6/6/6 | add | H1 | 723,201 | 3.45 | 224,216 | -79,281 | -78,103 |
| TRIO TOP1 6/6/6 | add | H2 | 537,321 | 1.48 | 283,344 | -78,899 | -78,228 |
| TRIO TOP1 8/8/4 | const | clean | 1,035,168 | 1.22 | 367,725 | -79,149 | -78,194 |
| TRIO TOP1 8/8/4 | const | H1 | 795,363 | 3.95 | 131,148 | -77,575 | -60,355 |
| TRIO TOP1 8/8/4 | const | H2 | 499,061 | 1.37 | 222,616 | -77,533 | -77,467 |
| TRIO TOP1 8/8/8 | const | clean | 1,389,012 | 1.76 | 310,340 | -78,863 | -77,723 |
| TRIO TOP1 8/8/8 | const | H1 | 656,213 | 3.26 | 194,529 | -76,984 | -76,948 |
| TRIO TOP1 8/8/8 | const | H2 | 482,182 | 1.59 | 262,571 | -78,287 | -78,021 |
| TRIO TOP1 6/6/4 | const | clean | 1,171,073 | 1.42 | 351,686 | -78,822 | -78,269 |
| TRIO TOP1 6/6/4 | const | H1 | 681,094 | 3.23 | 210,436 | -79,399 | -79,152 |
| TRIO TOP1 6/6/4 | const | H2 | 525,310 | 1.55 | 267,483 | -78,194 | -78,098 |
| TRIO TOP1 6/6/6 | const | clean | 1,389,012 | 1.76 | 310,340 | -78,863 | -77,723 |
| TRIO TOP1 6/6/6 | const | H1 | 656,213 | 3.26 | 194,529 | -76,984 | -76,948 |
| TRIO TOP1 6/6/6 | const | H2 | 482,182 | 1.59 | 262,571 | -78,287 | -78,021 |
| TRIO T3 8/8/4 | add | clean | 1,344,079 | 1.43 | 263,991 | -80,663 | -79,392 |
| TRIO T3 8/8/4 | add | H1 | 680,345 | 2.64 | 177,803 | -78,242 | -77,692 |
| TRIO T3 8/8/4 | add | H2 | 585,520 | 1.50 | 243,455 | -81,659 | -79,629 |
| TRIO T3 8/8/8 | add | clean | 1,057,127 | 1.10 | 277,407 | -84,591 | -80,753 |
| TRIO T3 8/8/8 | add | H1 | 597,557 | 2.31 | 213,319 | -80,100 | -79,166 |
| TRIO T3 8/8/8 | add | H2 | 433,026 | 1.08 | 243,282 | -83,420 | -80,887 |
| TRIO T3 6/6/4 | add | clean | 1,316,698 | 1.64 | 220,376 | -82,355 | -79,186 |
| TRIO T3 6/6/4 | add | H1 | 679,224 | 3.04 | 195,660 | -79,704 | -78,281 |
| TRIO T3 6/6/4 | add | H2 | 384,826 | 1.07 | 297,466 | -79,149 | -79,024 |
| TRIO T3 6/6/6 | add | clean | 1,401,468 | 1.67 | 307,733 | -84,736 | -79,228 |
| TRIO T3 6/6/6 | add | H1 | 728,994 | 3.40 | 200,211 | -80,207 | -78,656 |
| TRIO T3 6/6/6 | add | H2 | 451,901 | 1.20 | 300,101 | -79,750 | -79,748 |
| TRIO T3 8/8/4 | const | clean | 1,084,988 | 1.28 | 369,661 | -80,340 | -78,242 |
| TRIO T3 8/8/4 | const | H1 | 868,625 | 4.12 | 117,370 | -77,482 | -77,194 |
| TRIO T3 8/8/4 | const | H2 | 686,668 | 1.86 | 245,338 | -79,613 | -79,231 |
| TRIO T3 8/8/8 | const | clean | 1,463,012 | 1.88 | 200,215 | -77,498 | -77,309 |
| TRIO T3 8/8/8 | const | H1 | 625,375 | 2.96 | 175,009 | -78,904 | -78,839 |
| TRIO T3 8/8/8 | const | H2 | 331,689 | 1.02 | 298,663 | -78,010 | -78,002 |
| TRIO T3 6/6/4 | const | clean | 1,316,698 | 1.64 | 220,376 | -82,355 | -79,186 |
| TRIO T3 6/6/4 | const | H1 | 679,224 | 3.04 | 195,660 | -79,704 | -78,281 |
| TRIO T3 6/6/4 | const | H2 | 384,826 | 1.07 | 297,466 | -79,149 | -79,024 |
| TRIO T3 6/6/6 | const | clean | 1,463,012 | 1.88 | 200,215 | -77,498 | -77,309 |
| TRIO T3 6/6/6 | const | H1 | 625,375 | 2.96 | 175,009 | -78,904 | -78,839 |
| TRIO T3 6/6/6 | const | H2 | 331,689 | 1.02 | 298,663 | -78,010 | -78,002 |

**What the trio shows:**
- WT inside the same account is *not* the sleeve result. LIVE 8/8/4: all-in Sharpe 1.94 (pair 1.86) but maxDD $349k vs $280k, CVaR5 slightly worse; LIVE 8/8/8: Sharpe **1.46** (worse than the pair), maxDD $450k; B10 8/8/8 1.33; T3 8/8/4 1.65, 8/8/8 1.29. Only LIVE 6/6/6 (2.15), LIVE constant-risk 8/8/8 (2.01) and TOP1 constant-risk 8/8/8 (1.96) beat the pair's 1.86 by +0.10 or more in all-in Sharpe; no row moves the worst week (-$79k to -$87k vs -$82.5k: the combined week floor sets it), and the max drawdown is below the pair's $280k only for T3 8/8/4 ($264k) and TOP1 8/8/8 ($274k).
- The reason is netting. WT trades 7-8 times a day (1-min) or 2.5 times a day (10-min) and every WT entry opposite to an open ST/HM lot closes that lot at market and is absorbed (the NT8 defect modelled in ENGINE RECON (e)), while its protective orders stay working and open unintended orphan positions. Same sleeves in *their own account* (pair + k x WT stand-alone, WT with its own rules, no netting):

| wt | size | cell | net | sharpe | maxdd | worst_week | cvar5 |
|---|---|---|---|---|---|---|---|
| LIVE | 8/8/4 | NETTED trio (one account) | 3,349,014 | 1.94 | 349,280 | -84,203 | -80,584 |
| LIVE | 8/8/4 | SEPARATE (pair + WT own account, no netting) | 3,692,704 | 2.15 | 290,920 | -116,268 | -103,244 |
| LIVE | 8/8/8 | NETTED trio (one account) | 2,707,456 | 1.46 | 449,780 | -85,030 | -80,828 |
| LIVE | 8/8/8 | SEPARATE (pair + WT own account, no netting) | 4,700,398 | 2.26 | 322,609 | -154,818 | -130,050 |
| LIVE | 6/6/4 | NETTED trio (one account) | 2,753,649 | 1.80 | 357,331 | -85,985 | -80,052 |
| LIVE | 6/6/4 | SEPARATE (pair + WT own account, no netting) | 3,132,479 | 1.99 | 330,579 | -115,424 | -102,034 |
| LIVE | 6/6/6 | NETTED trio (one account) | 3,575,922 | 2.15 | 326,480 | -83,924 | -79,944 |
| LIVE | 6/6/6 | SEPARATE (pair + WT own account, no netting) | 3,636,326 | 2.07 | 345,917 | -134,674 | -115,688 |
| B10 | 8/8/4 | NETTED trio (one account) | 3,459,563 | 1.93 | 410,573 | -82,830 | -79,803 |
| B10 | 8/8/4 | SEPARATE (pair + WT own account, no netting) | 3,697,839 | 2.22 | 316,468 | -118,193 | -99,441 |
| B10 | 8/8/8 | NETTED trio (one account) | 2,530,134 | 1.33 | 417,098 | -87,182 | -81,999 |
| B10 | 8/8/8 | SEPARATE (pair + WT own account, no netting) | 4,710,667 | 2.35 | 372,625 | -154,582 | -122,228 |
| B10 | 6/6/4 | NETTED trio (one account) | 2,901,436 | 1.70 | 442,686 | -81,405 | -79,271 |
| B10 | 6/6/4 | SEPARATE (pair + WT own account, no netting) | 3,137,614 | 2.06 | 395,337 | -116,334 | -100,482 |
| B10 | 6/6/6 | NETTED trio (one account) | 3,385,769 | 1.94 | 381,617 | -81,142 | -79,224 |
| B10 | 6/6/6 | SEPARATE (pair + WT own account, no netting) | 3,644,028 | 2.15 | 441,407 | -135,691 | -113,169 |
| TOP1 | 8/8/4 | NETTED trio (one account) | 2,160,364 | 1.36 | 450,444 | -82,359 | -79,707 |
| TOP1 | 8/8/4 | SEPARATE (pair + WT own account, no netting) | 3,250,273 | 2.21 | 246,483 | -107,020 | -87,177 |
| TOP1 | 8/8/8 | NETTED trio (one account) | 2,369,471 | 1.48 | 274,096 | -84,412 | -79,191 |
| TOP1 | 8/8/8 | SEPARATE (pair + WT own account, no netting) | 3,815,535 | 2.44 | 245,072 | -136,624 | -96,007 |
| TOP1 | 6/6/4 | NETTED trio (one account) | 2,377,477 | 1.73 | 351,686 | -79,399 | -78,478 |
| TOP1 | 6/6/4 | SEPARATE (pair + WT own account, no netting) | 2,690,048 | 2.03 | 302,272 | -106,703 | -84,672 |
| TOP1 | 6/6/6 | NETTED trio (one account) | 2,689,687 | 1.88 | 334,756 | -79,768 | -78,690 |
| TOP1 | 6/6/6 | SEPARATE (pair + WT own account, no netting) | 2,972,679 | 2.16 | 320,422 | -121,505 | -88,222 |
| T3 | 8/8/4 | NETTED trio (one account) | 2,609,945 | 1.65 | 263,991 | -81,659 | -79,346 |
| T3 | 8/8/4 | SEPARATE (pair + WT own account, no netting) | 3,389,294 | 2.28 | 220,418 | -93,325 | -85,712 |
| T3 | 8/8/8 | NETTED trio (one account) | 2,087,710 | 1.29 | 277,407 | -84,591 | -80,710 |
| T3 | 8/8/8 | SEPARATE (pair + WT own account, no netting) | 4,093,577 | 2.56 | 224,489 | -109,234 | -96,676 |
| T3 | 6/6/4 | NETTED trio (one account) | 2,380,747 | 1.72 | 297,466 | -82,355 | -79,358 |
| T3 | 6/6/4 | SEPARATE (pair + WT own account, no netting) | 2,829,069 | 2.11 | 293,320 | -93,008 | -81,351 |
| T3 | 6/6/6 | NETTED trio (one account) | 2,582,363 | 1.80 | 307,733 | -84,736 | -79,721 |
| T3 | 6/6/6 | SEPARATE (pair + WT own account, no netting) | 3,181,210 | 2.28 | 306,994 | -100,963 | -84,873 |

  Separate accounts give all-in Sharpe 2.0-2.6 for every WT variant and size (T3 8/8/8: 2.56 vs the netted 1.29), at the price of a worse worst week (-$93k to -$155k) because the pair's week floor does not cover the WT account. So the WT benefit is available only if WT runs as its own strategy instance on its own account (or with its own account-level loss limit), not as a DualStrat third book in the same netted position.
- Correlation with the pair (weekly P&L, all weeks / worst-decile weeks = worst 17 of 168 weeks of the pair): trio LIVE 8/8/4 0.67 / -0.25; trio T3 0.83 / -0.34; the *increment* (trio minus pair) correlates -0.22 / -0.27 (LIVE 8/8/4) with the pair, i.e. WT's contribution is mildly counter-cyclical in the pair's bad weeks. WT stand-alone vs pair: LIVE 0.41 / -0.29; B10 0.26 / +0.20; T3 0.00 / -0.20; TOP1 -0.05 / -0.17.

## (c) Parameter plateau grid (pre-registered; 432 cells)
Grid: ATR {10,14,20,30} x mult {2,3,4} x EMA {off,100,200} x timeframe {1,3,5,10} min x exit {X1 60/60 bracket on the 1-second path, X2 trail-only (exit at the open after the opposite raw flip), X3 X2 + 120-minute time stop}. 8 NQ, live account rules, 1 tick/side + $34.88. Selection on the clean span only (eligible: >= 300 clean trades and clean Sharpe > 0 -> 210 of 432; rank by clean additive uplift at 20% share; top 10 advance; H1/H2 read once for those 10 plus the two fixed specs).

Clean uplift (pair + 20% x WT scaled to the pair's clean weekly vol) by exit: X1 mean -0.033, X2 -0.081, X3 -0.153; 142 of 432 cells have a positive clean uplift. By timeframe (mean): see table. The time stop (X3) does not help trend exits; longer bars (10 min) are best.

| tf | X1 | X2 | X3 |
|---|---|---|---|
| 1.00 | -0.08 | -0.33 | -0.32 |
| 3.00 | -0.08 | -0.08 | -0.20 |
| 5.00 | -0.04 | 0.04 | -0.08 |
| 10.00 | 0.07 | 0.04 | -0.01 |

Top 10 by clean uplift (the advanced set):

| an | m | ema | tf | exit | n_clean | sh | up | scale |
|---|---|---|---|---|---|---|---|---|
| 10 | 3.00 | 0 | 10 | X1 | 1150 | 2.17 | 0.42 | 2.19 |
| 10 | 3.00 | 100 | 10 | X1 | 794 | 1.91 | 0.38 | 2.65 |
| 14 | 3.00 | 0 | 10 | X1 | 1191 | 1.99 | 0.37 | 2.15 |
| 10 | 4.00 | 0 | 5 | X2 | 1176 | 1.68 | 0.28 | 1.54 |
| 14 | 4.00 | 0 | 5 | X2 | 1174 | 1.84 | 0.27 | 1.42 |
| 14 | 3.00 | 100 | 10 | X1 | 813 | 1.46 | 0.27 | 2.58 |
| 20 | 4.00 | 0 | 5 | X2 | 1178 | 1.79 | 0.26 | 1.43 |
| 10 | 3.00 | 200 | 10 | X1 | 735 | 1.34 | 0.25 | 2.59 |
| 14 | 4.00 | 100 | 5 | X2 | 989 | 1.72 | 0.24 | 1.49 |
| 14 | 3.00 | 0 | 10 | X2 | 979 | 1.77 | 0.23 | 1.36 |

### Selection-corrected null (reported; family level)
60 timing-destroyed replicates of the *whole* 432-cell selection (every cell's clean trades replaced by random-entry trades with the same count, hold distribution and bracket; same eligibility and ranking):

| statistic | real | null_mean | null_p95 | null_max | p_null_ge_real |
|---|---|---|---|---|---|
| n_el | 210.00 | 105.97 | 121.05 | 129.00 | 0.00 |
| top1 | 0.42 | 0.32 | 0.42 | 0.47 | 0.03 |
| top10 | 0.30 | 0.22 | 0.25 | 0.27 | 0.00 |
| n_ge_030 | 3.00 | 0.73 | 2.00 | 3.00 | 0.02 |

Reading: under the null the best eligible cell reaches a clean uplift of 0.32 on average (p95 0.42, max 0.47), real 0.425 (p = 0.03); the mean of the top 10 is 0.296 against a null maximum of 0.269 (0 of 60 replicates); the count of eligible cells is 210 against 106 +- 10 (never reached). So the clean-span structure in this family is **more than selection from noise**, as in the C7 ZB/6J finding; it is a statement about 2023-2025, not about WT as a durable edge (history below).

### The 12 scored cells (pair window 2023-08..2026-10; all numbers net)
| cell | trades_pw | trades_day | pts_per_trade | pts_bracket_units | stand_clean | stand_H1 | stand_H2 | stand_all | scale_to_pair | corr_all | wd_corr |
|---|---|---|---|---|---|---|---|---|---|---|---|
| ATR20_m2_ema100_tf1_X1 | 6322 | 7.64 | 2.30 | 0.04 | 1.40 | 3.20 | 2.92 | 1.98 | 1.38 | 0.41 | -0.29 |
| ATR20_m1.75_ema50_tf1_X1 | 6876 | 8.30 | 2.24 | 0.04 | 1.53 | 2.10 | 2.92 | 1.93 | 1.36 | 0.26 | 0.20 |
| ATR10_m3_ema0_tf10_X1 | 1989 | 2.40 | 4.01 | 0.07 | 2.17 | 1.83 | 0.34 | 1.68 | 2.19 | -0.05 | -0.17 |
| ATR10_m3_ema100_tf10_X1 | 1324 | 1.60 | 3.77 | 0.06 | 1.91 | 0.98 | 0.62 | 1.48 | 2.65 | -0.05 | -0.06 |
| ATR14_m3_ema0_tf10_X1 | 2035 | 2.46 | 4.54 | 0.08 | 1.99 | 3.15 | 1.42 | 2.05 | 2.15 | -0.00 | -0.20 |
| ATR10_m4_ema0_tf5_X2 | 1901 | 2.30 | 7.19 | 0.12 | 1.68 | 3.93 | -0.69 | 1.50 | 1.54 | 0.10 | -0.25 |
| ATR14_m4_ema0_tf5_X2 | 1895 | 2.29 | 7.66 | 0.13 | 1.84 | 4.03 | -0.04 | 1.76 | 1.42 | 0.14 | -0.52 |
| ATR14_m3_ema100_tf10_X1 | 1343 | 1.62 | 3.99 | 0.07 | 1.46 | 0.92 | 1.49 | 1.39 | 2.58 | 0.01 | -0.12 |
| ATR20_m4_ema0_tf5_X2 | 1896 | 2.29 | 6.76 | 0.11 | 1.79 | 3.89 | 0.29 | 1.82 | 1.43 | 0.15 | -0.55 |
| ATR10_m3_ema200_tf10_X1 | 1212 | 1.46 | 3.45 | 0.06 | 1.34 | 1.89 | 0.67 | 1.22 | 2.59 | -0.05 | -0.23 |
| ATR14_m4_ema100_tf5_X2 | 1601 | 1.93 | 7.68 | 0.13 | 1.72 | 1.77 | 1.65 | 1.71 | 1.49 | 0.26 | -0.01 |
| ATR14_m3_ema0_tf10_X2 | 1567 | 1.89 | 8.42 | 0.14 | 1.77 | 3.57 | -0.40 | 1.62 | 1.36 | 0.24 | -0.31 |

Additive and robustness numbers at the 20% share (up = weekly Sharpe uplift of pair + 20% x WT; boot = 5th/95th percentile of the all-in uplift, 3000 weekly resamples; own-null = standalone all-in Sharpe p95 of 200 random-entry replicates with the same count and hold, rank of the real cell; shift = circular-shift null rank (reported only); plateau = share of +-25% neighbours keeping 75% of the all-in uplift; slip2 = uplift at 2 ticks/side vs the 2-tick pair):

| cell | up20_clean | up20_H1 | up20_H2 | up20_all | boot_lo | boot_hi | ww_chg | own_null_p95 | own_null_rank | shift_rank | plateau | slip2_clean | slip2_H1 | slip2_H2 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ATR20_m2_ema100_tf1_X1 | 0.12 | 0.28 | 0.31 | 0.19 | 0.04 | 0.36 | 19.93 | 0.36 | 1.00 | 0.00 | 0.25 | 0.11 | 0.28 | 0.24 |
| ATR20_m1.75_ema50_tf1_X1 | 0.17 | 0.28 | 0.40 | 0.24 | 0.08 | 0.41 | 23.10 | 0.46 | 1.00 | 0.00 | 0.25 | 0.17 | 0.24 | 0.30 |
| ATR10_m3_ema0_tf10_X1 | 0.43 | 0.24 | 0.05 | 0.32 | 0.14 | 0.51 | 25.22 | 0.59 | 1.00 | 0.76 | 0.50 | 0.39 | 0.21 | -0.01 |
| ATR10_m3_ema100_tf10_X1 | 0.38 | 0.21 | 0.02 | 0.27 | 0.09 | 0.47 | 13.00 | 0.54 | 1.00 | 0.72 | 0.40 | 0.34 | 0.18 | -0.01 |
| ATR14_m3_ema0_tf10_X1 | 0.37 | 0.42 | 0.31 | 0.37 | 0.19 | 0.58 | 10.42 | 0.56 | 1.00 | 0.53 | 0.50 | 0.34 | 0.41 | 0.25 |
| ATR10_m4_ema0_tf5_X2 | 0.28 | 0.65 | -0.23 | 0.23 | 0.05 | 0.43 | 16.69 | 0.67 | 1.00 | 0.09 | 0.50 | 0.27 | 0.65 | -0.24 |
| ATR14_m4_ema0_tf5_X2 | 0.27 | 0.67 | -0.05 | 0.26 | 0.09 | 0.46 | 15.82 | 0.73 | 1.00 | 0.03 | 0.33 | 0.27 | 0.67 | -0.05 |
| ATR14_m3_ema100_tf10_X1 | 0.27 | 0.07 | 0.23 | 0.24 | 0.05 | 0.44 | 12.36 | 0.51 | 1.00 | 0.44 | 0.50 | 0.24 | 0.04 | 0.18 |
| ATR20_m4_ema0_tf5_X2 | 0.26 | 0.66 | -0.01 | 0.27 | 0.09 | 0.47 | 16.19 | 0.54 | 1.00 | 0.01 | 0.50 | 0.24 | 0.66 | -0.05 |
| ATR10_m3_ema200_tf10_X1 | 0.25 | 0.42 | 0.08 | 0.23 | 0.03 | 0.43 | 24.18 | 0.76 | 1.00 | 0.77 | 0.70 | 0.23 | 0.37 | 0.04 |
| ATR14_m4_ema100_tf5_X2 | 0.24 | 0.23 | 0.12 | 0.22 | 0.04 | 0.40 | 10.50 | 0.56 | 1.00 | 0.00 | 0.38 | 0.25 | 0.24 | 0.17 |
| ATR14_m3_ema0_tf10_X2 | 0.22 | 0.56 | -0.16 | 0.19 | 0.02 | 0.36 | 9.11 | 0.60 | 1.00 | 0.00 | 0.67 | 0.23 | 0.56 | -0.17 |

Gate checklist at 20% share (Y = pass):

| cell | G3 uplift>=0.10 c/H1/H2 | G3 worst week | G4 own null p95 | G4 bootstrap | G5 plateau | G5 2x slip | G6 wd corr |
|---|---|---|---|---|---|---|---|
| ATR20_m2_ema100_tf1_X1 | Y | Y | Y | Y | n | Y | Y |
| ATR20_m1.75_ema50_tf1_X1 | Y | n | Y | Y | n | Y | Y |
| ATR10_m3_ema0_tf10_X1 | n | n | Y | Y | n | n | Y |
| ATR10_m3_ema100_tf10_X1 | n | Y | Y | Y | n | n | Y |
| ATR14_m3_ema0_tf10_X1 | Y | Y | Y | Y | n | Y | Y |
| ATR10_m4_ema0_tf5_X2 | n | Y | Y | Y | n | n | Y |
| ATR14_m4_ema0_tf5_X2 | n | Y | Y | Y | n | n | Y |
| ATR14_m3_ema100_tf10_X1 | n | Y | Y | Y | n | n | Y |
| ATR20_m4_ema0_tf5_X2 | n | Y | Y | Y | n | n | Y |
| ATR10_m3_ema200_tf10_X1 | n | n | Y | Y | n | n | Y |
| ATR14_m4_ema100_tf5_X2 | Y | Y | Y | Y | n | Y | Y |
| ATR14_m3_ema0_tf10_X2 | n | Y | Y | Y | n | n | Y |

Gates 3 (uplift >= +0.10 on clean, H1 and H2 separately **and** worst week not worse than the share) at other shares (cells that pass the uplift part): LIVE at 20/30/50% (worst-week passes only at 20%, 19.9% vs 20%), B10 at 20/30/50% (fails worst week at every share), **T3 at 10/20/30/50% (worst week passes at every share)**, ATR14/m4/EMA100/5-min/X2 at 20/30/50% (H2 uplift only +0.12..+0.14). All other advanced cells fail the uplift gate on at least one span (the 5-min X2 trail-only cells and TOP1 have H1 +0.24..+0.67 but H2 -0.24..+0.05).

**Plateau detail** for the two main cells (neighbours are ATR / mult / EMA / timeframe / bracket at x0.75 and x1.25, rounded):

`ATR14_m3_ema0_tf10_X1` (base all-in uplift at 20% = 0.373):

| neighbour | spec | up_all20 | clean | H1 | H2 | keeps75 |
|---|---|---|---|---|---|---|
| ATR10_m3_ema0_tf10_X1 | {"an": 10, "m": 3.0, "ema": 0, "tf": 10, "exit": "X1"} | 0.32 | 0.42 | 0.23 | 0.05 | True |
| ATR14_m2.25_ema0_tf10_X1 | {"an": 14, "m": 2.25, "ema": 0, "tf": 10, "exit": "X1"} | 0.19 | 0.18 | 0.54 | -0.04 | False |
| ATR14_m3_ema0_tf8_X1 | {"an": 14, "m": 3.0, "ema": 0, "tf": 8, "exit": "X1"} | 0.28 | 0.28 | 0.36 | 0.17 | True |
| ATR14_m3_ema0_tf10_X1 | {"an": 14, "m": 3.0, "ema": 0, "tf": 10, "exit": "X1", "br": 45.0} | 0.36 | 0.29 | 0.28 | 0.58 | True |
| ATR18_m3_ema0_tf10_X1 | {"an": 18, "m": 3.0, "ema": 0, "tf": 10, "exit": "X1"} | 0.28 | 0.23 | 0.27 | 0.44 | True |
| ATR14_m3.75_ema0_tf10_X1 | {"an": 14, "m": 3.75, "ema": 0, "tf": 10, "exit": "X1"} | 0.05 | 0.16 | -0.45 | 0.03 | False |
| ATR14_m3_ema0_tf12_X1 | {"an": 14, "m": 3.0, "ema": 0, "tf": 12, "exit": "X1"} | 0.14 | 0.23 | -0.03 | -0.07 | False |
| ATR14_m3_ema0_tf10_X1 | {"an": 14, "m": 3.0, "ema": 0, "tf": 10, "exit": "X1", "br": 75.0} | 0.21 | 0.24 | 0.32 | 0.05 | False |

`ATR20_m2_ema100_tf1_X1` (WT-LIVE, base 0.191):

| neighbour | spec | up_all20 | clean | H1 | H2 | keeps75 |
|---|---|---|---|---|---|---|
| ATR15_m2_ema100_tf1_X1 | {"an": 15, "m": 2.0, "ema": 100, "tf": 1, "exit": "X1"} | 0.15 | 0.11 | 0.22 | 0.21 | True |
| ATR20_m1.5_ema100_tf1_X1 | {"an": 20, "m": 1.5, "ema": 100, "tf": 1, "exit": "X1"} | -0.01 | -0.00 | 0.03 | -0.04 | False |
| ATR20_m2_ema75_tf1_X1 | {"an": 20, "m": 2.0, "ema": 75, "tf": 1, "exit": "X1"} | 0.21 | 0.13 | 0.35 | 0.32 | True |
| ATR20_m2_ema100_tf1_X1 | {"an": 20, "m": 2.0, "ema": 100, "tf": 1, "exit": "X1", "br": 45.0} | 0.14 | 0.11 | 0.39 | 0.09 | False |
| ATR25_m2_ema100_tf1_X1 | {"an": 25, "m": 2.0, "ema": 100, "tf": 1, "exit": "X1"} | 0.14 | 0.07 | 0.15 | 0.29 | False |
| ATR20_m2.5_ema100_tf1_X1 | {"an": 20, "m": 2.5, "ema": 100, "tf": 1, "exit": "X1"} | 0.04 | -0.03 | 0.15 | 0.18 | False |
| ATR20_m2_ema125_tf1_X1 | {"an": 20, "m": 2.0, "ema": 125, "tf": 1, "exit": "X1"} | 0.09 | 0.04 | 0.25 | 0.08 | False |
| ATR20_m2_ema100_tf1_X1 | {"an": 20, "m": 2.0, "ema": 100, "tf": 1, "exit": "X1", "br": 75.0} | 0.04 | 0.02 | 0.31 | -0.07 | False |

The multiplier is the sensitive parameter: x0.75 of the multiplier turns the edge near zero or negative on several cells, and the bracket (45 / 75 pt) moves the uplift by a third in either direction. A real plateau would keep the neighbours; this does not.

### Constant-risk framing (16 contract-equivalents: pair x (1-s) + WT x s), INSURANCE verdict via t3_score
At 20% share every advanced cell has net cost between -6.4% and +2.6% (limit -5%), worst-week improvement -6.5% to +9.6% and CVaR5 improvement +2.5% to +16.8%, max-drawdown improvement +13% to +38%; the verdict thresholds (worst week or CVaR5 >= +20%) are not reached, so **INSURANCE verdict = NO for all 12 cells at all four shares** (table `CELLS_constrisk.csv`). T3 at 20%: Sharpe uplift +0.45 / +0.50 / +0.36, net +2.6%, worst week +8.3%, CVaR5 +12.8%, maxDD +37.7%: a Sharpe and drawdown improvement, not tail insurance.

### 2013-2026 reading of the scored cells (1-minute engine; fixed 60-pt bracket and, for X1, faithful scaling a), real costs, weekly Sharpe
| run | 2013-22 | 2023-26 | clean | H1 | H2 |
|---|---|---|---|---|---|
| ATR10_m3_ema0_tf10_X1_a_real | -0.76 | 1.29 | 2.45 | 1.15 | 0.26 |
| ATR10_m3_ema0_tf10_X1_fixed_real | 0.19 | 1.40 | 2.23 | 1.76 | 0.45 |
| ATR10_m3_ema100_tf10_X1_a_real | -0.80 | 0.73 | 1.79 | -0.88 | -0.66 |
| ATR10_m3_ema100_tf10_X1_fixed_real | -0.12 | 1.28 | 1.77 | 1.02 | 0.50 |
| ATR10_m3_ema200_tf10_X1_a_real | -0.70 | 1.06 | 1.61 | 0.55 | 0.13 |
| ATR10_m3_ema200_tf10_X1_fixed_real | 0.06 | 1.17 | 1.26 | 1.97 | 0.54 |
| ATR10_m4_ema0_tf5_X2_fixed_real | 0.22 | 1.16 | 1.69 | 3.80 | -0.49 |
| ATR14_m3_ema0_tf10_X1_a_real | -1.38 | 1.60 | 2.00 | 2.24 | 1.02 |
| ATR14_m3_ema0_tf10_X1_fixed_real | 0.06 | 1.82 | 2.15 | 3.19 | 1.56 |
| ATR14_m3_ema0_tf10_X2_fixed_real | 0.27 | 1.24 | 1.61 | 3.48 | -0.39 |
| ATR14_m3_ema100_tf10_X1_a_real | -1.26 | 0.86 | 1.59 | -1.28 | -0.44 |
| ATR14_m3_ema100_tf10_X1_fixed_real | -0.20 | 1.18 | 1.32 | 1.09 | 1.43 |
| ATR14_m4_ema0_tf5_X2_fixed_real | 0.32 | 1.26 | 1.88 | 3.70 | -0.22 |
| ATR14_m4_ema100_tf5_X2_fixed_real | -0.22 | 1.32 | 1.62 | 1.26 | 1.64 |
| ATR20_m1.75_ema50_tf1_X1_a_real | -2.22 | 0.88 | 1.38 | 1.75 | 0.31 |
| ATR20_m1.75_ema50_tf1_X1_fixed_real | -0.17 | 1.58 | 1.43 | 2.08 | 2.76 |
| ATR20_m2_ema100_tf1_X1_a_real | -1.57 | 0.95 | 1.73 | 1.58 | -0.21 |
| ATR20_m2_ema100_tf1_X1_fixed_real | 0.24 | 1.41 | 1.49 | 2.34 | 2.18 |
| ATR20_m4_ema0_tf5_X2_fixed_real | 0.35 | 1.42 | 1.80 | 3.98 | 0.17 |

Every cell is positive in 2023-2026 and close to zero or negative in 2013-2022 (fixed bracket: -0.22 to +0.35; scaled bracket: -0.70 to -2.22). Small-sample flag: not triggered (all >= 1,212 trades in the pair window).

### Insurance metric set per cell (standalone, live rules; clean / H1 / H2 / all-in)
Full table (net, Sharpe, Sortino, MAR, maxDD, worst week, CVaR5/10, %neg weeks for all 12 cells x 4 spans): `outputs/autopilot/wt/CELLS_ins.csv`. Key rows:

| cell | span | net | sharpe | sortino | mar | maxdd | worst_week | cvar5 | cvar10 | neg_wk |
|---|---|---|---|---|---|---|---|---|---|---|
| ATR20_m2_ema100_tf1_X1 | clean | 926,142 | 1.40 | 2.49 | 3.33 | 277,829 | -77,099 | -72,602 | -63,391 | 41.90 |
| ATR20_m2_ema100_tf1_X1 | H1 | 573,509 | 3.20 | 6.74 | 2.97 | 192,798 | -65,727 | -56,132 | -52,718 | 32.14 |
| ATR20_m2_ema100_tf1_X1 | H2 | 515,736 | 2.92 | 5.48 | 3.09 | 166,650 | -70,878 | -57,100 | -46,854 | 30.56 |
| ATR20_m2_ema100_tf1_X1 | all | 2,015,388 | 1.98 | 3.64 | 7.25 | 277,829 | -77,099 | -70,082 | -59,698 | 38.10 |
| ATR14_m3_ema0_tf10_X1 | clean | 840,691 | 1.99 | 3.58 | 3.95 | 212,885 | -58,749 | -51,787 | -42,782 | 43.81 |
| ATR14_m3_ema0_tf10_X1 | H1 | 336,963 | 3.15 | 6.73 | 4.82 | 69,903 | -39,244 | -34,654 | -32,971 | 39.29 |
| ATR14_m3_ema0_tf10_X1 | H2 | 230,913 | 1.42 | 2.35 | 1.20 | 192,246 | -58,749 | -54,006 | -47,007 | 38.89 |
| ATR14_m3_ema0_tf10_X1 | all | 1,408,566 | 2.05 | 3.66 | 6.62 | 212,885 | -58,749 | -51,064 | -43,022 | 41.67 |
| ATR14_m4_ema100_tf5_X2 | clean | 1,052,878 | 1.72 | 3.26 | 3.56 | 295,726 | -80,149 | -67,016 | -55,806 | 41.90 |
| ATR14_m4_ema100_tf5_X2 | H1 | 306,384 | 1.77 | 3.65 | 2.31 | 132,877 | -77,934 | -62,147 | -55,029 | 39.29 |
| ATR14_m4_ema100_tf5_X2 | H2 | 468,745 | 1.65 | 3.40 | 1.62 | 288,501 | -77,334 | -77,124 | -68,809 | 47.22 |
| ATR14_m4_ema100_tf5_X2 | all | 1,828,007 | 1.71 | 3.35 | 6.18 | 295,726 | -80,149 | -72,641 | -60,326 | 42.86 |

## (d) Loss-side Trade Health on WT (harness engine st_run9, tick resolution)
TH is **inert under the 1-second exit path** (B4b finding: `ST_EXIT=sec` ignores loss_th); the first attempt with `sec` gave identical results with and without TH and was discarded. The runs below use `ST_EXIT=tick` (100 ms prints), `ST_FILL=print`, NT8 windows (18:00-15:00 except 09:00-09:58, flat 16:55), 8 NQ, 1 tick/side + $34.88, live account rules applied to the trade rows afterwards. Fill model note: the tick path fills stops at the first print through the level (worse than the 1-s model's level-plus-gap rule), so TH-off here is a lower Sharpe (1.54 vs 1.98) than in (a); the TH on/off comparison is within the same engine. TH settings found in the repo: WT 'live' = ml 10 / req 2 / 30 s windows, mask (momentum, stall, efficiency, volatility-collapse) = `b3_common.W30` + `CELLA` shape (B10 `B_WT` fixed: `ml=10, req=2, win=30`); ST Cell A = ml 15 / req 3 / 30 s; B3-TH walk-forward modal for WT = ml 30 / req 3 / 15 s. The b11 Cfg has no TH field (TH off in all b11 work).

| spec | th | Sh clean | Sh H1 | Sh H2 | Sh all | net $ clean | net $ H1 | net $ H2 | net $ all | maxdd | worst_week | cvar5 | mar | th_cut_share_clean | th_exit_mean_pts | trades_clean |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| B10 | cellA_ml15_req3_w30 | 0.82 | 1.11 | 1.63 | 1.04 | 600,213 | 155,566 | 397,156 | 1,152,936 | 340,508 | -83,964 | -75,703 | 3.39 | 0.63 | -22.74 | 5802 |
| B10 | live_ml10_req2_w30 | -0.62 | 0.14 | -2.25 | -0.88 | -329,219 | 16,694 | -422,571 | -735,096 | 929,124 | -78,927 | -70,995 | -0.79 | 0.83 | -10.34 | 9646 |
| B10 | modal_ml30_req3_w15 | 1.07 | 1.13 | 2.93 | 1.43 | 721,189 | 205,697 | 550,290 | 1,477,176 | 194,588 | -79,961 | -73,071 | 7.59 | 0.43 | -36.89 | 4268 |
| B10 | off | 1.18 | 1.24 | 2.57 | 1.49 | 799,344 | 223,202 | 562,943 | 1,585,488 | 287,235 | -77,269 | -73,953 | 5.52 | 0.00 | nan | 3466 |
| LIVE | cellA_ml15_req3_w30 | 1.96 | 2.33 | -0.33 | 1.47 | 1,191,420 | 323,297 | -76,496 | 1,438,220 | 285,557 | -77,601 | -67,630 | 5.04 | 0.63 | -22.80 | 5149 |
| LIVE | live_ml10_req2_w30 | -0.74 | -0.94 | -1.20 | -0.90 | -341,725 | -109,995 | -273,484 | -725,204 | 1,026,482 | -78,295 | -71,920 | -0.71 | 0.83 | -10.32 | 8330 |
| LIVE | modal_ml30_req3_w15 | 1.67 | 1.90 | 1.25 | 1.62 | 1,161,890 | 314,996 | 250,076 | 1,726,962 | 273,429 | -79,068 | -78,022 | 6.32 | 0.42 | -36.91 | 3840 |
| LIVE | off | 1.25 | 2.36 | 1.72 | 1.54 | 839,702 | 437,852 | 344,002 | 1,621,557 | 307,829 | -77,189 | -71,451 | 5.27 | 0.00 | nan | 3218 |

**Verdict: 'TH collapses WT' is CONFIRMED for WT's own TH setting (ml 10 / req 2 / 30 s).** It cuts 83% of all trades (the mean TH exit is -10.3 pt) and turns WT-LIVE from +$1.62M (Sharpe 1.54, all-in) to **-$0.73M (Sharpe -0.90)**; WT-B10 from 1.49 to -0.88; WT-LIVE is negative on every span (clean -0.74, H1 -0.94, H2 -1.20), WT-B10 on clean and H2 (H1 +0.14). This reproduces the B3-era finding (MAR 8.21 -> 0.27, cut rate 75%) on the corrected-window, tick-level engine. A harsher-trigger setting is less destructive but still not helpful: ST Cell A (ml 15 / req 3) 1.47 vs 1.54 (H2 -0.33 vs 1.72); the B3 modal WT setting (ml 30 / req 3 / 15 s) 1.62 vs 1.54 all-in with clean 1.67 vs 1.25 but H2 1.25 vs 1.72 and cut share 42% -- neutral within noise, not an improvement that survives H2. Net: keep TH off for WT.

## Gates (FOUND needs all 7) - best cell `ATR14_m3_ema0_tf10_X1` and the fixed WT-LIVE
| gate | T3 `ATR14_m3_ema0_tf10_X1` | WT-LIVE `ATR20_m2_ema100_tf1_X1` |
|---|---|---|
| 1 pre-registered before the first run | PASS | PASS |
| 2 selection on clean only; H1/H2 read once | PASS (rank 3 by clean uplift 0.37; top-10 list written before H1/H2 were read) | n/a fixed a priori |
| 3 uplift >= +0.10 on clean, H1, H2 (20%) | PASS +0.37 / +0.42 / +0.31 (also 10/30/50%) | PASS +0.12 / +0.28 / +0.31 (20/30/50%) |
| 3b worst week not worse by more than the share | PASS (+10.4% at 20%, all shares) | PASS at 20% only (19.9% vs 20%), FAIL at 30/50% |
| 4 own timing-destroyed null p95 (standalone) | PASS 2.05 vs 0.56 | PASS 1.98 vs 0.36 |
| 4 bootstrap 90% CI of all-in uplift > 0 | PASS lo +0.19 | PASS lo +0.04 |
| 4 circular-shift null | reported: rank 0.53 (not a gate, no hedge claim) | reported: rank 0.00 |
| 5 plateau >= 75% of neighbours keep 75% of uplift | **FAIL 4/8 = 0.50** | **FAIL 2/8 = 0.25** |
| 5 survives 2x slippage (>= +0.10 each span) | PASS +0.34 / +0.41 / +0.25 | PASS +0.11 / +0.28 / +0.24 |
| 6 worst-decile-week correlation <= +0.30 | PASS -0.20 | PASS -0.29 |
| 7 NT8-codable spec + margin | spec yes (below); margin unverified; **not deliverable as a netted third DualStrat book (trio 1.65 < pair 1.86)** | spec yes; netted trio 8/8/4 1.94 vs 1.86 |
| small-sample flag (<100 trades in pair window) | no (2,035 trades; 2013-26 fixed-bracket Sharpe +0.06 in 2013-22, 1.82 in 2023-26) | no (6,322) |
| **Overall** | **LEAD** (fails plateau; also no 2013-22 support; single-account netting kills it) | **LEAD** (fails plateau) |

Other advanced cells: `ATR20_m1.75_ema50_tf1_X1` (the B10 book): passes uplift (+0.17/+0.28/+0.40) but fails worst week (+23% at 20%), plateau (0.25); `ATR14_m4_ema100_tf5_X2` (trail-only): uplift +0.24/+0.23/+0.12, fails plateau (0.38) and takes unlimited per-trade risk; the 5-min X2 no-EMA cells and TOP1 fail H2 uplift (-0.23..+0.05) and plateau.

## If it were to be taken forward (not FOUND; written because the brief asks for the exact checkbox)
DualStrat source is not on this box, so the checkbox/parameter names are the harness names: **WT book ON; ATR period 14; multiplier 3.0; EMA filter OFF; signal bars 10-minute (strategy on a 10-min series, ATR/EMA on the 10-min closes, stop/target 60/60 pt, entry at the next 1-min bar open if the execution series is 1-min); order bracket stop 60 pt / target 60 pt; same session windows as ST/HM (entries 18:00-15:00 ET except 09:00-09:58, flatten at the 16:55 bar open); 8 NQ contracts; per-book day rule 5R/-2R with R = $9,600; trade health OFF; WT must run as its own strategy instance on its own account, because as a third book inside the netted DualStrat account it loses the uplift**. Fixed WT-LIVE alternative (more trades, 7.6/day): ATR 20 / mult 2.0 / EMA 100 / 1-min, same exits. What would have to be true for FOUND: the plateau gate (a +-25% move in mult or bracket keeps 75% of the uplift in at least 6 of 8 neighbours) and a long-history read that is not negative at the faithful bracket scaling; neither holds today and nothing was re-run to change that.

## Honest assessment
- WT is a real, cheap-to-run trend-flip book in the 2023-2026 regime. It is not a durable independent edge: the faithful long-history read is negative (2013-2022 gross -0.33), it shares the pair's regime (all-weeks correlation 0.0-0.4), its edge depends on bracket width and multiplier, and its uplift as a third book in one NT8 account does not materialise because of netting.
- The earlier verdict ('rejected') rested on the retired HM; against the corrected pair WT adds Sharpe in every span as a separate sleeve, which is why this is a LEAD and not a NO. The multiplicity is 432 cells; the selection-corrected null says the clean-span structure is not pure selection noise (p = 0.03 for the best cell, < 0.02 for the top-10 mean).
- Remaining caveats: WT not verified against live NT8 fills; tick-engine vs 1-second fill differences move WT-LIVE's Sharpe between 1.54 and 1.98; 1-minute history engine is lower fidelity; account-level loss limits for a separate WT account are not modelled (the 'separate' rows use WT's own rules only, worst week -$93k to -$155k).

## Files
Code: `code/census/night_ins/ap_wt_core.py` (signals, 1-s book, 3-book account), `ap_wt_acct.py` (generic b11 account), `ap_wt_gate.py` (cell machinery, nulls, neighbours), `ap_wt_grid.py`, `ap_wt_cells.py`, `ap_wt_trio.py`, `ap_wt_sep.py`, `ap_wt_famnull.py`, `ap_wt_hist.py`, `ap_wt_hist2.py`, `ap_wt_th.py`, `ap_wt_th_rep.py`, `ap_wt_verdict.py`, `ap_wt_write.py`. Outputs: `outputs/autopilot/wt/` (grid_clean.csv, selected_top10.json, cells_scored.pkl, CELLS_*.csv, TRIO_all.csv, SEP_vs_NETTED.csv, HIST*.csv/txt, TH_*.csv, famnull.csv, rows_trio_*.parquet).

DONE WT
