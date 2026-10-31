# DS3_INST_A - auction / market-profile day structure (T-INSTITUTIONAL section A), INST-1, written 2026-10-31 16:39Z

**DATA line.** On disk: NQ tick tape 2023-02..2026-10 (/mnt/l2/l2vast/tables/NQ/tape, one outright per month), 1-s and 1-min tables with mbp-10 summaries, ES/RTY 1-s/1-min, raw mbp-10. Derived here from the tape (capped 2026-02-06): per RTH day volume profile with the 70% value area (POC, VAH, VAL), 30-min TPO counts (interior single prints >= 2 pts, poor high/low = no single-print tail > 2 pts), the overnight session (18:00 ET -> 09:30) hi/lo/VWAP, IB60 and IB30, IB-extension times at 0 / 0.5 / 1 / 2 x IB, and 1-s hi/lo/last arrays for 778 RTH days. **To buy: nothing for section A** (no quote needed). Prior-day levels are not comparable across a contract roll: 13 roll days carry open-location = na.

Prereg `l2vast/ds3/prereg/INST_A_prereg.md` sha256 `4225ba3d...` (logged in DECISIONS.md before any outcome statistic; file sha in DECISIONS.md is the one to check). PART 1 selection `out/inst/A/reg_selection.json` and PART 3 selection `sa_selection.json` were logged before the recent-window look; one recent look per part. Code `l2vast/ds3/code/inst/A/`, out `l2vast/ds3/out/inst/A/`, rows `out/recent_wins/inst_A.csv`.

## Page 1

**Plain sentence.** Auction day structure (A): 421 state x scope skip cells on the six live books (ex-ante state: open vs prior value area / range / overnight range, ON inventory, IB width and location, day type at 10:30 and 11:00, prior poor high/low and single prints, trade vs break / value / inventory), 36 positive in PRE and X' and looked at once in the recent windows, 0 PASS, 5 CANDIDATE rows (2 distinct ideas, shadow only, shrunk size 0); the best is K6 in NY-PM/close skipped when the PRIOR day left interior single prints: +1.99 pts per contract L6M (MDE 2.43; HOLD +1.85, PRE +0.86, X' +1.35), stack +1.22k/wk L6M (MDE 1.26k; PRE +0.42, X' +0.55), shuffled-day placebo rank 0.99, Romano-Wolf p 0.17 over the 36 looked-at cells (not significant), persistence 0.60; the stand-alone books are the opposite story: the IB break that agrees with the overnight inventory paid +6.9 / +10.5 pts per trade (avg of its 12 variants, PRE / X') and pays +5.34 (best variant, MDE 32.1) to -16.3 in L6M, a regime flip; the 80%-rule long/short back to value (A1, k=1) is +9.8 pts per trade L6M on 26 trades (MDE 27) but its shuffled prior-day placebo rank is only 0.65 and the purged-CV choice among all 66 cells earned -4.0 pts per trade out of sample; nothing is promoted.

Counts (per-contract gate AND stack gate, TOLERANT = T-SIXTY addendum literal): regime carried 36: STRICT 10, TOLERANT 9, TOL-B (post-hoc) 11, TOL-nc (post-hoc) 11, NOW-ONLY 14 (rows; 22 distinct rules after removing identical vectors); standalone carried 28 of 66: STRICT 5, TOLERANT 1, TOL-B (post-hoc) 1, TOL-nc (post-hoc) 1, NOW-ONLY 5. Tiers: PASS 0; CANDIDATE regime 5 rows / standalone 1; the rest DEAD. STRICT is not a subset of TOLERANT here because TOLERANT also requires the PRE worst-20 test and the stack gate. Nothing promoted; every row post-hoc labelled.

### Table 1 - regime cells with a positive L6M (looked at once; per contract = pts per planned lot of the scope's signals, state skipped; stack in $k/wk at live lots)

