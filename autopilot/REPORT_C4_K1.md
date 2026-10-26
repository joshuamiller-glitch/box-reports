# REPORT C4-K1 - let winners run (conditional target extension on the pair)

**Verdict: NO. 0 FOUND, 0 LEAD. The clean-only selection rule selects nothing: all 27 pre-registered cells lose weekly Sharpe and net on clean (best cell: EXT trig +45, target 100, stop kept -60, clean Sharpe 0.90 vs 1.46 live, net 64% of live).** Because nothing was selected, the H1/H2 columns below are shown for transparency only and were not used for any decision; the nulls, bootstrap, plateau and 2x-slippage stages were not run (no candidate exists to test).

Corrected NT8-faithful engine (REPORT_ENGINE_RECON.md), 8/8, 1 tick/side + NT8 commission $34.88, 

**Verdict key.** SURVIVES = (a) H2 net >= +5% and H2 max DD <= -10% vs the baseline row, (b) H1 net >= 90% and H1 DD <= +10%, (c) clean net >= 95% of baseline (matched null pending unless stated). INSURANCE = not SURVIVES, all-in cost >= -5% and one of all-in CVaR5 / worst week +25% or max DD +20% better, with clean and H1 CVaR5 and DD not worse. NO otherwise.

## What was run
- Pre-registered in PREREG_AUTOPILOT.md (cycle 4) before running: trigger = favourable extreme of PREVIOUS seconds reaches +{35,40,45} pts; then the target moves from +60 to {70,80,100} and the stop from -60 to {kept -60, entry, entry+20}: 3 x 3 x 3 = 27 cells + baseline.
- Engine: the C2-G1 / D2-E5 exact 1-second re-simulator (code/census/night_ins/ap_c4_k1_core.py, which copies its conventions: adverse level checked first within a second, stop/target fill at their level, 1 tick/side slippage as live). **Baseline check: the rebuilt baseline row equals the live rows exactly (0 of 13,089 rows differ in points or exit bar) and the account-level daily series equals the original rows' series (max |dx| = 0.0) in both configs.**
- Scope / limitation (same as C2-G1): only the own-bracket rows (7,664 of 13,089 = 59%) can be extended; the 5,425 rows closed by netting, a time block or another lot's order keep their live exit. Extended trades stay open longer than live, so their interaction with later entries (netting, per-book daily/weekly rules, orphan orders) is only modelled through the b11 account pass on the new exit times, not through the original FIFO netting. This overstates how freely an extended trade could be held; since the result is negative, the limitation does not change the verdict.
- Live rules re-applied on top (b11_nt8 / d1_core fast pass): per-book 5R/-2R, day lock 8R/2R/67%/0000, combined week floor -8R, per-book week rule off. Baseline B.Cfg(wk_floor=8,wk_loss_pb=None) computed in a clean process; the same cells vs B.Cfg() are in the second table.
- Selection rule (clean only, written to outputs/autopilot/c4/k1/selection.json before looking at H1/H2): clean weekly Sharpe uplift >= +0.10 and clean net >= 95% of live; top 3. Selected: none.

