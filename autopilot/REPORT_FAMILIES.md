# REPORT FAMILIES - METHOD-2 family scoring (all owners), compiled by a778

**INTERIM (owners are still posting; DONE METHOD-2 is printed only when all owners have posted).** 3,592 well-formed family rows scored (219 rows with a malformed layout skipped: owners to re-post). Config: fit 12 / read 3 / step 3, rule 'tilt', first OOS week 2024-02, gates a-d (OOS Sharpe and net > 0; null rank >= 0.95; 4-week block bootstrap lower bound > 0; both OOS halves net > 0) + executable; multiplicity: best-of-F rank = G(s)^F with G the pooled family-null CDF (170,189 null draws), F nominal = 3,938, F effective = 1208 (a4cf correlation clusters at 0.5, conservative) / 55.6 (participation ratio, optimistic).

**Gate (decision logged before A-D results existed):** best-of-F uses F_eff = 1208 greedy clusters at OOS correlation >= 0.5; the participation-ratio number (55.6) is a SENSITIVITY only, F=30 and nominal F=3,938 are printed for reference. **Counts.** Gates a-d pass (single-family): 88. PASS at the gate F_eff (1208): 0. Sensitivity: PR 55.6: 2; F=30: 5; nominal F: 0. The CONTROL ensembles (ST, HM, WT, pair; a027) are pre-specified live mechanisms chosen in-sample: they are REFERENCES, not search results (they fail the multiplicity at F_eff by construction); the item-8 ensemble is judged by its paired weekly-difference interval against the live pair. Circular-shift nulls are not used (POWER2: invalid for the OOS Sharpe). Library families use 'series-level drift-adjusted signflip' (weaker than the custom drift-matched random-entry null of the engine-built families).

