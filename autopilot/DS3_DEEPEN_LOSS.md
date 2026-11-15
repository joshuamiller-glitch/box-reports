# DS3_DEEPEN_LOSS - T-DEEPEN PART 1 loss side (W-LA items 1-5; W-LB section appended below). Built 2026-11-15 07:28Z

**VERDICT (running): 24 LA cells scored, 16 pass the programme tolerant gate in BOTH L3M and L6M (list in section 1); no PASS claimed. Each gate-passer gets its PART 0 battery; see section 6.**

LOT BASIS: sets are JN05W2 at BASE lots (live = x1.75; live caps = engine caps x1.75, P7 8,400 engine = 14,700 live). Engine fee $1.18/contract RT vs FEES.md $4.84: column d_mean_484 reprices the change in lots. dd/ww are $ per week series at base lots. prog = tolerant gate (dd cut > -2% and mean change > -3% of reference); strict = dd44_cut>0 and d_mean_484>=0 and dd_cut>=0.
Cells: TL3_LA_<grp>_*  S = state-cut grid (NOCUT, persist P1/2/3/5, arm A+-5/10, mult M05/M2, win W2/5/10; P7 edits the F3 context cells, FP/RP = fresh/rechase only) | E = WL_E1 | C = C22 | F = flat cuts (session, alone = book state cut OFF, tight, FC forecast units, ATR) | FA = state-cut arm in forecast units | X = state-cut arm +-10 under an entry-context tag. Hook code/th_deepen_la/la_hooks.py (identity: see below). W-PM owns all-session flat cuts TL3_PM_X_*.

Identity: TL3_LA_ID 202610: 598 trades net 25943.82 vs JN05W2 598 net 25943.82 -> IDENTICAL

## 1. Cells that pass the tolerant gate in L3M and L6M
- TL3_LA_C_N18
- TL3_LA_FA_K7_K02
- TL3_LA_FA_K7_K03
- TL3_LA_FA_K7_K04
- TL3_LA_F_K7_AS_D40
- TL3_LA_F_K7_LO_D40
- TL3_LA_F_K7_PR_D40
- TL3_LA_S_K7_NOCUT
- TL3_LA_S_K7_P3
- TL3_LA_XA_K7_ANDID
- TL3_LA_XA_M7_ANDID
- TL3_LA_XA_P7_ANDID
- TL3_LA_XA_U7_ANDID
- TL3_LA_X_K7_GAP15_T
- TL3_LA_X_K7_N3_L
- TL3_LA_X_K7_N3_T

## 2. Persist sensitivity of the state cut (live-fidelity risk: persist=3 lines were silent live, persist<=2 fired)
|                 |   ('d_mean', 'L3M') |   ('d_mean', 'L6M') |   ('dd_cut', 'L3M') |   ('dd_cut', 'L6M') |
|:----------------|--------------------:|--------------------:|--------------------:|--------------------:|
| ('K7', 'NOCUT') |              1318.6 |               308.3 |                17.6 |                17.6 |
| ('K7', 'P1')    |             -1220.5 |             -2394.2 |               -14.1 |               -14.1 |
| ('K7', 'P2')    |             -1090   |             -1794   |                 0.8 |                 0.8 |
| ('K7', 'P3')    |                 0   |                 0   |                 0   |                 0   |

Reading: a variant that only wins at P1/P2 and loses at P3/P5 is a live-fidelity risk.

## 3. STATE CUT GRID (item 1)
### L3M (4 cells)
| cell              |   weeks |    mean |   d_mean |      dd |   dd_ref |   dd_cut |   dd44_cut |   prog |   strict |   d_mean44 |   d_mean_484 |       ww |   ww_ref |   best5 |   w2l |   cuts_wk |   cuts_wk_ref |   n_wk |   n_wk_ref |
|:------------------|--------:|--------:|---------:|--------:|---------:|---------:|-----------:|-------:|---------:|-----------:|-------------:|---------:|---------:|--------:|------:|----------:|--------------:|-------:|-----------:|
| TL3_LA_S_K7_NOCUT |      13 | 17333.8 |   1318.6 | 29974.2 |  36370.5 |     17.6 |        1.8 |      1 |        1 |      592.4 |       1326.2 | -26603.7 | -36370.5 |     1   |     0 |      41.2 |          52.5 |  142.8 |      144.2 |
| TL3_LA_S_K7_P2    |      13 | 14925.2 |  -1090   | 36092.9 |  36370.5 |      0.8 |      -18.2 |      0 |        0 |    -2022.7 |      -1109.7 | -35050.9 | -36370.5 |     0.9 |     0 |      71.2 |          52.5 |  149.6 |      144.2 |
| TL3_LA_S_K7_P3    |      13 | 16015.2 |      0   | 36370.5 |  36370.5 |      0   |        0   |      1 |        0 |        0   |          0   | -36370.5 | -36370.5 |     1   |     0 |      52.5 |          52.5 |  144.2 |      144.2 |
| TL3_LA_S_K7_P1    |      13 | 14794.7 |  -1220.5 | 41516.2 |  36370.5 |    -14.1 |      -36   |      0 |        0 |    -1961.4 |      -1234.8 | -37536.2 | -36370.5 |     1   |     0 |      77.7 |          52.5 |  150.5 |      144.2 |

### L6M (4 cells)
| cell              |   weeks |    mean |   d_mean |      dd |   dd_ref |   dd_cut |   dd44_cut |   prog |   strict |   d_mean44 |   d_mean_484 |       ww |   ww_ref |   best5 |   w2l |   cuts_wk |   cuts_wk_ref |   n_wk |   n_wk_ref |
|:------------------|--------:|--------:|---------:|--------:|---------:|---------:|-----------:|-------:|---------:|-----------:|-------------:|---------:|---------:|--------:|------:|----------:|--------------:|-------:|-----------:|
| TL3_LA_S_K7_NOCUT |      26 | 25445.2 |    308.3 | 29974.2 |  36370.5 |     17.6 |        1.8 |      1 |        1 |      -80.7 |        310.6 | -26603.7 | -36370.5 |     1   |     1 |      45   |          57.1 |  159.4 |      160.3 |
| TL3_LA_S_K7_P2    |      26 | 23342.9 |  -1794   | 36092.9 |  36370.5 |      0.8 |      -18.2 |      0 |        0 |    -2269.8 |      -1802.1 | -35050.9 | -36370.5 |     0.9 |     0 |      77.6 |          57.1 |  163.4 |      160.3 |
| TL3_LA_S_K7_P3    |      26 | 25136.9 |      0   | 36370.5 |  36370.5 |      0   |        0   |      1 |        0 |        0   |          0   | -36370.5 | -36370.5 |     1   |     0 |      57.1 |          57.1 |  160.3 |      160.3 |
| TL3_LA_S_K7_P1    |      26 | 22742.7 |  -2394.2 | 41516.2 |  36370.5 |    -14.1 |      -36   |      0 |        0 |    -2796.8 |      -2405   | -37536.2 | -36370.5 |     1   |     1 |      84.8 |          57.1 |  165.4 |      160.3 |

