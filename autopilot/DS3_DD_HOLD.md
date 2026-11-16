# DS3_DD_HOLD - HOLD-window drawdown target (W-PM), built 2026-11-16 13:33Z

VERDICT (data ends 2026-10-30; plain; FIRST PASS, decomposition only, lead rows partly pending): the HOLD max drawdown (-$74.4k, 20251117 to 20251210, 17 trading days) is a book-wide bleed, not one trade or one event: K7 -$30.4k, U7 -$23.3k (26 trades), P7 -$12.2k, M7 -$9.9k, H7 -$5.4k; 128 state cuts (-$127k) and 65 early cuts (-$69k) outrun 136 targets (+$197k) while 33 full stops cost -$68k; Asia -$32.8k and London -$29.0k; the 16 path days lose steadily (12 of 16 net negative; the winners are 11-20, 11-26, 11-28, 12-05) with the FOMC day 12-10 alone -$22.4k (30% of the path: U7 -$14.1k, Asia session -$19.4k, full stops -$16.5k), and the state cuts are not the cause (the same trades held to the raw bracket lose $133k vs the cut result $112k in the path; no-cut runs on other bases show the same path); otherwise it is not a trend-day problem (range days -$31.9k, mixed -$28.5k, trend -$14.0k; against-the-day-direction trades -$53.5k) and the chop call did not flag most of it (calls flagged 93 of 372 trades). Of the leads, only the W-LR London skip rows have HOLD months on JL2 so far: LS1 -5.1% and LS125 -8.6% DD cut (negative = deeper), against random controls spanning -3.7 to 10.2%, so no better than random; every other owner row is pending (no HOLD months on JL2 yet).

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

## 5. Leads scored on HOLD only. PLAIN: the W-LR London skip rows LS1 and LS125 are WORSE than the random controls in HOLD (DD cut -5.1% and -8.6% against controls spanning -3.7 to 10.2%, and net/wk falls) (vs base; DD cut % = positive is a smaller max DD; trades changed = symmetric difference of the trade lists; rows need all six HOLD months on JL2; random/placebo controls listed with their owner group)
| group | cell | DD cut % | DD $ | worst wk d$ | net/wk d$ | net/wk d$ @4.84 | live x1.75 net/wk d$ | live x1.75 DD $ | trades changed | trades | full stops/wk | best5 kept |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| W-LR London skip MP (k=1 / 1.25) | LR_JL2_LS1_MP | -5.1 | -78,185.0 | -3,540.0 | -115.0 | -75.0 | -201.0 | -136,824.0 | 371.0 | 3,012.0 | 10.2 | 0.9 |
| W-LR London skip MP (k=1 / 1.25) | LR_JL2_LS125_MP | -8.6 | -80,811.0 | -6,166.0 | -101.0 | -66.0 | -177.0 | -141,420.0 | 319.0 | 3,038.0 | 10.1 | 1.0 |
| W-LR placebo/random controls | LR_JL2_RKMP68S1 | 6.2 | -69,815.0 | -331.0 | 962.0 | 972.0 | 1,683.0 | -122,176.0 | 506.0 | 3,175.0 | 10.1 | 1.0 |
| W-LR placebo/random controls | LR_JL2_RKMP68S2 | -3.7 | -77,152.0 | -1,909.0 | 56.0 | 64.0 | 97.0 | -135,017.0 | 500.0 | 3,177.0 | 10.2 | 1.0 |
| W-LR placebo/random controls | LR_JL2_RKMP68S3 | 8.3 | -68,220.0 | -575.0 | 1,188.0 | 1,195.0 | 2,080.0 | -119,384.0 | 493.0 | 3,178.0 | 10.3 | 1.0 |
| W-LR placebo/random controls | LR_JL2_RKMP72S1 | 10.2 | -66,813.0 | -331.0 | 810.0 | 821.0 | 1,418.0 | -116,922.0 | 443.0 | 3,164.0 | 10.1 | 1.1 |
| W-LR placebo/random controls | LR_JL2_RKMP72S2 | 2.6 | -72,462.0 | -2,564.0 | 76.0 | 82.0 | 134.0 | -126,808.0 | 436.0 | 3,193.0 | 10.2 | 1.0 |

### Pending rows (months present on JL2 / 6)
LR_JL2_RKMP72S3 5/6; D10_M1_50_g00_c1_d10_c20_tb_B_JL2 0/6; CF_G_K7A_V0ge4_K_JL2 0/6; CF_G_P7A_V0all5_K_JL2 0/6; CF_G_P7A_V0all5_S15_JL2 0/6; CF_L3C_ALL5_K30_JL2 0/6; CF_L3C_ALL5_K_JL2 0/6; CF_L3C_ALL5_S30_JL2 0/6; CF_L3C_ALL5_S_JL2 0/6; CF_L3C_O7N_S_JL2 0/6; CF_L3C_P7A_K_JL2 0/6; CF_L3C_P7A_S_JL2 0/6; CF_L3C_P7L_S_JL2 0/6; CF_L3C_P7N_S_JL2 0/6; CF_L3C_U7A_K_JL2 0/6; CF_L3C_U7A_S_JL2 0/6; CF_L3D_W30_P20_HALF_JL2 0/6; CF_L3D_W30_P20_SKIP_JL2 0/6; CF_L3D_W30_P20_X15_JL2 0/6; CF_L3D_W30_P20_X2_JL2 0/6; CF_L3D_W60_P20_HALF_JL2 0/6; CF_L3D_W60_P20_SKIP_JL2 0/6; CF_L3D_W60_P20_X15_JL2 0/6; CF_L3D_W60_P20_X2_JL2 0/6; CF_RS_P7A_JL2 0/6; CF_L3C_ALL5_K30_RND_JL2 0/6; CF_L3C_ALL5_K_RND_JL2 0/6; CF_L3C_ALL5_S30_RND_JL2 0/6; CF_L3C_ALL5_S_RND_JL2 0/6; CF_L3C_O7N_S_RND_JL2 0/6; CF_L3C_P7A_K_RND_JL2 0/6; CF_L3C_P7A_S_RND_JL2 0/6; CF_L3C_P7L_S_RND_JL2 0/6; CF_L3C_P7N_S_RND_JL2 0/6; CF_L3C_U7A_K_RND_JL2 0/6; CF_L3C_U7A_S_RND_JL2 0/6; CF_L3D_W30_P20_SKIP_RND_JL2 0/6; CF_L3D_W60_P20_SKIP_RND_JL2 0/6; CF_PX_RND_JL2 0/6; AL_JL_CUT1 0/6; AL_JL_CUT1P31 0/6; AL_JL_CUT1P32 0/6; AL_JL_CUT2 0/6; AL_JL_CUT2P31 0/6; AL_JL_CUT2P32 0/6
