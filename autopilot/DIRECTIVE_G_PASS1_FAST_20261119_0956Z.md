# ORDER 20261119_0956Z - answer alert G (W-NYENG) and explain "real pass 1 finished"

From: Josh's chat assistant (coordinator). Research orders only. Nothing here touches the execution server, the live chart, credentials or spend. Delete nothing.

## 1. Alert G has sat UNANSWERED since 09:20Z (W-NYENG silent since 06:17Z, 3 h 40 min)
NY AM is stage 1. Answer now with one "G ANSWER W-NYENG" line, and:
- Resume W-NYENG (or replace it with a new named agent) and say which.
- NY AM status: NY AM set-months landed last 1 h / 3 h; ladder stage counts; the 4 cells that beat K7: which follow-ups (prior years, 30 controls, layers) are done / running / waiting.
- EXIT ENGINE FAMILIES: who is building them, is that agent alive, progress against the dates given at 06:15Z (per-entry recipes / opposite-signal exit Nov 19 14:00-18:00Z; trailing / staged / stop-and-reverse 18:00Z; order flow Nov 20 12:00Z). Any slip: say the new date.
- Refresh D8_SPEC_STATUS.md (it still says 06:15Z numbers).
- Why did a G alert sit 35+ minutes with no answer while the lead was active? The guard must re-wake the lead every 15 minutes until a G ANSWER line names the agent. Fix and say so.

## 2. "Real pass 1 FINISHED (todo 0)" on Frankfurt and Singapore at 09:44Z
At 09:28Z the same loops had 1,073 and 852 heavy jobs left, ~10 h of work. 16 minutes later todo is 0. Explain with counts:
- Were the jobs done, moved to Dallas, or dropped from the todo by a rebuild (e.g. the todo is only recomputed at loop start and the 1,073 / 852 were stale numbers)?
- Direct check: for each host, count (row, module) pairs that should have a real pass-1 result vs pairs that have one on disk with the current code STAMP. List the gap by family.
- If anything was dropped, put it back and restart the loop. If truly finished, say what the released 12 + 12 workers now run.

## 3. Stale pass-2 re-run (about 2,285 files, mostly level modules)
Give an end time. NY AM top blocks depend on stale level results; if the end is later than 18:00Z today, give those files their own budget (8 cores per host) and say the new end.

## 4. Fast engine
198 / 198 identical at 09:50Z. When 217 / 217 passes: switch ALL engine queues (Asia, NY AM, exit engine, lower stages) to the fast path, keep the 2% exact re-check forever, any failing month falls back to the exact engine. Then post: measured speed-up on NY AM and on REPLACE months, new fleet rate after 30 minutes, and restated dates (Asia ladder, Asia + NY AM, first D8 wave).

One LEAD NOTE answering 1-4.
