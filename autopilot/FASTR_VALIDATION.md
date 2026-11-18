# FASTR_VALIDATION - fast replay of one new book under its own layers vs the exact engine (W-FASTR, order 1840Z item 1d)

generated 2026-11-18 19:45 UTC. Research only. The replay SCREENS layer settings of the BOOK; every verdict still comes from the exact engine.

## What it is
A first-order walk on the 1-second state tape (`/mnt/l2/l2vast/_th_state/days`: mid, bid/ask, print first/last/high/low per second) plus the print tape for the take rule. Input = the engine's own entries of the book (entry time and price); the replay re-derives EXIT and LAYER behaviour: bracket stop/target, UWTime exit, loss cuts (flat, no-follow-through, back-to-entry, scratch, recovery-lock), profit take, profit lock (1-2 steps), own day caps, entry no-trade times, stack-relative DAY-DONE for the new book, and the engine-native book give-back lock. Code `code/th_fastr` (fr_data, fr_core numba kernels, fr_validate, fr_screen, fr_grid, fr_rank_own, fr_page).

**Not replayed: ENTRY prices.** Engine entries are not first-print fills (the engine enters near the signal-time price, 1-2 points off the first print after +1 s), so a tape-only replay cannot rebuild them; the replay starts from the engine entry. Entries are fixed to the ADD set: layers that would change WHICH events enter (via the stack day-state) are not modelled.

## 1. Baseline (the ADD set itself, no own layer), all history
| book | months | trades | exit-reason match | points engine | points replay |
|---|---|---|---|---|---|
| WP10 (NY PM vol_350 money flow) | 43 | 1,920 | 99.5% | 4,114 | 3,936 (-4.3%) |
| XA3 (NY AM VWAP retest tick_5000) | 24 | 1,380 | 98.3% | 7,634 | 7,235 (-5.2%) |

Mismatches: engine StackCut exits (5 on WP10; a stack-level cut hitting the book) and day-state differences (XA3: 15 false DayHalt).

## 2. WP10 + one layer, trade for trade (last months 2026-08..10 as engine sets land)
| set | months | trades | reason_match | layer_exits | within_1s | points_engine | points_replay | points_gap | exit_px_err |
|---|---|---|---|---|---|---|---|---|---|
| CUT40 | 3 | 201 | 200/201 (99.5%) | 100/100 | 98% | 880.4 | 852.8 | -3.1% | +0.07 / 1.10 |
| CUT80 | 3 | 128 | 128/128 (100.0%) | 31/31 | 99% | 1684.3 | 1676.6 | -0.5% | -0.06 / 1.31 |
| NFT | 3 | 232 | 231/232 (99.6%) | 123/123 | 99% | 1215.6 | 1208.3 | -0.6% | -0.10 / 0.93 |
| BACK0 | 3 | 159 | 158/159 (99.4%) | 55/55 | 99% | 535.9 | 537.3 | +0.3% | -0.01 / 1.41 |
| TAKE90 | 3 | 109 | 109/109 (100.0%) | 34/34 | 100% | 575.0 | 552.3 | -3.9% | -0.21 / 1.50 |
| TAKE70 | 3 | 128 | 128/128 (100.0%) | 55/55 | 100% | 1336.8 | 1333.1 | -0.3% | -0.03 / 1.43 |
| LOCK60 | 3 | 136 | 136/136 (100.0%) | 26/26 | 100% | 731.5 | 716.5 | -2.0% | -0.11 / 1.63 |
| LOCK2 | 3 | 158 | 158/158 (100.0%) | 58/58 | 100% | 421.8 | 407.8 | -3.3% | -0.09 / 1.65 |
| DCAP | 3 | 106 | 106/106 (100.0%) | 2/2 | 98% | 1093.5 | 1075.3 | -1.7% | -0.17 / 1.66 |
| COMBO | 3 | 150 | 150/150 (100.0%) | 99/99 | 99% | 434.9 | 426.2 | -2.0% | -0.06 / 1.68 |

## 3. XA3 + one layer (2026-09, 2026-10 as engine sets land)
| set | months | trades | reason_match | layer_exits | within_1s | points_engine | points_replay | points_gap | exit_px_err |
|---|---|---|---|---|---|---|---|---|---|
| CUT40 | 2 | 120 | 120/120 (100.0%) | 46/46 | 99% | 1812.2 | 1817.0 | +0.3% | +0.04 / 0.35 |
| TAKE90 | 2 | 101 | 100/101 (99.0%) | 21/21 | 97% | 1833.2 | 1835.5 | +0.1% | +0.05 / 1.38 |
| TAKE70 | 2 | 115 | 113/115 (98.3%) | 52/52 | 100% | 1561.5 | 1658.2 | +6.2% | +0.03 / 0.97 |
| LOCK60 | 2 | 118 | 118/118 (100.0%) | 33/33 | 98% | 1117.8 | 1156.5 | +3.5% | +0.33 / 2.19 |
| LOCK2 | 2 | 125 | 122/125 (97.6%) | 56/58 | 99% | 1627.5 | 1655.1 | +1.7% | +0.22 / 2.15 |
| DCAP | 2 | 97 | 97/97 (100.0%) | 0/0 | 98% | 1763.5 | 1771.2 | +0.4% | +0.08 / 1.19 |
| COMBO | 2 | 118 | 117/118 (99.2%) | 47/47 | 97% | 1177.5 | 1212.5 | +3.0% | +0.32 / 2.28 |

