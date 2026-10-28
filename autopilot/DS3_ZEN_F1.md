# DS3_ZEN_F1 - T-ZEN family F1: regimes x levels x T0 touch-limit x fixed brackets (D3ZF1, 2026-10-28)

Research only; screen on the mapped conservative basis (1-min OHLC fills, $4.84 RT, 10-lot unit = $200/pt, pts/trade next to dollars). PRIMARY window 10:00-14:00 NY, PRE 2024-02..2025-06 for the screen; HOLD 2025-07-01..2026-02-06 and X 2023-04..2024-01 each looked at once for the top 30 (looks logged in DECISIONS.md before reading). UNTOUCHED not read.

## 1. Verdict

**No F1 cell survives: the pullback location (touch of any of 22 levels with a resting limit) does not beat random-in-regime. Across 32550 scored cells with n >= 100 the MEAN effect vs random-in-regime is -1.85 pts/trade (median -2.02; only 12.5% of cells are above zero; 48 cells have a CI lower bound > 0 against 814 expected by chance alone); the best PRE cell (R8_d40_a30 / L2e40_t5 / T0at / flat 955 / R1_60) shows +14.49 pts/trade (week-block MDE80 16.5), the reality-check adjusted p over all cells is 0.67, and in the single HOLD look the 30 selected cells average -2.90 pts/trade effect (8 of 30 positive, 0 with CI lower > 0).**

Gates: 1 of 30 pass G1-G5 on PRE; 0 pass G6 (HOLD); none pass G6+G7+G8; G10 (direct 1-s/L2 replay) was not run by this agent, so no cell can carry a CANDIDATE label here. Answer to the family question (plan section 9): the touch-limit pullback entries at these levels are worse than "trend regime + bracket" taken at a random minute, on average; the few cells that look positive in PRE are small-n selections from 35,640 (R8 with distance <= 20 pt filter, 90-140 trades) and fall apart in HOLD.

## 2. Counts block (descriptive, before any P&L)

Touch events and T0 fills per week (PRE, 75 weeks, window 10:00-14:00, regime R1; T0at; fills = limit at the line with a 1-tick trade-through inside 3 bars). Pool = every R1-qualified minute (random-in-regime candidates): 86252 minutes in PRE.

| level | touch events | fills (T0at) | fill rate | fills/wk | fill rate T0pre1 |
|---|---|---|---|---|---|
| L1_t2 | 1754 | 1320 | 0.75 | 17.6 | 0.79 |
| L1_t5 | 1800 | 1102 | 0.61 | 14.7 | 0.66 |
| L2e40_t2 | 3884 | 2884 | 0.74 | 38.5 | 0.79 |
| L2e40_t5 | 3916 | 2338 | 0.60 | 31.2 | 0.65 |
| L2e50_t2 | 3533 | 2639 | 0.75 | 35.2 | 0.79 |
| L2e50_t5 | 3577 | 2122 | 0.59 | 28.3 | 0.64 |
| L3e20_t2 | 2499 | 1873 | 0.75 | 25.0 | 0.80 |
| L3e20_t5 | 2509 | 1512 | 0.60 | 20.2 | 0.65 |
| L3e50_t2 | 1546 | 1168 | 0.76 | 15.6 | 0.79 |
| L3e50_t5 | 1673 | 1021 | 0.61 | 13.6 | 0.65 |
| L4_t2 | 1597 | 1206 | 0.76 | 16.1 | 0.79 |
| L4_t5 | 1710 | 1062 | 0.62 | 14.2 | 0.66 |
| L5_t2 | 2151 | 1644 | 0.76 | 21.9 | 0.80 |
| L5_t5 | 2114 | 1341 | 0.63 | 17.9 | 0.67 |
| L6m2_t2 | 1263 | 921 | 0.73 | 12.3 | 0.77 |
| L6m2_t5 | 1358 | 807 | 0.59 | 10.8 | 0.64 |
| L6m3_t2 | 1103 | 788 | 0.71 | 10.5 | 0.77 |
| L6m3_t5 | 1230 | 726 | 0.59 | 9.7 | 0.64 |
| L7k2 | 6087 | 4538 | 0.75 | 60.5 | 0.79 |
| L7k3 | 4406 | 3351 | 0.76 | 44.7 | 0.80 |
| L8_first | 21252 | 17536 | 0.83 | 233.8 | 0.86 |
| L8_second | 8158 | 6675 | 0.82 | 89.0 | 0.86 |

Regime pool sizes (minutes in PRE) and the REGIME-ONLY baseline ("trend regime + bracket" at a random minute, market entry, flat 14:00, net1 pts/trade, unsequenced expectation):

| regime | pool minutes | 20/30 | 20/60 | 1R 20 | 1R 60 | 30/60 | mean of 15 brackets (flat 14:00) | (flat 15:55) |
|---|---|---|---|---|---|---|---|---|
| R1 | 86252 | -1.89 | -1.89 | -1.73 | -0.34 | -1.46 | -1.63 | -1.61 |
| R2_20 | 86252 | -1.58 | -1.65 | -1.51 | +0.05 | -1.15 | -1.37 | -1.50 |
| R2_40 | 86252 | -1.62 | -1.72 | -1.53 | -0.06 | -1.24 | -1.43 | -1.58 |
| R2_50 | 86252 | -1.66 | -1.71 | -1.56 | -0.08 | -1.26 | -1.44 | -1.58 |
| R3 | 75075 | -1.75 | -1.71 | -1.64 | -0.01 | -1.21 | -1.46 | -1.51 |
| R4 | 86252 | -1.79 | -1.85 | -1.68 | -0.14 | -1.44 | -1.62 | -1.77 |
| R5 | 86252 | -1.78 | -1.85 | -1.70 | -0.03 | -1.42 | -1.59 | -1.75 |
| R4R5 | 79248 | -1.79 | -1.88 | -1.69 | +0.05 | -1.46 | -1.61 | -1.77 |
| R6 | 86252 | -1.74 | -1.85 | -1.66 | -0.55 | -1.44 | -1.55 | -1.70 |
| R7 | 86252 | -1.49 | -1.58 | -1.37 | +0.11 | -1.25 | -1.31 | -1.54 |
| R8 | 65408 | -1.70 | -1.55 | -1.64 | +0.37 | -1.00 | -1.34 | -1.41 |
| R1_d20_aNone | 14764 | -2.03 | -1.71 | -1.94 | -1.39 | -2.20 | -1.84 | -1.53 |
| R1_d20_a15 | 6172 | -2.16 | -1.34 | -2.03 | -1.60 | -2.24 | -1.79 | -1.25 |
| R1_d20_a30 | 4316 | -1.54 | -0.62 | -1.58 | +0.92 | -0.91 | -0.70 | -0.34 |
| R1_d40_aNone | 26383 | -2.25 | -1.81 | -2.08 | -0.83 | -1.88 | -1.99 | -1.43 |
| R1_d40_a15 | 15008 | -2.84 | -2.02 | -2.56 | -0.97 | -2.16 | -2.42 | -1.72 |
| R1_d40_a30 | 11355 | -2.60 | -1.75 | -2.42 | -0.07 | -1.79 | -2.10 | -1.62 |
| R1_dNone_a15 | 72854 | -1.93 | -1.95 | -1.74 | -0.30 | -1.48 | -1.66 | -1.71 |
| R1_dNone_a30 | 65920 | -1.89 | -2.00 | -1.73 | -0.23 | -1.52 | -1.66 | -1.79 |
| R8_d20_aNone | 6493 | -0.85 | -0.35 | -1.39 | +0.14 | -0.57 | -0.87 | -0.98 |
| R8_d20_a15 | 2161 | -0.28 | +1.72 | -1.20 | +2.49 | +1.81 | +0.61 | +1.25 |
| R8_d20_a30 | 1214 | +2.14 | +3.63 | +0.30 | +7.14 | +4.76 | +3.12 | +3.45 |
| R8_d40_aNone | 13764 | -2.05 | -1.34 | -2.13 | -0.34 | -1.23 | -1.86 | -1.39 |
| R8_d40_a15 | 6192 | -2.35 | -0.79 | -2.49 | +0.65 | -0.64 | -1.71 | -0.92 |
| R8_d40_a30 | 3860 | -1.75 | -0.44 | -2.17 | +2.02 | -0.09 | -1.16 | -0.83 |
| R8_dNone_a15 | 48979 | -1.68 | -1.57 | -1.62 | +0.79 | -1.01 | -1.31 | -1.40 |
| R8_dNone_a30 | 39861 | -1.50 | -1.48 | -1.49 | +1.06 | -0.94 | -1.20 | -1.41 |

