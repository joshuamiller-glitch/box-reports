# DS3_FLAT_VS_BOOK - flat stand-in vs book-based cut on the live-equivalent base TL3_EV_JN05W2JL2 (W-EV, user order 11-16)

**VERDICT (data ends 2026-10-30; FIRST PASS, running; 19 of 28 cells have a scored window; windows appear as months land; no PASS claimed).** Reference = TL3_EV_JN05W2JL2 (K7 flat 45 + K7 book cut; P7 book cut (ctx fresh 45/5x/w5/p10, rechase 30/10x/w5/p2) and NO P7 flat). Drawdown first.

## What is live-computable today and what is not
- LIVE TODAY (v1.9b, blind book): the flat stand-ins (K7 -0.75 x stop = 45, P7 -0.70 = 42; price-only, win=1 persist=1) are computable live; the book-based lines (K7 45/10x/w2/p3, P7 40/5x/w5/p3 or the F3 context cells) were NOT, because live read no book on 79% of losing seconds.
- With v1.9c (primary-series book) the clean book the engine uses becomes available: (b) book-based only and the book arm moves (e) are then live-computable; (a) book + flat and the flat level moves (d) are computable now and after v1.9c; (c) flat only is what live effectively ran.
- Engine note: the engine book is the clean one, so engine (b) is what v1.9c should do. Live results of (a)/(c) before v1.9c are NOT comparable to the engine (blind book, section 14 of DS3_ENGINE_VS_LIVE.md).

## Cell map
- ID = JN05W2JL2 with K7 flat re-expressed through la_hooks (must equal JL2); A_* = book + flat (K7 45 live, P7 42 stand-in); B_* = flat off (book only); C_* = flat only (that book cut off by la_hooks scut nocut); D_* = flat level moved (K7 39/51, P7 36/48; both together diagonal); E_* = book arm -10/+10 pts (K7 all sessions floor 15; P7 fresh and rechase); PC_* = persistent random-trigger flats (bucket 300, one draw per 5-min bucket per book and side, never re-drawn) REPLACING that book flat, q 0.05/0.10/0.20: the nonsense rate beside every flat row. Units: 60-pt stop; K7 -0.65/-0.75/-0.85 = 39/45/51 pts, P7 -0.60/-0.70/-0.80 = 36/42/48.
BASE: JL2 base (without live take/lock lines). A cut-vs-flat result can shift once the live take/lock lines are on (JL3 = TL3_EV_JL3), because they change which trades reach the cut.

Columns: dd_cut / dd44_cut = max-drawdown cut % vs JL2 (all weeks / W44 removed), ww = worst week $, best5 = share of the reference best-5 weeks kept, w2l = winning weeks turned losing, d_mean / d_mean_484 = $/wk vs JL2 base lots (live x1.75; $4.84 repriced), flat_wk = LaFlat exits per week, flat_usd_wk vs same_entries_noflat_usd_wk = the cut trades vs the same entries without the flat (path effect caution), t / p = weekly-cluster t and sign-flip p.

## L3M
### group ID
| cell         |   weeks |   dd_cut |   dd44_cut |       ww |   ww_ref |   best5 |   w2l |   d_mean |   d_mean_484 |   cuts_wk |   flat_wk |   flat_usd_wk |   same_entries_noflat_usd_wk |   t |   p |
|:-------------|--------:|---------:|-----------:|---------:|---------:|--------:|------:|---------:|-------------:|----------:|----------:|--------------:|-----------------------------:|----:|----:|
| TL3_EV_FB_ID |      13 |        0 |          0 | -13429.6 | -13429.6 |       1 |     0 |        0 |            0 |        53 |     17.31 |      -17865.3 |                     -17865.3 | nan |   1 |

### group a
| cell           |   weeks |   dd_cut |   dd44_cut |       ww |   ww_ref |   best5 |   w2l |   d_mean |   d_mean_484 |   cuts_wk |   flat_wk |   flat_usd_wk |   same_entries_noflat_usd_wk |      t |    p |
|:---------------|--------:|---------:|-----------:|---------:|---------:|--------:|------:|---------:|-------------:|----------:|----------:|--------------:|-----------------------------:|-------:|-----:|
| TL3_EV_FB_A_K7 |      13 |     0    |       0    | -13429.6 | -13429.6 |    1    |     0 |     0    |         0    |     53    |     17.31 |     -17865.3  |                    -17865.3  | nan    | 1    |
| TL3_EV_FB_A_KP |      13 |   -58.36 |     -58.36 | -21266.5 | -13429.6 |    0.96 |     0 | -1403.59 |     -1403.59 |     50.46 |     20.62 |     -23299.6  |                    -22835.7  |  -1.48 | 0.2  |
| TL3_EV_FB_A_P7 |      13 |  -150.8  |    -150.8  | -33681.9 | -13429.6 |    1.02 |     2 | -2481.36 |     -2477.42 |     55.92 |      3.31 |      -5386.64 |                     -5002.54 |  -0.98 | 0.35 |

