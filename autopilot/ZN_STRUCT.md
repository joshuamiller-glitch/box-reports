# ZN_STRUCT - T-ZONES-EXHAUST families C (swing/market structure), D (MA/bands), E (round numbers/grid)
Updated 2026-11-10 14:06Z. PRE-PROOF, post-hoc, Shadow only, FIRST-ORDER SCREEN ONLY unless the exact table below says otherwise. **ROLL-EXCL applied** (33 roll-artifact base trades weighted 0 via sz_core Base.rollw; every number rescored incl. X-prime and HOLD). No PASS claims.

**Price source:** ZN-CORE roll-continuous 1-min bars from the 1-s state arrays (/mnt/l2/l2vast/_th_zn/bars.npz, cont = raw - cum, 14 quarterly rolls); all levels on the continuous axis, distances to the last closed 1-min close at the signal second; round numbers / open-grid use the live price (cont + cum/4). bars1m_NQ.npz (back-adjusted) is NOT used. Entry proxy vs trade-list entry_px: median 0.8 pt, 99th pct 25 pts (fills/slippage and roll seconds).

**Base/method.** S1b-COMB (live D7 v1.5 state-cut lines, Q1-A, HALF D20 + OTE-62 inside the base lots), actions applied after, rounded lots (min 1). Cells = level type x variant (mode any/matched kind, touches 0/<=1/any, age 1h/4h/1d/5d) x geometry (D 5-90 pts and 0.25-1.5 ATR(5m,14), half-width 0/2/5/10, polarity ahead-present / ahead-absent / behind-present / behind-absent, count in target path >=1/>=2) x action (skip, half, quarter; up-size 1.5 labelled UP) x scope (stack, 7 books, 6 sessions, 42 book x session). Screen: 2882299 (mask, action, scope) rows kept of ~9,263,348 evaluated (identical masks deduplicated); candidates = lead screen (cut L6M, PRE, X' > 0 and equal-mean cut L6M > 0) with sanity gate touched <= 40% of trades and equal-mean factor 0.3-2.5 (drops "skip nearly everything" cells), top 2308 by min equal-mean cut per family plus the best per type x scope kind. maxDD/worst-20/Ulcer on all weeks, carry week dropped from means only; equal-mean = one global scalar so L6M mean equals Q1-A.

**Family-wise honesty.** p fam = 1-(1-q)^N with q the pooled per-hypothesis tail of the placebo z, N = 9,263,348 hypotheses evaluated (cells independent = conservative); it is ~1.00 for every cell, so NO cell is a CANDIDATE on the family test; "CANDIDATE (own-p only)" = clears placebo p <= .10 on L6M and PRE and WF but not the family max. Own-draw p (random same-count within book x session, B=100) is shown beside it. The "FAILS-LIVE-WEEK" tag uses the frozen live week (11-01..11-05, a +$104.8k week; any skip is mechanically penalised there).

**Walk-forward of the picking procedure (purged monthly, lowest trailing-26-week maxDD among each family top-150, embargo 7 d):** STRUCT_C: WF maxDD cut vs Q1-A 50%, picks [('67596bdc05b1', 6), ('3e95aed41b9b', 4)]; STRUCT_D: WF maxDD cut vs Q1-A 54%, picks [('b80e8ad9f0f9', 8), ('7d7839e89700', 5)]; STRUCT_E: WF maxDD cut vs Q1-A 55%, picks [('f1e306fae8ba', 8), ('73ab13c3846f', 7)]. (WF on pooled stack; picks are unstable across months if the top pick count is small.)

## C Swing / market structure
Plain sentence: best by min equal-mean cut over L6M/PRE/X': **sw15_3 v7 hw0 pt90 BA, skip on PE** cuts maxDD 56%/54%/60% (L6M/PRE/X') at equal lots and 57%/56%/61% at equal mean; own placebo p 0.01/0.07, family p 1.00; CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF. 236 of the 838 scored cells in this family are CANDIDATE (own-p only) and 3 of them also survive the live week.

