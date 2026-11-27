# LEAD FINDER (W-DYNA, 27 Nov 17:31Z UTC; order 1638Z item 1,3,4): DISCOVERY, NOT A RESULT

Answer first. While a trade is open and at least +0.25 R in profit (R = the book's own stop), I measured, at every full minute, whether another instrument had moved AGAINST the trade by >= 1.5 of its own sigma over the last w seconds while NQ itself was NOT yet turning (NQ own move over the same window > -0.5 sigma: a true lead), and what NQ did NEXT (give-back rate = NQ falls 0.1 R against the trade within 60 s / 300 s, and the mean NQ move in R) versus matched moments (same book, same time in trade, same open-R bin) where that instrument was not turning (z > -1.0). Subjects: the 11 books of WIDE_BRACKET_EDGE.md with verdict EDGE BEYOND DRIFT (AS MF1/2/3, LO MF1/3, NP MF2/3, NY MF1/2/4/5; the order's 13 = these + 2 replacements not yet named; NP MF2 has no stop in points so its path is missing: 10 books in the events). 626,541 decision moments. 2512 tests (session x side x instrument-window x 4 outcomes), fit = first 60% of each book's entries, judged on the last 40%, day-cluster bootstrap, Benjamini-Hochberg over all; 114 pass (q <= 0.05, >= 50 firing moments, same sign on the fit part). NY PM: 0 pass. The bootstrap p floor is 0.0025 (400 resamples), so many passes tie at the floor: the q values are coarse.

What the passes say (by session; give-back = NQ -0.1 R within 5 min): EFFECTS ARE SMALL (+3 to +8 percentage points of give-back rate, d in R of the mean NQ move about -0.01 to -0.03 R) and are mostly the cross-market / risk-off leaders at ONE-MINUTE resolution, not the second-level ones:
- Asia: bonds and FX and crude turning first (ZN r15, ZB r1, 6E r1, 6J r1/r5, 6B r1, CL r15 and CL over 5 s): NQ gives back 53-64 % of the time within 5 minutes after the leader fires against the trade vs 48-50 % otherwise (fires in 1-6 % of the profit minutes).
- NY AM: the stock/ETF tape (QQQ, SPY, GOOGL, MSFT r1/r15): give-back 72-76 % vs 64-66 % (base 58 %); firing in 5-10 % of minutes. Index futures (ES, RTY, YM) and bonds do NOT pass in NY AM.
- London: mixed and partly CONTRARY: ES over 5 s and RTY over 5 min turning against the trade while NQ has not turned is followed by LESS give-back (17-19 % vs 26-27 %), while ZB r15, QQQ/SPY r1 and NVDA r1 are followed by MORE (+8 to +15 pp).
- NY PM: nothing passes.
None of this is a rule: 2,512 tests, correlated features, one history, and the book entries were chosen on the same weeks. It says where to look first (cross-asset risk-off for Asia, the stock tape for NY AM) and that second-level index futures are NOT the early warning (ES/RTY at 5-60 s do not lead NQ in Asia or NY AM).

Base rates (all decision moments of the subject books; G60/G300 = NQ gives back 0.1 R within 60 s / 300 s; A300 = mean NQ move in R over 300 s):

| session | side | moments | G60 | G300 | A300 R |
|---|---|---|---|---|---|
| Asia | short | 271456 | 0.109 | 0.344 | +0.0033 |
| London | short | 185835 | 0.028 | 0.173 | +0.0012 |
| NY PM | short | 37119 | 0.105 | 0.412 | +0.0046 |
| NY AM | short | 132131 | 0.275 | 0.580 | +0.0052 |

## Asia: leaders by instrument (both sides pooled; best test per instrument, outcome G300 unless the G60 one is stronger)

