# REPORT RV1 - GC, CL and basket FVG-retrace sleeves: replication, plateau, family-wise null, stress, sizing, independence

Pre-registered in PREREG_AUTOPILOT.md BATCH RV before any run. Cells fixed to the RZ selections (GC FVG tf15 thr0.25; CL FVG tf15 thr0.25; BASKET = the nine RZ9 members; GC+CL added as an extra pair row). Same 1-minute simulator as RZ1 (base results reproduce: GC clean weekly Sharpe 2.59, additive-20% clean uplift +0.46). Per the coordinator these are cross-market support for the single FVG-family lead, not independent FOUNDs. Sleeve R series are unit-risk R per trade; uplift = weekly Sharpe uplift of PAIR + 20% (vol-matched on the clean span) minus PAIR.

## RV1a H0 (2023-02-10..2023-07-31)

| target | trades | net R/trade | t | weekly Sharpe | additive-20% uplift | pass |
|---|---|---|---|---|---|---|
| GC | 446 | -0.0071 | -0.1 | -0.17 | -0.11 | FAIL |
| CL | 441 | +0.0791 | +1.3 | +1.85 | +0.39 | PASS |
| GC+CL | 887 | +0.0179 | +0.8 | +0.98 | +0.16 | PASS |
| BASKET | 3119 | +0.0012 | +0.5 | +0.55 | +0.07 | PASS |

## RV1b alternating months (exit-label month parity, 2023-02..2026-10)

| target | half | trades | net R/trade | t (trades) | monthly-total Sharpe | monthly t | pass |
|---|---|---|---|---|---|---|---|
| GC | odd months | 1840 | +0.0807 | +2.6 | 2.02 | +2.7 | PASS |
| GC | even months | 1861 | +0.0951 | +3.1 | 2.56 | +3.5 | PASS |
| CL | odd months | 1726 | +0.1079 | +3.5 | 2.58 | +3.5 | PASS |
| CL | even months | 1737 | +0.0802 | +2.6 | 1.83 | +2.5 | PASS |
| GC+CL | odd months | 3566 | +0.0470 | +4.3 | 3.73 | +5.0 | PASS |
| GC+CL | even months | 3598 | +0.0440 | +4.1 | 3.17 | +4.4 | PASS |
| BASKET | odd months | 13211 | +0.0076 | +6.0 | 3.92 | +5.3 | PASS |
| BASKET | even months | 13114 | +0.0057 | +4.6 | 2.95 | +4.1 | PASS |

## RV1c exact +-25% plateau (one parameter at a time; neighbour passes if clean weekly Sharpe >= 75% of base and additive-20% uplift > 0 on H1 and H2)

### GC (base clean Sharpe 2.59, uplift +0.46/+0.75/+0.35); neighbours passing 11/12 -> PASS

| neighbour | trades | clean Sharpe | uplift clean/H1/H2 | |
|---|---|---|---|---|
| thr=0.75 | 4127 | 2.87 | +0.51/+0.88/+0.42 | ok |
| thr=1.25 | 3314 | 2.22 | +0.38/+0.74/+0.54 | ok |
| mint=22 | 3824 | 2.80 | +0.50/+0.69/+0.34 | ok |
| mint=38 | 3548 | 2.75 | +0.46/+0.65/+0.38 | ok |
| fr=0.375 | 3621 | 2.72 | +0.49/+0.70/+0.09 | ok |
| fr=0.625 | 3744 | 2.63 | +0.48/+0.97/+0.45 | ok |
| R=1.5 | 3917 | 2.47 | +0.45/+0.67/+0.32 | ok |
| R=2.5 | 3538 | 3.37 | +0.63/+0.76/+0.62 | ok |
| H=270 | 3789 | 2.80 | +0.51/+0.74/+0.29 | ok |
| H=450 | 3666 | 2.67 | +0.49/+0.79/+0.40 | ok |
| L=15 | 3673 | 1.72 | +0.28/+0.79/+0.23 | FAIL |
| L=25 | 3664 | 2.47 | +0.43/+0.53/+0.33 | ok |

### CL (base clean Sharpe 2.27, uplift +0.41/+0.36/+0.51); neighbours passing 9/12 -> PASS

