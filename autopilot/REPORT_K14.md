# REPORT K14 - EXIT WHEN SIGNED VOLUME RUNS AGAINST THE TRADE (D02 x M5), live pair
**Verdict: NO. FOUND 0. Selected (15, 1): weekly Sharpe uplift +0.20 clean / -0.51 H1 / -0.57 H2 (needed +0.10 each); all-in -0.06; bootstrap 90% CI of all-in uplift [-0.74, +0.63]; plateau 0.00 of 4; shifted-state null (best-of-grid) clean rank 0.88 (p95 +0.29).** Backlog 2 item 14. Runtime 27 s (grid, neighbours, 2x slip, 100-draw best-of-grid null). Pre-registered in PREREG_AUTOPILOT.md (K11/K13/K14/K16 block) before the first run.

## Set-up and fill model
- Rows: 13,089 live pair rows (ROWS_corrected_engine.parquet, 2023-02-10..2026-10-13), replayed from the fill on 1-second bars (ap_g11_c_core.rs, as G11-C/H10-A) with the 60/60 bracket until the trigger bar, exit at that 1-min bar close; rows whose real exit was external (kind 1) exit at the trigger bar close; rows and signals not touched keep their live P&L. Modified rows re-run through the live account B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (reproduced baseline 1.46/2.83/2.30). Slippage 1 tick/side + $34.88 per 8 lots; 2x = SLIP_PT 1.0. Triggers use data through the trigger bar only.
- Rule: NQ signed volume per minute (buy - sell aggressor contracts, outrights summed, DRIVERS parquet); run against the trade over the last m bars (window wholly after entry): net signed volume against >= thr and >= 70% of the m bars signed against; thr = mean over the previous 10 sessions of the 85th percentile of |m-bar net| in the same ET hour (causal); exit at that bar close.
- Grid (6 (m {5,10,15} bars x scope {all rows; only if in unrealised loss})); selection clean only; H1/H2 printed after selection (the grid table below lists all spans for transparency, only the selected cell was acted on).
- Null: external state series (ES returns / signed volume / VWAP deviation) circularly shifted by 7-400 whole days (time-of-day preserved), identical rule over the full grid, best clean uplift per draw, 100 draws, linear delta-P&L on the baseline account. Pair-change framing only (exit rule of the pair; no separate book so additive and constant-risk framings do not apply; ES/RTY cross-check not applicable). Pair rows start 2023-02, so the pre-2023 ERA flag is n/a.

## Grid (weekly Sharpe uplift vs baseline)
| cell | clean | H1 | H2 | all | rows changed | total pts delta |
|---|---|---|---|---|---|---|
| (5, 0) | -1.45 | -2.13 | -3.01 | -1.89 | 7531 | -18860 |
| (5, 1) | -1.52 | -2.17 | -1.94 | -1.69 | 6475 | -16778 |
| (10, 0) | -0.89 | -1.23 | -1.17 | -0.97 | 5704 | -12217 |
| (10, 1) | -0.50 | -0.98 | -1.06 | -0.67 | 4865 | -7564 |
| (15, 0) | -0.19 | -0.98 | -0.92 | -0.46 | 3773 | -7412 |
| (15, 1) | +0.20 | -0.51 | -0.57 | -0.06 | 3207 | -4308 |

Mechanism: flow persistence is short (mostly < 5 min, DRIVERS S2) and impact is permanent, so a sustained run of aggressor volume against an open trade should signal that the move is flow-driven and will continue. Result: the 5/10 bar cells fire on 37-58% of rows and wreck the pair (clean uplift -0.5 to -1.5); only the slowest, loss-only cell is positive on clean and it reverses on H1/H2. Signed volume available 2023-02-02..2026-10-13. Clean-best cell is the one H1/H2 reverse: the common failure.

## Result for the carried cell (15, 1)
Sharpe clean/H1/H2/all: pair 1.46/2.83/2.30/1.86; candidate 1.66/2.32/1.73/1.79. Neighbours: m x0.75: -0.79/+0.07/-1.24 (all -0.78); m x1.25: +0.14/-0.01/+0.26 (all +0.15); pct75: -0.90/-0.27/-1.22 (all -0.89); pct95: +0.10/-0.88/+0.16 (all -0.03); 
Weekly correlation with the pair 0.72 (same trades, no hedge claim; worst-decile correlation n/a).

## Gate checklist
- 3 uplift >= +0.10 on clean, H1, H2: FAIL (+0.20/-0.51/-0.57)
- worst week not worse (all-in): PASS (delta +932 $)
- own null p95 (clean / H1 / H2 / all-in rank): FAIL (0.88 / 0.54 / 0.14 / 0.62)
- bootstrap CI > 0: FAIL ([-0.74, +0.63])
- plateau >= 75% of +-25% neighbours keep >= 75%: FAIL (0.00 of 4)
- 2x slippage uplift >= +0.10 each span: FAIL (+0.28/-0.89/-0.64)
- replication (H0 and alt-month): FAIL (H0 -1.29; alt-month select odd -> (15, 1) -0.45 reads +0.87 even; select even -> (15, 0) +0.99 reads -1.35 odd)
- wd corr: n/a (modification of pair rows)
- Pre-registration, clean-only selection, H1/H2 once: PASS (process)

## Insurance metrics (weekly)
| span | pair Sharpe | cand Sharpe | pair Sortino | cand Sortino | pair CVaR5 | cand CVaR5 | pair maxDD | cand maxDD | pair worst wk | cand worst wk | pair %neg | cand %neg |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| clean | 1.46 | 1.66 | 2.78 | 3.23 | -78.7k | -79.8k | 280k | 289k | -81.9k | -81.6k | 42.9 | 40.0 |
| H1 | 2.83 | 2.32 | 6.09 | 4.59 | -77.6k | -77.8k | 152k | 146k | -78.3k | -77.8k | 39.3 | 39.3 |
| H2 | 2.30 | 1.73 | 4.69 | 3.08 | -81.1k | -79.0k | 217k | 225k | -82.5k | -79.6k | 44.4 | 38.9 |
| all | 1.86 | 1.79 | 3.63 | 3.41 | -79.2k | -79.5k | 280k | 289k | -82.5k | -81.6k | 42.9 | 39.9 |

## Executability / era
NT8: needs signed (aggressor-side) volume per minute inside the strategy: tick replay / Volumetric bars (bid/ask volume) on the NQ chart. Feasible with NT8 Order Flow+ volumetric bars; not on plain OHLCV. Coded as a rolling sum with a trailing per-hour quantile table. Margin: unchanged (exits only; same 8/8 pair). Fill model: market exit at the trigger bar close. Era flag: pair rows start 2023-02; pre-2023 and ES/RTY replication n/a; H0 as in the checklist. Mechanism depends on current structure (ES leads NQ at 1 minute, aggressor-flow persistence).
Files: code/census/night_ins/ap_k_core.py, ap_k_run.py; outputs/autopilot/k14/ (k14_summary.json, k14_all.pkl); log k14.log.

DONE K14
