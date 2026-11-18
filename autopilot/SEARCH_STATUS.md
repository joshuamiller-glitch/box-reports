# SEARCH_STATUS - full-search programme (plan 1722Z: no Globex deadline), W-GRIDOPS, refreshed 2026-11-18 17:25Z

Plain words. Data end 2026-11-15 (NQ). Research only, no spend. Phases: 1 finish the whole search -> 2 prove it is not luck (30 controls, selection-corrected null, trust) -> 3 gates/layers one by one then jointly -> 4 D8 spec. Every number below is a screen-level number unless it says engine.

## Phase 1 - progress (the grid is not split by session: one job = one bar row x one trigger module x one tag; every session reads the same results, so the percentages below are the same for NY AM, NY PM, London and Asia)

| item | done | todo | jobs/hour (last 60 min) | ETA at that rate |
|---|---|---|---|---|
| pass 1, all tags (real + random-entry nulls 1/2 + extra null draws) | 63567 result files | 80818 jobs | 1449 | 55.8 h |
| pass 2 (family cells, exits a2, top cells) | n/a | 25951 (a top cells 2387, a2 exit families 5840, c family cells 17724) | 925 | 28.1 h |

Pass-1 results on disk by tag: real 25281, null draw 1 17546, null draw 2 17467, extra draws (3-25) 2698 files. Pass-1 results still waiting for their pass-2 upgrade: real 15932.

Machine state: server 2 load 93.09 84.11 81.69 (64 threads); grid workers 60 (59 computing, avg cpu 55%); engine workers 24; forward-path tables built 166 of 322 rows.


## Blocked / cannot run (listed, not skipped silently)

Failed jobs leave an error stub that the loop retries after 4 hours (older stubs are retried automatically). Error files on disk: {'real': 355, 'p1real': 1713, 'p1rand1': 1561, 'p1rand2': 1526, 'p1gridops_test': 1}.

| module | failures (files) | why |
|---|---|---|
| trig_book_ofi | 288 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_cancel | 288 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_ice | 288 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_queue | 288 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_pslope | 288 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_dwm | 288 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_imb | 288 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_micro | 288 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_thin | 288 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_wall | 288 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_book_sweep | 288 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_xmarket_fast | 286 | all signal calls raised (cause needs a test) |
| trig_tape_run | 283 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_tape_block | 282 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_tape_unfinished | 282 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_tape_stack | 282 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_tape_sizemix | 281 | rows with no book/flow feature store (feat_c) or level feature (feat_d) on server 2; see GRIDOPS_BLOCKED.md for the row list |
| trig_levels_sd5 | 19 | all signal calls raised (cause needs a test) |
| trig_levels_sd15 | 19 | all signal calls raised (cause needs a test) |
| trig_levels_sd60 | 19 | all signal calls raised (cause needs a test) |
| trig_levels_fib60 | 19 | all signal calls raised (cause needs a test) |
| trig_levels_sdx5 | 19 | all signal calls raised (cause needs a test) |
| trig_levels_fib5 | 19 | all signal calls raised (cause needs a test) |
| trig_levels_sdx15 | 19 | all signal calls raised (cause needs a test) |
| trig_levels_fib15 | 19 | all signal calls raised (cause needs a test) |

## Phase 2 / 3 (running in parallel, from the 1722Z order)

- NY leads to the full standard: WP10 (NY PM money flow, keep K7 and add) and XA3 (NY AM VWAP retest on 5000-tick): autopilot/NEW_BOOK_ENGINE.md. London replacement programme: NEW_BOOK_ENGINE_LONDON.md. Near-target K7 lock controls: DS3_NEAR_TARGET.md. ORB fade controls: DS3_ORB_FADE_LEAD.md.
- Shortlist (bare, equal risk) and its trust audit: NEW_BOOK_SHORTLIST.md. Look-ahead gate for every reversal-type bar: BAR_LOOKAHEAD_GATE.md (all passed).
- Account-rule scoring (DAY-DONE mask from the JL3 day-state): in progress by W-DAYMASK; the side-by-side ranking appears below when its file exists.

## Clock order (addendum 1731Z): sessions are decided Asia -> London -> NY AM -> NY PM

