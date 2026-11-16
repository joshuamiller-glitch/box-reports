# DS3_BRACKET_DD - Part B: target by direction of the day (base TL3_EV_JN05W2JL2)
**STATUS (plain, not a PASS, no lead until controls are in): 25 of 40 Part B cells scored in HOLD; 1 pass the HOLD screen (max DD not worse than the reference, HOLD-path 2025-11-17..12-10 DD not worse, mean not more than 5% below); controls and the other windows are queued for those. L3M never ranks.**

Rule definitions. Day direction at the signal second from CLOSED 1-minute bars only (bar ts <= signal second - 60; price = last closed bar close): session open = price vs open of the first bar of the session (asia 18:00, london 02:00, nyam 09:30, nypm 12:00 ET; needs the first bar within 10 minutes); 18:00 ET open = price vs open of the 18:00 bar of the Globex day; session VWAP = price vs sum((h+l+c)/3 x volume)/sum(volume) since the session start; 60-min slope = price vs the close 60 minutes earlier; 3-of-4 vote = +1/-1 when at least 3 of the 4 agree, else no direction. WITH the day = trade side equals the direction; AGAINST = opposite; no direction = bracket unchanged. WITH: target 85 / 120 points, or trail (no target; once +30 points open a trailing exit 30 points behind the favourable extreme, via the engine trail mechanism); AGAINST: target 20 / 30 / 40 points, size x0.5, skip. Stop (60) and every other level stay at the JL2 values, lots at live values (the stop is unchanged, so constant-risk lots are the same cells). Controls per candidate: 3 placebos = the direction label taken 11 / 23 / 37 sessions earlier at the same clock; 3 matched random = random +-1 labels at the same clock (skip cells: random skip at the same share of signals as the real against-day share). W44-removed row for windows containing 2026-W44. $4.84 column beside the raw one. Dollars BASE lots, x1.75 = live.

