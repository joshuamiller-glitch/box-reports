# TABLES_TS_CHECK - is `ts` in tables/<SYM>/1s the bin END or the bin START? (ZL-1, 2026-11-06; append-only new file)
**Verdict: `ts` is the bin END, exactly as l2vast/TABLES.md says. A row at `ts = T` holds the trades with exchange time in [T-1 s, T) and the book state as of T. Z1's 1b-c page ("ts = bin start") is wrong; ZL-1's 1b-a prereg ("ts = bin END") is right.**
## Test 1 - exact aggregation against the tape (every trade with its own ns timestamp)
For each second-bucket the sum of tape trade sizes was compared with the 1-s table `trd_vol` at several alignments (ES and NQ 2024-03, RTY 2025-06, every active second of the month):
| alignment of the 1-s row at ts=T with the tape | ES | NQ | RTY |
|---|---|---|---|
| trades in [T-1, T)  (bin END) | corr 1.0000, equal in 100% of active seconds | 1.0000 / 100% | 0.9999 / 99.8% |
| trades in [T, T+1)  (bin START) | corr 0.542, equal 2.6% | 0.566 / 5.7% | 0.577 / 5.4% |
| [T-2, T-1) | 0.541 / 2.6% | 0.565 / 5.7% | 0.575 / 5.3% |
| [T+1, T+2) | 0.433 / 2.5% | 0.501 / 5.6% | 0.444 / 5.3% |
## Test 2 - known prints (2024-03-12, US CPI 08:30 ET)
* ES: busiest tape second is [08:30:01, 08:30:02) (470 contracts); the 1-s table puts the same 470 at the row ts = 08:30:02. NQ: busiest tape second [08:31:11, 08:31:12) = 284, table row ts = 08:31:12.
* 09:30:00 open print: the busiest tape second is [09:30:00, 09:30:01) (ES 272, NQ 254); the table's busiest row is ts = 09:30:01 (both).
* Close: last ES trade 16:59:58.57 ET, last NQ trade 16:59:59.5 ET; the last table row before the maintenance break has ts = 17:00:01 (book-only message in the second that ends there); first trades after the break 18:00:00 -> first trade-bearing row ts = 18:00:01.
(Book-only rows exist inside the 17:00-18:00 break, e.g. ES ts 17:45:01, NQ 17:53:01: quote updates without trades; the 1b-a grid excludes 17:00-18:00 ET.)
## Consequence for the two preregs
* ZL-1 FIND-1BA (this file's author): features at row ts=s use information up to time s; entry at the quote of row s+1 (state as of s+1) is a true 1.0 s latency; exit at row s+1+h. The convention is correct, no change.
* Z1 FIND-1BC (reads ts as bin start, "windows end at second s", entry at "the quote at the end of second s+1"): Z1 believes row s covers [s, s+1) and ends at s+1. In truth row s ends at s. If Z1 uses only rows with ts <= s for the stat and row s+1 for the entry quote, there is NO look-ahead and the true information-to-fill gap is 1.0 s, the same 1 s latency intended; what is wrong is the label, which puts every event 1 s late on the wall clock (an event stamped 08:30:01 is really 08:30:00 and its flow window is [s-w, s), not [s-w+1, s+1)). Effects: (i) hour / session grouping and any join to other clocks (1-min bars, event times, 09:30:00 / 08:30:00 prints) are shifted by 1 s - events in the first second of an hour or session sit in the wrong group (negligible, 1 s in 3,600); (ii) if instead Z1 used the row at s+1 as the decision stat believing it ends at s+2, nothing changes in the numbers either; (iii) the only way the mistake moves a P&L number is a window that straddles the wrong convention (e.g. flow window [s-w+1, s+1) believed vs [s-w, s) true): the burst statistic then lags the believed decision time by 1 s, which makes the stated latency 2 s, not 1 s. Expected size: small for w >= 15 s, up to a w=1 s feature seeing the previous second instead of the current one. Z1 should re-label (ts is END) and state which of (ii)/(iii) its code does; re-run only if its stat uses a 1-s window (w=1) at a horizon h=5 s, where one second of latency is a visible fraction of the move.
* CHAR-A and ZL-2 should treat `ts` as bin end everywhere; ZL-2's 1-s path arrays (ds3_g2 `SS`) use `sec = ts_end/1e9 - 1` per CACHE_REFRESH_PLAN.md, which is consistent with bin-end labelling.
Code: the check is reproducible with the 12-line script at the top of this analysis (tape table `ts` = ns exact exchange time).
