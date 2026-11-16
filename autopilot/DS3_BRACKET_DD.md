# DS3_BRACKET_DD - Part B: target by direction of the day (base TL3_EV_JN05W2JL2)
**STATUS (plain, not a PASS, no lead until controls are in): 40 of 40 Part B cells scored in HOLD; 1 pass the HOLD screen (max DD not worse than the reference, HOLD-path 2025-11-17..12-10 DD not worse, mean not more than 5% below); controls and the other windows are queued for those. L3M never ranks.**

Rule definitions. Day direction at the signal second from CLOSED 1-minute bars only (bar ts <= signal second - 60; price = last closed bar close): session open = price vs open of the first bar of the session (asia 18:00, london 02:00, nyam 09:30, nypm 12:00 ET; needs the first bar within 10 minutes); 18:00 ET open = price vs open of the 18:00 bar of the Globex day; session VWAP = price vs sum((h+l+c)/3 x volume)/sum(volume) since the session start; 60-min slope = price vs the close 60 minutes earlier; 3-of-4 vote = +1/-1 when at least 3 of the 4 agree, else no direction. WITH the day = trade side equals the direction; AGAINST = opposite; no direction = bracket unchanged. WITH: target 85 / 120 points, or trail (no target; once +30 points open a trailing exit 30 points behind the favourable extreme, via the engine trail mechanism); AGAINST: target 20 / 30 / 40 points, size x0.5, skip. Stop (60) and every other level stay at the JL2 values, lots at live values (the stop is unchanged, so constant-risk lots are the same cells). Controls per candidate: 3 placebos = the direction label taken 11 / 23 / 37 sessions earlier at the same clock; 3 matched random = random +-1 labels at the same clock (skip cells: random skip at the same share of signals as the real against-day share). W44-removed row for windows containing 2026-W44. $4.84 column beside the raw one. Dollars BASE lots, x1.75 = live.

