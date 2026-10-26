# REPORT PY5 - ST-ONLY CONTINUOUS SIZE TILT BY DAY/INTRADAY VOL STATE (M8 x D08/D06, H2-H4)
**Verdict: NO. FOUND 0. Carried GAP_N_a0.5: weekly Sharpe uplift +0.03 clean / -0.24 H1 / -0.19 H2 (needed +0.10 each); all-in -0.04; bootstrap 90% CI of all-in uplift [-0.29, +0.20]; plateau 0.00 of 4; own-null rank clean 1.00 (p95 +0.00); selection-corrected null: best-of-grid clean uplift p95 +0.27.** Pool of 5, pre-registered in PREREG_AUTOPILOT.md block 'BATCH 7 (worker ap_py2)' before the first scored run.

## Set-up and fill model
- identical 12 cells to PY4 applied to ST rows only (HM unchanged); percentile within the ST book.
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) via ROWS_corrected_engine, clean process (ap_h7_core -> ap_g6_core), baseline reproduced 1.46 / 2.83 / 2.30. Fill model as live: 1 tick/side + $34.88 per 8 lots; 2x slippage = SLIP_PT 1.0 on baseline and variant. Overlay NOT renormalised. Features use only data closed before the entry bar.
- Selection on clean only (uplift vs baseline per cell, clean): VR60_P_a0.25 -0.133, VR60_P_a0.5 -0.338, VR60_N_a0.25 -0.140, VR60_N_a0.5 -0.593, GAP_P_a0.25 -0.194, GAP_P_a0.5 -0.016, GAP_N_a0.25 +0.015, GAP_N_a0.5 +0.033, RV20_P_a0.25 -0.203, RV20_P_a0.5 -0.035, RV20_N_a0.25 -0.193, RV20_N_a0.5 -0.415. Max-clean cell carried; H1/H2 read once for it (other cells' H1/H2 are in the json, unused).

## Result for the carried cell (weekly Sharpe)
| span | pair | overlay | uplift | vs B.Cfg() | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.49 | +0.03 | -0.02 | +0.21 |
| H1 | 2.83 | 2.59 | -0.24 | +0.27 | -0.01 |
| H2 | 2.30 | 2.10 | -0.19 | -0.24 | -0.18 |
| all | 1.86 | 1.81 | -0.04 | -0.01 | +0.11 |

## Gate checklist
- 3 uplift >= +0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): PASS
- own shuffled-state null p95 clean and all-in: FAIL
- bootstrap CI > 0: FAIL
- plateau >= 75%: FAIL
- 2x slip >= +0.10 each span: FAIL
- selection-corrected null (clean uplift > 95th pct of re-selected null worlds): FAIL
- own shuffled-state null detail (rank/p95, 100 replicates): clean 1.00/+0.00, H1 0.00/+0.00, H2 0.00/+0.00, all 0.00/+0.00
- selection-corrected null (30 worlds, every state shuffled, full grid re-selected on clean): real clean uplift beats 33% of worlds; best-of-grid clean uplift >= +0.10 in 33% of worlds; passes +0.10 on clean AND H1 AND H2 in 0% of worlds (chance gate-1 pass rate)
- plateau neighbours (all-in uplift): {'a x0.75': -0.05, 'a x1.25': -0.07, 'win15': -0.05, 'win25': -0.04}
- flat-size controls (constant multiplier on the modulated rows, uplift clean/H1/H2/all): mean-of-factor 0.997: -0.15/-0.00/+0.00/-0.10; x0.9: -0.20/+0.87/+0.08/+0.02; x1.1: -0.14/-0.44/-0.55/-0.26
- worst-decile corr: n/a (modulator of the pair, weekly corr with pair 0.97; no hedge claim)
- factor range: min 0.50 max 1.50 mean 0.993 (all rows; rows of the other book are 1)
- Pre-registration, clean-only selection, H1/H2 once: PASS (process).

## Replication legs (>= 2 of 4 needed for FOUND)
- alternating-month split (2023-08..2026-10): odd->even: cell chosen on selection months = GAP_P_a0.5 (uplift +0.05), held-out +0.07; carried cell sel/held-out -0.08/-0.06; even->odd: cell chosen on selection months = VR60_P_a0.5 (uplift +0.22), held-out -0.55; carried cell sel/held-out -0.06/-0.08 -> FAILS
- ES / RTY 2023-26 cross-check (d1_f4_core ST+HM books, k=0.75, own-instrument state, same recipe): ES +0.00/-0.10/-0.09 (all -0.03), RTY -0.04/+0.25/-0.11 (all +0.00) -> FAILS
- H0 (2023-02..07): the 100-trade (10-week) warm-up leaves H0 largely unmodulated; not creditable. Newest live weeks: none beyond 2026-10-13 yet. ERA flag: not testable (pair rows start 2023-02).
- Legs held: 0 of 2 creditable (FOUND needs 2 of 4 and all gates).

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| clean cand | 1.49 | 2.88 | 4.58 | -79.3k | -78.4k | 302k | -81.9k | 41.0 |
| H1 cand | 2.59 | 5.64 | 3.23 | -78.7k | -78.1k | 186k | -79.8k | 42.9 |
| H2 cand | 2.10 | 4.40 | 3.41 | -80.0k | -78.5k | 218k | -82.5k | 44.4 |
| all cand | 1.81 | 3.61 | 9.03 | -79.5k | -78.5k | 302k | -82.5k | 42.3 |

Insurance flags (INS?, cost%, CVaR5 impr%, worst-week impr%, maxDD impr%): clean (False, 4.1, -0.7, 0.0, -7.9); H1 (False, 1.2, -1.4, -1.9, -22.7); H2 (False, -2.5, 1.4, 0.0, -0.1); all (False, 1.6, -0.4, 0.0, -7.9)

## Non-virgin disclosure
VR60 construct is read in PA5/PX27/G8-A, gap/ADR in PX26, trailing-vol sizing in B17, health-state cousins C11-HM/G0b/B8/B19: their H1/H2 were read pair-wide. Per-book application and the continuous tilt are new, but H1/H2 are not virgin for these state families; a FOUND would need the replication legs above.

## Executability
NT8 at NinjaTrader Brokerage via Rithmic: the strategies read a 1-min NQ vol state or a daily state (or the weekly P&L log) and set an entry-quantity multiplier in [0.5, 1.5] per book; peak contracts up to +50% on flagged entries; margin at 1.5x entry size for the modulated book.

Files: code/census/night_ins/ap_py2_run.py, ap_g10_rep.py, ap_h7_alt.py, ap_py2_xi.py, ap_py2_doc.py; outputs/autopilot/py5/.

DONE PY5
