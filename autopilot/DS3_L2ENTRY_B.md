# DS3_L2ENTRY_B - the order book as the signal: 7 new intraday books scored by ENTRY SESSION (T-L2-ENTRY section B)
Research only; NQ 1-s mbp-10 book + ES concordance, 2023-04..2026-02-06; UNTOUCHED never read (rows cut at 2026-02-06 22:00Z, windows capped at label day 20260206; vs_lib/S48 HOLD mask NOT used: HOLD here = 157 label days 2025-07..2026-02-06). Prereg l2vast/ds3/prereg/L2EB_prereg.md (sha256 357ec704... original text, c20f8185... with addendum A1; logged in DECISIONS.md before any statistic). One HOLD look logged. MEASURED fills: market +1 tick, stop-market measured walk 1.01 pts, limit target at touch with the measured target correction (1.4/1.5/4.2/4.3 pts by year), fee 0.242 pts, lots at $1,000 risk/trade (60-pt stop = 0.833 lots), exact lock engine (x_locks, R=$1,000). "stress" = conservative label only (entry +1 more tick, stop 2.02, target +1.0 pt), nothing dropped on it.

## VERDICT LINES (one per family; recent windows first; 2026 = 2026-01-01..2026-02-06 = ~5 weeks, MDE very large)
**B1 ABSORPTION at a level: DEAD** - 3,732 unique-cell events over 32 populated base cells (333 populated session cells incl. ES variant); 19 session cells reach G0 (n_PRE>=60, n_HOLD>=20), 0 of those have PRE t>=2; PASS 0; CANDIDATE 0 (White RC min p over the family 1.000); CANDIDATE-RECENT 0 cells vs 4.1 expected by chance under the shuffled-book placebo (same sessions/sides); median L6M cell -11.66 pts/trade (random-entry baseline about -2.2 = cost); best L6M cell B1_k5_h30_SHL ALL ALL: L6M -5.01 pts/trade (n=72, MDE 18.51), HOLD -5.29, PRE -4.99 (t -0.77), 2026 -7.41 (n=12).
**B2 ICEBERG at a level: DEAD** - 180,611 unique-cell events over 12 populated base cells (180 populated session cells incl. ES variant); 139 session cells reach G0 (n_PRE>=60, n_HOLD>=20), 0 of those have PRE t>=2; PASS 0; CANDIDATE 0 (White RC min p over the family 1.000); CANDIDATE-RECENT 20 cells vs 18.5 expected by chance under the shuffled-book placebo (same sessions/sides); median L6M cell -3.33 pts/trade (random-entry baseline about -2.2 = cost); best L6M cell B2_r20_R100 ES LONDON: L6M 17.86 pts/trade (n=31, MDE 27.91), HOLD 21.18, PRE -4.90 (t -0.91), 2026 16.55 (n=9).
**B3 FAILED SWEEP and reclaim: DEAD** - 756,963 unique-cell events over 24 populated base cells (360 populated session cells incl. ES variant); 347 session cells reach G0 (n_PRE>=60, n_HOLD>=20), 0 of those have PRE t>=2; PASS 0; CANDIDATE 0 (White RC min p over the family 1.000); CANDIDATE-RECENT 20 cells vs 47.8 expected by chance under the shuffled-book placebo (same sessions/sides); median L6M cell -4.92 pts/trade (random-entry baseline about -2.2 = cost); best L6M cell B3_m3_w10_VWB ALL CLOSE: L6M 11.32 pts/trade (n=52, MDE 17.03), HOLD 11.31, PRE -1.01 (t -0.31), 2026 30.88 (n=8).
**B4 IMBALANCE PERSISTENCE: DEAD** - 1,580 unique-cell events over 9 populated base cells (69 populated session cells incl. ES variant); 11 session cells reach G0 (n_PRE>=60, n_HOLD>=20), 0 of those have PRE t>=2; PASS 0; CANDIDATE 0 (White RC min p over the family 1.000); CANDIDATE-RECENT 0 cells vs 2.2 expected by chance under the shuffled-book placebo (same sessions/sides); median L6M cell -5.71 pts/trade (random-entry baseline about -2.2 = cost); best L6M cell B4_p120_avg ALL ASIA: L6M -0.99 pts/trade (n=31, MDE 29.83), HOLD -2.87, PRE -4.83 (t -0.79), 2026 20.45 (n=10).
**B5 PULLED BOOK: DEAD** - 730,377 unique-cell events over 2 populated base cells (32 populated session cells incl. ES variant); 32 session cells reach G0 (n_PRE>=60, n_HOLD>=20), 0 of those have PRE t>=2; PASS 0; CANDIDATE 0 (White RC min p over the family 1.000); CANDIDATE-RECENT 0 cells vs 1.3 expected by chance under the shuffled-book placebo (same sessions/sides); median L6M cell -3.19 pts/trade (random-entry baseline about -2.2 = cost); best L6M cell B5_d05 ALL CLOSE: L6M -2.02 pts/trade (n=460, MDE 5.74), HOLD -1.85, PRE -2.34 (t -1.90), 2026 -3.20 (n=112).
**B6 DEPTH SHIFT (wall appearing): DEAD** - 191,058 unique-cell events over 2 populated base cells (32 populated session cells incl. ES variant); 32 session cells reach G0 (n_PRE>=60, n_HOLD>=20), 0 of those have PRE t>=2; PASS 0; CANDIDATE 0 (White RC min p over the family 1.000); CANDIDATE-RECENT 3 cells vs 3.1 expected by chance under the shuffled-book placebo (same sessions/sides); median L6M cell -2.88 pts/trade (random-entry baseline about -2.2 = cost); best L6M cell B6_b ES LONDON: L6M 4.63 pts/trade (n=117, MDE 15.06), HOLD 4.15, PRE -13.07 (t -3.00), 2026 4.71 (n=23).
**B7 VPIN SPIKE at session extreme: DEAD** - 30,508 unique-cell events over 4 populated base cells (64 populated session cells incl. ES variant); 50 session cells reach G0 (n_PRE>=60, n_HOLD>=20), 0 of those have PRE t>=2; PASS 0; CANDIDATE 0 (White RC min p over the family 1.000); CANDIDATE-RECENT 6 cells vs 7.8 expected by chance under the shuffled-book placebo (same sessions/sides); median L6M cell -2.76 pts/trade (random-entry baseline about -2.2 = cost); best L6M cell B7_d10_cont ES ASIA: L6M 8.09 pts/trade (n=32, MDE 28.84), HOLD 3.29, PRE 0.72 (t 0.12), 2026 3.59 (n=9).

**Overall:** 1,894,829 events, 1,070 populated gated session cells (of 1,472 prereg; RC N = 1070); G0 passed by 630; PRE t>=2 and G0: 0; White RC min adjusted p 1.000; PASS 0, CANDIDATE 0 -> **no session book registered, no D6 cell spec issued.** CANDIDATE-RECENT (2026>0 and L6M>0, n_L6M>=30): 49 cells; expected by chance under the placebos: 84.8 (shuffled-book) / 42.9 (time-shuffled within day) -> the observed count is at or below what random entries would give, so the recent-window positives are in line with chance and are NOT promoted; table below for the monitor list only.

