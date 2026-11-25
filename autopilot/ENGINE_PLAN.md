# ENGINE_PLAN - fastest path through phases 2-4, no shortcuts (W-PLAN, order 1840Z), written 2026-11-18 18:45Z, refreshed hourly (rates + dated estimates at the bottom)

Plain words. Research only, no spend. "Set-month" = one engine run of one set (a stack variant) for one calendar month; it is the engine's unit of cost. Nothing here lowers a standard: 30 controls, the selection-corrected null, own fitted layers (jointly), prior years, exact-engine verdicts, identity on every machine and every new hook, clock order of decisions all stay. This page is about ORDER and PARALLELISM only. Numbers marked ASSUMED are not measured yet and are replaced by measurements as they arrive.

## 0. LADDER (orders 1932Z + 2042Z; supersedes the N = 3..50 sizing in section 2, which stays as the per-survivor cost model)
Sized on SURVIVOR_COUNTS.md (bare, 19:08Z): Asia 2,992 cells / 1,890 families; London 1,035 / 808; NY AM 9,504 / 4,556; NY PM 531 / 396 = 14,062 cells / 7,650 families. No top-N cap; a cell leaves only by FAILING a rung; engine capacity only sets the ORDER. Live numbers (rates, counts, hours, tables): section 11, refreshed hourly; the A/B hyper-thread factor and engine rates there replace the assumptions as they are measured. Fleet: current = box 1 + Dallas = 96 core-equivalents; pool = + A + B at ASSUMED 1.3 core-eq per physical core with SMT = 262.
Unit costs: R1 0.0091 core-h per pair (W-DAYMASK rate); R2 0.001-0.005 per cell; R3 per cell, measured on XA3 by W-SHORT: stage A (30 draws) 0.010 core-h, B (draws 31-200) 0.025, C (201-1,000) 0.105, D (1,001-10,000) 1.17; stage advance on EITHER p_L6M or p_ALL; R4 317 core-h per complete null draw; R5 0.045 core-h per engine set-month (160-180 s on Dallas/box 1; the 0.30 in the 1932Z order is the starved-A figure: its own 7.8 core-h per 30 controls implies 0.043); 30 date-shift controls 7.8 core-h per cell; layer programme 51 core-h per surviving book (29 with the validated fast replay).
Engine rate measured on A and B (30-min windows after dispatch start; includes per-month cache builds, not steady state): A 68-118 set-months/h, B 124-168 set-months/h, versus Dallas ~313 and box 1 ~450: the engine on A/B is improving but still far below the 1,300/h assumed per machine.

