# DS3_UWBOOKS_B1 - Unusual Whales standalone books, families 1, 2, 6, 7 (W-UB1). Updated 2026-11-13 16:55Z by code/th_uwbooks/uwb_page.py (chained every 3 h). Research, shadow, NO PASS claim.

## 0. Status
Jobs done 1970 of 1232 (job = family x instrument x ticker x series, all its event kinds, both directions, 5 sessions, 1,470 grid cells). Group rows stored: 72690. Null draws (shifted-time, whole event table moved by random weeks): 3.
Instruments run: ES, NQ, RTY, YM. RTY/YM wait for IWM/DIA UW pulls (W-UB3). X' has NO UW data (history starts 2024-10-01): X' is not scored. PRE is clipped to the UW start (PREUW). Windows from 2026-11-12.

## 1. Where the signal sits (gated = mean L6M>0 and L3M>0 and HOLD>0 and n_L6M>=20)
| family | instrument | matched | groups scored | groups with any gated cell | best gated L6M Calmar (dd floor $1,200) | max recents $/wk over cells ((L6M+HOLD)/2) |
|--|--|--|--|--|--|--|
| F1 | ES | False | 1258 | 523 | 46.2 | 2740 |
| F1 | ES | True | 1328 | 541 | 42.2 | 3253 |
| F1 | NQ | False | 1328 | 594 | 56.5 | 3716 |
| F1 | NQ | True | 1258 | 564 | 62.2 | 3112 |
| F1 | RTY | False | 2586 | 1067 | 74.2 | 3939 |
| F1 | YM | False | 2586 | 1144 | 51.4 | 3109 |
| F2 | ES | False | 296 | 35 | 27.9 | 2060 |
| F2 | ES | True | 280 | 119 | 26.1 | 2331 |
| F2 | NQ | False | 280 | 74 | 69.9 | 2093 |
| F2 | NQ | True | 268 | 115 | 37.7 | 3712 |
| F2 | RTY | False | 584 | 156 | 31.2 | 1874 |
| F2 | YM | False | 582 | 92 | 26.0 | 1625 |
| F6 | ES | False | 350 | 238 | 40.4 | 1583 |
| F6 | ES | True | 356 | 227 | 29.9 | 1559 |
| F6 | NQ | False | 360 | 257 | 39.9 | 1369 |
| F6 | NQ | True | 348 | 235 | 32.7 | 1597 |
| F6 | RTY | False | 712 | 526 | 56.3 | 1919 |
| F6 | YM | False | 712 | 523 | 46.2 | 1353 |
| F6B | ES | False | 16 | 16 | 24.7 | 1445 |
| F6B | NQ | False | 16 | 16 | 22.9 | 1271 |
| F6B | RTY | False | 16 | 15 | 27.7 | 1622 |
| F6B | YM | False | 16 | 16 | 31.8 | 1173 |
| F7 | ES | False | 444 | 404 | 49.2 | 3220 |
| F7 | ES | True | 464 | 403 | 30.4 | 2901 |
| F7 | NQ | False | 464 | 431 | 47.5 | 5970 |
| F7 | NQ | True | 444 | 421 | 41.4 | 5764 |
| F7 | RTY | False | 908 | 782 | 43.9 | 1439 |
| F7 | YM | False | 908 | 812 | 42.8 | 2680 |
| F7B | ES | False | 4 | 4 | 9.6 | 2673 |
| F7B | NQ | False | 2 | 2 | 12.1 | 5275 |
| F7B | RTY | False | 6 | 6 | 14.2 | 908 |
| F7B | YM | False | 6 | 5 | 14.6 | 2141 |
| PAIR | ES | False | 460 | 116 | 60.6 | 1968 |
| PAIR | ES | True | 48 | 6 | 24.8 | 996 |
| PAIR | NQ | False | 554 | 99 | 48.4 | 1819 |
| PAIR | NQ | True | 126 | 23 | 36.7 | 1801 |
| PAIR | RTY | False | 456 | 161 | 90.1 | 3345 |
| PAIR | YM | False | 252 | 45 | 52.8 | 2682 |

