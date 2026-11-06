

# DS3_INSTR2_BTC: T-INSTR-2 section 1, BTC / MBT own grids - interim 1 (stage 1: grid screen), 2026-11-05 20:16Z
Owner S4b. Prereg autopilot/T2_BTC_PREREG.md (sha256 21d031120fda0126b85c82ae8ad83798f5ce249507f25261a187c34a326752cb) + merged-series amendment in DECISIONS.md, grid n_tested 144,648 per series (T2BTC_NTESTED.md; four series: BTCM merged, MBT, BTC standard), written before the grids ran. Code l2vast/ds3/code/t2/ (t2_lib.py engine, t2_fam.py 11 families, t2_grid.py, t2_gate.py, t2_null.py, t2_top.py, t2_audit.py); cell tables /mnt/l2/l2vast/ds3_t2/<series>_cells.parquet; finalist trade frames /mnt/l2/l2vast/instr2_trades/<series>/<cell_id>.parquet (entry / exit epoch seconds, side, stop pts, R, lots_screen at $1,200 risk, lots_cap (MBT 1.7% participation cap per session from INSTR2_SESSIONS.md), risk $, net $, session, cell id). Shadow only, no PASS claims, nothing live. **Look-ahead audit passed:** bar-by-bar truncation test at 37 intraday cuts (17:00-18:30, 08:30-10:00, 15:30-16:10, 00:00-02:30 ET, random sessions, DST shifts) x 37 signal sets (every 12th set plus all of OR break, VWAP reclaim, session-extreme, failed-break, prior-day H/L): 0 failures in 1,369 checks; all levels are running or from the completed previous label day. Data: MBT 1-min 2022-01..2026-10, BTC standard 2022-01..2026-10, BTCM = union (MBT bars else BTC bars + last common offset); pre-2023 history is 2022 only (one bear year), so X' (2023-05..10) is the only 'old' window with n; MDE per cell = 2.8 x SE of R over the full sample (n 150-1,500 -> 0.07-0.25 R). Costs (proxy): entry/flat 2 ticks, stop 3 ticks, target needs 1 tick beyond; fee proxy $1.78 MBT / $4.84 BTC per round trip.
**CAP:** Z2's participation cap (1.7% of the median 5-min volume) allows 1.3-7.4 MBT contracts per 5 min by session (asia 1.43, london 1.29, pre 3.49, nyam 7.41, nypm 3.67, close 3.45) and < 1 BTC standard contract (0.14-0.90): BTC standard results are labelled CAP-BREACH; the usable leg is MBT. At the cap, risk per trade is $50-$540 (an MBT lot with a 3-ATR stop risks $37-$73): even a real edge here is a book of tens of dollars per week against the NQ stack's $17.7k per week (V0).
## Stage-1 summary per series
| series | cells (n>=30) | n>=150 | recent gate | tolerant | tolerant + persistence | share of cells with mean R > 0 | best full-sample t | cells t>3 |
|---|---|---|---|---|---|---|---|---|
| MBT (micro, own series) | 144396 | 141624 | 10381 | 2120 | 102 | 0.044 | 2.85 | 0 |

| series | cells (n>=30) | n>=150 | recent gate | tolerant | tolerant + persistence | share of cells with mean R > 0 | best full-sample t | cells t>3 |
|---|---|---|---|---|---|---|---|---|
| BTC+MBT merged (signal series; MBT lots tradable) | 144312 | 141624 | 10589 | 1359 | 119 | 0.034 | 3.41 | 7 |

| series | cells (n>=30) | n>=150 | recent gate | tolerant | tolerant + persistence | share of cells with mean R > 0 | best full-sample t | cells t>3 |
|---|---|---|---|---|---|---|---|---|
| BTC standard 5 BTC (own series) CAP-BREACH | 144480 | 141960 | 14710 | 1723 | 25 | 0.040 | 3.25 | 3 |

By session (cells passing each gate), MBT:

