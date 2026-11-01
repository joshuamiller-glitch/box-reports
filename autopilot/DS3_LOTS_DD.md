# DS3_LOTS_DD - lots re-solved under a drawdown constraint (E1, overnight order section E; Sat 2026-10-31 night). POST-HOC, SHADOW TABLE ONLY, nothing here is a PASS and nothing goes live

Capped 20260206, UNTOUCHED never read, no post-cap file opened. Engine DS3_ONE_CONVENTION (oc_lib.py unchanged; only a custom lot-table hook, `l2vast/ds3/code/lotsdd/ld_lib.py`), the Sunday composite (six pieces, slip +0.25, K6 70/30, parity stop, running max over taken signals, session-lot BookR, integer half-up min-1 ER lots), tie-out to DS3_DRAWDOWN exact (live composite L6M +41.1 / maxDD 22.9, PRE 241.2, 12R L6M +32.3). Prereg `l2vast/ds3/prereg/E1_LOTSDD_prereg.md` sha256 120d8cc019c2b544f3cb0881760549e4f187ec9dcf45d46130734f5d249eda5d (in DECISIONS.md before scoring). Units $k per week unless stated; windows L3M 14 / L6M 28 / HOLD 32 / PRE 75 / X' 44 weeks, ALL 149. A cell of the risk tables reads `mean / maxDD / weekly SD`; worst-20 is shown only for PRE, X', ALL (the L-windows have fewer than 20 losing weeks; there it is not a tail measure).

**How the 20 is counted.** Total lots = the sum over the six books of the book BASE lot, the largest session lot of that book (live: K6 2 + P6 7 + U6 4 + H6 4 + M6 2 + A6 1 = 20; O6 exempt and excluded). The constraint is sum of base lots <= 20; each session of a book may then be 0..base (0 = session off). The memo row 'session-lot sum' (live 48 = K6 4x2 + P6 3x7 + U6 2x4 + H6 4+2 + M6 2x2 + A6 1) is NOT constrained. 14 integer cells: K6 Asia/London/NY-AM/NY-PM, P6 Asia/London/NY-AM, U6 Asia/London, H6 Asia/NY-AM, M6 London/NY-AM, A6 Asia.

**The constraint** = weekly-cumulative maxDD on the solve window <= k x the maxDD of the LIVE composite on the same window and the same lock scenario, k = 1.0 / 0.75 / 0.5. Two lock scenarios: combined week lock off, and 12R(K6). Objective = mean $/wk on the solve window. The three tables below are solved on ALL 149 weeks (IN-SAMPLE; the live composite ALL maxDD is 241.2 off / 232.6 under 12R, one episode in PRE). Out-of-sample evidence is the walk-forward and the fixed-table protocol further down; read those before the tables.

### Table 1a - lot tables solved on ALL 149 wk (IN-SAMPLE), lock off
| cell | live | 1.0x cap | 0.75x cap | 0.5x cap |
|---|---|---|---|---|
| K6 asia | 2 | 5 | 5 | 5 |
| K6 london | 2 | 3 | 3 | 3 |
| K6 nyam | 2 | 5 | 5 | 5 |
| K6 nypm | 2 | 5 | 5 | 0 |
| P6 asia | 7 | 11 | 11 | 9 |
| P6 london | 7 | 11 | 0 | 0 |
| P6 nyam | 7 | 9 | 9 | 7 |
| U6 asia | 4 | 1 | 1 | 4 |
| U6 london | 4 | 1 | 1 | 3 |
| H6 asia | 4 | 2 | 2 | 1 |
| H6 nyam | 2 | 2 | 2 | 1 |
| M6 london | 2 | 1 | 1 | 0 |
| M6 nyam | 2 | 1 | 1 | 0 |
| A6 asia | 1 | 0 | 0 | 1 |
| base lots (THE 20: sum over books of max session lot) | 20 | 20 | 20 | 20 |
| session-lot sum (memo, not constrained) | 48 | 57 | 46 | 39 |

True-engine maxDD vs cap (ALL, $k): 1.0x: 237 vs cap 241; 0.75x: 178 vs cap 181; 0.5x: 118 vs cap 121.

### Table 1b - lot tables solved on ALL 149 wk (IN-SAMPLE), 12R
| cell | live | 1.0x cap | 0.75x cap | 0.5x cap |
|---|---|---|---|---|
| K6 asia | 2 | 3 | 3 | 1 |
| K6 london | 2 | 3 | 2 | 2 |
| K6 nyam | 2 | 3 | 3 | 2 |
| K6 nypm | 2 | 3 | 2 | 2 |
| P6 asia | 7 | 7 | 7 | 7 |
| P6 london | 7 | 7 | 7 | 7 |
| P6 nyam | 7 | 7 | 7 | 1 |
| U6 asia | 4 | 2 | 4 | 4 |
| U6 london | 4 | 0 | 4 | 3 |
| H6 asia | 4 | 4 | 3 | 3 |
| H6 nyam | 2 | 4 | 2 | 2 |
| M6 london | 2 | 1 | 1 | 2 |
| M6 nyam | 2 | 1 | 2 | 0 |
| A6 asia | 1 | 3 | 1 | 0 |
| base lots (THE 20: sum over books of max session lot) | 20 | 20 | 20 | 18 |
| session-lot sum (memo, not constrained) | 48 | 48 | 48 | 36 |

True-engine maxDD vs cap (ALL, $k): 1.0x: 173 vs cap 233; 0.75x: 147 vs cap 174; 0.5x: 117 vs cap 116 (INFEASIBLE by 1k).

