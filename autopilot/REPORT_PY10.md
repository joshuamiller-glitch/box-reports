# REPORT PY10 - OVERNIGHT-GAP TILT WITH REGIME-FLIPPED SIGN (PX26 cure; D06 x M4/M8, H4)
**Verdict: NO. FOUND 0. Selected L10_L0.25 (clean-only among 4 cells): weekly Sharpe uplift +0.02 clean / +0.31 H1 / -0.16 H2 (needed +0.10 each); all-in +0.01; vs flat-size control +0.02/+0.31/-0.16; bootstrap 90% CI all-in [-0.24, +0.27]; own null clean rank 0.79 (p95 +0.14); selection-corrected null clean rank 0.70 (p95 +0.16), all-in rank 0.57; plateau 0.25 of 4; 2x slip +0.06/+0.01/-0.19; H0 +0.02; failed: g1, g2, g3, g3b, g4, g5, g6, g7, g8, g9.** Pre-registered in PREREG_AUTOPILOT.md block 'PY7-PY10' before the first run.

## Disclosure (binding)
ALIGN was read on clean/H1/H2/alt-month in PX26 (parent NO): non-virgin. The regime score is new (no P&L read before). Maximum status is FOUND-PENDING; newest live weeks (after 2026-10-13) do not exist yet; pre-2023 not testable (pair rows start 2023-02-10; ERA FLAG n/a).

