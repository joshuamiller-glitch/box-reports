# DS3_CELL_TESTS - engine cell tests: do not trade / half size weak book x session cells on JL3 and JL2 (W-CELL, order 11-17 07:28Z JOB 2)
VERDICT (data ends 2026-10-31; FIRST PASS; see below)

> VALIDATION (desk standard, W-CELL, FIRST PASS, 2026-11-24 17:28Z): trials counted = 26 real engine cells (13 cell definitions x JL3 and JL2: 6 do-not-trade singles + the four weakest together + 5 half-size singles + the four weakest half-sized; K7 NY AM is 1 lot so not halvable), each reported, no best-of selection (ledger family CT1); correction = percentile among 30 persistent-draw engine controls per cell (JL3 only; valid draws only) + week-clustered bootstrap (2,000) + the calibrated ulcer-primary tiers of DS3_PASS_RULE (cutoffs_ulc TUNED); no family-wide White/SPA because no cell is selected as best; PBO not applicable (no fitted choice); numbers shown: IN-SAMPLE (every window is part of the 43 months; the cells are fixed by the stage-0/1 raw table, not fitted per window; walk-forward not applicable). Data ends 2026-10-31.
## M7 London focus (lead order 10:48Z; DO NOT TRADE M7 London = M7 session lots london 0)

Row (a) - JL3 cell vs JL3 base at the live price columns: mean $/wk change, max DD and worst week (base -> cell), ulcer change.

| column | window | mean $/wk base -> cell (change) | max DD base -> cell | worst week base -> cell | ulcer change |
|--|--|--|--|--|--|
| engine base lots $1.18 RT | L6M | 20,109 -> 21,147 (+1,038) | -30,189 -> -23,870 | -15,066 -> -14,160 | +15.0% |
| engine base lots $1.18 RT | HOLD | 9,996 -> 9,552 (-445) | -82,017 -> -67,418 | -36,787 -> -34,209 | +11.8% |
| engine base lots $1.18 RT | pooled | 8,022 -> 8,528 (+506) | -88,502 -> -76,979 | -38,412 -> -36,455 | +11.7% |
| $4.84 RT, base lots | L6M | 19,265 -> 20,359 (+1,093) | -31,112 -> -24,760 | -15,728 -> -14,786 | +14.8% |
| $4.84 RT, base lots | HOLD | 9,332 -> 8,942 (-389) | -83,755 -> -69,021 | -37,321 -> -34,688 | +12.3% |
| $4.84 RT, base lots | pooled | 7,493 -> 8,042 (+549) | -91,437 -> -79,673 | -38,899 -> -36,894 | +12.8% |
| x1.75 live lots, $1.18 RT | L6M | 37,463 -> 39,514 (+2,051) | -60,591 -> -46,986 | -31,735 -> -29,923 | +16.4% |
| x1.75 live lots, $1.18 RT | HOLD | 19,402 -> 18,442 (-961) | -152,332 -> -124,305 | -71,572 -> -66,416 | +12.3% |
| x1.75 live lots, $1.18 RT | pooled | 15,137 -> 16,121 (+984) | -172,602 -> -149,519 | -75,818 -> -71,909 | +12.7% |

Row (b) - FREED-BOOK effect, JL3, M7 London off (trades and $ at engine base lots; n lost ($) / n gained ($) / $ change on trades both runs share). M7 London lost trades are M7's own removed trades; K7/P7/U7/H7 London gains are other books using the freed room.

| window | M7 own London trades removed | K7 London | P7 London | U7 London | H7 London | K7+P7+U7+H7+A7+O7 other sessions (all, net $) | whole-stack $ change |
|--|--|--|--|--|--|--|--|
| L6M | 522 (-2,117) | 6 (-2,344) / 81 (+14,583) / +997 (5) | 3 (-2,540) / 33 (-2,286) / -1,718 (10) | 1 (-1,254) / 12 (+3,258) / +2,005 (3) | 0 (+0) / 7 (-950) / +0 (0) | +8,146 | +37,989 |
| HOLD | 454 (-9,112) | 18 (+1,471) / 63 (-15,788) / -796 (3) | 3 (+7,297) / 27 (+3,151) / -1,422 (5) | 0 (+0) / 7 (+12,128) / -3,110 (2) | 1 (-1,181) / 1 (+934) / +0 (0) | -12,355 | -29,527 |
| pooled | 2495 (-52,356) | 71 (-2,337) / 305 (+11,907) / -1,943 (19) | 34 (-2,249) / 114 (+7,698) / -5,772 (45) | 1 (-1,254) / 24 (+19,362) / +5,673 (21) | 1 (-1,181) / 23 (-1,358) / +0 (0) | +2,390 | +90,690 |

One line: L6M: M7 London own trades removed carried +2,117, other books in London net +22,027, other sessions net +8,146, stack total +37,989; HOLD: M7 London own trades removed carried +9,112, other books in London net -12,489, other sessions net -12,355, stack total -29,527; pooled: M7 London own trades removed carried +52,356, other books in London net +42,591, other sessions net +2,390, stack total +90,690. (Positive "own trades removed" means M7 London lost money in the base; the stack total is the whole-stack $ change, not the mean per week.)

Row (3) - why JL2 and JL3 disagree on ulcer for this cell:
- JL3 = JL2 + live persist=1 take lines (M7 pct >= 0.95 take with target 59.5) and P7/U7/H7 locks. In M7 London over 43 months JL2 has 2420 trades, net -66,772; JL3 has 2455 trades, net -60,492. M7 London exits JL2: StateCut 1230, Target 958, StopJoin 116, StopJoinFallback 67, StackCut 26. JL3: StateCut 1233, PolicyTake 496, Target 496, StopJoin 114, StopJoinFallback 68.
- Pooled: JL3 ulcer change +11.7% (mean +506 $/wk); JL2 +0.7% (mean +399 $/wk). Base ulcer (RMS daily drawdown, $) JL3 24,344 vs JL2 20,293. The difference is the stack, not M7 London itself: JL3 turns about half of M7 London's Target exits into PolicyTake exits (M7 London loses a little less, -60k vs -67k), and its P7/U7/H7 locks lengthen the other books' drawdowns (higher base ulcer, 24.3k vs 20.3k), so removing M7 London's trades takes out a larger share of the stack's drawdown in JL3 and leaves the freed room to different trades. Freed-room table above is JL3; JL2 M7 London own trades removed carried +61,977.

