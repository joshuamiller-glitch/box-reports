# DS3_P7_CUT - the most aggressive P7 state cut that still holds (ROLL-EXCL; PRE-PROOF; shadow only, nothing goes live)
**Labels: ROLL-EXCL (the 33 engine roll-artifact trades, key (book, entry second), 13 of them P7, are removed from every window, every series and the exported per-trade tables; SZ_BASE_PROOF.md section 9). Base S1b (tick bar close). First-order screen = P7 trades of S1b-NOCUT + exact 1-s MBP-10 state arrays; EXACT = replica engine re-run with only the P7 cut cell changed (other books = S1-COMB cells). Windows as of 2026-11-09, carrying week dropped from MEANS only (never before maxDD). Prereg sha256 9ca3a614122c5586 (DECISIONS.md). No PASS claims.**

## 1. Verdict
**Plain sentence.** The most aggressive P7 cut that does not raise L6M or PRE maxDD vs v2 is **none of the cells that could be tested exactly: the v2 line itself (45 pts / 5x / win 5 / persist 10, no newMae)**. The one faster cell that lowers exact L6M maxDD, fixed 40 pts / 5x / win 5 / persist 3 / noMae (5 pts earlier arm, persistence 3 instead of 10), changes the L6M stack mean by +3.6k $/wk (P7 alone +4.3k) and cuts L6M stack maxDD 17% (P7 alone 51%), but raises exact PRE stack maxDD by 25% (P7 alone 62%) with PRE mean -1.1k $/wk, so it does not hold. Cuts of last night's 4 stops (11-08/09): n/a, that night's rows are not on the box (0 evaluable); on the frozen week it would have cut 24 of 53 P7 trades (21 of the 24 live-cut trades; 7 of them were target-bracket trades), -56k vs the hold-to-bracket proxy (v2 -33k, old cell -14k).

1. Exact (ROLL-EXCL, S1b engine, only the P7 cut changed): of five candidate cells run on the L6M months, only 40/5x/w5/p3 lowers L6M maxDD vs v2; 35/5x/p3 (+10%), 25/20x/p3 (+28%) and the OLD live cell (+81%, mean -4.4k) raise it. 40/5x/w5/p3 then fails PRE (+25%). 45/5x/w5/p5 and V2 lots-scaled 25/5x/p4 were not completed (killed for time). Exact PRE exists only for v2 and 40/5x/p3.
2. The first-order screen (13,680 cells x 4 scopes, section 3-4) ranked the faster cells as large drawdown cutters; the exact engine reverses that for P7 (earlier cuts free the book and day lock for re-entries). First-order drawdown ranking is NOT usable for P7; the first-order table is shown only because the user asked for the full grid.
3. Nulls do not support any cell: family p over the grid is not significant, purged monthly walk-forward re-selection loses to fixed v2 (+17% / +41% maxDD), the held-out frozen live week loses to hold-to-bracket for every cut cell, the plain placebo does not discriminate.
4. S1b-COMB as run (exact L6M: stack mean 23.3k, maxDD 79.9k; P7 alone 14.8k / 91.2k) uses the asia override 50/5x/w3/p3/newMae V1 plus v2 elsewhere and beats the pooled v2 line on exact L6M (PRE not run). This is the only exact-confirmed faster P7 configuration, in L6M only. NOT proposed: no PRE exact result, in-sample selection.
5. MORNING.md top: nothing qualifies (no faster cell lowers drawdown at equal or better mean in BOTH exact L6M and PRE). Shadow only; the v2 line stays.

