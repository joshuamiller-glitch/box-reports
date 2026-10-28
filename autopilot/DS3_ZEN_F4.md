# DS3_ZEN_F4 - T-ZEN family F4: VWAP-band reversals, Z5 SD-extension band, SMT, extension targets (D3ZF4, 2026-10-28)

**1. Verdict: F4 is DEAD at the screen, nothing to carry. Of 1,038 cells (screened N = 1,038), 436 have n >= 100 PRE trades and NONE has a positive mean at both 1x and 2x cost (best raw 1x mean +1.91 pts/trade, 2x -0.27); the median of all 972 band cells is -2.48 pts/trade (about -$500 per 10-lot trade). The 15 n>=100 cells that beat the random-in-regime pool with CI lower > 0 (effect up to +5.4 pts vs a pool that loses ~5 pts, MDE80 2.7-5.9 pts, best-of-N White reality-check adjusted p >= 0.58) are a "trigger vs random reversal minute" artefact: against random direction on the same minutes the best cells are NEGATIVE (-0.9..-2.8 pts for the +-3 sigma T1 cluster, rank 0.2-0.4, i.e. the same minutes traded WITH the move do better than against it). The top 30 got their one HOLD look: 3 of 30 have HOLD effect > 0, 0 have CI lower > 0, mean HOLD net -3.2 pts/trade (PRE +0.05); 0 pass G9; G10 (direct 1-s/L2 replay) not run. SMT (ES vs NQ) as a filter on ZM1-3 and as a trigger at the 4H FVG: 0 of the 28 cells with n >= 100 has a positive net (best -0.65 pts/trade; effects vs pool -0.3..+1.8 pts, all inside MDE80 2.2-3.5; 8 more SMTZM cells have n < 100). SD-extension targets (-1.5/-2.25/-4) on E1-E5: all 30 cells have negative net (-0.6..-2.5 pts/trade) and effect vs random-in-regime -2.1..+0.1 (none significant). Label: no LEAD, no CONFIRMED, no best-of-F.**

## 2. Counts block (descriptive, no P&L, PRE 2024-02-01..2025-06-30 = 73.6 weeks, entry window 10:00-14:00, files l2vast/ds3/out/zen/f4/desc_counts_PRE.csv, desc_validity_PRE.csv, desc_PRE.log)

Definitions fixed before these counts (see prereg): band = RTH-anchored (09:30) session VWAP +-k*sd (volume-weighted sd of hlc3, valid after 30 bars); a TOUCH = FRESH cross (the bar's high/low reaches the band and the previous bar's did not); trigger window = the touch bar and the next 5 bars; one signal per touch episode; 5m EMA200 agrees = R1 side equals the reversal side at the signal bar.
One definition was changed after seeing counts and bracket geometry (never P&L): the first draft counted every bar beyond the band as a touch (T0 = 11,819 signals for +-2 sigma, "none"; Z5 stale-leg bands gave median band+10 stops of 70 pt); the fresh-cross rule replaced it (T0 = 1,989). Disclosed, counts only.

Signals in PRE (long+short) and per week, by band family, condition and trigger (A5 = 5m EMA200 agrees, none = no condition):

| family | cond | T0 | T1 | T2 | T3 | T4 | T5 | T6 | T7 | T8 | pool (reversal regime bars) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| +-2 sigma | A5 | 307 | 302 | 58 | 58 | 35 | 217 | 170 | 20 | 43 | 1,706 |
| +-2 sigma | none | 1,989 | 1,793 | 190 | 267 | 145 | 954 | 855 | 61 | 259 | 10,722 |
| +-3 sigma | A5 | 25 | 25 | 2 | 4 | 1 | 17 | 21 | 1 | 10 | 142 |
| +-3 sigma | none | 194 | 191 | 16 | 23 | 6 | 103 | 93 | 3 | 53 | 1,096 |
| Z5 -2.25 SD band | A5 | 276 | 243 | 39 | 43 | 11 | 164 | 149 | 12 | 85 | 1,609 |
| Z5 -2.25 SD band | none | 867 | 737 | 91 | 109 | 26 | 430 | 377 | 17 | 224 | 4,907 |

SMT / ZM / E cells (signals in PRE): SMT filter on ZM1/ZM2/ZM3 (1-min SMT) 998 / 196 / 914, (5-min SMT) 965 / 206 / 883; SMT standalone at an active same-direction 4H FVG: 827 (1-min), 404 (5-min). Extension-target entry cells (hold-candle signals): E1 6,298, E2 3,725, E3 2,989, E4 5,717, E5 10,972. SMT state share of 10:00-14:00 bars: bull 6.1% / bear 6.4% (1m), 6.0% / 6.4% (5m); ES 1-min present for 99.9% of PRE bars (ES table starts 2023-08, so SMT covers only 2023-08..2024-01 of the X span).
Of 1,038 cells, 522 have fewer than 100 PRE signals (before the validity skip) and get a COUNT, not a verdict (G5). Bracket validity (stop or target distance < 2 pt or on the wrong side = row skipped and counted, in the real set AND the placebo pool): the EMA200 target is invalid in 9-37% (+-2/3 sigma) and 26-71% (Z5) of reversal-regime bars; VWAP target 4-16% (Z5 31-67%); 20-pt target 0-15% (Z5 5-23%).

## 3. Grid enumeration and screened N (copied from the prereg, sha256 b0e17c657e0dafbe2b9cf017a7e9dbe3b4f5eb532fdecb2faac6b461b07049a6; cell table ZEN_F4_cells.csv sha256 64441c4a15ec28b74901ed359dd812b1722d857a83bd29747a7a2e1fcaee6205)

