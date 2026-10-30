# DS3_DECAY_B_HORIZON - T-SIGNAL-DECAY section B (decay / horizon exits) and the horizon part of D (SD-B, 2026-10-30)

Research only. No live, execution-server or chart change. Prereg `l2vast/ds3/prereg/SDB_prereg.md` sha256 bda82ca6d72784037749c0008b17dcd59e2f92fca17088e8aa6f9048ae285ed6 (DECISIONS.md, before scoring); PRE+X'-only selection file `l2vast/ds3/out/decay/B/selection.json` sha256 cba9c5edd56300ed834b59d5e361f90ea5f2f4095104c37238574fa5a6fd76c7; one recent look per group (tracks SDB_G1..G5 in holdout_looks.jsonl). Masks own and capped 20260206 (R26 0101.., L6M 20250801.., HOLD 20250701.., PRE 20240201..20250630, X' 20230401..20240131); UNTOUCHED never read. Code `l2vast/ds3/code/decay/` (dc_panel, dc_eng, dc_cells, dc_a, dc_b, dc_c, dc_d, dc_e, dc_stack); outputs `l2vast/ds3/out/decay/B/`.

## Verdict (one line per book; per contract, selected cell of each group, last 6 months, basis N, MDE = 2.8 SE)
**No horizon / decay exit beats hold-to-bracket. 0 PASS, 1 CANDIDATE-RECENT (CR, not a real candidate, see below), 7 DEAD (zero or near-zero fires, or CR), 57 BEST-AVAILABLE-NEGATIVE of 65 selected cells (5 groups x 13 streams).** On the 8 books that carry the stack (and pooled ALL11 / STACK6) every group's PRE+X'-selected cell is negative in the last 6 months on M, N and LIVE-CAL, and in HOLD. The time-exit family was scored before (THPB F7 conditional time stops, THPC1 fixed time, THLB time-only: all negative); this section adds unconditional/tighten/session-end/progress/flat-line/edge/ATR-time and agrees.

| book | best PRE+X' cell by group G1 (hard) | L6M N (MDE) | verdict |
|---|---|---|---|
| ST | session-end, tighten | -0.90 (1.68) | negative, in every window |
| HM | session-end, market | -2.43 (3.16); PRE +0.20 / X' +0.58 then HOLD -2.15 | negative recent: the only book whose G1 cell is positive in both selection windows, and it flips |
| WT | 60 min, tighten | -1.10 (1.09) | negative, nearest to zero of the stack books in every group |
| KB | session-end, tighten | -1.78 (1.95) | negative |
| SM | session-end, tighten | -0.78 (4.63) | negative, MDE too wide to say more |
| PE | 120 min, tighten | -1.45 (2.04) | negative |
| PB | 120 min, tighten | -1.54 (2.28) | negative |
| DN | 90 min, tighten | -1.94 (2.78) | negative |
| MV | session-end, market | -2.21 (2.73) | negative |
| MA | session-end, tighten | -3.80 (3.93) | negative |
| CR | 90 min, market | +0.22 (1.97) | PRE -0.26, X' -0.25: DEAD (PRE/X' negative; CR is a single-leg stand-in for a scale-out book with a stored dynamic exit, p(target)=0.15 recent: any exit looks good against a losing recent hold) |
| STACK6 / ALL11 | session-end, tighten | -1.01 (1.20) / -1.16 (1.22) | negative |

