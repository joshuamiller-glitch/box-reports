# DS3_DIPENTRY - arm-and-confirm dip entry (L2-gated primary), timer limit and market controls, ADD2 (D6-LIVE, thin/thick, joint rules, recent-first)
Research only; no live/execution change; UNTOUCHED never read (own capped masks; HOLD-mask audit: vs_lib.WINS['HOLD'] has no upper bound, DIPENTRY does not use it - trades dropped at label day > 20260206, 1-s path sliced at 2026-02-06 22:00Z, engine days to 20260206). Prereg l2vast/ds3/prereg/DIPENTRY_prereg.md sha256 9f73c2f93e2dd0fe (full sha in DECISIONS.md), addendum 2 sha256 8645ea77829478330def384de5fdb6923f22a3616d456569d5b649e9f2d435f1 (+ amendment A1: iceberg proxy), cells.csv sha256 b8a0dcd0...; PRE-only file autopilot/DS3_DIPENTRY_PREHOLD.md; one logged HOLD+2026+X' look (looks.jsonl track DIPENTRY). Code l2vast/ds3/code/dipentry/, outputs l2vast/ds3/out/dipentry/. Cells: 2,072 registered family + 11 ADD2 trade-level + 9 engine stacks. Units: stack delta $/week vs the market entry on the same signals, lot-matched (live lots ST10 HM10 WT7 KB5.2 SM7.4 PE5.6, others 10), MEASURED fills; each number is followed by (MDE80) in k$. Windows recent-first: 2026 (20260101-0206, ~6 weeks: 2026 alone is ~5 weeks), last 6 months L6M (20250801-0206), HOLD (20250701-0206), PRE (2024-02..2025-06), X' (2023-04..2024-01; CONTAMINATED: two dry-run prints before the look, disclosed in DECISIONS).

## Verdict (plain)
* **0 PASS / 0 CANDIDATE / 20 DEAD** of 20 book-cells (10 books x [PRE-best any family, PRE-best primary spec = single gate, market entry, bracket 0]); CR NOT TESTED (stored dynamic exit). Best-of-N White RC over all 2083 cells: PRE max t 1.48 p 0.85; L6M max t 2.13 p 0.55; HOLD max t 2.36 p 0.42. Nothing survives the best-of-N.
* The dip is not free: a limit/gated entry X below the signal buys X pts but skips the straight-up winners; at X>=10 almost every timer/gate cell loses 10-35 k$/wk (PRE median -20.8 k$ for timers). Only X=5 timers and rare gates (BIG_PRINT, IMB5_F30) are near zero or positive, all inside their MDE.
* Gated vs random timing at the same fill count (PRE placebo, 133 B1 cells): 6.0% of cells rank >= 0.95; the high ranks are rare gates (BIG_PRINT, IMB5_F30, CONCORD: p_tick ~1%), i.e. the confirmation event carries some information about WHICH dips are bought, but the cells themselves are not positive after the skipped winners.
* RECENT-FIRST: 29 of 2083 cells are positive in BOTH 2026 and L6M (label CANDIDATE-RECENT), 100 positive in L6M; with RC p 0.55 on L6M this is what chance gives. 2026 alone is ~5 weeks. Ranking by L6M selects on HOLD (already looked at).
* Walk-forward adaptive re-selection HURTS recently: chain Delta $/wk 12m-trailing quarterly: 2026 -157.4, L6M -56.8, HOLD -29.9, PRE 2.0 (MDE 55.8); 3m-trailing and 1m-trailing chains are also negative everywhere. The adaptive variant does not help the entry.
* D6-LIVE (3-of-8 + dip 10 + imb5 veto): stack Delta HOLD -35.9 k$/wk (MDE 101.0), L6M -57.1, 2026 -61.1; fills 69% of signals in HOLD; DEAD. Joint entry+profit+loss rules on the exact lock engine: no variant beats the stack as is (table 4).

### One verdict line per book (V2; PRE-best cell any family | PRE-best primary spec; failed gates listed; recent = positive 2026 and L6M)
* DN [best] A1_timer|-|X5|T120_mkt|b2: **DEAD** failed ['holdout_sign', 'SPAN2', 'placebo>=0.95', 'CI(PRE lo>0)', 'maxDD(engine)', 'cost', 'year_share', 'neighbours', 'RC_p<=0.05']; Delta $/wk 2026 0.7 (29.6), L6M -3.1 (12.3), HOLD -1.9 (11.7), PRE 0.6 (7.8), X' -4.6; fills HOLD 780/782; P(target|fill) 0.523 vs P(target|all signals) 0.527; 
* DN [prim] B1_gate|BIG_PRINT|X0|mkt|b0: **DEAD** failed ['mean_up', 'holdout_sign', 'SPAN2', 'placebo>=0.95', 'CI(PRE lo>0)', 'maxDD(engine)', 'cost', 'year_share', 'neighbours', 'RC_p<=0.05']; Delta $/wk 2026 -43.9 (22.5), L6M -12.5 (19.6), HOLD -7.7 (19.1), PRE -6.4 (11.5), X' -2.5; fills HOLD 627/782; P(target|fill) 0.517 vs P(target|all signals) 0.527; 
* HM [best] A1_timer|-|X5|T120_skip|b3: **DEAD** failed ['holdout_sign', 'placebo>=0.95', 'CI(PRE lo>0)', 'cost', 'year_share', 'RC_p<=0.05']; Delta $/wk 2026 -20.8 (58.7), L6M -13.3 (27.9), HOLD -10.7 (25.3), PRE 6.0 (14.3), X' 4.0; fills HOLD 547/1008; P(target|fill) 0.466 vs P(target|all signals) 0.506; 
* HM [prim] B1_gate|IMB5_F30|X0|mkt|b0: **DEAD** failed ['holdout_sign', 'SPAN2', 'placebo>=0.95', 'CI(PRE lo>0)', 'maxDD(engine)', 'cost', 'year_share', 'neighbours', 'RC_p<=0.05']; Delta $/wk 2026 -17.3 (33.8), L6M -12.0 (20.6), HOLD -10.1 (18.5), PRE 1.1 (12.9), X' -2.7; fills HOLD 782/1008; P(target|fill) 0.482 vs P(target|all signals) 0.506; 
* KB [best] B2_pair|PAIR4|X0|mkt|b0: **DEAD** failed ['SPAN2', 'placebo>=0.95', 'CI(PRE lo>0)', 'year_share', 'neighbours', 'RC_p<=0.05']; Delta $/wk 2026 0.3 (29.7), L6M 0.9 (18.8), HOLD 1.2 (18.3), PRE 4.6 (11.0), X' -2.9; fills HOLD 611/1374; P(target|fill) 0.471 vs P(target|all signals) 0.490; CANDIDATE-RECENT (2026 alone is ~5 weeks)
* KB [prim] B1_gate|BIG_PRINT|X0|mkt|b0: **DEAD** failed ['SPAN2', 'CI(PRE lo>0)', 'maxDD(engine)', 'neighbours', 'RC_p<=0.05']; Delta $/wk 2026 8.9 (36.8), L6M 7.6 (17.7), HOLD 9.1 (17.3), PRE 2.5 (10.1), X' -2.4; fills HOLD 839/1374; P(target|fill) 0.508 vs P(target|all signals) 0.490; CANDIDATE-RECENT (2026 alone is ~5 weeks)
* MA [best] B2_pair|PAIR8|X.5stop|lim|b3: **DEAD** failed ['holdout_sign', 'SPAN2', 'placebo>=0.95', 'CI(PRE lo>0)', 'maxDD(engine)', 'cost', 'year_share', 'neighbours', 'RC_p<=0.05']; Delta $/wk 2026 4.1 (45.3), L6M -14.4 (23.0), HOLD -7.3 (25.0), PRE 3.9 (17.7), X' -11.1; fills HOLD 226/474; P(target|fill) 0.363 vs P(target|all signals) 0.530; 
* MA [prim] B1_gate|IMB5_F30|X0|mkt|b0: **DEAD** failed ['holdout_sign', 'CI(PRE lo>0)', 'maxDD(engine)', 'cost', 'year_share', 'neighbours', 'RC_p<=0.05']; Delta $/wk 2026 1.8 (32.5), L6M -7.8 (15.3), HOLD -6.8 (13.5), PRE 2.1 (11.4), X' 1.1; fills HOLD 411/474; P(target|fill) 0.496 vs P(target|all signals) 0.530; 
* MV [best] B1_gate|IMB5_F30|X0|mkt|b0: **DEAD** failed ['holdout_sign', 'placebo>=0.95', 'CI(PRE lo>0)', 'maxDD(engine)', 'cost', 'year_share', 'neighbours', 'RC_p<=0.05']; Delta $/wk 2026 -25.2 (37.8), L6M -3.1 (26.0), HOLD -2.6 (23.2), PRE 7.6 (14.8), X' 6.6; fills HOLD 993/1251; P(target|fill) 0.474 vs P(target|all signals) 0.497; 
* MV [prim] B1_gate|IMB5_F30|X0|mkt|b0: **DEAD** failed ['holdout_sign', 'placebo>=0.95', 'CI(PRE lo>0)', 'maxDD(engine)', 'cost', 'year_share', 'neighbours', 'RC_p<=0.05']; Delta $/wk 2026 -25.2 (37.8), L6M -3.1 (26.0), HOLD -2.6 (23.2), PRE 7.6 (14.8), X' 6.6; fills HOLD 993/1251; P(target|fill) 0.474 vs P(target|all signals) 0.497; 
* PB [best] B2_pair|PAIR7|X0|lim|b2: **DEAD** failed ['holdout_sign', 'SPAN2', 'placebo>=0.95', 'maxDD(engine)', 'cost', 'year_share', 'RC_p<=0.05']; Delta $/wk 2026 -23.7 (58.3), L6M -34.4 (29.7), HOLD -25.3 (31.8), PRE 15.5 (18.7), X' -5.5; fills HOLD 555/965; P(target|fill) 0.468 vs P(target|all signals) 0.526; 
* PB [prim] B1_gate|CONCORD|X0|mkt|b0: **DEAD** failed ['holdout_sign', 'SPAN2', 'placebo>=0.95', 'CI(PRE lo>0)', 'maxDD(engine)', 'cost', 'year_share', 'RC_p<=0.05']; Delta $/wk 2026 -0.1 (41.9), L6M -18.7 (26.8), HOLD -17.2 (26.7), PRE 8.1 (15.6), X' -6.1; fills HOLD 644/965; P(target|fill) 0.498 vs P(target|all signals) 0.526; 
* PE [best] B2_pair|PAIR2|X0|mkt|b0: **DEAD** failed ['placebo>=0.95', 'CI(PRE lo>0)', 'year_share', 'RC_p<=0.05']; Delta $/wk 2026 32.9 (60.4), L6M 6.7 (19.4), HOLD 4.2 (17.8), PRE 7.6 (12.8), X' 0.0; fills HOLD 539/1311; P(target|fill) 0.484 vs P(target|all signals) 0.488; CANDIDATE-RECENT (2026 alone is ~5 weeks)
* PE [prim] B1_gate|CONCORD|X10|mkt|b0: **DEAD** failed ['SPAN2', 'placebo>=0.95', 'CI(PRE lo>0)', 'year_share', 'RC_p<=0.05']; Delta $/wk 2026 20.8 (39.2), L6M 6.3 (17.5), HOLD 5.7 (17.0), PRE 6.9 (12.2), X' -1.2; fills HOLD 507/1311; P(target|fill) 0.363 vs P(target|all signals) 0.488; CANDIDATE-RECENT (2026 alone is ~5 weeks)
* SM [best] B1_gate|WALL_BID|X0|lim|b3: **DEAD** failed ['SPAN2', 'placebo>=0.95', 'CI(PRE lo>0)', 'cost', 'year_share', 'RC_p<=0.05']; Delta $/wk 2026 1.2 (32.8), L6M 2.4 (11.6), HOLD 0.1 (11.1), PRE 2.8 (6.3), X' -1.7; fills HOLD 324/363; P(target|fill) 0.522 vs P(target|all signals) 0.521; CANDIDATE-RECENT (2026 alone is ~5 weeks)
* SM [prim] B1_gate|MICRO_CROSS|X0|mkt|b0: **DEAD** failed ['holdout_sign', 'placebo>=0.95', 'CI(PRE lo>0)', 'cost', 'year_share', 'neighbours', 'RC_p<=0.05']; Delta $/wk 2026 -5.1 (20.5), L6M -2.9 (6.1), HOLD -2.1 (5.6), PRE 1.0 (3.8), X' 1.6; fills HOLD 359/363; P(target|fill) 0.513 vs P(target|all signals) 0.521; 
* ST [best] B1_gate|BIG_PRINT|X0|lim|b0: **DEAD** failed ['SPAN2', 'placebo>=0.95', 'year_share', 'RC_p<=0.05']; Delta $/wk 2026 -42.5 (44.6), L6M 4.1 (32.4), HOLD 7.4 (29.5), PRE 13.7 (16.2), X' -4.5; fills HOLD 856/1382; P(target|fill) 0.518 vs P(target|all signals) 0.507; 
* ST [prim] B1_gate|BIG_PRINT|X0|mkt|b0: **DEAD** failed ['SPAN2', 'year_share', 'RC_p<=0.05']; Delta $/wk 2026 -48.2 (47.1), L6M 2.4 (33.0), HOLD 5.9 (30.0), PRE 11.8 (16.2), X' -4.3; fills HOLD 856/1382; P(target|fill) 0.516 vs P(target|all signals) 0.507; 
* WT [best] B2_pair|PAIR4|X5|lim|b3: **DEAD** failed ['SPAN2', 'placebo>=0.95', 'year_share', 'RC_p<=0.05']; Delta $/wk 2026 -0.4 (31.0), L6M 9.7 (20.2), HOLD 12.3 (20.1), PRE 11.8 (11.8), X' -2.3; fills HOLD 237/1893; P(target|fill) 0.506 vs P(target|all signals) 0.587; 
* WT [prim] B1_gate|IMB5_F30|X.25stop|mkt|b0: **DEAD** failed ['SPAN2', 'placebo>=0.95', 'year_share', 'RC_p<=0.05']; Delta $/wk 2026 0.1 (41.4), L6M 5.2 (19.2), HOLD 10.1 (23.4), PRE 7.5 (10.6), X' -0.5; fills HOLD 460/1893; P(target|fill) 0.467 vs P(target|all signals) 0.587; CANDIDATE-RECENT (2026 alone is ~5 weeks)
* CR (C6): NOT TESTED - stored dynamic exit (no static stop/target to re-base).