- BAND 972 = band family {+-2 sigma, +-3 sigma, Z5 -2.25 SD band} 3 x condition {5m EMA200 agrees, none} 2 x trigger {T0 touch, T1..T8} 9 x target {1m EMA200, VWAP, 20 pt} 3 x stop {band+10, band+20, extreme} 3 x flat {14:00, 15:55} 2 (= plan split 648 + 324).
- SMTZM 24 = ZM1/2/3 x SMT {1m, 5m} x bracket {15/20, 40/20} x flat 2. SMT4H 12 = {1m, 5m} x bracket {15/20, 30/20, 40/20} x flat 2. EXT 30 = k {1.5, 2.25, 4} x E1-E5 x flat 2 (stop 15). Total 1,038 = screened N (program N 291,130).
- Scored: 1,038 of 1,038 (none skipped as cells). Cells with a verdict allowed (n >= 100 sequenced valid trades PRE): 436; counts only: 602 (BAND 594, SMTZM 8). Rows skipped by the validity rule (stop or target distance < 2 pt or wrong side), counted per cell in stage1_cells.csv (n_bad, pool_bad); typical top-cell skips 2-9 real rows (+-3 sigma) and 161-172 of the Z5 rows.
- Screen results (PRE, pool-expectation placebo): G1 (effect > 0, CI lower > 0) in 49 cells, 15 of them with n >= 100 (+-3 sigma "none" 11, +-2 sigma A5 4; MDE80 2.7-5.9); G3 (net > 0 at 1x AND 2x) in 0 cells with n >= 100 (106 BAND cells with n < 100 pass G3, a count only); G5 (n >= 100 and effect >= MDE80) 2 cells. White reality check over the N: adjusted p of the best cell 0.996 (cells with >= 30 trades) / 0.579 (>= 100 trades). Trigger means (BAND, n>=100): T0 mean1 -2.0, T1 -1.7, T2 -4.5, T3 -2.3, T4 -1.3, T5 -2.5, T6 -3.3, T8 -2.2 pts/trade (T7 has < 100 trades everywhere). Effect vs random-in-regime averages: T0 +0.8, T1 +0.9, T2..T8 -3.3..-0.1, so the "reaction" triggers do not beat the bare touch (T0) in the pool metric either.
- Part means (n>=100 cells): VWAP bands with 5m EMA200 agreeing (+-2 sigma A5) mean1 -3.4; without the condition -2.1; Z5 band A5 -2.9, none -2.4; +-3 sigma none -0.8 (best family, still negative). The condition "5m EMA200 agrees" makes the bands WORSE, not better.

## 4. Top 10 by effect vs random-in-regime (n >= 100), regardless of verdict
RIR = random-in-regime (pool expectation in the screen; PRE effect/CI in this table is the pool-expectation bootstrap, the rank in the failed-gate text is from the 100-draw machinery). Forward weeks = 73.6 x (MDE80/effect)^2 (80% power planning number). HOLD (2025-07-01..2026-02-06) and X (2023-04..2024-01) were read ONCE for these 30 (looks logged in DECISIONS.md before the run).

