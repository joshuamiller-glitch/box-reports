# ZN-BOOK - T-ZONES-EXHAUST family F (book-derived levels on the 1-s state base) - refreshed 2026-11-09 18:04Z

Base S1b-COMB (live D7 v1.5 state-cut lines, Q1-A, HALF D20 + OTE-62 B73 D30 inside the base), 21,135 trades 2023-04..2026-10-30; windows as of 2026-11-09; maxDD/worst-20/Ulcer on ALL weeks, carry week dropped from MEANS only. ROLL-EXCL applied (33 trades alive across contract rolls get weight 0 in every daily series via sz_core Base.rollw); FIRST-ORDER SCREEN ONLY (exact top-5 queued); PRE-PROOF; post-hoc; Shadow only; no PASS claims. Prereg: ZN_BOOK_PREREG.md (sha in DECISIONS.md). Features: code/th_zn/zn_book_lv.py (all from the raw mbp-10 1-s state arrays, rows <= the signal-second row; NT8 needs the chart L2/DOM series for the book levels: walls/iceberg/absorption/sweep/max-size/depth pivot are Level-2 quantities, not chart-OHLC).

**Cells scored: 32155** (35 level sets x geometry x action x scope pooled / book / session / book x session; identical flags deduplicated). Label counts: no 24880, LEAD 2952, SCOPE-EFFECT 2628, UP 1486, CANDIDATE 209.