| neighbour | trades | clean Sharpe | uplift clean/H1/H2 | |
|---|---|---|---|---|
| thr=0.75 | 3737 | 2.67 | +0.50/+0.32/+0.71 | ok |
| thr=1.25 | 3166 | 1.36 | +0.24/+0.28/+0.36 | FAIL |
| mint=22 | 3780 | 1.19 | +0.16/+0.33/+0.55 | FAIL |
| mint=38 | 3159 | 2.53 | +0.44/+0.33/+0.62 | ok |
| fr=0.375 | 3395 | 3.05 | +0.57/+0.29/+0.26 | ok |
| fr=0.625 | 3508 | 1.66 | +0.29/+0.42/+0.64 | FAIL |
| R=1.5 | 3690 | 2.45 | +0.42/+0.38/+0.13 | ok |
| R=2.5 | 3296 | 2.12 | +0.36/+0.12/+0.45 | ok |
| H=270 | 3591 | 1.72 | +0.31/+0.21/+0.68 | ok |
| H=450 | 3397 | 1.81 | +0.33/+0.36/+0.49 | ok |
| L=15 | 3479 | 1.82 | +0.32/+0.29/+0.44 | ok |
| L=25 | 3438 | 2.25 | +0.40/+0.42/+0.65 | ok |

### GC+CL (base clean Sharpe 3.61, uplift +0.65/+0.91/+0.64); neighbours passing 10/12 -> PASS

| neighbour | trades | clean Sharpe | uplift clean/H1/H2 | |
|---|---|---|---|---|
| thr=0.75 | 7864 | 3.99 | +0.73/+0.95/+0.81 | ok |
| thr=1.25 | 6480 | 2.64 | +0.47/+0.82/+0.67 | FAIL |
| mint=22 | 7604 | 3.00 | +0.51/+0.82/+0.63 | ok |
| mint=38 | 6707 | 3.98 | +0.68/+0.85/+0.74 | ok |
| fr=0.375 | 7016 | 4.09 | +0.76/+0.79/+0.26 | ok |
| fr=0.625 | 7252 | 3.33 | +0.61/+1.17/+0.82 | ok |
| R=1.5 | 7607 | 3.66 | +0.66/+0.85/+0.36 | ok |
| R=2.5 | 6834 | 4.24 | +0.77/+0.75/+0.83 | ok |
| H=270 | 7380 | 3.40 | +0.62/+0.78/+0.69 | ok |
| H=450 | 7063 | 3.22 | +0.60/+0.89/+0.64 | ok |
| L=15 | 7152 | 2.58 | +0.45/+0.89/+0.48 | FAIL |
| L=25 | 7102 | 3.39 | +0.60/+0.76/+0.70 | ok |

### BASKET (base clean Sharpe 4.89, uplift +0.84/+0.72/+0.68); neighbours passing 11/12 -> PASS

| neighbour | trades | clean Sharpe | uplift clean/H1/H2 | |
|---|---|---|---|---|
| thr=0.75 | 29040 | 5.70 | +1.00/+0.93/+0.57 | ok |
| thr=1.25 | 23783 | 3.48 | +0.60/+0.61/+0.57 | FAIL |
| mint=22 | 28216 | 3.95 | +0.66/+0.48/+0.65 | ok |
| mint=38 | 24507 | 5.48 | +0.95/+0.63/+0.64 | ok |
| fr=0.375 | 25807 | 5.30 | +0.90/+0.78/+0.44 | ok |
| fr=0.625 | 26660 | 4.61 | +0.81/+0.82/+0.60 | ok |
| R=1.5 | 27980 | 4.19 | +0.69/+0.51/+0.39 | ok |
| R=2.5 | 25214 | 5.58 | +0.99/+0.91/+0.74 | ok |
| H=270 | 27001 | 4.67 | +0.81/+0.58/+0.69 | ok |
| H=450 | 25972 | 4.41 | +0.75/+0.75/+0.60 | ok |
| L=15 | 26493 | 4.00 | +0.66/+0.67/+0.39 | ok |
| L=25 | 26039 | 4.97 | +0.86/+0.64/+0.77 | ok |

## RV1d family-wise null (depth permutation; statistic = max clean weekly Sharpe over the grid)

Observed max over 72 cells (9 markets x 8) = 2.59; null worlds (n=100): median max 2.73, 95th pct 3.02, max 3.27; rank of the observed maximum = 0.29.

