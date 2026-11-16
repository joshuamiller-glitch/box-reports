# DS3_DD_HOLD - HOLD-window drawdown target (W-PM), built 2026-11-16 16:32Z

VERDICT (data ends 2026-10-30; plain; FIRST PASS, decomposition only, lead rows partly pending): the HOLD max drawdown (-$74.4k, 20251117 to 20251210, 17 trading days) is a book-wide bleed, not one trade or one event: K7 -$30.4k, U7 -$23.3k (26 trades), P7 -$12.2k, M7 -$9.9k, H7 -$5.4k; 128 state cuts (-$127k) and 65 early cuts (-$69k) outrun 136 targets (+$197k) while 33 full stops cost -$68k; Asia -$32.8k and London -$29.0k; the 16 path days lose steadily (12 of 16 net negative; the winners are 11-20, 11-26, 11-28, 12-05) with the FOMC day 12-10 alone -$22.4k (30% of the path: U7 -$14.1k, Asia session -$19.4k, full stops -$16.5k), and the state cuts are not the cause (the same trades held to the raw bracket lose $133k vs the cut result $112k in the path; no-cut runs on other bases show the same path); otherwise it is not a trend-day problem (range days -$31.9k, mixed -$28.5k, trend -$14.0k; against-the-day-direction trades -$53.5k) and the chop call did not flag most of it (calls flagged 93 of 372 trades). Of the leads, only the W-LR London skip rows have HOLD months on JL2 so far: the London skip (LS1 / LS125) does not cut the HOLD DD at any k (W-LR true points vs the 74,402 reference: k=1.25 +0.8%, k=1.5 -5.1%, k=1 +3.0% with a negative mean; my cells LS1_MP -5.1% and LS125_MP -8.6%), the random controls are not valid (W-LR found a per-second redraw, keep share 0.87-0.92 vs 0.60-0.73), status Off/Shadow; every other owner row is pending (no HOLD months on JL2 yet).

BASIS: base = TL3_EV_JN05W2JL2 (JN05W2 + JN04 London same-side cap 6 + ev panel; data end 2026-10-30; OLD-BASE label: it still lacks the P7 post-exit blackout, ATR-SKIP, NKD take, per W-EV), HOLD = 2025-11-01..2026-04-30 (6 months, 3,219 trades, net $216.1k = $8.36k/wk, max DD $74.4k, worst week $-31,211), base lots (live x1.75), engine fee $1.18/contract RT; "@4.84" columns reprice at $4.84 RT (delta contracts x $3.66). HOLD has no W44. Day = Globex label (exit ET + 6h).

Day-type definitions (hindsight labels for description only, from NQ 1-min mid by Globex day): TREND = |close-open| >= 0.45 x day range and range >= the median range of the previous 20 days; RANGE = |close-open| < 0.25 x range; MIXED = the rest. "with/against" = trade side vs the day close-open direction. CHOP CALL = W-CH1 walk-forward call chop_flag for that day and session (version K7_90_f33, chop_bucket_calls_through_20261111.parquet). TD CALL = W-TD trend_call_intervals (a trade entered inside a call interval is with or against the call side, none otherwise). EVENT = event_flags ev_day_any. Replacement = second or later entry of the same book in the same session; ssr = same side as the last closed trade of that session when it lost.

## 1. The drawdown path
Peak 20251117 (equity high) to trough 20251210; 372 trades, net $-74,402 over 16 trading days. Daily P&L inside the path (Globex label): 20251118: -3.1k, 20251119: -2.7k, 20251120: +2.7k, 20251121: -9.1k, 20251124: -10.8k, 20251125: -3.0k, 20251126: +8.2k, 20251128: +2.9k, 20251201: -4.5k, 20251202: -8.1k, 20251203: -8.8k, 20251204: -14.3k, 20251205: +4.6k, 20251208: -2.5k, 20251209: -3.2k, 20251210: -22.4k

HOLD drawdown episodes (peak, trough, depth, recovery):
| peak_day | trough_day | dd | recovered |
|--|--|--|--|
| 20,251,117 | 20,251,210 | -74,402 | 20,260,106 |
| 20,260,303 | 20,260,325 | -54,615 | 20,260,414 |
| 20,260,202 | 20,260,217 | -44,520 | 20,260,302 |
| 20,260,120 | 20,260,123 | -32,821 | 20,260,202 |

Six worst HOLD weeks: 2025-12-01/2025-12-07 -31.2k; 2026-03-23/2026-03-29 -30.9k; 2026-02-02/2026-02-08 -22.9k; 2026-01-19/2026-01-25 -14.4k; 2026-04-06/2026-04-12 -13.2k; 2026-03-16/2026-03-22 -7.6k

## 2. Decomposition of the peak-to-trough trades vs all HOLD trades (net $, loss $, share of trades, mean per trade)

### Book
| book | n path | net path $ | loss path $ | mean/trade path | n HOLD | mean/trade HOLD | n share path % | n share HOLD % |
|--|--|--|--|--|--|--|--|--|
| K7 | 138 | -30,380 | -87,919 | -220 | 1265 | 52 | 37 | 39 |
| U7 | 26 | -23,297 | -44,871 | -896 | 213 | 49 | 7 | 7 |
| P7 | 84 | -12,168 | -64,931 | -145 | 648 | 171 | 23 | 20 |
| M7 | 83 | -9,926 | -45,890 | -120 | 686 | 4 | 22 | 21 |
| H7 | 18 | -5,409 | -17,402 | -300 | 134 | -139 | 5 | 4 |
| O7 | 3 | 2,866 | -731 | 955 | 62 | 383 | 1 | 2 |
| A7 | 20 | 3,912 | -9,275 | 196 | 211 | 101 | 5 | 7 |

### Session
| sess | n path | net path $ | loss path $ | mean/trade path | n HOLD | mean/trade HOLD | n share path % | n share HOLD % |
|--|--|--|--|--|--|--|--|--|
| asia | 147 | -32,791 | -126,304 | -223 | 1270 | 134 | 40 | 39 |
| london | 151 | -28,983 | -98,519 | -192 | 1180 | 32 | 41 | 37 |
| nyam | 59 | -9,069 | -34,245 | -154 | 606 | 37 | 16 | 19 |
| nypm | 15 | -3,559 | -11,951 | -237 | 163 | -83 | 4 | 5 |