## Mechanism and design
PX26 ALIGN tilt was positive clean and weak in H1/H2 but flipped sign across alternating months. Regime = mean over previous L sessions of gap/ADR x RTH open-to-close move/ADR (gap continuation score); sgn>0 keep PX26 sign (aligned-with-gap entries up, counter-gap entries down), sgn<0 flip. m = (1 + lam*sgn*tercile(ALIGN)) renormalised to mean 1. Controls UNFLIPPED and INVERTED; gate: flipped beats unflipped on clean.
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) via ROWS_corrected_engine in a clean process (baseline reproduced 1.46 / 2.83 / 2.30, all-in 1.86). Fill: 1 tick/side + $34.88 per 8 lots; 2x slippage = SLIP_PT 1.0 on baseline and variant. Multiplier applied through B.Cfg.sizefn (whole contracts rounded by the engine). Features use only bars closed before the entry bar or earlier sessions; edges/terciles/CDFs frozen on clean entries.
- Nulls: (3) own block null = 100 joint within (book, year, ET-hour) permutations of the state, cell rebuilt with re-derived frozen edges (PY9: random afternoon break on the same fired days, same action and scope); (3b) selection-corrected null = 40 worlds, the whole 4-cell grid re-run per world, best-clean cell carried, statistic = its uplift (its clean mean -0.04, all-in mean -0.01). Flat-size control: constant multiplier 1.000 on every trade (the carried cell's mean multiplier).

## All cells (weekly-Sharpe uplift vs baseline; clean is the only selection column; H1/H2 of unselected cells shown after selection and unused)
| cell | clean | H1 | H2 | all | mean mult | min-max | share touched |
|---|---|---|---|---|---|---|---|
| L10_L0.25 | +0.02 | +0.31 | -0.16 | +0.01 | 1.000 | 0.75-1.25 | 1.000 |
| L10_L0.5 | -0.08 | +0.31 | -0.40 | -0.10 | 1.000 | 0.50-1.50 | 1.000 |
| L20_L0.25 | -0.24 | +0.18 | -0.13 | -0.15 | 1.000 | 0.75-1.25 | 1.000 |
| L20_L0.5 | -0.43 | +0.36 | -0.48 | -0.33 | 1.000 | 0.50-1.50 | 1.000 |

## Result for the carried cell (weekly Sharpe)
| span | pair | overlay | uplift | flat-size uplift | uplift minus flat | vs B.Cfg() | 2x slip uplift |
|---|---|---|---|---|---|---|---|
| clean | 1.46 | 1.48 | +0.02 | -0.00 | +0.02 | +0.11 | +0.06 |
| H1 | 2.83 | 3.14 | +0.31 | -0.00 | +0.31 | +0.15 | +0.01 |
| H2 | 2.30 | 2.13 | -0.16 | -0.00 | -0.16 | +0.09 | -0.19 |
| all | 1.86 | 1.87 | +0.01 | -0.00 | +0.01 | +0.11 | -0.02 |

## Gate checklist
- g1 uplift >= +0.10 clean/H1/H2: FAIL
- g2 worst week not worse (every span): FAIL
- g3 own block null p95 clean and all-in: FAIL
- g3b selection-corrected null p95 clean and all-in: FAIL
- g4 bootstrap 90% CI of all-in uplift > 0: FAIL
- g5 plateau >= 75%: FAIL
- g6 2x slip uplift >= +0.10 each span: FAIL
- g7 uplift minus flat-size control >= +0.10 clean/H1/H2: FAIL
- g8 flipped beats unflipped on clean: FAIL
- g9 replication legs >= 2 of 4 (H0, alt-month, ES/RTY, newest weeks n/a): 1 (H0+, alt-month-): FAIL
- worst week (cand vs pair, k$): clean -81.9 vs -81.9, H1 -77.8 vs -78.3, H2 -82.1 vs -82.5, all -82.1 vs -82.5
- own null (rank/p95): clean 0.79/+0.14, H1 0.75/+0.65, H2 0.10/+0.26, all 0.64/+0.16
- selection-corrected null (rank/p95): clean 0.70/+0.16, H1 0.70/+0.61, H2 0.23/+0.28, all 0.57/+0.16
- plateau neighbours (all-in uplift; need >= 0.01): {'lam x0.75': 0.17, 'lam x1.25': -0.03, 'L8': -0.03, 'L13': -0.02} ; neighbour definitions {'lam x0.75': "{'lam': 0.1875}", 'lam x1.25': "{'lam': 0.3125}", 'L8': "{'L': 8}", 'L13': "{'L': 13}"}
- flat-size control under 2x slippage: {'clean': -0.0, 'H1': -0.0, 'H2': -0.0, 'all': -0.0}
- bootstrap clean CI [-0.31, +0.38]; weekly corr with pair 0.97; worst-week delta all-in +441; worst-decile corr: n/a (overlay on the pair, no hedge claim)
- Reported controls (uplift clean/H1/H2/all): UNFLIPPED +0.06/+0.64/+0.31/+0.21; INVERTED -0.32/+0.17/-0.43/-0.28
- g10 insurance metrics: table below. g11 NT8-codable: see Executability.

## Replication legs (>= 2 of 4 needed for FOUND)
- H0 2023-02-10..07-31 (26 weeks, pair Sharpe 0.67): overlay 0.69, uplift +0.02 -> holds (needs > 0 and >= 50% of clean).
- Alternating months (2023-08..2026-10): carried cell odd-half +0.19, even-half -0.16 ; select-on-odd -> L10_L0.5 (sel +0.25) read even -0.46; select-on-even -> L10_L0.25 (sel -0.16) read odd +0.19 -> fails.
- ES/RTY: not run (features are NQ/ES-state or NQ-stop based; no standalone-book analogue pre-registered). Newest live weeks: none exist yet.

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| clean cand | 1.48 | 2.79 | 4.65 | -79.4k | -78.6k | 298k | -81.9k | 42.9 |
| H1 cand | 3.14 | 7.16 | 4.64 | -77.4k | -60.7k | 139k | -77.8k | 35.7 |
| H2 cand | 2.13 | 4.24 | 3.04 | -80.4k | -78.9k | 243k | -82.1k | 44.4 |
| all cand | 1.87 | 3.62 | 9.29 | -79.5k | -78.5k | 298k | -82.1k | 42.3 |

Insurance flags (INS?, cost%, CVaR5 impr%, worst-week impr%, maxDD impr%): clean (False, 4.3, -0.9, -0.1, -6.5); H1 (False, 8.9, 0.3, 0.6, 8.2); H2 (False, -3.0, 0.9, 0.5, -11.9); all (False, 3.3, -0.3, 0.5, -6.5)

## Executability
NT8: daily state series (gap/ADR20 at the open, previous-session RTH open/close/ADR), clean-frozen ALIGN tercile edges as constants, entry-quantity multiplier in [1-lam,1+lam]/mean. Execution at NinjaTrader Brokerage via Rithmic; no data purchase.

Files: code/census/night_ins/ap_py7_core.py, ap_py7_run.py, ap_py7_doc.py; outputs/autopilot/py10/ (runtime 1605s, pool of 4).

DONE PY10