```
        g_recent  tolerant  clear
ses                              
all          186        58      4
asia         884       640     68
london      3274       358      6
nyam        2325       363     24
nypm          74         3      0
pre         3638       698      0
```
By family, MBT cells passing tolerant + persistence:

```
fam
F1_keltner    80
F5_hmavwap    22
```

Family null (random side per signal, same entries / brackets): **pending** (BTCM 100 worlds running; MBT and NKD to follow within the load rule of 3 workers; NKD costs ~28 min per world, so a reduced world count will be reported with its number).  (BTCM series; MBT / BTC share the same grid and signal families.)
## Ranked table (16 columns; mean R per trade by window; R = net of costs / stop distance; 'thin' = fewer than 30 trades in the window; Calmar = (sum R per year)/maxDD in R; stack gain = NQ stack Calmar with the book added at $1,200 risk per trade, V0 base, carrying week dropped)
### MBT (own series)
| instrument | session | family | params | L1M | L3M | L6M | HOLD | MID | PRE | X' | maxDD (R) | Calmar (R/yr / maxDD) | corr to NQ stack | stack gain (Calmar HOLD / PRE at 1x) | placebo / family | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| MBT | asia | F1_keltner | b10_ema13_atr14_m2.5 6ATR/2R/T120 | +0.47 | +0.19 | +0.24 | +0.21 | -0.01 | -0.03 | -0.11 | 5.0 | 0.91 | +0.05 | 0.24->0.24 / 0.20->0.21 | pending | STAGE-1 clear; family null pending |
| MBT | asia | F1_keltner | b10_ema8_atr20_m2.5 3ATR/1.5R/T30 | +0.87 | +0.35 | +0.30 | +0.29 | +0.04 | -0.08 | +0.02 | 6.3 | 0.73 | -0.01 | 0.24->0.24 / 0.20->0.21 | pending | STAGE-1 clear; family null pending |
| MBT | asia | F1_keltner | b10_ema13_atr20_m2.5 6ATR/1R/T120 | +0.40 | +0.24 | +0.18 | +0.19 | +0.00 | -0.16 | -0.18 | 7.6 | 0.53 | +0.04 | 0.24->0.24 / 0.20->0.20 | pending | STAGE-1 clear; family null pending |
| MBT | asia | F1_keltner | b10_ema8_atr20_m2.5 3ATR/1.5R/T120 | +1.50 | +0.53 | +0.38 | +0.32 | +0.20 | +0.19 | -0.02 | 5.5 | 1.24 | +0.05 | 0.24->0.24 / 0.20->0.21 | pending | STAGE-1 clear; family null pending |
| MBT | asia | F1_keltner | b10_ema8_atr20_m2.5 2ATR/2R/T30 | +1.22 | +0.43 | +0.40 | +0.37 | +0.12 | -0.15 | -0.10 | 10.1 | 0.59 | -0.00 | 0.24->0.24 / 0.20->0.21 | pending | STAGE-1 clear; family null pending |
| MBT | asia | F1_keltner | b10_ema8_atr20_m2.5 $1200/2R/T30 | +1.40 | +0.63 | +0.43 | +0.35 | +0.18 | +0.15 | -0.07 | 10.5 | 0.65 | -0.04 | 0.24->0.24 / 0.20->0.21 | pending | STAGE-1 clear; family null pending |
### BTC+MBT merged (signal series)
| instrument | session | family | params | L1M | L3M | L6M | HOLD | MID | PRE | X' | maxDD (R) | Calmar (R/yr / maxDD) | corr to NQ stack | stack gain (Calmar HOLD / PRE at 1x) | placebo / family | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTCM | asia | F1_keltner | b10_ema13_atr14_m2.5 6ATR/2R/T120 | +0.46 | +0.19 | +0.24 | +0.20 | -0.02 | -0.03 | -0.09 | 7.3 | 0.49 | +0.06 | 0.24->0.24 / 0.20->0.20 | pending | STAGE-1 clear; family null pending |
| BTCM | asia | F1_keltner | b10_ema13_atr14_m2.5 6ATR/1R/T120 | +0.48 | +0.27 | +0.21 | +0.18 | -0.02 | -0.06 | +0.01 | 5.0 | 0.69 | +0.04 | 0.24->0.24 / 0.20->0.20 | pending | STAGE-1 clear; family null pending |
| BTCM | asia | F1_keltner | b10_ema8_atr20_m2.5 3ATR/1.5R/T30 | +0.87 | +0.35 | +0.30 | +0.29 | +0.04 | -0.08 | +0.53 | 6.6 | 0.77 | -0.03 | 0.24->0.24 / 0.20->0.21 | pending | STAGE-1 clear; family null pending |
| BTCM | asia | F1_keltner | b10_ema13_atr14_m2.5 6ATR/noTP/T120 | +0.46 | +0.19 | +0.22 | +0.19 | -0.02 | -0.08 | -0.09 | 7.3 | 0.47 | +0.04 | 0.24->0.24 / 0.20->0.20 | pending | STAGE-1 clear; family null pending |
| BTCM | asia | F1_keltner | b10_ema8_atr20_m2.5 3ATR/1.5R/T120 | +1.50 | +0.52 | +0.38 | +0.32 | +0.30 | +0.19 | +0.61 | 6.8 | 1.26 | +0.03 | 0.24->0.24 / 0.20->0.21 | pending | STAGE-1 clear; family null pending |
| BTCM | asia | F1_keltner | b10_ema13_atr20_m2.5 6ATR/1R/T120 | +0.40 | +0.20 | +0.18 | +0.19 | +0.00 | -0.18 | -0.01 | 5.9 | 0.77 | +0.03 | 0.24->0.24 / 0.20->0.20 | pending | STAGE-1 clear; family null pending |
### BTC standard (CAP-BREACH)
| instrument | session | family | params | L1M | L3M | L6M | HOLD | MID | PRE | X' | maxDD (R) | Calmar (R/yr / maxDD) | corr to NQ stack | stack gain (Calmar HOLD / PRE at 1x) | placebo / family | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC | nyam | F1_keltner | b5_ema13_atr7_m0.5 3ATR/noTP/T120 | +0.01 | +0.39 | +0.18 | +0.11 | +0.14 | -0.03 | +0.02 | 31.6 | 0.40 | +0.06 | 0.24->0.23 / 0.20->0.21 | pending | STAGE-1 clear CAP-BREACH; family null pending |
| BTC | asia | F2_supertrend | b15_atr14_m4 4ATR/1R/T120 | +0.35 | +0.13 | +0.09 | +0.13 | +0.16 | +0.16 | +0.04 | 5.1 | 1.29 | +0.00 | 0.24->0.24 / 0.20->0.21 | pending | STAGE-1 clear CAP-BREACH; family null pending |
| BTC | nyam | F5_hmavwap | b1_hma20 $2400/noTP/T120 | +0.20 | +0.18 | +0.16 | +0.13 | +0.14 | +0.01 | -0.02 | 27.8 | 0.38 | +0.01 | 0.24->0.24 / 0.20->0.19 | pending | STAGE-1 clear CAP-BREACH; family null pending |
| BTC | asia | F2_supertrend | b15_atr14_m4 $2400/1R/T120 | +0.41 | +0.18 | +0.09 | +0.16 | +0.10 | +0.09 | +0.08 | 7.1 | 0.77 | +0.01 | 0.24->0.24 / 0.20->0.21 | pending | STAGE-1 clear CAP-BREACH; family null pending |
| BTC | nyam | F2_supertrend | b15_atr5_m2 $2400/1R/T30 | -0.07 | +0.06 | +0.07 | +0.06 | -0.03 | +0.14 | -0.00 | 9.9 | 0.85 | +0.04 | 0.24->0.23 / 0.20->0.21 | pending | STAGE-1 clear CAP-BREACH; family null pending |
| BTC | asia | F2_supertrend | b15_atr14_m4 6ATR/1R/T120 | +0.33 | +0.12 | +0.06 | +0.09 | +0.25 | +0.13 | +0.09 | 3.4 | 1.89 | +0.01 | 0.24->0.24 / 0.20->0.21 | pending | STAGE-1 clear CAP-BREACH; family null pending |

