# PASS2_COMBINER - generic combiner (entry = trigger AND k-of-N conditions) with the matched random-skip null; market-type gate; time-of-day (W-P2A, 2026-11-19)

Order: DIRECTIVE_PASS2_PLAN_20261119_1850Z.md item D.1. Master text of settings, nulls, floors: PREREG_PASS2.md; implementation spec and its hash lines: PASS2_COMBINER_SPEC.md (DECISIONS.md: PREREG_P2A_COMBINER, AMENDMENT 1 side stream, AMENDMENT 2 kept-slot rule). Shadow research only. Everything below the line "TEST" is a TEST of the machinery on 3 top books per session (NOT results, no label).

## 1. What exists (code/th_pass2/)
| file | job |
|---|---|
| p2_core.py | book parse from a BEST_BOOKS row (desc: bar row, trigger module, variant, params, bracket, side); raw trigger events; per-event tape outcome for BOTH sides at the book's bracket (the grid's walker gcore2.walk1: same stop / target / print rules, measured slip, 4.84 USD RT); one-position blocking per UTC month, RE-BLOCKED after every skipped event; window metrics (L6M, L3M, Y2023-25) |
| p2_cond.py | CONDITION LIBRARY (families a-f, section 3), state columns (g), rolling 60-session percentile thresholds |
| p2_search.py | the screen: C1 confluence, C2 gate, C3 time; nulls; best-of-K; search-aware null; hold-out columns; outputs (flags, null flags, JSON) |
| p2_batch.py | runs the top-N books of a session, W workers, nice 8 own session, MemAvailable > 40 GB guard, skips finished books; 1-minute-bar books in London / NY are skipped (reference only) |
| p2_summary.py | markdown tables from the JSONs; p2_test_core.py / p2_test_ident.py / p2_test_lib.py = identity and library checks |
Per-book call: `python3 -I code/th_pass2/p2_search.py <best_books_*_full.csv> --rank R [--searchnull 10]` ; batch: `python3 -I code/th_pass2/p2_batch.py <csv> --top 50 --workers 6 --searchnull 10`.

## 2. Fast screen = which walker (answer to "which path walker")
The GRID's fixed-bracket tape walk (gcore2.walk1, identical rules to gcore2.sim_slice / build_chunk / run_table), not the exit-screen path walker (gexit.sim_path: that one is for exit recipes and is the right tool for W-XB / exit columns, not for entry filters). Differences to the exact engine, measured on the MF1 trades of Mdcdb0b6e in L6M (348 engine trades matched 348/348 by signal time): gross P&L per trade difference median 0 USD, 72% within 25 USD, sign agreement 99%, correlation 0.965; the rest are engine exits the screen does not have (StackCut 14, UWTime 47 = trade-health / stack rules; the screen entry is signal + 1 s, the engine +2 s). The screen is therefore a SCREEN: engine dollars are higher or lower by the stack rules, the ranking is what is carried. Event count identity: 3651 vs 3650 events for the same cell.

