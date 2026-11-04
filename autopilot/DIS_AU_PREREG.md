# DIS-AU prereg (S4b), 2026-11-04, written before any DIS-AU statistic

Question: do the LIVE books (KB, PE, SM, HM, MV, PB; ts2 Q1-A reference stack, 1-s engine, 935 label days 2023-04-03..2026-10-30) behave differently or misbehave on irregular sessions? Measurement, not a hypothesis search; Shadow only, no PASS claims, no purchases. Reuses the engine rows (H.rows(), H.d.kin, H.d.kflat, SS seconds) already used in DIS-P.

Day classes (label day ld, ET, from the minute table ds3_fade/minute.parquet and the rows themselves):
- EARLY: RTH last bar mod < 959 (CME early closes, e.g. 13:00 ET) or fewer than 300 RTH bars with RTH present.
- HOLIDAY_OPEN: Globex bars present on ld but RTH bars < 300 (full-holiday Globex partial).
- DAY_AFTER_HOLIDAY: the previous Mon-Fri label day is absent from the table (market closed) or class EARLY/HOLIDAY_OPEN.
- SUNDAY: sessions whose entry second falls on Sunday 18:00-24:00 ET (Sunday-open Asia session).
- NORMAL: all other days.
Trade-level flags: CROSS_MAINT = [entry, flat] spans 17:00-18:00 ET on a Mon-Thu (daily CME maintenance halt); LATE_EARLY = a trade open past the early close (flat second after the day's last RTH bar + 60 s) on an EARLY day; ENTRY_CLOSED = entry second with no bar in the minute table within +-60 s.

Measures per class x book (6 books + stack) and per flag: n trades, mean net USD per trade (Q1-A lots), win rate, mean hold (min), exits at kflat beyond last-bar time; paired difference vs NORMAL = (class mean per trade) minus (NORMAL mean per trade, same book), day-block bootstrap (1000 draws) CI, MDE = 2.8 SE. Rule-misbehaviour audit: list every trade with LATE_EARLY or ENTRY_CLOSED, every CROSS_MAINT trade with its flat time and fill price vs last pre-halt bar, and every HOLIDAY_OPEN / EARLY day trade count vs the day's usual count. Stop slippage: engine stop exits where the exit price differs from the stop level by > 1.5 pts, by class (if the row-level exit price is not exposed by the engine, reported as 'not measurable' and no substitute is invented).
Tests registered: classes (EARLY, HOLIDAY_OPEN, DAY_AFTER, SUNDAY) x (6 books + stack) = 28 comparisons + 3 flag comparisons x 7 = 21 -> n_tested 49. Family: BH over the 49 plus a day-shuffled class-label null (200 worlds) for the max |t|. Honest labels: any class with fewer than 20 trades is reported as 'thin, inside MDE', not tested.
2013+ extension: signal-level only (DIS-X found the 1-minute rebuild reproduces entries but not weekly P&L, corr 0.66), so history is used for day-class calendar counts and entry-stream behaviour (n entries on irregular sessions vs normal), not for P&L claims.
Outputs: ledger DIS_AU, rows in FADE_ROWS_DISAU.md (class table), n_tested line DISAU_NTESTED.md, interim in DS3_DISCOVER2.md (append only) within +2.5 h of the order.
