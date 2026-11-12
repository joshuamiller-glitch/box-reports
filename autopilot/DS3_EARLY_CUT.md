# DS3_EARLY_CUT - T-EARLY-CUT page 1 (W-X) - Thu Nov 12 07:50:45 AM UTC 2026

Shadow only; first-order (stored 1-s mid paths, LPB_BASE trades, exact promotion running, none finished). Table of record: DS3_EARLY_CUT_TABLE.md (+CSV). Prereg: EARLY_CUT_PREREG.md (sha in DECISIONS.md). Acceptance lists: DS3_EARLY_CUT_ACCEPT.md. Code: code/th_ec.

## 0. Bottom line (plain words)

- Where the full stops are (L6M, live rules, state cut already on): K7 13.1/week costing $18.6k/week, A7 3.9/wk $4.7k, U7 3.5/wk $10.8k, M7 2.0/wk $2.7k, H7 0.9/wk $1.4k, O7 0.8/wk $0.6k, P7 only 0.4/wk $1.2k (the P7 state cut at about -42 already leaves almost nothing at -54 or worse). Stack total 24.5 full stops/week, $40.1k/week, against a stack net of $19.8k/week. Frozen week: 3 full stops (K7 2, M7 1), $4.4k; P7 had none but 3 give-backs worth $13.0k (that is the near-zone program).
- No rule in families a-g meets the full order acceptance (full stops -50% in count and $ on L6M, recoveries lost <= stops saved in $ on L6M AND HOLD, net positive). The nearest is U7 Keltner-mid break exit: full stops 3.5 -> 1.0/wk and $10.8k -> $3.5k/wk, L6M balance +$28/wk, but HOLD balance -$556/wk, PRE -$2.1k/wk, X-prime -$1.6k/wk and the frozen week -$3.0k, so it is FAIL on the order HOLD clause (it goes to exact as EC_UKC). Rules that remove many full stops give back as much or more in recoveries (K7 flat cut at -30: saves $8.5k/wk of stops, loses $11.9k/wk of recoveries; P7 flat cut -30: saves $0.5k, loses $21k). The MAE table says why: from -40 a P7 or K7 trade still reaches the target 16-17% of the time against a fair-walk 25%, i.e. losers are somewhat persistent but nowhere near dead enough to pay the 1.2 pt cut slip and the lost target.
- Forward-only placebo (same fired trades, exit at a random later second before the live exit): 0 of 888 loss-side cells beat their placebo at p<0.05 on L6M, so no cut timing shows skill beyond "any later exit"; family null therefore not passed by any cell.
- What survives as small, consistent positives on all four windows (L6M/HOLD/PRE/X') with stack maxDD not worse: P7 scratch after MAE>=40 exit at breakeven for lots>=5 (fires 0.2/week, +$583/wk L6M; cannot reduce full stops, there are 0.4/week), U7 fresh recovery lock (MAE>=40, arm -20, exit -30; +$698/wk), M7 fresh flat -50, H7 partial 1/3 at -15, K7 geometry stop 55/target 60 (+$83/wk). Each is below the noise of the family (MDE) and is listed as a candidate, not a result.
- P7 45/60 geometry cell (the order first cell): with the live cut on it is +$37/wk (L6M), +$107 (HOLD), +$100 (PRE), +$49 (X'), stack maxDD cut +1.1/+1.8/+2.8/+0.8 % = positive on all four windows but worth almost nothing, because the live P7 cut exits near -42 before a 45 stop can act. Against hold-to-bracket (no cut) it is the quoted +$1,197/wk and +6.3% on L6M but negative on HOLD (-$540, -30%), X' (-$362, -12%). Table below.

## 1. Behavioural scorecard a-b of the live base (c-e need W-Q behavior_scorecard.py, ~21:30Z; not yet run on finalists)

fs = full stops (exit <= -90% of stop distance) per week and $/week; gb = give-back events (MFE >= 80% of target, closed below 50%); rt = round trips (closed <= breakeven after MFE >= 80%); net = base net $/wk.

| win | book | trades | fs_wk | fs_usd_wk | gb_wk | gb_usd_wk | rt_wk | rt_usd_wk | net_wk |
|--|--|--|--|--|--|--|--|--|--|
| L6M | ALL | 4472 | 24.5 | -40051.8 | 9.7 | -13427.6 | 9.0 | -14074.0 | 19783.9 |
| L6M | A7 | 345 | 3.9 | -4651.8 | 0.7 | -563.7 | 0.7 | -563.7 | 863.3 |
| L6M | H7 | 189 | 0.9 | -1392.8 | 0.7 | -493.0 | 0.5 | -599.3 | 2756.7 |
| L6M | K7 | 1639 | 13.1 | -18628.3 | 3.3 | -3261.7 | 3.2 | -3314.4 | 3407.0 |
| L6M | M7 | 942 | 2.0 | -2722.8 | 1.9 | -1830.7 | 1.9 | -1830.7 | -948.9 |
| L6M | O7 | 62 | 0.8 | -624.1 | 0.1 | 34.2 | 0.0 | -31.2 | 330.4 |
| L6M | P7 | 1017 | 0.4 | -1243.5 | 2.4 | -5492.8 | 2.0 | -5864.7 | 9636.5 |
| L6M | U7 | 278 | 3.5 | -10788.5 | 0.7 | -1819.8 | 0.7 | -1870.0 | 3738.8 |
| HOLD | ALL | 8136 | 23.0 | -37888.0 | 8.5 | -11758.4 | 7.8 | -12352.0 | 15622.6 |
| HOLD | A7 | 554 | 3.2 | -3742.0 | 0.5 | -427.9 | 0.5 | -427.9 | 763.6 |
| HOLD | H7 | 338 | 1.2 | -2049.6 | 0.5 | -405.8 | 0.4 | -501.0 | 729.4 |
| HOLD | K7 | 2934 | 12.1 | -17111.9 | 2.7 | -2646.0 | 2.7 | -2686.5 | 2173.7 |
| HOLD | M7 | 1764 | 1.9 | -2640.1 | 1.7 | -1612.3 | 1.7 | -1612.3 | -920.1 |
| HOLD | O7 | 136 | 0.7 | -573.3 | 0.2 | 132.8 | 0.0 | -28.8 | 679.2 |
| HOLD | P7 | 1899 | 0.4 | -1080.4 | 2.2 | -5241.0 | 2.0 | -5480.9 | 10003.7 |
| HOLD | U7 | 511 | 3.5 | -10690.8 | 0.6 | -1558.1 | 0.6 | -1614.5 | 2193.3 |
| PRE | ALL | 7801 | 16.9 | -28858.5 | 5.4 | -7261.7 | 4.8 | -7782.2 | 11882.2 |
| PRE | A7 | 353 | 1.4 | -1614.5 | 0.2 | -215.9 | 0.2 | -215.9 | 988.9 |
| PRE | H7 | 439 | 1.4 | -2764.7 | 0.3 | -373.8 | 0.3 | -422.2 | 1551.1 |
| PRE | K7 | 2711 | 8.6 | -12100.3 | 1.7 | -1392.1 | 1.5 | -1478.4 | 2828.5 |
| PRE | M7 | 1706 | 2.2 | -3116.5 | 1.0 | -926.5 | 1.0 | -929.7 | 564.4 |
| PRE | O7 | 205 | 0.6 | -472.6 | 0.2 | 46.2 | 0.1 | -44.1 | 654.3 |
| PRE | P7 | 1870 | 0.2 | -668.2 | 1.6 | -3494.2 | 1.4 | -3772.9 | 3696.0 |
| PRE | U7 | 517 | 2.5 | -8121.6 | 0.4 | -905.4 | 0.3 | -919.1 | 1599.0 |
| X' | ALL | 3029 | 17.5 | -28195.1 | 3.7 | -4826.2 | 3.0 | -5203.5 | 1342.3 |
| X' | A7 | 143 | 1.2 | -1430.4 | 0.2 | -180.5 | 0.2 | -182.9 | 288.0 |
| X' | H7 | 223 | 1.8 | -3725.4 | 0.4 | -710.1 | 0.4 | -710.1 | 318.5 |
| X' | K7 | 939 | 7.8 | -10826.9 | 1.0 | -909.1 | 0.8 | -996.7 | 153.2 |
| X' | M7 | 653 | 3.2 | -4408.7 | 0.8 | -749.5 | 0.7 | -760.4 | 111.2 |
| X' | O7 | 113 | 1.3 | -1021.2 | 0.2 | 38.9 | 0.0 | -35.6 | -125.8 |
| X' | P7 | 733 | 0.2 | -713.1 | 0.9 | -2060.2 | 0.7 | -2170.6 | -461.3 |
| X' | U7 | 225 | 2.0 | -6069.3 | 0.2 | -255.8 | 0.1 | -347.2 | 1058.5 |
| FROZEN | ALL | 187 | 3.0 | -4373.5 | 14.0 | -18745.4 | 12.0 | -19788.0 | 103595.9 |
| FROZEN | A7 | 23 | 0.0 | 0.0 | 3.0 | -528.5 | 2.0 | -1032.4 | -1442.1 |
| FROZEN | H7 | 3 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | -774.7 |
| FROZEN | K7 | 64 | 2.0 | -2757.4 | 6.0 | -3783.3 | 5.0 | -4322.1 | 15975.3 |
| FROZEN | M7 | 28 | 1.0 | -1616.2 | 2.0 | -1467.4 | 2.0 | -1467.4 | 5971.3 |
| FROZEN | O7 | 3 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 656.5 |
| FROZEN | P7 | 53 | 0.0 | 0.0 | 3.0 | -12966.2 | 3.0 | -12966.2 | 85718.5 |
| FROZEN | U7 | 6 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | -1777.4 |

## 2. P7 geometry (order first cell), four windows, first-order delta $/wk vs live and stack maxDD cut %

| mode | cell | dmean_L1M | dmean_L3M | dmean_L6M | dmean_HOLD | dmean_PRE | dmean_X' | cut_L6M | cut_HOLD | cut_PRE | cut_X' |
|--|--|--|--|--|--|--|--|--|--|--|--|
| BASE(live cut on) | 40/60 fixed | -52.8 | 93.0 | 738.6 | -35.0 | -130.6 | -175.3 | 3.3 | 2.9 | 14.5 | -9.5 |
| BASE(live cut on) | 45/60 fixed | -84.3 | -7.3 | 36.8 | 107.4 | 99.8 | 49.4 | 1.1 | 1.8 | 2.8 | 0.8 |
| BASE(live cut on) | 50/60 fixed | 0.0 | -11.0 | -20.4 | -20.8 | 9.1 | 30.5 | 0.3 | 0.7 | 0.7 | 0.3 |
| BASE(live cut on) | 55/60 fixed | 0.0 | -0.6 | 0.1 | -5.4 | 11.4 | 10.9 | -0.0 | -0.3 | 0.3 | -0.0 |
| BASE(live cut on) | 45/45 fixed | 625.6 | -2870.3 | -2387.2 | -1546.9 | -427.3 | -471.0 | 30.7 | 8.7 | 3.6 | 33.0 |
| BASE(live cut on) | 45/50 fixed | -4228.9 | -3923.1 | -2103.4 | -1236.6 | 328.3 | -485.8 | 22.1 | -10.7 | 15.0 | 8.0 |
| RAW(vs hold-to-bracket, no state cut) | 40/60 fixed | 882.7 | 2639.3 | 4109.4 | 1473.8 | -141.6 | -1093.9 | 22.5 | -11.3 | -45.3 | -47.3 |
| RAW(vs hold-to-bracket, no state cut) | 45/60 fixed | -2014.7 | 394.0 | 1196.6 | -540.2 | 240.4 | -362.3 | 6.3 | -30.3 | -27.1 | -11.9 |
| RAW(vs hold-to-bracket, no state cut) | 50/60 fixed | -1606.7 | 1755.0 | 1437.4 | -261.2 | 254.9 | 482.2 | 15.8 | -30.4 | -11.9 | -13.7 |
| RAW(vs hold-to-bracket, no state cut) | 55/60 fixed | 3990.7 | 1655.7 | 2090.2 | 1625.2 | -226.6 | 77.7 | 2.6 | 4.6 | -5.4 | -18.2 |
| RAW(vs hold-to-bracket, no state cut) | 45/45 fixed | 14149.3 | 3940.3 | 2787.8 | 136.2 | 610.3 | -1673.0 | -0.2 | -49.7 | -15.4 | -20.2 |
| RAW(vs hold-to-bracket, no state cut) | 45/50 fixed | 17221.3 | 2071.3 | 2323.4 | -310.3 | 966.1 | -1505.2 | -6.0 | -36.5 | -18.2 | -25.5 |

BASE = rule acts only before the live exit (live P7 40/5x/p3 cut stays on); RAW = delta vs hold-to-bracket, added to the live base (overstates, no state cut underneath). eq$ (equal-$-risk lots = lots x 60/stop) rows are in code/th_ec output p7geom.parquet: they raise mean by adding lots and worsen maxDD (L6M cut -13%), so they are leverage, not a result.

## 3. Best cell per family and book (mask ALL, plus best masked), L6M / HOLD / PRE / X' net $/wk and stack maxDD cut

Selection here = best L6M net among cells with stack maxDD cut >= 0 on L6M and HOLD (display only; ranking at risk of selection, see null). a=thesis/structure, b=geometry (fixed lots), c=no-follow-through/back-to-entry, d=scratch/recovery lock, e=partial cut.

| book | fam | mask | cell | fire_wk | fs_red | saved_usd | recov_usd | L6M | HOLD | PRE | Xp | cut_L6M | cut_HOLD |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| P7 | a | reentry | a-vwap buf0 exit-on-break | 2.65 | 0.10 | 37.69 | -2097.33 | 1021.69 | 115.20 | 298.46 | -186.76 | 17.29 | 8.10 |
| P7 | b | reentry | b-geom stop25 tgt45 fixed | 8.42 | -12.20 | -8160.74 | -6089.65 | 1197.64 | -985.96 | 643.82 | -288.36 | 16.71 | 4.51 |
| P7 | c | chasing | c-back0 after MFE>=40 | 4.11 | 0.40 | 444.62 | -6282.52 | 1825.87 | 276.23 | -1267.53 | -196.88 | 23.88 | 6.33 |
| P7 | d | lots>=5 | d-rlock MAE>=35 arm -20 exit -30 | 1.14 | 0.00 | 0.00 | -508.94 | 1152.34 | 338.15 | -171.78 | -290.58 | 6.11 | 4.74 |
| P7 | e | lots>=5 | e-partial F=0.33 at -30 noadd | 4.84 | 0.00 | 0.00 | -1932.90 | -274.44 | -353.92 | -672.77 | -80.98 | 0.58 | 2.62 |
| K7 | a | reentry | a-vwap buf0 stop+eq$lots | 4.15 | 0.17 | 3213.75 | -1644.35 | 334.44 | 338.90 | -640.93 | -173.61 | 8.17 | 0.52 |
| K7 | b | reentry | b-geom stop25 tgt50 fixed | 18.52 | -0.66 | -1903.27 | -5049.16 | 659.85 | 632.92 | -529.14 | -86.07 | 14.11 | 9.65 |
| K7 | c | reentry | c-nft X=20 N=20 full | 8.71 | 0.18 | 2707.17 | -3932.92 | 627.78 | 733.41 | -860.61 | -98.73 | 0.53 | 1.74 |
| K7 | d | reentry | d-scratch MAE>=25 exit -0 | 5.41 | 0.10 | 1979.76 | -2715.61 | 802.19 | 485.73 | 24.13 | -20.22 | 8.32 | 1.20 |
| K7 | e | reentry | e-partial F=0.50 at -25 noadd | 1.42 | 0.05 | 421.26 | -486.36 | 81.66 | 114.15 | -89.13 | -18.55 | 0.98 | 0.58 |
| M7 | a | chasing | a-vwap buf4 stop+eq$lots | 1.95 | 0.23 | 814.67 | -725.34 | 362.51 | 155.12 | -1165.91 | -585.58 | 0.34 | 2.39 |
| M7 | b | chasing | b-geom stop45 tgt50 fixed | 14.12 | -0.79 | -1165.74 | -2374.83 | 613.42 | 221.50 | -465.25 | -34.19 | 4.97 | 2.68 |
| M7 | c | chasing | c-back0 after MFE>=40 | 4.15 | 0.15 | 420.20 | -1964.52 | 564.46 | 153.50 | -718.91 | 115.25 | 3.14 | 2.58 |
| M7 | d | reentry | d-scratch MAE>=30 exit -5 | 0.69 | 0.02 | 45.32 | -163.38 | 286.78 | 256.03 | -100.22 | 77.09 | 0.67 | 0.75 |
| M7 | e | reentry | e-partial F=0.50 at -25 noadd | 0.53 | 0.00 | 0.00 | 0.00 | 114.97 | 93.20 | -68.59 | 23.40 | 0.35 | 0.23 |
| U7 | a | ALL | a-kc buf2 stop+eq$lots | 4.40 | 0.74 | 8764.52 | -4211.32 | 1221.87 | 811.28 | -2798.07 | -2258.23 | 17.74 | 2.26 |
| U7 | b | reentry | b-geom stop50 tgt45 fixed | 0.37 | 0.00 | 45.87 | -170.73 | 20.06 | -22.60 | 84.16 | 6.61 | 2.45 | 0.45 |
| U7 | c | fresh | c-nft X=5 N=15 half | 1.47 | 0.27 | 1086.49 | -569.77 | 632.39 | 486.82 | -135.93 | -243.40 | 0.70 | 0.13 |
| U7 | d | fresh | d-rlock MAE>=40 arm -20 exit -30 | 0.73 | 0.14 | 784.57 | -137.54 | 697.82 | 796.19 | 56.09 | 298.33 | 0.00 | 1.33 |
| U7 | e | reentry | e-partial F=0.67 at -35 readd | 0.16 | 0.02 | 58.12 | -20.57 | 42.29 | 33.70 | -35.61 | 10.26 | 0.62 | 0.89 |
| H7 | a | fresh | a-kc buf0 stop+eq$lots | 0.57 | 0.14 | 205.87 | -306.13 | 373.10 | 124.01 | -214.47 | -843.34 | 3.52 | 1.17 |
| H7 | b | fresh | b-geom stop30 tgt50 fixed | 1.02 | -0.18 | 35.41 | -143.68 | 623.37 | 181.59 | -130.11 | -346.23 | 3.96 | 0.43 |
| H7 | c | fresh | c-nft X=20 N=10 full | 0.61 | 0.14 | 186.86 | -356.55 | 183.81 | 225.20 | -481.82 | -519.62 | 5.05 | 2.79 |
| H7 | d | fresh | d-rlock MAE>=25 arm -20 exit -25 | 0.37 | 0.14 | 99.97 | -78.67 | 83.96 | -101.57 | -160.09 | -174.51 | 2.84 | 0.63 |
| H7 | e | fresh | e-partial F=0.33 at -15 noadd | 0.08 | 0.00 | 0.00 | 0.00 | 19.37 | 60.47 | 14.03 | -15.67 | 0.00 | 0.00 |
| A7 | a | chasing | a-fr1 buf6 stop+eq$lots | 3.95 | -0.18 | -884.40 | -1436.12 | 937.63 | 495.40 | -57.90 | 160.08 | 2.56 | 1.14 |
| A7 | b | reentry | b-geom stop35 tgt60 fixed | 0.65 | -0.07 | -44.24 | -78.47 | 98.37 | -9.96 | -40.05 | 0.00 | 1.08 | 0.00 |
| A7 | c | reentry | c-flat d=35 | 0.65 | 0.09 | 154.85 | -79.01 | 86.12 | -19.62 | -41.15 | 0.00 | 0.94 | 0.00 |
| A7 | d | reentry | d-rlock MAE>=30 arm -10 exit -15 | 0.28 | 0.03 | 104.92 | 0.00 | 167.98 | 38.12 | -18.84 | 0.00 | 1.55 | 0.00 |
| O7 | a | lots<5 | a-vwap buf0 exit-on-break | 0.24 | 0.20 | 88.05 | 0.00 | 119.14 | -88.74 | -27.76 | -5.27 | 0.00 | 0.00 |
| O7 | b | fresh | b-geom stop35 tgt60 fixed | 0.12 | 0.05 | 35.37 | -24.42 | -21.00 | -14.28 | -27.82 | 8.74 | 0.00 | 0.00 |
| O7 | c | chasing | c-nft X=20 N=10 full | 0.20 | 0.10 | 37.16 | 0.00 | 118.69 | 11.53 | -374.01 | 41.30 | 1.19 | 0.00 |
| O7 | d | chasing | d-rlock MAE>=30 arm -10 exit -15 | 0.16 | 0.10 | 41.63 | 0.00 | 59.56 | -30.68 | 18.59 | 27.12 | 0.00 | 0.00 |

## 4. Placebo and family null (loss-side non-geometry, ALL masks)

| book | cells | own05_L6M | own05_HOLD | fam05_L6M | min_p_own_L6M |
|--|--|--|--|--|--|
| A7 | 98 | 0 | 0 | 0 | 0.731 |
| H7 | 148 | 0 | 0 | 0 | 0.701 |
| K7 | 138 | 0 | 0 | 0 | 0.612 |
| M7 | 138 | 0 | 0 | 0 | 0.289 |
| O7 | 78 | 0 | 0 | 0 | 0.060 |
| P7 | 140 | 0 | 0 | 0 | 0.463 |
| U7 | 148 | 0 | 0 | 0 | 0.085 |

Placebo = same fired trades, exit at a uniformly random later second before the live exit (forward only), B=200; own p = P(placebo net >= cell net). Geometry cells have no fire-time placebo (they are brackets); they are judged on the four windows and the exact runs.

## 5. Finalists (first-order, preregistered pick rule) and acceptance trader test

Pick rule (frozen before looking at the list): per book (A) best non-geometry loss-side cell with fire >= 0.1/wk, net > 0 on all four windows and stack maxDD cut >= 0 on L6M and HOLD; (B) best cell meeting the order arithmetic (-50% count and $ of full stops, recoveries lost <= saved on L6M and HOLD) with net > 0 L6M+HOLD and maxDD not worse; (C) best fixed-lot geometry cell with four positive windows. 30 largest losers listing: DS3_EARLY_CUT_ACCEPT.md (L6M and frozen week for every finalist).

| book | cell | mask | fs_before_wk | fs_usd_before_wk | fs_after_wk | fs_usd_after_wk | stops_saved_usd_wk | recov_lost_usd_wk | bal_L6M | bal_HOLD | net_L6M | net_HOLD | net_PRE | net_Xp | frozen_net | ACCEPT |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| P7 | d-scratch MAE>=40 exit -0 | lots>=5 | 0.4 | 1243.5 | 0.4 | 1243.5 | 0.0 | 338.0 | -338.0 | -349.4 | 583.5 | 346.0 | 174.2 | 49.1 | -1281.0 | FAIL |
| P7 | c-back0 after MFE>=40 | chasing | 0.4 | 1243.5 | 0.2 | 787.2 | 444.6 | 6282.5 | -5837.9 | -7025.9 | 1825.9 | 276.2 | -1267.5 | -196.9 | -12632.5 | FAIL |
| K7 | a-st buf0 stop+eq$lots | chasing | 13.1 | 18628.3 | 12.7 | 17998.4 | 10581.8 | 1460.5 | 9119.3 | 7104.4 | 174.6 | 58.9 | -495.3 | -740.5 | 0.0 | FAIL |
| K7 | c-back0 after MFE>=10 | reentry | 13.1 | 18628.3 | 10.5 | 15162.7 | 3289.5 | 6784.2 | -3494.8 | -2643.8 | 146.6 | 99.8 | -940.2 | -193.3 | 898.0 | FAIL |
| K7 | b-geom stop55 tgt60 fixed | ALL | 13.1 | 18628.3 | 14.5 | 19376.2 | 1895.8 | 568.5 | 1327.4 | 1453.6 | 82.6 | 31.7 | 67.2 | 218.4 | 499.0 | FAIL |
| M7 | c-flat d=50 | fresh | 2.0 | 2722.8 | 1.8 | 2463.3 | 37.0 | -0.0 | 37.0 | 32.5 | 15.7 | 7.2 | 36.1 | 27.7 | 0.0 | FAIL |
| M7 | c-nft X=5 N=5 full | ALL | 2.0 | 2722.8 | 0.8 | 1048.9 | 1324.3 | 8304.6 | -6980.3 | -6950.6 | 408.9 | 237.5 | -1347.4 | -508.3 | -6022.5 | FAIL |
| U7 | d-rlock MAE>=40 arm -20 exit -30 | fresh | 3.5 | 10788.5 | 3.0 | 9267.2 | 784.6 | 137.5 | 647.0 | 714.3 | 697.8 | 796.2 | 56.1 | 298.3 | 0.0 | FAIL |
| U7 | a-kc buf2 stop+eq$lots | ALL | 3.5 | 10788.5 | 1.9 | 6143.6 | 8764.5 | 4202.1 | 4553.2 | 3757.8 | 1221.9 | 811.3 | -2798.1 | -2258.2 | -5815.0 | FAIL |
| U7 | a-kc buf2 exit-on-break | ALL | 3.5 | 10788.5 | 1.0 | 3462.8 | 3952.9 | 3924.6 | 28.3 | -556.1 | 724.3 | 397.7 | -2128.7 | -1558.8 | -2953.0 | FAIL |
| H7 | e-partial F=0.33 at -15 noadd | ALL | 0.9 | 1392.8 | 0.9 | 1358.9 | 33.9 | 80.9 | -47.0 | 7.0 | 15.5 | 95.4 | 20.5 | 96.5 | 0.0 | FAIL |
| H7 | a-fr1 buf6 exit-on-break | fresh | 0.9 | 1392.8 | 0.8 | 1198.9 | 146.7 | 203.3 | -56.7 | 26.2 | 49.3 | 170.8 | 78.6 | -310.1 | 0.0 | FAIL |
| A7 | d-rlock MAE>=30 arm -10 exit -15 | reentry | 3.9 | 4651.8 | 3.8 | 4506.0 | 104.9 | -0.0 | 104.9 | 7.6 | 168.0 | 38.1 | -18.8 | 0.0 | -1549.0 | FAIL |
| O7 | c-nft X=20 N=10 full | ALL | 0.8 | 624.1 | 0.7 | 562.7 | 37.2 | -0.0 | 37.2 | -66.0 | 118.7 | 11.5 | -410.4 | 28.3 | 533.5 | FAIL |

- P7 [d-scratch MAE>=40 exit -0, lots>=5]: full stops were 0.4/week costing $1244; now 0.4/week costing $1244; it saved $0/week on the stops it touched and gave up $338/week of recoveries (cut trades that were Targets under live rules). Net +583 $/wk L6M. Acceptance FAIL.
- P7 [c-back0 after MFE>=40, chasing]: full stops were 0.4/week costing $1244; now 0.2/week costing $787; it saved $445/week on the stops it touched and gave up $6283/week of recoveries (cut trades that were Targets under live rules). Net +1826 $/wk L6M. Acceptance FAIL.
- K7 [a-st buf0 stop+eq$lots, chasing]: full stops were 13.1/week costing $18628; now 12.7/week costing $17998; it saved $10582/week on the stops it touched and gave up $1460/week of recoveries (cut trades that were Targets under live rules). Net +175 $/wk L6M. Acceptance FAIL.
- K7 [c-back0 after MFE>=10, reentry]: full stops were 13.1/week costing $18628; now 10.5/week costing $15163; it saved $3289/week on the stops it touched and gave up $6784/week of recoveries (cut trades that were Targets under live rules). Net +147 $/wk L6M. Acceptance FAIL.
- K7 [b-geom stop55 tgt60 fixed, ALL]: full stops were 13.1/week costing $18628; now 14.5/week costing $19376; it saved $1896/week on the stops it touched and gave up $568/week of recoveries (cut trades that were Targets under live rules). Net +83 $/wk L6M. Acceptance FAIL.
- M7 [c-flat d=50, fresh]: full stops were 2.0/week costing $2723; now 1.8/week costing $2463; it saved $37/week on the stops it touched and gave up $-0/week of recoveries (cut trades that were Targets under live rules). Net +16 $/wk L6M. Acceptance FAIL.
- M7 [c-nft X=5 N=5 full, ALL]: full stops were 2.0/week costing $2723; now 0.8/week costing $1049; it saved $1324/week on the stops it touched and gave up $8305/week of recoveries (cut trades that were Targets under live rules). Net +409 $/wk L6M. Acceptance FAIL.
- U7 [d-rlock MAE>=40 arm -20 exit -30, fresh]: full stops were 3.5/week costing $10789; now 3.0/week costing $9267; it saved $785/week on the stops it touched and gave up $138/week of recoveries (cut trades that were Targets under live rules). Net +698 $/wk L6M. Acceptance FAIL.
- U7 [a-kc buf2 stop+eq$lots, ALL]: full stops were 3.5/week costing $10789; now 1.9/week costing $6144; it saved $8765/week on the stops it touched and gave up $4202/week of recoveries (cut trades that were Targets under live rules). Net +1222 $/wk L6M. Acceptance FAIL.
- U7 [a-kc buf2 exit-on-break, ALL]: full stops were 3.5/week costing $10789; now 1.0/week costing $3463; it saved $3953/week on the stops it touched and gave up $3925/week of recoveries (cut trades that were Targets under live rules). Net +724 $/wk L6M. Acceptance FAIL.
- H7 [e-partial F=0.33 at -15 noadd, ALL]: full stops were 0.9/week costing $1393; now 0.9/week costing $1359; it saved $34/week on the stops it touched and gave up $81/week of recoveries (cut trades that were Targets under live rules). Net +16 $/wk L6M. Acceptance FAIL.
- H7 [a-fr1 buf6 exit-on-break, fresh]: full stops were 0.9/week costing $1393; now 0.8/week costing $1199; it saved $147/week on the stops it touched and gave up $203/week of recoveries (cut trades that were Targets under live rules). Net +49 $/wk L6M. Acceptance FAIL.
- A7 [d-rlock MAE>=30 arm -10 exit -15, reentry]: full stops were 3.9/week costing $4652; now 3.8/week costing $4506; it saved $105/week on the stops it touched and gave up $-0/week of recoveries (cut trades that were Targets under live rules). Net +168 $/wk L6M. Acceptance FAIL.
- O7 [c-nft X=20 N=10 full, ALL]: full stops were 0.8/week costing $624; now 0.7/week costing $563; it saved $37/week on the stops it touched and gave up $-0/week of recoveries (cut trades that were Targets under live rules). Net +119 $/wk L6M. Acceptance FAIL.

Per-book deliverable status (policy grammar + v1.8 fields): see section 7. Because no finalist PASSes, the table above is the "best setting always delivered" row, not an install recommendation.

## 6. Exact promotion (fork, private driver ec_hooks.py)

Sets EC_ID, EC_G45/G40/G50/G55 (P7 stop x tgt 60), EC_S40 (P7 scratch), EC_RL (P7 recovery lock), EC_K55, EC_UKC / EC_UKCS (U7 Keltner-mid break / structure stop eq$ lots), EC_P3S (P7 3-min fractal structure stop eq$), EC_NFT_M7, EC_FLAT45 (P7), EC_FLAT45K (K7) written; 560 one-set-per-job lines queued by month in /mnt/l2/l2vast/_early_cut/ec_jobs.txt; nohup chain pid 2098554 / driver 2098556 (autopilot/DS3_EARLY_CUT_PIDS.txt) launches only when MemAvail >= 62 GB (MemAvail was ~29 GB at the last check, so the identity test EC_ID vs LPB_BASE 202610 has NOT run yet; the hook is untested on the engine). Fill model: market cuts at mid(row+1) -/+ 0.80 (engine continuity; live is 1.19-1.20 so cut savings overstate by ~0.4 pt = ~$8 per lot per cut), structure-stop exits at level -1.4 pt (live native central), geometry uses the engine bracket (native stop fills ~1.9 pt better than level, live is 1.4 adverse: geometry gains overstate by ~3 pt per stop). Exact rows: present.

| set | win | months | wks | mean | dd | cut | dmean | w20cut | fs_wk | fs_usd_wk | fs_ref_wk | fs_usd_ref_wk | fires_wk | recov_lost_n_wk | recov_lost_usd_wk | stops_saved_n_wk | stops_saved_usd_wk | other_cut_usd_wk | net_usd_wk | ntr | ntr_ref |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| EC_FLAT45 | L1M | 14 | 2.9 | -16216.5 | 51252.7 | 0.0 | -36.7 | -29.5 | 28.4 | -47271.9 | 28.4 | -47271.9 | 1.0 | 0.0 | 0.0 | 0.0 | 0.0 | -140.9 | -140.9 | 568 | 568 |
| EC_FLAT45 | L3M | 14 | 11.4 | 14837.4 | 76598.7 | 0.8 | -87.9 | -0.2 | 23.4 | -38971.0 | 23.4 | -38976.3 | 1.2 | 0.0 | 0.0 | 0.2 | 5.3 | -37.2 | -31.9 | 1875 | 1875 |
| EC_FLAT45 | L6M | 14 | 24.6 | 17431.7 | 76598.7 | 0.8 | 78.4 | 2.5 | 24.5 | -39869.3 | 24.5 | -40051.8 | 1.8 | 0.0 | 0.0 | 0.1 | 31.8 | 53.3 | 111.7 | 4472 | 4472 |
| EC_FLAT45 | HOLD | 14 | 50.7 | 16756.9 | 79782.0 | -1.2 | 79.5 | 0.5 | 22.9 | -37824.0 | 23.0 | -37888.0 | 1.6 | 0.0 | 0.0 | 0.1 | 23.6 | 24.9 | 61.4 | 8136 | 8136 |
| EC_FLAT45K | L1M | 14 | 2.9 | 18608.4 | 48568.8 | 5.2 | 1069.8 | 432.4 | 17.8 | -33397.9 | 28.4 | -47271.9 | 23.1 | 0.4 | -737.1 | 9.4 | 3030.5 | -598.0 | 2062.7 | 592 | 568 |
| EC_FLAT45K | L3M | 14 | 11.4 | 8966.7 | 79019.9 | -2.3 | 778.5 | -2.8 | 12.8 | -23301.6 | 23.4 | -38976.3 | 21.5 | 1.0 | -2429.0 | 10.0 | 3315.5 | -1095.3 | -378.4 | 1929 | 1875 |
| EC_FLAT45K | L6M | 14 | 24.6 | 19051.8 | 79019.9 | -2.3 | 1894.2 | 38.1 | 12.8 | -23274.3 | 24.5 | -40051.8 | 23.4 | 0.9 | -2432.0 | 11.4 | 3550.0 | -836.8 | 1371.1 | 4636 | 4472 |
| EC_FLAT45K | HOLD | 14 | 50.7 | 15992.1 | 83267.6 | -5.6 | 817.6 | 12.1 | 11.9 | -22153.6 | 23.0 | -37888.0 | 21.4 | 0.9 | -2396.4 | 10.4 | 3214.0 | -685.0 | 1168.5 | 8443 | 8136 |
| EC_G40 | L1M | 14 | 2.9 | -14684.2 | 54251.6 | -5.9 | 1495.6 | 2024.7 | 49.4 | -115589.9 | 28.4 | -47271.9 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 9658.7 | 582 | 568 |
| EC_G40 | L3M | 14 | 11.4 | 8718.9 | 63987.2 | 17.1 | -75.6 | 14.3 | 39.9 | -90843.0 | 23.4 | -38976.3 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 1942.7 | 1928 | 1875 |
| EC_G40 | L6M | 14 | 24.6 | 18618.2 | 63987.2 | 17.1 | 1264.9 | -7.2 | 41.9 | -94674.4 | 24.5 | -40051.8 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 148.7 | 4545 | 4472 |
| EC_G40 | HOLD | 14 | 50.7 | 14899.8 | 98186.1 | -24.5 | -274.7 | -16.6 | 38.4 | -86057.5 | 23.0 | -37888.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | -849.7 | 8227 | 8136 |
| EC_G45 | L1M | 15 | 2.9 | 1545.4 | 51235.7 | 0.0 | 1995.4 | 1242.6 | 43.8 | -102083.9 | 28.4 | -47271.9 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 5927.7 | 560 | 568 |
| EC_G45 | L3M | 15 | 11.4 | 13983.6 | 72985.7 | 5.5 | 1256.6 | 16.7 | 39.0 | -89334.9 | 23.4 | -38976.3 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 2277.6 | 1870 | 1875 |
| EC_G45 | L6M | 15 | 24.6 | 18636.9 | 72985.7 | 5.5 | 1556.1 | 15.8 | 40.6 | -92370.7 | 24.5 | -40051.8 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 678.3 | 4441 | 4472 |
| EC_G45 | HOLD | 15 | 50.7 | 15142.6 | 77153.7 | 2.1 | 766.3 | 6.5 | 37.8 | -84826.2 | 23.0 | -37888.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 332.1 | 8117 | 8136 |
| EC_G50 | L1M | 14 | 2.9 | -16058.5 | 51252.7 | 0.0 | 121.3 | -26.4 | 32.9 | -62506.6 | 28.4 | -47271.9 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | -125.9 | 571 | 568 |
| EC_G50 | L3M | 14 | 11.4 | 16692.4 | 76423.2 | 1.0 | -9.3 | 0.6 | 25.7 | -46865.8 | 23.4 | -38976.3 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 83.0 | 1880 | 1875 |
| EC_G50 | L6M | 14 | 24.6 | 17442.3 | 76423.2 | 1.0 | 89.0 | 3.5 | 27.8 | -51774.2 | 24.5 | -40051.8 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | -193.0 | 4475 | 4472 |
| EC_G50 | HOLD | 14 | 50.7 | 14575.1 | 76423.2 | 3.1 | 65.2 | 2.2 | 25.6 | -46869.9 | 23.0 | -37888.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | -71.9 | 8150 | 8136 |
| EC_G55 | L1M | 14 | 2.9 | -450.1 | 51252.7 | 0.0 | 0.0 | 13.2 | 28.4 | -47208.9 | 28.4 | -47271.9 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 63.0 | 568 | 568 |
| EC_G55 | L3M | 14 | 11.4 | 11068.7 | 78090.2 | -1.1 | -54.5 | -0.7 | 23.8 | -40351.5 | 23.4 | -38976.3 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | -101.7 | 1875 | 1875 |
| EC_G55 | L6M | 14 | 24.6 | 17094.2 | 78090.2 | -1.1 | 13.5 | 0.2 | 25.2 | -42534.7 | 24.5 | -40051.8 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | -140.1 | 4472 | 4472 |
| EC_G55 | HOLD | 14 | 50.7 | 14470.6 | 78090.2 | 1.0 | 94.3 | 1.0 | 23.5 | -39923.1 | 23.0 | -37888.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 20.3 | 8144 | 8136 |
| EC_ID | L1M | 1 | 2.9 | -16179.8 | 51252.7 | 0.0 | 0.0 | 0.0 | 28.4 | -47271.9 | 28.4 | -47271.9 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 568 | 568 |
| EC_K55 | L1M | 14 | 2.9 | -17047.2 | 52825.0 | -3.1 | -867.4 | -31.4 | 30.8 | -48825.6 | 28.4 | -47271.9 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | -149.7 | 575 | 568 |
| EC_K55 | L3M | 14 | 11.4 | 8347.9 | 75792.7 | 1.9 | 159.7 | -4.4 | 25.8 | -40749.9 | 23.4 | -38976.3 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | -603.5 | 1886 | 1875 |
| EC_K55 | L6M | 14 | 24.6 | 16801.5 | 75792.7 | 1.9 | 310.2 | 18.7 | 27.6 | -42588.5 | 24.5 | -40051.8 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | -344.4 | 4525 | 4472 |
| EC_K55 | HOLD | 14 | 50.7 | 14207.2 | 85624.4 | -8.6 | 119.9 | 1.8 | 25.7 | -39936.2 | 23.0 | -37888.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | -199.2 | 8212 | 8136 |
| EC_NFT_M7 | L1M | 14 | 2.9 | 19977.8 | 56041.3 | -9.3 | 2439.2 | 185.6 | 25.9 | -44433.3 | 28.4 | -47271.9 | 29.0 | 3.5 | -5415.2 | 2.4 | 2187.5 | 7360.5 | 885.2 | 611 | 568 |
| EC_NFT_M7 | L3M | 14 | 11.4 | 14201.8 | 71495.2 | 7.4 | -723.5 | -0.5 | 22.3 | -37592.0 | 23.4 | -38976.3 | 30.7 | 4.7 | -7724.6 | 1.0 | 1039.4 | 7776.3 | -61.4 | 2097 | 1875 |
| EC_NFT_M7 | L6M | 14 | 24.6 | 17522.4 | 71495.2 | 7.4 | -972.8 | -17.3 | 23.8 | -39046.5 | 24.5 | -40051.8 | 29.1 | 4.9 | -8043.9 | 1.0 | 1180.4 | 7215.5 | -1364.9 | 4894 | 4472 |
| EC_NFT_M7 | HOLD | 14 | 50.7 | 14171.1 | 73931.4 | 6.2 | -391.0 | 2.1 | 22.2 | -36882.1 | 23.0 | -37888.0 | 30.0 | 4.7 | -7571.5 | 1.1 | 1251.9 | 6802.1 | -640.8 | 9095 | 8136 |
| EC_P3S | L1M | 14 | 2.9 | -3935.9 | 50865.3 | 0.8 | -3485.9 | 2411.3 | 28.0 | -45684.7 | 28.4 | -47271.9 | 5.2 | 0.4 | -2810.6 | 0.0 | 0.0 | -5424.2 | 11503.0 | 549 | 568 |
| EC_P3S | L3M | 14 | 11.4 | 11149.3 | 50865.3 | 34.1 | -1577.7 | 15.7 | 23.3 | -38821.1 | 23.4 | -38976.3 | 7.4 | 1.0 | -8134.9 | 0.2 | 64.7 | -5874.9 | 2134.2 | 1807 | 1875 |
| EC_P3S | L6M | 14 | 24.6 | 14529.0 | 50865.3 | 34.1 | -4807.2 | -45.0 | 24.4 | -39645.6 | 24.5 | -40051.8 | 7.0 | 0.9 | -7407.8 | 0.1 | 30.1 | -5594.7 | -3127.9 | 4324 | 4472 |
| EC_P3S | HOLD | 14 | 50.7 | 13975.4 | 78731.8 | 0.1 | -1139.5 | -17.1 | 22.8 | -37484.3 | 23.0 | -37888.0 | 7.3 | 0.8 | -7274.7 | 0.0 | 14.6 | -5461.1 | -2171.9 | 7826 | 8136 |
| EC_RL | L1M | 14 | 2.9 | -984.5 | 55894.5 | -9.1 | -534.5 | -539.6 | 28.4 | -47271.9 | 28.4 | -47271.9 | 1.4 | 0.7 | -1701.2 | 0.0 | 0.0 | 925.8 | -2574.2 | 573 | 568 |
| EC_RL | L3M | 14 | 11.4 | 12608.0 | 77559.1 | -0.4 | -119.0 | -4.6 | 23.4 | -38976.3 | 23.4 | -38976.3 | 0.5 | 0.2 | -425.3 | 0.0 | 0.0 | 490.0 | -628.2 | 1883 | 1875 |
| EC_RL | L6M | 14 | 24.6 | 18964.8 | 77559.1 | -0.4 | -120.1 | -12.6 | 24.5 | -40051.8 | 24.5 | -40051.8 | 0.6 | 0.1 | -323.0 | 0.0 | 0.0 | 806.4 | -478.0 | 4495 | 4472 |
| EC_RL | HOLD | 14 | 50.7 | 15253.9 | 77559.1 | 1.6 | 79.4 | -1.7 | 23.0 | -37888.0 | 23.0 | -37888.0 | 0.7 | 0.1 | -413.6 | 0.0 | 0.0 | 773.5 | -132.8 | 8167 | 8136 |
| EC_S40 | L1M | 14 | 2.9 | -16179.8 | 51252.7 | 0.0 | 0.0 | 0.0 | 28.4 | -47271.9 | 28.4 | -47271.9 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 568 | 568 |
| EC_S40 | L3M | 14 | 11.4 | 11123.2 | 77224.2 | 0.0 | 0.0 | 0.0 | 23.4 | -38976.3 | 23.4 | -38976.3 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 1875 | 1875 |
| EC_S40 | L6M | 14 | 24.6 | 17838.0 | 77224.2 | 0.0 | 0.0 | 0.0 | 24.5 | -40051.8 | 24.5 | -40051.8 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 4472 | 4472 |
| EC_S40 | HOLD | 14 | 50.7 | 14680.2 | 78842.0 | 0.0 | 0.0 | 0.0 | 23.0 | -37888.0 | 23.0 | -37888.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 8136 | 8136 |
| EC_UKC | L1M | 14 | 2.9 | 1943.1 | 46520.7 | 9.2 | 2393.2 | 876.4 | 24.8 | -35156.9 | 28.4 | -47271.9 | 4.6 | 0.7 | -2968.3 | 3.5 | 6738.7 | 410.6 | 4180.9 | 568 | 568 |
| EC_UKC | L3M | 14 | 11.4 | 17663.4 | 63414.2 | 17.9 | 961.7 | 14.7 | 20.6 | -30324.4 | 23.4 | -38976.3 | 5.3 | 1.1 | -3732.3 | 2.8 | 5098.9 | 693.4 | 1997.7 | 1878 | 1875 |
| EC_UKC | L6M | 14 | 24.6 | 19535.6 | 63414.2 | 17.9 | 359.0 | 25.3 | 22.2 | -33013.0 | 24.5 | -40051.8 | 4.5 | 1.0 | -3541.9 | 2.4 | 3814.5 | 656.9 | 846.6 | 4476 | 4472 |
| EC_UKC | HOLD | 14 | 50.7 | 16325.5 | 74477.1 | 5.5 | 973.4 | 12.9 | 20.6 | -30693.6 | 23.0 | -37888.0 | 5.6 | 1.4 | -4625.1 | 2.6 | 4445.2 | 923.3 | 659.7 | 8182 | 8136 |
| EC_UKCS | L1M | 14 | 2.9 | 866.3 | 49607.6 | 3.2 | 1316.3 | 636.5 | 24.8 | -35156.9 | 28.4 | -47271.9 | 4.6 | 0.7 | -2993.0 | 3.5 | 5158.3 | 453.2 | 3036.4 | 568 | 568 |
| EC_UKCS | L3M | 14 | 11.4 | 10347.0 | 61971.8 | 19.8 | 1381.6 | 16.2 | 20.6 | -30324.4 | 23.4 | -38976.3 | 5.5 | 1.1 | -3841.4 | 2.8 | 3523.6 | 132.1 | 2197.2 | 1877 | 1875 |
| EC_UKCS | L6M | 14 | 24.6 | 18768.0 | 61971.8 | 19.8 | 930.0 | 25.0 | 22.2 | -33013.0 | 24.5 | -40051.8 | 4.5 | 1.0 | -3780.4 | 2.4 | 2585.7 | 221.1 | 1573.1 | 4475 | 4472 |
| EC_UKCS | HOLD | 14 | 50.7 | 16786.7 | 74256.7 | 5.8 | 475.4 | 13.0 | 20.6 | -30693.6 | 23.0 | -37888.0 | 5.6 | 1.4 | -4848.1 | 2.6 | 3025.0 | 559.0 | 875.1 | 8179 | 8136 |

## 7. Deliver per book (v1.7 grammar + v1.8 fields) - proposals only

Proposed loss-side grammar: `early <book> <session|*> [ctx=fresh|reentry|chasing] [lots>=N] <rule> [slip=1.2]` with rules `flat d=D` | `nft X=X N=Nmin [half]` | `back0 mfe=Y` | `scratch mae=D exit=-S` | `rlock mae=D arm=-A exit=-B` | `partial F=F at=-D` | `struct <fr1|fr3|fr5|kc|st|vwap> buf=B [stop eqlots]`. New v1.8 fields needed: StructStopMode/Feature/Buffer (levels: 1/3/5-min 2-2 fractal at signal, Keltner mid EMA20 5-min, Supertrend 5-min ATR10x3, session VWAP), NoFollowThroughX/N, ScratchMae/ScratchExit, PartialCutFrac/PartialCutAt, MaeBars (running MAE), EntryContext (fresh/reentry/chasing from P7_CONTEXT_DEFS; DayRegime cannot carry it, it is per-entry).

- P7: d-scratch MAE>=40 exit -0 [lots>=5] (best loss-side rule, all fou); c-back0 after MFE>=40 [chasing] (recents-first: L1M/L3M/L6M/H) - candidate only, FAIL on acceptance unless stated above.
- K7: a-st buf0 stop+eq$lots [chasing] (order PASS arithmetic (-50% ); c-back0 after MFE>=10 [reentry] (recents-first: L1M/L3M/L6M/H); b-geom stop55 tgt60 fixed [ALL] (best geometry (fixed lots), ) - candidate only, FAIL on acceptance unless stated above.
- M7: c-flat d=50 [fresh] (best loss-side rule, all fou); c-nft X=5 N=5 full [ALL] (recents-first: L1M/L3M/L6M/H) - candidate only, FAIL on acceptance unless stated above.
- U7: d-rlock MAE>=40 arm -20 exit -30 [fresh] (best loss-side rule, all fou); a-kc buf2 stop+eq$lots [ALL] (order PASS arithmetic (-50% ); a-kc buf2 exit-on-break [ALL] (recents-first: L1M/L3M/L6M/H) - candidate only, FAIL on acceptance unless stated above.
- H7: e-partial F=0.33 at -15 noadd [ALL] (best loss-side rule, all fou); a-fr1 buf6 exit-on-break [fresh] (recents-first: L1M/L3M/L6M/H) - candidate only, FAIL on acceptance unless stated above.
- A7: d-rlock MAE>=30 arm -10 exit -15 [reentry] (recents-first: L1M/L3M/L6M/H) - candidate only, FAIL on acceptance unless stated above.
- O7: c-nft X=20 N=10 full [ALL] (recents-first: L1M/L3M/L6M/H) - candidate only, FAIL on acceptance unless stated above.

## 8. Worst 10 L6M sessions of the stack, entry by entry, live vs with the per-book finalists applied together (first-order)

Finalists applied: A7: d-rlock MAE>=30 arm -10 exit -15 [reentry]; H7: e-partial F=0.33 at -15 noadd [ALL]; K7: a-st buf0 stop+eq$lots [chasing]; M7: c-flat d=50 [fresh]; O7: c-nft X=20 N=10 full [ALL]; P7: d-scratch MAE>=40 exit -0 [lots>=5]; U7: d-rlock MAE>=40 arm -20 exit -30 [fresh].


**20260520 asia: live $-23263 -> with finalists $-23133** (21 trades)

| entry_utc | book | side | lots | ctx | live_exit | live_pts | live_usd | after_usd | rule |
|--|--|--|--|--|--|--|--|--|--|
| 22:09 | K7 | L | 1 | fresh | StopJoinFallback | -63.8 | -1276.0 | -1276.0 | - |
| 22:26 | P7 | S | 4 | chasing | StateCut | -43.1 | -3454.0 | -3454.0 | - |
| 22:27 | K7 | S | 1 | chasing | StackCut | -66.0 | -1321.0 | -1321.0 | - |
| 22:33 | A7 | S | 1 | chasing | Stop | -58.2 | -1166.0 | -1166.0 | - |
| 23:12 | K7 | L | 1 | reentry | Target | 60.0 | 1199.0 | 1199.0 | - |
| 00:03 | K7 | S | 1 | reentry | Target | 60.0 | 1199.0 | 1199.0 | - |
| 00:15 | H7 | S | 2 | chasing | StateCut | -25.8 | -1034.0 | -1034.0 | rule |
| 01:00 | P7 | L | 1 | fresh | StateCut | -37.6 | -1506.0 | -1506.0 | - |
| 01:15 | K7 | L | 1 | reentry | StopJoinFallback | -61.8 | -1236.0 | -1236.0 | - |
| 01:36 | K7 | S | 1 | chasing | StateCut | -64.4 | -1290.0 | -1290.0 | - |
| 01:50 | H7 | S | 2 | fresh | StateCut | -24.9 | -999.0 | -999.0 | rule |
| 01:51 | K7 | L | 1 | reentry | StateCut | -49.9 | -1000.0 | -1000.0 | - |
| 01:51 | P7 | L | 4 | reentry | StateCut | -39.5 | -3164.0 | -3164.0 | - |
| 02:00 | H7 | L | 4 | chasing | StateCut | -26.5 | -2129.0 | -1999.0 | rule |
| 02:33 | K7 | S | 1 | reentry | Target | 60.0 | 1199.0 | 1199.0 | - |
| 02:45 | H7 | S | 2 | chasing | StateCut | -24.3 | -974.0 | -974.0 | rule |
| 03:00 | P7 | S | 4 | chasing | StateCut | -41.9 | -3354.0 | -3354.0 | - |
| 03:03 | K7 | S | 1 | chasing | StateCut | -31.9 | -640.0 | -640.0 | - |
| 03:42 | K7 | L | 1 | reentry | StateCut | -25.7 | -515.0 | -515.0 | - |
| 04:03 | K7 | L | 1 | reentry | StateCut | -38.0 | -762.0 | -762.0 | - |
| 04:42 | K7 | S | 1 | chasing | StateCut | -51.9 | -1040.0 | -1040.0 | - |

**20261023 asia: live $-20695 -> with finalists $-20695** (16 trades)

| entry_utc | book | side | lots | ctx | live_exit | live_pts | live_usd | after_usd | rule |
|--|--|--|--|--|--|--|--|--|--|
| 22:07 | P7 | L | 4 | fresh | StateCut | -42.9 | -3434.0 | -3434.0 | - |
| 22:24 | K7 | L | 1 | chasing | StateCut | -45.5 | -912.0 | -912.0 | - |
| 23:03 | K7 | S | 1 | reentry | StateCut | -27.5 | -552.0 | -552.0 | - |
| 23:08 | P7 | L | 4 | reentry | StateCut | -42.7 | -3424.0 | -3424.0 | - |
| 23:33 | K7 | S | 1 | chasing | StateCut | -30.7 | -615.0 | -615.0 | - |
| 23:53 | P7 | L | 4 | reentry | StateCut | -43.2 | -3464.0 | -3464.0 | - |
| 00:15 | K7 | L | 1 | reentry | StateCut | -30.8 | -617.0 | -617.0 | - |
| 00:48 | K7 | L | 1 | chasing | StateCut | -39.9 | -800.0 | -800.0 | - |
| 00:50 | U7 | L | 2 | chasing | StateCut | -29.7 | -1189.0 | -1189.0 | - |
| 00:54 | A7 | L | 1 | chasing | StateCut | -33.4 | -670.0 | -670.0 | - |
| 01:02 | A7 | L | 1 | chasing | StateCut | -33.3 | -667.0 | -667.0 | - |
| 01:15 | K7 | S | 1 | reentry | StateCut | -36.4 | -730.0 | -730.0 | - |
| 01:42 | K7 | L | 1 | chasing | StopJoinFallback | -60.5 | -1211.0 | -1211.0 | - |
| 01:47 | A7 | L | 1 | chasing | StateCut | -34.8 | -697.0 | -697.0 | - |
| 02:44 | A7 | L | 1 | chasing | StateCut | -33.9 | -680.0 | -680.0 | - |
| 03:30 | H7 | S | 2 | fresh | StateCut | -25.8 | -1034.0 | -1034.0 | rule |

**20260901 asia: live $-20072 -> with finalists $-20072** (8 trades)

| entry_utc | book | side | lots | ctx | live_exit | live_pts | live_usd | after_usd | rule |
|--|--|--|--|--|--|--|--|--|--|
| 22:34 | P7 | L | 4 | fresh | StateCut | -39.9 | -3199.0 | -3199.0 | - |
| 22:51 | K7 | S | 2 | chasing | StopJoin | -54.4 | -2177.0 | -2177.0 | - |
| 01:10 | H7 | L | 2 | fresh | Stop | -58.2 | -2332.0 | -2332.0 | rule |
| 02:30 | U7 | S | 2 | chasing | StopJoinFallback | -59.0 | -2362.0 | -2362.0 | - |
| 02:35 | P7 | S | 4 | chasing | StateCut | -40.5 | -3249.0 | -3249.0 | - |
| 04:32 | P7 | L | 4 | reentry | StateCut | -41.9 | -3359.0 | -3359.0 | - |
| 05:50 | U7 | L | 2 | reentry | StopJoin | -55.0 | -2202.0 | -2202.0 | - |
| 05:51 | A7 | L | 1 | fresh | Stop | -59.5 | -1191.0 | -1191.0 | - |

**20260910 asia: live $-19535 -> with finalists $-19745** (13 trades)

| entry_utc | book | side | lots | ctx | live_exit | live_pts | live_usd | after_usd | rule |
|--|--|--|--|--|--|--|--|--|--|
| 22:15 | H7 | S | 2 | chasing | Target | 59.9 | 2393.0 | 2393.0 | rule |
| 23:01 | P7 | S | 4 | chasing | StateCut | -40.9 | -3274.0 | -3274.0 | - |
| 23:12 | K7 | S | 1 | chasing | StateCut | -45.4 | -910.0 | -1092.0 | rule |
| 00:10 | U7 | L | 2 | chasing | StopJoin | -56.0 | -2242.0 | -2242.0 | - |
| 00:18 | K7 | L | 1 | chasing | StopJoin | -53.2 | -1066.0 | -1292.0 | rule |
| 01:00 | U7 | S | 2 | chasing | Stop | -66.0 | -2642.0 | -2642.0 | - |
| 01:02 | A7 | S | 1 | chasing | Stop | -60.0 | -1201.0 | -1201.0 | - |
| 01:07 | P7 | S | 4 | chasing | StateCut | -41.8 | -3349.0 | -3349.0 | - |
| 01:12 | K7 | S | 1 | chasing | StateCut | -27.4 | -550.0 | -550.0 | - |
| 03:24 | K7 | S | 1 | chasing | StateCut | -32.0 | -642.0 | -1357.0 | rule |
| 04:39 | K7 | L | 1 | reentry | Target | 60.0 | 1199.0 | 1199.0 | - |
| 05:01 | A7 | L | 1 | reentry | Stop | -59.5 | -1191.0 | -278.0 | rule |
| 05:07 | P7 | L | 7 | reentry | StateCut | -43.2 | -6059.0 | -6059.0 | - |

**20260618 asia: live $-18896 -> with finalists $-13406** (13 trades)

| entry_utc | book | side | lots | ctx | live_exit | live_pts | live_usd | after_usd | rule |
|--|--|--|--|--|--|--|--|--|--|
| 22:12 | K7 | L | 1 | chasing | Target | 60.0 | 1199.0 | 1199.0 | - |
| 22:48 | K7 | L | 2 | chasing | Target | 60.0 | 2398.0 | 2398.0 | - |
| 23:42 | P7 | S | 7 | fresh | StateCut | -47.2 | -6615.0 | -6615.0 | - |
| 00:00 | K7 | L | 2 | chasing | Target | 60.0 | 2398.0 | 2398.0 | - |
| 00:10 | U7 | L | 4 | chasing | StopJoin | -47.1 | -3775.0 | -3775.0 | - |
| 00:11 | A7 | L | 1 | chasing | Stop | -56.8 | -1136.0 | -1136.0 | - |
| 00:15 | H7 | L | 4 | chasing | StateCut | -19.9 | -1594.0 | -1537.0 | rule |
| 00:31 | P7 | L | 7 | chasing | StateCut | -37.2 | -5221.0 | 211.0 | rule |
| 00:45 | K7 | L | 1 | chasing | StateCut | -34.4 | -690.0 | -690.0 | - |
| 01:22 | A7 | L | 1 | chasing | Stop | -60.0 | -1201.0 | -1201.0 | - |
| 03:39 | K7 | S | 1 | reentry | Target | 60.0 | 1199.0 | 1199.0 | - |
| 04:40 | U7 | S | 4 | reentry | StopJoinFallback | -63.7 | -5100.0 | -5100.0 | - |
| 05:24 | K7 | L | 1 | chasing | StateCut | -37.8 | -757.0 | -757.0 | - |

**20260824 london: live $-17840 -> with finalists $-17840** (15 trades)

| entry_utc | book | side | lots | ctx | live_exit | live_pts | live_usd | after_usd | rule |
|--|--|--|--|--|--|--|--|--|--|
| 06:19 | P7 | S | 1 | chasing | StateCut | -40.0 | -1604.0 | -1604.0 | - |
| 06:31 | M7 | S | 2 | chasing | StateCut | -35.2 | -1409.0 | -1409.0 | - |
| 06:33 | K7 | S | 2 | chasing | StateCut | -40.8 | -1634.0 | -1634.0 | - |
| 07:36 | K7 | L | 1 | reentry | StateCut | -44.2 | -885.0 | -885.0 | - |
| 07:42 | M7 | S | 1 | chasing | StateCut | -34.4 | -690.0 | -690.0 | - |
| 07:51 | K7 | S | 1 | chasing | StateCut | -31.4 | -630.0 | -630.0 | - |
| 08:02 | P7 | S | 2 | chasing | StopJoin | -58.0 | -2322.0 | -2322.0 | - |
| 08:21 | K7 | L | 1 | reentry | Target | 60.0 | 1199.0 | 1199.0 | - |
| 08:53 | M7 | L | 1 | chasing | StateCut | -35.0 | -702.0 | -702.0 | - |
| 09:04 | P7 | L | 1 | chasing | StateCut | -42.8 | -857.0 | -857.0 | - |
| 09:05 | M7 | L | 1 | chasing | StateCut | -30.2 | -605.0 | -605.0 | - |
| 09:50 | M7 | L | 2 | chasing | StateCut | -35.9 | -1439.0 | -1439.0 | - |
| 11:12 | P7 | S | 2 | chasing | StateCut | -43.0 | -1724.0 | -1724.0 | - |
| 11:40 | U7 | L | 2 | chasing | Stop | -70.2 | -2812.0 | -2812.0 | - |
| 11:48 | P7 | L | 2 | chasing | StateCut | -43.0 | -1724.0 | -1724.0 | - |

**20261008 asia: live $-16898 -> with finalists $-15842** (10 trades)

| entry_utc | book | side | lots | ctx | live_exit | live_pts | live_usd | after_usd | rule |
|--|--|--|--|--|--|--|--|--|--|
| 22:10 | A7 | L | 1 | chasing | StackCut | -53.2 | -1066.0 | -1066.0 | - |
| 22:21 | P7 | L | 7 | chasing | StateCut | -41.9 | -5873.0 | -5873.0 | - |
| 22:42 | K7 | L | 2 | chasing | StopJoin | -57.0 | -2282.0 | -1226.0 | rule |
| 00:30 | U7 | S | 2 | fresh | StopJoinFallback | -54.0 | -2162.0 | -2162.0 | - |
| 00:44 | A7 | S | 1 | chasing | Stop | -60.5 | -1211.0 | -1211.0 | - |
| 00:56 | P7 | S | 7 | chasing | StateCut | -42.6 | -5978.0 | -5978.0 | - |
| 01:30 | K7 | L | 1 | fresh | StackCut | -35.8 | -716.0 | -716.0 | - |
| 01:45 | A7 | L | 1 | chasing | Stop | -60.0 | -1201.0 | -1201.0 | - |
| 03:36 | K7 | S | 1 | reentry | Target | 60.0 | 1199.0 | 1199.0 | - |
| 03:50 | U7 | S | 2 | chasing | Target | 59.9 | 2393.0 | 2393.0 | - |

**20260706 asia: live $-16897 -> with finalists $-15943** (23 trades)

| entry_utc | book | side | lots | ctx | live_exit | live_pts | live_usd | after_usd | rule |
|--|--|--|--|--|--|--|--|--|--|
| 22:09 | K7 | S | 1 | chasing | StopJoinFallback | -58.0 | -1161.0 | -207.0 | rule |
| 22:33 | K7 | L | 1 | reentry | StateCut | -48.3 | -967.0 | -967.0 | - |
| 22:40 | H7 | L | 2 | chasing | StateCut | -33.0 | -1324.0 | -1324.0 | rule |
| 23:13 | P7 | L | 4 | chasing | StateCut | -45.7 | -3659.0 | -3659.0 | - |
| 23:32 | A7 | L | 1 | chasing | StateCut | -47.5 | -952.0 | -952.0 | - |
| 00:03 | K7 | S | 2 | reentry | StopJoinFallback | -64.5 | -2582.0 | -2582.0 | - |
| 00:16 | P7 | L | 4 | chasing | StateCut | -40.5 | -3249.0 | -3249.0 | - |
| 00:27 | K7 | S | 1 | reentry | Target | 60.0 | 1199.0 | 1199.0 | - |
| 01:04 | P7 | S | 1 | reentry | Target | 60.0 | 2398.0 | 2398.0 | - |
| 01:06 | K7 | S | 1 | chasing | Target | 60.0 | 1199.0 | 1199.0 | - |
| 01:27 | A7 | S | 1 | chasing | StateCut | -42.9 | -860.0 | -860.0 | - |
| 01:30 | U7 | S | 4 | chasing | StateCut | -34.6 | -2774.0 | -2774.0 | - |
| 01:36 | P7 | S | 7 | chasing | Target | 60.0 | 8392.0 | 8392.0 | - |
| 01:45 | K7 | S | 1 | chasing | Target | 60.0 | 1199.0 | 1199.0 | - |
| 01:51 | A7 | S | 1 | chasing | StateCut | -53.7 | -1075.0 | -1075.0 | - |
| 01:58 | P7 | S | 7 | chasing | StateCut | -41.5 | -5813.0 | -5813.0 | - |
| 02:12 | P7 | S | 2 | chasing | Target | 59.9 | 2393.0 | 2393.0 | - |
| 02:15 | K7 | S | 2 | chasing | Target | 59.9 | 2393.0 | 2393.0 | - |
| 02:56 | P7 | S | 7 | chasing | StateCut | -42.1 | -5903.0 | -5903.0 | - |
| 03:12 | K7 | L | 1 | reentry | StateCut | -47.3 | -947.0 | -947.0 | - |
| 03:43 | P7 | S | 4 | chasing | StateCut | -38.3 | -3072.0 | -3072.0 | - |
| 03:54 | K7 | S | 1 | chasing | StopJoin | -60.0 | -1201.0 | -1201.0 | - |
| 04:21 | K7 | L | 1 | reentry | StateCut | -26.4 | -530.0 | -530.0 | - |

**20260518 asia: live $-16004 -> with finalists $-16004** (16 trades)

| entry_utc | book | side | lots | ctx | live_exit | live_pts | live_usd | after_usd | rule |
|--|--|--|--|--|--|--|--|--|--|
| 22:06 | K7 | L | 1 | chasing | StateCut | -32.0 | -642.0 | -642.0 | - |
| 22:19 | P7 | L | 4 | chasing | StateCut | -43.9 | -3514.0 | -3514.0 | - |
| 22:39 | P7 | L | 4 | chasing | StateCut | -36.6 | -2934.0 | -2934.0 | - |
| 22:42 | K7 | L | 1 | chasing | StateCut | -31.9 | -640.0 | -640.0 | - |
| 23:09 | K7 | S | 1 | reentry | Target | 60.0 | 1199.0 | 1199.0 | - |
| 23:37 | P7 | S | 4 | reentry | Target | 59.9 | 2393.0 | 2393.0 | - |
| 23:57 | P7 | S | 7 | reentry | StateCut | -40.5 | -5673.0 | -5673.0 | - |
| 00:06 | K7 | S | 1 | chasing | Target | 60.0 | 1199.0 | 1199.0 | - |
| 00:42 | K7 | S | 1 | chasing | StateCut | -38.9 | -780.0 | -780.0 | - |
| 00:47 | A7 | S | 1 | chasing | StateCut | -31.4 | -630.0 | -630.0 | - |
| 01:37 | A7 | S | 1 | chasing | StateCut | -41.8 | -837.0 | -837.0 | - |
| 01:51 | K7 | L | 1 | reentry | StateCut | -34.5 | -692.0 | -692.0 | - |
| 02:15 | K7 | L | 1 | reentry | StateCut | -30.4 | -610.0 | -610.0 | - |
| 03:45 | K7 | L | 1 | reentry | StateCut | -30.9 | -620.0 | -620.0 | - |
| 04:35 | H7 | S | 1 | chasing | StateCut | -57.8 | -2314.0 | -2314.0 | rule |
| 05:18 | K7 | S | 1 | chasing | StateCut | -45.4 | -910.0 | -910.0 | - |

**20260616 asia: live $-15709 -> with finalists $-15589** (9 trades)

| entry_utc | book | side | lots | ctx | live_exit | live_pts | live_usd | after_usd | rule |
|--|--|--|--|--|--|--|--|--|--|
| 22:12 | K7 | S | 1 | chasing | StateCut | -30.8 | -617.0 | -617.0 | - |
| 22:33 | P7 | S | 7 | chasing | StateCut | -44.0 | -6163.0 | -6163.0 | - |
| 22:40 | U7 | S | 4 | chasing | StateCut | -34.8 | -2789.0 | -2789.0 | - |
| 00:19 | P7 | L | 2 | fresh | StateCut | -45.2 | -1809.0 | -1809.0 | - |
| 00:51 | K7 | S | 1 | chasing | StateCut | -27.5 | -552.0 | -432.0 | rule |
| 01:07 | P7 | S | 4 | chasing | StateCut | -41.9 | -3359.0 | -3359.0 | - |
| 01:14 | A7 | S | 1 | chasing | StateCut | -54.8 | -1097.0 | -1097.0 | - |
| 02:57 | K7 | S | 1 | chasing | StateCut | -26.0 | -522.0 | -522.0 | - |
| 03:21 | K7 | L | 1 | reentry | Target | 60.0 | 1199.0 | 1199.0 | - |

## 9. Open items / questions (none blocking)
- Context tags: chase_k > 1.0 is true for 69% of trades (so "fresh" is a small cell, 17%); say if a stricter chasing cut (1.5-2.0, grid in P7_CONTEXT_DEFS) is wanted for the by-context table.
- Keltner mid, Supertrend and VWAP definitions are not in a spec I could find (5-min EMA20 close, 5-min ATR10x3, tick VWAP from the 18:00 ET file start were used); point me at the K7/U7/H7 definitions if they differ.
- Next cycle: context x session masks for the d/e families, a-family dynamic levels with exits at the structure level, combination rows (g), K7 chasing Supertrend stop to the exact slate (EC_KST), W-Q scorecard c-e on finalists (21:30Z), exact results as they land.
