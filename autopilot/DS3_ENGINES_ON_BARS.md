# DS3_ENGINES_ON_BARS - the live engines re-derived on every bar type (CONFIRM addendum 2 sec 4 + T-BARS-ALL sec 2a/2c; 2026-10-30)
Code l2vast/ds3/code/bars_eng/ (be_lib.py harness, importable); outputs l2vast/ds3/out/bars_eng/; prereg out/bars_eng/PREREG_BARS_ENG.md (G1-G5 appended before each group's statistics; sha256 lines in DECISIONS.md). Research only; masks own, capped 20260206; UNTOUCHED never read (bars read with a parquet label-day filter).

## Answer in one paragraph
"Are 1-minute Japanese candles best?" For the live books, on this data: on average no other bar type beats the native 1-min engine. Over 38 tick-built bar types plus 14 Heikin-Ashi versions, 5 live engines x 2 variants (and WT, MV, PB, PB7, DN), the median bar type is WORSE than the 1-min engine in PRE (median delta -0.4 to -4.0 pts per contract by engine) and only 0-21% of bar types beat it in both PRE and X'. Selection on PRE + X' only (z >= 2.0, both deltas > 0, n >= 40) registers 5 (ST HM KB SM PE), 2 (WT MV PB), 4 (PB7 DN) cells of 2,255 / 866 / 756; the number registered by the SAME pipeline on size-shuffled placebo bars is 1-3 / 1-4 per seed (G1 / G2) - the real counts are inside the placebo counts. None clears its recent MDE; White RC p = 0.94 / 0.93 / 0.79 / 0.96 (G1 / G2 / G4 / G3), Romano-Wolf survivors 0 in every group. Verdict: NO bar-type engine is promoted; a handful of session cells are listed CANDIDATE-RECENT (positive in both L6M and HOLD, far below MDE), see below. Caveat that matters for reading the negative average: the live parameters were chosen on 1-min bars, so every alternative bar starts at a selection disadvantage; the walk-forward re-fit (G5) removes that advantage and still finds nothing (pooled-ALL max z 1.85 vs a refitted 1-min control).

## Method (what was and was not done)
* Bars: the tick-built barlib (out/bars/README_BARLIB.md; t_sig as-of rule, bars usable at t_sig only, decision second = the second ending at/after t_sig). Types: time 15s 30s 1m 2m 3m 5m 15m 30m; tick 100 250 500 1000 2000; range 3/5/10/15/20 pt; renko 2.5/5/10/12/20/30 pt (+ wick versions 5/10/20); UniRenko 2.5/5/10/20 pt; volume 500..5000; dollar 25M/50M; and Heikin-Ashi of 14 of them. BAR-STORE's bars_store did not appear; HA, Kagi, P&F, line-break, footprint, imbalance/run, delta, momentum and the custom L2-event types are NOT done (HA only; the rest need the store).
* Engines (logic = the live recursions of sd_state/tr1/tp_sig/ap_wt_core; bar-counted parameters in bars; minute parameters converted at the realised bars per minute): ST, HM, KB, SM, PE, WT, MV, PB, PB7, DN. Variants: D = the type replaces the engine's bar; G = the engine's native 3m/5m/10m/15m frames converted to round(minutes x bpm) bars of the type (time types group on epoch buckets). NOT done: CRT (ladder/dynamic exits), iFVG, O6, D6 session cells beyond the session column (no portable signal code found; the CR and MA rows of the trade index are not re-derived).
* Control = the native engine on the 1-min bars (aux_bar): signal parity with trade_index: raw-signal recall ST 100%, HM 99.9%, KB 100%, SM 100%, PE 100%, WT 100%, MV 99.5%, PB 100%; taken-set overlap 91-99% (the library entry has no 1-tick entry cost; exit-type agreement 99.5%). Same 60/60 bracket from the FILL, same fills, same entry window (18:00-15:15 ET), same busy rule. WT keeps 45/33.75.
* Fills (measured): market = close of the decision second +1 tick, filled in the next print second; stop 1.01, time 0.995, target year correction 1.4/1.5/4.2/4.3, fee 0.242; columns M (primary), N (no target correction), P9 (stop 2.45). DN stop-entries: first print through the stop, previous close if gapped, +1 tick.
* Metric: mean net pts per contract per trade in the cell vs the control in the same session and window (lot-matched by construction: per contract). A first draft restricted to days on which both traded; it was dropped before any selection because conditioning on the control trading biases the cell mean.
* Placebo: the same engine on time bars whose durations are the type's own durations permuted within the label day (3 seeds x 38 types for G1 and G2; G4 and G3 placebos NOT run).

## Control (native 1-min, per contract, M basis; n in brackets) - ALL sessions; per-session table in out/bars_eng/control_table.csv
| book | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| ST | +0.4 (722) | +1.5 (1258) | +0.9 (1385) | -0.3 (3082) | +0.2 (1003) |
| HM | -0.0 (511) | +2.2 (918) | +1.4 (1016) | +0.1 (2330) | -0.4 (877) |
| WT | -1.4 (968) | -1.1 (1733) | -1.5 (1922) | -1.2 (4337) | -0.3 (1557) |
| KB | -3.9 (727) | -0.4 (1265) | -0.9 (1384) | +1.4 (3128) | -1.6 (1039) |
| SM | -2.4 (167) | -1.5 (317) | +0.1 (367) | +1.4 (908) | +0.4 (446) |
| PE | -4.5 (718) | -1.7 (1201) | -1.8 (1320) | -1.6 (3091) | +0.5 (1018) |
| MV | -0.2 (663) | -0.5 (1157) | -1.1 (1277) | +0.8 (2972) | -4.2 (1022) |
| PB | +3.7 (489) | +4.3 (877) | +3.0 (977) | -1.7 (2293) | +0.8 (832) |
| PB7 | -2.2 (400) | -1.5 (729) | -1.8 (805) | -0.5 (1816) | -0.0 (797) |
| DN | +1.0 (466) | +2.1 (843) | +1.5 (940) | +1.9 (2091) | -1.1 (851) |
MDE for a single book-window is typically 3-6 pts per contract (2.8 x SE with SD ~ 45 and n 700-1,300); every number below is read against that.

## Verdict per book (ALL sessions, PRE+X' only; fraction of bar types beating 1-min in BOTH PRE and X')
ST 2% | HM 6% | WT 10% | KB 0% | SM 0% | PE 17% | MV 0% | PB 2% | PB7 21% | DN 2-8%. Best PRE+X' cell per book (ALL sessions, delta vs 1-min per contract PRE / X'): WT on HA 15-min bars +1.6 / +3.8 (z 1.7); PB7 on 5,000-volume bars +4.9 / +10.8 (n 77, z 1.4); PE on 2,000-tick bars +3.3 / +0.1; HM on 5-min +0.5 / +2.5; ST on HA 15-min +1.4 / +1.5; none reaches z 2 pooled. Statement form asked for: "KB on 8-pt-class range bars vs 1-min": KB on 5-pt range bars is worse than KB on 1-min candles in PRE (median KB delta -3.3 PRE, -2.3 for the grouped variant); no KB bar type beats its 1-min version in both PRE and X' in the ALL-session pool.