The random comparator itself is negative at nearly every bracket (fee + the P9 conservative target correction): a bracket with a 20-pt target needs ~67-78% wins before costs. The only regimes whose plain "regime + bracket" baseline is positive are the tiny R8 cells with distance <= 20 pt and a cross older than 15-30 min (1,200-2,200 pool minutes in PRE, +2 to +7 pts at the 60-pt brackets): that is why they supply most of the top 30, and the effect of a level on top of them is measured against that already-positive pool.

## 3. Grid enumeration and screened N (from the prereg, sha256 a7960d3d... in DECISIONS.md)

27 regimes x 22 levels x 2 T0 x 17 brackets x 2 flat = **40,392 listed (N used for best-of-N language)**; 15 distinct brackets (negative-R 20/40 and 20/60 equal fixed 20x40 and 20x60) -> 35,640 distinct cells over 1,188 entry sets; scored (>= 30 PRE fills): 35400; skipped and counted (< 30 fills): 240; with n >= 100 (verdict allowed, in the top-30 pool): 32550; 30 <= n < 100 (count, not a verdict): 2850. Controls that are also tests: the "touch with market entry at the next open" control on the top 30 (30 cells, outside the 40,392; reported for explanation only). Reality check (centred max over all scored cells, 1000 week-block resamples, 75 weeks): null max p50 16.9, p95 27.9 pts/trade; best observed 14.5 -> p = 0.67. Program N 291,130 -> crude Bonferroni-scaled bound p >= 1.0 (nothing to scale).

## 4. Top-10 cells by PRE effect vs random-in-regime, regardless of verdict

Selection statistic = unsequenced grid effect (all fills); the exact columns are sequenced (one open trade) with 100 shared-seed random-in-regime draws. rir = random-in-regime mean net1 pts/trade; win = realised win rate vs cost-adjusted break-even (BE); fwd wk = forward weeks for 80% power (PRE weeks x (MDE80/effect)^2).