### HOLD window (2025-11..2026-04), whole-stack, vs JL2; drawdown first; HOLD path = 2025-11-17..12-10
| cell | max DD (ref) | worst week (ref) | HOLD-path DD (ref) | d net/wk (live x1.75; $4.84) | stops/wk | screen |
|---|---|---|---|---|---|---|
| 18:00 ET open: WITH the day -> trail after +30 by 30  | -69327 (-74402; +6.8%) | -23961 (-31211) | -61720 (-74402) | -2756 (-4823; -2786) | 7.93 (10.17) | fails screen |
| session VWAP: AGAINST the day -> skip  | -72108 (-74402; +3.1%) | -31437 (-31211) | -72108 (-74402) | +207 (+362; +228) | 10.09 (10.17) | SURVIVES screen -> controls queued |
| session VWAP: AGAINST the day -> target 40  | -73399 (-74402; +1.3%) | -39699 (-31211) | -73399 (-74402) | -844 (-1477; -843) | 10.21 (10.17) | fails screen |
| session VWAP: AGAINST the day -> target 30  | -74590 (-74402; -0.3%) | -36870 (-31211) | -74590 (-74402) | -400 (-700; -407) | 10.21 (10.17) | fails screen |
| session open: AGAINST the day -> target 30  | -75375 (-74402; -1.3%) | -26712 (-31211) | -75375 (-74402) | +1368 (+2393; +1339) | 9.55 (10.17) | fails screen |
| 60-min slope: AGAINST the day -> skip  | -76376 (-74402; -2.7%) | -35138 (-31211) | -76376 (-74402) | +1150 (+2012; +1169) | 10.06 (10.17) | fails screen |
| session VWAP: AGAINST the day -> target 20  | -76579 (-74402; -2.9%) | -37622 (-31211) | -76579 (-74402) | -630 (-1103; -639) | 10.21 (10.17) | fails screen |
| 18:00 ET open: AGAINST the day -> target 40  | -77292 (-74402; -3.9%) | -31417 (-31211) | -77292 (-74402) | +921 (+1613; +893) | 9.67 (10.17) | fails screen |
| session open: AGAINST the day -> size x0.5  | -77745 (-74402; -4.5%) | -32801 (-31211) | -77745 (-74402) | +723 (+1266; +747) | 9.94 (10.17) | fails screen |
| session open: WITH the day -> trail after +30 by 30  | -78084 (-74402; -4.9%) | -32051 (-31211) | -67960 (-74402) | -3532 (-6181; -3564) | 7.93 (10.17) | fails screen |
| 3-of-4 vote: WITH the day -> target 85  | -78109 (-74402; -5.0%) | -50510 (-31211) | -67663 (-74402) | +1916 (+3352; +1988) | 10.52 (10.17) | fails screen |
| 18:00 ET open: AGAINST the day -> target 20  | -78152 (-74402; -5.0%) | -32518 (-31211) | -78152 (-74402) | -660 (-1155; -734) | 8.97 (10.17) | fails screen |
| 18:00 ET open: AGAINST the day -> size x0.5  | -78290 (-74402; -5.2%) | -34247 (-31211) | -78290 (-74402) | +566 (+990; +589) | 9.82 (10.17) | fails screen |
| session open: AGAINST the day -> target 20  | -79150 (-74402; -6.4%) | -27555 (-31211) | -79150 (-74402) | +772 (+1350; +726) | 9.36 (10.17) | fails screen |
| session open: AGAINST the day -> target 40  | -79154 (-74402; -6.4%) | -29931 (-31211) | -79154 (-74402) | +785 (+1374; +772) | 9.75 (10.17) | fails screen |
| session open: AGAINST the day -> skip  | -79716 (-74402; -7.1%) | -24044 (-31211) | -72781 (-74402) | +956 (+1674; +1025) | 8.70 (10.17) | fails screen |
| 3-of-4 vote: AGAINST the day -> size x0.5  | -80283 (-74402; -7.9%) | -33609 (-31211) | -80283 (-74402) | +626 (+1095; +635) | 10.13 (10.17) | fails screen |
| 18:00 ET open: AGAINST the day -> target 30  | -80523 (-74402; -8.2%) | -30907 (-31211) | -80199 (-74402) | -929 (-1625; -979) | 9.55 (10.17) | fails screen |
| session VWAP: WITH the day -> target 85  | -80953 (-74402; -8.8%) | -53665 (-31211) | -63862 (-74402) | +2790 (+4883; +2868) | 10.60 (10.17) | fails screen |
| 3-of-4 vote: WITH the day -> trail after +30 by 30  | -81375 (-74402; -9.4%) | -31595 (-31211) | -63893 (-74402) | -3808 (-6664; -3839) | 7.97 (10.17) | fails screen |
| 60-min slope: AGAINST the day -> target 20  | -81394 (-74402; -9.4%) | -27191 (-31211) | -81394 (-74402) | -544 (-952; -563) | 10.06 (10.17) | fails screen |
| session open: WITH the day -> target 85  | -81762 (-74402; -9.9%) | -46285 (-31211) | -63951 (-74402) | +1374 (+2404; +1446) | 10.60 (10.17) | fails screen |
| 60-min slope: WITH the day -> trail after +30 by 30  | -82799 (-74402; -11.3%) | -28444 (-31211) | -54300 (-74402) | -1484 (-2597; -1527) | 7.50 (10.17) | fails screen |
| 18:00 ET open: WITH the day -> target 85  | -83446 (-74402; -12.2%) | -55826 (-31211) | -74089 (-74402) | +114 (+199; +184) | 10.56 (10.17) | fails screen |
| 3-of-4 vote: AGAINST the day -> target 30  | -83669 (-74402; -12.5%) | -36400 (-31211) | -83669 (-74402) | -678 (-1186; -683) | 10.06 (10.17) | fails screen |
| 3-of-4 vote: AGAINST the day -> skip  | -84101 (-74402; -13.0%) | -27415 (-31211) | -84101 (-74402) | -387 (-678; -372) | 9.90 (10.17) | fails screen |
| 60-min slope: AGAINST the day -> size x0.5  | -84287 (-74402; -13.3%) | -36551 (-31211) | -84287 (-74402) | +354 (+620; +370) | 10.17 (10.17) | fails screen |
| session VWAP: AGAINST the day -> size x0.5  | -84757 (-74402; -13.9%) | -37546 (-31211) | -84757 (-74402) | -241 (-422; -233) | 10.21 (10.17) | fails screen |
| 3-of-4 vote: AGAINST the day -> target 40  | -85293 (-74402; -14.6%) | -31799 (-31211) | -85293 (-74402) | -988 (-1729; -989) | 10.09 (10.17) | fails screen |
| 3-of-4 vote: AGAINST the day -> target 20  | -88274 (-74402; -18.6%) | -29704 (-31211) | -88274 (-74402) | -497 (-870; -507) | 9.98 (10.17) | fails screen |
| 18:00 ET open: AGAINST the day -> skip  | -92122 (-74402; -23.8%) | -40851 (-31211) | -56741 (-74402) | -862 (-1508; -748) | 8.43 (10.17) | fails screen |
| 60-min slope: AGAINST the day -> target 40  | -92309 (-74402; -24.1%) | -34251 (-31211) | -92309 (-74402) | -1273 (-2229; -1275) | 10.09 (10.17) | fails screen |
| 60-min slope: WITH the day -> target 85  | -92315 (-74402; -24.1%) | -50521 (-31211) | -56033 (-74402) | +3234 (+5660; +3311) | 10.48 (10.17) | fails screen |
| 60-min slope: AGAINST the day -> target 30  | -95720 (-74402; -28.7%) | -32795 (-31211) | -95720 (-74402) | -1248 (-2184; -1250) | 9.98 (10.17) | fails screen |
| session VWAP: WITH the day -> trail after +30 by 30  | -102410 (-74402; -37.6%) | -27949 (-31211) | -72761 (-74402) | -3729 (-6526; -3769) | 7.50 (10.17) | fails screen |
| session open: WITH the day -> target 120  | -105041 (-74402; -41.2%) | -39165 (-31211) | -105041 (-74402) | -496 (-868; -364) | 10.75 (10.17) | fails screen |
| 60-min slope: WITH the day -> target 120  | -106475 (-74402; -43.1%) | -37557 (-31211) | -106475 (-74402) | +910 (+1592; +1051) | 10.75 (10.17) | fails screen |
| 18:00 ET open: WITH the day -> target 120  | -109406 (-74402; -47.0%) | -39475 (-31211) | -107431 (-74402) | -2200 (-3850; -2075) | 10.40 (10.17) | fails screen |
| 3-of-4 vote: WITH the day -> target 120  | -110258 (-74402; -48.2%) | -39967 (-31211) | -110258 (-74402) | -558 (-976; -427) | 10.71 (10.17) | fails screen |
| session VWAP: WITH the day -> target 120  | -122283 (-74402; -64.4%) | -39223 (-31211) | -106650 (-74402) | +766 (+1341; +911) | 10.67 (10.17) | fails screen |

