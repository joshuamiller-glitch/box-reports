# ZN_STRUCT - T-ZONES-EXHAUST families C (swing/market structure), D (MA/bands), E (round numbers/grid)
Updated 2026-11-09 17:23Z. PRE-PROOF, post-hoc, Shadow only, FIRST-ORDER SCREEN ONLY (no exact engine run yet; exact top-5 per family queued below). No PASS claims.

**Price source:** ZN-CORE roll-continuous 1-min bars from the 1-s state arrays (/mnt/l2/l2vast/_th_zn/bars.npz, cont = raw - cum, 14 quarterly rolls); all levels on the continuous axis, distances to the last closed 1-min close at the signal second; round numbers / open-grid use the live price (cont + cum/4). bars1m_NQ.npz (back-adjusted) is NOT used. Entry proxy vs trade-list entry_px: median 0.8 pt, 99th pct 25 pts (fills/slippage and roll seconds).

**Base/method.** S1b-COMB (live D7 v1.5 state-cut lines, Q1-A, HALF D20 + OTE-62 inside the base lots), actions applied after, rounded lots (min 1). Cells = level type x variant (mode any/matched kind, touches 0/<=1/any, age 1h/4h/1d/5d) x geometry (D 5-90 pts and 0.25-1.5 ATR(5m,14), half-width 0/2/5/10, polarity ahead-present / ahead-absent / behind-present / behind-absent, count in target path >=1/>=2) x action (skip, half, quarter; up-size 1.5 labelled UP) x scope (stack, 7 books, 6 sessions, 42 book x session). Screen: 2905103 (mask, action, scope) rows kept of ~9,263,348 evaluated (identical masks deduplicated); candidates = lead screen (cut L6M, PRE, X' > 0 and equal-mean cut L6M > 0) with sanity gate touched <= 40% of trades and equal-mean factor 0.3-2.5 (drops "skip nearly everything" cells), top 2320 by min equal-mean cut per family plus the best per type x scope kind. maxDD/worst-20/Ulcer on all weeks, carry week dropped from means only; equal-mean = one global scalar so L6M mean equals Q1-A.

**Family-wise honesty.** p fam = 1-(1-q)^N with q the pooled per-hypothesis tail of the placebo z, N = 9,263,348 hypotheses evaluated (cells independent = conservative); it is ~1.00 for every cell, so NO cell is a CANDIDATE on the family test; "CANDIDATE (own-p only)" = clears placebo p <= .10 on L6M and PRE and WF but not the family max. Own-draw p (random same-count within book x session, B=100) is shown beside it. The "FAILS-LIVE-WEEK" tag uses the frozen live week (11-01..11-05, a +$104.8k week; any skip is mechanically penalised there).

**Walk-forward of the picking procedure (purged monthly, lowest trailing-26-week maxDD among each family top-150, embargo 7 d):** STRUCT_C: WF maxDD cut vs Q1-A 28%, picks [('67596bdc05b1', 5), ('3e95aed41b9b', 4)]; STRUCT_D: WF maxDD cut vs Q1-A 42%, picks [('1a3783ccae10', 7), ('63025853f94f', 5)]; STRUCT_E: WF maxDD cut vs Q1-A 51%, picks [('73ab13c3846f', 7), ('c4b95dfe2764', 5)]. (WF on pooled stack; picks are unstable across months if the top pick count is small.)

## C Swing / market structure
Plain sentence: best by min equal-mean cut over L6M/PRE/X': **fvg15 v20 hw5 pt20 BA, skip on PE** cuts maxDD 63%/63%/65% (L6M/PRE/X') at equal lots and 59%/59%/61% at equal mean; own placebo p 0.01/0.03, family p 1.00; CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF. 235 of the 836 scored cells in this family are CANDIDATE (own-p only) and 4 of them also survive the live week.

