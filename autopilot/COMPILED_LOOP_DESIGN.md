# COMPILED_LOOP_DESIGN (W-COMPILED, order 1337Z item 3) - written 14:2xZ, research only
Prereg: PREREG_COMPILED.md sha256:104c01a4d075e423 (DECISIONS.md). Code: code/th_compiled/ (fc_scan.py, fc_launch.py, classify.py, timing.py, id_comp.py). Nothing is switched in any queue; FL_COMPILED is opt-in and OFF.

## 1. Tools available (checked on all four hosts)
numba 0.67.0 + numpy 2.5.3 + llvmlite 0.49.0 in the venv on box 1, Dallas, Frankfurt, Singapore (identical); gcc everywhere; Python.h only on box 1 and Dallas (no python3.12 headers on Frankfurt/Singapore => a Cython / C-extension build would not compile there). Route: NUMBA (no install, no root, no spend).

## 2. Where the time really goes (fast path ON = FL_FAST+FL_NEXT; Asia ADD TL3_ASI_L753bf92a_ADD 202608, box 1, 7.52 M prints, 624 trades)
cProfile exaggerates small calls (243 s vs ~100 s CPU plain), so the table below uses perf_counter around the real base on_print (classify.py), split by what each print is:
| class of print (decided by the same predicate as P10 chainskip + gates) | prints | share | time in base on_print | ns / print |
|---|---|---|---|---|
| FIRST print of a second with a book in trade (the once-per-second rule-chain evaluation) | 691,420 | 9.2 % | 46.7 s (~47 % of the whole run's ~100 s CPU) | 67,500 |
| provably no-op print, all books idle | 4,493,744 | 59.7 % | 11.3 s | 2,500 |
| provably no-op print, a book in trade (P10 skip) | 1,876,200 | 24.9 % | 10.1 s | 5,400 |
| armed / lock 2 s / flat 5 s / poll 300 s / touches (everything else) | ~460,000 | 6.2 % | ~5.5 s | 3,000-30,000 |
Same shape on NY AM RK7 TL3_NYE_L01811caa_RK7 202608 (84 % of prints provably no-op; 10.2 % chain_second). Outside on_print: sim.run loop + next_print + min ~11 s, on_1m bars ~8-10 s, fixed ~5 s.
=> 85 % of the PRINTS are no-ops but they cost only ~21 s (+ ~11 s of run-loop overhead) = ~30 % of the CPU. The expensive thing is the per-second evaluation of the layered rule chain for every open trade: 1.49 M manage_th_l2 + 1.08 M manage_policy calls per set-month = ~47 % of the CPU, 67 us each (7 Python layers: ev_profit > ec_hooks > wb_hooks > state_base_b > rules_replica > adapter_replica._rule_call probe wrapper > sim; cProfile tottime: _rule_call 13.9 s, sim.manage_policy 14.9 s, state_base_b 9.3 s, ec_hooks 5.6 s, 68 M dict.get 12 s).

## 3. What was built: the print scanner (exact by construction)
fc_scan.py: Replica.run is re-compiled IN MEMORY from its own source with ONE inserted block after `tmin, pr = min(cand)`; a numba function advances over the longest run of prints that are provably no-ops and replays the only state they change (adv/fav extremes + their ns, cur_k) in bulk. A print is skipped only if: no event (heap/bar), RT_START, 2 s lock, 5 s flat, 300 s poll_policy, outage window / reconnect, max_ns is due; no book armed / entry_active (not exit_pending) / stop_triggered join; _mf_lim None; no resting target/stop/stopjoin level touched (conservative >= / <= superset); and for every open book the P10 predicate holds (recorded second / sample index / entry, th_l2_trail_px and _pf_lvl untouched; sec mode and gap mode both handled). Anything else runs through the unchanged Python path, so the scanner can only lose speed, never exactness. Disabled automatically if any on_print override outside {sim, mf_inject, mf_inject2, fl_patch, fl_patch_next} is in the MRO, on any exception, or with FC_OFF=1. fc_launch.py = fl_launch + FL_COMPILED (order: fl_patch -> fc_scan -> fl_patch_next).
## 4. Measured
- identity (trade for trade, cmp 1e-9, vs the PRODUCTION exact result in runs_rf): TL3_ASI_L753bf92a_ADD 202608 x3 variants OK; TL3_NYE_L01811caa_RK7 202608 x2 variants OK; subset of the 217 sample (items 0-23) running (id_comp.py): see MORNING.md lines.
- speed (same set-month, same host, paired runs, no profiler): NY AM RK7: fast path only 105.8 s CPU -> with scanner 96.2 s (1.10x; first version without gap-mode support), later versions 97.4 s (Asia) / 98.7 s (NY AM) while the fast-only reference was ~100-105 s: **1.03-1.10x on top of the fast path** (=~2.4-2.5x vs production). The scanner skipped 2.9-3.1 M of the 7.5 M prints (41 %) in ~210 k scans; the per-scan Python state build (~25 us) eats most of the gain on short in-trade stretches. Upper bound of the print-skipping approach with free scans: ~1.45x (30 % of the CPU).
## 5. Conclusion and the real lever
Compiling the per-print loop cannot give another LARGE factor: the cheap part is already patched/skipped; the remaining time is the per-second rule chain (47 % of CPU) which is Python rule code over Python objects, not a loop. Factor by Amdahl:
- scanner as built: 1.05-1.10x (measured); with a cheaper state build (incremental arrays) up to ~1.25-1.3x.
- port the per-second chain (manage_th_l2 + manage_policy decision logic of the 7 layers) to numba, array-based (rule list -> arrays; features pct / mins / secs_ext / pulled_mult / tot_rel / ahead_rel are array lookups: searchsorted on rts/rca/rcb, L['live'|'med'|'rel'|'tot8'], bpx/apx/asz/bsz): chain 47 % -> ~3 %: total ~1.7-1.8x on top of the fast path (~4x vs production). Needs a layer-by-layer port with a per-evaluation identity harness (state in = state out, 1.5 M evaluations per month): about 3-5 working days for one builder, high risk in ec_hooks / wb_hooks / state_base_b rule semantics.
- cheap exact micro-win first (hours): hoist the constants out of adapter_replica._rule_call (cell dict, dict(sim.TH) copy, pol_rules rebuild per call: only 3 TH keys change; pol_rules list rebuilt every call): est. 5-10 % of total.
Recommendation (for the lead): do NOT spend the 217-case identity on the scanner alone (1.05-1.1x); decide between (a) the chain port (3-5 days, ~1.7x) and (b) the _rule_call hoist (hours, ~1.07x) + scanner state-build rewrite (~1.2x). Also: running ~100 more engine slots is worth more than either until the chain is ported.

## 6. Answer to order 1426Z item 3 (posted NOW; numbers are the measurements above, estimates marked)
Per-month profile of the FAST-PATH engine (Asia ADD 202608 and NY AM RK7 202608, ~100 s CPU, 7.52 M prints, plain run, box 1):
| part | CPU s | share |
|---|---|---|
| once-per-second rule chain of open trades (1.49 M manage_th_l2 + 1.08 M manage_policy; 7 Python layers) | ~47 | ~47 % |
| per-print loop, provably no-op prints (idle 11.3 s + in-trade 10.1 s) | ~21 | ~21 % |
| sim.run loop / next_print / min per print | ~11 | ~11 % |
| 1-minute bar handlers (on_1m, r5/swb hooks) | ~8-10 | ~9 % |
| other prints (armed, 2 s lock, 5 s flat, poll, touches) | ~5.5 | ~5 % |
| fixed per process (imports, Bars5 init) | ~5 | ~5 % |
| month data loading / I/O | ~0 (mmap month cache, feature cache 240/240 hits) | ~0 % |
What is compiled today: only the print scanner (fc_scan.py, opt-in, not switched). NOT compiled: the hook chain, bar handlers.
FACTOR (Amdahl; exact engine = 229 s CPU, fast path = ~100 s = 2.3x):
- scanner as built: 1.03-1.10x over the fast path (measured) = ~2.4-2.5x over exact. Upper bound of print-skipping with free scans ~1.45x over the fast path.
- + chain port to numba (chain 47 % -> ~3 %): ~1.7x over the fast path = ~3.9x over exact (est.); scanner + chain port together ~1.8-1.9x = ~4.2-4.4x over exact (est.).
THE COMPILED LOOP ALONE IS UNDER 1.5x (1.05-1.10x). Next best levers, in order: (1) chain port (1.7x, 3-5 builder-days); (2) hoist per-call constants in adapter_replica._rule_call + rule-chain micro-patches (est. 1.05-1.1x, hours); (3) fill the engine slots (engine slots were 166 of ~280 at 12:45Z) and fast-path share >= 90 %: worth more than (2) tonight.
PLAN / DATES (estimates): today 15:00-18:00Z: (2) _rule_call hoist + its identity (217 sample + newer kinds ~320 set-months) as FL_NEXT revision C; Nov 20: chain-port design per layer + per-evaluation identity harness (state in = state out on 1.5 M evaluations/month); Nov 21-22: port of manage_th_l2/manage_policy base + features; Nov 22-23: ec_hooks / wb_hooks / state_base_b / ev_profit layers; identity on the 217 sample + newer kinds (trade for trade 1e-9), 2 % exact re-check (fl_recheck.py), automatic fallback; earliest switch-on Nov 23-24 if nothing mismatches (each mismatch costs ~1 day).
CORES for my identity / dev runs: now <= 8 processes at nice 5 on box 1 (MemAvail > 40 GB; the 24-case subset runner id_comp.py, 6 processes, is running: pids 2491416 and 2527519); for the revision-C identity (~320 set-months x ~95 s = ~8.5 core-h) 12 workers at nice 5 on Dallas for ~45 min (or the same on Frankfurt/Singapore spare); final identity of the chain port ~16 workers nice 5 on Dallas for ~1 h. Stage-1 engine caps unchanged.
TOOLS: numba 0.67.0 + numpy 2.5.3 + llvmlite 0.49 in the venv on all four hosts; gcc on all four; Python.h only on box 1 and Dallas; Cython not installed anywhere (not needed).
