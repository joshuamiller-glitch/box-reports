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


## Follow-up 2: definition sensitivity (D7 v1.3; maxDD cut vs base per window; flagged rows)

### PUL|k3|4h (keep 1h/24h rows carry their own stream name)

| stream     | frame   |     D | act   |   nflag |    L3M |    L6M |   HOLD |    MID |    PRE |     X' |   mean_HOLD |   mde_HOLD |
|:-----------|:--------|------:|:------|--------:|-------:|-------:|-------:|-------:|-------:|-------:|------------:|-----------:|
| PUL|k3|1h  | AH      | 20    | half  |    1200 |  0.101 | -0.233 | -0.233 | -0.153 | -0.142 |  0.042 |   -1333.44  |   2053.22  |
| PUL|k3|1h  | AH      | 40    | half  |    1458 |  0.041 | -0.247 | -0.247 | -0.111 | -0.13  |  0.042 |   -1386.8   |   2103.7   |
| PUL|k3|1h  | AH      | 20    | skip  |    1200 | -0.125 | -0.156 | -0.156 | -0.09  | -0.236 |  0.01  |    -486.054 |   5071.42  |
| PUL|k3|1h  | AH      | 40    | skip  |    1458 | -0.05  | -0.098 | -0.098 | -0.079 | -0.09  |  0.01  |    -424.139 |   5346.78  |
| PUL|k3|24h | AH      | 20    | skip  |    2164 |  0.324 |  0.348 |  0.348 | -0.009 | -0.035 |  0.059 |    1912.6   |   7223.62  |
| PUL|k3|24h | AH      | 40    | skip  |    3590 |  0.002 | -0.151 | -0.151 | -0.397 | -0.211 |  0.114 |    -160.648 |   7558.9   |
| PUL|k3|4h  | AH      | 20    | half  |    1564 |  0.182 | -0.181 | -0.181 | -0.205 | -0.124 |  0.055 |   -1187.37  |   2024.79  |
| PUL|k3|4h  | AH      | 40    | half  |    2138 |  0.315 | -0.106 | -0.106 | -0.743 | -0.09  |  0.072 |   -2420     |   4264.72  |
| PUL|k3|4h  | AH      | 10    | skip  |    1017 |  0.391 |  0.085 |  0.085 | -0.009 | -0.08  |  0.012 |    -467.97  |   2026.01  |
| PUL|k3|4h  | AH      | 20    | skip  |    1564 |  0.317 |  0.36  |  0.355 | -0.044 | -0.028 |  0.056 |    2423.84  |   7498.39  |
| PUL|k3|4h  | AH      | 30    | skip  |    1927 |  0.423 |  0.466 |  0.355 |  0.104 | -0.055 |  0.086 |    1529.13  |   8473.6   |
| PUL|k3|4h  | AH      | 40    | skip  |    2138 |  0.486 |  0.112 |  0.112 | -0.497 | -0.036 |  0.097 |    -842.13  |   9187.87  |
| PUL|k3|4h  | AH      | 60    | skip  |    2387 |  0.311 |  0.033 |  0.033 | -0.467 | -0.017 |  0.134 |   -1235.39  |   9067.89  |
| PUL|k3|4h  | AHF     |  0.25 | skip  |    1231 |  0.256 |  0.293 |  0.293 | -0.009 | -0.075 |  0.056 |    1372.45  |   4823.58  |
| PUL|k3|4h  | AHF     |  0.5  | skip  |    1833 |  0.423 |  0.466 |  0.355 |  0.104 | -0.055 |  0.086 |    1529.13  |   8473.6   |
| PUL|k3|4h  | AHF     |  0.75 | skip  |    2158 |  0.486 |  0.146 |  0.146 | -0.468 | -0.025 |  0.097 |    -734.461 |   9193.69  |
| PUL|k3|4h  | AT      |  2    | take  |     566 |  0.271 |  0.662 |  0.662 |  0.761 |  0.759 |  0.919 |  -23196.5   |  18271.9   |
| PUL|k3|4h  | AT      |  2    | up    |     566 | -0.101 | -0.008 | -0.008 | -0.004 | -0.002 | -0.015 |     152.72  |    770.558 |
| PUL|k3|4h  | BH      | 20    | half  |    3010 | -0.034 | -0.289 | -0.289 | -0.012 | -0.427 |  0.058 |   -1464.66  |   2296.81  |
| PUL|k3|4h  | BH      | 20    | skip  |    3010 | -0.273 | -0.459 | -0.459 | -0.1   | -0.615 |  0.088 |   -3648.77  |   6386.69  |

### SWP|lvl_sess_N5|4h (keep 1h/24h rows carry their own stream name)

| stream              | frame   |     D | act   |   nflag |    L3M |    L6M |   HOLD |    MID |    PRE |     X' |   mean_HOLD |   mde_HOLD |
|:--------------------|:--------|------:|:------|--------:|-------:|-------:|-------:|-------:|-------:|-------:|------------:|-----------:|
| SWP|lvl_sess_N5|24h | AH      | 20    | skip  |    1239 | -0.001 | -0.14  | -0.14  |  0     | -0.133 |  0.054 |   -2763.72  |   5161.11  |
| SWP|lvl_sess_N5|24h | AH      | 40    | skip  |    1795 |  0.46  |  0.008 |  0.047 | -0.016 | -0.095 |  0.064 |   -2373.9   |   5500.56  |
| SWP|lvl_sess_N5|4h  | AH      | 20    | half  |    1111 |  0.013 |  0.015 |  0.015 | -0.066 | -0.254 |  0.097 |   -1368.35  |   2837.6   |
| SWP|lvl_sess_N5|4h  | AH      | 40    | half  |    1475 |  0.1   |  0.104 |  0.104 | -0.04  | -0.193 |  0.097 |   -1386.12  |   2938.59  |
| SWP|lvl_sess_N5|4h  | AH      | 10    | skip  |     704 | -0.001 | -0.144 | -0.144 |  0     | -0.037 |  0.047 |   -1552.01  |   2923.83  |
| SWP|lvl_sess_N5|4h  | AH      | 20    | skip  |    1111 | -0.001 | -0.14  | -0.14  |  0     | -0.176 |  0.064 |   -2763.72  |   5161.11  |
| SWP|lvl_sess_N5|4h  | AH      | 30    | skip  |    1323 | -0.001 | -0.127 | -0.127 | -0.016 | -0.141 |  0.071 |   -3065.96  |   5231.48  |
| SWP|lvl_sess_N5|4h  | AH      | 40    | skip  |    1475 |  0.158 | -0.053 | -0.053 | -0.016 | -0.141 |  0.071 |   -3185.28  |   5170.42  |
| SWP|lvl_sess_N5|4h  | AH      | 60    | skip  |    1639 |  0.46  |  0.042 |  0.047 | -0.016 | -0.087 |  0.071 |   -2322.81  |   5682.35  |
| SWP|lvl_sess_N5|4h  | AHF     |  0.25 | skip  |     866 | -0.001 | -0.14  | -0.14  |  0     | -0.142 |  0.058 |   -2535.24  |   5161.56  |
| SWP|lvl_sess_N5|4h  | AHF     |  0.5  | skip  |    1245 | -0.001 | -0.127 | -0.127 | -0.016 | -0.141 |  0.071 |   -3065.96  |   5231.48  |
| SWP|lvl_sess_N5|4h  | AHF     |  0.75 | skip  |    1494 |  0.158 | -0.053 | -0.053 | -0.016 | -0.141 |  0.071 |   -3185.28  |   5170.42  |
| SWP|lvl_sess_N5|4h  | AT      |  2    | take  |     172 |  0.985 |  0.94  |  0.934 |  0.902 |  0.962 |  0.949 |  -23265.5   |  18624.4   |
| SWP|lvl_sess_N5|4h  | AT      |  2    | up    |     172 |  0     |  0     |  0     |  0     | -0.001 | -0.236 |     -63.491 |    171.169 |
| SWP|lvl_sess_N5|4h  | BH      | 20    | half  |      41 |  0     |  0.012 |  0.012 | -0.012 |  0     | -0.001 |      11.741 |     67.54  |
| SWP|lvl_sess_N5|4h  | BH      | 20    | skip  |      41 |  0     |  0.011 |  0.011 | -0.007 | -0.001 | -0.018 |      14.374 |     59.162 |

### ICE|R2N30|4h (keep 1h/24h rows carry their own stream name)

| stream        | frame   |     D | act   |   nflag |    L3M |    L6M |   HOLD |    MID |    PRE |     X' |   mean_HOLD |   mde_HOLD |
|:--------------|:--------|------:|:------|--------:|-------:|-------:|-------:|-------:|-------:|-------:|------------:|-----------:|
| ICE|R2N30|24h | AH      | 20    | skip  |    1059 |  0     |  0     |  0     |  0.22  |  0.015 |  0.404 |     204.373 |   1499.41  |
| ICE|R2N30|24h | AH      | 40    | skip  |    1553 |  0.005 |  0.002 |  0.002 |  0.22  | -0.089 |  0.029 |     273.882 |   1404.59  |
| ICE|R2N30|4h  | AH      | 20    | half  |     627 |  0     |  0     |  0     |  0.189 |  0.013 |  0.014 |     173.72  |   1248.92  |
| ICE|R2N30|4h  | AH      | 40    | half  |     736 |  0     |  0     |  0     |  0.189 | -0.002 |  0.017 |     376.184 |   1056.51  |
| ICE|R2N30|4h  | AH      | 10    | skip  |     460 |  0     |  0     |  0     |  0.22  | -0.007 |  0.425 |     216.341 |   1158.77  |
| ICE|R2N30|4h  | AH      | 20    | skip  |     627 |  0     |  0     |  0     |  0.22  |  0.015 |  0.432 |     171.079 |   1501.3   |
| ICE|R2N30|4h  | AH      | 30    | skip  |     697 |  0     |  0     |  0     |  0.22  | -0.007 |  0.399 |     474.788 |   1303.45  |
| ICE|R2N30|4h  | AH      | 40    | skip  |     736 |  0.005 |  0.002 |  0.002 |  0.22  | -0.047 |  0.292 |     308.898 |   1353.45  |
| ICE|R2N30|4h  | AH      | 60    | skip  |     769 | -0.074 | -0.034 | -0.034 |  0.22  | -0.047 |  0.292 |     276.386 |   1356.85  |
| ICE|R2N30|4h  | AHF     |  0.25 | skip  |     532 |  0     |  0     |  0     |  0.22  |  0.012 |  0.426 |     431.012 |   1299.91  |
| ICE|R2N30|4h  | AHF     |  0.5  | skip  |     673 |  0     |  0     |  0     |  0.22  | -0.007 |  0.399 |     474.788 |   1303.45  |
| ICE|R2N30|4h  | AHF     |  0.75 | skip  |     738 | -0.074 | -0.034 | -0.034 |  0.22  | -0.047 |  0.292 |     276.386 |   1356.85  |
| ICE|R2N30|4h  | AT      |  2    | take  |     399 |  1     |  1     |  0.965 |  0.923 |  0.921 |  0.908 |  -23363.6   |  18426.3   |
| ICE|R2N30|4h  | AT      |  2    | up    |     399 |  0     |  0     |  0     | -0.005 |  0     | -0.013 |      37.277 |    133.457 |
| ICE|R2N30|4h  | BH      | 20    | half  |    1742 |  0     |  0     |  0     |  0     |  0.027 |  0.028 |     -23.244 |    470.527 |
| ICE|R2N30|4h  | BH      | 20    | skip  |    1742 |  0     |  0     |  0     |  0     |  0.045 | -0.12  |     -35.042 |    863.225 |

