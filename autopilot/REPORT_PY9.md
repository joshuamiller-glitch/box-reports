# REPORT PY9 - AFTERNOON WHIPSAW HALT (H11-B x time of day; D00/D06 x M7, H2-H3)
**Verdict: NO. FOUND 0. Selected X20_HALF_NEXT (clean-only among 8 cells): weekly Sharpe uplift +0.05 clean / -0.08 H1 / -0.81 H2 (needed +0.10 each); all-in -0.16; vs flat-size control +0.35/-0.05/-1.06; bootstrap 90% CI all-in [-0.35, +0.01]; own null clean rank 0.65 (p95 +0.07); selection-corrected null clean rank 0.80 (p95 +0.06), all-in rank 0.38; plateau 0.00 of 3; 2x slip +0.03/-0.09/-0.51; H0 +0.00; failed: g1, g3, g3b, g4, g5, g6, g7, g9.** Pre-registered in PREREG_AUTOPILOT.md block 'PY7-PY10' before the first run.

## Disclosure (binding)
Parent H11-B (and its five variants J5W) were read on clean/H1/H2/H0/alt-month; the afternoon-trigger/next-session scope is a new cut but the stop-out observable is the parent one: H1/H2 non-virgin. Maximum status is FOUND-PENDING; newest live weeks (after 2026-10-13) do not exist yet; pre-2023 not testable (pair rows start 2023-02-10; ERA FLAG n/a).

