# DS3_LOCATION_MAP - T-FAVORABLE-ZONES section A: where do signals work from (FZ-1, 2026-10-30)

Research only. Windows are own masks capped 20260206 (UNTOUCHED never read). Prereg `autopilot/FZ_A_prereg.md` sha256 d42dca5a... and selection file `out/fz/A_selection.json` sha256 fc665178... were logged in DECISIONS.md BEFORE the recent look.
The location store is NTZ-1's `out/poi_store` (685 streams, imported through `poi_api`, not forked); non-POI features (premium/discount x10 ranges, OTE, HTF Supertrend/EMA/Ichimoku/BOS x5 TF, book-defended flags) are in `out/fz/feat.parquet` (code `code/fz/`).

## How to read the numbers
* A signal = one of the 44,370 capped held-signal trades (10 books). Its outcome here is the held-signal MARKET trade at the signal second (1 lot, so per contract = per lot), N basis (no target-fill correction) as the primary, M beside it. Brackets are 60/60, so one trade has a standard deviation of ~40 pts: a lift of 1 pt per contract needs thousands of trades to see.
* **lift** = the same book's signals WITH the location minus the same book's signals WITHOUT it (precision-weighted over books), pts per contract; [95% CI] week-clustered; MDE = 2.8 x SE. P(target) lift is in percentage points x 100 (0.01 = 1 pp).
* Selection used PRE (2024-02..2025-06) and X' (2023-04..2024-01) only: eligible = lift_N>0 and lift_M>0 in BOTH windows, n>=300/100, keep<=85%; ranked by the inverse-variance z of the two. Pooled top 300 + per-book top 30 (10 books) = 514 cells got ONE recent look (L6M, HOLD, 2026, L3M view-only). The other ~10,900 cells have only PRE/X' numbers (their recent columns are sealed and were not decoded).
* Typical L6M standard error of a selected cell: 2.20 pts per contract (MDE ~6.15).

## 0. Headline (read this first)
* 11,422 location cells scored on PRE and X'; 1672 pass the "positive in both windows on N and M" eligibility (pure chance would pass about 1/16 = 700). 514 selected.
* **The selected locations do not persist.** Pooled-selected (300): mean lift PRE 2.26 (selection window), X' 5.31, **L6M -0.82** (recent, out of sample); 135 of 300 positive in L6M (coin flip = 150); HOLD mean -1.12; 2026 mean -2.77.
* Multiplicity over the 514 selected cells on L6M: White RC p = 0.068, cumulative-adjusted (Sidak over 61422+ cells) p = 1.00, Romano-Wolf survivors 5, PBO 0.60 (L6M) / 0.65 (all) - a PBO above 0.5 means the in-sample best is not the out-of-sample best.

## 1. Ranked favourable-location list (pooled; ranked on PRE+X' z, recent columns = the single look)
Columns: PRE / X' lifts are the selection windows (optimistic by construction); L6M [CI] is out of sample; MAE_L6M = lift in mean adverse excursion (negative = shallower drawdown); plc = rank of the real L6M lift among 200 random-location placebo draws at the same fire rate within book x session x week (1/201 is best); RW = Romano-Wolf survivor over the 514 selected cells; qtrs_pos = quarters with positive lift (2023Q2..2026Q1).

| location | keep_L6M | n_L6M | PRE | Xp | L6M | MDE | HOLD | Y26 | L3M_view | Ptgt_L6M_pp | MAE_L6M | M_L6M | plc | RW | qtrs_pos |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| any ORB behind <= 20 pts | 3% | 268 | 0.74 | 11.74 | 3.46 [-2.66,9.57] | 8.74 | -0.95 | 4.12 | 4.29 | 4.50 | 0.49 | 3.25 | 97/201 | N | 7/12 |
| mit ORB behind <= 20 pts | 3% | 268 | 0.74 | 11.74 | 3.46 [-2.66,9.57] | 8.74 | -0.95 | 4.12 | 4.29 | 4.50 | 0.49 | 3.25 | 89/201 | N | 7/12 |
| book flag=dflip10 | 10% | 958 | 3.98 | 3.55 | 0.94 [-3.40,5.27] | 6.19 | 1.58 | -8.60 | -0.65 | 0.66 | -1.00 | 0.91 | 89/201 | N | 11/12 |
| fresh ARR behind <= 5 pts | 6% | 631 | 3.00 | 8.85 | 1.70 [-3.37,6.77] | 7.24 | -0.18 | 2.69 | 2.91 | 0.42 | -0.61 | 1.68 | 84/201 | N | 10/12 |
| mit FIB behind <= 5 pts | 1% | 113 | 9.27 | 7.82 | -5.25 [-14.40,3.90] | 13.07 | -3.57 | -25.97 | -16.17 | -6.18 | 0.24 | -4.98 | 154/201 | N | 10/12 |
| PRF-class POI behind <= 10 AND book defS | 20% | 1995 | 3.04 | 1.29 | 0.75 [-1.65,3.14] | 3.42 | -0.17 | 4.08 | 0.34 | 0.59 | -0.47 | 0.72 | 81/201 | N | 9/12 |
| any FIB behind <= 5 pts | 1% | 117 | 9.96 | 6.70 | -4.21 [-13.17,4.75] | 12.80 | -2.72 | -24.03 | -15.83 | -5.20 | 0.60 | -3.99 | 160/201 | N | 10/12 |
| mit SWG behind <= 10 pts | 70% | 6785 | 1.77 | 7.46 | 0.93 [-2.58,4.44] | 5.01 | 0.91 | -2.42 | 0.82 | -0.41 | -0.42 | 0.95 | 5/201 | N | 8/12 |
| mit MAS behind <= 20 pts | 2% | 208 | 0.39 | 13.24 | 2.81 [-7.45,13.07] | 14.65 | 1.91 | 4.75 | 8.24 | 0.31 | -0.03 | 2.79 | 88/201 | N | 9/12 |
| fresh ARR behind <= 15 pts | 22% | 2117 | 2.65 | 2.45 | 1.25 [-2.10,4.59] | 4.78 | 0.77 | 2.17 | 3.91 | -0.07 | -0.33 | 1.25 | 112/201 | N | 10/12 |
| BOS-class POI behind <= 2 AND book defS | 12% | 1148 | 2.81 | 3.99 | 0.49 [-3.62,4.60] | 5.88 | -1.06 | -1.71 | -1.77 | 0.52 | -0.24 | 0.47 | 75/201 | N | 9/12 |
| FIB-class POI behind <= 5 AND book defS | 18% | 1741 | 2.83 | 0.32 | 1.95 [-1.15,5.05] | 4.43 | 1.10 | 5.16 | 0.58 | 1.60 | -0.86 | 1.88 | 56/201 | N | 11/12 |
| any MAS behind <= 15 pts | 2% | 156 | 5.06 | 7.47 | -10.07 [-17.33,-2.81] | 10.37 | -10.32 | -16.02 | -8.63 | -11.89 | 3.90 | -9.57 | 200/201 | N | 9/12 |
| any SWG behind <= 10 pts | 70% | 6837 | 1.89 | 6.77 | 0.80 [-2.68,4.27] | 4.97 | 0.86 | -2.52 | 0.63 | -0.50 | -0.34 | 0.82 | 14/201 | N | 8/12 |
| SWG-class POI behind <= 2 AND book defS | 24% | 2303 | 2.25 | 2.13 | 0.67 [-1.61,2.94] | 3.25 | 0.01 | 1.47 | -0.64 | 0.40 | -0.49 | 0.65 | 88/201 | N | 9/12 |
| any SWG behind <= 15 pts | 1% | 137 | 5.81 | 13.53 | -1.15 [-14.85,12.54] | 19.56 | -0.50 | 11.79 | 5.22 | 0.70 | -0.89 | -1.19 | 158/201 | N | 7/12 |
| any WYK behind <= 2 pts | 1% | 115 | 4.09 | 12.92 | -7.01 [-16.75,2.73] | 13.91 | -4.38 | -18.50 | -11.58 | -7.98 | 0.45 | -6.67 | 194/201 | N | 7/12 |
| mit WYK behind <= 2 pts | 1% | 115 | 4.09 | 12.92 | -7.01 [-16.75,2.73] | 13.91 | -4.38 | -18.50 | -11.58 | -7.98 | 0.45 | -6.67 | 197/201 | N | 7/12 |
| mit SWG behind <= 15 pts | 1% | 137 | 5.81 | 13.25 | -1.15 [-14.85,12.54] | 19.56 | -0.50 | 11.79 | 5.22 | 0.70 | -0.89 | -1.19 | 142/201 | N | 7/12 |
| ARR-class POI behind <= 2 AND book defS | 25% | 2416 | 2.05 | 1.93 | 0.14 [-2.08,2.35] | 3.16 | -0.57 | 2.45 | -0.34 | 0.11 | -0.43 | 0.13 | 144/201 | N | 10/12 |
| mit SWG behind <= 15 pts | 81% | 7842 | 1.28 | 8.83 | 0.56 [-4.10,5.21] | 6.65 | 0.87 | -5.24 | -0.09 | -0.77 | -0.41 | 0.59 | 29/201 | N | 8/12 |
| fresh ARR behind <= 20 pts | 44% | 4307 | 1.93 | 1.97 | -0.14 [-2.56,2.28] | 3.46 | -1.21 | 3.72 | -0.24 | -0.26 | -0.14 | -0.13 | 175/201 | N | 9/12 |
| PRF-class POI behind <= 5 AND book defS | 15% | 1472 | 3.09 | 0.11 | 0.90 [-2.19,3.98] | 4.41 | 0.03 | 3.93 | 0.97 | 0.76 | -0.58 | 0.86 | 64/201 | N | 9/12 |
| FIB-class POI behind <= 2 AND book defS | 14% | 1399 | 2.42 | 1.77 | 2.68 [-0.89,6.26] | 5.10 | 1.49 | 6.27 | 1.32 | 2.47 | -1.02 | 2.58 | 22/201 | N | 9/12 |
| fresh ARR behind <= 20 pts | 28% | 2761 | 1.85 | 2.93 | 0.50 [-2.44,3.44] | 4.20 | -0.17 | 2.03 | 1.92 | -0.82 | -0.13 | 0.54 | 111/201 | N | 10/12 |
| mit ARR behind <= 2 pts | 20% | 1949 | 2.13 | 3.20 | -1.66 [-5.39,2.07] | 5.33 | -2.17 | -10.05 | -1.18 | -1.65 | 0.58 | -1.59 | 102/201 | N | 8/12 |
| mit SWG behind <= 10 pts | 65% | 6324 | 1.15 | 6.92 | -0.17 [-3.29,2.96] | 4.46 | -0.04 | -1.56 | -0.81 | -1.20 | 0.10 | -0.11 | 24/201 | N | 8/12 |
| fresh ARR behind <= 15 pts | 37% | 3641 | 1.84 | 2.12 | 1.09 [-1.54,3.73] | 3.76 | 0.19 | 2.71 | 1.36 | 0.75 | -0.35 | 1.06 | 103/201 | N | 9/12 |
| fresh ARR behind <= 20 pts | 37% | 3604 | 2.15 | 2.16 | 1.16 [-2.31,4.62] | 4.95 | 0.77 | 4.16 | 2.59 | 0.70 | 0.28 | 1.13 | 62/201 | N | 10/12 |
| mit MAS behind <= 15 pts | 2% | 168 | 2.95 | 13.06 | 1.57 [-9.83,12.96] | 16.28 | 1.16 | 5.38 | 10.15 | -0.74 | 0.61 | 1.59 | 120/201 | N | 9/12 |

