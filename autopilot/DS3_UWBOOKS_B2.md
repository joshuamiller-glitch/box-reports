# DS3_UWBOOKS_B2 - W-UB2: Tide, flow bursts, dark-pool/IV books (+pairs, joint). Built 2026-11-13 19:39Z by code/th_uwb2/uwb2_page.py. Research, shadow, NO PASS claim.
Prereg: autopilot/UWB2_PREREG.md (sha line in DECISIONS.md 14:30Z). Harness: code/th_uwbooks/harness.py (W-UB1) unchanged. Events: code/th_uwb2/uwb2_events.py. Screens: /mnt/l2/l2vast/_uwb2/B2/res_*.csv. Units: $ per week at 1 lot-set (lots = clip(round(1200/(stop pts x $/pt)),1,10)), fees in, measured NQ basis, ES/RTY 1 tick/side (UNMEASURED).

## 0. Plain verdict (read first)
FIRST PAGE, honest strength: WEAK TO NONE: the strongest lead fails its family null. After the roll-glitch harness fix (W-UB1 15:46Z) every screen was re-run from scratch; nothing below is PASS.
(1) Strongest single candidate (F4, flow burst): NQ short (fade) at NYPM 12:00-15:00 ET when NDX options show a 1-minute bullish net-premium burst (flX_d1_q95_up, NDX net call-minus-put premium change above the trailing-20-day q95), market entry, stop 2 x ATR14(5 min), target 1 x ATR, time exit 60 min: n=116 trades in L6M, all four recent windows positive (L1M +2,192 / L3M +1,386 / L6M +1,559 / HOLD +1,340 $/wk), PRE-UW -137, max DD L6M $2,268, bi-weekly WF +651 $/wk OOS with 74% of periods positive, beats all 10 shifted-time and all 10 shuffled-day placebo draws of the same cell (p=0.09 is the floor at 10 draws), weekly correlation with the live stack 0.12, trades while the live stack is flat 54% of the time. It is ONE cell chosen from a 1,470-cell grid and ~170 event kinds of the family; FAMILY NULL (F4 on NDX, 52 event tables x 1,470 cells, whole table shifted by random weeks, statistic = best gated cell recents per session, section 4): observed NYPM 2,226 vs shifted-time draws 2,311-3,425 so far (every draw above the observed), NYAM observed 2,233 vs 2,536-3,425: the best-of-family result is NOT distinguishable from what an unconditional grid search finds on shifted timing (same drift, same time of day). So the burst-fade cell is a LEAD(weak) only, its cell-level placebo is a within-cell test and does not cure the 1,470 x 52 selection. Not a book to size.
(2) F3 Market Tide: no cell separates from its family null by a margin (NYAM best raw cell p~0.11, others inside the null; the previous harness version, re-run pending). Tide-vs-price divergence in the opposite direction is almost empty (60-min price move beyond 3 ATR with Tide moving the other way: 0-17 events): Tide follows price.
(3) F5 dark-pool levels and IV: the Asia 'IV high -> short NQ for the whole session' cells (+8k $/wk L6M) are drift: the unconditional every-day cell in the same session earns about the same (section 3) and PRE-UW is negative; NY/London/PRE rows have n=19-43 trades (thin). Skew history does not exist on the plan.
(4) Unconditional baselines in section 3 are the bar: every trigger book must beat its session's untriggered best cell, which already earns hundreds to thousands of $/wk in L6M from a one-way drift.
(5) Pairs of top singles (NQ): the F4 NDX burst AND NDX gamma(vol) d1 rise (30 min) gives similar L6M with about 43% of the DD (983 vs 2,268) but is an in-sample pick; see pairs table. Joint stage is FIRST-ORDER only (no engine interaction); the exact-engine TL3_UW_ hooks for a book with its own entries are not built yet (next).
(6) Full option tape (0DTE vs longer, aggression, >=$100k bursts) is downloading newest-first; F4T screens start when >= 30 days are on disk; flow-alerts/skew cannot be back-tested.


