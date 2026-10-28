# DS3_DIV2_A_AUDIT - where the live stack makes, loses and idles (D3D2A, 2026-10-28). Descriptive; no preregs, no scoring of candidates; research only.

## Plain line

**The stack loses on 438 of 917 days (48%), 64% of the losing-day dollars on range days (ex-post label), in 12 of the 46 active half-hour entry slots that net negative (03:30, 05:00, 05:30, 07:00, 08:00, 11:30, 12:00, 13:00, 14:30, 16:30, 22:00, 23:30 ET; only 03:30 and 16:30 reach |t_week|>=1.8, so most are noise-level) and is idle (no entries) in 6 slots (09:00, 09:30, 15:00, 15:30, 16:00, 16:30 ET, 09:30-10:00 and 15:00-16:30, all of them live-rule entry blocks, not a lack of signals); it is never idle by choice of the signals: every other slot holds >= 1.10% of trades.**

Window used: label days 2023-04-03 .. 2026-10-16 (185 label weeks = X span 2023-04..2024-01 + WF 2024-02..2026-10), 25,898 trades, $7,431,624 total, $40,171/wk mean (WF-only mean reproduces the corrected live baseline $45,947/wk; the 2023 span is weaker, so the 185-week mean is lower). FLAG: this extends past 2026-02-06 because the official corrected-engine WF/HOLD series (DS3_SIZING_VOLSCALE, DS3_BLOCKRULES, D3DVG) run through 2026-10-16 and prior reports read HOLD 2025-07..2026-10; no data beyond what those reports used, nothing from a later untouched span. Anyone applying this audit to a date-bounded study subject to the 2026-02-06 rule must cut the trade table themselves (all rows carry label_day).

## Method (what was fixed)
- Stack = ST10 + HM10 + WT7 + KB/SM/PE(PB3B_R5_P1) at 10 x frozen monthly inverse-26w-SD weights, busy-correct regenerated rows (ST/HM/WT/KB/SM) and PB rows from books.pkl, exact per-book 1-s lock engine (sl_lib.run_book), live entry blocks (09:00-09:59, 15:00-16:54, 18:00-18:04, signals 16:55-18:00), size-dependent sweep cost netted (equal_risk.excess). Trade P&L = engine net x weight - sweep; day sums equal dvg_lib series() to 1e-10; WF mean $45,947.3/wk. Code l2vast/ds3/code/dv2a/ (dv2a_build.py, dv2a_labels.py, audit_lib.py, dv2a_audit.py).
- P&L and trade counts are attributed to the ENTRY time (ET naive, DST-correct since the engine clock is ET). A trade entered in a slot keeps its slot even if it runs into the next session. The per-slot table also shows mean lots OPEN (exposure) so a slot with few entries but an open position is not read as idle.
- Label day = the 18:00 ET (prior evening) to 17:00 ET trading day; weekday, event and day-type labels use the label day (a Sunday-evening Asia trade is a Monday-label trade).
- Day type (ex post, needs the 16:00 close): RTH 09:30-16:00 NQ 1-min; big = |close - open| >= prior-20-day median |close - open|; trend = big and the first hour (09:30-10:30) moved in the final direction; reversal = big and the first-hour move was opposite to the final move; range = not big. Thresholds use only prior days; the LABEL needs the close, so it is EX POST for every trade entered before 16:00. Ex-ante companions: fh_wide (first-hour range >= prior-20d median; known 10:30, usable for entries >= 10:30), fh_rev (first hour closes against the overnight move by > its median range; known 10:30), prev_daytype (yesterday, known at the open).
- Scheduled events, RECONSTRUCTED approximate calendar: FOMC decision days from the published meeting schedule typed from memory 2023-02..2026-09 (28 days in window; not machine-verified); NFP = first Friday of the month (BLS rule; holiday-shifted months not corrected); CPI proxy = in each month, the Tue-Thu between the 10th and 16th (not NFP/FOMC) with the largest 08:30-08:31 NQ range (the 8 first months match the real release dates I know: Apr 12, May 10, Jun 13, Jul 12, Aug 10, Sep 13, Oct 12, Nov 14 2023; later months unchecked); event = FOMC or NFP or CPI. PPI, retail sales, ISM, auctions, EIA are NOT in the calendar.
- VIX: k4/state/vix.csv (daily close) exists on disk; label = previous calendar day close, terciles with in-sample cut points (15.15 / 17.52) over the window (descriptive; cuts are not ex ante). Intraday VIX does not exist (see DS3_DIV2_G_NEEDS.md). A realised-vol tercile (prior-20d mean RTH range/open) is also given. Month-end = last 3 label days of the month; opex week = Mon-Fri of the third Friday.