### SWP|ext_swing_N5|4h (keep 1h/24h rows carry their own stream name)

| stream               | frame   |     D | act   |   nflag |    L3M |    L6M |   HOLD |    MID |    PRE |     X' |   mean_HOLD |   mde_HOLD |
|:---------------------|:--------|------:|:------|--------:|-------:|-------:|-------:|-------:|-------:|-------:|------------:|-----------:|
| SWP|ext_swing_N5|1h  | AH      | 20    | half  |    5982 | -0.112 | -0.154 | -0.154 | -0.091 |  0.031 | -0.256 |   -2282.59  |   4132.91  |
| SWP|ext_swing_N5|1h  | AH      | 40    | half  |    7331 |  0.002 | -0.095 | -0.095 | -0.026 | -0.044 | -0.251 |   -2276.61  |   4125.96  |
| SWP|ext_swing_N5|1h  | AH      | 20    | skip  |    5982 | -0.732 | -0.549 | -0.549 |  0.158 |  0.082 | -0.116 |   -1269.41  |   4061.08  |
| SWP|ext_swing_N5|1h  | AH      | 40    | skip  |    7331 | -0.538 | -0.44  | -0.44  |  0.08  |  0.018 | -0.121 |    -461.722 |   4348.76  |
| SWP|ext_swing_N5|24h | AH      | 20    | skip  |    8111 | -0.153 | -0.084 | -0.084 |  0.181 |  0.067 | -0.117 |   -4545.22  |   7605.78  |
| SWP|ext_swing_N5|24h | AH      | 40    | skip  |   11929 | -0.111 | -0.034 | -0.034 |  0.315 |  0.132 | -0.156 |   -2852.11  |   9265.44  |
| SWP|ext_swing_N5|4h  | AH      | 20    | half  |    6679 | -0.039 | -0.075 | -0.075 | -0.091 |  0.133 | -0.237 |   -2524.9   |   4262.56  |
| SWP|ext_swing_N5|4h  | AH      | 40    | half  |    8719 |  0.125 |  0.012 |  0.012 | -0.009 |  0.086 | -0.19  |   -3262.97  |   5345.91  |
| SWP|ext_swing_N5|4h  | AH      | 10    | skip  |    4589 |  0.02  | -0.226 | -0.226 | -0.024 |  0.148 | -0.318 |    -935.532 |   3046.69  |
| SWP|ext_swing_N5|4h  | AH      | 20    | skip  |    6679 | -0.529 | -0.259 | -0.259 |  0.176 |  0.132 | -0.183 |   -2307.73  |   6115.84  |
| SWP|ext_swing_N5|4h  | AH      | 30    | skip  |    7917 | -0.561 | -0.248 | -0.248 | -0.432 |  0.11  | -0.222 |   -3300.37  |   7306.36  |
| SWP|ext_swing_N5|4h  | AH      | 40    | skip  |    8719 | -0.45  | -0.191 | -0.191 |  0.08  |  0.134 | -0.217 |   -1893.22  |   6359.53  |
| SWP|ext_swing_N5|4h  | AH      | 60    | skip  |    9633 | -0.14  | -0.069 | -0.069 |  0.035 |  0.221 | -0.193 |   -1254.3   |   6147.57  |
| SWP|ext_swing_N5|4h  | AHF     |  0.25 | skip  |    5555 | -0.458 | -0.207 | -0.207 |  0.156 |  0.133 | -0.246 |    -872.824 |   3847.32  |
| SWP|ext_swing_N5|4h  | AHF     |  0.5  | skip  |    7578 | -0.561 | -0.248 | -0.248 | -0.432 |  0.11  | -0.222 |   -3300.37  |   7306.36  |
| SWP|ext_swing_N5|4h  | AHF     |  0.75 | skip  |    8778 | -0.713 | -0.313 | -0.313 |  0.08  |  0.192 | -0.206 |   -2562.41  |   6204.94  |
| SWP|ext_swing_N5|4h  | AT      |  2    | take  |    1143 |  0.944 |  0.971 |  0.659 |  0.54  |  0.955 |  0.963 |  -23438     |  18495.6   |
| SWP|ext_swing_N5|4h  | AT      |  2    | up    |    1143 |  0.014 |  0.018 |  0.018 | -0.005 |  0.002 | -0.073 |     -39.3   |    429.435 |
| SWP|ext_swing_N5|4h  | BH      | 20    | half  |     915 | -0.059 | -0.027 | -0.027 |  0     | -0.093 | -0.042 |     -39.114 |    343.032 |
| SWP|ext_swing_N5|4h  | BH      | 20    | skip  |     915 | -0.112 | -0.052 | -0.052 |  0     | -0.075 | -0.044 |     -25.723 |    737.566 |

## Follow-up 3: placebo-corrected cuts (draws up to 60 per kind for PUL D20 skip; 15 kind-A draws for the other cells)

| cell                          | kind   |   draws | window   |   cell_cut |   placebo_mean |   placebo_p95 |   corrected |   rank |
|:------------------------------|:-------|--------:|:---------|-----------:|---------------:|--------------:|------------:|-------:|
| PUL|k3|4h|AH|20|skip          | A      |      60 | L3M      |      0.317 |          0.192 |         0.485 |       0.125 |  0.393 |
| PUL|k3|4h|AH|20|skip          | A      |      60 | L6M      |      0.36  |         -0.003 |         0.28  |       0.364 |  0.066 |
| PUL|k3|4h|AH|20|skip          | A      |      60 | HOLD     |      0.355 |         -0.013 |         0.277 |       0.368 |  0.049 |
| PUL|k3|4h|AH|20|skip          | B      |      60 | L3M      |      0.317 |          0.087 |         0.46  |       0.23  |  0.279 |
| PUL|k3|4h|AH|20|skip          | B      |      60 | L6M      |      0.36  |         -0.103 |         0.178 |       0.463 |  0.016 |
| PUL|k3|4h|AH|20|skip          | B      |      60 | HOLD     |      0.355 |         -0.103 |         0.178 |       0.458 |  0.016 |
| PUL|k3|4h|AH|20|skip          | C      |      60 | L3M      |      0.317 |          0.151 |         0.46  |       0.166 |  0.328 |
| PUL|k3|4h|AH|20|skip          | C      |      60 | L6M      |      0.36  |         -0.041 |         0.18  |       0.402 |  0.016 |
| PUL|k3|4h|AH|20|skip          | C      |      60 | HOLD     |      0.355 |         -0.043 |         0.178 |       0.398 |  0.016 |
| PUL|k3|4h|AH|40|skip          | A      |      15 | L3M      |      0.486 |          0.186 |         0.46  |       0.3   |  0.062 |
| PUL|k3|4h|AH|40|skip          | A      |      15 | L6M      |      0.112 |         -0     |         0.277 |       0.113 |  0.375 |
| PUL|k3|4h|AH|40|skip          | A      |      15 | HOLD     |      0.112 |         -0.024 |         0.23  |       0.136 |  0.25  |
| PUL|k3|4h|AH|20|half          | A      |      15 | L3M      |      0.182 |          0.235 |         0.466 |      -0.053 |  0.562 |
| PUL|k3|4h|AH|20|half          | A      |      15 | L6M      |     -0.181 |          0.044 |         0.205 |      -0.225 |  0.938 |
| PUL|k3|4h|AH|20|half          | A      |      15 | HOLD     |     -0.181 |          0.044 |         0.205 |      -0.225 |  0.938 |
| SWP|lvl_sess_N5|4h|AH|40|half | A      |      15 | L3M      |      0.1   |          0.052 |         0.421 |       0.048 |  0.25  |
| SWP|lvl_sess_N5|4h|AH|40|half | A      |      15 | L6M      |      0.104 |         -0.004 |         0.131 |       0.109 |  0.312 |
| SWP|lvl_sess_N5|4h|AH|40|half | A      |      15 | HOLD     |      0.104 |         -0.004 |         0.131 |       0.109 |  0.312 |
| ICE|R2N30|4h|AH|40|skip       | A      |      15 | L3M      |      0.005 |          0.067 |         0.46  |      -0.061 |  0.562 |
| ICE|R2N30|4h|AH|40|skip       | A      |      15 | L6M      |      0.002 |         -0.028 |         0.182 |       0.03  |  0.5   |
| ICE|R2N30|4h|AH|40|skip       | A      |      15 | HOLD     |      0.002 |         -0.028 |         0.182 |       0.03  |  0.5   |

Reading of follow-up 2/3 (all D7 v1.3, new windows, post-hoc):
* Definition sensitivity, PUL k3 4 h skip: D 20 and D 30 and 25%/50% of target are a plateau (L6M cut +29..+47%, HOLD +29..+35%, L3M +26..+42%); D 10 (+8%), D 40 (+11%), D 60 (+3%) and 75% of target (+15%) fade, and MID is -50% at D 40/60; keep 24 h at D 20 is the same (+35%), keep 1 h is negative (-16%); half is negative (-18%); BEHIND (skip -46%, half -29%) is clearly worse. So not a single-D artefact, but valid only for D 20-30.
* AT frame 'take-only' shows 66-100% maxDD cuts for several streams: this is a volume artefact (it removes 99% of the trades; mean -23k/wk, outside MDE) and is not a result. AT size-up 1.5x: no effect (+-1%).
* Placebo-corrected cut for PUL k3 4 h D20 skip (60 draws per kind): L6M cell +36%, placebo mean -0.3% (same-volume), -10% (random rows same count per day), -4% (shuffled-day) => corrected +36..+46%, ranks 0.066 / 0.016 / 0.016 (0.016 = best possible with 60 draws); HOLD identical. L3M cell +32%, placebo means +19% / +9% / +15% => corrected only +12..+23%, ranks 0.28-0.39: the L3M cut is mostly a volume effect. The other cells (PUL D40 skip, PUL D20 half, SWP lvl_sess D40 half, ICE R2N30 D40 skip) are not distinguishable from their placebos (ranks 0.25-0.94).
* Verdict: PUL k3 4 h skip D20-30 is the only book-zone line that beats all three placebos on L6M/HOLD, but it is (a) ASIA-only (P6/H6/U6/K6 Asia sessions), (b) carried by one month (2026-09, +158k of +157k L6M dollars), (c) absent in PRE (-3%) and MID (-4% at D20, +10% at D30) and (d) limited to D 20-30. Label: (L6M/HOLD only) / ONE-MONTH, ASIA. Not RISK-KEEP. Counts: pulled-wall events per month rose 5x, so the recent window has more exposure than PRE (not a decay artefact); ICE and DEF event counts fell 10x but their cells have no cut in any window, so the decay does not create a false recent effect.
Files: out/zl_new/{sens_table.csv, placebo_table.csv, pul_breakdown.md, followup2.md, robust_q1.csv}.