| market | observed max over its 8 cells | null median | null 95th | rank vs market null |
|---|---|---|---|---|
| ES | 0.93 | 0.79 | 1.15 | 0.73 |
| RTY | 1.71 | 1.75 | 2.05 | 0.37 |
| YM | 1.19 | 1.22 | 1.68 | 0.46 |
| GC | 2.59 | 2.58 | 2.98 | 0.53 |
| CL | 2.27 | 2.15 | 2.71 | 0.63 |
| ZN | 0.75 | 0.86 | 1.07 | 0.17 |
| 6E | 0.77 | 0.64 | 1.03 | 0.70 |
| BTC | 2.24 | 2.04 | 2.48 | 0.71 |
| ETH | 2.04 | 2.33 | 2.96 | 0.29 |

Family-wise pass (rank >= 0.95): FAIL; GC market-level FAIL, CL market-level FAIL.

## RV1e stress set and fill bounds (weekly Sharpe clean/H1/H2/all; additive-20% uplift clean/H1/H2)

| target | scenario | trades | Sharpe c/H1/H2/all | uplift c/H1/H2 |
|---|---|---|---|---|
| GC | base | 3701 | 2.59/2.18/2.99/2.61 | +0.46/+0.75/+0.35 |
| GC | S1_slip2 | 3701 | 2.16/1.91/2.77/2.24 | +0.37/+0.69/+0.32 |
| GC | S2_adv1 | 3701 | 2.00/1.81/2.69/2.11 | +0.34/+0.68/+0.31 |
| GC | S3_miss20 | 2962 | 2.36/1.95/2.54/2.34 | +0.41/+0.67/+0.31 |
| GC | S4_all | 2957 | 1.42/1.27/2.07/1.52 | +0.23/+0.51/+0.23 |
| GC | TOUCH | 3729 | 3.13/2.49/3.06/3.03 | +0.56/+0.84/+0.38 |
| GC | THROUGH1 | 3701 | 2.59/2.18/2.99/2.61 | +0.46/+0.75/+0.35 |
| GC | STRICT | 3662 | 1.20/1.73/2.35/1.51 | +0.19/+0.67/+0.28 |
| CL | base | 3463 | 2.27/1.73/3.00/2.34 | +0.41/+0.36/+0.51 |
| CL | S1_slip2 | 3463 | 1.67/1.28/2.59/1.80 | +0.29/+0.23/+0.43 |
| CL | S2_adv1 | 3463 | 1.48/1.18/2.44/1.64 | +0.25/+0.20/+0.40 |
| CL | S3_miss20 | 2769 | 1.96/1.72/2.57/2.06 | +0.35/+0.34/+0.44 |
| CL | S4_all | 2777 | 0.77/0.73/1.88/1.01 | +0.12/+0.08/+0.29 |
| CL | TOUCH | 3503 | 2.74/2.15/4.22/2.95 | +0.50/+0.49/+0.79 |
| CL | THROUGH1 | 3463 | 2.27/1.73/3.00/2.34 | +0.41/+0.36/+0.51 |
| CL | STRICT | 3391 | 0.42/0.10/1.78/0.69 | +0.05/-0.06/+0.33 |
| GC+CL | base | 7164 | 3.61/3.02/4.49/3.72 | +0.65/+0.91/+0.64 |
| GC+CL | S1_slip2 | 7164 | 2.86/2.44/4.01/3.04 | +0.51/+0.77/+0.56 |
| GC+CL | S2_adv1 | 7164 | 2.61/2.28/3.84/2.82 | +0.46/+0.73/+0.53 |
| GC+CL | S3_miss20 | 5732 | 3.16/2.82/3.84/3.26 | +0.57/+0.80/+0.57 |
| GC+CL | S4_all | 5728 | 1.66/1.61/2.80/1.89 | +0.27/+0.53/+0.39 |
| GC+CL | TOUCH | 7232 | 4.38/3.70/5.39/4.52 | +0.80/+1.09/+0.85 |
| GC+CL | THROUGH1 | 7164 | 3.61/3.02/4.49/3.72 | +0.65/+0.91/+0.64 |
| GC+CL | STRICT | 7053 | 1.24/1.28/3.05/1.64 | +0.19/+0.54/+0.46 |
| BASKET | base | 26325 | 4.89/2.96/3.39/4.21 | +0.84/+0.72/+0.68 |
| BASKET | S1_slip2 | 26325 | 3.69/1.87/2.57/3.13 | +0.61/+0.47/+0.49 |
| BASKET | S2_adv1 | 26325 | 3.28/1.52/2.27/2.76 | +0.53/+0.40/+0.42 |
| BASKET | S3_miss20 | 21060 | 4.32/2.69/3.13/3.77 | +0.74/+0.64/+0.61 |
| BASKET | S4_all | 21071 | 1.81/0.31/1.44/1.49 | +0.26/+0.11/+0.22 |
| BASKET | TOUCH | 26650 | 6.04/3.89/4.46/5.32 | +1.05/+0.95/+0.94 |
| BASKET | THROUGH1 | 26325 | 4.89/2.96/3.39/4.21 | +0.84/+0.72/+0.68 |
| BASKET | STRICT | 25923 | 1.43/-0.05/1.15/1.13 | +0.19/+0.02/+0.16 |

