# DS3 T-BRACKET-PM FINAL (PROVISIONAL until direct replays land) - D3BL

Written 2026-10-27T09:18:40Z. Research only; no live recommendation. Status: provisional. Section A for tier 1 (D3BA, 21 cells PENDING_DIRECT, direct replay 30/45 months at 09:05Z) and sections B and C (D3NT nt_direct and the T2 agent's so3_direct replays, under the replay governor) have not scored. Everything below is mapped-screen except where stated.

## Verdict line
Brackets: 0 PASS, 0 CANDIDATE (+9 mapped-only PENDING_DIRECT, all sections). Best shape: none. Near-target: PENDING (nt_direct replay running under governor; scores after WF months land), diagnostic ratio n/a. Scale-out: PENDING (so3_direct replay running under governor). Pyramiding risk-constant: 635 cells scored, 0 PASS/CANDIDATE (all DEAD). Combined best on n/a: +$n/a/wk, maxDD delta n/a, CI [n/a]. Trade Health: 5928 cells scored, 0 PASS/CANDIDATE (cut EV: see rows).

## Scope and registry
l2vast/ds3/out/BRACKET_ENTRIES.json (+ .md): 48 entries. Tier 1 (active): ST10, HM10, KB, SM, EM. Tier 4 (active): 6 PRO2 + 8 PB3 pullback direct-series entries (row maps l2vast/ds3/out/bracket/rowmap/). Trend survivors: not run (mapped-only entries, stop/limit entries cannot be priced by the market-only direct arms). All other registry entries are paused. TB entries are marked unverified (entry price and bracket not stored).

## Cells scored (rows files in l2vast/ds3/rows/)
| section | scope | cells | result |
|--|--|--|--|
| A bracket shape | tier 1 (D3BA) | 21 | PENDING_DIRECT; scores when 45 direct months land |
| A | tier 4 | 392 | 391 DEAD, 1 mapped CANDIDATE (PB3F t45/s75 +3.06 [0.70,5.73], MDE 3.6): redundant with PB3D_R3_P2 (reverts a 2R base to 1R); 11 cells with CI lower bound >0 vs about 9.8 by chance |
| B near-target | tier 1 + tier 4 | 0 | PENDING (nt_direct replay running) |
| C scale-out | tier 1 + tier 4 | 0 | PENDING (so3_direct replay running) |
| D pyramiding | tier 1 | 215 | 215 DEAD (D3PY; trail-only exits are the only positive pooled cells, handed to A/G4) |
| D | tier 4 | 420 | 418 DEAD, 2 mapped CANDIDATE on PRO_ER5_EMA5 (D4_N15 +2.19 [-0.01,+4.59], D4_SG +0.81): original-stop variants, not risk-constant, smallest entry (637 trades, MDE about 3 pts), best of 30 |
| G1 loss-side TH | tier 1 | 4,800 | all DEAD; live TH rule negative on all 5 entries (ST -1.80, live-join profile -2.00 pts/trade, MDE 2.2); best of 960 does not beat the random-timing best-of-960 |
| G1 | tier 4 | 420 | all DEAD; TH_LIVE_ST negative on 14 of 14 |
| G2 profit-side TH | tier 1 | 150 | all DEAD |
| G2 | tier 4 | 420 | all DEAD, every entry's median cell negative (-1.5 to -6.8 pts/trade) |
| G3 new mechanisms | tier 1 | 138 | all DEAD |
| E / G4 combinations | - | 0 | not run: no robust PASS/CANDIDATE exists in A-D or G, and the mapped-only candidates are redundant or best-of-N (lead's instruction) |

Total: 7,000+ cells across A-D and G; 0 PASS; 0 direct-verified CANDIDATE. 3 mapped CANDIDATEs on tier 4 are registered in l2vast/struct48/paper_all/ds3_T4A_* and ds3_T4D_* with mapped-only caveats.

## Multiplicity
Leaderboard section 'Multiplicity' in autopilot/BRACKET_LEADERBOARD.md: cells with paired CI lower bound >0 are far below the 2.5 percent chance count over all scored cells (14 against about 174 at the last build), so the grids are no better than noise at the cell level. Best-of-N nulls: G1 best-of-960 matches random-timing cuts on every entry; A tier-4 median per entry is negative (-0.2 to -1.4 pts/trade).

## What this says (provisional)
- No bracket shape, pyramiding rule or trade-health rule beat the entry's own base bracket on identical entries on the mapped screen. Pyramiding pooled -0.5 to -4 pts/trade; the live TH-loss rule is negative everywhere.
- The only positive pooled signal is trail-only exits (D3PY): not yet scored in A/G4; candidate for follow-up if directed.
- The nulls are not strong nulls: paired MDE is about 1.5-2.7 pts/trade on large entries and 3-6 on small ones; effects below that could not be seen.

## Open items before this becomes final
1. D3BA tier-1 section A: direct months 30/45; finalises automatically at 45 done markers. Tier-4 section A used D3BA's interim calibration (calib_coef.pkl); rerun (about 15 min) if it recalibrates.
2. B and C scoring after their replay markers cover the WF months (report them as pending until then).
3. Equal-risk columns: present in the tier-4 rows; tier-1 G1 rows have none (per-trade deltas only).
4. Parameter-level NT8 specs through D3X: none requested (no PASS).
5. Update this file and the leaderboard when 1-2 land.