| rank | cell | n PRE | trades/wk | win / BE | PRE mean1 / 2x | PRE eff vs RIR [CI] (MDE80) | HOLD n, mean1, eff [CI] | X eff | RC p (n>=30 / >=100) | fwd weeks | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | B_vwap3_none_T1_tema_s20_f955 | 164 | 2.23 | 0.366 / 0.369 | -0.28 / -1.87 | 5.36 [1.88, 9.23] (5.19) | 63, 1.92, 1.18 [-3.91, 6.39] | 2.12 | 0.996 / 0.579 | 69 | G1 (PRE eff 5.19 CI lo 2.09 rank 0.93); G2 (vs random direction -2.76, lo -10.75, rank 0.31); G3 (1x -0.28, 2x -1.87); G4 (win 0.366 vs BE 0.369); G6 (HOLD eff 1.18 lo -3.91); G8 (RC p 1.00; n>=100 variant 0.58); G9 (positive years 2); G10 not run |
| 2 | B_vwap3_none_T1_tema_s10_f955 | 178 | 2.42 | 0.292 / 0.286 | 0.42 / -0.99 | 5.31 [1.26, 9.50] (5.93) | 66, -2.45, -4.61 [-12.06, 2.74] | 0.55 | 0.997 / 0.592 | 92 | G2 (vs random direction -2.35, lo -9.24, rank 0.28); G3 (1x 0.42, 2x -0.99); G5 (eff 5.31 < MDE80 5.93); G6 (HOLD eff -4.61 lo -12.06); G8 (RC p 1.00; n>=100 variant 0.59); G9 (positive years 2); G10 not run |
| 3 | B_z5_A5_T0_tvwap_s10_f955 | 100 | 1.36 | 0.320 / 0.354 | -1.22 / -2.73 | 5.28 [-1.00, 11.86] (9.18) | 49, -3.51, -1.99 [-7.48, 3.44] | -0.08 | 0.997 / 0.602 | 222 | G1 (PRE eff 5.53 CI lo 0.12 rank 0.91); G2 (vs random direction 0.37, lo -2.10, rank 0.54); G3 (1x -1.22, 2x -2.73); G4 (win 0.320 vs BE 0.354); G5 (eff 5.28 < MDE80 9.18); G6 (HOLD eff -1.99 lo -7.48); G7 (X eff -0.08); G8 (RC p 1.00; n>=100 variant 0.60); G9 (positive years 1); G10 not run |
| 4 | B_vwap3_none_T1_tema_s10_f840 | 178 | 2.42 | 0.315 / 0.311 | 0.25 / -1.17 | 4.84 [1.01, 8.37] (5.25) | 66, -0.96, -3.52 [-10.97, 3.85] | 0.40 | 0.999 / 0.714 | 87 | G2 (vs random direction -0.85, lo -5.51, rank 0.38); G3 (1x 0.25, 2x -1.17); G5 (eff 4.84 < MDE80 5.25); G6 (HOLD eff -3.52 lo -10.97); G8 (RC p 1.00; n>=100 variant 0.71); G9 (positive years 2); G10 not run |
| 5 | B_vwap3_none_T1_tema_s20_f840 | 164 | 2.23 | 0.390 / 0.399 | -0.64 / -2.22 | 4.77 [1.81, 8.09] (4.46) | 63, 2.58, 1.44 [-3.77, 6.62] | 1.94 | 1.000 / 0.729 | 64 | G1 (PRE eff 4.69 CI lo 1.91 rank 0.93); G2 (vs random direction -1.79, lo -7.37, rank 0.27); G3 (1x -0.64, 2x -2.22); G4 (win 0.390 vs BE 0.399); G6 (HOLD eff 1.44 lo -3.77); G8 (RC p 1.00; n>=100 variant 0.73); G9 (positive years 2); G10 not run |
| 6 | B_z5_A5_T0_tvwap_s10_f840 | 100 | 1.36 | 0.320 / 0.354 | -1.22 / -2.73 | 4.77 [-0.98, 11.02] (8.50) | 49, -3.62, -1.02 [-6.07, 4.04] | -0.60 | 1.000 / 0.729 | 234 | G1 (PRE eff 4.82 CI lo -0.28 rank 0.87); G2 (vs random direction 0.37, lo -2.10, rank 0.54); G3 (1x -1.22, 2x -2.73); G4 (win 0.320 vs BE 0.354); G5 (eff 4.77 < MDE80 8.50); G6 (HOLD eff -1.02 lo -6.07); G7 (X eff -0.60); G8 (RC p 1.00; n>=100 variant 0.73); G9 (positive years 1); G10 not run |
| 7 | B_vwap3_none_T1_tvwap_s10_f955 | 184 | 2.50 | 0.304 / 0.288 | 1.11 / -0.31 | 4.59 [1.45, 7.73] (4.59) | 67, -2.37, -3.62 [-11.21, 2.84] | -0.61 | 1.000 / 0.767 | 74 | G2 (vs random direction -2.60, lo -9.38, rank 0.24); G3 (1x 1.11, 2x -0.31); G5 (eff 4.59 < MDE80 4.59); G6 (HOLD eff -3.62 lo -11.21); G7 (X eff -0.61); G8 (RC p 1.00; n>=100 variant 0.77); G9 (positive years 2); G10 not run |
| 8 | B_z5_A5_T0_tvwap_s20_f955 | 108 | 1.47 | 0.380 / 0.451 | -3.24 / -4.93 | 4.43 [-1.51, 10.43] (8.44) | 50, -5.97, -3.26 [-8.38, 1.58] | 1.22 | 1.000 / 0.801 | 267 | G1 (PRE eff 3.05 CI lo -1.56 rank 0.76); G2 (vs random direction -2.38, lo -5.75, rank 0.20); G3 (1x -3.24, 2x -4.93); G4 (win 0.380 vs BE 0.451); G5 (eff 4.43 < MDE80 8.44); G6 (HOLD eff -3.26 lo -8.38); G8 (RC p 1.00; n>=100 variant 0.80); G9 (positive years 0); G10 not run |
| 9 | B_vwap3_none_T1_tvwap_s10_f840 | 184 | 2.50 | 0.326 / 0.307 | 1.21 / -0.24 | 4.20 [1.24, 7.19] (4.29) | 67, -1.34, -4.20 [-12.21, 2.77] | -0.33 | 1.000 / 0.848 | 77 | G2 (vs random direction -1.10, lo -5.71, rank 0.32); G3 (1x 1.21, 2x -0.24); G5 (eff 4.20 < MDE80 4.29); G6 (HOLD eff -4.20 lo -12.21); G7 (X eff -0.33); G8 (RC p 1.00; n>=100 variant 0.85); G9 (positive years 2); G10 not run |
| 10 | B_vwap3_none_T1_tvwap_s20_f955 | 169 | 2.30 | 0.391 / 0.387 | 0.28 / -1.34 | 4.19 [1.03, 7.56] (4.64) | 63, -1.00, -0.20 [-7.58, 5.36] | 1.56 | 1.000 / 0.848 | 90 | G1 (PRE eff 4.23 CI lo 1.77 rank 0.91); G2 (vs random direction -2.41, lo -10.15, rank 0.32); G3 (1x 0.28, 2x -1.34); G5 (eff 4.19 < MDE80 4.64); G6 (HOLD eff -0.20 lo -7.58); G8 (RC p 1.00; n>=100 variant 0.85); G9 (positive years 2); G10 not run |

All ten fail G3 (net not positive at 2x), G6 (HOLD CI lower <= 0), G8 and G10 (not run); all ten fail G2 (random direction; ranks 0.20-0.54); six of them also fail the G1 rank (0.76-0.93 of the draws) and four pass G1 (rank 0.96-0.97) but nothing else; the PRE edge of the "vwap3 none T1" family (rank 0.9-0.97 of the draws) is the same trade reached by several stop/target/flat variants (cells 1,2,4,5,7,9,10 are one cluster of ~170 trades at the +-3 sigma band: ~2.3-2.5 trades/week) and does not hold in HOLD (effect vs RIR -4.6..+1.4 pts, every CI spans zero, mean net -2.4..+2.6 on 63-68 trades). HOLD n is 38-77 per cell (below 100): a count, not a verdict, so G6 is also "inside MDE" for all.

## 5. By window, year, half-year, long/short (top 30 for windows; top 10 for the rest; RIR column = random-in-regime mean in the same slice)
Window table (hours from the WF sample = PRE + HOLD, mean pts/trade with effect vs RIR in brackets; the 14:00-15:30 and RTH-pooled columns are PRE only and exist for flat-15:55 cells; 09:30-10:00 is not defined because the bands need 30 session bars; claiming a best window would add 8 x 30 = 240 to N and none is claimed):

