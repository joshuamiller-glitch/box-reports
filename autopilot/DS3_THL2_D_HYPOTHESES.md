# DS3_THL2_D_HYPOTHESES - H1-H11 as named cell families (L2H, 2026-10-29)

Research only; UNTOUCHED never read (store max label day 20260206; HOLD capped). Prereg: l2vast/ds3/prereg/THL2_D_prereg.md (stage 1 sha256 eb2d615f..., amendment A1 for H4,H5,H7,H10 sha256 08c15545..., both in DECISIONS.md, logged before the cells they cover were scored; H11 was in the stage-1 prereg). 448 cells in total (stage 1: 326, stage 2: 102, stage 3 H12: 20). Data: 10-s decision rows of the 10 static-bracket books (CR excluded), MEASURED fills (market 0.995 pt, tightened stop 1.01 pt, exit at the 10-s close, conservative), paired vs the same trade held to the bracket (profit) / held to the stop (loss). Walk-forward: the cell is chosen on PRE (X and HOLD never used for selection) and, separately, by re-fitting chains (window 3m/12m/ew10, weekly, pooled or per book) on closed trades only. Placebo: L2 columns of another trade of the same label day (10 draws, whole family re-run, best-of-family PRE mean ranked against the real best); H11 path arm: random cuts at the same rate (10 draws). MDE = 2.8 SE with trade clusters (label day x session). RC = White reality check on PRE daily sums (family), over all 428 cells p = 0.73.

## RECENT WINDOWS FIRST (user directive 2026-10-29, part 5)

Windows: **2026 = 2026-01-01..2026-02-06, about 5 weeks and ~25 trading days, so every 2026 number below has an MDE (2.8 SE, trade clusters) of 1-4 pts and is mostly noise**; **last 6 months (L6M) = 2025-08-01..2026-02-06**; HOLD = 2025-07-01..2026-02-06 (nearly the same as L6M plus July 2025); PRE = 2024-02..2025-06; X = 2023-07..2024-01. Numbers are pts per trade of the book vs hold, MEASURED fills, net of cost in both arms. Per family, cells are ranked by L6M with HOLD as tie-break; **ranking and reading L6M on the same data is in-sample for the recent window**, so the rank-1 cell is shown beside the PRE-selected cell (the only out-of-sample choice). CANDIDATE-RECENT = a cell positive in 2026 AND in L6M (label only; gates unchanged; not a V2 tier).

**43 of 428 cells carry CANDIDATE-RECENT**; with ~5 weeks in 2026 (MDE 1-4 pts) a positive 2026 is nearly uninformative, and the labelled cells sit almost entirely in the "take winners" families (H7P, H8P, H6P, H1P, H4P) plus a few H11/H3 cells; none of them passes the unchanged gates (see the verdict ladder above).

| family | rank-1 by L6M | 2026 [n fired] (MDE) | L6M [n fired] (MDE) | HOLD | PRE | X | #CAND-RECENT / cells | PRE-selected cell: 2026 / L6M |
|---|---|---|---|---|---|---|---|---|
| H10|P | H10P|mfe20|trail4|price | +0.01 [1686] (4.5) | -0.32 [7257] (2.2) | +0.00 | -0.51 | -0.45 | 0/12 | -0.01 / -0.34 |
| H11b|L | H11|mfe30|d10|T120|book | +0.65 [307] (1.7) | +0.16 [1382] (0.9) | +0.01 | -0.30 | -0.62 | 4/60 | +0.33 / +0.05 |
| H11p|L | H11|mfe30|d10|T120|path | +0.29 [404] (2.2) | +0.03 [1717] (1.0) | -0.07 | -0.31 | -0.29 | 1/60 | -0.68 / -0.51 |
| H1|P | H1P|pct0.7|k2|take | +0.24 [299] (1.1) | +0.13 [1320] (0.4) | +0.17 | +0.09 | -0.12 | 4/18 | +0.24 / +0.13 |
| H2|L | H2L|behind4|k1.5 | -1.82 [433] (2.1) | -0.23 [1829] (0.9) | -0.20 | -0.28 | +0.23 | 0/7 | -2.04 / -0.24 |
| H2|P | H2P|behind8|k3 | -0.73 [1469] (4.4) | -0.82 [6431] (2.1) | -0.48 | -0.67 | -0.51 | 0/7 | -0.82 / -0.86 |
| H3|L | H3L|mae20|imb0.5|T30|cut | +0.24 [13] (0.3) | -0.02 [134] (0.3) | -0.02 | -0.16 | +0.05 | 0/24 | +0.30 / -0.25 |
| H3|P | H3P|mfe20|imb0.5|T30|take | +0.28 [28] (0.6) | +0.00 [184] (0.4) | -0.04 | -0.12 | -0.33 | 1/24 | -0.45 / -0.75 |
| H4|L | H4L|mae20|cons15|refill2|tt3 | -0.06 [15] (0.3) | -0.10 [160] (0.2) | -0.06 | -0.06 | +0.27 | 0/24 | -0.03 / -0.12 |
| H4|P | H4P|mfe20|cons15|refill4|take | +0.03 [80] (0.8) | +0.25 [917] (0.7) | +0.38 | -0.21 | +0.18 | 7/24 | +0.18 / +0.07 |
| H5|L | H5L|with-veto | -0.33 [96] (0.8) | -0.09 [372] (0.4) | -0.09 | -0.11 | -0.08 | 0/5 | -0.33 / -0.09 |
| H5|P | H5P|against|mfe20|take | +0.14 [1714] (4.5) | -0.03 [7352] (2.2) | +0.26 | -0.26 | -0.16 | 0/5 | +0.14 / -0.03 |
| H6|L | H6L|mae20|pul1000|cut | -1.35 [754] (3.1) | -0.41 [3525] (1.5) | -0.39 | -0.53 | +0.14 | 0/24 | -1.61 / -0.63 |
| H6|P | H6P|mfe20|pul500|take | +0.69 [1199] (3.5) | +0.43 [5165] (1.7) | +0.57 | +0.02 | +0.78 | 3/18 | +0.69 / +0.43 |
| H7|L | H7L|mae20|against30|n3|tt3 | -2.31 [1416] (4.0) | -1.42 [6233] (1.9) | -0.92 | -1.00 | -0.13 | 0/16 | -3.02 / -1.64 |
| H7|P | H7P|pct0.7|with10|n3|take | +1.26 [1276] (2.4) | +0.89 [5426] (1.0) | +0.97 | +0.43 | +0.09 | 13/16 | +1.26 / +0.89 |
| H8|L | H8L|thin0.5|mae20|tt6 | -0.18 [337] (1.5) | -0.16 [1616] (0.7) | -0.23 | -0.09 | +0.18 | 0/15 | -1.81 / -0.23 |
| H8|P | H8P|thin0.7|pct0.5|take | +1.25 [872] (2.4) | +0.90 [3571] (1.1) | +0.75 | +0.39 | -0.81 | 10/15 | +1.25 / +0.90 |
| H9|L | H9L|mae20|m300|flip3|tt3 | -0.48 [1010] (3.0) | -1.20 [4705] (1.6) | -0.89 | -0.85 | -0.34 | 0/36 | -2.29 / -1.76 |
| H9|P | H9P|mfe20|m0|take | -0.34 [1602] (4.5) | -0.33 [6995] (2.2) | -0.03 | -0.58 | -0.46 | 0/18 | -0.35 / -0.36 |