## Mechanism and design
H11-B gained from late-day truncation (a random morning break matched it). Here the trigger is N=2 fast stop-outs whose exit falls 12:00-16:59 ET; halt/halve the rest of the label day (SAME) or also the next label day Globex night and morning before 12:00 (NEXT). Mechanism: a late-day failure cluster marks a range regime that persists into the next session open. Null = random afternoon break on the same fired days, same action and scope (matched truncation).
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) via ROWS_corrected_engine in a clean process (baseline reproduced 1.46 / 2.83 / 2.30, all-in 1.86). Fill: 1 tick/side + $34.88 per 8 lots; 2x slippage = SLIP_PT 1.0 on baseline and variant. Multiplier applied through B.Cfg.sizefn (whole contracts rounded by the engine). Features use only bars closed before the entry bar or earlier sessions; edges/terciles/CDFs frozen on clean entries.
- Nulls: (3) own block null = 100 joint within (book, year, ET-hour) permutations of the state, cell rebuilt with re-derived frozen edges (PY9: random afternoon break on the same fired days, same action and scope); (3b) selection-corrected null = 40 worlds, the whole 8-cell grid re-run per world, best-clean cell carried, statistic = its uplift (its clean mean +0.05, all-in mean -0.16). Flat-size control: constant multiplier 0.963 on every trade (the carried cell's mean multiplier).

## All cells (weekly-Sharpe uplift vs baseline; clean is the only selection column; H1/H2 of unselected cells shown after selection and unused)
| cell | clean | H1 | H2 | all | mean mult | min-max | share touched |
|---|---|---|---|---|---|---|---|
| X10_HALT_SAME | +0.01 | +0.06 | +0.04 | +0.02 | 0.997 | 0.00-1.00 | 0.003 |
| X10_HALT_NEXT | -0.02 | +0.13 | -0.17 | -0.03 | 0.957 | 0.00-1.00 | 0.043 |
| X10_HALF_SAME | +0.00 | +0.02 | +0.00 | +0.01 | 0.998 | 0.50-1.00 | 0.003 |
| X10_HALF_NEXT | -0.01 | +0.07 | -0.14 | -0.03 | 0.981 | 0.50-1.00 | 0.038 |
| X20_HALT_SAME | +0.01 | +0.09 | +0.04 | +0.03 | 0.994 | 0.00-1.00 | 0.006 |
| X20_HALT_NEXT | -0.04 | -0.27 | -0.68 | -0.22 | 0.907 | 0.00-1.00 | 0.093 |
| X20_HALF_SAME | +0.00 | +0.04 | +0.00 | +0.01 | 0.997 | 0.50-1.00 | 0.005 |
| X20_HALF_NEXT | +0.05 | -0.08 | -0.81 | -0.16 | 0.963 | 0.50-1.00 | 0.075 |

## Result for the carried cell (weekly Sharpe)
| span | pair | overlay | uplift | flat-size uplift | uplift minus flat | vs B.Cfg() | 2x slip uplift |
|---|---|---|---|---|---|---|---|
| clean | 1.46 | 1.51 | +0.05 | -0.29 | +0.35 | +0.09 | +0.03 |
| H1 | 2.83 | 2.75 | -0.08 | -0.03 | -0.05 | +0.24 | -0.09 |
| H2 | 2.30 | 1.49 | -0.81 | +0.25 | -1.06 | -0.70 | -0.51 |
| all | 1.86 | 1.69 | -0.16 | -0.14 | -0.02 | -0.06 | -0.12 |

## Gate checklist
- g1 uplift >= +0.10 clean/H1/H2: FAIL
- g2 worst week not worse (every span): PASS
- g3 own block null p95 clean and all-in: FAIL
- g3b selection-corrected null p95 clean and all-in: FAIL
- g4 bootstrap 90% CI of all-in uplift > 0: FAIL
- g5 plateau >= 75%: FAIL
- g6 2x slip uplift >= +0.10 each span: FAIL
- g7 uplift minus flat-size control >= +0.10 clean/H1/H2: FAIL
- g8 >= 20 fired days (carried 45); truncation control = g3/g3b: PASS
- g9 replication legs >= 2 of 4 (H0, alt-month, ES/RTY, newest weeks n/a): 0 (H0-, alt-month-): FAIL
- worst week (cand vs pair, k$): clean -81.9 vs -81.9, H1 -78.3 vs -78.3, H2 -82.5 vs -82.5, all -82.5 vs -82.5
- own null (rank/p95): clean 0.65/+0.07, H1 0.69/-0.03, H2 0.06/-0.74, all 0.42/-0.15
- selection-corrected null (rank/p95): clean 0.80/+0.06, H1 0.62/-0.04, H2 0.12/-0.73, all 0.38/-0.14
- plateau neighbours (all-in uplift; need >= -0.12): {'N+1': -0.02, 'X x0.75': -0.04, 'X x1.25': -0.18} ; neighbour definitions {'N+1': "('p', 3, 20, 'HALF', 'NEXT')", 'X x0.75': "('p', 2, 15.0, 'HALF', 'NEXT')", 'X x1.25': "('p', 2, 25.0, 'HALF', 'NEXT')"}
- flat-size control under 2x slippage: {'clean': -0.06, 'H1': -0.08, 'H2': -0.03, 'all': -0.06}
- bootstrap clean CI [-0.11, +0.24]; weekly corr with pair 0.98; worst-week delta all-in +0; worst-decile corr: n/a (overlay on the pair, no hedge claim)
- Reported controls (uplift clean/H1/H2/all): SAME_scope +0.00/+0.04/+0.00/+0.01
- g10 insurance metrics: table below. g11 NT8-codable: see Executability.

## Replication legs (>= 2 of 4 needed for FOUND)
- H0 2023-02-10..07-31 (26 weeks, pair Sharpe 0.67): overlay 0.67, uplift +0.00 -> fails (needs > 0 and >= 50% of clean).
- Alternating months (2023-08..2026-10): carried cell odd-half -0.22, even-half -0.13 ; select-on-odd -> X10_HALT_SAME (sel +0.02) read even +0.03; select-on-even -> X20_HALT_SAME (sel +0.04) read odd +0.01 -> fails.
- ES/RTY: not run (features are NQ/ES-state or NQ-stop based; no standalone-book analogue pre-registered). Newest live weeks: none exist yet.

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| clean cand | 1.51 | 2.81 | 5.63 | -78.7k | -78.0k | 239k | -81.9k | 41.0 |
| H1 cand | 2.75 | 5.83 | 3.67 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 cand | 1.49 | 2.67 | 2.24 | -81.1k | -79.7k | 217k | -82.5k | 52.8 |
| all cand | 1.69 | 3.14 | 10.01 | -79.4k | -78.4k | 239k | -82.5k | 43.5 |

Insurance flags (INS?, cost%, CVaR5 impr%, worst-week impr%, maxDD impr%): clean (False, 0.9, 0.0, 0.0, 14.8); H1 (False, -6.1, 0.0, 0.0, -0.2); H2 (False, -36.0, 0.0, 0.0, 0.0); all (False, -11.1, -0.2, 0.0, 14.8)

## Executability
NT8: DualStrat parameter: count pair stop-outs with hold <= X minutes after 12:00 ET; on N=2 set a halt flag until 17:00 ET (SAME) or until 12:00 ET of the next trading session (NEXT). No margin change. Execution at NinjaTrader Brokerage via Rithmic; no data purchase.

Files: code/census/night_ins/ap_py7_core.py, ap_py7_run.py, ap_py9_run.py, ap_py7_doc.py; outputs/autopilot/py9/ (runtime 2502s, pool of 4).

DONE PY9