## Weekly P&L overview
| window | mean $/wk | worst wk | weeks<0 |
|---|---|---|---|
| all 185 wk | 40,171 | -318,557 | 71.00 |
| WF 142 wk (2024-02..) | 45,947 | -318,557 | 54.00 |
| X 2023-04..2024-01 | 21,096 | -157,300 | 17.00 |

## 1. Hour of day (30-min ET entry slot)
Columns: n = trades, share = % of all trades, rel = share / mean active-slot share (46 slots; 1.0 = average), pnl = net $ (sum over window), $/trade, t_wk = t of the weekly slot P&L mean (52-week-ish noise; 46 slots tested, so |t| < 2.5 is not evidence), yrs_neg = calendar years (2023-26) with negative slot P&L, lots open = mean contracts open per minute in the slot.
| slot | n | share % | rel | pnl $ | $/trade | t_wk | yrs_neg | lots open |
|---|---|---|---|---|---|---|---|---|
| 00:00 | 284 | 1.10 | 0.50 | 154,955 | 546 | 0.91 | 2.00 | 24.34 |
| 00:30 | 332 | 1.28 | 0.59 | 219,056 | 660 | 1.39 | 1.00 | 24.14 |
| 01:00 | 400 | 1.54 | 0.71 | 411,034 | 1,028 | 1.97 | 1.00 | 24.15 |
| 01:30 | 394 | 1.52 | 0.70 | 206,631 | 524 | 1.13 | 2.00 | 23.99 |
| 02:00 | 485 | 1.87 | 0.86 | 243,048 | 501 | 1.02 | 0.00 | 23.54 |
| 02:30 | 464 | 1.79 | 0.82 | 151,897 | 327 | 0.68 | 2.00 | 23.29 |
| 03:00 | 670 | 2.59 | 1.19 | 461,238 | 688 | 1.57 | 0.00 | 22.64 |
| 03:30 | 574 | 2.22 | 1.02 | -455,671 | -794 | -1.81 | 3.00 | 22.01 |
| 04:00 | 721 | 2.78 | 1.28 | 200,431 | 278 | 0.76 | 2.00 | 21.50 |
| 04:30 | 529 | 2.04 | 0.94 | 230,178 | 435 | 0.87 | 1.00 | 21.23 |
| 05:00 | 498 | 1.92 | 0.88 | -57,545 | -116 | -0.26 | 2.00 | 21.27 |
| 05:30 | 409 | 1.58 | 0.73 | -79,198 | -194 | -0.38 | 2.00 | 21.47 |
| 06:00 | 382 | 1.48 | 0.68 | 222,789 | 583 | 1.11 | 2.00 | 21.59 |
| 06:30 | 378 | 1.46 | 0.67 | 193,498 | 512 | 1.05 | 2.00 | 21.38 |
| 07:00 | 470 | 1.81 | 0.83 | -15,878 | -33.78 | -0.07 | 3.00 | 20.53 |
| 07:30 | 431 | 1.66 | 0.77 | 206,517 | 479 | 1.04 | 1.00 | 20.41 |
| 08:00 | 505 | 1.95 | 0.90 | -62,370 | -124 | -0.30 | 2.00 | 19.96 |
| 08:30 | 895 | 3.46 | 1.59 | 169,983 | 190 | 0.51 | 1.00 | 17.23 |
| 09:00 | 12.00 | 0.05 | 0.02 | 11,655 | 971 | 0.31 | 2.00 | 15.45 |
| 10:00 | 1,819 | 7.02 | 3.23 | 599,664 | 330 | 1.25 | 1.00 | 7.60 |
| 10:30 | 1,176 | 4.54 | 2.09 | 608,817 | 518 | 1.66 | 1.00 | 9.40 |
| 11:00 | 895 | 3.46 | 1.59 | 376,874 | 421 | 1.30 | 0.00 | 9.81 |
| 11:30 | 798 | 3.08 | 1.42 | -130,334 | -163 | -0.48 | 2.00 | 10.27 |
| 12:00 | 645 | 2.49 | 1.15 | -14,107 | -21.87 | -0.06 | 3.00 | 10.33 |
| 12:30 | 591 | 2.28 | 1.05 | 195,763 | 331 | 0.86 | 1.00 | 10.51 |
| 13:00 | 511 | 1.97 | 0.91 | -44,935 | -87.94 | -0.24 | 2.00 | 9.77 |
| 13:30 | 482 | 1.86 | 0.86 | 151,804 | 315 | 0.74 | 2.00 | 9.55 |
| 14:00 | 470 | 1.81 | 0.83 | 137,422 | 292 | 0.77 | 2.00 | 9.14 |
| 14:30 | 500 | 1.93 | 0.89 | -211,616 | -423 | -1.31 | 3.00 | 8.89 |
| 16:30 | 17.00 | 0.07 | 0.03 | -3,393 | -200 | -2.04 | 3.00 | 3.68 |
| 18:00 | 1,844 | 7.12 | 3.28 | 726,145 | 394 | 1.36 | 1.00 | 4.92 |
| 18:30 | 1,338 | 5.17 | 2.38 | 334,232 | 250 | 0.87 | 1.00 | 12.97 |
| 19:00 | 1,027 | 3.97 | 1.82 | 658,428 | 641 | 1.95 | 1.00 | 18.14 |
| 19:30 | 692 | 2.67 | 1.23 | 166,898 | 241 | 0.71 | 1.00 | 20.66 |
| 20:00 | 831 | 3.21 | 1.48 | 438,435 | 528 | 1.42 | 1.00 | 21.37 |
| 20:30 | 721 | 2.78 | 1.28 | 306,309 | 425 | 1.09 | 1.00 | 22.03 |
| 21:00 | 623 | 2.41 | 1.11 | 126,416 | 203 | 0.51 | 2.00 | 22.85 |
| 21:30 | 513 | 1.98 | 0.91 | 295,768 | 577 | 1.28 | 1.00 | 23.23 |
| 22:00 | 510 | 1.97 | 0.91 | -169,035 | -331 | -0.67 | 2.00 | 23.66 |
| 22:30 | 391 | 1.51 | 0.69 | 349,811 | 895 | 1.75 | 3.00 | 24.01 |
| 23:00 | 343 | 1.32 | 0.61 | 125,469 | 366 | 0.78 | 2.00 | 24.32 |
| 23:30 | 328 | 1.27 | 0.58 | -5,456 | -16.63 | -0.03 | 3.00 | 24.35 |