Cells labelled CANDIDATE-RECENT (top 12 by L6M): H8P|thin0.7|pct0.5|take (2026 +1.25, L6M +0.90, HOLD +0.75, PRE +0.39, X -0.81); H7P|pct0.7|with10|n3|take (2026 +1.26, L6M +0.89, HOLD +0.97, PRE +0.43, X +0.09); H7P|pct0.7|with10|n1|take (2026 +1.24, L6M +0.87, HOLD +0.96, PRE +0.40, X +0.12); H7P|pct0.7|with30|n1|take (2026 +1.25, L6M +0.86, HOLD +0.95, PRE +0.39, X +0.12); H7P|pct0.7|with30|n3|take (2026 +1.15, L6M +0.80, HOLD +0.90, PRE +0.40, X +0.14); H8P|thin0.7|pct0.5|tr4 (2026 +0.87, L6M +0.62, HOLD +0.50, PRE +0.05, X -0.75); H7P|pct0.5|with30|n3|take (2026 +0.74, L6M +0.60, HOLD +0.60, PRE +0.09, X -0.44); H7P|pct0.5|with10|n3|take (2026 +0.48, L6M +0.59, HOLD +0.58, PRE +0.11, X -0.55); H7P|pct0.5|with30|n1|take (2026 +0.68, L6M +0.59, HOLD +0.59, PRE +0.11, X -0.41); H7P|pct0.5|with10|n1|take (2026 +0.68, L6M +0.57, HOLD +0.57, PRE +0.11, X -0.44); H8P|thin0.7|pct0.5|tr8 (2026 +0.80, L6M +0.44, HOLD +0.33, PRE -0.00, X -0.62); H6P|mfe20|pul500|take (2026 +0.69, L6M +0.43, HOLD +0.57, PRE +0.02, X +0.78).

Reading: the recent windows do not change a verdict. H7P/H8P/H6P (take winners) are the only families with a clearly positive L6M (+0.4..+0.9) and a positive 2026 (+0.7..+1.3, n of 2026 fired a few hundred, MDE >1.5), the same cells that were LEAD; H7P/H8P are explained by the plain path rule (take at 70% of the way). Loss-side L2 rules (H2L, H6L, H7L, H8L, H9L) are negative in L6M for every cell; H11 cells are positive only in 2026 for a few long-T book arms (best L6M +0.16 [book arm], 2026 +0.78) and negative in X/PRE.

### Walk-forward chain: settings chosen by quarter (12m window, pooled, weekly re-fit; modal cell among trades entering that quarter; active = share of trades in the quarter with any cell chosen; mean = chain pts/trade of the book in that quarter). 3m-window version: chain_by_quarter.csv

