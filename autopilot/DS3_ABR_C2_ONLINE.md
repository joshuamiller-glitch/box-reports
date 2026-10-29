# DS3_ABR_C2_ONLINE - adaptive brackets, path-profile tables, online learners, ensembles, CUSUM, meta-label (ABRC2, 2026-10-29)

Research only; no live, execution-server or chart change; UNTOUCHED (label day > 2026-02-06) never read. Prereg l2vast/ds3/prereg/ABRC2_prereg.md sha256 75301ac84aa05faa8b2a7a15a26a11d047acbfa01579f6b5b65f13421abeaab7 (amendment A1: cell count only). PRE-only text autopilot/DS3_ABR_C2_PREHOLD.md sha256 ee5835e26a57fc7cb493c4998e8f1f107a2880dd1f43c1165eae7d9ceb59ee49 written before HOLD/X' were read; one logged look per prereg group (track ABR_C2 in out/abr/looks.jsonl). Code l2vast/ds3/code/abr_c2/. Outputs l2vast/ds3/out/abr/wf/c2/ (chains_*.npz = decision per entry per cell as a K32/K990 bracket index, cells_verdict.parquet = every statistic and gate per cell, final_tables.md, policy_candidate.txt, distill.json, placebo.json, rc_pre.json). Decision files are wide npz (one int8/int16 column per cell) rather than the THP long schema; the entry-level choice, the 60/60 comparator and fit-end rule are reproducible from them (fit_end <= entry_ts asserted in every batch chain).

## Verdict (plain)
**0 PASS, 0 CANDIDATE, 2,364 DEAD of 2,364 cells** (G1a 1,920 batch Bayesian regime tables; G1b 240 online tables; G2a 80 fixed-bracket re-selection; G3 25 online RLS; G4 51 ensembles/CUSUM/meta; G5 48 K990 path-profile tables). White reality check on PRE over all cells: max weekly t 2.24, p = 0.49 (G1a 0.48, G1b 0.38, G2a 0.63, G3 0.14, G4 0.73, G5 0.35). Shuffled-feature null: max t over the 2,185 shuffled counterparts is 1.62 vs 2.24 for the real G1a/G1b/G3 cells, a small gap that the best-of-N p of 0.49 says is not distinguishable from selection noise.

Plain sentence: choosing the bracket from the state at entry, re-fitted on the last N (any N from 1 week to 12 months, EWMA 5/10/20 days, intraday to monthly, or updated after every closed trade), adds +4.3 pts/trade in the PRE selection span for the best table (IN-SAMPLE selection, CI +0.4..+8.1, MDE 5.5) but +0.6 on HOLD (MDE 10.6) and +0.5 on X' (MDE 5.6) out of sample, i.e. nothing distinguishable from zero; the best-of-2,364 RC is p 0.49; nothing beats the simplest wide-bracket tilt (frozen abs120|OR|none: PRE +2.33, HOLD +3.17, X +0.22, ABRA, all within MDE); the fixed 60/60 stays the live bracket on every book. Across cells PRE and HOLD are NEGATIVELY correlated (r = -0.28 over G1a): the PRE winners regress.