## 1. D6-LIVE named cell (ADD2 part 1) beside the best registered cell per book
D6-LIVE = arm; first 10-s tick with price >= 10 pts against AND >= 3 of 8 confirms AND imb5 > -0.40; stop original, target 60 from fill, market +1 tick. Gate proxies from l2feat (labelled in prereg; exact definitions requested in L2FEAT_REQUESTS.txt); evaluated per 10-s tick not per second. Stack Delta $/wk (MDE) 2026 | L6M | HOLD | PRE | X':
| cell | Y26 | L6M | HOLD | PRE | X | fill HOLD | P(target|fill) HOLD | P(target) all |
|--|--|--|--|--|--|--|--|--|
| D6L | -61.1 (142.2) | -57.1 (95.4) | -35.9 (101.0) | -30.3 (58.6) | -22.2 (52.9) | 0.69 | 0.432 | 0.520 |
| D6L_dip5 | -29.7 (127.0) | -38.3 (86.6) | -21.8 (86.9) | -31.6 (51.5) | -12.3 (45.2) | 0.77 | 0.461 | 0.520 |
| D6L_2of8 | -32.0 (115.5) | -36.5 (85.8) | -20.3 (88.3) | -22.3 (54.3) | -14.7 (46.4) | 0.76 | 0.455 | 0.520 |

Per book HOLD / L6M Delta $/wk: D6-LIVE | best-by-PRE registered cell (pts/trade = Delta pts per signal):
| book | D6L HOLD (MDE) | D6L L6M | D6L 2026 | D6L pts/sig HOLD | D6L fill HOLD | D6L P(tgt|fill) | best cell | best HOLD | best L6M | best pts/sig HOLD |
|--|--|--|--|--|--|--|--|--|--|--|
| DN | -6.7 (15.2) | -8.8 | -3.8 | -1.38 | 0.76 | 0.447 | A1_timer|-|X5|T120_mkt|b2 | -1.9 | -3.1 | -0.38 |
| HM | -8.6 (26.4) | -13.5 | -16.8 | -1.36 | 0.68 | 0.421 | A1_timer|-|X5|T120_skip|b3 | -10.7 | -13.3 | -1.70 |
| KB | -0.2 (16.4) | -2.4 | -1.8 | -0.05 | 0.67 | 0.412 | B2_pair|PAIR4|X0|mkt|b0 | 1.2 | 0.9 | 0.28 |
| MA | -7.3 (10.2) | -8.7 | -10.0 | -2.45 | 0.74 | 0.437 | B2_pair|PAIR8|X.5stop|lim|b3 | -7.3 | -14.4 | -2.47 |
| MV | 7.0 (17.8) | 6.5 | -23.0 | 0.89 | 0.79 | 0.429 | B1_gate|IMB5_F30|X0|mkt|b0 | -2.6 | -3.1 | -0.34 |
| PB | -20.6 (21.9) | -24.8 | -21.6 | -3.41 | 0.73 | 0.422 | B2_pair|PAIR7|X0|lim|b2 | -25.3 | -34.4 | -4.19 |
| PE | -1.0 (14.4) | -0.1 | 25.8 | -0.21 | 0.77 | 0.402 | B2_pair|PAIR2|X0|mkt|b0 | 4.2 | 6.7 | 0.92 |
| SM | 0.3 (9.3) | 2.3 | 8.7 | 0.15 | 0.72 | 0.450 | B1_gate|WALL_BID|X0|lim|b3 | 0.1 | 2.4 | 0.06 |
| ST | -6.3 (21.9) | -11.1 | -14.1 | -0.73 | 0.68 | 0.424 | B1_gate|BIG_PRINT|X0|lim|b0 | 7.4 | 4.1 | 0.86 |
| WT | 7.5 (17.9) | 3.4 | -4.5 | 0.91 | 0.52 | 0.494 | B2_pair|PAIR4|X5|lim|b3 | 12.3 | 9.7 | 1.48 |

## 2. Thin / thick book at the dip (proxy rel_tot8 := depth_rel; exact 8-tick same-minute median requested)
| gate (dip >= 10) | HOLD Delta | L6M | PRE | fill HOLD | P(target|fill) HOLD | P(target|fill) PRE | fills HOLD |
|--|--|--|--|--|--|--|--|
| thin07 | -15.5 (152.5) | -61.2 | -24.6 | 0.47 | 0.436 | 0.422 | 5068 |
| thin05 | -25.7 (191.2) | -76.3 | -26.7 | 0.17 | 0.414 | 0.392 | 1794 |
| thick15 | -26.4 (149.0) | -49.2 | -25.6 | 0.27 | 0.390 | 0.384 | 2950 |
| thick20 | -41.4 (185.3) | -72.8 | -26.8 | 0.08 | 0.328 | 0.340 | 897 |
| thin07_x3of8 | -20.9 (175.1) | -68.9 | -25.5 | 0.31 | 0.412 | 0.398 | 3343 |
| thin05_x3of8 | -32.8 (196.0) | -83.3 | -22.1 | 0.09 | 0.388 | 0.371 | 998 |
| thick15_x3of8 | -41.6 (164.3) | -73.0 | -20.5 | 0.12 | 0.339 | 0.352 | 1287 |
| thick20_x3of8 | -32.0 (193.7) | -73.2 | -22.4 | 0.02 | 0.336 | 0.289 | 241 |