Net-negative slots (12): 03:30, 05:00, 05:30, 07:00, 08:00, 11:30, 12:00, 13:00, 14:30, 16:30, 22:00, 23:30. Their total $-1,249,539, vs $7,431,624 overall; the slot P&L is positive in all other slots. Of these, those negative in >= 3 of 4 years: 03:30, 07:00, 12:00, 14:30, 16:30, 23:30.
Idle slots (entry share < 10% of the mean slot share): 09:00, 09:30, 15:00, 15:30, 16:00, 16:30; these are exactly the live entry blocks (09:00-09:59 incl. the 12 PB rows at 09:00; 15:00-16:54, with 17 PB rows at 16:30). Thin slots (< 50%): 09:00, 09:30, 15:00, 15:30, 16:00, 16:30 (identical set). No-edge slots (weekly t < 1.0, i.e. net negative or indistinguishable from 0): 00:00, 02:30, 03:30, 04:00, 04:30, 05:00, 05:30, 07:00, 08:00, 08:30, 09:00, 11:30, 12:00, 12:30, 13:00, 13:30, 14:00, 14:30, 16:30, 18:30, 19:30, 21:00, 22:00, 23:00, 23:30. All helper sets are exported by audit_lib.
Thinnest traded slots: 09:00 (12 tr, 0.02x), 16:30 (17 tr, 0.03x), 00:00 (284 tr, 0.50x), 23:30 (328 tr, 0.58x), 00:30 (332 tr, 0.59x), 23:00 (343 tr, 0.61x). So: the stack is not idle at lunch or at night by entries; it trades fewer, lower-expectancy trades there (11:30-14:30 net $83,996 on 3997 trades = $21/trade vs $287/trade overall).