The full 65-cell table (PRE, X', HOLD, L6M, R26 on M/N/LIVE-CAL, MDE, touch share, placebo rank, RC p, failed gates) is `tiers.csv`; every window/session slice is `look.parquet` (also per entry session).

## What was scored (68 cell specs x 13 streams = 884 stored cell rows, all appended to DEAD_CELLS.csv as program SDB, side other; UF_TRIALS.json side="decay": n_cells 884, n_effective 1.8)
Data: the THP dp1m+ldp1m 1-min in-trade rows of all 11 books (47,131 library base-bracket trades, 6.72 M decision rows), hold = the library bracket exit on the identical entry; untouched trades stay in the denominator at delta 0. Fills: market exit at the decision second's close, cost 0.995 pt (BASIS_LIVE M); the +1-tick-only variant (0.25) adds +0.745 pt x touch share and is in `look.parquet` (`mean_M_cost1tick`; for the selected STACK6/ALL11 market cells it stays negative: STACK6 G4 -1.59 -> -1.08, ALL11 G4 -1.97 -> -1.46, G3 -0.06/-0.07; only the CR cells are positive on M anyway). Stops (tighten actions) are resolved on the 1-s path, stop first inside a second, gap rule, cost 1.01 (M, N) / 2.45 (LIVE-CAL). Bases: M, N (no target correction), LIVE-CAL (stop-class 2.45).
* G1 hard time exit: 5/10/15/20/30/45/60/90/120 min and the session end, market at the bar close or tighten (stop to entry if in profit, else to -(MAE+5 pts), path-resolved to the original exit). 20 cells.
* G2 progress: exit/tighten at age T (5/10/20/30) if the running MFE < X% (25/50) of the target. 16 cells.
* G3 flat-line: range of the last N (5/10/20) 1-min closes < k (0.5/1.0) x ATR14, in profit or at/under entry, market. 12 cells. (These rarely fire: touch share < 0.5% in most books/windows; only MV-uw fires 20%. The grid was too tight to test the idea; a looser k is a new prereg.)
* G4 edge-based: walk-forward monthly refit on 3 months of closed trades (rows of trades with closed_ts before the month start), E[rem_pts_meas | 14 age bins x 12 unrealised/R bins] and P(target before stop), shrinkage pooled -> book -> book x session -> book x session x vol_tag; exit when E < -0.995 (net of exit cost) / E < 0 / P < 50% / P < 40%. 12 cells. No model for the first 3 months (2023-04..06).
* G5 ATR-time: tau = cumulative ATR14/median-ATR minutes, exit at 15/30/60/120. 8 cells.
Selection per group and stream on the mean of PRE and X' on basis N; the recent windows were read once per group for the selected cells only. Unselected cells have PRE/X' values only.

## DEAD_CELLS lookup (before scoring)
`dead_lookup.py` on the exact grammar found no EXACT/NEAR hit for any G2-G5 cell and none for the tighten actions or the 5/15/45/90/120-min and session-end horizons (`dead_lookup_pre.csv`: 0/68 hits on my token grammar, which differs from the stored one; the family hits below were found by spec-form lookups of F7/THPC1/THLB/UFL5). The family hits are: THPB F7 (profit-side time stop t=10/20/30/60 min, exit if unrealised < +10/20/30; 20 streams, all negative PRE/X', e.g. HM t30 x30 PRE -4.8, KB -2.0, ST -1.4), THPC1 fixed time=10/20/30/60 X=10/20, THLB time-only loss arm, UFL5 stall T=5m. My G1 T in {10,20,30,60} market cells are the unconditional limit of F7 (NEAR-family, not rescored as such; scored here on the new 1-min panel with 0.995 cost and the six-book stack). Hits were reported, not rescored; the new parts are G2-G5, tighten, session end, and per-session columns.

## Controls
* Random-exit placebo at the same exit-age distribution and rate (200 draws market, 30 draws tight; per book, pooled streams use the sum of the book draws): for the 57 negative cells the real result is within or below the placebo cloud on L6M (rank on basis N: min 0.00, median 0.31, max 0.955; only CR G5 reaches 0.95; ALL11 ranks G1 0.27, G2 0.17, G3 0.05, G4 0.62, G5 0.10, i.e. mostly worse than random timing). No decay rule beats random exits at its own timing. Mean placebo delta is itself about -exit cost x touch share, which is why untouched/late rules look "less negative" than prompt ones.
* White RC over each group's cells on PRE+X' (basis N, day bootstrap, 2000): p 0.18-1.00; no group-stream has p <= 0.05 (best: HM G3 p=0.18 on a cell that fires on 0 recent trades, MA G3 0.46). Cumulative-adjusted (143,584 + 884 cells, Bonferroni) p = 1.0 for every non-degenerate cell.
* Tiers by V2 gates (PRE>0 and X'>0 on N; L6M and HOLD >= 0 on M, N, LIVE-CAL; placebo rank >= 0.95 in both samples; RC p <= 0.05; cumulative p <= 0.05; stack not negative).

## Per-contract headline, last 6 months (pts per trade per contract, M / N / LIVE-CAL, selected cell, MDE on N)
STACK6: G1 session-end tighten -0.71 / -1.01 / -0.85 (1.20); G2 progress X25 T20 tighten -0.65 / -0.99 / -0.79 (1.25); G3 flat N10 k0.5 profit -0.06 / -0.07 / -0.06 (0.11); G4 edge-book P40 -1.59 / -2.64 / -1.01 (2.41); G5 ATR-time 120 tighten -0.70 / -1.04 / -0.85 (1.23). ALL11 within 0.3 of these. The magnitudes are about the exit cost times the touch share (0.2-0.7) plus the forfeited wins.

## What the premise is worth (STACK6, L6M, M)
The rules do pick worse trades: P(target) among the trades each rule exits is 0.33-0.37 versus 0.53 for all trades (G1, G2, G4, G5; ALL11 0.33-0.36 vs 0.51). With symmetric 60/60 brackets that is not enough: per trade, saved loss +3.9 (G1), +4.8 (G2), +15.4 (G4), +4.4 (G5) pts versus forfeited wins -4.6, -5.4, -17.0, -5.1 pts, a net -0.7 to -1.6 pt. The signal "no progress in 20-120 min / session over" carries information (target odds drop by ~20 points) but it is smaller than the 0.995 pt exit cost plus the asymmetry between the exited winners and the stop-outs avoided.

## Session column (STACK6, L6M, selected cell N; entry session of the trade; slices below the MDE are noise)
G1 session-end tighten: ASIA -1.87 (2.87), LONDON -2.26 (2.98), PRE +0.88 (8.14, n 331), NY-AM +0.07 (1.69), NY-PM -0.56 (2.24). G2: ASIA -1.31, LONDON -2.12, NY-AM -0.09 (0.82), NY-PM -0.79. G4: ASIA -3.52, LONDON -4.54, NY-AM -1.37, NY-PM -1.70. G5: ASIA -0.58, LONDON -1.86, NY-AM -0.81, NY-PM -1.12. No session has a positive cell beyond its MDE; NY-AM is the least negative everywhere (trades are short, 14 min median, so a time exit rarely fires). Per-book x session slices for every selected cell are in `look.parquet`.

## Horizon: realised time-to-target (descriptive, all windows, no selection role; `time_to_target.csv`, `time_to_target_book.csv`)
The horizon of a 60/60 bracket is not the same across sessions. Six stack books, median minutes (L6M; PRE+X' in brackets): to target ASIA 120 (154), LONDON 68 (75), PRE 20 (29), NY-AM 13 (17), NY-PM 28 (24); P(target) 0.56 / 0.56 / 0.53 / 0.53 / 0.46. Stops come at about the same times as targets (median stop 125 / 80 / 29 / 14 / 26 min), i.e. the bracket resolves with no time asymmetry. By book, L6M, median minutes to target: ST 39, HM 53, KB 51, PE 58, WT 22, SM 77, DN 64, MV 51, PB 68, MA 75, CR 61; share of eventual targets arriving after 30 / 60 / 120 min: ST .57/.42/.27, HM .63/.47/.31, KB .64/.45/.29, PE .66/.49/.31, WT .44/.29/.15. Roughly 30% of the targets of most books need more than two hours, which is why 120-minute-and-below hard exits forfeit a third of the wins.

## Edge-based horizon (G4) and where the edge is "spent"
* The conditional-expectation model has no out-of-sample skill. Calibration of the walk-forward E[rem | age, unrealised] (deciles of the prediction vs the realised remaining pts, `edge_calib_*.csv`): book x session level predicts -14 to +14 pts in the extreme deciles and realises -0.0 / +5.1 (lowest decile PRE+X' / L6M) and -0.8 / +1.3 (highest decile). The lowest-predicted decile does not do worse than the highest; in L6M the order is reversed. The state (age, unrealised) carries no stable information about the remaining pts beyond the book's baseline, so "exit when E[rem] < exit cost" fires on bins that are noise and exits ~70% of trades (touch .59-.90).
* Mean remaining pts by age (descriptive, `edge_by_age_book.csv`, `edge_spent_book.csv`): there is no age at which the average trade's remaining expectancy turns below minus the exit cost and stays there, for any book in the recent half-year (L6M: spent age = never for 9 of 11 books; SM and MV only in the 180+ minute bin on M, n small; PRE+X': DN, MV, PB only in the 180+ minute bin). At 60 min the mean remaining pts (M) is +1.3 WT, +1.6 MV, +1.1 SM, +2.5 ST, +3.8 PE, +4.1 KB, +4.4 DN, +5.5 PB in L6M, -0.8..+3.0 in PRE+X' (mostly below +1.1). "PE's edge is spent after T minutes in session S": not supported; PE's remaining expectancy is not below the exit cost at any age in either sample.
* Hazard rule P(target) < 50/40%: worst of all families (L6M -1.0 to -6.5 N), because the target is hit by ~50% of all entries and the rule exits on the first low-probability bin.

## Lock-engine stack ($/week, exact engine l2s_stack/e2_joint, 6 books, M basis; the engine absorbs the re-entry effect; BASE L6M +65.7k/wk, HOLD +52.4k, PRE +44.1k, X' +20.6k)
Delta vs BASE (MDE): G1 session-end tighten L6M -24.7k (31.5k), HOLD -26.8k (29.8k), PRE -18.9k (28.3k), X' -16.5k (32.0k); G2 X25 T20 tighten -32.4k (37.0k), -27.6k, -31.7k, -26.3k; G3 flat -1.1k (2.2k), -0.9k, -2.1k, +1.2k; G4 edge-book P40 -74.1k (52.1k), -61.4k, -59.7k, -38.3k; G5 ATR-time 120 tighten -13.3k (23.6k), -21.1k, -22.2k, -14.3k. Per-book-selected combos: G1 -24.7k, G2 -34.6k, G3 -0.9k, G4 -72.1k, G5 -16.6k (L6M). R26 (~5 weeks, MDE 50-120k): G2/G5 +12.5k/+12.2k, noise. Only G4 is beyond its MDE (negative). The stack lines are M only (the engine has no N/LIVE-CAL switch here). Re-entry after an early exit adds nothing visible: stack deltas stay at or below the per-contract delta x trade count. File `stack.json`.

## Honest caveats
* Disclosures: before the prereg hash an engine smoke test printed ALL11 whole-sample M means of 10 cells (all negative); the stage-A log printed the whole-sample M mean of every cell (all windows pooled, no per-window recent number) before the selection hash. Neither changed the grid.
* Exit cost 0.995 follows BASIS_LIVE M; the directive's literal "+1 tick" is shown as a variant. Fees (identical in both arms) are not netted into deltas.
* "Tighten" defined here as stop-to-entry (in profit) or stop to -(MAE+5 pts) (at/under entry), with an immediate market exit if price is already through the level. Other tighten definitions (stop to MAE + X for other X, partial exits) are not scored.
* G3's grid almost never fires (the tiers there are zero-effect, not evidence against the idea); a flat-line prereg with k in {1.5, 2} is the one open knob. The CR stream is a single-leg stand-in; its positive recent cells are unreliable and PRE/X' negative.
* The lock engine and the 1-s path arrays load library rows beyond 2026-02-06 internally (as in earlier cycles); no statistic uses post-cut data, and trades/rows are cut at label day 20260206 before any use.
* Windows PRE/X'/HOLD/L6M were looked at hundreds of times by earlier programs; the cumulative-adjusted p of every cell is 1.0 here regardless.

## Policy output
None. No cell is >= 0 on all gates, so no THP_POLICY.txt rule and no DS3_THL2_NEEDS.md entry from section B. (Features that a D6 version of these rules would need and D6 already computes: mins_in_trade and the session clock; nothing new is required.)

## Next
Decay exits fail because the symmetric 60/60 bracket already pays for the horizon and the state variables here carry no stable out-of-sample information on remaining pts. If SD-A (signal invalidation) finds a book-level premise that predicts target odds beyond the ~20-point drop seen here, the hold-or-exit threshold should be re-derived from that, and the combined A+B stack (section D) can be tested; on this evidence B adds nothing to it.