## 4. STATE CUT ARM IN FORECAST UNITS (item 1)
### L3M (3 cells)
| cell             |   weeks |    mean |   d_mean |      dd |   dd_ref |   dd_cut |   dd44_cut |   prog |   strict |   d_mean44 |   d_mean_484 |       ww |   ww_ref |   best5 |   w2l |   cuts_wk |   cuts_wk_ref |   n_wk |   n_wk_ref |
|:-----------------|--------:|--------:|---------:|--------:|---------:|---------:|-----------:|-------:|---------:|-----------:|-------------:|---------:|---------:|--------:|------:|----------:|--------------:|-------:|-----------:|
| TL3_LA_FA_K7_K02 |      13 | 17372.4 |   1357.2 | 29974.2 |  36370.5 |     17.6 |        1.8 |      1 |        1 |      634.2 |       1364.3 | -26603.7 | -36370.5 |       1 |     0 |      41.4 |          52.5 |  142.8 |      144.2 |
| TL3_LA_FA_K7_K03 |      13 | 17333.8 |   1318.6 | 29974.2 |  36370.5 |     17.6 |        1.8 |      1 |        1 |      592.4 |       1326.2 | -26603.7 | -36370.5 |       1 |     0 |      41.2 |          52.5 |  142.8 |      144.2 |
| TL3_LA_FA_K7_K04 |      13 | 17333.8 |   1318.6 | 29974.2 |  36370.5 |     17.6 |        1.8 |      1 |        1 |      592.4 |       1326.2 | -26603.7 | -36370.5 |       1 |     0 |      41.2 |          52.5 |  142.8 |      144.2 |

### L6M (3 cells)
| cell             |   weeks |    mean |   d_mean |      dd |   dd_ref |   dd_cut |   dd44_cut |   prog |   strict |   d_mean44 |   d_mean_484 |       ww |   ww_ref |   best5 |   w2l |   cuts_wk |   cuts_wk_ref |   n_wk |   n_wk_ref |
|:-----------------|--------:|--------:|---------:|--------:|---------:|---------:|-----------:|-------:|---------:|-----------:|-------------:|---------:|---------:|--------:|------:|----------:|--------------:|-------:|-----------:|
| TL3_LA_FA_K7_K02 |      26 | 25467.4 |    330.5 | 29974.2 |  36370.5 |     17.6 |        1.8 |      1 |        1 |      -57.6 |        332.5 | -26603.7 | -36370.5 |       1 |     1 |      45.2 |          57.1 |  159.5 |      160.3 |
| TL3_LA_FA_K7_K03 |      26 | 25445.2 |    308.3 | 29974.2 |  36370.5 |     17.6 |        1.8 |      1 |        1 |      -80.7 |        310.6 | -26603.7 | -36370.5 |       1 |     1 |      45   |          57.1 |  159.4 |      160.3 |
| TL3_LA_FA_K7_K04 |      26 | 25445.2 |    308.3 | 29974.2 |  36370.5 |     17.6 |        1.8 |      1 |        1 |      -80.7 |        310.6 | -26603.7 | -36370.5 |       1 |     1 |      45   |          57.1 |  159.4 |      160.3 |

## 5. CONTEXT-TAGGED STATE CUT (items 1, 5)
### L3M (3 cells)
| cell                |   weeks |    mean |   d_mean |      dd |   dd_ref |   dd_cut |   dd44_cut |   prog |   strict |   d_mean44 |   d_mean_484 |       ww |   ww_ref |   best5 |   w2l |   cuts_wk |   cuts_wk_ref |   n_wk |   n_wk_ref |
|:--------------------|--------:|--------:|---------:|--------:|---------:|---------:|-----------:|-------:|---------:|-----------:|-------------:|---------:|---------:|--------:|------:|----------:|--------------:|-------:|-----------:|
| TL3_LA_X_K7_N3_T    |      13 | 17219.5 |   1204.4 | 31690.9 |  36370.5 |     12.9 |       -3.8 |      1 |        0 |      671.9 |       1202.1 | -28776.9 | -36370.5 |       1 |     0 |      48.6 |          52.5 |  145   |      144.2 |
| TL3_LA_X_K7_N3_L    |      13 | 17473.4 |   1458.2 | 31970.9 |  36370.5 |     12.1 |       -4.7 |      1 |        0 |      678   |       1456.3 | -26338.4 | -36370.5 |       1 |     0 |      47   |          52.5 |  144.9 |      144.2 |
| TL3_LA_X_K7_GAP15_T |      13 | 16551.5 |    536.3 | 32878.7 |  36370.5 |      9.6 |       -7.7 |      1 |        0 |      -94.1 |        538.2 | -28270.1 | -36370.5 |       1 |     0 |      48.8 |          52.5 |  143.5 |      144.2 |

### L6M (3 cells)
| cell                |   weeks |    mean |   d_mean |      dd |   dd_ref |   dd_cut |   dd44_cut |   prog |   strict |   d_mean44 |   d_mean_484 |       ww |   ww_ref |   best5 |   w2l |   cuts_wk |   cuts_wk_ref |   n_wk |   n_wk_ref |
|:--------------------|--------:|--------:|---------:|--------:|---------:|---------:|-----------:|-------:|---------:|-----------:|-------------:|---------:|---------:|--------:|------:|----------:|--------------:|-------:|-----------:|
| TL3_LA_X_K7_N3_T    |      26 | 26218   |   1081.1 | 31690.9 |  36370.5 |     12.9 |       -3.8 |      1 |        0 |      820.6 |       1084.8 | -28776.9 | -36370.5 |       1 |     0 |      52.2 |          57.1 |  159.3 |      160.3 |
| TL3_LA_X_K7_N3_L    |      26 | 26244   |   1107.1 | 31970.9 |  36370.5 |     12.1 |       -4.7 |      1 |        0 |      718.6 |       1111.1 | -26338.4 | -36370.5 |       1 |     0 |      49.9 |          57.1 |  159.2 |      160.3 |
| TL3_LA_X_K7_GAP15_T |      26 | 25681.8 |    544.9 | 32878.7 |  36370.5 |      9.6 |       -7.7 |      1 |        0 |      242.7 |        549.4 | -28270.1 | -36370.5 |       1 |     0 |      53.2 |          57.1 |  159   |      160.3 |