| rule (skip signals when ...) | scope | n skipped (/wk) | N L3M | L6M | HOLD | PRE | X' | MDE L6M | M L6M | LIVE-CAL L6M | stack L3M | L6M | HOLD | PRE | X' (MDE L6M) | 12R L6M / PRE | shuffle rank | RW p | STRICT / TOL / NOW | tier | persist | shrunk size |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| p_single | ALL nypmc | 213 (2.6) | +1.46 | +1.99 | +1.85 | +0.86 | +1.35 | 2.43 | +1.99 | +2.48 | +1.09 | +1.22 | +1.07 | +0.42 | +0.55 (1.26) | +0.71 / -0.21 | 0.99 | 0.17 | Y/Y/Y | CANDIDATE | 0.60 | 0.00 |
| p_single | K6 NY | 535 (4.7) | +1.26 | +0.62 | +0.52 | +0.27 | +1.06 | 1.46 | +0.62 | +0.82 | +2.44 | +1.41 | +1.16 | +0.45 | +1.21 (2.14) | +1.07 / -0.18 | 0.94 | 0.72 | Y/Y/Y | CANDIDATE | 0.65 | 0.00 |
| DT1100=trend | ALL nypmc | 46 (1.8) | -0.17 | +0.45 | +0.46 | +0.13 | +0.83 | 1.35 | +0.45 | +0.49 | -0.09 | +0.25 | +0.24 | +0.06 | +0.40 (0.64) | +0.06 / -0.24 | 0.95 | 0.84 | n/n/n | DEAD | 0.43 | 0.00 |
| AGAINST_BREAK | ALL nypmc | 233 (2.1) | +0.99 | +0.44 | +0.38 | +0.15 | +0.77 | 1.87 | +0.44 | +0.52 | +1.05 | +0.50 | +0.42 | -0.05 | +0.39 (1.31) | +0.13 / -0.51 | 0.77 | 0.95 | n/n/Y | DEAD | 0.55 | 0.00 |
| DT1100=normal | M6 nyam | 176 (1.9) | -0.01 | +0.24 | +0.08 | +0.02 | +0.23 | 0.89 | +0.24 | +0.26 | -0.19 | +0.36 | +0.08 | +0.05 | +0.28 (1.44) | +5.24 / +0.09 | 0.96 | 0.93 | n/n/n | DEAD | 0.43 | 0.00 |
| p_poorH | ALL nypmc | 75 (1.6) | +0.50 | +0.20 | +0.23 | +1.04 | +0.24 | 1.13 | +0.20 | +0.22 | +0.26 | +0.11 | +0.12 | +0.52 | +0.10 (0.61) | -0.01 / -0.27 | 0.67 | 0.97 | Y/Y/Y | DEAD | 0.52 | 0.00 |
| AGAINST_BREAK | ALL NY | 345 (2.7) | +0.22 | +0.17 | +0.15 | +0.05 | +0.25 | 0.45 | +0.17 | +0.18 | +1.48 | +1.06 | +0.91 | -0.06 | +0.84 (1.90) | +0.22 / -0.14 | 0.97 | 0.84 | n/n/Y | CANDIDATE | 0.57 | 0.00 |
| AGAINST_IB30 | M6 nyam | 67 (1.3) | +0.02 | +0.13 | +0.11 | +0.04 | +0.03 | 0.40 | +0.13 | +0.13 | +0.05 | +0.23 | +0.20 | +0.07 | +0.07 (0.79) | +0.21 / -0.05 | 0.78 | 0.93 | Y/Y/Y | DEAD | 0.44 | 0.00 |
| AGAINST_BREAK | ALL nyam | 112 (1.5) | +0.09 | +0.12 | +0.10 | +0.03 | +0.15 | 0.44 | +0.12 | +0.12 | +0.48 | +0.58 | +0.51 | +0.13 | +0.64 (1.30) | +0.21 / +0.42 | 0.98 | 0.93 | Y/n/Y | CANDIDATE | 0.53 | 0.00 |
| AGAINST_BREAK | K6 NY | 310 (2.5) | +0.43 | +0.09 | +0.05 | +0.16 | +0.43 | 0.84 | +0.09 | +0.10 | +1.24 | +0.52 | +0.40 | -0.00 | +0.55 (1.58) | -0.08 / -0.06 | 0.70 | 0.99 | n/n/Y | DEAD | 0.55 | 0.00 |
| DT1030=nv_cand | ALL nypmc | 264 (2.5) | +0.54 | +0.04 | +0.06 | +0.01 | +0.28 | 2.35 | +0.04 | +0.08 | +0.29 | +0.02 | +0.04 | +0.00 | +0.10 (1.26) | -0.63 / -0.45 | 0.55 | 1.00 | Y/Y/Y | DEAD | 0.48 | 0.00 |