## 2. Session (entry time)
| session | n | pnl $ | $/trade | trade % | P&L share % | worst-20-wk $ | worst-20 share % |
|---|---|---|---|---|---|---|---|
| Asia | 10,571 | 4,345,094 | 411 | 40.82 | 58.47 | -1,175,763 | 31.48 |
| Europe | 6,516 | 1,238,934 | 190 | 25.16 | 16.67 | -1,140,047 | 30.52 |
| PreUS | 907 | 181,638 | 200 | 3.50 | 2.44 | -292,724 | 7.84 |
| RTH1_0930_1030 | 1,819 | 599,664 | 330 | 7.02 | 8.07 | -311,424 | 8.34 |
| RTH2_1030_1200 | 2,869 | 855,357 | 298 | 11.08 | 11.51 | -344,949 | 9.24 |
| RTH3_1200_1400 | 2,229 | 288,525 | 129 | 8.61 | 3.88 | -439,186 | 11.76 |
| RTH4_1400_1530 | 970 | -74,195 | -76.49 | 3.75 | -1.00 | -31,067 | 0.83 |
| Close_1530_1600 | 0.00 | 0.00 | 0.00 | 0.00 | 0.00 | 0.00 | -0.00 |
| Post_1600_1800 | 17.00 | -3,393 | -200 | 0.07 | -0.05 | 82.86 | -0.00 |
| TOTAL | 25,898 | 7,431,624 | 287 | 100 | 100 | -3,735,079 | 100 |
RTH1 (09:30-10:30) holds only entries 10:00-10:29 (the 09:30-09:59 entry window is blocked live). Post_1600_1800 = 17 PB rows at 16:30. Entries 15:00-16:54 do not exist.

## 3. Day type (ex-post label; +ex-ante companions)
| daytype | days | mean $/day | sum $ | losing days | losing day % |
|---|---|---|---|---|---|
| range | 440 | -9,494 | -4,177,402 | 262 | 59.55 |
| reversal | 63.00 | 14,044 | 884,780 | 23.00 | 36.51 |
| trend | 378 | 27,381 | 10,349,915 | 136 | 35.98 |

P&L by session x day type (entry session; ex-post day type, so the night rows are labeled by the SAME label day RTH, i.e. a night trade is classified with information it did not have):
| session | range | reversal | trend |
|---|---|---|---|
| Asia | 1,528,100 | 4,194 | 2,337,169 |
| Europe | -19,947 | 222,335 | 1,206,589 |
| PreUS | -249,349 | 20,803 | 400,865 |
| RTH1_0930_1030 | -1,096,309 | -264,846 | 1,938,116 |
| RTH2_1030_1200 | -2,434,340 | 402,163 | 2,822,103 |
| RTH3_1200_1400 | -1,426,936 | 430,668 | 1,313,504 |
| RTH4_1400_1530 | -478,725 | 69,463 | 335,067 |
| Close_1530_1600 | 0.00 | 0.00 | 0.00 |
| Post_1600_1800 | 105 | 0.00 | -3,498 |

By first-hour range vs 20d median (known 10:30):
| fh_wide | days | mean | sum | loss_day_pct |
|---|---|---|---|---|
| FHnarrow | 430 | 18.49 | 7,951 | 53.02 |
| FHwide | 451 | 15,630 | 7,049,342 | 42.79 |