### Exit type (stops, full stops = Stop/StopJoin/StopJoinFallback; cuts = StateCut/EarlyCut/StackCut)
| exit_name | n path | net path $ | loss path $ | mean/trade path | n HOLD | mean/trade HOLD | n share path % | n share HOLD % |
|--|--|--|--|--|--|--|--|--|
| StateCut | 128 | -127,478 | -127,478 | -996 | 1056 | -1,060 | 34 | 33 |
| EarlyCut | 65 | -68,627 | -68,627 | -1,056 | 439 | -1,029 | 17 | 14 |
| StopJoin | 14 | -30,361 | -30,361 | -2,169 | 92 | -2,114 | 4 | 3 |
| StopJoinFallback | 5 | -19,379 | -19,379 | -3,876 | 42 | -2,541 | 1 | 1 |
| Stop | 14 | -18,079 | -18,079 | -1,291 | 129 | -1,308 | 4 | 4 |
| StackCut | 7 | -6,198 | -6,198 | -885 | 48 | -833 | 2 | 1 |
| BookLock | 1 | -696 | -696 | -696 | 34 | -432 | 0 | 1 |
| TimeBlock | 2 | -202 | -202 | -101 | 19 | -17 | 1 | 1 |
| Target | 136 | 196,618 | 0 | 1,446 | 1357 | 1,703 | 37 | 42 |

### Day type (hindsight)
| dtype | n path | net path $ | loss path $ | mean/trade path | n HOLD | mean/trade HOLD | n share path % | n share HOLD % |
|--|--|--|--|--|--|--|--|--|
| range | 103 | -31,901 | -76,857 | -310 | 945 | 73 | 28 | 29 |
| mixed | 161 | -28,524 | -122,632 | -177 | 1028 | -28 | 43 | 32 |
| trend | 108 | -13,977 | -71,531 | -129 | 1246 | 141 | 29 | 39 |

### Trade side vs day direction
| with_day | n path | net path $ | loss path $ | mean/trade path | n HOLD | mean/trade HOLD | n share path % | n share HOLD % |
|--|--|--|--|--|--|--|--|--|
| against | 167 | -53,526 | -125,460 | -321 | 1360 | -120 | 45 | 42 |
| with | 205 | -20,876 | -145,560 | -102 | 1859 | 204 | 55 | 58 |

### W-CH1 chop call at that day and session (1 = chop called)
| chop_call | n path | net path $ | loss path $ | mean/trade path | n HOLD | mean/trade HOLD | n share path % | n share HOLD % |
|--|--|--|--|--|--|--|--|--|
| 0 | 278 | -67,889 | -211,758 | -244 | 1,866 | 73 | 75 | 58 |
| 1 | 93 | -7,712 | -59,261 | -83 | 1,350 | 58 | 25 | 42 |

### W-TD trend call at entry
| td_call | n path | net path $ | loss path $ | mean/trade path | n HOLD | mean/trade HOLD | n share path % | n share HOLD % |
|--|--|--|--|--|--|--|--|--|
| none | 360 | -72,234 | -262,858 | -201 | 2745 | 76 | 97 | 85 |
| with | 6 | -3,358 | -5,755 | -560 | 339 | 68 | 2 | 11 |
| against | 6 | 1,190 | -2,407 | 198 | 135 | -121 | 2 | 4 |

### Event day
| event | n path | net path $ | loss path $ | mean/trade path | n HOLD | mean/trade HOLD | n share path % | n share HOLD % |
|--|--|--|--|--|--|--|--|--|
| 1 | 205 | -42,274 | -150,773 | -206 | 1,338 | 71 | 55 | 42 |
| 0 | 167 | -32,127 | -120,246 | -192 | 1,881 | 64 | 45 | 58 |

### Lots
| lotb | n path | net path $ | loss path $ | mean/trade path | n HOLD | mean/trade HOLD | n share path % | n share HOLD % |
|--|--|--|--|--|--|--|--|--|
| 4-6 | 18 | -46,273 | -54,664 | -2,571 | 192 | -215 | 5 | 6 |
| 1 | 297 | -22,207 | -157,675 | -75 | 2444 | 49 | 80 | 77 |
| 2-3 | 57 | -5,922 | -58,680 | -104 | 554 | 187 | 15 | 17 |

### Entry hour ET (loss makers)
| ehour | n path | net path $ | loss path $ | mean/trade path | n HOLD | mean/trade HOLD | n share path % | n share HOLD % |
|--|--|--|--|--|--|--|--|--|
| 18 | 29 | -16,512 | -28,500 | -569 | 277 | 84 | 8 | 9 |
| 5 | 18 | -16,075 | -18,473 | -893 | 173 | 60 | 5 | 5 |
| 23 | 15 | -13,229 | -20,422 | -882 | 98 | -440 | 4 | 3 |
| 11 | 19 | -9,847 | -14,642 | -518 | 212 | -177 | 5 | 7 |
| 1 | 18 | -9,574 | -19,164 | -532 | 148 | 283 | 5 | 5 |
| 6 | 19 | -8,140 | -14,139 | -428 | 152 | -50 | 5 | 5 |
| 3 | 25 | -6,925 | -17,715 | -277 | 202 | -99 | 7 | 6 |
| 0 | 14 | -6,352 | -12,341 | -454 | 102 | 85 | 4 | 3 |
| 12 | 8 | -5,715 | -9,312 | -714 | 68 | -231 | 2 | 2 |
| 22 | 11 | -3,704 | -8,494 | -337 | 127 | 183 | 3 | 4 |
| 7 | 21 | -2,715 | -15,897 | -129 | 177 | 215 | 6 | 5 |
| 10 | 37 | -2,088 | -18,872 | -56 | 332 | 110 | 10 | 10 |
| 8 | 14 | -2,048 | -8,042 | -146 | 76 | -438 | 4 | 2 |
| 13 | 4 | 563 | -1,834 | 141 | 59 | -22 | 1 | 2 |
| 14 | 3 | 1,593 | -805 | 531 | 36 | 96 | 1 | 1 |
| 20 | 18 | 1,934 | -12,452 | 107 | 203 | 82 | 5 | 6 |
| 2 | 23 | 2,413 | -10,780 | 105 | 173 | 195 | 6 | 5 |
| 9 | 3 | 2,866 | -731 | 955 | 62 | 383 | 1 | 2 |
| 4 | 31 | 4,507 | -13,475 | 145 | 227 | 70 | 8 | 7 |
| 21 | 14 | 5,761 | -8,630 | 411 | 165 | 428 | 4 | 5 |
| 19 | 28 | 8,885 | -16,300 | 317 | 150 | 188 | 8 | 5 |