### 1b. Same cells, recent-ranked view (DESCRIPTIVE ONLY: sorted by L6M, which is burned - not a selection)
| location | keep_L6M | n_L6M | PRE | Xp | L6M | MDE | HOLD | Y26 | L3M_view | Ptgt_L6M_pp | MAE_L6M | M_L6M | plc | RW | qtrs_pos |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| any ORB behind <= 15 pts | 3% | 293 | 2.51 | 5.34 | 11.73 [4.29,19.17] | 10.63 | 8.40 | 9.36 | 14.43 | 11.23 | -3.92 | 11.24 | 1/201 | N | 9/12 |
| mit ORB behind <= 15 pts | 3% | 293 | 2.69 | 5.72 | 11.73 [4.29,19.17] | 10.63 | 8.40 | 9.36 | 14.43 | 11.23 | -3.92 | 11.24 | 1/201 | N | 9/12 |
| any PRF behind <= 2 pts | 1% | 94 | 7.49 | 5.24 | 10.65 [2.16,19.14] | 12.13 | 7.89 | 4.53 | 10.21 | 9.52 | -3.66 | 10.25 | 14/201 | N | 10/12 |
| mit ORB behind <= 10 pts | 2% | 196 | 0.97 | 8.00 | 10.37 [3.29,17.46] | 10.12 | 7.99 | 5.62 | 12.28 | 10.40 | -3.46 | 9.92 | 2/201 | N | 9/12 |
| any ARR behind <= 20 pts | 1% | 127 | 3.54 | 19.33 | 9.85 [-0.50,20.21] | 14.79 | 5.23 | 16.95 | 9.60 | 5.47 | -0.27 | 9.62 | 20/201 | N | 10/12 |
| mit ARR behind <= 20 pts | 1% | 127 | 3.54 | 19.02 | 9.85 [-0.50,20.21] | 14.79 | 5.23 | 16.95 | 9.60 | 5.47 | -0.27 | 9.62 | 18/201 | N | 10/12 |
| PDX-class POI behind <= 2 AND book defS | 1% | 142 | 5.23 | 2.78 | 7.18 [-1.94,16.30] | 13.03 | 4.02 | 4.05 | 13.20 | 5.57 | -3.16 | 6.95 | 6/201 | N | 9/12 |
| WYK-class POI behind <= 5 AND book defR | 1% | 131 | 4.06 | 3.40 | 6.18 [-3.36,15.72] | 13.62 | 10.60 | -4.83 | 6.58 | 5.23 | -3.22 | 5.96 | 24/201 | N | 9/12 |
| SES-class POI behind <= 2 AND book defS | 2% | 203 | 5.11 | 3.73 | 5.71 [-1.30,12.72] | 10.01 | 5.27 | 3.86 | 3.37 | 4.29 | -3.16 | 5.53 | 9/201 | N | 11/12 |
| PDX-class POI behind <= 5 AND book defS | 3% | 266 | 4.05 | 3.72 | 5.35 [-0.40,11.09] | 8.20 | 3.68 | 2.16 | 6.92 | 5.35 | -2.48 | 5.13 | 19/201 | N | 10/12 |
| mit ORB behind <= 5 pts | 1% | 91 | 1.93 | 15.21 | 5.29 [-8.49,19.07] | 19.69 | 4.84 | 12.33 | 1.12 | 3.29 | -0.92 | 5.13 | 50/201 | N | 10/12 |
| any ORB behind <= 5 pts | 1% | 91 | 1.93 | 15.21 | 5.29 [-8.49,19.07] | 19.69 | 4.84 | 12.33 | 1.12 | 3.29 | -0.92 | 5.13 | 51/201 | N | 10/12 |
| ORB-class POI behind <= 10 AND book defS | 8% | 764 | 1.91 | 2.85 | 4.74 [-0.13,9.62] | 6.96 | 2.20 | 11.19 | 5.96 | 3.58 | -2.70 | 4.58 | 10/201 | N | 6/12 |
| fresh ARR behind <= 5 pts | 9% | 919 | 1.21 | 3.59 | 4.70 [0.49,8.91] | 6.01 | 2.85 | 0.91 | 6.25 | 3.92 | -1.61 | 4.54 | 5/201 | N | 8/12 |
| any MAS behind <= 15 pts | 2% | 179 | 2.34 | 9.27 | 4.54 [-7.44,16.52] | 17.11 | 5.59 | 7.66 | 14.91 | 6.40 | -1.21 | 4.26 | 62/201 | N | 9/12 |