**Reading guide.** The cut % columns are at EQUAL LOTS (the cell removes lots); the equal-mean columns rescale all lots by one factor so the L6M mean equals the Q1-A reference, then compare maxDD (the honest drawdown comparison). Every cell is compared to the SAME action applied to EVERY trade of its scope (group-wide baseline, columns gw_*; `gain_rk` = min equal-mean cut of the cell minus min equal-mean cut of the group-wide action): a level that only picks most of a weak book is labelled SCOPE-EFFECT, not a zone finding. p family = WY-style max-stat over ALL 32155 F cells (own = placebo p; family max in the table is over the whole F set, lf-max over the cell's level family only).

## 0. Reference rows (S1b-COMB, Q1-A live layer, no F zone)

| row | L6M maxDD | HOLD maxDD | PRE maxDD | X' maxDD | L6M mean $/wk | L6M worst-20 |
|---|---|---|---|---|---|---|
| live layer (S1b-COMB as is) | 79907 | 99496 | 140288 | 128944 | 21246 | 165224 |

## 1. Family F by level set (ranked by the minimum equal-mean cut over L6M/PRE/X', down-only cells with gain over the group-wide action > 0)

### wall - resting-size walls (size >= k x MedLevel in the top 10, persistence p s)

Cells 10031 (down-only 9587); LEAD/CANDIDATE 379; SCOPE-EFFECT 613. WF (purged monthly, 26-wk trailing, 7-d embargo, pick among all 9587 cells): house criterion cut 98.2% (degenerate: it picks near-zero-trade cells, mean 86 $/wk), with a >=85% mean-retention constraint cut 17.0% at mean 9514 vs ref 16547 $/wk (34 of 34 months picked a cell).

| level | geometry | action | scope | L6M maxDD cell/ref (cut%) | cut% HOLD/PRE/X' | equal-mean cut% L6M/PRE/X' | worst-20 L6M cell/ref | d mean $/wk L6M | touched % | placebo p L6M/PRE | p family own/max (lf-max) | WF | live wk d$ | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| wall_k3_p0 | BH-absent:B5 | quarter | s:london | 50126/79907 (37.3) | -24.8/47.8/30.8 | 33/44/26 | 190621/165224 | -1878 | 29.1 | 0.01/0.04 | 0.04/1.00 | ok | 134 | CANDIDATE (own-p only; family p 1.00) |
| wall_k3_p0 | BH-absent:B20 | quarter | s:london | 50126/79907 (37.3) | -18.8/47.8/30.8 | 33/44/26 | 190621/165224 | -1878 | 29.0 | 0.01/0.03 | 0.03/1.00 | ok | 134 | CANDIDATE (own-p only; family p 1.00) |
| wall_k3_p0 | BH-absent:B20 | half | s:london | 52897/79907 (33.8) | 1.0/38.4/25.6 | 32/36/23 | 197077/165224 | -873 | 29.0 | 0.01/0.04 | 0.04/1.00 | ok | -1372 | CANDIDATE (own-p only; family p 1.00) |
| wall_k3_p0 | BH-absent:B5 | half | s:london | 52897/79907 (33.8) | -2.6/40.1/25.6 | 32/38/23 | 197077/165224 | -873 | 29.1 | 0.01/0.02 | 0.02/1.00 | ok | -1372 | CANDIDATE (own-p only; family p 1.00) |
| wall_k3_p0 | BH-absent:B5 | skip | bs:PE:london | 53788/79907 (32.7) | -34.4/50.7/22.2 | 33/51/23 | 176830/165224 | 222 | 7.2 | 0.09/0.26 | 0.26/1.00 | ok | -4490 | LEAD |
| wall_k3_p0 | BH-absent:B20 | skip | bs:PE:london | 53788/79907 (32.7) | -26.0/50.7/22.2 | 33/51/23 | 176830/165224 | 222 | 7.2 | 0.05/0.26 | 0.26/1.00 | ok | -4490 | LEAD |
| wall_k3_p0 | BH-absent:B5 | quarter | b:PE | 42456/79907 (46.9) | 40.7/46.1/46.1 | 23/22/22 | 135455/165224 | -6803 | 22.4 | 0.05/0.25 | 0.25/1.00 | ok | -71183 | LEAD |
| wall_k3_p0 | BH-absent:B2 | half | ALL | 41696/79907 (47.8) | 49.8/43.0/52.9 | 27/21/34 | 131836/165224 | -6301 | 94.2 | 0.01/0.12 | 0.12/1.00 | ok | -38340 | LEAD |
| wall_k5_p0 | BH-absent:B20 | half | ALL | 38429/79907 (51.9) | 47.8/42.6/44.2 | 33/20/23 | 140518/165224 | -6135 | 97.0 | 0.01/0.16 | 0.16/1.00 | ok | -47489 | LEAD |
| wall_k5_p0 | BH-absent:B10 | half | ALL | 38429/79907 (51.9) | 47.8/42.6/44.2 | 33/20/23 | 140518/165224 | -6135 | 97.0 | 0.01/0.13 | 0.13/1.00 | ok | -47489 | LEAD |

*wall: "wall_k3_p0, quarter BH-absent:B5 on s:london" cuts L6M maxDD 37.3% (equal-mean 33% / PRE 44% / X' 26%) touching 29% of trades at -1878 $/wk mean change; placebo p 0.01/0.04, family p 1.00 (max over all F cells), WF holds, live week 134 $; label CANDIDATE (own-p only; family p 1.00).*

### ice - iceberg-refill levels

Cells 4505 (down-only 4152); LEAD/CANDIDATE 1017; SCOPE-EFFECT 728. WF (purged monthly, 26-wk trailing, 7-d embargo, pick among all 4152 cells): house criterion cut 43.1% (degenerate: it picks near-zero-trade cells, mean 2422 $/wk), with a >=85% mean-retention constraint cut -15.8% at mean 9306 vs ref 16547 $/wk (34 of 34 months picked a cell).

| level | geometry | action | scope | L6M maxDD cell/ref (cut%) | cut% HOLD/PRE/X' | equal-mean cut% L6M/PRE/X' | worst-20 L6M cell/ref | d mean $/wk L6M | touched % | placebo p L6M/PRE | p family own/max (lf-max) | WF | live wk d$ | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ice_w600_n1 | AH:D40/s-1/any/any | quarter | b:PE | 39738/79907 (50.3) | 18.2/51.0/51.7 | 35/36/37 | 148329/165224 | -5195 | 21.9 | 0.02/0.12 | 0.12/1.00 | no | -64405 | LEAD |
| ice_w600_n1 | AH:D20/s-1/any/any | quarter | b:PE | 39738/79907 (50.3) | 18.2/52.8/51.7 | 35/39/37 | 148329/165224 | -5195 | 21.9 | 0.02/0.05 | 0.05/1.00 | no | -64405 | LEAD |
| ice_w600_n1 | AH:A1/s-1/any/any | quarter | b:PE | 39738/79907 (50.3) | 17.1/51.0/51.7 | 35/36/37 | 148329/165224 | -5312 | 21.9 | 0.05/0.09 | 0.09/1.00 | no | -64405 | LEAD |
| ice_w600_n1 | AH:D10/s-1/any/any | quarter | b:PE | 39738/79907 (50.3) | 13.0/57.1/51.7 | 34/43/36 | 147482/165224 | -5394 | 21.9 | 0.01/0.01 | 0.01/1.00 | no | -64405 | LEAD |
| ice_w600_n1 | AH:A0.5/s-1/any/any | quarter | b:PE | 39738/79907 (50.3) | 20.7/48.5/63.4 | 35/33/52 | 149917/165224 | -5295 | 21.5 | 0.05/0.14 | 0.14/1.00 | no | -58398 | LEAD |
| ice_w600_n1 | AH:A0.5/s-1/any/any | quarter | s:london | 54636/79907 (31.6) | -10.9/43.1/27.8 | 35/46/32 | 211649/165224 | 1185 | 26.4 | 0.06/0.30 | 0.30/1.00 | no | 3873 | LEAD |
| ice_w600_n1 | AH:A0.5/s-1/any/any | skip | b:PE | 31400/79907 (60.7) | 13.4/57.9/68.7 | 35/31/48 | 91506/165224 | -8790 | 21.5 | 0.05/0.45 | 0.45/1.00 | no | -82360 | LEAD |
| ice_w600_n1 | AH:D5/s-1/any/any | quarter | b:PE | 39738/79907 (50.3) | 16.6/49.5/51.7 | 32/31/34 | 129638/165224 | -6092 | 21.8 | 0.03/0.08 | 0.08/1.00 | no | -58398 | LEAD |
| ice_w600_n1 | AH:D10/s-1/any/any | half | ALL | 43793/79907 (45.2) | 29.8/44.2/51.5 | 31/30/39 | 164984/165224 | -4546 | 85.3 | 0.02/0.07 | 0.07/1.00 | no | -40175 | LEAD |
| ice_w600_n1 | AH:D10/s-1/any/any | half | b:PE | 49103/79907 (38.6) | 25.0/36.5/36.1 | 31/29/29 | 185994/165224 | -2360 | 21.9 | 0.01/0.08 | 0.08/1.00 | no | -38611 | LEAD |

*ice: "ice_w600_n1, quarter AH:D40|s-1|any|any on b:PE" cuts L6M maxDD 50.3% (equal-mean 35% / PRE 36% / X' 37%) touching 22% of trades at -5195 $/wk mean change; placebo p 0.02/0.12, family p 1.00 (max over all F cells), WF fails, live week -64405 $; label LEAD.*

### abs - absorption levels (sold/bought into, held)

Cells 5333 (down-only 5084); LEAD/CANDIDATE 291; SCOPE-EFFECT 337. WF (purged monthly, 26-wk trailing, 7-d embargo, pick among all 5084 cells): house criterion cut 99.5% (degenerate: it picks near-zero-trade cells, mean 28 $/wk), with a >=85% mean-retention constraint cut 31.9% at mean 13555 vs ref 16547 $/wk (34 of 34 months picked a cell).

| level | geometry | action | scope | L6M maxDD cell/ref (cut%) | cut% HOLD/PRE/X' | equal-mean cut% L6M/PRE/X' | worst-20 L6M cell/ref | d mean $/wk L6M | touched % | placebo p L6M/PRE | p family own/max (lf-max) | WF | live wk d$ | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| abs_w300_v2 | BH-absent:B5 | quarter | s:london | 53719/79907 (32.8) | -15.1/47.8/31.9 | 28/44/27 | 180595/165224 | -1907 | 29.1 | 0.07/0.03 | 0.07/1.00 | ok | 3873 | CANDIDATE (own-p only; family p 1.00) |
| abs_w300_v2 | BH-absent:B20 | quarter | s:london | 56823/79907 (28.9) | -5.6/47.3/23.1 | 29/47/23 | 170204/165224 | -31 | 24.7 | 0.07/0.02 | 0.07/1.00 | ok | -1470 | CANDIDATE (own-p only; family p 1.00) |
| abs_w300_v2 | BH-absent:B5 | half | s:london | 55738/79907 (30.2) | 2.8/36.6/24.8 | 28/34/22 | 188238/165224 | -894 | 29.1 | 0.02/0.02 | 0.02/1.00 | ok | 1341 | CANDIDATE (own-p only; family p 1.00) |
| abs_w300_v2 | BH-absent:B5 | skip | s:london | 51886/79907 (35.1) | -42.0/55.5/25.9 | 30/52/20 | 189731/165224 | -1950 | 29.1 | 0.38/0.60 | 0.60/1.00 | ok | -1390 | LEAD |
| abs_w900_v4 | BH-absent:B20 | half | ALL | 41957/79907 (47.5) | 43.9/44.2/58.0 | 25/20/40 | 126665/165224 | -6609 | 97.8 | 0.01/0.09 | 0.09/1.00 | ok | -37680 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK |
| abs_w900_v2 | BH-absent:B20 | skip | s:london | 52471/79907 (34.3) | -42.0/52.9/29.4 | 25/47/20 | 182653/165224 | -3247 | 27.9 | 0.36/0.68 | 0.68/1.00 | ok | -4780 | LEAD |
| abs_w900_v2 | BH-absent:B10 | half | ALL | 41957/79907 (47.5) | 42.3/42.6/61.7 | 26/19/46 | 122302/165224 | -6472 | 92.8 | 0.02/0.13 | 0.13/1.00 | ok | -37680 | LEAD |
| abs_w300_v4 | BH-absent:B2 | half | ALL | 41957/79907 (47.5) | 43.9/43.3/43.3 | 25/19/19 | 131862/165224 | -6607 | 99.4 | 0.01/0.10 | 0.10/1.00 | ok | -37680 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK |
| abs_w300_v4 | BH-absent:B20 | quarter | s:london | 53719/79907 (32.8) | -19.1/47.8/20.4 | 31/47/19 | 163240/165224 | -527 | 31.1 | 0.08/0.04 | 0.08/1.00 | ok | 3873 | CANDIDATE (own-p only; family p 1.00) |
| abs_w900_v2 | BH-absent:B20 | half | s:london | 55292/79907 (30.8) | 1.2/39.2/22.8 | 27/35/18 | 175292/165224 | -1590 | 27.9 | 0.02/0.01 | 0.02/1.00 | ok | 66 | CANDIDATE (own-p only; family p 1.00) |

*abs: "abs_w300_v2, quarter BH-absent:B5 on s:london" cuts L6M maxDD 32.8% (equal-mean 28% / PRE 44% / X' 27%) touching 29% of trades at -1907 $/wk mean change; placebo p 0.07/0.03, family p 1.00 (max over all F cells), WF holds, live week 3873 $; label CANDIDATE (own-p only; family p 1.00).*

### swp - sweep levels (swept, now cleared)

Cells 5318 (down-only 5070); LEAD/CANDIDATE 827; SCOPE-EFFECT 467. WF (purged monthly, 26-wk trailing, 7-d embargo, pick among all 5070 cells): house criterion cut 52.8% (degenerate: it picks near-zero-trade cells, mean 6328 $/wk), with a >=85% mean-retention constraint cut 40.0% at mean 11745 vs ref 16547 $/wk (34 of 34 months picked a cell).

| level | geometry | action | scope | L6M maxDD cell/ref (cut%) | cut% HOLD/PRE/X' | equal-mean cut% L6M/PRE/X' | worst-20 L6M cell/ref | d mean $/wk L6M | touched % | placebo p L6M/PRE | p family own/max (lf-max) | WF | live wk d$ | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| swp_w900_t6 | AH:A0.5/s-1/any/any | skip | bs:PE:london | 58285/79907 (27.1) | -10.0/41.9/35.6 | 33/46/41 | 194847/165224 | 1856 | 6.0 | 0.18/0.39 | 0.39/1.00 | ok | -385 | LEAD |
| swp_w900_t6 | AH:D5/s-1/any/any | skip | bs:PE:london | 58285/79907 (27.1) | -10.0/41.9/47.5 | 32/46/51 | 192449/165224 | 1760 | 6.3 | 0.25/0.46 | 0.46/1.00 | ok | -385 | LEAD |
| swp_w900_t6 | AH:A1/s-1/any/any | half | ALL | 42386/79907 (47.0) | 32.7/40.7/38.0 | 41/35/32 | 208413/165224 | -2104 | 67.0 | 0.01/0.10 | 0.10/1.00 | ok | -26379 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK |
| swp_w900_t6 | AH:D10/s-1/any/any | skip | bs:PE:london | 58285/79907 (27.1) | -10.0/41.9/45.4 | 31/45/49 | 182854/165224 | 1376 | 6.3 | 0.18/0.41 | 0.41/1.00 | ok | -385 | LEAD |
| swp_w900_t6 | AH:A1/s-1/any/any | skip | bs:PE:london | 58285/79907 (27.1) | -10.0/41.9/52.1 | 31/45/55 | 182854/165224 | 1376 | 6.2 | 0.24/0.56 | 0.56/1.00 | ok | -385 | LEAD |
| swp_w900_t6 | AH:D20/s-1/any/any | skip | bs:PE:london | 58285/79907 (27.1) | -10.0/41.9/45.4 | 31/45/49 | 182854/165224 | 1376 | 6.3 | 0.22/0.50 | 0.50/1.00 | ok | -385 | LEAD |
| swp_w900_t6 | AH:A0.5/s-1/any/any | quarter | bs:PE:london | 60056/79907 (24.8) | 3.3/39.3/25.3 | 30/44/31 | 198618/165224 | 1733 | 6.0 | 0.05/0.04 | 0.05/1.00 | ok | 1040 | CANDIDATE (own-p only; family p 1.00) |
| swp_w900_t6 | AH:D5/s-1/any/any | quarter | bs:PE:london | 60056/79907 (24.8) | 3.3/39.3/39.4 | 30/44/44 | 202236/165224 | 1685 | 6.3 | 0.05/0.07 | 0.07/1.00 | ok | 1040 | CANDIDATE (own-p only; family p 1.00) |
| swp_w900_t6 | AH:A1.5/s-1/any/any | half | ALL | 42386/79907 (47.0) | 32.7/40.7/37.4 | 41/34/30 | 204747/165224 | -2343 | 67.6 | 0.01/0.04 | 0.04/1.00 | ok | -26379 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK |
| swp_w900_t6 | AH:D10/s-1/any/any | quarter | bs:PE:london | 60056/79907 (24.8) | 3.3/39.3/35.7 | 29/43/39 | 195040/165224 | 1397 | 6.3 | 0.10/0.06 | 0.10/1.00 | ok | 1040 | CANDIDATE (own-p only; family p 1.00) |

*swp: "swp_w900_t6, skip AH:A0.5|s-1|any|any on bs:PE:london" cuts L6M maxDD 27.1% (equal-mean 33% / PRE 46% / X' 41%) touching 6% of trades at 1856 $/wk mean change; placebo p 0.18/0.39, family p 1.00 (max over all F cells), WF holds, live week -385 $; label LEAD.*

### maxsz - max-size level of the last 5/15 min

Cells 5691 (down-only 5563); LEAD/CANDIDATE 557; SCOPE-EFFECT 349. WF (purged monthly, 26-wk trailing, 7-d embargo, pick among all 5563 cells): house criterion cut 20.2% (degenerate: it picks near-zero-trade cells, mean 4108 $/wk), with a >=85% mean-retention constraint cut 24.7% at mean 11368 vs ref 16547 $/wk (34 of 34 months picked a cell).

| level | geometry | action | scope | L6M maxDD cell/ref (cut%) | cut% HOLD/PRE/X' | equal-mean cut% L6M/PRE/X' | worst-20 L6M cell/ref | d mean $/wk L6M | touched % | placebo p L6M/PRE | p family own/max (lf-max) | WF | live wk d$ | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| maxsz_w300 | AH:D40/s-1/any/any | quarter | s:london | 59716/79907 (25.3) | -3.8/31.2/29.6 | 31/37/35 | 193923/165224 | 2043 | 14.3 | 0.12/0.17 | 0.17/1.00 | ok | 4924 | LEAD |
| maxsz_w300 | AH:D90/s-1/any/any | quarter | s:london | 59716/79907 (25.3) | -3.8/31.2/29.6 | 31/36/35 | 193923/165224 | 1851 | 14.3 | 0.02/0.14 | 0.14/1.00 | ok | 4924 | LEAD |
| maxsz_w300 | AH:D20/s-1/any/any | quarter | s:london | 60566/79907 (24.2) | -3.8/28.7/29.6 | 30/34/35 | 190733/165224 | 2064 | 14.0 | 0.04/0.30 | 0.30/1.00 | ok | 4924 | LEAD |
| maxsz_w900 | BH-absent:B10 | quarter | ALL | 46541/79907 (41.8) | 21.7/41.3/37.4 | 34/33/29 | 226884/165224 | -3211 | 51.6 | 0.02/0.04 | 0.04/1.00 | ok | -30379 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK |
| maxsz_w900 | BH-absent:B10 | half | ALL | 44396/79907 (44.4) | 22.2/33.7/31.5 | 42/31/28 | 232478/165224 | -1221 | 51.6 | 0.01/0.02 | 0.02/1.00 | ok | -18084 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK |
| maxsz_w300 | AH:D10/s-1/any/any | quarter | s:london | 62148/79907 (22.2) | -9.3/20.2/29.6 | 28/26/34 | 195031/165224 | 1813 | 13.2 | 0.09/0.51 | 0.51/1.00 | ok | 4924 | LEAD |
| maxsz_w300 | AH:A1/s-1/any/any | quarter | s:london | 62148/79907 (22.2) | -12.2/26.6/20.8 | 26/30/24 | 181492/165224 | 1124 | 12.2 | 0.08/0.16 | 0.16/1.00 | ok | 4924 | LEAD |
| maxsz_w900 | BH-absent:B2 | half | ALL | 44199/79907 (44.7) | 41.6/41.1/42.0 | 28/24/25 | 151762/165224 | -4840 | 87.3 | 0.01/0.11 | 0.11/1.00 | ok | -34033 | LEAD |
| maxsz_w900 | BH-absent:B5 | half | ALL | 47782/79907 (40.2) | 24.3/35.4/30.2 | 34/29/23 | 196128/165224 | -2030 | 70.6 | 0.01/0.11 | 0.11/1.00 | ok | -36564 | LEAD |
| maxsz_w300 | AH:D40/s-1/any/any | half | s:london | 65098/79907 (18.5) | -2.1/21.3/21.3 | 23/25/26 | 190828/165224 | 1369 | 14.3 | 0.10/0.20 | 0.20/1.00 | ok | 3958 | LEAD |

*maxsz: "maxsz_w300, quarter AH:D40|s-1|any|any on s:london" cuts L6M maxDD 25.3% (equal-mean 31% / PRE 37% / X' 35%) touching 14% of trades at 2043 $/wk mean change; placebo p 0.12/0.17, family p 1.00 (max over all F cells), WF holds, live week 4924 $; label LEAD.*

### dpiv - depth-imbalance pivot

Cells 1277 (down-only 1213); LEAD/CANDIDATE 90; SCOPE-EFFECT 134. WF (purged monthly, 26-wk trailing, 7-d embargo, pick among all 1213 cells): house criterion cut 35.0% (degenerate: it picks near-zero-trade cells, mean 4268 $/wk), with a >=85% mean-retention constraint cut -12.7% at mean 12719 vs ref 16547 $/wk (34 of 34 months picked a cell).

| level | geometry | action | scope | L6M maxDD cell/ref (cut%) | cut% HOLD/PRE/X' | equal-mean cut% L6M/PRE/X' | worst-20 L6M cell/ref | d mean $/wk L6M | touched % | placebo p L6M/PRE | p family own/max (lf-max) | WF | live wk d$ | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| dpiv_w900 | BH-absent:B5 | skip | s:nyam | 68939/79907 (13.7) | 10.0/17.4/-4.8 | 22/26/6 | 240623/165224 | 2490 | 21.1 | 0.13/0.11 | 0.13/1.00 | no | -17650 | LEAD |
| dpiv_w900 | AH:D20/s-1/any/any | skip | bs:SM:london | 72945/79907 (8.7) | -2.5/5.1/6.6 | 9/6/7 | 174858/165224 | 119 | 0.9 | 0.15/0.33 | 0.33/1.00 | no | -1200 | LEAD |
| dpiv_w900 | AH:A1/s-1/any/any | skip | bs:SM:london | 72945/79907 (8.7) | -2.5/5.1/8.4 | 9/6/9 | 174858/165224 | 119 | 0.8 | 0.07/0.32 | 0.32/1.00 | no | -1200 | LEAD |
| dpiv_w900 | AH:D40/s-1/any/any | skip | bs:SM:london | 72945/79907 (8.7) | -2.5/5.1/6.6 | 9/5/7 | 172456/165224 | 23 | 0.9 | 0.06/0.35 | 0.35/1.00 | no | -1200 | LEAD |
| dpiv_w900 | AH:A0.5/s-1/any/any | skip | bs:SM:london | 76788/79907 (3.9) | -4.8/2.7/4.7 | 6/5/7 | 176841/165224 | 540 | 0.7 | 0.20/0.36 | 0.36/1.00 | no | 0 | LEAD |
| dpiv_w900 | BH-absent:B5 | skip | b:KB | 71185/79907 (10.9) | -1.5/11.9/14.7 | 4/5/8 | 160596/165224 | -1790 | 25.0 | 0.04/0.25 | 0.25/1.00 | no | -11380 | LEAD |
| dpiv_w900 | BH-absent:B5 | skip | bs:PE:london | 60397/79907 (24.4) | -39.4/49.0/1.8 | 26/50/4 | 151709/165224 | 415 | 5.6 | 0.22/0.02 | 0.22/1.00 | no | -570 | LEAD |
| dpiv_w900 | BH-absent:B20 | skip | bs:KB:asia | 79437/79907 (0.6) | -0.4/0.5/12.0 | 3/3/14 | 172509/165224 | 677 | 4.4 | 0.17/0.38 | 0.38/1.00 | no | -3750 | LEAD |
| dpiv_w900 | BH-absent:B5 | quarter | bs:PE:london | 65788/79907 (17.7) | -16.2/40.1/0.8 | 20/41/3 | 160616/165224 | 539 | 5.6 | 0.21/0.02 | 0.21/1.00 | no | 321 | LEAD |
| dpiv_w900 | AH:D20/s-1/any/any | half | bs:SM:london | 76650/79907 (4.1) | -2.4/2.2/3.8 | 5/3/4 | 172111/165224 | 168 | 0.9 | 0.07/0.34 | 0.34/1.00 | no | 0 | LEAD |

*dpiv: "dpiv_w900, skip BH-absent:B5 on s:nyam" cuts L6M maxDD 13.7% (equal-mean 22% / PRE 26% / X' 6%) touching 21% of trades at 2490 $/wk mean change; placebo p 0.13/0.11, family p 1.00 (max over all F cells), WF fails, live week -17650 $; label LEAD.*

## 2. SIZE-UP when a level sits BEHIND the trade (UP rows: labelled, never promoted without the up-size bar; first-order overstates up-size mean)

| level | geometry | action | scope | L6M maxDD cell/ref (cut%) | cut% HOLD/PRE/X' | equal-mean cut% L6M/PRE/X' | worst-20 L6M cell/ref | d mean $/wk L6M | touched % | placebo p L6M/PRE | p family own/max (lf-max) | WF | live wk d$ | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| maxsz_w300 | BH-present:B20/s-1 | up1.5 | s:asia | 78318/79907 (2.0) | -8.7/-5.8/-10.8 | 35/30/27 | 335201/165224 | 11724 | 28.7 | 0.02/0.92 | 0.92/1.00 | ok | n/a | UP (report, never promoted) |
| maxsz_w900 | BH-present:B10/s-1 | up1.5 | ALL | 86459/79907 (-8.2) | -31.0/-12.4/-8.8 | 29/27/29 | 329764/165224 | 12138 | 48.4 | 0.01/0.09 | 0.09/1.00 | ok | n/a | UP (report, never promoted) |
| maxsz_w300 | BH-present:B5/s-1 | up1.5 | s:asia | 64954/79907 (18.7) | -15.8/3.8/-6.9 | 42/32/24 | 331691/165224 | 8907 | 16.8 | 0.01/0.55 | 0.55/1.00 | ok | n/a | UP (report, never promoted) |
| swp_w300_t6 | BH-present:B5/s-1 | up1.5 | s:asia | 91978/79907 (-15.1) | -13.8/9.6/-7.4 | 22/39/27 | 320070/165224 | 11198 | 26.1 | 0.71/0.30 | 0.71/1.00 | ok | n/a | UP (report, never promoted) |
| maxsz_w900 | BH-present:B20/s-1 | up1.5 | s:asia | 84577/79907 (-5.8) | -20.4/-3.0/-8.9 | 23/25/21 | 296212/165224 | 8778 | 26.1 | 0.28/0.89 | 0.89/1.00 | ok | n/a | UP (report, never promoted) |
| maxsz_w300 | BH-present:B10/s-1 | up1.5 | ALL | 92374/79907 (-15.6) | -43.5/-0.9/-26.1 | 27/36/20 | 325789/165224 | 12316 | 62.0 | 0.01/0.01 | 0.01/1.00 | ok | n/a | UP (report, never promoted) |
| maxsz_w300 | BH-present:B20/s-1 | up1.5 | bs:PE:asia | 80145/79907 (-0.3) | -0.7/-5.7/-5.1 | 24/20/20 | 255146/165224 | 6747 | 8.9 | 0.14/0.87 | 0.87/1.00 | ok | n/a | UP (report, never promoted) |
| swp_w900_t6 | BH-present:B5/s-1 | up1.5 | bs:PE:asia | 84101/79907 (-5.2) | -16.7/3.4/-4.6 | 20/26/20 | 248559/165224 | 7192 | 9.5 | 0.37/0.36 | 0.37/1.00 | ok | n/a | UP (report, never promoted) |

## 3. By scope: the best down-only cell per book / session / book x session (gain > 0 over the group-wide action; else the table says none)

| level | geometry | action | scope | L6M maxDD cell/ref (cut%) | cut% HOLD/PRE/X' | equal-mean cut% L6M/PRE/X' | worst-20 L6M cell/ref | d mean $/wk L6M | touched % | placebo p L6M/PRE | p family own/max (lf-max) | WF | live wk d$ | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| swp_w900_t6 | AH:A1/s-1/any/any | half | ALL | 42386/79907 (47.0) | 32.7/40.7/38.0 | 41/35/32 | 208413/165224 | -2104 | 67.0 | 0.01/0.10 | 0.10/1.00 | ok | -26379 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK |
| wall_k3_p15 | AH:A0.5/s-1/any/any | skip | b:HM | 79907/79907 (0.0) | 0.0/0.0/7.5 | 1/1/8 | 165015/165224 | 169 | 0.2 | 0.61/0.76 | 0.76/1.00 | ok | n/a | no |
| ice_w120_n2 | AH:D10/s-1/any/any | skip | b:KB | 77128/79907 (3.5) | -6.0/2.9/8.2 | 5/4/9 | 170805/165224 | 287 | 14.6 | 0.35/0.78 | 0.78/1.00 | no | -7955 | LEAD |
| swp_w900_t6 | AH:D10/s-1/any/any | skip | b:MV | 63343/79907 (20.7) | 11.8/10.1/8.4 | 27/17/15 | 243062/165224 | 2184 | 13.7 | 0.01/0.27 | 0.27/1.00 | ok | -7990 | LEAD |
| maxsz_w900 | AH:D90/s8/any/any | skip | b:OD | 79907/79907 (0.0) | -1.8/0.0/-0.3 | 1/1/1 | 166550/165224 | 299 | 1.1 | 0.34/0.58 | 0.58/1.00 | ok | n/a | no |
| dpiv_w900 | AH:A0.5/s-1/any/any | skip | b:PB | 79760/79907 (0.2) | 2.9/0.1/1.1 | 1/1/2 | 168196/165224 | 172 | 0.9 | 0.30/0.30 | 0.30/1.00 | no | -270 | LEAD |
| ice_w600_n1 | AH:D40/s-1/any/any | quarter | b:PE | 39738/79907 (50.3) | 18.2/51.0/51.7 | 35/36/37 | 148329/165224 | -5195 | 21.9 | 0.02/0.12 | 0.12/1.00 | no | -64405 | LEAD |
| maxsz_w300 | BH-absent:B20 | skip | b:SM | 76232/79907 (4.6) | 3.7/10.4/8.3 | 5/10/8 | 148038/165224 | 7 | 1.3 | 0.22/0.06 | 0.22/1.00 | ok | 1350 | LEAD |
| abs_w900_v2 | AH:A1/s6/any/any | skip | s:asia | 79907/79907 (0.0) | 0.0/0.0/3.4 | 2/2/6 | 178306/165224 | 523 | 0.2 | 0.49/0.70 | 0.70/1.00 | ok | 0 | no |
| ice_w600_n1 | AH:A0.5/s-1/any/any | quarter | s:london | 54636/79907 (31.6) | -10.9/43.1/27.8 | 35/46/32 | 211649/165224 | 1185 | 26.4 | 0.06/0.30 | 0.30/1.00 | no | 3873 | LEAD |
| maxsz_w900 | BH-absent:B5 | skip | s:nyam | 75266/79907 (5.8) | 11.8/11.0/33.2 | 9/14/36 | 269990/165224 | 982 | 22.3 | 0.37/0.57 | 0.57/1.00 | ok | -25205 | LEAD |
| swp_w900_t12 | BH-absent:B20 | skip | s:nypm | 78609/79907 (1.6) | 0.0/7.6/4.7 | 2/8/5 | 170388/165224 | 15 | 1.3 | 0.23/0.03 | 0.23/1.00 | ok | 640 | LEAD |
| wall_k3_p15 | AH:A1/s-1/any/any | skip | bs:HM:asia | 79907/79907 (0.0) | 0.0/0.0/2.0 | 1/1/3 | 165015/165224 | 169 | 0.3 | 0.37/0.56 | 0.56/1.00 | ok | n/a | no |
| maxsz_w900 | AH:D5/s8/any/any | skip | bs:HM:nyam | 79907/79907 (0.0) | 0.0/0.0/0.6 | 0/0/1 | 166420/165224 | 48 | 0.2 | 0.44/0.69 | 0.69/1.00 | ok | n/a | no |
| ice_w600_n2 | BH-absent:B20 | skip | bs:KB:asia | 79248/79907 (0.8) | 0.6/4.5/4.4 | 3/7/7 | 182968/165224 | 610 | 2.0 | 0.10/0.08 | 0.10/1.00 | no | -490 | LEAD |
| ice_w120_n4 | BH-absent:B5 | skip | bs:KB:london | 75500/79907 (5.5) | 10.2/9.1/4.6 | 7/10/6 | 160302/165224 | 354 | 8.1 | 0.06/0.56 | 0.56/1.00 | no | 195 | LEAD |
| ice_w120_n2 | AH:D10/s-1/any/any | skip | bs:KB:nyam | 80754/79907 (-1.1) | -3.3/-0.9/-1.5 | 2/2/2 | 181328/165224 | 742 | 5.6 | 0.12/0.86 | 0.86/1.00 | no | n/a | no |
| swp_w900_t12 | BH-absent:B20 | skip | bs:KB:nypm | 78609/79907 (1.6) | 0.0/7.6/4.7 | 2/8/5 | 170388/165224 | 15 | 1.3 | 0.19/0.01 | 0.19/1.00 | ok | 640 | LEAD |
| swp_w900_t6 | AH:D10/s-1/any/any | skip | bs:MV:london | 69549/79907 (13.0) | 6.6/8.3/3.3 | 18/13/8 | 212804/165224 | 1514 | 7.1 | 0.11/0.52 | 0.52/1.00 | ok | -6810 | LEAD |
| maxsz_w300 | BH-absent:B5 | skip | bs:MV:nyam | 80312/79907 (-0.5) | 2.3/0.9/4.9 | 4/5/9 | 193322/165224 | 1097 | 6.2 | 0.33/0.39 | 0.39/1.00 | ok | n/a | no |
| maxsz_w900 | AH:D90/s8/any/any | skip | bs:OD:nyam | 79907/79907 (0.0) | -1.8/0.0/-0.3 | 1/1/1 | 166550/165224 | 299 | 1.1 | 0.31/0.57 | 0.57/1.00 | ok | n/a | no |
| dpiv_w900 | AH:A0.5/s-1/any/any | skip | bs:PB:asia | 79760/79907 (0.2) | 2.9/0.1/1.1 | 1/1/2 | 168196/165224 | 172 | 0.9 | 0.23/0.14 | 0.23/1.00 | no | -270 | LEAD |
| abs_w900_v2 | AH:D10/s6/any/any | skip | bs:PE:asia | 79907/79907 (0.0) | 0.0/0.0/0.0 | 2/2/2 | 175223/165224 | 400 | 0.1 | 0.77/0.84 | 0.84/1.00 | ok | 0 | no |
| swp_w900_t6 | AH:A0.5/s-1/any/any | skip | bs:PE:london | 58285/79907 (27.1) | -10.0/41.9/35.6 | 33/46/41 | 194847/165224 | 1856 | 6.0 | 0.18/0.39 | 0.39/1.00 | ok | -385 | LEAD |
| (none) | | | bs:PE:nyam | no cell beats the group-wide action | | | | | | | | | | |
| maxsz_w300 | AH:D5/s8/tch0/any | skip | bs:SM:asia | 79907/79907 (0.0) | 0.0/0.0/-0.0 | 0/0/0 | 167586/165224 | 94 | 0.1 | 0.71/0.96 | 0.96/1.00 | ok | n/a | no |
| ice_w120_n2 | BH-absent:B20 | skip | bs:SM:london | 70626/79907 (11.6) | 2.3/12.0/16.7 | 15/15/19 | 177810/165224 | 796 | 1.6 | 0.10/0.12 | 0.12/1.00 | no | 120 | LEAD |

## 4. Purged monthly walk-forward of the picking procedure (per level family; OOS 2024-01..2026-10; all-weeks maxDD)

| level family | cells | house WF cut% | house WF mean $/wk | retention-constrained WF cut% | mean $/wk | ref mean $/wk | worst-20 WF / ref | equal-mean-free Calmar picker cut% |
|---|---|---|---|---|---|---|---|---|
| abs | 5084 | 99.5 | 28 | 31.9 | 13555 | 16547 | -784120/-1079974 | 31.9 |
| dpiv | 1213 | 35.0 | 4268 | -12.7 | 12719 | 16547 | -991060/-1079974 | 36.5 |
| ice | 4152 | 43.1 | 2422 | -15.8 | 9306 | 16547 | -828624/-1079974 | 39.2 |
| maxsz | 5563 | 20.2 | 4108 | 24.7 | 11368 | 16547 | -877840/-1079974 | -4.4 |
| swp | 5070 | 52.8 | 6328 | 40.0 | 11745 | 16547 | -788552/-1079974 | 42.1 |
| wall | 9587 | 98.2 | 86 | 17.0 | 9514 | 16547 | -890335/-1079974 | 44.0 |

## 7. Where zones HURT (by book; F cells scoped to one book, first-order, equal-mean minimum cut over L6M/PRE/X')

| book | cells | median equal-mean min cut % | share of cells with cut > 0 | share beating the same action on every trade of the book | best cell | worst cell |
|---|---|---|---|---|---|---|
| b:HM | 1069 | -1.2 | 18% | 96% | wall_k3_p15 AH:D5/s-1/any/any skip (1) | abs_w300_v8 BH-absent:B5 skip (-26) |
| b:KB | 1300 | -0.9 | 9% | 60% | ice_w120_n2 AH:D10/s-1/any/any skip (4) | swp_w300_t12 BH-absent:B5 skip (-30) |
| b:MV | 1143 | -0.7 | 22% | 40% | swp_w900_t6 AH:D10/s-1/any/any skip (15) | swp_w300_t12 BH-absent:B20 skip (-39) |
| b:OD | 144 | -3.4 | 15% | 69% | maxsz_w900 AH:D90/s8/any/any skip (1) | dpiv_w900 AH:D20/s-1/any/any skip (-8) |
| b:PB | 323 | -2.4 | 4% | 94% | dpiv_w900 AH:A0.5/s-1/any/any skip (1) | abs_w300_v2 BH-absent:B5 skip (-14) |
| b:PE | 1380 | -4.4 | 21% | 35% | ice_w600_n1 AH:D20/s-1/any/any quarter (35) | ice_w120_n4 BH-absent:B20 skip (-172) |
| b:SM | 1056 | -5.5 | 3% | 88% | maxsz_w300 BH-absent:B20 skip (5) | wall_k2_p5 AH:D5/s-1/any/any skip (-49) |

Sentence per book: books whose median equal-mean cut is negative are the ones where F zones HURT (the cell removes lots from trades that were not the drawdown); the standing rule keeps the zone layer ON everywhere, so these rows only say the F level adds nothing for that book.

## 8. Level-specificity (shifted +-25 pt along the trade direction and shuffled-day placebos; top 40 cells per level family by minimum equal-mean cut, among cells with gain over the group-wide action > 0)

| level family | tested | level-specific | not level-specific: a shifted level does as well | shuffled days do as well |
|---|---|---|---|---|
| abs | 40 | 31 | 1 | 8 |
| dpiv | 40 | 33 | 1 | 6 |
| ice | 40 | 36 | 4 | 0 |
| maxsz | 40 | 33 | 7 | 0 |
| swp | 40 | 34 | 6 | 0 |
| wall | 40 | 38 | 0 | 2 |

Control bases (top 200 by minimum equal-mean cut (gain > 0), same rules on the NOCUT / UNIF trade lists; lv_F rebuilt for those lists): median L6M cut live-base 32.8 / NOCUT 46.4 / UNIF 36.6; share of the 200 with L6M AND PRE cut > 0: live 100% / NOCUT 100% / UNIF 100%.

## 9. Roll check of the 1-s state levels

Jump seconds > 120 pts in the state mids: 15 over 931 days; 14 coincide with an instrument change (the rolls) and one is a Sunday-open gap. The F kernels cut every look-back window at the last instrument/have change, so no level spans a roll; 1-3 trades per roll fall within 15 min. The 1-min bars of nq1m_state (used only for ATR14 in ATR-unit geometry and the tree) carried 544 bars with TR > 100 pts (rolls/session gaps) that contaminated ATR14 for 240 trades; ATR14 is now the mean plain bar range (high-low) and the whole grid was re-run.


## 6. Learned layer: monotone small tree / small GBDT (<= 8 leaves) over causal zone features of A,B,G,F (lv_*.parquet) -> skip/half/full (FIRST-ORDER, purged monthly expanding WF 2024-01..2026-10, 7-day embargo, 3 seeds, family null = pnl permuted within book x session x month, 20 draws)

Features: nearest level ahead/behind in ATR, touches, age, strength, confluence, #levels in path per family (monotone: farther ahead -> better, closer support behind -> better), 7 representative F level sets, session, book, side, ER, ATR, lots. Action by the percentile of the prediction within the training predictions (bottom q_h% halved, bottom q_s% skipped). L6M/HOLD/PRE are fully OOS; X' is training-era (not scored). Re-target-distance learning needs path-level exact runs: queued.

| model | best policy (halve bottom q_h% / skip bottom q_s%) | equal-lots cut L6M/HOLD/PRE | equal-mean cut L6M/HOLD/PRE | d mean $/wk L6M/PRE | lots-changed trades | seed values of the equal-mean min | null (20 draws) 90th/max | family p | verdict |
|---|---|---|---|---|---|---|---|---|---|
| tree | 50/0 | 36.4/40.6/40.9 | 17.3/22.7/23.2 | -5054/-2240 | 5746 | 1/16/-15 | 18.7/27.7 | 0.24 | no (null reaches it) |
| gbdt | 50/0 | 16.2/26.0/23.7 | 11.7/22.0/19.6 | -1411/-2211 | 3422 | 11/7/10 | 17.0/32.3 | 0.33 | no (null reaches it) |

Single-level comparator (same OOS months, retention-constrained purged WF picker per level family; equal-mean cut on the OOS daily series):

| level family | equal-mean cut L6M/HOLD/PRE | min | d mean $/wk L6M |
|---|---|---|---|
| abs | 13.0/-5.6/37.5 | -5.6 | -2025 |
| dpiv | -24.1/-95.2/23.8 | -95.2 | -4352 |
| ice | -36.1/-30.6/-71.5 | -71.5 | -7269 |
| maxsz | -0.7/-31.3/11.2 | -31.3 | -4072 |
| swp | -44.2/-15.8/14.8 | -44.2 | -6613 |
| wall | -192.9/-135.2/-56.6 | -192.9 | -11239 |

Verdict: GBDT best-policy statistic 11.7 vs best single-level WF -5.6; own-null family p 0.33. The learned layer does NOT clear both bars (beat single-level cells OOS and the permutation null): reported as a FAILURE.


## Next (queue)

- exact engine top-5 per level family (set files by SZ-CORE queue); state-cut arm widening/tightening when a support sits just behind the adverse extreme (own subclass, cde_exact pattern); shifted-level / shuffled-day placebos for the top cells; control bases S1b-NOCUT / S1b-UNIF re-scoring; tree layer (section 6) over A..G + F features.