### Book x session
| bs | n path | net path $ | loss path $ | mean/trade path | n HOLD | mean/trade HOLD | n share path % | n share HOLD % |
|--|--|--|--|--|--|--|--|--|
| U7-london | 15 | -14,004 | -23,590 | -934 | 103 | 6 | 4 | 3 |
| P7-asia | 41 | -11,910 | -43,084 | -290 | 355 | 222 | 11 | 11 |
| K7-asia | 60 | -11,270 | -37,639 | -188 | 500 | 147 | 16 | 16 |
| U7-asia | 11 | -9,293 | -21,281 | -845 | 110 | 89 | 3 | 3 |
| K7-london | 37 | -9,246 | -22,433 | -250 | 359 | 67 | 10 | 11 |
| M7-london | 62 | -6,805 | -34,378 | -110 | 451 | -18 | 17 | 14 |
| K7-nyam | 26 | -6,305 | -15,896 | -243 | 243 | -76 | 7 | 8 |
| H7-asia | 15 | -4,230 | -15,024 | -282 | 94 | -148 | 4 | 3 |
| K7-nypm | 15 | -3,559 | -11,951 | -237 | 163 | -83 | 4 | 5 |
| M7-nyam | 21 | -3,121 | -11,513 | -149 | 235 | 46 | 6 | 7 |
| P7-nyam | 6 | -1,331 | -3,728 | -222 | 26 | 433 | 2 | 1 |
| H7-nyam | 3 | -1,179 | -2,377 | -393 | 40 | -119 | 1 | 1 |
| P7-london | 37 | 1,072 | -18,119 | 29 | 267 | 78 | 10 | 8 |
| O7-nyam | 3 | 2,866 | -731 | 955 | 62 | 383 | 1 | 2 |

### Entry number of the book in its session (replacement = 2nd+)
| en | n path | net path $ | loss path $ | mean/trade path | n HOLD | mean/trade HOLD | n share path % | n share HOLD % |
|--|--|--|--|--|--|--|--|--|
| 1st | 163 | -29,639 | -126,755 | -182 | 1332 | 26 | 44 | 41 |
| 2nd | 93 | -28,982 | -70,941 | -312 | 812 | 115 | 25 | 25 |
| 3rd | 55 | -13,792 | -40,171 | -251 | 495 | 87 | 15 | 15 |
| 4th+ | 61 | -1,988 | -33,152 | -33 | 580 | 78 | 16 | 18 |

### Same-side-after-loser (ssr) and opened-after-day-down
| ssr | n path | net path $ | loss path $ | mean/trade path | n HOLD | mean/trade HOLD | n share path % | n share HOLD % |
|--|--|--|--|--|--|--|--|--|
| fresh | 310 | -54,682 | -228,517 | -176 | 2708 | 76 | 83 | 84 |
| ssr | 62 | -19,720 | -42,503 | -318 | 511 | 18 | 17 | 16 |

day down >= $5k at entry: path trades 103 net $-13,432; all HOLD 470 net $48,716.

day down >= $10k at entry: path trades 29 net $2,061; all HOLD 147 net $21,572.

Stack cuts in the path: 7 trades, $-6,198 (HOLD total 48, $-39,964). DAY-DONE / book locks (BookLock, TimeBlock) in the path: 3 trades, $-899. The governor and lot-gate effects do not show in a trade list (they act by removing or shrinking entries): the governor-off and lot comparison come from the cells TL3_PM_JL_GOVOFF / PM_ALLNOSC when they run.

### The 15 biggest single losses in the path
| book | sess | side | lots | ehour | exit_name | net_fee | dtype | with_day | en_bs |
|--|--|--|--|--|--|--|--|--|--|
| U7 | london | -1 | 4 | 3 | StopJoinFallback | -5,085 | range | with | 1 |
| U7 | london | -1 | 4 | 5 | StopJoin | -4,760 | mixed | against | 1 |
| U7 | asia | -1 | 4 | 20 | StopJoinFallback | -4,740 | mixed | against | 1 |
| U7 | london | -1 | 4 | 7 | StopJoin | -4,685 | mixed | with | 2 |
| U7 | asia | -1 | 4 | 1 | StopJoinFallback | -4,665 | mixed | with | 1 |
| U7 | asia | 1 | 4 | 23 | StopJoin | -4,650 | mixed | with | 2 |
| P7 | asia | -1 | 4 | 18 | StateCut | -3,919 | range | with | 1 |
| P7 | asia | -1 | 4 | 18 | StateCut | -3,332 | mixed | against | 1 |
| H7 | asia | 1 | 4 | 23 | StateCut | -2,959 | mixed | with | 2 |
| P7 | asia | -1 | 4 | 0 | StateCut | -2,624 | range | with | 2 |
| U7 | asia | -1 | 2 | 23 | StopJoinFallback | -2,567 | trend | against | 1 |
| P7 | asia | -1 | 4 | 1 | StateCut | -2,559 | trend | with | 3 |
| P7 | asia | -1 | 4 | 23 | StateCut | -2,514 | trend | against | 3 |
| P7 | asia | 1 | 4 | 1 | StateCut | -2,479 | trend | with | 4 |
| P7 | asia | -1 | 4 | 23 | StateCut | -2,474 | trend | against | 3 |