Regime cells carried but negative in L6M (11 distinct): AGAINST_BREAK [K6 nyam], INV=short [M6 nyam], OL_ON=bottom [M6 nyam], OL_ON=mid [ALL nypmc], OL_VA=inside [ALL nypmc], P1030=lower [ALL nypmc], P1030=mid [ALL NY], P1030=mid [ALL nyam], P1030=mid [P6 nyam], p_single [ALL NY], p_single [H6 nyam]. These were positive in PRE and X' and negative now: the two selection windows do not predict L6M (chance).

### Table 2 - stand-alone books (NQ, 1 contract, N fills, 3-s decision delay; M = worst print of the delay second + 1 tick through for limits; LIVE_CAL = join stop 2.45; per trade net pts; stack = +5 contracts add-on, $k/wk)

| cell | n L6M | N L3M | L6M | HOLD | PRE | X' | MDE L6M | 1-s delay L6M | M L6M | LIVE-CAL L6M | stack5 L3M | L6M | HOLD | PRE | X' (MDE L6M) | placebo shuffle / IB-shift beaten of 4 | RW p | CV folds + | capacity (contracts) | STRICT/TOL/NOW | tier | persist |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A1|k=1|filt=0|tgt=0|stop=60 | 26 | +3.70 | +7.20 | +8.10 | +2.80 | +2.17 | 24.06 | +8.03 | -2.50 | +6.93 | +0.29 | +0.67 | +0.81 | +0.25 | +0.22 (1.97) | 0.68 / n/a | 0.85 | 3/5 | 6.00 | Y/n/Y | DEAD | 0.36 |
| A1|k=1|filt=0|tgt=0|stop=90 | 26 | +7.32 | +9.79 | +11.41 | +4.51 | +5.59 | 26.75 | +10.69 | +8.82 | +9.61 | +0.58 | +0.91 | +1.14 | +0.40 | +0.56 (2.15) | 0.65 / n/a | 0.78 | 4/5 | 6.00 | Y/Y/Y | DEAD | 0.38 |
| A1|k=1|filt=0|tgt=1|stop=60 | 36 | +17.49 | +7.64 | +6.13 | +0.28 | +2.33 | 38.78 | +7.77 | -5.49 | +7.12 | +2.12 | +0.98 | +0.90 | +0.03 | +0.29 (3.59) | 0.59 / n/a | 0.87 | 3/5 | 5.75 | Y/n/Y | DEAD | 0.42 |
| A2|filt=0|tgt=0|stop=45 | 125 | -1.30 | +1.09 | +0.74 | +0.20 | +2.04 | 17.66 | +2.06 | +0.81 | +0.39 | -0.56 | +0.48 | +0.34 | +0.09 | +0.94 (7.87) |  / 3 | 0.96 | 3/5 | 6.75 | n/n/n | DEAD | 0.33 |
| A2|filt=0|tgt=0|stop=60 | 125 | +1.20 | +1.16 | +0.78 | +1.61 | +0.56 | 20.00 | -0.24 | -0.46 | +0.54 | +0.51 | +0.52 | +0.36 | +0.72 | +0.26 (10.39) |  / 4 | 0.97 | 3/5 | 6.75 | Y/n/Y | CANDIDATE | 0.34 |
| A2|filt=0|tgt=0|stop=90 | 125 | -4.77 | +1.34 | +1.35 | +2.04 | +3.04 | 22.64 | +0.63 | +0.40 | +0.92 | -2.04 | +0.60 | +0.62 | +0.91 | +1.40 (10.64) |  / 3 | 0.97 | 3/5 | 6.75 | n/n/n | DEAD | 0.33 |
| A2|filt=0|tgt=1|stop=0 | 125 | -12.46 | -3.47 | -3.32 | +1.01 | +1.75 | 21.71 | -3.73 | -4.50 | -3.94 | -5.34 | -1.55 | -1.51 | +0.45 | +0.80 (11.04) |  / 2 | 0.99 | 2/5 | 6.75 | n/n/n | DEAD | 0.33 |
| A2|filt=0|tgt=1|stop=45 | 125 | -5.74 | -2.58 | -2.03 | +0.44 | +4.77 | 16.54 | -1.56 | -2.85 | -3.28 | -2.46 | -1.15 | -0.92 | +0.20 | +2.19 (7.07) |  / 3 | 0.99 | 2/5 | 6.75 | n/n/n | DEAD | 0.33 |
| A2|filt=0|tgt=1|stop=60 | 125 | -3.24 | -2.55 | -2.02 | +1.28 | +3.22 | 18.92 | -3.95 | -4.17 | -3.17 | -1.39 | -1.14 | -0.92 | +0.57 | +1.48 (9.53) |  / 4 | 0.99 | 2/5 | 6.75 | n/n/n | DEAD | 0.33 |
| A2|filt=0|tgt=1|stop=90 | 125 | -11.81 | -5.86 | -4.65 | +1.90 | +5.98 | 21.25 | -6.58 | -6.80 | -6.29 | -5.06 | -2.62 | -2.12 | +0.85 | +2.75 (10.33) |  / 2 | 0.99 | 2/5 | 6.75 | n/n/n | DEAD | 0.33 |
| A2|filt=0|tgt=2|stop=0 | 125 | -12.46 | +0.54 | -0.49 | +0.96 | +1.65 | 26.71 | +0.28 | -0.49 | +0.07 | -5.34 | +0.24 | -0.22 | +0.43 | +0.76 (13.66) |  / 3 | 0.98 | 2/5 | 6.75 | n/n/n | DEAD | 0.33 |
| A2|filt=0|tgt=2|stop=60 | 125 | -3.24 | +1.46 | +0.81 | +0.81 | +3.14 | 24.49 | +0.05 | -0.16 | +0.84 | -1.39 | +0.65 | +0.37 | +0.36 | +1.44 (12.46) |  / 4 | 0.97 | 3/5 | 6.75 | n/n/n | DEAD | 0.33 |
| A2|filt=0|tgt=2|stop=90 | 125 | -11.81 | -1.85 | -1.82 | +3.40 | +5.91 | 26.37 | -2.57 | -2.79 | -2.28 | -5.06 | -0.83 | -0.83 | +1.52 | +2.71 (13.02) |  / 3 | 0.99 | 3/5 | 6.75 | n/n/n | DEAD | 0.33 |
| A2|filt=1|tgt=0|stop=0 | 49 | -10.46 | -1.99 | +0.35 | +4.07 | +8.50 | 40.48 | -2.16 | -3.16 | -2.47 | -2.02 | -0.35 | +0.06 | +0.63 | +1.58 (7.38) | 0.32 / 1 | 0.99 | 3/5 | 7.00 | n/n/n | DEAD | 0.33 |
| A2|filt=1|tgt=0|stop=45 | 49 | +9.54 | +5.34 | +6.93 | +3.18 | +8.98 | 32.11 | +4.87 | +4.95 | +4.64 | +1.84 | +0.93 | +1.21 | +0.49 | +1.67 (5.64) | 0.71 / 3 | 0.89 | 4/5 | 7.00 | Y/n/Y | DEAD | 0.38 |
| A2|filt=1|tgt=0|stop=60 | 49 | +5.47 | -0.58 | +1.84 | +6.93 | +6.62 | 34.63 | -1.04 | -0.96 | -1.24 | +1.06 | -0.10 | +0.32 | +1.07 | +1.23 (6.80) | 0.40 / 2 | 0.99 | 4/5 | 7.00 | n/n/n | DEAD | 0.35 |
| A2|filt=1|tgt=0|stop=90 | 49 | -12.31 | -7.89 | -0.99 | +8.56 | +10.75 | 39.00 | -8.20 | -8.38 | -8.44 | -2.37 | -1.38 | -0.17 | +1.32 | +2.00 (7.44) | 0.17 / 2 | 0.99 | 3/5 | 7.00 | n/n/n | DEAD | 0.33 |
| A2|filt=1|tgt=1|stop=0 | 49 | -21.38 | -10.39 | -5.59 | +7.17 | +10.88 | 35.42 | -10.56 | -11.56 | -10.87 | -4.12 | -1.82 | -0.98 | +1.11 | +2.03 (6.45) | 0.15 / 1 | 0.99 | 3/5 | 7.00 | n/n/n | DEAD | 0.33 |
| A2|filt=1|tgt=1|stop=45 | 49 | -1.39 | -3.06 | +0.99 | +6.21 | +12.14 | 25.81 | -3.53 | -3.44 | -3.75 | -0.27 | -0.54 | +0.17 | +0.96 | +2.26 (4.48) | 0.43 / 2 | 0.99 | 4/5 | 7.00 | n/n/n | DEAD | 0.33 |
| A2|filt=1|tgt=1|stop=60 | 49 | -5.45 | -8.97 | -4.11 | +10.25 | +9.78 | 28.61 | -9.44 | -9.36 | -9.64 | -1.05 | -1.57 | -0.72 | +1.58 | +1.82 (5.37) | 0.18 / 1 | 0.99 | 2/5 | 7.00 | n/n/n | DEAD | 0.33 |
| A2|filt=1|tgt=1|stop=90 | 49 | -23.23 | -16.29 | -7.47 | +9.01 | +13.98 | 33.48 | -16.60 | -16.78 | -16.84 | -4.48 | -2.85 | -1.31 | +1.39 | +2.61 (6.36) | 0.10 / 1 | 0.99 | 3/5 | 7.00 | n/n/n | DEAD | 0.33 |
| A2|filt=1|tgt=2|stop=0 | 49 | -21.38 | -10.39 | -7.16 | +3.94 | +10.48 | 35.42 | -10.56 | -11.56 | -10.87 | -4.12 | -1.82 | -1.25 | +0.61 | +1.95 (6.45) | 0.14 / 1 | 0.99 | 3/5 | 7.00 | n/n/n | DEAD | 0.33 |
| A2|filt=1|tgt=2|stop=45 | 49 | -1.39 | -3.06 | -0.59 | +5.55 | +11.43 | 25.81 | -3.53 | -3.44 | -3.75 | -0.27 | -0.54 | -0.10 | +0.86 | +2.13 (4.48) | 0.37 / 2 | 0.99 | 3/5 | 7.00 | n/n/n | DEAD | 0.33 |
| A2|filt=1|tgt=2|stop=60 | 49 | -5.45 | -8.97 | -5.68 | +9.56 | +9.07 | 28.61 | -9.44 | -9.36 | -9.64 | -1.05 | -1.57 | -0.99 | +1.48 | +1.69 (5.37) | 0.16 / 1 | 0.99 | 2/5 | 7.00 | n/n/n | DEAD | 0.33 |
| A2|filt=1|tgt=2|stop=90 | 49 | -23.23 | -16.29 | -9.04 | +8.32 | +13.27 | 33.48 | -16.60 | -16.78 | -16.84 | -4.48 | -2.85 | -1.58 | +1.29 | +2.47 (6.36) | 0.10 / 1 | 0.99 | 3/5 | 7.00 | n/n/n | DEAD | 0.33 |
| A2|filt=2|tgt=2|stop=90 | 38 | +1.38 | -10.87 | -10.50 | +3.76 | +11.78 | 36.38 | -12.41 | -12.73 | -11.33 | +0.19 | -1.47 | -1.51 | +0.73 | +1.90 (4.35) | 0.26 / 0 | 0.99 | 4/5 | 6.75 | n/n/n | DEAD | 0.34 |
| A3|filt=1|tgt=0|stop=60 | 38 | -19.08 | -2.12 | -6.30 | +2.88 | +0.63 | 31.41 | -2.07 | -6.72 | -2.71 | -2.59 | -0.29 | -0.89 | +0.52 | +0.09 (3.86) | 0.56 / 2 | 0.99 | 3/5 | 7.38 | n/n/n | DEAD | 0.33 |
| A3|filt=1|tgt=0|stop=90 | 38 | -8.11 | -1.40 | -3.53 | +4.29 | +1.45 | 35.72 | -1.36 | -1.71 | -1.80 | -1.10 | -0.19 | -0.50 | +0.78 | +0.22 (4.31) | 0.44 / 1 | 0.99 | 3/5 | 7.38 | n/n/n | DEAD | 0.33 |

