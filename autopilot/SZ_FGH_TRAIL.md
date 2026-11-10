# SZ_FGH_TRAIL - T-TRAIL-L2: profit-state screens for U7 and H7 (all sessions), 2026-11-10 20:25Z

> Label: FIRST-ORDER SCREEN (REDO-R5 PTR engine, 1-s top-10 state paths of the LPB_BASE trade list, decision at the close of second s, market exit at the next row, slip 1.2 central / 0.57 low / 1.6 high) unless a row says EXACT. Base = live panel (LPB_BASE: P7 cap 8,400, 7/4/4, P7 cut 40/5x/w5/p3, all layers ON); the live profit branch stays ON and the rule acts on top. ROLLFIX1. PRE-PROOF, post-hoc, Shadow only, no PASS claims. Grid and promotion by SZ-IJK (ptr_screen.py stage 1 / ptr_stage2.py, about 18.6k cells per book, dead_lookup 0 hits, cells appended to DEAD_CELLS as program PTRL2); top-20 per book by recents key (mean equal-mean cut L6M/L3M/L1M), files /mnt/l2/l2vast/_th_ptr/top20_U7.txt / top20_H7.txt, tables table_U7.csv / table_H7.csv. Placebo = random exit at the same arm pct and same count (B=100); own-draw p shown; **family p here is over the 20 reported lines only, not the whole ~18.6k grid, so it UNDERSTATES the multiplicity (read it as an upper bound on the strength; the whole-grid family p would be larger)**. WF = bi-weekly re-pick of the single cell vs the live panel base (% of periods the cell beats live; 60% is the bar). Rule 2a label at the 25% PRE-mean floor. The live-week replay (clipped targets / caught give-backs) needs the frozen-week state features and is delivered by REDO-R13; pending.

## U7 (all sessions)
Top 20 first-order lines (recents-key order from ptr_top20; windows = stack maxDD cut % vs the live panel, + shallower):

