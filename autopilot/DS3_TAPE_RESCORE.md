# DS3_TAPE_RESCORE - re-score of GRID, ICT, BAR-ENG, CF-BARS, wave-2 and the D7 alt-bar cells on the store rebuilt from the de-duplicated tape (agent TAPE-2, 2026-10-31)

Research only; nothing live changed. **This is a RE-RUN of pre-stated cells, not a new search** (prereg `autopilot/PREREG_TAPE_RESCORE.md`, sha256 5df3d2360876648fcf7bf9e1c18076ef1fa405a10954b2fc374153d6fae49063, logged in DECISIONS.md before any re-scored statistic). Cap 202602 / label day 20260206 everywhere. No post-cap tape or L2 file was opened: the store builder reads the NEXT month's tape and 1-s table (the path by which TAPE-1 touched 2026-03), and TAPE-2 blocks that read in code (`rebuild_store.py`); the tape directory used has only months 2023-02..2026-02. The original store, tick library, tape and tables are untouched. Code `l2vast/ds3/code/tape_rescore/`, outputs `l2vast/ds3/out/tape_rescore/` (symlink to /mnt/l2/l2vast/ds3_tape_rescore).

## PAGE 1 - TIER CHANGES

**Verdict.** Rebuilding the 11 affected store months (and the same 11 label days of the tick-bar library) moves no registered conclusion: of 1,563 stored representatives / tiered rows re-scored (ICT 5, GRID 69, PB 254, TR 50, NEWE 65, NEWC 343, CF-BARS 777 rows over 7 stages; BAR-ENG registrations counted separately) **4 change tier, all CF-BARS and all zero-crossings of 0.00-0.08 pts per planned lot, inside every MDE** (the stored list of the whole programme is unchanged for 0 wave-2 representatives). Together with TAPE-1's wave 1 (1 of 68) that is 5 tier changes, none PASS-relevant; "0 PASS, bar types are not a base" stands. The rebuilt selection (threshold crossings, mostly one trade) adds 3 new non-DEAD representatives, none above LEAD / CANDIDATE-RECENT, none passes G6. D7 alt-bar identity cells: **no tier change**, three of five move by one trade, and library-vs-tape signals on the defect day 20260202 become exact (L01610 124/124, was 15/124).

| program (frozen harness, bpm frozen) | stored reps / rows re-scored | stored-tier changes | reps gained / lost by the rebuilt selection | tier of the gained (after G4 placebo) |
|---|---|---|---|---|
| ICT (CRT + iFVG, 61 series) | 5 (3 LEAD, 2 DEAD) | 0 | 0 / 0 (9 -> 9 selected cells) | - |
| GRID bracket grid PB7/DN (52 types) | 69 (all DEAD) | 0 | 5 / 7 | 5 DEAD (G4 n/a as for all GRID reps) |
| GRID walk-forward re-fit PE/PB/PB7/DN | 5 selected pairs | 0 (5/5 identical) | 0 / 0 | - |
| PB (T-PB + TB4) | 254 (249 DEAD, 3 LEAD, 2 CAND-RECENT) | 0 | 8 / 11 (11 lost were DEAD) | 8 DEAD (twin of the TB4W pair: placebo rank 0.60) |
| TR (TR1 + H4) | 50 (all DEAD) | 0 | 5 / 4 (DEAD) | 4 DEAD, **1 LEAD**: TR1F_vote_TSM_k3 range/16 G pre (fails G1 only; placebo 1.00) |
| NEWE (10 engines, 88 series) | 65 (63 DEAD, 2 CAND-RECENT) | 0 | 5 / 1 (DEAD) | 3 DEAD, **1 LEAD** eng PB7 hybridrenko/8 G NY-AM (fails G1 only; placebo 1.00), **1 CANDIDATE-RECENT** eng PE dol/400M D London (no failed gate except G6; placebo 1.00; PRE t 1.95 -> 2.13 from ONE added PRE trade, HOLD identical, HOLD paired +3.2 SE 6.2) |
| NEWC (wave-1 candidates, 36 series) | 343 (341 DEAD, 1 LEAD, 1 CAND-RECENT) | 0 | 12 / 11 (DEAD) | 12 DEAD (the 3 G1-only ones fail the placebo: 0.67 / 0.40 / 0.73) |
| BAR-ENG G1 / G2 / G4 | 5 / 2 / 4 registered | 0 (both CAND-RECENT cells keep it) | G4 +1 (negative recent: nothing) | - |
| BAR-ENG G3 brackets | 103 registered, 68 positive in L6M and HOLD | 0 of the 103 flip | +9 / -2 (5 of the gained are positive in both, +1 lost was) -> 110 registered, 72 positive-both | below MDE, registration only |
| BAR-ENG G5 re-fit | 10 registered | 0 | 0 / 1 (HM time_5m pre; no recent n >= 40) | - |
| BAR-ENG quant cells (qv_cells) | 10 | 0 | - | 8 identical, 2 move (below) |
| CF-BARS S1 / S2 / S2b / S2c / S3 / S4 | 92 / 85 / 120 / 120 / 120 / 120 rows | S1 0; **S2 1; S2b 2**; S2c 0; S3 0; S4 0 | top-12 pairs kept 85 / 89 / 105 / 117 / 120 / 117 of 120 | new top-12 entries mostly BEST-AVAILABLE-NEGATIVE (S1 1 CAND-RECENT, S2 1 + 2 CAND., placebo carried where stored) |
| CF-BARS S1c (wave 2 of CONFIRM-BARS) | 120 | **1** | 115 of 120 kept | - |