| instrument | window (lead) | outcome | fires in % of profit minutes (judge set) | give-back ON | give-back OFF | d | d on fit part | p | q | passes |
|---|---|---|---|---|---|---|---|---|---|---|
| RTY | 5 s | G60 | 2.5 | 0.250 | 0.194 | +0.037 | +0.015 | 0.0025 | 0.045 | YES |
| CL | 15 s | G60 | 6.2 | 0.220 | 0.195 | +0.025 | +0.008 | 0.0025 | 0.045 | YES |
| ZB | 300 s | G60 | 1.9 | 0.340 | 0.208 | +0.090 | +0.073 | 0.0025 | 0.045 | YES |
| 6E | 60 s | G300 | 1.2 | 0.580 | 0.485 | +0.068 | +0.058 | 0.0025 | 0.045 | YES |
| 6J | 60 s | G300 | 3.8 | 0.535 | 0.484 | +0.037 | +0.082 | 0.0025 | 0.045 | YES |
| ZN | 300 s | G60 | 1.7 | 0.354 | 0.197 | +0.109 | +0.077 | 0.0025 | 0.045 | YES |
| YM | 60 s | G60 | 0.1 | 0.482 | 0.195 | +0.226 | +0.049 | 0.0025 | 0.045 | YES |
| GC | 60 s | G60 | 3.6 | 0.241 | 0.187 | +0.040 | +0.025 | 0.0025 | 0.045 | YES |
| 6C | 300 s | G60 | 1.4 | 0.303 | 0.206 | +0.069 | +0.032 | 0.0025 | 0.045 | YES |
| 6B | 300 s | G60 | 1.2 | 0.302 | 0.200 | +0.072 | +0.026 | 0.0025 | 0.045 | YES |
| QQQ | 60 s | G60 | 0.6 | 0.492 | 0.257 | +0.214 | +nan | 0.0025 | 0.045 | no |
| AAPL | 60 s | G60 | 1.3 | 0.400 | 0.240 | +0.131 | +0.112 | 0.0125 | 0.124 | no |
| NKD | 60 s | G60 | 5.6 | 0.240 | 0.205 | +0.020 | -0.003 | 0.0399 | 0.265 | no |
| MSFT | 60 s | G60 | 1.2 | 0.419 | 0.293 | +0.126 | +nan | 0.0499 | 0.300 | no |

Passes by instrument (any window/outcome): CL 7, ZN 6, ZB 4, 6E 4, 6J 4, 6B 3, GC 2, 6C 1, YM 1, RTY 1

long trades: 0 passing tests
short trades: 32 passing tests

## NY AM: leaders by instrument (both sides pooled; best test per instrument, outcome G300 unless the G60 one is stronger)

| instrument | window (lead) | outcome | fires in % of profit minutes (judge set) | give-back ON | give-back OFF | d | d on fit part | p | q | passes |
|---|---|---|---|---|---|---|---|---|---|---|
| MSFT | 60 s | G60 | 7.0 | 0.460 | 0.353 | +0.045 | +0.031 | 0.0025 | 0.045 | YES |
| SPY | 60 s | G60 | 7.4 | 0.467 | 0.354 | +0.063 | +0.083 | 0.0025 | 0.045 | YES |
| DIA | 60 s | G60 | 7.4 | 0.462 | 0.355 | +0.056 | +0.056 | 0.0025 | 0.045 | YES |
| QQQ | 60 s | G300 | 9.7 | 0.715 | 0.640 | +0.032 | +0.030 | 0.0025 | 0.045 | YES |
| GOOGL | 900 s | G300 | 4.8 | 0.757 | 0.661 | +0.064 | +0.034 | 0.0025 | 0.045 | YES |
| bk7 | 300 s | G60 | 3.7 | 0.473 | 0.368 | +0.049 | +0.073 | 0.0025 | 0.045 | YES |
| IWM | 60 s | G60 | 8.1 | 0.454 | 0.357 | +0.045 | +0.084 | 0.0025 | 0.045 | YES |
| AMZN | 900 s | G60 | 5.0 | 0.450 | 0.379 | +0.047 | +0.023 | 0.0050 | 0.068 | no |
| AAPL | 900 s | G60 | 7.1 | 0.474 | 0.374 | +0.044 | -0.024 | 0.0050 | 0.068 | no |
| 6C | 60 s | G60 | 10.2 | 0.394 | 0.356 | +0.030 | +0.007 | 0.0075 | 0.090 | no |
| ZN | 300 s | G300 | 10.8 | 0.716 | 0.645 | +0.036 | +0.032 | 0.0075 | 0.090 | no |
| ZB | 300 s | G60 | 9.8 | 0.428 | 0.365 | +0.029 | +0.033 | 0.0100 | 0.108 | no |
| META | 60 s | G60 | 7.8 | 0.442 | 0.355 | +0.030 | +0.075 | 0.0125 | 0.124 | no |
| 6J | 300 s | G300 | 7.9 | 0.715 | 0.646 | +0.032 | +0.029 | 0.0200 | 0.169 | no |

Passes by instrument (any window/outcome): GOOGL 2, SPY 2, QQQ 2, bk7 2, DIA 1, IWM 1, MSFT 1

long trades: 0 passing tests
short trades: 10 passing tests

## London: leaders by instrument (both sides pooled; best test per instrument, outcome G300 unless the G60 one is stronger)