### Survivors with controls (HOLD; other windows as they land)
| candidate | window | real DD cut / d mean | placebo 1-3 | matched 1-3 | verdict |
|---|---|---|---|---|---|
| session VWAP: AGAINST the day -> skip  | HOLD | +3.1% / +207 | +18.5% / -1911; +20.4% / -4830; +14.4% / -5871 | +1.2% / +640; -2.4% / -26; -0.0% / +58 | FAILS this window |
| session VWAP: AGAINST the day -> skip  | L6M | -26.3% / -493 | n/f; n/f; n/f | n/f; n/f; n/f | not finished (controls pending) |
| session VWAP: AGAINST the day -> skip  | L3M | -26.3% / +1158 | n/f; n/f; n/f | n/f; n/f; n/f | not finished (controls pending) |
| session VWAP: AGAINST the day -> skip  | GAP | -23.9% / -1599 | +38.0% / -4189; -8.4% / -7603; -16.7% / -5870 | +1.0% / +813; +6.2% / +114; +0.1% / -188 | FAILS this window |
| session VWAP: AGAINST the day -> skip  | PRE | +14.8% / -534 | n/f; n/f; n/f | n/f; n/f; n/f | not finished (controls pending) |
| session VWAP: AGAINST the day -> skip  | X' | -46.0% / +178 | n/f; n/f; n/f | n/f; n/f; n/f | not finished (controls pending) |

## (W-BD2) DS3_BRACKET_DD_D - T-BRACKET-DD Parts D (partial exits), C (target by room), E (time) on TL3_EV_JN05W2JL2 (W-BD2)
> VALIDATION (W-DV, FIRST PASS, 2026-11-16): trials counted BD parts C 5 + D 8 + E 10 + F 22 engine cells, N_used from replay (TRIALS_LEDGER.csv TB-BDC..F); correction not applied (cells have 1-12 months, too short for RC / SPA on a common window); PBO not fitted; number shown is IN-SAMPLE; data end 2026-10-31.
**VERDICT (data ends 2026-10-31; FIRST PASS, rebuilt 16:04Z UTC): NO candidate qualifies yet (see per-candidate rows; some are not finished). Not finished candidates are listed as such; no row is called a lead without its 6 controls. Dollars BASE lots; live = x1.75; $4.84 = FEES.md RT repriced (net - lots x 3.66).**

