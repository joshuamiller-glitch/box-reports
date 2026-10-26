# REPORT SX3 - STATE-TAIL HALF-SIZE RULE (option-panel and cross-asset states, top or bottom clean tercile -> x0.5; D03/D07 x M7, H6)
**Verdict: NO. FOUND 0. Selected X:CL_V_1 (clean-only among 24 cells): weekly Sharpe uplift +0.09 clean / -0.17 H1 / -0.90 H2 (needed +0.10 each); all-in -0.14; bootstrap 90% CI all-in [-0.66, +0.37]; own null clean rank 0.95 (p95 +0.09); selection-corrected null clean rank 0.24 (p95 +0.42); plateau 0.00 of 2; 2x slip +0.26/-0.32/-1.09; H0 -0.22; ES/RTY all-in +0.00/+0.01; failed: g1, g2, g3, g3b, g4, g5, g6, g7, g9.** Pre-registered in PREREG_AUTOPILOT.md block 'BATCH SX' before the first scored run.

## Disclosure (binding)
As SX1/SX2; a tercile halving is a coarser use of the same states. Maximum status is FOUND-PENDING; newest live weeks (after 2026-10-13) do not exist yet; pre-2023 not testable (pair rows start 2023-02-10; ERA FLAG n/a).

## Mechanism and design
Risk rule instead of a tilt: entries taken while a two-week option-panel state or a 20-day other-asset state is in its clean top (or bottom) tercile are halved (multiplier 0.5, others 1, renormalised to mean 1); 16 cells = 8 states x 2 tails. The INVERTED control halves the opposite tail.
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) via ROWS_corrected_engine in a clean process (baseline reproduced 1.46 / 2.83 / 2.30, all-in 1.86; O(N) pass1 ap_pz_fast.py verified bit-identical to the original before use). Pair-change framing (overlay on the pair, constant-risk framing n/a). Fill: 1 tick/side + $34.88 per 8 lots; 2x slippage = SLIP_PT 1.0 on baseline and variant. Features use only data from earlier sessions or closed bars; frozen tables from clean.
- Own null: state series date-permuted in 20-day blocks and iid days; 200 draws. Selection-corrected null: 200 worlds, the whole 24-cell grid re-run per world, best-clean cell carried (its clean mean +0.19, all-in mean -0.05). Secondary nulls (rank/p95 clean, all-in): block20 0.95/+0.09, 0.80/+0.01; iid 0.94/+0.11, 0.83/-0.01. Flat-size control: constant 1.000 on every trade.
- Touched trades of the carried cell: 13184 in the pair window (6175 in clean).

## All cells (weekly-Sharpe uplift vs baseline; clean is the only selection column; H1/H2 of unselected cells shown after selection and unused)
| cell | clean | H1 | H2 | all | mean mult | touched (all) | touched (clean) |
|---|---|---|---|---|---|---|---|
| O:gex_norm_1 | -0.04 | +0.32 | -1.27 | -0.34 | 1.000 | 13184 | 6175 |
| O:gex_norm_-1 | -0.44 | +0.13 | -0.42 | -0.31 | 1.000 | 13184 | 6175 |
| O:zgd_1 | -0.09 | +0.15 | -1.58 | -0.46 | 1.000 | 13184 | 6175 |
| O:zgd_-1 | -0.41 | +0.00 | -0.54 | -0.34 | 1.000 | 13184 | 6175 |
| O:skew_1 | -0.44 | +1.73 | -0.71 | -0.23 | 1.000 | 13184 | 6175 |
| O:skew_-1 | -0.06 | -0.17 | -0.89 | -0.24 | 1.000 | 13184 | 6175 |
| O:term_1 | -0.18 | -0.35 | -0.83 | -0.33 | 1.000 | 13184 | 6175 |
| O:term_-1 | -0.38 | +0.95 | -1.04 | -0.35 | 1.000 | 13184 | 6175 |
| X:ZN_R_1 | -0.37 | -0.08 | -0.33 | -0.30 | 1.000 | 13184 | 6175 |
| X:ZN_R_-1 | -0.09 | -0.35 | +0.23 | -0.03 | 1.000 | 13184 | 6175 |
| X:ZN_V_1 | -0.44 | -0.17 | -1.07 | -0.53 | 1.000 | 13184 | 6175 |
| X:ZN_V_-1 | -0.16 | +0.72 | -0.26 | -0.06 | 1.000 | 13184 | 6175 |
| X:GC_R_1 | -0.05 | +0.58 | -0.60 | -0.11 | 1.000 | 13184 | 6175 |
| X:GC_R_-1 | -0.35 | -0.31 | -0.95 | -0.47 | 1.000 | 13184 | 6175 |
| X:GC_V_1 | -0.69 | -0.11 | -0.41 | -0.54 | 1.000 | 13184 | 6175 |
| X:GC_V_-1 | -0.40 | +0.49 | -0.14 | -0.20 | 1.000 | 13184 | 6175 |
| X:CL_R_1 | -0.41 | -0.33 | -0.56 | -0.40 | 1.000 | 13184 | 6175 |
| X:CL_R_-1 | -0.26 | +1.05 | -0.72 | -0.19 | 1.000 | 13184 | 6175 |
| X:CL_V_1 | +0.09 | -0.17 | -0.90 | -0.14 | 1.000 | 13184 | 6175 |
| X:CL_V_-1 | -0.30 | +0.02 | -0.40 | -0.24 | 1.000 | 13184 | 6175 |
| X:6J_R_1 | -0.19 | -0.49 | -0.26 | -0.22 | 1.000 | 13184 | 6175 |
| X:6J_R_-1 | -0.14 | -1.43 | -0.98 | -0.52 | 1.000 | 13184 | 6175 |
| X:6J_V_1 | -0.17 | +0.35 | -0.95 | -0.27 | 1.000 | 13184 | 6175 |
| X:6J_V_-1 | -0.43 | -1.14 | -1.30 | -0.72 | 1.000 | 13184 | 6175 |

