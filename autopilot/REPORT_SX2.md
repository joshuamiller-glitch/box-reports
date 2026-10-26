# REPORT SX2 - WEEKLY+ CROSS-ASSET STATE SIZE TILT (ZN / GC / CL / 6J signed 20-day trend and vol term; D07 x M4/M8, H6)
**Verdict: NO. FOUND 0. Selected X:CL_V_N_l0.25 (clean-only among 32 cells): weekly Sharpe uplift -0.02 clean / -0.87 H1 / -0.05 H2 (needed +0.10 each); all-in -0.14; bootstrap 90% CI all-in [-0.62, +0.29]; own null clean rank 0.88 (p95 +0.10); selection-corrected null clean rank 0.00 (p95 +0.47); plateau 0.00 of 4; 2x slip +0.11/-0.04/-0.31; H0 -0.26; ES/RTY all-in +0.01/+0.02; failed: g1, g2, g3, g3b, g4, g5, g6, g7, g9.** Pre-registered in PREREG_AUTOPILOT.md block 'BATCH SX' before the first scored run.

## Disclosure (binding)
H1/H2 of the pair are non-virgin for cross-asset families (H7-A/B/C, PZ4, PX20-24). The 20-day other-asset states are new. Maximum status is FOUND-PENDING; newest live weeks (after 2026-10-13) do not exist yet; pre-2023 not testable (pair rows start 2023-02-10; ERA FLAG n/a).

## Mechanism and design
20-day signed trend strength (sum of daily log returns / (sigma20 sqrt 20)) and vol term (ln sigma20/sigma120) of ZN, GC, CL and 6J known at the previous close; clean-frozen CDF rank z; multiplier 1 + sg*lam*z renormalised; 16 cells. PZ4 used the NQ/ES/RTY triple; H7 daily/intraday cross-asset moves; month-level other-asset trend and vol state is new.
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) via ROWS_corrected_engine in a clean process (baseline reproduced 1.46 / 2.83 / 2.30, all-in 1.86; O(N) pass1 ap_pz_fast.py verified bit-identical to the original before use). Pair-change framing (overlay on the pair, constant-risk framing n/a). Fill: 1 tick/side + $34.88 per 8 lots; 2x slippage = SLIP_PT 1.0 on baseline and variant. Features use only data from earlier sessions or closed bars; frozen tables from clean.
- Own null: state series date-permuted in 20-day blocks and iid days; 200 draws. Selection-corrected null: 200 worlds, the whole 32-cell grid re-run per world, best-clean cell carried (its clean mean +0.25, all-in mean -0.02). Secondary nulls (rank/p95 clean, all-in): block20 0.88/+0.10, 0.62/+0.10; iid 0.81/+0.14, 0.65/+0.08. Flat-size control: constant 1.000 on every trade.
- Touched trades of the carried cell: 13184 in the pair window (6175 in clean).