### C Swing / market structure top 15 (rank: candidates first, then min equal-mean cut)
| level | geometry | action | scope | maxDD cut L6M/HOLD/PRE/X' (all wks) | equal-mean cut L6M/PRE/X' | w20 cut L6M | d mean $/wk L6M | touched % | placebo p L6M/PRE | shuffled-days p | shifted +-25 beats | p fam (all hyp) | live wk d$ | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sw15_3 | v7 hw0 pt90 BA | skip | PE | 56/58/54/60 | 57/56/61 | 52 | 725 | 14.7 | 0.01/0.07 | 0.02 | no | 1.00 | -65500 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| sw1_5 | v18 hw0 atr1.5 AP | skip | PE | 65/-33/61/58 | 59/54/52 | 25 | -2878 | 20.9 | 0.01/0.07 | 0.07 | no | 1.00 | -93030 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| sw1_2 | v18 hw5 pt20 BA | skip | PE | 55/17/44/53 | 61/51/60 | 57 | 3821 | 10.4 | 0.01/0.08 | 0.10 | no | 1.00 | -67320 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| fvg15 | v20 hw5 pt20 BA | skip | PE | 63/37/63/68 | 50/51/57 | 13 | -6995 | 19.1 | 0.01/0.03 | 0.05 | no | 1.00 | -81065 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| sw5_3 | v7 hw5 pt40 BA | skip | PE | 66/28/56/53 | 63/52/49 | 48 | -1712 | 16.1 | 0.01/0.08 | 0.07 | no | 1.00 | -83110 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| sw15_3 | v6 hw0 pt90 BA | quarter | PE | 48/48/47/52 | 50/49/54 | 45 | 976 | 14.0 | 0.03/0.04 | 0.02 | no | 1.00 | -49137 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| ob5 | v10 hw10 atr0.25 AA | quarter | stack | 54/42/54/65 | 49/49/61 | 21 | -2282 | 26.7 | 0.01/0.03 | 0.02 | no | 1.00 | -35482 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| ob15 | v10 hw0 pt60 AA | quarter | stack | 64/49/60/59 | 55/49/49 | -6 | -4470 | 27.4 | 0.01/0.01 | 0.02 | no | 1.00 | -39058 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| sw15_3 | v7 hw0 pt90 BA | quarter | stack | 51/49/52/54 | 48/50/52 | 6 | -1132 | 21.3 | 0.01/0.01 | 0.02 | no | 1.00 | -45887 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| sw5_3 | v7 hw5 pt40 BA | quarter | PE | 50/29/52/52 | 48/50/50 | 38 | -911 | 14.6 | 0.01/0.01 | 0.02 | no | 1.00 | -58427 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| sw5_5 | v7 hw0 pt60 BA | quarter | PE | 51/45/50/51 | 48/47/48 | 36 | -1247 | 14.8 | 0.03/0.02 | 0.05 | no | 1.00 | -53437 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| sw1_3 | v4 hw0 atr1.5 AP | quarter | stack | 54/21/58/70 | 47/51/65 | 28 | -2828 | 28.3 | 0.01/0.03 | 0.05 | no | 1.00 | -64134 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| brk5 | v22 hw0 pt10 AA | quarter | stack | 64/55/62/72 | 50/47/60 | 2 | -6203 | 33.1 | 0.01/0.01 |  | no | 1.00 | -59449 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| sw5_3 | v7 hw10 pt40 BA | quarter | stack | 51/25/50/49 | 48/48/47 | 31 | -1015 | 20.8 | 0.01/0.03 |  | no | 1.00 | -59323 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| sw5_5 | v6 hw0 pt60 BA | skip | PE | 63/56/54/53 | 58/48/46 | 34 | -2629 | 16.7 | 0.02/0.07 |  | no | 1.00 | -74105 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |

### C Swing / market structure up-size (UP, report only, never promoted)
| level | geometry | action | scope | maxDD cut L6M/HOLD/PRE/X' (all wks) | equal-mean cut L6M/PRE/X' | w20 cut L6M | d mean $/wk L6M | touched % | placebo p L6M/PRE | shuffled-days p | shifted +-25 beats | p fam (all hyp) | live wk d$ | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| bos5 | v4 hw5 pt40 BP | up15 | stack | 24/-17/-6/-26 | 33/7/-10 | 34 | 3636 | 15.9 | 0.01/0.32 |  | no | 1.00 | -1665 | UP (report, never promoted) |
| bos5 | v4 hw2 pt40 BP | up15 | stack | 21/-17/-7/-24 | 31/6/-9 | 35 | 3605 | 15.4 | 0.01/0.32 |  | no | 1.00 | -980 | UP (report, never promoted) |
| bos5 | v16 hw5 pt40 BP | up15 | stack | 18/-16/-5/-24 | 28/8/-8 | 38 | 3791 | 15.3 | 0.01/0.26 |  | no | 1.00 | -1080 | UP (report, never promoted) |
| brk5 | v10 hw2 pt5 BP | up15 | stack | 17/-34/-22/24 | 40/12/45 | 91 | 8713 | 27.9 | 0.01/0.40 |  | no | 1.00 | 20682 | UP (report, never promoted) |
| bos5 | v4 hw10 pt40 BP | up15 | stack | 17/-15/-8/-25 | 26/4/-11 | 30 | 3320 | 16.9 | 0.01/0.48 |  | no | 1.00 | -1685 | UP (report, never promoted) |

### C Swing / market structure where the zone action HURTS (cut < 0 on L6M, PRE and X' together, >= 40 trades; most negative L6M)
| level | scope | # cells hurt | worst cut L6M | worst cut PRE | min d mean $/wk |
|---|---|---|---|---|---|
| sw15_5 | asia | 1753 | -183 | -49 | -20122 |
| bos5 | asia | 743 | -159 | -48 | -21868 |
| mitob5 | asia | 1849 | -154 | -38 | -18720 |
| sw60_3 | stack | 1387 | -151 | -35 | -15961 |
| brk15 | asia | 819 | -150 | -33 | -17616 |
| sw60_2 | asia | 2742 | -147 | -44 | -15186 |
| fvg15 | asia | 2314 | -147 | -53 | -23818 |
| sw5_3 | asia | 2577 | -145 | -66 | -20995 |

## D Moving-average / band levels
Plain sentence: best by min equal-mean cut over L6M/PRE/X': **k7any v0 hw5 pt20 BA, skip on PE** cuts maxDD 50%/47%/47% (L6M/PRE/X') at equal lots and 49%/46%/46% at equal mean; own placebo p 0.01/0.03, family p 1.00; CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF. 112 of the 819 scored cells in this family are CANDIDATE (own-p only) and 6 of them also survive the live week.

