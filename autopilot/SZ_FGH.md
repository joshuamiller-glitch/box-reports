# SZ_FGH - families F (time/session), G (signal quality), H (regime) + K slice (P7 lot table), refreshed 2026-11-09 14:23Z

Label: PRE-PROOF, post-hoc, Shadow only, FIRST-ORDER on S1b-COMB (pnl per lot x lots; mean unreliable, drawdown ranking usable), no PASS claims, entry match < .85. Prereg SZ_FGH_PREREG.md (sha in DECISIONS.md). 5230 cells x 3 bases (COMB live, NOCUT, UNIF controls). Ledger /mnt/l2/l2vast/_th_sz/ledger_FGH*.parquet; lots ratios of top cells M_FGH.npz.

Reading: cut = maxDD cut vs Q1-A at equal lots (objective a, + = shallower); eq-mean cut = objective b (every cell scaled by one global factor so L6M mean = Q1-A, size-down-everything cannot win); SEL = mean of eq-mean cut on L6M/PRE/X'; w20/Ulcer = cell/ref on L6M at equal lots (<1 better); $/wk per $1k = L6M mean change per $1k of L6M maxDD removed (+ = the cell also gains mean); p own = lot ratio permuted within book x session (100 draws), "degenerate" = whole book x session group moved, placebo cannot vary; p fam = max-stat over all cells (about 1 for everything with 5230 cells: labelled, not used to kill). All numbers are sz_core.Z.score (SZ-CORE convention: rolling windows as of 2026-11-09, maxDD/worst-20/Ulcer on ALL weeks of the window, carrying week dropped from means only); my own scorer (complete weeks only) agrees on L6M/PRE maxDD cuts exactly and differs in the equal-mean columns (L6M mean window), see section 8. Base data end 2026-10-30. Placebo p own = fgh SEL statistic (permutation within book x session, 100 draws); finalists also get sz_core placebo p (L6M/PRE cut).
Unavailable and proxied: DS7 St1Dist/signal-state arrays are not owned at trade level (proxies: dip size, EMA/TWAP slope, TWAP deviation, zone distances, EX-FEAT entry-second L2 features, 83% matched); L2 confirmation count is a proxy; no volume in nq1m_state (TWAP not VWAP); ES/RTY 1-s data ends 2026-10-16 (later trades neutral).
Calendar: FOMC/CPI/NFP dates entered from public schedules (memory); CHECKED against the owned NQ 1-min bars: median 08:30 ET one-minute range on listed CPI days 12.6x the pre-open norm (norm 2.1x), NFP 9.8x, FOMC 14:00 10.0x; 83% of CPI and 97% of FOMC days sit above the 90th percentile of all days; two NFP entries were wrong (2024-10 should be 10-04; 2025-10 had no release) and were fixed; the 08:30 spikes not on my list are PPI/ECI days (not used). Opex = 3rd Friday, roll_wk = days 7-14 of Mar/Jun/Sep/Dec, half-days = day after Thanksgiving, Dec 24, Jul 3 weekdays. Not checked against an official file.

## 1. Walk-forward of the picking procedure (purged monthly, 26 w train, 7 d embargo, 2024-01..2026-10, picks max equal-mean maxDD cut on the train weeks, 34 months)
| subset | OOS maxDD cut raw % | at equal mean % | d mean $/wk | w20 OOS/ref | picks/months |
|--|--|--|--|--|--|
| COMB F | -0.0 | -18.8 | -2618 | 1.00 | 34/34 |
| COMB G | 21.2 | -79.0 | -9279 | 0.65 | 34/34 |
| COMB H | 18.3 | -69.7 | -8597 | 0.85 | 34/34 |
| COMB K | 38.5 | 36.4 | -543 | 0.78 | 34/34 |
| COMB ALL | 21.2 | -81.9 | -9395 | 0.68 | 34/34 |
| COMB F_slot48 | 4.6 | 2.6 | -341 | 0.97 | 34/34 |
| COMB F_lot_table | 31.1 | 32.5 | +349 | 0.79 | 34/34 |
| COMB G_qgate | 23.1 | -60.7 | -8643 | 0.69 | 34/34 |
| COMB H_regime | 18.3 | -69.7 | -8597 | 0.85 | 34/34 |
| COMB H_atr | -7.8 | -27.8 | -2594 | 0.93 | 34/34 |
| COMB H_atr_P7 | -7.8 | -18.0 | -1434 | 0.89 | 33/34 |
| COMB K_joint | 35.6 | 27.9 | -1764 | 0.79 | 31/34 |
| COMB F_event_dow_edge | 5.8 | -17.0 | -3228 | 0.97 | 34/34 |
| COMB G_zone_l2 | 16.2 | -10.8 | -4036 | 0.82 | 34/34 |
| COMB UP_allowed_lot_table | 1.5 | 8.3 | +1235 | 0.94 | 34/34 |
| NOCUT K | 27.6 | 20.8 | -1247 | 0.79 | 34/34 |
| NOCUT K_joint | 38.1 | 34.0 | -886 | 0.74 | 34/34 |
| NOCUT F_lot_table | 11.3 | 3.6 | -1139 | 0.84 | 34/34 |
| NOCUT H_atr | -29.7 | -60.9 | -2796 | 0.82 | 34/34 |
| NOCUT F | 12.6 | -3.1 | -2198 | 0.85 | 34/34 |
| NOCUT G | 17.6 | -46.1 | -6284 | 0.75 | 34/34 |
| NOCUT H | 15.9 | -26.6 | -4840 | 0.77 | 34/34 |
| UNIF K | 25.9 | 27.1 | +247 | 0.76 | 34/34 |
| UNIF K_joint | 34.4 | 25.1 | -1873 | 0.77 | 34/34 |
| UNIF F_lot_table | 25.9 | 29.1 | +687 | 0.80 | 34/34 |
| UNIF H_atr | 21.3 | 9.3 | -2004 | 0.76 | 34/34 |
| UNIF F | 26.8 | 27.4 | +117 | 0.81 | 34/34 |
| UNIF G | -19.7 | -113.9 | -6637 | 0.84 | 34/34 |
| UNIF H | -7.0 | -58.6 | -4900 | 0.78 | 34/34 |