By first-hour reversal of the overnight move (known 10:30):
| fh_rev | days | mean | sum | loss_day_pct |
|---|---|---|---|---|
| FHrev | 73.00 | 32,886 | 2,400,674 | 36.99 |
| no | 844 | 5,961 | 5,030,951 | 48.70 |

By previous day type (known at the open):
| prev_daytype | days | mean | sum | loss_day_pct |
|---|---|---|---|---|
| range | 440 | 10,251 | 4,510,623 | 46.36 |
| reversal | 63.00 | 7,768 | 489,390 | 42.86 |
| trend | 378 | 4,906 | 1,854,514 | 50.53 |

Entries 10:30-16:00 by first-hour width (ex ante for these entries):
| fh_wide | n | pnl | per |
|---|---|---|---|
| FHnarrow | 2,942 | 281,515 | 95.69 |
| FHwide | 3,060 | 751,451 | 246 |

... by first-hour reversal label (D section reversal-day book trigger):
| fh_rev | n | pnl | per |
|---|---|---|---|
| FHrev | 491 | 323,769 | 659 |
| no | 5,511 | 709,198 | 129 |

## 4. Scheduled-event days (RECONSTRUCTED calendar), weekday, VIX, month-end, opex
|  | days | mean | sum | loss_day_pct |
|---|---|---|---|---|
| event=False | 803 | 9,021 | 7,243,828 | 46.58 |
| event=True | 114 | 1,647 | 187,796 | 56.14 |

| group | days | mean $/day | sum $ | losing day % |
|---|---|---|---|---|
| event=True | 114 | 1,647 | 187,796 | 56.14 |
| event=False | 803 | 9,021 | 7,243,828 | 46.58 |
| fomc=True | 28.00 | -8,703 | -243,678 | 60.71 |
| fomc=False | 889 | 8,634 | 7,675,302 | 47.36 |
| nfp=True | 43.00 | 3,897 | 167,590 | 53.49 |
| nfp=False | 874 | 8,311 | 7,264,035 | 47.48 |
| cpi=True | 43.00 | 6,137 | 263,884 | 55.81 |
| cpi=False | 874 | 8,201 | 7,167,741 | 47.37 |
| monthend=True | 126 | 10,045 | 1,265,674 | 46.03 |
| monthend=False | 791 | 7,795 | 6,165,950 | 48.04 |
| opexweek=True | 214 | 9,679 | 2,071,389 | 45.79 |
| opexweek=False | 703 | 7,625 | 5,360,235 | 48.36 |
| opexday=True | 42.00 | 22,758 | 955,850 | 35.71 |
| opexday=False | 875 | 7,401 | 6,475,775 | 48.34 |

Weekday (label day):
| wdname | days | mean | sum | loss_day_pct |
|---|---|---|---|---|
| Mon | 183 | 12,214 | 2,235,083 | 45.90 |
| Tue | 185 | 12,501 | 2,312,659 | 45.95 |
| Wed | 183 | 2,827 | 517,289 | 49.73 |
| Thu | 183 | 4,125 | 754,920 | 52.46 |
| Fri | 183 | 8,807 | 1,611,673 | 44.81 |

vix_terc (daily; VIX prev-day close, in-sample cuts; rv = prior-20d range):
| vix_terc | days | mean | sum | loss_day_pct |
|---|---|---|---|---|
| VIX_high | 306 | 7,099 | 2,172,426 | 48.69 |
| VIX_low | 307 | 11,877 | 3,646,150 | 44.63 |
| VIX_mid | 304 | 5,306 | 1,613,049 | 50.00 |

rv_terc (daily; VIX prev-day close, in-sample cuts; rv = prior-20d range):
| rv_terc | days | mean | sum | loss_day_pct |
|---|---|---|---|---|
| RV_high | 306 | 5,509 | 1,685,676 | 50.65 |
| RV_low | 306 | 14,356 | 4,392,973 | 42.16 |
| RV_mid | 305 | 4,436 | 1,352,975 | 50.49 |