* **H10|P**: 2024-Q1 H10P|mfe20|trail12|micro (act 90%, -1.99); 2024-Q2 H10P|mfe20|trail12|micro (act 46%, -0.05); 2024-Q3 (hold: nothing chosen) (act 0%, +0.00); 2024-Q4 (hold: nothing chosen) (act 0%, +0.00); 2025-Q1 (hold: nothing chosen) (act 0%, +0.00); 2025-Q2 (hold: nothing chosen) (act 0%, +0.00); 2025-Q3 (hold: nothing chosen) (act 0%, +0.00); 2025-Q4 H10P|mfe20|trail4|price (act 22%, -0.32); 2026-Q1 H10P|mfe20|trail4|price (act 82%, -0.73)
* **H11b|L**: 2024-Q1 H11|mfe20|d5|T30|book (act 100%, -0.50); 2024-Q2 H11|mfe30|d0|T60|book (act 38%, -0.07); 2024-Q3 (hold: nothing chosen) (act 0%, +0.00); 2024-Q4 H11|mfe20|d5|T300|book (act 91%, -0.20); 2025-Q1 H11|mfe20|d5|T300|book (act 23%, -0.18); 2025-Q2 (hold: nothing chosen) (act 0%, +0.00); 2025-Q3 (hold: nothing chosen) (act 0%, +0.00); 2025-Q4 (hold: nothing chosen) (act 0%, +0.00); 2026-Q1 (hold: nothing chosen) (act 0%, +0.00)
* **H11p|L**: 2024-Q1 H11|mfe20|d10|T10|path (act 100%, -0.52); 2024-Q2 H11|mfe30|d0|T10|path (act 59%, -0.48); 2024-Q3 (hold: nothing chosen) (act 0%, +0.00); 2024-Q4 H11|mfe20|d10|T300|path (act 91%, -0.38); 2025-Q1 H11|mfe20|d10|T300|path (act 18%, -0.03); 2025-Q2 (hold: nothing chosen) (act 0%, +0.00); 2025-Q3 (hold: nothing chosen) (act 0%, +0.00); 2025-Q4 (hold: nothing chosen) (act 0%, +0.00); 2026-Q1 (hold: nothing chosen) (act 0%, +0.00)
* **H1|P**: 2024-Q1 H1P|pct0.7|k3|take (act 100%, -0.24); 2024-Q2 H1P|pct0.5|k2|tr8 (act 100%, +0.52); 2024-Q3 H1P|pct0.5|k3|tr8 (act 100%, -0.60); 2024-Q4 H1P|pct0.7|k3|tr8 (act 78%, -0.08); 2025-Q1 H1P|pct0.7|k2|take (act 52%, +0.02); 2025-Q2 H1P|pct0.7|k2|take (act 1%, +0.10); 2025-Q3 H1P|pct0.7|k2|take (act 100%, -0.04); 2025-Q4 H1P|pct0.7|k2|take (act 100%, +0.28); 2026-Q1 H1P|pct0.7|k2|take (act 100%, +0.24)
* **H2|L**: 2024-Q1 H2L|behind8|k1.5 (act 100%, +0.30); 2024-Q2 H2L|behind8|k1.5 (act 100%, +0.31); 2024-Q3 H2L|behind4|k1.5 (act 57%, -0.68); 2024-Q4 (hold: nothing chosen) (act 0%, +0.00); 2025-Q1 H2L|behind8|k1.5 (act 7%, -0.13); 2025-Q2 (hold: nothing chosen) (act 0%, +0.00); 2025-Q3 (hold: nothing chosen) (act 0%, +0.00); 2025-Q4 H2L|behind8|k1.5 (act 7%, -0.00); 2026-Q1 (hold: nothing chosen) (act 0%, +0.00)
* **H2|P**: 2024-Q1 H2P|behind8|k1.5 (act 86%, -2.35); 2024-Q2 H2P|behind8|k1.5 (act 29%, +0.03); 2024-Q3 (hold: nothing chosen) (act 0%, +0.00); 2024-Q4 (hold: nothing chosen) (act 0%, +0.00); 2025-Q1 (hold: nothing chosen) (act 0%, +0.00); 2025-Q2 (hold: nothing chosen) (act 0%, +0.00); 2025-Q3 (hold: nothing chosen) (act 0%, +0.00); 2025-Q4 (hold: nothing chosen) (act 0%, +0.00); 2026-Q1 (hold: nothing chosen) (act 0%, +0.00)
* **H3|L**: 2024-Q1 H3L|mae10|imb0.5|T10|tt3 (act 100%, +0.44); 2024-Q2 H3L|mae20|imb0.3|T10|cut (act 100%, -0.43); 2024-Q3 H3L|mae20|imb0.3|T30|cut (act 100%, -0.50); 2024-Q4 H3L|mae20|imb0.3|T10|cut (act 100%, -1.17); 2025-Q1 H3L|mae20|imb0.5|T10|tt3 (act 100%, -0.14); 2025-Q2 H3L|mae10|imb0.5|T10|tt6 (act 100%, -0.21); 2025-Q3 H3L|mae10|imb0.5|T10|tt6 (act 89%, -0.09); 2025-Q4 (hold: nothing chosen) (act 0%, +0.00); 2026-Q1 (hold: nothing chosen) (act 0%, +0.00)
* **H3|P**: 2024-Q1 H3P|mfe20|imb0.5|T10|take (act 31%, -0.27); 2024-Q2 (hold: nothing chosen) (act 0%, +0.00); 2024-Q3 (hold: nothing chosen) (act 0%, +0.00); 2024-Q4 H3P|mfe20|imb0.5|T30|tr8 (act 6%, +0.00); 2025-Q1 (hold: nothing chosen) (act 0%, +0.00); 2025-Q2 (hold: nothing chosen) (act 0%, +0.00); 2025-Q3 (hold: nothing chosen) (act 0%, +0.00); 2025-Q4 (hold: nothing chosen) (act 0%, +0.00); 2026-Q1 (hold: nothing chosen) (act 0%, +0.00)
* **H4|L**: 2024-Q1 H4L|mae20|cons8|refill2|cut (act 100%, -0.08); 2024-Q2 H4L|mae10|cons15|refill2|cut (act 100%, -0.36); 2024-Q3 H4L|mae20|cons15|refill2|cut (act 100%, +0.12); 2024-Q4 H4L|mae20|cons15|refill2|cut (act 100%, -1.16); 2025-Q1 H4L|mae20|cons15|refill2|cut (act 38%, -0.21); 2025-Q2 (hold: nothing chosen) (act 0%, +0.00); 2025-Q3 H4L|mae10|cons15|refill2|cut (act 25%, -0.18); 2025-Q4 (hold: nothing chosen) (act 0%, +0.00); 2026-Q1 H4L|mae10|cons8|refill2|tt3 (act 29%, -0.08)
* **H4|P**: 2024-Q1 H4P|mfe20|cons8|refill4|take (act 100%, -0.91); 2024-Q2 H4P|mfe20|cons15|refill4|take (act 100%, +0.20); 2024-Q3 H4P|mfe10|cons8|refill2|take (act 100%, -1.18); 2024-Q4 H4P|mfe10|cons15|refill2|take (act 100%, -0.43); 2025-Q1 H4P|mfe10|cons15|refill2|take (act 100%, +0.04); 2025-Q2 H4P|mfe20|cons15|refill2|take (act 28%, -0.01); 2025-Q3 H4P|mfe20|cons3|refill2|take (act 62%, -0.05); 2025-Q4 H4P|mfe20|cons8|refill4|take (act 100%, +0.11); 2026-Q1 H4P|mfe20|cons8|refill4|take (act 100%, -0.24)
* **H5|L**: 2024-Q1 H5L|against|mae20|tt3 (act 90%, -1.06); 2024-Q2 H5L|against|mae20|tt3 (act 12%, -0.37); 2024-Q3 (hold: nothing chosen) (act 0%, +0.00); 2024-Q4 (hold: nothing chosen) (act 0%, +0.00); 2025-Q1 (hold: nothing chosen) (act 0%, +0.00); 2025-Q2 (hold: nothing chosen) (act 0%, +0.00); 2025-Q3 (hold: nothing chosen) (act 0%, +0.00); 2025-Q4 (hold: nothing chosen) (act 0%, +0.00); 2026-Q1 (hold: nothing chosen) (act 0%, +0.00)
* **H5|P**: 2024-Q1 H5P|against|mfe20|take (act 100%, -1.74); 2024-Q2 H5P|against|mfe20|take (act 46%, +0.16); 2024-Q3 (hold: nothing chosen) (act 0%, +0.00); 2024-Q4 (hold: nothing chosen) (act 0%, +0.00); 2025-Q1 (hold: nothing chosen) (act 0%, +0.00); 2025-Q2 (hold: nothing chosen) (act 0%, +0.00); 2025-Q3 H5P|against|mfe20|take (act 79%, -0.71); 2025-Q4 H5P|against|mfe20|take (act 59%, +0.36); 2026-Q1 H5P|against|mfe20|take (act 100%, +0.14)
* **H6|L**: 2024-Q1 H6L|mae20|pul1000|tt3 (act 90%, -0.87); 2024-Q2 H6L|mae20|pul500|cut (act 20%, -0.40); 2024-Q3 (hold: nothing chosen) (act 0%, +0.00); 2024-Q4 H6L|mae20|pul150|tt6 (act 14%, +0.07); 2025-Q1 (hold: nothing chosen) (act 0%, +0.00); 2025-Q2 (hold: nothing chosen) (act 0%, +0.00); 2025-Q3 H6L|mae20|pul500|tt6 (act 21%, -0.13); 2025-Q4 (hold: nothing chosen) (act 0%, +0.00); 2026-Q1 (hold: nothing chosen) (act 0%, +0.00)
* **H6|P**: 2024-Q1 H6P|mfe20|pul500|tr8 (act 100%, -0.99); 2024-Q2 H6P|mfe20|pul500|tr8 (act 100%, +0.19); 2024-Q3 H6P|mfe20|pul500|take (act 78%, -1.15); 2024-Q4 H6P|mfe20|pul500|take (act 14%, +0.14); 2025-Q1 (hold: nothing chosen) (act 0%, +0.00); 2025-Q2 (hold: nothing chosen) (act 0%, +0.00); 2025-Q3 H6P|mfe20|pul500|take (act 95%, -0.05); 2025-Q4 H6P|mfe20|pul500|take (act 83%, +0.72); 2026-Q1 H6P|mfe20|pul500|take (act 100%, +0.69)
* **H7|L**: 2024-Q1 H7L|mae20|against10|n3|tt3 (act 78%, -1.04); 2024-Q2 H7L|mae20|against10|n3|tt3 (act 12%, -0.35); 2024-Q3 (hold: nothing chosen) (act 0%, +0.00); 2024-Q4 (hold: nothing chosen) (act 0%, +0.00); 2025-Q1 (hold: nothing chosen) (act 0%, +0.00); 2025-Q2 (hold: nothing chosen) (act 0%, +0.00); 2025-Q3 (hold: nothing chosen) (act 0%, +0.00); 2025-Q4 (hold: nothing chosen) (act 0%, +0.00); 2026-Q1 (hold: nothing chosen) (act 0%, +0.00)
* **H7|P**: 2024-Q1 H7P|pct0.7|with10|n1|take (act 100%, -0.92); 2024-Q2 H7P|pct0.7|with30|n3|take (act 100%, +0.45); 2024-Q3 H7P|pct0.7|with30|n3|take (act 9%, -0.51); 2024-Q4 (hold: nothing chosen) (act 0%, +0.00); 2025-Q1 H7P|pct0.7|with10|n3|take (act 50%, +0.29); 2025-Q2 H7P|pct0.7|with10|n3|take (act 100%, +1.56); 2025-Q3 H7P|pct0.7|with10|n1|take (act 100%, +0.95); 2025-Q4 H7P|pct0.7|with10|n3|take (act 100%, +0.86); 2026-Q1 H7P|pct0.7|with10|n3|take (act 100%, +1.23)
* **H8|L**: 2024-Q1 H8L|thickveto1.25 (act 100%, +0.42); 2024-Q2 H8L|thickveto1.25 (act 100%, +0.01); 2024-Q3 H8L|thin0.5|mae20|tt6 (act 93%, -0.51); 2024-Q4 H8L|thin0.5|mae20|tt6 (act 100%, +0.28); 2025-Q1 H8L|thin0.5|mae20|tt6 (act 45%, -0.40); 2025-Q2 (hold: nothing chosen) (act 0%, +0.00); 2025-Q3 H8L|thickveto1.25 (act 45%, -0.21); 2025-Q4 H8L|thickveto1.25 (act 38%, -0.07); 2026-Q1 H8L|thickveto1.25 (act 18%, -0.06)
* **H8|P**: 2024-Q1 H8P|thickveto1.25 (act 100%, -0.83); 2024-Q2 H8P|thin0.5|pct0.25|take (act 94%, -0.42); 2024-Q3 H8P|thin0.5|pct0.5|take (act 85%, -0.28); 2024-Q4 H8P|thin0.5|pct0.5|take (act 89%, -0.36); 2025-Q1 H8P|thin0.7|pct0.5|take (act 69%, +0.16); 2025-Q2 H8P|thin0.7|pct0.5|take (act 100%, +1.28); 2025-Q3 H8P|thin0.7|pct0.5|take (act 100%, +0.32); 2025-Q4 H8P|thin0.7|pct0.5|take (act 100%, +0.81); 2026-Q1 H8P|thin0.7|pct0.5|take (act 100%, +1.25)
* **H9|L**: 2024-Q1 H9L|mae20|m300|flip3|tt3 (act 37%, -0.66); 2024-Q2 (hold: nothing chosen) (act 0%, +0.00); 2024-Q3 (hold: nothing chosen) (act 0%, +0.00); 2024-Q4 H9L|mae20|m0|flip2|tt3 (act 21%, +0.04); 2025-Q1 (hold: nothing chosen) (act 0%, +0.00); 2025-Q2 (hold: nothing chosen) (act 0%, +0.00); 2025-Q3 (hold: nothing chosen) (act 0%, +0.00); 2025-Q4 (hold: nothing chosen) (act 0%, +0.00); 2026-Q1 (hold: nothing chosen) (act 0%, +0.00)
* **H9|P**: 2024-Q1 H9P|mfe20|m0|tr8 (act 100%, -1.24); 2024-Q2 H9P|mfe20|m300|tr8 (act 46%, -0.07); 2024-Q3 (hold: nothing chosen) (act 0%, +0.00); 2024-Q4 (hold: nothing chosen) (act 0%, +0.00); 2025-Q1 (hold: nothing chosen) (act 0%, +0.00); 2025-Q2 (hold: nothing chosen) (act 0%, +0.00); 2025-Q3 (hold: nothing chosen) (act 0%, +0.00); 2025-Q4 H9P|mfe20|m0|take (act 22%, -0.32); 2026-Q1 H9P|mfe20|m0|take (act 82%, -0.94)

