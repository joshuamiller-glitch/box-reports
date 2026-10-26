# REPORT K11 - EXIT WHEN NQ/ES RESIDUAL MOVES AGAINST THE TRADE (D07 x M5), live pair
**Verdict: NO. FOUND 0. Selected (2, 1): weekly Sharpe uplift -0.02 clean / -0.20 H1 / -0.09 H2 (needed +0.10 each); all-in -0.06; bootstrap 90% CI of all-in uplift [-0.45, +0.30]; plateau 0.00 of 2; shifted-state null (best-of-grid) clean rank 0.94 (p95 -0.00).** Backlog 2 item 11. Runtime 18 s (grid, neighbours, 2x slip, 100-draw best-of-grid null). Pre-registered in PREREG_AUTOPILOT.md (K11/K13/K14/K16 block) before the first run.

## Set-up and fill model
- Rows: 13,089 live pair rows (ROWS_corrected_engine.parquet, 2023-02-10..2026-10-13), replayed from the fill on 1-second bars (ap_g11_c_core.rs, as G11-C/H10-A) with the 60/60 bracket until the trigger bar, exit at that 1-min bar close; rows whose real exit was external (kind 1) exit at the trigger bar close; rows and signals not touched keep their live P&L. Modified rows re-run through the live account B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (reproduced baseline 1.46/2.83/2.30). Slippage 1 tick/side + $34.88 per 8 lots; 2x = SLIP_PT 1.0. Triggers use data through the trigger bar only.
- Rule: residual = NQ 1-min point change - beta(lag1, rolling 390-bar OLS) x ES 1-min point change; Z = side x cumulative residual since entry close / (sigma_390 x sqrt(bars since entry)); exit at the close of the first bar >= entry+5 with Z <= -k.
- Grid (4 (k {1,2} x scope {all rows; only if in unrealised loss})); selection clean only; H1/H2 printed after selection (the grid table below lists all spans for transparency, only the selected cell was acted on).
- Null: external state series (ES returns / signed volume / VWAP deviation) circularly shifted by 7-400 whole days (time-of-day preserved), identical rule over the full grid, best clean uplift per draw, 100 draws, linear delta-P&L on the baseline account. Pair-change framing only (exit rule of the pair; no separate book so additive and constant-risk framings do not apply; ES/RTY cross-check not applicable). Pair rows start 2023-02, so the pre-2023 ERA flag is n/a.

## Grid (weekly Sharpe uplift vs baseline)
| cell | clean | H1 | H2 | all | rows changed | total pts delta |
|---|---|---|---|---|---|---|
| (1, 0) | -0.97 | -0.23 | +0.99 | -0.42 | 3816 | -5944 |
| (1, 1) | -0.48 | -0.46 | +1.41 | -0.10 | 3184 | -5794 |
| (2, 0) | -0.09 | +0.28 | -0.11 | -0.03 | 982 | -3468 |
| (2, 1) | -0.02 | -0.20 | -0.09 | -0.06 | 843 | -2978 |

Mechanism: the NQ-specific residual is mostly noise (DRIVERS: NQ 1-min return is 75-85% same-minute ES), so an NQ-only adverse move against the trade should not be a reason to leave; a market-wide (ES-led) adverse move should. Result: the residual exit fires on 6-29% of rows and mostly cuts trades that would have recovered. k=1 triggers on 3,816 of 13,089 rows (29%) and k=2 on 982/843, so the 1-sigma cells are a high-turnover rule; every cell lowers total points (dpts -3.0k to -5.9k). Selected cell has a negative clean uplift because the clean-best of four negative/near-zero cells is the least bad.

## Result for the carried cell (2, 1)
Sharpe clean/H1/H2/all: pair 1.46/2.83/2.30/1.86; candidate 1.44/2.63/2.21/1.79. Neighbours: k x0.75: -0.04/-0.58/+0.96 (all +0.10); k x1.25: -0.21/-0.29/-0.24 (all -0.24); 
Weekly correlation with the pair 0.91 (same trades, no hedge claim; worst-decile correlation n/a).

## Gate checklist
- 3 uplift >= +0.10 on clean, H1, H2: FAIL (-0.02/-0.20/-0.09)
- worst week not worse (all-in): PASS (delta +651 $)
- own null p95 (clean / H1 / H2 / all-in rank): FAIL (0.94 / 0.99 / 0.97 / 1.00)
- bootstrap CI > 0: FAIL ([-0.45, +0.30])
- plateau >= 75% of +-25% neighbours keep >= 75%: FAIL (0.00 of 2)
- 2x slippage uplift >= +0.10 each span: FAIL (+0.23/-0.43/-0.08)
- replication (H0 and alt-month): FAIL (H0 -0.16; alt-month select odd -> (2, 1) -0.45 reads +0.46 even; select even -> (2, 1) +0.46 reads -0.45 odd)
- wd corr: n/a (modification of pair rows)
- Pre-registration, clean-only selection, H1/H2 once: PASS (process)

## Insurance metrics (weekly)
| span | pair Sharpe | cand Sharpe | pair Sortino | cand Sortino | pair CVaR5 | cand CVaR5 | pair maxDD | cand maxDD | pair worst wk | cand worst wk | pair %neg | cand %neg |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| clean | 1.46 | 1.44 | 2.78 | 2.68 | -78.7k | -79.2k | 280k | 280k | -81.9k | -81.9k | 42.9 | 42.9 |
| H1 | 2.83 | 2.63 | 6.09 | 5.46 | -77.6k | -77.3k | 152k | 148k | -78.3k | -77.6k | 39.3 | 39.3 |
| H2 | 2.30 | 2.21 | 4.69 | 4.36 | -81.1k | -78.8k | 217k | 243k | -82.5k | -79.7k | 44.4 | 38.9 |
| all | 1.86 | 1.79 | 3.63 | 3.41 | -79.2k | -79.0k | 280k | 280k | -82.5k | -81.9k | 42.9 | 41.7 |

## Executability / era
NT8: a second data series (ES, same session template, 1-min), a rolling-390 regression beta and residual std computed per bar in the strategy, cumulative residual since entry per open position; ExitLong/ExitShort at market when Z <= -k (and optionally the position is under water). No new data feed beyond ES 1-min, which the account already has. Margin: unchanged (exits only; same 8/8 pair). Fill model: market exit at the trigger bar close. Era flag: pair rows start 2023-02; pre-2023 and ES/RTY replication n/a; H0 as in the checklist. Mechanism depends on current structure (ES leads NQ at 1 minute, aggressor-flow persistence).
Files: code/census/night_ins/ap_k_core.py, ap_k_run.py; outputs/autopilot/k11/ (k11_summary.json, k11_all.pkl); log k11.log.

DONE K11