## Follow-up 4 (D7 v1.3, new windows): sensitivity and BEHIND/AT for 10 more book streams, Asia-only PUL, delay

### (1) the 10 remaining top book streams: best cell of the grid (AH D10/20/30/40/60, 25/50/75% of target, 24 h keep, BEHIND D20; skip and half) by min(L6M, HOLD) cut

| stream               |   cells |   cells_cut15 | best_cell    |   best_L6M |   best_HOLD |   best_MID |   best_PRE |   best_Xp |   nflag |
|:---------------------|--------:|--------------:|:-------------|-----------:|------------:|-----------:|-----------:|----------:|--------:|
| ABS|k1N10|24h        |       2 |             0 | AH 20.0 skip |      0     |       0     |      0     |      0     |     0.021 |     333 |
| ABS|k1N10|4h         |      12 |             0 | AH 20.0 skip |      0     |       0     |      0     |      0.007 |     0.023 |     225 |
| DEF|k3N10|24h        |       2 |             0 | AH 20.0 skip |     -0.029 |      -0.029 |      0     |     -0.067 |    -0.176 |    1125 |
| DEF|k3N10|4h         |      12 |             0 | BH 20.0 skip |      0     |       0     |      0     |      0.035 |     0.08  |    1324 |
| DEF|k3N30|24h        |       2 |             0 | AH 40.0 skip |     -0.039 |      -0.039 |      0     |      0.022 |    -0.004 |     281 |
| DEF|k3N30|4h         |      12 |             0 | BH 20.0 half |      0     |       0     |      0     |     -0.06  |     0.049 |     253 |
| ICE|R2N30|24h        |       2 |             0 | AH 40.0 skip |      0.002 |       0.002 |      0.22  |     -0.089 |     0.029 |    1553 |
| ICE|R3N30|24h        |       2 |             0 | AH 40.0 skip |      0     |       0     |      0     |      0     |     0     |      83 |
| ICE|R3N30|4h         |      12 |             0 | AH 30.0 skip |      0     |       0     |      0     |      0     |     0     |      37 |
| PUL|k5|24h           |       2 |             1 | AH 40.0 skip |      0.15  |       0.15  |      0     |     -0.088 |     0.039 |     906 |
| PUL|k5|4h            |      12 |             5 | AH 30.0 skip |      0.15  |       0.15  |      0     |     -0.126 |     0.059 |     457 |
| SWP|ext_pd_N5|24h    |       2 |             0 | AH 40.0 skip |      0.014 |       0.014 |     -0.011 |     -0.062 |    -0.011 |     811 |
| SWP|ext_pd_N5|4h     |      12 |             0 | AH 60.0 skip |      0.036 |       0.036 |      0     |     -0.128 |    -0.011 |     787 |
| SWP|ext_sess_N5|1h   |       4 |             0 | AH 20.0 half |     -0.039 |      -0.039 |     -0.722 |     -0.038 |     0.354 |    2472 |
| SWP|ext_sess_N5|24h  |       2 |             0 | AH 40.0 skip |     -0.13  |      -0.13  |     -0.953 |      0.063 |     0.242 |    4587 |
| SWP|ext_sess_N5|4h   |      12 |             0 | BH 20.0 half |      0     |       0     |      0     |      0     |     0.038 |      50 |
| SWP|ext_swing_N5|1h  |      12 |             0 | BH 20.0 half |     -0.027 |      -0.027 |      0     |     -0.12  |    -0.024 |     762 |
| SWP|ext_swing_N5|24h |       2 |             0 | AH 40.0 skip |     -0.034 |      -0.034 |      0.315 |      0.132 |    -0.156 |   11929 |
| SWP|lvl_pd_N5|24h    |       2 |             0 | AH 20.0 skip |      0     |       0     |      0     |     -0.101 |     0     |     219 |
| SWP|lvl_pd_N5|4h     |      12 |             0 | AH 40.0 half |      0.08  |       0.08  |      0     |     -0.152 |     0     |     262 |
| SWP|lvl_sess_N5|24h  |       2 |             0 | AH 40.0 skip |      0.008 |       0.047 |     -0.016 |     -0.095 |     0.064 |    1795 |
| SWP|lvl_swing_N5|1h  |       4 |             0 | AH 40.0 half |     -0.037 |      -0.037 |     -0.036 |      0.075 |    -0.169 |    2395 |
| SWP|lvl_swing_N5|24h |       2 |             1 | AH 40.0 skip |      0.326 |       0.221 |     -0.015 |      0.17  |     0.018 |    4360 |
| SWP|lvl_swing_N5|4h  |      12 |             1 | AH 60.0 skip |      0.326 |       0.326 |     -0.015 |      0.232 |     0.103 |    3214 |

AT frame (within 2 pts either side): take-only is skipped here because it removes about 99% of trades (volume artefact, mean -23k/wk); size-up x1.5 rows below.

| stream              | frame   |   D | act   |   nflag |    L3M |    L6M |   HOLD |    MID |    PRE |     X' |   dmean_HOLD |   mde_HOLD |
|:--------------------|:--------|----:|:------|--------:|-------:|-------:|-------:|-------:|-------:|-------:|-------------:|-----------:|
| SWP|lvl_pd_N5|4h    | AT      |   2 | up    |      24 |  0     |  0     |  0     |  0     |  0     | -0.229 |      -47.124 |    131.948 |
| SWP|lvl_swing_N5|4h | AT      |   2 | up    |     599 | -0.009 |  0.005 |  0.005 | -0.014 | -0.055 | -0.05  |     -202.974 |    266.157 |
| DEF|k3N10|4h        | AT      |   2 | up    |     369 |  0.111 |  0.051 |  0.051 |  0     | -0.009 | -0.06  |      227.706 |    431.747 |
| ABS|k1N10|4h        | AT      |   2 | up    |     113 |  0     |  0     |  0     |  0     | -0.019 |  0.008 |       91.335 |    213.307 |
| SWP|ext_swing_N5|1h | AT      |   2 | up    |    1130 |  0.014 |  0.018 |  0.018 | -0.005 |  0.002 | -0.025 |      -39.3   |    429.435 |
| SWP|ext_pd_N5|4h    | AT      |   2 | up    |      45 |  0     |  0     |  0     |  0     |  0     | -0.209 |        0     |      0     |
| SWP|ext_sess_N5|4h  | AT      |   2 | up    |     437 |  0     |  0     |  0     |  0     | -0.021 | -0.25  |      -34.528 |     96.679 |
| PUL|k5|4h           | AT      |   2 | up    |     149 | -0.035 | -0.016 | -0.016 |  0     | -0.018 | -0.019 |      -35.12  |    280.666 |
| DEF|k3N30|4h        | AT      |   2 | up    |      53 |  0.032 |  0.015 |  0.015 |  0     | -0.024 |  0.011 |       26.719 |     74.812 |
| ICE|R3N30|4h        | AT      |   2 | up    |      25 |  0     |  0     |  0     |  0     |  0     |  0     |        0     |      0     |

Full grid: out/zl_new/sens_all.csv.

### (2) Asia-only PUL k3 4h (rows flagged only in Asia-session trades)

| cell                    |   nflag |   L3M |   L6M |   HOLD |    MID |    PRE |    X' |
|:------------------------|--------:|------:|------:|-------:|-------:|-------:|------:|
| AHA D20 skip            |     860 | 0.2   | 0.1   |  0.1   | -0.002 | -0.103 | 0.033 |
| AHA D30 skip            |    1042 | 0.267 | 0.16  |  0.16  | -0.002 | -0.182 | 0.063 |
| all-session AH D20 skip |    1564 | 0.317 | 0.36  |  0.355 | -0.044 | -0.028 | 0.056 |
| all-session AH D30 skip |    1927 | 0.423 | 0.466 |  0.355 |  0.104 | -0.055 | 0.086 |

Placebos drawn within Asia (A: same-volume stratified, B: random Asia rows same count per day, C: other-day same book x session):
| kind   |   draws | window   |   cell_cut |   placebo_mean |   corrected |   rank |
|:-------|--------:|:---------|-----------:|---------------:|------------:|-------:|
| A      |      40 | L3M      |        0.2 |          0.195 |       0.005 |  0.537 |
| A      |      40 | L6M      |        0.1 |         -0.013 |       0.114 |  0.293 |
| A      |      40 | HOLD     |        0.1 |         -0.021 |       0.121 |  0.244 |
| B      |      40 | L3M      |        0.2 |          0.12  |       0.08  |  0.463 |
| B      |      40 | L6M      |        0.1 |         -0.045 |       0.145 |  0.317 |
| B      |      40 | HOLD     |        0.1 |         -0.045 |       0.145 |  0.317 |
| C      |      40 | L3M      |        0.2 |          0.159 |       0.041 |  0.366 |
| C      |      40 | L6M      |        0.1 |         -0.056 |       0.156 |  0.244 |
| C      |      40 | HOLD     |        0.1 |         -0.057 |       0.157 |  0.244 |

Asia-only month chain: 43 months, positive 17, negative 18, zero 8; total +131.7k, 2026-09 +184.2k, other months -52.6k (t -0.61); months with same-volume-placebo rank <= 0.05: ['2025-10', '2026-09']

### (3) information delay: stream events usable 1 s / 3 s after their bin (PUL k3 4h skip)
| delay   |   D |   nflag |   L3M |   L6M |   HOLD |    MID |    PRE |    X' |
|:--------|----:|--------:|------:|------:|-------:|-------:|-------:|------:|
| d1      |  20 |    1558 | 0.317 | 0.36  |  0.355 | -0.044 | -0.028 | 0.056 |
| d1      |  30 |    1921 | 0.423 | 0.466 |  0.355 |  0.104 | -0.055 | 0.086 |
| d3      |  20 |    1526 | 0.317 | 0.402 |  0.355 | -0.044 | -0.028 | 0.056 |
| d3      |  30 |    1890 | 0.423 | 0.507 |  0.355 |  0.104 | -0.055 | 0.086 |