## 2. Plain lines (last 6 months, selected cells)
* "A signal fired with **any ORB behind <= 20 pts** reaches the target 57.1% of the time vs 52.8% without it (+4.5 pp), and earns 6.46 vs 3.15 pts per contract (lift 3.46 [-2.66,9.57], MDE 8.74) - L6M, n=268 signals, 3% of all signals. PRE+X'-selected.
* "A signal fired with **mit ORB behind <= 20 pts** reaches the target 57.1% of the time vs 52.8% without it (+4.5 pp), and earns 6.46 vs 3.15 pts per contract (lift 3.46 [-2.66,9.57], MDE 8.74) - L6M, n=268 signals, 3% of all signals. PRE+X'-selected.
* "A signal fired with **book flag=dflip10** reaches the target 53.3% of the time vs 52.9% without it (+0.7 pp), and earns 4.42 vs 3.12 pts per contract (lift 0.94 [-3.40,5.27], MDE 6.19) - L6M, n=958 signals, 10% of all signals. PRE+X'-selected.
* "A signal fired with **fresh ARR behind <= 5 pts** reaches the target 52.8% of the time vs 53.0% without it (+0.4 pp), and earns 4.38 vs 3.17 pts per contract (lift 1.70 [-3.37,6.77], MDE 7.24) - L6M, n=631 signals, 6% of all signals. PRE+X'-selected.
* "A signal fired with **mit FIB behind <= 5 pts** reaches the target 46.9% of the time vs 53.0% without it (-6.2 pp), and earns -1.85 vs 3.30 pts per contract (lift -5.25 [-14.40,3.90], MDE 13.07) - L6M, n=113 signals, 1% of all signals. PRE+X'-selected.
* "A signal fired with **PRF-class POI behind <= 10 AND book defS** reaches the target 53.5% of the time vs 52.8% without it (+0.6 pp), and earns 3.92 vs 3.07 pts per contract (lift 0.75 [-1.65,3.14], MDE 3.42) - L6M, n=1995 signals, 20% of all signals. PRE+X'-selected.
* "A signal fired with **any ORB behind <= 15 pts** reaches the target 63.8% of the time vs 52.6% without it (+11.2 pp), and earns 14.52 vs 2.89 pts per contract (lift 11.73 [4.29,19.17], MDE 10.63) - L6M, n=293 signals, 3% of all signals. PRE+X'-selected.
* "A signal fired with **mit ORB behind <= 15 pts** reaches the target 63.8% of the time vs 52.6% without it (+11.2 pp), and earns 14.52 vs 2.89 pts per contract (lift 11.73 [4.29,19.17], MDE 10.63) - L6M, n=293 signals, 3% of all signals. PRE+X'-selected.

