# DS3_ZEN_LINES_B - regime-line search with the entry fixed at ZM1 (D3ZLN, 2026-10-28)

**Verdict line:** best regime line / best entry line / EMA200 rank among N / effect vs random with MDE: **best regime line = B|rs240|WMA_100_hl2|dist40 (effect +1.85 pt/trade [-0.29, 4.50] vs random-in-regime, MDE80 3.33 = inside MDE, n 134, win 64.2% vs break-even 62.3%, HOLD -1.62 [-4.07, 1.11])**; entry line fixed here (best entry line: see LINES_C); **the 5-min EMA200 side ranks 2299 of 7085 eligible cells (2299 of N = 7,242) with effect -0.26 [-0.79, 0.31] (MDE80 0.80)**; 0 of 7,085 cells has a week-block CI above 0, 0 beats the 5-min EMA200 paired on the same weeks by more than the MDE, studentised White reality-check p of the best cell 0.99 over N = 7,242: **no regime line beats random-in-regime, and the EMA200 is one ordinary (below-median) member of the family.**

## 1. Counts block (descriptive, before any score)
Clusters: regime 2,414 (3m 209, 5m 234, 10m 290, 15m 306, 30m 353, 60m 459, 240m 563) - see DS3_ZEN_LINES_A.md. Entry events: ZM1 hold candle at the 1-min EMA200 or RTH VWAP (tol 2 pt), PRE, 10:00-14:00: 11,286 mapped (e, side) events, 86,252 PRE entry bars in the pool. 157 cells have fewer than 100 trades (counts, not verdicts); 7,085 are eligible.

## 2. Grid enumeration and screened N
2,414 regime-line clusters x 3 semantics (side; side + 5-bar slope; side + distance <= 40 pt) x entry ZM1 x one bracket x PRIMARY x flat 14:00 = **7,242 scored (0 skipped)**. Prereg `ZEN_LINES_B_prereg.md` sha256 bbd7907f43dc4a20c6420516709a1a613e9eab5e609551a93e9c09d620af9518 (logged in DECISIONS.md before scoring). Family reality check: studentised max-statistic, 2,000 week-block draws, 75 PRE weeks: best t = 1.76, p = 0.994 (raw-max p 0.948). Program N 291,130 (plan).

Summary of the 7,085 eligible cells: effect>0 in 814; mean net1>0 in 9; **net2>0 in 0**; CI lower>0 in 0 (expected ~2.5% = 177 by chance if the effect distribution were centred on 0 with width 1 SE, so the distribution is shifted NEGATIVE: median effect -0.39 pt/trade for 'side', -0.41 'slope', -0.17 'dist40'); win>break-even in 9; effect>=MDE80 in 0. The pooled random-in-regime expectation itself is -1.7 pt/trade (the 15-pt-stop / swing-target bracket loses about the cost of the spread of outcomes in every regime).

By regime timeframe (eligible cells, median effect / best / CI>0 count / median regime value = pool mean minus the unconditioned pool mean): rs10: -0.37 / 1.38 / 0 / -0.02; rs240: -0.31 / 1.85 / 0 / 0.04; rs60: -0.39 / 1.52 / 0 / 0.01; time_15m: -0.39 / 1.57 / 0 / -0.03; time_30m: -0.38 / 1.25 / 0 / -0.01; time_3m: -0.34 / 0.39 / 0 / 0.01; time_5m: -0.37 / 0.64 / 0 / -0.01. The regime itself is worth about 0 +- 0.04 pt/trade at the median; the best regime value cells (rs240 distance<=40 lines) are selection on 100-200 trades.


EMA200 reference (5-min EMA_200_close, cluster with SMMA_100): side: effect -0.26, n 2004, rank 2299; slope: effect -0.33, n 1841, rank 3140; dist40: effect +0.42, n 879, rank 175.