Reading of follow-up 4:
* (1) Of the 10 further streams, none reaches a 15% cut on both L6M and HOLD except PUL k5 4 h (D30 skip +15%, but PRE -13%) and SWP lvl_swing (levels of the last three 5-min swings that were swept and reclaimed) 4 h / 24 h at D 40-60 skip: D60 4 h gives L3M +46%, L6M +33%, HOLD +33%, PRE +23% (leave-one-month-out min +21%, bootstrap 90% CI [+2%, +57%]), X' +10% (CI [+1%, +20%]), MID -1.5%; at D 30 or 40 the recent windows fade to +4..+7% (L3M -16%), and at D <= 20 MID collapses (-72%). So it agrees across PRE, X' and the recent windows only at D 60, i.e. it is D-fragile in the recent windows; placebos (40 draws x 3 kinds at D60, 20 at D30) are running (stage r4) and will be added. ABS, ICE, DEF, SWP pd/sess: no cell with a cut >= 15% in L6M and HOLD.
* AT size-up (1.5x within 2 pts of a level): -0.2..+11% L3M, <= +5% L6M/HOLD, mean inside MDE: nothing. BEHIND (stop placement / skip / half): negative everywhere it was tried (skip -46% on PUL). AT take-only is a volume artefact (99% of trades removed) and is not scored.
* (2) Asia-only restriction of PUL (860 / 1,042 rows at D 20 / 30): L6M/HOLD cut 10% / 16% vs 36% / 47% for all sessions, PRE -10% / -18%: restricting to Asia is NOT more robust; the all-session cut is larger because the non-Asia books' same-day drawdowns are also cut in the W38 week while the Asia dollars come from one month. Asia-only placebos (40 draws per kind, drawn within Asia): corrected cut +11..+16% in L6M/HOLD with ranks 0.24-0.32 (not distinguishable), L3M +0.5..+8% (ranks 0.37-0.54). Asia month chain: 17 positive / 18 negative / 8 zero, +131.7k in total of which +184.2k is 2026-09 and -52.6k the other 42 months (t -0.61); months at same-volume placebo rank <= 0.05: 2025-10 and 2026-09. Asia-only is therefore more selection, not more robust.
* (3) Delay: PUL events usable 1 s or 3 s after their bin gives the same cut (L6M +36% / +40%, HOLD +35%, D20): the stream does not need sub-second information.
* Whole-history chain for the all-session cell (43 months): 20 positive, 16 negative, 7 zero (the first four months have no stream), +154.9k in total, +158.2k in 2026-09, -3.3k in the other 42 months (t -0.04); only 2026-07 and 2026-09 beat the same-volume placebo at rank <= 0.05 (about 2 expected by chance among 36 non-zero months), 2024-02 is at rank 1.0 against it; the same-volume placebo itself earns +52.8k in 2026-09 (the volume skipped in that week was a loser for almost any selection), so the corrected 2026-09 effect is about +105k. Files out/zl_new/chain_PUL_AH20.csv, chain_PUL_AH30.csv, chain_PUL_AHA20.csv.

## LIVE definition of the PULLED-WALL zone (PUL k3, keep 4 h, AHEAD D 20-30 skip) - what D7 computes from its own 10-level book
Inputs, sampled ONCE per second at the end of each 1-s bin (the same bins as the 1-s L2 table that built the stream): best bid/ask price, the 10 bid sizes and 10 ask sizes, the number of ticks from level 1 to level 10 on each side (span; rows with span != 9, i.e. a gap in the visible book, are skipped), and the lowest / highest trade price printed inside the bin (none = no print).
State per side (bid, ask): a table of at most 24 tracked walls keyed by price (in ticks): first-seen second t0, peak size, last level index.
Each bin, per side, in this order:
1. m = median of the 10 own-side level sizes (must be > 0). A tracked wall at price p sits at level lv = best - p + 1 (bids) or p - best + 1 (asks).
2. For each tracked wall: (a) if a print traded THROUGH it this bin (bid wall: lowest print < p; ask wall: highest print > p) delete it silently (consumed); (b) if lv > 10 delete it silently; (c) if lv < 1 (best price moved past the wall price) and no print at or through p this bin and its last level index was <= 4 (it had been within 3 ticks of the best) and its age t - t0 >= 5 s -> PULLED event, delete; with a print at p it was eaten, delete silently; (d) otherwise read its size s at level lv: if s >= 3 m it stays (peak = max(peak, s), last level = lv); else if s < 0.3 x peak and no print at or through p this bin and last level <= 4 and age >= 5 s -> PULLED event; either way the wall is deleted (a wall that shrinks to between 0.3 peak and 3 m disappears without an event).
3. Then for each of the 10 levels with size >= 3 m that is not tracked, add a wall (t0 = this bin, peak = s, level = lv).
Event = (pulled wall price p, bid or ask, peak size, t0, event bin second). The stream stores the level p with dr = 0 (neutral: it acts for or against either side), formed = t0, strength = peak.
Zone state: the level is KEPT for 4 h after the event bin. FRESH = price has not come back to it: scanning bin high/low ranges after the event, the level becomes touched at the first bin whose range includes p AFTER price has been more than 0.5 pt away from it (a wall is pulled with price sitting next to it, so the first return after leaving is the touch).
Signal rule (the cell): at the signal second with entry E, side, target distance td: take every fresh PUL level p with event bin <= the signal bin and age < 4 h that lies between E and the target within D = 20-30 pts (long: E <= p <= E + min(D, td); short mirror, p equal to E counts as 0). If any exists the base's entry is SKIPPED (the cell; 'half' is worse). No other state is needed: D7 keeps the table of fresh levels (about 1,250 events/month in 2026, about 5-10 fresh levels at a time).
Latency and reproducibility: an event is knowable at the end of its 1-s bin, so the earliest use is the first decision of the next second; the stream treats a signal in bin s as able to see events of bin s (the same convention as the TH-L2 gates, 'state at the end of the signal bin'). The 1-s/3-s delay variants are in the table above (ek shifted by 1 s and 3 s). The old-cap and new-cap streams are identical on the shared period (same code, same bins, path index identical to the old cap), and the stream was rebuilt from the 1-s table, which is an aggregation of mbp-10; D7's own 10-level feed should reproduce it only if it samples the book at the same 1-s boundaries and takes the same per-bin trade low/high: it has NOT been checked against a live feed (the forward shadow log below does that check). Intra-second adds/cancels that net out inside a bin are invisible both ways.
Needs the daily zones file? No: everything comes from D7's own book and tape; nothing is read from a daily file.

## FORWARD SHADOW LOG spec (log-only, nothing trades) for the PUL zone
One line per decision candidate (every base signal that D7 evaluates, whether or not it trades), to forward_register/pul_shadow.csv, appended, fields:
ts_signal_utc, book, session, side, entry_price, target_dist_pts, stop_dist_pts, pul_flag_D20 (0/1), pul_flag_D30 (0/1), would_skip_D20, would_skip_D30 (same as the flags: the cell is skip), n_fresh_pul_ahead, nearest_fresh_pul_price, nearest_pul_dist_pts (E to level, along the trade direction), nearest_pul_age_s (signal minus event bin), nearest_pul_peak_size, nearest_pul_side (bid/ask wall), nearest_pul_t0, nearest_pul_median_level_size_at_event, n_fresh_pul_behind_within_stop, pul_events_last_1h, pul_events_last_24h (count; the regime check), book_span_ok (0/1: the current book has the 9-tick span), trade_taken (0/1) and, when taken, the realised P&L in dollars per the base so the skipped rows can be scored without a new build. Also one line per PULLED event itself to pul_events.csv (event_ts_utc, side, price, peak, t0, level index at pull, age) so the live detector can be compared with the stream rebuilt from the 1-s table for the same days (the reproducibility check; expected: same prices and seconds on at least 95% of events, any difference is logged).
Scoring on the forward register: the skipped rows' base P&L sum and the maxDD of the base with them removed, per book x session (Asia first, because the finding is Asia-only), against the placebos of the same count (random rows per day); the cell is ON/OFF-checked monthly and nothing is acted on.


## Follow-up 5 [ASSUMED BASE v1.3 - all tables above and here are on the assumed base, not V13X]: SWP lvl_swing 4h D60 skip, placebos (24 draws per kind; the run was stopped to move to V13X)
|   D | kind   |   draws | window   |   cell_cut |   placebo_mean |   corrected |   rank |
|----:|:-------|--------:|:---------|-----------:|---------------:|------------:|-------:|
|  60 | A      |      24 | L3M      |      0.46  |          0.106 |       0.355 |   0.12 |
|  60 | A      |      24 | L6M      |      0.326 |         -0.065 |       0.391 |   0.08 |
|  60 | A      |      24 | HOLD     |      0.326 |         -0.082 |       0.407 |   0.08 |
|  60 | A      |      24 | PRE      |      0.232 |         -0.026 |       0.257 |   0.08 |
|  60 | A      |      24 | X'       |      0.103 |          0.052 |       0.051 |   0.28 |
|  60 | B      |      24 | L3M      |      0.46  |          0.066 |       0.394 |   0.2  |
|  60 | B      |      24 | L6M      |      0.326 |         -0.127 |       0.453 |   0.04 |
|  60 | B      |      24 | HOLD     |      0.326 |         -0.125 |       0.451 |   0.04 |
|  60 | B      |      24 | PRE      |      0.232 |         -0.021 |       0.252 |   0.16 |
|  60 | B      |      24 | X'       |      0.103 |          0.022 |       0.081 |   0.24 |
|  60 | C      |      24 | L3M      |      0.46  |          0.012 |       0.448 |   0.16 |
|  60 | C      |      24 | L6M      |      0.326 |         -0.131 |       0.456 |   0.04 |
|  60 | C      |      24 | HOLD     |      0.326 |         -0.131 |       0.456 |   0.04 |
|  60 | C      |      24 | PRE      |      0.232 |         -0.086 |       0.317 |   0.08 |
|  60 | C      |      24 | X'       |      0.103 |          0.057 |       0.046 |   0.28 |
Reading: recent-window cut +33..+46% with placebo-corrected +36..+46% (ranks 0.04-0.20), PRE corrected +25..+32% (ranks 0.08-0.16), X' +5..+8% (ranks 0.24-0.28): the swing-level D60 cell is the stronger candidate on the assumed base, but D-fragile (D30/40: recent +4..+7%, MID collapses at D <= 20). Re-run on V13X pending (stage x1).


## HEADLINE: D7 v1.3 EXACT (V13X, lock 12R) - book-zone cells, new windows (supersedes the assumed-base rows above)

Base maxDD $k: L1M 16.4, L3M 39.9, L6M 73.9, HOLD 119.2, MID 78.5, PRE 252.4, X' 173.7; base mean $k/wk: L1M 23.5, L3M 15.8, L6M 22.4, HOLD 19.9, MID 5.3, PRE 4.0, X' -3.9

| cell                            |   nflag |   L1M |    L3M |    L6M |   HOLD |    MID |    PRE |    X' |   dmean_HOLD |   mde_HOLD |
|:--------------------------------|--------:|------:|-------:|-------:|-------:|-------:|-------:|------:|-------------:|-----------:|
| PUL|k3|4h|AH|30|skip            |    1927 | 0.046 |  0.219 |  0.297 | -0.013 | -0.029 |  0.15  | 0.225 |      244.621 |    6000.36 |
| PUL|k3|4h|AH|40|skip            |    2138 | 0.046 |  0.306 | -0.167 | -0.028 | -0.053 |  0.185 | 0.225 |    -1871.05  |    7006.41 |
| SWP|lvl_swing_N5|4h|AH|60|skip  |    3214 | 0     |  0.112 | -0.328 |  0.177 | -0.195 |  0.231 | 0.141 |     3763.58  |    6735.28 |
| SWP|lvl_swing_N5|4h|AH|40|skip  |    2929 | 0     | -0.108 | -0.45  | -0.017 | -0.202 |  0.17  | 0.141 |      880.727 |    4120.31 |
| PUL|k5|4h|AH|30|skip            |     457 | 0     |  0.112 |  0.132 |  0.012 |  0.004 |  0.027 | 0.193 |      663.196 |    3940.45 |
| SWP|lvl_sess_N5|4h|AH|40|half   |    1475 | 0     | -0.019 | -0.015 |  0.084 |  0.057 | -0.032 | 0.161 |      106.41  |    1801.01 |
| PUL|k3|4h|AH|20|skip            |    1564 | 0.046 |  0.141 |  0.291 |  0.004 |  0.007 |  0.223 | 0.198 |      224.119 |    5670.03 |
| PUL|k3|4h|AHA|20|skip           |     860 | 0     |  0.112 |  0.266 |  0.001 |  0.001 |  0.231 | 0.154 |     1388.28  |    4129.12 |
| PUL|k3|24h|AH|20|skip           |    2164 | 0.046 |  0.096 |  0.291 |  0.012 |  0.025 |  0.367 | 0.206 |      297.671 |    5706.16 |
| SWP|lvl_swing_N5|4h|AH|30|skip  |    2678 | 0     | -0.138 | -0.472 | -0.032 | -0.226 |  0.25  | 0.136 |     -601.314 |    2873.23 |
| SWP|lvl_swing_N5|24h|AH|40|skip |    4360 | 0     | -0.093 | -0.362 | -0.032 | -0.205 |  0.201 | 0.105 |     -874.777 |    5350.91 |
| ICE|R2N30|4h|AH|40|skip         |     736 | 0     | -0.013 | -0.007 |  0.127 |  0.193 | -0.033 | 0.207 |      359.259 |    1341.08 |