Phase 1 is NOT split by session (one grid job feeds all four sessions), so the grid cores cannot be re-ordered by session without cost; what follows the clock order is the scoring and the later phases: scoring/ranking runs Asia first; in phases 3-4 each session is decided on the exact engine after the earlier session is final. Asia is NOT add-only: replace / add / mixed with a higher bar (drawdown first AND dollars, last 6 and 3 months, no red prior year, 30 controls, selection-corrected test).

## Top 10 Asia

(b) OWN-STOP ranking (stack-independent; carries the shortlist):

- not available yet (W-DAYMASK file autopilot/DAYMASK_RANK.md)

(a) BARE ranking:

- 1 | tm180 (NR, level) | levels_vwap.break_native {"n": 3, "k": 0.5} [both] | plain60/60: 60/60 | L6M +465 (1.00 lots) | L3M +0.422 / +0.606 / +0.377 / +0.051
- 2 | cusum_10 (NR) | momentum_cci.brk {"len": 30, "lvl": 200} [both] | plain60/60: 60/60 | L6M +485 (1.00 lots) | L3M +0.481 / +0.342 / +0.416 / +0.748
- 3 | time_m_7 (NR) | xmarket_rty.confirm {"w": 30} [both] | plain60/60: 60/60 | L6M +461 (1.00 lots) | L3M +0.477 / +0.348 / +0.342 / +0.548
- 4 | tick_300 (NR) | momentum_mvote.v3of5 {"scale": 1.0, "thr": 0.25} [both] | plain60/60: 60/60 | L6M +386 (1.00 lots) | L3M +0.334 / +0.673 / +0.501 / +0.423
- 5 | vsess_30 (NR) | bands_atrchan.break_ema_native {"clk": 5, "k": 1.5} [both] | plain60/60: 60/60 | L6M +424 (1.00 lots) | L3M +0.304 / +0.449 / +0.508 / +0.363
- 6 | vsess_30 (NR) | bands_envelope.break_ema_native {"clk": 10, "k": 1.5} [both] | plain60/60: 60/60 | L6M +424 (1.00 lots) | L3M +0.304 / +0.449 / +0.508 / +0.363
- 7 | vrb_400 (NR, level) | levels_swsr15.break_native {"n": 3, "k": 0.5} [both] | plain60/60: 60/60 | L6M +476 (1.00 lots) | L3M +0.300 / +0.312 / +0.536 / +0.436
- 8 | vol_750 (NR) | trend_libstack.ema_stack {"set": "5-13-34"} [both] | plain60/60: 60/60 | L6M +389 (1.00 lots) | L3M +0.406 / +0.299 / +0.431 / +0.222
- 9 | rng_20 (NR) | momentum_mvote.v3of5 {"scale": 1.0, "thr": 0.25} [both] | plain60/60: 60/60 | L6M +365 (1.00 lots) | L3M +0.330 / +0.431 / +0.295 / +0.301
- 10 | dib_1200 (NR, level) | levels_vwap.break_native {"n": 2, "k": 0.25} [both] | plain60/60: 60/60 | L6M +352 (1.00 lots) | L3M +0.316 / +0.493 / +0.301 / +0.780
  (bare equal-risk list from NEW_BOOK_SHORTLIST.md)

(c) CURRENT-STACK MASK ranking (valid for ADDING a book to today's stack only; information, never the sole reason to shortlist or drop; strong only here = depends on today's stack):

- not available yet (W-DAYMASK file autopilot/DAYMASK_RANK.md)

## Top 10 London

(b) OWN-STOP ranking (stack-independent; carries the shortlist):

- not available yet (W-DAYMASK file autopilot/DAYMASK_RANK.md)

(a) BARE ranking:

- 1 | dlt_70 (NR, level) | levels_zones.reject {"tol": 1.0, "conf": "body"} [both] | plain60/60: 60/60 | L6M +741 (1.00 lots) | L3M +0.540 / +0.439 / +0.499 / +0.351
- 2 | tm420 (NR) | momentum_stoch.zone_break {"len": 5, "lvl": 70} [both] | plain60/60: 60/60 | L6M +456 (1.00 lots) | L3M +0.498 / +0.490 / +0.637 / +0.440
- 3 | tm20 (NR) | xmarket_rates.with_ZN {"w": 1, "thr": 1.0} [long] | plain60/60: 60/60 | L6M +439 (1.00 lots) | L3M +0.361 / +0.337 / +0.592 / +0.672
- 4 | tm15 (NR) | trend_ma_hma.cross {"len": 21, "width": 3, "hyst": 0.0} [both] | asym10u/20u: 41/82 | L6M +383 (1.45 lots) | L3M +0.696 / +1.025 / +0.474 / -0.723
- 5 | tm30 (NR) | bands_bollinger.fade {"n": 10, "k": 1.5} [both] | asym15u/30u: 92/120 | L6M +453 (0.65 lots) | L3M +0.364 / +0.319 / +0.327 / +0.061
- 6 | dol_350 (NR, level) | levels_sdx3.rej_zone {"d": "A", "F": 0, "tgt": "opp"} [both] | plain60/60: 60/60 | L6M +378 (1.00 lots) | L3M +0.346 / +0.361 / +0.306 / -0.243
- 7 | vrb_400 (NR) | trend_ma_t3.cross {"len": 4, "width": 2, "hyst": 0.0} [both] | plain60/60: 60/60 | L6M +398 (1.00 lots) | L3M +0.350 / +0.392 / +0.305 / -0.535
- 8 | dlt_150 (NR) | bands_regchan.fade_linreg_native {"clk": 10, "k": 2.0} [both] | plain60/60: 60/60 | L6M +362 (1.00 lots) | L3M +0.386 / +0.379 / +0.365 / +0.104
- 9 | vsess_600 (NR) | xmarket_rates.with_ZN {"w": 1, "thr": 1.0} [both] | plain60/60: 60/60 | L6M +357 (1.00 lots) | L3M +0.321 / +0.330 / +0.412 / +0.581
- 10 | vrb_700 (NR) | book_dwm.dev_fade {"L": 50, "z": 1.0} [both] | plain60/60: 60/60 | L6M +467 (1.00 lots) | L3M +0.372 / +0.320 / +0.294 / +0.053
  (bare equal-risk list from NEW_BOOK_SHORTLIST.md)

(c) CURRENT-STACK MASK ranking (valid for ADDING a book to today's stack only; information, never the sole reason to shortlist or drop; strong only here = depends on today's stack):

- not available yet (W-DAYMASK file autopilot/DAYMASK_RANK.md)

## Top 10 NY AM

(b) OWN-STOP ranking (stack-independent; carries the shortlist):

- not available yet (W-DAYMASK file autopilot/DAYMASK_RANK.md)

(a) BARE ranking:

- 1 | frenko_40 (REV) | book_ofi.follow_sm {"L": 200, "z": 2.0, "sm": 3} [both] | plain60/60: 60/60 | L6M +1346 (1.00 lots) | L3M +0.853 / +0.921 / +1.427 / +0.378
- 2 | renko_10 (REV) | momentum_mvote.v3of5_native {"scale": 0.25, "thr": 0.25} [both] | plain60/60: 60/60 | L6M +1001 (1.00 lots) | L3M +1.069 / +0.876 / +0.894 / -0.145
- 3 | tick_5000 (NR, level) | levels_vwap.retest_native {"M": 6, "tol": 0.5} [both] | plain60/60: 60/60 | L6M +1264 (1.00 lots) | L3M +0.754 / +0.839 / +0.807 / +0.471
- 4 | pnf_7 (REV) | pullback_st.st {"st_mult": 2.0, "ema": 14, "arm": 10} [both] | plain60/60: 60/60 | L6M +1172 (1.00 lots) | L3M +0.989 / +0.707 / +0.761 / +0.086
- 5 | kagi_28 (REV) | book_ofi.follow_sm {"L": 50, "z": 1.0, "sm": 3} [both] | plain60/60: 60/60 | L6M +1046 (1.00 lots) | L3M +0.694 / +1.249 / +1.157 / +0.476
- 6 | renko_20 (REV) | trend_libstack.ema_hold {"len": 13, "hold": 3} [both] | plain60/60: 60/60 | L6M +804 (1.00 lots) | L3M +0.901 / +0.728 / +0.765 / -0.740
- 7 | rng_14 (NR) | tape_delta.follow_native {"L": 3600, "z": 1.0} [both] | plain60/60: 60/60 | L6M +1062 (1.00 lots) | L3M +0.669 / +0.669 / +0.720 / +0.116
- 8 | pnf_10 (REV, level) | levels_sdx_rng28.break {"d": "E", "F": 9, "n": 1} [both] | plain60/60: 60/60 | L6M +832 (1.00 lots) | L3M +0.667 / +1.014 / +0.935 / +0.738
- 9 | dol_6000 (NR, level) | levels_vwap.reject_native {"tol": 1.0, "conf": "body"} [both] | plain60/60: 60/60 | L6M +843 (1.00 lots) | L3M +0.652 / +0.741 / +0.678 / +0.664
- 10 | tick_5000 (NR, level) | levels_round.retest_native {"M": 10, "tol": 0.5} [both] | plain60/60: 60/60 | L6M +1059 (1.00 lots) | L3M +0.625 / +0.623 / +0.672 / +0.625
  (bare equal-risk list from NEW_BOOK_SHORTLIST.md)