### Greedy joint lot table (coordinate descent over the 15 book x session cells, daily P&L additive across disjoint trades; the picking procedure re-run each month on trailing 26 weeks)
| base | variant | WF OOS cut raw % | at equal mean % | d mean $/wk | in-sample table (book|session: lots) | in-sample cut L6M/PRE/X' % |
|--|--|--|--|--|--|--|
| COMB | down-only | 53.5 | -0.7 | -8921 | {"K7|1": 0, "K7|4": 0, "M7|1": 1, "M7|3": 0, "P7|1": 5, "P7|3": 0, "U7|1": 2} | 36/55/53 |
| COMB | up (UP, labelled) | 30.6 | 26.8 | -875 | {"A7|0": 7, "H7|0": 7, "H7|3": 6, "K7|0": 1, "K7|1": 0, "K7|3": 6, "M7|1": 1, "O7|3": 7, "P7|0": 6, "P7|1": 8, "P7|3": 0, "U7|0": 7, "U7|1": 2} | -13/36/25 |
| NOCUT | down-only | 31.1 | -69.2 | -8543 | {"H7|0": 1, "H7|3": 0, "K7|0": 1, "K7|1": 0, "M7|1": 1, "P7|0": 4, "P7|1": 1, "P7|3": 0, "U7|0": 2} | 74/62/64 |
| NOCUT | up (UP, labelled) | 9.5 | 17.0 | +1293 | {"A7|0": 8, "H7|0": 6, "H7|3": 8, "K7|0": 1, "K7|1": 5, "K7|3": 2, "K7|4": 3, "M7|1": 1, "O7|3": 8, "P7|0": 0, "P7|1": 5, "P7|3": 1, "U7|1": 5} | 47/16/16 |
| UNIF | down-only | 32.0 | -40.2 | -7760 | {"H7|0": 1, "K7|0": 1, "K7|4": 0, "M7|1": 1, "P7|0": 6, "P7|1": 6, "P7|3": 0, "U7|1": 3} | 51/40/30 |
| UNIF | up (UP, labelled) | 10.7 | 23.9 | +2621 | {"A7|0": 8, "H7|0": 2, "H7|3": 8, "K7|0": 4, "K7|1": 5, "K7|4": 6, "M7|1": 1, "M7|3": 2, "O7|3": 6, "P7|0": 6, "P7|1": 8, "P7|3": 1, "U7|0": 8, "U7|1": 1} | 34/4/-1 |

## 2. Lead 1 - P7 lot table by session (K slice): joint asia/london/nyam lots 3-7 (live 7/7/7). Top 12 of 20, drawdown-first by SEL
| technique | params | scope | cut L6M/HOLD/PRE/X' | d mean L6M/PRE | eq-mean cut L6M/PRE/X' | w20 L6M vs ref | Ulcer L6M vs ref | $/wk per $1k cut | chg share | p own / fam | NOCUT / UNIF cut L6M,PRE | live d$ | gate |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| P7_lot_table_joint | {"q_asia": 7, "q_london": 4, "q_nyam": 4} | P7 | 27/5/32/26 | +359/-428 | 28/33/27 | 1.37 | 0.76 | +17 | 0.12 | 0.01 / 1.00 | 30,26 / 29,35 | -3802 | True |
| P7_lot_table_joint | {"q_asia": 7, "q_london": 3, "q_nyam": 4} | P7 | 26/1/36/25 | -330/-765 | 25/35/24 | 1.30 | 0.75 | -16 | 0.12 | 0.08 / 1.00 | 31,29 / 30,39 | -5373 | True |
| P7_lot_table_joint | {"q_asia": 6, "q_london": 4, "q_nyam": 4} | P7 | 29/17/33/36 | -1983/-1242 | 24/27/31 | 1.24 | 0.71 | -85 | 0.22 | 0.01 / 1.00 | 39,29 / 36,32 | -15368 | True |
| P7_lot_table_joint | {"q_asia": 7, "q_london": 4, "q_nyam": 3} | P7 | 28/8/32/26 | -438/-486 | 26/31/24 | 1.34 | 0.75 | -20 | 0.13 | 0.16 / 1.00 | 33,31 / 29,38 | -7404 | True |
| P7_lot_table_joint | {"q_asia": 6, "q_london": 3, "q_nyam": 4} | P7 | 28/12/36/35 | -2615/-1580 | 20/29/28 | 1.16 | 0.71 | -117 | 0.22 | 0.04 / 1.00 | 39,33 / 37,37 | -16939 | True |
| P7_lot_table_joint | {"q_asia": 7, "q_london": 3, "q_nyam": 3} | P7 | 26/4/36/24 | -1128/-742 | 23/33/21 | 1.27 | 0.76 | -54 | 0.13 | 0.40 / 1.00 | 34,35 / 30,42 | -8974 | True |
| P7_lot_table_joint | {"q_asia": 6, "q_london": 4, "q_nyam": 3} | P7 | 30/19/33/36 | -2747/-1234 | 22/25/28 | 1.20 | 0.70 | -116 | 0.22 | 0.03 / 1.00 | 42,35 / 35,35 | -18970 | True |
| P7_lot_table_joint | {"q_asia": 5, "q_london": 3, "q_nyam": 4} | P7 | 28/14/33/33 | -2071/-1586 | 21/26/26 | 1.09 | 0.72 | -91 | 0.22 | 0.10 / 1.00 | 46,32 / 38,31 | -25196 | True |
| P7_lot_table_joint | {"q_asia": 6, "q_london": 3, "q_nyam": 3} | P7 | 28/14/36/35 | -3379/-1490 | 18/27/25 | 1.13 | 0.70 | -149 | 0.22 | 0.14 / 1.00 | 42,38 / 37,40 | -20540 | True |
| P7_lot_table_joint | {"q_asia": 5, "q_london": 3, "q_nyam": 3} | P7 | 29/16/33/33 | -2723/-2250 | 18/23/23 | 1.05 | 0.71 | -119 | 0.23 | 0.35 / 1.00 | 49,33 / 38,34 | -28797 | True |
| P7_lot_table_joint | {"q_asia": 5, "q_london": 4, "q_nyam": 4} | P7 | 30/19/30/33 | -3627/-1314 | 19/19/23 | 1.15 | 0.72 | -153 | 0.22 | 0.02 / 1.00 | 46,29 / 36,26 | -23625 | True |
| P7_lot_table_joint | {"q_asia": 4, "q_london": 4, "q_nyam": 4} | P7 | 28/30/30/39 | -3956/-1837 | 12/14/25 | 0.94 | 0.70 | -174 | 0.23 | 0.02 / 1.00 | 51,28 / 36,23 | -34489 | True |