### C Swing / market structure top 15 (rank: candidates first, then min equal-mean cut)
| level | geometry | action | scope | maxDD cut L6M/HOLD/PRE/X' (all wks) | equal-mean cut L6M/PRE/X' | w20 cut L6M | d mean $/wk L6M | touched % | placebo p L6M/PRE | shuffled-days p | shifted +-25 beats | p fam (all hyp) | live wk d$ | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| fvg15 | v20 hw5 pt20 BA | skip | PE | 63/33/63/65 | 59/59/61 | -13 | -2224 | 19.1 | 0.01/0.03 | 0.05 | no | 1.00 | -81065 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| sw15_3 | v7 hw0 pt90 BA | skip | PE | 56/43/54/56 | 57/56/58 | -52 | 725 | 14.7 | 0.01/0.07 | 0.02 | no | 1.00 | -65500 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| sw1_2 | v18 hw5 pt20 BA | skip | PE | 55/17/44/48 | 61/51/55 | -59 | 3821 | 10.4 | 0.01/0.08 | 0.10 | no | 1.00 | -67320 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| sw1_5 | v18 hw0 atr1.5 AP | skip | PE | 65/-37/61/57 | 59/54/50 | -21 | -2974 | 20.9 | 0.01/0.07 | 0.07 | no | 1.00 | -93030 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| sw15_3 | v6 hw0 pt90 BA | quarter | PE | 48/33/47/53 | 50/49/55 | -45 | 976 | 14.0 | 0.03/0.04 | 0.02 | no | 1.00 | -49137 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| sw15_3 | v7 hw0 pt90 BA | quarter | stack | 51/37/52/54 | 48/50/51 | -6 | -1132 | 21.3 | 0.01/0.01 | 0.02 | no | 1.00 | -45887 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| ob15 | v11 hw0 pt5 BA | quarter | stack | 52/24/51/67 | 49/48/64 | -9 | -1362 | 24.8 | 0.01/0.03 | 0.05 | no | 1.00 | -35397 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| ob5 | v10 hw5 pt20 AA | quarter | stack | 54/27/52/54 | 50/48/50 | -16 | -1951 | 24.9 | 0.01/0.01 | 0.05 | no | 1.00 | -35482 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| sw1_3 | v16 hw0 atr1.5 AP | quarter | stack | 54/14/55/67 | 48/49/63 | -30 | -2454 | 28.2 | 0.02/0.06 | 0.10 | no | 1.00 | -64134 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| sw5_5 | v6 hw10 pt40 BA | quarter | PE | 55/30/53/56 | 50/47/52 | -38 | -2272 | 16.9 | 0.01/0.02 | 0.02 | no | 1.00 | -55165 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| brk5 | v10 hw5 atr0.25 AA | quarter | stack | 56/37/53/69 | 51/47/66 | -32 | -2147 | 29.3 | 0.01/0.06 | 0.05 | no | 1.00 | -48122 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| sw1_3 | v16 hw0 atr1.5 AP | quarter | PE | 54/23/50/64 | 51/46/61 | -34 | -1563 | 19.7 | 0.01/0.06 | 0.10 | no | 1.00 | -63969 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| sw5_3 | v7 hw5 pt40 BA | quarter | PE | 50/18/52/48 | 48/50/46 | -38 | -911 | 14.6 | 0.01/0.01 |  | no | 1.00 | -58427 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| sw5_3 | v6 hw0 pt60 BA | quarter | stack | 54/23/46/45 | 54/46/44 | -33 | -273 | 18.5 | 0.02/0.03 |  | no | 1.00 | -56394 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| sw15_2 | v7 hw10 pt90 BA | skip | PE | 60/25/41/40 | 63/45/44 | -68 | 1692 | 11.0 | 0.01/0.10 |  | no | 1.00 | -57295 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |

### C Swing / market structure up-size (UP, report only, never promoted)
| level | geometry | action | scope | maxDD cut L6M/HOLD/PRE/X' (all wks) | equal-mean cut L6M/PRE/X' | w20 cut L6M | d mean $/wk L6M | touched % | placebo p L6M/PRE | shuffled-days p | shifted +-25 beats | p fam (all hyp) | live wk d$ | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| bos5 | v4 hw5 pt40 BP | up15 | stack | 24/-17/-6/-28 | 33/7/-13 | -34 | 3636 | 15.9 | 0.01/0.32 |  | no | 1.00 | -1665 | UP (report, never promoted) |
| bos5 | v4 hw2 pt40 BP | up15 | stack | 21/-17/-7/-27 | 31/6/-11 | -35 | 3605 | 15.4 | 0.01/0.32 |  | no | 1.00 | -980 | UP (report, never promoted) |
| bos5 | v16 hw5 pt40 BP | up15 | stack | 18/-16/-5/-26 | 28/8/-10 | -38 | 3791 | 15.3 | 0.01/0.26 |  | no | 1.00 | -1080 | UP (report, never promoted) |
| brk5 | v10 hw2 pt5 BP | up15 | stack | 17/-34/-22/27 | 40/12/47 | -91 | 8713 | 27.9 | 0.01/0.40 |  | no | 1.00 | 20682 | UP (report, never promoted) |
| bos5 | v4 hw10 pt40 BP | up15 | stack | 17/-15/-8/-28 | 26/4/-14 | -30 | 3320 | 16.9 | 0.01/0.48 |  | no | 1.00 | -1685 | UP (report, never promoted) |

### C Swing / market structure where the zone action HURTS (cut < 0 on L6M, PRE and X' together, >= 40 trades; most negative L6M)
| level | scope | # cells hurt | worst cut L6M | worst cut PRE | min d mean $/wk |
|---|---|---|---|---|---|
| sw15_5 | asia | 1961 | -202 | -49 | -20999 |
| bos5 | asia | 927 | -159 | -64 | -21914 |
| sw5_3 | stack | 335 | -156 | -76 | -17875 |
| mitob5 | asia | 2080 | -154 | -35 | -20978 |
| sw60_3 | stack | 1411 | -151 | -32 | -16059 |
| fvg15 | asia | 2630 | -150 | -53 | -24010 |
| brk15 | asia | 852 | -150 | -33 | -20543 |
| bos15 | asia | 1307 | -148 | -25 | -22546 |

## D Moving-average / band levels
Plain sentence: best by min equal-mean cut over L6M/PRE/X': **k7any v0 hw5 pt20 BA, skip on PE** cuts maxDD 50%/47%/46% (L6M/PRE/X') at equal lots and 49%/46%/46% at equal mean; own placebo p 0.01/0.03, family p 1.00; CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF. 104 of the 820 scored cells in this family are CANDIDATE (own-p only) and 11 of them also survive the live week.