## 3. The peak-to-trough path day by day ($k by book, session and exit group; market = NQ 1-min mid by Globex day, close-open signed; event = event calendar kinds)
| day | net $k | trades | K7 | U7 | P7 | M7 | H7 | A7 | asi | lon | nya | nyp | cuts | full stops | targets | range pts | close-open | day type | event |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 20251118 | -3.1 | 23 | 0.1 | -0.9 | -1.4 | -2.1 | 0.0 | 1.2 | -0.0 | -3.1 | 0.0 | 0.0 | -13.9 | 0.0 | 10.8 | 569 | -356 | trend |  |
| 20251119 | -2.7 | 26 | 0.1 | -1.1 | -0.9 | 1.0 | -1.0 | -0.7 | -4.5 | 1.8 | 0.0 | 0.0 | -16.0 | -2.3 | 15.6 | 524 | 417 | trend | AUC_BOND_20Y;EARN_AMC;FOMC_MIN |
| 20251120 | 2.7 | 37 | 0.2 | 2.4 | -0.3 | -0.9 | -1.0 | 2.4 | -1.4 | 2.0 | 0.8 | 1.3 | -19.1 | -1.0 | 22.8 | 1233 | -867 | trend | NFP |
| 20251121 | -9.1 | 22 | -5.1 | -2.3 | -0.9 | 0.4 | 0.0 | -1.2 | -6.4 | -2.7 | 0.0 | 0.0 | -12.6 | -4.9 | 8.4 | 678 | 253 | mixed |  |
| 20251124 | -10.8 | 22 | -2.5 | -5.0 | -2.9 | -0.4 | 0.0 | 0.0 | -7.3 | -3.5 | 0.0 | 0.0 | -15.5 | -3.8 | 8.4 | 614 | 490 | trend | AUC_NOTE_2Y |
| 20251125 | -3.0 | 24 | -2.3 | -1.1 | 1.3 | -0.9 | -1.2 | 1.2 | 1.1 | -1.9 | -2.2 | 0.0 | -10.3 | -3.5 | 10.8 | 505 | 105 | range | AUC_NOTE_5Y;PPI;RETAIL |
| 20251126 | 8.2 | 27 | -0.0 | -1.2 | 4.2 | 1.6 | 3.6 | 0.0 | 11.1 | -2.3 | 0.2 | -0.9 | -7.7 | -5.7 | 21.6 | 308 | 230 | mixed | AUC_NOTE_7Y |
| 20251128 | 2.9 | 10 | 2.4 | -4.7 | 2.4 | 0.4 | 2.4 | -0.0 | 0.1 | -0.8 | 3.6 | 0.0 | -0.8 | -5.9 | 9.6 | 183 | 173 | mixed |  |
| 20251201 | -4.5 | 32 | -4.1 | 0.1 | -0.6 | -0.5 | -1.2 | 1.7 | 7.1 | -7.4 | -4.3 | 0.0 | -15.9 | -5.9 | 18.0 | 322 | -98 | mixed | ISM_MFG |
| 20251202 | -8.1 | 24 | -4.5 | 2.4 | -0.3 | -0.3 | -4.0 | -0.7 | -9.2 | 4.8 | -3.7 | 0.0 | -15.9 | -3.0 | 10.8 | 332 | 188 | mixed | CHAIR_SPEECH |
| 20251203 | -8.8 | 16 | -3.4 | -2.3 | -1.2 | 0.0 | -1.9 | 0.0 | -4.5 | -1.1 | -4.4 | 1.2 | -9.4 | -4.2 | 4.8 | 254 | 23 | range | ISM_SVC |
| 20251204 | -14.3 | 18 | -5.2 | -5.1 | -2.3 | -5.9 | 2.4 | 0.0 | -0.2 | -10.5 | -3.6 | 0.0 | -11.1 | -7.5 | 4.2 | 232 | -26 | range |  |
| 20251205 | 4.6 | 24 | -4.0 | 4.8 | 3.1 | -2.4 | 1.2 | 0.0 | 6.6 | 3.1 | -2.3 | -2.8 | -11.6 | -1.2 | 17.4 | 278 | 101 | mixed | PCE |
| 20251208 | -2.5 | 23 | -2.0 | 2.4 | -5.3 | -0.1 | 1.3 | 1.2 | -0.1 | -4.9 | 6.4 | -3.9 | -15.7 | -1.2 | 14.4 | 265 | -53 | range | AUC_NOTE_3Y |
| 20251209 | -3.2 | 22 | -1.5 | 2.4 | -3.5 | 0.3 | -0.9 | 0.0 | -5.9 | 4.5 | -1.9 | 0.0 | -12.6 | -1.2 | 10.8 | 162 | -29 | range | AUC_NOTE_10Y |
| 20251210 | -22.4 | 22 | 1.4 | -14.1 | -3.4 | -0.0 | -5.1 | -1.2 | -19.4 | -7.0 | 2.4 | 1.6 | -14.3 | -16.5 | 8.4 | 326 | 93 | mixed | FOMC |

## 4. State-cut dominance in the path (JL2): are the 128 cuts the cause?
128 state cuts lose $-127,478 in the path (median 31 min after entry; 38 of 128 within 15 min, 40 after 60 min). Same trades held to the raw 60/60 bracket (1-s paths, 114 of 128 matched, no state cut): actual $-111,990 versus raw bracket $-133,388 on the matched trades, i.e. the cuts save $21,398 in the path and only 12% of these trades would have reached target. Over all HOLD: 893 matched cuts actual $955,427 vs raw bracket $1,086,415 (cuts save $130,989). So the cut is not what makes the drawdown: the entries lose with or without it.

By book:
| book | n | cut_loss | median_min | repl_n | repl_pnl | raw_bracket |
|--|--|--|--|--|--|--|
| A7 | 2 | -1,407 | 21 | 0 | 0 | -2,402 |
| H7 | 5 | -7,671 | 160 | 2 | 105 | -4,814 |
| K7 | 23 | -15,075 | 32 | 19 | 2,282 | -21,626 |
| M7 | 47 | -39,658 | 30 | 32 | -249 | -48,059 |
| P7 | 49 | -61,588 | 32 | 30 | -1,606 | -56,481 |
| U7 | 2 | -2,079 | 4 | 0 | 0 | -5 |

By session:
| sess | n | cut_loss | median_min | repl_pnl | raw_bracket |
|--|--|--|--|--|--|
| asia | 43 | -58,759 | 38 | 1,197 | -54,085 |
| london | 66 | -52,351 | 33 | 7,142 | -61,283 |
| nyam | 18 | -14,864 | 15 | -5,798 | -18,020 |
| nypm | 1 | -1,504 | 6 | -2,009 | 0 |

Time from entry to cut (min): (0.0, 5.0]: 16, (5.0, 15.0]: 22, (15.0, 30.0]: 25, (30.0, 60.0]: 25, (60.0, 120.0]: 17, (120.0, 1000000000.0]: 23. Replacement = next entry of the same book in the same session after the cut: 83 of 128 cuts were followed by one (gap median 31 min); those replacements made $532 in total (K7 +2.3k, M7 -0.2k, P7 -1.6k, H7 +0.1k, session split in the table), so freed-book replacement neither rescues nor deepens the path.

No-cut comparison from existing runs on other bases over the same peak-to-trough dates (JL2 itself has no no-cut run; flagged): JN05W2 (cut on) path -$92.0k vs JN05W2_NOCUT -$94.3k; JL2 -$74.4k vs JN05W2J_NOCUT (JN04RM base) -$76.5k. HOLD max DD with cuts off is worse, not better, on JN05W2 (-$110.3k, 2026-03-16..27) and about equal on JN05W2J (-$94.8k) while net per week rises on JN05W2 (+$2.4k/wk vs cut on) and is $0.2k/wk below JL2 on JN05W2J: the Dec 2025 path loses about the same with or without the state cut. A JL2 no-cut run (state cut off on the JL2 base) would settle it and is not queued (quota 0).

