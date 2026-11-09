# DS3_ZONES_EXHAUST - T-ZONES-EXHAUST (2026-11-09 17:29Z)

STATUS: PRE-PROOF, post-hoc, Shadow only, no PASS claims. FIRST-ORDER SCREEN ONLY unless the stage column says EXACT (exact engine rows are queued with SZ-CORE; none labelled EXACT here yet). Base S1b-COMB (live D7 v1.5 state cut, Q1-A, HALF D20 + OTE-62 B73 D30 in the base), carry week dropped from means only, maxDD/worst-20/Ulcer on all weeks, windows as of 2026-11-09, trade lists end 2026-10-30. Zone sources: 1-s state arrays (levels causal at the signal bar; volume = traded prints), see ZN_API.md. Held-out live week = frozen live file only; the 92 live cuts and the v1.5 night cuts are NOT used.

Grid screened: 347553 unique cells (family-level + per-level-type), 235159 with a placebo null (down-sizing), family max-stat over all of them; screen passers (L6M and PRE cut > 0, >= 20 trades changed): 53705.

## Reference rows (first-order, stack)

| ref | mean $/wk L6M | maxDD L6M | maxDD PRE | maxDD X' | maxDD HOLD | worst-20 L6M | note |
|---|---|---|---|---|---|---|---|
| REF_LIVE | 22996 | 79907 | 140288 | 116941 | 99496 | 165224 | live layer (HALF D20 + OTE-62 B73 D30 as in the exact base) |
| REF_NOZONE_FO | 28114 | 91798 | 144258 | 126134 | 112018 | 166013 | live zone halves undone at chain_nz lots (first-order; labelled UP; exact no-zone row queued) |
| REF_S4A | published S4A layer | | | | | | see DS3_TH_S4_ZONES_S1B.md; exact rows from SZ-CORE queue |

## Family A - Prior structure (prior-day/week/month H/L/C, overnight/Asia/London/pre-market, IB 30/60 + extensions, opening ranges, yesterday VWAP, settlement, gaps)