Plain line: a dip bought in a thin book (depth_rel <= 0.7) reaches the target 44% (HOLD) / 42% (PRE) vs 39% / 38% in a thick one (>= 1.5) and 33% / 34% (>= 2.0); all-signal rate 52% (library target, not comparable to target-from-fill). Direction: thin is better than thick for dips here, the opposite of the hypothesis; none of the thin/thick cells has a Delta above 0 in HOLD or PRE.

## 3. Dollar split incl. SKIPPED-BY-STOP (HOLD; $ over the window; per book for the PRE-best cell, then D6-LIVE; net of the six = the gate value)
| book/cell | skipped by stop (n, $) | skipped winners | other skipped losers | cheaper-fill winners | cheaper-fill losers | converted L->W | W->L | total |
|--|--|--|--|--|--|--|--|--|
| DN A1_timer|-|X5|T120_mkt|b2 | 0, 0 | 2, -22,223 | 0, 0 | 404, -6,920 | 341, 9,853 | 16, 351,330 | 19, -391,901 | -59,861 |
| HM A1_timer|-|X5|T120_skip|b3 | 59, 722,774 | 280, -2,985,425 | 122, 1,409,566 | 262, 262,000 | 273, 22,753 | 12, 226,362 | 0, 0 | -341,971 |
| KB B2_pair|PAIR4|X0|mkt|b0 | 189, 1,203,969 | 373, -2,094,654 | 201, 1,210,003 | 303, -28,016 | 269, 107,796 | 6, 72,869 | 33, -432,229 | 39,738 |
| MA B2_pair|PAIR8|X.5stop|lim|b3 | 32, 392,013 | 214, -2,337,009 | 2, 4,945 | 48, 340,000 | 130, 59,415 | 48, 1,306,241 | 0, 0 | -234,396 |
| MV B1_gate|IMB5_F30|X0|mkt|b0 | 120, 1,470,048 | 135, -1,499,166 | 3, 14,842 | 471, -2,621 | 461, 457,100 | 24, 407,395 | 37, -931,800 | -84,202 |
| PB B2_pair|PAIR7|X0|lim|b2 | 192, 2,352,077 | 217, -2,391,669 | 1, 3,197 | 254, -15,788 | 216, -16,553 | 23, 511,411 | 62, -1,252,197 | -809,522 |
| PE B2_pair|PAIR2|X0|mkt|b0 | 432, 2,963,617 | 332, -2,040,247 | 8, 11,272 | 276, -54,954 | 192, 16,576 | 9, 100,632 | 62, -861,920 | 134,977 |
| SM B1_gate|WALL_BID|X0|lim|b3 | 13, 117,849 | 26, -213,684 | 0, 0 | 162, -70,189 | 141, 2,111 | 15, 256,636 | 6, -89,607 | 3,117 |
| ST B1_gate|BIG_PRINT|X0|lim|b0 | 140, 1,715,056 | 224, -2,459,721 | 162, 1,949,753 | 451, -32,357 | 325, 63,750 | 19, 406,314 | 61, -1,404,548 | 238,246 |
| WT B2_pair|PAIR4|X5|lim|b3 | 295, 1,910,208 | 1023, -4,173,795 | 338, 2,127,437 | 99, 178,150 | 110, 7,980 | 28, 343,349 | 0, 0 | 393,328 |
| DN D6L | 5, 61,252 | 182, -2,006,823 | 0, 0 | 243, 45,734 | 316, 1,024,450 | 36, 660,310 | 0, 0 | -215,077 |
| HM D6L | 6, 73,502 | 270, -2,928,261 | 51, 604,711 | 272, 101,811 | 369, 1,172,050 | 40, 702,195 | 0, 0 | -273,991 |
| KB D6L | 3, 19,111 | 355, -2,008,235 | 96, 607,976 | 354, 49,820 | 523, 884,858 | 43, 439,072 | 0, 0 | -7,398 |
| MA D6L | 2, 24,501 | 121, -1,321,178 | 1, 1,647 | 141, 39,305 | 194, 692,050 | 15, 331,038 | 0, 0 | -232,636 |
| MV D6L | 5, 61,252 | 262, -2,899,971 | 1, 947 | 381, 82,141 | 539, 1,797,150 | 63, 1,181,817 | 0, 0 | 223,336 |
| PB D6L | 4, 49,002 | 251, -2,756,147 | 2, 2,095 | 282, 83,175 | 388, 1,232,250 | 38, 731,782 | 0, 0 | -657,843 |
| PE D6L | 10, 68,602 | 297, -1,826,121 | 0, 0 | 373, 43,620 | 572, 1,057,476 | 59, 625,515 | 0, 0 | -30,908 |
| SM D6L | 2, 18,131 | 89, -731,330 | 10, 82,807 | 105, 8,251 | 138, 332,371 | 19, 297,823 | 0, 0 | 8,053 |
| ST D6L | 10, 122,504 | 364, -3,966,574 | 73, 869,570 | 372, 87,454 | 512, 1,701,300 | 51, 983,522 | 0, 0 | -202,224 |
| WT D6L | 31, 200,734 | 731, -2,984,425 | 151, 944,153 | 391, 9,531 | 493, 1,090,005 | 96, 981,452 | 0, 0 | 241,450 |

Per entry session (HOLD, PRE-best cell per book): 
* DN: asia: total -163,224, skipped-by-stop 0 (0), skipped winners 0 (0); close: total -15,109, skipped-by-stop 0 (0), skipped winners 0 (0); london: total -92,248, skipped-by-stop 0 (0), skipped winners 0 (0); nyam: total 205,698, skipped-by-stop 0 (0), skipped winners 2 (-22,223); nypm: total 4,062, skipped-by-stop 0 (0), skipped winners 0 (0); pre: total 960, skipped-by-stop 0 (0), skipped winners 0 (0)
* HM: asia: total -123,653, skipped-by-stop 10 (122,504), skipped winners 104 (-1,155,206); close: total 1,000, skipped-by-stop 0 (0), skipped winners 0 (0); london: total -9,036, skipped-by-stop 20 (245,008), skipped winners 69 (-766,420); nyam: total -262,396, skipped-by-stop 11 (134,754), skipped winners 56 (-609,652); nypm: total 51,603, skipped-by-stop 14 (171,506), skipped winners 44 (-376,405); pre: total 511, skipped-by-stop 4 (49,002), skipped winners 7 (-77,741)
* KB: asia: total 64,367, skipped-by-stop 12 (76,442), skipped winners 81 (-467,875); close: total -281, skipped-by-stop 1 (6,370), skipped winners 1 (-5,768); london: total -127,299, skipped-by-stop 6 (38,221), skipped winners 58 (-335,022); nyam: total 145,865, skipped-by-stop 123 (783,536), skipped winners 137 (-778,176); nypm: total -40,460, skipped-by-stop 38 (242,068), skipped winners 83 (-432,720); pre: total -2,453, skipped-by-stop 9 (57,332), skipped winners 13 (-75,094)
* MA: asia: total -303, skipped-by-stop 15 (183,756), skipped winners 70 (-777,472); close: total 7,500, skipped-by-stop 0 (0), skipped winners 0 (0); london: total 4,131, skipped-by-stop 8 (98,003), skipped winners 57 (-632,402); nyam: total -141,551, skipped-by-stop 2 (24,501), skipped winners 44 (-486,231); nypm: total -54,169, skipped-by-stop 5 (61,252), skipped winners 33 (-329,808); pre: total -50,003, skipped-by-stop 2 (24,501), skipped winners 10 (-111,096)
* MV: asia: total -37,080, skipped-by-stop 1 (12,250), skipped winners 5 (-55,518); close: total 20,500, skipped-by-stop 1 (12,250), skipped winners 0 (0); london: total 46,986, skipped-by-stop 7 (85,753), skipped winners 3 (-33,335); nyam: total -423, skipped-by-stop 75 (918,780), skipped winners 82 (-910,591); nypm: total -24,483, skipped-by-stop 34 (416,514), skipped winners 40 (-444,184); pre: total -89,703, skipped-by-stop 2 (24,501), skipped winners 5 (-55,538)
* PB: asia: total -327,965, skipped-by-stop 100 (1,225,040), skipped winners 126 (-1,399,442); close: total 0, skipped-by-stop 0 (0), skipped winners 0 (0); london: total -200,274, skipped-by-stop 60 (735,024), skipped winners 69 (-747,972); nyam: total -97,458, skipped-by-stop 14 (171,506), skipped winners 8 (-88,833); nypm: total -119,532, skipped-by-stop 14 (171,506), skipped winners 8 (-88,833); pre: total -64,292, skipped-by-stop 4 (49,002), skipped winners 6 (-66,590)
* PE: asia: total -9,381, skipped-by-stop 159 (1,090,776), skipped winners 155 (-964,084); close: total 6,860, skipped-by-stop 1 (6,860), skipped winners 0 (0); london: total -161,033, skipped-by-stop 91 (624,280), skipped winners 86 (-532,184); nyam: total 227,430, skipped-by-stop 94 (644,861), skipped winners 36 (-220,953); nypm: total 83,442, skipped-by-stop 68 (466,495), skipped winners 44 (-254,613); pre: total -12,341, skipped-by-stop 19 (130,344), skipped winners 11 (-68,414)
* SM: asia: total 16,266, skipped-by-stop 0 (0), skipped winners 2 (-16,445); close: total 19,055, skipped-by-stop 1 (9,065), skipped winners 0 (0); london: total -1,539, skipped-by-stop 2 (18,131), skipped winners 2 (-16,430); nyam: total -41,001, skipped-by-stop 8 (72,522), skipped winners 19 (-156,170); nypm: total -35,072, skipped-by-stop 1 (9,065), skipped winners 3 (-24,638); pre: total 45,408, skipped-by-stop 1 (9,065), skipped winners 0 (0)
* ST: asia: total 395,547, skipped-by-stop 26 (318,510), skipped winners 73 (-810,667); close: total -3,242, skipped-by-stop 0 (0), skipped winners 1 (-11,092); london: total -193,469, skipped-by-stop 22 (269,509), skipped winners 65 (-712,935); nyam: total -8,638, skipped-by-stop 56 (686,022), skipped winners 53 (-578,246); nypm: total 22,487, skipped-by-stop 28 (343,011), skipped winners 25 (-269,061); pre: total 25,560, skipped-by-stop 8 (98,003), skipped winners 7 (-77,721)
* WT: asia: total 61,976, skipped-by-stop 51 (330,239), skipped winners 293 (-1,201,290); close: total 8,861, skipped-by-stop 2 (12,951), skipped winners 1 (-4,089); london: total 198,651, skipped-by-stop 42 (271,962), skipped winners 216 (-885,574); nyam: total -59,336, skipped-by-stop 111 (718,756), skipped winners 288 (-1,170,683); nypm: total 148,380, skipped-by-stop 68 (440,319), skipped winners 176 (-711,247); pre: total 34,795, skipped-by-stop 21 (135,981), skipped winners 49 (-200,913)