## 1. What the UW plan gives for historical flow (probe /mnt/l2/l2vast/_uwb2/probe_flow.out, no spend)
| endpoint | history on the plan | used here |
|---|---|---|
| /stock/{t}/net-prem-ticks (per-minute net call/put premium, ask/bid volume) | YES, 2 years (2024-10 verified), any ticker | F4 (SPX NDX QQQ SPY pulled; megacaps via W-UB3 pull net_prem_ticks) |
| /stock/{t}/greek-flow and greek-flow/{expiry=date} (0DTE delta/vega flow per minute) | YES, 2 years | F4Z (QQQ SPY SPX NDX) |
| /stock/{t}/flow-per-strike-intraday | YES, 2 years (~1 MB/day/ticker) | not yet screened |
| /option-trades/full-tape/{date} (every OPRA trade: size, premium, bid/ask-side tags, DTE) | YES, from 2023-12-14 (1-2 GB zip/day; 403 earlier) | streamed + aggregated (never stored): per-minute by DTE bucket 0 / 1-5 / 6+, call/put, ask/bid, >=$100k; code/th_uwb2/tape_pull.py; newest day first, ~4.5 min/day |
| /option-trades/flow-alerts, /option-trades (list), /stock/{t}/flow-recent | NO: only the latest 50 rows whatever the date param | forward register only (live recorder autopilot/forward/uw_live option_trades:SPX/NDX); W-UB3 pulls flow alerts forward |
| /stock/{t}/historical-risk-reversal-skew | NO: 0 rows beyond ~2 weeks | skew NOT testable historically |
| /stock/{t}/interpolated-iv | only the requested day (9 tenors), daily | IV level from volatility/stats (daily) used instead |
Cannot be tested: skew history; per-alert (sweep/floor flag) history older than the forward register; anything before 2024-10 for Tide/net-prem/greek-flow (plan limit ~2 yr; the tape reaches 2023-12 but only a few weeks are downloaded yet); X' window (no UW data).

## 2. Timestamps and no-look-ahead (lag per series)
| series | raw timestamp | usable from | lag stated |
|---|---|---|---|
| market tide (cumulative NCP/NPP/volume, per minute) | bar start (ET offset in string) | bar start + 60 s + 60 s assumed delivery lag (UWB_LAG, stress 180) | 120 s total; delivery lag ASSUMED, not measured |
| net-prem-ticks / greek-flow per ticker | tape_time / timestamp = bar start | same 120 s | same |
| full tape | executed_at; created_at is within 0.02 s of executed_at (measured, 2026-11-12: ~100% of premium within 1 s) | aggregated to the minute, bar start + 120 s | API availability lag of the live feed NOT measured |
| dark-pool levels, volatility/stats (IV, IV rank, RV), gex levels | daily, computed end of day | 18:05 ET of the file date; London/NY decisions use the PREVIOUS business day only | 1 day |
Thresholds: trailing-20-day mean of the per-day q95/q99 of |change|, shifted one day (no same-day information).
No-look-ahead proof (one sample day per family: feature recomputed from rows truncated at the bar start gives the identical value):
```
F3 tide X d15 up: decision 2026-10-15 10:11:00 ET = bar start 2026-10-15 10:09:00 ET + 60 s bar + 60 s lag; d15 from full array 96246279, from array truncated at the bar start 96246279 (equal: True)
F3 tide X d15 up: decision 2026-10-15 10:12:00 ET = bar start 2026-10-15 10:10:00 ET + 60 s bar + 60 s lag; d15 from full array 113949026, from array truncated at the bar start 113949026 (equal: True)
F3 tide X d15 up: decision 2026-10-15 10:13:00 ET = bar start 2026-10-15 10:11:00 ET + 60 s bar + 60 s lag; d15 from full array 108499587, from array truncated at the bar start 108499587 (equal: True)
F4 SPX net-prem-ticks X d5 up: decision 2026-10-14 10:15:00 ET = bar start 2026-10-14 10:13:00 ET + 120 s; d5 full 67371883 truncated 67371883 (equal: True)
F4 SPX net-prem-ticks X d5 up: decision 2026-10-14 10:16:00 ET = bar start 2026-10-14 10:14:00 ET + 120 s; d5 full 73348700 truncated 73348700 (equal: True)
F4 SPX net-prem-ticks X d5 up: decision 2026-10-14 10:17:00 ET = bar start 2026-10-14 10:15:00 ET + 120 s; d5 full 64660967 truncated 64660967 (equal: True)
F5 IV rank (vol_stats): decision 2026-10-09 10:01:00 ET uses the file of the PREVIOUS business day (computed EOD, usable from 18:05 ET of the file date)
F5 IV rank (vol_stats): decision 2026-10-15 10:01:00 ET uses the file of the PREVIOUS business day (computed EOD, usable from 18:05 ET of the file date)
F5 dark-pool level file 20261106 (end-of-day volume profile) used only from 18:00 ET of that date: levels [np.float64(647.0), np.float64(656.0), np.float64(658.0)]
```

