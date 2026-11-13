# DS3_SMART_A1 — T-SMART A1 (cut, then get back in), A6 (first trade sets the session), A7 (never green) — W-SM1

Generated 2026-11-13 02:42 UTC. Exact engine (JN05W2 stack: live panel base + F3 + E1 + C22 + BR3S + FLAT45K), one set per job, shared-memory engine, hook code/th_smart1/sm1_hooks.py (outermost hooklist entry, no engine file touched). Shadow only, no PASS claim. Prereg autopilot/SMART_A1_PREREG.md (sha in DECISIONS.md).

**CAVEAT on every number here:** the engine P7/K7 state cut fires in the engine but did NOT fire live on 11-11 (autopilot/DS3_P7_CUT_FIDELITY.md). A1 depends on cuts firing, so it is reported in two worlds: **E world** = engine state cut on (reference = JN05W2, "the cut alone"; re-entry after StateCut/EarlyCut) and **N world** = every state-cut arm off and the F3 context cut removed, FLAT45K kept = flat/full-stop only (reference = SM_A1_NC0; re-entry after Stop/StopJoin/EarlyCut). SM_A1_NC1 = N world with FLAT45K also off = never cutting.

Thresholds: A1 trigger levels/ A7 pts are in points (lot independent); A6 is count based, so all three transfer unchanged to the user lots (K7 4, M7 4, U7 7, P7 12/7/7, H7 7, A7 2; caps x1.75). Only dollars scale: multiply a cell's d mean by (user lots / the cell's average lots of the affected book); averages in section 4.

## 0. Trend-week clause first, then windows (exact; a window appears only when all its months are present)

| set | ref | months | 5 best ref wks kept | winning wks turned losing | L6M cut % | L6M d mean/wk (all wks) | HOLD cut % | HOLD d mean/wk | WF cut / beat |
|--|--|--|--|--|--|--|--|--|--|
| SM_A1E_C10L | JN05W2 | 5 | (running) ||||||
| SM_A1E_L0L | JN05W2 | 4 | (running) ||||||
| SM_A1E_XL | JN05W2 | 5 | (running) ||||||
| SM_A1N_C10L | SM_A1_NC0 | 4 | (running) ||||||
| SM_A1N_L0L | SM_A1_NC0 | 5 | (running) ||||||
| SM_A1N_XL | SM_A1_NC0 | 3 | (running) ||||||
| SM_A1_ID | JN05W2 | 1 | (running) ||||||
| SM_A1_NC0 | JN05W2 | 6 | 70% ($223k of $316k) | 2 of 20 | -51.3 | -6993 | - | - | - |
| SM_A1_T | JN05W2 | 1 | (running) ||||||
| SM_A6_freshNP7 | JN05W2 | 4 | (running) ||||||
| SM_A6_halfALL | JN05W2 | 5 | (running) ||||||
| SM_A6_halfNP7 | JN05W2 | 2 | (running) ||||||
| SM_A6_skipM7 | JN05W2 | 4 | (running) ||||||
| SM_A6_skipNP7 | JN05W2 | 5 | (running) ||||||
| SM_A7_P7a | JN05W2 | 3 | (running) ||||||

cut % = stack maxDD vs the reference (positive = shallower); d mean = all-weeks mean difference $/wk. Identity: SM_A1_ID (hook on, rules never fire) must equal JN05W2 trade for trade (see section 5).

## 1. A1 re-entry diagnostics (exact; L6M/HOLD when complete)

| set | window | re-entries/wk | win rate | net $/wk | second-loss rate | double-cost est $/wk | re-entry targets/wk | ref cuts/wk (losing cut/stop exits) | of which raw-path recoveries/wk |
|--|--|--|--|--|--|--|--|--|--|

## 2. A7 NEVER GREEN — first-order screen (JN05W2 trade list, 1-s mid paths, slip 0.8; screen only; 80 cells (k in 3/5/8/12 pts, N in 120/300/600/1200 s, X in 15..35 pts) x 6 books x sessions)

Forward-only placebo = the SAME fired trades exit at a uniformly random later second (200 draws): p_own = share of draws >= the cell. Family null = max z over the book's 80 cells. **A cell must beat its placebo (p_own <= .10 on L6M and HOLD) to go to exact; none does.**