| instrument | window (lead) | outcome | fires in % of profit minutes (judge set) | give-back ON | give-back OFF | d | d on fit part | p | q | passes |
|---|---|---|---|---|---|---|---|---|---|---|
| ES | 5 s | G300 | 1.6 | 0.176 | 0.261 | -0.065 | -0.047 | 0.0025 | 0.045 | YES |
| RTY | 300 s | G300 | 3.2 | 0.190 | 0.269 | -0.060 | -0.015 | 0.0025 | 0.045 | YES |
| ZN | 300 s | G60 | 3.3 | 0.072 | 0.048 | +0.024 | +0.024 | 0.0025 | 0.045 | YES |
| ZB | 900 s | G300 | 2.5 | 0.323 | 0.254 | +0.084 | +0.052 | 0.0025 | 0.045 | YES |
| CL | 300 s | G60 | 6.6 | 0.084 | 0.045 | +0.028 | +0.006 | 0.0025 | 0.045 | YES |
| NVDA | 60 s | G300 | 1.8 | 0.363 | 0.253 | +0.078 | +0.100 | 0.0025 | 0.045 | YES |
| AMZN | 60 s | G60 | 3.4 | 0.148 | 0.071 | +0.064 | +0.099 | 0.0025 | 0.045 | YES |
| SPY | 60 s | G300 | 2.1 | 0.521 | 0.316 | +0.147 | +0.156 | 0.0025 | 0.045 | YES |
| IWM | 60 s | G60 | 2.6 | 0.239 | 0.077 | +0.139 | +0.114 | 0.0025 | 0.045 | YES |
| QQQ | 60 s | G300 | 1.6 | 0.457 | 0.283 | +0.120 | +0.117 | 0.0025 | 0.045 | YES |
| TSLA | 60 s | G60 | 1.3 | 0.121 | 0.054 | +0.051 | +0.050 | 0.0050 | 0.068 | no |
| AAPL | 60 s | G60 | 2.7 | 0.151 | 0.073 | +0.065 | +0.051 | 0.0050 | 0.068 | no |
| YM | 60 s | G300 | 0.4 | 0.337 | 0.250 | +0.074 | +0.045 | 0.0075 | 0.090 | no |
| 6C | 300 s | G60 | 3.8 | 0.077 | 0.049 | +0.022 | +0.010 | 0.0100 | 0.108 | no |

Passes by instrument (any window/outcome): QQQ 3, NVDA 2, SPY 2, AMZN 1, CL 1, IWM 1, ES 1, RTY 1, ZB 1, ZN 1

long trades: 0 passing tests
short trades: 14 passing tests

## NY PM: leaders by instrument (both sides pooled; best test per instrument, outcome G300 unless the G60 one is stronger)

| instrument | window (lead) | outcome | fires in % of profit minutes (judge set) | give-back ON | give-back OFF | d | d on fit part | p | q | passes |
|---|---|---|---|---|---|---|---|---|---|---|
| DIA | 60 s | G60 | 1.4 | 0.270 | 0.129 | +0.122 | +nan | 0.0025 | 0.045 | no |
| bk7 | 60 s | G60 | 1.2 | 0.323 | 0.129 | +0.165 | +nan | 0.0025 | 0.045 | no |
| QQQ | 60 s | G300 | 1.9 | 0.603 | 0.435 | +0.137 | +nan | 0.0025 | 0.045 | no |
| SPY | 60 s | G60 | 1.9 | 0.312 | 0.126 | +0.161 | +nan | 0.0025 | 0.045 | no |
| ZB | 300 s | G300 | 2.7 | 0.364 | 0.443 | -0.090 | +0.046 | 0.0050 | 0.068 | no |
| IWM | 60 s | G60 | 1.3 | 0.257 | 0.128 | +0.107 | +nan | 0.0050 | 0.068 | no |
| 6J | 60 s | G300 | 2.0 | 0.535 | 0.440 | +0.087 | +0.056 | 0.0125 | 0.124 | no |
| CL | 60 s | G60 | 4.8 | 0.112 | 0.137 | -0.038 | -0.008 | 0.0125 | 0.124 | no |
| 6C | 60 s | G300 | 3.4 | 0.516 | 0.443 | +0.066 | +0.028 | 0.0175 | 0.155 | no |
| NVDA | 60 s | G60 | 2.5 | 0.228 | 0.129 | +0.080 | +nan | 0.0175 | 0.155 | no |
| RTY | 300 s | G60 | 2.1 | 0.079 | 0.138 | -0.053 | -0.013 | 0.0175 | 0.155 | no |
| 6B | 60 s | G300 | 2.3 | 0.540 | 0.440 | +0.089 | +0.044 | 0.0200 | 0.169 | no |
| ZN | 5 s | G300 | 14.3 | 0.417 | 0.451 | -0.034 | -0.014 | 0.0299 | 0.224 | no |
| GC | 60 s | G60 | 3.4 | 0.194 | 0.136 | +0.049 | -0.011 | 0.0374 | 0.253 | no |

Passes by instrument (any window/outcome): 

long trades: 0 passing tests
short trades: 0 passing tests

## ITEM 3: give-backs under the fixed bracket (exact trades on disk, 19 books; peak = best open profit from the 5-s path, give-back = final result below 50% of the peak)

