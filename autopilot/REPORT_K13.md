# REPORT K13 - EXIT ON SESSION-VWAP RECLAIM AGAINST THE TRADE (D00/D01 x M5), live pair
**Verdict: NO. FOUND 0. Selected ('G', 10, 0): weekly Sharpe uplift -0.14 clean / -1.07 H1 / -0.05 H2 (needed +0.10 each); all-in -0.23; bootstrap 90% CI of all-in uplift [-0.84, +0.38]; plateau 0.00 of 2; shifted-state null (best-of-grid) clean rank 0.03 (p95 +0.31).** Backlog 2 item 13. Runtime 11 s (grid, neighbours, 2x slip, 100-draw best-of-grid null). Pre-registered in PREREG_AUTOPILOT.md (K11/K13/K14/K16 block) before the first run.

## Set-up and fill model
- Rows: 13,089 live pair rows (ROWS_corrected_engine.parquet, 2023-02-10..2026-10-13), replayed from the fill on 1-second bars (ap_g11_c_core.rs, as G11-C/H10-A) with the 60/60 bracket until the trigger bar, exit at that 1-min bar close; rows whose real exit was external (kind 1) exit at the trigger bar close; rows and signals not touched keep their live P&L. Modified rows re-run through the live account B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (reproduced baseline 1.46/2.83/2.30). Slippage 1 tick/side + $34.88 per 8 lots; 2x = SLIP_PT 1.0. Triggers use data through the trigger bar only.
- Rule: VWAP = cumulative typical-price x volume / cumulative volume from the anchor; ARMED once the close is on the trade side of VWAP at some bar >= entry; exit at the close of the first later bar with side x (close - VWAP) <= -b.
- Grid (8 (anchor {Globex 18:00 ET, RTH 09:30-16:00} x buffer b {0, 10 pts} x scope {ST rows only; ST+HM})); selection clean only; H1/H2 printed after selection (the grid table below lists all spans for transparency, only the selected cell was acted on).
- Null: external state series (ES returns / signed volume / VWAP deviation) circularly shifted by 7-400 whole days (time-of-day preserved), identical rule over the full grid, best clean uplift per draw, 100 draws, linear delta-P&L on the baseline account. Pair-change framing only (exit rule of the pair; no separate book so additive and constant-risk framings do not apply; ES/RTY cross-check not applicable). Pair rows start 2023-02, so the pre-2023 ERA flag is n/a.

## Grid (weekly Sharpe uplift vs baseline)
| cell | clean | H1 | H2 | all | rows changed | total pts delta |
|---|---|---|---|---|---|---|
| ('G', 0, 0) | -0.45 | -0.29 | +0.05 | -0.28 | 2594 | -3704 |
| ('G', 0, 1) | -0.79 | +0.57 | -0.21 | -0.41 | 4487 | -5685 |
| ('G', 10, 0) | -0.14 | -1.07 | -0.05 | -0.23 | 1930 | -738 |
| ('G', 10, 1) | -0.37 | -0.93 | -0.11 | -0.36 | 3399 | -3551 |
| ('R', 0, 0) | -0.14 | -0.52 | -0.17 | -0.19 | 1294 | -2883 |
| ('R', 0, 1) | -0.28 | -0.59 | -0.34 | -0.32 | 2133 | -3321 |
| ('R', 10, 0) | -0.19 | -0.21 | -0.14 | -0.18 | 979 | -1597 |
| ('R', 10, 1) | -0.15 | -0.21 | -0.12 | -0.13 | 1597 | -1432 |

Mechanism: HM is a VWAP-relative trend rule (E5), so a close back across the session VWAP is the flow-reversal sign of the same participants; exiting there should cut the give-back. Result: for HM this is nearly its own exit, for ST it truncates winners; every cell loses points (dpts -0.7k to -5.7k). Under the Globex anchor 2,594-4,487 rows exit early; under RTH 979-2,133 (RTH VWAP is undefined outside 09:30-16:00, 72% of bars).

## Result for the carried cell ('G', 10, 0)
Sharpe clean/H1/H2/all: pair 1.46/2.83/2.30/1.86; candidate 1.32/1.76/2.24/1.62. Neighbours: b 7.5: -0.18/-0.79/-0.03 (all -0.20); b 12.5: -0.30/-1.13/+0.10 (all -0.31); 
Weekly correlation with the pair 0.78 (same trades, no hedge claim; worst-decile correlation n/a).

## Gate checklist
- 3 uplift >= +0.10 on clean, H1, H2: FAIL (-0.14/-1.07/-0.05)
- worst week not worse (all-in): PASS (delta +1706 $)
- own null p95 (clean / H1 / H2 / all-in rank): FAIL (0.03 / 0.02 / 0.44 / 0.01)
- bootstrap CI > 0: FAIL ([-0.84, +0.38])
- plateau >= 75% of +-25% neighbours keep >= 75%: FAIL (0.00 of 2)
- 2x slippage uplift >= +0.10 each span: FAIL (+0.05/-1.11/-0.13)
- replication (H0 and alt-month): FAIL (H0 -0.27; alt-month select odd -> ('R', 0, 0) -0.41 reads +0.12 even; select even -> ('G', 10, 0) +0.60 reads -0.79 odd)
- wd corr: n/a (modification of pair rows)
- Pre-registration, clean-only selection, H1/H2 once: PASS (process)

## Insurance metrics (weekly)
| span | pair Sharpe | cand Sharpe | pair Sortino | cand Sortino | pair CVaR5 | cand CVaR5 | pair maxDD | cand maxDD | pair worst wk | cand worst wk | pair %neg | cand %neg |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| clean | 1.46 | 1.32 | 2.78 | 2.32 | -78.7k | -78.5k | 280k | 262k | -81.9k | -79.5k | 42.9 | 41.0 |
| H1 | 2.83 | 1.76 | 6.09 | 3.30 | -77.6k | -79.2k | 152k | 231k | -78.3k | -80.8k | 39.3 | 42.9 |
| H2 | 2.30 | 2.24 | 4.69 | 4.77 | -81.1k | -79.1k | 217k | 214k | -82.5k | -80.0k | 44.4 | 44.4 |
| all | 1.86 | 1.62 | 3.63 | 3.00 | -79.2k | -78.9k | 280k | 284k | -82.5k | -80.8k | 42.9 | 42.3 |

## Executability / era
NT8: built-in session VWAP (or a coded cumulative VWAP with the 18:00 ET / 09:30 ET reset), armed flag per position, market exit on the cross. Fully codable on the NQ chart alone. Margin: unchanged (exits only; same 8/8 pair). Fill model: market exit at the trigger bar close. Era flag: pair rows start 2023-02; pre-2023 and ES/RTY replication n/a; H0 as in the checklist. Mechanism depends on current structure (ES leads NQ at 1 minute, aggressor-flow persistence).
Files: code/census/night_ins/ap_k_core.py, ap_k_run.py; outputs/autopilot/k13/ (k13_summary.json, k13_all.pkl); log k13.log.

DONE K13
