# ORDER 20261119_1534Z - fast share is 0-2%; first looks are being crowded out; exit-engine dollars used the wrong driver

From: Josh's chat assistant (coordinator). Research orders only. Nothing here touches the execution server, the live chart, credentials or spend. Delete nothing.

## 1. Fast share 2% at 15:20Z (Dallas 0/26, Frankfurt 0/102, Singapore 0/102)
Every time the queue front changes to a new set name the fleet falls back to the slow path, and per-kind identity (3 pairs, ~25 min, one book letter at a time) cannot keep up: RP7CT / RM7CT / RH7CT were asked for at 14:58Z and are still not in the file; now it is NYL xP7 / xM7 / xH7 layer-fit sets.
Decision: add kinds by FAMILY TEMPLATE, not by name. A template = set family with the live-book letter, the control shift and the layer variant number as wildcards (e.g. NYE_L<h>_R<book>CT<n><m|p>; NYL_<id>x<book>_<layer><n>; ASI_<L|M><h>_R<book>CT...). A template goes into FAST_KINDS when >= 6 exact-vs-fast pairs are identical across at least TWO different books and two variants, 0 failures. The 2% exact re-check forever and the launcher guard stay as the safety net; any mismatch switches the template off. Do the templates for everything now running or queued in the next 12 hours (list them), most slots first. Target >= 90% fast by 16:30Z. Post the share per host in HEALTH (already there: good).

## 2. First looks must not be crowded out
Josh wants the whole of both ladders finished. In the last hour Asia landed 916 set-months and most slots ran layer-fit and control sets for the same one or two NY AM cells against other books (xP7 152 jobs, xM7, RP7CT / RM7CT / RH7CT).
Rule from now: (a) follow-ups (controls, layers, exit runs) run only for rows that pass the STRICT recent-months test + rule B + persistence >= 0.58 (not the looser "yes" rows); (b) all follow-ups together get at most 30% of engine slots; first looks (Asia 59% / NY AM 41%) get at least 70%; (c) inside the 30%: K7 / A7 slot rows first, other-slot rows of the same cell after. Apply in QUEUES / PRIORITY / the dispatchers (the remote dispatchers ignore tag quotas: enforce it there, e.g. interleave files by ratio as ny_mix does). Post first-look set-months per hour for Asia and NY AM at 16:00Z and 16:30Z.

## 3. Exit-engine dollar numbers (W-COMBO finding 15:20Z)
The local runner pattern (tp_launch.py state_sizer_ijk.py jbjobs) does not reproduce the JL3 stack (618 trades / P7 $47.4k vs production driver 631 / $62.1k on 202605). So the 14:07Z exit result for the NY AM cell (fixed bracket vs bricks recipe: ulcer 9,342 vs 9,953 etc.) compares rows from different drivers. Mark it NOT VALID for dollars on the page now. Re-run every exit-engine REPLACE row through the production driver (jn05_run2 via the dispatchers), confirm a plain JL3 month reproduces the landed JL3 exactly through that path first, then republish. Also check which OTHER published numbers came from the jbjobs pattern (combination dry runs, W-FASTLADDER timing / identity pairs, layer identity sets) and say so. Find out WHY jbjobs differs from jn05_run2 (which is right vs the live strategy: the identity vs live was established on which driver?).

## 4. NY AM cell L01811caa also passes the strict test as a replacement for P7 and M7 (not only K7). Good: that is what the combination step is for (a cell fills one slot). Show on the NY AM page one row per slot option with all 8 strict numbers, rule B colours and the 43-month engine persistence.

One LEAD NOTE answering 1-4.
