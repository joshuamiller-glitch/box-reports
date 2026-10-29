# DS3_ABR_B_ORACLE - bracket space and oracle bounds (T-ADAPTIVE-BRACKETS section B, ABRA, 2026-10-29)
Research only. UNTOUCHED never read. Fees per FEES.md (0.242 pt per contract RT). No account ids. Prereg l2vast/ds3/prereg/ABR_B_prereg.md sha256 bcf6e859bfa821e1a86855f402ad7b7ffad4f3a3c9103f1b9db417ee83cf7685; PRE selections frozen in DS3_ABR_B_PREHOLD.md (sha256 in DECISIONS.md) before HOLD/X were opened; one logged look (out/abr/looks.jsonl, track ABR_B) for groups HG0 pooled, HG1 11 books, HG2 5 sessions, HG3 book x session (48 cells with PRE n >= 150).

## Headline
* Space: 990 brackets (18 stops x 11 targets x 5 time exits) scored on 47,131 entries of 11 books from the 1-s path, measured fills (basis M: stop = -S minus calibrated walk slip, target = +T minus the year target correction, time exit minus 0.995, minus 0.242 fee). The 60/60 control reproduces the stored exit type on every entry checked (Dec 2023, 536 non-WT/CR entries).
* **Pooled fixed-bracket oracle (best single bracket chosen on PRE, abs120 stop / OR-edge target / no time exit):** PRE (IN-SAMPLE) +2.33 pts/trade over 60/60 (CI -2.04..+6.70, MDE80 6.24, White best-of-990 p 0.66). HOLDOUT HOLD +3.17 (MDE 10.87), HOLDOUT X +0.22 (MDE 6.38). Nothing is distinguishable from zero in any window; the PRE gain is inside the best-of-990 noise (RC p 0.66) and does not repeat in X.
* Per book, same bracket frozen: HOLD gain>0 in 8 of 11 books, CI above 0 in 1; X gain>0 in 5 of 11, CI above 0 in 0. Per session: HOLD 5 of 6 positive, X 3 of 6 and one CI below 0. Book x session cells (48): HOLD 31 positive (2 CI>0, 2 CI<0), X 26 positive (4 CI>0, 2 CI<0), mean gain +1.69 (HOLD) and -0.42 (X): no consistent edge once multiplicity (48 cells x 990) is counted.
* **Per-trade oracle (hindsight best of 990 per entry) is about 115-120 pts/trade in PRE and HOLD, 80 in X. UPPER BOUND ONLY, NOT A RESULT**: with 990 draws per trade and paths of hundreds of points it mostly measures path range, not predictability. Any adaptive policy is to be compared with the fixed oracle (+2 to +3 pts/trade in-sample, MDE 6-11), not with this.
* Direction of the fixed oracle: wide stops (75-120 pts) with far targets/no time exit, i.e. holding the position longer with bigger risk. At constant-$-risk lots (RP basis, $12,000/trade risk) the pooled oracle is abs60|R3|none: PRE +350 $/trade vs 60/60 (MDE 633), HOLD +741 (MDE 1,029), X +70 (MDE 870); also not distinguishable from zero.

## Control and LIVE
60/60 (abs60|R1|none) mean M pts/trade pooled: PRE 0.34, HOLD 0.32, X -0.45. LIVE (stored base bracket) PRE 0.24. Net edge of the live bracket is about zero in every window, consistent with the earlier T-BRACKET finding.

