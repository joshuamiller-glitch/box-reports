# REPORT M2A - pair-modifier families registered as METHOD-2 families (PA4_NKD, PA5..PA10, PX1, PX20..PX27)

Registered: 16 families, 90 cells, `outputs/methods2/fam/<id>.npz` + 16 rows in FAMILY_REGISTRY.csv (order_form pair_overlay, pair_dependent 1, status ready, owner m2a). Built by `code/census/night_ins/ap_m2a_build.py`; OOS read by `ap_m2a_oos.py` (stats in `outputs/autopilot/m2a_stats.json`, verification in `m2a_verify.json`).

## Construction
- Cell series = daily USD P&L of the modified pair minus live pair daily P&L (delta), at the pair live size (`size_basis='pair_delta_live_size'`; the library-standard-size basis does not apply). Window = the pair rows of the source runs, 2023-02-10..2026-10-13 (950 label days; no pair rows 2023-02-01..09 or after 10-13), so first/last = 20230210/20261013 for every cell.
- No engine re-run was needed: each autopilot pickle (`pa*/pa*_all.pkl`, `px*/px*_all.pkl`) stores the modified daily series of EVERY pre-registered cell (R[cell] or X[cell]) plus the live pair series (`base`), produced by the clean-process harness B.Cfg(wk_floor=8,wk_loss_pb=None). Delta = stored cell series minus stored base.
- Verification: for every cell the all-in (2023-08..) weekly-Sharpe uplift recomputed from the delta matrix equals the stored summary json value (max abs error 0.000 in all 16 families, selected-cell uplift identical to the report headline).
- Full pre-registered grid per family (all cells, not only the carried one). Cell counts 3-9 (<10): the format would mark these 'tiny'; they are registered `ready` as instructed and flagged in notes (they can be merged into one pair-modifier super-family if the harness skips <10-cell families). PA4 in REPORT_PA4.md is the Databento job-status report (no cells); the PA4 mechanism family is REPORT_PA4_NKD (id PA4_NKD).

## OOS delta vs the live pair (ap_m2.py harness)
Walk-forward 9/3/3 months, rule `ew` (equal-risk weights by fit-window SD, cells with zero SD excluded), family ensemble = equal-risk average of all cells' delta series; 155 OOS weeks (2023-11..2026-10-13), each read once. 'Mean USD/wk' = equal-dollar average of the cells' delta on the OOS days (live size). 'Sharpe (unit)' = Sharpe of the equal-risk OOS delta series (harness metric). Null = 200 copies, all cells shifted by one common offset: demeaned (drift-neutral; tests the mean > 0) and raw shift (keeps drift = timing null). Rank = share of null Sharpes below the observed. The 'boot' column is the 4-week block bootstrap 90% interval of the OOS weekly mean delta in USD. These are delta (overlay minus pair) series, so a positive Sharpe means the overlay family improves the pair out of sample.

| family | cells | OOS wk mean delta USD | OOS Sharpe (unit) | OOS net USD | boot 90% USD/wk | H1 / H2 Sharpe | null rank demeaned (p95) | null rank raw (p95) | gates a/b/c/d |
|---|---|---|---|---|---|---|---|---|---|
| PA4_NKD | 9 | +453 | -0.15 | +70,238 | [-3,004, +3,945] | -1.25 / +0.96 | 0.47 (+0.37) | 0.41 (+0.46) | nnnn |
| PA5_VR60 | 9 | -1,178 | -0.26 | -182,582 | [-4,451, +1,909] | -0.16 / -0.35 | 0.09 (+0.24) | 0.27 (+0.07) | nnnn |
| PA6_VCX | 6 | -6,677 | -1.34 | -1,034,877 | [-11,668, -1,969] | -1.52 / -1.10 | 0.00 (+0.29) | 0.01 (-0.63) | nnnn |
| PA7_EAE | 6 | -1,910 | -0.42 | -296,079 | [-5,693, +1,711] | -0.31 / -0.53 | 0.00 (+0.30) | 0.32 (-0.10) | nnnn |
| PA8_GAP | 9 | -639 | -0.65 | -99,085 | [-2,038, +765] | -0.43 / -1.07 | 0.00 (+0.47) | 0.21 (+0.29) | nnnn |
| PA9_ALIGN | 9 | -4,098 | -1.61 | -635,220 | [-6,902, -1,410] | -2.11 / -1.09 | 0.00 (+0.27) | 0.68 (-1.48) | nnnn |
| PA10_K4 | 6 | -1,946 | -0.50 | -301,560 | [-5,066, +1,295] | -0.34 / -0.66 | 0.01 (+0.46) | 0.12 (+0.11) | nnnn |
| PX1_VR60MC | 6 | +2,269 | +0.65 | +351,739 | [-1,534, +5,806] | +0.70 / +0.61 | 1.00 (+0.27) | 0.52 (+0.83) | YYnY |
| PX20_ZNSHOCK | 4 | -1,931 | -0.42 | -299,270 | [-5,744, +1,648] | -0.21 / -0.65 | 0.00 (+0.47) | 0.46 (+0.03) | nnnn |
| PX21_6ESHOCK | 4 | -4,665 | -0.95 | -723,036 | [-8,804, -886] | -0.29 / -1.88 | 0.00 (+0.68) | 0.37 (-0.36) | nnnn |
| PX22_CLSHOCK | 4 | -4,346 | -0.92 | -673,659 | [-8,091, -536] | -0.23 / -1.66 | 0.00 (+0.52) | 0.20 (-0.18) | nnnn |
| PX23_GCJYSHOCK | 4 | -6,506 | -1.21 | -1,008,373 | [-11,708, -1,445] | -1.57 / -0.80 | 0.00 (+0.60) | 0.04 (-0.33) | nnnn |
| PX24_BTC | 9 | -1,468 | -0.92 | -227,592 | [-3,381, +352] | -1.32 / -0.49 | 0.00 (+0.14) | 0.14 (-0.26) | nnnn |
| PX25_FHR | 6 | -735 | -0.84 | -113,906 | [-1,563, +2] | -1.17 / -0.36 | 0.00 (+0.61) | 0.23 (-0.34) | nnnn |
| PX26_GAP | 6 | +867 | +0.49 | +134,450 | [-518, +2,150] | +0.00 / +1.20 | 0.92 (+0.53) | 0.19 (+1.41) | YnnY |
| PX27_L30VOL | 3 | -1,128 | -0.42 | -174,833 | [-3,984, +1,512] | -0.70 / -0.17 | 0.02 (+0.41) | 0.21 (+0.25) | nnnn |