## 1. Family x session x window - median over populated cells (n >= 30 in window), pts/trade MEASURED, recent first (random-entry universe = the cost baseline)
| family | session | cells | 2026 med (frac>0) | L6M med (frac>0) | HOLD med (frac>0) | PRE med (frac>0) | X' med (frac>0) | HOLD stress med |
|---|---|---|---|---|---|---|---|---|
| B1 | ALL | 62 | - | -10.96 (0.00) n=12 | -8.84 (0.00) n=12 | -4.41 (0.16) n=19 | 1.21 (0.57) n=7 | -10.04 |
| B1 | ASIA | 51 | - | -11.13 (0.00) n=4 | -7.59 (0.00) n=7 | -5.96 (0.18) n=11 | -2.42 (0.00) n=2 | -8.85 |
| B1 | LONDON | 52 | - | - | -2.66 (0.00) n=3 | -2.13 (0.00) n=7 | -2.47 (0.00) n=1 | -3.90 |
| B1 | PRE | 33 | - | - | - | - | - |  |
| B1 | NY-AM | 49 | - | - | - | -12.75 (0.00) n=1 | - |  |
| B1 | NY-PM | 39 | - | - | - | 4.86 (1.00) n=1 | - |  |
| B1 | CLOSE | 44 | - | - | - | -4.72 (0.00) n=2 | - |  |
| B1 | NY | 56 | - | -14.98 (0.00) n=2 | -11.53 (0.00) n=3 | -7.55 (0.00) n=6 | 9.33 (1.00) n=1 | -12.65 |
| B2 | ALL | 24 | -4.29 (0.07) n=14 | -2.82 (0.25) n=24 | -2.75 (0.21) n=24 | -2.79 (0.12) n=24 | -0.85 (0.33) n=24 | -3.96 |
| B2 | ASIA | 20 | -0.45 (0.50) n=4 | -6.13 (0.18) n=11 | -5.09 (0.09) n=11 | -1.07 (0.36) n=14 | -1.35 (0.17) n=6 | -6.34 |
| B2 | LONDON | 20 | -2.62 (0.00) n=4 | 1.56 (0.50) n=12 | 0.50 (0.62) n=13 | -1.84 (0.28) n=18 | -2.44 (0.29) n=14 | -0.75 |
| B2 | PRE | 20 | -1.01 (0.00) n=1 | -5.47 (0.14) n=7 | -2.31 (0.25) n=8 | 0.78 (0.58) n=12 | -3.47 (0.00) n=10 | -3.56 |
| B2 | NY-AM | 24 | -6.83 (0.00) n=10 | -3.67 (0.11) n=19 | -3.52 (0.15) n=20 | -4.78 (0.17) n=24 | -0.59 (0.45) n=20 | -4.74 |
| B2 | NY-PM | 24 | -3.70 (0.12) n=8 | -3.58 (0.06) n=17 | -3.98 (0.06) n=18 | -2.46 (0.08) n=24 | -0.27 (0.50) n=22 | -5.17 |
| B2 | CLOSE | 24 | -7.60 (0.00) n=6 | -2.49 (0.23) n=13 | -2.74 (0.20) n=15 | -2.54 (0.20) n=20 | -0.72 (0.40) n=15 | -3.77 |
| B2 | NY | 24 | -5.55 (0.15) n=13 | -3.25 (0.18) n=22 | -3.16 (0.18) n=22 | -3.14 (0.21) n=24 | 0.49 (0.58) n=24 | -4.36 |
| B3 | ALL | 48 | -4.61 (0.00) n=46 | -4.96 (0.00) n=48 | -4.74 (0.00) n=48 | -2.92 (0.06) n=48 | -1.34 (0.15) n=48 | -5.95 |
| B3 | ASIA | 40 | -5.30 (0.16) n=31 | -6.09 (0.00) n=37 | -5.75 (0.00) n=38 | -3.94 (0.05) n=40 | -0.94 (0.34) n=35 | -7.00 |
| B3 | LONDON | 40 | -6.18 (0.04) n=28 | -4.84 (0.08) n=38 | -4.29 (0.10) n=39 | -2.00 (0.12) n=40 | -4.30 (0.08) n=38 | -5.54 |
| B3 | PRE | 40 | 0.54 (0.71) n=7 | -5.83 (0.15) n=26 | -4.81 (0.25) n=28 | -2.55 (0.22) n=37 | -3.21 (0.24) n=34 | -6.06 |
| B3 | NY-AM | 48 | -5.19 (0.03) n=32 | -6.08 (0.00) n=48 | -4.77 (0.00) n=48 | -4.19 (0.17) n=48 | 0.17 (0.55) n=47 | -5.99 |
| B3 | NY-PM | 48 | -1.43 (0.38) n=16 | -5.02 (0.02) n=47 | -4.92 (0.02) n=48 | -2.81 (0.04) n=48 | 0.04 (0.51) n=47 | -6.09 |
| B3 | CLOSE | 48 | -7.93 (0.00) n=16 | -3.02 (0.36) n=44 | -3.26 (0.35) n=46 | -1.66 (0.23) n=48 | -0.48 (0.49) n=41 | -4.28 |
| B3 | NY | 48 | -3.84 (0.05) n=41 | -4.74 (0.00) n=48 | -4.40 (0.00) n=48 | -3.11 (0.15) n=48 | -0.36 (0.44) n=48 | -5.58 |
| B4 | ALL | 18 | - | -4.11 (0.00) n=5 | -5.75 (0.00) n=5 | -0.30 (0.50) n=6 | -4.25 (0.20) n=5 | -7.00 |
| B4 | ASIA | 18 | - | -4.67 (0.00) n=4 | -4.10 (0.00) n=5 | 2.38 (0.67) n=6 | -4.01 (0.00) n=3 | -5.36 |
| B4 | LONDON | 14 | - | -8.17 (0.00) n=1 | -7.87 (0.00) n=1 | -4.40 (0.33) n=3 | -11.21 (0.00) n=3 | -9.12 |
| B4 | PRE | 8 | - | - | - | - | - |  |
| B4 | NY-AM | 2 | - | - | - | - | - |  |
| B4 | NY-PM | 8 | - | - | - | - | - |  |
| B4 | CLOSE | 3 | - | - | - | - | - |  |
| B4 | NY | 8 | - | - | - | - | - |  |
| B5 | ALL | 4 | -3.25 (0.00) n=4 | -3.12 (0.00) n=4 | -3.11 (0.00) n=4 | -2.34 (0.00) n=4 | -1.76 (0.00) n=4 | -4.32 |
| B5 | ASIA | 4 | -3.41 (0.00) n=4 | -3.37 (0.00) n=4 | -3.39 (0.00) n=4 | -2.36 (0.00) n=4 | -1.37 (0.00) n=4 | -4.65 |
| B5 | LONDON | 4 | -4.26 (0.00) n=4 | -3.86 (0.00) n=4 | -3.78 (0.00) n=4 | -2.38 (0.00) n=4 | -1.63 (0.00) n=4 | -5.04 |
| B5 | PRE | 4 | -4.29 (0.00) n=4 | -3.94 (0.00) n=4 | -4.08 (0.00) n=4 | -2.28 (0.00) n=4 | -1.81 (0.00) n=4 | -5.33 |
| B5 | NY-AM | 4 | -3.38 (0.00) n=4 | -3.15 (0.00) n=4 | -3.11 (0.00) n=4 | -2.25 (0.00) n=4 | -1.58 (0.00) n=4 | -4.35 |
| B5 | NY-PM | 4 | -4.73 (0.00) n=4 | -3.00 (0.00) n=4 | -3.14 (0.00) n=4 | -2.60 (0.00) n=4 | -1.93 (0.00) n=4 | -4.34 |
| B5 | CLOSE | 4 | -3.19 (0.00) n=4 | -2.81 (0.00) n=4 | -2.57 (0.00) n=4 | -2.20 (0.00) n=4 | -1.85 (0.00) n=4 | -3.56 |
| B5 | NY | 4 | -3.12 (0.00) n=4 | -2.95 (0.00) n=4 | -2.99 (0.00) n=4 | -2.43 (0.00) n=4 | -1.47 (0.00) n=4 | -4.17 |
| B6 | ALL | 4 | -0.92 (0.50) n=4 | -2.94 (0.00) n=4 | -2.97 (0.00) n=4 | -2.30 (0.00) n=4 | -0.54 (0.50) n=4 | -4.19 |
| B6 | ASIA | 4 | -3.04 (0.00) n=4 | -2.70 (0.25) n=4 | -1.91 (0.25) n=4 | -0.74 (0.50) n=4 | -0.69 (0.00) n=3 | -3.16 |
| B6 | LONDON | 4 | -4.49 (0.00) n=3 | -3.20 (0.25) n=4 | -2.95 (0.25) n=4 | -3.09 (0.00) n=4 | -1.12 (0.00) n=3 | -4.21 |
| B6 | PRE | 4 | -7.00 (0.00) n=2 | -3.13 (0.00) n=4 | -1.94 (0.00) n=4 | 0.32 (0.50) n=4 | 0.57 (0.50) n=4 | -3.19 |
| B6 | NY-AM | 4 | -2.52 (0.33) n=3 | -5.40 (0.00) n=4 | -4.60 (0.00) n=4 | -2.23 (0.00) n=4 | -0.74 (0.25) n=4 | -5.84 |
| B6 | NY-PM | 4 | -2.46 (0.00) n=2 | -2.05 (0.00) n=4 | -2.10 (0.00) n=4 | -6.17 (0.00) n=4 | -0.76 (0.25) n=4 | -3.31 |
| B6 | CLOSE | 4 | -0.90 (0.50) n=4 | -0.35 (0.50) n=4 | 0.05 (0.50) n=4 | -1.60 (0.00) n=4 | -0.52 (0.25) n=4 | -0.97 |
| B6 | NY | 4 | 0.72 (0.50) n=4 | -3.14 (0.00) n=4 | -2.89 (0.00) n=4 | -3.02 (0.00) n=4 | -1.21 (0.25) n=4 | -4.08 |
| B7 | ALL | 8 | -2.95 (0.29) n=7 | -2.52 (0.00) n=8 | -2.04 (0.12) n=8 | -3.86 (0.12) n=8 | -1.57 (0.25) n=8 | -3.24 |
| B7 | ASIA | 8 | - | -9.81 (0.43) n=7 | -7.07 (0.43) n=7 | -2.46 (0.38) n=8 | -1.32 (0.43) n=7 | -8.33 |
| B7 | LONDON | 8 | - | 3.92 (0.67) n=3 | 1.87 (0.67) n=6 | -6.67 (0.25) n=8 | -4.07 (0.43) n=7 | 0.62 |
| B7 | PRE | 8 | - | - | - | -2.24 (0.38) n=8 | -2.73 (0.20) n=5 |  |
| B7 | NY-AM | 8 | - | -4.75 (0.12) n=8 | -5.24 (0.12) n=8 | -1.48 (0.50) n=8 | -2.56 (0.14) n=7 | -6.47 |
| B7 | NY-PM | 8 | - | -3.86 (0.20) n=5 | -5.05 (0.20) n=5 | -3.93 (0.25) n=8 | -0.60 (0.50) n=6 | -6.17 |
| B7 | CLOSE | 8 | - | - | -2.13 (0.50) n=2 | -0.48 (0.50) n=6 | -5.39 (0.40) n=5 | -3.11 |
| B7 | NY | 8 | -3.56 (0.50) n=2 | -2.63 (0.00) n=8 | -2.49 (0.12) n=8 | -2.12 (0.25) n=8 | -1.65 (0.00) n=8 | -3.66 |

