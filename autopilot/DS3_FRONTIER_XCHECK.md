# DS3_FRONTIER_XCHECK - independent cross-check of ZL-2's risk frontier (DIS-BD part 2, Z3, 2026-11-05)
Measurement, no PASS claims, nothing live. Prereg l2vast/ds3/prereg/DIS_BD_prereg.md sha256 b9d0674df737a516fa74c9efa9dc004f9947ecb7ba1a787f444315f09328dfd7. Engine tie-out of the base (part 1): autopilot/DS3_BASE_TIEOUT.md. Code l2vast/ds3/code/dis_bd/ (bd_cell.py, bd_xcheck.py); data l2vast/ds3/out/dis_bd/ (cell_*.pkl, xcheck.csv). Frontier: autopilot/DS3_RISK_FRONTIER.md, out/dis_ba/DS3_RISK_FRONTIER.csv (92 cells).

## Plain sentences
1. The live cell and five pause-0 frontier cells (all converged in ZL-2's loop) reproduce to the printed precision: on every metric (total, full-period mean, maxDD of the full period / 2026 / HOLD / PRE / L6M / X', worst day, worst week, peak net lots, synthetic tail) the largest difference is 0.00% / under $0.1k, far inside the Lead's 5% and ZL-2's 1% / $0.5k thresholds; the live tie-out is $2,520,149.07, mean $17.72k per week, HOLD maxDD $122.02k.
2. The user's key dial with the 30-minute pause (PE x0.5, cap 12, pause 30, gate 1R) is NOT confirmed: ZL-2's cell is one of the 31 that did not converge (last iterate) and my independently built, converged pause emulation disagrees by more than 5% on most metrics (total $1,613k vs $1,469k, +9.9%; full-period mean +12.3%; 2026 maxDD $31.1k vs $22.8k; HOLD maxDD $84.6k vs $62.4k, +35%; L6M maxDD +39%): the pause-30 numbers should not be read until ZL-2's re-run lands, and even then they depend on the definition of 'cut' and of the pause window.
3. Independence and its limits: the five pause-0 cells were rebuilt with my own lot construction (l1 stage from the ts2 module, PE weight in the ER slot, my own rounding and zone half), the ORIGINAL stack_expo.run_stack hook with a patched weighted base (not ZL-2's re-implementation of its fixed-point loop), my own gate switch (OC spec pb_loss) and my own window / carrying-week code, in separate processes; but both paths share the engine kernels and the lot-order module, so this checks the cell bookkeeping and the cap loop, not the engine itself.

## 1. Pause-0 cells: mine / ZL-2 ($k; mean per week; maxDD windows with carrying weeks dropped as in the frontier page)
| cell | total | full-period mean | full-period maxDD | 2026 mean | HOLD maxDD | PRE maxDD | worst day | worst week | peak net lots | max abs % diff over all 13 metrics |
|---|---|---|---|---|---|---|---|---|---|---|
| w0.50 cap10 pause0 gate1R | 1711.30 / 1711.30 | 12.13 / 12.13 | 61.14 / 61.14 | 24.29 / 24.29 | 65.00 / 65.00 | 61.14 / 61.14 | -27.06 / -27.06 | -42.44 / -42.44 | 12 / 12 | 0.00% |
| w0.50 cap12 pause0 gate1R | 1787.35 / 1787.35 | 12.60 / 12.60 | 62.36 / 62.36 | 25.06 / 25.06 | 66.63 / 66.63 | 62.36 / 62.36 | -27.06 / -27.06 | -44.53 / -44.53 | 14 / 14 | 0.00% |
| w0.50 cap8 pause0 gate1R | 1607.48 / 1607.48 | 11.25 / 11.25 | 58.63 / 58.63 | 22.36 / 22.36 | 52.86 / 52.86 | 58.30 / 58.30 | -27.06 / -27.06 | -39.94 / -39.94 | 11 / 11 | 0.00% |
| w0.50 cap- pause0 gate1R | 1842.40 / 1842.40 | 12.94 / 12.94 | 63.03 / 63.03 | 25.72 / 25.72 | 67.50 / 67.50 | 63.03 / 63.03 | -27.06 / -27.06 | -44.04 / -44.04 | 15 / 15 | 0.00% |
| w0.75 cap- pause0 gate1R | 1930.56 / 1930.56 | 13.53 / 13.53 | 62.93 / 62.93 | 25.63 / 25.63 | 78.09 / 78.09 | 62.93 / 62.93 | -29.76 / -29.76 | -41.19 / -41.19 | 16 / 16 | 0.00% |
| w1.00 cap- pause0 gate2R | 2520.15 / 2520.15 | 17.72 / 17.72 | 75.06 / 75.06 | 35.32 / 35.32 | 122.02 / 122.02 | 75.06 / 75.06 | -38.11 / -38.11 | -62.58 / -62.58 | 18 / 18 | 0.00% |
The cap loops converged in my run for all five cells (cap 8 / 10 / 12 reproduce DS3_EXPOSURE_CAP's $1,975k for the weight-1 version separately: see that page).

## 2. The key dial with pause 30: flagged, not a pass
My emulation: cuts = the box-side exits before the session flat (engine exit-type code 2 with exit before the flat), pause = skip that book's signals for 30 minutes after a cut, iterated to a fixed point (converged within 8 passes), on top of PE x0.5, cap 12 (original hook), gate 1R. ZL-2's pause mask uses the stored TH-L2 cut stream (ai_cuts.pkl), which is not the same object; its cell did not converge. Mine / ZL-2 (differences > 5% marked):
| metric | mine | ZL-2 | diff | % |
|---|---|---|---|---|
| total | 1613.34 | 1468.73 | +144.61 | +9.8% |
| F_mean | 11.70 | 10.42 | +1.28 | +12.3% |
| F_dd | 59.46 | 57.98 | +1.48 | +2.6% |
| Y26_mean | 24.32 | 21.23 | +3.09 | +14.5% |
| Y26_dd | 31.12 | 22.78 | +8.34 | +36.6% |
| HOLD_dd | 84.55 | 62.42 | +22.12 | +35.4% |
| PRE_dd | 52.07 | 46.42 | +5.65 | +12.2% |
| L6M_dd | 31.12 | 22.45 | +8.67 | +38.6% |
| X_dd | 31.03 | 32.89 | -1.86 | -5.7% |
| worst_day | -28.22 | -27.20 | -1.02 | +3.7% |
| worst_week | -43.32 | -41.50 | -1.81 | +4.4% |
| peak_net | 14.00 | 14.00 | +0.00 | +0.0% |
| tail_synth | 405.72 | 405.72 | +0.00 | +0.0% |
So at pause 30 the two definitions disagree on sign for the HOLD drawdown (mine: worse than the pause-0 cell, $66.6k -> $84.6k; ZL-2's: better, $62.4k) and on size for the cost (mine: total -9.7% vs pause 0; ZL-2's -17.8%). The pause family is definition-dependent and unconverged: treat every pause-15 / pause-30 row of the frontier as approximate, as ZL-2's page says.

## 3. By-product of the cross-check
Reading the engine record for this check showed that my DIS-AT outage replay had mislabelled the exit-type codes (0 stop, 1 target, 2 box-side exit); DS3_OUTAGE.md now carries an appended CORRECTION (worst synthetic cases smaller, scenarios with resting orders unchanged). The same record fields (ty0, kx0, lv0, sl0, tgl) are used by ZL-2's pause mask only through the stored cut stream, so the frontier pause-0 cells are unaffected.