## 5. The 20 worst weeks
| wk | stack $ | HM | KB | PE | SM | ST | WT | first day | trend days | event days |
|---|---|---|---|---|---|---|---|---|---|---|
| 202528 | -318,557 | -76,800 | -32,054 | -31,852 | 6,206 | -120,438 | -63,620 | 20,250,707 | 0.00 | 0.00 |
| 202411 | -306,664 | -56,138 | -50,922 | -97,217 | 2,928 | -56,984 | -48,330 | 20,240,311 | 3.00 | 1.00 |
| 202440 | -276,717 | -101,848 | 354 | -54,006 | -44,090 | -44,566 | -32,560 | 20,240,930 | 1.00 | 1.00 |
| 202621 | -253,955 | -114,514 | -15,872 | -56,120 | 26,017 | -63,746 | -29,718 | 20,260,518 | 2.00 | 0.00 |
| 202447 | -242,171 | -38,298 | -3,760 | -76,723 | -29,394 | -44,807 | -49,189 | 20,241,118 | 1.00 | 0.00 |
| 202530 | -207,162 | -40,112 | -31,673 | -12,350 | 14,951 | -92,286 | -45,691 | 20,250,721 | 2.00 | 0.00 |
| 202549 | -204,132 | -30,144 | -52,083 | 267 | 8,458 | -121,471 | -9,158 | 20,251,201 | 1.00 | 1.00 |
| 202604 | -185,098 | -91,240 | 15,137 | -56,476 | -3,839 | -39,137 | -9,543 | 20,260,119 | 2.00 | 0.00 |
| 202418 | -166,960 | -83,049 | 10,834 | -22,984 | -27,014 | -52,127 | 7,379 | 20,240,429 | 1.00 | 2.00 |
| 202434 | -163,818 | -42,550 | -60,067 | -28,803 | -220 | -43,965 | 11,787 | 20,240,819 | 2.00 | 0.00 |
| 202314 | -157,300 | -9,967 | -39,474 | -31,397 | -10,134 | -24,887 | -41,440 | 20,230,403 | 2.00 | 1.00 |
| 202333 | -153,954 | -25,628 | -78,565 | -12,007 | 7,052 | -14,957 | -29,849 | 20,230,814 | 4.00 | 0.00 |
| 202319 | -150,936 | -42,592 | -30,818 | 1,924 | 3,187 | -55,668 | -26,969 | 20,230,508 | 1.00 | 1.00 |
| 202335 | -149,477 | -8,516 | -44,545 | -13,925 | -6,136 | -39,806 | -36,549 | 20,230,828 | 1.00 | 1.00 |
| 202624 | -141,263 | -86,160 | -18,407 | 27,656 | 24,312 | -37,397 | -51,267 | 20,260,608 | 2.00 | 1.00 |
| 202331 | -138,873 | 3,428 | -3,662 | -40,860 | 5,293 | -68,920 | -34,153 | 20,230,731 | 2.00 | 1.00 |
| 202326 | -138,446 | -15,256 | -34,944 | -13,599 | -1,167 | -63,942 | -9,538 | 20,230,626 | 1.00 | 0.00 |
| 202316 | -134,210 | -20,953 | -9,398 | -55,074 | 18,588 | -19,031 | -48,341 | 20,230,417 | 2.00 | 0.00 |
| 202636 | -123,371 | -32,051 | 11,225 | 6,763 | -11,810 | -62,591 | -34,907 | 20,260,831 | 1.00 | 1.00 |
| 202635 | -122,015 | -9,210 | 17,819 | -19,490 | 32,522 | -107,848 | -35,808 | 20,260,824 | 1.00 | 0.00 |

Worst-20 total $-3,735,079 (average -186,754/wk) = 59% of all negative-week dollars ($-6,349,843 over 71 negative weeks). Years: {2023: 7, 2024: 5, 2025: 3, 2026: 5}.