| book | best cell by L6M net $/wk (k/N/X) | nfire | L6M net $/wk | HOLD net $/wk | p_own L6M | p_own HOLD | best stack-DD cell (k/N/X): L6M cut % / net $/wk | book max z (80 cells) | cells with p_own <= .10 on both |
|--|--|--|--|--|--|--|--|--|--|
| A7 | 8/600/30 | 201 | -96 | -165 | 1.00 | 0.38 | 3/120/15: 5.0% / -362 | -2.17 | 0 of 80 |
| H7 | 8/300/15 | 307 | 337 | 458 | 0.96 | 1.00 | 3/120/15: 0.0% / 18 | 3.18 | 0 of 80 |
| K7 | 12/1200/35 | 887 | 212 | -228 | 1.00 | 0.70 | 12/300/15: 8.6% / -2151 | -4.66 | 0 of 80 |
| M7 | 8/300/15 | 1079 | 594 | -38 | 1.00 | 1.00 | 3/120/15: 0.0% / 158 | -1.04 | 0 of 80 |
| P7 | 3/600/30 | 256 | -185 | 34 | 1.00 | 1.00 | 8/120/20: 24.4% / -5359 | -2.03 | 0 of 80 |
| U7 | 12/600/20 | 427 | 146 | 569 | 0.97 | 0.99 | 12/120/15: 11.0% / -645 | -0.39 | 0 of 80 |

Reading: where a cell cuts the stack drawdown (P7, K7) it is by shrinking P7/K7 winners and losers alike (net $/wk strongly negative, p_own 1.0 = a random later exit does better than the never-green condition); the positive-net cells (H7, M7, U7) are small and also lose to their placebo. A7 is therefore a size dial with no information in the condition.

## 3. A6 FIRST TRADE SETS THE SESSION — first-order screen (JN05W2 trade list; group = book x label day x entry session; if the first trade lost, later trades of that group x0 (skip) / x0.5 (half))

| act | books | trades affected | L6M cut % | L6M d mean/wk | HOLD cut % | HOLD d mean/wk | PRE cut % | X' cut % | L6M winners removed $/wk | L6M losers avoided $/wk |
|--|--|--|--|--|--|--|--|--|--|--|
| half | A7 | 216 | 2.5 | -28 | 1.5 | -119 | -1.6 | -0.0 | 2683 | 2361 |
| skip | A7 | 216 | 5.0 | -56 | 3.1 | -237 | -3.1 | 0.0 | 2683 | 2361 |
| half | H7 | 108 | 2.9 | -74 | -1.9 | 97 | -1.6 | 0.7 | 1241 | 856 |
| skip | H7 | 108 | 5.7 | -148 | -3.8 | 195 | -3.1 | 1.4 | 1241 | 856 |
| half | K7 | 2465 | 4.6 | -1030 | 5.3 | -767 | 3.4 | 15.0 | 15725 | 12988 |
| skip | K7 | 2465 | 2.4 | -2060 | -2.1 | -1534 | 4.8 | 30.0 | 15725 | 12988 |
| half | M7 | 1412 | -0.7 | 46 | 3.4 | 194 | -7.7 | -1.1 | 6977 | 7446 |
| skip | M7 | 1412 | -1.4 | 92 | 6.9 | 388 | -15.5 | -2.3 | 6977 | 7446 |
| half | P7 | 1381 | 5.4 | -1476 | 7.5 | -1770 | 14.4 | -5.2 | 21583 | 17476 |
| skip | P7 | 1381 | -5.2 | -2953 | 14.8 | -3541 | 7.8 | -23.7 | 21583 | 17476 |
| half | U7 | 145 | 0.0 | 159 | 6.1 | 90 | -3.2 | 0.0 | 2976 | 2908 |
| skip | U7 | 145 | 0.0 | 318 | 12.1 | 179 | -7.3 | 0.0 | 2976 | 2908 |
| half | all | 5727 | 11.8 | -2648 | 15.3 | -2425 | 9.2 | 9.3 | 51186 | 44035 |
| skip | all | 5727 | -4.8 | -5296 | 11.3 | -4851 | 17.6 | 7.8 | 51186 | 44035 |
| half | nonP7 | 4346 | 9.2 | -1128 | 12.4 | -971 | -4.8 | 14.6 | 29602 | 26559 |
| skip | nonP7 | 4346 | 18.5 | -2255 | 12.2 | -1941 | -9.9 | 29.1 | 29602 | 26559 |

Reading: removing the later trades of a book-session after a losing first trade takes out about as many winner dollars as loser dollars (e.g. all books: $51.2k winners vs $44.0k losers per week), so the family is a size dial that costs mean; only M7 (skip) is positive on mean and it moves the stack by < $100/wk. Exact sets run for the top cells (section 0).

## 4. Notes

dead_lookup before the sets: 10 family specs (reentry/never_green/first_trade/stop_and_reverse variants) = 0 hits. Exact cells and first-order cells are appended to the dead ledger after scoring (program SMART_A1).

Re-entry mechanics (hook): decision at the close of 1-s row r, order at row r+1, market through the full try_entry chain (panel, JN05W2 gates, post-cut blackout: U7 same-side 30 min applies), P7 45-s confirmation bypassed, one re-entry per cut, a re-entry trade never re-enters. State-book triggers (pulled_against / delta with) are NOT implemented: the 1-s state arrays carry no delta, so only price-proof triggers (level, cutk, ext) exist.
