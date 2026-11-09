# ZN-BOOK - T-ZONES-EXHAUST family F (book-derived levels on the 1-s state base) - refreshed 2026-11-09 17:20Z

Base S1b-COMB (live D7 v1.5 state-cut lines, Q1-A, HALF D20 + OTE-62 B73 D30 inside the base), 21,135 trades 2023-04..2026-10-30; windows as of 2026-11-09; maxDD/worst-20/Ulcer on ALL weeks, carry week dropped from MEANS only. FIRST-ORDER SCREEN ONLY (exact top-5 queued); PRE-PROOF; post-hoc; Shadow only; no PASS claims. Prereg: ZN_BOOK_PREREG.md (sha in DECISIONS.md). Features: code/th_zn/zn_book_lv.py (all from the raw mbp-10 1-s state arrays, rows <= the signal-second row; NT8 needs the chart L2/DOM series for the book levels: walls/iceberg/absorption/sweep/max-size/depth pivot are Level-2 quantities, not chart-OHLC).

**Cells scored: 32383** (35 level sets x geometry x action x scope pooled / book / session / book x session; identical flags deduplicated). Label counts: no 25021, LEAD 2881, SCOPE-EFFECT 2799, UP 1490, CANDIDATE 192.

**Reading guide.** The cut % columns are at EQUAL LOTS (the cell removes lots); the equal-mean columns rescale all lots by one factor so the L6M mean equals the Q1-A reference, then compare maxDD (the honest drawdown comparison). Every cell is compared to the SAME action applied to EVERY trade of its scope (group-wide baseline, columns gw_*; `gain_rk` = min equal-mean cut of the cell minus min equal-mean cut of the group-wide action): a level that only picks most of a weak book is labelled SCOPE-EFFECT, not a zone finding. p family = WY-style max-stat over ALL 32383 F cells (own = placebo p; family max in the table is over the whole F set, lf-max over the cell's level family only).

## 0. Reference rows (S1b-COMB, Q1-A live layer, no F zone)

| row | L6M maxDD | HOLD maxDD | PRE maxDD | X' maxDD | L6M mean $/wk | L6M worst-20 |
|---|---|---|---|---|---|---|
| live layer (S1b-COMB as is) | 79907 | 99496 | 140288 | 116941 | 21344 | 165224 |

## 1. Family F by level set (ranked by the minimum equal-mean cut over L6M/PRE/X', down-only cells with gain over the group-wide action > 0)

### wall - resting-size walls (size >= k x MedLevel in the top 10, persistence p s)

Cells 10179 (down-only 9731); LEAD/CANDIDATE 373; SCOPE-EFFECT 670. WF (purged monthly, 26-wk trailing, 7-d embargo, pick among all 9731 cells): house criterion cut 98.7% (degenerate: it picks near-zero-trade cells, mean 74 $/wk), with a >=85% mean-retention constraint cut 17.5% at mean 11153 vs ref 16574 $/wk (34 of 34 months picked a cell).

| level | geometry | action | scope | L6M maxDD cell/ref (cut%) | cut% HOLD/PRE/X' | equal-mean cut% L6M/PRE/X' | worst-20 L6M cell/ref | d mean $/wk L6M | touched % | placebo p L6M/PRE | p family own/max (lf-max) | WF | live wk d$ | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| wall_k3_p0 | BH-absent:B20 | quarter | s:london | 50126/79907 (37.3) | -40.1/47.8/34.0 | 33/44/29 | 190621/165224 | -1878 | 29.0 | 0.01/0.03 | 0.03/1.00 | ok | 134 | CANDIDATE (own-p only; family p 1.00) |
| wall_k3_p0 | BH-absent:B5 | quarter | s:london | 50126/79907 (37.3) | -46.1/47.8/34.0 | 33/44/29 | 190621/165224 | -1878 | 29.1 | 0.01/0.04 | 0.04/1.00 | ok | 134 | CANDIDATE (own-p only; family p 1.00) |
| wall_k3_p0 | BH-absent:B5 | half | s:london | 52897/79907 (33.8) | -23.9/40.1/28.3 | 32/38/26 | 197077/165224 | -873 | 29.1 | 0.01/0.02 | 0.02/1.00 | ok | -1372 | CANDIDATE (own-p only; family p 1.00) |
| wall_k3_p0 | BH-absent:B20 | half | s:london | 52897/79907 (33.8) | -20.3/38.4/28.3 | 32/36/26 | 197077/165224 | -873 | 29.0 | 0.01/0.04 | 0.04/1.00 | ok | -1372 | CANDIDATE (own-p only; family p 1.00) |
| wall_k3_p0 | BH-absent:B20 | skip | bs:PE:london | 53788/79907 (32.7) | -47.3/48.5/24.5 | 33/49/25 | 176830/165224 | 222 | 7.2 | 0.05/0.30 | 0.30/1.00 | ok | -4490 | LEAD |
| wall_k3_p0 | BH-absent:B5 | skip | bs:PE:london | 53788/79907 (32.7) | -55.7/48.5/24.5 | 33/49/25 | 176830/165224 | 222 | 7.2 | 0.09/0.35 | 0.35/1.00 | ok | -4490 | LEAD |
| wall_k2_p5 | BH-absent:B5 | skip | bs:PE:london | 56403/79907 (29.4) | -55.8/37.0/26.4 | 25/33/22 | 125848/165224 | -1491 | 7.0 | 0.17/0.91 | 0.91/1.00 | ok | -385 | LEAD |
| wall_k3_p0 | BH-absent:B5 | quarter | b:PE | 42456/79907 (46.9) | 32.1/46.1/46.6 | 22/21/22 | 135455/165224 | -6807 | 22.4 | 0.05/0.25 | 0.25/1.00 | ok | -71183 | LEAD |
| wall_k3_p0 | BH-absent:B20 | quarter | bs:PE:london | 58841/79907 (26.4) | -31.1/42.0/19.4 | 27/43/20 | 178851/165224 | 289 | 7.2 | 0.08/0.08 | 0.08/1.00 | ok | -2038 | CANDIDATE (own-p only; family p 1.00) |
| wall_k3_p0 | BH-absent:B5 | quarter | bs:PE:london | 58841/79907 (26.4) | -37.1/42.0/19.4 | 27/43/20 | 178851/165224 | 289 | 7.2 | 0.05/0.07 | 0.07/1.00 | ok | -2038 | CANDIDATE (own-p only; family p 1.00) |

*wall: "wall_k3_p0, quarter BH-absent:B20 on s:london" cuts L6M maxDD 37.3% (equal-mean 33% / PRE 44% / X' 29%) touching 29% of trades at -1878 $/wk mean change; placebo p 0.01/0.03, family p 1.00 (max over all F cells), WF holds, live week 134 $; label CANDIDATE (own-p only; family p 1.00).*

### ice - iceberg-refill levels

Cells 4509 (down-only 4156); LEAD/CANDIDATE 992; SCOPE-EFFECT 747. WF (purged monthly, 26-wk trailing, 7-d embargo, pick among all 4156 cells): house criterion cut 40.3% (degenerate: it picks near-zero-trade cells, mean 1799 $/wk), with a >=85% mean-retention constraint cut -12.4% at mean 10339 vs ref 16574 $/wk (34 of 34 months picked a cell).

| level | geometry | action | scope | L6M maxDD cell/ref (cut%) | cut% HOLD/PRE/X' | equal-mean cut% L6M/PRE/X' | worst-20 L6M cell/ref | d mean $/wk L6M | touched % | placebo p L6M/PRE | p family own/max (lf-max) | WF | live wk d$ | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ice_w600_n1 | AH:D20/s-1/any/any | quarter | b:PE | 39738/79907 (50.3) | -3.1/52.8/57.0 | 35/38/44 | 148329/165224 | -5339 | 21.9 | 0.02/0.05 | 0.05/1.00 | no | -64405 | LEAD |
| ice_w600_n1 | AH:D40/s-1/any/any | quarter | b:PE | 39738/79907 (50.3) | -3.1/51.0/57.0 | 35/36/44 | 148329/165224 | -5339 | 21.9 | 0.02/0.12 | 0.12/1.00 | no | -64405 | LEAD |
| ice_w600_n1 | AH:A0.5/s-1/any/any | quarter | s:london | 54636/79907 (31.6) | -32.2/43.1/30.6 | 35/46/34 | 211649/165224 | 1185 | 26.4 | 0.06/0.30 | 0.30/1.00 | no | 3873 | LEAD |
| ice_w600_n1 | AH:A1/s-1/any/any | quarter | b:PE | 39738/79907 (50.3) | -4.2/51.0/57.0 | 34/35/43 | 148329/165224 | -5456 | 21.9 | 0.05/0.09 | 0.09/1.00 | no | -64405 | LEAD |
| ice_w600_n1 | AH:D10/s-1/any/any | quarter | b:PE | 39738/79907 (50.3) | -8.3/57.1/57.0 | 34/43/43 | 147482/165224 | -5538 | 21.9 | 0.01/0.01 | 0.01/1.00 | no | -64405 | LEAD |
| ice_w600_n1 | AH:A0.5/s-1/any/any | quarter | b:PE | 39738/79907 (50.3) | -0.6/48.5/59.6 | 35/33/47 | 149917/165224 | -5295 | 21.5 | 0.05/0.14 | 0.14/1.00 | no | -58398 | LEAD |
| ice_w600_n1 | AH:A0.5/s-1/any/any | skip | b:PE | 31400/79907 (60.7) | -7.9/57.9/65.5 | 35/31/43 | 93967/165224 | -8790 | 21.5 | 0.05/0.45 | 0.45/1.00 | no | -82360 | LEAD |
| ice_w600_n1 | AH:D5/s-1/any/any | quarter | b:PE | 39738/79907 (50.3) | -4.7/49.5/57.0 | 31/30/40 | 129638/165224 | -6236 | 21.8 | 0.03/0.08 | 0.08/1.00 | no | -58398 | LEAD |
| ice_w600_n1 | AH:D10/s-1/any/any | half | ALL | 43793/79907 (45.2) | 8.5/44.2/51.6 | 31/30/39 | 164984/165224 | -4642 | 85.3 | 0.02/0.06 | 0.06/1.00 | no | -40175 | LEAD |
| ice_w600_n1 | AH:D90/s-1/any/any | quarter | s:london | 54636/79907 (31.6) | -35.1/44.2/24.5 | 35/47/29 | 209933/165224 | 1266 | 26.7 | 0.06/0.25 | 0.25/1.00 | no | 3873 | LEAD |

*ice: "ice_w600_n1, quarter AH:D20|s-1|any|any on b:PE" cuts L6M maxDD 50.3% (equal-mean 35% / PRE 38% / X' 44%) touching 22% of trades at -5339 $/wk mean change; placebo p 0.02/0.05, family p 1.00 (max over all F cells), WF fails, live week -64405 $; label LEAD.*

### abs - absorption levels (sold/bought into, held)

Cells 5346 (down-only 5097); LEAD/CANDIDATE 278; SCOPE-EFFECT 374. WF (purged monthly, 26-wk trailing, 7-d embargo, pick among all 5097 cells): house criterion cut 99.5% (degenerate: it picks near-zero-trade cells, mean 28 $/wk), with a >=85% mean-retention constraint cut 30.1% at mean 12850 vs ref 16574 $/wk (34 of 34 months picked a cell).

| level | geometry | action | scope | L6M maxDD cell/ref (cut%) | cut% HOLD/PRE/X' | equal-mean cut% L6M/PRE/X' | worst-20 L6M cell/ref | d mean $/wk L6M | touched % | placebo p L6M/PRE | p family own/max (lf-max) | WF | live wk d$ | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| abs_w300_v2 | BH-absent:B5 | quarter | s:london | 53719/79907 (32.8) | -36.4/47.8/35.1 | 28/44/30 | 180595/165224 | -1907 | 29.1 | 0.07/0.03 | 0.07/1.00 | ok | 3873 | CANDIDATE (own-p only; family p 1.00) |
| abs_w300_v2 | BH-absent:B20 | quarter | s:london | 56823/79907 (28.9) | -26.9/47.3/25.5 | 29/47/25 | 170204/165224 | -31 | 24.7 | 0.07/0.02 | 0.07/1.00 | ok | -1470 | CANDIDATE (own-p only; family p 1.00) |
| abs_w300_v2 | BH-absent:B5 | half | s:london | 55738/79907 (30.2) | -18.5/36.6/27.4 | 28/34/25 | 188238/165224 | -894 | 29.1 | 0.02/0.02 | 0.02/1.00 | ok | 1341 | CANDIDATE (own-p only; family p 1.00) |
| abs_w300_v2 | BH-absent:B5 | skip | s:london | 51886/79907 (35.1) | -63.3/55.5/28.5 | 30/52/23 | 189731/165224 | -1950 | 29.1 | 0.38/0.61 | 0.61/1.00 | ok | -1390 | LEAD |
| abs_w300_v4 | BH-absent:B20 | quarter | s:london | 53719/79907 (32.8) | -40.4/47.8/22.5 | 31/47/21 | 163240/165224 | -527 | 31.1 | 0.08/0.04 | 0.08/1.00 | ok | 3873 | CANDIDATE (own-p only; family p 1.00) |
| abs_w900_v2 | BH-absent:B20 | half | s:london | 55292/79907 (30.8) | -20.1/39.2/25.1 | 27/35/20 | 175292/165224 | -1590 | 27.9 | 0.02/0.01 | 0.02/1.00 | ok | 66 | CANDIDATE (own-p only; family p 1.00) |
| abs_w900_v2 | BH-absent:B20 | quarter | s:london | 53719/79907 (32.8) | -39.3/47.8/29.3 | 24/41/20 | 157433/165224 | -3182 | 27.9 | 0.05/0.01 | 0.05/1.00 | ok | 1960 | CANDIDATE (own-p only; family p 1.00) |
| abs_w900_v4 | BH-absent:B5 | half | s:london | 55292/79907 (30.8) | -21.4/39.2/23.7 | 27/36/20 | 181140/165224 | -1422 | 32.2 | 0.01/0.05 | 0.05/1.00 | ok | 1341 | CANDIDATE (own-p only; family p 1.00) |
| abs_w900_v4 | BH-absent:B20 | half | ALL | 41957/79907 (47.5) | 39.3/44.2/59.6 | 24/19/42 | 126665/165224 | -6705 | 97.8 | 0.01/0.09 | 0.09/1.00 | ok | -37680 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK |
| abs_w900_v8 | BH-absent:B20 | half | s:london | 55292/79907 (30.8) | -21.4/39.2/23.7 | 27/36/19 | 181140/165224 | -1518 | 32.3 | 0.01/0.04 | 0.04/1.00 | ok | 1341 | CANDIDATE (own-p only; family p 1.00) |

*abs: "abs_w300_v2, quarter BH-absent:B5 on s:london" cuts L6M maxDD 32.8% (equal-mean 28% / PRE 44% / X' 30%) touching 29% of trades at -1907 $/wk mean change; placebo p 0.07/0.03, family p 1.00 (max over all F cells), WF holds, live week 3873 $; label CANDIDATE (own-p only; family p 1.00).*

### swp - sweep levels (swept, now cleared)

Cells 5381 (down-only 5133); LEAD/CANDIDATE 811; SCOPE-EFFECT 491. WF (purged monthly, 26-wk trailing, 7-d embargo, pick among all 5133 cells): house criterion cut 52.8% (degenerate: it picks near-zero-trade cells, mean 6957 $/wk), with a >=85% mean-retention constraint cut 39.6% at mean 13044 vs ref 16574 $/wk (34 of 34 months picked a cell).

| level | geometry | action | scope | L6M maxDD cell/ref (cut%) | cut% HOLD/PRE/X' | equal-mean cut% L6M/PRE/X' | worst-20 L6M cell/ref | d mean $/wk L6M | touched % | placebo p L6M/PRE | p family own/max (lf-max) | WF | live wk d$ | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| swp_w900_t6 | AH:A1/s-1/any/any | half | ALL | 42386/79907 (47.0) | 25.2/40.7/41.9 | 41/35/36 | 208413/165224 | -2104 | 67.0 | 0.01/0.10 | 0.10/1.00 | ok | -26379 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK |
| swp_w900_t6 | AH:A1.5/s-1/any/any | half | ALL | 42386/79907 (47.0) | 26.3/40.7/41.3 | 41/34/34 | 204747/165224 | -2343 | 67.6 | 0.01/0.04 | 0.04/1.00 | ok | -26379 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK |
| swp_w900_t6 | AH:D15/s-1/any/any | half | ALL | 42386/79907 (47.0) | 26.3/40.7/40.4 | 41/34/33 | 204940/165224 | -2336 | 67.9 | 0.01/0.10 | 0.10/1.00 | ok | -26379 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK |
| swp_w900_t6 | AH:A0.5/s-1/any/any | skip | bs:PE:london | 58285/79907 (27.1) | -31.3/41.9/39.2 | 33/46/44 | 194847/165224 | 1856 | 6.0 | 0.18/0.34 | 0.34/1.00 | ok | -385 | LEAD |
| swp_w900_t6 | AH:D40/s-1/any/any | half | ALL | 42386/79907 (47.0) | 26.3/40.7/39.3 | 41/34/32 | 203743/165224 | -2286 | 68.1 | 0.01/0.05 | 0.05/1.00 | ok | -26379 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK |
| swp_w900_t6 | AH:D60/s-1/any/any | half | ALL | 42386/79907 (47.0) | 26.3/39.9/39.3 | 41/33/32 | 203743/165224 | -2286 | 68.1 | 0.01/0.06 | 0.06/1.00 | ok | -26379 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK |
| swp_w900_t6 | AH:D5/s-1/any/any | skip | bs:PE:london | 58285/79907 (27.1) | -31.3/41.9/42.1 | 32/46/46 | 192449/165224 | 1760 | 6.3 | 0.25/0.45 | 0.45/1.00 | ok | -385 | LEAD |
| swp_w900_t6 | AH:D10/s-1/any/any | half | ALL | 42386/79907 (47.0) | 26.3/40.7/39.4 | 41/34/32 | 204940/165224 | -2336 | 67.8 | 0.01/0.04 | 0.04/1.00 | ok | -26379 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK |
| swp_w900_t6 | AH:D20/s-1/any/any | half | ALL | 42386/79907 (47.0) | 26.3/40.7/39.3 | 41/34/32 | 204940/165224 | -2336 | 68.0 | 0.01/0.09 | 0.09/1.00 | ok | -26379 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK |
| swp_w900_t6 | AH:D90/s-1/any/any | half | ALL | 42386/79907 (47.0) | 26.3/39.9/39.3 | 41/33/32 | 203743/165224 | -2382 | 68.2 | 0.01/0.15 | 0.15/1.00 | ok | -26379 | LEAD |

*swp: "swp_w900_t6, half AH:A1|s-1|any|any on ALL" cuts L6M maxDD 47.0% (equal-mean 41% / PRE 35% / X' 36%) touching 67% of trades at -2104 $/wk mean change; placebo p 0.01/0.10, family p 1.00 (max over all F cells), WF holds, live week -26379 $; label CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK.*

### maxsz - max-size level of the last 5/15 min

Cells 5691 (down-only 5563); LEAD/CANDIDATE 530; SCOPE-EFFECT 377. WF (purged monthly, 26-wk trailing, 7-d embargo, pick among all 5563 cells): house criterion cut 22.8% (degenerate: it picks near-zero-trade cells, mean 5283 $/wk), with a >=85% mean-retention constraint cut 21.6% at mean 11162 vs ref 16574 $/wk (34 of 34 months picked a cell).

| level | geometry | action | scope | L6M maxDD cell/ref (cut%) | cut% HOLD/PRE/X' | equal-mean cut% L6M/PRE/X' | worst-20 L6M cell/ref | d mean $/wk L6M | touched % | placebo p L6M/PRE | p family own/max (lf-max) | WF | live wk d$ | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| maxsz_w900 | BH-absent:B10 | quarter | ALL | 46541/79907 (41.8) | 20.1/41.3/41.3 | 34/33/33 | 226884/165224 | -3355 | 51.6 | 0.02/0.04 | 0.04/1.00 | ok | -30379 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK |
| maxsz_w300 | AH:D40/s-1/any/any | quarter | s:london | 59716/79907 (25.3) | -7.5/31.2/32.6 | 31/37/38 | 193923/165224 | 2043 | 14.3 | 0.12/0.17 | 0.17/1.00 | ok | 4924 | LEAD |
| maxsz_w300 | AH:D90/s-1/any/any | quarter | s:london | 59716/79907 (25.3) | -7.5/31.2/32.6 | 31/36/37 | 193923/165224 | 1851 | 14.3 | 0.02/0.14 | 0.14/1.00 | ok | 4924 | LEAD |
| maxsz_w900 | BH-absent:B10 | half | ALL | 44396/79907 (44.4) | 22.2/33.7/34.7 | 42/30/31 | 232478/165224 | -1317 | 51.6 | 0.01/0.02 | 0.02/1.00 | ok | -18084 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK |
| maxsz_w300 | AH:D20/s-1/any/any | quarter | s:london | 60566/79907 (24.2) | -8.4/28.7/32.6 | 30/34/38 | 190733/165224 | 2064 | 14.0 | 0.04/0.30 | 0.30/1.00 | ok | 4924 | LEAD |
| maxsz_w900 | BH-absent:B5 | half | ALL | 47782/79907 (40.2) | 11.4/35.4/33.3 | 34/29/26 | 196128/165224 | -2030 | 70.6 | 0.01/0.11 | 0.11/1.00 | ok | -36564 | LEAD |
| maxsz_w300 | AH:D10/s-1/any/any | quarter | s:london | 62148/79907 (22.2) | -9.3/20.2/32.6 | 28/26/37 | 195031/165224 | 1813 | 13.2 | 0.09/0.51 | 0.51/1.00 | ok | 4924 | LEAD |
| maxsz_w300 | AH:A1/s-1/any/any | quarter | s:london | 62148/79907 (22.2) | -12.2/26.6/22.9 | 26/30/26 | 181492/165224 | 1124 | 12.2 | 0.08/0.16 | 0.16/1.00 | ok | 4924 | LEAD |
| maxsz_w900 | BH-absent:B2 | half | ALL | 44199/79907 (44.7) | 31.0/41.1/42.2 | 28/24/25 | 151762/165224 | -4840 | 87.3 | 0.01/0.11 | 0.11/1.00 | ok | -34033 | LEAD |
| maxsz_w300 | AH:D40/s-1/any/any | half | s:london | 65098/79907 (18.5) | -2.1/21.3/23.5 | 23/25/28 | 190828/165224 | 1369 | 14.3 | 0.10/0.20 | 0.20/1.00 | ok | 3958 | LEAD |

*maxsz: "maxsz_w900, quarter BH-absent:B10 on ALL" cuts L6M maxDD 41.8% (equal-mean 34% / PRE 33% / X' 33%) touching 52% of trades at -3355 $/wk mean change; placebo p 0.02/0.04, family p 1.00 (max over all F cells), WF holds, live week -30379 $; label CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK.*

### dpiv - depth-imbalance pivot

Cells 1277 (down-only 1213); LEAD/CANDIDATE 89; SCOPE-EFFECT 140. WF (purged monthly, 26-wk trailing, 7-d embargo, pick among all 1213 cells): house criterion cut 35.0% (degenerate: it picks near-zero-trade cells, mean 4301 $/wk), with a >=85% mean-retention constraint cut -27.8% at mean 12868 vs ref 16574 $/wk (34 of 34 months picked a cell).

| level | geometry | action | scope | L6M maxDD cell/ref (cut%) | cut% HOLD/PRE/X' | equal-mean cut% L6M/PRE/X' | worst-20 L6M cell/ref | d mean $/wk L6M | touched % | placebo p L6M/PRE | p family own/max (lf-max) | WF | live wk d$ | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| dpiv_w900 | AH:D20/s-1/any/any | skip | bs:SM:london | 72945/79907 (8.7) | -5.8/5.1/7.3 | 9/6/8 | 174858/165224 | 119 | 0.9 | 0.15/0.33 | 0.33/1.00 | no | -1200 | LEAD |
| dpiv_w900 | AH:A1/s-1/any/any | skip | bs:SM:london | 72945/79907 (8.7) | -2.5/5.1/9.3 | 9/6/10 | 174858/165224 | 119 | 0.8 | 0.07/0.32 | 0.32/1.00 | no | -1200 | LEAD |
| dpiv_w900 | AH:D40/s-1/any/any | skip | bs:SM:london | 72945/79907 (8.7) | -5.8/5.1/7.3 | 9/5/7 | 172456/165224 | 23 | 0.9 | 0.06/0.35 | 0.35/1.00 | no | -1200 | LEAD |
| dpiv_w900 | AH:A0.5/s-1/any/any | skip | bs:SM:london | 76788/79907 (3.9) | -4.8/2.7/5.2 | 6/5/7 | 176841/165224 | 540 | 0.7 | 0.20/0.36 | 0.36/1.00 | no | 0 | LEAD |
| dpiv_w900 | BH-absent:B5 | skip | bs:PE:london | 60397/79907 (24.4) | -60.7/49.0/2.0 | 26/50/4 | 151709/165224 | 415 | 5.6 | 0.22/0.02 | 0.22/1.00 | no | -570 | LEAD |
| dpiv_w900 | BH-absent:B5 | skip | b:KB | 71185/79907 (10.9) | -1.5/11.9/16.2 | 4/5/9 | 160596/165224 | -1792 | 25.0 | 0.04/0.25 | 0.25/1.00 | no | -11380 | LEAD |
| dpiv_w900 | BH-absent:B20 | skip | bs:KB:asia | 79437/79907 (0.6) | -0.4/0.5/13.2 | 3/3/16 | 172509/165224 | 674 | 4.4 | 0.17/0.38 | 0.38/1.00 | no | -3750 | LEAD |
| dpiv_w900 | BH-absent:B5 | quarter | bs:PE:london | 65788/79907 (17.7) | -37.4/40.1/1.0 | 20/41/3 | 160616/165224 | 539 | 5.6 | 0.21/0.02 | 0.21/1.00 | no | 321 | LEAD |
| dpiv_w900 | AH:D40/s-1/any/any | skip | b:KB | 79569/79907 (0.4) | -4.6/-1.5/1.9 | 5/3/6 | 200974/165224 | 1209 | 6.8 | 0.31/0.74 | 0.74/1.00 | no | n/a | no |
| dpiv_w900 | AH:D10/s-1/any/any | skip | b:KB | 79569/79907 (0.4) | -5.8/-4.0/0.8 | 7/3/7 | 195900/165224 | 1624 | 6.3 | 0.25/0.91 | 0.91/1.00 | no | n/a | no |

*dpiv: "dpiv_w900, skip AH:D20|s-1|any|any on bs:SM:london" cuts L6M maxDD 8.7% (equal-mean 9% / PRE 6% / X' 8%) touching 1% of trades at 119 $/wk mean change; placebo p 0.15/0.33, family p 1.00 (max over all F cells), WF fails, live week -1200 $; label LEAD.*

## 2. SIZE-UP when a level sits BEHIND the trade (UP rows: labelled, never promoted without the up-size bar; first-order overstates up-size mean)

| level | geometry | action | scope | L6M maxDD cell/ref (cut%) | cut% HOLD/PRE/X' | equal-mean cut% L6M/PRE/X' | worst-20 L6M cell/ref | d mean $/wk L6M | touched % | placebo p L6M/PRE | p family own/max (lf-max) | WF | live wk d$ | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| maxsz_w300 | BH-present:B20/s-1 | up1.5 | s:asia | 78318/79907 (2.0) | -34.4/-5.8/-5.7 | 37/32/32 | 335201/165224 | 11833 | 28.7 | 0.02/0.92 | 0.92/1.00 | ok | n/a | UP (report, never promoted) |
| maxsz_w900 | BH-present:B10/s-1 | up1.5 | ALL | 86459/79907 (-8.2) | -31.0/-12.4/-2.1 | 30/27/34 | 329764/165224 | 11927 | 48.4 | 0.01/0.09 | 0.09/1.00 | ok | n/a | UP (report, never promoted) |
| maxsz_w300 | BH-present:B5/s-1 | up1.5 | s:asia | 64954/79907 (18.7) | -26.5/3.8/-5.5 | 42/32/25 | 331691/165224 | 8907 | 16.8 | 0.01/0.55 | 0.55/1.00 | ok | n/a | UP (report, never promoted) |
| maxsz_w900 | BH-present:B20/s-1 | up1.5 | s:asia | 84577/79907 (-5.8) | -46.1/-3.0/-2.1 | 24/26/27 | 296212/165224 | 8674 | 26.1 | 0.28/0.89 | 0.89/1.00 | ok | n/a | UP (report, never promoted) |
| swp_w300_t6 | BH-present:B5/s-1 | up1.5 | s:asia | 91978/79907 (-15.1) | -38.3/9.6/-3.1 | 22/39/30 | 320070/165224 | 11150 | 26.1 | 0.71/0.30 | 0.71/1.00 | ok | n/a | UP (report, never promoted) |
| swp_w900_t6 | BH-present:B5/s-1 | up1.5 | s:asia | 91945/79907 (-15.1) | -47.7/10.4/-22.2 | 25/42/21 | 348490/165224 | 12660 | 29.3 | 0.62/0.25 | 0.62/1.00 | ok | n/a | UP (report, never promoted) |
| swp_w900_t6 | BH-present:B20/s-1 | up1.5 | s:asia | 91945/79907 (-15.1) | -41.7/6.2/-24.0 | 26/40/20 | 357982/165224 | 13039 | 31.2 | 0.62/0.61 | 0.62/1.00 | ok | n/a | UP (report, never promoted) |
| swp_w900_t6 | BH-present:B5/s-1 | up1.5 | bs:PE:asia | 84101/79907 (-5.2) | -17.4/3.4/-1.0 | 20/27/23 | 248559/165224 | 7384 | 9.5 | 0.37/0.36 | 0.37/1.00 | ok | n/a | UP (report, never promoted) |

## 3. By scope: the best down-only cell per book / session / book x session (gain > 0 over the group-wide action; else the table says none)

| level | geometry | action | scope | L6M maxDD cell/ref (cut%) | cut% HOLD/PRE/X' | equal-mean cut% L6M/PRE/X' | worst-20 L6M cell/ref | d mean $/wk L6M | touched % | placebo p L6M/PRE | p family own/max (lf-max) | WF | live wk d$ | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| swp_w900_t6 | AH:A1/s-1/any/any | half | ALL | 42386/79907 (47.0) | 25.2/40.7/41.9 | 41/35/36 | 208413/165224 | -2104 | 67.0 | 0.01/0.10 | 0.10/1.00 | ok | -26379 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK |
| wall_k3_p15 | AH:A1/s-1/any/any | skip | b:HM | 79907/79907 (0.0) | 0.0/0.0/2.2 | 1/1/3 | 165015/165224 | 169 | 0.3 | 0.47/0.18 | 0.47/1.00 | ok | n/a | no |
| ice_w120_n2 | AH:D10/s-1/any/any | skip | b:KB | 77128/79907 (3.5) | -6.0/2.9/9.0 | 5/4/10 | 170805/165224 | 287 | 14.6 | 0.35/0.78 | 0.78/1.00 | no | -7955 | LEAD |
| swp_w900_t6 | AH:D10/s-1/any/any | skip | b:MV | 63343/79907 (20.7) | 11.8/10.1/9.9 | 27/17/17 | 243062/165224 | 2184 | 13.7 | 0.01/0.27 | 0.27/1.00 | ok | -7990 | LEAD |
| maxsz_w900 | AH:D90/s8/any/any | skip | b:OD | 79907/79907 (0.0) | -1.8/0.0/-0.3 | 1/1/1 | 166550/165224 | 299 | 1.1 | 0.34/0.57 | 0.57/1.00 | ok | n/a | no |
| dpiv_w900 | AH:A0.5/s-1/any/any | skip | b:PB | 79760/79907 (0.2) | 2.9/0.1/1.3 | 1/1/2 | 168196/165224 | 172 | 0.9 | 0.30/0.30 | 0.30/1.00 | no | -270 | LEAD |
| ice_w600_n1 | AH:D20/s-1/any/any | quarter | b:PE | 39738/79907 (50.3) | -3.1/52.8/57.0 | 35/38/44 | 148329/165224 | -5339 | 21.9 | 0.02/0.05 | 0.05/1.00 | no | -64405 | LEAD |
| maxsz_w300 | BH-absent:B20 | skip | b:SM | 76232/79907 (4.6) | 3.7/10.4/9.2 | 5/10/9 | 148038/165224 | 7 | 1.3 | 0.22/0.06 | 0.22/1.00 | ok | 1350 | LEAD |
| abs_w900_v2 | AH:A1/s6/any/any | skip | s:asia | 79907/79907 (0.0) | 0.0/0.0/3.7 | 2/2/6 | 178306/165224 | 523 | 0.2 | 0.49/0.70 | 0.70/1.00 | ok | 0 | no |
| ice_w600_n1 | AH:A0.5/s-1/any/any | quarter | s:london | 54636/79907 (31.6) | -32.2/43.1/30.6 | 35/46/34 | 211649/165224 | 1185 | 26.4 | 0.06/0.30 | 0.30/1.00 | no | 3873 | LEAD |
| maxsz_w900 | BH-absent:B5 | skip | s:nyam | 75266/79907 (5.8) | 11.8/11.0/35.2 | 9/14/38 | 269990/165224 | 982 | 22.3 | 0.37/0.58 | 0.58/1.00 | ok | -25205 | LEAD |
| swp_w900_t12 | BH-absent:B20 | skip | s:nypm | 78609/79907 (1.6) | 0.0/7.6/5.2 | 2/8/5 | 170388/165224 | 15 | 1.3 | 0.23/0.03 | 0.23/1.00 | ok | 640 | LEAD |
| wall_k5_p15 | AH:A1/s-1/any/any | skip | bs:HM:asia | 79907/79907 (0.0) | 0.0/0.0/1.0 | 1/1/2 | 165015/165224 | 169 | 0.1 | 0.74/0.72 | 0.74/1.00 | ok | n/a | no |
| maxsz_w900 | AH:D5/s8/any/any | skip | bs:HM:nyam | 79907/79907 (0.0) | 0.0/0.0/0.6 | 0/0/1 | 166420/165224 | 48 | 0.2 | 0.44/0.69 | 0.69/1.00 | ok | n/a | no |
| ice_w600_n2 | BH-absent:B20 | skip | bs:KB:asia | 79248/79907 (0.8) | 0.6/4.5/4.9 | 4/8/8 | 182968/165224 | 799 | 2.0 | 0.10/0.08 | 0.10/1.00 | no | -490 | LEAD |
| ice_w120_n4 | BH-absent:B5 | skip | bs:KB:london | 75500/79907 (5.5) | 10.2/9.1/5.1 | 7/10/6 | 160302/165224 | 354 | 8.1 | 0.14/0.56 | 0.56/1.00 | no | 195 | LEAD |
| ice_w120_n2 | AH:D10/s-1/any/any | skip | bs:KB:nyam | 80754/79907 (-1.1) | -3.3/-0.9/-1.6 | 2/2/2 | 181328/165224 | 742 | 5.6 | 0.12/0.86 | 0.86/1.00 | no | n/a | no |
| swp_w900_t12 | BH-absent:B20 | skip | bs:KB:nypm | 78609/79907 (1.6) | 0.0/7.6/5.2 | 2/8/5 | 170388/165224 | 15 | 1.3 | 0.19/0.01 | 0.19/1.00 | ok | 640 | LEAD |
| swp_w900_t6 | AH:D10/s-1/any/any | skip | bs:MV:london | 69549/79907 (13.0) | 6.6/8.3/3.7 | 18/13/9 | 212804/165224 | 1514 | 7.1 | 0.11/0.52 | 0.52/1.00 | ok | -6810 | LEAD |
| maxsz_w300 | BH-absent:B5 | skip | bs:MV:nyam | 80312/79907 (-0.5) | 2.3/0.9/5.4 | 4/5/10 | 193322/165224 | 1097 | 6.2 | 0.33/0.39 | 0.39/1.00 | ok | n/a | no |
| maxsz_w900 | AH:D90/s8/any/any | skip | bs:OD:nyam | 79907/79907 (0.0) | -1.8/0.0/-0.3 | 1/1/1 | 166550/165224 | 299 | 1.1 | 0.31/0.57 | 0.57/1.00 | ok | n/a | no |
| dpiv_w900 | AH:A0.5/s-1/any/any | skip | bs:PB:asia | 79760/79907 (0.2) | 2.9/0.1/1.3 | 1/1/2 | 168196/165224 | 172 | 0.9 | 0.23/0.14 | 0.23/1.00 | no | -270 | LEAD |
| abs_w900_v4 | AH:A1/s6/any/any | skip | bs:PE:asia | 79907/79907 (0.0) | 0.0/0.0/0.0 | 2/2/2 | 175223/165224 | 400 | 0.1 | 0.85/0.86 | 0.86/1.00 | ok | 0 | no |
| swp_w900_t6 | AH:A0.5/s-1/any/any | skip | bs:PE:london | 58285/79907 (27.1) | -31.3/41.9/39.2 | 33/46/44 | 194847/165224 | 1856 | 6.0 | 0.18/0.34 | 0.34/1.00 | ok | -385 | LEAD |
| (none) | | | bs:PE:nyam | no cell beats the group-wide action | | | | | | | | | | |
| maxsz_w300 | AH:D5/s8/tch0/any | skip | bs:SM:asia | 79907/79907 (0.0) | 0.0/0.0/0.6 | 0/0/1 | 167586/165224 | 94 | 0.1 | 0.71/0.96 | 0.96/1.00 | ok | n/a | no |
| ice_w120_n2 | BH-absent:B20 | skip | bs:SM:london | 70626/79907 (11.6) | -0.5/12.0/18.4 | 15/15/21 | 177810/165224 | 796 | 1.6 | 0.10/0.12 | 0.12/1.00 | no | 120 | LEAD |

## 4. Purged monthly walk-forward of the picking procedure (per level family; OOS 2024-01..2026-10; all-weeks maxDD)

| level family | cells | house WF cut% | house WF mean $/wk | retention-constrained WF cut% | mean $/wk | ref mean $/wk | worst-20 WF / ref | equal-mean-free Calmar picker cut% |
|---|---|---|---|---|---|---|---|---|
| abs | 5097 | 99.5 | 28 | 30.1 | 12850 | 16574 | -820454/-1086950 | 31.9 |
| dpiv | 1213 | 35.0 | 4301 | -27.8 | 12868 | 16574 | -1000498/-1086950 | 32.8 |
| ice | 4156 | 40.3 | 1799 | -12.4 | 10339 | 16574 | -824121/-1086950 | 24.1 |
| maxsz | 5563 | 22.8 | 5283 | 21.6 | 11162 | 16574 | -918013/-1086950 | -1.5 |
| swp | 5133 | 52.8 | 6957 | 39.6 | 13044 | 16574 | -764068/-1086950 | 41.5 |
| wall | 9731 | 98.7 | 74 | 17.5 | 11153 | 16574 | -857744/-1086950 | 37.7 |

## 6. Learned layer: monotone small tree / small GBDT (<= 8 leaves) over causal zone features of A,B,G,F (lv_*.parquet) -> skip/half/full (FIRST-ORDER, purged monthly expanding WF 2024-01..2026-10, 7-day embargo, 3 seeds, family null = pnl permuted within book x session x month, 20 draws)

Features: nearest level ahead/behind in ATR, touches, age, strength, confluence, #levels in path per family (monotone: farther ahead -> better, closer support behind -> better), 7 representative F level sets, session, book, side, ER, ATR, lots. Action by the percentile of the prediction within the training predictions (bottom q_h% halved, bottom q_s% skipped). L6M/HOLD/PRE are fully OOS; X' is training-era (not scored). Re-target-distance learning needs path-level exact runs: queued.

| model | best policy (halve bottom q_h% / skip bottom q_s%) | equal-lots cut L6M/HOLD/PRE | equal-mean cut L6M/HOLD/PRE | d mean $/wk L6M/PRE | lots-changed trades | seed values of the equal-mean min | null (20 draws) 90th/max | family p | verdict |
|---|---|---|---|---|---|---|---|---|---|
| tree | 10/0 | -1.1/18.8/6.0 | 2.8/21.9/9.7 | 1023/-387 | 876 | -10/-8/-18 | 21.4/28.0 | 0.71 | no (null reaches it) |
| gbdt | 50/5 | 17.6/13.0/29.9 | 22.6/18.3/34.2 | 1538/-2140 | 3439 | 0/2/-16 | 13.3/20.4 | 0.10 | LEAD (own p<=.10 only) |

Single-level comparator (same OOS months, retention-constrained purged WF picker per level family; equal-mean cut on the OOS daily series):

| level family | equal-mean cut L6M/HOLD/PRE | min | d mean $/wk L6M |
|---|---|---|---|
| abs | -23.8/-36.1/0.9 | -36.1 | -6424 |
| dpiv | -20.7/-115.4/25.1 | -115.4 | -3830 |
| ice | -47.1/-62.6/-67.0 | -67.0 | -7334 |
| maxsz | -28.3/-50.6/2.3 | -50.6 | -6114 |
| swp | -12.7/9.5/24.2 | -12.7 | -4548 |
| wall | -64.9/-43.3/4.0 | -64.9 | -4554 |

Verdict: GBDT best-policy statistic 18.3 vs best single-level WF -12.7; own-null family p 0.10. The GBDT beats the best single-level WF in the minimum equal-mean cut and its null p is <= .10: a LEAD only (first-order, PRE-PROOF).
Caveat: the three seeds of the GBDT best policy give equal-mean minima 0/2/-16 (seed instability: the bootstrap of the training rows changes which trades are halved); the ensemble value above is the mean of the three seeds' predictions. The single-level WF comparator is negative at equal mean OOS: the in-sample cell cuts do not survive the picking procedure.


## Next (queue)

- exact engine top-5 per level family (set files by SZ-CORE queue); state-cut arm widening/tightening when a support sits just behind the adverse extreme (own subclass, cde_exact pattern); shifted-level / shuffled-day placebos for the top cells; control bases S1b-NOCUT / S1b-UNIF re-scoring; tree layer (section 6) over A..G + F features.