## Table (baseline row first), live config - H1/H2 shown for transparency only
| cell | verdict | clean net | clean Sh | H1 net | H1 Sh | H2 net | H2 Sh | all-in net vs live | all-in worst wk | all-in max DD |
|---|---|---|---|---|---|---|---|---|---|---|
| BASELINE live (reproduces the live rows) | BASELINE | 1,330k | 1.46 | 594k | 2.83 | 761k | 2.30 | +0% | -83k | 280k |
| EXT trig +35, target 70, stop kept -60 | NO | 329k | 0.35 | 815k | 2.79 | 636k | 1.68 | -34% | -82k | 615k |
| EXT trig +35, target 70, stop to entry | NO | -495k | -0.55 | 497k | 2.16 | -230k | -0.72 | -108% | -80k | 614k |
| EXT trig +35, target 70, stop to entry+20 | NO | -1,372k | -1.65 | 76k | 0.33 | -437k | -1.25 | -165% | -83k | 1,762k |
| EXT trig +35, target 80, stop kept -60 | NO | 680k | 0.69 | 515k | 1.96 | 451k | 1.09 | -39% | -82k | 470k |
| EXT trig +35, target 80, stop to entry | NO | -278k | -0.30 | 349k | 1.44 | 325k | 0.88 | -85% | -85k | 531k |
| EXT trig +35, target 80, stop to entry+20 | NO | -1,306k | -1.49 | 229k | 0.93 | -370k | -1.07 | -154% | -82k | 1,475k |
| EXT trig +35, target 100, stop kept -60 | NO | 788k | 0.84 | 237k | 0.99 | 113k | 0.26 | -58% | -85k | 554k |
| EXT trig +35, target 100, stop to entry | NO | -473k | -0.54 | 313k | 1.52 | 25k | 0.06 | -105% | -82k | 624k |
| EXT trig +35, target 100, stop to entry+20 | NO | -1,557k | -1.91 | 18k | 0.08 | -291k | -0.74 | -168% | -83k | 1,938k |
| EXT trig +40, target 70, stop kept -60 | NO | 329k | 0.35 | 812k | 2.78 | 636k | 1.68 | -34% | -82k | 616k |
| EXT trig +40, target 70, stop to entry | NO | -6k | -0.01 | 404k | 1.51 | -79k | -0.22 | -88% | -87k | 543k |
| EXT trig +40, target 70, stop to entry+20 | NO | -765k | -0.93 | 20k | 0.07 | -586k | -1.83 | -150% | -83k | 1,393k |
| EXT trig +40, target 80, stop kept -60 | NO | 691k | 0.70 | 509k | 1.93 | 451k | 1.09 | -39% | -82k | 470k |
| EXT trig +40, target 80, stop to entry | NO | 103k | 0.11 | 303k | 1.24 | 304k | 0.83 | -74% | -85k | 494k |
| EXT trig +40, target 80, stop to entry+20 | NO | -799k | -0.91 | 176k | 0.63 | -397k | -1.26 | -138% | -82k | 1,080k |
| EXT trig +40, target 100, stop kept -60 | NO | 790k | 0.85 | 237k | 0.99 | 113k | 0.26 | -58% | -85k | 554k |
| EXT trig +40, target 100, stop to entry | NO | -41k | -0.05 | 197k | 0.88 | -64k | -0.18 | -97% | -82k | 473k |
| EXT trig +40, target 100, stop to entry+20 | NO | -1,071k | -1.34 | -241k | -0.95 | -262k | -0.78 | -159% | -83k | 1,674k |
| EXT trig +45, target 70, stop kept -60 | NO | 324k | 0.35 | 810k | 2.77 | 541k | 1.40 | -38% | -82k | 616k |
| EXT trig +45, target 70, stop to entry | NO | 391k | 0.43 | 564k | 2.23 | 74k | 0.19 | -62% | -87k | 512k |
| EXT trig +45, target 70, stop to entry+20 | NO | -90k | -0.11 | 470k | 1.82 | -250k | -0.66 | -95% | -83k | 558k |
| EXT trig +45, target 80, stop kept -60 | NO | 735k | 0.75 | 507k | 1.93 | 442k | 1.07 | -37% | -82k | 470k |
| EXT trig +45, target 80, stop to entry | NO | 383k | 0.42 | 397k | 1.62 | 415k | 1.12 | -56% | -85k | 466k |
| EXT trig +45, target 80, stop to entry+20 | NO | -223k | -0.24 | 533k | 2.03 | -227k | -0.63 | -97% | -82k | 640k |
| EXT trig +45, target 100, stop kept -60 | NO | 849k | 0.90 | 231k | 0.97 | 113k | 0.26 | -56% | -85k | 551k |
| EXT trig +45, target 100, stop to entry | NO | 319k | 0.37 | 313k | 1.42 | 9k | 0.02 | -76% | -82k | 407k |
| EXT trig +45, target 100, stop to entry+20 | NO | -197k | -0.24 | 338k | 1.37 | -175k | -0.46 | -101% | -83k | 489k |