## 2. CANDIDATE-RECENT cells (2026 > 0 and last 6 months > 0; n_L6M >= 30), ranked by last 6 months (HOLD tie-break). NOT a V2 tier; every one fails a registered gate
2026 is ~5 weeks (26 label days): its MDE per trade is 3-10x the plausible effect. $/wk = locked weekly mean at $1,000 risk per trade (exact lock engine); MDE = 2.8 SD/sqrt(n) per trade.
| rank | cell | ES | session | 2026 n / pts / MDE | L6M n / pts / $wk / MDE | HOLD n / pts / $wk | PRE n / pts / t | X' n / pts | HOLD stress | placebo-b p (PRE) | stack add HOLD 20% $/wk | max corr to live book | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | B2_r20_R100 | ES | LONDON | 9 / 16.55 / 54.46 | 31 / 17.86 / 330 / 27.91 | 34 / 21.18 / 375 | 121 / -4.90 / -0.91 | 21 / 7.09 | 19.93 | 0.64 | 9338 | 0.09 (PE) | G1,G4,G5,G7 |
| 2 | B2_r10_SHL | ES | LONDON | 8 / 11.69 / 59.80 | 30 / 16.60 / 297 / 28.62 | 36 / 13.36 / 251 | 116 / -5.65 / -1.03 | 71 / -7.67 | 12.11 | 0.79 | 4978 | 0.08 (SM) | G1,G2,G4,G5,G7 |
| 3 | B2_r20_R50 | ES | LONDON | 12 / 16.55 / 46.45 | 58 / 13.25 / 391 / 20.82 | 65 / 14.21 / 423 | 241 / -1.72 / -0.45 | 33 / 3.98 | 12.96 | 0.38 | 7099 | 0.23 (HM) | G1,G4,G5,G7 |
| 4 | B3_m3_w10_VWB | ALL | CLOSE | 8 / 30.88 / 41.26 | 52 / 11.32 / 350 / 17.03 | 63 / 11.31 / 371 | 197 / -1.01 / -0.31 | 104 / 3.76 | 10.29 | 0.40 | 7082 | 0.19 (SM) | G1,G4,G5 |
| 5 | B7_d10_cont | ES | ASIA | 9 / 3.59 / 57.41 | 32 / 8.09 / 154 / 28.84 | 38 / 3.29 / 65 | 92 / 0.72 / 0.12 | 40 / 8.97 | 2.03 | 0.17 | 1562 | 0.31 (PE) | G1,G4,G5,G6 |
| 6 | B7_d05_cont | ALL | ASIA | 10 / 8.77 / 53.36 | 57 / 6.36 / 216 / 21.58 | 66 / 2.45 / 84 | 113 / 1.73 / 0.31 | 60 / -4.90 | 1.20 | 0.12 | 1864 | 0.29 (PE) | G1,G2,G4,G5,G7 |
| 7 | B3_m2_w10_VWB | ALL | CLOSE | 13 / 17.75 / 33.80 | 69 / 6.30 / 295 / 15.20 | 80 / 6.84 / 317 | 239 / 0.28 / 0.10 | 133 / 0.45 | 5.81 | 0.17 | 5850 | 0.20 (SM) | G1,G4,G5 |
| 8 | B3_m3_w30_VWB | ALL | CLOSE | 11 / 25.50 / 33.73 | 63 / 6.28 / 272 / 15.99 | 74 / 7.02 / 303 | 226 / -1.03 / -0.34 | 119 / 2.64 | 5.99 | 0.44 | 5407 | 0.15 (SM) | G1,G4,G5,G7 |
| 9 | B2_r20_PDL | ES | ALL | 15 / 5.43 / 41.76 | 55 / 5.76 / 188 / 20.39 | 62 / 4.56 / 147 | 168 / 3.11 / 0.72 | 58 / 6.77 | 3.40 | 0.17 | 3037 | 0.24 (KB) | G1,G4,G5 |
| 10 | B2_r10_PDL | ES | NY-AM | 7 / 5.44 / 66.02 | 39 / 5.55 / 129 / 25.67 | 45 / 5.52 / 129 | 82 / 9.74 / 1.54 | 29 / 12.90 | 4.30 | 0.04 | 3071 | 0.15 (KB) | G1,G5,G7 |
| 11 | B3_m3_w30_PDL | ALL | LONDON | 4 / 26.28 / 81.70 | 42 / 5.49 / 141 / 25.28 | 48 / 2.01 / 53 | 113 / -2.62 / -0.47 | 58 / -8.90 | 0.76 | 0.47 | 1278 | 0.21 (SM) | G1,G2,G4,G5,G7 |
| 12 | B3_m2_w30_VWB | ALL | CLOSE | 14 / 20.14 / 32.33 | 77 / 5.29 / 279 / 14.61 | 89 / 5.15 / 271 | 256 / -0.98 / -0.34 | 138 / 0.18 | 4.11 | 0.38 | 4789 | 0.13 (SM) | G1,G4,G5,G7 |
| 13 | B3_m3_w10_ORE | ALL | CLOSE | 8 / 8.10 / 57.66 | 49 / 4.78 / 124 / 18.33 | 57 / 4.49 / 120 | 176 / -0.28 / -0.08 | 62 / 0.98 | 3.47 | 0.41 | 2938 | 0.07 (HM) | G1,G4,G5,G7 |
| 14 | B2_r10_SHL | ALL | LONDON | 10 / 8.77 / 53.36 | 46 / 4.76 / 130 / 24.17 | 53 / 2.65 / 73 | 158 / -3.93 / -0.83 | 134 / -4.30 | 1.40 | 0.77 | 1362 | 0.08 (WT) | G1,G2,G4,G5,G7 |
| 15 | B6_b | ES | LONDON | 23 / 4.71 / 34.54 | 117 / 4.63 / 227 / 15.06 | 119 / 4.15 / 173 | 179 / -13.07 / -3.00 | 25 / -8.63 | 2.90 | 0.99 | 3767 | 0.11 (ST) | G1,G2,G4,G5,G7 |
| 16 | B7_d10_fade | ALL | LONDON | 8 / 11.69 / 59.80 | 58 / 4.57 / 158 / 21.32 | 70 / 3.30 / 120 | 183 / -6.26 / -1.43 | 108 / -4.71 | 2.05 | 0.86 | 2061 | 0.31 (PE) | G1,G2,G4,G5,G7 |
| 17 | B7_d10_cont | ALL | ASIA | 18 / 3.59 / 39.38 | 84 / 4.09 / 139 / 17.82 | 97 / 1.36 / -18 | 170 / 2.85 / 0.63 | 99 / 1.90 | 0.10 | 0.05 | -298 | 0.28 (PE) | G1,G5,G6,G7 |
| 18 | B2_r20_SHL | ALL | ALL | 14 / 13.78 / 43.43 | 54 / 4.09 / 132 / 21.71 | 57 / 4.75 / 141 | 201 / -2.30 / -0.57 | 150 / 3.35 | 3.53 | 0.65 | 2709 | 0.30 (ST) | G1,G4,G5,G7 |
| 19 | B2_r10_SHL | ALL | NY | 11 / 25.73 / 40.44 | 47 / 4.02 / 113 / 21.50 | 53 / 4.72 / 130 | 149 / -0.81 / -0.19 | 136 / 0.71 | 3.60 | 0.46 | 2932 | 0.25 (ST) | G1,G4,G5,G7 |
| 20 | B2_r20_VWB | ALL | CLOSE | 8 / 11.42 / 51.52 | 37 / 3.94 / 123 / 20.69 | 44 / 3.05 / 102 | 149 / -0.90 / -0.24 | 73 / 0.82 | 2.04 | 0.42 | 2394 | 0.18 (HM) | G1,G4,G5,G7 |
| 21 | B7_d10_fade | ES | LONDON | 7 / 5.44 / 66.02 | 55 / 3.92 / 128 / 21.93 | 67 / 2.71 / 94 | 166 / -7.09 / -1.54 | 64 / -8.25 | 1.46 | 0.84 | 1733 | 0.25 (PE) | G1,G2,G4,G5,G7 |
| 22 | B2_r10_ORE | ALL | CLOSE | 7 / 17.05 / 58.24 | 43 / 3.84 / 98 / 18.75 | 51 / 4.89 / 130 | 156 / -0.84 / -0.25 | 77 / 2.85 | 3.91 | 0.46 | 3089 | 0.16 (HM) | G1,G4,G5,G7 |
| 23 | B3_m3_w10_ORE | ES | CLOSE | 3 / 55.46 / 0.00 | 30 / 3.56 / 64 / 22.95 | 36 / 3.85 / 72 | 111 / -1.70 / -0.42 | 21 / 6.66 | 2.87 | 0.55 | 2173 | 0.04 (SM) | G1,G4,G5,G7 |
| 24 | B3_m2_w30_PDL | ALL | LONDON | 6 / 16.55 / 68.89 | 47 / 3.36 / 97 / 23.97 | 54 / 1.47 / 44 | 128 / -3.02 / -0.58 | 70 / -7.62 | 0.22 | 0.53 | 978 | 0.20 (SM) | G1,G2,G4,G5,G7 |
| 25 | B3_m2_w10_PDL | ALL | LONDON | 5 / 8.77 / 80.05 | 40 / 2.99 / 108 / 26.05 | 47 / 0.87 / 53 | 115 / -2.65 / -0.48 | 62 / -4.56 | -0.38 | 0.53 | 1219 | 0.18 (SM) | G1,G2,G4,G5,G7 |
| 26 | B3_m3_w10_VWB | ES | CLOSE | 5 / 26.03 / 63.29 | 32 / 2.66 / 51 / 23.08 | 40 / 2.60 / 54 | 132 / 2.63 / 0.67 | 39 / 3.51 | 1.57 | 0.09 | 1229 | 0.11 (WT) | G1,G4,G5 |
| 27 | B2_r10_SHL | ES | ALL | 21 / 2.12 / 35.55 | 105 / 2.59 / 94 / 15.33 | 117 / 0.64 / -20 | 331 / -6.38 / -2.06 | 165 / 0.65 | -0.57 | 0.94 | -273 | 0.23 (ST) | G1,G4,G5,G6,G7 |
| 28 | B3_m3_w30_VWB | ES | CLOSE | 8 / 23.67 / 41.62 | 46 / 2.47 / 68 / 19.15 | 54 / 2.45 / 69 | 155 / 1.83 / 0.52 | 46 / 4.67 | 1.42 | 0.11 | 1472 | 0.11 (WT) | G1,G4,G5 |
| 29 | B2_r20_SHL | ES | ALL | 10 / 8.77 / 53.36 | 38 / 2.32 / 52 / 25.61 | 39 / 0.69 / 14 | 160 / -5.34 / -1.20 | 68 / 2.82 | -0.52 | 0.80 | 296 | 0.33 (ST) | G1,G4,G5,G7 |
| 30 | B2_r10_SHL | ES | NY | 6 / 24.39 / 57.58 | 32 / 2.23 / 42 / 25.26 | 35 / 2.16 / 39 | 122 / -7.04 / -1.51 | 69 / 2.15 | 1.05 | 0.91 | 949 | 0.33 (ST) | G1,G4,G5,G7 |
| 31 | B3_m2_w10_ORE | ALL | CLOSE | 8 / 7.95 / 57.61 | 57 / 2.04 / 54 / 16.99 | 67 / 2.67 / 80 | 199 / 1.93 / 0.63 | 86 / 3.53 | 1.67 | 0.13 | 1896 | 0.19 (HM) | G1,G4,G5,G7 |
| 32 | B2_r20_R100 | ALL | ASIA | 15 / 0.99 / 43.57 | 49 / 1.94 / 23 / 23.28 | 53 / 1.58 / 15 | 143 / 2.16 / 0.44 | 28 / -5.72 | 0.33 | 0.13 | 344 | 0.12 (HM) | G1,G2,G4,G5,G7 |
| 33 | B3_m2_w30_VWB | ES | CLOSE | 10 / 11.81 / 40.84 | 58 / 1.86 / 64 / 16.87 | 68 / 2.47 / 87 | 196 / 0.15 / 0.05 | 63 / -1.51 | 1.45 | 0.24 | 1785 | 0.10 (SM) | G1,G2,G4,G5,G7 |
| 34 | B7_d10_fade | ALL | NY-AM | 20 / 14.61 / 35.76 | 109 / 1.84 / 123 / 15.42 | 130 / 2.32 / 131 | 276 / -5.75 / -1.63 | 159 / -2.56 | 1.09 | 0.90 | 2032 | 0.26 (ST) | G1,G2,G4,G5,G7 |
| 35 | B3_m2_w10_VWB | ES | CLOSE | 9 / 7.19 / 43.03 | 46 / 1.68 / 46 / 18.42 | 55 / 1.51 / 43 | 175 / 1.85 / 0.53 | 60 / -0.67 | 0.51 | 0.11 | 958 | 0.17 (SM) | G1,G2,G4,G5 |
| 36 | B2_r20_R50 | ALL | ASIA | 35 / 18.78 / 26.02 | 116 / 1.68 / 53 / 15.13 | 125 / -0.05 / -58 | 273 / -0.77 / -0.22 | 46 / 1.15 | -1.30 | 0.21 | -984 | 0.08 (HM) | G1,G3,G4,G5,G6,G7 |
| 37 | B6_b | ES | CLOSE | 30 / 5.04 / 26.17 | 86 / 1.43 / 75 / 14.23 | 102 / 2.73 / 114 | 305 / -1.96 / -0.71 | 51 / -3.50 | 1.69 | 0.59 | 2640 | 0.09 (KB) | G1,G2,G4,G5,G7 |
| 38 | B3_m2_w10_ORE | ES | CLOSE | 5 / 8.77 / 80.05 | 37 / 1.35 / 30 / 20.89 | 43 / 1.89 / 42 | 143 / -1.58 / -0.45 | 31 / 5.59 | 0.90 | 0.52 | 1129 | 0.17 (PE) | G1,G4,G5,G7 |
| 39 | B3_m3_w30_PDL | ALL | CLOSE | 10 / 9.19 / 40.71 | 33 / 1.27 / 25 / 19.88 | 44 / -1.32 / -30 | 82 / -4.52 / -0.88 | 34 / 5.58 | -2.29 | 0.70 | -1037 | 0.23 (SM) | G1,G3,G4,G5,G6,G7 |
| 40 | B2_r10_VWB | ES | NY-AM | 27 / 2.34 / 31.42 | 101 / 0.91 / 91 / 15.90 | 120 / 0.70 / 75 | 228 / -12.23 / -3.26 | 106 / 7.77 | -0.52 | 1.00 | 1224 | 0.12 (HM) | G1,G4,G5,G7 |