### D Moving-average / band levels top 15 (rank: candidates first, then min equal-mean cut)
| level | geometry | action | scope | maxDD cut L6M/HOLD/PRE/X' (all wks) | equal-mean cut L6M/PRE/X' | w20 cut L6M | d mean $/wk L6M | touched % | placebo p L6M/PRE | shuffled-days p | shifted +-25 beats | p fam (all hyp) | live wk d$ | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| k7any | v0 hw5 pt20 BA | skip | PE | 50/33/47/47 | 49/46/46 | 10 | -117 | 9.6 | 0.01/0.03 | 0.05 | no | 1.00 | -41425 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| stany | v0 hw5 pt20 BA | skip | PE | 57/33/39/40 | 60/44/44 | 32 | 1802 | 10.3 | 0.01/0.10 | 0.10 | no | 1.00 | -50875 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| k7any | v0 hw0 pt20 BA | quarter | stack | 57/9/46/51 | 54/42/48 | 9 | -1358 | 16.5 | 0.01/0.03 | 0.02 | no | 1.00 | -48740 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| stany | v0 hw0 pt20 BA | quarter | stack | 57/13/44/58 | 55/41/56 | 3 | -1150 | 17.0 | 0.01/0.03 | 0.05 | no | 1.00 | -55226 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| k7st_1 | v0 hw0 pt20 BA | quarter | stack | 53/17/44/49 | 49/40/46 | 12 | -1423 | 19.1 | 0.01/0.07 | 0.05 | no | 1.00 | -51671 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| stany | v0 hw0 pt20 BA | quarter | PE | 45/23/39/43 | 46/40/44 | 24 | 616 | 12.0 | 0.03/0.08 | 0.05 | no | 1.00 | -47219 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| k7any | v0 hw0 pt20 BA | quarter | PE | 54/18/39/40 | 55/40/41 | 33 | 534 | 11.3 | 0.01/0.06 | 0.05 | no | 1.00 | -40733 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| bbup_5 | v0 hw0 pt15 AA | quarter | london | 36/-7/44/41 | 38/46/43 | 3 | 728 | 11.5 | 0.01/0.06 | 0.05 | no | 1.00 | 3225 | CANDIDATE (own-p only; family p 1.00) [PRE-PROOF] |
| kc2.5lo_5 | v0 hw5 pt90 BA | half | stack | 44/25/44/44 | 38/38/38 | 29 | -2419 | 23.8 | 0.01/0.01 | 0.02 | no | 1.00 | -34903 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| kc2.5lo_5 | v0 hw10 pt60 BA | quarter | london | 37/-20/44/33 | 42/48/38 | 13 | 1702 | 10.4 | 0.01/0.02 | 0.02 | no | 1.00 | 3873 | CANDIDATE (own-p only; family p 1.00) [PRE-PROOF] |
| kc1.5lo_15 | v0 hw5 pt90 BA | skip | PE | 44/-37/51/49 | 37/45/43 | 13 | -2326 | 13.4 | 0.03/0.04 |  | no | 1.00 | -58660 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| bbmid_5 | v0 hw10 pt40 BA | quarter | PE | 35/28/31/45 | 40/37/50 | 59 | 2033 | 9.4 | 0.01/0.06 |  | no | 1.00 | -36427 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| bbup_15 | v0 hw5 pt30 AA | half | stack | 46/36/47/51 | 37/38/43 | 10 | -3440 | 32.0 | 0.02/0.02 |  | no | 1.00 | -32501 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| bbup_5 | v0 hw0 pt15 AA | quarter | PE | 48/44/46/58 | 39/36/51 | 8 | -3605 | 18.1 | 0.03/0.05 |  | no | 1.00 | -58908 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| emaany_60 | v0 hw5 pt40 BA | skip | london | 47/-55/57/44 | 38/50/35 | -11 | -3969 | 22.5 | 0.04/0.06 |  | no | 1.00 | -12205 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |

### D Moving-average / band levels up-size (UP, report only, never promoted)
| level | geometry | action | scope | maxDD cut L6M/HOLD/PRE/X' (all wks) | equal-mean cut L6M/PRE/X' | w20 cut L6M | d mean $/wk L6M | touched % | placebo p L6M/PRE | shuffled-days p | shifted +-25 beats | p fam (all hyp) | live wk d$ | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| bbmid_15 | v0 hw0 pt30 BP | up15 | stack | 22/-3/-10/42 | 25/-6/45 | 29 | 976 | 23.0 | 0.01/0.19 |  | no | 1.00 | 19019 | UP (report, never promoted) |
| kc2.5lo_15 | v0 hw10 pt90 BP | up15 | stack | 19/-4/-5/0 | 34/14/18 | 31 | 4965 | 24.5 | 0.01/0.13 |  | no | 1.00 | 2434 | UP (report, never promoted) |
| ema50_5 | v0 hw0 pt30 BP | up15 | stack | 18/-7/-7/36 | 26/4/43 | 44 | 2614 | 28.7 | 0.01/0.14 |  | no | 1.00 | 15528 | UP (report, never promoted) |
| bbmid_15 | v0 hw2 pt30 BP | up15 | stack | 18/-6/-10/42 | 23/-4/45 | 29 | 1360 | 24.9 | 0.01/0.17 |  | no | 1.00 | 19295 | UP (report, never promoted) |
| ema50_5 | v0 hw2 pt30 BP | up15 | stack | 16/-8/-7/41 | 27/6/48 | 50 | 3285 | 30.9 | 0.01/0.14 |  | no | 1.00 | 14503 | UP (report, never promoted) |