| # | cell (regime / level / T0 / flat / bracket) | n PRE (tr/wk) | PRE net1 pts ($/tr) | rir | effect [CI] rank | MDE80 | win vs BE | dir-effect (rank) | net2 | HOLD n / net1 / effect [CI lo] | X n / effect | adj p | fwd wk | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | R8_d40_a30 / L2e40_t5 / T0at / 955 / R1_60 | 63 (1.4) | +8.64 (+1729) | -1.42 | +10.07 [-1.55,+21.74] 1.00 | 16.5 | 0.587 vs 0.504 | +10.10 (0.91) | +6.69 | 34 / +7.17 / +5.48 [-5.7] | 55 / +5.48 | 0.67 | 201 | G1(effect +10.07, CI lo -1.55, rank 1.00); G2(dir effect +10.10, rank 0.91); G5(n 63<100: count not verdict; MDE80 16.5 vs effect +10.1); G6(HOLD eff +5.48 CI lo -5.68); G8(adj p 0.67); G10 not run |
| 2 | R8_d40_a30 / L2e40_t5 / T0pre1 / 955 / R1_60 | 69 (1.5) | +6.45 (+1289) | -1.36 | +7.81 [-1.64,+17.65] 0.95 | 13.7 | 0.580 vs 0.517 | +8.19 (0.92) | +4.56 | 35 / +5.08 / +3.00 [-7.5] | 58 / +3.82 | 0.87 | 231 | G1(effect +7.81, CI lo -1.64, rank 0.95); G2(dir effect +8.19, rank 0.92); G5(n 69<100: count not verdict; MDE80 13.7 vs effect +7.8); G6(HOLD eff +3.00 CI lo -7.54); G8(adj p 0.87); G10 not run |
| 3 | R8_d40_a30 / L2e50_t5 / T0at / 955 / R1_60 | 79 (1.6) | +4.86 (+972) | -1.54 | +6.41 [-3.34,+17.03] 0.94 | 14.7 | 0.519 vs 0.471 | +7.16 (0.86) | +2.99 | 37 / +5.48 / +3.38 [-7.5] | 58 / +8.43 | 0.98 | 395 | G1(effect +6.41, CI lo -3.34, rank 0.94); G2(dir effect +7.16, rank 0.86); G5(n 79<100: count not verdict; MDE80 14.7 vs effect +6.4); G6(HOLD eff +3.38 CI lo -7.45); G8(adj p 0.98); G10 not run |
| 4 | R1_d20_aNone / L5_t2 / T0at / 840 / R1_60 | 100 (1.7) | +8.31 (+1662) | -0.77 | +9.08 [-0.51,+18.25] 0.98 | 13.5 | 0.550 vs 0.455 | +8.95 (0.97) | +6.41 | 47 / -4.22 / -3.41 [-18.2] | 80 / +0.04 | 0.98 | 167 | G1(effect +9.08, CI lo -0.51, rank 0.98); G5(n 100; MDE80 13.5 vs effect +9.1); G6(HOLD eff -3.41 CI lo -18.24); G8(adj p 0.98); G9; G10 not run |
| 5 | R8_d20_aNone / L4_t2 / T0at / 840 / fix_T30_S60 | 101 (2.1) | +6.63 (+1327) | +0.15 | +6.48 [-0.32,+12.91] 0.99 | 9.6 | 0.703 vs 0.599 | +5.42 (0.97) | +4.28 | 27 / -11.31 / -12.51 [-28.8] | 67 / -1.67 | 0.99 | 164 | G1(effect +6.48, CI lo -0.32, rank 0.99); G5(n 101; MDE80 9.6 vs effect +6.5); G6(HOLD eff -12.51 CI lo -28.81); G7(X eff -1.67); G8(adj p 0.99); G9; G10 not run |
| 6 | R8_d20_aNone / L5_t2 / T0at / 955 / R1_60 | 81 (1.5) | +10.47 (+2094) | +1.81 | +8.65 [-1.15,+19.04] 1.00 | 14.2 | 0.580 vs 0.477 | +12.80 (0.99) | +8.50 | 43 / +7.97 / +2.50 [-10.8] | 73 / +0.69 | 0.99 | 203 | G1(effect +8.65, CI lo -1.15, rank 1.00); G5(n 81<100: count not verdict; MDE80 14.2 vs effect +8.7); G6(HOLD eff +2.50 CI lo -10.83); G8(adj p 0.99); G10 not run |
| 7 | R8_d20_aNone / L5_t2 / T0at / 840 / R1_60 | 81 (1.5) | +9.38 (+1876) | +1.43 | +7.95 [-0.77,+17.15] 1.00 | 13.1 | 0.543 vs 0.427 | +10.98 (0.98) | +7.44 | 43 / +0.93 / -0.44 [-13.0] | 73 / -4.51 | 0.99 | 203 | G1(effect +7.95, CI lo -0.77, rank 1.00); G5(n 81<100: count not verdict; MDE80 13.1 vs effect +7.9); G6(HOLD eff -0.44 CI lo -12.98); G7(X eff -4.51); G8(adj p 0.99); G9; G10 not run |
| 8 | R1_d20_aNone / L5_t2 / T0pre1 / 840 / R1_60 | 101 (1.7) | +6.42 (+1284) | -0.45 | +6.87 [-2.98,+16.36] 0.96 | 13.8 | 0.525 vs 0.452 | +7.03 (0.91) | +4.57 | 49 / -1.96 / -0.97 [-15.2] | 80 / -0.62 | 1.00 | 302 | G1(effect +6.87, CI lo -2.98, rank 0.96); G2(dir effect +7.03, rank 0.91); G5(n 101; MDE80 13.8 vs effect +6.9); G6(HOLD eff -0.97 CI lo -15.20); G7(X eff -0.62); G8(adj p 1.00); G9; G10 not run |
| 9 | R8_d20_aNone / L1_t5 / T0at / 955 / fix_T20_S60 | 97 (2.0) | +6.59 (+1317) | -1.50 | +8.09 [+3.25,+13.29] 1.00 | 7.2 | 0.835 vs 0.736 | +4.65 (0.95) | +4.12 | 35 / -1.44 / -0.18 [-10.3] | 68 / -3.66 | 1.00 | 60 | G5(n 97<100: count not verdict; MDE80 7.2 vs effect +8.1); G6(HOLD eff -0.18 CI lo -10.30); G7(X eff -3.66); G8(adj p 1.00); G9; G10 not run |
| 10 | R8_d20_aNone / L4_t2 / T0pre1 / 840 / fix_T30_S60 | 104 (2.1) | +6.49 (+1299) | +0.04 | +6.45 [-0.42,+12.87] 0.99 | 9.5 | 0.692 vs 0.588 | +4.87 (0.96) | +4.14 | 31 / -8.27 / -9.49 [-25.2] | 68 / -2.03 | 1.00 | 162 | G1(effect +6.45, CI lo -0.42, rank 0.99); G5(n 104; MDE80 9.5 vs effect +6.5); G6(HOLD eff -9.49 CI lo -25.23); G7(X eff -2.03); G8(adj p 1.00); G9; G10 not run |

PRE sequenced n is below the unsequenced grid n (overlapping approaches share a trade); n < 100 sequenced fails G5 as "count, not a verdict". The single cell passing G1-G5 in PRE: #14 R8_d20_aNone/L1_t5/T0pre1/955/fix_T20_S60 (HOLD effect -3.39).

## 5. Top 30: windows, years, half-years, long/short (random-in-regime column on every row)

### 5a. Gates and looks, all 30