Top 5 by win rate above break-even: B|rs240|WMA_100_hl2|dist40 win 64.2% vs BE 62.3% (+1.9 pp), net1 +0.45; B|rs240|HMA_377_close|dist40 win 67.2% vs BE 66.3% (+0.9 pp), net1 +0.21; B|rs60|ZLEMA_377_hl2|dist40 win 61.0% vs BE 60.2% (+0.8 pp), net1 +0.21; B|rs240|VWMA_233_hl2|dist40 win 64.5% vs BE 63.8% (+0.8 pp), net1 +0.18; B|rs60|ZLEMA_377_close|dist40 win 60.2% vs BE 59.5% (+0.7 pp), net1 +0.17. All within noise (9 of 7,085 cells have win>BE).

Paired against the 5-min EMA200 of the same semantics on the same weeks (difference of effects, shared bootstrap draws): cells with difference CI lower > 0 AND difference > MDE80 of the difference: **0**. Largest difference +1.43 (MDE80 of the difference 3.70).

## 4. Holdout (top 30, ONE look) and gates
Pre-holdout text DS3_ZEN_LINES_B_PREHOLD.md (sha in DECISIONS.md). HOLD n is 25-190 trades per cell (33 weeks); X = 2023-04..2024-01.

Gate pass counts over the 30: G6 0, G7 17, G8 0 (reality-check p of every cell > 0.05), G9 0; **no cell passes G1-G9; 0 CANDIDATE, 0 LEAD.** Mean HOLD effect of the 30 = 0.46 (PRE 1.30): the PRE ranking does not persist.