### D Moving-average / band levels top 15 (rank: candidates first, then min equal-mean cut)
| level | geometry | action | scope | maxDD cut L6M/HOLD/PRE/X' (all wks) | equal-mean cut L6M/PRE/X' | w20 cut L6M | d mean $/wk L6M | touched % | placebo p L6M/PRE | shuffled-days p | shifted +-25 beats | p fam (all hyp) | live wk d$ | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| k7any | v0 hw5 pt20 BA | skip | PE | 50/33/47/46 | 49/46/46 | -10 | -117 | 9.6 | 0.01/0.03 | 0.05 | no | 1.00 | -41425 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| k7any | v0 hw0 pt20 BA | quarter | stack | 57/9/46/46 | 54/42/43 | -9 | -1358 | 16.5 | 0.01/0.03 | 0.02 | no | 1.00 | -48740 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| stany | v0 hw0 pt20 BA | quarter | stack | 57/13/44/55 | 55/41/53 | -3 | -1150 | 17.0 | 0.01/0.03 | 0.05 | no | 1.00 | -55226 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| k7st_1 | v0 hw0 pt20 BA | quarter | stack | 53/17/44/53 | 49/41/50 | -12 | -1423 | 19.1 | 0.01/0.07 | 0.05 | no | 1.00 | -51671 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| stany | v0 hw0 pt20 BA | quarter | PE | 45/23/39/44 | 46/40/45 | -24 | 616 | 12.0 | 0.03/0.09 | 0.05 | no | 1.00 | -47219 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| k7any | v0 hw0 pt20 BA | quarter | PE | 54/18/39/44 | 55/40/45 | -33 | 534 | 11.3 | 0.01/0.06 | 0.05 | no | 1.00 | -40733 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| stany | v0 hw5 pt20 BA | skip | PE | 57/33/39/34 | 60/44/38 | -32 | 1802 | 10.3 | 0.01/0.10 | 0.07 | no | 1.00 | -50875 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| bbup_5 | v0 hw0 pt15 AA | quarter | london | 36/-28/44/46 | 38/46/47 | -3 | 728 | 11.5 | 0.01/0.06 | 0.05 | no | 1.00 | 3225 | CANDIDATE (own-p only; family p 1.00) [PRE-PROOF] |
| bbmid_5 | v0 hw10 pt40 BA | quarter | PE | 35/28/31/40 | 40/37/45 | -59 | 2033 | 9.4 | 0.01/0.06 |  | no | 1.00 | -36427 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| kc1.5lo_15 | v0 hw5 pt90 BA | skip | PE | 44/-41/51/44 | 37/45/37 | -13 | -2326 | 13.4 | 0.03/0.04 |  | no | 1.00 | -58660 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| bbup_15 | v0 hw5 pt30 AA | half | stack | 46/36/47/47 | 37/38/38 | -10 | -3440 | 32.0 | 0.02/0.02 |  | no | 1.00 | -32501 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| kc2.5up_5 | v0 hw0 pt15 AA | quarter | london | 35/-34/42/37 | 36/43/38 | -6 | 444 | 11.3 | 0.01/0.10 |  | no | 1.00 | 1997 | CANDIDATE (own-p only; family p 1.00) [PRE-PROOF] |
| bbup_5 | v0 hw0 pt15 AA | quarter | PE | 48/36/46/55 | 39/36/47 | -8 | -3605 | 18.1 | 0.03/0.05 |  | no | 1.00 | -58908 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| bbmid_5 | v0 hw2 pt30 BA | quarter | london | 32/-21/35/31 | 35/38/35 | -7 | 1369 | 8.4 | 0.01/0.10 |  | no | 1.00 | 1648 | CANDIDATE (own-p only; family p 1.00) [PRE-PROOF] |
| dsmaany | v0 hw0 pt90 AA | quarter | london | 33/-31/48/34 | 35/49/35 | -22 | 657 | 13.7 | 0.03/0.05 |  | yes | 1.00 | 3873 | CANDIDATE (own-p only; family p 1.00) [PRE-PROOF] |

### D Moving-average / band levels up-size (UP, report only, never promoted)
| level | geometry | action | scope | maxDD cut L6M/HOLD/PRE/X' (all wks) | equal-mean cut L6M/PRE/X' | w20 cut L6M | d mean $/wk L6M | touched % | placebo p L6M/PRE | shuffled-days p | shifted +-25 beats | p fam (all hyp) | live wk d$ | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| bbmid_15 | v0 hw0 pt30 BP | up15 | stack | 22/-3/-10/36 | 25/-6/39 | -29 | 1072 | 23.0 | 0.01/0.19 |  | no | 1.00 | 19019 | UP (report, never promoted) |
| kc2.5lo_15 | v0 hw10 pt90 BP | up15 | stack | 19/-25/-5/-0 | 34/14/18 | -31 | 5157 | 24.5 | 0.01/0.13 |  | no | 1.00 | 2434 | UP (report, never promoted) |
| ema50_5 | v0 hw0 pt30 BP | up15 | stack | 18/-7/-7/30 | 26/3/36 | -44 | 2467 | 28.7 | 0.01/0.14 |  | no | 1.00 | 15528 | UP (report, never promoted) |
| bbmid_15 | v0 hw2 pt30 BP | up15 | stack | 18/-6/-10/36 | 23/-3/40 | -29 | 1393 | 24.9 | 0.01/0.17 |  | no | 1.00 | 19295 | UP (report, never promoted) |
| ema50_5 | v0 hw2 pt30 BP | up15 | stack | 16/-8/-7/35 | 26/5/43 | -50 | 3139 | 30.9 | 0.01/0.13 |  | no | 1.00 | 14503 | UP (report, never promoted) |

