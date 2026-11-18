# SEARCH_STATUS - full-search programme (plan 1722Z: no Globex deadline), W-GRIDOPS, refreshed 2026-11-18 18:38Z

Plain words. Data end 2026-11-15 (NQ). Research only, no spend. Phases: 1 finish the whole search -> 2 prove it is not luck (30 controls, selection-corrected null, trust) -> 3 gates/layers one by one then jointly -> 4 D8 spec. Every number below is a screen-level number unless it says engine.

## Phase 1 - progress (the grid is not split by session: one job = one bar row x one trigger module x one tag; every session reads the same results, so the percentages below are the same for NY AM, NY PM, London and Asia)

| item | done | todo | jobs/hour (last 60 min) | ETA at that rate |
|---|---|---|---|---|
| pass 1, all tags (real + random-entry nulls 1/2 + extra null draws) | 69268 result files | 139421 jobs | 5116 | 27.3 h |
| pass 2 (family cells, exits a2, top cells) | n/a | 26334 (a top cells 1902, a2 exit families 6651, c family cells 17781) | 503 | 52.4 h |

NOTE (18:40Z): the grid is partitioned over server 2 (rows 0-1 of 12), A (2-6) and B (7-11) by W-S3; finished results are merged into server 2 every ~5 min (lag <= 10 min), the todo and worker counts are summed over the three servers. A and B also see 172 bar rows that are complete on box 1 but not yet on server 2, so total todo is higher than the earlier single-server figure (about +50%).

Pass-1 results on disk by tag: real 30667, null draw 1 17582, null draw 2 17497, extra draws (3-25) 2946 files. Pass-1 results still waiting for their pass-2 upgrade: real 21186.

Machines (grid partitioned across servers): 207.188.7.103 load 77.93 workers 30; 109.94.96.39 load 109.20 workers 112; 206.223.224.21 load 104.07 workers 124; grid workers 266 (259 computing), engine workers 24; forward-path tables built (summed over servers) 272.

Since 17:23Z: pass-1 todo 80818 -> 139421 (+58603), pass-2 todo 25951 -> 26334 (+383). Pass-2 todo grows when pass 1 delivers cells that earn pass 2.

## Machines (hourly; busy % is measured from /proc/stat against the REAL thread count of each machine)

| machine | real threads | busy % | load1 | grid workers (computing) | engine workers | re-rank/other workers | results/hour (this machine) |
|---|---|---|---|---|---|---|---|
| server 2 Dallas | 64 | 100.0 | 77.93 | 266 (259) | 12 | 23 | 5628 |
| A Frankfurt | 128 | 85.3 | 109.20 | 112 (109) | 0 | 0 | 3020 |
| B Singapore | 128 | 93.1 | 104.07 | 124 (120) | 0 | 0 | 3417 |
| box 1 London (lead, engine fillers) | 32 | 100 | 43.34 | 0 | see CORES.md | - | - |

Server 2 has 64 threads (SMT off in firmware, order 1830Z check), A and B 128 each, box 1 32. Total jobs/hour and the phase-1 ETA are in the table above (sum over servers; double counting warning applies until W-S3 merges results). Any machine under 85% busy for 3 readings with work pending gets a one-line explanation in MORNING.md.

## Blocked / cannot run (listed, not skipped silently)

Failed jobs leave an error stub that the loop retries after 4 hours (older stubs are retried automatically). Error files on disk: {'real': 355, 'p1real': 1680, 'p1rand1': 1481, 'p1rand2': 1448}.

| module | failures (files) | why |
|---|---|---|
| trig_book_ofi | 294 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_cancel | 294 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_ice | 294 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_queue | 294 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_pslope | 294 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_dwm | 294 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_imb | 294 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_micro | 294 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_thin | 294 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_wall | 294 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_sweep | 294 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_tape_run | 289 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_tape_block | 288 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_tape_unfinished | 287 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_tape_stack | 287 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_tape_sizemix | 287 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_levels_sd5 | 19 | all signal calls raised (cause needs a test) |
| trig_levels_sd15 | 19 | all signal calls raised (cause needs a test) |
| trig_levels_sd60 | 19 | all signal calls raised (cause needs a test) |
| trig_levels_fib60 | 19 | all signal calls raised (cause needs a test) |
| trig_levels_sdx5 | 19 | all signal calls raised (cause needs a test) |
| trig_levels_fib5 | 19 | all signal calls raised (cause needs a test) |
| trig_levels_sdx15 | 19 | all signal calls raised (cause needs a test) |
| trig_levels_fib15 | 19 | all signal calls raised (cause needs a test) |
| trig_levels_sdx3 | 19 | all signal calls raised (cause needs a test) |

