# REPORT PY7 - TWO-FEATURE SHRUNK TILT (overnight gap alignment + NQ/ES 60-min vol ratio; D06/D08 x M4/M8, H2-H4)
**Verdict: NO. FOUND 0. Selected W45_L0.5 (clean-only among 4 cells): weekly Sharpe uplift +0.28 clean / -0.77 H1 / +0.50 H2 (needed +0.10 each); all-in +0.17; vs flat-size control +0.28/-0.77/+0.50; bootstrap 90% CI all-in [-0.27, +0.61]; own null clean rank 0.84 (p95 +0.39); selection-corrected null clean rank 0.88 (p95 +0.35), all-in rank 0.88; plateau 0.50 of 4; 2x slip +0.50/-0.50/+0.11; H0 +0.53; failed: g1, g3, g3b, g4, g5, g6, g7, g9.** Pre-registered in PREREG_AUTOPILOT.md block 'PY7-PY10' before the first run.

## Disclosure (binding)
Both features were read on clean/H1/H2 in PX26 (ALIGN) and PA5/PX1 (vol ratio): every H1/H2 number is non-virgin; their parents were NO. Maximum status is FOUND-PENDING; newest live weeks (after 2026-10-13) do not exist yet; pre-2023 not testable (pair rows start 2023-02-10; ERA FLAG n/a).