## 7. FLAT CUTS (item 2)
### L3M (3 cells)
| cell               |   weeks |    mean |   d_mean |      dd |   dd_ref |   dd_cut |   dd44_cut |   prog |   strict |   d_mean44 |   d_mean_484 |       ww |   ww_ref |   best5 |   w2l |   cuts_wk |   cuts_wk_ref |   n_wk |   n_wk_ref |
|:-------------------|--------:|--------:|---------:|--------:|---------:|---------:|-----------:|-------:|---------:|-----------:|-------------:|---------:|---------:|--------:|------:|----------:|--------------:|-------:|-----------:|
| TL3_LA_F_K7_AS_D40 |      13 | 16575.6 |    560.4 | 28537.6 |  36370.5 |     21.5 |        6.5 |      1 |        1 |     -387.5 |        555.9 | -25118.4 | -36370.5 |       1 |     0 |      51.2 |          52.5 |  145.1 |      144.2 |
| TL3_LA_F_K7_LO_D40 |      13 | 16880.9 |    865.7 | 32040.3 |  36370.5 |     11.9 |       12.6 |      1 |        1 |      577   |        851.6 | -32040.3 | -36370.5 |       1 |     0 |      52.8 |          52.5 |  147.6 |      144.2 |
| TL3_LA_F_K7_PR_D40 |      13 | 16015.2 |      0   | 36370.5 |  36370.5 |      0   |        0   |      1 |        0 |        0   |          0   | -36370.5 | -36370.5 |       1 |     0 |      52.5 |          52.5 |  144.2 |      144.2 |

### L6M (3 cells)
| cell               |   weeks |    mean |   d_mean |      dd |   dd_ref |   dd_cut |   dd44_cut |   prog |   strict |   d_mean44 |   d_mean_484 |       ww |   ww_ref |   best5 |   w2l |   cuts_wk |   cuts_wk_ref |   n_wk |   n_wk_ref |
|:-------------------|--------:|--------:|---------:|--------:|---------:|---------:|-----------:|-------:|---------:|-----------:|-------------:|---------:|---------:|--------:|------:|----------:|--------------:|-------:|-----------:|
| TL3_LA_F_K7_AS_D40 |      26 | 25566.6 |    429.7 | 28537.6 |  36370.5 |     21.5 |        6.5 |      1 |        1 |      -30.5 |        430.7 | -25118.4 | -36370.5 |       1 |     0 |      55.6 |          57.1 |  159.9 |      160.3 |
| TL3_LA_F_K7_LO_D40 |      26 | 25580.2 |    443.3 | 32040.3 |  36370.5 |     11.9 |       12.6 |      1 |        1 |      287.8 |        437.2 | -32040.3 | -36370.5 |       1 |     0 |      56.5 |          57.1 |  161.7 |      160.3 |
| TL3_LA_F_K7_PR_D40 |      26 | 25136.9 |      0   | 36370.5 |  36370.5 |      0   |        0   |      1 |        0 |        0   |          0   | -36370.5 | -36370.5 |       1 |     0 |      57.1 |          57.1 |  160.3 |      160.3 |

## 8. C22 FAMILY (item 3)
### L3M (3 cells)
| cell         |   weeks |    mean |   d_mean |      dd |   dd_ref |   dd_cut |   dd44_cut |   prog |   strict |   d_mean44 |   d_mean_484 |       ww |   ww_ref |   best5 |   w2l |   cuts_wk |   cuts_wk_ref |   n_wk |   n_wk_ref |
|:-------------|--------:|--------:|---------:|--------:|---------:|---------:|-----------:|-------:|---------:|-----------:|-------------:|---------:|---------:|--------:|------:|----------:|--------------:|-------:|-----------:|
| TL3_LA_C_N18 |      13 | 16964.7 |    949.5 | 33755.5 |  36370.5 |      7.2 |      -10.6 |      1 |        0 |      338.6 |        994.3 | -33755.5 | -36370.5 |     1   |     0 |      48.9 |          52.5 |  135.7 |      144.2 |
| TL3_LA_C_N14 |      13 | 14784.8 |  -1230.4 | 50026.9 |  36370.5 |    -37.5 |      -63.8 |      0 |        0 |    -3313.4 |      -1105.4 | -36787.9 | -36370.5 |     0.9 |     0 |      42.9 |          52.5 |  121.2 |      144.2 |
| TL3_LA_C_N26 |      13 | 13630.6 |  -2384.6 | 52213.7 |  36370.5 |    -43.6 |       -0.2 |      0 |        0 |    -1263   |      -2416.4 | -52213.7 | -36370.5 |     1   |     0 |      55.4 |          52.5 |  150.9 |      144.2 |

### L6M (3 cells)
| cell         |   weeks |    mean |   d_mean |      dd |   dd_ref |   dd_cut |   dd44_cut |   prog |   strict |   d_mean44 |   d_mean_484 |       ww |   ww_ref |   best5 |   w2l |   cuts_wk |   cuts_wk_ref |   n_wk |   n_wk_ref |
|:-------------|--------:|--------:|---------:|--------:|---------:|---------:|-----------:|-------:|---------:|-----------:|-------------:|---------:|---------:|--------:|------:|----------:|--------------:|-------:|-----------:|
| TL3_LA_C_N18 |      26 | 25294.4 |    157.5 | 33755.5 |  36370.5 |      7.2 |      -10.6 |      1 |        0 |     -167.4 |        203.3 | -33755.5 | -36370.5 |     1   |     0 |      53.5 |          57.1 |  152.1 |      160.3 |
| TL3_LA_C_N14 |      26 | 22799.6 |  -2337.3 | 50026.9 |  36370.5 |    -37.5 |      -63.8 |      0 |        0 |    -3381.5 |      -2209.5 | -36787.9 | -36370.5 |     0.8 |     1 |      47.9 |          57.1 |  138.1 |      160.3 |
| TL3_LA_C_N26 |      26 | 23447.5 |  -1689.4 | 52213.7 |  36370.5 |    -43.6 |       -0.2 |      0 |        0 |    -1123.3 |      -1721   | -52213.7 | -36370.5 |     1   |     0 |      59.7 |          57.1 |  166.8 |      160.3 |