### Last walk-forward re-fit in full (final refit time in the sample; pooled; trailing window on closed trades; top 5 cells by trailing mean delta; chosen = best cell if its trailing mean > 0, else hold)

* **H10|P** (12m, refit 2026-02-06 17:00Z, n=19910 closed trades): H10P|mfe20|trail4|price +0.22, H10P|mfe20|trail4|micro +0.22, H10P|mfe20|trail8|micro -0.01, H10P|mfe20|trail8|price -0.02, H10P|mfe20|trail12|price -0.10; chosen: H10P|mfe20|trail4|price
* **H11b|L** (12m, refit 2026-02-06 17:00Z, n=19910 closed trades): H11|mfe30|d10|T300|book -0.15, H11|mfe30|d5|T300|book -0.22, H11|mfe30|d10|T10|book -0.24, H11|mfe30|d10|T120|book -0.25, H11|mfe30|d10|T60|book -0.27; chosen: HOLD (no cell > 0)
* **H11p|L** (12m, refit 2026-02-06 17:00Z, n=19910 closed trades): H11|mfe30|d10|T120|path -0.25, H11|mfe30|d5|T120|path -0.27, H11|mfe30|d0|T300|path -0.29, H11|mfe30|d10|T30|path -0.29, H11|mfe30|d5|T30|path -0.30; chosen: HOLD (no cell > 0)
* **H1|P** (12m, refit 2026-02-06 17:00Z, n=19910 closed trades): H1P|pct0.7|k2|take +0.22, H1P|pct0.5|k2|take +0.16, H1P|pct0.7|k2|tr4 +0.07, H1P|pct0.5|k5|take +0.04, H1P|pct0.5|k2|tr4 +0.04; chosen: H1P|pct0.7|k2|take
* **H2|L** (12m, refit 2026-02-06 17:00Z, n=19910 closed trades): H2L|behind4|k1.5 -0.26, H2L|behind8|k1.5 -0.26, H2L|behind8|k2 -0.28, H2L|behind4|k3 -0.28, H2L|behind8|k3 -0.29; chosen: HOLD (no cell > 0)
* **H2|P** (12m, refit 2026-02-06 17:00Z, n=19910 closed trades): H2P|behind4|k1.5 -0.18, H2P|behind8|k1.5 -0.21, H2P|behind8|k3 -0.21, H2P|base -0.21, H2P|behind8|k2 -0.22; chosen: HOLD (no cell > 0)
* **H3|L** (12m, refit 2026-02-06 17:00Z, n=19910 closed trades): H3L|mae20|imb0.3|T30|cut -0.05, H3L|mae10|imb0.5|T30|cut -0.06, H3L|mae20|imb0.5|T30|cut -0.06, H3L|mae10|imb0.3|T30|cut -0.13, H3L|mae10|imb0.3|T30|tt3 -0.15; chosen: HOLD (no cell > 0)
* **H3|P** (12m, refit 2026-02-06 17:00Z, n=19910 closed trades): H3P|mfe10|imb0.3|T30|take -0.09, H3P|mfe20|imb0.3|T30|take -0.10, H3P|mfe20|imb0.5|T30|take -0.10, H3P|mfe20|imb0.5|T30|tr8 -0.10, H3P|mfe20|imb0.5|T30|tr4 -0.10; chosen: HOLD (no cell > 0)
* **H4|L** (12m, refit 2026-02-06 17:00Z, n=19910 closed trades): H4L|mae10|cons8|refill2|tt3 +0.00, H4L|mae20|cons15|refill2|tt3 -0.01, H4L|mae20|cons8|refill2|tt3 -0.01, H4L|mae20|cons15|refill2|cut -0.01, H4L|mae10|cons15|refill2|tt3 -0.04; chosen: H4L|mae10|cons8|refill2|tt3
* **H4|P** (12m, refit 2026-02-06 17:00Z, n=19910 closed trades): H4P|mfe20|cons8|refill4|take +0.25, H4P|mfe10|cons8|refill4|take +0.24, H4P|mfe20|cons15|refill4|take +0.17, H4P|mfe10|cons15|refill4|take +0.15, H4P|mfe10|cons3|refill2|take +0.13; chosen: H4P|mfe20|cons8|refill4|take
* **H5|L** (12m, refit 2026-02-06 17:00Z, n=19910 closed trades): H5L|with-veto -0.09, H5L|against|mae20|tt3 -1.03, H5L|against|mae20|cut -1.03, H5L|against|mae10|cut -1.40, H5L|against|mae10|tt3 -1.45; chosen: HOLD (no cell > 0)
* **H5|P** (12m, refit 2026-02-06 17:00Z, n=19910 closed trades): H5P|against|mfe20|take +0.52, H5P|against|mfe20|tr4 +0.12, H5P|against|mfe10|take -0.07, H5P|with-veto -0.21, H5P|against|mfe10|tr4 -0.49; chosen: H5P|against|mfe20|take
* **H6|L** (12m, refit 2026-02-06 17:00Z, n=19910 closed trades): H6L|mae20|pul500|tt6 -0.18, H6L|mae20|pul500|tt3 -0.21, H6L|mae20|pul1000|cut -0.27, H6L|mae20|pul1000|tt6 -0.29, H6L|mae20|pul1000|tt3 -0.32; chosen: HOLD (no cell > 0)
* **H6|P** (12m, refit 2026-02-06 17:00Z, n=19910 closed trades): H6P|mfe20|pul500|take +0.79, H6P|mfe10|pul500|take +0.54, H6P|mfe20|pul150|take +0.54, H6P|mfe20|pul500|tr4 +0.43, H6P|mfe20|pul1000|take +0.29; chosen: H6P|mfe20|pul500|take
* **H7|L** (12m, refit 2026-02-06 17:00Z, n=19910 closed trades): H7L|mae20|against10|n3|tt3 -0.98, H7L|mae20|against10|n3|cut -1.00, H7L|mae20|against30|n3|tt3 -1.02, H7L|mae20|against30|n1|tt3 -1.03, H7L|mae20|against30|n3|cut -1.04; chosen: HOLD (no cell > 0)
* **H7|P** (12m, refit 2026-02-06 17:00Z, n=19910 closed trades): H7P|pct0.7|with10|n3|take +1.10, H7P|pct0.7|with10|n1|take +1.10, H7P|pct0.7|with30|n1|take +1.09, H7P|pct0.7|with30|n3|take +1.06, H7P|pct0.5|with10|n3|take +0.86; chosen: H7P|pct0.7|with10|n3|take
* **H8|L** (12m, refit 2026-02-06 17:00Z, n=19910 closed trades): H8L|thickveto1.25 -0.12, H8L|thickveto1.5 -0.18, H8L|thin0.5|mae20|tt6 -0.23, H8L|thickveto2 -0.28, H8L|thin0.5|mae10|tt6 -0.37; chosen: HOLD (no cell > 0)
* **H8|P** (12m, refit 2026-02-06 17:00Z, n=19910 closed trades): H8P|thin0.7|pct0.5|take +0.93, H8P|thin0.7|pct0.25|take +0.60, H8P|thin0.7|pct0.5|tr4 +0.56, H8P|thin0.7|pct0.5|tr8 +0.41, H8P|thin0.5|pct0.5|take +0.33; chosen: H8P|thin0.7|pct0.5|take
* **H9|L** (12m, refit 2026-02-06 17:00Z, n=19910 closed trades): H9L|mae20|m300|flip3|cut -0.76, H9L|mae20|m300|flip1|tt3 -0.86, H9L|mae20|m0|flip3|cut -0.87, H9L|mae20|m300|flip2|tt3 -0.87, H9L|mae20|m300|flip1|cut -0.88; chosen: HOLD (no cell > 0)
* **H9|P** (12m, refit 2026-02-06 17:00Z, n=19910 closed trades): H9P|mfe20|m0|take +0.13, H9P|mfe20|m100|take +0.11, H9P|mfe20|m300|take +0.00, H9P|mfe20|m0|tr4 -0.14, H9P|mfe20|m100|tr4 -0.14; chosen: H9P|mfe20|m0|take