| # | line (grammar) | fires | cut L6M / L3M / L1M / HOLD / PRE / X' | d mean L6M / PRE $/wk | worst-20 cut L6M | slip low / high L6M cut | own p / family p (top-20) | WF % beat | rule 2a |
|--|--|--|--|--|--|--|--|--|--|
| 1 | * pct>=0.3 pulled_against_mult>=20 ahead_rel_slow>=1.2 take win=5 persist=3 | 252 | 26.8 / 26.8 / 25.2 / -0.2 / 3.7 / -10.3 | +1087 / -260 | +34 | 27.2 / 26.6 | 0.27 / 0.99 | 14 | OK-PRIOR |
| 2 | * pct>=0.3 pulled_against_mult>=20 tighten 20 win=5 persist=5 | 285 | 26.2 / 26.2 / 28.1 / -12.4 / -0.4 / -1.5 | +723 / -601 | +28 | 26.6 / 25.9 | 0.54 / 1.00 | 10 | OK-PRIOR |
| 3 | * pct>=0.3 pulled_against_mult>=20 step 5 win=5 persist=5 | 354 | 29.1 / 29.1 / 28.7 / -9.6 / -1.0 / -0.1 | +46 / -461 | +20 | 29.7 / 28.7 | 0.67 / 1.00 | 9 | OK-PRIOR |
| 4 | * pct>=0.3 pulled_against_mult>=20 take win=5 persist=5 | 375 | 29.4 / 29.4 / 27.2 / -9.9 / -0.6 / -0.4 | +40 / -455 | +24 | 30.0 / 29.0 | 0.62 / 1.00 | 10 | OK-PRIOR |
| 5 | * pct>=0.3 pulled_against_mult>=20 tighten 8 win=5 persist=5 | 353 | 29.4 / 29.4 / 26.9 / -9.5 / -1.1 / -0.2 | +51 / -484 | +20 | 30.0 / 29.1 | 0.52 / 1.00 | 9 | OK-PRIOR |
| 6 | * pct>=0.3 delta_mult>=30 step 5 win=15 persist=1 | 369 | 25.0 / 25.0 / 16.3 / -8.8 / 1.7 / 1.2 | +1694 / -17 | +43 | 25.3 / 24.8 | 0.53 / 1.00 | 22 | OK-PRIOR |
| 7 | * pct>=0.4 delta_mult>=20 step 5 win=15 persist=5 | 399 | 27.7 / 27.7 / 10.5 / -6.9 / 4.9 / 5.7 | +1608 / -564 | +48 | 28.2 / 27.4 | 0.32 / 1.00 | 25 | OK-PRIOR |
| 8 | * pct>=0.3 delta_mult>=30 take win=15 persist=1 | 376 | 23.2 / 23.2 / 16.7 / -8.6 / 1.3 / 2.5 | +1663 / -2 | +41 | 23.6 / 23.0 | 0.54 / 1.00 | 22 | OK-PRIOR |
| 9 | * pct>=0.3 delta_mult>=30 tighten 8 win=15 persist=1 | 369 | 25.0 / 25.0 / 15.8 / -8.5 / 1.5 / 1.4 | +1653 / -14 | +42 | 25.3 / 24.8 | 0.55 / 1.00 | 22 | OK-PRIOR |
| 10 | * pct>=0.2 pulled_against_mult>=30 imb5<=-0.3 take win=8 persist=1 | 425 | 25.6 / 25.6 / 25.3 / -4.9 / 0.8 / -3.1 | +326 / -202 | +27 | 26.5 / 25.1 | 0.56 / 1.00 | 16 | OK-PRIOR |
| 11 | * pct>=0.3 pulled_against_mult>=20 ahead_rel>=1.2 take win=5 persist=3 | 251 | 24.7 / 24.7 / 24.3 / -1.7 / 3.7 / -6.9 | +341 / -253 | +15 | 25.1 / 24.4 | 0.30 / 1.00 | 13 | OK-PRIOR |
| 12 | * pct>=0.2 pulled_mult>=5 secs_fav<=0 take win=5 persist=3 | 427 | 28.9 / 28.9 / 26.4 / -3.9 / 9.4 / 9.0 | -999 / -555 | +18 | 30.0 / 28.3 | 0.11 / 0.87 | 18 | OK-PRIOR |
| 13 | * pct>=0.2 pulled_against_mult>=30 imb5<=-0.3 tighten 16 win=8 persist=1 | 370 | 25.1 / 25.1 / 19.1 / -6.0 / 1.1 / -3.0 | +364 / -139 | +25 | 25.7 / 24.6 | 0.52 / 1.00 | 18 | OK-PRIOR |
| 14 | * pct>=0.4 tot_rel_slow>=1.5 tighten 20 persist=2 | 549 | 22.5 / 22.5 / 17.0 / 3.2 / 6.9 / 1.4 | +426 / -774 | +3 | 23.2 / 22.1 | 0.29 / 0.99 | 34 | OK-PRIOR |
| 15 | * pct>=0.2 wall_ahead_mult>=10 lock 10 persist=2 wall_ticks=2 | 289 | 17.8 / 17.8 / 5.4 / -10.4 / -2.5 / -17.3 | +946 / -550 | +7 | 17.9 / 17.7 | 0.75 / 1.00 | 8 | OK-PRIOR |
| 16 | * pct>=0.2 wall_ahead_mult>=10 lock 0 persist=2 wall_ticks=2 | 244 | 14.7 / 14.7 / 4.5 / -12.8 / -2.2 / -25.0 | +1327 / -545 | +14 | 14.8 / 14.6 | 0.66 / 1.00 | 11 | OK-PRIOR |
| 17 | * pct>=0.2 dd>=20 lock 10 persist=10 | 423 | 17.1 / 17.1 / 6.2 / -4.0 / 15.7 / -7.4 | +824 / -660 | +9 | 17.6 / 16.8 | 0.04 / 0.63 | 16 | OK-PRIOR |
| 18 | * pct>=0.3 wall_ahead_mult>=10 lock 0 persist=2 wall_ticks=2 | 171 | 14.7 / 14.7 / 4.5 / -6.3 / -1.4 / -6.0 | +1135 / -391 | +14 | 14.8 / 14.6 | 0.61 / 1.00 | 9 | OK-PRIOR |
| 19 | * pct>=0.6 pulled_mult>=30 scale 0.75 win=8 persist=2 | 298 | 13.1 / 13.1 / 2.8 / -6.1 / 5.1 / -1.3 | +803 / -137 | +26 | 13.5 / 12.9 | 0.48 / 1.00 | 11 | OK-PRIOR |
| 20 | * pct>=0.3 dd>=20 scale 0.75 persist=10 | 457 | 13.9 / 13.9 / 0.7 / -6.5 / 8.3 / -10.5 | +788 / -346 | +24 | 14.1 / 13.7 | 0.15 / 0.90 | 19 | OK-PRIOR |

### U7 equal-MEAN cut beside the best lines, and reference rows (first-order, slip 1.2)
| row | cut L6M / PRE / HOLD / X' | equal-mean cut L6M / PRE | d mean L6M / PRE $/wk | fires |
|--|--|--|--|--|
| NO RULE (live panel as is; reference) | 0 / 0 / 0 / 0 | 0 / 0 | 0 / 0 | 0 |
| REFERENCE live policy line of the blind week: profit U7 * pct>=0.17 tot_rel>=1.5 take win=5 persist=1 | 9.1 / 6.3 / -9.8 / -2.5 | -3.7 / -6.8 | -1951 / -1835 | 1022 |
| top-1: * pct>=0.3 pulled_against_mult>=20 ahead_rel_slow>=1.2 take win=5 persist=3 | 26.8 / 3.7 / -0.2 / -10.3 | 30.3 / 8.4 | +1087 / -260 | 252 |
| top-2: * pct>=0.3 pulled_against_mult>=20 tighten 20 win=5 persist=5 | 26.2 / -0.4 / -12.4 / -1.5 | 28.6 / 2.9 | +723 / -601 | 285 |
| top-3: * pct>=0.3 pulled_against_mult>=20 step 5 win=5 persist=5 | 29.1 / -1.0 / -9.6 / -0.1 | 29.2 / -0.8 | +46 / -461 | 354 |
| top-4: * pct>=0.3 pulled_against_mult>=20 take win=5 persist=5 | 29.4 / -0.6 / -9.9 / -0.4 | 29.5 / -0.4 | +40 / -455 | 375 |
| top-5: * pct>=0.3 pulled_against_mult>=20 tighten 8 win=5 persist=5 | 29.4 / -1.1 / -9.5 / -0.2 | 29.6 / -0.9 | +51 / -484 | 353 |