## Main table (basis M, pts per lot, constant 10-lot slip; IN-SAMPLE = PRE, HOLDOUT = HOLD, X)
| group | window | label | n | fixed-oracle bracket (PRE-selected) | mean bracket | mean 60/60 | mean LIVE | gain vs 60/60 [95% CI] | MDE80 | per-trade oracle (UPPER BOUND) |
|--|--|--|--|--|--|--|--|--|--|--|
| ALL | PRE | IN-SAMPLE | 26022 | abs120|OR|none | 2.67 | 0.34 | 0.24 | +2.33 [-2.04, +6.70] | 6.24 | 118.6 |
| ALL | HOLD | HOLDOUT | 11396 | abs120|OR|none | 3.49 | 0.32 | 0.23 | +3.17 [-4.44, +10.78] | 10.87 | 115.3 |
| ALL | X | HOLDOUT | 9713 | abs120|OR|none | -0.23 | -0.45 | -0.31 | +0.22 [-4.24, +4.69] | 6.38 | 79.9 |
| ST | PRE | IN-SAMPLE | 3020 | abs75|R3|none | 2.11 | 0.43 | 0.40 | +1.68 [-3.05, +6.41] | 6.76 | 121.1 |
| ST | HOLD | HOLDOUT | 1382 | abs75|R3|none | 4.20 | 1.03 | 0.87 | +3.17 [-4.20, +10.53] | 10.52 | 117.4 |
| ST | X | HOLDOUT | 988 | abs75|R3|none | -0.20 | 0.65 | 0.40 | -0.85 [-6.39, +4.70] | 7.92 | 80.3 |
| HM | PRE | IN-SAMPLE | 2285 | abs120|PD|sess | 3.40 | 0.42 | 0.43 | +2.98 [+0.32, +5.63] | 3.79 | 117.7 |
| HM | HOLD | HOLDOUT | 1008 | abs120|PD|sess | 0.09 | 1.64 | 1.53 | -1.55 [-6.37, +3.28] | 6.89 | 115.6 |
| HM | X | HOLDOUT | 863 | abs120|PD|sess | 1.25 | 0.29 | 0.04 | +0.96 [-1.90, +3.81] | 4.07 | 80.5 |
| WT | PRE | IN-SAMPLE | 4265 | abs120|OR|none | 3.36 | -0.05 | -0.99 | +3.41 [-2.15, +8.97] | 7.94 | 117.5 |
| WT | HOLD | HOLDOUT | 1893 | abs120|OR|none | 3.31 | -0.12 | -1.29 | +3.43 [-4.99, +11.86] | 12.04 | 114.1 |
| WT | X | HOLDOUT | 1527 | abs120|OR|none | 0.08 | -0.37 | -0.03 | +0.45 [-5.40, +6.30] | 8.36 | 78.5 |
| KB | PRE | IN-SAMPLE | 3093 | abs75|R3|none | 4.11 | 1.14 | 1.17 | +2.97 [-0.50, +6.43] | 4.95 | 121.2 |
| KB | HOLD | HOLDOUT | 1374 | abs75|R3|none | 2.66 | -0.85 | -1.04 | +3.50 [-0.88, +7.89] | 6.27 | 114.5 |
| KB | X | HOLDOUT | 1033 | abs75|R3|none | -1.26 | -1.02 | -1.30 | -0.24 [-4.23, +3.75] | 5.70 | 79.0 |
| SM | PRE | IN-SAMPLE | 904 | abs120|OR|none | 5.97 | 2.25 | 2.41 | +3.71 [-2.96, +10.39] | 9.54 | 120.4 |
| SM | HOLD | HOLDOUT | 363 | abs120|OR|none | 14.81 | 1.68 | 1.51 | +13.13 [-0.75, +27.02] | 19.84 | 120.9 |
| SM | X | HOLDOUT | 441 | abs120|OR|none | 7.07 | 0.85 | 0.67 | +6.22 [-1.58, +14.02] | 11.14 | 88.4 |
| PE | PRE | IN-SAMPLE | 3049 | abs120|OR|none | 2.47 | -0.96 | -0.96 | +3.44 [-1.41, +8.29] | 6.93 | 119.1 |
| PE | HOLD | HOLDOUT | 1311 | abs120|OR|none | -2.25 | -1.10 | -1.25 | -1.16 [-9.83, +7.51] | 12.39 | 112.1 |
| PE | X | HOLDOUT | 1001 | abs120|OR|none | -1.09 | 0.98 | 0.71 | -2.07 [-7.73, +3.58] | 8.07 | 79.5 |
| PB | PRE | IN-SAMPLE | 2261 | a5m_2|R3|none | 4.81 | -1.50 | -1.51 | +6.31 [+1.93, +10.70] | 6.27 | 117.4 |
| PB | HOLD | HOLDOUT | 965 | a5m_2|R3|none | 3.03 | 3.45 | 3.29 | -0.42 [-5.03, +4.19] | 6.58 | 118.1 |
| PB | X | HOLDOUT | 823 | a5m_2|R3|none | -0.79 | 1.27 | 1.12 | -2.07 [-4.84, +0.71] | 3.96 | 79.3 |
| DN | PRE | IN-SAMPLE | 1762 | abs75|R3|none | 4.35 | 2.86 | 2.86 | +1.49 [-3.93, +6.92] | 7.75 | 117.4 |
| DN | HOLD | HOLDOUT | 782 | abs75|R3|none | 6.99 | 2.88 | 2.74 | +4.11 [-3.89, +12.11] | 11.43 | 117.3 |
| DN | X | HOLDOUT | 728 | abs75|R3|none | -2.05 | 0.02 | -0.22 | -2.07 [-8.63, +4.48] | 9.36 | 78.4 |
| MV | PRE | IN-SAMPLE | 2922 | abs120|VW|none | 2.77 | 0.85 | 0.79 | +1.92 [-2.68, +6.53] | 6.58 | 121.8 |
| MV | HOLD | HOLDOUT | 1253 | abs120|VW|none | 1.33 | -0.32 | -0.59 | +1.65 [-6.99, +10.29] | 12.34 | 116.0 |
| MV | X | HOLDOUT | 1002 | abs120|VW|none | -3.62 | -3.48 | -3.70 | -0.15 [-6.13, +5.83] | 8.54 | 76.3 |
| MA | PRE | IN-SAMPLE | 1093 | abs120|OR|none | 5.65 | 1.15 | 1.14 | +4.50 [-2.65, +11.65] | 10.21 | 115.6 |
| MA | HOLD | HOLDOUT | 474 | abs120|OR|none | 13.73 | 3.38 | 3.19 | +10.35 [-0.31, +21.01] | 15.23 | 120.3 |
| MA | X | HOLDOUT | 520 | abs120|OR|none | 4.23 | 1.56 | 1.41 | +2.68 [-4.47, +9.82] | 10.21 | 84.4 |
| CR | PRE | IN-SAMPLE | 1368 | abs120|R1.5|120m | 4.14 | -0.90 | 0.24 | +5.05 [+1.14, +8.95] | 5.58 | 109.9 |
| CR | HOLD | HOLDOUT | 591 | abs120|R1.5|120m | -0.21 | -6.76 | -2.09 | +6.55 [+1.61, +11.49] | 7.06 | 107.2 |
| CR | X | HOLDOUT | 787 | abs120|R1.5|120m | -1.71 | -4.32 | -1.03 | +2.61 [-1.55, +6.78] | 5.95 | 82.3 |
| asia | PRE | IN-SAMPLE | 6689 | abs120|VW|none | 4.28 | 2.09 | 1.99 | +2.19 [-5.08, +9.46] | 10.38 | 135.1 |
| asia | HOLD | HOLDOUT | 3205 | abs120|VW|none | 5.55 | 0.06 | 0.22 | +5.49 [-8.34, +19.32] | 19.75 | 131.4 |
| asia | X | HOLDOUT | 2464 | abs120|VW|none | 0.19 | -0.36 | -0.30 | +0.55 [-7.28, +8.38] | 11.18 | 97.7 |
| london | PRE | IN-SAMPLE | 5732 | abs60|R3|none | 0.17 | -1.52 | -1.41 | +1.69 [-3.30, +6.69] | 7.13 | 127.6 |
| london | HOLD | HOLDOUT | 2411 | abs60|R3|none | 8.45 | 2.99 | 2.28 | +5.46 [-2.50, +13.42] | 11.37 | 136.2 |
| london | X | HOLDOUT | 1716 | abs60|R3|none | 0.77 | 0.90 | 1.49 | -0.13 [-8.14, +7.87] | 11.43 | 95.0 |
| pre | PRE | IN-SAMPLE | 1600 | abs75|R3|none | 5.46 | -2.25 | -2.33 | +7.71 [-2.17, +17.59] | 14.12 | 124.0 |
| pre | HOLD | HOLDOUT | 583 | abs75|R3|none | -2.85 | -5.15 | -3.69 | +2.30 [-16.33, +20.93] | 26.61 | 113.6 |
| pre | X | HOLDOUT | 624 | abs75|R3|none | -15.44 | -2.82 | -2.14 | -12.63 [-22.82, -2.44] | 14.56 | 82.0 |
| nyam | PRE | IN-SAMPLE | 6850 | a5m_2|R3|none | 7.87 | 2.25 | 1.94 | +5.62 [-4.22, +15.47] | 14.06 | 116.5 |
| nyam | HOLD | HOLDOUT | 3207 | a5m_2|R3|none | 0.85 | 0.34 | 0.13 | +0.50 [-7.00, +8.00] | 10.72 | 107.3 |
| nyam | X | HOLDOUT | 2853 | a5m_2|R3|none | 1.46 | 0.38 | 0.23 | +1.07 [-1.80, +3.95] | 4.11 | 76.2 |
| nypm | PRE | IN-SAMPLE | 5074 | abs120|PD|sess | 4.69 | -1.37 | -1.41 | +6.06 [+0.66, +11.46] | 7.71 | 89.0 |
| nypm | HOLD | HOLDOUT | 1964 | abs120|PD|sess | -1.93 | -0.83 | -0.81 | -1.10 [-8.32, +6.11] | 10.31 | 78.1 |
| nypm | X | HOLDOUT | 2010 | abs120|PD|sess | -2.12 | -2.39 | -2.21 | +0.27 [-3.34, +3.88] | 5.16 | 50.9 |
| close | PRE | IN-SAMPLE | 77 | a1m_0.75|R3|60m | 1.97 | -16.57 | -16.95 | +18.55 [+8.80, +28.29] | 13.92 | 50.9 |
| close | HOLD | HOLDOUT | 26 | a1m_0.75|R3|60m | -8.27 | -9.56 | -9.59 | +1.29 [-28.78, +31.36] | 42.96 | 32.3 |
| close | X | HOLDOUT | 46 | a1m_0.75|R3|60m | 0.17 | 9.10 | 6.99 | -8.93 [-25.60, +7.74] | 23.82 | 41.1 |
Full CSV including RP and G bases and all 48 book x session cells: l2vast/ds3/out/abr/oracle_windows.csv. Selection details and RC p per group: DS3_ABR_B_PREHOLD.md and out/abr/oracle_pre.json.