## 9. WL_E1 (item 4)
### L3M (4 cells)
| cell             |   weeks |    mean |   d_mean |      dd |   dd_ref |   dd_cut |   dd44_cut |   prog |   strict |   d_mean44 |   d_mean_484 |       ww |   ww_ref |   best5 |   w2l |   cuts_wk |   cuts_wk_ref |   n_wk |   n_wk_ref |
|:-----------------|--------:|--------:|---------:|--------:|---------:|---------:|-----------:|-------:|---------:|-----------:|-------------:|---------:|---------:|--------:|------:|----------:|--------------:|-------:|-----------:|
| TL3_LA_E_G3      |      13 | 15410.2 |   -605   | 30533.4 |  36370.5 |     16   |        0   |      0 |        0 |    -1223.2 |       -609.2 | -29556.4 | -36370.5 |     0.9 |     0 |      52.6 |          52.5 |  144.2 |      144.2 |
| TL3_LA_E_NOEV0   |      13 | 16786.3 |    771.1 | 37779.4 |  36370.5 |     -3.9 |      -23.7 |      0 |        0 |     -489.6 |        784   | -33271.9 | -36370.5 |     1   |     0 |      51.8 |          52.5 |  143.5 |      144.2 |
| TL3_LA_E_G1NOEV0 |      13 | 14493.2 |  -1522   | 39875.9 |  36370.5 |     -9.6 |      -30.6 |      0 |        0 |    -3223.4 |      -1440.9 | -39321   | -36370.5 |     0.9 |     0 |      48.7 |          52.5 |  138.6 |      144.2 |
| TL3_LA_E_G1      |      13 | 13036.9 |  -2978.2 | 45958.6 |  36370.5 |    -26.4 |      -50.5 |      0 |        0 |    -3234.1 |      -2927   | -39238.5 | -36370.5 |     0.9 |     1 |      50   |          52.5 |  139.5 |      144.2 |

### L6M (4 cells)
| cell             |   weeks |    mean |   d_mean |      dd |   dd_ref |   dd_cut |   dd44_cut |   prog |   strict |   d_mean44 |   d_mean_484 |       ww |   ww_ref |   best5 |   w2l |   cuts_wk |   cuts_wk_ref |   n_wk |   n_wk_ref |
|:-----------------|--------:|--------:|---------:|--------:|---------:|---------:|-----------:|-------:|---------:|-----------:|-------------:|---------:|---------:|--------:|------:|----------:|--------------:|-------:|-----------:|
| TL3_LA_E_G3      |      26 | 24151.6 |   -985.2 | 30533.4 |  36370.5 |     16   |        0   |      0 |        0 |    -1297.2 |       -988.8 | -29556.4 | -36370.5 |     1   |     0 |      57.4 |          57.1 |  160.3 |      160.3 |
| TL3_LA_E_NOEV0   |      26 | 24830.8 |   -306.1 | 37779.4 |  36370.5 |     -3.9 |      -23.7 |      0 |        0 |     -954.3 |       -284   | -33271.9 | -36370.5 |     1   |     0 |      55.9 |          57.1 |  158   |      160.3 |
| TL3_LA_E_G1NOEV0 |      26 | 21570.3 |  -3566.6 | 39875.9 |  36370.5 |     -9.6 |      -30.6 |      0 |        0 |    -4465.1 |      -3441.4 | -39321   | -36370.5 |     0.9 |     0 |      51.4 |          57.1 |  149.7 |      160.3 |
| TL3_LA_E_G1      |      26 | 22100   |  -3036.9 | 45958.6 |  36370.5 |    -26.4 |      -50.5 |      0 |        0 |    -3162   |      -2963.4 | -39238.5 | -36370.5 |     0.9 |     2 |      53.7 |          57.1 |  153.3 |      160.3 |

## 6. Auto-expansions (PART 0)



---
# SECTION W-LB (items 6-9)
# DS3_DEEPEN_LOSS_B - T-DEEPEN PART 1 item 6 (SKIPS) and item 9 (EXECUTION COSTS), W-LB

**VERDICT (plain): 44 of 228 cells have an exact L3M result so far; 9 pass the tolerant gate in L3M with a positive mean (candidates for promotion, none claimed). Item 9 cost measurement is in section 1: fees plus excess slippage are 16.0% of L6M gross, the 08:30 bump is only about $50-60/wk of it. No PASS claim.**

Written 2026-11-15T07:02Z (date -u). Research only, shadow, no PASS claims. Prereg autopilot/DEEPEN_LB_PREREG.md (sha 9d2b5bd88f64ed49 in DECISIONS.md). Code code/th_deepen_lb (lb_hooks.py outermost additive hook; lb_cells.py registry; lb_score.py; lb_page.py), bulk /mnt/l2/l2vast/_deepen_lb. Identity: TL3_LB_ID 202610: 598 trades net 25943.82 vs JN05W2 598 net 25943.82 -> IDENTICAL | TL3_LB_ID0 202610: 598 trades net 25943.82 vs JN05W2 598 net 25943.82 -> IDENTICAL.

**LOT BASIS.** Sets run at BASE lots (live user lots x1.75; live caps = engine caps x1.75, P7 day cap 8,400 engine = 14,700 live). The engine charges $1.18/contract RT in net_fee; FEES.md standard is $4.84 (NQ proxy), MNQ $1.78. Every table carries a $4.84 column (d mean $4.84 = d mean repriced on the change in contracts) and a live-excess column (adds entry +0.23, cut +0.40, stop +0.44, target 0 pt, +1.36 pt on non-target exits 08:30-08:44 ET; passive fills carry no entry excess). Noise floor (DS3_REDO_R4_ENTRY): |maxDD cut| below ~8% and |mean delta| below ~$1,238/wk is path-dependence level.

## 1. Item 9 measured first: what each book and session pays per dollar earned (JN05W2 exact trade list)

Cost = FEES.md $4.84/contract RT + live-excess slip (entry +0.23 pt, market cut +0.40, stop +0.44, target 0, +1.36 pt on non-target exits starting 08:30-08:44 ET), points x $20 x contracts (model of th_smart_b/b1_cost_audit.py; slip means from the 187 frozen live trades and the DN stop-fill study). Cost per contract is lot-invariant: fee 4.84 + entry 4.60 = 9.44 for a target round trip, 17.4 for a cut, 18.2 for a stop, +27.2 more at 08:30-08:44. Code m1_cost.py, m2_section.py.

### 1.1 Where the cost goes (all books)

| window | gross $ | fee $ | entry excess $ | cut excess $ | stop excess $ | 08:30 bump $ | total cost $ | cost % of gross | cost $/wk | 08:30 bump $/wk | contracts/wk |
|---|---|---|---|---|---|---|---|---|---|---|---|
| L3M | 255494 | 16369 | 15557 | 13688 | 1918 | 789 | 48321 | 18.9 | 3677 | 60 | 257 |
| L6M | 669769 | 36697 | 34877 | 30400 | 4092 | 1414 | 107480 | 16.0 | 4112 | 54 | 290 |
| HOLD | 968266 | 65626 | 62371 | 54312 | 8246 | 3509 | 194063 | 20.0 | 3732 | 67 | 261 |
| PRE | 471952 | 37587 | 35724 | 29928 | 5914 | 4406 | 113559 | 24.1 | 1320 | 51 | 90 |
| X' | 470362 | 52562 | 49956 | 37456 | 13050 | 9493 | 162518 | 34.6 | 2084 | 122 | 139 |