## Gates (counts of cells failing; none softened)
mean_up 1,217; holdout_sign 762; PRE CI excludes 0: 2,352 fail (12 pass: 11 G1a, 1 G1b); placebo >= 0.90 2,351 fail (placebo ranks were run for the top-10 PRE cells of each family only; every other cell is treated as failing); neighbours 1,875; 2x_slip 1,631; G_basis 2,095; year_share > 60% 2,203; SPAN2 (X' <= 0) 2,050; maxDD not worse 2,364 (every policy has a deeper weekly maxDD than 60/60 at live lots: wider stops); RC p > 0.05 2,364. Cells with PRE>0, HOLD>0 and X'>0: G1a 79, G1b 4, G4 3, G5 9, G2a 0, G3 0. The best PRE cell g1a|sess|pooled|0|ew5|1w (session table, EWMA half-life 5 days, weekly re-fit, no gate) passes mean_up, holdout sign, neighbours (3/3) and both placebo ranks (1.00/1.00) and fails G_basis, maxDD and RC_p, so it is DEAD under the prereg (CANDIDATE allows one other failure). Placebo ranks of 1.00 against shuffled and random-assignment draws for this cell are the within-cell selection (best of 1,920), not an edge: the shuffled-feature best-of-N max is 1.62 t vs 2.24.

## Walk-forward results, selected cells (WALK-FORWARD OOS chain; PRE is where the cell was picked = IN-SAMPLE selection; HOLD and X' are confirmation; delta vs 60/60, pts per lot at 10 lots, week-cluster CI; usd_wk at live lots)
| cell | PRE | HOLD | X' (2023-07..2024-01) | verdict | failed |
|--|--|--|--|--|--|
| G1a sess table, pooled, ew5, 1w (best PRE) | +4.26 [+0.44,+8.07] MDE 5.5 | +0.57 [-6.83,+7.97] MDE 10.6 | +0.52 MDE 5.6 | DEAD | G_basis, maxDD, RC |
| G1a tod table, z1, ew10, 1w | +4.06 | +0.05 [-5.1,+5.2] MDE 7.4 | -0.08 | DEAD | G_basis, year_share, SPAN2, maxDD, RC |
| G1b online tod table, z1, hl 20d (best online table) | +2.78 [+0.06,+5.50] | -1.30 MDE 7.0 | -1.88 | DEAD | holdout_sign, 2x_slip, G_basis, year_share, SPAN2, maxDD, RC |
| G2a fixed re-selection, pooled 12m, monthly (best baseline) | +1.55 [-3.79,+6.90] MDE 7.6 | +2.82 [-1.73,+7.38] MDE 6.5 | -0.83 | DEAD | CI, placebo (0.55), SPAN2, maxDD, RC |
| G3 online RLS lam .995, margin 4 | +2.46 [-0.57,+5.48] MDE 4.3 | +3.19 [-2.69,+9.07] MDE 8.4 | -1.56 | DEAD | CI, placebo (0.10), year_share, SPAN2, maxDD, RC |
| G4 best (FIXREL E1 ensemble) | +1.48 | +2.82 [-2.7,+8.4] | -3.16 | DEAD | CI, placebo, neighbours, year_share, SPAN2, maxDD, RC |
| G5 K990 path-profile table, sess, ew20, 1w | +2.42 [-0.77,+5.61] | -0.63 MDE 8.8 | +0.57 | DEAD | holdout_sign, CI, 2x_slip, G_basis, year_share, maxDD, RC |
| baseline: frozen best-PRE fixed bracket abs120/OR/none (ABRA) | +2.33 MDE 6.2 | +3.17 MDE 10.9 | +0.22 MDE 6.4 | (bound, not a cell) | |
| baseline: random bracket assignment, same bracket distribution (20 draws/top cell) | see placebo.json; the random draws beat the 12m/1w re-selection chains (rank 0.00) and are below the table chains | | | | |
No cell has a HOLD CI above 0 except two G1a sig3 z=1 12m cells whose PRE is about 0 (-0.03/+0.38) and X' is negative (multiplicity: 2 of 2,364). Win rate falls for every wide-bracket policy (0.43 vs 0.52 for 60/60) and average realised R is higher only because the stop is wider and the winners larger, which is the same shape change that ABRA's oracle shows.

## Answers to the asked questions
* Recency: in PRE, mean delta over G1a cells is -0.55 (1w) -0.09 (2w) +0.29 (1m) +0.11 (3m) +0.26 (6m) +0.18 (12m) +0.30 (YTD) -0.59 (ew5) -0.08 (ew10) -0.06 (ew20): short windows are no better than long ones (they are worse for 1w/ew5) and add noise. Steps: weekly +0.86, monthly -0.07, daily -0.38, intraday -0.51 (PRE), so intraday re-fits do NOT beat daily or weekly; with the all-actions-resolved availability rule intraday re-fits add almost no new training trades anyway. HOLD means by window are all within 1.5 pts and sign-unstable; X' is negative for every window (the first chain months have 3 months of warm-up only).
* Keys: the only keysets with positive PRE mean are session (+0.75), time of day (+0.87) and session x ATR (+0.49); ATR, VIX, first-hour range, ES-NQ correlation, signal strength and their combinations are around zero or negative; the confidence gate z=1 is no better than z=0 (PRE -0.20 vs +0.15); pooled beats per-book. The session/time-of-day signal in PRE is the tilt toward wide brackets whose advantage differs by session, and it flips in 2026 (best cell 2026 -5.1 pts, -$318k/wk at live lots).
* Online vs batch: online Bayesian tables PRE mean -0.36, batch -0.02; RLS (the only family with mean PRE > 0, +1.46, HOLD +2.6) is X' negative in all 25 cells and has placebo rank 0.00-0.10 against random assignment of its own bracket mix: it is the wide-bracket tilt, not state information.
* CUSUM trigger (24 cells): triggers 500-1,000 times over 136 weeks (it fires on ordinary noise), best PRE +0.57; no improvement over scheduled re-fits. Meta-label gate (9 cells) and window ensembles (18 cells) add nothing: best PRE +1.48 (FIXREL ensemble), its placebo rank is 0.00.
* K990 (path-profile over every bracket in the grid) is no better than K32: best PRE +2.42, HOLD -0.63..+0.9, selection among 990 actions adds noise (RC p 0.35).

## Primary tables for the best-by-PRE policy and the stack (full set for four other policies in final_tables.md)
### P_BEST_PRE (G1a sess table ew5/1w) (WALK-FORWARD OOS chain; HOLD/X = confirmation; PRE = selection span)
| span | n | delta vs 60/60 pts/trade [95% CI] | MDE80 | $/wk at live lots | win pol/ctrl | avg R pol/ctrl | diff share |
|--|--|--|--|--|--|--|--|
| HOLD | 11396 | +0.57 [-6.83,+7.97] | 10.57 | 48544 | 0.42/0.52 | 0.002/0.005 | 0.97 |
| PRE | 26022 | +4.26 [+0.44,+8.07] | 5.45 | 240162 | 0.43/0.52 | 0.040/0.006 | 0.98 |
| X | 7039 | +0.52 [-3.42,+4.46] | 5.63 | 14310 | 0.45/0.51 | 0.014/0.005 | 0.99 |

| book (all scored) | n | delta vs 60/60 pts/trade [95% CI] | MDE80 | $/wk at live lots | win pol/ctrl | avg R pol/ctrl | diff share |
|--|--|--|--|--|--|--|--|
| CR | 2511 | -0.56 [-3.87,+2.74] | 4.72 | -2074 | 0.42/0.49 | -0.048/-0.051 | 0.97 |
| DN | 3074 | +1.88 [-2.04,+5.80] | 5.61 | 8497 | 0.44/0.53 | 0.053/0.041 | 0.98 |
| HM | 3914 | +1.94 [-1.60,+5.48] | 5.06 | 11172 | 0.43/0.52 | 0.032/0.013 | 0.98 |
| KB | 5232 | +3.24 [-0.04,+6.52] | 4.69 | 12964 | 0.43/0.52 | 0.029/0.007 | 0.98 |
| MA | 1935 | +2.34 [-1.44,+6.12] | 5.40 | 6655 | 0.45/0.53 | 0.038/0.030 | 0.98 |
| MV | 4907 | +3.95 [-0.83,+8.73] | 6.83 | 28485 | 0.43/0.52 | 0.028/0.003 | 0.98 |
| PB | 3821 | +5.65 [+1.06,+10.23] | 6.55 | 31728 | 0.44/0.52 | 0.057/0.002 | 0.98 |
| PE | 5087 | +2.58 [-1.19,+6.35] | 5.39 | 10828 | 0.43/0.51 | 0.014/-0.011 | 0.98 |
| SM | 1587 | +3.63 [-0.61,+7.87] | 6.06 | 6269 | 0.45/0.53 | 0.056/0.032 | 0.98 |
| ST | 5119 | +1.83 [-2.17,+5.84] | 5.72 | 13782 | 0.43/0.52 | 0.030/0.015 | 0.98 |
| WT | 7270 | +2.51 [-0.86,+5.89] | 4.82 | 18821 | 0.43/0.52 | 0.015/0.001 | 0.98 |

| entry session | n | delta vs 60/60 pts/trade [95% CI] | MDE80 | $/wk at live lots | win pol/ctrl | avg R pol/ctrl | diff share |
|--|--|--|--|--|--|--|--|
| asia | 11663 | +4.17 [-1.35,+9.68] | 7.88 | 58237 | 0.42/0.53 | 0.063/0.025 | 0.98 |
| close | 140 | -5.80 [-20.02,+8.43] | 20.32 | -1826 | 0.39/0.41 | -0.156/-0.158 | 0.95 |
| london | 9402 | -3.40 [-9.01,+2.21] | 8.01 | -40227 | 0.39/0.52 | -0.049/0.003 | 0.98 |
| nyam | 12090 | +4.52 [-1.87,+10.91] | 9.13 | 67617 | 0.45/0.53 | 0.059/0.022 | 1.00 |
| nypm | 8498 | +4.48 [-0.43,+9.39] | 7.01 | 47715 | 0.47/0.50 | 0.028/-0.020 | 0.95 |
| pre | 2664 | +4.68 [-3.30,+12.65] | 11.39 | 14871 | 0.39/0.49 | -0.009/-0.057 | 0.96 |

| trade year | n | delta vs 60/60 pts/trade [95% CI] | MDE80 | $/wk at live lots | win pol/ctrl | avg R pol/ctrl | diff share |
|--|--|--|--|--|--|--|--|
| 2023 | 5935 | +1.33 [-2.77,+5.44] | 5.86 | 44687 | 0.46/0.51 | 0.011/0.002 | 1.00 |
| 2024 | 15529 | +4.36 [-0.25,+8.97] | 6.59 | 207123 | 0.44/0.52 | 0.058/0.021 | 0.97 |
| 2025 | 20678 | +2.77 [-2.51,+8.05] | 7.54 | 184546 | 0.42/0.52 | 0.013/-0.007 | 0.98 |
| 2026 | 2315 | -5.14 [-12.40,+2.11] | 10.37 | -318520 | 0.44/0.54 | -0.022/0.027 | 1.00 |

| 2023 span (2023-07..12) | n | delta vs 60/60 pts/trade [95% CI] | MDE80 | $/wk at live lots | win pol/ctrl | avg R pol/ctrl | diff share |
|--|--|--|--|--|--|--|--|
| 2023 | 5935 | +1.33 [-2.77,+5.44] | 5.86 | 44687 | 0.46/0.51 | 0.011/0.002 | 1.00 |

### P_RLS (G3 lam .995 m4) (WALK-FORWARD OOS chain; HOLD/X = confirmation; PRE = selection span)
| span | n | delta vs 60/60 pts/trade [95% CI] | MDE80 | $/wk at live lots | win pol/ctrl | avg R pol/ctrl | diff share |
|--|--|--|--|--|--|--|--|
| HOLD | 11396 | +3.19 [-2.69,+9.07] | 8.40 | 210223 | 0.43/0.52 | 0.024/0.005 | 0.96 |
| PRE | 26022 | +2.46 [-0.57,+5.48] | 4.32 | 134554 | 0.43/0.52 | 0.022/0.006 | 0.96 |
| X | 7039 | -1.56 [-5.00,+1.88] | 4.91 | -68162 | 0.44/0.51 | -0.024/0.005 | 0.93 |

| book (all scored) | n | delta vs 60/60 pts/trade [95% CI] | MDE80 | $/wk at live lots | win pol/ctrl | avg R pol/ctrl | diff share |
|--|--|--|--|--|--|--|--|
| CR | 2511 | +1.57 [-1.73,+4.87] | 4.71 | 5800 | 0.43/0.49 | -0.029/-0.051 | 0.96 |
| DN | 3074 | -0.37 [-4.05,+3.32] | 5.26 | -1651 | 0.43/0.53 | 0.014/0.041 | 0.94 |
| HM | 3914 | +0.66 [-2.86,+4.19] | 5.03 | 3822 | 0.43/0.52 | 0.005/0.013 | 0.95 |
| KB | 5232 | +2.26 [-0.97,+5.49] | 4.62 | 9047 | 0.43/0.52 | 0.019/0.007 | 0.95 |
| MA | 1935 | +2.06 [-1.73,+5.84] | 5.41 | 5859 | 0.44/0.53 | 0.029/0.030 | 0.95 |
| MV | 4907 | +3.30 [-0.48,+7.08] | 5.40 | 23823 | 0.42/0.52 | 0.014/0.003 | 0.95 |
| PB | 3821 | +3.35 [+0.05,+6.65] | 4.72 | 18829 | 0.43/0.52 | 0.029/0.002 | 0.96 |
| PE | 5087 | +2.67 [-0.35,+5.68] | 4.31 | 11174 | 0.42/0.51 | -0.003/-0.011 | 0.95 |
| SM | 1587 | +2.07 [-2.42,+6.57] | 6.42 | 3582 | 0.45/0.53 | 0.052/0.032 | 0.96 |
| ST | 5119 | +2.21 [-1.06,+5.48] | 4.67 | 16632 | 0.43/0.52 | 0.024/0.015 | 0.95 |
| WT | 7270 | +1.50 [-1.26,+4.26] | 3.95 | 11214 | 0.43/0.52 | 0.020/0.001 | 0.95 |

| entry session | n | delta vs 60/60 pts/trade [95% CI] | MDE80 | $/wk at live lots | win pol/ctrl | avg R pol/ctrl | diff share |
|--|--|--|--|--|--|--|--|
| asia | 11663 | -0.02 [-4.75,+4.71] | 6.76 | -230 | 0.40/0.53 | 0.010/0.025 | 0.96 |
| close | 140 | +0.52 [-7.59,+8.62] | 11.58 | 191 | 0.34/0.41 | -0.235/-0.158 | 0.96 |
| london | 9402 | -0.91 [-5.89,+4.07] | 7.12 | -9100 | 0.40/0.52 | -0.021/0.003 | 0.95 |
| nyam | 12090 | +4.79 [+0.07,+9.51] | 6.74 | 68743 | 0.46/0.53 | 0.066/0.022 | 0.96 |
| nypm | 8498 | +5.94 [+0.13,+11.74] | 8.29 | 60430 | 0.46/0.50 | 0.036/-0.020 | 0.95 |
| pre | 2664 | -3.88 [-10.02,+2.26] | 8.77 | -11826 | 0.37/0.49 | -0.121/-0.057 | 0.96 |

| trade year | n | delta vs 60/60 pts/trade [95% CI] | MDE80 | $/wk at live lots | win pol/ctrl | avg R pol/ctrl | diff share |
|--|--|--|--|--|--|--|--|
| 2023 | 5935 | -1.02 [-4.24,+2.21] | 4.61 | -47725 | 0.44/0.51 | -0.025/0.002 | 0.94 |
| 2024 | 15529 | +2.27 [-1.17,+5.71] | 4.91 | 103770 | 0.45/0.52 | 0.043/0.021 | 0.94 |
| 2025 | 20678 | +2.73 [-1.12,+6.58] | 5.50 | 185029 | 0.41/0.52 | 0.001/-0.007 | 0.96 |
| 2026 | 2315 | +1.57 [-16.80,+19.93] | 26.24 | 106694 | 0.42/0.54 | 0.048/0.027 | 0.95 |

| 2023 span (2023-07..12) | n | delta vs 60/60 pts/trade [95% CI] | MDE80 | $/wk at live lots | win pol/ctrl | avg R pol/ctrl | diff share |
|--|--|--|--|--|--|--|--|
| 2023 | 5935 | -1.02 [-4.24,+2.21] | 4.61 | -47725 | 0.44/0.51 | -0.025/0.002 | 0.94 |

### P_FIXREL (G2a pooled 12m/1m) (WALK-FORWARD OOS chain; HOLD/X = confirmation; PRE = selection span)
| span | n | delta vs 60/60 pts/trade [95% CI] | MDE80 | $/wk at live lots | win pol/ctrl | avg R pol/ctrl | diff share |
|--|--|--|--|--|--|--|--|
| HOLD | 11396 | +2.82 [-1.73,+7.38] | 6.50 | 170127 | 0.36/0.52 | 0.055/0.005 | 1.00 |
| PRE | 26022 | +1.55 [-3.79,+6.90] | 7.64 | 83549 | 0.41/0.52 | 0.016/0.006 | 1.00 |
| X | 7039 | -0.83 [-4.06,+2.40] | 4.61 | -33186 | 0.47/0.51 | -0.011/0.005 | 1.00 |

| book (all scored) | n | delta vs 60/60 pts/trade [95% CI] | MDE80 | $/wk at live lots | win pol/ctrl | avg R pol/ctrl | diff share |
|--|--|--|--|--|--|--|--|
| CR | 2511 | +0.23 [-3.50,+3.96] | 5.33 | 855 | 0.41/0.49 | -0.033/-0.051 | 1.00 |
| DN | 3074 | +0.42 [-4.83,+5.68] | 7.50 | 1913 | 0.41/0.53 | 0.039/0.041 | 1.00 |
| HM | 3914 | -0.39 [-4.61,+3.83] | 6.02 | -2249 | 0.40/0.52 | 0.016/0.013 | 1.00 |
| KB | 5232 | +0.83 [-2.62,+4.29] | 4.93 | 3333 | 0.40/0.52 | 0.012/0.007 | 1.00 |
| MA | 1935 | +2.87 [-1.82,+7.55] | 6.69 | 8156 | 0.43/0.53 | 0.056/0.030 | 1.00 |
| MV | 4907 | +1.35 [-2.77,+5.47] | 5.88 | 9726 | 0.40/0.52 | 0.017/0.003 | 1.00 |
| PB | 3821 | +3.24 [-1.47,+7.95] | 6.72 | 18201 | 0.41/0.52 | 0.036/0.002 | 1.00 |
| PE | 5087 | +2.19 [-1.97,+6.34] | 5.94 | 9155 | 0.40/0.51 | 0.017/-0.011 | 1.00 |
| SM | 1587 | +4.22 [-0.47,+8.90] | 6.69 | 7286 | 0.43/0.53 | 0.068/0.032 | 1.00 |
| ST | 5119 | +0.82 [-3.80,+5.44] | 6.60 | 6203 | 0.40/0.52 | 0.021/0.015 | 1.00 |
| WT | 7270 | +2.13 [-1.93,+6.19] | 5.80 | 15962 | 0.40/0.52 | 0.023/0.001 | 1.00 |

| entry session | n | delta vs 60/60 pts/trade [95% CI] | MDE80 | $/wk at live lots | win pol/ctrl | avg R pol/ctrl | diff share |
|--|--|--|--|--|--|--|--|
| asia | 11663 | -1.00 [-7.47,+5.48] | 9.25 | -17509 | 0.37/0.53 | 0.008/0.025 | 1.00 |
| close | 140 | -6.60 [-19.94,+6.75] | 19.06 | -2227 | 0.41/0.41 | -0.159/-0.158 | 1.00 |
| london | 9402 | +1.32 [-5.75,+8.38] | 10.10 | 15003 | 0.38/0.52 | 0.036/0.003 | 1.00 |
| nyam | 12090 | +4.35 [-1.34,+10.04] | 8.13 | 61934 | 0.44/0.53 | 0.054/0.022 | 1.00 |
| nypm | 8498 | +1.01 [-3.97,+5.98] | 7.11 | 11747 | 0.45/0.50 | -0.006/-0.020 | 1.00 |
| pre | 2664 | +2.17 [-7.66,+12.01] | 14.05 | 8692 | 0.37/0.49 | -0.024/-0.057 | 1.00 |

| trade year | n | delta vs 60/60 pts/trade [95% CI] | MDE80 | $/wk at live lots | win pol/ctrl | avg R pol/ctrl | diff share |
|--|--|--|--|--|--|--|--|
| 2023 | 5935 | -0.57 [-2.25,+1.11] | 2.40 | -23002 | 0.48/0.51 | -0.011/0.002 | 1.00 |
| 2024 | 15529 | +2.04 [-3.57,+7.65] | 8.02 | 90612 | 0.43/0.52 | 0.027/0.021 | 1.00 |
| 2025 | 20678 | +1.87 [-3.98,+7.71] | 8.35 | 121363 | 0.37/0.52 | 0.025/-0.007 | 1.00 |
| 2026 | 2315 | -0.05 [-7.83,+7.72] | 11.10 | 7477 | 0.36/0.54 | 0.033/0.027 | 1.00 |

| 2023 span (2023-07..12) | n | delta vs 60/60 pts/trade [95% CI] | MDE80 | $/wk at live lots | win pol/ctrl | avg R pol/ctrl | diff share |
|--|--|--|--|--|--|--|--|
| 2023 | 5935 | -0.57 [-2.25,+1.11] | 2.40 | -23002 | 0.48/0.51 | -0.011/0.002 | 1.00 |

### P_ONLINE_TAB (G1b tod z1 hl20) (WALK-FORWARD OOS chain; HOLD/X = confirmation; PRE = selection span)
| span | n | delta vs 60/60 pts/trade [95% CI] | MDE80 | $/wk at live lots | win pol/ctrl | avg R pol/ctrl | diff share |
|--|--|--|--|--|--|--|--|
| HOLD | 11396 | -1.30 [-6.21,+3.62] | 7.03 | -67202 | 0.42/0.52 | -0.017/0.005 | 0.79 |
| PRE | 26022 | +2.78 [+0.06,+5.50] | 3.88 | 161268 | 0.42/0.52 | 0.036/0.006 | 0.80 |
| X | 7039 | -1.88 [-4.67,+0.91] | 3.99 | -77650 | 0.46/0.51 | -0.002/0.005 | 0.78 |

| book (all scored) | n | delta vs 60/60 pts/trade [95% CI] | MDE80 | $/wk at live lots | win pol/ctrl | avg R pol/ctrl | diff share |
|--|--|--|--|--|--|--|--|
| CR | 2511 | +2.34 [-0.52,+5.19] | 4.08 | 8635 | 0.43/0.49 | -0.026/-0.051 | 0.76 |
| DN | 3074 | -0.85 [-4.00,+2.30] | 4.50 | -3845 | 0.43/0.53 | 0.021/0.041 | 0.78 |
| HM | 3914 | +0.73 [-2.37,+3.84] | 4.44 | 4212 | 0.42/0.52 | 0.019/0.013 | 0.80 |
| KB | 5232 | +1.73 [-0.94,+4.40] | 3.81 | 6918 | 0.43/0.52 | 0.027/0.007 | 0.81 |
| MA | 1935 | +1.46 [-2.18,+5.10] | 5.20 | 4147 | 0.45/0.53 | 0.045/0.030 | 0.77 |
| MV | 4907 | +1.99 [-1.45,+5.43] | 4.92 | 14343 | 0.42/0.52 | 0.023/0.003 | 0.80 |
| PB | 3821 | +1.57 [-2.17,+5.31] | 5.34 | 8818 | 0.43/0.52 | 0.026/0.002 | 0.79 |
| PE | 5087 | +0.43 [-2.21,+3.07] | 3.77 | 1787 | 0.42/0.51 | 0.001/-0.011 | 0.80 |
| SM | 1587 | +0.02 [-4.06,+4.10] | 5.83 | 41 | 0.45/0.53 | 0.029/0.032 | 0.78 |
| ST | 5119 | +0.77 [-2.07,+3.60] | 4.06 | 5760 | 0.42/0.52 | 0.018/0.015 | 0.81 |
| WT | 7270 | +0.62 [-1.87,+3.10] | 3.56 | 4605 | 0.42/0.52 | 0.008/0.001 | 0.79 |

| entry session | n | delta vs 60/60 pts/trade [95% CI] | MDE80 | $/wk at live lots | win pol/ctrl | avg R pol/ctrl | diff share |
|--|--|--|--|--|--|--|--|
| asia | 11663 | +1.05 [-2.77,+4.87] | 5.45 | 13167 | 0.41/0.53 | 0.034/0.025 | 0.81 |
| close | 140 | -4.06 [-13.80,+5.68] | 13.92 | -1420 | 0.39/0.41 | -0.114/-0.158 | 0.78 |
| london | 9402 | -1.40 [-6.74,+3.95] | 7.63 | -14643 | 0.41/0.52 | -0.010/0.003 | 0.75 |
| nyam | 12090 | +1.93 [-2.59,+6.45] | 6.46 | 28136 | 0.44/0.53 | 0.038/0.022 | 0.85 |
| nypm | 8498 | +2.17 [-1.21,+5.55] | 4.83 | 22783 | 0.46/0.50 | 0.009/-0.020 | 0.72 |
| pre | 2664 | +1.51 [-5.52,+8.53] | 10.04 | 6825 | 0.38/0.49 | -0.037/-0.057 | 0.86 |

| trade year | n | delta vs 60/60 pts/trade [95% CI] | MDE80 | $/wk at live lots | win pol/ctrl | avg R pol/ctrl | diff share |
|--|--|--|--|--|--|--|--|
| 2023 | 5935 | -1.04 [-3.73,+1.64] | 3.84 | -46934 | 0.46/0.51 | 0.002/0.002 | 0.81 |
| 2024 | 15529 | +2.21 [-1.23,+5.65] | 4.92 | 105441 | 0.44/0.52 | 0.044/0.021 | 0.74 |
| 2025 | 20678 | +0.57 [-2.92,+4.06] | 4.99 | 43082 | 0.40/0.52 | -0.001/-0.007 | 0.84 |
| 2026 | 2315 | +1.91 [-8.13,+11.96] | 14.35 | 147675 | 0.45/0.54 | 0.019/0.027 | 0.73 |

| 2023 span (2023-07..12) | n | delta vs 60/60 pts/trade [95% CI] | MDE80 | $/wk at live lots | win pol/ctrl | avg R pol/ctrl | diff share |
|--|--|--|--|--|--|--|--|
| 2023 | 5935 | -1.04 [-3.73,+1.64] | 3.84 | -46934 | 0.46/0.51 | 0.002/0.002 | 0.81 |

### FROZEN abs120|OR|none (WALK-FORWARD OOS chain; HOLD/X = confirmation; PRE = selection span)
| span | n | delta vs 60/60 pts/trade [95% CI] | MDE80 | $/wk at live lots | win pol/ctrl | avg R pol/ctrl | diff share |
|--|--|--|--|--|--|--|--|
| HOLD | 11396 | +3.17 [-4.44,+10.78] | 10.87 | 202427 | 0.44/0.52 | 0.029/0.005 | 1.00 |
| PRE | 26022 | +2.33 [-2.04,+6.70] | 6.24 | 128128 | 0.44/0.52 | 0.022/0.006 | 1.00 |
| X | 7039 | +1.01 [-4.66,+6.67] | 8.09 | 35464 | 0.48/0.51 | 0.011/0.005 | 1.00 |

| book (all scored) | n | delta vs 60/60 pts/trade [95% CI] | MDE80 | $/wk at live lots | win pol/ctrl | avg R pol/ctrl | diff share |
|--|--|--|--|--|--|--|--|
| CR | 2511 | +1.07 [-2.64,+4.78] | 5.30 | 3949 | 0.48/0.49 | -0.017/-0.051 | 1.00 |
| DN | 3074 | +0.84 [-4.30,+5.98] | 7.34 | 3800 | 0.44/0.53 | 0.027/0.041 | 1.00 |
| HM | 3914 | +1.00 [-2.92,+4.91] | 5.60 | 5729 | 0.44/0.52 | 0.015/0.013 | 1.00 |
| KB | 5232 | +1.83 [-1.60,+5.26] | 4.90 | 7330 | 0.45/0.52 | 0.019/0.007 | 1.00 |
| MA | 1935 | +5.36 [+0.32,+10.40] | 7.20 | 15248 | 0.47/0.53 | 0.060/0.030 | 1.00 |
| MV | 4907 | +2.34 [-2.15,+6.83] | 6.41 | 16907 | 0.44/0.52 | 0.021/0.003 | 1.00 |
| PB | 3821 | +4.15 [-0.64,+8.93] | 6.83 | 23302 | 0.45/0.52 | 0.036/0.002 | 1.00 |
| PE | 5087 | +1.66 [-2.15,+5.46] | 5.44 | 6949 | 0.44/0.51 | 0.009/-0.011 | 1.00 |
| SM | 1587 | +6.26 [+0.98,+11.54] | 7.54 | 10809 | 0.46/0.53 | 0.068/0.032 | 1.00 |
| ST | 5119 | +1.10 [-3.69,+5.88] | 6.84 | 8249 | 0.44/0.52 | 0.017/0.015 | 1.00 |
| WT | 7270 | +3.22 [-0.88,+7.33] | 5.86 | 24103 | 0.45/0.52 | 0.027/0.001 | 1.00 |

| entry session | n | delta vs 60/60 pts/trade [95% CI] | MDE80 | $/wk at live lots | win pol/ctrl | avg R pol/ctrl | diff share |
|--|--|--|--|--|--|--|--|
| asia | 11663 | +2.91 [-3.21,+9.03] | 8.74 | 39240 | 0.42/0.53 | 0.037/0.025 | 1.00 |
| close | 140 | -5.75 [-20.18,+8.68] | 20.61 | -1873 | 0.41/0.41 | -0.127/-0.158 | 1.00 |
| london | 9402 | +2.46 [-5.02,+9.94] | 10.69 | 29407 | 0.42/0.52 | 0.022/0.003 | 1.00 |
| nyam | 12090 | +4.22 [-1.66,+10.10] | 8.40 | 60345 | 0.48/0.53 | 0.046/0.022 | 1.00 |
| nypm | 8498 | +0.41 [-4.27,+5.09] | 6.68 | 4162 | 0.48/0.50 | -0.007/-0.020 | 1.00 |
| pre | 2664 | -2.59 [-12.19,+7.01] | 13.72 | -5666 | 0.41/0.49 | -0.050/-0.057 | 1.00 |

| trade year | n | delta vs 60/60 pts/trade [95% CI] | MDE80 | $/wk at live lots | win pol/ctrl | avg R pol/ctrl | diff share |
|--|--|--|--|--|--|--|--|
| 2023 | 5935 | +1.74 [-4.11,+7.59] | 8.35 | 63464 | 0.48/0.51 | 0.016/0.002 | 1.00 |
| 2024 | 15529 | +2.34 [-2.49,+7.17] | 6.90 | 104595 | 0.45/0.52 | 0.030/0.021 | 1.00 |
| 2025 | 20678 | +2.64 [-3.00,+8.29] | 8.06 | 178321 | 0.43/0.52 | 0.018/-0.007 | 1.00 |
| 2026 | 2315 | +1.10 [-16.43,+18.63] | 25.04 | 90353 | 0.43/0.54 | 0.023/0.027 | 1.00 |

| 2023 span (2023-07..12) | n | delta vs 60/60 pts/trade [95% CI] | MDE80 | $/wk at live lots | win pol/ctrl | avg R pol/ctrl | diff share |
|--|--|--|--|--|--|--|--|
| 2023 | 5935 | +1.74 [-4.11,+7.59] | 8.35 | 63464 | 0.48/0.51 | 0.016/0.002 | 1.00 |

## STACK LEVEL (all 11 books, scored span 2023-07..2026-02, 136 weeks; walk-forward chains)
| series | basis | $/wk mean | SD of weekly $ | maxDD $ | worst-20-weeks sum $ | mean lots | mean stop pts | mean risk/trade $ |
|--|--|--|--|--|--|--|--|--|
| LIVE brackets (stack as is) | const lots (live) | 20169 | 313000 | 2868721 | -9961702 | 8.3 | 55.1 | 9178 |
| 60/60 | const lots (live) | 20748 | 331981 | 2864608 | -10702091 | 8.3 | 60.0 | 10018 |
| 60/60 | const $-risk | 21487 | 402185 | 3683324 | -13254325 | 10.0 | 60.0 | 12000 |
| P_BEST_PRE (G1a sess table ew5/1w) | const lots (live) | 167875 | 1109989 | 8391696 | -28452362 | 8.3 | 89.6 | 14938 |
| P_BEST_PRE (G1a sess table ew5/1w) | const $-risk | 98647 | 735809 | 6125885 | -21066179 | 9.3 | 89.6 | 12083 |
| P_RLS (G3 lam .995 m4) | const lots (live) | 128879 | 900565 | 5917423 | -21666679 | 8.3 | 81.2 | 13556 |
| P_RLS (G3 lam .995 m4) | const $-risk | 50273 | 666337 | 5193796 | -19090188 | 10.8 | 81.2 | 12079 |
| P_FIXREL (G2a pooled 12m/1m) | const lots (live) | 99289 | 1260903 | 9079785 | -37441068 | 8.3 | 96.5 | 16101 |
| P_FIXREL (G2a pooled 12m/1m) | const $-risk | 84934 | 866536 | 6450141 | -25434180 | 7.7 | 96.5 | 12073 |
| P_ONLINE_TAB (G1b tod z1 hl20) | const lots (live) | 76171 | 852203 | 7370615 | -24891803 | 8.3 | 79.8 | 13306 |
| P_ONLINE_TAB (G1b tod z1 hl20) | const $-risk | 58689 | 697776 | 5924479 | -21813546 | 9.5 | 79.8 | 12076 |
| FROZEN abs120|OR|none | const lots (live) | 147121 | 1260022 | 8683723 | -38245579 | 8.3 | 120.0 | 20036 |
| FROZEN abs120|OR|none | const $-risk | 90545 | 749460 | 5257293 | -22713027 | 5.0 | 120.0 | 12000 |

## Stop slippage at the chosen stops (estimator slip10 at the exit stop, stop-type exits only; mean pts per lot; 10 lots)
| policy | 2023 | 2024 | 2025 | 2026 | share stop exits | mean stop S |
|--|--|--|--|--|--|--|
| 60/60 | 0.51 | 0.87 | 0.94 | 0.69 | 0.45 | 60.0 |
| P_BEST_PRE (G1a sess table ew5/1w) | 0.38 | 0.73 | 0.91 | 0.88 | 0.44 | 89.6 |
| P_RLS (G3 lam .995 m4) | 0.41 | 0.70 | 0.89 | 0.60 | 0.46 | 81.2 |
| P_FIXREL (G2a pooled 12m/1m) | 0.43 | 0.72 | 0.96 | 0.67 | 0.50 | 96.5 |
| P_ONLINE_TAB (G1b tod z1 hl20) | 0.54 | 0.90 | 0.93 | 0.71 | 0.48 | 79.8 |
| FROZEN abs120|OR|none | 0.31 | 0.72 | 0.96 | 0.64 | 0.41 | 120.0 |

Measured-walk reference (stopfill_by_stop_year.csv, mean slip pts): abs60 10 lots 2023 0.45 / 2024 0.84 / 2025 0.95 / 2026 0.63; abs120 10 lots 0.26 / 0.72 / 0.96 / 0.65, at rp lots (5) 0.13 / 0.50 / 0.65 / 0.41.

## Exposure effect (constant lots): risk per trade = stop x lots x $20
- 60/60: mean risk/trade $10018, p90 $12000, share of trades with stop > 60 pts 0.00; daily sum of risk taken (mean) $662745 vs 60/60 $662745
- P_BEST_PRE (G1a sess table ew5/1w): mean risk/trade $14938, p90 $24000, share of trades with stop > 60 pts 0.68; daily sum of risk taken (mean) $988265 vs 60/60 $662745
- P_RLS (G3 lam .995 m4): mean risk/trade $13556, p90 $24000, share of trades with stop > 60 pts 0.59; daily sum of risk taken (mean) $896781 vs 60/60 $662745
- P_FIXREL (G2a pooled 12m/1m): mean risk/trade $16101, p90 $24000, share of trades with stop > 60 pts 0.73; daily sum of risk taken (mean) $1065157 vs 60/60 $662745
- P_ONLINE_TAB (G1b tod z1 hl20): mean risk/trade $13306, p90 $24000, share of trades with stop > 60 pts 0.53; daily sum of risk taken (mean) $880261 vs 60/60 $662745
- FROZEN abs120|OR|none: mean risk/trade $20036, p90 $24000, share of trades with stop > 60 pts 1.00; daily sum of risk taken (mean) $1325491 vs 60/60 $662745

State of the exposure effect in plain terms: every policy the search likes widens the stop (mean stop 80-97 pts vs 60, 68% of trades above 60 pts for the best cell). At constant lots that raises the risk per trade by 49% (mean $14.9k vs $10.0k, p90 $24k vs $12k) and the daily risk taken by 49% ($988k vs $663k); the extra $/wk (+$147k/wk at live lots, +$77k/wk at constant $-risk lots, in-sample dominated: PRE $240k/wk vs HOLD $49k/wk and 2026 negative) comes with weekly SD 3.3x higher and maxDD 2.9x deeper at constant lots (1.8x / 1.7x at constant $-risk). At constant $-risk parity the frozen abs120 stack has SD 749k vs 402k and maxDD $5.3M vs $3.7M for 60/60. Stop slippage at the chosen stops is the same as or slightly below the 60/60 level in the estimator (0.4-0.9 pt/lot by year, wider stops no worse; measured-walk table agrees at 10 lots) and is NOT what drives any result.

## Distilled table (item 6)
l2vast/ds3/out/abr/wf/c2/policy_candidate.txt: 91 rules over 4 NT8-computable features (session, ATR14 ratio tercile with PRE cut points, Keltner signal-strength tercile, overnight vol bucket), cells give stop, target, time exit, lot multiplier 60/stop; header says NOT for live. Student fitted on PRE only, static: PRE +9.30 (IN-SAMPLE, 91 rules: overfit) HOLD +0.30 [-4.02,+4.62] (MDE 6.2) X' +1.16; teacher (best PRE walk-forward cell) HOLD +0.57 (MDE 10.6). Retained gain on HOLD = 52% of the teacher (target 80% NOT met), but both numbers are inside the MDE, so retained gain is not a meaningful statistic here. The honest policy file is the 60/60 table.

## Caveats and deviations
* Availability rule: a trade is used for fitting only once ALL actions' outcomes are known (max TEX over the action set, i.e. about 6 h median, up to a day), so intraday refit steps add few same-day trades. Conservative on purpose.
* Min training count per-book scope: 600 pooled trades (approx 60 per book) instead of per-book counting. Constant-lot basis uses 10-lot measured scores (M10) with live lots only in $; CR lots assumed 10. 2x_slip charges the exit-stop estimator slip again on stop exits of both arms; the G basis is gross at touch (no costs): the G_basis gate removes cells that win only because of the cost/target-correction convention.
* Placebo draws: 20 shuffled-feature and 20 random-assignment draws for the top-10 PRE cells per family (59 cells); one shuffled draw for every G1/G3 cell (feeds the placebo RC). G2a/G4 have random-assignment only; G5 none (shown as NaN and treated as failing). Neighbours for G4 = cells that differ in one setting.
* ABRA had already looked at HOLD/X for its fixed-bracket groups; the ABRC2 look is for its own cells. The frozen abs120|OR|none is in the candidate set (disclosed in prereg section 0). Long-horizon realism: the policy picks time exits using the stored minute profile, not a live replay; target fills use the year correction convention of ABRA (short-target fills untested).
* Incident: my first g4 run (ensemble/CUSUM/meta) was lost to the memory cap (an array decompressed once per column kept 130 GB RSS; the coordinator sent SIGTERM). Fixed by loading each npz once and copying columns; g4 and the evaluator were rerun with ulimit -v caps, at most 12 workers, MemAvailable stayed above 100 GB afterwards. Nothing from the lost run was used.
* ABRA audit (out/abr/audit_results.json, checked before finalising): entry-row test 0 mismatches over 19,272 feature comparisons on 132 entries; aux-series truncation test finished: 4 cut points x 38 series, 0 mismatching series (aux_series_mismatches 0). No leak found in the entry features.
