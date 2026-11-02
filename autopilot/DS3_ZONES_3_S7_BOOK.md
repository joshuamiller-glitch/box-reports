# DS3_ZONES_3_S7_BOOK - ZL-1 order-book zones, NEW CAP (label days <= 20261030), written 2026-11-02 00:23Z
Bases: pass 1 on D7 **v1.2 interim** (22+ cells, all |maxDD cut| <= 7% in L3M/L6M/HOLD/MID, none ranked) and the main table on D7 **v1.3** (code/d7base/d7_v13.py, lock 12R, profit side best-effort gated take lines). Windows from cap/windows.py (L1M L2M view). Everything post-hoc, Shadow only, no PASS claim. Prereg sha256 dc117cd39dc84c4503e8d683e0da04054b3bcca5c056df98e269cc5189751f3e (ZL1_zones_scoring_prereg.md) plus stream preregs d84ca7c0... / 342e59e6....

## DATA line
NQ 1-s L2 table (aggregates of mbp-10) 2023-08 .. 2026-10-30 (1-s tables incl. the 2026-10 weekly ext parts; no duplicated timestamps; path arrays ds3_g2_redo, identical to the old ones through the old cap so old streams stay valid); derivable, nothing to buy. 96 streams rebuilt to the new cap: /mnt/l2/l2vast/ds3_zones3_new/zl1/streams_book/ (link l2vast/ds3/out/zl_new), POI format, README out/zl/README_streams_book.md (still valid), per-day counts counts_per_day.csv. Regime note: iceberg-refill and defended-wall event counts fall about 10x from 2023-24 to 2026 (ICE R2N30 1239/month in 2023-08, 80/month in 2026-10) while pulled walls rise; the L2 book behaves differently now, so recent-window book zones have few events.