### Session lot-table cells (one book x session at a time, down-only), top 12 of 41
| technique | params | scope | cut L6M/HOLD/PRE/X' | d mean L6M/PRE | eq-mean cut L6M/PRE/X' | w20 L6M vs ref | Ulcer L6M vs ref | $/wk per $1k cut | chg share | p own / fam | NOCUT / UNIF cut L6M,PRE | live d$ | gate |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| lot_table_cell | {"book": "P7", "live_q": 7, "q": 1, "sess": 1} | P7 | 28/-26/44/9 | +243/-165 | 29/45/10 | 1.12 | 0.78 | +11 | 0.08 | 0.03 / 1.00 | 25,28 / 29,42 | +654 | True |
| lot_table_cell | {"book": "P7", "live_q": 7, "q": 0, "sess": 1} | P7 | 28/-41/51/6 | -639/-104 | 25/49/3 | 1.03 | 0.73 | -29 | 0.08 | 1.00(degenerate) / 1.00 | 29,33 / 31,49 | -385 | True |
| lot_table_cell | {"book": "P7", "live_q": 7, "q": 0, "sess": 3} | P7 | 15/22/16/35 | +711/-1990 | 18/18/37 | 1.57 | 0.84 | +57 | 0.06 | 1.00(degenerate) / 1.00 | 35,28 / 26,29 | -15995 | True |
| lot_table_cell | {"book": "P7", "live_q": 7, "q": 1, "sess": 3} | P7 | 15/18/12/34 | +1298/-1513 | 19/16/37 | 1.49 | 0.84 | +110 | 0.05 | 0.01 / 1.00 | 30,24 / 21,23 | -11696 | True |
| lot_table_cell | {"book": "P7", "live_q": 7, "q": 2, "sess": 3} | P7 | 11/18/11/25 | +1110/-1492 | 15/15/28 | 1.43 | 0.87 | +121 | 0.05 | 0.07 / 1.00 | 26,21 / 17,21 | -11696 | True |
| lot_table_cell | {"book": "P7", "live_q": 7, "q": 2, "sess": 1} | P7 | 23/-27/40/7 | -1824/-212 | 18/36/-0 | 1.07 | 0.81 | -99 | 0.08 | 0.25 / 1.00 | 20,27 / 25,37 | +2242 | True |
| lot_table_cell | {"book": "P7", "live_q": 7, "q": 3, "sess": 1} | P7 | 19/-16/28/7 | -305/-310 | 17/27/6 | 1.01 | 0.88 | -20 | 0.08 | 0.32 / 1.00 | 14,23 / 19,27 | +824 | True |
| lot_table_cell | {"book": "P7", "live_q": 7, "q": 4, "sess": 1} | P7 | 17/-12/25/10 | -906/+28 | 14/22/6 | 1.08 | 0.88 | -69 | 0.08 | 0.07 / 1.00 | 14,20 / 17,23 | +2394 | True |
| lot_table_cell | {"book": "P7", "live_q": 7, "q": 4, "sess": 3} | P7 | 5/13/8/17 | +1088/-662 | 9/11/21 | 1.31 | 0.94 | +263 | 0.05 | 0.04 / 1.00 | 16,14 / 12,12 | -6197 | True |
| lot_table_cell | {"book": "P7", "live_q": 7, "q": 3, "sess": 3} | P7 | 5/13/7/14 | +290/-1466 | 6/9/15 | 1.28 | 0.93 | +67 | 0.05 | 0.55 / 1.00 | 19,14 / 11,15 | -9798 | True |
| lot_table_cell | {"book": "U7", "live_q": 4, "q": 0, "sess": 1} | U7 | 14/-12/13/-1 | +15/-232 | 14/13/-1 | 0.98 | 0.95 | +1 | 0.03 | 1.00(degenerate) / 1.00 | 3,17 / -1,14 | +4160 | True |
| lot_table_cell | {"book": "U7", "live_q": 4, "q": 1, "sess": 1} | U7 | 8/-6/9/7 | -159/-138 | 8/9/6 | 0.94 | 0.99 | -24 | 0.03 | 0.19 / 1.00 | 2,12 / -1,10 | +3966 | True |

### UP-allowed lot-table cells (labelled UP, never promoted), top 6
| technique | params | scope | cut L6M/HOLD/PRE/X' | d mean L6M/PRE | eq-mean cut L6M/PRE/X' | w20 L6M vs ref | Ulcer L6M vs ref | $/wk per $1k cut | chg share | p own / fam | NOCUT / UNIF cut L6M,PRE | live d$ | gate |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| lot_table_cell | {"book": "A7", "live_q": 1, "q": 7, "sess": 0} | A7 | -15/-12/15/6 | +2691/+3979 | -3/24/16 | 1.02 | 1.19 | -230 | 0.05 | 0.49 / 1.00 | -5,3 / -5,4 | -6330 | True |
| lot_table_cell | {"book": "A7", "live_q": 1, "q": 6, "sess": 0} | A7 | -12/-9/12/12 | +2117/+3153 | -3/20/20 | 1.05 | 1.16 | -213 | 0.05 | 0.38 / 1.00 | -3,2 / -3,4 | -4915 | True |
| lot_table_cell | {"book": "P7", "live_q": 7, "q": 5, "sess": 1} | P7 | 8/-3/17/10 | +50/+98 | 8/17/10 | 1.01 | 0.98 | +8 | 0.07 | 0.09 / 1.00 | 7,15 / 8,16 | +2233 | True |
| lot_table_cell | {"book": "A7", "live_q": 1, "q": 5, "sess": 0} | A7 | -9/-8/10/10 | +1794/+2653 | -1/17/17 | 1.10 | 1.14 | -248 | 0.05 | 0.48 / 1.00 | -3,2 / -3,3 | -4220 | True |
| lot_table_cell | {"book": "A7", "live_q": 1, "q": 8, "sess": 0} | A7 | -20/-16/18/-2 | +3014/+4480 | -6/27/10 | 0.96 | 1.22 | -190 | 0.05 | 0.53 / 1.00 | -5,3 / -4,5 | -7025 | False |
| lot_table_cell | {"book": "U7", "live_q": 4, "q": 8, "sess": 0} | U7 | 3/-10/-7/4 | +2530/+1312 | 13/4/13 | 1.37 | 0.99 | +937 | 0.03 | 1.00(degenerate) / 1.00 | 17,-8 / 14,-10 | +2405 | True |