| # | cell | n PRE | PRE eff | HOLD n | HOLD net1 | HOLD rir | HOLD eff [CI] | X n | X net1 | X eff | 2024 / 2025 / 2026 net1 | G1 G2 G3 G4 G5 | G6 G7 G8 G9 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | R8_d40_a30 / L2e40_t5 / T0at / 955 / R1_60 | 63 | +10.07 | 34 | +7.17 | +1.70 | +5.48 [-5.7,+17.7] | 55 | +5.28 | +5.48 | +9.5 / +5.0 / +37.9 | n n Y Y n | n Y n Y |
| 2 | R8_d40_a30 / L2e40_t5 / T0pre1 / 955 / R1_60 | 69 | +7.81 | 35 | +5.08 | +2.07 | +3.00 [-7.5,+15.3] | 58 | +3.71 | +3.82 | +6.5 / +3.5 / +37.5 | n n Y Y n | n Y n Y |
| 3 | R8_d40_a30 / L2e50_t5 / T0at / 955 / R1_60 | 79 | +6.41 | 37 | +5.48 | +2.09 | +3.38 [-7.5,+14.8] | 58 | +8.36 | +8.43 | +5.9 / +3.6 / +12.7 | n n Y Y n | n Y n Y |
| 4 | R1_d20_aNone / L5_t2 / T0at / 840 / R1_60 | 100 | +9.08 | 47 | -4.22 | -0.80 | -3.41 [-18.2,+10.3] | 80 | -1.50 | +0.04 | +12.3 / -5.6 / +9.2 | n Y Y Y n | n Y n n |
| 5 | R8_d20_aNone / L4_t2 / T0at / 840 / fix_T30_S60 | 101 | +6.48 | 27 | -11.31 | +1.20 | -12.51 [-28.8,+1.9] | 67 | -1.40 | -1.67 | +5.0 / +0.6 / -60.2 | n Y Y Y n | n n n n |
| 6 | R8_d20_aNone / L5_t2 / T0at / 955 / R1_60 | 81 | +8.65 | 43 | +7.97 | +5.47 | +2.50 [-10.8,+15.7] | 73 | -0.31 | +0.69 | +9.2 / +8.9 / +26.5 | n Y Y Y n | n Y n Y |
| 7 | R8_d20_aNone / L5_t2 / T0at / 840 / R1_60 | 81 | +7.95 | 43 | +0.93 | +1.37 | -0.44 [-13.0,+11.3] | 73 | -3.44 | -4.51 | +8.8 / +2.2 / +26.5 | n Y Y Y n | n n n n |
| 8 | R1_d20_aNone / L5_t2 / T0pre1 / 840 / R1_60 | 101 | +6.87 | 49 | -1.96 | -0.99 | -0.97 [-15.2,+12.2] | 80 | -2.12 | -0.62 | +11.4 / -5.7 / +9.2 | n n Y Y n | n n n n |
| 9 | R8_d20_aNone / L1_t5 / T0at / 955 / fix_T20_S60 | 97 | +8.09 | 35 | -1.44 | -1.25 | -0.18 [-10.3,+11.9] | 68 | -3.38 | -3.66 | +7.6 / +0.5 / -9.8 | Y Y Y Y n | n n n n |
| 10 | R8_d20_aNone / L4_t2 / T0pre1 / 840 / fix_T30_S60 | 104 | +6.45 | 31 | -8.27 | +1.21 | -9.49 [-25.2,+4.3] | 68 | -1.75 | -2.03 | +4.7 / +1.9 / -60.2 | n Y Y Y n | n n n n |
| 11 | R8_d40_a15 / L2e40_t5 / T0at / 955 / R1_60 | 136 | +6.40 | 63 | +2.36 | +2.28 | +0.07 [-10.7,+10.2] | 97 | +0.22 | +2.12 | +7.8 / +1.2 / +21.8 | n Y Y Y n | n Y n n |
| 12 | R1_d20_aNone / L5_t2 / T0at / 955 / R1_60 | 100 | +7.75 | 47 | +2.22 | -1.23 | +3.45 [-14.1,+20.6] | 80 | +0.47 | +2.01 | +12.3 / +0.1 / +9.2 | n Y Y Y n | n Y n n |
| 13 | R8_d20_aNone / L5_t2 / T0pre1 / 955 / fix_T20_S60 | 130 | +6.03 | 59 | +0.05 | -0.99 | +1.04 [-6.7,+7.3] | 103 | -2.90 | -3.22 | +4.9 / +1.0 / +15.4 | Y Y Y Y n | n n n n |
| 14 | R8_d20_aNone / L1_t5 / T0pre1 / 955 / fix_T20_S60 | 100 | +7.49 | 40 | -4.70 | -1.32 | -3.39 [-13.1,+7.1] | 79 | -1.24 | -1.54 | +6.7 / -1.4 / -9.8 | Y Y Y Y Y | n n n n |
| 15 | R8_d20_aNone / L5_t2 / T0at / 955 / fix_T20_S60 | 126 | +5.57 | 55 | -0.98 | -0.96 | -0.02 [-8.5,+6.8] | 106 | -2.07 | -2.28 | +4.2 / +0.7 / +15.4 | Y Y Y Y n | n n n n |
| 16 | R8_d40_a15 / L2e40_t5 / T0pre1 / 955 / R1_60 | 141 | +6.51 | 64 | +1.50 | +2.24 | -0.74 [-10.7,+9.2] | 98 | -1.03 | +0.96 | +8.0 / +0.6 / +21.6 | n Y Y Y n | n Y n n |
| 17 | R8_d20_aNone / L1_t5 / T0pre1 / 840 / fix_T30_S60 | 90 | +8.55 | 36 | -3.56 | +0.98 | -4.54 [-15.8,+8.1] | 74 | +0.76 | +0.24 | +8.2 / +1.3 / -3.1 | Y Y Y Y n | n Y n n |
| 18 | R8_d20_aNone / L4_t2 / T0at / 840 / fix_T25_S60 | 109 | +4.99 | 28 | -12.06 | +0.26 | -12.32 [-26.0,+1.0] | 70 | -4.11 | -4.41 | +3.9 / -1.1 / -60.2 | n n Y Y n | n n n n |
| 19 | R8_d20_aNone / L4_t2 / T0at / 840 / negR_T25_S50 | 109 | +5.71 | 30 | -10.07 | +0.01 | -10.08 [-21.8,+1.1] | 70 | -2.26 | -1.63 | +4.1 / +0.0 / -50.2 | n Y Y Y n | n n n n |
| 20 | R8_d40_a30 / L2e50_t5 / T0pre1 / 955 / R1_60 | 84 | +3.87 | 38 | +6.51 | +2.28 | +4.22 [-8.1,+19.3] | 62 | +7.01 | +7.05 | +2.8 / +4.3 / +12.5 | n n Y Y n | n Y n Y |
| 21 | R8_d20_aNone / L1_t5 / T0at / 840 / fix_T30_S60 | 87 | +8.30 | 32 | -3.06 | +1.19 | -4.25 [-16.4,+9.2] | 62 | -1.28 | -1.79 | +8.0 / +1.6 / -3.1 | Y Y Y Y n | n n n n |
| 22 | R8_d20_aNone / L5_t2 / T0pre1 / 840 / fix_T20_S60 | 130 | +5.36 | 59 | -1.33 | -1.18 | -0.15 [-7.2,+5.4] | 103 | -3.79 | -4.24 | +5.4 / -0.7 / +15.4 | Y n Y Y n | n n n n |
| 23 | R8_d20_aNone / L4_t2 / T0at / 840 / R1_40 | 95 | +8.59 | 28 | -7.89 | +0.96 | -8.84 [-19.9,+3.1] | 64 | -3.07 | -2.94 | +5.5 / +4.9 / -40.2 | Y Y Y Y n | n n n n |
| 24 | R8_d20_aNone / L5_t2 / T0at / 955 / fix_T25_S60 | 111 | +6.87 | 51 | -0.33 | +0.75 | -1.08 [-9.4,+6.8] | 92 | -2.71 | -3.48 | +5.4 / +1.5 / +20.4 | Y Y Y Y n | n n n n |
| 25 | R8_d20_aNone / L5_t2 / T0at / 840 / fix_T20_S60 | 126 | +5.08 | 55 | -2.41 | -1.24 | -1.17 [-8.5,+4.8] | 106 | -3.04 | -3.39 | +5.0 / -1.0 / +15.4 | Y n Y Y n | n n n n |
| 26 | R8_d20_aNone / L4_t2 / T0at / 955 / fix_T25_S60 | 109 | +5.54 | 28 | -6.33 | +0.93 | -7.26 [-24.4,+7.5] | 70 | -4.02 | -4.69 | +3.1 / +2.6 / -60.2 | n n Y Y n | n n n n |
| 27 | R8_d20_aNone / L4_t2 / T0pre1 / 840 / negR_T25_S50 | 112 | +5.41 | 34 | -7.37 | -0.07 | -7.30 [-19.2,+3.5] | 73 | -0.80 | -0.10 | +3.4 / +1.2 / -50.2 | n Y Y Y n | n n n n |
| 28 | R8_d20_aNone / L1_t5 / T0at / 955 / fix_T30_S60 | 87 | +7.88 | 32 | -1.20 | +2.00 | -3.21 [-17.7,+11.5] | 62 | +0.90 | -0.72 | +6.4 / +2.6 / -3.1 | Y Y Y Y n | n n n n |
| 29 | R8_d20_aNone / L1_t5 / T0pre1 / 955 / fix_T30_S60 | 90 | +8.40 | 36 | -5.05 | +1.79 | -6.84 [-20.3,+6.6] | 74 | +3.46 | +1.82 | +6.9 / -0.0 / -3.1 | Y Y Y Y n | n Y n n |
| 30 | R8_d20_aNone / L4_t2 / T0at / 955 / fix_T30_S60 | 101 | +5.61 | 27 | -9.61 | +2.30 | -11.91 [-33.1,+7.0] | 67 | -0.79 | -2.00 | +3.8 / +0.4 / -60.2 | n n Y Y n | n n n n |