## 2. EXACT engine rows (reference = exact v2 line, P7 cell 45/5x/w5/p10 noMae in every session; S1b-COMB as run uses the asia override 50/5x/w3/p3/newMae V1 and is shown separately)
Exact windows are reported only when every month of the window was run (L6M = 202605-202610; PRE = 202402-202506). Stack = all 7 books; P7 = the P7 book alone. dd cut % = (v2 maxDD - cell maxDD) / v2 maxDD, positive = lower drawdown.
| cell | window | months run | stack mean $/wk | stack maxDD | stack dd cut % | stack mean vs v2 | stack Ulcer | stack worst-20 | P7 mean | P7 maxDD | P7 dd cut % | P7 mean vs v2 | P7 cuts on the 13 roll trades (first-order) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| v2 (45/5x/w5/p10 noMae, fixed) | L6M | 6 | 20393 | 95245 | 0 | 0 | 40845 | 89055 | 11807 | 84540 | 0 | 0 | 1 |
| v2 (45/5x/w5/p10 noMae, fixed) | PRE | 17 | 13438 | 106877 | 0 | 0 | 32254 | -653766 | 5752 | 71013 | 0 | 0 | 1 |
| OLD live (30/30x/w5/p1 newMae, fixed) | L6M | 6 | 16745 | 172620 | -81.2 | -4424 | 64857 | -7507 | 6989 | 216619 | -156.2 | -4534 | 0 |
| OLD live (30/30x/w5/p1 newMae, fixed) | PRE | 0 of 17 | not complete | | | | | | | | | | 0 |
| X1 fixed 35/5x/w5/p3 noMae | L6M | 6 | 23255 | 104923 | -10.2 | +2086 | 40366 | 132086 | 12629 | 121985 | -44.3 | +1105 | 1 |
| X1 fixed 35/5x/w5/p3 noMae | PRE | 0 of 17 | not complete | | | | | | | | | | 1 |
| X4 fixed 25/20x/w5/p3 noMae | L6M | 6 | 15518 | 121696 | -27.8 | -5650 | 46743 | 11874 | 6722 | 140009 | -65.6 | -4801 | 0 |
| X4 fixed 25/20x/w5/p3 noMae | PRE | 0 of 17 | not complete | | | | | | | | | | 0 |
| X5 fixed 40/5x/w5/p3 noMae | L6M | 6 | 24722 | 79107 | +16.9 | +3554 | 30531 | 212819 | 15823 | 41005 | +51.5 | +4300 | 1 |
| X5 fixed 40/5x/w5/p3 noMae | PRE | 17 | 13753 | 133779 | -25.2 | -1056 | 38919 | -643992 | 5279 | 114902 | -61.8 | -1201 | 1 |
| X6 fixed 45/5x/w5/p5 noMae | L6M | 2 of 6 | not complete | | | | | | | | | | 1 |
| X6 fixed 45/5x/w5/p5 noMae | PRE | 0 of 17 | not complete | | | | | | | | | | 1 |
| X2 V2 lots-scaled 25/5x/w5/p4 noMae | L6M | 0 of 6 | not complete | | | | | | | | | | 1 |
| X2 V2 lots-scaled 25/5x/w5/p4 noMae | PRE | 0 of 17 | not complete | | | | | | | | | | 1 |