The D7 v1.5 coded TH-L2 profit branch (`ThL2ProfitOn`, tighten 30 pts behind the best price when the book is thick >= 2x for 10 s from +30 pts) ships OFF; the blind-week live policy line above is the closest live profit rule in the grammar and is the reference row.

### U7 SELECTIVE lines (fire on < 30% of the book's trades, or a non-exit action tighten/lock/step/scale; tolerant on PRE and HOLD (> -5%); not in the top-20) - file /mnt/l2/l2vast/_th_ptr/sel_U7.txt for promotion after the top-5
| # | line | fires | cut L6M / L3M / HOLD / PRE / X' | equal-mean cut L6M / PRE | d mean L6M / PRE | own p / family p (8 lines) | WF % beat | rule 2a |
|--|--|--|--|--|--|--|--|--|
| 1 | * pct>=0.4 delta_mult>=20 tighten 30 win=15 persist=5 | 257 | 24.7 / 24.7 / -0.2 / 3.8 / -0.4 | 30.5 / 11.3 | +1617 / -689 | 0.45 / 1.00 | 15 | OK-PRIOR |
| 2 | * pct>=0.4 delta_mult>=30 step 5 win=15 persist=1 | 311 | 24.3 / 24.3 / -4.6 / 1.7 / 0.1 | 29.1 / 8.0 | +1195 / -65 | 0.49 / 1.00 | 29 | OK-PRIOR |
| 3 | * pct>=0.5 pulled_against_mult>=50 tighten 30 win=15 persist=1 | 172 | 21.4 / 21.4 / -0.9 / 0.6 / -4.2 | 28.7 / 9.9 | +1973 / -104 | 0.59 / 1.00 | 18 | OK-PRIOR |
| 4 | * pct>=0.5 pulled_against_mult>=50 step 20 win=15 persist=1 | 169 | 21.3 / 21.3 / -5.0 / 1.2 / -3.8 | 28.4 / 10.1 | +1875 / -39 | 0.51 / 1.00 | 16 | OK-PRIOR |
| 5 | * pct>=0.3 delta_mult>=30 ahead_rel>=1.2 tighten 16 win=15 persist=1 | 160 | 20.0 / 20.0 / -1.3 / 2.9 / 4.1 | 26.2 / 10.5 | +1471 / -380 | 0.26 / 0.96 | 15 | OK-PRIOR |
| 6 | * pct>=0.3 pulled_against_mult>=20 ahead_rel_slow>=1.2 tighten 16 win=5 persist=3 | 218 | 21.4 / 21.4 / -1.6 / 5.8 / -10.3 | 23.3 / 8.1 | +532 / -485 | 0.22 / 0.89 | 11 | OK-PRIOR |
| 7 | * pct>=0.4 tot_rel_slow>=1.5 tighten 30 persist=2 | 450 | 23.0 / 23.0 / 3.3 / 13.9 / 2.4 | 24.6 / 15.6 | +399 / -360 | 0.07 / 0.37 | 37 | OK-PRIOR |
| 8 | * pct>=0.5 pulled_mult>=5 secs_fav<=0 take win=5 persist=3 | 288 | 25.5 / 25.5 / -2.7 / 1.6 / -1.6 | 25.3 / 1.3 | -62 / -220 | 0.64 / 1.00 | 15 | OK-PRIOR |

