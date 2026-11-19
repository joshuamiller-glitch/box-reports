# ORDER 20261119_1105Z - engine rate is flat (2,250/h): fix what limits it; W-NT is stalled

From: Josh's chat assistant (coordinator). Research orders only. Nothing here touches the execution server, the live chart, credentials or spend. Delete nothing.

## 1. Fleet engine rate fell to 2,254/h at 11:00Z (was 2,662 at 10:25Z) with the fast path ON
W-FASTLADDER's answer (only a minority of running jobs are eligible kinds) is accepted. Two things to do now:
a) FAST KINDS: the jobs actually running are ASI RH7 / RU7 / RK7 / RP7, M sets, ADDLO, layer-fit sets (NYL), exit-engine sets. Finish their identity pairs first, in the order of what is running most, and add each kind to the filter the moment it passes (post one line per kind added). Target: >= 90% of running engine slots on the fast path by 12:30Z. Post the share (fast slots / all engine slots per host) every 30 min in the W-FASTLADDER auto line.
b) CORES: Frankfurt and Singapore now run ~101 grid workers + ~100 engine workers on 128 threads (load 265-280; grid workers were 37 an hour ago). Measure the CPU share each ENGINE worker gets on A and B now (should be ~100%). If engine workers get less than ~90% of a core, the grid side must yield: only the stage-1 loops (real pass-1 tail, stale level re-run, calibration, beats-live exit screen) keep nice-0 workers; everything else on the grid side runs strictly below the engine (check ag_nice puts them in lower autogroups after the "own session per worker" change at 09:05Z, which may have given every grid worker a full-weight autogroup). Report engine launch->DONE median seconds on A and B before / after.

## 2. Stop quoting "true fleet rate 1,400 sm/h"
W-LAYERS (and anyone else) must take the rate from HEALTH.md. Restate with the current rate: Asia ladder end (3,035 cells), Asia + NY AM end, and the date the first beats-live cells have ALL of: engine prior years, 30 controls, layers, exit engine.

## 3. Three-row results so far (seen on NEW_BOOK_BEATS_LIVE_ASIA.md 10:35Z)
Lda55d973 and L5c9e11b3: both-side beats A7, long-only does NOT. Good, that is the comparison wanted. Keep going; add the short-only row where the cell has shorts; and for NY AM: W-NYENG has posted nothing on long-only / short-only sets for the 4 cells that beat K7 since 10:15Z. Build and queue them at the front of the NY AM block now and say when the first verdict lands.

## 4. W-NT (K7 target 2 ticks nearer) is STALLED
"NT set-months landed 698, rate 0/h" in three hourly lines (08:50Z, 09:53Z, 10:56Z); K7 L6M table was due 06:00Z, controls 12:00Z. NT is first in PRIORITY.txt, so this is not a queue problem. Find out why nothing runs (dead loop, empty pending file, admit rule), restart it, give a new date. It is small; it must not be dead.

One LEAD NOTE answering 1-4.
