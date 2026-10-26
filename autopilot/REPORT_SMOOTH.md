# REPORT SMOOTH - risk-rule settings for the smoothest income on the live pair (NT8-faithful engine, 13 rule axes varied jointly)

**Verdict: NO ROBUST CELL on the primary objective (weekly Sharpe). 7,853 grid cells (6,000-cell Latin hypercube + 1,851 refinement neighbours + live + plain) and 256 stored DAYRULES/WEEKGB reference cells were scored. 1,583 cells beat live by >= +0.10 all-in weekly Sharpe and 683 do so in clean, H1 and H2 alike; 509 of those have a plateau >= 60%; but the walk-forward on the cell choice LOSES to the live rules (OOS 2024-02..2026-10: chosen-cell Sharpe 1.70 / CVaR5 -96k / net 74% of live, against live 2.15 / -79k / 100%), and the best in-sample Sharpe (2.68, net 126% of live, CVaR5 -59k) ranks only 0.28 against the best-of-8,109 random-halt null (median null best 2.72). Gate funnel (Sharpe objective): 1583 -> signs 683 -> plateau 509 -> matched null 509 -> best-of-N 0 -> walk-forward 0: 0 survive.** On the secondary CVaR5 the pre-registered gates are passed by 495 cells (their gain is the 6R week floor / 3R day floor / 1R-arm tail rules, bought at income cost out of sample; see section 6). Nothing here changes the live pair; no live change is recommended.

## 1. Base, engine, conventions

