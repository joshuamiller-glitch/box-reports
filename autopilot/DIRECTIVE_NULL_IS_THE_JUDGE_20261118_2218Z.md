# ORDER 20261118_2218Z: after the R3 sanity check: the whole-search null is the judge; queues; real pass-1 rate

Research only. Nothing here touches the execution server, a live chart, credentials, spend or data deletion.

## 1. Luck test: what the sanity check changes (22:06Z LEAD NOTE accepted as read)
Per-cell p-values against unselected random entries are a SCREEN and a RANKING, not a calibrated pass rule.
The calibrated answer is the whole-search null: null draws run through the SAME ladder (R0 -> R1 -> R2 -> R3
stages, both SET 1 and SET 2 statistics), giving "how many null cells get as far as the real ones".
a. Make that comparison the pass rule per session: for each ladder depth / p threshold, real count vs mean null
   count = measured false-discovery rate. Report the threshold where measured FDR <= 10% (also 5%, 20%),
   separately on the p_L6M and p_ALL rankings. Josh picks between them with the measured rates in front of him.
b. Do not wait for all 5 draws: publish the comparison after draw 1 is complete for a session (label it
   "1 draw, coarse"), refine as draws 2-5 land. Say when draw 1 is complete per session at today's rates.
c. Order of null work: finish draws 1-2 for the sessions in clock order (Asia, London, NY AM, NY PM) before
   starting 3-5. If moving share from null draws 3-5 to draws 1-2 gets a first calibrated table sooner, do it.
d. Meanwhile the engine does NOT wait: it takes cells best-first by the screen (stage B/C p_L6M, then p_ALL),
   labelled "screen rank, not yet calibrated". No cap. Finish the pseudo-real extension and append it.
e. The 13 void Asia cells: grid re-score, then back into R3.

## 2. Queues (night rule: >= 12 h of work per machine with no decision, before 02:00Z)
HEALTH.md 22:15Z: engine queue 3.3 h (flat at ~4 h for an hour), Dallas grid queue 3.8 h.
Refill both now to >= 12 h and say what went in. Candidates: stage-B/C screen leaders per session (item 1d),
London / Asia lead sets, layer programmes, near-target controls. Dallas: more grid rows or null share.

## 3. Real pass 1 rate
W-GRIDOPS 22:05Z: pass 1 4,403 jobs/h but only 139 REAL (21:05Z: 1,584 real). Why did the real rate fall
11x? How many real pass-1 jobs are left, and is ~Nov 19 13:30Z still the end of real pass 1? If the filler
or the R3 oversubscription on A / B (load 300+ on 128 threads) is starving real work, fix the priorities:
real pass 1 > R3 stages > pass 2 + exits > null 1-2 > null 3-5.

## 4. Dallas error stubs
176 -> 99 -> 51 -> 107 -> 135 per 30 min (box 1: 49). What are they (which jobs, which error), are they
retried, and is any result lost? Fix or explain in one LEAD NOTE.