Spec of each listed cell family (for the monitor list; no D6 spec is issued because none is registered):
- B2_r20_R100: iceberg: 10-s consumed/mean displayed best >= 20 at R100 level (<=2 ticks), best not lower than window start, enter on 2-tick move away within 60 s
- B2_r10_SHL: iceberg: 10-s consumed/mean displayed best >= 10 at SHL level (<=2 ticks), best not lower than window start, enter on 2-tick move away within 60 s
- B2_r20_R50: iceberg: 10-s consumed/mean displayed best >= 20 at R50 level (<=2 ticks), best not lower than window start, enter on 2-tick move away within 60 s
- B3_m3_w10_VWB: failed sweep: sweep >= 3 levels beyond VWB level, reclaimed within 10 s (mid 1 tick back, 10-s delta turned) -> reclaim direction
- B3_m2_w10_VWB: failed sweep: sweep >= 2 levels beyond VWB level, reclaimed within 10 s (mid 1 tick back, 10-s delta turned) -> reclaim direction
- B3_m3_w30_VWB: failed sweep: sweep >= 3 levels beyond VWB level, reclaimed within 30 s (mid 1 tick back, 10-s delta turned) -> reclaim direction
- B6_b: side depth10 / trailing-hour mean from <= 0.5 to >= 1.5 within 60 s (wall appears); trade away from the wall
- B7_d10_cont: vpin50 in trailing-5-day top 10% with price within 5 ticks of the session extreme; CONTINUATION (with the extreme)
- B7_d05_cont: vpin50 in trailing-5-day top 5% with price within 5 ticks of the session extreme; CONTINUATION (with the extreme)
- B7_d10_fade: vpin50 in trailing-5-day top 10% with price within 5 ticks of the session extreme; FADE (against the extreme)