## Phase 2 / 3 (running in parallel, from the 1722Z order)

- NY leads to the full standard: WP10 (NY PM money flow, keep K7 and add) and XA3 (NY AM VWAP retest on 5000-tick): autopilot/NEW_BOOK_ENGINE.md. London replacement programme: NEW_BOOK_ENGINE_LONDON.md. Near-target K7 lock controls: DS3_NEAR_TARGET.md. ORB fade controls: DS3_ORB_FADE_LEAD.md.
- Shortlist (bare, equal risk) and its trust audit: NEW_BOOK_SHORTLIST.md. Look-ahead gate for every reversal-type bar: BAR_LOOKAHEAD_GATE.md (all passed).
- Account-rule scoring (DAY-DONE mask from the JL3 day-state): in progress by W-DAYMASK; the side-by-side ranking appears below when its file exists.

## Survivor rule (order 1845Z: NO CAP, rule-based, no top-N anywhere)

A cell goes forward to phases 2-3 if ALL of these hold, judged on the OWN-STOP ranking (stack-independent) with bare and current-stack mask shown beside it:
- positive over the last 6 months (26 weeks to the data end) AND over the last 3 months beside it, on EQUAL RISK (R = points / the cell stop in points);
- prior years 2023 / 2024 / 2025 not a disaster: AMBER = 15-30% worse than the reference (shown, still goes forward flagged), RED = more than 30% worse (shown, NOT delivered as a pick);
- persistence over 60% (share of 2-week periods positive in the rolling pick); at least 100 trades in the last 6 months;
- passes the trust audit (brute-force re-simulation, 6 truncation cuts, fills at least signal + 1 s) and the look-ahead gate.
Engine capacity decides the ORDER cells are tested in (best first), never WHETHER a passing cell is tested. If the count makes phases 2-3 long, the count and the hours are reported here; nothing is trimmed. Near-duplicates (the same trigger on neighbouring bar sizes or parameters) are grouped as one FAMILY for the engine: best member first, neighbours listed with their screen numbers and run after, nothing dropped. Cells that fail the rule stay on disk with the reason so a later 2-week refit can pick them up.

### Counts passing per session

Not available yet: W-SHORT writes autopilot/SURVIVOR_COUNTS.md (counts per session on own-stop / bare / mask, failures by reason, number of families, path of the failing-cell file). The 4,000-cell tables in DAYMASK_RANK.md are capped for display only and are NOT the survivor count.

## Clock order (addendum 1731Z): sessions are decided Asia -> London -> NY AM -> NY PM

Phase 1 is NOT split by session (one grid job feeds all four sessions), so the grid cores cannot be re-ordered by session without cost; what follows the clock order is the scoring and the later phases: scoring/ranking runs Asia first; in phases 3-4 each session is decided on the exact engine after the earlier session is final. Asia is NOT add-only: replace / add / mixed with a higher bar (drawdown first AND dollars, last 6 and 3 months, no red prior year, 30 controls, selection-corrected test).

## Top 10 Asia

(b) OWN-STOP ranking (stack-independent; carries the shortlist):

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | cusum_40 | levels_fib15.break_native {"n": 3, "k": 0.5} | plain60/60 | +673 | +70 | +0.43 | 555 | AMBER/ok/ok | L6M @1.5 stops +673 / @3 stops <=0 or <100 tr |
| 2 | vsess_300 | levels_profile_va.retest {"M": 6, "tol": 0.0} | plain60/60 | +376 | -130 | +0.24 | 298 | ok/ok/ok | L6M @1.5 stops +376 / @3 stops +569 |
| 3 | vsess_300 | levels_profile_va.retest_native {"M": 6, "tol": 0.0} | plain60/60 | +376 | -130 | +0.24 | 298 | ok/ok/ok | L6M @1.5 stops +376 / @3 stops +569 |
| 4 | cdr_100 | levels_vwap.break {"n": 3, "k": 0.5} | plain60/60 | +389 | +239 | +0.25 | 419 | ok/ok/ok | L6M @1.5 stops +389 / @3 stops +177 |
| 5 | dib_10000 | book_cancel.canc_follow {"L": 50, "z": 1.0} | plain60/60 | +380 | +430 | +0.24 | 533 | ok/ok/ok | L6M @1.5 stops +380 / @3 stops <=0 or <100 tr |
| 6 | cusum_28 | levels_vwap.break {"n": 3, "k": 0.5} | plain60/60 | +325 | +93 | +0.21 | 452 | ok/ok/ok | L6M @1.5 stops +325 / @3 stops +267 |
| 7 | dib_2000 | book_micro.follow_sm {"L": 200, "z": 2.0, "sm": 3} | plain60/60 | +368 | -27 | +0.24 | 462 | AMBER/ok/ok | L6M @1.5 stops +368 / @3 stops <=0 or <100 tr |
| 8 | kagi_10 | bands_atrchan.fade_ext_native {"clk": 5, "k": 1.0} | plain60/60 | +436 | -278 | +0.28 | 385 | AMBER/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |
| 9 | dlt_400 | structure_libpattern.nr {"n": 4} | plain60/60 | +329 | +16 | +0.21 | 119 | ok/ok/ok | L6M @1.5 stops +329 / @3 stops +328 |
| 10 | cdr_100 | levels_vwap.break {"n": 2, "k": 0.5} | asym20u/10u | +705 | -593 | +0.23 | 243 | AMBER/ok/ok | L6M @1.5 stops +705 / @3 stops +501 |