### group b
| cell           |   weeks |   dd_cut |   dd44_cut |       ww |   ww_ref |   best5 |   w2l |   d_mean |   d_mean_484 |   cuts_wk |   flat_wk |   flat_usd_wk |   same_entries_noflat_usd_wk |      t |    p |
|:---------------|--------:|---------:|-----------:|---------:|---------:|--------:|------:|---------:|-------------:|----------:|----------:|--------------:|-----------------------------:|-------:|-----:|
| TL3_EV_FB_B_P7 |      13 |     0    |       0    | -13429.6 | -13429.6 |    1    |     0 |     0    |         0    |     53    |     17.31 |      -17865.3 |                     -17865.3 | nan    | 1    |
| TL3_EV_FB_B_K7 |      13 |   -51.16 |     -51.16 | -20300.3 | -13429.6 |    1.07 |     1 |  -588.46 |      -581.14 |     57.69 |      0    |           0   |                          0   |  -0.37 | 0.72 |
| TL3_EV_FB_B_KP |      13 |   -51.16 |     -51.16 | -20300.3 | -13429.6 |    1.07 |     1 |  -588.46 |      -581.14 |     57.69 |      0    |           0   |                          0   |  -0.37 | 0.71 |

### group c
| cell           |   weeks |   dd_cut |   dd44_cut |       ww |   ww_ref |   best5 |   w2l |   d_mean |   d_mean_484 |   cuts_wk |   flat_wk |   flat_usd_wk |   same_entries_noflat_usd_wk |    t |    p |
|:---------------|--------:|---------:|-----------:|---------:|---------:|--------:|------:|---------:|-------------:|----------:|----------:|--------------:|-----------------------------:|-----:|-----:|
| TL3_EV_FB_C_K7 |      13 |    -3.72 |      -3.72 | -13929.4 | -13429.6 |    1.05 |     0 |   893.66 |       909.14 |     39.62 |     26.54 |      -27113.1 |                     -22122.5 | 1.34 | 0.21 |
| TL3_EV_FB_C_KP |      13 |   -63.63 |     -63.63 | -21515.5 | -13429.6 |    1.14 |     1 |  2482.94 |      2499.83 |     20.92 |     43.69 |      -58306.5 |                     -42820.2 | 1.18 | 0.26 |
| TL3_EV_FB_C_P7 |      13 |   -93.83 |     -93.83 | -23796.1 | -13429.6 |    1.08 |     1 |   977.18 |       980.84 |     34.15 |     34.08 |      -48781.3 |                     -38584.2 | 0.48 | 0.64 |

### group d
| cell                   |   weeks |   dd_cut |   dd44_cut |       ww |   ww_ref |   best5 |   w2l |   d_mean |   d_mean_484 |   cuts_wk |   flat_wk |   flat_usd_wk |   same_entries_noflat_usd_wk |     t |    p |
|:-----------------------|--------:|---------:|-----------:|---------:|---------:|--------:|------:|---------:|-------------:|----------:|----------:|--------------:|-----------------------------:|------:|-----:|
| TL3_EV_FB_D_K7_D51     |      13 |   -16.7  |     -16.7  | -14809.9 | -13429.6 |    1.12 |     1 |  1183.85 |      1195.68 |     55.15 |     11.77 |      -13899.5 |                     -11874.7 |  1.24 | 0.27 |
| TL3_EV_FB_D_K7_D39     |      13 |   -35.5  |     -35.5  | -16093.6 | -13429.6 |    1.04 |     1 |   656.26 |       652.88 |     49.46 |     21.77 |      -19782   |                     -17543   |  0.76 | 0.51 |
| TL3_EV_FB_D_P7_D36     |      13 |   -52.55 |     -52.55 | -20486.5 | -13429.6 |    0.96 |     0 | -1364    |     -1368.51 |     50.69 |     21.38 |      -23690   |                     -23014   | -1.36 | 0.21 |
| TL3_EV_FB_D_P7_D48     |      13 |   -65.12 |     -65.12 | -22175.5 | -13429.6 |    0.94 |     1 | -1548.29 |     -1546.32 |     50.92 |     19.62 |      -22769.8 |                     -21911.7 | -1.64 | 0.14 |
| TL3_EV_FB_D_KP_D39_D36 |      13 |   -71.55 |     -71.55 | -23038   | -13429.6 |    1.02 |     0 |  -908.46 |      -920.28 |     47.77 |     26    |      -25675.2 |                     -22805.2 | -0.78 | 0.4  |
| TL3_EV_FB_D_KP_D51_D48 |      13 |   -76.26 |     -76.26 | -23670.8 | -13429.6 |    1.06 |     0 |  -373.29 |      -359.78 |     53.08 |     14.08 |      -18811   |                     -15921.1 | -0.26 | 0.8  |