## Result for the carried cell (weekly Sharpe)
| span | pair | overlay | uplift | flat-size uplift | uplift minus flat | vs B.Cfg() | 2x slip uplift |
|---|---|---|---|---|---|---|---|
| clean | 1.46 | 1.55 | +0.09 | +0.00 | +0.09 | +0.16 | +0.26 |
| H1 | 2.83 | 2.66 | -0.17 | +0.00 | -0.17 | +0.56 | -0.32 |
| H2 | 2.48 | 1.58 | -0.90 | +0.00 | -0.90 | -1.07 | -1.09 |
| all | 1.90 | 1.76 | -0.14 | +0.00 | -0.14 | -0.04 | -0.12 |

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
- worst week (cand vs pair, k$): clean -80.6 vs -81.9, H1 -78.4 vs -78.3, H2 -80.1 vs -82.5, all -80.6 vs -82.5
- own null (rank/p95): clean 0.95/+0.09, H1 0.35/+1.08, H2 0.38/+0.13, all 0.80/+0.01
- selection-corrected null (rank/p95): clean 0.24/+0.42, H1 0.41/+1.25, H2 0.39/+0.04, all 0.32/+0.29
- plateau neighbours (all-in uplift; need >= -0.11): {'W15': -0.06, 'W25': -0.31} ; definitions {'W15': "{'W': 15}", 'W25': "{'W': 25}"}
- bootstrap clean CI [-0.48, +0.67]; weekly corr with pair 0.84; worst-week delta all-in +1972; worst-decile corr: n/a (overlay on the pair, no hedge claim)
- Controls (uplift clean/H1/H2/all): FLAT0.9 -0.29/+0.04/-0.10/-0.21; FLAT1.1 -0.22/-0.63/-0.38/-0.30; INVERTED -0.30/+0.02/-0.40/-0.24
- g10 insurance metrics: table below. g11 NT8-codable: see Executability.

## Replication legs (>= 2 of 4 needed for FOUND)
- H0 2023-02-10..07-31 (26 weeks, pair Sharpe 0.67): overlay 0.45, uplift -0.22 -> fails.
- Alternating months (2023-08..2026-10): carried cell odd-half -0.29, even-half -0.01; select-on-odd -> X:GC_R_1 (sel +0.25) read even -0.50; select-on-even -> X:ZN_R_-1 (sel +0.45) read odd -0.49 -> fails (needs both > 0 and mean >= 50% of all-in).
- ES / RTY standalone ST+HM books (d1_f4_core, ADR20 k=0.75, live account rules, 1 tick/side, own-instrument state, same recipe): ES +0.08/-0.20/-0.26 (all +0.00, modified 2791 of 2791, base all-in -0.77); RTY -0.23/+0.36/+0.30 (all +0.01, modified 2795 of 2795, base all-in -0.38) -> holds; same calendar window as the pair (correlated evidence).
- Newest live weeks: none exist after 2026-10-13; the forward monitor (PZ5) will score them. ERA flag: pair rows start 2023-02, pre-2023 not testable (n/a).

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 pair | 2.48 | 5.08 | 3.77 | -81.1k | -79.2k | 217k | -82.5k | 41.7 |
| all pair | 1.90 | 3.71 | 9.79 | -79.2k | -78.2k | 280k | -82.5k | 42.3 |
| clean cand | 1.55 | 2.86 | 5.26 | -78.5k | -78.1k | 270k | -80.6k | 42.9 |
| H1 cand | 2.66 | 6.26 | 5.35 | -78.4k | -78.2k | 132k | -78.4k | 35.7 |
| H2 cand | 1.58 | 3.41 | 1.94 | -79.4k | -78.5k | 295k | -80.1k | 44.4 |
| all cand | 1.76 | 3.48 | 9.15 | -78.8k | -78.3k | 295k | -80.6k | 42.3 |

Insurance flags (INS?, cost%, CVaR5 impr%, worst-week impr%, maxDD impr%): clean (False, 6.7, 0.3, 1.6, 3.6); H1 (False, 18.7, -1.0, -0.1, 13.3); H2 (False, -30.3, 2.1, 2.9, -35.5); all (False, -1.8, 0.6, 2.4, -5.2)

## Executability
NT8: same inputs as SX1/SX2; quantity x0.5 on flagged entries (reduce-only; lowers peak contracts). Execution at NinjaTrader Brokerage via Rithmic; no data purchase.

Files: code/census/night_ins/ap_pz_fast.py, ap_pz_core.py (pipeline2), ap_sx_run.py, ap_sx_state.py, ap_sx_xi.py, ap_sx_doc.py; outputs/autopilot/sx3/ (runtime 614s, pool of 5).

DONE SX3
