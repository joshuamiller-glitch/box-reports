# DS3_THL2_C_POLICIES - PROFIT side: walk-forward policies on the order book (L2P, 2026-10-29)
Research only; nothing here is a live recommendation. UNTOUCHED never read (all windows capped 2026-02-06; audit logged in DECISIONS.md). Prereg `l2vast/ds3/prereg/THL2P_prereg.md` sha256 df60233e1ca5c30bf82cc22af60ef57dc63bff1e3607c7e57f0d64b512c80dcf + addendum A1 sha256 16dfaa376277f2417b26609024ac7dce65d7b947862f9e0eb619e53380703be1 (119 cells, frozen before any delta was read). Code `l2vast/ds3/code/l2feat/` (l2p_data, l2p_fit, l2p_fit2, l2p_tab, l2p_score, l2p_report*, l2p_distil, l2p_nightly); outputs `l2vast/ds3/out/thp/wf/l2p/` (cells.parquet, cell_deltas.npy, per_book_session.csv, importance_by_quarter.csv, report_tables*.md).

## Verdict (plain)
**Nothing beats hold-to-bracket on the profit side, with or without the order book.** 0 of 119 cells pass; White reality check over all 119 cells p = 0.34 (PRE), 0.29 (HOLD). 13 cells are positive in both 2026 and the last 6 months (label CANDIDATE-RECENT, gates unchanged) but every one of them has |delta| <= 0.12 pt/trade with MDE 0.06-0.27 (2026 alone is ~5 weeks and ~2,200 trades: MDE 0.5-2.8), fires on 0.1-3% of trades (or, for the optimal-stopping cells, loses to nothing only because random exits lose in 2026), and the hazard cells lose to a RANDOM exit at the same rate (rank 0.00: the MEASURED basis rewards any early market exit because hold-to-bracket carries the 1.4-4.3 pt limit-target correction; a random exit at a 55% rate earns +2.4 pts/trade in PRE, so "positive vs hold" is not evidence). The adaptive variant (re-select the best of the 119 cells on its trailing 6 months, hold if none > 0) earns +0.25 (2026, MDE 2.3), -0.12 (last 6 months, MDE 1.4), +0.03 (HOLD, MDE 1.3), +0.17 (PRE), -0.52 (X): nothing.

**The book at the target / the book at the stop / the tape against me adds -0.32 / -0.24 / -0.28 pts per trade over hold-with-the-path (last 6 months; 95% CI each spans 0, MDE ~0.4), i.e. nothing; the path alone adds -0.20 (last 6 months), +0.03 (HOLD), -0.38 (PRE) pts per trade over hold - also nothing.** (Book at the target = ahead-side wall profile, queue and round-number features; book at the stop = behind side; tape = delta, OFI, sweeps, large prints, VPIN, ES; "adds" = the matched ablation cell with that family minus the path-only cell, GBM, window exp.) Adding the full L2 library to the path (B minus P over 26 matched configurations): last 6 months -0.22 [-0.47,+0.03], HOLD -0.19 [-0.44,+0.07], PRE +0.06 [-0.11,+0.23], 2026 -0.29 [-0.80,+0.22]. Adding tranches 2-4 (B2 minus B, 10 configs): -0.20 [-0.51,+0.12] last 6 months. The book does carry real information (shuffling the L2 columns within the day or lagging them 60 s makes the same models LOSE 0.2-0.7 pt/trade more: e.g. B clf q0.3 PRE +0.16 real vs -0.06 shuffled vs -0.01 lagged), but that information is already priced in the path and is smaller than the 0.995-pt exit cost: it reduces the damage of a wrong exit, it never produces a positive one.

wall_tgt / wall_stop (size AT the bracket levels) are finite and non-trivially visible in 0.1% (target) and 0.0% (stop) of in-profit minutes (19 k of 3.2 M dp1m rows): brackets are 33-60 pts away, the 10 visible mbp-10 levels cover ~2.5 pts. They cannot carry a policy; they enter only through ahead_L1..10 / behind_L1..10 / cum_ahead / cum_behind / maxlv_*. A real wall test needs MBO deep-book at the target price (see DS3_THL2_NEEDS.md).

Feature importance (gain share, B = context + path + L2, regression, 32 monthly re-fits): context ~22%, path ~24%, tape ~20-22%, book state ~12%, book at the stop ~10%, book at the target ~11%; by quarter the shares are stable (tape rises from 16% in 2023-Q3 to 22% in 2026-Q1, book@target falls in the clf from 16% to 9-11%); the top single features of the LAST re-fit are mae_R, rnd100_behind (distance to the next x00 behind), vpin50, vol_tag, atr_ratio, mfe_R, depth10, rnd100_ahead - no wall feature, no imb5/imb10 in the top 20.

Per book / session (see per_book_session.csv, tables below): the only cell families with a sign pattern are session-specific (NY-PM entry session: clf q0.3 +2.1 in 2026 and +0.75 PRE for B, +1.05 PRE for P, but -0.15 / +0.18 last 6 months, 8,185 trades, exit rate 33-36%): the same size in the path-only and the L2 model, so not an L2 effect, and not stable across windows. By book, 2026 gains of +0.7..+1.5 in PB/PE/ST/MV cells flip sign in the last 6 months.

