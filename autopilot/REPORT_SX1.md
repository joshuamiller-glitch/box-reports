# REPORT SX1 - WEEKLY+ OPTION-STATE SIZE TILT (dealer-gamma panel gex_norm / zgd / skew / term, 10-day mean; D03 x M4/M8, H6)
**Verdict: NO. FOUND 0. Selected O:zgd_N_l0.5 (clean-only among 16 cells): weekly Sharpe uplift +0.22 clean / +0.08 H1 / -1.37 H2 (needed +0.10 each); all-in -0.22; bootstrap 90% CI all-in [-0.74, +0.31]; own null clean rank 0.97 (p95 +0.14); selection-corrected null clean rank 0.76 (p95 +0.38); plateau 0.00 of 4; 2x slip +0.18/-0.28/-1.75; H0 +0.50; ES/RTY all-in +0.29/-0.03; failed: g1, g3, g3b, g4, g5, g6, g7, g9.** Pre-registered in PREREG_AUTOPILOT.md block 'BATCH SX' before the first scored run.

## Disclosure (binding)
H1/H2 of the pair are non-virgin for option-state families (G8-E daily OI state, G8 gamma level). The 10-day smoothed observables are new. Option panel history is 2019-2026 (ES panel used for the ES/RTY cross-check). Maximum status is FOUND-PENDING; newest live weeks (after 2026-10-13) do not exist yet; pre-2023 not testable (pair rows start 2023-02-10; ERA FLAG n/a).

## Mechanism and design
Two-week smoothed state of the NQ option panel (outputs/autopilot/opt/feat_NQ.parquet: normalised dealer gamma, zero-gamma distance, skew, term slope) known at the previous close; z = clean-frozen empirical-CDF rank in [-1,1]; multiplier 1 + sg*lam*z renormalised to mean 1; 16 cells (4 features x 2 signs x lam 0.25/0.5). G8-E tested the daily open-interest state and J-block the daily gamma level; the 10-day smoothed panel state at a two-week horizon is new.
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) via ROWS_corrected_engine in a clean process (baseline reproduced 1.46 / 2.83 / 2.30, all-in 1.86; O(N) pass1 ap_pz_fast.py verified bit-identical to the original before use). Pair-change framing (overlay on the pair, constant-risk framing n/a). Fill: 1 tick/side + $34.88 per 8 lots; 2x slippage = SLIP_PT 1.0 on baseline and variant. Features use only data from earlier sessions or closed bars; frozen tables from clean.
- Own null: state series date-permuted in 20-day blocks (block20) and iid days; same permutation for all features; 200 draws. Selection-corrected null: 200 worlds, the whole 16-cell grid re-run per world, best-clean cell carried (its clean mean +0.15, all-in mean -0.04). Secondary nulls (rank/p95 clean, all-in): block20 0.97/+0.14, 0.75/+0.04; iid 0.95/+0.21, 0.74/+0.06. Flat-size control: constant 1.000 on every trade.
- Touched trades of the carried cell: 13184 in the pair window (6175 in clean).

## All cells (weekly-Sharpe uplift vs baseline; clean is the only selection column; H1/H2 of unselected cells shown after selection and unused)
| cell | clean | H1 | H2 | all | mean mult | touched (all) | touched (clean) |
|---|---|---|---|---|---|---|---|
| O:gex_norm_P_l0.25 | -0.68 | -0.46 | -0.27 | -0.52 | 1.000 | 13184 | 6175 |
| O:gex_norm_P_l0.5 | -0.74 | +0.25 | -0.39 | -0.48 | 1.000 | 13184 | 6175 |
| O:gex_norm_N_l0.25 | -0.10 | -0.06 | -1.09 | -0.34 | 1.000 | 13184 | 6175 |
| O:gex_norm_N_l0.5 | -0.10 | -0.01 | -1.62 | -0.51 | 1.000 | 13184 | 6175 |
| O:zgd_P_l0.25 | -0.59 | -0.28 | -0.41 | -0.46 | 1.000 | 13184 | 6175 |
| O:zgd_P_l0.5 | -0.69 | -0.24 | -0.46 | -0.52 | 1.000 | 13184 | 6175 |
| O:zgd_N_l0.25 | -0.14 | -0.21 | -1.15 | -0.41 | 1.000 | 13184 | 6175 |
| O:zgd_N_l0.5 | +0.22 | +0.08 | -1.37 | -0.22 | 1.000 | 13184 | 6175 |
| O:skew_P_l0.25 | -0.44 | -1.00 | -0.18 | -0.45 | 1.000 | 13184 | 6175 |
| O:skew_P_l0.5 | -0.28 | -1.85 | -1.41 | -0.77 | 1.000 | 13184 | 6175 |
| O:skew_N_l0.25 | -0.48 | +1.06 | +0.08 | -0.16 | 1.000 | 13184 | 6175 |
| O:skew_N_l0.5 | -0.56 | +1.80 | -0.35 | -0.30 | 1.000 | 13184 | 6175 |
| O:term_P_l0.25 | -0.26 | +0.62 | -0.94 | -0.30 | 1.000 | 13184 | 6175 |
| O:term_P_l0.5 | -0.51 | +0.13 | -0.96 | -0.53 | 1.000 | 13184 | 6175 |
| O:term_N_l0.25 | -0.15 | -0.34 | +0.22 | -0.05 | 1.000 | 13184 | 6175 |
| O:term_N_l0.5 | -0.37 | -0.84 | -0.03 | -0.32 | 1.000 | 13184 | 6175 |

