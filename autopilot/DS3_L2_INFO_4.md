# DS3_L2_INFO_4 - 100-ms lead-lag of ES / RTY vs NQ at the signal second of the six books (INST-5, written 2026-10-31)

**DATA line.** On disk: 100-ms tables (mbp-10 reduced) for NQ / ES / RTY, RTH only (ET 09:30-16:15) 2023-08(NQ 2023-02)..; NQ overnight 100-ms existed; ES and RTY overnight did NOT, so I built them from the raw mbp-10 (the same reducer, `--night`) for 2023-08..2026-01 into out/inst5/night (30 months each, peak RSS 3-4 GB per worker, ~1-3 min per month; far below the 30 GB limit); the 2026-02 raw month file was not decoded (overnight signals of 2026-02 are not scored) and no post-cap file was opened; all reads ts <= 2026-02-06 22:00Z. 16:15-18:00 ET has no 100-ms data. Features/targets for 23,216 signal seconds of the six books + 210,000 random seconds in out/inst5/t2/. To buy: nothing. Prereg `l2vast/ds3/prereg/INFO4_prereg.md` sha256 `eaaea066...`; selection sha `a17d5dbf...` logged before the one recent look; dead_lookup (substring over all stored specs + 40 sampled specs): 0 hits (neighbour: N1D es_lead at 15-180 s).

## Page 1