### HOLD window (2025-11..2026-04), whole-stack, vs JL2; drawdown first; HOLD path = 2025-11-17..12-10
| cell | max DD (ref) | worst week (ref) | HOLD-path DD (ref) | d net/wk (live x1.75; $4.84) | stops/wk | screen |
|---|---|---|---|---|---|---|
| 18:00 ET open: WITH the day -> trail after +30 by 30  | -69327 (-74402; +6.8%) | -23961 (-31211) | -61720 (-74402) | -2756 (-4823; -2786) | 7.93 (10.17) | fails screen |
| session VWAP: AGAINST the day -> skip  | -72108 (-74402; +3.1%) | -31437 (-31211) | -72108 (-74402) | +207 (+362; +228) | 10.09 (10.17) | SURVIVES screen -> controls queued |
| session VWAP: AGAINST the day -> target 40  | -73399 (-74402; +1.3%) | -39699 (-31211) | -73399 (-74402) | -844 (-1477; -843) | 10.21 (10.17) | fails screen |
| session VWAP: AGAINST the day -> target 30  | -74590 (-74402; -0.3%) | -36870 (-31211) | -74590 (-74402) | -400 (-700; -407) | 10.21 (10.17) | fails screen |
| session open: AGAINST the day -> target 30  | -75375 (-74402; -1.3%) | -26712 (-31211) | -75375 (-74402) | +1368 (+2393; +1339) | 9.55 (10.17) | fails screen |
| session VWAP: AGAINST the day -> target 20  | -76579 (-74402; -2.9%) | -37622 (-31211) | -76579 (-74402) | -630 (-1103; -639) | 10.21 (10.17) | fails screen |
| 18:00 ET open: AGAINST the day -> target 40  | -77292 (-74402; -3.9%) | -31417 (-31211) | -77292 (-74402) | +921 (+1613; +893) | 9.67 (10.17) | fails screen |
| session open: AGAINST the day -> size x0.5  | -77745 (-74402; -4.5%) | -32801 (-31211) | -77745 (-74402) | +723 (+1266; +747) | 9.94 (10.17) | fails screen |
| session open: WITH the day -> trail after +30 by 30  | -78084 (-74402; -4.9%) | -32051 (-31211) | -67960 (-74402) | -3532 (-6181; -3564) | 7.93 (10.17) | fails screen |
| 18:00 ET open: AGAINST the day -> target 20  | -78152 (-74402; -5.0%) | -32518 (-31211) | -78152 (-74402) | -660 (-1155; -734) | 8.97 (10.17) | fails screen |
| 18:00 ET open: AGAINST the day -> size x0.5  | -78290 (-74402; -5.2%) | -34247 (-31211) | -78290 (-74402) | +566 (+990; +589) | 9.82 (10.17) | fails screen |
| session open: AGAINST the day -> target 20  | -79150 (-74402; -6.4%) | -27555 (-31211) | -79150 (-74402) | +772 (+1350; +726) | 9.36 (10.17) | fails screen |
| session open: AGAINST the day -> target 40  | -79154 (-74402; -6.4%) | -29931 (-31211) | -79154 (-74402) | +785 (+1374; +772) | 9.75 (10.17) | fails screen |
| session open: AGAINST the day -> skip  | -79716 (-74402; -7.1%) | -24044 (-31211) | -72781 (-74402) | +956 (+1674; +1025) | 8.70 (10.17) | fails screen |
| 18:00 ET open: AGAINST the day -> target 30  | -80523 (-74402; -8.2%) | -30907 (-31211) | -80199 (-74402) | -929 (-1625; -979) | 9.55 (10.17) | fails screen |
| session VWAP: WITH the day -> target 85  | -80953 (-74402; -8.8%) | -53665 (-31211) | -63862 (-74402) | +2790 (+4883; +2868) | 10.60 (10.17) | fails screen |
| session open: WITH the day -> target 85  | -81762 (-74402; -9.9%) | -46285 (-31211) | -63951 (-74402) | +1374 (+2404; +1446) | 10.60 (10.17) | fails screen |
| 18:00 ET open: WITH the day -> target 85  | -83446 (-74402; -12.2%) | -55826 (-31211) | -74089 (-74402) | +114 (+199; +184) | 10.56 (10.17) | fails screen |
| session VWAP: AGAINST the day -> size x0.5  | -84757 (-74402; -13.9%) | -37546 (-31211) | -84757 (-74402) | -241 (-422; -233) | 10.21 (10.17) | fails screen |
| 18:00 ET open: AGAINST the day -> skip  | -92122 (-74402; -23.8%) | -40851 (-31211) | -56741 (-74402) | -862 (-1508; -748) | 8.43 (10.17) | fails screen |
| 60-min slope: WITH the day -> target 85  | -92315 (-74402; -24.1%) | -50521 (-31211) | -56033 (-74402) | +3234 (+5660; +3311) | 10.48 (10.17) | fails screen |
| session VWAP: WITH the day -> trail after +30 by 30  | -102410 (-74402; -37.6%) | -27949 (-31211) | -72761 (-74402) | -3729 (-6526; -3769) | 7.50 (10.17) | fails screen |
| session open: WITH the day -> target 120  | -105041 (-74402; -41.2%) | -39165 (-31211) | -105041 (-74402) | -496 (-868; -364) | 10.75 (10.17) | fails screen |
| 18:00 ET open: WITH the day -> target 120  | -109406 (-74402; -47.0%) | -39475 (-31211) | -107431 (-74402) | -2200 (-3850; -2075) | 10.40 (10.17) | fails screen |
| session VWAP: WITH the day -> target 120  | -122283 (-74402; -64.4%) | -39223 (-31211) | -106650 (-74402) | +766 (+1341; +911) | 10.67 (10.17) | fails screen |
| 60-min slope: WITH the day -> target 120  | not finished | | | | | |
| 60-min slope: WITH the day -> trail after +30 by 30  | not finished | | | | | |
| 60-min slope: AGAINST the day -> target 20  | not finished | | | | | |
| 60-min slope: AGAINST the day -> target 30  | not finished | | | | | |
| 60-min slope: AGAINST the day -> target 40  | not finished | | | | | |
| 60-min slope: AGAINST the day -> size x0.5  | not finished | | | | | |
| 60-min slope: AGAINST the day -> skip  | not finished | | | | | |
| 3-of-4 vote: WITH the day -> target 85  | not finished | | | | | |
| 3-of-4 vote: WITH the day -> target 120  | not finished | | | | | |
| 3-of-4 vote: WITH the day -> trail after +30 by 30  | not finished | | | | | |
| 3-of-4 vote: AGAINST the day -> target 20  | not finished | | | | | |
| 3-of-4 vote: AGAINST the day -> target 30  | not finished | | | | | |
| 3-of-4 vote: AGAINST the day -> target 40  | not finished | | | | | |
| 3-of-4 vote: AGAINST the day -> size x0.5  | not finished | | | | | |
| 3-of-4 vote: AGAINST the day -> skip  | not finished | | | | | |

(Part D page by W-BD2: autopilot/DS3_BRACKET_DD_D.md, not yet present)
