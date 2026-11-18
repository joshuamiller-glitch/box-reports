# PHASE 2 TOOLING - end-to-end test on today's leads WP10 (NY PM) and XA3 (NY AM) and its COST in core-hours (W-SHORT, order 1840Z item 1c), 2026-11-18 ~19:00Z

Cells: **XA3** = NY AM | tick_5000 | levels_vwap.retest_native {M 6, tol 0.5} | plain 60/60 | both. **WP10** = NY PM | vol_350 | tape_libvol.cmf {len 10} | asym20u/10u (median stop/target 120/101 pts) | both. Screen level = naked trigger, 1 lot, $4.84 incl, points on the 26 weeks to the data end. Code: code/th_short/gp2test.py (steps i, iv, iii), gsel_rule.py, gstage3.py. CPU seconds are process CPU time on server 2 (one thread).

## Results of the four tests

| test | XA3 (NY AM) | WP10 (NY PM) |
|---|---|---|
| (i) 30 same-bracket random-entry controls, screen, L6M points | real +1,644 vs null mean -162 (sd 1,556, max +2,891): **beats 25 of 30 (83rd percentile)**; by year real vs draws: 2023 beats 27/30, 2024 30/30, 2025 29/30 | real +1,236 vs null mean +787 (sd 1,746, max +4,437): **beats 15 of 30 (50th percentile)**; 2023 beats 25/30, 2024 26/30, 2025 21/30 |
| (ii) 30 date-shift ENGINE controls (JL3 stack + the book's trades shifted by +-7..105 days; engine base lots, raw engine fee, 202605-202610; W-NYENG sets TL3_NYE_<cell>_CT*, all 180 set-months DONE) | ADD delta vs JL3: real **+$54,428** vs controls mean -$11,860 (sd $21,137, max +$24,259): **beats 30 of 30** | real **+$41,748** vs controls mean -$4,823 (sd $21,221, max +$41,613): **beats 30 of 30, but the best control is within $135** |
| (iii) selection-corrected best-pick null | see cost table (the draws themselves are the cost; scoring one draw per session measured) | same |
| (iv) trust audit (brute-force tape walk trade-for-trade, 6 truncation cuts, fills >= signal + 1 s) | PASS (0 mismatches, 0/6 cuts differ, fills never early); 641 trades L6M, avg hold 11.8 min, win 52% | PASS; 413 trades L6M, avg hold 69 min, win 54%, stop 120 / target 101 pts |

READING: the engine date-shift controls say both leads beat 30/30 shifted copies of themselves (the shift keeps the book's own time-of-day structure but breaks the dates). The screen-level random-entry control (same bracket, same count, independent side) is a harder, different test: XA3 beats 25 of 30 draws (not all 30: 5 random-entry draws did better in L6M), WP10 sits at the median of its draws (a wide asym20u/10u stop in this trending window earns +787 pts on average for RANDOM entries; WP10's +1,236 is not distinguishable from that at screen level). So WP10's screen edge over random entries with its own bracket is NOT established; its engine result rests on the date-shift test only. Neither number has the selection correction (iii) yet.

## Cost in core-hours (measured; per cell, per session; one core = one thread)

| item | unit cost (measured) | per cell | per session, N shortlisted cells | notes |
|---|---|---|---|---|
| (i) 30 same-bracket random-entry draws (screen, pass 2 on the cell's (row, module) file) | XA3 28 CPU-s per draw, WP10 47 CPU-s per draw | 14-23 CPU-min = 0.24-0.39 core-h (cells sharing a (row, module) file share the draws) | N=3: ~1; N=6: ~2; N=10: ~3; N=20: ~6; N=50: ~15 core-h | draws already on disk are reused (20+ existed for the 23 NY pairs) |
| (ii) 30 date-shift engine controls (L6M = 6 months) | engine pace measured 2.6 core-min per set-month (server 2: 551 set-months/h on 24 workers, 14:02Z); WP10 + XA3 together did 360 set-months | 180 set-months = **7.8 core-h** | N=3: 23; N=6: 47; N=10: 78; N=20: 156; N=50: 390 core-h | per book as ADD only; replace-variants (RK7 etc.) and prior years are extra |
| (iii-a) producing ONE full null draw of the SAME pass-1 search (all rows x all modules, random entries) | sample of 30 jobs: mean 14.8 CPU-s, median 8.1, p90 23.0 per (row, module) job; ~77,000 jobs per draw (the 1845Z count) | - | **~317 core-h per draw; 20 draws = ~6,300 core-h** (draws serve all four sessions at once: the grid file of a (row, module) holds all four sessions) | wall at the current fleet (64 + 128 + 128 + 32 = 352 threads, all cores) about 18 h for 20 draws; draws 1 and 2 are already partly done as part of phase 1 |
| (iii-b) scoring one draw for a session | load pool 224 CPU-s + rolling 168 CPU-s = 392 CPU-s (measured on a 4.6 M-cell NY AM pool) | - | 0.11 core-h per draw per session; 20 draws x 4 sessions = 8.7 core-h | memory ~25 GB per scorer process |
| (iv) trust audit + look-ahead | XA3 5 CPU-s, WP10 19 CPU-s per cell (about 12 s average, bar-size dependent) | 0.001-0.005 core-h | NY AM bare-passing cells (see SURVIVOR_COUNTS.md): ~8,900 -> ~30 core-h; N=50: 0.2 core-h | run best-first on every rule-passing cell |
| rule evaluation of a whole session (gsel_rule.py: all 4-4.6 M cells, reasons, families) | ~340 CPU-s load + scoring, 25 GB | - | 0.1 core-h per session per ranking variant | writes rule/<var>_<session>.parquet |

CRITICAL ITEM: (iii-a) dominates phase 2 (about 6,300 core-h, ~18 h of the whole fleet) and is independent of N. Cheapest honest way to shorten it: the 20 draws are needed only once for all four sessions; start them as soon as pass 1 on real is done (they use the same tables), or give them a dedicated server. Everything else per-cell is small (engine controls dominate: 7.8 core-h per cell).

## Tool status
- gp2test.py steps i / iv / iii run end to end on both leads (this page). gstage3.py (A audit, B nulls, CD rolling) ran on the 48-row shortlist earlier. gsel_rule.py (rule-based shortlist + families) runs per session and variant.
- Open: the selection-corrected best-pick null needs 20 full draws (not on disk yet; 2 exist partly); the own-stop and current-stack-mask variants exist for ~1,700 pairs only, so the full-grid own-stop counts wait for the phase-1 scoring.
- Scratch of this test removed: res/wsrand_t (my 30 sampled jobs). Null draws p1rand1..30 for the XA3 and WP10 (row, module) files stay (useful).
