# DS3 T-BRACKET-PM section C (scale-out) - STATUS (S48-T2 agent, 2026-10-27)

**STATUS: PREREGISTERED, TAPE LAYER BUILT, DIRECT REPLAY NOT YET RUN. 0 cells scored: 0 PASS, 0 CANDIDATE, 0 DEAD from this track.** Nothing below is a result; the nearest scored evidence is T2 SO / SO2 / SO2 (all DEAD: direct two-leg central -0.15 pts/trade [CI includes 0], holdout negative, mapped +1.04 was an artifact of the stop-join credit).

## Frozen preregs (before any scored cell; DECISIONS.md lines 2026-10-26T17:48Z; ledger +145 cells)
29 cells each, one prereg per entry, same design: f {33,50}% x first exit {0.5R,0.75R,1R} x remainder {2R, trail 30} x remainder stop {unchanged, breakeven} (24) + f50/L1R breakeven+5 with 2R and trail30, 1.5R target, trail 20, and f50/L0.5R next-level (1R) target (5). Neighbours one-step along f, L, remainder, stop. Mechanism, predicted effect (0 or slightly negative; breakeven stops -0.3..+0.2 pts/trade), MDE (about 0.4-0.8 pts/trade; up to ~1.2 for the 1-2k-trade books), nearest scored cells and results are in each file.
| entry | prereg | sha256 |
|---|---|---|
| ST10 | l2vast/ds3/prereg/DS3_TSO_ST10_prereg.md | b8c332ae77483611abe345c12e78c44fcce7c572cfb3df5255372928348418ae |
| HM10 | l2vast/ds3/prereg/DS3_TSO_HM10_prereg.md | 7b7c08251ec4507c55799a8158875c4bdbb5deb72d2df4dd0cc72e2888746385 |
| KB | l2vast/ds3/prereg/DS3_TSO_KB_prereg.md | 3183f9fba9076933451c18ffd96e143ab703eecd007b34705c1da63777c54c8c |
| SM | l2vast/ds3/prereg/DS3_TSO_SM_prereg.md | ba2f3aaba7e9ec24b4dc3611ce03d1f2f548f93ed107cbdc43a3406e3dfec33a |
| EM | l2vast/ds3/prereg/DS3_TSO_EM_prereg.md | 910b739f52a39235575729412cc037a112fec77634347fc807d32bf15a9aa1d2 |

## Built (all CPU-only, no replay launched)
- code/tso/so3_cells.py (29 cells, neighbours), so3_tape.py (1-s tape geometry for 17 remainder rules incl. breakeven / breakeven+5 / trail / 1.5R / next level; per-ratio bracket row files; event lists), so3_direct.py (governor-compatible orchestrator + month worker: all five entries in one pass over each month's mbp-10 file, arms (qty,ratio) incl. the two-leg 5+5 / 3+7 lot splits, XJ stop-join exits, leg-B trail/BE/force exits and the placebo partial-exit grid), so3_score.py (assembly of the two legs with the sequential-sweep leg-B entry price, firmlib per-book-lock engine, 50-contract pass, paired test with 10,000 session-block draws, shape-level placebo (i)(ii)(iii) by grid recombination with the SO2 bias correction, 1.5x/2x, long/short, session, quiet/wide, by year, equal_risk columns, verdict). so3_score.py has NOT been run (no replay data yet) and is untested.
- out/tso/<ENTRY>/{geo.npz, events.parquet, rows_r*.parquet} for ST10, HM10, KB, SM, EM (rows = the registry trade lists; ei = signal_id).
- Note for the whole box: l2vast/failpred/econlib.py (and everything that imports it, e.g. struct48/code/t2lib.py) no longer imports: the benchmark rows regenerate to 14,488 against the 14,486-entry P9 table (a data refresh). The section-C code therefore uses firmlib only.

## Why the replay has not been launched, and what it needs
Workload for the five core entries (28k trades, 12 arms, ~430k exit/placebo events): about 3x the SO2 replay, i.e. ~70 worker-hours for the 33 WF months (~100 with the 2023 span). The 14 tier-4 pullback entries would add ~2x more (two of them, PB3E/PB3F, have their own non-60/1R base brackets and need a different base arm) - not feasible at the governor's share; I propose they be screened only after the five core entries, and direct-replayed only if a core entry shows a positive paired CI.
The replay governor (replay_governor.py) only throttles orchestrators named in its PRIO/WKEY lists. To run this track under it, replay_governor.py needs the key 'so3_direct.py orch' (worker key 'so3_direct.py worker' is already matched by its '_direct.py worker' pattern). I did not edit the governor, and did not launch any worker. Requested of the lead: (1) add the key; (2) launch `python3 l2vast/ds3/code/tso/so3_direct.py orch 2` (it is month-major, WF months first, 2023 span last, skip-if-done) or tell me to; (3) re-invoke the T2 agent when /mnt/l2/l2vast/ds3_tso/done_* covers the 33 WF months to run `so3_score.py <ENTRY> pre`, write the pre-holdout text, log the holdout look once per prereg group and run `final`.
Coordination: cells A, D, G stay with D3BL's worker, B with D3NT; section C is only in these five preregs, no overlap.

## Verdict line
Scale-out: not scored. Prior from SO/SO2: DEAD (paired mean -0.03..-0.24 pts/trade, CIs include 0, holdout negative); the new breakeven-stop cells are the only genuinely new mechanism.