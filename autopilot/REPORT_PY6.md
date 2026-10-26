# REPORT PY6 - PAIR ROLLING 8-WEEK HEALTH AS A CONTINUOUS SIZE MODULATOR (M8 x D00, H5)
**Verdict: NO. FOUND 0. Carried H2_N_a0.25: weekly Sharpe uplift -0.10 clean / -0.44 H1 / +0.05 H2 (needed +0.10 each); all-in -0.13; bootstrap 90% CI of all-in uplift [-0.53, +0.24]; plateau 0.00 of 4; own-null rank clean 0.71 (p95 +0.09); selection-corrected null: best-of-grid clean uplift p95 +0.32.** Pool of 5, pre-registered in PREREG_AUTOPILOT.md block 'BATCH 7 (worker ap_py2)' before the first scored run.

## Set-up and fill model
- weekly health of the baseline pair from the 8 completed weeks before the entry week (H1 = 8-week Sharpe, H2 = 8-week P&L z vs expanding weekly sd); f = clip(1 + sg*a*(2p-1), 0.5, 1.5), p = expanding percentile of the health series (factor 1 until 10 prior values), applied to both books; 8 cells = metric{H1,H2} x sg{+,-} x a{0.25,0.5}. Difference to cousins: C11-HM is a binary HM-only OFF switch at the expanding 10th percentile of HM own 8-week Sharpe (+0.20/-0.32/-0.23); B8 switches an external 5-min ensemble ON after trailing pair loss (adds a sleeve, no rescale); G0b is a one-sided drawdown-from-peak step-down; PY6 is two-sided and continuous (size up and down) on a rolling risk-adjusted score of both books.
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) via ROWS_corrected_engine, clean process (ap_h7_core -> ap_g6_core), baseline reproduced 1.46 / 2.83 / 2.30. Fill model as live: 1 tick/side + $34.88 per 8 lots; 2x slippage = SLIP_PT 1.0 on baseline and variant. Overlay NOT renormalised. Features use only data closed before the entry bar.
- Selection on clean only (uplift vs baseline per cell, clean): H1_P_a0.25 -0.190, H1_P_a0.5 -0.470, H1_N_a0.25 -0.150, H1_N_a0.5 -0.433, H2_P_a0.25 -0.323, H2_P_a0.5 -0.439, H2_N_a0.25 -0.103, H2_N_a0.5 -0.185. Max-clean cell carried; H1/H2 read once for it (other cells' H1/H2 are in the json, unused).

## Result for the carried cell (weekly Sharpe)
| span | pair | overlay | uplift | vs B.Cfg() | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.36 | -0.10 | +0.16 | +0.03 |
| H1 | 2.83 | 2.39 | -0.44 | -0.11 | -0.16 |
| H2 | 2.30 | 2.34 | +0.05 | -0.36 | -0.37 |
| all | 1.86 | 1.72 | -0.13 | +0.00 | -0.09 |

## Gate checklist
- 3 uplift >= +0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): PASS
- own shuffled-state null p95 clean and all-in: FAIL
- bootstrap CI > 0: FAIL
- plateau >= 75%: FAIL
- 2x slip >= +0.10 each span: FAIL
- selection-corrected null (clean uplift > 95th pct of re-selected null worlds): FAIL
- own shuffled-state null detail (rank/p95, 100 replicates): clean 0.71/+0.09, H1 0.23/+0.88, H2 0.77/+0.53, all 0.71/+0.05
- selection-corrected null (30 worlds, every state shuffled, full grid re-selected on clean): real clean uplift beats 0% of worlds; best-of-grid clean uplift >= +0.10 in 57% of worlds; passes +0.10 on clean AND H1 AND H2 in 0% of worlds (chance gate-1 pass rate)
- plateau neighbours (all-in uplift): {'a x0.75': -0.05, 'a x1.25': -0.49, 'win6': 0.07, 'win10': -0.31}
- flat-size controls (constant multiplier on the modulated rows, uplift clean/H1/H2/all): mean-of-factor 0.949: -0.27/-0.07/+0.18/-0.15; x0.9: -0.29/+0.04/-0.09/-0.21; x1.1: -0.22/-0.63/-0.36/-0.30
- worst-decile corr: n/a (modulator of the pair, weekly corr with pair 0.92; no hedge claim)
- factor range: min 0.75 max 1.25 mean 0.948 (all rows; rows of the other book are 1)
- Pre-registration, clean-only selection, H1/H2 once: PASS (process).

## Replication legs (>= 2 of 4 needed for FOUND)
- alternating-month split (2023-08..2026-10): odd->even: cell chosen on selection months = H1_N_a0.25 (uplift -0.00), held-out -0.25; carried cell sel/held-out -0.05/-0.25; even->odd: cell chosen on selection months = H2_P_a0.5 (uplift +0.05), held-out -0.87; carried cell sel/held-out -0.25/-0.05 -> FAILS
- ES / RTY 2023-26 cross-check (d1_f4_core ST+HM books, k=0.75, own-instrument state, same recipe): ES +0.30/-0.00/+0.18 (all +0.23), RTY +0.18/-0.15/+0.01 (all +0.07) -> HOLDS
- H0 (2023-02..07): the 100-trade (10-week) warm-up leaves H0 largely unmodulated; not creditable. Newest live weeks: none beyond 2026-10-13 yet. ERA flag: not testable (pair rows start 2023-02).
- Legs held: formally 1 of 2, but vacuous: the NQ carried cell has negative all-in uplift (-0.13) so the ES/RTY positive uplifts are not a replication of anything (selected sign is the opposite of the cell that helps ES/RTY on clean). Effective legs held: 0.

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| clean cand | 1.36 | 2.55 | 3.48 | -78.2k | -77.7k | 366k | -79.2k | 44.8 |
| H1 cand | 2.39 | 4.58 | 3.53 | -78.5k | -78.0k | 140k | -79.1k | 42.9 |
| H2 cand | 2.34 | 5.17 | 3.03 | -77.6k | -73.6k | 251k | -78.1k | 47.2 |
| all cand | 1.72 | 3.35 | 6.91 | -78.2k | -77.7k | 366k | -79.2k | 45.2 |

Insurance flags (INS?, cost%, CVaR5 impr%, worst-week impr%, maxDD impr%): clean (False, -4.1, 0.7, 3.3, -30.7); H1 (False, -17.1, -1.1, -1.0, 8.0); H2 (False, 0.2, 4.3, 5.4, -15.6); all (False, -5.8, 1.2, 4.0, -30.7)

## Non-virgin disclosure
VR60 construct is read in PA5/PX27/G8-A, gap/ADR in PX26, trailing-vol sizing in B17, health-state cousins C11-HM/G0b/B8/B19: their H1/H2 were read pair-wide. Per-book application and the continuous tilt are new, but H1/H2 are not virgin for these state families; a FOUND would need the replication legs above.

## Executability
NT8 at NinjaTrader Brokerage via Rithmic: the strategies read a 1-min NQ vol state or a daily state (or the weekly P&L log) and set an entry-quantity multiplier in [0.5, 1.5] per book; peak contracts up to +50% on flagged entries; margin at 1.5x entry size for the modulated book.

Files: code/census/night_ins/ap_py2_run.py, ap_g10_rep.py, ap_h7_alt.py, ap_py2_xi.py, ap_py2_doc.py; outputs/autopilot/py6/.

DONE PY6