Reading: the three big pieces are the fee, the entry excess (0.23 pt on EVERY contract) and the market-cut excess; the 08:30-08:44 bump is a rounding error at stack level (about $40-50/wk against ~$21k/wk of L6M gross), so avoiding the 08:30 fill cannot be worth more than that and any rule that gives up entries or exits to dodge it must be judged against that ceiling.

### 1.2 Ranking: books by cost per dollar earned (cost / net, lower is better; cost > net means the book is net negative after cost)

**L3M**

| book | trades | contracts | gross $ | cost $ | net $ | cost per $ net | cost % gross | cost $/wk | net $/wk | cost $/trade | net $/contract |
|---|---|---|---|---|---|---|---|---|---|---|---|
| O7 | 20 | 20 | 6005 | 296 | 5709 | 0.05 | 4.9 | 23 | 434 | 14.8 | 285.4 |
| U7 | 121 | 330 | 63097 | 4488 | 58609 | 0.08 | 7.1 | 342 | 4460 | 37.1 | 177.6 |
| H7 | 84 | 150 | 13804 | 2119 | 11685 | 0.18 | 15.4 | 161 | 889 | 25.2 | 77.9 |
| P7 | 467 | 1530 | 120025 | 21929 | 98096 | 0.22 | 18.3 | 1669 | 7465 | 47.0 | 64.1 |
| K7 | 687 | 790 | 47560 | 11334 | 36226 | 0.31 | 23.8 | 863 | 2757 | 16.5 | 45.9 |
| M7 | 336 | 402 | 5976 | 5888 | 88 | 67.04 | 98.5 | 448 | 7 | 17.5 | 0.2 |
| A7 | 160 | 160 | -971 | 2268 | -3239 | net<0 | gross<0 | 173 | -247 | 14.2 | -20.2 |

**L6M**

| book | trades | contracts | gross $ | cost $ | net $ | cost per $ net | cost % gross | cost $/wk | net $/wk | cost $/trade | net $/contract |
|---|---|---|---|---|---|---|---|---|---|---|---|
| O7 | 46 | 46 | 10742 | 694 | 10048 | 0.07 | 6.5 | 27 | 384 | 15.1 | 218.4 |
| H7 | 176 | 329 | 53350 | 4563 | 48786 | 0.09 | 8.6 | 175 | 1866 | 25.9 | 148.3 |
| U7 | 271 | 731 | 105206 | 9933 | 95272 | 0.10 | 9.4 | 380 | 3645 | 36.7 | 130.3 |
| P7 | 1037 | 3469 | 344599 | 49282 | 295317 | 0.17 | 14.3 | 1885 | 11298 | 47.5 | 85.1 |
| K7 | 1553 | 1780 | 132978 | 25282 | 107696 | 0.23 | 19.0 | 967 | 4120 | 16.3 | 60.5 |
| A7 | 353 | 353 | 20714 | 4891 | 15823 | 0.31 | 23.6 | 187 | 605 | 13.9 | 44.8 |
| M7 | 733 | 874 | 2181 | 12835 | -10654 | net<0 | 588.5 | 491 | -408 | 17.5 | -12.2 |

**HOLD**

| book | trades | contracts | gross $ | cost $ | net $ | cost per $ net | cost % gross | cost $/wk | net $/wk | cost $/trade | net $/contract |
|---|---|---|---|---|---|---|---|---|---|---|---|
| O7 | 104 | 104 | 28356 | 1559 | 26797 | 0.06 | 5.5 | 30 | 515 | 15.0 | 257.7 |
| U7 | 484 | 1290 | 125129 | 17905 | 107224 | 0.17 | 14.3 | 344 | 2062 | 37.0 | 83.1 |
| P7 | 1838 | 6163 | 551061 | 88051 | 463010 | 0.19 | 16.0 | 1693 | 8904 | 47.9 | 75.1 |
| A7 | 564 | 564 | 42234 | 7815 | 34419 | 0.23 | 18.5 | 150 | 662 | 13.9 | 61.0 |
| H7 | 307 | 580 | 35822 | 8298 | 27524 | 0.30 | 23.2 | 160 | 529 | 27.0 | 47.5 |
| K7 | 2747 | 3179 | 186248 | 45359 | 140889 | 0.32 | 24.4 | 872 | 2709 | 16.5 | 44.3 |
| M7 | 1408 | 1679 | -584 | 25077 | -25661 | net<0 | gross<0 | 482 | -493 | 17.8 | -15.3 |

### 1.3 Book x session where cost is more than half of gross (L6M or L3M), the places a cost cut is worth most

| window | book | session | trades | gross $ | cost $ | net $ | cost % gross |
|---|---|---|---|---|---|---|---|
| L3M | A7 | asia | 160 | -971 | 2268 | -3239 | gross<0 |
| L3M | K7 | nyam | 88 | -1844 | 1263 | -3107 | gross<0 |
| L3M | M7 | london | 248 | -5159 | 4671 | -9830 | gross<0 |
| L3M | P7 | nyam | 58 | -3765 | 1811 | -5576 | gross<0 |
| L6M | K7 | london | 427 | 11892 | 7347 | 4545 | 62 |
| L6M | K7 | nyam | 188 | 5175 | 2656 | 2519 | 51 |
| L6M | M7 | london | 519 | -8433 | 9814 | -18247 | gross<0 |
| L6M | P7 | london | 346 | 14036 | 11389 | 2647 | 81 |
| HOLD | H7 | nyam | 73 | 211 | 1025 | -814 | 486 |
| HOLD | K7 | nyam | 408 | -12749 | 5839 | -18588 | gross<0 |
| HOLD | M7 | london | 976 | -15691 | 18950 | -34641 | gross<0 |

### 1.4 Micro contracts for the odd lot (analytic, no engine cell)

MNQ is 1/10 of an NQ contract at $1.78 RT (FEES.md, proxy) = $17.80 per NQ-equivalent against $4.84 for NQ: micros cost 3.7x more per unit of exposure, so they can only be used for the fractional remainder, never to cut the fee bill. Typical use: the half-size rules round an odd lot UP (7 -> 4, user lots K7 4, M7 4, U7 7, P7 12/7/7, H7 7, A7 2); holding 3 NQ + 5 MNQ = 3.5 exactly costs 3 x 4.84 + 5 x 1.78 = $23.4 vs 4 x 4.84 = $19.4, i.e. +$4.0 per trade, and the same for entry slip (+0.23 pt on 5 micro contracts is $0.23 x 5 x $2 = $2.3 vs 0.5 NQ $2.3, the same per unit). It removes a 14% size overshoot on odd-lot half trades; with P7 net per contract about $85 (L6M) the overshoot is worth about 0.5 x $85 x (share of halved trades) in variance terms but zero in expectation (the rounding is symmetric across lots), so it is a risk-exactness tool, not an edge. Verdict: no cell run; it would only matter inside a sizing layer that halves, and costs +$4 per such trade.


