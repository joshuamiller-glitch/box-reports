# DS3_ZONES_3_NOISE - the maxDD NOISE BAND for the whole ZONES-3 program (Z3, 2026-11-02 ~03:00Z). INTERIM, ASSUMED BASE (D7 v1.3-assumed, lock 12R, N fills); the band is base-specific and is recomputed on V13X when it is announced. Research only, no PASS claims.

## The rule (all agents)
**A drawdown cut counts only if it exceeds the noise band of its window in L6M AND in at least one of PRE / X' (same sign, cut > band). Cuts inside the band are labelled NOISE. The band for a cell is the 95th percentile of |maxDD change| produced by an information-free perturbation of the same size (rows touched): use the row of the table below nearest to the number of rows the cell changes (a unit of 1,000-2,000 rows -> "flip 5.0" or "flip 2.0"; a one-line screen of ~500 rows -> "flip 2.0"; a handful of rows -> "drop 10/30"). When unsure use "flip 2.0" (conservative on the small side, lenient on the large side). A cell must also keep the robustness standard (ONE-WEEK, bootstrap, placebo ranks); passing the band is necessary, not sufficient.**

## What was perturbed (information-free)
Base = the shipped composite on D7 v1.3-assumed (six core books, live11 lots, U7, gated take lines, 12R lock). Live candidate rows = 25,771 (rows with lots > 0). Perturbation types: DROP k = 1, 3, 10, 30 random live rows (extra_skip); FLIP p = 0.5, 1, 2, 5 % of the live rows to HALF lots (extra_mult 0.5), the size of a zone action. Draws are round-robin by type: n per type below (interim; the run continues to 300 per type, shards in `out/zones3/s3_v13/noise_lock12_*.pkl`, `noise_an.py` recomputes). NOT done yet: lock-off frame, the one-day lock-reset shift, V13X.
n draws per type: drop 1 30, drop 3 28, drop 10 30, drop 30 28, flip 0.5 30, flip 1.0 28, flip 2.0 29, flip 5.0 27.

## Table 1 - the noise band: 95th percentile of |maxDD cut| (fraction of the shipped window maxDD) for a no-information perturbation
| type | L3M | L6M | HOLD | MID | PRE | X |
|---|---|---|---|---|---|---|
| drop 1 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 |
| drop 3 | 0.000 | 0.000 | 0.000 | 0.000 | 0.012 | 0.000 |
| drop 10 | 0.024 | 0.030 | 0.030 | 0.000 | 0.022 | 0.030 |
| drop 30 | 0.141 | 0.183 | 0.183 | 0.009 | 0.158 | 0.055 |
| flip 0.5 | 0.298 | 0.263 | 0.263 | 0.303 | 0.270 | 0.192 |
| flip 1.0 | 0.139 | 0.300 | 0.300 | 0.550 | 0.204 | 0.199 |
| flip 2.0 | 0.473 | 0.216 | 0.216 | 0.636 | 0.263 | 0.241 |
| flip 5.0 | 0.460 | 0.313 | 0.313 | 0.576 | 0.526 | 0.310 |