Row (c) - M7 London DO NOT TRADE (JL3) per window: percentile of the real cell among its OWN valid controls (share of valid controls the cell beats; higher = better), number of valid controls in that window, ulcer change. Tier = CONFIRMED; W44 variant = CONFIRMED.

| window | valid controls (of landed) | pct ulcer | pct mean | pct max DD | pct worst week | ulcer change | mean change $/wk | P(ulcer lower) |
|--|--|--|--|--|--|--|--|--|
| L6M | 19 (of 31) | 1.00 | 0.95 | 0.95 | 0.89 | +15.0% | +1,038 | 0.83 |
| HOLD | 19 (of 30) | 0.95 | 0.53 | 0.89 | 0.11 | +11.8% | -445 | 0.80 |
| GAP | 19 (of 29) | 0.26 | 0.95 | 0.21 | 0.05 | +14.4% | +1,859 | 0.98 |
| PRE | 19 (of 29) | 0.37 | 1.00 | 0.42 | 0.53 | +17.5% | +314 | 0.92 |
| X' | 19 (of 19) | 0.32 | 0.21 | 0.58 | 1.00 | +5.7% | +443 | 0.88 |
| pooled | 19 (of 19) | 0.68 | 0.89 | 0.58 | 0.11 | +11.7% | +506 | 0.98 |

Row (d) - half-session variants (JL3, real cells only, no controls): M7 London lots 0 only 02:00-05:00 ET, or only 05:00-08:30 ET (hook th_cell/ct_hooks.py; inert setting TL3_CT_JL3_X_ID = base). Ulcer change / mean change $/wk base lots / max DD base -> cell.

| variant | L6M | HOLD | pooled (months landed) |
|--|--|--|--|
| zero 02:00-05:00 ET only (43 mo) | -5.5% / -1,312 / -30,189 -> -31,395 | +2.4% / -814 / -82,017 -> -70,179 | +11.8% / +88 / -88,502 -> -70,179 |
| zero 05:00-08:30 ET only (43 mo) | +12.1% / +1,228 / -30,189 -> -24,519 | +15.1% / +198 / -82,017 -> -69,728 | +4.0% / +358 / -88,502 -> -87,287 |
| whole London (reference) (43 mo) | +15.0% / +1,038 / -30,189 -> -23,870 | +11.8% / -445 / -82,017 -> -67,418 | +11.7% / +506 / -88,502 -> -76,979 |



