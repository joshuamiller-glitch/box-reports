# DS3_CELL_TESTS - engine cell tests: do not trade / half size weak book x session cells on JL3 and JL2 (W-CELL, order 11-17 07:28Z JOB 2)
VERDICT (data ends 2026-10-31; FIRST PASS; see below)

> VALIDATION (desk standard, W-CELL, FIRST PASS, 2026-11-17 08:10Z): trials counted = 26 real engine cells (13 cell definitions x JL3 and JL2: 6 do-not-trade singles + the four weakest together + 5 half-size singles + the four weakest half-sized; K7 NY AM is 1 lot so not halvable), each reported, no best-of selection (ledger family CT1); correction = percentile among 30 persistent-draw engine controls per cell (JL3 only; valid draws only) + week-clustered bootstrap (2,000) + the calibrated ulcer-primary tiers of DS3_PASS_RULE (cutoffs_ulc TUNED); no family-wide White/SPA because no cell is selected as best; PBO not applicable (no fitted choice); numbers shown: IN-SAMPLE (every window is part of the 43 months; the cells are fixed by the stage-0/1 raw table, not fitted per window; walk-forward not applicable). Data ends 2026-10-31.

## Status (what has landed)
- Base months landed: JL3 13 of 43, JL2 43 of 43. Real cells with at least one scored window: 22 of 26; with all 43 months: 0.
- Controls (JL3 + persistent random skip): N M7 London 0 landed / 0 valid; N K7 NY AM 0 landed / 0 valid; N P7 London 0 landed / 0 valid; N P7 NY AM 0 landed / 0 valid; N K7 NY PM 0 landed / 0 valid; N K7 London 0 landed / 0 valid; N four weakest (M7 Lon 0 landed / 0 valid; H M7 London 0 landed / 0 valid; H P7 London 0 landed / 0 valid; H P7 NY AM 0 landed / 0 valid; H K7 NY PM 0 landed / 0 valid; H K7 London 0 landed / 0 valid; H four weakest (M7 Lon 0 landed / 0 valid. A cell with fewer than 10 valid controls in a window is NOT FINISHED, never passing.
- Mechanism: ev_panel hook (outermost) overrides the book session lot table: do-not-trade = lots 0 in that session (engine entry gate, same as M7 asia = 0 today), half = lots/2 rounded half up (K7 2->1, M7 2->1, P7 4->2). Everything else (stack cap, locks, cuts, sizer, day caps, freed stack room, re-entries) runs unchanged = engine test, not path arithmetic. Identity cells TL3_CT_JL3_ID / TL3_CT_JL2_ID: TL3_CT_JL3_ID 202610: 691 trades net 37159.82 vs TL3_EV_JL3 691 net 37159.82 -> IDENTICAL; TL3_CT_JL2_ID 202610: 642 trades net 27487.58 vs TL3_EV_JN05W2JL2 642 net 27487.58 -> IDENTICAL.
- Four weakest chosen by the raw-base table (DS3_REBUILD_S1 / S0: one book alone, no layers): lowest mean R per trade: M7 London -0.009 (net -$48k), P7 NY AM 0.006, P7 London 0.008, K7 NY AM 0.008 (net $18k over 43 months); next K7 NY PM 0.015, K7 London 0.024. Stage 5 has no session-lot leave-one-out, so the raw base decides.
- Controls: book-wide persistent random skip (one uniform per 5-minute bucket, book, side; same seed set across cells), p calibrated by pilots so the realised share of the book removed matches the cell share within max(min(0.05, 0.25 x share), 0.002) (stricter than 0.05 for small shares); draw valid if pooled over its landed months it is within that tolerance. Half-size stand-in controls: 50% persistent skip inside the cell session, L6M + HOLD months only (so half-size tiers cannot reach older windows: shown as PROVISIONAL/NOT FINISHED).

## Table 1 - JL3: ulcer change / mean change per window (engine base lots; ulcer + = lower than base)
Cell vs JL3 base, same engine, same months. ulcer cell = % change of RMS daily drawdown (+ better); d mean = $/wk base lots (x1.75 and $4.84 in Table 3). P(ulcer lower) week-clustered bootstrap 2,000. Percentile (pct) = share of valid controls the real cell beats on ulcer / mean / max DD (L6M and HOLD). Tier from calibrated tiers; W44 = week 2026-10-26..11-01 removed.

| cell | L6M | HOLD | GAP | PRE | X' | pooled | P(ulcer lower) L6M / HOLD / pooled | max DD base -> cell, L6M / pooled | worst week base -> cell, L6M / pooled | pct ulcer / mean / DD, L6M | pct, HOLD | valid controls L6M | tier | tier W44 |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| DO NOT TRADE M7 London (1 mo) | n/l | n/l | n/l | n/l | n/l | n/l | n/l / n/l / n/l | n/l / n/l | n/l / n/l | n/a | n/a | 0 | NOT FINISHED (fewer than 10 valid controls in L6M/L3M) | NOT FINISHED |
| DO NOT TRADE K7 NY AM (1 mo) | n/l | n/l | n/l | n/l | n/l | n/l | n/l / n/l / n/l | n/l / n/l | n/l / n/l | n/a | n/a | 0 | NOT FINISHED (fewer than 10 valid controls in L6M/L3M) | NOT FINISHED |
| DO NOT TRADE P7 London (2 mo) | n/l | n/l | n/l | n/l | n/l | n/l | n/l / n/l / n/l | n/l / n/l | n/l / n/l | n/a | n/a | 0 | NOT FINISHED (fewer than 10 valid controls in L6M/L3M) | NOT FINISHED |
| DO NOT TRADE P7 NY AM (1 mo) | n/l | n/l | n/l | n/l | n/l | n/l | n/l / n/l / n/l | n/l / n/l | n/l / n/l | n/a | n/a | 0 | NOT FINISHED (fewer than 10 valid controls in L6M/L3M) | NOT FINISHED |
| DO NOT TRADE K7 NY PM (2 mo) | n/l | n/l | n/l | n/l | n/l | n/l | n/l / n/l / n/l | n/l / n/l | n/l / n/l | n/a | n/a | 0 | NOT FINISHED (fewer than 10 valid controls in L6M/L3M) | NOT FINISHED |
| DO NOT TRADE K7 London (3 mo) | n/l | n/l | n/l | n/l | n/l | n/l | n/l / n/l / n/l | n/l / n/l | n/l / n/l | n/a | n/a | 0 | NOT FINISHED (fewer than 10 valid controls in L6M/L3M) | NOT FINISHED |
| DO NOT TRADE four weakest (M7 London + P7 NY AM + P7 London + K7 NY AM) | not landed | | | | | | | | | | | | | | |
| HALF SIZE M7 London | not landed | | | | | | | | | | | | | | |
| HALF SIZE P7 London (2 mo) | n/l | n/l | n/l | n/l | n/l | n/l | n/l / n/l / n/l | n/l / n/l | n/l / n/l | n/a | n/a | 0 | NOT FINISHED (fewer than 10 valid controls in L6M/L3M) | NOT FINISHED |
| HALF SIZE P7 NY AM (1 mo) | n/l | n/l | n/l | n/l | n/l | n/l | n/l / n/l / n/l | n/l / n/l | n/l / n/l | n/a | n/a | 0 | NOT FINISHED (fewer than 10 valid controls in L6M/L3M) | NOT FINISHED |
| HALF SIZE K7 NY PM (2 mo) | n/l | n/l | n/l | n/l | n/l | n/l | n/l / n/l / n/l | n/l / n/l | n/l / n/l | n/a | n/a | 0 | NOT FINISHED (fewer than 10 valid controls in L6M/L3M) | NOT FINISHED |
| HALF SIZE K7 London (2 mo) | n/l | n/l | n/l | n/l | n/l | n/l | n/l / n/l / n/l | n/l / n/l | n/l / n/l | n/a | n/a | 0 | NOT FINISHED (fewer than 10 valid controls in L6M/L3M) | NOT FINISHED |
| HALF SIZE four weakest (M7 London + P7 NY AM + P7 London + K7 NY AM) (1 mo) | n/l | n/l | n/l | n/l | n/l | n/l | n/l / n/l / n/l | n/l / n/l | n/l / n/l | n/a | n/a | 0 | NOT FINISHED (fewer than 10 valid controls in L6M/L3M) | NOT FINISHED |

## Table 2 - JL2: ulcer change / mean change per window (engine base lots; ulcer + = lower than base)
Cell vs JL2 base, same engine, same months. ulcer cell = % change of RMS daily drawdown (+ better); d mean = $/wk base lots (x1.75 and $4.84 in Table 3). P(ulcer lower) week-clustered bootstrap 2,000. JL2: no controls built for this base (percentile on JL3 controls does not transfer): tier = NOT FINISHED, bootstrap only.

| cell | L6M | HOLD | GAP | PRE | X' | pooled | P(ulcer lower) L6M / HOLD / pooled | max DD base -> cell, L6M / pooled | worst week base -> cell, L6M / pooled | tier |
|--|--|--|--|--|--|--|--|--|--|--|
| DO NOT TRADE M7 London | not landed | | | | | | | | | | |
| DO NOT TRADE K7 NY AM (2 mo) | n/l | n/l | n/l | n/l | n/l | n/l | n/l / n/l / n/l | n/l / n/l | n/l / n/l | NOT FINISHED (no JL2 controls) |
| DO NOT TRADE P7 London (1 mo) | n/l | n/l | n/l | n/l | n/l | n/l | n/l / n/l / n/l | n/l / n/l | n/l / n/l | NOT FINISHED (no JL2 controls) |
| DO NOT TRADE P7 NY AM (1 mo) | n/l | n/l | n/l | n/l | n/l | n/l | n/l / n/l / n/l | n/l / n/l | n/l / n/l | NOT FINISHED (no JL2 controls) |
| DO NOT TRADE K7 NY PM (4 mo) | n/l | n/l | n/l | n/l | n/l | n/l | n/l / n/l / n/l | n/l / n/l | n/l / n/l | NOT FINISHED (no JL2 controls) |
| DO NOT TRADE K7 London (2 mo) | n/l | n/l | n/l | n/l | n/l | n/l | n/l / n/l / n/l | n/l / n/l | n/l / n/l | NOT FINISHED (no JL2 controls) |
| DO NOT TRADE four weakest (M7 London + P7 NY AM + P7 London + K7 NY AM) (3 mo) | n/l | n/l | n/l | n/l | n/l | n/l | n/l / n/l / n/l | n/l / n/l | n/l / n/l | NOT FINISHED (no JL2 controls) |
| HALF SIZE M7 London (2 mo) | n/l | n/l | n/l | n/l | n/l | n/l | n/l / n/l / n/l | n/l / n/l | n/l / n/l | NOT FINISHED (no JL2 controls) |
| HALF SIZE P7 London (2 mo) | n/l | n/l | n/l | n/l | n/l | n/l | n/l / n/l / n/l | n/l / n/l | n/l / n/l | NOT FINISHED (no JL2 controls) |
| HALF SIZE P7 NY AM | not landed | | | | | | | | | | |
| HALF SIZE K7 NY PM (1 mo) | n/l | n/l | n/l | n/l | n/l | n/l | n/l / n/l / n/l | n/l / n/l | n/l / n/l | NOT FINISHED (no JL2 controls) |
| HALF SIZE K7 London (2 mo) | n/l | n/l | n/l | n/l | n/l | n/l | n/l / n/l / n/l | n/l / n/l | n/l / n/l | NOT FINISHED (no JL2 controls) |
| HALF SIZE four weakest (M7 London + P7 NY AM + P7 London + K7 NY AM) (2 mo) | n/l | n/l | n/l | n/l | n/l | n/l | n/l / n/l / n/l | n/l / n/l | n/l / n/l | NOT FINISHED (no JL2 controls) |

## Table 3 - mean change $/wk at the three price/size columns (JL3 | JL2), L6M / HOLD / pooled
| cell | base lots $1.18 RT | $4.84 RT | x1.75 live lots $1.18 RT |
|--|--|--|--|
| DO NOT TRADE M7 London | n/l/n/l/n/l  |  n/l | n/l/n/l/n/l  |  n/l | n/l/n/l/n/l  |  n/l |
| DO NOT TRADE K7 NY AM | n/l/n/l/n/l  |  n/l/n/l/n/l | n/l/n/l/n/l  |  n/l/n/l/n/l | n/l/n/l/n/l  |  n/l/n/l/n/l |
| DO NOT TRADE P7 London | n/l/n/l/n/l  |  n/l/n/l/n/l | n/l/n/l/n/l  |  n/l/n/l/n/l | n/l/n/l/n/l  |  n/l/n/l/n/l |
| DO NOT TRADE P7 NY AM | n/l/n/l/n/l  |  n/l/n/l/n/l | n/l/n/l/n/l  |  n/l/n/l/n/l | n/l/n/l/n/l  |  n/l/n/l/n/l |
| DO NOT TRADE K7 NY PM | n/l/n/l/n/l  |  n/l/n/l/n/l | n/l/n/l/n/l  |  n/l/n/l/n/l | n/l/n/l/n/l  |  n/l/n/l/n/l |
| DO NOT TRADE K7 London | n/l/n/l/n/l  |  n/l/n/l/n/l | n/l/n/l/n/l  |  n/l/n/l/n/l | n/l/n/l/n/l  |  n/l/n/l/n/l |
| DO NOT TRADE four weakest (M7 London + P7 NY AM + P7 London + K7 NY AM) | n/l  |  n/l/n/l/n/l | n/l  |  n/l/n/l/n/l | n/l  |  n/l/n/l/n/l |
| HALF SIZE M7 London | n/l  |  n/l/n/l/n/l | n/l  |  n/l/n/l/n/l | n/l  |  n/l/n/l/n/l |
| HALF SIZE P7 London | n/l/n/l/n/l  |  n/l/n/l/n/l | n/l/n/l/n/l  |  n/l/n/l/n/l | n/l/n/l/n/l  |  n/l/n/l/n/l |
| HALF SIZE P7 NY AM | n/l/n/l/n/l  |  n/l | n/l/n/l/n/l  |  n/l | n/l/n/l/n/l  |  n/l |
| HALF SIZE K7 NY PM | n/l/n/l/n/l  |  n/l/n/l/n/l | n/l/n/l/n/l  |  n/l/n/l/n/l | n/l/n/l/n/l  |  n/l/n/l/n/l |
| HALF SIZE K7 London | n/l/n/l/n/l  |  n/l/n/l/n/l | n/l/n/l/n/l  |  n/l/n/l/n/l | n/l/n/l/n/l  |  n/l/n/l/n/l |
| HALF SIZE four weakest (M7 London + P7 NY AM + P7 London + K7 NY AM) | n/l/n/l/n/l  |  n/l/n/l/n/l | n/l/n/l/n/l  |  n/l/n/l/n/l | n/l/n/l/n/l  |  n/l/n/l/n/l |

## Table 4 - FREED-BOOK effects on JL3 (what the other books do with the freed stack room): trades lost / gained per book and $ (base lots), cell vs JL3, window shown
For do-not-trade cells the cell's own trades are "lost" by design (own book); lost / gained on OTHER books and the $ change on trades both runs share (path effect) are the freed-room effect. Format: n lost ($) / n gained ($) / common-trade change $ (n changed).

Window L6M
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

Window HOLD
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
| DO NOT TRADE M7 London | n/l | n/l | n/l | n/l | n/l | n/l | n/l | n/l |
| DO NOT TRADE K7 NY AM | n/l | n/l | n/l | n/l | n/l | n/l | n/l | n/l |
| DO NOT TRADE P7 London | n/l | n/l | n/l | n/l | n/l | n/l | n/l | n/l |
| DO NOT TRADE P7 NY AM | n/l | n/l | n/l | n/l | n/l | n/l | n/l | n/l |
| DO NOT TRADE K7 NY PM | n/l | n/l | n/l | n/l | n/l | n/l | n/l | n/l |
| DO NOT TRADE K7 London | n/l | n/l | n/l | n/l | n/l | n/l | n/l | n/l |
| HALF SIZE P7 London | n/l | n/l | n/l | n/l | n/l | n/l | n/l | n/l |
| HALF SIZE P7 NY AM | n/l | n/l | n/l | n/l | n/l | n/l | n/l | n/l |
| HALF SIZE K7 NY PM | n/l | n/l | n/l | n/l | n/l | n/l | n/l | n/l |
| HALF SIZE K7 London | n/l | n/l | n/l | n/l | n/l | n/l | n/l | n/l |
| HALF SIZE four weakest (M7 London + P7 NY AM + P7 London + K7 NY AM) | n/l | n/l | n/l | n/l | n/l | n/l | n/l | n/l |

## Table 6 - W44-removed variant (JL3; week 2026-10-26..11-01 removed): ulcer change / mean change
| cell | L3M | L6M | pooled | tier W44 |
|--|--|--|--|--|
| DO NOT TRADE M7 London | n/l | n/l | n/l | NOT FINISHED |
| DO NOT TRADE K7 NY AM | n/l | n/l | n/l | NOT FINISHED |
| DO NOT TRADE P7 London | n/l | n/l | n/l | NOT FINISHED |
| DO NOT TRADE P7 NY AM | n/l | n/l | n/l | NOT FINISHED |
| DO NOT TRADE K7 NY PM | n/l | n/l | n/l | NOT FINISHED |
| DO NOT TRADE K7 London | n/l | n/l | n/l | NOT FINISHED |
| HALF SIZE P7 London | n/l | n/l | n/l | NOT FINISHED |
| HALF SIZE P7 NY AM | n/l | n/l | n/l | NOT FINISHED |
| HALF SIZE K7 NY PM | n/l | n/l | n/l | NOT FINISHED |
| HALF SIZE K7 London | n/l | n/l | n/l | NOT FINISHED |
| HALF SIZE four weakest (M7 London + P7 NY AM + P7 London + K7 NY AM) | n/l | n/l | n/l | NOT FINISHED |

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