## 2. Exact cells (JN05W2 base, all layers ON; delta vs JN05W2 on the same months; cut % positive = shallower maxDD)

Columns: L3M/L6M/HOLD = maxDD cut % / d mean $/wk (engine) / d mean $/wk at $4.84 and live-excess / worst-week change / gate (tolerant) ; x44 = DD cut with 2026-W44 removed from both; b5 = 5 best base weeks kept; w2l = winning weeks turned losing. A window shows only when all its months exist.

### BR  breadth-extreme skip to the other books (parent BR3S = P7 breadth_ext15 == 3 skip, already in JN05W2)

| cell | months | L3M cut / d mean / $4.84 / live-exc / d ww / gate / x44 cut / b5 / w2l | L6M cut / d mean / live-exc / gate | HOLD cut / d mean | PRE cut / d mean |
|---|---|---|---|---|---|
| BR_K7_X15 | 3 | -7.2 / -3577 / -3566 / -3545 / -3809 / False / 11.1 / 0.88 / 0 | - / - / - / - | - / - | - / - |
| BR_K7_H15 | 3 | 14.8 / -602 / -598 / -584 / 7753 / False / 2.5 / 0.98 / 0 | - / - / - / - | - / - | - / - |
| BR_U7_X15 | 3 | 0.5 / -1409 / -1376 / -1307 / 2643 / False / 0.7 / 0.98 / 1 | - / - / - / - | - / - | - / - |
| BR_U7_H15 | 3 | 4.8 / -540 / -519 / -470 / 3687 / True / 0.1 / 0.99 / 0 | - / - / - / - | - / - | - / - |
| BR_H7_X15 | 3 | -12.2 / -819 / -816 / -813 / -6390 / False / -5.3 / 0.99 / 0 | - / - / - / - | - / - | - / - |
| BR_H7_H15 | 3 | -4.6 / -82 / -77 / -61 / -2403 / False / -0.4 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| BR_M7_X15 | 3 | -6.1 / -1491 / -1489 / -1490 / -2520 / False / 3.9 / 0.97 / 0 | - / - / - / - | - / - | - / - |
| BR_M7_H15 | 3 | 1.2 / 144 / 147 / 157 / 615 / True / 5.7 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| BR_A7_X15 | 3 | 0.0 / 0 / 0 / 0 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| BR_A7_H15 | 3 | 0.0 / 0 / 0 / 0 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| BR_O7_X15 | 3 | 0.0 / 0 / 0 / 0 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| BR_O7_H15 | 3 | 0.0 / 0 / 0 / 0 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| BR_ALL6_X15 | 3 | -16.1 / -5079 / -5030 / -4925 / -6601 / False / 24.7 / 0.85 / 0 | - / - / - / - | - / - | - / - |
| BR_ALL6_H15 | 3 | 10.2 / -1631 / -1601 / -1526 / 6505 / False / 14.5 / 0.94 / 0 | - / - / - / - | - / - | - / - |
| BR_P7_X30 | 3 | -9.3 / -4193 / -4146 / -4051 / 7835 / False / -31.6 / 0.84 / 1 | - / - / - / - | - / - | - / - |
| BR_P7_X5 | 3 | 0.0 / 0 / 0 / 0 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| BR_P7_H2 | 3 | 0.4 / -1321 / -1286 / -1222 / 187 / False / -6.5 / 0.97 / 0 | - / - / - / - | - / - | - / - |
| BR_P7_V19 | 3 | 0.0 / 0 / 0 / 0 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |

### EV  skips / half before scheduled events (calendar from 2024-10; identity before)

| cell | months | L3M cut / d mean / $4.84 / live-exc / d ww / gate / x44 cut / b5 / w2l | L6M cut / d mean / live-exc / gate | HOLD cut / d mean | PRE cut / d mean |
|---|---|---|---|---|---|
| EV_T0830_P10_S | 3 | 0.0 / -37 / -36 / -29 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| EV_T0830_P10_H | 3 | 0.0 / 51 / 52 / 55 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| EV_T0830_P20_S | 3 | 0.0 / -71 / -70 / -62 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| EV_T0830_P20_H | 3 | 0.0 / 51 / 52 / 55 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| EV_T0830_P30_S | 3 | 0.0 / -71 / -70 / -62 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| EV_T0830_P30_H | 3 | 0.0 / 51 / 52 / 55 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| EV_T0830_P60_S | 3 | 0.0 / 206 / 209 / 222 / 0 / True / -0.7 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| EV_T0830_P60_H | 3 | 0.0 / 102 / 103 / 107 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| EV_FOMC_P15_S | 3 | 0.0 / 0 / 0 / 0 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| EV_FOMC_P15_H | 3 | 0.0 / 0 / 0 / 0 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| EV_FOMC_P30_S | 3 | 0.0 / 0 / 0 / 0 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| EV_FOMC_P30_H | 3 | 0.0 / 0 / 0 / 0 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| EV_FOMC_P60_S | 3 | 0.0 / 0 / 0 / 0 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| EV_FOMC_P60_H | 3 | 0.0 / 0 / 0 / 0 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| EV_EARN_Q60_S | 3 | 0.0 / 0 / 0 / 0 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| EV_EARN_Q60_H | 3 | 0.0 / 0 / 0 / 0 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| EV_EARN_Q120_S | 3 | 0.0 / -91 / -91 / -91 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| EV_EARN_Q120_H | 3 | 0.0 / 0 / 0 / 0 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |

### RB  range used up AND breadth / event day (HAR+CME forecast; plain range rule is W-EC)

| cell | months | L3M cut / d mean / $4.84 / live-exc / d ww / gate / x44 cut / b5 / w2l | L6M cut / d mean / live-exc / gate | HOLD cut / d mean | PRE cut / d mean |
|---|---|---|---|---|---|

### TG  target 1-2 ticks short

| cell | months | L3M cut / d mean / $4.84 / live-exc / d ww / gate / x44 cut / b5 / w2l | L6M cut / d mean / live-exc / gate | HOLD cut / d mean | PRE cut / d mean |
|---|---|---|---|---|---|
| TG1_K7 | 3 | -0.2 / 455 / 457 / 464 / -105 / True / -0.3 / 1.03 / 0 | - / - / - / - | - / - | - / - |
| TG1_P7 | 3 | -0.2 / -230 / -230 / -230 / -95 / True / -0.5 / 0.99 / 0 | - / - / - / - | - / - | - / - |
| TG1_U7 | 3 | -0.1 / -69 / -69 / -69 / -50 / True / -0.2 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| TG1_H7 | 3 | -0.1 / -22 / -22 / -22 / -30 / True / -0.1 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| TG1_A7 | 3 | -0.1 / 208 / 208 / 209 / -45 / True / -0.1 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| TG1_ALL | 3 | -0.7 / 368 / 369 / 377 / -360 / True / -1.3 / 1.02 / 0 | - / - / - / - | - / - | - / - |
| TG2_U7 | 3 | -0.2 / -138 / -138 / -138 / -100 / True / -0.5 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| TG2_H7 | 3 | -0.1 / -36 / -36 / -38 / -60 / True / -0.2 / 1.00 / 0 | - / - / - / - | - / - | - / - |