Publication: **THP_POLICY profit side stays EMPTY** (hold-to-bracket). The nightly script `l2vast/ds3/code/l2feat/l2p_nightly.py` (single command, `python3 l2p_nightly.py [--asof YYYYMMDD]`) re-fits the B-set classifier on the trailing 12 months, applies it to the last 60 label days out of time, gates on delta > 0 and >= 30 fires, distils to <= 12 `profit * * <conds> take` rules over imb5/imb10/delta60/wall_tgt/wall_stop/pct/mins/secs_ext/dd/vel30/eff120 and writes autopilot/THP_POLICY_L2_PROFIT.txt (today: out-of-time delta -0.047, 207 fires -> header only, no rules). Distillation of the recent-positive teachers (L|exp|haz d0.05, B|3m|haz d0.05, P|3m|haz d0.05) into D6 features yields 0 rules (the hazard teachers fire on 1-3% of rows from rare, high-dimensional states); B|exp|clf q0.3 distils to 1 rule (`mins > 949.5 pct <= 0.494 take`: 18% of the teacher's L6M gain, still negative). Candidate files: wf/l2p/policy_candidate_*.txt. No feature outside the D6 live set is needed (nothing won).

Tables below are generated by l2p_report.py / l2p_report2.py (recent windows first: 2026 ~5.4 weeks, last 6 months 2025-08..2026-02-06, HOLD, PRE, X). Mean pts/trade vs hold-to-bracket, MEASURED fills, trades without a fire count as 0, 95% day-cluster CI, MDE = 2.8 SE, $/wk at live lots (LOTS of DS3_THP_B_RULES), exit rate and the mean of random exits at the same rate and the rank of the real cell among them.

## TOP 15 cells ranked by last-6-months, HOLD tie-break (recent first; mean pts/trade vs hold-to-bracket, MEASURED, 95% CI day-cluster, MDE, $/wk at live lots)

| cell                | 2026 (~5.4 wk)                            | last 6 mo                                | HOLD                                      | PRE                                       | X                                         |   exit rate L6M |   random-exit mean L6M |   rank vs random |
|:--------------------|:------------------------------------------|:-----------------------------------------|:------------------------------------------|:------------------------------------------|:------------------------------------------|----------------:|-----------------------:|-----------------:|
| P|3m|haz|d0.05      | +0.30 [-0.06,+0.66] MDE 0.51 ($+19254/wk) | +0.12 [-0.07,+0.31] MDE 0.27 ($+5837/wk) | +0.12 [-0.05,+0.30] MDE 0.25 ($+5414/wk)  | -0.11 [-0.25,+0.04] MDE 0.21 ($-5569/wk)  | -0.01 [-0.13,+0.12] MDE 0.18 ($+121/wk)   |           0.014 |                   0.25 |                0 |
| L|exp|dp|m0         | +0.27 [-0.12,+0.66] MDE 0.56 ($+18512/wk) | +0.12 [-0.03,+0.27] MDE 0.22 ($+7511/wk) | +0.11 [-0.03,+0.24] MDE 0.20 ($+6220/wk)  | -0.04 [-0.26,+0.19] MDE 0.32 ($-1375/wk)  | -0.92 [-2.92,+1.08] MDE 2.86 ($-34913/wk) |           0.019 |                  -0.24 |                1 |
| P|exp|dp|m0         | +0.70 [-0.22,+1.63] MDE 1.32 ($+36958/wk) | +0.12 [-0.46,+0.70] MDE 0.83 ($+5541/wk) | +0.20 [-0.36,+0.76] MDE 0.80 ($+11552/wk) | -0.20 [-0.68,+0.28] MDE 0.68 ($-10286/wk) | -1.18 [-3.17,+0.82] MDE 2.85 ($-43589/wk) |           0.29  |                  -5.21 |                1 |
| B|exp|dp|m1         | +0.09 [-0.04,+0.23] MDE 0.19 ($+5775/wk)  | +0.10 [-0.06,+0.26] MDE 0.22 ($+5227/wk) | +0.09 [-0.05,+0.23] MDE 0.20 ($+4410/wk)  | -0.00 [-0.09,+0.08] MDE 0.12 ($+217/wk)   | -1.02 [-1.83,-0.20] MDE 1.17 ($-34767/wk) |           0.024 |                  -0.48 |                1 |
| B|3m|haz|d0.05      | -0.03 [-0.27,+0.22] MDE 0.35 ($-1265/wk)  | +0.10 [-0.04,+0.23] MDE 0.19 ($+5730/wk) | +0.08 [-0.04,+0.21] MDE 0.18 ($+4501/wk)  | +0.09 [-0.05,+0.23] MDE 0.20 ($+4975/wk)  | +0.04 [-0.05,+0.14] MDE 0.14 ($+1695/wk)  |           0.007 |                   0.17 |                0 |
| L|exp|haz|d0.05     | +0.30 [-0.09,+0.69] MDE 0.56 ($+18138/wk) | +0.09 [-0.11,+0.29] MDE 0.29 ($+3521/wk) | +0.10 [-0.08,+0.29] MDE 0.27 ($+4803/wk)  | +0.01 [-0.12,+0.13] MDE 0.17 ($-206/wk)   | -0.06 [-0.16,+0.04] MDE 0.14 ($-1918/wk)  |           0.021 |                   0.34 |                0 |
| P|3m|haz|d0.15      | -0.01 [-0.15,+0.14] MDE 0.20 ($-510/wk)   | +0.05 [-0.03,+0.14] MDE 0.12 ($+2975/wk) | +0.02 [-0.06,+0.10] MDE 0.12 ($+1388/wk)  | -0.07 [-0.13,-0.01] MDE 0.08 ($-3846/wk)  | +0.01 [-0.01,+0.02] MDE 0.02 ($+209/wk)   |           0.003 |                   0.07 |                0 |
| L|3m|haz|d0.15      | +0.06 [-0.04,+0.17] MDE 0.15 ($+6128/wk)  | +0.05 [+0.01,+0.09] MDE 0.06 ($+3355/wk) | +0.04 [+0.01,+0.08] MDE 0.05 ($+2831/wk)  | +0.00 [-0.04,+0.05] MDE 0.07 ($+204/wk)   | +0.00 [+0.00,+0.00] MDE 0.00 ($+0/wk)     |           0.001 |                   0.06 |                0 |
| B|3m|haz|d0.15      | +0.01 [-0.10,+0.12] MDE 0.15 ($+1778/wk)  | +0.04 [-0.03,+0.11] MDE 0.09 ($+2619/wk) | +0.04 [-0.02,+0.10] MDE 0.09 ($+2210/wk)  | +0.02 [-0.05,+0.08] MDE 0.09 ($+1059/wk)  | +0.00 [+0.00,+0.00] MDE 0.00 ($+0/wk)     |           0.002 |                   0.06 |                0 |
| P|exp|reg|m1|tight6 | +0.88 [-1.08,+2.83] MDE 2.80 ($+47559/wk) | +0.04 [-1.25,+1.33] MDE 1.84 ($-1635/wk) | +0.44 [-0.84,+1.72] MDE 1.82 ($+22469/wk) | -0.49 [-1.47,+0.50] MDE 1.41 ($-25544/wk) | -0.76 [-2.73,+1.21] MDE 2.81 ($-27281/wk) |           0.528 |                   1.47 |                0 |
| B|exp|haz|d0.05     | +0.35 [-0.10,+0.79] MDE 0.64 ($+24430/wk) | +0.03 [-0.16,+0.22] MDE 0.27 ($-291/wk)  | +0.04 [-0.14,+0.21] MDE 0.25 ($+381/wk)   | -0.03 [-0.15,+0.10] MDE 0.18 ($-1801/wk)  | +0.02 [-0.04,+0.09] MDE 0.09 ($+986/wk)   |           0.019 |                   0.26 |                0 |
| P|exp|haz|d0.05     | -0.12 [-0.58,+0.34] MDE 0.66 ($-13398/wk) | +0.03 [-0.21,+0.26] MDE 0.34 ($-274/wk)  | +0.02 [-0.20,+0.23] MDE 0.31 ($-610/wk)   | -0.04 [-0.16,+0.07] MDE 0.17 ($-1878/wk)  | -0.06 [-0.19,+0.06] MDE 0.18 ($-2522/wk)  |           0.027 |                   0.34 |                0 |
| B|exp|haz|d0.15     | +0.20 [-0.00,+0.40] MDE 0.29 ($+13234/wk) | +0.03 [-0.09,+0.14] MDE 0.16 ($+1105/wk) | +0.02 [-0.08,+0.12] MDE 0.15 ($+582/wk)   | -0.02 [-0.07,+0.03] MDE 0.07 ($-1310/wk)  | -0.00 [-0.01,+0.01] MDE 0.01 ($-98/wk)    |           0.005 |                   0.09 |                0 |
| L|3m|haz|d0.05      | +0.10 [-0.18,+0.38] MDE 0.40 ($+9148/wk)  | +0.03 [-0.08,+0.13] MDE 0.15 ($+1707/wk) | +0.02 [-0.07,+0.12] MDE 0.14 ($+1441/wk)  | +0.05 [-0.08,+0.19] MDE 0.20 ($+3779/wk)  | +0.04 [-0.09,+0.18] MDE 0.19 ($+2222/wk)  |           0.006 |                   0.09 |                0 |
| L|exp|haz|d0.15     | +0.11 [-0.07,+0.29] MDE 0.26 ($+9068/wk)  | +0.02 [-0.06,+0.11] MDE 0.12 ($+1790/wk) | +0.03 [-0.05,+0.11] MDE 0.11 ($+2270/wk)  | +0.03 [-0.02,+0.07] MDE 0.06 ($+1388/wk)  | -0.00 [-0.01,+0.00] MDE 0.01 ($-142/wk)   |           0.006 |                   0.09 |                0 |

## Feature set x model, mean over its cells (pts/trade vs hold)

| set   | model       |   n |   Y2026 |    L6M |   HOLD |    PRE |      X |   best_L6M |   best_PRE |
|:------|:------------|----:|--------:|-------:|-------:|-------:|-------:|-----------:|-----------:|
| B     | gbm_clf     |   4 |  -0.324 | -0.706 | -0.599 |  0.051 | -0.893 |     -0.206 |      0.162 |
| B     | gbm_reg     |   6 |  -0.837 | -1.056 | -0.689 | -0.679 | -1.687 |     -0.707 |     -0.466 |
| B     | gbm_tighten |   4 |  -0.339 | -0.882 | -0.547 | -0.257 | -1.448 |     -0.629 |     -0.113 |
| B     | hazard      |   4 |   0.132 |  0.048 |  0.043 |  0.015 |  0.017 |      0.098 |      0.088 |
| B     | online      |   2 |  -1.099 | -1.258 | -0.695 | -0.778 | -1.789 |     -1.258 |     -0.778 |
| B     | optstop     |   4 |   0.603 | -0.187 | -0.016 | -0.276 | -0.984 |      0.099 |     -0.004 |
| B     | table       |   4 |  -1.418 | -1.344 | -0.989 | -0.792 | -1.756 |     -1.272 |     -0.417 |
| B2    | gbm_clf     |   4 |  -0.352 | -0.865 | -0.79  | -0.069 | -1.001 |     -0.241 |      0.178 |
| B2    | gbm_reg     |   6 |  -0.738 | -1.278 | -0.854 | -0.741 | -1.859 |     -0.958 |     -0.572 |
| L     | gbm_clf     |   4 |  -0.314 | -0.822 | -0.675 |  0.036 | -1.066 |     -0.116 |      0.16  |
| L     | gbm_reg     |   6 |  -1.2   | -1.177 | -0.811 | -0.745 | -1.992 |     -0.652 |     -0.571 |
| L     | gbm_tighten |   4 |  -0.665 | -1.013 | -0.678 | -0.297 | -1.767 |     -0.831 |     -0.223 |
| L     | hazard      |   4 |   0.142 |  0.046 |  0.051 |  0.022 | -0.005 |      0.087 |      0.055 |
| L     | online      |   2 |  -1.642 | -1.307 | -0.906 | -0.88  | -1.97  |     -1.307 |     -0.88  |
| L     | optstop     |   4 |   0.324 | -0.099 | -0.004 | -0.214 | -0.63  |      0.119 |      0     |
| L     | table       |   4 |  -1.202 | -1.223 | -0.841 | -0.844 | -1.66  |     -0.9   |     -0.593 |
| L2x   | gbm_clf     |   2 |  -0.007 | -0.34  | -0.24  |  0.074 | -1.199 |     -0.238 |      0.103 |
| L2x   | gbm_reg     |   3 |  -0.092 | -1.066 | -0.659 | -0.547 | -2.027 |     -1.018 |     -0.451 |
| P     | gbm_clf     |   4 |   0.01  | -0.441 | -0.383 |  0.027 | -0.645 |     -0.043 |      0.265 |
| P     | gbm_reg     |   6 |  -0.265 | -0.855 | -0.502 | -0.848 | -1.289 |     -0.072 |     -0.663 |
| P     | gbm_tighten |   4 |   0.2   | -0.594 | -0.267 | -0.494 | -1.136 |      0.035 |     -0.442 |
| P     | hazard      |   4 |   0.058 |  0.055 |  0.043 | -0.049 | -0.014 |      0.119 |      0.026 |
| P     | online      |   2 |  -1.81  | -1.291 | -0.851 | -1.089 | -1.287 |     -1.275 |     -1.086 |
| P     | optstop     |   4 |   0.395 | -0.002 |  0.119 | -0.105 | -1.078 |      0.117 |      0.05  |
| P     | table       |   4 |  -0.99  | -0.966 | -0.687 | -0.77  | -2.068 |     -0.57  |     -0.607 |
| PA    | gbm_clf     |   2 |   0.124 | -0.264 | -0.163 | -0.014 | -0.36  |     -0.142 |      0.121 |
| PA    | gbm_reg     |   3 |   0.546 | -0.671 | -0.197 | -1.158 | -0.759 |     -0.638 |     -1.053 |
| PB    | gbm_clf     |   2 |   0.123 | -0.254 | -0.196 | -0.047 | -0.323 |     -0.145 |      0.081 |
| PB    | gbm_reg     |   3 |   0.02  | -0.534 | -0.18  | -1.091 | -1.066 |     -0.354 |     -0.948 |
| PS    | gbm_clf     |   2 |   0.046 | -0.213 | -0.137 |  0.048 | -0.509 |     -0.142 |      0.174 |
| PS    | gbm_reg     |   3 |  -0.357 | -0.636 | -0.204 | -1.117 | -0.99  |     -0.469 |     -1.018 |
| PT    | gbm_clf     |   2 |  -0.01  | -0.243 | -0.174 |  0.238 | -0.373 |     -0.134 |      0.33  |
| PT    | gbm_reg     |   3 |  -0.405 | -0.62  | -0.35  | -0.973 | -1.682 |     -0.494 |     -0.962 |

## L2 contribution = (L2+path) - (path), matched configurations; mean over matched cells and the best/worst pair (pts/trade, day-cluster CI of the pooled difference)

* B-P (26 matched cells, mean difference): Y2026 -0.289 [-0.801,+0.224]; L6M -0.219 [-0.470,+0.032]; HOLD -0.187 [-0.440,+0.067]; PRE +0.059 [-0.107,+0.225]; X -0.111 [-0.392,+0.170]

* L-P (26 matched cells, mean difference): Y2026 -0.429 [-0.891,+0.032]; L6M -0.253 [-0.499,-0.007]; HOLD -0.221 [-0.474,+0.032]; PRE +0.038 [-0.131,+0.207]; X -0.191 [-0.539,+0.157]

* B2-B (tranches 2-4 added) (10 matched cells, mean difference): Y2026 +0.048 [-0.593,+0.689]; L6M -0.196 [-0.511,+0.118]; HOLD -0.175 [-0.477,+0.126]; PRE -0.085 [-0.339,+0.168]; X -0.147 [-0.578,+0.284]

## Ablation (window exp, GBM): book family added to path, minus path alone (matched reg m0,1,2 and clf q.3,.4), mean pts/trade

* book ahead = toward the TARGET (profile, walls, queue): Y2026 +0.103 [-0.595,+0.800]; L6M -0.322 [-0.660,+0.015]; HOLD -0.258 [-0.597,+0.081]; PRE -0.277 [-0.514,-0.041]; X +0.102 [-0.333,+0.537]

* book behind = toward the STOP (profile, walls, queue): Y2026 -0.214 [-1.006,+0.579]; L6M -0.235 [-0.626,+0.155]; HOLD -0.261 [-0.643,+0.121]; PRE -0.250 [-0.486,-0.014]; X -0.068 [-0.507,+0.372]

* tape against me (delta, OFI, sweeps, big prints, VPIN, ES): Y2026 -0.522 [-1.357,+0.312]; L6M -0.282 [-0.676,+0.111]; HOLD -0.354 [-0.732,+0.024]; PRE -0.065 [-0.322,+0.192]; X -0.457 [-0.922,+0.008]

* book state (imbalance, depth, spread, micro, pulled/added): Y2026 -0.471 [-1.284,+0.342]; L6M -0.281 [-0.657,+0.096]; HOLD -0.252 [-0.623,+0.119]; PRE -0.228 [-0.476,+0.021]; X -0.097 [-0.430,+0.236]

* path alone (P, exp, mean of its 13 cells) vs hold: Y2026 +0.102; L6M -0.199; HOLD +0.029; PRE -0.379; X -0.832

## Placebos (apply-only) on L/B exp take cells: real vs shuffled-L2-within-day vs 60-s-lagged L2, mean pts/trade

| id                   |   PRE_mean |   PRE_plc_shuf |   PRE_plc_lag |   L6M_mean |   L6M_plc_shuf |   L6M_plc_lag |   HOLD_mean |   HOLD_plc_shuf |   HOLD_plc_lag |
|:---------------------|-----------:|---------------:|--------------:|-----------:|---------------:|--------------:|------------:|----------------:|---------------:|
| L|exp|clf|q0.3       |      0.16  |         -0.272 |        -0.4   |     -0.116 |         -0.341 |        -0.502 |      -0.05  |          -0.253 |         -0.38  |
| L|exp|clf|q0.4       |      0.095 |         -0.407 |        -0.759 |     -0.206 |         -0.235 |        -0.687 |      -0.051 |          -0.011 |         -0.411 |
| B|exp|clf|q0.3       |      0.162 |         -0.06  |        -0.009 |     -0.206 |         -0.223 |        -0.609 |      -0.127 |          -0.15  |         -0.492 |
| B|exp|clf|q0.4       |     -0.13  |         -0.505 |        -0.695 |     -0.31  |         -0.411 |        -0.721 |      -0.314 |          -0.13  |         -0.608 |
| B|exp|reg|m1|tight6  |     -0.427 |        nan     |       nan     |     -0.629 |        nan     |       nan     |      -0.262 |         nan     |        nan     |
| L|exp|reg|m2         |     -0.61  |         -1.059 |        -0.883 |     -0.652 |         -1.373 |        -1.052 |      -0.379 |          -0.825 |         -0.535 |
| B|exp|reg|m1         |     -0.751 |         -1.132 |        -0.919 |     -0.707 |         -1.489 |        -0.979 |      -0.355 |          -0.963 |         -0.428 |
| B|exp|reg|m2         |     -0.739 |         -1.039 |        -0.921 |     -0.709 |         -1.326 |        -0.8   |      -0.344 |          -0.841 |         -0.209 |
| B|exp|reg|m0         |     -1.031 |         -1.157 |        -0.968 |     -0.733 |         -1.589 |        -1.174 |      -0.387 |          -1.04  |         -0.641 |
| B|exp|reg|m1|tight10 |     -0.372 |        nan     |       nan     |     -0.759 |        nan     |       nan     |      -0.434 |         nan     |        nan     |
| L|exp|reg|m1|tight6  |     -0.393 |        nan     |       nan     |     -0.831 |        nan     |       nan     |      -0.482 |         nan     |        nan     |
| L|exp|reg|m1|tight10 |     -0.306 |        nan     |       nan     |     -0.873 |        nan     |       nan     |      -0.564 |         nan     |        nan     |
| L|exp|reg|m1         |     -0.823 |         -1.182 |        -0.868 |     -1.033 |         -1.513 |        -1.422 |      -0.647 |          -0.974 |         -0.887 |
| L|exp|reg|m0         |     -0.914 |         -1.257 |        -1.025 |     -1.056 |         -1.695 |        -1.557 |      -0.683 |          -1.126 |         -0.993 |
## Importance by quarter (share of gain over monthly re-fits, B=context+path+L2, window exp)

| model   | q       |   context |   path |   book state |   book@stop (behind) |   book@target (ahead) |   tape |
|:--------|:--------|----------:|-------:|-------------:|---------------------:|----------------------:|-------:|
| clf     | 2023-Q3 |     0.283 |  0.252 |        0.085 |                0.109 |                 0.156 |  0.115 |
| clf     | 2023-Q4 |     0.306 |  0.232 |        0.086 |                0.083 |                 0.153 |  0.14  |
| clf     | 2024-Q1 |     0.311 |  0.227 |        0.09  |                0.075 |                 0.167 |  0.131 |
| clf     | 2024-Q2 |     0.319 |  0.264 |        0.091 |                0.071 |                 0.137 |  0.12  |
| clf     | 2024-Q3 |     0.339 |  0.27  |        0.088 |                0.063 |                 0.119 |  0.12  |
| clf     | 2024-Q4 |     0.362 |  0.257 |        0.088 |                0.066 |                 0.107 |  0.12  |
| clf     | 2025-Q1 |     0.34  |  0.281 |        0.103 |                0.058 |                 0.098 |  0.12  |
| clf     | 2025-Q2 |     0.335 |  0.293 |        0.109 |                0.058 |                 0.091 |  0.114 |
| clf     | 2025-Q3 |     0.359 |  0.289 |        0.105 |                0.055 |                 0.087 |  0.106 |
| clf     | 2025-Q4 |     0.368 |  0.279 |        0.098 |                0.054 |                 0.096 |  0.104 |
| clf     | 2026-Q1 |     0.381 |  0.252 |        0.1   |                0.051 |                 0.114 |  0.102 |
| reg     | 2023-Q3 |     0.252 |  0.249 |        0.108 |                0.121 |                 0.114 |  0.157 |
| reg     | 2023-Q4 |     0.253 |  0.234 |        0.102 |                0.106 |                 0.105 |  0.2   |
| reg     | 2024-Q1 |     0.227 |  0.243 |        0.121 |                0.089 |                 0.112 |  0.208 |
| reg     | 2024-Q2 |     0.22  |  0.257 |        0.118 |                0.093 |                 0.113 |  0.2   |
| reg     | 2024-Q3 |     0.222 |  0.251 |        0.116 |                0.094 |                 0.118 |  0.198 |
| reg     | 2024-Q4 |     0.23  |  0.247 |        0.116 |                0.104 |                 0.106 |  0.197 |
| reg     | 2025-Q1 |     0.222 |  0.244 |        0.121 |                0.099 |                 0.108 |  0.206 |
| reg     | 2025-Q2 |     0.218 |  0.242 |        0.122 |                0.106 |                 0.107 |  0.205 |
| reg     | 2025-Q3 |     0.209 |  0.242 |        0.121 |                0.111 |                 0.103 |  0.214 |
| reg     | 2025-Q4 |     0.211 |  0.235 |        0.124 |                0.1   |                 0.116 |  0.214 |
| reg     | 2026-Q1 |     0.214 |  0.22  |        0.13  |                0.106 |                 0.108 |  0.223 |

## LAST re-fit in full (refit 2026-02 = applied to 2026-02-01..02-06): top 20 features, GBM regression of remaining pts, set B, window exp

| feature             |   gain share | family              |
|:--------------------|-------------:|:--------------------|
| mae_R               |       0.0679 | path                |
| rnd100_behind       |       0.0553 | book@stop (behind)  |
| vpin50              |       0.0552 | tape                |
| vol_tag             |       0.0511 | context             |
| atr_ratio           |       0.0486 | path                |
| mfe_R               |       0.0485 | path                |
| depth10             |       0.0458 | book state          |
| rnd100_ahead        |       0.0443 | book@target (ahead) |
| mod_sin             |       0.0355 | context             |
| side                |       0.0354 | context             |
| sec_since_mfe       |       0.0332 | path                |
| depth_rel           |       0.0322 | book state          |
| mod_cos             |       0.0304 | context             |
| mins                |       0.0268 | context             |
| svpin50             |       0.0229 | tape                |
| es_imb10            |       0.0216 | tape                |
| es_imb5             |       0.0185 | tape                |
| t_since_big_with    |       0.0177 | tape                |
| es_ofi5_30          |       0.0168 | tape                |
| t_since_big_against |       0.0151 | tape                |

Top 8 by quarter (reg): 2023-Q3 m9: mae_R,vol_tag,mfe_R,rnd100_ahead; 2023-Q4 m12: mae_R,mfe_R,side,rnd100_ahead; 2024-Q1 m3: mae_R,mfe_R,rnd100_ahead,side; 2024-Q2 m6: mae_R,rnd100_ahead,mfe_R,side; 2024-Q3 m9: mae_R,mfe_R,rnd100_ahead,mod_cos; 2024-Q4 m12: mae_R,atr_ratio,mfe_R,mod_cos; 2025-Q1 m3: mae_R,mfe_R,rnd100_ahead,atr_ratio; 2025-Q2 m6: mae_R,mfe_R,rnd100_ahead,vpin50; 2025-Q3 m9: mae_R,mfe_R,rnd100_behind,vpin50; 2025-Q4 m12: mae_R,rnd100_behind,vpin50,atr_ratio

## Walk-forward re-selection over all 119 prereg cells (best trailing-6-month cell, hold if none > 0), applied to the next month

| span   |     n |   mean |     lo |    hi |   mde |    usd_wk |   exit_rate |
|:-------|------:|-------:|-------:|------:|------:|----------:|------------:|
| Y2026  |  2229 |  0.251 | -1.336 | 1.838 | 2.268 |   9041.5  |       0.311 |
| L6M    |  9743 | -0.115 | -1.07  | 0.84  | 1.364 |  -9218.91 |       0.282 |
| HOLD   | 10805 |  0.031 | -0.857 | 0.919 | 1.268 |   1002.96 |       0.275 |
| PRE    | 24654 |  0.168 | -0.198 | 0.533 | 0.522 |   9094.89 |       0.091 |
| X      |  6487 | -0.516 | -1.155 | 0.123 | 0.913 | -18456.1  |       0.06  |

Chosen cell by quarter: 2024-01: PA|exp|clf|q0.4; 2024-04: PT|exp|clf|q0.3; 2024-07: B|exp|haz|d0.05; 2024-10: PT|exp|clf|q0.3; 2025-01: PT|exp|clf|q0.3; 2025-04: B|3m|clf|q0.4; 2025-07: L|exp|clf|q0.4; 2025-10: PT|exp|clf|q0.4; 2026-01: P|exp|reg|m1|tight6

LAST re-selection (applies to 2026-02): ('P|3m|haz|d0.05', 0.133)

## Per book / session (cells: top-recent, B hazard 3m, B clf q.3, P clf q.3)

| cell           | by      | key    |     n |   Y2026 |    L6M |    PRE |   exit_rate |
|:---------------|:--------|:-------|------:|--------:|-------:|-------:|------------:|
| P|3m|haz|d0.05 | book    | DN     |  3074 |   0.404 | -0.249 | -0.063 |       0.016 |
| P|3m|haz|d0.05 | book    | HM     |  3914 |  -0.078 | -0.029 |  0.142 |       0.016 |
| P|3m|haz|d0.05 | book    | KB     |  5232 |   0.337 |  0.351 | -0.08  |       0.024 |
| P|3m|haz|d0.05 | book    | MA     |  1935 |   0     |  0.028 | -0.049 |       0.012 |
| P|3m|haz|d0.05 | book    | MV     |  4907 |  -0.119 |  0.024 | -0.257 |       0.017 |
| P|3m|haz|d0.05 | book    | PB     |  3821 |   0.671 |  0.025 | -0.261 |       0.02  |
| P|3m|haz|d0.05 | book    | PE     |  5087 |   0.921 |  0.236 | -0.219 |       0.019 |
| P|3m|haz|d0.05 | book    | SM     |  1587 |   0.301 |  0.347 | -0.237 |       0.02  |
| P|3m|haz|d0.05 | book    | ST     |  5119 |   0.702 |  0.354 | -0.053 |       0.02  |
| P|3m|haz|d0.05 | book    | WT     |  7270 |  -0.119 |  0.013 | -0.029 |       0.007 |
| P|3m|haz|d0.05 | session | asia   | 10977 |   0.098 |  0.05  | -0.02  |       0.004 |
| P|3m|haz|d0.05 | session | london |  8627 |   0.268 |  0.09  |  0.039 |       0.016 |
| P|3m|haz|d0.05 | session | nyam   | 11581 |   0.419 |  0.061 | -0.051 |       0.027 |
| P|3m|haz|d0.05 | session | nypm   |  8185 |  -0.265 | -0.171 | -0.175 |       0.009 |
| P|3m|haz|d0.05 | session | pre    |  2444 |   2.718 |  1.974 | -0.996 |       0.059 |
| B|3m|haz|d0.05 | book    | DN     |  3074 |   0     |  0.125 | -0.121 |       0.015 |
| B|3m|haz|d0.05 | book    | HM     |  3914 |   0.051 |  0.09  |  0.209 |       0.012 |
| B|3m|haz|d0.05 | book    | KB     |  5232 |   0.051 |  0.15  | -0.024 |       0.013 |
| B|3m|haz|d0.05 | book    | MA     |  1935 |   0     | -0.136 |  0.43  |       0.016 |
| B|3m|haz|d0.05 | book    | MV     |  4907 |   0.229 |  0.268 | -0.136 |       0.014 |
| B|3m|haz|d0.05 | book    | PB     |  3821 |  -0.283 | -0.071 |  0.226 |       0.013 |
| B|3m|haz|d0.05 | book    | PE     |  5087 |  -0.198 |  0.12  |  0.258 |       0.014 |
| B|3m|haz|d0.05 | book    | SM     |  1587 |   0     |  0     |  0.006 |       0.013 |
| B|3m|haz|d0.05 | book    | ST     |  5119 |  -0.026 |  0.14  |  0.203 |       0.016 |
| B|3m|haz|d0.05 | book    | WT     |  7270 |  -0.072 |  0.053 | -0     |       0.002 |
| B|3m|haz|d0.05 | session | asia   | 10977 |   0     |  0.018 |  0.039 |       0.001 |
| B|3m|haz|d0.05 | session | london |  8627 |   0.369 |  0.286 |  0.005 |       0.008 |
| B|3m|haz|d0.05 | session | nyam   | 11581 |  -0.33  |  0.036 |  0.249 |       0.02  |
| B|3m|haz|d0.05 | session | nypm   |  8185 |  -0.161 |  0.046 |  0.153 |       0.015 |
| B|3m|haz|d0.05 | session | pre    |  2444 |   0.155 |  0.29  | -0.327 |       0.03  |
| B|exp|clf|q0.3 | book    | DN     |  3074 |   0.662 | -0.547 |  0.52  |       0.116 |
| B|exp|clf|q0.3 | book    | HM     |  3914 |  -0.427 | -0.141 |  0.136 |       0.133 |
| B|exp|clf|q0.3 | book    | KB     |  5232 |   0.269 | -0.163 | -0.002 |       0.11  |
| B|exp|clf|q0.3 | book    | MA     |  1935 |   1.051 | -0.857 | -0.311 |       0.136 |
| B|exp|clf|q0.3 | book    | MV     |  4907 |   0.445 | -0.219 |  0.176 |       0.119 |
| B|exp|clf|q0.3 | book    | PB     |  3821 |   1.489 | -0.343 |  0.202 |       0.134 |
| B|exp|clf|q0.3 | book    | PE     |  5087 |   1.012 | -0.203 |  0.314 |       0.121 |
| B|exp|clf|q0.3 | book    | SM     |  1587 |  -0.194 | -0.43  | -0.249 |       0.118 |
| B|exp|clf|q0.3 | book    | ST     |  5119 |  -0.247 | -0.212 |  0.267 |       0.113 |
| B|exp|clf|q0.3 | book    | WT     |  7270 |   0.008 |  0.142 |  0.14  |       0.04  |
| B|exp|clf|q0.3 | session | asia   | 10977 |   0     | -0.4   | -0.226 |       0.072 |
| B|exp|clf|q0.3 | session | london |  8627 |   0     | -0.037 |  0.04  |       0.014 |
| B|exp|clf|q0.3 | session | nyam   | 11581 |   0.062 | -0.201 |  0.162 |       0.068 |
| B|exp|clf|q0.3 | session | nypm   |  8185 |   2.144 | -0.152 |  0.748 |       0.326 |
| B|exp|clf|q0.3 | session | pre    |  2444 |   0     | -0.026 | -0.069 |       0.012 |
| P|exp|clf|q0.3 | book    | DN     |  3074 |   0.604 | -0.111 |  0.644 |       0.121 |
| P|exp|clf|q0.3 | book    | HM     |  3914 |  -0.37  | -0.027 |  0.571 |       0.135 |
| P|exp|clf|q0.3 | book    | KB     |  5232 |  -0.03  | -0.202 |  0.028 |       0.122 |
| P|exp|clf|q0.3 | book    | MA     |  1935 |   0.592 | -0.919 | -0.052 |       0.131 |
| P|exp|clf|q0.3 | book    | MV     |  4907 |   0.485 | -0.06  |  0.407 |       0.125 |
| P|exp|clf|q0.3 | book    | PB     |  3821 |   1.323 | -0.129 |  0.104 |       0.137 |
| P|exp|clf|q0.3 | book    | PE     |  5087 |   1.145 |  0.154 |  0.47  |       0.128 |
| P|exp|clf|q0.3 | book    | SM     |  1587 |  -0.686 | -0.222 | -0.218 |       0.113 |
| P|exp|clf|q0.3 | book    | ST     |  5119 |  -0.435 |  0.058 |  0.182 |       0.122 |
| P|exp|clf|q0.3 | book    | WT     |  7270 |   0.195 |  0.178 |  0.199 |       0.043 |
| P|exp|clf|q0.3 | session | asia   | 10977 |   0     |  0.041 |  0.016 |       0.058 |
| P|exp|clf|q0.3 | session | london |  8627 |   0     |  0.015 |  0.021 |       0.014 |
| P|exp|clf|q0.3 | session | nyam   | 11581 |   0.054 | -0.181 |  0.065 |       0.073 |
| P|exp|clf|q0.3 | session | nypm   |  8185 |   2.142 |  0.181 |  1.046 |       0.362 |
| P|exp|clf|q0.3 | session | pre    |  2444 |   0     | -0.35  |  0.009 |       0.011 |