## 3. Unconditional baseline (drift control; every business day at the session start, no trigger) - best cell by recents, n_L6M>=20
| inst | session | table | dir | cell | n L6M | L3M | L6M | HOLD | DD L6M |
|---|---|---|---|---|---|---|---|---|---|
| NQ | asia | base_asia1805 | -1 | Ep3_Sa1_Tnone_XSE | 87 | 1933 | 6495 | 3958 | 27580 |
| NQ | london | base_lon0200 | -1 | Ep3_Sa1_Tnone_XSE | 96 | 3392 | 1411 | 317 | 26717 |
| NQ | pre | base_pre0830 | -1 | Emkt_Sa1_T90_X30 | 126 | 1530 | 1123 | 968 | 8750 |
| NQ | nyam | base_nyam0930 | 1 | Ep10_S30_Tnone_XSE | 121 | 4934 | 2698 | 1659 | 23318 |
| NQ | nypm | base_nypm1200 | -1 | Emkt_S90_Tnone_XSE | 130 | 3369 | 1787 | 1313 | 14780 |
| ES | asia | base_asia1805 | -1 | Eb1_Sa1_Tnone_XSE | 54 | 2576 | 2740 | 1469 | 21659 |
| ES | london | base_lon0200 | 1 | Ep10_Sa2_Tnone_XSE | 53 | 1843 | 612 | 625 | 17419 |
| ES | pre | base_pre0830 | -1 | Emkt_S30_Ta2_X30 | 123 | 698 | 556 | 550 | 6111 |
| ES | nyam | base_nyam1000 | -1 | Eb5_S45_Tnone_XSE | 62 | 791 | 1519 | 1235 | 5385 |
| ES | nypm | base_nypm1200 | -1 | Emkt_S45_Tnone_XSE | 129 | 3132 | 1922 | 705 | 12970 |
| RTY | asia | base_asia1805 | -1 | Eb5_S30_Tnone_XSE | 47 | 464 | 1176 | 876 | 8299 |
| RTY | london | base_lon0200 | 1 | Emkt_S90_Tnone_XSE | 106 | 825 | 666 | 750 | 7877 |
| RTY | pre | base_pre0830 | -1 | Emkt_S45_T45_X120 | 122 | 937 | 761 | 993 | 4518 |
| RTY | nyam | base_nyam1000 | -1 | Eb3_S30_Tnone_XSE | 67 | 1103 | 2417 | 1058 | 10572 |
| RTY | nypm | base_nypm1200 | -1 | Eb1_S30_Tnone_XSE | 64 | 1549 | 1508 | 1083 | 12135 |
Reading: the best unconditional cell in each session already earns hundreds to thousands of $/wk in L6M (a one-way short/long drift over the last months picked from 1,470 cells). A UW trigger book only counts if it clearly beats this, not zero.

## 4. Family null (shifted-time, B draws; statistic = best gated cell recents (L6M+HOLD)/2 with n_L6M>=20, L3M>0, per session)
| null file | draws | asia | london | pre | nyam | nypm |
|---|---|---|---|---|---|---|
| null_F3_ES_shift | 8 | - | - | - | obs 2768 vs q95 3018 p=0.56 | obs 1059 vs q95 1611 p=1.00 |
| null_F3_NQ_shift | 8 | - | - | - | obs 3465 vs q95 4087 p=0.22 | obs 2240 vs q95 2675 p=0.67 |
| null_F4_ES_shift_SPX | 8 | - | - | - | obs 2090 vs q95 3319 p=1.00 | obs 1305 vs q95 1767 p=1.00 |
| null_F4_NQ_shift_NDX | 8 | - | - | - | obs 2233 vs q95 3717 p=1.00 | obs 2226 vs q95 3203 p=0.89 |
| null_F4_NQ_shift_QQQ | 8 | - | - | - | obs 2629 vs q95 3321 p=0.56 | obs 2211 vs q95 2677 p=0.44 |
| null_F5dp_ES_shift | 8 | obs 1740 vs q95 2423 p=0.56 | obs 1203 vs q95 2218 p=1.00 | obs 429 vs q95 668 p=0.78 | obs 1627 vs q95 2250 p=0.67 | obs 761 vs q95 1364 p=1.00 |
| null_F5dp_NQ_shift | 8 | obs 2716 vs q95 4443 p=0.89 | obs 1418 vs q95 2486 p=1.00 | obs 528 vs q95 1305 p=1.00 | obs 2053 vs q95 3246 p=0.78 | obs 1278 vs q95 2456 p=1.00 |
| null_F5iv_ES_shift | 8 | obs 3249 vs q95 3009 p=0.11 | obs 1521 vs q95 1665 p=0.22 | - | obs 2332 vs q95 1790 p=0.11 | - |
| null_F5iv_NQ_shift | 8 | obs 6349 vs q95 5621 p=0.11 | obs 1501 vs q95 2806 p=1.00 | - | obs 2534 vs q95 1886 p=0.11 | - |