| cell | PRE (re-run) effect [CI] | HOLD n | HOLD net1 | HOLD effect [CI] | rank | X (2023-04..2024-01) effect | 2024 net$ / 2025 / 2026 (10 lots, $) | G6 G7 G8 G9 |
|---|---|---|---|---|---|---|---|---|
| B|rs240|WMA_100_hl2|dist40 | 1.91 [-0.14, 4.42] | 49 | -3.74 | -1.62 [-4.07, 1.11] | 0.10 | 0.48 | 40304 / -47642 / -12918 | n Y n n |
| B|rs240|WMA_50_hlc3|dist40 | 1.63 [-0.26, 3.60] | 102 | -3.05 | -0.54 [-2.83, 1.27] | 0.31 | 0.67 | -6523 / -76116 / -2274 | n Y n n |
| B|time_15m|VIDYA_377_close|dist40 | 1.51 [-0.84, 4.31] | 83 | -3.99 | -0.05 [-2.02, 2.20] | 0.46 | 0.76 | -2268 / -65531 / -10831 | n Y n n |
| B|rs60|VIDYA_100_hl2|dist40 | 1.39 [-0.56, 3.65] | 82 | -3.10 | 0.24 [-2.41, 2.60] | 0.57 | 0.64 | 10284 / -67396 / -13897 | n Y n n |
| B|rs240|T3_34_hl2|dist40 | 1.37 [-0.68, 3.24] | 70 | -3.67 | -0.72 [-3.08, 0.74] | 0.32 | -4.70 | -4441 / -60954 / -12755 | n n n n |
| B|rs60|ZLEMA_377_hl2|dist40 | 1.64 [-0.83, 3.83] | 70 | -1.72 | 1.52 [-1.06, 3.89] | 0.96 | 1.03 | 8420 / -31038 / -1900 | n Y n n |
| B|rs60|SMMA_89_hl2|dist40 | 1.44 [-0.56, 3.57] | 86 | -1.14 | 0.80 [-1.64, 3.89] | 0.73 | -1.24 | 7837 / -28378 / -4267 | n n n n |
| B|rs60|VIDYA_89_close|dist40 | 1.23 [-0.81, 3.37] | 75 | -1.87 | 1.08 [-1.32, 3.67] | 0.83 | -1.12 | 23361 / -56059 / -9387 | n n n n |
| B|rs60|ZLEMA_233_hl2|dist40 | 1.34 [-0.53, 3.09] | 91 | -1.04 | 1.43 [-0.29, 3.22] | 0.93 | -0.08 | 3858 / -54786 / -6571 | n n n n |
| B|rs60|LSMA_377_close|dist40 | 1.59 [-0.31, 3.35] | 74 | -0.89 | 1.48 [-0.95, 3.79] | 0.95 | 1.54 | -18941 / -17493 / -4135 | n Y n n |
| B|rs60|ZLEMA_233_close|dist40 | 1.29 [-0.47, 3.02] | 91 | -0.98 | 1.52 [-0.50, 3.32] | 0.94 | -0.05 | 8731 / -58742 / -3523 | n n n n |
| B|rs10|VIDYA_377_close|dist40 | 1.40 [-0.46, 3.57] | 86 | -1.91 | 0.86 [-1.89, 4.12] | 0.81 | -1.40 | 9474 / -34338 / -8365 | n n n n |
| B|rs240|MCG_34_hl2|dist40 | 1.34 [-0.41, 3.26] | 117 | -3.35 | -0.41 [-2.83, 1.74] | 0.32 | 0.83 | 23337 / -111339 / -1705 | n Y n n |
| B|rs60|VIDYA_100_hlc3|dist40 | 1.23 [-0.67, 3.19] | 79 | -2.10 | 1.02 [-1.39, 3.52] | 0.76 | -0.05 | 9147 / -57443 / -14139 | n n n n |
| B|rs240|ZLEMA_100_close|dist40 | 1.36 [-0.96, 3.43] | 73 | -1.50 | 2.22 [-0.38, 4.18] | 0.98 | 1.59 | 3717 / -31250 / 1850 | n Y n n |
| B|rs60|KAMA_233_hl2|dist40 | 1.27 [-0.20, 2.63] | 142 | -3.08 | 0.20 [-1.72, 1.74] | 0.62 | -2.17 | -21389 / -83476 / -28272 | n n n n |
| B|time_30m|VIDYA_200_close|dist40 | 1.10 [-1.13, 3.93] | 71 | -3.14 | 1.03 [-1.16, 4.05] | 0.75 | 0.29 | -19942 / -53134 / -3637 | n Y n n |
| B|rs240|ZLEMA_144_close|dist40 | 1.28 [-0.35, 2.75] | 63 | -0.86 | 1.37 [-2.08, 5.70] | 0.90 | 0.61 | -29975 / 4051 / -15353 | n Y n n |
| B|rs240|MCG_34_hlc3|dist40 | 1.12 [-0.52, 2.91] | 122 | -3.42 | -0.59 [-2.76, 1.48] | 0.28 | 0.79 | 20090 / -119005 / -1892 | n Y n n |
| B|rs240|ALMA_144_hl2|dist40 | 1.31 [-0.91, 3.37] | 59 | -0.13 | 1.52 [-2.09, 4.36] | 0.82 | -1.83 | -4792 / -2352 / -1952 | n n n n |
| B|rs240|LSMA_50_hl2|dist40 | 0.98 [-0.68, 2.60] | 114 | -3.27 | -0.21 [-1.18, 1.13] | 0.41 | -0.21 | 26275 / -108279 / -21623 | n n n n |
| B|rs240|ZLEMA_144_hl2|dist40 | 1.20 [-0.41, 2.82] | 57 | -0.87 | 1.23 [-2.14, 5.84] | 0.91 | 1.24 | -35784 / -9257 / -12304 | n Y n n |
| B|rs240|LSMA_200_hlc3|dist40 | 1.22 [-0.82, 3.20] | 111 | -2.86 | -0.85 [-3.25, 1.27] | 0.23 | -7.29 | 8620 / -65885 / -9995 | n n n n |
| B|time_30m|VIDYA_200_hlc3|dist40 | 1.07 [-1.12, 3.29] | 91 | -3.91 | -0.05 [-2.94, 2.51] | 0.48 | 0.49 | 8135 / -98439 / -4490 | n Y n n |
| B|time_30m|VIDYA_200_hl2|dist40 | 1.01 [-0.99, 3.31] | 94 | -4.26 | -0.60 [-3.75, 2.11] | 0.36 | 0.22 | 1085 / -101288 / -4490 | n Y n n |
| B|rs10|VIDYA_377_hl2|dist40 | 1.10 [-0.63, 3.10] | 97 | -2.96 | -0.18 [-2.25, 2.23] | 0.34 | 0.17 | 7427 / -103406 / 2398 | n Y n n |
| B|rs60|SMA_100_hl2|dist40 | 1.14 [-0.40, 2.61] | 100 | -3.44 | -0.41 [-2.84, 2.27] | 0.36 | 1.27 | -10083 / -69841 / -19165 | n Y n n |
| B|rs240|HMA_377_close|dist40 | 1.11 [-0.52, 3.11] | 125 | -2.96 | 0.13 [-1.60, 2.84] | 0.57 | -0.10 | 21039 / -79316 / -10659 | n n n n |
| B|rs60|ZLEMA_377_close|dist40 | 1.35 [-0.84, 3.49] | 68 | -1.41 | 1.69 [-0.70, 3.98] | 0.96 | 0.65 | 7780 / -24462 / -3859 | n Y n n |
| B|rs240|TEMA_55_hlc3|dist40 | 1.02 [-0.37, 2.36] | 96 | -1.53 | 0.67 [-1.83, 3.77] | 0.79 | -0.39 | 1669 / -59327 / -13981 | n n n n |