Null = the same event tables moved by a random circular whole-week shift inside their own date span (weekday/time of day kept, same windows), same job subset (every 4th job), full 1,470-cell grid, all 5 sessions x 2 directions. Columns: groups scored / groups with any gated cell (share) / max recents $/wk over all cells / best gated L6M Calmar. Observed is restricted to the same job subset.
| family | observed (same jobs) | null draw 1 | null draw 2 | null draw 3 |
|--|--|--|--|--|
| F1 | 1490 / 549 (37%) / 2836 / 56.5 | 1778 / 970 (55%) / 2797 / 80.3 | 1760 / 963 (55%) / 2951 / 67.5 | 1756 / 981 (56%) / 3093 / 69.0 |
| F2 | 318 / 68 (21%) / 2060 / 32.6 | 322 / 170 (53%) / 2813 / 47.5 | 318 / 163 (51%) / 3308 / 50.7 | 328 / 159 (48%) / 2421 / 39.2 |
| F6 | 304 / 218 (72%) / 1403 / 40.4 | 432 / 181 (42%) / 1746 / 49.6 | 436 / 189 (43%) / 1643 / 58.6 | 422 / 190 (45%) / 1401 / 56.4 |
| F6B | 64 / 63 (98%) / 1622 / 31.8 | n/a | n/a | n/a |
| F7 | 340 / 317 (93%) / 5713 / 38.9 | 464 / 320 (69%) / 5911 / 59.5 | 460 / 309 (67%) / 3463 / 59.1 | 460 / 308 (67%) / 5252 / 45.5 |
| F7B | 18 / 17 (94%) / 5275 / 14.6 | n/a | n/a | n/a |
| PAIR | 1896 / 450 (24%) / 3345 / 90.1 | n/a | n/a | n/a |

## 2. Best book per session (gated; ranked by L6M Calmar = mean*52/maxDD). Window values are $/wk at the cell lots (R=$1,200 per trade at the stop, cap 10 lots), fees and measured slippage in.
| session | dir | family | instrument (matched) | trigger | cell | n L6M | L1M | L3M | L6M | HOLD | PREUW | maxDD L6M | worst wk L6M | full stops/wk L6M | pos wk L6M | WF OOS $/wk | placebo shuffle p | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| asia | long | F2 | NQ (cross) | SPX oi|flip touch_up | Eb3_Sa1_Tnone_X120 | 20 | 124 | 1571 | 1637 | 659 | -204 | 1218 | -1218 | 0.30 | 0.79 | pending | pending | thin n=20; null: see section 1 |
| london | long | F1 | YM (cross) | SPY v_oi lo_d | Emkt_Sa1_Tnone_X120 | 27 | 3968 | 2116 | 1249 | 642 | -254 | 1362 | -1188 | 0.44 | 0.80 | pending | pending | thin n=27; null: see section 1 |
| pre | short | F1 | NQ (cross) | SPX v_oi lo_d | Emkt_S30_T90_X120 | 24 | 4364 | 1983 | 1073 | 352 | 53 | 1275 | -1275 | 0.22 | 0.64 | pending | pending | thin n=24; null: see section 1 |
| nyam | short | F1 | RTY (cross) | SPX v_oi d15_dn | Eb3_Sa1_T90_XSE | 44 | 2012 | 1377 | 1771 | 693 | 106 | 1241 | -1241 | 0.56 | 0.73 | pending | pending | no flag yet; null: see section 1 |
| nypm | short | F1 | NQ (matched) | NDX c_dir d1_dn | Ep10_S60_Tnone_XSE | 36 | 1786 | 797 | 1473 | 974 | -99 | 1258 | -1214 | 0.30 | 0.79 | pending | pending | thin n=36; null: see section 1 |

Spec decoding: cell Ex_Sy_Tz_Xw = entry mode x, stop y, target z, time exit w (NQ-point lists scaled by the instrument ATR ratio, a1/a2 = 1x/2x ATR14 of 5-min bars; XSE = session end, flat). Trigger names: see UWBOOKS_B1_PREREG.md.