## 3. Condition library (about 340 conditions per book; every one oriented to the event side and causal at the bar close of the signal bar). Full list for one book: /mnt/l2/l2vast/_pass2/library_example_nyam2.csv (name, family, source, param, coverage, rate)
| fam | conditions (parameter grid) | source |
|---|---|---|
| a levels (about 126) | 14 level classes x {near-backing level within 0.5 / 1 / 2 u; reaction (bar extreme within d u of a backing level and close back on the trade side) 0.5 / 1 / 2 u; room (no opposing level within 3 / 6 u)} ; side-of-line flags (VWAP, POC, day open, prior close, 00:00 open, prior-day H/L, VAH/VAL, Asia / London H/L); inside value area. u = trailing 50-bar median range of the book's bar. Classes: prior day H/L (RTH, full), prior week H/L, session levels (Asia, London, overnight, pre-market), opening range / initial balance 5 / 15 / 30 / 60, opens, VWAP and +-1 / 2 sigma bands (session, anchored, yesterday / week / month), volume profile (POC, VAH, VAL, HVN, LVN, naked POC), pivots (floor D/W, CPR, Camarilla, Woodie), supply / demand zones (SD 5 / 15 / 60 proximal prices), swing S/R (5 / 15 / 60 incl. equal highs / lows), Fibonacci (15 / 60), round numbers 50 / 100, running session high / low | feat_d minute-grid lines (1,477 causal lines, code/th_grid/triggers_d/fd_common.py rules), computed round numbers, own bars |
| b HTF (12) | larger bar of the SAME bar type at the size nearest 3x and 5x (shown with ratio): close vs EMA20 / EMA50, EMA20 slope, MACD histogram sign, SuperTrend side, ER20 > 0.3 in trade direction | gjob.load_bars of the larger row; last completed larger bar at the signal time |
| c momentum / state (about 52) | MACD (12,26,9) and (6,13,5): histogram sign / rising, line sign; CCI14 / CCI20: sign, > 100, rising; RSI14 > 50 / 55 / 60; ROC 5 / 10 / 20; EMA 10 / 20 / 50: side and slope; SuperTrend; squeeze (Bollinger 20,2 inside Keltner 20, 10, 1.5): fired within 1 / 3 / 6 bars with momentum agreeing, momentum sign; the grid's own momentum + trend modules with state_fn at DEFAULTS (native variant on non-time bars; the book's own module excluded) | ind.py on the OWN bar series (bar-native lengths in bars) |
| d tape / volume (17) | bar delta sign; delta / volume > 0.1 / 0.25; CVD 3 / 5 / 10 sign; CVD at its 10 / 20-bar extreme with price; volume > 1.0 / 1.5 / 2.0 x its 50-bar median; fast bar (seconds per bar < 0.7 / 0.5 x median; not on time bars); same-direction run 2 / 3; feat_c tape columns (10 / 25-print block delta, run volume, big-print share) | bar columns; feat_c |
| e order book (27 where feat_c exists) | top-of-book imbalance 1 / 3 / 5 / 10 levels > 0 / 0.2 / 0.4 in trade direction; micro-price sign; price slope; OFI sign; deviation from the depth-weighted mid; spread <= 2 ticks; depth ratio > 1; support wall on the trade side (ratio >= 3 / 6, within 4 / 10 ticks), opposing wall absent; sweep with the trade; opposing wall pulled; ice on the support side | feat_c b_* (rows without a feat_c store, e.g. rng_10, report "not available") |
| f cross-market (about 105) | ES, RTY, YM, NKD, MEGA: own-return z (5 / 15 / 30 min) agreeing > 0 / 1; relative-to-NQ z (5 / 15 / 60) both ways; new w-minute extreme with the trade; 6J, ZN, ZB, GC, CL, 6E: z agreeing and inverse; NYSE TICK (+5 s delay): MA5 / 15 / 30 / 60 sign, close vs MA60, 15-min extreme beyond +-500 | feat_d/xm minute store, last completed minute |
| g market-type STATE (6 metrics) | ER20, ER50, ADX14, Bollinger/Keltner width ratio, session range so far / 20-session median, previous-session range / median; thresholds = percentiles 25 / 33 / 50 / 67 / 75 over the trailing 60 sessions (earlier sessions only) | own bars, session grouping |
| h time | 30-minute block of the session (Asia 16, London 14, NY AM 13, NY PM 8 blocks), day of week | event time |
Conditions with L6M coverage < 0.8 or a rate < 2% are NOT APPLICABLE on that book and are listed in kept.json (examples: Asia has no opening-range / initial-balance lines, no London levels yet; MEGA only exists in NY hours; NKD 27%). Coverage by session is therefore automatic, nothing is silently zero.
No time-bar indicator is put on an alt bar: every indicator in c, d is computed on the book's own bar; HTF is the same bar type. Order-book and tape features come from the book's own bar row.

## 4. Search method (STATED): enumeration inside a small pool, greedy chains, plus an extended beam; no exhaustive search over the library
1. All singles (about 250 usable conditions) scored; each gets a 200-draw matched null; gain = own score minus the null's mean score.
2. POOL = top 12 by gain (positive L6M gain and L3M $/wk above the null mean; completed by the best of the rest up to 6) - PREREG 1.1 C1.
3. Enumeration over the pool: every subset of size 2 and 3 with k in {all, majority, 1} (about 790 sets).
4. Greedy forward chains N = 4..12: k = all, k = N-1 (PREREG) and k = majority (extra).
5. EXTENDED (EXT) beam: pool 60, beam 25, N <= 10, k in {N, N-1, majority} per node. Not in the PREREG; it finds the largest in-sample gains and, in the TEST, the clearest over-fit (section 7).
"Any k, any N" over the whole library is not enumerated (2^340 subsets); what is scored is 1,073 to 1,125 C1 settings per book plus 122 gate settings plus 29 to 128 time settings (1,247 to 1,329 in total). Exact counts per book in kept.json (n_screened).