- Engine: the NT8-faithful 1-second-engine trade rows (ROWS_corrected_engine, 13,184 rows, TH-OFF) through the account layer of DAYRULES/WEEKGB (per-book rules -> combined day lock -> combined week stage), clean process. **Live config asserted: weekly Sharpe clean/H1/H2/all-in 1.46/2.83/2.48/1.90** (all-in net $2,743,504, max DD $280,110, worst week -$82,524, CVaR5 -$79,220). TH: the base is TH-OFF for both books (as DAYRULES/WEEKGB); **the live chart has ST TH ON, HM TH OFF**; no TH-on pair rows exist, so every delta is against the TH-off live cell. Dollars at 8/8; **6/6 is 0.75x linear (no lot rounding)**; R = $9,600 per book at 8/8 ($7,200 at 6/6). Pre-registered as block SMOOTH in PREREG_AUTOPILOT.md before any cell was scored.
- Evaluator: numba re-implementation of pass 1 + lock_stage on the stored trade rows (no entry re-simulation), ~1.2 ms per cell on 8 threads. **Validation against the engine: max daily difference $0.00** on the live cell, plain, 20 random symmetric cells run through `b11_nt8.run(Cfg(...))` (the engine itself), 20 random full-axis cells through a plain-python reference chain (new axes included), and all 214 stored DAYRULES series. See sm/validate_evaluator.json.
- Axes (13): per-book daily target ST x HM {off,3,4,5,6,8}R; per-book daily floor ST x HM {off,1,1.5,2,3}R; combined cap {off,4,5,6,8,10,12}R; give-back arm {off,1,1.5,2,3,4}R x give-back {33,50,67,80}%; lock start {00:00, 09:30 ET} (gates the give-back arm, as the engine's gb_start); combined day loss floor {off,2,3,4}R; combined week floor {off,6,8,10}R; per-book week loss rule {off,6}R; week give-back {off, arm 5R keep 50%, arm 6R keep 67%}; max trades per book per session {off,6,10}. Live = 5/5, 2/2, cap 8, arm 2R, give-back 67%, 00:00, day floor off, week floor 8, per-book week off, week GB off, max trades off.
- Search: 6,000-cell seeded LHS (every level of every axis hit >= 857 times; the minimum is the 12R cap level), refinement of the 50 best on Sharpe and 50 best on CVaR5 (+-1 step on all 13 axes, 1,851 new cells), live and plain, and the stored DAYRULES (214) and WEEKGB (42) cell series as references (library = 8,109 series). Selection is on the all-in span 2023-08-01..2026-10-16 (weekly P&L of ISO weeks); walk-forward weeks start 2023-02-10.
- Live was itself tuned on this same window, so every comparison against live in the walk-forward is tilted toward live; the in-sample table is tilted toward the searched cells. Neither is a clean out-of-sample statement about the future; the pair has ~3.7 years of data.

## 2. Pareto frontier: in-sample best vs walk-forward procedure, side by side

Each row: among cells with all-in net >= level x live net, the cell with the best weekly Sharpe (or best CVaR5). Income and CVaR5 (or Sharpe) are shown beside every figure. The walk-forward columns are the stitched OOS weeks of the PROCEDURE (best cell on trailing 52 weeks under the same trailing-income constraint, applied to the next 13 weeks, 11 folds, 141 weeks) against live over the same weeks. Because the best Sharpe cell has more income than live in-sample, the income constraint never binds for the Sharpe procedure and its five rows are identical.

| income level | objective | IN-SAMPLE best cell (all-in span) | net all-in (% live) | Sharpe c/H1/H2/all | CVaR5 | %neg wk | max DD | worst wk | longest DD (wk) | WF OOS Sharpe | WF OOS CVaR5 | WF OOS net | WF OOS %neg wk | WF OOS worst wk | WF OOS max DD (weekly eq.) | WF OOS longest DD (wk) | WF OOS net % of live OOS | in-sample cell on the same OOS weeks (Sharpe / CVaR5 / net) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 100/95/90/80/70% | Sharpe | tgt 8/8R flr 1/1.5R cap 12 arm 1R gb80% start 0000 dayflr 3 wkflr 6 pbwk 6 wkGB 5R/keep50% maxtr 10 | 3.45M (126%) | 1.89/3.85/4.10/**2.68** | -59k | 36.3 | 233k | -63k | 15 | 1.70 | -96k | 1.96M | 36.2 | -138k | 343k | 24 | 74% | 2.94 / -59k / 3.26M |
| 100% | CVaR5 | tgt 8/5R flr 2/1R cap off arm 1R gb80% start 0000 dayflr 3 wkflr 6 pbwk off wkGB 5R/keep50% maxtr 6 | 2.85M (104%) | 2.23/2.25/3.20/**2.46** | -58k | 38.7 | 240k | -59k | 14 | 1.77 | -74k | 1.76M | 40.4 | -117k | 302k | 23 | 66% | 2.71 / -59k / 2.71M |
| 95% | CVaR5 | tgt 8/5R flr 2/1R cap off arm 1R gb80% start 0000 dayflr 3 wkflr 6 pbwk off wkGB 5R/keep50% maxtr 6 | 2.85M (104%) | 2.23/2.25/3.20/**2.46** | -58k | 38.7 | 240k | -59k | 14 | 1.77 | -62k | 1.72M | 41.1 | -73k | 226k | 23 | 65% | 2.71 / -59k / 2.71M |
| 90% | CVaR5 | tgt 5/offR flr 2/3R cap 8 arm 1R gb80% start 0000 dayflr 3 wkflr 6 pbwk 6 wkGB 6R/keep67% maxtr 10 | 2.55M (93%) | 1.69/2.90/2.70/**2.12** | -58k | 44.6 | 212k | -59k | 23 | 1.70 | -67k | 1.70M | 42.6 | -97k | 228k | 40 | 64% | 2.26 / -58k / 2.33M |
| 80% | CVaR5 | tgt 5/offR flr 2/3R cap 8 arm 1R gb80% start 0000 dayflr 3 wkflr 6 pbwk 6 wkGB 6R/keep67% maxtr 10 | 2.55M (93%) | 1.69/2.90/2.70/**2.12** | -58k | 44.6 | 212k | -59k | 23 | 1.62 | -70k | 1.59M | 43.3 | -78k | 261k | 40 | 60% | 2.26 / -58k / 2.33M |
| 70% | CVaR5 | tgt 4/5R flr 1.5/offR cap 5 arm 1R gb67% start 0000 dayflr 3 wkflr 6 pbwk off wkGB 5R/keep50% maxtr 6 | 1.99M (72%) | 1.80/2.37/2.63/**2.09** | -58k | 41.1 | 224k | -59k | 17 | 1.64 | -70k | 1.42M | 42.6 | -78k | 245k | 40 | 53% | 2.37 / -58k / 1.94M |
| live (reference) | - | live cell | 2.74M (100%) | 1.46/2.83/2.48/**1.90** | -79k | 42.3 | 280k | -83k | 23 | 2.15 | -79k | 2.66M | 40.4 | -83k | 245k | 8 | 100% | - |

Reading: the in-sample frontier looks like free lunch (Sharpe up to 2.68 at 126% of live income; CVaR5 up to -58k at 104%); the walk-forward procedure delivers the opposite once the choice has to be made on past weeks: OOS Sharpe 1.70 against live 2.15, net 74% of live, and the CVaR5 procedure improves the OOS tail only by giving up income (100% band: CVaR5 -74k, net 66%, Sharpe 1.77, 90% band: CVaR5 -67k, net 64%, Sharpe 1.70, 70% band: CVaR5 -70k, net 53%, Sharpe 1.64). Folds where the Sharpe-chosen cell kept at least live's income: 2 of 11; distinct cells chosen: 11 of 11 (the choice is unstable).

### Walk-forward cell choice per fold (rolling: trailing 52 weeks -> next 13)

| fold (test weeks) | chosen on Sharpe (trailing 52w) | test-block net | live test-block net | chosen on CVaR5 at 100% income band | test-block net |
|---|---|---|---|---|---|
| 202406-202418 | tgt 5/3R flr 2/offR cap 5 arm 1.5R gb50% start 0000 dayflr 4 wkflr off pbwk off wkGB 5R/keep50% maxtr 6 | 38k | 81k | tgt off/4R flr 1/3R cap off arm 1R gb33% start 0000 dayflr 2 wkflr off pbwk off wkGB 6R/keep67% maxtr off | 147k |
| 202419-202431 | tgt 8/4R flr off/offR cap 6 arm 1.5R gb50% start 0000 dayflr 2 wkflr 10 pbwk off wkGB 5R/keep50% maxtr 10 | 378k | 421k | tgt 4/8R flr off/2R cap 8 arm 1R gb50% start 0000 dayflr 2 wkflr 8 pbwk 6 wkGB off maxtr 6 | 441k |
| 202432-202444 | tgt 8/4R flr 3/2R cap 8 arm 1.5R gb50% start 0000 dayflr 4 wkflr 10 pbwk 6 wkGB 5R/keep50% maxtr 10 | 130k | 33k | tgt 4/8R flr off/2R cap 8 arm 1R gb50% start 0000 dayflr 2 wkflr 8 pbwk 6 wkGB off maxtr 6 | 59k |
| 202445-202505 | tgt 8/4R flr 3/2R cap 10 arm 1.5R gb50% start 0000 dayflr 4 wkflr 10 pbwk 6 wkGB 5R/keep50% maxtr 6 | 205k | 243k | tgt 8/3R flr 3/offR cap 6 arm 1R gb50% start 0000 dayflr 3 wkflr off pbwk 6 wkGB 6R/keep67% maxtr 6 | -15k |
| 202506-202518 | tgt off/offR flr 1.5/3R cap 12 arm 1R gb67% start 0000 dayflr off wkflr 10 pbwk off wkGB 5R/keep50% maxtr off | 185k | 314k | tgt 6/6R flr off/1R cap 12 arm 1R gb50% start 0000 dayflr 2 wkflr 8 pbwk 6 wkGB 6R/keep67% maxtr 10 | 93k |
| 202519-202531 | tgt 8/8R flr off/offR cap off arm 1.5R gb50% start 0000 dayflr 4 wkflr off pbwk off wkGB 5R/keep50% maxtr 6 | -106k | 164k | tgt off/8R flr 3/offR cap 8 arm 1R gb67% start 0000 dayflr 3 wkflr off pbwk off wkGB 6R/keep67% maxtr off | 69k |
| 202532-202544 | tgt 8/5R flr 2/1R cap off arm 1R gb80% start 0000 dayflr 3 wkflr 6 pbwk off wkGB off maxtr 6 | 234k | 354k | tgt 8/5R flr 2/1R cap off arm 1R gb80% start 0000 dayflr 3 wkflr 6 pbwk off wkGB 5R/keep50% maxtr 6 | 202k |
| 202545-202605 | tgt 5/3R flr off/1R cap 6 arm 1.5R gb80% start 0000 dayflr 4 wkflr 6 pbwk off wkGB off maxtr off | 123k | 258k | tgt 6/6R flr 3/1R cap off arm 4R gb80% start 0930 dayflr off wkflr 6 pbwk 6 wkGB 6R/keep67% maxtr 6 | 244k |
| 202606-202618 | tgt 8/3R flr 1.5/2R cap 4 arm offR gb67% start 0930 dayflr 4 wkflr 6 pbwk off wkGB off maxtr off | 414k | 241k | tgt 6/3R flr 3/1R cap 12 arm 1.5R gb80% start 0000 dayflr 3 wkflr 6 pbwk 6 wkGB off maxtr off | 209k |
| 202619-202631 | tgt 4/offR flr off/1R cap 12 arm 4R gb67% start 0930 dayflr 4 wkflr 8 pbwk off wkGB 5R/keep50% maxtr 10 | 221k | 363k | tgt off/3R flr off/offR cap 8 arm 1R gb80% start 0000 dayflr 3 wkflr 6 pbwk 6 wkGB 5R/keep50% maxtr 6 | 256k |
| 202632-202642 | tgt 4/offR flr off/offR cap 8 arm 3R gb50% start 0930 dayflr 4 wkflr 8 pbwk off wkGB 5R/keep50% maxtr 10 | 136k | 190k | tgt off/3R flr off/offR cap 8 arm 1R gb80% start 0000 dayflr 3 wkflr 6 pbwk 6 wkGB 5R/keep50% maxtr 6 | 54k |

### Supplementary: expanding-window variant of the same procedure (all weeks since 2023-02-10 -> next 13; not pre-registered, reported as a sensitivity check)

| procedure | OOS Sharpe | OOS CVaR5 | OOS net (% of live OOS) | %neg wk | distinct cells chosen |
|---|---|---|---|---|---|
| expanding window, best on Sharpe, income >= none | 1.85 | -95k | 1.97M (74%) | 34.8 | 8 |
| expanding window, best on Sharpe, income >= 100% | 1.85 | -95k | 1.97M (74%) | 34.8 | 8 |
| expanding window, best on Sharpe, income >= 90% | 1.85 | -95k | 1.97M (74%) | 34.8 | 8 |
| expanding window, best on Sharpe, income >= 70% | 1.85 | -95k | 1.97M (74%) | 34.8 | 8 |
| expanding window, best on CVaR5, income >= none | 1.08 | -67k | 0.78M (29%) | 41.8 | 5 |
| expanding window, best on CVaR5, income >= 100% | 1.97 | -67k | 1.71M (64%) | 41.1 | 8 |
| expanding window, best on CVaR5, income >= 90% | 1.77 | -68k | 1.53M (57%) | 40.4 | 8 |
| expanding window, best on CVaR5, income >= 70% | 1.22 | -68k | 0.92M (34%) | 41.1 | 8 |

## 3. Top 10 cells on weekly Sharpe (in-sample, with income and CVaR5 beside)

| rank | cell | net all-in (% live) | Sharpe c/H1/H2/all | CVaR5 | %neg wk | max DD | worst wk | longest DD (wk) | other-objective | span signs (c/H1/H2) on this objective | plateau | matched-null rank | best-of-N rank | WF gain at band |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | tgt 8/8R flr 1/1.5R cap 12 arm 1R gb80% start 0000 dayflr 3 wkflr 6 pbwk 6 wkGB 5R/keep50% maxtr 10 | 3.45M (126%) | 1.89/3.85/4.10/**2.68** | -59k | 36.3 | 233k | -63k | 15 | CVaR5 -59k | +++ | 0.60 | 1.00 | 0.28 | -0.45 |
| 2 | tgt 4/offR flr off/offR cap 10 arm 3R gb50% start 0000 dayflr 4 wkflr 8 pbwk off wkGB 5R/keep50% maxtr 10 | 3.55M (129%) | 1.82/3.50/4.63/**2.66** | -78k | 26.2 | 356k | -79k | 20 | CVaR5 -78k | +++ | 0.48 | 1.00 | 0.22 | -0.45 |
| 3 | tgt 4/offR flr off/3R cap 8 arm 3R gb50% start 0000 dayflr 4 wkflr 8 pbwk off wkGB 5R/keep50% maxtr 10 | 3.39M (123%) | 1.79/3.50/4.74/**2.65** | -78k | 25.6 | 373k | -79k | 20 | CVaR5 -78k | +++ | 0.45 | 1.00 | 0.18 | -0.45 |
| 4 | tgt 4/8R flr off/offR cap 8 arm 3R gb50% start 0000 dayflr 4 wkflr 8 pbwk off wkGB 5R/keep50% maxtr 10 | 3.35M (122%) | 1.74/3.50/4.74/**2.62** | -78k | 26.2 | 373k | -79k | 20 | CVaR5 -78k | +++ | 0.55 | 1.00 | 0.11 | -0.45 |
| 5 | tgt 4/offR flr off/offR cap 8 arm 3R gb50% start 0000 dayflr 4 wkflr 8 pbwk off wkGB 5R/keep50% maxtr 10 | 3.35M (122%) | 1.74/3.50/4.74/**2.62** | -78k | 26.2 | 373k | -79k | 20 | CVaR5 -78k | +++ | 0.52 | 1.00 | 0.11 | -0.45 |
| 6 | tgt 6/4R flr off/1.5R cap 8 arm 1R gb67% start 0930 dayflr off wkflr off pbwk off wkGB 6R/keep67% maxtr off | 3.31M (121%) | 1.67/3.69/5.10/**2.60** | -107k | 30.4 | 274k | -165k | 16 | CVaR5 -107k | +++ | 0.56 | 1.00 | 0.10 | -0.45 |
| 7 | tgt 5/offR flr off/offR cap 8 arm 3R gb50% start 0000 dayflr 4 wkflr 8 pbwk off wkGB 5R/keep50% maxtr 10 | 3.32M (121%) | 1.69/3.67/4.76/**2.60** | -78k | 26.8 | 374k | -79k | 20 | CVaR5 -78k | +++ | 0.38 | 1.00 | 0.09 | -0.45 |
| 8 | tgt off/offR flr 1/offR cap off arm 1R gb80% start 0000 dayflr 3 wkflr 8 pbwk 6 wkGB 5R/keep50% maxtr 10 | 3.39M (124%) | 1.92/3.38/3.79/**2.59** | -76k | 36.3 | 276k | -78k | 14 | CVaR5 -76k | +++ | 0.59 | 1.00 | 0.06 | -0.45 |
| 9 | tgt 6/8R flr 3/2R cap 10 arm 4R gb50% start 0000 dayflr 4 wkflr 8 pbwk 6 wkGB 5R/keep50% maxtr 6 | 3.36M (123%) | 1.83/4.02/3.79/**2.58** | -78k | 27.4 | 398k | -79k | 17 | CVaR5 -78k | +++ | 0.61 | 1.00 | 0.06 | -0.45 |
| 10 | tgt 5/3R flr off/2R cap 8 arm 4R gb50% start 0930 dayflr 4 wkflr 8 pbwk 6 wkGB 5R/keep50% maxtr 6 | 3.43M (125%) | 1.75/3.94/4.19/**2.58** | -78k | 28.6 | 398k | -79k | 17 | CVaR5 -78k | +++ | 0.62 | 1.00 | 0.06 | -0.45 |

## 4. Top 10 cells on CVaR5

| rank | cell | net all-in (% live) | Sharpe c/H1/H2/all | CVaR5 | %neg wk | max DD | worst wk | longest DD (wk) | other-objective | span signs (c/H1/H2) on this objective | plateau | matched-null rank | best-of-N rank | WF gain at band |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | tgt off/8R flr 1/offR cap 8 arm 1R gb33% start 0000 dayflr 2 wkflr 6 pbwk 6 wkGB off maxtr off | 0.65M (24%) | 0.95/0.94/0.42/**0.82** | -58k | 46.4 | 281k | -61k | 59 | Sharpe 0.82 | +++ | 0.93 | 1.00 | 1.00 | +9.0k |
| 2 | tgt 4/5R flr 1.5/offR cap 5 arm 1R gb67% start 0000 dayflr 3 wkflr 6 pbwk off wkGB 5R/keep50% maxtr 6 | 1.99M (72%) | 1.80/2.37/2.63/**2.09** | -58k | 41.1 | 224k | -59k | 17 | Sharpe 2.09 | +++ | 0.95 | 1.00 | 1.00 | +9.0k |
| 3 | tgt 4/5R flr 1.5/offR cap 4 arm 1R gb67% start 0000 dayflr 3 wkflr 6 pbwk 6 wkGB 6R/keep67% maxtr 6 | 1.47M (54%) | 1.24/2.11/2.18/**1.61** | -58k | 44.0 | 185k | -59k | 22 | Sharpe 1.61 | +++ | 0.94 | 1.00 | 1.00 | +9.0k |
| 4 | tgt 3/5R flr 2/2R cap 6 arm 1R gb67% start 0000 dayflr 3 wkflr 6 pbwk off wkGB 5R/keep50% maxtr off | 1.91M (70%) | 1.79/2.23/2.34/**2.00** | -58k | 41.1 | 227k | -59k | 17 | Sharpe 2.00 | +++ | 0.95 | 1.00 | 1.00 | +9.0k |
| 5 | tgt off/4R flr 1/1R cap 4 arm 1R gb33% start 0000 dayflr 2 wkflr 6 pbwk off wkGB off maxtr off | 0.67M (24%) | 0.87/1.31/0.51/**0.86** | -58k | 45.2 | 276k | -60k | 36 | Sharpe 0.86 | +++ | 0.93 | 1.00 | 1.00 | +9.0k |
| 6 | tgt 3/8R flr 1.5/offR cap 6 arm 1R gb67% start 0000 dayflr 3 wkflr 6 pbwk off wkGB 5R/keep50% maxtr off | 1.92M (70%) | 1.75/1.99/2.67/**2.01** | -58k | 41.7 | 225k | -59k | 17 | Sharpe 2.01 | +++ | 0.95 | 1.00 | 1.00 | +9.0k |
| 7 | tgt 4/5R flr 1.5/offR cap 4 arm 1R gb67% start 0000 dayflr 3 wkflr 6 pbwk off wkGB 6R/keep67% maxtr 10 | 1.66M (60%) | 1.48/2.21/2.40/**1.82** | -58k | 43.5 | 202k | -59k | 17 | Sharpe 1.82 | +++ | 0.95 | 1.00 | 1.00 | +9.0k |
| 8 | tgt 5/offR flr 2/offR cap 6 arm 1R gb80% start 0000 dayflr 3 wkflr 6 pbwk 6 wkGB 6R/keep67% maxtr 10 | 1.86M (68%) | 1.53/2.29/1.92/**1.76** | -58k | 44.0 | 215k | -59k | 23 | Sharpe 1.76 | +++ | 0.94 | 1.00 | 1.00 | +9.0k |
| 9 | tgt 5/4R flr 1.5/1.5R cap 5 arm 1R gb67% start 0000 dayflr 3 wkflr 6 pbwk 6 wkGB 6R/keep67% maxtr 6 | 1.59M (58%) | 1.34/2.34/2.30/**1.72** | -58k | 42.9 | 213k | -60k | 18 | Sharpe 1.72 | +++ | 0.95 | 1.00 | 1.00 | +9.0k |
| 10 | tgt 4/5R flr 1.5/offR cap 4 arm 1R gb67% start 0000 dayflr 3 wkflr 6 pbwk 6 wkGB 5R/keep50% maxtr 10 | 1.23M (45%) | 1.24/1.70/1.69/**1.42** | -58k | 42.3 | 232k | -59k | 18 | Sharpe 1.42 | +++ | 0.95 | 1.00 | 1.00 | +9.0k |

Notes: plateau = share of the +-1-step neighbours (up to 26) keeping >= 75% of the cell's all-in gain on that objective; matched-null rank = share of 200 random-halt replicates (PLAIN base, same day-level and week-level firing rates as the cell) below the cell; best-of-N rank = share of the 200 null worlds whose best of N=8,109 random-halt cells is below the cell; WF gain at band = OOS procedure value at the cell's income band minus live OOS (Sharpe points, or CVaR5 $k); span signs = improvement over live in clean/H1/H2 on that objective. Firing-rate matching counts a day as fired if a per-book rule blocked an entry or the day lock fired, which is why the matched rates are high (live: 669 of 953 days) and the null is a hard bar.

## 5. Validity of the search result

Gate funnel (all gates pre-registered; a cell must pass every one on its own objective):

| gate | Sharpe objective | CVaR5 objective |
|---|---|---|
| grid cells scored | 7,853 | 7,853 |
| (gain) all-in gain over live (Sharpe >= +0.10 / CVaR5 >= +$1) | 1,583 | 4,194 |
| (d) strict span signs (clean, H1, H2 all improve) | 683 | 3,042 |
| (c) plateau >= 60% of neighbours keep >= 75% of the gain | 509 | 2,993 |
| (b) matched random-halt null rank >= 0.95: passed / evaluated (Sharpe: all plateau survivors; CVaR5: the top 300 + top 100 per income band by CVaR5 among walk-forward survivors) | 509 / 509 | 574 / 579 |
| (b) best-of-N null rank >= 0.95 (of those passing the matched null) | 0 / 509 | 495 / 574 |
| (a) walk-forward gain > 0 at the cell's income band (procedure-level, so identical for every cell in a band) | 0 / 0 | 495 / 495 |

**Sharpe.** The walk-forward procedure never beats live out of sample at any income band (OOS Sharpe 1.70 vs 2.15), so (a) rules out every Sharpe cell regardless of the others. The best-of-N null is equally unforgiving: random-halt cells at matched firing rates reach a best Sharpe of 2.58 / **2.72** / 2.95 (5th / median / 95th percentile over 200 null worlds, N=8,109 cells each) against the best real cell 2.68 (rank 0.28). Rank of the best real cell against smaller independent-trial counts: N=16: 0.99, N=64: 0.98, N=256: 0.95, N=1024: 0.85, N=4096: 0.47. The real cells are strongly correlated (the effective number of independent trials is far below 8,109), so the full-N null is conservative; but even at N=1,024 the best cell is not clearly outside what luck produces, and the walk-forward result is independent of that debate. Matched-null rank (cell vs random halts at its own firing rate, no multiplicity correction): 509 of the 509 plateau-surviving Sharpe cells reach 0.95; i.e. the rules do beat random halting at the same intensity, which is the weakest of the gates; the multiplicity (best-of-N) and walk-forward gates are the binding ones.

**CVaR5.** 495 cells pass every pre-registered gate when CVaR5 is the objective (matched null and best-of-N evaluated on the 579 shortlisted; 186 of the 495 also gain >= +0.10 all-in Sharpe). Their common structure is the tail machinery (combined week floor 6R instead of 8R is the dominant lever: marginal mean CVaR5 -60k at 6R vs -78k at 8R; plus combined day loss floor 3R-4R and give-back arm 1R with 80% give-back): in-sample CVaR5 -58k to -59k against live -79k, worst week -59k to -63k against -83k. Two readings of the recommendation rule: (A) strict, Sharpe primary: no cell qualifies (section 6). (B) CVaR5-lens: the cell with the smallest income cost among the CVaR5-robust cells that also gain >= +0.10 Sharpe is tgt 8/8R flr 1/1.5R cap 12 arm 1R gb80% start 0000 dayflr 3 wkflr 6 pbwk 6 wkGB 5R/keep50% maxtr 10 (net 126% of live, Sharpe 2.68, CVaR5 -59k) - it is the same cell as the top Sharpe cell, which fails reading (A) on the walk-forward (-0.45 Sharpe) and best-of-N (0.28). The CVaR5 walk-forward gain is real but small and bought with income and Sharpe: the procedure at the 100% band reaches OOS CVaR5 -74k vs live -79k but at 66% of live OOS income and OOS Sharpe 1.77 < 2.15 (95% band: -62k, 65%, Sharpe 1.77). Fold consistency of the top Sharpe cell itself (in-sample, 11 test blocks of 13 weeks): net >= live in 8 of 11 blocks, better worst week in 10 of 11. I do not recommend acting on (B): the cell was found on these same weeks, the choice procedure that would have found it out of sample does not.

### Where the smoothness comes from (marginal means over the 6,000-cell LHS; balanced design, so each row is an unbiased average over all other axes)

| axis | level | mean weekly Sharpe | mean CVaR5 | mean net (% live) | cells |
|---|---|---|---|---|---|
| stw | 3 | 1.44 | -84k | 68% | 1000 |
| stw | 4 | 1.53 | -85k | 73% | 1000 |
| stw | 5 | 1.49 | -84k | 72% | 1001 |
| stw | 6 | 1.53 | -85k | 74% | 1000 |
| stw | 8 | 1.51 | -85k | 73% | 1000 |
| stw | off | 1.52 | -85k | 73% | 1001 |
| hmw | 3 | 1.49 | -85k | 72% | 1000 |
| hmw | 4 | 1.50 | -85k | 72% | 1000 |
| hmw | 5 | 1.50 | -86k | 72% | 1001 |
| hmw | 6 | 1.50 | -84k | 72% | 1000 |
| hmw | 8 | 1.51 | -84k | 72% | 1000 |
| hmw | off | 1.50 | -84k | 72% | 1001 |
| stl | 1 | 1.62 | -82k | 76% | 1200 |
| stl | 1.5 | 1.44 | -85k | 70% | 1200 |
| stl | 2 | 1.45 | -85k | 70% | 1201 |
| stl | 3 | 1.49 | -86k | 72% | 1200 |
| stl | off | 1.52 | -85k | 73% | 1201 |
| hml | 1 | 1.41 | -83k | 66% | 1200 |
| hml | 1.5 | 1.53 | -85k | 74% | 1200 |
| hml | 2 | 1.52 | -85k | 73% | 1201 |
| hml | 3 | 1.52 | -85k | 73% | 1200 |
| hml | off | 1.53 | -86k | 74% | 1201 |
| cap | 4 | 1.22 | -86k | 53% | 858 |
| cap | 5 | 1.28 | -85k | 57% | 857 |
| cap | 6 | 1.36 | -84k | 62% | 857 |
| cap | 8 | 1.61 | -83k | 79% | 858 |
| cap | 10 | 1.68 | -84k | 84% | 857 |
| cap | 12 | 1.67 | -86k | 85% | 857 |
| cap | off | 1.69 | -85k | 86% | 858 |
| arm | 1 | 1.41 | -79k | 60% | 1000 |
| arm | 1.5 | 1.55 | -81k | 70% | 1000 |
| arm | 2 | 1.51 | -84k | 71% | 1001 |
| arm | 3 | 1.46 | -87k | 73% | 1000 |
| arm | 4 | 1.56 | -88k | 80% | 1000 |
| arm | off | 1.52 | -89k | 78% | 1001 |
| gb | 33 | 1.30 | -84k | 60% | 1250 |
| gb | 50 | 1.54 | -84k | 71% | 1248 |
| gb | 67 | 1.56 | -86k | 76% | 2254 |
| gb | 80 | 1.57 | -84k | 77% | 1250 |
| start | 0 | 1.51 | -83k | 70% | 3002 |
| start | 570 | 1.49 | -86k | 74% | 3000 |
| dfl | 2 | 1.23 | -79k | 57% | 1500 |
| dfl | 3 | 1.56 | -84k | 74% | 1500 |
| dfl | 4 | 1.66 | -87k | 81% | 1500 |
| dfl | off | 1.55 | -88k | 76% | 1502 |
| wfl | 6 | 1.43 | -60k | 66% | 1500 |
| wfl | 8 | 1.54 | -78k | 73% | 1502 |
| wfl | 10 | 1.51 | -94k | 74% | 1500 |
| wfl | off | 1.52 | -106k | 75% | 1500 |
| pbw | 6 | 1.50 | -84k | 72% | 3000 |
| pbw | off | 1.51 | -86k | 73% | 3002 |
| wgb | off | 1.42 | -84k | 74% | 2002 |
| wgb | (5, 0.5) | 1.54 | -85k | 71% | 2000 |
| wgb | (6, 0.67) | 1.55 | -85k | 72% | 2000 |
| maxt | 6 | 1.56 | -84k | 72% | 2000 |
| maxt | 10 | 1.50 | -86k | 73% | 2000 |
| maxt | off | 1.45 | -84k | 71% | 2002 |

### Single changes from the live cell (all 26 one-step neighbours)

| single change from live | net all-in (% live) | Sharpe c/H1/H2/all | CVaR5 | %neg wk | max DD | worst wk | longest DD (wk) | span signs on Sharpe | matched-null rank (Sharpe) | matched-null rank (CVaR5) |
|---|---|---|---|---|---|---|---|---|---|---|
| stw: 5 -> 4 | 2.85M (104%) | 1.49/3.10/2.50/**1.96** | -79k | 41.1 | 253k | -83k | 23 | +++ | 0.96 | 0.90 |
| hmw: 5 -> 4 | 2.85M (104%) | 1.49/2.89/2.55/**1.96** | -79k | 41.7 | 280k | -82k | 23 | +++ | 0.94 | 0.98 |
| stl: 2 -> 1.5 | 2.70M (98%) | 1.49/2.65/2.12/**1.82** | -79k | 41.1 | 356k | -82k | 23 | +-- | 0.94 | 0.84 |
| hml: 2 -> 1.5 | 2.80M (102%) | 1.51/2.99/2.60/**1.98** | -79k | 40.5 | 286k | -83k | 23 | +++ | 0.98 | 0.94 |
| cap: 8 -> 6 | 2.31M (84%) | 1.26/2.51/2.15/**1.68** | -79k | 42.9 | 248k | -83k | 23 | --- | 0.86 | 0.96 |
| arm: 2 -> 1.5 | 2.56M (93%) | 1.75/1.60/2.08/**1.82** | -79k | 41.7 | 218k | -82k | 23 | +-- | 0.97 | 0.96 |
| gb: 67 -> 50 | 2.44M (89%) | 1.51/1.89/2.28/**1.75** | -80k | 42.3 | 235k | -83k | 23 | +-- | 0.91 | 0.61 |
| dfl: None -> 4 | 2.69M (98%) | 1.53/2.42/2.40/**1.87** | -79k | 41.1 | 241k | -81k | 23 | +-- | 0.94 | 0.87 |
| wfl: 8 -> 6 | 1.79M (65%) | 1.04/1.95/1.24/**1.23** | -60k | 48.2 | 473k | -64k | 37 | --- | 0.49 | 1.00 |
| pbw: None -> 6 | 2.50M (91%) | 1.30/2.55/2.29/**1.72** | -79k | 42.3 | 344k | -82k | 23 | --- | 0.88 | 0.98 |
| maxt: None -> 10 | 2.69M (98%) | 1.46/2.96/2.26/**1.87** | -79k | 41.7 | 280k | -82k | 23 | -+- | 0.95 | 0.98 |
| wgb: None -> (5, 0.5) | 2.77M (101%) | 1.70/2.79/2.87/**2.13** | -79k | 32.1 | 276k | -83k | 11 | +-+ | 0.99 | 0.85 |
| wfl: 8 -> 10 | 2.65M (97%) | 1.32/2.50/2.59/**1.78** | -98k | 41.1 | 318k | -101k | 23 | --+ | 0.92 | 0.00 |
| start: 0 -> 570 | 2.40M (87%) | 1.31/2.45/1.45/**1.53** | -80k | 44.6 | 405k | -83k | 23 | --- | 0.75 | 0.87 |
| gb: 67 -> 80 | 2.99M (109%) | 1.40/2.77/2.55/**1.90** | -80k | 44.6 | 329k | -83k | 23 | --+ | 0.96 | 0.81 |
| arm: 2 -> 3 | 2.80M (102%) | 0.95/3.67/2.77/**1.74** | -80k | 40.5 | 393k | -83k | 23 | -++ | 0.94 | 0.63 |
| cap: 8 -> 10 | 2.86M (104%) | 1.58/2.77/2.20/**1.91** | -79k | 42.9 | 280k | -83k | 23 | +-- | 0.96 | 0.95 |
| hml: 2 -> 3 | 2.81M (102%) | 1.36/2.50/3.06/**1.91** | -78k | 44.0 | 314k | -79k | 23 | --+ | 0.95 | 1.00 |
| stl: 2 -> 3 | 2.45M (89%) | 1.21/3.69/1.54/**1.64** | -79k | 41.1 | 305k | -81k | 24 | -+- | 0.84 | 0.93 |
| hmw: 5 -> 6 | 2.70M (99%) | 1.46/2.68/2.43/**1.87** | -79k | 42.3 | 280k | -83k | 23 | +-- | 0.93 | 0.91 |
| stw: 5 -> 6 | 2.81M (102%) | 1.46/2.83/2.57/**1.92** | -79k | 42.3 | 280k | -83k | 23 | -++ | 0.97 | 0.94 |

### Reference cells

| reference | net all-in (% live) | Sharpe c/H1/H2/all | CVaR5 | %neg wk | max DD | worst wk | longest DD (wk) |
|---|---|---|---|---|---|---|---|
| LIVE (re-scored, asserted 1.46/2.83/2.48/1.90) | 2.74M (100%) | 1.46/2.83/2.48/**1.90** | -79k | 42.3 | 280k | -83k | 23 |
| PLAIN (no daily rules, week floor 8 kept) | 2.80M (102%) | 0.98/3.88/0.83/**1.41** | -83k | 44.6 | 497k | -92k | 31 |
| best stored DAYRULES/WEEKGB cell on Sharpe: WG GBa arm=5R keep=67% | 2.64M (96%) | 1.75/3.13/3.06/**2.28** | -79k | 32.1 | 255k | -83k | 12 |
| best stored DAYRULES/WEEKGB cell on Sharpe: WG GBb arm=5R keep=67% | 2.84M (104%) | 1.66/2.97/3.46/**2.26** | -79k | 34.5 | 251k | -83k | 13 |
| best stored DAYRULES/WEEKGB cell on Sharpe: WG GBa arm=4R keep=67% | 2.33M (85%) | 1.59/3.55/2.88/**2.19** | -79k | 28.6 | 250k | -83k | 12 |
| best stored DAYRULES/WEEKGB cell on CVaR5: DR G3 ST flr=1 HM flr=1 | 2.12M (77%) | 1.40/3.05/1.03/**1.55** | -78k | 42.3 | 321k | -79k | 37 |
| best stored DAYRULES/WEEKGB cell on CVaR5: DR G3 ST flr=2 HM flr=3 | 2.81M (102%) | 1.36/2.50/3.06/**1.91** | -78k | 44.0 | 314k | -79k | 23 |
| best stored DAYRULES/WEEKGB cell on CVaR5: DR G3 ST flr=1 HM flr=2 | 2.77M (101%) | 1.19/2.97/3.22/**1.91** | -78k | 39.3 | 364k | -79k | 23 |

## 6. Recommendation

**No cell is robust. The live risk rules stay.** No cell passes walk-forward gain > 0, both null ranks >= 0.95 and the plateau on weekly Sharpe, so there is no recommended cell and no DualStrat change. The pair's live rules are not beaten out of sample by any combination of the 13 axes; the in-sample frontier is selection on a 3.7-year window. Leads worth forward-watching only (zero capital): (i) the week give-back lock (arm 5R, keep 50%) as a single change (the WEEKGB cell GBa arm=5R keep=50%: +0.23 in-sample Sharpe at 101% of live income, clean and H2 up, H1 flat; it beats its matched random-halt null (Sharpe rank 0.99) and WEEKGB already scored this cell NO (list A, null rank 0.42 on max DD); it is one cell of the grid and is not distinguishable from selection noise); (ii) the 6R week floor combined with a 3R day loss floor as tail insurance, at an income cost. Neither is evidence enough to act on.

## 7. What the illustrative cells would have done in each of the last 8 weeks, and DualStrat field values

No cell is recommended, so the blocks below are for information about the two leading candidates only; they are not a proposal. Per-week P&L at 8/8 (6/6 = 0.75x).

**Highest in-sample weekly Sharpe cell (NOT recommended: fails the walk-forward and best-of-N gates; shown so the fields and the last 8 weeks are visible)**: tgt 8/8R flr 1/1.5R cap 12 arm 1R gb80% start 0000 dayflr 3 wkflr 6 pbwk 6 wkGB 5R/keep50% maxtr 10

| ISO week | live W P&L | cell W P&L | cell - live | cell day-lock days | cell blocked-entry days (per-book/trade cap) | cell week lock (floor or give-back) | live day-lock days |
|---|---|---|---|---|---|---|---|
| 202635 | -56,305 | 16,588 | 72,892 | 5 | 5 | no | 3 |
| 202636 | -77,416 | -59,492 | 17,923 | 4 | 5 | yes | 2 |
| 202637 | -36,884 | -15,916 | 20,968 | 4 | 5 | no | 3 |
| 202638 | 116,706 | 41,792 | -74,915 | 4 | 4 | yes | 4 |
| 202639 | 134,077 | 99,565 | -34,513 | 5 | 3 | no | 3 |
| 202640 | -15,630 | 12,758 | 28,388 | 5 | 5 | no | 2 |
| 202641 | -54,750 | -22,496 | 32,254 | 2 | 3 | no | 2 |
| 202642 | 38,045 | 29,323 | -8,722 | 4 | 5 | no | 4 |

202642 by label day (cell vs live):

| label day | live | cell | day lock (cell) | blocked entries (cell) |
|---|---|---|---|---|
| 20261012 | -3,344 | -230 | yes | 7 |
| 20261013 | 10,211 | 5,811 | yes | 9 |
| 20261014 | 7,860 | 890 | yes | 8 |
| 20261015 | 16,436 | 4,071 | yes | 22 |
| 20261016 | 6,881 | 18,780 | - | 16 |

DualStrat field semantics (names to confirm; DualStrat and the Rithmic config were never read). Fields for lock start, week give-back, per-book weekly loss limit and the per-session trade cap are assumed to be additions or already present in the lock panel; availability is NOT verified and is for the operator to confirm.

| field (semantics; names to confirm, DualStrat never read) | 8/8 | 6/6 (0.75x linear) |
|---|---|---|
| per-book daily profit target ST / HM | $76,800 / $76,800 | $57,600 / $57,600 |
| per-book daily loss limit ST / HM | $9,600 / $14,400 | $7,200 / $10,800 |
| combined daily profit cap (R) | 12 | 12 |
| combined give-back lock arm (R) / give-back % | 1 / 80% | 1 / 80% |
| give-back lock active from (ET) | 00:00 | same |
| combined daily loss floor (R) | 3 | 3 |
| combined weekly loss floor (R) | 6 | 6 |
| per-book weekly loss limit | $57,600 | $43,200 |
| combined WEEK give-back: arm R / keep % | 5 / keep 50% | same |
| max trades per book per session | 10 | same |

**Best single change from live: add the combined week give-back lock, arm 5R / keep 50% (+0.23 in-sample Sharpe at 101% of live income; clean and H2 up, H1 flat 2.79 vs 2.83). NOT recommended: see section 6; shown for the same reason**: tgt 5/5R flr 2/2R cap 8 arm 2R gb67% start 0000 dayflr off wkflr 8 pbwk off wkGB 5R/keep50% maxtr off

| ISO week | live W P&L | cell W P&L | cell - live | cell day-lock days | cell blocked-entry days (per-book/trade cap) | cell week lock (floor or give-back) | live day-lock days |
|---|---|---|---|---|---|---|---|
| 202635 | -56,305 | 21,582 | 77,887 | 3 | 5 | yes | 3 |
| 202636 | -77,416 | -77,416 | 0 | 2 | 3 | yes | 2 |
| 202637 | -36,884 | -36,884 | 0 | 3 | 4 | no | 3 |
| 202638 | 116,706 | 36,467 | -80,240 | 4 | 3 | yes | 4 |
| 202639 | 134,077 | 134,077 | 0 | 3 | 3 | no | 3 |
| 202640 | -15,630 | 36,693 | 52,324 | 2 | 4 | yes | 2 |
| 202641 | -54,750 | -54,750 | 0 | 2 | 2 | no | 2 |
| 202642 | 38,045 | 33,239 | -4,806 | 4 | 3 | yes | 4 |

202642 by label day (cell vs live):

| label day | live | cell | day lock (cell) | blocked entries (cell) |
|---|---|---|---|---|
| 20261012 | -3,344 | -3,344 | - | 7 |
| 20261013 | 10,211 | 10,211 | yes | 9 |
| 20261014 | 7,860 | 7,860 | yes | 0 |
| 20261015 | 16,436 | 18,511 | yes | 7 |
| 20261016 | 6,881 | 0 | yes | 0 |

DualStrat field semantics (names to confirm; DualStrat and the Rithmic config were never read). Fields for lock start, week give-back, per-book weekly loss limit and the per-session trade cap are assumed to be additions or already present in the lock panel; availability is NOT verified and is for the operator to confirm.

| field (semantics; names to confirm, DualStrat never read) | 8/8 | 6/6 (0.75x linear) |
|---|---|---|
| per-book daily profit target ST / HM | $48,000 / $48,000 | $36,000 / $36,000 |
| per-book daily loss limit ST / HM | $19,200 / $19,200 | $14,400 / $14,400 |
| combined daily profit cap (R) | 8 | 8 |
| combined give-back lock arm (R) / give-back % | 2 / 67% | 2 / 67% |
| give-back lock active from (ET) | 00:00 | same |
| combined daily loss floor (R) | off | off |
| combined weekly loss floor (R) | 8 | 8 |
| per-book weekly loss limit | off | off |
| combined WEEK give-back: arm R / keep % | 5 / keep 50% | same |
| max trades per book per session | off | same |

## 8. Method notes and limits

- Matched random-halt null: base = PLAIN (no per-book rules, no day lock, week floor 8), random halts at uniformly random grid minutes with the cell's own day-level rate (days with a per-book block, trade-cap block or day lock) and week-level rate (weeks with a week lock); 200 replicates. The best-of-N null draws N=8,109 (day-rate, week-rate) pairs from the library cells' empirical rates per world, 200 worlds; prefix sizes N=16..4,096 are the same worlds truncated.
- The walk-forward chooses from the fixed library (the 6,000-cell search is not re-run per fold; the refinement neighbours were picked using all-in data, which flatters the walk-forward slightly in favour of the searched cells; live still wins).
- Longest DD is in weeks under water on weekly equity; max DD is on daily equity (in-sample) and weekly equity (walk-forward columns). Week = ISO week of the label day.
- Selection among ~8,100 correlated cells inflates the best in-sample cell; the best-of-N null and the walk-forward are the two controls reported. Cells are not independent; read the funnel counts as clusters, not independent successes.
- Files: code/census/night_ins/ap_sm_core.py, ap_sm_grid.py, ap_sm_run.py, ap_sm_validate.py, ap_sm_analyze.py, ap_sm_bestofn.py, ap_sm_report.py; outputs/autopilot/sm/ (lib.npz, analysis.pkl, bestofn.npz, validate_evaluator.json, library_metrics.csv).