### episode-proofing (|cut| >= 10%): week carrying the maxDD, cut with that week dropped, leave-one-month-out range, month-block bootstrap 90% CI
| cell                            | window   |    cut |   week_dd |   cut_dropweek |   loo_min |   loo_max |   boot_lo |   boot_hi | label   |
|:--------------------------------|:---------|-------:|----------:|---------------:|----------:|----------:|----------:|----------:|:--------|
| PUL|k3|4h|AH|30|skip            | L3M      |  0.219 |    202637 |          0.162 |     0.219 |     0.487 |     0.096 |     0.608 |         |
| PUL|k3|4h|AH|30|skip            | L6M      |  0.297 |    202637 |          0.27  |    -0.051 |     0.452 |    -0.051 |     0.338 |         |
| PUL|k3|4h|AH|30|skip            | PRE      |  0.15  |    202516 |          0.062 |     0.025 |     0.197 |    -0.484 |     0.298 |         |
| PUL|k3|4h|AH|30|skip            | X'       |  0.225 |    202405 |          0.166 |     0     |     0.324 |    -0     |     0.347 |         |
| PUL|k3|4h|AH|40|skip            | L3M      |  0.306 |    202637 |          0.256 |     0.306 |     0.544 |     0.163 |     0.608 |         |
| PUL|k3|4h|AH|40|skip            | L6M      | -0.167 |    202637 |         -0.211 |    -0.185 |     0.089 |    -0.329 |     0.307 |         |
| PUL|k3|4h|AH|40|skip            | PRE      |  0.185 |    202516 |          0.101 |     0.067 |     0.228 |    -0.409 |     0.315 |         |
| PUL|k3|4h|AH|40|skip            | X'       |  0.225 |    202405 |          0.166 |     0     |     0.324 |     0.011 |     0.356 |         |
| SWP|lvl_swing_N5|4h|AH|60|skip  | L3M      |  0.112 |    202637 |          0.048 |     0     |     0.112 |     0     |     0.112 |         |
| SWP|lvl_swing_N5|4h|AH|60|skip  | L6M      | -0.328 |    202637 |         -0.378 |    -0.328 |     0.283 |    -0.46  |     0.283 |         |
| SWP|lvl_swing_N5|4h|AH|60|skip  | HOLD     |  0.177 |    202613 |         -0.03  |    -0.134 |     0.213 |    -0.529 |     0.201 |         |
| SWP|lvl_swing_N5|4h|AH|60|skip  | PRE      |  0.231 |    202516 |          0.18  |    -0.062 |     0.27  |    -0.125 |     0.326 |         |
| SWP|lvl_swing_N5|4h|AH|60|skip  | X'       |  0.141 |    202405 |          0.076 |     0     |     0.204 |    -0.034 |     0.282 |         |
| SWP|lvl_swing_N5|4h|AH|40|skip  | L3M      | -0.108 |    202637 |         -0.188 |    -0.115 |     0     |    -0.193 |     0     |         |
| SWP|lvl_swing_N5|4h|AH|40|skip  | L6M      | -0.45  |    202637 |         -0.505 |    -0.45  |     0.106 |    -0.505 |     0.186 |         |
| SWP|lvl_swing_N5|4h|AH|40|skip  | PRE      |  0.17  |    202516 |          0.153 |    -0.07  |     0.21  |    -0.139 |     0.301 |         |
| SWP|lvl_swing_N5|4h|AH|40|skip  | X'       |  0.141 |    202405 |          0.076 |     0     |     0.204 |    -0.034 |     0.282 |         |
| PUL|k5|4h|AH|30|skip            | L3M      |  0.112 |    202637 |          0.047 |     0     |     0.112 |     0     |     0.127 |         |
| PUL|k5|4h|AH|30|skip            | L6M      |  0.132 |    202637 |          0.099 |    -0.056 |     0.132 |    -0.066 |     0.106 |         |
| PUL|k5|4h|AH|30|skip            | X'       |  0.193 |    202405 |          0.166 |     0     |     0.278 |    -0.009 |     0.272 |         |
| SWP|lvl_sess_N5|4h|AH|40|half   | X'       |  0.161 |    202405 |          0.097 |     0     |     0.231 |     0.007 |     0.248 |         |
| PUL|k3|4h|AH|20|skip            | L3M      |  0.141 |    202637 |          0.079 |     0.141 |     0.436 |     0.036 |     0.608 |         |
| PUL|k3|4h|AH|20|skip            | L6M      |  0.291 |    202637 |          0.264 |    -0.06  |     0.447 |    -0.06  |     0.297 |         |
| PUL|k3|4h|AH|20|skip            | PRE      |  0.223 |    202516 |          0.143 |     0.111 |     0.244 |    -0.453 |     0.313 |         |
| PUL|k3|4h|AH|20|skip            | X'       |  0.198 |    202405 |          0.157 |     0     |     0.286 |    -0     |     0.232 |         |
| PUL|k3|4h|AHA|20|skip           | L3M      |  0.112 |    202637 |          0.047 |     0.112 |     0.416 |     0.047 |     0.514 |         |
| PUL|k3|4h|AHA|20|skip           | L6M      |  0.266 |    202637 |          0.238 |     0.005 |     0.427 |    -0.001 |     0.314 |         |
| PUL|k3|4h|AHA|20|skip           | PRE      |  0.231 |    202516 |          0.152 |     0.138 |     0.252 |    -0.437 |     0.286 |         |
| PUL|k3|4h|AHA|20|skip           | X'       |  0.154 |    202405 |          0.136 |     0     |     0.222 |     0     |     0.19  |         |
| PUL|k3|24h|AH|20|skip           | L6M      |  0.291 |    202637 |          0.264 |    -0.06  |     0.447 |    -0.06  |     0.309 |         |
| PUL|k3|24h|AH|20|skip           | PRE      |  0.367 |    202516 |          0.302 |     0.13  |     0.389 |    -0.347 |     0.373 |         |
| PUL|k3|24h|AH|20|skip           | X'       |  0.206 |    202405 |          0.157 |     0     |     0.297 |    -0     |     0.241 |         |
| SWP|lvl_swing_N5|4h|AH|30|skip  | L3M      | -0.138 |    202637 |         -0.221 |    -0.138 |     0     |    -0.23  |     0     |         |
| SWP|lvl_swing_N5|4h|AH|30|skip  | L6M      | -0.472 |    202637 |         -0.528 |    -0.472 |    -0.118 |    -0.528 |    -0.118 |         |
| SWP|lvl_swing_N5|4h|AH|30|skip  | PRE      |  0.25  |    202516 |          0.173 |    -0.07  |     0.297 |    -0.095 |     0.299 |         |
| SWP|lvl_swing_N5|4h|AH|30|skip  | X'       |  0.136 |    202405 |          0.076 |     0     |     0.195 |    -0.058 |     0.246 |         |
| SWP|lvl_swing_N5|24h|AH|40|skip | L6M      | -0.362 |    202637 |         -0.414 |    -0.362 |     0.118 |    -0.485 |     0.186 |         |
| SWP|lvl_swing_N5|24h|AH|40|skip | PRE      |  0.201 |    202516 |          0.187 |     0.01  |     0.24  |    -0.074 |     0.315 |         |
| SWP|lvl_swing_N5|24h|AH|40|skip | X'       |  0.105 |    202405 |          0.088 |     0     |     0.151 |    -0.026 |     0.137 |         |
| ICE|R2N30|4h|AH|40|skip         | HOLD     |  0.127 |    202613 |          0     |     0     |     0.14  |    -0.007 |     0.202 |         |
| ICE|R2N30|4h|AH|40|skip         | X'       |  0.207 |    202405 |          0.15  |     0     |     0.298 |    -0.134 |     0.408 |         |