### U7 held-out live week replay (frozen file, 11-01..05; REDO-R13 `RL.replay`, slip 1.2; $ = lots x 20 x ((fire price - slip) - live exit))
| line | book targets / clipped | clip cost $ | book give-backs / caught | give-back P&L / saved $ | other trades $ | net $ |
|--|--|--|--|--|--|--|
| * pct>=0.17 tot_rel>=1.5 take win=5 persist=1 | 3 / 1 | -822 | 0 / 0 | +0 / +0 | +9775 | +8953 |
| * pct>=0.3 pulled_against_mult>=20 ahead_rel_slow>=1.2 take win=5 persist=3 | 3 / 0 | +0 | 0 / 0 | +0 / +0 | +4004 | +4004 |
| * pct>=0.3 pulled_against_mult>=20 tighten 20 win=5 persist=5 | 3 / 0 | +0 | 0 / 0 | +0 / +0 | +2614 | +2614 |
| * pct>=0.3 pulled_against_mult>=20 step 5 win=5 persist=5 | 3 / 0 | +0 | 0 / 0 | +0 / +0 | +3464 | +3464 |
| * pct>=0.3 pulled_against_mult>=20 take win=5 persist=5 | 3 / 1 | -2766 | 0 / 0 | +0 / +0 | +4354 | +1588 |
| * pct>=0.3 pulled_against_mult>=20 tighten 8 win=5 persist=5 | 3 / 0 | +0 | 0 / 0 | +0 / +0 | +3784 | +3784 |
| * pct>=0.4 delta_mult>=20 tighten 30 win=15 persist=5 | 3 / 0 | +0 | 0 / 0 | +0 / +0 | +0 | +0 |
| * pct>=0.4 delta_mult>=30 step 5 win=15 persist=1 | 3 / 0 | +0 | 0 / 0 | +0 / +0 | +0 | +0 |
| * pct>=0.5 pulled_against_mult>=50 tighten 30 win=15 persist=1 | 3 / 0 | +0 | 0 / 0 | +0 / +0 | +0 | +0 |
| * pct>=0.5 pulled_against_mult>=50 step 20 win=15 persist=1 | 3 / 0 | +0 | 0 / 0 | +0 / +0 | +0 | +0 |
The week has very few events for this book (3 Target exits, 0 give-backs), so the replay is an anecdote, not evidence.

### U7 EXACT rows (promoted PTR_U7_nn sets vs LPB, slip 0.8 engine hook)
| set | line | months | cut L6M / PRE / X' / HOLD | d mean L6M / PRE | label |
|--|--|--|--|--|--|
| PTR_U7_01 | profit U7 * pct>=0.3 pulled_against_mult>=20 ahead_rel_slow>=1.2 take win=5 persist=3 | 12 | 16.9 / n/a / n/a / -1.3 | +585 / +nan |  |
| PTR_U7_02 | profit U7 * pct>=0.3 pulled_against_mult>=20 tighten 20 win=5 persist=5 | 12 | 16.2 / n/a / n/a / -12.1 | +389 / +nan |  |
| PTR_U7_03 | profit U7 * pct>=0.3 pulled_against_mult>=20 step 5 win=5 persist=5 | 10 | 16.1 / n/a / n/a / n/a | -374 / +nan |  |
| PTR_U7_04 | profit U7 * pct>=0.3 pulled_against_mult>=20 take win=5 persist=5 | 10 | 16.5 / n/a / n/a / n/a | -435 / +nan |  |
| PTR_U7_05 | profit U7 * pct>=0.3 pulled_against_mult>=20 tighten 8 win=5 persist=5 | 10 | 16.5 / n/a / n/a / n/a | -369 / +nan |  |
| PTR_U7_PC01 | profit U7 * pct>=0.5 pulled_mult>=3 secs_fav<=2 take win=8 persist=10 wall_ticks=8 | 12 | 33.2 / n/a / n/a / -7.4 | +958 / +nan |  |
| PTR_U7_PC02 | profit U7 * pct>=0.5 pulled_mult>=3 secs_fav<=2 take win=10 persist=10 wall_ticks=8 | 12 | 33.1 / n/a / n/a / -7.4 | +845 / +nan |  |
| PTR_U7_PC03 | profit U7 * pct>=0.5 pulled_mult>=3 secs_fav<=2 take win=15 persist=10 wall_ticks=8 | 10 | 33.1 / n/a / n/a / n/a | +845 / +nan |  |
| PTR_U7_PC04 | profit U7 * pct>=0.5 pulled_mult>=5 secs_fav<=2 take win=10 persist=10 wall_ticks=8 | 10 | 20.6 / n/a / n/a / n/a | +754 / +nan |  |
| PTR_U7_PC05 | profit U7 * pct>=0.5 pulled_mult>=5 secs_fav<=2 take win=15 persist=10 wall_ticks=8 | 10 | 33.1 / n/a / n/a / n/a | +845 / +nan |  |
| PTR_U7_S01 | profit U7 * pct>=0.4 delta_mult>=20 tighten 30 win=15 persist=5 | 10 | 9.1 / n/a / n/a / n/a | +1074 / +nan |  |

**Plain sentence, U7 (first-order screen, not a verdict):** the best-screening U7 line is "* pct>=0.3 pulled_against_mult>=20 ahead_rel_slow>=1.2 take win=5 persist=3": L6M stack maxDD cut 27% (equal-mean 30.3%) and +1087 $/wk on L6M, but PRE +3.7% (equal-mean 8.4%), X' -10.3%, HOLD -0.2%, bi-weekly WF 14% of periods (bar 60%) and own placebo p 0.27. **U7: the book-based protection is: take the profit at +0.3 of target when against-side cancellations reach 20x MedLevel over 5 s and against depth is 1.2x its slow baseline; in the held-out week it kept 0 of 0 give-backs (U7 had none) and clipped 0 of 3 live targets (cost $0), so the live week says nothing either way; the first-order cost on the fills is the PRE/X'/HOLD columns.** It fires on 252 of the book's trades. The live U7 profit setting stays until exact rows confirm.