## 3. Lead 2 - ATR regime (>= 1.3-1.6x the prior-20-day median of the daily median 5-min ATR): skip or halve. Picking-procedure WF FAILS (-7.8% raw, -27.8% equal mean)
| technique | params | scope | cut L6M/HOLD/PRE/X' | d mean L6M/PRE | eq-mean cut L6M/PRE/X' | w20 L6M vs ref | Ulcer L6M vs ref | $/wk per $1k cut | chg share | p own / fam | NOCUT / UNIF cut L6M,PRE | live d$ | gate |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| regime | {"cond": "atr_rel_ge1.3", "m": 0} | ALL | -2/18/53/54 | +2322/-6995 | 7/57/58 | 1.32 | 0.66 | -1477 | 0.52 | 0.05 / 1.00 | 37,-3 / 30,29 | -81695 | True |
| regime | {"cond": "atr_rel_ge1.3", "m": 0} | P7 | -1/19/40/61 | +2390/-2946 | 8/45/64 | 1.33 | 0.74 | -2958 | 0.12 | 0.08 / 1.00 | 37,5 / 32,37 | -51095 | True |
| regime | {"cond": "atr_rel_ge1.6", "m": 0} | P7 | 22/27/36/49 | +524/-2592 | 23/37/50 | 1.40 | 0.75 | +30 | 0.09 | 0.01 / 1.00 | 26,38 / 12,49 | -39590 | True |
| regime | {"cond": "atr_rel_ge1.3", "m": 0.5} | ALL | 6/24/21/56 | +1681/-1475 | 12/26/59 | 1.27 | 0.78 | +370 | 0.16 | 0.01 / 1.00 | 19,15 / 23,22 | -27584 | True |
| regime | {"cond": "atr_rel_ge1.6", "m": 0} | ALL | 6/25/41/62 | -2553/-5363 | -3/35/58 | 1.09 | 0.91 | -526 | 0.40 | 0.05 / 1.00 | 17,47 / 9,55 | -61700 | True |
| regime | {"cond": "atr_rel_ge1.6", "m": 0.5} | ALL | 12/19/25/51 | -238/-1152 | 11/24/51 | 1.27 | 0.85 | -25 | 0.11 | 0.01 / 1.00 | 10,25 / 6,32 | -22102 | True |
| regime | {"cond": "atr_rel_ge1.3", "m": 0.5} | P7 | 2/21/17/49 | +1927/-998 | 9/23/52 | 1.28 | 0.87 | +1240 | 0.11 | 0.01 / 1.00 | 20,7 / 22,16 | -22162 | True |
| regime | {"cond": "atr_rel_ge1.6", "m": 0.5} | P7 | 12/22/19/39 | +980/-824 | 15/22/41 | 1.36 | 0.86 | +104 | 0.08 | 0.01 / 0.52 | 13,23 / 8,23 | -17009 | True |
| regime | {"cond": "atr_rel_ge1.3", "m": 0} | M7 | -1/13/8/13 | +1090/+32 | 4/13/17 | 1.22 | 1.01 | -1770 | 0.12 | 0.02 / 1.00 | -4,17 / 5,18 | -8350 | True |
| regime | {"cond": "atr_rel_ge1.3", "m": 0} | K7 | 3/-9/4/6 | +171/-1691 | 3/5/7 | 1.09 | 0.94 | +81 | 0.20 | 0.13 / 1.00 | 5,-3 / 13,4 | -16475 | True |

## 4F. F Time / session excluding lot tables (584 down-only cells, 197 gate, 54 gate + control-bases ok)
| technique | params | scope | cut L6M/HOLD/PRE/X' | d mean L6M/PRE | eq-mean cut L6M/PRE/X' | w20 L6M vs ref | Ulcer L6M vs ref | $/wk per $1k cut | chg share | p own / fam | NOCUT / UNIF cut L6M,PRE | live d$ | gate |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| dow | {"dow": 2, "m": 0} | ALL | 51/27/4/35 | +1171/-2509 | 54/8/39 | 0.88 | 0.56 | +29 | 0.20 | 0.01 / 1.00 | 55,31 / 39,24 | -28160 | True |
| dow | {"dow": 0, "m": 0} | ALL | 24/-119/22/52 | -1865/-2093 | 18/15/48 | 0.58 | 0.73 | -96 | 0.19 | 0.08 / 1.00 | 1,23 / 16,16 | -28440 | True |
| dow | {"dow": 2, "m": 0} | P7 | 32/12/11/32 | +427/-1255 | 33/12/34 | 0.99 | 0.69 | +17 | 0.05 | 0.02 / 1.00 | 41,26 / 26,16 | -9060 | True |
| dow | {"dow": 0, "m": 0} | P7 | 1/-43/13/51 | -798/-562 | -2/10/50 | 0.93 | 0.93 | -733 | 0.05 | 0.08 / 1.00 | 9,11 / 25,6 | -24760 | True |
| slot48 | {"m": 0, "slot": 20} | ALL | 4/11/3/35 | +503/-800 | 6/5/36 | 1.26 | 0.96 | +158 | 0.09 | 0.18 / 1.00 | 18,-0 / 16,16 | +5745 | True |
| dow | {"dow": 2, "m": 0.5} | P7 | 14/6/6/19 | +578/-475 | 16/8/21 | 1.07 | 0.89 | +50 | 0.04 | 0.02 / 1.00 | 17,12 / 14,7 | -3410 | True |
| slot48 | {"m": 0, "slot": 20} | P7 | 7/13/4/32 | +298/-96 | 8/5/33 | 1.20 | 0.96 | +55 | 0.02 | 0.20 / 1.00 | 20,7 / 17,15 | +5610 | True |
| dow | {"dow": 2, "m": 0.5} | ALL | 15/11/6/23 | -50/-895 | 15/6/23 | 0.99 | 0.88 | -4 | 0.07 | 0.05 / 1.00 | 21,10 / 15,5 | -6193 | True |
| slot48 | {"m": 0, "slot": 22} | P7 | 7/-2/5/13 | +1559/-838 | 12/11/18 | 1.21 | 0.96 | +281 | 0.01 | 0.09 / 1.00 | 11,7 / 7,3 | -6000 | True |
| slot48 | {"m": 0, "slot": 15} | ALL | 2/-21/9/2 | +2463/+189 | 11/17/11 | 1.11 | 1.09 | +1483 | 0.02 | 0.07 / 1.00 | -15,12 / -0,12 | +5425 | True |