### D Moving-average / band levels where the zone action HURTS (cut < 0 on L6M, PRE and X' together, >= 40 trades; most negative L6M)
| level | scope | # cells hurt | worst cut L6M | worst cut PRE | min d mean $/wk |
|---|---|---|---|---|---|
| bbany_5 | asia | 59 | -131 | -27 | -18462 |
| stany | asia | 76 | -127 | -19 | -18384 |
| k7any | asia | 109 | -123 | -18 | -18805 |
| bbup_15 | stack | 16 | -123 | -11 | -9951 |
| bblo_15 | stack | 6 | -105 | -58 | -10664 |
| kc2.5up_5 | asia | 179 | -101 | -25 | -19718 |
| ema20_15 | asia | 37 | -99 | -13 | -20760 |
| bbmid_5 | asia | 175 | -97 | -37 | -21626 |

## E Round numbers / grid
Plain sentence: best by min equal-mean cut over L6M/PRE/X': **grid0.5 v0 hw2 pt10 AA, quarter on london** cuts maxDD 33%/46%/30% (L6M/PRE/X') at equal lots and 29%/43%/26% at equal mean; own placebo p 0.07/0.09, family p 1.00; CANDIDATE (own-p only; family p 1.00) PRE-PROOF. 26 of the 606 scored cells in this family are CANDIDATE (own-p only) and 5 of them also survive the live week.

