# REPORT PZ3 - PARTNER OPEN-P&L STATE AT ENTRY (underwater throttle / in-profit pyramid; D00 x M4/M7, H1-H2)
**Verdict: NO. FOUND 0. Selected UW0.2_HALF (clean-only among 6 cells): weekly Sharpe uplift -0.12 clean / +0.78 H1 / +0.21 H2 (needed +0.10 each); all-in +0.09; bootstrap 90% CI all-in [-0.03, +0.24]; own null clean rank 0.31 (p95 +0.10); selection-corrected null clean rank 0.04 (p95 +0.29); plateau 0.50 of 4; 2x slip +0.03/+0.79/+0.20; H0 -0.03; ES/RTY all-in +0.04/-0.01; failed: g1, g2, g3, g3b, g4, g5, g6, g7, g9.** Pre-registered in PREREG_AUTOPILOT.md block 'BATCH 8 PZ1-PZ5' before the first scored run.

## Disclosure (binding)
H0a priced stacking by direction only (a in {0,0.5,1.5}); K26 blocks on combined open risk. The partner mark-to-market state is new; H1/H2 non-virgin for the stacking family. Maximum status is FOUND-PENDING; newest live weeks (after 2026-10-13) do not exist yet; pre-2023 not testable (pair rows start 2023-02-10; ERA FLAG n/a).

## Mechanism and design
Same-direction stacked entries (other book open) split by the partner mark-to-market at the entry bar: underwater <= -theta R (adding risk to a losing pair) -> skip/halve; in profit >= +theta R -> pyramid x1.5. UW theta {0.1,0.2} R x {SKIP,HALF}, PP theta {0.25,0.5} R x 1.5 (6 cells; UW thetas amended before the run for counts, PZ AMENDMENT 1). Control STACK_ALL applies the same multiplier to every stacked entry regardless of the partner state. Null: partner P&L values permuted among stacked rows.
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) via ROWS_corrected_engine in a clean process (baseline reproduced 1.46 / 2.83 / 2.30, all-in 1.86; O(N) pass1 ap_pz_fast.py verified bit-identical to the original before use). Pair-change framing (overlay on the pair, constant-risk framing n/a). Fill: 1 tick/side + $34.88 per 8 lots; 2x slippage = SLIP_PT 1.0 on baseline and variant. Features use only data from earlier sessions or closed bars; frozen tables from clean.
- Own null: partner-P&L permutation among stacked rows, 200 replicates. Selection-corrected null: 200 worlds, the whole 6-cell grid re-run per world, best-clean cell carried (its clean mean +0.09, all-in mean +0.04). Secondary nulls (rank/p95 clean, all-in): permstate 0.31/+0.10, 0.89/+0.12. Flat-size control: constant 0.995 on every trade.
- Touched trades of the carried cell: 136 in the pair window (77 in clean).

## All cells (weekly-Sharpe uplift vs baseline; clean is the only selection column; H1/H2 of unselected cells shown after selection and unused)
| cell | clean | H1 | H2 | all | mean mult | touched (all) | touched (clean) |
|---|---|---|---|---|---|---|---|
| UW0.1_SKIP | -0.31 | +1.20 | +0.14 | -0.01 | 0.980 | 260 | 139 |
| UW0.1_HALF | -0.21 | +0.87 | +0.11 | +0.02 | 0.990 | 260 | 139 |
| UW0.2_SKIP | -0.12 | +0.85 | +0.23 | +0.11 | 0.990 | 136 | 77 |
| UW0.2_HALF | -0.12 | +0.78 | +0.21 | +0.09 | 0.995 | 136 | 77 |
| PP0.25_x1.5 | -0.51 | +0.07 | -0.02 | -0.30 | 1.033 | 875 | 452 |
| PP0.5_x1.5 | -0.29 | +0.09 | -0.20 | -0.21 | 1.015 | 394 | 193 |

## Result for the carried cell (weekly Sharpe)
| span | pair | overlay | uplift | flat-size uplift | uplift minus flat | vs B.Cfg() | 2x slip uplift |
|---|---|---|---|---|---|---|---|
| clean | 1.46 | 1.34 | -0.12 | -0.13 | +0.02 | -0.11 | +0.03 |
| H1 | 2.83 | 3.61 | +0.78 | +0.06 | +0.72 | +0.41 | +0.79 |
| H2 | 2.30 | 2.50 | +0.21 | +0.13 | +0.07 | +0.34 | +0.20 |
| all | 1.86 | 1.95 | +0.09 | -0.05 | +0.14 | +0.08 | +0.19 |