(a) BARE ranking:

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | dib_240 | momentum_mvote.v3of5_native {"scale": 1.0, "thr": 0.25} | plain60/60 | +616 | +1066 | +0.39 | 777 | ok/ok/ok | bare only (not positive on own-stop) |
| 2 | frenko_40 | book_ofi.follow_sm {"L": 50, "z": 1.0, "sm": 3} | plain60/60 | +446 | +73 | +0.29 | 708 | ok/ok/ok | strong on (b) too |
| 3 | cusum_80 | momentum_cci.zero_native {"len": 30, "lvl": 50} | plain60/60 | +435 | -495 | +0.28 | 441 | ok/ok/ok | bare only (not positive on own-stop) |
| 4 | dchg_28 | bands_regchan.break_linreg {"n": 20, "k": 2.0} | plain60/60 | +381 | -584 | +0.24 | 442 | ok/ok/ok | bare only (not positive on own-stop) |
| 5 | cusum_40 | levels_fib15.break_native {"n": 3, "k": 0.5} | plain60/60 | +300 | +313 | +0.19 | 713 | ok/ok/ok | strong on (b) too |
| 6 | cdr_100 | levels_vwap.break_native {"n": 2, "k": 0.5} | plain60/60 | +323 | +983 | +0.21 | 561 | ok/ok/ok | strong on (b) too |
| 7 | dchg_10 | bands_vwap.walk_native {"clk": 6, "k": 1.0, "N": 2} | plain60/60 | +355 | +530 | +0.23 | 538 | AMBER/ok/ok | bare only (not positive on own-stop) |
| 8 | dlt_400 | structure_libpattern.nr {"n": 4} | plain60/60 | +328 | +14 | +0.21 | 121 | ok/ok/ok | strong on (b) too |
| 9 | dchg_10 | bands_atrchan.break_ext {"n": 40, "atr": 14, "k": 4.0} | plain60/60 | +325 | +43 | +0.21 | 464 | ok/ok/ok | bare only (not positive on own-stop) |
| 10 | kagi_10 | bands_atrchan.break_ext {"n": 40, "atr": 14, "k": 4.0} | plain60/60 | +312 | +37 | +0.20 | 464 | ok/ok/ok | bare only (not positive on own-stop) |

(c) CURRENT-STACK MASK ranking (valid for ADDING a book to today's stack only; information, never the sole reason to shortlist or drop; strong only here = depends on today's stack):

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | cusum_40 | levels_fib15.break_native {"n": 3, "k": 0.5} | plain60/60 | +467 | +418 | +0.30 | 706 | ok/ok/ok | also positive on (b) |
| 2 | dchg_28 | bands_regchan.break_linreg {"n": 20, "k": 2.0} | plain60/60 | +377 | -579 | +0.24 | 440 | ok/ok/ok | depends on today's stack |
| 3 | dib_10000 | book_cancel.canc_follow {"L": 50, "z": 1.0} | plain60/60 | +459 | +227 | +0.29 | 694 | AMBER/ok/ok | also positive on (b) |
| 4 | kagi_20 | book_ofi.follow {"L": 100, "z": 2.0} | plain60/60 | +348 | +426 | +0.22 | 552 | ok/ok/ok | depends on today's stack |
| 5 | cdr_100 | levels_vwap.break {"n": 3, "k": 0.0} | plain60/60 | +317 | +497 | +0.20 | 528 | ok/ok/ok | depends on today's stack |
| 6 | cdr_100 | levels_vwap.break_native {"n": 3, "k": 0.0} | plain60/60 | +317 | +497 | +0.20 | 528 | ok/ok/ok | depends on today's stack |
| 7 | cdr_100 | levels_vwap.break_native {"n": 2, "k": 0.5} | plain60/60 | +364 | +1033 | +0.23 | 554 | ok/ok/AMBER | also positive on (b) |
| 8 | dchg_10 | bands_vwap.walk_native {"clk": 6, "k": 1.0, "N": 2} | plain60/60 | +355 | +530 | +0.23 | 538 | AMBER/ok/ok | depends on today's stack |
| 9 | dlt_400 | structure_libpattern.nr {"n": 4} | plain60/60 | +328 | +14 | +0.21 | 121 | ok/ok/ok | also positive on (b) |
| 10 | cusum_28 | levels_vwap.retest {"M": 10, "tol": 0.5} | plain60/60 | +292 | +776 | +0.19 | 471 | ok/ok/ok | depends on today's stack |