## In-sample reference (whole 2023-02-10..2026-10-13, no walk-forward) and cell spread
| family | IS ensemble Sharpe (unit) | IS wk mean delta USD | OOS cell-level Sharpe median [min, max] |
|---|---|---|---|
| PA4_NKD | +0.12 | +345 | +0.03 [-0.35, +0.61] |
| PA5_VR60 | -0.16 | -549 | -0.19 [-0.89, +1.10] |
| PA6_VCX | -0.91 | -4,790 | -1.23 [-1.73, -0.31] |
| PA7_EAE | -0.40 | -1,556 | -0.33 [-0.78, -0.05] |
| PA8_GAP | -0.38 | -582 | -0.34 [-0.73, -0.05] |
| PA9_ALIGN | -1.74 | -4,336 | -1.23 [-1.87, -0.04] |
| PA10_K4 | -0.34 | -1,124 | -0.34 [-0.96, -0.07] |
| PX1_VR60MC | +0.60 | +2,305 | +0.63 [-0.29, +1.10] |
| PX20_ZNSHOCK | -0.42 | -1,764 | -0.43 [-0.49, -0.28] |
| PX21_6ESHOCK | -1.00 | -4,006 | -0.97 [-1.26, -0.81] |
| PX22_CLSHOCK | -0.66 | -2,878 | -0.84 [-1.11, -0.65] |
| PX23_GCJYSHOCK | -0.90 | -4,720 | -1.06 [-1.20, -0.80] |
| PX24_BTC | -0.39 | -837 | -0.56 [-1.05, +0.72] |
| PX25_FHR | -0.72 | -600 | -0.76 [-1.30, +1.33] |
| PX26_GAP | +0.75 | +1,000 | +0.48 [-0.30, +1.17] |
| PX27_L30VOL | -0.13 | -506 | -0.35 [-0.73, +0.47] |

## Reading
- 2 of 16 families have a positive OOS ensemble delta (PX1_VR60MC, PX26_GAP); none has a bootstrap interval of the weekly mean above 0, so none passes gate (c); no family passes gates a-d jointly. PX1_VR60MC (raw rank 0.52, demeaned rank 1.00) is the only one with a notable positive OOS delta (+2.3k USD/wk, Sharpe +0.65, both halves positive) but its interval is [-1.5k, ...] and the raw timing null does not separate it; it is the PA5 near-miss cure and remains a lead for the family test, not a pass. PX26_GAP: +0.49, H1 0.00 / H2 +1.20, demeaned rank 0.92.
- Most families have a negative OOS delta: the live pair is already close to the best of its neighbourhood out of sample. Demeaned ranks near 0 for negative-drift deltas are expected (the demeaned null has zero mean), so read the raw-shift rank for timing and the sign of the mean for direction.
- Multiplicity: F=16 families scored here; best-of-F ranks are left to the central REPORT_FAMILIES harness (this report gives single-family ranks).
- Caveat: delta series are at the pair's live size and are only defined 2023-02-10..2026-10-13 (pair-dependent); H0, 2013-22 and ES/RTY transplant are not applicable. Executable: market-entry quantity multiplier/skip/early-exit overlays on the live NT8 pair (see source reports).

DONE M2A