## All cells (weekly-Sharpe uplift vs baseline; clean is the only selection column; H1/H2 of unselected cells shown after selection and unused)
| cell | clean | H1 | H2 | all | mean mult | touched (all) | touched (clean) |
|---|---|---|---|---|---|---|---|
| X:ZN_R_P_l0.25 | -0.18 | -0.88 | -0.05 | -0.24 | 1.000 | 13184 | 6175 |
| X:ZN_R_P_l0.5 | -0.26 | -0.75 | -0.25 | -0.31 | 1.000 | 13184 | 6175 |
| X:ZN_R_N_l0.25 | -0.47 | +0.16 | -0.28 | -0.35 | 1.000 | 13184 | 6175 |
| X:ZN_R_N_l0.5 | -0.30 | -0.07 | -0.35 | -0.30 | 1.000 | 13184 | 6175 |
| X:ZN_V_P_l0.25 | -0.09 | +0.30 | +0.19 | +0.05 | 1.000 | 13184 | 6175 |
| X:ZN_V_P_l0.5 | -0.11 | +0.38 | -0.59 | -0.17 | 1.000 | 13184 | 6175 |
| X:ZN_V_N_l0.25 | -0.23 | +0.44 | -0.98 | -0.29 | 1.000 | 13184 | 6175 |
| X:ZN_V_N_l0.5 | -0.49 | +0.01 | -1.28 | -0.54 | 1.000 | 13184 | 6175 |
| X:GC_R_P_l0.25 | -0.66 | +0.76 | -0.10 | -0.33 | 1.000 | 13184 | 6175 |
| X:GC_R_P_l0.5 | -0.52 | +0.05 | -1.05 | -0.53 | 1.000 | 13184 | 6175 |
| X:GC_R_N_l0.25 | -0.16 | -0.61 | -0.29 | -0.24 | 1.000 | 13184 | 6175 |
| X:GC_R_N_l0.5 | -0.37 | -0.69 | -0.80 | -0.51 | 1.000 | 13184 | 6175 |
| X:GC_V_P_l0.25 | -0.29 | +0.51 | +0.05 | -0.07 | 1.000 | 13184 | 6175 |
| X:GC_V_P_l0.5 | -0.44 | -0.05 | -0.51 | -0.40 | 1.000 | 13184 | 6175 |
| X:GC_V_N_l0.25 | -0.18 | -0.24 | -0.38 | -0.22 | 1.000 | 13184 | 6175 |
| X:GC_V_N_l0.5 | -0.42 | -0.22 | -1.29 | -0.58 | 1.000 | 13184 | 6175 |
| X:CL_R_P_l0.25 | -0.23 | -0.19 | -0.36 | -0.23 | 1.000 | 13184 | 6175 |
| X:CL_R_P_l0.5 | -0.29 | +0.08 | -0.89 | -0.39 | 1.000 | 13184 | 6175 |
| X:CL_R_N_l0.25 | -0.27 | -0.17 | -0.11 | -0.19 | 1.000 | 13184 | 6175 |
| X:CL_R_N_l0.5 | -0.33 | -0.18 | -0.37 | -0.29 | 1.000 | 13184 | 6175 |
| X:CL_V_P_l0.25 | -0.65 | +0.21 | -0.98 | -0.63 | 1.000 | 13184 | 6175 |
| X:CL_V_P_l0.5 | -0.33 | +0.42 | -1.59 | -0.52 | 1.000 | 13184 | 6175 |
| X:CL_V_N_l0.25 | -0.02 | -0.87 | -0.05 | -0.14 | 1.000 | 13184 | 6175 |
| X:CL_V_N_l0.5 | -0.38 | -1.02 | -0.30 | -0.42 | 1.000 | 13184 | 6175 |
| X:6J_R_P_l0.25 | -0.43 | -0.87 | -0.29 | -0.44 | 1.000 | 13184 | 6175 |
| X:6J_R_P_l0.5 | -0.11 | +0.06 | -1.71 | -0.50 | 1.000 | 13184 | 6175 |
| X:6J_R_N_l0.25 | -0.48 | -0.10 | +0.17 | -0.28 | 1.000 | 13184 | 6175 |
| X:6J_R_N_l0.5 | -0.42 | +0.15 | -1.07 | -0.48 | 1.000 | 13184 | 6175 |
| X:6J_V_P_l0.25 | -0.31 | -0.52 | -0.47 | -0.36 | 1.000 | 13184 | 6175 |
| X:6J_V_P_l0.5 | -0.33 | -0.62 | -1.46 | -0.64 | 1.000 | 13184 | 6175 |
| X:6J_V_N_l0.25 | -0.09 | +0.32 | -0.56 | -0.15 | 1.000 | 13184 | 6175 |
| X:6J_V_N_l0.5 | -0.08 | +1.48 | -0.97 | -0.08 | 1.000 | 13184 | 6175 |

