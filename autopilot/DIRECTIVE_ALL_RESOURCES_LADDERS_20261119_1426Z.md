# ORDER 20261119_1426Z - Josh: all resources on finishing the Asia + NY AM ladders

From: Josh's chat assistant (coordinator). Research orders only. Nothing here touches the execution server, the live chart, credentials or spend. Delete nothing.

Josh (14:23Z): "all resources ahead". No side studies; everything goes to finishing stage 1 (Asia + NY AM, REPLACE only) and the combination step.

1. CPU for the engine. The cap test showed A / B saturate at ~100 engine slots because ~40 nice-0 search workers per host share the CPU. Decision: keep ONLY the calibration deeper-rung runners at nice 0 (12 per host on Frankfurt / Singapore; calibration is the judge for stage 1). Move to low priority (below the engine, single low-weight group) or stop: the heavy event-bar / footprint row loops (the 8 orphan heavy rows, vfpL tail), the null re-run loops, and every London / NY PM search or screen job. Dallas the same: engine first. Then re-measure: engine CPU per busy process, slots, set-months/h per host before / after 30 min. If engine processes then have headroom, step the caps up (cap_steps) until rate stops rising.

2. Fleet rate fell to 2,574/h at 14:10Z during the queue rebuild. Confirm every host is back at its cap with no idle slots (dispatchers not stalling on parked or missing lines, file pushes healthy) and post the rate at 14:45Z and 15:15Z.

3. Compiled engine (W-COMPILED) is the main speed lever: it keeps its builder and whatever cores its identity runs need. Post the plan, the expected total factor (per-print machinery + hook chain) and the date it can switch on.

4. Nothing new is to be started that is not stage 1: no extra studies, no London / NY PM engine lines ahead of stage 1 (they stay queued behind), ORB / range-use / near-target refresh crons to low priority or paused (keep their pages; do not delete).

5. Still owed from order 1337Z / 1407Z: the single REPLACE-only "stage 1 complete" date (with and without the compiled engine), the arithmetic for one or two more 128-thread servers, the 98 Asia cells that were never queued (are they queued now), and autopilot/D8_COMBINATION_PLAN.md.

One LEAD NOTE answering 1-5.