Window shipped maxDD on this base (L3M/L6M/HOLD/MID/PRE/X'): see noise_band_lock12.csv (base_maxdd).

## Table 2 - distribution of the signed cut (+ = smaller maxDD) and the worst-20 / Calmar noise for the three most comparable sizes
| type | win | n | p5 | p25 | p50 | p75 | p95 | SD of cut | SD of w20 ($) | SD of Calmar |
|---|---|---|---|---|---|---|---|---|---|---|
| drop 30 | L3M | 28 | -0.062 | 0.0 | 0.0 | 0.0 | 0.037 | 0.125 | 20113.767 | 0.051 |
| drop 30 | L6M | 28 | -0.182 | 0.0 | 0.0 | 0.007 | 0.034 | 0.089 | 15817.671 | 0.022 |
| drop 30 | HOLD | 28 | -0.182 | 0.0 | 0.0 | 0.007 | 0.034 | 0.089 | 4469.905 | 0.02 |
| drop 30 | MID | 28 | -0.009 | 0.0 | 0.0 | 0.0 | 0.0 | 0.094 | 13124.514 | 0.045 |
| drop 30 | PRE | 28 | -0.158 | -0.004 | 0.0 | 0.001 | 0.009 | 0.061 | 5702.321 | 0.002 |
| drop 30 | X | 28 | -0.038 | -0.008 | 0.0 | 0.005 | 0.043 | 0.041 | 3616.989 | 0.0 |
| flip 2.0 | L3M | 29 | -0.03 | 0.007 | 0.059 | 0.201 | 0.473 | 0.177 | 38680.543 | 0.148 |
| flip 2.0 | L6M | 29 | -0.216 | -0.083 | 0.008 | 0.046 | 0.178 | 0.117 | 32260.847 | 0.036 |
| flip 2.0 | HOLD | 29 | -0.216 | -0.089 | 0.008 | 0.046 | 0.178 | 0.119 | 13650.573 | 0.034 |
| flip 2.0 | MID | 29 | -0.636 | -0.087 | -0.012 | -0.004 | 0.164 | 0.255 | 35735.105 | 0.124 |
| flip 2.0 | PRE | 29 | -0.263 | -0.121 | -0.044 | -0.002 | 0.044 | 0.102 | 13558.267 | 0.005 |
| flip 2.0 | X | 29 | -0.194 | -0.04 | 0.032 | 0.054 | 0.18 | 0.115 | 7001.192 | 0.001 |
| flip 5.0 | L3M | 27 | -0.247 | 0.003 | 0.134 | 0.436 | 0.46 | 0.233 | 53995.013 | 0.211 |
| flip 5.0 | L6M | 27 | -0.313 | -0.202 | -0.004 | 0.112 | 0.173 | 0.175 | 51188.123 | 0.058 |
| flip 5.0 | HOLD | 27 | -0.313 | -0.202 | -0.004 | 0.112 | 0.173 | 0.175 | 18578.213 | 0.052 |
| flip 5.0 | MID | 27 | -0.576 | -0.45 | -0.012 | 0.007 | 0.095 | 0.269 | 40892.027 | 0.128 |
| flip 5.0 | PRE | 27 | -0.526 | -0.249 | -0.072 | 0.0 | 0.087 | 0.2 | 17404.376 | 0.007 |
| flip 5.0 | X | 27 | -0.133 | -0.044 | -0.006 | 0.102 | 0.292 | 0.13 | 12642.479 | 0.001 |


## Table 3 - the ZONES-3 finalists of Z3 (91 non-shipped cells, v1.3-assumed grid) re-expressed as cut / band (band type matched by rows changed)
Cells passing the rule (L6M and one of PRE/X' above band): **0 of 91**. Cells with >= 3 windows above band: 0. Top 10 by cut/band in L6M:
| unit | action | rows | band type | cut L6M | cut/band L6M | cut PRE | cut/band PRE | cut X | cut/band X |
|---|---|---|---|---|---|---|---|---|---|
| bar4hmid | d3 | 777 | flip 2.0 | 0.18 | 0.86 | -0.09 | -0.33 | -0.13 | -0.55 |
| bar4hmid | d5 | 777 | flip 2.0 | 0.18 | 0.85 | -0.08 | -0.29 | -0.17 | -0.69 |
| bar4hmid | d1 | 777 | flip 2.0 | 0.18 | 0.85 | -0.05 | -0.17 | -0.13 | -0.54 |
| bar4hmid | wt | 777 | flip 2.0 | 0.18 | 0.85 | -0.23 | -0.87 | -0.18 | -0.74 |
| bar4hmid | rb | 777 | flip 2.0 | 0.18 | 0.85 | -0.22 | -0.83 | -0.15 | -0.63 |
| bar4hmid | b73 | 777 | flip 2.0 | 0.18 | 0.85 | -0.22 | -0.82 | -0.15 | -0.62 |
| camH3 | rt | 526 | flip 2.0 | 0.17 | 0.8 | -0.08 | -0.29 | -0.04 | -0.18 |
| bar4hmid | rt | 777 | flip 2.0 | 0.17 | 0.79 | 0.1 | 0.37 | -0.13 | -0.54 |
| ALL7 | rt | 5920 | flip 5.0 | 0.2 | 0.63 | -0.19 | -0.35 | -0.17 | -0.55 |
| O62_30 | skip | 2179 | flip 5.0 | 0.19 | 0.61 | -0.1 | -0.2 | -0.22 | -0.71 |

Label: every Z3 cell whose cut is inside its band in L6M is NOISE, including ALL7 skip, OTE705 rb, kijun1h wt, camH3 take (their L6M cuts of 11-31% sit at or below the flip-2/5% band of 22-31%).

## Table 4 - other programs on the v1.3-assumed base (cuts from DEAD_CELLS; band = flip 2.0 and flip 5.0, conservative because their row counts are unknown)
| program   | band     |   cells |   L6M_above |   pass_rule |   pass_share |
|:----------|:---------|--------:|------------:|------------:|-------------:|
| ZL1       | flip 2.0 |      74 |           1 |           0 |   0          |
| ZL1       | flip 5.0 |      74 |           1 |           0 |   0          |
| ZONES3S4A | flip 2.0 |    1328 |          36 |          17 |   0.0128012  |
| ZONES3S4A | flip 5.0 |    1328 |          14 |           6 |   0.00451807 |
ZL1 (74 cells, tape/book zones): 0 cells pass. ZONES3S4A (1,328 screen cells): 17 pass at flip 2.0 and 6 at flip 5.0 (1.3% / 0.5% of cells; with ~1,300 cells and a 95% band a few passes are expected by chance); the passing cells are listed in noise_fin_other_lock12.csv logic (top by L6M: ARR FVG 30m D40 skip 40%, DEV on_L D40 skip 38%, ARR iplFVG 15s D20 skip 36%, SWG f5H 15s D40 skip 32%, SWG f3H 15s D40 skip 29%). Z1's line table and Z2's CRT4h / camH3 / kijun1h / PDmid picks are not in DEAD_CELLS in comparable form on this base: Z1/Z2 owners should apply Table 1 to their own cut columns (Z2's candidate grid cuts are on the v1.1 base, so only a rough guide).

## Reading
A one-line zone change (hundreds to ~1,500 rows) moves the L6M maxDD by up to 22-31% and the PRE maxDD by 26-53% (95th percentile) by chance on this base; MID is the noisiest (55-64% for flips of 1-5%) because its shipped maxDD is one 43k episode. The earlier observation (4 walk-forward switches moving MID maxDD by -83%) is therefore inside the band. Apparent drawdown cuts below about 30% in L6M, 50% in PRE or 31% in X' are not evidence on this base.
Caveats: n per type is small in this interim (27-30 draws, so the 95th percentile of |cut| is the top 1-2 draws); the band is for the information-free perturbation types used here (random row drops and random half-lot flips), not for a timing-structured perturbation; it is specific to the assumed base and to N fills. Code `l2vast/ds3/code/zones3_s3/noise7.py`, `noise_an.py`, `noise_fin.py`.


# V13X (D7 v1.3 EXACT) noise band - appended 2026-11-02 04:15Z. The section above is the ASSUMED-base interim (V13-assumed); this one is the headline. Interim n = 43-44 draws per type (lock 12R) / 37-38 (lock-off) of 300 planned; the run continues (`out/zones3/s3_v13x/noise_*_0.pkl`, `noise_an6.py` recomputes).
Base: V13X.run_v13x, live11 lots, exact U7 (never binds), exact take lines, lock 12R (and engine-own per-book locks only for 'off'). Live candidate rows 26,645. Same perturbations: drop k = 1,3,10,30 random live rows; halve lots of a random 0.5/1/2/5 % of the live rows. Band = 95th percentile of |maxDD change| / shipped maxDD of the window.
Shipped V13X maxDD (12R): L3M 39.9k, L6M 73.9k, HOLD 119.2k, MID 78.5k, PRE 252.4k, X' 173.7k.
## Band, lock 12R
| type | L3M | L6M | HOLD | MID | PRE | X' | n |
|---|---|---|---|---|---|---|---|
| drop 1 | 0.000 | 0.007 | 0.000 | 0.000 | 0.000 | 0.003 | 44 |
| drop 3 | 0.000 | 0.009 | 0.000 | 0.000 | 0.006 | 0.012 | 44 |
| drop 10 | 0.000 | 0.008 | 0.021 | 0.004 | 0.117 | 0.034 | 44 |
| drop 30 | 0.063 | 0.066 | 0.062 | 0.053 | 0.100 | 0.047 | 44 |
| flip 0.5 | 0.178 | 0.298 | 0.140 | 0.098 | 0.136 | 0.126 | 44 |
| flip 1.0 | 0.152 | 0.326 | 0.129 | 0.096 | 0.153 | 0.193 | 44 |
| flip 2.0 | 0.246 | 0.302 | 0.281 | 0.241 | 0.178 | 0.256 | 44 |
| flip 5.0 | 0.311 | 0.358 | 0.396 | 0.299 | 0.277 | 0.287 | 43 |

## Band, lock-off (engine's own per-book locks only)
| type | L3M | L6M | HOLD | MID | PRE | X' | n |
|---|---|---|---|---|---|---|---|
| drop 1 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 38 |
| drop 3 | 0.002 | 0.006 | 0.006 | 0.000 | 0.018 | 0.007 | 38 |
| drop 10 | 0.018 | 0.019 | 0.019 | 0.011 | 0.037 | 0.050 | 38 |
| drop 30 | 0.074 | 0.143 | 0.107 | 0.068 | 0.098 | 0.048 | 38 |
| flip 0.5 | 0.104 | 0.087 | 0.091 | 0.083 | 0.091 | 0.097 | 38 |
| flip 1.0 | 0.150 | 0.105 | 0.096 | 0.148 | 0.140 | 0.076 | 38 |
| flip 2.0 | 0.178 | 0.148 | 0.148 | 0.189 | 0.205 | 0.131 | 38 |
| flip 5.0 | 0.211 | 0.214 | 0.214 | 0.343 | 0.202 | 0.287 | 37 |

## Rule (unchanged): a cut counts only if cut > band of its window in L6M AND in PRE or X' (same sign), band row = nearest in rows changed (zone unit ~1,000-2,000 rows: flip 5.0; ~500 rows: flip 2.0).
## Re-expression (V13X band, lock 12R)
Z3 cells (91 non-shipped V13X grid cells): **passing the rule: 0**; cells with >= 3 windows above band: 0. Largest L6M cut/band:
| unit | action | rows | band type | cut L6M | cut/band L6M | cut PRE | cut/band PRE | cut X | cut/band X |
|---|---|---|---|---|---|---|---|---|---|
| OTE705 | d1 | 1024 | flip 5.0 | 0.32 | 0.9 | -0.13 | -0.47 | 0.12 | 0.41 |
| OTE705 | d3 | 1024 | flip 5.0 | 0.26 | 0.72 | -0.02 | -0.07 | -0.07 | -0.24 |
| OTE705 | d5 | 1024 | flip 5.0 | 0.24 | 0.68 | -0.15 | -0.54 | -0.07 | -0.26 |
| OTE705 | rb | 1024 | flip 5.0 | 0.23 | 0.65 | -0.13 | -0.45 | 0.01 | 0.05 |
| OTE705 | b73 | 1024 | flip 5.0 | 0.23 | 0.63 | -0.13 | -0.49 | 0.02 | 0.09 |
| OTE79 | d1 | 1141 | flip 5.0 | 0.22 | 0.62 | -0.08 | -0.28 | -0.04 | -0.15 |
| OTE79 | d3 | 1141 | flip 5.0 | 0.21 | 0.59 | -0.1 | -0.37 | -0.09 | -0.33 |
| bar4hmid | rt | 777 | flip 2.0 | 0.15 | 0.49 | -0.0 | -0.01 | -0.1 | -0.39 |

ALL7 skip on V13X: L6M -7.2%, HOLD +25.9%, MID +33.7%, PRE +15.2%, X' +34.2% - L6M is negative (fails), PRE +15% sits below its band (18-28%), HOLD/MID/X' exceed it (14-40%): **PARTIAL (older + HOLD/MID windows only), not L6M**. It is not ONE-WEEK (drop-5-weeks minimum +7% HOLD, +4% PRE) but its month-block bootstrap P(cut>0) is 0.50 (HOLD) / 0.83 (PRE) and the interval spans zero.
Other programs' cuts (DEAD_CELLS, scored on the assumed base): ZL1 0 of 74 pass; ZONES3S4A 7 of 1,328 pass at flip 2.0 and 3 at flip 5.0 (the lead should have the S4 owners re-score those on V13X before calling any a lead; their L6M/PRE signs flip with the base).
## Noise-floor facts that matter
(1) the walk-forward chains' whole-period cut (+16% / +26%) is inside the flip-2/5% band (PRE 18-28%), so it is not a cut; (2) the 'drop 30' perturbation (30 random rows of 26,645 = 0.1%) already moves PRE maxDD by up to 10%; (3) lock-off bands are smaller than 12R bands in L6M (15-21% vs 30-36%): the 12R lock amplifies path noise; (4) one-day lock-reset shift not run.

## Frame comparison (lock 12R vs lock-off, V13X, appended ~05:00Z)
Noise bands differ strongly between frames: flip 2% / flip 5% - lock 12R: L3M 25/31, L6M 30/36, HOLD 28/40, MID 24/30, PRE 18/28, X' 26/29 %; lock-off: L3M 18/21, L6M 15/21, HOLD 15/21, MID 19/34, PRE 21/20, X' 13/29 %. The combined 12R lock roughly doubles the L6M/HOLD noise band (a lock that pulls a whole week of trades makes the maxDD path-dependent). Use the band of the frame you score in; the headline frame is lock-off until the user confirms the combined lock. n = 43 (12R) / 38 (lock-off) draws per type so far (continuing for lock-off). Rule check in the lock-off frame: Z3 cells passing 0 / 91 (see DS3_ZONES_3_S3.md).

## Refined V13X band (appended ~06:00Z; n = 57 draws per type in lock-off, ~75 in lock 12R; both frames, flip 2% / flip 5% / drop 30)
| frame | type | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|
| lock-off (HEADLINE) | flip 2.0 | 0.174 | 0.149 | 0.149 | 0.237 | 0.172 | 0.146 |
| lock-off | flip 5.0 | 0.211 | 0.216 | 0.215 | 0.350 | 0.240 | 0.288 |
| lock-off | drop 30 | 0.075 | 0.132 | 0.083 | 0.119 | 0.098 | 0.051 |
| lock 12R | flip 2.0 | 0.237 | 0.306 | 0.300 | 0.216 | 0.207 | 0.206 |
| lock 12R | flip 5.0 | 0.325 | 0.372 | 0.398 | 0.245 | 0.281 | 0.293 |
| lock 12R | drop 30 | 0.068 | 0.076 | 0.069 | 0.057 | 0.116 | 0.081 |
Practical thresholds for a zone unit of ~500-1,500 rows in the lock-off headline frame: L6M cut > 15-22% AND PRE cut > 17-24% (or X' > 15-29%). The full per-type tables are in `out/zones3/s3_v13x/noise_band_{lock12,off}.csv`. Best-of-N chance null (placebo matrix of the 7 finalist cells x 100 draws, standardised cut, V13X): lock 12R - best cell per window p vs the best-of-101 null 0.93-1.00 (O62_30 d5 L6M, bar4hmid wt MID/PRE, kijun1h wt X'); lock-off - ALL7 rt L6M p 0.69, bar4hmid wt MID 0.25, kijun1h wt X' 0.25, others 1.00 (vs best-of-10: 0.02-0.08 for those three). No finalist is distinguishable from the best of ~100 cells by chance in either frame.

## FINAL lock-off band (HEADLINE frame), V13X, n = 107 draws per type (105 for flip 5.0); appended ~07:30Z
| type | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|
| drop 1 / 3 | 0.000 | 0.000-0.007 | 0.000-0.007 | 0.000 | 0.000-0.017 | 0.000-0.008 |
| drop 10 | 0.025 | 0.023 | 0.023 | 0.018 | 0.035 | 0.062 |
| drop 30 | 0.068 | 0.054 | 0.078 | 0.082 | 0.094 | 0.062 |
| flip 0.5 | 0.090 | 0.063 | 0.071 | 0.074 | 0.093 | 0.085 |
| flip 1.0 | 0.139 | 0.121 | 0.121 | 0.158 | 0.127 | 0.123 |
| flip 2.0 | 0.166 | 0.162 | 0.153 | 0.203 | 0.215 | 0.148 |
| flip 5.0 | 0.227 | 0.208 | 0.201 | 0.327 | 0.256 | 0.246 |
**One-day lock-reset shift** (week key of every day moved one day later / earlier, no other change; one deterministic run each): maxDD cut vs unshifted lock-off base, +1 day: L3M -7.6%, L6M -23.7%, HOLD -23.7%, MID +12.4%, PRE -7.3%, X' -0.6%; -1 day: L3M +2.7%, L6M -18.2%, HOLD -18.2%, MID +6.7%, PRE +2.8%, X' +9.9%. A calendar-day shift of the lock reset alone moves L6M/HOLD maxDD by ~18-24% - the size of a 2-5% random half-lot flip - so lock-reset timing is itself a noise source of that size; the band above (flip 2% to 5%) is the right yardstick for any zone cell that changes ~500-1,500 rows.
**Final rule (lock-off, headline): a zone cell counts only if its maxDD cut exceeds, for its size (flip 2.0 row for ~500 rows, flip 5.0 row for 1,000+ rows), BOTH the L6M band (16% / 21%) AND the PRE band (22% / 26%) or the X' band (15% / 25%), same sign; in lock 12R use the 12R rows (L6M 31% / 37%, PRE 21% / 28%, X' 21% / 29%, final n in the next line when the 12R run completes).** Z3's 91 cells: 0 pass in lock-off (rule recomputed with the final band; csv `noise_fin_mine_off.csv`). Best-of-N null with 100 draws per finalist in both frames: no finalist beats the best of ~100 cells (lock-off best-of-101 p >= 0.25, lock 12R >= 0.93).


# V13Y (D7 v1.3 EXACT + add-fill ordering fix) NOISE BAND - appended 2026-11-02 ~09:20Z (the V13X sections above are on the DEFECT BASE)
Phase-averaged (K = 9 lock-reset phases: week key shifted -4..+4 label days), paired with the shipped layer at the same phase, perturbation = random 2% / 5% of live rows halved, n = 50 draws per type (60 planned), both frames. PA band = 95th percentile of |phase-averaged paired maxDD cut|; single-path band = phase 0 only.
## Phase-averaged band (USE THIS ONE)
| frame | flip | L3M | L6M | HOLD | MID | PRE | X' | n |
|---|---|---|---|---|---|---|---|---|
| lock-off | 2% | 0.323 | 0.155 | 0.133 | 0.268 | 0.115 | 0.141 | 51 |
| lock-off | 5% | 0.320 | 0.200 | 0.191 | 0.398 | 0.161 | 0.224 | 50 |
| lock 12R | 2% | 0.163 | 0.110 | 0.107 | 0.265 | 0.133 | 0.099 | 50 |
| lock 12R | 5% | 0.228 | 0.248 | 0.135 | 0.411 | 0.154 | 0.133 | 50 |

## Single-path band (phase 0)
| frame | flip | L3M | L6M | HOLD | MID | PRE | X' | n |
|---|---|---|---|---|---|---|---|---|
| lock-off | 2% | 0.273 | 0.151 | 0.127 | 0.586 | 0.166 | 0.180 | 51 |
| lock-off | 5% | 0.255 | 0.269 | 0.228 | 0.778 | 0.172 | 0.222 | 50 |
| lock 12R | 2% | 0.567 | 0.214 | 0.144 | 0.192 | 0.273 | 0.377 | 50 |
| lock 12R | 5% | 0.627 | 0.681 | 0.253 | 0.335 | 0.353 | 0.471 | 50 |

Shipped-layer maxDD across the 9 phases on V13Y ($k, mean / SD / range): lock-off L6M 118 / 9.5 / 96-126, PRE 138 / 7.7 / 129-150, X' 76 / 11.8 / 67-97, MID 30 / 1.3; lock 12R L6M 87 / 23 / 53-121, PRE 185 / 66 / 107-282, X' 99 / 30 / 75-145, MID 42 / 16.
Rule (unchanged, now on the PA statistic): a phase-averaged cut counts only if it exceeds the PA band in L6M AND in PRE or X' (row = nearest in rows changed: flip 2 for ~500 rows, flip 5 for 1,000+). Lock-off: L6M 15.5 / 20, PRE 11.5 / 16, X' 14 / 22 %. Lock 12R: L6M 11 / 25, PRE 13 / 15, X' 10 / 13 %. Phase-averaging shrinks the 12R band 3x (L6M single-path flip-5 68% -> 25%) but only slightly in lock-off (L6M 27% -> 20%): the lock-off noise is mostly WHICH rows are halved (70-90% of the variance is draw-specific, V13X check), i.e. trade-selection noise of the maxDD extreme, not lock phase; it cannot be averaged away by phase and needs more draws/rows (a real effect must exceed it).

## V13Y band FINAL (n = 60 draws per type, K = 9) - appended ~10:00Z
| frame | flip | L3M | L6M | HOLD | MID | PRE | X |
|---|---|---|---|---|---|---|---|
| lock-off | 2% | 0.308 | 0.157 | 0.145 | 0.261 | 0.114 | 0.159 |
| lock-off | 5% | 0.335 | 0.199 | 0.191 | 0.366 | 0.174 | 0.230 |
| lock 12R | 2% | 0.171 | 0.117 | 0.112 | 0.239 | 0.131 | 0.100 |
| lock 12R | 5% | 0.226 | 0.239 | 0.117 | 0.373 | 0.131 | 0.145 |
