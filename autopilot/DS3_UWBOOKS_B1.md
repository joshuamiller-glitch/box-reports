# DS3_UWBOOKS_B1 - Unusual Whales standalone books, families 1, 2, 6, 7 (W-UB1). Updated 2026-11-13 16:16Z by code/th_uwbooks/uwb_page.py (chained every 3 h). Research, shadow, NO PASS claim.

## 0. Status
Jobs done 602 of 602 (job = family x instrument x ticker x series, all its event kinds, both directions, 5 sessions, 1,470 grid cells). Group rows stored: 33152. Null draws (shifted-time, whole event table moved by random weeks): 3.
Instruments run: ES, NQ. RTY/YM wait for IWM/DIA UW pulls (W-UB3). X' has NO UW data (history starts 2024-10-01): X' is not scored. PRE is clipped to the UW start (PREUW). Windows from 2026-11-12.

## 1. Where the signal sits (gated = mean L6M>0 and L3M>0 and HOLD>0 and n_L6M>=20)
| family | instrument | matched | groups scored | groups with any gated cell | best gated L6M Calmar (dd floor $1,200) | max recents $/wk over cells ((L6M+HOLD)/2) |
|--|--|--|--|--|--|--|
| F1 | ES | False | 1258 | 523 | 46.2 | 2740 |
| F1 | ES | True | 1328 | 541 | 42.2 | 3253 |
| F1 | NQ | False | 1328 | 594 | 56.5 | 3716 |
| F1 | NQ | True | 1258 | 564 | 62.2 | 3112 |
| F2 | ES | False | 296 | 35 | 27.9 | 2060 |
| F2 | ES | True | 280 | 119 | 26.1 | 2331 |
| F2 | NQ | False | 280 | 74 | 69.9 | 2093 |
| F2 | NQ | True | 268 | 115 | 37.7 | 3712 |
| F6 | ES | False | 350 | 238 | 40.4 | 1583 |
| F6 | ES | True | 356 | 227 | 29.9 | 1559 |
| F6 | NQ | False | 360 | 257 | 39.9 | 1369 |
| F6 | NQ | True | 348 | 235 | 32.7 | 1597 |
| F7 | ES | False | 444 | 404 | 49.2 | 3220 |
| F7 | ES | True | 464 | 403 | 30.4 | 2901 |
| F7 | NQ | False | 464 | 431 | 47.5 | 5970 |
| F7 | NQ | True | 444 | 421 | 41.4 | 5764 |

Null = the same event tables moved by a random circular whole-week shift inside their own date span (weekday/time of day kept, same windows), same job subset (every 4th job), full 1,470-cell grid, all 5 sessions x 2 directions. Columns: groups scored / groups with any gated cell (share) / max recents $/wk over all cells / best gated L6M Calmar. Observed is restricted to the same job subset.
| family | observed (same jobs) | null draw 1 | null draw 2 | null draw 3 |
|--|--|--|--|--|
| F1 | 1490 / 549 (37%) / 2836 / 56.5 | 1778 / 970 (55%) / 2797 / 80.3 | 1760 / 963 (55%) / 2951 / 67.5 | 1756 / 981 (56%) / 3093 / 69.0 |
| F2 | 318 / 68 (21%) / 2060 / 32.6 | 322 / 170 (53%) / 2813 / 47.5 | 318 / 163 (51%) / 3308 / 50.7 | 328 / 159 (48%) / 2421 / 39.2 |
| F6 | 304 / 218 (72%) / 1403 / 40.4 | 432 / 181 (42%) / 1746 / 49.6 | 436 / 189 (43%) / 1643 / 58.6 | 422 / 190 (45%) / 1401 / 56.4 |
| F7 | 340 / 317 (93%) / 5713 / 38.9 | 464 / 320 (69%) / 5911 / 59.5 | 460 / 309 (67%) / 3463 / 59.1 | 460 / 308 (67%) / 5252 / 45.5 |