## Descriptive (new cap, keep 4 h; reaction rate = price moves 5 pts away on the approach side before 5 pts through, 30 min, vs 200 random-level placebo draws; p = share of draws >= observed)
| stream               |     n |   ev_day |   X5_obs |   X5_A |   X5_pA |   X5_B |   X5_pB |   X5_L3M |   X5_L3M_A |   X5_L6M |   X5_L6M_A |
|:---------------------|------:|---------:|---------:|-------:|--------:|-------:|--------:|---------:|-----------:|---------:|-----------:|
| ABS|k10N10|4h        |    55 |    0.065 |    0.457 |  0.455 |   0.520 |  0.491 |   0.795 |    1.000 |      0.467 |    0.571 |      0.529 |
| ABS|k1N10|4h         |  4785 |    5.690 |    0.500 |  0.494 |   0.210 |  0.503 |   0.670 |    0.511 |      0.554 |    0.488 |      0.499 |
| ABS|k1N30|4h         |   265 |    0.315 |    0.495 |  0.521 |   0.800 |  0.539 |   0.955 |    0.000 |      0.452 |    0.000 |      0.427 |
| ABS|k2N10|4h         |  1170 |    1.391 |    0.504 |  0.478 |   0.030 |  0.483 |   0.040 |    0.581 |      0.583 |    0.539 |      0.476 |
| ABS|k2N30|4h         |    77 |    0.092 |    0.458 |  0.516 |   0.830 |  0.593 |   0.995 |  nan     |    nan     |    0.000 |      0.335 |
| ABS|k3N10|4h         |   548 |    0.652 |    0.488 |  0.474 |   0.265 |  0.485 |   0.440 |    0.529 |      0.592 |    0.465 |      0.449 |
| ABS|k3N30|4h         |    27 |    0.032 |    0.364 |  0.479 |   0.920 |  0.577 |   1.000 |  nan     |    nan     |  nan     |    nan     |
| ABS|k5N10|4h         |   223 |    0.265 |    0.516 |  0.455 |   0.050 |  0.499 |   0.250 |    0.750 |      0.550 |    0.545 |      0.432 |
| ABS|k5N30|4h         |    15 |    0.018 |    0.615 |  0.633 |   0.675 |  0.702 |   0.980 |  nan     |    nan     |  nan     |    nan     |
| ABS|k5N5|4h          |   628 |    0.747 |    0.495 |  0.482 |   0.250 |  0.499 |   0.605 |    0.525 |      0.492 |    0.429 |      0.447 |
| DEF|k3N10|4h         | 16475 |   19.590 |    0.495 |  0.501 |   0.935 |  0.502 |   0.965 |    0.535 |      0.509 |    0.539 |      0.508 |
| DEF|k3N30|4h         |  2161 |    2.570 |    0.481 |  0.502 |   0.985 |  0.500 |   0.975 |    0.524 |      0.435 |    0.586 |      0.439 |
| DEF|k3N60|4h         |   434 |    0.516 |    0.476 |  0.502 |   0.840 |  0.505 |   0.885 |    0.000 |      0.345 |    0.000 |      0.345 |
| DEF|k5N30|4h         |   781 |    0.929 |    0.452 |  0.491 |   0.995 |  0.493 |   0.995 |    0.429 |      0.355 |    0.571 |      0.424 |
| ICE|R2N10|4h         | 24098 |   28.654 |    0.503 |  0.506 |   0.800 |  0.506 |   0.915 |    0.536 |      0.528 |    0.504 |      0.503 |
| ICE|R2N30|4h         | 24365 |   28.971 |    0.504 |  0.505 |   0.680 |  0.507 |   0.910 |    0.559 |      0.532 |    0.510 |      0.508 |
| ICE|R3N30|4h         |  1243 |    1.478 |    0.504 |  0.489 |   0.125 |  0.499 |   0.235 |    0.700 |      0.528 |    0.588 |      0.523 |
| ICE|R5N30|4h         |    10 |    0.012 |    0.250 |  0.479 |   0.940 |  0.277 |   0.920 |  nan     |    nan     |  nan     |    nan     |
| PUL|k3|4h            | 25510 |   30.333 |    0.499 |  0.496 |   0.175 |  0.497 |   0.185 |    0.517 |      0.500 |    0.507 |      0.494 |
| PUL|k5|4h            |  6090 |    7.241 |    0.496 |  0.493 |   0.260 |  0.494 |   0.330 |    0.527 |      0.500 |    0.507 |      0.492 |
| SWP|ext_pd_N15|4h    |   751 |    0.893 |    0.436 |  0.494 |   1.000 |  0.477 |   0.985 |    0.472 |      0.466 |    0.535 |      0.485 |
| SWP|ext_pd_N5|4h     |   723 |    0.860 |    0.434 |  0.493 |   1.000 |  0.478 |   0.995 |    0.462 |      0.470 |    0.523 |      0.481 |
| SWP|ext_sess_N15|4h  |  7177 |    8.534 |    0.481 |  0.504 |   1.000 |  0.496 |   1.000 |    0.495 |      0.496 |    0.486 |      0.498 |
| SWP|ext_sess_N5|4h   |  6982 |    8.302 |    0.484 |  0.503 |   1.000 |  0.495 |   0.985 |    0.497 |      0.497 |    0.487 |      0.498 |
| SWP|ext_swing_N15|4h | 38623 |   45.925 |    0.490 |  0.504 |   1.000 |  0.501 |   1.000 |    0.509 |      0.507 |    0.495 |      0.504 |
| SWP|ext_swing_N5|4h  | 37675 |   44.798 |    0.489 |  0.504 |   1.000 |  0.501 |   1.000 |    0.476 |      0.503 |    0.486 |      0.504 |
| SWP|lvl_pd_N15|4h    |   751 |    0.893 |    0.455 |  0.466 |   0.740 |  0.464 |   0.725 |    0.421 |      0.424 |    0.492 |      0.461 |
| SWP|lvl_pd_N5|4h     |   723 |    0.860 |    0.456 |  0.465 |   0.695 |  0.468 |   0.785 |    0.411 |      0.417 |    0.487 |      0.459 |
| SWP|lvl_sess_N15|4h  |  7177 |    8.534 |    0.487 |  0.491 |   0.805 |  0.491 |   0.820 |    0.476 |      0.495 |    0.473 |      0.488 |
| SWP|lvl_sess_N5|4h   |  6982 |    8.302 |    0.486 |  0.491 |   0.815 |  0.490 |   0.805 |    0.475 |      0.498 |    0.473 |      0.490 |
| SWP|lvl_swing_N15|4h | 38623 |   45.925 |    0.498 |  0.500 |   0.710 |  0.499 |   0.675 |    0.498 |      0.500 |    0.492 |      0.496 |
| SWP|lvl_swing_N5|4h  | 37675 |   44.798 |    0.501 |  0.500 |   0.390 |  0.503 |   0.760 |    0.504 |      0.501 |    0.500 |      0.496 |
Reading: no book stream reacts better than random levels except by chance (ABS k2N10 0.504 vs 0.478 p 0.03 and ABS k5N10 0.516 vs 0.455 p 0.05 among 32 rows, n 1170 / 223); sweep extremes (where the stops sat) and defended walls react WORSE than random levels (rank 0.99-1.0).