| cell | 10-11 mean (eff) n | 11-12 | 12-13 | 13-14 | 14:00-15:30 PRE mean (RIR) n | RTH-pooled PRE mean (RIR) n |
|---|---|---|---|---|---|---|
| B_vwap3_none_T1_tema_s20_f955 | 1.39 (3.75) n=131 | 3.03 (-1.93) n=33 | -1.75 (7.53) n=30 | -4.70 (8.22) n=33 | 3.94 (3.49) n=48 | 0.35 (-2.46) n=221 |
| B_vwap3_none_T1_tema_s10_f955 | 0.55 (2.58) n=137 | 0.90 (-2.90) n=36 | 1.14 (6.69) n=34 | -6.33 (4.92) n=37 | -1.58 (1.28) n=53 | -0.23 (-2.31) n=242 |
| B_z5_A5_T0_tvwap_s10_f955 | -2.92 (-1.53) n=46 | 2.61 (16.84) n=38 | -4.49 (-2.28) n=35 | -3.39 (-1.20) n=30 | -4.71 (-9.64) n=30 | -1.50 (-7.02) n=189 |
| B_vwap3_none_T1_tema_s10_f840 | 0.55 (2.84) n=137 | 0.90 (-2.20) n=36 | 2.44 (7.10) n=34 | -5.67 (2.48) n=37 | n/a (flat 14:00) | n/a (flat 14:00) |
| B_vwap3_none_T1_tema_s20_f840 | 1.14 (3.97) n=131 | 3.03 (-0.94) n=33 | -0.16 (8.32) n=30 | -5.70 (3.75) n=33 | n/a (flat 14:00) | n/a (flat 14:00) |
| B_z5_A5_T0_tvwap_s10_f840 | -2.92 (-0.98) n=46 | 2.61 (13.64) n=38 | -4.49 (-0.71) n=35 | -3.57 (-0.21) n=30 | n/a (flat 14:00) | n/a (flat 14:00) |
| B_vwap3_none_T1_tvwap_s10_f955 | 0.92 (1.08) n=144 | 0.18 (-2.08) n=36 | 3.94 (8.10) n=34 | -6.14 (8.02) n=37 | -1.95 (0.27) n=53 | 0.42 (-1.56) n=248 |
| B_z5_A5_T0_tvwap_s20_f955 | -5.57 (-2.16) n=50 | 2.60 (14.85) n=43 | -9.03 (-4.94) n=34 | -5.64 (-1.26) n=31 | -0.92 (-2.56) n=32 | -2.51 (-6.99) n=210 |
| B_vwap3_none_T1_tvwap_s10_f840 | 0.92 (1.28) n=144 | 0.18 (-1.38) n=36 | 4.40 (8.00) n=34 | -4.23 (3.64) n=37 | n/a (flat 14:00) | n/a (flat 14:00) |
| B_vwap3_none_T1_tvwap_s20_f955 | 1.07 (0.99) n=136 | 1.51 (-1.04) n=33 | 1.84 (9.61) n=30 | -8.06 (7.88) n=33 | 3.62 (2.63) n=48 | 0.90 (-1.49) n=226 |
| B_vwap3_none_T0_tema_s10_f840 | -0.14 (2.15) n=136 | 0.15 (-2.94) n=35 | 0.83 (5.49) n=33 | -3.08 (5.08) n=34 | n/a (flat 14:00) | n/a (flat 14:00) |
| B_z5_A5_T0_tvwap_s20_f840 | -5.57 (-1.68) n=50 | 2.60 (12.23) n=43 | -9.03 (-4.30) n=34 | -5.28 (-0.13) n=31 | n/a (flat 14:00) | n/a (flat 14:00) |
| B_vwap3_none_T0_tema_s10_f955 | -0.14 (1.89) n=136 | 0.15 (-3.64) n=35 | 0.36 (5.91) n=33 | -5.70 (5.55) n=34 | -5.43 (1.28) n=57 | -2.05 (-2.31) n=242 |
| B_vwap3_none_T1_tvwap_sext_f955 | 0.20 (0.15) n=142 | 4.25 (2.09) n=36 | -2.15 (0.53) n=32 | 0.83 (8.72) n=36 | 0.05 (0.01) n=51 | 0.93 (-1.74) n=238 |
| B_vwap3_none_T1_tvwap_s20_f840 | 0.89 (1.20) n=136 | 1.51 (-0.05) n=33 | 2.05 (9.49) n=30 | -4.59 (4.59) n=33 | n/a (flat 14:00) | n/a (flat 14:00) |
| B_vwap3_none_T1_tema_sext_f955 | 0.03 (0.29) n=134 | 2.69 (-0.10) n=36 | -4.90 (-0.87) n=32 | 0.63 (6.47) n=36 | 0.43 (0.93) n=51 | 0.70 (-1.50) n=232 |
| B_vwap3_none_T1_tvwap_sext_f840 | 0.20 (0.15) n=142 | 4.25 (2.09) n=36 | -1.93 (0.52) n=32 | -1.68 (4.97) n=36 | n/a (flat 14:00) | n/a (flat 14:00) |
| B_vwap3_none_T1_tema_sext_f840 | 0.03 (0.29) n=134 | 2.69 (-0.10) n=36 | -3.58 (-0.17) n=32 | -3.17 (4.06) n=36 | n/a (flat 14:00) | n/a (flat 14:00) |
| B_vwap3_none_T0_tvwap_s10_f955 | 0.37 (0.53) n=143 | -1.25 (-3.52) n=35 | 0.95 (5.10) n=33 | -6.00 (8.16) n=34 | -5.83 (0.27) n=57 | -1.37 (-1.56) n=248 |
| B_vwap3_none_T0_tvwap_s10_f840 | 0.37 (0.73) n=143 | -1.25 (-2.82) n=35 | 1.42 (5.02) n=33 | -3.22 (4.65) n=34 | n/a (flat 14:00) | n/a (flat 14:00) |
| B_vwap2_none_T4_tema_s20_f955 | -2.44 (-0.00) n=52 | 0.83 (3.17) n=37 | 6.35 (8.64) n=32 | -18.57 (-16.11) n=36 | -3.09 (1.96) n=32 | 1.28 (-0.74) n=152 |
| B_vwap3_none_T5_t20_sext_f840 | -3.48 (-0.70) n=75 | 6.04 (7.13) n=20 | 3.15 (4.65) n=18 | 5.95 (4.30) n=28 | n/a (flat 14:00) | n/a (flat 14:00) |
| B_vwap3_none_T5_t20_s10_f840 | -3.62 (-0.59) n=75 | 6.82 (8.19) n=20 | 2.22 (3.65) n=18 | 4.64 (1.97) n=27 | n/a (flat 14:00) | n/a (flat 14:00) |
| B_vwap3_none_T5_t20_sext_f955 | -3.48 (-0.70) n=75 | 6.04 (7.13) n=20 | 2.76 (4.41) n=18 | 5.74 (4.35) n=28 | -3.88 (-3.00) n=30 | 0.30 (-1.83) n=139 |
| B_vwap2_none_T4_tema_s20_f840 | -3.04 (-0.49) n=52 | 0.61 (3.02) n=37 | 4.91 (7.41) n=32 | -12.52 (-12.52) n=36 | n/a (flat 14:00) | n/a (flat 14:00) |
| B_vwap2_none_T4_tvwap_s10_f955 | -4.78 (-2.49) n=56 | 7.67 (8.48) n=38 | 9.05 (10.05) n=34 | -12.62 (-9.95) n=38 | -16.14 (-2.28) n=33 | -1.32 (-1.12) n=157 |
| B_vwap3_none_T5_t20_s10_f955 | -3.62 (-0.59) n=75 | 6.82 (8.19) n=20 | 1.32 (3.12) n=18 | 5.15 (2.09) n=27 | -1.77 (-1.79) n=29 | 0.75 (-1.33) n=137 |
| B_z5_none_T8_tvwap_s10_f955 | -1.99 (0.93) n=24 | -0.76 (2.90) n=30 | -3.98 (-2.58) n=44 | -4.00 (1.90) n=59 | -7.52 (-4.11) n=51 | -3.00 (-3.81) n=259 |
| B_vwap3_none_T0_tema_s20_f840 | -0.24 (2.58) n=131 | -6.66 (-10.63) n=34 | -2.18 (6.30) n=30 | -4.24 (5.21) n=34 | n/a (flat 14:00) | n/a (flat 14:00) |
| B_vwap2_A5_T1_tvwap_s10_f955 | -0.89 (2.67) n=228 | -5.00 (-2.08) n=60 | -9.73 (4.02) n=17 | -3.40 (5.59) n=17 | -7.02 (-0.39) n=8 | -1.57 (-3.76) n=255 |

