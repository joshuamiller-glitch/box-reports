# DS3_ZONES_EXHAUST - T-ZONES-EXHAUST (2026-11-09 18:12Z)

STATUS: ROLL-EXCL (33 roll-artifact trades excluded, sz_core.Base rollw), PRE-PROOF, post-hoc, Shadow only, no PASS claims. FIRST-ORDER SCREEN ONLY unless the stage column says EXACT (exact engine rows are queued with SZ-CORE; none labelled EXACT here yet). Base S1b-COMB (live D7 v1.5 state cut, Q1-A, HALF D20 + OTE-62 B73 D30 in the base), carry week dropped from means only, maxDD/worst-20/Ulcer on all weeks, windows as of 2026-11-09, trade lists end 2026-10-30. Zone sources: 1-s state arrays (levels causal at the signal bar; volume = traded prints), see ZN_API.md. Held-out live week = frozen live file only; the 92 live cuts and the v1.5 night cuts are NOT used.

Grid screened: 347553 unique cells (family-level + per-level-type), 235159 with a placebo null (down-sizing), family max-stat over all of them; screen passers (L6M and PRE cut > 0, >= 20 trades changed): 53321.

## Reference rows (first-order, stack)

| ref | mean $/wk L6M | maxDD L6M | maxDD PRE | maxDD X' | maxDD HOLD | worst-20 L6M | note |
|---|---|---|---|---|---|---|---|
| REF_LIVE | 22948 | 79907 | 140288 | 128944 | 99496 | 165224 | live layer (HALF D20 + OTE-62 B73 D30 as in the exact base) |
| REF_NOZONE_FO | 28121 | 91798 | 144258 | 136616 | 112018 | 167377 | live zone halves undone at chain_nz lots (first-order; labelled UP; exact no-zone row queued) |
| REF_S4A | published S4A layer | | | | | | see DS3_TH_S4_ZONES_S1B.md; exact rows from SZ-CORE queue |

## Family A - Prior structure (prior-day/week/month H/L/C, overnight/Asia/London/pre-market, IB 30/60 + extensions, opening ranges, yesterday VWAP, settlement, gaps)