## H7 (all sessions)
Top 20 first-order lines (recents-key order from ptr_top20; windows = stack maxDD cut % vs the live panel, + shallower):

| # | line (grammar) | fires | cut L6M / L3M / L1M / HOLD / PRE / X' | d mean L6M / PRE $/wk | worst-20 cut L6M | slip low / high L6M cut | own p / family p (top-20) | WF % beat | rule 2a |
|--|--|--|--|--|--|--|--|--|--|
| 1 | * pct>=0.4 dd>=20 or ice_against>=3 take persist=5 | 463 | 9.8 / 9.8 / 0.0 / 3.1 / 1.9 / 17.1 | +597 / -394 | +12 | 9.9 / 9.7 | 0.04 / 0.38 | 34 | OK-PRIOR |
| 2 | * pct>=0.4 dd>=20 or ice_against>=3 tighten 16 persist=5 | 396 | 9.4 / 9.4 / 0.0 / 3.1 / 1.9 / 15.7 | +516 / -355 | +10 | 9.5 / 9.3 | 0.04 / 0.55 | 33 | OK-PRIOR |
| 3 | * pct>=0.3 pulled_mult>=20 secs_fav<=0 take win=10 persist=2 | 138 | 9.3 / 9.3 / -0.3 / -2.8 / -2.7 / 0.0 | +228 / -295 | +1 | 9.5 / 9.2 | 0.47 / 1.00 | 3 | OK-PRIOR |
| 4 | * pct>=0.2 ice_against>=3 or pulled_mult>=30 take win=5 persist=3 | 516 | 7.1 / 7.1 / 3.7 / -2.8 / 1.7 / 11.4 | +245 / -578 | +12 | 7.3 / 7.0 | 0.26 / 1.00 | 23 | OK-PRIOR |
| 5 | * pct>=0.5 dd>=16 tighten 20 persist=10 | 219 | 6.8 / 6.8 / 0.0 / -1.2 / 0.5 / 14.1 | +442 / -324 | +10 | 6.9 / 6.8 | 0.14 / 0.85 | 11 | OK-PRIOR |
| 6 | * pct>=0.4 sweep_against>=8 tighten 5 win=5 persist=10 | 206 | 9.4 / 9.4 / -2.1 / -1.3 / -5.1 / 6.1 | +233 / -125 | +1 | 9.5 / 9.3 | 0.64 / 1.00 | 1 | OK-PRIOR |
| 7 | * pct>=0.4 sweep_against>=8 take win=5 persist=10 | 213 | 9.5 / 9.5 / -2.1 / -1.3 / -5.1 / 6.0 | +209 / -153 | +1 | 9.6 / 9.4 | 0.66 / 1.00 | 1 | OK-PRIOR |
| 8 | * pct>=0.4 sweep_against>=8 tighten 8 win=5 persist=10 | 200 | 9.3 / 9.3 / -1.9 / -1.5 / -5.4 / 6.2 | +222 / -135 | -0 | 9.4 / 9.2 | 0.77 / 1.00 | 1 | OK-PRIOR |
| 9 | * pct>=0.5 dd>=16 or sweep_against>=8 take win=3 persist=5 | 366 | 8.1 / 8.1 / -1.7 / -1.8 / -2.5 / 9.3 | +363 / -336 | +4 | 8.3 / 8.0 | 0.14 / 0.94 | 11 | OK-PRIOR |
| 10 | * pct>=0.4 sweep_against>=8 step 5 win=5 persist=10 | 200 | 9.0 / 9.0 / -2.2 / -1.7 / -5.1 / 6.2 | +232 / -126 | -0 | 9.1 / 8.9 | 0.75 / 1.00 | 1 | OK-PRIOR |
| 11 | * pct>=0.5 ice_against>=1 tighten 8 persist=3 | 585 | 7.8 / 7.8 / -0.8 / 2.2 / -9.2 / 5.8 | +284 / -620 | -0 | 8.1 / 7.6 | 0.40 / 1.00 | 32 | OK-PRIOR |
| 12 | * pct>=0.5 dd>=16 step 10 persist=10 | 231 | 5.7 / 5.7 / 0.0 / -1.1 / 0.8 / 14.9 | +408 / -253 | +9 | 5.8 / 5.6 | 0.11 / 0.85 | 15 | OK-PRIOR |
| 13 | * pct>=0.2 pulled_mult>=30 take win=8 persist=10 | 49 | 4.4 / 4.4 / 3.8 / -0.9 / -0.9 / 0.0 | +331 / -133 | +5 | 4.5 / 4.4 | 0.52 / 1.00 | 3 | OK-PRIOR |
| 14 | * pct>=0.5 ice_against>=1 step 5 persist=3 | 594 | 6.8 / 6.8 / -0.6 / 2.0 / -9.3 / 6.0 | +309 / -649 | -1 | 7.1 / 6.6 | 0.36 / 1.00 | 32 | OK-PRIOR |
| 15 | * pct>=0.4 delta_mult>=10 lock 10 win=10 persist=10 | 200 | 6.3 / 6.3 / 0.0 / 1.6 / -2.1 / 2.4 | +310 / -139 | +4 | 6.4 / 6.2 | 0.35 / 1.00 | 25 | OK-PRIOR |
| 16 | * pct>=0.4 delta_mult>=10 lock 5 win=10 persist=10 | 182 | 6.4 / 6.4 / 0.0 / 2.4 / -2.8 / 5.8 | +265 / -160 | +3 | 6.6 / 6.4 | 0.41 / 1.00 | 22 | OK-PRIOR |
| 17 | * pct>=0.4 delta_mult>=10 lock 5 win=8 persist=3 | 279 | 9.7 / 9.7 / -4.6 / 1.0 / -1.0 / 10.1 | +107 / -349 | -2 | 9.8 / 9.6 | 0.17 / 0.96 | 24 | OK-PRIOR |
| 18 | * pct>=0.4 delta_mult>=10 lock 2 win=10 persist=10 | 172 | 5.8 / 5.8 / 0.0 / 2.0 / -3.2 / 5.2 | +267 / -62 | +3 | 5.9 / 5.7 | 0.56 / 1.00 | 20 | OK-PRIOR |
| 19 | * pct>=0.2 pulled_mult>=30 scale 0.5 win=8 persist=10 | 49 | 2.2 / 2.2 / 1.9 / 0.0 / 0.0 / 0.0 | +125 / -50 | +2 | 2.2 / 2.2 | 0.36 / 1.00 | 0 | OK-PRIOR |
| 20 | * pct>=0.2 pulled_mult>=30 scale 0.75 win=5 persist=3 | 86 | 2.2 / 2.2 / 1.9 / -0.9 / 1.5 / 0.0 | +141 / -50 | +4 | 2.3 / 2.2 | 0.27 / 1.00 | 3 | OK-PRIOR |