By year (WF, top 10):

| cell | year | n | mean1 | RIR mean | effect | win |
|---|---|---|---|---|---|---|
| B_vwap3_none_T1_tema_s20_f955 | 2024 | 112 | 0.04 | -0.59 | 0.63 | 0.384 |
| B_vwap3_none_T1_tema_s20_f955 | 2025 | 105 | -2.24 | -9.99 | 7.75 | 0.314 |
| B_vwap3_none_T1_tema_s20_f955 | 2026 | 10 | 30.54 | 21.66 | 8.87 | 0.600 |
| B_vwap3_none_T1_tema_s10_f955 | 2024 | 123 | 1.10 | -1.27 | 2.37 | 0.301 |
| B_vwap3_none_T1_tema_s10_f955 | 2025 | 111 | -3.01 | -7.03 | 4.02 | 0.252 |
| B_vwap3_none_T1_tema_s10_f955 | 2026 | 10 | 11.13 | 17.77 | -6.64 | 0.400 |
| B_z5_A5_T0_tvwap_s10_f955 | 2024 | 57 | 0.28 | -3.15 | 3.43 | 0.404 |
| B_z5_A5_T0_tvwap_s10_f955 | 2025 | 88 | -2.92 | -6.01 | 3.08 | 0.261 |
| B_z5_A5_T0_tvwap_s10_f955 | 2026 | 4 | -13.12 | -14.66 | 1.55 | 0.000 |
| B_vwap3_none_T1_tema_s10_f840 | 2024 | 123 | 1.55 | -1.27 | 2.81 | 0.317 |
| B_vwap3_none_T1_tema_s10_f840 | 2025 | 111 | -2.89 | -6.27 | 3.38 | 0.288 |
| B_vwap3_none_T1_tema_s10_f840 | 2026 | 10 | 11.13 | 17.77 | -6.64 | 0.400 |
| B_vwap3_none_T1_tema_s20_f840 | 2024 | 112 | 0.17 | -0.77 | 0.94 | 0.402 |
| B_vwap3_none_T1_tema_s20_f840 | 2025 | 105 | -2.55 | -9.18 | 6.63 | 0.343 |
| B_vwap3_none_T1_tema_s20_f840 | 2026 | 10 | 30.54 | 21.66 | 8.87 | 0.600 |
| B_z5_A5_T0_tvwap_s10_f840 | 2024 | 57 | 0.28 | -3.36 | 3.64 | 0.404 |
| B_z5_A5_T0_tvwap_s10_f840 | 2025 | 88 | -2.99 | -6.03 | 3.04 | 0.261 |
| B_z5_A5_T0_tvwap_s10_f840 | 2026 | 4 | -13.12 | -10.05 | -3.07 | 0.000 |
| B_vwap3_none_T1_tvwap_s10_f955 | 2024 | 128 | 2.60 | -0.07 | 2.67 | 0.320 |
| B_vwap3_none_T1_tvwap_s10_f955 | 2025 | 113 | -3.28 | -6.74 | 3.46 | 0.239 |
| B_vwap3_none_T1_tvwap_s10_f955 | 2026 | 10 | 8.42 | 13.96 | -5.54 | 0.300 |
| B_z5_A5_T0_tvwap_s20_f955 | 2024 | 61 | -1.15 | -3.93 | 2.78 | 0.459 |
| B_z5_A5_T0_tvwap_s20_f955 | 2025 | 93 | -5.60 | -7.03 | 1.43 | 0.344 |
| B_z5_A5_T0_tvwap_s20_f955 | 2026 | 4 | -14.46 | -16.61 | 2.15 | 0.250 |
| B_vwap3_none_T1_tvwap_s10_f840 | 2024 | 128 | 3.02 | 0.06 | 2.96 | 0.336 |
| B_vwap3_none_T1_tvwap_s10_f840 | 2025 | 113 | -3.00 | -5.79 | 2.80 | 0.274 |
| B_vwap3_none_T1_tvwap_s10_f840 | 2026 | 10 | 8.42 | 21.06 | -12.64 | 0.300 |
| B_vwap3_none_T1_tvwap_s20_f955 | 2024 | 117 | 1.90 | 0.82 | 1.07 | 0.419 |
| B_vwap3_none_T1_tvwap_s20_f955 | 2025 | 105 | -3.30 | -9.65 | 6.35 | 0.305 |
| B_vwap3_none_T1_tvwap_s20_f955 | 2026 | 10 | 10.88 | 17.58 | -6.69 | 0.400 |