## Per year (pooled; PRE-selected bracket by trade year; in-year best is IN-SAMPLE)
| year | n | window mix | gain vs 60/60 | MDE80 | in-year best (IN-SAMPLE) |
|--|--|--|--|--|--|
| 2023 | 8,609 | X | +0.63 | 6.44 | abs120|NS|none +0.36 |
| 2024 | 15,529 | PRE 14,425 / X 1,104 | +2.34 | 6.90 | abs120|NS|none +4.94 |
| 2025 | 20,678 | PRE 11,597 / HOLD 9,081 | +2.64 | 8.06 | abs120|R1.5|none +2.55 |
| 2026 | 2,315 | HOLD | +1.10 | 25.04 | abs120|R3|120m +8.93 |
Per-book per-year rows: out/abr/oracle_years.csv.

## Target-correction sensitivity (basis G beside M, short targets)
The year target correction (1.4/1.5/4.2/4.3 pts) is charged at every target distance although it was measured at the 60-pt target; it penalises short targets most. Pooled, abs60 stop, no time exit (M includes all costs: slip, correction, 0.242 fee; G is gross at touch, so M-G is not the correction alone):
| target (abs60 stop, no time exit) | window | n | M (measured) | G (gross at touch) | M-G |
|--|--|--|--|--|--|
| R0.5 | PRE | 26022 | -0.92 | 1.48 | -2.41 |
| R0.5 | HOLD | 11396 | -1.33 | 1.99 | -3.32 |
| R0.5 | X | 9713 | -0.19 | 1.19 | -1.38 |
| R0.75 | PRE | 26022 | -0.19 | 2.05 | -2.24 |
| R0.75 | HOLD | 11396 | -0.54 | 2.44 | -2.98 |
| R0.75 | X | 9713 | -0.17 | 1.11 | -1.28 |
| R1 | PRE | 26022 | 0.34 | 2.45 | -2.11 |
| R1 | HOLD | 11396 | 0.32 | 3.03 | -2.71 |
| R1 | X | 9713 | -0.45 | 0.75 | -1.21 |
| R1.25 | PRE | 26022 | 0.55 | 2.58 | -2.02 |
| R1.25 | HOLD | 11396 | 0.39 | 2.86 | -2.47 |
| R1.25 | X | 9713 | -0.53 | 0.62 | -1.14 |
| R1.5 | PRE | 26022 | 0.92 | 2.86 | -1.93 |
| R1.5 | HOLD | 11396 | 0.87 | 3.19 | -2.31 |
| R1.5 | X | 9713 | -0.24 | 0.86 | -1.10 |
| R2 | PRE | 26022 | 1.04 | 2.83 | -1.79 |
| R2 | HOLD | 11396 | 2.03 | 4.08 | -2.04 |
| R2 | X | 9713 | -0.53 | 0.52 | -1.05 |
| R3 | PRE | 26022 | 2.09 | 3.71 | -1.62 |
| R3 | HOLD | 11396 | 4.02 | 5.70 | -1.68 |
| R3 | X | 9713 | -0.10 | 0.88 | -0.98 |
Short targets lose more in M than in G (R0.5: M-G -2.4 PRE / -3.3 HOLD vs R3: -1.6 / -1.7). In G the ordering is flat or slightly rising with target (1.5 to 3.7), in M it is -0.9 to +2.1: the M basis tilts toward far targets, so the oracle's preference for far targets is partly this convention. The pooled G-selected bracket is the same abs120|OR|none (PRE +1.89, HOLD +2.19, X +0.07 over 60/60, MDE 6.3-11), i.e. the conclusion does not depend on the correction. A distance-dependent correction was not measured; replay of short-target limit fills is the open item.