## 3. Highest PRE t cells (selection window), all failing G0 or later gates
| cell | ES | session | PRE n / pts / t | X' pts | HOLD n / pts | L6M pts | 2026 pts | RC p | failed |
|---|---|---|---|---|---|---|---|---|---|
| B2_r20_SHL | ALL | CLOSE | 27 / 17.24 / 2.29 | 5.02 | 5 / 26.77 | 26.77 | 55.46 | 1.000 | G0,G5 |
| B3_m2_w30_PDL | ES | PRE | 38 / 20.09 / 2.21 | -30.89 | 8 / -17.49 | -11.23 | 55.46 | 1.000 | G0,G2,G3,G5,G6,G7 |
| B3_m3_w10_PDL | ES | NY-AM | 102 / 10.76 / 1.90 | 3.23 | 45 / -14.90 | -14.24 | -2.90 | 1.000 | G1,G3,G5,G6,G7 |
| B3_m2_w10_PDL | ALL | NY-AM | 170 / 8.00 / 1.80 | 0.55 | 81 / -5.48 | -6.24 | 0.99 | 1.000 | G1,G3,G5,G6,G7 |
| B3_m2_w10_PDL | ES | NY-AM | 121 / 9.31 / 1.78 | 5.65 | 60 / -10.53 | -10.89 | 10.57 | 1.000 | G1,G3,G5,G6,G7 |
| B7_d10_cont | ES | NY-AM | 114 / 9.61 / 1.78 | -4.30 | 71 / -6.87 | -8.40 | -29.42 | 1.000 | G1,G2,G3,G4,G5,G6,G7 |
| B2_r10_VWB | ES | PRE | 47 / 14.69 / 1.74 | -3.39 | 14 / -27.88 | -27.88 | -61.25 | 1.000 | G0,G1,G2,G3,G4,G5,G6,G7 |
| B3_m2_w30_PDL | ALL | NY-AM | 180 / 7.28 / 1.69 | 1.79 | 84 / -7.46 | -8.43 | 0.99 | 1.000 | G1,G3,G5,G6,G7 |
| B3_m2_w30_PDL | ALL | PRE | 58 / 12.41 / 1.63 | -8.84 | 17 / -6.31 | -7.37 | 32.12 | 1.000 | G0,G1,G2,G3,G5,G6,G7 |
| B2_r20_SHL | ES | CLOSE | 21 / 14.40 / 1.62 | -0.56 | 5 / 26.77 | 26.77 | 55.46 | 1.000 | G0,G1,G2,G5 |
| B2_r10_PDL | ALL | NY-AM | 129 / 7.98 / 1.57 | 3.22 | 62 / -0.30 | -0.79 | 8.77 | 1.000 | G1,G3,G5,G6,G7 |
| B3_m2_w10_PDL | ES | PRE | 29 / 16.68 / 1.56 | -36.24 | 8 / -17.49 | -11.23 | 55.46 | 1.000 | G0,G1,G2,G3,G4,G5,G6,G7 |
| B3_m3_w30_PDL | ES | PRE | 29 / 16.58 / 1.55 | -46.30 | 5 / -14.57 | -2.90 | 55.46 | 1.000 | G0,G1,G2,G3,G4,G5,G6,G7 |
| B2_r10_PDL | ES | NY-AM | 82 / 9.74 / 1.54 | 12.90 | 45 / 5.52 | 5.55 | 5.44 | 1.000 | G1,G5,G7 |
| B3_m3_w10_PDL | ALL | NY-AM | 144 / 7.07 / 1.46 | -0.44 | 72 / -6.61 | -6.65 | 2.41 | 1.000 | G1,G2,G3,G5,G6,G7 |