**Plain sentence (interim, stage 1):** over 144,648 cells per series, 96% of the cells lose money after costs (median mean R -0.07 to -0.08); the few that survive the tolerant gate and persistence are one signal cluster, the 10-minute Keltner flip with a wide 2.5-ATR band in the Asia session (n 165-350 trades, t about 3.4 against 144,648 cells tested), plus a few Supertrend 15-minute and HMA-VWAP cells; correlation to the NQ stack is about 0.0-0.08, which is the diversification property, but the dollars at the participation cap are negligible and the family test decides whether any of it is more than best-of-F.

## Family null result (S4b, BTC/MBT merged series BTCM, 100 random-side worlds, completed; per-world results in /mnt/l2/l2vast/ds3_t2/BTCM_null.pkl)
Random side per signal (same entries, same 84 brackets, same sessions), gates applied exactly as to the real grid. Observed vs null: tolerant cells 1,359 vs null median 1,127 (95th 1,314), p 0.05; tolerant + persistence cells 119 vs null median 14 (95th 36, max 53 in 100 worlds), p 0.01; max over cells of min(t_L6M, t_HOLD): observed 3.42 vs null median 3.07 (95th 3.63), p 0.13; the same maximum among tolerant cells 3.01 vs null median 2.71 (95th 3.23), p 0.22. Reading: the COUNT of persistently positive cells is above the random-side null (14 distinct signal sets, essentially the 10-minute Keltner flip with a 2.5-ATR band in the Asia session, 165-350 trades), but the STRENGTH of the best cell (t about 3.4) is inside the null range (p 0.13 / 0.22): the family max-stat does not reach the bar (p <= .10). Caveat on the null: random side destroys the structure of trend-flip signals (consecutive Keltner flips alternate side by construction), so a persistence excess against it also reflects that structure; a shifted-trigger or shuffled-day null is not run. Economics: the cluster trades the Asia session where MBT is THIN (participation cap 1.43 contracts per 5 min) and BTC standard is below one contract: at the cap a trade risks about $50, and the book's correlation to the NQ stack is 0.0-0.08 with no change in stack Calmar (0.24 -> 0.24). Label: best-of-F WATCH (CAP-bound), not a lead; the bar is not cleared (family max-stat p 0.13). MBT and BTC own-series nulls and the purged walk-forward were not run because T-FIND (autopilot/DIRECTIVE_T_FIND_20261105.md) supersedes the remaining generic grids once the current stage finished; the BTCM null governs the BTC / MBT underlying.