### LE  passive vs market entry per book / session (through-1-tick fill rule, market on timeout)

| cell | months | L3M cut / d mean / $4.84 / live-exc / d ww / gate / x44 cut / b5 / w2l | L6M cut / d mean / live-exc / gate | HOLD cut / d mean | PRE cut / d mean |
|---|---|---|---|---|---|

### WK  work the cut with a resting limit (per book / session / 08:30)

| cell | months | L3M cut / d mean / $4.84 / live-exc / d ww / gate / x44 cut / b5 / w2l | L6M cut / d mean / live-exc / gate | HOLD cut / d mean | PRE cut / d mean |
|---|---|---|---|---|---|

### SJ  join-then-market stop seconds

| cell | months | L3M cut / d mean / $4.84 / live-exc / d ww / gate / x44 cut / b5 / w2l | L6M cut / d mean / live-exc / gate | HOLD cut / d mean | PRE cut / d mean |
|---|---|---|---|---|---|

## 3. Hits and auto-expansions (PART 0)

Hits (L3M tolerant gate and d mean > 0): BR_M7_H15, EV_T0830_P10_H, EV_T0830_P20_H, EV_T0830_P30_H, EV_T0830_P60_S, EV_T0830_P60_H, TG1_K7, TG1_A7, TG1_ALL

Auto-expansions launched (expansion of <parent>):