### E Round numbers / grid top 15 (rank: candidates first, then min equal-mean cut)
| level | geometry | action | scope | maxDD cut L6M/HOLD/PRE/X' (all wks) | equal-mean cut L6M/PRE/X' | w20 cut L6M | d mean $/wk L6M | touched % | placebo p L6M/PRE | shuffled-days p | shifted +-25 beats | p fam (all hyp) | live wk d$ | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| grid0.5 | v0 hw2 pt10 AA | quarter | london | 33/-23/46/30 | 29/43/26 | 19 | -1481 | 13.4 | 0.07/0.09 |  | no | 1.00 | -2539 | CANDIDATE (own-p only; family p 1.00) [PRE-PROOF] |
| grid1 | v0 hw10 atr1 AA | quarter | london | 32/-5/45/21 | 36/48/26 | 18 | 1335 | 13.0 | 0.08/0.10 |  | no | 1.00 | -3532 | CANDIDATE (own-p only; family p 1.00) [PRE-PROOF] |
| grid1 | v0 hw5 pt40 AA | half | stack | 42/38/47/57 | 24/31/44 | -13 | -4909 | 31.7 | 0.03/0.04 |  | no | 1.00 | -35506 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| rn50 | v0 hw0 atr0.5 AA | quarter | london | 35/-4/48/17 | 41/52/24 | 25 | 2175 | 12.0 | 0.01/0.02 |  | no | 1.00 | 2954 | CANDIDATE (own-p only; family p 1.00) [PRE-PROOF] |
| grid1 | v0 hw0 pt30 AA | half | london | 29/6/36/23 | 28/35/22 | 19 | -251 | 13.0 | 0.01/0.09 |  | yes | 1.00 | -725 | CANDIDATE (own-p only; family p 1.00) [PRE-PROOF] |
| grid0.5 | v0 hw0 atr1 AA | half | london | 31/-3/34/20 | 31/34/21 | 29 | 281 | 12.4 | 0.01/0.10 |  | yes | 1.00 | -3614 | CANDIDATE (own-p only; family p 1.00) [PRE-PROOF] |
| rn50 | v0 hw10 atr0.5 BP | skip | london | 33/0/48/10 | 39/53/19 | 14 | 2502 | 13.4 | 0.02/0.04 |  | no | 1.00 | -12260 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| grid1 | v0 hw0 pt30 AA | quarter | stack | 47/38/55/70 | 15/27/52 | -28 | -8049 | 33.6 | 0.02/0.09 |  | yes | 1.00 | -53906 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| rn50 | v0 hw5 atr1 BP | skip | PE | 55/45/51/26 | 44/40/9 | 9 | -4317 | 14.3 | 0.02/0.06 |  | no | 1.00 | -44170 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| grid2 | v0 hw5 pt40 AA | quarter | stack | 48/42/57/64 | 7/22/35 | -35 | -9434 | 33.7 | 0.07/0.05 |  | no | 1.00 | -57346 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| rn50 | v0 hw5 atr1 AP | quarter | stack | 38/30/44/21 | 21/29/-0 | -17 | -4705 | 20.6 | 0.09/0.06 |  | yes | 1.00 | -45239 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK [PRE-PROOF] |
| rn25 | v0 hw10 atr0.5 AP | quarter | stack | 61/57/62/61 | 43/44/42 | -13 | -6711 | 30.9 | 0.01/0.02 | 0.02 | yes | 1.00 | -61140 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was CANDIDATE] |
| grid0.5 | v0 hw5 pt30 AA | skip | london | 42/-31/46/34 | 48/51/40 | 57 | 2885 | 22.0 | 0.06/0.53 | 0.59 | yes | 1.00 | -12530 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| rn25 | v0 hw2 atr1 AP | half | stack | 48/41/47/49 | 38/37/40 | 10 | -3474 | 30.0 | 0.01/0.02 | 0.02 | yes | 1.00 | -38382 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was CANDIDATE] |
| rn25 | v0 hw5 atr0.5 AP | quarter | PE | 46/30/42/47 | 41/37/42 | 10 | -1900 | 15.2 | 0.01/0.12 | 0.05 | yes | 1.00 | -49864 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |

### E Round numbers / grid up-size (UP, report only, never promoted)
| level | geometry | action | scope | maxDD cut L6M/HOLD/PRE/X' (all wks) | equal-mean cut L6M/PRE/X' | w20 cut L6M | d mean $/wk L6M | touched % | placebo p L6M/PRE | shuffled-days p | shifted +-25 beats | p fam (all hyp) | live wk d$ | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| grid1 | v0 hw2 pt10 BP | up15 | stack | 6/-4/-12/-12 | 11/-5/-5 | 15 | 1347 | 8.7 | 0.07/0.87 |  | no | 1.00 | 13815 | UP (report, never promoted) |
| grid1 | v0 hw5 atr0.25 BP | up15 | stack | 5/-7/-10/-6 | 14/1/5 | 25 | 2378 | 7.1 | 0.05/0.80 |  | no | 1.00 | 14415 | UP (report, never promoted) |
| grid1 | v0 hw0 atr0.5 BP | up15 | stack | 4/-8/-15/-6 | 15/-2/5 | 29 | 2899 | 7.0 | 0.06/0.96 |  | no | 1.00 | 14883 | UP (report, never promoted) |
| grid1 | v0 hw2 pt5 BP | up15 | stack | 4/4/-7/-3 | 11/1/4 | 18 | 1723 | 5.1 | 0.03/0.78 |  | no | 1.00 | 7200 | UP (report, never promoted) |
| grid1 | v0 hw2 atr0.25 BP | up15 | stack | 4/-2/-11/-9 | 12/-1/1 | 25 | 2095 | 4.9 | 0.08/0.91 |  | no | 1.00 | 11415 | UP (report, never promoted) |