Per-book contribution to the 20 worst weeks (book-level week sums; the stack week is the sum):
| book | worst-20 $ | share of worst-20 % | all-weeks $ | worst-20 / all-weeks |
|---|---|---|---|---|
| ST | -1,174,576 | 31.45 | 1,863,321 | -0.63 |
| HM | -921,600 | 24.67 | 1,611,247 | -0.57 |
| WT | -617,465 | 16.53 | 314,989 | -1.96 |
| PE | -586,273 | 15.70 | 1,298,244 | -0.45 |
| KB | -450,875 | 12.07 | 1,442,177 | -0.31 |
| SM | 15,710 | -0.42 | 901,646 | 0.02 |

Worst-20-week P&L by entry slot (10 worst and 5 best slots; full table slot_table.csv):
| slot | n | worst-20 $ | rest $ | worst20 $/tr | share of w20 loss % |
|---|---|---|---|---|---|
| 10:00 | 197 | -311,424 | 911,088 | -1,581 | 8.34 |
| 18:00 | 191 | -293,492 | 1,019,637 | -1,537 | 7.86 |
| 08:30 | 92.00 | -276,061 | 446,044 | -3,001 | 7.39 |
| 22:00 | 60.00 | -260,056 | 91,021 | -4,334 | 6.96 |
| 12:30 | 62.00 | -231,690 | 427,453 | -3,737 | 6.20 |
| 11:30 | 72.00 | -228,039 | 97,705 | -3,167 | 6.11 |
| 20:00 | 79.00 | -218,059 | 656,494 | -2,760 | 5.84 |
| 04:00 | 65.00 | -199,884 | 400,315 | -3,075 | 5.35 |
| 05:30 | 44.00 | -155,248 | 76,050 | -3,528 | 4.16 |
| 02:00 | 49.00 | -137,822 | 380,870 | -2,813 | 3.69 |
| 16:30 | 1.00 | 82.86 | -3,476 | 82.86 | -0.00 |
| 00:30 | 37.00 | 15,953 | 203,103 | 431 | -0.43 |
| 02:30 | 37.00 | 23,811 | 128,086 | 644 | -0.64 |
| 22:30 | 37.00 | 47,049 | 302,761 | 1,272 | -1.26 |
| 01:00 | 31.00 | 51,862 | 359,171 | 1,673 | -1.39 |

Worst-20 losses by session (see session table): Asia -1,175,763, Europe -1,140,047, PreUS -292,724, RTH1_0930_1030 -311,424, RTH2_1030_1200 -344,949, RTH3_1200_1400 -439,186, RTH4_1400_1530 -31,067, Close_1530_1600 0, Post_1600_1800 83.

Days inside the 20 worst weeks, by day type (ex post):
| daytype | days | sum | mean | day share % (all window) |
|---|---|---|---|---|
| na | 2.00 | 28,103 | 14,051 | nan |
| range | 61.00 | -2,481,519 | -40,681 | 49.94 |
| reversal | 5.00 | -273,815 | -54,763 | 7.15 |
| trend | 32.00 | -1,007,847 | -31,495 | 42.91 |
80 of 100 days inside the worst-20 weeks lose; the 15 worst single days of the window:
| label_day | pnl | daytype | wdname | fh_wide | event | vix_terc |
|---|---|---|---|---|---|---|
| 20251121 | -138,774 | range | Fri | FHwide | False | VIX_high |
| 20240820 | -137,641 | range | Tue | FHnarrow | False | VIX_low |
| 20240501 | -135,656 | range | Wed | FHnarrow | True | VIX_mid |
| 20241002 | -135,529 | range | Wed | FHwide | False | VIX_high |
| 20240311 | -134,797 | range | Mon | FHwide | False | VIX_low |
| 20260720 | -128,148 | trend | Mon | FHnarrow | False | VIX_high |
| 20250605 | -120,563 | trend | Thu | FHnarrow | False | VIX_high |
| 20251210 | -120,116 | reversal | Wed | FHnarrow | True | VIX_mid |
| 20250926 | -118,590 | range | Fri | FHwide | False | VIX_mid |
| 20250327 | -118,199 | range | Thu | FHnarrow | False | VIX_high |
| 20260123 | -116,053 | trend | Fri | FHwide | False | VIX_mid |
| 20250514 | -113,562 | range | Wed | FHnarrow | False | VIX_high |
| 20240408 | -111,199 | range | Mon | FHnarrow | False | VIX_mid |
| 20251118 | -111,076 | range | Tue | FHwide | False | VIX_high |
| 20230928 | -110,739 | trend | Thu | FHwide | False | VIX_high |