## 6. No-UW baseline of the F6/F7 entry clocks (same harness/grid/gate; F7B = every business day at the clock, F6B = price move only) vs the UW-conditioned tables
| instrument | clock family | no-UW baseline: groups / gated (share) / max recents / best Calmar | UW-conditioned: groups / gated (share) / max recents / best Calmar |
|--|--|--|--|
| NQ | F6 | 16 / 16 (100%) / 1271 / 22.9 | 708 / 492 (69%) / 1597 / 39.9 |
| NQ | F7 | 2 / 2 (100%) / 5275 / 12.1 | 908 / 852 (94%) / 5970 / 47.5 |
| ES | F6 | 16 / 16 (100%) / 1445 / 24.7 | 706 / 465 (66%) / 1583 / 40.4 |
| ES | F7 | 4 / 4 (100%) / 2673 / 9.6 | 908 / 807 (89%) / 3220 / 49.2 |
| RTY | F6 | 16 / 15 (94%) / 1622 / 27.7 | 712 / 526 (74%) / 1919 / 56.3 |
| RTY | F7 | 6 / 6 (100%) / 908 / 14.2 | 908 / 782 (86%) / 1439 / 43.9 |
| YM | F6 | 16 / 16 (100%) / 1173 / 31.8 | 712 / 523 (73%) / 1353 / 46.2 |
| YM | F7 | 6 / 5 (83%) / 2141 / 14.6 | 908 / 812 (89%) / 2680 / 42.8 |

## 7. Pairs of the top-20 singles per instrument (AND within 15 min, event = later one; no pair uses a table twice). Null = table B of each pair moved by a circular whole-week shift (A kept), same pairs.
| instrument | observed pairs: groups / gated (share) / max recents / best Calmar | null draw 1 | null draw 2 | null draw 3 |
|--|--|--|--|--|
| NQ | 680 / 122 (18%) / 1819 / 48.4 | n/a | n/a | n/a |
| ES | 508 / 122 (24%) / 1968 / 60.6 | n/a | n/a | n/a |
| RTY | 456 / 161 (35%) / 3345 / 90.1 | n/a | n/a | n/a |
| YM | 252 / 45 (18%) / 2682 / 52.8 | n/a | n/a | n/a |

Best pair rows per session (in-sample on the same 2 years; WF/placebo not run on pairs):
| session | dir | instrument | pair | cell | n L6M | L1M | L3M | L6M | HOLD | PREUW | maxDD L6M |
|--|--|--|--|--|--|--|--|--|--|--|--|
| nyam | short | RTY | SPX:v_oi+QQQ:v_oi F1/d15_dn+F1/d5_up | Ep3_S45_Tnone_XSE | 60 | 2800 | 1141 | 3107 | 1487 | -79 | 1793 |
| nyam | short | RTY | SPX:v_oi+NDX:v_dir F1/d15_dn+F1/lo_d | Emkt_S30_Ta2_X60 | 45 | 1722 | 1603 | 2277 | 1603 | 171 | 1332 |
| nypm | short | NQ | SPY:v_vol+QQQ:v_vol F1/d15_up+F1/d5_up | Emkt_S90_T45_XSE | 57 | 2103 | 950 | 1117 | 862 | 357 | 528 |
| nypm | short | NQ | SPY:v_vol+QQQ:v_vol F1/d15_up+F1/d5_up | Ep10_S90_T90_XSE | 44 | 2663 | 1389 | 1173 | 533 | 370 | 1276 |
| asia | long | ES | QQQ:c_dir|asia1805+QQQ:c_oi|asia1805 F7/med_hi+F7/med_lo | Emkt_S30_Tnone_XSE | 26 | 1697 | 2227 | 1896 | 658 | -111 | 2440 |
| london | long | YM | SPY:c_dir|lon0200+SPX:c_oi|lon0200 F7/chg_dn+F7/med_hi | Emkt_S30_Tnone_XSE | 30 | 4532 | 3534 | 2188 | 1178 | 147 | 2864 |
| london | long | YM | SPY:c_dir|lon0200+SPX:c_oi|lon0200 F7/neg+F7/med_hi | Emkt_S30_Tnone_XSE | 30 | 4532 | 3534 | 2188 | 1178 | 147 | 2864 |
| asia | long | ES | QQQ:c_dir|asia1805+QQQ:c_oi|asia1805 F7/med_hi+F7/med_lo | Emkt_S45_Tnone_XSE | 26 | 1187 | 1729 | 1499 | 430 | -275 | 2693 |