## Top 10 London

(b) OWN-STOP ranking (stack-independent; carries the shortlist):

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | cusum_28 | trend_macd.hist_turn_native {"len": 26, "width": 0.03} | plain60/60 | +744 | +972 | +0.48 | 364 | ok/ok/ok | L6M @1.5 stops +370 / @3 stops +431 |
| 2 | dib_2000 | book_micro.fade {"L": 50, "z": 1.0} | plain60/60 | +618 | +173 | +0.40 | 339 | ok/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |
| 3 | frenko_28 | book_pslope.fade_sm {"L": 50, "z": 2.0, "sm": 3} | plain60/60 | +504 | +632 | +0.32 | 262 | AMBER/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |
| 4 | kagi_14 | book_cancel.canc_follow {"L": 100, "z": 1.0} | plain60/60 | +500 | -828 | +0.32 | 181 | ok/AMBER/AMBER | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |
| 5 | dchg_20 | levels_fib60.false_break {"M": 3, "k": 0.5} | sym15u | +702 | +1290 | +0.23 | 161 | ok/ok/ok | L6M @1.5 stops +623 / @3 stops +67 |
| 6 | dchg_20 | levels_fib60.false_break {"M": 1, "k": 0.0} | sym15u | +702 | +1290 | +0.23 | 161 | ok/ok/ok | L6M @1.5 stops +623 / @3 stops +67 |
| 7 | dchg_20 | levels_fib60.false_break_native {"M": 1, "k": 0.0} | sym15u | +702 | +1290 | +0.23 | 161 | ok/ok/ok | L6M @1.5 stops +623 / @3 stops +67 |
| 8 | dib_2000 | book_micro.fade {"L": 50, "z": 1.0} | plain60/60 | +334 | -346 | +0.21 | 176 | ok/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |
| 9 | dib_240 | xmarket_nkd.follow {"w": 1, "thr": 1.0} | plain60/60 | +441 | +482 | +0.28 | 250 | ok/AMBER/ok | L6M @1.5 stops +95 / @3 stops <=0 or <100 tr |
| 10 | cusum_40 | xmarket_fx.with_6E {"w": 15, "thr": 2.0} | plain60/60 | +323 | +1029 | +0.21 | 212 | ok/ok/ok | L6M @1.5 stops +323 / @3 stops +88 |

(a) BARE ranking:

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | dlt_150 | bands_regchan.fade_linreg_native {"clk": 10, "k": 2.0} | plain60/60 | +471 | -91 | +0.30 | 150 | ok/ok/ok | bare only (not positive on own-stop) |
| 2 | drb_1200 | bands_regchan.fade_linreg {"n": 20, "k": 2.0} | plain60/60 | +491 | +620 | +0.31 | 227 | ok/ok/AMBER | strong on (b) too |
| 3 | cdr_250 | levels_vwap_bands.reject {"tol": 0.0, "conf": "close"} | plain60/60 | +352 | +384 | +0.23 | 446 | ok/ok/ok | strong on (b) too |
| 4 | cdr_250 | levels_vwap_bands.reject_native {"tol": 0.0, "conf": "close"} | plain60/60 | +352 | +384 | +0.23 | 446 | ok/ok/ok | strong on (b) too |
| 5 | dlt_100 | levels_vwap_bands.false_break {"M": 1, "k": 0.0} | plain60/60 | +395 | +156 | +0.25 | 315 | ok/ok/AMBER | strong on (b) too |
| 6 | dlt_100 | levels_vwap_bands.false_break_native {"M": 1, "k": 0.0} | plain60/60 | +395 | +156 | +0.25 | 315 | ok/ok/AMBER | strong on (b) too |
| 7 | dib_2000 | book_micro.fade_native {"L": 900, "z": 1.0} | plain60/60 | +331 | +596 | +0.21 | 741 | ok/ok/ok | bare only (not positive on own-stop) |
| 8 | drb_240 | barnative_delta.run {"n": 3, "thr": 0.0} | plain60/60 | +405 | -248 | +0.26 | 785 | ok/AMBER/ok | strong on (b) too |
| 9 | dib_2000 | book_imb.delta_fade {"lv": 1, "thr": 0.2} | plain60/60 | +311 | +686 | +0.20 | 801 | ok/ok/ok | strong on (b) too |
| 10 | dchg_20 | barnative_profile.va_fade {"va": 0.5, "buf": 0.0} | plain60/60 | +304 | +505 | +0.20 | 189 | ok/ok/ok | bare only (not positive on own-stop) |