Purged 5-fold CV with 1-day embargo over ALL 66 stand-alone cells (cell chosen on the four training folds by mean net pts, scored on the held-out fold): pooled out-of-sample -3.96 pts per trade over 207 trades; fold choices: fold 0 A2|filt=1|tgt=0|stop=90 train +7.2 -> test +3.6 (n 44); fold 1 A1|k=1|filt=0|tgt=0|stop=90 train +10.2 -> test -0.2 (n 29); fold 2 A1|k=1|filt=0|tgt=0|stop=90 train +8.6 -> test +4.6 (n 24); fold 3 A2|filt=1|tgt=1|stop=45 train +11.0 -> test -11.5 (n 55); fold 4 A2|filt=1|tgt=1|stop=90 train +9.4 -> test -8.2 (n 55).

### Table 3 - PART 2 target diagnostic (day-level touch rates, no selection, no cells)

| test | value |
|---|---|
| open above VA: n | 280 |
| open above VA: touches VA edge nearest | 0.65 |
| open above VA: touches POC | 0.43214285714285716 |
| open above VA: touches opposite edge | 0.275 |
| open below VA: n | 203 |
| open below VA: touches VA edge nearest | 0.645320197044335 |
| open below VA: touches POC | 0.43842364532019706 |
| open below VA: touches opposite edge | 0.2955665024630542 |
| prior HIGH POOR dist 0-30pt: n / touched | 15 / 0.87 |
| prior HIGH not poor dist 0-30pt: n / touched | 61 / 0.84 |
| prior HIGH POOR dist 30-60pt: n / touched | 14 / 0.64 |
| prior HIGH not poor dist 30-60pt: n / touched | 65 / 0.71 |
| prior HIGH POOR dist 60-120pt: n / touched | 23 / 0.61 |
| prior HIGH not poor dist 60-120pt: n / touched | 117 / 0.48 |
| prior HIGH POOR dist 120-400pt: n / touched | 20 / 0.05 |
| prior HIGH not poor dist 120-400pt: n / touched | 214 / 0.20 |
| prior LOW POOR dist 0-30pt: n / touched | 4 / 1.00 |
| prior LOW not poor dist 0-30pt: n / touched | 39 / 0.95 |
| prior LOW POOR dist 30-60pt: n / touched | 8 / 0.38 |
| prior LOW not poor dist 30-60pt: n / touched | 53 / 0.70 |
| prior LOW POOR dist 60-120pt: n / touched | 9 / 0.22 |
| prior LOW not poor dist 60-120pt: n / touched | 121 / 0.43 |
| prior LOW POOR dist 120-400pt: n / touched | 17 / 0.12 |
| prior LOW not poor dist 120-400pt: n / touched | 346 / 0.20 |

