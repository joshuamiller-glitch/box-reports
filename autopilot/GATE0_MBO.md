# GATE0_MBO - can exact CME MBO reproduce the live cut? (Test 1; PRE-PROOF; MBO-BOOK, 2026-11-08)
## VERDICT (rule fixed by the user)
Best of 112 pre-registered delivery conventions reproduces 51 of 92 live cuts in the STRICT window (55.4%, needs >= 85%) with 48 false cuts out of 99 fires (48.5% of fires, 45.7% of 105 trades, needs <= 10%); no convention passes, so the live cut cannot be reproduced from any purchasable data: an exact MBO rebuild (identical to mbp-10 at 100% on every validated window) gives the same 41-51 of 92 as the owned mbp-10 stream did, and the failure is not a missing book but too many early or false fires (38 early, 10 held trades cut, only 3 misses), e.g. P7 Wed 11-04 19:57 held to Target but the rule fires at 44.6x a normal level with -30.8 pt (table rows 80, 85, 91, 92, 98). Programme stops here per the rule; the MBO history quote was not requested.
## Cost (GATE0_MBO_DATA.md was not present when this was written)
MANIFEST.jsonl quotes: 2.9986 + 3.4958 + 4.9014 + 3.6633 = USD 15.06 for 4 files, 160,413,127 records (file sha256 in /mnt/l2/l2vast/_mbo_book/raw_sha.txt). Actual billed cost: take from GATE0_MBO_DATA.md.
## Pre-registration
DECISIONS.md line 2026-11-08 MBO-BOOK; file l2vast/ds3/prereg/MBO_BOOK_prereg.md sha256 ce3cd92a9f7e6686ddb677ac5ace2b5d57c51b772aac5f7b9ec3468d20586f28, written before any scoring; grid, scoring and the 85%/10% rule were not changed after the first score. Seal: ds3_all_ea/manifest_after.json sha256 759f2258daac9d28... unchanged. Only /mnt/l2/l2vast/_mbo_book/ written (plus code/mbo_book, prereg, this report, DECISIONS.md line).
## 1. Book rebuild and validation
Code code/mbo_book/ (mbo_book.py numba: hash table of live orders, per-side price-level aggregation, A/C/M/R/F/T/N; test_synth.py 0 mismatches against a python reference; mbo_run.py -> T table with the 20-level book on every T record and at the F_LAST end of its event, plus 50 ms grids per clock; 2,316,491 T records = the owned mbp-10 count). F (resting fill) reduces the order, T does not touch the book. F_LAST (flag 128) ends an event, not an MDP3 packet (sequence repeats inside a packet; most A/C/M carry 128).
Validation vs owned mbp-10 raw: top-10 state at every event end joined on (ts_recv, ts_event, sequence): 2026-11-02 14:00-14:10Z sample window 215,545 rows 0 mismatches; further windows (11-01 23:10/23:30/00:00/01:00/03:00, 11-02 23:00/23:10, 11-03 23:00 (6 of 107,354 rows differ, 99.994%), 11-03 23:10, 11-04 16:00 (3 of 1,007,997), 11-04 21:33, 11-04 23:00/23:10): 0-6 mismatches. First 10 min of the file (11-01 23:00-23:10Z): 1.85% rows mismatch because the request starts at 23:00Z and orders entered in the pre-open hour are missing (659,802 cancels of unknown orders on day 1, 2,741,504 over the week; recommend the 22:00-23:00Z pre-open hour if any rerun is made); all 105 trades start after 23:36Z. One window (11-05 11:00Z) joined only 824 rows, a join-file issue of the validator, not a book mismatch finding. Log /mnt/l2/l2vast/_mbo_book/validation_full.log.
## 2. Convention table (112 conventions; top 20 by strict; full /mnt/l2/l2vast/_mbo_book/convention_table.csv)
Name = cadence (E book on T record, P book at event end, number = conflation ms, _lag = one interval older) _ agg0 fill / agg1 aggressor order / agg2 per interval _ clk0 ts_recv / clk1 ts_event _ L levels.
| conv | strict | % | fires | false | false%fires | false%105 | decision% | held cut | early | miss |
|--|--|--|--|--|--|--|--|--|--|--|
| 50_agg1_clk1_L20 | 51 | 55.4 | 99 | 48 | 48.5 | 45.7 | 87.6 | 10 | 38 | 3 |
| 50_agg0_clk0_L20 | 50 | 54.3 | 99 | 49 | 49.5 | 46.7 | 87.6 | 10 | 39 | 3 |
| 50_agg1_clk0_L20 | 50 | 54.3 | 99 | 49 | 49.5 | 46.7 | 87.6 | 10 | 39 | 3 |
| 50_agg0_clk1_L20 | 50 | 54.3 | 99 | 49 | 49.5 | 46.7 | 87.6 | 10 | 39 | 3 |
| 500_lag_agg0_clk0_L10 | 49 | 53.3 | 88 | 39 | 44.3 | 37.1 | 79.0 | 9 | 30 | 13 |
| 250_agg1_clk0_L10 | 49 | 53.3 | 91 | 42 | 46.2 | 40.0 | 81.9 | 9 | 33 | 10 |
| 50_agg0_clk0_L10 | 49 | 53.3 | 92 | 43 | 46.7 | 41.0 | 81.0 | 10 | 33 | 10 |
| 100_agg1_clk0_L10 | 49 | 53.3 | 92 | 43 | 46.7 | 41.0 | 82.9 | 9 | 34 | 9 |
| 50_agg0_clk1_L10 | 49 | 53.3 | 92 | 43 | 46.7 | 41.0 | 81.0 | 10 | 33 | 10 |
| 50_lag_agg0_clk0_L10 | 49 | 53.3 | 93 | 44 | 47.3 | 41.9 | 83.8 | 9 | 35 | 8 |
| 50_lag_agg0_clk1_L10 | 49 | 53.3 | 93 | 44 | 47.3 | 41.9 | 83.8 | 9 | 35 | 8 |
| 50_lag_agg1_clk1_L10 | 49 | 53.3 | 93 | 44 | 47.3 | 41.9 | 83.8 | 9 | 35 | 8 |
| 100_agg2_clk0_L10 | 49 | 53.3 | 94 | 45 | 47.9 | 42.9 | 84.8 | 9 | 36 | 7 |
| 100_agg1_clk0_L20 | 49 | 53.3 | 99 | 50 | 50.5 | 47.6 | 87.6 | 10 | 40 | 3 |
| 100_agg2_clk0_L20 | 49 | 53.3 | 99 | 50 | 50.5 | 47.6 | 87.6 | 10 | 40 | 3 |
| 100_agg1_clk1_L20 | 49 | 53.3 | 99 | 50 | 50.5 | 47.6 | 87.6 | 10 | 40 | 3 |
| 100_agg2_clk1_L20 | 49 | 53.3 | 99 | 50 | 50.5 | 47.6 | 87.6 | 10 | 40 | 3 |
| 500_agg0_clk0_L10 | 48 | 52.2 | 85 | 37 | 43.5 | 35.2 | 76.2 | 9 | 28 | 16 |
| 500_lag_agg0_clk1_L10 | 48 | 52.2 | 85 | 37 | 43.5 | 35.2 | 76.2 | 9 | 28 | 16 |
| E_agg0_clk0_L10 | 48 | 52.2 | 87 | 39 | 44.8 | 37.1 | 78.1 | 9 | 30 | 14 |
Max strict by cadence: C50 51, C100 49, C250 49, C500 49, E 48, P 47. By levels: 20 -> 51, 10 -> 49. By clock: ts_event 51, ts_recv 50. By aggregation: order 51, fill 50, interval 49. Spread over all 112: 41-51 (median 47). Decision-level best 87.6% is not informative: the rule fires on almost every armed loser (99 fires on 105 trades).
Informational (best convention, CUT trades only): fires within [-10, +2] s of the live exit: 60; within [-30, +2] s: 72; fires earlier than 30 s: 17.
## 3. Best convention (50_agg1_clk1_L20) by book and by half
Book (strict counts):
```
      cut  strict  held  held_cut
book                             
A7     14      10     1         1
H7      2       1     0         0
K7     30      17     4         3
M7     13       6     3         2
O7      2       2     0         0
P7     24      12     4         4
U7      3       2     0         0
X3      2       1     0         0
X4      1       0     1         0
X5      1       0     0         0
```
Half (before / after Tue 11-03 17:00 ET):
```
      cut  strict  held_cut
half                       
H1     33      18         4
H2     59      33         6
```
## 4. Per-trade failures under the best convention (every trade that is not right: 51 of 105)
Features are at the firing callback. For EARLY fire / FALSE rows the best-pm columns are empty ('none armed') because the trade ended at the fire; the 'max best pm over all 112' column is the largest pulled_mult any convention reaches inside [L-3, L+1] with armed loss and newMae, and 'conv matching' is how many of the 112 conventions match that trade strictly. Stop source: repl = replica recorded stop, NOMI = nominal stop (policy only matters on a few rows).
| # | book | side | qty | live exit ET | live kind | result | d (s) | rule | unreal@fire | pulled | Med | pm@fire | secs_ext | best pm in [L-3,L+1] (armed,newMae) | its unreal/secs/pulled/Med | max best-pm over all 112 conv | conv matching | stop src |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 0 | P7 | L | 10 | 11-01 20:25:34 | Target | FALSE (held cut) | -3709 | panel | -33.20 | 129 | 2.52 | 51.2 | 0.07 | none armed |  | none | 0 | repl |
| 1 | P7 | L | 4 | 11-01 23:02:27 | Target | FALSE (held cut) | -7406 | panel | -31.38 | 95 | 2.73 | 34.8 | 1.91 | none armed |  | none | 0 | NOMI |
| 8 | U7 | S | 6 | 11-02 03:01:49 | ThL2Cut | MISS |  |  |  | | | |  | 23.4 | -32.0/0.1/63/2.69 | 24.8 | 0 | repl |
| 10 | X5 | S | 2 | 11-02 04:06:50 | ThL2Cut | EARLY fire | -12 | panel | -30.50 | 112 | 2.35 | 47.6 | 0.00 | none armed |  | none | 0 | repl |
| 7 | M7 | S | 3 | 11-02 04:18:39 | ThL2Cut | EARLY fire | -170 | panel | -32.08 | 72 | 2.36 | 30.6 | 0.07 | none armed |  | none | 0 | repl |
| 9 | P7 | S | 2 | 11-02 04:18:39 | ThL2Cut | EARLY fire | -2318 | panel | -30.62 | 77 | 2.43 | 31.7 | 0.09 | none armed |  | none | 0 | repl |
| 11 | X4 | L | 2 | 11-02 07:06:08 | ThL2Cut | EARLY fire | -488 | panel | -31.38 | 104 | 2.90 | 35.8 | 0.00 | none armed |  | 25.3 | 0 | NOMI |
| 16 | X3 | S | 2 | 11-02 08:36:46 | PolicyCut | EARLY fire | -15 | panel | -30.25 | 129 | 2.77 | 46.6 | 0.37 | none armed |  | 25.5 | 0 | NOMI |
| 13 | P7 | S | 2 | 11-02 08:36:55 | PolicyCut | EARLY fire | -3 | panel | -31.12 | 310 | 2.40 | 129.0 | 1.99 | 130.4 | -32.9/1.9/314/2.41 | 207.7 | 16 | repl |
| 19 | P7 | S | 4 | 11-02 10:09:42 | PolicyCut | EARLY fire | -254 | panel | -30.19 | 384 | 2.78 | 138.1 | 0.12 | none armed |  | 151.6 | 8 | repl |
| 21 | H7 | L | 1 | 11-02 10:38:19 | PolicyCut | EARLY fire | -335 | panel | -30.25 | 295 | 4.28 | 68.9 | 0.34 | none armed |  | 48.1 | 8 | repl |
| 20 | M7 | L | 1 | 11-02 10:47:27 | ThL2Cut | EARLY fire | -515 | panel | -30.25 | 296 | 3.51 | 84.3 | 0.17 | none armed |  | 42.3 | 12 | repl |
| 25 | P7 | S | 4 | 11-02 20:29:16 | PolicyCut | EARLY fire | -4 | panel | -30.87 | 150 | 2.11 | 71.2 | 0.23 | none armed |  | none | 0 | repl |
| 28 | P7 | S | 4 | 11-02 21:03:11 | ThL2Cut | EARLY fire | -587 | panel | -30.44 | 97 | 2.18 | 44.6 | 0.00 | none armed |  | 52.8 | 40 | repl |
| 27 | K7 | L | 1 | 11-02 22:36:58 | PolicyCut | EARLY fire | -8734 | policy | -29.50 | 116 | 2.14 | 54.3 | 0.00 | none armed |  | none | 0 | repl |
| 29 | A7 | S | 1 | 11-03 00:42:01 | ThL2Cut | EARLY fire | -13 | panel | -34.50 | 77 | 2.35 | 32.8 | 0.92 | none armed |  | none | 0 | repl |
| 32 | K7 | L | 1 | 11-03 01:47:31 | ThL2Cut | EARLY fire | -117 | panel | -34.25 | 78 | 2.08 | 37.6 | 0.18 | none armed |  | none | 0 | repl |
| 34 | M7 | S | 1 | 11-03 02:47:29 | Stop | FALSE (held cut) | -1163 | panel | -33.75 | 78 | 2.15 | 36.2 | 1.66 | none armed |  | none | 0 | repl |
| 33 | K7 | S | 1 | 11-03 02:55:35 | Stop | FALSE (held cut) | -1575 | panel | -46.00 | 140 | 2.19 | 63.9 | 0.00 | none armed |  | none | 0 | repl |
| 40 | K7 | L | 2 | 11-03 18:37:42 | PolicyCut | EARLY fire | -203 | panel | -31.13 | 77 | 2.24 | 34.3 | 0.00 | none armed |  | 30.5 | 6 | repl |
| 42 | P7 | L | 7 | 11-03 18:37:42 | PolicyCut | EARLY fire | -206 | panel | -32.36 | 82 | 2.25 | 36.5 | 0.33 | none armed |  | 30.5 | 6 | repl |
| 43 | P7 | S | 4 | 11-03 19:04:10 | PolicyCut | EARLY fire | -4 | panel | -30.25 | 67 | 2.16 | 31.0 | 2.30 | none armed |  | 48.7 | 24 | repl |
| 44 | K7 | S | 1 | 11-03 19:04:10 | PolicyCut | EARLY fire | -17 | panel | -36.00 | 106 | 2.18 | 48.7 | 0.00 | none armed |  | 35.6 | 0 | repl |
| 48 | A7 | S | 1 | 11-03 20:41:30 | PolicyCut | EARLY fire | -7 | panel | -30.25 | 84 | 1.87 | 45.0 | 0.00 | none armed |  | none | 0 | repl |
| 53 | P7 | S | 4 | 11-03 22:16:23 | ThL2Cut | EARLY fire | -18 | panel | -30.81 | 70 | 1.74 | 40.2 | 1.87 | none armed |  | none | 0 | repl |
| 55 | P7 | S | 4 | 11-03 23:09:26 | PolicyCut | EARLY fire | -12 | panel | -31.37 | 80 | 1.72 | 46.5 | 0.00 | none armed |  | none | 0 | repl |
| 56 | K7 | S | 1 | 11-03 23:39:04 | ThL2Cut | EARLY fire | -3 | panel | -30.00 | 138 | 1.86 | 74.2 | 1.08 | 77.9 | -30.0/0.4/145/1.86 | 84.3 | 0 | repl |
| 60 | A7 | L | 1 | 11-04 00:43:18 | Target | FALSE (held cut) | -616 | panel | -35.75 | 73 | 1.82 | 40.1 | 0.00 | none armed |  | none | 0 | NOMI |
| 63 | K7 | L | 2 | 11-04 01:19:12 | ThL2Cut | EARLY fire | -69 | panel | -32.38 | 57 | 1.78 | 32.0 | 0.88 | none armed |  | 22.8 | 0 | repl |
| 64 | K7 | L | 1 | 11-04 02:21:31 | ThL2Cut | EARLY fire | -36 | panel | -33.50 | 71 | 2.16 | 32.9 | 0.17 | none armed |  | 25.7 | 0 | repl |
| 66 | K7 | L | 1 | 11-04 04:02:07 | PolicyCut | EARLY fire | -182 | panel | -30.75 | 85 | 2.31 | 36.8 | 0.69 | none armed |  | none | 0 | repl |
| 67 | P7 | L | 4 | 11-04 04:02:07 | PolicyCut | EARLY fire | -60 | panel | -30.13 | 88 | 2.27 | 38.8 | 0.00 | none armed |  | 39.2 | 0 | repl |
| 68 | M7 | L | 2 | 11-04 04:02:07 | PolicyCut | EARLY fire | -39 | panel | -33.00 | 85 | 2.25 | 37.8 | 0.00 | none armed |  | 39.2 | 0 | repl |
| 69 | K7 | S | 1 | 11-04 04:08:30 | ThL2Cut | EARLY fire | -14 | panel | -30.50 | 83 | 2.20 | 37.8 | 1.60 | none armed |  | 39.5 | 3 | repl |
| 70 | K7 | L | 1 | 11-04 05:45:01 | ThL2Cut | EARLY fire | -5 | panel | -32.00 | 107 | 2.12 | 50.6 | 0.28 | none armed |  | none | 0 | repl |
| 76 | K7 | L | 1 | 11-04 14:17:26 | ThL2Cut | MISS |  |  |  | | | |  | 70.8 | -30.2/0.7/202/2.85 | 91.4 | 0 | repl |
| 77 | K7 | S | 1 | 11-04 15:31:33 | PolicyCut | MISS |  |  |  | | | |  | 88.9 | -31.2/0.8/248/2.79 | 109.0 | 24 | repl |
| 79 | K7 | S | 1 | 11-04 19:30:26 | ThL2Cut | EARLY fire | -13 | panel | -32.75 | 106 | 2.38 | 44.6 | 1.19 | none armed |  | none | 0 | repl |
| 81 | A7 | S | 1 | 11-04 19:44:04 | ThL2Cut | EARLY fire | -6 | panel | -30.00 | 122 | 2.23 | 54.8 | 3.71 | none armed |  | 26.3 | 25 | repl |
| 80 | P7 | S | 7 | 11-04 19:57:29 | Target | FALSE (held cut) | -1636 | panel | -30.82 | 106 | 2.38 | 44.6 | 1.19 | none armed |  | none | 0 | repl |
| 85 | K7 | S | 1 | 11-04 22:53:11 | Target | FALSE (held cut) | -2779 | panel | -30.50 | 136 | 2.17 | 62.8 | 0.00 | none armed |  | none | 0 | repl |
| 87 | A7 | S | 1 | 11-05 01:13:43 | ThL2Cut | EARLY fire | -136 | panel | -30.50 | 73 | 2.01 | 36.3 | 0.35 | none armed |  | none | 0 | repl |
| 88 | P7 | S | 4 | 11-05 01:47:21 | ThL2Cut | EARLY fire | -24 | panel | -33.50 | 61 | 2.03 | 30.0 | 0.65 | none armed |  | 43.7 | 4 | repl |
| 89 | M7 | L | 1 | 11-05 02:22:04 | ThL2Cut | EARLY fire | -5 | panel | -33.25 | 71 | 2.14 | 33.1 | 0.00 | none armed |  | 40.9 | 6 | repl |
| 91 | M7 | L | 2 | 11-05 03:17:20 | Target | FALSE (held cut) | -1258 | policy | -29.50 | 94 | 2.06 | 45.7 | 0.00 | none armed |  | none | 0 | repl |
| 92 | P7 | L | 7 | 11-05 03:17:20 | Target | FALSE (held cut) | -1258 | policy | -28.08 | 94 | 2.06 | 45.7 | 0.00 | none armed |  | none | 0 | repl |
| 94 | P7 | L | 2 | 11-05 03:48:37 | ThL2Cut | EARLY fire | -29 | policy | -29.13 | 86 | 2.70 | 31.9 | 1.98 | none armed |  | 17.5 | 0 | repl |
| 95 | M7 | L | 1 | 11-05 03:48:37 | ThL2Cut | EARLY fire | -29 | policy | -29.25 | 86 | 2.70 | 31.9 | 1.98 | none armed |  | 17.5 | 0 | NOMI |
| 98 | K7 | S | 1 | 11-05 04:35:14 | BookLock | FALSE (held cut) | -13 | panel | -42.25 | 87 | 2.54 | 34.2 | 0.47 | none armed |  | none | 0 | repl |
| 99 | M7 | L | 1 | 11-05 07:22:47 | ThL2Cut | EARLY fire | -12 | panel | -31.75 | 95 | 2.45 | 38.7 | 1.02 | none armed |  | none | 0 | repl |
| 102 | M7 | S | 1 | 11-05 08:04:50 | ThL2Cut | EARLY fire | -7 | panel | -31.00 | 95 | 2.62 | 36.3 | 0.00 | none armed |  | 49.0 | 10 | repl |
The three MISS rows show the missing-support direction: #8 U7 (-32.0 pt, pulled 63 vs 30 x 2.69 = 80.7, best pm 24.8 under every convention), #76 K7 and #77 K7 reach pm 70.8 / 88.9 but fail newMae/throttle/timing. The dominant error is the opposite: 38 CUT trades fire 3 s to 2,318 s before the live cut and 10 HELD trades fire at pm 34-64, i.e. the rebuilt book carries MORE cancelled size than the live DOM did (the live code saw pm below 30 where the exact book says 31-138). Pairs of identical live outcome/different sim: P7 #19 (pm 138.1, -254 s), H7 #21 (68.9, -335 s), M7 #20 (84.3, -515 s) were held 4-9 minutes longer by the live strategy at pm 69-138.
## 5. Caveats
Entry state is the live file average, one entry second (adds inside the trade not modelled; they would only make newMae more permissive, which cannot remove the early fires); 11 of 105 stop distances are NOMINAL (policy rows only); sgn from the exact pre-trade top of book (live used NT8 Bid/Ask events); MedLevel seeded at the first snapshot of the week; DS7 panel arm 30 for all books. These are listed in the pre-registration; none was tuned after scoring. Counts are small (92 cuts, 13 held).