(c) CURRENT-STACK MASK ranking (valid for ADDING a book to today's stack only; information, never the sole reason to shortlist or drop; strong only here = depends on today's stack):

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | dlt_70 | levels_zones.reject {"tol": 1.0, "conf": "body"} | plain60/60 | +674 | -435 | +0.43 | 182 | ok/ok/ok | also positive on (b) |
| 2 | dib_2000 | book_micro.fade {"L": 50, "z": 1.0} | plain60/60 | +647 | +578 | +0.41 | 563 | ok/ok/ok | also positive on (b) |
| 3 | dlt_70 | levels_zones.reject {"tol": 0.5, "conf": "body"} | plain60/60 | +569 | -575 | +0.36 | 156 | ok/ok/ok | depends on today's stack |
| 4 | dib_2000 | book_imb.delta_fade {"lv": 1, "thr": 0.2} | plain60/60 | +452 | +657 | +0.29 | 293 | ok/ok/ok | depends on today's stack |
| 5 | dlt_150 | bands_regchan.fade_linreg_native {"clk": 10, "k": 2.0} | plain60/60 | +373 | -316 | +0.24 | 130 | ok/ok/ok | depends on today's stack |
| 6 | dib_6000 | xmarket_rates.with_ZB {"w": 1, "thr": 1.0} | plain60/60 | +355 | -18 | +0.23 | 431 | ok/ok/ok | depends on today's stack |
| 7 | dlt_70 | levels_session_hl.false_break {"M": 2, "k": 0.5} | plain60/60 | +465 | +392 | +0.30 | 146 | ok/AMBER/AMBER | depends on today's stack |
| 8 | dchg_14 | trend_heikin.run {"len": 5, "width": 0.25} | sym15u | +837 | +418 | +0.27 | 217 | AMBER/ok/ok | also positive on (b) |
| 9 | dchg_14 | trend_heikin.run_native {"len": 5, "width": 0.25} | sym15u | +697 | +551 | +0.22 | 214 | ok/ok/ok | depends on today's stack |
| 10 | dib_2000 | manual_macd.histturn {"f": 24, "s": 52, "g": 18} | plain60/60 | +337 | +1018 | +0.22 | 578 | ok/ok/ok | depends on today's stack |

## Top 10 NY AM

(b) OWN-STOP ranking (stack-independent; carries the shortlist):

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | cusum_20 | book_ofi.follow {"L": 200, "z": 2.0} | plain60/60 | +2026 | +333 | +1.30 | 496 | AMBER/AMBER/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops +579 |
| 2 | kagi_14 | bands_atrchan.break_ext_native {"clk": 10, "k": 2.0} | plain60/60 | +1283 | +766 | +0.82 | 541 | ok/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |
| 3 | frenko_40 | book_ofi.follow_sm {"L": 200, "z": 2.0, "sm": 3} | plain60/60 | +1038 | -54 | +0.67 | 345 | ok/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |
| 4 | dchg_28 | momentum_willr.break_native {"len": 14, "lvl": 10} | plain60/60 | +1004 | +498 | +0.64 | 661 | ok/ok/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops +368 |
| 5 | frenko_28 | book_ofi.follow_sm {"L": 50, "z": 2.0, "sm": 3} | plain60/60 | +1256 | +74 | +0.81 | 435 | AMBER/AMBER/ok | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |
| 6 | cusum_28 | manual_cci.go {"len": 34, "lvl": 100} | plain60/60 | +1300 | +308 | +0.83 | 523 | AMBER/ok/AMBER | L6M @1.5 stops +1060 / @3 stops <=0 or <100 tr |
| 7 | dib_6000 | tape_block.b10_follow_sm {"L": 50, "z": 1.0, "sm": 3} | plain60/60 | +910 | -72 | +0.58 | 594 | ok/ok/ok | L6M @1.5 stops +351 / @3 stops <=0 or <100 tr |
| 8 | cusum_20 | tape_block.b25_follow {"L": 100, "z": 1.5} | plain60/60 | +878 | -347 | +0.56 | 503 | ok/ok/ok | L6M @1.5 stops +1333 / @3 stops +1239 |
| 9 | drb_400 | bands_bollinger.break_native {"clk": 20, "k": 1.5} | plain60/60 | +853 | +31 | +0.55 | 762 | ok/ok/ok | L6M @1.5 stops +1429 / @3 stops +1061 |
| 10 | dchg_28 | bands_donchian.break {"n": 10, "buf": 0.0} | plain60/60 | +1017 | -15 | +0.65 | 671 | ok/ok/AMBER | L6M @1.5 stops +1181 / @3 stops +570 |