G9 counted on WF = PRE + HOLD (2026 has 5 weeks). Passing G6: 0; G7: 11; G9: 5.

### 5b. By entry window (PRE; entries re-run on the 09:30-15:55 window; cell = real mean net1 / random-in-regime mean / n; flat as the cell for <= 14:00, 15:55 for 14:00-15:30 and RTH pooled)

| # | cell | 09:30-10 | 10-11 | 11-12 | 12-13 | 13-14 | 14:00-15:30 | RTH pooled |
|---|---|---|---|---|---|---|---|---|
| 1 | R8_d40_a30 / L2e40_t5 / T0at / 955 / R1_60 | - (0) | +33.4 / +13.8 (11) | -7.6 / +7.6 (14) | +1.3 / +0.2 (19) | +13.6 / +0.1 (19) | -4.8 / +6.3 (20) | +4.9 / +3.8 (93) |
| 2 | R8_d40_a30 / L2e40_t5 / T0pre1 / 955 / R1_60 | - (0) | +33.3 / +13.8 (11) | -11.2 / +7.6 (15) | +0.9 / +0.2 (21) | +10.4 / +0.1 (22) | -9.8 / +6.3 (21) | +2.7 / +3.8 (99) |
| 3 | R8_d40_a30 / L2e50_t5 / T0at / 955 / R1_60 | - (0) | +14.7 / +13.8 (11) | +1.4 / +7.6 (23) | +0.7 / +0.2 (19) | +6.8 / +0.1 (26) | +0.1 / +6.3 (24) | +3.7 / +3.8 (113) |
| 4 | R1_d20_aNone / L5_t2 / T0at / 840 / R1_60 | +2.3 / -1.1 (103) | +17.5 / +0.1 (41) | +11.4 / -2.5 (22) | -11.0 / -1.1 (13) | +17.7 / -2.3 (9) | +4.2 / +0.6 (24) | +7.2 / +0.4 (213) |
| 5 | R8_d20_aNone / L4_t2 / T0at / 840 / fix_T30_S60 | +4.8 / +4.7 (52) | +8.4 / +0.5 (35) | +10.2 / -1.2 (26) | +3.8 / +1.1 (17) | +3.3 / -2.6 (17) | -3.5 / +1.6 (22) | +3.9 / -0.3 (176) |
| 6 | R8_d20_aNone / L5_t2 / T0at / 955 / R1_60 | +6.9 / +5.6 (39) | +21.0 / +3.8 (33) | +3.1 / +0.7 (18) | -0.7 / +2.3 (15) | +30.6 / -3.4 (10) | +4.2 / +0.0 (24) | +9.7 / +0.8 (140) |
| 7 | R8_d20_aNone / L5_t2 / T0at / 840 / R1_60 | +7.4 / +5.9 (39) | +19.8 / +4.6 (33) | +10.3 / +0.6 (18) | -8.1 / +0.5 (15) | +14.5 / -4.2 (10) | +4.2 / +0.0 (24) | +9.7 / +0.8 (140) |
| 8 | R1_d20_aNone / L5_t2 / T0pre1 / 840 / R1_60 | +2.6 / -1.1 (105) | +11.3 / +0.1 (42) | +14.3 / -2.5 (21) | -14.1 / -1.1 (12) | +17.0 / -2.3 (9) | +3.8 / +0.6 (24) | +6.3 / +0.4 (214) |
| 9 | R8_d20_aNone / L1_t5 / T0at / 955 / fix_T20_S60 | -6.1 / -0.7 (10) | +3.6 / -2.3 (19) | +11.2 / -2.0 (27) | +8.6 / -0.3 (26) | +1.8 / -0.9 (25) | +3.2 / +0.1 (38) | +3.8 / -1.0 (165) |
| 10 | R8_d20_aNone / L4_t2 / T0pre1 / 840 / fix_T30_S60 | +6.0 / +4.7 (55) | +8.3 / +0.5 (35) | +9.2 / -1.2 (27) | +3.7 / +1.1 (17) | +4.4 / -2.6 (19) | -1.2 / +1.6 (21) | +4.1 / -0.3 (182) |
| 11 | R8_d40_a15 / L2e40_t5 / T0at / 955 / R1_60 | +57.3 / +11.6 (3) | +20.5 / +7.9 (46) | -14.5 / +2.8 (36) | +3.5 / +0.7 (27) | +11.1 / +1.7 (27) | -1.7 / +5.0 (36) | +5.0 / +3.2 (181) |
| 12 | R1_d20_aNone / L5_t2 / T0at / 955 / R1_60 | +3.2 / -0.5 (103) | +18.1 / -0.8 (41) | +7.7 / +0.0 (22) | -1.7 / +1.7 (13) | +29.6 / +1.5 (9) | +4.2 / +0.6 (24) | +7.2 / +0.4 (213) |
| 13 | R8_d20_aNone / L5_t2 / T0pre1 / 955 / fix_T20_S60 | -2.9 / -0.7 (47) | +8.0 / -2.3 (42) | +7.9 / -2.0 (34) | -0.5 / -0.3 (26) | +4.9 / -0.9 (25) | +0.7 / +0.1 (38) | +2.0 / -1.0 (219) |
| 14 | R8_d20_aNone / L1_t5 / T0pre1 / 955 / fix_T20_S60 | -4.1 / -0.7 (11) | +2.8 / -2.3 (18) | +8.9 / -2.0 (29) | +9.4 / -0.3 (29) | +1.0 / -0.9 (24) | +4.5 / +0.1 (45) | +4.1 / -1.0 (174) |
| 15 | R8_d20_aNone / L5_t2 / T0at / 955 / fix_T20_S60 | -3.3 / -0.7 (46) | +7.7 / -2.3 (41) | +7.6 / -2.0 (33) | -1.2 / -0.3 (25) | +4.5 / -0.9 (24) | +1.5 / +0.1 (39) | +1.9 / -1.0 (216) |
| 16 | R8_d40_a15 / L2e40_t5 / T0pre1 / 955 / R1_60 | +57.3 / +11.6 (3) | +19.6 / +7.9 (48) | -14.8 / +2.8 (37) | +4.4 / +0.7 (28) | +11.3 / +1.7 (27) | -1.9 / +5.0 (35) | +4.9 / +3.2 (184) |
| 17 | R8_d20_aNone / L1_t5 / T0pre1 / 840 / fix_T30_S60 | +3.1 / +4.7 (11) | -1.5 / +0.5 (14) | +13.3 / -1.2 (29) | +13.4 / +1.1 (24) | +2.8 / -2.6 (22) | +9.1 / +1.6 (36) | +6.5 / -0.3 (152) |
| 18 | R8_d20_aNone / L4_t2 / T0at / 840 / fix_T25_S60 | +1.5 / +2.2 (53) | +6.4 / +0.5 (39) | +6.7 / -1.3 (26) | +4.5 / +1.4 (19) | +4.9 / -1.8 (20) | -5.7 / +0.7 (25) | +2.5 / -0.7 (189) |
| 19 | R8_d20_aNone / L4_t2 / T0at / 840 / negR_T25_S50 | +1.2 / +3.0 (53) | +7.5 / -0.2 (39) | +2.5 / -2.0 (27) | +6.6 / +1.6 (19) | +4.9 / -1.8 (20) | -2.7 / +1.1 (26) | +3.0 / -0.3 (192) |
| 20 | R8_d40_a30 / L2e50_t5 / T0pre1 / 955 / R1_60 | - (0) | +18.3 / +13.8 (12) | +1.2 / +7.6 (23) | -10.2 / +0.2 (22) | +7.2 / +0.1 (27) | -0.4 / +6.3 (22) | +2.0 / +3.8 (116) |
| 21 | R8_d20_aNone / L1_t5 / T0at / 840 / fix_T30_S60 | +0.9 / +4.7 (10) | +0.5 / +0.5 (15) | +11.8 / -1.2 (26) | +13.2 / +1.1 (23) | +3.6 / -2.6 (22) | +8.7 / +1.6 (31) | +5.8 / -0.3 (143) |
| 22 | R8_d20_aNone / L5_t2 / T0pre1 / 840 / fix_T20_S60 | -1.9 / -0.0 (47) | +8.3 / -0.5 (42) | +8.0 / -1.3 (34) | -2.0 / +1.3 (26) | +4.1 / -1.1 (25) | +0.7 / +0.1 (38) | +2.0 / -1.0 (219) |
| 23 | R8_d20_aNone / L4_t2 / T0at / 840 / R1_40 | +8.7 / +4.4 (53) | +13.1 / +0.1 (29) | +8.6 / -2.3 (24) | +3.9 / +1.0 (17) | +4.0 / -2.5 (18) | +2.4 / +3.0 (24) | +6.5 / +0.5 (173) |
| 24 | R8_d20_aNone / L5_t2 / T0at / 955 / fix_T25_S60 | -0.2 / +1.6 (45) | +6.3 / -1.2 (37) | +9.9 / -2.5 (28) | -2.3 / -0.6 (20) | +10.9 / -1.5 (22) | +3.0 / +0.7 (36) | +3.3 / -0.7 (195) |
| 25 | R8_d20_aNone / L5_t2 / T0at / 840 / fix_T20_S60 | -2.2 / -0.0 (46) | +8.0 / -0.5 (41) | +7.8 / -1.3 (33) | -2.7 / +1.3 (25) | +4.0 / -1.1 (24) | +1.5 / +0.1 (39) | +1.9 / -1.0 (216) |
| 26 | R8_d20_aNone / L4_t2 / T0at / 955 / fix_T25_S60 | +1.5 / +1.6 (53) | +6.4 / -1.2 (39) | +4.0 / -2.5 (26) | +5.4 / -0.6 (19) | +5.6 / -1.5 (20) | -5.7 / +0.7 (25) | +2.5 / -0.7 (189) |
| 27 | R8_d20_aNone / L4_t2 / T0pre1 / 840 / negR_T25_S50 | +2.3 / +3.0 (56) | +7.4 / -0.2 (39) | +1.9 / -2.0 (28) | +5.0 / +1.6 (19) | +5.5 / -1.8 (22) | -3.6 / +1.1 (23) | +2.6 / -0.3 (196) |
| 28 | R8_d20_aNone / L1_t5 / T0at / 955 / fix_T30_S60 | +0.9 / +4.1 (10) | +1.4 / -0.5 (15) | +13.9 / -2.0 (26) | +8.4 / -0.8 (23) | -0.3 / -2.3 (22) | +8.7 / +1.6 (31) | +5.8 / -0.3 (143) |
| 29 | R8_d20_aNone / L1_t5 / T0pre1 / 955 / fix_T30_S60 | +3.1 / +4.1 (11) | -0.6 / -0.5 (14) | +15.2 / -2.0 (29) | +9.1 / -0.8 (24) | -0.6 / -2.3 (22) | +9.1 / +1.6 (36) | +6.5 / -0.3 (152) |
| 30 | R8_d20_aNone / L4_t2 / T0at / 955 / fix_T30_S60 | +4.8 / +4.1 (52) | +8.4 / -0.5 (35) | +7.7 / -2.0 (26) | +0.9 / -0.8 (17) | +1.1 / -2.3 (17) | -3.5 / +1.6 (22) | +3.9 / -0.3 (176) |

