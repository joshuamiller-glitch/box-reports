# FASTR_VALIDATION - fast replay of one new book under its own layers vs the exact engine (W-FASTR, order 1840Z item 1d)

generated 2026-11-18 19:06 UTC. Research only. The replay SCREENS layer settings of the BOOK; every verdict still comes from the exact engine.

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
| CUT40 | 2 | 147 | 146/147 (99.3%) | 77/77 | 98% | 441.9 | 423.4 | -4.2% | +0.15 / 1.09 |
| CUT80 | 1 | 42 | 42/42 (100.0%) | 9/9 | 100% | 1081.2 | 1084.9 | +0.3% | +0.09 / 1.58 |
| NFT | 1 | 79 | 79/79 (100.0%) | 44/44 | 100% | 613.2 | 610.9 | -0.4% | -0.03 / 1.04 |
| BACK0 | 3 | 159 | 158/159 (99.4%) | 55/55 | 99% | 535.9 | 537.3 | +0.3% | -0.01 / 1.41 |
| TAKE90 | 3 | 109 | 109/109 (100.0%) | 34/34 | 100% | 575.0 | 552.3 | -3.9% | -0.21 / 1.50 |
| TAKE70 | 3 | 128 | 128/128 (100.0%) | 55/55 | 100% | 1336.8 | 1333.1 | -0.3% | -0.03 / 1.43 |
| LOCK60 | 3 | 136 | 136/136 (100.0%) | 26/26 | 100% | 731.5 | 716.5 | -2.0% | -0.11 / 1.63 |
| LOCK2 | 3 | 158 | 158/158 (100.0%) | 58/58 | 100% | 421.8 | 407.8 | -3.3% | -0.09 / 1.65 |
| DCAP | 3 | 106 | 106/106 (100.0%) | 2/2 | 98% | 1093.5 | 1075.3 | -1.7% | -0.17 / 1.66 |
| COMBO | 3 | 150 | 150/150 (100.0%) | 99/99 | 99% | 434.9 | 426.2 | -2.0% | -0.06 / 1.68 |

## 3. XA3 + one layer (2026-09, 2026-10 as engine sets land)
pending

## 4. OWN-BOOK ranking: does the replay rank settings like the engine?
```
   set  months  eng_mean  rep_mean  eng_ulcer  rep_ulcer  eng_worst  rep_worst  eng_maxdd  rep_maxdd  daily_corr  dollars_eng  dollars_rep
 CUT40       2     902.9     861.7     6785.1     6590.9    -5239.2    -5084.2   -10889.1   -10449.1         1.0       8126.5       7755.5
 CUT80       2    1980.2    1989.1     4714.2     4629.3    -2046.6    -2016.6   -10279.9   -10214.9         1.0      17821.6      17901.6
   NFT       1    2376.2    2367.1     2914.0     2927.8    -2929.9    -2945.3    -6276.2    -6281.6         1.0      11881.1      11835.5
 BACK0       3     765.2     767.4    10201.0    10219.6    -4832.7    -4882.9   -18860.8   -18822.8         1.0       9947.9       9975.6
TAKE90       3     844.0     809.1     5840.4     5978.0    -2817.8    -2853.8   -11943.8   -12165.6         1.0      10972.4      10518.2
TAKE70       3    2008.9    2003.2     3749.6     3698.2    -3593.6    -3599.2   -10823.1   -10719.3         1.0      26115.5      26041.5
LOCK60       3    1074.8    1051.7     4857.5     4958.7    -4367.1    -4428.1    -9815.6   -10108.5         1.0      13971.8      13672.0
 LOCK2       3     590.0     568.5     7754.0     7917.8    -4652.0    -4493.0   -14685.0   -14828.0         1.0       7670.3       7391.1
  DCAP       3    1642.8    1608.7     3999.0     4055.1    -2528.6    -2694.3   -11598.4   -11669.8         1.0      21357.0      20912.8
 COMBO       3     613.3     599.8    10001.2    10027.0    -4449.3    -4566.5   -20446.1   -20381.1         1.0       7972.5       7797.5
mean   own-book Spearman over 7 full sets: 1.00 | median relative error 2.1%
ulcer  own-book Spearman over 7 full sets: 1.00 | median relative error 1.4%
worst  own-book Spearman over 7 full sets: 0.96 | median relative error 1.4%
maxdd  own-book Spearman over 7 full sets: 1.00 | median relative error 1.0%
overall own-book $: engine 135837 replay 133801 (-1.5%); daily P&L correlation range 0.998..1.000
```

Stack-level deltas (stack ulcer / worst week with the other books) are NOT reliable from the replay: predicted vs engine ulcer Spearman about 0.5. Cause: the new book's closes and P&L change the other books through the day-state gate and caps, which the replay cannot re-simulate. So the replay ranks the BOOK's own layer settings; the stack effect of the top settings comes from the exact engine.

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
