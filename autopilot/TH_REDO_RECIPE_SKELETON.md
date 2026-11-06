# TH_REDO_RECIPE_SKELETON - programs A-F of T-TH-REDO: cells, windows, placebos, nulls, compute (CHAR-A, 2026-11-06; for CHAR-B to freeze preregs). Skeleton only; grids copy DIRECTIVE_T_TH_REDO_20261106.md "Program"; counts are from the published grids (TH_FAMILY_RESCORE_PLAN.md, pages cited there). No compute run.
## Common recipe (all programs)
* Engine: the PROVEN engine after Gate 0 (fixed engine, kfix on, unthinned exit-aware rows, 1-s TH-L2 clock); D7 v1.4 exact base (Q1-A, locks, split, zones HALF), live lots. PRE-PROOF numbers labelled as such.
* Windows: recents method, session by session (asia/london/pre/nyam/nypm/close), L1M..L6M first, then PRE and HOLD; tolerant gate; drawdown first; MDE stated per cell.
* Fills: both bases printed, measured basis M decides (target nominal N shown; 3.39 pt/lot fill artefact).
* Placebos: forward-only shift5 / side / days; random exits of the same count (null for every cell = same number of exits at random times on the same trades, 1,000 draws).
* Family control: Westfall-Young max-stat over the whole program grid (not per book), reporting family p and best-of-F.
* Validation: purged walk-forward with own-parameter refit; carrying week dropped (re-score without the single week carrying most P&L); live week as held-out where marked.
* Phases: PA9 = 9 lock-reset phases. Engine-run cost = finalists x 9 phases x 2 bases x 2 fills = 36 runs per finalist.
* Two-stage design: stage 1 screens all cells on the library/1-s path (cheap, trade-level paired vs own base), stage 2 sends finalists (top by stage-1 plus all frozen controls) through the engine.
## Programs
| prog | cells (screen) | structure | notes |
|--|--|--|--|
| A LOSS L2 | arm 8 x mult 7 x window 5 x persistence 5 x new-extreme 2 = 2,800 per book x session unit; x 11 books x 6 sessions = 184,800 raw (per-book global rule: 11 x 2,800 = 30,800); book-flip triggers 4 (imbalance, iceberg, delta turn, sweep) x ~6 thresholds = 24 per unit; blackout 0-60 min {0,5,15,30,60} x {same side, both} = 10; lot-scaled arm ~3 | persistence cells contain the sustained-cut reading; plus HM a30/3of3/w10 neighbourhood 161 (RETEST grid) | family = all A cells; output best live loss rule per book and policy lines |
| B LOSS L1 | 29,160 per entry (5 eligibility x 3 votes x 9 momentum x 9 stall x 6 efficiency x 2 eval freq); 960 screened per entry as published; combined with A: 2 modes (ReplacePath, AddToPath) x top 10 A = 20 per book | original DS3 TH-loss grid | per-entry paired, replicate published 0/4,800 on the proven engine as a sanity read |
| C PROFIT L2 | ~150 cells per entry (145-153); 30 screened as published; gated take lines pct x ahead_rel x tot_rel x pulled_mult x ice_against (D7 take-line grid, 5 lines + variants); lock-to-BE at pct, scale-out half at pct, trail by book state ~60 | basis N and measured | thick-book multiple/seconds/trail ticks from group-06 |
| D PROFIT L1 | ~150 (PhMin/PhReq/PhTrail) + chandelier/ATR ~60 + time-decay ~20 + scale-out ~20 = ~250 per entry; alone and combined with top 10 C | | |
| E BOTH | top 5 loss x top 5 profit per book = 25 per book; vs loss-only vs plain 60/60; live week held-out (187 trades) | finalists only | no new family; control = A-D families |
| F POLICY | no search | THP_POLICY_D7.txt from E, passing rules only, empty sides stated with reason | |
## Compute estimate (formula; t_run must come from BASE-4 Gate-0 timing)
* Stage 1 (1-s paired screening): ~ cells x trades x seconds-of-path. A: 30,800 global cells x ~25k library trades x 1-s path is one vectorised pass per (arm, window, persistence) combination; estimate hours not days on 16 workers, dominated by the 1-s path loading (~10 min per book to load).
* Stage 2 (engine): finalists F_prog x 36 runs x t_run. Suggested F: A 40, B 20, C 30, D 20, E 25 = 135 finalists -> 4,860 full-history runs; at t_run = 5 min that is ~405 h serial, ~25 h on 16 workers; at t_run = 30 min it is not feasible and F must drop to ~15 per program (phases cut to 3 for non-finalists). CHAR-B: freeze F after BASE-4 reports t_run.
* Nulls: random-exit draws 1,000 per cell are on the stage-1 path (cheap); not on the engine.
* Sequence suggestion: A, C first (live families, bases N and M), then B, D, then E, F.