## 5. Best book per session (ranked by consistency across L3M/L6M/HOLD over max DD; DD first), with full evidence

### ASIA
| fam | inst | ticker/series | trigger kind | dir | entry/stop/target/time cell | n L6M | L1M | L3M | L6M | HOLD | PRE-UW | DD L6M | DD HOLD | worst wk L6M | stops/wk | pos wk L6M | WF $/wk (DD, pos periods) | placebo shift p | placebo shuffle p | corr stack L6M | stack DD L6M -> with book | idle share |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| F5iv | NQ | QQQ asia1805 | iv_hi | SHORT | Emkt_Sa1_Tnone_XSE | 64 | 10990 | 3937 | 6765 | 4285 | -885 | 10166 | 14376 | -5187 | 1.67 | 0.44 | 111 (13949, 0.34) | 0.09 | 0.09 | 0.32 | 36371 -> 36515 | 0.98 |
| F5iv | NQ | QQQ asia1805 | ivr_hi | SHORT | Emkt_Sa1_Tnone_XSE | 74 | 10990 | 3937 | 8026 | 4673 | -729 | 10166 | 17259 | -5187 | 1.85 | 0.53 | 141 (14471, 0.29) | 0.09 | 0.09 | 0.32 | 36371 -> 36515 | 0.98 |

### LONDON
| fam | inst | ticker/series | trigger kind | dir | entry/stop/target/time cell | n L6M | L1M | L3M | L6M | HOLD | PRE-UW | DD L6M | DD HOLD | worst wk L6M | stops/wk | pos wk L6M | WF $/wk (DD, pos periods) | placebo shift p | placebo shuffle p | corr stack L6M | stack DD L6M -> with book | idle share |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| F5dp | RTY | SPY 3 | touch_dn | LONG | Eb1_S90_Tnone_XSE | 27 | 1193 | 680 | 649 | 591 | nan | 1439 | 1439 | -1439 | 0.22 | 0.75 | 555 (1439, 0.69) | 0.09 | 0.18 | -0.02 | 36371 -> 34150 | 0.24 |
| F5iv | NQ | QQQ lon0200 | vrp_hi | LONG | Emkt_S90_Tnone_X120 | 53 | 529 | 792 | 829 | 647 | 181 | 1922 | 1922 | -1814 | 0.30 | 0.63 | 168 (12029, 0.44) | 0.09 | 0.09 | -0.00 | 36371 -> 38184 | 0.10 |

### PRE
| fam | inst | ticker/series | trigger kind | dir | entry/stop/target/time cell | n L6M | L1M | L3M | L6M | HOLD | PRE-UW | DD L6M | DD HOLD | worst wk L6M | stops/wk | pos wk L6M | WF $/wk (DD, pos periods) | placebo shift p | placebo shuffle p | corr stack L6M | stack DD L6M -> with book | idle share |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| F5dp | NQ | SPY 3 | touch_up | SHORT | Ep3_S30_Ta1_X120 | 30 | 1122 | 783 | 468 | 358 | nan | 2455 | 2455 | -2455 | 0.30 | 0.74 | 253 (1799, 0.69) | 0.09 | 0.09 | -0.09 | 36371 -> 36545 | 0.67 |
| F5dp | RTY | QQQ 3 | touch_dn | SHORT | Emkt_Sa2_T30_X15 | 43 | -27 | 459 | 327 | 274 | nan | 2515 | 2515 | -2515 | 0.15 | 0.79 | 306 (2515, 0.62) | 0.09 | 0.09 | 0.07 | 36371 -> 38885 | 0.56 |