## 5. Null, gates, selection (as pre-registered; see PASS2_COMBINER_SPEC.md)
- Floor: after any setting L6M and L3M keep >= 60% of the reference trades and >= F per week; F = Asia 5, NY AM 2 (PREREG), London 3, NY PM 2 (PROPOSED here for the sessions the PREREG leaves open: below the 10th percentile of first-look books at 1 lot). Settings below the floor stay in screen_all.csv with gate_ok False and are out of every contest.
- Matched random-skip null: same number of kept EVENTS per week, drawn within the week, same walker incl. re-blocking (so a random skip frees later signals exactly as a real skip does). 200 draws for every screened setting, 1,000 for the top 10 of a component, 10,000 for kept settings. Flip settings: same number of flipped events per week. p6 = share of null draws with an L6M SCORE at least as high (SCORE = L6M $/wk / max(ulcer, 200 USD)). The L6M ulcer / $/wk p-values are also stored (p_ulcer6, p_pwk6).
- Best-of-K (max-T): 200 replicates of the best score over K random sets of the sizes of the floor-passing settings; the component's best must beat the 90th percentile.
- SEARCH-AWARE null (the missing piece found in the TEST): the whole C1 search repeated on condition rows permuted within weeks (outcomes untouched), 10 replicates in the TEST, 30 draws for the inner pool gain; the real best score must beat these. Cost about 38% of a book's CPU.
- Hold-out: Y2023 / Y2024 / Y2025 (202511 excluded) are never used for selection; each kept setting is shown with its own and the reference's $/wk, ulcer, score per year.
- Kept per book: C1 5 (3 non-EXT by score, the best EXT, one by lowest ulcer with $/wk >= 80% of reference), C2 3, C3 3; each floor-passing and p6 <= 0.10 (best of component carried with a note if none). C3 guard: dropped events lose money in both halves (odd / even weeks) of L6M.

## 6. Interface to W-P2B (agreed 19:00-19:20Z)
Files: `/mnt/l2/l2vast/_pass2/flags/<setid>.parquet`, `<setid>_null.parquet`, `/mnt/l2/l2vast/_pass2/combiner/<setid>/kept.json`, `screen_all.csv` (every scored setting with metrics and null). `<setid>` = the BEST_BOOKS set name (e.g. TL3_ASI_Ldcdb0b6e_RA7).
Flag parquet: one row per RAW trigger event of the book's session (before blocking; verified 100% key match to the engine event file Ldcdb0b6e.parquet: 7131 of 7131). Columns: `ts` int64 = signal bar t_close (UTC s) + 2 (the engine event ts), `side` int64 = the original event side (also for flipped events), `flag_<settingid>` int8 (1 = take), `flip_<settingid>` int8 (gate settings that flip: 1 = trade the opposite side at the same bracket), `nconf_<settingid>` int16 (conditions satisfied, C1), `er` float32 (ER20), `state` int8 (ER20 >= its median), `bits` uint64 (one bit per condition of the book's pool, order in kept.json "pool"). Null file: same ts / side, `flag_null_<settingid>_<seed>` (seeds 0-19), `flip_null_...` for flips. An event with no row = taken.
Setting JSON (kept.json -> settings[]):
```
{"setting_id": "C1_E3_1_34_330_47", "component": "C1", "desc": "...", "flag_col": "flag_C1_...", "flip_col": null,
 "params": {"conds": ["LV_OPENS_near_back_2u", "..."], "k": 1, "N": 3},                     # C2: {"metric": "ER50", "pct": 33, "action": "trend_only|range_only|flip_in_range|flip_in_trend"}; C3: {"kind": "drop_block|keep_window|drop_first|drop_last|drop_dow", ...}
 "conditions": [{"name": "...", "family": "a", "source": "feat_d.lines:OPENS", "param": {...}}],  "k": 1, "N": 3, "ext": false,
 "L6M": {"pwk":..,"ulcer":..,"maxdd":..,"worst_wk":..,"score":..,"ntr":..,"tpw":..}, "L3M": {...}, "hold": {"Y2023": {...}, "Y2024": {...}, "Y2025": {...}},
 "floor_ok": true, "null": {"draws": 10000, "p6":.., "p3":.., "p_pwk6":.., "p_ulcer6":.., "score6_mean":.., "ntr6_mean":..}, "guard": null, "note": ""}
```
kept.json top level also has: book (set, desc, row, module, params, bracket, side), reference metrics, floor, summary per component (K, best, max-T q90, beats_maxT, search_null_p), ref_holdout, pool, not_applicable, cpu_seconds, cpu_total, library_timing, n_screened.
Side convention (AMENDMENT 1): rows with cell id L... and a desc side other than both are scored on the both-side event file (see section 8), so the flag file has both sides.