Reading: a day that opens outside the prior value area touches the nearest VA edge 65% of the time, the POC 43%, the opposite edge only 28-30% (not 80%); a naked prior-day poor high/low is not touched more often than a normal prior high/low at the same distance (counts are small: 15 / 14 / 23 poor highs per distance bucket). The NTZ1 family (prior-day VAH/VAL/POC as POI ahead of the trade, skip/shrink) is already in DEAD_CELLS (25 near hits on the PRF:vah:day spec); no re-target cell is scored in this pass.

## Method notes, gates and what is open

* Trade frame (part 1): composite on the one-convention engine at live lots (K6 2 / P6 7 / U6 4 / H6 4 (2 NY-AM) / M6 2 / A6 1 = engine books KB PE SM HM MV PB), 10,532 kept signals 2023-04..2026-02-06; per contract = net pts per planned lot (engine pnl); N = Native stop 1.28, M = measured per-trade fill cost, LIVE_CAL = join stop 2.45. Only K6 trades in the NY-PM / close sessions at live lots, so ALL = K6 there (identical rows kept visible in the csv, removed from the tables).
* Stack line: the skipped signals are removed on the engine (zone_override), so the blocked-by-position signals are freed exactly as D6 would; delta vs the as-is composite on the same engine, MDE = 2.8 x SE of the paired weekly delta, 12R combined lock column beside. Composite L6M level 41.1k/wk.
* Multiplicity: selection over 421 cells (>= 40 skipped signals) on PRE and X' only; the recent look is OOS for the 36 carried cells; RC/RW/DSR/PBO run over the 36 (RC p of the group 0.54; PBO 0.32; Sidak-cumulative with 3.07M earlier cells). No cell survives Romano-Wolf at 5% (smallest p 0.17).
* Placebos: (1) shuffled days: every state column of a day replaced by a random other day of the same calendar year (prior-day levels re-based to today's prior close), 200 draws, rank = share of draws below the real L6M value; (2) time-shifted IB: IB window moved to 11:00 / 11:30 / 12:00 / 12:30 ET, IB-family states recomputed (plac_ibshift_max in the csv). Stand-alone: A1 prior VA from a random same-year day (200), A2/A3 filter cells ON inventory shuffled across days (200), A2/A3 time-shifted IB (4). Cells without an applicable placebo are not penalised for it (stated).
* Disclosed ordering slip: the dead_lookup of the specs was run AFTER the first scoring pass, not before (the prereg said before). Result: 0 EXACT/NEAR hits for any of the 421 + 66 specs (new spec vocabulary); nearby scored families: NTZ1 (PRF vah/val/poc ahead-of-trade, 3,594 specs matching), EINT2 (e.or60 = IB60 range deciles, e.ongap, e.on), NTE1C (px.loc.ON.sidedloc). DEAD_CELLS +487 rows appended (append_cells; file not rebuilt).
* IB extension at 0.5 / 1 / 2 x IB is used inside A2 targets; the 'IB extension' day-type rows at 11:00 used 0.25 / 0.5 IB (1.0 IB in 30 min is too rare). DT1100='neutral' never occurred (0 signals). One definition change before scoring: the open-in-overnight-range and 10:30-in-IB states are location terciles (the first drafts were constant by construction).
* Capacity: top-5 depth on the side hit at the fire second: median depth 27 contracts, capacity (25% participation) 6-7 NQ contracts for every stand-alone cell - a 5-lot add-on is already at the limit; the live stack trades 10-30 contracts at the same minutes.
* Persistence score = edge_columns.persist_score (family 'regime' for part 1, 'entry structure' for part 3) with z6 from the stack L3M delta; shrunk size from shrink_for (RE-6 formula). All shrunk sizes are 0 (the family shrinkage for a selected edge of z6 < 2 is negative).
* Structural question (MORNING.md): none blocking. The T-SIXTY TOLERANT clause (L6M - PRE) < 100% of L6M is applied literally (it implies PRE > 0), as SIXTY-1 did; TOL-B (clause 5 loosened to PRE > -1.0 x L6M gain) and TOL-nc (clause 5 dropped) are shown beside it, labelled post-hoc; the user has not said which reading he meant; headline = literal TOLERANT.