**Plain sentence.** At the signal second of the six books there is no usable 100-ms lead: after a decision delay of 100 / 250 / 500 ms the best ES/RTY-based feature per (delay, horizon) has |IC| of 0.00-0.03 against a day-clustered MDE of 0.04-0.05 (none beyond MDE in L6M), the implied gross is 0.00-0.07 pt per action for the ES/RTY micro-price and return features (the largest, 0.19 pt, is NQ's own 2-s reversal at a 10-s horizon) against the 1.49 pt round trip (break-even IC 0.18-0.75), 0 LEAD, and filtering the signals by the lead loses in PRE and X' for all three q (10/20/30%). With no delay (reference, not a decision) the same-instant micro-price offset difference ES minus NQ has IC -0.040 at 0.5 s and -0.034 at 1 s (MDE 0.040 / 0.041; PRE -0.043 / -0.037, X' -0.084 / -0.074; placebo rank 1.00 / 0.98; implied gross 0.10 / 0.11 pt): a real but sub-cost carrier that is gone after 100 ms. Unconditional seconds show the same pattern with 3x smaller MDE (IC -0.077 at 0.5 s, d=0) and fall to |IC| <= 0.025 at 100 ms and ~0.01 at 250-500 ms. The 1-s tables of INFO-3 aggregated nothing that matters.

### Table 1 - selected cell per (delay, horizon), state = signal second (IC Spearman, side-signed, NQ mid-to-mid; MDE = 2.8 SE day-cluster; IC sign = the PRE+X' sign, negative means the feature predicts a move AGAINST the signal; rank = |IC_L6M| among 200 within-day shuffles; lag60 = same feature 60 s earlier; ctrl = NQ's own move at the same window)

| delay s | h s | feature | IC PRE | IC X' | IC L3M | IC L6M | MDE L6M | IC HOLD | IC 2026 | lag60 | ctrl | rank | sigma(y) | implied gross pt | cost | break-even IC | top-decile mean y L6M (se) | STRICT/TOL/TOL-B/NOW | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 0 | 0.5 | mo_div_es | -0.043 | -0.084 | -0.037 | -0.040 | 0.040 | -0.044 | -0.070 | +0.008 | -0.023 | 1.00 | 1.40 | 0.099 | 1.49 | 0.61 | +0.06 (0.09) | Y/Y/Y/Y | CANDIDATE |
| 0 | 1 | mo_div_es | -0.037 | -0.074 | -0.018 | -0.034 | 0.041 | -0.035 | -0.044 | +0.002 | -0.029 | 0.98 | 1.85 | 0.111 | 1.49 | 0.46 | +0.11 (0.10) | Y/Y/Y/Y | CANDIDATE |
| 0 | 2 | mo_div_es | -0.032 | -0.052 | +0.004 | -0.013 | 0.045 | -0.011 | -0.006 | -0.004 | -0.014 | 0.65 | 2.59 | 0.060 | 1.49 | 0.33 | +0.15 (0.15) | n/n/n/n | DEAD |
| 0 | 5 | nq_r_2.0 | -0.027 | -0.048 | -0.014 | -0.025 | 0.044 | -0.015 | -0.004 | +0.021 | -0.025 | 0.90 | 3.67 | 0.161 | 1.49 | 0.23 | +0.34 (0.36) | Y/Y/Y/Y | DEAD |
| 0 | 10 | nq_r_2.0 | -0.026 | -0.044 | -0.007 | -0.020 | 0.039 | -0.013 | -0.006 | -0.012 | -0.020 | 0.77 | 4.76 | 0.164 | 1.49 | 0.18 | +0.08 (0.39) | Y/Y/Y/Y | DEAD |
| 0.1 | 0.5 | mo_div_es | -0.018 | -0.042 | -0.003 | -0.006 | 0.041 | -0.008 | -0.050 | +0.004 | -0.016 | 0.34 | 1.22 | 0.012 | 1.49 | 0.70 | +0.10 (0.07) | Y/Y/Y/Y | DEAD |
| 0.1 | 1 | mo_div_rty | -0.028 | -0.023 | -0.005 | -0.020 | 0.039 | -0.018 | -0.007 | -0.014 | -0.022 | 0.84 | 1.73 | 0.062 | 1.49 | 0.49 | +0.02 (0.08) | Y/Y/Y/Y | DEAD |
| 0.1 | 2 | nq_r_1.0 | -0.023 | -0.030 | -0.010 | -0.001 | 0.043 | +0.001 | -0.009 | +0.025 | -0.001 | 0.07 | 2.44 | 0.004 | 1.49 | 0.35 | +0.05 (0.21) | n/Y/Y/Y | DEAD |
| 0.1 | 5 | nq_r_2.0 | -0.027 | -0.058 | -0.022 | -0.021 | 0.050 | -0.013 | -0.011 | +0.014 | -0.021 | 0.82 | 3.54 | 0.128 | 1.49 | 0.24 | +0.32 (0.35) | Y/Y/Y/Y | DEAD |
| 0.1 | 10 | nq_r_2.0 | -0.024 | -0.044 | -0.018 | -0.022 | 0.043 | -0.015 | -0.025 | -0.011 | -0.022 | 0.83 | 4.66 | 0.176 | 1.49 | 0.18 | +0.07 (0.39) | Y/Y/Y/Y | DEAD |
| 0.25 | 0.5 | rrty_0.1 | -0.020 | -0.021 | +0.019 | +0.006 | 0.054 | +0.008 | +0.049 | -0.011 | -0.026 | 0.34 | 1.17 | 0.013 | 1.49 | 0.73 | +0.05 (0.09) | n/n/n/n | DEAD |
| 0.25 | 1 | mo_div_rty | -0.026 | -0.006 | -0.007 | -0.022 | 0.048 | -0.018 | -0.012 | -0.015 | -0.028 | 0.88 | 1.71 | 0.066 | 1.49 | 0.50 | -0.00 (0.08) | Y/Y/Y/Y | DEAD |
| 0.25 | 2 | res_0.1 | -0.027 | -0.021 | +0.003 | -0.002 | 0.044 | +0.000 | +0.030 | -0.007 | -0.009 | 0.14 | 2.41 | 0.010 | 1.49 | 0.35 | +0.08 (0.04) | n/n/n/n | DEAD |
| 0.25 | 5 | nq_r_2.0 | -0.029 | -0.059 | -0.017 | -0.019 | 0.054 | -0.013 | -0.006 | +0.010 | -0.019 | 0.81 | 3.50 | 0.119 | 1.49 | 0.24 | +0.26 (0.34) | Y/Y/Y/Y | DEAD |
| 0.25 | 10 | nq_r_2.0 | -0.023 | -0.046 | -0.023 | -0.024 | 0.043 | -0.018 | -0.022 | -0.011 | -0.024 | 0.87 | 4.62 | 0.192 | 1.49 | 0.18 | +0.02 (0.38) | Y/Y/Y/Y | DEAD |
| 0.5 | 0.5 | res_0.5 | -0.010 | -0.032 | +0.038 | +0.014 | 0.050 | +0.016 | +0.030 | +0.016 | -0.003 | 0.64 | 1.14 | 0.028 | 1.49 | 0.75 | +0.05 (0.07) | n/n/n/n | DEAD |
| 0.5 | 1 | res_0.5 | -0.015 | -0.061 | +0.017 | +0.004 | 0.039 | +0.007 | -0.019 | +0.018 | -0.022 | 0.21 | 1.62 | 0.012 | 1.49 | 0.52 | -0.07 (0.18) | n/n/n/n | DEAD |
| 0.5 | 2 | nq_r_1.0 | -0.020 | -0.044 | -0.027 | -0.005 | 0.039 | -0.004 | +0.004 | +0.021 | -0.005 | 0.28 | 2.33 | 0.019 | 1.49 | 0.36 | -0.19 (0.21) | Y/Y/Y/Y | DEAD |
| 0.5 | 5 | nq_r_2.0 | -0.032 | -0.060 | -0.014 | -0.023 | 0.046 | -0.017 | +0.013 | +0.016 | -0.023 | 0.86 | 3.47 | 0.140 | 1.49 | 0.25 | +0.20 (0.32) | Y/Y/Y/Y | DEAD |
| 0.5 | 10 | nq_r_2.0 | -0.024 | -0.043 | -0.025 | -0.021 | 0.042 | -0.016 | -0.018 | -0.009 | -0.021 | 0.82 | 4.62 | 0.170 | 1.49 | 0.18 | -0.02 (0.36) | Y/Y/Y/Y | DEAD |

Counts over the 20 signal-state cells: STRICT 14, TOLERANT 15, TOL-B 15, TOL-nc 15, NOW-ONLY 15, CANDIDATE 2 (both at d=0, the reference), LEAD 0. The IC-form gates pass often because the selected IC keeps its (negative) sign in all windows, but |IC| is inside the MDE in every decision cell (d >= 0.1 s), so the tier is DEAD. The top-decile mean y is the HIGH-feature decile (for negative-IC features that is the adverse side).

### Table 2 - unconditional seconds (210,000, same features; for context)

| delay s | h s | feature | IC PRE | IC X' | IC L6M | MDE L6M | rank | implied gross pt | tier |
|---|---|---|---|---|---|---|---|---|---|
| 0 | 0.5 | mo_div_es | -0.066 | -0.091 | -0.077 | 0.013 | 1.00 | 0.105 | CANDIDATE |
| 0 | 1 | mo_div_es | -0.051 | -0.074 | -0.048 | 0.014 | 1.00 | 0.091 | CANDIDATE |
| 0 | 2 | mo_div_es | -0.039 | -0.055 | -0.033 | 0.015 | 1.00 | 0.089 | CANDIDATE |
| 0 | 5 | mo_div_es | -0.017 | -0.026 | -0.021 | 0.016 | 1.00 | 0.091 | CANDIDATE |
| 0 | 10 | mo_div_es | -0.019 | -0.019 | -0.016 | 0.014 | 1.00 | 0.096 | CANDIDATE |
| 0.1 | 0.5 | mo_div_es | -0.024 | -0.029 | -0.025 | 0.014 | 1.00 | 0.033 | CANDIDATE |
| 0.1 | 1 | mo_div_es | -0.020 | -0.034 | -0.017 | 0.015 | 1.00 | 0.032 | CANDIDATE |
| 0.1 | 2 | mo_div_es | -0.019 | -0.026 | -0.011 | 0.014 | 0.97 | 0.030 | CANDIDATE |
| 0.1 | 5 | nq_r_2.0 | -0.008 | -0.018 | -0.013 | 0.018 | 0.98 | 0.055 | CANDIDATE |
| 0.1 | 10 | leadrty_0.5 | +0.010 | +0.013 | +0.005 | 0.016 | 0.66 | 0.031 | DEAD |
| 0.25 | 0.5 | nq_r_0.5 | -0.015 | -0.013 | -0.013 | 0.017 | 0.98 | 0.017 | CANDIDATE |
| 0.25 | 1 | mo_div_es | -0.014 | -0.018 | -0.004 | 0.015 | 0.52 | 0.008 | DEAD |
| 0.25 | 2 | nq_r_1.0 | -0.016 | -0.014 | -0.010 | 0.018 | 0.97 | 0.028 | CANDIDATE |
| 0.25 | 5 | nq_r_2.0 | -0.009 | -0.018 | -0.010 | 0.016 | 0.94 | 0.042 | CANDIDATE |
| 0.25 | 10 | leadrty_0.5 | +0.010 | +0.012 | +0.002 | 0.015 | 0.34 | 0.013 | DEAD |
| 0.5 | 0.5 | mo_div_es | -0.008 | -0.017 | +0.007 | 0.013 | 0.79 | 0.009 | DEAD |
| 0.5 | 1 | mo_div_es | -0.008 | -0.018 | +0.003 | 0.014 | 0.41 | 0.006 | DEAD |
| 0.5 | 2 | nq_r_2.0 | -0.015 | -0.013 | -0.004 | 0.016 | 0.68 | 0.011 | DEAD |
| 0.5 | 5 | nq_r_2.0 | -0.009 | -0.017 | -0.007 | 0.017 | 0.83 | 0.030 | DEAD |
| 0.5 | 10 | nq_r_2.0 | -0.007 | -0.012 | -0.007 | 0.016 | 0.82 | 0.040 | DEAD |

### Table 3 - filter stage on the six books (skip the signal when the (d=0.25 s, h=1 s) selected feature mo_div_rty is in its worst q of PRE+X'; per contract = pts per planned lot, kept signals, N)

| q | skipped | L3M | L6M | MDE L6M | PRE | X' | carried (PRE and X' > 0) |
|---|---|---|---|---|---|---|---|
| 10% | 812 | -0.12 | -0.26 | 0.61 | -0.15 | -0.30 | False |
| 20% | 1581 | +0.14 | -0.26 | 0.87 | -0.20 | -0.57 | False |
| 30% | 2397 | -0.58 | -0.86 | 1.17 | -0.37 | -1.14 | False |

No filter cell is carried, so no recent look or stack line was run (the pre-declared stack stage stops at selection). Linked to the engine trades: 17,576 of 51,998 candidate rows (the sig table holds the six books' signals; the rest are other books).

## Limits
* Mid-to-mid information only (no fills); decision delay modelled as the order landing at T+d with the feature known at T. The 250 ms point uses the last 100-ms state at or before T+0.25 s (T+0.2 s). The signal-second timestamp is the 1-s bar label (information through T), as in INFO-1..3; the sub-second position of the signal inside the second is unknown, so d=0 is optimistic.
* The 100-ms rows are event-driven in the overnight tables; the state is carried forward (30 s staleness guard); RTH tables are complete.
* ES/RTY exist from 2023-08 only: X' is 2023-08..2024-01 for these features. Overnight 2026-02 is missing (raw month not decoded).
* The 40 selected features are dominated by the known micro-price carrier (`mo_div`, cycles 2-3) and NQ's own 1-2 s reversal; the pure ES/RTY return lead features (`lead*`, `r*`) were never the selected ones except `rrty_0.1`, `res_0.1/0.5`, whose IC is within +-0.014.
* Code l2vast/ds3/code/inst5/t2_*.py, rows out/recent_wins/info4.csv, DEAD_CELLS +2,498 rows with the A2 rows.