(a) BARE ranking:

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | frenko_40 | book_ofi.follow_sm {"L": 200, "z": 2.0, "sm": 3} | plain60/60 | +1751 | +147 | +1.12 | 582 | AMBER/AMBER/ok | strong on (b) too |
| 2 | dchg_28 | book_ofi.follow_sm {"L": 50, "z": 1.0, "sm": 3} | plain60/60 | +1370 | -2321 | +0.88 | 1270 | AMBER/ok/ok | strong on (b) too |
| 3 | cusum_20 | book_ofi.follow_native {"L": 3600, "z": 2.0} | plain60/60 | +1408 | +528 | +0.90 | 1026 | AMBER/ok/ok | bare only (not positive on own-stop) |
| 4 | dib_15000 | structure_fvg.cont {"w": 0.75} | plain60/60 | +1081 | +455 | +0.69 | 495 | ok/ok/ok | bare only (not positive on own-stop) |
| 5 | drb_2000 | levels_vwap.break_native {"n": 3, "k": 0.5} | plain60/60 | +1148 | +991 | +0.74 | 753 | AMBER/ok/AMBER | bare only (not positive on own-stop) |
| 6 | dlt_100 | bands_bollinger.walk_native {"clk": 10, "k": 2.0, "N": 2} | plain60/60 | +1255 | +1563 | +0.80 | 502 | AMBER/ok/AMBER | bare only (not positive on own-stop) |
| 7 | dchg_40 | tape_block.b10_follow_sm {"L": 50, "z": 1.0, "sm": 3} | plain60/60 | +1077 | +289 | +0.69 | 816 | ok/AMBER/AMBER | bare only (not positive on own-stop) |
| 8 | dchg_14 | momentum_mvote.v4of5 {"scale": 0.25, "thr": 0.25} | sym15u | +1910 | +1158 | +0.61 | 491 | ok/ok/AMBER | strong on (b) too |
| 9 | dlt_70 | levels_vwap.break {"n": 3, "k": 0.5} | asym15u/30u | +1594 | -272 | +0.51 | 346 | ok/ok/ok | strong on (b) too |
| 10 | dib_240 | bands_avwap0930.walk_0930 {"minbars": 20, "k": 1.5, "N": 2} | plain60/60 | +1035 | -283 | +0.66 | 886 | ok/ok/AMBER | strong on (b) too |

(c) CURRENT-STACK MASK ranking (valid for ADDING a book to today's stack only; information, never the sole reason to shortlist or drop; strong only here = depends on today's stack):

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | cusum_20 | book_ofi.follow {"L": 200, "z": 2.0} | plain60/60 | +1493 | +667 | +0.96 | 633 | ok/ok/ok | also positive on (b) |
| 2 | dchg_40 | manual_macd.sigcross_native {"f": 5, "s": 13, "g": 4} | plain60/60 | +1357 | -639 | +0.87 | 604 | ok/ok/ok | depends on today's stack |
| 3 | kagi_20 | book_ofi.follow_native {"L": 900, "z": 2.0} | plain60/60 | +1199 | -192 | +0.77 | 660 | ok/ok/ok | depends on today's stack |
| 4 | dchg_14 | tape_block.b10_follow_sm {"L": 100, "z": 1.5, "sm": 3} | plain60/60 | +1288 | -231 | +0.83 | 817 | AMBER/ok/ok | also positive on (b) |
| 5 | dib_6000 | book_ofi.follow_native {"L": 3600, "z": 2.0} | plain60/60 | +1400 | -564 | +0.90 | 612 | AMBER/AMBER/ok | also positive on (b) |
| 6 | dib_6000 | tape_block.b10_follow_sm {"L": 50, "z": 1.0, "sm": 3} | plain60/60 | +1302 | +460 | +0.83 | 800 | AMBER/ok/ok | also positive on (b) |
| 7 | dchg_14 | tape_block.b25_follow {"L": 100, "z": 1.5} | plain60/60 | +1355 | +25 | +0.87 | 665 | ok/AMBER/ok | also positive on (b) |
| 8 | dchg_28 | levels_vwap.break {"n": 3, "k": 0.5} | plain60/60 | +892 | -280 | +0.57 | 538 | ok/ok/ok | depends on today's stack |
| 9 | drb_700 | bands_atrchan.break_ext {"n": 10, "atr": 14, "k": 3.0} | sym8u | +1187 | -66 | +0.56 | 414 | ok/ok/ok | depends on today's stack |
| 10 | dib_25000 | tape_block.b10_follow_sm {"L": 100, "z": 1.5, "sm": 3} | plain60/60 | +981 | +494 | +0.63 | 259 | AMBER/ok/ok | also positive on (b) |