### H7 equal-MEAN cut beside the best lines, and reference rows (first-order, slip 1.2)
| row | cut L6M / PRE / HOLD / X' | equal-mean cut L6M / PRE | d mean L6M / PRE $/wk | fires |
|--|--|--|--|--|
| NO RULE (live panel as is; reference) | 0 / 0 / 0 / 0 | 0 / 0 | 0 / 0 | 0 |
| REFERENCE live policy line of the blind week: profit H7 * pct>=0.3 ahead_rel>=1.5 take win=5 persist=1 | 4.2 / -16.1 / 4.3 / 8.5 | -0.6 / -22.0 | -897 / -1035 | 771 |
| top-1: * pct>=0.4 dd>=20 or ice_against>=3 take persist=5 | 9.8 / 1.9 / 3.1 / 17.1 | 13.0 / 5.3 | +597 / -394 | 463 |
| top-2: * pct>=0.4 dd>=20 or ice_against>=3 tighten 16 persist=5 | 9.4 / 1.9 / 3.1 / 15.7 | 12.1 / 4.9 | +516 / -355 | 396 |
| top-3: * pct>=0.3 pulled_mult>=20 secs_fav<=0 take win=10 persist=2 | 9.3 / -2.7 / -2.8 / 0.0 | 10.4 / -1.4 | +228 / -295 | 138 |
| top-4: * pct>=0.2 ice_against>=3 or pulled_mult>=30 take win=5 persist=3 | 7.1 / 1.7 / -2.8 / 11.4 | 8.2 / 2.9 | +245 / -578 | 516 |
| top-5: * pct>=0.5 dd>=16 tighten 20 persist=10 | 6.8 / 0.5 / -1.2 / 14.1 | 9.2 / 3.1 | +442 / -324 | 219 |

The D7 v1.5 coded TH-L2 profit branch (`ThL2ProfitOn`, tighten 30 pts behind the best price when the book is thick >= 2x for 10 s from +30 pts) ships OFF; the blind-week live policy line above is the closest live profit rule in the grammar and is the reference row.

