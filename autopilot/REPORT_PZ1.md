# REPORT PZ1 - NQ 20-DAY REGIME SIZE TILT (trend strength / drawdown / vol term; D08 x M4/M8, H5)
**Verdict: NO. FOUND 0. Selected TS20_N_l0.5 (clean-only among 12 cells): weekly Sharpe uplift +0.06 clean / -0.37 H1 / -1.46 H2 (needed +0.10 each); all-in -0.32; bootstrap 90% CI all-in [-0.91, +0.27]; own null clean rank 0.90 (p95 +0.19); selection-corrected null clean rank 0.34 (p95 +0.38); plateau 0.00 of 4; 2x slip +0.23/-0.48/-1.92; H0 -0.43; ES/RTY all-in +0.26/+0.04; failed: g1, g2, g3, g3b, g4, g5, g6, g7, g9.** Pre-registered in PREREG_AUTOPILOT.md block 'BATCH 8 PZ1-PZ5' before the first scored run.

## Disclosure (binding)
H1/H2 of the pair were read for the neighbouring state families (RV20 level in PY4/PY5/H8-A, 20-day range in G8-C, own-drift alignment in J9P-A, VIX blocks PY1-PY3); the 20-day trend-strength / drawdown / vol-term observables are new, but H1/H2 are not virgin for the family. Maximum status is FOUND-PENDING; newest live weeks (after 2026-10-13) do not exist yet; pre-2023 not testable (pair rows start 2023-02-10; ERA FLAG n/a).

## Mechanism and design
Month-level, pair-independent NQ states known before the entry day: TS20 = |20-day log return| / (daily sigma20*sqrt 20) (trend persistence irrespective of direction), DD60 = drawdown of the last close from its 60-day high (log), VT20 = ln(sigma20/sigma120). z = clean-frozen empirical-CDF rank in [-1,1]; m = (1 + sg*lam*z) renormalised to mean 1 over all trades, lam in {0.25,0.5}, both signs pre-registered (12 cells). The tilt is a continuous shrunk size modulator, not a switch; the flat-size control is a constant multiplier at the same mean (=1, i.e. the baseline) and at 0.9/1.1.
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) via ROWS_corrected_engine in a clean process (baseline reproduced 1.46 / 2.83 / 2.30, all-in 1.86; O(N) pass1 ap_pz_fast.py verified bit-identical to the original before use). Pair-change framing (overlay on the pair, constant-risk framing n/a). Fill: 1 tick/side + $34.88 per 8 lots; 2x slippage = SLIP_PT 1.0 on baseline and variant. Features use only data from earlier sessions or closed bars; frozen tables from clean.
- Own null: state series permuted in 20-trading-day blocks (random order and offset; preserves month-level persistence), cell rebuilt, 200 replicates (iid-day permutation null reported as secondary). Selection-corrected null: 200 worlds, the whole 12-cell grid re-run per world, best-clean cell carried (its clean mean +0.12, all-in mean -0.07). Secondary nulls (rank/p95 clean, all-in): block20 0.90/+0.19, 0.65/-0.00; iid 0.85/+0.20, 0.54/+0.05. Flat-size control: constant 1.000 on every trade.
- Touched trades of the carried cell: 13089 in the pair window (6175 in clean).

## All cells (weekly-Sharpe uplift vs baseline; clean is the only selection column; H1/H2 of unselected cells shown after selection and unused)
| cell | clean | H1 | H2 | all | mean mult | touched (all) | touched (clean) |
|---|---|---|---|---|---|---|---|
| TS20_P_l0.25 | -0.26 | +0.77 | -0.56 | -0.20 | 1.000 | 13089 | 6175 |
| TS20_P_l0.5 | -0.40 | +1.19 | -1.21 | -0.36 | 1.000 | 13089 | 6175 |
| TS20_N_l0.25 | -0.10 | -0.30 | -0.41 | -0.19 | 1.000 | 13089 | 6175 |
| TS20_N_l0.5 | +0.06 | -0.37 | -1.46 | -0.32 | 1.000 | 13089 | 6175 |
| DD60_P_l0.25 | -0.32 | -0.63 | -0.83 | -0.48 | 1.000 | 13089 | 6175 |
| DD60_P_l0.5 | -0.14 | -0.62 | -0.59 | -0.32 | 1.000 | 13089 | 6175 |
| DD60_N_l0.25 | -0.29 | -0.20 | -0.63 | -0.33 | 1.000 | 13089 | 6175 |
| DD60_N_l0.5 | -0.06 | -0.81 | -0.78 | -0.32 | 1.000 | 13089 | 6175 |
| VT20_P_l0.25 | -0.62 | +0.89 | -0.61 | -0.40 | 1.000 | 13089 | 6175 |
| VT20_P_l0.5 | -0.05 | +0.72 | -1.21 | -0.18 | 1.000 | 13089 | 6175 |
| VT20_N_l0.25 | -0.17 | -0.25 | +0.09 | -0.10 | 1.000 | 13089 | 6175 |
| VT20_N_l0.5 | -0.03 | -0.71 | -0.86 | -0.32 | 1.000 | 13089 | 6175 |