### Table 2 - risk lines of the live table and the six ALL-solved tables (true engine; `mean / maxDD / SD`, $k)
| lock | table | L3M | L6M | HOLD | PRE | X' | ALL | worst-20 PRE / X' / ALL | Calmar ALL | mean / abs(w20) ALL |
|---|---|---|---|---|---|---|---|---|---|---|
| lock off | live | 34.4 / 21 / 45 | 41.1 / 23 / 43 | 38.6 / 97 / 52 | 23.1 / 241 / 56 | 8.0 / 121 / 33 | 22.3 / 241 / 50 | -875 / -420 / -1098 | 0.092 | 0.0203 |
| lock off | solved 1.0x | 46.8 / 46 / 65 | 55.0 / 46 / 62 | 53.7 / 80 / 71 | 31.0 / 234 / 69 | 8.8 / 237 / 47 | 29.8 / 237 / 66 | -997 / -665 / -1317 | 0.126 | 0.0226 |
| lock off | solved 0.75x | 36.3 / 80 / 69 | 45.4 / 58 / 57 | 43.4 / 96 / 65 | 32.5 / 178 / 64 | 8.4 / 124 / 46 | 28.2 / 178 / 61 | -845 / -608 / -1286 | 0.159 | 0.0219 |
| lock off | solved 0.5x | 31.7 / 91 / 64 | 39.5 / 48 / 51 | 36.6 / 91 / 58 | 27.5 / 118 / 53 | 10.2 / 97 / 38 | 24.7 / 118 / 51 | -618 / -440 / -982 | 0.210 | 0.0252 |
| 12R | live | 29.0 / 27 / 48 | 32.3 / 27 / 45 | 31.4 / 35 / 49 | 15.1 / 233 / 50 | 1.0 / 120 / 30 | 14.7 / 233 / 46 | -608 / -468 / -688 | 0.063 | 0.0213 |
| 12R | solved 1.0x | 37.4 / 28 / 58 | 44.1 / 28 / 54 | 38.4 / 130 / 60 | 19.5 / 173 / 59 | 3.2 / 165 / 35 | 19.0 / 173 / 55 | -740 / -556 / -889 | 0.110 | 0.0214 |
| 12R | solved 0.75x | 28.1 / 36 / 51 | 31.2 / 36 / 48 | 29.1 / 70 / 54 | 19.7 / 147 / 54 | 5.9 / 93 / 32 | 17.9 / 147 / 50 | -686 / -466 / -806 | 0.122 | 0.0222 |
| 12R | solved 0.5x | 22.1 / 25 / 47 | 29.3 / 44 / 44 | 28.7 / 44 / 45 | 7.6 / 115 / 36 | 0.7 / 117 / 29 | 10.2 / 117 / 38 | -526 / -445 / -624 | 0.087 | 0.0164 |

**Walk-forward in one sentence (lock off, cap 1.0x, monthly re-solve on the trailing 6 months, next month scored, 25 months 2024-01..2026-01):** the solver reports a mean of 39.9 on its own windows against 23.2 for the live table on the same windows (+16.7), but the next month delivers 27.8 against 28.4 for live (-0.7, MDE 11.6), maxDD 233 vs 241, worst-20 -1279 vs -989, weekly SD 62.7 vs 54.4, with 16 lots of table churn per month (sum of absolute cell changes, 6.8 of 14 cells move) - so monthly re-solving buys no out-of-sample mean and no tail relief; the 0.5x cap lowers the chained maxDD to 173 (-28%) at -2.7 but its forward 26-week maxDD is 1.55x its own target (median) and the worst-20 is not better (-997); under the 12R lock the re-solved tables are worse than live (13.7 vs 19.9).

**Shadow recommendation: none of the solved tables.** The half-way table (average of solved and live, rounded half up) is the only variant that is not worse than live out-of-sample in the walk-forward with the lock off: cap 1.0x / 0.75x / 0.5x mean 29.4 / 29.0 / 28.7 vs live 28.4, maxDD 192 / 164 / 127 vs 241; but that maxDD gain is ONE drawdown episode (PRE, 2024-25), the fixed-table protocol (section 2) does not reproduce it, and under 12R the same construction is inconsistent across caps (maxDD 147 / 234 / 271 vs 233, mean -3.5 / -11.0 / -6.5). The user decides lots; the live table stays.