## 4. Joint cell with L2 trade-health rules on the exact lock engine (books ST HM WT KB SM PE, live lots, BASE lock spec; stack as is = market entries)
Weekly Delta mean vs stack as is, k$ (MDE); SD, maxDD of the cell stack in HOLD; worst-20-weeks over PRE+HOLD (stack as is -3,668.9 k$):
| line | 2026 | L6M | HOLD | PRE | X' | HOLD SD (base 162.5) | HOLD maxDD (base 696.2) | W20 PRE+HOLD |
|--|--|--|--|--|--|--|--|--|
| D6-LIVE entry alone | 64.1 (121.8) | -13.0 (58.2) | -8.5 (56.2) | -29.9 (32.9) | -16.0 (35.8) | 121.7 | 889.7 | -3,119.5 |
| profit rule alone (base entries) | 28.1 (108.7) | -16.3 (38.5) | -16.5 (37.6) | -9.5 (22.5) | -1.0 (23.9) | 139.6 | 725.6 | -3,747.3 |
| loss rule 3x alone | -2.3 (91.6) | -33.3 (42.4) | -28.4 (38.9) | -35.1 (28.6) | 0.7 (33.1) | 128.4 | 784.3 | -3,508.0 |
| loss rule 10x alone | -2.3 (91.7) | -32.3 (41.8) | -27.7 (38.3) | -34.2 (28.6) | 0.9 (32.9) | 128.0 | 761.8 | -3,508.2 |
| loss rule 20x alone | -3.3 (92.3) | -32.1 (41.5) | -27.2 (37.6) | -35.1 (28.6) | 1.0 (32.8) | 128.7 | 771.0 | -3,488.2 |
| JOINT entry+profit+loss 3x | 40.5 (122.6) | -28.0 (58.9) | -21.8 (62.0) | -40.9 (37.7) | -10.7 (38.5) | 98.5 | 762.5 | -2,803.5 |
| JOINT entry+profit+loss 10x | 40.4 (122.6) | -28.2 (59.0) | -22.0 (62.1) | -40.9 (37.7) | -10.4 (38.5) | 98.5 | 763.0 | -2,793.8 |
| JOINT entry+profit+loss 20x | 39.7 (122.6) | -28.7 (59.4) | -22.8 (62.3) | -38.6 (36.8) | -8.8 (38.5) | 99.2 | 769.1 | -2,744.9 |
Rule definitions as registered (proxies: depth_rel >= 1.5 on two consecutive 10-s ticks for the 8-tick depth; pulled_sup10 / (depth10/20) for cancelled own-side size). Reading: the loss cut and the profit trail each cost money on the engine; the joint line is no better than D6-LIVE alone. Needed exact features are in L2FEAT_REQUESTS.txt.

## 5. RECENT FIRST
### 5a. Top 15 cells by L6M (HOLD tie-break; pooled PRE/X' as sanity) - ranking selects on HOLD; RC over all ranked cells p(L6M) = 0.55, p(HOLD) = 0.42, p(PRE) = 0.85
| cell | 2026 | L6M | HOLD | PRE | X' | fill L6M | label |
|--|--|--|--|--|--|--|--|
| A1_timer|-|X10|T1800_mkt|b1 | 31.8 (94.5) | 26.7 (41.7) | 28.5 (38.3) | -10.4 | 1.8 | 0.90 | CANDIDATE-RECENT |
| B1_gate|BIG_PRINT|X0|lim|b0 | -40.8 (188.0) | 24.3 (135.0) | 46.8 (132.0) | 33.3 | -5.5 | 0.63 |  |
| A1_timer|-|X5|T1800_mkt|b1 | 10.3 (49.8) | 22.5 (29.5) | 22.3 (26.5) | 1.6 | 1.8 | 0.95 | CANDIDATE-RECENT |
| B1_gate|MICRO_CROSS|X5|mkt|b1 | 19.4 (92.6) | 21.2 (62.2) | 26.3 (58.5) | -11.5 | 2.6 | 0.82 | CANDIDATE-RECENT |
| D_learned|LGB_th2|X5|mkt|b1 | -18.2 (86.1) | 20.4 (67.6) | 26.7 (64.1) | -21.9 | -25.9 | 0.81 |  |
| D_learned|LGB_th0|X5|mkt|b1 | -18.2 (86.1) | 20.4 (67.6) | 26.7 (64.1) | -21.9 | -26.7 | 0.81 |  |
| D_learned|LGB_th1|X5|mkt|b1 | -18.2 (86.1) | 20.4 (67.6) | 26.7 (64.1) | -21.9 | -26.7 | 0.81 |  |
| A1_timer|-|X10|T900_mkt|b1 | 31.1 (72.2) | 20.1 (34.2) | 20.9 (30.8) | -11.9 | 4.3 | 0.93 | CANDIDATE-RECENT |
| A1_timer|-|X5|Topp_skip|b1 | -0.1 (55.9) | 19.9 (37.0) | 22.6 (35.8) | 3.8 | 5.4 | 0.91 |  |
| D_learned|LGB_th2|X0|mkt|b1 | -26.9 (64.8) | 19.4 (53.5) | 23.5 (48.4) | -19.0 | -12.9 | 0.85 |  |
| A1_timer|-|X10|Topp_skip|b1 | 18.1 (101.5) | 19.1 (55.8) | 24.4 (58.1) | -6.2 | 2.6 | 0.82 | CANDIDATE-RECENT |
| D_learned|LGB_th0|X0|mkt|b1 | -22.3 (59.9) | 18.5 (42.7) | 21.1 (37.6) | -19.4 | -5.7 | 0.88 |  |
| A1_timer|-|X5|T900_mkt|b1 | 17.4 (35.5) | 18.0 (26.7) | 16.8 (23.8) | 1.3 | 0.9 | 0.96 | CANDIDATE-RECENT |
| A1_timer|-|X.25stop|T1800_mkt|b1 | 27.3 (135.8) | 17.7 (52.5) | 23.0 (47.6) | -12.2 | 1.0 | 0.87 | CANDIDATE-RECENT |
| B1_gate|MICRO_CROSS|X5|lim|b1 | 11.6 (89.9) | 17.4 (58.8) | 23.4 (55.8) | -18.4 | 2.9 | 0.81 | CANDIDATE-RECENT |

Every label above carries: n = 45 L6M signals per week-scale as shown in MDE, 2026 alone is ~5 weeks; none survives RC. CANDIDATE-RECENT count 29 of 2083.
### 5b. Walk-forward adaptive variants (family A1/A2/B1/B2/C, per-book re-selection; WITH-HOLD = market when no cell has positive fit score)
| chain | 2026 | L6M | HOLD | PRE | X' (from 2023-07) |
|--|--|--|--|--|--|
| Q_trail12m | -157.4 (133.5) | -56.8 (101.8) | -29.9 (110.4) | 2.0 (55.8) | -37.3 (88.7) |
| Q_trail3m | -102.8 (198.9) | -63.9 (123.2) | -32.4 (141.2) | -22.2 (54.5) | -31.4 (82.6) |
| M_trail1m | -98.8 (115.0) | -59.6 (88.0) | -22.6 (123.3) | -17.2 (56.9) | -20.4 (54.5) |
PRE placebo for the 12m chain: rank 1.00 (random cell choices mean -17.6 k$/wk) - the selection beats random choices but not the market entry.