## Mechanism and design
Two weak, near-independent entry-state signals each carry the sign pre-registered in its parent (aligned with the overnight gap/ADR up, PX26; high NQ/ES realised-vol ratio down, PA5/PX1). m = (1 + lam*(z_gap+z_vol)/2) renormalised to mean 1, z = clean-frozen empirical-CDF rank in [-1,1] (RTH-only for the gap, 0 elsewhere). Averaging two ranks halves tilt noise; lam caps the size range at +-lam.
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) via ROWS_corrected_engine in a clean process (baseline reproduced 1.46 / 2.83 / 2.30, all-in 1.86). Fill: 1 tick/side + $34.88 per 8 lots; 2x slippage = SLIP_PT 1.0 on baseline and variant. Multiplier applied through B.Cfg.sizefn (whole contracts rounded by the engine). Features use only bars closed before the entry bar or earlier sessions; edges/terciles/CDFs frozen on clean entries.
- Nulls: (3) own block null = 100 joint within (book, year, ET-hour) permutations of the state, cell rebuilt with re-derived frozen edges (PY9: random afternoon break on the same fired days, same action and scope); (3b) selection-corrected null = 40 worlds, the whole 4-cell grid re-run per world, best-clean cell carried, statistic = its uplift (its clean mean +0.07, all-in mean +0.01). Flat-size control: constant multiplier 1.000 on every trade (the carried cell's mean multiplier).

## All cells (weekly-Sharpe uplift vs baseline; clean is the only selection column; H1/H2 of unselected cells shown after selection and unused)
| cell | clean | H1 | H2 | all | mean mult | min-max | share touched |
|---|---|---|---|---|---|---|---|
| W45_L0.25 | -0.11 | -0.42 | +0.29 | -0.07 | 1.000 | 0.77-1.27 | 1.000 |
| W45_L0.5 | +0.28 | -0.77 | +0.50 | +0.17 | 1.000 | 0.53-1.54 | 1.000 |
| W60_L0.25 | -0.05 | -0.04 | +0.52 | +0.08 | 1.000 | 0.77-1.27 | 1.000 |
| W60_L0.5 | +0.11 | -0.05 | +0.25 | +0.12 | 1.000 | 0.54-1.55 | 1.000 |

## Result for the carried cell (weekly Sharpe)
| span | pair | overlay | uplift | flat-size uplift | uplift minus flat | vs B.Cfg() | 2x slip uplift |
|---|---|---|---|---|---|---|---|
| clean | 1.46 | 1.74 | +0.28 | -0.00 | +0.28 | +0.54 | +0.50 |
| H1 | 2.83 | 2.06 | -0.77 | -0.00 | -0.77 | +0.02 | -0.50 |
| H2 | 2.30 | 2.80 | +0.50 | -0.00 | +0.50 | +0.78 | +0.11 |
| all | 1.86 | 2.03 | +0.17 | -0.00 | +0.17 | +0.50 | +0.26 |

## Gate checklist
- g1 uplift >= +0.10 clean/H1/H2: FAIL
- g2 worst week not worse (every span): PASS
- g3 own block null p95 clean and all-in: FAIL
- g3b selection-corrected null p95 clean and all-in: FAIL
- g4 bootstrap 90% CI of all-in uplift > 0: FAIL
- g5 plateau >= 75%: FAIL
- g6 2x slip uplift >= +0.10 each span: FAIL
- g7 uplift minus flat-size control >= +0.10 clean/H1/H2: FAIL
- g8 combination beats gap-only and vol-only on clean (same lam): PASS
- g9 replication legs >= 2 of 4 (H0, alt-month, ES/RTY, newest weeks n/a): 1 (H0+, alt-month-): FAIL
- worst week (cand vs pair, k$): clean -80.3 vs -81.9, H1 -77.4 vs -78.3, H2 -81.8 vs -82.5, all -81.8 vs -82.5
- own null (rank/p95): clean 0.84/+0.39, H1 0.12/+0.80, H2 0.88/+0.74, all 0.79/+0.39
- selection-corrected null (rank/p95): clean 0.88/+0.35, H1 0.15/+0.93, H2 0.95/+0.49, all 0.88/+0.26
- plateau neighbours (all-in uplift; need >= 0.13): {'lam x0.75': 0.08, 'lam x1.25': 0.47, 'W34': 0.1, 'W56': 0.15} ; neighbour definitions {'lam x0.75': "{'lam': 0.375}", 'lam x1.25': "{'lam': 0.625}", 'W34': "{'W': 34}", 'W56': "{'W': 56}"}
- flat-size control under 2x slippage: {'clean': -0.0, 'H1': -0.0, 'H2': -0.0, 'all': -0.0}
- bootstrap clean CI [-0.20, +0.79]; weekly corr with pair 0.89; worst-week delta all-in +695; worst-decile corr: n/a (overlay on the pair, no hedge claim)
- Reported controls (uplift clean/H1/H2/all): GAP_ONLY +0.03/+0.46/+0.29/+0.17; VOL_ONLY -0.17/-0.05/-0.56/-0.23
- g10 insurance metrics: table below. g11 NT8-codable: see Executability.

## Replication legs (>= 2 of 4 needed for FOUND)
- H0 2023-02-10..07-31 (26 weeks, pair Sharpe 0.67): overlay 1.20, uplift +0.53 -> holds (needs > 0 and >= 50% of clean).
- Alternating months (2023-08..2026-10): carried cell odd-half +0.11, even-half +0.21 ; select-on-odd -> W60_L0.5 (sel +0.13) read even +0.09; select-on-even -> W60_L0.25 (sel +0.23) read odd -0.08 -> fails.
- ES/RTY: not run (features are NQ/ES-state or NQ-stop based; no standalone-book analogue pre-registered). Newest live weeks: none exist yet.

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| clean cand | 1.74 | 3.43 | 5.60 | -79.2k | -78.3k | 291k | -80.3k | 40.0 |
| H1 cand | 2.06 | 4.56 | 2.85 | -77.3k | -77.2k | 172k | -77.4k | 35.7 |
| H2 cand | 2.80 | 6.60 | 3.94 | -80.9k | -65.2k | 230k | -81.8k | 41.7 |
| all cand | 2.03 | 4.20 | 10.40 | -79.4k | -78.3k | 291k | -81.8k | 39.9 |

Insurance flags (INS?, cost%, CVaR5 impr%, worst-week impr%, maxDD impr%): clean (False, 22.3, -0.6, 1.9, -3.7); H1 (False, -17.7, 0.4, 1.1, -13.2); H2 (False, 19.1, 0.2, 0.8, -5.8); all (False, 12.5, -0.2, 0.8, -3.7)

## Executability
NT8: ES as a second data series; daily gap/ADR20 state computed at 09:30; rolling sums of squared 1-min log returns of NQ and ES over W bars; clean-frozen CDF tables as constants; entry-quantity multiplier in [1-lam, 1+lam]/mean (sizes round to whole contracts); margin +up to 50% on top-rank entries at lam 0.5. Execution at NinjaTrader Brokerage via Rithmic; no data purchase.

Files: code/census/night_ins/ap_py7_core.py, ap_py7_run.py, ap_py7_doc.py; outputs/autopilot/py7/ (runtime 1745s, pool of 4).

DONE PY7