### D Moving-average / band levels where the zone action HURTS (cut < 0 on L6M, PRE and X' together, >= 40 trades; most negative L6M)
| level | scope | # cells hurt | worst cut L6M | worst cut PRE | min d mean $/wk |
|---|---|---|---|---|---|
| bblo_5 | asia | 22 | -145 | -19 | -15633 |
| bbany_5 | asia | 68 | -131 | -27 | -18752 |
| k7any | asia | 128 | -128 | -36 | -20792 |
| stany | asia | 81 | -127 | -19 | -18334 |
| bbup_15 | stack | 21 | -123 | -16 | -9951 |
| emaany_15 | asia | 60 | -111 | -18 | -20938 |
| bblo_15 | stack | 9 | -105 | -55 | -11490 |
| bbup_15 | asia | 55 | -104 | -20 | -18913 |

## E Round numbers / grid
Plain sentence: best by min equal-mean cut over L6M/PRE/X': **grid0.5 v0 hw2 pt5 BA, quarter on london** cuts maxDD 36%/48%/34% (L6M/PRE/X') at equal lots and 31%/44%/29% at equal mean; own placebo p 0.03/0.06, family p 1.00; CANDIDATE (own-p only; family p 1.00) PRE-PROOF. 27 of the 619 scored cells in this family are CANDIDATE (own-p only) and 5 of them also survive the live week.

### E Round numbers / grid top 15 (rank: candidates first, then min equal-mean cut)
| level | geometry | action | scope | maxDD cut L6M/HOLD/PRE/X' (all wks) | equal-mean cut L6M/PRE/X' | w20 cut L6M | d mean $/wk L6M | touched % | placebo p L6M/PRE | shuffled-days p | shifted +-25 beats | p fam (all hyp) | live wk d$ | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| grid0.5 | v0 hw2 pt5 BA | quarter | london | 36/-41/48/34 | 31/44/29 | 1 | -2009 | 14.1 | 0.03/0.06 | 0.02 | no | 1.00 | 3873 | CANDIDATE (own-p only; family p 1.00) [PRE-PROOF] |
| grid1 | v0 hw10 atr1 AA | quarter | london | 32/-26/45/24 | 36/48/28 | -18 | 1335 | 13.0 | 0.08/0.10 |  | no | 1.00 | -3532 | CANDIDATE (own-p only; family p 1.00) [PRE-PROOF] |
| rn50 | v0 hw0 atr0.5 AA | quarter | london | 35/-25/48/19 | 41/52/26 | -25 | 2175 | 12.0 | 0.01/0.02 |  | no | 1.00 | 2954 | CANDIDATE (own-p only; family p 1.00) [PRE-PROOF] |
| grid1 | v0 hw5 pt40 AA | half | stack | 42/25/47/57 | 24/31/44 | 13 | -4909 | 31.7 | 0.03/0.04 |  | no | 1.00 | -35506 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| grid1 | v0 hw0 pt30 AA | half | london | 29/-15/36/25 | 28/35/24 | -19 | -251 | 13.0 | 0.01/0.09 |  | yes | 1.00 | -725 | CANDIDATE (own-p only; family p 1.00) [PRE-PROOF] |
| grid0.5 | v0 hw0 atr1 AA | half | london | 31/-24/34/22 | 31/34/23 | -29 | 281 | 12.4 | 0.01/0.10 |  | yes | 1.00 | -3614 | CANDIDATE (own-p only; family p 1.00) [PRE-PROOF] |
| rn50 | v0 hw10 atr0.5 BP | skip | london | 33/-21/48/11 | 39/53/20 | -14 | 2502 | 13.4 | 0.02/0.04 |  | no | 1.00 | -12260 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| grid1 | v0 hw0 pt30 AA | quarter | stack | 47/30/55/67 | 16/28/47 | 28 | -8049 | 33.6 | 0.02/0.10 |  | yes | 1.00 | -53906 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| grid2 | v0 hw5 pt40 AA | quarter | stack | 48/34/57/60 | 7/22/28 | 35 | -9434 | 33.7 | 0.07/0.05 |  | no | 1.00 | -57346 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| rn50 | v0 hw5 atr1 BP | skip | PE | 55/41/51/21 | 44/40/3 | -9 | -4317 | 14.3 | 0.02/0.07 |  | no | 1.00 | -44170 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| rn50 | v0 hw5 atr1 AP | quarter | stack | 38/31/44/23 | 20/29/2 | 17 | -4849 | 20.6 | 0.09/0.06 |  | yes | 1.00 | -45239 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| grid0.5 | v0 hw0 pt30 AA | skip | london | 40/-58/38/40 | 45/43/44 | -59 | 2289 | 23.4 | 0.07/0.91 | 0.93 | yes | 1.00 | -6010 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| rn25 | v0 hw2 atr1 AP | half | stack | 48/29/47/50 | 38/37/40 | -10 | -3474 | 30.0 | 0.01/0.02 | 0.02 | yes | 1.00 | -38382 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was CANDIDATE] |
| rn25 | v0 hw5 atr0.5 AP | quarter | PE | 46/9/42/52 | 41/37/48 | -10 | -1900 | 15.2 | 0.01/0.12 | 0.05 | yes | 1.00 | -49864 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| rn25 | v0 hw10 atr0.5 AP | quarter | stack | 61/37/62/57 | 43/44/37 | 13 | -6711 | 30.9 | 0.01/0.02 | 0.02 | yes | 1.00 | -61140 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was CANDIDATE] |