**LAST re-fit in full (the one live today): quarterly 12m-trailing, 2026-01-01; fit window = trades closed before the refit; cell, fills in window, fit score $:**
* DN: A1_timer|-|X.5stop|Topp_skip|b3 (fills 888, score 353,717)
* HM: A1_timer|-|X15|Topp_skip|b3 (fills 1360, score 429,880)
* KB: B1_gate|IMB5_F30|X5|lim|b3 (fills 1104, score 535,149)
* MA: B1_gate|IMB10_F30|X15|lim|b3 (fills 273, score 380,006)
* MV: A1_timer|-|X15|Topp_skip|b1 (fills 1921, score 1,039,079)
* PB: A1_timer|-|X20|T300_mkt|b3 (fills 1734, score 585,282)
* PE: B1_gate|IMB5_F20|X20|lim|b3 (fills 1347, score 759,725)
* SM: B1_gate|DELTA10_TURN|X5|mkt|b3 (fills 544, score 414,811)
* ST: B1_gate|IMB5_F20|X20|mkt|b3 (fills 1025, score 1,078,001)
* WT: B1_gate|IMB10_F30|X20|lim|b3 (fills 226, score 1,140,586)

Monthly 1m-trailing refit 2026-02-01: DN: B1_gate|OFI_TURN|X5|lim|b3; HM: A1_timer|-|X15|T900_mkt|b2; KB: A1_timer|-|X20|T1800_mkt|b2; MA: B1_gate|BIG_PRINT|X0|lim|b2; MV: B1_gate|BIG_PRINT|X0|lim|b2; PB: A1_timer|-|X20|T1800_mkt|b0; PE: B1_gate|IMB10_F30|X0|lim|b2; SM: B1_gate|MICRO_CROSS|X5|lim|b2; ST: B1_gate|ICEBERG|X0|mkt|b2; WT: B1_gate|MICRO_CROSS|X5|mkt|b1

Tonight (policy view): the chosen cells are mostly limit-at-best / bracket-3 (stop from fill, original target) gated on IMB5/IMB10 flips at X 15-20 plus timers on DN/HM/MV; they are fit on 12 months of closed trades and the chain they belong to lost money in 2026 and L6M, so they are NOT a recommendation.
### 5c. Gate drift: chosen gate (X, mode, bracket) by quarter, 12m-trailing chain
| book   | 2023-07-01             | 2023-10-01           | 2024-01-01           | 2024-04-01           | 2024-07-01            | 2024-10-01          | 2025-01-01          | 2025-04-01          | 2025-07-01          | 2025-10-01             | 2026-01-01             |
|:-------|:-----------------------|:---------------------|:---------------------|:---------------------|:----------------------|:--------------------|:--------------------|:--------------------|:--------------------|:-----------------------|:-----------------------|
| DN     | -/X1/T900_skip/b1      | -/X1/T900_skip/b1    | -/X6/T1800_mkt/b0    | -/X6/T1800_mkt/b2    | WALL_BID/X0/lim/b0    | BIG_PRINT/X0/lim/b2 | BIG_PRINT/X0/lim/b2 | -/X1/T120_mkt/b2    | -/X1/T120_mkt/b2    | -/X6/Topp_skip/b3      | -/X6/Topp_skip/b3      |
| HM     | -/X4/T900_skip/b3      | IMB5_F30/X4/lim/b3   | -/X4/T600_skip/b3    | -/X1/T120_skip/b2    | PAIR1/X0/lim/b0       | PAIR1/X0/mkt/b0     | PAIR1/X0/mkt/b0     | CONCORD/X0/lim/b3   | IMB5_F30/X0/mkt/b2  | -/X3/Topp_skip/b3      | -/X3/Topp_skip/b3      |
| KB     | PAIR8/X1/lim/b0        | -/X2/T120_skip/b2    | PAIR6/X0/lim/b0      | PAIR6/X0/lim/b0      | PAIR6/X0/mkt/b0       | PAIR1/X0/mkt/b0     | BIG_PRINT/X0/mkt/b2 | -/X6/T600_mkt/b2    | PAIR4/X0/mkt/b0     | IMB10_POS20/X1/lim/b3  | IMB5_F30/X1/lim/b3     |
| MA     | PAIR1/X0/mkt/b0        | PAIR2/X1/lim/b3      | -/X6/T900_mkt/b2     | WALL_BID/X0/mkt/b2   | -/X4/T600_mkt/b2      | -/X4/T600_mkt/b2    | OFI_TURN/X0/lim/b2  | PAIR9/X0/lim/b2     | IMB10_F30/X0/lim/b3 | IMB10_F30/X0/lim/b3    | IMB10_F30/X3/lim/b3    |
| MV     | PAIR5/X0/lim/b1        | PAIR0/X0/lim/b1      | PAIR5/X0/lim/b3      | PAIR5/X0/lim/b3      | WALL_BID/X0/mkt/b2    | BIG_PRINT/X0/mkt/b2 | BIG_PRINT/X0/mkt/b2 | BIG_PRINT/X0/mkt/b2 | PAIR1/X0/mkt/b0     | PAIR1/X0/lim/b0        | -/X3/Topp_skip/b1      |
| PB     | ABSORB/X1/lim/b0       | BIG_PRINT/X0/mkt/b2  | PAIR8/X1/mkt/b1      | WALL_BID/X0/lim/b0   | PAIR6/X0/lim/b0       | PAIR6/X0/lim/b0     | PAIR7/X0/mkt/b2     | PAIR7/X0/lim/b2     | PAIR7/X0/lim/b2     | IMB10_POS20/X3/lim/b3  | -/X4/T300_mkt/b3       |
| PE     | -/X2/T300_skip/b3      | -/X2/T300_skip/b3    | -/X2/T300_skip/b3    | -/X2/T300_skip/b3    | -/X2/T900_mkt/b0      | -/X2/T900_mkt/b0    | -/X2/T900_mkt/b0    | CONCORD/X2/mkt/b0   | PAIR4/X2/lim/b1     | PAIR1/X0/lim/b0        | IMB5_F20/X4/lim/b3     |
| SM     | -/X6/T900_mkt/b0       | -/X3/T1800_mkt/b2    | -/X3/T1800_mkt/b2    | PAIR6/X0/lim/b0      | PAIR6/X0/lim/b0       | ICEBERG/X1/lim/b2   | -/X6/T600_mkt/b3    | ICEBERG/X0/mkt/b2   | -/X3/T300_mkt/b2    | DELTA10_TURN/X1/mkt/b3 | DELTA10_TURN/X1/mkt/b3 |
| ST     | -/X6/Topp_skip/b2      | IMB10_F20/X4/lim/b3  | PAIR7/X4/lim/b3      | IMB10_F30/X0/mkt/b3  | BIG_PRINT/X0/mkt/b1   | PAIR1/X0/mkt/b0     | BIG_PRINT/X0/lim/b0 | BIG_PRINT/X0/lim/b0 | BIG_PRINT/X0/lim/b0 | BIG_PRINT/X0/lim/b0    | IMB5_F20/X4/mkt/b3     |
| WT     | DELTA30_TURN/X1/lim/b2 | IMB5_POS20/X1/lim/b3 | IMB5_POS20/X1/lim/b3 | IMB5_POS20/X1/lim/b3 | DELTA60_POS/X2/lim/b3 | PAIR6/X0/mkt/b2     | PAIR6/X0/mkt/b2     | PAIR7/X1/lim/b1     | PAIR3/X0/lim/b2     | PAIR1/X1/lim/b2        | IMB10_F30/X4/lim/b3    |
Drift read: the chosen gate changes almost every quarter in every book (IMB flips, DELTA turns and plain timers alternate); there is no persistent gate, which is why the chain does not beat the market entry.