## Status (what has landed)
- Base months landed: JL3 44 of 43, JL2 44 of 43. Real cells with at least one scored window: 26 of 26; with all 43 months: 26.
- Controls (JL3 + persistent random skip): N M7 London 60 landed / 19 valid; N K7 NY AM 30 landed / 0 valid; N P7 London 30 landed / 0 valid; N P7 NY AM 30 landed / 0 valid; N K7 NY PM 30 landed / 0 valid; N K7 London 30 landed / 0 valid; N four weakest (M7 Lon 30 landed / 0 valid; H M7 London 60 landed / 0 valid; H P7 London 30 landed / 0 valid; H P7 NY AM 30 landed / 0 valid; H K7 NY PM 30 landed / 0 valid; H K7 London 30 landed / 0 valid; H four weakest (M7 Lon 30 landed / 0 valid. A cell with fewer than 10 valid controls in a window is NOT FINISHED, never passing.
- Mechanism: ev_panel hook (outermost) overrides the book session lot table: do-not-trade = lots 0 in that session (engine entry gate, same as M7 asia = 0 today), half = lots/2 rounded half up (K7 2->1, M7 2->1, P7 4->2). Everything else (stack cap, locks, cuts, sizer, day caps, freed stack room, re-entries) runs unchanged = engine test, not path arithmetic. Identity cells TL3_CT_JL3_ID / TL3_CT_JL2_ID: TL3_CT_JL3_ID 202609: 647 trades net 85599.32 vs TL3_EV_JL3 647 net 85599.32 -> IDENTICAL; TL3_CT_JL3_ID 202610: 691 trades net 37159.82 vs TL3_EV_JL3 691 net 37159.82 -> IDENTICAL; TL3_CT_JL2_ID 202609: 645 trades net 113229.66 vs TL3_EV_JN05W2JL2 645 net 113229.66 -> IDENTICAL; TL3_CT_JL2_ID 202610: 642 trades net 27487.58 vs TL3_EV_JN05W2JL2 642 net 27487.58 -> IDENTICAL.
- Four weakest chosen by the raw-base table (DS3_REBUILD_S1 / S0: one book alone, no layers): lowest mean R per trade: M7 London -0.009 (net -$48k), P7 NY AM 0.006, P7 London 0.008, K7 NY AM 0.008 (net $18k over 43 months); next K7 NY PM 0.015, K7 London 0.024. Stage 5 has no session-lot leave-one-out, so the raw base decides.
- Controls: book-wide persistent random skip (one uniform per 5-minute bucket, book, side; same seed set across cells), p calibrated by pilots so the realised share of the book removed matches the cell share within max(min(0.05, 0.25 x share), 0.002) (stricter than 0.05 for small shares); draw valid if pooled over its landed months it is within that tolerance. Half-size stand-in controls: 50% persistent skip inside the cell session, L6M + HOLD months only (so half-size tiers cannot reach older windows: shown as PROVISIONAL/NOT FINISHED).

## Table 1 - JL3: ulcer change / mean change per window (engine base lots; ulcer + = lower than base)
Cell vs JL3 base, same engine, same months. ulcer cell = % change of RMS daily drawdown (+ better); d mean = $/wk base lots (x1.75 and $4.84 in Table 3). P(ulcer lower) week-clustered bootstrap 2,000. Percentile (pct) = share of valid controls the real cell beats on ulcer / mean / max DD (L6M and HOLD). Tier from calibrated tiers; W44 = week 2026-10-26..11-01 removed.

| cell | L6M | HOLD | GAP | PRE | X' | pooled | P(ulcer lower) L6M / HOLD / pooled | max DD base -> cell, L6M / pooled | worst week base -> cell, L6M / pooled | pct ulcer / mean / DD, L6M | pct, HOLD | valid controls L6M | tier | tier W44 |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| DO NOT TRADE M7 London (43 mo) | +15.0% / +1,038 | +11.8% / -445 | +14.4% / +1,859 | +17.5% / +314 | +5.7% / +443 | +11.7% / +506 | 0.83 / 0.80 / 0.98 | -30,189 -> -23,870 / -88,502 -> -76,979 | -15,066 -> -14,160 / -38,412 -> -36,455 | 1.00 / 0.95 / 0.95 | 0.95 / 0.53 / 0.89 | 19 of 31 landed | CONFIRMED | CONFIRMED |
| DO NOT TRADE K7 NY AM (43 mo) | -16.1% / +171 | +3.5% / -515 | +1.0% / +1,250 | -8.4% / -942 | -4.6% / -466 | -4.3% / -438 | 0.01 / 0.68 / 0.40 | -30,189 -> -37,671 / -88,502 -> -88,029 | -15,066 -> -19,093 / -38,412 -> -37,966 | n/a | n/a | 0 of 0 landed | NOT FINISHED (fewer than 10 valid controls in L6M/L3M) | NOT FINISHED |
| DO NOT TRADE P7 London (43 mo) | -2.0% / -1,883 | +8.3% / -1,237 | +16.2% / +1,070 | +40.5% / +1,927 | +5.1% / -127 | +15.6% / -16 | 0.20 / 0.27 / 0.83 | -30,189 -> -31,637 / -88,502 -> -73,812 | -15,066 -> -17,426 / -38,412 -> -34,644 | n/a | n/a | 0 of 0 landed | NOT FINISHED (fewer than 10 valid controls in L6M/L3M) | NOT FINISHED |
| DO NOT TRADE P7 NY AM (43 mo) | +2.7% / -395 | +0.4% / -566 | -3.8% / -386 | +4.3% / +555 | -3.3% / -110 | +0.8% / -94 | 0.93 / 0.47 / 0.58 | -30,189 -> -28,337 / -88,502 -> -87,259 | -15,066 -> -14,441 / -38,412 -> -39,775 | n/a | n/a | 0 of 0 landed | NOT FINISHED (fewer than 10 valid controls in L6M/L3M) | NOT FINISHED |
| DO NOT TRADE K7 NY PM (43 mo) | -1.9% / -860 | +0.7% / -238 | -0.2% / -1,071 | +13.0% / +134 | -16.0% / -434 | -0.3% / -472 | 0.33 / 0.49 / 0.52 | -30,189 -> -31,822 / -88,502 -> -82,239 | -15,066 -> -17,515 / -38,412 -> -37,654 | n/a | n/a | 0 of 0 landed | NOT FINISHED (fewer than 10 valid controls in L6M/L3M) | NOT FINISHED |
| DO NOT TRADE K7 London (43 mo) | -2.7% / -519 | -0.0% / -1,778 | +0.1% / -675 | +12.3% / -59 | +3.7% / +273 | +6.9% / -321 | 0.47 / 0.14 / 0.60 | -30,189 -> -26,923 / -88,502 -> -76,362 | -15,066 -> -19,605 / -38,412 -> -35,742 | n/a | n/a | 0 of 0 landed | NOT FINISHED (fewer than 10 valid controls in L6M/L3M) | NOT FINISHED |
| DO NOT TRADE four weakest (M7 London + P7 NY AM + P7 London + K7 NY AM) (43 mo) | -10.9% / -1,181 | +9.6% / -2,090 | +23.8% / +2,893 | +49.1% / +1,189 | +5.2% / -137 | +19.5% / -117 | 0.14 / 0.63 / 0.94 | -30,189 -> -32,384 / -88,502 -> -74,167 | -15,066 -> -22,847 / -38,412 -> -30,117 | n/a | n/a | 0 of 0 landed | NOT FINISHED (fewer than 10 valid controls in L6M/L3M) | NOT FINISHED |
| HALF SIZE M7 London (43 mo) | +5.5% / +234 | +1.9% / +245 | +3.0% / -194 | +0.9% / -139 | +4.9% / +220 | +2.3% / +120 | 0.98 / 0.98 / 0.94 | -30,189 -> -26,619 / -88,502 -> -90,541 | -15,066 -> -12,898 / -38,412 -> -38,573 | n/a | n/a | 0 of 60 landed | NOT FINISHED (fewer than 10 valid controls in L6M/L3M) | NOT FINISHED |
| HALF SIZE P7 London (43 mo) | +1.4% / -369 | -0.4% / -611 | +9.0% / +525 | +8.1% / +289 | +5.3% / +185 | +5.0% / +30 | 0.22 / 0.41 / 0.78 | -30,189 -> -28,512 / -88,502 -> -83,863 | -15,066 -> -14,566 / -38,412 -> -36,802 | n/a | n/a | 0 of 0 landed | NOT FINISHED (fewer than 10 valid controls in L6M/L3M) | NOT FINISHED |
| HALF SIZE P7 NY AM (43 mo) | +1.1% / -80 | +1.7% / -104 | -0.4% / +476 | +1.6% / +22 | -0.0% / -20 | +0.9% / +4 | 0.83 / 0.81 / 0.80 | -30,189 -> -29,263 / -88,502 -> -87,311 | -15,066 -> -15,066 / -38,412 -> -38,538 | n/a | n/a | 0 of 0 landed | NOT FINISHED (fewer than 10 valid controls in L6M/L3M) | NOT FINISHED |
| HALF SIZE K7 NY PM (43 mo) | +0.4% / -80 | +0.8% / -323 | -3.3% / -444 | -2.9% / -91 | -1.8% / -225 | -1.3% / -219 | 0.80 / 0.33 / 0.26 | -30,189 -> -30,189 / -88,502 -> -89,678 | -15,066 -> -15,066 / -38,412 -> -38,412 | n/a | n/a | 0 of 0 landed | NOT FINISHED (fewer than 10 valid controls in L6M/L3M) | NOT FINISHED |
| HALF SIZE K7 London (43 mo) | -6.8% / -17 | -1.9% / -495 | -5.0% / -660 | +1.7% / -282 | +5.6% / +161 | +1.6% / -117 | 0.36 / 0.35 / 0.46 | -30,189 -> -32,986 / -88,502 -> -86,850 | -15,066 -> -22,935 / -38,412 -> -37,455 | n/a | n/a | 0 of 0 landed | NOT FINISHED (fewer than 10 valid controls in L6M/L3M) | NOT FINISHED |
| HALF SIZE four weakest (M7 London + P7 NY AM + P7 London + K7 NY AM) (43 mo) | +7.4% / -450 | +6.6% / -106 | +11.7% / +695 | +9.9% / -56 | +6.8% / +380 | +7.4% / +114 | 0.75 / 1.00 / 0.97 | -30,189 -> -24,015 / -88,502 -> -84,591 | -15,066 -> -12,399 / -38,412 -> -35,262 | n/a | n/a | 0 of 0 landed | NOT FINISHED (fewer than 10 valid controls in L6M/L3M) | NOT FINISHED |

## Table 2 - JL2: ulcer change / mean change per window (engine base lots; ulcer + = lower than base)
Cell vs JL2 base, same engine, same months. ulcer cell = % change of RMS daily drawdown (+ better); d mean = $/wk base lots (x1.75 and $4.84 in Table 3). P(ulcer lower) week-clustered bootstrap 2,000. JL2: no controls built for this base (percentile on JL3 controls does not transfer): tier = NOT FINISHED, bootstrap only.

| cell | L6M | HOLD | GAP | PRE | X' | pooled | P(ulcer lower) L6M / HOLD / pooled | max DD base -> cell, L6M / pooled | worst week base -> cell, L6M / pooled | tier |
|--|--|--|--|--|--|--|--|--|--|--|
| DO NOT TRADE M7 London (43 mo) | +12.0% / +108 | -2.3% / -164 | +6.4% / +1,352 | +10.7% / +725 | -8.7% / +312 | +0.7% / +399 | 0.68 / 0.64 / 0.95 | -22,565 -> -20,902 / -74,402 -> -70,940 | -13,430 -> -13,357 / -43,527 -> -44,644 | NOT FINISHED (no JL2 controls) |
| DO NOT TRADE K7 NY AM (43 mo) | -13.7% / -576 | +1.9% / -150 | +4.3% / +1,190 | -8.8% / -558 | -7.2% / -609 | -5.4% / -445 | 0.05 / 0.75 / 0.42 | -22,565 -> -26,161 / -74,402 -> -72,158 | -13,430 -> -16,246 / -43,527 -> -39,060 | NOT FINISHED (no JL2 controls) |
| DO NOT TRADE P7 London (43 mo) | -13.5% / -2,841 | -11.1% / -1,064 | +11.1% / +807 | +40.1% / +2,142 | -0.5% / -404 | +7.6% / -245 | 0.01 / 0.17 / 0.56 | -22,565 -> -26,842 / -74,402 -> -75,909 | -13,430 -> -15,939 / -43,527 -> -48,992 | NOT FINISHED (no JL2 controls) |
| DO NOT TRADE P7 NY AM (43 mo) | +3.0% / -313 | +0.7% / -436 | -3.2% / -983 | +1.4% / +441 | -5.0% / -139 | -1.2% / -142 | 0.81 / 0.52 / 0.49 | -22,565 -> -22,565 / -74,402 -> -73,618 | -13,430 -> -12,805 / -43,527 -> -44,676 | NOT FINISHED (no JL2 controls) |
| DO NOT TRADE K7 NY PM (43 mo) | -1.8% / -1,419 | +5.0% / +542 | +3.7% / -1,058 | +14.3% / +148 | -8.4% / -526 | +2.7% / -451 | 0.35 / 0.53 / 0.61 | -22,565 -> -23,013 / -74,402 -> -70,843 | -13,430 -> -16,114 / -43,527 -> -41,927 | NOT FINISHED (no JL2 controls) |
| DO NOT TRADE K7 London (43 mo) | -4.4% / -1,439 | -0.6% / -606 | +1.3% / -1,472 | +7.8% / +400 | +9.4% / +329 | +6.1% / -232 | 0.34 / 0.27 / 0.54 | -22,565 -> -22,203 / -74,402 -> -61,748 | -13,430 -> -16,669 / -43,527 -> -38,768 | NOT FINISHED (no JL2 controls) |
| DO NOT TRADE four weakest (M7 London + P7 NY AM + P7 London + K7 NY AM) (43 mo) | -13.9% / -1,695 | -6.1% / -1,591 | +21.5% / +2,541 | +49.9% / +1,422 | -31.1% / -759 | -1.3% / -368 | 0.12 / 0.55 / 0.81 | -22,565 -> -30,405 / -74,402 -> -71,729 | -13,430 -> -21,054 / -43,527 -> -41,807 | NOT FINISHED (no JL2 controls) |
| HALF SIZE M7 London (43 mo) | +5.4% / +200 | +3.6% / +164 | -0.2% / +39 | +2.5% / -24 | -0.2% / +194 | +1.6% / +124 | 0.96 / 0.89 / 0.93 | -22,565 -> -21,950 / -74,402 -> -71,851 | -13,430 -> -12,002 / -43,527 -> -44,393 | NOT FINISHED (no JL2 controls) |
| HALF SIZE P7 London (43 mo) | +0.2% / -541 | +2.4% / -267 | +7.1% / +252 | +13.8% / +389 | +2.7% / -4 | +6.1% / -32 | 0.37 / 0.49 / 0.73 | -22,565 -> -21,889 / -74,402 -> -75,097 | -13,430 -> -14,478 / -43,527 -> -40,768 | NOT FINISHED (no JL2 controls) |
| HALF SIZE P7 NY AM (43 mo) | +1.4% / +142 | +0.7% / -228 | -1.3% / -81 | +0.0% / -9 | +0.0% / +1 | +0.1% / -19 | 0.59 / 0.82 / 0.50 | -22,565 -> -22,565 / -74,402 -> -73,732 | -13,430 -> -13,430 / -43,527 -> -44,074 | NOT FINISHED (no JL2 controls) |
| HALF SIZE K7 NY PM (43 mo) | +0.5% / -316 | +0.8% / -156 | -1.1% / -396 | -1.5% / -42 | -3.2% / -240 | -1.4% / -218 | 0.81 / 0.32 / 0.31 | -22,565 -> -22,508 / -74,402 -> -74,038 | -13,430 -> -13,430 / -43,527 -> -43,527 | NOT FINISHED (no JL2 controls) |
| HALF SIZE K7 London (43 mo) | +2.4% / +376 | +0.6% / -70 | +0.1% / -513 | +0.4% / -65 | +4.1% / +103 | +1.7% / +9 | 0.35 / 0.22 / 0.46 | -22,565 -> -22,565 / -74,402 -> -73,877 | -13,430 -> -14,940 / -43,527 -> -41,658 | NOT FINISHED (no JL2 controls) |
| HALF SIZE four weakest (M7 London + P7 NY AM + P7 London + K7 NY AM) (43 mo) | +5.7% / -381 | +8.2% / -84 | +5.6% / +264 | +17.7% / +410 | +1.4% / +157 | +7.9% / +83 | 0.95 / 0.96 / 0.96 | -22,565 -> -20,996 / -74,402 -> -74,190 | -13,430 -> -13,050 / -43,527 -> -42,180 | NOT FINISHED (no JL2 controls) |

## Table 3 - mean change $/wk at the three price/size columns (JL3 | JL2), L6M / HOLD / pooled
| cell | base lots $1.18 RT | $4.84 RT | x1.75 live lots $1.18 RT |
|--|--|--|--|
| DO NOT TRADE M7 London | +1,038/-445/+506  |  +108/-164/+399 | +1,093/-389/+549  |  +166/-107/+442 | +2,051/-961/+984  |  +229/-358/+772 |
| DO NOT TRADE K7 NY AM | +171/-515/-438  |  -576/-150/-445 | +190/-488/-416  |  -556/-127/-424 | +342/-1,030/-875  |  -1,151/-300/-891 |
| DO NOT TRADE P7 London | -1,883/-1,237/-16  |  -2,841/-1,064/-245 | -1,813/-1,191/+22  |  -2,777/-1,020/-212 | -3,674/-2,537/-41  |  -5,573/-2,043/-458 |
| DO NOT TRADE P7 NY AM | -395/-566/-94  |  -313/-436/-142 | -388/-561/-89  |  -306/-431/-137 | -747/-1,086/-176  |  -653/-779/-263 |
| DO NOT TRADE K7 NY PM | -860/-238/-472  |  -1,419/+542/-451 | -834/-210/-444  |  -1,393/+567/-423 | -1,720/-476/-944  |  -2,838/+1,084/-901 |
| DO NOT TRADE K7 London | -519/-1,778/-321  |  -1,439/-606/-232 | -474/-1,739/-294  |  -1,392/-575/-206 | -1,059/-3,605/-672  |  -2,900/-1,289/-483 |
| DO NOT TRADE four weakest (M7 London + P7 NY AM + P7 London + K7 NY AM) | -1,181/-2,090/-117  |  -1,695/-1,591/-368 | -1,020/-1,952/-3  |  -1,541/-1,458/-260 | -2,197/-4,194/-250  |  -3,345/-3,004/-711 |
| HALF SIZE M7 London | +234/+245/+120  |  +200/+164/+124 | +243/+254/+128  |  +209/+174/+131 | +501/+558/+264  |  +492/+398/+263 |
| HALF SIZE P7 London | -369/-611/+30  |  -541/-267/-32 | -351/-596/+39  |  -522/-254/-24 | -663/-1,278/+56  |  -1,008/-487/-50 |
| HALF SIZE P7 NY AM | -80/-104/+4  |  +142/-228/-19 | -79/-103/+4  |  +144/-227/-18 | -118/-162/+8  |  +259/-363/-28 |
| HALF SIZE K7 NY PM | -80/-323/-219  |  -316/-156/-218 | -78/-321/-217  |  -314/-154/-215 | -160/-645/-439  |  -632/-311/-436 |
| HALF SIZE K7 London | -17/-495/-117  |  +376/-70/+9 | -13/-492/-115  |  +380/-71/+10 | -8/-971/-226  |  +800/-122/+23 |
| HALF SIZE four weakest (M7 London + P7 NY AM + P7 London + K7 NY AM) | -450/-106/+114  |  -381/-84/+83 | -423/-81/+131  |  -351/-62/+99 | -783/-177/+235  |  -669/+16/+201 |

## Table 4 - FREED-BOOK effects on JL3 (what the other books do with the freed stack room): trades lost / gained per book and $ (base lots), cell vs JL3, window shown
For do-not-trade cells the cell's own trades are "lost" by design (own book); lost / gained on OTHER books and the $ change on trades both runs share (path effect) are the freed-room effect. Format: n lost ($) / n gained ($) / common-trade change $ (n changed).

Window L6M
| cell | K7 | M7 | U7 | P7 | H7 | A7 | O7 | total lost / gained / common $ |
|--|--|--|--|--|--|--|--|--|
| DO NOT TRADE M7 London | 6 (-2,344) / 81 (+14,583) / +997 (5) | 522 (-2,117) / 40 (+5,679) / -200 (1) | 1 (-1,254) / 12 (+3,258) / +2,005 (3) | 3 (-2,540) / 33 (-2,286) / -1,718 (10) | 0 (+0) / 7 (-950) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 7 (-2,338) / +0 (0) | -8,255 / +17,947 / +1,084 |
| DO NOT TRADE K7 NY AM | 222 (-4,126) / 64 (+476) / +879 (3) | 1 (-700) / 9 (+514) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 3 (-3,138) / +0 (0) | 0 (+0) / 1 (+939) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | -4,826 / -1,209 / +879 |
| DO NOT TRADE P7 London | 37 (+2,090) / 35 (-183) / +803 (7) | 18 (+4,046) / 34 (-3,924) / -605 (1) | 1 (+1,199) / 8 (-9,009) / +3,209 (3) | 401 (+29,076) / 3 (-773) / -1,152 (5) | 2 (+2,098) / 1 (-1,171) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 2 (-1,558) / 3 (+263) / +0 (0) | +36,950 / -14,797 / +2,255 |
| DO NOT TRADE P7 NY AM | 3 (+1,488) / 3 (-1,618) / +0 (0) | 0 (+0) / 2 (+172) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 45 (+6,215) / 1 (-1,224) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | +7,703 / -2,671 / +0 |
| DO NOT TRADE K7 NY PM | 170 (+23,808) / 1 (+1,199) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | +23,808 / +1,199 / +0 |
| DO NOT TRADE K7 London | 478 (-1,070) / 103 (+1,850) / +1,929 (7) | 10 (+2,512) / 40 (-6,814) / +0 (0) | 1 (-2,452) / 7 (-6,903) / +3,209 (3) | 1 (+1,109) / 17 (-1,360) / -2,745 (7) | 0 (+0) / 2 (-1,761) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 5 (-946) / +0 (0) | +99 / -15,935 / +2,393 |
| DO NOT TRADE four weakest (M7 London + P7 NY AM + P7 London + K7 NY AM) | 229 (-12,140) / 126 (-8,676) / +1,319 (9) | 523 (-933) / 70 (+3,442) / -200 (1) | 0 (+0) / 16 (-8,522) / +4,408 (3) | 445 (+35,964) / 1 (-1,224) / -1,152 (5) | 0 (+0) / 9 (+2,831) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 1 (-786) / 9 (-1,171) / +0 (0) | +22,104 / -13,320 / +4,375 |
| HALF SIZE M7 London | 4 (+1,462) / 3 (+548) / -141 (2) | 3 (+4,630) / 12 (-1,155) / +13,003 (88) | 0 (+0) / 2 (-2,582) / +727 (1) | 1 (-2,699) / 3 (+1,889) / -919 (6) | 1 (+1,199) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 1 (-637) / +0 (0) | +4,592 / -1,937 / +12,670 |
| HALF SIZE P7 London | 14 (-702) / 3 (+548) / +2,432 (5) | 8 (+3,259) / 2 (+269) / -605 (1) | 0 (+0) / 2 (+1,176) / +817 (2) | 8 (+279) / 9 (-2,201) / -9,967 (100) | 1 (+899) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 2 (-1,558) / 0 (+0) / +0 (0) | +2,176 / -207 / -7,323 |
| HALF SIZE P7 NY AM | 0 (+0) / 1 (-887) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / -1,227 (9) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | +0 / -887 / -1,227 |
| HALF SIZE K7 NY PM | 1 (+1,199) / 1 (+1,199) / -2,101 (17) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | +1,199 / +1,199 / -2,101 |
| HALF SIZE K7 London | 14 (+8,719) / 22 (+5,852) / +4,095 (43) | 6 (-2,442) / 4 (-1,315) / +0 (0) | 1 (-2,452) / 1 (-1,191) / -622 (3) | 1 (+1,199) / 2 (-1,402) / -831 (3) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | +5,023 / +1,944 / +2,642 |
| HALF SIZE four weakest (M7 London + P7 NY AM + P7 London + K7 NY AM) | 13 (+295) / 6 (+24) / +1,490 (6) | 10 (+6,775) / 15 (-1,592) / +13,003 (88) | 0 (+0) / 4 (-4,128) / +817 (2) | 9 (-2,419) / 14 (-3,497) / -12,403 (108) | 1 (+899) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | +5,550 / -9,194 / +2,906 |

Window HOLD
| cell | K7 | M7 | U7 | P7 | H7 | A7 | O7 | total lost / gained / common $ |
|--|--|--|--|--|--|--|--|--|
| DO NOT TRADE M7 London | 18 (+1,471) / 63 (-15,788) / -796 (3) | 454 (-9,112) / 37 (-6,537) / -223 (1) | 0 (+0) / 7 (+12,128) / -3,110 (2) | 3 (+7,297) / 27 (+3,151) / -1,422 (5) | 1 (-1,181) / 1 (+934) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 6 (-1,356) / +0 (0) | -1,525 / -7,468 / -5,551 |
| DO NOT TRADE K7 NY AM | 267 (-20,806) / 64 (-26,487) / -5,307 (5) | 0 (+0) / 8 (-2,324) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | -20,806 / -28,812 / -5,307 |
| DO NOT TRADE P7 London | 22 (-2,564) / 42 (-9,966) / -2,131 (4) | 4 (-3,391) / 39 (-6,756) / -146 (3) | 0 (+0) / 4 (+9,566) / -1,201 (1) | 301 (+24,176) / 2 (-1,344) / -1,890 (7) | 0 (+0) / 1 (+934) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 5 (-839) / +0 (0) | +18,222 / -8,405 / -5,367 |
| DO NOT TRADE P7 NY AM | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 27 (+14,637) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | +14,637 / +0 / +0 |
| DO NOT TRADE K7 NY PM | 178 (+7,273) / 1 (+1,114) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | +7,273 / +1,114 / +0 |
| DO NOT TRADE K7 London | 393 (+32,289) / 74 (-9,135) / -1,538 (14) | 6 (+1,350) / 44 (-8,999) / -667 (1) | 1 (+2,398) / 4 (+3,761) / -1,893 (2) | 4 (+1,011) / 22 (+6,614) / +2,375 (5) | 1 (+894) / 1 (+934) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 3 (+512) / +0 (0) | +37,941 / -6,313 / -1,724 |
| DO NOT TRADE four weakest (M7 London + P7 NY AM + P7 London + K7 NY AM) | 276 (-19,480) / 146 (-33,816) / -5,007 (8) | 451 (-6,896) / 72 (-11,988) / -223 (1) | 0 (+0) / 9 (+15,719) / -3,110 (2) | 328 (+38,813) / 0 (+0) / -1,890 (7) | 0 (+0) / 7 (-210) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 9 (-1,070) / +0 (0) | +12,437 / -31,364 / -10,230 |
| HALF SIZE M7 London | 6 (-926) / 2 (-1,864) / +0 (0) | 0 (+0) / 15 (-3,598) / +15,311 (84) | 0 (+0) / 0 (+0) / -1,893 (2) | 1 (+1,094) / 3 (-233) / -1,227 (2) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | +168 / -5,695 / +12,191 |
| HALF SIZE P7 London | 15 (+1,838) / 4 (-1,648) / +297 (2) | 7 (-2,538) / 2 (-2,011) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 5 (+700) / 4 (+1,118) / -13,544 (85) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | -0 / -2,540 / -13,247 |
| HALF SIZE P7 NY AM | 0 (+0) / 0 (+0) / +0 (0) | 1 (-717) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / -3,406 (5) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | -717 / +0 / -3,406 |
| HALF SIZE K7 NY PM | 0 (+0) / 4 (+818) / -9,163 (21) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | +0 / +818 / -9,163 |
| HALF SIZE K7 London | 7 (-133) / 23 (+1,037) / -13,065 (44) | 0 (+0) / 2 (-1,392) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 1 (+1,119) / -622 (1) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | -133 / +764 / -13,687 |
| HALF SIZE four weakest (M7 London + P7 NY AM + P7 London + K7 NY AM) | 20 (-5,573) / 5 (-2,587) / +297 (2) | 8 (-3,255) / 16 (-4,839) / +15,311 (84) | 0 (+0) / 0 (+0) / -1,893 (2) | 6 (+1,794) / 7 (+885) / -16,950 (90) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | -7,034 / -6,541 / -3,235 |

Window pooled
| cell | K7 | M7 | U7 | P7 | H7 | A7 | O7 | total lost / gained / common $ |
|--|--|--|--|--|--|--|--|--|
| DO NOT TRADE M7 London | 71 (-2,337) / 305 (+11,907) / -1,943 (19) | 2495 (-52,356) / 235 (+2,929) / -1,103 (4) | 1 (-1,254) / 24 (+19,362) / +5,673 (21) | 34 (-2,249) / 114 (+7,698) / -5,772 (45) | 1 (-1,181) / 23 (-1,358) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 22 (-2,163) / +0 (0) | -59,378 / +38,376 / -3,145 |
| DO NOT TRADE K7 NY AM | 1889 (+23,320) / 682 (-46,988) / -4,192 (21) | 2 (-1,544) / 28 (-6,630) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 4 (-3,793) / +0 (0) | 0 (+0) / 5 (+1,480) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | +21,775 / -55,931 / -4,192 |
| DO NOT TRADE P7 London | 96 (+5,934) / 203 (+316) / -2,719 (18) | 40 (-1,833) / 131 (-15,047) / -2,640 (9) | 1 (+1,199) / 15 (+7,840) / +17,356 (16) | 1693 (-1,296) / 26 (+941) / -6,439 (38) | 2 (+2,098) / 11 (+1,469) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 2 (-1,558) / 14 (+526) / +0 (0) | +4,543 / -3,954 / +5,558 |
| DO NOT TRADE P7 NY AM | 3 (+1,488) / 12 (+1,117) / +193 (1) | 0 (+0) / 2 (+172) / +0 (0) | 0 (+0) / 0 (+0) / +940 (1) | 252 (+18,146) / 4 (-315) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | +19,634 / +974 / +1,133 |
| DO NOT TRADE K7 NY PM | 1286 (+90,083) / 4 (+2,494) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / -732 (1) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | +90,083 / +2,494 / -732 |
| DO NOT TRADE K7 London | 1952 (+79,712) / 458 (+18,107) / -4,646 (50) | 33 (+546) / 151 (-18,334) / -1,980 (8) | 2 (-55) / 16 (+622) / +12,835 (19) | 15 (+1,350) / 63 (+19,630) / -4,319 (29) | 1 (+894) / 9 (-1,481) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 1 (-781) / 17 (+1,096) / +0 (0) | +81,665 / +19,640 / +1,890 |
| DO NOT TRADE four weakest (M7 London + P7 NY AM + P7 London + K7 NY AM) | 1956 (+17,731) / 994 (-70,312) / -3,498 (46) | 2496 (-49,277) / 329 (-1,365) / -1,103 (4) | 0 (+0) / 31 (+15,963) / +13,822 (24) | 1940 (+20,384) / 7 (+16,762) / -6,439 (38) | 0 (+0) / 39 (+3,114) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 1 (-786) / 31 (-873) / +0 (0) | -11,948 / -36,710 / +2,781 |
| HALF SIZE M7 London | 36 (+6,263) / 25 (-481) / +1,285 (5) | 15 (+11,976) / 67 (+4,565) / +34,009 (471) | 0 (+0) / 3 (-180) / -2,242 (6) | 6 (-3,360) / 23 (+4,796) / -2,495 (16) | 1 (+1,199) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 1 (+1,799) / 2 (+1,162) / +0 (0) | +17,877 / +9,862 / +30,557 |
| HALF SIZE P7 London | 34 (+491) / 22 (-4,015) / +3,788 (10) | 20 (-1,689) / 11 (-3,787) / -1,772 (5) | 0 (+0) / 4 (+4,778) / +8,888 (6) | 29 (-12,038) / 34 (-5,607) / -10,592 (408) | 1 (+899) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 2 (-1,558) / 0 (+0) / +0 (0) | -13,897 / -8,631 / +311 |
| HALF SIZE P7 NY AM | 0 (+0) / 1 (-887) / +0 (0) | 4 (-2,344) / 2 (+348) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 1 (+1,109) / 1 (+8,387) / -8,330 (26) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | -1,235 / +7,847 / -8,330 |
| HALF SIZE K7 NY PM | 8 (-3,800) / 28 (-3,427) / -41,449 (177) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | -3,800 / -3,427 / -41,449 |
| HALF SIZE K7 London | 37 (+8,685) / 84 (+8,247) / -20,694 (200) | 10 (-4,525) / 12 (-2,856) / -1,609 (2) | 1 (-2,452) / 1 (-1,191) / -1,870 (5) | 1 (+1,199) / 6 (+2,768) / -1,801 (10) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | +2,906 / +6,968 / -25,975 |
| HALF SIZE four weakest (M7 London + P7 NY AM + P7 London + K7 NY AM) | 70 (+4,707) / 46 (-4,644) / +4,272 (14) | 39 (+8,028) / 80 (+1,971) / +32,420 (469) | 0 (+0) / 6 (-527) / +4,719 (10) | 37 (-13,181) / 60 (+5,097) / -20,308 (434) | 2 (+2,098) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 1 (+1,799) / 1 (+1,799) / +0 (0) | +3,450 / +3,696 / +21,104 |

## Table 5 - trade counts per window (cell vs JL3 base) and week-clustered bootstrap detail (JL3, pooled and L6M)
| cell | L6M (cell / base) | HOLD (cell / base) | GAP (cell / base) | PRE (cell / base) | X' (cell / base) | pooled (cell / base) | mean-change 90% interval L6M | pooled |
|--|--|--|--|--|--|--|--|--|
| DO NOT TRADE M7 London | 3940 / 4292 | 2976 / 3311 | 1011 / 1138 | 3912 / 4315 | 5388 / 5992 | 17673 / 19552 | -1,090..+2,960 | -63..+1,107 |
| DO NOT TRADE K7 NY AM | 4146 / 4292 | 3116 / 3311 | 1054 / 1138 | 4055 / 4315 | 5529 / 5992 | 18380 / 19552 | -637..+964 | -845..+8 |
| DO NOT TRADE P7 London | 3915 / 4292 | 3077 / 3311 | 1055 / 1138 | 4021 / 4315 | 5581 / 5992 | 18118 / 19552 | -3,293..-343 | -508..+491 |
| DO NOT TRADE P7 NY AM | 4250 / 4292 | 3284 / 3311 | 1122 / 1138 | 4252 / 4315 | 5905 / 5992 | 19315 / 19552 | -931..+124 | -269..+82 |
| DO NOT TRADE K7 NY PM | 4123 / 4292 | 3134 / 3311 | 1061 / 1138 | 3999 / 4315 | 5489 / 5992 | 18270 / 19552 | -1,652..-33 | -851..-90 |
| DO NOT TRADE K7 London | 3976 / 4292 | 3054 / 3311 | 1076 / 1138 | 4008 / 4315 | 5686 / 5992 | 18262 / 19552 | -1,964..+865 | -826..+177 |
| DO NOT TRADE four weakest (M7 London + P7 NY AM + P7 London + K7 NY AM) | 3325 / 4292 | 2499 / 3311 | 805 / 1138 | 3172 / 4315 | 4407 / 5992 | 14590 / 19552 | -4,044..+1,641 | -1,040..+837 |
| HALF SIZE M7 London | 4304 / 4292 | 3324 / 3311 | 1139 / 1138 | 4329 / 4315 | 6002 / 5992 | 19613 / 19552 | -349..+779 | -101..+340 |
| HALF SIZE P7 London | 4275 / 4292 | 3294 / 3311 | 1141 / 1138 | 4323 / 4315 | 6000 / 5992 | 19537 / 19552 | -1,492..+518 | -208..+253 |
| HALF SIZE P7 NY AM | 4293 / 4292 | 3310 / 3311 | 1137 / 1138 | 4315 / 4315 | 5992 / 5992 | 19551 / 19552 | -261..+86 | -71..+91 |
| HALF SIZE K7 NY PM | 4292 / 4292 | 3315 / 3311 | 1138 / 1138 | 4321 / 4315 | 6002 / 5992 | 19572 / 19552 | -334..+182 | -343..-94 |
| HALF SIZE K7 London | 4299 / 4292 | 3330 / 3311 | 1143 / 1138 | 4332 / 4315 | 5998 / 5992 | 19606 / 19552 | -881..+883 | -341..+105 |
| HALF SIZE four weakest (M7 London + P7 NY AM + P7 London + K7 NY AM) | 4298 / 4292 | 3305 / 3311 | 1141 / 1138 | 4327 / 4315 | 6010 / 5992 | 19596 / 19552 | -1,911..+788 | -261..+463 |

## Table 6 - W44-removed variant (JL3; week 2026-10-26..11-01 removed): ulcer change / mean change
| cell | L3M | L6M | pooled | tier W44 |
|--|--|--|--|--|
| DO NOT TRADE M7 London | +11.3% / +484 | +13.5% / +1,106 | +11.7% / +512 | CONFIRMED |
| DO NOT TRADE K7 NY AM | -22.9% / +338 | -16.4% / +313 | -4.3% / -421 | NOT FINISHED |
| DO NOT TRADE P7 London | -1.1% / -1,006 | -2.9% / -1,728 | +15.7% / +14 | NOT FINISHED |
| DO NOT TRADE P7 NY AM | +5.2% / -705 | +3.2% / -408 | +0.8% / -94 | NOT FINISHED |
| DO NOT TRADE K7 NY PM | -4.8% / -508 | -3.8% / -997 | -0.3% / -489 | NOT FINISHED |
| DO NOT TRADE K7 London | -4.7% / -1,322 | -4.3% / -612 | +6.9% / -333 | NOT FINISHED |
| DO NOT TRADE four weakest (M7 London + P7 NY AM + P7 London + K7 NY AM) | -14.4% / -1,876 | -8.2% / -790 | +19.6% / -59 | NOT FINISHED |
| HALF SIZE M7 London | +10.1% / +231 | +6.5% / +242 | +2.3% / +121 | NOT FINISHED |
| HALF SIZE P7 London | +3.7% / +67 | +1.3% / -369 | +5.0% / +32 | NOT FINISHED |
| HALF SIZE P7 NY AM | +1.9% / -283 | +1.3% / -83 | +0.9% / +4 | NOT FINISHED |
| HALF SIZE K7 NY PM | -0.2% / -367 | -0.2% / -118 | -1.3% / -225 | NOT FINISHED |
| HALF SIZE K7 London | -12.1% / -420 | -7.9% / -17 | +1.6% / -118 | NOT FINISHED |
| HALF SIZE four weakest (M7 London + P7 NY AM + P7 London + K7 NY AM) | +13.9% / -324 | +8.3% / -453 | +7.4% / +116 | NOT FINISHED |

## Table 7 - controls: draws landed / valid, realised vs cell share (JL3)
| control set | landed | valid | per-draw (book, cell share, realised, tol) of the first 3 draws |
|--|--|--|--|
| DO NOT TRADE M7 London | 60 | 19 | [('M7', 0.684, 0.582, 0.05)]; None; [('M7', 0.683, 0.612, 0.05)] |
| DO NOT TRADE K7 NY AM | 30 | 0 | None; None; None |
| DO NOT TRADE P7 London | 30 | 0 | None; None; None |
| DO NOT TRADE P7 NY AM | 30 | 0 | None; None; None |
| DO NOT TRADE K7 NY PM | 30 | 0 | None; None; None |
| DO NOT TRADE K7 London | 30 | 0 | None; None; None |
| DO NOT TRADE four weakest (M7 London + P7 NY AM + P7 London + K7 NY AM) | 30 | 0 | None; None; None |
| HALF SIZE M7 London | 60 | 0 | [('M7', 0.5, 0.899, 0.05)]; [('M7', 0.5, 0.917, 0.05)]; [('M7', 0.5, 0.908, 0.05)] |
| HALF SIZE P7 London | 30 | 0 | None; None; None |
| HALF SIZE P7 NY AM | 30 | 0 | None; None; None |
| HALF SIZE K7 NY PM | 30 | 0 | None; None; None |
| HALF SIZE K7 London | 30 | 0 | None; None; None |
| HALF SIZE four weakest (M7 London + P7 NY AM + P7 London + K7 NY AM) | 30 | 0 | None; None; None |

## Notes
- Everything is FIRST PASS, in-sample over the 43 months; a window is shown only when every month of it landed for the cell and for the base. "n/l" = not landed. Missing = not finished.
- JL2 does not carry the live persist=1 take/lock lines (JL3 does); both are shown, tiers only on JL3.
- Raw-base context: DS3_REBUILD_S1.md raw table (mean R per trade by book x session). Stack effects (cap 6 lots, freed room) can make a raw-base weak cell still pay in the stack; this page is the engine answer.
