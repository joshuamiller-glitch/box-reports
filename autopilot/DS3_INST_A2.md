# DS3_INST_A2 - INST-A follow-ups: (a) re-target to unfinished-auction levels, (b) ES / RTY day-structure states as regime (INST-5, written 2026-10-31)

**DATA line.** On disk: the NQ day table of INST-1 (value area, poor high/low, single prints; 778 RTH days), the one-convention engine's 1-s hi/lo/close path (roll-adjusted prices: levels carry the per-day roll offset, 13 roll steps), ES and RTY tick tapes 2023-08.. Derived here (nothing to buy): the same day table for ES and RTY (650 RTH days each, 2023-08..2026-02-06, single-print and poor-tail threshold 3 ticks), 98 ES/RTY/cross states. Prereg `l2vast/ds3/prereg/INST_A2_prereg.md` sha256 `2cc36199...` (full sha in DECISIONS.md), selections logged before the one recent look (part a `f2d8a821...`, part b `2f728d87...`). dead_lookup was run BEFORE scoring but on a sample: the full per-spec run (3,741 specs) was too slow (22 CPU-min for under 1,283 specs), so I searched all 1,382,271 stored specs for the new vocabulary (inst_a2 / tp_at_level: 0 hits) and ran is_dead on 80 random specs (0 EXACT/NEAR, 0 partial). Header time of the prereg (~18:10Z) is approximate; the DECISIONS.md line carries the true time. Caps: 202602, masks 20260206, UNTOUCHED never read, 3 workers.

## Page 1