By half-year (WF, top 10; M13 drift: see rows):

| cell | half-year | n | mean1 | RIR mean | effect |
|---|---|---|---|---|---|
| B_vwap3_none_T1_tema_s20_f955 | 2024H1 | 53 | -0.85 | 1.14 | -1.99 |
| B_vwap3_none_T1_tema_s20_f955 | 2024H2 | 59 | 0.84 | -2.26 | 3.11 |
| B_vwap3_none_T1_tema_s20_f955 | 2025H1 | 52 | -0.97 | -17.54 | 16.57 |
| B_vwap3_none_T1_tema_s20_f955 | 2025H2 | 53 | -3.48 | -2.87 | -0.61 |
| B_vwap3_none_T1_tema_s20_f955 | 2026H1 | 10 | 30.54 | 21.66 | 8.87 |
| B_vwap3_none_T1_tema_s10_f955 | 2024H1 | 60 | 0.83 | -0.58 | 1.41 |
| B_vwap3_none_T1_tema_s10_f955 | 2024H2 | 63 | 1.35 | -1.96 | 3.31 |
| B_vwap3_none_T1_tema_s10_f955 | 2025H1 | 55 | -1.11 | -13.70 | 12.58 |
| B_vwap3_none_T1_tema_s10_f955 | 2025H2 | 56 | -4.87 | -0.78 | -4.09 |
| B_vwap3_none_T1_tema_s10_f955 | 2026H1 | 10 | 11.13 | 17.77 | -6.64 |
| B_z5_A5_T0_tvwap_s10_f955 | 2024H1 | 36 | 4.49 | 1.86 | 2.62 |
| B_z5_A5_T0_tvwap_s10_f955 | 2024H2 | 21 | -6.93 | -10.38 | 3.45 |
| B_z5_A5_T0_tvwap_s10_f955 | 2025H1 | 43 | -3.21 | -10.78 | 7.57 |
| B_z5_A5_T0_tvwap_s10_f955 | 2025H2 | 45 | -2.65 | 0.01 | -2.66 |
| B_z5_A5_T0_tvwap_s10_f955 | 2026H1 | 4 | -13.12 | -14.66 | 1.55 |
| B_vwap3_none_T1_tema_s10_f840 | 2024H1 | 60 | 1.75 | -0.07 | 1.82 |
| B_vwap3_none_T1_tema_s10_f840 | 2024H2 | 63 | 1.35 | -2.47 | 3.82 |
| B_vwap3_none_T1_tema_s10_f840 | 2025H1 | 55 | -2.64 | -12.64 | 9.99 |
| B_vwap3_none_T1_tema_s10_f840 | 2025H2 | 56 | -3.12 | -0.30 | -2.83 |
| B_vwap3_none_T1_tema_s10_f840 | 2026H1 | 10 | 11.13 | 17.77 | -6.64 |
| B_vwap3_none_T1_tema_s20_f840 | 2024H1 | 53 | 0.11 | 1.54 | -1.44 |
| B_vwap3_none_T1_tema_s20_f840 | 2024H2 | 59 | 0.23 | -3.01 | 3.23 |
| B_vwap3_none_T1_tema_s20_f840 | 2025H1 | 52 | -2.39 | -16.37 | 13.98 |
| B_vwap3_none_T1_tema_s20_f840 | 2025H2 | 53 | -2.70 | -2.39 | -0.31 |
| B_vwap3_none_T1_tema_s20_f840 | 2026H1 | 10 | 30.54 | 21.66 | 8.87 |
| B_z5_A5_T0_tvwap_s10_f840 | 2024H1 | 36 | 4.49 | 2.06 | 2.43 |
| B_z5_A5_T0_tvwap_s10_f840 | 2024H2 | 21 | -6.93 | -11.17 | 4.25 |
| B_z5_A5_T0_tvwap_s10_f840 | 2025H1 | 43 | -3.21 | -9.35 | 6.14 |
| B_z5_A5_T0_tvwap_s10_f840 | 2025H2 | 45 | -2.78 | -1.85 | -0.93 |
| B_z5_A5_T0_tvwap_s10_f840 | 2026H1 | 4 | -13.12 | -10.05 | -3.07 |
| B_vwap3_none_T1_tvwap_s10_f955 | 2024H1 | 64 | 1.92 | 0.09 | 1.83 |
| B_vwap3_none_T1_tvwap_s10_f955 | 2024H2 | 64 | 3.28 | -0.24 | 3.52 |
| B_vwap3_none_T1_tvwap_s10_f955 | 2025H1 | 56 | -2.29 | -12.01 | 9.73 |
| B_vwap3_none_T1_tvwap_s10_f955 | 2025H2 | 57 | -4.26 | -1.90 | -2.37 |
| B_vwap3_none_T1_tvwap_s10_f955 | 2026H1 | 10 | 8.42 | 13.96 | -5.54 |
| B_z5_A5_T0_tvwap_s20_f955 | 2024H1 | 35 | 0.81 | -2.16 | 2.97 |
| B_z5_A5_T0_tvwap_s20_f955 | 2024H2 | 26 | -3.79 | -6.32 | 2.52 |
| B_z5_A5_T0_tvwap_s20_f955 | 2025H1 | 47 | -5.96 | -12.60 | 6.65 |
| B_z5_A5_T0_tvwap_s20_f955 | 2025H2 | 46 | -5.23 | -0.45 | -4.79 |
| B_z5_A5_T0_tvwap_s20_f955 | 2026H1 | 4 | -14.46 | -16.61 | 2.15 |
| B_vwap3_none_T1_tvwap_s10_f840 | 2024H1 | 64 | 2.76 | 0.65 | 2.11 |
| B_vwap3_none_T1_tvwap_s10_f840 | 2024H2 | 64 | 3.28 | -0.54 | 3.83 |
| B_vwap3_none_T1_tvwap_s10_f840 | 2025H1 | 56 | -2.94 | -10.65 | 7.71 |
| B_vwap3_none_T1_tvwap_s10_f840 | 2025H2 | 57 | -3.05 | -1.33 | -1.73 |
| B_vwap3_none_T1_tvwap_s10_f840 | 2026H1 | 10 | 8.42 | 21.06 | -12.64 |
| B_vwap3_none_T1_tvwap_s20_f955 | 2024H1 | 57 | 0.58 | 1.35 | -0.77 |
| B_vwap3_none_T1_tvwap_s20_f955 | 2024H2 | 60 | 3.14 | 0.29 | 2.85 |
| B_vwap3_none_T1_tvwap_s20_f955 | 2025H1 | 52 | -3.36 | -15.44 | 12.08 |
| B_vwap3_none_T1_tvwap_s20_f955 | 2025H2 | 53 | -3.24 | -4.27 | 1.03 |
| B_vwap3_none_T1_tvwap_s20_f955 | 2026H1 | 10 | 10.88 | 17.58 | -6.69 |

