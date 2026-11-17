# DS3_CELL_TESTS - engine cell tests: do not trade / half size weak book x session cells on JL3 and JL2 (W-CELL, order 11-17 07:28Z JOB 2)
VERDICT (data ends 2026-10-31; FIRST PASS; see below)

> VALIDATION (desk standard, W-CELL, FIRST PASS, 2026-11-17 09:10Z): trials counted = 26 real engine cells (13 cell definitions x JL3 and JL2: 6 do-not-trade singles + the four weakest together + 5 half-size singles + the four weakest half-sized; K7 NY AM is 1 lot so not halvable), each reported, no best-of selection (ledger family CT1); correction = percentile among 30 persistent-draw engine controls per cell (JL3 only; valid draws only) + week-clustered bootstrap (2,000) + the calibrated ulcer-primary tiers of DS3_PASS_RULE (cutoffs_ulc TUNED); no family-wide White/SPA because no cell is selected as best; PBO not applicable (no fitted choice); numbers shown: IN-SAMPLE (every window is part of the 43 months; the cells are fixed by the stage-0/1 raw table, not fitted per window; walk-forward not applicable). Data ends 2026-10-31.

## Status (what has landed)
- Base months landed: JL3 14 of 43, JL2 43 of 43. Real cells with at least one scored window: 26 of 26; with all 43 months: 0.
- Controls (JL3 + persistent random skip): N M7 London 0 landed / 0 valid; N K7 NY AM 0 landed / 0 valid; N P7 London 0 landed / 0 valid; N P7 NY AM 0 landed / 0 valid; N K7 NY PM 0 landed / 0 valid; N K7 London 0 landed / 0 valid; N four weakest (M7 Lon 0 landed / 0 valid; H M7 London 0 landed / 0 valid; H P7 London 0 landed / 0 valid; H P7 NY AM 0 landed / 0 valid; H K7 NY PM 0 landed / 0 valid; H K7 London 0 landed / 0 valid; H four weakest (M7 Lon 0 landed / 0 valid. A cell with fewer than 10 valid controls in a window is NOT FINISHED, never passing.
- Mechanism: ev_panel hook (outermost) overrides the book session lot table: do-not-trade = lots 0 in that session (engine entry gate, same as M7 asia = 0 today), half = lots/2 rounded half up (K7 2->1, M7 2->1, P7 4->2). Everything else (stack cap, locks, cuts, sizer, day caps, freed stack room, re-entries) runs unchanged = engine test, not path arithmetic. Identity cells TL3_CT_JL3_ID / TL3_CT_JL2_ID: TL3_CT_JL3_ID 202609: 647 trades net 85599.32 vs TL3_EV_JL3 647 net 85599.32 -> IDENTICAL; TL3_CT_JL3_ID 202610: 691 trades net 37159.82 vs TL3_EV_JL3 691 net 37159.82 -> IDENTICAL; TL3_CT_JL2_ID 202609: 645 trades net 113229.66 vs TL3_EV_JN05W2JL2 645 net 113229.66 -> IDENTICAL; TL3_CT_JL2_ID 202610: 642 trades net 27487.58 vs TL3_EV_JN05W2JL2 642 net 27487.58 -> IDENTICAL.
- Four weakest chosen by the raw-base table (DS3_REBUILD_S1 / S0: one book alone, no layers): lowest mean R per trade: M7 London -0.009 (net -$48k), P7 NY AM 0.006, P7 London 0.008, K7 NY AM 0.008 (net $18k over 43 months); next K7 NY PM 0.015, K7 London 0.024. Stage 5 has no session-lot leave-one-out, so the raw base decides.
- Controls: book-wide persistent random skip (one uniform per 5-minute bucket, book, side; same seed set across cells), p calibrated by pilots so the realised share of the book removed matches the cell share within max(min(0.05, 0.25 x share), 0.002) (stricter than 0.05 for small shares); draw valid if pooled over its landed months it is within that tolerance. Half-size stand-in controls: 50% persistent skip inside the cell session, L6M + HOLD months only (so half-size tiers cannot reach older windows: shown as PROVISIONAL/NOT FINISHED).

## Table 1 - JL3: ulcer change / mean change per window (engine base lots; ulcer + = lower than base)
Cell vs JL3 base, same engine, same months. ulcer cell = % change of RMS daily drawdown (+ better); d mean = $/wk base lots (x1.75 and $4.84 in Table 3). P(ulcer lower) week-clustered bootstrap 2,000. Percentile (pct) = share of valid controls the real cell beats on ulcer / mean / max DD (L6M and HOLD). Tier from calibrated tiers; W44 = week 2026-10-26..11-01 removed.

| cell | L6M | HOLD | GAP | PRE | X' | pooled | P(ulcer lower) L6M / HOLD / pooled | max DD base -> cell, L6M / pooled | worst week base -> cell, L6M / pooled | pct ulcer / mean / DD, L6M | pct, HOLD | valid controls L6M | tier | tier W44 |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| DO NOT TRADE M7 London (13 mo) | +15.0% / +1,038 | n/l | n/l | n/l | n/l | n/l | 0.83 / n/l / n/l | -30,189 -> -23,870 / n/l | -15,066 -> -14,160 / n/l | n/a | n/a | 0 of 0 landed | NOT FINISHED (fewer than 10 valid controls in L6M/L3M) | NOT FINISHED |
| DO NOT TRADE K7 NY AM (14 mo) | -16.1% / +171 | n/l | n/l | n/l | n/l | n/l | 0.01 / n/l / n/l | -30,189 -> -37,671 / n/l | -15,066 -> -19,093 / n/l | n/a | n/a | 0 of 0 landed | NOT FINISHED (fewer than 10 valid controls in L6M/L3M) | NOT FINISHED |
| DO NOT TRADE P7 London (14 mo) | -2.0% / -1,883 | n/l | n/l | n/l | n/l | n/l | 0.20 / n/l / n/l | -30,189 -> -31,637 / n/l | -15,066 -> -17,426 / n/l | n/a | n/a | 0 of 0 landed | NOT FINISHED (fewer than 10 valid controls in L6M/L3M) | NOT FINISHED |
| DO NOT TRADE P7 NY AM (13 mo) | +2.7% / -395 | +0.4% / -566 | n/l | n/l | n/l | n/l | 0.93 / 0.47 / n/l | -30,189 -> -28,337 / n/l | -15,066 -> -14,441 / n/l | n/a | n/a | 0 of 0 landed | NOT FINISHED (fewer than 10 valid controls in L6M/L3M) | NOT FINISHED |
| DO NOT TRADE K7 NY PM (13 mo) | -1.9% / -860 | n/l | n/l | n/l | n/l | n/l | 0.33 / n/l / n/l | -30,189 -> -31,822 / n/l | -15,066 -> -17,515 / n/l | n/a | n/a | 0 of 0 landed | NOT FINISHED (fewer than 10 valid controls in L6M/L3M) | NOT FINISHED |
| DO NOT TRADE K7 London (14 mo) | n/l | -0.0% / -1,778 | n/l | n/l | n/l | n/l | n/l / 0.14 / n/l | n/l / n/l | n/l / n/l | n/a | n/a | 0 | NOT FINISHED (fewer than 10 valid controls in L6M/L3M) | NOT FINISHED |
| DO NOT TRADE four weakest (M7 London + P7 NY AM + P7 London + K7 NY AM) (15 mo) | -10.9% / -1,181 | +9.6% / -2,090 | n/l | n/l | n/l | n/l | 0.14 / 0.63 / n/l | -30,189 -> -32,384 / n/l | -15,066 -> -22,847 / n/l | n/a | n/a | 0 of 0 landed | NOT FINISHED (fewer than 10 valid controls in L6M/L3M) | NOT FINISHED |
| HALF SIZE M7 London (14 mo) | +5.5% / +234 | +1.9% / +245 | n/l | n/l | n/l | n/l | 0.98 / 0.98 / n/l | -30,189 -> -26,619 / n/l | -15,066 -> -12,898 / n/l | n/a | n/a | 0 of 0 landed | NOT FINISHED (fewer than 10 valid controls in L6M/L3M) | NOT FINISHED |
| HALF SIZE P7 London (13 mo) | n/l | -0.4% / -611 | n/l | n/l | n/l | n/l | n/l / 0.41 / n/l | n/l / n/l | n/l / n/l | n/a | n/a | 0 | NOT FINISHED (fewer than 10 valid controls in L6M/L3M) | NOT FINISHED |
| HALF SIZE P7 NY AM (14 mo) | +1.1% / -80 | +1.7% / -104 | n/l | n/l | n/l | n/l | 0.83 / 0.81 / n/l | -30,189 -> -29,263 / n/l | -15,066 -> -15,066 / n/l | n/a | n/a | 0 of 0 landed | NOT FINISHED (fewer than 10 valid controls in L6M/L3M) | NOT FINISHED |
| HALF SIZE K7 NY PM (13 mo) | n/l | +0.8% / -323 | n/l | n/l | n/l | n/l | n/l / 0.33 / n/l | n/l / n/l | n/l / n/l | n/a | n/a | 0 | NOT FINISHED (fewer than 10 valid controls in L6M/L3M) | NOT FINISHED |
| HALF SIZE K7 London (14 mo) | -6.8% / -17 | -1.9% / -495 | n/l | n/l | n/l | n/l | 0.36 / 0.35 / n/l | -30,189 -> -32,986 / n/l | -15,066 -> -22,935 / n/l | n/a | n/a | 0 of 0 landed | NOT FINISHED (fewer than 10 valid controls in L6M/L3M) | NOT FINISHED |
| HALF SIZE four weakest (M7 London + P7 NY AM + P7 London + K7 NY AM) (14 mo) | +7.4% / -450 | +6.6% / -106 | n/l | n/l | n/l | n/l | 0.75 / 1.00 / n/l | -30,189 -> -24,015 / n/l | -15,066 -> -12,399 / n/l | n/a | n/a | 0 of 0 landed | NOT FINISHED (fewer than 10 valid controls in L6M/L3M) | NOT FINISHED |

## Table 2 - JL2: ulcer change / mean change per window (engine base lots; ulcer + = lower than base)
Cell vs JL2 base, same engine, same months. ulcer cell = % change of RMS daily drawdown (+ better); d mean = $/wk base lots (x1.75 and $4.84 in Table 3). P(ulcer lower) week-clustered bootstrap 2,000. JL2: no controls built for this base (percentile on JL3 controls does not transfer): tier = NOT FINISHED, bootstrap only.

| cell | L6M | HOLD | GAP | PRE | X' | pooled | P(ulcer lower) L6M / HOLD / pooled | max DD base -> cell, L6M / pooled | worst week base -> cell, L6M / pooled | tier |
|--|--|--|--|--|--|--|--|--|--|--|
| DO NOT TRADE M7 London (13 mo) | +12.0% / +108 | n/l | n/l | n/l | n/l | n/l | 0.68 / n/l / n/l | -22,565 -> -20,902 / n/l | -13,430 -> -13,357 / n/l | NOT FINISHED (no JL2 controls) |
| DO NOT TRADE K7 NY AM (11 mo) | -13.7% / -576 | n/l | n/l | n/l | n/l | n/l | 0.05 / n/l / n/l | -22,565 -> -26,161 / n/l | -13,430 -> -16,246 / n/l | NOT FINISHED (no JL2 controls) |
| DO NOT TRADE P7 London (8 mo) | -13.5% / -2,841 | n/l | n/l | n/l | n/l | n/l | 0.01 / n/l / n/l | -22,565 -> -26,842 / n/l | -13,430 -> -15,939 / n/l | NOT FINISHED (no JL2 controls) |
| DO NOT TRADE P7 NY AM (5 mo) | n/l | n/l | n/l | n/l | n/l | n/l | n/l / n/l / n/l | n/l / n/l | n/l / n/l | NOT FINISHED (no JL2 controls) |
| DO NOT TRADE K7 NY PM (15 mo) | -1.8% / -1,419 | +5.0% / +542 | n/l | n/l | n/l | n/l | 0.35 / 0.53 / n/l | -22,565 -> -23,013 / n/l | -13,430 -> -16,114 / n/l | NOT FINISHED (no JL2 controls) |
| DO NOT TRADE K7 London (13 mo) | n/l | -0.6% / -606 | n/l | n/l | n/l | n/l | n/l / 0.27 / n/l | n/l / n/l | n/l / n/l | NOT FINISHED (no JL2 controls) |
| DO NOT TRADE four weakest (M7 London + P7 NY AM + P7 London + K7 NY AM) (14 mo) | n/l | -6.1% / -1,591 | n/l | n/l | n/l | n/l | n/l / 0.55 / n/l | n/l / n/l | n/l / n/l | NOT FINISHED (no JL2 controls) |
| HALF SIZE M7 London (13 mo) | +5.4% / +200 | +3.6% / +164 | n/l | n/l | n/l | n/l | 0.96 / 0.89 / n/l | -22,565 -> -21,950 / n/l | -13,430 -> -12,002 / n/l | NOT FINISHED (no JL2 controls) |
| HALF SIZE P7 London (14 mo) | +0.2% / -541 | +2.4% / -267 | n/l | n/l | n/l | n/l | 0.37 / 0.49 / n/l | -22,565 -> -21,889 / n/l | -13,430 -> -14,478 / n/l | NOT FINISHED (no JL2 controls) |
| HALF SIZE P7 NY AM (5 mo) | n/l | n/l | n/l | n/l | n/l | n/l | n/l / n/l / n/l | n/l / n/l | n/l / n/l | NOT FINISHED (no JL2 controls) |
| HALF SIZE K7 NY PM (13 mo) | +0.5% / -316 | n/l | n/l | n/l | n/l | n/l | 0.81 / n/l / n/l | -22,565 -> -22,508 / n/l | -13,430 -> -13,430 / n/l | NOT FINISHED (no JL2 controls) |
| HALF SIZE K7 London (14 mo) | +2.4% / +376 | +0.6% / -70 | n/l | n/l | n/l | n/l | 0.35 / 0.22 / n/l | -22,565 -> -22,565 / n/l | -13,430 -> -14,940 / n/l | NOT FINISHED (no JL2 controls) |
| HALF SIZE four weakest (M7 London + P7 NY AM + P7 London + K7 NY AM) (13 mo) | n/l | +8.2% / -84 | n/l | n/l | n/l | n/l | n/l / 0.96 / n/l | n/l / n/l | n/l / n/l | NOT FINISHED (no JL2 controls) |

## Table 3 - mean change $/wk at the three price/size columns (JL3 | JL2), L6M / HOLD / pooled
| cell | base lots $1.18 RT | $4.84 RT | x1.75 live lots $1.18 RT |
|--|--|--|--|
| DO NOT TRADE M7 London | +1,038/n/l/n/l  |  +108/n/l/n/l | +1,093/n/l/n/l  |  +166/n/l/n/l | +2,051/n/l/n/l  |  +229/n/l/n/l |
| DO NOT TRADE K7 NY AM | +171/n/l/n/l  |  -576/n/l/n/l | +190/n/l/n/l  |  -556/n/l/n/l | +342/n/l/n/l  |  -1,151/n/l/n/l |
| DO NOT TRADE P7 London | -1,883/n/l/n/l  |  -2,841/n/l/n/l | -1,813/n/l/n/l  |  -2,777/n/l/n/l | -3,674/n/l/n/l  |  -5,573/n/l/n/l |
| DO NOT TRADE P7 NY AM | -395/-566/n/l  |  n/l/n/l/n/l | -388/-561/n/l  |  n/l/n/l/n/l | -747/-1,086/n/l  |  n/l/n/l/n/l |
| DO NOT TRADE K7 NY PM | -860/n/l/n/l  |  -1,419/+542/n/l | -834/n/l/n/l  |  -1,393/+567/n/l | -1,720/n/l/n/l  |  -2,838/+1,084/n/l |
| DO NOT TRADE K7 London | n/l/-1,778/n/l  |  n/l/-606/n/l | n/l/-1,739/n/l  |  n/l/-575/n/l | n/l/-3,605/n/l  |  n/l/-1,289/n/l |
| DO NOT TRADE four weakest (M7 London + P7 NY AM + P7 London + K7 NY AM) | -1,181/-2,090/n/l  |  n/l/-1,591/n/l | -1,020/-1,952/n/l  |  n/l/-1,458/n/l | -2,197/-4,194/n/l  |  n/l/-3,004/n/l |
| HALF SIZE M7 London | +234/+245/n/l  |  +200/+164/n/l | +243/+254/n/l  |  +209/+174/n/l | +501/+558/n/l  |  +492/+398/n/l |
| HALF SIZE P7 London | n/l/-611/n/l  |  -541/-267/n/l | n/l/-596/n/l  |  -522/-254/n/l | n/l/-1,278/n/l  |  -1,008/-487/n/l |
| HALF SIZE P7 NY AM | -80/-104/n/l  |  n/l/n/l/n/l | -79/-103/n/l  |  n/l/n/l/n/l | -118/-162/n/l  |  n/l/n/l/n/l |
| HALF SIZE K7 NY PM | n/l/-323/n/l  |  -316/n/l/n/l | n/l/-321/n/l  |  -314/n/l/n/l | n/l/-645/n/l  |  -632/n/l/n/l |
| HALF SIZE K7 London | -17/-495/n/l  |  +376/-70/n/l | -13/-492/n/l  |  +380/-71/n/l | -8/-971/n/l  |  +800/-122/n/l |
| HALF SIZE four weakest (M7 London + P7 NY AM + P7 London + K7 NY AM) | -450/-106/n/l  |  n/l/-84/n/l | -423/-81/n/l  |  n/l/-62/n/l | -783/-177/n/l  |  n/l/+16/n/l |

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
| DO NOT TRADE K7 London | n/l | | | | | | | |
| DO NOT TRADE four weakest (M7 London + P7 NY AM + P7 London + K7 NY AM) | 229 (-12,140) / 126 (-8,676) / +1,319 (9) | 523 (-933) / 70 (+3,442) / -200 (1) | 0 (+0) / 16 (-8,522) / +4,408 (3) | 445 (+35,964) / 1 (-1,224) / -1,152 (5) | 0 (+0) / 9 (+2,831) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 1 (-786) / 9 (-1,171) / +0 (0) | +22,104 / -13,320 / +4,375 |
| HALF SIZE M7 London | 4 (+1,462) / 3 (+548) / -141 (2) | 3 (+4,630) / 12 (-1,155) / +13,003 (88) | 0 (+0) / 2 (-2,582) / +727 (1) | 1 (-2,699) / 3 (+1,889) / -919 (6) | 1 (+1,199) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 1 (-637) / +0 (0) | +4,592 / -1,937 / +12,670 |
| HALF SIZE P7 London | n/l | | | | | | | |
| HALF SIZE P7 NY AM | 0 (+0) / 1 (-887) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / -1,227 (9) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | +0 / -887 / -1,227 |
| HALF SIZE K7 NY PM | n/l | | | | | | | |
| HALF SIZE K7 London | 14 (+8,719) / 22 (+5,852) / +4,095 (43) | 6 (-2,442) / 4 (-1,315) / +0 (0) | 1 (-2,452) / 1 (-1,191) / -622 (3) | 1 (+1,199) / 2 (-1,402) / -831 (3) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | +5,023 / +1,944 / +2,642 |
| HALF SIZE four weakest (M7 London + P7 NY AM + P7 London + K7 NY AM) | 13 (+295) / 6 (+24) / +1,490 (6) | 10 (+6,775) / 15 (-1,592) / +13,003 (88) | 0 (+0) / 4 (-4,128) / +817 (2) | 9 (-2,419) / 14 (-3,497) / -12,403 (108) | 1 (+899) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | +5,550 / -9,194 / +2,906 |

Window HOLD
| cell | K7 | M7 | U7 | P7 | H7 | A7 | O7 | total lost / gained / common $ |
|--|--|--|--|--|--|--|--|--|
| DO NOT TRADE M7 London | n/l | | | | | | | |
| DO NOT TRADE K7 NY AM | n/l | | | | | | | |
| DO NOT TRADE P7 London | n/l | | | | | | | |
| DO NOT TRADE P7 NY AM | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 27 (+14,637) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | 0 (+0) / 0 (+0) / +0 (0) | +14,637 / +0 / +0 |
| DO NOT TRADE K7 NY PM | n/l | | | | | | | |
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
| DO NOT TRADE M7 London | n/l | | | | | | | |
| DO NOT TRADE K7 NY AM | n/l | | | | | | | |
| DO NOT TRADE P7 London | n/l | | | | | | | |
| DO NOT TRADE P7 NY AM | n/l | | | | | | | |
| DO NOT TRADE K7 NY PM | n/l | | | | | | | |
| DO NOT TRADE K7 London | n/l | | | | | | | |
| DO NOT TRADE four weakest (M7 London + P7 NY AM + P7 London + K7 NY AM) | n/l | | | | | | | |
| HALF SIZE M7 London | n/l | | | | | | | |
| HALF SIZE P7 London | n/l | | | | | | | |
| HALF SIZE P7 NY AM | n/l | | | | | | | |
| HALF SIZE K7 NY PM | n/l | | | | | | | |
| HALF SIZE K7 London | n/l | | | | | | | |
| HALF SIZE four weakest (M7 London + P7 NY AM + P7 London + K7 NY AM) | n/l | | | | | | | |

## Table 5 - trade counts per window (cell vs JL3 base) and week-clustered bootstrap detail (JL3, pooled and L6M)
| cell | L6M (cell / base) | HOLD (cell / base) | GAP (cell / base) | PRE (cell / base) | X' (cell / base) | pooled (cell / base) | mean-change 90% interval L6M | pooled |
|--|--|--|--|--|--|--|--|--|
| DO NOT TRADE M7 London | 3940 / 4292 | n/l | n/l | n/l | n/l | n/l | -1,090..+2,960 | n/l |
| DO NOT TRADE K7 NY AM | 4146 / 4292 | n/l | n/l | n/l | n/l | n/l | -637..+964 | n/l |
| DO NOT TRADE P7 London | 3915 / 4292 | n/l | n/l | n/l | n/l | n/l | -3,293..-343 | n/l |
| DO NOT TRADE P7 NY AM | 4250 / 4292 | 3284 / 3311 | n/l | n/l | n/l | n/l | -931..+124 | n/l |
| DO NOT TRADE K7 NY PM | 4123 / 4292 | n/l | n/l | n/l | n/l | n/l | -1,652..-33 | n/l |
| DO NOT TRADE K7 London | n/l | 3054 / 3311 | n/l | n/l | n/l | n/l | n/l | n/l |
| DO NOT TRADE four weakest (M7 London + P7 NY AM + P7 London + K7 NY AM) | 3325 / 4292 | 2499 / 3311 | n/l | n/l | n/l | n/l | -4,044..+1,641 | n/l |
| HALF SIZE M7 London | 4304 / 4292 | 3324 / 3311 | n/l | n/l | n/l | n/l | -349..+779 | n/l |
| HALF SIZE P7 London | n/l | 3294 / 3311 | n/l | n/l | n/l | n/l | n/l | n/l |
| HALF SIZE P7 NY AM | 4293 / 4292 | 3310 / 3311 | n/l | n/l | n/l | n/l | -261..+86 | n/l |
| HALF SIZE K7 NY PM | n/l | 3315 / 3311 | n/l | n/l | n/l | n/l | n/l | n/l |
| HALF SIZE K7 London | 4299 / 4292 | 3330 / 3311 | n/l | n/l | n/l | n/l | -881..+883 | n/l |
| HALF SIZE four weakest (M7 London + P7 NY AM + P7 London + K7 NY AM) | 4298 / 4292 | 3305 / 3311 | n/l | n/l | n/l | n/l | -1,911..+788 | n/l |

## Table 6 - W44-removed variant (JL3; week 2026-10-26..11-01 removed): ulcer change / mean change
| cell | L3M | L6M | pooled | tier W44 |
|--|--|--|--|--|
| DO NOT TRADE M7 London | +11.3% / +484 | +13.5% / +1,106 | n/l | NOT FINISHED |
| DO NOT TRADE K7 NY AM | -22.9% / +338 | -16.4% / +313 | n/l | NOT FINISHED |
| DO NOT TRADE P7 London | -1.1% / -1,006 | -2.9% / -1,728 | n/l | NOT FINISHED |
| DO NOT TRADE P7 NY AM | +5.2% / -705 | +3.2% / -408 | n/l | NOT FINISHED |
| DO NOT TRADE K7 NY PM | -4.8% / -508 | -3.8% / -997 | n/l | NOT FINISHED |
| DO NOT TRADE K7 London | n/l | n/l | n/l | NOT FINISHED |
| DO NOT TRADE four weakest (M7 London + P7 NY AM + P7 London + K7 NY AM) | -14.4% / -1,876 | -8.2% / -790 | n/l | NOT FINISHED |
| HALF SIZE M7 London | +10.1% / +231 | +6.5% / +242 | n/l | NOT FINISHED |
| HALF SIZE P7 London | +3.7% / +67 | n/l | n/l | NOT FINISHED |
| HALF SIZE P7 NY AM | +1.9% / -283 | +1.3% / -83 | n/l | NOT FINISHED |
| HALF SIZE K7 NY PM | n/l | n/l | n/l | NOT FINISHED |
| HALF SIZE K7 London | -12.1% / -420 | -7.9% / -17 | n/l | NOT FINISHED |
| HALF SIZE four weakest (M7 London + P7 NY AM + P7 London + K7 NY AM) | +13.9% / -324 | +8.3% / -453 | n/l | NOT FINISHED |

## Table 7 - controls: draws landed / valid, realised vs cell share (JL3)
| control set | landed | valid | per-draw (book, cell share, realised, tol) of the first 3 draws |
|--|--|--|--|
| DO NOT TRADE M7 London | 0 | 0 | |
| DO NOT TRADE K7 NY AM | 0 | 0 | |
| DO NOT TRADE P7 London | 0 | 0 | |
| DO NOT TRADE P7 NY AM | 0 | 0 | |
| DO NOT TRADE K7 NY PM | 0 | 0 | |
| DO NOT TRADE K7 London | 0 | 0 | |
| DO NOT TRADE four weakest (M7 London + P7 NY AM + P7 London + K7 NY AM) | 0 | 0 | |
| HALF SIZE M7 London | 0 | 0 | |
| HALF SIZE P7 London | 0 | 0 | |
| HALF SIZE P7 NY AM | 0 | 0 | |
| HALF SIZE K7 NY PM | 0 | 0 | |
| HALF SIZE K7 London | 0 | 0 | |
| HALF SIZE four weakest (M7 London + P7 NY AM + P7 London + K7 NY AM) | 0 | 0 | |

## Notes
- Everything is FIRST PASS, in-sample over the 43 months; a window is shown only when every month of it landed for the cell and for the base. "n/l" = not landed. Missing = not finished.
- JL2 does not carry the live persist=1 take/lock lines (JL3 does); both are shown, tiers only on JL3.
- Raw-base context: DS3_REBUILD_S1.md raw table (mean R per trade by book x session). Stack effects (cap 6 lots, freed room) can make a raw-base weak cell still pay in the stack; this page is the engine answer.
