## 6. GAPMAP STATUS

7,280 cells = 13 drivers x 7 horizons x 8 use-modes x 10 instruments (driver D00 = pair-internal state). Source: GAPMAP.md (hourly merge; the rebuild crash on the MONITOR verdict was fixed 2026-10-17).

| status | cells |
|---|---|
| TESTED | 1,542 (NO 1,032; LEAD 488; INSURANCE 3; FOUND-PENDING recorded at family level, not per cell) |
| VOID | 3 (tested only on the retired baseline / legacy selection) |
| UNTESTED | 532 (52 claimed by a running worker) |
| NOT APPLICABLE | 5,187 |

Untested by data class: on disk 48, cheap to buy 178, mbp-10 (L2) 80, options trades 36, other 189 (QQQ/VX curve/calendar/COT detail or engine-gated).

Coverage by driver (applicable cells only; verdicts FOUND/PENDING/LEAD/INSURANCE/NO):

| driver | applicable | tested | void | untested | tested % | verdicts (FOUND/PENDING/LEAD/INS/NO) |
|---|---|---|---|---|---|---|
| D00 pair-internal state | 163 | 157 | 3 | 2 | 96% | 0/0/26/2/129 |
| D01 order flow | 144 | 141 | 0 | 3 | 97% | 0/0/74/0/67 |
| D02 flow persistence | 144 | 122 | 0 | 18 | 84% | 0/0/48/0/74 |
| D03 dealer gamma / 0DTE | 163 | 46 | 0 | 117 | 28% | 0/0/12/0/34 |
| D04 cash basket / breadth | 101 | 20 | 0 | 81 | 19% | 0/0/0/0/20 |
| D05 liquidity / depth | 144 | 0 | 0 | 144 | 0% | 0/0/0/0/0 |
| D06 clock / calendar | 186 | 163 | 0 | 21 | 87% | 0/0/71/0/92 |
| D07 cross-asset | 195 | 172 | 0 | 20 | 88% | 0/0/60/0/112 |
| D08 volatility regime | 194 | 177 | 0 | 15 | 91% | 0/0/96/0/78 |
| D09 positioning / COT | 60 | 46 | 0 | 14 | 76% | 0/0/0/0/46 |
| D10 events | 207 | 161 | 0 | 44 | 77% | 0/0/51/0/110 |
| D11 price patterns / microstructure patterns | 197 | 173 | 0 | 22 | 87% | 0/0/24/1/148 |
| D12 ML on features | 195 | 164 | 0 | 31 | 84% | 0/0/26/0/122 |


**What each untested block needs.**
- D05 liquidity/depth (144 cells, 0% tested) and part of D01-D03: **L2 / mbp-10**. The ES job was delivered and reduced to per-second proxy features (raw deleted; report-only); the RTY job (GLBX-20261015-XDLHWMFQ3R) has only 2023-08..10 raw on disk and was last seen processing; the NQ job (GLBX-20261013-Y3PCQ4MKV3), the one that matters, has not landed. Pre-registered L2 families and the whipsaw-cure K-L2 start the hour NQ lands. Re-buying costs ~$2,025 and would exceed the cap.
- D03 dealer gamma / 0DTE (117 cells): options trades/definitions (36 untested cells on options data; 304 cells already tested showed IC <= 0.03; Rithmic has no OPRA feed, so not executable anyway).
- D04 cash basket / breadth (81 cells): QQQ/SPY constituent minute data on a split-adjusted basis (basket panel is raw prices; the audit found no exposure).
- D09 COT (14) and D10 events (44): calendar files (release times) and COT detail; partly "other".
- Pair-side NQ execution modes (M4-M8) that need sub-second cross-asset latency or a model frozen before 2023 (pair history starts 2023-02-10): structurally untestable at retail latency or with honest design.
- The 25 on-disk unclaimed cells left after the sweeper are QQQ/VX cells without data on disk.

**Running now (14:10Z).** The research workers have returned their batches and the machine is nearly idle (load ~0). Live processes: the NQ mbp-10 hourly state watcher, the GC fade newest-weeks watcher (every 6 h, waits for 8 complete weeks), the Q34 ES1 forward watcher (every 6 h), the K-L2 trigger (fires when NQ lands), the 12-hour portfolio-assembly daemon, the hourly GAPMAP merge, and the two report-drafting agents for this document. No new search is queued because the unclaimed on-disk cells are exhausted and further cell-counting only adds false discoveries.