Status per candidate (windows with real + 6 controls all finished): C M7 london lvl k1.0: none; C H7 asia har k1.0: none; C K7 nypm lvl k0.8: none; C M7 london har k0.5: none; D K7 nyam X15 T58 BE1 (Step1 b): none; D K7 nyam X40 T85 BE1: none; D M7 london X20 TR15: none; D K7 london X40 T85 BE1: none; D M7 nyam X40 T85 BE0: none; D K7 london X40 T58 BE0: none; D U7 london X40 T85 BE0: none; E U7 asia tstop60<5: none; E U7 asia tstop30<5: none; E U7 london tstop30<5: none; E U7 london tstop60<5: none; E M7 london steps60: none; E K7 london tstop30<5: none

Definitions. Reference = TL3_EV_JN05W2JL2 (final, 43 months), live layers unchanged. Windows: HOLD 2025-11-01..2026-04-30; HP = HOLD path 2025-11-17..2025-12-10; L6M 2026-05..10; L3M 2026-08..10; GAP 2026-02-07..04-30; PRE 2024-10..2025-06; X' 2023-04..2024-01 (same definitions as DS3_BRACKET_BUILD). DD = whole-stack max drawdown of cumulative daily $ (Globex day of exit). Placebo (3 seeds) = the same rule applied to a pseudo-random subset of ALL signals (every book x session) with the same expected count as the cell (share of all signals). Matched random control (3 seeds) = the same rule on a pseudo-random 50% of the cell's own book x session signals (same book x session x month mix, half the count: read against half the real effect). Pass (addendum): DD cut > 0 vs reference, beats ALL 6 controls on DD cut, d mean not below -5% of the reference mean, in HOLD and L6M; neighbours must agree (surface). Lots at live values: the rules change no lots (stop unchanged; the breakeven stop only follows the partial), so the constant-risk column (lots x baseStop/newStop) equals the live-lots column.

## Window HOLD (20251101..20260430)

| candidate | real (drawdown first) | W44 removed | verdict |
|---|---|---|---|
| C M7 london lvl k1.0 | not finished | n/a | not finished |
| C H7 asia har k1.0 | not finished | n/a | not finished |
| C K7 nypm lvl k0.8 | not finished | n/a | not finished |
| C M7 london har k0.5 | not finished | n/a | not finished |
| D K7 nyam X15 T58 BE1 (Step1 b) | not finished | n/a | not finished |
| D K7 nyam X40 T85 BE1 | not finished | n/a | not finished |
| D M7 london X20 TR15 | not finished | n/a | not finished |
| D K7 london X40 T85 BE1 | not finished | n/a | not finished |
| D M7 nyam X40 T85 BE0 | not finished | n/a | not finished |
| D K7 london X40 T58 BE0 | not finished | n/a | not finished |
| D U7 london X40 T85 BE0 | not finished | n/a | not finished |
| E U7 asia tstop60<5 | DD -67360 (ref -74402; +9.5%), worst wk -35178 (ref -31211), d mean -536/wk (live x1.75 -938; $4.84 -538; -6.4% of ref), n 3217 (3219) | n/a | not finished (controls 3/6 done) |
| E U7 asia tstop30<5 | not finished | n/a | not finished |
| E U7 london tstop30<5 | not finished | n/a | not finished |
| E U7 london tstop60<5 | not finished | n/a | not finished |
| E M7 london steps60 | not finished | n/a | not finished |
| E K7 london tstop30<5 | not finished | n/a | not finished |