## 6. Controls and families (recent-first; stack Delta k$/wk (MDE))
### 6a. Timer limits (pure timer, bracket 1 = original stop/original target; bracket 0 shown for until-opposite). Market entry = 0 by definition.
| X | T | fallback | br | 2026 | L6M | HOLD | PRE | X' | fill HOLD | P(tgt|fill) HOLD |
|--|--|--|--|--|--|--|--|--|--|--|
| 5 | T120_skip | | b0 | -56.0 (210.4) | -47.7 (102.4) | -25.7 (115.7) | 1.0 (58.7) | -8.0 (58.7) | 0.58 | 0.499 |
| 5 | T120_skip | | b1 | -47.8 (194.6) | -35.7 (98.8) | -14.4 (110.7) | 2.8 (53.2) | -6.8 (58.5) | 0.58 | 0.475 |
| 5 | T600_skip | | b0 | -46.0 (137.0) | -9.3 (64.0) | 2.8 (73.0) | 7.2 (41.8) | -11.3 (45.2) | 0.78 | 0.503 |
| 5 | T600_skip | | b1 | -39.4 (110.5) | 7.8 (56.7) | 17.3 (64.1) | 13.9 (34.3) | -8.2 (43.9) | 0.78 | 0.477 |
| 5 | T600_mkt | | b0 | -26.2 (91.1) | 9.0 (40.5) | 10.3 (37.0) | 1.2 (25.6) | 1.8 (21.8) | 0.97 | 0.513 |
| 5 | T600_mkt | | b1 | 9.7 (33.5) | 11.2 (24.3) | 9.6 (21.9) | 1.2 (12.6) | -0.2 (12.4) | 0.97 | 0.504 |
| 5 | T1800_mkt | | b0 | -12.0 (80.2) | 11.0 (33.4) | 11.5 (32.6) | -0.1 (26.2) | -1.2 (27.2) | 0.95 | 0.507 |
| 5 | T1800_mkt | | b1 | 10.3 (49.8) | 22.5 (29.5) | 22.3 (26.5) | 1.6 (16.0) | 1.8 (16.1) | 0.95 | 0.493 |
| 5 | Topp_skip | | b0 | -8.9 (75.9) | -2.2 (44.0) | 3.8 (44.8) | -5.1 (30.5) | 4.3 (27.5) | 0.91 | 0.501 |
| 5 | Topp_skip | | b1 | -0.1 (55.9) | 19.9 (37.0) | 22.6 (35.8) | 3.8 (19.2) | 5.4 (24.6) | 0.91 | 0.476 |
| 10 | T120_skip | | b0 | -67.0 (229.8) | -71.1 (133.7) | -36.2 (154.5) | -31.1 (80.0) | 6.1 (74.2) | 0.33 | 0.478 |
| 10 | T120_skip | | b1 | -48.1 (211.2) | -67.5 (125.0) | -35.4 (146.1) | -25.9 (74.7) | 6.6 (72.3) | 0.33 | 0.431 |
| 10 | T600_skip | | b0 | -25.4 (176.4) | -34.8 (97.6) | -9.9 (111.6) | -13.7 (65.5) | -4.0 (61.6) | 0.59 | 0.481 |
| 10 | T600_skip | | b1 | 13.5 (158.3) | -9.1 (84.1) | 8.8 (99.2) | -5.2 (59.5) | -4.9 (61.1) | 0.59 | 0.434 |
| 10 | T600_mkt | | b0 | -32.4 (138.1) | 4.9 (57.3) | 10.1 (51.0) | -10.5 (30.4) | 10.3 (27.3) | 0.94 | 0.503 |
| 10 | T600_mkt | | b1 | 15.4 (49.4) | 12.1 (27.9) | 12.5 (25.7) | -12.7 (20.5) | 3.3 (17.0) | 0.94 | 0.493 |
| 10 | T1800_mkt | | b0 | -12.9 (151.4) | 1.4 (59.8) | 10.8 (55.9) | -14.3 (37.9) | 7.2 (35.9) | 0.90 | 0.493 |
| 10 | T1800_mkt | | b1 | 31.8 (94.5) | 26.7 (41.7) | 28.5 (38.3) | -10.4 (26.4) | 1.8 (24.5) | 0.90 | 0.472 |
| 10 | Topp_skip | | b0 | -6.5 (99.1) | -15.1 (72.1) | -0.4 (75.1) | -20.3 (46.9) | -0.3 (45.0) | 0.82 | 0.477 |
| 10 | Topp_skip | | b1 | 18.1 (101.5) | 19.1 (55.8) | 24.4 (58.1) | -6.2 (36.2) | 2.6 (40.7) | 0.82 | 0.431 |
| 15 | T120_skip | | b0 | -111.7 (313.0) | -77.1 (156.0) | -37.9 (174.3) | -27.9 (89.7) | 6.8 (76.3) | 0.21 | 0.451 |
| 15 | T120_skip | | b1 | -116.4 (308.8) | -81.0 (148.1) | -42.4 (167.4) | -20.8 (84.4) | 8.8 (74.8) | 0.21 | 0.381 |
| 15 | T600_skip | | b0 | -40.8 (241.0) | -50.0 (127.9) | -19.5 (143.4) | -20.3 (75.2) | 1.1 (71.2) | 0.45 | 0.453 |
| 15 | T600_skip | | b1 | 1.3 (228.1) | -29.8 (110.7) | -2.2 (130.6) | -10.7 (67.4) | 1.9 (68.5) | 0.45 | 0.389 |
| 15 | T600_mkt | | b0 | -82.6 (98.2) | -4.1 (75.9) | -0.4 (66.7) | -9.0 (35.9) | 10.5 (31.2) | 0.93 | 0.494 |
| 15 | T600_mkt | | b1 | -10.6 (77.7) | 5.9 (36.4) | 8.4 (32.0) | -14.0 (25.7) | 2.2 (19.7) | 0.93 | 0.486 |
| 15 | T1800_mkt | | b0 | -44.6 (155.0) | -7.8 (72.2) | 3.1 (66.3) | -15.4 (43.5) | 8.8 (40.4) | 0.86 | 0.477 |
| 15 | T1800_mkt | | b1 | 25.1 (137.0) | 16.2 (55.1) | 22.5 (50.0) | -11.6 (31.6) | 0.1 (33.1) | 0.86 | 0.454 |
| 15 | Topp_skip | | b0 | -57.0 (109.6) | -44.3 (90.8) | -24.3 (97.8) | -15.8 (57.3) | -7.4 (58.5) | 0.73 | 0.446 |
| 15 | Topp_skip | | b1 | -21.8 (107.4) | -4.4 (66.4) | 7.0 (75.1) | -3.8 (45.4) | -3.0 (52.6) | 0.73 | 0.382 |
| 20 | T120_skip | | b0 | -147.6 (321.0) | -78.9 (161.7) | -39.4 (183.8) | -32.6 (98.4) | 4.9 (77.8) | 0.13 | 0.423 |
| 20 | T120_skip | | b1 | -160.1 (335.9) | -86.3 (155.5) | -46.1 (176.9) | -31.1 (94.4) | 5.4 (77.1) | 0.13 | 0.334 |
| 20 | T600_skip | | b0 | -77.9 (285.6) | -75.7 (141.1) | -39.6 (160.9) | -30.8 (82.7) | 5.5 (74.5) | 0.34 | 0.420 |
| 20 | T600_skip | | b1 | -40.5 (325.6) | -64.6 (130.9) | -28.7 (150.4) | -28.9 (75.2) | 4.3 (72.1) | 0.34 | 0.340 |
| 20 | T600_mkt | | b0 | -129.5 (119.0) | -20.4 (80.7) | -15.8 (71.0) | -6.1 (38.3) | 11.1 (32.0) | 0.91 | 0.487 |
| 20 | T600_mkt | | b1 | -24.2 (101.2) | -6.5 (44.3) | -3.1 (39.7) | -19.8 (28.1) | 2.0 (20.7) | 0.91 | 0.482 |
| 20 | T1800_mkt | | b0 | -52.6 (147.9) | -12.2 (85.2) | 1.4 (78.7) | -20.3 (43.5) | 7.8 (38.5) | 0.83 | 0.466 |
| 20 | T1800_mkt | | b1 | 13.7 (138.3) | -4.0 (70.2) | 6.8 (64.6) | -16.6 (33.9) | -0.1 (36.0) | 0.83 | 0.441 |
| 20 | Topp_skip | | b0 | -60.9 (133.6) | -61.6 (107.6) | -38.2 (118.3) | -25.6 (61.0) | -9.5 (62.2) | 0.65 | 0.415 |
| 20 | Topp_skip | | b1 | -18.1 (163.8) | -24.1 (84.2) | -6.6 (97.7) | -11.9 (51.0) | -8.8 (56.5) | 0.65 | 0.335 |
| .25stop | T120_skip | | b0 | -110.4 (310.9) | -77.5 (153.1) | -38.2 (171.5) | -31.3 (89.1) | 8.8 (77.0) | 0.22 | 0.461 |
| .25stop | T120_skip | | b1 | -114.8 (313.8) | -81.5 (146.4) | -44.3 (164.3) | -23.6 (83.7) | 10.0 (75.3) | 0.22 | 0.392 |
| .25stop | T600_skip | | b0 | -37.4 (237.4) | -50.7 (124.3) | -20.9 (139.9) | -23.2 (73.7) | 1.5 (71.7) | 0.47 | 0.460 |
| .25stop | T600_skip | | b1 | 2.4 (225.4) | -33.0 (107.6) | -7.2 (126.5) | -11.5 (66.4) | 2.0 (69.1) | 0.47 | 0.396 |
| .25stop | T600_mkt | | b0 | -82.8 (93.4) | -2.7 (72.9) | 1.8 (64.1) | -13.0 (35.0) | 10.9 (31.4) | 0.93 | 0.496 |
| .25stop | T600_mkt | | b1 | -13.2 (76.9) | 6.3 (33.3) | 8.9 (29.4) | -14.5 (25.6) | 1.9 (19.6) | 0.93 | 0.488 |
| .25stop | T1800_mkt | | b0 | -39.0 (156.4) | -4.3 (69.5) | 6.6 (63.9) | -18.6 (43.1) | 10.3 (40.4) | 0.87 | 0.482 |
| .25stop | T1800_mkt | | b1 | 27.3 (135.8) | 17.7 (52.5) | 23.0 (47.6) | -12.2 (31.3) | 1.0 (33.0) | 0.87 | 0.458 |
| .25stop | Topp_skip | | b0 | -48.7 (113.2) | -42.1 (88.8) | -22.9 (95.3) | -18.2 (55.9) | -7.6 (58.7) | 0.75 | 0.452 |
| .25stop | Topp_skip | | b1 | -18.0 (112.2) | -4.0 (64.9) | 5.6 (72.9) | -4.1 (44.3) | -4.1 (52.8) | 0.75 | 0.390 |
| .5stop | T120_skip | | b0 | -138.4 (335.4) | -76.7 (165.1) | -35.3 (188.8) | -22.8 (102.5) | 6.9 (80.6) | 0.07 | 0.374 |
| .5stop | T120_skip | | b1 | -149.6 (326.0) | -77.7 (162.4) | -36.5 (187.3) | -21.4 (100.5) | 5.4 (80.1) | 0.07 | 0.271 |
| .5stop | T600_skip | | b0 | -104.2 (318.0) | -85.1 (154.2) | -46.8 (177.8) | -32.1 (98.0) | 3.1 (80.8) | 0.23 | 0.363 |
| .5stop | T600_skip | | b1 | -105.7 (298.8) | -85.7 (144.1) | -46.1 (170.4) | -31.9 (90.8) | -3.3 (79.2) | 0.23 | 0.261 |
| .5stop | T600_mkt | | b0 | -125.7 (149.6) | -26.8 (84.8) | -21.8 (74.5) | -9.2 (40.1) | 8.2 (35.0) | 0.90 | 0.480 |
| .5stop | T600_mkt | | b1 | -38.7 (47.5) | -11.8 (46.0) | -9.0 (42.1) | -26.1 (29.6) | -3.0 (24.9) | 0.90 | 0.479 |
| .5stop | T1800_mkt | | b0 | -72.1 (123.8) | -18.5 (87.1) | 0.5 (82.9) | -31.8 (49.4) | 4.8 (40.3) | 0.80 | 0.447 |
| .5stop | T1800_mkt | | b1 | -10.4 (106.2) | -12.5 (72.5) | 0.2 (71.0) | -24.2 (41.2) | -10.6 (42.3) | 0.80 | 0.428 |
| .5stop | Topp_skip | | b0 | -63.2 (217.3) | -82.4 (120.7) | -54.1 (143.2) | -30.6 (75.5) | -17.3 (78.0) | 0.55 | 0.352 |
| .5stop | Topp_skip | | b1 | -41.9 (206.0) | -52.0 (98.0) | -32.1 (121.5) | -13.6 (64.9) | -29.4 (68.1) | 0.55 | 0.255 |
### 6b. Single gates, market entry, bracket 0 (original stop, target from fill): X = 0 / 10 / 20 (full 7-level grid in final_cells.csv)
| gate | X | 2026 | L6M | HOLD | PRE | X' | fill HOLD | P(tgt|fill) HOLD |
|--|--|--|--|--|--|--|--|--|
| ABSORB | 0 | -32.4 (76.8) | -18.0 (31.8) | -12.7 (29.4) | -8.1 (25.2) | -7.2 (22.9) | 0.99 | 0.515 |
| ABSORB | 10 | -35.5 (126.6) | -40.6 (84.9) | -22.3 (90.0) | -27.4 (56.1) | -22.3 (51.7) | 0.73 | 0.449 |
| ABSORB | 20 | -73.2 (172.2) | -75.1 (112.9) | -49.1 (124.2) | -32.4 (69.8) | -21.3 (66.7) | 0.58 | 0.384 |
| ANY | 0 | -43.1 (43.3) | -21.3 (24.1) | -18.7 (21.8) | -22.2 (18.0) | -14.2 (13.5) | 1.00 | 0.518 |
| ANY | 10 | -9.0 (115.4) | -26.7 (85.3) | -11.8 (85.9) | -22.0 (53.3) | -9.8 (46.8) | 0.78 | 0.463 |
| ANY | 20 | -40.7 (177.4) | -64.2 (108.5) | -43.9 (118.6) | -34.0 (65.7) | -20.6 (65.1) | 0.62 | 0.398 |
| BIG_PRINT | 0 | -68.7 (223.9) | 13.3 (136.3) | 37.3 (134.0) | 30.8 (63.3) | -7.0 (47.5) | 0.64 | 0.518 |
| BIG_PRINT | 10 | -64.5 (206.5) | -31.7 (170.7) | -0.1 (183.4) | -24.1 (90.4) | 9.4 (75.5) | 0.26 | 0.393 |
| BIG_PRINT | 20 | -111.0 (265.0) | -59.7 (168.4) | -20.2 (187.3) | -28.7 (98.9) | 1.0 (80.2) | 0.19 | 0.334 |
| CONCORD | 0 | -148.9 (229.3) | -27.8 (105.7) | -18.4 (112.0) | -20.3 (63.0) | -32.0 (58.0) | 0.64 | 0.515 |
| CONCORD | 10 | -123.8 (254.6) | -72.9 (153.3) | -37.2 (168.2) | -25.6 (82.2) | -7.0 (66.3) | 0.30 | 0.381 |
| CONCORD | 20 | -137.1 (304.9) | -67.2 (166.1) | -29.6 (184.2) | -30.8 (90.1) | -5.3 (73.0) | 0.23 | 0.329 |
| DELTA10_TURN | 0 | -51.6 (141.5) | -34.7 (47.3) | -28.5 (43.1) | -30.3 (32.0) | -11.8 (20.4) | 0.99 | 0.513 |
| DELTA10_TURN | 10 | -48.5 (88.8) | -28.0 (89.2) | -8.7 (94.5) | -38.8 (55.1) | -9.8 (47.3) | 0.73 | 0.450 |
| DELTA10_TURN | 20 | -103.2 (162.2) | -79.8 (118.2) | -52.5 (131.7) | -47.7 (66.2) | -22.9 (67.0) | 0.57 | 0.377 |
| DELTA30_TURN | 0 | -61.3 (68.6) | -33.0 (40.2) | -26.7 (37.8) | -31.5 (33.8) | -9.1 (18.3) | 0.97 | 0.512 |
| DELTA30_TURN | 10 | -92.3 (91.1) | -54.9 (96.4) | -30.7 (105.8) | -46.7 (58.4) | -9.7 (50.5) | 0.68 | 0.439 |
| DELTA30_TURN | 20 | -149.8 (180.7) | -89.2 (129.8) | -60.1 (141.9) | -48.0 (70.0) | -21.2 (67.8) | 0.53 | 0.369 |
| DELTA60_POS | 0 | -41.8 (72.5) | -22.1 (30.1) | -19.2 (27.0) | -19.5 (19.2) | -14.7 (18.8) | 1.00 | 0.518 |
| DELTA60_POS | 10 | -90.8 (85.1) | -57.2 (100.4) | -35.6 (106.2) | -43.5 (60.6) | -4.3 (50.6) | 0.68 | 0.439 |
| DELTA60_POS | 20 | -116.7 (200.9) | -77.1 (131.1) | -49.6 (143.1) | -46.4 (72.1) | -22.7 (65.6) | 0.51 | 0.369 |
| ICEBERG | 0 | -22.6 (46.9) | -22.1 (31.9) | -20.5 (28.3) | -19.4 (19.8) | -8.0 (16.1) | 1.00 | 0.517 |
| ICEBERG | 10 | 0.7 (136.1) | -24.2 (86.7) | -9.3 (87.3) | -19.1 (53.9) | -11.1 (48.5) | 0.77 | 0.460 |
| ICEBERG | 20 | -44.3 (178.9) | -62.4 (107.4) | -41.4 (117.2) | -34.1 (67.1) | -21.4 (64.6) | 0.61 | 0.395 |
| IMB10_F20 | 0 | -74.2 (83.6) | -1.5 (61.5) | 11.0 (56.4) | -20.5 (40.4) | -7.7 (35.4) | 0.84 | 0.508 |
| IMB10_F20 | 10 | -124.1 (178.2) | -61.3 (125.1) | -33.0 (135.0) | -39.4 (68.8) | -12.9 (61.1) | 0.48 | 0.404 |
| IMB10_F20 | 20 | -180.0 (245.8) | -97.1 (146.2) | -58.3 (164.8) | -39.1 (85.4) | -16.8 (72.4) | 0.35 | 0.330 |
| IMB10_F30 | 0 | -71.1 (223.4) | -73.1 (143.3) | -38.3 (142.2) | -15.6 (64.7) | -21.6 (65.7) | 0.54 | 0.499 |
| IMB10_F30 | 10 | -145.0 (278.2) | -91.6 (147.9) | -47.3 (175.2) | -29.1 (91.8) | -17.0 (79.9) | 0.25 | 0.377 |
| IMB10_F30 | 20 | -168.1 (339.3) | -93.1 (159.4) | -44.8 (185.6) | -38.3 (97.2) | -14.5 (82.6) | 0.17 | 0.309 |
| IMB10_POS20 | 0 | -88.4 (137.4) | -13.7 (56.3) | -13.5 (49.3) | -12.7 (39.7) | -18.4 (31.8) | 0.92 | 0.510 |
| IMB10_POS20 | 10 | -134.7 (147.4) | -44.8 (113.5) | -24.3 (114.5) | -27.7 (62.6) | -19.4 (47.3) | 0.59 | 0.426 |
| IMB10_POS20 | 20 | -158.7 (237.7) | -79.3 (136.4) | -51.5 (151.3) | -47.5 (79.1) | -14.2 (66.6) | 0.44 | 0.355 |
| IMB5_F20 | 0 | -64.1 (215.3) | -23.7 (72.7) | -13.7 (65.1) | -14.2 (41.5) | 2.4 (32.1) | 0.92 | 0.510 |
| IMB5_F20 | 10 | -159.1 (143.3) | -64.3 (137.0) | -42.1 (139.7) | -24.2 (65.0) | -7.0 (54.6) | 0.57 | 0.418 |
| IMB5_F20 | 20 | -184.4 (220.8) | -83.4 (150.3) | -53.6 (160.3) | -37.9 (80.0) | -23.3 (71.5) | 0.43 | 0.349 |
| IMB5_F30 | 0 | -73.4 (108.2) | -30.3 (103.0) | -29.3 (91.3) | 0.8 (53.0) | 10.1 (47.7) | 0.76 | 0.500 |
| IMB5_F30 | 10 | -149.1 (253.8) | -68.4 (143.3) | -42.8 (149.5) | -18.6 (75.6) | -10.3 (64.7) | 0.42 | 0.403 |
| IMB5_F30 | 20 | -194.7 (294.6) | -88.1 (158.5) | -53.2 (167.2) | -31.2 (87.8) | -7.8 (76.2) | 0.30 | 0.335 |
| IMB5_POS20 | 0 | -34.5 (121.8) | -20.8 (48.0) | -13.8 (43.4) | -12.5 (36.5) | -7.2 (22.4) | 0.97 | 0.513 |
| IMB5_POS20 | 10 | -102.3 (103.8) | -42.8 (112.5) | -24.1 (112.3) | -28.1 (63.8) | -12.9 (52.0) | 0.66 | 0.435 |
| IMB5_POS20 | 20 | -127.2 (218.1) | -74.9 (133.1) | -44.7 (145.6) | -42.3 (74.4) | -16.4 (66.7) | 0.50 | 0.367 |
| MICRO_CROSS | 0 | -50.3 (123.4) | -41.5 (41.3) | -33.7 (38.2) | -12.2 (24.9) | -12.1 (17.0) | 0.99 | 0.513 |
| MICRO_CROSS | 10 | -25.0 (95.6) | -33.0 (90.3) | -15.5 (93.1) | -31.6 (52.1) | -13.5 (45.6) | 0.73 | 0.447 |
| MICRO_CROSS | 20 | -91.9 (184.3) | -84.7 (117.2) | -55.3 (129.8) | -38.5 (65.4) | -21.8 (66.3) | 0.57 | 0.376 |
| OFI_TURN | 0 | -59.8 (168.5) | -28.7 (56.9) | -25.9 (50.4) | -22.3 (26.2) | -12.3 (18.5) | 0.97 | 0.511 |
| OFI_TURN | 10 | -44.5 (99.0) | -41.1 (97.4) | -21.4 (100.8) | -29.8 (54.8) | -7.6 (49.5) | 0.72 | 0.447 |
| OFI_TURN | 20 | -117.1 (179.5) | -83.1 (114.6) | -56.4 (127.7) | -37.9 (69.4) | -18.2 (68.3) | 0.56 | 0.377 |
| PULL_ASK | 0 | -25.1 (76.9) | -25.5 (32.3) | -21.2 (29.4) | -16.1 (22.3) | -11.3 (16.8) | 0.99 | 0.516 |
| PULL_ASK | 10 | -53.1 (86.9) | -39.6 (97.9) | -21.6 (99.8) | -32.3 (53.6) | -2.6 (51.5) | 0.71 | 0.446 |
| PULL_ASK | 20 | -95.1 (177.3) | -74.8 (115.7) | -50.0 (130.1) | -40.8 (67.5) | -20.8 (67.9) | 0.55 | 0.378 |
| SWEEP_FAIL | 0 | -37.9 (82.3) | -29.6 (32.4) | -25.9 (29.1) | -25.7 (21.1) | -14.1 (18.5) | 1.00 | 0.516 |
| SWEEP_FAIL | 10 | -48.9 (89.5) | -33.2 (90.8) | -15.1 (94.8) | -36.8 (56.8) | -7.9 (46.4) | 0.73 | 0.450 |
| SWEEP_FAIL | 20 | -98.1 (179.3) | -80.6 (118.9) | -52.9 (132.1) | -44.1 (67.4) | -24.0 (67.1) | 0.57 | 0.378 |
| WALL_BID | 0 | -172.2 (182.1) | -35.5 (97.7) | -28.0 (86.6) | -14.5 (49.1) | 20.7 (48.7) | 0.81 | 0.495 |
| WALL_BID | 10 | -153.5 (203.4) | -53.3 (138.1) | -30.4 (139.4) | -33.8 (74.4) | -2.9 (64.7) | 0.47 | 0.403 |
| WALL_BID | 20 | -153.9 (283.3) | -71.9 (156.5) | -46.9 (163.7) | -35.5 (84.9) | -10.0 (74.4) | 0.35 | 0.335 |
### 6c. Best pairs, learned gate, staged (best 4 each by L6M)
**B2_pair** (pairs are of the PRE top-5 singles: BIG_PRINT...)
* B2_pair|PAIR8|X5|mkt|b1 ('ABSORB', 'MICRO_CROSS'): 33.7 (164.5) | 12.6 (88.5) | 22.2 (85.8) | -22.8 (45.7) | -2.9 (47.0); fill HOLD 0.69
* B2_pair|PAIR8|X5|lim|b1 ('ABSORB', 'MICRO_CROSS'): 26.9 (166.1) | 9.3 (85.7) | 20.0 (84.5) | -24.9 (46.7) | -1.5 (47.7); fill HOLD 0.68
* B2_pair|PAIR8|X0|mkt|b2 ('ABSORB', 'MICRO_CROSS'): 0.3 (96.7) | 8.8 (63.6) | 14.4 (58.9) | -12.2 (30.9) | -3.9 (36.6); fill HOLD 0.94
* B2_pair|PAIR8|X0|lim|b2 ('ABSORB', 'MICRO_CROSS'): -10.6 (125.4) | 5.1 (64.2) | 11.7 (59.6) | -16.5 (31.2) | 0.8 (37.5); fill HOLD 0.93
**D_learned**
* D_learned|LGB_th2|X5|mkt|b1: -18.2 (86.1) | 20.4 (67.6) | 26.7 (64.1) | -21.9 (34.0) | -25.9 (52.6); fill HOLD 0.81
* D_learned|LGB_th0|X5|mkt|b1: -18.2 (86.1) | 20.4 (67.6) | 26.7 (64.1) | -21.9 (34.0) | -26.7 (53.2); fill HOLD 0.81
* D_learned|LGB_th1|X5|mkt|b1: -18.2 (86.1) | 20.4 (67.6) | 26.7 (64.1) | -21.9 (34.0) | -26.7 (53.2); fill HOLD 0.81
* D_learned|LGB_th2|X0|mkt|b1: -26.9 (64.8) | 19.4 (53.5) | 23.5 (48.4) | -19.0 (28.7) | -12.9 (46.4); fill HOLD 0.85
**C_staged**
* C_staged|ICEBERG|X-|0-10-20_orig|b0: -0.1 (99.6) | -8.2 (51.5) | -0.8 (55.9) | -18.4 (32.7) | -12.4 (32.6); fill HOLD 1.00
* C_staged|ANY|X-|0-10-20_orig|b0: -9.1 (84.6) | -9.5 (51.7) | -2.1 (55.7) | -18.3 (32.0) | -12.3 (32.9); fill HOLD 1.00
* C_staged|ABSORB|X-|0-10-20_orig|b0: -19.0 (90.8) | -18.7 (55.7) | -7.7 (61.1) | -18.2 (36.2) | -15.1 (36.6); fill HOLD 0.99
* C_staged|IMB10_POS20|X-|0-10-20_orig|b0: -77.4 (148.5) | -21.5 (82.0) | -11.2 (86.3) | -23.4 (47.3) | -7.9 (38.6); fill HOLD 0.92
Learned gate (LightGBM walk-forward, 10 quarterly refits from 2023-10-01): best cell PRE -14.7, HOLD 28.2 k$/wk; median PRE -35.3 - it picks a gate that fires at 65% of signals and is worse than market in PRE; DEAD.
### 6d. Random-gate placebo (PRE rank of real vs 20 random gates at the same fill count; top 8)
| gate      |   lv |     real |   rand_mean |   rand_sd |   rank |   p_tick |
|:----------|-----:|---------:|------------:|----------:|-------:|---------:|
| BIG_PRINT |    0 |  30828.8 |     -9048.9 |    8151.9 |      1 |      0   |
| ICEBERG   |    2 | -19103.1 |    -25649   |    2205   |      1 |      0.6 |
| ICEBERG   |    3 | -17774.3 |    -24041.7 |    2030.6 |      1 |      0.7 |
| ABSORB    |    4 | -32354.5 |    -39303   |    2934.8 |      1 |      0.3 |
| IMB5_F30  |    0 |    795.6 |    -14517.1 |    6893.3 |      1 |      0   |
| ICEBERG   |    5 | -18565.8 |    -26053.6 |    1932.8 |      1 |      0.7 |
| IMB5_F30  |    2 | -18583.2 |    -28963.7 |    5090.1 |      1 |      0   |
| CONCORD   |    1 | -11891.9 |    -24430.1 |    6629.2 |      1 |      0   |