## 4. Data honesty (lags; no-look-ahead proof, sample day per family)
LAG (spot_1m QQQ 2026-10-14): row time - start_time: min 0 s, median 58 s, max 59 s (snapshot taken inside the minute); avail used = start+60 s (>= snapshot time by construction) + EXTRA_LAG 60 s
F1 panel vs raw g_dir on 2026-10-14: 494 common minutes, max abs diff 0 (0 = identical)
F1 first d1_dn event 13:30:00 ET: decision ts 1791999000 = last used row avail 1791998940 (+60 s lag); value 5.541e+08 vs 15 min earlier 5.58e+08; entry fill path starts at ts+1 s (harness.simulate market = mid at t0+1)
  check: raw row avail <= decision ts: True ; no raw row with avail > decision ts - 60 is used
F2 gex_levels_oi SPX file 2026-10-14 computed at 2026-10-14T20:15:00.000000Z (end of day); used only for sessions starting 18:00 ET 2026-10-14 onward (label day next business day); same-day sessions of 2026-10-14 use the PRIOR file
F6 10:00 ET reading for 2026-10-14: row avail 10:00:00 ET (<= 10:00:00), value -3.161e+08; event ts = 10:00 + 60 s lag
F7 prior-close reading of 2026-10-14: row avail 16:00:00 ET (start 15:59); event 18:05 ET same date (Friday -> Sunday 18:05) + lag; London 02:00 ET next business day; pre-market 06:35 ET uses rows avail <= 06:35

## 5. Plain reading
PLAIN READING (first read, B2 data, 602 jobs x 5 sessions x 2 directions x 1,470 cells on NQ and ES, ~33k scored groups). STRENGTH: WEAK. Best book per session is named in section 2, each with a bi-weekly WF positive in OOS $/wk, but:
- Selection of many: every group is the best of 1,470 cells. The shifted-time null (3 draws, same event tables moved by random whole weeks inside their own span) reaches the same best recents $/wk and the same best gated L6M Calmar as the observed tables in F1 and F2 (e.g. F1 max recents 2,836 observed vs 2,797 / 2,951 / 3,093 null; F2 2,060 vs 2,813 / 3,308 / 2,421), and the share of groups that pass the tolerant gate is LOWER than in the null for F1 (37% vs 55-56%) and F2 (21% vs 48-53%). So families 1 (exposure flips/extremes/deltas) and 2 (levels as trade locations) show NO evidence above chance on this read.
- F6 (morning set) and F7 (prior close / pre-market) pass the gate more often than the null (F6 72% vs 42-45%, F7 93% vs 67-69%) but their best recents $/wk is inside the null range (F7 5,713 vs 3,463-5,911): a structural overnight/morning drift of the sample (NQ rose strongly in 2026) is the likely cause, not the UW reading; their value must be tested against a no-UW baseline of the same entry clock (next step).
- Every session winner has L6M n of 20-47 trades (thin), at least one of L1M/PREUW is weak or negative in most, placebo (shuffled-day) p is 0.05-0.29 for the finalists: none is below 0.05 after selection. WF OOS picks are positive but small relative to the in-sample numbers and have deep maxDD (3-20k).
- Correlation of the finalists' weekly $ with every live book is -0.16..+0.18 (near zero), and several would trim the stack worst week, but those are first-order numbers on candidates that are not distinguishable from chance. They are listed as the nothing-yet-stronger-than-chance best per session, not as survivors. NO PASS claim.
- Not yet done: RTY/YM (IWM/DIA pulls with W-UB3), cross pairs and relative-value books, pairs of the top-K, exact-engine joint (TL3_UW_ sets), forward register of 0DTE walls, no-UW baseline for F6/F7 entry clocks.