Books on the 15 worst days: HM -471,751, ST -459,853, SM -262,355, PE -254,945, KB -209,922, WT -191,814.

## 6. Book x session P&L ($, whole window)
| book | Asia | Europe | PreUS | RTH1_0930_1030 | RTH2_1030_1200 | RTH3_1200_1400 | RTH4_1400_1530 | Close_1530_1600 | Post_1600_1800 | TOTAL |
|---|---|---|---|---|---|---|---|---|---|---|
| HM | 1,419,786 | 300,963 | -133,086 | 45,478 | 171,794 | -128,250 | -62,886 | 0.00 | -2,551 | 1,611,247 |
| KB | 538,888 | 260,308 | 18,159 | 221,977 | 113,071 | 277,184 | 14,224 | 0.00 | -1,633 | 1,442,177 |
| PE | 669,377 | 198,323 | -30,297 | 39,003 | 302,271 | 74,809 | 44,758 | 0.00 | 0.00 | 1,298,244 |
| SM | 482,324 | 184,142 | 65,540 | 99,554 | 100,767 | -87,938 | 57,258 | 0.00 | 0.00 | 901,646 |
| ST | 705,107 | 237,713 | 256,347 | 228,529 | 114,123 | 305,326 | 16,176 | 0.00 | 0.00 | 1,863,321 |
| WT | 529,613 | 57,486 | 4,977 | -34,876 | 53,331 | -152,607 | -143,725 | 0.00 | 791 | 314,989 |

Trades:
| book | Asia | Europe | PreUS | RTH1_0930_1030 | RTH2_1030_1200 | RTH3_1200_1400 | RTH4_1400_1530 | Close_1530_1600 | Post_1600_1800 |
|---|---|---|---|---|---|---|---|---|---|
| HM | 1668 | 983 | 117 | 238 | 442 | 384 | 162 | 0 | 6 |
| KB | 1953 | 1009 | 155 | 369 | 581 | 422 | 170 | 0 | 8 |
| PE | 1819 | 1070 | 171 | 282 | 535 | 423 | 168 | 0 | 0 |
| SM | 678 | 651 | 91 | 146 | 175 | 144 | 83 | 0 | 0 |
| ST | 1793 | 1008 | 175 | 451 | 481 | 314 | 137 | 0 | 0 |
| WT | 2660 | 1795 | 198 | 333 | 655 | 542 | 250 | 0 | 3 |

## 7. Reading and what the DIV2 agents should take
- Overnight (Asia + Europe + pre-US, entries 18:00-09:30) = 78% of P&L from 69% of trades; RTH entries (10:00-15:00) = 22% of P&L. The stack is long volatility-at-the-open: 18:00-19:30 and 10:00-11:30 are its engines (slot rel 1.4-3.3x).
- The stack has NO entries 09:30-10:00 and 15:00-16:54 (rules). A candidate that trades 09:30-10:00 or 15:00-16:00 is disjoint by construction (the stack carries open positions through those minutes though: see lots open); score it separately from candidates in traded-but-weak hours.
- Traded-but-weak hours: 03:30 (the single largest net-negative slot, -$456k, negative in how many years: see table), 11:30, 14:30 and 22:00, plus the 05:00-05:30, 08:00 pocket. Each is a mined slot out of 46; treat the loss-slot set as a place to look for hedges, not as proof of a structural leak (only 03:30 and 16:30 have |t_wk| near 2).
- Worst weeks are dominated by trend/impulse regimes in which the trend books (ST/HM/KB) take losses together: see the per-book table; use audit_lib.worst20() and weekly_of() to score any candidate in exactly these weeks.