## 3. First-order screen: reference rows by window (P7 alone and stack; dd = maxDD $, mean $/wk, worst-20 = sum of the 20 worst weeks, Ulcer)
First-order caveat: re-entries, locks and day caps after an earlier cut are NOT re-simulated; the exact rows in section 2 show the first-order drawdown ranking is NOT predictive for P7 (e.g. first-order says 35/5x/p3 cuts L6M stack maxDD 26% vs v2, exact says +10%).
| row | scope | L1M dd / mean | L2M dd / mean | L3M dd / mean | L6M dd / mean | HOLD dd / mean | MID dd / mean | PRE dd / mean | X' dd / mean |
|---|---|---|---|---|---|---|---|---|---|
| v2 (45/5x/w5/p10 noMae, fixed) | P7 alone | 53k / -17.7k | 53k / 12.2k | 53k / 7.1k | 152k / 7.3k | 152k / 5.5k | 74k / 2.8k | 121k / 4.8k | 139k / -0.4k |
| v2 (45/5x/w5/p10 noMae, fixed) | stack | 75k / -25.1k | 75k / 25.6k | 85k / 12.0k | 117k / 16.9k | 117k / 11.3k | 103k / 9.0k | 123k / 13.0k | 136k / 1.5k |
| OLD live (30/30x/w5/p1 newMae, fixed) | P7 alone | 65k / 12.2k | 65k / 21.6k | 98k / 9.4k | 199k / 9.5k | 199k / 7.4k | 59k / 7.2k | 103k / 5.9k | 148k / -1.4k |
| OLD live (30/30x/w5/p1 newMae, fixed) | stack | 87k / 17.1k | 87k / 36.4k | 130k / 15.5k | 165k / 19.9k | 165k / 13.3k | 93k / 12.8k | 108k / 14.2k | 139k / 0.8k |
| never cut | P7 alone | 74k / 10.5k | 74k / 23.3k | 79k / 11.2k | 199k / 6.8k | 199k / 5.5k | 79k / 8.1k | 117k / 4.6k | 149k / -1.4k |
| never cut | stack | 96k / 15.4k | 96k / 38.2k | 115k / 17.5k | 164k / 16.1k | 164k / 11.3k | 110k / 12.6k | 126k / 12.8k | 139k / 0.8k |
| X1 fixed 35/5x/w5/p3 noMae | P7 alone | 47k / -4.5k | 47k / 4.1k | 48k / 1.0k | 92k / 10.9k | 92k / 7.7k | 41k / 7.3k | 94k / 2.7k | 137k / -0.9k |
| X1 fixed 35/5x/w5/p3 noMae | stack | 67k / 2.4k | 67k / 14.3k | 80k / 4.2k | 87k / 19.9k | 94k / 12.9k | 94k / 11.8k | 86k / 10.7k | 140k / 0.7k |
| X4 fixed 25/20x/w5/p3 noMae | P7 alone | 29k / -8.9k | 29k / 11.9k | 39k / 7.9k | 96k / 12.8k | 96k / 8.2k | 45k / 14.8k | 106k / 5.2k | 111k / 0.4k |
| X4 fixed 25/20x/w5/p3 noMae | stack | 49k / -16.3k | 49k / 22.2k | 72k / 11.1k | 84k / 21.8k | 92k / 13.8k | 73k / 20.3k | 88k / 13.4k | 122k / 1.5k |
| X5 fixed 40/5x/w5/p3 noMae | P7 alone | 52k / -4.6k | 52k / 13.0k | 52k / 6.4k | 101k / 12.5k | 101k / 9.6k | 40k / 12.1k | 89k / 3.9k | 136k / -1.2k |
| X5 fixed 40/5x/w5/p3 noMae | stack | 61k / 2.3k | 61k / 28.7k | 84k / 13.2k | 95k / 22.1k | 95k / 15.4k | 93k / 17.7k | 107k / 12.4k | 144k / 0.9k |
| X6 fixed 45/5x/w5/p5 noMae | P7 alone | 61k / 14.4k | 61k / 21.0k | 71k / 8.6k | 171k / 11.2k | 171k / 7.2k | 52k / 9.5k | 117k / 4.2k | 137k / -0.0k |
| X6 fixed 45/5x/w5/p5 noMae | stack | 83k / 19.2k | 83k / 35.8k | 111k / 14.8k | 136k / 21.7k | 136k / 13.0k | 98k / 14.0k | 125k / 12.5k | 137k / 1.9k |

First-order worst-20 weeks / Ulcer, L6M and PRE (stack): v2: w20 16k/-665k, Ulcer 49k/38k; OLD: w20 -33k/-654k, Ulcer 62k/33k; X1: w20 139k/-603k, Ulcer 35k/33k; X4: w20 161k/-652k, Ulcer 32k/34k; X5: w20 101k/-669k, Ulcer 38k/38k; X6: w20 -3k/-715k, Ulcer 53k/42k