| rung | in -> out | core-h | hours, current fleet (96) | hours, pool (262) | > 48 h? |
|---|---|---|---|---|---|
| R0 bare (done) | 4.4M-4.8M cells per session -> 14,062 cells / 7,650 families | done | - | - | no |
| R1 own-stop | 14,062 -> unknown (arrays for ~1,700 pairs; grid re-running the rest); failers kept | <= 128 | 1.3 | 0.5 | no |
| R2 trust + look-ahead | R1 passers -> unknown | 14-70 | < 1 | < 1 | no |
| R3 stage A: 30 draws, every family-best (0.010 core-h per cell, measured on XA3) | 7,650 -> advance to B on EITHER p_L6M or p_ALL | 76 | 0.8 | 0.3 | no |
| R3 stage B: draws 31-200 (0.025 per cell) | 2,300-7,650 cells (ASSUMED 30-100%; on W-LONENG's 28 cells 27 qualified on whole history) | 57-191 | 0.6-2.0 | 0.2-0.7 | no |
| R3 stage C: draws 201-1,000 (0.105 per cell) | 230-2,300 cells (ASSUMED 3-30%) -> BH at q = 10% per session on p_L6M (SET 1) and p_ALL (SET 2) | 24-241 | 0.3-2.5 | 0.1-0.9 | no |
| R3 stage D: draws 1,001-10,000 (1.17 per cell) for cells at the minimum p of stage C | 76-380 cells (ASSUMED 1-5%) | 90-448 | 0.9-4.7 | 0.3-1.7 | no |
| R3 neighbours, same procedure after their best member (6,412 cells; family "isolated" if the best passes and all neighbours fail) | | 207-803 | 2.2-8.4 | 0.8-3.1 | no |
| R3 total (stages A-D, family-bests + neighbours) | TWO pass sets per session: SET 1 = inside BH on p_L6M, SET 2 = inside BH on p_ALL (whole history); counts at q 5/10/20% in SURVIVOR_COUNTS.md | 454-1,759 | 4.7-18 | 1.7-6.7 | no |
| R4 whole-search null, 5 complete draws, ~25% of A+B | all four sessions -> false-discovery ratio per session, best-pick comparison | 1,585 | 16.5 (whole current fleet) | 38 h at 25% of A+B (42 core-eq); 6 h on the whole pool | no (38 h) |
| R5 engine for the BH passers (+ layers) | P passers | 67.5 per passer (16.5 R5a-c + 51 layers) | see table | see table | when P > ~186 |

Engine hours for the BH passers (q = 10%, expected false passers = 0.1 x P); W-SHORT's stage B/C counts per session replace this table when they appear (they are not in SURVIVOR_COUNTS.md yet):
| passers P | expected false | core-h | hours on pool (262) | hours on current fleet (96) | extra A/B-class machines to finish in 48 h |
|---|---|---|---|---|---|
| 50 | 5 | 3,375 | 13 | 35 | none |
| 100 | 10 | 6,750 | 26 | 70 (> 48) | none |
| 200 | 20 | 13,500 | 52 (> 48) | 141 | 0.2 |
| 400 | 40 | 27,000 | 103 | 281 | 3.6 |
| 800 | 80 | 54,000 | 206 | 563 | 10 |
| 1,600 | 160 | 108,000 | 412 | 1,125 | 24 |
Break-even for the 48 h flag: P <= ~186 on the pool (~276 with the validated fast replay); P <= ~68 on the current fleet.

TWO PASS SETS (W-SHORT 2057Z): the engine plan is sized on SET 1 (p_L6M, the pick rule) with SET 2 (p_ALL, whole history) beside it; the union is the upper case. W-SHORT's cost per passer is 264 set-months (12 L6M + 72 prior years + 180 controls) = ~13 core-h; W-PLAN keeps the larger 16.5 core-h (prior years priced on every replace variant) + 51 layers. XA3 reference at 1,000 draws: p_L6M 0.092, p_ALL 0.0030, p_PRIOR 0.0020 (not inside BH on L6M alone).

MINIMUM p reachable and BH: p = (1 + hits) / (1 + draws): 30 draws -> 0.032, 200 -> 0.005, 1,000 -> 0.001, so a cell cannot pass on 30 draws alone. BH at q = 10% rejects the k-th smallest p only if p <= k x 0.10 / m (m = family-bests of the session). With 1,000 draws a session needs at least k >= 10 x m x 0.001 cells at the minimum p: Asia >= 19, London >= 8, NY AM >= 46, NY PM >= 4; a session with fewer such cells passes NOTHING at 1,000 draws even if its best cells are real, so the best few need stage D (10,000 draws, p_min 0.0001; BH floor m/1,000 cells at 0.0001). Stage D is now in the plan (1.17 core-h per cell).

HONEST LINES. (a) R4 as now ordered (5 draws) is 38 h at 25% of A+B: no longer above 48 h. (b) No screen rung R1-R4 exceeds 48 h on the pool. (c) The ENGINE exceeds 48 h of the pool when more than ~186 family-bests pass BH (4 sessions together); the pass counts are unknown until stage B/C results exist (W-SHORT). (d) If every family-best went through R5 (what the old R3 would have allowed), it is 126,226 core-h = 482 h (20 days) on the pool: not feasible, which is what the BH gate prevents.

DATED ESTIMATES, OLDER VERSION (written 2026-11-18 20:50Z; SUPERSEDED by the dated block at the end of section 11, written 2026-11-19 00:10Z; from SEARCH_STATUS.md 20:30Z: phase 1 real pass 1 ~17 h, pass 2 + exits ~49 h at the current 50% null split and ~28 h at the restored split (null ~25% of A+B); the 2042Z order restores the split):
| milestone | estimate | basis |
|---|---|---|
| phase 1 real pass 1 done | Nov 19 ~13:30Z | 17 h (SEARCH_STATUS 20:30Z) |
| phase 1 pass 2 + exits done | Nov 20 ~01:00Z (restored split, 28 h); Nov 20 ~22:00Z if the split is not restored (49 h) | SEARCH_STATUS |
| R3 end per session (stages A-C, neighbours after the best): Asia, London, NY PM | Nov 19 ~early afternoon after R1/R2 re-run (~20:00Z+); screen cost only 1.7-6.7 h of the pool but jobs run at nice 5 behind the engine and ahead of the null | W-SHORT queue; ASSUMED |
| R3 end NY AM (4,556 families) | Nov 19 ~afternoon-evening | same; largest session |
| R4 5 null draws (calibration) | Nov 20 ~11:00Z (38 h at 25% of A+B; W-GRIDOPS publishes its own ETA) | 1,585 core-h |
| engine for the BH passers (R5 + layers) | starts per session as soon as its R3 BH set exists (Nov 19 afternoon); at a 25% share before phase 1 ends, the whole pool after it | P unknown |
| D8 spec page (clock-order chain 4-8 h + 2 h after the last engine link) | P = 50: Nov 21 ~03:00Z; P = 100: Nov 21 ~16:00Z; P = 200: Nov 22 ~18:00Z; P = 400: Nov 24 ~21:00Z; P = 800: Nov 29 ~03:00Z; P = 1,600: ~Dec 7 | engine core-h at 67.5 per passer, pool 262 core-eq after Nov 20 12:00Z, 65 core-eq before; +-12 h |
D8 range today: Nov 21 (P <= 100) to Nov 22-24 (P = 200-400); the BH pass counts will move this; more machines shorten only the P >= 200 cases (table above).

## 1. What the machines can do (measured 18:40Z)

| machine | real threads | engine set-months/hour measured (DONE files, per clock hour) | workers then | per worker | engine-ready? |
|---|---|---|---|---|---|
| box 1 London | 32 | 609 (13h) 406 (14h) 614 (15h) 620 (16h) 426 (17h) 320 (18h, partial) | 11-26 (grid shares the box) | ~24/h | yes (identity 691 / 37,159.82, 637 / 41,239.76 passed) |
| server 2 Dallas (SMT off) | 64 | 547 (13h) 287 (14h) 499 (15h) 471 (16h) 288 (17h) 196 (18h, partial) | 24-28 (cap 28 then 14) | ~17/h | yes (same identity runs) |
| A Frankfurt | 128 (64 cores x 2) | none yet | 0 | ASSUMED ~13/h per worker (hyper-threads ~65% of a full core) | NO: engine data copy not started (W-S3); identity not run |
| B Singapore | 128 | none yet | 0 | ASSUMED same | NO |

- Engine worker memory: ~0.7-1.0 GB resident each (tp_launch RSS 0.74 GB box 1, 0.96 GB server 2) plus the shared per-month cache mapped from /mnt/l2/l2vast/_th_tp/cache (223 GB on box 1, same on server 2, ~2.5 GB per month). Memory limits only box 1 (floor 40 GB; free 38-54 GB while the grid shares it). On the 1.5 TB machines memory is not a limit.
- What the engine needs on A and B (ENGINE-READY recipe, none of it started): /mnt/l2/l2vast/_hist_replica 43 GB + _th_sz 14 GB + _newdata 0.5 GB + the code + the per-month engine cache (223 GB; copy it from server 2 with many parallel streams, or let each worker build it: 7 GB unpack + 2.5 GB per month, which costs ~minutes per month and is the slow way). Copy time ASSUMED 20-40 min for the 60 GB at the measured 127 MB/s (server 2 -> A, 8 streams) / 470 MB/s (box 1 -> A); +~30-60 min for the 223 GB cache; B is fed from A (86-156 MB/s). Then the identity check (2 set-months) before ANY result from that machine is used. Realistic engine-ready hour: A ~20:00Z, B ~20:30Z if W-S3 starts the engine copy now (not before the grid copy is done).
- Whole-fleet capacity if every machine did only engine work: ASSUMED ~1,000/h (box 1 + Dallas, measured at the current cap) now; ~4,500/h (box 1 560 + Dallas 1,100 + A ~1,400 + B ~1,400) once A and B are engine-ready. First measurement of A/B per-worker rate replaces the assumption (W-GRIDOPS measures jobs/hour at 64/96/120 workers once).

## 2. Count the work (set-months, engine only) for N survivors per session

Definitions. Per survivor: ADD at 1 base lot over the full history = 43 months (202304-202610); 30 date-shift engine controls on L6M = 30 x 6 = 180; REPLACE each live book of that session = R x 43 (NY AM R=3 plus keep-H7 mixed, NY PM R=1, London R=4, Asia R=5, per the live books earning in that session). Whole-session and mixed sets are shared across survivors (capped: best-2, best-3, mixed ~13 sets x 43 = 560 per session). The 30 same-bracket random-entry controls and the selection-corrected best-pick null (>= 20 draws of the same search) and the trust audit are SCREEN-level, on the grid (cost counted in section 4, not here). Phase 3a: per book 10 layers x 48 set-months (L6M fit grid) + joint <= 40 combos x 6 + prior years 37 months x (10 winning settings + joint); with the validated fast-replay screen (W-FASTR, if it validates) only the top 2-3 settings per layer reach the engine (L6M part falls from 720 to ~230). Books reaching 3a = about half the survivors. 3b (replace/add/mixed again with layered books) ~170 per book. 3c joint across sessions ~800 (30 stack controls x 6 + prior years + ~10 stack candidates). Clock-order re-runs = later-session finalists re-run against the rebuilt day-state after each earlier session is final.

N is NOT a limit (order 1845Z): there is no top-N cut anywhere in phases 1-3; every cell that passes the rule is tested, capacity only sets the ORDER (best first). N below is only the workload estimate: passing cells per session = 3, 6, 10, 20 or 50.

| item (set-months) | N=3 | N=6 | N=10 | N=20 | N=50 |
|---|---|---|---|---|---|
| phase 2 per survivor (ADD 43 + 30 controls 180 + replace; avg 363 over the 4 sessions) x 4 sessions | 4,400 | 8,700 | 14,500 | 29,000 | 72,600 |
| whole-session + mixed (shared, capped, 4 sessions) | 2,200 | 2,200 | 2,200 | 2,200 | 2,200 |
| phase 3a layers, exact engine only (books reaching 3a = N/2 per session x 4; 1,133 per book) | 6,800 | 13,600 | 22,700 | 45,300 | 113,300 |
| phase 3a with the fast-replay screen (only if W-FASTR validates; 640 per book) | 3,800 | 7,700 | 12,800 | 25,600 | 64,000 |
| 3b stack questions with layered books (170 per book) | 1,000 | 2,000 | 3,400 | 6,800 | 17,000 |
| 3c joint across sessions | 800 | 800 | 800 | 800 | 800 |
| clock-order re-runs (1,020 per book-per-session) | 1,500 | 3,100 | 5,100 | 10,200 | 25,500 |
| TOTAL engine, no screen | 16,700 | 30,400 | 48,700 | 94,300 | 231,400 |
| TOTAL engine, with validated screen | 13,700 | 24,500 | 38,800 | 74,600 | 182,100 |

Hours = total / fleet rate. Fleet rates: 2 machines (box 1 + Dallas, measured) 1,000/h; 4 machines (A and B engine-ready, ASSUMED) 4,500/h; 5 machines (one more 128-thread server, ASSUMED +1,400/h); the pool is shared with the grid, so these are engine-only hours.

| hours (no screen / with screen) | N=3 | N=6 | N=10 | N=20 | N=50 |
|---|---|---|---|---|---|
| 2 machines (1,000/h) | 17 / 14 | 30 / 25 | 49 / 39 | 94 / 75 | 231 / 182 |
| 4 machines (4,500/h) | 3.7 / 3.0 | 6.8 / 5.4 | 10.8 / 8.6 | 21 / 17 | 51 / 40 |
| 5 machines (5,900/h) | 2.8 / 2.3 | 5.2 / 4.2 | 8.3 / 6.6 | 16 / 13 | 39 / 31 |
| machines needed (128-thread class) to finish the engine in 24 h, no screen / screen | 2 / 2 | 2 / 2 | 3 / 3 | 4 / 4 | 8 / 7 |
| machines needed to finish in 12 h, no screen / screen | 2 / 2 | 3 / 3 | 4 / 4 | 6 / 5 | 14 / 11 |

(Machine counts: needed rate / 1,400 per added 128-thread machine, plus box 1 + Dallas worth ~1,000/h; ASSUMED rates; the first measured A/B per-worker rate replaces them. Price per machine-hour of the rented servers is not known to W-PLAN: Josh knows it. Phase 1 (grid, ~3,250 core-hours left, ~12 h of the whole pool) is on top and uses the same machines.)

FAMILY GROUPING (order 1845Z item 4; changes the ORDER, drops nothing). Measured on the durable candidate list (690 distinct cells, tagged candidates so far): grouping by session + trigger.variant (the same trigger on neighbouring bar sizes and neighbouring parameters) gives 373 families (1.85 cells per family; biggest families 21, 18, 17 cells); counting the bar type as part of the family gives 487. Rule used: a family = same session + same trigger.variant (the "_native" suffix folded in); the best member by the OWN-STOP ranking (R per week, weakest prior year) runs first through every phase; the neighbours are listed on the page with their screen numbers and queued behind it; each neighbour still gets its own phase 2 (controls) and its own layer fit (no inheritance: that would be a shortcut). So the totals above stand: the saving is that the first round of every idea reaches a verdict after ~54% of the work, the rest of each family follows. At ~1.85 cells per family, "first round" hours are about 0.54 x the table; if N passing cells = 20 means 20 FAMILIES the full table applies to the heads and ~1.85x that when every neighbour runs.

Reading: with two machines the engine stages alone are 0.7 day (N=3) to 10 days (N=50); with four engine-ready machines 4 h (N=3) to ~2 days (N=50). That is the whole reason to get A and B engine-ready now.

## 3. Phase 1 (grid) on the same machines (from SEARCH_STATUS.md 18:33Z)
Pass 1: 108,212 jobs left at 7,111/h = 15 h (sum over machines, double-count warning until W-S3 merges). Pass 2: 25,918 jobs (top cells 1,932; exit families 6,205; family cells 17,781) at 620/h = 42 h at today's allocation (day-state re-rank holds 22 server-2 workers until ~20:00Z). Grid jobs share the same machines as the engine, so the fleet is a single pool: ASSUMED effective core-equivalents (SMT = 1.3 per core): box 1 32 + Dallas 64 + A 83 + B 83 = 262. Grid remaining ~3,250 core-hours (pass 1 ~2,150 at 0.020 core-h per job measured; pass 2 ~1,100 ASSUMED) = ~12 h if the whole pool did only grid; engine for N=6 ~1,200 core-hours (0.05 core-h per set-month) = ~4.6 h. So pure compute is ~17 h; add ~1.5x for hand-off gaps and re-runs = ~25 h.

## 4. Critical path (what actually sets the date)
1. Phase 1 pass 2 (family cells + exits): the long pole. Sessions do not finish separately: every bar row feeds all four sessions, so a session's phase-1 ranking is complete when the pass-2 jobs of its bar rows finish; per-session ranking tables exist from W-DAYMASK (three rankings, partial coverage until ~20:00Z).
2. Phase 2 per session (controls, null, trust): can start per session on the families already complete (do not wait for all four).
3. Phase 3 is a CHAIN in clock order for DECISIONS: Asia -> London -> NY AM -> NY PM, each link = layer fit (L6M round, then joint, then prior years, ~3 rounds of 1-1.5 h each on a free fleet) + day-state rebuild + stack run. Minimum chain length ~4 links x 4-6 h = 16-24 h if run strictly in order.
4. D8 spec page needs the last link plus ~2 h.

## 5. Order of running (dependencies, not habit)
- STAGE every candidate: last 6 + 3 months first; prior years and controls only for rows still alive (triage, not a shortcut: every survivor still gets everything).
- COMPUTE is not clock-ordered, DECISIONS are. While Asia is being decided run London / NY AM / NY PM candidates PROVISIONALLY against today's stack on the other machines; when an earlier session is final, re-run only the later finalists against the rebuilt day-state. Cost of the re-runs (N=6): 3,000 set-months = ~0.7 h of an engine-ready 4-machine fleet (3 h on today's 2 machines). Cost of waiting instead: the later sessions' whole stage-3 time stacks on the chain (+4-8 h of wall clock). Verdict: provisional parallel + targeted re-run is cheaper than waiting; the final numbers for a later session are only the re-run ones.
- Sessions whose pass-2 families are complete enter phase 2 immediately (start with the NY leads WP10 / XA3 which are already in phase 2 / 3a gating).
- ENGINE QUEUE PRIORITY, top first: (1) lead / finalist sets (WP10, XA3 first; then each session's finalists in clock order), (2) controls for finalists (30 date-shift), (3) layer fitting (tag NYL gate: open only after the lead controls clear), (4) provisional later-session runs, (5) near-target K7 lock controls and ORB controls to 30 (ordered to keep running; small), (6) old programme queues only on cores nothing above can use (inventory below). Mechanism: PRIORITY.txt tag order + quotas, QUEUES.txt order on server 2; W-PLAN does not edit other agents' queues, it lists changes for the lead.

## 6. Old queues (inventory, set-months; nothing deleted; Josh decides what to cancel)
| queue / tag | file | set-months | in PRIORITY.txt quota | proposal |
|---|---|---|---|---|
| NY leads WP10/XA3 (NYF) | _nye/pending_f.txt | 112 | 20 | KEEP (priority 1) |
| NY other (NYE, NYW) | _nye/pending.txt | 80 | 16 / 8 | KEEP (finalists) |
| London K7/M7 programme | _lon/pending.txt | 282 | 8 | KEEP (priority 1-4 by clock order) |
| near-target (NT) | _nt/pending.txt (+first 1) | 407 | 8 | KEEP (ordered) |
| ORB controls | _orb/pending.txt | 0 now | 4 | KEEP |
| parked NY variants | _nye/parked_1722.txt | 333 | - | keep parked; re-queue only a cell that becomes a finalist |
| parked London variants | _lon/parked_1722.txt | 120 | - | keep parked |
| P7L (P7 NY AM lots) | _p7l/pending.txt | 1,220 | 4 | park (not needed for the new-book plan; propose cancel unless Josh wants it) |
| SWB (bar swap B) | _major_sw/pending_b.txt | 1,778 | 8 | propose CANCEL (no weak cell proven; loop stopped 17:23Z) |
| SWA, ME | pending_a 0 / _major_e 1 | 1 | 4 / 4 | nothing queued |
| MF (ORB fade rest, mixed) | _major_f/pending.txt | 585 | 0 | park; keep only the ORB controls |
| EV engine-vs-live | _engvslive/l3_pending 1,642 + first 22 + pending 19 | 1,683 | 0 | park |
| DD drawdown page | _dd/pending.txt + first | 17,665 | 0 | park until after the D8 spec (largest single block) |
| S3 rebuild (S3, S3W, S3J, s3_first) | _rebuild/* | 21,909 | 0 | park (it is the T-REBUILD programme; Josh decides) |
| MB, MD, CF, CT | 59 + 4 + 24 + 2 | 89 | 0 | park |
| TOTAL old/parked | | ~44,900 | | ~10 h of an engine-ready 4-machine fleet, ~45 h at today's 1,000/h: none of it runs unless a core is free |

## 7. NO-SHORTCUTS list (what is NOT being skipped; speed must never silently drop one)
30 same-bracket random-entry controls AND 30 date-shift engine controls per finalist; the selection-corrected best-pick null (>= 20 draws of the same search) per session; trust audit (brute force, 6 truncation cuts, fills >= signal + 1 s) and the look-ahead gate on every shortlisted cell; own fitted layers per book (10 layers incl. DAY-DONE as a setting in stack-relative units, own day caps), fitted on the trailing 6 months one at a time and then jointly, tested on prior years (amber 15-30%, red > 30%) and the 2-week roll; prior years for every survivor; the exact engine gives every verdict (the fast replay only screens settings and is dropped if it cannot be validated trade-for-trade on WP10 and XA3); engine IDENTITY (691 / 37,159.82 and 637 / 41,239.76) on each machine before any of its results count and on every new hook; clock order of decisions with the day-state rebuilt after each session; every layer ON, "off" only as a reference row.

## 8. The single biggest thing that would shorten it
Make A and B ENGINE-READY now (engine data + engine cache copy + identity): takes the engine phases from ~24-30 h (N=6, today's 2 machines) to ~5-7 h, i.e. saves ~17-24 hours of the critical path, for roughly 1-1.5 hours of copy work. The grid copy to A/B is done or running; the engine copy has not been started. Second: Dallas SMT is off in firmware (64 threads); turning it on (provider request + reboot at a quiet moment) would add ~+19 core-equivalents (~+7% of the pool): small. A fifth machine would add ~83 core-eq (+32%): about -3 hours on the 25-hour compute total; it is not the lever, the idle engine hardware is.

NOTE: sections 2 and 9 use an ASSUMED 4,500 set-months/h for four engine-ready machines; the live block (section 11) recomputes the projection from measured rates (3,600/h on the first run: Dallas per-worker rate x 0.65 SMT factor x 90% busy) and replaces the assumed 0.65 by the measured A/B per-worker ratio as soon as A or B runs >= 20 engine workers for a full hour. Use section 11 for the current hours.

## 9. Dated estimates (refreshed hourly; ASSUMED parts marked; current time 2026-11-18 18:45Z)
| milestone | estimate (two engine machines only) | estimate (A and B engine-ready by ~20:30Z) |
|---|---|---|
| A, B engine-ready (data + identity) | not planned | Nov 18 ~20:00-21:30Z |
| phase 1 pass 1 done | Nov 19 ~10:00Z | Nov 19 ~06:00-08:00Z (grid + engine share the pool) |
| phase 1 pass 2 + exits done | Nov 20 ~12:00Z or later (42 h at 620/h) | Nov 19 ~22:00Z - Nov 20 ~06:00Z |
| phase 2 (controls, null, trust) per session | starts as families finish; ends ~+10 h after phase 1 | ends ~+4-6 h after phase 1 |
| phase 3 decisions in clock order (Asia, London, NY AM, NY PM) | Nov 21 - Nov 22 | Nov 20 evening - Nov 21 midday |
| D8 build-spec page | Nov 22 | Nov 21 ~12:00-18:00Z |
The two NY leads (WP10, XA3) are ahead of this timeline: lead sets controls + prior years finish ~19:00-20:00Z; layer hooks wait behind that gate (tag NYL).

## 10. Open facts (not verified; to be replaced)
SMT scaling of the engine on A/B (ASSUMED 0.65 per thread); engine copy time to A/B; whether the fast replay (W-FASTR) validates; per-job grid cost of pass 2 (rate confounded by the +60% own-stop/account scoring and the day-state re-run on the same cores); number of survivors N per session (unknown until phase 2: the table gives N = 3, 6, 10).

Hourly measured rates (appended by W-PLAN each hour; format: HHZ box1 / Dallas / A / B set-months/h, workers):
- 18:40Z box 1 ~320/h (partial hour, 11 workers), Dallas ~196/h (partial, 24 workers), A 0, B 0.

<!-- ENGINE_PLAN_LIVE -->
## 11. LIVE NUMBERS (auto, W-PLAN code/th_plan/plan_refresh.py, refreshed 2026-11-25 03:05Z; sections 1-9 above are the written plan, this block is the measurement)

Measured engine set-months per clock hour (DONE marks; UTC hour; the current hour is partial):

| hour (Z) | box 1 London | Dallas (server 2) | A Frankfurt | B Singapore | total |
|---|---|---|---|---|---|
| 11-24T21 | 0 | 1105 | 2004 | 2346 | 5455 |
| 11-24T22 | 0 | 831 | 1570 | 1797 | 4198 |
| 11-24T23 | 0 | 460 | 765 | 916 | 2141 |
| 11-25T00 | 0 | 451 | 811 | 960 | 2222 |
| 11-25T01 | 0 | 1011 | 1864 | 2182 | 5057 |
| 11-25T02 | 0 | 678 | 1217 | 1427 | 3322 |
| 11-25T03 | 0 | 56 | 107 | 117 | 280 |
| workers now | 0 | 54 | 203 | 203 | 460 |
| mean of last 3 full hours | 0 | 713 | 1297 | 1523 | 3534 |

Hyper-thread factor for A/B: MEASURED 0.48 per worker vs Dallas (A Frankfurt, 203 workers; note: workers share cores with the grid, so a lower bound).
Engine-ready status: box 1 London NO engine runs yet, Dallas (server 2) engine runs seen, A Frankfurt engine runs seen, B Singapore engine runs seen.

Hours for the engine workload (section 2 totals, no screen / with validated fast replay) at the CURRENT measured fleet rate of 3534 set-months/h; and at the rate if A and B reach Dallas-equivalent per-thread speed x 0.48:

| N per session | set-months (no screen / screen) | hours at current fleet | hours with A and B engine-ready (projected) |
|---|---|---|---|
| 3 | 16700 / 13700 | 5 / 4 h | 7.6 / 6.3 h |
| 6 | 30400 / 24500 | 9 / 7 h | 13.9 / 11.2 h |
| 10 | 48700 / 38800 | 14 / 11 h | 22.3 / 17.8 h |
| 20 | 94300 / 74600 | 27 / 21 h | 43.1 / 34.1 h |
| 50 | 231400 / 182100 | 65 / 52 h | 105.9 / 83.3 h |

Projected engine rate with A and B engine-ready: 2186 set-months/h (box 1 + Dallas measured + 2 x 128 threads x 13 per Dallas thread x factor x 90% busy).

Queue inventory (set-months waiting; nothing deleted; decision list for Josh):

| queue | file | set-months | proposal |
|---|---|---|---|
| NY leads (NYF) | _nye/pending_f.txt | 0 | keep |
| NY other (NYE) | _nye/pending.txt | 0 | keep |
| London K7/M7 | _lon/pending.txt | 10413 | keep |
| near-target (NT) | _nt/pending.txt | 160 | keep |
| parked NY variants | _nye/parked_1722.txt | 332 | parked |
| parked London variants | _lon/parked_1722.txt | 120 | parked |
| P7L | _p7l/pending.txt | 1216 | park (cancel only if Josh says) |
| SWB bar swap B | _major_sw/pending_b.txt | 1778 | PROPOSE CANCEL |
| MF (ORB fade rest) | _major_f/pending.txt | 585 | park (keep ORB controls) |
| EV engine-vs-live | _engvslive/l3_pending.txt | 1642 | park |
| DD drawdown page | _dd/pending.txt | 17562 | park |
| S3 rebuild | _rebuild/s3_pending.txt | 20518 | park |
| S3W | _rebuild/s3w_pending.txt | 508 | park |
| S3J | _rebuild/s3j_pending.txt | 378 | park |
| S3 first | _rebuild/s3_first.txt | 505 | park |
| MB | _major_b/pending.txt | 59 | park |
| TOTAL parked / cancel candidates | | 45203 | ~21 h of the projected fleet; none runs unless a core is free |

### Ladder (order 1932Z): cheapest test first, no cap, a cell leaves only by FAILING a test (core-hours: R1-R3 and R5 per-unit costs from section 11 head; UPPER BOUNDS where the pass share of the previous rung is unknown)

| rung | cells / families in | out (pass) | core-h (low-high) | hours on current fleet 96 core-eq (box 1 + Dallas) | hours on pool 262 core-eq (A+B engine-ready, ASSUMED SMT 1.3/core) | > 48 h? |
|---|---|---|---|---|---|---|
| R0 bare rule (done) | all evaluated cells | 35985 cells / 18712 families | 0-0 | 0.0-0.0 | 0.0-0.0 | no |
| R1 own-stop (2 stops; 1.5/3 shown) | 35985 cells | unknown: own-stop arrays exist for ~1,700 pairs only; failers kept, labelled | 327-327 | 3.4-3.4 | 1.2-1.2 | no |
| R2 trust + look-ahead | R1 passers (<= 35985) | unknown | 36-180 | 0.4-1.9 | 0.1-0.7 | no |
| R3 stage A: 30 same-bracket draws, every family-best (0.010 core-h per cell) | 18712 families | advance to B on EITHER p_L6M or p_ALL | 187-187 | 1.9-1.9 | 0.7-0.7 | no |
| R3 stage B: draws 31-200 (0.025 per cell) | 5614-18712 cells (ASSUMED 30-100%) | advance to C when p <= 0.02 | 140-468 | 1.5-4.9 | 0.5-1.8 | no |
| R3 stage C: draws 201-1,000 (0.105 per cell) | 561-5614 cells (ASSUMED 3-30%) | BH at q = 10% per session on p_L6M (SET 1) and on p_ALL (SET 2) | 59-589 | 0.6-6.1 | 0.2-2.2 | no |
| R3 stage D: draws 1,001-10,000 (1.17 per cell), for cells at the minimum p of stage C | 187-936 cells (ASSUMED 1-5%) | p_min 0.0001 | 219-1095 | 2.3-11.4 | 0.8-4.2 | no |
| R3 neighbours (same procedure after their best member), all stages | 17273 cells | family "isolated" if the best passes and all neighbours fail | 559-2159 | 5.8-22.5 | 2.1-8.2 | no |
| R4 whole-search null: 5 complete draws (calibration of R3 + best-pick comparison), at ~25% of A+B | all four sessions | false-discovery ratio per session | 1585-1585 | 16.5-16.5 | 6.0-6.0 | no |

R4 (5 null draws, 317 core-h each) = 1585 core-h; at a fixed 25% share of A+B (A+B = 166 core-eq assumed => 42 core-eq): 38 h (under 48 h); on the whole pool 6.0 h.

R5 for the BH passers (q = 10%; W-SHORT publishes the pass counts per session in SURVIVOR_COUNTS.md when stage B/C results exist: present). Per passing family-best: R5a+R5b+R5c 16.3 core-h (session mean; Asia 19.4, London 17.5, NY AM 15.5, NY PM 11.7) + layer programme 51 core-h (29 with the validated fast replay) = 67.3 core-h per passer. Expected false passers = q x passes. Until the counts exist: table by assumed total number of passers P over the four sessions:

| passers P (all sessions) | expected false (10%) | engine core-h (R5 + layers) | hours on the pool (262) | hours on the current fleet (96) | > 48 h? | extra A/B-class machines (83 core-eq each) to finish the engine in 48 h |
|---|---|---|---|---|---|---|
| 50 | 5 | 3366 | 13 | 35 | no (current fleet: no) | none |
| 100 | 10 | 6733 | 26 | 70 | no (current fleet: YES) | none |
| 200 | 20 | 13465 | 51 | 140 | YES | 0.2 |
| 400 | 40 | 26930 | 103 | 281 | YES | 3.6 |
| 800 | 80 | 53860 | 206 | 561 | YES | 10.4 |
| 1600 | 160 | 107721 | 411 | 1122 | YES | 23.9 |
Break-even: the engine for the BH passers fits in 48 h on the pool for P <= 187 (with the fast replay P <= 277); on the current fleet P <= 68.
MINIMUM P-VALUE per stage (p = (1 + hits) / (1 + draws)): stage A 30 draws = 0.032, stage B 200 = 0.005, stage C 1,000 = 0.001. A cell cannot pass on 30 draws alone. BH at q = 10% rejects the k-th smallest p only if p <= k x 0.10 / m (m = family-bests of the session): with 1,000 draws (p_min 0.001) a session needs at least k >= 10 x m x 0.001 cells at p = 0.001 to reject ANYTHING: Asia (m=3847) k >= 38, London (m=2237) k >= 22, NY AM (m=11460) k >= 115, NY PM (m=1168) k >= 12. A session with fewer such cells passes nothing at 1,000 draws even if its best cells are real: the top few then need more draws (stage D, 10,000: p_min 0.0001), which is cheap (~100-250 CPU-min per cell).

Per session if EVERY family-best went through R5 (upper bound, not the plan; the plan is the BH passers above):

| session | cells / families | R3 family-best core-h | R5a L6M+L3M | R5b prior years | R5c 30 controls | R5 total core-h | hours on pool | hours on current fleet |
|---|---|---|---|---|---|---|---|---|
| Asia | 6487 / 3847 | 923-1500 | 6232 | 38432 | 30007 | 74670 | 285 | 778 |
| London | 3158 / 2237 | 537-872 | 3020 | 18623 | 17449 | 39092 | 149 | 407 |
| NYAM | 24702 / 11460 | 2750-4469 | 12377 | 76324 | 89388 | 178088 | 680 | 1855 |
| NYPM | 1638 / 1168 | 280-456 | 631 | 3889 | 9110 | 13631 | 52 | 142 |

HONEST LINE (> 48 h of the fleet): no screen rung (R1-R4) needs more than 48 h on the pool (R4: 38 h at 25% of A+B). The ENGINE for the BH passers needs more than 48 h of the pool when the number of passers P exceeds ~187 (more than ~277 on the pool with the validated fast replay); on the current fleet (box 1 + Dallas) above P ~ 68. Counts of BH passers per session are not known until stage B/C finish; if they exceed the break-even, Josh decides between more machines and waiting. Nothing is trimmed to fit.
Measured engine rate on A / B (first 30 min, includes cache builds, NOT steady state): A 1296 (last 30 min x2), B 1544 (last 30 min x2) set-months/h; per-set-month cost 0.045 core-h on Dallas/box 1 (160-180 s) versus 0.30 on A when the engine was starved (1,072 s at nice 10). The order text quotes 0.3 per set-month; 7.8 core-h per cell for 30 controls implies 0.043: both are shown, the measured non-starved value is used for the totals.


**DATED ESTIMATES (W-PLAN, written 2026-11-19 00:10Z; inputs: W-GRIDOPS 22:25Z / 23:05Z, W-SHORT R3 state at 23:32Z, engine queue report 00:00Z; rates change, the script re-prints this block as written until W-PLAN edits it):**

| milestone | estimate | basis |
|---|---|---|
| REAL pass 1 end | Nov 19 ~03:00-08:00Z | W-GRIDOPS 03:00-06:00Z; measured 1,904 real jobs/h at 23:05Z with ~11.5k left at 00:00Z = ~6 h (06:00Z) |
| pass 2 + exit families end | Nov 20 ~04:00-10:00Z | 23.6k jobs left at 690/h = 34 h (SEARCH_STATUS); W-GRIDOPS ~30 h |
| null draws 1-2 end (calibration check, first full table) | Nov 19 ~23:00Z to Nov 21 ~00:00Z (95.5k jobs at nice 10, 25-50 h); a PARTIAL calibration table (sessions covered so far) was due ~23:55Z and is not on SURVIVOR_COUNTS.md yet | W-GRIDOPS |
| null draws 3-5 end (5-draw calibration complete) | ~Nov 21 midday - Nov 22 (200k jobs, parked until real pass 1 ends, then ~5-6k jobs/h) | ASSUMED rate |
| R3 compute end per session (stages A-D, clock order Asia, London, NY AM, NY PM) | stage A for all 7,650 family-bests: Nov 19 ~00:00-02:00Z (restarted 20:59Z, wall 3-5 h); stages B-D: Nov 19 ~08:00Z (ASSUMED, W-SHORT owns); the pass SET decision waits for the calibrated rule (draws 1-2): Nov 20-21 | W-SHORT |
| engine queue (R5a on the 2,333-cell seed: NY AM 1,937 + NY PM 396, XA3 layers, London/Asia stages 2-3, NT2 controls) | 44.4k set-months = 30.7 h at 1,450/h -> drains ~Nov 20 07:00Z if nothing is added (R5a only: 12 set-months per cell; prior years and controls are added only for cells not negative) | lead report 00:00Z |
| engine hours for the passers after calibration: per passer 264 set-months (12 + 72 + 180; W-SHORT) + layers ~1,133 set-months (640 with a validated fast replay) = ~1,400 set-months | at the measured 1,450 set-months/h (engine share today): P = 50 / 100 / 200 / 400 -> 48 / 96 / 193 / 386 h (31 / 62 / 125 / 250 h with the screen); at the whole pool after phase 1 (262 core-eq = ~5,800 set-months/h): 12 / 24 / 48 / 96 h (8 / 16 / 31 / 62 h) | 0.045 core-h per set-month |
| D8 spec page (clock-order chain 4-8 h + 2 h after the last engine link) | P <= 100: Nov 21 ~20:00Z - Nov 22 ~04:00Z; P = 200: Nov 22 ~20:00Z - Nov 23 ~04:00Z; P = 400: Nov 24 ~20:00Z; earliest possible Nov 21 evening; +-12 h; moves with (a) the calibrated pass counts P, (b) the engine rate on A/B (A 69-118, B 132-168 set-months/h, oversubscribed), (c) whether the engine gets the whole pool after phase 1 | assumes phase 1 done Nov 20 ~10:00Z and the engine on the whole pool after it |
48 h flag: the engine queue (30.7 h) is under 48 h; the passer engine work exceeds 48 h of the measured engine share for P >= 50 and of the whole pool for P >= ~200 (no screen). Josh decides between more machines and waiting once P is known.

DECISION LIST FOR JOSH (nothing is deleted by W-PLAN): (1) cancel SWB (bar swap B queue): no weak cell proven, loop stopped; (2) keep P7L, EV, DD, S3 rebuild PARKED (they only run on cores nothing else can use) or cancel them if you do not want them any more; (3) MF: keep ORB controls only. Server price: NOT GIVEN to W-PLAN, no cost row is shown and none is guessed.
<!-- /ENGINE_PLAN_LIVE -->