## Same cells against B.Cfg() (robustness): net change vs that baseline, by span
| cell | verdict | clean net | H1 net | H2 net | all-in net |
|---|---|---|---|---|---|
| BASELINE live (reproduces the live rows) | BASELINE | +0% | +0% | +0% | +0% |
| EXT trig +35, target 70, stop kept -60 | NO | -40% | +70% | -30% | -18% |
| EXT trig +35, target 70, stop to entry | NO | -132% | -7% | -99% | -100% |
| EXT trig +35, target 70, stop to entry+20 | NO | -211% | -88% | -117% | -161% |
| EXT trig +35, target 80, stop kept -60 | NO | -21% | -15% | -35% | -25% |
| EXT trig +35, target 80, stop to entry | NO | -106% | -41% | -30% | -71% |
| EXT trig +35, target 80, stop to entry+20 | NO | -219% | -59% | -121% | -160% |
| EXT trig +35, target 100, stop kept -60 | NO | -32% | -57% | -87% | -53% |
| EXT trig +35, target 100, stop to entry | NO | -116% | -37% | -69% | -87% |
| EXT trig +35, target 100, stop to entry+20 | NO | -215% | -104% | -90% | -157% |
| EXT trig +40, target 70, stop kept -60 | NO | -40% | +69% | -30% | -18% |
| EXT trig +40, target 70, stop to entry | NO | -93% | -40% | -95% | -84% |
| EXT trig +40, target 70, stop to entry+20 | NO | -144% | -94% | -170% | -143% |
| EXT trig +40, target 80, stop kept -60 | NO | -21% | -17% | -35% | -24% |
| EXT trig +40, target 80, stop to entry | NO | -73% | -60% | -52% | -64% |
| EXT trig +40, target 80, stop to entry+20 | NO | -173% | -62% | -152% | -147% |
| EXT trig +40, target 100, stop kept -60 | NO | -28% | -57% | -87% | -51% |
| EXT trig +40, target 100, stop to entry | NO | -79% | -60% | -78% | -76% |
| EXT trig +40, target 100, stop to entry+20 | NO | -171% | -135% | -108% | -145% |
| EXT trig +45, target 70, stop kept -60 | NO | -40% | +69% | -29% | -18% |
| EXT trig +45, target 70, stop to entry | NO | -66% | -11% | -72% | -58% |
| EXT trig +45, target 70, stop to entry+20 | NO | -100% | -13% | -114% | -89% |
| EXT trig +45, target 80, stop kept -60 | NO | -17% | -17% | -36% | -23% |
| EXT trig +45, target 80, stop to entry | NO | -53% | -29% | -43% | -46% |
| EXT trig +45, target 80, stop to entry+20 | NO | -125% | +6% | -120% | -101% |
| EXT trig +45, target 100, stop kept -60 | NO | -27% | -59% | -87% | -51% |
| EXT trig +45, target 100, stop to entry | NO | -46% | -32% | -68% | -50% |
| EXT trig +45, target 100, stop to entry+20 | NO | -116% | -28% | -116% | -101% |

## Clean-only table (the only table the selection used)
| cell | clean net | clean Sharpe | vs live | net / live |
|---|---|---|---|---|
| EXT trig +45, target 100, stop kept -60 | 849k | 0.90 | -0.56 | 64% |
| EXT trig +40, target 100, stop kept -60 | 790k | 0.85 | -0.61 | 59% |
| EXT trig +35, target 100, stop kept -60 | 788k | 0.84 | -0.62 | 59% |
| EXT trig +45, target 80, stop kept -60 | 735k | 0.75 | -0.71 | 55% |
| EXT trig +40, target 80, stop kept -60 | 691k | 0.70 | -0.76 | 52% |
| EXT trig +35, target 80, stop kept -60 | 680k | 0.69 | -0.77 | 51% |
| EXT trig +45, target 70, stop to entry | 391k | 0.43 | -1.03 | 29% |
| EXT trig +45, target 80, stop to entry | 383k | 0.42 | -1.04 | 29% |
| EXT trig +45, target 100, stop to entry | 319k | 0.37 | -1.09 | 24% |
| EXT trig +35, target 70, stop kept -60 | 329k | 0.35 | -1.11 | 25% |
| EXT trig +40, target 70, stop kept -60 | 329k | 0.35 | -1.11 | 25% |
| EXT trig +45, target 70, stop kept -60 | 324k | 0.35 | -1.11 | 24% |