## 5. By window (PRE, top 10; flat 15:55; mean net1 vs random-in-regime mean, n, CI of the effect), by year / half-year, long / short, mirror (top 10 + EMA200 refs)
| cell | 09:30-10 | 10-11 | 11-12 | 12-13 | 13-14 | PRIMARY 10-14 | 14:00-15:30 | RTH pooled |
|---|---|---|---|---|---|---|---|---|
| B|rs240|WMA_100_hl2|dist40 | -1.47 vs -2.32 (n 37; CI -3.6..6.8) | 0.31 vs -2.34 (n 48; CI -1.6..8.4) | -0.09 vs -2.02 (n 40; CI -3.2..6.3) | -0.42 vs -0.99 (n 32; CI -3.5..5.0) | 3.29 vs -0.50 (n 15; CI -1.1..12.3) | 0.47 vs -1.48 (n 134; CI -0.1..4.6) | 0.10 vs -2.25 (n 22; CI -3.8..7.3) | 0.37 vs -1.73 (n 197; CI 0.3..4.0) |
| B|rs240|WMA_50_hlc3|dist40 | -3.57 vs -3.28 (n 58; CI -3.8..3.4) | 0.21 vs -1.68 (n 67; CI -1.4..4.8) | 1.28 vs -2.57 (n 50; CI 0.4..6.7) | -5.99 vs -2.01 (n 31; CI -7.8..0.3) | -1.02 vs -2.06 (n 46; CI -1.9..4.4) | -0.57 vs -2.08 (n 188; CI -0.4..3.3) | -0.62 vs -1.01 (n 67; CI -4.3..3.6) | -1.21 vs -1.94 (n 330; CI -0.7..2.0) |
| B|time_15m|VIDYA_377_close|dist40 | -1.36 vs -1.27 (n 35; CI -4.3..4.1) | -1.20 vs -1.12 (n 37; CI -5.5..6.1) | -0.98 vs -2.46 (n 31; CI -3.2..5.7) | -0.09 vs -2.90 (n 34; CI -1.2..7.8) | -0.29 vs -2.71 (n 20; CI -0.5..6.5) | -0.74 vs -2.26 (n 120; CI -0.6..4.3) | -1.08 vs -1.46 (n 27; CI -4.8..5.5) | -0.74 vs -2.02 (n 183; CI -0.3..2.8) |
| B|rs60|VIDYA_100_hl2|dist40 | 1.06 vs -1.93 (n 41; CI -0.6..7.2) | -0.01 vs -1.92 (n 49; CI -1.6..5.5) | 0.42 vs -2.02 (n 29; CI -2.3..6.8) | -0.97 vs -2.29 (n 29; CI -4.5..6.6) | -1.44 vs -2.70 (n 37; CI -1.8..4.7) | -0.46 vs -2.22 (n 140; CI -0.2..4.0) | -0.37 vs -1.13 (n 39; CI -3.2..5.2) | 0.23 vs -1.86 (n 226; CI 0.7..3.6) |
| B|rs240|T3_34_hl2|dist40 | 1.81 vs -0.85 (n 46; CI -2.0..7.5) | -2.51 vs -2.24 (n 38; CI -4.4..2.9) | -0.00 vs -2.62 (n 25; CI -1.6..5.8) | 2.62 vs -1.89 (n 21; CI 1.5..9.1) | -1.63 vs -2.74 (n 19; CI -5.8..7.5) | -0.84 vs -2.33 (n 100; CI -0.6..3.7) | -1.11 vs -0.45 (n 53; CI -3.9..2.6) | -0.19 vs -1.72 (n 215; CI 0.1..3.0) |
| B|rs60|ZLEMA_377_hl2|dist40 | -0.59 vs -2.72 (n 58; CI -1.0..5.3) | -3.10 vs -1.61 (n 51; CI -5.5..2.7) | 3.52 vs -1.22 (n 39; CI 2.0..7.0) | 4.93 vs -1.34 (n 14; CI -0.1..14.3) | -2.03 vs -0.64 (n 17; CI -7.8..3.0) | -0.05 vs -1.24 (n 118; CI -1.3..3.3) | -1.36 vs -1.14 (n 32; CI -5.5..7.4) | -0.09 vs -1.35 (n 221; CI -0.8..3.2) |
| B|rs60|SMMA_89_hl2|dist40 | -1.44 vs -3.21 (n 66; CI -1.5..5.4) | 1.17 vs -1.06 (n 65; CI -1.7..5.8) | -2.21 vs -1.93 (n 32; CI -4.7..3.1) | -1.23 vs -1.92 (n 35; CI -3.9..5.4) | 1.15 vs -1.02 (n 36; CI -2.6..7.0) | 0.04 vs -1.49 (n 162; CI -0.6..3.7) | 0.56 vs -1.10 (n 58; CI -2.7..5.8) | -0.04 vs -1.52 (n 299; CI 0.0..3.1) |
| B|rs60|VIDYA_89_close|dist40 | -1.13 vs -1.45 (n 44; CI -3.6..4.9) | 0.43 vs -1.05 (n 52; CI -2.0..5.4) | 0.44 vs -1.74 (n 29; CI -3.0..6.3) | -2.50 vs -2.65 (n 32; CI -5.1..5.7) | -0.77 vs -2.42 (n 35; CI -1.9..5.5) | -0.55 vs -1.93 (n 143; CI -0.6..3.7) | -0.12 vs -2.10 (n 31; CI -2.6..7.0) | -0.33 vs -1.95 (n 223; CI 0.2..3.1) |
| B|rs60|ZLEMA_233_hl2|dist40 | -2.97 vs -2.92 (n 103; CI -2.9..2.8) | 0.10 vs -2.88 (n 78; CI -0.0..5.8) | -1.51 vs -2.61 (n 40; CI -2.4..4.3) | -3.43 vs -2.57 (n 41; CI -4.0..2.3) | -2.21 vs -2.50 (n 40; CI -3.5..4.8) | -1.22 vs -2.65 (n 195; CI -0.5..3.2) | -3.70 vs -1.35 (n 82; CI -4.8..-0.3) | -2.17 vs -2.35 (n 407; CI -1.1..1.4) |
| B|rs60|LSMA_377_close|dist40 | -0.48 vs -1.81 (n 59; CI -2.2..5.5) | -2.36 vs -2.69 (n 52; CI -2.5..3.7) | 0.58 vs -2.34 (n 51; CI -0.3..5.6) | 1.74 vs -1.06 (n 17; CI -1.3..7.7) | -4.20 vs -4.14 (n 29; CI -5.2..4.7) | -1.39 vs -2.60 (n 146; CI -0.5..2.9) | -1.59 vs -0.32 (n 57; CI -5.4..2.9) | -1.18 vs -2.00 (n 270; CI -0.9..2.7) |