Long / short split (WF, top 10):

| cell | side | n | mean1 | RIR mean | effect |
|---|---|---|---|---|---|
| B_vwap3_none_T1_tema_s20_f955 | long | 153 | 1.60 | -3.70 | 5.30 |
| B_vwap3_none_T1_tema_s20_f955 | short | 74 | -2.30 | -4.35 | 2.05 |
| B_vwap3_none_T1_tema_s10_f955 | long | 163 | 0.26 | -2.87 | 3.13 |
| B_vwap3_none_T1_tema_s10_f955 | short | 81 | -1.61 | -3.33 | 1.71 |
| B_z5_A5_T0_tvwap_s10_f955 | long | 82 | -2.14 | -4.53 | 2.39 |
| B_z5_A5_T0_tvwap_s10_f955 | short | 67 | -1.77 | -6.00 | 4.23 |
| B_vwap3_none_T1_tema_s10_f840 | long | 163 | 0.13 | -2.79 | 2.92 |
| B_vwap3_none_T1_tema_s10_f840 | short | 81 | -0.49 | -2.49 | 2.00 |
| B_vwap3_none_T1_tema_s20_f840 | long | 153 | 1.21 | -3.58 | 4.79 |
| B_vwap3_none_T1_tema_s20_f840 | short | 74 | -1.73 | -3.79 | 2.05 |
| B_z5_A5_T0_tvwap_s10_f840 | long | 82 | -2.14 | -3.64 | 1.51 |
| B_z5_A5_T0_tvwap_s10_f840 | short | 67 | -1.85 | -7.03 | 5.18 |
| B_vwap3_none_T1_tvwap_s10_f955 | long | 169 | 0.30 | -2.22 | 2.52 |
| B_vwap3_none_T1_tvwap_s10_f955 | short | 82 | -0.06 | -2.70 | 2.63 |
| B_z5_A5_T0_tvwap_s20_f955 | long | 86 | -3.73 | -5.98 | 2.25 |
| B_z5_A5_T0_tvwap_s20_f955 | short | 72 | -4.56 | -6.34 | 1.78 |
| B_vwap3_none_T1_tvwap_s10_f840 | long | 169 | 0.27 | -1.57 | 1.84 |
| B_vwap3_none_T1_tvwap_s10_f840 | short | 82 | 1.05 | -1.65 | 2.70 |
| B_vwap3_none_T1_tvwap_s20_f955 | long | 157 | 0.73 | -2.92 | 3.65 |
| B_vwap3_none_T1_tvwap_s20_f955 | short | 75 | -1.73 | -3.52 | 1.79 |

## 6. Heat tables
None defined for this family.

## 7. Realised stop / target distribution (PRE, structural brackets; top 10)