## Why: touching +35..+45 is not enough information
Rows whose outcome changed (the trades that touched the trigger and no longer end at the live +60), points per trade, live vs extended:
| cell | rows changed | live mean pts | extended mean pts | total pts change | ended at extended target | ended at -60 / raised stop | ended at flatten |
|---|---|---|---|---|---|---|---|
| EXT trig +35, target 70, stop kept -60 | 4833 | +60.0 | +60.3 | +1,320 | 4418 | 321 | 94 |
| EXT trig +35, target 70, stop to entry | 5454 | +46.3 | +41.7 | -25,253 | 3235 | 2194 | 25 |
| EXT trig +35, target 70, stop to entry+20 | 5454 | +46.3 | +37.6 | -47,780 | 1912 | 3533 | 9 |
| EXT trig +35, target 80, stop kept -60 | 4833 | +60.0 | +61.0 | +4,833 | 4071 | 578 | 184 |
| EXT trig +35, target 80, stop to entry | 5454 | +46.3 | +42.1 | -23,362 | 2836 | 2564 | 54 |
| EXT trig +35, target 80, stop to entry+20 | 5454 | +46.3 | +37.5 | -48,122 | 1582 | 3852 | 20 |
| EXT trig +35, target 100, stop kept -60 | 4832 | +60.0 | +61.1 | +5,371 | 3461 | 1022 | 350 |
| EXT trig +35, target 100, stop to entry | 5453 | +46.3 | +42.3 | -21,786 | 2249 | 3091 | 114 |
| EXT trig +35, target 100, stop to entry+20 | 5454 | +46.3 | +37.5 | -48,302 | 1172 | 4238 | 44 |
| EXT trig +40, target 70, stop kept -60 | 4820 | +60.0 | +60.3 | +1,450 | 4407 | 319 | 94 |
| EXT trig +40, target 70, stop to entry | 5288 | +49.4 | +46.1 | -17,572 | 3464 | 1798 | 26 |
| EXT trig +40, target 70, stop to entry+20 | 5288 | +49.4 | +42.5 | -36,617 | 2367 | 2907 | 14 |
| EXT trig +40, target 80, stop kept -60 | 4820 | +60.0 | +61.0 | +4,993 | 4061 | 575 | 184 |
| EXT trig +40, target 80, stop to entry | 5288 | +49.4 | +46.3 | -16,053 | 3030 | 2201 | 57 |
| EXT trig +40, target 80, stop to entry+20 | 5288 | +49.4 | +42.5 | -36,362 | 1968 | 3290 | 30 |
| EXT trig +40, target 100, stop kept -60 | 4819 | +60.0 | +61.2 | +5,701 | 3454 | 1017 | 349 |
| EXT trig +40, target 100, stop to entry | 5287 | +49.4 | +46.6 | -14,444 | 2404 | 2766 | 118 |
| EXT trig +40, target 100, stop to entry+20 | 5288 | +49.4 | +42.5 | -36,132 | 1464 | 3766 | 58 |
| EXT trig +45, target 70, stop kept -60 | 4791 | +60.0 | +60.3 | +1,550 | 4381 | 316 | 94 |
| EXT trig +45, target 70, stop to entry | 5120 | +52.3 | +50.0 | -11,522 | 3642 | 1448 | 30 |
| EXT trig +45, target 70, stop to entry+20 | 5120 | +52.3 | +47.3 | -25,769 | 2781 | 2320 | 19 |
| EXT trig +45, target 80, stop kept -60 | 4791 | +60.0 | +61.0 | +4,973 | 4036 | 571 | 184 |
| EXT trig +45, target 80, stop to entry | 5120 | +52.3 | +50.3 | -10,368 | 3178 | 1876 | 66 |
| EXT trig +45, target 80, stop to entry+20 | 5120 | +52.3 | +47.3 | -25,745 | 2307 | 2775 | 38 |
| EXT trig +45, target 100, stop kept -60 | 4790 | +60.0 | +61.2 | +5,550 | 3432 | 1011 | 348 |
| EXT trig +45, target 100, stop to entry | 5119 | +52.3 | +50.8 | -7,368 | 2534 | 2455 | 131 |
| EXT trig +45, target 100, stop to entry+20 | 5120 | +52.3 | +47.6 | -23,805 | 1735 | 3311 | 74 |