### Chain results, recent first (12m pooled weekly chain; pts/trade (MDE))

| family | 2026 | L6M | HOLD | PRE | X |
|---|---|---|---|---|---|
| H10|P | -0.73 (4.1) | -0.34 (1.2) | -0.30 | -0.08 | -0.52 |
| H11b|L | +0.00 (0.0) | +0.00 (0.0) | +0.00 | -0.16 | -0.60 |
| H11p|L | +0.00 (0.0) | +0.00 (0.0) | +0.00 | -0.19 | -0.21 |
| H1|P | +0.24 (1.1) | +0.13 (0.4) | +0.17 | -0.01 | -0.22 |
| H2|L | +0.00 (0.0) | -0.00 (0.2) | -0.00 | -0.10 | +0.11 |
| H2|P | +0.00 (0.0) | +0.00 (0.0) | +0.00 | -0.16 | -0.47 |
| H3|L | +0.00 (0.0) | -0.06 (0.3) | -0.05 | -0.39 | -0.67 |
| H3|P | +0.00 (0.0) | +0.00 (0.0) | +0.00 | +0.00 | -1.13 |
| H4|L | -0.08 (0.3) | -0.08 (0.2) | -0.07 | -0.27 | -0.47 |
| H4|P | -0.24 (1.6) | -0.04 (0.6) | -0.01 | -0.28 | -0.52 |
| H5|L | +0.00 (0.0) | +0.00 (0.0) | +0.00 | -0.23 | +0.02 |
| H5|P | +0.14 (4.5) | -0.07 (1.8) | -0.02 | -0.05 | -0.74 |
| H6|L | +0.00 (0.0) | +0.00 (0.0) | -0.04 | -0.17 | -0.34 |
| H6|P | +0.69 (3.5) | +0.29 (1.7) | +0.47 | -0.19 | -0.25 |
| H7|L | +0.00 (0.0) | +0.00 (0.0) | +0.00 | -0.24 | -0.18 |
| H7|P | +1.23 (2.4) | +0.89 (1.0) | +0.96 | +0.38 | -0.45 |
| H8|L | -0.06 (0.6) | -0.12 (0.6) | -0.11 | -0.10 | -0.07 |
| H8|P | +1.25 (2.4) | +0.90 (1.1) | +0.75 | +0.19 | -1.04 |
| H9|L | +0.00 (0.0) | +0.00 (0.0) | +0.00 | -0.08 | -0.61 |
| H9|P | -0.94 (4.0) | -0.39 (1.2) | -0.35 | -0.03 | -0.35 |


