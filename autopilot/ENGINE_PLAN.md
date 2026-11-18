# ENGINE_PLAN - fastest path through phases 2-4, no shortcuts (W-PLAN, order 1840Z), written 2026-11-18 18:45Z, refreshed hourly (rates + dated estimates at the bottom)

Plain words. Research only, no spend. "Set-month" = one engine run of one set (a stack variant) for one calendar month; it is the engine's unit of cost. Nothing here lowers a standard: 30 controls, the selection-corrected null, own fitted layers (jointly), prior years, exact-engine verdicts, identity on every machine and every new hook, clock order of decisions all stay. This page is about ORDER and PARALLELISM only. Numbers marked ASSUMED are not measured yet and are replaced by measurements as they arrive.

## 0. LADDER (order 1932Z, supersedes the N = 3..50 sizing in section 2; section 2 stays as the per-survivor cost model)
The work is sized on SURVIVOR_COUNTS.md (bare, 19:08Z): Asia 2,992 cells / 1,890 families; London 1,035 / 808; NY AM 9,504 / 4,556; NY PM 531 / 396 = 14,062 cells / 7,650 families. No top-N cap; a cell leaves only by FAILING a rung; engine capacity only sets the order. Live version of every number below (rates, counts, hours, per-session table): section 11, refreshed hourly. Fleet definitions: current fleet = box 1 + Dallas = 96 core-equivalents; pool = + A + B at ASSUMED 1.3 core-eq per physical core with SMT = 262 core-eq (the factor is replaced by the measured one when A/B steady rates exist). Costs: R1 0.0091 core-h per (row, module) pair (W-DAYMASK re-run rate; <= one pair per cell), R2 0.001-0.005 per cell, R3 0.24-0.39 per cell (W-SHORT's own table prices Asia at 418 core-h for 1,349 pairs because cells of the same row and module share a simulation, so my per-cell R3 numbers are upper bounds), R4 6,300 fixed, R5 0.045 core-h per engine set-month measured (160-180 s per month on Dallas/box 1); 7.8 core-h per cell for 30 controls.
NOTE on the 0.3 core-h per set-month in the order: 0.30 is the STARVED-A figure (1,072 s per month at nice 10 beside 112 grid workers). It is inconsistent with the order's own 7.8 core-h per cell for 30 controls, which implies 0.043. Totals here use the measured non-starved 0.045; if A's guaranteed-share rate (24-32 engine workers) also lands near 0.3, every R5 number rises ~6.7x on A only, not on Dallas/box 1.
A engine rate measured so far (first 30 min after dispatch start, includes per-month cache builds, NOT steady state): ~44 set-months/h with 32 engine workers beside 112 grid workers (load 142 on 128 threads); B: engine just starting (0 done). The per-hour measurements and the SMT factor update in section 11 automatically.

| rung | in -> out | core-h | hours, current fleet (96) | hours, pool (262) | > 48 h? |
|---|---|---|---|---|---|
| R0 bare (done) | 4.4M-4.8M cells per session -> 14,062 cells / 7,650 families | done | - | - | no |
| R1 own-stop | 14,062 -> unknown (arrays built for ~1,700 pairs; grid re-running the rest); failers kept as "depends on today's stack" | <= 128 | 1.3 | 0.5 | no |
| R2 trust + look-ahead | R1 passers -> unknown (sample audit 47/48) | 14-70 | < 1 | < 1 | no |
| R3 30 same-bracket draws (pass >= 27/30; counts at 24 / 27 / 29 shown) | 7,650 family-bests first, then 6,412 neighbours -> unknown (XA3 25/30, WP10 15/30) | 1,836-2,984 (best) + 1,539-2,501 (neighbours) | 19-31 + 16-26 | 7-11 + 6-10 | no (current fleet 35-57 h for all) |
| R4 selection-corrected null, 20 draws, whole search | all sessions -> FDR per session | 6,300 | 66 | 24 (at 100% of the pool); at the ordered 25% of A+B (42 core-eq) = 152 h | YES at 25% share: 152 h (6.3 days); finishing in 48 h needs 131 core-eq = 79% of A+B |
| R5a engine L6M+L3M, ADD + replace each live book | 7,650 family-bests -> rows not negative go on | 9,287 (upper bound) | 97 | 35 | YES on the current fleet |
| R5b prior years (37 months) | survivors of R5a | 57,269 (upper bound at 100%) | 597 | 219 | YES even on the pool |
| R5c 30 date-shift engine controls | survivors of R5b | 59,670 (upper bound at 100%) | 622 | 228 | YES even on the pool |
| phase 3 layers (10 layers, one at a time then jointly, exact engine) | every R5c survivor (book) | 51 per book (29 with the validated fast replay) | - | - | depends on the count |
Per-session R5 upper bounds (core-h / hours on the pool): Asia 36,685 / 140 h; London 14,120 / 54 h; NY AM 70,800 / 270 h; NY PM 4,621 / 18 h.

HONEST LINES. (a) R4 needs more than 48 h at the ordered 25% share of A+B: 152 hours, i.e. it finishes about Nov 25, not with phase 1; to finish with phase 1 it needs ~131 core-eq (79% of A+B, or half of the pool). (b) R5 at 100% of the R3-passing family-bests is 126,226 core-h = 482 hours (20 days) on the pool: more than 48 h by 10x. It fits in 48 h on the pool only if <= 10% of the R3 passers proceed to R5 (4% on the current fleet); including the layer programme (51 core-h per surviving book x books) the limit is ~2.4% of the R3 passers (about 185 family-bests). (c) Nothing is trimmed: the fraction that passes R3 is unknown until R3 runs (XA3 passes at 24/30 and fails at 27, WP10 fails), so the engine plan must wait for the R3 pass count. Josh decides between more machines and waiting.

DATED ESTIMATE FOR THE D8 SPEC PAGE (assumes phase 1 + R1-R3 finished by Nov 20 ~12:00Z, R4 run at 79% of A+B so it is done by then, pool then devoted to R5 + layers; ASSUMED pool rate 262 core-eq; two-link slack included; clock-order chain +4-8 h; spec page +2 h):
| share f of R3-passing family-bests that go through R5 + layers | engine core-h (R5 + layers) | hours on the 262 pool | D8 spec page | more machines to finish the engine in 48 h |
|---|---|---|---|---|
| 1% (77 families) | 5,200 | 20 h | Nov 21 ~18:00Z - Nov 22 ~02:00Z | none (fits) |
| 2.4% (185) | 12,400 | 48 h | Nov 22 ~20:00Z - Nov 23 ~04:00Z | none (this is the 48 h line) |
| 3% (230) | 15,500 | 59 h | Nov 23 ~08:00Z - 16:00Z | +1 machine of the A/B class (+83 core-eq) |
| 10% (765) | 51,600 | 197 h | Nov 29 | about +10 machines of the A/B class |
| 100% (7,650) | 516,000 | 1,970 h (82 days) | not reachable | about +90 machines: not a machine question, a count question |
The two quantities Josh needs to read this table are f (known only after R3 runs) and the real engine rate on A and B under a guaranteed engine share (first measurement 44 set-months/h on A is far below the 1,300/h assumed; steady state not reached). Until f and the A/B steady rate are known the honest D8 date is a range: Nov 22 (f <= 2.4%) to beyond Nov 29.

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
## 11. LIVE NUMBERS (auto, W-PLAN code/th_plan/plan_refresh.py, refreshed 2026-11-18 19:31Z; sections 1-9 above are the written plan, this block is the measurement)

Measured engine set-months per clock hour (DONE marks; UTC hour; the current hour is partial):

| hour (Z) | box 1 London | Dallas (server 2) | A Frankfurt | B Singapore | total |
|---|---|---|---|---|---|
| 11-18T13 | 609 | 547 | 0 | 0 | 1156 |
| 11-18T14 | 406 | 287 | 0 | 0 | 693 |
| 11-18T15 | 614 | 499 | 0 | 0 | 1113 |
| 11-18T16 | 620 | 471 | 0 | 0 | 1091 |
| 11-18T17 | 426 | 288 | 0 | 0 | 714 |
| 11-18T18 | 305 | 180 | 0 | 0 | 485 |
| 11-18T19 | 217 | 104 | 26 | 0 | 347 |
| workers now | 40 | 24 | 61 | 4 | 129 |
| mean of last 3 full hours | 450 | 313 | 0 | 0 | 763 |

Hyper-thread factor for A/B: ASSUMED 0.65 (no A/B engine measurement yet).
Engine-ready status: box 1 London engine runs seen, Dallas (server 2) engine runs seen, A Frankfurt NO engine runs yet, B Singapore NO engine runs yet.

Hours for the engine workload (section 2 totals, no screen / with validated fast replay) at the CURRENT measured fleet rate of 763 set-months/h; and at the rate if A and B reach Dallas-equivalent per-thread speed x 0.65 (assumed):

| N per session | set-months (no screen / screen) | hours at current fleet | hours with A and B engine-ready (projected) |
|---|---|---|---|
| 3 | 16700 / 13700 | 22 / 18 h | 6.1 / 5.0 h |
| 6 | 30400 / 24500 | 40 / 32 h | 11.2 / 9.0 h |
| 10 | 48700 / 38800 | 64 / 51 h | 17.9 / 14.3 h |
| 20 | 94300 / 74600 | 124 / 98 h | 34.7 / 27.5 h |
| 50 | 231400 / 182100 | 303 / 239 h | 85.2 / 67.0 h |

Projected engine rate with A and B engine-ready: 2716 set-months/h (box 1 + Dallas measured + 2 x 128 threads x 13 per Dallas thread x factor x 90% busy).

Queue inventory (set-months waiting; nothing deleted; decision list for Josh):

| queue | file | set-months | proposal |
|---|---|---|---|
| NY leads (NYF) | _nye/pending_f.txt | 0 | keep |
| NY other (NYE) | _nye/pending.txt | 0 | keep |
| London K7/M7 | _lon/pending.txt | 118 | keep |
| near-target (NT) | _nt/pending.txt | 381 | keep |
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
| TOTAL parked / cancel candidates | | 45203 | ~17 h of the projected fleet; none runs unless a core is free |

### Ladder (order 1932Z): cheapest test first, no cap, a cell leaves only by FAILING a test (core-hours: R1-R3 and R5 per-unit costs from section 11 head; UPPER BOUNDS where the pass share of the previous rung is unknown)

| rung | cells / families in | out (pass) | core-h (low-high) | hours on current fleet 96 core-eq (box 1 + Dallas) | hours on pool 262 core-eq (A+B engine-ready, ASSUMED SMT 1.3/core) | > 48 h? |
|---|---|---|---|---|---|---|
| R0 bare rule (done) | all evaluated cells | 14062 cells / 7650 families | 0-0 | 0.0-0.0 | 0.0-0.0 | no |
| R1 own-stop (2 stops; 1.5/3 shown) | 14062 cells | unknown: own-stop arrays exist for ~1,700 pairs only; failers kept, labelled | 128-128 | 1.3-1.3 | 0.5-0.5 | no |
| R2 trust + look-ahead | R1 passers (<= 14062) | unknown | 14-70 | 0.1-0.7 | 0.1-0.3 | no |
| R3 same-bracket random entries, 30 draws: family-best first | 7650 families (14062 cells) | unknown (XA3 25/30, WP10 15/30; threshold >= 27/30) | 1836-2984 | 19.1-31.1 | 7.0-11.4 | no |
| R3 all family members after the best | 6412 cells | unknown | 1539-2501 | 16.0-26.0 | 5.9-9.5 | no |
| R4 selection-corrected null (20 draws, whole search, shared) | all four sessions | FDR per session when run | 6300-6300 | 65.6-65.6 | 24.0-24.0 | YES (current) |
| R5a engine L6M + L3M: ADD + replace each live book (6 months, family-best, UPPER BOUND = every R3 family-best passes) | 7650 families | rows not negative go on | 9287-9287 | 96.7-96.7 | 35.4-35.4 | YES (current) |
| R5b engine prior years 37 months (UPPER BOUND) | 7650 families |  | 57269-57269 | 596.6-596.6 | 218.6-218.6 | YES (even on the pool) |
| R5c 30 date-shift engine controls, 7.8 core-h per cell (UPPER BOUND) | 7650 families |  | 59670-59670 | 621.6-621.6 | 227.7-227.7 | YES (even on the pool) |

R5 total at 100% of family-bests proceeding (upper bound): 126226 core-h = 482 h on the 262 pool = 20.1 days. Break-even: the R5 work fits in 48 h on the pool only if <= 10% of the R3-passing family-bests proceed (<= 4% on the current 96 core-eq).
R4 at a fixed 25% share of A+B (A+B = 166 core-eq assumed => 42 core-eq): 152 h; to finish in 48 h it needs 131 core-eq (79% of A+B).

Per session (upper bounds; hours on the 262 pool / on the current 96 core-eq):

| session | cells / families | R3 family-best core-h | R5a L6M+L3M | R5b prior years | R5c 30 controls | R5 total core-h | hours on pool | hours on current fleet |
|---|---|---|---|---|---|---|---|---|
| Asia | 2992 / 1890 | 454-737 | 3062 | 18881 | 14742 | 36685 | 140 | 382 |
| London | 1035 / 808 | 194-315 | 1091 | 6727 | 6302 | 14120 | 54 | 147 |
| NYAM | 9504 / 4556 | 1093-1777 | 4920 | 30343 | 35537 | 70800 | 270 | 738 |
| NYPM | 531 / 396 | 95-154 | 214 | 1319 | 3089 | 4621 | 18 | 48 |

HONEST LINE (> 48 h of the fleet): R5b engine prior years 37 months needs 57269 core-h = 219 h on the pool (597 h on the current fleet); R5c 30 date-shift engine controls, 7.8 core-h per cell needs 59670 core-h = 228 h on the pool (622 h on the current fleet). Rungs R4 and R5a are also above 48 h on the current fleet alone. Josh decides between more machines and waiting; nothing is trimmed to fit.
Measured engine rate on A / B (first 30 min, includes cache builds, NOT steady state): A 52 (last 30 min x2), B 0 (last 30 min x2) set-months/h; per-set-month cost 0.045 core-h on Dallas/box 1 (160-180 s) versus 0.30 on A when the engine was starved (1,072 s at nice 10). The order text quotes 0.3 per set-month; 7.8 core-h per cell for 30 controls implies 0.043: both are shown, the measured non-starved value is used for the totals.


DECISION LIST FOR JOSH (nothing is deleted by W-PLAN): (1) cancel SWB (bar swap B queue): no weak cell proven, loop stopped; (2) keep P7L, EV, DD, S3 rebuild PARKED (they only run on cores nothing else can use) or cancel them if you do not want them any more; (3) MF: keep ORB controls only. Server price: NOT GIVEN to W-PLAN, no cost row is shown and none is guessed.
<!-- /ENGINE_PLAN_LIVE -->