## 4. Gate funnel (session cells at 60/60, MEASURED)
| gate | definition | cells passing |
|---|---|---|
| G0 | n_PRE>=60 and n_HOLD>=20 | 630 of 1133 |
| G1 | PRE mean>0 and t>=2 | 13 of 1133 |
| G2 | X' mean>0 | 357 of 1133 |
| G3 | HOLD>0 and L6M>0 | 183 of 1133 |
| G4 | beats both placebos (p<=0.05, PRE) | 20 of 1133 |
| G5 | White RC p<=0.05 (PRE weekly $) | 0 of 1133 |
| G6 | stack add 20%: HOLD d_mean>0, d_Sharpe>0 | 171 of 1133 |
| G7 | year share <=60% | 36 of 1133 |
| G0..G7 all | PASS | 0 |
G8 (beats own flip) was only to be run for cells passing G0-G7: none, so not run.

## 5. Bracket grid {30,60,90}x{30,60,90} (sensitivity; 9 brackets x all session cells = charged in the extended best-of-N)
| family | bracket cells with n_PRE>=60 | PRE t>=2 (any bracket) | PRE t>=2 and X'>0 and HOLD>0 and L6M>0 | best PRE t | 60/60 best PRE t |
|---|---|---|---|---|---|
| B1 | 179 | 1 | 0 | 2.22 | 0.27 |
| B2 | 1288 | 1 | 0 | 2.56 | 1.57 |
| B3 | 3143 | 8 | 0 | 3.34 | 1.90 |
| B4 | 99 | 0 | 0 | 1.08 | 1.00 |
| B5 | 288 | 0 | 0 | -0.27 | -0.30 |
| B6 | 288 | 0 | 0 | 1.02 | 0.40 |
| B7 | 486 | 0 | 0 | 1.78 | 1.78 |

Extended family size 13,248 bracket-session cells (prereg); with ~5% expected false positives at t>=2 one-sided ~2.5% the counts above are what chance alone predicts (n bracket cells x 0.023), see column 2.

## 6. Live blocks vs none, and stress label
Across the 168 populated (cell, ES) ALL-session books at 60/60: median pts/trade L6M LIVE -4.11 vs NOBLK(09:00-09:59 allowed) -4.13; HOLD -4.04 vs -3.98; PRE -2.80 vs -2.72. Stress minus measured (HOLD, session cells with n>=30): median -1.22 pts/trade.