## 2. Best book per session (gated; ranked by L6M Calmar = mean*52/maxDD). Window values are $/wk at the cell lots (R=$1,200 per trade at the stop, cap 10 lots), fees and measured slippage in.
| session | dir | family | instrument (matched) | trigger | cell | n L6M | L1M | L3M | L6M | HOLD | PREUW | maxDD L6M | worst wk L6M | full stops/wk L6M | pos wk L6M | WF OOS $/wk | placebo shuffle p | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| asia | long | F2 | NQ (cross) | SPX oi|flip touch_up | Eb3_Sa1_Tnone_X120 | 20 | 124 | 1571 | 1637 | 659 | -204 | 1218 | -1218 | 0.30 | 0.79 | 172 | 0.19 | thin n=20; placebo p>0.1; null: see section 1 |
| london | long | F1 | ES (cross) | QQQ g_oi d1_up | Ep10_Sa2_Tnone_XSE | 28 | 141 | 1663 | 1130 | 472 | -155 | 1279 | -1279 | 0.48 | 0.73 | 196 | 0.05 | thin n=28; null: see section 1 |
| pre | short | F1 | NQ (cross) | SPX v_oi lo_d | Emkt_S30_T90_X60 | 24 | 4364 | 1983 | 1073 | 352 | 53 | 1275 | -1275 | 0.22 | 0.64 | 250 | 0.05 | thin n=24; null: see section 1 |
| nyam | short | F1 | NQ (matched) | QQQ v_dir d15_up | Eb3_S30_Tnone_X120 | 27 | 5272 | 1994 | 3022 | 1297 | 293 | 2528 | -1227 | 0.48 | 0.50 | 701 | 0.10 | thin n=27; null: see section 1 |
| nypm | short | F1 | NQ (matched) | NDX c_dir d1_dn | Ep10_S60_Tnone_XSE | 36 | 1786 | 797 | 1473 | 974 | -99 | 1258 | -1214 | 0.30 | 0.79 | 524 | 0.29 | thin n=36; placebo p>0.1; null: see section 1 |

Spec decoding: cell Ex_Sy_Tz_Xw = entry mode x, stop y, target z, time exit w (NQ-point lists scaled by the instrument ATR ratio, a1/a2 = 1x/2x ATR14 of 5-min bars; XSE = session end, flat). Trigger names: see UWBOOKS_B1_PREREG.md.