## 3. The map over ALL 11,422 cells (PRE + X' only; the recent look is not used here)
Family summary (pooled PRE+X' lift in pts per contract; n_keep>=300). A family with no information has mean z ~ 0 and share_pos ~ 50%:

| fam | cells | median_lift | mean_z | share_pos | best_z | worst_z |
|---|---|---|---|---|---|---|
| BOOK | 27 | -0.2 | 0.06 | 0.37 | 4.06 | -2.01 |
| CONF | 29 | -0.2 | -1.1 | 0.48 | 2.5 | -36.67 |
| DISC | 40 | -0.63 | -0.46 | 0.32 | 1.85 | -2.63 |
| HTF | 30 | 0.89 | 0.68 | 0.9 | 1.85 | -0.26 |
| HTFN | 18 | 1.18 | 0.85 | 1.0 | 2.02 | 0.08 |
| HTFX | 30 | -0.71 | -0.48 | 0.2 | 0.79 | -1.97 |
| OTE | 5 | 0.86 | 0.54 | 0.6 | 2.48 | -0.69 |
| POI | 5000 | 0.36 | 0.22 | 0.6 | 4.16 | -3.54 |
| POICLS | 225 | 0.32 | 0.18 | 0.58 | 2.21 | -1.76 |
| POIDEF | 144 | 0.89 | 0.72 | 0.77 | 3.4 | -1.45 |
| POITF | 175 | 0.05 | 0.04 | 0.51 | 2.25 | -2.58 |

### 3a. POI class x freshness (stream-level cells, median over tf and D)

| cls | var | cells | median_lift | mean_z | share_pos | hit_pp |
|---|---|---|---|---|---|---|
| ARR | any | 629 | 0.61 | 0.4 | 0.72 | 0.42 |
| ARR | fresh | 335 | 0.54 | 0.4 | 0.67 | 0.38 |
| ARR | mit | 628 | 0.58 | 0.39 | 0.73 | 0.39 |
| BOS | any | 70 | 0.75 | 0.56 | 0.77 | 0.26 |
| BOS | fresh | 25 | 0.33 | 0.22 | 0.68 | 0.39 |
| BOS | mit | 70 | 0.7 | 0.52 | 0.79 | 0.15 |
| CRT | any | 29 | 0.41 | 0.16 | 0.59 | 0.59 |
| CRT | fresh | 6 | 1.28 | 0.37 | 0.67 | 1.93 |
| CRT | mit | 29 | 0.34 | 0.22 | 0.59 | 0.55 |
| DEV | any | 36 | -0.01 | 0.03 | 0.5 | 1.01 |
| DEV | fresh | 17 | -0.71 | -0.24 | 0.41 | 0.93 |
| DEV | mit | 28 | 1.93 | 0.81 | 1.0 | 3.2 |
| EQL | any | 62 | -0.29 | -0.15 | 0.4 | -0.61 |
| EQL | fresh | 12 | 0.99 | 0.43 | 0.92 | 1.49 |
| EQL | mit | 62 | -0.14 | -0.13 | 0.44 | -0.46 |
| FIB | any | 249 | -0.09 | 0.05 | 0.47 | -0.17 |
| FIB | fresh | 66 | -0.11 | 0.03 | 0.48 | 0.19 |
| FIB | mit | 244 | -0.04 | 0.09 | 0.47 | -0.26 |
| GAP | any | 28 | -0.03 | -0.08 | 0.5 | 0.84 |
| GAP | mit | 28 | 0.12 | 0.06 | 0.54 | 0.86 |
| KZ | any | 31 | -0.33 | -0.27 | 0.35 | -1.16 |
| KZ | mit | 31 | -0.27 | -0.26 | 0.39 | -1.15 |
| MAS | any | 96 | -0.32 | -0.14 | 0.47 | -0.73 |
| MAS | fresh | 1 | 0.86 | 0.32 | 1.0 | 0.59 |
| MAS | mit | 86 | -0.47 | -0.22 | 0.45 | -1.08 |
| OPN | any | 21 | -0.99 | -0.17 | 0.29 | -0.57 |
| OPN | mit | 20 | -0.57 | -0.09 | 0.35 | -0.53 |
| ORB | any | 109 | 0.52 | 0.32 | 0.67 | -0.52 |
| ORB | mit | 109 | 0.43 | 0.33 | 0.69 | -0.52 |
| PDX | any | 43 | -1.12 | -0.57 | 0.3 | -0.71 |
| PDX | mit | 43 | -1.02 | -0.52 | 0.3 | -0.71 |
| PIV | any | 81 | -0.02 | -0.08 | 0.49 | -0.31 |
| PIV | mit | 81 | -0.06 | -0.06 | 0.47 | -0.22 |
| PRF | any | 224 | -0.63 | -0.23 | 0.4 | -0.43 |
| PRF | fresh | 47 | -0.04 | 0.01 | 0.49 | -0.04 |
| PRF | mit | 216 | -0.57 | -0.22 | 0.4 | -0.48 |
| RND | any | 20 | 0.24 | 0.25 | 0.5 | 0.08 |
| RND | fresh | 20 | 0.24 | 0.25 | 0.5 | 0.08 |
| SES | any | 59 | 0.06 | -0.04 | 0.51 | -0.38 |
| SES | mit | 59 | 0.09 | -0.03 | 0.54 | -0.34 |
| SWG | any | 352 | 0.72 | 0.56 | 0.69 | 0.22 |
| SWG | fresh | 168 | 0.36 | 0.2 | 0.59 | 0.33 |
| SWG | mit | 352 | 0.82 | 0.62 | 0.68 | 0.33 |
| WYK | any | 39 | 1.15 | 0.43 | 0.62 | 0.46 |
| WYK | fresh | 1 | 0.18 | 0.08 | 1.0 | -0.17 |
| WYK | mit | 38 | 1.29 | 0.43 | 0.61 | 0.36 |

### 3b. Distance D x freshness (all stream-level cells)

| D | var | cells | median_lift | mean_z | share_pos |
|---|---|---|---|---|---|
| 0 | any | 76 | 0.56 | 0.32 | 0.74 |
| 0 | mit | 76 | 0.56 | 0.32 | 0.72 |
| 2 | any | 240 | 0.85 | 0.61 | 0.78 |
| 2 | fresh | 44 | 0.26 | 0.22 | 0.57 |
| 2 | mit | 230 | 0.91 | 0.64 | 0.78 |
| 5 | any | 372 | 0.67 | 0.34 | 0.67 |
| 5 | fresh | 102 | 0.15 | 0.17 | 0.54 |
| 5 | mit | 364 | 0.71 | 0.37 | 0.69 |
| 10 | any | 461 | 0.13 | 0.15 | 0.54 |
| 10 | fresh | 151 | 0.38 | 0.28 | 0.63 |
| 10 | mit | 448 | 0.17 | 0.21 | 0.58 |
| 15 | any | 499 | 0.09 | 0.08 | 0.52 |
| 15 | fresh | 186 | 0.59 | 0.34 | 0.66 |
| 15 | mit | 489 | 0.16 | 0.09 | 0.53 |
| 20 | any | 530 | 0.1 | 0.07 | 0.53 |
| 20 | fresh | 215 | 0.38 | 0.24 | 0.6 |
| 20 | mit | 517 | 0.16 | 0.09 | 0.54 |

### 3c. Premium / discount (side-aligned depth into the dealing range; fav = discount for longs / premium for shorts)

| location | n_PRE | keep% | PRE | Xp | z | hit_pp |
|---|---|---|---|---|---|---|
| discount/premium(fav) 5m <= 0.500 | 3084 | 13.0 | 1.36 | 3.72 | 1.85 | 1.99 |
| PREMIUM/discount(adverse) 1d >= 0.667 | 11002 | 45.0 | 1.01 | 4.91 | 1.44 | 0.85 |
| PREMIUM/discount(adverse) 15m >= 0.667 | 19322 | 78.0 | 1.49 | 0.35 | 1.24 | 1.28 |
| PREMIUM/discount(adverse) pweek >= 0.667 | 11180 | 45.0 | 1.76 | 1.3 | 1.13 | 0.49 |
| PREMIUM/discount(adverse) week >= 0.667 | 12994 | 53.0 | 1.6 | 1.2 | 1.04 | 0.52 |
| PREMIUM/discount(adverse) sess >= 0.667 | 18072 | 73.0 | 0.96 | 0.67 | 0.71 | -0.03 |
| PREMIUM/discount(adverse) 4h >= 0.667 | 12606 | 51.0 | 0.45 | 2.71 | 0.67 | 0.3 |
| PREMIUM/discount(adverse) day >= 0.667 | 16568 | 67.0 | 0.19 | 2.46 | 0.62 | 0.27 |
| discount/premium(fav) pweek <= 0.333 | 8414 | 34.0 | -1.26 | -4.43 | -1.46 | -1.31 |
| discount/premium(fav) 15m <= 0.200 | 527 | 2.0 | -6.15 | 3.18 | -1.53 | -2.75 |
| discount/premium(fav) week <= 0.200 | 2328 | 9.0 | -4.23 | -1.36 | -1.54 | -2.34 |
| discount/premium(fav) day <= 0.200 | 332 | 1.0 | -5.02 | -6.55 | -1.64 | -4.84 |
| discount/premium(fav) pweek <= 0.200 | 6482 | 26.0 | -1.91 | -6.47 | -2.23 | -2.61 |
| discount/premium(fav) 1d <= 0.200 | 6541 | 27.0 | -2.4 | -6.75 | -2.54 | -2.91 |
| discount/premium(fav) sess <= 0.200 | 428 | 2.0 | -5.5 | -9.32 | -2.63 | -4.69 |

### 3d. OTE

| location | n_PRE | keep% | PRE | Xp | z | hit_pp |
|---|---|---|---|---|---|---|
| OTE 1h | 530 | 2.0 | 7.47 | 7.0 | 2.48 | 5.46 |
| OTE 4h | 754 | 3.0 | 1.44 | 1.5 | 0.52 | 1.13 |
| OTE any | 2823 | 11.0 | 1.73 | -2.24 | 0.51 | 0.8 |
| OTE 1d | 1113 | 5.0 | 2.43 | -9.4 | -0.12 | -0.64 |
| OTE 15m | 205 | 1.0 | 2.2 | -6.16 | -0.32 | 0.36 |
| OTE 5m | 419 | 2.0 | -2.34 | 0.12 | -0.69 | -0.7 |

### 3e. HTF trend agreement ("agree" = tool in the signal direction)

| location | n_PRE | keep% | PRE | Xp | z | hit_pp |
|---|---|---|---|---|---|---|
| HTF ich 5m agree | 15882 | 64.0 | 2.2 | 2.5 | 1.85 | 1.54 |
| HTF ichc 1h agree | 12187 | 49.0 | 2.05 | 3.69 | 1.66 | 1.49 |
| HTF st 1h agree | 13495 | 55.0 | 2.11 | 3.96 | 1.57 | 1.67 |
| HTF ema 15m agree | 11114 | 45.0 | 0.91 | 4.53 | 1.23 | 0.87 |
| HTF ema50 15m agree | 18162 | 74.0 | 0.12 | 5.0 | 1.22 | 0.26 |
| HTF ich 1d agree | 8903 | 36.0 | 1.34 | 3.36 | 1.16 | 0.15 |
| HTF ich 1h agree | 9157 | 37.0 | 1.23 | 4.19 | 1.13 | 0.98 |
| HTF ema 1h agree | 10290 | 42.0 | 1.12 | 2.61 | 1.0 | 0.57 |
| HTF ema50 4h agree | 12852 | 52.0 | 0.44 | 0.66 | 0.31 | -0.36 |
| HTF ema 4h agree | 10138 | 41.0 | 0.46 | 0.35 | 0.29 | -0.78 |
| HTF st 4h agree | 12544 | 51.0 | -0.09 | 1.71 | 0.21 | 0.1 |
| HTF ema 1d agree | 9521 | 39.0 | -0.91 | 4.33 | 0.05 | -1.38 |
| HTF ichc 5m agree | 18897 | 77.0 | -0.11 | 0.1 | -0.02 | -0.35 |
| HTF st 5m agree | 20889 | 85.0 | -0.76 | 1.05 | -0.19 | -0.42 |
| HTF ema 5m agree | 14493 | 59.0 | -1.83 | 3.85 | -0.26 | -0.59 |

### 3e'. HTF trend AGAINST the signal (control)

| location | n_PRE | keep% | PRE | Xp | z | hit_pp |
|---|---|---|---|---|---|---|
| HTF ich 5m against | 1630 | 7.0 | 2.82 | -1.08 | 0.79 | 1.97 |
| HTF ema 15m against | 8256 | 34.0 | 2.0 | -3.09 | 0.66 | 1.15 |
| HTF ichc 5m against | 3082 | 13.0 | 0.76 | -0.05 | 0.35 | 1.0 |
| HTF ema 1d against | 9475 | 38.0 | 1.21 | -1.56 | 0.31 | 1.47 |
| HTF ichc 15m against | 6676 | 27.0 | 2.7 | -6.0 | 0.3 | 0.84 |
| HTF st 5m against | 3755 | 15.0 | 0.76 | -1.05 | 0.19 | 0.42 |
| HTF ema 1h against | 10192 | 41.0 | 0.38 | -2.45 | -0.17 | 0.16 |
| HTF ich 15m against | 4738 | 19.0 | 1.85 | -5.72 | -0.19 | -0.13 |
| HTF st 15m against | 7897 | 32.0 | -0.3 | -3.41 | -0.93 | -0.99 |
| HTF ema 5m against | 5424 | 22.0 | 0.52 | -4.61 | -0.94 | -0.61 |
| HTF ich 4h against | 8257 | 34.0 | -0.18 | -4.6 | -0.95 | -1.02 |
| HTF ema50 15m against | 6482 | 26.0 | -0.12 | -5.0 | -1.22 | -0.26 |
| HTF st 1h against | 11149 | 45.0 | -2.11 | -3.96 | -1.57 | -1.67 |
| HTF ich 1h against | 7726 | 31.0 | -2.92 | -2.18 | -1.87 | -1.74 |
| HTF ichc 1h against | 9463 | 38.0 | -2.67 | -3.71 | -1.97 | -1.88 |

### 3f. HTF agreement counts

| location | n_PRE | keep% | PRE | Xp | z | hit_pp |
|---|---|---|---|---|---|---|
| HTF tf=1h on 1h | 5180 | 21.0 | 3.57 | 3.76 | 2.02 | 2.13 |
| HTF tf=15m on 15m | 7395 | 30.0 | 3.12 | 0.22 | 1.79 | 1.3 |
| HTF tf=15m on 15m | 16681 | 68.0 | -0.09 | 5.88 | 1.46 | 0.95 |
| HTF tf=1h4h1d on 1h4h1d | 11965 | 49.0 | 1.04 | 3.82 | 1.21 | 0.56 |
| HTF tf=1h on 1h | 11129 | 45.0 | 1.14 | 4.44 | 1.16 | 0.9 |
| HTF tf=5m on 5m | 10076 | 41.0 | 0.13 | 3.83 | 0.98 | 0.65 |
| HTF tf=1d on 1d | 5865 | 24.0 | -0.61 | 8.19 | 0.96 | -0.87 |
| HTF tf=1h4h1d on 1h4h1d | 15740 | 64.0 | 1.14 | 2.52 | 0.92 | 0.39 |
| HTF tf=1d on 1d | 9916 | 40.0 | 0.95 | 2.5 | 0.86 | -0.27 |
| HTF tf=1h4h1d on 1h4h1d | 8375 | 34.0 | 0.17 | 4.14 | 0.85 | -0.25 |
| HTF tf=1h on 1h | 13717 | 56.0 | 0.64 | 2.71 | 0.66 | 0.33 |
| HTF tf=1d on 1d | 12035 | 49.0 | 0.91 | 0.85 | 0.58 | -0.32 |
| HTF tf=4h on 4h | 10140 | 41.0 | -0.1 | 2.74 | 0.52 | -0.16 |
| HTF tf=5m on 5m | 18382 | 75.0 | 0.06 | 1.47 | 0.46 | 0.14 |
| HTF tf=4h on 4h | 5558 | 23.0 | 0.23 | 1.33 | 0.35 | -0.7 |
| HTF tf=4h on 4h | 12206 | 50.0 | -0.12 | 2.07 | 0.31 | -0.34 |
| HTF tf=5m on 5m | 20933 | 85.0 | -0.59 | 1.67 | 0.13 | -0.49 |
| HTF tf=15m on 15m | 13787 | 56.0 | -0.61 | 2.32 | 0.08 | -0.48 |

### 3g. Book defended (side-aligned flags at the signal second)

| location | n_PRE | keep% | PRE | Xp | z | hit_pp |
|---|---|---|---|---|---|---|
| book flag=dflip10 | 2480 | 10.0 | 3.98 | 3.55 | 4.06 | 2.69 |
| book flag=abs3 | 2 | 0.0 | 59.39 | -47.06 | 3.36 | -7.18 |
| book flag=sweep | 6389 | 26.0 | 1.62 | 1.23 | 1.99 | 0.98 |
| book flag=bigp1 | 3954 | 16.0 | 1.69 | 1.78 | 1.68 | 0.19 |
| book flag=micro25 | 6974 | 28.0 | -0.03 | 2.96 | 1.62 | 2.05 |
| book flag=bigp50 | 148 | 1.0 | 7.53 | -2.55 | 1.46 | 2.41 |
| book flag=micro1 | 8020 | 33.0 | 0.14 | 2.19 | 1.26 | 0.72 |
| book flag=ice | 12 | 0.0 | 6.11 | 12.67 | 1.05 | 13.14 |
| book flag=oppheavy4 | 514 | 2.0 | -0.79 | -7.51 | -1.11 | -0.38 |
| book flag=refill1 | 4915 | 20.0 | -2.64 | 1.44 | -1.47 | -1.17 |
| book flag=oppheavy6 | 87 | 0.0 | -5.61 | -13.82 | -2.01 | -4.55 |
| book flag=dflip30 | 1615 | 7.0 | -1.9 | -4.36 | -2.01 | -1.86 |
| book flag=abs2 | 6 | 0.0 | -1.59 | -47.06 | -49.19 | -57.47 |
| book flag=abs5 | 0 | 0.0 | nan | nan | nan | nan |
| book flag=abs10 | 0 | 0.0 | nan | nan | nan | nan |

### 3h. Confluence (number of distinct POI classes / timeframes behind within D)

| location | n_PRE | keep% | PRE | Xp | z | hit_pp |
|---|---|---|---|---|---|---|
| confluence ntf>=2 within 5 (fresh) | 15372 | 62.0 | 1.51 | 3.86 | 2.5 | 0.98 |
| confluence ncls>=2 within 10 (fresh) | 14923 | 61.0 | 1.36 | 3.64 | 2.08 | 1.05 |
| confluence ntf>=2 within 2 (fresh) | 6646 | 27.0 | 1.19 | 2.05 | 1.84 | 1.36 |
| confluence ntf>=3 within 5 (fresh) | 11558 | 47.0 | 1.03 | 2.51 | 1.7 | 0.43 |
| confluence ncls>=2 within 5 (fresh) | 8897 | 36.0 | 0.28 | 3.81 | 1.53 | 1.12 |
| confluence ntf>=2 within 10 (fresh) | 20996 | 85.0 | 0.65 | 3.65 | 1.02 | -0.56 |
| confluence ncls>=3 within 10 (fresh) | 7875 | 32.0 | 0.73 | 0.32 | 0.71 | 0.46 |
| confluence ncls>=2 within 2 (any) | 23618 | 96.0 | 0.51 | 3.79 | 0.7 | 0.03 |
| confluence ntf>=3 within 2 (any) | 23715 | 96.0 | -2.23 | -1.88 | -0.98 | -2.67 |
| confluence ncls>=3 within 5 (any) | 23421 | 95.0 | -2.08 | -2.06 | -1.0 | -2.65 |
| confluence ncls>=3 within 2 (fresh) | 784 | 3.0 | -4.22 | 0.28 | -1.07 | -1.07 |
| confluence ncls>=4 within 2 (fresh) | 183 | 1.0 | -8.15 | 1.67 | -1.11 | -1.72 |
| confluence ntf>=3 within 5 (any) | 24321 | 99.0 | -5.47 | -4.82 | -1.41 | -6.45 |
| confluence ncls>=4 within 5 (fresh) | 1325 | 5.0 | -3.67 | 0.58 | -1.44 | -0.95 |
| confluence ntf>=2 within 10 (any) | 24594 | 100.0 | -4.25 | -59.14 | -36.67 | -52.89 |

### 3i. POI behind AND book flag (defended)

| location | n_PRE | keep% | PRE | Xp | z | hit_pp |
|---|---|---|---|---|---|---|
| PIV-class POI behind <= 2 AND book defA | 3 | 0.0 | 18.96 | 58.46 | 37.15 | 30.71 |
| PDX-class POI behind <= 5 AND book defA | 4 | 0.0 | 21.84 | 9.91 | 29.88 | 23.13 |
| MAS-class POI behind <= 5 AND book defA | 9 | 0.0 | -8.49 | 29.85 | 28.83 | 30.03 |
| PDX-class POI behind <= 2 AND book defA | 3 | 0.0 | 9.94 | 30.2 | 12.84 | 14.39 |
| PRF-class POI behind <= 10 AND book defS | 5031 | 20.0 | 3.04 | 1.29 | 3.4 | 1.76 |
| BOS-class POI behind <= 2 AND book defS | 2884 | 12.0 | 2.81 | 3.99 | 3.06 | 2.44 |
| FIB-class POI behind <= 5 AND book defS | 4416 | 18.0 | 2.83 | 0.32 | 3.04 | 1.86 |
| SWG-class POI behind <= 2 AND book defS | 5722 | 23.0 | 2.25 | 2.13 | 2.98 | 1.61 |
| WYK-class POI behind <= 5 AND book defA | 2 | 0.0 | -62.3 | -0.11 | -51.55 | -28.83 |
| SES-class POI behind <= 2 AND book defA | 3 | 0.0 | -30.41 | -62.37 | -55.53 | -24.55 |
| OPN-class POI behind <= 10 AND book defA | 3 | 0.0 | -62.75 | -12.9 | -80.45 | -49.69 |
| KZ-class POI behind <= 2 AND book defA | 3 | 0.0 | -30.56 | nan | nan | nan |
| KZ-class POI behind <= 5 AND book defA | 3 | 0.0 | -30.56 | nan | nan | nan |
| OPN-class POI behind <= 2 AND book defA | 0 | 0.0 | nan | 58.76 | nan | nan |
| WYK-class POI behind <= 2 AND book defA | 1 | 0.0 | -63.5 | nan | nan | nan |

## 4. By book (PRE+X' pooled lift of the group, pts per contract; protocol-dependence)

| group | ST | HM | WT | KB | SM | PE | PB | DN | MV | MA |
|---|---|---|---|---|---|---|---|---|---|---|
| disc fav third (1h,4h,1d,pday) | -1.07 | -2.97 | -0.95 | -1.73 | -2.74 | -3.09 | -3.80 | -1.20 | -2.10 | -3.11 |
| HTF st+ich+bos agree (1h,4h) | 2.10 | 2.64 | 0.60 | 1.94 | 3.68 | 2.68 | 3.76 | 2.18 | 0.96 | 1.80 |
| POI fresh behind<=5 (cls PDX,SES,ARR) | -0.35 | 3.55 | 2.28 | 2.53 | 7.43 | -0.07 | -1.75 | 6.61 | 6.93 | 2.36 |
| POI mit(retest) behind<=5 (cls PDX,SES,ARR) | 1.69 | -2.45 | 5.06 | -2.37 | 6.52 | 6.36 | -5.21 | 2.67 | 3.34 | -0.99 |
| book defended (abs2/refill2/imbsup2) | 3.28 | 0.24 | -0.02 | -2.92 | 0.17 | 1.85 | 0.59 | -1.75 | -1.33 | 7.56 |

## 5. Per-book ranked lists (selected on PRE+X' per book; recent columns = the single look; pts per contract within that book)

### ST

| location | PRE | Xp | L6M | SE | n_L6M | HOLD | Y26 | Ptgt_pp |
|---|---|---|---|---|---|---|---|---|
| fresh ARR behind <= 20 pts | 5.36 | 4.11 | 1.41 | 2.86 | 490 | 0.87 | -0.54 | 0.34 |
| any MAS behind <= 20 pts | 13.99 | 13.41 | -6.56 | 10.59 | 30 | -3.84 | 8.34 | -5.29 |
| any EQL behind <= 20 pts | 5.51 | 3.08 | 1.99 | 3.17 | 597 | 2.18 | -2.24 | 0.82 |
| mit any CRT-class POI behind <= 2 pts | 6.62 | 16.07 | 3.80 | 6.01 | 77 | 5.78 | 2.31 | 2.89 |
| mit EQL behind <= 20 pts | 5.69 | 2.46 | 2.50 | 3.09 | 589 | 2.45 | -2.24 | 1.19 |
| any RND behind <= 2 pts | 8.49 | 22.67 | 15.87 | 4.99 | 65 | 14.94 | 16.13 | 13.48 |
| fresh RND behind <= 2 pts | 8.49 | 22.67 | 15.87 | 4.99 | 65 | 14.94 | 16.13 | 13.48 |
| fresh ARR behind <= 2 pts | 8.20 | 15.75 | -2.45 | 7.76 | 52 | 1.38 | 8.97 | -1.91 |

### HM

| location | PRE | Xp | L6M | SE | n_L6M | HOLD | Y26 | Ptgt_pp |
|---|---|---|---|---|---|---|---|---|
| mit ARR behind <= 2 pts | 8.90 | 7.99 | -1.73 | 5.45 | 127 | -1.20 | 2.60 | -1.78 |
| any ARR behind <= 2 pts | 8.90 | 7.99 | -1.73 | 5.45 | 127 | -1.20 | 2.60 | -1.78 |
| any ARR behind <= 0 pts (in-zone) | 9.39 | 6.01 | 1.18 | 6.07 | 115 | 0.74 | 10.84 | 0.28 |
| mit ARR behind <= 0 pts (in-zone) | 9.39 | 6.01 | 1.18 | 6.07 | 115 | 0.74 | 10.84 | 0.28 |
| mit ARR behind <= 10 pts | 9.09 | 7.62 | 3.70 | 6.29 | 150 | 2.82 | -5.79 | 0.09 |
| any PRF behind <= 15 pts | 8.95 | 15.16 | -10.96 | 7.69 | 82 | -9.30 | 27.64 | -8.82 |
| mit PRF behind <= 15 pts | 9.98 | 16.52 | -8.60 | 7.65 | 70 | -8.18 | 37.31 | -6.73 |
| any ARR behind <= 2 pts | 7.64 | 2.92 | -4.71 | 4.15 | 236 | -5.73 | 6.11 | -3.74 |

### WT

| location | PRE | Xp | L6M | SE | n_L6M | HOLD | Y26 | Ptgt_pp |
|---|---|---|---|---|---|---|---|---|
| mit SES behind <= 10 pts | 14.62 | 7.97 | -3.66 | 6.50 | 40 | -2.89 | 10.86 | -4.72 |
| any SES behind <= 10 pts | 14.62 | 7.97 | -3.66 | 6.50 | 40 | -2.89 | 10.86 | -4.72 |
| mit SES behind <= 15 pts | 10.46 | 4.12 | -1.86 | 4.99 | 54 | -0.23 | 4.17 | -2.28 |
| any SES behind <= 15 pts | 10.46 | 4.12 | -1.86 | 4.99 | 54 | -0.23 | 4.17 | -2.28 |
| mit SWG behind <= 5 pts | 0.22 | 8.46 | -1.61 | 1.38 | 962 | -1.14 | -4.68 | -2.26 |
| any SES behind <= 20 pts | 8.46 | 2.41 | 0.24 | 3.46 | 76 | 0.71 | -5.71 | -0.42 |
| mit SES behind <= 20 pts | 8.46 | 2.41 | 0.24 | 3.46 | 76 | 0.71 | -5.71 | -0.42 |
| any SWG behind <= 5 pts | 0.22 | 8.05 | -1.54 | 1.37 | 963 | -1.08 | -4.68 | -2.16 |

### KB

| location | PRE | Xp | L6M | SE | n_L6M | HOLD | Y26 | Ptgt_pp |
|---|---|---|---|---|---|---|---|---|
| any ORB behind <= 20 pts | 7.46 | 31.70 | -10.45 | 7.64 | 39 | -12.69 | -10.47 | -9.30 |
| mit ORB behind <= 20 pts | 7.46 | 31.70 | -10.45 | 7.64 | 39 | -12.69 | -10.47 | -9.30 |
| any WYK behind <= 20 pts | 2.29 | 22.74 | -6.86 | 9.16 | 43 | -1.37 | -48.04 | -3.65 |
| mit WYK behind <= 20 pts | 1.85 | 22.74 | -8.45 | 9.10 | 42 | -2.57 | -48.04 | -4.97 |
| any ORB behind <= 20 pts | 12.49 | 8.62 | -2.87 | 6.41 | 48 | 0.23 | -6.38 | -4.37 |
| mit ORB behind <= 20 pts | 12.49 | 8.62 | -2.87 | 6.41 | 48 | 0.23 | -6.38 | -4.37 |
| any ORB behind <= 15 pts | 12.70 | 17.65 | -6.56 | 7.64 | 35 | -5.68 | -13.26 | -7.39 |
| mit ORB behind <= 15 pts | 12.70 | 17.65 | -6.56 | 7.64 | 35 | -5.68 | -13.26 | -7.39 |

### SM

| location | PRE | Xp | L6M | SE | n_L6M | HOLD | Y26 | Ptgt_pp |
|---|---|---|---|---|---|---|---|---|
| mit SWG behind <= 20 pts | 11.51 | 21.25 | 8.78 | 7.43 | 248 | 11.94 | 17.04 | 6.96 |
| any SWG behind <= 20 pts | 10.56 | 20.14 | 10.00 | 7.46 | 249 | 14.13 | 17.04 | 8.00 |
| mit SWG behind <= 20 pts | 10.95 | 15.84 | 11.10 | 7.40 | 248 | 13.03 | 12.38 | 8.88 |
| confluence ntf>=3 within 5 (fresh) | 10.79 | 6.70 | 2.60 | 6.42 | 196 | 2.33 | -3.79 | 1.53 |
| any SWG behind <= 20 pts | 11.82 | 12.66 | 8.49 | 7.16 | 238 | 12.56 | 11.98 | 6.47 |
| mit SWG behind <= 20 pts | 12.25 | 11.43 | 7.42 | 7.10 | 237 | 10.63 | 11.98 | 5.57 |
| mit SWG behind <= 20 pts | 11.00 | 14.69 | 6.46 | 6.77 | 248 | 9.89 | 12.11 | 5.05 |
| any SWG behind <= 20 pts | 9.99 | 14.68 | 10.00 | 7.46 | 249 | 13.15 | 12.38 | 8.00 |

### PE

| location | PRE | Xp | L6M | SE | n_L6M | HOLD | Y26 | Ptgt_pp |
|---|---|---|---|---|---|---|---|---|
| fresh ARR behind <= 5 pts | 16.05 | 14.46 | 11.53 | 15.75 | 19 | 11.36 | 15.40 | 8.96 |
| book flag=bigp1 | 4.00 | 12.25 | -1.21 | 6.70 | 130 | 0.70 | 11.35 | -2.42 |
| mit ARR behind <= 10 pts | 13.15 | 9.82 | 14.61 | 5.55 | 1141 | 15.17 | 8.15 | 9.90 |
| mit SWG behind <= 10 pts | 3.49 | 9.60 | 7.40 | 4.11 | 785 | 8.09 | -1.92 | 5.48 |
| any ARR behind <= 15 pts | 9.90 | 12.91 | 14.41 | 6.04 | 1122 | 15.78 | 5.24 | 13.80 |
| HTF tf=1h on 1h | 6.94 | 5.39 | 2.86 | 4.74 | 258 | 2.22 | -12.27 | 1.18 |
| any SWG behind <= 10 pts | 3.40 | 9.38 | 7.41 | 4.19 | 789 | 8.31 | -2.82 | 5.52 |
| any FIB behind <= 20 pts | 12.12 | 15.06 | -9.51 | 10.03 | 27 | 3.06 | 33.76 | -8.53 |

### PB

| location | PRE | Xp | L6M | SE | n_L6M | HOLD | Y26 | Ptgt_pp |
|---|---|---|---|---|---|---|---|---|
| any ARR behind <= 10 pts | 8.46 | 23.58 | 4.56 | 7.29 | 794 | 7.46 | -11.80 | 1.63 |
| mit PRF behind <= 15 pts | 17.39 | 8.06 | 2.39 | 9.19 | 33 | 3.07 | -27.34 | -2.87 |
| mit SWG behind <= 20 pts | 3.52 | 18.21 | 11.16 | 3.89 | 659 | 12.32 | 15.97 | 7.20 |
| mit ARR behind <= 10 pts | 6.39 | 24.49 | 3.97 | 7.56 | 789 | 6.83 | -14.99 | 1.13 |
| any SWG behind <= 5 pts | 5.24 | 23.97 | 14.56 | 8.09 | 794 | 13.71 | -1.34 | 10.72 |
| any SWG behind <= 5 pts | 4.26 | 22.37 | 10.18 | 6.01 | 771 | 8.98 | -10.63 | 7.75 |
| CRT-class POI behind <= 10 AND book defS | 18.59 | 2.02 | -10.09 | 6.64 | 57 | -9.33 | -19.97 | -9.27 |
| fresh PRF behind <= 15 pts | 6.74 | 5.92 | -1.35 | 3.74 | 253 | -1.62 | 7.57 | -1.85 |

### DN

| location | PRE | Xp | L6M | SE | n_L6M | HOLD | Y26 | Ptgt_pp |
|---|---|---|---|---|---|---|---|---|
| mit any SWG-class POI behind <= 2 pts | 6.64 | 62.03 | 7.02 | 38.29 | 697 | 5.74 |  | 3.80 |
| any any SWG-class POI behind <= 2 pts | 6.64 | 62.03 | 7.02 | 38.29 | 697 | 5.74 |  | 3.80 |
| any FIB behind <= 20 pts | 16.10 | 18.00 | 13.59 | 11.69 | 21 | 6.60 | -16.21 | 13.28 |
| any FIB behind <= 20 pts | 10.26 | 12.92 | -2.56 | 7.47 | 58 | -1.79 | -4.86 | -2.24 |
| fresh ARR behind <= 20 pts | 9.24 | 8.13 | -3.76 | 9.16 | 63 | -7.44 | -16.44 | -3.28 |
| any FIB behind <= 15 pts | 9.32 | 10.61 | 0.72 | 8.69 | 43 | 1.08 | -10.11 | -0.31 |
| any FIB behind <= 5 pts | 7.66 | 15.92 | -4.21 | 9.98 | 22 | -10.75 | 14.90 | -3.90 |
| mit SWG behind <= 5 pts | 7.97 | 3.31 | -5.21 | 3.54 | 457 | -4.50 | -2.80 | -1.75 |

### MV

| location | PRE | Xp | L6M | SE | n_L6M | HOLD | Y26 | Ptgt_pp |
|---|---|---|---|---|---|---|---|---|
| any PIV behind <= 10 pts | 5.41 | 37.40 | -5.57 | 12.10 | 25 | -2.31 | -14.32 | -2.81 |
| mit PIV behind <= 10 pts | 6.19 | 36.67 | -5.57 | 12.10 | 25 | -2.31 | -14.32 | -2.81 |
| fresh FIB behind <= 15 pts | 10.49 | 12.80 | 4.92 | 6.72 | 74 | 1.51 | 19.62 | 3.53 |
| any KZ behind <= 10 pts | 21.63 | 1.08 | 9.20 | 17.44 | 15 | -2.29 | -66.05 | 9.37 |
| mit KZ behind <= 10 pts | 21.63 | 1.08 | 9.20 | 17.44 | 15 | -2.29 | -66.05 | 9.37 |
| fresh any 30s POI behind <= 2 pts | 5.27 | 5.80 | -9.10 | 4.45 | 222 | -8.00 | -29.20 | -7.66 |
| mit ARR behind <= 2 pts | 6.33 | 6.45 | -5.83 | 4.84 | 157 | -6.79 | -13.71 | -4.20 |
| any ARR behind <= 2 pts | 6.29 | 6.06 | -6.49 | 4.62 | 159 | -7.75 | -13.71 | -4.90 |

### MA

| location | PRE | Xp | L6M | SE | n_L6M | HOLD | Y26 | Ptgt_pp |
|---|---|---|---|---|---|---|---|---|
| any SWG behind <= 15 pts | 16.72 | 63.69 | -27.77 | 15.26 | 397 | -29.05 | -21.33 | -15.84 |
| fresh any 30s POI behind <= 20 pts | 31.07 | 63.45 | 28.31 | 18.29 | 398 | 31.02 | 67.71 | 21.69 |
| any any 30s POI behind <= 2 pts | 20.74 | 64.19 | 7.59 | 29.76 | 403 | 4.89 | 66.93 | 4.59 |
| any any PRF-class POI behind <= 20 pts | 21.50 | 63.45 | 2.96 | 11.45 | 394 | -6.13 | -15.59 | 0.72 |
| mit SWG behind <= 20 pts | 14.13 | 63.57 | -7.76 | 20.85 | 399 | 8.93 | -55.49 | -8.11 |
| any ARR behind <= 20 pts | 29.17 | 48.95 | -29.14 | 21.67 | 402 | -12.64 | -55.49 | -25.77 |
| mit ARR behind <= 15 pts | 38.49 | 8.50 | 16.45 | 24.72 | 400 | 23.96 | -15.03 | 11.89 |
| mit any SWG-class POI behind <= 2 pts | 25.08 | 27.29 | -0.04 | 18.03 | 391 | 2.67 | -25.79 | -1.77 |

## 6. Drift by quarter of the top-10 pooled locations (lift in pts per contract, N)

| location | 2023Q2 | 2023Q3 | 2023Q4 | 2024Q1 | 2024Q2 | 2024Q3 | 2024Q4 | 2025Q1 | 2025Q2 | 2025Q3 | 2025Q4 | 2026Q1 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| any ORB behind <= 20 pts | 13.1 | 12.1 | 10.4 | 30.1 | -10.9 | 11.1 | 13.7 | -0.6 | -9.5 | -13.0 | -0.4 | 4.1 |
| mit ORB behind <= 20 pts | 13.1 | 12.1 | 10.4 | 30.1 | -10.9 | 11.1 | 13.7 | -0.6 | -9.5 | -13.0 | -0.4 | 4.1 |
| book flag=dflip10 | 3.3 | 2.3 | 4.0 | 1.8 | 5.2 | 5.8 | 1.2 | 3.7 | 5.1 | 2.9 | 5.3 | -8.6 |
| fresh ARR behind <= 5 pts | 3.4 | 8.2 | 10.2 | 10.7 | 6.4 | 1.7 | 0.7 | -1.0 | 6.6 | -3.4 | 1.7 | 2.7 |
| mit FIB behind <= 5 pts | 2.7 | 12.6 | 7.0 | 3.8 | 8.3 | 14.9 | 2.7 | 16.8 | 5.8 | 5.3 | -4.1 | -26.0 |
| PRF-class POI behind <= 10 AND book defS | 1.5 | 3.1 | 1.0 | -0.7 | 5.5 | 3.5 | 0.3 | 4.9 | 2.3 | -2.6 | -0.7 | 4.1 |
| any FIB behind <= 5 pts | 2.8 | 11.3 | 5.3 | 3.8 | 11.4 | 16.0 | 3.4 | 18.2 | 3.0 | 7.3 | -4.1 | -24.0 |
| mit SWG behind <= 10 pts | 12.4 | 10.0 | -0.5 | 4.5 | 3.1 | -1.4 | -0.9 | 2.0 | 4.3 | 1.8 | 2.0 | -2.4 |
| mit MAS behind <= 20 pts | 13.3 | 18.5 | 10.8 | 1.6 | 3.9 | -13.3 | 0.4 | -0.3 | 5.9 | -7.0 | 12.0 | 4.8 |
| fresh ARR behind <= 15 pts | 0.2 | 0.5 | 4.1 | 5.9 | 2.6 | 2.9 | -0.2 | 2.9 | 3.5 | -1.6 | 2.1 | 2.2 |

## 7. Session columns of the top-10 pooled (lift pts per contract: PRE | X' | L6M)

| location | asia | close | london | nyam | nypm | pre |
|---|---|---|---|---|---|---|
| any ORB behind <= 20 pts | 2.8 | 18.7 | 9.5 | -36.1 | -23.5 | 74.0 | 6.6 | 5.8 | -18.4 | 2.5 | 10.5 | 6.0 | -5.4 | 6.7 | 8.9 | -14.0 | 28.5 | 41.5 |
| mit ORB behind <= 20 pts | 2.8 | 18.7 | 9.5 | -36.1 | -23.5 | 74.0 | 6.6 | 5.8 | -18.4 | 2.5 | 10.5 | 6.0 | -5.4 | 6.7 | 8.9 | -14.0 | 28.5 | 41.5 |
| book flag=dflip10 | 7.6 | 3.1 | -5.1 | -37.9 | -26.4 | 59.0 | 4.1 | -2.3 | -3.5 | 1.1 | 4.7 | 5.9 | 6.0 | 6.5 | 0.8 | -1.4 | 4.4 | 15.5 |
| fresh ARR behind <= 5 pts | 5.7 | 9.6 | -0.7 | 2.8 | -13.5 |  | -4.6 | 11.5 | -5.2 | 10.0 | 10.1 | 18.3 | 3.2 | 2.6 | -1.8 | 7.6 | 10.5 | 12.8 |
| mit FIB behind <= 5 pts | 13.1 | -2.1 | -27.7 | 96.2 |  |  | 23.0 | 6.7 | 12.1 | 4.4 | 13.4 | -9.4 | -1.8 | 6.2 | -4.1 | -14.7 | 42.9 | 16.7 |
| PRF-class POI behind <= 10 AND book defS | 3.3 | -3.0 | -1.8 | 21.4 | -2.6 | -32.8 | 0.8 | 6.9 | -0.1 | 3.3 | 0.4 | 4.5 | 4.9 | 0.0 | -1.2 | 3.3 | 13.1 | 2.3 |
| any FIB behind <= 5 pts | 15.4 | -4.9 | -29.5 | 96.2 |  |  | 24.1 | 3.9 | 15.1 | 3.0 | 14.4 | -7.8 | -0.6 | 6.3 | -4.1 | -14.7 | 42.9 | 16.7 |
| mit SWG behind <= 10 pts | -1.0 | 6.2 | -2.4 | -3.8 | -28.2 | -10.9 | 2.1 | 18.8 | 2.2 | 4.2 | 8.0 | 0.3 | 1.4 | 2.8 | 2.5 | 3.5 | 3.7 | 4.1 |
| mit MAS behind <= 20 pts | 7.6 | 11.4 | 11.0 |  | 19.9 |  | -9.9 | -5.1 | -7.1 | -5.6 | 20.7 | -2.9 | 1.9 | 21.9 | 27.2 | 23.4 | 1.5 | -48.5 |
| fresh ARR behind <= 15 pts | 5.2 | 2.2 | -0.3 | -14.0 | -15.4 | -5.8 | 0.4 | 8.2 | -1.9 | 3.1 | 1.7 | 5.3 | 2.6 | -0.6 | -0.8 | 2.3 | 0.2 | 9.1 |

## 8. Method notes and caveats
* Concurrency: the same signal is often in several books; week-clustered SEs are per book-stratified. Book-defended flags are from the l2set bit-planes (10-s windows, side-aligned); absorption/iceberg are rare (<1%). "Defended AT the POI" for POIs farther than the visible 10 levels (~2.5 pts) is a signal-second book flag plus the POI behind, not the size at the POI price.
* POI distance = entry back to the POI near edge between entry and stop (poi_api behind channel). Fresh = never touched since formation, mit = touched before = retest. Round numbers are raw-frame; HTF arrays/profile levels are those of CF-ENG/CF-A.
* Placebo: random fire-rate masks permuted within book x session x week (200 draws). The random-level placebo for POI cells and the shuffled-day placebo are run on the section-B rule cells (finalists).