### E Round numbers / grid up-size (UP, report only, never promoted)
| level | geometry | action | scope | maxDD cut L6M/HOLD/PRE/X' (all wks) | equal-mean cut L6M/PRE/X' | w20 cut L6M | d mean $/wk L6M | touched % | placebo p L6M/PRE | shuffled-days p | shifted +-25 beats | p fam (all hyp) | live wk d$ | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| grid1 | v0 hw2 pt10 BP | up15 | stack | 6/-15/-12/-6 | 11/-5/1 | -15 | 1347 | 8.7 | 0.07/0.87 |  | no | 1.00 | 13815 | UP (report, never promoted) |
| grid1 | v0 hw5 atr0.25 BP | up15 | stack | 5/-9/-10/-1 | 15/2/10 | -25 | 3016 | 7.1 | 0.05/0.80 |  | no | 1.00 | 14415 | UP (report, never promoted) |
| grid1 | v0 hw0 atr0.5 BP | up15 | stack | 4/-8/-15/-3 | 14/-3/7 | -29 | 2657 | 7.0 | 0.06/0.96 |  | no | 1.00 | 14883 | UP (report, never promoted) |
| grid1 | v0 hw2 pt5 BP | up15 | stack | 4/-3/-7/1 | 10/-0/8 | -18 | 1620 | 5.1 | 0.03/0.78 |  | no | 1.00 | 7200 | UP (report, never promoted) |
| grid1 | v0 hw2 atr0.25 BP | up15 | stack | 4/-4/-11/-5 | 11/-2/3 | -25 | 1965 | 4.9 | 0.08/0.91 |  | no | 1.00 | 11415 | UP (report, never promoted) |

### E Round numbers / grid where the zone action HURTS (cut < 0 on L6M, PRE and X' together, >= 40 trades; most negative L6M)
| level | scope | # cells hurt | worst cut L6M | worst cut PRE | min d mean $/wk |
|---|---|---|---|---|---|
| rn100 | asia | 51 | -78 | -15 | -14741 |
| rn50 | asia | 67 | -73 | -20 | -18006 |
| rn25 | PE|asia | 79 | -58 | -22 | -13409 |
| grid0.5 | asia | 124 | -57 | -22 | -20043 |
| rn50 | PE|asia | 49 | -55 | -14 | -10856 |
| grid1 | asia | 79 | -55 | -25 | -20571 |
| grid0.5 | PE|asia | 90 | -53 | -13 | -13208 |
| grid2 | asia | 40 | -47 | -14 | -21946 |

## Level-specificity test (is it the LEVEL or just de-risking the scope?)
For every scored cell: (a) group-wide baseline = the same action applied to EVERY trade of the scope (gain = cell min equal-mean cut minus group-wide min equal-mean cut, must exceed 5 pts), (b) shifted-level placebo: all levels moved +-25 pts (entry shifted, same geometry), cell must beat both shifted versions on min equal-mean cut, (c) random same-count placebo p <= .10 (L6M and PRE), (d) shuffled-days p <= .15 (top 40 per family). Cells failing are relabelled SCOPE-EFFECT (gain <= 5) or NOT-LEVEL-SPECIFIC (shifted levels do as well) and are NOT candidates.