## Session cells registered (PRE+X' selection, z >= 2.0; one recent look, taken once per group; delta per contract vs native 1-min in the same session; MDE = 2.8 SE)
| group | cell | PRE d | X' d | L6M d [MDE] | HOLD d [MDE] | L3M d (view) | tier |
|---|---|---|---|---|---|---|---|
| G1 | PE on 2,000-contract volume bars, NY-PM | +5.5 | +6.5 | +3.8 [14.6] | +2.9 [14.0] | +6.7 | CANDIDATE-RECENT (positive both, 0.3 MDE; DSR 0.09; RW p 0.99) |
| G1 | PE on 10-pt UniRenko, London | +5.5 | +10.4 | -7.3 [17] | -5.8 [16] | | DEAD recent |
| G1 | SM on 5-min, NY-PM | +4.3 | +16.6 | -0.8 [34] | -7.5 [32] | | DEAD recent |
| G2 | WT on 5-min, pre-open | +10.4 | +3.8 | -4.7 [20] | -1.5 [19] | | DEAD recent |
| G2 | WT on HA 15-min, NY-AM | +5.6 | +4.7 | +0.7 [16] | -1.7 [15] | | DEAD recent (HOLD) |
| G4 | PB7 on HA 2-min, London | +10.4 | +9.0 | +3.8 [21] | +6.4 [20] | +6.3 | CANDIDATE-RECENT (positive both, 0.2-0.3 MDE; DSR 0.13; RW p 0.89; boot CI HOLD -4.1..+17.0) |
| G4 | DN on 2,500/5,000-volume bars, pre-open | +12.3 | +13.7 | -2.0 [34] | +0.9 [33] | | DEAD recent |
| G3 | 103 bracket-grid cells (30/45/75/90 and prior-day-level target); 68 positive in both L6M and HOLD, mostly SM pre-open cells whose 1-min control is a negative n~40 sample | | | mean +13.7 | mean +11.2 | | CANDIDATE-RECENT at best, all below MDE (SM pre: L6M d +65 vs MDE 85); WT HA-15m NY-AM b30 and time_30m NY-AM b30 have Sharpe 4.3, DSR 0.6, but RW p 0.98 and RC p 0.96 for the group |
| G5 | 10 walk-forward-refit pairs (SM HA-15m Asia, HM HA-2m pre ...) | | | negative or ~0 vs native and vs refitted 1-min (e.g. HM volume_1000 London L6M +4.8, HOLD 0.0) | | | DEAD recent |
Stack (exact lock engine, live lots, native book rows with the session replaced), $/wk cell vs control L3M / L6M / HOLD / PRE / X': PE vol-2000 NY-PM -4.8k vs -6.2k / +3.2k vs +1.9k / +2.7k vs +1.5k / +3.4k vs +3.4k / -0.6k vs -2.9k; PB7 HA-2m London -3.4k vs -4.5k / -3.5k vs -8.8k / -4.4k vs -9.5k / +8.4k vs +9.3k / +3.9k vs +2.5k; all other registered cells negative in L3M and mostly in L6M (out/bars_eng/stack_registered.txt). Structure vs information: engine on different bars = signal timing change (INFORMATION-type, not a split/lot factor).