| cell | median stop pts | p90 stop | median target dist | p90 target | target hit | stop hit | n skipped (invalid) |
|---|---|---|---|---|---|---|---|
| B_vwap3_none_T1_tema_s20_f955 | 24.8 | 43.3 | 60.6 | 138.0 | 0.360 | 0.628 | 9 |
| B_vwap3_none_T1_tema_s10_f955 | 14.3 | 33.1 | 60.7 | 137.3 | 0.287 | 0.708 | 9 |
| B_z5_A5_T0_tvwap_s10_f955 | 11.9 | 20.2 | 31.2 | 83.0 | 0.330 | 0.670 | 172 |
| B_vwap3_none_T1_tema_s10_f840 | 14.3 | 33.1 | 60.7 | 137.3 | 0.258 | 0.669 | 9 |
| B_vwap3_none_T1_tema_s20_f840 | 24.8 | 43.3 | 60.6 | 138.0 | 0.317 | 0.591 | 9 |
| B_z5_A5_T0_tvwap_s10_f840 | 11.9 | 20.2 | 31.2 | 83.0 | 0.330 | 0.670 | 172 |
| B_vwap3_none_T1_tvwap_s10_f955 | 14.4 | 33.1 | 60.0 | 138.0 | 0.299 | 0.696 | 2 |
| B_z5_A5_T0_tvwap_s20_f955 | 21.0 | 30.1 | 31.6 | 83.2 | 0.389 | 0.611 | 161 |
| B_vwap3_none_T1_tvwap_s10_f840 | 14.4 | 33.1 | 60.0 | 138.0 | 0.277 | 0.658 | 2 |
| B_vwap3_none_T1_tvwap_s20_f955 | 24.9 | 43.3 | 59.9 | 138.8 | 0.379 | 0.604 | 2 |

Typical: +-3 sigma band cells with the EMA200 target risk a median 14-25 pts for a median 60 pt target distance (p90 138 pts) with target hit 26-39% against a stop hit 59-71%; the Z5 cells have 160+ rows skipped as invalid.


## 8. Deviations and disclosures
- Holdout looks used: ONE for HOLD (top 30) and ONE for X (same 30) - both read in stage 2 after DS3_ZEN_F4_PREHOLD.md (sha256 70450ba60c2cc156dae9c869a90d0f7b7629e327bec91c6e6a3252784dcac066) was logged; stage 1 loaded data with cutoff 20250630 only. Tracks D3ZF4, D3ZF4_X. HOLD capped at 2026-02-06 (standing rule).
- Selection effects: the top 30 were chosen on PRE by effect vs the pool expectation among n >= 100 cells; they are strongly clustered (the same ~170 +-3 sigma trades under 6 stop/target/flat variants) so 30 cells are about 6-8 independent ideas. The G1 'rank' in the screen is the pool expectation (CI lower > 0 as the screen test); the 100-draw rank was computed for the top 30 only.
- Measuring caveat: the random-in-regime pool in a reversal regime is strongly negative (about -5 pts/trade for the +-3 sigma and Z5 brackets with wide EMA200/VWAP targets) because a random minute in the first 5 bars after the band touch is usually still in the momentum move; the "effect" is therefore large even when the cell itself loses. The random-direction placebo shows the right sign of that: the same minutes traded WITH the move beat the reversal trade in 23 of the top 30 (mean random-direction effect -0.74 pts, mean rank 0.42). The gate list uses both, as the brief demands.
- Definitions chosen where the addenda are silent (prereg lists them): fresh-cross touch (changed from 'any bar beyond the band' after descriptive counts and stop geometry, before any P&L), trigger window 5 bars, T4 swing strength 2 / 30 bars, T5 FVG body gap >= 0.25 pt, T6 FVG lookback 15 bars, T7 EMA9/21, T8 volume >= 2x median20 on a bar closing in the reversal direction (the delta/absorption variant is not built), extreme = 6-bar extreme +-1 tick, Z5 band = 2.25 x leg range from the leg start (strength-3 swings, legs >= 10 pt), entries are market at the next open (T0 'limit at the level' is not used because the band moves), session VWAP anchored 09:30 (ETH variant not run), SMT = ES new 60-bar extreme without an NQ new extreme within 15 min (1-min and 5-min), ZM tolerances 5 pt, SMT cell brackets 15/20, 30/20, 40/20. The SMT part covers 2023-08 onward (ES table), so the X span has SMT only 2023-08..2024-01.
- Not run: G10 direct 1-s/L2 replay (no replay launched, needs PRIO_ALLOW + governor restart); sizing / management shapes; section 7 filters and section 8 portfolio add (F6). The screen is on the mapped conservative 1-min basis (0.05-0.13 pts/trade more conservative than 1-s on tight stops) - far smaller than the deficits here (-2.5 pts median).
- ZM3 caveat: with the 5-pt zone tolerance and first/second-touch rule a 1-min FVG or OB lies at the touched line in ~98% of ZM1 signals, so ZM3 is nearly ZM1 (the tiers ZM1/ZM3 are not separable in the SMT part; F5 owns the tier question).
- Lib bugs: none found. Unit tests: f4_test.py 53/53 (signals, SMT, ZM, E cells, leg extensions, 4H zones unchanged when later bars are deleted; log out/zen/f4/f4_test.log).
- Plain answer to the base question: does a reversal from the VWAP +-2/3 sigma bands (or the Z5 -2.25 band), with or without the 5m EMA200 agreeing, with T1-T8 triggers, SMT confirmation or extension targets, add anything over a random entry in the same regime and window with the same bracket? Against the random-in-regime pool a few +-3 sigma variants look positive in PRE, but they are negative in net, negative against random direction and reverse in HOLD; the family as a whole is a net loser (-2.5 pts/trade median), and conditioning on the 5m EMA200 side makes it worse.

## 9. Files / code paths
- Report: autopilot/DS3_ZEN_F4.md; pre-holdout: autopilot/DS3_ZEN_F4_PREHOLD.md. Prereg: l2vast/ds3/prereg/ZEN_F4_ALL_prereg.md (+ .sha256, ZEN_F4_cells.csv).
- Code: l2vast/ds3/code/zen/f4/{f4_mod.py (detectors, brackets, SMT, ZM, legs), f4_groups.py, f4_cells.py, f4_run.py (stage1/2/3), f4_desc.py, f4_test.py, f4_report.py}.
- Outputs: l2vast/ds3/out/zen/f4/{stage1_cells.csv (all 1,038 cells), stage1_top30.csv, stage1_weekly.npz, stage2_top30.csv, stage2_tables.pkl, stage3_windows.csv, desc_counts_PRE.csv, desc_validity_PRE.csv, *.log, *_table.md}.

DONE F4