- HIT BR_M7_H15: L3M cut 1.2% d mean 144 (adj 157) -> promoted to L6M/HOLD/GAP/PRE and battery launched
- - BR_M7_H15_Sasi: expansion of BR_M7_H15
- - BR_M7_H15_Slon: expansion of BR_M7_H15
- - BR_M7_H15_Snya: expansion of BR_M7_H15
- - BR_M7_H15_Snyp: expansion of BR_M7_H15
- - BR_M7_H15_xt5: expansion of BR_M7_H15
- - BR_M7_H15_30: expansion of BR_M7_H15
- - BR_M7_H15_v19: expansion of BR_M7_H15
- - BR_M7_H15_G2: expansion of BR_M7_H15
- - BR_M7_H15_K7: expansion of BR_M7_H15
- - BR_M7_H15_P7: expansion of BR_M7_H15
- - BR_M7_H15_U7: expansion of BR_M7_H15
- - BR_M7_H15_H7: expansion of BR_M7_H15
- - BR_M7_H15_A7: expansion of BR_M7_H15
- - BR_M7_H15_O7: expansion of BR_M7_H15
- - NOT SUPPORTED in this registry: size-UP mirror (needs a size-up hook), carry to next session, fresh/rechase split, joint (sent to W-JV)
- HIT EV_T0830_P30_H: L3M cut 0.0% d mean 51 (adj 55) -> promoted to L6M/HOLD/GAP/PRE and battery launched
- - EV_T0830_P30_H_p5: expansion of EV_T0830_P30_H
- - EV_T0830_P30_H_p15: expansion of EV_T0830_P30_H
- - EV_T0830_P30_H_p45: expansion of EV_T0830_P30_H
- - EV_T0830_P30_H_p90: expansion of EV_T0830_P30_H
- - EV_T0830_P30_H_sasi: expansion of EV_T0830_P30_H
- - EV_T0830_P30_H_slon: expansion of EV_T0830_P30_H
- - EV_T0830_P30_H_snya: expansion of EV_T0830_P30_H
- - EV_T0830_P30_H_snyp: expansion of EV_T0830_P30_H
- - EV_T0830_P30_H_oth: expansion of EV_T0830_P30_H
- - EV_T0830_P30_H_kCPI: expansion of EV_T0830_P30_H
- - EV_T0830_P30_H_kPCE: expansion of EV_T0830_P30_H
- - EV_T0830_P30_H_kISM_MFG: expansion of EV_T0830_P30_H
- - EV_T0830_P30_H_kFOMC: expansion of EV_T0830_P30_H
- - NOT SUPPORTED in this registry: size-UP mirror (needs a size-up hook), carry to next session, fresh/rechase split, joint (sent to W-JV)
- HIT EV_T0830_P60_S: L3M cut 0.0% d mean 206 (adj 222) -> promoted to L6M/HOLD/GAP/PRE and battery launched
- - EV_T0830_P60_S_p5: expansion of EV_T0830_P60_S
- - EV_T0830_P60_S_p15: expansion of EV_T0830_P60_S
- - EV_T0830_P60_S_p45: expansion of EV_T0830_P60_S
- - EV_T0830_P60_S_p90: expansion of EV_T0830_P60_S
- - EV_T0830_P60_S_sasi: expansion of EV_T0830_P60_S
- - EV_T0830_P60_S_slon: expansion of EV_T0830_P60_S
- - EV_T0830_P60_S_snya: expansion of EV_T0830_P60_S
- - EV_T0830_P60_S_snyp: expansion of EV_T0830_P60_S
- - EV_T0830_P60_S_oth: expansion of EV_T0830_P60_S
- - EV_T0830_P60_S_kCPI: expansion of EV_T0830_P60_S
- - EV_T0830_P60_S_kPCE: expansion of EV_T0830_P60_S
- - EV_T0830_P60_S_kISM_MFG: expansion of EV_T0830_P60_S
- - EV_T0830_P60_S_kFOMC: expansion of EV_T0830_P60_S
- HIT EV_T0830_P60_H: L3M cut 0.0% d mean 102 (adj 107) -> promoted to L6M/HOLD/GAP/PRE and battery launched
- - EV_T0830_P60_H_p5: expansion of EV_T0830_P60_H
- - EV_T0830_P60_H_p15: expansion of EV_T0830_P60_H
- - EV_T0830_P60_H_p45: expansion of EV_T0830_P60_H
- - EV_T0830_P60_H_p90: expansion of EV_T0830_P60_H
- - EV_T0830_P60_H_sasi: expansion of EV_T0830_P60_H
- - EV_T0830_P60_H_slon: expansion of EV_T0830_P60_H
- - EV_T0830_P60_H_snya: expansion of EV_T0830_P60_H
- - EV_T0830_P60_H_snyp: expansion of EV_T0830_P60_H
- - EV_T0830_P60_H_oth: expansion of EV_T0830_P60_H
- - EV_T0830_P60_H_kCPI: expansion of EV_T0830_P60_H
- - EV_T0830_P60_H_kPCE: expansion of EV_T0830_P60_H
- - EV_T0830_P60_H_kISM_MFG: expansion of EV_T0830_P60_H
- - EV_T0830_P60_H_kFOMC: expansion of EV_T0830_P60_H
- - NOT SUPPORTED in this registry: size-UP mirror (needs a size-up hook), carry to next session, fresh/rechase split, joint (sent to W-JV)
- HIT EV_T0830_P10_H: L3M cut 0.0% d mean 51 (adj 55) -> promoted to L6M/HOLD/GAP/PRE and battery launched
- - EV_T0830_P10_H_p5: expansion of EV_T0830_P10_H
- - EV_T0830_P10_H_p15: expansion of EV_T0830_P10_H
- - EV_T0830_P10_H_p45: expansion of EV_T0830_P10_H
- - EV_T0830_P10_H_p90: expansion of EV_T0830_P10_H
- - EV_T0830_P10_H_sasi: expansion of EV_T0830_P10_H
- - EV_T0830_P10_H_slon: expansion of EV_T0830_P10_H
- - EV_T0830_P10_H_snya: expansion of EV_T0830_P10_H
- - EV_T0830_P10_H_snyp: expansion of EV_T0830_P10_H
- - EV_T0830_P10_H_oth: expansion of EV_T0830_P10_H
- - EV_T0830_P10_H_kCPI: expansion of EV_T0830_P10_H
- - EV_T0830_P10_H_kPCE: expansion of EV_T0830_P10_H
- - EV_T0830_P10_H_kISM_MFG: expansion of EV_T0830_P10_H
- - EV_T0830_P10_H_kFOMC: expansion of EV_T0830_P10_H
- HIT EV_T0830_P20_H: L3M cut 0.0% d mean 51 (adj 55) -> promoted to L6M/HOLD/GAP/PRE and battery launched
- - EV_T0830_P20_H_p5: expansion of EV_T0830_P20_H
- - EV_T0830_P20_H_p15: expansion of EV_T0830_P20_H
- - EV_T0830_P20_H_p45: expansion of EV_T0830_P20_H
- - EV_T0830_P20_H_p90: expansion of EV_T0830_P20_H
- - EV_T0830_P20_H_sasi: expansion of EV_T0830_P20_H
- - EV_T0830_P20_H_slon: expansion of EV_T0830_P20_H
- - EV_T0830_P20_H_snya: expansion of EV_T0830_P20_H
- - EV_T0830_P20_H_snyp: expansion of EV_T0830_P20_H
- - EV_T0830_P20_H_oth: expansion of EV_T0830_P20_H
- - EV_T0830_P20_H_kCPI: expansion of EV_T0830_P20_H
- - EV_T0830_P20_H_kPCE: expansion of EV_T0830_P20_H
- - EV_T0830_P20_H_kISM_MFG: expansion of EV_T0830_P20_H
- - EV_T0830_P20_H_kFOMC: expansion of EV_T0830_P20_H
- - NOT SUPPORTED in this registry: size-UP mirror (needs a size-up hook), carry to next session, fresh/rechase split, joint (sent to W-JV)
- HIT TG1_K7: L3M cut -0.2% d mean 455 (adj 464) -> promoted to L6M/HOLD/GAP/PRE and battery launched
- - TG1_K7_t3: expansion of TG1_K7
- - TG1_K7_t4: expansion of TG1_K7
- - TG1_K7_K7: expansion of TG1_K7
- - TG1_K7_P7: expansion of TG1_K7
- - TG1_K7_U7: expansion of TG1_K7
- - TG1_K7_H7: expansion of TG1_K7
- - TG1_K7_M7: expansion of TG1_K7
- - TG1_K7_A7: expansion of TG1_K7
- - TG1_K7_sasi: expansion of TG1_K7
- - TG1_K7_slon: expansion of TG1_K7
- - TG1_K7_snya: expansion of TG1_K7
- - TG1_K7_snyp: expansion of TG1_K7
- HIT TG1_A7: L3M cut -0.1% d mean 208 (adj 209) -> promoted to L6M/HOLD/GAP/PRE and battery launched
- - TG1_A7_t3: expansion of TG1_A7
- - TG1_A7_t4: expansion of TG1_A7
- - TG1_A7_K7: expansion of TG1_A7
- - TG1_A7_P7: expansion of TG1_A7
- - TG1_A7_U7: expansion of TG1_A7
- - TG1_A7_H7: expansion of TG1_A7
- - TG1_A7_M7: expansion of TG1_A7
- - TG1_A7_A7: expansion of TG1_A7
- - TG1_A7_sasi: expansion of TG1_A7
- - TG1_A7_slon: expansion of TG1_A7
- - TG1_A7_snya: expansion of TG1_A7
- - TG1_A7_snyp: expansion of TG1_A7
- - NOT SUPPORTED in this registry: size-UP mirror (needs a size-up hook), carry to next session, fresh/rechase split, joint (sent to W-JV)
- HIT TG1_ALL: L3M cut -0.7% d mean 368 (adj 377) -> promoted to L6M/HOLD/GAP/PRE and battery launched
- - TG1_ALL_t3: expansion of TG1_ALL
- - TG1_ALL_t4: expansion of TG1_ALL
- - TG1_ALL_K7: expansion of TG1_ALL
- - TG1_ALL_P7: expansion of TG1_ALL
- - TG1_ALL_U7: expansion of TG1_ALL
- - TG1_ALL_H7: expansion of TG1_ALL
- - TG1_ALL_M7: expansion of TG1_ALL
- - TG1_ALL_A7: expansion of TG1_ALL
- - TG1_ALL_sasi: expansion of TG1_ALL
- - TG1_ALL_slon: expansion of TG1_ALL
- - TG1_ALL_snya: expansion of TG1_ALL
- - TG1_ALL_snyp: expansion of TG1_ALL
- - NOT SUPPORTED in this registry: size-UP mirror (needs a size-up hook), carry to next session, fresh/rechase split, joint (sent to W-JV)

## 4. Not run / limits
- Passive-entry fill rule: a print through the limit by 1 tick (primary). Engine has no queue position model; real fill rates for resting limits are not in the frozen live set. Treat LE rows as an upper bound on fills.
- 08:30: bump of +1.36 pt applies to market/stop exits starting 08:30-08:44 ET and is NOT inside the engine; it is added in the live-exc column only.
- Stop-limit cut, depth-conditional passive entry and per-slot refits (SMART_B not-run list) are queued only after the first hits.