## 4. OWN-BOOK ranking: does the replay rank settings like the engine?
```
   set  months  eng_mean  rep_mean  eng_ulcer  rep_ulcer  eng_worst  rep_worst  eng_maxdd  rep_maxdd  daily_corr  dollars_eng  dollars_rep
 CUT40       3    1279.6    1237.2     8006.2     8611.8    -5239.2    -5084.2   -13828.3   -14459.3         1.0      16634.7      16083.7
 CUT80       3    2543.6    2531.7     4088.1     4055.6    -2046.6    -2016.6   -10279.9   -10214.9         1.0      33067.0      32912.0
   NFT       3    1783.8    1772.5     3341.9     3323.2    -3216.4    -3261.4    -8403.7    -8374.1         1.0      23189.1      23042.1
 BACK0       3     765.2     767.4    10201.0    10219.6    -4832.7    -4882.9   -18860.8   -18822.8         1.0       9947.9       9975.6
TAKE90       3     844.0     809.1     5840.4     5978.0    -2817.8    -2853.8   -11943.8   -12165.6         1.0      10972.4      10518.2
TAKE70       3    2008.9    2003.2     3749.6     3698.2    -3593.6    -3599.2   -10823.1   -10719.3         1.0      26115.5      26041.5
LOCK60       3    1074.8    1051.7     4857.5     4958.7    -4367.1    -4428.1    -9815.6   -10108.5         1.0      13971.8      13672.0
 LOCK2       3     590.0     568.5     7754.0     7917.8    -4652.0    -4493.0   -14685.0   -14828.0         1.0       7670.3       7391.1
  DCAP       3    1642.8    1608.7     3999.0     4055.1    -2528.6    -2694.3   -11598.4   -11669.8         1.0      21357.0      20912.8
 COMBO       3     613.3     599.8    10001.2    10027.0    -4449.3    -4566.5   -20446.1   -20381.1         1.0       7972.5       7797.5
mean   own-book Spearman over 10 full sets: 1.00 | median relative error 2.1%
ulcer  own-book Spearman over 10 full sets: 1.00 | median relative error 1.4%
worst  own-book Spearman over 10 full sets: 0.99 | median relative error 1.4%
maxdd  own-book Spearman over 10 full sets: 1.00 | median relative error 0.8%
overall own-book $: engine 170898 replay 168347 (-1.5%); daily P&L correlation range 0.999..1.000
```

Stack-level deltas (stack ulcer / worst week with the other books) are NOT reliable from the replay: predicted vs engine ulcer Spearman about 0.5. Cause: the new book's closes and P&L change the other books through the day-state gate and caps, which the replay cannot re-simulate. So the replay ranks the BOOK's own layer settings; the stack effect of the top settings comes from the exact engine.

## 4b. ENTRY-FILTER layers (no-trade times, post-stop blackout, DAY-DONE setting): engine-blocked signals vs replay-skipped
Engine = the layered engine set vs the ADD set on the same month (signals the layer removed). A filter also changes later entries (one position at a time), which an engine-entered replay cannot add.

| entry filter | month | engine blocked vs ADD | replay skips | both | only engine | only replay | false skips on layered engine trades |
|---|---|---|---|---|---|---|---|
| no-trade 13:30-14:00 ET | 202609 | 0 | 0 | 0 | 0 | 0 | 0 |
| no-trade 13:30-14:00 ET | 202610 | 4 | 2 | 2 | 2 | 0 | 0 |
| same-side blackout 30 min after stop/cut | 202608 | 4 | 3 | 3 | 1 | 0 | 0 |
| same-side blackout 30 min after stop/cut | 202609 | 13 | 7 | 7 | 6 | 0 | 0 |
| same-side blackout 30 min after stop/cut | 202610 | 12 | 5 | 5 | 7 | 0 | 0 |
| DAY-DONE 10 closes / -1200 (stack-relative) | 202608 | 11 | 1 | 1 | 10 | 0 | 0 |
| DAY-DONE 10 closes / -1200 (stack-relative) | 202609 | 17 | 3 | 3 | 14 | 0 | 0 |
| DAY-DONE 10 closes / -1200 (stack-relative) | 202610 | 4 | 0 | 0 | 4 | 0 | 0 |

Reading: the no-trade window matches (no false skips). The blackout needs the same-side-after-stop-or-cut rule and then has no false skips but misses most engine blocks; the stack-relative DAY-DONE setting misses most (the engine rule counts all books incl. the new one and re-gates the live books). Entry filters of the stack-interplay kind are therefore NOT validated and are shown as NOT validated in FASTR_LAYER_SCREEN.md.

## 5. Engine semantics learned (these differ from the hook docstrings)
- Target: fills at the level on the first print touching it (the engine fill is the level). Stop: triggers exactly at entry -/+ stop_pts (print touch), fills 1.24 pt better than the level on average. UWTime: exit_ts + 1 s at the opposite quote.
- Profit take (ev_profit): evaluated at print level, at most once per second of print flow (THR_MODE gap), on the evaluating print; fires when unrealised >= pct x target distance and the favourable extreme is >= secs old; market fill about 1.5 s later at the opposite quote. Evaluating the first/last print of the second misses cases.
- Profit lock: armed at the closed-second mid (pct of target), level tighten-only, exits on the first print touching it (market, opposite quote).
- Loss cuts (ec_hooks): decision at the close of second r on the mid, exit at row r+1 mid -/+ 0.8.
- Day caps (book): do NOT exit an open trade on unrealised P&L; after a closed trade takes the day past a cap, later entries are blocked, but a signal already in flight enters and exits at once (exit name DayHalt, about +8 pts).
- Book give-back lock (native, inherited): day (closed + open) peak >= 2R and day <= 0.5 peak -> exit and halt the book; reproduced 6/6 on WP10 L6M.

## 6. Limits
- Only engine-entered trades; stack-level effects not modelled; entry fills not rebuilt; StackCut not modelled; first-order second-resolution decisions (a layer decision inside one second can differ by one row).
- Ranking validity shown for WP10 on 3 months; XA3 on 2 months.
