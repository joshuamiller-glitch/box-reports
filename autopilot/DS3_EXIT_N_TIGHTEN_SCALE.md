# DS3_EXIT_N_TIGHTEN_SCALE - T-EXIT-N family E2: TIGHTEN (breakeven / +X, trail) on the true fill basis N (S4b, written 13:43Z 2026-11-02)
POST-HOC, no PASS claim, Shadow only. Prereg l2vast/ds3/prereg/EXITN_E2_prereg.md sha256 7eb0286f9f51d97cb9830e99ffd2f056e9f6694e6c31394194ee4795d4ed7db5 (DECISIONS.md 2026-11-02T14:42Z), logged before any statistic. SCALE-OUT was taken by ZL-3 (DS3_ZONES_3_SCALEOUT.md) and is not duplicated here (the 8 scale-out cells of the prereg were dropped from this run).
Base = D7 V13T_LIVE (V13Z, profit lines empty, xcost 0.80, stop fill 2.45 pt worse, targets nominal, resting add cancelled on any exit, per-book locks, lock none). Base maxDD $k: {'L6M': 151, 'HOLD': 151, 'MID': 44, 'PRE': 166, "X'": 92}; mean $k/wk {'L6M': np.float64(36.7), 'HOLD': np.float64(30.4), 'MID': np.float64(24.0), 'PRE': np.float64(17.3), "X'": np.float64(4.8)}.
Rules (1-s path, from each library row's entry second to its library exit second; pct = side*(SC[j]-E)/td; evaluated once per second): BE = after the first second with pct >= P (0.3/0.5/0.7) and the gate, stop to E + X (X 0/1/2 pts = 0/4/8 ticks); exit at the first later second whose low/high crosses it, at the stop level, priced as a stop (2.45 pt worse); TR = trail N pts (5/7.5/11.25/15 = 20/30/45/60 ticks) behind the running favourable extreme after arming; K7TR = the live panel line AS CODED (K7/KB only, P 0.70, tot_rel >= 1.2, trail 30 pts). Gates use the 1-s hour-normalised arrays (tot_rel = relTh; ahead_rel = relAh long / relBh short): G1 tot>=1.2, G2 ahead>=1.5, G3 tot>=1.5 and ahead>=1.2. 61 cells, one engine run each.
## Plain sentence
**On true fills no tighten rule pays.** Of 61 cells (breakeven/+X at pct 0.3/0.5/0.7 gated and ungated, trails 5-15 pts, and the K7 panel line as coded) 0 are eligible and the best mean change in HOLD is -0.20k/wk (all inside MDE, nearly all negative; ungated rules cost -4k to -14k/wk and deepen HOLD/MID maxDD). The K7 line as coded: -0.79k/wk in HOLD, -0.11k in PRE, maxDD HOLD +5%, PRE -3%, MID -21%: neutral on average, no tail cut. Breakeven stops are hit by the ordinary pullback of winners at an extra 2.45-pt stop cost; trails give up the right tail. The P>=0.7 gated BE variants are the least bad (arming is rare) and cut HOLD maxDD +9..+13% with PRE ~0% but X' -30..-45% (harm). No placebo was run (no cell passes eligibility).
## Family summary (per kind and arming pct; d in $k/wk; cutH_pos / cutP_pos = share of cells with a positive HOLD / PRE maxDD cut)
|               |   cells |   mean_dHOLD |   best_dHOLD |   mean_dPRE |   cutH_pos |   cutP_pos |   best_S |   elig |
|:--------------|--------:|-------------:|-------------:|------------:|-----------:|-----------:|---------:|-------:|
| ('BE', 0.3)   |      12 |       -17.26 |       -12.43 |      -14.2  |       0    |       0    |    -0.51 |      0 |
| ('BE', 0.5)   |      12 |        -8.86 |        -4.23 |       -9.11 |       0    |       0    |    -0.02 |      0 |
| ('BE', 0.7)   |      12 |        -1.91 |        -0.2  |       -4.1  |       0.42 |       0.42 |    -0.07 |      0 |
| ('K7TR', 0.7) |       1 |        -0.79 |        -0.79 |       -0.11 |       1    |       0    |     0.01 |      0 |
| ('TR', 0.3)   |       8 |       -29.68 |       -27.53 |      -17.83 |       0    |       0    |    -1.52 |      0 |
| ('TR', 0.5)   |       8 |       -22.87 |       -20.1  |      -14.55 |       0    |       0    |    -0.45 |      0 |
| ('TR', 0.7)   |       8 |       -12.67 |       -11.46 |       -7.8  |       0    |       0.75 |    -0.11 |      0 |
## Top 15 by S (equal-risk maxDD cut mean over HOLD, PRE, X')
| cell | rows changed | S | elig | cut HOLD / PRE / X' / L6M / MID | mean d HOLD / PRE / X' $k/wk (MDE HOLD) | S/T/N |
|---|---|---|---|---|---|---|
| K7TR_P0.7_30_G1 | 1474 | +0.008 | n | +5% / -3% / -1% / +5% / -21% | -0.8 / -0.1 / +0.1 (2.4) | n/n/n |
| BE_P0.5_1_G3 | 10828 | -0.021 | n | -4% / -2% / -2% / +18% / -75% | -4.4 / -8.4 / -0.6 (10.1) | n/n/n |
| BE_P0.5_0_G3 | 10600 | -0.036 | n | -7% / -2% / -5% / +15% / -79% | -4.7 / -7.4 / -0.8 (10.1) | n/n/n |
| BE_P0.5_2_G3 | 11038 | -0.041 | n | -2% / -7% / -5% / +22% / -71% | -4.2 / -8.1 / -0.8 (10.2) | n/n/n |
| BE_P0.7_2_G1 | 7641 | -0.069 | n | +13% / +1% / -42% / +13% / -42% | -1.9 / -4.3 / +0.4 (7.1) | n/n/n |
| BE_P0.5_0_G2 | 14387 | -0.079 | n | -8% / -34% / +5% / +4% / -77% | -8.6 / -8.9 / -1.0 (10.8) | n/n/n |
| BE_P0.7_2_G3 | 4590 | -0.083 | n | +1% / +1% / -36% / +1% / -24% | -0.3 / -2.6 / +0.9 (6.4) | n/n/n |
| BE_P0.7_1_G1 | 7501 | -0.087 | n | +9% / +1% / -40% / +9% / -14% | -1.6 / -5.0 / +0.4 (7.0) | n/n/n |
| BE_P0.7_1_G3 | 4507 | -0.088 | n | -1% / +1% / -32% / -1% / -26% | -0.2 / -2.6 / +1.1 (6.3) | n/n/n |
| BE_P0.7_0_G3 | 4408 | -0.091 | n | -3% / -0% / -31% / -3% / -28% | -0.3 / -2.3 / +1.1 (6.2) | n/n/n |
| BE_P0.7_0_G1 | 7338 | -0.097 | n | +4% / -1% / -39% / +4% / -18% | -1.9 / -4.7 / +0.4 (7.0) | n/n/n |
| TR_P0.7_15_ungated | 24880 | -0.110 | n | -30% / +5% / +22% / -30% / -66% | -11.9 / -7.7 / -0.8 (12.1) | n/n/n |
| BE_P0.7_2_ungated | 11058 | -0.130 | n | -3% / -1% / -35% / +16% / -65% | -4.9 / -4.8 / +0.8 (8.3) | n/n/n |
| BE_P0.7_1_ungated | 10851 | -0.131 | n | +2% / -15% / -33% / +12% / -44% | -4.7 / -5.9 / +0.7 (8.2) | n/n/n |
| BE_P0.5_1_ungated | 21571 | -0.131 | n | -46% / -9% / +6% / -12% / -191% | -12.7 / -10.3 / -1.9 (11.6) | n/n/n |
## The v1.3 panel tighten line as coded (K7 tighten 30, pct >= 0.70, tot_rel >= 1.2): mean delta by KB session, $k/wk
| K7 (KB) session | HOLD mean d $k/wk | PRE mean d | X' mean d |
|---|---|---|---|
| asia | +0.39 | -0.06 | -0.08 |
| london | -0.92 | -0.24 | -0.43 |
| pre | +0.00 | +0.00 | +0.00 |
| nyam | -0.04 | -0.16 | +0.06 |
| nypm | -0.22 | +0.35 | +0.54 |
| close | +0.00 | +0.00 | +0.00 |

Fired on 1474 library rows (KB only).
## Not scored / caveats
Scale-out (ZL-3). Rest-to-breakeven after a scale-out (the inject API cannot combine a partial and a later full exit without double counting). pulled_mult and ice_against gates (no 1-s array on disk). Entry second = library entry second (the 70/30 dip-fill timing is approximated; the engine ignores an injected exit at or before the real fill). A6 PB7 rows (22,357, no library trade row) untouched. Lock 12R reference, Z3's V13T PA band, per-book x session cuts and carrying-week naming are not run because no cell is eligible. Ledger: 61 cells appended to DEAD_CELLS (program EXITN_E2). Cubes /mnt/l2/l2vast/ds3_zones3_new/e2/cubes, table e2_table.pkl, code zones3/s4b/e2.py + e2_an.py.


# E2b - FLOW-GATED TIGHTEN (added 14:07Z 2026-11-02)
Prereg l2vast/ds3/prereg/EXITN_E2B_prereg.md sha256 4dea07a66bbf20636ea1cd72eb847fa4cb0f99b831fc8a7c66878000e4325c04 (logged before scoring). Same base (V13T_LIVE lock none), cost model, path rules and standards as above; the arming gate is pct >= P (0.3/0.5/0.7) AND a flow condition against the trade, from the shared 1-s arrays built for E1/E2/E3 (/mnt/l2/l2vast/ds3_flow1s/, README, audit 0 violations): F1 delta-turn against (delta5 against and delta30 with), F2 large print against (tier-2 >= 25 lots against in 30 s, more than with), F3 pulled own support mult5 >= 50 / 100, F3a pulled ahead-side liquidity (the other reading) >= 50 / 100, F4 iceberg against (ahead-side ratio) >= 100 / 300; actions BE0, BE1, TR7.5 (stop priced 2.45). 72 cells.
## Plain sentence
**Flow-gated tightening does not pay on true fills either:** 0 of 72 cells are eligible, the best HOLD mean change is -1.00k/wk (all negative), the best score is +0.009 (F2 large-print-against with a 7.5-pt trail at pct 0.5, HOLD maxDD +10% but PRE -12% and MID -30%). The large-print gate (F2) is the most selective (about 8k rows), the others arm on 14k-27k rows like the static gates; none of them picks the trades that reverse: the average armed trade still finishes better than its tightened exit once the 2.45-pt stop fill and the foregone target are paid.
## Per gate
| gate     |   cells |   rows_mean |   mean_dHOLD |   best_dHOLD |   mean_dPRE |   cutH_pos |   best_S |   elig |
|:---------|--------:|------------:|-------------:|-------------:|------------:|-----------:|---------:|-------:|
| F1_T0    |       9 |    26384.1  |       -13.12 |        -2.08 |      -10.33 |       0.22 |    -0.02 |      0 |
| F2_T25   |       9 |     8195.22 |        -3.01 |        -1    |       -1.83 |       0.67 |     0.01 |      0 |
| F3_T100  |       9 |    23250.9  |       -12.09 |        -1.44 |       -8.07 |       0.22 |    -0.01 |      0 |
| F3_T50   |       9 |    27134.1  |       -14.49 |        -2.74 |      -10.86 |       0    |    -0.07 |      0 |
| F3a_T100 |       9 |    24065.2  |       -12.17 |        -2.28 |       -8.58 |       0    |    -0.01 |      0 |
| F3a_T50  |       9 |    27515.7  |       -14.19 |        -2.86 |      -10.73 |       0.11 |    -0.11 |      0 |
| F4_T100  |       9 |    23919.1  |       -10.4  |        -3    |       -9.44 |       0    |    -0.1  |      0 |
| F4_T300  |       9 |    14288.8  |        -2.51 |        -1.14 |       -4.18 |       0    |    -0.03 |      0 |
## Top 10 by S
| cell | rows | S | elig | cut HOLD / PRE / X' / L6M / MID | mean d HOLD / PRE $k/wk (MDE HOLD) |
|---|---|---|---|---|---|
| F2_T25_P0.5_TR7.5 | 13018 | +0.009 | n | +10% / -12% / +13% / +10% / -30% | -4.4 / -2.0 (6.2) |
| F3a_T100_P0.7_BE0 | 8162 | -0.005 | n | -6% / -0% / +4% / -6% / -60% | -2.3 / -3.6 (7.4) |
| F3_T100_P0.7_BE1 | 7931 | -0.007 | n | +4% / +3% / -4% / +11% / -48% | -1.9 / -2.1 (8.1) |
| F3_T100_P0.7_BE0 | 7771 | -0.015 | n | +3% / +2% / -4% / +7% / -50% | -1.4 / -2.0 (7.3) |
| F3a_T100_P0.7_BE1 | 8323 | -0.019 | n | -2% / -14% / +5% / -2% / -54% | -2.9 / -4.1 (8.1) |
| F1_T0_P0.7_BE1 | 8924 | -0.021 | n | +6% / +6% / -35% / +6% / -50% | -2.6 / -4.5 (7.9) |
| F4_T300_P0.7_BE0 | 4772 | -0.027 | n | -4% / -3% / -2% / -3% / -33% | -2.2 / -1.1 (3.1) |
| F4_T300_P0.7_BE1 | 4873 | -0.029 | n | -3% / -3% / -5% / -3% / -32% | -2.2 / -1.0 (3.1) |
| F1_T0_P0.7_BE0 | 8731 | -0.063 | n | +3% / +4% / -34% / +3% / -54% | -2.1 / -4.1 (7.3) |
| F2_T25_P0.5_BE1 | 5266 | -0.063 | n | +12% / -8% / -20% / +12% / -15% | -1.0 / -0.6 (4.7) |
Ledger: 72 cells appended (program EXITN_E2B). Cubes /mnt/l2/l2vast/ds3_zones3_new/e2/cubes_b, table e2b_table.pkl, code zones3/s4b/e2b.py.