(c) CURRENT-STACK MASK ranking (valid for ADDING a book to today's stack only; information, never the sole reason to shortlist or drop; strong only here = depends on today's stack):

- not available yet (W-DAYMASK file autopilot/DAYMASK_RANK.md)

## Top 10 NY PM

(b) OWN-STOP ranking (stack-independent; carries the shortlist):

- not available yet (W-DAYMASK file autopilot/DAYMASK_RANK.md)

(a) BARE ranking:

- 1 | dib_400 (NR) | tape_libvol.cmf {"len": 10} [both] | plain60/60: 60/60 | L6M +891 (1.00 lots) | L3M +0.721 / +0.962 / +0.712 / -0.345
- 2 | tm1800 (NR) | xmarket_ym.follow {"w": 5, "thr": 1.0} [both] | plain60/60: 60/60 | L6M +754 (1.00 lots) | L3M +0.943 / +0.716 / +1.155 / +0.156
- 3 | tm900 (NR) | xmarket_es.follow {"w": 5, "thr": 1.0} [both] | plain60/60: 60/60 | L6M +918 (1.00 lots) | L3M +0.659 / +0.836 / +0.622 / +0.059
- 4 | vrb_700 (NR) | momentum_libosc.stochrsi {"len": 21, "lvl": 20} [both] | plain60/60: 60/60 | L6M +837 (1.00 lots) | L3M +0.603 / +0.869 / +0.621 / +0.039
- 5 | time_s_20 (NR) | bands_atrchan.break_ext {"n": 10, "atr": 14, "k": 2.0} [both] | plain60/60: 60/60 | L6M +833 (1.00 lots) | L3M +1.048 / +0.622 / +0.599 / -0.164
- 6 | tm10 (NR) | manual_macd.sigcross {"f": 19, "s": 39, "g": 9} [both] | asym10u/20u: 55/110 | L6M +687 (1.09 lots) | L3M +0.563 / +0.785 / +1.352 / -0.726
- 7 | dol_350 (NR) | trend_adx_di.di_cross {"len": 7, "width": 15} [both] | plain60/60: 60/60 | L6M +777 (1.00 lots) | L3M +0.700 / +0.555 / +0.587 / +0.286
- 8 | time_s_30 (NR) | structure_libpattern.nr {"n": 7} [both] | plain60/60: 60/60 | L6M +659 (1.00 lots) | L3M +0.621 / +1.204 / +0.529 / +0.233
- 9 | dol_500 (NR, level) | levels_fibr_dev.break_native {"n": 2, "k": 0.25} [short] | plain60/60: 60/60 | L6M +572 (1.00 lots) | L3M +0.347 / +0.338 / +0.349 / +0.021
- 10 | dlt_70 (NR, level) | levels_vwap.break {"n": 1, "k": 0.5} [both] | plain60/60: 60/60 | L6M +571 (1.00 lots) | L3M +0.549 / +0.423 / +0.338 / -0.190
  (bare equal-risk list from NEW_BOOK_SHORTLIST.md)

(c) CURRENT-STACK MASK ranking (valid for ADDING a book to today's stack only; information, never the sole reason to shortlist or drop; strong only here = depends on today's stack):

- not available yet (W-DAYMASK file autopilot/DAYMASK_RANK.md)

## Honest limits

- Rankings are best-of-many on the last 6 months; the selection-corrected best-pick null (phase 2b) is not applied yet to any row.
- Screen numbers are naked triggers; the engine rows (NEW_BOOK_ENGINE*.md) show layers and account rules change results both ways.