A: the best equal-mean cell is a **skip** when the A ahead 60 pts hw2 fresh=t0 age<=5d (level set ALL) is within reach, scope london: stack maxDD cut 56/54/-28 % (L6M/PRE/X') at equal lots and 59/58/-19 % at equal mean, touching 23.2% of trades; label **LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY]**. It does not hold as a setting because X' maxDD gets worse by 28%; the random same-count placebo reaches it (p 0.12); the purged walk-forward of the picking procedure does not beat the live layer; the family max-stat over the whole zone set (p 1.00) is not cleared; levels shifted by +/-25 pts do as well (p_shift 0.33), so the cut is not level-specific. The live HALF D20 + OTE-62 B73 D30 layer stays ON.

Ranked by min(equal-mean cut L6M, PRE) among screen passers; top 15 (full grid in /mnt/l2/l2vast/_th_zn/grid_all.parquet).

| level | geometry | action | scope (book|session) | maxDD cut % L6M/HOLD/PRE/X' | maxDD $ cell|ref L6M/PRE | equal-mean cut % L6M/PRE/X' | worst-20 L6M cell|ref | d mean $/wk L6M | trades touched % | placebo p L6M/PRE (B400) | shift/day placebo p | own p | family p (max) | WF ok | live-week d$ | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | ahead 60 pts hw2 fresh=t0 age<=5d | skip | london | 56/-77/54/-28 | 35161|79907/63964|140288 | 59/58/-19 | 267396|165224 | 1877 | 23.2 | 0.00/0.12 | 0.33/0.02 | 0.15/1.00 | False | 585 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 60 pts hw10 fresh=t0 age<=5d | skip | london | 54/-73/55/-28 | 36359|79907/62667|140288 | 58/58/-19 | 252216|165224 | 1770 | 23.9 | 0.00/0.13 | 0.33/0.02 | 0.15/1.00 | False | 585 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 60 pts hw2 fresh=t0 age<=1d | skip | london | 56/-77/54/-34 | 35161|79907/63964|140288 | 59/58/-25 | 264047|165224 | 1743 | 22.9 | 0.00/0.13 | 0.33/0.02 | 0.11/1.00 | False | 585 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 60 pts hw10 fresh=t0 age<=1d | skip | london | 54/-73/55/-40 | 36359|79907/62667|140288 | 57/58/-31 | 248868|165224 | 1636 | 23.6 | 0.00/0.13 | 0.33/0.02 | 0.13/1.00 | False | 585 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 60 pts hw2 fresh=t0 | skip | london | 56/-75/54/-21 | 35161|79907/63964|140288 | 59/57/-13 | 262029|165224 | 1662 | 23.3 | 0.00/0.15 | 0.33/0.02 | 0.21/1.00 | False | 585 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 60 pts hw10 fresh=t0 | skip | london | 54/-70/55/-14 | 36359|79907/62667|140288 | 57/58/-7 | 246850|165224 | 1555 | 24.1 | 0.00/0.16 | 0.33/0.02 | 0.16/1.00 | False | 585 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 60 pts hw5 fresh=t0 age<=5d | skip | london | 56/-65/54/-22 | 35161|79907/63964|140288 | 59/57/-14 | 254328|165224 | 1511 | 23.6 | 0.00/0.15 | 0.33/0.02 | 0.18/1.00 | False | 585 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 60 pts hw5 fresh=t0 age<=1d | skip | london | 56/-65/54/-33 | 35161|79907/63964|140288 | 58/57/-25 | 250979|165224 | 1377 | 23.2 | 0.00/0.14 | 0.33/0.02 | 0.13/1.00 | False | 585 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 60 pts hw5 fresh=t0 | skip | london | 56/-63/54/-14 | 35161|79907/63964|140288 | 58/57/-8 | 248962|165224 | 1296 | 23.7 | 0.00/0.18 | 0.33/0.02 | 0.13/1.00 | False | 585 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 1 atr fresh=t1 age<=1d | skip | london | 52/-47/51/-21 | 38750|79907/68075|140288 | 56/56/-10 | 307992|165224 | 2629 | 23.6 | 0.00/0.35 | 0.33/0.02 | 0.25/1.00 | False | 6170 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 1 atr fresh=t1 age<=4h | skip | london | 52/-52/51/-18 | 38750|79907/69281|140288 | 56/56/-6 | 308939|165224 | 3020 | 23.2 | 0.00/0.36 | 0.33/0.02 | 0.34/1.00 | False | 6170 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 1 atr fresh=t1 age<=5d | skip | london | 52/-47/51/-24 | 38750|79907/69054|140288 | 56/55/-13 | 308642|165224 | 2655 | 23.6 | 0.00/0.37 | 0.33/0.02 | 0.39/1.00 | False | 6170 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 1 atr fresh=t1 | skip | london | 52/-47/51/-24 | 38750|79907/69054|140288 | 56/55/-13 | 307443|165224 | 2607 | 23.7 | 0.00/0.40 | 0.33/0.02 | 0.34/1.00 | False | 6170 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 1.5 atr fresh=t0 age<=1d | skip | london | 54/-67/51/-50 | 36908|79907/69132|140288 | 58/55/-38 | 270374|165224 | 2103 | 21.4 | 0.00/0.23 | 0.33/0.02 | 0.26/1.00 | False | 2570 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 1.5 atr fresh=t0 age<=5d | skip | london | 54/-67/51/-49 | 36908|79907/69132|140288 | 57/54/-37 | 273722|165224 | 2185 | 21.5 | 0.00/0.23 | 0.33/0.02 | 0.23/1.00 | False | 2570 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |

Label counts in the ledger: {'LEAD': 172}

## Family B - VWAP / volume-profile family (session/RTH VWAP and sigma bands, anchored VWAPs, developing/prior/composite POC VAH VAL, naked POCs, HVN/LVN)

B: the best equal-mean cell is a **skip** when the B ahead 0.25 atr hw10 age<=1h (level set ALL) is within reach, scope london: stack maxDD cut 42/57/-9 % (L6M/PRE/X') at equal lots and 49/63/5 % at equal mean, touching 20.9% of trades; label **LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY]**. It does not hold as a setting because X' maxDD gets worse by 9%; the purged walk-forward of the picking procedure does not beat the live layer; the family max-stat over the whole zone set (p 1.00) is not cleared; levels shifted by +/-25 pts do as well (p_shift 0.33), so the cut is not level-specific. The live HALF D20 + OTE-62 B73 D30 layer stays ON.

Ranked by min(equal-mean cut L6M, PRE) among screen passers; top 15 (full grid in /mnt/l2/l2vast/_th_zn/grid_all.parquet).

| level | geometry | action | scope (book|session) | maxDD cut % L6M/HOLD/PRE/X' | maxDD $ cell|ref L6M/PRE | equal-mean cut % L6M/PRE/X' | worst-20 L6M cell|ref | d mean $/wk L6M | trades touched % | placebo p L6M/PRE (B400) | shift/day placebo p | own p | family p (max) | WF ok | live-week d$ | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | ahead 0.25 atr hw10 age<=1h | skip | london | 42/-100/57/-9 | 46497|79907/60378|140288 | 49/63/5 | 231738|165224 | 3488 | 20.9 | 0.03/0.03 | 0.33/0.07 | 0.07/1.00 | False | 3715 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 15 pts hw10 age<=1h | skip | london | 40/-104/52/-16 | 47696|79907/67838|140288 | 49/59/1 | 247269|165224 | 4310 | 24.6 | 0.11/0.51 | 0.33/0.10 | 0.52/1.00 | False | 4305 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 0.25 atr hw10 fresh=t1 age<=1d | skip | london | 40/-108/60/-4 | 47696|79907/56199|140288 | 48/65/10 | 241134|165224 | 3580 | 21.2 | 0.03/0.00 | 0.33/0.07 | 0.05/1.00 | False | 4370 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 15 pts hw10 fresh=t1 age<=1d | skip | london | 39/-109/57/-18 | 48895|79907/60870|140288 | 48/63/-1 | 252020|165224 | 4216 | 24.8 | 0.11/0.15 | 0.33/0.13 | 0.18/1.00 | False | 4960 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 0.25 atr hw10 fresh=t0 age<=1d | skip | london | 40/-108/60/-11 | 47696|79907/56199|140288 | 48/65/3 | 233844|165224 | 3267 | 21.2 | 0.05/0.00 | 0.33/0.10 | 0.05/1.00 | False | 3715 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 15 pts hw10 fresh=t0 age<=1d | skip | london | 39/-109/56/-18 | 48895|79907/62290|140288 | 48/62/-1 | 249251|165224 | 4084 | 24.8 | 0.10/0.19 | 0.33/0.20 | 0.23/1.00 | False | 4305 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 0.25 atr hw10 fresh=t1 | skip | london | 40/-113/60/-3 | 47696|79907/55621|140288 | 47/65/9 | 228696|165224 | 3116 | 21.4 | 0.05/0.00 | 0.33/0.05 | 0.11/1.00 | False | 4370 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 0.25 atr hw10 fresh=t1 age<=5d | skip | london | 40/-113/60/-4 | 47696|79907/55621|140288 | 47/65/8 | 228696|165224 | 3054 | 21.4 | 0.06/0.00 | 0.33/0.05 | 0.08/1.00 | False | 4370 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 15 pts hw10 fresh=t1 | skip | london | 39/-116/57/-17 | 48895|79907/60870|140288 | 47/62/-1 | 240877|165224 | 3736 | 24.9 | 0.15/0.16 | 0.33/0.07 | 0.15/1.00 | False | 4960 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 15 pts hw10 fresh=t1 age<=5d | skip | london | 39/-116/57/-18 | 48895|79907/60870|140288 | 47/62/-3 | 240877|165224 | 3674 | 24.9 | 0.11/0.14 | 0.33/0.18 | 0.20/1.00 | False | 4960 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 0.25 atr hw10 fresh=t0 | skip | london | 40/-113/60/-10 | 47696|79907/55621|140288 | 47/65/2 | 221406|165224 | 2930 | 21.3 | 0.05/0.00 | 0.33/0.08 | 0.02/1.00 | False | 3715 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 0.25 atr hw10 fresh=t0 age<=5d | skip | london | 40/-113/60/-11 | 47696|79907/55621|140288 | 47/65/1 | 221406|165224 | 2898 | 21.3 | 0.06/0.00 | 0.33/0.07 | 0.05/1.00 | False | 3715 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 15 pts hw10 fresh=t0 | skip | london | 39/-116/56/-17 | 48895|79907/62290|140288 | 47/61/-2 | 236814|165224 | 3523 | 24.9 | 0.14/0.19 | 0.33/0.15 | 0.18/1.00 | False | 4305 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 15 pts hw10 fresh=t0 age<=5d | skip | london | 39/-116/56/-18 | 48895|79907/62290|140288 | 46/61/-3 | 236814|165224 | 3491 | 24.9 | 0.16/0.18 | 0.33/0.11 | 0.25/1.00 | False | 4305 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | ahead 30 pts hw2 age<=1h | skip | london | 35/-96/57/-15 | 51654|79907/60102|140288 | 46/64/4 | 245651|165224 | 4879 | 26.9 | 0.30/0.23 | 0.33/0.33 | 0.34/1.00 | False | 11005 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |

Label counts in the ledger: {'LEAD': 172}

## Family C - Swing / market structure

C: the best equal-mean cell is a **skip** when the C nan nan pts fresh=nan age<=nan [nan] (level set nan) is within reach, scope ALL: stack maxDD cut 63/63/65 % (L6M/PRE/X') at equal lots and 59/59/61 % at equal mean, touching nan% of trades; label **CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF**. It does not hold as a setting because the family max-stat over the whole zone set (p 1.00) is not cleared. The live HALF D20 + OTE-62 B73 D30 layer stays ON.

Ranked by min(equal-mean cut L6M, PRE) among screen passers; top 15 (full grid in /mnt/l2/l2vast/_th_zn/grid_all.parquet).

| level | geometry | action | scope (book|session) | maxDD cut % L6M/HOLD/PRE/X' | maxDD $ cell|ref L6M/PRE | equal-mean cut % L6M/PRE/X' | worst-20 L6M cell|ref | d mean $/wk L6M | trades touched % | placebo p L6M/PRE (B400) | shift/day placebo p | own p | family p (max) | WF ok | live-week d$ | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| nan | nan  pts fresh=nan age<=nan [nan] | skip | ALL | 63/33/63/65 | 29680|79907/51496|140288 | 59/59/61 | 187323|165224 | -2224 |  | / | /0.05 | 0.03/1.00 | True | -81065 | S1 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| nan | nan  pts fresh=nan age<=nan [nan] | skip | ALL | 68/-30/62/54 | 25839|79907/52879|140288 | 63/57/48 | 209107|165224 | -2488 |  | / | /0.17 | 0.16/1.00 | True | -91315 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | nan  pts fresh=nan age<=nan [nan] | skip | ALL | 49/-6/51/31 | 40759|79907/68648|140288 | 57/58/41 | 284901|165224 | 4333 |  | / | / | 0.06/1.00 | True | 14410 | S1 | CANDIDATE (own-p only; family p 1.00) PRE-PROOF |
| nan | nan  pts fresh=nan age<=nan [nan] | skip | ALL | 56/43/54/56 | 35508|79907/63885|140288 | 57/56/58 | 251349|165224 | 725 |  | / | /0.02 | 0.07/1.00 | True | -65500 | S1 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| nan | nan  pts fresh=nan age<=nan [nan] | skip | ALL | 66/4/60/67 | 27176|79907/55530|140288 | 62/55/63 | 229231|165224 | -2471 |  | / | /0.17 | 0.21/1.00 | True | -87550 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | nan  pts fresh=nan age<=nan [nan] | skip | ALL | 56/49/54/48 | 35508|79907/63885|140288 | 56/55/48 | 245014|165224 | 287 |  | / | /0.02 | 0.03/1.00 | True | -66905 | S1 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| nan | nan  pts fresh=nan age<=nan [nan] | skip | ALL | 69/7/53/42 | 24730|79907/66594|140288 | 71/55/45 | 264980|165224 | 1098 |  | / | / | 0.33/1.00 | True | -89055 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | nan  pts fresh=nan age<=nan [nan] | skip | ALL | 65/-37/61/55 | 28103|79907/55358|140288 | 60/55/48 | 214784|165224 | -2798 |  | / | /0.17 | 0.19/1.00 | True | -86520 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | nan  pts fresh=nan age<=nan [nan] | skip | ALL | 66/6/59/67 | 27176|79907/57347|140288 | 62/54/63 | 230121|165224 | -2179 |  | / | /0.20 | 0.19/1.00 | True | -87550 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | nan  pts fresh=nan age<=nan [nan] | skip | ALL | 65/-37/61/57 | 28103|79907/55358|140288 | 59/54/50 | 199752|165224 | -2974 |  | / | /0.07 | 0.07/1.00 | True | -93030 | S1 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| nan | nan  pts fresh=nan age<=nan [nan] | skip | ALL | 69/4/53/42 | 24730|79907/66594|140288 | 70/54/44 | 254593|165224 | 683 |  | / | / | 0.30/1.00 | True | -89055 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | nan  pts fresh=nan age<=nan [nan] | skip | ALL | 55/15/55/50 | 36163|79907/63487|140288 | 52/52/48 | 226890|165224 | -1034 |  | / | /0.29 | 0.38/1.00 | True | -92865 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | nan  pts fresh=nan age<=nan [nan] | skip | ALL | 66/7/56/48 | 27549|79907/61881|140288 | 63/52/44 | 244467|165224 | -1808 |  | / | / | 0.08/1.00 | True | -83110 | S1 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| nan | nan  pts fresh=nan age<=nan [nan] | quarter | ALL | 62/49/62/53 | 30349|79907/53408|140288 | 52/52/41 | 156186|165224 | -4383 |  | / | / | 0.01/1.00 | True | -39058 | S1 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| nan | nan  pts fresh=nan age<=nan [nan] | skip | ALL | 55/17/44/47 | 36213|79907/79213|140288 | 61/51/54 | 262110|165224 | 3821 |  | / | /0.10 | 0.12/1.00 | True | -67320 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |

Label counts in the ledger: {'NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD]': 543, 'CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK': 195, 'CANDIDATE (own-p only; family p 1.00)': 40, 'LEAD': 35, 'UP (report, never promoted)': 15, 'NOT-LEVEL-SPECIFIC (shifted levels do as well) [was CANDIDATE]': 12, 'SCOPE-EFFECT [was LEAD]': 8, 'SCOPE-EFFECT [was CANDIDATE]': 3}

## Family D - Moving-average / band levels

D: the best equal-mean cell is a **skip** when the D nan nan pts fresh=nan age<=nan [nan] (level set nan) is within reach, scope ALL: stack maxDD cut 57/53/47 % (L6M/PRE/X') at equal lots and 55/51/44 % at equal mean, touching nan% of trades; label **NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD]**. It does not hold as a setting because the family max-stat over the whole zone set (p 1.00) is not cleared. The live HALF D20 + OTE-62 B73 D30 layer stays ON.

Ranked by min(equal-mean cut L6M, PRE) among screen passers; top 15 (full grid in /mnt/l2/l2vast/_th_zn/grid_all.parquet).

| level | geometry | action | scope (book|session) | maxDD cut % L6M/HOLD/PRE/X' | maxDD $ cell|ref L6M/PRE | equal-mean cut % L6M/PRE/X' | worst-20 L6M cell|ref | d mean $/wk L6M | trades touched % | placebo p L6M/PRE (B400) | shift/day placebo p | own p | family p (max) | WF ok | live-week d$ | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| nan | nan  pts fresh=nan age<=nan [nan] | skip | ALL | 57/50/53/47 | 34156|79907/65704|140288 | 55/51/44 | 241023|165224 | -1028 |  | / | /0.37 | 0.40/1.00 | True | -75270 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | nan  pts fresh=nan age<=nan [nan] | skip | ALL | 50/33/47/46 | 40204|79907/74992|140288 | 49/46/46 | 181612|165224 | -117 |  | / | /0.05 | 0.03/1.00 | True | -41425 | S1 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| nan | nan  pts fresh=nan age<=nan [nan] | skip | ALL | 47/-38/49/38 | 42040|79907/72131|140288 | 46/47/37 | 178621|165224 | -655 |  | / | / | 0.59/1.00 | True | 4220 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | nan  pts fresh=nan age<=nan [nan] | skip | ALL | 59/25/40/34 | 32939|79907/83701|140288 | 62/45/40 | 247609|165224 | 2163 |  | / | /0.20 | 0.23/1.00 | True | -39435 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | nan  pts fresh=nan age<=nan [nan] | skip | ALL | 45/-45/44/27 | 44341|79907/78209|140288 | 46/45/29 | 166595|165224 | 430 |  | / | / | 0.64/1.00 | True | -5710 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | nan  pts fresh=nan age<=nan [nan] | skip | ALL | 57/36/41/35 | 34255|79907/82801|140288 | 60/45/39 | 224829|165224 | 1655 |  | / | /0.24 | 0.21/1.00 | True | -46135 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | nan  pts fresh=nan age<=nan [nan] | skip | ALL | 34/-26/43/32 | 52561|79907/80437|140288 | 45/52/43 | 230631|165224 | 4269 |  | / | /0.22 | 0.16/1.00 | True | -9925 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | nan  pts fresh=nan age<=nan [nan] | skip | ALL | 57/22/44/52 | 34684|79907/78583|140288 | 56/44/52 | 178507|165224 | -96 |  | / | /0.05 | 0.08/1.00 | True | -41385 | S1 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| nan | nan  pts fresh=nan age<=nan [nan] | skip | ALL | 57/33/39/34 | 34255|79907/85326|140288 | 60/44/38 | 217339|165224 | 1802 |  | / | /0.07 | 0.10/1.00 | True | -50875 | S1 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| nan | nan  pts fresh=nan age<=nan [nan] | skip | ALL | 60/22/43/54 | 31817|79907/79922|140288 | 60/43/54 | 206042|165224 | 40 |  | / | /0.05 | 0.17/1.00 | True | -56980 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | nan  pts fresh=nan age<=nan [nan] | skip | ALL | 40/4/41/34 | 48036|79907/82657|140288 | 43/44/37 | 184467|165224 | 1118 |  | / | / | 0.75/1.00 | True | -4645 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | nan  pts fresh=nan age<=nan [nan] | skip | ALL | 46/-60/48/39 | 43230|79907/72270|140288 | 42/45/35 | 161578|165224 | -1684 |  | / | / | 0.37/1.00 | True | 14180 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | nan  pts fresh=nan age<=nan [nan] | quarter | ALL | 57/9/46/46 | 34736|79907/76381|140288 | 54/42/43 | 180818|165224 | -1358 |  | / | /0.02 | 0.03/1.00 | True | -48740 | S1 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| nan | nan  pts fresh=nan age<=nan [nan] | skip | ALL | 39/-38/37/42 | 48704|79907/88956|140288 | 44/42/47 | 218241|165224 | 1940 |  | / | /0.39 | 0.69/1.00 | True | 5100 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | nan  pts fresh=nan age<=nan [nan] | skip | ALL | 57/20/48/51 | 33966|79907/72585|140288 | 52/42/44 | 172999|165224 | -2546 |  | / | /0.02 | 0.03/1.00 | True | -66750 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was CANDIDATE] |

Label counts in the ledger: {'NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD]': 635, 'CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK': 86, 'LEAD': 60, 'CANDIDATE (own-p only; family p 1.00)': 18, 'NOT-LEVEL-SPECIFIC (shifted levels do as well) [was CANDIDATE]': 17, 'UP (report, never promoted)': 15, 'no': 2, 'SCOPE-EFFECT [was CANDIDATE]': 1, 'SCOPE-EFFECT [was LEAD]': 1}

## Family E - Round numbers / grid

E: the best equal-mean cell is a **skip** when the E nan nan pts fresh=nan age<=nan [nan] (level set nan) is within reach, scope ALL: stack maxDD cut 45/51/21 % (L6M/PRE/X') at equal lots and 52/56/30 % at equal mean, touching nan% of trades; label **NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD]**. It does not hold as a setting because the family max-stat over the whole zone set (p 1.00) is not cleared. The live HALF D20 + OTE-62 B73 D30 layer stays ON.

Ranked by min(equal-mean cut L6M, PRE) among screen passers; top 15 (full grid in /mnt/l2/l2vast/_th_zn/grid_all.parquet).

| level | geometry | action | scope (book|session) | maxDD cut % L6M/HOLD/PRE/X' | maxDD $ cell|ref L6M/PRE | equal-mean cut % L6M/PRE/X' | worst-20 L6M cell|ref | d mean $/wk L6M | trades touched % | placebo p L6M/PRE (B400) | shift/day placebo p | own p | family p (max) | WF ok | live-week d$ | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| nan | nan  pts fresh=nan age<=nan [nan] | skip | ALL | 45/-59/51/21 | 43582|79907/69372|140288 | 52/56/30 | 267197|165224 | 3431 |  | / | /0.12 | 0.28/1.00 | True | -6525 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | nan  pts fresh=nan age<=nan [nan] | skip | ALL | 45/-72/52/25 | 43582|79907/67756|140288 | 51/57/32 | 270547|165224 | 3047 |  | / | /0.51 | 0.42/1.00 | True | -12570 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | nan  pts fresh=nan age<=nan [nan] | skip | ALL | 44/-63/50/22 | 44577|79907/70213|140288 | 50/55/30 | 259376|165224 | 2952 |  | / | /0.17 | 0.22/1.00 | True | -8270 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | nan  pts fresh=nan age<=nan [nan] | skip | ALL | 44/-60/42/19 | 44728|79907/82033|140288 | 51/49/29 | 268894|165224 | 3820 |  | / | /0.98 | 0.82/1.00 | True | -11785 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | nan  pts fresh=nan age<=nan [nan] | skip | ALL | 43/-64/42/17 | 45926|79907/81905|140288 | 49/49/27 | 264079|165224 | 3658 |  | / | / | 0.92/1.00 | True | -11785 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | nan  pts fresh=nan age<=nan [nan] | skip | ALL | 42/-53/49/32 | 45980|79907/71517|140288 | 48/54/38 | 259551|165224 | 2885 |  | / | /0.34 | 0.36/1.00 | True | -12530 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | nan  pts fresh=nan age<=nan [nan] | skip | ALL | 43/-47/41/4 | 45810|79907/83073|140288 | 49/47/15 | 230793|165224 | 2695 |  | / | / | 0.81/1.00 | True | -10660 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | nan  pts fresh=nan age<=nan [nan] | skip | ALL | 38/-38/57/7 | 49928|79907/60887|140288 | 47/63/21 | 217253|165224 | 3590 |  | / | / | 0.42/1.00 | True | -9980 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | nan  pts fresh=nan age<=nan [nan] | skip | ALL | 49/-63/53/16 | 40475|79907/65921|140288 | 46/50/10 | 171048|165224 | -1866 |  | / | / | 0.74/1.00 | True | -640 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | nan  pts fresh=nan age<=nan [nan] | skip | ALL | 41/-57/39/26 | 47179|79907/84946|140288 | 47/45/33 | 273204|165224 | 2850 |  | / | /0.90 | 0.86/1.00 | True | -12530 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | nan  pts fresh=nan age<=nan [nan] | skip | ALL | 41/-55/48/1 | 47331|79907/73229|140288 | 45/51/8 | 203617|165224 | 1622 |  | / | / | 0.80/1.00 | True | -3335 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | nan  pts fresh=nan age<=nan [nan] | skip | ALL | 39/-82/54/10 | 48378|79907/64775|140288 | 44/58/18 | 262139|165224 | 2399 |  | / | / | 0.41/1.00 | True | -10130 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | nan  pts fresh=nan age<=nan [nan] | skip | ALL | 49/47/48/17 | 40972|79907/72663|140288 | 44/43/9 | 208629|165224 | -2004 |  | / | / | 0.11/1.00 | True | -49890 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |
| nan | nan  pts fresh=nan age<=nan [nan] | quarter | ALL | 61/37/62/57 | 31141|79907/53687|140288 | 43/44/37 | 143247|165224 | -6711 |  | / | /0.02 | 0.02/1.00 | True | -61140 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was CANDIDATE] |
| nan | nan  pts fresh=nan age<=nan [nan] | skip | ALL | 39/-50/48/3 | 48351|79907/73008|140288 | 43/51/8 | 192279|165224 | 1344 |  | / | / | 0.56/1.00 | True | -15715 | S1 | NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD] |

Label counts in the ledger: {'NOT-LEVEL-SPECIFIC (shifted levels do as well) [was LEAD]': 519, 'NOT-LEVEL-SPECIFIC (shifted levels do as well) [was CANDIDATE]': 29, 'SCOPE-EFFECT [was LEAD]': 22, 'CANDIDATE (own-p only; family p 1.00)': 16, 'UP (report, never promoted)': 15, 'SCOPE-EFFECT [was CANDIDATE]': 12, 'CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK': 11, 'LEAD': 10}

## Family F - Book-derived

F: the best equal-mean cell is a **skip** when the F AH:A0.5|s-1|any|any (level set nan) is within reach, scope ALL: stack maxDD cut 54/54/23 % (L6M/PRE/X') at equal lots and 49/49/13 % at equal mean, touching 14.9% of trades; label **CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF**. It does not hold as a setting because the family max-stat over the whole zone set (p 1.00) is not cleared. The live HALF D20 + OTE-62 B73 D30 layer stays ON.

Ranked by min(equal-mean cut L6M, PRE) among screen passers; top 15 (full grid in /mnt/l2/l2vast/_th_zn/grid_all.parquet).

| level | geometry | action | scope (book|session) | maxDD cut % L6M/HOLD/PRE/X' | maxDD $ cell|ref L6M/PRE | equal-mean cut % L6M/PRE/X' | worst-20 L6M cell|ref | d mean $/wk L6M | trades touched % | placebo p L6M/PRE (B400) | shift/day placebo p | own p | family p (max) | WF ok | live-week d$ | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| nan | AH:A0.5|s-1|any|any | skip | ALL | 54/25/54/23 | 36558|79907/64123|140288 | 49/49/13 | 152805|165224 | -2436 | 14.9 | / | / | 0.04/1.00 | True | -72315 | S1 first-order SCREEN ONLY | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| nan | AH:A0.5|s-1|any|any | skip | ALL | 54/25/54/23 | 36558|79907/64123|140288 | 49/49/13 | 152805|165224 | -2436 | 14.9 | / | / | 0.04/1.00 | True | -72315 | S1 first-order SCREEN ONLY | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| nan | AH:D20|s-1|any|any | skip | ALL | 54/27/54/34 | 36558|79907/64142|140288 | 45/45/21 | 131856|165224 | -3651 | 15.6 | / | / | 0.10/1.00 | True | -72315 | S1 first-order SCREEN ONLY | LEAD PRE-PROOF |
| nan | AH:D10|s-1|any|any | skip | ALL | 54/27/54/34 | 36558|79907/64142|140288 | 45/45/21 | 131856|165224 | -3651 | 15.6 | / | / | 0.06/1.00 | True | -72315 | S1 first-order SCREEN ONLY | LEAD PRE-PROOF |
| nan | AH:D10|s-1|any|any | skip | ALL | 54/27/54/34 | 36558|79907/64142|140288 | 45/45/21 | 131856|165224 | -3651 | 15.6 | / | / | 0.06/1.00 | True | -72315 | S1 first-order SCREEN ONLY | LEAD PRE-PROOF |
| nan | AH:D20|s-1|any|any | skip | ALL | 54/27/54/34 | 36558|79907/64142|140288 | 45/45/21 | 131856|165224 | -3651 | 15.6 | / | / | 0.10/1.00 | True | -72315 | S1 first-order SCREEN ONLY | LEAD PRE-PROOF |
| nan | AH:A1|s-1|any|any | skip | ALL | 54/25/55/31 | 36558|79907/63361|140288 | 45/46/18 | 131856|165224 | -3651 | 15.5 | / | / | 0.06/1.00 | True | -72315 | S1 first-order SCREEN ONLY | LEAD PRE-PROOF |
| nan | AH:A1|s-1|any|any | skip | ALL | 54/25/55/31 | 36558|79907/63361|140288 | 45/46/18 | 131856|165224 | -3651 | 15.5 | / | / | 0.06/1.00 | True | -72315 | S1 first-order SCREEN ONLY | LEAD PRE-PROOF |
| nan | BH-absent:B5 | quarter | ALL | 46/17/45/14 | 42844|79907/76667|140288 | 46/45/14 | 239276|165224 | -3 | 58.9 | / | / | 0.08/1.00 | True | -28936 | S1 first-order SCREEN ONLY | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| nan | BH-absent:B5 | quarter | ALL | 46/17/45/14 | 42844|79907/76667|140288 | 46/45/14 | 239276|165224 | -3 | 58.9 | / | / | 0.08/1.00 | True | -28936 | S1 first-order SCREEN ONLY | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| nan | AH:A0.5|s-1|any|any | quarter | ALL | 57/17/56/29 | 34440|79907/61654|140288 | 46/45/12 | 179099|165224 | -4406 | 64.8 | / | / | 0.02/1.00 | True | -41344 | S1 first-order SCREEN ONLY | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| nan | AH:A0.5|s-1|any|any | quarter | ALL | 57/17/56/29 | 34440|79907/61654|140288 | 46/45/12 | 179099|165224 | -4406 | 64.8 | / | / | 0.02/1.00 | True | -41344 | S1 first-order SCREEN ONLY | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| nan | AH:D90|s-1|any|any | skip | ALL | 54/27/54/34 | 36558|79907/64142|140288 | 45/45/20 | 131856|165224 | -3843 | 15.7 | / | / | 0.12/1.00 | True | -72315 | S1 first-order SCREEN ONLY | LEAD PRE-PROOF |
| nan | AH:D90|s-1|any|any | skip | ALL | 54/27/54/34 | 36558|79907/64142|140288 | 45/45/20 | 131856|165224 | -3843 | 15.7 | / | / | 0.12/1.00 | True | -72315 | S1 first-order SCREEN ONLY | LEAD PRE-PROOF |
| nan | AH:D5|s-1|any|any | quarter | ALL | 57/31/60/4 | 34440|79907/55776|140288 | 44/49/-23 | 171184|165224 | -5011 | 67.1 | / | / | 0.01/1.00 | True | -45126 | S1 first-order SCREEN ONLY | SCOPE-EFFECT (no equal-mean gain over the same action on every trade of ALL) PRE-PROOF |

Label counts in the ledger: {'no': 50042, 'LEAD': 5762, 'UP (report, never promoted)': 2980, 'SCOPE-EFFECT (no equal-mean gain over the same action on every trade of ALL)': 1590, 'SCOPE-EFFECT (no equal-mean gain over the same action on every trade of s:nyam)': 522, 'SCOPE-EFFECT (no equal-mean gain over the same action on every trade of s:london)': 464, 'SCOPE-EFFECT (no equal-mean gain over the same action on every trade of bs:SM:london)': 452, 'SCOPE-EFFECT (no equal-mean gain over the same action on every trade of bs:PE:nyam)': 438, 'SCOPE-EFFECT (no equal-mean gain over the same action on every trade of b:PE)': 422, 'SCOPE-EFFECT (no equal-mean gain over the same action on every trade of bs:PE:london)': 310, 'SCOPE-EFFECT (no equal-mean gain over the same action on every trade of b:MV)': 282, 'SCOPE-EFFECT (no equal-mean gain over the same action on every trade of bs:MV:london)': 278, 'SCOPE-EFFECT (no equal-mean gain over the same action on every trade of b:KB)': 256, 'CANDIDATE (own-p only; family p 1.00)': 202, 'CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK': 182, 'SCOPE-EFFECT (no equal-mean gain over the same action on every trade of bs:KB:london)': 182, 'SCOPE-EFFECT (no equal-mean gain over the same action on every trade of bs:KB:nypm)': 142, 'SCOPE-EFFECT (no equal-mean gain over the same action on every trade of s:nypm)': 142, 'SCOPE-EFFECT (no equal-mean gain over the same action on every trade of b:SM)': 74, 'SCOPE-EFFECT (no equal-mean gain over the same action on every trade of bs:KB:asia)': 36, 'SCOPE-EFFECT (no equal-mean gain over the same action on every trade of bs:MV:nyam)': 4, 'SCOPE-EFFECT (no equal-mean gain over the same action on every trade of bs:KB:nyam)': 2, 'SCOPE-EFFECT (no equal-mean gain over the same action on every trade of bs:SM:asia)': 2}

## Family G - Event / time levels (09:30 / 10:00 / 11:30 / 15:00 prints, settlement, first-5-min range)

G: the best equal-mean cell is a **skip** when the G behind 90 pts age<=4h (level set ALL) is within reach, scope ALL: stack maxDD cut 14/18/30 % (L6M/PRE/X') at equal lots and 21/25/36 % at equal mean, touching 27.2% of trades; label **LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY]**. It does not hold as a setting because the random same-count placebo reaches it (p 0.36); the family max-stat over the whole zone set (p 1.00) is not cleared; levels shifted by +/-25 pts do as well (p_shift 0.33), so the cut is not level-specific. The live HALF D20 + OTE-62 B73 D30 layer stays ON.

Ranked by min(equal-mean cut L6M, PRE) among screen passers; top 15 (full grid in /mnt/l2/l2vast/_th_zn/grid_all.parquet).

| level | geometry | action | scope (book|session) | maxDD cut % L6M/HOLD/PRE/X' | maxDD $ cell|ref L6M/PRE | equal-mean cut % L6M/PRE/X' | worst-20 L6M cell|ref | d mean $/wk L6M | trades touched % | placebo p L6M/PRE (B400) | shift/day placebo p | own p | family p (max) | WF ok | live-week d$ | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | behind 90 pts age<=4h | skip | ALL | 14/13/18/30 | 68850|79907/115341|140288 | 21/25/36 | 241851|165224 | 2469 | 27.2 | 0.36/0.22 | 0.33/0.38 | 0.41/1.00 | True | -11225 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | behind 90 pts hw5 age<=4h | skip | ALL | 12/14/19/28 | 70048|79907/113530|140288 | 21/27/35 | 249923|165224 | 2886 | 27.6 | 0.46/0.19 | 0.33/0.46 | 0.51/1.00 | True | -10510 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | behind 90 pts hw10 age<=4h | skip | ALL | 12/20/18/33 | 70048|79907/115161|140288 | 21/26/40 | 250281|165224 | 2754 | 28.0 | 0.45/0.31 | 0.33/0.49 | 0.52/1.00 | True | -10510 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | behind 90 pts hw2 age<=4h | skip | ALL | 12/13/19/28 | 70048|79907/113530|140288 | 20/26/34 | 242515|165224 | 2445 | 27.3 | 0.46/0.19 | 0.33/0.49 | 0.49/1.00 | True | -11225 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | behind 90 pts age<=1d | skip | ALL | 12/14/19/27 | 70048|79907/113229|140288 | 20/26/33 | 239094|165224 | 2311 | 27.6 | 0.45/0.16 | 0.33/0.41 | 0.41/1.00 | True | -11225 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | behind 90 pts hw5 age<=1d | skip | ALL | 11/14/21/25 | 71247|79907/111418|140288 | 19/28/32 | 248452|165224 | 2728 | 28.1 | 0.55/0.11 | 0.33/0.66 | 0.64/1.00 | True | -10510 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | behind 90 pts hw10 age<=1d | skip | ALL | 11/20/19/30 | 71247|79907/113050|140288 | 19/27/36 | 248810|165224 | 2548 | 28.5 | 0.56/0.24 | 0.33/0.56 | 0.48/1.00 | True | -10510 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | behind 90 pts hw2 age<=1d | skip | ALL | 11/14/21/25 | 71247|79907/111418|140288 | 18/27/31 | 239757|165224 | 2287 | 27.8 | 0.50/0.11 | 0.33/0.51 | 0.49/1.00 | True | -11225 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | behind 1.5 atr hw5 age<=4h | skip | ALL | 12/13/11/35 | 70005|79907/124684|140288 | 19/18/40 | 238210|165224 | 1945 | 26.2 | 0.43/0.75 | 0.33/0.49 | 0.66/1.00 | True | -10885 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | behind 1.5 atr hw10 age<=4h | skip | ALL | 11/21/12/34 | 71204|79907/124037|140288 | 17/18/39 | 241257|165224 | 1905 | 26.9 | 0.50/0.69 | 0.33/0.61 | 0.82/1.00 | True | -13285 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | behind 90 pts hw5 age<=4h | skip | PE | 6/16/18/23 | 75075|79907/114682|140288 | 17/28/32 | 254649|165224 | 2904 | 5.3 | 0.83/0.13 | 0.67/0.84 | 0.84/1.00 | True | -3995 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | behind 90 pts hw10 age<=4h | skip | PE|nyam | 6/24/18/27 | 75075|79907/114682|140288 | 17/28/35 | 254649|165224 | 2904 | 5.3 | 0.84/0.12 | 0.67/0.90 | 0.87/1.00 | True | -3995 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | behind 90 pts hw10 age<=4h | skip | PE | 6/24/18/27 | 75075|79907/114682|140288 | 17/28/35 | 254649|165224 | 2904 | 5.3 | 0.87/0.11 | 0.67/0.87 | 0.87/1.00 | True | -3995 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | behind 90 pts hw5 age<=4h | skip | PE|nyam | 6/16/18/23 | 75075|79907/114682|140288 | 17/28/32 | 254649|165224 | 2904 | 5.3 | 0.86/0.11 | 0.67/0.79 | 0.84/1.00 | True | -3995 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |
| ALL | behind 1.5 atr hw5 age<=1d | skip | ALL | 11/13/13/35 | 71204|79907/122280|140288 | 17/18/39 | 234858|165224 | 1719 | 26.7 | 0.56/0.58 | 0.33/0.62 | 0.57/1.00 | True | -10300 | S1 first-order | LEAD PRE-PROOF [FIRST-ORDER SCREEN ONLY] |

Label counts in the ledger: {'LEAD': 51, 'CANDIDATE (own-p only; family p 1.00)': 5}

## Zone layer setting (standing rule: the layer stays ON; skip-all/off are reference rows only)

Cells labelled CANDIDATE in the merged ledgers: %d (all first-order screen, family p mostly 1.00 because the null is the max over the whole zone set of ~235k down-sizing cells). Until an EXACT row beats the live HALF D20 + OTE-62 B73 D30 layer on L6M, PRE, X' and HOLD with placebo/family/WF gates, the recommended setting per book x session is the live layer unchanged. Candidate additions are registered for exact runs in /mnt/l2/l2vast/_th_joint/layers/zone/topK.json (live layer always one of the five).

## Old-vs-new (ZONES-3 published cells) and base-change proof

Pending: published ZONES-3 / B73 cells are being re-scored on the S1b state base and compared with the published numbers (method of SZ_BASE_PROOF.md); table added in the next refresh.

## Not yet covered (other owners / next refresh)

- Families C (swing/structure), D (MA/band), E (round numbers), F (book-derived): ZN-STRUCT / ZN-BOOK ledgers merged here when present.
- Actions beyond skip/half/quarter/up (delay-until-through, re-targets, structure stop, 70/30 add, state-cut arm, cooldown): exact-engine only, top-5 per family, queued via SZ-CORE.
- Entry-trigger books (section 5): ZN-TRIG.