### NYAM
| fam | inst | ticker/series | trigger kind | dir | entry/stop/target/time cell | n L6M | L1M | L3M | L6M | HOLD | PRE-UW | DD L6M | DD HOLD | worst wk L6M | stops/wk | pos wk L6M | WF $/wk (DD, pos periods) | placebo shift p | placebo shuffle p | corr stack L6M | stack DD L6M -> with book | idle share |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| F5iv | RTY | SPX nyam1000 | ivr_lo | SHORT | Eb3_S90_T30_XSE | 42 | 182 | 329 | 457 | 292 | 57 | 528 | 528 | -528 | 0.07 | 0.80 | 38 (10868, 0.47) | 0.09 | 0.09 | -0.04 | 36371 -> 35915 | 0.59 |
| F4 | NQ | QQQ X | flX_d5_q99_up | LONG | Ep5_S90_Tnone_X60 | 23 | 1588 | 854 | 922 | 906 | 131 | 1814 | 2358 | -1814 | 0.19 | 0.80 | 31 (9451, 0.24) | 0.18 | 0.09 | -0.04 | 36371 -> 32304 | 0.60 |
| PAIR | NQ | F4|NDX|X|flX_d1_q95_up F1|NDX|g_vol|d1_up | AND30 | LONG | Emkt_Sa2_Ta2_X60 | 37 | nan | 264 | 448 | 690 | -73 | 5111 | 5111 | -3027 | 0.41 | 0.57 | 201 (6947, 0.47) | 0.45 | 0.18 | -0.20 | 36371 -> 36371 | 0.59 |

### NYPM
| fam | inst | ticker/series | trigger kind | dir | entry/stop/target/time cell | n L6M | L1M | L3M | L6M | HOLD | PRE-UW | DD L6M | DD HOLD | worst wk L6M | stops/wk | pos wk L6M | WF $/wk (DD, pos periods) | placebo shift p | placebo shuffle p | corr stack L6M | stack DD L6M -> with book | idle share |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| F4 | NQ | NDX X | flX_d1_q95_up | SHORT | Emkt_Sa2_Ta1_X60 | 116 | 2192 | 1386 | 1559 | 1340 | -137 | 2268 | 2268 | -1536 | 0.44 | 0.81 | 651 (3950, 0.74) | 0.09 | 0.09 | 0.12 | 36371 -> 35490 | 0.54 |
| F4 | NQ | NDX ncp | flncp_d5_q95_up | SHORT | Ep3_Sa1_T90_XSE | 50 | 1877 | 3468 | 2554 | 1830 | 240 | 2646 | 3537 | -2646 | 0.44 | 0.79 | 118 (20712, 0.38) | 0.09 | 0.09 | 0.08 | 36371 -> 34575 | 0.56 |
| PAIR | NQ | F4|NDX|X|flX_d1_q95_up F1|NDX|g_vol|d1_up | AND30 | SHORT | Ep3_Sa2_T90_X60 | 61 | 647 | 711 | 1429 | 874 | 355 | 983 | 2496 | -983 | 0.11 | 0.84 | 404 (3819, 0.50) | 0.09 | 0.09 | 0.15 | 36371 -> 36195 | 0.57 |

Cell code: E = entry (mkt: market at decision+1 s; b1/b3/b5: after N min only if price moved with the trigger; p3/p5/p10: limit pullback, 15 min), S = stop (points x instrument ATR scale, or aN = N x ATR14 5-min), T = target (none = no target), X = time exit minutes or SE = session end (flat by session end). Lots equal-$-risk R=$1,200.

## 6. Screen coverage
rows in screens (top cells per table x session x direction): inst    ES    NQ   RTY / fam                    / F0      46    47    41 / F3    1049  1063  1066 / F4    2987  3033  2972 / F4T   6847  6961  6897 / F4Z   1352  1382  1364 / F5dp   509   541   525 / F5iv  1161  1199  1183
Full-tape days aggregated so far: 121 (newest first from 2026-11-12). F4T (tape DTE/aggression bursts) screen waits for >= 30 days.