Measured, not assumed:
- **Stop raised to entry or entry+20 is destructive in every configuration** (18 of 27 cells), also with locks off (per-book-rules-only clean Sharpe -2 to +0.55 vs 1.13; the same finding as C2-G1: the banked +60 is worth more than the pullbacks the raised stop cuts).
- **Stop kept at -60 (9 cells): the extension is roughly neutral-to-positive at the trade level and clearly positive without the day lock, but the live day lock turns it negative.** With the live day lock and week floor, clean net falls 36%-75% and clean Sharpe to 0.35-0.90; with only the per-book daily rule (the lock off) the same rows give clean net +16% to +49% and clean Sharpe 1.21-1.36 vs 1.13. The number of day-lock days rises from 392 to 430-511 on clean. Mechanism: extended winners are held open, their open profit swings, and the combined give-back lock (arm 2R, keep 33%) fires on the retracements and flattens both books at the next open, giving back what the extension gained. The live lock was fitted to a book whose winners are banked at +60 within minutes.
- Table (stop-kept cells; diagnostic only, not a scored result; `diag_locks_off.csv` has all 28 cells and all spans):

| cell | live rules: clean net / Sharpe / lock days | per-book rules only (no day lock, no week floor): clean net / Sharpe | per-book-only all-in net vs its baseline |
|---|---|---|---|
| BASELINE | 1,330k / 1.46 / 392 | 1,266k / 1.13 | +0% |
| EXT trig +35, target 70, stop kept -60 | 329k / 0.35 / 430 | 1,464k / 1.23 | +11% |
| EXT trig +35, target 80, stop kept -60 | 680k / 0.69 / 458 | 1,851k / 1.44 | +11% |
| EXT trig +35, target 100, stop kept -60 | 788k / 0.84 / 510 | 1,895k / 1.34 | +19% |
| EXT trig +40, target 70, stop kept -60 | 329k / 0.35 / 430 | 1,453k / 1.22 | +12% |
| EXT trig +40, target 80, stop kept -60 | 691k / 0.70 / 457 | 1,811k / 1.42 | +11% |
| EXT trig +40, target 100, stop kept -60 | 790k / 0.85 / 511 | 1,927k / 1.36 | +21% |
| EXT trig +45, target 70, stop kept -60 | 324k / 0.35 / 430 | 1,443k / 1.21 | +12% |
| EXT trig +45, target 80, stop kept -60 | 735k / 0.75 / 456 | 1,807k / 1.42 | +13% |
| EXT trig +45, target 100, stop kept -60 | 849k / 0.90 / 511 | 1,884k / 1.34 | +19% |

- Caveat on the lock-off numbers: they are an UPPER bound. The extended trades are held to their own target/stop/flatten with no FIFO netting against later opposite entries (limitation above), so real extended trades would sometimes be closed early at the entry-bar open, and they also change which later entries the per-book rules allow.

## Gates
Not reached: no cell passes the clean-only selection (gate 2), so there is nothing to test for the circular-shift/random-trigger/path-destroyed nulls, bootstrap, rolling Sharpe, plateau or 2x slippage. The pre-registered stages for a selected cell stay available in ap_c4_k1_run.py (stage1 grid, select).

## Follow-up suggestion (for the lead; NOT scored here, needs its own pre-registration)
The extension (stop kept -60, trigger +40..+45, target 100) is worth about +50% net on raw trades with locks off but loses to the live day lock. The only way it could be a find is jointly with a re-tuned lock (arm/give-back/cap), which is a different family: it must be pre-registered, selected on clean only, and judged against the live baseline including the lock. Because both the day lock and the extension were chosen/tested on the same 3.2 years, the joint search has real overfitting risk; D1/D2 E8 (adaptive thresholds) already found lock re-tuning alone does not survive. Prior: 5%.

## Implementability
Not applicable (nothing to implement). For reference, a conditional bracket modification (move the target and stop after a profit trigger) is a small code change in DualStrat (an OnBarUpdate/OnExecution handler that calls the order-modify on the live target and stop once Position profit >= trigger), not a pure parameter change.

## Fill model / slippage
1-second bars, adverse-first within a second, stop and target fills at their level (no gaps), 1 tick/side + NT8 commission $34.88 per trade (live). Live-fills calibration still not available.

Runtime: grid 11 s on 5 workers (28 cells x 2 configs), baseline verification < 2 s; selection < 1 s.

DONE C4_K1