### E Round numbers / grid where the zone action HURTS (cut < 0 on L6M, PRE and X' together, >= 40 trades; most negative L6M)
| level | scope | # cells hurt | worst cut L6M | worst cut PRE | min d mean $/wk |
|---|---|---|---|---|---|
| rn100 | asia | 49 | -78 | -15 | -14547 |
| rn50 | asia | 60 | -67 | -20 | -17433 |
| grid0.5 | asia | 120 | -57 | -22 | -19945 |
| grid1 | asia | 84 | -55 | -25 | -20376 |
| grid0.5 | PE|asia | 83 | -53 | -12 | -13097 |
| rn25 | PE|asia | 60 | -52 | -22 | -13313 |
| rn50 | PE|asia | 41 | -50 | -12 | -8770 |
| grid2 | asia | 35 | -47 | -14 | -21655 |

## Level-specificity test (is it the LEVEL or just de-risking the scope?)
For every scored cell: (a) group-wide baseline = the same action applied to EVERY trade of the scope (gain = cell min equal-mean cut minus group-wide min equal-mean cut, must exceed 5 pts), (b) shifted-level placebo: all levels moved +-25 pts (entry shifted, same geometry), cell must beat both shifted versions on min equal-mean cut, (c) random same-count placebo p <= .10 (L6M and PRE), (d) shuffled-days p <= .15 (top 40 per family). Cells failing are relabelled SCOPE-EFFECT (gain <= 5) or NOT-LEVEL-SPECIFIC (shifted levels do as well) and are NOT candidates.

| family | cells scored | level-specific | SCOPE-EFFECT | NOT-LEVEL-SPECIFIC | level-specific CANDIDATE (own-p only) | ... that also pass the live week |
|---|---|---|---|---|---|---|
| C | 838 | 268 | 11 | 559 | 236 | 37 |
| D | 819 | 165 | 2 | 650 | 112 | 14 |
| E | 606 | 35 | 13 | 557 | 26 | 13 |

Typical generic cells (SCOPE-EFFECT / shifted-equal), most frequent scopes: asia 549, london 348, PE 290, PE|asia 240, ALL 221, SM 34.

## Best SETTING of the zone layer per book x session (standing rule: the layer stays ON; live HALF D20 + OTE-62 B73 D30 stays unless a level-specific cell beats it; first-order; all rows ADDITIONS on top of the live layer)
| scope | best level-specific cell | action | maxDD cut L6M/PRE/X' | equal-mean min cut | gain vs group-wide | d mean $/wk L6M | placebo p | live wk d$ | verdict |
|---|---|---|---|---|---|---|---|---|---|
| PE|london | pd1h_38 v0 hw0 atr1 BP | skip | 26/29/23 | 28 | 26 | 1948 | 0.09 | -3425 | ADD candidate (first-order; exact queued only for the family top-5) |
| PE|asia | k7any v0 hw2 pt30 BA | skip | 15/19/16 | 20 | 228 | 1293 | 0.05 | -28735 | ADD candidate (first-order; exact queued only for the family top-5) |
| SM|asia | rn100 v0 hw5 pt40 BP | skip | 2/7/14 | 1 | 34 | -425 | 0.06 | -2405 | lead only: live layer stays |

For every book x session not listed, no level-specific cell cleared the screen: the live layer stays unchanged there.