## Verdicts (one line each, yes/no = does an L2 rule add pts over hold net of measured cost)

* **H1 wall on target (take/tighten): NO.** True wall_tgt is visible in 0.05% of seconds (mbp-10 reaches ~2.5 pts, the target is 33-60 pts away), so only the PROXY (depth ahead within 8 ticks >= k x median, at >=50/70% of the way) was testable: best cell pct0.7/k2/take PRE +0.09 [-0.14,+0.33], HOLD +0.17, X -0.12 (LEAD by the ladder), but it is WORSE than the plain path rule it gates ("take at 70% of the way": -0.29 PRE, -0.78 HOLD [-1.39,-0.16] vs that control); verdict DEAD as an L2 effect, true-wall version UNTESTABLE on mbp-10 (needs MBO deep book).
* **H2 wall behind (hold through the stall, do not cut): NO.** The veto changes almost nothing (loss: unfiltered live-like rule PRE -0.30 / HOLD -0.24; with behind-8 wall >=1.5x median -0.23 / -0.19, i.e. +0.07 but inside noise; profit JADE-like stall rule -0.68 unfiltered vs -0.66); DEAD, the stall rules themselves lose against hold.
* **H3 lean against (imb5 against >=0.3/0.5 for >=10/30 s after +X): NO.** Profit take/tighten best PRE -0.27 (HOLD -0.59); loss cut/tighten best PRE +0.02, HOLD -0.23; 0 of 24 profit cells positive in PRE and HOLD; DEAD.
* **H4 queue drain at the supporting best (consumed >=3/8/15 contracts/s, refill <=2/4, at a new extreme): NO (LEAD at most).** Profit best H4P mfe20/cons8/refill2/trail4 PRE +0.06 [-0.14,+0.26] on 1,019 fired trades, HOLD +0.11 (177 fired), X -0.48; MDE 0.29-0.37, so the sample cannot see an effect below ~0.3 pt; loss side PRE +0.01, HOLD -0.07; neither passes X.
* **H5 iceberg at the extreme: NO.** Against-iceberg take/cut best PRE -0.26 (profit) and the with-veto for the loss rule -0.11 PRE / -0.09 HOLD; the iceberg flag (10x displayed) fires on ~63% of 1-s seconds at 2x, so it is near-always on; DEAD.
* **H6 pulled size (>=150/500/1000 contracts cancelled on the supporting side in 10 s at a new extreme): NO (profit LEAD weak).** Profit take best PRE +0.02 [-0.76,+0.80], HOLD +0.57, X +0.78, but 2x-cost PRE -0.49 and RC p 0.72, MDE 1.1/1.6; loss cut PRE -0.30, HOLD -0.48 (the "cut the loser on a pull" half loses; the pulled gate does improve on the pure new-MAE cut with no pull condition, pul0 PRE -1.07..-1.31 vs -0.30 at pul>=500, but both stay below hold); not significant.
* **H7 sweep against (cut loser) / sweep into target (take): loser cut NO, winner take is the path rule.** Loser cut at a sweep against: PRE -1.08, HOLD -1.19 (clear loser). Winner take at pct>=0.7 with a sweep with the trade: PRE +0.43 [-0.04,+0.89], HOLD +0.97, X +0.09, RC p 0.08, placebo rank 1.0, chain 12m pooled PRE +0.38 / HOLD +0.96 / X -0.45; BUT the plain path rule "take at 70% of the way" gives PRE +0.39, HOLD +0.94, X +0.12 and the sweep gate adds +0.04 [-0.04,+0.12] PRE / +0.03 [-0.12,+0.18] HOLD (nothing). 2x-cost PRE -0.11. LEAD for a PATH rule, L2 contribution zero; not published.
* **H8 thin book tighten / thick hold: NO.** Winner take when total 8-tick depth <=0.7x session median and pct>=0.5: PRE +0.39 [-0.10,+0.87], HOLD +0.75, X -0.81 (CI upper bound 0.00 in X), RC p 0.23; minus the path control (take at pct>=0.5) +0.28 PRE [-0.24,+0.81], +0.18 HOLD [-0.57,+0.92], so the thin gate is not distinguishable from nothing; the loser side (tighten or thick-veto) is negative in PRE and HOLD; LEAD only on a seen-data basis.
* **H9 OFI30 persistence (take at first flip, cut at the n-th flip): NO.** Profit take PRE -0.57, HOLD -0.04; loss cut best PRE -0.60, HOLD -1.33; DEAD.
* **H10 microprice crossing the trail level: NO.** The microprice trail is indistinguishable from the same price trail (trail 4/8/12 pts, mfe >=10/20: PRE -0.49 vs -0.51, -0.58 vs -0.58, -0.67 vs -0.66; HOLD -0.02 vs 0.00); both lose against hold-to-bracket; DEAD.
* **H11 round-trip cut (user): NO.** 120 cells (mfe >=10/15/20/30; below entry, -5, -10 for 10-300 s; path arm and book-against arm imb5<=-0.2 & delta60<0): 0 of 60 path cells and 0 of 60 book cells are positive in both PRE and HOLD. Cell means PRE -0.64 / HOLD -0.72 (path), -0.59 / -0.62 (book); the book condition improves the paired cell by +0.05 PRE, +0.10 HOLD (noise, MDE 0.5-0.8). Best path cell mfe30/d0/T30 PRE -0.32 [-0.87,+0.23], HOLD -0.55; best book cell mfe30/d5/T300 PRE -0.21 [-0.59,+0.17], HOLD -0.08, X -0.55. Placebo rank 0.0-0.1 (random cuts at the same rate do as well or better). Cutting a winner that fell back through entry costs more than the stop that hold would later have taken; DEAD.

## Table (best PRE-selected cell per family; pts per trade of the book vs hold, MEASURED; [95% trade-cluster CI]; fired = trades where the rule acts, PRE/HOLD; MDE = 2.8 SE PRE/HOLD; 2x = double exit cost PRE/HOLD; RC p = White best-of-family on PRE; placebo = rank of the real best-of-family vs the shuffled-book best-of-family)

