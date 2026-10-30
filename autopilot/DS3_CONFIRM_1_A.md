# DS3_CONFIRM_1_A - stage 1A: volume-profile and VWAP-band confirmations on the 70/30 base (CF-A, 2026-10-30)
Research only; UNTOUCHED never read; masks capped 20260206 (Y26, L3M 20251106.., L6M, HOLD, PRE, X'). Prereg l2vast/ds3/prereg/CONFIRM_S1A_prereg.md sha256 fb2be159c1b31d4939eb4a44d42b62326c835ba721e8a6d539480d15f47ed405 (DECISIONS.md, before any statistic). Selection files hashed before the recent look: sel_stats da973a9f...eea636, selpl_stats 215de818...526345, sel_pick.json e364a96e...625c72; recent_stats 5227204e...91f35fd (one look). dead_lookup 0/300 hits; 300 cells appended to DEAD_CELLS.csv (program CFA1), UF_TRIALS side=confirm n_cells=300 (cumulative 143,884). Code l2vast/ds3/code/confirm/{cf_levels_profile,cf_levels_profile_test,cfa1_cells,cfa1_score,cfa1_placebo,cfa1_stack,cfa1_streams}.py; outputs l2vast/ds3/out/confirm/cfa1/.

## Verdict
**0 PASS / 0 CANDIDATE / 300 DEAD.** Holding the 30% slice of the 70/30 split for a POC / VAH / VAL / HVN / LVN / naked-POC / VWAP-band touch (market at touch, resting limit, dip+touch, limit after dip) never beats the plain 3-pt dip split in money: per planned lot (the quantity that scales with dollars) 0 of 300 cells are >= 0 vs the floor in L6M and HOLD, 0 in PRE, 0 in PRE and X' together (L6M best -0.42, HOLD best -0.32, PRE best -0.35 pt/planned lot; MDE ~0.15-0.2). Max t over the 300 cells: PRE -1.55, X' +1.17, L3M +0.56, L6M -1.13, HOLD -0.92 (RC/Bonferroni p ~ 1.0 in every window; no cell near a multiplicity threshold).
**The per-contract headline is a weighting artefact (STRUCTURE).** On pts per contract of the final position, 114 of 300 cells are positive vs the floor in L3M/L6M/HOLD (up to about +3.3 per contract, fill 30-55%). That arises because trades whose level is never touched are straight-up winners (about +22 pts per contract) carrying only 0.7 lots, and filled trades are averaged over a larger final size; the same cells lose per planned lot and in the lock-engine stack. Per-contract is reported first as directed but must not be read as an edge.
**Level information is nil beyond distance.** Random-level placebo (distances permuted within book x session, 30 draws, N): effect of the real level over the placebo in L6M: mean -0.07 (range -0.21..+0.08), ranks mean 0.30; PRE effect mean -0.02, X' +0.15, ranks 0.56/0.81 with several X' ranks 1.0 (not confirmed in PRE or recent). So a deeper add is what changes the numbers, not which level it is.

## Best cell per family (PRE+X'-selected, per planned lot, delta vs 70/30 plain-dip floor, basis N, ENG6; the stack lines are in the next table)
| family | cell | Y26 | L3M | L6M | HOLD | PRE | X | fill L6M | per-contract delta L6M |
|---|---|---|---|---|---|---|---|---|---|
| POC | CFA1|poc|sw15|c2_3 | -0.46 | -0.05 | -0.66 | -0.55 | -0.35 | -0.02 | 0.18 | +1.06 |
| VAH | CFA1|vah|ANY|b | -0.60 | -0.16 | -0.69 | -0.54 | -0.38 | +0.27 | 0.33 | +1.68 |
| VAL | CFA1|val|ANY|c2_8 | -0.28 | +0.05 | -0.76 | -0.75 | -0.39 | -0.05 | 0.31 | +1.93 |
| HVNLVNNP | CFA1|hvn|week|b | -1.31 | -0.35 | -0.90 | -0.76 | -0.47 | +0.17 | 0.06 | -0.66 |
| VWAP | CFA1|b1|day|c2_8 | -0.72 | -0.18 | -0.95 | -0.74 | -0.39 | -0.10 | 0.12 | +0.26 |
## Stack (exact lock engine, 6 books, $/wk, basis N; M basis in stack_lines.parquet; all picked cells below the floor in PRE, X' and L6M)
| row | Y26 | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|---|
| floor 70/30 plain 3-pt dip | 37.0k | 31.3k | 79.1k | 66.7k | 61.8k | 18.2k |
| market at signal | 18.9k | 11.1k | 61.5k | 48.3k | 58.0k | 16.0k |
| val ANY (nearest anchor) b | 53.4k | 32.8k | 71.6k | 57.4k | 45.7k | 15.0k |
| val ANY c2_8 | 50.2k | 28.2k | 68.0k | 52.6k | 44.0k | 19.7k |
| poc sw15 c2_3 | 48.2k | 21.3k | 61.9k | 51.0k | 40.5k | 17.1k |
| vah ANY b | 28.5k | 8.6k | 56.3k | 47.9k | 37.7k | 28.2k |
Only Y26 and L3M show the VAL-anywhere cells above the floor (5 and 6 weeks of data; not selectable, "L3M only"); L6M, HOLD and PRE are all below. On M (measured with target-fill correction) every row is negative-to-flat in L3M.

## What was built (level generators, causal, closed-anchor)
cf_levels_profile.py: POC/VAH/VAL (70% value area), HVN/LVN (smoothed profile peaks/troughs, 3 each), naked POCs (day, week; dead at first retrace) for anchors sess (previous completed D6 session), day, week, month, 15-m and 1-h swing legs (fractal 2/2, known at the 2nd confirming bar close); VWAP + 1/2/3 sigma anchored day open, RTH open, week, month, last confirmed 15-m swing low/high. 1-s tape (bars2) shifted per day onto the back-adjusted study path (constant per-contract offset, 0 inconsistent days). Truncation causality test cf_levels_profile_test.py: 0 mismatches of 6.3M (cut 20250117) and 2.4M (cut 20231101). Streams exported in cf_engine.Events format (76 files out/confirm/streams/cfa1__<kind>__<anchor>.parquet, INDEX cfa1_INDEX.txt; profile levels as one event per closed anchor and direction, VWAP bands re-sampled every 15 min; mitigation = first touch) plus first-touch indices per cell (streams_touch.npz) for CF-COMBO. Single-confirmation rankings (PRE+X' only, N, per-contract and per-planned-lot delta; cols cid, name, n, fill, dS, x, ranks) in out/confirm/rankings/s1a_<book>.parquet for ENG6 and the 11 books.

## Limitations (stated)
Volume profile from 1-s bar volume spread uniformly over [low, high] (not tick prints); VWAP price (h+l+c)/3 per second; VWAP level frozen at arming (live-moving VWAP touch not modelled); level must be on the adverse side at 1 pt .. stop-1 pt (no 'reclaim from below' variant); sessions/weeks from label days (week = ISO week of label days). Splits, multipliers, re-based targets are STRUCTURE. Per-book numbers (11 books) are in recent_stats.parquet group column; lock engine only for the 6 engine books. Quant layer: no cell reached CANDIDATE-RECENT, so DEAD rows carry RC (max-t) and 30-draw placebo ranks only; DSR/PBO/CV/latency/capacity not run; qv.py not yet available. Controls not run: shuffled-day structures, time-matched random confirmations (random-level placebo only). Placebo draws 30 (not 200). Trade-level per-contract CIs via day-clustered SE (seS in the stats tables).
## RECENT_WINS
out/recent_wins/CF-A.csv: 114 rows (per-contract delta vs floor > 0 in L3M), all labelled STRUCTURE / DEAD / L3M-only; 60 cells are also positive per planned lot in L3M only (negative in L6M, HOLD, PRE).
