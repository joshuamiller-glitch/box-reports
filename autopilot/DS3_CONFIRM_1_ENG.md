# DS3_CONFIRM_1_ENG -- stage 1 (CF-ENG): FVG / inverse FVG / implied FVG / order block / breaker x 14 timeframes x mechanics a, b, c on the 70/30 base
Prereg: CF_ENG_STAGE1_prereg.md sha256 2b14d95caff18240147107874a58f542f044799e30024133f40b60b647ded822 (logged in DECISIONS.md before scoring). PRE u X' selection file out/confirm/eng/s1_selection_PRE_X.json (sha logged in DECISIONS.md) fixed before the one recent look.
Engine: l2vast/ds3/code/confirm/cf_engine.py + cf_events.py (API: cf_engine_API.md); scorer cf1_run.py / cf1_score.py / cf1_finish.py. 560 cells (5 families x 14 TF x {a, b-near/mid/far, c1, c2-near/mid/far}) x 10 books (KB PE SM HM MV PB DN ST WT + MA; CR has no 1-s path), all windows, sessions. Per-trade nets (M, N, +1-tick stress, 5 placebo draws, shifted-day) in out/confirm/eng/s1/<tf>.npz; event streams out/confirm/streams/s1_<fam>_<tf>.parquet; per-book PRE+X' rankings out/confirm/rankings/stage1ENG_<book>.parquet (+POOL).
Unit: pts per PLANNED lot (the unfilled 30% earns 0), delta = paired cell minus the plain 3-pt dip 70/30 split (floor, no gate, M basis). Splits / re-based targets / fixed-distance resting limits are STRUCTURE, not L2 edge. Bases: M and N scored (LIVE-CAL / LIVE-P9 not available yet). Known engine deviation: hold dies at the original stop/target second (13 of 44,370 plain-dip trades differ from lj_kernel.jrun, which fills a dip after the stop second).

## Verdict
No cell passes. Across the 560 pooled cells the mean delta vs the plain dip floor on PRE u X' is about zero (a -0.015, b +0.020, c1 +0.004, c2 +0.018 pt per planned lot) and all mechanics are below market-at-signal (-0.03 to -0.07). White RC over the 560 cells on PRE u X' weekly deltas: p = 0.20 DN, 0.43 HM, 0.89 KB, 0.98 MA, 0.66 MV, 0.17 PB, 0.70 PE, 0.40 POOL, 0.35 SM, 0.74 ST, 0.15 WT -- nothing reaches 0.05 even before the cumulative correction (143,584 earlier cells + 560; stage n_effective = 3.2 by participation ratio, cells are near-copies). Tiering: PASS none. CANDIDATE-RECENT (weak, RC p > 0.05, fails cumulative gate): DN iFVG 1m c2-near. All others BEST-AVAILABLE-NEGATIVE or DEAD (placebo / recent). MV iFVG 2m c2-far passes the prereg gates on M but is negative on N (L6M -0.16) and 2026 (-1.01), so it is not carried (profit rule: >= 0 on N).
The floor has not moved: no cell beats the plain 3-pt dip split reliably in the last 6 months for any book once the PRE u X' selection is applied.

## What PRE u X' (selection data only) says in aggregate (pooled 9 books, mean over cells)
By family delta vs floor: OB +0.041, implied FVG +0.030, iFVG +0.002, FVG -0.003, breaker -0.007. By timeframe: 15 s -0.054, 30 s -0.022, 45 s -0.002, 1 m +0.004, 2 m +0.031, 3 m +0.037, 5 m -0.004, 10 m -0.017, 15 m +0.012, 30 m +0.065, 1 h +0.029, 4 h/1 d/1 w +0.03 (fill 0.0-1.5%: they almost never fire; the positive number is the unfilled-30% structure). Fill rate (pre): 78% at 15 s, 64% at 1 m, 38% at 5 m, 14% at 30 m, 8% at 1 h, ~0 at 1 d/1 w. Placebo (5 draws; random-level for b/c2, time-matched random for a/c1) averages +0.02 to +0.06 on PRE u X', i.e. as large as the real cells; only 17.7% of the 560 cells beat the max of their 5 placebo draws. Shuffled-day structures average -0.03 to +0.03 (same). Mean delta vs market-at-signal is -0.04 (every mechanic worse than not waiting).