## 4. Ranked table (first-order, ROBUST-gated: stack AND P7-alone maxDD <= v2 in L6M, PRE, HOLD and X'; own-null p <= 0.20), drawdown first = min(stack dd cut L6M, PRE), mean tie-break; UNRELIABLE for P7 per section 2 - use it only to choose exact candidates
7090 of 54720 cells are ROBUST-gated; 3711 of those have own-null p <= 0.20. Columns: dd cut % (stack) L6M/PRE/HOLD/X'; stack mean change vs v2 $/wk L6M/PRE; P7-alone dd cut % L6M/PRE; cuts = trades cut of 4,682.
| # | cell (arm spec A / MULT / win / persist / newMae) | scope | eff arm (median pt) | cuts | stack dd cut % L6M/PRE/HOLD/X' | stack mean chg L6M/PRE | P7 dd cut % L6M/PRE | own-null p |
|---|---|---|---|---|---|---|---|---|
| 1 | USD $2000 / 3x / w2 / p4 / newMae | pooled | 25 | 2279 | +43/+42/+21/+40 | +3135/-3602 | +73/+37 | 0.02 |
| 2 | V1 25 / 20x / w10 / p1 / newMae | pooled | 25 | 2687 | +45/+39/+4/+51 | -417/-3747 | +48/+11 | 0.05 |
| 3 | fixed 25 / 5x / w2 / p3 / noMae | pooled | 25 | 2742 | +37/+36/+9/+25 | +448/-3903 | +50/+2 | 0.17 |
| 4 | V1 25 / 5x / w3 / p4 / newMae | pooled | 25 | 2413 | +38/+35/+12/+38 | +5435/-2786 | +67/+21 | 0.02 |
| 5 | V1 25 / 3x / w2 / p4 / newMae | pooled | 25 | 2310 | +34/+40/+18/+23 | +4871/-2617 | +69/+37 | 0.02 |
| 6 | fixed 25 / 20x / w7 / p4 / noMae | pooled | 25 | 2265 | +43/+32/+11/+7 | +4517/-1682 | +53/+12 | 0.20 |
| 7 | V1 30 / 10x / w7 / p5 / newMae | pooled | 30 | 2576 | +31/+38/+3/+49 | -11/-4710 | +43/+2 | 0.10 |
| 8 | fixed 25 / 10x / w5 / p5 / newMae | pooled | 25 | 2405 | +33/+31/+8/+8 | +4185/-2839 | +61/+28 | 0.07 |
| 9 | V2 25 / 15x / w6 / p2 / newMae | pooled | 25 | 2503 | +31/+31/+2/+5 | +1854/-2729 | +47/+7 | 0.02 |
| 10 | fixed 30 / 10x / w2 / p1 / noMae | pooled | 30 | 2535 | +35/+30/+15/+21 | +4383/-1329 | +46/+20 | 0.05 |
| 11 | USD $2000 / 8x / w3 / p4 / newMae | pooled | 25 | 1366 | +30/+31/+21/+14 | +3172/-1610 | +56/+45 | 0.02 |
| 12 | fixed 25 / 20x / w7 / p5 / noMae | pooled | 25 | 2096 | +34/+30/+15/+21 | +3994/-2463 | +54/+18 | 0.12 |
| 13 | USD $2000 / 20x / w10 / p4 / newMae | pooled | 25 | 2359 | +47/+30/+6/+22 | +167/-4691 | +61/+6 | 0.07 |
| 14 | fixed 30 / 8x / w2 / p2 / noMae | pooled | 30 | 2533 | +34/+30/+21/+31 | +3057/-1517 | +52/+19 | 0.05 |
| 15 | fixed 25 / 20x / w6 / p4 / noMae | pooled | 25 | 1914 | +33/+30/+20/+18 | +3812/-1376 | +40/+27 | 0.10 |
| 16 | V1 35 / 3x / w6 / p5 / newMae | pooled | 35 | 2526 | +32/+30/+16/+31 | +2792/-4052 | +64/+1 | 0.05 |
| 17 | V1 35 / 10x / w3 / p1 / newMae | pooled | 35 | 2245 | +33/+30/+2/+24 | +4744/-3234 | +65/+34 | 0.02 |
| 18 | fixed 25 / 5x / w4 / p5 / newMae | pooled | 25 | 2743 | +30/+34/+12/+28 | +670/-4439 | +51/+4 | 0.10 |
| 19 | fixed 25 / 30x / w10 / p3 / newMae | pooled | 25 | 1483 | +30/+29/+11/+8 | +4753/-768 | +44/+17 | 0.02 |
| 20 | V1 35 / 8x / w3 / p2 / newMae | pooled | 35 | 2274 | +29/+30/+1/+14 | +4941/-2348 | +57/+11 | 0.02 |

