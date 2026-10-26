# REPORT DDMIN - comprehensive drawdown study of the live pair (levers A, B, C, D, E, F searched jointly; in-sample and walk-forward side by side)

**Verdict: NO ROBUST CELL.** 136,720 cells were scored (89,494 unique pair-side evaluations in the library incl. refinement; 255 reference rows). The in-sample composite best (lowest DD52 at >= 90% of live net, sleeve edge 50%) is c 3/5/4 ; tabs live/g60/t1.5/live ; tgt 5/offR flr 1.5/3R cap 12 arm 1R gb80% start 0000 dayflr 4 wkflr 10 pbwk off wkGB off maxtr off ; E K4u 20%, CL240 20%, BM13 10% (net 90% of live, CVaR5 -$49k) against live DD52 $245k, but it does not clear the pre-registered gates: the walk-forward on the cell choice at the composite objective is NEGATIVE (WF-A pair-side levers: OOS DD52 $214k on 53% of live OOS income vs live $245k; WF-B all levers incl. sleeves: OOS DD52 $187k on 26% of live OOS income vs live $245k), the best-of-N null ranks the in-sample best at 0.55 (20 null worlds), and see sections 2-4 for plateau, matched-null and span checks. No live change is recommended.

**Secondary objectives.** On the SECONDARY objectives the pre-registered gates are passed by the best cell at worst@80%, worst@90% (section 3b); these are tail-risk (CVaR5 / worst week) improvements that do NOT reduce DD52 (the same cells have DD52 above live) and rest on the research WT-10 book as an 8-contract third book with ST removed, which is itself replication-failed; see section 7.

Power of the search (section 2): a planted rule that removes 50% of the worst-decile weekly losses at 3% income cost is found in-sample in 20/20 seeds, and passes every gate (walk-forward, both nulls) in 15/20 (recall 0.75, stated acceptance level 0.8: NOT met); at half that size it is found in-sample in 20/20 seeds but passes every gate in only 3/20, the walk-forward on the cell choice being the limiting gate. The verdict is therefore "no robust cell found at this power".