### three placebos (A same-volume stratified, B random rows same count per day, C other-day same book x session), V13X
| cell                         | kind   |   draws | window   |   cell_cut |   placebo_mean |   corrected |   rank |
|:-----------------------------|:-------|--------:|:---------|-----------:|---------------:|------------:|-------:|
| PUL|k3|4h D20 skip           | A      |      60 | L3M      |      0.141 |         -0.089 |       0.231 |  0.131 |
| PUL|k3|4h D20 skip           | A      |      60 | L6M      |      0.291 |         -0.127 |       0.418 |  0.098 |
| PUL|k3|4h D20 skip           | A      |      60 | HOLD     |      0.004 |          0.107 |      -0.103 |  0.721 |
| PUL|k3|4h D20 skip           | A      |      60 | MID      |      0.007 |          0.044 |      -0.038 |  0.623 |
| PUL|k3|4h D20 skip           | A      |      60 | PRE      |      0.223 |          0.083 |       0.139 |  0.197 |
| PUL|k3|4h D20 skip           | A      |      60 | X'       |      0.198 |          0.005 |       0.194 |  0.18  |
| PUL|k3|4h D20 skip           | B      |      60 | L3M      |      0.141 |         -0.043 |       0.184 |  0.311 |
| PUL|k3|4h D20 skip           | B      |      60 | L6M      |      0.291 |         -0.096 |       0.387 |  0.098 |
| PUL|k3|4h D20 skip           | B      |      60 | HOLD     |      0.004 |          0.023 |      -0.018 |  0.656 |
| PUL|k3|4h D20 skip           | B      |      60 | MID      |      0.007 |          0.047 |      -0.041 |  0.705 |
| PUL|k3|4h D20 skip           | B      |      60 | PRE      |      0.223 |          0.116 |       0.107 |  0.213 |
| PUL|k3|4h D20 skip           | B      |      60 | X'       |      0.198 |          0.03  |       0.169 |  0.016 |
| PUL|k3|4h D20 skip           | C      |      60 | L3M      |      0.141 |         -0.126 |       0.267 |  0.115 |
| PUL|k3|4h D20 skip           | C      |      60 | L6M      |      0.291 |         -0.187 |       0.478 |  0.016 |
| PUL|k3|4h D20 skip           | C      |      60 | HOLD     |      0.004 |          0.089 |      -0.085 |  0.672 |
| PUL|k3|4h D20 skip           | C      |      60 | MID      |      0.007 |          0.039 |      -0.033 |  0.574 |
| PUL|k3|4h D20 skip           | C      |      60 | PRE      |      0.223 |          0.048 |       0.175 |  0.148 |
| PUL|k3|4h D20 skip           | C      |      60 | X'       |      0.198 |          0.037 |       0.161 |  0.164 |
| SWP|lvl_swing_N5|4h D60 skip | A      |      30 | L3M      |      0.112 |         -0.081 |       0.194 |  0.355 |
| SWP|lvl_swing_N5|4h D60 skip | A      |      30 | L6M      |     -0.328 |         -0.094 |      -0.234 |  0.774 |
| SWP|lvl_swing_N5|4h D60 skip | A      |      30 | HOLD     |      0.177 |          0.132 |       0.045 |  0.452 |
| SWP|lvl_swing_N5|4h D60 skip | A      |      30 | MID      |     -0.195 |          0.05  |      -0.245 |  0.968 |
| SWP|lvl_swing_N5|4h D60 skip | A      |      30 | PRE      |      0.231 |          0.192 |       0.04  |  0.484 |
| SWP|lvl_swing_N5|4h D60 skip | A      |      30 | X'       |      0.141 |          0.049 |       0.092 |  0.452 |
| SWP|lvl_swing_N5|4h D60 skip | B      |      30 | L3M      |      0.112 |         -0.052 |       0.164 |  0.355 |
| SWP|lvl_swing_N5|4h D60 skip | B      |      30 | L6M      |     -0.328 |         -0.086 |      -0.242 |  0.839 |
| SWP|lvl_swing_N5|4h D60 skip | B      |      30 | HOLD     |      0.177 |          0.129 |       0.048 |  0.355 |
| SWP|lvl_swing_N5|4h D60 skip | B      |      30 | MID      |     -0.195 |          0.07  |      -0.265 |  1     |
| SWP|lvl_swing_N5|4h D60 skip | B      |      30 | PRE      |      0.231 |          0.137 |       0.094 |  0.29  |
| SWP|lvl_swing_N5|4h D60 skip | B      |      30 | X'       |      0.141 |          0.017 |       0.125 |  0.226 |
| SWP|lvl_swing_N5|4h D60 skip | C      |      30 | L3M      |      0.112 |         -0.17  |       0.282 |  0.161 |
| SWP|lvl_swing_N5|4h D60 skip | C      |      30 | L6M      |     -0.328 |         -0.101 |      -0.227 |  0.839 |
| SWP|lvl_swing_N5|4h D60 skip | C      |      30 | HOLD     |      0.177 |          0.211 |      -0.034 |  0.613 |
| SWP|lvl_swing_N5|4h D60 skip | C      |      30 | MID      |     -0.195 |          0.098 |      -0.294 |  0.968 |
| SWP|lvl_swing_N5|4h D60 skip | C      |      30 | PRE      |      0.231 |          0.099 |       0.132 |  0.323 |
| SWP|lvl_swing_N5|4h D60 skip | C      |      30 | X'       |      0.141 |          0.108 |       0.033 |  0.419 |

### PUL D20 skip on V13X: Asia vs rest and month chain
L6M: total +119.1k; Asia +75.8k; non-Asia +43.3k

HOLD: total +11.7k; Asia -23.0k; non-Asia +34.7k

PRE: total -37.8k; Asia -20.0k; non-Asia -17.7k

PUL D20 skip month chain (V13X): 43 months, positive 23, negative 14, zero 6; total +13.2k, 2026-09 +64.0k, other months -50.8k (t -0.37)

