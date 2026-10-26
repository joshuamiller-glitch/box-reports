# REPORT H7-B - EXIT WHEN NQ/REF CONFIRMATION BREAKS MID-TRADE (D07 x M5, H2-H4)
**Verdict: NO. FOUND 0. Selected RTY_NQAHEAD_k1.5: weekly Sharpe uplift +0.19 clean / -0.92 H1 / -0.25 H2 (needed +0.10 each); all-in -0.06; bootstrap 90% CI of all-in uplift [-0.42, +0.29]; plateau 0.00 of 2; null rank clean 1.00 (p95 -0.26).** Pool of 5, pre-registered in PREREG_AUTOPILOT.md section H7 before the first run.

## Set-up and fill model
- Since-entry spread Dv = side x (dlnNQ - dlnREF)/(sigma x sqrt n); exit at next bar open when Dv >= k (NQAHEAD) or <= -k (REFAHEAD), from entry+5 min; REF {ES,RTY} x k {1.5,2,3}; 12 cells; same patch machinery as G6c time-flatten (locks re-run). Null: same exited trades, exit at a uniformly random bar inside the trade (100 draws).
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) via ROWS_corrected_engine, clean process, baseline reproduced 1.46 / 2.83 / 2.30. Fill model as live: 1 tick/side + $34.88 per 8 lots; 2x slippage = SLIP_PT 1.0 on baseline and variant. Overlay NOT renormalised. Features use only bars closed before the entry bar (ES/RTY/macro 1-min back-adjusted, forward-filled, stale>5min -> off).
- Selection on clean only (uplift vs baseline per cell, clean): ES_NQAHEAD_k1.5 -0.131, ES_NQAHEAD_k2.0 -0.149, ES_NQAHEAD_k3.0 -0.070, ES_REFAHEAD_k1.5 -0.140, ES_REFAHEAD_k2.0 +0.135, ES_REFAHEAD_k3.0 -0.084, RTY_NQAHEAD_k1.5 +0.188, RTY_NQAHEAD_k2.0 +0.068, RTY_NQAHEAD_k3.0 +0.188, RTY_REFAHEAD_k1.5 -0.213, RTY_REFAHEAD_k2.0 +0.171, RTY_REFAHEAD_k3.0 +0.012. Top cell carried; H1/H2 read once for it (other cells' H1/H2 are in the json, unused).

## Result for the carried cell (weekly Sharpe)
| span | pair | overlay | uplift | vs B.Cfg() | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.65 | +0.19 | +0.13 | +0.21 |
| H1 | 2.83 | 1.91 | -0.92 | -0.29 | -0.86 |
| H2 | 2.30 | 2.04 | -0.25 | +0.11 | -0.30 |
| all | 1.86 | 1.80 | -0.06 | +0.05 | -0.04 |

## Gate checklist
- 3 uplift >= +0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): PASS
- null p95 clean and all-in: PASS
- bootstrap CI > 0: FAIL
- plateau >= 75%: FAIL
- 2x slip >= +0.10 each span: FAIL
- null detail (rank/p95): clean 1.00/-0.26, H1 0.36/-0.35, H2 0.98/-0.37, all 1.00/-0.38
- plateau neighbours (all-in uplift): {'k x0.75': -0.02, 'k x1.25': -0.07}
- worst-decile corr: n/a (overlay on pair, weekly corr with pair 0.92; no hedge claim)
- affected share/range: min 0.00 max 1.00 mean 0.847
- Pre-registration, clean-only selection, H1/H2 once: PASS (process).

## Replication (pre-registered alternating-month split, 2023-08..2026-10, weekly Sharpe uplift from daily series)
- odd->even: cell selected on the selection months = RTY_NQAHEAD_k2.0 (uplift +0.06); read on held-out months -0.33. Carried clean cell RTY_NQAHEAD_k1.5: selection-months -0.13, held-out -0.01.
- even->odd: cell selected on the selection months = ES_REFAHEAD_k1.5 (uplift +0.46); read on held-out months -0.45. Carried clean cell RTY_NQAHEAD_k1.5: selection-months -0.01, held-out -0.13.
- Cross-instrument: REF dimension (ES vs RTY) is inside the grid (see per-cell clean uplifts above); H0 / pre-2023: not testable (pair rows and harness series start 2023-02/08). ERA FLAG: not testable.

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| clean cand | 1.65 | 3.10 | 6.31 | -78.7k | -78.0k | 226k | -81.9k | 41.0 |
| H1 cand | 1.91 | 3.72 | 2.73 | -79.1k | -78.8k | 174k | -79.8k | 35.7 |
| H2 cand | 2.04 | 4.12 | 3.31 | -78.6k | -78.0k | 212k | -78.7k | 41.7 |
| all cand | 1.80 | 3.44 | 11.51 | -78.9k | -78.2k | 226k | -81.9k | 40.5 |

Insurance flags (INS?, cost%, CVaR5 impr%, worst-week impr%, maxDD impr%): clean (False, 7.3, 0.1, 0.0, 19.2); H1 (False, -20.0, -1.9, -1.9, -14.5); H2 (False, -7.7, 3.0, 4.7, 2.4); all (False, -3.0, 0.4, 0.8, 19.2)

## Executability
NT8 at NinjaTrader Brokerage via Rithmic: ES/RTY (or macro) 1-min feeds in the same workspace drive an entry-size multiplier (A, C) or a market exit on the open position (B) of the existing strategies; margin unchanged (multiplier <= 1.5 raises peak contracts only on flagged entries).

Files: code/census/night_ins/ap_h7_core.py, ap_h7_run.py, ap_h7_alt.py, ap_h7_doc.py (rep = ap_g10_rep.py); outputs/autopilot/h7_b/.

Note: the exit-family null (random exit bar) is a weak benchmark because random exits are costly; the verdict rests on the failed H1/H2, bootstrap, plateau and slippage gates.

DONE H7-B