| cell | 2024 | 2025H1 | long | short | mirror |
|---|---|---|---|---|---|
| B|rs240|WMA_100_hl2|dist40 | net 2.31 eff 2.47 (n 78) | net -2.13 eff 2.26 (n 56) | net -1.68 eff -0.29 (n 66) | net 2.54 eff 3.93 (n 70) | net -1.98 eff -0.66 (n 134) |
| B|rs240|WMA_50_hlc3|dist40 | net -0.27 eff 1.36 (n 134) | net -1.50 eff 2.22 (n 54) | net -0.83 eff 1.39 (n 82) | net -0.60 eff 1.62 (n 107) | net -1.75 eff -0.38 (n 176) |
| B|time_15m|VIDYA_377_close|dist40 | net -0.19 eff 1.84 (n 86) | net -1.50 eff 0.97 (n 34) | net -0.94 eff 1.19 (n 58) | net -0.18 eff 1.95 (n 65) | net -1.78 eff -1.23 (n 142) |
| B|rs60|VIDYA_100_hl2|dist40 | net 0.63 eff 2.69 (n 106) | net -4.49 eff -2.14 (n 34) | net -2.07 eff 0.06 (n 79) | net 1.27 eff 3.41 (n 61) | net -2.34 eff -1.56 (n 134) |
| B|rs240|T3_34_hl2|dist40 | net 0.12 eff 2.30 (n 69) | net -3.59 eff -0.20 (n 31) | net 2.79 eff 5.33 (n 43) | net -3.68 eff -1.13 (n 57) | net -1.67 eff -0.11 (n 109) |
| B|rs60|ZLEMA_377_hl2|dist40 | net 0.82 eff 1.56 (n 85) | net -1.35 eff 1.18 (n 33) | net -0.44 eff 0.78 (n 77) | net 1.12 eff 2.34 (n 43) | net -4.41 eff -2.51 (n 142) |
| B|rs60|SMMA_89_hl2|dist40 | net 0.52 eff 1.91 (n 104) | net -1.12 eff 0.68 (n 58) | net 1.36 eff 2.86 (n 81) | net -1.49 eff 0.00 (n 81) | net -3.55 eff -2.09 (n 176) |
| B|rs60|VIDYA_89_close|dist40 | net 1.36 eff 2.88 (n 108) | net -5.34 eff -3.02 (n 35) | net -2.93 eff -1.23 (n 75) | net 2.50 eff 4.20 (n 69) | net -2.49 eff -1.58 (n 154) |
| B|rs60|ZLEMA_233_hl2|dist40 | net -0.22 eff 2.33 (n 133) | net -3.43 eff -0.56 (n 62) | net -0.10 eff 2.55 (n 106) | net -2.54 eff 0.11 (n 92) | net -2.88 eff -1.77 (n 236) |
| B|rs60|LSMA_377_close|dist40 | net -1.01 eff 1.64 (n 128) | net -2.33 eff -0.03 (n 18) | net -0.61 eff 1.95 (n 98) | net -2.52 eff 0.04 (n 50) | net -0.74 eff -0.34 (n 167) |
| B|rs60|ZLEMA_233_close|dist40 | net -0.01 eff 2.46 (n 127) | net -3.77 eff -0.93 (n 59) | net 0.22 eff 2.80 (n 98) | net -2.69 eff -0.11 (n 91) | net -2.30 eff -1.19 (n 239) |
| B|rs10|VIDYA_377_close|dist40 | net 0.59 eff 1.43 (n 106) | net -0.85 eff 1.94 (n 58) | net 1.11 eff 2.41 (n 92) | net -0.85 eff 0.44 (n 75) | net -3.32 eff -1.68 (n 180) |
| B|rs240|MCG_34_hl2|dist40 | net 0.95 eff 1.95 (n 119) | net -2.03 eff 1.10 (n 85) | net 0.69 eff 2.34 (n 103) | net -1.19 eff 0.47 (n 103) | net -3.48 eff -2.13 (n 212) |