A: the best equal-mean cell is a **skip** when the A ahead 60 pts hw10 fresh=t0 age<=5d (level set ALL) is within reach, scope london: stack maxDD cut 54/55/-25 % (L6M/PRE/X') at equal lots and 58/58/-16 % at equal mean, touching 23.9% of trades; label **LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY]**. It does not hold as a setting because X' maxDD gets worse by 25%; the random same-count placebo reaches it (p 0.12); the purged walk-forward of the picking procedure does not beat the live layer; the family max-stat over the whole zone set (p 1.00) is not cleared; levels shifted by +/-25 pts do as well (p_shift 0.33), so the cut is not level-specific. The live HALF D20 + OTE-62 B73 D30 layer stays ON.

Ranked by min(equal-mean cut L6M, PRE) among screen passers; top 15 (full grid in /mnt/l2/l2vast/_th_zn/grid_all.parquet).

| level | geometry | action | scope (book|session) | maxDD cut % L6M/HOLD/PRE/X' | maxDD $ cell|ref L6M/PRE | equal-mean cut % L6M/PRE/X' | worst-20 L6M cell|ref | d mean $/wk L6M | trades touched % | placebo p L6M/PRE (B400) | shift/day placebo p | own p | family p (max) | WF ok | live-week d$ | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | ahead 60 pts hw10 fresh=t0 age<=5d | skip | london | 54/-51/55/-25 | 36359|79907/62667|140288 | 58/58/-16 | 252216|165224 | 1770 | 23.9 | 0.00/0.12 | 0.33/0.02 | 0.11/1.00 | False | 585 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 60 pts hw2 fresh=t0 age<=5d | skip | london | 56/-56/54/-26 | 35161|79907/64391|140288 | 59/58/-16 | 267396|165224 | 1877 | 23.2 | 0.00/0.13 | 0.33/0.02 | 0.10/1.00 | False | 585 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 60 pts hw10 fresh=t0 age<=1d | skip | london | 54/-51/55/-37 | 36359|79907/62667|140288 | 57/58/-28 | 248868|165224 | 1636 | 23.6 | 0.00/0.12 | 0.33/0.02 | 0.13/1.00 | False | 585 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 60 pts hw2 fresh=t0 | skip | london | 56/-54/54/-19 | 35161|79907/63964|140288 | 59/57/-11 | 262029|165224 | 1662 | 23.3 | 0.00/0.14 | 0.33/0.02 | 0.20/1.00 | False | 585 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 60 pts hw10 fresh=t0 | skip | london | 54/-49/55/-13 | 36359|79907/62667|140288 | 57/58/-6 | 246850|165224 | 1555 | 24.1 | 0.00/0.16 | 0.33/0.02 | 0.16/1.00 | False | 585 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 60 pts hw2 fresh=t0 age<=1d | skip | london | 56/-56/54/-32 | 35161|79907/64391|140288 | 59/57/-23 | 264047|165224 | 1743 | 22.9 | 0.00/0.14 | 0.33/0.02 | 0.15/1.00 | False | 585 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 60 pts hw5 fresh=t0 age<=5d | skip | london | 56/-44/54/-20 | 35161|79907/63964|140288 | 59/57/-12 | 254328|165224 | 1511 | 23.6 | 0.00/0.16 | 0.33/0.02 | 0.13/1.00 | False | 585 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 60 pts hw5 fresh=t0 age<=1d | skip | london | 56/-44/54/-30 | 35161|79907/63964|140288 | 58/57/-23 | 250979|165224 | 1377 | 23.2 | 0.00/0.14 | 0.33/0.02 | 0.08/1.00 | False | 585 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 60 pts hw5 fresh=t0 | skip | london | 56/-42/54/-13 | 35161|79907/63964|140288 | 58/57/-7 | 248962|165224 | 1296 | 23.7 | 0.00/0.18 | 0.33/0.02 | 0.18/1.00 | False | 585 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 1 atr fresh=t1 age<=1d | skip | london | 52/-26/51/-19 | 38750|79907/68075|140288 | 56/56/-8 | 307992|165224 | 2629 | 23.6 | 0.00/0.33 | 0.33/0.02 | 0.30/1.00 | False | 6170 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 1 atr fresh=t1 age<=4h | skip | london | 52/-30/51/-16 | 38750|79907/69281|140288 | 56/56/-5 | 308939|165224 | 3020 | 23.2 | 0.00/0.35 | 0.33/0.02 | 0.36/1.00 | False | 6170 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 1 atr fresh=t1 age<=5d | skip | london | 52/-26/51/-21 | 38750|79907/69054|140288 | 56/55/-11 | 308642|165224 | 2655 | 23.6 | 0.00/0.37 | 0.33/0.02 | 0.46/1.00 | False | 6170 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 1 atr fresh=t1 | skip | london | 52/-26/51/-21 | 38750|79907/69054|140288 | 56/55/-11 | 307443|165224 | 2607 | 23.7 | 0.00/0.39 | 0.33/0.02 | 0.39/1.00 | False | 6170 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 1.5 atr fresh=t0 age<=1d | skip | london | 54/-46/51/-46 | 36908|79907/69132|140288 | 58/55/-34 | 270296|165224 | 2103 | 21.4 | 0.00/0.22 | 0.33/0.02 | 0.23/1.00 | False | 2570 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 1.5 atr fresh=t0 age<=5d | skip | london | 54/-46/51/-45 | 36908|79907/69132|140288 | 57/54/-34 | 273645|165224 | 2185 | 21.5 | 0.00/0.23 | 0.33/0.02 | 0.20/1.00 | False | 2570 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |

Label counts in the ledger: {'LEAD': 172}

## Family B - VWAP / volume-profile family (session/RTH VWAP and sigma bands, anchored VWAPs, developing/prior/composite POC VAH VAL, naked POCs, HVN/LVN)

B: the best equal-mean cell is a **skip** when the B ahead 0.25 atr hw10 age<=1h (level set ALL) is within reach, scope london: stack maxDD cut 42/57/-8 % (L6M/PRE/X') at equal lots and 50/63/6 % at equal mean, touching 20.9% of trades; label **LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY]**. It does not hold as a setting because X' maxDD gets worse by 8%; the purged walk-forward of the picking procedure does not beat the live layer; the family max-stat over the whole zone set (p 1.00) is not cleared; levels shifted by +/-25 pts do as well (p_shift 0.33), so the cut is not level-specific. The live HALF D20 + OTE-62 B73 D30 layer stays ON.

Ranked by min(equal-mean cut L6M, PRE) among screen passers; top 15 (full grid in /mnt/l2/l2vast/_th_zn/grid_all.parquet).

| level | geometry | action | scope (book|session) | maxDD cut % L6M/HOLD/PRE/X' | maxDD $ cell|ref L6M/PRE | equal-mean cut % L6M/PRE/X' | worst-20 L6M cell|ref | d mean $/wk L6M | trades touched % | placebo p L6M/PRE (B400) | shift/day placebo p | own p | family p (max) | WF ok | live-week d$ | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | ahead 0.25 atr hw10 age<=1h | skip | london | 42/-79/57/-8 | 46497|79907/60378|140288 | 50/63/6 | 231738|165224 | 3488 | 20.9 | 0.03/0.03 | 0.33/0.02 | 0.05/1.00 | False | 3715 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 15 pts hw10 age<=1h | skip | london | 40/-83/54/-14 | 47696|79907/64273|140288 | 49/61/3 | 247269|165224 | 4310 | 24.6 | 0.11/0.30 | 0.33/0.10 | 0.36/1.00 | False | 4305 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 0.25 atr hw10 fresh=t1 age<=1d | skip | london | 40/-87/60/-4 | 47696|79907/56199|140288 | 48/65/10 | 241134|165224 | 3580 | 21.2 | 0.03/0.00 | 0.33/0.07 | 0.13/1.00 | False | 4370 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 15 pts hw10 fresh=t1 age<=1d | skip | london | 39/-88/57/-16 | 48895|79907/60102|140288 | 48/63/1 | 252020|165224 | 4216 | 24.8 | 0.11/0.11 | 0.33/0.13 | 0.15/1.00 | False | 4960 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 0.25 atr hw10 fresh=t0 age<=1d | skip | london | 40/-87/60/-10 | 47696|79907/56199|140288 | 48/65/3 | 233844|165224 | 3267 | 21.2 | 0.05/0.00 | 0.33/0.10 | 0.08/1.00 | False | 3715 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 15 pts hw10 fresh=t0 age<=1d | skip | london | 39/-88/57/-16 | 48895|79907/60102|140288 | 48/63/0 | 249251|165224 | 4084 | 24.8 | 0.10/0.10 | 0.33/0.20 | 0.16/1.00 | False | 4305 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 0.25 atr hw10 fresh=t1 | skip | london | 40/-92/60/-3 | 47696|79907/55621|140288 | 47/65/9 | 228696|165224 | 3116 | 21.4 | 0.05/0.00 | 0.33/0.05 | 0.11/1.00 | False | 4370 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 0.25 atr hw10 fresh=t1 age<=5d | skip | london | 40/-92/60/-4 | 47696|79907/55621|140288 | 47/65/8 | 228696|165224 | 3054 | 21.4 | 0.06/0.00 | 0.33/0.05 | 0.05/1.00 | False | 4370 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 15 pts hw10 fresh=t1 | skip | london | 39/-95/58/-15 | 48895|79907/59420|140288 | 47/63/-0 | 240877|165224 | 3736 | 24.9 | 0.15/0.09 | 0.33/0.07 | 0.16/1.00 | False | 4960 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 15 pts hw10 fresh=t1 age<=5d | skip | london | 39/-95/58/-16 | 48895|79907/59420|140288 | 47/63/-1 | 240877|165224 | 3674 | 24.9 | 0.11/0.08 | 0.33/0.18 | 0.21/1.00 | False | 4960 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 0.25 atr hw10 fresh=t0 | skip | london | 40/-92/60/-9 | 47696|79907/55621|140288 | 47/65/3 | 221406|165224 | 2930 | 21.3 | 0.05/0.00 | 0.33/0.08 | 0.11/1.00 | False | 3715 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 0.25 atr hw10 fresh=t0 age<=5d | skip | london | 40/-92/60/-10 | 47696|79907/55621|140288 | 47/65/2 | 221406|165224 | 2898 | 21.3 | 0.06/0.00 | 0.33/0.07 | 0.13/1.00 | False | 3715 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 15 pts hw10 fresh=t0 | skip | london | 39/-95/58/-15 | 48895|79907/59420|140288 | 47/63/-1 | 236814|165224 | 3523 | 24.9 | 0.14/0.08 | 0.33/0.15 | 0.18/1.00 | False | 4305 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 15 pts hw10 fresh=t0 age<=5d | skip | london | 39/-95/58/-16 | 48895|79907/59420|140288 | 46/63/-2 | 236814|165224 | 3491 | 24.9 | 0.16/0.09 | 0.33/0.11 | 0.13/1.00 | False | 4305 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 30 pts hw2 age<=1h | skip | london | 35/-75/57/-14 | 51654|79907/60102|140288 | 46/64/5 | 245651|165224 | 4879 | 26.9 | 0.30/0.22 | 0.33/0.33 | 0.28/1.00 | False | 11005 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |

Label counts in the ledger: {'LEAD': 172}

## Family C - Swing / market structure

C: the best equal-mean cell is a **skip** when the C sw1_5 nan (level set nan) is within reach, scope ALL: stack maxDD cut 68/62/56 % (L6M/PRE/X') at equal lots and 64/58/50 % at equal mean, touching % of trades; label **NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD]**. It does not hold as a setting because the family max-stat over the whole zone set (p 1.00) is not cleared. The live HALF D20 + OTE-62 B73 D30 layer stays ON.

Ranked by min(equal-mean cut L6M, PRE) among screen passers; top 15 (full grid in /mnt/l2/l2vast/_th_zn/grid_all.parquet).

| level | geometry | action | scope (book|session) | maxDD cut % L6M/HOLD/PRE/X' | maxDD $ cell|ref L6M/PRE | equal-mean cut % L6M/PRE/X' | worst-20 L6M cell|ref | d mean $/wk L6M | trades touched % | placebo p L6M/PRE (B400) | shift/day placebo p | own p | family p (max) | WF ok | live-week d$ | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| nan | sw1_5 nan | skip | ALL | 68/-26/62/56 | 25839|79907/52879|140288 | 64/58/50 | 215168|165224 | -2392 |  | / | /0.17 | 0.16/1.00 | True | -91315 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | sw5_5 nan | skip | ALL | 49/3/51/34 | 40759|79907/68648|140288 | 57/58/44 | 284901|165224 | 4333 |  | / | / | 0.06/1.00 | True | 14410 | S1 | CANDIDATE (own-p only; family p 1.00) PRE-PROOF |
| nan | sw15_3 nan | skip | ALL | 56/58/54/60 | 35508|79907/63885|140288 | 57/56/61 | 251349|165224 | 725 |  | / | /0.02 | 0.07/1.00 | True | -65500 | S1 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| nan | sw1_3 nan | skip | ALL | 66/8/60/70 | 27176|79907/55530|140288 | 62/55/66 | 235293|165224 | -2375 |  | / | /0.17 | 0.22/1.00 | True | -87550 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | sw1_5 nan | skip | ALL | 69/11/53/44 | 24730|79907/66594|140288 | 71/55/47 | 270977|165224 | 1194 |  | / | /0.32 | 0.33/1.00 | True | -89055 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | sw15_3 nan | skip | ALL | 56/56/54/52 | 35508|79907/63885|140288 | 56/55/53 | 245014|165224 | 287 |  | / | /0.02 | 0.03/1.00 | True | -66905 | S1 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| nan | sw1_5 nan | skip | ALL | 65/-32/61/59 | 28103|79907/55358|140288 | 60/55/53 | 220845|165224 | -2703 |  | / | /0.17 | 0.19/1.00 | True | -86520 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | sw1_3 nan | skip | ALL | 66/11/59/70 | 27176|79907/57347|140288 | 62/55/67 | 236182|165224 | -2083 |  | / | /0.17 | 0.19/1.00 | True | -87550 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | sw1_5 nan | skip | ALL | 65/-33/61/58 | 28103|79907/55358|140288 | 59/54/52 | 205750|165224 | -2878 |  | / | /0.07 | 0.07/1.00 | True | -93030 | S1 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| nan | sw1_5 nan | skip | ALL | 69/9/53/44 | 24730|79907/66594|140288 | 70/54/46 | 260590|165224 | 779 |  | / | / | 0.29/1.00 | True | -89055 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | sw1_5 nan | skip | ALL | 55/20/55/55 | 36163|79907/63487|140288 | 53/53/53 | 232887|165224 | -938 |  | / | /0.32 | 0.38/1.00 | True | -92865 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | sw5_3 nan | skip | ALL | 66/28/56/53 | 27549|79907/61881|140288 | 63/52/49 | 244467|165224 | -1712 |  | / | /0.07 | 0.08/1.00 | True | -83110 | S1 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| nan | ob15 nan | quarter | ALL | 62/49/62/58 | 30349|79907/53408|140288 | 52/52/47 | 156701|165224 | -4383 |  | / | / | 0.01/1.00 | True | -39058 | S1 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| nan | ob15 nan | quarter | ALL | 64/49/61/54 | 28662|79907/54361|140288 | 55/52/42 | 156133|165224 | -4262 |  | / | / | 0.01/1.00 | True | -36143 | S1 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| nan | sw1_2 nan | skip | ALL | 55/17/44/52 | 36213|79907/79213|140288 | 61/51/58 | 259649|165224 | 3821 |  | / | /0.10 | 0.11/1.00 | True | -67320 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |

Label counts in the ledger: {'NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD]': 546, 'CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK': 199, 'CANDIDATE (own-p only; family p 1.00)': 37, 'LEAD': 32, 'UP (report, never promoted)': 15, 'NOT-LEVEL-SPECIFIC (shifted levels do as well) [was CANDIDATE]': 13, 'SCOPE-EFFECT [was LEAD]': 8, 'SCOPE-EFFECT [was CANDIDATE]': 3}

## Family D - Moving-average / band levels

D: the best equal-mean cell is a **quarter** when the D kc2.5lo_5 nan (level set nan) is within reach, scope ALL: stack maxDD cut 56/54/26 % (L6M/PRE/X') at equal lots and 54/53/23 % at equal mean, touching % of trades; label **NOT-LEVEL-SPECIFIC (shifted levels do as well) [was CANDIDATE]**. It does not hold as a setting because the family max-stat over the whole zone set (p 1.00) is not cleared. The live HALF D20 + OTE-62 B73 D30 layer stays ON.

Ranked by min(equal-mean cut L6M, PRE) among screen passers; top 15 (full grid in /mnt/l2/l2vast/_th_zn/grid_all.parquet).

| level | geometry | action | scope (book|session) | maxDD cut % L6M/HOLD/PRE/X' | maxDD $ cell|ref L6M/PRE | equal-mean cut % L6M/PRE/X' | worst-20 L6M cell|ref | d mean $/wk L6M | trades touched % | placebo p L6M/PRE (B400) | shift/day placebo p | own p | family p (max) | WF ok | live-week d$ | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| nan | kc2.5lo_5 nan | quarter | ALL | 56/35/54/26 | 35507|79907/63998|140288 | 54/53/23 | 191173|165224 | -879 |  | / | / | 0.02/1.00 | True | -55894 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was CANDIDATE] |
| nan | bblo_5 nan | skip | ALL | 57/50/53/48 | 34156|79907/65704|140288 | 55/51/46 | 247020|165224 | -932 |  | / | /0.37 | 0.41/1.00 | True | -75270 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | kc2.5lo_5 nan | quarter | ALL | 52/38/54/30 | 38390|79907/64073|140288 | 50/52/27 | 188492|165224 | -1027 |  | / | / | 0.01/1.00 | True | -60694 | S1 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| nan | kc2.5lo_5 nan | quarter | ALL | 50/41/54/30 | 39935|79907/64073|140288 | 47/51/25 | 180942|165224 | -1446 |  | / | / | 0.03/1.00 | True | -60694 | S1 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| nan | k7any nan | skip | ALL | 50/33/47/47 | 40204|79907/74992|140288 | 49/46/46 | 181612|165224 | -117 |  | / | /0.05 | 0.03/1.00 | True | -41425 | S1 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| nan | bbup_5 nan | skip | ALL | 47/-17/49/39 | 42040|79907/72131|140288 | 46/47/37 | 178621|165224 | -655 |  | / | /0.44 | 0.57/1.00 | True | 4220 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | kc2.5lo_5 nan | quarter | ALL | 48/35/54/27 | 41503|79907/64642|140288 | 46/52/24 | 190169|165224 | -891 |  | / | / | 0.02/1.00 | True | -53494 | S1 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| nan | bblo_5 nan | skip | ALL | 57/50/53/45 | 34156|79907/65304|140288 | 50/45/35 | 215148|165224 | -3131 |  | / | / | 0.55/1.00 | True | -72405 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | maall_15 nan | skip | ALL | 34/-5/43/38 | 52561|79907/80437|140288 | 45/52/48 | 230631|165224 | 4269 |  | / | /0.20 | 0.16/1.00 | True | -9925 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | bbup_15 nan | quarter | ALL | 57/25/61/42 | 34405|79907/54502|140288 | 44/50/25 | 144252|165224 | -5323 |  | / | / | 0.01/1.00 | True | -35704 | S1 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| nan | kc2.5lo_5 nan | skip | ALL | 39/-22/34/25 | 48630|79907/92931|140288 | 49/44/37 | 200418|165224 | 4349 |  | / | / | 0.91/1.00 | True | 3770 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | kc2.5lo_5 nan | skip | ALL | 46/-44/48/36 | 43489|79907/72502|140288 | 44/47/34 | 200870|165224 | -730 |  | / | / | 0.68/1.00 | True | 170 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | kc2.5lo_5 nan | quarter | ALL | 38/-3/42/30 | 49412|79907/81113|140288 | 44/48/37 | 196903|165224 | 2398 |  | / | / | 0.02/1.00 | True | 5073 | S1 | CANDIDATE (own-p only; family p 1.00) PRE-PROOF |
| nan | k7any nan | skip | ALL | 57/22/44/57 | 34684|79907/78583|140288 | 56/44/57 | 178507|165224 | -96 |  | / | /0.05 | 0.08/1.00 | True | -41385 | S1 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| nan | stany nan | skip | ALL | 57/33/39/40 | 34255|79907/85326|140288 | 60/44/44 | 217339|165224 | 1802 |  | / | /0.10 | 0.10/1.00 | True | -50875 | S1 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |

Label counts in the ledger: {'NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD]': 636, 'CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK': 98, 'LEAD': 53, 'UP (report, never promoted)': 15, 'NOT-LEVEL-SPECIFIC (shifted levels do as well) [was CANDIDATE]': 14, 'CANDIDATE (own-p only; family p 1.00)': 14, 'no': 2, 'SCOPE-EFFECT [was CANDIDATE]': 1, 'SCOPE-EFFECT [was LEAD]': 1}

## Family E - Round numbers / grid

E: the best equal-mean cell is a **skip** when the E grid0.5 nan (level set nan) is within reach, scope ALL: stack maxDD cut 45/51/25 % (L6M/PRE/X') at equal lots and 52/56/33 % at equal mean, touching % of trades; label **NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD]**. It does not hold as a setting because the family max-stat over the whole zone set (p 1.00) is not cleared. The live HALF D20 + OTE-62 B73 D30 layer stays ON.

Ranked by min(equal-mean cut L6M, PRE) among screen passers; top 15 (full grid in /mnt/l2/l2vast/_th_zn/grid_all.parquet).

| level | geometry | action | scope (book|session) | maxDD cut % L6M/HOLD/PRE/X' | maxDD $ cell|ref L6M/PRE | equal-mean cut % L6M/PRE/X' | worst-20 L6M cell|ref | d mean $/wk L6M | trades touched % | placebo p L6M/PRE (B400) | shift/day placebo p | own p | family p (max) | WF ok | live-week d$ | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| nan | grid0.5 nan | skip | ALL | 45/-38/51/25 | 43582|79907/69372|140288 | 52/56/33 | 267197|165224 | 3431 |  | / | /0.17 | 0.29/1.00 | True | -6525 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | grid0.5 nan | skip | ALL | 45/-50/49/22 | 43582|79907/71516|140288 | 51/54/30 | 270547|165224 | 3047 |  | / | /0.66 | 0.55/1.00 | True | -12570 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | grid0.5 nan | skip | ALL | 44/-41/50/23 | 44577|79907/70213|140288 | 50/55/32 | 259376|165224 | 2952 |  | / | /0.17 | 0.20/1.00 | True | -8270 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | grid0.5 nan | skip | ALL | 42/-31/46/34 | 45980|79907/76317|140288 | 48/51/40 | 259551|165224 | 2885 |  | / | /0.59 | 0.53/1.00 | True | -12530 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | rn50 nan | skip | ALL | 43/-25/41/3 | 45810|79907/83073|140288 | 49/47/14 | 230793|165224 | 2695 |  | / | / | 0.79/1.00 | True | -10660 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | grid1 nan | skip | ALL | 38/-17/57/6 | 49928|79907/60887|140288 | 47/63/20 | 217253|165224 | 3590 |  | / | / | 0.38/1.00 | True | -9980 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | grid0.5 nan | skip | ALL | 44/-39/38/16 | 44728|79907/86833|140288 | 51/46/27 | 268894|165224 | 3820 |  | / | / | 0.90/1.00 | True | -11785 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | grid0.5 nan | skip | ALL | 49/-42/53/15 | 40475|79907/65921|140288 | 46/50/9 | 171048|165224 | -1866 |  | / | / | 0.70/1.00 | True | -640 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | grid0.5 nan | skip | ALL | 43/-43/38/15 | 45926|79907/86705|140288 | 49/46/25 | 264079|165224 | 3658 |  | / | / | 0.95/1.00 | True | -11785 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | rn50 nan | skip | ALL | 41/-33/48/0 | 47331|79907/73229|140288 | 45/52/8 | 203617|165224 | 1622 |  | / | / | 0.80/1.00 | True | -3335 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | grid0.5 nan | skip | ALL | 39/-60/51/9 | 48378|79907/68932|140288 | 44/55/16 | 262139|165224 | 2399 |  | / | / | 0.63/1.00 | True | -10130 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | rn50 nan | skip | ALL | 49/47/48/20 | 40972|79907/72663|140288 | 44/43/13 | 208629|165224 | -2004 |  | / | / | 0.11/1.00 | True | -49890 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | rn50 nan | skip | ALL | 39/-28/45/2 | 48351|79907/77808|140288 | 43/48/8 | 192279|165224 | 1344 |  | / | / | 0.75/1.00 | True | -15715 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | rn25 nan | quarter | ALL | 61/57/62/61 | 31141|79907/53687|140288 | 43/44/42 | 143247|165224 | -6711 |  | / | /0.02 | 0.02/1.00 | True | -61140 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was CANDIDATE] |
| nan | grid0.5 nan | skip | ALL | 33/-36/42/19 | 53826|79907/80796|140288 | 43/51/31 | 275525|165224 | 4333 |  | / | /0.80 | 0.69/1.00 | True | -8890 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |

Label counts in the ledger: {'NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD]': 528, 'NOT-LEVEL-SPECIFIC (shifted levels do as well) [was CANDIDATE]': 29, 'UP (report, never promoted)': 15, 'CANDIDATE (own-p only; family p 1.00)': 13, 'CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK': 13, 'SCOPE-EFFECT [was LEAD]': 9, 'LEAD': 9, 'SCOPE-EFFECT [was CANDIDATE]': 4, 'no': 1}

## Family F - Book-derived

F: the best equal-mean cell is a **skip** when the F ahead 0.5 atr [nan] (level set swp_w300_t6) is within reach, scope ALL: stack maxDD cut 54/54/20 % (L6M/PRE/X') at equal lots and 49/49/11 % at equal mean, touching 14.9% of trades; label **CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF**. It does not hold as a setting because the family max-stat over the whole zone set (p 1.00) is not cleared. The live HALF D20 + OTE-62 B73 D30 layer stays ON.

Ranked by min(equal-mean cut L6M, PRE) among screen passers; top 15 (full grid in /mnt/l2/l2vast/_th_zn/grid_all.parquet).

| level | geometry | action | scope (book|session) | maxDD cut % L6M/HOLD/PRE/X' | maxDD $ cell|ref L6M/PRE | equal-mean cut % L6M/PRE/X' | worst-20 L6M cell|ref | d mean $/wk L6M | trades touched % | placebo p L6M/PRE (B400) | shift/day placebo p | own p | family p (max) | WF ok | live-week d$ | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| swp_w300_t6 | ahead 0.5 atr [nan] | skip | ALL | 54/39/54/20 | 36558|79907/64123|140288 | 49/49/11 | 152805|165224 | -2340 | 14.9 | / | / | 0.04/1.00 | True | -72315 | S1 first-order SCREEN ONLY | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| swp_w300_t6 | ahead 0.5 atr [nan] | skip | ALL | 54/39/54/20 | 36558|79907/64123|140288 | 49/49/11 | 152805|165224 | -2340 | 14.9 | / | / | 0.04/1.00 | True | -72315 | S1 first-order SCREEN ONLY | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| swp_w300_t6 | ahead 5 pts [nan] | skip | ALL | 54/49/54/26 | 36558|79907/64613|140288 | 47/47/15 | 140691|165224 | -2914 | 15.4 | / | / | 0.06/1.00 | True | -76525 | S1 first-order SCREEN ONLY | LEAD PRE-PROOF |
| swp_w300_t6 | ahead 5 pts [nan] | skip | ALL | 54/49/54/26 | 36558|79907/64613|140288 | 47/47/15 | 140691|165224 | -2914 | 15.4 | / | / | 0.06/1.00 | True | -76525 | S1 first-order SCREEN ONLY | LEAD PRE-PROOF |
| swp_w300_t6 | ahead 1 atr [nan] | skip | ALL | 54/46/55/33 | 36558|79907/63361|140288 | 46/46/20 | 131856|165224 | -3555 | 15.5 | / | / | 0.06/1.00 | True | -72315 | S1 first-order SCREEN ONLY | LEAD PRE-PROOF |
| swp_w300_t6 | ahead 20 pts [nan] | skip | ALL | 54/49/56/40 | 36558|79907/61190|140288 | 46/48/28 | 131856|165224 | -3555 | 15.6 | / | 0.00/0.03 | 0.04/1.00 | True | -72315 | S1 first-order SCREEN ONLY | LEAD PRE-PROOF |
| swp_w300_t6 | ahead 10 pts [nan] | skip | ALL | 54/49/56/40 | 36558|79907/61190|140288 | 46/48/28 | 131856|165224 | -3555 | 15.6 | / | 0.00/0.05 | 0.05/1.00 | True | -72315 | S1 first-order SCREEN ONLY | LEAD PRE-PROOF |
| swp_w300_t6 | ahead 10 pts [nan] | skip | ALL | 54/49/56/40 | 36558|79907/61190|140288 | 46/48/28 | 131856|165224 | -3555 | 15.6 | / | 0.00/0.05 | 0.05/1.00 | True | -72315 | S1 first-order SCREEN ONLY | LEAD PRE-PROOF |
| swp_w300_t6 | ahead 20 pts [nan] | skip | ALL | 54/49/56/40 | 36558|79907/61190|140288 | 46/48/28 | 131856|165224 | -3555 | 15.6 | / | 0.00/0.03 | 0.04/1.00 | True | -72315 | S1 first-order SCREEN ONLY | LEAD PRE-PROOF |
| swp_w300_t6 | ahead 1 atr [nan] | skip | ALL | 54/46/55/33 | 36558|79907/63361|140288 | 46/46/20 | 131856|165224 | -3555 | 15.5 | / | / | 0.06/1.00 | True | -72315 | S1 first-order SCREEN ONLY | LEAD PRE-PROOF |
| swp_w900_t6 | ahead 0.5 atr [nan] | quarter | ALL | 57/38/56/26 | 34440|79907/61654|140288 | 46/45/8 | 179099|165224 | -4406 | 64.8 | / | / | 0.02/1.00 | True | -41344 | S1 first-order SCREEN ONLY | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| swp_w900_t6 | ahead 0.5 atr [nan] | quarter | ALL | 57/38/56/26 | 34440|79907/61654|140288 | 46/45/8 | 179099|165224 | -4406 | 64.8 | / | / | 0.02/1.00 | True | -41344 | S1 first-order SCREEN ONLY | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| swp_w300_t6 | ahead 90 pts [nan] | skip | ALL | 54/49/56/40 | 36558|79907/61190|140288 | 45/48/27 | 131856|165224 | -3747 | 15.7 | / | 1.00/0.06 | 0.05/1.00 | True | -72315 | S1 first-order SCREEN ONLY | LEAD PRE-PROOF |
| swp_w300_t6 | ahead 90 pts [nan] | skip | ALL | 54/49/56/40 | 36558|79907/61190|140288 | 45/48/27 | 131856|165224 | -3747 | 15.7 | / | 1.00/0.06 | 0.05/1.00 | True | -72315 | S1 first-order SCREEN ONLY | LEAD PRE-PROOF |
| swp_w900_t6 | ahead 5 pts [nan] | quarter | ALL | 57/39/60/13 | 34440|79907/55776|140288 | 44/49/-12 | 171184|165224 | -5011 | 67.1 | / | / | 0.01/1.00 | True | -45126 | S1 first-order SCREEN ONLY | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |

Label counts in the ledger: {'no': 49760, 'LEAD': 5904, 'UP (report, never promoted)': 2972, 'SCOPE-EFFECT (no equal-mean gain over the same action on every trade of ALL)': 1492, 'SCOPE-EFFECT (no equal-mean gain over the same action on every trade of s:nyam)': 512, 'SCOPE-EFFECT (no equal-mean gain over the same action on every trade of s:london)': 426, 'SCOPE-EFFECT (no equal-mean gain over the same action on every trade of b:PE)': 420, 'SCOPE-EFFECT (no equal-mean gain over the same action on every trade of bs:PE:nyam)': 416, 'SCOPE-EFFECT (no equal-mean gain over the same action on every trade of bs:SM:london)': 362, 'SCOPE-EFFECT (no equal-mean gain over the same action on every trade of bs:PE:london)': 298, 'SCOPE-EFFECT (no equal-mean gain over the same action on every trade of b:MV)': 272, 'SCOPE-EFFECT (no equal-mean gain over the same action on every trade of bs:MV:london)': 268, 'SCOPE-EFFECT (no equal-mean gain over the same action on every trade of b:KB)': 252, 'CANDIDATE (own-p only; family p 1.00)': 214, 'CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK': 204, 'SCOPE-EFFECT (no equal-mean gain over the same action on every trade of bs:KB:london)': 170, 'SCOPE-EFFECT (no equal-mean gain over the same action on every trade of bs:KB:nypm)': 116, 'SCOPE-EFFECT (no equal-mean gain over the same action on every trade of s:nypm)': 116, 'SCOPE-EFFECT (no equal-mean gain over the same action on every trade of b:SM)': 70, 'SCOPE-EFFECT (no equal-mean gain over the same action on every trade of bs:KB:asia)': 56, 'SCOPE-EFFECT (no equal-mean gain over the same action on every trade of bs:KB:nyam)': 4, 'SCOPE-EFFECT (no equal-mean gain over the same action on every trade of bs:MV:nyam)': 4, 'SCOPE-EFFECT (no equal-mean gain over the same action on every trade of bs:SM:asia)': 2}

## Family G - Event / time levels (09:30 / 10:00 / 11:30 / 15:00 prints, settlement, first-5-min range)

G: the best equal-mean cell is a **skip** when the G behind 90 pts age<=4h (level set ALL) is within reach, scope ALL: stack maxDD cut 14/18/27 % (L6M/PRE/X') at equal lots and 21/25/34 % at equal mean, touching 27.2% of trades; label **LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY]**. It does not hold as a setting because the random same-count placebo reaches it (p 0.36); the family max-stat over the whole zone set (p 1.00) is not cleared; levels shifted by +/-25 pts do as well (p_shift 0.33), so the cut is not level-specific. The live HALF D20 + OTE-62 B73 D30 layer stays ON.

Ranked by min(equal-mean cut L6M, PRE) among screen passers; top 15 (full grid in /mnt/l2/l2vast/_th_zn/grid_all.parquet).

| level | geometry | action | scope (book|session) | maxDD cut % L6M/HOLD/PRE/X' | maxDD $ cell|ref L6M/PRE | equal-mean cut % L6M/PRE/X' | worst-20 L6M cell|ref | d mean $/wk L6M | trades touched % | placebo p L6M/PRE (B400) | shift/day placebo p | own p | family p (max) | WF ok | live-week d$ | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | behind 90 pts age<=4h | skip | ALL | 14/13/18/27 | 68850|79907/115341|140288 | 21/25/34 | 241851|165224 | 2469 | 27.2 | 0.36/0.21 | 0.33/0.38 | 0.33/1.00 | True | -11225 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | behind 90 pts hw5 age<=4h | skip | ALL | 12/14/19/26 | 70048|79907/113530|140288 | 21/27/33 | 249923|165224 | 2886 | 27.6 | 0.46/0.19 | 0.33/0.52 | 0.51/1.00 | True | -10510 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | behind 90 pts hw10 age<=4h | skip | ALL | 12/20/18/30 | 70048|79907/115161|140288 | 21/26/37 | 250281|165224 | 2754 | 28.0 | 0.45/0.30 | 0.33/0.54 | 0.46/1.00 | True | -10510 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | behind 90 pts hw2 age<=4h | skip | ALL | 12/13/19/25 | 70048|79907/113530|140288 | 20/26/32 | 242515|165224 | 2445 | 27.3 | 0.46/0.18 | 0.33/0.44 | 0.57/1.00 | True | -11225 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | behind 90 pts age<=1d | skip | ALL | 12/14/19/25 | 70048|79907/113229|140288 | 20/26/31 | 239094|165224 | 2311 | 27.6 | 0.45/0.15 | 0.33/0.52 | 0.56/1.00 | True | -11225 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | behind 90 pts hw5 age<=1d | skip | ALL | 11/14/21/22 | 71247|79907/111418|140288 | 19/28/30 | 248452|165224 | 2728 | 28.1 | 0.55/0.10 | 0.33/0.66 | 0.61/1.00 | True | -10510 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | behind 90 pts hw10 age<=1d | skip | ALL | 11/20/19/27 | 71247|79907/113050|140288 | 19/27/34 | 248810|165224 | 2548 | 28.5 | 0.56/0.23 | 0.33/0.62 | 0.66/1.00 | True | -10510 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | behind 90 pts hw2 age<=1d | skip | ALL | 11/14/21/22 | 71247|79907/111418|140288 | 18/27/29 | 239757|165224 | 2287 | 27.8 | 0.50/0.11 | 0.33/0.51 | 0.54/1.00 | True | -11225 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | behind 1.5 atr hw5 age<=4h | skip | ALL | 12/13/11/36 | 70005|79907/124684|140288 | 19/18/40 | 238210|165224 | 1945 | 26.2 | 0.43/0.74 | 0.33/0.34 | 0.70/1.00 | True | -10885 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | behind 1.5 atr hw10 age<=4h | skip | ALL | 11/21/12/35 | 71204|79907/124037|140288 | 17/18/40 | 241257|165224 | 1905 | 26.9 | 0.50/0.67 | 0.33/0.61 | 0.56/1.00 | True | -13285 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | behind 90 pts hw5 age<=4h | skip | PE|nyam | 6/16/18/21 | 75075|79907/114682|140288 | 17/28/30 | 254649|165224 | 2904 | 5.3 | 0.86/0.11 | 0.67/0.84 | 0.82/1.00 | True | -3995 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | behind 90 pts hw10 age<=4h | skip | PE|nyam | 6/24/18/24 | 75075|79907/114682|140288 | 17/28/33 | 254649|165224 | 2904 | 5.3 | 0.84/0.12 | 0.67/0.90 | 0.82/1.00 | True | -3995 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | behind 90 pts hw10 age<=4h | skip | PE | 6/24/18/24 | 75075|79907/114682|140288 | 17/28/33 | 254649|165224 | 2904 | 5.3 | 0.87/0.11 | 0.67/0.87 | 0.87/1.00 | True | -3995 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | behind 90 pts hw5 age<=4h | skip | PE | 6/16/18/21 | 75075|79907/114682|140288 | 17/28/30 | 254649|165224 | 2904 | 5.3 | 0.83/0.13 | 0.67/0.79 | 0.84/1.00 | True | -3995 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | behind 1.5 atr hw5 age<=1d | skip | ALL | 11/13/13/38 | 71204|79907/122280|140288 | 17/18/42 | 234858|165224 | 1719 | 26.7 | 0.56/0.57 | 0.33/0.62 | 0.67/1.00 | True | -10300 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |

Label counts in the ledger: {'LEAD': 51, 'CANDIDATE (own-p only; family p 1.00)': 5}

## Family S4 - S4

S4: the best equal-mean cell is a **half** when the S4   pts fresh=nan age<=nan [nan] (level set PoiSet8) is within reach, scope ALL: stack maxDD cut 35/37/40 % (L6M/PRE/X') at equal lots and 16/18/23 % at equal mean, touching 29.7% of trades; label ****. It does not hold as a setting because the family max-stat over the whole zone set (p 0.88) is not cleared. The live HALF D20 + OTE-62 B73 D30 layer stays ON.

Ranked by min(equal-mean cut L6M, PRE) among screen passers; top 15 (full grid in /mnt/l2/l2vast/_th_zn/grid_all.parquet).

| level | geometry | action | scope (book|session) | maxDD cut % L6M/HOLD/PRE/X' | maxDD $ cell|ref L6M/PRE | equal-mean cut % L6M/PRE/X' | worst-20 L6M cell|ref | d mean $/wk L6M | trades touched % | placebo p L6M/PRE (B400) | shift/day placebo p | own p | family p (max) | WF ok | live-week d$ | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PoiSet8 |   pts fresh=nan age<=nan [nan] | half | ALL | 35/34/37/40 | 51800|79907/88494|140288 | 16/18/23 | 171476|165224 | -6365 | 29.7 | / | / | 0.13/0.88 |  |  | S1 first-order |  |
| PoiSet8 |   pts fresh=nan age<=nan [nan] | half | ALL | 27/34/34/34 | 58541|79907/92287|140288 | 15/24/23 | 169776|165224 | -3124 | 23.8 | / | / | 0.19/0.88 |  |  | S1 first-order |  |
| PoiSet8 |   pts fresh=nan age<=nan [nan] | half | ALL | 32/39/41/35 | 54297|79907/83331|140288 | 4/16/8 | 127095|165224 | -6255 | 32.3 | / | / | 0.21/0.96 |  |  | S1 first-order |  |
| PoiSet8 |   pts fresh=nan age<=nan [nan] | skip | ALL | -2/0/0/7 | 81106|79907/140288|140288 | -1/1/8 | 161906|165224 | 192 | 0.9 | / | / | 0.55/1.00 |  |  | S1 first-order |  |
| PoiSet8 |   pts fresh=nan age<=nan [nan] | half | ALL | 4/23/35/32 | 76875|79907/91492|140288 | -4/30/27 | 145972|165224 | -1644 | 22.2 | / | / | 0.71/1.00 |  |  | S1 first-order |  |
| PoiSet8 |   pts fresh=nan age<=nan [nan] | skip | ALL | -5/0/0/24 | 83563|79907/140288|140288 | -4/1/24 | 155677|165224 | 214 | 4.0 | / | / | 0.64/1.00 |  |  | S1 first-order |  |
| PoiSet8 |   pts fresh=nan age<=nan [nan] | skip | ALL | -6/2/1/17 | 84813|79907/139288|140288 | -4/3/18 | 143806|165224 | 462 | 7.1 | / | / | 0.73/1.00 |  |  | S1 first-order |  |
| PoiSet8 |   pts fresh=nan age<=nan [nan] | skip | ALL | 3/-9/17/-18 | 77762|79907/116117|140288 | -6/10/-28 | 126576|165224 | -1858 | 23.7 | / | / | 0.54/1.00 |  |  | S1 first-order |  |
| PoiSet8 |   pts fresh=nan age<=nan [nan] | ref | ALL | -15/-13/-3/-6 | 91798|79907/144258|140288 | -9/2/-1 | 167377|165224 | 1352 | 7.5 | / | / | 0.38/1.00 |  |  | S1 first-order |  |
| PoiSet8 |   pts fresh=nan age<=nan [nan] | skip | ALL | -10/0/-1/17 | 87811|79907/141487|140288 | -11/-2/16 | 144158|165224 | -273 | 3.7 | / | / | 0.76/1.00 |  |  | S1 first-order |  |
| PoiSet8 |   pts fresh=nan age<=nan [nan] | half | ALL | -4/17/34/30 | 83011|79907/92445|140288 | -11/29/25 | 143220|165224 | -1549 | 17.5 | / | / | 0.81/1.00 |  |  | S1 first-order |  |
| PoiSet8 |   pts fresh=nan age<=nan [nan] | half | ALL | 13/27/35/42 | 69183|79907/91016|140288 | -17/13/21 | 122697|165224 | -7130 | 26.3 | / | / | 0.60/1.00 |  |  | S1 first-order |  |
| PoiSet8 |   pts fresh=nan age<=nan [nan] | ref | ALL | -13/-8/1/7 | 90644|79907/139299|140288 | -18/-3/3 | 140228|165224 | -907 | 4.6 | / | / | 0.68/1.00 |  |  | S1 first-order |  |
| PoiSet8 |   pts fresh=nan age<=nan [nan] | skip | ALL | -9/7/-2/10 | 87357|79907/143530|140288 | -21/-13/0 | 133422|165224 | -2541 | 10.7 | / | / | 0.76/1.00 |  |  | S1 first-order |  |
| PoiSet8 |   pts fresh=nan age<=nan [nan] | skip | ALL | -12/10/4/26 | 89379|79907/135192|140288 | -37/-18/9 | 74442|165224 | -4458 | 16.1 | / | / | 0.68/1.00 |  |  | S1 first-order |  |

Label counts in the ledger: {'': 17}

## Zone layer setting (standing rule: the layer stays ON; skip-all/off are reference rows only)

Cells labelled CANDIDATE in the merged ledgers: %d (all first-order screen, family p mostly 1.00 because the null is the max over the whole zone set of ~235k down-sizing cells). Until an EXACT row beats the live HALF D20 + OTE-62 B73 D30 layer on L6M, PRE, X' and HOLD with placebo/family/WF gates, the recommended setting per book x session is the live layer unchanged. Candidate additions are registered for exact runs in /mnt/l2/l2vast/_th_joint/layers/zone/topK.json (live layer always one of the five).

## Exact-engine rows (REF_ZOFF = zone layer off REFERENCE row; ZNC_* = ZN-CORE top cells)

Months landed: {'REF_ZOFF': 0, 'ZNC_A0': 0, 'ZNC_A1': 0, 'ZNC_B0': 0, 'ZNC_B1': 0}. Rows appear when a whole window (L6M 202605-202610, PRE 202402-202506, X' 202304-202401, HOLD 202511-202604) is present; stage [EXACT partial] otherwise.

No exact month has landed yet (queue position behind tiers 0-1).


## Old-vs-new: every published ZONES-3 / S4 zone cell, with the base-change proof

Columns: **published** = the V13Y/V13T-era ZONES-3 verdict (old per-print-cut engine) as quoted on DS3_TH_S4_ZONES_S1B.md; **S4 page** = the same cell on the S1b-COMB state base as published by S345 (windows as of 2026-10-31, carrying weeks DROPPED before maxDD, the S3 defect, first-order); **new** = the same cell re-scored here on S1b-COMB with ALL weeks and windows as of 2026-11-09 (zone features = the PoiSet replay at the signal second, s345_common.zone_features; Z scorer); **old base** = the same cells (same replay rule) on the old V0 trade list (V13T ts2, 21,397 trades) and on replica HOLD (S1b engine with the old live per-print cut). SAME-TO-DOLLAR: none of the cells is identical between pages (the page used 10-31 windows with the carrying week dropped; new uses 11-09, all weeks). Equal-mean = scale lots so the L6M mean equals the reference (S1b-COMB base layer).

| cell | published L6M/PRE/X' | S4 page L6M/PRE/X' | new L6M/HOLD/PRE/X' | new equal-mean cut L6M/PRE/X' | d mean $/wk L6M | placebo p L6M/PRE (own, B100) | old base V0 L6M/PRE/X' | replica HOLD base L6M/PRE/X' | change vs S4 page (L6M) | verdict |
|---|---|---|---|---|---|---|---|---|---|---|
| ZOFF |  | -9/-3/-18 | -15/-13/-3/-6 | -9/2/-1 | 1352 | 0.38/0.29 | -5/-11/-15 | -18/-7/-27 | -6 | base-ref row |
| ZREPLAY |  | -6/1/-5 | -13/-8/1/7 | -18/-3/3 | -907 | 0.68/0.32 | -9/-7/1 | -33/5/-4 | -7 | base-ref row |
| open20 half | +41 / +17 / +9 (VOLUME) | 45/41/31 | 32/39/41/35 | 4/16/8 | -6255 | 0.21/0.09 | 22/32/3 | 55/38/21 | -13 | L6M and PRE cut > 0 on all 3 bases (screen) |
| open40 half |  | 48/34/20 | 27/34/34/34 | 15/24/23 | -3124 | 0.16/0.19 | 20/24/-22 | 50/26/25 | -21 | L6M and PRE cut > 0 on all 3 bases (screen) |
| open60 half | +42 / +4 / +33 (VOLUME) | 41/34/28 | -4/17/34/30 | -11/29/25 | -1549 | 0.81/0.02 | 4/31/-9 | 30/15/24 | -45 | does not hold on every base; negative at equal mean (cut is lot reduction) |
| openA40 half | +35 / +20 / +41 (VOLUME) | 48/37/31 | 35/34/37/40 | 16/18/23 | -6365 | 0.05/0.13 | 22/26/25 | 54/37/23 | -13 | L6M and PRE cut > 0 on all 3 bases (screen) |
| openA60 half |  | 46/35/18 | 13/27/35/42 | -17/13/21 | -7130 | 0.60/0.14 | -3/19/15 | 44/15/27 | -33 | does not hold on every base; negative at equal mean (cut is lot reduction) |
| sopen40 half | +41 / +11 / +21 (NOISE) | 40/35/23 | 4/23/35/32 | -4/30/27 | -1644 | 0.71/0.04 | 6/26/-15 | 38/26/14 | -36 | L6M and PRE cut > 0 on all 3 bases (screen); negative at equal mean (cut is lot reduction) |
| nA20>=2 skip |  | -6/-1/14 | -10/0/-1/17 | -11/-2/16 | -273 | 0.76/0.67 | 1/6/8 | -16/4/-2 | -4 | does not hold on every base; negative at equal mean (cut is lot reduction) |
| nA20>=3 skip |  | 1/0/-2 | -2/0/0/7 | -1/1/8 | 192 | 0.49/0.55 | 0/0/11 | -1/3/-8 | -2 | does not hold on every base; negative at equal mean (cut is lot reduction) |
| nA40>=1 skip | +5 / -5 / -4 (NOISE (v1.2 assumed); sA40>=1 pub: 36/0/-5 NOISE ONE-WEEK) | -17/9/10 | -27/-2/9/2 | -104/-48/-59 | -8321 | 0.83/0.73 | -9/20/32 | -55/20/12 | -10 | does not hold on every base; negative at equal mean (cut is lot reduction) |
| nA40>=2 skip |  | -1/-2/27 | -9/7/-2/10 | -21/-13/0 | -2541 | 0.57/0.76 | -25/19/33 | -23/5/8 | -8 | does not hold on every base; negative at equal mean (cut is lot reduction) |
| nA40>=3 skip |  | 1/0/21 | -5/0/0/24 | -4/1/24 | 214 | 0.47/0.64 | 2/-2/16 | -8/-9/-1 | -5 | does not hold on every base; negative at equal mean (cut is lot reduction) |
| nA60>=1 skip | +36 / -36 / +7 (NOISE ONE-WEEK) | -11/12/6 | -11/-0/12/6 | -58/-26/-34 | -6498 | 0.66/0.68 | 36/30/-4 | 9/12/-2 | +0 | does not hold on every base; negative at equal mean (cut is lot reduction) |
| nA60>=2 skip |  | -3/4/34 | -12/10/4/26 | -37/-18/9 | -4458 | 0.58/0.68 | -44/2/24 | -43/13/18 | -8 | does not hold on every base; negative at equal mean (cut is lot reduction) |
| nA60>=3 skip |  | 0/1/32 | -6/2/1/17 | -4/3/18 | 462 | 0.50/0.73 | -7/2/28 | -13/-2/1 | -6 | does not hold on every base; negative at equal mean (cut is lot reduction) |
| rho60>=2 skip | +41 / +1 / +36 (VOLUME ONE-WEEK) | 3/15/4 | 3/-9/17/-18 | -6/10/-28 | -1858 | 0.54/0.49 | 38/7/23 | 21/21/-22 | +0 | L6M and PRE cut > 0 on all 3 bases (screen); negative at equal mean (cut is lot reduction) |

ZOFF = live zone half undone (a REFERENCE row: the layer stays ON; a negative cut means removing it deepens drawdown). ZREPLAY = replay of the published 8-line PoiSet HALF D20 on every trade = the REF_S4A first-order cross-check (M table /mnt/l2/l2vast/_th_zn/M_ZN_REF_S4A.npz); in the exact engine the S4A published layer IS the live layer, so its exact row is the live-layer reference row of SZ-CORE (replay vs live half agree on 88.5% of informative trades).

### Whole HALF layer vs zone off (maxDD cut of the layer, + = the layer makes drawdown shallower)

| source | L6M | HOLD | MID | PRE | X' | note |
|---|---|---|---|---|---|---|
| published V13T (old engine; take lines off, lock none) | +20 | +15 | +20 | -1 | -19 | DS3_ZONES_3_HALF_FINAL_V13T.md; ranks vs placebo 0.32 / 0.24 / 0.36 / 0.70 / 0.86 |
| published V13TLIVE | +7 | +7 | +25 | +7 | -16 | DS3_ZONES_3_HALF_FINAL_V13TLIVE.md |
| new S1b-COMB first-order (ZOFF rescored, all weeks, 11-09) | 13 | 11 | -4 | 3 | 6 | layer vs ZOFF; ZOFF is first-order (undo the replay-inferred live half at chain_nz lots) |

### Base-change proof (same reference row, three bases; Q1-A with the live zone layer; stack, all weeks)

| base | trades | zone-inferred share | maxDD L6M | maxDD PRE | maxDD X' | maxDD HOLD | mean $/wk L6M |
|---|---|---|---|---|---|---|---|
| old V0 (V13T ts2, per-print cuts) | 21397 | 8.2% | 104809 | 88180 | 80802 | 122025 | 23778 |
| replica HOLD (S1b engine, old live cut) | 23855 | 7.2% | 119980 | 155580 | 75870 | 119980 | 19166 |
| S1b-COMB (state cut, live D7 v1.5) | 21135 | 7.5% | 79907 | 140288 | 128944 | 99496 | 26769 |

Reading: the base changed (SZ_BASE_PROOF.md: state cuts 38% of exits vs 54-57% per-print cuts, stops 3% -> 14%), and the zone-cell cuts move 20-60 points between bases; the half-type cells keep a positive L6M/PRE cut on every base mainly because they halve 47-81% of trades, which is why the equal-mean column and the placebo decide, not the cut. Per-line published cells (kijun1h, PDmid, CRT4h, KCup4h, camH3, OTE705/79/62 HALF and SKIP marginals; V13T and V13TLIVE) need the exact engine with one line left out and are NOT re-scored here (first-order cannot isolate a line: the replay only stores the nearest line); the whole-layer row above stands in. The B73 / B8 / generic-B73 pages (DS3_B73_ORDERING_NOTE.md, DS3_B8_ZONE_TARGET_SHIPPED_V13Z.md, DS3_ZONES_3_B73_GENERIC.md) are delay/re-target actions: exact-engine only, not re-scored in this refresh.


## Not yet covered (other owners / next refresh)

- Families C (swing/structure), D (MA/band), E (round numbers), F (book-derived): ZN-STRUCT / ZN-BOOK ledgers merged here when present.
- Actions beyond skip/half/quarter/up (delay-until-through, re-targets, structure stop, 70/30 add, state-cut arm, cooldown): exact-engine only, top-5 per family, queued via SZ-CORE.
- Entry-trigger books (section 5): ZN-TRIG.