### group e
| cell               |   weeks |   dd_cut |   dd44_cut |     ww |   ww_ref |   best5 |   w2l |   d_mean |   d_mean_484 |   cuts_wk |   flat_wk |   flat_usd_wk |   same_entries_noflat_usd_wk |     t |   p |
|:-------------------|--------:|---------:|-----------:|-------:|---------:|--------:|------:|---------:|-------------:|----------:|----------:|--------------:|-----------------------------:|------:|----:|
| TL3_EV_FB_E_KP_M10 |      13 |  -138.32 |    -138.32 | -32005 | -13429.6 |    0.79 |     1 | -4007.63 |     -4034.37 |     62.69 |     15.77 |      -17273.9 |                     -15691.3 | -1.79 | 0.1 |

### group control (persistent random-trigger flat, bucket 300)
| cell                |   weeks |   dd_cut |   dd44_cut |       ww |   ww_ref |   best5 |   w2l |   d_mean |   d_mean_484 |   cuts_wk |   flat_wk |   flat_usd_wk |   same_entries_noflat_usd_wk |     t |    p |
|:--------------------|--------:|---------:|-----------:|---------:|---------:|--------:|------:|---------:|-------------:|----------:|----------:|--------------:|-----------------------------:|------:|-----:|
| TL3_EV_FB_PC_P7_Q10 |      13 |   -39.8  |     -39.8  | -18775.3 | -13429.6 |    1    |     1 |  -926.73 |      -935.18 |     57.15 |      2.46 |       -452.07 |                      -155.26 | -0.76 | 0.48 |
| TL3_EV_FB_PC_P7_Q05 |      13 |   -49.08 |     -49.08 | -20020.3 | -13429.6 |    1.08 |     1 |  -597.42 |      -592.63 |     57.38 |      0.92 |       -162.7  |                         9.43 | -0.36 | 0.74 |

## L6M
### group ID
| cell         |   weeks |   dd_cut |   dd44_cut |       ww |   ww_ref |   best5 |   w2l |   d_mean |   d_mean_484 |   cuts_wk |   flat_wk |   flat_usd_wk |   same_entries_noflat_usd_wk |   t |   p |
|:-------------|--------:|---------:|-----------:|---------:|---------:|--------:|------:|---------:|-------------:|----------:|----------:|--------------:|-----------------------------:|----:|----:|
| TL3_EV_FB_ID |      26 |        0 |          0 | -13429.6 | -13429.6 |       1 |     0 |        0 |            0 |     55.96 |     19.38 |      -20170.4 |                     -20170.4 | nan |   1 |

### group a
| cell           |   weeks |   dd_cut |   dd44_cut |       ww |   ww_ref |   best5 |   w2l |   d_mean |   d_mean_484 |   cuts_wk |   flat_wk |   flat_usd_wk |   same_entries_noflat_usd_wk |      t |    p |
|:---------------|--------:|---------:|-----------:|---------:|---------:|--------:|------:|---------:|-------------:|----------:|----------:|--------------:|-----------------------------:|-------:|-----:|
| TL3_EV_FB_A_K7 |      26 |     0    |       0    | -13429.6 | -13429.6 |    1    |     0 |     0    |         0    |     55.96 |     19.38 |      -20170.4 |                    -20170.4  | nan    | 1    |
| TL3_EV_FB_A_KP |      26 |   -58.36 |     -58.36 | -21266.5 | -13429.6 |    1    |     0 |  -799.23 |      -799.65 |     53.69 |     22.5  |      -24957.4 |                    -24561.9  |  -1.44 | 0.17 |
| TL3_EV_FB_A_P7 |      26 |  -150.8  |    -150.8  | -33681.9 | -13429.6 |    1.02 |     2 | -2351.3  |     -2336.09 |     59.54 |      3.04 |       -4696.6 |                     -4325.16 |  -1.56 | 0.13 |

### group b
| cell           |   weeks |   dd_cut |   dd44_cut |       ww |   ww_ref |   best5 |   w2l |   d_mean |   d_mean_484 |   cuts_wk |   flat_wk |   flat_usd_wk |   same_entries_noflat_usd_wk |      t |    p |
|:---------------|--------:|---------:|-----------:|---------:|---------:|--------:|------:|---------:|-------------:|----------:|----------:|--------------:|-----------------------------:|-------:|-----:|
| TL3_EV_FB_B_P7 |      26 |     0    |       0    | -13429.6 | -13429.6 |    1    |     0 |      0   |          0   |     55.96 |     19.38 |      -20170.4 |                     -20170.4 | nan    | 1    |
| TL3_EV_FB_B_K7 |      26 |   -51.16 |     -51.16 | -20300.3 | -13429.6 |    1.02 |     1 |   -998.4 |       -983.2 |     61.62 |      0    |           0   |                          0   |  -0.92 | 0.36 |
| TL3_EV_FB_B_KP |      26 |   -51.16 |     -51.16 | -20300.3 | -13429.6 |    1.02 |     1 |   -998.4 |       -983.2 |     61.62 |      0    |           0   |                          0   |  -0.92 | 0.37 |