## Crypto follow-up: deepening the 10-minute Keltner / wide band / Asia cluster - 2026-11-06 01:50Z
Prereg autopilot/T2_CRYPTO_CLUSTER_PREREG.md (sha256 e124855d2a3d751aa4780ea9162b35443bb3553a4a5d455e097728f3b5468bc4, before any follow-up statistic); n_tested 4,536 neighbourhood cells (54 signal sets x 84 brackets, Asia session) + 600 fresh placebo worlds (T2BTC_NTESTED.md); code l2vast/ds3/code/t2/t2_cluster.py, t2_cluster_an.py, t2_cluster_null.py; data /mnt/l2/l2vast/ds3_t2/cluster_*.pkl. Series BTCM (merged), MBT, BTC standard (CAP-BREACH). Shadow only, no purchases, no PASS claims. **History starts 2022-01: pre-2023 means 2022 only (one bear year); X' (2023-05..10-11) is a 5-month window; there is no 2013+ check for BTC / MBT.**
### (1) Plateau, not a spike
Median over the 84 brackets of the full-sample mean R of the four centre sets (b10, m 2.5), their share of positive brackets, passing cells, and the neighbours (one parameter changed by one step: bar 5 / 15, EMA 8 / 13 / 21, ATR 14 / 20, band 2.0 / 3.0) with a positive median:
```
              centre  med_mean  share_pos  clear  neigh  neigh_pos  neigh_med
 b10 ema8 atr14 m2.5     0.074      1.000     20      6          5      0.094
 b10 ema8 atr20 m2.5     0.144      1.000     63      6          4      0.065
b10 ema13 atr14 m2.5     0.050      0.905      4      7          5      0.056
b10 ema13 atr20 m2.5     0.056      0.893     14      7          5      0.044
```
All four centres have a positive median (0.05-0.14 R) with 89-100% of their brackets positive, and 4 of 6 or 5 of 6-7 neighbours positive (67-83%, above the 60% PLATEAU rule); 10 of the 54 sets have a passing cell and 22 a tolerant cell. The ridge is band >= 2.5 and bar >= 10 min with EMA 8-13; it is a plateau of one family (slow Keltner flips in the Asia session), not a single spike.
### (2) Year-by-year (calendar years; mean R, median over the brackets of the set, n per year about 30-60)
```
                 set  Y2022  Y2023  Y2024  Y2025  Y2026  brackets
 b10 ema8 atr20 m2.5  0.140  0.015  0.074  0.172  0.178        84
b10 ema13 atr14 m2.5  0.099 -0.189  0.104  0.053  0.132        84
b10 ema13 atr20 m2.5  0.117 -0.154  0.110  0.029  0.114        84
 b10 ema8 atr14 m2.5  0.079 -0.048  0.036  0.148  0.122        84
```
The reference cells (top six by min(t_L6M, t_HOLD), BTCM):
```
                            cell   n     mean        Y2022        Y2023        Y2024        Y2025        Y2026  q_pos
  (10, 13, 14, 2.5) 6ATR/2R/T120 254 0.068541 +0.14 (n 53) -0.14 (n 45) +0.11 (n 51) +0.08 (n 60) +0.13 (n 45)   0.70
  (10, 13, 14, 2.5) 6ATR/1R/T120 254 0.066288 +0.10 (n 53) -0.09 (n 45) +0.11 (n 51) +0.08 (n 60) +0.12 (n 45)   0.65
  (10, 8, 20, 2.5) 3ATR/1.5R/T30 165 0.149906 +0.11 (n 34) +0.13 (n 29) +0.09 (n 32) +0.14 (n 35) +0.27 (n 35)   0.65
(10, 13, 14, 2.5) 6ATR/noTP/T120 254 0.065687 +0.17 (n 53) -0.14 (n 45) +0.09 (n 51) +0.06 (n 60) +0.12 (n 45)   0.65
 (10, 8, 20, 2.5) 3ATR/1.5R/T120 165 0.250371 +0.14 (n 34) +0.16 (n 29) +0.34 (n 32) +0.29 (n 35) +0.31 (n 35)   0.70
  (10, 13, 20, 2.5) 6ATR/1R/T120 262 0.083688 +0.15 (n 57) -0.11 (n 42) +0.11 (n 53) +0.09 (n 59) +0.14 (n 51)   0.65
```
2022 (the only pre-2023 year) is positive in all centre sets (+0.08 to +0.14 R); 2023 is the weak year (-0.19 to +0.02 for the EMA 13 sets; +0.02 and -0.05 for EMA 8); 2024-2026 are positive and 2025-2026 are the strongest. Quarterly: the share of quarters with a positive sum is 65-70% (20 quarters).
### (3) MBT vs BTC vs BTCM, and what the executable size means
Correlation of the 4,536 full-sample cell means across series: BTCM-MBT 0.96, BTCM-BTC 0.87, MBT-BTC 0.86. Reference cells by series:
```
(10, 13, 14, 2.5) 6ATR/2R/T120: BTCM n 254 mean +0.069 t 1.80; MBT n 243 mean +0.091 t 2.29; BTC n 286 mean +0.049 t 1.36
(10, 13, 14, 2.5) 6ATR/1R/T120: BTCM n 254 mean +0.066 t 1.95; MBT n 243 mean +0.068 t 1.98; BTC n 286 mean +0.053 t 1.60
(10, 8, 20, 2.5) 3ATR/1.5R/T30: BTCM n 165 mean +0.150 t 2.64; MBT n 164 mean +0.135 t 2.34; BTC n 177 mean +0.089 t 1.56
(10, 13, 14, 2.5) 6ATR/noTP/T120: BTCM n 254 mean +0.066 t 1.71; MBT n 243 mean +0.097 t 2.19; BTC n 286 mean +0.043 t 1.22
(10, 8, 20, 2.5) 3ATR/1.5R/T120: BTCM n 165 mean +0.250 t 3.36; MBT n 164 mean +0.200 t 2.70; BTC n 177 mean +0.208 t 2.75
(10, 13, 20, 2.5) 6ATR/1R/T120: BTCM n 262 mean +0.084 t 2.49; MBT n 247 mean +0.080 t 2.38; BTC n 263 mean +0.059 t 1.67
```
MBT carries the same edge as BTCM (t 2.0-2.7 before fees); BTC standard is weaker (t 1.2-2.8) and CAP-BREACH (cap 0.14 contracts in Asia). Executable size on MBT (cap 1.43 contracts per 5 min in Asia, 39-59 trades per year, risk $76-143 per trade, before fees):
```
                            cell   n  per_year  lots_mean  risk_mean  usd_trade  usd_week  usd_total  usd_week_screen
  (10, 13, 14, 2.5) 6ATR/2R/T120 243     57.81       1.43     143.23      11.99     13.33    2914.53           121.57
  (10, 13, 14, 2.5) 6ATR/1R/T120 243     57.81       1.43     143.23      11.79     13.11    2864.97            91.01
  (10, 8, 20, 2.5) 3ATR/1.5R/T30 164     39.39       1.43      76.31      12.69      9.61    2081.24           123.12
(10, 13, 14, 2.5) 6ATR/noTP/T120 243     57.81       1.43     143.23      10.96     12.18    2662.70           128.94
 (10, 8, 20, 2.5) 3ATR/1.5R/T120 164     39.39       1.43      76.31      17.62     13.34    2888.89           182.09
  (10, 13, 20, 2.5) 6ATR/1R/T120 247     59.11       1.43     142.26      13.86     15.75    3422.60           108.60
```
That is $9.6-15.8 per week (about $500-820 per year) at the cap, against the NQ stack's $17.7k per week (V0): 0.1% of it.
### (4) Own-parameter walk-forward (BTCM; at each quarter from 2023-Q1 choose the cell with the best mean R over the trailing window (n >= 12, mean > 0) and trade it the next quarter; 4,536 cells; placebo = 300 random picks among the eligible cells per quarter)
```
 lookback  annual  quarters_traded  trades   sumR  meanR  placebo_median  placebo_p
        4   False               16      79 13.000  0.165           0.020      0.023
        8   False               16      74  7.021  0.095           0.032      0.246
        4    True               16      88 12.458  0.142           0.033      0.066
        8    True               16      64 -2.250 -0.035           0.034      0.880
```
Fixed centre cell held over the same quarters: mean R 0.134 (131 trades). Quarterly refit on the trailing 4 quarters gives 0.165 R per trade (79 trades, 16 quarters) vs the random-pick placebo median 0.02 (p 0.02); the annual refit on the trailing 4 quarters 0.142 (p 0.07); the trailing 8-quarter variants are 0.095 (p 0.25) and -0.035 (p 0.88): positive in three of four refit rules, but the sample is 64-88 trades.
### (5) Fresh family test: 200 new worlds per placebo on the 54-set neighbourhood (Asia, tolerant + persistence), seeds 1001-1200
| placebo (200 worlds) | cells passing tolerant + persistence: null median / 95th / max (observed 127) | p | distinct signal sets with a passing cell: null median / max (observed 10) | p | max min(t_L6M, t_HOLD): null median / 95th (observed 2.89) | p |
|---|---|---|---|---|---|---|
| random side | 1 / 19 / 57 | 0.005 | 1 / 4 | 0.005 | 2.22 / 3.08 | 0.085 |
| forward-shifted trigger 5-60 min, same side | 7 / 24 / 69 | 0.005 | 2 / 6 | 0.005 | 2.10 / 2.69 | 0.030 |
| forward day shift 3-30 days, same clock minute and side | 1 / 16 / 75 | 0.005 | 1 / 4 | 0.005 | 2.14 / 3.02 | 0.090 |

