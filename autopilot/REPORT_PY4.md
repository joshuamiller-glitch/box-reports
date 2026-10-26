# REPORT PY4 - HM-ONLY CONTINUOUS SIZE TILT BY DAY/INTRADAY VOL STATE (M8 x D08/D06, H2-H4)
**Verdict: NO. FOUND 0. Carried VR60_N_a0.25: weekly Sharpe uplift +0.18 clean / +0.25 H1 / -0.00 H2 (needed +0.10 each); all-in +0.18; bootstrap 90% CI of all-in uplift [-0.05, +0.44]; plateau 0.50 of 4; own-null rank clean 0.66 (p95 +0.33); selection-corrected null: best-of-grid clean uplift p95 +0.37.** Pool of 5, pre-registered in PREREG_AUTOPILOT.md block 'BATCH 7 (worker ap_py2)' before the first scored run.

## Set-up and fill model
- HM rows only (ST unchanged); states VR60 (ln 60-min realised vol / trailing 7,800-bar baseline), GAP (|overnight gap|/ADR20, RTH entries), RV20 (20-day realised vol of NQ daily returns); f = clip(1 + sg*a*(2p-1), 0.5, 1.5) with walk-forward expanding percentile p within the HM book (factor 1 for the first 100 HM trades); 12 cells = 3 states x sg{+,-} x a{0.25,0.5}.
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) via ROWS_corrected_engine, clean process (ap_h7_core -> ap_g6_core), baseline reproduced 1.46 / 2.83 / 2.30. Fill model as live: 1 tick/side + $34.88 per 8 lots; 2x slippage = SLIP_PT 1.0 on baseline and variant. Overlay NOT renormalised. Features use only data closed before the entry bar.
- Selection on clean only (uplift vs baseline per cell, clean): VR60_P_a0.25 -0.051, VR60_P_a0.5 -0.103, VR60_N_a0.25 +0.176, VR60_N_a0.5 -0.278, GAP_P_a0.25 +0.053, GAP_P_a0.5 -0.038, GAP_N_a0.25 -0.083, GAP_N_a0.5 -0.036, RV20_P_a0.25 -0.151, RV20_P_a0.5 -0.012, RV20_N_a0.25 -0.154, RV20_N_a0.5 +0.027. Max-clean cell carried; H1/H2 read once for it (other cells' H1/H2 are in the json, unused).

## Result for the carried cell (weekly Sharpe)
| span | pair | overlay | uplift | vs B.Cfg() | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.64 | +0.18 | +0.14 | +0.26 |
| H1 | 2.83 | 3.08 | +0.25 | +0.59 | +0.06 |
| H2 | 2.30 | 2.29 | -0.00 | +0.33 | -0.26 |
| all | 1.86 | 2.04 | +0.18 | +0.26 | +0.14 |

## Gate checklist
- 3 uplift >= +0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): FAIL
- own shuffled-state null p95 clean and all-in: FAIL
- bootstrap CI > 0: FAIL
- plateau >= 75%: FAIL
- 2x slip >= +0.10 each span: FAIL
- selection-corrected null (clean uplift > 95th pct of re-selected null worlds): FAIL
- own shuffled-state null detail (rank/p95, 100 replicates): clean 0.66/+0.33, H1 0.80/+0.56, H2 0.34/+0.66, all 0.74/+0.31
- selection-corrected null (30 worlds, every state shuffled, full grid re-selected on clean): real clean uplift beats 47% of worlds; best-of-grid clean uplift >= +0.10 in 80% of worlds; passes +0.10 on clean AND H1 AND H2 in 10% of worlds (chance gate-1 pass rate)
- plateau neighbours (all-in uplift): {'a x0.75': 0.14, 'a x1.25': 0.16, 'W45': 0.12, 'W75': 0.22}
- flat-size controls (constant multiplier on the modulated rows, uplift clean/H1/H2/all): mean-of-factor 1.008: +0.00/+0.03/+0.07/+0.02; x0.9: -0.13/-0.24/+0.29/-0.05; x1.1: +0.06/-0.38/+0.58/+0.13
- worst-decile corr: n/a (modulator of the pair, weekly corr with pair 0.96; no hedge claim)
- factor range: min 0.75 max 1.25 mean 1.003 (all rows; rows of the other book are 1)
- Pre-registration, clean-only selection, H1/H2 once: PASS (process).

## Replication legs (>= 2 of 4 needed for FOUND)
- alternating-month split (2023-08..2026-10): odd->even: cell chosen on selection months = GAP_P_a0.5 (uplift +0.15), held-out -0.04; carried cell sel/held-out +0.08/+0.16; even->odd: cell chosen on selection months = VR60_P_a0.5 (uplift +0.77), held-out -0.39; carried cell sel/held-out +0.16/+0.08 -> FAILS
- ES / RTY 2023-26 cross-check (d1_f4_core ST+HM books, k=0.75, own-instrument state, same recipe): ES +0.05/-0.25/+0.08 (all +0.01), RTY -0.11/+0.04/+0.10 (all -0.04) -> FAILS
- H0 (2023-02..07): the 100-trade (10-week) warm-up leaves H0 largely unmodulated; not creditable. Newest live weeks: none beyond 2026-10-13 yet. ERA flag: not testable (pair rows start 2023-02).
- Legs held: 0 of 2 creditable (FOUND needs 2 of 4 and all gates).

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| clean cand | 1.64 | 3.06 | 5.74 | -79.6k | -78.5k | 252k | -87.8k | 40.0 |
| H1 cand | 3.08 | 7.69 | 4.83 | -77.5k | -67.6k | 159k | -77.8k | 35.7 |
| H2 cand | 2.29 | 4.75 | 3.13 | -78.8k | -77.9k | 244k | -79.6k | 38.9 |
| all cand | 2.04 | 4.06 | 11.84 | -79.2k | -78.3k | 252k | -87.8k | 39.3 |

Insurance flags (INS?, cost%, CVaR5 impr%, worst-week impr%, maxDD impr%): clean (False, 8.7, -1.0, -7.2, 10.2); H1 (False, 29.6, 0.1, 0.6, -5.0); H2 (False, 0.3, 2.8, 3.5, -12.3); all (False, 10.9, -0.0, -6.4, 10.2)

## Non-virgin disclosure
VR60 construct is read in PA5/PX27/G8-A, gap/ADR in PX26, trailing-vol sizing in B17, health-state cousins C11-HM/G0b/B8/B19: their H1/H2 were read pair-wide. Per-book application and the continuous tilt are new, but H1/H2 are not virgin for these state families; a FOUND would need the replication legs above.

## Executability
NT8 at NinjaTrader Brokerage via Rithmic: the strategies read a 1-min NQ vol state or a daily state (or the weekly P&L log) and set an entry-quantity multiplier in [0.5, 1.5] per book; peak contracts up to +50% on flagged entries; margin at 1.5x entry size for the modulated book.

Files: code/census/night_ins/ap_py2_run.py, ap_g10_rep.py, ap_h7_alt.py, ap_py2_xi.py, ap_py2_doc.py; outputs/autopilot/py4/.

DONE PY4