## 7. TEST (3 books per session; machinery test, NOT results; screen walker, 1 lot; run 2 after AMENDMENT 2; run 1 in /mnt/l2/l2vast/_pass2/run1_superseded)
Books: Asia ranks 2, 3, 4 and NY AM ranks 1, 2, 3 of the BEST_BOOKS_*_full.csv as of 19:00Z. Tables per book (every kept setting, hold-out per year, null p): autopilot/PASS2_COMBINER_TEST_TABLES.md.
| book | events | ref L6M $/wk / ulcer | C1 best score vs max-T q90 | C1 search-aware p (10 permuted searches) | C2 best vs q90 | C3 best vs q90 | CPU s (of which search-aware null) |
|---|---|---|---|---|---|---|---|
| Asia rank 2 Ldcdb0b6e cdr_100 mvote | 7,132 | 1971 / 3695 | 6.00 vs 1.42 | 0.09 | 0.84 vs 1.31 | 0.74 vs 1.18 | 94 (31) |
| Asia rank 3 L86781ac0 vrb_700 bollinger | 6,999 | 1770 / 5246 | 4.11 vs 1.43 | 0.55 | 0.76 vs 1.11 | 0.55 vs 1.06 | 107 (32) |
| Asia rank 4 Lc4e74264 time_m_3 pullback_ema | 36,736 | 1341 / 4863 | 2.93 vs 1.26 | 0.82 | 0.72 vs 0.90 | 0.44 vs 0.87 | 323 (151) |
| NY AM rank 1 Ld9ea2776 rng_10 profile_nodes | 46,881 | 900 / 9234 | 4.43 vs 1.06 | 0.36 | 0.54 vs 0.90 | 0.68 vs 0.55 (beats) | 516 (199) |
| NY AM rank 2 Lb44a3e99 tm300 tape_delta | 2,862 | 1117 / 5073 | 2.61 vs 1.04 | 0.27 | 0.65 vs 0.87 | 0.39 vs 0.66 | 45 (17) |
| NY AM rank 3 L678ebadd tib_6000 profile_va | 15,406 | 2252 / 5885 | 8.54 vs 1.39 | 0.09 | 0.89 vs 1.17 | 0.59 vs 0.89 | 168 (67) |
What the TEST shows about the machinery (not about the books):
1. The plain matched random-skip null and the max-T null are beaten by the best C1 setting on every book (p6 = 0.0001): picking among 1,100 condition sets on L6M finds large in-sample ulcer cuts (for example Asia rank 2: ulcer 3695 -> 772 with 4,630 vs 1,971 $/wk). The null that pays for the SEARCH (permuted condition rows, whole search repeated) is beaten at p 0.09 on two books and not at all on four (p 0.27 to 0.82). So a "beats the random-skip null" result is necessary and not sufficient; the search-aware null must be on every C1 verdict. The hold-out years agree: the kept settings beat the reference score in 0 to 2 of 3 prior years (most often 1), the extended-beam settings least.
2. C2 best settings do not beat the max-T q90 on any of six books; C3 beats it on one (NY AM rank 1: drop the first 30-minute block, 0.68 vs 0.55, guard passed) and that setting is far worse than the reference in all three prior years (Y2023 -771 vs +426 $/wk, Y2024 -204 vs +1,103, Y2025 +40 vs +606). These are screens, not labels.
3. The library coverage varies by book: 327 to 341 conditions, 34 to 86 not applicable (Asia 81 to 86: opening-range and London lines, MEGA, NKD, part of the order book); rng_10 has no feat_c store (book conditions absent).
4. The enumeration over the PREREG pool (non-EXT) improves the L6M ulcer less than the beam and holds up no better out of sample; no setting in the TEST earns a label.