Aggressiveness ladder (most aggressive = lowest effective arm, then most cuts; ROBUST-gated, own p <= 0.20), best by drawdown per arm level:
| eff arm | best cell | cuts | stack dd cut L6M/PRE | stack mean chg L6M/PRE |
|---|---|---|---|---|
| 25 | D 2000/3x/w2/p4/M | 2279 | +43/+42 | +3135/-3602 |
| 30 | V1 30/10x/w7/p5/M | 2576 | +31/+38 | -11/-4710 |
| 35 | V1 35/3x/w6/p5/M | 2526 | +32/+30 | +2792/-4052 |
| 38 | D 3000/8x/w4/p5/- | 2124 | +27/+27 | +6419/-2804 |
| 40 | V1 40/5x/w5/p3/- | 2425 | +29/+28 | +6764/-3097 |
| 45 | V1 45/20x/w9/p3/- | 1873 | +22/+22 | +3062/-325 |
| 50 | D 4000/5x/w3/p3/M | 2129 | +24/+24 | +4324/-2027 |

Per entry session (other sessions stay at v2), best ROBUST cell by drawdown first-order:
| session | best cell | cuts | stack dd cut L6M/PRE | stack mean chg L6M/PRE |
|---|---|---|---|---|
| pooled | D 2000/3x/w2/p4/M | 2279 | +43/+42 | +3135/-3602 |
| asia | F 30/3x/w3/p5/M | 1140 | +23/+24 | +4340/-620 |
| london | V2 45/8x/w4/p2/- | 715 | +14/+13 | +1720/-84 |
| nyam | V1 25/20x/w6/p2/M | 364 | +25/+21 | +3927/-2019 |

First-order heat, pooled fixed arm, noMae, win 5: stack min(dd cut L6M, PRE) % by ARM x MULT at persist 3 (positive = both windows cut):
| ARM \ MULT | 3 | 5 | 8 | 10 | 15 | 20 | 30 | 40 |
|---|---|---|---|---|---|---|---|---|
| 25 | +24 | +24 | +26 | +30 | +32 | +28 | -19 | -39 |
| 30 | +36 | +36 | +31 | +30 | +19 | +14 | -29 | -39 |
| 35 | +26 | +26 | +26 | +25 | +9 | +13 | -34 | -39 |
| 40 | +13 | +13 | +11 | +15 | +4 | -0 | -42 | -39 |
| 45 | -7 | -8 | -12 | -10 | -16 | -12 | -40 | -39 |