## Result for the carried cell (weekly Sharpe)
| span | pair | overlay | uplift | flat-size uplift | uplift minus flat | vs B.Cfg() | 2x slip uplift |
|---|---|---|---|---|---|---|---|
| clean | 1.46 | 1.68 | +0.22 | -0.00 | +0.22 | +0.97 | +0.18 |
| H1 | 2.83 | 2.90 | +0.08 | -0.00 | +0.08 | -0.14 | -0.28 |
| H2 | 2.48 | 1.12 | -1.37 | -0.00 | -1.37 | -1.15 | -1.75 |
| all | 1.90 | 1.68 | -0.22 | -0.00 | -0.22 | +0.28 | -0.38 |

## Gate checklist
- g1 uplift >= +0.10 clean/H1/H2: FAIL
- g2 worst week not worse (every span): PASS
- g3 own null p95 clean and all-in (200): FAIL
- g3b selection-corrected null p95 clean and all-in (200 worlds): FAIL
- g4 bootstrap 90% CI of all-in uplift > 0: FAIL
- g5 plateau >= 75%: FAIL
- g6 2x slip uplift >= +0.10 each span: FAIL
- g7 uplift minus flat-size control >= +0.10 clean/H1/H2: FAIL
- g8 carried beats the INVERTED-sign control on clean: PASS
- g9 replication legs >= 2 of 4 (newest weeks n/a): 1 (H0+, alt-month-, ES/RTY-): FAIL
- worst week (cand vs pair, k$): clean -79.9 vs -81.9, H1 -78.0 vs -78.3, H2 -79.7 vs -82.5, all -79.9 vs -82.5
- own null (rank/p95): clean 0.97/+0.14, H1 0.61/+0.94, H2 0.12/+0.19, all 0.75/+0.04
- selection-corrected null (rank/p95): clean 0.76/+0.38, H1 0.66/+0.97, H2 0.07/+0.43, all 0.19/+0.28
- plateau neighbours (all-in uplift; need >= -0.16): {'W8': -0.55, 'W12': -0.55, 'lam x0.75': -0.21, 'lam x1.25': -0.71} ; definitions {'W8': "{'W': 8}", 'W12': "{'W': 12}", 'lam x0.75': "{'lam': 0.375}", 'lam x1.25': "{'lam': 0.625}"}
- bootstrap clean CI [-0.34, +0.81]; weekly corr with pair 0.85; worst-week delta all-in +2629; worst-decile corr: n/a (overlay on the pair, no hedge claim)
- Controls (uplift clean/H1/H2/all): FLAT0.9 -0.29/+0.04/-0.10/-0.21; FLAT1.1 -0.22/-0.63/-0.38/-0.30; INVERTED -0.69/-0.24/-0.46/-0.52
- g10 insurance metrics: table below. g11 NT8-codable: see Executability.

## Replication legs (>= 2 of 4 needed for FOUND)
- H0 2023-02-10..07-31 (26 weeks, pair Sharpe 0.67): overlay 1.17, uplift +0.50 -> holds.
- Alternating months (2023-08..2026-10): carried cell odd-half -0.38, even-half -0.07; select-on-odd -> O:skew_P_l0.25 (sel +0.03) read even -0.92; select-on-even -> O:skew_N_l0.5 (sel +0.41) read odd -0.97 -> fails (needs both > 0 and mean >= 50% of all-in).
- ES / RTY standalone ST+HM books (d1_f4_core, ADR20 k=0.75, live account rules, 1 tick/side, own-instrument state, same recipe): ES +0.38/-0.08/+0.25 (all +0.29, modified 2791 of 2791, base all-in -0.77); RTY +0.06/-0.31/-0.03 (all -0.03, modified 2795 of 2795, base all-in -0.38) -> fails; same calendar window as the pair (correlated evidence).
- Newest live weeks: none exist after 2026-10-13; the forward monitor (PZ5) will score them. ERA flag: pair rows start 2023-02, pre-2023 not testable (n/a).

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 pair | 2.48 | 5.08 | 3.77 | -81.1k | -79.2k | 217k | -82.5k | 41.7 |
| all pair | 1.90 | 3.71 | 9.79 | -79.2k | -78.2k | 280k | -82.5k | 42.3 |
| clean cand | 1.68 | 3.17 | 5.72 | -78.7k | -78.2k | 266k | -79.9k | 40.0 |
| H1 cand | 2.90 | 6.34 | 3.84 | -60.6k | -53.1k | 133k | -78.0k | 32.1 |
| H2 cand | 1.12 | 2.13 | 1.31 | -79.3k | -78.9k | 313k | -79.7k | 44.4 |
| all cand | 1.68 | 3.21 | 7.80 | -78.9k | -78.4k | 313k | -79.9k | 39.9 |

Insurance flags (INS?, cost%, CVaR5 impr%, worst-week impr%, maxDD impr%): clean (False, 14.4, 0.0, 2.4, 5.0); H1 (False, -14.1, 21.9, 0.4, 12.6); H2 (False, -49.8, 2.2, 3.5, -44.1); all (False, -10.9, 0.4, 3.2, -11.9)

## Executability
NT8: needs the daily option-panel feature (computed offline from OPRA definition/statistics files; nightly file), a 10-day mean and clean-frozen CDF table as constants; entry-quantity multiplier in [1-lam,1+lam]/mean on both books. Execution at NinjaTrader Brokerage via Rithmic; no data purchase.

Files: code/census/night_ins/ap_pz_fast.py, ap_pz_core.py (pipeline2), ap_sx_run.py, ap_sx_state.py, ap_sx_xi.py, ap_sx_doc.py; outputs/autopilot/sx1/ (runtime 442s, pool of 5).

DONE SX1