## 8. Findings outside the combiner (act on them)
- BEST_BOOKS rows with cell id L... and desc side "long" are scored on a both-side stream (Asia 227 rows, NY AM 501 rows). Checked: Asia Ldcdb0b6e (event file 3,650 long + 3,481 short; its long-only twin is Mdcdb0b6e at rank 136), NY AM L678ebadd (7,801 long + 7,604 short; engine L6M 2,702 $/wk, screen both sides 2,252, long only -927). The desc side column is therefore wrong for those rows; pass 2 uses the stream that was scored (AMENDMENT 1). Whoever owns BEST_BOOKS should fix the label or re-score as long-only; the long-only streams are different books.

## 9. Cost per book (cpu seconds, measured; box load average about 100 during the TEST, nice 8)
| part | seconds |
|---|---|
| events + tape walk (both sides) | 3 to 40 (scales with raw events) |
| library (about 340 conditions incl. grid state modules, HTF load) | 7 to 25 |
| C1 + C2 + C3 screen (about 1,300 settings, 200-draw nulls each) | 15 to 100 |
| nulls: 1,000 / 10,000 draws, best-of-K (200 x K) | 40 to 150 |
| search-aware null (10 permuted searches) | 17 to 199 |
| total per book | 44 to 516, mean 209 (130 without the search-aware null); books with > 30,000 raw events (range / tick bars) are 5 to 9 minutes |
Full screen of 50 books per session: about 2.9 CPU hours with the search-aware null (1.8 without). With 6 workers at nice 8 on this loaded box (each worker gets roughly a third to a half of a core) the wall time is about 1.5 to 2.5 hours per session; Asia 50 then NY AM 50 in sequence is about 4 hours; the code is ready now, so the first full Asia screen can start the minute the BEST_BOOKS list of the batch is frozen and would finish about 2 h later (a start at 19:30Z gives 21:30Z). Memory per worker 3 to 6 GB; batch runner keeps box-1 MemAvailable above 40 GB.

## 10. What does not exist / limits (stated)
- Own-bracket trigger modules (zones / Fibonacci / swing S/R families that emit their own stop and target columns) are not supported by the combiner v1: the book raises "own-bracket module". Count not yet measured on the list.
- Entry method, exits, in-trade management, re-entry, sizer are other components (W-P2B hooks / exit screen); the combiner only supplies flag columns and the ER / state / nconf columns for the sizer and gate hooks.
- "Switch a session between a trend book and a range book by state" needs two books' flags together; not built here (state column er / state is in every flag file; W-COMBO stage).
- London and NY PM floors are proposals; not run.
- The screen uses the grid's slip model and signal + 1 s entry; engine differences in section 2.
- Conditions needing live data that D7 may not have (feat_c book columns, UW, megacap feed, ES) are in the library as such and carry their data need in the source column; the live-path cost is the TOOLS / FEEDS question, not decided here.
- The search-aware null is run for C1 only; C2 / C3 have max-T only (about 120 settings each, less selection freedom).

## 11. Live books (added 19:50Z)
Live books enter the combiner as streams (book, session) via `p2_search.py --live BOOK:SESSION` (p2_core.LiveBook). Event source = the JL3 exact-engine trades (runs_rf/TL3_EV_JL3, 2023-04 to 2026-10); outcome = the realised 1-lot net trade with the live exits and layers as run. IMPORTANT FOR THE JOINT STAGE: these events are the ENGINE-TRADED signals only; signals dropped by the stack (DAY-DONE, stack cut, caps) are missing, a skipped event removes its trade without re-blocking, and the stack rules are not re-run, so a screen gain can be partly a stack effect; only the exact engine joint stage decides. Indicator bars = the live row (K7 tm180, U7 tm600, P7 / H7 / A7 / O7 tm300), last completed bar before the signal; M7 (tm60 = 1-minute) is not screened in London / NY (bar rule). Identity: P7 Asia L6M 4001 vs BEST_BOOKS 3918 $/wk, ulcer 1658 vs 1688, 22.8 vs 22.8 trades/wk. All live results are "screen only", with the search-aware p beside them (P7 Asia: C1 p 0.18). Flag files: ts = sig_ns seconds (no +2).