## AHEAD frame on D7 v1.3 (skip/half at D 20/40, fresh nearest level between entry and target), ranked by mean of L6M and HOLD maxDD cut (top 15 of 56; full table out/zl_new/table_q1.csv)
cut = 1 - maxDD(cell)/maxDD(base) (weekly cumulative, live lots); n flagged = trade rows flagged of 88,490.
| job                            |   nflag |   L3M_cut |   L6M_cut |   HOLD_cut |   MID_cut |   PRE_cut |   X'_cut |   HOLD_dmean |   HOLD_mde |
|:-------------------------------|--------:|----------:|----------:|-----------:|----------:|----------:|---------:|-------------:|-----------:|
| PUL|k3|4h|AH|20|skip           |    1564 |     0.317 |     0.360 |      0.355 |    -0.044 |    -0.028 |    0.056 |     2423.836 |   7498.385 |
| PUL|k3|4h|AH|40|skip           |    2138 |     0.486 |     0.112 |      0.112 |    -0.497 |    -0.036 |    0.097 |     -842.130 |   9187.872 |
| SWP|lvl_sess_N5|4h|AH|40|half  |    1475 |     0.100 |     0.104 |      0.104 |    -0.040 |    -0.193 |    0.097 |    -1386.122 |   2938.589 |
| SWP|lvl_swing_N5|4h|AH|20|skip |    2309 |    -0.066 |     0.084 |      0.084 |    -0.724 |     0.205 |    0.117 |    -1007.524 |   4350.888 |
| SWP|lvl_pd_N5|4h|AH|40|half    |     262 |     0.000 |     0.080 |      0.080 |     0.000 |    -0.152 |    0.000 |     -139.064 |    977.672 |
| SWP|lvl_swing_N5|4h|AH|40|skip |    2929 |    -0.106 |     0.066 |      0.066 |    -0.015 |     0.228 |    0.103 |       72.803 |   2432.769 |
| SWP|lvl_sess_N5|4h|AH|20|half  |    1111 |     0.013 |     0.015 |      0.015 |    -0.066 |    -0.254 |    0.097 |    -1368.346 |   2837.598 |
| SWP|ext_pd_N5|4h|AH|40|skip    |     656 |     0.015 |     0.014 |      0.014 |     0.000 |    -0.062 |   -0.011 |    -1261.632 |   4282.864 |
| SWP|ext_swing_N5|4h|AH|40|half |    8719 |     0.125 |     0.012 |      0.012 |    -0.009 |     0.086 |   -0.190 |    -3262.971 |   5345.908 |
| SWP|ext_pd_N5|4h|AH|40|half    |     656 |     0.016 |     0.008 |      0.008 |     0.000 |    -0.049 |    0.005 |    -2082.430 |   3954.046 |
| SWP|ext_pd_N5|4h|AH|20|skip    |     427 |     0.013 |     0.006 |      0.006 |     0.000 |     0.113 |   -0.011 |    -1338.710 |   4452.346 |
| SWP|ext_pd_N5|4h|AH|20|half    |     427 |     0.009 |     0.004 |      0.004 |     0.000 |    -0.111 |    0.005 |    -2163.992 |   3979.139 |
| ICE|R2N30|4h|AH|40|skip        |     736 |     0.005 |     0.002 |      0.002 |     0.220 |    -0.047 |    0.292 |      308.898 |   1353.452 |
| SWP|lvl_pd_N5|4h|AH|20|half    |     199 |     0.000 |     0.000 |      0.000 |     0.000 |    -0.132 |    0.000 |     -335.532 |   1025.325 |
| ABS|k1N10|4h|AH|40|skip        |     252 |     0.000 |     0.000 |      0.000 |     0.000 |     0.007 |    0.023 |     -487.876 |    597.625 |