The sub-window tables describe the same PRE sample; no best-window claim is made (it would add 240 to N).

### 5c. Long / short split and half-year (WF) for the top 10

| # | PRE long n / net1 | PRE short n / net1 | HOLD long n / net1 | HOLD short n / net1 | WF by half-year (n, net1 pts) |
|---|---|---|---|---|---|
| 1 | 35 / +3.47 | 28 / +15.11 | 17 / +6.49 | 17 / +7.86 | 2024H1: 23, +4.3; 2024H2: 23, +14.7; 2025H1: 17, +6.4; 2025H2: 31, +4.2; 2026H1: 3, +37.9 |
| 2 | 40 / +2.14 | 29 / +12.39 | 18 / +2.45 | 17 / +7.86 | 2024H1: 27, -1.1; 2024H2: 25, +14.7; 2025H1: 17, +6.3; 2025H2: 32, +2.0; 2026H1: 3, +37.5 |
| 3 | 45 / +0.65 | 34 / +10.44 | 17 / +14.30 | 20 / -2.02 | 2024H1: 30, +1.8; 2024H2: 29, +10.1; 2025H1: 20, +1.9; 2025H2: 33, +4.6; 2026H1: 4, +12.7 |
| 4 | 50 / +6.78 | 50 / +9.85 | 27 / -2.27 | 20 / -6.84 | 2024H1: 34, +3.7; 2024H2: 43, +19.2; 2025H1: 23, -5.1; 2025H2: 42, -5.8; 2026H1: 5, +9.2 |
| 5 | 61 / +11.11 | 40 / -0.20 | 7 / -21.59 | 20 / -7.71 | 2024H1: 38, +4.0; 2024H2: 41, +6.0; 2025H1: 22, +12.4; 2025H2: 26, -9.4; 2026H1: 1, -60.2 |
| 6 | 38 / +5.11 | 43 / +15.21 | 24 / +8.68 | 19 / +7.08 | 2024H1: 33, -4.3; 2024H2: 32, +23.1; 2025H1: 16, +15.7; 2025H2: 39, +6.1; 2026H1: 4, +26.5 |
| 7 | 38 / +9.19 | 43 / +9.54 | 24 / +4.86 | 19 / -4.03 | 2024H1: 33, -2.5; 2024H2: 32, +20.5; 2025H1: 16, +11.7; 2025H2: 39, -1.7; 2026H1: 4, +26.5 |
| 8 | 51 / +5.38 | 50 / +7.47 | 28 / -0.25 | 21 / -4.25 | 2024H1: 34, +3.9; 2024H2: 44, +17.2; 2025H1: 23, -10.4; 2025H2: 44, -3.2; 2026H1: 5, +9.2 |
| 9 | 62 / +6.63 | 35 / +6.50 | 11 / -2.38 | 24 / -1.00 | 2024H1: 35, +4.3; 2024H2: 43, +10.2; 2025H1: 19, +2.5; 2025H2: 32, -0.7; 2026H1: 3, -9.8 |
| 10 | 64 / +10.83 | 40 / -0.45 | 9 / -11.22 | 22 / -7.07 | 2024H1: 40, +3.4; 2024H2: 41, +5.9; 2025H1: 23, +12.9; 2025H2: 30, -6.5; 2026H1: 1, -60.2 |