## 3. Finalist detail (top 3 per session, re-simulated; WF = bi-weekly re-pick over all 1,470 cells of the group, trail 26 wk; placebo = shuffled-day events, B=20: p = share of draws whose best-cell recents >= the group best-cell recents)
| session | dir | inst | trigger | cell | spec entry | stop | target | time exit | L6M | HOLD | WF mean $/wk | WF maxDD | WF worst | WF periods positive | placebo q95 | placebo p |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| asia | 1 | NQ | F2 SPX oi|flip touch_up | Eb3_Sa1_Tnone_X120 | enter at +3 min if price moved in direction | 1 x ATR5 | none | 120 min | 1637 | 659 | 172 | 11501 | -1814 | 0.44 | 2185 | 0.19 |
| asia | 1 | NQ | F2 SPX oi|flip touch_up | Eb3_Sa1_T90_X120 | enter at +3 min if price moved in direction | 1 x ATR5 | 90 NQ-pts x 1.00 = 90.0 NQ pts | 120 min | 1512 | 656 | 172 | 11501 | -1814 | 0.44 | 2185 | 0.19 |
| asia | -1 | ES | F7 QQQ g_dir|asia1805 med_hi | Eb3_S45_Tnone_XSE | enter at +3 min if price moved in direction | 45 NQ-pts x 0.19 = 8.6 ES pts | none | session end | 1273 | 669 | -219 | 20867 | -3467 | 0.29 | 1910 | 0.10 |
| london | 1 | ES | F1 QQQ g_oi d1_up | Ep10_Sa2_Tnone_XSE | limit pullback 10 NQ-pts | 2 x ATR5 | none | session end | 1130 | 472 | 196 | 3541 | -1489 | 0.42 | 702 | 0.05 |
| london | 1 | ES | F1 QQQ g_oi d1_up | Ep10_Sa2_Tnone_X120 | limit pullback 10 NQ-pts | 2 x ATR5 | none | 120 min | 1130 | 472 | 196 | 3541 | -1489 | 0.42 | 702 | 0.05 |
| london | 1 | ES | F1 QQQ g_oi d1_up | Ep10_Sa2_T90_XSE | limit pullback 10 NQ-pts | 2 x ATR5 | 90 NQ-pts x 0.19 = 17.3 ES pts | session end | 1088 | 540 | 196 | 3541 | -1489 | 0.42 | 702 | 0.05 |
| nyam | -1 | NQ | F1 QQQ v_dir d15_up | Eb3_S30_Tnone_X120 | enter at +3 min if price moved in direction | 30 NQ-pts x 1.00 = 30.0 NQ pts | none | 120 min | 3022 | 1297 | 701 | 5011 | -2427 | 0.55 | 2008 | 0.10 |
| nyam | -1 | NQ | F1 QQQ v_dir d15_up | Eb3_S30_Tnone_XSE | enter at +3 min if price moved in direction | 30 NQ-pts x 1.00 = 30.0 NQ pts | none | session end | 3017 | 1295 | 701 | 5011 | -2427 | 0.55 | 2008 | 0.10 |
| nyam | 1 | NQ | F1 QQQ c_oi hi_d | Ep10_S30_Tnone_X60 | limit pullback 10 NQ-pts | 30 NQ-pts x 1.00 = 30.0 NQ pts | none | 60 min | 1704 | 868 | 67 | 7523 | -5056 | 0.35 | 2404 | 0.24 |
| nypm | -1 | NQ | F1 NDX c_dir d1_dn | Ep10_S60_Tnone_XSE | limit pullback 10 NQ-pts | 60 NQ-pts x 1.00 = 60.0 NQ pts | none | session end | 1473 | 974 | 524 | 2738 | -1976 | 0.63 | 2105 | 0.29 |
| nypm | -1 | NQ | F1 SPY v_vol d15_up | Ep10_Sa2_T60_XSE | limit pullback 10 NQ-pts | 2 x ATR5 | 60 NQ-pts x 1.00 = 60.0 NQ pts | session end | 1304 | 720 | 241 | 5917 | -2455 | 0.60 | 2455 | 0.90 |
| nypm | -1 | NQ | F1 NDX c_dir d1_dn | Ep10_S45_Tnone_XSE | limit pullback 10 NQ-pts | 45 NQ-pts x 1.00 = 45.0 NQ pts | none | session end | 1240 | 862 | 524 | 2738 | -1976 | 0.63 | 2105 | 0.29 |
| pre | -1 | NQ | F1 SPX v_oi lo_d | Emkt_S30_T90_X60 | market at t0+1s | 30 NQ-pts x 1.00 = 30.0 NQ pts | 90 NQ-pts x 1.00 = 90.0 NQ pts | 60 min | 1073 | 352 | 250 | 3773 | -1417 | 0.35 | 425 | 0.05 |
| pre | -1 | NQ | F1 SPX v_oi lo_d | Emkt_S30_T90_XSE | market at t0+1s | 30 NQ-pts x 1.00 = 30.0 NQ pts | 90 NQ-pts x 1.00 = 90.0 NQ pts | session end | 1073 | 352 | 250 | 3773 | -1417 | 0.35 | 425 | 0.05 |
| pre | -1 | NQ | F1 SPX v_oi lo_d | Emkt_S30_T90_X120 | market at t0+1s | 30 NQ-pts x 1.00 = 30.0 NQ pts | 90 NQ-pts x 1.00 = 90.0 NQ pts | 120 min | 1073 | 352 | 250 | 3773 | -1417 | 0.35 | 425 | 0.05 |