## 5. Leads scored on HOLD only. PLAIN: the W-LR London skip does not cut the HOLD drawdown at any k (W-LR true points vs the 74,402 reference: k=1.25 +0.8%, k=1.5 -5.1%, k=1 +3.0% with a negative mean; my scored cells LS1_MP -5.1% and LS125_MP -8.6%); the random controls RKMP* below are NOT VALID (W-LR: per-second redraw, keep share 0.87-0.92 vs 0.60-0.73) and are shown for completeness only; status Off/Shadow (vs base; DD cut % = positive is a smaller max DD; trades changed = symmetric difference of the trade lists; rows need all six HOLD months on JL2; random/placebo controls listed with their owner group)
| group | cell | DD cut % | DD $ | worst wk d$ | net/wk d$ | net/wk d$ @4.84 | live x1.75 net/wk d$ | live x1.75 DD $ | trades changed | trades | full stops/wk | best5 kept |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| W-LR London skip MP (k=1 / 1.25) | LR_JL2_LS1_MP | -5.1 | -78,185.0 | -3,540.0 | -115.0 | -75.0 | -201.0 | -136,824.0 | 371.0 | 3,012.0 | 10.2 | 0.9 |
| W-LR London skip MP (k=1 / 1.25) | LR_JL2_LS125_MP | -8.6 | -80,811.0 | -6,166.0 | -101.0 | -66.0 | -177.0 | -141,420.0 | 319.0 | 3,038.0 | 10.1 | 1.0 |
| W-LR placebo/random controls | LR_JL2_RKMP68S1 | 6.2 | -69,815.0 | -331.0 | 962.0 | 972.0 | 1,683.0 | -122,176.0 | 506.0 | 3,175.0 | 10.1 | 1.0 |
| W-LR placebo/random controls | LR_JL2_RKMP68S2 | -3.7 | -77,152.0 | -1,909.0 | 56.0 | 64.0 | 97.0 | -135,017.0 | 500.0 | 3,177.0 | 10.2 | 1.0 |
| W-LR placebo/random controls | LR_JL2_RKMP68S3 | 8.3 | -68,220.0 | -575.0 | 1,188.0 | 1,195.0 | 2,080.0 | -119,384.0 | 493.0 | 3,178.0 | 10.3 | 1.0 |
| W-LR placebo/random controls | LR_JL2_RKMP72S1 | 10.2 | -66,813.0 | -331.0 | 810.0 | 821.0 | 1,418.0 | -116,922.0 | 443.0 | 3,164.0 | 10.1 | 1.1 |
| W-LR placebo/random controls | LR_JL2_RKMP72S2 | 2.6 | -72,462.0 | -2,564.0 | 76.0 | 82.0 | 134.0 | -126,808.0 | 436.0 | 3,193.0 | 10.2 | 1.0 |
| W-LR placebo/random controls | LR_JL2_RKUC65S2 | 4.9 | -70,741.0 | -810.0 | 550.0 | 556.0 | 962.0 | -123,796.0 | 545.0 | 3,188.0 | 10.2 | 1.0 |
| W-LR placebo/random controls | LR_JL2_RKUC65S3 | 8.3 | -68,197.0 | -575.0 | 1,356.0 | 1,364.0 | 2,373.0 | -119,345.0 | 512.0 | 3,173.0 | 10.2 | 1.0 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_JL2_ddopen18_wR30_30_a | 6.8 | -69,327.0 | 7,250.0 | -2,756.0 | -2,786.0 | -4,823.0 | -121,322.0 | 1,584.0 | 3,389.0 | 7.9 | 0.7 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_JL2_ddopen18_wT120_a | -47.0 | -109,406.0 | -8,264.0 | -2,200.0 | -2,075.0 | -3,850.0 | -191,461.0 | 1,315.0 | 2,600.0 | 10.4 | 1.1 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_JL2_ddopen18_wT85_a | -12.2 | -83,446.0 | -24,615.0 | 114.0 | 184.0 | 199.0 | -146,030.0 | 1,101.0 | 2,854.0 | 10.6 | 1.1 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_JL2_ddopen18_w_aK | -23.8 | -92,122.0 | -9,640.0 | -862.0 | -748.0 | -1,508.0 | -161,214.0 | 1,694.0 | 2,643.0 | 8.4 | 0.9 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_JL2_ddopen18_w_aT20 | -5.0 | -78,152.0 | -1,308.0 | -660.0 | -734.0 | -1,155.0 | -136,766.0 | 970.0 | 3,581.0 | 9.0 | 1.0 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_JL2_ddopen18_w_aT30 | -8.2 | -80,523.0 | 304.0 | -929.0 | -979.0 | -1,625.0 | -140,914.0 | 721.0 | 3,450.0 | 9.6 | 1.0 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_JL2_ddopen18_w_aT40 | -3.9 | -77,292.0 | -207.0 | 921.0 | 893.0 | 1,613.0 | -135,261.0 | 597.0 | 3,352.0 | 9.7 | 1.0 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_JL2_ddopen18_w_aZ05 | -5.2 | -78,290.0 | -3,036.0 | 566.0 | 589.0 | 990.0 | -137,008.0 | 537.0 | 3,294.0 | 9.8 | 1.1 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_JL2_ddsess_wR30_30_a | -4.9 | -78,084.0 | -840.0 | -3,532.0 | -3,564.0 | -6,181.0 | -136,648.0 | 1,690.0 | 3,391.0 | 7.9 | 0.6 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_JL2_ddsess_wT120_a | -41.2 | -105,041.0 | -7,955.0 | -496.0 | -364.0 | -868.0 | -183,822.0 | 1,394.0 | 2,569.0 | 10.8 | 0.9 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_JL2_ddsess_wT85_a | -9.9 | -81,762.0 | -15,074.0 | 1,374.0 | 1,446.0 | 2,404.0 | -143,083.0 | 1,177.0 | 2,840.0 | 10.6 | 1.0 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_JL2_ddsess_w_aK | -7.1 | -79,716.0 | 7,167.0 | 956.0 | 1,025.0 | 1,674.0 | -139,504.0 | 1,251.0 | 2,914.0 | 8.7 | 1.0 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_JL2_ddsess_w_aT20 | -6.4 | -79,150.0 | 3,656.0 | 772.0 | 726.0 | 1,350.0 | -138,513.0 | 796.0 | 3,399.0 | 9.4 | 1.1 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_JL2_ddsess_w_aT30 | -1.3 | -75,375.0 | 4,498.0 | 1,368.0 | 1,339.0 | 2,393.0 | -131,906.0 | 589.0 | 3,320.0 | 9.6 | 1.1 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_JL2_ddsess_w_aT40 | -6.4 | -79,154.0 | 1,280.0 | 785.0 | 772.0 | 1,374.0 | -138,520.0 | 503.0 | 3,260.0 | 9.7 | 1.1 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_JL2_ddsess_w_aZ05 | -4.5 | -77,745.0 | -1,590.0 | 723.0 | 747.0 | 1,266.0 | -136,053.0 | 404.0 | 3,239.0 | 9.9 | 1.0 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_JL2_ddslope60_wR30_30_a | -11.3 | -82,799.0 | 2,766.0 | -1,484.0 | -1,527.0 | -2,597.0 | -144,899.0 | 1,748.0 | 3,463.0 | 7.5 | 0.7 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_JL2_ddslope60_wT120_a | -43.1 | -106,475.0 | -6,346.0 | 910.0 | 1,051.0 | 1,592.0 | -186,332.0 | 1,439.0 | 2,502.0 | 10.8 | 1.0 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_JL2_ddslope60_wT85_a | -24.1 | -92,315.0 | -19,310.0 | 3,234.0 | 3,311.0 | 5,660.0 | -161,552.0 | 1,206.0 | 2,819.0 | 10.5 | 1.2 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_JL2_ddslope60_w_aT30 | -28.7 | -95,720.0 | -1,584.0 | -1,248.0 | -1,250.0 | -2,184.0 | -167,510.0 | 429.0 | 3,206.0 | 10.0 | 1.1 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_JL2_ddslope60_w_aZ05 | -13.3 | -84,287.0 | -5,340.0 | 354.0 | 370.0 | 620.0 | -147,502.0 | 270.0 | 3,215.0 | 10.2 | 1.0 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_JL2_ddvote_wR30_30_a | -9.4 | -81,375.0 | -384.0 | -3,808.0 | -3,839.0 | -6,664.0 | -142,407.0 | 1,688.0 | 3,389.0 | 8.0 | 0.6 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_JL2_ddvote_w_aT40 | -14.6 | -85,293.0 | -588.0 | -988.0 | -989.0 | -1,729.0 | -149,263.0 | 302.0 | 3,211.0 | 10.1 | 1.0 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_JL2_ddvote_w_aZ05 | -7.9 | -80,283.0 | -2,398.0 | 626.0 | 635.0 | 1,095.0 | -140,495.0 | 178.0 | 3,223.0 | 10.1 | 1.0 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_JL2_ddvwap_wR30_30_a | -37.6 | -102,410.0 | 3,261.0 | -3,729.0 | -3,769.0 | -6,526.0 | -179,218.0 | 1,815.0 | 3,430.0 | 7.5 | 0.7 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_JL2_ddvwap_wT120_a | -64.4 | -122,283.0 | -8,012.0 | 766.0 | 911.0 | 1,341.0 | -213,995.0 | 1,505.0 | 2,494.0 | 10.7 | 0.9 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_JL2_ddvwap_wT85_a | -8.8 | -80,953.0 | -22,454.0 | 2,790.0 | 2,868.0 | 4,883.0 | -141,668.0 | 1,235.0 | 2,818.0 | 10.6 | 1.1 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_JL2_ddvwap_w_aK | 3.1 | -72,108.0 | -226.0 | 207.0 | 228.0 | 362.0 | -126,189.0 | 720.0 | 3,105.0 | 10.1 | 1.0 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_JL2_ddvwap_w_aT20 | -2.9 | -76,579.0 | -6,411.0 | -630.0 | -639.0 | -1,103.0 | -134,013.0 | 466.0 | 3,229.0 | 10.2 | 1.0 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_JL2_ddvwap_w_aT30 | -0.3 | -74,590.0 | -5,659.0 | -400.0 | -407.0 | -700.0 | -130,533.0 | 354.0 | 3,233.0 | 10.2 | 1.0 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_JL2_ddvwap_w_aT40 | 1.3 | -73,399.0 | -8,488.0 | -844.0 | -843.0 | -1,477.0 | -128,448.0 | 292.0 | 3,203.0 | 10.2 | 1.0 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_JL2_ddvwap_w_aZ05 | -13.9 | -84,757.0 | -6,335.0 | -241.0 | -233.0 | -422.0 | -148,325.0 | 198.0 | 3,239.0 | 10.2 | 1.0 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x40s1p35 | -2.0 | -75,897.0 | -6,670.0 | -707.0 | -714.0 | -1,237.0 | -132,820.0 | 283.0 | 3,194.0 | 11.2 | 1.0 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x40s1p60 | 2.0 | -72,931.0 | -8,481.0 | -717.0 | -729.0 | -1,255.0 | -127,630.0 | 456.0 | 3,179.0 | 12.3 | 1.0 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x40s1p81 | -6.5 | -79,251.0 | -3,523.0 | -638.0 | -655.0 | -1,116.0 | -138,689.0 | 604.0 | 3,173.0 | 12.7 | 1.1 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x40s2p35 | -10.3 | -82,066.0 | -441.0 | 117.0 | 111.0 | 204.0 | -143,615.0 | 297.0 | 3,180.0 | 11.0 | 0.9 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x40s2p60 | -7.8 | -80,186.0 | 625.0 | 1,528.0 | 1,509.0 | 2,674.0 | -140,326.0 | 515.0 | 3,196.0 | 11.5 | 1.0 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x40s2p81 | -14.4 | -85,147.0 | -5,693.0 | 1,195.0 | 1,170.0 | 2,091.0 | -149,007.0 | 654.0 | 3,187.0 | 11.8 | 1.0 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x40s3p35 | -8.0 | -80,322.0 | -1,538.0 | -683.0 | -690.0 | -1,196.0 | -140,563.0 | 296.0 | 3,185.0 | 11.1 | 1.0 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x40s3p60 | -9.6 | -81,545.0 | -2,941.0 | -83.0 | -97.0 | -145.0 | -142,704.0 | 443.0 | 3,184.0 | 11.6 | 1.1 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x40s3p81 | -17.3 | -87,266.0 | -3,634.0 | -458.0 | -477.0 | -802.0 | -152,715.0 | 539.0 | 3,184.0 | 12.0 | 1.1 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x60s1p92 | 0.4 | -74,137.0 | -8,037.0 | -37.0 | -36.0 | -65.0 | -129,740.0 | 259.0 | 3,206.0 | 10.1 | 1.0 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x60s2p92 | -12.6 | -83,740.0 | -612.0 | 1,690.0 | 1,682.0 | 2,957.0 | -146,544.0 | 222.0 | 3,249.0 | 9.8 | 1.0 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_bA7_sas_JL2_pol_fx40x40 | 2.9 | -72,222.0 | 2,296.0 | -1,305.0 | -1,304.0 | -2,284.0 | -126,388.0 | 477.0 | 3,226.0 | 12.1 | 0.9 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_bA7_sas_JL2_pol_fx40x40s101 | 6.1 | -69,854.0 | 4,446.0 | -420.0 | -422.0 | -735.0 | -122,245.0 | 205.0 | 3,234.0 | 11.1 | 0.9 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_bA7_sas_JL2_pol_fx40x40s102 | 1.3 | -73,447.0 | -3,997.0 | -1,246.0 | -1,247.0 | -2,180.0 | -128,532.0 | 182.0 | 3,231.0 | 10.8 | 0.9 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_bA7_sas_JL2_pol_fx40x40s103 | 2.6 | -72,436.0 | 4,770.0 | 322.0 | 320.0 | 564.0 | -126,764.0 | 198.0 | 3,237.0 | 11.0 | 1.0 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_pol_fx40x40 | -14.2 | -84,992.0 | -3,937.0 | -431.0 | -460.0 | -754.0 | -148,735.0 | 418.0 | 3,265.0 | 14.5 | 1.0 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_pol_fx40x40s101 | -3.1 | -76,691.0 | -697.0 | 61.0 | 46.0 | 107.0 | -134,210.0 | 235.0 | 3,242.0 | 12.5 | 1.0 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_pol_fx40x40s102 | -7.3 | -79,843.0 | -1,462.0 | -267.0 | -280.0 | -467.0 | -139,725.0 | 196.0 | 3,251.0 | 12.1 | 1.0 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_pol_fx40x40s103 | -7.8 | -80,200.0 | -2,220.0 | -315.0 | -332.0 | -551.0 | -140,349.0 | 254.0 | 3,255.0 | 12.5 | 1.0 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_pol_fx40x60s102 | -0.6 | -74,867.0 | -400.0 | -31.0 | -35.0 | -54.0 | -131,017.0 | 69.0 | 3,246.0 | 10.2 | 1.0 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_pol_fx40x60s103 | 3.0 | -72,172.0 | 237.0 | -553.0 | -558.0 | -968.0 | -126,300.0 | 64.0 | 3,249.0 | 10.2 | 0.9 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_bK7_slo_JL2_pol_fx40x60 | -2.3 | -76,096.0 | 368.0 | -194.0 | -201.0 | -339.0 | -133,168.0 | 194.0 | 3,269.0 | 10.2 | 1.0 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_bK7_slo_JL2_pol_fx40x60s101 | 1.9 | -73,010.0 | 768.0 | 64.0 | 60.0 | 112.0 | -127,767.0 | 127.0 | 3,244.0 | 10.2 | 1.0 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_bU7_sas_JL2_pol_fx40x40 | 9.7 | -67,152.0 | -2,076.0 | 1,155.0 | 1,124.0 | 2,022.0 | -117,515.0 | 427.0 | 3,250.0 | 10.2 | 1.0 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_bU7_sas_JL2_pol_fx40x40s101 | 14.9 | -63,345.0 | -402.0 | 1,262.0 | 1,244.0 | 2,209.0 | -110,854.0 | 219.0 | 3,252.0 | 10.1 | 1.1 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_bU7_sas_JL2_pol_fx40x40s102 | 9.9 | -67,038.0 | -7,403.0 | 691.0 | 679.0 | 1,209.0 | -117,316.0 | 212.0 | 3,219.0 | 10.0 | 1.0 |
| W-D10 five bracket cells (D10 own JL2 runs) | D10_M1_50_g00_c1_d10_c20_tb_B_bU7_sas_JL2_pol_fx40x40s103 | -3.1 | -76,674.0 | -2,076.0 | -686.0 | -701.0 | -1,201.0 | -134,180.0 | 200.0 | 3,233.0 | 10.3 | 0.9 |
| W-CF3/FL1 L3 arrival and P7 Asia gated | CF_L3C_ALL5_K_JL2 | 21.5 | -58,435.0 | -4,567.0 | -2,606.0 | -2,420.0 | -4,560.0 | -102,262.0 | 2,270.0 | 2,369.0 | 5.6 | 0.6 |
| W-CF3/FL1 L3 arrival and P7 Asia gated | CF_L3C_ALL5_S_JL2 | 3.9 | -71,528.0 | -24,993.0 | 322.0 | 299.0 | 564.0 | -125,174.0 | 1,335.0 | 3,240.0 | 10.3 | 1.1 |
| W-CF3/FL1 L3 arrival and P7 Asia gated | CF_L3C_P7A_S_JL2 | 2.2 | -72,770.0 | -8,856.0 | -1,182.0 | -1,179.0 | -2,069.0 | -127,348.0 | 570.0 | 3,175.0 | 10.2 | 1.0 |
| W-CF3/FL1 L3 arrival and P7 Asia gated | CF_L3C_U7A_K_JL2 | 11.1 | -66,165.0 | -3,647.0 | 930.0 | 940.0 | 1,627.0 | -115,789.0 | 200.0 | 3,225.0 | 9.2 | 1.0 |
| W-CF3/FL1 L3 arrival and P7 Asia gated | CF_L3C_U7A_S_JL2 | 10.2 | -66,807.0 | -7,787.0 | 1,239.0 | 1,229.0 | 2,168.0 | -116,913.0 | 238.0 | 3,251.0 | 10.2 | 1.0 |
| CF random controls | CF_L3C_ALL5_K_RND_JL2 | 0.3 | -74,153.0 | -28.0 | -541.0 | -369.0 | -947.0 | -129,768.0 | 2,250.0 | 2,429.0 | 5.8 | 0.7 |
| CF random controls | CF_L3C_ALL5_S_RND_JL2 | 23.8 | -56,722.0 | 3,509.0 | 1,637.0 | 1,624.0 | 2,865.0 | -99,263.0 | 1,298.0 | 3,217.0 | 10.2 | 1.0 |
| CF random controls | CF_L3C_U7A_K_RND_JL2 | 8.6 | -68,010.0 | -1,694.0 | 783.0 | 800.0 | 1,370.0 | -119,018.0 | 217.0 | 3,188.0 | 9.2 | 1.0 |
| CF random controls | CF_L3C_U7A_S_RND_JL2 | 13.9 | -64,025.0 | -721.0 | 626.0 | 628.0 | 1,096.0 | -112,043.0 | 266.0 | 3,223.0 | 9.9 | 1.1 |

