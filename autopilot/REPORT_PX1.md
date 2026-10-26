# REPORT PX1 - PA5 NEAR-MISS CURE: de-risking-controlled NQ/ES 60-min realised-vol-ratio tilt (D07/D08 x M8, H2)
**Verdict: NO. FOUND 0. Primary cell W60_MEAN1 (TWO_V, top vol-ratio tercile x0.75/bottom x1.25, renormalised to mean size 1): weekly Sharpe uplift +0.24 clean / +0.29 H1 / -0.16 H2 (needed +0.10 each); all-in +0.18; vs flat-0.96x control +0.54/+0.32/-0.38; bootstrap 90% CI of all-in uplift [-0.27, +0.62]; plateau 0.33 of 6; 2x slip +0.34/+0.40/-0.21; ES/RTY all-in +0.09/+0.00.** Pre-registered fresh in PREREG_AUTOPILOT.md block 'PX1' before the first run.

## Disclosure (binding)
H1/H2 for the NQ pair were ALREADY read for the parent PA5 (L60_TWO_V +0.55/+0.55/+0.06, REPORT_PA5.md). Every NQ number on H1/H2/all-in below is non-virgin. Even with every gate passing, the maximum status is FOUND-PENDING until the newest live weeks (after 2026-10-13) confirm; H0 is not testable (pair rows start 2023-08). ES/RTY is the only data not used by the parent, but it covers the same calendar window.

## Pre-registered design (summary)
- Feature/terciles/scheme identical to PA5 (q_W = ln(sqrt(sum r_NQ^2)/sqrt(sum r_ES^2)), W bars ending at EI-1, |r|>2% zeroed, terciles frozen on clean entries). Grid 6 cells = W {45,60,75} x {RAW, MEAN1}, MEAN1 = RAW divided by its mean over all pair trades (constant scalar). Primary W60_MEAN1 declared before running; no selection among cells.
- Controls: flat 0.96x size; random-tercile-assignment null (global permutation of the primary's multiplier vector, identical distribution, 100 draws); block null (feature permuted within book/year/ET-hour, 100 draws).
- Plateau neighbours (all MEAN1-renormalised): tercile share 25%/42%, multiplier deviation x0.75/x1.25, W 45/75; need >= 5 of 6 to keep >= 75% of all-in uplift.
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) via ROWS_corrected_engine, clean process, baseline reproduced 1.46/2.83/2.30. Fill: 1 tick/side + $34.88 per 8 lots; 2x slippage = SLIP_PT 1.0 on baseline and candidate. Multipliers applied through the sizing function (contract counts are rounded in the engine).

## All six cells and the flat control (weekly-Sharpe uplift vs baseline; clean is the only selection-relevant column; no cell is selected)
| cell | clean | H1 | H2 | all | mean mult (all/clean) | min-max | share touched |
|---|---|---|---|---|---|---|---|
| W45_RAW | +0.30 | +0.14 | +0.43 | +0.31 | 0.959/1.000 | 0.75-1.25 | 0.71 |
| W45_MEAN1 | +0.28 | +0.04 | +0.14 | +0.22 | 1.000/1.042 | 0.78-1.30 | 1.00 |
| W60_RAW | +0.55 | +0.55 | +0.06 | +0.47 | 0.960/1.000 | 0.75-1.25 | 0.71 |
| W60_MEAN1 | +0.24 | +0.29 | -0.16 | +0.18 | 1.000/1.042 | 0.78-1.30 | 1.00 |
| W75_RAW | +0.07 | -0.29 | +0.13 | +0.04 | 0.959/1.000 | 0.75-1.25 | 0.71 |
| W75_MEAN1 | -0.07 | -0.53 | -0.05 | -0.13 | 1.000/1.043 | 0.78-1.30 | 1.00 |
| flat 0.96x | -0.30 | -0.03 | +0.21 | -0.15 | 0.960/0.960 | 0.96 | 1.00 |

## Result for the primary cell (weekly Sharpe)
| span | pair | overlay | uplift | flat-0.96x uplift | uplift minus flat | vs B.Cfg() | 2x slip uplift |
|---|---|---|---|---|---|---|---|
| clean | 1.46 | 1.70 | +0.24 | -0.30 | +0.54 | +0.41 | +0.34 |
| H1 | 2.83 | 3.12 | +0.29 | -0.03 | +0.32 | +1.28 | +0.40 |
| H2 | 2.30 | 2.13 | -0.16 | +0.21 | -0.38 | +0.22 | -0.21 |
| all | 1.86 | 2.03 | +0.18 | -0.15 | +0.33 | +0.50 | +0.23 |