Controls (DD cut % vs reference / d mean $/wk):
| candidate | placebo 1 | placebo 2 | placebo 3 | matched 1 | matched 2 | matched 3 |
|---|---|---|---|---|---|---|
| C M7 london lvl k1.0 | n/f | n/f | n/f | n/f | n/f | n/f |
| C H7 asia har k1.0 | n/f | n/f | n/f | n/f | n/f | n/f |
| C K7 nypm lvl k0.8 | n/f | n/f | n/f | n/f | n/f | n/f |
| C M7 london har k0.5 | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 nyam X15 T58 BE1 (Step1 b) | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 nyam X40 T85 BE1 | n/f | n/f | n/f | n/f | n/f | n/f |
| D M7 london X20 TR15 | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 london X40 T85 BE1 | n/f | n/f | n/f | n/f | n/f | n/f |
| D M7 nyam X40 T85 BE0 | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 london X40 T58 BE0 | n/f | n/f | n/f | n/f | n/f | n/f |
| D U7 london X40 T85 BE0 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 asia tstop60<5 | -0.3% / -145 | +14.3% / -306 | +3.4% / +290 | n/f | n/f | n/f |
| E U7 asia tstop30<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 london tstop30<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 london tstop60<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E M7 london steps60 | n/f | n/f | n/f | n/f | n/f | n/f |
| E K7 london tstop30<5 | n/f | n/f | n/f | n/f | n/f | n/f |

## Window HP (20251117..20251210)

| candidate | real (drawdown first) | W44 removed | verdict |
|---|---|---|---|
| C M7 london lvl k1.0 | not finished | n/a | not finished |
| C H7 asia har k1.0 | not finished | n/a | not finished |
| C K7 nypm lvl k0.8 | not finished | n/a | not finished |
| C M7 london har k0.5 | not finished | n/a | not finished |
| D K7 nyam X15 T58 BE1 (Step1 b) | not finished | n/a | not finished |
| D K7 nyam X40 T85 BE1 | not finished | n/a | not finished |
| D M7 london X20 TR15 | not finished | n/a | not finished |
| D K7 london X40 T85 BE1 | not finished | n/a | not finished |
| D M7 nyam X40 T85 BE0 | not finished | n/a | not finished |
| D K7 london X40 T58 BE0 | not finished | n/a | not finished |
| D U7 london X40 T85 BE0 | not finished | n/a | not finished |
| E U7 asia tstop60<5 | DD -67360 (ref -74402; +9.5%), worst wk -34178 (ref -31211), d mean +2054/wk (live x1.75 +3594; $4.84 +2051; +12.1% of ref), n 408 (407) | n/a | not finished (controls 4/6 done) |
| E U7 asia tstop30<5 | not finished | n/a | not finished |
| E U7 london tstop30<5 | not finished | n/a | not finished |
| E U7 london tstop60<5 | not finished | n/a | not finished |
| E M7 london steps60 | not finished | n/a | not finished |
| E K7 london tstop30<5 | not finished | n/a | not finished |

Controls (DD cut % vs reference / d mean $/wk):
| candidate | placebo 1 | placebo 2 | placebo 3 | matched 1 | matched 2 | matched 3 |
|---|---|---|---|---|---|---|
| C M7 london lvl k1.0 | n/f | n/f | n/f | n/f | n/f | n/f |
| C H7 asia har k1.0 | n/f | n/f | n/f | n/f | n/f | n/f |
| C K7 nypm lvl k0.8 | n/f | n/f | n/f | n/f | n/f | n/f |
| C M7 london har k0.5 | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 nyam X15 T58 BE1 (Step1 b) | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 nyam X40 T85 BE1 | n/f | n/f | n/f | n/f | n/f | n/f |
| D M7 london X20 TR15 | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 london X40 T85 BE1 | n/f | n/f | n/f | n/f | n/f | n/f |
| D M7 nyam X40 T85 BE0 | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 london X40 T58 BE0 | n/f | n/f | n/f | n/f | n/f | n/f |
| D U7 london X40 T85 BE0 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 asia tstop60<5 | -0.3% / -73 | +14.3% / +3099 | +3.4% / +735 | +6.7% / +1448 | n/f | n/f |
| E U7 asia tstop30<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 london tstop30<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 london tstop60<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E M7 london steps60 | n/f | n/f | n/f | n/f | n/f | n/f |
| E K7 london tstop30<5 | n/f | n/f | n/f | n/f | n/f | n/f |

## Window L6M (20260501..20261031)

