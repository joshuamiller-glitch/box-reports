# REPORT PA5 - NQ/ES REALISED-VOL RATIO TILT (D07/D08 x M8, H2)
**Verdict: NO. FOUND 0. Selected L60_TWO_V: weekly Sharpe uplift +0.55 clean / +0.55 H1 / +0.06 H2 (needed +0.10 each); all-in +0.47; bootstrap 90% CI of all-in uplift [+0.01, +0.95]; plateau 0.17 of 6; null rank clean 1.00 (p95 +0.39).** Pool of 5, pre-registered in PREREG_AUTOPILOT.md block 'PA4 / PA5 / PA6 / PA7' before the first run.

## Set-up and fill model
- q_W = ln(sqrt(sum r_NQ^2)/sqrt(sum r_ES^2)) over the W 1-minute bars ending at EI-1, W in {30,60,120}; terciles frozen from clean entries; HIGH_DOWN (top x0.5), HIGH_UP (top x1.5), TWO_V (top x0.75 / bottom x1.25); 9 cells. H7-A used the return spread, not the vol ratio.
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) via ROWS_corrected_engine, clean process, baseline reproduced 1.46 / 2.83 / 2.30. Fill model as live: 1 tick/side + $34.88 per 8 lots; 2x slippage = SLIP_PT 1.0 on baseline and variant. Overlay NOT renormalised. Features use only data closed before the entry bar (daily state: 17:00 ET closes before the entry label day).
- Selection on clean only (uplift vs baseline per cell, clean): L30_HIGH_DOWN -0.190, L30_HIGH_UP -0.446, L30_TWO_V +0.204, L60_HIGH_DOWN +0.002, L60_HIGH_UP -0.261, L60_TWO_V +0.555, L120_HIGH_DOWN -0.267, L120_HIGH_UP -0.263, L120_TWO_V -0.047. Top eligible cell carried; H1/H2 read once for it (other cells' H1/H2 are in the json, unused).

## Result for the carried cell (weekly Sharpe)
| span | pair | overlay | uplift | vs B.Cfg() | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 2.01 | +0.55 | +0.69 | +0.58 |
| H1 | 2.83 | 3.38 | +0.55 | +1.55 | +0.11 |
| H2 | 2.30 | 2.35 | +0.06 | +0.38 | -0.17 |
| all | 1.86 | 2.33 | +0.47 | +0.77 | +0.36 |

## Gate checklist
- 3 uplift >= +0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): PASS
- null p95 clean and all-in: PASS
- bootstrap CI > 0: PASS
- plateau >= 75%: FAIL
- 2x slip >= +0.10 each span: FAIL
- null detail (rank/p95): clean 1.00/+0.39, H1 0.81/+0.92, H2 0.76/+0.72, all 1.00/+0.31
- plateau neighbours (all-in uplift): {'share25': 0.26, 'share42': 0.19, 'm x0.75': 0.37, 'm x1.25': 0.06, 'L x0.75': 0.31, 'L x1.25': 0.04}
- worst-decile corr: n/a (overlay on pair, weekly corr with pair 0.87; no hedge claim)
- affected share/range: min 0.75 max 1.25 mean 0.960
- Pre-registration, clean-only selection, H1/H2 once: PASS (process).

## Replication (pre-registered alternating-month split, 2023-08..2026-10, weekly Sharpe uplift from daily series)
- odd->even: cell selected on the selection months = L60_TWO_V (uplift -0.01); read on held-out months +0.82. Carried clean cell L60_TWO_V: selection-months -0.01, held-out +0.82.
- even->odd: cell selected on the selection months = L60_TWO_V (uplift +0.82); read on held-out months -0.01. Carried clean cell L60_TWO_V: selection-months +0.82, held-out -0.01.
- H0 / pre-2023: not testable (pair rows start 2023-08). ERA FLAG: not testable.
- Replication status: a FOUND would need >= 2 of {newest live weeks, H0, ES/RTY 2023-26, alternating-month split}; none are credited unless the gates above pass.

## Reading
Near-miss, formally NO: the carried cell L60_TWO_V (tilt 0.75x on the top tercile of the 60-minute NQ/ES vol ratio, 1.25x on the bottom tercile, 67% of entries touched, mean multiplier 0.96) is the best of the family and clears null (rank 1.00 clean/all-in), bootstrap CI (>0) and worst week, and every plateau neighbour has a positive all-in uplift (+0.04 to +0.37), but H2 is +0.06 (needs +0.10), the plateau test fails (1 of 6 keep 75% of +0.47), 2x slippage H2 is -0.17, and the alternating-month split is lopsided (one half of the months carries +0.82, the other -0.01). Only L30_TWO_V (+0.20) and L60_TWO_V (+0.55) are clean-positive; the HIGH_DOWN/HIGH_UP one-sided schemes are not (-0.45 to +0.00), so the effect is the lower-vol-ratio tercile sized up, not the stress tercile sized down; part of it is the 0.96 mean-size (small de-risking) effect. Disclosure for any follow-up: H1/H2 of this cell are now read; a variant could only be FOUND with newest live weeks, ES/RTY (ES/RTY cross-check pre-registered only if NQ gates pass, so not run) or H0. NT8: ES as second series, rolling sums of squared 1-min returns, quantity multiplier.

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| clean cand | 2.01 | 4.11 | 5.90 | -79.1k | -78.4k | 317k | -80.4k | 35.2 |
| H1 cand | 3.38 | 7.84 | 5.30 | -77.9k | -77.6k | 158k | -78.3k | 25.0 |
| H2 cand | 2.35 | 5.08 | 2.92 | -79.5k | -78.5k | 259k | -80.5k | 41.7 |
| all cand | 2.33 | 4.88 | 10.92 | -79.1k | -78.3k | 317k | -80.5k | 35.1 |

Insurance flags (INS?, cost%, CVaR5 impr%, worst-week impr%, maxDD impr%): clean (False, 40.7, -0.5, 1.9, -13.3); H1 (False, 41.3, -0.4, -0.0, -4.3); H2 (False, -0.9, 1.9, 2.4, -19.0); all (False, 29.0, 0.1, 2.4, -13.3)

## Executability
NT8 at NinjaTrader Brokerage via Rithmic: the existing strategies read the state (daily closes of ZN/6J/GC or NQ, or the 1-minute NQ tape) and set an entry-quantity multiplier (or skip); margin unchanged for multipliers <= 1; peak contracts +25-50% on flagged entries for multipliers > 1.

Files: code/census/night_ins/ap_pa1_run.py, ap_g10_rep.py, ap_h7_alt.py, ap_pa1_doc.py; outputs/autopilot/pa5/.

DONE PA5