## Gate checklist
- g1 uplift >= +0.10 clean/H1/H2: FAIL
- g2 uplift minus flat-0.96x control >= +0.10 clean/H1/H2: FAIL
- g3 worst week not worse (all-in): PASS
- g4 null p95 clean and all-in (random-assignment AND block null): FAIL
- g5 bootstrap 90% CI of all-in uplift > 0: FAIL
- g6 plateau >= 75% (>=5 of 6): FAIL
- g7 2x slip uplift >= +0.10 each span: FAIL
- g8 alternating-month split: held-out > 0 both directions and >= 25% of selection-half: FAIL
- g9 ES/RTY leg: both all-in > 0, mean >= 50% of NQ all-in, no span below -0.10: FAIL
- null detail, random assignment (rank/p95): clean 0.99/+0.15, H1 0.74/+1.01, H2 0.76/+0.36, all 0.97/+0.08
- null detail, block permutation (rank/p95): clean 0.87/+0.32, H1 0.78/+0.54, H2 0.71/+0.50, all 0.97/+0.12
- plateau neighbours (all-in uplift; need >= 0.13): {'share25': 0.07, 'share42': 0.05, 'm x0.75': 0.32, 'm x1.25': 0.08, 'L45': 0.22, 'L75': -0.13}
- flat-0.96x control under 2x slippage (all spans): {'clean': -0.06, 'H1': -0.06, 'H2': 0.14, 'all': -0.02}
- bootstrap CI clean: [-0.21, +0.74]; weekly corr with pair 0.88; worst-week delta all-in +1131
- g10 insurance metrics: table below. g11 NT8-codable: see Executability.
- Pre-registration, no selection, H1/H2 non-virgin (disclosed): process PASS.

## Alternating-month split (2023-08..2026-10; selects among the 6 cells on one half, reads on the other)
- odd->even: selected W45_RAW (selection-half uplift +0.10), read +0.39. Primary W60_MEAN1: selection-half -0.14, held-out +0.39.
- even->odd: selected W60_RAW (selection-half uplift +0.82), read -0.01. Primary W60_MEAN1: selection-half +0.39, held-out -0.14.

## Mandatory ES/RTY leg (standalone ST+HM books via d1_f4_core, ADR20 k=0.75, equal R, live account rules, 1 tick/side; own/reference vol ratio: ES book ES/NQ, RTY book RTY/ES; terciles frozen on each book clean entries; weekly-Sharpe uplift; proxies, no null)
| book | cell | clean | H1 | H2 | all-in | base all-in Sharpe |
|---|---|---|---|---|---|---|
| ES | W45_RAW | +0.14 | -0.30 | +0.18 | +0.08 | -0.75 |
| ES | W45_MEAN1 | +0.12 | -0.18 | +0.34 | +0.12 | -0.75 |
| ES | W60_RAW | +0.17 | -0.39 | +0.04 | +0.05 | -0.75 |
| ES | W60_MEAN1 | +0.19 | -0.44 | +0.19 | +0.09 | -0.75 |
| ES | W75_RAW | +0.14 | -0.42 | +0.11 | +0.05 | -0.75 |
| ES | W75_MEAN1 | +0.18 | -0.51 | +0.25 | +0.09 | -0.75 |
| ES | flat0.96 | +0.02 | -0.19 | -0.11 | -0.03 | -0.75 |
| RTY | W45_RAW | +0.13 | -0.01 | -0.08 | +0.06 | -0.41 |
| RTY | W45_MEAN1 | +0.13 | +0.03 | -0.08 | +0.07 | -0.41 |
| RTY | W60_RAW | +0.06 | +0.15 | -0.35 | -0.01 | -0.41 |
| RTY | W60_MEAN1 | +0.07 | +0.20 | -0.36 | +0.00 | -0.41 |
| RTY | W75_RAW | +0.01 | +0.08 | -0.15 | -0.01 | -0.41 |
| RTY | W75_MEAN1 | +0.01 | +0.08 | -0.15 | -0.01 | -0.41 |
| RTY | flat0.96 | -0.05 | +0.01 | -0.08 | -0.04 | -0.41 |
- Trades: ES 2780 (clean 1517), RTY 2784 (clean 1512). Primary W60_MEAN1 all-in: ES +0.09, RTY +0.00; mean +0.05 vs NQ +0.18 (27% of NQ): g9 FAIL. Same calendar window as the pair, so correlated evidence, not independent draws.
- ERA / H0: not testable (pair rows start 2023-08).
- Replication status under Amendment 2: needs >= 2 of {newest live weeks, H0, ES/RTY, alternating-month}; newest live weeks pending, H0 n/a.

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| clean cand | 1.70 | 3.36 | 5.01 | -79.5k | -78.6k | 322k | -81.4k | 38.1 |
| H1 cand | 3.12 | 6.93 | 4.67 | -78.0k | -77.7k | 160k | -78.2k | 25.0 |
| H2 cand | 2.13 | 4.33 | 3.18 | -79.5k | -78.4k | 214k | -79.6k | 44.4 |
| all cand | 2.03 | 4.09 | 9.45 | -79.3k | -78.5k | 322k | -81.4k | 37.5 |

Insurance flags (INS?, cost%, CVaR5 impr%, worst-week impr%, maxDD impr%): clean (False, 21.1, -0.9, 0.6, -14.8); H1 (False, 26.2, -0.5, 0.2, -5.7); H2 (False, -10.7, 1.9, 3.6, 1.7); all (False, 13.2, -0.1, 1.4, -14.8)

## Executability
NT8 at NinjaTrader Brokerage via Rithmic: ES as a second data series in the NQ strategy, rolling sums of squared 1-min log returns (NQ, ES) over W=60 bars, tercile edges as constants from the 2023-08..2025-07 entries, entry-quantity multiplier (MEAN1 range about 0.78-1.30; sizes round to whole contracts). Margin unchanged at multipliers <= 1; peak contracts about +30% on bottom-tercile entries. No data purchase.

Files: code/census/night_ins/ap_pc_run.py, ap_pc_rep.py, ap_pc_alt.py, ap_pc_xi.py, ap_pc_doc.py; outputs/autopilot/px1/.

DONE PX1