Read this first: (1) the sleeve series are NON-VIRGIN (selected as families on the same 142 weeks the portfolio layer scores; the live pair's window is its own best period), so every sleeve-bearing number is optimistic; the search ranks sleeve cells at 50% of the sleeves' backtest edge, 100% and 0% are reported. (2) Lever B (Trade Health) uses a3a74's TICK-level TH tables (ManageLoss port on trade prints, validated 97.9% exit type and 95.9% type+time within 2 minutes against the live log, so no longer PROVISIONAL); the earlier 1-second TH tables (81-84% time match) were superseded and are not in the final library; the live chart runs ST TH OFF from 2026-10-20 (user decision) so TH-off is the base and TH is a lever. (3) Everything is relative to the TH-off NT8-faithful engine base (weekly Sharpe clean/H1/H2/all 1.46/2.83/2.48/1.90 in SMOOTH; this evaluator's live cell re-scored over the 142-week window: net $2,665k, DD52 $245k, worst week -$83k, CVaR5 -$79k, Sharpe 2.14; the small difference to the SMOOTH live cell (17 days, max $16.8k) is the ordering of simultaneous entries (two books entering in the same minute), which the stored rows resolved with an unstable pandas sort and this engine resolves ST before HM; all comparisons use this engine's live cell). (4) Combined-lock values: the base is the SMOOTH live cell (combined cap 8R, arm 2R, give-back 67% from 00:00, week floor 8R, per-book daily +5R/-2R, per-book week off, size 8 per book), which the user has confirmed equals the live chart values; a3a74's earlier reading of the file defaults (cap 5R, per-book week -6R) is NOT the chart; that cell is kept as a reference row and is reachable on the D grid. (5) Window: the 142 ISO weeks 2024-02-01..2026-10-16 (live pair 8/8: DD52 $245k, 6/6: $184k).

## 1. Engine, evaluator extension and validation

- Variable contracts: the pre-netting per-book event streams (entries after each book's own busy gate, every exit leg with its second-level resolution; identical to nt8sim.acct for the live books, and a3a74's B/C tables in the same format) are merged and re-netted by a numba FIFO lot-netting replay with quantities (opposite entry closes the oldest opposite lots up to its size, the residual opens a lot; a bracket exit closes the oldest same-side lots, the residual opens an orphan opposite lot; session flat closes all), then the SMOOTH account layer (per-book rules, combined day lock, combined week stage) runs on the lot slices, all in one compiled function. Units: R per book = $1,200 x its contracts ($9,600 at 8); combined-lock R = $1,200 x (ST+HM)/2; WT-10 (research cell, 10-min ATR14x3, 60/60) rules fixed at 5R/-2R of its own contracts and WT-10 contracts do not scale the combined lock. Fractional contracts allowed (half legs). 6/6 = 0.75x linear.
- Validation (outputs/autopilot/ddmin/validate_evaluator.json): (i) reproduction of ROWS_corrected_engine at 8/8: 13,184 rows, plain daily series max difference $7e-12 vs the stored-row evaluator; (ii) live + plain + 38 random full-axis cells vs the SMOOTH numba evaluator on tie-order-matched rows: max daily difference $0.00; (iii) single-book runs vs the engine nt8sim.acct with only that book's signals (ST-only, HM-only; 40 cells each, per-book rules): max daily difference ST $0.00, HM $0.00; (iv) variable contracts vs an independent pure-python quantity-netting engine (nt8sim.acct with FIFO quantities run on the engine itself), 30 (ST,HM) sizes incl. 16/0, 0/16, 12/4, 1/16: max daily difference $2.9e-11 (plain rows); (v) exact linearity: (6,6) vs 0.75x(8,8) max diff $8.4e-11, (16,16) vs 2x(8,8) $0.0e+00.
- Search: Latin hypercube of 30,000 cells over A (ST 0..16 x HM 0..16 x WT-10 {0,1,2,3,4,6,8}) x B/C (one a3a74 table per book drawn from the available tables; ST/HM: 54 TH-off geometry tables or 192 tick-level TH cells or the tick control; WT-10: 54 geometry tables) x D (13 SMOOTH axes) x E (up to 3 of 9 sleeves at 10/20/30% risk, total <= 60%) in a stage with B,C = live (30,000 cells) and a stage with the tables (30,000 cells); then two refinement rounds (+-1 step on A, tables, D and E around the 150 best per objective at the 90% floor and the 50 best at the other floors, plus an exhaustive E sweep of all 1780 sleeve combinations around each seed); references: live, plain, the chart cell, 27 PORTFOLIO single-sleeve cells (10/20/30%), 7,853 SMOOTH cells re-run in this engine, and the stored DAYRULES (214) / WEEKGB (42) series. Library 136,720 rows.

## 2. Planted-improvement test (power of the search)

Rule P (pre-registered in PREREG block DDMIN): in the worst 10% of a cell's own weeks it removes a fraction f of the loss and in every other positive week it shaves 3% (known income cost). Full-size test f = 50% (levels off/25%/50%), half-size test f = 25% (levels off/12.5%/25%); each seed = a fresh 3,000-cell LHS over A x D x P on the live B,C, two refinement rounds (+-1 step incl. the P level), then the same walk-forward on the cell choice (composite objective, 90% floor, WF-A), matched random-halt null (200 reps) and a best-of-N null (40 pair-side worlds, N = 13,000).

| test | seeds | in-sample composite best carries P | carries the top level | passes WF gain > 0 + matched null >= 0.95 + best-of-N >= 0.95 (any P level) | passes with the top level | WF gain > 0 | median DD52 of the best cell | median DD52 of the best cell without P | live DD52 |
|---|---|---|---|---|---|---|---|---|---|
| full (f = 50%) | 20 | 20/20 (1.00) | 20/20 | 15/20 (recall 0.75) | 15/20 | 15/20 | $63k | $134k | $245k |
| half (f = 25%) | 20 | 20/20 (1.00) | 20/20 | 3/20 (recall 0.15) | 3/20 | 3/20 | $93k | $126k | $245k |

Walk-forward diagnostics: share of folds whose chosen cell carries the planted rule: full 1.00, half 0.90. In-sample the search finds the planted rule in 20/20 (full) and 20/20 (half) seeds and both nulls are passed in every seed; the walk-forward gate (cell choice made on 52 trailing weeks) is the limiting gate.

Stated acceptance level: recall >= 0.8 at f = 50%. Result: recall 0.75 (NOT MET). Search power is the finding; the verdict language below is 'no robust cell found at this power'.

## 3. Per objective and income floor: in-sample best vs walk-forward, side by side

Floors are shares of live net over the same weeks (live = this engine's 8/8 live cell, no sleeves). In-sample = best cell of the whole library on the 142 weeks (sleeves at 50% edge). Walk-forward = the PROCEDURE (best cell per objective and floor on the trailing 52 weeks, applied to the next 13, rolled): WF-A = library cells without sleeves (142 OOS weeks 2024-02..2026-10, 11 folds, first fold has 51 trailing weeks), WF-B = all cells incl. sleeves (90 OOS weeks 2025-02..2026-10, 7 folds; sleeve series start 2024-02). OOS values are on the stitched weekly path against live over the same weeks; the in-sample cell is also shown on those same OOS weeks. "WF gain" = parity-scaled objective (objective at live income by linear size scaling) of the procedure minus live over the same OOS weeks; > 0 = better than live.

### Objective: DD52 (52-week max drawdown, weekly path)

| floor | IN-SAMPLE best cell | net (% live) | DD52 | P(DD>200k) | CVaR5 | worst wk | longest DD | Sharpe | WF-A OOS value / net % of live OOS / OOS Sharpe / OOS CVaR5 (live value) | WF-A gain | WF-B OOS value / net % / Sharpe / CVaR5 (live value) | WF-B gain | in-sample cell on the WF-B weeks: value / net % |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 100% | c 2/9/4 ; tabs TH-tick(m25,r2,w30,mo6,pb4,e0.35)/g75/t2/part/g45/t0.75 ; tgt 8/3R flr 3/2R cap off arm 1.5R gb80% start 0930 dayflr 4 wkflr off pbwk 6 wkGB off maxtr 10 ; E K4h 10%, BM13 20%, BTC 10% | 106% | $77k | 0.5% | -$60k | -$76k | 9 | 3.07 | $270k / 39% / 1.30 / -$66k (live $245k) | - | $243k / 39% / 1.54 / -$66k (live $245k) | - | $76k / 97% |
| 90% | c 3/5/4 ; tabs live/g60/t1.5/live ; tgt 5/offR flr 1.5/3R cap 12 arm 1R gb80% start 0000 dayflr 4 wkflr 10 pbwk off wkGB off maxtr off ; E K4u 20%, CL240 20%, BM13 10% | 90% | $69k | 0.1% | -$49k | -$59k | 16 | 3.27 | $214k / 53% / 1.76 / -$67k (live $245k) | - | $187k / 26% / 1.05 / -$67k (live $245k) | - | $69k / 84% |
| 80% | c 3/5/4 ; tabs live/g60/t1.5/live ; tgt 5/offR flr 1.5/3R cap 12 arm 1R gb80% start 0000 dayflr 4 wkflr 10 pbwk off wkGB off maxtr off ; E K4h 20%, CL240 10% | 82% | $67k | 0.2% | -$48k | -$57k | 9 | 3.00 | $176k / 42% / 1.50 / -$67k (live $245k) | - | $187k / 28% / 1.16 / -$66k (live $245k) | - | $67k / 77% |
| 70% | c 3/5/4 ; tabs live/g60/t1.5/live ; tgt 5/offR flr 1.5/3R cap 12 arm 1R gb80% start 0000 dayflr 4 wkflr 10 pbwk off wkGB off maxtr off ; E K4h 20%, CL240 10% | 82% | $67k | 0.2% | -$48k | -$57k | 9 | 3.00 | $254k / 33% / 1.31 / -$62k (live $245k) | - | $187k / 22% / 0.93 / -$66k (live $245k) | - | $67k / 77% |

### Objective: P(DD > $200k) (52-week block bootstrap, 20,000 draws, CRN)

| floor | IN-SAMPLE best cell | net (% live) | DD52 | P(DD>200k) | CVaR5 | worst wk | longest DD | Sharpe | WF-A OOS value / net % of live OOS / OOS Sharpe / OOS CVaR5 (live value) | WF-A gain | WF-B OOS value / net % / Sharpe / CVaR5 (live value) | WF-B gain | in-sample cell on the WF-B weeks: value / net % |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 100% | c 2/9/8 ; tabs g45/t1/live/live ; tgt 5/offR flr off/3R cap 10 arm 1R gb67% start 0000 dayflr 4 wkflr off pbwk 6 wkGB 5R/keep50% maxtr off ; E K4u 20%, CL240 10%, BM13 30% | 101% | $91k | 0.2% | -$50k | -$77k | 9 | 3.39 | $469k / 33% / 0.87 / -$78k (live $245k) | - | $239k / 102% / 2.53 / -$79k (live $245k) | + | $91k / 98% |
| 90% | c 2/9/4 ; tabs TH-tick(m25,r2,w30,mo6,pb4,e0.35)/g75/t2/part/g45/t0.75 ; tgt 8/3R flr 3/3R cap off arm 1.5R gb80% start 0930 dayflr 4 wkflr off pbwk 6 wkGB 5R/keep50% maxtr 10 ; E K4u 10%, BM13 20%, BTC 30% | 94% | $75k | 0.0% | -$60k | -$73k | 11 | 3.38 | $469k / 42% / 1.05 / -$78k (live $245k) | - | $239k / 102% / 2.53 / -$79k (live $245k) | + | $73k / 79% |
| 80% | c 2/9/4 ; tabs TH-tick(m25,r2,w30,mo6,pb4,e0.35)/g75/t2/part/g45/t0.75 ; tgt 8/3R flr 3/3R cap off arm 1.5R gb80% start 0930 dayflr 4 wkflr off pbwk 6 wkGB 5R/keep50% maxtr 10 ; E K4u 10%, BM13 20%, BTC 30% | 94% | $75k | 0.0% | -$60k | -$73k | 11 | 3.38 | $469k / 40% / 1.05 / -$78k (live $245k) | - | $239k / 102% / 2.53 / -$79k (live $245k) | + | $73k / 79% |
| 70% | c 2/9/4 ; tabs TH-tick(m25,r2,w30,mo6,pb4,e0.35)/g75/t2/part/g45/t0.75 ; tgt 8/3R flr 3/3R cap off arm 1.5R gb80% start 0930 dayflr 4 wkflr off pbwk 6 wkGB 5R/keep50% maxtr 10 ; E K4u 10%, BM13 20%, BTC 30% | 94% | $75k | 0.0% | -$60k | -$73k | 11 | 3.38 | $469k / 40% / 1.05 / -$78k (live $245k) | - | $239k / 102% / 2.53 / -$79k (live $245k) | + | $73k / 79% |

### Objective: CVaR5 of weekly P&L

| floor | IN-SAMPLE best cell | net (% live) | DD52 | P(DD>200k) | CVaR5 | worst wk | longest DD | Sharpe | WF-A OOS value / net % of live OOS / OOS Sharpe / OOS CVaR5 (live value) | WF-A gain | WF-B OOS value / net % / Sharpe / CVaR5 (live value) | WF-B gain | in-sample cell on the WF-B weeks: value / net % |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 100% | c 0/9/8 ; tabs live ; tgt 3/offR flr 1/3R cap 12 arm offR gb67% start 0000 dayflr 4 wkflr 6 pbwk off wkGB off maxtr off ; E K4u 10%, B7 10% | 100% | $264k | 27.0% | -$39k | -$45k | 30 | 2.36 | -$62k / 47% / 1.38 / -$62k (live -$79k) | - | -$62k / 55% / 1.71 / -$62k (live -$80k) | - | -$40k / 119% |
| 90% | c 0/9/8 ; tabs live ; tgt 3/offR flr 1/3R cap off arm offR gb67% start 0000 dayflr 4 wkflr 6 pbwk off wkGB off maxtr 10 ; E none | 90% | $282k | 31.2% | -$36k | -$37k | 30 | 2.18 | -$45k / 47% / 1.36 / -$45k (live -$79k) | - | -$60k / 58% / 1.82 / -$60k (live -$80k) | - | -$36k / 111% |
| 80% | c 0/8/8 ; tabs live ; tgt 3/offR flr 1/3R cap off arm offR gb67% start 0000 dayflr 4 wkflr 6 pbwk off wkGB off maxtr off ; E none | 82% | $321k | 26.3% | -$31k | -$32k | 31 | 2.16 | -$45k / 49% / 1.41 / -$45k (live -$79k) | - | -$37k / 69% / 2.20 / -$37k (live -$80k) | + | -$31k / 101% |
| 70% | c 0/8/6 ; tabs live/g75/t1 ; tgt 3/offR flr 1/3R cap off arm offR gb67% start 0000 dayflr 4 wkflr 6 pbwk off wkGB off maxtr off ; E none | 75% | $317k | 27.0% | -$31k | -$32k | 31 | 2.04 | -$67k / 37% / 1.13 / -$67k (live -$79k) | - | -$35k / 48% / 1.67 / -$35k (live -$80k) | + | -$31k / 92% |

### Objective: worst week

| floor | IN-SAMPLE best cell | net (% live) | DD52 | P(DD>200k) | CVaR5 | worst wk | longest DD | Sharpe | WF-A OOS value / net % of live OOS / OOS Sharpe / OOS CVaR5 (live value) | WF-A gain | WF-B OOS value / net % / Sharpe / CVaR5 (live value) | WF-B gain | in-sample cell on the WF-B weeks: value / net % |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 100% | c 0/9/6 ; tabs live ; tgt 3/offR flr 1/3R cap off arm offR gb67% start 0000 dayflr off wkflr 6 pbwk off wkGB off maxtr 10 ; E K4u 10%, CL240 10%, B7 10% | 101% | $270k | 20.9% | -$40k | -$41k | 15 | 2.41 | -$95k / 49% / 1.46 / -$50k (live -$83k) | - | -$75k / 55% / 1.69 / -$62k (live -$83k) | - | -$41k / 114% |
| 90% | c 0/9/8 ; tabs live ; tgt 3/offR flr 1/3R cap 12 arm offR gb67% start 0000 dayflr 4 wkflr 6 pbwk off wkGB off maxtr off ; E none | 94% | $290k | 29.9% | -$36k | -$37k | 31 | 2.21 | -$37k / 68% / 1.87 / -$34k (live -$83k) | + | -$75k / 74% / 2.21 / -$60k (live -$83k) | - | -$37k / 114% |
| 80% | c 0/8/8 ; tabs live ; tgt 3/offR flr 1/3R cap off arm offR gb67% start 0000 dayflr 4 wkflr 6 pbwk off wkGB off maxtr off ; E none | 82% | $321k | 26.3% | -$31k | -$32k | 31 | 2.16 | -$37k / 62% / 1.72 / -$34k (live -$83k) | + | -$46k / 81% / 2.55 / -$37k (live -$83k) | + | -$32k / 101% |
| 70% | c 0/8/8 ; tabs live ; tgt 3/offR flr 1/3R cap off arm offR gb67% start 0000 dayflr 4 wkflr 6 pbwk off wkGB off maxtr off ; E none | 82% | $321k | 26.3% | -$31k | -$32k | 31 | 2.16 | -$162k / 45% / 1.30 / -$54k (live -$83k) | - | -$46k / 58% / 2.01 / -$35k (live -$83k) | + | -$32k / 101% |

### Objective: longest drawdown (weeks)

| floor | IN-SAMPLE best cell | net (% live) | DD52 | P(DD>200k) | CVaR5 | worst wk | longest DD | Sharpe | WF-A OOS value / net % of live OOS / OOS Sharpe / OOS CVaR5 (live value) | WF-A gain | WF-B OOS value / net % / Sharpe / CVaR5 (live value) | WF-B gain | in-sample cell on the WF-B weeks: value / net % |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 100% | c 3/10/8 ; tabs live/live/g60/t0.75 ; tgt off/4R flr 1.5/3R cap 10 arm 1R gb80% start 0000 dayflr 4 wkflr off pbwk off wkGB off maxtr 6 ; E K4u 10%, BM13 20%, BTC 30% | 144% | $124k | 5.2% | -$66k | -$94k | 5 | 3.64 | 35 / 58% / 1.21 / -$95k (live 8) | - | 15 / 70% / 1.79 / -$76k (live 8) | - | 5 / 125% |
| 90% | c 3/10/8 ; tabs live/live/g60/t0.75 ; tgt off/4R flr 1.5/3R cap 10 arm 1R gb80% start 0000 dayflr 4 wkflr off pbwk off wkGB off maxtr 6 ; E K4u 10%, BM13 20%, BTC 30% | 144% | $124k | 5.2% | -$66k | -$94k | 5 | 3.64 | 35 / 75% / 1.58 / -$91k (live 8) | - | 15 / 70% / 1.79 / -$76k (live 8) | - | 5 / 125% |
| 80% | c 3/10/8 ; tabs live/live/g60/t0.75 ; tgt off/4R flr 1.5/3R cap 10 arm 1R gb80% start 0000 dayflr 4 wkflr off pbwk off wkGB off maxtr 6 ; E K4u 10%, BM13 20%, BTC 30% | 144% | $124k | 5.2% | -$66k | -$94k | 5 | 3.64 | 44 / 51% / 1.21 / -$86k (live 8) | - | 15 / 70% / 1.79 / -$76k (live 8) | - | 5 / 125% |
| 70% | c 3/10/8 ; tabs live/live/g60/t0.75 ; tgt off/4R flr 1.5/3R cap 10 arm 1R gb80% start 0000 dayflr 4 wkflr off pbwk off wkGB off maxtr 6 ; E K4u 10%, BM13 20%, BTC 30% | 144% | $124k | 5.2% | -$66k | -$94k | 5 | 3.64 | 44 / 51% / 1.21 / -$86k (live 8) | - | 15 / 70% / 1.79 / -$76k (live 8) | - | 5 / 125% |

Distinct cells chosen by the walk-forward procedure at the composite (DD52, 90%): WF-A 10 of 11 folds, WF-B 7 of 7 folds.

### 3b. Gate table for the best cell of every (objective, floor)

A cell is robust on its objective when: WF gain > 0 (procedure level, WF-A for sleeve-free cells else WF-B), matched null >= 0.95 on that objective, best-of-N null >= 0.95 (20 worlds), plateau >= 60%, strict span signs.

| objective | floor | cell | WF gain ($ at parity; tag) | OOS net % of live | matched null | best-of-N | plateau | span signs | ROBUST |
|---|---|---|---|---|---|---|---|---|---|
| dd52 | 100% | c 2/9/4 ; tabs TH-tick(m25,r2,w30,mo6,pb4,e0.35)/g75/t2/part/g45/t0.75 ; tgt 8/3R flr 3/2R cap off arm 1.5R gb80% start 0930 dayflr 4 wkflr off pbwk 6 wkGB off maxtr 10 ; E K4h 10%, BM13 20%, BTC 10% | -372,409 (B) | 39% | 1.00 | 0.70 | 0.77 | +++ | no |
| dd52 | 90% | c 3/5/4 ; tabs live/g60/t1.5/live ; tgt 5/offR flr 1.5/3R cap 12 arm 1R gb80% start 0000 dayflr 4 wkflr 10 pbwk off wkGB off maxtr off ; E K4u 20%, CL240 20%, BM13 10% | -473,310 (B) | 26% | 1.00 | 0.55 | 0.77 | +++ | no |
| dd52 | 80% | c 3/5/4 ; tabs live/g60/t1.5/live ; tgt 5/offR flr 1.5/3R cap 12 arm 1R gb80% start 0000 dayflr 4 wkflr 10 pbwk off wkGB off maxtr off ; E K4h 20%, CL240 10% | -424,977 (B) | 28% | 1.00 | 0.35 | 0.75 | +++ | no |
| dd52 | 70% | c 3/5/4 ; tabs live/g60/t1.5/live ; tgt 5/offR flr 1.5/3R cap 12 arm 1R gb80% start 0000 dayflr 4 wkflr 10 pbwk off wkGB off maxtr off ; E K4h 20%, CL240 10% | -603,937 (B) | 22% | 1.00 | 0.25 | 0.75 | +++ | no |
| p200 | 100% | c 2/9/8 ; tabs g45/t1/live/live ; tgt 5/offR flr off/3R cap 10 arm 1R gb67% start 0000 dayflr 4 wkflr off pbwk 6 wkGB 5R/keep50% maxtr off ; E K4u 20%, CL240 10%, BM13 30% | 10,347 (B) | 102% | 1.00 | 0.45 | 0.93 | +++ | no |
| p200 | 90% | c 2/9/4 ; tabs TH-tick(m25,r2,w30,mo6,pb4,e0.35)/g75/t2/part/g45/t0.75 ; tgt 8/3R flr 3/3R cap off arm 1.5R gb80% start 0930 dayflr 4 wkflr off pbwk 6 wkGB 5R/keep50% maxtr 10 ; E K4u 10%, BM13 20%, BTC 30% | 10,347 (B) | 102% | 1.00 | 0.55 | 1.00 | +++ | no |
| p200 | 80% | c 2/9/4 ; tabs TH-tick(m25,r2,w30,mo6,pb4,e0.35)/g75/t2/part/g45/t0.75 ; tgt 8/3R flr 3/3R cap off arm 1.5R gb80% start 0930 dayflr 4 wkflr off pbwk 6 wkGB 5R/keep50% maxtr 10 ; E K4u 10%, BM13 20%, BTC 30% | 10,347 (B) | 102% | 1.00 | 0.25 | 1.00 | +++ | no |
| p200 | 70% | c 2/9/4 ; tabs TH-tick(m25,r2,w30,mo6,pb4,e0.35)/g75/t2/part/g45/t0.75 ; tgt 8/3R flr 3/3R cap off arm 1.5R gb80% start 0930 dayflr 4 wkflr off pbwk 6 wkGB 5R/keep50% maxtr 10 ; E K4u 10%, BM13 20%, BTC 30% | 10,347 (B) | 102% | 1.00 | 0.15 | 1.00 | +++ | no |
| cvar5 | 100% | c 0/9/8 ; tabs live ; tgt 3/offR flr 1/3R cap 12 arm offR gb67% start 0000 dayflr 4 wkflr 6 pbwk off wkGB off maxtr off ; E K4u 10%, B7 10% | -30,989 (B) | 55% | 1.00 | 1.00 | 0.90 | +++ | no |
| cvar5 | 90% | c 0/9/8 ; tabs live ; tgt 3/offR flr 1/3R cap off arm offR gb67% start 0000 dayflr 4 wkflr 6 pbwk off wkGB off maxtr 10 ; E none | -16,944 (A) | 47% | 1.00 | 1.00 | 0.93 | +++ | no |
| cvar5 | 80% | c 0/8/8 ; tabs live ; tgt 3/offR flr 1/3R cap off arm offR gb67% start 0000 dayflr 4 wkflr 6 pbwk off wkGB off maxtr off ; E none | -11,871 (A) | 49% | 1.00 | 1.00 | 0.89 | +++ | no |
| cvar5 | 70% | c 0/8/6 ; tabs live/g75/t1 ; tgt 3/offR flr 1/3R cap off arm offR gb67% start 0000 dayflr 4 wkflr 6 pbwk off wkGB off maxtr off ; E none | -102,338 (A) | 37% | 1.00 | 1.00 | 0.82 | +++ | no |
| worst | 100% | c 0/9/6 ; tabs live ; tgt 3/offR flr 1/3R cap off arm offR gb67% start 0000 dayflr off wkflr 6 pbwk off wkGB off maxtr 10 ; E K4u 10%, CL240 10%, B7 10% | -53,600 (B) | 55% | 1.00 | 1.00 | 0.76 | +++ | no |
| worst | 90% | c 0/9/8 ; tabs live ; tgt 3/offR flr 1/3R cap 12 arm offR gb67% start 0000 dayflr 4 wkflr 6 pbwk off wkGB off maxtr off ; E none | 28,439 (A) | 68% | 1.00 | 1.00 | 0.82 | +++ | YES |
| worst | 80% | c 0/8/8 ; tabs live ; tgt 3/offR flr 1/3R cap off arm offR gb67% start 0000 dayflr 4 wkflr 6 pbwk off wkGB off maxtr off ; E none | 23,511 (A) | 62% | 1.00 | 1.00 | 0.70 | +++ | YES |
| worst | 70% | c 0/8/8 ; tabs live ; tgt 3/offR flr 1/3R cap off arm offR gb67% start 0000 dayflr 4 wkflr 6 pbwk off wkGB off maxtr off ; E none | -277,686 (A) | 45% | 1.00 | 1.00 | 0.70 | +++ | no |
| longdd | 100% | c 3/10/8 ; tabs live/live/g60/t0.75 ; tgt off/4R flr 1.5/3R cap 10 arm 1R gb80% start 0000 dayflr 4 wkflr off pbwk off wkGB off maxtr 6 ; E K4u 10%, BM13 20%, BTC 30% | -7 (B) | 70% | 1.00 | 0.00 | 0.92 | ++- | no |
| longdd | 90% | c 3/10/8 ; tabs live/live/g60/t0.75 ; tgt off/4R flr 1.5/3R cap 10 arm 1R gb80% start 0000 dayflr 4 wkflr off pbwk off wkGB off maxtr 6 ; E K4u 10%, BM13 20%, BTC 30% | -7 (B) | 70% | 1.00 | 0.00 | 0.92 | ++- | no |
| longdd | 80% | c 3/10/8 ; tabs live/live/g60/t0.75 ; tgt off/4R flr 1.5/3R cap 10 arm 1R gb80% start 0000 dayflr 4 wkflr off pbwk off wkGB off maxtr 6 ; E K4u 10%, BM13 20%, BTC 30% | -7 (B) | 70% | 1.00 | 0.00 | 0.92 | ++- | no |
| longdd | 70% | c 3/10/8 ; tabs live/live/g60/t0.75 ; tgt off/4R flr 1.5/3R cap 10 arm 1R gb80% start 0000 dayflr 4 wkflr off pbwk off wkGB off maxtr 6 ; E K4u 10%, BM13 20%, BTC 30% | -7 (B) | 70% | 1.00 | 0.00 | 0.92 | ++- | no |

### 3c. Tail-risk (worst-week / CVaR5) cells: what they buy and what they cost

The tail objectives are not the headline (composite = DD52) but several cells pass the pre-registered gates on them. This table shows their full footprint beside the live cell: tail insurance (week floor 6R, day loss floor 3-4R, tight targets) cuts the worst week and CVaR5 but does not reduce DD52 and lengthens the longest drawdown, and the strongest cells remove ST and run the research WT-10 book (replication-failed LEAD) at 8 contracts.

| cell | objective @ floor | net | DD52 | P(DD>200k) | CVaR5 | worst | longest DD | Sharpe | matched null | best-of-N | plateau | span signs | WF gain (tag) | robust |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LIVE | - | 100% | $245k | 42.5% | -$79k | -$83k | 8 | 2.14 | | | | | | |
| c 0/9/8 ; tabs live ; tgt 3/offR flr 1/3R cap 12 arm offR gb67% start 0000 dayflr 4 wkflr 6 pbwk off wkGB off maxtr off ; E K4u 10%, B7 10% | cvar5@100% | 100% | $264k | 27.0% | -$39k | -$45k | 30 | 2.36 | 1.00 | 1.00 | 0.90 | +++ | - (B) | no |
| c 0/9/8 ; tabs live ; tgt 3/offR flr 1/3R cap off arm offR gb67% start 0000 dayflr 4 wkflr 6 pbwk off wkGB off maxtr 10 ; E none | cvar5@90% | 90% | $282k | 31.2% | -$36k | -$37k | 30 | 2.18 | 1.00 | 1.00 | 0.93 | +++ | - (A) | no |
| c 8/8/0 ; tabs live ; tgt off/5R flr 1/1R cap 12 arm 1R gb67% start 0000 dayflr 2 wkflr 6 pbwk off wkGB 6R/keep67% maxtr 10 ; E none | cvar5@90% | 90% | $212k | 20.0% | -$58k | -$58k | 17 | 2.43 | 1.00 | 0.00 | 0.65 | +++ | - (A) | no |
| c 0/8/8 ; tabs live ; tgt 3/offR flr 1/3R cap off arm offR gb67% start 0000 dayflr 4 wkflr 6 pbwk off wkGB off maxtr off ; E none | cvar5@80% | 82% | $321k | 26.3% | -$31k | -$32k | 31 | 2.16 | 1.00 | 1.00 | 0.89 | +++ | - (A) | no |
| c 0/8/6 ; tabs live/g75/t1 ; tgt 3/offR flr 1/3R cap off arm offR gb67% start 0000 dayflr 4 wkflr 6 pbwk off wkGB off maxtr off ; E none | cvar5@70% | 75% | $317k | 27.0% | -$31k | -$32k | 31 | 2.04 | 1.00 | 1.00 | 0.82 | +++ | - (A) | no |
| c 0/9/6 ; tabs live ; tgt 3/offR flr 1/3R cap off arm offR gb67% start 0000 dayflr off wkflr 6 pbwk off wkGB off maxtr 10 ; E K4u 10%, CL240 10%, B7 10% | worst@100% | 101% | $270k | 20.9% | -$40k | -$41k | 15 | 2.41 | 1.00 | 1.00 | 0.76 | +++ | - (B) | no |
| c 0/9/8 ; tabs live ; tgt 3/offR flr 1/3R cap 12 arm offR gb67% start 0000 dayflr 4 wkflr 6 pbwk off wkGB off maxtr off ; E none | worst@90% | 94% | $290k | 29.9% | -$36k | -$37k | 31 | 2.21 | 1.00 | 1.00 | 0.82 | +++ | + (A) | YES |
| c 8/8/0 ; tabs live ; tgt off/5R flr 1/1R cap 12 arm 1R gb67% start 0000 dayflr 2 wkflr 6 pbwk off wkGB 6R/keep67% maxtr 10 ; E none | worst@90% | 90% | $212k | 20.0% | -$58k | -$58k | 17 | 2.43 | 1.00 | 0.00 | 0.55 | +++ | + (A) | no |
| c 0/8/8 ; tabs live ; tgt 3/offR flr 1/3R cap off arm offR gb67% start 0000 dayflr 4 wkflr 6 pbwk off wkGB off maxtr off ; E none | worst@80% | 82% | $321k | 26.3% | -$31k | -$32k | 31 | 2.16 | 1.00 | 1.00 | 0.70 | +++ | + (A) | YES |
| c 0/8/8 ; tabs live ; tgt 3/offR flr 1/3R cap off arm offR gb67% start 0000 dayflr 4 wkflr 6 pbwk off wkGB off maxtr off ; E none | worst@70% | 82% | $321k | 26.3% | -$31k | -$32k | 31 | 2.16 | 1.00 | 1.00 | 0.70 | +++ | - (A) | no |

## 4. Top 20 cells on the composite (lowest DD52 at >= 90% of live net), in-sample, every lever and all validity columns

Null ranks: matched = share of 200 replicates (PLAIN D at the cell's A,B,C with random halts at the cell's firing rates, sleeves circularly shifted) with a worse parity-scaled DD52; best-of-N = share of search-replicating null worlds whose best DD52 at >= 90% income is worse than the cell's (20 worlds). Plateau = share of +-1-step neighbours (A, tables, D, E) keeping >= 75% of the cell's DD gain at income parity. Span signs = DD gain at parity vs live in clean / H1 / H2 weeks of the window. Edge columns: DD52 / net % at sleeve edge 100% | 50% | 0%.

| # | cell (contracts ST/HM/WT | tables | D | sleeves) | net | DD52 | P(DD>200k) | CVaR5 | worst | longest DD | Sharpe | edge 100% DD/net | edge 0% DD/net | matched null | best-of-N | plateau | span signs | WF gain (WF tag) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | c 3/5/4 ; tabs live/g60/t1.5/live ; tgt 5/offR flr 1.5/3R cap 12 arm 1R gb80% start 0000 dayflr 4 wkflr 10 pbwk off wkGB off maxtr off ; E K4u 20%, CL240 20%, BM13 10% | 90% | $69k | 0.1% | -$49k | -$59k | 16 | 3.27 | $57k / 107% | $94k / 73% | 1.00 | 0.55 | 0.77 | +++ | - (B) |
| 2 | c 3/5/4 ; tabs live/g60/t1.5/live ; tgt 5/offR flr 1.5/3R cap 12 arm 1R gb80% start 0000 dayflr 4 wkflr 10 pbwk off wkGB off maxtr off ; E K4u 20%, CL240 20%, BM13 20% | 93% | $71k | 0.1% | -$49k | -$62k | 16 | 3.30 | $59k / 114% | $112k / 73% | 1.00 | 0.50 | 0.82 | +++ | - (B) |
| 3 | c 3/5/4 ; tabs live/g60/t1.5/live ; tgt 5/offR flr 1.5/3R cap 12 arm 1R gb80% start 0000 dayflr 4 wkflr 10 pbwk off wkGB off maxtr off ; E K4h 30%, CL240 20%, BM13 10% | 92% | $72k | 0.1% | -$51k | -$61k | 8 | 3.16 | $62k / 111% | $92k / 73% | 1.00 | 0.45 | 0.89 | +++ | - (B) |
| 4 | c 3/5/4 ; tabs live/g60/t1.5/live ; tgt 5/offR flr 1.5/3R cap 12 arm 1R gb80% start 0000 dayflr 4 wkflr 10 pbwk off wkGB off maxtr off ; E K4h 20%, CL240 20%, BM13 20% | 92% | $73k | 0.1% | -$50k | -$59k | 16 | 3.21 | $62k / 110% | $95k / 73% | 1.00 | 0.45 | 0.86 | +++ | - (B) |
| 6 | c 2/9/4 ; tabs TH-tick(m25,r2,w30,mo6,pb4,e0.35)/g75/t2/part/g45/t0.75 ; tgt 8/3R flr 3/3R cap off arm 1.5R gb80% start 0930 dayflr 4 wkflr off pbwk 6 wkGB 5R/keep50% maxtr 10 ; E K4u 10%, BM13 20%, BTC 30% | 94% | $75k | 0.0% | -$60k | -$73k | 11 | 3.38 | $69k / 110% | $108k / 78% | 1.00 | 0.35 | 0.79 | +++ | - (B) |
| 7 | c 2/9/4 ; tabs TH-tick(m25,r2,w30,mo6,pb4,e0.35)/g75/t2/part/g45/t0.75 ; tgt 8/3R flr 3/3R cap off arm 1.5R gb80% start 0930 dayflr 4 wkflr off pbwk 6 wkGB 5R/keep50% maxtr 10 ; E K4u 10%, BM13 20%, BTC 30% | 94% | $75k | 0.0% | -$60k | -$73k | 11 | 3.38 | $69k / 110% | $108k / 78% | 1.00 | 0.35 | 0.79 | +++ | - (B) |
| 8 | c 2/9/4 ; tabs TH-tick(m25,r2,w30,mo6,pb4,e0.35)/g75/t2/part/g45/t0.75 ; tgt 8/3R flr 3/3R cap off arm 1.5R gb80% start 0930 dayflr 4 wkflr off pbwk 6 wkGB 5R/keep50% maxtr 10 ; E K4u 10%, BM13 20%, BTC 30% | 94% | $75k | 0.0% | -$60k | -$73k | 11 | 3.38 | $69k / 110% | $108k / 78% | 1.00 | 0.35 | 0.79 | +++ | - (B) |
| 9 | c 2/9/4 ; tabs TH-tick(m25,r2,w30,mo6,pb4,e0.35)/g75/t2/part/g45/t0.75 ; tgt 8/3R flr 3/3R cap off arm 1.5R gb80% start 0930 dayflr 4 wkflr off pbwk 6 wkGB 5R/keep50% maxtr 10 ; E K4u 10%, BM13 10%, BTC 30% | 91% | $75k | 0.0% | -$63k | -$72k | 9 | 3.29 | $69k / 104% | $91k / 78% | 1.00 | 0.35 | 0.77 | +++ | - (B) |
| 10 | c 2/9/4 ; tabs TH-tick(m25,r2,w30,mo6,pb4,e0.35)/g75/t2/part/g45/t0.75 ; tgt 8/3R flr 3/3R cap off arm 1.5R gb80% start 0930 dayflr 4 wkflr off pbwk 6 wkGB 5R/keep50% maxtr 10 ; E K4u 10%, BM13 10%, BTC 30% | 91% | $75k | 0.0% | -$63k | -$72k | 9 | 3.29 | $69k / 104% | $91k / 78% | 1.00 | 0.35 | 0.77 | +++ | - (B) |
| 11 | c 2/9/4 ; tabs TH-tick(m25,r2,w30,mo6,pb4,e0.35)/g75/t2/part/g45/t0.75 ; tgt 8/3R flr 3/3R cap off arm 1.5R gb80% start 0930 dayflr 4 wkflr off pbwk 6 wkGB 5R/keep50% maxtr 10 ; E K4u 10%, BM13 10%, BTC 30% | 91% | $75k | 0.0% | -$63k | -$72k | 9 | 3.29 | $69k / 104% | $91k / 78% | 1.00 | 0.35 | 0.77 | +++ | - (B) |
| 12 | c 2/9/4 ; tabs TH-tick(m25,r2,w30,mo6,pb4,e0.35)/g75/t2/part/g45/t0.75 ; tgt 8/3R flr 3/3R cap off arm 1.5R gb80% start 0930 dayflr 4 wkflr off pbwk 6 wkGB 5R/keep50% maxtr 10 ; E K4u 10%, BM13 10%, BTC 30% | 91% | $75k | 0.0% | -$63k | -$72k | 9 | 3.29 | $69k / 104% | $91k / 78% | 1.00 | 0.35 | 0.77 | +++ | - (B) |
| 13 | c 2/9/4 ; tabs TH-tick(m25,r2,w30,mo6,pb4,e0.35)/g75/t2/part/g45/t0.75 ; tgt 8/3R flr 3/3R cap off arm 1.5R gb80% start 0930 dayflr 4 wkflr off pbwk 6 wkGB 5R/keep50% maxtr 10 ; E K4h 10%, BM13 10%, BTC 30% | 90% | $75k | 0.0% | -$63k | -$71k | 13 | 3.24 | $69k / 103% | $94k / 78% | 1.00 | 0.35 | 0.74 | +++ | - (B) |
| 14 | c 2/9/4 ; tabs TH-tick(m25,r2,w30,mo6,pb4,e0.35)/g75/t2/part/g45/t0.75 ; tgt 8/3R flr 3/3R cap off arm 1.5R gb80% start 0930 dayflr 4 wkflr off pbwk 6 wkGB 5R/keep50% maxtr 10 ; E K4h 10%, BM13 10%, BTC 30% | 90% | $75k | 0.0% | -$63k | -$71k | 13 | 3.24 | $69k / 103% | $94k / 78% | 1.00 | 0.35 | 0.74 | +++ | - (B) |
| 15 | c 2/9/4 ; tabs TH-tick(m25,r2,w30,mo6,pb4,e0.35)/g75/t2/part/g45/t0.75 ; tgt 8/3R flr 3/3R cap off arm 1.5R gb80% start 0930 dayflr 4 wkflr off pbwk 6 wkGB 5R/keep50% maxtr 10 ; E K4h 10%, BM13 10%, BTC 30% | 90% | $75k | 0.0% | -$63k | -$71k | 13 | 3.24 | $69k / 103% | $94k / 78% | 1.00 | 0.35 | 0.74 | +++ | - (B) |
| 16 | c 2/9/4 ; tabs TH-tick(m25,r2,w30,mo6,pb4,e0.35)/g75/t2/part/g45/t0.75 ; tgt 8/3R flr 3/3R cap off arm 1.5R gb80% start 0930 dayflr 4 wkflr off pbwk 6 wkGB 5R/keep50% maxtr 10 ; E K4h 10%, BM13 10%, BTC 30% | 90% | $75k | 0.0% | -$63k | -$71k | 13 | 3.24 | $69k / 103% | $94k / 78% | 1.00 | 0.35 | 0.74 | +++ | - (B) |
| 17 | c 3/5/4 ; tabs live/g60/t1.5/live ; tgt 5/offR flr 1.5/3R cap 12 arm 1R gb80% start 0000 dayflr 4 wkflr 10 pbwk off wkGB off maxtr off ; E K4h 20%, CL240 30%, BM13 10% | 92% | $75k | 0.2% | -$53k | -$65k | 11 | 3.22 | $65k / 111% | $101k / 73% | 1.00 | 0.35 | 0.89 | +++ | - (B) |
| 18 | c 2/9/4 ; tabs TH-tick(m25,r2,w30,mo6,pb4,e0.35)/g75/t2/part/g45/t0.75 ; tgt 8/3R flr 3/3R cap off arm 1.5R gb80% start 0930 dayflr 4 wkflr off pbwk 6 wkGB 5R/keep50% maxtr 10 ; E C11DIP 20%, BM13 10%, BTC 30% | 92% | $76k | 0.1% | -$63k | -$75k | 9 | 3.33 | $72k / 106% | $94k / 78% | 1.00 | 0.35 | 0.76 | +++ | - (B) |
| 19 | c 2/9/4 ; tabs TH-tick(m25,r2,w30,mo6,pb4,e0.35)/g75/t2/part/g45/t0.75 ; tgt 8/3R flr 3/3R cap off arm 1.5R gb80% start 0930 dayflr 4 wkflr off pbwk 6 wkGB 5R/keep50% maxtr 10 ; E C11DIP 20%, BM13 10%, BTC 30% | 92% | $76k | 0.1% | -$63k | -$75k | 9 | 3.33 | $72k / 106% | $94k / 78% | 1.00 | 0.35 | 0.76 | +++ | - (B) |
| 20 | c 2/9/4 ; tabs TH-tick(m25,r2,w30,mo6,pb4,e0.35)/g75/t2/part/g45/t0.75 ; tgt 8/3R flr 3/3R cap off arm 1.5R gb80% start 0930 dayflr 4 wkflr off pbwk 6 wkGB 5R/keep50% maxtr 10 ; E C11DIP 20%, BM13 10%, BTC 30% | 92% | $76k | 0.1% | -$63k | -$75k | 9 | 3.33 | $72k / 106% | $94k / 78% | 1.00 | 0.35 | 0.76 | +++ | - (B) |

### 4b. Best composite cell by lever family (DD52 at >= 90% of live net)

| family | cell | net | DD52 | P(DD>200k) | CVaR5 | worst | longest DD | Sharpe | matched null | best-of-N | plateau | span signs | WF gain (tag) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| all levers | c 3/5/4 ; tabs live/g60/t1.5/live ; tgt 5/offR flr 1.5/3R cap 12 arm 1R gb80% start 0000 dayflr 4 wkflr 10 pbwk off wkGB off maxtr off ; E K4u 20%, CL240 20%, BM13 10% | 90% | $69k | 0.1% | -$49k | -$59k | 16 | 3.27 | 1.00 | 0.55 | 0.77 | +++ | - (B) |
| pair-side levers only (A, B, C, D; no sleeves) | c 2/10/8 ; tabs g60/t0.75/live/live ; tgt 5/offR flr off/3R cap 10 arm 1R gb80% start 0000 dayflr 4 wkflr off pbwk 6 wkGB 5R/keep50% maxtr off ; E none | 98% | $104k | 2.8% | -$60k | -$86k | 10 | 2.88 | 1.00 | 0.75 | 0.84 | +++ | - (A) |
| with sleeves | c 3/5/4 ; tabs live/g60/t1.5/live ; tgt 5/offR flr 1.5/3R cap 12 arm 1R gb80% start 0000 dayflr 4 wkflr 10 pbwk off wkGB off maxtr off ; E K4u 20%, CL240 20%, BM13 10% | 90% | $69k | 0.1% | -$49k | -$59k | 16 | 3.27 | 1.00 | 0.55 | 0.77 | +++ | - (B) |
| D only (live contracts 8/8, live tables; the SMOOTH-type rule grid) | c 8/8/0 ; tabs live ; tgt 8/3R flr off/offR cap off arm 1R gb67% start 0000 dayflr 3 wkflr 6 pbwk off wkGB off maxtr off ; E none | 101% | $149k | 12.0% | -$59k | -$61k | 10 | 2.56 | 1.00 | 0.00 | 0.67 | +++ | - (A) |
| E only (live pair + sleeves) | c 8/8/0 ; tabs live ; tgt 5/5R flr 2/2R cap 8 arm 2R gb67% start 0000 dayflr off wkflr 8 pbwk off wkGB off maxtr off ; E K4h 10%, BM13 30% | 112% | $188k | 35.8% | -$89k | -$133k | 13 | 2.36 | 0.99 | 0.00 | 0.53 | +++ | - (B) |
| A only/allocation (live rules, live tables) | c 7/8/0 ; tabs live ; tgt 5/5R flr 2/2R cap 8 arm 2R gb67% start 0000 dayflr off wkflr 8 pbwk off wkGB off maxtr off ; E none | 95% | $220k | 47.1% | -$74k | -$75k | 13 | 2.15 | 1.00 | 0.00 | 0.46 | ++- | - (A) |

## 5. Reference cells (same engine, same window, sleeve edge 50% where sleeves)

| reference | net (% live) | DD52 | P(DD>200k) | CVaR5 | worst wk | longest DD | Sharpe |
|---|---|---|---|---|---|---|---|
| LIVE (SMOOTH live cell, this engine) | 100% | $245k | 42.5% | -$79k | -$83k | 8 | 2.14 |
| chart cell (combined cap 5R, per-book week -6R) | 28% | $380k | 81.7% | -$60k | -$62k | 67 | 0.72 |
| PLAIN (no daily rules, week floor 8R) | 94% | $461k | 95.1% | -$83k | -$92k | 31 | 1.40 |
| best SMOOTH-grid cell on DD52 at >= 90% (A, B, C live; no sleeves) | 101% | $149k | 12.0% | -$59k | -$61k | 10 | 2.56 |
| best stored DAYRULES / WEEKGB cell on DD52 at >= 90%: WG PBW ST T=6R | 102% | $211k | 37.0% | -$79k | -$83k | 8 | 2.24 |
| PORTFOLIO: live pair + K4h at 20% risk | 106% | $228k | 37.7% | -$82k | -$88k | 10 | 2.27 |
| PORTFOLIO: live pair + WT432 at 20% risk | 104% | $237k | 48.8% | -$88k | -$98k | 12 | 2.09 |
| PORTFOLIO: live pair + C11DIP at 20% risk | 105% | $293k | 47.6% | -$85k | -$102k | 10 | 2.22 |
| PORTFOLIO: live pair + CL240 at 20% risk | 106% | $258k | 46.2% | -$86k | -$94k | 12 | 2.23 |
| PORTFOLIO: live pair + BM13 at 20% risk | 106% | $213k | 39.2% | -$85k | -$114k | 13 | 2.25 |
| PORTFOLIO: live pair + BTC at 20% risk | 104% | $256k | 39.9% | -$82k | -$89k | 12 | 2.20 |

## 5b. Lever B alone: Trade Health on the live pair (tick-level port; live contracts 8/8, live rules, live geometry)

Lever B uses a3a74's TICK-level tables (ManageLoss port on NQ trade prints as a state-consistent per-book re-run; validated against the live log: exit type 97.9%, type + exit time within 2 minutes 95.9%, status OK_TICK, no longer PROVISIONAL); the earlier 1-second TH tables are superseded and not used. Each book has 192 TH-on cells (MinPoints {10,15,20,25}, Required {2,3}, window {30,60} s, momentum {4,6,8} pts, pullback {4,6} pts, efficiency {0.35,0.5}) at live geometry plus the same-method control tk_off (which differs from the stored live stream by about $64k net over 2023-08..2026-10). TH-off (the stored live stream) remains the base. Tick TH exists for ST and HM only (no WT-10 TH table).

| row | net (% live) | DD52 | P(DD>200k) | CVaR5 | worst wk | longest DD | Sharpe |
|---|---|---|---|---|---|---|---|
| TH off (stored live stream) | 100% | $245k | 42.5% | -$79k | -$83k | 8 | 2.14 |
| tick control tk_off, both books | 98% | $242k | 46.9% | -$78k | -$79k | 10 | 2.10 |
| live-fit values ST 15/3 only (tick) | 91% | $518k | 68.4% | -$80k | -$88k | 41 | 1.81 |
| live-fit values HM 10/3 only (tick) | 86% | $273k | 59.9% | -$79k | -$82k | 28 | 1.85 |
| live-fit values both on (tick) | 49% | $321k | 82.0% | -$80k | -$96k | 28 | 1.13 |
| ST TH on: best in-sample DD52 at >= 90% income (best of 192 cells, NOT validated): tk_m10_r3_w30_mo6_pb4_e0.35 | 105% | $186k | 45.0% | -$80k | -$85k | 14 | 2.20 |
| ST TH on: median over 192 cells | 86% | $332k | | -$79k | -$80k | | |
| HM TH on: best in-sample DD52 at >= 90% income (best of 192 cells, NOT validated): tk_m25_r3_w30_mo8_pb4_e0.35 | 105% | $163k | 33.0% | -$79k | -$85k | 10 | 2.23 |
| HM TH on: median over 192 cells | 81% | $311k | | -$78k | -$80k | | |

a3a74's own lever-B validation (REPORT_TH_TICK.md): best-of-576 TH cells in-sample (best HM-only cell cuts DD $242k -> $177k with net +$220k) beats the random-exit null, but no cell passes the plateau gate (0-17% vs the 60% bar) and the walk-forward on the cell choice is worse than TH-off (OOS DD +46%, net -16%); the live-fit cells cost the pair about $1,084k net with both on. The joint search below includes the tick cells as table choices.

## 6. Attribution: where the drawdown reduction comes from (composite best cells)

"Alone" = that lever changed from live with everything else live; "sequential" = levers added in the order A -> B (Trade Health) -> C (geometry) -> D (rules) -> E (sleeves @ 50% edge) -> size (parity: the cell scaled linearly to live income). Income, CVaR5 and DD are shown beside every figure; DD at parity = DD52 x live net / cell net. B alone / C alone are n/a when the table with only that part changed was not drawn by the stratified sample.

**composite best (all levers): c 3/5/4 ; tabs live/g60/t1.5/live ; tgt 5/offR flr 1.5/3R cap 12 arm 1R gb80% start 0000 dayflr 4 wkflr 10 pbwk off wkGB off maxtr off ; E K4u 20%, CL240 20%, BM13 10%**

| step | net (% live) | DD52 | CVaR5 | worst | DD52 at income parity | DD change vs live (own size) |
|---|---|---|---|---|---|---|
| alone: live | 100% | $245k | -$79k | -$83k | $245k | $0k |
| alone: A alone (contracts) | 37% | $189k | -$40k | -$42k | $518k | -$56k |
| alone: B alone (Trade Health) | 100% | $245k | -$79k | -$83k | $245k | $0k |
| alone: C alone (bracket geometry) | 82% | $364k | -$81k | -$83k | $442k | $119k |
| alone: D alone (rules) | 114% | $283k | -$96k | -$99k | $247k | $38k |
| alone: E alone (sleeves) | 117% | $253k | -$87k | -$99k | $216k | $8k |
| sequential: live | 100% | $245k | -$79k | -$83k | $245k | $0k |
| sequential: +A | 37% | $189k | -$40k | -$42k | $518k | -$56k |
| sequential: +B (TH) | 37% | $189k | -$40k | -$42k | $518k | $0k |
| sequential: +C (geometry) | 38% | $211k | -$40k | -$41k | $549k | $21k |
| sequential: +D (rules) | 73% | $127k | -$48k | -$50k | $175k | -$84k |
| sequential: +E (sleeves @50% edge) | 90% | $69k | -$49k | -$59k | $77k | -$58k |
| size (linear scale to live income) | 100% | $77k | -$55k | -$66k | $77k | $8k |

**best pair-side-only cell (A, B, C, D; no sleeves): c 2/10/8 ; tabs g60/t0.75/live/live ; tgt 5/offR flr off/3R cap 10 arm 1R gb80% start 0000 dayflr 4 wkflr off pbwk 6 wkGB 5R/keep50% maxtr off ; E none**

| step | net (% live) | DD52 | CVaR5 | worst | DD52 at income parity | DD change vs live (own size) |
|---|---|---|---|---|---|---|
| alone: live | 100% | $245k | -$79k | -$83k | $245k | $0k |
| alone: A alone (contracts) | 52% | $378k | -$62k | -$69k | $728k | $133k |
| alone: B alone (Trade Health) | 100% | $245k | -$79k | -$83k | $245k | $0k |
| alone: C alone (bracket geometry) | 69% | $699k | -$79k | -$82k | $1,011k | $454k |
| alone: D alone (rules) | 95% | $289k | -$96k | -$125k | $304k | $44k |
| alone: E alone (sleeves) | 100% | $245k | -$79k | -$83k | $245k | $0k |
| sequential: live | 100% | $245k | -$79k | -$83k | $245k | $0k |
| sequential: +A | 52% | $378k | -$62k | -$69k | $728k | $133k |
| sequential: +B (TH) | 52% | $378k | -$62k | -$69k | $728k | $0k |
| sequential: +C (geometry) | 52% | $408k | -$61k | -$66k | $779k | $30k |
| sequential: +D (rules) | 98% | $104k | -$60k | -$86k | $106k | -$304k |
| sequential: +E (sleeves @50% edge) | 98% | $104k | -$60k | -$86k | $106k | $0k |
| size (linear scale to live income) | 100% | $106k | -$61k | -$87k | $106k | $2k |

## 7. Recommended cell

**None on the composite (lowest DD52 at >= 90% of live net).** No cell passes all of: walk-forward gain > 0 on the procedure at its objective and floor, matched null >= 0.95, best-of-N null >= 0.95, plateau >= 60%, strict span signs. Funnel in section 9. The live settings stay. Leading illustrative cells follow (NOT recommended; they show what the search found and why it fails), with DualStrat field values at 8/8 and 6/6 (semantics only; DualStrat.cs was not read by this report; names to confirm) and what each would have done in each of the last 12 weeks.

### composite best (all levers)

c 3/5/4 ; tabs live/g60/t1.5/live ; tgt 5/offR flr 1.5/3R cap 12 arm 1R gb80% start 0000 dayflr 4 wkflr 10 pbwk off wkGB off maxtr off ; E K4u 20%, CL240 20%, BM13 10%

| field (semantics) | 8/8-equivalent (as searched) | 6/6-equivalent (all contracts and dollars x 0.75) |
|---|---|---|
| contracts ST / HM / WT-10 | 3 / 5 / 4 | 2.25 / 3.75 / 3 |
| per-book daily profit target ST / HM | $18,000 / off | $13,500 / off |
| per-book daily loss limit ST / HM | $5,400 / $18,000 | $4,050 / $13,500 |
| combined daily profit cap | $57,600 | $43,200 |
| combined give-back lock arm / give-back % | $4,800 / 80% | $3,600 / 80% |
| give-back lock active from (ET) | 00:00 | 00:00 |
| combined daily loss floor | $19,200 | $14,400 |
| combined weekly loss floor | $48,000 | $36,000 |
| per-book weekly loss limit ST / HM | off / off | off / off |
| combined WEEK give-back arm / keep | off | off |
| max trades per book per session | off | off |
| ST trade health / geometry | TH off, stop 60 pts, target 1R (60 pts), partial none, time stop none | TH off, stop 60 pts, target 1R (60 pts), partial none, time stop none |
| HM trade health / geometry | TH off, stop 60 pts, target 1.5R (90 pts), partial none, time stop none | TH off, stop 60 pts, target 1.5R (90 pts), partial none, time stop none |
| WT-10 trade health / geometry | TH off, stop 60 pts, target 1R (60 pts), partial none, time stop none | TH off, stop 60 pts, target 1R (60 pts), partial none, time stop none |
| sleeve NQ-eq contracts (@ risk fraction of pair-6/6 SD) | K4u 2.8 (20% risk); CL240 1.4 (20% risk); BM13 1.9 (10% risk) | K4u 2.1 (20% risk); CL240 1.1 (20% risk); BM13 1.5 (10% risk) |

Last 12 ISO weeks (8/8-equivalent $; 6/6 = x0.75): sleeve column at 50% edge.

| ISO week | live | cell pair-side | cell sleeves | cell total | cell - live | cell total 6/6 | live 6/6 |
|---|---|---|---|---|---|---|---|
| 202631 | 52,186 | 19,320 | 49,376 | 68,697 | 16,511 | 51,523 | 39,139 |
| 202632 | 40,233 | -48,821 | 17,096 | -31,725 | -71,958 | -23,794 | 30,174 |
| 202633 | -10,198 | 24,192 | 9,379 | 33,572 | 43,770 | 25,179 | -7,648 |
| 202634 | 111,628 | 57,745 | -4,010 | 53,734 | -57,894 | 40,300 | 83,721 |
| 202635 | -56,064 | -12,361 | 1,845 | -10,515 | 45,549 | -7,886 | -42,048 |
| 202636 | -77,415 | -19,413 | 4,801 | -14,611 | 62,803 | -10,958 | -58,061 |
| 202637 | -36,884 | -37,743 | 2,839 | -34,903 | 1,980 | -26,177 | -27,663 |
| 202638 | 116,706 | 5,847 | 1,198 | 7,045 | -109,660 | 5,283 | 87,529 |
| 202639 | 134,077 | 43,571 | -9,708 | 33,863 | -100,214 | 25,397 | 100,558 |
| 202640 | -15,630 | 22,756 | -8,383 | 14,373 | 30,003 | 10,779 | -11,722 |
| 202641 | -54,750 | -49,862 | -4,010 | -53,873 | 876 | -40,405 | -41,062 |
| 202642 | 38,044 | 10,097 | -2,754 | 7,342 | -30,701 | 5,507 | 28,533 |
| sum | 241,932 | 15,329 | 57,669 | 72,998 | -168,933 | 54,749 | 181,449 |

### best pair-side-only cell (A, B, C, D; no sleeves)

c 2/10/8 ; tabs g60/t0.75/live/live ; tgt 5/offR flr off/3R cap 10 arm 1R gb80% start 0000 dayflr 4 wkflr off pbwk 6 wkGB 5R/keep50% maxtr off ; E none

| field (semantics) | 8/8-equivalent (as searched) | 6/6-equivalent (all contracts and dollars x 0.75) |
|---|---|---|
| contracts ST / HM / WT-10 | 2 / 10 / 8 | 1.5 / 7.5 / 6 |
| per-book daily profit target ST / HM | $12,000 / off | $9,000 / off |
| per-book daily loss limit ST / HM | off / $36,000 | off / $27,000 |
| combined daily profit cap | $72,000 | $54,000 |
| combined give-back lock arm / give-back % | $7,200 / 80% | $5,400 / 80% |
| give-back lock active from (ET) | 00:00 | 00:00 |
| combined daily loss floor | $28,800 | $21,600 |
| combined weekly loss floor | off | off |
| per-book weekly loss limit ST / HM | $14,400 / $72,000 | $10,800 / $54,000 |
| combined WEEK give-back arm / keep | $36,000 / keep 50% | $27,000 / keep 50% |
| max trades per book per session | off | off |
| ST trade health / geometry | TH off, stop 60 pts, target 0.75R (45 pts), partial none, time stop none | TH off, stop 60 pts, target 0.75R (45 pts), partial none, time stop none |
| HM trade health / geometry | TH off, stop 60 pts, target 1R (60 pts), partial none, time stop none | TH off, stop 60 pts, target 1R (60 pts), partial none, time stop none |
| WT-10 trade health / geometry | TH off, stop 60 pts, target 1R (60 pts), partial none, time stop none | TH off, stop 60 pts, target 1R (60 pts), partial none, time stop none |
| sleeve NQ-eq contracts (@ risk fraction of pair-6/6 SD) | none | none |

Last 12 ISO weeks (8/8-equivalent $; 6/6 = x0.75): sleeve column at 50% edge.

| ISO week | live | cell pair-side | cell sleeves | cell total | cell - live | cell total 6/6 | live 6/6 |
|---|---|---|---|---|---|---|---|
| 202631 | 52,186 | 38,722 | 0 | 38,722 | -13,463 | 29,041 | 39,139 |
| 202632 | 40,233 | -5,661 | 0 | -5,661 | -45,894 | -4,245 | 30,174 |
| 202633 | -10,198 | 18,839 | 0 | 18,839 | 29,037 | 14,129 | -7,648 |
| 202634 | 111,628 | 60,614 | 0 | 60,614 | -51,013 | 45,461 | 83,721 |
| 202635 | -56,064 | 24,218 | 0 | 24,218 | 80,283 | 18,164 | -42,048 |
| 202636 | -77,415 | -53,914 | 0 | -53,914 | 23,501 | -40,435 | -58,061 |
| 202637 | -36,884 | -50,072 | 0 | -50,072 | -13,188 | -37,554 | -27,663 |
| 202638 | 116,706 | 10,199 | 0 | 10,199 | -106,506 | 7,649 | 87,529 |
| 202639 | 134,077 | 48,568 | 0 | 48,568 | -85,508 | 36,426 | 100,558 |
| 202640 | -15,630 | 32,778 | 0 | 32,778 | 48,409 | 24,584 | -11,722 |
| 202641 | -54,750 | -85,526 | 0 | -85,526 | -30,776 | -64,144 | -41,062 |
| 202642 | 38,044 | 21,072 | 0 | 21,072 | -16,972 | 15,804 | 28,533 |
| sum | 241,932 | 59,839 | 0 | 59,839 | -182,093 | 44,879 | 181,449 |

### Passes the gates on worst@80% only (tail objective, NOT a DD reduction): c 0/8/8 ; tabs live ; tgt 3/offR flr 1/3R cap off arm offR gb67% start 0000 dayflr 4 wkflr 6 pbwk off wkGB off maxtr off ; E none

c 0/8/8 ; tabs live ; tgt 3/offR flr 1/3R cap off arm offR gb67% start 0000 dayflr 4 wkflr 6 pbwk off wkGB off maxtr off ; E none

| field (semantics) | 8/8-equivalent (as searched) | 6/6-equivalent (all contracts and dollars x 0.75) |
|---|---|---|
| contracts ST / HM / WT-10 | 0 / 8 / 8 | 0 / 6 / 6 |
| per-book daily profit target ST / HM | $0 / off | $0 / off |
| per-book daily loss limit ST / HM | $0 / $28,800 | $0 / $21,600 |
| combined daily profit cap | off | off |
| combined give-back lock arm / give-back % | off | off |
| give-back lock active from (ET) | 00:00 | 00:00 |
| combined daily loss floor | $19,200 | $14,400 |
| combined weekly loss floor | $28,800 | $21,600 |
| per-book weekly loss limit ST / HM | off / off | off / off |
| combined WEEK give-back arm / keep | off | off |
| max trades per book per session | off | off |
| HM trade health / geometry | TH off, stop 60 pts, target 1R (60 pts), partial none, time stop none | TH off, stop 60 pts, target 1R (60 pts), partial none, time stop none |
| WT-10 trade health / geometry | TH off, stop 60 pts, target 1R (60 pts), partial none, time stop none | TH off, stop 60 pts, target 1R (60 pts), partial none, time stop none |
| sleeve NQ-eq contracts (@ risk fraction of pair-6/6 SD) | none | none |

Last 12 ISO weeks (8/8-equivalent $; 6/6 = x0.75): sleeve column at 50% edge.

| ISO week | live | cell pair-side | cell sleeves | cell total | cell - live | cell total 6/6 | live 6/6 |
|---|---|---|---|---|---|---|---|
| 202631 | 52,186 | -30,243 | 0 | -30,243 | -82,429 | -22,682 | 39,139 |
| 202632 | 40,233 | -30,339 | 0 | -30,339 | -70,572 | -22,754 | 30,174 |
| 202633 | -10,198 | 14,973 | 0 | 14,973 | 25,171 | 11,229 | -7,648 |
| 202634 | 111,628 | 12,083 | 0 | 12,083 | -99,544 | 9,062 | 83,721 |
| 202635 | -56,064 | -31,212 | 0 | -31,212 | 24,852 | -23,409 | -42,048 |
| 202636 | -77,415 | -29,489 | 0 | -29,489 | 47,926 | -22,116 | -58,061 |
| 202637 | -36,884 | -31,729 | 0 | -31,729 | 5,155 | -23,796 | -27,663 |
| 202638 | 116,706 | -29,813 | 0 | -29,813 | -146,519 | -22,360 | 87,529 |
| 202639 | 134,077 | 70,363 | 0 | 70,363 | -63,713 | 52,772 | 100,558 |
| 202640 | -15,630 | -29,144 | 0 | -29,144 | -13,514 | -21,858 | -11,722 |
| 202641 | -54,750 | 44,578 | 0 | 44,578 | 99,328 | 33,433 | -41,062 |
| 202642 | 38,044 | 39,124 | 0 | 39,124 | 1,080 | 29,343 | 28,533 |
| sum | 241,932 | -30,847 | 0 | -30,847 | -272,780 | -23,135 | 181,449 |

### Passes the gates on worst@90% only (tail objective, NOT a DD reduction): c 0/9/8 ; tabs live ; tgt 3/offR flr 1/3R cap 12 arm offR gb67% start 0000 dayflr 4 wkflr 6 pbwk off wkGB off maxtr off ; E none

c 0/9/8 ; tabs live ; tgt 3/offR flr 1/3R cap 12 arm offR gb67% start 0000 dayflr 4 wkflr 6 pbwk off wkGB off maxtr off ; E none

| field (semantics) | 8/8-equivalent (as searched) | 6/6-equivalent (all contracts and dollars x 0.75) |
|---|---|---|
| contracts ST / HM / WT-10 | 0 / 9 / 8 | 0 / 6.75 / 6 |
| per-book daily profit target ST / HM | $0 / off | $0 / off |
| per-book daily loss limit ST / HM | $0 / $32,400 | $0 / $24,300 |
| combined daily profit cap | $64,800 | $48,600 |
| combined give-back lock arm / give-back % | off | off |
| give-back lock active from (ET) | 00:00 | 00:00 |
| combined daily loss floor | $21,600 | $16,200 |
| combined weekly loss floor | $32,400 | $24,300 |
| per-book weekly loss limit ST / HM | off / off | off / off |
| combined WEEK give-back arm / keep | off | off |
| max trades per book per session | off | off |
| HM trade health / geometry | TH off, stop 60 pts, target 1R (60 pts), partial none, time stop none | TH off, stop 60 pts, target 1R (60 pts), partial none, time stop none |
| WT-10 trade health / geometry | TH off, stop 60 pts, target 1R (60 pts), partial none, time stop none | TH off, stop 60 pts, target 1R (60 pts), partial none, time stop none |
| sleeve NQ-eq contracts (@ risk fraction of pair-6/6 SD) | none | none |

Last 12 ISO weeks (8/8-equivalent $; 6/6 = x0.75): sleeve column at 50% edge.

| ISO week | live | cell pair-side | cell sleeves | cell total | cell - live | cell total 6/6 | live 6/6 |
|---|---|---|---|---|---|---|---|
| 202631 | 52,186 | -33,360 | 0 | -33,360 | -85,546 | -25,020 | 39,139 |
| 202632 | 40,233 | -33,742 | 0 | -33,742 | -73,975 | -25,306 | 30,174 |
| 202633 | -10,198 | 13,805 | 0 | 13,805 | 24,003 | 10,353 | -7,648 |
| 202634 | 111,628 | 13,669 | 0 | 13,669 | -97,958 | 10,252 | 83,721 |
| 202635 | -56,064 | -37,117 | 0 | -37,117 | 18,947 | -27,837 | -42,048 |
| 202636 | -77,415 | -33,161 | 0 | -33,161 | 44,254 | -24,870 | -58,061 |
| 202637 | -36,884 | -35,566 | 0 | -35,566 | 1,317 | -26,675 | -27,663 |
| 202638 | 116,706 | 84,260 | 0 | 84,260 | -32,445 | 63,195 | 87,529 |
| 202639 | 134,077 | 65,929 | 0 | 65,929 | -68,147 | 49,447 | 100,558 |
| 202640 | -15,630 | -33,772 | 0 | -33,772 | -18,142 | -25,329 | -11,722 |
| 202641 | -54,750 | 49,441 | 0 | 49,441 | 104,191 | 37,080 | -41,062 |
| 202642 | 38,044 | 32,015 | 0 | 32,015 | -6,029 | 24,011 | 28,533 |
| sum | 241,932 | 52,401 | 0 | 52,401 | -189,530 | 39,301 | 181,449 |

## 8. Sizing (lever F): own size, size matched to the pair 6/6 DD52 ($184k weekly path), and a vol-targeted variant

Matched = the whole cell scaled linearly so that its DD52 equals $183.7k (leverage, not edge); vol-targeted = weekly scale = own full-window weekly SD over the trailing 26-week SD (>= 13 weeks), lagged one week, clipped to [0.5, 2] (weekly risk budget held constant). Income, CVaR5 and DD beside every figure; sleeve edge 50%.

| cell | variant | net (% live) | DD52 | P(DD>200k) | CVaR5 | worst | Sharpe | scale |
|---|---|---|---|---|---|---|---|---|
| LIVE | own size | 100% | $245k | 42.5% | -$79k | -$83k | 2.14 | 1.00 |
| LIVE | size matched to pair 6/6 DD | 75% | $184k | 15.2% | -$60k | -$62k | 2.14 | 0.75 |
| LIVE | vol-targeted | 103% | $275k | 50.4% | -$91k | -$100k | 2.09 | mean 1.03 |
| composite best (all levers) | own size | 90% | $69k | 0.1% | -$49k | -$59k | 3.27 | 1.00 |
| composite best (all levers) | size matched to pair 6/6 DD | 240% | $184k | 49.7% | -$131k | -$158k | 3.27 | 2.66 |
| composite best (all levers) | vol-targeted | 99% | $94k | 0.6% | -$53k | -$67k | 3.30 | mean 1.08 |
| best pair-side-only cell (A, B, C, D; no sleeves) | own size | 98% | $104k | 2.8% | -$60k | -$86k | 2.88 | 1.00 |
| best pair-side-only cell (A, B, C, D; no sleeves) | size matched to pair 6/6 DD | 173% | $184k | 43.5% | -$106k | -$151k | 2.88 | 1.77 |
| best pair-side-only cell (A, B, C, D; no sleeves) | vol-targeted | 102% | $118k | 5.0% | -$68k | -$89k | 2.73 | mean 1.05 |

## 9. Gate funnel and validity summary (composite objective, 90% floor)

| gate | cells |
|---|---|
| library rows | 136,720 |
| net >= 90% of live | 44,125 |
| ... and DD52 better than live at income parity (gain) | 23,590 |
| top 300 by DD52 at >= 90% (the gate rows below are evaluated for these) | 300 |
| strict span signs (clean, H1, H2 all improve) | 300 |
| plateau >= 60% | 295 |
| matched null rank >= 0.95 (200 replicates per cell) | 300 |
| best-of-N null rank >= 0.95 | 0 |
| walk-forward gain > 0 (procedure level: WF-A for pair-side cells, WF-B with sleeves) | 0 |
| ALL gates | 0 |

Reading: the matched null and the span/plateau gates are the weak gates (the rules and the sleeves beat random halts and shifted sleeves of the same intensity in-sample, as in SMOOTH); the binding gates are the best-of-N null and the walk-forward on the cell choice. The sleeves' diversification of the pair is real arithmetic if their edge is real (50%-edge rows) but the sleeve series are non-virgin, so the 50% and 0% edge columns are the honest read; the best-of-N null replicates the search with sleeve series circularly shifted against the pair (marginals kept, timing destroyed) and still reaches comparable drawdowns, i.e. most of the in-sample drawdown reduction from sleeves is generic diversification by independent positive-drift series, which no cell choice on this window can distinguish from selection.

## 10. Method notes and limits

- Pre-registered as block DDMIN in PREREG_AUTOPILOT.md before any search cell was scored. Walk-forward gain is defined as the parity-scaled objective (objective at live income by linear size scaling) of the procedure minus live over the same OOS weeks; OOS income share is shown beside it. WF library = the final library (fixed; refinement neighbours were chosen on all-in data, which flatters the walk-forward in favour of the searched cells).
- Best-of-N (the worlds were generated from the immediately preceding library version whose B tables were the superseded 1-second TH rows; the null cells use PLAIN D with random halts at library rates, so only the (A, B, C) structure draw differs, and TH rows are rare among strong cells; they were not regenerated for time): 20 search-replicating null worlds (random-halt pair-side cells at library structures and rates, sleeves circularly shifted per world, random E draws plus the same exhaustive E sweep around the world's own top seeds); N = library size; a pair-side-only variant (sleeves ignored) is used for pair-side-only cells. p200 in the null worlds uses 2,000 bootstrap draws on both sides.
- Trade Health: tick-level tables (see 5b); the 1-second TH tables are not used. Brackets: partial = half at +1R then trail (BE initial); time stop = exit at the open of the first bar >= N minutes after entry. Lever B and C tables are a3a74's sample: 54 TH-off geometries per book (a 54-point sample of the 144-point stop x target x partial x time-stop space), 192 tick TH cells + control for ST and HM, not the full B x C x per-book space; neighbours exist only among sampled tables. WT-10 has geometry tables only.
- Overlap with live: through 2026-10-16 the live ST book ran with TH ON (64% of ST exits were TH loss exits) and the combined give-back lock went live on 2026-10-15; the live record is not the TH-off base.
- Files: code/census/night_ins/ap_dd_core.py (evaluator), ap_dd_events.py, ap_dd_lib.py, ap_dd_met.py, ap_dd_an.py, ap_dd_search.py, ap_dd_refine.py, ap_dd_nulls.py, ap_dd_worlds.py, ap_dd_valid.py, ap_dd_extra.py, ap_dd_planted.py, ap_dd_validate.py, ap_dd_report.py; outputs in outputs/autopilot/ddmin/ (libfinal_*.pkl, valid_*.pkl, worlds_*.npz, planted_*.pkl, validate_evaluator.json).