| candidate | real (drawdown first) | W44 removed | verdict |
|---|---|---|---|
| C M7 london lvl k1.0 | not finished | not finished | not finished |
| C H7 asia har k1.0 | not finished | not finished | not finished |
| C K7 nypm lvl k0.8 | not finished | not finished | not finished |
| C M7 london har k0.5 | not finished | not finished | not finished |
| D K7 nyam X15 T58 BE1 (Step1 b) | not finished | not finished | not finished |
| D K7 nyam X40 T85 BE1 | not finished | not finished | not finished |
| D M7 london X20 TR15 | not finished | not finished | not finished |
| D K7 london X40 T85 BE1 | not finished | not finished | not finished |
| D M7 nyam X40 T85 BE0 | not finished | not finished | not finished |
| D K7 london X40 T58 BE0 | not finished | not finished | not finished |
| D U7 london X40 T85 BE0 | not finished | not finished | not finished |
| E U7 asia tstop60<5 | not finished | not finished | not finished |
| E U7 asia tstop30<5 | not finished | not finished | not finished |
| E U7 london tstop30<5 | not finished | not finished | not finished |
| E U7 london tstop60<5 | not finished | not finished | not finished |
| E M7 london steps60 | not finished | not finished | not finished |
| E K7 london tstop30<5 | not finished | not finished | not finished |

Controls (DD cut % vs reference / d mean $/wk):
| candidate | placebo 1 | placebo 2 | placebo 3 | matched 1 | matched 2 | matched 3 |
|---|---|---|---|---|---|---|
| C M7 london lvl k1.0 | n/f | n/f | n/f | n/f | n/f | n/f |
| C H7 asia har k1.0 | n/f | n/f | n/f | n/f | n/f | n/f |
| C K7 nypm lvl k0.8 | n/f | n/f | n/f | n/f | n/f | n/f |
| C M7 london har k0.5 | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 nyam X15 T58 BE1 (Step1 b) | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 nyam X40 T85 BE1 | n/f | n/f | n/f | n/f | n/f | n/f |
| D M7 london X20 TR15 | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 london X40 T85 BE1 | n/f | n/f | n/f | n/f | n/f | n/f |
| D M7 nyam X40 T85 BE0 | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 london X40 T58 BE0 | n/f | n/f | n/f | n/f | n/f | n/f |
| D U7 london X40 T85 BE0 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 asia tstop60<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 asia tstop30<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 london tstop30<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 london tstop60<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E M7 london steps60 | n/f | n/f | n/f | n/f | n/f | n/f |
| E K7 london tstop30<5 | n/f | n/f | n/f | n/f | n/f | n/f |

## Window L3M (20260801..20261031)

| candidate | real (drawdown first) | W44 removed | verdict |
|---|---|---|---|
| C M7 london lvl k1.0 | not finished | not finished | not finished |
| C H7 asia har k1.0 | not finished | not finished | not finished |
| C K7 nypm lvl k0.8 | not finished | not finished | not finished |
| C M7 london har k0.5 | not finished | not finished | not finished |
| D K7 nyam X15 T58 BE1 (Step1 b) | not finished | not finished | not finished |
| D K7 nyam X40 T85 BE1 | not finished | not finished | not finished |
| D M7 london X20 TR15 | not finished | not finished | not finished |
| D K7 london X40 T85 BE1 | not finished | not finished | not finished |
| D M7 nyam X40 T85 BE0 | not finished | not finished | not finished |
| D K7 london X40 T58 BE0 | not finished | not finished | not finished |
| D U7 london X40 T85 BE0 | not finished | not finished | not finished |
| E U7 asia tstop60<5 | not finished | not finished | not finished |
| E U7 asia tstop30<5 | not finished | not finished | not finished |
| E U7 london tstop30<5 | not finished | not finished | not finished |
| E U7 london tstop60<5 | not finished | not finished | not finished |
| E M7 london steps60 | not finished | not finished | not finished |
| E K7 london tstop30<5 | not finished | not finished | not finished |

Controls (DD cut % vs reference / d mean $/wk):
| candidate | placebo 1 | placebo 2 | placebo 3 | matched 1 | matched 2 | matched 3 |
|---|---|---|---|---|---|---|
| C M7 london lvl k1.0 | n/f | n/f | n/f | n/f | n/f | n/f |
| C H7 asia har k1.0 | n/f | n/f | n/f | n/f | n/f | n/f |
| C K7 nypm lvl k0.8 | n/f | n/f | n/f | n/f | n/f | n/f |
| C M7 london har k0.5 | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 nyam X15 T58 BE1 (Step1 b) | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 nyam X40 T85 BE1 | n/f | n/f | n/f | n/f | n/f | n/f |
| D M7 london X20 TR15 | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 london X40 T85 BE1 | n/f | n/f | n/f | n/f | n/f | n/f |
| D M7 nyam X40 T85 BE0 | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 london X40 T58 BE0 | n/f | n/f | n/f | n/f | n/f | n/f |
| D U7 london X40 T85 BE0 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 asia tstop60<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 asia tstop30<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 london tstop30<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 london tstop60<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E M7 london steps60 | n/f | n/f | n/f | n/f | n/f | n/f |
| E K7 london tstop30<5 | n/f | n/f | n/f | n/f | n/f | n/f |