The count excess HOLDS against all three placebos (the observed 127 passing cells and 10 passing sets exceed the maximum of 200 worlds, p 0.005 = the floor), and the max-stat is at p 0.085 (random side), 0.030 (forward-shifted trigger) and 0.090 (day shift). **Selection caveat (important): the neighbourhood was chosen because it contained the best persistently positive cells of the 144,648-cell grid, so this fresh-world test is conditional on the selected region; the unconditional family test is the full-grid null (count p 0.01, max-stat p 0.13).** There is no out-of-selection data (history 2022-2026 was used to pick the region).
### (6) Stack (weekly and daily correlation with the Q1-A ts2 NQ stack, carry-dropped Calmar in dollars)
```
(10, 13, 14, 2.5) 6ATR/2R/T120 | corr daily V0 -0.06 V2 -0.06 | weekly V0 -0.08 V2 -0.04 | Calmar L6M 0.701 -> 0.701 (capped) / 0.701 (screen $1,200) | HOLD 0.238 -> 0.238 / 0.240 | PRE 0.202 -> 0.203 / 0.208
(10, 13, 14, 2.5) 6ATR/1R/T120 | corr daily V0 -0.06 V2 -0.06 | weekly V0 -0.06 V2 -0.03 | Calmar L6M 0.701 -> 0.701 (capped) / 0.701 (screen $1,200) | HOLD 0.238 -> 0.238 / 0.240 | PRE 0.202 -> 0.203 / 0.207
(10, 8, 20, 2.5) 3ATR/1.5R/T30 | corr daily V0 -0.04 V2 -0.04 | weekly V0 -0.01 V2 -0.00 | Calmar L6M 0.701 -> 0.701 (capped) / 0.701 (screen $1,200) | HOLD 0.238 -> 0.239 / 0.245 | PRE 0.202 -> 0.202 / 0.203
(10, 13, 14, 2.5) 6ATR/noTP/T120 | corr daily V0 -0.06 V2 -0.05 | weekly V0 -0.07 V2 -0.03 | Calmar L6M 0.701 -> 0.701 (capped) / 0.701 (screen $1,200) | HOLD 0.238 -> 0.238 / 0.240 | PRE 0.202 -> 0.203 / 0.207
(10, 8, 20, 2.5) 3ATR/1.5R/T120 | corr daily V0 -0.06 V2 -0.05 | weekly V0 -0.07 V2 -0.04 | Calmar L6M 0.701 -> 0.701 (capped) / 0.701 (screen $1,200) | HOLD 0.238 -> 0.239 / 0.248 | PRE 0.202 -> 0.203 / 0.208
(10, 13, 20, 2.5) 6ATR/1R/T120 | corr daily V0 -0.06 V2 -0.05 | weekly V0 -0.01 V2 +0.03 | Calmar L6M 0.701 -> 0.701 (capped) / 0.701 (screen $1,200) | HOLD 0.238 -> 0.238 / 0.240 | PRE 0.202 -> 0.204 / 0.209
```
Correlation about -0.06 to 0.00 (V0 and V2): a diversifier in the correlation sense. At the capped size the stack Calmar does not move (0.701 -> 0.701 L6M; HOLD 0.238 -> 0.238-0.239; PRE unchanged to three decimals); at the screen size ($1,200 risk per trade, not executable under the cap) it moves by +0.001 to +0.010 (HOLD).
### (7) Fees and spread
Fees were NOT in the grid costs (the grid charged points only: 2 ticks entry, 3 ticks stop, 2 ticks flat); with the MBT round trip proxy $1.78 per lot (FEES.md has no MBT; CME exchange + clearing + NFA is about $0.50 and the broker commission is the unknown; PROXY-MICRO) the fee is 0.03-0.06 R per trade on these stops:
```
                            cell   n  mean_R_nofee  fee_R  mean_R_fee  t_nofee  t_fee  usd_trade_fee  fee_usd_trade
  (10, 13, 14, 2.5) 6ATR/2R/T120 243         0.091  0.030       0.061    2.288  1.529          9.449          2.545
  (10, 13, 14, 2.5) 6ATR/1R/T120 243         0.068  0.030       0.038    1.978  1.098          9.245          2.545
  (10, 8, 20, 2.5) 3ATR/1.5R/T30 164         0.135  0.058       0.078    2.336  1.329         10.145          2.545
(10, 13, 14, 2.5) 6ATR/noTP/T120 243         0.097  0.030       0.066    2.187  1.508          8.412          2.545
 (10, 8, 20, 2.5) 3ATR/1.5R/T120 164         0.200  0.058       0.143    2.698  1.904         15.070          2.545
  (10, 13, 20, 2.5) 6ATR/1R/T120 247         0.080  0.029       0.050    2.376  1.491         11.311          2.545
```
After the fee the mean R is 0.04-0.14 and the t-statistics fall to 1.1-1.9 (MBT, before multiple-testing), and the net is $8-15 per trade at the cap. The Asia spread cannot be measured (MBT L2 / ticks not owned, no purchase): proxy = the median 1-min MBT bar range in the Asia session, 25 points (p25 5, p75 55) against the base round-trip cost of 35 points (10 + 15 + 10) i.e. about 1.4 x one median bar range. Cost sensitivity of mean R (points costs x 0 / 0.5 / 1 / 2 / 3; no fee):
```
                            cell   cm0  cm0.5   cm1   cm2    cm3
  (10, 13, 14, 2.5) 6ATR/2R/T120 0.101  0.085 0.069 0.035  0.001
  (10, 13, 14, 2.5) 6ATR/1R/T120 0.097  0.080 0.066 0.034 -0.007
  (10, 8, 20, 2.5) 3ATR/1.5R/T30 0.205  0.175 0.150 0.081  0.022
(10, 13, 14, 2.5) 6ATR/noTP/T120 0.100  0.083 0.066 0.031 -0.004
 (10, 8, 20, 2.5) 3ATR/1.5R/T120 0.324  0.271 0.250 0.163  0.115
  (10, 13, 20, 2.5) 6ATR/1R/T120 0.112  0.097 0.084 0.053  0.017
```
All six reference cells stay positive at 2 x base cost; three of six fall to about zero or below at 3 x. 
### Verdict
Label: **WATCH** (best-of-F, CAP-bound), not a lead. For: a plateau of one family across 10 sets, positive in 2022 and 2024-2026, MBT and BTCM agree, correlation about 0 to the NQ stack, walk-forward positive in three of four refit rules (quarterly refit p 0.02), and the fresh-world count and max-stat tests pass at p <= 0.10 conditional on the selected region. Against: the unconditional full-grid test fails the max-stat bar (p 0.13), fees take 0.03-0.06 R and leave t 1.1-1.9, 2023 is negative for the EMA 13 sets, the edge sits in the thin Asia session where MBT cap is 1.43 contracts (about $8-15 per week net, 0.1% of the stack), the history is one bear year plus 3.8 years, and there is no data on box to measure the real Asia spread. It does not clear the bar and is not worth running as a P&L contributor; it is a documented Asia-session trend-persistence regularity of BTC futures that a larger account or MBT size could revisit.