**The tier changes, with the failed gate** (CF-BARS rule: CANDIDATE-RECENT needs d_floor >= 0 in L6M and HOLD; CANDIDATE adds PRE and X' > 0 and beating the placebo):
1. CF S1c, PE, `ha|5m|three|d|near|X3|A70|N`: CANDIDATE-RECENT -> BEST-AVAILABLE-NEGATIVE. HOLD d_floor +0.039 -> -0.008 (gate "HOLD >= 0" fails); L6M +0.414 -> +0.362. HA is recursive, so the move also carries over from the replayed days.
2. CF S2, PE, `renkomed|m1|rev|d|near|X3|A70|N`: BEST-AVAILABLE-NEGATIVE -> CANDIDATE-RECENT. HOLD -0.024 -> +0.023, L6M +0.115 -> +0.167 (now passes "recent >= 0"; the carried placebo is still not beaten; MDE about 1).
3. CF S2b, HM, `vrb|s30|close_fav|c1|near|X3|A70|N`: BEST-AVAILABLE-NEGATIVE -> CANDIDATE-RECENT. L6M -0.001 -> +0.002, HOLD -0.001 -> +0.002 (a 0.003-pt crossing; no content).
4. CF S2b, WT, `vol|10000|close_fav|d|near|X3|A70|N`: CANDIDATE -> BEST-AVAILABLE-NEGATIVE. L6M +0.045 -> -0.043 (gate "L6M >= 0" fails); HOLD +0.200 -> +0.120.
5. (TAPE-1, wave 1, recorded here) L01684 SM tick/500 D pre: LEAD -> DEAD, G5 (PRE N-basis +0.21 -> -0.35), it already failed G4.
Newly gained representatives that are not DEAD (selection crossings, not tier changes of a stored cell): TR1F_vote_TSM_k3 range/16 (LEAD), PB7 hybridrenko/8 (LEAD), PE dol/400M London (CANDIDATE-RECENT). Their recent windows were already in the stored wide tables (computed for every cell, view only), so no extra look was taken; none is promotable (HOLD CIs include 0, below MDE, G6 fails).

**Net effect.**
* Leaderboards (LEADERBOARD, TREND, PULLBACK, SBS, STRUCT48, PRED, BRACKET): none of them contains a BARS-CAND, BAR-ENG, CF-BARS or bar-store row (searched); **net effect 0**.
* DS3_BARS_ALL_CANDIDATES.md: wave 1 unchanged except L01684 (TAPE-1); wave 2 headline lines unchanged: the TB4W 10-min Asia pair keeps CANDIDATE-RECENT (t 4.39 -> 4.42, HOLD paired +13.36 identical), TE6 / L02766 etc. unchanged; counts become: NEWE 2 -> 3 CANDIDATE-RECENT, 0 -> 1 LEAD, TR 0 -> 1 LEAD, PB / ICT / GRID / NEWC unchanged. View-only RECENT_WINS (L3M-positive cells): 653 of 91,880 wave-2 cells change membership (0.7%; ICT 21, PB 114, TR 102, NEWE 69, NEWC 347) because L3M contains the defect day 20260202.
* CF-COMBO BAR members (top 8 mech-d rows per book): 7 of 80 members change (WT 3, KB / PB / PE / ST 1 each); the presence files of those members need regenerating from `tape_rescore/cf/cells_*`.

**D7 alt-bar identity cells** (library code run on ORIGINAL vs REBUILT store, bpm frozen; per contract, M):
| cell | tier | HOLD n, M | L6M n, M | PRE n, M | signals vs tape on 20260202 | all 10 days exact |
|---|---|---|---|---|---|---|
| L02766 5-min ST NY-AM | LEAD, unchanged | 124, +6.60 same | 113, +5.47 same | 270, +8.10 same | 4/4 same | 49/50 same |
| L01501 HA-3m NY-AM | LEAD, unchanged | 106, +3.76 same | 92, +5.34 same | 257, +0.81 same | 2/4 -> 4/4 | 53/55 -> 55/55 |
| L01610 range-8 pre-open | CAND-RECENT, unchanged | 74 -> 73, +1.10 -> +2.16 | 68 -> 67, +0.76 -> +1.91 | 306 -> 305, +0.14 -> -0.33 | 15/124 -> 124/124 | 1293/1403 -> 1402/1403 |
| L01490 vol-500 London | LEAD, unchanged | 108 -> 107, +4.46 -> +4.17 | 94 -> 93, +5.78 -> +5.46 | 316, +0.57 same | 7/9 same (2 non-defect misses remain) | 193/196 same |
| L02783 4-min London | LEAD, unchanged | 102, +10.62 same | 87, +9.59 same | 256 -> 257, +2.39 -> +2.60 | 4/4 (library had 2 extra) | 53/53 (was 53 of 55 library) |
So the answer is yes for numbers (3 of 5 cells, one trade each), no for tiers or conclusions; the weekly-cumulative risk picture below moves only for L01610 / L01490.

**Risk picture (standing order DRAWDOWN-FIRST)**, D7 cells at 1 lot (no D7 lots are set; $ = M x 20), weekly-cumulative, original -> rebuilt:
| cell | window | mean $/wk | maxDD $ | worst-20 wk $ |
|---|---|---|---|---|
| L01610 | L6M | +43 -> +107 | 6,159 same | -632 -> -555 |
| L01610 | HOLD | +60 -> +117 | 6,159 same | -935 -> -859 |
| L01610 | PRE | +13 -> -30 | 23,240 -> 23,691 | -2,550 -> -2,571 |
| L01490 | L6M | +402 -> +376 | 5,748 same | -407 -> -411 |
| L01490 | HOLD | +311 -> +288 | 6,159 same | -736 same |
| L02783 | PRE | +168 -> +183 | 11,956 same | -2,419 same |
| L02766, L01501 (all windows), L01490 / L02783 other windows | | unchanged | unchanged | unchanged |
Full table `out/tape_rescore/d7_risk.csv` (L3M / L6M / HOLD / PRE / X'). Same-lot maxDD changes by at most +2% (L01610 PRE); equal-risk re-scaling and the same-volume random-cut placebo are not applicable (the comparison is the same rule on corrected data, not a rule that cuts volume). The CF-BARS and representative cells that changed tier have no stack unit (planned-lot per signal / per-contract research cells), so no risk line exists for them; stated, not estimated.

**Cost and recommendation.** Rebuild of the 11 store months 4.6 CPU-min (about 1.5 min wall at 3 workers), 4.8 GB (164 series x 11 months); tick-library patch of the 11 label days 38 types about 25 s plus 1.3 GB. Re-score: wave-2 daily tables about 82 CPU-min, BAR-ENG about 20 CPU-min, GRID about 17 CPU-min, CF-BARS cells about 2.3 CPU-h (489 specs), scoring about 20 CPU-min; about 4 CPU-h, 1.6 h wall at 3 workers (the originals logged about 20 CPU-h). **Recommendation: yes, re-issue the 11 store months and the 11 tick-library label days** (swap the files, keep the originals as a dated backup): it is cheap, the rebuild is bit-identical to TAPE-1's, it removes a known identity defect (D7 shadow signals on weekend-start months, `ek` back-steps in 128 of 164 series, doubled volume), and it is needed before the 2026-11 month and the weekly ext enter the library (reducer patch + de-duplication, TAPE-1 section 5). **Do NOT re-issue the downstream tier tables or reports**: no conclusion changes; the 8 changed cells are appended to DEAD_CELLS (program TAPE2RESCORE) and this file supersedes the five tier lines above. bpm freezing is immaterial on a real re-issue: the bars-per-minute moves 0.06% median (0.17% max) and only 1 of 164 store series x 7 groupings (kagi/16 at 30 minutes) and 0 of 38 library types would change round(minutes x bpm); keep the frozen constants anyway (`bpm_store_orig_vs_new.csv`).

---

## 1. Rebuilt store and verification (task 1)
* Rebuild: `rebuild_store.py` = `bars_build.build_month` with the tape directory `tape_rescore/tape_dropin/` (clean months -> original files, 11 defective months -> TAPE-1's de-duplicated copies) into the NEW scratch store `tape_rescore/bars_store_t2/` (164 series x 11 months). `bars_store_full/` is a per-file symlink view (original months + the rebuilt 11) used by the scorers.
* Day volume: the store tc/1m day volume equals the library volume on 9 of 11 days to the contract; on 20230703 and 20240603 it is 131 / 144 contracts below (final partial minute dropped by the builder, same in the original), vol_ok True on 11 of 11 (False on 11 of 11 before). First 2 h vs the L2 1-min table: ratio 1.0000 on 11 of 11 days (originally 2.00 on 6 days, 1.5-1.65 on 5). Whole-day ratio vs library before: 1.014-1.065.
* Event-bar phase: tick/500, tick/1000, vol/500, vol/1000 rebuilt independently from the de-duplicated tape (own loop, rule of `seg_vol`) match the store bar for bar on all 11 days: 44 of 44 series-days identical (count, ts1, volume). `ek` back-steps inside a day: 0 of 164 series (128 before).
* All 164 series are bit-identical to TAPE-1's rebuild (independent run). After hour 2 the share of bars identical to the original: time bars 99%, range / renko / kagi / P&F 99.6-100%, HA 91%, volume / dollar 26%, tick 0% (phase shift), as TAPE-1 found.
* Tick-bar library (used by BAR-ENG and GRID, not by the store): the E1 cache month slice equals the stable-sorted tape file; dropping the sorted positions of the original rows [0,b) reproduces the sorted de-duplicated tape exactly (ts, px, size, side) in 11 of 11 months; the 11 label days were rebuilt for 38 types and spliced (`barlib_t2/`); control: the same day-slice procedure on original ticks reproduces the stored rows exactly (76 of 76 type-days incl. a clean day). Day volume after the patch equals the library day volume on all 11 days. Files: `verify_volume.csv`, `verify_eventbar_phase.csv`, `verify_series_vs_orig.csv`, `barlib_*.csv`.

## 2. Method
Same code as the originals, imported unchanged: `wave2_*` job workers (ICT, PB, TR, NEWE, NEWC via `bc_run.worker`), `wave2_pipe.cellstats / widen / select_pre_x`, `wave2_tier.tier_table` (gates G1-G7, placebo ranks and G6 carried from the stored files; a representative new to the selection has G4 n/a and was given its own 15-draw placebo when its only open gate was G4: 7 reps), `be_score / be_stage2 / be_qv` rules, `bars_events` + `bars_score` + `bars_report.tier`. bpm frozen at the original value (`tr_patch.py`). Baseline = the stored daily tables through the same scoring code: it reproduces the stored tier of 5 / 254 / 50 / 65 / 343 / 69 / 777 of the same counts (all). Tiers are the pre-PAIRFIX REPS_TIERED tiers (as TAPE-1); PAIRFIX relabels are separate and untouched. Daily-table rows changed: ICT 12,459 of 2.04 M, PB 27,580 of 11.75 M, TR 17,993 of 4.35 M, NEWE 12,258 of 2.84 M, NEWC 67,981 of 20.99 M; 86-97% of them on the 11 label days, the rest recursive-indicator carry-over (HA etc.). Largest representative move: PRE t 0.31, HOLD paired 4.4 pts (below the MDEs of 13-25).

## 3. BAR-ENG detail (tick-bar library, 52 types, trades re-run for G1 / G2 / G4, five brackets, parameter grid)
Registered cells (PRE + X' rule, z >= 2): G1 5 -> 5, G2 2 -> 2, G4 4 -> 5 (+ha_tick_500 PB7 G London, L6M -6.9 / HOLD -7.2), G3 103 -> 110 (101 kept, 2 lost, 9 gained; 11 cells cross z = 2), G5 10 -> 9. CANDIDATE-RECENT proxy (registered and d > 0 in L6M and HOLD): G1 2 -> 2 (PE volume_2000 NY-PM +3.82 / +2.88, unchanged), G4 1 -> 1 (PB7 HA-2min London +3.77 / +6.38, identical), G3 68 -> 72. Quant cells: PE volume_2000 NY-PM d_PRE +5.49 -> +5.36, MV tick_2000 pre b75 n_HOLD 42 -> 43 and d_HOLD +9.5 -> +11.3, PE unirenko_10_15 London b90 d_PRE +8.26 -> +7.61, the other 7 identical. Program-level RC / PBO / DSR were not recomputed (carried; they fail every cell).
## 4. CF-BARS detail
489 specs re-run (cells through `cf_engine`), rankings (PRE + X') regenerated; recent look recomputed for the stored selected cells; placebo draws carried. Top-12 turnover is the visible effect (rank cuts are sensitive): kept 85 / 120 in S1 down to 120 / 120 in S3; Spearman of the cell scores 0.90-0.99 within book. Best candidate per (stage, book) changes in 11 of 69, mostly renko / unirenko ties; the one with a tier consequence is S2 DN (renkomed m1 n2 CAND-RECENT -> renko 24 rev CANDIDATE, d_L6M +0.22 -> +0.70, MDE about 1). RE5_CONFIRMBARS* DEAD_CELLS rows (recent-edge re-reads of these cells) were not re-run.
## 5. Files and bookkeeping
`score/<group>/{reps_compare,reps_new_selection,reps_new_selection_tiers,reps_dropped_from_selection}.csv`, `grid/score/`, `bars_eng/score/`, `cf/{tiers_*,rankcmp_*,cf_summary,combo_bar_members}.csv`, `d7_*.json/csv`, `d7_risk.csv`. DEAD_CELLS: 8 + 3 correction rows appended (program TAPE2RESCORE; the first L01684 row was picked wrongly, the correction rows say so and carry the right cell, tick/500 D pre); nothing rebuilt. UF_TRIALS untouched (same cells re-run). Not done: G4 / G6 recomputation for stored reps, BAR-ENG program-level RC, the ALT library-trade-reproduction counts (only signals and windows), regeneration of CF-COMBO presence files.
