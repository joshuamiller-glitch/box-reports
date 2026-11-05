

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