## 7. Walk-forward re-selection (monthly; top-5 (cell,ES) per session by trailing 6 months, n>=30; scored the next month) vs all cells
| session | months | selected trades | selected pts/trade | all-cells pts/trade | selected 2026 pts/trade (n) | selected L6M pts/trade (n) |
|---|---|---|---|---|---|---|
| ASIA | 19 | 1314 | -7.22 | -3.53 | -3.42 (224) | -9.65 (525) |
| LONDON | 19 | 1299 | -4.72 | -3.02 | -1.45 (121) | -0.06 (271) |
| PRE | 19 | 1160 | -6.63 | -3.26 | -12.62 (24) | -6.95 (415) |
| NY-AM | 19 | 1470 | -1.61 | -3.45 | -4.71 (179) | -3.26 (1015) |
| NY-PM | 19 | 1293 | -6.68 | -2.97 | -3.98 (51) | -2.94 (231) |
| CLOSE | 19 | 904 | -0.14 | -2.47 | 16.75 (46) | 0.72 (227) |

LAST re-fit (data to 2026-02-06; trailing 6 months 2025-08-01..2026-02-06, n>=30): the top-5 per session. This is what an adaptive run would hold tonight if it ran this layer; none clears a gate and none is recommended.
| session | rank | cell | ES | trailing n | trailing pts/trade | trailing t | spec |
|---|---|---|---|---|---|---|---|
| ASIA | 1 | B7_d10_cont | ES | 32 | 8.09 | 0.79 | vpin50 in trailing-5-day top 10% with price within 5 ticks of the session extreme; CONTINUATION (with the extreme) |
| ASIA | 2 | B7_d05_cont | ALL | 57 | 6.36 | 0.83 | vpin50 in trailing-5-day top 5% with price within 5 ticks of the session extreme; CONTINUATION (with the extreme) |
| ASIA | 3 | B7_d10_cont | ALL | 84 | 4.09 | 0.64 | vpin50 in trailing-5-day top 10% with price within 5 ticks of the session extreme; CONTINUATION (with the extreme) |
| ASIA | 4 | B2_r20_R100 | ALL | 49 | 1.94 | 0.23 | iceberg: 10-s consumed/mean displayed best >= 20 at R100 level (<=2 ticks), best not lower than window start, enter on 2-tick move away within 60 s |
| ASIA | 5 | B2_r20_R50 | ALL | 116 | 1.68 | 0.31 | iceberg: 10-s consumed/mean displayed best >= 20 at R50 level (<=2 ticks), best not lower than window start, enter on 2-tick move away within 60 s |
| LONDON | 1 | B2_r20_R100 | ES | 31 | 17.86 | 1.79 | iceberg: 10-s consumed/mean displayed best >= 20 at R100 level (<=2 ticks), best not lower than window start, enter on 2-tick move away within 60 s |
| LONDON | 2 | B2_r10_SHL | ES | 30 | 16.60 | 1.62 | iceberg: 10-s consumed/mean displayed best >= 10 at SHL level (<=2 ticks), best not lower than window start, enter on 2-tick move away within 60 s |
| LONDON | 3 | B2_r20_R50 | ES | 58 | 13.25 | 1.78 | iceberg: 10-s consumed/mean displayed best >= 20 at R50 level (<=2 ticks), best not lower than window start, enter on 2-tick move away within 60 s |
| LONDON | 4 | B2_r10_R100 | ES | 117 | 9.64 | 1.84 | iceberg: 10-s consumed/mean displayed best >= 10 at R100 level (<=2 ticks), best not lower than window start, enter on 2-tick move away within 60 s |
| LONDON | 5 | B3_m3_w30_PDL | ALL | 42 | 5.49 | 0.61 | failed sweep: sweep >= 3 levels beyond PDL level, reclaimed within 30 s (mid 1 tick back, 10-s delta turned) -> reclaim direction |
| PRE | 1 | B3_m3_w10_SHL | ALL | 39 | 7.63 | 0.82 | failed sweep: sweep >= 3 levels beyond SHL level, reclaimed within 10 s (mid 1 tick back, 10-s delta turned) -> reclaim direction |
| PRE | 2 | B3_m2_w10_SHL | ALL | 40 | 5.91 | 0.64 | failed sweep: sweep >= 2 levels beyond SHL level, reclaimed within 10 s (mid 1 tick back, 10-s delta turned) -> reclaim direction |
| PRE | 3 | B3_m2_w30_SHL | ES | 32 | 4.45 | 0.43 | failed sweep: sweep >= 2 levels beyond SHL level, reclaimed within 30 s (mid 1 tick back, 10-s delta turned) -> reclaim direction |
| PRE | 4 | B3_m2_w30_SHL | ALL | 44 | 2.46 | 0.28 | failed sweep: sweep >= 2 levels beyond SHL level, reclaimed within 30 s (mid 1 tick back, 10-s delta turned) -> reclaim direction |
| PRE | 5 | B2_r20_R50 | ALL | 78 | 0.14 | 0.02 | iceberg: 10-s consumed/mean displayed best >= 20 at R50 level (<=2 ticks), best not lower than window start, enter on 2-tick move away within 60 s |
| NY-AM | 1 | B2_r10_PDL | ES | 39 | 5.55 | 0.61 | iceberg: 10-s consumed/mean displayed best >= 10 at PDL level (<=2 ticks), best not lower than window start, enter on 2-tick move away within 60 s |
| NY-AM | 2 | B7_d10_fade | ALL | 109 | 1.84 | 0.33 | vpin50 in trailing-5-day top 10% with price within 5 ticks of the session extreme; FADE (against the extreme) |
| NY-AM | 3 | B2_r10_VWB | ES | 101 | 0.91 | 0.16 | iceberg: 10-s consumed/mean displayed best >= 10 at VWB level (<=2 ticks), best not lower than window start, enter on 2-tick move away within 60 s |
| NY-AM | 4 | B3_m3_w10_R100 | ES | 306 | -0.55 | -0.17 | failed sweep: sweep >= 3 levels beyond R100 level, reclaimed within 10 s (mid 1 tick back, 10-s delta turned) -> reclaim direction |
| NY-AM | 5 | B2_r10_PDL | ALL | 54 | -0.79 | -0.10 | iceberg: 10-s consumed/mean displayed best >= 10 at PDL level (<=2 ticks), best not lower than window start, enter on 2-tick move away within 60 s |
| NY-PM | 1 | B7_d10_cont | ALL | 54 | 2.87 | 0.40 | vpin50 in trailing-5-day top 10% with price within 5 ticks of the session extreme; CONTINUATION (with the extreme) |
| NY-PM | 2 | B3_m2_w30_SHL | ALL | 135 | 0.79 | 0.17 | failed sweep: sweep >= 2 levels beyond SHL level, reclaimed within 30 s (mid 1 tick back, 10-s delta turned) -> reclaim direction |
| NY-PM | 3 | B2_r20_VWB | ES | 38 | 0.04 | 0.00 | iceberg: 10-s consumed/mean displayed best >= 20 at VWB level (<=2 ticks), best not lower than window start, enter on 2-tick move away within 60 s |
| NY-PM | 4 | B6_b | ES | 92 | -0.15 | -0.02 | side depth10 / trailing-hour mean from <= 0.5 to >= 1.5 within 60 s (wall appears); trade away from the wall |
| NY-PM | 5 | B3_m3_w30_R100 | ALL | 452 | -0.46 | -0.18 | failed sweep: sweep >= 3 levels beyond R100 level, reclaimed within 30 s (mid 1 tick back, 10-s delta turned) -> reclaim direction |
| CLOSE | 1 | B3_m3_w10_VWB | ALL | 52 | 11.32 | 1.86 | failed sweep: sweep >= 3 levels beyond VWB level, reclaimed within 10 s (mid 1 tick back, 10-s delta turned) -> reclaim direction |
| CLOSE | 2 | B3_m2_w10_VWB | ALL | 69 | 6.30 | 1.16 | failed sweep: sweep >= 2 levels beyond VWB level, reclaimed within 10 s (mid 1 tick back, 10-s delta turned) -> reclaim direction |
| CLOSE | 3 | B3_m3_w30_VWB | ALL | 63 | 6.28 | 1.10 | failed sweep: sweep >= 3 levels beyond VWB level, reclaimed within 30 s (mid 1 tick back, 10-s delta turned) -> reclaim direction |
| CLOSE | 4 | B3_m2_w30_VWB | ALL | 77 | 5.29 | 1.01 | failed sweep: sweep >= 2 levels beyond VWB level, reclaimed within 30 s (mid 1 tick back, 10-s delta turned) -> reclaim direction |
| CLOSE | 5 | B3_m3_w10_ORE | ALL | 49 | 4.78 | 0.73 | failed sweep: sweep >= 3 levels beyond ORE level, reclaimed within 10 s (mid 1 tick back, 10-s delta turned) -> reclaim direction |