## EXACT engine results for the queued ZS_* sets (exact vs first-order maxDD cut; windows present only when all their months have landed)
| set | cell | level / geometry / action / scope | window | exact cut | first-order cut | exact equal-mean cut | exact d mean $/wk | stage |
|---|---|---|---|---|---|---|---|---|
| ZS_C0 | 6e93e2da912d |  | L1M | 14.9 | 44.5 | 23.4 | 3962 | [EXACT] |
| ZS_C0 | 6e93e2da912d |  | L2M | 14.9 | 44.5 | 23.4 | -1967 | [EXACT] |
| ZS_C0 | 6e93e2da912d |  | L3M | 15.0 | 44.6 | 23.4 | -1936 | [EXACT] |
| ZS_C0 | 6e93e2da912d |  | L6M | 15.0 | 44.6 | 23.4 | 2344 | [EXACT] |
| ZS_C0 | 6e93e2da912d |  | PRE | 17.1 | 54.8 | 25.4 | -949 | [EXACT] |
| ZS_C0 | 6e93e2da912d |  | X' | 44.5 | 33.9 | 50.1 | 1643 | [EXACT] |
| ZS_D0 | b0c41cc34961 | bbup_5 v0 hw0 pt15 AA quarter london | L1M | 29.2 | 40.1 | 26.7 | -5069 | [EXACT] |
| ZS_D0 | b0c41cc34961 | bbup_5 v0 hw0 pt15 AA quarter london | L2M | 29.2 | 40.1 | 26.7 | -4717 | [EXACT] |
| ZS_D0 | b0c41cc34961 | bbup_5 v0 hw0 pt15 AA quarter london | L3M | 20.3 | 39.9 | 17.5 | 2955 | [EXACT] |
| ZS_D0 | b0c41cc34961 | bbup_5 v0 hw0 pt15 AA quarter london | L6M | 20.3 | 36.4 | 17.5 | -838 | [EXACT] |
| ZS_D0 | b0c41cc34961 | bbup_5 v0 hw0 pt15 AA quarter london | PRE | 38.7 | 44.2 | 36.5 | -898 | [EXACT] |
| ZS_D0 | b0c41cc34961 | bbup_5 v0 hw0 pt15 AA quarter london | X' | 33.4 | 41.0 | 31.0 | 2635 | [EXACT] |

## Top-5 per family for exact (level-specific, p_own <= .10; QUEUED with SZ-CORE as sets ZS_C0-4 / ZS_D0-4 / ZS_E0-4: L6M months for all 15, PRE, X-prime and HOLD for the top-2 per family; M table /mnt/l2/l2vast/_th_zn/M_ZN_STRUCT.npz; registry file /mnt/l2/l2vast/_th_zn/topK_STRUCT.json
- C Swing / market structure: e2b9736063c7 (sw15_3 v7 hw0 pt90 BA skip PE), b6032b93a83c (sw1_5 v18 hw0 atr1.5 AP skip PE), afc2cc12b466 (sw1_2 v18 hw5 pt20 BA skip PE), 2aa652b6eec4 (fvg15 v20 hw5 pt20 BA skip PE), 9584448d018a (sw5_3 v7 hw5 pt40 BA skip PE)
- D Moving-average / band levels: 5fe923a731af (k7any v0 hw5 pt20 BA skip PE), 80eb3e013ac2 (stany v0 hw5 pt20 BA skip PE), ad30a7e5008c (k7any v0 hw0 pt20 BA quarter ALL), 1f468f7eae60 (stany v0 hw0 pt20 BA quarter ALL), a3da423704c7 (k7st_1 v0 hw0 pt20 BA quarter ALL)
- E Round numbers / grid: 42047584662f (grid0.5 v0 hw2 pt10 AA quarter london), a0ae92ccf4f0 (grid1 v0 hw10 atr1 AA quarter london), 1fd1cee89b7d (grid1 v0 hw5 pt40 AA half ALL), 24b410a63e69 (rn50 v0 hw0 atr0.5 AA quarter london), a44faa83748b (grid1 v0 hw0 pt30 AA half london)

Caveats: levels are 1-min-bar approximations of the NT8 chart series (flip levels use 1-min extremes instead of 1-s bins; 60-min bars bucket on UTC hours); K7/U7 Supertrend/Keltner book lines, HMA-VWAP and weekly/monthly option strikes (not owned) are not yet in the set; re-target / delay-until-through / structure-stop / 70-30 actions are not static tables and wait for the exact engine (top-5 only); confluence and strength filters are only tested after selection.