## 5. Nulls and walk-forward
- Family null over the full P7 grid (54,720 cell x scope; 40 worlds, each circularly shifts the pulled-support series within every trade so the state condition is decoupled from price; statistic = max over cells of min(stack dd cut L6M, PRE) vs the real v2): null mean 48.9, max 52.0; observed best 51.7; family p = 0.049. The observed best cells are 25-pt cells with large mean loss; most of the dd cut is available from the ARM condition alone.
- Placebo (random same-count cuts at random seconds beyond the arm, 100 draws, pre ROLL-EXCL shortlist of 950 cells): every cell p = 0.0099 (the floor); random cuts raise maxDD by 97% (L6M) / 153% (PRE) on average, so this placebo does not discriminate; the shifted-pulled worlds above are the informative null (own-null p column).
- Purged monthly walk-forward over 2024-01..2026-10 (7-day embargo, 26-week training, whole 54,720-cell set per month; stack): v2 mean 13619 / maxDD 123101; pick = lowest training maxDD: mean 8544 / maxDD 144491; pick = no-worse-than-v2 training maxDD, highest training mean: mean 13893 / maxDD 173069. Re-selecting cells month by month LOSES to the fixed v2 line on drawdown (+17% / +41%): no selection procedure here is supported out of sample.
- Older-windows-select / newer-windows-test (first-order, 54,720 cells): cells that do not raise PRE and X' maxDD (stack and P7-alone) also do not raise L6M and HOLD in 63% of cases against a 31% base rate.

## 6. Held-out live week (frozen file P7 rows only: 53 P7 trades, 24 live cuts = 13 PolicyCut + 11 ThL2Cut, 0 stops, actual P7 net $86,010; bracket proxy = stop signal -+ 60 / target fill -+ 60 on the 1-s arrays, $114,722). The old per-print live cuts are NOT ground truth. The night of 11-08/09 (4 stops) is NOT on the box; the 7 later P7 rows of the unfrozen file have no state arrays (label day 11-06): not scored.
| cell | cuts of 53 | cuts on the 24 live-cut trades | cuts on trades whose bracket was a target | cuts on stop-bracket trades | week net if cell cuts, else bracket $ | vs bracket proxy | vs actual on the 24 |
|---|---|---|---|---|---|---|---|
| v2 (45/5x/w5/p10 noMae, fixed) | 17 | 16 | 4 | 13 | 81440 | -33282 | -21884 |
| OLD live (30/30x/w5/p1 newMae, fixed) | 9 | 8 | 2 | 7 | 100672 | -14050 | -4467 |
| X1 fixed 35/5x/w5/p3 noMae | 28 | 24 | 10 | 18 | 36790 | -77931 | -8733 |
| X4 fixed 25/20x/w5/p3 noMae | 27 | 23 | 10 | 17 | 38914 | -75808 | 3511 |
| X5 fixed 40/5x/w5/p3 noMae | 24 | 21 | 7 | 17 | 58879 | -55843 | -18017 |
| X6 fixed 45/5x/w5/p5 noMae | 20 | 19 | 4 | 16 | 86637 | -28085 | -22752 |
Every cut cell loses to hold-to-bracket in this week (6 of the 24 live cuts were followed by a target). Per-trade table of the 24 live-cut trades for v2 and X5 (second after entry @ mid price at the cut second+1): /mnt/l2/l2vast/_th_p7cut/live24_table.csv
Would-have-cut for the 4 stops of the night 11-08/09: not evaluable (file not on the box; MORNING_FLAGS.md).

## 7. v1.5 policy line (exact grammar of DS7.cs v1.4: `side book regime cond [cond ...] action`, cond = feature op value, no spaces inside a cond; pct = unrealised / stop distance (60 pt), so ARM pts = 60 x |pct|)
- v2 line (the reference, unchanged): `loss P7 * pct<=-0.7500 pulled_mult>=5 win=5 persist=10 cut`
- best faster cell by exact L6M (fails exact PRE, NOT proposed): `loss P7 * pct<=-0.6667 pulled_mult>=5 win=5 persist=3 cut`  (ARM 40, no secs_ext condition because newMae is off)
- OLD live cell on state, for reference: `loss P7 * pct<=-0.5000 pulled_mult>=30 secs_ext<=5 win=5 persist=1 cut`
Fields the v1.4 grammar lacks for ANY of these lines (DS3_TH_STATE section 2): (a) `win=` per-rule window for the exact state pulled quantity (cancels NET of trades, own side, MedLevel EWMA 0.001; today one global ThL2PulledSecs and the per-print PulledSupport), (b) `persist=` consecutive seconds the whole condition holds, (c) `armlots=v1|v2` (lot-scaled arm, needs a `lots` feature) and `armusd=X` for the dollar arm clip(X/(lots*20),15,50) - neither needed by the 40/5x/p3 or v2 line, (d) session regime = CURRENT session at evaluation while the scored scope is the ENTRY session (needed for per-session cells), (e) evaluation once per second with a 1 s decision latency and market-exit cost 0.80 pt as scored. For the winning cell (none) the missing fields are (a) and (b) only.