| book | trades | stop pts | peak >= 0.5R | gave back > 50% of peak | share | $ given back | peak >= 0.5R but ended at a LOSS | $ lost after +0.5R |
|---|---|---|---|---|---|---|---|---|
| AS_MF1 | 1943 | 40 | 1192 | 543 | 46% | +2008270 | 353 | -755370 |
| AS_MF2 | 634 | 60 | 321 | 101 | 32% | +398515 | 67 | -103245 |
| AS_MF3 | 2579 | 45 | 1546 | 86 | 6% | +360830 | 73 | -200535 |
| AS_MF4 | 906 | 30 | 474 | 179 | 38% | +189139 | 10 | -13449 |
| LO_MF1 | 1086 | 90 | 7 | 1 | 14% | +5800 | 0 | +0 |
| LO_MF2 | 2958 | 45 | 1838 | 519 | 28% | +2566385 | 424 | -1265030 |
| LO_MF3 | 1755 | 120 | 610 | 2 | 0% | +5635 | 1 | -250 |
| NP_MF1 | 3528 | 30 | 2300 | 870 | 38% | +1633483 | 388 | -644433 |
| NP_MF3 | 1128 | 80 | 531 | 3 | 1% | +13480 | 1 | -3780 |
| NP_MF4 | 1789 | 60 | 985 | 310 | 32% | +1363920 | 207 | -480510 |
| NY_MF1 | 1633 | 120 | 888 | 246 | 28% | +2545390 | 159 | -1024490 |
| NY_MF2 | 1959 | 60 | 1204 | 306 | 25% | +1996790 | 260 | -1021695 |
| NY_MF3 | 979 | 120 | 563 | 154 | 27% | +1563905 | 105 | -639440 |
| NY_MF4 | 3231 | 90 | 38 | 6 | 16% | +33110 | 3 | -15420 |
| NY_MF5 | 2574 | 60 | 1578 | 426 | 27% | +1666195 | 356 | -834265 |
| NY_MF6 | 2897 | 90 | 33 | 4 | 12% | +23065 | 1 | -10985 |
| NY_MF7 | 879 | 120 | 285 | 0 | 0% | +0 | 0 | +0 |
| NY_MF8 | 922 | 80 | 441 | 0 | 0% | +0 | 0 | +0 |
| NY_MF9 | 671 | 80 | 292 | 1 | 0% | +4610 | 1 | -3005 |

Read: for the 120/120 and 60/60 books a trade that reached +0.5 R ends below half of that peak 25-46 % of the time and 10-30 % of such trades end at a LOSS (NY MF1: 246 of 888 trades that reached +0.5 R gave back more than half, $2.5M of open profit given back over 42 months, 159 of them ended at a loss, -$1.02M). Small-target books (90/30, 80/40) cannot reach +0.5 R (the target takes them out first): their give-back is the stop side. NP MF2 is missing (no point stop in the exact set). (b) the best landscape exit: after W-SUNDAY's rows land.

## ITEM 4: instruments / data missing to widen the leader set (named, no quote, no purchase)
- SECOND-level series: only ES, RTY, CL, GC, ZN and NQ exist at 1-second (instr_1s). YM, ZB, 6E, 6J, 6B, 6C, NKD exist only at 1 MINUTE (xmkt), so a lead shorter than a minute cannot be measured for them; Asia leaders (6J, 6E, ZN, CL) are exactly the ones that fire at one minute: second-level YM/ZB/6E/6J/NKD would show whether the true lead is seconds.
- Stocks and ETFs: 1-minute returns since 2024-10 only (10 tickers + basket); no second-level stock/ETF tape, no tick-level QQQ/SPY (the NY AM leaders), no sector ETFs / semis (SMH, XLK, SOXX), no more megacaps beyond the eight, no breadth (advancers/decliners) and NYSE TICK only at 1 minute.
- Volatility: no VIX / VX futures / VVIX series (a vol-up leader), no 10-year yield / DXY spot beyond the ZN/ZB and 6E/6J futures.
- Options flow: UW net-premium and tide at 1 second only as the stored ticks (SPY/QQQ since 2024-10); intraday option walls/gamma by strike only for 9 recorded days (UW_INTRADAY_HISTORY.md); no index-option order-flow at event level.
- Order book of the leaders: NQ MBO exists (2023-04..2026-11); ES/RTY/ZN book data (L2/L3) does not (mbp-10 only for NQ/ES in tables?), so an ES book pull/absorb lead cannot be tested.
- Event calendar (FOMC/CPI/NFP times) and news timestamps: not on the box.
Caveats: DISCOVERY; correlated tests; one history; the subject books were chosen on the same weeks; outcome windows overlap between consecutive minutes of one trade (day-cluster bootstrap, not trade-cluster).