W-AL1 hold/cut, FIRST-ORDER only (reported by W-AL1, no engine, JL2 base HOLD trades, dollars saved by cutting at +k min instead of the actual exit, before costs and path/replacement effects; exact JL2 HOLD rows blocked by AL quota 0): CUT1 (15 min, 60-min forecast z<-1.0) 369 trades -$12.7k (random-trigger placebos -$42.9k, -$42.4k); CUT2 (z<-1.5) 150 trades -$5.3k (placebo -$11.2k); CUT3 (30 min, z<-1.0) 244 trades +$33.8k (U7 +21.3k, K7 +6.4k, H7 +6.3k, P7 +6.0k; placebo -$23.8k); CUTR1 (ridge only, live-computable) 297 trades -$3.7k (placebo -$14.4k); CUT1A (Asia only) 133 trades +$3.9k (placebo +$4.6k, no better). Reading: the forecast cut beats random cuts but is zero to negative against holding except CUT3, and no evidence yet that it reduces the $74.4k HOLD drawdown; the older-base exact run showed trade-level gain with stack-level loss through replacement flow. Base lots, x1.75 live.

### Pending rows (months present on JL2 / 6)
LR_JL2_RKMP72S3 5/6; LR_JL2_RKUC65S1 5/6; D10_M1_50_g00_c1_d10_c20_tb_B_JL2 0/6; D10_M1_50_g00_c1_d10_c20_tb_B_JL2_ddslope60_w_aK 5/6; D10_M1_50_g00_c1_d10_c20_tb_B_JL2_ddslope60_w_aT20 5/6; D10_M1_50_g00_c1_d10_c20_tb_B_JL2_ddslope60_w_aT40 5/6; D10_M1_50_g00_c1_d10_c20_tb_B_JL2_ddvote_wT120_a 4/6; D10_M1_50_g00_c1_d10_c20_tb_B_JL2_ddvote_wT85_a 4/6; D10_M1_50_g00_c1_d10_c20_tb_B_JL2_ddvote_w_aK 5/6; D10_M1_50_g00_c1_d10_c20_tb_B_JL2_ddvote_w_aT20 4/6; D10_M1_50_g00_c1_d10_c20_tb_B_JL2_ddvote_w_aT30 4/6; D10_M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x60s1p81 5/6; D10_M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x60s2p81 5/6; D10_M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x60s3p81 5/6; D10_M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x60s3p92 5/6; D10_M1_50_g00_c1_d10_c20_tb_B_JL2_rs1p60_pol_fx45x60 1/6; D10_M1_50_g00_c1_d10_c20_tb_B_JL2_rs2p60_pol_fx45x60 1/6; D10_M1_50_g00_c1_d10_c20_tb_B_JL2_rs3p60_pol_fx45x60 1/6; D10_M1_50_g00_c1_d10_c20_tb_B_bA7_sas_JL2_pol_fx45x60 1/6; D10_M1_50_g00_c1_d10_c20_tb_B_bA7_sas_JL2_rs101p500_pol_fx45x60 1/6; D10_M1_50_g00_c1_d10_c20_tb_B_bA7_sas_JL2_rs102p500_pol_fx45x60 1/6; D10_M1_50_g00_c1_d10_c20_tb_B_bA7_sas_JL2_rs103p500_pol_fx45x60 1/6; D10_M1_50_g00_c1_d10_c20_tb_B_bH7_sam_JL2_gb40B40 1/6; D10_M1_50_g00_c1_d10_c20_tb_B_bH7_sam_JL2_gb50B40 1/6; D10_M1_50_g00_c1_d10_c20_tb_B_bH7_sas_JL2_gb40B40 1/6; D10_M1_50_g00_c1_d10_c20_tb_B_bH7_sas_JL2_gb60B30 1/6; D10_M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_gb40B40 1/6; D10_M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_gb50B20 1/6; D10_M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_pol_fx40x60 5/6; D10_M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_pol_fx40x60s101 5/6; D10_M1_50_g00_c1_d10_c20_tb_B_bK7_slo_JL2_pol_fx40x60s102 4/6; D10_M1_50_g00_c1_d10_c20_tb_B_bK7_slo_JL2_pol_fx40x60s103 5/6; D10_M1_50_g00_c1_d10_c20_tb_B_bM7_sam_JL2_ddvote_w_aT20 1/6; D10_M1_50_g00_c1_d10_c20_tb_B_bM7_sam_pl11_JL2_ddvote_w_aT20 1/6; D10_M1_50_g00_c1_d10_c20_tb_B_bM7_sam_pl23_JL2_ddvote_w_aT20 1/6; D10_M1_50_g00_c1_d10_c20_tb_B_bM7_sam_pl37_JL2_ddvote_w_aT20 1/6; D10_M1_50_g00_c1_d10_c20_tb_B_bM7_sam_plR1p75_JL2_ddvote_w_aT20 1/6; D10_M1_50_g00_c1_d10_c20_tb_B_bM7_sam_plR2p75_JL2_ddvote_w_aT20 1/6; D10_M1_50_g00_c1_d10_c20_tb_B_bM7_sam_plR3p75_JL2_ddvote_w_aT20 0/6; D10_M1_50_g00_c1_d10_c20_tb_B_bO7_sam_JL2_ddvote_w_aT20 1/6; D10_M1_50_g00_c1_d10_c20_tb_B_bO7_sam_JL2_ddvote_w_aT25 1/6; D10_M1_50_g00_c1_d10_c20_tb_B_bO7_sam_pl11_JL2_ddvote_w_aT20 0/6; D10_M1_50_g00_c1_d10_c20_tb_B_bP7_sam_JL2_gb40B30 1/6; D10_M1_50_g00_c1_d10_c20_tb_B_bP7_sas_JL2_gb40B40 1/6; D10_M1_50_g00_c1_d10_c20_tb_B_bP7_sas_JL2_gb50B40 1/6; CF_G_K7A_V0ge4_K_JL2 0/6; CF_G_P7A_V0all5_K_JL2 0/6; CF_G_P7A_V0all5_S15_JL2 0/6; CF_L3C_ALL5_K30_JL2 0/6; CF_L3C_ALL5_S30_JL2 0/6; CF_L3C_O7N_S_JL2 0/6; CF_L3C_P7A_K_JL2 1/6; CF_L3C_P7L_S_JL2 0/6; CF_L3C_P7N_S_JL2 0/6; CF_L3D_W30_P20_HALF_JL2 0/6; CF_L3D_W30_P20_SKIP_JL2 0/6; CF_L3D_W30_P20_X15_JL2 0/6; CF_L3D_W30_P20_X2_JL2 0/6; CF_L3D_W60_P20_HALF_JL2 0/6; CF_L3D_W60_P20_SKIP_JL2 0/6; CF_L3D_W60_P20_X15_JL2 0/6; CF_L3D_W60_P20_X2_JL2 0/6; CF_RS_P7A_JL2 0/6; CF_L3C_ALL5_K30_RND_JL2 0/6; CF_L3C_ALL5_S30_RND_JL2 0/6; CF_L3C_O7N_S_RND_JL2 0/6; CF_L3C_P7A_K_RND_JL2 0/6; CF_L3C_P7A_S_RND_JL2 2/6; CF_L3C_P7L_S_RND_JL2 0/6; CF_L3C_P7N_S_RND_JL2 0/6; CF_L3D_W30_P20_SKIP_RND_JL2 0/6; CF_L3D_W60_P20_SKIP_RND_JL2 0/6; CF_PX_RND_JL2 0/6; AL_JL_CUT1 0/6; AL_JL_CUT1P31 0/6; AL_JL_CUT1P32 0/6; AL_JL_CUT2 0/6; AL_JL_CUT2P31 0/6; AL_JL_CUT2P32 0/6