(PRE contains 2024 and 2025H1 only; 2026 is HOLD. 'mirror' = the opposite side at the same events, which must lose: it does in the cells shown.) Full 30-cell tables: out/zen/lines/B_extra.json.

## 6. Heat table: line type x lookback, close price, 5-min regime, side semantics (effect vs random-in-regime, pt/trade; cluster representatives only)
| type \ lookback | 9 | 20 | 21 | 34 | 50 | 55 | 89 | 100 | 144 | 200 | 233 | 377 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALMA | -0.3 |  |  |  |  |  | -0.3 | -0.4 | -0.3 | -0.3 | -0.4 | -0.3 |
| DEMA | -0.3 | -0.4 |  | -0.4 | -0.3 | -0.1 | -0.4 | -0.4 | -0.4 | -0.3 | -0.3 | -0.4 |
| EMA | -0.4 | -0.2 |  | -0.3 | -0.4 | -0.4 | -0.4 | -0.3 | -0.4 | -0.3 | -0.4 | -0.6 |
| FAMA |  |  |  |  |  |  |  |  |  |  |  |  |
| FRAMA | -0.5 | -0.4 | -0.2 | -0.3 | -0.7 | -0.7 | -0.1 | -0.3 | -0.2 | -0.4 | -0.3 | -0.5 |
| HMA | -0.3 | -0.2 |  | -0.6 | -0.5 | -0.5 | -0.2 | -0.3 | -0.4 | -0.5 | -0.5 | -0.5 |
| ITREND |  |  |  |  |  |  |  |  |  |  |  |  |
| KAMA | -0.7 | -0.4 |  | -0.6 | -0.4 | -0.4 | -0.6 | -0.6 | -0.4 | -0.4 | -0.4 | -0.4 |
| LSMA | -0.1 | -0.5 |  | -0.4 | -0.4 | -0.3 | -0.5 | -0.4 | -0.4 | -0.5 | -0.6 | -0.2 |
| MAMA |  |  |  |  |  |  |  |  |  |  |  |  |
| MCG |  |  | -0.2 |  |  |  |  | -0.3 |  |  |  |  |
| SMA | -0.5 | -0.2 |  | -0.3 | -0.4 | -0.3 | -0.4 | -0.4 | -0.3 | -0.4 | -0.4 | -0.6 |
| SMMA | -0.3 | -0.3 |  | -0.4 |  | -0.3 | -0.3 |  | -0.7 | -0.6 | -0.5 | -0.5 |
| T3 | -0.6 | -0.2 | -0.3 | -0.4 | -0.5 | -0.5 | -0.3 | -0.4 | -0.5 | -0.3 | -0.4 | -0.6 |
| TEMA | -0.1 | -0.3 |  | -0.4 | -0.4 | -0.4 | -0.2 | -0.3 | -0.4 | -0.3 | -0.4 | -0.3 |
| TMA | -0.3 | -0.3 |  | -0.4 | -0.4 | -0.4 | -0.4 | -0.4 | -0.4 | -0.3 | -0.4 | -0.5 |
| VIDYA | -0.5 | -0.5 |  | -0.4 | -0.4 | -0.4 | -0.5 | -0.7 | -0.5 | -0.6 | -0.6 | -0.4 |
| VWMA |  | -0.5 |  | -0.5 | -0.3 |  | -0.3 |  | -0.3 | -0.3 | -0.3 | -0.6 |
| WMA | -0.3 | -0.6 |  | -0.2 | -0.3 | -0.3 | -0.3 | -0.3 | -0.4 | -0.4 | -0.4 | -0.4 |
| ZLEMA | -0.3 | -0.3 | -0.3 | -0.5 | -0.4 | -0.3 | -0.4 | -0.3 | -0.4 | -0.5 | -0.4 | -0.4 |