## 8. Files, rules
Code: outputs/code/th_p7cut/ (prep_p7, kern_p7, score_p7, run_grid, run_score, final_rank, famnull, wf, placebo, live_prep, live_eval, p7_exact, exact_score, export_joint, gen_report). Data: /mnt/l2/l2vast/_th_p7cut/ (private; exact runs under exact/runs/<SET>/<yyyymm>). Joint export: /mnt/l2/l2vast/_th_joint/layers/cut/ (topK.json, roll_excl flag column). Live files read: P7 rows only of data/live/StratTrades_DS7_<acct>.csv and data/live_frozen/..., nt8log_latest.txt (no P7 lines). Regression: exact runner with the S1-COMB P7 cells reproduces S1-COMB 202610 exactly (823 trades). Pre-ROLL-EXCL tables kept in _th_p7cut/pre_rollexcl/. Exact rows were run with the roll trades inside the engine and excluded at scoring.
## 9. STANDING RULES 2 / 2a relabel (recents first; bi-weekly re-pick walk-forward = primary OOS test; ROLL-EXCL; first-order for the picks)
**Bi-weekly re-pick WF (P7 cut family, 54,720 cell x scope series, stack):** refit every 14 days from 2024-01-01 (74 periods), pick on the trailing 26 weeks ending 7 days before the refit (purge), hold 14 days. Pick key B = lowest training stack maxDD among cells whose training mean >= the live (v2) training mean and maxDD < v2's (else stay on v2); key A = lowest training maxDD only. Live setting = v2 line (45/5x/w5/p10); S1b-COMB as run (asia override) is the second reference. Files: /mnt/l2/l2vast/_th_p7cut/wf2_periods.csv, wf2_summary.json (outputs/code/th_p7cut/wf2.py).
| series (OOS, stack, first-order) | share of 74 refit periods beating v2 (P&L of the 2 weeks) | since 2026-05 (13 periods) | OOS mean $/wk all / L6M-part / PRE-part | OOS maxDD all / L6M-part / PRE-part |
|---|---|---|---|---|
| v2 (live) | - | - | 13.6k / 19.4k / 12.6k | 123k / 117k / 123k |
| bi-weekly re-pick, key B | 42% | 54% | 10.8k / 19.8k / 7.5k | 122k / 103k / 122k |
| bi-weekly re-pick, key A | 42% | 54% | 9.1k / 18.9k / 5.3k | 112k / 103k / 85k |
| S1b-COMB as run (fixed) | 70% | 69% | 14.1k / 22.2k / 13.3k | 144k / 110k / 108k |
| fixed 40/5x/w5/p3 (first-order) | 53% | 77% | 13.6k / 22.7k / 11.6k | 107k / 95k / 107k |
| fixed 40/5x/w5/p3, EXACT periods | L6M window 7 of 13 periods (54%); PRE window 17 of 36 (47%) | | exact L6M +3.6k, PRE -1.1k vs v2 | exact L6M stack maxDD -17%, PRE +25% |
**The re-pick procedure beats the live setting in 42% of refit periods (< 60%): rule 2a allowance = 15%, not 25%.** (The WF % for fixed 40/5x/w5/p3 is 53% first-order / 54% exact L6M / 47% exact PRE, also < 60%.) The procedure's OOS mean is below v2 (10.8k vs 13.6k, PRE-part 7.5k vs 12.6k): re-picking on the trailing 26 weeks does not improve on v2 here.