## 6. Marginals over the whole grid (PRE, cells with n >= 100, effect vs random-in-regime pts/trade, unsequenced; mean over cells, share of cells > 0)

**by T0**

| T0 | cells | mean effect | share >0 | mean n | mean target-first win | mean BE |
|---|---|---|---|---|---|---|
| T0at | 16170 | -1.72 | 0.13 | 1659 | 0.554 | 0.663 |
| T0pre1 | 16380 | -1.98 | 0.12 | 1734 | 0.547 | 0.663 |

**by flat**

| flat | cells | mean effect | share >0 | mean n | mean target-first win | mean BE |
|---|---|---|---|---|---|---|
| 840 | 16275 | -1.69 | 0.13 | 1697 | 0.515 | 0.663 |
| 955 | 16275 | -2.00 | 0.12 | 1697 | 0.586 | 0.663 |

**by level**

| level | cells | mean effect | share >0 | mean n | mean target-first win | mean BE |
|---|---|---|---|---|---|---|
| L1_t2 | 1500 | -2.50 | 0.06 | 863 | 0.533 | 0.663 |
| L1_t5 | 1500 | -1.67 | 0.14 | 729 | 0.553 | 0.663 |
| L2e40_t2 | 1560 | -2.08 | 0.06 | 1789 | 0.542 | 0.663 |
| L2e40_t5 | 1470 | -1.17 | 0.19 | 1534 | 0.568 | 0.663 |
| L2e50_t2 | 1560 | -2.18 | 0.07 | 1641 | 0.539 | 0.663 |
| L2e50_t5 | 1470 | -1.01 | 0.22 | 1396 | 0.569 | 0.663 |
| L3e20_t2 | 1560 | -1.92 | 0.15 | 1188 | 0.542 | 0.663 |
| L3e20_t5 | 1560 | -1.16 | 0.23 | 976 | 0.563 | 0.663 |
| L3e50_t2 | 1500 | -2.55 | 0.10 | 744 | 0.530 | 0.663 |
| L3e50_t5 | 1500 | -2.10 | 0.10 | 655 | 0.544 | 0.663 |
| L4_t2 | 1440 | -0.63 | 0.30 | 827 | 0.577 | 0.663 |
| L4_t5 | 1440 | -0.40 | 0.35 | 762 | 0.583 | 0.663 |
| L5_t2 | 1440 | -1.94 | 0.17 | 1139 | 0.547 | 0.663 |
| L5_t5 | 1290 | -1.58 | 0.16 | 1010 | 0.571 | 0.663 |
| L6m2_t2 | 1380 | -2.89 | 0.08 | 644 | 0.539 | 0.663 |
| L6m2_t5 | 1380 | -2.00 | 0.10 | 561 | 0.556 | 0.663 |
| L6m3_t2 | 1260 | -2.34 | 0.11 | 607 | 0.548 | 0.663 |
| L6m3_t5 | 1260 | -2.48 | 0.08 | 543 | 0.553 | 0.663 |
| L7k2 | 1620 | -1.60 | 0.03 | 2721 | 0.546 | 0.663 |
| L7k3 | 1620 | -1.27 | 0.12 | 2042 | 0.555 | 0.663 |
| L8_first | 1620 | -2.83 | 0.00 | 9524 | 0.521 | 0.663 |
| L8_second | 1620 | -2.37 | 0.00 | 3839 | 0.536 | 0.663 |

**by regime**

| regime | cells | mean effect | share >0 | mean n | mean target-first win | mean BE |
|---|---|---|---|---|---|---|
| R1 | 1320 | -2.23 | 0.00 | 2737 | 0.557 | 0.663 |
| R1_d20_a15 | 1260 | -1.07 | 0.33 | 347 | 0.547 | 0.663 |
| R1_d20_a30 | 1050 | -2.84 | 0.10 | 257 | 0.526 | 0.663 |
| R1_d20_aNone | 1320 | -0.13 | 0.47 | 584 | 0.566 | 0.663 |
| R1_d40_a15 | 1320 | -1.70 | 0.14 | 694 | 0.539 | 0.663 |
| R1_d40_a30 | 1290 | -2.47 | 0.06 | 520 | 0.521 | 0.663 |
| R1_d40_aNone | 1320 | -1.34 | 0.16 | 1005 | 0.554 | 0.663 |
| R1_dNone_a15 | 1320 | -2.55 | 0.00 | 2394 | 0.552 | 0.663 |
| R1_dNone_a30 | 1320 | -2.80 | 0.00 | 2138 | 0.547 | 0.663 |
| R2_20 | 1320 | -2.26 | 0.01 | 3056 | 0.560 | 0.663 |
| R2_40 | 1320 | -2.32 | 0.01 | 2970 | 0.557 | 0.663 |
| R2_50 | 1320 | -2.32 | 0.00 | 2939 | 0.557 | 0.663 |
| R3 | 1320 | -2.20 | 0.00 | 2424 | 0.560 | 0.663 |
| R4 | 1320 | -1.98 | 0.04 | 2756 | 0.556 | 0.663 |
| R4R5 | 1320 | -1.96 | 0.04 | 2613 | 0.557 | 0.663 |
| R5 | 1320 | -2.39 | 0.01 | 3040 | 0.554 | 0.663 |
| R6 | 1320 | -2.59 | 0.00 | 2653 | 0.552 | 0.663 |
| R7 | 1320 | -2.39 | 0.01 | 2849 | 0.559 | 0.663 |
| R8 | 1320 | -1.55 | 0.15 | 1943 | 0.559 | 0.663 |
| R8_d20_a15 | 540 | -1.50 | 0.21 | 197 | 0.551 | 0.663 |
| R8_d20_a30 | 240 | -3.97 | 0.00 | 141 | 0.521 | 0.663 |
| R8_d20_aNone | 1320 | +0.54 | 0.61 | 267 | 0.575 | 0.663 |
| R8_d40_a15 | 1170 | -0.88 | 0.33 | 313 | 0.536 | 0.663 |
| R8_d40_a30 | 930 | -2.31 | 0.08 | 219 | 0.505 | 0.663 |
| R8_d40_aNone | 1320 | -0.81 | 0.34 | 519 | 0.549 | 0.663 |
| R8_dNone_a15 | 1200 | -1.61 | 0.14 | 1639 | 0.551 | 0.663 |
| R8_dNone_a30 | 1110 | -1.94 | 0.10 | 1410 | 0.546 | 0.663 |