(The same grid for 3m/10m/15m/30m/60m/240m is in B_pre.parquet.)

## 7. Realised stop and R:R
Stop 15.0 pt in every trade (median = p90 = 15). Median target distance of the top-10 cells: 9.5, 10.5, 10.0, 9.2, 9.4, 11.2, 11.2, 9.8, 10.0, 8.9 pt -> realised R:R about 0.6-0.9; break-even win rates 58-67%.

## 8. L6 robustness (top cells; neighbours and overlap are in LINES_D)
See DS3_ZEN_LINES_D.md for neighbour stability (13 of 20 base lines flip sign with a neighbouring lookback), mirror, 2x cost (net2 > 0 in 0 of 7,085 cells) and overlap with PE / ST / HM / WT.

## Deviations and disclosures
- Screen is on the mapped conservative basis (1-min OHLC fills; 0.05-0.13 pts/trade more conservative than 1-s on tight stops). **G10 (direct 1-s/L2 replay) was NOT run** by this agent (needs a replay worker allow-listed in the governor; request in MORNING.md). No cell can therefore be labelled CANDIDATE; the best possible label is 'screen G1-G9 pass, G10 pending'; none reached it.
- Bracket (fixed for all LINES blocks): 15-pt stop measured from the entry price (the realised stop is exactly 15.0 pt for every trade: median = p90 = 15), target = nearest confirmed 1-min swing (k=2, last 12 swings) beyond the entry at distance 5..60 pt; entries with no such target do not exist (about 48% of bar x side rows, same rule in every placebo pool). Median realised target distance and R:R are in the tables (R:R = target distance / 15, about 0.7).
- All trades come from `Z.simulate()` (table built once per entry bar x side; identity to a fresh `simulate()` on 300 random events is a unit test). `zen_struct.grid_eval` is NOT used, so the fill_mode=1 grid bug reported by D3ZF1 does not apply (market entries only).
- The one-open-trade rule is applied to each real set; the grid placebo is the exact pool expectation (unsequenced); the top cells are re-run with `Z.placebo_in_regime` / `placebo_random_dir` (100 draws) and agree with the pool expectation to within 0.1 pt in all spot checks (B top 30 table in out/zen/lines/B_top30_pre.json).
- Gate G1 rank: in the grid the rank gate is replaced by the week-block bootstrap (CI lower > 0); the full-draw rank is reported for the top cells. G2 likewise.
- By-window tables use a separate engine with entries 09:30-15:55 and flat 15:55 (so the PRIMARY row there is the 15:55-flat variant); the screen itself is flat 14:00 only (plan table). Flat-15:55 and window re-reads are counted as disclosed additions to N.
- Holdout looks used: ONE look (HOLD) + ONE X read for this block, logged in out/zen/lines/looks.jsonl and DECISIONS.md BEFORE HOLD/X were read. The 2023 X span is in memory during the screen for line warm-up but is not scored.
- Selection effects: cells chosen on PRE effect (top 30 per prereg rule); the winner's-curse is visible: PRE effects of the selected cells average +1.3 (B), +2.0 (C) pt/trade and fall to +0.5 (B), -1.2 (C) in HOLD.
- Closed-bar rule: `out/zen/lines/zl_test.log`, 24 tests, 0 failures (events, regimes, entry lines, stacks unchanged when all later bars are deleted).
- Files: code l2vast/ds3/code/zen/lines/*.py; outputs l2vast/ds3/out/zen/lines/ ; prereg l2vast/ds3/prereg/ZEN_LINES_{B,C,D}_prereg.md(+.sha256).

DONE LINES_B