## Top 10 NY PM

(b) OWN-STOP ranking (stack-independent; carries the shortlist):

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | dlt_70 | bands_regchan.break_linreg {"n": 10, "k": 1.5} | sym15u | +2155 | +808 | +0.69 | 177 | AMBER/AMBER/AMBER | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |
| 2 | drb_1200 | bands_regchan.break_linreg {"n": 20, "k": 2.0} | plain60/60 | +972 | +77 | +0.62 | 288 | ok/ok/AMBER | L6M @1.5 stops +1000 / @3 stops +996 |
| 3 | cdr_250 | xmarket_fx.with_6J {"w": 1, "thr": 1.0} | sym15u | +1837 | +1382 | +0.59 | 170 | ok/ok/AMBER | L6M @1.5 stops <=0 or <100 tr / @3 stops <=0 or <100 tr |
| 4 | dchg_14 | bands_donchian.fade {"n": 10, "buf": 0.0} | plain60/60 | +798 | +30 | +0.51 | 209 | AMBER/ok/ok | L6M @1.5 stops +490 / @3 stops <=0 or <100 tr |
| 5 | dchg_20 | trend_heikin.flip_after_run_native {"len": 8, "width": 0.25} | plain60/60 | +591 | +394 | +0.38 | 303 | ok/ok/ok | L6M @1.5 stops +418 / @3 stops +864 |
| 6 | dib_3500 | book_wall.near_fade {"m": 4, "d": 4} | plain60/60 | +535 | -54 | +0.34 | 318 | ok/ok/ok | L6M @1.5 stops +822 / @3 stops +362 |
| 7 | drb_700 | trend_macd.hist_turn_native {"len": 12, "width": 0.01} | plain60/60 | +619 | +100 | +0.40 | 310 | ok/ok/ok | L6M @1.5 stops +161 / @3 stops <=0 or <100 tr |
| 8 | cusum_28 | xmarket_ym.diverge {"w": 30} | sym30u | +1278 | +774 | +0.41 | 175 | ok/AMBER/ok | L6M @1.5 stops +593 / @3 stops +683 |
| 9 | cusum_28 | xmarket_ym.diverge {"w": 30} | asym15u/30u | +1278 | +774 | +0.41 | 175 | AMBER/ok/ok | L6M @1.5 stops +593 / @3 stops +683 |
| 10 | drb_400 | bands_atrchan.break_ext {"n": 20, "atr": 14, "k": 2.0} | plain60/60 | +508 | +30 | +0.33 | 368 | ok/ok/ok | L6M @1.5 stops +363 / @3 stops <=0 or <100 tr |

(a) BARE ranking:

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | dib_400 | trend_supertrend.native {"len": 14, "width": 3.0} | plain60/60 | +803 | +727 | +0.51 | 1033 | ok/ok/ok | bare only (not positive on own-stop) |
| 2 | dib_400 | trend_supertrend.plain {"len": 14, "width": 3.0} | plain60/60 | +757 | +1253 | +0.49 | 1013 | ok/ok/ok | strong on (b) too |
| 3 | dchg_20 | trend_heikin.flip_after_run_native {"len": 8, "width": 0.25} | plain60/60 | +882 | +731 | +0.57 | 640 | ok/AMBER/ok | strong on (b) too |
| 4 | drb_400 | bands_atrchan.break_ext {"n": 20, "atr": 14, "k": 2.0} | plain60/60 | +784 | +871 | +0.50 | 982 | ok/ok/ok | strong on (b) too |
| 5 | dib_240 | bands_regchan.fade_stderr {"n": 10, "k": 1.5} | plain60/60 | +605 | +1459 | +0.39 | 1133 | ok/ok/ok | bare only (not positive on own-stop) |
| 6 | dib_25000 | book_cancel.net_follow_native {"L": 900, "z": 1.0} | plain60/60 | +647 | +685 | +0.41 | 701 | ok/ok/ok | strong on (b) too |
| 7 | dib_3500 | barnative_speed.burst_fade {"len": 10, "r": 0.4} | plain60/60 | +811 | +1354 | +0.52 | 967 | ok/ok/AMBER | bare only (not positive on own-stop) |
| 8 | dib_2000 | book_ofi.follow_native {"L": 1800, "z": 1.5} | plain60/60 | +571 | -1305 | +0.37 | 989 | ok/ok/ok | bare only (not positive on own-stop) |
| 9 | dlt_70 | levels_vwap.break {"n": 1, "k": 0.5} | plain60/60 | +743 | +206 | +0.48 | 378 | ok/ok/AMBER | bare only (not positive on own-stop) |
| 10 | cdr_160 | momentum_stoch.revert_native {"len": 5, "lvl": 15} | plain60/60 | +527 | +675 | +0.34 | 919 | ok/ok/ok | strong on (b) too |