## Window GAP (20260207..20260430)

| candidate | real (drawdown first) | W44 removed | verdict |
|---|---|---|---|
| C M7 london lvl k1.0 | not finished | n/a | not finished |
| C H7 asia har k1.0 | not finished | n/a | not finished |
| C K7 nypm lvl k0.8 | not finished | n/a | not finished |
| C M7 london har k0.5 | not finished | n/a | not finished |
| D K7 nyam X15 T58 BE1 (Step1 b) | not finished | n/a | not finished |
| D K7 nyam X40 T85 BE1 | not finished | n/a | not finished |
| D M7 london X20 TR15 | not finished | n/a | not finished |
| D K7 london X40 T85 BE1 | not finished | n/a | not finished |
| D M7 nyam X40 T85 BE0 | not finished | n/a | not finished |
| D K7 london X40 T58 BE0 | not finished | n/a | not finished |
| D U7 london X40 T85 BE0 | not finished | n/a | not finished |
| E U7 asia tstop60<5 | DD -66335 (ref -54615; -21.5%), worst wk -35178 (ref -30852), d mean -2312/wk (live x1.75 -4046; $4.84 -2310; -23.6% of ref), n 1603 (1613) | n/a | not finished (controls 3/6 done) |
| E U7 asia tstop30<5 | not finished | n/a | not finished |
| E U7 london tstop30<5 | not finished | n/a | not finished |
| E U7 london tstop60<5 | not finished | n/a | not finished |
| E M7 london steps60 | not finished | n/a | not finished |
| E K7 london tstop30<5 | not finished | n/a | not finished |

Controls (DD cut % vs reference / d mean $/wk):
| candidate | placebo 1 | placebo 2 | placebo 3 | matched 1 | matched 2 | matched 3 |
|---|---|---|---|---|---|---|
| C M7 london lvl k1.0 | n/f | n/f | n/f | n/f | n/f | n/f |
| C H7 asia har k1.0 | n/f | n/f | n/f | n/f | n/f | n/f |
| C K7 nypm lvl k0.8 | n/f | n/f | n/f | n/f | n/f | n/f |
| C M7 london har k0.5 | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 nyam X15 T58 BE1 (Step1 b) | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 nyam X40 T85 BE1 | n/f | n/f | n/f | n/f | n/f | n/f |
| D M7 london X20 TR15 | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 london X40 T85 BE1 | n/f | n/f | n/f | n/f | n/f | n/f |
| D M7 nyam X40 T85 BE0 | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 london X40 T58 BE0 | n/f | n/f | n/f | n/f | n/f | n/f |
| D U7 london X40 T85 BE0 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 asia tstop60<5 | -7.3% / -201 | -5.7% / -1337 | +0.0% / +571 | n/f | n/f | n/f |
| E U7 asia tstop30<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 london tstop30<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 london tstop60<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E M7 london steps60 | n/f | n/f | n/f | n/f | n/f | n/f |
| E K7 london tstop30<5 | n/f | n/f | n/f | n/f | n/f | n/f |

## Window PRE (20241001..20250630)

| candidate | real (drawdown first) | W44 removed | verdict |
|---|---|---|---|
| C M7 london lvl k1.0 | not finished | n/a | not finished |
| C H7 asia har k1.0 | not finished | n/a | not finished |
| C K7 nypm lvl k0.8 | not finished | n/a | not finished |
| C M7 london har k0.5 | not finished | n/a | not finished |
| D K7 nyam X15 T58 BE1 (Step1 b) | not finished | n/a | not finished |
| D K7 nyam X40 T85 BE1 | not finished | n/a | not finished |
| D M7 london X20 TR15 | not finished | n/a | not finished |
| D K7 london X40 T85 BE1 | not finished | n/a | not finished |
| D M7 nyam X40 T85 BE0 | not finished | n/a | not finished |
| D K7 london X40 T58 BE0 | not finished | n/a | not finished |
| D U7 london X40 T85 BE0 | not finished | n/a | not finished |
| E U7 asia tstop60<5 | not finished | n/a | not finished |
| E U7 asia tstop30<5 | not finished | n/a | not finished |
| E U7 london tstop30<5 | not finished | n/a | not finished |
| E U7 london tstop60<5 | not finished | n/a | not finished |
| E M7 london steps60 | not finished | n/a | not finished |
| E K7 london tstop30<5 | not finished | n/a | not finished |