## 4G. G Signal quality excluding lot tables (3548 down-only cells, 966 gate, 401 gate + control-bases ok)
| technique | params | scope | cut L6M/HOLD/PRE/X' | d mean L6M/PRE | eq-mean cut L6M/PRE/X' | w20 L6M vs ref | Ulcer L6M vs ref | $/wk per $1k cut | chg share | p own / fam | NOCUT / UNIF cut L6M,PRE | live d$ | gate |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| qgate | {"feat": "dB", "m": 0, "q": 0.2, "tail": "high"} | P7 | 28/39/33/0 | +3484/-4163 | 37/42/13 | 1.17 | 0.61 | +158 | 0.06 | 0.05 / 1.00 | 48,6 / 37,29 | -55565 | True |
| qgate | {"feat": "dA", "m": 0, "q": 0.1, "tail": "high"} | ALL | 10/-0/33/0 | +3427/-1359 | 22/42/13 | 1.24 | 0.89 | +417 | 0.09 | 0.02 / 1.00 | 19,17 / 12,28 | +710 | True |
| qgate | {"feat": "dA", "m": 0, "q": 0.3, "tail": "high"} | ALL | 15/1/21/0 | +3995/-2321 | 28/33/15 | 1.25 | 0.67 | +327 | 0.24 | 0.11 / 1.00 | 26,19 / 20,43 | -28410 | True |
| qgate | {"feat": "dA", "m": 0, "q": 0.3, "tail": "high"} | P7 | -2/10/32/0 | +3723/-1185 | 13/42/14 | 1.37 | 0.91 | -2690 | 0.06 | 0.09 / 1.00 | 36,17 / 22,35 | -12670 | True |
| qgate_x_er | {"er": "erhigh", "feat": "f_sweep2_w30", "m": 0, "q": 0.2, "tail": "high"} | ALL | 18/10/22/0 | +2811/-2709 | 27/31/11 | 1.34 | 0.64 | +195 | 0.10 | 0.09 / 1.00 | 53,24 / 44,35 | +0 | True |
| qgate_x_er | {"er": "erhigh", "feat": "dA", "m": 0, "q": 0.2, "tail": "high"} | ALL | 5/-2/35/0 | +2943/-1810 | 15/42/11 | 1.05 | 1.00 | +757 | 0.07 | 0.05 / 1.00 | -12,20 / -0,40 | +10570 | True |
| qgate | {"feat": "dB", "m": 0.5, "q": 0.2, "tail": "high"} | P7 | 14/21/32/0 | +2027/-1686 | 21/38/8 | 1.18 | 0.81 | +178 | 0.06 | 0.03 / 1.00 | 25,7 / 27,32 | -24625 | True |
| qgate | {"feat": "dA", "m": 0, "q": 0.5, "tail": "high"} | P7 | 14/8/15/0 | +3416/-303 | 26/26/14 | 1.26 | 0.84 | +306 | 0.09 | 0.16 / 1.00 | 45,16 / 28,35 | -12950 | True |
| qgate_x_er | {"er": "erhigh", "feat": "dip30", "m": 0, "q": 0.5, "tail": "high"} | ALL | 31/-1/50/0 | -1845/-4440 | 26/46/-7 | 1.26 | 0.48 | -74 | 0.20 | 0.04 / 1.00 | 58,51 / 52,58 | -52620 | False |
| qgate | {"feat": "dB", "m": 0, "q": 0.1, "tail": "high"} | P7 | -6/8/35/0 | +3318/-2603 | 7/43/12 | 1.14 | 0.93 | -691 | 0.03 | 0.11 / 1.00 | 1,6 / -9,25 | -37575 | True |

## 4H. H Regime excluding lot tables (854 down-only cells, 284 gate, 119 gate + control-bases ok)
| technique | params | scope | cut L6M/HOLD/PRE/X' | d mean L6M/PRE | eq-mean cut L6M/PRE/X' | w20 L6M vs ref | Ulcer L6M vs ref | $/wk per $1k cut | chg share | p own / fam | NOCUT / UNIF cut L6M,PRE | live d$ | gate |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| regime | {"cond": "atr_rel_ge1.3", "m": 0} | ALL | -2/18/53/54 | +2322/-6995 | 7/57/58 | 1.32 | 0.66 | -1477 | 0.52 | 0.05 / 1.00 | 37,-3 / 30,29 | -81695 | True |
| regime | {"cond": "atr_rel_ge1.3", "m": 0} | P7 | -1/19/40/61 | +2390/-2946 | 8/45/64 | 1.33 | 0.74 | -2958 | 0.12 | 0.08 / 1.00 | 37,5 / 32,37 | -51095 | True |
| regime | {"cond": "atr_rel_ge1.6", "m": 0} | P7 | 22/27/36/49 | +524/-2592 | 23/37/50 | 1.40 | 0.75 | +30 | 0.09 | 0.01 / 1.00 | 26,38 / 12,49 | -39590 | True |
| regime | {"cond": "adx5_ge20", "m": 0} | P7 | 36/7/57/45 | -3607/-5926 | 23/48/34 | 1.22 | 0.42 | -125 | 0.19 | 0.10 / 1.00 | 79,40 / 67,59 | -68150 | True |
| regime | {"cond": "adx5_ge20", "m": 0.5} | P7 | 40/21/26/38 | -522/-2149 | 38/24/36 | 1.30 | 0.65 | -17 | 0.18 | 0.01 / 1.00 | 56,25 / 48,27 | -29763 | True |
| regime | {"cond": "adx5_ge20", "m": 0.5} | ALL | 41/20/38/43 | -2574/-3575 | 33/29/35 | 1.09 | 0.57 | -78 | 0.30 | 0.02 / 1.00 | 59,27 / 61,39 | -33303 | True |
| regime | {"cond": "atr_rel_ge1.3", "m": 0.5} | ALL | 6/24/21/56 | +1681/-1475 | 12/26/59 | 1.27 | 0.78 | +370 | 0.16 | 0.01 / 1.00 | 19,15 / 23,22 | -27584 | True |
| regime | {"cond": "on_ratio_ge0.6", "m": 0} | P7 | 32/18/48/37 | -2159/-616 | 24/42/30 | 0.96 | 0.63 | -84 | 0.11 | 0.33 / 1.00 | 69,56 / 41,46 | -41335 | True |
| regime | {"cond": "prior_trend_day", "m": 0} | ALL | 6/-38/41/58 | -1383/-127 | -1/36/55 | 0.80 | 0.90 | -296 | 0.33 | 0.03 / 1.00 | 30,42 / 52,48 | -16660 | True |
| regime | {"cond": "atr_rel_ge1.6", "m": 0} | ALL | 6/25/41/62 | -2553/-5363 | -3/35/58 | 1.09 | 0.91 | -526 | 0.40 | 0.05 / 1.00 | 17,47 / 9,55 | -61700 | True |

