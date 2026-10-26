# REPORT PZ4 - MONTH-LEVEL CROSS-INDEX STATE TILT (NQ-RTY dispersion, NQ/ES and RTY/NQ vol ratios; D07 x M4/M8, H5)
**Verdict: NO. FOUND 0. Selected DISP20_N_l0.5 (clean-only among 12 cells): weekly Sharpe uplift +0.09 clean / +0.59 H1 / +0.47 H2 (needed +0.10 each); all-in +0.27; bootstrap 90% CI all-in [-0.28, +0.85]; own null clean rank 0.91 (p95 +0.19); selection-corrected null clean rank 0.40 (p95 +0.41); plateau 0.25 of 4; 2x slip +0.20/+0.68/+0.05; H0 +0.01; ES/RTY all-in +0.05/+0.26; failed: g1, g2, g3, g3b, g4, g5, g6, g7, g9.** Pre-registered in PREREG_AUTOPILOT.md block 'BATCH 8 PZ1-PZ5' before the first scored run.

## Disclosure (binding)
E6 (concentration regime) and PA5/PX1 (60-min NQ/ES vol ratio) are the neighbours; month-level cross-index states are new but H1/H2 are not virgin for the family (vol-ratio and RS tilts H7-A, PA5, PX1 were read). Maximum status is FOUND-PENDING; newest live weeks (after 2026-10-13) do not exist yet; pre-2023 not testable (pair rows start 2023-02-10; ERA FLAG n/a).

## Mechanism and design
States over 20 days known before the entry day: DISP20 = |20-day (rNQ - rRTY)| / (sigma of the daily spread * sqrt 20), VNE20 = ln(sigma20 NQ / sigma20 ES) (NQ-specific stress at a month horizon; PA5/PX1 used 60 minutes), VRN20 = ln(sigma20 RTY / sigma20 NQ). Same continuous mean-1 form, grid (12 cells), neighbours, nulls and controls as PZ1. ES/RTY legs use the instrument own analogue (partners: NQ->RTY,ES; ES->RTY,NQ; RTY->NQ,ES).
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) via ROWS_corrected_engine in a clean process (baseline reproduced 1.46 / 2.83 / 2.30, all-in 1.86; O(N) pass1 ap_pz_fast.py verified bit-identical to the original before use). Pair-change framing (overlay on the pair, constant-risk framing n/a). Fill: 1 tick/side + $34.88 per 8 lots; 2x slippage = SLIP_PT 1.0 on baseline and variant. Features use only data from earlier sessions or closed bars; frozen tables from clean.
- Own null: state series permuted in 20-trading-day blocks, 200 replicates (iid-day permutation reported as secondary). Selection-corrected null: 200 worlds, the whole 12-cell grid re-run per world, best-clean cell carried (its clean mean +0.15, all-in mean -0.04). Secondary nulls (rank/p95 clean, all-in): block20 0.91/+0.19, 0.99/+0.06; iid 0.90/+0.17, 0.99/+0.02. Flat-size control: constant 1.000 on every trade.
- Touched trades of the carried cell: 13089 in the pair window (6175 in clean).

## All cells (weekly-Sharpe uplift vs baseline; clean is the only selection column; H1/H2 of unselected cells shown after selection and unused)
| cell | clean | H1 | H2 | all | mean mult | touched (all) | touched (clean) |
|---|---|---|---|---|---|---|---|
| DISP20_P_l0.25 | -0.26 | +0.03 | -1.12 | -0.43 | 1.000 | 13089 | 6175 |
| DISP20_P_l0.5 | -0.18 | -0.42 | -1.59 | -0.56 | 1.000 | 13089 | 6175 |
| DISP20_N_l0.25 | -0.00 | +1.29 | -0.20 | +0.13 | 1.000 | 13089 | 6175 |
| DISP20_N_l0.5 | +0.09 | +0.59 | +0.47 | +0.27 | 1.000 | 13089 | 6175 |
| VNE20_P_l0.25 | -0.47 | +0.19 | -0.53 | -0.39 | 1.000 | 13089 | 6175 |
| VNE20_P_l0.5 | -0.61 | +0.12 | -0.26 | -0.40 | 1.000 | 13089 | 6175 |
| VNE20_N_l0.25 | -0.09 | -0.43 | +0.22 | -0.06 | 1.000 | 13089 | 6175 |
| VNE20_N_l0.5 | -0.17 | -0.66 | -0.33 | -0.26 | 1.000 | 13089 | 6175 |
| VRN20_P_l0.25 | -0.42 | -0.50 | +0.54 | -0.17 | 1.000 | 13089 | 6175 |
| VRN20_P_l0.5 | -0.27 | -0.31 | +0.25 | -0.11 | 1.000 | 13089 | 6175 |
| VRN20_N_l0.25 | -0.43 | -0.05 | -0.87 | -0.49 | 1.000 | 13089 | 6175 |
| VRN20_N_l0.5 | +0.02 | -0.17 | -0.73 | -0.18 | 1.000 | 13089 | 6175 |