## 3b. First-order joint (finalist weekly $ added to the live stack S1B-COMB weekly, own lots; exact-engine joint via TP sets TL3_UW_* follows)
| finalist id | corr KB/PE/SM/HM/MV/PB/OD | corr stack | stack maxDD L6M -> with | stack worst wk L6M -> with | cand mean L6M | weeks trading |
|--|--|--|--|--|--|--|
| F1_ES_QQQ_g_oi_d1_up_london_1_Ep10_Sa2_T90_XSE | 0.08/0.07/0.04/-0.10/-0.16/0.06/0.01 | 0.04 | 79907 -> 79727 | -62941 -> -64220 | 1130 | 42 |
| F1_ES_QQQ_g_oi_d1_up_london_1_Ep10_Sa2_Tnone_X120 | 0.07/0.14/0.10/-0.09/-0.06/0.09/0.02 | 0.12 | 79907 -> 79727 | -62941 -> -64220 | 1173 | 42 |
| F1_ES_QQQ_g_oi_d1_up_london_1_Ep10_Sa2_Tnone_XSE | 0.07/0.14/0.10/-0.09/-0.06/0.09/0.02 | 0.12 | 79907 -> 79727 | -62941 -> -64220 | 1173 | 42 |
| F1_NQ_NDX_c_dir_d1_dn_nypm_-1_Ep10_S45_Tnone_XSE | 0.03/0.11/0.14/0.05/-0.11/0.10/-0.15 | 0.10 | 79907 -> 79194 | -62941 -> -63855 | 1196 | 61 |
| F1_NQ_NDX_c_dir_d1_dn_nypm_-1_Ep10_S60_Tnone_XSE | 0.02/0.10/0.13/0.05/-0.14/0.09/-0.15 | 0.08 | 79907 -> 79194 | -62941 -> -59795 | 1426 | 61 |
| F1_NQ_QQQ_c_oi_hi_d_nyam_1_Ep10_S30_Tnone_X60 | 0.04/-0.03/-0.00/0.02/-0.02/-0.09/-0.08 | -0.02 | 79907 -> 74395 | -62941 -> -62941 | 1395 | 31 |
| F1_NQ_QQQ_v_dir_d15_up_nyam_-1_Eb3_S30_Tnone_X120 | 0.04/0.12/0.06/0.07/0.00/-0.09/-0.13 | 0.11 | 79907 -> 78451 | -62941 -> -64168 | 3140 | 47 |
| F1_NQ_QQQ_v_dir_d15_up_nyam_-1_Eb3_S30_Tnone_XSE | 0.04/0.12/0.06/0.07/0.00/-0.09/-0.13 | 0.11 | 79907 -> 78451 | -62941 -> -64168 | 3135 | 47 |
| F1_NQ_SPX_v_oi_lo_d_pre_-1_Emkt_S30_T90_X120 | 0.13/0.08/-0.02/-0.02/0.11/-0.10/-0.08 | 0.08 | 79907 -> 79907 | -62941 -> -59351 | 1117 | 73 |
| F1_NQ_SPX_v_oi_lo_d_pre_-1_Emkt_S30_T90_X60 | 0.13/0.08/-0.02/-0.02/0.11/-0.10/-0.08 | 0.08 | 79907 -> 79907 | -62941 -> -59351 | 1117 | 73 |
| F1_NQ_SPX_v_oi_lo_d_pre_-1_Emkt_S30_T90_XSE | 0.13/0.08/-0.02/-0.02/0.11/-0.10/-0.08 | 0.08 | 79907 -> 79907 | -62941 -> -59351 | 1117 | 73 |
| F1_NQ_SPY_v_vol_d15_up_nypm_-1_Ep10_Sa2_T60_XSE | 0.03/0.02/0.11/0.10/-0.02/0.01/-0.05 | 0.05 | 79907 -> 76926 | -62941 -> -60551 | 1229 | 97 |
| F2_NQ_SPX_oi-flip_touch_up_asia_1_Eb3_Sa1_T90_X120 | -0.05/-0.01/0.01/0.11/0.06/0.06/-0.01 | 0.01 | 79907 -> 79907 | -62941 -> -58836 | 1444 | 52 |
| F2_NQ_SPX_oi-flip_touch_up_asia_1_Eb3_Sa1_Tnone_X120 | -0.04/0.05/0.04/0.11/0.08/0.05/0.01 | 0.07 | 79907 -> 79907 | -62941 -> -59148 | 1574 | 52 |
| F7_ES_QQQ_g_dir-asia1805_med_hi_asia_-1_Eb3_S45_Tnone_XSE | -0.01/0.17/0.11/0.11/0.10/0.09/0.01 | 0.18 | 79907 -> 79907 | -62941 -> -64287 | 1374 | 74 |

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