### group c
| cell           |   weeks |   dd_cut |   dd44_cut |       ww |   ww_ref |   best5 |   w2l |   d_mean |   d_mean_484 |   cuts_wk |   flat_wk |   flat_usd_wk |   same_entries_noflat_usd_wk |     t |    p |
|:---------------|--------:|---------:|-----------:|---------:|---------:|--------:|------:|---------:|-------------:|----------:|----------:|--------------:|-----------------------------:|------:|-----:|
| TL3_EV_FB_C_K7 |      26 |    -3.72 |      -3.72 | -13929.4 | -13429.6 |    0.97 |     1 |  -381.27 |      -368.6  |     42.46 |     29    |      -29800.1 |                     -24709.9 | -0.36 | 0.82 |
| TL3_EV_FB_C_KP |      26 |   -63.63 |     -63.63 | -21515.5 | -13429.6 |    0.93 |     3 |  -943.12 |      -924.68 |     22.85 |     47.08 |      -60969.2 |                     -45672.5 | -0.51 | 0.64 |
| TL3_EV_FB_C_P7 |      26 |   -93.83 |     -93.83 | -23796.1 | -13429.6 |    0.96 |     1 | -1387.22 |     -1375.11 |     36.15 |     36.96 |      -50868.2 |                     -41025.1 | -1.1  | 0.29 |

### group d
| cell                   |   weeks |   dd_cut |   dd44_cut |       ww |   ww_ref |   best5 |   w2l |   d_mean |   d_mean_484 |   cuts_wk |   flat_wk |   flat_usd_wk |   same_entries_noflat_usd_wk |     t |    p |
|:-----------------------|--------:|---------:|-----------:|---------:|---------:|--------:|------:|---------:|-------------:|----------:|----------:|--------------:|-----------------------------:|------:|-----:|
| TL3_EV_FB_D_K7_D51     |      26 |   -16.7  |     -16.7  | -14809.9 | -13429.6 |    1.01 |     1 |  -243.12 |      -230.87 |     58.27 |     14.08 |      -16647.6 |                     -14253.5 | -0.33 | 0.76 |
| TL3_EV_FB_D_K7_D39     |      26 |   -35.5  |     -35.5  | -16755.7 | -13429.6 |    1    |     1 |  -822.51 |      -823.63 |     52.31 |     24.77 |      -22560.8 |                     -19319.2 | -1.12 | 0.29 |
| TL3_EV_FB_D_P7_D36     |      26 |   -52.55 |     -52.55 | -20486.5 | -13429.6 |    0.99 |     0 | -1227.22 |     -1228.91 |     53.15 |     23.58 |      -25800.3 |                     -25398.1 | -2.02 | 0.06 |
| TL3_EV_FB_D_KP_D39_D36 |      26 |   -71.55 |     -71.55 | -23038   | -13429.6 |    0.99 |     0 | -2140.43 |     -2145.5  |     49.81 |     29    |      -28193.8 |                     -24567   | -2.56 | 0.02 |
| TL3_EV_FB_D_KP_D51_D48 |      26 |   -76.26 |     -76.26 | -23670.8 | -13429.6 |    1    |     0 | -1006.68 |      -993.45 |     56.23 |     16.27 |      -20874.9 |                     -18111.5 | -1.17 | 0.26 |

## HOLD
### group d
| cell                   |   weeks |   dd_cut |   dd44_cut |       ww |   ww_ref |   best5 |   w2l |   d_mean |   d_mean_484 |   cuts_wk |   flat_wk |   flat_usd_wk |   same_entries_noflat_usd_wk |     t |    p |
|:-----------------------|--------:|---------:|-----------:|---------:|---------:|--------:|------:|---------:|-------------:|----------:|----------:|--------------:|-----------------------------:|------:|-----:|
| TL3_EV_FB_D_KP_D51_D48 |      52 |   -11.96 |     -11.96 | -31949.1 | -31210.9 |    1.06 |     2 |     -773 |      -762.17 |     48.35 |     15.35 |      -19722.3 |                     -16938.2 | -1.27 | 0.21 |

## GAP
(no cell has all months of this window yet)

## PRE
(no cell has all months of this window yet)

## X'
(no cell has all months of this window yet)

