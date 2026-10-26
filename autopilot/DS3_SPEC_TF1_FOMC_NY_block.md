# DS3_SPEC_TF1_FOMC_NY_block - executability spec and identity test (D3X, 2026-10-26)

Research output; NOT a live recommendation. **Object: an entry filter (trade-modifier), not a book.** Verdict: **DELIVERABLE** as a date-list gate on NQ NY-window entries. Track verdict CANDIDATE (paired CI includes 0; effect +28.8 pts/blocked trade below the 48 pt MDE; tested on a proxy book, so it must be re-tested on the actual DS3 books before use).

## 1. Rule (NT8)
- Applies to any DS3 book on NQ (it is a gate in front of the book's entry logic, no bars of its own). Hard-coded list of FOMC statement dates (ET) below (source: federalreserve.gov calendars via l2vast/standS/event_calendar_core.csv, all 32 entries VERIFIED, 2023-02-01 to 2026-12-09; the strategy needs the 2027+ dates added from the Fed calendar each year).
- Block: on an FOMC date, ignore NEW ENTRIES (including the entry leg of a reversal) whose decision (signal) bar starts in [09:30, 15:30) ET. Entries outside that window and exits/stops of open positions are untouched; positions already open are managed normally (the filter blocks entries only, as in the paired test).
- Order types / bars: none of its own (inherits the host book's bars; NT8 reads the ET date of the bar and a minute-of-day compare, no extra data).
- Neighbours tested: entries >= 13:30 only; FOMC day + next day NY. Both agree in sign (row: effects 34.6 and 13.2 pts).

FOMC dates: 2023-02-01, 2023-03-22, 2023-05-03, 2023-06-14, 2023-07-26, 2023-09-20, 2023-11-01, 2023-12-13, 2024-01-31, 2024-03-20, 2024-05-01, 2024-06-12, 2024-07-31, 2024-09-18, 2024-11-07, 2024-12-18, 2025-01-29, 2025-03-19, 2025-05-07, 2025-06-18, 2025-07-30, 2025-09-17, 2025-10-29, 2025-12-10, 2026-01-28, 2026-03-18, 2026-04-29, 2026-06-17, 2026-07-29, 2026-09-16, 2026-10-28, 2026-12-09

## 2. Identity test
The tested object is the set of trades removed. The box replayed the proxy book from scratch (5-minute Supertrend(10,3) flips inside the ASIA/LON/NY entry windows, next-bar-open fills; x_tf1.py, own bars/ET/indicator code) and compared with the library's proxy book (l2vast/ds3/out/def/proxy_book.pkl) on label days >= 2023-02-01: **5135 library trades, 5135 replay trades, 2 mismatches (0.039%)**. The blocked set (NY-window trades entered on FOMC ET dates): library 82 (WF window 56), replay 82 (WF 56), identical trade-for-trade on 82 of 82. The two proxy-book trades that differ are ASIA-session trades (2024-09-17 entry 21:30 vs 21:10 ET; 2026-09-15 entry 21:05 vs 21:10 ET), not NY-window or FOMC-day trades; cause not isolated (candidates: ATR seeding, a missing-minute bar). Limit 2%: pass.

## 3. Data, holidays, fills, cost
Calendar only; no price data beyond the host book's chart. FOMC dates are never early-close days. A rescheduled/unscheduled FOMC meeting is not in the list and would not be blocked. Costs: the filter itself has none; its benefit is that blocked trades cost 28.8 pts more than average (CI [-8.1, +56.1] pts, 56 pairs in WF, holdout +31.3 pts, 2023-04..2024-01 +24.7 pts, placebo 0.964).

## 4. Position limits, expectation, what could kill it
No contracts of its own. Weekly effect on the proxy book +$455/wk (2 NQ, 25.6 trades/wk), maxDD effect -$33.5k (proxy book is net negative, so the filter mostly removes a bad book's bad days). Kill list: the effect lives on ~14 FOMC days in WF (underpowered, year share max 0.51); the proxy book is not a DS3 book (ORB/ST/Renko may react differently on FOMC days); FOMC days with a 14:00 statement are already partly cut by the 15:00 no-entry gap of the T-B books, so the incremental effect on those books may be near zero; the list must be maintained.