## Selected cells (top-3 per book on PRE u X' by delta vs floor, fill >= 10%; ONE look at recent windows). delta vs plain-dip floor, pts per planned lot (MDE in parentheses where shown); stack = lock-engine $/wk delta vs the floor stack (engine books only)
| book | cell (family TF mech level) | PRE | X' | L6M (MDE) | HOLD | 2026 | L6M fill | L6M N | L6M +1tick | stack L6M $/wk | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|
| DN | iFVG 2m b far | +0.86 | +0.35 | +0.89 (1.83) | +0.86 | +0.86 | 58% | +0.75 | +0.84 | n/a | DEAD (placebo: beaten in L6M, not on X') |
| DN | iFVG 1m c2 near | +0.79 | +0.40 | +0.16 (1.48) | +0.29 | +1.84 | 68% | +0.05 | +0.13 | n/a | CANDIDATE-RECENT (weak) |
| DN | OB 10m a | +0.51 | +0.97 | -0.99 | -0.71 | -2.72 | 40% | -1.42 | | n/a | BEST-AVAILABLE-NEGATIVE |
| HM | OB 45s b mid | +0.63 | +0.39 | -0.93 (1.34) | -0.65 | -0.58 | 61% | -1.15 | -0.88 | +765 | BEST-AVAILABLE-NEGATIVE |
| HM | iplFVG 3m b mid | +0.51 | +0.33 | -0.53 | -0.41 | +0.34 | 64% | -0.73 | -0.58 | -930 | BEST-AVAILABLE-NEGATIVE |
| HM | OB 45s c2 mid | +0.49 | +0.34 | -0.13 | +0.08 | -0.02 | 57% | -0.33 | -0.37 | +2241 | BEST-AVAILABLE-NEGATIVE |
| KB | iplFVG 1m b far | +0.57 | -0.09 | +0.64 (0.82) | +0.52 | +1.34 | 73% | +0.56 | +0.60 | +6249 | DEAD (placebo; closest to a lead, see below) |
| KB | iplFVG 1m c2 mid | +0.56 | +0.13 | +0.31 (1.29) | +0.15 | +1.04 | 66% | +0.16 | +0.22 | +2532 | DEAD (placebo) |
| KB | iplFVG 1m b mid | +0.57 | -0.10 | +0.37 (1.14) | +0.20 | +1.18 | 73% | +0.26 | +0.37 | +4904 | DEAD (placebo) |
| PE | iFVG 2m c2 far | +0.67 | +0.30 | +0.25 (1.34) | +0.22 | +1.10 | 59% | +0.05 | +0.22 | -2563 | DEAD (placebo) |
| PE | iFVG 2m c2 mid | +0.58 | +0.24 | +0.19 | +0.05 | +1.39 | 61% | -0.01 | +0.16 | -1018 | DEAD (placebo) |
| PE | iplFVG 3m b near | +0.47 | +0.35 | +0.29 (1.17) | +0.21 | +1.96 | 59% | +0.05 | +0.25 | -1340 | DEAD (placebo: L6M plac max +0.95) |
| SM | OB 45s b mid | +0.62 | +1.98 | -0.37 (2.56) | -0.76 | +1.60 | 64% | -0.58 | -0.59 | +508 | BEST-AVAILABLE-NEGATIVE |
| SM | iplFVG 30s b near | +1.13 | +0.66 | -0.56 | -0.66 | -0.34 | 79% | -0.69 | -0.56 | -801 | BEST-AVAILABLE-NEGATIVE |
| SM | OB 45s b near | +0.11 | +2.29 | -0.40 | -0.78 | +1.63 | 68% | -0.59 | -0.46 | -315 | BEST-AVAILABLE-NEGATIVE |
| ST | OB 30s c2 far | +0.22 | +0.91 | -0.79 (1.23) | -0.77 | -1.36 | 54% | -1.05 | -0.87 | -2284 | BEST-AVAILABLE-NEGATIVE |
| ST | OB 2m b near | +0.25 | +0.74 | -0.47 | -0.29 | -1.48 | 41% | -0.84 | -0.61 | -2213 | BEST-AVAILABLE-NEGATIVE |
| ST | OB 2m c2 near | +0.20 | +0.74 | -0.63 | -0.40 | -1.44 | 40% | -1.00 | -0.75 | -7271 | BEST-AVAILABLE-NEGATIVE |
| WT | OB 2m a | +0.25 | +0.64 | +0.18 (0.82) | +0.35 | -0.01 | 43% | -0.24 | | -2880 | DEAD (placebo; N < 0) |
| WT | breaker 3m c1 | +0.37 | +0.34 | +0.10 (0.77) | +0.21 | -0.09 | 24% | -0.46 | | -6152 | DEAD (placebo; N < 0) |
| WT | iplFVG 10m c1 | +0.38 | +0.34 | +0.08 (0.79) | +0.20 | +0.41 | 35% | -0.38 | | -8689 | DEAD (placebo; N < 0) |
| MV | iFVG 2m c2 far | +0.41 | +0.46 | +0.03 (1.43) | +0.04 | -1.01 | 61% | -0.16 | -0.02 | n/a | passes M gates, fails N / 2026 -> not carried |
| MV | FVG 15m c2 mid | +0.56 | +0.14 | +0.09 | +0.19 | -0.27 | 30% | -0.32 | +0.09 | n/a | DEAD (placebo) |
| MV | iplFVG 30s b near | +0.56 | -0.02 | -0.10 | -0.17 | -0.79 | 78% | -0.20 | -0.12 | n/a | BEST-AVAILABLE-NEGATIVE |
| PB | iplFVG 30m b far / c1 / c2 far | +0.93 / +0.88 / +0.83 | +0.51 / +0.17 / +0.12 | -1.24 / -1.23 / -0.95 | -0.87 / -1.03 / -0.62 | -0.93 / +0.02 / -1.13 | 31-45% | all < -1.3 | | n/a | BEST-AVAILABLE-NEGATIVE |
| MA | iplFVG 2m a; iplFVG 5m b far; OB 1m b mid | +0.43 / +0.60 / +0.17 | +0.22 / -0.27 / +0.50 | -0.56 / -0.89 / -0.91 | -0.55 / -0.74 / -0.92 | -0.46 / -0.45 / +0.63 | 65-88% | all < -0.6 | | n/a | BEST-AVAILABLE-NEGATIVE |
| POOL (9 books) | OB 1m c2 far; OB 45s b mid; iplFVG 10m b near | +0.17 / +0.16 / +0.20 | +0.40 / +0.40 / +0.29 | -0.02 (0.72) / -0.08 / -0.27 | -0.01 / -0.02 / -0.16 | +0.28 / +0.07 / -0.35 | 46% / 57% / 35% | -0.31 / -0.30 / -0.69 | | n/a | BEST-AVAILABLE-NEGATIVE |
Every L6M delta is inside its MDE (0.7-3.0 pt). Full rows incl. sessions (asia/london/pre/nyam/nypm, L6M and PRE), controls, 2026, per-window CIs: out/confirm/eng/s1_selected_recent.csv. Session note for the one weak candidate (DN iFVG 1m c2-near, L6M delta by session): asia -0.82, london +0.39, nyam +0.47, nypm +0.16, pre +3.4 (n=34); PRE asia +1.39, london +0.67, nyam +0.42, nypm +1.18 -- the L6M gain is the pre-market sliver, not a stable session.

## Plain sentences
- Holding the KB signal for an implied FVG on the 1-minute tape and resting the 30% at its far edge (b-far) adds +0.64 pt per planned lot in the last 6 months (MDE 0.82, fill 73%, N basis +0.56, +1-tick stress +0.60, lock-engine KB stack +$6.2k/wk) -- but the PRE+X' delta was +0.57 / -0.09 and its PRE+X' delta (+0.37 pooled) did not beat the max of its 5 random-level placebo draws on PRE (+0.44); in L6M it does beat them (+0.64 vs +0.51), RC p(KB) = 0.89 over the stage: DEAD by gate, flagged as the nearest-to-a-lead (the effect is a deeper-than-3-pt resting limit, i.e. structure).
- Holding a signal for a market entry at the confirmation (mechanic a) adds nothing: pooled delta vs the plain dip floor -0.015 on PRE u X' and -0.07 vs market at signal.
- Resting the 30% at a 5-minute FVG CE instead of a plain 3-pt dip: pooled PRE u X' delta for 5m FVG b-mid is in out/confirm/rankings/stage1ENG_POOL.parquet (cell confirm|fam=FVG|tf=5m|mech=b|lvl=mid); it was not selected in any book's top-3 and is not read in the recent windows.
- The best confirmation overall in this stage (POOL, selected on PRE u X') is the 1-minute order block with a limit at its far edge after the 3-pt dip (c2): -0.02 pt per planned lot in L6M (MDE 0.72) -- indistinguishable from the floor.

## Controls and caveats
Random-level placebo / time-matched random / shuffled-day are computed for all 560 cells (columns plac_d_px, plac_dmax_px, shift_d_px in the rankings); on average they are as large as the real cells. Only 5 placebo draws per cell, so "placebo-beaten" = beats the max of 5 (p ~0.17 per window). 4h / 1d / 1w and >= 1 h cells fill < 10%: ranked out (reported in the rankings with ok_fill False). The one-sentence mechanism per family is in the prereg. Higher-timeframe cells are essentially the unfilled-30% structure.
Bookkeeping: DEAD_CELLS.csv +593 rows (program CFENG1: 560 pooled cells with PRE/X' values, 33 selected with recent values), UF_TRIALS.json confirm cycle 1 (560 cells, n_effective 3.2). Policy text: none (no PASS and no CANDIDATE that survives N).
Next (stage 2 suggestions, not done): KB implied-FVG 1m b-far is the only cell positive in 4 of 5 windows with a positive stack; retest it with the structure-stop variant and 100%/pure-wait bases before anything else.
