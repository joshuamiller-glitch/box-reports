# DS3_BOOK_WEIGHTS - per-book lot weights (risk budget) on the live stack, interim (DIS-AH, CAL, 2026-11-04)
SIZER / RISK-BUDGET question. Research only, nothing live, no PASS claims; the live lot order (session lots -> A06/B02 -> ER Q1-A -> zone HALF) is unchanged unless the user decides. Scope note l2vast/ds3/prereg/DISAH_scope.md sha256 fcd0a2928610bd2af7704983792a903cbbb645f17ef888860fae93e089103857 (DECISIONS.md, before any outcome). Code l2vast/ds3/code/discover/{diah.py, diah_report.py}; out/diah_cells.csv, diah_rolling.csv; ledger DIS_AH (61 cells); n_tested DISAH = 61.

## 0. Method, hook, dead lookup
Engine: sizer_harness ts2 (run_v13t_ts2), Q1-A reference, locks re-run in every cell (unlike the leave-one-out in DS3_CONCENTRATION.md), integer lots as live, corrected carrying weeks (L6M/HOLD 202630-202637, PRE 202506-202509, X' 202321-202341), weekly label weeks, live lots, lock-reset phase 0 (PA9 over nine phases for the best handful). **Hook:** the engine takes one per-row multiplier m applied after the session lots and A06/B02 (round, min 1 lot) and before the zone HALF. The book weight is folded into that slot (m = Q1-A ER multiplier x book weight, one rounding of session_lots x m). There is NO separate book-weight hook with its own rounding after the ER step, so the live composition (ER rounded, then something else) is approximated by product-then-round; the engine was not edited. Weight 0 = extra_skip (a zero multiplier keeps the 1-lot minimum). Consequence of integer lots with a 1-lot minimum: PB (1 lot) is unchanged for any weight 0.5-1 (PB=0.5 and 0.75 equal live), KB (2 lots) is unchanged at 0.75, and MV (2 lots) moves only at 0.5 and 1.25-1.5.
Dead lookup (cited): DS3_LOTS_DD (E1, lots re-solved per book and session under a drawdown constraint on the one-convention engine, in-sample table plus walk-forward read separately); SIZER_S35 / S35B per-book lock cells (scope=PerBook, ts2, 290 rows, locks not weights); T-SIZER S-series ER / vol-scaled lots (Q1-A kept); THPC3 / EXP1 'perbook' rows are profit rules; EQR lots factor; SDA2 sigdecay book cells are exit rules. No DEAD_CELLS row sets a per-book lot multiplier on Q1-A ts2 with locks re-run, so the grid is new but is the same family as E1 and is read with the E1 caution (in-sample drawdown-constrained lot solutions did not hold out of sample there; see DS3_LOTS_DD walk-forward).
Live reference (live): HOLD mean 29078/wk, maxDD 122025, Calmar 0.24; PRE 16118 / 75057 / 0.21; L6M 45311 / 62576 / 0.72. Calmar = mean weekly P&L / maxDD (weekly cumulative).

## 1. PE alone (drawdown first)
| cell | HOLD mean | HOLD maxDD | HOLD Calmar | HOLD worst | PRE mean | PRE maxDD | PRE Calmar | PRE worst | L6M mean | L6M maxDD | L6M Calmar | L6M worst |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| LIVE | 29078 | 122025 | 0.24 | -62576 | 16118 | 75057 | 0.21 | -61712 | 45311 | 62576 | 0.72 | -62576 |
| PE=0 | 13623 | 32922 | 0.41 | -28180 | 6222 | 72287 | 0.09 | -31150 | 17585 | 32922 | 0.53 | -28180 |
| PE=0.5 | 22367 | 82360 | 0.27 | -45137 | 11329 | 61282 | 0.18 | -43842 | 33270 | 41814 | 0.80 | -41814 |
| PE=0.75 | 25197 | 98415 | 0.26 | -51541 | 12791 | 65272 | 0.20 | -49199 | 38763 | 46604 | 0.83 | -46604 |
| PE=1.25 | 32001 | 145011 | 0.22 | -81231 | 17239 | 104503 | 0.16 | -77890 | 51484 | 56192 | 0.92 | -56192 |
| PE=1.5 | 35473 | 174681 | 0.20 | -99246 | 20358 | 95146 | 0.21 | -81326 | 57771 | 79911 | 0.72 | -79911 |

| cell | X' mean | X' maxDD | X' Calmar | X' worst | MID mean | MID maxDD | MID Calmar | MID worst | ALL mean | ALL maxDD | ALL Calmar | ALL worst |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| LIVE | 1863 | 49417 | 0.04 | -27157 | 16114 | 59703 | 0.27 | -29860 | 13477 | 122025 | 0.11 | -62576 |
| PE=0 | 2664 | 28322 | 0.09 | -15719 | 9883 | 12175 | 0.81 | -9550 | 5645 | 87183 | 0.06 | -31889 |
| PE=0.5 | 2219 | 34780 | 0.06 | -21209 | 13350 | 37223 | 0.36 | -20327 | 9918 | 82696 | 0.12 | -45137 |
| PE=0.75 | 2280 | 40215 | 0.06 | -23397 | 13541 | 46873 | 0.29 | -24130 | 11324 | 98415 | 0.12 | -51541 |
| PE=1.25 | -28 | 72497 | -0.00 | -30814 | 16944 | 63780 | 0.27 | -32168 | 14551 | 145011 | 0.10 | -81231 |
| PE=1.5 | -232 | 82544 | -0.00 | -36049 | 18399 | 75435 | 0.24 | -39322 | 16671 | 174681 | 0.10 | -99246 |

By year (mean $/wk, maxDD $; carry weeks not dropped in the by-year view):

| cell | 2023 mean | 2023 maxDD | 2024 mean | 2024 maxDD | 2025 mean | 2025 maxDD | 2026 mean | 2026 maxDD |
|--|--|--|--|--|--|--|--|--|
| LIVE | 1837 | 80802 | 14431 | 75057 | 13557 | 88180 | 22571 | 122025 |
| PE=0 | 930 | 51833 | 7250 | 41530 | 3984 | 75389 | 9891 | 87183 |
| PE=0.5 | 1215 | 57470 | 11376 | 61282 | 8702 | 67737 | 17345 | 82696 |
| PE=0.75 | 1511 | 65269 | 12751 | 65272 | 9972 | 74102 | 19935 | 98415 |
| PE=1.25 | 1134 | 91330 | 15464 | 104503 | 14924 | 106326 | 24922 | 145011 |
| PE=1.5 | 1301 | 110995 | 17847 | 95146 | 17644 | 124032 | 27755 | 174681 |

Reading: PE x0.5 cuts HOLD maxDD from 122025 to 82360 (-33%) and PRE maxDD from 75057 to 61282, at a mean cost of 23% in HOLD, 30% in PRE, 27% in L6M. Calmar improves in HOLD and L6M and falls in PRE. PE x0 (the DIS-AF leave-one-out, now with locks re-run) gives HOLD Calmar 0.41 (DIS-AF subtraction said 0.41) and PRE 0.09. PE x1.25-1.5 raises the mean and the maxDD more than proportionally.

## 2. PE x HM
| cell | HOLD mean | HOLD maxDD | HOLD Calmar | HOLD worst | PRE mean | PRE maxDD | PRE Calmar | PRE worst | L6M mean | L6M maxDD | L6M Calmar | L6M worst |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| LIVE | 29078 | 122025 | 0.24 | -62576 | 16118 | 75057 | 0.21 | -61712 | 45311 | 62576 | 0.72 | -62576 |
| PE=0.5,HM=1.25 | 24497 | 77467 | 0.32 | -43041 | 11899 | 66071 | 0.18 | -46757 | 35372 | 43041 | 0.82 | -43041 |
| PE=0.5,HM=1.5 | 25608 | 76052 | 0.34 | -45608 | 11764 | 76003 | 0.15 | -51396 | 36734 | 45608 | 0.81 | -45608 |
| PE=0.75,HM=1.25 | 27327 | 93522 | 0.29 | -47830 | 13360 | 70062 | 0.19 | -52114 | 40865 | 47830 | 0.85 | -47830 |
| PE=0.75,HM=1.5 | 28437 | 92107 | 0.31 | -50397 | 13226 | 79994 | 0.17 | -56752 | 42227 | 50397 | 0.84 | -50397 |
| PE=0,HM=1.25 | 15753 | 32633 | 0.48 | -29406 | 6790 | 77089 | 0.09 | -36772 | 19688 | 32633 | 0.60 | -29406 |
| PE=0,HM=1.5 | 16863 | 33732 | 0.50 | -31973 | 6655 | 95213 | 0.07 | -44075 | 21049 | 33732 | 0.62 | -31973 |
| PE=1,HM=0.5 | 25914 | 125253 | 0.21 | -70979 | 15656 | 69740 | 0.22 | -56855 | 41715 | 58415 | 0.71 | -58415 |
| PE=1,HM=1.25 | 31208 | 117132 | 0.27 | -63802 | 16687 | 78749 | 0.21 | -64627 | 47413 | 63802 | 0.74 | -63802 |
| PE=1,HM=1.5 | 32319 | 115717 | 0.28 | -66369 | 16553 | 88681 | 0.19 | -69266 | 48775 | 66369 | 0.73 | -66369 |

| cell | X' mean | X' maxDD | X' Calmar | X' worst | MID mean | MID maxDD | MID Calmar | MID worst | ALL mean | ALL maxDD | ALL Calmar | ALL worst |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| LIVE | 1863 | 49417 | 0.04 | -27157 | 16114 | 59703 | 0.27 | -29860 | 13477 | 122025 | 0.11 | -62576 |
| PE=0.5,HM=1.25 | 2254 | 39889 | 0.06 | -20972 | 14399 | 41378 | 0.35 | -23454 | 10611 | 82510 | 0.13 | -49327 |
| PE=0.5,HM=1.5 | 1978 | 42079 | 0.05 | -22522 | 14138 | 39978 | 0.35 | -24670 | 10815 | 88340 | 0.12 | -51396 |
| PE=0.75,HM=1.25 | 2316 | 45324 | 0.05 | -23160 | 14590 | 51028 | 0.29 | -27257 | 12018 | 93522 | 0.13 | -52114 |
| PE=0.75,HM=1.5 | 2040 | 47514 | 0.04 | -25636 | 14328 | 49628 | 0.29 | -28474 | 12222 | 92107 | 0.13 | -56752 |
| PE=0,HM=1.25 | 2699 | 31899 | 0.08 | -15482 | 10932 | 16330 | 0.67 | -12677 | 6338 | 91393 | 0.07 | -38122 |
| PE=0,HM=1.5 | 2423 | 36209 | 0.07 | -16095 | 10670 | 17031 | 0.63 | -13893 | 6542 | 95213 | 0.07 | -44075 |
| PE=1,HM=0.5 | 1931 | 41136 | 0.05 | -27963 | 14761 | 54274 | 0.27 | -28110 | 12628 | 125253 | 0.10 | -70979 |
| PE=1,HM=1.25 | 1899 | 54526 | 0.03 | -28231 | 17163 | 63858 | 0.27 | -32970 | 14171 | 117132 | 0.12 | -64627 |
| PE=1,HM=1.5 | 1623 | 56716 | 0.03 | -32142 | 16902 | 62458 | 0.27 | -34187 | 14374 | 115717 | 0.12 | -69266 |

By year:

| cell | 2023 mean | 2023 maxDD | 2024 mean | 2024 maxDD | 2025 mean | 2025 maxDD | 2026 mean | 2026 maxDD |
|--|--|--|--|--|--|--|--|--|
| LIVE | 1837 | 80802 | 14431 | 75057 | 13557 | 88180 | 22571 | 122025 |
| PE=0.5,HM=1.25 | 1142 | 68162 | 11972 | 66071 | 9215 | 72432 | 19047 | 82510 |
| PE=0.5,HM=1.5 | 900 | 67476 | 12186 | 76003 | 9376 | 66943 | 19685 | 88340 |
| PE=0.75,HM=1.25 | 1437 | 75960 | 13348 | 70062 | 10485 | 78797 | 21637 | 93522 |
| PE=0.75,HM=1.5 | 1195 | 75275 | 13561 | 79994 | 10646 | 73748 | 22275 | 92107 |
| PE=0,HM=1.25 | 857 | 57920 | 7844 | 39419 | 4497 | 79807 | 11594 | 91393 |
| PE=0,HM=1.5 | 615 | 56642 | 8058 | 41071 | 4658 | 95213 | 12232 | 94977 |
| PE=1,HM=0.5 | 2217 | 67361 | 13850 | 69740 | 12717 | 83900 | 20308 | 125253 |
| PE=1,HM=1.25 | 1764 | 92070 | 15028 | 78749 | 14070 | 92875 | 24273 | 117132 |
| PE=1,HM=1.5 | 1522 | 91158 | 15241 | 88681 | 14231 | 86765 | 24911 | 115717 |

## 3. Risk-parity-style weights (inverse of each book's own weekly maxDD in HOLD / PRE / mean of both, normalised so the base-lot-weighted average weight is 1; snapped to the grid)
| cell | weights (KB, PE, SM, HM, MV, PB) |
|--|--|
| RP-HOLD | KB=0.97;PE=0.31;SM=1.17;HM=1.83;MV=0.82;PB=2.25 |
| RP-PRE | KB=1.49;PE=0.49;SM=0.76;HM=0.96;MV=0.97;PB=4.78 |
| RP-HOLDPRE | KB=1.26;PE=0.41;SM=1.00;HM=1.37;MV=0.95;PB=3.26 |
| RPsnap-HOLD | KB=1.00;PE=0.50;SM=1.25;HM=1.50;MV=0.75;PB=1.50 |
| RPsnap-PRE | KB=1.50;PE=0.50;SM=0.75;HM=1.00;MV=1.00;PB=1.50 |
| RPsnap-HOLDPRE | KB=1.25;PE=0.50;SM=1.00;HM=1.25;MV=1.00;PB=1.50 |

| cell | HOLD mean | HOLD maxDD | HOLD Calmar | HOLD worst | PRE mean | PRE maxDD | PRE Calmar | PRE worst | L6M mean | L6M maxDD | L6M Calmar | L6M worst |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| RP-HOLD | 24553 | 48557 | 0.51 | -48557 | 10758 | 85058 | 0.13 | -49393 | 31920 | 48557 | 0.66 | -48557 |
| RP-PRE | 23716 | 90155 | 0.26 | -65861 | 13497 | 61915 | 0.22 | -52036 | 31193 | 65861 | 0.47 | -65861 |
| RP-HOLDPRE | 23766 | 61769 | 0.38 | -53473 | 12268 | 65519 | 0.19 | -51583 | 32836 | 53473 | 0.61 | -53473 |
| RPsnap-HOLD | 27101 | 81865 | 0.33 | -55602 | 12716 | 72346 | 0.18 | -54066 | 37576 | 55602 | 0.68 | -55602 |
| RPsnap-PRE | 24412 | 86994 | 0.28 | -53823 | 12576 | 76501 | 0.16 | -58241 | 36559 | 53823 | 0.68 | -53823 |
| RPsnap-HOLDPRE | 25563 | 80309 | 0.32 | -54285 | 12710 | 73042 | 0.17 | -52951 | 36138 | 54285 | 0.67 | -54285 |

| cell | X' mean | X' maxDD | X' Calmar | X' worst | MID mean | MID maxDD | MID Calmar | MID worst | ALL mean | ALL maxDD | ALL Calmar | ALL worst |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| RP-HOLD | 3177 | 41891 | 0.08 | -21233 | 15435 | 30058 | 0.51 | -17712 | 10290 | 100660 | 0.10 | -55500 |
| RP-PRE | 3712 | 46943 | 0.08 | -20908 | 13003 | 40974 | 0.32 | -27366 | 10934 | 115267 | 0.09 | -65861 |
| RP-HOLDPRE | 2904 | 39387 | 0.07 | -21303 | 12727 | 31248 | 0.41 | -17372 | 10454 | 108827 | 0.10 | -56974 |
| RPsnap-HOLD | 2673 | 44414 | 0.06 | -24058 | 15825 | 43597 | 0.36 | -25716 | 11777 | 93033 | 0.13 | -55602 |
| RPsnap-PRE | 2519 | 37191 | 0.07 | -21996 | 11500 | 39428 | 0.29 | -22497 | 10695 | 118986 | 0.09 | -58241 |
| RPsnap-HOLDPRE | 2482 | 42854 | 0.06 | -23319 | 13607 | 42838 | 0.32 | -23113 | 11119 | 94599 | 0.12 | -54285 |

By year:

| cell | 2023 mean | 2023 maxDD | 2024 mean | 2024 maxDD | 2025 mean | 2025 maxDD | 2026 mean | 2026 maxDD |
|--|--|--|--|--|--|--|--|--|
| RP-HOLD | 901 | 68012 | 11857 | 62053 | 8741 | 89441 | 18593 | 100660 |
| RP-PRE | 895 | 92684 | 14325 | 61915 | 10400 | 115267 | 16455 | 99174 |
| RP-HOLDPRE | 921 | 76897 | 12921 | 65519 | 9353 | 95971 | 17290 | 108827 |
| RPsnap-HOLD | 1307 | 66954 | 13164 | 72346 | 10578 | 69285 | 20834 | 93033 |
| RPsnap-PRE | 923 | 74465 | 13192 | 76501 | 9538 | 78259 | 17772 | 118986 |
| RPsnap-HOLDPRE | 895 | 84354 | 13145 | 73042 | 9889 | 78764 | 19240 | 94599 |

## 4. Single-book sensitivity (KB, MV, SM, PB; HOLD / PRE / L6M)
| cell | HOLD mean | HOLD maxDD | HOLD Calmar | HOLD worst | PRE mean | PRE maxDD | PRE Calmar | PRE worst | L6M mean | L6M maxDD | L6M Calmar | L6M worst |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| KB=0 | 25985 | 116128 | 0.22 | -58792 | 13923 | 70519 | 0.20 | -60351 | 38765 | 58792 | 0.66 | -58792 |
| KB=0.5 | 27755 | 128513 | 0.22 | -67008 | 15719 | 76673 | 0.21 | -59246 | 43066 | 62566 | 0.69 | -62566 |
| KB=0.75 | 29078 | 122025 | 0.24 | -62576 | 16118 | 75057 | 0.21 | -61712 | 45311 | 62576 | 0.72 | -62576 |
| KB=1.25 | 29607 | 122605 | 0.24 | -66819 | 16284 | 81949 | 0.20 | -65399 | 46245 | 66819 | 0.69 | -66819 |
| KB=1.5 | 31001 | 121661 | 0.25 | -70401 | 16919 | 87439 | 0.19 | -75319 | 48938 | 70401 | 0.70 | -70401 |
| MV=0 | 29038 | 108666 | 0.27 | -61920 | 15654 | 71668 | 0.22 | -61544 | 45401 | 61920 | 0.73 | -61920 |
| MV=0.5 | 28951 | 121360 | 0.24 | -61334 | 16288 | 71665 | 0.23 | -59786 | 45055 | 61334 | 0.73 | -61334 |
| MV=0.75 | 29078 | 122025 | 0.24 | -62576 | 16118 | 75057 | 0.21 | -61712 | 45311 | 62576 | 0.72 | -62576 |
| MV=1.25 | 29102 | 119906 | 0.24 | -66445 | 16060 | 77198 | 0.21 | -63639 | 45397 | 64435 | 0.70 | -64435 |
| MV=1.5 | 28741 | 114652 | 0.25 | -66728 | 16412 | 85395 | 0.19 | -61914 | 43462 | 59534 | 0.73 | -59534 |
| SM=0 | 26462 | 122217 | 0.22 | -64170 | 14998 | 79434 | 0.19 | -58609 | 43190 | 50953 | 0.85 | -50953 |
| SM=0.5 | 27823 | 121823 | 0.23 | -63246 | 15521 | 77147 | 0.20 | -60488 | 44255 | 56764 | 0.78 | -56764 |
| SM=0.75 | 28569 | 124760 | 0.23 | -63355 | 15917 | 75750 | 0.21 | -59996 | 44927 | 59758 | 0.75 | -59758 |
| SM=1.25 | 29907 | 125576 | 0.24 | -65569 | 16424 | 74164 | 0.22 | -61875 | 46026 | 65569 | 0.70 | -65569 |
| SM=1.5 | 30372 | 122840 | 0.25 | -68387 | 16670 | 74227 | 0.22 | -63591 | 46376 | 68387 | 0.68 | -68387 |
| PB=0 | 28235 | 116845 | 0.24 | -56474 | 15212 | 80608 | 0.19 | -57842 | 44761 | 56347 | 0.79 | -56347 |
| PB=0.5 | 29078 | 122025 | 0.24 | -62576 | 16118 | 75057 | 0.21 | -61712 | 45311 | 62576 | 0.72 | -62576 |
| PB=0.75 | 29078 | 122025 | 0.24 | -62576 | 16118 | 75057 | 0.21 | -61712 | 45311 | 62576 | 0.72 | -62576 |
| PB=1.25 | 29143 | 119402 | 0.24 | -63829 | 16098 | 75057 | 0.21 | -61712 | 45400 | 63829 | 0.71 | -63829 |
| PB=1.5 | 29792 | 124287 | 0.24 | -69576 | 16764 | 72940 | 0.23 | -64220 | 45550 | 69576 | 0.65 | -69576 |

## 5. Selection caution: rolling origin (choose on years before t, evaluate year t; carry weeks dropped; objective on weekly vectors of the cells above)
| year | rule | weights | prior_calmar | live_prior_calmar | eval_mean | live_mean | eval_maxdd | live_maxdd | eval_calmar | live_calmar |
|--|--|--|--|--|--|--|--|--|--|--|
| 2024 | max Calmar | PE=0.50;HM=0.00 | 0.05 | 0.02 | 9721.02 | 14431.41 | 43230.32 | 75056.65 | 0.22 | 0.19 |
| 2024 | min maxDD s.t. mean>=90% live | PE=0.50;HM=0.00 | 0.05 | 0.02 | 9721.02 | 14431.41 | 43230.32 | 75056.65 | 0.22 | 0.19 |
| 2025 | max Calmar | PE=0.50;HM=0.00 | 0.15 | 0.11 | 8827.45 | 16523.94 | 48490.31 | 71413.82 | 0.18 | 0.23 |
| 2025 | min maxDD s.t. mean>=90% live | PE=1.00;HM=0.00 | 0.12 | 0.11 | 14512.85 | 16523.94 | 55613.71 | 71413.82 | 0.26 | 0.23 |
| 2026 | max Calmar | SM=1.50 | 0.17 | 0.14 | 32004.97 | 30497.52 | 122840.31 | 122024.73 | 0.26 | 0.25 |
| 2026 | min maxDD s.t. mean>=90% live | PE=1.00;HM=0.50 | 0.16 | 0.14 | 27541.66 | 30497.52 | 125253.11 | 122024.73 | 0.22 | 0.25 |

## 6. Paired block-bootstrap vs live, MDE, PA9 (best cells by HOLD Calmar, plus the grid's headline cells)
Bootstrap = moving blocks of 4 weeks, 2,000 draws, paired on the same weeks; p = share of draws with no improvement (Calmar) or no reduction (maxDD); BH q over all 61 cells using the worse of the HOLD and PRE Calmar p; MDE = 2.8 x SE of the paired weekly difference in HOLD. PA9 = genuine nine lock-reset phases, maxDD cut % vs the base (positive = shallower).
| cell | weights | MDE HOLD ($/wk) | p dCalmar HOLD | p dCalmar PRE | p dmaxDD HOLD | BH q | PA9 maxDD cut % | label |
|--|--|--|--|--|--|--|--|--|
| RP-HOLD | KB=0.97;PE=0.31;SM=1.17;HM=1.83;MV=0.82;PB=2.25 | 8133 | 0.091 | 0.855 | 0.042 | 1.00 | L6M +4.0 / HOLD +17.5 / PRE -1.4 / X' +15.8 pass2 False | REGIME (HOLD-only gain) |
| PE=0,HM=1.5 | PE=0.00;HM=1.50 | 11329 | 0.109 | 0.918 | 0.010 | 1.00 |  | REGIME (HOLD-only gain) |
| PE=0,HM=1.25 | PE=0.00;HM=1.25 | 11568 | 0.119 | 0.847 | 0.010 | 1.00 |  | REGIME (HOLD-only gain) |
| PE=0 | PE=0.00 | 11960 | 0.153 | 0.846 | 0.009 | 1.00 |  | REGIME (HOLD-only gain) |
| PE=0,HM=0.75 | PE=0.00;HM=0.75 | 12212 | 0.189 | 0.809 | 0.018 | 1.00 |  | REGIME (HOLD-only gain) |
| RP-HOLDPRE | KB=1.26;PE=0.41;SM=1.00;HM=1.37;MV=0.95;PB=3.26 | 6656 | 0.176 | 0.751 | 0.074 | 1.00 | L6M -3.8 / HOLD +10.8 / PRE -8.8 / X' +4.8 pass2 False | REGIME (HOLD-only gain) |
| PE=0.5,HM=1.5 | PE=0.50;HM=1.50 | 5042 | 0.061 | 0.855 | 0.058 | 1.00 | L6M +15.7 / HOLD +27.6 / PRE +13.8 / X' +16.5 pass2 False | REGIME (HOLD-only gain) |
| RPsnap-HOLD | KB=1.00;PE=0.50;SM=1.25;HM=1.50;MV=0.75;PB=1.50 | 5233 | 0.089 | 0.788 | 0.052 | 1.00 | L6M +11.2 / HOLD +23.8 / PRE +18.0 / X' +17.1 pass2 False | REGIME (HOLD-only gain) |
| PE=0.5 | PE=0.50 | 5467 | 0.081 | 0.736 | 0.050 | 1.00 |  | REGIME (HOLD-only gain) |
| PE=0.75 | PE=0.75 | 3932 | 0.152 | 0.741 | 0.057 | 1.00 |  | WEAK (in-sample Calmar gain, q>0.2) |

Distribution of labels over the 61 cells: {'DEAD': 30, 'REGIME (HOLD-only gain)': 22, 'WEAK (in-sample Calmar gain, q>0.2)': 9}.

## 7. What it says
1. **Trading PE less cuts the drawdown by roughly what it costs in mean; it is a risk-budget dial, not a free gain.** PE x0.75: maxDD HOLD -19%, PRE -13%, L6M -26%, X' -19%, worst week -62.6k -> -51.5k; mean HOLD -13%, PRE -21%, L6M -14%. PE x0.5: maxDD HOLD -33%, PRE -18%, L6M -33%, X' -30%, worst week -45.1k; mean HOLD -23%, PRE -30%, L6M -27%. Calmar rises in HOLD (0.24 -> 0.26 / 0.27) and L6M (0.72 -> 0.83 / 0.80) and is flat to lower in PRE (0.21 -> 0.20 / 0.18). PE x1.25-1.5 raises the mean by 10-22% and the maxDD by 19-43% (HOLD), Calmar down. By year the PE x0.5 effect is a smaller 2026 and 2025 maxDD but also a smaller mean in every year (table above).
2. **PE x0 with locks re-run is a different number from the DIS-AF subtraction** (HOLD Calmar 0.41 in both because PE's lots vanish, but PRE Calmar 0.09 and L6M 0.53): removing PE removes most of the mean (HOLD 29.1k -> 13.6k) for a maxDD of 32.9k. HM x1.25-1.5 on top of PE x0.5 recovers some mean (HOLD Calmar 0.32-0.34, PRE 0.15-0.18); PE x0.5 with HM x1.25 has a genuine PA9 maxDD cut of L6M +21 / HOLD +32 / PRE +18 / X' +16% (pass2), the best-behaved cell in drawdown terms, but its mean is -16% HOLD, -26% PRE, -22% L6M.
3. **Risk-parity weights fit the window they are fitted on.** RP-HOLD (inverse own HOLD maxDD) has HOLD Calmar 0.51 (maxDD 48.6k) but PRE 0.13 and a smaller mean; RP-PRE does the opposite (PRE 0.22, HOLD 0.26, L6M 0.47); the combined RP-HOLDPRE is 0.38 / 0.19 / 0.61. The snapped versions sit in between. None improves HOLD, PRE and L6M together.
4. **Small books do not matter at integer lots.** KB, MV, SM, PB moves change Calmar by at most 0.03 in either direction with no consistent sign (PB is 1 lot, so 0.5-0.75 are no-ops; KB 0.75 is a no-op); these are noise-level effects of lock interaction and rounding.
5. **Selection caution holds.** No cell has BH q below 1.0 (smallest raw p 0.27 on the worse of HOLD and PRE), because PRE Calmar rarely improves; HOLD-only p for PE x0.5 is 0.08 (maxDD p 0.05), in sample. Rolling origin: weights chosen on prior years do not hold up: 2024 chooses PE 0.5 / HM 0 (mean -33%, maxDD -42%, Calmar 0.22 vs 0.19), 2025 chooses the same cell by Calmar and gets mean -47% and Calmar 0.18 vs live 0.23 (the drawdown-constrained rule picks PE 1 / HM 0: Calmar 0.26 vs 0.23, mean -12%), 2026 picks SM 1.5 (Calmar 0.26 vs 0.25) or PE 1 / HM 0.5 (0.22 vs 0.25). The only year with a clean win is 2024 for a rule built on 2023, the year PE and the stack were weakest.
6. **Labels.** 0 LEAD-IN-SAMPLE, 22 REGIME (Calmar gain in HOLD that does not carry to PRE/L6M), 9 WEAK (in-sample Calmar gain, q > 0.2), 30 DEAD. PE x0.75 (WEAK: HOLD +0.02, PRE -0.01, L6M +0.11 Calmar, drawdown -19% HOLD) is the mildest dial and the one that does not give up PRE. Drawdown conclusion: concentration in PE can be turned down at a mean cost of about the same proportion; nothing here shows a weighting that improves drawdown without giving up mean outside the sample it was picked on. This is a decision for the user (risk appetite), not a research finding.
