# REPORT PA4_NKD - NKD-STATE TILT OF GLOBEX ENTRIES (D07 x M4, H3)
**Verdict: NO. FOUND 0. Selected L60_ALIGN_UP: weekly Sharpe uplift -0.09 clean / -0.42 H1 / +0.74 H2 (needed +0.10 each); all-in +0.08; bootstrap 90% CI of all-in uplift [-0.34, +0.51]; plateau 0.00 of 6; null rank clean 0.70 (p95 +0.14).** Pool of 5, J9P idea 4, pre-registered in PREREG_AUTOPILOT.md block 'PA4 / PA5 / PA6 / PA7' before the first run.

## Set-up and fill model
- n_L = side x (ln NKD[EI-1]-ln NKD[EI-1-L])/(sigma_NKD1m sqrt L), L in {60,180,360} minutes, applied to entries 18:00-02:59 ET only (others multiplier 1); terciles frozen from clean Globex entries; COUNTER_DOWN (bottom x0.5), ALIGN_UP (top x1.5), TWO (0.75/1.25); 9 cells. J10 tested NKD only as a standalone NQ signal (NO).
- Regenerated 2026-10-16 from outputs/autopilot/pa4/ (pa4_all.pkl, pa4_summary.json, pa4_alt.json, rep.log, alt.log) because the original idea report file REPORT_PA4.md was overwritten by the L2 scaffolding report (ID collision; REPORT_PA4.md is the L2 report and is untouched). Numbers are read from the stored result files, nothing re-run.
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) via ROWS_corrected_engine, clean process, baseline reproduced 1.46 / 2.83 / 2.30. Fill model as live: 1 tick/side + $34.88 per 8 lots; 2x slippage = SLIP_PT 1.0 on baseline and variant. Overlay NOT renormalised. Features use only data closed before the entry bar (daily state: 17:00 ET closes before the entry label day).
- Selection on clean only (uplift vs baseline per cell, clean): L60_COUNTER_DOWN -0.196, L60_ALIGN_UP -0.091, L60_TWO -0.370, L180_COUNTER_DOWN -0.279, L180_ALIGN_UP -0.541, L180_TWO -0.519, L360_COUNTER_DOWN -0.594, L360_ALIGN_UP -0.618, L360_TWO -0.317. Top eligible cell carried; H1/H2 read once for it (other cells' H1/H2 are in the json, unused).

## Result for the carried cell (weekly Sharpe)
| span | pair | overlay | uplift | vs B.Cfg() | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.37 | -0.09 | -0.11 | -0.02 |
| H1 | 2.83 | 2.41 | -0.42 | -0.15 | -0.24 |
| H2 | 2.30 | 3.04 | +0.74 | +0.44 | +0.64 |
| all | 1.86 | 1.93 | +0.08 | +0.02 | +0.13 |

## Gate checklist
- 3 uplift >= +0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): PASS
- null p95 clean and all-in: FAIL
- bootstrap CI > 0: FAIL
- plateau >= 75%: FAIL
- 2x slip >= +0.10 each span: FAIL
- null detail (rank/p95): clean 0.70/+0.14, H1 0.33/+0.69, H2 1.00/+0.28, all 0.95/+0.07
- plateau neighbours (all-in uplift): {'share25': -0.09, 'share42': -0.12, 'm x0.75': -0.06, 'm x1.25': -0.24, 'L x0.75': -0.21, 'L x1.25': -0.23}
- worst-decile corr: n/a (overlay on pair, weekly corr with pair 0.90; no hedge claim)
- affected share/range: min 1.00 max 1.50 mean 1.050
- Pre-registration, clean-only selection, H1/H2 once: PASS (process).

## Replication (pre-registered alternating-month split, 2023-08..2026-10, weekly Sharpe uplift from daily series)
- odd->even: cell selected on the selection months = L60_ALIGN_UP (uplift +0.23); read on held-out months -0.11. Carried clean cell L60_ALIGN_UP: selection-months +0.23, held-out -0.11.
- even->odd: cell selected on the selection months = L60_COUNTER_DOWN (uplift +0.48); read on held-out months -0.23. Carried clean cell L60_ALIGN_UP: selection-months -0.11, held-out +0.23.
- H0 / pre-2023: not testable (pair rows start 2023-08). ERA FLAG: not testable.
- Replication status: a FOUND would need >= 2 of {newest live weeks, H0, ES/RTY 2023-26, alternating-month split}; none are credited unless the gates above pass.

## Reading
Clean NO. All nine cells are clean-negative (-0.09 to -0.62); the carried L60_ALIGN_UP (x1.5 on the top NKD-agreement tercile of Globex entries, 8.6% of clean entries touched, mean multiplier 1.05) has clean -0.09 / H1 -0.42 / H2 +0.74, all-in +0.08 with bootstrap CI straddling zero, plateau 0 of 6, and the alternating-month split reverses sign (selection-months +0.23 reads -0.11; the other half selects L60_COUNTER_DOWN +0.48 and reads -0.23). Affected entries are only 8.6-17.6% of the clean sample, so the effect is small either way and no insurance improvement appears (CVaR5/worst week essentially unchanged, maxDD worse -34% clean). NKD does not add information for Globex NQ entries beyond the pair. Disclosure: H1/H2 read once for the carried cell only; the H2 +0.74 is not selection-eligible. Closed in GAPMAP (D07 x H3 x M4 x NQ).

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| clean cand | 1.37 | 2.56 | 3.47 | -78.3k | -77.9k | 375k | -79.5k | 45.7 |
| H1 cand | 2.41 | 5.17 | 3.09 | -79.5k | -78.7k | 194k | -80.2k | 35.7 |
| H2 cand | 3.04 | 6.91 | 5.02 | -78.8k | -78.1k | 232k | -79.8k | 33.3 |
| all cand | 1.93 | 3.88 | 8.17 | -78.8k | -78.2k | 375k | -80.2k | 41.7 |

Insurance flags (INS?, cost%, CVaR5 impr%, worst-week impr%, maxDD impr%): clean (False, -2.1, 0.5, 2.9, -33.9); H1 (False, 0.8, -2.5, -2.5, -27.8); H2 (False, 52.7, 2.9, 3.3, -6.6); all (False, 14.1, 0.6, 2.8, -33.9)

## Executability
NT8 at NinjaTrader Brokerage via Rithmic: the existing strategies read the state (daily closes of ZN/6J/GC or NQ, or the 1-minute NQ tape) and set an entry-quantity multiplier (or skip); margin unchanged for multipliers <= 1; peak contracts +25-50% on flagged entries for multipliers > 1.

Files: code/census/night_ins/ap_pa1_run.py, ap_g10_rep.py, ap_h7_alt.py, ap_pa1_doc.py (regenerated via ap_pc_doc_pa4.py); outputs/autopilot/pa4/.

DONE PA4_NKD