## 7. Method, deviations, disclosures
* Signals = THP taken-signal series of each book (the base busy chain); signals the base blocked while a position was open, which a skipped/late arm would free, are NOT modelled; opposite-signal expiry uses the raw pre-chain events for ST HM WT KB SM and the next opposite taken signal for the others. The exact lock engine runs on the modified rows (entry sample, price, exit sample) with the busy rule re-applied; engine books ST HM WT KB SM PE only (live lots).
* Arm also dies when the ORIGINAL target level is touched (added; otherwise a dip after a 60-pt run-away is bought). Gates evaluated on 10-s ticks (l2feat grid), fills at the next print (market, close + 1 tick) or limit at the tick close with touch fills (optimistic; a 1-tick trade-through variant is registered: 24 cells, all negative PRE). D6 session lots 0 / time block not modelled.
* Gate proxies (sweep reclaim, big print side, absorption holds, 8-tick depth) are labelled in the prereg; exact features requested (L2FEAT_REQUESTS.txt).
* X' contaminated (two dry-run prints of X' aggregates before the look; nothing changed after). Learned cells scored in X' only from 2023-10-01. CR not simulated. Pairs = PRE top-5 singles by the registered rule.
* maxDD gate is evaluated only for cells run through the engine (the two per-book selections of the 6 engine books); others FAIL by default as registered. cost gate approximated as -0.25 pt per fill. The random-gate placebo exists for B1 market bracket-0 cells only (other families FAIL the placebo gate as registered).
* Ranking by L6M uses HOLD data already looked at; RC kept over all ranked cells.

## 8. Candidate policy / nightly script
Entry section candidate (not for live) written to l2vast/ds3/out/dipentry/policy_entry_candidate.txt: cells >= 0 in 2026, L6M and HOLD on measured fills (KB, PE, SM PRE-best cells) with the header numbers, all labelled V2 DEAD / CANDIDATE-RECENT with MDE. Nightly re-fit: l2vast/ds3/code/dipentry/de_nightly.py (rebuilds ticks for new months, reruns the grid and prints the walk-forward choice per book; capped at 2026-02-06 until the data window moves).