**Relabel (exact numbers, vs exact v2; allowance = min(25, L6M maxDD cut % + 10) only if WF >= 60%, else 15%; PRE mean floor -$1k/wk):**
| cell | exact L6M stack maxDD cut / mean chg | exact PRE stack maxDD vs v2 | exact PRE stack mean chg (P7 alone) | allowance used | label |
|---|---|---|---|---|---|
| 40/5x/w5/p3/noMae | -17% maxDD (+3.6k) | +25.2% deeper (P7 alone +62%) | -1.06k (P7 alone -1.2k) | 15% (WF 42-54% < 60%; even at 25% the maxDD is outside, and the mean is below the -1k floor) | **RECENT-ONLY** (both numbers: L6M maxDD -17% / PRE +25%; WF 42% procedure, 54% / 47% fixed cell) |
| 35/5x/w5/p3/noMae | exact L6M maxDD +10% (worse), mean +2.1k | not run | not run | 15% | fails the recents gate (L6M deeper); no PRE label |
| 25/20x/w5/p3/noMae | exact L6M +28% (worse), mean -5.7k | not run | not run | 15% | fails the recents gate |
| OLD live 30/30x/w5/p1/newMae | exact L6M +81% (worse), mean -4.4k | not run | not run | 15% | fails the recents gate |
| S1b-COMB as run (asia 50/5x/w3/p3/newMae V1, v2 elsewhere) | exact L6M stack maxDD 79.9k vs v2 95.2k = -16% (mean +2.9k); first-order WF 70% >= 60% | not run (exact PRE not run) | not run | min(25, 16+10) = 25% if WF >= 60% (first-order, fixed cell) | recents PASS-LIKE, PRE UNTESTED exactly: not labelled; first-order PRE stack maxDD 108k vs v2 123k (-12%), mean 13.3k vs 12.6k |
Everything else in the 13,680-cell first-order grid is not relabelled one by one: the first-order drawdown ranking is not predictive for P7 (section 2), and the re-pick procedure itself is under 60%.

## 10. REFIT 2026-11-22 (what the bi-weekly procedure picks today; trailing 26 weeks to the data end 2026-11-05; first-order, ROLL-EXCL)
- Key B pick: **pooled USD arm clip($2000/(lots x 20), 15, 50 pts) / MULT 20x / win 7 s / persist 1 s / noMae**. Key A pick: USD $2000 / 8x / win 3 / persist 2 (pooled).
- First-order comparison, stack maxDD / mean $/wk: L6M 54k / 21.4k vs v2 117k / 15.8k vs COMB-as-run 110k / 22.3k vs 40/5x/p3 95k / 22.1k; L3M 54k / 7.8k vs v2 85k / 16.4k vs COMB 92k / 16.2k; L1M 40k / -13.4k vs v2 75k / -25.1k vs COMB 64k / +9.8k; PRE 75k / 7.9k vs v2 123k / 13.9k (mean -6.0k/wk below the -1k floor) vs COMB 108k / 13.0k.
- Reading: the pick lowers first-order drawdown in every recent window but gives up mean in L3M and PRE, it has not been run in the exact engine, and first-order drawdown for P7 has been shown unreliable (the exact engine reversed 3 of 4 first-order-ranked faster cells). The procedure beat v2 in only 42% of past refit periods. **Not proposed; v2 stays live; COMB-as-run (asia override) is the only exactly confirmed recent improvement.** Exact run of the pick (6 L6M + 17 PRE months) was not done (time, memory cap).
- If adopted anyway the v1.5 line differs from live: `loss P7 * pct<=-0.2500 pulled_mult>=20 win=7 persist=1 armusd=2000 cut` (pct is the 15-pt floor of the clip, the arm is the dollar rule: needs the `armusd=` extension, plus `win=` and `persist=`; lots-scaled arm needs a `lots` feature). The live (v2) line remains `loss P7 * pct<=-0.7500 pulled_mult>=5 win=5 persist=10 cut`.