### H7 SELECTIVE lines (fire on < 30% of the book's trades, or a non-exit action tighten/lock/step/scale; tolerant on PRE and HOLD (> -5%); not in the top-20) - file /mnt/l2/l2vast/_th_ptr/sel_H7.txt for promotion after the top-5
| # | line | fires | cut L6M / L3M / HOLD / PRE / X' | equal-mean cut L6M / PRE | d mean L6M / PRE | own p / family p (8 lines) | WF % beat | rule 2a |
|--|--|--|--|--|--|--|--|--|
| 1 | * pct>=0.5 dd>=16 or sweep_against>=8 tighten 16 win=3 persist=5 | 318 | 6.3 / 6.3 / -1.0 / -2.5 / 9.5 | 7.6 / -1.1 | +266 / -393 | 0.22 / 0.75 | 13 | OK-PRIOR |
| 2 | * pct>=0.5 dd>=16 tighten 12 persist=10 | 238 | 5.7 / 5.7 / -1.1 / 0.9 / 14.5 | 8.0 / 3.3 | +414 / -266 | 0.17 / 0.63 | 15 | OK-PRIOR |
| 3 | * pct>=0.5 dd>=16 tighten 5 persist=10 | 238 | 5.7 / 5.7 / -1.1 / 0.9 / 14.5 | 8.0 / 3.3 | +414 / -266 | 0.17 / 0.63 | 15 | OK-PRIOR |
| 4 | * pct>=0.2 ice_against>=3 or pulled_mult>=30 tighten 16 win=5 persist=3 | 458 | 6.3 / 6.3 / -3.0 / 1.5 / 12.7 | 7.1 / 2.4 | +179 / -362 | 0.30 / 0.88 | 23 | OK-PRIOR |
| 5 | * pct>=0.4 delta_mult>=10 tighten 20 win=10 persist=10 | 311 | 8.4 / 8.4 / 3.2 / -2.3 / 5.0 | 8.7 / -2.0 | +60 / -264 | 0.24 / 0.82 | 22 | OK-PRIOR |
| 6 | * pct>=0.2 pulled_mult>=30 tighten 5 win=8 persist=10 | 49 | 4.4 / 4.4 / -0.9 / -0.9 / 0.0 | 6.1 / 0.8 | +327 / -134 | 0.50 / 0.98 | 3 | OK-PRIOR |
| 7 | * pct>=0.2 pulled_mult>=30 tighten 8 win=8 persist=10 | 48 | 4.2 / 4.2 / -0.9 / -0.9 / 0.0 | 5.8 / 0.7 | +308 / -128 | 0.63 / 0.99 | 3 | OK-PRIOR |
| 8 | * pct>=0.4 ice_against>=3 tighten 8 persist=5 | 329 | 6.6 / 6.6 / 0.0 / -1.1 / 18.8 | 7.8 / 0.2 | +225 / -166 | 0.10 / 0.60 | 9 | OK-PRIOR |

### H7 held-out live week replay (frozen file, 11-01..05; REDO-R13 `RL.replay`, slip 1.2; $ = lots x 20 x ((fire price - slip) - live exit))
| line | book targets / clipped | clip cost $ | book give-backs / caught | give-back P&L / saved $ | other trades $ | net $ |
|--|--|--|--|--|--|--|
| * pct>=0.3 ahead_rel>=1.5 take win=5 persist=1 | 1 / 1 | -684 | 2 / 2 | -1974 / +3213 | +0 | +2529 |
| * pct>=0.4 dd>=20 or ice_against>=3 take persist=5 | 1 / 1 | -659 | 2 / 0 | -1974 / +0 | +0 | -659 |
| * pct>=0.4 dd>=20 or ice_against>=3 tighten 16 persist=5 | 1 / 1 | -799 | 2 / 0 | -1974 / +0 | +0 | -799 |
| * pct>=0.3 pulled_mult>=20 secs_fav<=0 take win=10 persist=2 | 1 / 0 | +0 | 2 / 0 | -1974 / +0 | +0 | +0 |
| * pct>=0.2 ice_against>=3 or pulled_mult>=30 take win=5 persist=3 | 1 / 1 | -652 | 2 / 0 | -1974 / +0 | +0 | -652 |
| * pct>=0.5 dd>=16 tighten 20 persist=10 | 1 / 0 | +0 | 2 / 0 | -1974 / +0 | +0 | +0 |
| * pct>=0.5 dd>=16 or sweep_against>=8 tighten 16 win=3 persist=5 | 1 / 0 | +0 | 2 / 0 | -1974 / +0 | +0 | +0 |
| * pct>=0.5 dd>=16 tighten 12 persist=10 | 1 / 0 | +0 | 2 / 0 | -1974 / +0 | +0 | +0 |
| * pct>=0.5 dd>=16 tighten 5 persist=10 | 1 / 0 | +0 | 2 / 0 | -1974 / +0 | +0 | +0 |
| * pct>=0.2 ice_against>=3 or pulled_mult>=30 tighten 16 win=5 persist=3 | 1 / 1 | -799 | 2 / 0 | -1974 / +0 | +0 | -799 |
The week has very few events for this book (1 Target exits, 2 give-backs), so the replay is an anecdote, not evidence.