(c) CURRENT-STACK MASK ranking (valid for ADDING a book to today's stack only; information, never the sole reason to shortlist or drop; strong only here = depends on today's stack):

| rank | bar row | module.variant params | bracket | L6M pts | L3M pts | R/week | trades L6M | prior yrs (R flags 23/24/25) | flag |
|---|---|---|---|---|---|---|---|---|---|
| 1 | dchg_20 | book_ofi.follow_sm {"L": 100, "z": 1.5, "sm": 3} | plain60/60 | +770 | -152 | +0.49 | 470 | ok/ok/ok | depends on today's stack |
| 2 | kagi_20 | book_ofi.follow_sm {"L": 100, "z": 1.5, "sm": 3} | plain60/60 | +765 | -155 | +0.49 | 470 | ok/ok/ok | depends on today's stack |
| 3 | cdr_100 | bands_regchan.break_linreg {"n": 10, "k": 1.5} | plain60/60 | +743 | -49 | +0.48 | 565 | ok/ok/ok | also positive on (b) |
| 4 | cusum_56 | tape_vpin.fade {"N": 10, "thr": 0.05} | plain60/60 | +709 | -11 | +0.45 | 218 | ok/AMBER/ok | depends on today's stack |
| 5 | dlt_100 | bands_regchan.break_stderr_native {"clk": 10, "k": 2.0} | plain60/60 | +568 | +415 | +0.36 | 464 | ok/ok/ok | depends on today's stack |
| 6 | dchg_20 | book_ofi.norm_fade {"L": 200, "z": 2.0} | plain60/60 | +584 | +26 | +0.37 | 268 | ok/ok/ok | depends on today's stack |
| 7 | kagi_20 | book_ofi.norm_fade {"L": 200, "z": 2.0} | plain60/60 | +581 | +24 | +0.37 | 268 | ok/ok/ok | depends on today's stack |
| 8 | dchg_20 | trend_heikin.flip_after_run_native {"len": 8, "width": 0.25} | plain60/60 | +550 | +770 | +0.35 | 380 | ok/ok/ok | also positive on (b) |
| 9 | dlt_70 | bands_regchan.break_linreg {"n": 10, "k": 1.5} | plain60/60 | +503 | -725 | +0.32 | 577 | ok/ok/ok | also positive on (b) |
| 10 | dib_10000 | tape_run.runv_fade {"thr": 100} | plain60/60 | +614 | +745 | +0.39 | 275 | ok/AMBER/ok | depends on today's stack |

## Honest limits

- Rankings are best-of-many on the last 6 months; the selection-corrected best-pick null (phase 2b) is not applied yet to any row.
- Screen numbers are naked triggers; the engine rows (NEW_BOOK_ENGINE*.md) show layers and account rules change results both ways.

<!-- ENGINE_PLAN_ETAS -->
**Phase ETAs (W-PLAN, from ENGINE_PLAN.md section 11, 2026-11-18 18:39Z):**

- phase 1 pass 1: 139421 jobs left at 5116/h = 27.3 h (rate from the grid line above; sums over machines).
- phase 1 pass 2: 26334 jobs left at 503/h = 52.4 h at today's allocation.
- phases 2-3 engine, N = 6 passing cells per session: 30400 set-months = 31 h at the current fleet (973/h) or 8.5 h with A and B engine-ready (projected 3589/h). Full table: ENGINE_PLAN.md section 11.
- N is not a limit (order 1845Z): N only sizes the estimate; engine capacity decides the ORDER, never whether a passing cell is tested.
<!-- /ENGINE_PLAN_ETAS -->