Reading (V13X is the headline; every table above this block is the ASSUMED base): on the exact base the pulled-wall cell gets BETTER where the assumed base had it fail (PRE +22%, X' +20%, L6M +29%) and is flat where the assumed base had it large (HOLD +0.4%: the HOLD maxDD episode is not touched). It is not carried by the 2026-09 episode on this base (L6M cut +26% without W37; the month chain is +13.2k in total, +64.0k in 2026-09 and -50.8k in the other 42 months, so it is a drawdown-shape effect, not a mean effect). Against the placebos the L6M cut is the only window with ranks <= 0.1; PRE/X' ranks are 0.15-0.2 (X' with random-rows placebo 0.016). Label LEAD (weak); the SWP lvl_swing D60 candidate flips sign in L6M/MID and is DEAD as a base-dependent result.


## HEADLINE V13X (exact base), stage x2: definition grid (D 10/20/30/40/60, 25/50/75% of target, 1h/4h/24h keep, BEHIND D20 skip/half, AT 2 pts size-up; skip and half) for the other 10 book streams + PUL k3/k5 (154 cells; AT take-only not scored: volume artefact, it removes 99% of trades)
Base maxDD $k: L1M 16.4, L3M 39.9, L6M 73.9, HOLD 119.2, MID 78.5, PRE 252.4, X' 173.7.
Best cell per stream by min(L6M cut, PRE cut, X' cut):
| stream               |   cells |   best_min_L6M_PRE_X |   best_L6M |   best_PRE |
|:---------------------|--------:|---------------------:|-----------:|-----------:|
| PUL|k3|4h            |       4 |                0.15  |      0.297 |      0.209 |
| PUL|k5|24h           |       2 |                0.132 |      0.132 |      0.185 |
| PUL|k5|4h            |      13 |                0.027 |      0.132 |      0.152 |
| SWP|ext_sess_N5|4h   |      13 |                0.005 |      0.039 |      0.249 |
| DEF|k3N30|4h         |      13 |                0.004 |      0.019 |      0.101 |
| ABS|k1N10|24h        |       2 |                0     |      0     |      0.015 |
| SWP|ext_pd_N5|4h     |      13 |                0     |      0     |      0.334 |
| SWP|lvl_pd_N5|4h     |      13 |                0     |      0     |      0.054 |
| ABS|k1N10|4h         |      13 |                0     |      0     |      0.081 |
| ICE|R3N30|4h         |      13 |                0     |      0     |      0     |
| DEF|k3N10|4h         |      13 |               -0.001 |      0.067 |      0.15  |
| SWP|ext_swing_N5|1h  |      13 |               -0.004 |     -0.004 |      0.254 |
| SWP|ext_sess_N5|24h  |       2 |               -0.009 |      0.045 |      0.249 |
| ICE|R3N30|24h        |       2 |               -0.015 |      0     |      0     |
| SWP|lvl_pd_N5|24h    |       2 |               -0.027 |     -0.025 |      0.035 |
| SWP|lvl_swing_N5|4h  |      13 |               -0.034 |     -0.019 |      0.25  |
| DEF|k3N30|24h        |       2 |               -0.059 |     -0.059 |      0.051 |
| SWP|ext_pd_N5|24h    |       2 |               -0.06  |     -0.06  |      0.302 |
| DEF|k3N10|24h        |       2 |               -0.189 |     -0.154 |      0.187 |
| SWP|lvl_swing_N5|24h |       2 |               -0.362 |     -0.362 |      0.311 |
| SWP|ext_swing_N5|24h |       2 |               -0.688 |     -0.688 |      0.263 |
Reading: on the exact base no stream except PUL reaches a 15% cut in L6M, PRE and X' together (ABS, ICE, DEF, SWP pd/sess/swing: DEAD in the AHEAD, BEHIND and AT frames); PUL k3 4 h D30 (min 15%) and PUL k5 24 h D40 (min 13%) are the only others. Full cells: out/zl_new/x2_cells.csv.


## HEADLINE V13X LOCK-OFF (engine per-book locks only, no combined 12R) - PUL k3
Lock-off base maxDD $k: L1M 36.6, L3M 49.9, L6M 132.6, HOLD 132.6, MID 62.6, PRE 178.4, X' 134.8.
| cell (skip) | nflag | L3M | L6M | HOLD | MID | PRE | X' |
|--|--|--|--|--|--|--|--|
| PUL k3 4h D20 | 1564 | -1% | +1% | +1% | -14% | +17% | +11% |
| PUL k3 4h D30 | 1927 | +11% | +8% | +2% | -55% | +13% | +11% |
| PUL k3 24h D20 | 2164 | +6% | +6% | 0% | -16% | +13% | +10% |
| PUL k3 4h D20 Asia-only | 860 | +25% | +12% | +7% | +9% | +6% | +9% |
Placebos on lock-off (20 draws per kind, D20): PRE cut +17% vs placebo mean -6..+4% (ranks 0.10 all kinds); X' +11% (ranks 0.05-0.52); L6M +1% vs placebo -0..+7% (rank 0.43-0.62).
Reading: with the combined 12R lock ON the PUL cell cuts L6M maxDD 29% (V13X), with the lock OFF it cuts 1%: the L6M effect is a property of how the lock engine reacts to the skipped rows, not a standalone drawdown cut. What survives without the lock is PRE +13..+17% and X' +10..+11% (placebo ranks 0.05-0.52). Label: FRAGILE (lock-dependent), LEAD only for PRE/X'.


## HEADLINE V13X, B4 liquidity pools (stage x4): LQP streams = UNSWEPT swing (fractal-5) and equal (2 / 3 touches within 1 pt, nothing beyond between) highs and lows on 15m / 1h / 4h path bars (31,214 levels to 20261030; fresh until price touches the level; kept 5 days; POI format in out/zl_new/streams_book/LQP*; causal audit 97/97 rows reproduced from as-of-truncated data, 0 index violations); AHEAD D20/40 and BEHIND D20 skip/half
Best cell per stream by min(L6M, PRE, X' cut):
| stream       |   cells |   best_min |   best_L6M |   best_PRE |   best_Xp |
|:-------------|--------:|-----------:|-----------:|-----------:|----------:|
| LQP|swH|15m  |       6 |      0.078 |      0.083 |      0.352 |     0.192 |
| LQP|eqL2|15m |       6 |      0.019 |      0.085 |      0.019 |     0.02  |
| LQP|eqH2|15m |       6 |      0.017 |      0.017 |      0.11  |     0.11  |
| LQP|swL|4h   |       6 |      0.008 |      0.008 |      0.162 |     0.139 |
| LQP|eqH2|1h  |       6 |      0     |      0     |      0.012 |     0.017 |
| LQP|eqH3|1h  |       6 |      0     |      0     |      0     |     0     |
| LQP|eqH3|15m |       6 |      0     |      0     |      0.006 |     0.021 |
| LQP|eqL3|15m |       6 |      0     |      0     |      0     |     0     |
| LQP|eqL2|1h  |       6 |      0     |      0     |      0     |     0     |
| LQP|swH|1h   |       6 |      0     |      0.005 |      0.232 |     0.039 |
| LQP|swH|4h   |       6 |      0     |      0.015 |      0.118 |     0     |
| LQP|swL|15m  |       6 |      0     |      0.143 |      0.127 |     0.276 |
| LQP|swL|1h   |       6 |      0     |      0     |      0.383 |     0.12  |

Sweep-then-reverse frame (a swept-and-reclaimed level BEHIND the entry within 5 / 10 pts = the reversal has started; size x1.5) and the sweep streams as skip ahead (x2 above): 
| stream              | frame   |   D | act   |   nflag |   L3M |   L6M |   HOLD |   MID |    PRE |     X' |   dmean_HOLD |      m |
|:--------------------|:--------|----:|:------|--------:|------:|------:|-------:|------:|-------:|-------:|-------------:|-------:|
| SWP|lvl_pd_N5|4h    | BH      |   5 | up    |       0 | 0     | 0     |      0 |     0 |  0     |  0     |        0     |  0     |
| SWP|lvl_pd_N5|4h    | BH      |  10 | up    |       0 | 0     | 0     |      0 |     0 |  0     |  0     |        0     |  0     |
| SWP|ext_pd_N5|4h    | BH      |   5 | up    |       0 | 0     | 0     |      0 |     0 |  0     |  0     |        0     |  0     |
| SWP|ext_pd_N5|4h    | BH      |  10 | up    |       0 | 0     | 0     |      0 |     0 |  0     |  0     |        0     |  0     |
| SWP|lvl_sess_N5|4h  | BH      |   5 | up    |       5 | 0     | 0     |      0 |     0 |  0     |  0     |        0     |  0     |
| SWP|lvl_sess_N5|4h  | BH      |  10 | up    |       9 | 0     | 0     |      0 |     0 |  0     |  0.004 |        0     |  0     |
| SWP|ext_sess_N5|4h  | BH      |   5 | up    |       4 | 0     | 0     |      0 |     0 |  0     |  0     |        0     |  0     |
| SWP|ext_sess_N5|4h  | BH      |  10 | up    |      11 | 0     | 0     |      0 |     0 |  0     |  0.004 |        0     |  0     |
| SWP|lvl_swing_N5|4h | BH      |   5 | up    |      68 | 0     | 0     |      0 |     0 |  0     | -0.012 |        0     | -0.012 |
| SWP|lvl_swing_N5|4h | BH      |  10 | up    |     165 | 0.008 | 0.004 |      0 |     0 |  0     | -0.011 |       19.924 | -0.011 |
| SWP|ext_swing_N5|4h | BH      |   5 | up    |      88 | 0     | 0     |      0 |     0 |  0     |  0.004 |        0     |  0     |
| SWP|ext_swing_N5|4h | BH      |  10 | up    |     248 | 0.008 | 0.004 |      0 |     0 | -0.113 | -0.006 |        7.84  | -0.113 |
Reading: no liquidity-pool cell reaches 15% on L6M, PRE and X' together (best LQP swH 15m D20 half: L6M +8%, PRE +24%, X' +8%); unswept swing/equal levels ahead are not skip zones on the exact base, and the sweep-then-reverse size-up has no effect (nflag small, cuts about 0). DEAD. The measured pool sizes (tape) stay with ZL-2 (DS3_ZONES_3_L2_TAPE.md): the unswept levels cannot know their pool before the break, only after.


## HEADLINE V13X (12R lock ON): PUL k3 4h D20 skip, 100 placebo draws per kind
| kind   |   draws | window   |   cell_cut |   placebo_mean |   placebo_p95 |   corrected |   rank |
|:-------|--------:|:---------|-----------:|---------------:|--------------:|------------:|-------:|
| A      |     100 | L3M      |      0.141 |         -0.067 |         0.322 |       0.208 |  0.178 |
| A      |     100 | L6M      |      0.291 |         -0.125 |         0.296 |       0.416 |  0.069 |
| A      |     100 | HOLD     |      0.004 |          0.089 |         0.363 |      -0.085 |  0.683 |
| A      |     100 | MID      |      0.007 |          0.042 |         0.285 |      -0.035 |  0.604 |
| A      |     100 | PRE      |      0.223 |          0.085 |         0.317 |       0.138 |  0.208 |
| A      |     100 | X'       |      0.198 |          0.021 |         0.296 |       0.178 |  0.208 |
| B      |     100 | L3M      |      0.141 |         -0.024 |         0.372 |       0.166 |  0.267 |
| B      |     100 | L6M      |      0.291 |         -0.057 |         0.321 |       0.348 |  0.099 |
| B      |     100 | HOLD     |      0.004 |          0.024 |         0.137 |      -0.02  |  0.634 |
| B      |     100 | MID      |      0.007 |          0.048 |         0.208 |      -0.042 |  0.663 |
| B      |     100 | PRE      |      0.223 |          0.112 |         0.302 |       0.111 |  0.198 |
| B      |     100 | X'       |      0.198 |          0.03  |         0.117 |       0.168 |  0.01  |
| C      |     100 | L3M      |      0.141 |         -0.093 |         0.287 |       0.234 |  0.149 |
| C      |     100 | L6M      |      0.291 |         -0.163 |         0.235 |       0.454 |  0.02  |
| C      |     100 | HOLD     |      0.004 |          0.106 |         0.364 |      -0.102 |  0.723 |
| C      |     100 | MID      |      0.007 |          0.06  |         0.348 |      -0.053 |  0.584 |
| C      |     100 | PRE      |      0.223 |          0.055 |         0.289 |       0.168 |  0.139 |
| C      |     100 | X'       |      0.198 |          0.03  |         0.287 |       0.168 |  0.149 |
Reading: L6M corrected +35..+45% (ranks 0.02-0.10), PRE +11..+14% (0.14-0.21), X' +17..+18% (0.01-0.21), L3M +17..+23% (0.15-0.27), HOLD/MID negative. Only L6M (and X' with random rows) are at or below rank 0.1; the combined-lock dependence (lock off: L6M +1%) is in the section above. Label: LOCK-ONLY for L6M; PRE/X' = LEAD (weak, ranks 0.14-0.21).


## HEADLINE (lock=None, V13X with the engine per-book locks only; user rule: headline lock=None, LOCK-ONLY label for lock=12-only cuts)
Cells (maxDD cut vs the lock-off base; base maxDD $k L6M 132.6, PRE 178.4, X' 134.8, MID 62.6):
| cell                            |   nflag |    L1M |    L3M |    L6M |   HOLD |    MID |    PRE |    X' |
|:--------------------------------|--------:|-------:|-------:|-------:|-------:|-------:|-------:|------:|
| SWP|lvl_swing_N5|4h|AH|60|skip  |    3214 | -0.057 |  0.09  |  0.209 |  0.08  |  0.113 | -0.007 | 0.095 |
| SWP|lvl_swing_N5|4h|AH|40|skip  |    2929 | -0.057 | -0.049 |  0.009 |  0.009 |  0.092 |  0.024 | 0.074 |
| LQP|swH|15m|AH|20|half          |    9426 |  0     | -0.03  | -0.091 | -0.091 | -0.052 |  0.111 | 0.059 |
| ICE|R2N30|4h|AH|40|skip         |     736 |  0     |  0     | -0.009 | -0.009 |  0.238 | -0.003 | 0.069 |
| SWP|lvl_sess_N5|4h|AH|40|half   |    1475 | -0.016 |  0.082 |  0.218 |  0.031 | -0.03  | -0.01  | 0.039 |
| SWP|lvl_swing_N5|4h|AH|30|skip  |    2678 | -0.057 | -0.102 | -0.035 | -0.035 |  0.092 |  0.024 | 0.074 |
| SWP|lvl_swing_N5|24h|AH|40|skip |    4360 | -0.088 |  0.062 |  0.041 |  0.041 |  0.197 |  0.008 | 0.042 |
| PUL|k5|4h|AH|30|skip            |     457 |  0     |  0.098 |  0.079 |  0.073 | -0.204 | -0.023 | 0.104 |
| PUL|k3|4h|AH|40|skip            |    2138 |  0.015 | -0.049 | -0.083 | -0.083 | -0.514 |  0.142 | 0.113 |
| PUL|k3|4h|AH|20|skip            |    1564 |  0     | -0.01  |  0.014 |  0.014 | -0.138 |  0.166 | 0.11  |
| PUL|k3|4h|AH|30|skip            |    1927 | -0.071 |  0.105 |  0.084 |  0.024 | -0.554 |  0.129 | 0.113 |
| PUL|k3|24h|AH|20|skip           |    2164 |  0     |  0.057 |  0.061 | -0.003 | -0.16  |  0.133 | 0.104 |
| PUL|k3|4h|AHA|20|skip           |     860 |  0     |  0.252 |  0.115 |  0.073 |  0.091 |  0.058 | 0.091 |
Placebos on lock=None (PUL 60 draws per kind, SWP lvl_swing 20 per kind):
| cell                    | kind   |   draws | window   |   cell_cut |   placebo_mean |   corrected |   rank |
|:------------------------|:-------|--------:|:---------|-----------:|---------------:|------------:|-------:|
| PUL|k3|4h D20           | A      |      60 | L6M      |      0.014 |          0.023 |      -0.009 |  0.59  |
| PUL|k3|4h D20           | A      |      60 | PRE      |      0.166 |         -0.09  |       0.256 |  0.049 |
| PUL|k3|4h D20           | A      |      60 | X'       |      0.11  |          0.025 |       0.085 |  0.246 |
| PUL|k3|4h D20           | B      |      60 | L6M      |      0.014 |          0.023 |      -0.009 |  0.475 |
| PUL|k3|4h D20           | B      |      60 | PRE      |      0.166 |         -0.016 |       0.183 |  0.066 |
| PUL|k3|4h D20           | B      |      60 | X'       |      0.11  |          0.005 |       0.105 |  0.033 |
| PUL|k3|4h D20           | C      |      60 | L6M      |      0.014 |          0.03  |      -0.016 |  0.525 |
| PUL|k3|4h D20           | C      |      60 | PRE      |      0.166 |         -0.098 |       0.264 |  0.049 |
| PUL|k3|4h D20           | C      |      60 | X'       |      0.11  |          0.061 |       0.049 |  0.475 |
| SWP|lvl_swing_N5|4h D60 | A      |      20 | L6M      |      0.209 |          0.034 |       0.175 |  0.381 |
| SWP|lvl_swing_N5|4h D60 | A      |      20 | PRE      |     -0.007 |         -0.065 |       0.057 |  0.333 |
| SWP|lvl_swing_N5|4h D60 | A      |      20 | X'       |      0.095 |         -0.029 |       0.124 |  0.238 |
| SWP|lvl_swing_N5|4h D60 | B      |      20 | L6M      |      0.209 |          0.047 |       0.162 |  0.095 |
| SWP|lvl_swing_N5|4h D60 | B      |      20 | PRE      |     -0.007 |         -0.093 |       0.086 |  0.381 |
| SWP|lvl_swing_N5|4h D60 | B      |      20 | X'       |      0.095 |          0.061 |       0.034 |  0.333 |
| SWP|lvl_swing_N5|4h D60 | C      |      20 | L6M      |      0.209 |          0.042 |       0.167 |  0.19  |
| SWP|lvl_swing_N5|4h D60 | C      |      20 | PRE      |     -0.007 |         -0.066 |       0.059 |  0.476 |
| SWP|lvl_swing_N5|4h D60 | C      |      20 | X'       |      0.095 |          0.05  |       0.044 |  0.476 |
Verdict (lock=None): PUL k3 4h skip D20 = LOCK-ONLY for the L6M cut (+29% with the 12R lock, +1% without); without the lock it keeps PRE +17% (placebo-corrected +18..+26%, ranks 0.05-0.07) and X' +11% (corrected +5..+10%, ranks 0.03-0.48), with MID -14%, HOLD +1%, L6M +1%: LEAD (weak) on PRE/X' only, no recent-window evidence, not RISK-KEEP. SWP lvl_swing 4h D60 (L6M +21% lock-off, +33% lock-on assumed base) has PRE -1% and X' +10% with placebo ranks 0.1-0.5: DEAD. The remaining cells (PUL k5, ICE R2N30 D40 MID +24% only, LQP swH 15m, SWP lvl_sess half L6M +22% but PRE -1%) fail at least one of L6M/PRE/X': DEAD. Per-cell files out/zl_new/lockoff_cells.csv, placebo_lockoff.csv.


## HEADLINE lock=None screen of every book / LQP stream (V13X, AHEAD D20/40, skip/half, 112 cells; base maxDD $k L6M 132.6, PRE 178.4, X' 134.8)
Best cell per stream by min(L6M, PRE, X' cut), top 14:
| stream              |   cells |   best_min |   best_L6M |   best_PRE |   best_Xp |
|:--------------------|--------:|-----------:|-----------:|-----------:|----------:|
| SWP|lvl_swing_N5|4h |       4 |      0.083 |      0.083 |      0.114 |     0.136 |
| PUL|k3|24h          |       4 |      0.061 |      0.061 |      0.133 |     0.148 |
| SWP|ext_pd_N5|4h    |       4 |      0.03  |      0.065 |      0.081 |     0.077 |
| LQP|eqL2|15m        |       4 |      0.027 |      0.027 |      0.066 |     0.077 |
| SWP|ext_swing_N5|4h |       4 |      0.015 |      0.189 |      0.015 |     0.217 |
| PUL|k5|4h           |       4 |      0.014 |      0.079 |      0.014 |     0.104 |
| LQP|eqH2|15m        |       4 |      0.005 |      0.005 |      0.006 |     0.152 |
| LQP|eqH3|1h         |       4 |      0     |      0     |      0     |     0     |
| LQP|eqH2|1h         |       4 |      0     |      0     |      0     |     0     |
| LQP|eqH3|15m        |       4 |      0     |      0     |      0     |     0     |
| ABS|k2N10|4h        |       4 |      0     |      0     |      0     |     0     |
| ICE|R3N30|4h        |       4 |      0     |      0     |      0     |     0     |
| ICE|R2N30|4h        |       4 |      0     |      0     |      0.045 |     0.121 |
| LQP|eqL3|15m        |       4 |      0     |      0     |      0     |     0.005 |
Reading: with the combined lock removed no book or liquidity-pool stream reaches a 10% cut on L6M, PRE and X' together (best: SWP lvl_swing 4h D20 half L6M +8%, PRE +9%, X' +14%; PUL k3 24h D20 skip +6/+13/+10 with MID -16%). DEAD in both lock frames; PUL k3 4h D20 remains the only LEAD (weak, PRE/X' only).


## PUL k3 4h D20 skip, lock=None: where the cell-minus-base dollars come from (V13X, $k)

L6M: total +22.4k; Asia +14.2k; London +10.4k; NY-AM -8.4k; NY-PM +6.1k
HOLD: total -62.4k; Asia -18.2k; London -12.2k; NY-AM -36.2k; NY-PM +4.2k
PRE: total +60.2k; Asia +32.5k; London +35.8k; NY-AM +1.6k; NY-PM -9.6k
X': total +30.6k; Asia +23.6k; London +3.5k; NY-AM +2.3k; NY-PM +1.2k

By realised-vol tercile:
| window   | vol T1        | vol T2       | vol T3        |
|:---------|:--------------|:-------------|:--------------|
| L6M      | +18.9k (2d)   | +14.4k (36d) | -11.0k (93d)  |
| HOLD     | +14.1k (17d)  | -10.4k (76d) | -66.1k (165d) |
| PRE      | -4.3k (121d)  | -8.6k (122d) | +73.1k (121d) |
| X'       | +26.2k (137d) | +4.4k (72d)  | +0.0k (7d)    |

PRE episode-proofing (lock none): cut +0.166, maxDD week 202516, cut without it +0.077, leave-one-month-out [+0.133,+0.222], bootstrap 90% [-0.052,+0.349]
X' episode-proofing (lock none): cut +0.110, maxDD week 202337, cut without it +0.110, LOO-month [+0.000,+0.157], bootstrap 90% [-0.079,+0.289]
month chain (lock none): 43 months, positive 23, negative 15, zero 5; total +31.7k; largest month 2025-04 +48.7k; worst 2025-11 -34.3k


## HEADLINE lock=None: PUL k3 definition sensitivity and 100-draw placebos (V13X; base maxDD $k L6M 132.6, PRE 178.4, X' 134.8, MID 62.6)
| stream     | frame   |     D | act   |   nflag |    L1M |    L3M |    L6M |   HOLD |    MID |    PRE |     X' |   dmean_HOLD |   mde_HOLD |
|:-----------|:--------|------:|:------|--------:|-------:|-------:|-------:|-------:|-------:|-------:|-------:|-------------:|-----------:|
| PUL|k3|24h | AH      | 20    | skip  |    2164 |  0     |  0.057 |  0.061 | -0.003 | -0.16  |  0.133 |  0.104 |    -1402.87  |    3753.48 |
| PUL|k3|24h | AH      | 40    | skip  |    3590 |  0.015 | -0.213 | -0.419 | -0.419 | -0.601 | -0.098 |  0.148 |    -2932.31  |    5461.12 |
| PUL|k3|4h  | AH      | 20    | half  |    1564 |  0     | -0.053 | -0.105 | -0.105 | -0.158 |  0.068 |  0.06  |    -1087.92  |    2036.93 |
| PUL|k3|4h  | AH      | 30    | half  |    1927 |  0     | -0.021 | -0.048 | -0.048 | -0.142 |  0.065 |  0.063 |     -416.251 |    2400.18 |
| PUL|k3|4h  | AH      | 10    | skip  |    1017 |  0     | -0.147 | -0.016 | -0.016 |  0.069 |  0.086 |  0.091 |     -796.779 |    2167.89 |
| PUL|k3|4h  | AH      | 20    | skip  |    1564 |  0     | -0.01  |  0.014 |  0.014 | -0.138 |  0.166 |  0.11  |    -1199.55  |    3367.89 |
| PUL|k3|4h  | AH      | 30    | skip  |    1927 | -0.071 |  0.105 |  0.084 |  0.024 | -0.554 |  0.129 |  0.113 |    -1028.9   |    4414.62 |
| PUL|k3|4h  | AH      | 40    | skip  |    2138 |  0.015 | -0.049 | -0.083 | -0.083 | -0.514 |  0.142 |  0.113 |    -1582.04  |    4377.51 |
| PUL|k3|4h  | AH      | 60    | skip  |    2387 |  0.015 | -0.025 | -0.24  | -0.24  | -0.493 |  0.191 |  0.113 |    -2692.72  |    4519.74 |
| PUL|k3|4h  | AHA     | 20    | skip  |     860 |  0     |  0.252 |  0.115 |  0.073 |  0.091 |  0.058 |  0.091 |     -402.452 |    2616.47 |
| PUL|k3|4h  | AHF     |  0.25 | skip  |    1231 |  0     | -0.045 |  0.054 |  0.054 |  0.099 |  0.006 |  0.11  |     -400.939 |    2525.37 |
| PUL|k3|4h  | AHF     |  0.5  | skip  |    1833 | -0.071 |  0.105 |  0.084 |  0.024 | -0.554 |  0.129 |  0.113 |    -1028.9   |    4414.62 |
| PUL|k3|4h  | AHF     |  0.75 | skip  |    2158 |  0.015 | -0.049 | -0.204 | -0.204 | -0.493 |  0.142 |  0.113 |    -2088.99  |    4516.37 |
| PUL|k3|4h  | AT      |  2    | up    |     566 | -0.018 |  0.104 |  0.02  |  0.02  | -0.012 | -0.08  | -0.041 |      167.176 |    1384.56 |
| PUL|k3|4h  | BH      | 20    | half  |    3010 | -0.077 | -0.198 | -0.026 | -0.026 |  0.126 | -0.17  | -0.081 |      -24.498 |    3714.12 |
| PUL|k3|4h  | BH      | 20    | skip  |    3010 | -0.084 | -0.284 | -0.042 | -0.042 |  0.175 | -0.287 |  0.126 |    -1753.98  |    4816.86 |

PUL k3 4h D20 skip, 100 draws per kind:
| kind   |   draws | window   |   cell_cut |   placebo_mean |   corrected |   rank |
|:-------|--------:|:---------|-----------:|---------------:|------------:|-------:|
| A      |     100 | L3M      |     -0.01  |         -0.067 |       0.057 |  0.446 |
| A      |     100 | L6M      |      0.014 |          0.048 |      -0.035 |  0.634 |
| A      |     100 | HOLD     |      0.014 |         -0.039 |       0.053 |  0.446 |
| A      |     100 | MID      |     -0.138 |         -0.06  |      -0.078 |  0.673 |
| A      |     100 | PRE      |      0.166 |         -0.068 |       0.234 |  0.03  |
| A      |     100 | X'       |      0.11  |          0.033 |       0.077 |  0.277 |
| B      |     100 | L3M      |     -0.01  |          0.012 |      -0.022 |  0.624 |
| B      |     100 | L6M      |      0.014 |          0.033 |      -0.019 |  0.515 |
| B      |     100 | HOLD     |      0.014 |         -0.014 |       0.028 |  0.505 |
| B      |     100 | MID      |     -0.138 |          0.082 |      -0.22  |  0.931 |
| B      |     100 | PRE      |      0.166 |         -0.022 |       0.188 |  0.05  |
| B      |     100 | X'       |      0.11  |          0.003 |       0.107 |  0.03  |
| C      |     100 | L3M      |     -0.01  |         -0.051 |       0.042 |  0.505 |
| C      |     100 | L6M      |      0.014 |          0.039 |      -0.025 |  0.545 |
| C      |     100 | HOLD     |      0.014 |         -0.029 |       0.043 |  0.416 |
| C      |     100 | MID      |     -0.138 |         -0.039 |      -0.099 |  0.713 |
| C      |     100 | PRE      |      0.166 |         -0.099 |       0.265 |  0.03  |
| C      |     100 | X'       |      0.11  |          0.047 |       0.063 |  0.366 |
Reading (lock=None): the PUL cell is a PRE effect: PRE cut +17% (corrected +19..+27%, placebo ranks 0.03-0.05 for all three kinds), positive at every D (D10 +9%, D30 +13%, D40 +14%, D60 +19%), X' +11% (ranks 0.03 random-rows, 0.28-0.37 the other two), but L3M/L6M/HOLD are 0 to +10% (placebo-corrected -4..+6%) and MID is -14% (rank 0.67-0.93 against it); BEHIND skip -28% L3M / -29% PRE (bad); half is worse than skip. So with the lock removed the recent windows (L6M, HOLD, MID, L3M) show no benefit, and the PRE/X' benefit (2023-2025) does not continue: LEAD (weak), historical only, no recent evidence; not RISK-KEEP.