### H7 EXACT rows (promoted PTR_H7_nn sets vs LPB, slip 0.8 engine hook)
| set | line | months | cut L6M / PRE / X' / HOLD | d mean L6M / PRE | label |
|--|--|--|--|--|--|
| PTR_H7_01 | profit H7 * pct>=0.4 dd>=20 or ice_against>=3 take persist=5 | 23 | 4.8 / n/a / n/a / 3.0 | +367 / +nan |  |
| PTR_H7_02 | profit H7 * pct>=0.4 dd>=20 or ice_against>=3 tighten 16 persist=5 | 23 | 4.3 / n/a / n/a / 3.0 | +286 / +nan |  |
| PTR_H7_03 | profit H7 * pct>=0.3 pulled_mult>=20 secs_fav<=0 take win=10 persist=2 | 10 | 11.2 / n/a / n/a / n/a | -262 / +nan |  |
| PTR_H7_04 | profit H7 * pct>=0.2 ice_against>=3 or pulled_mult>=30 take win=5 persist=3 | 10 | 7.2 / n/a / n/a / n/a | +319 / +nan |  |
| PTR_H7_05 | profit H7 * pct>=0.5 dd>=16 tighten 20 persist=10 | 10 | 1.7 / n/a / n/a / n/a | +189 / +nan |  |
| PTR_H7_06 | profit H7 * pct>=0.4 sweep_against>=8 tighten 5 win=5 persist=10 | 10 | 8.6 / n/a / n/a / n/a | +30 / +nan |  |
| PTR_H7_07 | profit H7 * pct>=0.4 sweep_against>=8 take win=5 persist=10 | 10 | 8.8 / n/a / n/a / n/a | +7 / +nan |  |
| PTR_H7_08 | profit H7 * pct>=0.4 sweep_against>=8 tighten 8 win=5 persist=10 | 10 | 8.5 / n/a / n/a / n/a | +10 / +nan |  |
| PTR_H7_09 | profit H7 * pct>=0.5 dd>=16 or sweep_against>=8 take win=3 persist=5 | 10 | 5.1 / n/a / n/a / n/a | +118 / +nan |  |
| PTR_H7_10 | profit H7 * pct>=0.4 sweep_against>=8 step 5 win=5 persist=10 | 10 | 8.2 / n/a / n/a / n/a | +17 / +nan |  |
| PTR_H7_11 | profit H7 * pct>=0.5 ice_against>=1 tighten 8 persist=3 | 10 | 6.0 / n/a / n/a / n/a | +39 / +nan |  |
| PTR_H7_12 | profit H7 * pct>=0.5 dd>=16 step 10 persist=10 | 10 | 0.4 / n/a / n/a / n/a | +144 / +nan |  |
| PTR_H7_13 | profit H7 * pct>=0.2 pulled_mult>=30 take win=8 persist=10 | 10 | 4.5 / n/a / n/a / n/a | +316 / +nan |  |
| PTR_H7_14 | profit H7 * pct>=0.5 ice_against>=1 step 5 persist=3 | 10 | 5.0 / n/a / n/a / n/a | +54 / +nan |  |
| PTR_H7_15 | profit H7 * pct>=0.4 delta_mult>=10 lock 10 win=10 persist=10 | 10 | 2.2 / n/a / n/a / n/a | -208 / +nan |  |
| PTR_H7_16 | profit H7 * pct>=0.4 delta_mult>=10 lock 5 win=10 persist=10 | 10 | 2.5 / n/a / n/a / n/a | +94 / +nan |  |
| PTR_H7_17 | profit H7 * pct>=0.4 delta_mult>=10 lock 5 win=8 persist=3 | 10 | 5.8 / n/a / n/a / n/a | -30 / +nan |  |
| PTR_H7_18 | profit H7 * pct>=0.4 delta_mult>=10 lock 2 win=10 persist=10 | 10 | 2.0 / n/a / n/a / n/a | +118 / +nan |  |
| PTR_H7_19 | profit H7 * pct>=0.2 pulled_mult>=30 scale 0.5 win=8 persist=10 | 2 | n/a / n/a / n/a / n/a | +nan / +nan |  |
| PTR_H7_20 | profit H7 * pct>=0.2 pulled_mult>=30 scale 0.75 win=5 persist=3 | 2 | n/a / n/a / n/a / n/a | +nan / +nan |  |
| PTR_H7_S01 | profit H7 * pct>=0.5 dd>=16 or sweep_against>=8 tighten 16 win=3 persist=5 | 23 | 3.4 / n/a / n/a / -1.0 | +115 / +nan |  |

**Plain sentence, H7 (first-order only, not a verdict):** the best H7 line is "* pct>=0.4 dd>=20 or ice_against>=3 take persist=5": it cuts L6M stack maxDD by 10% (HOLD +3.1%, PRE +1.9%, X' +17.1%) with d mean +597$/wk L6M, own placebo p 0.04, and a bi-weekly WF of 34% (bar 60%). H7 is a small book (about 1,100 trades), so every cut here is inside the noise of the stack; the protection is "take when the giveback from the extreme reaches 20 points or against-side refills reach 3", costing a few hundred dollars a week on PRE. A book whose best cell is this small is still delivered with the number; the live H7 setting stays. **H7: the book-based protection is "take when the giveback from the extreme reaches 20 points or against-side refills reach 3, from +0.4 of target"; in the held-out week it caught 0 of H7's 2 give-backs (-$1,974) and clipped its 1 live target (cost $659): it keeps none of the give-backs and costs the one fill - one-week anecdote.**