## Multiplicity and quant layer (local implementation of QL-1; be_qv*.py)
Cells scored: G1 2,255, G2 866, G4 756, G3 15,404, G5 1,845 (UF_TRIALS side="engines_bars", +19,281 rows appended to DEAD_CELLS). White RC p (PRE+X' daily delta series, stationary bootstrap, 500 draws): G1 0.94, G2 0.93, G4 0.79, G3 0.96; Romano-Wolf survivors 0/2,251, 0/866, 0/751, 0/15,374; PBO (CSCV S=8): G1 0.27, G2 0.53, G4 0.19, G3 0.00 (a dominated-by-one-cell artefact; read with the RC); DSR of the registered cells 0.02-0.25 (G1,G2,G4), N = cells in the program. Cell-level (be_qv_cells.csv, 10 cells: 2 CANDIDATE-RECENT + top 8 G3): day- and week-clustered SE ~ 4.5 (PE vol-2000) / 5-7 (PB7) in HOLD, block-bootstrap CI of the HOLD delta includes 0 for every cell; latency 1 s / 3 s: PE vol-2000 HOLD cell mean -2.1 -> -1.4 -> -0.7 (no sensitivity), PB7 +4.5 -> +4.5 -> +3.8; N and P9 bases within 0.2 of M for the delta; quarters with positive delta 9/12 (PE), 10/12 (PB7), fold SD 8.0 / 7.5 pts; neighbour mean (same family sizes, PRE+X') +2.8 (PE, 4 neighbours) and n/a (PB7 HA-2m, neighbours not scored in the same session threshold); stack correlation (weekly delta $ vs control stack) -0.12 / -0.28; top-5%-of-trades share of the gain 1.55 (PE; the gain is carried by a few trades) / 0.44 (PB7); breakeven entry slippage = the cell mean (PE vol-2000 HOLD -2.1: negative already, PB7 +4.5). NOT computed (missing columns, so nothing is promoted): capacity at the book depth (needs the mbp-10 join at the bar-based fills), regime (vol tercile) split, 200-draw placebo rank (3-seed pools only, G1 and G2), +-25/50% parameter sensitivity beyond the G5 grid, purged k-fold (rules are fixed, not fitted; the rolling quarterly fold dispersion is given instead), G3/G4 placebos.

## Placebo
G1: placebo seeds select 3 / 1 / 1 cells (max z 2.38 / 2.03 / 2.18, mean z -0.33) vs real 5 (max 2.14, mean z -0.37). G2: 1 / 4 / 1 (max z 2.19 / 2.44 / 2.15) vs real 2 (max 2.19). The real selections are inside the placebo noise: price-driven bar formation adds no detectable information over random-time bars of the same size distribution, and the average alternative is -0.3 z below 1-min regardless of how it is built (a parameter-fit and bar-size effect, not a bar-type effect).

## RECENT_WINS (view only, never used for selection)
l2vast/ds3/out/recent_wins/bars_eng.csv (4,326 rows positive in L3M, all tiers; columns incl. L3M CI, L6M/HOLD/PRE/X', delta $ vs 1-min at live lots, plain sentence). Examples are mostly large-bracket variants and PB/DN books that were themselves positive on 1-min in the last 3 months (PB +3.7 on 1-min); the right column to read is delta vs 1-min. These are mostly regime, not bar type.

## Open items
CRT, iFVG, O6, D6 session cells, MA/CR rows; BAR-STORE types (Kagi, P&F, line break, footprint, imbalance/run, delta, momentum, L2-event); G3/G4 placebos; capacity and regime columns of the quant layer; walk-forward re-fit for PE, PB, PB7, DN; bracket grid for PB7/DN. NT8 specs of the CANDIDATE-RECENT cells appended to DS3_THL2_NEEDS.md (BAR-ENG section).