| family | best cell | cells | PRE | HOLD | X | fired | MDE | 2x cost | RC p | placebo | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|
| H1|P | H1P|pct0.7|k2|take | 18 | +0.09 [-0.14,+0.32] | +0.17 [-0.14,+0.48] | -0.12 | 3,563/1,549 | 0.33/0.44 | -0.05/+0.03 | 0.61 | 1.0 | LEAD |
| H2|P | H2P|behind8|k1.5 | 7 | -0.66 [-1.61,+0.28] | -0.50 [-1.90,+0.90] | -0.46 | 15,840/7,108 | 1.35/2.00 | -1.30/-1.16 | 0.93 | 0.7 | DEAD |
| H2|L | H2L|behind8|k1.5 | 7 | -0.23 [-0.64,+0.18] | -0.19 [-0.79,+0.41] | +0.18 | 4,616/1,999 | 0.59/0.86 | -0.41/-0.37 | 0.90 | 0.8 | DEAD |
| H3|P | H3P|mfe20|imb0.3|T10|take | 24 | -0.27 [-0.86,+0.33] | -0.59 [-1.50,+0.32] | -0.77 | 7,002/3,102 | 0.85/1.30 | -0.55/-0.88 | 1.00 | 0.0 | DEAD |
| H3|L | H3L|mae20|imb0.5|T10|tt6 | 24 | +0.02 [-0.16,+0.21] | -0.23 [-0.52,+0.07] | -0.12 | 1,147/503 | 0.27/0.42 | -0.02/-0.27 | 0.90 | 0.8 | DEAD |
| H4|P | H4P|mfe20|cons8|refill2|tr4 | 24 | +0.06 [-0.14,+0.26] | +0.11 [-0.15,+0.37] | -0.48 | 1,019/177 | 0.29/0.37 | +0.02/+0.09 | 0.73 | 1.0 | LEAD |
| H4|L | H4L|mae20|cons15|refill2|cut | 24 | +0.01 [-0.22,+0.25] | -0.07 [-0.25,+0.10] | +0.47 | 1,616/267 | 0.33/0.25 | -0.05/-0.10 | 0.88 | 0.6 | DEAD |
| H5|P | H5P|against|mfe20|take | 5 | -0.26 [-1.25,+0.73] | +0.26 [-1.17,+1.69] | -0.16 | 18,231/8,102 | 1.42/2.05 | -0.99/-0.49 | 0.81 | 0.2 | DEAD |
| H5|L | H5L|with-veto | 5 | -0.11 [-0.29,+0.08] | -0.09 [-0.34,+0.15] | -0.08 | 0/5 | 0.26/0.35 | -0.14/-0.13 | 0.98 | 0.8 | DEAD |
| H6|P | H6P|mfe20|pul500|take | 18 | +0.02 [-0.76,+0.80] | +0.57 [-0.57,+1.71] | +0.78 | 12,619/5,656 | 1.12/1.63 | -0.49/+0.05 | 0.72 | 0.5 | LEAD |
| H6|L | H6L|mae20|pul500|tt6 | 24 | -0.30 [-0.92,+0.32] | -0.48 [-1.37,+0.41] | -0.04 | 9,152/4,048 | 0.88/1.27 | -0.67/-0.86 | 0.97 | 0.0 | DEAD |
| H7|P | H7P|pct0.7|with10|n3|take | 16 | +0.43 [-0.04,+0.89] | +0.97 [+0.31,+1.63] | +0.09 | 13,350/5,954 | 0.67/0.95 | -0.11/+0.42 | 0.08 | 1.0 | LEAD |
| H7|L | H7L|mae20|against30|n1|cut | 16 | -1.08 [-2.07,-0.09] | -1.19 [-2.64,+0.25] | -0.47 | 17,455/7,629 | 1.41/2.07 | -1.78/-1.90 | 0.99 | 0.0 | DEAD |
| H8|P | H8P|thin0.7|pct0.5|take | 15 | +0.39 [-0.10,+0.87] | +0.75 [+0.03,+1.47] | -0.81 | 8,065/3,767 | 0.69/1.03 | +0.06/+0.40 | 0.23 | 1.0 | LEAD |
| H8|L | H8L|thickveto1.25 | 15 | -0.07 [-0.47,+0.33] | -0.20 [-0.79,+0.38] | +0.27 | 4,371/1,918 | 0.57/0.84 | -0.25/-0.38 | 0.93 | 0.4 | DEAD |
| H9|P | H9P|mfe20|m100|take | 18 | -0.57 [-1.55,+0.40] | -0.04 [-1.48,+1.39] | -0.45 | 17,297/7,699 | 1.39/2.05 | -1.27/-0.75 | 0.93 | 0.1 | DEAD |
| H9|L | H9L|mae20|m0|flip3|cut | 36 | -0.60 [-1.54,+0.33] | -1.33 [-2.70,+0.05] | -0.52 | 16,168/6,995 | 1.33/1.96 | -1.26/-1.97 | 0.96 | 0.0 | DEAD |
| H10|P | H10P|mfe20|trail4|micro | 12 | -0.49 [-1.49,+0.50] | -0.02 [-1.47,+1.43] | -0.47 | 17,968/7,999 | 1.42/2.07 | -1.22/-0.75 | 0.90 | 0.4 | DEAD |
| H11p|L | H11|mfe30|d0|T30|path | 60 | -0.32 [-0.87,+0.23] | -0.55 [-1.41,+0.31] | +0.04 | 6,104/2,716 | 0.79/1.23 | -0.57/-0.80 | 0.98 | 0.0 | DEAD |
| H11b|L | H11|mfe30|d5|T300|book | 60 | -0.21 [-0.59,+0.17] | -0.08 [-0.63,+0.47] | -0.55 | 3,528/1,397 | 0.54/0.79 | -0.35/-0.21 | 0.99 | 0.1 | DEAD |

Verdict ladder (prereg): PASS = PRE CI excludes 0, PRE/HOLD/X all >0, 2x-cost PRE and HOLD >0, RC p <=0.05, placebo >=0.95, >=200 fired; CANDIDATE = PRE/HOLD/X >0, 2x >0, placebo >=0.90, RC p <=0.10; LEAD = PRE>0 and HOLD>0; else DEAD. **0 PASS, 0 CANDIDATE, 5 families LEAD (H1P, H4P, H6P, H7P, H8P), 15 DEAD.** No family reaches the survivor bar, so no hypothesis enters the candidate policy.

## Walk-forward re-fitting chains (best HOLD chain per family; chain re-selects the cell weekly on closed trades)