## The one cell with a recent cut: PUL k3 4 h, D 20, skip (pulled-wall levels, fake support/resistance within 20 pts ahead)
| window | maxDD base -> cell | cut | mean delta $/wk (MDE) | worst-20 base -> cell |
|--|--|--|--|--|
| L1M | 16,128 -> 16,128 | +0.00 | +756 (11,442) | 104,284 -> 108,066 |
| L2M | 34,175 -> 28,889 | +0.15 | +17,998 (36,814) | 105,333 -> 267,318 |
| L3M | 43,587 -> 29,763 | +0.32 | +12,443 (26,104) | 106,060 -> 267,813 |
| L6M | 94,071 -> 60,179 | +0.36 | +5,812 (13,870) | -62,810 -> 89,759 |
| HOLD | 94,071 -> 60,684 | +0.35 | +2,424 (7,498) | -369,200 -> -341,660 |
| MID | 43,072 -> 44,951 | -0.04 | -344 (2,884) | 236,625 -> 232,499 |
| PRE | 175,098 -> 179,982 | -0.03 | -263 (1,945) | -456,008 -> -446,046 |
| X' | 234,635 -> 221,542 | +0.06 | +353 (1,152) | -368,542 -> -353,010 |

Robustness (rob table): | job                  | win   |   cut |   cut_dropweek |   loo_min |   loo_max |   boot_lo |   boot_hi |   week_dd |   label |
|:---------------------|:------|------:|---------------:|----------:|----------:|----------:|----------:|----------:|--------:|
| PUL|k3|4h|AH|20|skip | L3M   | 0.317 |          0.182 |     0.314 |     0.56  |    -0.006 |     0.593 |    202638 |     nan |
| PUL|k3|4h|AH|20|skip | L6M   | 0.36  |          0.307 |     0.327 |     0.484 |     0.102 |     0.45  |    202638 |     nan |
| PUL|k3|4h|AH|20|skip | HOLD  | 0.355 |          0.301 |    -0.108 |     0.437 |    -0.483 |     0.343 |    202638 |     nan |
Sensitivity: D 40 gives L3M +49% but L6M +11%, HOLD +11%, MID -50% (D-fragile); the 1 h keep is worse (L6M -16%, PRE -24%); half instead of skip is worse (L6M -18%). The maxDD week is 2026-W38 in every recent window; the cut is positive in L3M/L6M/HOLD (+32/+36/+36%) but PRE -3%, MID -4%, X' +6%: it lives in the last 3 months (Asia books: KB/HM +72k, +32k in L6M by book x session). **Label: FRAGILE and recent-only (not RISK-KEEP: PRE/MID do not agree, D40 fails, HOLD leave-one-month-out minimum is negative).**
Placebos for this cell (20 draws each; rank = share of placebo cuts >= the cell's cut; low rank is good):
| placebo                                       |   draws |   L3M_mean |   L6M_mean |   HOLD_mean |   L3M_rank |   L6M_rank |   HOLD_rank |
|:----------------------------------------------|--------:|-----------:|-----------:|------------:|-----------:|-----------:|------------:|
| same-volume random skip (stratified)          |      20 |      0.190 |      0.007 |      -0.013 |      0.400 |      0.050 |       0.050 |
| random rows, same count per day               |      20 |      0.170 |     -0.009 |      -0.009 |      0.350 |      0.000 |       0.000 |
| shuffled-day (same book x session, other day) |      20 |      0.151 |     -0.039 |      -0.041 |      0.300 |      0.000 |       0.000 |

## 'L2 zone confirms a price line' (8 coded lines at D20 fresh ahead; confirmed = a book level of the stream within 5 pts of that line's distance; "weak line" = line without book evidence)
confirm_skip (skip confirmed rows): L6M cut -9% to +1.3%, essentially no effect (89-625 rows); weak_full (undo the HALF on lines without book evidence = nearly all line rows, since confirmation is rare) makes maxDD 12-40% WORSE in L6M (PUL -12%, swing/session sweeps -30..-40%, ICE/DEF -31%) and worse in every recent window: the shipped HALF on the price lines is doing its work and the book streams cannot separate good from weak lines. Full rows: out/zl_new/table_q2.csv (18 cells). ZL-3 owns the combined learned rule; features for it: out/zl_new/feats.npz (ahead/behind fresh distance and age per stream for every trade row).

## Not done yet (next): BEHIND / AT frames, D 10/30/60 and fraction-of-target for the top streams, definition variants, per vol tercile, month purged walk-forward (Z3 owns), 1-s/3-s delay (skip/half only: not applicable). Book x session cube per cell is stored in res_q1_0.pkl.
## Plain sentence (interim): order-book zones add about nothing to the drawdown cut of the price zones on the new windows: 53 of 56 AHEAD cells cut maxDD by under 10% in L6M/HOLD (the streams flag 199-8,719 of 88,490 trade rows) and the one that cuts much (pulled walls, D20 skip, L3M/L6M/HOLD 32-36%) fails PRE/MID/D40 and is fragile; "they are the same information / they are worse" for confirming price lines.

## Placebo verdict for PUL k3 4h D20 skip (v1.3)
L6M and HOLD cut (36%) beats all three placebos (ranks 0.00-0.05 of 20 draws; resolution 1/21), but L3M does not (placebo ranks 0.30-0.40: random same-volume skips already cut L3M maxDD by 15-19%, a volume effect) and PRE/MID/D40/HOLD-leave-one-month-out disagree. Label: (L6M/HOLD only) FRAGILE, not RISK-KEEP; needs ZL-3's walk-forward and 100+ draws before any use. D7 live definition of the stream: see DS3_ZONES_3_L2_BOOK.md (PUL: wall >= 3x median level size, >= 5 s old, within 3 ticks of best, then size < 0.3 x peak or best moves past it with no print at/through it; level = wall price, kept 4 h; fresh until price leaves 0.5 pt and returns).


## Follow-up 1 (00:50Z): PUL k3 4h D20 skip, where it comes from (books: book0..5 = K6 P6 U6 H6 M6 A6)
## PUL k3 4h D20 skip: where the cell-minus-base dollars come from (D7 v1.3, $k summed over the window)

### L3M: by book (rows) x session (cols), $k; total +161.8k; Asia +139.9k, non-Asia +21.9k

|       |   asia |   london |   pre |   nyam |   nypm |   close |
|:------|-------:|---------:|------:|-------:|-------:|--------:|
| K6    |   15.7 |      1.8 |     0 |   -3.5 |    2.5 |       0 |
| P6    |   60.5 |      2.8 |     0 |    0   |    0   |       0 |
| U6    |   15.5 |     13.9 |     0 |    0   |    0   |       0 |
| H6    |   41.8 |      0   |     0 |    8.5 |    0   |       0 |
| M6    |    0   |     -5.2 |     0 |    1.1 |    0   |       0 |
| A6    |    6.3 |      0   |     0 |    0   |    0   |       0 |

### L6M: by book (rows) x session (cols), $k; total +156.9k; Asia +136.7k, non-Asia +20.2k

|       |   asia |   london |   pre |   nyam |   nypm |   close |
|:------|-------:|---------:|------:|-------:|-------:|--------:|
| K6    |   12.4 |      7.4 |     0 |    0.4 |   -8.5 |       0 |
| P6    |   71.7 |     -4.1 |     0 |    0   |    0   |       0 |
| U6    |   19.4 |     15.9 |     0 |    0   |    0   |       0 |
| H6    |   31.9 |      0   |     0 |   10.6 |    0   |       0 |
| M6    |    0   |     -0.8 |     0 |   -0.7 |    0   |       0 |
| A6    |    1.4 |      0   |     0 |    0   |    0   |       0 |

### HOLD: by book (rows) x session (cols), $k; total +126.0k; Asia +130.1k, non-Asia -4.0k

|       |   asia |   london |   pre |   nyam |   nypm |   close |
|:------|-------:|---------:|------:|-------:|-------:|--------:|
| K6    |   17.5 |     10.1 |     0 |   -0.8 |  -10.9 |       0 |
| P6    |   59.1 |     -6.9 |     0 |  -19.4 |    0   |       0 |
| U6    |   26.5 |     15.9 |     0 |    0   |    0   |       0 |
| H6    |   23.1 |      0   |     0 |   14.3 |    0   |       0 |
| M6    |    0   |     -4.1 |     0 |   -2.3 |    0   |       0 |
| A6    |    3.8 |      0   |     0 |    0   |    0   |       0 |

### MID: by book (rows) x session (cols), $k; total -4.1k; Asia +1.1k, non-Asia -5.2k

|       |   asia |   london |   pre |   nyam |   nypm |   close |
|:------|-------:|---------:|------:|-------:|-------:|--------:|
| K6    |    5.7 |      2.2 |     0 |   -1.1 |   -2.4 |       0 |
| P6    |   -5.9 |      0.8 |     0 |    0   |    0   |       0 |
| U6    |    7.1 |     -0.1 |     0 |    0   |    0   |       0 |
| H6    |   -8.2 |      0   |     0 |   -0.9 |    0   |       0 |
| M6    |    0   |     -1.3 |     0 |   -2.5 |    0   |       0 |
| A6    |    2.5 |      0   |     0 |    0   |    0   |       0 |

### PRE: by book (rows) x session (cols), $k; total -19.7k; Asia +39.0k, non-Asia -58.7k

|       |   asia |   london |   pre |   nyam |   nypm |   close |
|:------|-------:|---------:|------:|-------:|-------:|--------:|
| K6    |   22.9 |      1.4 |     0 |    0.7 |   -5.8 |       0 |
| P6    |    9.2 |    -25.9 |     0 |    4   |    0   |       0 |
| U6    |   -0.1 |    -14.2 |     0 |    0   |    0   |       0 |
| H6    |   -1.4 |      0   |     0 |   -6.1 |    0   |       0 |
| M6    |    0   |     -8.5 |     0 |   -4.4 |    0   |       0 |
| A6    |    8.5 |      0   |     0 |    0   |    0   |       0 |

### X': by book (rows) x session (cols), $k; total +15.5k; Asia +14.8k, non-Asia +0.7k

|       |   asia |   london |   pre |   nyam |   nypm |   close |
|:------|-------:|---------:|------:|-------:|-------:|--------:|
| K6    |   -1.9 |      0.7 |     0 |    0.9 |   -0.6 |       0 |
| P6    |   20.6 |      9.4 |     0 |    1.1 |    0   |       0 |
| U6    |   -0.9 |     -0.7 |     0 |    0   |    0   |       0 |
| H6    |   -2.7 |      0   |     0 |    0   |    0   |       0 |
| M6    |    0   |     -9.3 |     0 |   -0.6 |    0   |       0 |
| A6    |   -0.4 |      0   |     0 |    0   |    0   |       0 |

### by realised-volatility tercile of the day (daily path range, whole-sample terciles), cell-base $k and day counts

| window   | T1            | T2            | T3            |
|:---------|:--------------|:--------------|:--------------|
| L6M      | +18.1k (2d)   | +86.6k (36d)  | +52.3k (93d)  |
| HOLD     | +12.6k (17d)  | +63.1k (76d)  | +50.3k (165d) |
| PRE      | -21.7k (121d) | -25.8k (122d) | +27.7k (121d) |
| X'       | +8.7k (137d)  | +6.8k (72d)   | +0.0k (7d)    |

### cuts with the 2026-W38 week dropped (leave-one-episode-out) and all windows

| window   |    cut |   week_of_maxDD |   cut_without_W38 |   cut_drop_dd_week |   loo_month_min |   loo_month_max | boot90       |
|:---------|-------:|----------------:|------------------:|-------------------:|----------------:|----------------:|:-------------|
| L3M      |  0.317 |          202638 |             0.182 |              0.182 |           0.314 |           0.56  | [-0.01,0.59] |
| L6M      |  0.36  |          202638 |             0.307 |              0.307 |           0.327 |           0.484 | [0.10,0.45]  |
| HOLD     |  0.355 |          202638 |             0.301 |              0.301 |          -0.108 |           0.437 | [-0.48,0.34] |
| MID      | -0.044 |          202613 |            -0.044 |              0     |          -0.044 |           0     | [-0.09,0.00] |
| PRE      | -0.028 |          202518 |            -0.028 |             -0.081 |          -0.15  |           0.092 | [-0.33,0.22] |
| X'       |  0.056 |          202347 |             0.056 |              0.058 |           0.017 |           0.074 | [-0.05,0.14] |

### (4) count artefact check: PUL k3 events per month, rows flagged D20, and monthly cell-base $k

|         |   events |   flagged_rows |   delta_k |   events_per_flag |
|:--------|---------:|---------------:|----------:|------------------:|
| 2023-08 |      286 |             11 |       1.3 |               0   |
| 2023-09 |      177 |             12 |       6.2 |               0.1 |
| 2023-10 |      225 |              5 |      -0.2 |               0   |
| 2023-11 |      225 |              9 |      10.8 |               0   |
| 2023-12 |      254 |             13 |      -8.3 |               0.1 |
| 2024-01 |      270 |             17 |       5.8 |               0.1 |
| 2024-02 |      224 |             17 |     -22.1 |               0.1 |
| 2024-03 |      265 |             27 |       2.6 |               0.1 |
| 2024-04 |      282 |             18 |      15.8 |               0.1 |
| 2024-05 |      210 |             11 |      -4.3 |               0.1 |
| 2024-06 |      205 |             16 |       0   |               0.1 |
| 2024-07 |      485 |             25 |       1.9 |               0.1 |
| 2024-08 |     1261 |             75 |      -9.2 |               0.1 |
| 2024-09 |      633 |             34 |      -8.8 |               0.1 |
| 2024-10 |      379 |             28 |      -0.2 |               0.1 |
| 2024-11 |      223 |             16 |       2.3 |               0.1 |
| 2024-12 |      283 |             21 |       6.8 |               0.1 |
| 2025-01 |      438 |             21 |     -25.5 |               0   |
| 2025-02 |      857 |             48 |     -13.7 |               0.1 |
| 2025-03 |      864 |             50 |      -1.2 |               0.1 |
| 2025-04 |     1447 |            101 |      19.1 |               0.1 |
| 2025-05 |      587 |             41 |      11.8 |               0.1 |
| 2025-06 |     1190 |             51 |       5   |               0   |
| 2025-07 |      416 |             12 |       0   |               0   |
| 2025-08 |      366 |             13 |      -1.4 |               0   |
| 2025-09 |      309 |             10 |       3   |               0   |
| 2025-10 |      454 |             34 |      31.4 |               0.1 |
| 2025-11 |      589 |             28 |      -7.1 |               0   |
| 2025-12 |     1270 |             39 |     -27.4 |               0   |
| 2026-01 |      351 |             31 |       7.8 |               0.1 |
| 2026-02 |      457 |              9 |       0   |               0   |
| 2026-03 |     1388 |            105 |       7.2 |               0.1 |
| 2026-04 |      818 |             47 |     -11.3 |               0.1 |
| 2026-05 |      834 |             46 |      12.3 |               0.1 |
| 2026-06 |     1841 |            114 |     -50.1 |               0.1 |
| 2026-07 |     1705 |            175 |      33   |               0.1 |
| 2026-08 |     1270 |             75 |      -0.2 |               0.1 |
| 2026-09 |     1340 |            101 |     158.2 |               0.1 |
| 2026-10 |      832 |             58 |       3.8 |               0.1 |

Spearman(events, delta_k) = 0.01; Spearman(flagged rows, delta_k) = 0.11; PUL events/month: 2023-08..2024-07 mean 259, 2025-08..2026-02 mean 542, 2026-03..10 mean 1254

Reading: (a) it is an ASIA product: of +157k cell-minus-base dollars in L6M, +137k is Asia (P6 +72k, H6 +32k, U6 +19k, K6 +12k); non-Asia +20k; in HOLD non-Asia is -4k. (b) It is ONE MONTH: monthly delta is +158k in 2026-09 (the W38 episode) and the other 27 months net to about -2k (Spearman of monthly event count vs delta 0.01). Dropping W38 from the window leaves the maxDD cut at 30-31% in L6M/HOLD only because the next-largest drawdown episode is also reduced, but L3M falls from 32% to 18%. (c) volatility: L6M gain sits in the middle and top vol terciles (+87k / +52k); in PRE it loses in the two low terciles (-22k / -26k) and gains only in the top (+28k): no stable regime. (d) count artefact: pulled-wall events per month ROSE (about 260/month in 2023-24 to 540 in 2025-26 to 1,250 in 2026-03..10) and flagged rows per month rose from about 10-40 to 50-175, so the recent window has several times the exposure that PRE had; ICE and DEF are the streams whose counts fell 10x (their cells show no cut in any window, so there is nothing to explain).