## Passing families (gates a-d), sorted by OOS Sharpe
| family | owner | cells | OOS Sharpe | net (unit) | max DD @6/6 | worst week @6/6 | null kind | null rank | boot lo | half1 / half2 | pair corr | plateau breadth / class | best-of-F gate F_eff | nominal | PR 55.6 (sens.) | F=30 | PASS |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| SK_K4BOOKS | a3a74 | 26 | 2.24 | 73.1 | 210,000 | -190,991 | custom drift-matched LONG-ONLY ran | 1.00 | 0.31 | 1.99 / 3.13 | -0.00 | 1.00 flat (~97%) [26 cells incl. duplicates; see REPORT_K4_M2] | 0.786 | 0.455 | 0.989 | 0.994 | fail multiplicity |
| CTRL_HM | intraday | 229 | 2.18 | 71.4 | 210,000 | -75,235 | signflip (two-sided CONTROL book;  | 1.00 | 0.28 | 1.61 / 2.72 | +0.61 | 1.00 flat | 0.644 | 0.238 | 0.980 | 0.989 | fail multiplicity |
| B7 | a778 | 62 | 1.95 | 29.5 | 210,000 | -76,857 | series-level drift-adjusted signfl | 1.00 | 0.10 | 3.00 / 0.91 | -0.05 | 0.19 peaked | 0.187 | 0.004 | 0.926 | 0.959 | fail multiplicity |
| T3S1_BOOKS_B:B_ST | a778 | 180 | 1.93 | 64.3 | 210,000 | -64,639 | series-level drift-adjusted signfl | 1.00 | 0.24 | 2.24 / 1.63 | +0.66 | 0.44 peaked | 0.166 | 0.003 | 0.921 | 0.956 | fail multiplicity |
| T3S1_BOOKS_B:B_HM | a778 | 80 | 1.92 | 54.8 | 210,000 | -73,435 | series-level drift-adjusted signfl | 1.00 | 0.19 | 1.60 / 2.22 | +0.57 | 0.40 peaked | 0.145 | 0.002 | 0.915 | 0.953 | fail multiplicity |
| T3S1_G_G_v1:G_G4@NQMNQCM#1 | a778 | 400 | 1.86 | 45.7 | 210,000 | -52,618 | series-level drift-adjusted signfl | 1.00 | 0.15 | 1.07 / 2.53 | +0.61 | 0.26 peaked | 0.066 | 0.000 | 0.882 | 0.935 | fail multiplicity |
| T3S1_BOOKS_B:B_WT | a778 | 153 | 1.85 | 56.5 | 210,000 | -64,696 | series-level drift-adjusted signfl | 1.00 | 0.17 | 2.15 / 1.58 | +0.51 | 0.41 peaked | 0.061 | 0.000 | 0.879 | 0.933 | fail multiplicity |
| TINYMERGE:RW:market | a778 | 15 | 1.84 | 55.0 | 210,000 | -187,721 | series-level drift-adjusted signfl | 1.00 | 0.22 | 1.69 / 2.57 | +0.01 | 0.73 intermediate | 0.051 | 0.000 | 0.872 | 0.929 | fail multiplicity |
| N1-EN_HO_RB-5m-MR | a4cf9c23 | 128 | 1.83 | 71.7 | 210,000 | -43,287 | custom drift-matched day-permutati | 0.98 | 0.17 | 2.90 / 1.51 | +0.01 | 0.85 peaked | 0.045 | 0.000 | 0.867 | 0.926 | fail multiplicity |
| CTRL_PAIR | intraday | 247 | 1.83 | 66.0 | 210,000 | -59,691 | signflip (two-sided CONTROL book;  | 1.00 | 0.23 | 1.68 / 1.95 | +0.84 | 1.00 peaked | 0.045 | 0.000 | 0.867 | 0.926 | fail multiplicity |
| SK_K4BOOKS_ESHEDGED | a3a74 | 26 | 1.80 | 52.1 | 210,000 | -159,605 | custom drift-matched LONG-ONLY ran | 1.00 | 0.16 | 1.87 / 1.95 | -0.04 | 1.00 flat (~97%) [26 cells incl. duplicates; see REPORT_K4_M2] | 0.029 | 0.000 | 0.850 | 0.916 | fail multiplicity |
| T3S1_G_G_v1:G_G3@NQMNQCM#2 | a778 | 400 | 1.79 | 41.5 | 210,000 | -75,652 | series-level drift-adjusted signfl | 1.00 | 0.12 | 0.79 / 2.64 | +0.62 | 0.28 peaked | 0.025 | 0.000 | 0.844 | 0.913 | fail multiplicity |
| T3S1_G_G_v1:G_G6@NQMNQCM#1 | a778 | 400 | 1.78 | 39.1 | 210,000 | -53,699 | series-level drift-adjusted signfl | 1.00 | 0.13 | 1.46 / 2.06 | +0.62 | 0.24 intermediate | 0.023 | 0.000 | 0.841 | 0.911 | fail multiplicity |
| T3S1_G_G_v1:G_G3@NQMNQCM#1 | a778 | 400 | 1.77 | 39.4 | 210,000 | -77,935 | series-level drift-adjusted signfl | 0.99 | 0.14 | 1.00 / 2.50 | +0.63 | 0.41 peaked | 0.021 | 0.000 | 0.837 | 0.909 | fail multiplicity |
| BM13_NQ | intraday | 6 | 1.77 | 90.5 | 210,000 | -150,043 | signflip (one random sign per ISO  | 1.00 | 0.31 | 1.89 / 1.64 | -0.02 | 0.50 nan | 0.019 | 0.000 | 0.833 | 0.906 | fail multiplicity |
| T3S1_G_G_v1:G_G4@NQMNQCM#2 | a778 | 265 | 1.74 | 49.8 | 210,000 | -51,916 | series-level drift-adjusted signfl | 1.00 | 0.15 | 1.10 / 2.35 | +0.56 | 0.49 intermediate | 0.011 | 0.000 | 0.813 | 0.895 | fail multiplicity |
| B1 | a778 | 65 | 1.71 | 24.9 | 210,000 | -43,118 | series-level drift-adjusted signfl | 1.00 | 0.07 | 3.89 / 0.07 | +0.15 | 0.28 peaked | 0.006 | 0.000 | 0.790 | 0.881 | fail multiplicity |
| TINYMERGE:G:market | a778 | 12 | 1.70 | 26.3 | 210,000 | -110,811 | none (no factor; plain signflip) | 0.99 | 0.07 | 2.74 / 0.82 | -0.02 | 0.50 peaked | 0.005 | 0.000 | 0.785 | 0.877 | fail multiplicity |
| T3S1_G_G_v1:G_G1@NQMNQCM#1 | a778 | 400 | 1.67 | 33.4 | 210,000 | -86,668 | series-level drift-adjusted signfl | 1.00 | 0.10 | 1.13 / 2.10 | +0.56 | 0.26 peaked | 0.002 | 0.000 | 0.754 | 0.859 | fail multiplicity |
| C10S1_CL:240_lr | a778 | 20 | 1.66 | 82.3 | 210,000 | -130,117 | series-level drift-adjusted signfl | 1.00 | 0.17 | 0.97 / 2.09 | +0.06 | 0.60 peaked | 0.002 | 0.000 | 0.751 | 0.857 | fail multiplicity |
| CTRL_ST | intraday | 229 | 1.65 | 56.0 | 210,000 | -63,894 | signflip (two-sided CONTROL book;  | 1.00 | 0.16 | 1.52 / 1.75 | +0.71 | 1.00 peaked | 0.001 | 0.000 | 0.740 | 0.850 | fail multiplicity |
| T3S1_G_G_v1:G_G2@NQMNQCM#1 | a778 | 400 | 1.57 | 32.0 | 210,000 | -69,430 | series-level drift-adjusted signfl | 0.98 | 0.08 | 1.40 / 1.71 | +0.54 | 0.20 peaked | 0.000 | 0.000 | 0.673 | 0.808 | fail multiplicity |
| T3S1_G_G_v1:G_G5@NQMNQCM#1 | a778 | 400 | 1.57 | 36.4 | 210,000 | -68,114 | series-level drift-adjusted signfl | 0.98 | 0.10 | 1.08 / 2.06 | +0.50 | 0.20 intermediate | 0.000 | 0.000 | 0.671 | 0.806 | fail multiplicity |
| N7-RSI-ES | a3a74 | 45 | 1.52 | 53.1 | 210,000 | -100,095 | custom run-structure-matched rando | 0.99 | 0.16 | 1.61 / 1.78 | +0.07 | 0.98 flat (~97%) | 0.000 | 0.000 | 0.628 | 0.778 | fail multiplicity |
| N16-F1-RTY | n9 | 68 | 1.49 | 34.3 | 210,000 | -57,142 | signflip (1000 reps; one random si | 0.99 | 0.08 | 1.97 / 0.91 | -0.01 | 0.43 nan | 0.000 | 0.000 | 0.591 | 0.753 | fail multiplicity |
| BM11_NQ | intraday | 8 | 1.46 | 62.6 | 210,000 | -122,126 | signflip (one random sign per ISO  | 0.99 | 0.13 | 1.92 / 0.94 | -0.03 | 0.75 peaked (~80%) | 0.000 | 0.000 | 0.556 | 0.728 | fail multiplicity |
| T3S1_G_G_v1:G_G1@NQMNQCM#3 | a778 | 400 | 1.46 | 29.4 | 210,000 | -57,370 | series-level drift-adjusted signfl | 0.98 | 0.07 | 0.43 / 2.39 | +0.58 | 0.27 peaked | 0.000 | 0.000 | 0.548 | 0.723 | fail multiplicity |
| B7XC | a778 | 52 | 1.44 | 25.4 | 210,000 | -83,050 | series-level drift-adjusted signfl | 0.99 | 0.05 | 2.12 / 0.82 | -0.00 | 0.12 peaked | 0.000 | 0.000 | 0.532 | 0.712 | fail multiplicity |
| T3S1_G_G_v1:G_G1@NQMNQCM#4 | a778 | 400 | 1.44 | 35.7 | 210,000 | -52,536 | series-level drift-adjusted signfl | 0.99 | 0.09 | 0.71 / 2.12 | +0.61 | 0.25 peaked | 0.000 | 0.000 | 0.530 | 0.710 | fail multiplicity |
| C11DIP | a778 | 64 | 1.43 | 48.8 | 210,000 | -94,995 | series-level drift-adjusted signfl | 1.00 | 0.10 | 0.81 / 2.23 | +0.03 | 0.61 peaked | 0.000 | 0.000 | 0.528 | 0.708 | fail multiplicity |
| TINYMERGE:I:market | a778 | 14 | 1.39 | 40.6 | 210,000 | -99,120 | series-level drift-adjusted signfl | 0.99 | 0.09 | 1.57 / 1.22 | +0.09 | 0.14 flat | 0.000 | 0.000 | 0.467 | 0.663 | fail multiplicity |
| C10S1_CL:240_macd | a778 | 20 | 1.38 | 52.1 | 210,000 | -154,683 | series-level drift-adjusted signfl | 0.99 | 0.12 | 1.23 / 1.49 | +0.05 | 0.60 peaked | 0.000 | 0.000 | 0.462 | 0.660 | fail multiplicity |
| SK_K4_PAIRVAR | a3a74 | 10 | 1.37 | 42.6 | 228,911 | -95,141 | weekly-block sign-flip on the delt | 0.99 | 0.08 | 1.16 / 1.56 | -0.01 | nan nan | 0.000 | 0.000 | 0.449 | 0.649 | fail multiplicity |
| N2-ISM_S-RANGE-MET | a027 | 108 | 1.35 | 46.5 | 210,000 | -105,059 | signflip (1000 reps; one random si | 0.99 | 0.10 | 1.64 / 1.04 | -0.01 | 0.44 nan | 0.000 | 0.000 | 0.413 | 0.621 | fail multiplicity |
| N7-RSI-ES-K1 | a3a74 | 190 | 1.34 | 43.9 | 210,000 | -126,342 | custom run-structure-matched rando | 0.99 | 0.12 | 1.36 / 1.94 | +0.07 | 0.98 flat (~97%) | 0.000 | 0.000 | 0.411 | 0.619 | fail multiplicity |
| N3-ROLL-6J-K1 | a3a74 | 128 | 1.34 | 51.2 | 210,000 | -106,155 | custom run-structure-matched rando | 0.97 | 0.11 | 1.74 / 0.97 | +0.22 | 0.49 peaked (~80%) | 0.000 | 0.000 | 0.409 | 0.617 | fail multiplicity |
| T3S1_G_G_v1:G_G1@NQMNQCM#2 | a778 | 400 | 1.34 | 29.4 | 210,000 | -57,219 | series-level drift-adjusted signfl | 0.98 | 0.06 | 0.41 / 2.18 | +0.58 | 0.26 peaked | 0.000 | 0.000 | 0.406 | 0.615 | fail multiplicity |
| BM8_RTY | intraday | 12 | 1.32 | 43.0 | 210,000 | -113,600 | signflip (one random sign per ISO  | 0.99 | 0.11 | 1.90 / 0.51 | -0.08 | 0.50 peaked (~80%) | 0.000 | 0.000 | 0.386 | 0.598 | fail multiplicity |
| N10-CSMAX-MENR | n9 | 24 | 1.31 | 44.3 | 210,000 | -77,177 | signflip (1000 reps; one random si | 0.99 | 0.07 | 1.21 / 1.38 | -0.03 | 0.50 nan | 0.000 | 0.000 | 0.372 | 0.587 | fail multiplicity |
| T3S1_G_G_v1:G_G6@NQMNQCM#2 | a778 | 127 | 1.31 | 32.1 | 210,000 | -60,155 | series-level drift-adjusted signfl | 0.97 | 0.06 | 0.71 / 1.82 | +0.55 | 0.23 intermediate | 0.000 | 0.000 | 0.370 | 0.585 | fail multiplicity |
| N4-NR7-ENR-c570 | a027 | 168 | 1.31 | 18.0 | 210,000 | -57,761 | signflip (1000 reps; one random si | 0.98 | 0.03 | 0.01 / 2.23 | -0.01 | 0.36 nan | 0.000 | 0.000 | 0.368 | 0.583 | fail multiplicity |
| M2-B-A9-ffw-Renko | a4cf9c23 | 100 | 1.31 | 28.9 | nan | nan | custom drift-matched random-entry  | 1.00 | 0.08 | 2.26 / 0.68 | -0.01 | 0.36 peaked | 0.000 | 0.000 | 0.363 | 0.579 | fail multiplicity |
| T3S1_G_G_v1:G_G1@NQMNQCM#6 | a778 | 166 | 1.30 | 33.4 | 210,000 | -47,545 | series-level drift-adjusted signfl | 0.98 | 0.07 | 0.57 / 2.01 | +0.59 | 0.31 peaked | 0.000 | 0.000 | 0.360 | 0.576 | fail multiplicity |
| TINYMERGE:L:market | a778 | 19 | 1.30 | 22.7 | 210,000 | -39,308 | series-level drift-adjusted signfl | 1.00 | 0.04 | 1.47 / 1.17 | +0.04 | 0.11 peaked | 0.000 | 0.000 | 0.359 | 0.576 | fail multiplicity |
| N8-DISP-6B | a3a74 | 72 | 1.30 | 25.8 | 210,000 | -95,268 | custom run-structure-matched rando | 1.00 | 0.04 | 1.33 / 1.30 | +0.13 | 0.43 peaked (~80%) | 0.000 | 0.000 | 0.354 | 0.571 | fail multiplicity |
| BM12_NQ | intraday | 12 | 1.28 | 45.7 | 210,000 | -107,798 | signflip (one random sign per ISO  | 0.98 | 0.08 | 1.29 / 1.34 | +0.01 | 0.67 flat (~97%) | 0.000 | 0.000 | 0.333 | 0.552 | fail multiplicity |
| N3-ROLL-ZB | a3a74 | 72 | 1.27 | 48.4 | 210,000 | -164,573 | custom run-structure-matched rando | 1.00 | 0.11 | 1.50 / 1.02 | +0.04 | 0.50 peaked (~80%) | 0.000 | 0.000 | 0.315 | 0.536 | fail multiplicity |
| WT432:ATR30_m4 | a778 | 36 | 1.26 | 32.8 | 210,000 | -61,709 | series-level drift-adjusted signfl | 0.99 | 0.05 | 1.28 / 1.23 | +0.35 | 0.11 peaked | 0.000 | 0.000 | 0.295 | 0.518 | fail multiplicity |
| T3S1_G_G_v1:G_G3@NQMNQCM#3 | a778 | 253 | 1.24 | 31.8 | 210,000 | -63,379 | series-level drift-adjusted signfl | 0.98 | 0.04 | 0.57 / 1.92 | +0.57 | 0.40 peaked | 0.000 | 0.000 | 0.278 | 0.501 | fail multiplicity |
| Q37_RTY | intraday | 8 | 1.24 | 47.9 | 210,000 | -46,797 | signflip (one random sign per ISO  | 0.97 | 0.01 | 0.28 / 2.08 | +0.16 | 0.50 flat (~97%) | 0.000 | 0.000 | 0.273 | 0.496 | fail multiplicity |
| B1leg_BTC | a778 | 180 | 1.22 | 24.1 | 210,000 | -74,906 | series-level drift-adjusted signfl | 0.95 | 0.04 | 1.55 / 0.93 | +0.00 | 0.18 peaked | 0.000 | 0.000 | 0.247 | 0.470 | fail multiplicity |
| N11-FIRSTBAR-MET | n9 | 180 | 1.21 | 45.3 | 210,000 | -105,174 | signflip (1000 reps; one random si | 0.98 | 0.09 | 2.17 / 0.78 | +0.01 | 0.37 nan | 0.000 | 0.000 | 0.237 | 0.459 | fail multiplicity |
| TINYMERGE:V:market | a778 | 40 | 1.20 | 35.3 | 210,000 | -63,964 | series-level drift-adjusted signfl | 0.99 | 0.07 | 1.57 / 0.75 | +0.02 | 0.47 peaked | 0.000 | 0.000 | 0.223 | 0.445 | fail multiplicity |
| WT432:ATR20_m4 | a778 | 36 | 1.19 | 30.1 | 210,000 | -57,455 | series-level drift-adjusted signfl | 0.97 | 0.02 | 1.27 / 1.10 | +0.36 | 0.17 peaked | 0.000 | 0.000 | 0.216 | 0.438 | fail multiplicity |
| M2-B-A9-ffw-Range | a4cf9c23 | 100 | 1.17 | 25.8 | nan | nan | custom drift-matched random-entry  | 1.00 | 0.03 | 2.51 / 0.55 | +0.01 | 0.00 peaked | 0.000 | 0.000 | 0.184 | 0.401 | fail multiplicity |
| T3S1_G_G_v1:G_G1@NQMNQCM#5 | a778 | 400 | 1.17 | 25.5 | 210,000 | -47,326 | series-level drift-adjusted signfl | 0.97 | 0.03 | 0.66 / 1.64 | +0.61 | 0.18 peaked | 0.000 | 0.000 | 0.183 | 0.400 | fail multiplicity |
| N7-RSI-HE-K1 | a3a74 | 186 | 1.16 | 28.6 | 210,000 | -86,218 | custom run-structure-matched rando | 1.00 | 0.06 | 1.92 / 0.48 | -0.14 | 0.96 flat (~97%) | 0.000 | 0.000 | 0.177 | 0.393 | fail multiplicity |
| MG_ENTRY | ap_m2c | 18 | 1.16 | 3.1 | 210,000 | -49,467 | signflip (one random sign per ISO  | 0.98 | 0.02 | 0.98 / 1.33 | +0.14 | 0.28 peaked (~80%) | 0.000 | 0.000 | 0.176 | 0.392 | fail multiplicity |
| N3-ROLL-ZN | a3a74 | 72 | 1.16 | 45.5 | 210,000 | -90,977 | custom run-structure-matched rando | 1.00 | 0.06 | 1.60 / 0.68 | +0.00 | 0.50 peaked (~80%) | 0.000 | 0.000 | 0.174 | 0.389 | fail multiplicity |
| N10-CSMAX-COMM | n9 | 72 | 1.16 | 39.0 | 210,000 | -80,512 | signflip (1000 reps; one random si | 0.98 | 0.05 | 1.25 / 1.06 | +0.00 | 0.50 nan | 0.000 | 0.000 | 0.171 | 0.386 | fail multiplicity |
| N13-XLEAD-HO | n9 | 274 | 1.14 | 15.0 | 210,000 | -62,731 | signflip (1000 reps; one random si | 0.98 | 0.01 | 0.95 / 1.27 | +0.02 | 0.45 nan | 0.000 | 0.000 | 0.155 | 0.366 | fail multiplicity |
| N8-RISK-6A-K1 | a3a74 | 256 | 1.14 | 17.8 | 210,000 | -130,729 | custom run-structure-matched rando | 1.00 | 0.03 | 1.14 / 1.18 | +0.03 | 0.48 peaked (~80%) | 0.000 | 0.000 | 0.150 | 0.360 | fail multiplicity |
| N3-ROLL-ZF | a3a74 | 72 | 1.13 | 49.0 | 210,000 | -114,781 | custom run-structure-matched rando | 0.99 | 0.05 | 1.74 / 0.44 | -0.01 | 0.50 peaked (~80%) | 0.000 | 0.000 | 0.147 | 0.355 | fail multiplicity |
| BI8_YM | intraday | 12 | 1.10 | 52.8 | 210,000 | -91,214 | signflip (one random sign per ISO  | 1.00 | 0.01 | 1.42 / 0.72 | +0.06 | 0.58 peaked (~80%) | 0.000 | 0.000 | 0.114 | 0.310 | fail multiplicity |
| N10-CSVOL-MENR | n9 | 36 | 1.09 | 45.3 | 210,000 | -77,157 | signflip (1000 reps; one random si | 0.96 | 0.03 | 1.56 / 0.79 | +0.08 | 0.50 nan | 0.000 | 0.000 | 0.112 | 0.307 | fail multiplicity |
| N3-ROLL-ZB-K1 | a3a74 | 128 | 1.09 | 42.5 | 210,000 | -98,630 | custom run-structure-matched rando | 0.98 | 0.09 | 1.41 / 0.75 | +0.03 | 0.50 peaked (~80%) | 0.000 | 0.000 | 0.106 | 0.298 | fail multiplicity |
| N7-MRZ-HG | a3a74 | 140 | 1.07 | 30.3 | 210,000 | -90,877 | custom run-structure-matched rando | 0.99 | 0.04 | 0.43 / 1.87 | +0.16 | 0.92 flat (~97%) | 0.000 | 0.000 | 0.093 | 0.278 | fail multiplicity |
| N3-CARRY-ES | a3a74 | 80 | 1.07 | 29.1 | 210,000 | -59,217 | custom run-structure-matched rando | 0.96 | 0.04 | 0.24 / 1.78 | -0.01 | 0.54 peaked (~80%) | 0.000 | 0.000 | 0.089 | 0.272 | fail multiplicity |
| N7-MRZ-HG-K1 | a3a74 | 296 | 1.05 | 31.9 | 210,000 | -102,512 | custom run-structure-matched rando | 0.98 | 0.04 | 0.53 / 1.84 | +0.15 | 0.90 flat (~97%) | 0.000 | 0.000 | 0.081 | 0.258 | fail multiplicity |
| SW20_RTY | a3a74 | 48 | 1.04 | 35.6 | 210,000 | -100,324 | custom drift-matched random-entry  | 0.98 | 0.05 | 1.45 / 0.62 | +0.06 | 0.39 peaked (~80% class) | 0.000 | 0.000 | 0.073 | 0.244 | fail multiplicity |
| PX1_VR60MC | ap_m2c | 6 | 1.04 | 33.2 | 210,000 | -113,611 | signflip (one random sign per ISO  | 0.97 | 0.02 | 1.08 / 1.00 | +0.02 | 0.83 peaked (~80%) | 0.000 | 0.000 | 0.072 | 0.241 | fail multiplicity |
| N3-ROLL-ZN-K1 | a3a74 | 128 | 1.04 | 41.7 | 210,000 | -120,268 | custom run-structure-matched rando | 0.99 | 0.05 | 1.63 / 0.44 | -0.00 | 0.50 peaked (~80%) | 0.000 | 0.000 | 0.070 | 0.237 | fail multiplicity |
| C10S1_6E:240_macd | a778 | 20 | 1.03 | 32.0 | 210,000 | -141,937 | series-level drift-adjusted signfl | 0.95 | 0.03 | 1.05 / 1.02 | -0.01 | 0.20 peaked | 0.000 | 0.000 | 0.068 | 0.235 | fail multiplicity |
| N3-ROLL-ZF-K1 | a3a74 | 128 | 1.03 | 41.4 | 210,000 | -102,716 | custom run-structure-matched rando | 0.98 | 0.03 | 1.77 / 0.29 | -0.02 | 0.50 peaked (~80%) | 0.000 | 0.000 | 0.064 | 0.228 | fail multiplicity |
| N3-ROLL-6J | a3a74 | 72 | 1.02 | 31.2 | 210,000 | -114,948 | custom run-structure-matched rando | 0.96 | 0.03 | 1.38 / 0.65 | +0.21 | 0.50 peaked (~80%) | 0.000 | 0.000 | 0.061 | 0.221 | fail multiplicity |
| WT432:ATR10_m3 | a778 | 36 | 1.00 | 21.1 | 210,000 | -71,247 | series-level drift-adjusted signfl | 0.96 | 0.00 | 0.69 / 1.32 | +0.37 | 0.42 peaked | 0.000 | 0.000 | 0.051 | 0.202 | fail multiplicity |
| N7-MRZ-YM | a3a74 | 143 | 1.00 | 31.5 | 210,000 | -155,307 | custom run-structure-matched rando | 0.98 | 0.05 | 0.68 / 2.12 | +0.06 | 0.94 flat (~97%) | 0.000 | 0.000 | 0.049 | 0.197 | fail multiplicity |
| N3-CARRY-ES-K1 | a3a74 | 38 | 1.00 | 37.7 | 210,000 | -78,622 | custom run-structure-matched rando | 0.95 | 0.01 | 0.39 / 1.56 | +0.01 | 0.74 flat (~97%) | 0.000 | 0.000 | 0.049 | 0.197 | fail multiplicity |
| T3S1_G_G_v1:G_G5@NQMNQCM#2 | a778 | 57 | 0.99 | 32.3 | 210,000 | -55,612 | series-level drift-adjusted signfl | 0.97 | 0.01 | 0.47 / 1.50 | +0.54 | 0.42 flat | 0.000 | 0.000 | 0.047 | 0.192 | fail multiplicity |
| N13-CSMOM-COMMXX | n9 | 84 | 0.99 | 19.2 | 210,000 | -89,287 | signflip (1000 reps; one random si | 0.96 | 0.02 | 0.55 / 1.30 | -0.07 | 0.48 nan | 0.000 | 0.000 | 0.046 | 0.189 | fail multiplicity |
| SW10_NQ | a3a74 | 216 | 0.99 | 25.1 | 210,000 | -69,878 | custom drift-matched random-entry  | 0.99 | 0.02 | 1.64 / 0.06 | +0.24 | 0.44 peaked (~80% class) | 0.000 | 0.000 | 0.043 | 0.184 | fail multiplicity |
| N7-MRZ-YM-K1 | a3a74 | 298 | 0.98 | 30.6 | 210,000 | -149,535 | custom run-structure-matched rando | 1.00 | 0.05 | 0.67 / 1.98 | +0.04 | 0.96 flat (~97%) | 0.000 | 0.000 | 0.042 | 0.180 | fail multiplicity |
| N7-RSI-HE | a3a74 | 45 | 0.97 | 25.4 | 210,000 | -107,442 | custom run-structure-matched rando | 1.00 | 0.04 | 1.69 / 0.35 | -0.17 | 0.98 peaked (~80%) | 0.000 | 0.000 | 0.037 | 0.168 | fail multiplicity |
| M2-B-A4-ffw-Tother | a4cf9c23 | 100 | 0.97 | 16.7 | nan | nan | custom drift-matched random-entry  | 1.00 | 0.01 | 0.08 / 1.90 | +0.04 | -0.37 peaked | 0.000 | 0.000 | 0.036 | 0.166 | fail multiplicity |
| M2-A-A9-nro-V1 | a4cf9c23 | 119 | 0.96 | 25.4 | nan | nan | custom drift-matched random-entry  | 1.00 | 0.00 | 1.13 / 0.88 | +0.06 | 0.44 peaked | 0.000 | 0.000 | 0.034 | 0.162 | fail multiplicity |
| N8-CORR-6B | a3a74 | 108 | 0.95 | 21.0 | 210,000 | -63,165 | custom run-structure-matched rando | 0.99 | 0.00 | 1.41 / 0.56 | +0.08 | 0.49 peaked (~80%) | 0.000 | 0.000 | 0.030 | 0.151 | fail multiplicity |
| N8-RISK-6A | a3a74 | 288 | 0.85 | 18.3 | 210,000 | -131,670 | custom run-structure-matched rando | 1.00 | 0.01 | 0.62 / 1.37 | -0.09 | 0.49 peaked (~80%) | 0.000 | 0.000 | 0.008 | 0.073 | fail multiplicity |
| M2R3-RENKO-ES | a4cf9c23 | 100 | 0.78 | 127.0 | nan | nan | custom drift-matched random-entry  | 0.97 | 0.08 | 0.92 / 1.42 | -0.17 | -0.20 peaked | 0.000 | 0.000 | 0.003 | 0.041 | fail multiplicity |

## FACTOR section: passing families clustered at OOS weekly correlation >= 0.5 (one bet counted once)
34 factors (greedy clusters at OOS correlation >= 0.5) from 78 gate-passing families with an OOS series. INDEPENDENT bets represented by the passing families: 34 by clustering, 12.1 by the participation ratio of their OOS correlation matrix.

| factor leader | members (n) | leader OOS Sharpe | pair corr | members (first 8) |
|---|---|---|---|---|
| SK_K4BOOKS | 5 | 2.24 | -0.00 | SK_K4BOOKS, TINYMERGE:RW:market, SK_K4BOOKS_ESHEDGED, N7-RSI-ES, N7-RSI-ES-K1 |
| CTRL_HM | 21 | 2.18 | +0.61 | CTRL_HM, T3S1_BOOKS_B:B_ST, T3S1_BOOKS_B:B_HM, T3S1_G_G_v1:G_G4@NQMNQCM#1, CTRL_PAIR, T3S1_G_G_v1:G_G3@NQMNQCM#2, T3S1_G_G_v1:G_G6@NQMNQCM#1, T3S1_G_G_v1:G_G3@NQMNQCM#1 |
| B7 | 2 | 1.95 | -0.05 | B7, B7XC |
| T3S1_BOOKS_B:B_WT | 1 | 1.85 | +0.51 | T3S1_BOOKS_B:B_WT |
| N1-EN_HO_RB-5m-MR | 1 | 1.83 | +0.01 | N1-EN_HO_RB-5m-MR |
| BM13_NQ | 3 | 1.77 | -0.02 | BM13_NQ, BM11_NQ, BM12_NQ |
| B1 | 2 | 1.71 | +0.15 | B1, B1leg_BTC |
| TINYMERGE:G:market | 1 | 1.70 | -0.02 | TINYMERGE:G:market |
| C10S1_CL:240_lr | 1 | 1.66 | +0.06 | C10S1_CL:240_lr |
| C11DIP | 1 | 1.43 | +0.03 | C11DIP |
| TINYMERGE:I:market | 1 | 1.39 | +0.09 | TINYMERGE:I:market |
| C10S1_CL:240_macd | 1 | 1.38 | +0.05 | C10S1_CL:240_macd |
| N2-ISM_S-RANGE-MET | 1 | 1.35 | -0.01 | N2-ISM_S-RANGE-MET |
| N3-ROLL-6J-K1 | 2 | 1.34 | +0.22 | N3-ROLL-6J-K1, N3-ROLL-6J |
| BM8_RTY | 1 | 1.32 | -0.08 | BM8_RTY |
| N4-NR7-ENR-c570 | 1 | 1.31 | -0.01 | N4-NR7-ENR-c570 |
| M2-B-A9-ffw-Renko | 2 | 1.31 | -0.01 | M2-B-A9-ffw-Renko, M2-B-A9-ffw-Range |
| TINYMERGE:L:market | 1 | 1.30 | +0.04 | TINYMERGE:L:market |
| N8-DISP-6B | 2 | 1.30 | +0.13 | N8-DISP-6B, N8-CORR-6B |
| N3-ROLL-ZB | 6 | 1.27 | +0.04 | N3-ROLL-ZB, N3-ROLL-ZN, N3-ROLL-ZF, N3-ROLL-ZB-K1, N3-ROLL-ZN-K1, N3-ROLL-ZF-K1 |
| WT432:ATR30_m4 | 3 | 1.26 | +0.35 | WT432:ATR30_m4, WT432:ATR20_m4, WT432:ATR10_m3 |
| Q37_RTY | 1 | 1.24 | +0.16 | Q37_RTY |
| TINYMERGE:V:market | 2 | 1.20 | +0.02 | TINYMERGE:V:market, BI8_YM |
| N7-RSI-HE-K1 | 2 | 1.16 | -0.14 | N7-RSI-HE-K1, N7-RSI-HE |
| N8-RISK-6A-K1 | 2 | 1.14 | +0.03 | N8-RISK-6A-K1, N8-RISK-6A |
| N7-MRZ-HG | 2 | 1.07 | +0.16 | N7-MRZ-HG, N7-MRZ-HG-K1 |
| N3-CARRY-ES | 2 | 1.07 | -0.01 | N3-CARRY-ES, N3-CARRY-ES-K1 |
| SW20_RTY | 1 | 1.04 | +0.06 | SW20_RTY |
| C10S1_6E:240_macd | 1 | 1.03 | -0.01 | C10S1_6E:240_macd |
| N7-MRZ-YM | 2 | 1.00 | +0.06 | N7-MRZ-YM, N7-MRZ-YM-K1 |
| SW10_NQ | 1 | 0.99 | +0.24 | SW10_NQ |
| M2-B-A4-ffw-Tother | 1 | 0.97 | +0.04 | M2-B-A4-ffw-Tother |
| M2-A-A9-nro-V1 | 1 | 0.96 | +0.06 | M2-A-A9-nro-V1 |
| M2R3-RENKO-ES | 1 | 0.78 | -0.17 | M2R3-RENKO-ES |

## All families (top 60 by OOS Sharpe; the full table is outputs/methods2/FAMILY_RESULTS.csv)
| family | owner | cells | OOS Sharpe | null rank | boot lo | a b c d | best-of-F gate | nominal | PR | F=30 | pair corr |
|---|---|---|---|---|---|---|---|---|---|---|---|
| SK_K4BOOKS | a3a74 | 26 | 2.24 | 1.00 | 0.31 | 1111 | 0.786 | 0.455 | 0.989 | 0.994 | -0.00 |
| CTRL_HM | intraday | 229 | 2.18 | 1.00 | 0.28 | 1111 | 0.644 | 0.238 | 0.980 | 0.989 | +0.61 |
| B7 | a778 | 62 | 1.95 | 1.00 | 0.10 | 1111 | 0.187 | 0.004 | 0.926 | 0.959 | -0.05 |
| T3S1_BOOKS_B:B_ST | a778 | 180 | 1.93 | 1.00 | 0.24 | 1111 | 0.166 | 0.003 | 0.921 | 0.956 | +0.66 |
| T3S1_BOOKS_B:B_HM | a778 | 80 | 1.92 | 1.00 | 0.19 | 1111 | 0.145 | 0.002 | 0.915 | 0.953 | +0.57 |
| T3S1_G_G_v1:G_G4@NQMNQCM#1 | a778 | 400 | 1.86 | 1.00 | 0.15 | 1111 | 0.066 | 0.000 | 0.882 | 0.935 | +0.61 |
| T3S1_BOOKS_B:B_WT | a778 | 153 | 1.85 | 1.00 | 0.17 | 1111 | 0.061 | 0.000 | 0.879 | 0.933 | +0.51 |
| TINYMERGE:RW:market | a778 | 15 | 1.84 | 1.00 | 0.22 | 1111 | 0.051 | 0.000 | 0.872 | 0.929 | +0.01 |
| N1-EN_HO_RB-5m-MR | a4cf9c23 | 128 | 1.83 | 0.98 | 0.17 | 1111 | 0.045 | 0.000 | 0.867 | 0.926 | +0.01 |
| CTRL_PAIR | intraday | 247 | 1.83 | 1.00 | 0.23 | 1111 | 0.045 | 0.000 | 0.867 | 0.926 | +0.84 |
| SK_K4BOOKS_ESHEDGED | a3a74 | 26 | 1.80 | 1.00 | 0.16 | 1111 | 0.029 | 0.000 | 0.850 | 0.916 | -0.04 |
| T3S1_G_G_v1:G_G3@NQMNQCM#2 | a778 | 400 | 1.79 | 1.00 | 0.12 | 1111 | 0.025 | 0.000 | 0.844 | 0.913 | +0.62 |
| T3S1_G_G_v1:G_G6@NQMNQCM#1 | a778 | 400 | 1.78 | 1.00 | 0.13 | 1111 | 0.023 | 0.000 | 0.841 | 0.911 | +0.62 |
| T3S1_G_G_v1:G_G3@NQMNQCM#1 | a778 | 400 | 1.77 | 0.99 | 0.14 | 1111 | 0.021 | 0.000 | 0.837 | 0.909 | +0.63 |
| BM13_NQ | intraday | 6 | 1.77 | 1.00 | 0.31 | 1111 | 0.019 | 0.000 | 0.833 | 0.906 | -0.02 |
| T3S1_G_G_v1:G_G4@NQMNQCM#2 | a778 | 265 | 1.74 | 1.00 | 0.15 | 1111 | 0.011 | 0.000 | 0.813 | 0.895 | +0.56 |
| B1 | a778 | 65 | 1.71 | 1.00 | 0.07 | 1111 | 0.006 | 0.000 | 0.790 | 0.881 | +0.15 |
| TINYMERGE:G:market | a778 | 12 | 1.70 | 0.99 | 0.07 | 1111 | 0.005 | 0.000 | 0.785 | 0.877 | -0.02 |
| T3S1_G_G_v1:G_G1@NQMNQCM#1 | a778 | 400 | 1.67 | 1.00 | 0.10 | 1111 | 0.002 | 0.000 | 0.754 | 0.859 | +0.56 |
| N3-SPREAD-SI | a3a74 | 106 | 1.67 | 0.00 | 0.04 | 1010 | 0.002 | 0.000 | 0.753 | 0.858 | +0.07 |
| C10S1_CL:240_lr | a778 | 20 | 1.66 | 1.00 | 0.17 | 1111 | 0.002 | 0.000 | 0.751 | 0.857 | +0.06 |
| CTRL_ST | intraday | 229 | 1.65 | 1.00 | 0.16 | 1111 | 0.001 | 0.000 | 0.740 | 0.850 | +0.71 |
| N3-CARRY-GC | a3a74 | 102 | 1.61 | 0.88 | 0.12 | 1011 | 0.001 | 0.000 | 0.714 | 0.834 | +0.07 |
| N7-TREND-GC | a3a74 | 108 | 1.60 | 0.14 | 0.16 | 1011 | 0.000 | 0.000 | 0.700 | 0.825 | -0.02 |
| T3S1_G_G_v1:G_G2@NQMNQCM#1 | a778 | 400 | 1.57 | 0.98 | 0.08 | 1111 | 0.000 | 0.000 | 0.673 | 0.808 | +0.54 |
| T3S1_G_G_v1:G_G5@NQMNQCM#1 | a778 | 400 | 1.57 | 0.98 | 0.10 | 1111 | 0.000 | 0.000 | 0.671 | 0.806 | +0.50 |
| N17-G3-HO | n9 | 56 | 1.56 | 0.00 | nan | 1000 | 0.000 | 0.000 | 0.661 | 0.800 | +0.19 |
| N7-RSI-ES | a3a74 | 45 | 1.52 | 0.99 | 0.16 | 1111 | 0.000 | 0.000 | 0.628 | 0.778 | +0.07 |
| N16-F1-RTY | n9 | 68 | 1.49 | 0.99 | 0.08 | 1111 | 0.000 | 0.000 | 0.591 | 0.753 | -0.01 |
| BM11_NQ | intraday | 8 | 1.46 | 0.99 | 0.13 | 1111 | 0.000 | 0.000 | 0.556 | 0.728 | -0.03 |
| T3S1_G_G_v1:G_G1@NQMNQCM#3 | a778 | 400 | 1.46 | 0.98 | 0.07 | 1111 | 0.000 | 0.000 | 0.548 | 0.723 | +0.58 |
| SW35_GC | a3a74 | 18 | 1.46 | 0.36 | 0.13 | 1011 | 0.000 | 0.000 | 0.546 | 0.721 | -0.02 |
| B7XC | a778 | 52 | 1.44 | 0.99 | 0.05 | 1111 | 0.000 | 0.000 | 0.532 | 0.712 | -0.00 |
| T3S1_G_G_v1:G_G1@NQMNQCM#4 | a778 | 400 | 1.44 | 0.99 | 0.09 | 1111 | 0.000 | 0.000 | 0.530 | 0.710 | +0.61 |
| C11DIP | a778 | 64 | 1.43 | 1.00 | 0.10 | 1111 | 0.000 | 0.000 | 0.528 | 0.708 | +0.03 |
| B11 | a778 | 60 | 1.42 | 0.99 | 0.06 | 1110 | 0.000 | 0.000 | 0.506 | 0.693 | +0.06 |
| TINYMERGE:I:market | a778 | 14 | 1.39 | 0.99 | 0.09 | 1111 | 0.000 | 0.000 | 0.467 | 0.663 | +0.09 |
| C10S1_CL:240_macd | a778 | 20 | 1.38 | 0.99 | 0.12 | 1111 | 0.000 | 0.000 | 0.462 | 0.660 | +0.05 |
| SK_K4_PAIRVAR | a3a74 | 10 | 1.37 | 0.99 | 0.08 | 1111 | 0.000 | 0.000 | 0.449 | 0.649 | -0.01 |
| N2-ISM_S-RANGE-MET | a027 | 108 | 1.35 | 0.99 | 0.10 | 1111 | 0.000 | 0.000 | 0.413 | 0.621 | -0.01 |
| N7-RSI-ES-K1 | a3a74 | 190 | 1.34 | 0.99 | 0.12 | 1111 | 0.000 | 0.000 | 0.411 | 0.619 | +0.07 |
| N3-ROLL-6J-K1 | a3a74 | 128 | 1.34 | 0.97 | 0.11 | 1111 | 0.000 | 0.000 | 0.409 | 0.617 | +0.22 |
| T3S1_G_G_v1:G_G1@NQMNQCM#2 | a778 | 400 | 1.34 | 0.98 | 0.06 | 1111 | 0.000 | 0.000 | 0.406 | 0.615 | +0.58 |
| BM8_RTY | intraday | 12 | 1.32 | 0.99 | 0.11 | 1111 | 0.000 | 0.000 | 0.386 | 0.598 | -0.08 |
| N7-BRK-GC | a3a74 | 60 | 1.32 | 0.01 | 0.09 | 1011 | 0.000 | 0.000 | 0.373 | 0.588 | +0.00 |
| N10-CSMAX-MENR | n9 | 24 | 1.31 | 0.99 | 0.07 | 1111 | 0.000 | 0.000 | 0.372 | 0.587 | -0.03 |
| T3S1_G_G_v1:G_G6@NQMNQCM#2 | a778 | 127 | 1.31 | 0.97 | 0.06 | 1111 | 0.000 | 0.000 | 0.370 | 0.585 | +0.55 |
| N4-NR7-ENR-c570 | a027 | 168 | 1.31 | 0.98 | 0.03 | 1111 | 0.000 | 0.000 | 0.368 | 0.583 | -0.01 |
| M2-B-A9-ffw-Renko | a4cf9c23 | 100 | 1.31 | 1.00 | 0.08 | 1111 | 0.000 | 0.000 | 0.363 | 0.579 | -0.01 |
| T3S1_G_G_v1:G_G1@NQMNQCM#6 | a778 | 166 | 1.30 | 0.98 | 0.07 | 1111 | 0.000 | 0.000 | 0.360 | 0.576 | +0.59 |
| TINYMERGE:L:market | a778 | 19 | 1.30 | 1.00 | 0.04 | 1111 | 0.000 | 0.000 | 0.359 | 0.576 | +0.04 |
| N8-DISP-6B | a3a74 | 72 | 1.30 | 1.00 | 0.04 | 1111 | 0.000 | 0.000 | 0.354 | 0.571 | +0.13 |
| BM12_NQ | intraday | 12 | 1.28 | 0.98 | 0.08 | 1111 | 0.000 | 0.000 | 0.333 | 0.552 | +0.01 |
| N3-ROLL-ZB | a3a74 | 72 | 1.27 | 1.00 | 0.11 | 1111 | 0.000 | 0.000 | 0.315 | 0.536 | +0.04 |
| N17-G3-RB | n9 | 56 | 1.26 | 0.00 | nan | 1000 | 0.000 | 0.000 | 0.305 | 0.527 | +0.31 |
| SW34_ES | a3a74 | 18 | 1.26 | 0.88 | 0.05 | 1011 | 0.000 | 0.000 | 0.298 | 0.521 | +0.12 |
| WT432:ATR30_m4 | a778 | 36 | 1.26 | 0.99 | 0.05 | 1111 | 0.000 | 0.000 | 0.295 | 0.518 | +0.35 |
| T3S1_G_G_v1:G_G3@NQMNQCM#3 | a778 | 253 | 1.24 | 0.98 | 0.04 | 1111 | 0.000 | 0.000 | 0.278 | 0.501 | +0.57 |
| Q37_RTY | intraday | 8 | 1.24 | 0.97 | 0.01 | 1111 | 0.000 | 0.000 | 0.273 | 0.496 | +0.16 |
| B1leg_BTC | a778 | 180 | 1.22 | 0.95 | 0.04 | 1111 | 0.000 | 0.000 | 0.247 | 0.470 | +0.00 |

## Ensemble comparison (METHOD-2 item 8; summary of REPORT_ENSEMBLE.md, descriptive, not a PASS)
**Verdict (unchanged): not a replacement candidate.** With the live account layer applied to the ensemble (combined day lock cap 8R / arm 2R / give back 67% from 00:00, week floor -8R, per-book 5R/-2R, R = $9,600, minute-resolution marks) the equal-risk ensemble of the ST + HM + WT-10 grids in ONE account earns the live pair's return (OOS Sharpe 2.00 vs 2.10, net $2.64M vs $2.62M, 142 OOS weeks 2024-02..2026-10-16) and the same worst week (-97k vs -83k; the -8R week floor binds), but its max drawdown is still 376k against 280k, and the paired Sharpe-difference 90% interval is [-1.03, +0.85]: it does not exclude under-performance. The lock layer closes the tail gap that Part 1 showed (DD $374-455k -> 376k; worst week -$134k..-150k -> -97k) except for the drawdown. One-account is clearly better than separate accounts (Sharpe 1.26 for three separate accounts). Realisable 10-instance integer version: Sharpe 2.19, DD 276k (as good as the pair on point estimates, but the 3- and 5-instance versions are at 1.60 and the interval is as wide: the difference between 3, 5 and 10 instances is noise).
| book | cells | OOS Sharpe | net | max DD | worst week | CVaR5 | % neg wk | halves Sharpe (h1 / h2) | paired weekly-mean diff 90% CI ($/wk) | Sharpe-diff 90% CI | corr with pair |
|---|---|---|---|---|---|---|---|---|---|---|---|
| LIVE PAIR (library PAIR; 2 cells) | 2 | 2.05 | $2.56M | 280k | -83k | -79k | 42 | 1.76 / 2.30 | - | - | 1.00 |
| pair without daily rules (week floor kept) | 2 | 1.41 | $2.51M | 497k | -92k | -83k | 46 | - | - | - | - |
| E0 ST+HM+WT-10 grids (pre-specified live mechanism) | 728 | 1.93 | $2.49M | 422k | -150k | -119k | 37 | 1.49 / 2.28 | [-8,444, +7,766] | [-1.05, +0.86] | +0.64 |
| E1 = E0 + gates-a-d trend families in the pair factor | 6656 | 1.95 | $2.55M | 449k | -146k | -113k | 38 | 1.33 / 2.43 | [-8,218, +7,554] | [-0.95, +0.73] | +0.68 |
| E2 gates-a-d trend families only | 6386 | 1.95 | $2.56M | 455k | -143k | -112k | 38 | 1.34 / 2.43 | [-8,113, +7,540] | [-0.93, +0.73] | +0.68 |
| E3 ST+HM grids only | 458 | 2.12 | $2.78M | 374k | -134k | -110k | 36 | 1.73 / 2.45 | [-5,122, +8,400] | [-0.69, +0.92] | +0.74 |

Full text: outputs/autopilot/REPORT_ENSEMBLE.md.

## Pair-overlay (delta) families: leverage-matched control
A delta (modified pair minus live pair) that correlates >= 0.9 with the pair is leverage on the pair in its good window (its OOS delta Sharpe mirrors the pair's own 2024-26 Sharpe), not an edge. Each overlay family is re-scored on the residual alpha series (weekly delta regressed on the live pair weekly P&L over each fold's FIT window; residual = delta - beta x pair), sign-flip null, gates a-d; |corr| >= 0.9 families are labelled LEVERAGE and cannot PASS until the residual passes. The earlier E9 re-verification (0 of 37 candidates on the live baseline) is consistent.

| family | owner | cells | note | residual OOS Sharpe | null rank | boot lo | gates a b c d | PASS |
|---|---|---|---|---|---|---|---|---|
| SK_K4_PAIRVAR | a3a74 | 10 | overlay delta; corr(delta, pair) -0.21; beta -0.07; delta OOS Sharpe 1.02; scored on the RESIDUAL | 1.37 | 0.99 | 0.08 | 1111 | no |
| MG_ENTRY | ap_m2c | 18 | overlay delta; corr(delta, pair) -0.31; beta -0.19; delta OOS Sharpe 0.08; scored on the RESIDUAL | 1.16 | 0.98 | 0.02 | 1111 | no |
| PX1_VR60MC | ap_m2c | 6 | overlay delta; corr(delta, pair) -0.15; beta -0.08; delta OOS Sharpe 0.78; scored on the RESIDUAL | 1.04 | 0.97 | 0.02 | 1111 | no |
| DR_G1 | a3a74 | 14 | overlay delta; corr(delta, pair) +0.05; beta -0.01; delta OOS Sharpe 1.02; scored on the RESIDUAL | 0.83 | 0.86 | -0.12 | 1001 | no |
| PX26_GAP | ap_m2c | 6 | overlay delta; corr(delta, pair) +0.10; beta +0.01; delta OOS Sharpe 0.70; scored on the RESIDUAL | 0.72 | 0.91 | -0.10 | 1001 | no |
| MG_WHIP | ap_m2c | 23 | overlay delta; corr(delta, pair) -0.12; beta -0.03; delta OOS Sharpe 0.36; scored on the RESIDUAL | 0.69 | 0.83 | -0.12 | 1001 | no |
| PY4_HMTILT | ap_m2c | 12 | overlay delta; corr(delta, pair) -0.07; beta -0.04; delta OOS Sharpe 0.37; scored on the RESIDUAL | 0.68 | 0.89 | -0.09 | 1001 | no |
| PA5_VR60 | ap_m2c | 9 | overlay delta; corr(delta, pair) -0.23; beta -0.12; delta OOS Sharpe 0.37; scored on the RESIDUAL | 0.67 | 0.89 | -0.10 | 1001 | no |
| DR_G4 | a3a74 | 75 | overlay delta; corr(delta, pair) -0.13; beta -0.06; delta OOS Sharpe 0.37; scored on the RESIDUAL | 0.64 | 0.88 | -0.10 | 1001 | no |
| MG_RISKRULE2 | ap_m2c | 16 | overlay delta; corr(delta, pair) -0.01; beta -0.22; delta OOS Sharpe 0.60; scored on the RESIDUAL | 0.61 | 0.85 | -0.16 | 1000 | no |
| DR_G2 | a3a74 | 36 | overlay delta; corr(delta, pair) -0.15; beta -0.02; delta OOS Sharpe 0.47; scored on the RESIDUAL | 0.56 | 0.77 | -0.18 | 1001 | no |
| PZ3_PARTSTATE | ap_m2c | 6 | overlay delta; corr(delta, pair) -0.03; beta -0.02; delta OOS Sharpe 0.60; scored on the RESIDUAL | 0.51 | 0.80 | -0.10 | 1000 | no |
| PZ4_XINDEX | ap_m2c | 12 | overlay delta; corr(delta, pair) -0.22; beta -0.10; delta OOS Sharpe -0.22; scored on the RESIDUAL | 0.46 | 0.77 | -0.17 | 1000 | no |
| PY8_MINSKIP | ap_m2c | 4 | overlay delta; corr(delta, pair) -0.10; beta -0.03; delta OOS Sharpe 0.26; scored on the RESIDUAL | 0.43 | 0.76 | -0.13 | 1000 | no |
| PZ2_PARTEXIT | ap_m2c | 4 | overlay delta; corr(delta, pair) -0.06; beta -0.04; delta OOS Sharpe 0.44; scored on the RESIDUAL | 0.43 | 0.78 | -0.24 | 1000 | no |
| PX20_ZNSHOCK | ap_m2c | 4 | overlay delta; corr(delta, pair) -0.27; beta -0.21; delta OOS Sharpe -0.25; scored on the RESIDUAL | 0.42 | 0.77 | -0.14 | 1001 | no |
| MG_TILT_MKT | ap_m2c | 27 | overlay delta; corr(delta, pair) -0.27; beta -0.08; delta OOS Sharpe -0.35; scored on the RESIDUAL | 0.39 | 0.70 | -0.16 | 1001 | no |
| PX22_CLSHOCK | ap_m2c | 4 | overlay delta; corr(delta, pair) -0.43; beta -0.24; delta OOS Sharpe -0.40; scored on the RESIDUAL | 0.33 | 0.72 | -0.14 | 1000 | no |
| H0D | ap_m2c | 12 | overlay delta; corr(delta, pair) -0.10; beta -0.61; delta OOS Sharpe -0.08; scored on the RESIDUAL | 0.31 | 0.76 | -0.20 | 1000 | no |
| H11_B | ap_m2c | 12 | overlay delta; corr(delta, pair) -0.16; beta -0.03; delta OOS Sharpe -0.12; scored on the RESIDUAL | 0.30 | 0.70 | -0.28 | 1001 | no |
| G8_C | ap_m2c | 16 | overlay delta; corr(delta, pair) -0.29; beta -0.06; delta OOS Sharpe -0.04; scored on the RESIDUAL | 0.28 | 0.68 | -0.32 | 1000 | no |
| PY5_STTILT | ap_m2c | 12 | overlay delta; corr(delta, pair) -0.06; beta -0.05; delta OOS Sharpe 0.05; scored on the RESIDUAL | 0.24 | 0.67 | -0.24 | 1001 | no |
| DR_G5 | a3a74 | 62 | overlay delta; corr(delta, pair) -0.11; beta -0.05; delta OOS Sharpe 0.23; scored on the RESIDUAL | 0.19 | 0.66 | -0.32 | 1000 | no |
| J9P_A | ap_m2c | 12 | overlay delta; corr(delta, pair) -0.19; beta -0.10; delta OOS Sharpe -0.16; scored on the RESIDUAL | 0.15 | 0.50 | -0.19 | 1001 | no |
| PAIR_STOPENTRY | a3a74 | 17 | overlay delta: NOT residual-scored (excluded from PASS) | 0.13 | 0.62 | -0.23 | 1000 | no |
| MG_RISKRULE | ap_m2c | 20 | overlay delta; corr(delta, pair) -0.32; beta -0.15; delta OOS Sharpe -0.33; scored on the RESIDUAL | 0.11 | 0.59 | -0.28 | 1001 | no |
| H7_A | ap_m2c | 12 | overlay delta; corr(delta, pair) -0.20; beta -0.14; delta OOS Sharpe -0.38; scored on the RESIDUAL | 0.10 | 0.47 | -0.20 | 1000 | no |
| PX21_6ESHOCK | ap_m2c | 4 | overlay delta; corr(delta, pair) -0.42; beta -0.20; delta OOS Sharpe -0.34; scored on the RESIDUAL | 0.08 | 0.55 | -0.21 | 1000 | no |
| G8_B | ap_m2c | 48 | overlay delta; corr(delta, pair) -0.02; beta -0.06; delta OOS Sharpe -0.16; scored on the RESIDUAL | 0.06 | 0.51 | -0.17 | 1000 | no |
| D1F8 | a778 | 32 | overlay delta; corr(delta, pair) +0.85; beta +0.54; delta OOS Sharpe 1.87; scored on the RESIDUAL | 0.05 | 0.47 | -0.22 | 1000 | no |
| PY3_VIXSKEW | ap_m2c | 12 | overlay delta; corr(delta, pair) -0.24; beta -0.06; delta OOS Sharpe -0.21; scored on the RESIDUAL | 0.05 | 0.54 | -0.29 | 1000 | no |
| PA4_NKD | ap_m2c | 9 | overlay delta; corr(delta, pair) -0.07; beta -0.07; delta OOS Sharpe -0.27; scored on the RESIDUAL | 0.05 | 0.56 | -0.31 | 1000 | no |
| H7_B | ap_m2c | 12 | overlay delta; corr(delta, pair) -0.25; beta -0.07; delta OOS Sharpe -0.44; scored on the RESIDUAL | 0.03 | 0.59 | -0.21 | 1000 | no |
| PY6_HEALTH | ap_m2c | 8 | overlay delta; corr(delta, pair) -0.19; beta -0.10; delta OOS Sharpe -0.94; scored on the RESIDUAL | -0.07 | 0.45 | -0.35 | 0000 | no |
| MG_EXIT | ap_m2c | 74 | overlay delta; corr(delta, pair) -0.24; beta -0.19; delta OOS Sharpe -0.99; scored on the RESIDUAL | -0.09 | 0.49 | -0.19 | 0000 | no |
| SX3 | a3a74 | 24 | overlay delta; corr(delta, pair) -0.14; beta -0.13; delta OOS Sharpe -0.73; scored on the RESIDUAL | -0.09 | 0.43 | -0.28 | 0000 | no |
| PY7_TWOFEAT | ap_m2c | 4 | overlay delta; corr(delta, pair) -0.07; beta -0.05; delta OOS Sharpe -0.22; scored on the RESIDUAL | -0.12 | 0.53 | -0.44 | 0000 | no |
| PA9_ALIGN | ap_m2c | 9 | overlay delta; corr(delta, pair) -0.02; beta -0.04; delta OOS Sharpe -0.04; scored on the RESIDUAL | -0.13 | 0.40 | -0.43 | 0000 | no |
| H7_C | ap_m2c | 18 | overlay delta; corr(delta, pair) -0.15; beta -0.05; delta OOS Sharpe -0.93; scored on the RESIDUAL | -0.14 | 0.47 | -0.32 | 0000 | no |
| PY2_VIXVXS | ap_m2c | 12 | overlay delta; corr(delta, pair) -0.25; beta -0.09; delta OOS Sharpe -0.56; scored on the RESIDUAL | -0.15 | 0.40 | -0.41 | 0000 | no |
| DR_G3 | a3a74 | 25 | overlay delta; corr(delta, pair) -0.18; beta -0.08; delta OOS Sharpe -0.41; scored on the RESIDUAL | -0.15 | 0.39 | -0.44 | 0000 | no |
| H8_B | ap_m2c | 16 | overlay delta; corr(delta, pair) -0.26; beta -0.14; delta OOS Sharpe -1.00; scored on the RESIDUAL | -0.16 | 0.39 | -0.35 | 0000 | no |
| J9P_B | ap_m2c | 18 | overlay delta; corr(delta, pair) -0.13; beta -0.06; delta OOS Sharpe -0.46; scored on the RESIDUAL | -0.17 | 0.39 | -0.46 | 0000 | no |
| G11_B | ap_m2c | 15 | overlay delta; corr(delta, pair) -0.22; beta -0.06; delta OOS Sharpe -0.39; scored on the RESIDUAL | -0.19 | 0.39 | -0.32 | 0000 | no |
| PX25_FHR | ap_m2c | 6 | overlay delta; corr(delta, pair) +0.14; beta -0.01; delta OOS Sharpe 0.32; scored on the RESIDUAL | -0.19 | 0.39 | -0.50 | 0000 | no |
| G11_C | ap_m2c | 32 | overlay delta; corr(delta, pair) -0.06; beta -0.24; delta OOS Sharpe -0.52; scored on the RESIDUAL | -0.22 | 0.34 | -0.37 | 0000 | no |
| G6A | ap_m2c | 15 | overlay delta; corr(delta, pair) -0.05; beta -0.10; delta OOS Sharpe -0.82; scored on the RESIDUAL | -0.35 | 0.28 | -0.36 | 0000 | no |
| G6B | ap_m2c | 10 | overlay delta; corr(delta, pair) -0.17; beta -0.08; delta OOS Sharpe -0.65; scored on the RESIDUAL | -0.35 | 0.27 | -0.56 | 0000 | no |
| MG_EVENT | ap_m2c | 26 | overlay delta; corr(delta, pair) -0.18; beta -0.02; delta OOS Sharpe -0.27; scored on the RESIDUAL | -0.36 | 0.27 | -0.45 | 0000 | no |
| PY9_PMWHIP | ap_m2c | 8 | overlay delta; corr(delta, pair) -0.14; beta -0.04; delta OOS Sharpe -0.45; scored on the RESIDUAL | -0.37 | 0.32 | -0.85 | 0000 | no |
| PY10_GAPFLIP | ap_m2c | 4 | overlay delta; corr(delta, pair) +0.08; beta +0.01; delta OOS Sharpe -0.44; scored on the RESIDUAL | -0.38 | 0.38 | -0.38 | 0000 | no |
| PX24_BTC | ap_m2c | 9 | overlay delta; corr(delta, pair) -0.00; beta -0.03; delta OOS Sharpe -0.20; scored on the RESIDUAL | -0.38 | 0.20 | -0.55 | 0000 | no |
| SX2 | a3a74 | 32 | overlay delta; corr(delta, pair) -0.21; beta -0.09; delta OOS Sharpe -1.40; scored on the RESIDUAL | -0.39 | 0.25 | -0.37 | 0000 | no |
| PA10_K4 | ap_m2c | 6 | overlay delta; corr(delta, pair) -0.12; beta -0.09; delta OOS Sharpe -0.11; scored on the RESIDUAL | -0.39 | 0.32 | -0.39 | 0000 | no |
| H0B | ap_m2c | 18 | overlay delta; corr(delta, pair) -0.10; beta -0.03; delta OOS Sharpe -0.70; scored on the RESIDUAL | -0.43 | 0.28 | -0.31 | 0000 | no |
| PA6_VCX | ap_m2c | 6 | overlay delta; corr(delta, pair) -0.15; beta -0.22; delta OOS Sharpe -0.23; scored on the RESIDUAL | -0.43 | 0.28 | -0.48 | 0000 | no |
| SX1 | a3a74 | 16 | overlay delta; corr(delta, pair) -0.17; beta -0.11; delta OOS Sharpe -0.82; scored on the RESIDUAL | -0.44 | 0.21 | -0.36 | 0000 | no |
| PA7_EAE | ap_m2c | 6 | overlay delta; corr(delta, pair) -0.15; beta -0.15; delta OOS Sharpe -0.98; scored on the RESIDUAL | -0.45 | 0.23 | -0.61 | 0000 | no |
| H8_A | ap_m2c | 24 | overlay delta; corr(delta, pair) -0.09; beta -0.04; delta OOS Sharpe -0.98; scored on the RESIDUAL | -0.48 | 0.22 | -0.53 | 0000 | no |
| H6A | ap_m2c | 10 | overlay delta; corr(delta, pair) -0.03; beta -0.09; delta OOS Sharpe -0.79; scored on the RESIDUAL | -0.48 | 0.21 | -0.47 | 0000 | no |
| MG_TILT_CAL | ap_m2c | 15 | overlay delta; corr(delta, pair) -0.27; beta -0.10; delta OOS Sharpe -0.93; scored on the RESIDUAL | -0.49 | 0.24 | -0.39 | 0000 | no |
| PX27_L30VOL | ap_m2c | 3 | overlay delta: NOT residual-scored (excluded from PASS) | -0.52 | 0.26 | -0.49 | 0000 | no |
| H0A | ap_m2c | 15 | overlay delta; corr(delta, pair) -0.02; beta -0.20; delta OOS Sharpe -0.40; scored on the RESIDUAL | -0.52 | 0.27 | -0.34 | 0000 | no |
| D2E9 | a778 | 37 | overlay delta; corr(delta, pair) +0.95 LEVERAGE; beta +0.84; delta OOS Sharpe 2.32; scored on the RESIDUAL | -0.61 | 0.24 | -17715.37 | 0000 | no |
| TINYMERGE:B:pair_overlay | a778 | 21 | overlay delta; corr(delta, pair) +0.97 LEVERAGE; beta +0.92; delta OOS Sharpe 1.96; scored on the RESIDUAL | -0.61 | 0.28 | -4265.61 | 0000 | no |
| G8_D | ap_m2c | 36 | overlay delta; corr(delta, pair) -0.29; beta -0.26; delta OOS Sharpe -1.39; scored on the RESIDUAL | -0.63 | 0.20 | -0.26 | 0000 | no |
| PY1_VIXCHG | ap_m2c | 12 | overlay delta; corr(delta, pair) -0.18; beta -0.07; delta OOS Sharpe -1.26; scored on the RESIDUAL | -0.63 | 0.13 | -0.49 | 0000 | no |
| PAIR_SE1_ENTRYEXEC | a3a74 | 11 | overlay delta: NOT residual-scored (excluded from PASS) | -0.65 | 0.16 | -0.47 | 0000 | no |
| PX23_GCJYSHOCK | ap_m2c | 4 | overlay delta; corr(delta, pair) -0.24; beta -0.33; delta OOS Sharpe -1.12; scored on the RESIDUAL | -0.68 | 0.17 | -0.46 | 0000 | no |
| MG_TILT_MKT2 | ap_m2c | 16 | overlay delta; corr(delta, pair) -0.18; beta -0.10; delta OOS Sharpe -0.51; scored on the RESIDUAL | -0.75 | 0.14 | -0.50 | 0000 | no |
| G8_A | ap_m2c | 24 | overlay delta; corr(delta, pair) -0.20; beta -0.23; delta OOS Sharpe -1.19; scored on the RESIDUAL | -0.81 | 0.09 | -0.45 | 0000 | no |
| FV15 | a778 | 79 | overlay delta; corr(delta, pair) -0.32; beta -0.23; delta OOS Sharpe -1.30; scored on the RESIDUAL | -0.81 | 0.08 | -0.38 | 0000 | no |
| PZ1_NQREGIME | ap_m2c | 12 | overlay delta; corr(delta, pair) -0.28; beta -0.11; delta OOS Sharpe -1.09; scored on the RESIDUAL | -0.81 | 0.07 | -0.58 | 0000 | no |
| C9R1 | a778 | 51 | overlay delta; corr(delta, pair) +0.99 LEVERAGE; beta +0.94; delta OOS Sharpe 1.77; scored on the RESIDUAL | -1.01 | 0.01 | -19435.67 | 0000 | no |
| PA8_GAP | ap_m2c | 9 | overlay delta; corr(delta, pair) -0.12; beta -0.01; delta OOS Sharpe -1.04; scored on the RESIDUAL | -1.01 | 0.02 | -1.14 | 0000 | no |
| G11_A | ap_m2c | 16 | overlay delta; corr(delta, pair) -0.25; beta -0.21; delta OOS Sharpe -1.52; scored on the RESIDUAL | -1.14 | 0.04 | -0.43 | 0000 | no |
| H8_C | ap_m2c | 24 | overlay delta; corr(delta, pair) +0.13; beta -0.05; delta OOS Sharpe -1.51; scored on the RESIDUAL | -1.23 | 0.01 | -1.01 | 0000 | no |
| MG_BRACKET | ap_m2c | 24 | overlay delta; corr(delta, pair) -0.05; beta -0.15; delta OOS Sharpe -1.16; scored on the RESIDUAL | -1.65 | 0.00 | -0.97 | 0000 | no |

## Malformed / missing rows (owners to re-post)
Malformed rows skipped in FAMILY_RESULTS.csv: 219; by owner: {'a4cf9c233a6b3256d': 121, 'n9': 82, 'a3a74': 11, 'a027': 5}.

family ids: SW5_ZN (a3a74), SW6_ZN (a3a74), SW8_ZN (a3a74), SW13_BTC (a3a74), SW15_CL (a3a74), SW15_RTY (a3a74), SW15_ES (a3a74), SW15_YM (a3a74), SW15_GC (a3a74), SW15_ZN (a3a74), SW18_ZN (a3a74), M2-D-YM-A6-ffw-T3 (a4cf9c23), M2-D-ZN-A2-ffw-T3 (a4cf9c23), M2-D-ZN-A5-ffw-T3 (a4cf9c23), M2-D-YM-A6-ffw-T3 (a4cf9c23), M2-D-ZN-A2-ffw-T3 (a4cf9c23), M2-D-ZN-A5-ffw-T3 (a4cf9c23), N1-RT_ZN_ZB-5m-MR (a4cf9c23), N1-RT_ZN_ZF-5m-MR (a4cf9c23), N1-RT_ZN_ZB-5m-MR (a4cf9c23), N1-RT_ZN_ZF-5m-MR (a4cf9c23), N1-RT_ZN_ZF-5m-MOM (a4cf9c23), N1-RT_ZB_ZF-5m-MR (a4cf9c23), N1-RT_ZN_ZT-5m-MR (a4cf9c23), N1-RT_ZB_ZF-5m-MOM (a4cf9c23), N1-RT_ZN_ZT-5m-MOM (a4cf9c23), N1-RT_ZB_ZT-5m-MR (a4cf9c23), N1-RT_ZB_ZT-5m-MOM (a4cf9c23), N1-RT_ZF_ZT-5m-MOM (a4cf9c23), N1-RT_ZF_ZT-5m-MR (a4cf9c23), N1-FX_6E_6A-5m-MR (a4cf9c23), N1-FX_6E_6J-5m-MOM (a4cf9c23), N1-FX_6E_6B-5m-MR (a4cf9c23), N1-FX_6E_6B-5m-MOM (a4cf9c23), N1-FX_6E_6C-5m-MR (a4cf9c23), N1-FX_6E_6A-5m-MOM (a4cf9c23), N1-FX_6E_6C-5m-MOM (a4cf9c23), N1-FX_6J_6B-5m-MR (a4cf9c23), N1-FX_6J_6B-5m-MOM (a4cf9c23), N1-FX_6B_6A-5m-MOM (a4cf9c23), N1-FX_6J_6A-5m-MR (a4cf9c23), N1-FX_6B_6A-5m-MR (a4cf9c23), N1-FX_6J_6A-5m-MOM (a4cf9c23), N1-FX_6A_6C-5m-MOM (a4cf9c23), N1-FX_6B_6C-5m-MR (a4cf9c23), N1-FX_6A_6C-5m-MR (a4cf9c23), N1-FX_6J_6C-5m-MOM (a4cf9c23), N1-AG_ZC_ZS-5m-MR (a4cf9c23), N1-AG_ZC_ZW-5m-MOM (a4cf9c23), N1-FX_6B_6C-5m-MOM (a4cf9c23), N1-AG_ZC_ZW-5m-MR (a4cf9c23), N1-AG_ZC_ZS-5m-MOM (a4cf9c23), N1-AG_ZS_ZW-5m-MR (a4cf9c23), N1-FX_6J_6C-5m-MR (a4cf9c23), N1-AG_ZS_ZW-5m-MOM (a4cf9c23), N1-XA_ES_ZN-5m-MR (a4cf9c23), N1-XA_NQ_ZN-5m-MR (a4cf9c23), N1-XA_GC_ZN-5m-MOM (a4cf9c23), N1-XA_ES_6A-5m-MOM (a4cf9c23), N1-XA_ZB_ES-5m-MR (a4cf9c23), N1-RT_FLY1-5m-MOM (a4cf9c23), N1-RT_FLY1-5m-MR (a4cf9c23), N1-RT_FLY2-5m-MOM (a4cf9c23), N1-RT_FLY2-5m-MR (a4cf9c23), N1-FX_FLY-5m-MOM (a4cf9c23), N1-FX_FLY-5m-MR (a4cf9c23), N1-FX_TRI-5m-MR (a4cf9c23), N1-AG_CRUSH-5m-MR (a4cf9c23), N1-AG_CRUSH-5m-MOM (a4cf9c23), N1-XA_RISK-5m-MR (a4cf9c23), N1-RT_ZN_ZB-30m-MR (a4cf9c23), N1-RT_ZN_ZF-30m-MOM (a4cf9c23), N1-RT_ZN_ZF-30m-MR (a4cf9c23), N1-RT_ZN_ZT-30m-MR (a4cf9c23), N1-RT_ZB_ZF-30m-MR (a4cf9c23), N1-RT_ZF_ZT-30m-MR (a4cf9c23), N1-AG_ZC_ZW-30m-MR (a4cf9c23), N4-ATRR-RTS-c840 (a027), N4-ATRR-AGS-c780 (a027), N6-SETTLE-WIN-o20-FX (a027), N6-SETTLE-WIN-o60-RTS (a027), N6-SETTLE-POST-RTS (a027), N1-RT_FLY1-30m-MOM (a4cf9c23), N1-RT_FLY1-30m-MR (a4cf9c23), N1-RT_FLY2-30m-MR (a4cf9c23), N1-FX_FLY-30m-MR (a4cf9c23), N9-HOURALGO-FX (n9), N9-STALEEXT-RTS (n9), N9-RVOLBRK-RTS (n9), N9-HOURALGO-RTS (n9), N9-AR1SW-RTS (n9), N9-ROUNDNUM-RTS (n9), N9-ROUNDNUM-AGS (n9), N9-AR1SW-AGS (n9), N9-HOURALGO-AGS (n9), N5-IMB-NQ-ETH (a4cf9c23), N5-BURST-ES-MID (a4cf9c23), N5-BURST-ES-CLOSE (a4cf9c23), N5-BURST-ES-ETH (a4cf9c23), N5-SVP-NQ-ETH (a4cf9c23), N5-IMB-ES-OPEN (a4cf9c23), N5-IMB-ES-MID (a4cf9c23), N5-IMB-ES-CLOSE (a4cf9c23), N5-IMB-ES-ETH (a4cf9c23), N5-EXH-NQ-ETH (a4cf9c23), N5-SVP-ES-MID (a4cf9c23), N5-SVP-ES-CLOSE (a4cf9c23), N5-SVP-ES-ETH (a4cf9c23), N5-THIN-ES-OPEN (a4cf9c23), N5-THIN-ES-MID (a4cf9c23), N5-THIN-ES-CLOSE (a4cf9c23), N5-THIN-ES-ETH (a4cf9c23), N5-ICE-NQ-MID (a4cf9c23), N5-RATE-ES-OPEN (a4cf9c23), N5-RATE-ES-MID (a4cf9c23), N5-RATE-ES-CLOSE (a4cf9c23), N5-RATE-ES-ETH (a4cf9c23), N5-ICE-ES-MID (a4cf9c23), N5-ICE-ES-CLOSE (a4cf9c23), N5-ICE-ES-ETH (a4cf9c23), N5-EXH-ES-OPEN (a4cf9c23), N5-EXH-ES-MID (a4cf9c23), N5-EXH-ES-CLOSE (a4cf9c23), N5-EXH-ES-ETH (a4cf9c23), N5-SV-NQ-MID (a4cf9c23), N5-SV-NQ-ETH (a4cf9c23), N5-MOMC-NQ-ETH (a4cf9c23), N5-THIN-NQ-MID (a4cf9c23), N5-THIN-NQ-ETH (a4cf9c23), N12-ROUNDLMT-BRK-RTS (n9), N5-SV-ES-MID (a4cf9c23), N5-SV-ES-CLOSE (a4cf9c23), N5-SV-ES-ETH (a4cf9c23), N5-FADEC-ES-OPEN (a4cf9c23), N5-FADEC-ES-MID (a4cf9c23), N5-FADEC-ES-CLOSE (a4cf9c23), N5-FADEC-ES-ETH (a4cf9c23), N14-KAMA-RTS (n9), N14-STOCHX-RTS (n9), N5-LL-ES2NQ-MID (a4cf9c23), N5-LL-ES2NQ-ETH (a4cf9c23), N5-MOMC-ES-OPEN (a4cf9c23), N5-MOMC-ES-MID (a4cf9c23), N5-MOMC-ES-CLOSE (a4cf9c23), N5-MOMC-ES-ETH (a4cf9c23), N17-G2-ZC (n9), N19-H2_15-ZN (n9), N19-H2_15-ZB (n9), N19-H2_15-ZC (n9), N19-H2_30-ZB (n9), N19-H2_30-ZC (n9), N19-H2_5-ZC (n9), N20-SRVOL-CL-tf15 (n9), N20-SBRK-CL-tf15 (n9), N20-SRVOL-CL-tf30 (n9), N20-SRVOL-CL-tf5 (n9), N20-SMR-CL-tf30 (n9), N20-SMR-CL-tf5 (n9), N20-SMOM-CL-tf5 (n9), N20-SMR-CL-tf15 (n9), N20-STOD-CL-c1 (n9), N20-SMOM-ES-tf15 (n9), N20-SMOM-CL-tf15 (n9), N20-SMOM-CL-tf30 (n9), N20-SBRK-CL-tf5 (n9), N20-SMOM-ES-tf30 (n9), N20-SMOM-ES-tf5 (n9), N20-SMR-ES-tf15 (n9), N20-SMR-ES-tf30 (n9), N20-SRVOL-ES-tf15 (n9), N20-SRVOL-ES-tf30 (n9), N20-SMR-ES-tf5 (n9), N20-SRANGE-ES-tf15 (n9), N20-SRANGE-ES-tf5 (n9), N20-SRVOL-GC-tf15 (n9), N20-SRVOL-ES-tf5 (n9), N20-STOD-ES-c1 (n9), N20-SMR-GC-tf30 (n9), N20-SMR-GC-tf5 (n9), N20-SRVOL-GC-tf30 (n9), N20-SRVOL-GC-tf5 (n9), N20-SMOM-GC-tf5 (n9), N20-SMR-GC-tf15 (n9), N20-SMOM-GC-tf15 (n9), N20-SMOM-GC-tf30 (n9), N20-STOD-GC-c1 (n9), N20-SMOM-NQ-tf5 (n9), N20-SRVOL-NQ-tf5 (n9), N20-SMR-RTY-tf5 (n9), N20-SMOM-RTY-tf15 (n9), N20-SMOM-RTY-tf30 (n9), N20-SMOM-RTY-tf5 (n9), N20-SRVOL-RTY-tf30 (n9), N20-SRVOL-RTY-tf5 (n9), N20-SRVOL-RTY-tf15 (n9), N20-SMR-ZN-tf15 (n9), N20-SMR-ZN-tf30 (n9), N20-SMR-ZN-tf5 (n9), N20-SRANGE-ZN-tf15 (n9), N20-SLEAD-ZN-tf5 (n9), N20-SMOM-ZN-tf15 (n9), N20-SMOM-ZN-tf30 (n9), N20-SMOM-ZN-tf5 (n9), N20-SRVOL-ZN-tf15 (n9), N20-SRVOL-ZN-tf30 (n9), N20-SRANGE-ZN-tf30 (n9), N20-SRANGE-ZN-tf5 (n9), N20-SRVOL-ZN-tf5 (n9), N20-STOD-ZN-c1 (n9), N5-LL-NQ2ES-OPEN (a4cf9c23), N5-LL-NQ2ES-MID (a4cf9c23), N5-LL-NQ2ES-CLOSE (a4cf9c23), N5-LL-NQ2ES-ETH (a4cf9c23), N21-CVDDIV-ZN-tf30 (n9), N21-CVDDIV-ZN-tf5 (n9), N21-CVDDIV-ZN-tf15 (n9), N21-DMOM-ZN-tf15 (n9), N21-DPERS-ZN-tf5 (n9), N21-PDDIS-ZN-tf5 (n9)

Registered READY families with no posted result: 16 by owner {'a778': 14, 'a4cf9c233a6b3256d': 2}
