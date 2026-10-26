# CONVENTIONS - report and code ID prefixes (written 2026-10-16 by worker I after the R-batch ID collision)

Rule: BEFORE choosing an ID prefix for a new batch, list `outputs/autopilot/REPORT_*.md`, `status/*.txt`, `outputs/autopilot/<id>/` and `code/census/night_ins/ap_<prefix>*` and pick a prefix that does not appear. Record the prefix in this file in the same edit. Never write REPORT_<id>.md without checking it does not exist (writers should open with mode `x` or check first). Two-letter prefixes are cheapest to keep unique (RW, RX, ...).

## Prefixes in use (from the REPORT_*.md files present on 2026-10-16 ~23:30Z; owner notes where known)

| prefix | reports | examples | owner / note |
|---|---|---|---|
| A | 9 | A1, A10, A2, A3, A5, A6 | worker I (backlog2 group A A1-A10; also GAPMAP A?) |
| ASSEMBLY_<timestamp> | 12 | assembly job outputs | LIBRARY / assembly worker (timestamped names, no collision risk) |
| B | 21 | B1, B10, B11, B12, B14, B15 | B-series (capacity backlog B1-B19, several workers; B15 = worker I) |
| BASKET | 1 | BASKET |  |
| C | 25 | C10_S1, C11_DIP, C11_HM, C11_REP2, C1_F1, C1_F2 | cycle 1-11 families |
| D | 8 | D30, D31, D32, D33, D34, D35 | D30-D37 worker I (flow persistence); D1/D2/D3 earlier directives |
| DRIVERS | 1 | DRIVERS |  |
| E | 5 | E1, E2, E3, E4, E7 | E1-E7 evidence-driven (worker I), E8 lead |
| ERA_RETRO | 1 | ERA_RETRO |  |
| G | 22 | G0a, G0b, G0c, G1, G10_1, G10_2 | GAPMAP gap workers (G0-G11) |
| GC_FADE_V2 | 1 | GC_FADE_V2 |  |
| H | 19 | H0a, H0b, H0c, H0d, H10_A, H10_B | H-series (H0-H11) |
| I | 17 | I1, I10, I1_devsel, I2, I2_devsel, I3 | worker I batch 1 |
| ICT | 1 | ICT |  |
| J | 29 | J0A, J0B, J0C, J1, J10, J10_firstpass_dataerr | worker I batch 2 + other J-series (J0*, J5W, J6a-c, J7V, J9P, J11) |
| K | 34 | K, K1, K10, K100, K11, K12 | worker I batch 3 (K1-K10, K4P, K4V2) + other workers (K11-K27, K84, K96-K100) |
| K_CURE | 1 | K_CURE |  |
| L | 13 | L10, L2, L3, L4, L5, L6 | worker I batch 4 (L2-L10) + others (L90-L93) |
| N | 7 | N1, N2, N3, N4, N5, N6 | N1-N7 (b2356 or GAP) |
| OPT | 1 | OPT0DTE |  |
| OPTIONS | 1 | OPTIONS |  |
| P | 4 | P1, P1B, P1_DECOMP, P2 | P1/P2 priorities, PA*, PX* |
| PA | 9 | PA10, PA3, PA4, PA4_NKD, PA5, PA6 |  |
| PULLBACK | 1 | PULLBACK |  |
| PX | 12 | PX1, PX20, PX21, PX22, PX23, PX24 |  |
| PX_L2ES | 1 | PX_L2ES |  |
| Q | 10 | Q1A, Q1B, Q1C, Q1D, Q2, Q3 | Q-series (Q1A-Q7A) |
| R | 10 | R10_b2356, R1_b2356, R2_b2356, R3_b2356, R4_b2356, R5 | R1-R10 = b2356 worker (kurtosis, Asian breakout, 30-min analogues, macro momentum) |
| RW | 16 | RW1, RW10, RW11, RW12, RW12P, RW13 | worker I batch R (RW1-RW15, RW12P) |
| S | 10 | S1, S10, S2, S3, S4, S5 | S1-S10 b2356 worker |
| T | 7 | T1, T1b, T2, T3, T4, T5 | T1-T6 b2356 worker |
| U | 3 | U1, U2, U3 | U1-U3 |
| V | 10 | V1, V10, V2, V3, V4, V5 | V1-V10 b2356 worker |
| W | 7 | W1, W2, W3, W4, W5, W6 | W1-W8 b2356 worker |
| WT | 2 | WT, WT2 | WT re-score |
| X | 6 | X1, X1_REP, X2, X3, X4, X5 | X1-X5 b2356 / X_BOOT |
| X_BOOT | 1 | X_BOOT |  |
| Y | 10 | Y1, Y10, Y2, Y3, Y4, Y5 | Y1-Y10 b2356 worker |
| Z | 9 | Z1, Z10, Z2, Z3, Z4, Z5 | Z1-Z10 b2356 worker |

## Reserved for the current ideation worker (worker I)
- RX*: all new families from 2026-10-16 23:30Z (code prefix ap_rx_; reports REPORT_RX<n>.md; status/RX<n>.txt; library family RX<n>).
- RW*: batch R (done).
- The b2356 worker's regenerated R1,R2,R3,R4,R9,R10 reports are REPORT_R<n>_b2356.md (original files were overwritten by worker I on 2026-10-16 and regenerated from outputs/autopilot/b2356/ with ap_y_report.py).

## Collision incident (2026-10-16)
Worker I used R1-R15 for a K4-deepening batch while the b2356 worker already owned R1-R10; REPORT_R1/2/3/4/9/10 and status/R1-R4,R9,R10 were overwritten, then restored by regeneration. Library rows saved by worker I under family R2/R3/R4/R9/R10/R12/R12P were re-labelled RW* with update_meta; b2356 rows keep their R-families (their `source` field now points at the _b2356 reports).

## Added 2026-10-17
- RX (batch RX, done), RY (batch RY: RY1-RY10, K4 independence tests; code ap_ry*; library family RY<n>) are worker I's. RZ (batch RZ: RZ1-RZ10, range-regime and structural limit-order items; code ap_rz*) is done. RV (RV1 follow-up on RZ FVG sleeves; code ap_rv_*) is done. Next prefix for worker I: RU (check before use).

## Added 2026-10-17 (worker BK)
- BK (batch BK: BK1-BK10, backlog-2 residue groups F/G/J; code ap_bk*; REPORT_BK<n>.md; status/BK.txt; library family BK<n>). Next free prefix after BK: BL (check before use).
- BI (batch BI: BI1-BI10, ideas in IDEAS_BI.md; code ap_bi_*; REPORT_BI<n>.md; status/BI.txt; library family BI<n>) registered 2026-10-17 by worker BK. Next free prefix: BM.
- BJ (batch BJ: BJ1-BJ10, IDEAS_BJ.md; code ap_bj_*; REPORT_BJ<n>.md; status/BJ.txt; library family BJ<n>) registered 2026-10-17 by worker BK. BI8B also written. Next free prefix: BM.
- BM (batch BM: BM1-BM10, IDEAS_BM.md; code ap_bm_*; REPORT_BM<n>.md; status/BM.txt; library family BM<n>) registered 2026-10-17 by worker BK. BL1/BL2 reports written. Next free prefix: BN.
- I5<letter>: IDEAS-5000 families (REPORT_I5A.md ...), outputs/ideas5000/
