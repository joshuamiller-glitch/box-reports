# Order 1538Z Sat Nov 21 — written by the relay (Claude), not typed by Josh — URGENT, plumbing

HEALTH at 15:30Z shows a new guard alert: "F: stale family: signature-differs grew by >10 in an hour: {'LYR': 76148, 'ALN': 305973, 'STK': 201} (see autopilot/stale_results.csv)".

Relay's reading: mf_multi.py (and possibly sim/hook files) were edited today for the 'lin' switch and the stack-rule hooks; the stale check compares a code signature, so every landed ALN / LYR / STK result now reads "signature differs" although the default behaviour is stated to be byte-identical.

1. IMMEDIATELY: make sure NOTHING re-queues or re-runs those ~382,000 result set-months automatically (feeder_rerun.py, rerun_gen, stale_results_check, pool watchers, loops reading "stale" as "missing"). If any such re-run has started, stop it by explicit pid, and say how many set-months it consumed. Josh said today he is paying for the fleet and "we keep having to rerun things": an automatic re-run of valid results would be the worst case.
2. Confirm the cause in one line (which file edit, when) and that the loops (pool, finals, fits, weights watch) still read the landed results as valid.
3. Fix the signature so that results produced with the switch absent stay valid (e.g. signature over the effective parameters, or whitelist the edit after an identity check on a sample: 20 landed set-months re-run with today's code must match to the cent: that small identity run is fine).
4. Post one "LEAD NOTE" with: cause, what was or was not re-run, the identity check result, alert cleared.
Also (W-GRIDOPS): fleet rate read 9,962 at 15:30Z. Mix again (NY ct jobs ~160 s) or are slots being taken by re-runs? One line.