## RV1f sizing (assumed initial margins, NOT verified with the broker: GC $11,000, MGC $1,100, CL $6,500, MCL $650)

| target / member | share | $ per R | median stop $/contract | contracts | micro contracts | margin $ (standard) |
|---|---|---|---|---|---|---|
| GC/GC | 10% | 1,083 | 367 | 2.95 | 29.5 MGC | 32,471 |
| GC/GC | 20% | 2,165 | 367 | 5.90 | 59.0 MGC | 64,941 |
| GC/GC | 30% | 3,248 | 367 | 8.86 | 88.6 MGC | 97,412 |
| CL/CL | 10% | 1,297 | 300 | 4.32 | 43.2 MCL | 28,098 |
| CL/CL | 20% | 2,594 | 300 | 8.65 | 86.5 MCL | 56,196 |
| CL/CL | 30% | 3,890 | 300 | 12.97 | 129.7 MCL | 84,293 |
| BASKET/ES | 20% | 835 | 375 | 2.23 | - | - |
| BASKET/RTY | 20% | 835 | 203 | 4.11 | - | - |
| BASKET/YM | 20% | 835 | 344 | 2.43 | - | - |
| BASKET/GC | 20% | 835 | 367 | 2.28 | 22.8 MGC | 25,051 |
| BASKET/CL | 20% | 835 | 300 | 2.78 | 27.8 MCL | 18,098 |
| BASKET/6E | 20% | 835 | 188 | 4.45 | - | - |
| BASKET/BTC | 20% | 835 | 1,123 | 0.74 | - | - |

## RV1g independence (correlations of daily and weekly P&L, 2023-08..2026-10)

| series | vs PAIR daily | PAIR weekly | vs E1 daily | E1 weekly | vs IMP3 daily | IMP3 weekly | mean $ in worst-decile pair weeks (20% share) |
|---|---|---|---|---|---|---|---|
| GC | +0.00 | +0.00 | +0.01 | -0.01 | +0.03 | +0.06 | +5,079 |
| CL | +0.06 | +0.04 | +0.02 | +0.14 | +0.06 | +0.09 | +1,684 |
| GC+CL | +0.05 | +0.04 | +0.02 | +0.09 | +0.06 | +0.11 | +5,209 |
| BASKET | +0.06 | +0.12 | +0.10 | +0.10 | +0.05 | +0.08 | +10,855 |
| E1 vs PAIR | +0.20 | +0.21 | | | | | |
| IMP3 vs PAIR | +0.11 | +0.13 | | | | | |

## RV1 summary of pre-registered passes

| target | H0 | alt months | plateau | stress+STRICT | family-wise null (market-level) |
|---|---|---|---|---|---|
| GC | FAIL | PASS | PASS | PASS | FAIL |
| CL | PASS | PASS | PASS | FAIL | FAIL |
| GC+CL | PASS | PASS | PASS | PASS | FAIL (family) |
| BASKET | PASS | PASS | PASS | PASS | FAIL (family) |

Quote only (RV2): GLBX.MDP3 trades GC.v.0 2023-02-01..2026-10-14 $114.81; CL.v.0 $122.85; total $237.66 (not bought; see SPEND.json notes).

DONE RV1