## Result for the carried cell (weekly Sharpe)
| span | pair | overlay | uplift | flat-size uplift | uplift minus flat | vs B.Cfg() | 2x slip uplift |
|---|---|---|---|---|---|---|---|
| clean | 1.46 | 1.55 | +0.09 | +0.00 | +0.09 | +0.18 | +0.20 |
| H1 | 2.83 | 3.42 | +0.59 | +0.00 | +0.59 | +1.83 | +0.68 |
| H2 | 2.30 | 2.76 | +0.47 | +0.00 | +0.47 | -0.40 | +0.05 |
| all | 1.86 | 2.13 | +0.27 | +0.00 | +0.27 | +0.30 | +0.26 |

## Gate checklist
- g1 uplift >= +0.10 clean/H1/H2: FAIL
- g2 worst week not worse (every span): FAIL
- g3 own null p95 clean and all-in (200): FAIL
- g3b selection-corrected null p95 clean and all-in (200 worlds): FAIL
- g4 bootstrap 90% CI of all-in uplift > 0: FAIL
- g5 plateau >= 75%: FAIL
- g6 2x slip uplift >= +0.10 each span: FAIL
- g7 uplift minus flat-size control >= +0.10 clean/H1/H2: FAIL
- g8 carried beats the INVERTED-sign control on clean: PASS
- g9 replication legs >= 2 of 4 (newest weeks n/a): 1 (H0-, alt-month-, ES/RTY+): FAIL
- worst week (cand vs pair, k$): clean -83.0 vs -81.9, H1 -81.5 vs -78.3, H2 -79.6 vs -82.5, all -83.0 vs -82.5
- own null (rank/p95): clean 0.91/+0.19, H1 0.84/+1.26, H2 0.96/+0.39, all 0.99/+0.06
- selection-corrected null (rank/p95): clean 0.40/+0.41, H1 0.84/+0.94, H2 0.95/+0.46, all 0.96/+0.26
- plateau neighbours (all-in uplift; need >= 0.20): {'lam x0.75': 0.36, 'lam x1.25': -0.01, 'W15': 0.05, 'W25': -0.41} ; definitions {'lam x0.75': "{'lam': 0.375}", 'lam x1.25': "{'lam': 0.625}", 'W15': "{'W': 15}", 'W25': "{'W': 25}"}
- bootstrap clean CI [-0.48, +0.70]; weekly corr with pair 0.83; worst-week delta all-in -449; worst-decile corr: n/a (overlay on the pair, no hedge claim)
- Controls (uplift clean/H1/H2/all): FLAT0.9 -0.29/+0.04/-0.09/-0.21; FLAT1.1 -0.22/-0.63/-0.36/-0.30; INVERTED -0.18/-0.42/-1.59/-0.56
- g10 insurance metrics: table below. g11 NT8-codable: see Executability.

## Replication legs (>= 2 of 4 needed for FOUND)
- H0 2023-02-10..07-31 (26 weeks, pair Sharpe 0.67): overlay 0.68, uplift +0.01 -> fails.
- Alternating months (2023-08..2026-10): carried cell odd-half -0.06, even-half +0.60; select-on-odd -> DISP20_N_l0.5 (sel -0.06) read even +0.60; select-on-even -> DISP20_N_l0.5 (sel +0.60) read odd -0.06 -> fails (needs both > 0 and mean >= 50% of all-in).
- ES / RTY standalone ST+HM books (d1_f4_core, ADR20 k=0.75, live account rules, 1 tick/side, own-instrument state, same recipe): ES +0.15/+0.31/-0.47 (all +0.05, modified 2780 of 2780, base all-in -0.75); RTY +0.53/+0.26/-0.61 (all +0.26, modified 2784 of 2784, base all-in -0.41) -> holds; same calendar window as the pair (correlated evidence).
- Newest live weeks: none exist after 2026-10-13; the forward monitor (PZ5) will score them. ERA flag: pair rows start 2023-02, pre-2023 not testable (n/a).

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| clean cand | 1.55 | 2.82 | 5.14 | -80.5k | -79.2k | 268k | -83.0k | 40.0 |
| H1 cand | 3.42 | 7.53 | 5.67 | -79.7k | -78.8k | 139k | -81.5k | 28.6 |
| H2 cand | 2.76 | 5.89 | 4.06 | -79.3k | -78.4k | 219k | -79.6k | 36.1 |
| all cand | 2.13 | 4.11 | 11.38 | -80.4k | -79.1k | 268k | -83.0k | 37.5 |

Insurance flags (INS?, cost%, CVaR5 impr%, worst-week impr%, maxDD impr%): clean (False, 3.7, -2.3, -1.3, 4.2); H1 (False, 33.0, -2.7, -4.1, 8.3); H2 (False, 16.4, 2.2, 3.5, -0.5); all (False, 13.8, -1.4, -0.5, 4.2)

## Executability
NT8: needs ES and RTY daily closes (second/third data series) and NQ; rolling 20-day statistics; clean-frozen CDF tables; entry-quantity multiplier in [1-lam,1+lam]/mean; margin +up to 50% on top-rank entries at lam 0.5. Execution at NinjaTrader Brokerage via Rithmic; no data purchase.

Files: code/census/night_ins/ap_pz_fast.py, ap_pz_core.py, ap_pz1_run.py, ap_pz_xi.py, ap_pz_doc.py; outputs/autopilot/pz4/ (runtime 454s, pool of 5).

DONE PZ4