## 4K. K P7 excluding lot tables (0 down-only cells, 0 gate, 0 gate + control-bases ok)
none

## 5. Calmar frontier vs Q1-A (down-only, first-order; mean is the weak side)
Cells that dominate Q1-A on BOTH L6M mean and maxDD (d mean L6M > 0, cut L6M > 0, cut PRE > 0, cut X' > -3): 464 (of 5047 down-only). Top 10 by SEL:
| technique | params | scope | cut L6M/HOLD/PRE/X' | d mean L6M/PRE | eq-mean cut L6M/PRE/X' | w20 L6M vs ref | Ulcer L6M vs ref | $/wk per $1k cut | chg share | p own / fam | NOCUT / UNIF cut L6M,PRE | live d$ | gate |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| regime | {"cond": "atr_rel_ge1.6", "m": 0} | P7 | 22/27/36/49 | +524/-2592 | 23/37/50 | 1.40 | 0.75 | +30 | 0.09 | 0.01 / 1.00 | 26,38 / 12,49 | -39590 | True |
| dow | {"dow": 2, "m": 0} | ALL | 51/27/4/35 | +1171/-2509 | 54/8/39 | 0.88 | 0.56 | +29 | 0.20 | 0.01 / 1.00 | 55,31 / 39,24 | -28160 | True |
| regime | {"cond": "atr_rel_ge1.3", "m": 0.5} | ALL | 6/24/21/56 | +1681/-1475 | 12/26/59 | 1.27 | 0.78 | +370 | 0.16 | 0.01 / 1.00 | 19,15 / 23,22 | -27584 | True |
| qgate | {"feat": "dB", "m": 0, "q": 0.2, "tail": "high"} | P7 | 28/39/33/0 | +3484/-4163 | 37/42/13 | 1.17 | 0.61 | +158 | 0.06 | 0.05 / 1.00 | 48,6 / 37,29 | -55565 | True |
| P7_lot_table_joint | {"q_asia": 7, "q_london": 4, "q_nyam": 4} | P7 | 27/5/32/26 | +359/-428 | 28/33/27 | 1.37 | 0.76 | +17 | 0.12 | 0.01 / 1.00 | 30,26 / 29,35 | -3802 | True |
| regime | {"cond": "atr_rel_ge1.3", "m": 0.5} | P7 | 2/21/17/49 | +1927/-998 | 9/23/52 | 1.28 | 0.87 | +1240 | 0.11 | 0.01 / 1.00 | 20,7 / 22,16 | -22162 | True |
| lot_table_cell | {"book": "P7", "live_q": 7, "q": 1, "sess": 1} | P7 | 28/-26/44/9 | +243/-165 | 29/45/10 | 1.12 | 0.78 | +11 | 0.08 | 0.03 / 1.00 | 25,28 / 29,42 | +654 | True |
| dow | {"dow": 2, "m": 0} | P7 | 32/12/11/32 | +427/-1255 | 33/12/34 | 0.99 | 0.69 | +17 | 0.05 | 0.02 / 1.00 | 41,26 / 26,16 | -9060 | True |
| regime | {"cond": "atr_rel_ge1.6", "m": 0.5} | P7 | 12/22/19/39 | +980/-824 | 15/22/41 | 1.36 | 0.86 | +104 | 0.08 | 0.01 / 0.52 | 13,23 / 8,23 | -17009 | True |
| qgate | {"feat": "dA", "m": 0, "q": 0.1, "tail": "high"} | ALL | 10/-0/33/0 | +3427/-1359 | 22/42/13 | 1.24 | 0.89 | +417 | 0.09 | 0.02 / 1.00 | 19,17 / 12,28 | +710 | True |

Cells that cut drawdown by giving up mean (gate on, d mean <= 0): 315; cheapest rate ($ weekly mean per $1k L6M maxDD removed), top 8:
| technique | params | scope | cut L6M/HOLD/PRE/X' | d mean L6M/PRE | eq-mean cut L6M/PRE/X' | w20 L6M vs ref | Ulcer L6M vs ref | $/wk per $1k cut | chg share | p own / fam | NOCUT / UNIF cut L6M,PRE | live d$ | gate |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| regime | {"cond": "RTY_leads_against_60", "m": 0} | K7 | 0/-2/5/5 | -1124/-1586 | -5/0/0 | 0.89 | 0.95 | -12943 | 0.17 | 0.49 / 1.00 | 23,-3 / 13,1 | +0 | True |
| regime | {"cond": "RTY_disagree_60", "m": 0} | P7 | 0/13/19/33 | -971/-733 | -5/15/30 | 1.04 | 1.05 | -11180 | 0.05 | 0.18 / 1.00 | 9,13 / 17,13 | +0 | True |
| regime | {"cond": "RTY_leads_against_15", "m": 0.5} | P7 | 0/12/11/11 | -960/-944 | -4/8/7 | 1.03 | 0.93 | -11062 | 0.09 | 0.48 / 1.00 | 29,14 / 30,8 | +0 | True |
| regime | {"cond": "RTY_lags_60", "m": 0} | M7 | 0/4/3/3 | -638/-421 | -2/0/1 | 1.04 | 1.05 | -10209 | 0.06 | 0.50 / 1.00 | 4,12 / 3,8 | +0 | True |
| regime | {"cond": "RTY_lags_15", "m": 0} | M7 | 0/-1/11/8 | -597/+73 | -2/9/6 | 1.06 | 1.02 | -6881 | 0.06 | 0.13 / 1.00 | 1,16 / 3,16 | +0 | True |
| regime | {"cond": "RTY_leads_against_60", "m": 0.5} | K7 | 0/-3/2/13 | -421/-300 | -2/1/11 | 0.97 | 1.04 | -4847 | 0.03 | 0.04 / 1.00 | 6,-1 / 5,-0 | +0 | True |
| slot48 | {"m": 0.5, "slot": 6} | P7 | 0/2/3/7 | -417/+21 | -2/1/5 | 1.00 | 1.06 | -3694 | 0.01 | 0.47 / 1.00 | -4,4 / -1,4 | +1025 | True |
| regime | {"cond": "RTY_disagree_60", "m": 0.5} | P7 | 0/12/10/16 | -236/-394 | -1/9/15 | 1.09 | 1.05 | -2720 | 0.04 | 0.18 / 1.00 | 5,7 / 8,7 | +0 | True |

## 6. Per-book breakdown: best gated down-only cell acting on one book only (scope = book; stack effect), by SEL

**K7** (220 gated cells)
| technique | params | scope | cut L6M/HOLD/PRE/X' | d mean L6M/PRE | eq-mean cut L6M/PRE/X' | w20 L6M vs ref | Ulcer L6M vs ref | $/wk per $1k cut | chg share | p own / fam | NOCUT / UNIF cut L6M,PRE | live d$ | gate |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| regime | {"cond": "prior_trend_day", "m": 0} | K7 | 5/13/7/21 | +211/-981 | 6/8/22 | 1.06 | 1.04 | +52 | 0.11 | 0.03 / 1.00 | 0,3 / 4,2 | +5090 | True |
| dow | {"dow": 2, "m": 0} | K7 | 3/5/4/7 | +939/-326 | 7/8/10 | 1.10 | 1.00 | +398 | 0.07 | 0.06 / 1.00 | 7,2 / 8,2 | -7620 | True |
| regime | {"cond": "prior_dir_with", "m": 0} | K7 | 3/-5/7/22 | -664/-1165 | -0/5/20 | 0.88 | 1.03 | -333 | 0.17 | 0.11 / 1.00 | 12,4 / 6,4 | -5885 | True |

**P7** (224 gated cells)
| technique | params | scope | cut L6M/HOLD/PRE/X' | d mean L6M/PRE | eq-mean cut L6M/PRE/X' | w20 L6M vs ref | Ulcer L6M vs ref | $/wk per $1k cut | chg share | p own / fam | NOCUT / UNIF cut L6M,PRE | live d$ | gate |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| regime | {"cond": "atr_rel_ge1.3", "m": 0} | P7 | -1/19/40/61 | +2390/-2946 | 8/45/64 | 1.33 | 0.74 | -2958 | 0.12 | 0.08 / 1.00 | 37,5 / 32,37 | -51095 | True |
| regime | {"cond": "atr_rel_ge1.6", "m": 0} | P7 | 22/27/36/49 | +524/-2592 | 23/37/50 | 1.40 | 0.75 | +30 | 0.09 | 0.01 / 1.00 | 26,38 / 12,49 | -39590 | True |
| regime | {"cond": "adx5_ge20", "m": 0} | P7 | 36/7/57/45 | -3607/-5926 | 23/48/34 | 1.22 | 0.42 | -125 | 0.19 | 0.10 / 1.00 | 79,40 / 67,59 | -68150 | True |

**M7** (401 gated cells)
| technique | params | scope | cut L6M/HOLD/PRE/X' | d mean L6M/PRE | eq-mean cut L6M/PRE/X' | w20 L6M vs ref | Ulcer L6M vs ref | $/wk per $1k cut | chg share | p own / fam | NOCUT / UNIF cut L6M,PRE | live d$ | gate |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| qgate | {"feat": "dip15", "m": 0, "q": 0.5, "tail": "high"} | M7 | 17/10/16/0 | +1759/-203 | 22/21/6 | 1.31 | 0.87 | +129 | 0.09 | 0.01 / 1.00 | 4,10 / 13,12 | +390 | True |
| l2_confirm_count_PROXY | {"k": 2, "m": 0} | M7 | 15/5/20/-3 | +842/-382 | 18/22/0 | 1.30 | 0.91 | +70 | 0.09 | 0.01 / 1.00 | 11,23 / 14,20 | +0 | True |
| regime | {"cond": "atr_rel_ge1.3", "m": 0} | M7 | -1/13/8/13 | +1090/+32 | 4/13/17 | 1.22 | 1.01 | -1770 | 0.12 | 0.02 / 1.00 | -4,17 / 5,18 | -8350 | True |

**U7** (159 gated cells)
| technique | params | scope | cut L6M/HOLD/PRE/X' | d mean L6M/PRE | eq-mean cut L6M/PRE/X' | w20 L6M vs ref | Ulcer L6M vs ref | $/wk per $1k cut | chg share | p own / fam | NOCUT / UNIF cut L6M,PRE | live d$ | gate |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| qgate | {"feat": "f_er20_5m", "m": 0, "q": 0.5, "tail": "low"} | U7 | 17/-5/3/0 | +924/-171 | 20/7/4 | 1.21 | 0.90 | +70 | 0.03 | 0.03 / 1.00 | 16,5 / 10,3 | +0 | True |
| regime | {"cond": "adx5_le20", "m": 0} | U7 | 11/11/10/3 | +499/+319 | 13/12/5 | 1.02 | 0.97 | +58 | 0.02 | 0.03 / 1.00 | 0,-4 / -1,10 | +3890 | True |
| regime | {"cond": "RTY_lags_15", "m": 0} | U7 | 0/5/2/26 | -76/-177 | -0/1/26 | 1.01 | 1.06 | -879 | 0.01 | 0.01 / 1.00 | 8,5 / 7,8 | +0 | True |

**A7** (57 gated cells)
| technique | params | scope | cut L6M/HOLD/PRE/X' | d mean L6M/PRE | eq-mean cut L6M/PRE/X' | w20 L6M vs ref | Ulcer L6M vs ref | $/wk per $1k cut | chg share | p own / fam | NOCUT / UNIF cut L6M,PRE | live d$ | gate |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| regime | {"cond": "prior_dir_with", "m": 0} | A7 | 5/0/1/1 | +559/-259 | 7/3/3 | 1.02 | 1.02 | +139 | 0.03 | 0.02 / 1.00 | 4,2 / 3,3 | +2425 | True |
| dow | {"dow": 2, "m": 0} | A7 | 2/1/1/-1 | +570/-70 | 5/3/2 | 1.06 | 1.04 | +339 | 0.01 | 0.02 / 1.00 | 2,3 / 3,3 | +1360 | True |
| regime | {"cond": "atr_rel_ge1.6", "m": 0} | A7 | -2/-1/0/2 | +499/-104 | 1/3/4 | 1.00 | 1.04 | -416 | 0.01 | 0.11 / 1.00 | -1,1 / -1,1 | +795 | True |

**H7** (114 gated cells)
| technique | params | scope | cut L6M/HOLD/PRE/X' | d mean L6M/PRE | eq-mean cut L6M/PRE/X' | w20 L6M vs ref | Ulcer L6M vs ref | $/wk per $1k cut | chg share | p own / fam | NOCUT / UNIF cut L6M,PRE | live d$ | gate |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| regime | {"cond": "prior_close_low", "m": 0} | H7 | 3/0/-1/13 | -130/-317 | 2/-1/13 | 0.95 | 1.05 | -56 | 0.01 | 0.01 / 1.00 | -1,-1 / -1,-1 | +0 | True |
| regime | {"cond": "adx5_ge40", "m": 0} | H7 | 0/1/-1/8 | +102/-180 | 0/-0/9 | 0.96 | 1.07 | n/a | 0.00 | 0.07 / 1.00 | -1,-1 / 2,-1 | +0 | True |
| regime | {"cond": "RTY_disagree_60", "m": 0} | H7 | 0/2/1/0 | +493/-496 | 2/3/3 | 1.07 | 1.05 | +5678 | 0.01 | 0.04 / 1.00 | 3,1 / 3,1 | +0 | True |

**O7** (89 gated cells)
| technique | params | scope | cut L6M/HOLD/PRE/X' | d mean L6M/PRE | eq-mean cut L6M/PRE/X' | w20 L6M vs ref | Ulcer L6M vs ref | $/wk per $1k cut | chg share | p own / fam | NOCUT / UNIF cut L6M,PRE | live d$ | gate |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| regime | {"cond": "RTY_disagree_60", "m": 0} | O7 | 0/-2/1/6 | +278/-364 | 1/2/7 | 1.03 | 1.07 | n/a | 0.01 | 0.02 / 1.00 | 0,1 / 1,1 | +0 | True |
| regime | {"cond": "adx5_ge35", "m": 0} | O7 | 0/0/1/2 | +161/-218 | 1/2/3 | 1.00 | 1.07 | n/a | 0.01 | 0.09 / 1.00 | -0,2 / 0,2 | +695 | True |
| qgate | {"feat": "twap_slope_sg", "m": 0, "q": 0.3, "tail": "low"} | O7 | 0/-1/1/0 | +365/-6 | 2/2/2 | 1.01 | 1.08 | n/a | 0.00 | 0.03 / 1.00 | 1,1 / 2,1 | +0 | True |

## 7. Finalists (<= 12): down-only, tolerant gate, w20 not worse, NOCUT and UNIF controls cut > 0 on L6M and PRE, p own <= .10; one per technique x scope, ranked by SEL. NONE has p fam <= .10; none is a CANDIDATE; EXACT engine re-run pending (needs the lots-override hook).
| technique | params | scope | cut L6M/HOLD/PRE/X' | d mean L6M/PRE | eq-mean cut L6M/PRE/X' | w20 L6M vs ref | Ulcer L6M vs ref | $/wk per $1k cut | chg share | p own / fam | NOCUT / UNIF cut L6M,PRE | live d$ | gate |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| dow | {"dow": 2, "m": 0} | ALL | 51/27/4/35 | +1171/-2509 | 54/8/39 | 0.88 | 0.56 | +29 | 0.20 | 0.01 / 1.00 | 55,31 / 39,24 | -28160 | True |
| regime | {"cond": "prior_trend_day", "m": 0} | ALL | 6/-38/41/58 | -1383/-127 | -1/36/55 | 0.80 | 0.90 | -296 | 0.33 | 0.03 / 1.00 | 30,42 / 52,48 | -16660 | True |
| dow | {"dow": 2, "m": 0} | P7 | 32/12/11/32 | +427/-1255 | 33/12/34 | 0.99 | 0.69 | +17 | 0.05 | 0.02 / 1.00 | 41,26 / 26,16 | -9060 | True |
| P7_lot_table_joint | {"q_asia": 4, "q_london": 4, "q_nyam": 4} | P7 | 28/30/30/39 | -3956/-1837 | 12/14/25 | 0.94 | 0.70 | -174 | 0.23 | 0.02 / 1.00 | 51,28 / 36,23 | -34489 | True |
| l2_confirm_count_PROXY | {"k": 2, "m": 0.5} | ALL | 28/30/19/27 | -3264/-2378 | 15/6/14 | 0.87 | 0.75 | -147 | 0.19 | 0.10 / 1.00 | 25,28 / 6,34 | +0 | True |
| zone_near_behind | {"dist": 30, "m": 0.5} | P7 | 1/2/0/18 | +52/-772 | 1/0/19 | 0.96 | 1.07 | +68 | 0.03 | 0.09 / 1.00 | 6,1 / 0,1 | +0 | True |
| qgate | {"feat": "twap_slope_sg", "m": 0.5, "q": 0.5, "tail": "low"} | U7 | 4/-1/5/0 | -58/-43 | 4/5/-0 | 0.99 | 1.03 | -17 | 0.02 | 0.10 / 1.00 | 2,6 / 0,5 | +2678 | True |

Finalist live definitions (all multiplicative on live lots, round, min 1): see params; P7 table cells = SessionLots P7 asia,london,nyam; regime/slot/gate cells = multiplier x0 / x0.5 on the stated trades.

sz_core placebo (same lot-change values on random trades, same book x session; p of the cut): dow {"dow": 2, "m": 0} ALL: L6M 0.01 PRE 0.74; regime {"cond": "prior_trend_day", "m": 0} ALL: L6M 0.50 PRE 0.19; dow {"dow": 2, "m": 0} P7: L6M 0.04 PRE 0.55; P7_lot_table_joint {"q_asia": 4, "q_london": 4, "q_nyam": 4} P7: L6M 0.18 PRE 0.37; l2_confirm_count_PROXY {"k": 2, "m": 0.5} ALL: L6M 0.07 PRE 0.37; zone_near_behind {"dist": 30, "m": 0.5} P7: L6M 0.35 PRE 0.70; qgate {"feat": "twap_slope_sg", "m": 0.5, "q": 0.5, "tail": "low"} U7: L6M 0.22 PRE 0.31

## 8. Scorer difference (fgh complete-weeks scorer vs sz_core): maxDD cut on L6M, PRE, X' identical to 0.1 point for the top-20 cells; the equal-mean columns differ because L6M means differ (carry-week and window edge). Gate counts COMB: sz_core 1557, fgh scorer 1373.