## Result for the carried cell (weekly Sharpe)
| span | pair | overlay | uplift | flat-size uplift | uplift minus flat | vs B.Cfg() | 2x slip uplift |
|---|---|---|---|---|---|---|---|
| clean | 1.46 | 1.52 | +0.06 | +0.00 | +0.06 | +0.61 | +0.23 |
| H1 | 2.83 | 2.45 | -0.37 | +0.00 | -0.37 | +1.00 | -0.48 |
| H2 | 2.30 | 0.84 | -1.46 | +0.00 | -1.46 | -1.16 | -1.92 |
| all | 1.86 | 1.54 | -0.32 | +0.00 | -0.32 | +0.28 | -0.34 |

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
- worst week (cand vs pair, k$): clean -80.0 vs -81.9, H1 -79.6 vs -78.3, H2 -80.4 vs -82.5, all -80.4 vs -82.5
- own null (rank/p95): clean 0.90/+0.19, H1 0.42/+1.00, H2 0.14/+0.22, all 0.65/-0.00
- selection-corrected null (rank/p95): clean 0.34/+0.38, H1 0.35/+1.07, H2 0.09/+0.40, all 0.10/+0.23
- plateau neighbours (all-in uplift; need >= -0.24): {'lam x0.75': -0.14, 'lam x1.25': -0.49, 'W15': -0.47, 'W25': -0.69} ; definitions {'lam x0.75': "{'lam': 0.375}", 'lam x1.25': "{'lam': 0.625}", 'W15': "{'W': 15}", 'W25': "{'W': 25}"}
- bootstrap clean CI [-0.54, +0.70]; weekly corr with pair 0.81; worst-week delta all-in +2150; worst-decile corr: n/a (overlay on the pair, no hedge claim)
- Controls (uplift clean/H1/H2/all): FLAT0.9 -0.29/+0.04/-0.09/-0.21; FLAT1.1 -0.22/-0.63/-0.36/-0.30; INVERTED -0.40/+1.19/-1.21/-0.36
- g10 insurance metrics: table below. g11 NT8-codable: see Executability.

## Replication legs (>= 2 of 4 needed for FOUND)
- H0 2023-02-10..07-31 (26 weeks, pair Sharpe 0.67): overlay 0.24, uplift -0.43 -> fails.
- Alternating months (2023-08..2026-10): carried cell odd-half -0.22, even-half -0.46; select-on-odd -> TS20_N_l0.25 (sel -0.05) read even -0.34; select-on-even -> TS20_P_l0.25 (sel +0.33) read odd -0.73 -> fails (needs both > 0 and mean >= 50% of all-in).
- ES / RTY standalone ST+HM books (d1_f4_core, ADR20 k=0.75, live account rules, 1 tick/side, own-instrument state, same recipe): ES +0.25/+0.24/+0.34 (all +0.26, modified 2780 of 2780, base all-in -0.75); RTY +0.08/+0.48/-0.46 (all +0.04, modified 2784 of 2784, base all-in -0.41) -> holds; same calendar window as the pair (correlated evidence).
- Newest live weeks: none exist after 2026-10-13; the forward monitor (PZ5) will score them. ERA flag: pair rows start 2023-02, pre-2023 not testable (n/a).

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| clean cand | 1.52 | 2.82 | 4.99 | -78.9k | -78.3k | 271k | -80.0k | 41.9 |
| H1 cand | 2.45 | 4.90 | 4.21 | -78.8k | -78.5k | 142k | -79.6k | 32.1 |
| H2 cand | 0.84 | 1.41 | 0.94 | -79.2k | -78.5k | 277k | -80.4k | 50.0 |
| all cand | 1.54 | 2.82 | 7.98 | -79.1k | -78.5k | 277k | -80.4k | 42.3 |

Insurance flags (INS?, cost%, CVaR5 impr%, worst-week impr%, maxDD impr%): clean (False, 1.7, -0.3, 2.3, 3.1); H1 (False, 1.0, -1.6, -1.7, 6.1); H2 (False, -65.9, 2.3, 2.6, -27.5); all (False, -17.6, 0.1, 2.6, 1.0)

## Executability
NT8: daily close series of NQ (16:59 ET), rolling 20/60/120-day statistics, clean-frozen CDF tables as constants, entry-quantity multiplier in [1-lam,1+lam]/mean applied to both books (rounds to whole contracts); margin +up to 50% on top-rank entries at lam 0.5. Execution at NinjaTrader Brokerage via Rithmic; no data purchase.

Files: code/census/night_ins/ap_pz_fast.py, ap_pz_core.py, ap_pz1_run.py, ap_pz_xi.py, ap_pz_doc.py; outputs/autopilot/pz1/ (runtime 447s, pool of 5).

DONE PZ1