| family | cells scored | level-specific | SCOPE-EFFECT | NOT-LEVEL-SPECIFIC | level-specific CANDIDATE (own-p only) | ... that also pass the live week |
|---|---|---|---|---|---|---|
| C | 836 | 270 | 11 | 555 | 235 | 40 |
| D | 820 | 164 | 2 | 652 | 104 | 18 |
| E | 619 | 37 | 34 | 548 | 27 | 16 |

Typical generic cells (SCOPE-EFFECT / shifted-equal), most frequent scopes: asia 560, london 379, PE 281, PE|asia 223, ALL 211, MV 38.

## Best SETTING of the zone layer per book x session (standing rule: the layer stays ON; live HALF D20 + OTE-62 B73 D30 stays unless a level-specific cell beats it; first-order; all rows ADDITIONS on top of the live layer)
| scope | best level-specific cell | action | maxDD cut L6M/PRE/X' | equal-mean min cut | gain vs group-wide | d mean $/wk L6M | placebo p | live wk d$ | verdict |
|---|---|---|---|---|---|---|---|---|---|
| PE|london | pd1h_38 v0 hw0 atr1 BP | skip | 26/29/25 | 30 | 27 | 1948 | 0.09 | -3425 | ADD candidate (first-order; exact queued only for the family top-5) |
| PE|asia | k7any v0 hw2 pt30 BA | skip | 15/19/18 | 20 | 236 | 1293 | 0.05 | -28735 | ADD candidate (first-order; exact queued only for the family top-5) |
| MV|london | ema20_15 v0 hw2 pt20 BA | skip | 14/16/12 | 14 | 40 | 686 | 0.07 | -2190 | ADD candidate (first-order; exact queued only for the family top-5) |
| SM|asia | rn100 v0 hw2 pt40 BP | skip | 2/7/11 | 1 | 34 | -425 | 0.05 | -2405 | lead only: live layer stays |

For every book x session not listed, no level-specific cell cleared the screen: the live layer stays unchanged there.

## Top-5 per family for exact (level-specific, p_own <= .10; QUEUED with SZ-CORE as sets ZS_C0-4 / ZS_D0-4 / ZS_E0-4: L6M months for all 15, PRE, X-prime and HOLD for the top-2 per family; M table /mnt/l2/l2vast/_th_zn/M_ZN_STRUCT.npz; registry file /mnt/l2/l2vast/_th_zn/topK_STRUCT.json
- C Swing / market structure: 2aa652b6eec4 (fvg15 v20 hw5 pt20 BA skip PE), e2b9736063c7 (sw15_3 v7 hw0 pt90 BA skip PE), afc2cc12b466 (sw1_2 v18 hw5 pt20 BA skip PE), b6032b93a83c (sw1_5 v18 hw0 atr1.5 AP skip PE), 3b2da7cb961f (sw15_3 v6 hw0 pt90 BA quarter PE)
- D Moving-average / band levels: 5fe923a731af (k7any v0 hw5 pt20 BA skip PE), ad30a7e5008c (k7any v0 hw0 pt20 BA quarter ALL), 1f468f7eae60 (stany v0 hw0 pt20 BA quarter ALL), a3da423704c7 (k7st_1 v0 hw0 pt20 BA quarter ALL), 8ca05ddebfbd (stany v0 hw0 pt20 BA quarter PE)
- E Round numbers / grid: d87874dba5c6 (grid0.5 v0 hw2 pt5 BA quarter london), a0ae92ccf4f0 (grid1 v0 hw10 atr1 AA quarter london), 24b410a63e69 (rn50 v0 hw0 atr0.5 AA quarter london), 1fd1cee89b7d (grid1 v0 hw5 pt40 AA half ALL), a44faa83748b (grid1 v0 hw0 pt30 AA half london)

Caveats: levels are 1-min-bar approximations of the NT8 chart series (flip levels use 1-min extremes instead of 1-s bins; 60-min bars bucket on UTC hours); K7/U7 Supertrend/Keltner book lines, HMA-VWAP and weekly/monthly option strikes (not owned) are not yet in the set; re-target / delay-until-through / structure-stop / 70-30 actions are not static tables and wait for the exact engine (top-5 only); confluence and strength filters are only tested after selection.