* H1|P: 12m/pooled: PRE -0.01, HOLD +0.17 [-0.14,+0.48], X -0.22
* H2|P: 12m/pooled: PRE -0.16, HOLD +0.00 [+0.00,+0.00], X -0.47
* H2|L: 12m/pooled: PRE -0.10, HOLD -0.00 [-0.10,+0.09], X +0.11
* H3|P: 12m/pooled: PRE +0.00, HOLD +0.00 [+0.00,+0.00], X -1.13
* H3|L: 12m/perbook: PRE -0.28, HOLD -0.02 [-0.29,+0.26], X -0.24
* H4|P: 3m/pooled: PRE -0.16, HOLD +0.21 [-0.38,+0.81], X -0.23
* H4|L: 12m/pooled: PRE -0.27, HOLD -0.07 [-0.20,+0.06], X -0.47
* H5|P: 3m/pooled: PRE -0.42, HOLD +0.03 [-1.18,+1.25], X -0.63
* H5|L: 12m/pooled: PRE -0.23, HOLD +0.00 [+0.00,+0.00], X +0.02
* H6|P: 12m/pooled: PRE -0.19, HOLD +0.47 [-0.62,+1.56], X -0.25
* H6|L: 12m/pooled: PRE -0.17, HOLD -0.04 [-0.25,+0.16], X -0.34
* H7|P: 12m/pooled: PRE +0.38, HOLD +0.96 [+0.29,+1.64], X -0.45
* H7|L: 12m/pooled: PRE -0.24, HOLD +0.00 [+0.00,+0.00], X -0.18
* H8|P: 12m/pooled: PRE +0.19, HOLD +0.75 [+0.03,+1.47], X -1.04
* H8|L: 12m/pooled: PRE -0.10, HOLD -0.11 [-0.46,+0.24], X -0.07
* H9|P: 12m/perbook: PRE -0.43, HOLD -0.29 [-1.05,+0.48], X -0.54
* H9|L: 12m/pooled: PRE -0.08, HOLD +0.00 [+0.00,+0.00], X -0.61
* H10|P: 12m/perbook: PRE -0.45, HOLD -0.26 [-0.97,+0.45], X -0.86
* H11p|L: 12m/pooled: PRE -0.19, HOLD +0.00 [+0.00,+0.00], X -0.21
* H11b|L: 12m/perbook: PRE -0.60, HOLD +0.03 [-0.43,+0.48], X -0.15

Only H7P (12m pooled) is positive in PRE and HOLD (+0.38, +0.96) and it is the path rule above (X -0.45). Per book and session of the best cells: out/thp/wf/l2h/breakdown.csv; for H7P the take-at-70% rule is positive in HOLD for 8 of 10 books and negative for HM and MA, positive in every session in HOLD, but PRE has 3 negative books (HM, MA, SM) and 2 negative sessions (close, nyam); the sign pattern is not stable enough to key a policy by book.

## Path-only control (the most useful side result)

Take the whole position at the first 10-s close with pct >= 0.7 (70% of the way to target), MEASURED, vs hold-to-bracket, no L2 at all: X +0.12 [-0.93,+1.16], PRE +0.39 [-0.10,+0.87], HOLD +0.94 [+0.24,+1.65] pts/trade of the book (13.6k / 6.1k fired trades); pct >= 0.5: X -0.42, PRE +0.11, HOLD +0.57. The H7 cell that wraps it fails the 2x-cost gate in PRE (-0.11) and the X window is only +0.09..+0.12, i.e. a LEAD at best, on seen data, and not an L2 finding. It says the bracket target is on average slightly too far for the last 30% of the move with the 0.995-pt market exit: it is worth a THP_C path study, not a policy.

## Reading across the eleven

Nothing in the 10-level book, the queue, the sweeps or the pulled/added size beats hold-to-bracket after measured costs, once placebo, best-of-N and the matching path-only control are applied. The L2 gates (H1 wall, H8 thin, H7 sweep) add 0 +/- 0.3 pt to the plain path rule they sit on. The descriptive map (DS3_THL2_B_MAP.md) shows the same: total book thickness against the session median is the only feature with a large decile spread (thick book, winner: PRE -4.7 pts remaining vs +2.4 in the thinnest decile; HOLD -0.2 vs +3.5) but that is mostly a selection of time-of-day and trade-progress states and does not survive the paired rule test (H8). Files: cells_all.csv (all 428 cells x X/PRE/HOLD, fired counts, 2x, NOTC), fam_summary.csv, chains.csv, breakdown.csv, lead_controls.csv, h7_control.csv in l2vast/ds3/out/thp/wf/l2h/.

## ADDENDUM: H12 ES-book lean (post-hoc, amendment A2 sha 75b3836e...; 20 cells; found from the map-B reading es_imb5 L6M t=+4.0)

* **H12 ES book leaning against the trade (es_imb5 <= -0.1/-0.2): NO.** Despite the largest decile spread in the whole map (loser: remaining P&L L6M +6.7 pts adjusted in the top es_imb5 decile vs -1.2 in the bottom; monotone in 2026, L6M, HOLD, much weaker in PRE and reversed in X), every rule built on it loses against hold: loser cut 8 cells PRE -0.70..-1.31, L6M -1.06..-2.27, 2026 -0.41..-2.89; winner take/trail PRE -0.35..-1.00 (best mfe20/es0.1/take: PRE -0.35, HOLD +0.17, L6M -0.13, 2026 +0.22); the veto of the live-loss stall rule is the only near-zero cell (PRE -0.17, HOLD +0.05, L6M 0.00, 2026 -1.27). Chains negative (best HOLD +0.01, 12m pooled loss). RC p 0.98/0.86; all-cell RC p 0.74. Why the map did not become a rule: the decile table reports remaining P&L ADJUSTED for position in the trade; the raw remaining P&L of the weak-book losers is still about zero or positive, i.e. less than the 1-pt cost of leaving, so a lower rem decile does not mean a profitable cut. Read every `adj` spread in the map as a diagnostic, not as an exit signal.

| family | rank-1 by L6M | 2026 (MDE) | L6M (MDE) | HOLD | PRE | X | #CAND-RECENT | PRE-selected: 2026 / L6M |
|---|---|---|---|---|---|---|---|---|
| H12|P | H12P|mfe20|es0.1|take | +0.22 (4.5) | -0.13 (2.1) | +0.17 | -0.35 | -0.14 | 0/10 | +0.22 / -0.13 |
| H12|L | H12L|veto|es0.1 | -1.27 (1.8) | -0.00 (0.7) | +0.05 | -0.17 | +0.10 | 0/10 | -1.27 / -0.00 |

Table rows (same columns as the main table):

| family | best cell | cells | PRE | HOLD | X | fired | MDE | 2x cost | RC p | placebo | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|
| H12|P | H12P|mfe20|es0.1|take | 10 | -0.35 [-1.33,+0.63] | +0.17 [-1.26,+1.59] | -0.14 | 17,771/7,879 | 1.40/2.03 | -1.06/-0.56 | 0.86 | 0.6 | DEAD |
| H12|L | H12L|veto|es0.1 | 10 | -0.17 [-0.50,+0.15] | +0.05 [-0.44,+0.53] | +0.10 | 3,114/1,379 | 0.46/0.69 | -0.30/-0.08 | 0.98 | 1.0 | DEAD |

Totals with H12: 448 cells, 0 PASS, 0 CANDIDATE, 5 LEAD families, 17 DEAD (22 families); all-cell RC p 0.74.