## ADDENDUM (2026-11-08, requested by the lead after seeing GATE0_MBO_DATA.md; POST-HOC rebuild-correctness check, NOT a new grid; the 112-convention grid and the scoring are unchanged)
Code: code/mbo_book/seq_check.py, mbo_run.py (--order=file|recv_seq|ev_seq), run_score_sub.py; outputs /mnt/l2/l2vast/_mbo_book/{full,full_recv_seq,full_ev_seq}, sub_*.csv, val_*.log. Seal re-hashed: ds3_all_ea/manifest_after.json 759f2258daac9d2865ee3fc098e4f5a6d596a57227b9ad41f91d4a9f182965d2 unchanged; no purchase.
**(1) Ordering used in the verdict:** FILE ORDER as delivered (Databento orders by ts_recv, then exchange order within it). No sort by sequence or ts_event; a single instrument (id 261401), all channel_id as in the file; state carried across the four files; chunks cut at an F_LAST (flag 128) boundary.
**(2) The backward steps (file 11-03 23:00 -> 11-04 23:00, 52.2 M events):** 197 backward steps in `sequence`; ts_recv is monotone (0 decreases). 196 of 197 are inside ONE ts_recv value (same ts_recv as the previous record, delta 0) and all 197 are on the same channel_id (8); typical pattern 2833 -> 2832 -> 2829, i.e. records of one packet/ts_recv group with sequence out of order. The 197th is the Globex-open special trade record (sequence 297,664,259 -> 0, order_id 0, side N, ts_event reset), not a reorder. Before the check, the verdict code did not treat them specially (file order).
**(3) Reruns (best 5 by the original table + per-print, no-conflation reference E_agg0_clk0_L20; same 105 trades, same scoring):**
| convention | file order strict / false / fires | recv_seq: stable sort by (ts_recv, sequence) | ev_seq: stable sort by (ts_event, sequence) |
|--|--|--|--|
| 50_agg1_clk1_L20 | 51 / 48 / 99 | 51 / 48 / 99 | 51 / 48 / 99 |
| 50_agg0_clk0_L20 | 50 / 49 / 99 | 50 / 49 / 99 | 48 / 45 / 93 |
| 50_agg1_clk0_L20 | 50 / 49 / 99 | 50 / 49 / 99 | 48 / 45 / 93 |
| 50_agg0_clk1_L20 | 50 / 49 / 99 | 50 / 49 / 99 | 50 / 49 / 99 |
| 500_lag_agg0_clk0_L10 | 49 / 39 / 88 | 49 / 39 / 88 | 46 / 38 / 84 |
| E_agg0_clk0_L20 (per print, no conflation) | 47 / 42 / 89 | 47 / 42 / 89 | 47 / 42 / 89 |
Book vs mbp-10 (rows differing / joined at event ends, 10-min windows): 11-01 23:00Z (file start transient) file 2441 / 132,055, recv_seq 2441, ev_seq 2441; 11-03 23:00Z file 6 / 107,354, recv_seq 6, ev_seq 18,677 (82.6% agree); 11-04 16:00Z file 3 / 1,007,997, recv_seq 3, the ev_seq run was only validated here before the window fix (3); 11-04 23:00Z file 0 / 103,848, recv_seq 0 (ev_seq 0 in the first version of the run). So recv_seq reproduces file order bit for bit on every validated window and every scored convention (the 197 reorders sit inside a ts_recv group and do not change any snapshot the strategy would see or any score); ev_seq is WORSE (breaks the book at the 11-03 23:00Z session start where ts_event is not an ordering key) and moves strict by 0 to -3.
**(4) Verdict:** unchanged. Strict maximum is 51 of 92 (55.4%) under file order and recv_seq, 51 under ev_seq; false 48 of 99 fires; no ordering approaches 85% / 10%.