## 8. Overlap with the live books (pairwise weekly P&L correlation, PRE+HOLD weeks) and marginal add to the stack - for the top CANDIDATE-RECENT cells
Stack add = cell weekly series scaled to 10/20/30% of the live stack PRE weekly SD, added to the stack weekly P&L (stack locks NOT re-run: approximate), HOLD window. Cells are all inside their MDE; adds are shown for completeness.
| cell | ES | session | HM | KB | PE | SM | ST | WT | add10 $/wk (dSD) | add20 | add30 |
|---|---|---|---|---|---|---|---|---|---|---|---|
| B2_r20_R100 | ES | LONDON | -0.09 | -0.02 | 0.09 | -0.04 | -0.03 | -0.08 | 4669 (3038) | 9338 (6627) | 14007 (10733) |
| B2_r10_SHL | ES | LONDON | 0.06 | 0.06 | 0.00 | 0.08 | 0.05 | 0.08 | 2489 (-718) | 4978 (-883) | 7467 (-492) |
| B2_r20_R50 | ES | LONDON | -0.23 | -0.02 | -0.07 | 0.02 | -0.01 | 0.02 | 3549 (1161) | 7099 (2702) | 10648 (4612) |
| B3_m3_w10_VWB | ALL | CLOSE | 0.08 | -0.08 | -0.05 | 0.19 | 0.08 | -0.05 | 3541 (1506) | 7082 (3692) | 10623 (6530) |
| B7_d10_cont | ES | ASIA | 0.13 | 0.17 | 0.31 | 0.02 | 0.22 | 0.05 | 781 (3581) | 1562 (7551) | 2343 (11883) |
| B7_d05_cont | ALL | ASIA | 0.09 | -0.08 | 0.29 | 0.17 | -0.06 | -0.07 | 932 (-667) | 1864 (976) | 2796 (4855) |
| B3_m2_w10_VWB | ALL | CLOSE | 0.13 | 0.02 | -0.02 | 0.20 | 0.06 | -0.02 | 2925 (1722) | 5850 (3976) | 8775 (6738) |
| B3_m3_w30_VWB | ALL | CLOSE | 0.06 | -0.05 | -0.04 | 0.15 | 0.07 | -0.03 | 2704 (1180) | 5407 (3103) | 8111 (5744) |
| B2_r20_PDL | ES | ALL | 0.11 | 0.24 | 0.07 | -0.06 | -0.06 | -0.14 | 1518 (-696) | 3037 (-584) | 4555 (337) |
| B2_r10_PDL | ES | NY-AM | 0.06 | 0.15 | -0.02 | 0.00 | -0.09 | -0.04 | 1535 (1643) | 3071 (4171) | 4606 (7544) |
| B3_m3_w30_PDL | ALL | LONDON | -0.03 | -0.12 | 0.03 | 0.21 | -0.13 | -0.12 | 639 (-3580) | 1278 (-5429) | 1917 (-5480) |
| B3_m2_w30_VWB | ALL | CLOSE | 0.12 | 0.06 | 0.01 | 0.13 | 0.08 | 0.02 | 2395 (1955) | 4789 (4527) | 7184 (7687) |
| B3_m3_w10_ORE | ALL | CLOSE | -0.07 | 0.01 | -0.07 | 0.05 | -0.01 | 0.02 | 1469 (286) | 2938 (1066) | 4408 (2333) |
| B2_r10_SHL | ALL | LONDON | -0.00 | 0.04 | -0.06 | 0.07 | 0.03 | 0.08 | 681 (-290) | 1362 (345) | 2043 (1895) |
| B6_b | ES | LONDON | 0.10 | 0.04 | 0.06 | 0.05 | 0.11 | 0.05 | 1883 (2388) | 3767 (5955) | 5650 (10623) |

## 9. Reading, limits, MDE
- Random-entry baseline (placebo universe, same fills/brackets): about -2.2 pts/trade = cost (fee 0.24 + entry tick 0.25 + stop/time cost ~1 + target correction 1.4-4.3 on the 60-pt targets); every family sits at or below that on every window pooled, so the book state at the entry second carries no net edge at 60/60 after measured fills.
- MDE per trade (80% power): typically 2.8 x SD / sqrt(n) with SD ~ 40-45 pts at 60/60: n=100 -> ~12 pts, n=500 -> ~5 pts, n=2,000 -> ~2.6 pts. Every family-session null above is a null only for effects larger than its MDE; the bigger families (B3, B5, B6) can exclude +2.5 pts/trade, the small ones (B1, B4 strict, B7) cannot exclude +10.
- B1 (absorption) and B4 strict (imb5/imb10 on every row for P s) are too rare (a few dozen events per session in 3 years; 6 prereg cells empty): underpowered, DEAD on G0, not evidence of no effect.
- Event definitions follow prereg + addendum A1 (B2 displayed = window-mean best size; B4 avg cells added). Book prices are raw contract space, fills come from the back-adjusted path (offset checked: path minus book mid is stable to within ~1.5 pts at the 99.9th percentile inside a month); events within 120 s of a roll are dropped.
- 6 prereg cells have zero events (B1 k20 PDL/ORE variants, B4 strict p120 cost, etc.) and are reported as n=0.
- Placebo (a) time-shuffle within day matches (label day, session, side): it removes day-direction beta and is therefore harsher than (b); both reported (cells.csv placebos.parquet).
- Files: out/l2eb/cells_full.csv (all 1,133 populated session cells with gates), out/l2eb/cells.parquet (all brackets), out/l2eb/placebos.parquet; events and trade lists in /mnt/l2/l2vast/ds3_l2eb/.