## Result for the carried cell (weekly Sharpe)
| span | pair | overlay | uplift | flat-size uplift | uplift minus flat | vs B.Cfg() | 2x slip uplift |
|---|---|---|---|---|---|---|---|
| clean | 1.46 | 1.44 | -0.02 | +0.00 | -0.02 | +0.09 | +0.11 |
| H1 | 2.83 | 1.96 | -0.87 | +0.00 | -0.87 | +0.38 | -0.04 |
| H2 | 2.48 | 2.44 | -0.05 | +0.00 | -0.05 | +0.19 | -0.31 |
| all | 1.90 | 1.76 | -0.14 | +0.00 | -0.14 | +0.17 | +0.02 |

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
- worst week (cand vs pair, k$): clean -85.3 vs -81.9, H1 -79.1 vs -78.3, H2 -82.4 vs -82.5, all -85.3 vs -82.5
- own null (rank/p95): clean 0.88/+0.10, H1 0.08/+0.79, H2 0.64/+0.66, all 0.62/+0.10
- selection-corrected null (rank/p95): clean 0.00/+0.47, H1 0.11/+0.94, H2 0.82/+0.39, all 0.28/+0.32
- plateau neighbours (all-in uplift; need >= -0.10): {'W15': -0.1, 'W25': -0.04, 'lam x0.75': -0.16, 'lam x1.25': -0.17} ; definitions {'W15': "{'W': 15}", 'W25': "{'W': 25}", 'lam x0.75': "{'lam': 0.1875}", 'lam x1.25': "{'lam': 0.3125}"}
- bootstrap clean CI [-0.44, +0.40]; weekly corr with pair 0.89; worst-week delta all-in -2795; worst-decile corr: n/a (overlay on the pair, no hedge claim)
- Controls (uplift clean/H1/H2/all): FLAT0.9 -0.29/+0.04/-0.10/-0.21; FLAT1.1 -0.22/-0.63/-0.38/-0.30; INVERTED -0.65/+0.21/-0.98/-0.63
- g10 insurance metrics: table below. g11 NT8-codable: see Executability.

## Replication legs (>= 2 of 4 needed for FOUND)
- H0 2023-02-10..07-31 (26 weeks, pair Sharpe 0.67): overlay 0.41, uplift -0.26 -> fails.
- Alternating months (2023-08..2026-10): carried cell odd-half +0.20, even-half -0.50; select-on-odd -> X:ZN_V_P_l0.25 (sel +0.30) read even -0.18; select-on-even -> X:6J_V_N_l0.5 (sel +0.60) read odd -0.73 -> fails (needs both > 0 and mean >= 50% of all-in).
- ES / RTY standalone ST+HM books (d1_f4_core, ADR20 k=0.75, live account rules, 1 tick/side, own-instrument state, same recipe): ES +0.10/-0.24/-0.18 (all +0.01, modified 2791 of 2791, base all-in -0.77); RTY -0.13/+0.27/+0.18 (all +0.02, modified 2795 of 2795, base all-in -0.38) -> holds; same calendar window as the pair (correlated evidence).
- Newest live weeks: none exist after 2026-10-13; the forward monitor (PZ5) will score them. ERA flag: pair rows start 2023-02, pre-2023 not testable (n/a).

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 pair | 2.48 | 5.08 | 3.77 | -81.1k | -79.2k | 217k | -82.5k | 41.7 |
| all pair | 1.90 | 3.71 | 9.79 | -79.2k | -78.2k | 280k | -82.5k | 42.3 |
| clean cand | 1.44 | 2.67 | 4.62 | -80.2k | -78.9k | 283k | -85.3k | 41.9 |
| H1 cand | 1.96 | 3.47 | 2.42 | -78.7k | -78.5k | 186k | -79.1k | 39.3 |
| H2 cand | 2.44 | 5.36 | 3.50 | -79.9k | -74.8k | 245k | -82.4k | 36.1 |
| all cand | 1.76 | 3.36 | 9.25 | -80.2k | -78.9k | 283k | -85.3k | 40.5 |

Insurance flags (INS?, cost%, CVaR5 impr%, worst-week impr%, maxDD impr%): clean (False, -1.6, -1.9, -4.2, -1.0); H1 (False, -24.3, -1.3, -1.1, -22.6); H2 (False, 4.7, 1.5, 0.1, -12.7); all (False, -4.6, -1.2, -3.4, -1.0)

## Executability
NT8: needs daily closes of ZN, GC, CL, 6J (extra data series), rolling 20/120-day statistics, clean-frozen CDF tables; entry-quantity multiplier. Execution at NinjaTrader Brokerage via Rithmic; no data purchase.

Files: code/census/night_ins/ap_pz_fast.py, ap_pz_core.py (pipeline2), ap_sx_run.py, ap_sx_state.py, ap_sx_xi.py, ap_sx_doc.py; outputs/autopilot/sx2/ (runtime 761s, pool of 5).

DONE SX2