## Stop slippage (measured-walk estimator, calibrated on DN; out/abr/stopfill_by_stop_year.csv)
Mean slip at 10 lots by stop: 0.4 pt (2023) to about 1.0 pt (2025), almost flat in S; at risk-parity lots tight stops cost more (2025: S=20 1.60 pt at 30 lots, S=60 0.95, S=120 0.65 at 5 lots). Calibration vs DN real walk: correlation 0.55, factor 0.68 (1 lot) / 0.83 (10) / 0.84 (14). This is lower than DN's real 1.7 pt in 2025 because bracket stops trigger in ordinary conditions, DN stop-entries on breakouts; it is an estimate from 1-s snapshots, not a replay.

## Deviations and caveats
* WT45 extra row not scored separately (LIVE covers WT's own 45/33.75). CR uses static brackets from its entry; its live column is the stored dynamic exit.
* Structure targets fall back to 2R when no valid level exists (flag in geometry.npz fb).
* Same-row ties: stop before target (library rule). Weekly clustering, 2,000-draw RC, seed 20261029.
* Entries of the 11 books overlap in time (stack), so effective sample size is far below n; MDEs use week clusters.
* Number of groups inspected at HOLD/X: 65 (1+11+6 incl. CLOSE+48 cells) x 3 selection bases.