## Gate checklist
- g1 uplift >= +0.10 clean/H1/H2: FAIL
- g2 worst week not worse (every span): FAIL
- g3 own null p95 clean and all-in (200): FAIL
- g3b selection-corrected null p95 clean and all-in (200 worlds): FAIL
- g4 bootstrap 90% CI of all-in uplift > 0: FAIL
- g5 plateau >= 75%: FAIL
- g6 2x slip uplift >= +0.10 each span: FAIL
- g7 uplift minus flat-size control >= +0.10 clean/H1/H2: FAIL
- g8 carried beats STACK_ALL (same multiplier on every stacked entry) on clean: PASS
- g9 replication legs >= 2 of 4 (newest weeks n/a): 0 (H0-, alt-month-, ES/RTY-): FAIL
- worst week (cand vs pair, k$): clean -83.5 vs -81.9, H1 -78.4 vs -78.3, H2 -81.1 vs -82.5, all -83.5 vs -82.5
- own null (rank/p95): clean 0.31/+0.10, H1 1.00/+0.41, H2 0.74/+0.45, all 0.89/+0.12
- selection-corrected null (rank/p95): clean 0.04/+0.29, H1 0.99/+0.55, H2 0.79/+0.53, all 0.67/+0.25
- plateau neighbours (all-in uplift; need >= 0.07): {'th x0.75': 0.01, 'th x1.25': 0.01, 'dev x0.75': 0.08, 'dev x1.25': 0.08} ; definitions {'th x0.75': "{'th': 0.15000000000000002}", 'th x1.25': "{'th': 0.25}", 'dev x0.75': "{'dev': 0.75}", 'dev x1.25': "{'dev': 1.25}"}
- bootstrap clean CI [-0.23, -0.02]; weekly corr with pair 0.99; worst-week delta all-in -971; worst-decile corr: n/a (overlay on the pair, no hedge claim)
- Controls (uplift clean/H1/H2/all): STACK_ALL_same_m -0.26/+0.37/+0.38/+0.03
- g10 insurance metrics: table below. g11 NT8-codable: see Executability.

## Replication legs (>= 2 of 4 needed for FOUND)
- H0 2023-02-10..07-31 (26 weeks, pair Sharpe 0.67): overlay 0.64, uplift -0.03 -> fails.
- Alternating months (2023-08..2026-10): carried cell odd-half -0.13, even-half +0.32; select-on-odd -> PP0.5_x1.5 (sel -0.09) read even -0.33; select-on-even -> UW0.2_SKIP (sel +0.39) read odd -0.17 -> fails (needs both > 0 and mean >= 50% of all-in).
- ES / RTY standalone ST+HM books (d1_f4_core, ADR20 k=0.75, live account rules, 1 tick/side, own-instrument state, same recipe): ES +0.04/+0.08/+0.03 (all +0.04, modified 18 of 2780, base all-in -0.75); RTY +0.02/-0.02/-0.09 (all -0.01, modified 28 of 2784, base all-in -0.41) -> fails; same calendar window as the pair (correlated evidence).
- Newest live weeks: none exist after 2026-10-13; the forward monitor (PZ5) will score them. ERA flag: pair rows start 2023-02, pre-2023 not testable (n/a).

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| clean cand | 1.34 | 2.52 | 4.29 | -79.3k | -78.3k | 282k | -83.5k | 44.8 |
| H1 cand | 3.61 | 8.20 | 5.15 | -78.0k | -66.3k | 152k | -78.4k | 35.7 |
| H2 cand | 2.50 | 5.08 | 3.78 | -80.4k | -79.0k | 216k | -81.1k | 38.9 |
| all cand | 1.95 | 3.81 | 9.98 | -79.5k | -78.4k | 282k | -83.5k | 42.3 |

Insurance flags (INS?, cost%, CVaR5 impr%, worst-week impr%, maxDD impr%): clean (False, -9.1, -0.7, -2.0, -0.5); H1 (False, 31.6, -0.5, -0.2, -0.0); H2 (False, 7.5, 0.9, 1.7, 0.5); all (False, 4.6, -0.4, -1.2, -0.5)

## Executability
NT8: at order submission read the other book position and average price, compute the mark in points / 60; scale quantity (0 / 50% / 150%). Pyramid raises peak contracts by 50% on flagged entries. Execution at NinjaTrader Brokerage via Rithmic; no data purchase.

Files: code/census/night_ins/ap_pz_fast.py, ap_pz_core.py, ap_pz3_run.py, ap_pz_xi.py, ap_pz_doc.py; outputs/autopilot/pz3/ (runtime 222s, pool of 5).

DONE PZ3