**Plain sentence.** Neither follow-up produces an edge. (a) Taking profit at an unfinished-auction level (prior poor high/low, single-print edge, prior value-area edge) instead of the book's native exit: of 420 cells only 81 are triggered 40+ times, 10 are positive in PRE and X', and all 10 are inside the noise in the recent look (best K6 UA 10-30 pt band: +0.11 pt per contract L6M, MDE 0.36; stack +0.83k/wk, MDE 1.59k; shuffled-prior-day placebo rank 0.92; the non-poor-high/low control does about as well), 0 PASS, 0 CANDIDATE, 0 STRICT/TOLERANT; a shorten-only chooser at these distances just takes small profits earlier. (b) ES / RTY versions of the day-structure states as a skip regime for the six books: 1,094 of 2,058 cells reach 40 skipped signals, 51 are positive in PRE and X', 19 stay positive in L6M, 13 STRICT, 5 literal TOLERANT, 4 CANDIDATE rows (2 distinct ideas, shadow only, shrunk size 0), 0 PASS; the best, skipping NY-PM/close signals when RTY's overnight inventory is LONG, is +1.35 pt per contract L6M (MDE 2.85; PRE +0.03, X' +0.18; shuffled-frame rank 0.98; Romano-Wolf p 0.79 over the 51), stack +0.71k/wk L6M (MDE 1.56k), PRE +0.01k, so it is positive everywhere but never beyond MDE; nothing is promoted.

Counts (per-contract AND stack gate; literal TOLERANT = headline, TOL-B and TOL-nc post hoc beside):

| part | cells scored | carried (PRE and X' > 0) | L6M > 0 | STRICT | TOLERANT | TOL-B | TOL-nc | NOW-ONLY | CANDIDATE | PASS |
|---|---|---|---|---|---|---|---|---|---|---|
| (a) target chooser | 81 (of 420) | 10 | 6 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| (b) ES/RTY regime | 1,094 (of 2,058) | 51 | 19 | 13 | 5 | 5 | 5 | 16 | 4 | 0 |

STRICT can exceed TOLERANT because TOLERANT also needs the PRE worst-20 test, the stack gate and PRE > 0 (rows count identical vectors twice: ALL_nypmc and K6_nypmc are the same signals). The walk-forward persistence of each column over 2024-26 asked for in the T-SIXTY addendum was NOT computed here (only 51 + 10 carried cells, no per-column history).

### Table 1 - part (b) cells with L6M > 0 (per contract = pts per planned lot, skipped signals removed; stack $k/wk at live lots on the one-convention engine, parity stop, no lock; MDE = 2.8 SE)

| rule (skip when ...) | scope | n skipped | L3M | L6M | MDE L6M | HOLD | PRE | X' | M L6M | LIVE-CAL L6M | stack L3M | stack L6M | stack MDE | stack PRE | stack X' | 12R L6M | shuffle rank | RW p | NQ-own PRE | STRICT/TOL/TOL-B/NOW | tier | persist |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| RTY.INV=long | ALL_nypmc | 228 | +0.68 | +1.35 | 2.85 | +1.09 | +0.03 | +0.18 | +1.35 | +1.46 | +0.34 | +0.71 | 1.56 | +0.01 | +0.08 | +0.12 | 0.97 | 0.79 | -0.78 | Y/n/n/Y | CANDIDATE | +0.47 |
| RTY.DIVERGE_DT1100 | ALL_nypmc | 255 | +1.78 | +1.17 | 3.25 | +1.11 | +0.17 | +0.32 | +1.17 | +1.63 | +1.27 | +0.83 | 1.72 | +0.04 | +0.13 | -0.17 | 0.96 | 0.93 |  | Y/n/n/Y | CANDIDATE | +0.55 |
| ES.P1030=lower | ALL_nypmc | 219 | +0.77 | +0.53 | 2.09 | +0.53 | +0.39 | +0.41 | +0.53 | +0.58 | +0.41 | +0.29 | 1.16 | +0.21 | +0.18 | -0.04 | 0.80 | 0.98 | +0.53 | Y/n/n/Y | DEAD | +0.49 |
| RTY.OL_VA=above | ALL_nypmc | 175 | +0.70 | +0.53 | 2.46 | +0.47 | +0.30 | +0.17 | +0.53 | +0.55 | +0.35 | +0.27 | 1.25 | +0.14 | +0.07 | -0.20 | 0.34 | 0.99 | -0.51 | Y/n/n/Y | DEAD | +0.47 |
| RTY.WITH_BREAK | K6_NY | 512 | +0.79 | +0.32 | 1.74 | +0.15 | +0.04 | +0.20 | +0.32 | +0.23 | +1.67 | +0.77 | 3.14 | -0.14 | +0.18 | +1.03 | 0.84 | 0.99 | -0.76 | n/n/n/Y | DEAD | +0.51 |
| RTY.WITH_BREAK | ALL_nypmc | 319 | -0.06 | +0.31 | 3.23 | +0.02 | +0.22 | +0.44 | +0.31 | +0.40 | +0.79 | +0.64 | 2.09 | +0.05 | +0.23 | +0.59 | 0.62 | 1.00 | -0.93 | n/n/n/n | DEAD | +0.49 |
| ES.IBW=mid | K6_NY | 302 | +0.96 | +0.30 | 1.58 | +0.17 | +0.21 | +0.06 | +0.30 | +0.28 | +1.37 | +0.39 | 2.37 | +0.28 | +0.06 | -0.49 | 0.90 | 0.99 | -0.19 | Y/Y/Y/Y | DEAD | +0.52 |
| RTY.IB_UNBROKEN | ALL_nypmc | 74 | +0.78 | +0.27 | 1.17 | +0.20 | +0.06 | +0.18 | +0.27 | +0.29 | +0.41 | +0.14 | 0.63 | +0.04 | +0.08 | -0.00 | 0.70 | 0.99 | -0.02 | Y/Y/Y/Y | DEAD | +0.52 |
| RTY.DT1100=non_trend | K6_NY | 185 | +0.42 | +0.22 | 0.78 | +0.16 | +0.05 | +0.08 | +0.22 | +0.23 | +0.67 | +0.39 | 0.94 | +0.02 | +0.09 | +0.14 | 0.89 | 0.97 | -0.08 | Y/Y/Y/Y | DEAD | +0.55 |
| RTY.IBW=narrow | K6_NY | 293 | +0.53 | +0.05 | 1.14 | +0.01 | +0.08 | +0.10 | +0.05 | -0.08 | +0.41 | -0.09 | 1.47 | +0.07 | +0.11 | -0.32 | 0.76 | 1.00 | -0.32 | n/n/n/n | DEAD | +0.49 |
| ES.OL_RNG=inside | ALL_nypmc | 398 | +1.59 | +0.04 | 3.25 | -0.18 | +0.02 | +0.49 | +0.04 | +0.12 | +0.81 | +0.06 | 1.35 | +0.01 | +0.19 | -0.15 | 0.55 | 1.00 | -0.24 | n/n/n/Y | DEAD | +0.54 |
| RTY.DT1030=trend_cand | ALL_NY | 151 | +0.08 | +0.03 | 0.54 | +0.03 | +0.18 | +0.06 | +0.04 | +0.04 | +0.57 | +0.33 | 1.90 | +0.59 | +0.17 | -0.47 | 0.82 | 1.00 | -0.16 | Y/Y/Y/Y | DEAD | +0.49 |

Carried but negative in L6M: 32 rows (selection windows do not predict L6M). ES-frame cells carried 20 / RTY 31 of 51; RTY and the cross states supply all 4 CANDIDATE rows. The NQ-own counterpart of the same state is mostly non-positive in PRE (diagnostic column), so the ES/RTY frame is not a copy of the NQ states.

### Table 2 - part (a) target chooser, the 10 carried cells (take profit at the level; per contract = engine delta over rows kept in both baseline and variant; stack = engine delta incl. re-admitted signals; NORM = same band with a non-poor prior high/low)

| cell | triggered | L3M | L6M | MDE L6M | HOLD | PRE | X' | NORM control L6M | P1 shuffled-day rank | P2 random-level rank | stack L6M | stack MDE | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| lvl=SINGLE|band=10-30|scope=ALL_NY | 119 | +0.34 | -0.05 | 0.78 | -0.04 | +0.09 | +0.01 | +0.05 | 0.43 | 0.35 |  |  | DEAD |
| lvl=SINGLE|band=10-30|scope=K6_ALL | 79 | -0.02 | +0.09 | 0.30 | +0.08 | +0.01 | +0.23 | -0.04 | 0.88 | 0.89 | +0.76 | 1.22 | DEAD |
| lvl=VA|band=10-30|scope=M6_nyam | 61 | +0.13 | -0.03 | 0.36 | +0.09 | +0.10 | +0.20 | -0.10 | 0.52 | 0.14 |  |  | DEAD |
| lvl=VA|band=10-30|scope=M6_NY | 61 | +0.13 | -0.03 | 0.36 | +0.09 | +0.10 | +0.20 | -0.10 | 0.52 | 0.14 |  |  | DEAD |
| lvl=VA|band=30-60|scope=M6_ALL | 104 | -0.04 | +0.05 | 0.29 | +0.04 | +0.07 | +0.06 | -0.04 | 0.69 | 0.75 | +0.17 | 0.96 | DEAD |
| lvl=VA|band=30-60|scope=M6_nyam | 66 | -0.03 | +0.06 | 0.35 | +0.04 | +0.04 | +0.02 | -0.01 | 0.72 | 0.71 | +0.12 | 0.67 | DEAD |
| lvl=VA|band=30-60|scope=M6_NY | 66 | -0.03 | +0.06 | 0.35 | +0.04 | +0.04 | +0.02 | -0.01 | 0.72 | 0.71 | +0.12 | 0.67 | DEAD |
| lvl=UA|band=10-30|scope=K6_ALL | 107 | -0.02 | +0.11 | 0.36 | +0.10 | +0.05 | +0.23 | -0.04 | 0.92 | 0.93 | +0.83 | 1.59 | DEAD |
| lvl=UA|band=10-30|scope=K6_NY | 54 | -0.09 | +0.02 | 0.43 | +0.01 | +0.28 | +0.30 | +0.00 | 0.62 | 0.84 | +0.33 | 1.12 | DEAD |
| lvl=UA|band=10-30|scope=M6_ALL | 60 | -0.05 | -0.01 | 0.17 | +0.00 | -0.02 | +0.15 | +0.07 | 0.52 | 0.56 |  |  | DEAD |

Stack lines are computed only for cells positive in L6M per contract (blank = negative). Levels are not special: the NORM control and the random-level placebo give similar numbers at the same distance.

## Method notes and limits
* Re-target = limit take-profit at the nearest level of the set in the profit direction within a distance band, filled when the 1-s high/low touches it before the composite's native final exit (M basis: one tick through); second leg cancelled if not yet filled; stop cost removed. SHORTEN-only: extending the target to a farther level needs a path re-simulation of the stop/target legs and is NOT scored (named gap). The 60-120 pt band produced no cell with 40 triggers. Per-row p0 edit by the delta method; selection used the engine's own pnl-per-p0 map (+0.001 perturbation) with the kept set fixed; the carried cells were re-run exactly (N / M / LIVE_CAL per contract, parity stack incl. 12R) - the exact N values are what the tables show.
* Engine prices are roll-adjusted (additive): the first version of the level builder compared actual prior-day levels with adjusted entry prices and produced no triggers; fixed with a per-day roll offset (engine 1-s close minus actual last at 09:30:30) BEFORE any selection statistic; the prereg level definitions are unchanged.
* Part (b) states use the INST-A vocabulary on the ES / RTY frames (poor/single threshold 3 ticks) plus AGREE/DIVERGE cross states with the NQ frame; ES/RTY frames start 2023-08 and the trailing-60-day cuts about 2023-11, so X' is short for these states.
* Multiplicity: qv.program_validity over the carried cells (RC group p, RW, DSR, PBO) with 420 / 2,058 trial denominators and the cumulative count; no cell survives Romano-Wolf (smallest p 0.70 part a, 0.79 part b).
* DEAD_CELLS +2,498 rows (append_cells, backup DEAD_CELLS.csv.bak_inst5_*; includes the INFO-4 rows). Rows: out/recent_wins/inst_A2.csv. Code l2vast/ds3/code/inst5/, out l2vast/ds3/out/inst5/.
* Structural question (MORNING): none blocking.