**by bracket**

| bracket | cells | mean effect | share >0 | mean n | mean target-first win | mean BE |
|---|---|---|---|---|---|---|
| R1_20 | 2170 | -1.32 | 0.12 | 1697 | 0.437 | 0.539 |
| R1_30 | 2170 | -1.76 | 0.11 | 1697 | 0.425 | 0.526 |
| R1_40 | 2170 | -2.03 | 0.11 | 1697 | 0.407 | 0.519 |
| R1_60 | 2170 | -2.78 | 0.10 | 1697 | 0.336 | 0.513 |
| fix_T15_S40 | 2170 | -1.81 | 0.10 | 1697 | 0.660 | 0.766 |
| fix_T15_S60 | 2170 | -1.71 | 0.12 | 1697 | 0.726 | 0.831 |
| fix_T20_S30 | 2170 | -1.48 | 0.13 | 1697 | 0.537 | 0.636 |
| fix_T20_S40 | 2170 | -1.67 | 0.13 | 1697 | 0.600 | 0.699 |
| fix_T20_S60 | 2170 | -1.53 | 0.17 | 1697 | 0.668 | 0.777 |
| fix_T25_S40 | 2170 | -1.83 | 0.13 | 1697 | 0.540 | 0.644 |
| fix_T25_S60 | 2170 | -1.88 | 0.15 | 1697 | 0.609 | 0.730 |
| fix_T30_S40 | 2170 | -1.98 | 0.11 | 1697 | 0.487 | 0.596 |
| fix_T30_S60 | 2170 | -2.06 | 0.15 | 1697 | 0.557 | 0.688 |
| negR_T15_S45 | 2170 | -1.93 | 0.10 | 1697 | 0.681 | 0.786 |
| negR_T25_S50 | 2170 | -1.93 | 0.14 | 1697 | 0.581 | 0.693 |

Target-first win is a lower-bound proxy for the win rate in the screen (flat exits are not counted as wins); exact win rates for the top 30 are in section 4/5.

## 7. Realised stop distribution and R:R

Fixed-point brackets: the realised stop is the bracket stop (20-60 pt) by construction (gap-through-stop fills are at the open: realised loss can be larger, reason code 0 exits are in the trade frames); realised R:R = target/stop of the cell (0.25-1.0; the 1R cells 1.0). Median/p90 realised stop = the bracket stop. No structural stops in F1.

## 8. Deviations and disclosures

- Screen is on the mapped conservative basis; 1-min bars are 0.05-0.13 pts/trade more conservative than the 1-s path for tight stops (plan section 3); F1 brackets are 15-60 pt so the bias is small against MDEs of 7-16 pts.
- T0 is a causal reading: the limit is placed at the close of the touch bar j at the level value of bar j (off 0) or 1 pt on the price side of it (off 1), live 3 bars, 1-tick trade-through, tick-rounded conservative (buy down, sell up). The brief says "touch = the closed bar extreme reaches the line within tolerance"; with a limit that is a RETURN to the line after the approach. Expiry 3, new-approach rule (previous bar clear of line+tol), L7 tol 2, L8 touch from the lib FVG first/second entry, L5 = VWAP +/- 1 sigma on the with-trend side: all assumed where the addenda are silent.
- The random-in-regime comparator is a MARKET entry at the next open of every regime-qualified minute (as the brief prescribes), while T0 trades are limit fills. A limit fill is selected on price moving against the entry first (adverse selection) and gets a better entry price, so part of every T0 effect is fill mechanics rather than location. Explanatory control on the top 30 only: "same touch signals, market entry at the next open, same bracket" (PRE_mkt_touch_effect in f1_top30_final.csv): mean PRE effect +3.39 vs +6.93 for the limit version, i.e. about half of the PRE effect of the selected cells is the limit fill and half survives with market entry; neither survives HOLD. (30 extra control cells, disclosed in N.)
- Grid-screen real trades are NOT sequenced (overlapping approaches each count; dependence handled by the week-block bootstrap); the top 30 are re-run with the one-open-trade rule, which lowers n (12 of 30 fall below n = 100 sequenced: count, not a verdict for G5) and moves the effect by 1.3 pts on average (max 4.4) against the grid value.
- Lib bug (reported, not edited): zen_struct._grid with fill_mode=1 builds the running maximum from the fill bar, so a spike in the fill bar counts as a target hit from the next bar (lib treats the target as not live in the fill bar). F1 uses a corrected copy (f1_mod._grid_f1, identical to simulate() on all 15 brackets for limit and market entries; tests f1_test.log 7/7). Any other family using grid_eval with limit entries (fill_mode=1) and fixed/absolute targets is affected.
- Selection effects: 40,392 listed cells, top 30 chosen on PRE grid effect with n >= 100; ties between brackets of the same entry set are NOT thinned (the 30 are 14 distinct entry sets). Two regimes (R8 with distance <= 20/40) supply 27 of the 30 and have 6-15k pool minutes, so their cells are small-n.
- Holdout looks used: 1 HOLD (30 cells), 1 X (30 cells); the PRE columns in section 5a come from the stage-2 full-sample run for consistency (take rates differ slightly), the gate columns G1-G5 use the stage-1 PRE-only run that was hashed in the PREHOLD text.
- X span: ES SMT etc. not relevant. 2023 bars are used for EMA warm-up only before 2023-04.
- G10 (direct 1-s/L2 replay) not run (no replay launched; governor allow-list belongs to main). No spec is written because nothing passes.

## 9. Files

- code: l2vast/ds3/code/zen/f1/{f1_mod,f1_exact,f1_test,f1_screen,f1_rc,f1_stage1,f1_prehold,f1_stage2,f1_report}.py (tests: l2vast/ds3/out/zen/f1/f1_test.log)
- prereg: l2vast/ds3/prereg/ZEN_F1_main_prereg.md (+ .sha256, ZEN_F1_main_cells.csv.gz); PREHOLD: autopilot/DS3_ZEN_F1_PREHOLD.md
- PRE tables for downstream families (l2vast/ds3/out/zen/f1/): f1_pre_all_cells.csv.gz (35,640 distinct cells: n, real, random-in-regime, effect, CI, MDE80, adjusted p, win vs BE), f1_pre_top30_grid.csv, f1_top30_final.csv (stage-1 + HOLD + X metrics), f1_pre_grid.pkl (per-week sums), f1_stage1_windows.pkl, f1_stage1_trades.pkl, f1_stage2_real.pkl (sequenced trade frames of the top 30)

DONE F1
