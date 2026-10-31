# FWD_AB_SETS - forward A/B of two DualStrat2 parameter sets (trackFWD; report-only; numbers only)

- SET A (live): live: 14 lots, pb -2R/+5R, cap 8R, give-back 2R/keep50, week floor 8R
- SET B (user set): A with cap removed, week floor 12R, Asia 14 / London 10 / NY 10 lots
- B keeps give-back arm 2R/keep 50%; BEST5-exact (keep 67% after 2 trades) NOT included
- Engine: exact 1-s lock engine (firmlib/ds2lib), pair trades regenerated on the 1-s tape. **Fills: forward weeks: flat natural fills (no L2 replay available); history/dry-run weeks: corrected P9 points.** Weekly $ at 14/14 report scale (8/8 x 1.75). Natural fills differ from P9 execution; on history (WF weekly mean) A: P9 $22,759 vs natural $29,917, B: P9 $32,791 vs natural $32,482.
- Tape in nt8sim ends label day 20261030 (2026-10-30 20:59:00 UTC). Live column: <repo>/data/live/StratTrades_DualStrat2_<acct>.csv.
- Official 4 weeks = ISO W44..W47; W43 is informational (pre-decision). **4 weeks cannot decide anything; no verdict is given.**

## Weekly table ($, 14/14 scale; live column = realised StratTrades pnlNet, live account size)

| week | role | status | A net | A trades | A worst day | B net | B trades | B worst day | B - A | live net | live trades | fill |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 2026-W43 | info | DONE | -134,500 | 49 | -68,420 | -86,278 | 53 | -67,742 | 48,223 | -189,750 | 49 | natural |
| 2026-W44 | official | DONE | -135,078 | 10 | -67,607 | -45,769 | 32 | -67,607 | 89,308 | -63,815 | 33 | natural |
| 2026-W45 | official | PENDING | - | - | - | - | - | - | - | - | - | nt8sim tape ends label day 20261030 (needs 20261106) |
| 2026-W46 | official | PENDING | - | - | - | - | - | - | - | - | - | nt8sim tape ends label day 20261030 (needs 20261113) |
| 2026-W47 | official | PENDING | - | - | - | - | - | - | - | - | - | nt8sim tape ends label day 20261030 (needs 20261120) |
| 2026-W42 | dry-run (pre-forward, P9 points) | DONE | 125,895 | 35 | 18,787 | 104,688 | 35 | -1,922 | -21,207 | - | - | p9 |

## Running table (official weeks only, cumulative from W44; maxDD on the daily path)

| through | weeks | A cum | A wk mean | A maxDD | A worst day | A worst wk | B cum | B wk mean | B maxDD | B worst day | B worst wk | live cum |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 2026-W44 | 1 | -135,078 | -135,078 | 135,078 | -67,607 | -135,078 | -45,769 | -45,769 | 135,078 | -67,607 | -45,769 | -63,815 |

## Final 4-week summary

PENDING (1/4 official weeks scored). Table appears when W44..W47 are all DONE.

Dry run: 2026-W42 (last pre-forward week, P9 points) A 125,895 / B 104,688; natural-fill equivalents A 116,134 / B 101,718.