Page 2 onward: fixed-table protocol, walk-forward detail, placebo, overfitting, cost of being wrong, method. Files: `l2vast/ds3/code/lotsdd/`, `l2vast/ds3/out/lotsdd/` (cache_all.pkl = every true-engine daily series, ~9.5k tables; final_sel.json = every key's table; risk_lines.csv; lot_tables.csv; wf_tables.csv).

## 2. Fixed table, solved once, judged out of sample (the one recent look)

Solved on PRE+X' (20230401..20250630, 118 weeks; cap = k x live composite maxDD on that span), judged on L6M and HOLD, which the solver never saw. Reverse: solved on HOLD (20250701..20260206, 32 weeks), judged on PRE and X'. `shrunk` = round-half-up average of solved and live.

### Table 3 - solved on PRE+X', lock off: lot tables
| cell | live | 1.0x | 0.75x | 0.5x |
|---|---|---|---|---|
| K6 asia | 2 | 5 | 5 | 5 |
| K6 london | 2 | 0 | 0 | 3 |
| K6 nyam | 2 | 5 | 5 | 5 |
| K6 nypm | 2 | 5 | 5 | 1 |
| P6 asia | 7 | 11 | 8 | 9 |
| P6 london | 7 | 0 | 7 | 2 |
| P6 nyam | 7 | 10 | 6 | 10 |
| U6 asia | 4 | 2 | 0 | 3 |
| U6 london | 4 | 2 | 0 | 1 |
| H6 asia | 4 | 0 | 0 | 0 |
| H6 nyam | 2 | 1 | 0 | 1 |
| M6 london | 2 | 0 | 1 | 0 |
| M6 nyam | 2 | 0 | 4 | 0 |
| A6 asia | 1 | 1 | 3 | 1 |
| base lots (THE 20: sum over books of max session lot) | 20 | 20 | 20 | 20 |
| session-lot sum (memo, not constrained) | 48 | 42 | 44 | 41 |

In-sample (solve window) true maxDD vs cap ($k): 1.0x 220 vs 241, mean 25.8 vs live 17.6; 0.75x 158 vs 181, mean 24.0 vs live 17.6; 0.5x 116 vs 121, mean 22.5 vs live 17.6.

| table | L6M mean / maxDD / SD | HOLD mean / maxDD / SD | in-sample mean / maxDD | placebo (true engine, feasible random, same 20) |
|---|---|---|---|---|
| live | 41.1 / 23 / 43 | 38.6 / 97 / 52 | - | - |
| 1.0x solved | 38.6 / 64 / 64 | 36.2 / 102 / 69 | 25.8 / 220 | n=274/300 feasible; L6M mean rank 0.07, maxDD rank 0.83; HOLD 0.06/0.87 |
| 1.0x shrunk | 41.1 / 34 / 56 | 38.0 / 116 / 63 | 19.9 / 167 |  |
| 0.75x solved | 33.6 / 59 / 54 | 32.2 / 109 / 62 | 24.0 / 158 | n/a (not run) |
| 0.75x shrunk | 41.7 / 34 / 49 | 39.5 / 93 / 56 | 20.1 / 188 |  |
| 0.5x solved | 39.0 / 48 / 50 | 36.9 / 89 / 59 | 22.5 / 116 | n=31/300 feasible; L6M mean rank 0.00, maxDD rank 0.74; HOLD 0.00/0.81 |
| 0.5x shrunk | 37.3 / 29 / 48 | 35.5 / 116 / 58 | 18.6 / 186 |  |

### Table 3 - solved on PRE+X', 12R: lot tables
| cell | live | 1.0x | 0.75x | 0.5x |
|---|---|---|---|---|
| K6 asia | 2 | 3 | 2 | 1 |
| K6 london | 2 | 2 | 2 | 2 |
| K6 nyam | 2 | 3 | 3 | 2 |
| K6 nypm | 2 | 2 | 2 | 2 |
| P6 asia | 7 | 7 | 7 | 7 |
| P6 london | 7 | 8 | 6 | 7 |
| P6 nyam | 7 | 9 | 3 | 1 |
| U6 asia | 4 | 2 | 4 | 4 |
| U6 london | 4 | 0 | 4 | 3 |
| H6 asia | 4 | 3 | 3 | 3 |
| H6 nyam | 2 | 0 | 2 | 2 |
| M6 london | 2 | 0 | 2 | 2 |
| M6 nyam | 2 | 0 | 2 | 0 |
| A6 asia | 1 | 3 | 1 | 0 |
| base lots (THE 20: sum over books of max session lot) | 20 | 20 | 20 | 18 |
| session-lot sum (memo, not constrained) | 48 | 42 | 43 | 36 |

In-sample (solve window) true maxDD vs cap ($k): 1.0x 182 vs 233, mean 15.1 vs live 10.0; 0.75x 118 vs 174, mean 10.6 vs live 10.0; 0.5x 117 vs 116 INFEASIBLE, mean 5.1 vs live 10.0.

| table | L6M mean / maxDD / SD | HOLD mean / maxDD / SD | in-sample mean / maxDD | placebo (true engine, feasible random, same 20) |
|---|---|---|---|---|
| live | 32.3 / 27 / 45 | 31.4 / 35 / 49 | - | - |
| 1.0x solved | 29.7 / 50 / 55 | 27.2 / 104 / 61 | 15.1 / 182 | n=299/400 feasible; L6M mean rank 0.16, maxDD rank 0.38; HOLD 0.14/0.84 |
| 1.0x shrunk | 34.5 / 57 / 54 | 32.4 / 68 / 60 | 13.7 / 143 |  |
| 0.75x solved | 30.3 / 33 / 45 | 27.7 / 70 / 50 | 10.6 / 118 | n/a (not run) |
| 0.75x shrunk | 29.3 / 34 / 46 | 27.1 / 69 / 51 | 11.5 / 132 |  |
| 0.5x solved | 29.3 / 44 / 44 | 28.7 / 44 / 45 | 5.1 / 117 | n=25/400 feasible; L6M mean rank 0.00, maxDD rank 0.28; HOLD 0.00/0.08 |
| 0.5x shrunk | 35.1 / 23 / 44 | 32.4 / 48 / 48 | 7.1 / 139 |  |

### Table 3 - solved on HOLD, lock off: lot tables
| cell | live | 1.0x | 0.75x | 0.5x |
|---|---|---|---|---|
| K6 asia | 2 | 4 | 2 | 1 |
| K6 london | 2 | 5 | 5 | 5 |
| K6 nyam | 2 | 2 | 5 | 3 |
| K6 nypm | 2 | 5 | 0 | 4 |
| P6 asia | 7 | 9 | 9 | 8 |
| P6 london | 7 | 9 | 9 | 7 |
| P6 nyam | 7 | 8 | 8 | 7 |
| U6 asia | 4 | 0 | 0 | 0 |
| U6 london | 4 | 0 | 0 | 0 |
| H6 asia | 4 | 6 | 6 | 6 |
| H6 nyam | 2 | 6 | 6 | 6 |
| M6 london | 2 | 0 | 0 | 0 |
| M6 nyam | 2 | 0 | 0 | 0 |
| A6 asia | 1 | 0 | 0 | 0 |
| base lots (THE 20: sum over books of max session lot) | 20 | 20 | 20 | 19 |
| session-lot sum (memo, not constrained) | 48 | 54 | 50 | 47 |

In-sample (solve window) true maxDD vs cap ($k): 1.0x 92 vs 97, mean 58.3 vs live 38.6; 0.75x 72 vs 73, mean 57.3 vs live 38.6; 0.5x 44 vs 48, mean 50.6 vs live 38.6.

| table | PRE mean / maxDD / SD | X' mean / maxDD / SD | in-sample mean / maxDD | placebo (true engine, feasible random, same 20) |
|---|---|---|---|---|
| live | 23.1 / 241 / 56 | 8.0 / 121 / 33 | - | - |
| 1.0x solved | 23.5 / 374 / 69 | 3.7 / 226 / 40 | 58.3 / 92 | n/a (not run) |
| 1.0x shrunk | 22.4 / 288 / 65 | 6.3 / 183 / 38 | 46.7 / 101 |  |
| 0.75x solved | 26.8 / 214 / 65 | 6.9 / 201 / 40 | 57.3 / 72 | n/a (not run) |
| 0.75x shrunk | 23.9 / 202 / 64 | 6.9 / 175 / 38 | 46.0 / 113 |  |
| 0.5x solved | 21.3 / 313 / 59 | 4.1 / 180 / 35 | 50.6 / 44 | n/a (not run) |
| 0.5x shrunk | 25.1 / 226 / 61 | 6.0 / 174 / 35 | 46.2 / 89 |  |

### Table 3 - solved on HOLD, 12R: lot tables
| cell | live | 1.0x | 0.75x | 0.5x |
|---|---|---|---|---|
| K6 asia | 2 | 2 | 2 | 2 |
| K6 london | 2 | 2 | 2 | 2 |
| K6 nyam | 2 | 0 | 0 | 0 |
| K6 nypm | 2 | 2 | 2 | 2 |
| P6 asia | 7 | 8 | 8 | 8 |
| P6 london | 7 | 7 | 5 | 5 |
| P6 nyam | 7 | 7 | 6 | 6 |
| U6 asia | 4 | 1 | 3 | 3 |
| U6 london | 4 | 1 | 3 | 3 |
| H6 asia | 4 | 5 | 4 | 4 |
| H6 nyam | 2 | 5 | 4 | 4 |
| M6 london | 2 | 3 | 2 | 2 |
| M6 nyam | 2 | 3 | 2 | 2 |
| A6 asia | 1 | 1 | 1 | 1 |
| base lots (THE 20: sum over books of max session lot) | 20 | 20 | 20 | 20 |
| session-lot sum (memo, not constrained) | 48 | 47 | 44 | 44 |

In-sample (solve window) true maxDD vs cap ($k): 1.0x 35 vs 35, mean 40.3 vs live 31.4; 0.75x 22 vs 27, mean 33.6 vs live 31.4; 0.5x 22 vs 18 INFEASIBLE, mean 33.6 vs live 31.4.

| table | PRE mean / maxDD / SD | X' mean / maxDD / SD | in-sample mean / maxDD | placebo (true engine, feasible random, same 20) |
|---|---|---|---|---|
| live | 15.1 / 233 / 50 | 1.0 / 120 / 30 | - | - |
| 1.0x solved | 11.9 / 211 / 51 | -7.1 / 388 / 29 | 40.3 / 35 | n/a (not run) |
| 1.0x shrunk | 11.3 / 208 / 51 | -1.3 / 161 / 31 | 34.4 / 36 |  |
| 0.75x solved | 14.7 / 130 / 45 | -0.4 / 148 / 26 | 33.6 / 22 | n/a (not run) |
| 0.75x shrunk | 15.7 / 237 / 49 | 0.8 / 151 / 29 | 30.9 / 26 |  |
| 0.5x solved | 14.7 / 130 / 45 | -0.4 / 148 / 26 | 33.6 / 22 | n/a (not run) |
| 0.5x shrunk | 15.7 / 237 / 49 | 0.8 / 151 / 29 | 30.9 / 26 |  |

### Reading of the fixed-table protocol
* lock off, solved on PRE+X' then judged: L6M mean 38.6 / 33.6 / 39.0 (1.0x / 0.75x / 0.5x) vs live 41.1, L6M maxDD 64 / 59 / 48 vs 23; HOLD maxDD 102 / 109 / 89 vs 97. Solved on HOLD then judged on PRE: maxDD 374 / 214 / 313 vs live 241; X' maxDD 226 / 201 / 180 vs 121; PRE mean 23.5 / 26.8 / 21.3 vs 23.1.
* 12R, solved on PRE+X' then judged: L6M mean 29.7 / 30.3 / 29.3 (1.0x / 0.75x / 0.5x) vs live 32.3, L6M maxDD 50 / 33 / 44 vs 27; HOLD maxDD 104 / 70 / 44 vs 35. Solved on HOLD then judged on PRE: maxDD 211 / 130 / 130 vs live 233; X' maxDD 388 / 148 / 148 vs 120; PRE mean 11.9 / 14.7 / 14.7 vs 15.1.
* A cap met in the solve window is not met in the judged window: the recent-fit tables load P6/K6 and the 2024-25 episode then costs more than live; the PRE-fit tables load the same books and the recent windows' maxDD is several times the live value. The mean gain in the judged windows is small or negative against live (compare the columns).

## 3. Walk-forward: monthly re-solve on the trailing 6 months, next month scored (2024-01..2026-01, 25 months)

Per month: solve on the 26-ish label weeks before the month (cap = k x the live composite maxDD in that window), run the chosen table through the true engine on the full history, take that table's daily series for the month's own days, chain the 25 months. OOS window 20240101..20260131; live = the same days. `S` = solved table, `H` = half-way (solved+live)/2 rounded half up. dMean = paired weekly delta vs live over the chained weeks, MDE = 2.8 x SE. In-sample = mean of the solved table on its own solve windows (true engine); live in-sample on the same windows is 23.2 (off) / 15.2 (12R). Turnover = mean over consecutive months of the sum of absolute cell changes (lots); vs live = mean sum of absolute cell differences to the live table. Forward-26w maxDD/target = maxDD of the table over the 26 weeks starting at the month (overlapping, diagnostic) divided by that month's cap; live shown for reference. Month hit = share of months in which the table beat live in dollars.

| lock | table | OOS mean | OOS maxDD | OOS SD | OOS worst-20 | OOS Calmar | dMean vs live (MDE) | in-sample mean | IS - OOS gap | month hit | turnover / vs live | fwd-26w maxDD / target (median) | in-sample feasible months |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| lock off | live | 28.4 | 241 | 54.4 | -989 | 0.118 | - | 23.2 | - | - | 0 / 0 | - | - |
| lock off | solved 1.0x | 27.8 | 233 | 62.7 | -1279 | 0.119 | -0.7 (11.6) | 39.9 | 17.4 | 64% | 15.9 / 32.4 | 0.94 (live 1.01) | 100% |
| lock off | solved 0.75x | 27.0 | 199 | 61.2 | -1178 | 0.136 | -1.4 (11.7) | 39.7 | 17.9 | 52% | 17.0 / 33.4 | 1.19 (live 1.35) | 100% |
| lock off | solved 0.5x | 25.7 | 173 | 55.1 | -997 | 0.149 | -2.7 (11.0) | 35.8 | 15.3 | 44% | 18.8 / 30.0 | 1.55 (live 2.03) | 100% |
| lock off | half-way 1.0x | 29.4 | 192 | 56.6 | -989 | 0.153 | 1.0 (6.4) | 30.8 | 6.6 | 68% | 9.0 / 18.7 | 0.86 (live 1.01) | - |
| lock off | half-way 0.75x | 29.0 | 164 | 54.9 | -922 | 0.177 | 0.6 (6.8) | 30.5 | 6.7 | 60% | 10.0 / 19.2 | 1.05 (live 1.35) | - |
| lock off | half-way 0.5x | 28.7 | 127 | 54.9 | -879 | 0.226 | 0.3 (6.5) | 28.7 | 5.2 | 56% | 11.3 / 17.4 | 1.52 (live 2.03) | - |
| 12R | live | 19.9 | 233 | 49.7 | -622 | 0.086 | - | 15.2 | - | - | 0 / 0 | - | - |
| 12R | solved 1.0x | 13.7 | 180 | 45.3 | -870 | 0.076 | -6.2 (11.0) | 27.5 | 18.5 | 28% | 18.9 / 25.0 | 0.84 (live 0.61) | 100% |
| 12R | solved 0.75x | 10.6 | 169 | 40.3 | -733 | 0.062 | -9.4 (10.4) | 22.4 | 16.5 | 36% | 21.0 / 26.5 | 1.28 (live 0.82) | 100% |
| 12R | solved 0.5x | 6.7 | 383 | 38.4 | -719 | 0.017 | -13.2 (9.8) | 19.0 | 17.0 | 12% | 16.3 / 23.4 | 1.52 (live 1.23) | 76% |
| 12R | half-way 1.0x | 16.5 | 147 | 49.2 | -771 | 0.112 | -3.5 (7.5) | 20.9 | 9.1 | 28% | 11.4 / 14.6 | 0.69 (live 0.61) | - |
| 12R | half-way 0.75x | 9.0 | 234 | 42.0 | -712 | 0.038 | -11.0 (8.6) | 17.5 | 13.2 | 16% | 13.2 / 16.3 | 1.04 (live 0.82) | - |
| 12R | half-way 0.5x | 13.4 | 271 | 43.6 | -644 | 0.050 | -6.5 (6.7) | 15.4 | 6.7 | 16% | 9.5 / 13.1 | 1.45 (live 1.23) | - |

`IS - OOS gap` = (solved in-sample mean minus live in-sample mean on the same windows) minus (OOS dMean): the part of the in-sample uplift that did not survive.

### Reading
* lock off: re-solving monthly changes 6.8 of 14 cells per month on average (sum of absolute changes 15.9 lots; largest single month 54), and the solved table sits on average 32 lots (L1) from the live table. Realised vs target: the search found a table feasible in-sample (true engine) in 100% of months at 1.0x (100% at 0.5x), but over the following 26 weeks the maxDD is at or below the cap in only 52% (1.0x), 36% (0.75x), 24% (0.5x) of months (live: 48% / 48% / 44%); the median ratio of forward maxDD solved/live is 1.11 (1.0x), 1.14 (0.5x): the maxDD constraint does not carry forward.
* 12R: re-solving monthly changes 7.9 of 14 cells per month on average (sum of absolute changes 18.9 lots; largest single month 48), and the solved table sits on average 25 lots (L1) from the live table. Realised vs target: the search found a table feasible in-sample (true engine) in 100% of months at 1.0x (76% at 0.5x), but over the following 26 weeks the maxDD is at or below the cap in only 52% (1.0x), 44% (0.75x), 24% (0.5x) of months (live: 68% / 60% / 24%); the median ratio of forward maxDD solved/live is 1.29 (1.0x), 1.19 (0.5x): the maxDD constraint does not carry forward.

## 4. Placebo: where does the solved table rank among random tables with the same total lots?

Random tables with exactly 20 base lots (random split of the 20 over the six books, session lots uniform in 0..base, at least one session at the base), kept if feasible (maxDD <= cap on the solve window). `rank` = share of feasible random tables that are AS GOOD or BETTER as the solved table (mean: share with mean >= solved; maxDD: share with maxDD <= solved), so a small mean rank = the solved table beats most random tables.

**Lock off, exact-per-book decomposition (55k, 37k, 6k feasible draws; approximation: books are coupled only through the stack-wide Asia stop cut, decomposition maxDD error sd 3.6% of ALL):**

| solve | cap | feasible draws | in-sample mean: solved vs draws median / 95th | judged window | judged mean rank | judged maxDD rank | draws median mean / maxDD |
|---|---|---|---|---|---|---|---|
| PRE+X | 1.0x | 55008 | 25.8 vs 11.3 / 16.0 (rank 0.000) | L6M | 0.04 | 0.83 | 26.4 / 43 (solved 38.6 / 64) |
| PRE+X | 1.0x | 55008 | 25.8 vs 11.3 / 16.0 (rank 0.000) | HOLD | 0.04 | 0.89 | 24.6 / 69 (solved 36.2 / 102) |
| PRE+X | 0.75x | 37006 | 24.0 vs 11.4 / 15.7 (rank 0.000) | L6M | 0.12 | 0.85 | 25.8 / 40 (solved 33.6 / 59) |
| PRE+X | 0.75x | 37006 | 24.0 vs 11.4 / 15.7 (rank 0.000) | HOLD | 0.08 | 0.93 | 24.0 / 67 (solved 32.2 / 109) |
| PRE+X | 0.5x | 6128 | 22.5 vs 11.9 / 15.5 (rank 0.000) | L6M | 0.00 | 0.79 | 24.4 / 35 (solved 39.0 / 48) |
| PRE+X | 0.5x | 6128 | 22.5 vs 11.9 / 15.5 (rank 0.000) | HOLD | 0.00 | 0.86 | 22.5 / 64 (solved 36.9 / 89) |
| HOLD | 1.0x | 51189 | 58.3 vs 24.8 / 37.0 (rank 0.000) | PRE | 0.03 | 1.00 | 15.8 / 161 (solved 23.5 / 374) |
| HOLD | 1.0x | 51189 | 58.3 vs 24.8 / 37.0 (rank 0.000) | X' | 0.45 | 0.99 | 3.4 / 129 (solved 3.7 / 226) |
| HOLD | 0.75x | 33596 | 57.3 vs 24.3 / 36.1 (rank 0.000) | PRE | 0.00 | 0.86 | 15.1 / 158 (solved 26.8 / 214) |
| HOLD | 0.75x | 33596 | 57.3 vs 24.3 / 36.1 (rank 0.000) | X' | 0.06 | 0.97 | 3.6 / 127 (solved 6.9 / 201) |
| HOLD | 0.5x | 6516 | 50.6 vs 23.6 / 33.8 (rank 0.000) | PRE | 0.01 | 0.99 | 13.2 / 147 (solved 21.3 / 313) |
| HOLD | 0.5x | 6516 | 50.6 vs 23.6 / 33.8 (rank 0.000) | X' | 0.41 | 0.91 | 3.6 / 127 (solved 4.1 / 180) |
| ALL | 1.0x | 55028 | 29.8 vs 14.2 / 19.6 (rank 0.000) | (in-sample) | - | - | - |
| ALL | 0.75x | 37170 | 28.2 vs 14.2 / 19.0 (rank 0.000) | (in-sample) | - | - | - |
| ALL | 0.5x | 5971 | 24.7 vs 14.2 / 17.8 (rank 0.000) | (in-sample) | - | - | - |

**True engine (both lock scenarios; random draws run through the engine, feasible = maxDD <= cap on PRE+X'):**

| lock | cap | feasible / drawn | in-sample mean rank (solved) | L6M mean rank / maxDD rank | HOLD mean rank / maxDD rank | draws median L6M mean / maxDD (solved) | draws median HOLD mean / maxDD (solved) |
|---|---|---|---|---|---|---|---|
| lock off | 1.0x | 274/300 | 0.000 | 0.07 / 0.83 | 0.06 / 0.87 | 26.5 / 43 (38.6 / 64) | 24.8 / 72 (36.2 / 102) |
| lock off | 0.5x | 31/300 | 0.000 | 0.00 / 0.74 | 0.00 / 0.81 | 24.8 / 35 (39.0 / 48) | 22.9 / 64 (36.9 / 89) |
| 12R | 1.0x | 299/400 | 0.003 | 0.16 / 0.38 | 0.14 / 0.84 | 19.6 / 57 (29.7 / 50) | 18.7 / 71 (27.2 / 104) |
| 12R | 0.5x | 25/400 | 0.880 | 0.00 / 0.28 | 0.00 / 0.08 | 18.9 / 55 (29.3 / 44) | 17.9 / 67 (28.7 / 44) |

**Walk-forward placebo (lock off, decomposition; 300 chains, each month a random table feasible in that month's solve window at the same cap, same total lots):**

| cap | placebo chain mean (median) | placebo chain maxDD (median) | solved chain mean / maxDD | mean rank | maxDD rank | Calmar rank | half-way chain mean / maxDD | maxDD rank | distance-matched placebo (same L1 distance to live per month) mean / maxDD | solved mean rank | maxDD rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1.0x | 19.0 | 160 | 27.8 / 233 | 0.00 | 0.90 | 0.51 | 29.4 / 192 | 0.76 | 23.6 / 200 | 0.01 | 0.77 |
| 0.5x | 17.4 | 143 | 25.7 / 173 | 0.00 | 0.76 | 0.26 | 28.7 / 127 | 0.30 | 21.9 / 164 | 0.00 | 0.69 |

Reading. Against RANDOM tables with the same 20 lots the solved tables rank at the top on mean (they are not random: they follow the books that earned money), which is a weak test because most random tables are poor allocations. The relevant comparison is the live table (hand-halved, balanced): the solved table does not beat it out of sample (section 3), and on maxDD out of sample the solved table is worse than most random feasible tables with the lock off (maxDD rank 0.74-1.00 in the fixed protocol, 0.69-0.90 in the walk-forward; a high rank = most random tables have a smaller drawdown), mixed under 12R (0.08-0.84; the 12R 0.5x PRE+X' solve is itself 1% infeasible, hence its in-sample rank 0.88). The solver buys in-sample mean by loading P6 and K6 (the books with the best 2023-26 sessions) and that is exactly what does not survive.

## 5. Overfitting statement, in-sample vs out-of-sample, shrinkage, effective N

* **What is being fitted.** 14 integer variables (cells) on one stack, with a budget of 20 and a drawdown cap that is binding on a single episode: the live composite's ALL maxDD of 241k is one episode of 7 weeks (weeks labelled 202434..202440, PRE), and its L6M maxDD of 23k is 1 week(s) (weeks ending 202543). A maxDD cap therefore constrains the lots in whatever the one or two worst weeks of the window were, and leaves everything else free for the mean: the optimum loads the sessions that earned money in the rest of the window.
* **Effective N.** Walk-forward solve window = 26-27 weekly observations (26 label weeks) for 14 free integers = under 2 weeks per variable; the autocorrelation-adjusted N of those windows has median 19 weeks, and the binding drawdown episode of the live composite in those windows has median 4 (max 7) weeks. The fixed solves use 118 weeks (PRE+X', adjusted N 71, binding episode 9 weeks), 32 weeks (HOLD, adjusted N 28, episode 3 weeks) and 149 (ALL, adjusted N 87, episode 7 weeks). The effective number of independent drawdown episodes behind any cap is about 1 (PRE) in the long windows and 1 (L6M) in the short ones. The weekly SE of the paired OOS delta gives the MDE column: the out-of-sample delta vs live is inside its MDE in every row except: 12R H0.75 -11.0 vs MDE 8.6; 12R S0.5 -13.2 vs MDE 9.8 (all negative)
* **In-sample vs out-of-sample gap (lock off, cap 1.0x, $k/wk).** Walk-forward: in-sample uplift over live on the solver's own windows +16.7, out-of-sample -0.7 (gap 17.4); with the half-way table +7.6 in-sample, 1.0 out-of-sample. Fixed PRE+X' solve: in-sample +8.1, out-of-sample L6M -2.6, HOLD -2.3; reverse (solved on HOLD): in-sample +19.7, out-of-sample PRE 0.4, X' -4.2. Under 12R: walk-forward in-sample +12.3, out-of-sample -6.2.
* **The in-sample optimum is biased upward by construction** (maximum over ~10^12 integer tables of a noisy objective, plus the selection of the table that exploits the single worst week): the in-sample mean is not an estimate of anything. The honest numbers are the out-of-sample rows. The 'IS - OOS gap' column in section 3 is the size of the bias in this study.
* **Shrinkage toward live (average of solved and live, half up).** Out-of-sample (walk-forward, lock off) it keeps the mean (29.4 vs live 28.4, delta 1.0, MDE 6.4) and keeps most of the in-sample maxDD gain (192 vs 241); the 0.5x half-way table: 127, worst-20 -879 vs -989. This is a shrinkage the data cannot validate further: the improvement in maxDD out-of-sample is one episode (PRE). Under 12R it is inconsistent across caps (section 3).

## 6. Cost of being wrong: if the regime of 2024-25 returns (PRE and X' maxDD and worst-20 for every lot table)

Tables solved on the RECENT windows only (HOLD, latest 6 months to 2026-02-06) are the ones a monthly re-solve would put live now; PRE and X' are completely out of sample for them. The ALL- and PRE+X'-solved tables have PRE/X' in their own fit (in-sample lines, shown for contrast).

| lock | table (solve window) | PRE maxDD | PRE worst-20 | PRE mean | X' maxDD | X' worst-20 | X' mean | L3M maxDD | L6M maxDD |
|---|---|---|---|---|---|---|---|---|---|
| lock off | live | 241 | -875 | 23.1 | 121 | -420 | 8.0 | 21 | 23 |
| lock off | 1.0x (latest 6M, OUT of sample for PRE/X') | 370 | -1259 | 22.0 | 217 | -635 | 3.3 | 27 | 16 |
| lock off | 1.0x half-way (latest 6M, OUT of sample for PRE/X') | 245 | -1134 | 22.8 | 188 | -543 | 5.8 | 37 | 24 |
| lock off | 0.75x (latest 6M, OUT of sample for PRE/X') | 246 | -1035 | 23.8 | 179 | -581 | 1.8 | 12 | 13 |
| lock off | 0.75x half-way (latest 6M, OUT of sample for PRE/X') | 200 | -935 | 21.2 | 139 | -449 | 3.9 | 36 | 23 |
| lock off | 0.5x (latest 6M, OUT of sample for PRE/X') | 321 | -1155 | 21.0 | 218 | -638 | 1.3 | 29 | 4 |
| lock off | 0.5x half-way (latest 6M, OUT of sample for PRE/X') | 223 | -1085 | 21.1 | 177 | -526 | 4.0 | 45 | 17 |
| lock off | 1.0x (HOLD, OUT of sample for PRE/X') | 374 | -1152 | 23.5 | 226 | -609 | 3.7 | 29 | 44 |
| lock off | 1.0x half-way (HOLD, OUT of sample for PRE/X') | 288 | -1074 | 22.4 | 183 | -532 | 6.3 | 36 | 34 |
| lock off | 0.75x (HOLD, OUT of sample for PRE/X') | 214 | -1011 | 26.8 | 201 | -599 | 6.9 | 25 | 28 |
| lock off | 0.75x half-way (HOLD, OUT of sample for PRE/X') | 202 | -991 | 23.9 | 175 | -546 | 6.9 | 20 | 21 |
| lock off | 0.5x (HOLD, OUT of sample for PRE/X') | 313 | -954 | 21.3 | 180 | -524 | 4.1 | 22 | 9 |
| lock off | 0.5x half-way (HOLD, OUT of sample for PRE/X') | 226 | -893 | 25.1 | 174 | -495 | 6.0 | 25 | 15 |
| lock off | 1.0x (PRE+X', in-sample for PRE/X') | 220 | -848 | 35.9 | 149 | -592 | 7.9 | 84 | 64 |
| lock off | 1.0x half-way (PRE+X', in-sample for PRE/X') | 164 | -767 | 27.4 | 167 | -607 | 6.5 | 54 | 34 |
| lock off | 0.75x (PRE+X', in-sample for PRE/X') | 158 | -695 | 34.7 | 131 | -541 | 5.2 | 59 | 59 |
| lock off | 0.75x half-way (PRE+X', in-sample for PRE/X') | 188 | -762 | 28.6 | 141 | -532 | 5.2 | 34 | 34 |
| lock off | 0.5x (PRE+X', in-sample for PRE/X') | 116 | -613 | 29.8 | 108 | -526 | 9.6 | 75 | 48 |
| lock off | 0.5x half-way (PRE+X', in-sample for PRE/X') | 186 | -789 | 24.5 | 121 | -496 | 8.1 | 58 | 29 |
| lock off | 1.0x (ALL, in-sample) | 234 | -997 | 31.0 | 237 | -665 | 8.8 | 46 | 46 |
| lock off | 1.0x half-way (ALL, in-sample) | 231 | -934 | 27.9 | 181 | -561 | 7.2 | 29 | 30 |
| lock off | 0.75x (ALL, in-sample) | 178 | -845 | 32.5 | 124 | -608 | 8.4 | 80 | 58 |
| lock off | 0.75x half-way (ALL, in-sample) | 166 | -819 | 26.2 | 136 | -550 | 6.5 | 44 | 34 |
| lock off | 0.5x (ALL, in-sample) | 118 | -618 | 27.5 | 97 | -440 | 10.2 | 91 | 48 |
| lock off | 0.5x half-way (ALL, in-sample) | 132 | -760 | 23.3 | 122 | -482 | 6.4 | 52 | 27 |
| 12R | live | 233 | -608 | 15.1 | 120 | -468 | 1.0 | 27 | 27 |
| 12R | 1.0x (latest 6M, OUT of sample for PRE/X') | 186 | -861 | 13.9 | 214 | -640 | 0.1 | 33 | 24 |
| 12R | 1.0x half-way (latest 6M, OUT of sample for PRE/X') | 214 | -837 | 13.5 | 196 | -607 | 0.2 | 42 | 27 |
| 12R | 0.75x (latest 6M, OUT of sample for PRE/X') | 155 | -575 | 15.0 | 144 | -445 | 0.4 | 35 | 20 |
| 12R | 0.75x half-way (latest 6M, OUT of sample for PRE/X') | 233 | -608 | 15.1 | 120 | -468 | 1.0 | 27 | 27 |
| 12R | 0.5x (latest 6M, OUT of sample for PRE/X') | 138 | -545 | 14.6 | 153 | -450 | 1.2 | 46 | 18 |
| 12R | 0.5x half-way (latest 6M, OUT of sample for PRE/X') | 224 | -600 | 14.0 | 162 | -448 | 2.1 | 21 | 32 |
| 12R | 1.0x (HOLD, OUT of sample for PRE/X') | 211 | -619 | 11.9 | 388 | -533 | -7.1 | 35 | 35 |
| 12R | 1.0x half-way (HOLD, OUT of sample for PRE/X') | 208 | -648 | 11.3 | 161 | -475 | -1.3 | 36 | 36 |
| 12R | 0.75x (HOLD, OUT of sample for PRE/X') | 130 | -532 | 14.7 | 148 | -437 | -0.4 | 34 | 18 |
| 12R | 0.75x half-way (HOLD, OUT of sample for PRE/X') | 237 | -566 | 15.7 | 151 | -459 | 0.8 | 26 | 26 |
| 12R | 0.5x (HOLD, OUT of sample for PRE/X') | 130 | -532 | 14.7 | 148 | -437 | -0.4 | 34 | 18 |
| 12R | 0.5x half-way (HOLD, OUT of sample for PRE/X') | 237 | -566 | 15.7 | 151 | -459 | 0.8 | 26 | 26 |
| 12R | 1.0x (PRE+X', in-sample for PRE/X') | 182 | -751 | 20.2 | 120 | -552 | 6.0 | 48 | 50 |
| 12R | 1.0x half-way (PRE+X', in-sample for PRE/X') | 143 | -692 | 19.5 | 106 | -541 | 3.4 | 56 | 57 |
| 12R | 0.75x (PRE+X', in-sample for PRE/X') | 116 | -616 | 15.5 | 118 | -483 | 1.8 | 33 | 33 |
| 12R | 0.75x half-way (PRE+X', in-sample for PRE/X') | 110 | -646 | 16.3 | 132 | -490 | 3.0 | 34 | 34 |
| 12R | 0.5x (PRE+X', in-sample for PRE/X') | 115 | -526 | 7.6 | 117 | -445 | 0.7 | 25 | 44 |
| 12R | 0.5x half-way (PRE+X', in-sample for PRE/X') | 139 | -578 | 11.4 | 117 | -464 | -0.4 | 24 | 23 |
| 12R | 1.0x (ALL, in-sample) | 173 | -740 | 19.5 | 165 | -556 | 3.2 | 28 | 28 |
| 12R | 1.0x half-way (ALL, in-sample) | 183 | -783 | 17.7 | 170 | -560 | 0.7 | 32 | 32 |
| 12R | 0.75x (ALL, in-sample) | 147 | -686 | 19.7 | 93 | -466 | 5.9 | 36 | 36 |
| 12R | 0.75x half-way (ALL, in-sample) | 136 | -696 | 19.5 | 98 | -494 | 5.0 | 36 | 36 |
| 12R | 0.5x (ALL, in-sample) | 115 | -526 | 7.6 | 117 | -445 | 0.7 | 25 | 44 |
| 12R | 0.5x half-way (ALL, in-sample) | 139 | -578 | 11.4 | 117 | -464 | -0.4 | 24 | 23 |

Reading. A table solved on the recent windows and then hit by a 2024-25 regime: lock off, latest-6M solve, PRE maxDD 370 / 246 / 321 (1.0x / 0.75x / 0.5x) vs live 241; HOLD-solved: 374 / 214 / 313. The cap that looks tight on the recent window (a single week in L6M) does not bound the drawdown of a different regime. Conversely the tables solved on ALL or PRE+X' (which contain the PRE episode) have large L3M/L6M drawdowns (91k L3M for the ALL 0.5x table vs live 21k): a cap on the long window is not a cap on the recent one.

## 7. Method, approximations, integrity

* **Search.** The engine is not linear in lots: integer half-up min-1 ER rounding, governors (BookR) on the session planned lot, the per-book day/week locks, the stack-wide Asia stop cut (a stop in one book cuts the open rows of the others), and, in the 12R scenario, the combined lock whose threshold is 12 x R_K6 with R_K6 following the K6 base lot. I therefore used (1) a PROPOSAL surrogate: lock off = exact per-book enumeration of every session-lot combination (K6 6^4, P6 13^3, U6 9^2, H6 9^2, M6 6^2, A6 4 = 3,695 combos, 2,197 engine runs) summed over books (books are independent except through the Asia stop cut; the sum matches the true engine to a mean error of ~$0.3k/wk and a maxDD error with sd 3.6% of ALL); lock 12R = live series + sum of single-cell deviations (poor: the true maxDD missed the cap by up to 90k); coordinate ascent with 1-cell and 2-cell moves, 60-200 restarts; (2) a bias-corrected loop: the proposal is run through the TRUE engine, the effective cap is shifted by the observed true-minus-cap gap, 6 iterations; (3) true-engine +-1 neighbour local search from each key's own best until no neighbour improves (6 stages, ~9,500 true engine runs in the cache); (4) the reported table of each key = the best true penalised score (mean minus 100 x excess maxDD) among ITS OWN proposals and neighbours only, so no table proposed from another window's data can be selected (no look-ahead through the shared cache). Every number in the tables is a true engine run; the surrogate error is stated, not hidden. 12R keys are the least reliable (local optimum, a few infeasible by 1-20% as marked).
* **Walk-forward** uses the tables chosen on windows that end before the month; chained monthly series are cut from each table's full-history run (a week lock that straddles a month boundary is evaluated under the table of the day it starts; the engine is run on the whole history so open positions at the boundary are the table's own).
* **Placebo** as in section 4; lock-off placebo draws use the decomposition (stated), the PRE+X' placebo for both locks re-runs the draws through the true engine.
* **Integrity.** Masks capped 20260206, no post-cap file opened, UNTOUCHED never read. The recent window (L6M/HOLD) is looked at once per protocol (fixed PRE+X' solve -> L6M/HOLD; reverse HOLD -> PRE/X'); the ALL-sample tables and the walk-forward windows use recent data in the fit and are labelled in-sample. The L6M as-is maxDD of the composite is a single week; the optimum under a maxDD constraint is dominated by that one week and by the single PRE episode. No PASS claim, no significance claim; nothing goes live. Prereg sha above; dead_lookup + append_cells after scoring (DEAD_CELLS rows E1LOTS).

## 8. Recommendation (Shadow only; the user decides lots)

1. Keep the live table. No solved table beats it out of sample on the mean (lock off: all inside MDE; 12R: lower, two rows beyond MDE) and the solved tables do not reduce the tail (worst-20, SD) out of sample; re-solving monthly only churns lots.
2. No lot table is recommended for Shadow. The only variant with an out-of-sample maxDD gain in the walk-forward is the monthly half-way table (lock off), and the fixed-table protocol DISAGREES (the PRE+X' half-way tables have a larger L6M maxDD than live at all three caps and a larger HOLD maxDD at two of three, section 2): two protocols, two answers = noise-level evidence. If the user wants a paper row anyway for learning, log the monthly half-way 0.5x table (lock off) beside the live book with no real lots and judge it on forward weeks only.
3. With the combined 12R lock ON, the re-solved tables are worse than live on the mean out of sample at every cap (walk-forward dMean -6.2 / -9.4 / -13.2 vs MDE 11.0 / 10.4 / 9.8) and the maxDD result is erratic; the 12R surrogate is also the weakest. Do not size lots to a drawdown cap while the 12R lock is on.