Controls (DD cut % vs reference / d mean $/wk):
| candidate | placebo 1 | placebo 2 | placebo 3 | matched 1 | matched 2 | matched 3 |
|---|---|---|---|---|---|---|
| C M7 london lvl k1.0 | n/f | n/f | n/f | n/f | n/f | n/f |
| C H7 asia har k1.0 | n/f | n/f | n/f | n/f | n/f | n/f |
| C K7 nypm lvl k0.8 | n/f | n/f | n/f | n/f | n/f | n/f |
| C M7 london har k0.5 | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 nyam X15 T58 BE1 (Step1 b) | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 nyam X40 T85 BE1 | n/f | n/f | n/f | n/f | n/f | n/f |
| D M7 london X20 TR15 | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 london X40 T85 BE1 | n/f | n/f | n/f | n/f | n/f | n/f |
| D M7 nyam X40 T85 BE0 | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 london X40 T58 BE0 | n/f | n/f | n/f | n/f | n/f | n/f |
| D U7 london X40 T85 BE0 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 asia tstop60<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 asia tstop30<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 london tstop30<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 london tstop60<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E M7 london steps60 | n/f | n/f | n/f | n/f | n/f | n/f |
| E K7 london tstop30<5 | n/f | n/f | n/f | n/f | n/f | n/f |

## Window X' (20230401..20240131)

| candidate | real (drawdown first) | W44 removed | verdict |
|---|---|---|---|
| C M7 london lvl k1.0 | not finished | n/a | not finished |
| C H7 asia har k1.0 | not finished | n/a | not finished |
| C K7 nypm lvl k0.8 | not finished | n/a | not finished |
| C M7 london har k0.5 | not finished | n/a | not finished |
| D K7 nyam X15 T58 BE1 (Step1 b) | not finished | n/a | not finished |
| D K7 nyam X40 T85 BE1 | not finished | n/a | not finished |
| D M7 london X20 TR15 | not finished | n/a | not finished |
| D K7 london X40 T85 BE1 | not finished | n/a | not finished |
| D M7 nyam X40 T85 BE0 | not finished | n/a | not finished |
| D K7 london X40 T58 BE0 | not finished | n/a | not finished |
| D U7 london X40 T85 BE0 | not finished | n/a | not finished |
| E U7 asia tstop60<5 | not finished | n/a | not finished |
| E U7 asia tstop30<5 | not finished | n/a | not finished |
| E U7 london tstop30<5 | not finished | n/a | not finished |
| E U7 london tstop60<5 | not finished | n/a | not finished |
| E M7 london steps60 | not finished | n/a | not finished |
| E K7 london tstop30<5 | not finished | n/a | not finished |

Controls (DD cut % vs reference / d mean $/wk):
| candidate | placebo 1 | placebo 2 | placebo 3 | matched 1 | matched 2 | matched 3 |
|---|---|---|---|---|---|---|
| C M7 london lvl k1.0 | n/f | n/f | n/f | n/f | n/f | n/f |
| C H7 asia har k1.0 | n/f | n/f | n/f | n/f | n/f | n/f |
| C K7 nypm lvl k0.8 | n/f | n/f | n/f | n/f | n/f | n/f |
| C M7 london har k0.5 | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 nyam X15 T58 BE1 (Step1 b) | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 nyam X40 T85 BE1 | n/f | n/f | n/f | n/f | n/f | n/f |
| D M7 london X20 TR15 | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 london X40 T85 BE1 | n/f | n/f | n/f | n/f | n/f | n/f |
| D M7 nyam X40 T85 BE0 | n/f | n/f | n/f | n/f | n/f | n/f |
| D K7 london X40 T58 BE0 | n/f | n/f | n/f | n/f | n/f | n/f |
| D U7 london X40 T85 BE0 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 asia tstop60<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 asia tstop30<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 london tstop30<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E U7 london tstop60<5 | n/f | n/f | n/f | n/f | n/f | n/f |
| E M7 london steps60 | n/f | n/f | n/f | n/f | n/f | n/f |
| E K7 london tstop30<5 | n/f | n/f | n/f | n/f | n/f | n/f |


